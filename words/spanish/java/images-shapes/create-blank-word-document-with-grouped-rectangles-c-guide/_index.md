---
category: general
date: 2026-07-23
description: Crea un documento de Word en blanco y agrega una forma rectangular en
  C#. Aprende cómo insertar formas y agrupar formas en Word usando Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- group shapes word
- how to insert shapes
- how to group shapes
language: es
lastmod: 2026-07-23
og_description: Crea un documento de Word en blanco en C# y aprende cómo insertar
  formas, agregar una forma de rectángulo y agrupar formas en Word con Aspose.Words.
og_image_alt: Screenshot showing a blank Word document with two rectangle shapes grouped
  together
og_title: Crear documento de Word en blanco con rectángulos agrupados – tutorial de
  C#
schemas:
- author: Aspose
  dateModified: '2026-07-23'
  description: Create blank word document and add rectangle shape in C#. Learn how
    to insert shapes and group shapes word using Aspose.Words.
  headline: Create blank word document with grouped rectangles – C# guide
  type: TechArticle
- description: Create blank word document and add rectangle shape in C#. Learn how
    to insert shapes and group shapes word using Aspose.Words.
  name: Create blank word document with grouped rectangles – C# guide
  steps:
  - name: What if I need more than two shapes?
    text: Just keep calling `builder.InsertShape(...)` and `group.AppendChild(...)`
      for each new shape. The group can hold any number of children.
  - name: Can I set fill colour or border on the rectangles?
    text: 'Absolutely. After creating a rectangle you can tweak its `FillColor`, `OutlineColor`,
      and `LineWidth`:'
  - name: How do I move the whole group after it’s been created?
    text: 'Use the group''s `Left` and `Top` properties, measured in points:'
  - name: What about scaling the group?
    text: Set `group.Width` and `group.Height` or use `group.ScaleX` / `group.ScaleY`.
      The child rectangles retain their proportions relative to the group.
  - name: Does this work with older .doc files?
    text: Aspose.Words abstracts the file format, so the same code works for `.doc`
      and `.docx`. The only limitation is that some newer shape features may be down‑sampled
      when saving to the older binary format.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Crear documento de Word en blanco con rectángulos agrupados – Guía de C#
url: /es/java/images-shapes/create-blank-word-document-with-grouped-rectangles-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear documento de Word en blanco con rectángulos agrupados – Guía C#

¿Alguna vez necesitaste **crear documento de Word en blanco** que ya contenga un conjunto de formas, pero no estabas seguro de cómo agruparlas correctamente? No eres el único. En muchos escenarios de generación de informes o plantillas deseas un lienzo limpio con un par de rectángulos que actúen como marcadores de posición, y que se muevan juntos como una sola unidad.

En este tutorial recorreremos los pasos exactos para **crear documento de Word en blanco**, **añadir forma de rectángulo**, y luego **agrupar formas en Word** usando la biblioteca Aspose.Words. Al final tendrás un archivo `.docx` listo para usar donde los dos rectángulos forman parte de un grupo, de modo que cualquier posicionamiento o redimensionamiento posterior los afecte a ambos a la vez.  

También responderemos a las preguntas comunes “**cómo insertar formas**” y “**cómo agrupar formas**” que aparecen en foros y Stack Overflow. No se requieren documentos externos—todo lo que necesitas está aquí.

---

## Requisitos previos

- .NET 6 o posterior (el código también compila con .NET Core)  
- Aspose.Words para .NET (paquete NuGet `Aspose.Words`)  
- Un conocimiento básico de la sintaxis de C# (si ya has escrito un “Hello World”, estás listo)  

Si aún no has instalado Aspose.Words, ejecuta:

```bash
dotnet add package Aspose.Words
```

Eso es todo—sin DLLs extra, sin interop COM, solo una referencia limpia a NuGet.

---

## Paso 1: Crear documento de Word en blanco e inicializar el builder

Lo primero que hacemos es crear un objeto `Document` vacío. Piensa en él como una hoja de papel fresca. Luego adjuntamos un `DocumentBuilder`, que es la herramienta práctica que Aspose proporciona para insertar contenido.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document doc = new Document();               // <-- create blank word document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Por qué es importante:** Sin un `DocumentBuilder` tendrías que manipular manualmente el árbol de nodos de bajo nivel, lo que es propenso a errores. El builder abstrae las complejidades XML de un archivo `.docx`.

---

## Paso 2: Cómo insertar formas – añadir primero un contenedor de grupo

Aspose te permite insertar una *forma de grupo* que luego puede contener otras formas. Esta es la base para **agrupar formas en Word**.  

```csharp
        // Step 2: Insert a group shape that will act as a container
        Shape group = builder.InsertGroupShape();
```

> **Consejo profesional:** El grupo en sí es invisible hasta que añades formas hijas, por lo que no verás ningún artefacto en el documento resultante hasta el siguiente paso.

---

## Paso 3: Añadir forma de rectángulo – los objetos visibles reales

Ahora **añadiremos forma de rectángulo** dos veces, cada una con su propio tamaño. El método `InsertShape` recibe un `ShapeType` y dimensiones en puntos (1 pt ≈ 1/72 pulgada).

