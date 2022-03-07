# mc10-springboot-mysql


# Clase Magistral 10 - Argentina Programa - Java Spring Boot

Cronograma de clases oficial:

[https://argentinaprograma.inti.gob.ar/mod/page/view.php?id=566](https://argentinaprograma.inti.gob.ar/mod/page/view.php?id=566)

Textos oficiales ArgentinaPrograma Java Spring Boot: [https://argentinaprograma.inti.gob.ar/mod/page/view.php?id=515](https://argentinaprograma.inti.gob.ar/mod/page/view.php?id=515)

Masterclass grabada oficial ArgentinaPrograma: [https://argentinaprograma.inti.gob.ar/mod/page/view.php?id=559](https://argentinaprograma.inti.gob.ar/mod/page/view.php?id=559)

Un curso de Java Spring boot para ver los contenidos y la cantidad de clases de profesionales que enseñan esto:  [https://sceu.frba.utn.edu.ar/e-learning/detalle/curso/1270/fundamentos-de-spring-framework-para-java?gclid=CjwKCAiAyPyQBhB6EiwAFUuakj9MDbO2vzNwyXU_j2hRVdBRHaWExSNRlydI2zNANDEy2kDfCf0iuBoCGAoQAvD_BwE](https://sceu.frba.utn.edu.ar/e-learning/detalle/curso/1270/fundamentos-de-spring-framework-para-java?gclid=CjwKCAiAyPyQBhB6EiwAFUuakj9MDbO2vzNwyXU_j2hRVdBRHaWExSNRlydI2zNANDEy2kDfCf0iuBoCGAoQAvD_BwE)

Página oficial Java Spring Boot: [https://spring.io/projects/spring-boot](https://spring.io/projects/spring-boot)

**PRECONDICIONES:** 

Tener instalado / instalar lo siguiente: 

- MySQL Community Edition: [https://dev.mysql.com/downloads/](https://dev.mysql.com/downloads/)
- Bajar **DBeaver:** [https://dbeaver.com/download/](https://dbeaver.com/download/)
- JDK Java Development Kit: [https://www.oracle.com/java/technologies/javase/jdk17-archive-downloads.html](https://www.oracle.com/java/technologies/javase/jdk17-archive-downloads.html)
- Netbeans: [https://netbeans.apache.org/download/index.html](https://netbeans.apache.org/download/index.html)
- Opcional - Netbeans Dark Darcula plugin: [https://draculatheme.com/netbeans](https://draculatheme.com/netbeans)
- Postman: [https://www.postman.com/downloads/](https://www.postman.com/downloads/)

- Haber visto la masterclass grabada de ArgentinaPrograma **MC9** (***Programación Java Web***)  - o algun otro video tutorial dónde se explique JSP, JPA y Servlets: [https://argentinaprograma.inti.gob.ar/mod/page/view.php?id=333](https://argentinaprograma.inti.gob.ar/mod/page/view.php?id=333)

**Glosario de esta clase:**

- Entidad / Business Object /  Objeto de negocios
- Data Transfer Object (DTO)
- Data Access Object (DAO)  / Repository / spring-data-jpa / mysql-driver / h2-database (solo si quiero mockear una db local)
- **JPA (Java Persistence API)**
- REST API (GET, POST, PUT, DELETE) / Webservices
- **XML** (Extensible Markup Language)
- Apache Tomcat
- PathVariables
- Query strings (query params - RequestParam en spring)

Longbok

Spring Boot Dev Tools

MVC (Model View Controller)

Las operaciones HTTP más importantes que nos permitirán manipular los recursos son cuatro:

- GET para consultar y leer
- POST para crear
- PUT para editar
- DELETE para eliminar.

Other Sources > application properties (poner la configuración de la Base de datos que vamos a usar)

```
# Hibernate ddl auto (create, create-drop, validate, update, none)
spring.jpa.hibernate.ddl-auto= update
```

spring.jpa.hibernate.ddl-auto=update

spring.datasource.url=jdbc:mysql://localhost:3306/spring_jpa?useSSL=false&serverTimezone=UTC

spring.datasource.username=root

spring.datasource.password=1234

spring.jpa.database-platform=org.hibernate.dialect.MySQL8Dialect

**javax.persistent.entity**

En el PersonaRepository poner:

@Repository

public interface PersonaRepository extends **JpaRepository** <Persona, Long> {

}

Para inyección de dependencias de los repositories, usamos una inyección de dependencias de Spring

@Autowired  

El service necesita el @Service

**Controller:** 

@**RestController** 

@PostMapping

@GetMapping

@PutMapping

@DeleteMapping 

etcccc

**Controller → Service →  Repository**

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1921deb6-9526-42ff-b636-d1a2a31bfc8e/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/56b38e89-3c95-4c20-9a3b-9dd14045fb90/Untitled.png)

[https://www.youtube.com/watch?v=vTu2HQrXtyw&ab_channel=DATACLOUDER](https://www.youtube.com/watch?v=vTu2HQrXtyw&ab_channel=DATACLOUDER)

![Screen Shot 2022-03-03 at 18.12.08.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5379b51e-5e55-4180-9f1c-1b7f232b07ba/Screen_Shot_2022-03-03_at_18.12.08.png)

**CLIENTE** → Controller → Service → Repository + Model ⇒ **BASE DE DATOS** 

**BASE DE DATOS** ⇒ Model + Repository → Service → Controller → **CLIENTE**  

**Hibernate JPA Spring Annotations**

[https://thorben-janssen.com/key-jpa-hibernate-annotations/](https://thorben-janssen.com/key-jpa-hibernate-annotations/)

`@Entity`

**`public`** **`class`** `MyEntity {`

`@Id`

`@GeneratedValue(strategy = GenerationType.IDENTITY)`

`@ Column(name = "id", updatable = **false**, nullable = **false**)`

`**private**` `Long id;`

`@ManyToOne(fetch = FetchType.LAZY)`

`**private**` `Publisher publisher;`

`@OneToMany(mappedBy = "publisher", cascade = CascadeType.ALL)`

`@OneToMany(mappedBy = "publisher", cascade = CascadeType.ALL)`

`**private**` `Set<Book> books;`

`@OneToOne(fetch = FetchType.LAZY)`

`**private**` `Book book;`

`@OneToOne(mappedBy = "book")`

`**private**` `Manuscript manuscript;`

**Un tutorial completo con ManyToMany y todo el codigo java / dbs / spring etc!**

[https://www.bezkoder.com/jpa-many-to-many/](https://www.bezkoder.com/jpa-many-to-many/)

Accessing JPA Data with REST (springboot)

[https://spring.io/guides/gs/accessing-data-rest/](https://spring.io/guides/gs/accessing-data-rest/)

[Clase](https://www.notion.so/Clase-e234b46b82ad46b8aed1535ec694986a)

[](https://www.notion.so/5f65c547cc744192bcb96e5458b27f7e)
