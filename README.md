# Template para crear ETL's
## Requisitos
### Python
La versión de Python instalada en el servidor es la `3.6.9`, asegurar que los paquetes utilizados sean compatibles con dicha versión.

### Ambiente virtual
Si se utiliza un ambiente virtual usar [venv](https://docs.python.org/3/tutorial/venv.html) y llamarlo /venv, este ambiente ya esta agregado al archivo `.gitignore` para que no se incluya en el repositorio final.

### Requerimientos
Utilizar un [archivo de requerimientos](https://pip.pypa.io/en/stable/user_guide/#requirements-files) para la instalación de los paquetes en el ambiente virtual.

### Archivo de ejecución
Al ejecutarse el ETL se mandará llamar el archivo de nombre `etl/__main__.py` por lo que esa es la entrada.

### Repositorio
Clonar este repositorio y utilizarlo como guía, después cambiar el repositorio a uno personal utilizando el comando `git remote set-url` y dar acceso de lectura al usuario [geroblesv](https://github.com/geroblesv/)

### Agendar ejecución
La ejecución de los ETL's es mediante `CRON`, para agendar la ejecución automatizada del ETL favor de tomar [esta guía](https://crontab.guru/) y envíar el horario de por correo a la cuenta de correo gerardo.robles@udem.edu.mx.

## Recomendaciones
### Datos sensibles
Utilizar [config parser](https://docs.python.org/3/library/configparser.html) para variables sensibles como nombre de usuario, contraseñas, puertos, servidores, etc.
### Log
Imprimir a consola solo lo necesario para no llenar el Log con información basura.
### Código
Seguir las recomendaciones de la [guía de Python](https://www.python.org/dev/peps/pep-0008/)