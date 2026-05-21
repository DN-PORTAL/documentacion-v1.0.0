# Documentación de Prompts para Generación de Proyecto Spring Boot

> Documento en formato Markdown (.md) listo para exportar o utilizar en GitHub, Notion, Con

## Objetivo
Este documento contiene una colección de prompts estructurados para automatizar la generación de proyectos backend utilizando Java 21, Spring Boot, arquitectura multicapa, DTOs, mappers, manejo de excepciones, pruebas unitarias y base de datos H2/PostgreSQL.

---

# 1. Crear el POM del Proyecto

## Objetivo
Generar el archivo `pom.xml` para un proyecto Spring Boot utilizando Java 21 y dependencias necesarias para APIs REST, persistencia y pruebas.

## Prompt
```text
Crea un pom para spring boot con los siguiente:
maven con java 21, con spring-boot-starter-parent 3.4.5 con las dependencias de web, jpa, postgresql, devtools,
groupId:org.jacoco  artifactId:jacoco-maven-plugin version:0.8.14 y el pluggin respectivo.
lombok, actuator, metada del proyecto Group com.ia, Artifact todo, name mcsv-todo, packaging jar

agregar el pluggin:
<plugin>
    <groupId>org.jacoco</groupId>
    <artifactId>jacoco-maven-plugin</artifactId>
    <version>0.8.14</version>
    <executions>
        <!-- Prepara el agente antes de correr los tests -->
        <execution>
            <id>prepare-agent</id>
            <goals>
                <goal>prepare-agent</goal>
            </goals>                        
        </execution>

        <!-- Genera el reporte despues de correr los tests -->
        <execution>
            <id>report</id>
            <phase>test</phase>
            <goals>
                <goal>report</goal>
            </goals>
        </execution>
    </executions>                
</plugin>

<!-- Agregar dependencia de pruebas -->
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-test</artifactId>
    <scope>test</scope>
</dependency>
```

---

# 2. Crear Proyecto Base

## Objetivo
Generar la estructura inicial del proyecto utilizando el `pom.xml` previamente definido.

## Prompt
```text
creame un proyecto con el pom.xml y sus especificaciones
```

---

# 3. Migrar application.properties a application.yml

## Objetivo
Cambiar la configuración del proyecto para utilizar formato YAML.

## Prompt
```text
modificame la extension de application por yml, y realiza las correcciones necesarias para el formato yml en el archivo application, y agregar server.port: 8080
```

---

# 4. Validación y Limpieza de Caché

## Objetivo
Revisar errores de compilación y limpiar caché del entorno VSCode si es necesario.

## Prompt
```text
revisar los errores, y si es necesario limpiar cache de vsc
```

---

# 5. Generar DDL para PostgreSQL

## Objetivo
Generar el script SQL basado en una imagen o modelo entidad-relación.

## Prompt
```text
generame un ddl para postgres teniendo en cuentas los forengkeys segun la imagen y guardalo en un archivo sql en resource con el nombre de query.
No realices la referencia a USER y valida el orden de la creacion de tablas para evitar errores al momento de hacer referencias en los forengkeys
```

---

# 6. Crear Arquitectura Multicapa

## Objetivo
Crear únicamente la estructura de paquetes del proyecto.

## Prompt
```text
Creame una estructura multicapa, con los siguientes package: controller, models,service,repository,dto,mappers,commons solo las carpetas
```

---

# 7. Generar Entidades

## Objetivo
Crear entidades JPA basadas en el archivo `query.sql`.

## Prompt
```text
generame las entidades un archivo por cada una, haciendo referencia a las propiedades de la tabla definiendo el nombre de las columnas con @Column en la carpeta models, @Table
utilizando lombok, y el patron builder el ddl query.sql si estamos usando java con una version igual o mayor a la 17 usar la importacion de jakarta
```

---

# 8. Generar DTOs

## Objetivo
Crear DTOs de request y response por cada entidad.

## Prompt
```text
Generame los dtos para cada entidad, es importante crear un dto resquestDto y responseDto para cada entidad, y un archivo para cada uno utilizando lombok y el patron builder,
en el caso de los responseDto,  la propiedead datetime debe ser de tipo String, en el caso de los requestDto no debe contener las propiedades Id o primerkey y tampoco
las propiedades createdAt y updatedAt
```

---

# 9. Crear Mappers

## Objetivo
Crear clases mapper para conversión entre entidades y DTOs.

## Prompt
```text
Generar los mappers para cada una de las entidades y dto, con lombok y patron builder: toEntity y toDto
utilizar el formato DateTimeFormatter format_response = DateTimeFormatter.ofPattern("dd-MM-yyyy HH:mm:ss") para conversion de LocalDateTime a String
```

