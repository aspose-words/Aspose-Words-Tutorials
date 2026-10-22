---
category: general
date: 2026-08-10
description: Crear documento de Word programáticamente con Aspose.Words, luego agregar
  un botón de control ActiveX. Insertar botón de comando ActiveX en minutos.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- add activex control word
- insert activex command button
language: es
lastmod: 2026-08-10
og_description: Crea un documento de Word programáticamente usando Aspose.Words, luego
  agrega un botón de control ActiveX. Aprende a insertar rápidamente un botón de comando
  ActiveX.
og_image_alt: Screenshot of a Word document created programmatically with an ActiveX
  command button
og_title: Crear documento Word programáticamente – agregar un botón ActiveX en C#
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create word document programmatically with Aspose.Words, then add an
    ActiveX control word button. Insert activex command button in minutes.
  headline: Create word document programmatically and add ActiveX button
  type: TechArticle
- description: Create word document programmatically with Aspose.Words, then add an
    ActiveX control word button. Insert activex command button in minutes.
  name: Create word document programmatically and add ActiveX button
  steps:
  - name: Open `ActiveX_CommandButton.docx` in Microsoft Word.
    text: Open `ActiveX_CommandButton.docx` in Microsoft Word.
  - name: Enable the **Developer** tab if it isn’t visible (`File → Options → Customize
      Ribbon → check Developer`).
    text: Enable the **Developer** tab if it isn’t visible (`File → Options → Customize
      Ribbon → check Developer`).
  - name: Click **Design Mode**. The button should appear with the label “Submit”.
    text: Click **Design Mode**. The button should appear with the label “Submit”.
  - name: If you added an `OnAction` macro, click the button while Design Mode is
      off to trigger the macro.
    text: If you added an `OnAction` macro, click the button while Design Mode is
      off to trigger the macro.
  type: HowTo
tags:
- Aspose.Words
- ActiveX
- C#
title: Crear documento de Word programáticamente y agregar un botón ActiveX
url: /es/net/working-with-oleobjects-and-activex/create-word-document-programmatically-and-add-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear documento de Word programáticamente y agregar botón ActiveX

Si necesitas **crear documento de Word programáticamente**, esta guía te lleva a través de todo el proceso con Aspose.Words for .NET. También aprenderás cómo **agregar elementos de control activex en Word** y **insertar objetos de botón de comando activex** en un único ejemplo autónomo.

Generar archivos Word desde código elimina el paso manual de abrir Microsoft Word, permitiéndote crear informes, facturas o contratos basados en datos automáticamente. Al final de este tutorial tendrás una aplicación de consola C# lista para ejecutar que produce un archivo `.docx` que contiene un CommandButton ActiveX interactivo.

## Requisitos previos

* .NET 6.0 SDK o posterior (el código también funciona con .NET Framework 4.6+)
* Visual Studio 2022 o cualquier IDE que soporte desarrollo .NET
* Una licencia válida de Aspose.Words for .NET (puedes usar la clave de evaluación gratuita para pruebas)
* Familiaridad básica con la sintaxis de C# y el concepto de controles COM/ActiveX

> **Consejo profesional:** Si planeas distribuir el documento generado a usuarios que no tengan Word instalado, incrusta los archivos de tiempo de ejecución del control ActiveX junto al `.docx` o proporciona una plantilla habilitada para macros.

## Crear documento de Word programáticamente – configuración inicial

Primero, agrega el paquete NuGet Aspose.Words a tu proyecto:

```bash
dotnet add package Aspose.Words
```

Luego crea un nuevo proyecto de consola (si aún no tienes uno):

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
```

Abre el archivo `Program.cs` generado – reemplazaremos su contenido con la solución completa a continuación.

## Paso 1: Importar espacios de nombres y configurar la licencia

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // OPTIONAL: Apply your Aspose.Words license to remove evaluation watermarks.
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");
```

