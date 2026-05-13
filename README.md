# SmartLogix — Arquetipo Maven Base

## Descripción

Este repositorio contiene el arquetipo Maven base utilizado como plantilla para generar los componentes backend de SmartLogix (BFF y microservicios). Fue generado desde [start.spring.io](https://start.spring.io) con las dependencias necesarias para el proyecto.

## Tecnologías incluidas

| Dependencia | Versión | Propósito |
|---|---|---|
| Spring Boot Parent | 4.0.6 | Gestión centralizada de dependencias |
| Java | 21 | Lenguaje de programación |
| Spring Web MVC | - | Creación de APIs REST |
| Spring Data JPA | - | Persistencia con Hibernate |
| Spring Validation | - | Validación de datos |
| Resilience4j | 2025.1.1 | Circuit Breaker |
| Lombok | - | Reducción de boilerplate |
| MySQL Connector | - | Driver de base de datos |
| JUnit 5 + Mockito | - | Pruebas unitarias |

## Estructura del arquetipo

```
demo/
├── src/
│   ├── main/
│   │   ├── java/com/example/demo/
│   │   │   └── DemoApplication.java      ← punto de entrada
│   │   └── resources/
│   │       └── application.properties    ← configuración base
│   └── test/
│       └── java/com/example/demo/
│           └── DemoApplicationTests.java ← test base
├── pom.xml                               ← dependencias del arquetipo
├── mvnw                                  ← Maven Wrapper (Linux/Mac)
└── mvnw.cmd                              ← Maven Wrapper (Windows)
```

## Cómo usar este arquetipo para generar un nuevo microservicio

### Paso 1 — Clonar el repositorio
```bash
git clone https://github.com/PaulinaCampusano/smartlogix-arquetipo-maven.git
```

### Paso 2 — Copiar la carpeta demo
Copia la carpeta `demo/` y renómbrala con el nombre de tu microservicio:
```bash
cp -r demo/ mi-microservicio
cd mi-microservicio
```

### Paso 3 — Modificar el pom.xml
Edita los siguientes campos en el `pom.xml`:
```xml
<groupId>com.smartlogix</groupId>
<artifactId>mi-microservicio</artifactId>
<name>mi-microservicio</name>
```

### Paso 4 — Configurar application.properties
Edita `src/main/resources/application.properties`:
```properties
spring.application.name=mi-microservicio
server.port=XXXX
spring.datasource.url=jdbc:mysql://localhost:3306/db_mims?createDatabaseIfNotExist=true
spring.datasource.username=root
spring.datasource.password=
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
```

### Paso 5 — Renombrar el paquete base
Renombra el paquete `com.example.demo` por `com.smartlogix.{nombre}` en todos los archivos Java.

### Paso 6 — Ejecutar el microservicio
```bash
./mvnw spring-boot:run
```

### Paso 7 — Ejecutar las pruebas
```bash
./mvnw test
```

## Microservicios generados con este arquetipo

| Componente | Repositorio | Puerto |
|---|---|---|
| MS-Inventario | github.com/Gouramichelle/smartlogix-inventario | 8081 |
| MS-Pedidos | github.com/Gouramichelle/smartlogix-pedidos | 8086 |
| BFF | github.com/Gouramichelle/smartlogix-bff | 8088 |

## Proyecto SmartLogix

SmartLogix es una plataforma de gestión logística para PYMEs de eCommerce.
Curso: Desarrollo Fullstack III (DSY1106) — DuocUC
