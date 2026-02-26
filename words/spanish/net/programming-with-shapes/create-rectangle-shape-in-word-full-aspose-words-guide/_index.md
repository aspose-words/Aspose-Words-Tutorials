---
category: general
date: 2026-02-26
description: Crea una forma rectangular en Word usando Aspose.Words y aprende cómo
  agregar la forma a Word, aplicar sombra a la forma y establecer la transparencia
  de la forma en minutos.
draft: false
keywords:
- create rectangle shape
- add shape to word
- apply shadow to shape
- set shape transparency
- rectangle with shadow
language: es
og_description: Crea una forma rectangular en Word usando Aspose.Words. Aprende a
  agregar una forma a Word, aplicar sombra a la forma y establecer la transparencia
  de la forma rápidamente.
og_title: Crear forma de rectángulo en Word – Guía completa de Aspose.Words
tags:
- Aspose.Words
- C#
- Word Automation
title: Crear forma de rectángulo en Word – Guía completa de Aspose.Words
url: /es/net/programming-with-shapes/create-rectangle-shape-in-word-full-aspose-words-guide/
---

any tables: we translated.

Check any bullet lists: we translated.

Check any italic *text*: we kept.

Check any bold **text**: we kept.

Check any technical terms: we kept English for those phrases.

Now produce final content.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear forma rectangular en Word – Guía completa de Aspose.Words

¿Alguna vez necesitaste **create rectangle shape** en un documento de Word pero no sabías por dónde empezar? No estás solo—muchos desarrolladores se topan con ese obstáculo al automatizar informes o facturas. En este tutorial recorreremos un ejemplo completo, listo‑para‑ejecutar que muestra cómo **add shape to Word**, aplicar una sombra sutil y controlar la transparencia de la forma, todo con Aspose.Words para .NET.

Al final de la guía tendrás un archivo `.docx` que contiene un rectángulo limpio con una sombra pulida—perfecto para branding, call‑outs, o simplemente para que tu documento se vea un poco más profesional. No se requieren herramientas externas, solo unas pocas líneas de C#.

## Lo que necesitarás

