---
category: general
date: 2026-11-22
description: Aprende a insertar un control Forms2Ole en Word con C#. Esta guía paso
  a paso cubre DocumentBuilder, la colocación del botón de comando y el guardado del
  .docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert forms2ole control word
- Aspose.Words
- DocumentBuilder
- command button
- C# Word automation
language: es
lastmod: 2026-11-22
og_description: Inserte el control Forms2Ole en Word con C#. Siga esta guía para agregar
  un botón de comando usando Aspose.Words y DocumentBuilder.
og_image_alt: Screenshot of a Word document showing an inserted Forms2Ole command
  button created with C#
og_title: Insertar control Forms2Ole en Word con C# – guía completa
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Learn to insert a Forms2Ole control in Word with C#. This step‑by‑step
    guide covers DocumentBuilder, command button placement, and saving the .docx.
  headline: How to insert Forms2Ole control in Word using C# and Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Cómo insertar el control Forms2Ole en Word usando C# y Aspose.Words
url: /es/net/working-with-oleobjects-and-activex/how-to-insert-forms2ole-control-in-word-using-c-and-aspose-w/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo insertar el control Forms2Ole en Word usando C# y Aspose.Words

Si necesitas **insertar el control Forms2Ole en Word**, este tutorial te muestra exactamente cómo hacerlo con C#. Ya sea que estés creando una plantilla rellenable o automatizando la creación de formularios, la solución a continuación te permite agregar un botón de comando programáticamente.

Aprenderás cómo crear un documento en blanco, usar `DocumentBuilder` para colocar el control y guardar el resultado como un `.docx`. La guía también cubre problemas comunes, como los sistemas de coordenadas y la compatibilidad con versiones antiguas de Word.

## Requisitos previos

* .NET 6.0 o posterior (el código también funciona con .NET Framework 4.6+)
* Aspose.Words para .NET (paquete NuGet `Aspose.Words`)
* Un conocimiento básico de C# y del modelo de objetos de Word
* Un IDE como Visual Studio o VS Code

## Paso 1: Configurar el proyecto e importar espacios de nombres

Crea una nueva aplicación de consola y agrega el paquete Aspose.Words:

```bash
dotnet new console -n InsertForms2OleDemo
cd InsertForms2OleDemo
dotnet add package Aspose.Words
```

En `Program.cs` importa los espacios de nombres requeridos:

```csharp
using System;
using System.Drawing;               // for Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;        // for Forms2OleControl
```

> **Consejo profesional:** Usa la última versión de Aspose.Words para obtener soporte completo del API `Forms2OleControl`.

## Paso 2: Crear un documento en blanco e inicializar DocumentBuilder

La clase `Document` representa el archivo de Word, mientras que `DocumentBuilder` proporciona métodos para insertar contenido.

```csharp
// Step 2: Create a new blank document
Document doc = new Document();

// Initialize DocumentBuilder for the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` funciona como un cursor; después de esta línea puedes comenzar a colocar elementos en cualquier parte del documento.

## Paso 3: Definir la posición y el tamaño del botón

Word mide las coordenadas en puntos (1 pt ≈ 1/72 in). La estructura `Rectangle` de `System.Drawing` describe los límites del control.

```csharp
// Step 3: Define the button's position and size (x, y, width, height)
Rectangle buttonBounds = new Rectangle(0, 0, 100, 30); // 100 pt wide, 30 pt tall
```

* `0,0` coloca el control en la esquina superior izquierda de la página actual.
* Ajusta `x` e `y` para mover el botón a otra posición (p. ej., `new Rectangle(150, 200, 100, 30)`).

## Paso 4: Insertar el botón de comando Forms2Ole

Ahora usa `InsertForms2OleControl` para agregar el control. El método requiere el tipo de control, un nombre y los límites definidos anteriormente.

```csharp
// Step 4: Insert a Forms2Ole command button named "ClickMe"
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,   // type of control
    "ClickMe",                  // internal name (used for VBA or macros)
    buttonBounds);              // position and size
```

