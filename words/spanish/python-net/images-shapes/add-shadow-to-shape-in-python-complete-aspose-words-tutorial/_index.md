---
category: general
date: 2026-06-08
description: Agrega sombra a la forma usando Aspose.Words para Python y establece
  el color de relleno de la forma en solo unos pocos pasos. Aprende el flujo de trabajo
  completo con código ejecutable.
draft: false
keywords:
- add shadow to shape
- set shape fill color
- Aspose.Words Python shadow
- shape formatting Python
- PDF generation Aspose
language: es
og_description: Agrega sombra a una forma con Aspose.Words para Python y establece
  instantáneamente el color de relleno de la forma. Sigue este tutorial paso a paso
  para generar un PDF.
og_title: Agregar sombra a una forma en Python – Guía completa de Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-08'
  description: Add shadow to shape using Aspose.Words for Python and set shape fill
    color in just a few steps. Learn the full workflow with runnable code.
  headline: Add Shadow to Shape in Python – Complete Aspose.Words Tutorial
  type: TechArticle
- description: Add shadow to shape using Aspose.Words for Python and set shape fill
    color in just a few steps. Learn the full workflow with runnable code.
  name: Add Shadow to Shape in Python – Complete Aspose.Words Tutorial
  steps:
  - name: Create the Document and Builder
    text: '```python import aspose.words as aw from aspose.words.drawing import ShadowEffect,
      ShadowType, Color'
  - name: Insert a Rectangle Shape and Set Its Fill Color
    text: '```python # Insert a rectangle shape of width 200 points and height 100
      points. rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE,
      200, 100)'
  - name: Define the Shadow Effect
    text: '```python # Create a new shadow effect object. shape_shadow = ShadowEffect()
      shape_shadow.type = ShadowType.OUTER # outer shadow around the shape shape_shadow.blur_radius
      = 10.0 # softer edges shape_shadow.distance = 5.0 # how far the shadow sits
      from the shape shape_shadow.direction = 45 # angle in'
  - name: Apply the Shadow to the Shape
    text: '```python # Attach the shadow effect to the rectangle. rectangle_shape.shadow_effect
      = shape_shadow ```'
  - name: Save the Document as PDF
    text: '```python # Choose a folder you have write access to. output_path = "YOUR_DIRECTORY/ShadowShape.pdf"
      doc.save(output_path) print(f"Document saved to {output_path}") ```'
  type: HowTo
tags:
- Aspose.Words
- Python
- Document Automation
title: Añadir sombra a una forma en Python – Tutorial completo de Aspose.Words
url: /es/python/images-shapes/add-shadow-to-shape-in-python-complete-aspose-words-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Agregar sombra a una forma en Python – Tutorial completo de Aspose.Words

¿Alguna vez te has preguntado cómo **agregar sombra a una forma** al generar un documento con Aspose.Words para Python? No eres el único. Ya sea que estés creando una plantilla de informe, un folleto de marketing o un diagrama técnico, una sombra sutil puede hacer que un rectángulo destaque y se vea más profesional.  

En esta guía también te mostraremos **cómo establecer el color de relleno de la forma**, para que obtengas un rectángulo totalmente estilizado listo para exportar a PDF. La solución es sencilla, el código está listo para ejecutarse y el razonamiento detrás de cada línea se explica en inglés sencillo.

## Qué cubre este tutorial

- Inicializar un documento Aspose.Words y un builder.  
- Insertar una forma rectangular y **establecer su color de relleno**.  
- Definir y aplicar un **efecto de sombra** a esa forma.  
- Guardar el resultado como PDF.  
- Ejemplo completo y ejecutable más consejos para errores comunes.

Al final del artículo podrás insertar un rectángulo con estilo en cualquier archivo Word o PDF con solo unas pocas líneas de Python. Sin herramientas externas, sin conjeturas.

> **Requisitos previos** – Necesitas Python 3.7+ y el paquete `aspose-words` (`pip install aspose-words`). Cualquier IDE o editor de texto de tu elección sirve; Visual Studio Code funciona muy bien.

---

## Agregar sombra a una forma – Paso a paso

A continuación desglosamos el proceso en bloques lógicos. Cada paso incluye el código exacto que necesitas, una breve explicación de *por qué* es importante y un consejo rápido para que no te encuentres con obstáculos más adelante.

### Paso 1: Crear el documento y el builder

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowType, Color

# Create a new, empty document.
doc = aw.Document()

# DocumentBuilder gives us a convenient way to add content.
builder = aw.DocumentBuilder(doc)
```

**Por qué es importante:** `Document` es el contenedor de todo—páginas, estilos, imágenes y formas. `DocumentBuilder` es la API de alto nivel que nos permite colocar objetos sin preocuparnos por los árboles de nodos de bajo nivel.

### Paso 2: Insertar una forma rectangular y establecer su color de relleno

```python
# Insert a rectangle shape of width 200 points and height 100 points.
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# Set the interior color of the shape.
rectangle_shape.fill_color = Color.BLUE   # <-- set shape fill color
```

**Por qué es importante:** La forma actúa como un lienzo para nuestra sombra. Al **establecer el color de relleno de la forma** nos aseguramos de que el rectángulo no sea solo una caja transparente; se convierte en un elemento visible que la sombra puede acentuar. Puedes reemplazar `Color.BLUE` con cualquier valor RGB o incluso un degradado si necesitas más estilo.

> **Consejo profesional:** Si planeas reutilizar el mismo color en muchas formas, guárdalo en una variable (`my_fill = Color.from_argb(0, 120, 200, 255)`) y reutiliza esa referencia.

### Paso 3: Definir el efecto de sombra

