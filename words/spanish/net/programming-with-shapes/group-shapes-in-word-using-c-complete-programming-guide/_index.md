---
category: general
date: 2026-10-13
description: Agrupa formas en Word con C# – aprende cómo agrupar formas y añadir formas
  al grupo usando Aspose.Words en unos pocos pasos fáciles.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- how to group shapes
- add shapes to group
language: es
lastmod: 2026-10-13
og_description: Agrupa formas en Word usando C# y Aspose.Words. Sigue esta guía para
  aprender cómo agrupar formas y añadir formas al grupo en un documento de Word.
og_image_alt: Screenshot of a Word document showing two shapes combined into a single
  grouped shape
og_title: Agrupar formas en Word con C# – guía paso a paso
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: group shapes in Word with C# – learn how to group shapes and add shapes
    to group using Aspose.Words in a few easy steps.
  headline: Group shapes in Word using C# – complete programming guide
  type: TechArticle
- description: group shapes in Word with C# – learn how to group shapes and add shapes
    to group using Aspose.Words in a few easy steps.
  name: Group shapes in Word using C# – complete programming guide
  steps:
  - name: Load the Word document
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Retrieve the shapes you want to group
    text: '```csharp // Get the first shape (index 0) and second shape (index 1) from
      the whole document. Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0,
      true); Shape secondShape = (Shape)doc.GetChild(NodeType.Shape, 1, true); ```'
  - name: Create a new `GroupShape` container
    text: '```csharp GroupShape groupShape = new GroupShape(doc); ```'
  - name: Add the individual shapes to the group
    text: '```csharp groupShape.AppendChild(firstShape); groupShape.AppendChild(secondShape);
      ```'
  - name: Insert the group shape into the document body
    text: '```csharp // Insert the group as the last child of the first paragraph.
      Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph; firstParagraph.AppendChild(groupShape);
      ```'
  - name: Save the modified document
    text: '```csharp string outputPath = @"YOUR_DIRECTORY\output.docx"; doc.Save(outputPath);
      ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Agrupar formas en Word usando C# – guía completa de programación
url: /es/net/programming-with-shapes/group-shapes-in-word-using-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Agrupar formas en Word usando C# – guía completa de programación

Si necesitas **agrupar formas en Word** programáticamente, esta guía te muestra exactamente cómo. Al final de las dos primeras frases sabrás el código necesario, la razón detrás de cada paso y cómo **añadir formas al grupo** sin sorpresas.

Cubrirémos todo, desde cargar un archivo `.docx` hasta guardar el documento actualizado. El tutorial asume que tienes conocimientos básicos de C# y una referencia a la biblioteca Aspose.Words for .NET. No se requiere documentación externa—solo copia, pega y ejecuta.

## Requisitos previos

- .NET 6.0 o posterior (el código también funciona con .NET Framework 4.7+)
- Paquete NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)
- Un documento Word (`input.docx`) que ya contiene al menos dos formas (p. ej., imágenes, AutoShapes)

> **Consejo profesional:** Si estás probando, crea un archivo Word sencillo con dos rectángulos mediante la interfaz de Word. Guárdalo como `input.docx` en una carpeta que controles.

## Agrupar formas en Word – guía paso a paso

A continuación dividimos el proceso en cinco pasos lógicos. Cada paso incluye el código C# exacto, una explicación de *por qué* se necesita la línea y una breve nota sobre errores comunes.

### Paso 1: Cargar el documento Word

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

string inputPath = @"YOUR_DIRECTORY\input.docx";
Document doc = new Document(inputPath);
```

**Por qué:** `Document` es el punto de entrada para cualquier manipulación de Word. Proporcionar la ruta completa del archivo carga el documento en memoria, permitiéndonos consultar y modificar su árbol de nodos.

**Trampa:** Pasar una ruta relativa puede fallar cuando el directorio de trabajo difiere. Usa una ruta absoluta o `Path.Combine` con `AppContext.BaseDirectory`.

### Paso 2: Recuperar las formas que deseas agrupar

```csharp
// Get the first shape (index 0) and second shape (index 1) from the whole document.
Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
Shape secondShape = (Shape)doc.GetChild(NodeType.Shape, 1, true);
```

**Por qué:** `GetChild` recorre el árbol del documento y devuelve el nodo *n‑ésimo* del tipo solicitado. Establecer `isDeep` a `true` busca en todo el documento, no solo en la sección actual.

**Caso límite:** Si el documento contiene menos de dos formas, `firstShape` o `secondShape` serán `null` y se lanzará una excepción al intentar convertir. Protege contra esto:

```csharp
if (firstShape == null || secondShape == null)
    throw new InvalidOperationException("The document must contain at least two shapes to group.");
