# Internet Access — Agent Sandbox

> **Source:** [kiro.dev/docs/autonomous-agent/sandbox/internet-access/](https://kiro.dev/docs/autonomous-agent/sandbox/internet-access/)

---

El Agent Sandbox puede configurarse con diferentes niveles de acceso a Internet según tus necesidades de seguridad y dependencias del proyecto.

---

## Access Levels

### 1. Connections Access Only *(más seguro)*

El nivel mínimo requerido para que el sandbox funcione. Permite al agente:
- Clonar repositorios de GitHub
- Abrir y actualizar pull requests
- Acceder a GitHub a través del gateway service de Kiro

> **Recomendado** cuando tus tareas no requieren dependencias externas.

---

### 2. Common Dependencies

Incluye acceso a conexiones **más** registros de paquetes comunes y herramientas de desarrollo. Permite instalar dependencias desde package managers populares sin requerir acceso completo a Internet.

**Dominios permitidos automáticamente:**

```
alpinelinux.org  amazonaws.com  anaconda.com  apache.org  apt.llvm.org
archlinux.org  aws.amazon.com  azure.com  bitbucket.org  bower.io
centos.org  cocoapods.org  continuum.io  cpan.org  crates.io
debian.org  docker.com  docker.io  dot.net  dotnet.microsoft.com
eclipse.org  fedoraproject.org  gcr.io  ghcr.io  github.com
githubusercontent.com  gitlab.com  golang.org  google.com  goproxy.io
gradle.org  hashicorp.com  haskell.org  hex.pm  java.com  java.net
jcenter.bintray.com  json-schema.org  json.schemastore.org  k8s.io
launchpad.net  maven.org  mcr.microsoft.com  metacpan.org  microsoft.com
nodejs.org  npmjs.com  npmjs.org  nuget.org  oracle.com  packagecloud.io
packages.microsoft.com  packagist.org  pkg.go.dev  ppa.launchpad.net
pub.dev  pypa.io  pypi.org  pypi.python.org  pythonhosted.org  quay.io
ruby-lang.org  rubyforge.org  rubygems.org  rubyonrails.org  rustup.rs
rvm.io  sourceforge.net  spring.io  swift.org  ubuntu.com
visualstudio.com  yarnpkg.com
```

---

### 3. Open Internet

Proporciona acceso irrestricto a Internet al sandbox.

> ⚠️ **Advertencia de seguridad:** Habilitar permisos de red expone tu entorno a riesgos de seguridad, incluyendo: ataques de prompt injection, extracción de código y secrets, introducción de malware o fallas de seguridad, y uso de contenido que podría violar términos de licencia. Considerá cuidadosamente estos riesgos antes de habilitarlo.

---

### 4. Custom Allow-list

Especificá una lista de dominios permitidos separados por coma. Usá el formato `.domain` para incluir todos los subdominios.

**Ejemplos:**

| Entrada | Qué permite |
|---|---|
| `api.example.com` | Solo ese dominio específico |
| `.example.com` | `example.com` y todos sus subdominios (`api.example.com`, `www.example.com`, etc.) |
| `api.example.com, .cdn.example.com` | Múltiples dominios y patrones de subdominio |

---

## Related

- [Environment Variables →](./02_Environment%20Variables.md)
- [Environment Configuration →](./04_Environment%20Configuration.md)