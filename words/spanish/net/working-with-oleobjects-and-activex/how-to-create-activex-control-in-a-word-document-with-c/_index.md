---
category: general
date: 2026-09-14
description: Crear un control ActiveX en un documento de Word con C#. Aprende cómo
  insertar ActiveX, añadir un botón interactivo y generar el archivo .docx de forma
  programática.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex control
- how to insert activex
- add interactive button
- create word document
- create button with code
language: es
lastmod: 2026-09-14
og_description: Crea un control ActiveX en un documento de Word con C#. Sigue este
  ejemplo completo para insertar ActiveX, añadir un botón interactivo y guardar el
  archivo.
og_image_alt: Screenshot of a Word document containing a newly created ActiveX CommandButton
og_title: Crear control ActiveX en Word usando C# – guía paso a paso
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Create ActiveX control in a Word document with C#. Learn how to insert
    ActiveX, add interactive button, and generate the .docx file programmatically.
  headline: How to create ActiveX control in a Word document with C#
  type: TechArticle
tags:
- ActiveX
- C#
- Word automation
title: Cómo crear un control ActiveX en un documento de Word con C#
url: /es/net/working-with-oleobjects-and-activex/how-to-create-activex-control-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo crear un control ActiveX en un documento Word con C#

Si necesitas **crear un control ActiveX** dentro de un archivo Microsoft Word, esta guía te muestra una solución completa y lista‑para‑ejecutar. Verás exactamente cómo insertar un ActiveX CommandButton, establecer sus propiedades y guardar el archivo `.docx` resultante usando solo código C#.

Agregar un botón interactivo a un documento Word es un requisito común cuando deseas que los usuarios finales activen macros o lógica personalizada directamente desde la interfaz del documento. El ejemplo a continuación demuestra **cómo insertar ActiveX** sin depender de herramientas de terceros, y también cubre **cómo crear un documento Word** programáticamente.

Al final de este tutorial podrás **crear un botón con código**, personalizar su título y generar un archivo Word portátil que preserve el control ActiveX.

## Requisitos previos

- .NET 6.0 o posterior (la biblioteca Aspose.Words for .NET funciona con .NET Core y .NET Framework)
- Una referencia al paquete NuGet `Aspose.Words`  
  ```bash
  dotnet add package Aspose.Words
  ```
- Conocimientos básicos de C# y programación orientada a objetos

## Paso 1: Configurar el proyecto e importar espacios de nombres

Crea un nuevo proyecto de consola (o integra el código en cualquier aplicación C# existente). Importa los espacios de nombres requeridos para que el compilador pueda localizar las clases de procesamiento de Word.

```csharp
using System;
using System.Drawing;               // Provides RectangleF
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
```

> **Por qué este paso es importante** – La API `Aspose.Words` proporciona las clases `Document`, `DocumentBuilder` y `Forms2OleControl` que te permiten manipular archivos Word a nivel de objeto. Sin estas referencias el resto del código no compilaría.

## Paso 2: Crear un nuevo documento Word y un DocumentBuilder

El objeto `Document` representa todo el paquete `.docx`, mientras que `DocumentBuilder` ofrece una API fluida para insertar contenido.

```csharp
// Step 2: Initialize a fresh Word document
Document document = new Document();

// Attach a builder to the document – the builder knows where to write next
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Explicación** – Instanciar un `Document` nuevo te brinda un lienzo limpio. El cursor del builder comienza al inicio de la primera sección, listo para la siguiente inserción.

## Paso 3: Insertar el ActiveX CommandButton

Usa `InsertForms2OleControl` para colocar un control ActiveX en una ubicación específica. El método requiere el tipo de control y un `RectangleF` que define las coordenadas X/Y y el tamaño (en puntos).

```csharp
// Step 3: Add an ActiveX CommandButton at (100,100) with width 120 and height 30
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,
    new RectangleF(100, 100, 120, 30));
