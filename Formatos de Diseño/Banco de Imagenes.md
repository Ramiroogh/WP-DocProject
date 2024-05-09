# Documentación del Proyecto: Banco de Imágenes

## Introducción
El proyecto consiste en el desarrollo de un sitio web de banco de imágenes para colorear. El objetivo principal es proporcionar una plataforma donde los usuarios puedan acceder a imágenes para colorear, organizadas por categorías, y puedan ver una previsualización de las mismas antes de descargarlas. Para lograr esto, se utilizan varios plugins de WordPress que permiten la gestión de las imágenes y la interacción con los usuarios.

## Gestión de Enrutado
**Lightweight Sidebar Manager:** Se utiliza para crear y gestionar el sidebar del sitio. Permite añadir widgets personalizados, como un menú de navegación, que facilitan la navegación por las diferentes categorías de imágenes.

## Gestion y Control de visualización de Imágenes
**FooGallery:** Se utiliza para crear galerías de imágenes y organizarlas por categorías. Permite mostrar las imágenes en una galería y generar shortcodes para insertarlas en diferentes partes del sitio.

**FooBox:** Este plugin se utiliza para el efecto de lightbox al hacer clic en una imagen de la galería. Permite mostrar la imagen en una ventana modal sin cambiar de página, lo que mejora la experiencia del usuario al ver las imágenes en detalle.

---
## Implementación
1. **Creación de Categorías de Imágenes:**
   - Se crean categorías de imágenes en WordPress para organizar las imágenes por temas como animales, naturaleza, personajes de cuentos, entre otros.

2. **Subida de Imágenes:**
   - Se suben las imágenes a WordPress y se asignan a las categorías correspondientes.

3. **Configuración de FooGallery:**
   - Se crea una galería de imágenes utilizando FooGallery.
   - Se asignan las imágenes a la galería y se organizan por categorías.

4. **Configuración de FooBox:**
   - Se configura FooBox para que se active al hacer clic en una imagen de la galería.
   - Se personaliza la apariencia de la ventana modal para que muestre la imagen en detalle y permita su descarga.

5. **Creación de Sidebar:**
   - Se utiliza Lightweight Sidebar Manager para crear un sidebar personalizado.
   - Se añade un widget de menú de navegación que enlaza a las diferentes categorías de imágenes.

6. **Integración de Shortcodes:**
   - Se generan shortcodes de FooGallery para insertar las galerías de imágenes en las páginas y publicaciones del sitio.
   - Se utilizan shortcodes de FooBox para habilitar el efecto de lightbox en las imágenes de la galería.

---
## Conclusiones
El uso de plugins como FooGallery, FooBox y Lightweight Sidebar Manager ha permitido desarrollar un sitio web de banco de imágenes para colorear de manera efectiva y eficiente. Estos plugins han facilitado la gestión y organización de las imágenes, así como la mejora de la experiencia del usuario al navegar y visualizar las imágenes en el sitio.