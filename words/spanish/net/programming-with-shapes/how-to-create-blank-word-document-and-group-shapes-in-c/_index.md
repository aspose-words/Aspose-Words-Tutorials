---
category: general
date: 2026-10-07
description: Crear un documento Word en blanco en C# y aprender a añadir una forma
  de rectángulo, insertar una forma de imagen y agrupar múltiples formas para informes
  dinámicos.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- insert image shape
- group multiple shapes
- add image to word
language: es
lastmod: 2026-10-07
og_description: Crea un documento Word en blanco en C# con Aspose.Words. Aprende a
  agregar una forma rectangular, insertar una forma de imagen y agrupar múltiples
  formas para documentos profesionales.
og_image_alt: Screenshot of a Word file showing a grouped rectangle and logo created
  with C#
og_title: Crear documento Word en blanco y agrupar formas en C# – guía paso a paso
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Create blank Word document in C# and learn to add rectangle shape,
    insert image shape, and group multiple shapes for dynamic reports.
  headline: How to create blank Word document and group shapes in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Cómo crear un documento Word en blanco y agrupar formas en C#
url: /es/net/programming-with-shapes/how-to-create-blank-word-document-and-group-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo crear un documento Word en blanco y agrupar formas en C#

Si necesitas **crear un documento Word en blanco** de forma programática, esta guía te muestra exactamente cómo hacerlo. Verás cómo **añadir una forma rectangular**, **insertar una forma de imagen** y **agrupar varias formas** para que se comporten como un solo objeto cuando **agregues una imagen a Word** más adelante.

Trabajar con archivos Word desde código puede parecer intimidante, pero Aspose.Words hace que el proceso sea sencillo. Al final de este tutorial tendrás un fragmento reutilizable en C# que genera un archivo Word limpio y vacío que contiene un rectángulo y un logotipo agrupados. Puedes incrustar el resultado en facturas, informes o cualquier flujo de trabajo de documentos automatizado.

## Requisitos previos

Antes de comenzar, asegúrate de tener:

* .NET 6.0 o posterior (el código también funciona con .NET Framework 4.7+).  
* Una licencia válida de Aspose.Words for .NET o una clave de evaluación gratuita.  
* Un archivo de imagen (p. ej., `logo.png`) colocado en una carpeta a la que puedas hacer referencia desde el código.  
* Visual Studio 2022 o cualquier IDE compatible con C#.

No se requieren paquetes NuGet adicionales más allá de `Aspose.Words`.

## Cómo crear un documento Word en blanco con Aspose.Words

El primer paso siempre es **crear un documento Word en blanco**. Este objeto alojará todas las formas posteriores.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// 1️⃣ Initialize a new empty document.
Document doc = new Document();

// 2️⃣ Prepare a DocumentBuilder – it simplifies adding content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` representa todo el archivo `.docx`. En este punto el archivo está vacío, lo que satisface el requisito de *crear un documento Word en blanco*.

## Crear un contenedor para agrupar varias formas

Agrupar formas te permite moverlas, rotarlas o cambiar su tamaño juntas. Aspose.Words proporciona la clase `GroupShape` para este propósito.

```csharp
// 3️⃣ Create a GroupShape that will hold our drawing objects.
GroupShape group = new GroupShape(doc)
{
    // Define the container’s position and size on the page.
    Bounds = new Rectangle(50, 50, 300, 200)
};

// Append the group to the first paragraph of the first section.
doc.FirstSection.Body.FirstParagraph.AppendChild(group);
```

El rectángulo `Bounds` determina dónde aparece el grupo en la página. Al colocar el grupo en el primer párrafo garantizas que el **crear documento Word en blanco** contendrá inmediatamente un contenedor visual.

## Cómo añadir una forma rectangular dentro del grupo

Un requisito común es **añadir una forma rectangular** como fondo o borde. El siguiente código crea un rectángulo y lo agrega al grupo definido previamente.

```csharp
// 4️⃣ Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width = 100,
    Height = 80,
    Left = 20,
    Top = 20,
    // Optional: give the rectangle a light gray fill.
    FillColor = Color.LightGray
};

// Add the rectangle to the group.
group.AppendChild(rectangle);
```

Como el rectángulo vive dentro del `GroupShape`, se moverá junto con cualquier otra forma que agregues después. Esta es la esencia de la funcionalidad **agrupar varias formas**.

## Cómo insertar una forma de imagen dentro del grupo

A continuación, **insertarás una forma de imagen** (el logotipo) y la colocarás junto al rectángulo. Esto demuestra el flujo de trabajo **agregar imagen a Word**.

