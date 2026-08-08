---
category: general
date: 2026-08-07
description: Aprende cómo agregar un control ActiveX en un documento de Word usando
  C#. Incluye asociar una macro con un botón y añadir ejemplos de botones clicables
  en Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex control
- associate macro with button
- add clickable button word
- add command button word
language: es
lastmod: 2026-08-07
og_description: cómo agregar un control ActiveX en un documento de Word usando Aspose.Words.
  Sigue esta guía para insertar un botón, asociar una macro al botón y agregar una
  palabra de botón clicable.
og_image_alt: Screenshot showing a Word document with an ActiveX command button inserted
  via Aspose.Words
og_title: Cómo agregar un control ActiveX en Word – tutorial completo de C#
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Learn how to add activex control in a Word document using C#. Includes
    associate macro with button and add clickable button word examples.
  headline: how to add activex control in Word with Aspose.Words – step‑by‑step guide
  type: TechArticle
- description: Learn how to add activex control in a Word document using C#. Includes
    associate macro with button and add clickable button word examples.
  name: how to add activex control in Word with Aspose.Words – step‑by‑step guide
  steps:
  - name: Why each line matters
    text: '| Line | Purpose | |------|---------| | `Document doc = new Document();`
      | Instantiates a fresh Word package in memory. | | `DocumentBuilder builder
      = new DocumentBuilder(doc);` | Provides a fluent API for inserting content,
      including ActiveX controls. | | `InsertForms2OleControl` | The only Aspose.'
  - name: Common pitfalls when associating a macro
    text: '* **Macro security settings** – If the document is opened on a machine
      with strict security policies, the macro may be blocked. Provide instructions
      to lower the security level or sign the macro. * **Naming conflicts** – The
      macro name must be unique within the document’s VBA project; otherwise Word'
  - name: 'Edge case: Long captions'
    text: Word truncates captions that exceed the button’s width. To avoid clipping,
      either increase the width argument in `InsertForms2OleControl` or shorten the
      text. Testing with different languages (e.g., German or Japanese) is advisable
      because character width varies.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Cómo agregar un control ActiveX en Word con Aspose.Words – guía paso a paso
url: /es/net/working-with-oleobjects-and-activex/how-to-add-activex-control-in-word-with-aspose-words-step-by/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# cómo agregar un control activex en Word con Aspose.Words

Si necesita **how to add activex control** en un archivo Microsoft Word de forma programática, este tutorial le muestra los pasos exactos usando Aspose.Words para .NET. Verá cómo insertar un botón de comando, establecer su leyenda, y **associate macro with button** para que el control reaccione cuando el usuario haga clic en él. Al final tendrá un archivo `.docm` habilitado para macros que contiene un botón totalmente funcional.

Agregar un botón ActiveX es un requisito común al crear plantillas interactivas como solicitudes de préstamo, formularios de incorporación de empleados o informes automatizados. Esta guía recorre cada línea de código, explica **why** cada paso y cubre los problemas típicos que podría encontrar.

## Requisitos previos

