---
category: general
date: 2026-10-20
description: Crear un documento Word programáticamente y agregar un botón de comando
  usando Aspose.Words. Aprende a insertar un control ActiveX y establecer el texto
  del botón.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- add command button
- add activex control
- insert activex button
- set button caption
language: es
lastmod: 2026-10-20
og_description: Crear documento de Word programáticamente e incrustar un botón de
  comando ActiveX. Este tutorial explica cómo insertar el control y establecer su
  título con Aspose.Words.
og_image_alt: Word file showing an ActiveX command button inserted by Aspose.Words
og_title: Crear documento de Word programáticamente – agregar botón ActiveX
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create Word document programmatically and add a command button using
    Aspose.Words. Learn to insert an ActiveX control and set button caption.
  headline: Create Word document programmatically with an ActiveX button
  type: TechArticle
- description: Create Word document programmatically and add a command button using
    Aspose.Words. Learn to insert an ActiveX control and set button caption.
  name: Create Word document programmatically with an ActiveX button
  steps:
  - name: 'Open a terminal or Visual Studio and create a new console project:'
    text: 'Open a terminal or Visual Studio and create a new console project:'
  - name: 'Add the Aspose.Words package:'
    text: 'Add the Aspose.Words package:'
  - name: '(Optional) If you have a license file, place it in the project root and
      add the following line at the start of `Program.cs` to avoid evaluation watermarks:'
    text: '(Optional) If you have a license file, place it in the project root and
      add the following line at the start of `Program.cs` to avoid evaluation watermarks:'
  - name: Open `ActiveXCommandButton.docx` in Microsoft Word.
    text: Open `ActiveXCommandButton.docx` in Microsoft Word.
  - name: Switch to **Design Mode** (Developer tab → **Design Mode**) to see the button’s
      borders.
    text: Switch to **Design Mode** (Developer tab → **Design Mode**) to see the button’s
      borders.
  - name: If the button does not appear, check that the **Developer** tab is enabled
      and that your Word version supports ActiveX controls.
    text: If the button does not appear, check that the **Developer** tab is enabled
      and that your Word version supports ActiveX controls.
  - name: For macro‑enabled files (`.docm`), ensure the macro name in `OnClick` matches
      a VBA routine; otherwise Word will display a security warning.
    text: For macro‑enabled files (`.docm`), ensure the macro name in `OnClick` matches
      a VBA routine; otherwise Word will display a security warning.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Crear documento de Word programáticamente con un botón ActiveX
url: /es/net/working-with-oleobjects-and-activex/create-word-document-programmatically-with-an-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear documento Word programáticamente con un botón ActiveX

Cree un documento Word programáticamente con Aspose.Words, luego agregue un botón de comando que los usuarios puedan pulsar. Esta guía le muestra cómo insertar un control ActiveX, configurar sus propiedades y guardar el resultado como un archivo **.docx**.

Verá un ejemplo completo y ejecutable que puede copiar en una aplicación de consola. Al final del tutorial podrá generar un archivo Word que contiene un botón de comando totalmente funcional, y comprenderá cómo **add command button**, **add activex control**, **insert activex button**, y **set button caption** sin salir de su código C#.

## Requisitos previos

* .NET 6.0 SDK o posterior instalado  
* Visual Studio 2022 (o cualquier IDE compatible con C#)  
* Un archivo de licencia de Aspose.Words para .NET (la prueba gratuita funciona para este ejemplo)  
* Familiaridad básica con C# y el sistema de proyectos .NET  

No se requieren paquetes NuGet adicionales más allá de **Aspose.Words** porque el soporte ActiveX está incorporado en la biblioteca.

## Paso 1: Configurar el proyecto y agregar Aspose.Words

1. Abra una terminal o Visual Studio y cree un nuevo proyecto de consola:

   ```bash
   dotnet new console -n WordActiveXDemo
   cd WordActiveXDemo
   ```

2. Agregue el paquete Aspose.Words:

   ```bash
   dotnet add package Aspose.Words
   ```

3. (Opcional) Si tiene un archivo de licencia, colóquelo en la raíz del proyecto y agregue la siguiente línea al inicio de `Program.cs` para evitar marcas de agua de evaluación:

   ```csharp
   Aspose.Words.License license = new Aspose.Words.License();
   license.SetLicense("Aspose.Words.lic");
   ```

## Paso 2: Crear documento Word programáticamente – inicializar el documento

La primera operación es **create Word document programmatically**. Haga esto instanciando un objeto `Document` y un `DocumentBuilder` que le permite editar el contenido del documento.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;   // Provides ActiveX control types
using System.Drawing;        // For Point and Size structs

// Initialize a new blank document
Document document = new Document();

// DocumentBuilder gives a cursor‑based API for inserting elements
DocumentBuilder builder = new DocumentBuilder(document);
```

El `Document` representa todo el archivo, mientras que el `DocumentBuilder` mantiene un cursor que puede mover a cualquier ubicación del documento. Esta separación mantiene la API limpia y le permite **add activex control** más adelante sin gestionar manualmente estructuras de bajo nivel.

## Paso 3: Agregar botón de comando – insertar un control ActiveX

Ahora **add command button** insertando un control ActiveX de tipo `OleControlType.CommandButton`. El método `InsertForms2OleControl` requiere el tipo de control, una ubicación (`Point`) y un tamaño (`Size`).

```csharp
// Define where the button will appear (X = 100 pt, Y = 150 pt)
Point buttonPosition = new Point(100, 150);

// Define the button dimensions (width = 120 pt, height = 30 pt)
Size buttonSize = new Size(120, 30);

// Insert the ActiveX command button at the current cursor location
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton, // control type
    buttonPosition,              // position
    buttonSize);                 // size
