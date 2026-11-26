---
category: general
date: 2026-11-18
description: Aprende a crear una forma rectangular en un documento de Word con C#.
  La guía también cubre cómo establecer el tamaño de la forma, la posición de la forma
  y agrupar formas en Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- set shape size
- group shapes in word
- set shape dimensions
- set shape position
language: es
lastmod: 2026-11-18
og_description: Crea una forma rectangular en un archivo de Word usando C# y aprende
  a establecer las dimensiones de la forma, la posición de la forma y a agrupar formas
  en Word.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  shape created with C#
og_title: Crear forma rectangular y agrupar formas en Word con C#
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Learn how to create rectangle shape in a Word document with C#. The
    guide also covers set shape size, set shape position, and group shapes in Word.
  headline: How to create rectangle shape and group shapes in Word using C#
  type: TechArticle
- description: Learn how to create rectangle shape in a Word document with C#. The
    guide also covers set shape size, set shape position, and group shapes in Word.
  name: How to create rectangle shape and group shapes in Word using C#
  steps:
  - name: Initialize the document and builder
    text: '```csharp using System; using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Insert a group shape
    text: '```csharp // Step 2: Insert a group shape that will hold multiple child
      shapes GroupShape group = builder.InsertGroupShape(); ```'
  - name: Create the rectangle and set its size
    text: '```csharp // Step 3: Create a rectangle shape, set its size, and add it
      to the group Shape rectangle = new Shape(doc, ShapeType.Rectangle); rectangle.Width
      = 100; // set shape size (width) in points rectangle.Height = 50; // set shape
      size (height) in points group.AppendChild(rectangle); ```'
  - name: Create the ellipse, set dimensions, and position it
    text: '```csharp // Step 4: Create an ellipse shape, set its size and position,
      and add it to the group Shape ellipse = new Shape(doc, ShapeType.Ellipse); ellipse.Width
      = 80; // set shape dimensions (width) ellipse.Height = 80; // set shape dimensions
      (height) ellipse.Left = 120; // set shape position rela'
  - name: Save the document
    text: '```csharp // Step 5: Save the document containing the grouped shapes doc.Save("GroupShape.docx");
      Console.WriteLine("Document saved successfully."); } } ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Cómo crear una forma rectangular y agrupar formas en Word usando C#
url: /es/java/images-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-using/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo crear una forma rectangular y agrupar formas en Word usando C#

Si necesitas **crear una forma rectangular** en un documento de Word, este tutorial te muestra una solución completa y lista para ejecutar. Verás cómo establecer el tamaño de la forma, establecer la posición de la forma y agrupar formas en Word para que se comporten como un solo objeto.

Trabajar con formas es un requisito común al generar informes, facturas o diagramas de forma programática. Al final de esta guía podrás generar un archivo `.docx` que contiene un rectángulo, una elipse y un contenedor agrupado, todo creado con Aspose.Words for .NET.

## Requisitos previos

- .NET 6.0 SDK o posterior (el código también funciona con .NET Framework 4.7+)
- Paquete NuGet de Aspose.Words for .NET (`Install-Package Aspose.Words`)
- Un editor de código o IDE (Visual Studio, VS Code, Rider, etc.)

No se requieren bibliotecas adicionales.

## Cómo crear una forma rectangular y agrupar formas en Word

Los pasos principales son:

1. **Crear un documento en blanco** y un `DocumentBuilder`.
2. **Insertar un `GroupShape`** que contendrá las formas individuales.
3. **Crear una forma rectangular**, establecer sus dimensiones y agregarla al grupo.
4. **Crear una forma elíptica**, establecer su tamaño y posición, y agregarla al grupo.
5. **Guardar** el documento.

Cada paso se explica a continuación, y el código fuente completo sigue a la explicación.

### Paso 1: Inicializar el documento y el constructor

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` representa todo el archivo de Word, mientras que `DocumentBuilder` proporciona una API fluida para insertar contenido. Inicializarlos es obligatorio antes de poder agregar cualquier forma.

### Paso 2: Insertar una forma de grupo

```csharp
        // Step 2: Insert a group shape that will hold multiple child shapes
        GroupShape group = builder.InsertGroupShape();
```

Un `GroupShape` funciona como un contenedor; todas las formas hijas se mueven juntas. Esta es la forma recomendada de **agrupar formas en Word** cuando necesitas transformaciones colectivas (p. ej., mover, rotar o eliminar).

### Paso 3: Crear el rectángulo y establecer su tamaño

```csharp
        // Step 3: Create a rectangle shape, set its size, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width = 100;   // set shape size (width) in points
        rectangle.Height = 50;   // set shape size (height) in points
        group.AppendChild(rectangle);
```

Aquí **creamos una forma rectangular** y **establecemos el tamaño de la forma** asignando `Width` y `Height`. En Aspose.Words, los tamaños se expresan en puntos (1 pt ≈ 1/72 in). Establecer las dimensiones explícitamente garantiza que el rectángulo aparezca exactamente como se desea.

### Paso 4: Crear la elipse, establecer dimensiones y posicionarla

```csharp
        // Step 4: Create an ellipse shape, set its size and position, and add it to the group
        Shape ellipse = new Shape(doc, ShapeType.Ellipse);
        ellipse.Width = 80;      // set shape dimensions (width)
        ellipse.Height = 80;     // set shape dimensions (height)
        ellipse.Left = 120;      // set shape position relative to the group
        group.AppendChild(ellipse);