- **Aspose.Words for .NET** (la última versión a principios de 2026). Puedes obtenerlo de NuGet (`Install-Package Aspose.Words`).
- Un entorno de desarrollo .NET (Visual Studio, Rider, o VS Code con la extensión C#).
- Familiaridad básica con la sintaxis de C#—nada elegante, solo las habituales sentencias `using` y la creación de objetos.

Si ya los tienes, genial—¡vamos a sumergirnos!

## Crear forma rectangular – Pasos principales

A continuación se muestra el código fuente completo. Copia‑pega en un nuevo proyecto de consola, pulsa **F5**, y verás aparecer `ShadowDemo.docx` en la carpeta que especifiques.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // Needed for Color

// Step 1: Create a new blank document.
Document document = new Document();

// Step 2: Insert a rectangle shape and define its size.
Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
{
    Width  = 200,   // Width in points (≈2.78 inches)
    Height = 100    // Height in points (≈1.39 inches)
};

// Step 3: Apply a shadow with fine‑grained control over its appearance.
rectangleShape.Shadow = new Shadow
{
    BlurRadius   = 5.0,                     // Softness of the shadow edge
    Distance     = 4.0,                     // How far the shadow is offset
    Direction    = 45,                      // Angle of the offset (degrees)
    Color        = Color.Gray,              // Shadow colour
    Transparency = 0.2,                     // Opacity (0 = opaque, 1 = fully transparent)
    Spread       = 0.3                      // Size of the shadow spread
};

// Step 4: Add the shape to the first paragraph of the document.
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

// Step 5: Save the document with the shadowed shape.
document.Save("ShadowDemo.docx");
```

### Por qué funciona esto

- **`Document`** es el punto de entrada; representa todo el archivo Word.
- **`Shape`** con `ShapeType.Rectangle` indica a Aspose que queremos un objeto de dibujo rectangular.
- Establecer **`Width`** y **`Height`** le da a la forma un tamaño determinista; de lo contrario, usa un marcador de posición diminuto.
- El objeto **`Shadow`** nos permite afinar cada aspecto visual: desenfoque, distancia, dirección, color, transparencia y expansión. Ese es el corazón de *apply shadow to shape*.
- Finalmente, **`AppendChild`** inserta la forma en el primer párrafo del documento, que es la forma más sencilla de *add shape to Word* sin lidiar con tablas o encabezados.

Al abrir `ShadowDemo.docx`, verás un rectángulo gris colocado cómodamente en el documento, su sombra inclinada hacia abajo‑derecha en un ángulo de 45°. La sombra no es un bloque sólido; el radio de desenfoque suaviza los bordes, y la transparencia hace que parezca una sombra natural en lugar de una superposición dura.

![ejemplo de crear forma rectangular](image.png "crear forma rectangular con sombra en Word usando Aspose.Words")

*(La imagen anterior muestra el resultado final del fragmento de código.)*

## Añadir forma al documento Word – Opciones de ubicación

El ejemplo usa el **primer párrafo** porque es la forma más rápida de ver algo en pantalla. En escenarios reales podrías querer:

- Insertar la forma en una **sección** o **encabezado/pie de página** específico.
- Colocarla dentro de una **celda de tabla** para alinearla con datos tabulares.
- Envolverla con opciones de **ajuste de texto** (p. ej., `WrapType.Square`) para que el texto circundante fluya alrededor del rectángulo.

Aquí tienes una variación rápida que coloca la forma en un nuevo párrafo con un estilo personalizado:

```csharp
Paragraph para = new Paragraph(document);
para.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading2;
para.AppendChild(rectangleShape);
document.FirstSection.Body.AppendChild(para);
```

*Consejo profesional:* Siempre agrega la forma **después** de configurar sus propiedades; de lo contrario, puede que necesites llamar a `UpdateLayout` para refrescar la apariencia visual.

## Aplicar sombra a la forma – Ajuste fino del aspecto

Las sombras pueden cambiar drásticamente la estética de un documento. La clase `Shadow` expone varias propiedades:

| Propiedad      | Qué controla                                   | Valores típicos |
|---------------|------------------------------------------------|-----------------|
| `BlurRadius`  | Suavidad de los bordes de la sombra            | 2.0 – 10.0      |
| `Distance`    | Cuán lejos está la sombra de la forma          | 1.0 – 8.0       |
| `Direction`   | Ángulo en grados (0 = izquierda, 90 = arriba)  | 0 – 360         |
| `Color`       | Color de la sombra (cualquier `System.Drawing.Color`) | Gray, Black, Custom |
| `Transparency`| Opacidad (0 = totalmente opaco, 1 = invisible) | 0.0 – 0.5       |
| `Spread`      | Expansión de la sombra antes de aplicar el desenfoque | 0.0 – 1.0       |

Si deseas un aspecto **sutil y profesional**, mantén `BlurRadius` alrededor de 4‑6 y `Transparency` cerca de 0.2, como en el código anterior. Para un **efecto dramático**, aumenta `Distance` a 6, establece `Direction` a 135°, y reduce `Transparency` a 0.05.

## Establecer transparencia de la forma y expansión de la sombra

La transparencia no solo afecta a la sombra; también puedes hacer que el propio rectángulo sea parcialmente translúcido:

```csharp
rectangleShape.FillColor = Color.LightBlue;
rectangleShape.Transparency = 0.3; // 30% transparent fill
```

Combinar un relleno semi‑transparente con una sombra suave suele producir una sensación de UI moderna—ideal para paneles de control o maquetas de diseño incrustadas en informes.

### Casos límite a vigilar

1. **Older Word versions** (pre‑2007) no soportan algunas propiedades de sombra. Si apuntas a archivos `.doc`, considera simplificar la sombra (p. ej., establecer `BlurRadius` a 0).
2. **High DPI displays** pueden renderizar la sombra ligeramente diferente. Prueba en el entorno objetivo si la fidelidad visual es crítica.
3. **Overlapping shapes**—Aspose renderiza sombras en el orden en que se añaden. Inserta las formas de atrás hacia adelante para evitar oclusiones no deseadas.

## Guardar y verificar el resultado

El método `Document.Save` detecta automáticamente el formato de salida a partir de la extensión del archivo. Para un archivo **`.docx`** obtienes el formato Open XML, que la mayoría de los procesadores de Word modernos entienden. Si necesitas una versión **PDF** con el mismo estilo visual, simplemente cambia la extensión:

```csharp
document.Save("ShadowDemo.pdf");
```

Al abrir el `ShadowDemo.docx` generado (o `ShadowDemo.pdf`) deberías ver un **rectángulo con sombra** limpio, confirmando que has creado con éxito *create rectangle shape* y *apply shadow to shape* usando Aspose.Words.

## Preguntas frecuentes

**Q: ¿Puedo usar una forma diferente, como una elipse?**  
A: Por supuesto. Cambia `ShapeType.Rectangle` por `ShapeType.Ellipse` (o cualquier otro enum `ShapeType`). Las propiedades de sombra permanecen iguales.

**Q: ¿Qué pasa si necesito que el rectángulo sea clicable?**  
A: Puedes asignar un hipervínculo a la forma:

```csharp
rectangleShape.Href = "https://example.com";
```

**Q: ¿Esto funciona en .NET 6+?**  
A: Sí. Aspose.Words 23.11 y versiones posteriores soportan completamente .NET 6, .NET 7 y .NET 8. Simplemente referencia el paquete NuGet correspondiente.

**Q: ¿Cómo cambio el color de la sombra para que coincida con mi marca?**  
A: Usa cualquier `System.Drawing.Color` que desees:

```csharp
rectangleShape.Shadow.Color = Color.FromArgb(255, 30, 144, 255); // DodgerBlue
```

## Conclusión

Hemos cubierto todo lo que necesitas para **create rectangle shape** en un documento Word, **add shape to Word**, **apply shadow to shape**, y **set shape transparency**. El código completo y ejecutable está al principio de esta página, y las explicaciones deberían darte la confianza suficiente para ajustar tamaños, colores y parámetros de sombra en cualquier proyecto.

¿Listo para el siguiente paso? Prueba experimentando con:

- Múltiples formas superpuestas para crear un efecto de insignia.
- Tamaño dinámico basado en el contenido del documento (p. ej., calcular el ancho a partir de una columna de tabla).
- Exportar el documento a PDF o HTML manteniendo la sombra.

No dudes en dejar un comentario si encuentras algún problema, o compartir tus propias variaciones del tema “rectángulo con sombra”.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}