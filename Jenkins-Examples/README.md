# Ejemplo complejo de CI y CD
##### https://community.sonarsource.com/t/is-sonarqube-server-6-7-3-supporting-npm-angular-jenkins/4789/3
##### https://community.sonarsource.com/t/is-sonarqube-server-6-7-3-supporting-npm-angular-jenkins/4789/2
##### https://www.youtube.com/watch?v=SWl_XicACyk

Las actividades realizadas consisnten en:

### 1. Utilizar un trigger que notifique a Jenkins sobre cambios en el repositorio.
### 2. Utilizar Git para objetener el repositorio y una rama pre-definida.
### 3. Construir el proyecto utilizando NodeJS y Scanearlo con SonarQube.
### 4. Obtener las metricas de calidad para continuar con los siguientes pasos.
### 5. Crear la imagen del proyecto utilizando docker
### 6. Desplegar el conedor utilizando la imagen creada del proyecto.

# Confiruaciones del Entorno DEVOPS

## SonarQube.

### 1. Cambiar contraseña de usuario.
### 2. Crear un TOKEN para Jenkins.
### 3. Cambiar los proyecto a privados.


# Jenkins

Una vez instalado Jenkins se deben instalar plugins.

## Plugins necesarios.

#### 1. SonarQube
#### 2. SonarQube Scanner (2.9)

#### 3. NodeJS Plugin (1.3.3)
#### 4. Gitlab Plugin (1.5.13)

## Configuracion de Jenkins

#### 1). Configurar Servidor de SonarQube 

Configurar el Sistema -> SonarQube servers
```
Name: SonarQube
URL del servidor: http://sonarqube:9000
```
Server authentication token: Activar la opcion y agregar el TOKEN generado desde SonarQube.

### 2). Configurar Herramientas Globales

Configurar el Sistema -> Global Tool COnfiguration

#### SonarQube Scanner
```
SonarQube Scanner
Name: SonarScanner

[*] Instalar automáticamente
```
#### NodeJS
```
NodeJS
Nombre: NodeJS

[*] Instalar automáticamente
```

### 3). Configurar Credenciales 

Credenciales -> System -> Global credentials -> Add credentials

##### Kind: Username with password

```
Username: <usuario_de_gitlab>

Password: <password_de_gitlab>

ID: <nombre_credencial> 

```
# Gitlab

## Creacion de Trigger en Repositorio.

### Repositorio -> Integracion



Configurar:

```
URL: <http://servirdor_jenkins/project/nombre_de_proyecto>

Secret Token: <token generado en jenkins>

```

Trigger:

#### Seleccionar : Push events -> agregar el nombre de la rama (branch).



