---
category: general
date: 2026-10-13
description: Aprenda cómo agregar un botón de comando programáticamente usando Aspose.Words.
  Esta guía también muestra cómo crear un botón en un documento Word con código C#
  completo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add command button programmatically
- create word document button
language: es
lastmod: 2026-10-13
og_description: Agrega un botón de comando programáticamente a un documento de Word
  usando Aspose.Words. Sigue este tutorial completo para crear un botón en un documento
  de Word con C#.
og_image_alt: Screenshot of a Word document with a command button inserted programmatically
og_title: Agregar un botón de comando programáticamente a un documento de Word – guía
  paso a paso
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to add a command button programmatically using Aspose.Words.
    This guide also shows how to create a Word document button with full C# code.
  headline: How to add a command button programmatically in a Word document
  type: TechArticle
- description: Learn how to add a command button programmatically using Aspose.Words.
    This guide also shows how to create a Word document button with full C# code.
  name: How to add a command button programmatically in a Word document
  steps:
  - name: 'Create a new console project:'
    text: 'Create a new console project:'
  - name: 'Add the Aspose.Words NuGet package:'
    text: 'Add the Aspose.Words NuGet package:'
  - name: Open **Program.cs** and replace its content with the scaffold shown in the
      next steps.
    text: Open **Program.cs** and replace its content with the scaffold shown in the
      next steps.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Cómo agregar un botón de comando programáticamente en un documento de Word
url: /es/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo agregar un botón de comando programáticamente en un documento Word  

Si necesita **agregar un botón de comando programáticamente**, Aspose.Words ofrece una API limpia que le permite incrustar controles de formulario OLE directamente en un archivo .docx. Este tutorial le guía a través de cada paso necesario para **crear un botón en un documento Word** que se comporte como un botón de formulario normal cuando el documento se abre en Microsoft Word.  

Aprenderá cómo configurar el entorno de desarrollo, insertar el botón, configurar sus propiedades y verificar el resultado. No se requieren utilidades externas, solo un proyecto .NET y la biblioteca Aspose.Words for .NET.  

## Requisitos previos  

Antes de comenzar, asegúrese de tener:  

* SDK .NET 6.0 o posterior instalado.  
* Una versión reciente de Aspose.Words for .NET (los ejemplos usan 23.12, pero cualquier versión 22.x+ funciona).  
* Un IDE como Visual Studio 2022 o Visual Studio Code.  

El código se ejecuta en Windows, macOS y Linux porque Aspose.Words es independiente de la plataforma.  

## Paso 1: Configurar el proyecto y referenciar Aspose.Words  

1. Cree un nuevo proyecto de consola:  

   ```bash
   dotnet new console -n WordButtonDemo
   cd WordButtonDemo
   ```  

2. Agregue el paquete NuGet Aspose.Words:  

   ```bash
   dotnet add package Aspose.Words
   ```  

3. Abra **Program.cs** y reemplace su contenido con la estructura mostrada en los siguientes pasos.  

Configurar el proyecto de esta manera garantiza que el compilador pueda localizar los espacios de nombres `Aspose.Words` y `Aspose.Words.Drawing.Forms` requeridos para los controles de formulario.  

## Paso 2: Inicializar un documento en blanco y un DocumentBuilder  

La clase `Document` representa todo el archivo Word, mientras que `DocumentBuilder` ofrece una API fluida para agregar contenido.  

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Forms;
using System.Drawing;   // required for RectangleF

// Create an empty document.
Document doc = new Document();

// Create a builder linked to the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```  

*Por qué este paso es importante* – Sin un `DocumentBuilder` no puede posicionar el botón con precisión en la página. El builder también respeta la ubicación actual del cursor, lo que facilita la inserción de múltiples controles más adelante.  

## Paso 3: Insertar el control OLE del botón de comando  

Aspose.Words trata un botón de comando como un control OLE de tipo `ControlType.CommandButton`. Define su ubicación y tamaño con un `RectangleF` medido en puntos (1 punto = 1/72 de pulgada).  

```csharp
// Define the button rectangle: X=100, Y=150, Width=120, Height=30 (points)
RectangleF buttonRect = new RectangleF(100, 150, 120, 30);

// Insert the command button at the current cursor position.
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,
    buttonRect);
```  

**Puntos clave**  

* El origen del rectángulo (X, Y) es relativo a la esquina superior izquierda de la página.  
* Cambiar el `Width` o `Height` modifica el tamaño visual del botón.  
* `InsertForms2OleControl` devuelve un objeto `Forms2OleControl` que puede configurar adicionalmente.  

## Paso 4: Configurar el nombre y el texto del botón  

El **name** es usado por el motor de macros de Word para identificar el control, mientras que el **caption** es el texto que ve el usuario.  

