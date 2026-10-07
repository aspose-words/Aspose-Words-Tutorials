---
category: general
date: 2026-10-07
description: Aprende cómo insertar un botón de comando OLE en un documento de Word
  con Aspose.Words C#. Guía paso a paso que cubre DocumentBuilder, propiedades y cómo
  guardar el archivo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert OLE command button
- Aspose.Words OLE control
- C# DocumentBuilder InsertForms2OleControl
- OleControlType CommandButton
- Word OLE command button
language: es
lastmod: 2026-10-07
og_description: Inserte un botón de comando OLE en un documento de Word usando C#.
  Siga este tutorial conciso para añadir, configurar y guardar un CommandButton funcional
  con Aspose.Words.
og_image_alt: Insert OLE command button example in Word document
og_title: Insertar botón de comando OLE en Word con C# – guía completa de Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to insert OLE command button in a Word document with Aspose.Words
    C#. Step‑by‑step guide covering DocumentBuilder, properties, and saving the file.
  headline: How to insert OLE command button in a Word document using C#
  type: TechArticle
- description: Learn how to insert OLE command button in a Word document with Aspose.Words
    C#. Step‑by‑step guide covering DocumentBuilder, properties, and saving the file.
  name: How to insert OLE command button in a Word document using C#
  steps:
  - name: Why this works
    text: '* `DocumentBuilder` is the primary API for building Word documents programmatically.
      * `InsertForms2OleControl` tells Aspose.Words to embed a **Forms2 OLE control**,
      which is the legacy Word form technology that supports command buttons, check
      boxes, etc. * The `OleControlType.CommandButton` enum va'
  - name: 1. What if the button does not appear where I expect?
    text: '* Word uses points, not pixels. Convert screen pixels to points (`points
      = pixels * 72 / DPI`). * Ensure the rectangle does not intersect page margins;
      otherwise Word may shift the control.'
  - name: 2. Can I insert the button into an existing document?
    text: Yes. Load the document with `new Document("Existing.docx")` and use the
      same `DocumentBuilder` workflow. Just remember to move the builder’s cursor
      (`builder.MoveToDocumentEnd()`, `builder.MoveToBookmark("myBookmark")`, etc.)
      before calling `InsertForms2OleControl`.
  - name: 3. How do I attach a macro to the button?
    text: 'Aspose.Words does not create VBA code, but you can embed a macro after
      the document is generated:'
  - name: 4. Does this work with .NET Core on Linux?
    text: The OLE control is a Windows‑specific feature because it relies on COM.
      On Linux the button will be inserted, but it will appear as a static picture
      without interactive behavior. For cross‑platform interactive forms, consider
      using content controls (`StructuredDocumentTag`) instead.
  - name: 5. What if I need a different size or multiple buttons?
    text: Create additional `Rectangle` objects with unique coordinates and repeat
      the `InsertForms2OleControl` call. Each button can have its own `Caption` and
      `Name`.
  type: HowTo
tags:
- Aspose.Words
- C#
- OLE
- Word automation
title: Cómo insertar un botón de comando OLE en un documento de Word usando C#
url: /es/net/working-with-oleobjects-and-activex/how-to-insert-ole-command-button-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo insertar un botón de comando OLE en un documento Word usando C#

Si necesitas **insertar un botón de comando OLE** en un archivo Word de forma programática, esta guía te muestra exactamente cómo hacerlo con Aspose.Words para .NET. Ya sea que estés creando un informe con formularios o automatizando una plantilla que requiera interacción del usuario, los pasos a continuación te ofrecen una solución completa y ejecutable.

Aprenderás a crear un documento en blanco, usar `DocumentBuilder` para colocar un `Forms2OleControl`, establecer el texto y el nombre del botón, y finalmente guardar el `.docx`. No se requieren herramientas externas más allá de la biblioteca Aspose.Words.

## Requisitos previos

Antes de comenzar, asegúrate de contar con:

* .NET 6.0 o posterior (el código también funciona con .NET Framework 4.7+)
* Una licencia válida de Aspose.Words para .NET o una clave de evaluación gratuita
* Visual Studio 2022 (o cualquier IDE de C# que prefieras)
* Familiaridad básica con la sintaxis de C# y los conceptos OLE de Word

> **Consejo profesional:** Si utilizas la evaluación gratuita, el documento generado contendrá una pequeña marca de agua. Una versión con licencia la elimina automáticamente.

## Paso 1: Instalar Aspose.Words

Agrega el paquete Aspose.Words a tu proyecto mediante NuGet:

```bash
dotnet add package Aspose.Words
```

El paquete incluye los espacios de nombres `Aspose.Words.Drawing` y `Aspose.Words.Drawing.Ole` necesarios para los controles OLE.

## Paso 2: Insertar botón de comando OLE con DocumentBuilder

El núcleo del tutorial es el método `InsertForms2OleControl`. Crea un **Forms2 OLE CommandButton** en una ubicación y tamaño específicos.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
using System.Drawing;

// Create a new blank document and a DocumentBuilder to edit it
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Define the rectangle where the button will appear (x, y, width, height)
// Values are in points (1 point = 1/72 inch)
Rectangle buttonRect = new Rectangle(100, 100, 120, 30);

// Insert the Forms2 OLE CommandButton control
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,   // <-- OleControlType CommandButton (secondary keyword)
    buttonRect);

// Set the button's caption and name properties
commandButton.OleFormat.ObjectProps["Caption"] = "Click Me";
commandButton.OleFormat.ObjectProps["Name"] = "cmdSubmit";
```

