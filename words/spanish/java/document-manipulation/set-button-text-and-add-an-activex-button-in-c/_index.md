---
category: general
date: 2026-10-10
description: Establezca el texto del botón y añada un botón ActiveX en C# usando Aspose.Words.
  Aprenda cómo insertar un botón, crear un control de botón y personalizar la leyenda
  en un documento de Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button text
- how to insert button
- create button control
- add activex control
- add activex button
language: es
lastmod: 2026-10-10
og_description: Establezca el texto del botón y añada un botón ActiveX en C# con Aspose.Words.
  Siga esta guía paso a paso para insertar un botón, crear el control del botón y
  personalizar su leyenda.
og_image_alt: Screenshot of a Word document showing an ActiveX button with custom
  text
og_title: Establecer el texto del botón y agregar un botón ActiveX en C# – guía completa
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Set button text and add an ActiveX button in C# using Aspose.Words.
    Learn how to insert button, create button control, and customize the caption in
    a Word document.
  headline: Set button text and add an ActiveX button in C#
  type: TechArticle
tags:
- ActiveX
- C#
- Aspose.Words
- button control
- document automation
title: Establecer el texto del botón y agregar un botón ActiveX en C#
url: /es/java/document-manipulation/set-button-text-and-add-an-activex-button-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Establecer texto del botón y agregar un botón ActiveX en C#

Si necesitas **establecer texto del botón** en un botón ActiveX dentro de un documento Word, esta guía te muestra exactamente cómo hacerlo. Al final del tutorial podrás **insertar botón**, crear un **control de botón** y personalizar su leyenda con solo unas pocas líneas de código C#.

Trabajar con controles ActiveX es común cuando deseas formularios interactivos en Word—ya sea que estés creando una plantilla de contrato, una encuesta o una herramienta interna. El ejemplo utiliza Aspose.Words para .NET, una biblioteca que permite manipular archivos Word sin necesidad de tener Microsoft Office instalado.

## Prerrequisitos

Antes de comenzar, asegúrate de tener:

