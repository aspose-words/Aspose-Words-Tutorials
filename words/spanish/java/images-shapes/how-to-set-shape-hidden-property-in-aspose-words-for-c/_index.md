---
category: general
date: 2026-08-20
description: Aprenda cómo establecer la propiedad oculta de una forma en Aspose.Words
  para C#. Esta guía muestra cómo insertar una imagen y ocultar la forma para que
  nunca aparezca en la interfaz de usuario ni en la salida de impresión.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set shape hidden property
- insert image into document
- hide shape in Aspose.Words
- C# shape hidden property
- Aspose.Words DocumentBuilder
- prevent shape from printing
language: es
lastmod: 2026-08-20
og_description: Establecer la propiedad oculta de la forma en Aspose.Words con C#.
  Insertar una imagen, ocultar la forma y asegurarse de que nunca se muestre en la
  interfaz de usuario ni en la salida de impresión.
og_image_alt: Diagram illustrating set shape hidden property on a Word document shape
og_title: Establecer la propiedad oculta de la forma en Aspose.Words – guía completa
  de C#
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to set shape hidden property in Aspose.Words for C#. This
    guide shows inserting an image and hiding the shape so it never appears in the
    UI or print output.
  headline: How to set shape hidden property in Aspose.Words for C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document Automation
- Shape Handling
title: Cómo establecer la propiedad oculta de la forma en Aspose.Words para C#
url: /es/java/images-shapes/how-to-set-shape-hidden-property-in-aspose-words-for-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo establecer la propiedad oculta de una forma en Aspose.Words para C#

Si necesitas **establecer la propiedad oculta de una forma** en un documento Word, este tutorial te muestra los pasos exactos usando Aspose.Words para .NET. Ya sea que estés construyendo un motor de plantillas, generando informes o incrustando un logotipo que debe permanecer invisible, aprenderás a insertar una imagen y ocultar la forma para que nunca aparezca en la UI ni en la salida de impresión.

En esta guía también cubrimos **insertar imagen en el documento**, explicamos por qué ocultar una forma es importante para la impresión y recorremos el código completo y ejecutable. No se requieren referencias externas—solo copia, pega y ejecuta.

## Requisitos previos

Antes de comenzar, asegúrate de tener:

* .NET 6.0 o posterior (la última versión de Aspose.Words está dirigida a .NET 6+)
* Una licencia válida de Aspose.Words para .NET (o usa el modo de evaluación gratuito)
* Visual Studio 2022 o cualquier IDE de C# que prefieras
* Un archivo de imagen (p. ej., `logo.png`) colocado en una carpeta a la que puedas hacer referencia desde el código

## Paso 1: Crear un nuevo Document y DocumentBuilder

La clase `DocumentBuilder` es el punto de entrada para crear contenido Word de forma programática. Permite insertar párrafos, tablas y formas como imágenes.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Initialize a new blank document
        Document doc = new Document();
        // DocumentBuilder provides methods to add content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*¿Por qué este paso?*  
Crear un `Document` te brinda una representación en memoria de un archivo .docx, mientras que el `DocumentBuilder` suministra la API fluida que inserta objetos. Sin estos objetos no puedes colocar una forma en el documento.

## Paso 2: Insertar la imagen como una forma

Aspose.Words trata cada imagen como un `Shape`. El método `InsertImage` devuelve esa instancia de `Shape`, que luego puedes manipular.

```csharp
        // Step 2: Insert an image into the document
        // The returned Shape object lets us modify properties like size, rotation, and visibility.
        Shape picture = builder.InsertImage(@"YOUR_DIRECTORY\logo.png");
```

*¿Por qué este paso?*  
Usar `InsertImage` no solo agrega la imagen al flujo de texto, sino que también te da una referencia (`picture`) que puedes configurar. Esto es esencial para la **propiedad oculta de la forma en C#** que estableceremos a continuación.

## Paso 3: Establecer la propiedad oculta de la forma

La propiedad `Hidden` controla si la forma participa en la UI y la impresión. Establecerla en `true` hace que la forma sea invisible en la UI de Word y garantiza que no se imprimirá.

```csharp
        // Step 3: Hide the inserted shape so it won't appear in the UI or print output
        picture.Hidden = true;
```

*¿Por qué este paso?*  
Cuando una forma está marcada como oculta, Word la trata como un comentario—presente en la estructura del documento pero nunca renderizada. Este es el núcleo de **establecer la propiedad oculta de una forma**.

## Paso 4: Guardar el documento

Finalmente, escribe el documento en disco. Puedes elegir cualquier formato compatible con Aspose.Words (`.docx`, `.pdf`, `.html`, etc.).

