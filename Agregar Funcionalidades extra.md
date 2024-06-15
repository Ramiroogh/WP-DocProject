En WordPress, las funcionalidades adicionales, como interacciones con AJAX o renderizado de contenido dinámico, suelen agregarse al archivo **functions.php** del tema activo por varias razones:

Importante: se recomiendo hacer una copia del tema, theme-child.

1. **Temas y Plugins:** WordPress utiliza temas para controlar el aspecto visual y la estructura de tu sitio, y plugins para agregar funcionalidades adicionales. El archivo functions.php es un lugar común donde tanto los temas como los plugins pueden agregar funcionalidades personalizadas.

2. **Jerarquía de Plantillas:** WordPress sigue una jerarquía de plantillas para determinar cómo se muestra el contenido en tu sitio. Las páginas individuales pueden tener su propio archivo de plantilla, pero el tema activo define las funciones generales y los estilos que se aplican a todas las páginas.

3. **Consistencia y Mantenimiento:** Al centralizar las funcionalidades personalizadas en el archivo functions.php del tema, se facilita el mantenimiento y la gestión de código, ya que todas las personalizaciones están en un solo lugar.

4. **Compatibilidad:** El archivo functions.php del tema activo se carga en cada página de tu sitio, lo que garantiza que las funcionalidades personalizadas estén disponibles en todo momento, independientemente de la página que se esté viendo.

Si deseas agregar interacciones con AJAX o renderizado de contenido dinámico en otros componentes de tu sitio, generalmente es recomendable hacerlo en el archivo functions.php del tema activo para asegurarte de que esas funcionalidades estén disponibles en todas las páginas y componentes del sitio. Sin embargo, también puedes crear un plugin personalizado para agregar estas funcionalidades si prefieres mantenerlas separadas del tema.

---

I. Introducción

Para implementar AJAX con FooGallery en WordPress, necesitarás crear un widget personalizado que permita filtrar las imágenes por categoría. Este widget entonces enviará una solicitud AJAX al servidor de WordPress para obtener las imágenes de la categoría seleccionada y actualizará el shortcode de FooGallery con estas imágenes.

II. Pasos para la Implementación

1. Creación del Widget

Primero, necesitarás crear un widget personalizado en WordPress. Este widget deberá tener un formulario con un menú desplegable que contenga todas las categorías de imágenes disponibles.

```php
class Filtro_Categoria_Widget extends WP_Widget {
    // constructor
    public function __construct() {
        parent::__construct(
            'filtro_categoria_widget',
            __('Filtro de Categoría', 'text_domain')
        );
    }

    // widget form creation
    public function form($instance) {
        // Lista de categorías
        $categorias = get_categories(array('taxonomy' => 'foogallery_category'));
        
        echo '<select id="categoria_select" name="categoria_select">';
        foreach ($categorias as $categoria) {
            echo '<option value="'.$categoria->term_id.'">'.$categoria->name.'</option>';
        }
        echo '</select>';
    }
}
```

2. Implementación de AJAX en WordPress

Para implementar AJAX en WordPress, necesitas agregar dos acciones: una para manejar la solicitud AJAX en el lado del servidor y otra para imprimir la URL de AJAX en el lado del cliente.

```php
// Agrega la acción AJAX en el lado del servidor
add_action('wp_ajax_filtrar_imagenes', 'filtrar_imagenes');
add_action('wp_ajax_nopriv_filtrar_imagenes', 'filtrar_imagenes');

function filtrar_imagenes() {
    $categoria_id = $_POST['categoria_id'];

    // Obtén las imágenes de la categoría seleccionada
    $imagenes = get_images_from_category($categoria_id);

    // Genera el nuevo shortcode de FooGallery
    $shortcode = generate_foogallery_shortcode($imagenes);

    // Envía el nuevo shortcode al cliente
    echo $shortcode;

    wp_die();
}

// Imprime la URL de AJAX en el lado del cliente
add_action('wp_head', 'ajaxurl');
function ajaxurl() {
    echo '<script type="text/javascript">
            var ajaxurl = "' . admin_url('admin-ajax.php') . '";
          </script>';
}
```

3. Enviar la Solicitud AJAX al Seleccionar una Categoría

Finalmente, necesitarás escribir el código JavaScript para enviar la solicitud AJAX al servidor cuando el usuario seleccione una categoría. Este código actualizará el shortcode de FooGallery con las nuevas imágenes.

```php
jQuery(document).ready(function($) {
    $('#categoria_select').change(function() {
        var categoria_id = $(this).val();

        $.post(ajaxurl, {
            action: 'filtrar_imagenes',
            categoria_id: categoria_id
        }, function(shortcode) {
            // Actualiza el shortcode de FooGallery con el nuevo
            $('#foogallery_container').html(shortcode);
        });
    });
});
```

Estos códigos son ejemplos básicos y pueden requerir ajustes según tu configuración exacta y necesidades. Te recomendaría probarlos en un entorno de desarrollo antes de implementarlos en un sitio en vivo.

III. Conclusion

AJAX puede ser una herramienta muy útil para mejorar la interactividad y la eficiencia de tu sitio de WordPress. En combinación con FooGallery, puedes crear un banco de imágenes dinámico y fácil de usar que permita a los usuarios filtrar las imágenes por categoría sin tener que recargar la página.

---
 Distribución de los Códigos

Para implementar AJAX con FooGallery en WordPress, necesitarás trabajar con varios archivos. Aquí te dejo una guía de en qué archivos y con qué nombres deberías colocar cada pieza de código:

1. Creación del Widget

El código para la creación del widget debería ir en el archivo functions.php de tu tema activo. Si prefieres mantener las cosas más organizadas, puedes crear un archivo separado para el código del widget, por ejemplo, filtro-categoria-widget.php, y luego incluirlo en functions.php con require_once.

2. Implementación de AJAX en WordPress

El código para la implementación de AJAX también debería ir en el archivo functions.php de tu tema activo. De nuevo, si prefieres mantener las cosas más organizadas, puedes crear un archivo separado para el código AJAX, por ejemplo, ajax-functions.php, y luego incluirlo en functions.php con require_once.

3. Enviar la Solicitud AJAX al Seleccionar una Categoría

El código JavaScript para enviar la solicitud AJAX debería ir en un archivo JavaScript separado, por ejemplo, ajax-scripts.js. Este archivo debería estar ubicado en la carpeta js de tu tema activo. Luego, necesitarás encolar este archivo en WordPress utilizando la función wp_enqueue_script en functions.php.

Por favor, ten en cuenta que estos son solo ejemplos y puedes organizar tus archivos de la manera que mejor se adapte a tus necesidades. Además, recuerda siempre hacer una copia de seguridad de tus archivos antes de hacer cualquier cambio.