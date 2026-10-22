---
category: general
date: 2026-08-20
description: Aprende cómo crear un control ActiveX, establecer el tamaño del botón
  y agregar el botón a Word con un ejemplo completo en C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex control
- set button size
- add button to word
- how to insert button
- create clickable button
language: es
lastmod: 2026-08-20
og_description: Crear un control ActiveX en un archivo de Word con C#. Este tutorial
  muestra cómo establecer el tamaño del botón, agregar el botón a Word y crear un
  botón clicable.
og_image_alt: Screenshot of a Word document showing a newly created ActiveX control
  button
og_title: Crea un control ActiveX en Word – guía paso a paso en C#
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to create ActiveX control, set button size, and add button
    to Word with a complete C# example.
  headline: How to create ActiveX control in a Word document using C#
  type: TechArticle
- description: Learn how to create ActiveX control, set button size, and add button
    to Word with a complete C# example.
  name: How to create ActiveX control in a Word document using C#
  steps:
  - name: Why this works
    text: '* `InsertForms2OleControl` tells Word to embed an OLE object of type **CommandButton**,
      which is the classic ActiveX button class. * The width and height arguments
      directly **set button size**; Word translates the values from points (1 pt ≈
      1/72 in). * Naming the control (`Name = "btnSubmit"`) makes'
  - name: Pro tip
    text: 'If you want a square button, set both dimensions to the same value:'
  - name: 1. What if the button does not appear after saving?
    text: '* Verify that the Aspose.Words version supports `InsertForms2OleControl`.
      Versions prior to 22.5 lack this feature. * Ensure the target file format is
      `.docx` or `.doc`. Older formats like `.rtf` cannot store ActiveX objects.'
  - name: 2. Can I insert the button at a specific bookmark?
    text: 'Yes. Move the builder to the bookmark before calling `InsertForms2OleControl`:'
  - name: 3. How to **set button size** dynamically based on text length?
    text: Calculate the required width using the `Graphics.MeasureString` method (from
      `System.Drawing`) and convert pixels to points (`points = pixels * 72 / DPI`).
      Then pass the computed width to `InsertForms2OleControl`.
  - name: 4. Is there a way to add multiple buttons in a loop?
    text: 'Absolutely. Wrap the insertion logic in a `for` loop and adjust the `Left`
      and `Top` properties for each iteration:'
  type: HowTo
tags:
- ActiveX
- C#
- Aspose.Words
- Word automation
title: Cómo crear un control ActiveX en un documento de Word usando C#
url: /es/java/integration-interoperability/how-to-create-activex-control-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo crear un control ActiveX en un documento Word usando C#

Si necesita **crear un control ActiveX** dentro de un archivo Microsoft Word, esta guía le muestra exactamente cómo hacerlo. Verá cómo **agregar un botón a Word**, establecer las dimensiones del botón y hacer que el control sea clicable, todo con un programa C# breve y autocontenido.

En este tutorial usted:

* Entenderá por qué un control ActiveX es útil para documentos Word interactivos.  
* Aprenderá el código exacto necesario para **establecer el tamaño del botón** y asignar un texto.  
* Verá cómo **crear un botón clicable** que luego puede enlazarse a una macro o lógica externa.  

Los pasos funcionan con Aspose.Words .NET 23.12 o posterior y solo requieren un entorno de desarrollo .NET.

> **Prerequisite** – Tiene una licencia válida de Aspose.Words (o está usando la versión de evaluación) y Visual Studio 2022 o cualquier IDE de C#.

---

## Cómo crear un control ActiveX en un documento Word

El primer paso es instanciar un `Document` vacío y un `DocumentBuilder`. El builder proporciona la API de alto nivel para insertar objetos como controles ActiveX.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new empty document and obtain a DocumentBuilder.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // The rest of the steps are explained in the following sections.
            InsertActiveXButton(builder);

            // Save the result so you can open it in Word.
            doc.Save("ActiveXButton.docx");
            Console.WriteLine("Document saved as ActiveXButton.docx");
        }
