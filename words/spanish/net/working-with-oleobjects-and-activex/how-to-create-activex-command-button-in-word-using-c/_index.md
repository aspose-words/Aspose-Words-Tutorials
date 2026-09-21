---
category: general
date: 2026-09-21
description: Aprende cómo crear un botón de comando ActiveX en un documento de Word
  con Aspose.Words y C#. Guía paso a paso que cubre la inserción, el posicionamiento
  y el guardado.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex command button
- aspose.words activex
- c# documentbuilder
- insertforms2olecontrol
- activeX control in word
- programmatically add button
language: es
lastmod: 2026-09-21
og_description: Crea un botón de comando ActiveX en un documento de Word usando C#
  y Aspose.Words. Sigue este tutorial completo para insertar, posicionar y guardar
  el botón programáticamente.
og_image_alt: Screenshot showing an ActiveX command button inserted in a Word document
  using C#
og_title: Crear un botón de comando ActiveX en Word con C# – guía completa
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create ActiveX command button in a Word document with
    Aspose.Words and C#. Step‑by‑step guide covers insertion, positioning, and saving.
  headline: How to create ActiveX command button in Word using C#
  type: TechArticle
tags:
- ActiveX
- C#
- Aspose.Words
- Word automation
- DocumentBuilder
title: Cómo crear un botón de comando ActiveX en Word usando C#
url: /es/net/working-with-oleobjects-and-activex/how-to-create-activex-command-button-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo crear un botón de comando ActiveX en Word usando C#

Si necesitas **crear un botón de comando ActiveX** dentro de un archivo Word, esta guía te muestra los pasos exactos. Usando Aspose.Words para .NET puedes agregar, posicionar y configurar el botón completamente desde código C#.

La inserción programática de un botón ActiveX elimina el trabajo manual de la interfaz y permite la generación automatizada de documentos para formularios, informes o plantillas interactivas. En este tutorial aprenderás a usar **DocumentBuilder**, el método **InsertForms2OleControl**, y propiedades relacionadas para lograr un botón completamente funcional.

## Lo que necesitarás

* SDK de .NET 6.0 o posterior (el código también funciona con .NET Framework 4.7+)
* Aspose.Words para .NET (paquete NuGet `Aspose.Words`)
* Un IDE como Visual Studio 2022 o VS Code
* Conocimientos básicos de C# y conceptos de documentos Word

No se requiere una instalación adicional de Office porque Aspose.Words funciona de forma independiente de Microsoft Word.

## Paso 1: Configurar el proyecto C#

Crea un nuevo proyecto de consola y agrega el paquete Aspose.Words.

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
dotnet add package Aspose.Words
```

La biblioteca `Aspose.Words` proporciona la clase **DocumentBuilder** que utilizaremos para manipular el documento.

## Paso 2: Inicializar el documento y el builder

El primer bloque de código crea un documento en blanco y una instancia de `DocumentBuilder`. Este objeto es el punto de entrada para todas las operaciones de procesamiento de Word.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

// Create a new blank document.
Document doc = new Document();

// Create a builder to edit the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Por qué es importante:** `DocumentBuilder` mantiene la posición actual del cursor, por lo que cualquier inserción posterior aparecerá exactamente donde coloques el cursor.

## Paso 3: Insertar el botón de comando ActiveX

El método **InsertForms2OleControl** crea un control ActiveX del tipo solicitado. Aquí solicitamos un `CommandButton` y especificamos su tamaño en puntos (200 × 30 pt).

```csharp
// Insert an ActiveX CommandButton control (200 × 30 pt).
Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
    OleControlType.CommandButton, 200, 30);
```

**Explicación:**  
* `OleControlType.CommandButton` indica a Aspose.Words que cree un botón en lugar de otro tipo de control.  
* El método devuelve un objeto `Forms2OleControl`, que expone campos de posición y propiedades.

## Paso 4: Posicionar el botón y establecer sus propiedades

Después de la inserción puedes mover el botón a cualquier ubicación de la página y asignarle un nombre programático y una leyenda visible.

```csharp
// Position the button (coordinates are in points).
cmdBtn.Left = 100;          // X‑coordinate
cmdBtn.Top = 150;           // Y‑coordinate

