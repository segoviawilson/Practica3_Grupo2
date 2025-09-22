## INTEGRANTES.
| Nombre | Cargo | URL GitHub |
|---|:---:|---:|
| Daniel Alquinga | :technologist: Desarrollador | https://github.com/superdavi/Practica3_Grupo2.git |
| Daniel Baldeon | :technologist: Desarrollador | https://github.com/debpdhs/Practica3_Grupo2.git |
| Bryan Miño | :technologist: Desarrollador | https://github.com/bmiomi/tarea3-grupo2.git |
| Wilson Segovia | :technologist: Desarrollador | https://github.com/segoviawilson/Practica3_Grupo2.git |
| Leonardo Tuguminago | :technologist: Desarrollador | https://github.com/ltuguminago/fastapi-app.git |

# 1. Análisis de vulnerabilidades con docker scout mediante un flujo de github actions

Con base en el laboratorio de fastapi-app, deberan subir la imagen que le corresponde a su grupo y las aplicaciones a su repositorio de github. Construir la imagen, subir a docker hub y realizar el análisis de vulnerabilidades con docker scout mediante un flujo de github actions.

# 2. Configuración e Instalación

### PASO 1: 📂 Estructura de Archivos

<img width="222" height="185" alt="structura fastapi" src="https://github.com/user-attachments/assets/9e959e1b-bfc3-4a77-b489-b578ade1ac24" />


### PASO 2: Iniciar sessión en DockerHub y crear repositorio

<img width="946" height="553" alt="Crear repositorio DockerHub" src="https://github.com/user-attachments/assets/38ceed27-051c-4595-9506-e0a57ea78ddf" />

### PASO 3: En la termina, iniciar sessión con las credenciales de DockerHub

```bash
docker login -u ltuguminago
```

**Salida Esperada**

<img width="554" height="168" alt="image" src="https://github.com/user-attachments/assets/3d369e43-5b55-428e-8938-f1ac0f928410" />


### PASO 4: Construir imagen de Docker MultiStage

```bash
docker build -t hello-multistage -f Dockerfile .
```

**Salida Esperada**

<img width="553" height="252" alt="image" src="https://github.com/user-attachments/assets/5603e67a-f627-4d7e-866a-1d4f33ec1d1c" />


### PASO 5: Revisamos la imagen construida

```bash
docker images
```

**Salida Esperada**

<img width="554" height="129" alt="image" src="https://github.com/user-attachments/assets/394cac2b-4e18-4b51-a283-8b94fb3c51e6" />


### PASO 6: Tagear la imagen "usuario_DockerHub/repositorio"

```bash
docker tag hello-multistage:latest ltuguminago/fastapi-app:v1
```

**Salida Esperada**

<img width="554" height="132" alt="image" src="https://github.com/user-attachments/assets/f1bf0c5c-5a95-48a7-a790-e3f66b735fee" />


### PASO 7: Subir imagen al DockerHub

```bash
docker push ltuguminago/fastapi-app:v1
```

**Salida Esperada**

<img width="553" height="170" alt="image" src="https://github.com/user-attachments/assets/767d4095-fc44-42f6-814e-4fb568c1050b" />


### PASO 8: Revizar la imagen subida en el repositorio de DockerHub

<img width="554" height="323" alt="image" src="https://github.com/user-attachments/assets/47960375-54f3-4eaa-ae66-1bab8e46f04a" />


### PASO 9: Iniciar sessión en GitHub y crear repositorio

<img width="554" height="285" alt="image" src="https://github.com/user-attachments/assets/d9660a02-3237-4e88-9066-814b89bc9799" />


### PASO 10: El repositorio debe contener los siguientes archivos

<img width="554" height="317" alt="image" src="https://github.com/user-attachments/assets/f3769194-bd69-4179-be32-ce28f036f64c" />


### PASO 11: Ingresar al siguiente directorio

- Setting/secrets and variables/Actions

### PASO 12. Crear las variables con las credenciales deL DockerHub

```bash
DOCKERHUB_USERNAME
DOCKERHUB_TOKEN
```

**Salida Esperada**

<img width="1197" height="774" alt="secrets and varibles" src="https://github.com/user-attachments/assets/ed654656-0c58-458f-a643-62bb0fca9e69" />

### PASO 12: Ingresar al siguiente directorio

- Action/Docker image/ Configure

**Salida Esperada**

<img width="554" height="353" alt="image" src="https://github.com/user-attachments/assets/0a8516c5-2dca-4cce-b7a8-1372bb5378b0" />





### PASO 13: Reemplazar el contenido del workflows actual por el contenido del archivo fastapi.ylm

- Modificar el parametro IMAGE_NAME con el usuario del DockerHub + el nombre del repositorio.

```bash
IMAGE_NAME: ltuguminago/fastapi-app
```

- Modificar el parametro push con el valor de true, para que la imagen suba al DockerHub

```bash
push: true
```

- Guardar el archivo con el nombre "scout.yml"

<img width="554" height="340" alt="image" src="https://github.com/user-attachments/assets/594e8588-e108-4b36-b7a6-ec6721b7f994" />


### PASO 14: Ingresar al siguiente directorio "Action", para ver ejecutandose el workflows.

<img width="553" height="280" alt="image" src="https://github.com/user-attachments/assets/887157d9-a5be-43d2-9876-48e8416f9b7b" />


### PASO 15: Ingresar al build-and-analyze

<img width="554" height="527" alt="image" src="https://github.com/user-attachments/assets/bf275737-3dc2-4ef1-b557-94c0ab2ff683" />


### PASO 16: Terminada la ejecución workflows, finalmente se puede revisar el reporte docker-scout-report, descargando el archivo.

<img width="554" height="431" alt="image" src="https://github.com/user-attachments/assets/b8b603e7-5897-4d9f-a860-af0f3aa411fe" />

<img width="554" height="377" alt="image" src="https://github.com/user-attachments/assets/1963381d-8502-48b3-8ddd-477c3fd94bfa" />


## PASO 17. Visualizar el reporte

<img width="554" height="358" alt="image" src="https://github.com/user-attachments/assets/4a394e36-222f-40d4-a612-2bf64b63ec4f" />

## PASO 18. Revisar en DockerHub, la imagen subida.

<img width="554" height="351" alt="image" src="https://github.com/user-attachments/assets/e87ab904-8f6b-422f-b3fc-0903f8a77504" />



# 3. Conclusiones

- La implementación de Docker Scout dentro de GitHub Actions permite automatizar completamente el análisis de vulnerabilidades en imágenes Docker, integrando la seguridad directamente en el pipeline de CI/CD.

- Al ejecutar el análisis en cada push al repositorio, se identifica proactivamente vulnerabilidades en etapas tempranas del desarrollo, reduciendo riesgos de seguridad en producción.

- Docker Scout proporciona visibilidad completa sobre las vulnerabilidades en todas las capas de la imagen, facilitando la identificación de dependencias problemáticas en la aplicación FastAPI.

- GitHub Actions proporciona registros detallados de cada ejecución, creando un historial auditable de los estados de seguridad de la aplicación a lo largo del tiempo.