* SDK .NET 6.0 o posterior instalado  
* Visual Studio 2022 (o cualquier IDE que soporte C#)  
* Una licencia de Aspose.Words para .NET (la evaluación gratuita funciona para aprendizaje)  

También necesitas una referencia al paquete NuGet `Aspose.Words`:

```bash
dotnet add package Aspose.Words
```

## Cómo insertar un botón en un documento Word

El primer paso es crear un nuevo `Document` y un `DocumentBuilder`. El builder es el punto de entrada para agregar contenido, incluidos los controles ActiveX.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Por qué es importante:** `Document` representa todo el archivo .docx, mientras que `DocumentBuilder` proporciona métodos de alto nivel como `InsertParagraph` e `InsertFormField`. Comenzar con un documento limpio garantiza que el botón aparezca exactamente donde lo deseas.

## Crear control de botón con Forms2OleControl

Ahora creamos el control de botón real. `Forms2OleControl` es la clase que Aspose.Words usa para todos los objetos ActiveX, y el tipo `COMMANDBUTTON` se renderiza como un botón clicable en Word.

```csharp
        // Step 2: Insert a Forms2OleControl of type COMMANDBUTTON
        Forms2OleControl button = builder.InsertForms2OleControl(
            Forms2OleControlType.COMMANDBUTTON, // control type
            100,  // left position (points)
            50,   // top position (points)
            200,  // width (points)
            150); // height (points)
```

**Explicación:**  
* `InsertForms2OleControl` coloca el control en las coordenadas exactas que proporcionas.  
* El tamaño se define en puntos (1 punto = 1/72 de pulgada). Ajusta estos números para que encajen en tu diseño.

## Agregar control ActiveX y asignarle un nombre único

Cada objeto ActiveX debe tener un nombre distinto para que puedas referenciarlo más tarde (por ejemplo, al manejar eventos en VBA).

```csharp
        // Step 3: Assign a unique name to the control
        button.SetName("MyActiveXButton");
```

**Consejo:** Evita espacios o caracteres especiales en el nombre; Word trata el nombre como un identificador en su modelo interno de formularios.

## Establecer texto del botón (leyenda) en el botón ActiveX

Aquí es donde entra en juego la palabra clave principal **set button text**. La propiedad `Caption` define la etiqueta que los usuarios ven en el botón.

```csharp
        // Step 4: Set the text that appears on the button
        button.SetCaption("Click Me");
```

Puedes cambiar la leyenda en cualquier momento antes de guardar el documento. Si más adelante necesitas localizar la interfaz, simplemente llama a `SetCaption` nuevamente con una cadena diferente.

## Guardar el documento y verificar el resultado

Finalmente, escribe el documento en disco. Abrir el archivo en Microsoft Word mostrará el botón con la leyenda personalizada.

```csharp
        // Step 5: Save the document
        doc.Save("ActiveXButton.docx");
        System.Console.WriteLine("Document created with an ActiveX button.");
    }
}
```

**Salida esperada:** Cuando abras *ActiveXButton.docx* en Word, verás un botón posicionado en las coordenadas especificadas, etiquetado **Click Me**. Al hacer clic en el botón se activará el comportamiento predeterminado del botón de comando de Word (que puedes personalizar más tarde con VBA).

![Set button text example](https://example.com/activex-button.png){alt="Ejemplo de establecer texto del botón"}

## Agregar botón ActiveX y manejar eventos (opcional)

Si necesitas que el botón realice una acción personalizada, puedes agregar una macro VBA que responda al evento `Click`. La macro puede inyectarse programáticamente, pero eso está fuera del alcance de este tutorial. Lo importante es que el botón ya está presente y su leyenda está establecida—listo para cualquier manejo de eventos que elijas.

## Problemas comunes y cómo evitarlos

| Problema | Por qué ocurre | Solución |
|----------|----------------|----------|
| El botón aparece desalineado | Las coordenadas están en puntos, no en píxeles | Convertir valores de píxeles a puntos (`points = pixels * 72 / DPI`) |
| La leyenda no cambia después de guardar | `SetCaption` llamado después de `Save` | Siempre establecer la leyenda **antes** de llamar a `doc.Save` |
| El control no es visible en versiones antiguas de Word | Algunas versiones antiguas de Word no soportan completamente ActiveX | Probar en la versión objetivo de Word; considerar usar un `CheckBox` o `DropDownList` como alternativa |
| Advertencia de licencia en la salida | La licencia de evaluación expira | Aplicar una licencia válida de Aspose.Words mediante `License license = new License(); license.SetLicense("Aspose.Words.lic");` |

## Ejemplo completo y ejecutable

A continuación se muestra el programa completo que puedes copiar, pegar y ejecutar. Incluye todas las directivas `using` necesarias y demuestra todo el flujo de trabajo, desde la creación del documento hasta el guardado.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXButtonDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new document and builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert an ActiveX command button at a specific location
            Forms2OleControl button = builder.InsertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON,
                100,   // left (points)
                50,    // top (points)
                200,   // width (points)
                150);  // height (points)

            // Give the button a unique identifier
            button.SetName("MyActiveXButton");

            // Set the visible text on the button (set button text)
            button.SetCaption("Click Me");

            // Save the document
            const string outputPath = "ActiveXButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}. Open it in Word to see the button.");
        }
    }
}
```

Ejecuta el programa con `dotnet run`. Después de la ejecución, abre *ActiveXButton.docx* para confirmar que la leyenda del botón dice **Click Me**.

## Resumen de lo que aprendiste

* Aprendiste cómo **set button text** en un botón ActiveX usando Aspose.Words.  
* Viste los pasos exactos para **how to insert button**, **create button control**, y **add activex control** a un documento Word.  
* Ahora dispones de un fragmento de código reutilizable que puedes adaptar a cualquier proyecto de automatización de Word basado en formularios.

## Próximos pasos

* Explora otros valores de `Forms2OleControlType` como `CHECKBOX` o `LISTBOX` para crear formularios más complejos.  
* Combina el botón con una macro VBA para realizar cálculos o validaciones de datos.  
* Usa la API `FormField` de Aspose.Words para leer la entrada del usuario después de que el documento haya sido completado.

Siéntete libre de experimentar con el tamaño, la posición y la leyenda para que coincidan con los requisitos de tu diseño. Si encuentras algún problema, la documentación de Aspose.Words ofrece referencias detalladas para cada clase utilizada en este tutorial.

¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [Add Shadow to Shape in Word with Aspose.Words – Step‑by‑Step](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-word-with-aspose-words-step-by-step/)
- [Add Page Numbers to the Footer of a Word Document Using Aspose.Words for .NET](/words/english/net/working-with-headers-and-footers/add-page-numbers/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}