* .NET 6 (o .NET Core 3.1 / .NET Framework 4.8) instalado.  
* Una licencia válida de Aspose.Words para .NET o una clave de evaluación temporal.  
* Visual Studio 2022 (o cualquier IDE que soporte C#).  
* Familiaridad básica con macros de Word (VBA) si planea escribir la macro que activará el botón.

> **Consejo profesional:** Cuando ejecute el ejemplo, guarde la salida en una carpeta donde tenga permiso de escritura, de lo contrario `doc.Save` lanzará una excepción.

## Cómo agregar un control ActiveX en un documento Word usando Aspose.Words

El núcleo de la solución es un breve programa en C# que crea un nuevo documento, inserta un control ActiveX **CommandButton**, y guarda el archivo como un documento habilitado para macros (`.docm`). El código está completo y listo para copiar‑pegar.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert an ActiveX CommandButton control (Forms2OleControl)
        // Parameters: control type, left, top, width, height (in points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            0,   // left position (points)
            0,   // top position (points)
            150, // width (points)
            30   // height (points)
        );

        // Step 3: Set the button's visible caption – this is the add clickable button word
        commandButton.Caption = "Click Me";

        // Step 4 (optional): Associate a macro with the button's click action
        // This demonstrates how to associate macro with button
        commandButton.OnAction = "MyMacro";

        // Step 5: Save the document as a macro‑enabled file to preserve the button reference
        // The file extension .docm tells Word to keep ActiveX controls and macros
        doc.Save("CommandButton.docm");
    }
}
```

### Por qué cada línea es importante

| Línea | Propósito |
|------|-----------|
| `Document doc = new Document();` | Instancia un nuevo paquete Word en memoria. |
| `DocumentBuilder builder = new DocumentBuilder(doc);` | Proporciona una API fluida para insertar contenido, incluidos controles ActiveX. |
| `InsertForms2OleControl` | El único método de Aspose.Words que crea un control ActiveX; especifica el tipo de control (`CommandButton`) y su geometría. |
| `commandButton.Caption = "Click Me";` | Establece el **add clickable button word** que el usuario final ve. Sin una leyenda el botón aparece en blanco. |
| `commandButton.OnAction = "MyMacro";` | **associate macro with button** – indica a Word qué macro VBA ejecutar cuando se hace clic en el control. |
| `doc.Save("CommandButton.docm");` | Guarda el documento como un archivo habilitado para macros; un `.docx` regular eliminaría el control y la macro. |

> **Nota:** Las coordenadas (izquierda, superior) se miden en puntos (1 pt ≈ 1/72 in). Ajústelos para posicionar el botón donde lo necesite en la página.

## Cómo asociar una macro al botón

La propiedad `OnAction` vincula el botón a una macro VBA llamada `MyMacro`. Aún necesita crear esa macro dentro del archivo Word, ya sea manualmente o inyectando código VBA programáticamente (Aspose.Words no escribe código VBA). Aquí hay una macro mínima que puede agregar usando el editor **Developer → Visual Basic** de Word:

```vba
Sub MyMacro()
    MsgBox "Button clicked!", vbInformation, "ActiveX Demo"
End Sub
```

Cuando el usuario abre `CommandButton.docm` y hace clic en el botón, Word ejecuta `MyMacro` y muestra un cuadro de mensaje. Si la seguridad de macros está configurada en **Disable all macros without notification**, el botón aparecerá deshabilitado. Recomiende a los usuarios habilitar macros para el documento o firmar la macro con un certificado de confianza.

### Problemas comunes al asociar una macro

* **Configuraciones de seguridad de macros** – Si el documento se abre en una máquina con políticas de seguridad estrictas, la macro puede ser bloqueada. Proporcione instrucciones para reducir el nivel de seguridad o firmar la macro.  
* **Conflictos de nombres** – El nombre de la macro debe ser único dentro del proyecto VBA del documento; de lo contrario Word mostrará errores de “nombre de procedimiento duplicado”.  
* **Word 64‑bit vs 32‑bit** – Los controles ActiveX funcionan igual, pero el editor VBA puede mostrar mensajes de advertencia diferentes según la versión de Office.  

## Cómo agregar la palabra de botón clicable a un formulario Word

La propiedad `Caption` es lo que los usuarios ven en el botón. Puede personalizarla más:

```csharp
commandButton.Caption = "Submit Form";
commandButton.Font.Size = 10;      // Adjust font size
commandButton.Font.Name = "Arial"; // Choose a readable font
```

Si necesita que la leyenda cambie dinámicamente según la entrada del usuario, puede acceder al control más tarde mediante el modelo de objetos de Word:

```vba
Sub UpdateButtonCaption()
    Dim btn As InlineShape
    Set btn = ActiveDocument.InlineShapes(1).OLEFormat.Object
    btn.Caption = "Updated Text"
