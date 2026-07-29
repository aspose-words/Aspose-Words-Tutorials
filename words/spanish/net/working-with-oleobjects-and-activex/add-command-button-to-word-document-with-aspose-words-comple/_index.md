---
category: general
date: 2026-07-29
description: Agregar un botón de comando a un documento de Word usando Aspose.Words.
  Aprende cómo establecer las propiedades del control ActiveX y definir el texto del
  botón de comando en unos pocos pasos sencillos.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add command button to word document
- set activex control properties
- set command button caption
- Aspose.Words ActiveX example
- C# insert ActiveX control
language: es
lastmod: 2026-07-29
og_description: Agregar botón de comando a un documento de Word con Aspose.Words.
  Este tutorial muestra cómo establecer las propiedades del control ActiveX y configurar
  rápidamente el texto del botón de comando.
og_image_alt: Screenshot of a Word document with a Submit command button inserted
  via C#
og_title: Añadir botón de comando al documento Word – Aspose.Words paso a paso
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Add command button to word document using Aspose.Words. Learn how to
    set activex control properties and set command button caption in a few easy steps.
  headline: Add Command Button to Word Document with Aspose.Words – Complete Guide
  type: TechArticle
- description: Add command button to word document using Aspose.Words. Learn how to
    set activex control properties and set command button caption in a few easy steps.
  name: Add Command Button to Word Document with Aspose.Words – Complete Guide
  steps:
  - name: Setting the Caption
    text: 'The caption is the text that appears on the button itself. To **set command
      button caption**, simply assign a string to the `Caption` property:'
  - name: Naming the Control
    text: 'Giving the control a meaningful name makes it easier to reference later
      (for example, when automating Word macros). We’ll set the `Name` property:'
  - name: Positioning on the Page
    text: 'Word uses points (1/72 of an inch) for layout. Adjust the `Left` and `Top`
      properties to place the button where you need it:'
  - name: Expected Result
    text: 1. The Word document opens with a single page. 2. A rectangular button labeled
      **Submit** appears at the coordinates you specified. 3. If you right‑click the
      button and choose **Properties**, you’ll see the name `btnSubmit` and other
      properties you set.
  - name: Inserting Other ActiveX Types
    text: 'The `InsertForms2OleControl` method isn’t limited to command buttons. You
      can embed check boxes, option buttons, or even custom ActiveX objects:'
  - name: Handling Word Versions
    text: Older Word versions (pre‑2007) use the binary `.doc` format, which stores
      ActiveX controls differently. Aspose.Words automatically converts the control
      when you save as `.doc`, but some properties (like precise positioning) may
      shift. If you target legacy formats, test the output in the specific Wor
  - name: Security Settings
    text: 'Word may disable ActiveX controls on machines with strict macro security.
      To avoid a “Security Warning” dialog, consider:'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Agregar botón de comando a un documento Word con Aspose.Words – Guía completa
url: /es/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Agregar Botón de Comando a Documento Word – Guía Completa de Programación

¿Alguna vez necesitaste **add command button to word document** pero no estabas seguro de qué llamadas API usar? No estás solo; muchos desarrolladores se topan con ese obstáculo cuando intentan incrustar controles interactivos en un archivo DOCX. La buena noticia es que Aspose.Words lo hace sorprendentemente sencillo. En esta guía recorreremos la creación de un control ActiveX CommandButton, **set activex control properties**, y **set command button caption**—todo con código C# limpio que puedes copiar‑pegar ahora mismo.

Al final de este tutorial tendrás un archivo Word totalmente funcional que contiene un botón “Submit” clicable, listo para abrirse en Microsoft Word. Sin scripts VBA externos, sin manipulación manual de la UI—solo control programático puro.

## Lo Que Aprenderás

* Cómo crear un documento Word en blanco y un `DocumentBuilder`.
* La llamada exacta al método para **add command button to word document** usando Aspose.Words.
* Formas de **set activex control properties** como tamaño, posición y nombre.
* La técnica adecuada para **set command button caption** para que el botón muestre exactamente lo que deseas.
* Consejos para manejar casos límite como diferentes tipos de botones, escalado DPI y compatibilidad de versiones de Word.