### Por qué funciona

* `DocumentBuilder` es la API principal para crear documentos Word de forma programática.  
* `InsertForms2OleControl` indica a Aspose.Words que inserte un **control OLE Forms2**, que es la tecnología de formularios heredada de Word que admite botones de comando, casillas de verificación, etc.  
* El valor del enumerado `OleControlType.CommandButton` especifica que el control insertado es un **botón de comando**, el tipo exacto que solicitaste al querer **insertar un botón de comando OLE**.  
* El `Rectangle` determina la posición visual. Ajusta las coordenadas X/Y o el ancho/alto para que coincidan con tu diseño.

## Paso 3: Guardar el documento

Después de configurar el botón, escribe el documento en disco. Puedes elegir cualquier formato compatible con Aspose.Words (`.docx`, `.pdf`, `.odt`, …). Para este tutorial guardaremos como documento Word.

```csharp
// Choose a folder you have write access to
string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");

// Save the document containing the button
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Al abrir `CommandButton.docx` en Microsoft Word, verás un botón clicable con la etiqueta **Click Me**. Al pulsarlo en Word se abre el cuadro de diálogo predeterminado “Ejecutar macro”, porque el botón es un control de formulario OLE; más adelante puedes asociar una macro o código VBA si lo necesitas.

## Paso 4: Verificar el resultado (salida esperada)

Abre el archivo generado:

1. El botón aparece en las coordenadas que especificaste (aproximadamente 1,4 in desde la izquierda y la parte superior de la página).  
2. La etiqueta muestra **Click Me**.  
3. La propiedad `Name` (`cmdSubmit`) es visible en el panel **Desarrollador → Propiedades** de Word, lo cual es útil cuando necesitas referenciar el control desde VBA.

![Ejemplo de inserción de botón de comando OLE en documento Word](insert-ole-button.png)

*Texto alternativo de la imagen*: **Ejemplo de inserción de botón de comando OLE en documento Word** (incluye la palabra clave principal para accesibilidad y SEO).

## Casos límite y preguntas frecuentes

### 1. ¿Qué pasa si el botón no aparece donde lo espero?

* Word usa puntos, no píxeles. Convierte píxeles de pantalla a puntos (`points = pixels * 72 / DPI`).  
* Asegúrate de que el rectángulo no intersecte los márgenes de la página; de lo contrario Word puede desplazar el control.

### 2. ¿Puedo insertar el botón en un documento existente?

Sí. Carga el documento con `new Document("Existing.docx")` y usa el mismo flujo de trabajo con `DocumentBuilder`. Solo recuerda mover el cursor del builder (`builder.MoveToDocumentEnd()`, `builder.MoveToBookmark("myBookmark")`, etc.) antes de llamar a `InsertForms2OleControl`.

### 3. ¿Cómo asocio una macro al botón?

Aspose.Words no crea código VBA, pero puedes incrustar una macro después de generar el documento:

```csharp
// Load the generated document
Document doc = new Document(outputPath);

