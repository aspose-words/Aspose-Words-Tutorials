---
category: general
date: 2026-09-05
description: Crear documento Word usando Aspose.Words C# y aprender cómo insertar
  un botón de comando ActiveX, establecer el tamaño del botón y agregar funcionalidad
  interactiva al botón.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- how to insert activex
- add command button
- add interactive button
- set button size
language: es
lastmod: 2026-09-05
og_description: Crear un documento de Word en C# e insertar un botón de comando ActiveX.
  Este tutorial muestra cómo establecer el tamaño del botón y agregar funciones interactivas
  al botón.
og_image_alt: Screenshot of a Word document that contains an ActiveX command button
  created with C#
og_title: Crear documento Word con botón de comando ActiveX en C# – guía paso a paso
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create Word document using Aspose.Words C# and learn how to insert
    ActiveX command button, set button size, and add interactive button functionality.
  headline: How to create Word document with an ActiveX command button in C#
  type: TechArticle
- description: Create Word document using Aspose.Words C# and learn how to insert
    ActiveX command button, set button size, and add interactive button functionality.
  name: How to create Word document with an ActiveX command button in C#
  steps:
  - name: '**Initialize a new document** and a `DocumentBuilder` to edit it.'
    text: '**Initialize a new document** and a `DocumentBuilder` to edit it.'
  - name: '**Insert an ActiveX command button** using `InsertForms2OleControl`.'
    text: '**Insert an ActiveX command button** using `InsertForms2OleControl`.'
  - name: '**Configure the button** – caption, size, and position.'
    text: '**Configure the button** – caption, size, and position.'
  - name: '**Save** the document to disk.'
    text: '**Save** the document to disk.'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
- UI controls
title: Cómo crear un documento de Word con un botón de comando ActiveX en C#
url: /es/net/working-with-oleobjects-and-activex/how-to-create-word-document-with-an-activex-command-button-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo crear un documento Word con un botón de comando ActiveX en C#

Si necesitas **crear un documento Word** de forma programática e incrustar un elemento UI clicable, esta guía te muestra exactamente cómo. Usando Aspose.Words para .NET puedes **crear un documento Word**, **añadir un botón de comando**, y controlar su apariencia —todo sin abrir Microsoft Word.

Aprenderás **cómo insertar controles ActiveX**, **establecer el tamaño del botón**, y hacer que el botón se comporte como un componente UI interactivo. No se requiere experiencia previa con COM o VBA; solo un entorno de desarrollo .NET y la biblioteca Aspose.Words.

## Lo que lograrás

Al final de este tutorial podrás:

* **Crear un documento Word** desde cero con C#.
* **Insertar un botón de comando ActiveX** (el clásico control “Click Me”).
* **Establecer el tamaño** y la posición del botón con precisión.
* Opcionalmente añadir lógica simple de **botón interactivo** (p. ej., un marcador de macro).
* Guardar el archivo como `.docx` que puede abrirse en Microsoft Word o cualquier visor compatible.

### Requisitos previos

| Requisito | Motivo |
|-----------|--------|
| .NET 6.0 o posterior | Proporciona el runtime para el código C#. |
| Aspose.Words para .NET (última versión) | Suministra las API `Document`, `DocumentBuilder` y `Forms2OleControl` usadas en el ejemplo. |
| Visual Studio 2022 (o cualquier IDE de C#) | Facilita compilar y ejecutar la muestra. |
| Conocimientos básicos de C# | Necesarios para entender el flujo del código. |

> **Consejo profesional:** Si estás usando una versión de prueba de Aspose.Words, asegúrate de establecer la licencia antes de ejecutar el código para evitar marcas de agua de evaluación.

## Cómo crear un documento Word – flujo de trabajo general

El proceso consta de cuatro pasos lógicos:

1. **Inicializar un nuevo documento** y un `DocumentBuilder` para editarlo.  
2. **Insertar un botón de comando ActiveX** usando `InsertForms2OleControl`.  
3. **Configurar el botón** – título, tamaño y posición.  
4. **Guardar** el documento en disco.

Cada paso se explica en su propia sección a continuación.

![Documento Word con un botón ActiveX](/images/activex-button.png "Captura de pantalla de un documento Word que contiene un botón de comando ActiveX creado con C#")

## Cómo insertar un botón de comando ActiveX

La parte **cómo insertar activex** comienza con el método `InsertForms2OleControl`. Este método crea un control basado en COM que Word trata como un objeto ActiveX.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

// 1️⃣ Create a blank document and a builder.
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 2️⃣ Insert an ActiveX CommandButton control.
//    Parameters: control type, width, height, left, top (all in points).
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,   // ActiveX type
    150,                           // Width (points)
    100,                           // Height (points)
    50,                            // Left offset from page margin
    50);                           // Top offset from page margin
```

**Por qué funciona:** `OleControlType.CommandButton` indica a Aspose.Words que cree el clásico botón estilo VB. El tamaño y la ubicación se expresan en puntos (1 punto = 1/72 de pulgada), lo que brinda un control preciso del diseño.

## Cómo añadir el botón de comando y establecer el tamaño del botón

Después de insertar el control puedes ajustar sus propiedades visuales. El paso **añadir botón de comando** también cubre **establecer el tamaño del botón**.

```csharp
// 3️⃣ Set the button's caption – the text the user sees.
commandButton.Caption = "Click Me";

