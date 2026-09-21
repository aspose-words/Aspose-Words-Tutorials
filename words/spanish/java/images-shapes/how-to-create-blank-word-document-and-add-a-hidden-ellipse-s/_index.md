---
category: general
date: 2026-09-21
description: Crear un documento de Word en blanco con una elipse oculta usando C#.
  Aprende cómo ocultar una forma en Word y generar una forma oculta programáticamente.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to create ellipse
- hide shape in word
- create hidden shape
language: es
lastmod: 2026-09-21
og_description: Crea un documento Word en blanco con una elipse oculta usando C#.
  Esta guía muestra cómo ocultar una forma en Word y crear formas ocultas programáticamente.
og_image_alt: Screenshot of a blank Word document that contains a hidden ellipse shape
  created with C#
og_title: Crear documento Word en blanco con una forma de elipse oculta en C#
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create blank Word document with a hidden ellipse using C#. Learn how
    to hide shape in Word and generate a hidden shape programmatically.
  headline: How to create blank Word document and add a hidden ellipse shape in C#
  type: TechArticle
- questions:
  - answer: The shape’s XML adds a few hundred bytes, which is negligible for most
      use cases. The file remains essentially the same size as a truly empty document.
    question: Does hiding a shape affect document size?
  - answer: Yes. Load the document, locate the shape (`doc.GetChildNodes(NodeType.Shape,
      true)`), and set `shape.Hidden = false`.
    question: Can I unhide the shape later programmatically?
  - answer: No. Hidden objects are excluded from the print layout, so the printed
      page stays blank.
    question: Will the hidden shape appear when printing?
  - answer: 'The `Hidden` property is part of the OOXML spec, so any Word processor
      that fully implements OOXML (Word, LibreOffice, Google Docs) will respect the
      hidden flag. --- ## Conclusion You now know how to **create blank Word document**,
      **how to create ellipse**, **hide shape in Word**, and **create hidd'
    question: Is this approach compatible with Office Open XML (OOXML) only?
  type: FAQPage
tags:
- Aspose.Words
- C#
- Word automation
title: Cómo crear un documento Word en blanco y agregar una forma de elipse oculta
  en C#
url: /es/java/images-shapes/how-to-create-blank-word-document-and-add-a-hidden-ellipse-s/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo crear un documento Word en blanco y añadir una forma elíptica oculta en C#

Si necesitas **crear un documento Word en blanco** que contenga un gráfico invisible, esta guía te muestra exactamente cómo hacerlo. Al final del tutorial tendrás un archivo .docx que parece vacío pero que realmente almacena una forma elíptica oculta en el diseño.

Usaremos Aspose.Words para .NET para construir el documento, insertar una elipse, ocultarla y guardar el archivo. Los pasos también cubren **cómo crear objetos elipse**, la manera correcta de **ocultar una forma en Word**, y cómo **crear código de forma oculta** que funciona con cualquier proyecto .NET.

## Requisitos previos

Antes de comenzar, asegúrate de tener:

