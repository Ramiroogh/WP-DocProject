# Columnas CSV, para Posts

Para crear múltiples posts con categorías y subcategorías en WordPress utilizando un archivo CSV, necesitarás incluir columnas adicionales en tu archivo CSV para especificar las categorías y subcategorías, además de los detalles básicos de los posts. A continuación te explico las columnas que necesitarías:

1. **post_title**: El título del post.
2. **post_content**: El contenido del post.
3. **post_excerpt**: Un resumen breve del post.
4. **post_permalink**: El enlace permanente del post.
5. **featured_image**: URL de la imagen destacada del post.
6. **categories**: Las categorías y subcategorías del post, separadas por comas.
7. **tags**: Etiquetas relacionadas con el post (opcional).

---

Aquí tienes un ejemplo del contenido que debería tener el archivo CSV:

| post_title       | post_content                                                                                          | post_excerpt                                          | post_permalink                    | featured_image | categories                              | tags                     |
|------------------|-------------------------------------------------------------------------------------------------------|------------------------------------------------------|----------------------------------|----------------|-----------------------------------------|--------------------------|
| Post 1           | Contenido del post 1                                                                                  | Resumen del post 1                                    | post-1                            | image1.jpg     | Categoría 1,Subcategoría 1,Subcategoría 2 | etiqueta1, etiqueta2     |
| Post 2           | Contenido del post 2                                                                                  | Resumen del post 2                                    | post-2                            | image2.jpg     | Categoría 2,Subcategoría 3               | etiqueta3, etiqueta4     |

### Ejemplo Práctico

- **Post Title**: "Animales del Bosque: Ardillas"
- **Post Content**: "Explora la vida de las ardillas en su hábitat natural. Conoce más sobre sus comportamientos y características únicas."
- **Post Excerpt**: "Descubre las ardillas del bosque y sus fascinantes comportamientos."
- **Post Permalink**: "animales-bosque-ardillas"
- **Featured Image**: "URL de la imagen destacada"
- **Categories**: "Animales, Bosque, Ardillas"
- **Tags**: "Mamíferos, Naturaleza"

### Archivo CSV Ejemplo

| post_title                    | post_content                                                                                   | post_excerpt                                                  | post_permalink                  | featured_image  | categories                             | tags              |
|-------------------------------|------------------------------------------------------------------------------------------------|----------------------------------------------------------------|--------------------------------|-----------------|------------------------------------------|-------------------|
| Animales del Bosque: Ardillas | Explora la vida de las ardillas en su hábitat natural. Conoce más sobre sus comportamientos.    | Descubre las ardillas del bosque y sus fascinantes comportamientos. | animales-bosque-ardillas       | (URL de imagen) | Animales, Bosque, Ardillas               | Mamíferos, Naturaleza  |
| Animales del Bosque: Ciervos  | Conoce la majestuosidad de los ciervos en los bosques. Aprende sobre su hábitat y su vida diaria. | Descubre los ciervos del bosque y su vida diaria.              | animales-bosque-ciervos         | (URL de imagen) | Animales, Bosque, Ciervos                | Mamíferos, Fauna       |

---

### Configuración de Widgets y Filtrado

Una vez que importes los posts, puedes usar los widgets de Elementor para mostrar estos posts en las páginas que desees. Puedes configurar el filtrado de los widgets para mostrar posts específicos según las categorías o etiquetas que definiste en el CSV.

1. **Usa el widget "Posts" de Elementor**:
   - Agrega el widget "Posts" a tu página.
   - En las opciones del widget, selecciona "Query" (Consulta) y elige "Categories" para filtrar los posts por categorías específicas.

2. **Configura el filtrado**:
   - Puedes configurar filtros adicionales basados en etiquetas u otros criterios.
   - Asegúrate de que las categorías y etiquetas estén correctamente configuradas para que el filtrado funcione como deseas.