```

La llamada anterior **insert activex button** en el documento en las coordenadas exactas que especifique. Las coordenadas se miden en puntos (1 pt ≈ 1/72 in). Si necesita el botón en un párrafo específico, mueva primero el cursor del builder:

```csharp
builder.Writeln("Click the button below:");
builder.MoveToDocumentEnd(); // places the cursor after the paragraph
```

## Paso 4: Establecer el título del botón – personalizar el texto del botón de comando

Un botón sin etiqueta es confuso, por lo que **set button caption** a algo significativo. La propiedad `Caption` define el texto que se muestra en el botón, mientras que `Name` le da al control un identificador programático.

```csharp
// Give the button a unique name for later reference
commandButton.Name = "btnSubmit";

// Set the visible text on the button
commandButton.Caption = "Submit";

// Optional: assign a macro name that Word will call when the button is clicked
commandButton.OnClick = "SubmitForm()";
```

Si más adelante exporta el documento a un formato habilitado para macros (`.docm`), el valor `OnClick` debe coincidir con el nombre de una macro VBA. Para un `.docx` simple, la propiedad se almacena pero no se ejecuta, lo cual está bien para la mayoría de los escenarios de automatización.

## Paso 5: Guardar el documento que contiene el botón ActiveX

Después de configurar el control, puede **save the document**. Elija un directorio al que tenga permiso de escritura y use la extensión `.docx` para máxima compatibilidad.

```csharp
// Replace with your desired output folder
string outputPath = Path.Combine(Environment.CurrentDirectory, "ActiveXCommandButton.docx");

// Save the document to disk
document.Save(outputPath);
```

Al abrir el archivo generado en Microsoft Word, verá un botón etiquetado **Submit** en las coordenadas que especificó. Al hacer clic en el botón en el cliente de escritorio, se intentará ejecutar la macro `SubmitForm` (si existe).

## Paso 6: Verificar el resultado y solucionar problemas comunes

1. Abra `ActiveXCommandButton.docx` en Microsoft Word.  
2. Cambie a **Design Mode** (pestaña Developer → **Design Mode**) para ver los bordes del botón.  
3. Si el botón no aparece, verifique que la pestaña **Developer** esté habilitada y que su versión de Word admita controles ActiveX.  
4. Para archivos habilitados para macros (`.docm`), asegúrese de que el nombre de la macro en `OnClick` coincida con una rutina VBA; de lo contrario Word mostrará una advertencia de seguridad.

### Consejo profesional

Los controles ActiveX son solo para Windows. Si necesita interactividad multiplataforma, considere usar **Content Controls** (`RichTextContentControl`) en lugar de un botón ActiveX.

## Código fuente completo

A continuación se muestra el programa completo, listo para ejecutar. Cópialo en `Program.cs` y ejecuta `dotnet run`.



## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarle a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en sus propios proyectos.

- [Crear documento Word con botón ActiveX – Guía C#](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)
- [Agregar botón de comando a documento Word con Aspose.Words – Guía completa](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)
- [Crear botón en documento Word con Aspose.Words – Ejemplo de código completo](/words/english/net/working-with-oleobjects-and-activex/create-word-document-button-with-aspose-words-full-code-exam/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}