// Set the button's programmatic name and displayed text.
cmdBtn.Name = "btnSubmit";
cmdBtn.Caption = "Submit";
```

**Consejo profesional:** El sistema de coordenadas comienza en la esquina superior izquierda de la página. Ajusta `Left` y `Top` para alinear el botón con otros campos de formulario.

## Paso 5: Guardar el documento

Finalmente, escribe el documento en disco. El archivo contendrá el botón ActiveX, listo para abrirse en Microsoft Word donde el botón será interactivo.

```csharp
// Save the document that now contains the ActiveX button.
doc.Save("ActiveXCommandButton.docx");
```

Cuando abras `ActiveXCommandButton.docx` en Word, verás un botón etiquetado **Submit** en la ubicación especificada. Al hacer clic en él en Word se activará el comportamiento predeterminado del botón de comando (que puedes personalizar más tarde con VBA o complementos de Word).

## Ejemplo completo y ejecutable

Unir todas las piezas genera un programa autónomo que puedes copiar, pegar y ejecutar.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // 1. Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert an ActiveX CommandButton (200 × 30 pt).
        Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
            OleControlType.CommandButton, 200, 30);

        // 3. Position and configure the button.
        cmdBtn.Left = 100;          // X‑coordinate (points)
        cmdBtn.Top = 150;           // Y‑coordinate (points)
        cmdBtn.Name = "btnSubmit";
        cmdBtn.Caption = "Submit";

        // 4. Save the document.
        doc.Save("ActiveXCommandButton.docx");

        Console.WriteLine("Document created successfully.");
    }
}
```

**Salida esperada:** La consola imprime *“Document created successfully.”* y la carpeta ahora contiene `ActiveXCommandButton.docx`. Al abrir el archivo en Microsoft Word se muestra un botón **Submit** clicable posicionado a 100 pt del margen izquierdo y 150 pt de la parte superior de la página.

## Problemas comunes y cómo evitarlos

| Problema | Por qué ocurre | Solución |
|----------|----------------|----------|
| El botón aparece fuera de la página | Los valores `Left`/`Top` exceden las dimensiones de la página | Utiliza `doc.FirstSection.PageSetup.PageWidth` y `PageHeight` para calcular coordenadas seguras |
| El botón no es visible en Word | El documento se guardó en un formato que elimina los controles ActiveX (p.ej., `.txt`) | Siempre guarda como `.docx` o `.doc` |
| Error de tiempo de ejecución `ArgumentOutOfRangeException` | El ancho o la altura se establecen en cero o negativo | Asegúrate de que los argumentos de tamaño pasados a `InsertForms2OleControl` sean números positivos |

## Extender la solución

Puedes personalizar aún más el botón estableciendo propiedades adicionales como `Enabled`, `Visible`, o adjuntando una macro mediante VBA. La clase **Forms2OleControl** también te permite insertar otros controles ActiveX como casillas de verificación (`OleControlType.CheckBox`) o cuadros combinados (`OleControlType.ComboBox`).

Si necesitas generar varios botones en un bucle, encapsula la lógica de inserción en un método auxiliar:

```csharp
static Forms2OleControl AddCommandButton(DocumentBuilder builder,
    string name, string caption, double left, double top)
{
    var btn = builder.InsertForms2OleControl(OleControlType.CommandButton, 200, 30);
    btn.Name = name;
    btn.Caption = caption;
    btn.Left = left;
    btn.Top = top;
    return btn;
}
```

## Conclusión

Ahora sabes cómo **crear un botón de comando ActiveX** en un documento Word usando C# y Aspose.Words. El tutorial cubrió la configuración del proyecto, la inserción del botón con `InsertForms2OleControl`, su posicionamiento y el guardado del archivo final. Con esta base puedes automatizar formularios complejos, incrustar controles interactivos e integrar documentos Word en soluciones .NET más grandes.

A continuación, explora temas relacionados como los campos de formulario **Aspose.Words ActiveX**, el estilo avanzado de **C# DocumentBuilder**, o cómo agregar programáticamente **controles ActiveX en Word** para casillas de verificación y listas desplegables. Experimenta con diferentes coordenadas y tamaños para adaptarlos a tus requisitos de diseño específicos. ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Crear documento Word con Aspose.Words para .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Crear forma rectangular en Word con Aspose.Words – Guía paso a paso](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Crear un documento Word con tabla usando Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}