---

# 10. Crear Interface CRUD Genérica

## Objetivo
Crear una interface genérica reutilizable para operaciones CRUD.

## Prompt
```java
public interface ICrudCommons<T, ID> {
    public T save(T entity);
    public T update(ID id, T entity);
    public T findById(ID id);
    public T delete(ID id);
}
```

---

# 11. Crear Repositories

## Objetivo
Generar interfaces Repository utilizando Spring Data JPA.

## Prompt
```text
Generame las interfaces Repository para cada entidad Colocar una I antes de cada nombre de archivo por buena practica, y extender de JpaRepository para cada uno de ellas.
```

---

# 12. Crear Interfaces Service

## Objetivo
Generar interfaces de servicios basadas en `ICrudCommons`.

## Prompt
```text
Generar las interfaces services para cada entidad colocar una I antes de cada nombre de archivo por buena practica y extender de la interface IcrudCommons
```

---

# 13. Crear Carpeta impl

## Objetivo
Crear carpeta de implementaciones de servicios.

## Prompt
```text
crear una carpeta impl en service
```

---

# 14. Implementar Servicios

## Objetivo
Crear implementación de servicios utilizando Repository y BeanUtils.

## Prompt
```text
Generar las clases para implementar de cada interface de service, inyectando con lombok la interface de repository, para el metodo update utilizar BeanUtils.copyProperties ignorando la pk y createdAt y que despues de hacer
copyProperties upate la propiedad updatedAt con LocaDateTime.now. Para el metodo save actualizar createAt y UpdateAt con LocalDateTime.now
```

---

# 15. Crear Controllers

## Objetivo
Crear controladores REST utilizando DTOs y servicios.

## Prompt
```text
generame los controllers para cada entidad inyectando la interface de los servicios con lombok para los eventos post y put recibir en el body requestDto,
y luego mappear los request a entity para pasarlos como parametros a los servicios en el caso de los otros metodos mappear la respuesta a un responseDto
```

---

# 16. Configurar H2

## Objetivo
Agregar dependencia H2 y comentar PostgreSQL.

## Prompt
```text
agregar la dependencia para inicializar una base de datos h2  y comentar la dependencia para postgres
```

---

# 17. Configurar Cadena de Conexión H2

## Objetivo
Agregar configuración H2 en `application.yml`.

## Prompt
```text
creme la cadena de conexion para h2 en application.yml no adiciones nada mas
```

---

# 18. Ejecutar query.sql Automáticamente

## Objetivo
Aplicar el script SQL al iniciar la aplicación.

## Prompt
```text
modificca application.yml para que cuando inicie la aplicacion apli el querysql a la bd h2
```

---

# 19. Crear Clase Main

## Objetivo
Crear clase principal Spring Boot.

## Prompt
```text
no found main appliaction
```

---

# 20. Crear Archivos REST Client

## Objetivo
Generar archivos HTTP para pruebas de endpoints.

## Prompt
```text
creame los archivos con las peticiones para cada controllador utilizando rest client, deben ser archivos deferentes en una carpeta en el proyecto que se llame testhttp
```

---

# 21. Agregar Método getAll

## Objetivo
Agregar método `getAll()` en services y controllers.

## Prompt
```text
en las interfaces de cada servicio crea un metodo abstracto getAll para devolver un List e implementalo en cada servicio y tambien crear el metodo para cada contoller
es importante que los metodos que se agregan deben estar en el cuerpo de la clase y al final
```

---

# 22. Actualizar Peticiones HTTP

## Objetivo
Actualizar archivos REST Client con endpoint `getAll`.

## Prompt
```text
actualizar los archivos de testhttp con el nuevo endpoint getall para cada controller
```

---

# 23. Crear ExceptionDto

## Objetivo
Crear DTO estandarizado para manejo de errores.

## Prompt
```text
creame una carpeta exception en ella un exceptionDto para devolver tres campos hora, mensaje, url, codeStatus
```

---

# 24. Crear Excepciones Personalizadas

## Objetivo
Generar excepciones customizadas utilizando `@ResponseStatus`.

## Prompt
```text
creame las clases :
RuntimeCustomException @ResponseStatus(value = HttpStatus.INTERNAL_SERVER_ERROR),
BadRequesException @ResponseStatus(value = HttpStatus.BAD_REQUEST),
ResourceNotFoundException @ResponseStatus(value =  HttpStatus.NOT_FOUND),
ResourceUnAuthorizedException @ResponseStatus(value =  HttpStatus.UNAUTHORIZED),
ValidatedRequestException @ResponseStatus(value =  HttpStatus.ACCEPTED)
```

---

# 25. Crear GlobalExceptionHandler

