# WCONE_MARKET

#### ¡SUGERENCIA!
Cambiar **application.properties** por la extención "YML", quedari de la siguiente forma **application.yml**

***PERFIL***
```application.yml
spring:
  profiles:
    active: dev
```
\
***CAMBIAR EL PUERTO.***
```application.yml
server:
  port: 8079
```
\
***CAMBIAR RUTA URL.***
```application.yml
server:
  servlet:
    context-path: /Path
```

## CONEXIÓN A MySQL
### Datasource
```application.yml
spring:
  #1. Conexión a BD MySQL
  datasource:
    url: jdbc:mysql://localhost:3306/wcone_market?useSSL=false&serverTimeZone=UTC
    driverClassName: com.mysql.jdbc.Driver
    username: root
    password:

```
### Jpa
```application.yml
  #2. Jpa nos permite resolver problemas de almacenamiento de los objetos en una base de datos relacional
  jpa:
    database-platform: org.hibernate.dialect.MySQL5InnoDBDialect
    hibernate.ddl-auto: update
    generate-ddl: true
    show-sql: true
```
### Logging
```application.yml
#3. Nos muestre los log de las consulta de la BD.
logging:
  level:
    org:
      hibernate:
        SQL: debug
```


## SWAGGER 3
**INSTALAR LAS DOS DEPEDENCIAS.**
| Link             | Dependencía                                                                |
| ----------------- | ------------------------------------------------------------------ |
| https://mvnrepository.com/artifact/io.springfox/springfox-boot-starter/3.0.0 | `io.springfox:springfox-boot-starter:3.0.0` |
| https://mvnrepository.com/artifact/io.springfox/springfox-swagger-ui/3.0.0 | `io.springfox:springfox-swagger-ui:3.0.0` |

## build.gradle
```application.yml
dependencies {
// swagger2
	implementation "io.springfox:springfox-boot-starter:3.0.0"
	implementation 'io.springfox:springfox-swagger-ui:3.0.0'
}
```

**LA URL DE ACCESO A LA DOCUMENTACIÓN ES =**
`{host}:{puerto} / {contexto} /swagger-ui/index.html`