```csharp
        // Step 4: Save the document to a .docx file
        doc.Save(@"OUTPUT\HiddenImageDocument.docx");
        // Optional: Save as PDF to verify the shape really stays hidden when printed
        doc.Save(@"OUTPUT\HiddenImageDocument.pdf");
    }
}
```

*¿Por qué este paso?*  
Guardar finaliza los cambios en memoria. Abrir el `.docx` resultante en Microsoft Word no muestra ninguna imagen visible, y la exportación a PDF confirma que la forma nunca aparece en la salida de impresión.

## Ejemplo completo y ejecutable

Juntando todo, aquí tienes el programa completo que puedes compilar y ejecutar:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeHiddenDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Initialize a blank document and a builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert an image as a shape
            // Replace YOUR_DIRECTORY with the actual folder that contains logo.png
            Shape picture = builder.InsertImage(@"YOUR_DIRECTORY\logo.png");

            // 3️⃣ Set the shape hidden property
            picture.Hidden = true; // This hides the shape in UI and when printing

            // 4️⃣ Save the document in both DOCX and PDF formats
            doc.Save(@"OUTPUT\HiddenImageDocument.docx");
            doc.Save(@"OUTPUT\HiddenImageDocument.pdf");

            Console.WriteLine("Document created successfully. The image is hidden.");
        }
    }
}
```

**Salida esperada**

* Al abrir `HiddenImageDocument.docx` en Microsoft Word no se muestra ninguna imagen visible.  
* Exportar o imprimir el documento (o abrir el PDF) tampoco muestra la imagen.  
* La forma oculta sigue existiendo en el XML del documento, lo que puedes verificar abriendo el `.docx` como un zip y examinando `word/document.xml`—verás un elemento `<w:pict>` con `w:hidden="true"`.

## Variaciones comunes y casos límite

| Situación | Qué hacer | Por qué es importante |
|-----------|-----------|-----------------------|
| **Falta el archivo de imagen** | Envuelve `InsertImage` en un `try/catch` y maneja `FileNotFoundException`. | Evita que la aplicación se bloquee y permite registrar un error claro. |
| **Múltiples formas ocultas** | Llama `picture.Hidden = true` para cada `Shape` que insertes, o itera sobre `doc.GetChildNodes(NodeType.Shape, true)`. | Garantiza que cada elemento visual no deseado permanezca invisible. |
| **Necesitar la forma visible solo en modo edición** | Establece `picture.Hidden = false` después de editar, y vuelve a cambiarlo antes de guardar. | Permite trabajar con la forma en la UI mientras el resultado final queda limpio. |
| **Impresión en versiones antiguas de Word** | Verifica el documento con Word 2010 o posterior; la bandera oculta es compatible con todas las versiones modernas. | Asegura la compatibilidad en toda tu base de usuarios. |
| **Usar un formato de archivo diferente (p. ej., PDF directamente)** | La bandera `Hidden` funciona igual; Aspose.Words la respeta durante la conversión a PDF. | Confirma que **evitar que la forma se imprima** funciona para todos los destinos de exportación. |

## Consejo profesional: Verificar la bandera oculta programáticamente

Si necesitas confirmar que una forma está oculta antes de guardar, puedes inspeccionar la propiedad:

```csharp
bool isHidden = picture.Hidden;
Console.WriteLine($"Shape hidden? {isHidden}");
```

Esta simple comprobación es útil en pipelines automatizados donde debes garantizar el cumplimiento de políticas de generación de documentos.

## Conclusión

Ahora sabes cómo **establecer la propiedad oculta de una forma** en Aspose.Words para C#. Insertando una imagen, aplicando `picture.Hidden = true` y guardando el documento, la forma queda fuera de la UI y nunca aparece en la salida impresa. Esta técnica es esencial cuando necesitas marcadores de posición, marcas de agua o elementos de branding que deben permanecer invisibles para los usuarios finales.

### ¿Qué sigue?

* Explora otras propiedades de forma como `picture.WrapType`, `picture.Rotation` y `picture.RelativeHorizontalPosition`.  
* Aprende a **ocultar una forma en Aspose.Words** de forma condicional según la entrada del usuario o la configuración.  
* Combina formas ocultas con bucles de **insertar imagen en el documento** para generar marcadores invisibles dinámicos para procesamiento posterior (p. ej., campos de combinación de correspondencia).

Siéntete libre de experimentar con diferentes formatos de imagen, diseños de documento y destinos de exportación. Ocultar formas te brinda un control granular sobre lo que tus lectores realmente ven—y lo que permanece detrás de escena. ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}