> **Prerequisite:** Visual Studio (o cualquier IDE de C#) con Aspose.Words para .NET instalado (paquete NuGet `Aspose.Words`). No se requiere experiencia previa en ActiveX.

---

## Paso 1: Configurar el Proyecto e Importar Espacios de Nombres

Antes de que podamos **add command button to word document**, necesitamos un proyecto C# que haga referencia a Aspose.Words. Crea una nueva aplicación de consola .NET y luego agrega el paquete NuGet:

```bash
dotnet add package Aspose.Words
```

Ahora trae los espacios de nombres requeridos a tu archivo fuente:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.ActiveX;
```

Estas tres directivas `using` te dan acceso a las clases `Document`, `DocumentBuilder` y `Forms2OleControl` que impulsan la inserción de ActiveX.

*Pro tip:* Si estás usando Visual Studio, el IDE sugerirá agregar estas automáticamente cuando escribas los nombres de clase.

---

## Paso 2: Crear un Documento en Blanco y un Builder

Un nuevo objeto `Document` representa un archivo Word vacío. El `DocumentBuilder` es nuestra práctica “pluma” que nos permite dibujar, insertar texto y—crucialmente—colocar controles ActiveX.

```csharp
// Initialize a new, empty Word document.
Document doc = new Document();

// Attach a builder to the document for editing.
DocumentBuilder builder = new DocumentBuilder(doc);
```

En este punto el documento es solo un lienzo en blanco—piénsalo como una hoja limpia esperando tu botón de comando.

---

## Paso 3: Insertar el Control ActiveX CommandButton

Ahora finalmente **add command button to word document**. Aspose.Words proporciona el método `InsertForms2OleControl`, que acepta el tipo de control y sus dimensiones. Usaremos `Forms2OleControlType.CommandButton` y le daremos un ancho cómodo de 150 puntos y una altura de 30 puntos.

```csharp
// Insert a CommandButton ActiveX control with a specific size.
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton,
    width: 150,
    height: 30);
```

El método devuelve una instancia `Forms2OleControl`, que utilizaremos para **set activex control properties** en el siguiente paso.

---

## Paso 4: Configurar el Control – Nombre, Texto y Posición

### Establecer el Texto

El texto es el que aparece en el propio botón. Para **set command button caption**, simplemente asigna una cadena a la propiedad `Caption`:

```csharp
commandButton.Caption = "Submit";
```

Puedes cambiar `"Submit"` a cualquier cosa—“Save”, “Export”, “Launch”, etc.—y Word mostrará ese texto exacto.

### Nombrar el Control

Dar al control un nombre significativo facilita referenciarlo después (por ejemplo, al automatizar macros de Word). Estableceremos la propiedad `Name`:

```csharp
commandButton.Name = "btnSubmit";
```

### Posicionar en la Página

Word usa puntos (1/72 de pulgada) para el diseño. Ajusta las propiedades `Left` y `Top` para colocar el botón donde lo necesites:

```csharp
commandButton.Left = 100; // 100 points from the left margin
commandButton.Top  = 200; // 200 points from the top of the page
```

Si necesitas alinear el botón respecto a un párrafo, puedes mover primero el cursor del builder y luego insertar el control; las coordenadas serán relativas a esa ubicación.

*Edge case:* En monitores de alta DPI el tamaño visual puede aparecer ligeramente diferente en Word. Para mantener el tamaño físico del botón consistente en todos los dispositivos, puedes calcular los puntos basándote en el DPI objetivo (normalmente 96 DPI para Word).

---

## Paso 5: Guardar el Documento

Con el botón totalmente configurado, guardar el archivo es una sola línea:

```csharp
// Save the document; the ActiveX control is stored inside the DOCX.
doc.Save("CommandButton.docx");
```

El `CommandButton.docx` resultante contiene un botón ActiveX totalmente funcional. Ábrelo en Microsoft Word y verás un botón “Submit” posicionado exactamente donde lo colocaste.

### Resultado Esperado

1. El documento Word se abre con una sola página.
2. Un botón rectangular etiquetado **Submit** aparece en las coordenadas que especificaste.
3. Si haces clic derecho en el botón y eliges **Properties**, verás el nombre `btnSubmit` y otras propiedades que configuraste.

---

## Paso 6: Variaciones Avanzadas y Errores Comunes

### Insertar Otros Tipos de ActiveX

El método `InsertForms2OleControl` no se limita a botones de comando. Puedes incrustar casillas de verificación, botones de opción o incluso objetos ActiveX personalizados:

```csharp
// Example: Insert a CheckBox instead of a CommandButton.
Forms2OleControl checkBox = builder.InsertForms2OleControl(
    Forms2OleControlType.CheckBox,
    width: 20,
    height: 20);
