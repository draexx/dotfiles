# Mis Configuraciones Personales (Dotfiles)

Este repositorio contiene mi colección personal de archivos de configuración para diversas herramientas y aplicaciones que uso en mi sistema operativo Linux y macOS. El objetivo es mantener un entorno de trabajo consistente, productivo y estéticamente agradable.

## Tabla de Contenidos

- Requerimientos
- Instalación
- Uso
- Detalles de las Configuraciones
- Herramientas Adicionales
- Agradecimientos

## Requerimientos

Para utilizar estas configuraciones, necesitarás tener instalados los siguientes programas. A continuación, se detallan los programas y cómo instalarlos en sistemas basados en Debian/Ubuntu (usando apt), Arch Linux (usando pacman) y macOS (usando brew).

### General

* zsh: Un potente intérprete de comandos.
  - sudo apt install zsh
  - sudo pacman -S zsh
  - brew install zsh

* oh-my-zsh: Un framework para gestionar la configuración de zsh.
  - Sigue las instrucciones en https://ohmyz.sh/

* starship: Un prompt minimalista, rápido y personalizable para cualquier shell.
  - sudo apt install starship (puede requerir un PPA)
  - sudo pacman -S starship
  - brew install starship

* fastfetch: Una herramienta para mostrar información del sistema de forma rápida.
  - sudo apt install fastfetch (puede requerir un PPA)
  - sudo pacman -S fastfetch
  - brew install fastfetch

* Hack Nerd Font: Fuente tipográfica usada en Kitty. Necesaria para los iconos.
  - Descarga desde https://www.nerdfonts.com/font-downloads y coloca en ~/.local/share/fonts/

* VSCode o Cursor: Editores de código.
  - Descargar desde https://code.visualstudio.com/ o https://cursor.sh/

* btop: Un monitor de sistema con una interfaz gráfica atractiva y moderna.
  - sudo apt install btop
  - sudo pacman -S btop
  - brew install btop

* glances: Un monitor de sistema en tiempo real.
  - sudo apt install glances
  - sudo pacman -S glances
  - brew install glances

* eza: Un reemplazo moderno para ls.
  - sudo apt install eza (puede requerir un PPA)
  - sudo pacman -S eza
  - brew install eza

* duf: Una utilidad para visualizar el uso del disco.
  - sudo apt install duf (puede requerir un PPA)
  - sudo pacman -S duf
  - brew install duf

* cmatrix: (Opcional) Un efecto de lluvia de código Matrix en la terminal.
  - sudo apt install cmatrix
  - sudo pacman -S cmatrix
  - brew install cmatrix

### Específicos de Configuración

#### CONKY

* Conky: Un monitor de sistema ligero para X.
  - sudo apt install conky-all
  - sudo pacman -S conky

* Lua: Necesario para algunos scripts de Conky.
  - sudo apt install lua5.3 (o la versión que necesite tu script)
  - sudo pacman -S lua

#### i3wm

* i3-wm: Un gestor de ventanas tiling.
  - sudo apt install i3
  - sudo pacman -S i3-wm

* i3status: Una utilidad para generar una barra de estado para i3.
  - sudo apt install i3status
  - sudo pacman -S i3status

* dmenu (o un lanzador compatible como rofi): Para lanzar aplicaciones.
  - sudo apt install dmenu o sudo apt install rofi
  - sudo pacman -S dmenu o sudo pacman -S rofi

* feh o nitrogen: Para gestionar fondos de pantalla.
  - sudo apt install feh o sudo apt install nitrogen
  - sudo pacman -S feh o sudo pacman -S nitrogen

#### Kitty

* Kitty: Un emulador de terminal rápido, con muchas funciones y acelerado por GPU.
  - sudo apt install kitty
  - sudo pacman -S kitty
  - brew install kitty

#### Zellij

* Zellij: Un multiplexor de terminal y entorno de trabajo.
  - cargo install --locked zellij (requiere Rust y Cargo)
  - sudo pacman -S zellij (puede estar en AUR)
  - brew install zellij

Nota: Algunos paquetes pueden tener nombres diferentes o requerir repositorios adicionales (como PPAs en Ubuntu, AUR en Arch Linux o Homebrew en macOS) dependiendo de la distribución y su versión.

## Instalación

A continuación se explica cómo instalar estas configuraciones en tu sistema.

ADVERTENCIA: Realiza una copia de seguridad de tus configuraciones actuales antes de proceder, ya que los siguientes comandos pueden sobrescribir archivos existentes.

1. Clona este repositorio:
   git clone https://github.com/draexx/dotfiles.git
   cd dotfiles

