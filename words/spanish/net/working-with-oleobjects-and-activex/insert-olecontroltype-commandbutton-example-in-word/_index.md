---
category: general
date: 2026-08-17
description: Inserte un ejemplo de OleControlType.CommandButton en Word usando Aspose.Words.
  Aprenda cómo agregar controles de formulario a un documento de Word de forma programática.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert olecontroltype.commandbutton example
- how to add form controls to word document
- Aspose.Words ActiveX button
- C# Word automation
- programmatic form controls
language: es
lastmod: 2026-08-17
og_description: Inserte un ejemplo de OleControlType.CommandButton en Word con Aspose.Words.
  Siga esta guía para agregar controles de formulario a un documento de Word.
og_image_alt: Screenshot showing an ActiveX CommandButton inserted into a Word document
  using Aspose.Words
og_title: Insertar ejemplo de OleControlType.CommandButton en Word
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: Insert OleControlType.CommandButton example in Word using Aspose.Words.
    Learn how to add form controls to a Word document programmatically.
  headline: Insert OleControlType.CommandButton example in Word
  type: TechArticle
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Insertar ejemplo de OleControlType.CommandButton en Word
url: /es/net/working-with-oleobjects-and-activex/insert-olecontroltype-commandbutton-example-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Insertar ejemplo de OleControlType.CommandButton en Word

Si necesita **insert OleControlType.CommandButton example** en un archivo Word, esta guía le muestra cómo. Aprenderá **cómo agregar controles de formulario a un documento Word** usando Aspose.Words, con un programa C# completo y ejecutable.

Los controles de formulario, como los botones ActiveX, le permiten crear plantillas de Word interactivas, útiles para contratos, cuestionarios o herramientas internas. Los pasos a continuación cubren todo, desde la configuración del proyecto hasta la verificación de que el botón aparezca correctamente en el archivo `.docx` guardado.

## Requisitos previos

