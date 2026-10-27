---
category: general
date: 2026-10-23
description: Aprenda cómo insertar una elipse y cómo agregar una forma de rectángulo
  en Word usando Aspose.Words. Incluye mover el cursor a la forma y cómo crear una
  forma grupal.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert ellipse
- how to add rectangle
- move cursor to shape
- insert rectangle shape word
- how to create group shape
language: es
lastmod: 2026-10-23
og_description: Cómo insertar una elipse y cómo añadir una forma rectangular en Word
  con Aspose.Words. Sigue la guía paso a paso para mover el cursor a la forma y crear
  una forma grupal.
og_image_alt: Screenshot of a Word document showing a group shape containing a rectangle
  and an ellipse
og_title: Cómo insertar formas de elipse y rectángulo en un grupo de formas de Word
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Learn how to insert ellipse and how to add rectangle shape in Word
    using Aspose.Words. Includes move cursor to shape and how to create group shape.
  headline: How to insert ellipse and rectangle shapes inside a group shape with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Cómo insertar formas de elipse y rectángulo dentro de un grupo de formas con
  Aspose.Words
url: /es/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo insertar formas de elipse y rectángulo dentro de una forma de grupo con Aspose.Words

Si necesitas saber **cómo insertar una elipse** en un documento Word de forma programática, esta guía muestra el proceso completo. También verás **cómo agregar una forma de rectángulo**, aprenderás a **mover el cursor a la forma** y descubrirás **cómo crear una forma de grupo** que contiene varios objetos de dibujo.

La automatización de Word a menudo requiere una posición precisa de los objetos de dibujo. Al final de este tutorial podrás generar un archivo `.docx` que contiene un rectángulo y una elipse agrupados, listo para más estilos o exportación. No se requieren herramientas externas más allá de la biblioteca Aspose.Words para .NET y un entorno de desarrollo .NET.

## Requisitos previos

* .NET 6.0 o posterior instalado.
* Aspose.Words para .NET (paquete NuGet `Aspose.Words`) añadido a tu proyecto.
* Conocimientos básicos de la sintaxis de C# y Visual Studio (o cualquier IDE).

Estos requisitos garantizan que el código se compile sin configuración adicional.

## Cómo crear una forma de grupo en Word

