# Instalación: Kiro CLI

> **Fuente:** [kiro.dev/docs/cli/installation/](https://kiro.dev/docs/cli/installation/)

---

##macOS

Puede instalar Kiro CLI para macOS de forma nativa en la línea de comando:

```bash
curl -fsSL https://cli.kiro.dev/install | bash
```

Kiro le indicará que abra su navegador web, donde seguirá los pasos que se indican en [Autenticación](https://kiro.dev/docs/cli/authentication).

---

## Linux — Imagen de aplicación

Puede instalar Kiro CLI para Linux utilizando el formato AppImage, que es portátil y funciona en la mayoría de las distribuciones de Linux sin necesidad de instalación.

1. Descargue Kiro CLI para Linux AppImage:
   ```
   https://desktop-release.q.us-east-1.amazonaws.com/latest/kiro-cli.appimage
   ```

2. Haga que AppImage sea ejecutable:
   ```golpecito
   chmod +x kiro-cli.appimage
   ```

3. Ejecute AppImage:
   ```golpecito
   ./kiro-cli.appimage
   ```

4. Kiro le indicará que abra su navegador web para seguir los pasos de [Autenticación](https://kiro.dev/docs/cli/authentication).

---

## Linux: con un archivo zip

### Requisitos de instalación y actualización

- Debes poder extraer o "descomprimir" el paquete descargado.
- Kiro CLI requiere **glibc 2.34 o posterior** (incluido de forma predeterminada en la mayoría de las principales distribuciones de Linux lanzadas desde 2021).
- Para distribuciones más antiguas con glibc < 2.34, utilice la **versión especial basada en musl** (indicada por `-musl.zip` en el nombre del archivo).
- Compatible con versiones **x86_64** de 64 bits** y **ARM aarch64** de: Fedora, Ubuntu, Amazon Linux 2023.

### Comprobando tu versión de glibc

```bash
ldd --version
```

- Si **2.34 o más reciente** → use la versión estándar.
- Si es **mayor** → use la versión musl.

### Descargue el archivo de instalación

**Versión estándar (glibc 2.34+):**

Linuxx86-64:
```golpecito
curl --proto '=https' --tlsv1.2 -sSf \
  'https://desktop-release.q.us-east-1.amazonaws.com/latest/kirocli-x86_64-linux.zip' \
  -o 'kirocli.zip'
```

BRAZO de Linux (aarch64):
```golpecito
curl --proto '=https' --tlsv1.2 -sSf \
  'https://desktop-release.q.us-east-1.amazonaws.com/latest/kirocli-aarch64-linux.zip' \
  -o 'kirocli.zip'
```

**Versión Musl (para glibc < 2.34):**

Linux x86-64 con musl:
```golpecito
curl --proto '=https' --tlsv1.2 -sSf \
  'https://desktop-release.q.us-east-1.amazonaws.com/latest/kirocli-x86_64-linux-musl.zip' \
  -o 'kirocli.zip'
```

Linux ARM (aarch64) con musl:
```golpecito
curl --proto '=https' --tlsv1.2 -sSf \
  'https://desktop-release.q.us-east-1.amazonaws.com/latest/kirocli-aarch64-linux-musl.zip' \
  -o 'kirocli.zip'
```

### Instalar Kiro CLI

1. Descomprima el instalador:
   ```golpecito
   descomprimir kirocli.zip
   ```

2. Ejecute el programa de instalación:
   ```golpecito
   ./kirocli/install.sh
   ```

De forma predeterminada, los archivos se instalan en `~/.local/bin`.

---

## Linux — Ubuntu (paquete .deb)

1. Descargue Kiro CLI para Ubuntu:
   ```golpecito
   wget https://desktop-release.q.us-east-1.amazonaws.com/latest/kiro-cli.deb
   ```

2. Instale el paquete:
   ```golpecito
   sudo dpkg -i kiro-cli.deb
   sudo apt-get install -f
   ```

3. Inicie Kiro CLI:
   ```golpecito
   kiro-cli
   ```

4. Kiro le indicará que abra su navegador web para seguir los pasos de [Autenticación](https://kiro.dev/docs/cli/authentication).

---

## Configuración de proxy

Kiro CLI (v1.8.0 y posteriores) admite servidores proxy comúnmente utilizados en entornos empresariales. La CLI respeta automáticamente las variables de entorno de proxy estándar.

### Configuración de variables de entorno de proxy

```golpecito
# Proxy HTTP para tráfico no SSL
exportar HTTP_PROXY=http://proxy.company.com:8080

# Proxy HTTPS para tráfico SSL
exportar HTTPS_PROXY=http://proxy.company.com:8080

# Omitir proxy para dominios específicos
exportar NO_PROXY=localhost,127.0.0.1,.empresa.com
```

### Proxy con autenticación

```bash
export HTTP_PROXY=http://username:password@proxy.company.com:8080
export HTTPS_PROXY=http://username:password@proxy.company.com:8080
```

### Solución de problemas de proxy

- Verificar la accesibilidad y las credenciales del servidor proxy.
- Asegúrese de que su firewall corporativo permita conexiones a endpoints de AWS
- Póngase en contacto con su administrador de TI si falla la validación del certificado SSL
- Verifique que el servidor proxy admita los protocolos requeridos

---

## Desinstalación de Kiro CLI

**macOS:**
```golpecito
desinstalación de kiro-cli
```

**Ubuntu:**
```golpecito
sudo apt-get eliminar kiro-cli
sudo apt-get purge kiro-cli # Eliminar los archivos de configuración restantes
```

---

## Debug de Kiro CLI

Si tiene problemas con Kiro CLI, ejecute `kiro-cli doctor` para identificar y solucionar problemas comunes:

```bash
kiro-cli doctor
```

---

## Próximos pasos

- [Autenticación →](https://kiro.dev/docs/cli/authentication/)
- [Modelos →](https://kiro.dev/docs/cli/models/)