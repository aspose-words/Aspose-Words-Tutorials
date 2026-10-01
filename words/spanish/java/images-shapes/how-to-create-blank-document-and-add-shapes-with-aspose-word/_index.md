---
category: general
date: 2026-09-30
description: Crear un documento en blanco e insertar una forma rectangular, una elipse
  y agrupar varias formas en C# usando Aspose.Words. Aprende cómo insertar formas
  y cómo crear un grupo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- insert rectangle shape
- group multiple shapes
- how to insert shapes
- how to create group
language: es
lastmod: 2026-09-30
og_description: Crea un documento en blanco en C# y aprende cómo insertar formas y
  agrupar varias formas con Aspose.Words. Sigue el tutorial paso a paso.
og_image_alt: Screenshot of a C# program that creates a blank document, inserts a
  rectangle and ellipse, and groups them together.
og_title: Crear un documento en blanco y agrupar formas en C# – Guía de Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Create blank document and insert rectangle shape, ellipse, and group
    multiple shapes in C# using Aspose.Words. Learn how to insert shapes and how to
    create group.
  headline: How to create blank document and add shapes with Aspose.Words in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- document automation
- shapes
title: Cómo crear un documento en blanco y agregar formas con Aspose.Words en C#
url: /es/java/images-shapes/how-to-create-blank-document-and-add-shapes-with-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo crear un documento en blanco y agregar formas con Aspose.Words en C#

Si necesita **crear un documento en blanco** y completarlo con gráficos, esta guía le muestra exactamente cómo. Verá cómo **insertar una forma rectangular**, agregar otros objetos de dibujo y luego **agrupar varias formas** para que se comporten como una sola unidad.

Trabajar con formas es un requisito frecuente al generar contratos, certificados o informes personalizados. En este tutorial aprenderá el flujo de trabajo completo, desde la inicialización del documento hasta el guardado del archivo final, utilizando la API Aspose.Words para .NET.

## Requisitos previos

Antes de comenzar, asegúrese de tener:

* SDK de .NET 6.0 (o posterior) instalado  
* Una licencia válida de Aspose.Words para .NET (la versión de prueba gratuita funciona para este ejemplo)  
* Un IDE como Visual Studio 2022 o Visual Studio Code  

No se requieren paquetes NuGet adicionales más allá de `Aspose.Words`.

## Cómo crear un documento en blanco y trabajar con formas

El primer paso es instanciar un objeto `Document`. Este objeto representa el archivo Word en memoria y le brinda acceso al `DocumentBuilder`, que es la herramienta principal para insertar contenido.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Por qué es importante:** Un documento en blanco le proporciona un lienzo limpio. El `DocumentBuilder` mantiene el punto de inserción actual, de modo que cada forma que añada se coloca automáticamente en la página correspondiente.

## Insertar forma rectangular y otras formas

A continuación, agregamos un rectángulo y una elipse. Ambas llamadas utilizan el mismo método `InsertShape`, que es la forma recomendada **de insertar formas** en Aspose.Words.

```csharp
        // Step 2: Insert a rectangle shape (100 × 50 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangle.StrokeColor = System.Drawing.Color.Blue;   // optional styling
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // Step 3: Insert an ellipse shape (80 × 80 points)
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.StrokeColor = System.Drawing.Color.Green;
        ellipse.FillColor = System.Drawing.Color.LightGreen;
```

*El método `InsertShape` posiciona automáticamente la forma en la ubicación actual del cursor.* Si necesita una colocación precisa, puede ajustar `Shape.Left` y `Shape.Top` después de la inserción.

## Agrupar varias formas en un solo objeto

Ahora combinamos el rectángulo y la elipse en una entidad lógica única. Agrupar es útil cuando desea mover o cambiar el tamaño de varias formas a la vez.