```csharp
        // Step 3: Insert two rectangle shapes with desired dimensions
        Shape rect1 = builder.InsertShape(ShapeType.Rectangle, 100, 50); // 100 pt × 50 pt
        Shape rect2 = builder.InsertShape(ShapeType.Rectangle, 80, 40);  // 80 pt × 40 pt
```

> **¿Por qué rectángulos?** Son la forma geométrica más simple, perfecta para marcadores de posición, maquetas de UI tipo botón o elementos gráficos simples.

---

## Paso 4: Cómo agrupar formas – adjuntar los rectángulos al grupo

Con los rectángulos creados, ahora **agruparemos las formas** añadiéndolos como hijos de la forma de grupo que insertamos antes.

```csharp
        // Step 4: Append the rectangles to the group shape
        group.AppendChild(rect1);
        group.AppendChild(rect2);
```

> **¿Qué ocurre bajo el capó?** La forma de grupo se convierte en el nodo padre en el árbol XML del documento. Mover el grupo mueve ambos rectángulos juntos, preservando sus posiciones relativas.

---

## Paso 5: Guardar el documento – ahora tienes un archivo Word con forma agrupada

Finalmente, guardamos el documento en disco. Cambia la ruta a una ubicación que exista en tu máquina.

```csharp
        // Step 5: Save the document with the grouped shapes
        doc.Save("GroupShape.docx");   // Creates a blank word document with grouped rectangles
    }
}
```

Ese es todo el programa. Ejecútalo, abre `GroupShape.docx` y verás dos rectángulos juntos. Si seleccionas uno, todo el grupo se resalta—exactamente lo que **agrupar formas en Word** debe hacer.

---

## Código fuente completo en un solo lugar

Para mayor comodidad, aquí tienes el ejemplo completo listo para copiar y pegar:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a group shape that will contain other shapes
        Shape group = builder.InsertGroupShape();

        // Insert two rectangle shapes with desired dimensions
        Shape rect1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        Shape rect2 = builder.InsertShape(ShapeType.Rectangle, 80, 40);

        // Add the rectangles to the group shape
        group.AppendChild(rect1);
        group.AppendChild(rect2);

        // Save the document
        doc.Save("GroupShape.docx");
    }
}
```

**Salida esperada:** Al abrir `GroupShape.docx` se muestra una página en blanco con dos rectángulos agrupados. Seleccionar un rectángulo selecciona automáticamente el otro, confirmando que el agrupamiento tuvo éxito.

---

## Preguntas frecuentes y manejo de casos límite

### ¿Qué pasa si necesito más de dos formas?

Simplemente sigue llamando a `builder.InsertShape(...)` y `group.AppendChild(...)` para cada nueva forma. El grupo puede contener cualquier número de hijos.

### ¿Puedo establecer color de relleno o borde en los rectángulos?

Claro. Después de crear un rectángulo puedes ajustar su `FillColor`, `OutlineColor` y `LineWidth`:

```csharp
rect1.FillColor = System.Drawing.Color.LightBlue;
rect1.OutlineColor = System.Drawing.Color.DarkBlue;
rect1.LineWidth = 1.5;
```

### ¿Cómo muevo todo el grupo después de haberlo creado?

Utiliza las propiedades `Left` y `Top` del grupo, medidas en puntos:

```csharp
group.Left = 150;   // move 150 pt from the left margin
group.Top  = 200;   // move 200 pt from the top of the page
```

### ¿Qué hay de escalar el grupo?

Establece `group.Width` y `group.Height` o usa `group.ScaleX` / `group.ScaleY`. Los rectángulos hijos conservan sus proporciones relativas al grupo.

### ¿Esto funciona con archivos .doc antiguos?

Aspose.Words abstrae el formato del archivo, por lo que el mismo código funciona para `.doc` y `.docx`. La única limitación es que algunas características de forma más recientes pueden degradarse al guardar en el formato binario más antiguo.

---

## Consejos profesionales para código listo para producción

- **Liberar recursos** – Envuelve `Document` en un bloque `using` si trabajas con archivos grandes para liberar memoria rápidamente.  
- **Manejo de errores** – Captura `Aspose.Words.Fonts.FontSettingsException` si planeas incrustar fuentes personalizadas.  
- **Rendimiento** – Al insertar muchas formas, desactiva temporalmente las actualizaciones de diseño con `doc.LayoutOptions = new LayoutOptions { UpdateFields = false };` y vuelve a activarlas después.

---

## Conclusión

Ahora sabes **cómo crear documento de Word en blanco**, **añadir forma de rectángulo**, y **agrupar formas en Word** usando Aspose.Words en C#. El ejemplo cubre los pasos esenciales de “**cómo insertar formas**” y “**cómo agrupar formas**”, explica por qué cada línea existe y también aborda personalizaciones, casos límite y buenas prácticas.

A continuación, podrías explorar **cómo insertar imágenes**, **añadir texto dentro de formas agrupadas**, o **exportar el documento a PDF**—todo sigue el mismo patrón de usar `DocumentBuilder` y la manipulación de formas. Sigue experimentando; la API de Aspose es lo suficientemente rica como para manejar casi cualquier escenario de automatización de Word que imagines.

¡Feliz codificación, y no dudes en dejar un comentario si encuentras algún obstáculo!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Insertar formas en documentos Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Crear forma de grupo en documento Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Crear forma rectangular en Word usando C# – Guía paso a paso](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}