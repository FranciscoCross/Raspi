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

Portainer
docker run -d  -p 9000:9000 --name=portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data --network monitoreo_cosas portainer/portainer-ce:latest

Forwardear Puertos:
MQTT 1883
Webserver 443

Todo con Docker-Compose
- Runner self hosted
- Update server ???
- 

