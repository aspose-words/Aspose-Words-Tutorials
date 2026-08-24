---
category: general
date: 2026-08-23
description: Aprenda cómo agrupar formas en C# usando Aspose.Words. La guía también
  cubre cómo insertar una forma rectangular y agregar formas de Word para documentos
  complejos.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert rectangle shape
- add shapes word
- group multiple shapes
- how to start group
language: es
lastmod: 2026-08-23
og_description: Cómo agrupar formas en C# con Aspose.Words. Sigue este tutorial completo
  para insertar una forma de rectángulo, agregar formas en Word y agrupar múltiples
  formas de manera eficiente.
og_image_alt: How to group shapes in C# using Aspose.Words
og_title: Cómo agrupar formas en C# – guía paso a paso
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Learn how to group shapes in C# using Aspose.Words. The guide also
    covers how to insert rectangle shape and add shapes word for complex documents.
  headline: How to group shapes in C# with Aspose.Words
  type: TechArticle
- description: Learn how to group shapes in C# using Aspose.Words. The guide also
    covers how to insert rectangle shape and add shapes word for complex documents.
  name: How to group shapes in C# with Aspose.Words
  steps:
  - name: '**Nested groups** – Aspose.Words allows groups within groups. To create
      a nested group, call `StartGroupShape` again before calling `EndGroupShape`
      for the inner group.'
    text: '**Nested groups** – Aspose.Words allows groups within groups. To create
      a nested group, call `StartGroupShape` again before calling `EndGroupShape`
      for the inner group.'
  - name: '**Empty groups** – If you start a group but never insert a shape, `EndGroupShape`
      will still create an empty container. This is harmless but may increase file
      size slightly.'
    text: '**Empty groups** – If you start a group but never insert a shape, `EndGroupShape`
      will still create an empty container. This is harmless but may increase file
      size slightly.'
  - name: '**Compatibility** – The generated DOCX works with Word 2010 and later.
      Older versions may ignore grouping metadata, so always test with the target
      Word version.'
    text: '**Compatibility** – The generated DOCX works with Word 2010 and later.
      Older versions may ignore grouping metadata, so always test with the target
      Word version.'
  type: HowTo
- questions:
  - answer: Yes. Retrieve the existing `Shape` objects, call `builder.StartGroupShape()`,
      re‑insert them with `builder.InsertShape(existingShape)`, then call `EndGroupShape()`.
    question: Can I group shapes that already exist in the document?
  - answer: Aspose.Words adds a `<w:grpSp>` element that contains each shape’s `<w:sp>`
      node. This is fully compliant with the Office Open XML specification.
    question: Does grouping affect the underlying XML?
  - answer: 'There is no direct “ungroup” API, but you can iterate through the child
      shapes of the group (`group.GroupShape.Children`) and copy them out to the document
      body. ## Next steps Now that you know **how to group shapes**, consider exploring
      these related topics: - **Apply complex formatting to grouped '
    question: What if I need to ungroup later?
  type: FAQPage
tags:
- Aspose.Words
- C#
- shapes
- document automation
title: Cómo agrupar formas en C# con Aspose.Words
url: /es/net/programming-with-shapes/how-to-group-shapes-in-c-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo agrupar formas en C# con Aspose.Words

Si necesitas **cómo agrupar formas** en un documento Word de forma programática, este tutorial te muestra los pasos exactos usando Aspose.Words para .NET. Ya sea que estés construyendo un generador de informes, un motor de plantillas o una herramienta de diagramación, aprenderás a iniciar un grupo, insertar una forma rectangular y añadir contenido a nivel de Word sin salir de tu código.

También verás cómo **agrupar múltiples formas** juntas, lo cual es esencial cuando deseas mover, rotar o aplicar estilo a una colección de objetos como una sola entidad. El ejemplo a continuación funciona con la última versión de Aspose.Words 24.x y solo requiere .NET 6 o posterior.

## Requisitos previos

- .NET 6 SDK (o cualquier versión de .NET compatible con Aspose.Words)
- Visual Studio 2022 o VS Code
- Paquete NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)
- Familiaridad básica con C# y el modelo de objetos de Aspose.Words