```

### Paso 3: Crear un nuevo contenedor `GroupShape`

```csharp
GroupShape groupShape = new GroupShape(doc);
```

**Por qué:** `GroupShape` actúa como un nodo padre que puede contener varios objetos `Shape`. Hereda de `Shape`, por lo que puede insertarse donde se permite una forma regular (p. ej., dentro de un párrafo).

### Paso 4: Añadir las formas individuales al grupo

```csharp
groupShape.AppendChild(firstShape);
groupShape.AppendChild(secondShape);
```

**Por qué:** `AppendChild` mueve las formas de sus ubicaciones originales al nuevo grupo. Después de esta llamada, las formas originales ya no existen como nodos independientes; pasan a ser parte de `groupShape`.

**Consejo:** Agrupar ajusta automáticamente las posiciones relativas de las formas hijas. Si necesitas un diseño específico, establece la propiedad `GroupShape.Bounds` *antes* de añadir los hijos.

```csharp
// Example: set the group to start at (100, 100) points and be 300x200 points large.
groupShape.Bounds = new System.Drawing.RectangleF(100, 100, 300, 200);
```

### Paso 5: Insertar la forma de grupo en el cuerpo del documento

```csharp
// Insert the group as the last child of the first paragraph.
Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;
firstParagraph.AppendChild(groupShape);
```

**Por qué:** Un `GroupShape` debe colocarse dentro de un párrafo (o una celda de tabla) para renderizarse. Al añadirlo al primer párrafo garantizamos una ubicación visible sin alterar el diseño existente.

### Paso 6: Guardar el documento modificado

```csharp
string outputPath = @"YOUR_DIRECTORY\output.docx";
doc.Save(outputPath);
```

**Por qué:** `Save` escribe los cambios en memoria de vuelta a un archivo `.docx`. También puedes guardar en un flujo o a PDF cambiando la sobrecarga.

**Verificación del resultado:** Abre `output.docx` en Microsoft Word. Deberías ver las dos formas originales ahora combinadas en un único objeto agrupado. Seleccionar el grupo mostrará los manejadores de agrupación estándar de Word.

## Cómo agrupar formas programáticamente – ideas más profundas

- **Propiedad del nodo:** Cuando llamas a `AppendChild`, la referencia `ParentNode` de la forma cambia automáticamente. Esto evita nodos “huérfanos” que podrían corromper el documento.
- **Preservar formato:** Agrupar **no** pierde ningún formato de la forma (color de relleno, estilo de línea, etc.). Todas las formas hijas conservan sus propiedades originales.
- **Grupos anidados:** `GroupShape` puede contener otros objetos `GroupShape`, permitiendo jerarquías de varios niveles. Simplemente trata al grupo interno como cualquier otra forma.

## Añadir formas al grupo y gestionarlas después

Si necesitas añadir más formas después de crear el grupo inicial, puedes reutilizar la misma instancia `GroupShape`:

```csharp
// Assume we have a third shape somewhere in the document.
Shape thirdShape = (Shape)doc.GetChild(NodeType.Shape, 2, true);
groupShape.AppendChild(thirdShape);
```

Cuando más tarde necesites desagrupar, itera sobre `groupShape.GetChildNodes(NodeType.Shape, true)` y vuelve a insertar cada hijo donde los necesites.

```csharp
foreach (Shape child in groupShape.GetChildNodes(NodeType.Shape, true))
{
    // Example: move each child back to the original paragraph.
    firstParagraph.AppendChild(child);
}
firstParagraph.RemoveChild(groupShape); // Remove the empty group container.
```

**Por qué es importante:** Algunos flujos de trabajo requieren agrupación temporal (p. ej., alinear varios objetos) seguida de desagrupación para ediciones individuales posteriores.

## Ejemplo completo ejecutable

A continuación hay un programa autónomo que puedes compilar y ejecutar tal cual. Reemplaza `YOUR_DIRECTORY` con una ruta de carpeta real en tu máquina.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Load the document.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath);

        // 2. Retrieve the first two shapes.
        Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        Shape secondShape = (Shape)doc.GetChild(NodeType.Shape, 1, true);

        if (firstShape == null || secondShape == null)
        {
            Console.WriteLine("Document must contain at least two shapes.");
            return;
        }

        // 3. Create a GroupShape container.
        GroupShape groupShape = new GroupShape(doc);

        // Optional: define the group’s bounding box.
        groupShape.Bounds = new System.Drawing.RectangleF(100, 100, 300, 200);

        // 4. Add the shapes to the group.
        groupShape.AppendChild(firstShape);
        groupShape.AppendChild(secondShape);

        // 5. Insert the group into the first paragraph.
        Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(groupShape);

        // 6. Save the result.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Grouped shapes saved to {outputPath}");
    }
}
```

**Salida esperada:** Cuando abras `output.docx`, las dos formas originales aparecen como un único objeto agrupado. Seleccionar el grupo muestra los manejadores de agrupación familiares de Word, permitiéndote mover, redimensionar o rotar todo el conjunto junto.

## Conclusión

Ahora sabes cómo **agrupar formas en Word** usando C# y Aspose.Words, y has visto los pasos exactos para **añadir formas al grupo** y luego manipularlas o desagruparlas. Esta técnica es ideal para automatizar diseños de informes, crear diagramas compuestos o preparar plantillas de Word que requieran posicionamiento preciso de varios objetos.

A continuación, explora temas relacionados como **cómo agrupar formas** con diferentes tipos de anclaje, aplicar **formato avanzado** a objetos agrupados, o exportar el resultado agrupado a PDF. Experimenta con grupos anidados para crear gráficos complejos programáticamente.

¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Insertar formas en documentos Word usando Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Crear forma de grupo en documento Word usando Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Añadir efecto de sombra a formas de Word – Guía completa en C#](/words/english/net/programming-with-shapes/add-shadow-effect-to-word-shapes-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}