---
category: general
date: 2026-10-23
description: Cree un documento Word en blanco, añada una forma rectangular y oculte
  la forma en Word usando Aspose.Words. Código paso a paso para desarrolladores .NET.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- how to insert shape
- hide shape word
language: es
lastmod: 2026-10-23
og_description: Crea un documento Word en blanco, agrega una forma rectangular y oculta
  la forma en Word con Aspose.Words. Sigue el ejemplo completo en C#.
og_image_alt: Screenshot of a Word document containing a hidden rectangle shape
og_title: Crear un documento de Word en blanco y añadir una forma rectangular oculta
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Create a blank Word document, add a rectangle shape, and hide the shape
    in Word using Aspose.Words. Step‑by‑step code for .NET developers.
  headline: Create a blank Word document and add a rectangle shape
  type: TechArticle
tags:
- Aspose.Words
- .NET
- Word automation
title: Crear un documento de Word en blanco y añadir una forma de rectángulo
url: /es/java/images-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear un documento Word en blanco y agregar una forma rectangular

Si necesitas **crear un documento Word en blanco**, esta guía te muestra cómo hacerlo con Aspose.Words for .NET. También aprenderás **cómo insertar una forma**—específicamente un rectángulo—y **ocultar la forma en Word** para que no afecte el diseño.

El tutorial recorre cada línea de código, explica por qué cada paso es importante y cubre problemas comunes como la visibilidad de formas ocultas en diferentes modos de vista de Word. Al final tendrás un archivo `.docx` totalmente funcional que contiene una forma rectangular oculta que podrás revelar o manipular programáticamente.

## Requisitos previos

- .NET 6.0 o posterior (el código también funciona con .NET Framework 4.6+)
- Paquete NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)
- Un entorno de desarrollo como Visual Studio 2022 o VS Code con extensiones de C#
- Familiaridad básica con la sintaxis de C# y los conceptos de documentos Word

No se requiere ninguna instalación adicional de Office porque Aspose.Words funciona completamente en memoria.

## Crear un documento Word en blanco

El primer paso es instanciar un objeto `Document` vacío. Este objeto representa un archivo Word que aún no contiene secciones, párrafos ni contenido.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document
Document document = new Document();
```

**Por qué es importante:**  
Un `Document` en blanco te brinda un lienzo limpio. Si comienzas desde una plantilla existente, las formas ocultas podrían heredar estilos no deseados. Empezar desde cero garantiza que la forma rectangular que agregues después sea el único contenido que controlas.

## Agregar una forma rectangular al documento

A continuación, necesitamos un `DocumentBuilder` para colocar contenido en el documento. El método `InsertShape` del builder es la forma estándar **de insertar formas**, como rectángulos, círculos o dibujos personalizados.

```csharp
// Step 2: Initialize a DocumentBuilder to add content
DocumentBuilder builder = new DocumentBuilder(document);

// Step 3: Insert a rectangle shape of size 200x100 points
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

**Por qué es importante:**  
`InsertShape` devuelve un objeto `Shape` que puedes configurar más (color, estilo de línea, etc.). Las dimensiones se dan en puntos (1 punto = 1/72 de pulgada), lo que coincide con el sistema de medición interno de Word.

### Opcional: aplicar estilo al rectángulo

Si deseas que el rectángulo tenga un borde visible cuando lo vuelvas a mostrar más tarde, puedes establecer su grosor de línea y color:

```csharp
rectangleShape.LineWeight = 0.5;               // Thin border
rectangleShape.LineColor = System.Drawing.Color.Blue;
```

Estas líneas son opcionales porque la forma se ocultará en el siguiente paso.

## Ocultar la forma en Word

Word permite que las formas se oculten del diseño mientras siguen formando parte del modelo de objetos del documento. Establecer la propiedad `Hidden` a `true` hace que la forma sea invisible en la vista normal pero aún seleccionable a través de la API.

```csharp
// Step 4: Hide the shape so it does not appear in the layout
rectangleShape.Hidden = true;
```

**Por qué es importante:**  
Una forma oculta es útil para almacenar metadatos, marcadores de posición para procesamiento posterior o contenido condicional que revelas solo bajo ciertas circunstancias (p. ej., al generar un informe final). La forma permanece en el archivo, por lo que puedes volver a mostrarla programáticamente más tarde con `rectangleShape.Hidden = false;`.

## Guardar el documento

Finalmente, escribe el documento en disco. La extensión del archivo determina el formato de Word; `.docx` es el formato Open XML moderno.