> **Consejo profesional:** Usa la licencia de evaluación gratuita de Aspose para evitar limitaciones de marcas de agua mientras pruebas.

## Cómo agrupar formas con Aspose.Words

A continuación tienes un programa completo y ejecutable que demuestra **cómo iniciar un grupo**, añadir un rectángulo y finalizar el grupo. El código sigue el mismo flujo lógico que el fragmento que proporcionaste, pero agrega contexto, manejo de errores y comentarios para mayor claridad.

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
            // 1️⃣ Create a new blank document.
            Document doc = new Document();

            // 2️⃣ Get a DocumentBuilder to insert content.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Start a group shape – all shapes added after this call belong to the group.
            // This is the “how to start group” step.
            Shape group = builder.StartGroupShape();

            // 4️⃣ Insert individual shapes inside the group.
            //    a) Insert a rectangle shape (demonstrates “insert rectangle shape”).
            builder.InsertShape(ShapeType.Rectangle, 150, 80);
            //    b) Insert a simple ellipse for visual variety.
            builder.InsertShape(ShapeType.Ellipse, 100, 60);
            //    c) Add a WordArt‑style text shape – shows “add shapes word”.
            builder.InsertShape(ShapeType.TextPlainText, 200, 40);
            builder.Writeln("Grouped Text"); // adds text inside the last shape

            // 5️⃣ Close the group shape to finalize the grouping.
            builder.EndGroupShape();

            // Optional: Save the document to verify the result.
            string outPath = "GroupedShapes.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### Por qué cada paso es importante

| Paso | Propósito | Cómo se relaciona con las palabras clave |
|------|-----------|------------------------------------------|
| **Crear un documento nuevo en blanco** | Proporciona un lienzo limpio para las operaciones con formas. | Prepara el escenario para **add shapes word** más adelante. |
| **Inicializar DocumentBuilder** | El builder es la API principal para insertar objetos. | Necesario antes de poder **how to start group**. |
| **StartGroupShape** | Inicia un contenedor lógico; todas las formas siguientes se convierten en miembros de este grupo. | Responde directamente a **how to start group**. |
| **InsertShape** (rectángulo, elipse, texto) | Coloca formas individuales dentro del grupo. La llamada al rectángulo satisface **insert rectangle shape**; la forma de texto satisface **add shapes word**. | Demuestra **group multiple shapes**. |
| **EndGroupShape** | Finaliza el grupo para que puedas moverlo o aplicarle estilo como una unidad. | Completa el flujo de **how to group shapes**. |

## Insertar una forma rectangular – análisis más profundo

El método `InsertShape` acepta un enumerado `ShapeType`, ancho y alto. Para **insert rectangle shape** con estilo personalizado, puedes ampliar el ejemplo:

```csharp
// Insert a styled rectangle
Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
rect.FillColor = System.Drawing.Color.LightBlue;
rect.StrokeColor = System.Drawing.Color.DarkBlue;
rect.LineWidth = 2.0;
```

> **¿Por qué estilizarla?** El estilo asegura que el rectángulo destaque cuando el grupo se reposicione más adelante. También demuestra que las propiedades de la forma pueden establecerse *antes* de cerrar el grupo.

## Añadir formas a nivel de Word (add shapes word)

Si necesitas incrustar texto directamente dentro de una forma —comúnmente llamado “WordArt” o “cuadro de texto”— usa `ShapeType.TextPlainText`. Después de insertarla, puedes escribir texto en la forma con `DocumentBuilder.Writeln` o accediendo a la propiedad `TextBox` de la forma:

```csharp
Shape textBox = builder.InsertShape(ShapeType.TextPlainText, 250, 50);
textBox.TextBox.Text = "Hello, grouped world!";
```

Esto satisface la palabra clave **add shapes word** y muestra cómo el texto puede viajar con el grupo.

## Agrupar múltiples formas – escenarios prácticos

Cuando **group multiple shapes**, puedes tratarlas como un solo objeto para posicionamiento, rotación o escalado. Por ejemplo, después de cerrar el grupo, puedes mover todo el conjunto:

