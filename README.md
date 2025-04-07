# 🎬 Proyecto Backend de Gestión de Películas

Este proyecto está desarrollado con **Java** y **Spring Boot**, y permite gestionar un listado de películas. Se puede consultar, crear, actualizar, eliminar o votar por películas mediante peticiones HTTP.

## 📦 Tecnologías utilizadas

- Java 17+
- Spring Boot
- Spring Data JPA
- H2 / MySQL (configurable)
- Postman (para pruebas)
- Maven

📂 Estructura del Proyecto

src
└── main
    └── java
        └── com._Luis8.peliculas
            ├── controllers
            │   └── MovieController.java
            ├── models
            │   └── Movie.java
            └── repositories
                └── MovieRepository.java

🧩 Explicación de los archivos

  ✅ Movie.java
      Ubicación: models/Movie.java
      Este archivo define la entidad Movie, que representa una película en la base de datos.
    
    Campos principales:
      id: identificador único generado automáticamente.
      title: título de la película.
      year: año de estreno.
      votes: número de votos recibidos.
      rating: nota media de la película.
      imageUrl: URL con la imagen del cartel de la película.
      
    Anotaciones importantes:
      @Entity y @Table(name = "movies"): indican que esta clase se mapea con la tabla movies.
      @Id y @GeneratedValue: especifican la clave primaria y su generación automática.
      @Column(name = "image_url"): define el nombre de la columna en la base de datos.

✅ MovieRepository.java
    Ubicación: repositories/MovieRepository.java
    Es una interfaz que extiende JpaRepository<Movie, Long>, lo que permite acceder a todas las operaciones CRUD sin necesidad de implementar nada manualmente.
    Spring Boot se encarga de inyectar automáticamente la implementación concreta gracias a Spring Data JPA.

✅ MovieController.java
    Ubicación: controllers/MovieController.java
    Este es el controlador REST del proyecto. Define todos los endpoints para gestionar películas:

      GET /api/peliculas: devuelve todas las películas.
      GET /api/peliculas/{id}: devuelve una película por su ID.
      POST /api/peliculas: crea una nueva película.
      PUT /api/peliculas/{id}: actualiza una película existente.
      DELETE /api/peliculas/{id}: elimina una película.
      GET /api/peliculas/vote/{id}/{rating}: vota una película y actualiza su media.

    Notas adicionales:
      Todos los métodos están anotados con @CrossOrigin para permitir llamadas desde un frontend externo.
      Se usa ResponseEntity para devolver respuestas HTTP con los códigos apropiados.
      El método de voto calcula la media ponderada actualizando el número de votos y el rating medio.

🔧 Posibles mejoras futuras

    Añadir autenticación y autorización.
    Validaciones más estrictas con @Valid.
    Conectar con un frontend en Angular, React o Vue.
    Documentación automática con Swagger.
