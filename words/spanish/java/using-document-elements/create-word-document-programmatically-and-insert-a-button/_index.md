---
category: general
date: 2026-09-21
description: Crear documento de Word programáticamente y aprender cómo guardar el
  documento de Word con un botón, insertar un botón de comando de Word y establecer
  el texto del botón de comando usando DocumentBuilder.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- save word document button
- insert command button word
- set command button caption
- how to use documentbuilder
language: es
lastmod: 2026-09-21
og_description: Crea documentos Word programáticamente con Aspose.Words. Aprende cómo
  guardar el documento Word con un botón, insertar un botón de comando, establecer
  el texto del botón de comando y usar DocumentBuilder para formularios interactivos.
og_image_alt: Screenshot of a Word file that contains an inserted CommandButton created
  programmatically
og_title: Crear documento de Word programáticamente y añadir un botón
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create word document programmatically and learn how to save word document
    button, insert command button word, and set command button caption using DocumentBuilder.
  headline: Create word document programmatically and insert a button
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word Automation
title: Crear documento de Word programáticamente e insertar un botón
url: /es/java/using-document-elements/create-word-document-programmatically-and-insert-a-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear documento Word programáticamente e insertar un botón

Si necesitas **crear documento Word programáticamente**, Aspose.Words ofrece una API fluida que te permite añadir controles interactivos como un CommandButton. Este tutorial también explica **cómo usar DocumentBuilder**, cómo **guardar documento Word con botón**, y cómo **establecer el texto del botón** para que aparezca exactamente como esperas dentro del archivo .docx.

Aprenderás a:

* Inicializar un documento en blanco con `Document`.
* Trabajar con `DocumentBuilder` para editar el documento.
* Insertar un **CommandButton** (`insert command button word`).
* Establecer el nombre y el texto visible del botón (`set command button caption`).
* Persistir el resultado en disco (`save word document button`).

Los pasos están escritos para desarrolladores .NET que usan C# y la última versión de Aspose.Words para .NET (v24.10). No se requieren paquetes NuGet adicionales más allá de Aspose.Words.

---

## Qué necesitas antes de comenzar