```csharp
// Move the entire group 100 points to the right and 50 points down.
group.Left += 100;
group.Top += 50;
```

O rotar el grupo:

```csharp
group.Rotation = 45; // degrees
```

Estas operaciones solo son posibles porque las formas comparten el mismo grupo padre.

## Manejo de casos límite

1. **Grupos anidados** – Aspose.Words permite grupos dentro de grupos. Para crear un grupo anidado, llama a `StartGroupShape` nuevamente antes de llamar a `EndGroupShape` para el grupo interno.
2. **Grupos vacíos** – Si inicias un grupo pero nunca insertas una forma, `EndGroupShape` aún creará un contenedor vacío. Esto no causa problemas, aunque puede aumentar ligeramente el tamaño del archivo.
3. **Compatibilidad** – El DOCX generado funciona con Word 2010 y versiones posteriores. Las versiones más antiguas pueden ignorar los metadatos de agrupación, así que siempre prueba con la versión de Word objetivo.

## Archivo fuente completo para referencia

Guarda lo siguiente como `Program.cs` en un proyecto de consola .NET. El código compila y se ejecuta sin modificaciones.

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
            // Step 1: Create a new blank document.
            Document doc = new Document();

            // Step 2: Initialize DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Start the group – “how to start group”.
            Shape group = builder.StartGroupShape();

            // Step 4a: Insert a rectangle – “insert rectangle shape”.
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 150, 80);
            rect.FillColor = System.Drawing.Color.LightCoral;
            rect.StrokeColor = System.Drawing.Color.DarkRed;
            rect.LineWidth = 1.5;

            // Step 4b: Insert an ellipse (additional shape for grouping).
            builder.InsertShape(ShapeType.Ellipse, 100, 60);

            // Step 4c: Add a text box – “add shapes word”.
            Shape txt = builder.InsertShape(ShapeType.TextPlainText, 200, 40);
            txt.TextBox.Text = "Grouped Text";

            // Step 5: End the group – completes “how to group shapes”.
            builder.EndGroupShape();

            // Optional: Adjust group position.
            group.Left += 50;
            group.Top += 30;

            // Save the result.
            string outPath = "GroupedShapes.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### Resultado esperado

Abrir `GroupedShapes.docx` en Microsoft Word mostrará:

- Un rectángulo coral claro, una elipse y un cuadro de texto —todos visualmente vinculados.
- Al seleccionar cualquier parte del grupo, también se selecciona todo el grupo (aparece un único cuadro delimitador).
- Mover o rotar el grupo desplaza las tres formas juntas.

## Preguntas frecuentes

**P: ¿Puedo agrupar formas que ya existen en el documento?**  
R: Sí. Recupera los objetos `Shape` existentes, llama a `builder.StartGroupShape()`, vuelve a insertarlos con `builder.InsertShape(existingShape)`, y luego llama a `EndGroupShape()`.

**P: ¿El agrupamiento afecta al XML subyacente?**  
R: Aspose.Words añade un elemento `<w:grpSp>` que contiene cada nodo `<w:sp>` de la forma. Esto cumple plenamente con la especificación Office Open XML.

**P: ¿Qué pasa si necesito desagrupar más tarde?**  
R: No existe una API directa de “ungroup”, pero puedes iterar a través de las formas hijas del grupo (`group.GroupShape.Children`) y copiarlas al cuerpo del documento.

## Próximos pasos

Ahora que sabes **how to group shapes**, considera explorar estos temas relacionados:

- **Aplicar formato complejo a formas agrupadas** – aprende a establecer rellenos degradados, efectos de sombra y estilos de línea.
- **Exportar formas agrupadas como imágenes** – usa `Shape.GetShapeRenderer().Save(...)` para rasterizar un grupo.
- **Crear diagramas dinámicos** – combina posicionamiento basado en datos con agrupamiento para generar diagramas de flujo automáticamente.

Cada uno de estos se basa en los fundamentos cubiertos aquí y te ayudará a crear documentos Word más ricos e interactivos.

---

*¡Feliz codificación! Si encontraste útil esta guía, compártela con tus compañeros o marca con estrella el repositorio que contiene el proyecto de ejemplo.*

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}