// Add a VBA macro module (requires Aspose.Words licensing)
doc.VbaProject.Modules.Add("Module1", "Sub cmdSubmit_Click()\n MsgBox \"Button clicked!\"\nEnd Sub");

// Save again
doc.Save(outputPath);
```

### 4. ¿Funciona esto con .NET Core en Linux?

El control OLE es una característica específica de Windows porque depende de COM. En Linux el botón se insertará, pero aparecerá como una imagen estática sin comportamiento interactivo. Para formularios interactivos multiplataforma, considera usar controles de contenido (`StructuredDocumentTag`) en su lugar.

### 5. ¿Qué pasa si necesito un tamaño diferente o varios botones?

Crea objetos `Rectangle` adicionales con coordenadas únicas y repite la llamada a `InsertForms2OleControl`. Cada botón puede tener su propio `Caption` y `Name`.

## Ejemplo completo funcionando

A continuación tienes el programa completo que puedes copiar y pegar en una aplicación de consola. Incluye todas las directivas `using` necesarias, manejo de errores y comentarios.

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

namespace OleCommandButtonDemo
{
    class Program
    {
        static void Main()
        {
            try
            {
                // 1️⃣ Create a new blank document
                Document document = new Document();
                DocumentBuilder builder = new DocumentBuilder(document);

                // 2️⃣ Define button rectangle (x, y, width, height) in points
                Rectangle buttonRect = new Rectangle(100, 100, 120, 30);

                // 3️⃣ Insert the Forms2 OLE CommandButton control
                Forms2OleControl commandButton = builder.InsertForms2OleControl(
                    OleControlType.CommandButton,
                    buttonRect);

                // 4️⃣ Set visual properties
                commandButton.OleFormat.ObjectProps["Caption"] = "Click Me";
                commandButton.OleFormat.ObjectProps["Name"] = "cmdSubmit";

                // 5️⃣ Save the document
                string outputPath = Path.Combine(
                    Environment.CurrentDirectory,
                    "CommandButton.docx");

                document.Save(outputPath);
                Console.WriteLine($"Document saved successfully: {outputPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"Error: {ex.Message}");
            }
        }
    }
}
```

Ejecuta el programa, abre el `CommandButton.docx` generado y verás el botón **Click Me** listo para personalizarse.

## Conclusión

Ahora sabes cómo **insertar un botón de comando OLE** en un documento Word usando C# y Aspose.Words. El tutorial cubrió:

* Instalación del paquete Aspose.Words  
* Uso de `DocumentBuilder.InsertForms2OleControl` con `OleControlType.CommandButton`  
* Configuración de propiedades del botón (`Caption`, `Name`)  
* Guardado y verificación del resultado  

A partir de aquí puedes explorar temas relacionados como **Aspose.Words OLE control** para casillas de verificación, cuadros combinados o incrustar hojas de cálculo Excel completas. También podrías experimentar con la automatización de **Word OLE command button** en plantillas más grandes, o reemplazar los controles OLE por **content controls** modernos para obtener mejor compatibilidad multiplataforma.

Si lo deseas, adapta los valores del rectángulo, agrega varios botones o adjunta macros VBA para satisfacer las necesidades de tu aplicación. ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Insert Ole Object In Word Document](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object/)
- [Insert Ole Object In Word Document As Icon](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object-as-icon/)
- [Insert Ole Object In Word With Ole Package](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object-with-ole-package/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}