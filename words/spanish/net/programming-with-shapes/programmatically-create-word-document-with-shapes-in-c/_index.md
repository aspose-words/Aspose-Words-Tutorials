---
category: general
date: 2026-11-22
description: Crear programáticamente un documento Word en C# e insertar una forma
  rectangular, insertar varias formas y escribir las formas en Word usando Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically create word document
- insert rectangle shape
- insert multiple shapes
- write shapes to word
language: es
lastmod: 2026-11-22
og_description: Crear programáticamente un documento Word en C# insertando una forma
  rectangular, insertando varias formas y escribiendo las formas en Word con Aspose.Words.
og_image_alt: Screenshot of a Word document showing a rectangle and an ellipse grouped
  together
og_title: Crear programáticamente un documento Word con formas en C#
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Programmatically create Word document in C# and insert rectangle shape,
    insert multiple shapes, and write shapes to Word using Aspose.Words.
  headline: Programmatically create Word document with shapes in C#
  type: TechArticle
- description: Programmatically create Word document in C# and insert rectangle shape,
    insert multiple shapes, and write shapes to Word using Aspose.Words.
  name: Programmatically create Word document with shapes in C#
  steps:
  - name: '**Initialize** a new `Document` and a `DocumentBuilder`.'
    text: '**Initialize** a new `Document` and a `DocumentBuilder`.'
  - name: '**Insert multiple shapes** (a rectangle and an ellipse) and place them
      inside a `GroupShape`.'
    text: '**Insert multiple shapes** (a rectangle and an ellipse) and place them
      inside a `GroupShape`.'
  - name: '**Write shapes to Word** by saving the `Document` to a `.docx` file.'
    text: '**Write shapes to Word** by saving the `Document` to a `.docx` file.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Crear programáticamente un documento Word con formas en C#
url: /es/net/programming-with-shapes/programmatically-create-word-document-with-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear programáticamente un documento Word con formas en C#

Si necesitas **crear programáticamente un documento Word** que contenga gráficos personalizados, esta guía te muestra cómo hacerlo con Aspose.Words para .NET. Aprenderás a insertar una forma rectangular, agregar formas adicionales, agruparlas y, finalmente, escribir las formas en Word, todo en unas pocas líneas de C#.

Crear un archivo Word con gráficos ya no requiere edición manual ni scripts de macro. Al final de este tutorial tendrás un método reutilizable que produce un archivo `.docx` que contiene un rectángulo y una elipse agrupados, listo para procesamiento posterior o generación de informes.

## Lo que necesitarás

