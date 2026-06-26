# Geovisor Mesoamérica

Este es un visualizador de mapas interactivo ligero, responsivo y moderno basado en **Leaflet**. Está diseñado para ejecutarse completamente del lado del cliente, lo que lo hace ideal para ser alojado de forma gratuita en **GitHub Pages** sin necesidad de bases de datos ni servidores activos.

---

## 🚀 Guía de Publicación Rápida (Crea tu propio Geovisor)

Cualquier persona puede crear una copia de este geovisor y publicar su propio mapa con datos personalizados en su cuenta de GitHub. Sigue estos sencillos pasos directamente desde la interfaz web de GitHub (sin necesidad de escribir comandos de consola ni programar):

### 📋 Paso 1: Hacer un Fork del Repositorio
Un "Fork" crea una copia idéntica de este repositorio bajo tu propia cuenta de GitHub para que puedas realizar cambios de manera independiente.
1. Inicia sesión en tu cuenta de [GitHub](https://github.com).
2. Ve al repositorio original: [https://github.com/copernicuscentroamerica/geovisor](https://github.com/copernicuscentroamerica/geovisor).
3. Haz clic en el botón **Fork** en la esquina superior derecha y selecciona **Crear un nuevo fork**.
4. Define el propietario (tu cuenta de usuario) y el nombre del repositorio (por ejemplo: `geovisor`).
6. Haz clic en el botón verde **Create fork** en la parte inferior para iniciar el proceso de clonación.

### 🗑️ Paso 2: Eliminar las Capas de Ejemplo
Para evitar que se muestren las capas de ejemplo predeterminadas en tu mapa, debes eliminarlas:
1. Dentro de tu nuevo repositorio en GitHub, entra a la carpeta `data/` haciendo clic sobre ella (o ingresando a [data/](data/)).
2. Para cada archivo de ejemplo que desees borrar (por ejemplo, `Areas_Protegidas_corte.json` y `Limite_ZonaEstudio.json`):
   - Haz clic sobre el nombre del archivo.
   - En la parte superior derecha del visor de archivo, haz clic en el botón de los tres puntos `...` y selecciona **Delete file** (Eliminar archivo).
   - Confirma el borrado haciendo clic en el botón verde **Commit changes...** (Confirmar cambios).
   - En el cuadro que se despliega, haz clic en **Commit changes** (Confirmar cambios) para guardar.

### 📤 Paso 3: Subir tus Propias Capas de Datos
> [!TIP]
> Si tienes tus capas en formatos tradicionales como Shapefile (.shp), KML o GPX, puedes utilizar la herramienta web gratuita [Mapshaper](https://mapshaper.org/) (cuyo enlace directo está integrado en el panel de capas del geovisor) para convertirlas a GeoJSON antes de subirlas.

Ahora puedes cargar tus archivos geográficos a la carpeta de datos:
1. Asegúrate de estar dentro de la carpeta `data/` (o [data/](data/)) en tu repositorio en GitHub.
2. Haz clic en el botón **Add file** (Añadir archivo) en la esquina superior derecha y selecciona **Upload files** (Subir archivos).
3. Arrastra y suelta tus propios archivos espaciales en formato **GeoJSON** o **JSON** (por ejemplo: `mis_capas_locales.json`).
4. Haz clic en el botón verde **Commit changes** al final de la página para guardar los archivos cargados.

### ⚙️ Paso 4: Modificar el Archivo de Configuración
Debes registrar tus nuevas capas en el archivo de configuración para que el geovisor las reconozca y las dibuje en el mapa:
1. Regresa al directorio raíz de tu repositorio y abre el archivo [configuracion_geovisor.json](configuracion_geovisor.json).
2. Haz clic en el icono del **lápiz** (Editar este archivo) en la esquina superior derecha.
3. Modifica las siguientes propiedades clave:
   - `"titulo_geovisor"`: Escribe el título personalizado de tu mapa (ej. `"Geovisor de Juan"`).
   - `"autor_desarrollador"`: Escribe tu nombre o el de tu organización.
   - `"capas_a_cargar"`: Escribe la lista de nombres exactos de los archivos GeoJSON/JSON que subiste en la carpeta `data/`, separados por comas y entre comillas.
4. **Ejemplo de configuración corregida:**
   ```json
   {
     "titulo_geovisor": "Geovisor de Juan",
     "autor_desarrollador": "Mi Organización",
     "mapa_base_defecto": "dark",
     "capas_a_cargar": [
       "mis_capas_locales.json"
     ]
   }
   ```
5. Desplázate hacia abajo y haz clic en el botón verde **Commit changes** para guardar.

### 🌐 Paso 5: Activar el Despliegue en GitHub Pages
Configura GitHub para que aloje públicamente tu geovisor de forma gratuita:
1. En la parte superior de tu repositorio, haz clic en la pestaña **Settings** (Configuración).
2. En el menú lateral izquierdo, bajo la sección *Code and automation*, haz clic en **Pages**.
3. En la sección **Build and deployment** -> **Branch**:
   - En *Source*, asegúrate de que esté seleccionado *Deploy from a branch*.
   - En *Branch*, selecciona la rama que deseas compilar (usa `main` para el geovisor original, o la rama `limpio` si deseas desplegar la versión del Geovisor simplificada).
   - Deja la carpeta de destino en `/ (root)`.
   - Haz clic en el botón **Save** (Guardar).

### 🔗 Paso 6: Visitar tu Geovisor en Vivo
1. El proceso de publicación toma alrededor de 1 a 2 minutos.
2. Espera un momento y refresca la pestaña **Pages** en la configuración de GitHub.
3. En la parte superior verás un recuadro verde con el mensaje:
   `Your site is live at https://tu-usuario.github.io/tu-repositorio/`
4. Haz clic en ese enlace para acceder a tu geovisor publicado. ¡Ya está listo para compartir con el mundo!

---

## 🛠️ Desarrollo Local (Avanzado)

Si eres desarrollador y deseas probar o personalizar el código de forma local en tu computadora:

1. Clona el repositorio en tu máquina:
   ```bash
   git clone https://github.com/tu-usuario/tu-repositorio.git
   cd tu-repositorio
   ```
2. Inicia el servidor de desarrollo local ejecutando:
   ```bash
   node server.js
   ```
3. Abre en tu navegador `http://localhost:8081`. 
   *(Nota: Este servidor local dinámico escanea automáticamente la carpeta `data/` y carga las capas al vuelo sin necesidad de agregarlas manualmente a `configuracion_geovisor.json`, lo que facilita la experimentación rápida).*