## Objetivo
Centralizar el manejo de excepciones.

## Prompt
```text
Crear la  Clase para manejar GlobalExceptionHandlerm
con la siguiente estructura:

@Slf4j
@RestControllerAdvice
public class GlobalExceptionHandler {

  private static final DateTimeFormatter FORMATTER = DateTimeFormatter.ofPattern("dd-MM-yyyy HH:mm:ss");

  private HttpStatus getStatus(Throwable ex) {
    ResponseStatus status = ex.getClass().getAnnotation(ResponseStatus.class);
    if (status != null) {
      return status.value();
    }
    return HttpStatus.INTERNAL_SERVER_ERROR;
  }

  @ExceptionHandler({
      BadRequestException.class,
      ResourceNotFoundException.class,
      ResourceUnAuthorizedException.class,
      ValidatedRequestException.class,
      RuntimeCustomException.class,
      ConflictException.class,
      InternalServerErrorException.class,
      ValidatedRequestException.class
  })
  public ResponseEntity<ExceptionDto> handleCustomExceptions(RuntimeException ex, HttpServletRequest request) {
    HttpStatus status = getStatus(ex);

    ExceptionDto dto = ExceptionDto.builder()
        .hora(LocalDateTime.now().format(FORMATTER))
        .mensaje(ex.getMessage())
        .url(request.getRequestURI())
        .codeStatus(status.value())
        .build();

    log.error(ex.getClass().getSimpleName() + ": ", ex);

    return ResponseEntity.status(status).body(dto);
  }

  @ExceptionHandler(MethodArgumentNotValidException.class)
  public ResponseEntity<ExceptionDto> handleValidationException(MethodArgumentNotValidException ex,
      HttpServletRequest request) {
    HttpStatus status = HttpStatus.BAD_REQUEST;

    String mensaje = ex.getBindingResult().getAllErrors().stream()
        .map(error -> {
          if (error instanceof org.springframework.validation.FieldError fe) {
            return fe.getField() + ": " + fe.getDefaultMessage();
          } else {
            return error.getDefaultMessage();
          }
        })
        .collect(Collectors.joining(", "));

    ExceptionDto dto = ExceptionDto.builder()
        .hora(LocalDateTime.now().format(FORMATTER))
        .mensaje(mensaje)
        .url(request.getRequestURI())
        .codeStatus(status.value())
        .build();

    log.error("ValidationException: {}", mensaje);

    return ResponseEntity.status(status).body(dto);
  }
}
```

---

# 26. Aplicar Exceptions en Servicios

## Objetivo
Implementar excepciones customizadas en la lógica de negocio.

## Prompt
```text
aplicar los exception en la capa servicios, para customizar las respuestas de errores.
```

---

# 27. Crear Pruebas Unitarias Controller

## Objetivo
Crear pruebas unitarias del controlador utilizando Mockito.

## Prompt
```text
crear la clase stateControllerTest, en test,
utilizar @Mock para los servicios o mapper que tengra referencia el controller
en el metodo setUp, inicializa las entidades y dtos necesarios para crear los metodos que se van a testear del controller
en el metodo setUp inicializar MockitoAnnotations.openMocks(this) ;
e implementar los metodos necesarios para el test del controller stateController    es para pasar una auditoria
```

---

# Recomendaciones Generales

## Buenas Prácticas
- Utilizar Java 21.
- Mantener separación por capas.
- Usar DTOs para evitar exponer entidades.
- Aplicar manejo global de excepciones.
- Usar Lombok para reducir código repetitivo.
- Aplicar patrón Builder.
- Utilizar H2 para pruebas locales.
- Mantener cobertura de pruebas con JaCoCo.
- Mantener nomenclatura consistente (`IService`, `IRepository`).

---

# Flujo Recomendado de Ejecución

1. Crear `pom.xml`
2. Crear proyecto base
3. Configurar `application.yml`
4. Generar DDL
5. Crear arquitectura multicapa
6. Crear entidades
7. Crear DTOs
8. Crear mappers
9. Crear repositories
10. Crear services
11. Implementar services
12. Crear controllers
13. Configurar H2
14. Crear peticiones HTTP
15. Implementar excepciones
16. Crear pruebas unitarias
17. Ejecutar JaCoCo

---

# Resultado Esperado

Al finalizar todos los prompts se obtiene:

- Proyecto Spring Boot completo.
- Arquitectura multicapa.
- Persistencia con JPA.
- DTOs y Mappers.
- CRUD completo.
- Base de datos H2/PostgreSQL.
- Manejo global de excepciones.
- Pruebas unitarias.
- Cobertura de código con JaCoCo.
- Archivos HTTP para pruebas.

