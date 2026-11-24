# Prácticas de automatización de API

Proyecto de ejercicios de automatización de pruebas para una API de biblioteca. Incluye ejemplos de solicitudes HTTP, validación de respuestas y uso de grupos de pruebas.

## Stack y tecnologías

- **Java 11** como compatibilidad de compilación.
- **Groovy 3.0.2** para escribir las pruebas y ejemplos.
- **Gradle** con los plugins de Java y Groovy para administrar dependencias y ejecutar las pruebas.
- **REST Assured 4.3.1** para realizar solicitudes y validar respuestas HTTP.
- **TestNG 7.3.0** como framework de pruebas y organización por grupos.
- **JSON Schema Validator 3.0.3** para validar la estructura de las respuestas.

## Funcionalidades desarrolladas

- Configuración compartida de REST Assured para la API de biblioteca, con encabezados JSON (`Content-Type` y `Accept`).
- Prueba de consulta de libros (`GET /books`) que verifica que se devuelvan varios títulos.
- Prueba de creación y eliminación de un libro (`POST /books` y `DELETE /books`), comprobando los códigos HTTP y el mensaje de eliminación.
- Prueba de eliminación de un libro inexistente, que verifica el error devuelto por la API.
- Validación de la respuesta de `GET /books` contra un esquema JSON que comprueba campos de los libros y la estructura general.
- Ejercicio básico de Groovy con repetición, closures y recorrido de una lista.

## Estructura del proyecto

```text
src/
└── test/
    ├── groovy/       # Configuración común y pruebas/ejemplos en Groovy
    └── resources/    # JSON de ejemplo y esquema para validar respuestas
build.gradle          # Plugins, dependencias y configuración de TestNG
```

## Ejecución

Requisitos: **JDK 11** y **Gradle** instalados. Desde la raíz del proyecto:

```bash
gradle test
```

Las pruebas llaman al servicio externo configurado en `Base.groovy` (`qa-library-dev.herokuapp.com`), por lo que se requiere acceso a internet y que ese servicio esté disponible. La tarea `test` está configurada para ejecutar el grupo `smoke` y excluir `regression`; por eso, `booksSchemaIsValid`, que pertenece a `regression`, no se ejecuta con el comando anterior.
