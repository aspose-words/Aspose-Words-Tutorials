---
category: general
date: 2026-08-14
description: Cómo agregar un botón ActiveX en un documento de Word usando Aspose.Words
  – aprende a crear un documento de Word vacío e insertar un botón ActiveX programáticamente.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex
- insert activex button
- create empty word document
- create word document aspose
language: es
lastmod: 2026-08-14
og_description: Cómo agregar un botón ActiveX en un documento Word con Aspose.Words.
  Este tutorial le muestra cómo crear un documento Word vacío, insertar un botón ActiveX
  y guardar el resultado.
og_image_alt: Screenshot of an ActiveX button inserted into a Word document using
  Aspose.Words
og_title: Cómo agregar un botón ActiveX en Word – Guía de Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to add ActiveX button in a Word document using Aspose.Words – learn
    to create an empty Word document and insert an ActiveX button programmatically.
  headline: How to add ActiveX button in a Word document with Aspose.Words
  type: TechArticle
- description: How to add ActiveX button in a Word document using Aspose.Words – learn
    to create an empty Word document and insert an ActiveX button programmatically.
  name: How to add ActiveX button in a Word document with Aspose.Words
  steps:
  - name: Does the button work in all Word versions?
    text: ActiveX controls are supported in the desktop version of Word on Windows.
      They are not rendered in Word Online, Word for macOS, or mobile clients. If
      you need cross‑platform interactivity, consider using content controls or HTML‑based
      solutions instead.
  - name: What if I need a different size or position?
    text: '`InsertForms2OleControl` places the control at the current builder cursor.
      To move it, adjust the cursor with `builder.MoveTo` before insertion, or modify
      the control’s `Left` and `Top` properties after creation:'
  - name: Can I add other ActiveX types?
    text: Yes. The `Forms2OleControlType` enumeration includes `CheckBox`, `OptionButton`,
      `ListBox`, and more. Replace `CommandButton` with the desired enum value and
      adjust properties accordingly.
  - name: Is a macro required for the button to do something?
    text: The button itself does nothing until you attach VBA code. In Word, press
      **Alt+F11** to open the VBA editor, locate `btnSubmit_Click`, and write the
      desired logic. The generated document will retain the VBA project if you enable
      the **SaveFormat.Doc** (legacy `.doc`) format, but `.docx` files cannot
  type: HowTo
tags:
- Aspose.Words
- ActiveX
- Word automation
- C#
title: Cómo agregar un botón ActiveX en un documento Word con Aspose.Words
url: /es/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo agregar un botón ActiveX en un documento Word con Aspose.Words

Si necesitas **cómo agregar controles ActiveX** a un archivo Word generado, esta guía te muestra los pasos exactos. Aprenderás a **insertar un botón ActiveX** programáticamente, comenzando desde un **crear documento Word vacío** y terminando con un archivo guardado que puede abrirse en Microsoft Word.

Agregar un botón que ejecute código VBA o desencadene una macro es un requisito común para generadores de informes automáticos, plantillas de formularios o contratos interactivos. Usar Aspose.Words para .NET te permite crear el documento sin lanzar Office, manteniendo el proceso rápido y amigable para servidores.

## Requisitos previos

Antes de comenzar, asegúrate de tener:

* SDK de .NET 6.0 (o posterior) instalado.
* Visual Studio 2022 o cualquier IDE compatible con C#.
* Paquete NuGet Aspose.Words for .NET (`Aspose.Words` versión 24.9 o más reciente).  
  Instálalo con:
  ```bash
  dotnet add package Aspose.Words
  ```
* Un entorno Windows si planeas probar el botón ActiveX, porque los controles ActiveX requieren la versión de Windows de Microsoft Word.

## Paso 1: Crear un documento Word vacío

La primera tarea es **crear un documento Word vacío** en memoria. Aspose.Words proporciona la clase `Document` para este propósito.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new, blank Word document.
Document doc = new Document();
```

`Document` representa todo el archivo .docx. En este punto el documento no contiene páginas, pero puedes comenzar a agregar contenido de inmediato.

## Paso 2: Inicializar un DocumentBuilder

`DocumentBuilder` es un asistente que te permite insertar texto, imágenes y otros objetos en el documento. Trabaja sobre la instancia `Document` que acabas de crear.

```csharp
// Initialise the builder with the blank document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

El builder mantiene una posición de cursor; cualquier cosa que insertes después de esta línea aparecerá al inicio de la primera página.

## Paso 3: Insertar un control ActiveX CommandButton

