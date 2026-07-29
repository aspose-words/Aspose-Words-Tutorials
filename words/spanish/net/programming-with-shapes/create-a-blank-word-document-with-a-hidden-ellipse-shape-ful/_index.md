---
category: general
date: 2026-07-29
description: Crea un documento de Word en blanco y aprende cómo ocultar una forma,
  crear un objeto oculto y crear una forma elíptica usando Aspose.Words en C#. Código
  paso a paso incluido.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- blank word document
- how to hide shape
- create hidden object
- create ellipse shape
language: es
lastmod: 2026-07-29
og_description: Crea un documento de Word en blanco y oculta la forma al instante.
  Aprende a crear un objeto oculto y dibujar una forma elíptica usando Aspose.Words
  en C#.
og_image_alt: Hidden ellipse shape inserted into a blank Word document
og_title: Crear un documento de Word en blanco con una forma elíptica oculta – Tutorial
  de C#
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Create a blank word document and learn how to hide shape, create hidden
    object, and create ellipse shape using Aspose.Words in C#. Step‑by‑step code included.
  headline: Create a Blank Word Document with a Hidden Ellipse Shape – Full C# Guide
  type: TechArticle
- description: Create a blank word document and learn how to hide shape, create hidden
    object, and create ellipse shape using Aspose.Words in C#. Step‑by‑step code included.
  name: Create a Blank Word Document with a Hidden Ellipse Shape – Full C# Guide
  steps:
  - name: What if the target Word version doesn’t support hidden shapes?
    text: The `Hidden` flag is part of the Office Open XML spec and is respected by
      Word 2007+ and LibreOffice. Older formats (e.g., `.doc`) ignore the flag, so
      always save as `.docx` when you need reliable hiding.
  - name: Can I hide other types of objects (pictures, tables)?
    text: Yes. Any node derived from `Shape`—including pictures, text boxes, and even
      SmartArt—exposes the `Hidden` property. Just set it to `true` before insertion.
  - name: Does hiding a shape affect document performance?
    text: Negligibly. The shape is stored as XML markup, and Word skips rendering
      hidden objects during layout. If you embed many hidden objects, the file size
      grows, but rendering stays fast.
  - name: How does this differ from using a bookmark or comment as a marker?
    text: Bookmarks are invisible by design, but they’re meant for navigation, not
      visual placeholders. Comments appear in the margin. A hidden shape gives you
      a visual object (size, position) that you can later reveal or manipulate, which
      is handy for templating scenarios.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word Automation
- Shapes
title: Crear un documento Word en blanco con una forma elíptica oculta – Guía completa
  de C#
url: /es/net/programming-with-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape-ful/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear un documento Word en blanco con una forma de elipse oculta – Guía completa en C#

¿Alguna vez necesitaste crear un **documento Word en blanco** y luego ocultar una forma dentro de él? Tal vez estés generando una plantilla donde ciertos marcadores deben permanecer invisibles hasta un paso posterior. En este tutorial recorreremos exactamente **cómo ocultar una forma**, cómo **crear un objeto oculto**, e incluso cómo **crear una forma de elipse** usando Aspose.Words para .NET. Al final tendrás un fragmento de C# listo para ejecutar que produce un archivo DOCX que contiene una elipse invisible.

## Lo que aprenderás

- Inicializar un nuevo documento Word en blanco con Aspose.Words.  
- Construir una forma de elipse, establecer sus dimensiones y posicionarla en la página.  
- Marcar la forma como oculta para que nunca aparezca en pantalla ni en la impresión.  
- Guardar el resultado en disco y verificar que el objeto oculto sea realmente invisible.  

No se requieren bibliotecas externas más allá de Aspose.Words, y el código funciona con la versión 24.10 o superior (la propiedad `Hidden` se introdujo en esa versión). ¡Comencemos!