```

Las **dimensiones de la forma** para la elipse son idénticas en ancho y alto, produciendo un círculo perfecto. La propiedad `Left` demuestra **establecer la posición de la forma**: la elipse comienza a 120 pt a la derecha del origen del grupo, por lo que no se superpone al rectángulo.

### Paso 5: Guardar el documento

```csharp
        // Step 5: Save the document containing the grouped shapes
        doc.Save("GroupShape.docx");
        Console.WriteLine("Document saved successfully.");
    }
}
```

Guardar escribe el archivo de Word en el disco. Puedes abrir `GroupShape.docx` en Microsoft Word para verificar que el rectángulo y la elipse están agrupados y posicionados correctamente.

## Configuración de dimensiones y tamaño de la forma – análisis profundo

- **Puntos vs. pulgadas**: 72 pt = 1 in. Si prefieres pulgadas, multiplica por 72 (p. ej., `2.5 * 72` para 2.5 in).
- **Escalado automático**: Si omites `Width` o `Height`, la forma usa su tamaño predeterminado. Establece explícitamente **el tamaño de la forma** para evitar sorpresas en el diseño.
- **Relación de aspecto**: Para formas como `Ellipse`, mantener `Width` y `Height` iguales conserva una apariencia circular.

## Posicionamiento de una forma en Word

Las propiedades `Left` y `Top` controlan el desplazamiento de la forma dentro de su contenedor (el grupo o la página). Los valores positivos mueven la forma a la derecha/abajo; los valores negativos la desplazan a la izquierda/arriba. Al agrupar, las posiciones son relativas al origen del grupo, lo que simplifica los cálculos de diseño.

## Agrupar formas en Word usando Aspose.Words

Agrupar es esencial cuando deseas que varias formas actúen como una sola unidad. El objeto `GroupShape`:

- Soporta `AppendChild` para agregar cualquier `Shape` (rectángulo, elipse, imagen, etc.).
- Permite mover, rotar o eliminar todo el grupo con una sola llamada.
- Mantiene las posiciones de las formas hijas relativas al grupo, facilitando la gestión de diagramas complejos.

**Consejo profesional:** Después de agregar todas las formas hijas, puedes ajustar el `Width`, `Height`, `Left` y `Top` del grupo para reposicionar toda la colección en un solo paso.

## Ejemplo completo ejecutable

A continuación se muestra el programa completo que puedes copiar, pegar y ejecutar. Incluye todas las directivas `using`, un método `Main` y comentarios que explican cada línea.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a GroupShape to hold child shapes
        GroupShape group = builder.InsertGroupShape();

        // 3️⃣ Create a rectangle, set its dimensions, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width = 100;   // set shape size (width) in points
        rectangle.Height = 50;   // set shape size (height) in points
        group.AppendChild(rectangle); // add rectangle to the group

        // 4️⃣ Create an ellipse, set size and position, then add it to the group
        Shape ellipse = new Shape(doc, ShapeType.Ellipse);
        ellipse.Width = 80;      // set shape dimensions (width)
        ellipse.Height = 80;     // set shape dimensions (height)
        ellipse.Left = 120;      // set shape position inside the group
        group.AppendChild(ellipse); // add ellipse to the group

        // 5️⃣ Save the document
        doc.Save("GroupShape.docx");
        Console.WriteLine("Document 'GroupShape.docx' created with a rectangle and an ellipse grouped together.");
    }
}
```

**Salida esperada:** Después de ejecutar el programa, `GroupShape.docx` aparece en la carpeta de ejecución. Al abrirlo en Word se muestra un rectángulo (100 pt × 50 pt) a la izquierda y una elipse (80 pt × 80 pt) posicionada a 120 pt a la derecha, ambas dentro de un único objeto agrupado.

![Documento de Word con rectángulo y elipse agrupados](grouped_shapes.png){: .center alt="Captura de pantalla de un documento de Word que muestra un rectángulo y una elipse agrupados creados con C#" }

*La imagen anterior ilustra el resultado final; el rectángulo y la elipse son seleccionables como un solo grupo.*

## Preguntas frecuentes y casos límite

| Pregunta | Respuesta |
|----------|----------|
| **¿Puedo agregar más de dos formas?** | Sí. Llama a `group.AppendChild(yourShape)` para cada forma adicional. |
| **¿Qué pasa si necesito rotar el grupo?** | Usa `group.RotationAngle = 45;` (grados) después de agregar todos los hijos. |
| **¿Cómo cambio el color de fondo del grupo?** | Establece `group.FillColor = System.Drawing.Color.LightGray;`. |
| **¿Esto funcionará con archivos .doc?** | Aspose.Words admite `.doc` y `.docx`. El mismo código funciona; solo cambia la extensión del archivo en `Save`. |
| **¿Hay un impacto de memoria al agrupar muchas formas?** | Agrupar en sí añade una sobrecarga mínima. La principal preocupación es el número total de formas; mantenlo razonable para documentos grandes. |

## Conclusión

En este tutorial aprendiste cómo **crear una forma rectangular** en un archivo de Word usando C#, cómo **establecer el tamaño de la forma**, **establecer las dimensiones de la forma**, **establecer la posición de la forma**, y finalmente cómo **agrupar formas en Word** con Aspose.Words. El ejemplo completo demuestra un enfoque limpio y mantenible que puedes ampliar a diagramas más complejos, gráficos o imágenes personalizadas.

A continuación, podrías explorar:

- Añadir texto dentro de las formas (`Shape.TextPath.Text = "Hello"`).
- Insertar imágenes en un `GroupShape`.
- Exportar las formas agrupadas a PDF con `doc.Save("output.pdf")`.

Siéntete libre de experimentar con diferentes tamaños, posiciones y tipos de formas adicionales para adaptarlos a las necesidades de tu proyecto. ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Crear forma de grupo en documento Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}