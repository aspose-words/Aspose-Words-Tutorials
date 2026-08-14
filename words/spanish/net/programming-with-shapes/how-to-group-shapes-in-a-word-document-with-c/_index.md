---
category: general
date: 2026-08-14
description: Cómo agrupar formas en un documento de Word usando C#. Aprende a crear
  un documento de Word, insertar una forma rectangular, agrupar formas en Word y guardar
  el documento como docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- create word document
- insert rectangle shape
- group shapes in word
- save document as docx
language: es
lastmod: 2026-08-14
og_description: Cómo agrupar formas en un documento de Word usando C#. Sigue este
  tutorial completo para crear un archivo de Word, insertar una forma rectangular,
  agrupar formas en Word y guardar el resultado como un docx.
og_image_alt: Screenshot showing how to group shapes in a Word document using C#
og_title: Cómo agrupar formas en un documento de Word con C# – guía paso a paso
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to group shapes in a Word document using C#. Learn to create Word
    document, insert rectangle shape, group shapes in Word, and save document as docx.
  headline: How to group shapes in a Word document with C#
  type: TechArticle
- description: How to group shapes in a Word document using C#. Learn to create Word
    document, insert rectangle shape, group shapes in Word, and save document as docx.
  name: How to group shapes in a Word document with C#
  steps:
  - name: Create a new blank document
    text: The first thing you do when you want to **create Word document** programmatically
      is instantiate a `Document` object. This object represents the entire .docx
      file in memory.
  - name: Insert a rectangle shape
    text: To demonstrate **insert rectangle shape**, we use the `InsertShape` method.
      The rectangle will act as the first member of the group.
  - name: Insert an ellipse shape
    text: Next, we **insert ellipse shape** (the API calls it `Ellipse`). This will
      be the second member of the group.
  - name: Group the rectangle and ellipse
    text: Now we answer the central question **how to group shapes** in a Word document.
      Aspose.Words provides `AppendGroupShape` to create a group container, and then
      you call `Group()` on that container.
  - name: Save the document as a DOCX file
    text: The final step is to **save document as docx**. You can choose any path
      you like; the example uses a placeholder `"YOUR_DIRECTORY"` that you should
      replace with a real folder.
  - name: Expected output
    text: When you open `groupedShapes.docx` in Microsoft Word, you will see a light‑blue
      rectangle and a light‑coral ellipse locked together. Clicking either shape selects
      both, allowing you to move or resize them as a single unit.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: Cómo agrupar formas en un documento de Word con C#
url: /es/net/programming-with-shapes/how-to-group-shapes-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo agrupar formas en un documento de Word con C#

Si necesitas **cómo agrupar formas** en un documento de Word, esta guía te muestra los pasos exactos usando C# y la biblioteca Aspose.Words. Verás cómo crear un documento de Word, insertar una forma rectangular, agrupar formas en Word y, finalmente, **guardar el documento como docx**—todo en un único programa ejecutable.

Crear y manipular formas es un requisito común al generar informes, contratos o folletos de marketing de forma programática. Al final de este tutorial tendrás un fragmento de código reutilizable que podrás insertar en cualquier proyecto .NET.

## Requisitos previos

- .NET 6.0 o posterior instalado  
- Visual Studio 2022 (o cualquier IDE que soporte .NET)  
- Una licencia de Aspose.Words para .NET (o una prueba gratuita)  
- Familiaridad básica con la sintaxis de C#  

No se requieren paquetes NuGet adicionales más allá de `Aspose.Words`.

## Cómo agrupar formas en un documento de Word

El núcleo de la solución es un proceso de cinco pasos. Cada paso se explica en detalle, y el código fuente completo se proporciona al final del artículo.

### Paso 1: Crear un nuevo documento en blanco

Lo primero que haces cuando deseas **crear un documento de Word** programáticamente es instanciar un objeto `Document`. Este objeto representa todo el archivo .docx en memoria.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document doc = new Document();

// Obtain a DocumentBuilder to add content
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Por qué es importante:** `DocumentBuilder` es un asistente de alto nivel que te permite insertar texto, tablas y formas sin manejar manualmente el árbol de nodos subyacente.

### Paso 2: Insertar una forma rectangular

Para demostrar **insertar forma rectangular**, usamos el método `InsertShape`. El rectángulo actuará como el primer miembro del grupo.

```csharp
// Insert a rectangle (100x50 points) at the current cursor position
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// Optional: set a fill color so the shape is visible
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
```

**Por qué es importante:** Las formas se posicionan en relación al punto de inserción. Establecer un color de relleno te ayuda a ver la forma cuando abres el documento resultante.

### Paso 3: Insertar una forma elíptica

A continuación, **insertamos forma elíptica** (la API la llama `Ellipse`). Esta será el segundo miembro del grupo.

```csharp
// Insert an ellipse (80x40 points) right after the rectangle
Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 40);
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```

**Por qué es importante:** Al insertar la elipse inmediatamente después del rectángulo, ambas formas terminan en el mismo párrafo, lo que simplifica la agrupación posterior.

### Paso 4: Agrupar el rectángulo y la elipse

Ahora respondemos a la pregunta central **cómo agrupar formas** en un documento de Word. Aspose.Words proporciona `AppendGroupShape` para crear un contenedor de grupo, y luego llamas a `Group()` sobre ese contenedor.