```csharp
// 5️⃣ Create an image shape.
Shape picture = new Shape(doc, ShapeType.Image)
{
    Width = 80,
    Height = 80,
    Left = 150,
    Top = 30
};

// Load the image from disk. Replace the path with your actual image location.
picture.ImageData.SetImage(Image.FromFile(@"YOUR_DIRECTORY/logo.png"));

// Add the image shape to the same group.
group.AppendChild(picture);
```

El método `SetImage` lee el archivo e lo incrusta directamente en el documento Word, asegurando que la imagen persista incluso cuando el archivo fuente se mueva. Esto completa el paso **insertar forma de imagen** y finaliza el requisito **agregar imagen a Word**.

## Guardar el documento

Finalmente, persiste el archivo en disco. El archivo guardado contiene el documento en blanco, el rectángulo agrupado y el logotipo incrustado.

```csharp
// 6️⃣ Save the document with the grouped shapes.
doc.Save(@"YOUR_DIRECTORY/GroupShape.docx");
```

Cuando abras `GroupShape.docx` en Microsoft Word, verás un único grupo que incluye un rectángulo gris claro y el logotipo posicionados lado a lado. Seleccionar cualquier parte del grupo te permite mover o cambiar el tamaño de toda la colección, demostrando que las formas están efectivamente **agrupadas**.

## Ejemplo completo y ejecutable

A continuación tienes el programa completo que puedes copiar, pegar y ejecutar. Reemplaza `YOUR_DIRECTORY` con una ruta absoluta o relativa que exista en tu máquina.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a blank Word document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Create a GroupShape to hold the rectangle and image.
        GroupShape group = new GroupShape(doc)
        {
            Bounds = new Rectangle(50, 50, 300, 200)
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(group);

        // Step 3: Add a rectangle shape inside the group.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 100,
            Height = 80,
            Left = 20,
            Top = 20,
            FillColor = Color.LightGray
        };
        group.AppendChild(rectangle);

        // Step 4: Insert an image shape inside the group.
        Shape picture = new Shape(doc, ShapeType.Image)
        {
            Width = 80,
            Height = 80,
            Left = 150,
            Top = 30
        };
        picture.ImageData.SetImage(Image.FromFile(@"YOUR_DIRECTORY/logo.png"));
        group.AppendChild(picture);

        // Step 5: Save the document.
        doc.Save(@"YOUR_DIRECTORY/GroupShape.docx");
    }
}
```

### Resultado esperado

* Un archivo llamado `GroupShape.docx` ubicado en `YOUR_DIRECTORY`.  
* Al abrir el archivo en Word se muestra un único grupo visual que contiene un rectángulo gris a la izquierda y el `logo.png` a la derecha.  
* Seleccionar cualquier parte del grupo visual permite mover o cambiar el tamaño de toda la colección, confirmando que las formas están correctamente **agrupadas**.

## Preguntas frecuentes y manejo de casos límite

| Pregunta | Respuesta |
|---|---|
| **¿Puedo añadir más de dos formas al mismo grupo?** | Sí. Llama a `group.AppendChild(yourShape)` para cada `Shape` adicional. El grupo puede contener cualquier número de objetos de dibujo. |
| **¿Qué ocurre si falta el archivo de imagen?** | `SetImage` lanzará una `FileNotFoundException`. Envuelve la llamada en un bloque try‑catch y proporciona una alternativa (p. ej., una forma de marcador de posición). |
| **¿Necesito establecer `WrapType` para las formas?** | Por defecto las formas son inline. Si necesitas comportamiento flotante, establece `picture.WrapType = WrapType.Inline;` u otro modo de ajuste antes de agregar al grupo. |
| **¿Cómo afecta el tamaño del documento a los límites del grupo?** | El rectángulo `Bounds` se define en puntos (1 pt ≈ 1/72 in). Ajusta el tamaño si colocas el grupo en un diseño de página diferente (p. ej., A4 vs. Letter). |
| **¿Puedo reutilizar el mismo grupo en otro documento?** | Sí. Clona el grupo con `GroupShape cloned = (GroupShape)group.Clone(true);` e insértalo en otro `Document`. |

## Consejos profesionales

* **Reutiliza el `DocumentBuilder`** para añadir texto antes o después del grupo. Respeta automáticamente la posición actual del cursor.  
* **Establece `Shape.StrokeColor`** si necesitas un borde visible alrededor del rectángulo.  
* **Utiliza PNGs de alta resolución** para el logotipo y evitar la pixelación cuando

## ¿Qué deberías aprender a continuación?


Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Crear forma de grupo en un documento Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Crear forma rectangular en Word usando C# – Guía paso a paso](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Insertar imagen en línea en un documento Word usando Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}