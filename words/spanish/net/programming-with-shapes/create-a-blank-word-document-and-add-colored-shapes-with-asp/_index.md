---
category: general
date: 2026-09-21
description: Crear un documento Word en blanco usando Aspose.Words, establecer el
  tamaño de la forma, establecer la posición de la forma, establecer el color de la
  forma y guardar el archivo docx en una única demostración.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- set shape size
- save docx file
- set shape position
- set shape color
language: es
lastmod: 2026-09-21
og_description: Cree un documento Word en blanco, establezca el tamaño de la forma,
  la posición de la forma, el color de la forma y guarde el archivo docx con Aspose.Words
  en minutos.
og_image_alt: Screenshot of a blank Word document containing two colored rectangles
  grouped together
og_title: Crea un documento Word en blanco y agrega formas coloreadas – Guía de Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create a blank Word document using Aspose.Words, set shape size, set
    shape position, set shape color, and save the docx file in a single walkthrough.
  headline: Create a blank Word document and add colored shapes with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Crea un documento Word en blanco y agrega formas coloreadas con Aspose.Words
url: /es/net/programming-with-shapes/create-a-blank-word-document-and-add-colored-shapes-with-asp/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear un documento Word en blanco y agregar formas coloreadas con Aspose.Words

Si necesitas **crear un documento Word en blanco** de forma programática, esta guía te muestra cómo hacerlo con Aspose.Words. Aprenderás a **establecer el tamaño de la forma**, **establecer la posición de la forma**, **establecer el color de la forma**, y finalmente **guardar el archivo docx** sin salir de tu IDE.

Trabajar con archivos Word en C# a menudo implica manejar llamadas de bajo nivel a OpenXML, pero Aspose.Words abstrae la complejidad. Al final de este tutorial tendrás un `.docx` completamente funcional que contiene una forma agrupada compuesta por dos rectángulos coloreados, ideal para informes, certificados o plantillas personalizadas.

## Requisitos previos

- .NET 6.0 o posterior (el código también funciona con .NET Framework 4.7+)
- Aspose.Words for .NET 23.9 o más reciente (instalar vía NuGet: `Install-Package Aspose.Words`)
- Familiaridad básica con C# y Visual Studio (o cualquier editor de C#)

No se requiere un archivo Word existente; el tutorial comienza **creando un documento Word en blanco** desde cero.

## Crear un documento Word en blanco con Aspose.Words

El primer paso es instanciar un objeto `Document`. Este objeto representa un archivo Word vacío en memoria.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Initialize a new, empty document.
Document document = new Document();

// DocumentBuilder gives you a cursor to add content.
DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` comienza vacío, lo cual es exactamente lo que necesitas cuando **creas un documento Word en blanco**. El `builder` se usará más adelante para insertar el grupo de formas en la posición actual del cursor.

## Establecer el tamaño de la forma y crear un GroupShape

Un `GroupShape` funciona como un contenedor que puede albergar múltiples formas individuales. Primero, define las dimensiones generales del contenedor.

```csharp
// Create a GroupShape that will hold multiple shapes.
// Width = 300 points, Height = 200 points.
GroupShape groupShape = new GroupShape(document, 300, 200);

// Position the group on the page: 100 points from the left, 100 points from the top.
groupShape.Left = 100;
groupShape.Top  = 100;
```

Aquí **establecemos el tamaño de la forma** para el propio grupo (300 × 200). Los mismos nombres de propiedades (`Width`, `Height`) se usan para cada forma hija, dándote un control detallado sobre cada elemento.

## Agregar el primer rectángulo y establecer el color de la forma

Ahora agrega un rectángulo al grupo y asígnale un color de fondo.

```csharp
// First rectangle – light blue background.
Shape rectangle1 = new Shape(document, ShapeType.Rectangle)
{
    Width = 120,
    Height = 80,
    Left = 0,          // Position relative to the group’s left edge.
    Top = 0,           // Position relative to the group’s top edge.
    FillColor = Color.LightBlue
};

// Append the rectangle to the group.
groupShape.AppendChild(rectangle1);
```

La propiedad `FillColor` **establece el color de la forma**. Usar `System.Drawing.Color` te permite elegir cualquier valor ARGB predefinido o personalizado.

## Agregar un segundo rectángulo, establecer su tamaño, posición y color

Un segundo rectángulo demuestra cómo **establecer la posición de la forma** relativa al grupo y cómo cambiar su color.

```csharp
// Second rectangle – light coral background.
Shape rectangle2 = new Shape(document, ShapeType.Rectangle)
{
    Width = 120,
    Height = 80,
    Left = 150,               // 150 points to the right of the group’s left edge.
    Top = 0,                  // Same vertical alignment as the first rectangle.
    FillColor = Color.LightCoral
};