```csharp
        // Step 4: Create a group shape that will hold multiple shapes
        GroupShape groupShape = builder.InsertGroupShape();

        // Step 5: Add the rectangle and ellipse to the group
        groupShape.AppendChild(rectangle);
        groupShape.AppendChild(ellipse);

        // Optional: Apply a border to the whole group
        groupShape.StrokeColor = System.Drawing.Color.DarkGray;
        groupShape.LineWidth = 1.5;
```

**Cómo funciona:** `InsertGroupShape` crea un contenedor que se comporta como cualquier otro `Shape`. Al llamar a `AppendChild`, mueve las formas existentes al contenedor, que actualiza automáticamente sus coordenadas relativas.

### Consejo práctico

Si más adelante necesita **crear un grupo** de forma programática para más de dos formas, simplemente repita `AppendChild` para cada instancia adicional de `Shape`. El grupo puede contener cualquier número de objetos de dibujo, incluidas imágenes, cuadros de texto o incluso otros grupos.

## Ejemplo completo – cómo insertar formas y guardar el documento

A continuación se muestra el programa completo y ejecutable que demuestra cada paso descrito hasta ahora. Ejecutar el código genera un archivo `ShapesDemo.docx` que contiene un rectángulo, una elipse y una forma agrupada.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Create a blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2. Insert rectangle shape
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangle.StrokeColor = System.Drawing.Color.Blue;
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // 3. Insert ellipse shape
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.StrokeColor = System.Drawing.Color.Green;
        ellipse.FillColor = System.Drawing.Color.LightGreen;

        // 4. Create a group shape
        GroupShape groupShape = builder.InsertGroupShape();

        // 5. Add shapes to the group
        groupShape.AppendChild(rectangle);
        groupShape.AppendChild(ellipse);

        // Optional styling for the group
        groupShape.StrokeColor = System.Drawing.Color.DarkGray;
        groupShape.LineWidth = 1.5;

        // 6. Save the document
        string outputPath = "ShapesDemo.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Salida esperada:** Al abrir `ShapesDemo.docx` en Microsoft Word se muestra una sola página con un rectángulo azul, una elipse verde y un borde gris que rodea al grupo. Mover el grupo desplaza ambas formas juntas, confirmando que la operación **agrupar varias formas** se realizó con éxito.

## Preguntas frecuentes y manejo de casos límite

| Pregunta | Respuesta |
|----------|-----------|
| *¿Qué pasa si necesito las formas en una página específica?* | Llame a `builder.MoveToDocumentEnd();` antes de insertar las formas, o use `builder.MoveToSection(sectionIndex);` para dirigirse a una sección concreta. |
| *¿Puedo agregar texto dentro de una forma agrupada?* | Sí. Cree una `Shape` de tipo `ShapeType.TextBox`, configure su texto y luego `AppendChild` al `GroupShape`. |
| *¿Las dimensiones de la forma usan puntos o píxeles?* | Aspose.Words utiliza **puntos** (1 pt = 1/72 pulgada). Esto garantiza un dimensionado coherente en impresoras y pantallas. |
| *¿Cómo cambiar la rotación del grupo?* | Establezca `groupShape.RotationAngle = 45;` (grados). Todas las formas hijas giran alrededor del origen del grupo. |

## Conclusión

Ahora sabe cómo **crear un documento en blanco**, **insertar una forma rectangular**, **cómo insertar formas** como elipses y **agrupar varias formas** en un solo objeto usando Aspose.Words para .NET. El ejemplo de código completo muestra el enfoque recomendado, y los consejos anteriores le ayudarán a adaptar la solución a escenarios más complejos, como agregar cuadros de texto o rotar grupos.

¿Listo para seguir explorando? Intente agregar una forma de imagen al grupo, experimente con diferentes colores de relleno o genere un informe de varias páginas donde cada página contenga su propio diagrama agrupado. Los mismos principios se aplican, por lo que puede escalar este patrón a cualquier proyecto de automatización de documentos.

## ¿Qué deberías aprender a continuación?

Los tutoriales siguientes cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarle a dominar características adicionales de la API y explorar enfoques de implementación alternativos en sus propios proyectos.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}