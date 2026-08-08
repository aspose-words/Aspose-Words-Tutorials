---
category: general
date: 2026-08-07
description: Cómo agrupar formas en Word con Aspose.Words y agregar formas a un documento
  Word usando C#. Sigue esta guía paso a paso para obtener código limpio y reutilizable.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes in word
- add shapes to word document
language: es
lastmod: 2026-08-07
og_description: Cómo agrupar formas en Word usando Aspose.Words para .NET. Este tutorial
  le muestra cómo agregar formas a un documento de Word, agruparlas y guardar el archivo
  con código C# claro.
og_image_alt: Screenshot of a rectangle and ellipse grouped in a Word document created
  with Aspose.Words
og_title: Cómo agrupar formas en Word – guía rápida de C#
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to group shapes in Word with Aspose.Words and add shapes to Word
    document using C#. Follow this step‑by‑step guide for clean, reusable code.
  headline: How to group shapes in Word and add shapes to Word document
  type: TechArticle
- description: How to group shapes in Word with Aspose.Words and add shapes to Word
    document using C#. Follow this step‑by‑step guide for clean, reusable code.
  name: How to group shapes in Word and add shapes to Word document
  steps:
  - name: Create a document and a builder
    text: A `Document` object represents the entire DOCX file. `DocumentBuilder` provides
      a convenient API for editing the document.
  - name: Add the rectangle shape
    text: A rectangle is created by specifying `ShapeType.Rectangle`. Width, height,
      and location are set in points (1 pt ≈ 1/72 in).
  - name: Add the ellipse shape
    text: The ellipse uses `ShapeType.Ellipse`. Its size and position are independent
      of the rectangle, which allows you to control the final layout of the group.
  - name: Group the two shapes
    text: '`GroupShape` acts as a container that treats its children as a single object.
      This is the essential operation for **how to group shapes in Word**.'
  - name: Insert the grouped shape into the document
    text: '`DocumentBuilder.InsertNode` places the `GroupShape` at the current cursor
      location. Because we have not moved the builder, the group appears at the start
      of the first page.'
  - name: Save the document
    text: Finally, write the DOCX file to disk. Use a full path that your application
      can write to.
  - name: Expected output
    text: Open `GroupShape.docx`. You will see a single visual object that contains
      a blue rectangle on the left and a green ellipse on the right. Selecting the
      object in Word highlights both shapes simultaneously—proof that **how to group
      shapes in Word** succeeded.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Cómo agrupar formas en Word y agregar formas a un documento de Word
url: /es/net/programming-with-shapes/how-to-group-shapes-in-word-and-add-shapes-to-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo agrupar formas en Word y agregar formas a un documento Word

Si necesitas **how to group shapes in Word**, esta guía te lleva a través del proceso completo usando Aspose.Words for .NET. También aprenderás **add shapes to Word document** con unas pocas líneas de código C#, de modo que el resultado esté listo para cualquier escenario de informes o plantillas.

El tutorial cubre todo lo que necesitas: paquetes NuGet requeridos, un archivo fuente completo y una explicación de por qué cada paso es importante. Al final podrás generar un DOCX que contiene un rectángulo y una elipse combinados en una sola forma grupal.

## Requisitos previos

* .NET 6.0 SDK o posterior instalado  
* Visual Studio 2022 (o cualquier IDE que soporte .NET)  
* Paquete NuGet Aspose.Words for .NET (`Aspose.Words`) – la prueba gratuita funciona para pruebas, pero una licencia elimina las marcas de agua de evaluación  

Estos elementos son las únicas dependencias externas para **add shapes to Word document**.

## Cómo agrupar formas en Word

El núcleo de la solución consiste en crear formas individuales, colocarlas en la página y luego envolverlas en un `GroupShape`. Los pasos siguientes reflejan el orden lógico del código.

### Paso 1: Crear un documento y un constructor

Un objeto `Document` representa todo el archivo DOCX. `DocumentBuilder` proporciona una API conveniente para editar el documento.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create an empty Word document
Document doc = new Document();

// DocumentBuilder lets you insert nodes, text, and shapes
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Por qué es importante*: El `Document` es el contenedor de todos los elementos de Word. El `DocumentBuilder` lleva un registro de la posición actual del cursor, lo cual es necesario cuando más adelante insertes la forma agrupada.

### Paso 2: Agregar la forma de rectángulo

Un rectángulo se crea especificando `ShapeType.Rectangle`. Ancho, alto y ubicación se establecen en puntos (1 pt ≈ 1/72 in).

```csharp
Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
rectangleShape.Width = 100;               // 100 pt wide
rectangleShape.Height = 50;               // 50 pt tall
rectangleShape.Left = 0;                  // X‑coordinate
rectangleShape.Top = 0;                   // Y‑coordinate
rectangleShape.StrokeColor = Color.Blue; // Outline color
```

*Por qué es importante*: Establecer `StrokeColor` hace que la forma sea visible cuando se abre el documento. También podrías rellenar la forma con `FillColor` si se requiere un interior sólido.