```python
# Create a new shadow effect object.
shape_shadow = ShadowEffect()
shape_shadow.type = ShadowType.OUTER          # outer shadow around the shape
shape_shadow.blur_radius = 10.0               # softer edges
shape_shadow.distance = 5.0                   # how far the shadow sits from the shape
shape_shadow.direction = 45                   # angle in degrees (45° = diagonal)
shape_shadow.color = Color.from_argb(128, 0, 0, 0)  # semi‑transparent black
```

**Por qué es importante:** Una sombra no es solo un truco visual; transmite profundidad y jerarquía. `blur_radius` controla la suavidad, `distance` determina el desplazamiento y `direction` permite simular una fuente de luz. Ajusta estos valores para que coincidan con tu lenguaje de diseño.

### Paso 4: Aplicar la sombra a la forma

```python
# Attach the shadow effect to the rectangle.
rectangle_shape.shadow_effect = shape_shadow
```

**Por qué es importante:** Hasta que se ejecuta esta línea, la forma permanece plana. Asignar `shadow_effect` indica a Aspose.Words que renderice el rectángulo con la sombra definida cuando se guarde el documento.

### Paso 5: Guardar el documento como PDF

```python
# Choose a folder you have write access to.
output_path = "YOUR_DIRECTORY/ShadowShape.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

**Por qué es importante:** Guardar como PDF bloquea el estilo visual, haciendo que la sombra aparezca exactamente como la diseñaste. También puedes guardar como `.docx` si necesitas editar más tarde—Aspose.Words maneja ambos formatos sin problemas.

---

## Establecer el color de relleno de la forma – Personalizando la apariencia

Si necesitas un tono diferente, reemplaza la asignación `Color.BLUE` con cualquiera de los siguientes ejemplos:

```python
# Solid RGB color
rectangle_shape.fill_color = Color.from_argb(255, 255, 165, 0)   # orange

# Semi‑transparent fill
rectangle_shape.fill_color = Color.from_argb(128, 0, 128, 0)    # 50% transparent green
```

> **Por qué podrías querer esto:** Un relleno semitransparente combinado con una sombra puede crear un efecto “vidrio” popular en maquetas de UI modernas.

---

## Ejemplo completo y funcional

Aquí tienes el script completo en un solo bloque. Copia y pégalo en un archivo llamado `shadow_shape.py` y ejecútalo—suponiendo que hayas instalado `aspose-words`.

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowType, Color

# 1️⃣ Create document and builder
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# 2️⃣ Insert rectangle and set fill color
rect = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
rect.fill_color = Color.BLUE          # set shape fill color

# 3️⃣ Configure shadow
shadow = ShadowEffect()
shadow.type = ShadowType.OUTER
shadow.blur_radius = 10.0
shadow.distance = 5.0
shadow.direction = 45
shadow.color = Color.from_argb(128, 0, 0, 0)

# 4️⃣ Apply shadow
rect.shadow_effect = shadow

# 5️⃣ Save as PDF
output = "ShadowShape.pdf"
doc.save(output)
print(f"✅ PDF generated: {output}")
```

**Salida esperada:** Abre `ShadowShape.pdf` y verás un rectángulo azul con una sombra negra suave y diagonal desplazada hacia la esquina inferior derecha. La sombra debería verse ligeramente difuminada, dando a la forma una apariencia elevada.

---

## Errores comunes y consejos profesionales

| Problema | Por qué ocurre | Solución |
|------|----------------|-----|
| **Sombra no visible** | El relleno de la forma es completamente transparente o el visor de PDF desactiva las sombras. | Asegúrate de que `fill_color` sea opaco (`alpha = 255`) o ajusta la opacidad del `color` de la sombra. |
| **Error de ruta de archivo** | `YOUR_DIRECTORY` no existe o no tienes permiso de escritura. | Usa `os.makedirs("YOUR_DIRECTORY", exist_ok=True)` antes de `doc.save`. |
| **Importación incorrecta** | Intentar importar `ShadowEffect` del sub‑módulo incorrecto. | Importa exactamente como se muestra: `from aspose.words.drawing import ShadowEffect, ShadowType, Color`. |
| **Color inesperado** | Usar `Color.from_argb` con el orden incorrecto (alpha, rojo, verde, azul). | Recuerda el orden: **alpha**, **rojo**, **verde**, **azul**. |

---

## Próximos pasos – Expande tu kit de herramientas de formas

Ahora que sabes cómo **agregar sombra a una forma** y **establecer el color de relleno de la forma**, puedes explorar:

- **Rellenos degradados** (`LinearGradientBrush`) para fondos más ricos.  
- **Múltiples sombras** (interior + exterior) encadenando objetos `ShadowEffect`.  
- **Otros tipos de forma** (`Ellipse`, `Polygon`) para crear íconos o elementos de diagramas de flujo.  
- **Incrustar el PDF** en una respuesta web o adjunto de correo electrónico usando Flask o Django.

Cada uno de estos temas se basa en los mismos conceptos básicos cubiertos aquí, por lo que te sentirás como en casa.

---

## Conclusión

Hemos recorrido el proceso completo de **agregar sombra a una forma** en Aspose.Words para Python mientras también **establecemos el color de relleno de la forma**. Desde la creación del documento hasta la exportación a PDF, el código es autónomo y listo para producción.  

Siéntete libre de ajustar el radio de desenfoque, la distancia o el color para que coincidan con las directrices de tu marca. Si encuentras un caso límite o tienes una solicitud de función, deja un comentario abajo—¡feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Configura la licencia de Aspose.Words en Python](/words/english/python-net/getting-started/aspose-words-license-python-setup/)
- [Crear forma rectangular en Word con Aspose.Words – Guía paso a paso](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Tutorial de sombra de forma Aspose.Words – Agregar una sombra a una forma Word en C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}