```csharp
// Get the first paragraph of the document (where the shapes live)
Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;

// Create a group shape that contains the rectangle and ellipse
Shape groupedShape = firstParagraph.AppendGroupShape(new[] { rectangleShape, ellipseShape });

// Turn the container into a true group – the shapes will move and scale together
groupedShape.Group();
```

**Por qué es importante:** Una vez agrupadas, cualquier transformación (mover, cambiar tamaño, rotar) aplicada a `groupedShape` afecta automáticamente tanto al rectángulo como a la elipse. Esto es esencial para mantener la consistencia del diseño en documentos generados.

### Paso 5: Guardar el documento como archivo DOCX

El paso final es **guardar el documento como docx**. Puedes elegir cualquier ruta que desees; el ejemplo usa un marcador de posición `"YOUR_DIRECTORY"` que deberías reemplazar con una carpeta real.

```csharp
// Define the output path (ensure the directory exists)
string outputPath = @"C:\Temp\groupedShapes.docx";

// Save the document in DOCX format
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Document saved successfully to {outputPath}");
```

**Por qué es importante:** Guardar como DOCX preserva los metadatos de agrupación, de modo que cuando abras el archivo en Microsoft Word verás el rectángulo y la elipse actuando como un solo objeto.

## Ejemplo completo y ejecutable

A continuación se muestra el programa completo que combina los cinco pasos. Cópialo en un nuevo proyecto de consola, restaura el paquete NuGet Aspose.Words y ejecútalo.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new blank document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Insert a rectangle shape (100x50 points)
            Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            rectangleShape.FillColor = System.Drawing.Color.LightBlue;

            // Step 3: Insert an ellipse shape (80x40 points)
            Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 40);
            ellipseShape.FillColor = System.Drawing.Color.LightCoral;

            // Step 4: Group the rectangle and ellipse
            Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;
            Shape groupedShape = firstParagraph.AppendGroupShape(new[] { rectangleShape, ellipseShape });
            groupedShape.Group();

            // Step 5: Save the document as DOCX
            string outputPath = @"C:\Temp\groupedShapes.docx";
            doc.Save(outputPath, SaveFormat.Docx);

            Console.WriteLine($"Document saved successfully to {outputPath}");
        }
    }
}
```

### Salida esperada

Cuando abras `groupedShapes.docx` en Microsoft Word, verás un rectángulo azul claro y una elipse coral claro bloqueados juntos. Al hacer clic en cualquiera de las formas se seleccionan ambas, permitiéndote moverlas o redimensionarlas como una única unidad.

## Preguntas frecuentes y casos límite

| Question | Answer |
|----------|--------|
| **¿Puedo agrupar más de dos formas?** | Sí. Pasa cualquier número de objetos `Shape` a `AppendGroupShape`. El método acepta un array, por lo que puedes construir una colección dinámicamente. |
| **¿Qué pasa si necesito que el grupo esté anclado a una celda de tabla?** | Inserta las formas dentro del párrafo de la celda, luego llama a `AppendGroupShape` sobre ese párrafo. El grupo hereda el anclaje de la celda. |
| **¿Afecta la agrupación al XML subyacente?** | Aspose.Words escribe un elemento `<w:grpSp>` que contiene las formas hijas. Word reconoce esto como un grupo, preservando la posición relativa. |
| **¿Cómo desagrupar más tarde?** | Llama a `groupedShape.Ungroup()`; el método devuelve las formas individuales para que puedas manipularlas por separado. |
| **¿Hay un impacto de rendimiento al agrupar muchas formas?** | Agrupar en sí es poco costoso, pero renderizar grupos muy grandes (cientos de formas) puede aumentar el tamaño del archivo. Considera aplanar las imágenes si el tamaño se vuelve un problema. |

## Consejos profesionales

- **Establece posiciones explícitas** (`Left`, `Top`) si necesitas una alineación precisa antes de agrupar.  
- **Usa `Shape.WrapType = WrapType.Inline`** cuando quieras que el grupo se comporte como un elemento de párrafo en lugar de un objeto flotante.  
- **Aplica un estilo de línea** al grupo (`groupedShape.LineFormat`) para dar a toda la colección un borde.  
- **Reutiliza el grupo**: después de llamar a `Group()`, puedes clonar `groupedShape` e insertar el clon en otra parte del documento.

## Próximos pasos

Ahora que sabes **cómo agrupar formas** en un documento de Word, puedes explorar temas relacionados como:

- **Insertar forma rectangular** con texto o imágenes personalizadas dentro de la forma.  
- **Crear diagramas complejos** anidando grupos (agrupar un grupo).  
- **Exportar el documento como PDF** manteniendo la agrupación de formas (`doc.Save("output.pdf", SaveFormat.Pdf)`).  

Cada uno de estos se basa en los mismos fundamentos cubiertos aquí, por lo que estás bien posicionado para ampliar tu conjunto de herramientas de automatización de Word.

## Conclusión

Este tutorial demostró **cómo agrupar formas** en un documento de Word usando C#. Aprendiste a **crear un documento de Word**, **insertar forma rectangular**, **agrupar formas en Word**, y finalmente **guardar el documento como docx**. Con el ejemplo completo y ejecutable y los consejos prácticos proporcionados, puedes integrar la agrupación de formas en cualquier flujo de trabajo de generación de documentos. ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Crear forma de grupo en documento de Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insertar formas en documentos de Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Crear forma rectangular en Word usando C# – Guía paso a paso](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}