checkBox.Name = "chkAgree";
checkBox.Caption = "I Agree";
```

El mismo patrón de **set activex control properties** se aplica—solo cambia el enum de tipo.

### Manejo de Versiones de Word

Las versiones más antiguas de Word (pre‑2007) usan el formato binario `.doc`, que almacena los controles ActiveX de forma diferente. Aspose.Words convierte automáticamente el control al guardar como `.doc`, pero algunas propiedades (como la posición precisa) pueden desplazarse. Si apuntas a formatos heredados, prueba la salida en la versión específica de Word que necesites.

### Configuraciones de Seguridad

Word puede desactivar los controles ActiveX en máquinas con seguridad de macros estricta. Para evitar el cuadro de diálogo “Security Warning”, considera:

* Firmar el documento con un certificado de confianza.
* Indicar a los usuarios que habiliten el contenido ActiveX para esa ubicación de archivo.
* Usar una alternativa sin macros (p.ej., controles de contenido simples) si la seguridad es una preocupación.

---

## Paso 7: Ejemplo Completo Funcional

A continuación se muestra el programa completo, listo para ejecutar, que incorpora cada paso que discutimos. Cópialo en tu `Program.cs`, ajusta la ruta de salida si es necesario y pulsa **Run**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.ActiveX;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a CommandButton ActiveX control.
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,
            width: 150,   // Width in points
            height: 30);  // Height in points

        // Step 3: Set the control's name and caption.
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";

        // Step 4: Position the control on the page.
        commandButton.Left = 100; // 100 points from left edge
        commandButton.Top  = 200; // 200 points from top edge

        // Optional: Add a paragraph above the button for context.
        builder.MoveToDocumentEnd();
        builder.Writeln("Click the button below to submit the form:");

        // Step 5: Save the document.
        string outputPath = "CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved successfully to {outputPath}");
    }
}
```

**Qué hace este código:**

* Comienza con un documento nuevo.
* Inserta un botón de comando, **sets activex control properties**, y **sets command button caption**.
* Agrega un breve párrafo explicativo.
* Guarda el archivo como `CommandButton.docx`.

Ejecuta el programa, abre el archivo generado y verás el botón situado debajo del texto explicativo.

---

## Conclusión

Acabamos de demostrar cómo **add command button to word document** usando Aspose.Words, cómo **set activex control properties**, y cómo **set command button caption**—todo en un fragmento C# conciso y listo para producción. El enfoque escala: cambia el tipo de control, ajusta dimensiones, o itera sobre una fuente de datos para incrustar docenas de botones automáticamente.

¿Quieres ir más allá? Prueba:

* Vincular el botón a una macro que active una exportación de datos.
* Agregar imágenes o íconos personalizados dentro del botón usando la propiedad `Picture`.
* Construir un formulario completo con múltiples controles ActiveX (cuadros de texto, cuadros combinados, etc.).

La experimentación es la mejor manera de dominar la automatización de Word. Si encuentras un problema, recuerda verificar nuevamente tus cálculos de DPI y la configuración de seguridad de Word. ¡Feliz codificación, y que tus documentos sean cada vez más interactivos!

## ¿Qué Deberías Aprender a Continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Add Content Using Document Builder in Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}