2. Copia los archivos de configuración:

   * Conky:
     mkdir -p ~/.config/conky
     cp -r conky/* ~/.config/conky/

   * i3wm:
     mkdir -p ~/.config/i3
     cp i3wm/config ~/.config/i3/config
     cp i3wm/i3status.conf ~/.config/i3/i3status.conf

   * Kitty:
     mkdir -p ~/.config/kitty
     cp kitty/kitty.conf ~/.config/kitty/kitty.conf
     La configuración es completamente autónoma — no requiere theme.conf ni colors.conf externos. Los colores ANSI y el esquema visual están integrados directamente en kitty.conf.

   * Zsh (.zshrc):
     Instala primero los plugins de oh-my-zsh:
     git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
     git clone --depth 1 https://github.com/marlonrichert/zsh-autocomplete.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autocomplete
     git clone https://github.com/zdharma-continuum/fast-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/fast-syntax-highlighting
     Luego copia el archivo de configuración:
     cp zsh/.zshrc ~/.zshrc
     source ~/.zshrc

   * Zellij:
     mkdir -p ~/.config/zellij
     cp zellij/config.kdl ~/.config/zellij/config.kdl
     cp zellij/layout.kdl ~/.config/zellij/layout.kdl

   * Starship (prompt de zsh):
     Starship se inicializa automáticamente desde el .zshrc. La configuración personalizada se encuentra en starship/starship.toml.
     mkdir -p ~/.config
     cp starship/starship.toml ~/.config/starship.toml

   * btop:
     mkdir -p ~/.config/btop
     cp btop/btop.conf ~/.config/btop/btop.conf

Importante: Revisa las rutas y los nombres de los archivos de configuración específicos de cada programa, ya que pueden variar ligeramente. Los comandos anteriores asumen las ubicaciones más comunes.

## Uso

Una vez que hayas instalado los programas requeridos y copiado los archivos de configuración, así es como puedes empezar a usarlos:

### Conky

Para iniciar Conky con una configuración específica, puedes ejecutarlo desde la terminal. Por ejemplo, para usar conky_maia:
conky -c ~/.config/conky/conky_maia

Puedes reemplazar conky_maia con el nombre de otro archivo de configuración de Conky que hayas copiado.

Para que Conky se inicie automáticamente con tu sesión de escritorio, puedes añadir el comando anterior a las aplicaciones de inicio de tu entorno de escritorio o gestor de ventanas.
- En i3wm: Añade exec --no-startup-id conky -c ~/.config/conky/tu_conky_config a tu archivo ~/.config/i3/config.
- En otros entornos (GNOME, KDE, XFCE): Busca la configuración de "Aplicaciones al inicio" o "Autostart" y añade el comando.

### i3wm

Para usar la configuración de i3wm:
1. Asegúrate de haber copiado el archivo config a ~/.config/i3/config.
2. Cierra la sesión actual de tu entorno de escritorio y, en la pantalla de inicio de sesión (display manager), selecciona "i3" como tu sesión antes de ingresar tu contraseña.
3. Si ya estás en una sesión de i3, puedes recargar la configuración con el atajo de teclado predeterminado Mod+Shift+r (donde Mod suele ser la tecla Alt o Super/Windows).

Revisa el archivo ~/.config/i3/config para conocer los atajos de teclado personalizados y otras configuraciones.

### Kitty

Kitty aplicará automáticamente la configuración de ~/.config/kitty/kitty.conf cada vez que inicies una nueva ventana de terminal.

- La configuración actual usa la fuente Hack Regular a 9.5pt con paleta de colores estilo GNOME Terminal (#171717 de fondo).
- Las pestañas se muestran en la parte superior con estilo powerline angled.
- Para recargar la configuración sin cerrar Kitty: Ctrl+Shift+F5.

Atajos de teclado:
- Ctrl+Shift+T = Nueva pestaña
- Ctrl+Shift+Q = Cerrar pestaña
- Ctrl+Shift+Right = Siguiente pestaña
- Ctrl+Shift+Left = Pestaña anterior
- Ctrl+Shift+Alt+T = Renombrar pestaña
- Ctrl+Shift+C = Copiar
- Ctrl+Shift+V = Pegar

### Zsh

El archivo zsh/.zshrc configura el entorno de shell completo con oh-my-zsh y los siguientes plugins:
- zsh-autosuggestions: Sugiere comandos basados en el historial mientras escribes.
- zsh-autocomplete: Autocompletado en tiempo real con menú interactivo.
- fast-syntax-highlighting: Resaltado de sintaxis en tiempo real en la línea de comandos.

Además incluye:
- fastfetch al iniciar la terminal para mostrar info del sistema.
- starship como prompt visual.
- Atajo alias ssh="kitty +kitten ssh" para mantener la fuente en conexiones remotas.
- Corrección del comportamiento de las teclas de flecha con zsh-autocomplete.
- Alias para eza que reemplazan a ls con una versión moderna y con iconos.

### Zellij

Zellij cargará su configuración desde ~/.config/zellij/config.kdl al iniciarse.
zellij

Si deseas iniciar Zellij con un layout específico:
zellij --layout ~/.config/zellij/layout.kdl

### Starship (Zsh Prompt)

Starship se inicializa automáticamente mediante la línea eval "$(starship init zsh)" incluida en el .zshrc. El prompt se aplica al abrir cualquier nueva terminal Zsh. La configuración personalizada se encuentra en ~/.config/starship.toml.

## Detalles de las Configuraciones

A continuación, se ofrece una breve descripción de cada conjunto de configuraciones incluidas en este repositorio.

### CONKY
Archivos de configuración para Conky, un monitor de sistema ligero y personalizable para X11.
- clock_rings_maia.lua: Script Lua para un widget de reloj con anillos.
- conky_lua_maia
- conky_maia
- conky_maia1
- conky_shortcuts_live_maia
- conky1.10_shortcuts_maia

==================== CAPTURA DE PANTALLA PARA CONKY ====================
![Vista previa de Conky](screenshots/conky_preview.png)
(Coloca aquí tu captura de pantalla de Conky en acción)

### i3wm
Configuración personalizada para i3-wm, un gestor de ventanas tiling para X11.
- config: Archivo principal de configuración de i3.
- config-i3: Posiblemente una variante o copia de seguridad de la configuración.
- i3status.conf: Configuración para i3status, usado para generar la barra de estado de i3.

==================== CAPTURA DE PANTALLA PARA I3WM ====================
![Vista previa de i3wm](screenshots/i3wm_preview.png)
(Coloca aquí tu captura de pantalla de i3wm en acción)

### Kitty
Configuración para Kitty, un emulador de terminal rápido y con aceleración GPU.
- kitty.conf: Configuración completa y autónoma. Incluye fuente, colores, pestañas y atajos de teclado en un solo archivo.
  * Fuente: Hack Regular, 9.5pt
  * Tema: Colores estilo GNOME Terminal con paleta ANSI completa (16 colores) integrada
  * Pestañas: Barra superior con estilo powerline angled
  * Opacidad: 90% de transparencia de fondo

NOTA: Los archivos theme.conf y colors.conf ya no son necesarios — todo está integrado directamente en kitty.conf.

==================== CAPTURA DE PANTALLA PARA KITTY ====================
![Vista previa de Kitty](screenshots/kitty_preview.png)
(Coloca aquí tu captura de pantalla de Kitty en acción)

### Zsh
Configuración completa del entorno de shell para zsh con oh-my-zsh.
- zsh/.zshrc: Archivo de configuración principal de zsh.
  * Plugins: zsh-autosuggestions, zsh-autocomplete, fast-syntax-highlighting
  * Prompt via Starship (eval "$(starship init zsh)")
  * fastfetch al inicio de la terminal
  * Alias python -> python3 y ssh -> kitty +kitten ssh
  * Alias para eza (reemplazo de ls)
  * Configuración de NVM para Node.js

==================== CAPTURA DE PANTALLA PARA ZSH ====================
![Vista previa de Zsh](screenshots/zsh_preview.png)
(Coloca aquí tu captura de pantalla de la terminal Zsh con Starship)

### Zellij
Configuración para Zellij, un multiplexor de terminal y entorno de trabajo.
- config.kdl: Archivo principal de configuración de Zellij, usando KDL (KDL Document Language).
- layout.kdl: Define un layout específico para las sesiones de Zellij.

==================== CAPTURA DE PANTALLA PARA ZELLIJ ====================
![Vista previa de Zellij](screenshots/zellij_preview.png)
(Coloca aquí tu captura de pantalla de Zellij en acción)

### btop
Configuración para btop, un monitor de sistema con interfaz gráfica.
- btop.conf: Archivo de configuración principal que define colores, actualización, y qué información se muestra.

==================== CAPTURA DE PANTALLA PARA BTOP ====================
![Vista previa de btop](screenshots/btop_preview.png)
(Coloca aquí tu captura de pantalla de btop en acción)

### Starship
Configuración personalizada del prompt para Zsh.
- starship.toml: Archivo de configuración que define el formato, colores y módulos del prompt.

==================== CAPTURA DE PANTALLA PARA STARSHIP ====================
![Vista previa de Starship](screenshots/starship_preview.png)
(Coloca aquí tu captura de pantalla del prompt de Starship)

## Herramientas Adicionales

Estas herramientas son opcionales, no requieren configuración específica, pero mejoran la experiencia general.

### cmatrix (Efecto Matrix)
Un clásico para divertirse en la terminal.
- Instalación: sudo apt install cmatrix, sudo pacman -S cmatrix, o brew install cmatrix.
- Uso recomendado: cmatrix -b -C cyan (efecto azul en lugar de verde).

### glances (Monitor en tiempo real)
Alternativa moderna a top y htop.
- Instalación: sudo apt install glances, sudo pacman -S glances, o brew install glances.
- Uso recomendado: Simplemente ejecuta glances para ver el monitor interactivo. Puedes cambiar el tema presionando 2 (oscuro) o 5 (claro).

### duf (Uso de disco con interfaz mejorada)
Alternativa visual a df.
- Instalación: sudo apt install duf, sudo pacman -S duf, o brew install duf.
- Uso recomendado: duf o duf --only-fs ext4,ntfs,apfs para filtrar discos.

## Agradecimientos

Este proyecto se ha inspirado en el trabajo de muchas personas en la comunidad de personalización de Linux.

- Agradecimientos a la comunidad de r/unixporn por la inspiración constante.
- Inspirado por los dotfiles de otros proyectos de código abierto.

---

Si encuentras algún problema o tienes sugerencias, no dudes en abrir un issue en el repositorio.