* SDK de .NET 6.0 o posterior instalado  
* Visual Studio 2022 (o cualquier editor de C#)  
* Una licencia de Aspose.Words para .NET o una copia de evaluación gratuita  
* Familiaridad básica con la sintaxis de C#  

No se requieren paquetes NuGet adicionales más allá de `Aspose.Words`.

## Crear documento Word en blanco con Aspose.Words

El primer paso es generar un archivo Word vacío. Esto nos brinda un lienzo limpio donde luego podemos insertar gráficos ocultos.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document doc = new Document();

        // The document is currently empty – it contains no paragraphs or shapes.
        // This is the foundation for all further operations.
```

**Por qué empezamos con un documento en blanco** – Partir de un archivo vacío garantiza que ningún contenido no deseado interfiera con la forma oculta. Además, mantiene el tamaño del archivo al mínimo, lo cual es útil cuando el documento se usa posteriormente como plantilla.

## Cómo crear una elipse dentro del documento en blanco

A continuación necesitamos un `DocumentBuilder` para añadir contenido. El builder nos permite colocar formas exactamente donde queremos.

```csharp
        // Step 2: Initialize a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert an ellipse shape (width: 100 points, height: 50 points)
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

        // The ellipse now exists on the page, but it is visible by default.
```

**Explicación** – `ShapeType.Ellipse` indica a Aspose.Words que dibuje una figura circular‑ish. El ancho y la altura se miden en puntos (1 pt ≈ 1/72 pulgada). Puedes ajustar estos valores para adaptarlos a tus necesidades de diseño.

## Ocultar la forma en Word para que no aparezca en el diseño

Una forma que está oculta sigue existiendo en el XML del documento, lo que puede ser útil para metadatos, formato condicional o modificaciones programáticas posteriores. Para ocultarla, establecemos la propiedad `Hidden` a `true`.

```csharp
        // Step 4: Hide the shape so it does not appear in the layout
        ellipse.Hidden = true;

        // When Hidden = true, Word treats the shape as if it were not there.
        // The shape remains in the document’s DOM, allowing you to retrieve or modify it later.
```

**Por qué ocultar la forma** – Las formas ocultas son ignoradas por el motor de diseño, de modo que la página parece completamente en blanco. Sin embargo, los datos de la forma persisten, lo que puede ser útil para almacenar marcadores, marcadores de posición o XML personalizado que procesos posteriores puedan leer.

## Guardar el documento con la forma oculta

Finalmente escribimos el archivo en disco. El `.docx` guardado se abrirá en Microsoft Word sin contenido visible, pero la elipse oculta seguirá presente.

```csharp
        // Step 5: Save the document with the hidden shape
        doc.Save(@"C:\Temp\HiddenEllipse.docx");

        // The file now contains a hidden ellipse and appears empty when opened.
    }
}
```

**Verificación** – Abre el archivo generado en Word, luego presiona `Alt+F9` para alternar los códigos de campo y `Ctrl+A` → `Ctrl+Shift+F9` para ver objetos ocultos. Verás la elipse en el XML del documento (`word/document.xml`) pero nada en la página.

---

## Ejemplo completo y ejecutable

A continuación tienes el programa completo que puedes copiar‑pegar en un nuevo proyecto de consola. Incluye todas las directivas `using` y el método `Main` para que puedas ejecutarlo sin infraestructura adicional.

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
            // 1️⃣ Create a new blank Word document
            Document doc = new Document();

            // 2️⃣ Prepare a builder to insert content
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert an ellipse (100 pt × 50 pt)
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

            // 4️⃣ Hide the ellipse so the page stays empty
            ellipse.Hidden = true;

            // 5️⃣ Save the file
            string outPath = @"C:\Temp\HiddenEllipse.docx";
            doc.Save(outPath);

            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

**Salida esperada** – Cuando ejecutes el programa, la consola imprimirá la ruta del archivo, y el archivo Word resultante no contendrá objetos visibles. Si inspeccionas el documento con una herramienta de compresión (`.docx` es un archivo zip), encontrarás el elemento `<w:pict>` que describe la elipse dentro de `word/document.xml`.

---

## Variaciones comunes y casos límite

| Escenario | Qué cambiar | Por qué importa |
|----------|-------------|-----------------|
| **Forma diferente** | Reemplaza `ShapeType.Ellipse` por `ShapeType.Rectangle`, `ShapeType.Line`, etc. | Permite ocultar otros gráficos manteniendo el mismo flujo de trabajo. |
| **Múltiples formas ocultas** | Llama a `InsertShape` varias veces y establece `Hidden = true` en cada una. | Útil para incrustar una colección de marcadores o marcadores de posición. |
| **Visibilidad condicional** | Usa `shape.Visible = false` junto con `shape.Hidden = true` para mayor seguridad. | Algunas versiones antiguas de Word respetan `Visible` de forma distinta; establecer ambos cubre todos los casos. |
| **Guardar en un stream** | Reemplaza `doc.Save(path)` por `doc.Save(stream, SaveFormat.Docx)`. | Permite enviar el documento directamente por HTTP o almacenarlo en una base de datos. |
| **Aplicar un estilo** | Después de la inserción, modifica `ellipse.FillColor`, `ellipse.LineWeight`, etc. antes de ocultarla. | El estilo de la forma se conserva en el XML, lo que puede ser útil para revelar la forma más tarde. |

**Consejo profesional:** Siempre prueba la forma oculta en la versión de Word objetivo (p. ej., Word 2019, Word 365) porque a veces aparecen peculiaridades de renderizado cuando los objetos ocultos interactúan con diseños de página complejos.

---

## Preguntas frecuentes

**P: ¿Ocultar una forma afecta el tamaño del documento?**  
R: El XML de la forma añade unos pocos cientos de bytes, lo cual es insignificante para la mayoría de los casos. El archivo permanece esencialmente del mismo tamaño que un documento realmente vacío.

**P: ¿Puedo volver a mostrar la forma más adelante de forma programática?**  
R: Sí. Carga el documento, localiza la forma (`doc.GetChildNodes(NodeType.Shape, true)`) y establece `shape.Hidden = false`.

**P: ¿La forma oculta aparecerá al imprimir?**  
R: No. Los objetos ocultos se excluyen del diseño de impresión, por lo que la página impresa sigue en blanco.

**P: ¿Este enfoque es compatible solo con Office Open XML (OOXML)?**  
R: La propiedad `Hidden` forma parte de la especificación OOXML, por lo que cualquier procesador de Word que implemente completamente OOXML (Word, LibreOffice, Google Docs) respetará la bandera oculta.

---

## Conclusión

Ahora sabes cómo **crear un documento Word en blanco**, **crear una elipse**, **ocultar una forma en Word** y **crear una forma oculta** usando Aspose.Words para .NET. El tutorial cubrió todo el ciclo de vida: desde inicializar un archivo vacío hasta insertar, ocultar y guardar la forma, además de los pasos de verificación y variaciones comunes.

A continuación, podrías explorar:

* Añadir cuadros de texto ocultos para metadatos (técnica *hide shape in word* aplicada a texto)  
* Usar partes XML personalizadas para almacenar datos estructurados junto a formas ocultas  
* Convertir el documento con forma oculta a PDF manteniendo los elementos ocultos  

Experimenta con diferentes formas y configuraciones de visibilidad para ver cómo el contenido oculto puede servir como un almacén de datos ligero dentro de archivos Word.

¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Crear forma rectangular en Word usando C# – Guía paso a paso](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Crear forma de grupo en un documento Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Crear documento Word con un rectángulo sombreado – Guía paso a paso](/words/english/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}