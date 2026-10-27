---
category: general
date: 2026-09-08
description: Aprende a crear un documento Word en blanco, insertar una forma de rectángulo
  y agrupar varias formas usando C#. Sigue esta guía paso a paso.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert rectangle shape
- group multiple shapes
- add shapes to group
language: es
lastmod: 2026-09-08
og_description: Crea un documento Word en blanco, inserta una forma de rectángulo
  y agrupa varias formas en C#. Este tutorial te guía a través del proceso completo.
og_image_alt: Screenshot showing a blank Word document with a grouped rectangle and
  ellipse shape
og_title: Crear documento Word en blanco con formas agrupadas en C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to create blank Word document, insert rectangle shape and
    group multiple shapes using C#. Follow this step‑by‑step guide.
  headline: How to create blank Word document with grouped shapes
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Cómo crear un documento Word en blanco con formas agrupadas
url: /es/java/images-shapes/how-to-create-blank-word-document-with-grouped-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo crear un documento Word en blanco con formas agrupadas

Si necesitas **crear un documento Word en blanco** que contenga gráficos personalizados, esta guía te muestra exactamente cómo hacerlo. Aprenderás a **insertar una forma rectangular**, **agrupar múltiples formas** y **añadir formas al grupo** usando Aspose.Words for .NET.

Un documento en blanco te brinda un lienzo limpio, y agrupar formas te permite mover, cambiar el tamaño o rotarlas como una sola unidad. Este tutorial cubre cada paso—desde la inicialización del documento hasta guardar el archivo final—para que puedas copiar el código en tu propio proyecto y ver resultados inmediatos.

## Lo que necesitarás

Antes de comenzar, asegúrate de tener:

* .NET 6.0 o posterior (el código también funciona con .NET Framework 4.6+)
* Una licencia válida de Aspose.Words for .NET (la evaluación gratuita funciona para pruebas)
* Un IDE como Visual Studio 2022 o Visual Studio Code
* Familiaridad básica con la sintaxis de C#

No se requieren paquetes NuGet adicionales más allá de `Aspose.Words`.

## Cómo crear un documento Word en blanco

El primer paso es instanciar un objeto `Document`. Este objeto representa un archivo `.docx` vacío que puedes editar con un `DocumentBuilder`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new blank document and a builder to edit it.
            Document doc = new Document();               // Blank Word document
            DocumentBuilder builder = new DocumentBuilder(doc);
```

El constructor `Document` crea un **documento Word en blanco** en memoria. El `DocumentBuilder` proporciona una API fluida para insertar texto, imágenes y objetos de dibujo.

## Insertar una forma rectangular en el documento

A continuación, agrega una forma rectangular. El rectángulo será el primer hijo del grupo que crearemos más adelante.

```csharp
            // Step 2: Insert a rectangle shape (100 pt wide, 50 pt high).
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            // Optional: give the rectangle a fill color for visibility.
            rectangle.FillColor = System.Drawing.Color.LightBlue;
```

Llamar a `InsertShape` con `ShapeType.Rectangle` **inserta una forma rectangular** en la posición actual del cursor. El ancho y la altura se expresan en puntos (1 pt ≈ 1/72 in).

## Agrupar múltiples formas juntas

Un `GroupShape` actúa como un contenedor. Todas las formas hijas dentro del grupo se mueven y transforman juntas. Primero, crea el grupo y luego agrega el rectángulo que acabamos de crear.

```csharp
            // Step 3: Create a group shape that will hold multiple child shapes.
            GroupShape group = builder.InsertGroupShape();
            // Append the rectangle as the first child of the group.
            group.AppendChild(rectangle);
```

El método `InsertGroupShape` coloca un grupo vacío en el cursor del builder. Al añadir el rectángulo, **agrupamos múltiples formas**—el rectángulo pasa a formar parte de la colección interna de nodos del grupo.

## Añadir formas al grupo y guardar el archivo

Ahora agrega una segunda forma—una elipse—para demostrar cómo varios objetos comparten el mismo contenedor. Después, guarda el documento.

```csharp
            // Step 4: Insert an ellipse shape (80 pt wide, 80 pt high).
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
            ellipse.FillColor = System.Drawing.Color.Pink;

            // Append the ellipse to the same group.
            group.AppendChild(ellipse);

            // Step 5: Save the document containing the grouped shapes.
            string outputPath = "GroupShapeDemo.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