![Diagram of a hidden ellipse inside a blank Word document](https://example.com/hidden-ellipse.png "Hidden ellipse shape inserted into a blank Word document")

## Crear un documento Word en blanco e insertar una forma de elipse oculta

El primer paso es crear un documento totalmente nuevo. Piensa en `Document` como un lienzo vacío; `DocumentBuilder` es tu pincel.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document and a DocumentBuilder to edit it.
Document document = new Document();               // This is your blank word document.
DocumentBuilder builder = new DocumentBuilder(document);
```

> **¿Por qué comenzar con un documento en blanco?**  
> Un lienzo limpio garantiza que ningún contenido preexistente interfiera con la forma oculta que estás a punto de añadir. Además, hace que el ejemplo sea más fácil de copiar y pegar en cualquier proyecto.

## Cómo ocultar una forma: establecer la propiedad Hidden

Aspose.Words 24.10 introdujo la bandera `Hidden` en `Shape`. Cuando se establece en `true`, Word trata la forma como un comentario: completamente invisible en la interfaz y al imprimir.

```csharp
// Step 2: Create an ellipse shape and set its size and position.
Shape ellipseShape = new Shape(document, ShapeType.Ellipse);
ellipseShape.Width = 100;   // Width in points
ellipseShape.Height = 80;   // Height in points
ellipseShape.Left = 150;    // Horizontal offset from the left margin
ellipseShape.Top = 150;     // Vertical offset from the top margin

// Step 3: Hide the shape so it does not appear when the document is viewed or printed.
ellipseShape.Hidden = true;   // This is the key to "how to hide shape"
```

> **Consejo profesional:** Si más adelante necesitas revelar la forma de forma programática, simplemente cambia `ellipseShape.Hidden = false;` y vuelve a guardar el documento.

## Crear objeto oculto: insertar la forma en el documento

Ahora que la elipse está preparada y oculta, la insertamos en la posición actual del cursor del builder. La posición del builder por defecto es el inicio del primer párrafo, lo cual es perfecto para un documento en blanco.

```csharp
// Step 4: Insert the hidden shape into the document at the current builder position.
builder.InsertNode(ellipseShape);
```

> **¿Qué pasa si necesitas la forma en una página específica?**  
> Mueve el builder a la página deseada primero (`builder.MoveToDocumentEnd();` o `builder.MoveToPage(pageNumber);`) antes de llamar a `InsertNode`.

## Guardar el documento que contiene la forma oculta

Finalmente, escribe el archivo en disco. La salida será un DOCX estándar que cualquier procesador de Word puede abrir—excepto que la elipse permanecerá invisible.

```csharp
// Step 5: Save the document containing the hidden shape.
document.Save("YOUR_DIRECTORY/HiddenShape.docx");
```

> **Salida esperada:** Abre `HiddenShape.docx` en Microsoft Word. No verás ningún gráfico, pero el tamaño del archivo será ligeramente mayor que el de un documento verdaderamente vacío porque la elipse oculta se almacena en el XML.

## Verificar la elipse oculta programáticamente (opcional)

Si deseas comprobar que la forma está realmente oculta, puedes cargar el archivo guardado e inspeccionar la propiedad `Hidden` de la forma:

```csharp
Document loaded = new Document("YOUR_DIRECTORY/HiddenShape.docx");
Shape loadedShape = (Shape)loaded.GetChild(NodeType.Shape, 0, true);
Console.WriteLine($"Is shape hidden? {loadedShape.Hidden}"); // Should print True
```

Ejecutar este fragmento imprime `True`, confirmando que el objeto oculto sobrevivió al ciclo guardar‑cargar.

## Casos límite y preguntas frecuentes

### ¿Qué ocurre si la versión de Word objetivo no admite formas ocultas?

La bandera `Hidden` forma parte de la especificación Office Open XML y es respetada por Word 2007+ y LibreOffice. Los formatos más antiguos (p. ej., `.doc`) ignoran la bandera, por lo que siempre debes guardar como `.docx` cuando necesites un ocultamiento fiable.

### ¿Puedo ocultar otros tipos de objetos (imágenes, tablas)?

Sí. Cualquier nodo derivado de `Shape`—incluyendo imágenes, cuadros de texto e incluso SmartArt—expone la propiedad `Hidden`. Simplemente establécela en `true` antes de la inserción.

### ¿Ocultar una forma afecta el rendimiento del documento?

De forma insignificante. La forma se almacena como marcado XML, y Word omite renderizar los objetos ocultos durante el diseño. Si insertas muchas formas ocultas, el tamaño del archivo crecerá, pero la renderización seguirá siendo rápida.

### ¿En qué se diferencia esto de usar un marcador o un comentario como indicador?

Los marcadores son invisibles por diseño, pero están pensados para la navegación, no como marcadores visuales. Los comentarios aparecen en el margen. Una forma oculta te brinda un objeto visual (tamaño, posición) que puedes revelar o manipular más adelante, lo cual es útil en escenarios de plantillas.

## Ejemplo completo en funcionamiento

A continuación se muestra el programa completo, listo para copiar y pegar. Incluye todas las directivas `using`, la creación de la elipse oculta y un paso de verificación.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class HiddenEllipseDemo
{
    static void Main()
    {
        // 1️⃣ Create a blank word document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Build the ellipse shape.
        Shape ellipse = new Shape(doc, ShapeType.Ellipse)
        {
            Width = 100,
            Height = 80,
            Left = 150,
            Top = 150,
            Hidden = true               // ← how to hide shape
        };

        // 3️⃣ Insert the hidden shape.
        builder.InsertNode(ellipse);

        // 4️⃣ Save the file.
        string outPath = "HiddenEllipse.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}");

        // 5️⃣ Optional: Verify that the shape is hidden.
        Document loaded = new Document(outPath);
        Shape loadedEllipse = (Shape)loaded.GetChild(NodeType.Shape, 0, true);
        Console.WriteLine($"Is the ellipse hidden? {loadedEllipse.Hidden}");
    }
}
```

Ejecutar el programa crea `HiddenEllipse.docx` en la carpeta de ejecución. Ábrelo—verás una página en blanco perfectamente normal, pero la elipse oculta vive silenciosamente dentro.

## Resumen

Hemos cubierto cómo **crear un documento Word en blanco**, **ocultar una forma**, **crear un objeto oculto** y **crear una forma de elipse**, todo con unas pocas líneas de C#. La lección clave es la propiedad `Hidden` en `Shape`, que convierte cualquier elemento visual en un marcador invisible sin romper la compatibilidad con Word.

## ¿Qué sigue?

- **Estilizar la forma oculta** (color de relleno, estilo de línea) para que, cuando la reveles más adelante, tenga exactamente el aspecto deseado.  
- **Combinar formas ocultas con marcadores** para construir plantillas dinámicas que puedan activarse o desactivarse.  
- **Explorar otros tipos de forma**—rectángulos, flechas o incluso rutas SVG personalizadas—cambiando `ShapeType.Ellipse`.  

Siéntete libre de experimentar: cambia el tamaño, mueve la posición o inserta múltiples elipses ocultas. El mismo patrón funciona para cualquier forma de Aspose.Words que necesites mantener fuera de la vista.

Si encuentras algún problema o tienes ideas para ampliar este patrón, deja un comentario abajo. ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}