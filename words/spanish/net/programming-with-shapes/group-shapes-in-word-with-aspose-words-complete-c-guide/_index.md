---
category: general
date: 2026-07-19
description: Agrupa formas en Word usando Aspose.Words. Aprende cómo agregar una forma
  de rectángulo, definir una forma de elipse e insertar una forma en documentos de
  Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- how to group shapes
- insert shape into word
- define ellipse shape
language: es
lastmod: 2026-07-19
og_description: Agrupa formas en Word con Aspose.Words. Domina la adición de forma
  rectangular, la definición de forma elíptica y la inserción de formas en documentos
  de Word.
og_image_alt: Screenshot of grouped shapes in a Word document created with Aspose.Words
og_title: Agrupar formas en Word – Tutorial paso a paso de C#
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Group shapes in Word using Aspose.Words. Learn how to add rectangle
    shape, define ellipse shape, and insert shape into Word documents.
  headline: Group Shapes in Word with Aspose.Words – Complete C# Guide
  type: TechArticle
- description: Group shapes in Word using Aspose.Words. Learn how to add rectangle
    shape, define ellipse shape, and insert shape into Word documents.
  name: Group Shapes in Word with Aspose.Words – Complete C# Guide
  steps:
  - name: Set Up the Document and Builder
    text: We start by creating an empty `Document` and a `DocumentBuilder`. The builder
      is our “pen” that lets us insert content wherever we need it.
  - name: Add Rectangle Shape (add rectangle shape)
    text: Now we **add rectangle shape** to the document. We set its size, position,
      and fill colour to make it stand out.
  - name: Define Ellipse Shape (define ellipse shape)
    text: Next, we **define ellipse shape**. Notice the different `ShapeType` and
      the offset (`Left = 120`) so the ellipse sits beside the rectangle.
  - name: (Optional) Insert Individual Shapes for Preview
    text: If you want to see each shape before grouping, you can **insert shape into
      Word** individually. This step is optional but handy for debugging.
  - name: How to Group Shapes – Create a GroupShape
    text: 'Here’s the core of the tutorial: **how to group shapes**. We create a `GroupShape`,
      attach our rectangle and ellipse, and decide how the group behaves with surrounding
      text.'
  - name: Insert the Grouped Shape into the Document (insert shape into word)
    text: Now we **insert shape into Word**—but this time it’s the grouped container,
      not the individual pieces.
  - name: Save the Document
    text: Finally, write the file to disk. You can change the path to suit your project
      layout.
  - name: What if I need more than two shapes?
    text: Just keep calling `groupShape.AppendChild(yourNewShape);` before inserting
      the group. The API imposes no limit on the number of child shapes.
  - name: Can I rotate or resize the whole group?
    text: Absolutely. `GroupShape` inherits from `Shape`, so you can set properties
      like `RotationAngle`, `Width`, or `Height` on the group itself, and all child
      shapes will follow.
  - name: How do I change the group’s background colour?
    text: Use `groupShape.FillColor`. This fills the invisible bounding box; it can
      be handy for highlighting.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word Automation
title: Agrupar formas en Word con Aspose.Words – Guía completa de C#
url: /es/net/programming-with-shapes/group-shapes-in-word-with-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Agrupar formas en Word – Guía completa en C#

¿Alguna vez te has preguntado cómo **agrupar formas en Word** sin complicarte con la interfaz? No estás solo. Ya sea que estés generando contratos, folletos o diagramas de forma programática, poder **añadir forma de rectángulo**, **definir forma de elipse**, y luego **agrupar formas en Word** puede ahorrarte horas de trabajo manual.

En este tutorial recorreremos un ejemplo del mundo real usando **Aspose.Words for .NET**. Al final sabrás exactamente cómo **insertar forma en Word**, combinarlas y producir un documento pulido que podrás enviar a clientes o compañeros de equipo.

---

## Lo que necesitarás

Antes de comenzar, asegúrate de tener lo siguiente:

- **Aspose.Words for .NET** (última versión, p.ej., 24.9). Puedes obtenerlo de NuGet con `Install-Package Aspose.Words`.
- Un entorno de desarrollo .NET (Visual Studio 2022 o VS Code con la extensión C# funciona bien).
- Familiaridad básica con la sintaxis de C# — nada complicado, solo las habituales sentencias `using` y la creación de objetos.

Eso es todo. Sin bibliotecas adicionales, sin interop COM, solo código administrado puro.

---

## Cómo agrupar formas en Word usando Aspose.Words

A continuación tienes un desglose paso a paso que refleja el código que ya tienes. Cada paso explica **por qué** lo hacemos, no solo **qué** hace la línea, para que puedas adaptar el patrón a cualquier forma que desees.

### Paso 1: Configurar el documento y el builder

Comenzamos creando un `Document` vacío y un `DocumentBuilder`. El builder es nuestro “bolígrafo” que nos permite insertar contenido donde lo necesitemos.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();
// The builder will help us place shapes and text
DocumentBuilder builder = new DocumentBuilder(document);
```

> **¿Por qué?** El objeto `Document` representa todo el archivo .docx, mientras que `DocumentBuilder` ofrece una API conveniente para insertar nodos (como formas) sin tener que manejar el árbol de nodos subyacente.

### Paso 2: Añadir forma de rectángulo (add rectangle shape)

Ahora **añadimos una forma de rectángulo** al documento. Establecemos su tamaño, posición y color de relleno para que destaque.

```csharp
// Create a rectangle shape
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 100;                     // Width in points
rectangleShape.Height = 50;                      // Height in points
rectangleShape.Left   = 0;                       // X‑coordinate
rectangleShape.Top    = 0;                       // Y‑coordinate
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
```

> **Consejo:** Puedes cambiar `FillColor` a cualquier `System.Drawing.Color` que prefieras. Esto es útil cuando necesitas secciones codificadas por color en un informe.

### Paso 3: Definir forma de elipse (define ellipse shape)

A continuación, **definimos una forma de elipse**. Observa el diferente `ShapeType` y el desplazamiento (`Left = 120`) para que la elipse quede al lado del rectángulo.

```csharp
// Create an ellipse shape
Shape ellipseShape = new Shape(document, ShapeType.Ellipse);
ellipseShape.Width  = 80;
ellipseShape.Height = 40;
ellipseShape.Left   = 120;   // Position it to the right of the rectangle
ellipseShape.Top    = 0;
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```

> **Por qué es importante:** Al posicionar las formas explícitamente, controlas cómo aparecen antes de agruparlas. Si dependes del diseño automático, el agrupamiento podría quedar descentrado.

### Paso 4: (Opcional) Insertar formas individuales para vista previa

Si deseas ver cada forma antes de agrupar, puedes **insertar forma en Word** individualmente. Este paso es opcional pero útil para depurar.

```csharp
// Insert the rectangle and ellipse separately (useful for preview)
builder.InsertNode(rectangleShape);
builder.InsertNode(ellipseShape);
```

> **Consejo profesional:** Comenta estas dos líneas una vez que estés seguro de que las formas se ven bien; de lo contrario terminarás con visuales duplicados después del agrupamiento.

### Paso 5: Cómo agrupar formas – Crear un GroupShape

Este es el núcleo del tutorial: **cómo agrupar formas**. Creamos un `GroupShape`, adjuntamos nuestro rectángulo y elipse, y decidimos cómo se comporta el grupo con el texto circundante.

```csharp
// Create a container for the group
GroupShape groupShape = new GroupShape(document);

// Add the rectangle and ellipse to the group
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);

