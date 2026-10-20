---
category: general
date: 2026-09-18
description: Crea un documento Word en blanco y oculta una forma elíptica usando Aspose.Words.
  Aprende cómo ocultar una forma en Word, cómo insertar una elipse y crear una forma
  oculta rápidamente.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to hide shape
- how to insert ellipse
- hide shape in word
- create hidden shape
language: es
lastmod: 2026-09-18
og_description: Crea un documento Word en blanco y oculta una forma elíptica en Word.
  Esta guía te muestra paso a paso cómo insertar una elipse, ocultar la forma en Word
  y crear una forma oculta con Aspose.Words.
og_image_alt: Screenshot of a blank Word document containing a hidden ellipse shape
  created with Aspose.Words
og_title: Crear un documento de Word en blanco con una forma de elipse oculta
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create a blank Word document and hide an ellipse shape using Aspose.Words.
    Learn how to hide shape in Word, how to insert ellipse, and create hidden shape
    quickly.
  headline: Create a blank Word document with a hidden ellipse shape
  type: TechArticle
- description: Create a blank Word document and hide an ellipse shape using Aspose.Words.
    Learn how to hide shape in Word, how to insert ellipse, and create hidden shape
    quickly.
  name: Create a blank Word document with a hidden ellipse shape
  steps:
  - name: Pro tip
    text: If you later need to make the shape visible again, simply set `ellipse.Hidden
      = false;` and save the document.
  - name: What if the shape still appears?
    text: '* Ensure you are using Aspose.Words 23.9 or later – older versions had
      a bug where `Hidden` was ignored for some shape types. * Verify that you are
      not applying any additional formatting (e.g., `WrapType`) that forces the shape
      to occupy layout space.'
  - name: Can I hide other shape types?
    text: Yes. The same `Hidden` property works for `ShapeType.Rectangle`, `ShapeType.Picture`,
      etc. Just replace `ShapeType.Ellipse` with the desired type.
  - name: How to list hidden shapes later?
    text: '```csharp foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
      { if (shape.Hidden) Console.WriteLine($"Hidden shape: {shape.ShapeType}"); }
      ```'
  - name: Next steps
    text: '* Explore **how to hide shape** conditionally based on document content.
      * Learn **how to unhide shape** when generating a final version of the document.
      * Combine hidden shapes with **custom document properties** to embed machine‑readable
      data.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Crear un documento de Word en blanco con una forma de elipse oculta
url: /es/java/images-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear un documento Word en blanco con una forma de elipse oculta

Si necesitas **crear un documento Word en blanco** que contenga una forma que no deseas que aparezca en el diseño, esta guía te muestra exactamente cómo hacerlo. Usando Aspose.Words for .NET puedes insertar programáticamente una elipse y luego ocultar la forma para que el documento permanezca visualmente vacío mientras sigue conteniendo los datos de la forma.

En este tutorial aprenderás:

* cómo **crear objetos de documento Word en blanco**,
* cómo **insertar una elipse** usando `DocumentBuilder`,
* cómo **ocultar la forma en Word** para que no afecte la página,
* cómo **crear objetos de forma oculta** para procesamiento posterior.

Los pasos funcionan con .NET 6+ y la última versión de Aspose.Words (23.9 al momento de escribir). No se requiere instalación adicional de Office.

## Requisitos previos

* Visual Studio 2022 (o cualquier IDE de C#)
* .NET 6 SDK o posterior
* Aspose.Words for .NET paquete NuGet  
  ```bash
  dotnet add package Aspose.Words
  ```
* Conocimientos básicos de C# y conceptos de documentos Word

## Paso 1: Crear un documento Word en blanco

Lo primero que debes hacer es instanciar un objeto `Document`. Este objeto representa un archivo `.docx` vacío y es la base para todas las operaciones posteriores.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document
Document doc = new Document();   // <-- creates a blank Word document in memory
```

Crear un **documento Word en blanco** te brinda un lienzo limpio – sin párrafos, sin secciones, solo la estructura subyacente del paquete. Este es el punto de partida ideal cuando solo necesitas una forma oculta y nada más.

## Paso 2: Inicializar un DocumentBuilder

`DocumentBuilder` proporciona una API conveniente para añadir contenido a un `Document`. Funciona como un cursor que se desplaza a través del documento.

