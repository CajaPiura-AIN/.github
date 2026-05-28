# Area de Analítica e Inteligencia de Negocios

## Vertical de Ciencia de Datos

### Instalación de herramientas

El ciclo de vida de un proyecto de ciencia de datos, tanto para desarrollo como para producción, requiere contar con ciertas herramientas. Estas herramientas se instalan una única vez para ser usados en cualquier proyecto de ciencia de datos o MLOps.

#### Advertencia

Lee previamente el Instructivo para el Uso de Equipos de Cómputo e Informáticos v2.1 (lo ubica en Infoline360 de Caja Piura). Según ello, consulte con la supervisora de la Vertical de Ciencia de Datos para proceder con las instalaciones.

#### Recomendación

Casi todas las siguientes instalaciones se realizan por línea de comandos. Se recomienda ejecutar estas instrucciones en PowerShell 7.

De no contar con acceso a alguna otra *command line interface*, instalar PowerShell 7 desde:

- Microsoft Store (Recomendado)
- [Paquete MSI](https://learn.microsoft.com/es-es/powershell/scripting/install/install-powershell-on-windows?view=powershell-7.6#msi)

#### Para la única instalación de los herramientas

**[scoop](https://scoop.sh/)**

Un instalador de línea de comandos para Windows. Scoop es un gestor de paquetes para Windows. Descarga, instala y configura todo automáticamente dentro de un perfil de usuario, sin permisos de administrador.

- Instalación:
    ```shell
    Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
    Invoke-RestMethod -Uri https://get.scoop.sh | Invoke-Expression
    ```
- Verificación: `scoop --version`
- Uso: Será usado posteriormente para instalar *pipx* y *Go*.


**[pipx](https://pipx.pypa.io/stable/)**

`pipx` instala y ejecuta aplicaciones Python para usuarios finales en entornos aislados. Internamente utiliza `pip`, pero a diferencia de este, crea un entorno virtual independiente para cada aplicación, manteniendo así el sistemo limpio.

- Instalación:
    ```shell
    scoop install pipx
    pipx ensurepath
    ```
- Verificación: `pipx --version`
- Uso particular: Será usado posteriormente para instalar el resto de aplicaciones vía `pipx install <tool>`

#### Para la documentación

**[LaTeX](https://www.latex-project.org/)**

$\LaTeX$ es un sistema de composición tipográfica de alta calidad; incluye características diseñadas para la producción de documentación técnica y científica.

El uso de $\LaTeX$ requiere la instalación de una distribución TeX (el motor y paquetes), un editor de código y una extensión en dicho editor.

- Instalación de la distribución *MikTeX*: https://miktex.org/download
- Verificación: `miktex --version`
- Instalación de extensión para habilitar el uso de $\LaTeX$ en su IDE:
    - en VSCode, Positron o Antigravity: [LaTeX Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop).
    - en PyCharm: [TeXiFy IDEA](https://plugins.jetbrains.com/plugin/9473-texify-idea)
- Uso: [Aprende LaTeX en 5 minutos](https://www.youtube.com/watch?v=xzaTBYkqG-4&t=16s)

#### Para la gestión de versiones

Tanto para versionar código como datos.

**[Git](https://git-scm.com/)**

Sistema de control de versiones de código.

- Instalación: `scoop install git`
- Verificación: `git --version`
- Documentación: [Pro Git](https://git-scm.com/book/en/v2)
- Configuración:
    - establecer nombre de usuario: `git config --global user.name "<nombres y apellidos>"`
    - establecer correo de usuario: `git config --global user.email "<correo>@cajapiura.pe"`
    - renombrar rama principal por defecto: `git config --global init.defaultBranch main`
- Uso: basado en las herramientas *commitizen* y *git-flow-next*

**[GitHub](https://github.com/)**

GitHub es una plataforma en la nube utilizada para alojar código fuente y gestionar proyectos de código. Se usa GitHub para alojar las plantillas del área AIN bajo la organización [*CajaPiura-AIN*](https://github.com/CajaPiura-AIN).

Instrucciones:
- Estar registrados en GitHub. Así contar con una cuenta en esta plataforma.
- Los usuarios deben ser miembros y pertenecer a un equipo (*team*) de la organización. Así obtendrá los accesos necesarios para interactuar con repositorios de la organización. Solicitar ser miembro y pertenecer a un equipo de la organización vía correo electrónico a la propietaria de la organización (`kcordova@cajapiura.pe`).
- Para que el usuario interactúe con los repositorioes de la organizació, GitHub requiere que el usuario realice su autenticación. Cada usuario debe:
    - generar su clave SSH -> `ssh-keygen -t ed25519 -C "email"`. En la generación de la clave SSH, dar aceptar a todas las peticiones.
    - registrar la clave en su cuenta GitHub:
        - copiar la clave pública de ejecutar en PowerShell `cat ~/.ssh/id_ed25519.pub`
        - entrar a `GitHub → Settings → SSH and GPG Keys`. Pegar en `New SSH Key`
        - verificar en PowerShell -> `ssh -T git@github.com`

**[Commitizen](https://commitizen-tools.github.io/commitizen/)**

Commitizen es una potente herramienta de gestión de versiones que ayuda a los equipos a mantener mensajes de confirmación coherentes y significativos, al tiempo que automatiza la gestión de versiones.

¿Qué hace Commitizen? Hace cumplir convenciones de commits estandarizadas (por defecto [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/))

- Instalación: `pipx install commitizen`
- Verificación: `cz version`
- Documentanción: Diríjase a la sección [Basic Commands](https://commitizen-tools.github.io/commitizen/)
- Uso básico:
    - `cz commit`: para la confirmación de versiones de código
    - `cz bump`: para la definición de lanzamiento de versiones de código


**[Git-Flow-Next](https://git-flow.sh/)**

git-flow-next es una reimplementación moderna del popular modelo de ramificación git-flow. Desarrollado en Go, prioriza la fiabilidad, la extensibilidad y una mejor experiencia para el desarrollador.

- Requisito: Git-flow-next requiere previamente la instalación de Go: `scoop install go`
- Verificación: `go version`
- Instalación:
    ```shell
    go install github.com/gittower/git-flow-next@latest
    ```
- Verificación: `git-flow-next version`
- Uso: Revise la sección [*Quick Start*](https://git-flow.sh/docs/installation/)

**[Data Version Control DVC](https://dvc.org/)**

Gestiona los datos de la misma manera que se gestiona el código. Utilizando un modelo similar a Git, se aplica las mejores prácticas de ingeniería de software a los equipos de datos, IA/ML y ciencia de datos.

DVC se puede instalar en VSCode, en cualquier terminal del sistema, y utilizarse como una biblioteca de Python.

DVC no reemplaza ni incluye Git. Se debe tener Git en tu sistema para habilitar funciones importantes como el control de versiones de datos y la experimentación rápida.

- Instalación: `pipx install dvc`
- Verificación: `dvc --version` en una nueva instancia del CLI.
- Documentación: https://doc.dvc.org/start

#### Para la gestión de proyectos como paquetes

**[uv](https://docs.astral.sh/uv/)**

Un paquete y gestor de proyectos de Python extremadamente rápido, escrito en Rust.

- Instalación: `pipx install uv`
- Verificación: `uv --version`
- Documentación: https://docs.astral.sh/uv/guides/


#### Para la obtención de toolkits

**[Cookiecutter](https://cookiecutter.readthedocs.io/en/stable/index.html)**

Cookiecutter crea proyectos desde plantillas cookiecutters, por ejemplo, el toolkit de Caja Piura de proyectos de ciencia de datos y/o MLOps.

- Requisito: Para que Cookiecutter pueda descargar la plantilla remota es estrictamente necesario tener instalado Git.
- Instalación: `pipx install cookiecutter`
- Verificación: `cookiecutter --version`
- Documentación de uso: https://cookiecutter.readthedocs.io/en/stable/usage.html
- Uso particular:
    ```shell
    cookiecutter git+ssh://git@github.com/CajaPiura-AIN/<toolkit>.git
    ```

### Lista de toolkits

Se debe contar mínimo con Cookiecutter para la descarga de toolkits. Sin embargo, se recomienda realizar contar con todas las herramientas instaladas para una mayor facilidad de trabajo en el uso de los toolkits.

- [Toolkit MLOps](https://github.com/CajaPiura-AIN/caja_piura-toolkit-dsp)

  ```shell
  cookiecutter git+ssh://git@github.com/CajaPiura-AIN/caja_piura-toolkit-dsp.git
  ```

- [Skill para documentar scripts SQL](https://github.com/CajaPiura-AIN/caja_piura-generator_docs_sql)

  ```shell
  cookiecutter git+ssh://git@github.com/CajaPiura-AIN/caja_piura-generator_docs_sql.git
  ```
