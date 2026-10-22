---
category: general
date: 2026-10-04
description: Aprende a agrupar formas en Word usando C#. Esta guía muestra cómo insertar
  una forma de rectángulo, agrupar múltiples formas y crear un archivo de Word en
  blanco de forma programática.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- insert rectangle shape
- group multiple shapes
- append child to group
- create blank word file
language: es
lastmod: 2026-10-04
og_description: Agrupa formas en Word usando C#. Sigue esta guía paso a paso para
  insertar una forma rectangular, agrupar varias formas y crear un archivo Word en
  blanco con DocumentBuilder.
og_image_alt: Screenshot of grouped rectangle and ellipse shapes inside a Word document
og_title: Agrupa formas en Word con C# – tutorial completo de DocumentBuilder
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to group shapes in Word using C#. This guide shows how to
    insert rectangle shape, group multiple shapes, and create a blank Word file programmatically.
  headline: How to group shapes in Word with C# and DocumentBuilder
  type: TechArticle
- description: Learn how to group shapes in Word using C#. This guide shows how to
    insert rectangle shape, group multiple shapes, and create a blank Word file programmatically.
  name: How to group shapes in Word with C# and DocumentBuilder
  steps:
  - name: '**Create a blank Word file** – Starting with a clean document guarantees
      that no hidden formatting interferes with shape positioning.'
    text: '**Create a blank Word file** – Starting with a clean document guarantees
      that no hidden formatting interferes with shape positioning.'
  - name: '**Initialize DocumentBuilder** – `DocumentBuilder` abstracts low‑level
      node manipulation, letting you focus on layout.'
    text: '**Initialize DocumentBuilder** – `DocumentBuilder` abstracts low‑level
      node manipulation, letting you focus on layout.'
  - name: '**Insert individual shapes** – You first need separate objects (`insert
      rectangle shape` and an ellipse) before you can group them. Adjusting `Left`
      and `Top` ensures they appear side‑by‑side.'
    text: '**Insert individual shapes** – You first need separate objects (`insert
      rectangle shape` and an ellipse) before you can group them. Adjusting `Left`
      and `Top` ensures they appear side‑by‑side.'
  - name: '**Group multiple shapes** – By creating a `GroupShape` and using **append
      child to group**, you turn two independent drawings into a single logical unit.
      Moving or resizing the group will affect both children simultaneously.'
    text: '**Group multiple shapes** – By creating a `GroupShape` and using **append
      child to group**, you turn two independent drawings into a single logical unit.
      Moving or resizing the group will affect both children simultaneously.'
  - name: '**Save the document** – The final file, `GroupedShapes.docx`, can be opened
      in Microsoft Word to verify that the rectangle and ellipse are indeed grouped
      (select one, and both move together).'
    text: '**Save the document** – The final file, `GroupedShapes.docx`, can be opened
      in Microsoft Word to verify that the rectangle and ellipse are indeed grouped
      (select one, and both move together).'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shape handling
- DocumentBuilder
title: Cómo agrupar formas en Word con C# y DocumentBuilder
url: /es/java/images-shapes/how-to-group-shapes-in-word-with-c-and-documentbuilder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo agrupar formas en Word con C# y DocumentBuilder

Si necesita **agrupar formas en Word** desde una aplicación C#, este tutorial le muestra exactamente cómo hacerlo. Verá cómo *insertar una forma rectangular*, combinar varios dibujos en un solo grupo y, finalmente, **crear un archivo Word en blanco** que contenga los objetos agrupados.

Trabajar con formas es un requisito común al generar informes, facturas o plantillas personalizadas de forma programática. Al final de esta guía tendrá un fragmento de código reutilizable que podrá insertar en cualquier proyecto .NET que haga referencia a Aspose.Words.

## Lo que aprenderá

- Crear un documento Word en blanco desde cero.  
- Insertar una forma rectangular y una elipse usando `DocumentBuilder`.  
- **Agrupar múltiples formas** en un `GroupShape`.  
- Usar **append child to group** para construir la jerarquía.  
- Guardar el archivo en disco y verificar el resultado.

No se requiere experiencia previa con Aspose.Words, pero debería tener una comprensión básica de C# y el desarrollo .NET.

## Requisitos previos

| Requisito | Razón |
|-------------|--------|
| .NET 6.0 o posterior | Proporciona el tiempo de ejecución para el código C#. |
| Aspose.Words for .NET (última versión) | Proporciona `Document`, `DocumentBuilder` y clases de formas. |
| Un IDE como Visual Studio 2022 (o VS Code) | Facilita compilar y ejecutar el ejemplo. |
| Permiso de escritura en una carpeta de su máquina | Necesario para la llamada `doc.save`. |

Instale Aspose.Words vía NuGet:

```bash
dotnet add package Aspose.Words
```

---

## Agrupar formas en Word – guía paso a paso

A continuación se muestra el programa completo y ejecutable. Cada sección se explica en detalle para que entienda **por qué** el código está escrito de esta manera, no solo **qué** hace.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

namespace WordShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // -------------------------------------------------
            // Step 1: create a blank Word file
            // -------------------------------------------------
            // The Document constructor creates an empty .docx container.
            Document doc = new Document();

            // -------------------------------------------------
            // Step 2: initialize DocumentBuilder to add content
            // -------------------------------------------------
            // DocumentBuilder is the high‑level API for inserting text,
            // images, tables, and shapes into the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // -------------------------------------------------
            // Step 3: insert individual shapes
            // -------------------------------------------------
            // Insert a rectangle shape – this demonstrates the
            // "insert rectangle shape" keyword in practice.
            Shape rectangle = builder.InsertShape(
                ShapeType.Rectangle,   // shape type
                100,                  // width in points
                50);                  // height in points

            // Position the rectangle a little away from the left margin.
            rectangle.Left = 100;   // points from the left edge
            rectangle.Top = 100;    // points from the top of the page

            // Insert an ellipse shape to accompany the rectangle.
            Shape ellipse = builder.InsertShape(
                ShapeType.Ellipse,
                80,
                80);
            ellipse.Left = rectangle.Left + rectangle.Width + 20; // place right of rectangle
            ellipse.Top = rectangle.Top; // align tops

            // -------------------------------------------------
            // Step 4: create a GroupShape and append children
            // -------------------------------------------------
            // A GroupShape acts like a container; any shape added to it
            // moves together with the group. This fulfills the
            // "group multiple shapes" requirement.
            GroupShape group = builder.InsertGroupShape();

            // The "append child to group" operation builds the hierarchy.
            group.AppendChild(rectangle);
            group.AppendChild(ellipse);

            // Optional: give the group a name for later reference.
            group.Name = "MyShapeGroup";

            // -------------------------------------------------
            // Step 5: save the document containing the grouped shapes
            // -------------------------------------------------
            string outputPath = @"GroupedShapes.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Por qué cada paso es importante

1. **Crear un archivo Word en blanco** – Comenzar con un documento limpio garantiza que ningún formato oculto interfiera con la posición de las formas.  
2. **Inicializar DocumentBuilder** – `DocumentBuilder` abstrae la manipulación de nodos de bajo nivel, permitiéndole centrarse en el diseño.  
3. **Insertar formas individuales** – Primero necesita objetos separados (`insert rectangle shape` y una elipse) antes de poder agruparlos. Ajustar `Left` y `Top` asegura que aparezcan uno al lado del otro.  
4. **Agrupar múltiples formas** – Al crear un `GroupShape` y usar **append child to group**, convierte dos dibujos independientes en una única unidad lógica. Mover o redimensionar el grupo afectará a ambos hijos simultáneamente.  
5. **Guardar el documento** – El archivo final, `GroupedShapes.docx`, puede abrirse en Microsoft Word para verificar que el rectángulo y la elipse están realmente agrupados (seleccione uno y ambos se moverán juntos).

### Resultado esperado

Abra `GroupedShapes.docx` en Microsoft Word:

- Verá un rectángulo y una elipse colocados uno al lado del otro.  
- Seleccionar cualquiera de las formas resaltará ambas, confirmando que pertenecen al mismo grupo.  
- El grupo puede arrastrarse, redimensionarse o formatearse como un solo objeto.

![Diagrama del rectángulo y la elipse agrupados dentro de un documento Word](https://example.com/grouped-shapes.png){: .center-image alt="Diagrama del rectángulo y la elipse agrupados dentro de un documento Word"}

*La captura de pantalla ilustra las formas agrupadas finales.*

---

## Insertar forma rectangular – personalizando tamaño y estilo

Si necesita un rectángulo con un color de relleno o borde específico, modifique el objeto `Shape` después de la inserción:

```csharp
rectangle.FillColor = System.Drawing.Color.LightBlue;
rectangle.StrokeColor = System.Drawing.Color.DarkBlue;
rectangle.LineWidth = 2.0; // points
```

Estas propiedades forman parte de la clase `Shape`, y funcionan para cualquier tipo de forma, no solo para rectángulos. Ajustar el estilo antes de **append child to group** garantiza que el grupo herede las propiedades visuales que establezca.

---

## Agrupar múltiples formas – manejando más de dos objetos

El ejemplo agrupa un rectángulo y una elipse, pero puede agregar cualquier número de formas:

```csharp
// Create additional shapes as needed
Shape triangle = builder.InsertShape(ShapeType.Triangle, 60, 60);
triangle.Left = ellipse.Left + ellipse.Width + 20;
triangle.Top = ellipse.Top;