### Paso 3: Agregar la forma de elipse

La elipse usa `ShapeType.Ellipse`. Su tamaño y posición son independientes del rectángulo, lo que te permite controlar el diseño final del grupo.

```csharp
Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
ellipseShape.Width = 80;
ellipseShape.Height = 80;
ellipseShape.Left = 120;                  // Placed to the right of the rectangle
ellipseShape.Top = 0;
ellipseShape.StrokeColor = Color.Green;
```

*Por qué es importante*: Al posicionar la elipse en `Left = 120`, no se superpone al rectángulo, haciendo que el grupo sea visualmente distinto.

### Paso 4: Agrupar las dos formas

`GroupShape` actúa como un contenedor que trata a sus hijos como un solo objeto. Esta es la operación esencial para **how to group shapes in Word**.

```csharp
GroupShape groupShape = new GroupShape(doc);
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);
```

*Por qué es importante*: Agrupar te permite mover, cambiar el tamaño o rotar ambas formas juntas. Cualquier transformación aplicada a `groupShape` se propaga a sus hijos.

### Paso 5: Insertar la forma agrupada en el documento

`DocumentBuilder.InsertNode` coloca el `GroupShape` en la ubicación actual del cursor. Como no hemos movido el constructor, el grupo aparece al inicio de la primera página.

```csharp
builder.InsertNode(groupShape);
```

*Por qué es importante*: Insertar el nodo directamente evita la necesidad de un párrafo o celda de tabla separados. El grupo pasa a formar parte del flujo del documento.

### Paso 6: Guardar el documento

Finalmente, escribe el archivo DOCX en disco. Usa una ruta completa a la que tu aplicación pueda escribir.

```csharp
doc.Save(@"C:\Temp\GroupShape.docx");
```

*Por qué es importante*: `doc.Save` finaliza todos los cambios. El archivo resultante puede abrirse en Microsoft Word, LibreOffice o cualquier visor que admita DOCX.

## Archivo fuente completo

Copia el código a continuación en un nuevo proyecto de consola (`dotnet new console`) y ejecútalo. El programa crea un archivo llamado `GroupShape.docx` que contiene un rectángulo y una elipse agrupados.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordShapeGrouping
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new document and a builder to edit it
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Define a rectangle shape
            Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
            rectangleShape.Width = 100;
            rectangleShape.Height = 50;
            rectangleShape.Left = 0;
            rectangleShape.Top = 0;
            rectangleShape.StrokeColor = Color.Blue;

            // Step 3: Define an ellipse shape
            Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
            ellipseShape.Width = 80;
            ellipseShape.Height = 80;
            ellipseShape.Left = 120;
            ellipseShape.Top = 0;
            ellipseShape.StrokeColor = Color.Green;

            // Step 4: Group the two shapes together
            GroupShape groupShape = new GroupShape(doc);
            groupShape.AppendChild(rectangleShape);
            groupShape.AppendChild(ellipseShape);

            // Step 5: Insert the grouped shape into the document
            builder.InsertNode(groupShape);

            // Step 6: Save the document
            doc.Save(@"C:\Temp\GroupShape.docx");
        }
    }
}
```

### Resultado esperado

Abre `GroupShape.docx`. Verás un único objeto visual que contiene un rectángulo azul a la izquierda y una elipse verde a la derecha. Seleccionar el objeto en Word resalta ambas formas simultáneamente—prueba de que **how to group shapes in Word** tuvo éxito.

## Preguntas comunes y casos límite

* **¿Puedo agregar más de dos formas?**  
  Sí. Llama a `groupShape.AppendChild` para cada `Shape` adicional antes de insertar el grupo.

* **¿Qué pasa si necesito rotar el grupo?**  
  Establece `groupShape.RotationAngle = 45;` (ángulo en grados) después de crear el grupo.

* **¿Necesito llamar a `doc.UpdatePageLayout()`?**  
  No para este escenario. El diseño se actualiza automáticamente al guardar el documento.

* **¿Cómo afecta la licencia al código?**  
  Con una licencia válida de Aspose.Words (`License license = new License(); license.SetLicense("Aspose.Words.lic");`) el documento generado no contiene marca de agua de evaluación.

## Conclusión

Ahora sabes **how to group shapes in Word** y **add shapes to Word document** usando Aspose.Words for .NET. El tutorial cubrió la creación de un documento, la definición de formas individuales, su agrupación, inserción del grupo y guardado del archivo.  

A partir de aquí puedes experimentar con:

* Agregar cuadros de texto o imágenes al grupo  
* Cambiar colores de relleno, estilos de línea o efectos de sombra  
* Agrupar formas dentro de tablas o encabezados  

Estas extensiones te permiten crear plantillas Word sofisticadas de forma programática manteniendo el código limpio y mantenible. ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Crear forma de grupo en documento Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insertar formas en documentos Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Crear documento Word con Aspose.Words – Guía paso a paso](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}