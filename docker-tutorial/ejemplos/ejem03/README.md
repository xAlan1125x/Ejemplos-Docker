Informe de inconvenientes de portabilidad

Incompatibilidad de comandos: El script original usaba chmod +x, un comando nativo de Linux que en Windows PowerShell tira un error de "no se reconoce el término".

Interpretación errónea de rutas: Al ejecutar el .sh en Git Bash, el entorno intentó traducir rutas virtuales (/var/lib/mysql) mezclándolas con rutas locales de Windows, lo que rompió el montaje.

Dependencia del directorio actual ($(pwd)): Si ejecutas el script estando parado por accidente en System32, el script intenta crear carpetas allí y el sistema operativo lo rebota por "Acceso denegado".