*Por qué es importante*: Importar `Aspose.Words.Drawing` te da acceso a `Forms2OleControl`, la clase que representa un control ActiveX dentro de un documento Word. Configurar una licencia al inicio evita advertencias en tiempo de ejecución en producción.

## Paso 2: Crear un documento en blanco y un DocumentBuilder

```csharp
            // Create a new empty Word document.
            Document doc = new Document();

            // DocumentBuilder provides a convenient API for inserting text, tables, and controls.
            DocumentBuilder builder = new DocumentBuilder(doc);
```

El objeto `Document` es la representación en memoria de un archivo `.docx`. `DocumentBuilder` funciona como un cursor que se desplaza por el documento para insertar elementos.

## Paso 3: Insertar un control ActiveX CommandButton

```csharp
            // Insert an ActiveX CommandButton.
            // Parameters: control type, width, height, left position, top position (all in points).
            Forms2OleControl commandBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, // ActiveX type
                100,   // Width in points
                50,    // Height in points
                150,   // Left offset from the page margin
                200);  // Top offset from the page margin
```

`InsertForms2OleControl` crea un objeto OLE que Word trata como un control ActiveX. El sistema de coordenadas usa puntos (1 punto = 1/72 de pulgada), lo que coincide con el motor de diseño de Word.

## Paso 4: Establecer el texto del botón y propiedades opcionales

```csharp
            // Set the text that appears on the button.
            commandBtn.Caption = "Submit";

            // Optional: assign a macro name that Word will call when the button is clicked.
            // commandBtn.OnAction = "MyMacroName";
```

Establecer la propiedad `Caption` es la forma más común de etiquetar el botón. Si necesitas que el botón ejecute una macro VBA, asigna el nombre de la macro a `OnAction`. Este tutorial se centra en la parte visual; la integración de macros se cubre en la sección “Próximos pasos”.

## Paso 5: Guardar el documento

```csharp
            // Define the output path – change this to a folder that exists on your machine.
            string outputPath = @"ActiveX_CommandButton.docx";

            // Save the document with the embedded ActiveX control.
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Al ejecutar el programa, verás un mensaje en la consola confirmando que `ActiveX_CommandButton.docx` se ha escrito en el disco.

### Código fuente completo (listo para copiar y pegar)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            Forms2OleControl commandBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton,
                100, 50, 150, 200);

            commandBtn.Caption = "Submit";
            // commandBtn.OnAction = "MyMacroName";

            string outputPath = @"ActiveX_CommandButton.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Ejecutar el fragmento produce un archivo Word que contiene un **botón de comando ActiveX** clicable. Abre el archivo en Microsoft Word, cambia a **Modo de diseño** (pestaña Developer → Design Mode), y verás el botón renderizado exactamente donde lo colocaste.

## Paso 6: Verificar el resultado

1. Abre `ActiveX_CommandButton.docx` en Microsoft Word.
2. Habilita la pestaña **Developer** si no está visible (`File → Options → Customize Ribbon → check Developer`).
3. Haz clic en **Design Mode**. El botón debería aparecer con la etiqueta “Submit”.
4. Si agregaste una macro `OnAction`, haz clic en el botón mientras el Modo de diseño está desactivado para ejecutar la macro.

Si el botón no se muestra, verifica que la configuración de seguridad de Word permita controles ActiveX (`File → Options → Trust Center → Trust Center Settings → ActiveX Settings`).

## Preguntas comunes y casos límite

| Pregunta | Respuesta |
|----------|-----------|
| **¿Puedo insertar otros tipos de ActiveX?** | Sí. El enum `Forms2OleControlType` incluye `CheckBox`, `OptionButton`, `ComboBox`, etc. Reemplaza `CommandButton` con el valor del enum deseado. |

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Crear forma de grupo en documento Word usando Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Crear documento Word con encabezado y pie de página usando Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Insertar imagen en línea en documento Word usando Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}