```csharp
// Step 5: Save the document with the hidden shape
string outputPath = @"C:\Temp\HiddenShape.docx";
document.Save(outputPath);
```

**Resultado:**  
Al abrir `HiddenShape.docx` en Microsoft Word se muestra una página en blanco. El rectángulo no es visible, pero si vas a **Inicio → Seleccionar → Panel de selección**, verás la forma listada y podrás alternar su visibilidad.

## Ejemplo completo funcional

A continuación tienes el programa completo que puedes copiar, pegar y ejecutar. Incluye todas las declaraciones `using` necesarias y comentarios.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document
        Document document = new Document();

        // Initialize a DocumentBuilder for content insertion
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a rectangle shape (200x100 points)
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // Optional styling (comment out if not needed)
        rectangleShape.LineWeight = 0.5;
        rectangleShape.LineColor = System.Drawing.Color.Blue;

        // Hide the shape so it does not appear in the layout
        rectangleShape.Hidden = true;

        // Save the document
        string outputPath = @"C:\Temp\HiddenShape.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Salida esperada:**  

- La consola muestra la ruta de guardado.  
- `HiddenShape.docx` se abre como una página en blanco en Word.  
- La forma rectangular existe pero está oculta; puedes verificarla mediante el *Panel de selección* o configurando programáticamente `Hidden = false` y volviendo a abrir el archivo.

## Preguntas comunes y casos límite

| Pregunta | Respuesta |
|----------|-----------|
| **¿Puedo ocultar otros tipos de forma?** | Sí. Cualquier `Shape` (p. ej., `ShapeType.Ellipse`, `ShapeType.Picture`) admite la propiedad `Hidden`. |
| **¿Aumentará el tamaño del archivo la forma oculta?** | El aumento es insignificante (unos pocos kilobytes) porque los datos de la forma se almacenan como XML en el paquete `.docx`. |
| **¿Qué pasa si necesito que la forma aparezca solo en la vista de impresión?** | Utiliza la propiedad `Shape.IsPrint` en lugar de `Hidden`. Establecer `IsPrint = false` oculta la forma en la salida impresa pero la mantiene visible en pantalla. |
| **¿Cómo volver a mostrar la forma más tarde?** | Carga el documento, localiza la forma (p. ej., por `Shape.Name`), luego establece `shape.Hidden = false;` y guarda. |
| **¿Funciona esto con el formato .doc (binario)?** | Sí, Aspose.Words puede guardar en `.doc` usando `document.Save("file.doc");`. La bandera oculta se conserva. |

## Consejos profesionales

- **Nombra tus formas**: `rectangleShape.Name = "PlaceholderRectangle";` facilita encontrarlas más tarde mediante `document.GetChildNodes(NodeType.Shape, true).Cast<Shape>().FirstOrDefault(s => s.Name == "PlaceholderRectangle")`.
- **Procesamiento por lotes**: Si necesitas agregar formas ocultas a muchos documentos, envuelve el código en un método y reutiliza la instancia de `DocumentBuilder`.
- **Rendimiento**: Crear una forma es barato, pero guardar documentos grandes con frecuencia puede estar limitado por I/O. Considera usar `MemoryStream` para el procesamiento intermedio.

## Conclusión

Ahora sabes cómo **crear un documento Word en blanco**, **agregar una forma rectangular** y **ocultar la forma en Word** usando Aspose.Words for .NET. Esta técnica te permite incrustar marcadores de posición invisibles que puedes revelar o manipular más tarde, un patrón útil para la generación dinámica de informes, contenido condicional y plantillas de documentos.

Los siguientes pasos que podrías explorar:

- Reemplaza el rectángulo con una imagen o gráfico usando `ShapeType.Picture`.
- Usa **cómo insertar forma** en secciones de encabezado/pie de página para marcadores de posición tipo marca de agua.
- Combina formas ocultas con validación de datos basada en **agregar forma rectangular** (p. ej., almacenando JSON en la propiedad `AlternativeText` de una forma).

¡Feliz codificación, y siéntete libre de experimentar con otros tipos de forma y opciones de visibilidad para adaptarlos a tus necesidades de automatización de documentos!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Crear documento Word – Cómo agregar forma rectangular y sombra](/words/english/net/programming-with-shapes/create-word-document-how-to-add-rectangle-shape-and-shadow/)
- [Crear forma de grupo en documento Word usando Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Crear un documento Word en blanco con una forma elíptica oculta – Guía completa en C#](/words/english/net/programming-with-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape-ful/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}