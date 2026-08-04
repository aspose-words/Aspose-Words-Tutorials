---
category: general
date: 2026-08-04
description: Insertar forma de rectángulo en un documento de Word con C#. Aprende
  cómo agrupar formas en Word, guardar el documento como docx y usar DocumentBuilder
  para diseños avanzados.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to group shapes
- group shapes in word
- save document as docx
- how to use builder
language: es
lastmod: 2026-08-04
og_description: Inserte una forma rectangular en un archivo de Word usando C# y luego
  agrupe las formas para diseños avanzados. Este tutorial también cubre cómo guardar
  el documento como docx y usar DocumentBuilder de manera eficiente.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  created with C# DocumentBuilder
og_title: Insertar forma de rectángulo en Word – Guía paso a paso en C#
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Insert rectangle shape in a Word document with C#. Learn how to group
    shapes in Word, save document as docx, and use DocumentBuilder for advanced layouts.
  headline: Insert rectangle shape in Word using C# – complete guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Insertar forma de rectángulo en Word usando C# – guía completa
url: /es/java/images-shapes/insert-rectangle-shape-in-word-using-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Insertar forma de rectángulo en Word usando C# – guía completa

Si necesitas **insertar forma de rectángulo** en un documento Word usando C#, este tutorial te muestra exactamente cómo hacerlo. También aprenderás **cómo agrupar formas** en Word, **guardar el documento como docx**, y **cómo usar Builder** para un código limpio y mantenible.

Trabajar con formas es un requisito común al generar informes, certificados o diseños personalizados de forma programática. Al final de esta guía tendrás un ejemplo completamente ejecutable que crea un rectángulo, agrega una elipse, los agrupa y guarda el resultado como un archivo DOCX.

## Requisitos previos

* .NET 6.0 o posterior instalado  
* Visual Studio 2022 (o cualquier IDE que soporte C#)  
* La biblioteca **Aspose.Words for .NET** (disponible vía NuGet)  

Puedes agregar la biblioteca con el siguiente comando:

```bash
dotnet add package Aspose.Words
```

## Insertar forma de rectángulo con DocumentBuilder

El primer paso es crear un nuevo `Document` y un `DocumentBuilder`. El builder te brinda una API fluida para insertar contenido, incluidas formas.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document.
        Document document = new Document();

        // Initialize the builder that will edit the document.
        DocumentBuilder builder = new DocumentBuilder(document);
```

La instancia de `DocumentBuilder` es el objeto central que usarás para **insertar forma de rectángulo** y otros elementos. Rastrea la posición actual del cursor dentro del documento, de modo que cualquier inserción ocurre exactamente donde lo necesitas.

## Cómo insertar una forma de rectángulo

Con el builder listo, llama a `InsertShape`. Especificas el `ShapeType`, el ancho y la altura en puntos (1 pt ≈ 1/72 in).

```csharp
        // Insert a rectangle of 100 pt width and 50 pt height.
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.FillColor = System.Drawing.Color.LightBlue;
        rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;
```

*Por qué es importante*: Establecer `FillColor` y `StrokeColor` hace que el rectángulo sea visualmente distinto, lo que ayuda cuando luego lo agrupas con otras formas.

## Cómo agrupar formas en Word

Agrupar formas te permite mover, rotar o formatear varios objetos como una sola entidad. Después de insertar el rectángulo, agrega otra forma (una elipse en este ejemplo) y luego crea un `GroupShape`.

```csharp
        // Insert an ellipse of 80 pt diameter.
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.FillColor = System.Drawing.Color.LightCoral;
        ellipseShape.StrokeColor = System.Drawing.Color.Maroon;

        // Insert an empty group container.
        GroupShape groupShape = builder.InsertGroupShape();

        // Add the rectangle and ellipse to the group.
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
```

La llamada `InsertGroupShape` crea un marcador de posición que puede contener cualquier número de formas hijas. Al añadir el rectángulo y la elipse, efectivamente **agrupas formas en Word**. El grupo se comporta como una sola forma: puedes reposicionarlo, aplicar un borde o cambiar su tamaño sin afectar la disposición interna de cada hijo.

### Consejo profesional

Después de agrupar, puedes cambiar la posición del grupo relativa a la página:

```csharp
        // Move the whole group 150 pt right and 100 pt down.
        groupShape.Left = 150;
        groupShape.Top = 100;
```

## Guardar documento como docx

Una vez que las formas están organizadas, necesitas persistir el archivo. El método `Document.Save` determina automáticamente el formato a partir de la extensión del archivo. Para **guardar el documento como docx**, pasa una ruta que termine con `.docx`.

```csharp
        // Save the document to the output folder.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        document.Save(outputPath);
    }
}
```

Ejecutar el programa crea `output.docx`. Abre el archivo en Microsoft Word y verás un rectángulo azul claro y una elipse coral claro agrupados juntos. Puedes hacer clic en el grupo y moverlo como un solo objeto.

## Cómo usar DocumentBuilder de manera eficaz

`DocumentBuilder` es más que un inserter de formas; también maneja texto, tablas, encabezados y pies de página. Cuando combinas la creación de formas con texto, recuerda restablecer el cursor si necesitas insertar contenido en otro lugar:

```csharp
        // Move the cursor to a new paragraph after the group.
        builder.Writeln(); // Inserts a line break.
        builder.Font.Size = 12;
        builder.Writeln("Shapes have been added and grouped successfully.");
