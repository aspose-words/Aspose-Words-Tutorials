---
category: general
date: 2026-09-27
description: Crear programáticamente un documento Word con una forma de grupo usando
  Aspose.Words en C#. Sigue esta guía paso a paso para generar el archivo y aprender
  consejos útiles.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically create word document
- how to create group shape word
- Aspose.Words group shape
- C# Word automation
- StructuredDocumentTag example
language: es
lastmod: 2026-09-27
og_description: Crear programáticamente un documento Word con una forma de grupo usando
  Aspose.Words. Este tutorial te guía a través del código completo en C#, explica
  cada paso y muestra el resultado final.
og_image_alt: Screenshot of a Word document containing a group shape with a text placeholder
og_title: Crear programáticamente un documento Word con un grupo de formas – Guía
  de C#
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Programmatically create a Word document with a group shape using Aspose.Words
    in C#. Follow this step‑by‑step guide to generate the file and learn useful tips.
  headline: Programmatically create a Word document with a group shape
  type: TechArticle
- description: Programmatically create a Word document with a group shape using Aspose.Words
    in C#. Follow this step‑by‑step guide to generate the file and learn useful tips.
  name: Programmatically create a Word document with a group shape
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code also works with .NET Framework 4.7+). - Aspose.Words
      for .NET NuGet package (`Install-Package Aspose.Words`). - A C# IDE such as
      Visual Studio 2022 or VS Code with the C# extension.'
  - name: Expected output screenshot (conceptual)
    text: '``` +-----------------------------------------------------------+ | ┌───────────────────────────────────────────────┐
      | | │ [Enter text here] │ | | └───────────────────────────────────────────────┘
      | +-----------------------------------------------------------+ ```'
  - name: Adding more child shapes
    text: 'You can enrich the group by appending additional drawing objects, such
      as pictures or text boxes:'
  - name: Controlling wrapping style
    text: 'If you need the group shape to stay behind text or to have tight wrapping,
      set the `WrapType` property:'
  - name: 'Edge case: Empty group shape'
    text: A `GroupShape` without children renders as an invisible placeholder. Always
      verify that at least one child (e.g., an SDT or a picture) is added; otherwise
      Word may drop the group during saving.
  - name: Compatibility note
    text: Aspose.Words 23.10+ fully supports `GroupShape` and `StructuredDocumentTag`.
      If you target older versions, the `AppendChild` method may behave differently,
      and you might need to call `UpdatePageLayout` after saving.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Crear programáticamente un documento de Word con un grupo de formas
url: /es/net/programming-with-shapes/programmatically-create-a-word-document-with-a-group-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear programáticamente un documento Word con una forma de grupo

Si necesita **crear programáticamente un documento Word** que contenga un dibujo agrupado, esta guía le muestra exactamente cómo hacerlo con Aspose.Words for .NET. Ya sea que esté construyendo un generador de contratos, un creador de informes o una herramienta de llenado de formularios, aprenderá el código C# completo, por qué cada llamada a la API es importante y cómo manejar casos límite comunes.

Crear una forma agrupada en Word puede resultar complicado porque el modelo de objetos de Word trata las formas de grupo como contenedores de otros objetos de dibujo. Este tutorial no solo responde a **cómo crear documentos Word con forma de grupo**, sino que también muestra cómo incrustar un StructuredDocumentTag (SDT) de texto sin formato dentro del grupo para que la forma pueda contener contenido editable.

## Lo que lograrás

- Inicializar un nuevo documento Word en blanco con `Document` y `DocumentBuilder`.
- Insertar un `GroupShape` en la posición actual del cursor.
- Añadir un `StructuredDocumentTag` (SDT) de texto sin formato al shape de grupo.
- Guardar el archivo como `.docx` que pueda abrirse en Microsoft Word.
- Comprender las propiedades clave de `GroupShape` y `StructuredDocumentTag` para futuras extensiones.

### Requisitos previos

- .NET 6.0 o posterior (el código también funciona con .NET Framework 4.7+).
- Paquete NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`).
- Un IDE de C# como Visual Studio 2022 o VS Code con la extensión C#.

---

## Crear programáticamente un documento Word – configurar el proyecto

1. **Crear un nuevo proyecto de consola**  
   ```bash
   dotnet new console -n WordGroupShapeDemo
   cd WordGroupShapeDemo
   dotnet add package Aspose.Words
   ```
2. **Abrir el proyecto en su IDE** y reemplazar el contenido de `Program.cs` con el código mostrado en las siguientes secciones.

> **Consejo profesional:** Mantenga la carpeta del proyecto limpia; Aspose.Words escribe el archivo de salida en el directorio de trabajo a menos que proporcione una ruta absoluta.

## Paso 1: Inicializar el documento y el builder

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;

// Create a new blank document.
Document doc = new Document();

// DocumentBuilder gives you a cursor to insert nodes.
DocumentBuilder builder = new DocumentBuilder(doc);

