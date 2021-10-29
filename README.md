# SpringbootUno

Connección a MYSQL
Archivo ---> Cambiar application.properties por application.yml
#0. Indicar porque puerte se inicia nuestra app
server:
  port: 8079

spring:
#1. Conexión a BD MySQL
  datasource:
    url: jdbc:mysql://localhost:3306/curso_springboot?useSSL=false&serverTimeZone=UTC
    driverClassName: com.mysql.jdbc.Driver
    username: root
    password:
#2. Jpa nos permite resolver problemas de almacenamiento de los objetos en una base de datos relacional
  jpa:
    database-platform: org.hibernate.dialect.MySQL5InnoDBDialect
    hibernate.ddl-auto: update
    generate-ddl: true
    show-sql: true
#3. Nos muestre los log de las consulta de la BD.
logging:
  level:
    org:
      hibernate:
        SQL: debug