```

> **Por qué funciona** – `OleControlType.CommandButton` indica a la API que cree un CommandButton estándar de Windows. El rectángulo posiciona el botón relativo a la esquina superior‑izquierda de la página, permitiéndote **agregar un botón interactivo** exactamente donde lo necesitas.

## Paso 4: Configurar las propiedades del botón

Ahora establece el texto visible del botón (`Caption`) y su nombre interno (`Name`). Estas propiedades son lo que los usuarios ven y lo que el código VBA puede referenciar más adelante.

```csharp
// Step 4: Define the button’s caption and programmatic name
commandButton.Caption = "Click Me";
commandButton.Name = "btnClick";
```

> **Consejo práctico** – El `Name` debe ser único dentro del documento; de lo contrario, las macros VBA pueden referenciar el control incorrecto.

## Paso 5: Guardar el documento

Finalmente, escribe el archivo en disco. El control ActiveX se almacena dentro del paquete Word, por lo que el archivo guardado conservará toda la funcionalidad al abrirse en Microsoft Word.

```csharp
// Step 5: Persist the document – the ActiveX control stays embedded
string outputPath = @"C:\Temp\CommandButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

> **Resultado** – Al abrir `CommandButton.docx` en Word se muestra un CommandButton clicable con la etiqueta “Click Me”. El control puede enlazarse a una macro mediante la interfaz de Word (`Developer → Design Mode → Properties`).

## Listado completo del código fuente

Unir todos los pasos produce un programa único y autónomo que puedes copiar, pegar y ejecutar.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Create a new document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert an ActiveX CommandButton at the desired location
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new RectangleF(100, 100, 120, 30));

        // Set the button's caption and internal name
        commandButton.Caption = "Click Me";
        commandButton.Name = "btnClick";

        // Save the document – the control is preserved
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### Salida esperada

Ejecutar el programa imprime una línea de confirmación:

```
Document saved to C:\Temp\CommandButton.docx
```

Al abrir el archivo generado en Microsoft Word, verás un **CommandButton** colocado en las coordenadas especificadas. Al hacer clic en el botón en modo de diseño se resalta; en modo de ejecución se comporta como cualquier botón ActiveX estándar.

## Variaciones comunes y casos límite

| Escenario | Ajuste |
|----------|------------|
| **Different control type** | Reemplaza `OleControlType.CommandButton` por `OleControlType.CheckBox`, `OleControlType.OptionButton`, etc. |
| **Multiple buttons** | Llama a `InsertForms2OleControl` repetidamente, actualizando las coordenadas `RectangleF` para cada nuevo botón. |
| **Dynamic sizing** | Calcula las dimensiones del rectángulo basándote en el tamaño de página (`builder.PageSetup.PageWidth`). |
| **Saving to a stream** | Usa `document.Save(stream, SaveFormat.Docx)` cuando necesites devolver el archivo desde una API web. |
| **Word 97‑2003 format** | Cambia el formato de guardado a `SaveFormat.Doc` para producir un archivo `.doc` que aún incruste el control ActiveX. |

> **Consejo profesional:** Siempre prueba el documento generado en la versión objetivo de Word, ya que las versiones más antiguas pueden aplicar configuraciones de seguridad que deshabilitan los controles ActiveX por defecto.

## Preguntas frecuentes

**¿Funciona esto con .NET Core?**  
Sí. La biblioteca Aspose.Words es multiplataforma y totalmente compatible con .NET Core y .NET 5/6+.

**¿Puedo asignar una macro al botón programáticamente?**  
La API no incrusta código VBA directamente. Después de generar el documento, ábrelo en Word, habilita la pestaña Developer y graba o escribe una macro que haga referencia a `btnClick`.

**¿Qué pasa si el botón no aparece?**  
Verifica que la pestaña `Developer` esté habilitada en Word y que el documento no se abra en **Protected View**. También confirma que las coordenadas del rectángulo estén dentro de los márgenes de la página.

## Conclusión

Ahora sabes cómo **crear un control ActiveX** dentro de un archivo Word usando C#. El tutorial cubrió **cómo insertar ActiveX**, demostró **agregar un botón interactivo**, mostró **cómo crear un documento Word** desde cero, e ilustró **cómo crear un botón con código** que persiste después de guardar.  

A partir de aquí puedes explorar tipos adicionales de ActiveX, conectar el botón a macros VBA, o incrustar la lógica en un servicio más amplio de generación de documentos. Experimenta con diferentes tamaños, posiciones y propiedades de control para adaptar la experiencia de usuario que necesitas.

---

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Crear nuevo documento Word](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Crear proyecto VBA en documento Word](/words/english/net/working-with-vba-macros/create-vba-project/)
- [Crear y dar estilo a un documento Word en Aspose.Words para .NET](/words/english/net/document-styling/apply-paragraph-style/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}