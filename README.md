# Sistema de Gestión de Biblioteca Escolar

Aplicación de escritorio en Java (Swing) con MySQL. Evaluación Final Transversal - Desarrollo Orientado a Objetos II.

## Cómo ejecutarlo
1. Abre MySQL Workbench y ejecuta `sql/Script_crea_tablas_biblioteca.sql` y luego `sql/Script_poblado_tablas_biblioteca.sql`.
2. Abre la carpeta del proyecto en IntelliJ IDEA (se importa como proyecto Maven; descarga solo MySQL Connector/J).
3. En `src/main/java/util/DatabaseConnection.java` revisa el usuario y la clave de tu MySQL.
4. Ejecuta `biblioteca/Main.java`.

Para generar el ejecutable: `mvn package` (o Maven > Lifecycle > package en IntelliJ). Queda en `target/biblioteca-escolar.jar`.

## Usuarios de prueba
| Rol | Usuario | Contraseña |
|---|---|---|
| Bibliotecario | biblio@colegio.cl | admin123 |
| Estudiante | camila@colegio.cl | 1234 |

## Estructura
- `modelo/`: Persona (abstracta), Usuario, Estudiante, Libro, Categoria, Prestamo
- `dao/`: CrudDAO (interfaz) y un DAO por tabla
- `controlador/`: intermediarios entre vistas y DAO
- `vista/`: ventanas JFrame y paneles
- `util/`: DatabaseConnection (Singleton) y Mensajes

## Patrones y conceptos aplicados
- **MVC**: vista (JFrame) -> controlador -> modelo/DAO
- **DAO**: toda consulta SQL está en las clases `dao/`
- **Singleton**: `DatabaseConnection.getInstance()`
- **Herencia / abstracción / polimorfismo / interfaz**: `Persona` (abstracta) -> `Usuario` y `Estudiante`; `CrudDAO<T>`
- **Hilos**: `PrestamoController.registrarPrestamoEnSegundoPlano` usa un `Thread`
- **Sincronización**: `PrestamoDAO.registrarPrestamo` y `devolverLibro` son `synchronized` y usan transacción
- **Prueba de concurrencia**: ejecutar `biblioteca/PruebaConcurrencia.java`