Una forma de grupo actúa como un contenedor que te permite mover, rotar o formatear varias formas como una sola unidad. El siguiente código crea un grupo con un tamaño específico (300 × 200 puntos) y prepara el documento para operaciones de dibujo adicionales.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapeDemo
{
    static void Main()
    {
        // Create a new blank document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a group shape that will act as a container for other shapes.
        GroupShape group = builder.InsertGroupShape(300, 200);
        
        // The group shape is now part of the document.
        // Subsequent shape insertions will be placed inside this group.
```

*Por qué este paso es importante*: La forma de grupo define un sistema de coordenadas local. Todas las formas añadidas después de mover el cursor al grupo se posicionarán respecto al origen del grupo, lo que simplifica los cálculos de diseño.

## Cómo agregar una forma de rectángulo en Word

Ahora que el grupo existe, puedes **insertar una forma de rectángulo** dentro de él. El rectángulo servirá como fondo o como marcador visual para otro contenido.

```csharp
        // Move the cursor into the group so that the next shape is added to it.
        builder.MoveTo(group);
        
        // Insert a rectangle of width 100 points and height 50 points.
        builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

*Explicación*: `MoveTo(group)` indica al builder que el punto de inserción activo es la forma de grupo. Sin mover el cursor, `InsertShape` añadiría el rectángulo al cuerpo principal del documento en lugar del grupo.

## Cómo insertar una elipse

Con el rectángulo en su lugar, ahora puedes demostrar **cómo insertar una elipse**. La elipse se centrará dentro del mismo grupo, superponiéndose al rectángulo si lo deseas.

```csharp
        // Keep the cursor inside the same group.
        builder.MoveTo(group);
        
        // Insert an ellipse of width 80 points and height 80 points.
        builder.InsertShape(ShapeType.Ellipse, 80, 80);
```

*Por qué el cursor debe moverse*: Cada llamada a `InsertShape` respeta la ubicación actual del cursor. Volver a llamar a `MoveTo(group)` garantiza que la elipse también sea un hijo del grupo, preservando la jerarquía prevista.

## Mover el cursor a la forma antes de insertar objetos adicionales

Si necesitas agregar más formas más adelante, siempre **mueve el cursor a la forma** antes de cada inserción. Este patrón evita colocaciones accidentales fuera del grupo.

```csharp
        // Example: add a third shape, such as a line.
        builder.MoveTo(group);
        builder.InsertShape(ShapeType.Line, 150, 0);
```

*Consejo*: Reutilizar `MoveTo(group)` es barato y mejora la legibilidad del código. También facilita el mantenimiento futuro porque el contexto de inserción es explícito.

## Guardar el documento

Finalmente, guarda el documento en disco. El ejemplo guarda el archivo como `GroupShape.docx` en la carpeta que especifiques.

```csharp
        // Save the document to the desired location.
        document.Save(@"C:\Temp\GroupShape.docx");
    }
}
```

Cuando abras el archivo guardado en Microsoft Word, verás un único grupo que contiene un rectángulo y una elipse, ambos posicionados correctamente.

### Resultado esperado

* Un archivo `.docx` llamado `GroupShape.docx`.
* Dentro del documento, un objeto de dibujo agrupado con tamaño de 300 × 200 puntos.
* Dentro del grupo:
  * Un rectángulo (100 × 50 puntos) ubicado en el origen del grupo.
  * Una elipse (80 × 80 puntos) superpuesta al rectángulo.
  * Cualquier forma adicional que hayas añadido después de mover el cursor.

## Variaciones comunes y casos límite

| Situación | Enfoque recomendado |
|-----------|----------------------|
| **Diferentes tamaños de unidad** | Aspose.Words usa puntos (1 pt = 1/72 in). Convierte centímetros o pulgadas a puntos antes de llamar a `InsertShape`. |
| **Rotar formas dentro del grupo** | Después de insertar una forma, recupera su objeto `ShapeBase` y establece `ShapeBase.RotationAngle`. |
| **Agregar texto dentro de una forma** | Usa `ShapeBase.AppendChild(new Paragraph(document))` y luego agrega un `Run` con el texto deseado. |
| **Guardar como PDF en lugar de DOCX** | Llama a `document.Save("GroupShape.pdf", SaveFormat.Pdf);` – la jerarquía del grupo se conserva en la salida PDF. |

Estas variaciones demuestran que la misma lógica de **cómo insertar una elipse** puede adaptarse a muchos escenarios del mundo real.

## Consejos profesionales

* **Reutiliza la misma instancia de `DocumentBuilder`** – reduce la sobrecarga de memoria y mantiene el estado del documento consistente.
* **Valida las dimensiones de la forma** – anchuras o alturas extremadamente grandes pueden causar problemas de renderizado en versiones antiguas de Word.
* **Agrupa antes de aplicar estilos** – aplicar colores de relleno o estilos de línea al grupo después de agregar todos los hijos garantiza una apariencia uniforme.

## Conclusión

Ahora entiendes **cómo insertar una elipse** y **cómo agregar una forma de rectángulo** dentro de un contenedor agrupado en un documento Word usando Aspose.Words. Al mover consistentemente el **cursor a la forma** antes de cada inserción, mantienes una jerarquía limpia y evitas colocaciones accidentales. El ejemplo completo compila, se ejecuta y produce una forma agrupada que puede personalizarse o exportarse más adelante.

¿Listo para explorar más? Prueba combinar esta técnica con **cómo crear una forma de grupo** para diagramas complejos, o experimenta con **insertar forma de rectángulo en Word** junto a cuadros de texto para generar informes enriquecidos. ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Cómo crear una forma de rectángulo y formas de grupo en Word con Aspose.Words](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)
- [Cómo crear un documento Word en blanco y agregar una forma de elipse oculta en C#](/words/english/java/images-shapes/how-to-create-blank-word-document-and-add-a-hidden-ellipse-s/)
- [Cómo crear un docx con forma de grupo y agregar controles interactivos en C#](/words/english/java/images-shapes/how-to-create-group-shape-docx-and-add-interactive-controls/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}