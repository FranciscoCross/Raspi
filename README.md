# Servidor SmartPlant Raspberry Pi 4
Este repositorio contiene los archivos de configuración correspondientes al servidor Raspberry Pi 4 del proyecto SmartPlant (también llamado PowerPot), para aplicar prácticas DevSecOps al desarrollo IoT, en este caso la aplicación se trata de un sistema de monitoreo de variables aptas para cultivo.

El repositorio que corresponde al dispositivo ESP32 es: [SmartPlant ESP32](https://github.com/FeedehC/SmartPlant/)

## Guía de Configuración
A continuación se describe cómo partir de este proyecto para iniciar su propio servidor para ofrecer los servicios necesarios para el proyecto SmartPlant. Se recomienda utilizar una **Raspberry Pi 4** con **Ubuntu Server 22.04**, aunque hay archivos alternativos para hacerlo con una PC.

### Fork del Repositorio
El primer paso es forkear (bifurcar o "copiar") este repositorio en su cuenta de GitHub.

IMAGEN

Una vez listo el fork, clone el repositorio, preferentemente usando SSH.

### Docker Compose
El próximo paso es intalar Docker Compose. En distribuciones basadas en Ubuntu se puede instalar con el comando:
```
sudo apt install docker-compose
```

### Portainer
Una herramienta muy útil para administrar los contenedores de Docker que se ejecutan en el servidor es Portainer. Esta herramienta ofrece una interfaz web que permite visualizar, reiniciar y detener contenedores con problemas. Para instalarla ejecutar el comando:
```
docker run -d  -p 9000:9000 --name=portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data --network monitoreo_cosas portainer/portainer-ce:latest
```
Para ver la interfaz del programa ingrese a un navegador y coloque en la barra de direcciones IP_RASPI:9000, donde IP_RASPI es la dirección IP privada de la Raspberry Pi que ejecuta Portainer.

## Runner Self-Hosted
El Runner es el servicio que ejecuta las tareas de los Workflows de GitHub Actions. Ejecuta la compilación, testeo y configuración del binario resultante cada vez que haya una nueva versión disponible en el repositorio ESP32 (LINK).

### Credenciales
Antes de poder iniciar el Runner se deben configurar las credenciales. Para esto se debe acceder a la carpeta **/Docker/Github-docker-runner** y crear un archivo llamado ".env" en el cual se indican las siguientes variables de entorno.
```
RUNNER_REPOSITORY_URL=Link del Repositorio ESP32
GITHUB_ACCESS_TOKEN=Token
```

Debe crear un GitHub Access Token en su cuenta de GitHub, como se indica en la imagen.

IMAGEN


Para iniciarlo, dirigirse a la carpeta /Docker/Github-docker-runner y ejecutar el comando:
```
docker-compose up -d
```

Al generar un nuevo token, debe elegir que permisos asignarle, asegúrese de tildar los siguientes:

- **repo**
- **workflow**


### Puertos
Para tener acceso a los servicios públicos se debe configurar el Router para redireccionar el tráfico entrante por los puertos que se indican a continuación.
- **1883 para MQTT**
- **443 para el Servidor Web de Actualizaciones de Firmware**
Todos los puertos deben redireccionar el tráfico hacia la IP privada de la Raspberry Pi.

Todo con Docker-Compose
- Runner self hosted
- Update server ???
- 

