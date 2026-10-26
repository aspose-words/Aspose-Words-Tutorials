---
category: general
date: 2026-10-26
description: Crea un documento Word en blanco en C# y aprende a insertar un grupo
  de formas, luego agrega una forma rectangular al grupo. Esta guía cubre cómo agrupar
  múltiples formas paso a paso.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group multiple shapes
- insert rectangle shape
- how to insert group
- how to add rectangle
language: es
lastmod: 2026-10-26
og_description: Crea un documento Word en blanco en C# y observa cómo insertar un
  grupo, luego agrega una forma rectangular. Domina la agrupación de múltiples formas
  con un ejemplo de código completo.
og_image_alt: Screenshot showing a blank Word document with a grouped rectangle shape
og_title: Crear documento Word en blanco y agrupar múltiples formas – tutorial de
  C#
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Create a blank Word document in C# and learn how to insert a group
    shape, then add a rectangle shape to the group. This guide covers group multiple
    shapes step‑by‑step.
  headline: How to create blank Word document and group multiple shapes
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Cómo crear un documento Word en blanco y agrupar múltiples formas
url: /es/java/images-shapes/how-to-create-blank-word-document-and-group-multiple-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo crear un documento Word en blanco y agrupar varias formas

Si necesitas **crear un documento Word en blanco** de forma programática, este tutorial te muestra exactamente cómo. Verás cómo insertar una forma de grupo y luego **agregar un rectángulo** a ese grupo, cubriendo todo el flujo de trabajo desde un documento vacío hasta un dibujo agrupado.

Trabajar con archivos Word a menudo implica organizar varios dibujos juntos—piensa en un diagrama compuesto de múltiples formas. Al final de esta guía podrás **agrupar varias formas**, insertar una **forma de rectángulo**, y comprender **cómo insertar un grupo** y **cómo agregar un rectángulo** de manera limpia y reutilizable.

## Qué necesitarás

* .NET 6.0 o posterior (el código también funciona con .NET Framework 4.6+)
* Paquete NuGet **Aspose.Words for .NET** (`Install-Package Aspose.Words`)
* Un conocimiento básico de C# y del IDE Visual Studio (cualquier IDE funciona)

> **Consejo profesional:** Aspose.Words se ejecuta completamente sin conexión; no necesitas una conexión a internet después de que el paquete esté instalado.

## Paso 1: Crear un documento Word en blanco

La primera operación es instanciar un objeto `Document` vacío. Este objeto representa el **documento Word en blanco** que luego enriquecerás con formas.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1 – create a new blank Word document
        Document doc = new Document();               // <-- blank document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Por qué es importante:* Un `Document` sin secciones ni párrafos sigue siendo un archivo .docx válido. Comenzar desde una hoja limpia garantiza que ningún formato oculto interfiera con las formas que agregarás más adelante.

## Paso 2: Insertar una forma de grupo (cómo insertar un grupo)

Una **forma de grupo** actúa como un contenedor que puede contener otros objetos de dibujo. En Aspose.Words la creas con `InsertGroupShape`.

```csharp
        // Step 2 – insert a group shape that will hold other shapes
        GroupShape group = builder.InsertGroupShape();   // <-- container for shapes
```

*¿Por qué usar un grupo?* Agrupar te permite mover, rotar o cambiar el tamaño de varias formas como una sola unidad. Esto es esencial para diagramas donde los elementos deben permanecer alineados.

## Paso 3: Insertar una forma de rectángulo (insertar forma de rectángulo)

Ahora agrega un rectángulo al documento. El método `InsertShape` devuelve un objeto `Shape` que luego puedes adjuntar al grupo.

```csharp
        // Step 3 – create a rectangle shape with specific dimensions
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50); // width=100pt, height=50pt
```

*¿Por qué un rectángulo?* Los rectángulos son el bloque de construcción más común para diagramas de flujo, maquetas de UI y gráficos de marcador de posición. Las dimensiones se expresan en puntos (1 pt ≈ 1/72 pulgada).

## Paso 4: Agregar el rectángulo al grupo (cómo agregar un rectángulo)