End Sub
```

### Caso límite: Leyendas largas

Word trunca las leyendas que exceden el ancho del botón. Para evitar el recorte, aumente el argumento de ancho en `InsertForms2OleControl` o acorte el texto. Es aconsejable probar con diferentes idiomas (p. ej., alemán o japonés) porque el ancho de los caracteres varía.

## Cómo agregar la palabra de botón de comando para automatización de formularios

Más allá de la leyenda visual, el concepto **add command button word** cubre el nombre programático del control. Aspose.Words no expone una propiedad directa `Name` para controles ActiveX, pero puede establecer el campo `AltText`, que Word trata como el identificador del control:

```csharp
commandButton.AltText = "SubmitButton";
```

Más tarde en VBA puede referenciar el botón por su valor `AltText`:

```vba
Sub FindButton()
    Dim shp As Shape
    For Each shp In ActiveDocument.Shapes
        If shp.AlternativeText = "SubmitButton" Then
            MsgBox "Found the Submit button!"
        End If
    Next shp
End Sub
```

Esta técnica es útil cuando tiene varios botones y necesita diferenciarlos programáticamente.

## Ejemplo completo funcionando

A continuación se muestra el programa completo que puede compilar y ejecutar como una aplicación de consola. Incluye estilo opcional, asociación de macro y un bloque de comentarios que describe cada paso.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class AddActiveXButton
{
    static void Main()
    {
        // 1️⃣ Create a new document and a builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert an ActiveX CommandButton.
        //    left=50pt, top=100pt places the button away from the margin.
        Forms2OleControl btn = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            50,   // left
            100,  // top
            200,  // width
            40    // height
        );

        // 3️⃣ Add clickable button word (caption) and style it.
        btn.Caption = "Submit Form";
        btn.Font.Size = 11;
        btn.Font.Name = "Calibri";

        // 4️⃣ Associate macro with button – this is how to associate macro with button.
        btn.OnAction = "SubmitMacro";

        // 5️⃣ Give the control a friendly identifier (add command button word).
        btn.AltText = "SubmitButton";

        // 6️⃣ Save as macro‑enabled document.
        doc.Save("SubmitForm.docm");
    }
}
```

**Resultado esperado:** Al abrir `SubmitForm.docm` en Microsoft Word se muestra un botón con borde azul etiquetado *Submit Form*. Al hacer clic en el botón se dispara la macro VBA `SubmitMacro` (si agregó la macro al documento). El botón puede moverse, redimensionarse o estilizarse más usando el mismo objeto `Forms2OleControl`.

## Probando la solución

1. Compile y ejecute la aplicación de consola C#.  
2. Abra el `SubmitForm.docm` generado en Word.  
3. Si se le solicita, habilite las macros.  
4. Haga clic en el botón *Submit Form* – debería ver el cuadro de mensaje definido en `SubmitMacro`.

Si el botón aparece pero no hace nada, verifique que el nombre de la macro coincida exactamente (`SubmitMacro`) y que la seguridad de macros no esté bloqueando la ejecución.

## Preguntas frecuentes

| Pregunta | Respuesta |
|----------|-----------|
| *¿Puedo agregar más de un botón ActiveX?* | Sí. Llame a `InsertForms2OleControl` varias veces con diferentes coordenadas. Use valores distintos de `OnAction` y `AltText` para diferenciarlos. |
| *¿El control ActiveX es visible en Word Online?* | No. |

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos con explicaciones paso a paso para ayudarle a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en sus propios proyectos.

- [Agregar contenido usando Document Builder en Aspose.Words para .NET](/words/english/net/add-content-using-document-builder/)
- [Tutorial de sombra de forma Aspose.Words – Agregar una sombra a una forma Word en C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Agregar una nueva sección a un documento Word | Aspose.Words para .NET](/words/english/net/document-sections/add-section/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}