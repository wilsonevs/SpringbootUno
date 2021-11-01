# SpringbootUno_DB

Connección a MYSQL
Archivo ---> Cambiar application.properties por application.yml
#0. Indicar porque puerte se inicia nuestra app
*server:
*  port: 8079

spring:
#1. Conexión a BD MySQL
*  datasource:
 *   url: jdbc:mysql://localhost:3306/curso_springboot?useSSL=false&serverTimeZone=UTC
 *   driverClassName: com.mysql.jdbc.Driver
 *   username: root
 *   password:
#2. Jpa nos permite resolver problemas de almacenamiento de los objetos en una base de datos relacional
*  jpa:
*    database-platform: org.hibernate.dialect.MySQL5InnoDBDialect
*    hibernate.ddl-auto: update
*    generate-ddl: true
*    show-sql: true
#3. Nos muestre los log de las consulta de la BD.
*logging:
*  level:
*    org:
*      hibernate:
*        SQL: debug

# Archivo build.gradle
	--> Implementamos dentro de dependencies --> runtimeOnly 'mysql:mysql-connector-java'

SWAGGER 3
Si están utilizando la versión 3.0.0 de swagger, se debe tener en cuenta lo siguiente:

En el archivo bundle.gradle se debe añadir las siguientes líneas
implementation "io.springfox:springfox-boot-starter:3.0.0"
compile “io.springfox:springfox-swagger-ui:3.0.0”

En la clase SwaggerConfig ya no hace falta añadir la anotación @EnableSwagger2

La url de acceso a la documentación es: {host}:{puerto} / {contexto} /swagger-ui/index.html

http://localhost:8079/wcone_market/api/swagger-ui/index.html
iNSTAALAR ESTAS DOS DEPEDENCIAS
https://mvnrepository.com/artifact/io.springfox/springfox-boot-starter/3.0.0
implementation "io.springfox:springfox-boot-starter:3.0.0"
https://mvnrepository.com/artifact/io.springfox/springfox-swagger-ui/3.0.0
implementation 'io.springfox:springfox-swagger-ui:3.0.0'