- .NET 6.0 SDK o posterior instalado  
- Visual Studio 2022 (o cualquier IDE de C#)  
- Una licencia de Aspose.Words para .NET o una licencia temporal gratuita  
- Familiaridad básica con C# y conceptos de archivos Word  

> **Consejo profesional:** Si está usando la versión de prueba gratuita, coloque el archivo de licencia en la misma carpeta que el ejecutable y cárguelo al inicio de `Main`.

## Paso 1: Crear un nuevo proyecto de consola y agregar Aspose.Words

Abra una terminal y ejecute:

```bash
dotnet new console -n OleCommandButtonDemo
cd OleCommandButtonDemo
dotnet add package Aspose.Words
```

Esto crea un proyecto limpio y descarga el paquete más reciente de Aspose.Words, que proporciona las APIs `Document`, `DocumentBuilder` y `InsertForms2OleControl` necesarias para el **insert OleControlType.CommandButton example**.

## Paso 2: Escribir el programa completo

Cree o reemplace `Program.cs` con el siguiente código. Contiene todas las directivas `using` requeridas, la carga de la licencia y el flujo de trabajo de cuatro pasos mostrado en el fragmento original.

```csharp
using System;
using System.Drawing;               // For Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;          // For OleControlType

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // Optional: load a trial or commercial license.
        // -------------------------------------------------
        // var license = new Aspose.Words.License();
        // license.SetLicense("Aspose.Words.lic");

        // -------------------------------------------------
        // Step 1: Create a new blank document
        // -------------------------------------------------
        Document doc = new Document();

        // -------------------------------------------------
        // Step 2: Initialize a DocumentBuilder to work with the document
        // -------------------------------------------------
        DocumentBuilder builder = new DocumentBuilder(doc);

        // -------------------------------------------------
        // Step 3: Insert an ActiveX CommandButton control
        // -------------------------------------------------
        // OleControlType.CommandButton creates a CommandButton.
        // "ClickMe" is the control's name.
        // The Rectangle defines the button's position (x, y) and size (width, height).
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            "ClickMe",
            new Rectangle(100, 100, 80, 30));

        // -------------------------------------------------
        // Step 4: Save the document containing the ActiveX button
        // -------------------------------------------------
        string outputPath = "ActiveXButton.docx";
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### Por qué cada línea es importante

* **License loading** – garantiza que no esté limitado por restricciones de evaluación.  
* **`Document doc = new Document();`** – crea el contenedor para todo el contenido de Word; esta es la base del **insert OleControlType.CommandButton example**.  
* **`DocumentBuilder builder = new DocumentBuilder(doc);`** – proporciona una API fluida para agregar texto, imágenes y controles.  
* **`InsertForms2OleControl`** – el método principal que implementa **cómo agregar controles de formulario a un documento Word**. El valor de enumeración `OleControlType.CommandButton` indica a Aspose.Words que cree un botón ActiveX.  
* **`new Rectangle(100, 100, 80, 30)`** – posiciona el botón a 100 pts de los márgenes izquierdo y superior, con un ancho de 80 pts y una altura de 30 pts. Ajuste estos números para que se adapten a su diseño.  
* **`doc.Save`** – escribe el archivo .docx en el disco; el archivo ahora contiene el botón incrustado.

## Paso 3: Compilar y ejecutar el programa

Desde la carpeta del proyecto, ejecute:

```bash
dotnet run
```

Debería ver el mensaje en la consola:

```
Document saved to ActiveXButton.docx
```

Abra `ActiveXButton.docx` en Microsoft Word. Verá un botón etiquetado **ClickMe** posicionado aproximadamente en el centro de la página. Al hacer clic en el botón se activa el comportamiento predeterminado de ActiveX (que normalmente no hace nada a menos que adjunte una macro).

![ejemplo de insert olecontroltype.commandbutton](/images/activex-button.png "CommandButton ActiveX insertado en un documento Word")

*Texto alternativo de la imagen:* ejemplo de insert olecontroltype.commandbutton – un CommandButton ActiveX mostrado en un documento Word.

## Paso 4: Personalizar el botón (opcional)

El **insert OleControlType.CommandButton example** básico crea un botón predeterminado. Puede modificar su título, fuente o incluso adjuntar una macro editando el objeto OLE subyacente. A continuación se muestra una forma concisa de cambiar el título del botón después de la inserción:

```csharp
// Retrieve the first shape (our button) from the document
Shape buttonShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

// Access the OLE format and set the caption
buttonShape.OleFormat.GetControl().SetProperty("Caption", "Submit");
```

> **Nota:** La manipulación directa de propiedades OLE requiere comprender la interfaz COM subyacente. Para la mayoría de los escenarios, el título predeterminado es suficiente.

## Paso 5: Problemas comunes y cómo evitarlos

| Problema | Por qué ocurre | Solución |
|----------|----------------|----------|
| El botón no aparece en Word | El documento se guardó como `.docx` pero se abrió en un visor que elimina los controles OLE (p.ej., Google Docs). | Abra el archivo en Microsoft Word o Word Online con permisos de edición. |
| Error de tiempo de ejecución `ArgumentOutOfRangeException` | Las coordenadas del `Rectangle` están fuera de los márgenes de la página. | Utilice valores dentro del tamaño de página (p.ej., 0‑500 para A4). |
| Excepción de licencia | Una licencia de prueba expira después de 30 días. | Cargue un archivo de licencia válido o solicite una prueba extendida a Aspose. |

## Paso 6: Cómo este ejemplo encaja en proyectos de automatización más grandes

Cuando necesite **cómo agregar controles de formulario a un documento Word** a gran escala —por ejemplo, generar cientos de plantillas de contrato— envuelva la lógica de inserción en un método reutilizable:

```csharp
static void AddCommandButton(DocumentBuilder builder, string name, Rectangle bounds)
{
    builder.InsertForms2OleControl(OleControlType.CommandButton, name, bounds);
}
```

Luego puede llamar a `AddCommandButton` dentro de bucles que procesen filas de datos, asegurando que cada documento generado contenga un botón con un nombre único (p.ej., `Approve_001`, `Approve_002`).

## Conclusión

Ahora tiene un **insert OleControlType.CommandButton example** completo que demuestra **cómo agregar controles de formulario a un documento Word** usando Aspose.Words para .NET. El tutorial cubrió la configuración del proyecto, el código fuente completo, consejos de personalización y pasos comunes de solución de problemas.

Desde aquí podría explorar:

- Agregar otros tipos de control como **CheckBox** o **ComboBox** (`OleControlType.CheckBox`, `OleControlType.ComboBox`).  
- Vincular el botón a una macro VBA para una interactividad más rica.  
- Generar PDFs del mismo documento preservando los campos de formulario.

¡Experimente con diferentes tamaños, posiciones y nombres de control para adaptarlos a su caso de uso específico! ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarle a dominar características adicionales de la API y explorar enfoques de implementación alternativos en sus propios proyectos.

- [Insertar campo de formulario Combo Box en documento Word](/words/english/net/add-content-using-documentbuilder/insert-combo-box-form-field/)
- [Insertar campo de formulario Check Box en documento Word](/words/english/net/add-content-using-documentbuilder/insert-check-box-form-field/)
- [Insertar campo de formulario de entrada de texto en documento Word](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}