La llamada a `InsertShape` **añade formas al grupo** cuando añades el `Shape` devuelto al `GroupShape`. Guardar el `Document` escribe un archivo `.docx` que puedes abrir en Microsoft Word, LibreOffice o cualquier visor compatible.

### Resultado esperado

Al abrir *GroupShapeDemo.docx*, verás una página en blanco con un objeto agrupado que contiene un rectángulo azul claro y una elipse rosa. Seleccionar el grupo te permite mover ambas formas juntas, confirmando que **agrupar múltiples formas** funcionó como se esperaba.

## ¿Por qué usar un GroupShape?

* **Transformaciones atómicas** – Escalar, rotar o mover el grupo afecta a todos los hijos de manera uniforme.
* **Organización lógica** – Mantiene los gráficos relacionados juntos, facilitando el mantenimiento de la estructura del documento.
* **Rendimiento** – Renderizar un solo contenedor suele ser más rápido que manejar muchas formas independientes.

Si necesitas modificar un hijo individual más adelante, puedes recuperarlo de `group.ChildNodes` por índice o por su propiedad `Name`.

## Variaciones comunes y casos límite

| Scenario                                 | How to adapt the code                                                            |
|------------------------------------------|----------------------------------------------------------------------------------|
| **Tipos de forma diferentes**                | Replace `ShapeType.Rectangle` or `ShapeType.Ellipse` with any other `ShapeType` |
| **Agregar texto dentro de una forma**           | Use `Shape.TextPath.Text = "Hello"` after inserting the shape                    |
| **Establecer un ángulo de rotación**             | `group.Rotation = 45;` (degrees)                                                 |
| **Guardar como PDF en lugar de DOCX**        | `doc.Save("GroupShapeDemo.pdf");`                                                |
| **Aplicar un borde al grupo**       | `group.LineStyle = LineStyle.Single;`<br>`group.LineWidth = 1.5;`               |

## Consejos profesionales

* **Nombra tus formas** – `rectangle.Name = "MyRect";` facilita localizarlas más tarde.
* **Usa posicionamiento relativo** – Establece `group.RelativeHorizontalPosition` a `RelativeHorizontalPosition.Page` si deseas que el grupo permanezca anclado a los márgenes de la página.
* **Libera recursos** – Envuelve el `Document` en un bloque `using` cuando trabajes en aplicaciones más grandes para liberar la memoria no administrada rápidamente.

## Código fuente completo para copiar y pegar rápidamente

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new blank document and a builder to edit it.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a rectangle shape (100 pt × 50 pt) and give it a light‑blue fill.
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            rectangle.FillColor = System.Drawing.Color.LightBlue;

            // Create a group shape and add the rectangle as its first child.
            GroupShape group = builder.InsertGroupShape();
            group.AppendChild(rectangle);

            // Insert an ellipse shape (80 pt × 80 pt) with a pink fill.
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
            ellipse.FillColor = System.Drawing.Color.Pink;
            group.AppendChild(ellipse);

            // Save the document. The file will contain the grouped rectangle and ellipse.
            string outputPath = "GroupShapeDemo.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Copia el código en un nuevo proyecto de consola, restaura el paquete NuGet `Aspose.Words` y ejecútalo. El archivo de salida aparece en la carpeta `bin/Debug/net6.0` del proyecto (o equivalente).

## Próximos pasos

Ahora que puedes **crear un documento Word en blanco**, **insertar una forma rectangular** y **agrupar múltiples formas**, podrías explorar:

* Añadir **cuadros de texto** dentro de un grupo para crear diagramas etiquetados.
* Exportar el gráfico agrupado a una imagen con `doc.Save("image.png", SaveFormat.Png)`.
* Combinar grupos con tablas para informes con formato enriquecido.

Experimenta con diferentes propiedades de forma, jerarquías de grupos y formatos de exportación para aprovechar al máximo las capacidades de dibujo de Aspose.Words.

--- 

*Recuerda*: agrupar formas es una manera poderosa de mantener tus documentos Word ordenados y tu código mantenible. ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}