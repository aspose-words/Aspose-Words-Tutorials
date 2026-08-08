---
category: general
date: 2026-08-07
description: Insertar forma de rectángulo en C# usando Aspose.Words y aprender cómo
  ocultar la forma, establecer el color de relleno y agregar la forma de rectángulo
  a un documento de Word de manera eficiente.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to hide shape
- how to insert shape
- how to set fill color
- add rectangle shape
language: es
lastmod: 2026-08-07
og_description: Inserte una forma rectangular en un documento de Word con C#. Aprenda
  cómo ocultar la forma, establecer el color de relleno y agregar una forma rectangular
  usando Aspose.Words.
og_image_alt: Screenshot showing a hidden yellow rectangle shape inserted into a Word
  document
og_title: Insertar forma de rectángulo en C# – tutorial completo de Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Insert rectangle shape in C# using Aspose.Words and learn how to hide
    shape, set fill color, and add rectangle shape to a Word document efficiently.
  headline: Insert rectangle shape in C# with Aspose.Words – step‑by‑step guide
  type: TechArticle
- description: Insert rectangle shape in C# using Aspose.Words and learn how to hide
    shape, set fill color, and add rectangle shape to a Word document efficiently.
  name: Insert rectangle shape in C# with Aspose.Words – step‑by‑step guide
  steps:
  - name: What each step does
    text: '| Step | Reason | |------|--------| | **Create a new document** | Provides
      a clean canvas; you can also load an existing .docx by passing a file path to
      `new Document(path)`. | | **Initialize DocumentBuilder** | `DocumentBuilder`
      is the high‑level helper that lets you insert text, tables, and shapes'
  - name: 1. Making the shape visible again
    text: 'If a later part of your workflow needs to reveal the hidden rectangle,
      you can toggle the flag:'
  - name: 2. Adding a border (stroke)
    text: 'A hidden shape can still have a visible border when you decide to show
      it. Set the `LineColor` and `LineWidth` properties:'
  - name: 3. Positioning the rectangle absolutely
    text: 'For precise layout control, switch the shape’s `WrapType` to `WrapType.Inline`
      (default) or `WrapType.TopBottom` and adjust `Left`/`Top` properties:'
  - name: 4. Using a different measurement unit
    text: 'Aspose.Words works in points (1 pt = 1/72 inch). If you prefer centimeters,
      convert first:'
  - name: Next steps
    text: '* Explore **how to insert shape** inside tables or headers/footers for
      watermarks. * Combine **add rectangle shape** with content controls to create
      dynamic placeholders. * Review Aspose.Words’ **shape manipulation** API for
      advanced features like rotation, gradient fills, and SVG import.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
- document generation
title: Insertar forma de rectángulo en C# con Aspose.Words – guía paso a paso
url: /es/net/programming-with-shapes/insert-rectangle-shape-in-c-with-aspose-words-step-by-step-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Insertar forma rectangular en C# con Aspose.Words – guía paso a paso

Si necesitas **insertar forma rectangular** en un documento Word desde C#, esta guía te muestra exactamente cómo hacerlo. Verás cómo establecer el color de relleno, ocultar la forma para que no aparezca en el diseño final y guardar el archivo, todo con solo unas pocas líneas de código.

En las siguientes secciones cubrimos todo lo que necesitas saber: requisitos previos, el listado completo de código, explicaciones de cada paso y consejos para variaciones comunes, como volver a hacer visible la forma o usar un color diferente. Al final podrás **añadir forma rectangular** a cualquier archivo .docx de forma programática.

## Requisitos previos

* **Aspose.Words for .NET** (versión 23.10 o posterior). Puedes instalarlo vía NuGet:

  ```bash
  dotnet add package Aspose.Words
  ```

* SDK .NET 6.0 o posterior instalado en tu máquina.
* Un conocimiento básico de C# y Visual Studio (o cualquier IDE que prefieras).

No se requieren bibliotecas adicionales; las API relacionadas con formas forman parte del paquete central de Aspose.Words.

## Insertar forma rectangular con Aspose.Words