// Append the new shape to the existing group
group.AppendChild(triangle);
```

**Consejo profesional:** Después de haber creado un grupo complejo, puede bloquear su diseño para evitar cambios accidentales:

```csharp
group.LockAspectRatio = true;
group.RelativeHorizontalPosition = RelativeHorizontalPosition.Margin;
group.RelativeVerticalPosition = RelativeVerticalPosition.Margin;
```

---

## Append child to group – el orden importa

El orden en que llama a `AppendChild` define el orden Z (qué forma aparece encima). En el ejemplo, el rectángulo se agrega primero, luego la elipse, por lo que la elipse se superpone al rectángulo si se intersectan. Reordenar es tan simple como llamar a `RemoveChild` y volver a agregar:

```csharp
group.RemoveChild(ellipse);
group.AppendChild(ellipse); // now ellipse is on top
```

---

## Crear archivo Word en blanco – método auxiliar reutilizable

Si su aplicación necesita frecuentemente un documento nuevo, encapsule la lógica de creación:

```csharp
/// <summary>
/// Returns a new empty Document with a single section.
/// </summary>
static Document CreateBlankWordFile()
{
    Document emptyDoc = new Document();
    // Optionally set default page size, margins, etc.
    emptyDoc.FirstSection.PageSetup.PageWidth = 595;  // A4 width in points
    emptyDoc.FirstSection.PageSetup.PageHeight = 842; // A4 height in points
    return emptyDoc;
}
```

Luego puede reemplazar la línea `new Document()` en el programa principal con `CreateBlankWordFile()`. Esto demuestra el concepto de **create blank word file** de manera reutilizable.

---

## Errores comunes y cómo evitarlos

| Problema | Por qué ocurre | Solución |
|-------|----------------|-----|
| Las formas aparecen fuera de la página | Los valores predeterminados de `Left`/`Top` son 0, lo que coloca la forma en el margen. | Establezca explícitamente `Left` y `Top` después de la inserción. |
| El grupo pierde formato | Cambiar una forma hija después de haberla añadido a un grupo puede romper el diseño del grupo. | Aplique todas las propiedades visuales **antes** de llamar a `AppendChild`. |
| El archivo guardado está vacío | `DocumentBuilder` nunca se usó para agregar un nodo, o `doc.Save` se llamó en una instancia diferente de `Document`. | Verifique que está guardando el mismo `Document` que construyó. |
| Advertencias de compatibilidad en Word | Uso de características de forma más recientes no compatibles |  |

## ¿Qué debería aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarle a dominar características adicionales de la API y explorar enfoques de implementación alternativos en sus propios proyectos.

- [Crear forma de grupo en documento Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insertar formas en documentos Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Crear forma rectangular en Word usando C# – Guía paso a paso](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}