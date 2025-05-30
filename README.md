# JYV_TOOLS (Alquiler de Herramientas)

Es un aplicativo que permite la gestion de alquileres de herramienta y equipos de construcciones para 
contratista, particulares y empresas  que requieren de esta maquinaria sin tener la necesidad de comprarlas.

## TECNOLOGIAS UTILIZADAS

* Spring boot(MVC)
* Java 
* PostgreSQL
* JWT
* HTML(Thymeleaf)
* CSS
* Javascript

## Instrucciones para clonar

Para poder abrir el aplicativo en tu maquina local deberas clonar el repositorio desde el control de versiones github  o el de tu preferencia
utilizabndo el siguiente comando 
```
git clone  https://github.com/YurleyBG/Proyecto_SpringBootFinal.git
```
despues de tener clonado , abrir en tu editor de codigo preferido , en este caso aplicaria a visual studio code 
descargaremos las siguientes extensiones para poder ejecutar :
```
  1. Extension Pack for Java
  2. Spring Boot Dashboard
  3. Spring Boot Tools
  4. Spring Initializr Java Support
  5. Spring Boot Extension Pack

```
Despues de esto  podremos correr el codigo  siguiendo estos pasos:

![explication](https://github.com/user-attachments/assets/212ae34e-eea9-47cf-8039-ec82e5a12f8c)

## Dependencias utilizadas
Estas dependencias se encuentran aplicadas en el pom.xml del archivo springboot:

###  Dependencias para el Jwt
```
    <dependency>
			<groupId>io.jsonwebtoken</groupId>
			<artifactId>jjwt-api</artifactId>
			<version>0.12.3</version>
		</dependency>

		<dependency>
			<groupId>io.jsonwebtoken</groupId>
			<artifactId>jjwt-jackson</artifactId>
			<version>0.12.5</version>
		</dependency>

		<dependency>
			<groupId>io.jsonwebtoken</groupId>
			<artifactId>jjwt-impl</artifactId>
			<version>0.12.6</version>
		</dependency>

```
### Dependencias para PostgreSQL
```
    <dependency>
			<groupId>org.postgresql</groupId>
			<artifactId>postgresql</artifactId>
			<scope>runtime</scope>
		</dependency>

```
### Dependencias para Thymeleaf(Motor de plantilla)
```
	  <dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-thymeleaf</artifactId>
		</dependency>

```

## Estructura del proyecto:

### Application: 
+ service: Aquí se implementaron las reglas y operaciones que definencomo actuara cada endpoint.
  
###  Auth:
Tiene lo relacionado con el jwt y spring security.

### Config: 
Tiene las configuracion y authorizaciones para el sistema.

###  Domain:
+ DTO: Response y Request
+ Entity: tiene todas la clases con sus repectivos atributos y relaciones.
  
###  Infraestructure:
+ Controllers : tiene todo el manejo o  endpoints de las apiRest.
+ Repository: interfaz definida para el acceso de datos de una entidad especifica.
+ Repository Impl: implementacion completa .
+ Util : contienes la excepciones personalizadas y globales

###  JWT: 
contiene todo lo relacionado con las filtraciones y el jwt service.

###  Resource:
+ static:
  	+ Css: contienes los estilos para las paginas.
  	+ Js: contiene los javascripts para el consumo de apis.
  	+ Img: contiene las imagenes locales.
+ Templates:
  Aqui se encuentras todos los archivos html implementados que se imlementaron con thymeleaf.
  

## Configuración del application.properties

0. Nombre de la aplicación Este nombre se usa para identificar la aplicación en entornos de monitoreo o registros.
```
    spring.application.name=jyv_tool

```
1. Configuración de la Base de Datos PostgreSQL
```
    spring.datasource.url=jdbc:postgresql://localhost:5432/JYV_TOOL
    spring.sql.init.encoding=UTF-8
    spring.datasource.username=postgres
    spring.datasource.password=campus2023
    spring.datasource.driver-class-name=org.postgresql.Driver

```
2.Configuración de JPA/Hibernate y Nivel de Logging
```

  spring.jpa.show-sql=true
  spring.jpa.properties.hibernate.format_sql=true
  spring.jpa.hibernate.ddl-auto=create-drop
  logging.level.org.springframework.security=DEBUG
  logging.level.com.example.jyv_tool=DEBUG


```
##  Diagrama

![image](https://github.com/user-attachments/assets/92aed5b8-70c9-4770-8098-be3d876e5e16)


##  Explicación de la autenticación y roles

Se implemento el JWT(json web token) y spring security  para generar la autenticaciones y permisos.

Cabe recalcar que este proyecto fue manejado por el motor de plantillas thymeleaf para la implemetacion del HTML , lo que hizo que fuera necesario el manejo de cookies
para la autenticacion directa desde el frontend , pero de igual manera  tambien permite la autenticacion desde  postman en el encabezado de Authorization: Bearer.

![image](https://github.com/user-attachments/assets/d33f4628-5270-441a-9565-7a4d67d219da)

El proyecto aun esta en proceso en lo que respecta a la parte del frontend , pero el login y registro esta totalmente funcional con la autorizacion de permisos.

### ROLES PERMITIDOS
+ Cliente
+ Proveedor
+ Administrador

### PERMISOS PARA TODOS

+ bienvenida
+ Login
+ Registro

### PERMISOS PARA CLIENTES

+ Pagina principal(herramientas disponibles)
+ Reservas
+ Pagos
+ Historial
+ perfil

### PERMISOS PARA PROVEEDORES

+ Pagina principal(herramientas)
+ Gestionar reservas
+ generar facturas
+ Agrega y eliminar herramientas
+ perfil
    
### PERMISOS PARA ADMINISTRADORES

+ Pagina principal(clientes , proveedores)
+ gestion de reportes
+ modulo de supervision
+ perfil

El usuario  podra ver una vista de bienvenida que le dara las opciones de registro y login. 
podra registrarse segun su rol despues sera ridereccionado al apartado de login para acceder a la vista
segun el rol. EL login se manejo con cookies para poder dar los permisos.

## ENDPOINTS DE LAS ENTIDADES(CRUD)

* Alquiler: Delete,Get,Post,Patch
* Usuario: Delete,Get,Post,Patch
* Reserva: Get,Post,Patch
* Pago: Get,Post,Patch
* Multas: Get,Post,Patch
* Inventario: Get,Patch
* Herramientas: Delete,Get,Post,Patch
* Factura: Delete,Get
* Entrega: Get,Post,Patch
* Devoluciones: Get,Post
* Otras: Get

## SWAGGER

En resource se encuentra una carpeta llamada yml dentro de ella se encuentra el archivo swagger.yml que contiene la documentacion de la api.
si quiere ver de mejor manera y con mas detalles entra al siguiente link 

[editor.swagger.io/](https://editor.swagger.io/))


y pega la informacion del archivo swagger.yml y automaticamente la podras ver.

Este es un ejemplo de lo que podras ver: 

![image](https://github.com/user-attachments/assets/34ea91d7-2963-40ef-bbfe-bd8edae61d35)

![image](https://github.com/user-attachments/assets/26869198-2212-4fff-863c-76890b67db82)

![image](https://github.com/user-attachments/assets/4c792b5f-8676-499b-ae7b-fc2360643329)
![image](https://github.com/user-attachments/assets/f649ea0a-197a-4454-943b-456b95c74330)
![image](https://github.com/user-attachments/assets/2276f1a2-7fcb-4dcf-b728-e993fc7a3d73)
![image](https://github.com/user-attachments/assets/9426e729-3028-44bb-9039-22808dcd0aba)
![image](https://github.com/user-attachments/assets/0a2cbdca-cd4a-41f4-90f4-f4bf3cc7d5ed)

![image](https://github.com/user-attachments/assets/aa6bf4af-c24e-4a58-a08c-56f69a4fb81a)
![image](https://github.com/user-attachments/assets/e57dbb0c-9165-4f9b-a7f3-7cdbc99b0be7)
![image](https://github.com/user-attachments/assets/41db2cb8-a4ef-4955-8bd5-b7e2d6dc81a3)
![image](https://github.com/user-attachments/assets/bc210330-9f96-4e2f-b544-084964a9bd05)





## DATOS IMPORTANTES
+ El HTMLCONTROLLER contiene cada uno de los endpoints para poder acceder a los html.
+ Para insertar los datos debes descomentar lo siguiente esta en application.propierities:
```

##spring.jpa.hibernate.ddl-auto=update
##spring.sql.init.mode=always


```

y volver a comentar para que no se dupliquen las insert en cada ejecucion.

+ El data.sql que esta en templates contiene los inserts.

+ Se implemento el manejo de CORS para poder hacer el consumo de las apis.

  

## Guía para ejecutar pruebas unitarias y de integración

Estos son algunos de los EndPoints

post: Puedes utilizar postman o el servidor de tu preferencia para una mejor experiencia  o solo utilizar directamente .

* Filtrar por categoria
 
http://localhost:8080/Api/herramienta?category=Electricas

* Obtener Herramientas disponibles
  
http://localhost:8080/Api/herramienta?available=true

+ Obtener usuarios
  
http://localhost:8080/Api/usuario

+ Registrar nuevos usuarios
  
http://localhost:8080/auth/registrar

![image](https://github.com/user-attachments/assets/a2e6af58-3b93-484a-bc76-9bf145268314)


+ Iniciar sesion
  
http://localhost:8080/auth/login

![image](https://github.com/user-attachments/assets/6e7aea68-e662-4580-8004-4f8e10c0d86d)


+ Obtener Herramientas

http://localhost:8080/Api/herramienta

+ Obtener Reservas
  
http://localhost:8080/Api/reserva

## Mas Informacion

[Ir al sitio ](https://www.notion.so/JYV_TOOLS-1fec7817025d80d589f6c1e6ae54a35e?pvs=4)

## Proyecto desarrollado por 
  + Yurley Botello
  + Valentina Molina
  + Jhonatan Omaña
    