El objeto `Forms2OleControl` devuelto te permite modificar propiedades como `Enabled`, `Visible`, o incluso asignar un nombre de macro más adelante.

### ¿Por qué usar Forms2Ole?

* **Compatibilidad heredada** – Los controles Forms2Ole funcionan en Word 97‑2003 (`.doc`) y en archivos `.docx` más recientes.
* **Soporte de macros** – Pueden activar macros VBA, lo que los hace ideales para plantillas interactivas.
* **Posicionamiento preciso** – A diferencia de los controles de contenido, tú controlas coordenadas exactas.

## Paso 5: Guardar el documento

Finalmente, escribe el archivo en disco. Elige una carpeta a la que tengas permiso de escritura.

```csharp
// Step 5: Save the document to see the inserted button
string outputPath = @"./output.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Abre `output.docx` en Microsoft Word. Verás un botón con la etiqueta **ClickMe** en la esquina superior izquierda de la primera página. Al hacer clic en él en Word no ocurrirá nada hasta que asignes una macro, pero el control está completamente funcional.

## Manejo de casos límite comunes

| Situación | Cómo solucionarlo |
|-----------|-------------------|
| **Button appears off‑page** | Verifica que las coordenadas del `Rectangle` estén dentro de los márgenes de la página. Usa `builder.PageSetup.PageWidth` y `PageHeight` para calcular límites seguros. |
| **Control not visible in older Word versions** | Guarda el documento como `.doc` (`doc.Save("output.doc", SaveFormat.Doc)`) para garantizar la compatibilidad de Forms2Ole con Word 97‑2003. |
| **Need to change the caption** | Después de la inserción, establece `commandButton.Caption = "Submit";`. |
| **Assign a macro** | Establece `commandButton.MacroName = "MyMacro"`; la macro debe existir en el proyecto VBA del documento. |
| **Multiple buttons** | Repite el Paso 4 con diferentes valores de `Rectangle` y nombres únicos. |

## Ejemplo completo y ejecutable

Juntando todo, aquí tienes un programa autónomo que puedes copiar, pegar y ejecutar:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace InsertForms2OleDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new blank document
            Document doc = new Document();

            // Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Define button bounds (x, y, width, height) in points
            Rectangle buttonBounds = new Rectangle(0, 0, 100, 30);

            // Insert a Forms2Ole command button named "ClickMe"
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                "ClickMe",
                buttonBounds);

            // Optional: set button caption
            commandButton.Caption = "Click Me!";

            // Save the document
            string outputPath = "output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Salida esperada:** Después de ejecutar el programa, `output.docx` se abre en Word con un botón clicable etiquetado *Click Me!* ubicado en la esquina superior izquierda de la primera página.

## Conclusión

Ahora sabes cómo **insertar el control Forms2Ole en Word** usando C# y Aspose.Words. El proceso implica crear un `Document`, posicionar un `Rectangle` y llamar a `InsertForms2OleControl` mediante `DocumentBuilder`. Con el ejemplo de código completo y la guía de casos límite, puedes integrar botones de comando en cualquier flujo de trabajo automatizado de Word.

### Próximos pasos

* Explora otros valores de `ControlType` como `CheckBox` u `OptionButton`.
* Combina controles Forms2Ole con macros VBA para formularios interactivos.
* Usa `DocumentBuilder.MoveTo` para colocar botones en párrafos o tablas específicas.
* Revisa la documentación de Aspose.Words sobre **Forms2Ole** para configuraciones avanzadas de propiedades.

¡Feliz codificación y disfruta creando documentos Word más ricos con C# y Aspose.Words!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Cómo insertar un botón de comando OLE en un documento Word usando C#](/words/english/net/working-with-oleobjects-and-activex/how-to-insert-ole-command-button-in-a-word-document-using-c/)
- [Cómo agregar un control ActiveX en Word con Aspose.Words – guía paso a paso](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-control-in-word-with-aspose-words-step-by/)
- [Agregar botón de comando a documento Word con Aspose.Words – Guía completa](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}