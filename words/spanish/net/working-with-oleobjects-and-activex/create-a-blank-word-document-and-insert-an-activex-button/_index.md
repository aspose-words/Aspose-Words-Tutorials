---
category: general
date: 2026-11-18
description: Crea un documento de Word en blanco e inserta un botón ActiveX con C#.
  Aprende cómo agregar el control, establecer el texto del botón y guardar el archivo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert activex
- how to add control
- insert activex button
- set button caption
language: es
lastmod: 2026-11-18
og_description: Crea un documento Word en blanco e inserta un botón ActiveX usando
  C#. Sigue este tutorial completo para agregar el control, establecer el texto del
  botón y guardar el resultado.
og_image_alt: Screenshot of a Word document showing an inserted ActiveX button with
  the caption “Press”
og_title: Crea un documento de Word en blanco e inserta un botón ActiveX – guía paso
  a paso
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Create a blank Word document and insert an ActiveX button with C#.
    Learn how to add control, set button caption, and save the file.
  headline: Create a blank Word document and insert an ActiveX button
  type: TechArticle
- description: Create a blank Word document and insert an ActiveX button with C#.
    Learn how to add control, set button caption, and save the file.
  name: Create a blank Word document and insert an ActiveX button
  steps:
  - name: Prerequisites
    text: '* .NET 6.0 or later (the code also works with .NET Framework 4.6+). * Aspose.Words
      for .NET installed (`Install-Package Aspose.Words`). * Basic familiarity with
      C# and Visual Studio or any .NET‑compatible IDE.'
  - name: Tip
    text: 'If you need the button to appear on a specific page, move the builder’s
      cursor first:'
  - name: Expected result
    text: Opening `with_button.docx` in Word shows a blank page with a rectangular
      button labeled **Press**. Clicking the button does nothing by default because
      no VBA macro is attached, but the control is fully functional and can be wired
      to code later.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: Crear un documento de Word en blanco e insertar un botón ActiveX
url: /es/net/working-with-oleobjects-and-activex/create-a-blank-word-document-and-insert-an-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear un documento Word en blanco e insertar un botón ActiveX

Si necesitas **crear un documento Word en blanco** y colocar un botón ActiveX interactivo dentro de él, esta guía te muestra exactamente cómo hacerlo con Aspose.Words para .NET. Verás el código completo, entenderás por qué cada línea es importante y aprenderás a **establecer el texto del botón** para que el control parezca listo para la interacción del usuario.

Además del objetivo principal, cubriremos **cómo insertar ActiveX**, los pasos **cómo agregar un control** a un archivo Word y los matices de **insertar un botón ActiveX** con un texto personalizado. Al final tendrás un patrón reutilizable para cualquier escenario de automatización de documentos que requiera elementos de UI incrustados.

## Lo que aprenderás

* Cómo **crear un documento Word en blanco** de forma programática.  
* Las llamadas exactas a la API necesarias para **insertar un botón ActiveX** y configurar sus propiedades.  
* Cómo **establecer el texto del botón** para que el control muestre el texto deseado.  
* Consejos para guardar el archivo en la ubicación que prefieras y manejar problemas comunes.

### Requisitos previos

* .NET 6.0 o superior (el código también funciona con .NET Framework 4.6+).  
* Aspose.Words para .NET instalado (`Install-Package Aspose.Words`).  
* Familiaridad básica con C# y Visual Studio o cualquier IDE compatible con .NET.

---

## Crear un documento Word en blanco con Aspose.Words

El primer paso es instanciar un objeto `Document` vacío. Este objeto representa un archivo Word que no contiene contenido hasta que añadamos algo.

```csharp
// Step 1: Create a new blank document
Document document = new Document();
```

*Por qué es importante*: Un `Document` vacío te brinda un lienzo limpio. Puedes añadir párrafos, tablas o controles más adelante sin preocuparte por el formato existente.

---

## Inicializar un DocumentBuilder para trabajar con el documento

`DocumentBuilder` es una clase auxiliar que te permite insertar contenido en la posición actual del cursor. Rastrea automáticamente dónde te encuentras en el documento.

```csharp
// Step 2: Initialise a DocumentBuilder for the empty document
DocumentBuilder builder = new DocumentBuilder(document);
```

*Por qué es importante*: Sin un `DocumentBuilder` tendrías que manipular manualmente el árbol de nodos de bajo nivel. El builder simplifica la inserción de texto, imágenes y controles ActiveX.

---

## Cómo insertar un botón ActiveX (insert activex button)

Ahora usamos `InsertForms2OleControl` para incrustar un control ActiveX. El método requiere tres argumentos:

1. El tipo de control (`OleControlType.CommandButton`).  
2. Un nombre interno para el control (utilizado por VBA o código de macro).  
3. Un `RectangleF` que define la posición y el tamaño en la página.

```csharp
// Step 3: Insert a CommandButton ActiveX control at the current cursor position
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,          // type of control
    "ClickMe",                             // internal name (identifier)
    new System.Drawing.RectangleF(0, 0, 100, 30)); // x, y, width, height
```

