# Métodos de autenticación: Kiro CLI

> **Fuente:** [kiro.dev/docs/cli/authentication/](https://kiro.dev/docs/cli/authentication/)

---

## Iniciar sesión en Kiro CLI

1. En la línea de comando, ingrese `kiro-cli` o `kiro-cli login`. Se le pedirá que presione Entrar para completar el inicio de sesión en su navegador.

2. En su navegador, elija la organización o sistema a través del cual se autenticará:
   -Google
   -GitHub
   - Identificación del constructor
   - Su organización, incluido AWS GovCloud (EE. UU.)

3. Después de autenticarse, recibirá un mensaje en su navegador que lo dirigirá nuevamente a su terminal.

4. Cuando regrese a su terminal, deberá iniciar sesión con Kiro CLI.

> **Nota:** Los métodos de inicio de sesión individuales como GitHub, Google y AWS Builder ID **no están disponibles** en las regiones de AWS GovCloud (EE. UU.).
>
> Los usuarios saben que usarán Kiro con AWS GovCloud (EE. UU.) asegurándose de que la URL de inicio utilizada durante la autenticación contenga `"us-gov-home"`, por ejemplo:
> ```
> https://start.us-gov-home.awsapps.com/directory/d-XXXXXXXXXX
> ```
>
> **Kiro IDE versión 0.9.2+** y **Kiro CLI versión 1.25.0+** son necesarios para la compatibilidad con las regiones de AWS GovCloud (EE. UU.).

---

## Iniciar sesión desde una máquina remota

Cuando se ejecuta Kiro CLI en una máquina remota (a través de SSH, SSM, contenedores, etc.), la autenticación funciona de manera diferente ya que la máquina remota no puede abrir un navegador.

- **Para Builder ID e IAM Identity Center:** Kiro CLI utiliza **autenticación de código de dispositivo**. Verá una URL y un código para ingresar en su navegador local; no se requiere configuración adicional.
- **Para inicio de sesión social (Google o GitHub):** La CLI utiliza autenticación PKCE que requiere **reenvío de puertos**. La devolución de llamada de OAuth redirige a "localhost", que no llegará a la CLI remota sin un túnel.

**Para iniciar sesión con inicio de sesión social en una máquina remota:**

1. Ejecute `kiro-cli login` y seleccione *"Usar gratis con Google o GitHub"*
2. Anote el número de puerto que se muestra (varía cada vez, por ejemplo, `49153`)
3. En una nueva terminal en su **máquina local**, configure el reenvío de puertos:
   ```golpecito
   ssh -L <PUERTO>:localhost:<PUERTO> -N usuario@host-remoto
   ```
   Reemplace `<PORT>` con el puerto del paso 2 y `user@remote-host` con sus credenciales remotas.
4. Presione Entrar en la CLI y luego abra la URL en su navegador local.
5. Autenticación completa: la devolución de llamada llega a la CLI a través del túnel

**Ejemplos de reenvío de puertos SSH:**

```golpecito
# Reenvío de puerto básico (reemplace 49153 con su puerto real)
ssh -L 49153:localhost:49153 -N usuario@host-remoto

# Con un archivo de identidad personalizado (común para EC2)
ssh -i ~/.ssh/my-key.pem -L 49153:localhost:49153 -N usuario@host-remoto

# Usando un alias de configuración SSH
ssh -L 49153:localhost:49153 -N miservidor
```

**Solución de problemas de reenvío de puertos:**

| Problema | Solución |
|---|---|
| Se agotó el tiempo de autenticación | El reenvío de puertos no está activo o es un puerto incorrecto. Verifique que el puerto coincida con la salida CLI. |
| No se pudo vincular el puerto de devolución de llamada | El puerto está en uso en el control remoto. Ejecute `lsof -i :<PORT>` para identificar el proceso. |
| Dirección ya en uso (SSH) | El puerto está en uso local. Cierre otros túneles o sesiones SSH obsoletas. |
| El túnel se desconecta a mitad de la autenticación | Mantenga la terminal SSH abierta hasta que se complete la autenticación. Agregue `-o ServerAliveInterval=60` |

---

## Cerrar sesión en Kiro CLI

```bash
kiro-cli logout
```

---

## Solución de problemas de autenticación

Si encuentra problemas durante el proceso de autenticación, como fallas de redireccionamiento del navegador o errores de inicio de sesión, consulte nuestra [guía de solución de problemas](https://kiro.dev/docs/troubleshooting/#authentication-issues) para obtener soluciones específicas de la plataforma y correcciones comunes.

---

## Próximos pasos

- [Revisar preguntas frecuentes →](https://kiro.dev/faq)
- [Explorar funciones de chat →](https://kiro.dev/docs/cli/chat)
- [Comenzar con Kiro CLI →](https://kiro.dev/docs/cli)