```csharp
// Set a unique identifier for the button.
commandButton.Name = "cmdSubmit";

// Set the text displayed on the button.
commandButton.Caption = "Submit";
```  

Si planea agregar macros VBA más adelante, use un nombre descriptivo porque el grabador de macros de Word hace referencia a esta propiedad.  

## Paso 5: (Opcional) Guardar el documento y verificar el resultado  

Guardar el archivo le permite abrirlo en Microsoft Word para confirmar que el botón aparece y funciona.  

```csharp
// Save the document to the output folder.
string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButtonDemo.docx");
doc.Save(outputPath);

Console.WriteLine($"Document saved to: {outputPath}");
```  

Al abrir *CommandButtonDemo.docx* en Word, debería ver un botón etiquetado **Submit** ubicado aproximadamente a 1.4 pulgadas del margen izquierdo y 2.1 pulgadas de la parte superior de la página. Hacer clic en el botón no hace nada por defecto porque no hay ninguna macro adjunta, pero el control visual es completamente funcional.  

## Paso 6: Casos límite y errores comunes  

| Situación | Qué observar | Solución recomendada |
|-----------|--------------|----------------------|
| **El botón se superpone al texto existente** | El rectángulo puede intersectar con un párrafo, provocando problemas de diseño. | Inserte el botón después de llamar a `builder.Writeln()` para mover el cursor a una nueva línea, o ajuste la coordenada `Y`. |
| **El documento se abre con una advertencia** | Algunas versiones de Word marcan los controles OLE que no tienen un programa vinculado. | Asegúrese de que el tipo de control sea `CommandButton`; Word lo trata como un elemento de formulario estándar y no requiere un programa externo. |
| **Ejecutando en Linux con entorno sin interfaz** | Word no puede iniciarse para probar la UI, pero el archivo sigue siendo válido. | Utilice una prueba unitaria que lea las propiedades del control (`commandButton.Name`, `commandButton.Caption`) para verificar que se establecieron correctamente. |
| **Se necesitan varios botones** | Reutilizar el mismo `DocumentBuilder` sin mover el cursor agrega el botón encima del anterior. | Llame a `builder.MoveToDocumentEnd()` o ajuste el valor `Y` del rectángulo antes de cada inserción. |

Abordar estos casos límite temprano ahorra tiempo al escalar la solución a formularios completos con docenas de controles.  

## Paso 7: Ejemplo completo y ejecutable  

A continuación se muestra un programa autónomo que puede copiar, pegar y ejecutar sin modificaciones (excepto la restauración de NuGet).  

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

namespace WordButtonDemo
{
    class Program
    {
        static void Main()
        {
            // 1. Create a new empty document.
            Document doc = new Document();

            // 2. Create a DocumentBuilder to work with the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3. Define the button rectangle (position + size).
            RectangleF buttonRect = new RectangleF(100, 150, 120, 30);

            // 4. Insert the command button OLE control.
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                buttonRect);

            // 5. Set identifying properties.
            commandButton.Name = "cmdSubmit";
            commandButton.Caption = "Submit";

            // 6. Save the document.
            string outputPath = Path.Combine(
                Environment.CurrentDirectory,
                "CommandButtonDemo.docx");
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

**Salida esperada**  

Ejecutar el programa imprime una ruta similar a:  

```
Document saved to: C:\Path\To\WordButtonDemo\CommandButtonDemo.docx
```  

Abrir el *CommandButtonDemo.docx* generado muestra un único botón **Submit** colocado en las coordenadas definidas en el código. No aparecen elementos UI adicionales, confirmando que el flujo de trabajo **add command button programmatically** se completó con éxito.  

## Conclusión  

Ahora sabe cómo **add a command button programmatically** a un documento Word usando Aspose.Words, y también comprende cómo **create a Word document button** que luego puede conectarse a macros VBA o herramientas de automatización externas. El proceso consiste en inicializar un documento, insertar un control OLE `CommandButton`, configurar sus propiedades y guardar el archivo.  

A partir de aquí podría:  

* Agregar más controles (casillas de verificación, campos de texto) repitiendo el paso 3 con diferentes valores de `ControlType`.  
* Adjuntar macros VBA al botón para realizar acciones como guardar un formulario o enviar un correo electrónico.  
* Generar formularios completos dinámicamente iterando sobre una colección de definiciones de campos basada en datos.  

Experimente con las coordenadas del rectángulo y el texto del botón para que coincidan con el diseño de su UI. ¡Feliz codificación!  

## ¿Qué debería aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarle a dominar características adicionales de la API y explorar enfoques de implementación alternativos en sus propios proyectos.

- [Agregar un campo de formulario Combo Box a un documento Word con Aspose.Words para .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Agregar un campo de formulario Check Box a un documento Word con Aspose.Words para .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)
- [Crear un documento Word en blanco con Aspose.Words – Guía paso a paso](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}