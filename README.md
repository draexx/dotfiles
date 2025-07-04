# Mis Configuraciones Personales (Dotfiles)

Este repositorio contiene mi colección personal de archivos de configuración para diversas herramientas y aplicaciones que uso en mi sistema operativo Linux. El objetivo es mantener un entorno de trabajo consistente, productivo y estéticamente agradable.

## Tabla de Contenidos
- [Requerimientos](#requerimientos)
  - [General](#general)
  - [Específicos de Configuración](#específicos-de-configuración)
- [Instalación](#instalación)
- [Uso](#uso)
  - [Conky](#conky)
  - [i3wm](#i3wm)
  - [Kitty](#kitty)
  - [Zellij](#zellij)
  - [Starship (Zsh Prompt)](#starship-zsh-prompt)
- [Detalles de las Configuraciones](#detalles-de-las-configuraciones)
  - [CONKY](#conky-1)
  - [i3wm](#i3wm-1)
  - [Kitty](#kitty-1)
  - [Zellij](#zellij-1)
- [Agradecimientos (Opcional)](#agradecimientos-opcional)
- [Contribuir](#contribuir)
- [Licencia](#licencia)

## Requerimientos

Para utilizar estas configuraciones, necesitarás tener instalados los siguientes programas. A continuación, se detallan los programas y cómo instalarlos en sistemas basados en Debian/Ubuntu (usando `apt`) y Arch Linux (usando `pacman`).

### General
- **zsh**: Un potente intérprete de comandos.
  - `sudo apt install zsh`
  - `sudo pacman -S zsh`
- **oh-my-zsh**: Un framework para gestionar la configuración de zsh.
  - Sigue las instrucciones en [https://ohmyz.sh/](https://ohmyz.sh/)
- **starship**: Un prompt minimalista, rápido y personalizable para cualquier shell.
  - `sudo apt install starship` (puede requerir un PPA o estar en versiones recientes)
  - `sudo pacman -S starship`
- **VSCode** o **Cursor**: Editores de código.
  - Descargar desde [https://code.visualstudio.com/](https://code.visualstudio.com/) o [https://cursor.sh/](https://cursor.sh/)
- **glances**: Un monitor de sistema en tiempo real.
  - `sudo apt install glances`
  - `sudo pacman -S glances`
- **eza**: Un reemplazo moderno para `ls`.
  - `sudo apt install eza` (puede requerir un PPA o estar en versiones recientes)
  - `sudo pacman -S eza`
- **duf**: Una utilidad para visualizar el uso del disco.
  - `sudo apt install duf` (puede requerir un PPA o estar en versiones recientes)
  - `sudo pacman -S duf`
- **fastfetch**: Una herramienta para mostrar información del sistema de forma rápida.
  - `sudo apt install fastfetch` (puede requerir un PPA o estar en versiones recientes)
  - `sudo pacman -S fastfetch`

### Específicos de Configuración

#### CONKY
- **Conky**: Un monitor de sistema ligero para X.
  - `sudo apt install conky-all`
  - `sudo pacman -S conky`
- **Lua**: Necesario para algunos scripts de Conky.
  - `sudo apt install lua5.3` (o la versión que necesite tu script)
  - `sudo pacman -S lua`

#### i3wm
- **i3-wm**: Un gestor de ventanas tiling.
  - `sudo apt install i3`
  - `sudo pacman -S i3-wm`
- **i3status**: Una utilidad para generar una barra de estado para i3.
  - `sudo apt install i3status`
  - `sudo pacman -S i3status`
- **dmenu** (o un lanzador compatible como **rofi**): Para lanzar aplicaciones.
  - `sudo apt install dmenu` o `sudo apt install rofi`
  - `sudo pacman -S dmenu` o `sudo pacman -S rofi`
- **feh** o **nitrogen**: Para gestionar fondos de pantalla.
  - `sudo apt install feh` o `sudo apt install nitrogen`
  - `sudo pacman -S feh` o `sudo pacman -S nitrogen`

#### Kitty
- **Kitty**: Un emulador de terminal rápido, con muchas funciones y acelerado por GPU.
  - `sudo apt install kitty`
  - `sudo pacman -S kitty`

#### Zellij
- **Zellij**: Un multiplexor de terminal y entorno de trabajo.
  - `cargo install --locked zellij` (requiere Rust y Cargo)
  - `sudo pacman -S zellij` (puede estar en AUR)

**Nota:** Algunos paquetes pueden tener nombres diferentes o requerir repositorios adicionales (como PPAs en Ubuntu o AUR en Arch Linux) dependiendo de la distribución y su versión.

## Instalación

A continuación se explica cómo instalar estas configuraciones en tu sistema.

**Advertencia:** Realiza una copia de seguridad de tus configuraciones actuales antes de proceder, ya que los siguientes comandos pueden sobrescribir archivos existentes.

1.  **Clona este repositorio:**
    ```bash
    git clone https://github.com/tu_usuario/tu_repositorio.git
    cd tu_repositorio
    ```
    (Reemplaza `tu_usuario/tu_repositorio` con la URL real del repositorio)

2.  **Copia los archivos de configuración:**

    *   **Conky:**
        ```bash
        mkdir -p ~/.config/conky
        cp -r conky/* ~/.config/conky/
        ```

    *   **i3wm:**
        ```bash
        mkdir -p ~/.config/i3
        cp i3wm/config ~/.config/i3/config
        cp i3wm/i3status.conf ~/.config/i3/i3status.conf
        # Si tienes un archivo config-i3 separado que quieras usar, renómbralo o ajústalo según sea necesario.
        # cp i3wm/config-i3 ~/.config/i3/config-i3
        ```

    *   **Kitty:**
        ```bash
        mkdir -p ~/.config/kitty
        cp kitty/kitty.conf ~/.config/kitty/kitty.conf
        cp kitty/theme.conf ~/.config/kitty/theme.conf
        # Los temas adicionales están en kitty/kitty-themes/themes, puedes copiarlos también si lo deseas
        # cp -r kitty/kitty-themes/themes ~/.config/kitty/kitty-themes/
        # Y luego referenciarlos desde tu kitty.conf
        ```
        Asegúrate de que `kitty.conf` incluya la línea `include ./theme.conf` o la ruta correcta si la cambias.
        Si usas `colors.conf` directamente, copia ese en su lugar o ajústalo.

    *   **Zellij:**
        ```bash
        mkdir -p ~/.config/zellij
        cp zellij/config.kdl ~/.config/zellij/config.kdl
        # Si usas un layout específico al iniciar zellij:
        # cp zellij/layout.kdl ~/.config/zellij/layout.kdl
        ```

    *   **Starship (prompt de zsh):**
        Si tienes un archivo de configuración para Starship (no listado en los archivos del repo pero mencionado en requerimientos), usualmente va en:
        ```bash
        # mkdir -p ~/.config
        # cp tu_starship_config.toml ~/.config/starship.toml
        ```
        (Este repositorio no parece incluir un `starship.toml` directamente, así que este paso es general).

    *   **Archivos de inicio de Zsh (`.zshrc`):**
        Este repositorio no incluye un `.zshrc`, pero si lo hiciera, lo copiarías a tu directorio home:
        ```bash
        # cp .zshrc ~/.zshrc
        ```

**Importante:** Revisa las rutas y los nombres de los archivos de configuración específicos de cada programa, ya que pueden variar ligeramente. Los comandos anteriores asumen las ubicaciones más comunes.

## Uso

Una vez que hayas instalado los programas requeridos y copiado los archivos de configuración, así es como puedes empezar a usarlos:

### Conky
Para iniciar Conky con una configuración específica, puedes ejecutarlo desde la terminal. Por ejemplo, para usar `conky_maia`:
```bash
conky -c ~/.config/conky/conky_maia
```
Puedes reemplazar `conky_maia` con el nombre de otro archivo de configuración de Conky que hayas copiado.

Para que Conky se inicie automáticamente con tu sesión de escritorio, puedes añadir el comando anterior a las aplicaciones de inicio de tu entorno de escritorio o gestor de ventanas.
- **En i3wm:** Añade `exec --no-startup-id conky -c ~/.config/conky/tu_conky_config` a tu archivo `~/.config/i3/config`.
- **En otros entornos (GNOME, KDE, XFCE):** Busca la configuración de "Aplicaciones al inicio" o "Autostart" y añade el comando.

### i3wm
Para usar la configuración de i3wm:
1.  Asegúrate de haber copiado el archivo `config` a `~/.config/i3/config`.
2.  Cierra la sesión actual de tu entorno de escritorio y, en la pantalla de inicio de sesión (display manager), selecciona "i3" como tu sesión antes de ingresar tu contraseña.
3.  Si ya estás en una sesión de i3, puedes recargar la configuración con el atajo de teclado predeterminado `Mod+Shift+r` (donde `Mod` suele ser la tecla Alt o Super/Windows).

Revisa el archivo `~/.config/i3/config` para conocer los atajos de teclado personalizados y otras configuraciones.

### Kitty
Kitty aplicará automáticamente la configuración de `~/.config/kitty/kitty.conf` cada vez que inicies una nueva ventana de terminal.
- Si realizas cambios en `kitty.conf` mientras Kitty está abierto, estos no se aplicarán a las ventanas existentes. Puedes cerrar y reabrir Kitty o, en algunos casos, usar `Ctrl+Shift+F5` (o el atajo configurado) para recargar la configuración en la pestaña actual.
- Los temas se gestionan a través de la directiva `include` en `kitty.conf`. Si copiaste `theme.conf`, asegúrate de que `kitty.conf` lo incluya correctamente.

### Zellij
Zellij cargará su configuración desde `~/.config/zellij/config.kdl` al iniciarse.
```bash
zellij
```
Si deseas iniciar Zellij con un layout específico (por ejemplo, `layout.kdl` que copiaste a `~/.config/zellij/`), puedes hacerlo con:
```bash
zellij --layout ~/.config/zellij/layout.kdl
```
O, si el archivo `layout.kdl` está en el directorio de configuración por defecto de Zellij, puedes usar un nombre más corto si Zellij lo soporta, o configurar layouts por defecto en `config.kdl`.

### Starship (Zsh Prompt)
Si Starship está instalado y tu `~/.zshrc` está configurado para usarlo (generalmente con una línea como `eval "$(starship init zsh)"`), el prompt se aplicará automáticamente cada vez que abras una nueva terminal Zsh. Si has copiado un archivo `starship.toml` a `~/.config/`, Starship lo usará para la personalización del prompt.

## Detalles de las Configuraciones

A continuación, se ofrece una breve descripción de cada conjunto de configuraciones incluidas en este repositorio.

### CONKY
Archivos de configuración para Conky, un monitor de sistema ligero y personalizable para X11.
- `clock_rings_maia.lua`: Script Lua para un widget de reloj con anillos.
- `conky_lua_maia`
- `conky_maia`
- `conky_maia1`
- `conky_shortcuts_live_maia`
- `conky1.10_shortcuts_maia`

### Vista previa
![Conky Configuración](./screenshots/conky_preview.png)

### i3wm
Configuración personalizada para i3-wm, un gestor de ventanas tiling para X11.
- `config`: Archivo principal de configuración de i3.
- `config-i3`: Posiblemente una variante o copia de seguridad de la configuración.
- `i3status.conf`: Configuración para i3status, usado para generar la barra de estado de i3.

### Vista previa
![i3wm Configuración](./screenshots/i3wm_preview.png)

### Kitty
Configuración para Kitty, un emulador de terminal rápido, con muchas funciones y acelerado por GPU.
- `kitty.conf`: Archivo principal de configuración de Kitty.
- `theme.conf`: Archivo de tema separado, probablemente incluido en `kitty.conf`.
- `colors.conf`: Podría ser una definición de esquema de colores, alternativa o complementaria a `theme.conf`.
- `kitty-themes/`: Directorio que contiene una colección de temas para Kitty.

### Vista previa
![Kitty Configuración](./screenshots/kitty_preview.png)

### Zellij
Configuración para Zellij, un multiplexor de terminal y entorno de trabajo.
- `config.kdl`: Archivo principal de configuración de Zellij, usando KDL (KDL Document Language).
- `layout.kdl`: Define un layout específico para las sesiones de Zellij.

### Vista previa
![Zellij Configuración](./screenshots/zellij_preview.png)

## Agradecimientos (Opcional)

Este proyecto se ha inspirado en el trabajo de muchas personas en la comunidad de personalización de Linux. Si alguna configuración específica o idea proviene de otro proyecto o persona, considera añadir un agradecimiento aquí.

Por ejemplo:
*   Agradecimientos a [Nombre del Proyecto/Persona] por [Contribución específica o inspiración].
*   Inspirado por los dotfiles de [Usuario de GitHub/GitLab].