// 4️⃣ Optionally change size after insertion (if you need dynamic sizing).
//    Width and height are mutable properties.
commandButton.Width = 200;   // New width in points
commandButton.Height = 80;   // New height in points

// 5️⃣ Move the button if you need a different position.
commandButton.Left = 100;    // New left offset
commandButton.Top = 120;     // New top offset
```

**Explicación:**  

* `Caption` es la etiqueta que se muestra en el botón.  
* `Width` y `Height` te permiten **establecer el tamaño del botón** después de la inserción inicial —útil cuando el tamaño depende de datos en tiempo de ejecución.  
* `Left` y `Top` reposicionan el control sin recrear el documento.

> **Error común:** Olvidar usar puntos en lugar de píxeles hará que el botón aparezca demasiado pequeño o demasiado grande. Siempre convierte los valores de píxeles (`px * 72 / DPI`) si partes de medidas de pantalla.

## Cómo añadir un botón interactivo (opcional)

Un botón ActiveX puede ejecutar una macro al hacer clic, pero incrustar código VBA desde C# está fuera del alcance de un flujo puro de Aspose.Words. En su lugar, puedes añadir una propiedad de marcador que Word reconocerá como nombre de macro.

```csharp
// 6️⃣ Assign a macro name (the macro must exist in the Word template).
commandButton.OleFormat.Object = "MyMacroName";
```

Cuando el usuario abre el `.docx` generado en Word, al hacer clic en el botón se intentará ejecutar `MyMacroName`. Si la macro no existe, Word pedirá al usuario crearla.

**Por qué podrías usar esto:** Para formularios corporativos donde una macro completa campos, el código C# solo necesita colocar el botón; la lógica de la macro vive en el proyecto VBA del documento.

## Guardar el documento y verificar el resultado

```csharp
// 7️⃣ Save the document to the desired folder.
string outputPath = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.Desktop), "CommandButton.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

**Salida esperada:** Al abrir `CommandButton.docx` en Microsoft Word se muestra un botón con la etiqueta **Click Me** posicionado a 100 pts del margen izquierdo y 120 pts del superior. Las dimensiones del botón son **200 pts × 80 pts**. Al hacer clic se dispara el marcador de macro (si está presente).

## Ejemplo completo y funcional

A continuación tienes el programa completo, ejecutable, que reúne todo. Cópialo en un nuevo proyecto de Console App, añade el paquete NuGet de Aspose.Words y ejecútalo.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control.
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton, // ActiveX type
            150,                         // Initial width
            100,                         // Initial height
            50,                          // Left offset
            50);                         // Top offset

        // Set button caption and resize.
        commandButton.Caption = "Click Me";
        commandButton.Width = 200;   // Set button size (width)
        commandButton.Height = 80;   // Set button size (height)
        commandButton.Left = 100;    // Re‑position horizontally
        commandButton.Top = 120;     // Re‑position vertically

        // Optional: link to a macro named MyMacroName.
        commandButton.OleFormat.Object = "MyMacroName";

        // Save the document.
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Ejecuta el programa y luego abre el archivo generado. Verás el **botón interactivo** listo para personalizaciones adicionales.

## Preguntas frecuentes

| Pregunta | Respuesta |
|----------|-----------|
| **¿Esto funciona con .NET Core?** | Sí. Aspose.Words soporta .NET Standard, por lo que el mismo código se ejecuta en .NET 5/6/7. |
| **¿Puedo usar otros controles ActiveX (p. ej., CheckBox)?** | Por supuesto. Sustituye `OleControlType.CommandButton` por `OleControlType.CheckBox`, `OleControlType.OptionButton`, etc. |
| **¿Qué pasa si necesito un botón más grande en una página apaisada?** | Ajusta las propiedades `Width`, `Height`, `Left` y `Top` proporcionalmente. Recuerda que los puntos permanecen iguales sin importar la orientación de la página. |
| **¿Se requiere una macro para que el botón sea clicable?** | No. El botón funciona como elemento UI; una macro solo añade comportamiento personalizado al hacer clic. |

## Conclusión

Ahora sabes cómo **crear un documento Word** con Aspose.Words, **añadir un botón de comando**, **establecer el tamaño del botón**, y opcionalmente vincular el botón a una macro para obtener comportamiento de **botón interactivo**. Este enfoque te permite automatizar la creación de formularios, generar informes dinámicos o construir prototipos UI basados en Word directamente desde C#.

A continuación, podrías explorar:

* **Cómo insertar casillas de verificación ActiveX** para formularios de encuesta.  
* **Cómo añadir contenido de texto enriquecido** alrededor del botón usando `DocumentBuilder`.  
* **Cómo proteger el documento** manteniendo funcional el botón.  

¡Experimenta con diferentes tipos de controles, tamaños y nombres de macro para adaptarlos a tu escenario específico. Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Create a Word Document with Table Using Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}