Aspose.Words expone el método `InsertForms2OleControl` para agregar controles de formulario heredados, incluidos los ActiveX. El método requiere el tipo de control y su tamaño en puntos.

```csharp
// Insert an ActiveX CommandButton (150x30 points).
Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton, 150, 30);
```

El objeto `Forms2OleControl` devuelto te permite configurar propiedades como el nombre y el título del control.

## Paso 4: Configurar las propiedades del botón

Establecer un `Name` significativo te permite referenciar el control desde código VBA más adelante. La `Caption` es el texto que el usuario ve en el botón.

```csharp
// Set the button’s programmatic name (used in VBA) and displayed caption.
cmdBtn.Name = "btnSubmit";
cmdBtn.Caption = "Submit";
```

> **Consejo profesional:** Mantén el nombre corto y alfanumérico; Word rechazará nombres que contengan espacios o caracteres especiales.

## Paso 5: Guardar el documento

Finalmente, escribe el documento en disco. Usa la extensión `.docx` para archivos Word modernos; el botón ActiveX funciona de la misma manera en archivos `.doc`, pero `.docx` es el formato preferido para proyectos nuevos.

```csharp
// Save the document containing the ActiveX button.
doc.Save(@"C:\Temp\ActiveXButton.docx");
```

Cuando abras `ActiveXButton.docx` en Microsoft Word, verás un botón **Submit** clicable. Si habilitas macros, puedes adjuntar código VBA a `btnSubmit_Click` y hacer que se ejecute cuando el usuario haga clic en el botón.

## Ejemplo completo y ejecutable

Unir todas las piezas te brinda un programa autónomo que puedes copiar, pegar y ejecutar.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create an empty Word document.
            Document doc = new Document();

            // Step 2: Initialise DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Insert an ActiveX CommandButton control.
            Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, 150, 30);

            // Step 4: Set button properties.
            cmdBtn.Name = "btnSubmit";
            cmdBtn.Caption = "Submit";

            // Step 5: Save the document.
            string outputPath = @"C:\Temp\ActiveXButton.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Salida esperada** – Después de ejecutar el programa, la consola muestra la ubicación de guardado, y al abrir el archivo generado en Word se muestra un botón etiquetado **Submit** posicionado en la parte superior de la primera página.

## Manejo de preguntas comunes y casos límite

### ¿El botón funciona en todas las versiones de Word?

Los controles ActiveX son compatibles con la versión de escritorio de Word en Windows. No se renderizan en Word Online, Word para macOS o clientes móviles. Si necesitas interactividad multiplataforma, considera usar controles de contenido o soluciones basadas en HTML.

### ¿Qué pasa si necesito un tamaño o posición diferentes?

`InsertForms2OleControl` coloca el control en la posición actual del cursor del builder. Para moverlo, ajusta el cursor con `builder.MoveTo` antes de la inserción, o modifica las propiedades `Left` y `Top` del control después de crearlo:

```csharp
cmdBtn.Left = 100;   // points from the left margin
cmdBtn.Top = 200;    // points from the top margin
```

### ¿Puedo agregar otros tipos de ActiveX?

Sí. La enumeración `Forms2OleControlType` incluye `CheckBox`, `OptionButton`, `ListBox` y más. Reemplaza `CommandButton` con el valor de enumeración deseado y ajusta las propiedades según corresponda.

### ¿Se requiere una macro para que el botón haga algo?

El botón por sí mismo no hace nada hasta que adjuntas código VBA. En Word, pulsa **Alt+F11** para abrir el editor VBA, localiza `btnSubmit_Click` y escribe la lógica deseada. El documento generado conservará el proyecto VBA si habilitas el formato **SaveFormat.Doc** (formato legado `.doc`), pero los archivos `.docx` no pueden almacenar macros VBA. Usa el formato `.doc` si necesitas VBA incrustado.

## Conclusión

Ahora sabes **cómo agregar controles ActiveX** a un archivo Word usando Aspose.Words. Siguiendo los pasos para **crear un documento Word vacío**, inicializar un `DocumentBuilder`, **insertar un botón ActiveX**, configurar sus propiedades y guardar el archivo, puedes generar plantillas Word interactivas directamente desde tu código .NET.

A continuación, explora temas relacionados como el manejo de eventos del **insert ActiveX button**, agregar **create word document aspose** para tablas o imágenes, y asegurar documentos habilitados para macros en despliegues empresariales. Experimenta con diferentes tipos de controles y opciones de diseño para adaptar la experiencia del usuario a las necesidades de tu aplicación.

¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create a Word Document with Table Using Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}