// Set wrapping – Inline makes the group act like a character in the text flow
groupShape.WrapType = WrapType.Inline;
```

> **Explicación:** `GroupShape` es esencialmente un mini‑lienzo que contiene otras formas. Al establecer `WrapType` a `Inline`, todo el grupo se mueve como una sola unidad cuando añades o eliminas texto.

### Paso 6: Insertar la forma agrupada en el documento (insert shape into word)

Ahora **insertamos forma en Word**—pero esta vez es el contenedor agrupado, no las piezas individuales.

```csharp
// Insert the grouped shape at the current cursor position
builder.InsertNode(groupShape);
```

> **¿Qué ocurre internamente?** La llamada `InsertNode` agrega el `GroupShape` a la colección de nodos del documento. Como el grupo ya contiene el rectángulo y la elipse, aparecen juntos como un solo objeto.

### Paso 7: Guardar el documento

Finalmente, escribe el archivo en disco. Puedes cambiar la ruta para adaptarla a la estructura de tu proyecto.

```csharp
// Save the resulting .docx file
document.Save("YOUR_DIRECTORY/GroupShape.docx");
```

> **Resultado:** Abre `GroupShape.docx` en Microsoft Word y verás un rectángulo azul claro y una elipse coral bloqueados juntos. Arrastrar uno mueve al otro—exactamente lo que promete “agrupar formas en Word”.

---

## Confirmación visual

A continuación tienes una maqueta de cómo se ven las formas agrupadas dentro del archivo Word.

![Captura de pantalla de formas agrupadas en un documento Word creado con Aspose.Words](grouped_shapes_placeholder.png "agrupar formas en Word")

*El texto alternativo de la imagen contiene la palabra clave principal para accesibilidad y SEO.*

---

## Preguntas frecuentes y casos límite

### ¿Qué pasa si necesito más de dos formas?

Simplemente sigue llamando a `groupShape.AppendChild(yourNewShape);` antes de insertar el grupo. La API no impone límite en la cantidad de formas hijas.

### ¿Puedo rotar o cambiar el tamaño de todo el grupo?

Absolutamente. `GroupShape` hereda de `Shape`, por lo que puedes establecer propiedades como `RotationAngle`, `Width` o `Height` en el propio grupo, y todas las formas hijas seguirán.

```csharp
groupShape.RotationAngle = 15;   // Rotate the entire group 15 degrees
groupShape.Width = 250;          // Stretch the group uniformly
```

### ¿Cómo cambio el color de fondo del grupo?

Usa `groupShape.FillColor`. Esto rellena el cuadro delimitador invisible; puede ser útil para resaltar.

```csharp
groupShape.FillColor = System.Drawing.Color.LightGray;
```

### ¿Esto funciona con formatos Word antiguos (.doc)?

`Aspose.Words` también puede guardar en `.doc`—solo reemplaza la extensión del archivo en `Save`. Sin embargo, algunas funciones avanzadas de formas (como el agrupamiento) solo son totalmente compatibles con el formato OOXML `.docx`.

---

## Ejemplo completo y funcional

Copia y pega el siguiente bloque en una nueva aplicación de consola para ver todo el proceso en acción. No falta ninguna pieza; este es un **ejemplo completo y ejecutable**.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing; // For Color

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Add rectangle shape
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width  = 100;
        rectangleShape.Height = 50;
        rectangleShape.Left   = 0;
        rectangleShape.Top    = 0;
        rectangleShape.FillColor = Color.LightBlue;

        // 3️⃣ Define ellipse shape
        Shape ellipseShape = new Shape(document, ShapeType.Ellipse);
        ellipseShape.Width  = 80;
        ellipseShape.Height = 40;
        ellipseShape.Left   = 120;
        ellipseShape.Top    = 0;
        ellipseShape.FillColor = Color.LightCoral;

        // 4️⃣ (Optional) Preview individual shapes
        // builder.InsertNode(rectangleShape);
        // builder.InsertNode(ellipseShape);

        // 5️⃣ Group the shapes together
        GroupShape groupShape = new GroupShape(document);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        groupShape.WrapType = WrapType.Inline;

        // 6️⃣ Insert the grouped shape into the document
        builder.InsertNode(groupShape);

        // 7️⃣ Save the file
        document.Save("GroupShape.docx");

        System.Console.WriteLine("Document created successfully!");
    }
}
```

**Salida esperada:** Cuando abras `GroupShape.docx`, verás un único objeto agrupado que consiste en un rectángulo azul claro y una elipse coral claro, perfectamente alineados lado a lado.

---

## Resumen

Acabamos de cubrir todo lo que necesitas para **agrupar formas en Word** con Aspose.Words:

1. Crear un documento y un builder.  
2. **Add rectangle shape** y **define ellipse shape** con dimensiones explícitas.  
3. (Opcionalmente) **insert shape into Word** para una vista previa rápida.  
4. Usa `GroupShape` para **how to group shapes** — agrega cada hijo, establece el ajuste y inserta.  
5. Guarda el archivo y verifica el

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Insertar formas en documentos Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Crear forma de rectángulo en Word con Aspose.Words – Guía paso a paso](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Tutorial de sombra de forma Aspose.Words – Añadir una sombra a una forma Word en C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}