| Requisito previo | Razón |
|------------------|-------|
| Visual Studio 2022 (o cualquier IDE de C#) | Para compilar y ejecutar el código de ejemplo. |
| .NET 6.0 SDK o posterior | Proporciona el tiempo de ejecución para el ejemplo. |
| Aspose.Words para .NET (v24.10 o más reciente) | La biblioteca que te permite **crear documento Word programáticamente** y manipular controles de formulario. |
| Familiaridad básica con C# y conceptos OOP | Necesario para comprender el flujo del código. |

Puedes instalar Aspose.Words vía NuGet:

```bash
dotnet add package Aspose.Words
```

---

## Crear documento Word programáticamente

El primer paso es instanciar un `Document` vacío. Este objeto representa todo el archivo Word en memoria.

```csharp
// Step 1: Create a new blank document
Document doc = new Document();
```

Crear el documento programáticamente te brinda un lienzo limpio en el que puedes añadir párrafos, tablas o controles interactivos.  

---

## Cómo usar DocumentBuilder

`DocumentBuilder` es la clase principal para editar un `Document`. Proporciona métodos para insertar texto, imágenes y campos de formulario. En este tutorial lo usamos para colocar un CommandButton.

```csharp
// Step 2: Initialize a DocumentBuilder to edit the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

El builder mantiene un cursor interno que apunta a la ubicación actual de inserción. Por defecto comienza al inicio de la primera sección, lo cual es ideal para nuestro ejemplo.

---

## Insertar command button word

Aspose.Words trata un CommandButton como un control ActiveX. El método `InsertForms2OleControl` crea un control OLE genérico que luego configuramos como botón.

```csharp
// Step 3: Insert an ActiveX Forms2OleControl (a CommandButton)
Forms2OleControl commandButton = builder.InsertForms2OleControl();
```

En este punto el control existe en el documento pero no tiene representación visual hasta que definimos su tipo.

---

## Establecer el texto del botón

Ahora indicamos al control OLE que debe comportarse como un CommandButton y le asignamos una etiqueta amigable.

```csharp
// Step 4: Define the control as a CommandButton
commandButton.SetControlType(Forms2OleControlType.COMMANDBUTTON);

// Step 5: Set a unique name for the button (used for identification)
commandButton.SetName("btnSubmit");

// Step 6: Set the visible caption that appears on the button
commandButton.SetCaption("Submit");
```

Establecer el **texto del botón** es esencial porque Word muestra este texto en la superficie del botón. Si omites `SetCaption`, el botón aparecerá con una etiqueta genérica.

---

## Guardar documento Word con botón

Finalmente, persiste el documento en disco. El método `Save` escribe todo el paquete Word, incluido el botón recién insertado, en un archivo .docx.

```csharp
// Step 7: Save the document containing the CommandButton
doc.Save("YOUR_DIRECTORY/CommandButton.docx");
```

El archivo `CommandButton.docx` ahora contiene un botón totalmente funcional con la etiqueta **Submit**. Cuando el usuario abre el archivo en Microsoft Word y hace clic en el botón, se ejecutará la acción predeterminada (que luego puedes enlazar mediante VBA).

---

## Ejemplo completo

A continuación tienes el programa completo que puedes copiar, pegar y ejecutar. Demuestra todo el flujo de trabajo, desde la creación del documento hasta el guardado del botón.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Initialize DocumentBuilder (how to use DocumentBuilder)
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a CommandButton (insert command button word)
        Forms2OleControl commandButton = builder.InsertForms2OleControl();

        // 4. Define the control type as CommandButton
        commandButton.SetControlType(Forms2OleControlType.COMMANDBUTTON);

        // 5. Give the button a unique name (optional but useful)
        commandButton.SetName("btnSubmit");

        // 6. Set the visible caption (set command button caption)
        commandButton.SetCaption("Submit");

        // 7. Save the document (save word document button)
        string outputPath = @"C:\Temp\CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Resultado esperado**

* Un archivo llamado `CommandButton.docx` ubicado en la ruta que especificaste.
* Al abrir el archivo en Microsoft Word se muestra un único botón **Submit** en la primera página.
* El botón puede seleccionarse, redimensionarse o enlazarse a una macro desde la pestaña **Developer** de Word.

---

## Preguntas frecuentes y manejo de casos límite

| Pregunta | Respuesta |
|----------|-----------|
| *¿Qué pasa si necesito más de un botón?* | Repite los pasos 3‑6 con nombres y textos diferentes. Cada botón debe tener un valor único en `SetName`. |
| *¿Puedo establecer el tamaño del botón?* | Sí. Después de insertar el control, puedes modificar sus propiedades `Width` y `Height` mediante el objeto `OleFormat`. |
| *¿Funcionará el botón en todas las versiones de Word?* | Los controles ActiveX son compatibles con la versión de escritorio de Word (Windows). No se renderizan en Word Online ni en macOS. |
| *¿Cómo agregar un manejador de clic?* | Necesitas escribir código VBA que haga referencia al nombre del botón (`btnSubmit`). La macro VBA puede incrustarse usando `doc.VbaProject`. |
| *¿Qué pasa si necesito insertar el botón dentro de una celda de tabla?* | Mueve el cursor del builder a la celda deseada (`builder.MoveTo(cell.FirstParagraph)`) antes de llamar a `InsertForms2OleControl`. |

---

## Consejos profesionales

* **Consejo pro:** Siempre asigna un nombre significativo con `SetName`. Facilita la automatización VBA y simplifica la depuración.
* **Cuidado con:** Olvidar llamar a `SetControlType`. Sin esta llamada el objeto OLE aparece como un marcador genérico en lugar de un botón clicable.
* **Consejo de rendimiento:** Si generas muchos documentos en un bucle, reutiliza una única instancia de `DocumentBuilder` y llama a `builder.MoveToDocumentEnd()` antes de cada inserción para evitar reinicios innecesarios del cursor.

---

## Próximos pasos

Ahora que sabes cómo **crear documento Word programáticamente**, **insertar command button word**, **establecer el texto del botón** y **guardar documento Word con botón**, puedes explorar escenarios más avanzados:

* Añadir controles **TextFormField** para entrada del usuario.
* Combinar botones con campos **MacroButton** para ejecutar VBA directamente.
* Usar **DocumentBuilder.InsertImage** para colocar íconos en tus botones.
* Integrar con ASP.NET para generar formularios Word en

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Create New Word Document](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}