El núcleo de la solución es un programa breve y autónomo que crea un documento en blanco, inserta un rectángulo, lo colorea, lo oculta y luego guarda el archivo. A continuación se muestra el código fuente completo con comentarios en línea que explican el *porqué* de cada línea.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // Required for Color struct

// 1️⃣ Create a new, empty Word document.
Document document = new Document();

// 2️⃣ Obtain a DocumentBuilder – the primary API for editing the document.
DocumentBuilder builder = new DocumentBuilder(document);

// 3️⃣ Insert a rectangle shape of 100 × 50 points.
//    ShapeType.Rectangle tells Aspose.Words to create a simple rectangular drawing object.
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// 4️⃣ Set the shape's fill color to yellow.
//    The FillColor property accepts a System.Drawing.Color value.
rectangleShape.FillColor = Color.Yellow;

// 5️⃣ Hide the shape so it does not appear in the rendered document.
//    When Hidden = true, the shape is stored in the file but omitted from layout.
//    This is useful for placeholders, bookmarks, or metadata.
rectangleShape.Hidden = true;

// 6️⃣ Save the document to disk.
//    Change the path to a folder you have write access to.
document.Save(@"C:\Temp\HiddenRectangleShape.docx");
```

### Qué hace cada paso

| Paso | Razón |
|------|--------|
| **Create a new document** | Proporciona un lienzo limpio; también puedes cargar un .docx existente pasando una ruta de archivo a `new Document(path)`. |
| **Initialize DocumentBuilder** | `DocumentBuilder` es el asistente de alto nivel que te permite insertar texto, tablas y formas sin lidiar con árboles de nodos de bajo nivel. |
| **Insert rectangle shape** | El método `InsertShape` devuelve un objeto `Shape` que puedes personalizar más (tamaño, posición, bordes, etc.). |
| **Set fill color** | La propiedad `FillColor` controla el color interior; puedes usar cualquier valor `Color` (`Color.Red`, `Color.FromArgb(255, 0, 255, 0)`, etc.). |
| **Hide the shape** | `Hidden = true` indica a Word que ignore la forma durante el diseño mientras sigue manteniéndola en el XML del documento. Esta es la forma estándar de almacenar objetos invisibles. |
| **Save the document** | Guarda los cambios en un archivo .docx. El archivo guardado contendrá la forma rectangular oculta. |

## Cómo establecer el color de relleno de una forma

Cambiar el color de relleno es tan simple como asignar un `System.Drawing.Color` a la propiedad `FillColor`. Si necesitas un tono personalizado, usa `Color.FromArgb`:

```csharp
// Example: set a semi‑transparent teal fill
rectangleShape.FillColor = Color.FromArgb(128, 0, 128, 128);
```

*Por qué es importante*: El color de relleno se almacena en el XML de la forma (`<w:fill>` atributo). Cuando la forma está oculta, el color sigue existiendo, lo que puede ser útil para procesamiento posterior (p. ej., extraer metadatos basados en códigos de color).

## Cómo ocultar la forma en el documento final

La bandera `Hidden` es una propiedad booleana en la clase `Shape`. Establecerla en `true` garantiza que la forma sea ignorada por el motor de diseño de Word.

```csharp
rectangleShape.Hidden = true;
```

**Problemas comunes**

* **Oculto vs. Visible** – Si más adelante necesitas que la forma aparezca, simplemente establece `Hidden = false`.
* **Compatibilidad** – Las versiones más antiguas de Word (previas a 2007) pueden tratar los objetos de dibujo ocultos de manera diferente. Aspose.Words mantiene la compatibilidad almacenando la bandera en el elemento OOXML apropiado.

## Cómo insertar una forma programáticamente

Aunque el ejemplo usa un rectángulo, el mismo método `InsertShape` funciona para muchas otras formas (elipse, triángulo, línea, etc.). El primer argumento es un valor del enum `ShapeType`:

```csharp
// Insert an ellipse with the same dimensions
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
ellipse.FillColor = Color.LightBlue;
```

**Consejo**: Si necesitas colocar la forma en una ubicación específica de la página, usa `builder.MoveTo` para establecer el punto de inserción antes de llamar a `InsertShape`.

## Añadir forma rectangular a un documento existente

A menudo estarás mejorando una plantilla en lugar de comenzar desde cero. Reemplaza el paso 1 con:

```csharp
// Load an existing .docx file
Document document = new Document(@"C:\Templates\ReportTemplate.docx");
```

Todos los pasos posteriores permanecen idénticos, y el rectángulo se añadirá dondequiera que el cursor del builder esté posicionado (generalmente al final del documento por defecto).

## Manejo de casos límite y variaciones

### 1. Volver a hacer visible la forma

Si una parte posterior de tu flujo de trabajo necesita revelar el rectángulo oculto, puedes alternar la bandera:

```csharp
rectangleShape.Hidden = false;   // Shape will now be rendered
```

### 2. Añadir un borde (trazo)

Una forma oculta aún puede tener un borde visible cuando decides mostrarla. Establece las propiedades `LineColor` y `LineWidth`:

```csharp
rectangleShape.LineColor = Color.Black;
rectangleShape.LineWeight = 1.5; // points
```

### 3. Posicionar el rectángulo de forma absoluta

Para un control preciso del diseño, cambia el `WrapType` de la forma a `WrapType.Inline` (predeterminado) o `WrapType.TopBottom` y ajusta las propiedades `Left`/`Top`:

```csharp
rectangleShape.WrapType = WrapType.TopBottom;
rectangleShape.Left = 72;   // 1 inch from the left margin
rectangleShape.Top = 144;   // 2 inches from the top margin
```

### 4. Usar una unidad de medida diferente

Aspose.Words trabaja en puntos (1 pt = 1/72 pulgada). Si prefieres centímetros, conviértelos primero:

```csharp
float cmToPoints = 28.3465f; // 1 cm ≈ 28.3465 pt
float width = 5 * cmToPoints;   // 5 cm wide
float height = 2 * cmToPoints;  // 2 cm tall
Shape cmRectangle = builder.InsertShape(ShapeType.Rectangle, width, height);
```

## Ejemplo completo ejecutable

A continuación está el programa *completo* que puedes copiar, pegar y ejecutar. Incluye todas las directivas `using` necesarias y usa rutas absolutas que deberías ajustar a tu entorno.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class InsertRectangleShapeDemo
{
    static void Main()
    {
        // Create a blank document.
        Document doc = new Document();

        // Use DocumentBuilder to edit the document.
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 100 × 50 pt rectangle.
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // Set the fill color to yellow.
        rect.FillColor = Color.Yellow;

        // Hide the shape so it does not affect layout.
        rect.Hidden = true;

        // Save the result.
        string outputPath = @"C:\Temp\HiddenRectangleShape.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Resultado esperado**: El archivo `HiddenRectangleShape.docx` se abre en Microsoft Word sin *forma visible*, pero el rectángulo oculto está presente en el XML del documento. Puedes verificar su existencia abriendo el .docx como un archivo zip e inspeccionando `word/document.xml` en busca de un elemento `<w:shape>` con los atributos `w:fill="yellow"` y `w:hidden="true"`.

## Conclusión

Ahora sabes cómo **insertar forma rectangular** en un documento Word usando C# y Aspose.Words, cómo **establecer el color de relleno** y cómo **ocultar la forma** para que permanezca invisible en el diseño final. El mismo patrón funciona para otros tipos de formas, colores personalizados y plantillas existentes. Experimenta con bordes, posicionamiento absoluto y diferentes unidades de medida para adaptar la forma a tus requisitos exactos.

### Próximos pasos

* Explora **cómo insertar forma** dentro de tablas o encabezados/pies de página para marcas de agua.
* Combina **añadir forma rectangular** con controles de contenido para crear marcadores de posición dinámicos.
* Revisa la API de **manipulación de formas** de Aspose.Words para funciones avanzadas como rotación, rellenos degradados e importación de SVG.

¡Siéntete libre de adaptar el código a tu propio proyecto y cuéntanos en los comentarios qué desafío relacionado con formas resolviste a continuación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Crear forma rectangular en Word usando C# – Guía paso a paso](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Tutorial de sombra de forma en Aspose.Words – Añadir una sombra a una forma de Word en C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Crear forma de grupo en documento Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}