```csharp
// Step 2: Initialise a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

El builder crea automáticamente una primera sección y párrafo predeterminados, por lo que puedes comenzar a insertar formas sin añadir secciones manualmente.

## Paso 3: Insertar una forma de elipse

Ahora **insertamos una elipse** usando el método `InsertShape`. El método recibe una enumeración `ShapeType`, el ancho y la altura (en puntos).

```csharp
// Step 3: Insert an ellipse shape with a width of 100 points and a height of 50 points
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
```

¿Por qué una elipse? Una elipse es una forma vectorial que puede ocultarse sin afectar el flujo de texto circundante. El ancho de 100 pt y la altura de 50 pt son arbitrarios; puedes ajustarlos según tus necesidades de procesamiento posterior.

## Paso 4: Ocultar la forma para que no aparezca en el diseño

Para **ocultar la forma en Word**, establece la propiedad `Hidden` del objeto `Shape` a `true`. Cuando el documento se abre en Microsoft Word, la forma será invisible y no ocupará espacio en el diseño.

```csharp
// Step 4: Hide the shape so it does not appear in the layout
ellipse.Hidden = true;   // <-- this hides the shape in Word
```

El indicador `Hidden` se almacena en el XML de la forma (`<w:hidden/>`). Word respeta este atributo durante el renderizado, por lo que el documento parece completamente en blanco aunque la forma exista.

### Consejo profesional

Si más adelante necesitas volver a hacer visible la forma, simplemente establece `ellipse.Hidden = false;` y guarda el documento.

## Paso 5: Guardar el documento con la forma oculta

Finalmente, persiste el documento en disco. El archivo será un `.docx` normal que cualquier procesador de Word podrá abrir.

```csharp
// Step 5: Save the document with the hidden shape
doc.Save(@"C:\Temp\HiddenEllipse.docx");
```

El archivo guardado, `HiddenEllipse.docx`, es un **crear documento Word en blanco** que contiene una elipse oculta. Al abrirlo en Microsoft Word se muestra una página vacía, pero la forma sigue presente en la estructura Open XML.

## Ejemplo completo en funcionamiento

A continuación se muestra el programa completo y autónomo que puedes copiar, pegar y ejecutar.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace HiddenShapeDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a blank Word document
            Document doc = new Document();

            // 2️⃣ Initialise DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert an ellipse shape (width: 100pt, height: 50pt)
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

            // 4️⃣ Hide the shape so it does not affect layout
            ellipse.Hidden = true;

            // 5️⃣ Save the result
            string outputPath = @"C:\Temp\HiddenEllipse.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Salida esperada**

* Aparece un archivo llamado `HiddenEllipse.docx` en `C:\Temp`.
* Al abrir el archivo en Microsoft Word se muestra una página completamente en blanco.
* Si inspeccionas el documento con el Open XML SDK o un visor de zip, encontrarás el elemento `<w:shape>` con `<w:hidden/>` dentro de la parte del documento.

## Preguntas comunes y casos límite

### ¿Qué pasa si la forma sigue apareciendo?

* Asegúrate de estar usando Aspose.Words 23.9 o posterior – versiones anteriores tenían un error donde `Hidden` se ignoraba para algunos tipos de forma.
* Verifica que no estés aplicando ningún formato adicional (p. ej., `WrapType`) que obligue a la forma a ocupar espacio en el diseño.

### ¿Puedo ocultar otros tipos de forma?

Sí. La misma propiedad `Hidden` funciona para `ShapeType.Rectangle`, `ShapeType.Picture`, etc. Simplemente reemplaza `ShapeType.Ellipse` por el tipo deseado.

### ¿Cómo listar las formas ocultas más tarde?

```csharp
foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
{
    if (shape.Hidden)
        Console.WriteLine($"Hidden shape: {shape.ShapeType}");
}
```

Este fragmento recorre todas las formas e imprime aquellas que están ocultas, lo que es útil para flujos de trabajo de **crear forma oculta** donde más adelante necesites procesarlas o mostrarlas.

## Conclusión

Ahora sabes cómo **crear un documento Word en blanco**, **insertar una elipse** y **ocultar la forma en Word** para producir una **crear forma oculta** que permanece invisible para el lector. Esta técnica es útil para almacenar metadatos, marcadores o XML personalizado dentro de un documento sin alterar su apariencia visual.

### Próximos pasos

* Explora **cómo ocultar la forma** de manera condicional según el contenido del documento.
* Aprende **cómo mostrar la forma** al generar una versión final del documento.
* Combina formas ocultas con **propiedades de documento personalizadas** para incrustar datos legibles por máquinas.

Siéntete libre de experimentar con diferentes tipos de forma, tamaños y lógica de estado oculto para adaptarlos a tu escenario de automatización. ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Crear documento Word en blanco con forma de rectángulo sombreada – Guía paso a paso](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Crear forma de rectángulo en Word con Aspose.Words – Guía paso a paso](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Crear forma de grupo en documento Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}