- .NET 6.0 o posterior (el código también funciona con .NET Framework 4.6+)
- Aspose.Words para .NET (paquete NuGet `Aspose.Words`)
- Un IDE como Visual Studio 2022 (cualquier editor que pueda compilar C# sirve)

> **Consejo profesional:** Instala el paquete con el comando CLI `dotnet add package Aspose.Words` antes de comenzar a programar.

## Crear programáticamente un documento Word – visión general

El flujo general consta de tres fases lógicas:

1. **Inicializar** un nuevo `Document` y un `DocumentBuilder`.  
2. **Insertar múltiples formas** (un rectángulo y una elipse) y colocarlas dentro de un `GroupShape`.  
3. **Escribir las formas en Word** guardando el `Document` en un archivo `.docx`.

Cada fase está encapsulada en un paso dedicado a continuación, para que puedas copiar‑pegar el código directamente en tu proyecto.

![Crear programáticamente un documento Word con formas agrupadas](grouped-shapes.png){: .align-center alt="Crear programáticamente un documento Word con formas agrupadas"}

## Paso 1: Inicializar el documento y el builder

La clase `Document` representa todo el archivo Word, mientras que `DocumentBuilder` ofrece una API fluida para agregar contenido.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document document = new Document();

// Initialize a DocumentBuilder for the document
DocumentBuilder builder = new DocumentBuilder(document);
```

*Por qué es importante:* Crear primero el `Document` te brinda un lienzo limpio. El `DocumentBuilder` rastrea el punto de inserción actual, lo cual es esencial cuando luego adjuntas formas a una jerarquía de párrafos.

## Paso 2: Insertar un contenedor de forma grupal

Un `GroupShape` te permite tratar varias formas individuales como una sola unidad. Esto es útil cuando deseas moverlas o redimensionarlas juntas.

```csharp
// Insert a group shape container at the current cursor position
GroupShape groupShape = builder.InsertGroupShape();
```

*Explicación:* `InsertGroupShape` inserta un contenedor vacío y lo establece automáticamente como la forma actual. Todas las inserciones de forma posteriores se agregarán a este contenedor hasta que cierres el grupo.

## Insertar forma rectangular

Ahora añadimos el primer gráfico: un rectángulo. Esto satisface el requisito de **insertar forma rectangular**.

```csharp
// Insert a rectangle shape (width: 100 pt, height: 50 pt)
builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

El rectángulo hereda el contexto de formato del grupo, por lo que aparece dentro del `GroupShape`. También puedes establecer el color de línea, el relleno o el texto más adelante si lo necesitas.

## Insertar múltiples formas

Para demostrar la capacidad de **insertar múltiples formas**, añadimos una elipse justo después del rectángulo. Puedes seguir agregando cualquier número de formas (p. ej., triángulos, estrellas) antes de cerrar el grupo.

```csharp
// Insert an ellipse shape (width: 80 pt, height: 40 pt)
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

En este punto el grupo contiene dos formas distintas: un rectángulo y una elipse. Como comparten el mismo padre, puedes moverlas como una unidad.

## Paso 3: Adjuntar la forma grupal a la jerarquía de párrafos

Los documentos Word almacenan el contenido en un árbol de párrafos. Para que el grupo sea visible en el archivo final, debemos adjuntarlo al párrafo actual.

```csharp
// Append the group shape to the current paragraph so it becomes part of the document flow
groupShape.AppendChild(builder.CurrentParagraph);
```

*Por qué es necesario este paso:* Sin agregar el grupo a un párrafo, las formas existen solo en memoria y se omiten al guardar el documento.

## Paso 4: Guardar el documento – escribir las formas en Word

Finalmente, persistimos el `Document` en memoria en el disco. Esto cumple el objetivo de **escribir las formas en Word**.

```csharp
// Define the output path (adjust the folder as needed)
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");

// Save the document in DOCX format
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Al abrir `GroupShape.docx` en Microsoft Word, verás un rectángulo y una elipse agrupados, exactamente como el código los insertó.

### Resultado esperado

- Un archivo llamado **GroupShape.docx** ubicado en la carpeta de salida del proyecto.  
- Dentro del archivo Word: un solo párrafo que contiene un rectángulo agrupado (100 pt × 50 pt) y una elipse (80 pt × 40 pt). Seleccionar cualquiera de las formas selecciona todo el grupo.

## Manejo de casos límite comunes

| Situación | Recomendación |
|-----------|----------------|
| **DPI o tamaño de página diferentes** | Establece explícitamente `builder.PageSetup.PaperSize` antes de insertar las formas para evitar escalados inesperados. |
| **Necesidad de posicionar las formas con precisión** | Usa `builder.MoveTo` para mover el punto de inserción, luego define las propiedades `groupShape.Left` y `groupShape.Top` (los valores están en puntos). |

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Crear documento Word – Insertar forma rectangular y sombra en C#](/words/english/net/programming-with-shapes/create-word-document-insert-rectangle-shape-shadow-in-c/)
- [Crear documento Word programáticamente y agrupar formas en C#](/words/english/net/programming-with-shapes/create-word-document-programmatically-and-group-shapes-in-c/)
- [Crear programáticamente un documento Word con una forma grupal](/words/english/net/programming-with-shapes/programmatically-create-a-word-document-with-a-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}