```

El método `InsertActiveXButton` (definido a continuación) contiene la lógica para **cómo insertar un botón** y configurarlo.

```csharp
        /// <summary>
        /// Inserts a CommandButton ActiveX control, sets its size, name, and caption.
        /// </summary>
        static void InsertActiveXButton(DocumentBuilder builder)
        {
            // Step 2: Insert a CommandButton ActiveX control with the desired size (width: 100, height: 30).
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                "CommandButton", 100, 30);

            // Step 3: Assign a name to the control for later reference.
            commandButton.Name = "btnSubmit";

            // Step 4: Set the caption that will be displayed on the button.
            commandButton.Caption = "Submit";

            // Optional: Position the button on the page (e.g., 100 points from the top left).
            commandButton.Left = 100;
            commandButton.Top = 150;
        }
    }
}
```

Ejecutar el programa crea **ActiveXButton.docx**. Al abrir el archivo en Word se muestra un botón con la etiqueta **Submit**. El control es totalmente funcional: al hacer clic se dispara el evento estándar `CommandButton_Click`, que luego puede enlazarse a una macro VBA.

### Por qué funciona esto

* `InsertForms2OleControl` indica a Word que incruste un objeto OLE de tipo **CommandButton**, que es la clase clásica de botón ActiveX.  
* Los argumentos de ancho y alto **establecen el tamaño del botón** directamente; Word traduce los valores de puntos (1 pt ≈ 1/72 in).  
* Nombrar el control (`Name = "btnSubmit"`) facilita su localización desde VBA (`ActiveDocument.InlineShapes("btnSubmit")`).  

---

## Establecer el tamaño y el texto del botón

Si necesita una apariencia diferente, ajuste los argumentos numéricos en la llamada a `InsertForms2OleControl`. La firma del método es:

```csharp
Forms2OleControl InsertForms2OleControl(string progId, double width, double height);
```

* **progId** – El identificador programático de la clase ActiveX (`"CommandButton"` para un botón estándar).  
* **width / height** – Tamaño en puntos. Para un botón de 2 cm de ancho, use `width = 56.7` (2 cm ≈ 56.7 pt).  

También puede modificar el texto después de la inserción:

```csharp
commandButton.Caption = "Send Request";
```

Cambiar el texto no afecta al tamaño, pero sí al feedback visual para el usuario.

### Consejo profesional

Si desea un botón cuadrado, establezca ambas dimensiones al mismo valor:

```csharp
Forms2OleControl squareBtn = builder.InsertForms2OleControl("CommandButton", 50, 50);
squareBtn.Caption = "OK";
```

---

## Agregar un botón a Word y hacerlo clicable

El código anterior ya **agrega un botón a Word**. Para que el botón realice una acción, debe escribir una macro VBA que maneje el evento `Click`. Aquí tiene una macro mínima que puede pegar en el editor VBA de Word (`Alt+F11` → Insert → Module):

```vba
Sub btnSubmit_Click()
    MsgBox "You clicked the Submit button!", vbInformation
End Sub
```

Como el control se llama `btnSubmit`, Word asigna automáticamente el evento `Click` a `btnSubmit_Click`. Esta es la forma estándar de **crear un botón clicable** sin bibliotecas externas.

> **Note:** La configuración de seguridad de macros en Word puede bloquear controles ActiveX. Asegúrese de que “Enable all macros” o “Enable VBA macros” esté seleccionado para el documento, o firme digitalmente la macro para uso en producción.

---

## Preguntas comunes: cómo insertar un botón y solución de problemas

### 1. ¿Qué pasa si el botón no aparece después de guardar?

* Verifique que la versión de Aspose.Words admita `InsertForms2OleControl`. Las versiones anteriores a la 22.5 no incluyen esta característica.  
* Asegúrese de que el formato de archivo de destino sea `.docx` o `.doc`. Los formatos antiguos como `.rtf` no pueden almacenar objetos ActiveX.

### 2. ¿Puedo insertar el botón en un marcador específico?

Sí. Mueva el builder al marcador antes de llamar a `InsertForms2OleControl`:

```csharp
builder.MoveToBookmark("InsertHere");
builder.InsertForms2OleControl("CommandButton", 100, 30);
```

### 3. ¿Cómo **establecer el tamaño del botón** dinámicamente según la longitud del texto?

Calcule el ancho necesario usando el método `Graphics.MeasureString` (de `System.Drawing`) y convierta píxeles a puntos (`points = pixels * 72 / DPI`). Luego pase el ancho calculado a `InsertForms2OleControl`.

### 4. ¿Hay una forma de agregar varios botones en un bucle?

Absolutamente. Envuelva la lógica de inserción en un bucle `for` y ajuste las propiedades `Left` y `Top` en cada iteración:

```csharp
for (int i = 0; i < 3; i++)
{
    Forms2OleControl btn = builder.InsertForms2OleControl("CommandButton", 80, 25);
    btn.Name = $"btnOption{i + 1}";
    btn.Caption = $"Option {i + 1}";
    btn.Left = 50;
    btn.Top = 100 + i * 40; // stagger vertically
}
```

---

## Resultado esperado

Al ejecutar el programa y abrir **ActiveXButton.docx**:

* Aparece un único botón **Submit** cerca de la esquina superior izquierda de la primera página.  
* El tamaño del botón coincide con las dimensiones que proporcionó (`100 pt × 30 pt`).  
* Si agregó la macro VBA, al hacer clic se muestra un cuadro de mensaje: “You clicked the Submit button!”.

Ahora ha creado con éxito **un control ActiveX**, **establecido el tamaño del botón** y **agregado el botón a Word**, mientras aprendía **cómo insertar un botón** y **crear un botón clicable** para futuras tareas de automatización.

---

## Conclusión

En este tutorial aprendió a **crear un control ActiveX** dentro de un documento Word con C#. Siguiendo los pasos puede **establecer el tamaño del botón**, dar al control un nombre significativo y **agregar el botón a Word** para que se convierta en un **botón clicable** vinculado a una macro VBA.  

A partir de aquí podría explorar:

* Vincular el botón a un complemento COM .NET en lugar de VBA.  
* Usar otras clases ActiveX como `CheckBox` o `ComboBox`.  
* Automatizar la creación de formularios completos con múltiples controles.

Siéntase libre de experimentar con diferentes tamaños

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarle a dominar características adicionales de la API y explorar enfoques de implementación alternativos en sus propios proyectos.

- [Crear documento Word con imagen flotante en .NET](/words/english/net/add-content-using-document-builder/insert-floating-image/)
- [Crear documento Word con encabezado y pie de página usando Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Crear PDF accesible desde Word – Guía completa](/words/english/net/programming-with-pdfsaveoptions/create-accessible-pdf-from-word-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}