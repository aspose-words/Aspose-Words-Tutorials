---
category: general
date: 2026-09-21
description: Aprende a agrupar formas en Word usando Aspose.Words para C#. Esta guía
  paso a paso cubre la creación, el posicionamiento y el guardado de formas agrupadas.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in Word
- Aspose.Words shape grouping
- C# Word shape manipulation
- DocumentBuilder insert shape
- GroupShape container
language: es
lastmod: 2026-09-21
og_description: Agrupa formas en Word usando Aspose.Words para C#. Sigue este conciso
  tutorial para crear, posicionar y guardar formas agrupadas programáticamente.
og_image_alt: Screenshot of grouped shapes in Word document created with Aspose.Words
og_title: Agrupa formas en Word con Aspose.Words – guía completa de C#
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to group shapes in Word using Aspose.Words for C#. This step‑by‑step
    guide covers creating, positioning, and saving grouped shapes.
  headline: How to group shapes in Word with Aspose.Words for C#
  type: TechArticle
- description: Learn how to group shapes in Word using Aspose.Words for C#. This step‑by‑step
    guide covers creating, positioning, and saving grouped shapes.
  name: How to group shapes in Word with Aspose.Words for C#
  steps:
  - name: Create a blank document and a `DocumentBuilder`
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Insert the first rectangle shape
    text: '```csharp // Insert a rectangle that is 100 points wide and 50 points tall.
      Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50); ```'
  - name: Insert the second rectangle and offset it
    text: '```csharp // Insert the second rectangle with the same dimensions. Shape
      shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);'
  - name: Create a `GroupShape` large enough for both rectangles
    text: '```csharp // The group must be wide enough to contain both shapes (100
      pt + 120 pt + 100 pt = 320 pt). // We give a little extra margin, so the group
      width is set to 300 pt and height to 100 pt. GroupShape group = new GroupShape(doc,
      300, 100); ```'
  - name: Append the individual shapes to the group
    text: '```csharp group.AppendChild(shape1); group.AppendChild(shape2); ```'
  - name: Insert the grouped shape back into the document
    text: '```csharp // Insert the GroupShape at the current builder position. builder.InsertNode(group);
      ```'
  - name: Save the document
    text: '```csharp // Replace YOUR_DIRECTORY with an absolute or relative path where
      you have write permission. doc.Save("YOUR_DIRECTORY/GroupedShapes.docx"); ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Cómo agrupar formas en Word con Aspose.Words para C#
url: /es/net/programming-with-shapes/how-to-group-shapes-in-word-with-aspose-words-for-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo agrupar formas en Word con Aspose.Words para C#

Si necesitas **agrupar formas en Word** de forma programática, Aspose.Words lo hace muy sencillo. Este tutorial te muestra cómo crear dos formas rectangulares, colocarlas una al lado de la otra, combinarlas en un `GroupShape` y guardar el resultado como un archivo DOCX.

Verás un ejemplo completo y ejecutable, explicaciones de por qué cada paso es importante y consejos para manejar casos comunes como formas superpuestas o tamaños dinámicos. Al final de esta guía podrás integrar la agrupación de formas en cualquier proyecto de automatización de Word.

## Requisitos previos

Antes de comenzar, asegúrate de tener:

