# WCONE_MARKET

Configuración del proyecto del lenguaje java con el poderoso framework Spring boot.




## APPLICATION.YML
#### ¡SUGERENCIA!

Cambiar **application.properties** por la extención "YML", **application.yml**. Nos brindara un manejo mucho mas legible.

Se pueden especificar varias propiedades dentro de su application.propertiesarchivo, dentro de su application.ymlarchivo o como interruptores de línea de comando. Este apéndice proporciona una lista de propiedades comunes de Spring Boot y referencias a las clases subyacentes que las consumen.

#### DOCUMENTACIÓN
Formato = [YAML](https://www.baeldung.com/spring-boot-yaml-vs-properties)\
Comunes de la aplicación = 
1.[PROPERTIES](https://docs.spring.io/spring-boot/docs/current/reference/html/application-properties.html),
2.[PROPERTIES](https://docs.spring.io/spring-boot/docs/1.1.6.RELEASE/reference/html/common-application-properties.html)

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
| [SpringFox Boot Starter](https://mvnrepository.com/artifact/io.springfox/springfox-boot-starter/3.0.0) | `io.springfox:springfox-boot-starter:3.0.0` |
| [SpringFox Swagger UI](https://mvnrepository.com/artifact/io.springfox/springfox-swagger-ui/3.0.0) | `io.springfox:springfox-swagger-ui:3.0.0` |

### build.gradle
```application.yml
dependencies {
// swagger2
	implementation "io.springfox:springfox-boot-starter:3.0.0"
	implementation 'io.springfox:springfox-swagger-ui:3.0.0'
}
```

### Maven

```application.yml
<!-- https://mvnrepository.com/artifact/io.springfox/springfox-boot-starter -->
<dependency>
    <groupId>io.springfox</groupId>
    <artifactId>springfox-boot-starter</artifactId>
    <version>3.0.0</version>
</dependency>

<!-- https://mvnrepository.com/artifact/io.springfox/springfox-swagger-ui -->
<dependency>
    <groupId>io.springfox</groupId>
    <artifactId>springfox-swagger-ui</artifactId>
    <version>3.0.0</version>
</dependency>
```

## NAVEGADOR
**LA URL DE ACCESO A LA DOCUMENTACIÓN ES =**
`{host}:{puerto} / {contexto} /swagger-ui/index.html`
## AuthenticationManager

Reemplazar el método authenticationManagerBeande WebSecurityConfigurerAdapterexponer la AuthenticationManager construido usando configure(AuthenticationManagerBuilder)como un grano de primavera:

```SecurityConfig.java
 @Bean(name = BeanIds.AUTHENTICATION_MANAGER)
   @Override
   public AuthenticationManager authenticationManagerBean() throws Exception {
       return super.authenticationManagerBean();
   }
```
Es posible que desee usar @Import para agregar clases de 
@Configuration a la otra clase (AuthController en mi caso):
```AuthController.java
@Import(SecurityConfig.class)
@RestController
@RequestMapping("/auth")
public class AuthController {

    @Autowired
    private AuthenticationManager authenticationManager;

    //some logic

}
```