groupShape.AppendChild(rectangle2);
```

Debido a que el ancho del grupo es de 300 puntos, los dos rectángulos de 120 puntos encajan cómodamente con un espacio de 30 puntos. Ajusta `Left` y `Top` si necesitas un diseño diferente.

## Insertar el GroupShape en el documento

Con el grupo completamente configurado, colócalo en la posición actual del cursor.

```csharp
// Insert the completed group shape at the builder’s current location.
builder.InsertNode(groupShape);
```

`InsertNode` escribe la forma directamente en el cuerpo del documento, preservando la **posición de la forma establecida** exacta que definiste anteriormente.

## Guardar el archivo docx

El paso final es persistir el documento en disco. Esto demuestra la operación de **guardar archivo docx**.

```csharp
// Define the output path (ensure the directory exists).
string outputPath = @"C:\Temp\GroupShape.docx";

// Save the document in DOCX format.
document.Save(outputPath);
```

Después de ejecutar el programa, abre `GroupShape.docx` en Microsoft Word. Deberías ver una página en blanco con una forma agrupada que contiene dos rectángulos coloreados posicionados lado a lado.

### Resultado esperado

- Un archivo `.docx` de una sola página.
- La página contiene una forma grupada ubicada a 100 pts de los márgenes izquierdo y superior.
- Dentro del grupo, un rectángulo azul claro está a la izquierda, y un rectángulo coral claro está a la derecha, cada uno de 120 × 80 pts.

## Ejemplo completo y ejecutable

A continuación se muestra el programa completo que puedes copiar y pegar en una aplicación de consola. No se requieren archivos adicionales.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Define a GroupShape and set its size and position.
        GroupShape groupShape = new GroupShape(document, 300, 200)
        {
            Left = 100,
            Top = 100
        };

        // 3️⃣ First rectangle – set size, position, and color.
        Shape rectangle1 = new Shape(document, ShapeType.Rectangle)
        {
            Width = 120,
            Height = 80,
            Left = 0,
            Top = 0,
            FillColor = Color.LightBlue
        };
        groupShape.AppendChild(rectangle1);

        // 4️⃣ Second rectangle – set size, position, and color.
        Shape rectangle2 = new Shape(document, ShapeType.Rectangle)
        {
            Width = 120,
            Height = 80,
            Left = 150,
            Top = 0,
            FillColor = Color.LightCoral
        };
        groupShape.AppendChild(rectangle2);

        // 5️⃣ Insert the grouped shape into the document.
        builder.InsertNode(groupShape);

        // 6️⃣ Save the docx file.
        string outputPath = @"C:\Temp\GroupShape.docx";
        document.Save(outputPath);

        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Ejecutar este programa crea el documento exacto descrito anteriormente, cumpliendo los cuatro objetivos: **crear documento Word en blanco**, **establecer el tamaño de la forma**, **establecer la posición de la forma**, **establecer el color de la forma**, y **guardar archivo docx**.

## Variaciones comunes y casos límite

| Escenario | Qué cambiar | Por qué es importante |
|----------|----------------|----------------|
| **Tipos de forma diferentes** | Reemplazar `ShapeType.Rectangle` por `ShapeType.Ellipse`, `ShapeType.Triangle`, etc. | Permite crear gráficos más complejos sin imágenes externas. |
| **Dimensiones dinámicas** | Calcular `Width` y `Height` a partir de la entrada del usuario o archivos de configuración. | Hace que la solución sea reutilizable en múltiples plantillas de documento. |
| **Guardar como PDF** | Llamar a `document.Save("output.pdf", SaveFormat.Pdf);` | Si los destinatarios necesitan un formato no editable, PDF es una opción segura. |
| **Agregar texto dentro de una forma** | Crear una forma `TextBox` y establecer `TextBox.Text`. | Útil para crear insignias o llamadas con etiqueta. |
| **Múltiples grupos en una página** | Repetir los pasos 2‑5 con diferentes valores de `Left`/`Top`. | Permite crear paneles de control o diseños de múltiples secciones. |

### Consejo profesional

Cuando necesites alinear las formas con precisión, usa la propiedad `ShapeBase.WrapType = WrapType.Inline` antes de insertar el grupo. Esto obliga al grupo a comportarse como un párrafo, evitando un flujo de texto inesperado a su alrededor.

## Conclusión

Ahora sabes cómo **crear un documento Word en blanco** con Aspose.Words, **establecer el tamaño de la forma**, **establecer la posición de la forma**, **establecer el color de la forma**, y **guardar el archivo docx**. El ejemplo completo demuestra un patrón limpio y reutilizable para agregar gráficos agrupados a cualquier proyecto de automatización de Word.

A partir de aquí puedes explorar:

- Agregar más formas o imágenes al mismo `GroupShape` (variaciones de **establecer el tamaño de la forma**, **establecer el color de la forma**).
- Usar `ShapeBase.Rotation` para rotar rectángulos con efectos decorativos.
- Exportar el mismo documento como PDF o HTML para ampliar la distribución (alternativa a **guardar archivo docx**).

Siéntete libre de experimentar con diferentes colores, tamaños y lógica de diseño para adaptarlos a tus necesidades específicas de informes o plantillas. ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Crear forma grupada en documento Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Crear forma rectangular en Word usando C# – Guía paso a paso](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Tutorial de sombra de forma Aspose.Words – Añadir una sombra a una forma Word en C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}