```

Mantener el estado del builder explícito evita sobrescrituras accidentales y hace que el código sea más fácil de mantener.

## Casos límite y variaciones

| Situación | Enfoque recomendado |
|-----------|----------------------|
| **Más de dos formas** | Inserta cada forma, luego llama a `AppendChild` para cada forma antes de guardar. |
| **Grupos anidados** | Crea un grupo, agrega formas, luego inserta ese grupo en otro `GroupShape`. |
| **Unidades de medida diferentes** | Usa `builder.ConvertPixelsToPoints` si tienes dimensiones en píxeles. |
| **Compatibilidad con versiones antiguas de Word** | Guarda como `.doc` cambiando la extensión; la mayoría de las características de forma siguen funcionando. |

## Ejemplo completo y funcional

A continuación se muestra el programa completo que puedes copiar y pegar en un nuevo proyecto de consola. No se requieren fragmentos adicionales.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Insert a rectangle shape.
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.FillColor = System.Drawing.Color.LightBlue;
        rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;

        // 3️⃣ Insert an ellipse shape.
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.FillColor = System.Drawing.Color.LightCoral;
        ellipseShape.StrokeColor = System.Drawing.Color.Maroon;

        // 4️⃣ Create a group shape and add both shapes.
        GroupShape groupShape = builder.InsertGroupShape();
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);

        // Optional: reposition the group.
        groupShape.Left = 150;
        groupShape.Top = 100;

        // 5️⃣ Add a caption below the group.
        builder.Writeln();
        builder.Font.Size = 12;
        builder.Writeln("Grouped rectangle and ellipse created with DocumentBuilder.");

        // 6️⃣ Save the document as DOCX.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        document.Save(outputPath);
    }
}
```

**Resultado esperado**: Al abrir `output.docx` se muestra un rectángulo azul claro y una elipse coral claro agrupados, posicionados a 150 pt del margen izquierdo y 100 pt de la parte superior. El título aparece debajo del grupo.

## Conclusión

Ahora sabes cómo **insertar forma de rectángulo** en un archivo Word usando C#, **cómo agrupar formas en Word**, y **cómo guardar el documento como docx** con el `DocumentBuilder` de Aspose.Words. Al dominar estos pasos puedes crear diseños complejos—certificados, informes o formularios personalizados—completamente mediante código.

A continuación, explora temas relacionados como **agregar cuadros de texto**, **trabajar con tablas**, o **exportar a PDF**. Cada uno de estos se basa en los mismos fundamentos de `DocumentBuilder` que acabas de practicar.

¿Listo para automatizar tus documentos Word? Intenta ampliar el ejemplo con más formas, aplicando degradados, o iterando sobre datos para generar un informe completo en una sola ejecución. ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Crear forma de grupo en documento Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insertar formas en documentos Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Crear forma de rectángulo en Word con Aspose.Words – Guía paso a paso](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}