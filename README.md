# Template para crear ETL's
## Requisitos
### Python
La versión de Python instalada en el servidor es la `3.6.9`, asegurar que los paquetes utilizados sean compatibles con dicha versión.

### Ambiente virtual
Si se utiliza un ambiente virtual usar [venv](https://docs.python.org/3/tutorial/venv.html) y llamarlo /venv, este ambiente ya esta agregado al archivo `.gitignore` para que no se incluya en el repositorio final.  
Ejemplo:
```shell
python -m venv venv
```

Activar el ambiente de la siguiente forma:  

Windows
```bash
venv\Scripts\activate.bat
```

Mac/Linux
```bash
source venv/bin/activate
```

### Requerimientos
El servidor utiliza ambientes virtuales, por lo que es necesario utilizar un [archivo de requerimientos](https://pip.pypa.io/en/stable/user_guide/#requirements-files) para la instalación de los paquetes en dicho ambiente.  
Ejemplo:
```shell
pip freeze > requirements.txt
```

### Archivo de ejecución
Al ejecutarse el ETL se mandará llamar el archivo de nombre `etl/__main__.py`, puedes cambiar el nombre de la carpeta pero el archivo es obligatorio con la estructura proporcionada.  
Ejemplo:
```python
import app

if __name__ == '__main__':
    # Aquí puedes mandar llamar métodos de otros módulos.
    app.run()
```

### Credenciales de Banner
Hay que crear un archivo de configuración con las credenciales de Banner llamado `config_banner.ini` y dejarlo en la carpeta raíz del proyecto siguiendo esta estructura y sustituyendo tu usuario y contraseña en donde dice `tu_usuario_de_banner` y `tu_password_de_banner`:  
```ini
[db]
banner_username = tu_usuario_de_banner
banner_password = tu_password_de_banner
```
Este archivo esta agregado en el archivo `.gitignore` por lo que no se mandaran tus credenciales al servidor y sera remplazado localmente por un archivo de configuración local.

### Repositorio
Clonar este repositorio y utilizarlo como guía, después cambiar el repositorio a uno personal utilizando el comando `git remote set-url` y dar acceso de lectura al usuario [geroblesv](https://github.com/geroblesv/)

### Agendar ejecución
La ejecución de los ETL's es mediante `CRON`, para agendar la ejecución automatizada del ETL favor de tomar [esta guía](https://crontab.guru/) y envíar el horario de por correo a la cuenta de correo gerardo.robles@udem.edu.mx.

## Recomendaciones
### Datos sensibles
Utilizar [config parser](https://docs.python.org/3/library/configparser.html) para variables sensibles como nombre de usuario, contraseñas, puertos, servidores, etc.  
Ejemplo:
```python 
from configparser import ConfigParser

config = ConfigParser()
config.read(Path(__file__).resolve().joinpath('config.ini'))
```
Puedes agregar el archivo de configuración a tu archivo `.gitignore` y enviarlo por correo para que los datos no estén publicados en el repositorio.
### Log
Imprimir a consola solo lo necesario para no llenar el Log con información basura, imprimir en log hace lento el proceso.
### Código
Seguir las recomendaciones de la [guía de Python](https://www.python.org/dev/peps/pep-0008/)
### Lectura y escritura de archivos
Utilizar `Path` para leer y escribir archivos.  
Ejemplo:
```python
file = Path(__file__).resolve().joinpath('file.txt')
```