Una forma creada con `InsertShape` reside directamente en el cuerpo del documento. Para que forme parte del grupo, llama a `AppendChild` en el `GroupShape`.

```csharp
        // Step 4 – add the rectangle to the previously created group
        group.AppendChild(rectangle);   // <-- rectangle now belongs to the group
```

*¿Qué ocurre internamente?* `AppendChild` mueve el nodo del rectángulo de la historia principal del documento a la colección interna del grupo, preservando su tamaño y posición respecto al origen del grupo.

## Paso 5: Guardar el documento

Finalmente, escribe el archivo en disco. Puedes abrir el `.docx` resultante en Microsoft Word para ver el rectángulo agrupado.

```csharp
        // Step 5 – save the document to a file
        doc.Save("GroupedShapeExample.docx");
    }
}
```

> **Caso límite:** Si planeas agregar más formas (p. ej., círculos, líneas) al mismo grupo, repite **Paso 3** y **Paso 4** para cada nueva forma antes de guardar. El grupo ajustará automáticamente su cuadro delimitador para abarcar todos los hijos.

## Cómo agrupar varias formas – ampliando el ejemplo

A continuación hay un fragmento rápido que agrega una segunda forma (una elipse) al mismo grupo, demostrando **agrupar varias formas** en un solo documento.

```csharp
        // Additional shape: an ellipse
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 40);
        group.AppendChild(ellipse);   // now the group contains rectangle + ellipse
```

Cuando abras `GroupedShapeExample.docx`, verás que el rectángulo y la elipse se mueven juntos al seleccionar el grupo en Word.

## Preguntas frecuentes y solución de problemas

| Pregunta | Respuesta |
|----------|-----------|
| **¿Necesito una licencia para Aspose.Words?** | Una evaluación gratuita funciona sin licencia, pero agrega una marca de agua. Para producción, aplica una licencia para eliminar la marca de agua y desbloquear el rendimiento completo. |
| **¿Puedo posicionar las formas con precisión?** | Sí. Después de insertar una forma puedes establecer las propiedades `Shape.Left`, `Shape.Top`, `Shape.Width` y `Shape.Height`. |
| **¿Qué pasa si el rectángulo desaparece después de guardar?** | Asegúrate de llamar a `group.AppendChild(rectangle)` *después* de insertar el rectángulo. Primero agregar la forma al cuerpo del documento y luego moverla al grupo es necesario. |
| **¿Es posible agrupar formas en diferentes secciones?** | No. Todas las formas en un grupo deben pertenecer a la misma historia (sección). Crea grupos separados por sección si es necesario. |

## Resumen

Ahora sabes cómo **crear un documento Word en blanco**, **insertar un grupo**, **agregar un rectángulo**, y **agrupar varias formas** usando Aspose.Words para .NET. El ejemplo completo y ejecutable anterior puede copiarse en una aplicación de consola y ejecutarse de inmediato.

## Próximos pasos

* Experimenta con tamaños y colores de **insertar forma de rectángulo** (`rectangle.FillColor = Color.LightBlue;`).  
* Explora otros tipos de forma (`ShapeType.Polygon`, `ShapeType.Line`) para enriquecer tus diagramas.  
* Aprende a convertir el `.docx` final a PDF (`doc.Save("output.pdf");`) para distribución.  
* Profundiza en **cómo agregar un rectángulo** a documentos existentes que ya contienen texto—usa `DocumentBuilder.MoveTo` para posicionar el grupo donde lo necesites.

Siéntete libre de adaptar el código a tus propias necesidades de informes o generación de diagramas. ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Cómo crear un documento Word en blanco y agrupar formas en C#](/words/english/net/programming-with-shapes/how-to-create-blank-word-document-and-group-shapes-in-c/)
- [Cómo agrupar formas en Word y agregar formas a un documento Word](/words/english/net/programming-with-shapes/how-to-group-shapes-in-word-and-add-shapes-to-word-document/)
- [Cómo crear una forma de rectángulo y agrupar formas en Word con Aspose.Words](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}