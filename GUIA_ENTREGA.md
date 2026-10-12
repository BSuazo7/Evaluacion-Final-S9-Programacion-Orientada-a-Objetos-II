# Guía rápida para entregar (checklist)

## 1. Antes de grabar el video (15 min)
- [ ] Instalar/abrir MySQL y ejecutar TUS scripts oficiales del AVA (crea tablas, luego poblado).
      Si da error de columna (por ejemplo `titulo` vs `título`, `contrasena` vs `contraseña`),
      cambia ese nombre en los DAO (`LibroDAO`, `UsuarioDAO`, `PrestamoDAO`, `ReporteDAO`).
      Si algo no te calza, puedes usar los scripts que vienen en la carpeta `sql/`.
- [ ] Abrir el proyecto en IntelliJ, esperar que Maven descargue el driver.
- [ ] Poner tu usuario/clave de MySQL en `DatabaseConnection.java`.
- [ ] Ejecutar `Main` y probar: login, crear/editar/eliminar libro, registrar estudiante, préstamo, devolución, reportes.
- [ ] Ejecutar `PruebaConcurrencia` (debe salir 3 exitosos, 7 rechazados, stock final 0).

## 2. Guion del video (3 a 5 minutos, con tu cara visible)
1. (0:00) Saludo con tu cara: nombre, ramo, "Sistema de Biblioteca Escolar".
2. (0:20) Mostrar IntelliJ: carpetas modelo / dao / controlador / vista / util. Explicar MVC en una frase:
   "la vista muestra, el controlador recibe los clics, el DAO habla con la base de datos".
3. (0:50) `DatabaseConnection`: Singleton = una sola conexión compartida (constructor privado + getInstance).
4. (1:15) `Persona` -> `Usuario` / `Estudiante` (herencia, clase abstracta) y la interfaz `CrudDAO`.
5. (1:40) Demo de la app: login como bibliotecario, libros (crear/modificar/eliminar), estudiantes.
6. (2:40) Demo préstamo: registrar (se ve el aviso "en segundo plano", la ventana no se congela), devolver, ver atraso en rojo.
7. (3:30) Mostrar `PrestamoDAO.registrarPrestamo` (synchronized + transacción) y el hilo en `PrestamoController`.
   Mencionar la `PruebaConcurrencia`.
8. (4:00) Reportes y login como estudiante (solo ve libros, préstamos y su historial).
9. (4:30) Cierre.

## 3. GitHub (obligatorio)
1. Crear repositorio PÚBLICO en github.com (por ejemplo `biblioteca-escolar`).
2. En la carpeta del proyecto, en una terminal:
   ```
   git init
   git add .
   git commit -m "Proyecto inicial: modelo, DAO y conexión Singleton"
   git branch -M main
   git remote add origin https://github.com/TU_USUARIO/biblioteca-escolar.git
   git push -u origin main
   ```
   Tip: para tener "commits descriptivos" haz 3 o 4 commits separados
   (ej. "Agrego modelos y DAO", "Agrego interfaz gráfica", "Agrego hilos y sincronización", "Agrego reportes y README").
3. Copiar el link del repositorio.

## 4. Entrega en el AVA
- [ ] .zip del proyecto completo (código + carpeta sql). Si puedes, incluye `target/biblioteca-escolar.jar`.
- [ ] Video grabado con Kaltura.
- [ ] Link del repositorio de GitHub en el espacio de entrega.