*Por qué es importante*: Este es el núcleo de **cómo insertar activex** en un documento Word. Las coordenadas del rectángulo se expresan en puntos (1 punto = 1/72 de pulgada). Ajústalas para posicionar el botón donde lo necesites.

### Consejo

Si necesitas que el botón aparezca en una página específica, mueve primero el cursor del builder:

```csharp
builder.MoveToSection(0);  // moves to the first (and only) section
builder.InsertParagraph(); // ensures there is a paragraph to host the control
```

---

## Cómo establecer el texto del botón (set button caption)

Después de colocar el control, puedes modificar sus propiedades. La propiedad más visible es `Caption`, que determina el texto que se muestra en el botón.

```csharp
// Step 4: Set the visible caption of the button
commandButton.Caption = "Press";
```

*Por qué es importante*: Los usuarios ven el texto del botón, no el nombre interno. Cambiarlo hace que el botón sea significativo en el documento final.

---

## Guardar el documento que contiene el botón

Finalmente, escribe el documento en disco. Puedes elegir cualquier formato compatible (`.docx`, `.pdf`, etc.). Aquí lo guardamos como documento Word.

```csharp
// Step 5: Save the document with the ActiveX button
string outputPath = @"C:\Temp\with_button.docx";
document.Save(outputPath);
```

*Por qué es importante*: Persistir el archivo permite abrirlo en Microsoft Word y probar el botón. Cuando el documento se abre, el botón aparecerá con el texto “Presionar”.

### Resultado esperado

Al abrir `with_button.docx` en Word se muestra una página en blanco con un botón rectangular etiquetado **Presionar**. Hacer clic en el botón no produce ninguna acción por defecto porque no hay una macro VBA asociada, pero el control está completamente funcional y puede enlazarse a código más adelante.

---

## Cómo agregar un control a un párrafo específico (how to add control)

A veces deseas que el botón esté dentro de un párrafo concreto, por ejemplo después de algún texto instructivo. Usa `MoveTo` para posicionar el builder antes de insertar el control.

```csharp
// Example: add a paragraph, then insert the button after it
builder.Writeln("Click the button below to continue:");
builder.InsertParagraph(); // creates a new empty paragraph
builder.InsertForms2OleControl(
    OleControlType.CommandButton,
    "ContinueBtn",
    new System.Drawing.RectangleF(0, 0, 120, 35));
```

*Por qué es importante*: Este patrón demuestra **cómo agregar control** en contexto, asegurando que el diseño del documento siga siendo lógico.

---

## Problemas comunes y cómo evitarlos

| Problema | Por qué ocurre | Solución |
|----------|----------------|----------|
| El botón aparece fuera de la página | Las coordenadas del rectángulo están fuera de los márgenes | Usa `builder.PageSetup` para obtener las dimensiones de la página y calcula un `RectangleF` seguro. |
| El texto no se muestra | `Caption` se establece antes de que el control esté completamente inicializado | Establece `Caption` **después** de la llamada a `InsertForms2OleControl`, como se muestra en el Paso 4. |
| El documento se guarda sin el botón | El cursor del builder se movió después de la inserción sin confirmar los cambios | Mantén el builder en la misma página o llama a `builder.Document.UpdatePageLayout()` antes de guardar. |

---

## Ejemplo completo y ejecutable

A continuación tienes el programa completo que puedes copiar, pegar y ejecutar. Crea un archivo Word en blanco, inserta un botón ActiveX, establece su texto y guarda el resultado.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Initialise DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(document);

        // Optional: add some explanatory text
        builder.Writeln("Below is an ActiveX button created programmatically:");
        builder.InsertParagraph();

        // 3️⃣ Insert the ActiveX CommandButton
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            "MyButton",
            new RectangleF(0, 0, 100, 30));

        // 4️⃣ Set the button caption
        commandButton.Caption = "Press";

        // 5️⃣ Save the document
        string outputPath = @"C:\Temp\with_button.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Salida**: Después de ejecutar el programa, abre `C:\Temp\with_button.docx` en Microsoft Word. Verás una sola página con el texto “A continuación se muestra un botón ActiveX creado programáticamente:” seguido de un botón etiquetado **Presionar**.

---

## Conclusión

Ahora sabes cómo **crear un documento Word en blanco**, **insertar un botón ActiveX**, **establecer el texto del botón** y **guardar** el resultado usando Aspose.Words para .NET. El mismo patrón puede ampliarse a otros controles ActiveX (casillas de verificación, listas, etc.) cambiando `OleControlType`.  

A continuación, podrías explorar **cómo insertar eventos de botón ActiveX** con VBA, o **cómo agregar control** a documentos existentes que ya contienen contenido. Ambos temas se basan directamente en los conceptos cubiertos aquí.

¡Feliz codificación y siéntete libre de experimentar con diferentes tamaños, posiciones y textos para adaptarlos a los requisitos de UI de tu aplicación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques alternativos de implementación en tus propios proyectos.

- [How to create Word document C# with an ActiveX command button](/words/english/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-with-an-activex-command-button/)
- [How to add ActiveX button in a Word document with Aspose.Words](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}