* .NET 6.0 (o posterior) instalado – Aspose.Words es compatible con .NET Standard 2.0+, .NET Core y .NET Framework.
* Una licencia válida de Aspose.Words for .NET (o una clave de evaluación temporal) – la biblioteca funciona sin licencia pero añade una marca de agua.
* Visual Studio 2022 (o cualquier IDE de C#) para compilar y ejecutar el ejemplo.

No se requieren paquetes NuGet adicionales más allá de `Aspose.Words`.

## Cómo agrupar formas en Word usando Aspose.Words

El núcleo de la solución es un objeto **`GroupShape`** que actúa como contenedor para las formas individuales. A continuación desglosamos el proceso en pasos claros.

### Paso 1: Crear un documento en blanco y un `DocumentBuilder`

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty Word document.
Document doc = new Document();

// DocumentBuilder provides convenient methods for inserting content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*¿Por qué este paso?*  
`Document` representa todo el archivo DOCX, mientras que `DocumentBuilder` proporciona métodos fluidos (p. ej., `InsertShape`) que colocan automáticamente los nuevos elementos en la posición actual del cursor.

### Paso 2: Insertar la primera forma rectangular

```csharp
// Insert a rectangle that is 100 points wide and 50 points tall.
Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

La llamada a `InsertShape` agrega la forma al documento y devuelve un objeto `Shape` que puedes configurar más (color, borde, etc.). El tamaño se expresa en puntos (1 pt ≈ 1/72 in).

### Paso 3: Insertar el segundo rectángulo y desplazarlo

```csharp
// Insert the second rectangle with the same dimensions.
Shape shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// Move the second shape 120 points to the right so the two rectangles do not overlap.
shape2.Left = 120; // Horizontal offset from the left edge of the page.
```

Establecer `Left` posiciona la forma respecto al margen de la página. El desplazamiento debe ser mayor que el ancho de la primera forma (100 pt) para evitar superposición; usamos 120 pt para dejar un pequeño espacio.

### Paso 4: Crear un `GroupShape` lo suficientemente grande para ambos rectángulos

```csharp
// The group must be wide enough to contain both shapes (100 pt + 120 pt + 100 pt = 320 pt).
// We give a little extra margin, so the group width is set to 300 pt and height to 100 pt.
GroupShape group = new GroupShape(doc, 300, 100);
```

`GroupShape` recibe el `Document` propietario y las dimensiones del contenedor. El ancho del contenedor debe superar el borde derecho de la forma más alejada; de lo contrario, la segunda forma quedaría recortada.

### Paso 5: Añadir las formas individuales al grupo

```csharp
group.AppendChild(shape1);
group.AppendChild(shape2);
```

Al añadirlas, las formas se mueven a la colección interna del grupo. Después de esta llamada, las formas ya no son objetos independientes en el árbol del documento; pertenecen al grupo.

### Paso 6: Insertar la forma agrupada de nuevo en el documento

```csharp
// Insert the GroupShape at the current builder position.
builder.InsertNode(group);
```

`InsertNode` coloca todo el `GroupShape` donde se encuentre actualmente el cursor. Si necesitas el grupo en un párrafo específico, mueve el builder a ese párrafo primero.

### Paso 7: Guardar el documento

```csharp
// Replace YOUR_DIRECTORY with an absolute or relative path where you have write permission.
doc.Save("YOUR_DIRECTORY/GroupedShapes.docx");
```

El archivo resultante contiene dos rectángulos que se comportan como un solo objeto: puedes moverlos, redimensionarlos o eliminarlos juntos en Microsoft Word.

## Código fuente completo

Juntando todos los pasos se obtiene un programa autónomo:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert the first rectangle (100 pt × 50 pt).
        Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // 3️⃣ Insert the second rectangle and offset it horizontally.
        Shape shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        shape2.Left = 120; // Prevent overlap.

        // 4️⃣ Create a GroupShape container large enough for both.
        GroupShape group = new GroupShape(doc, 300, 100);

        // 5️⃣ Add both rectangles to the group.
        group.AppendChild(shape1);
        group.AppendChild(shape2);

        // 6️⃣ Insert the grouped shape back into the document.
        builder.InsertNode(group);

        // 7️⃣ Save the document.
        doc.Save("YOUR_DIRECTORY/GroupedShapes.docx");
    }
}
```

**Salida esperada:** Al abrir *GroupedShapes.docx* en Microsoft Word se muestran dos rectángulos lado a lado, tratados como un único objeto seleccionable. Arrastrar el grupo mueve ambos rectángulos simultáneamente.

## Variaciones comunes y casos límite

| Situación | Ajuste recomendado |
|-----------|--------------------|
| **Más de dos formas** | Crea objetos `Shape` adicionales, posiciónalos según corresponda y añádelos al mismo `GroupShape`. |
| **Tamaño dinámico** | Calcula el ancho/alto del grupo basándote en los valores máximos de `Right` y `Bottom` de las formas hijas. |
| **Tipos de forma diferentes** | `ShapeType.Ellipse`, `ShapeType.Triangle`, etc., pueden insertarse de la misma manera; el contenedor del grupo no se preocupa del tipo. |
| **Formas rotadas** | Establece `shape.Rotation = 45;` antes de añadir; la rotación se conserva dentro del grupo. |
| **Guardar como PDF** | Llama a `doc.Save("GroupedShapes.pdf");` – el grupo se mantiene en la representación PDF. |

**Consejo profesional:** Después de agrupar, aún puedes modificar formas individuales accediendo a `group.GetChildNodes(NodeType.Shape, true)`. Esto es útil cuando necesitas cambiar el color de relleno de un rectángulo sin romper el grupo.

## Cómo verificar la agrupación programáticamente

Si necesitas confirmar que las formas están agrupadas correctamente (p. ej., en pruebas unitarias), examina la jerarquía de nodos del documento:

```csharp
NodeCollection groups = doc.GetChildNodes(NodeType.GroupShape, true);
Console.WriteLine($"Number of groups: {groups.Count}");
Console.WriteLine($"Children in first group: {groups[0].GetChildNodes(NodeType.Shape, true).Count}");
```

La salida debería ser:

```
Number of groups: 1
Children in first group: 2
```

Esto confirma que **las formas agrupadas en Word** se crearon según lo esperado.

## Conclusión

Ahora sabes cómo **agrupar formas en Word** con Aspose.Words para C#. El proceso implica crear formas individuales, posicionarlas, envolverlas en un `GroupShape` e insertar el grupo de nuevo en el documento. Con el ejemplo completo anterior puedes ampliar la técnica a cualquier número de formas, diferentes tipos o incluso combinarla con cuadros de texto e imágenes.

A continuación, explora temas relacionados como **agrupación de formas en Aspose.Words**, **manipulación de formas Word en C#** y **DocumentBuilder insert shape** para escenarios más avanzados de automatización de documentos. Experimenta con tamaños dinámicos, agrupación condicional y exportación a PDF para aprovechar al máximo el potencial de Aspose.Words.

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques alternativos en tus propios proyectos.

- [Insertar formas en documentos Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Crear forma rectangular en Word con Aspose.Words – Guía paso a paso](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Tutorial de sombra de forma en Aspose.Words – Añadir sombra a una forma Word en C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}