// Optional: set the page size or margins if your shape must fit a specific area.
builder.PageSetup.PageWidth = 595;   // A4 width in points
builder.PageSetup.PageHeight = 842;  // A4 height in points
```

**Por qué es importante:**  
`Document` representa todo el archivo Word, mientras que `DocumentBuilder` le permite posicionar nuevos elementos sin navegar manualmente por el árbol de nodos. Establecer las dimensiones de la página al principio garantiza que la forma de grupo no desborde la página.

## Paso 2: Insertar un GroupShape en la posición actual del cursor

```csharp
// Create an empty GroupShape container.
GroupShape groupShape = new GroupShape(doc)
{
    // Give the group a size that comfortably holds its children.
    Width = 300,
    Height = 150,

    // Position the group relative to the page (you can also use RelativeHorizontalPosition).
    Left = 100,
    Top = 100
};

// Insert the group shape into the document where the builder is currently positioned.
builder.InsertNode(groupShape);
```

**Explicación:**  
Un `GroupShape` es un objeto de dibujo que puede contener otras formas, imágenes o cuadros de texto. Al establecer `Width`, `Height`, `Left` y `Top`, controla su ubicación exacta en la página. El método `InsertNode` coloca la forma en el flujo principal del documento, comportándose como un objeto flotante.

## Paso 3: Añadir un StructuredDocumentTag (SDT) de texto sin formato dentro del grupo

```csharp
// Create a plain‑text SDT that will act as a content placeholder.
StructuredDocumentTag sdtTag = new StructuredDocumentTag(doc, SdtType.PlainText, true)
{
    // Provide a helpful tag title that appears as a tooltip in Word.
    Title = "GroupShapeText",
    // Set default placeholder text.
    PlaceholderName = "Enter text here"
};

// Append the SDT to the group shape's child collection.
groupShape.AppendChild(sdtTag);
```

**¿Por qué usar un SDT?**  
Los StructuredDocumentTags son los controles de contenido nativos de Word. Permiten a los usuarios editar el texto directamente en el documento guardado, y pueden ser accedidos programáticamente más tarde para la extracción de datos. Colocar un SDT dentro de una forma de grupo le permite combinar agrupación visual con contenido editable.

## Paso 4: Guardar el documento

```csharp
// Define the output path – replace with your desired directory.
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShapeDemo.docx");

// Save the document in DOCX format.
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Document saved to: {outputPath}");
```

**Resultado:**  
Al abrir `GroupShapeDemo.docx` en Microsoft Word se muestra un rectángulo flotante (la forma de grupo) que contiene un marcador de posición de texto que dice “Enter text here”. Los usuarios pueden hacer clic dentro de la forma y escribir directamente.

### Captura de pantalla del resultado esperado (conceptual)

```
+-----------------------------------------------------------+
|   ┌───────────────────────────────────────────────┐   |
|   │  [Enter text here]                               │   |
|   └───────────────────────────────────────────────┘   |
+-----------------------------------------------------------+
```

El cuadro externo es el `GroupShape`; el área gris interna es el `StructuredDocumentTag`.

---

## Cómo crear documentos Word con forma de grupo – consideraciones adicionales

### Añadir más formas hijas

Puedes enriquecer el grupo añadiendo objetos de dibujo adicionales, como imágenes o cuadros de texto:

```csharp
// Example: add a picture inside the same group.
Shape picture = new Shape(doc, ShapeType.Image)
{
    ImageData = ImageData.FromFile("logo.png"),
    Width = 100,
    Height = 50,
    Left = 10,
    Top = 80
};
groupShape.AppendChild(picture);
```

### Controlar el estilo de ajuste

Si necesitas que la forma de grupo quede detrás del texto o tenga un ajuste estrecho, establece la propiedad `WrapType`:

```csharp
groupShape.WrapType = WrapType.Inline; // Makes the shape behave like a paragraph.
```

### Caso límite: Forma de grupo vacía

Un `GroupShape` sin hijos se renderiza como un marcador de posición invisible. Siempre verifica que se añada al menos un hijo (por ejemplo, un SDT o una imagen); de lo contrario Word puede eliminar el grupo al guardar.

### Nota de compatibilidad

Aspose.Words 23.10+ soporta completamente `GroupShape` y `StructuredDocumentTag`. Si apuntas a versiones anteriores, el método `AppendChild` puede comportarse de manera diferente, y podrías necesitar llamar a `UpdatePageLayout` después de guardar.

---

## Ejemplo completo ejecutable

Los siguientes fragmentos se deben copiar en `Program.cs` y ejecutar el proyecto. El código incluye todos los pasos anteriores en un programa único y autocontenido.



## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarle a dominar características adicionales de la API y explorar enfoques de implementación alternativos en sus propios proyectos.

- [Crear forma de grupo en documento Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Crear forma rectangular en Word usando C# – Guía paso a paso](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Crear documento Word en blanco con Aspose.Words – Guía paso a paso](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}