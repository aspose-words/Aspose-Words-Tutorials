---
category: general
date: 2026-10-20
description: Ocultar/Mostrar una forma con la nueva propiedad `Hidden` usando Aspose.Words
  para C#. Aprende cómo alternar la visibilidad de la forma, manejar casos límite
  y guardar el resultado.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- Hide/Show a Shape with the new `Hidden` prop
- Aspose.Words hide shape
- C# shape hidden property
- Word document shape visibility
- programmatically hide shape
language: es
lastmod: 2026-10-20
og_description: Oculta/ muestra una forma con la nueva propiedad `Hidden` usando Aspose.Words
  para C#. Domina el cambio de visibilidad de formas y evita errores comunes.
og_image_alt: Screenshot of a Word document where a shape is hidden using the Hidden
  property
og_title: Ocultar/Mostrar una forma con la nueva propiedad `Hidden` en Aspose.Words
  (C#)
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Hide/Show a Shape with the new `Hidden` prop using Aspose.Words for
    C#. Learn how to toggle shape visibility, handle edge cases, and save the result.
  headline: Hide/Show a Shape with the new `Hidden` prop in Aspose.Words for C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Ocultar/Mostrar una forma con la nueva propiedad `Hidden` en Aspose.Words para
  C#
url: /es/net/programming-with-shapes/hide-show-a-shape-with-the-new-hidden-prop-in-aspose-words-f/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ocultar/Mostrar una Forma con la nueva propiedad `Hidden` en Aspose.Words para C#

Si necesitas **Ocultar/Mostrar una Forma con la nueva propiedad `Hidden`** en un documento Word, esta guía te muestra exactamente cómo hacerlo con Aspose.Words para .NET. Ya sea que estés generando informes, creando plantillas o limpiando documentos importados, controlar la visibilidad de las formas programáticamente te ahorra la edición manual.

En este tutorial aprenderás a cargar un documento, localizar una forma, alternar la propiedad `Hidden` y guardar el archivo modificado. Los pasos también cubren variaciones comunes, como manejar múltiples formas y tratar con gráficos en línea versus flotantes.

## Requisitos previos

Antes de comenzar, asegúrate de tener:

* .NET 6.0 (o posterior) instalado – Aspose.Words es compatible con .NET Standard 2.0 y .NET Core.  
* Una copia con licencia de **Aspose.Words for .NET** (la versión de prueba gratuita sirve para explorar).  
* Un IDE como Visual Studio 2022 o Visual Studio Code.  
* Un documento Word (`input.docx`) que contenga al menos una forma (por ejemplo, una imagen, SmartArt o un lienzo de dibujo).

## Paso 1: Cargar el documento Word

La primera operación es crear un objeto `Document` que represente el archivo .docx en disco.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*Por qué este paso es importante*: `Document` es el punto de entrada para todas las operaciones de Aspose.Words. Cargar el archivo en memoria te brinda acceso completo a su árbol de nodos, incluidas las formas.

## Paso 2: Obtener la forma objetivo

Para alternar la visibilidad debes obtener una referencia al nodo de forma. El ejemplo a continuación recupera la primera forma del documento, pero puedes adaptar la lógica para localizar formas por nombre, tipo o índice.

```csharp
// Get the first Shape node in the document tree
Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

if (shape == null)
{
    throw new InvalidOperationException("No shape was found in the document.");
}
```

*Por qué este paso es importante*: `GetChild` con `true` realiza una búsqueda profunda, asegurando que encuentres formas incluso cuando están anidadas dentro de tablas o encabezados. Verificar `null` evita una `NullReferenceException` cuando el documento no contiene formas.

## Paso 3: Ocultar la forma con la propiedad `Hidden`

Aspose.Words introdujo la propiedad `Hidden` para controlar si una forma se renderiza o se imprime. Asignarla a `true` oculta la forma; asignarla a `false` vuelve a hacerla visible.

```csharp
// Hide the shape so it will not appear in the rendered document
shape.Hidden = true;
```

Si necesitas **mostrar** una forma previamente oculta, simplemente asigna `false`:

```csharp
// Show the shape again
shape.Hidden = false;
```

*Por qué este paso es importante*: La propiedad `Hidden` funciona tanto para formas flotantes como en línea, y se integra con el formato nativo “Hidden” de Word. Este enfoque es más fiable que eliminar la forma porque el nodo permanece en el árbol del documento, preservando el diseño y las referencias.

## Paso 4: Guardar el documento modificado

Después de ajustar la visibilidad, escribe los cambios en un nuevo archivo (o sobrescribe el original si lo deseas).

```csharp
// Save the document with the updated shape visibility
doc.Save("YOUR_DIRECTORY/ShapeHidden.docx");
```

*Por qué este paso es importante*: `Save` serializa el árbol de nodos en memoria en un paquete .docx que Word puede abrir. La bandera oculta se persiste, de modo que al abrir el archivo en Microsoft Word la forma se mostrará según la configuración de `Hidden`.

## Ejemplo completo y ejecutable

Unir todos los pasos te brinda un programa autónomo que puedes copiar, compilar y ejecutar.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class HideShowShapeExample
{
    static void Main()
    {
        // 1. Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Retrieve the first shape in the document
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            Console.WriteLine("No shape found. Exiting.");
            return;
        }

        // 3. Toggle the Hidden property
        // Hide the shape
        shape.Hidden = true;
        // To show the shape again, uncomment the following line:
        // shape.Hidden = false;

        // 4. Save the modified document
        doc.Save("YOUR_DIRECTORY/ShapeHidden.docx");

        Console.WriteLine("Document saved. Shape hidden = " + shape.Hidden);
    }
}
```

**Salida esperada** al ejecutar el programa:

```
Document saved. Shape hidden = True
```

Abrir `ShapeHidden.docx` en Microsoft Word muestra el documento sin la forma objetivo. Si estableces `shape.Hidden = false;` antes de guardar, la forma reaparecerá.

## Manejo de múltiples formas

El ejemplo anterior funciona para una sola forma. Los documentos del mundo real a menudo contienen muchos gráficos. Usa un bucle para ocultar o mostrar todas las formas que cumplan una condición (por ejemplo, un nombre o tipo específico).

```csharp
// Hide every picture shape in the document
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    if (s.ShapeType == ShapeType.Image)
    {
        s.Hidden = true; // hide picture
    }
}
doc.Save("YOUR_DIRECTORY/AllPicturesHidden.docx");
```

*Consejo*: Filtrar por `ShapeType` evita ocultar inadvertidamente elementos decorativos como cuadros de texto o SmartArt.

## Casos límite y buenas prácticas

| Situación | Manejo recomendado |
|-----------|--------------------|
| **La forma está dentro de un encabezado/pie de página** | Recupera primero el nodo de encabezado/pie y luego llama a `GetChild(NodeType.Shape, …)` sobre ese sub‑documento. |
| **El documento no contiene formas** | Siempre verifica `null` después de `GetChild` o comprueba `doc.GetChildNodes(NodeType.Shape, true).Count`. |
| **Necesitas preservar la bandera oculta entre diferentes versiones de Word** | La propiedad `Hidden` se almacena en el XML de la forma como `<w:hidden/>`, que es compatible con Word 2007 y posteriores. |
| **Rendimiento con documentos grandes** | Usa `doc.GetChildNodes(NodeType.Shape, true)` una sola vez y reutiliza la colección en lugar de llamar repetidamente a `GetChild`. |

## Consejo profesional: combinar `Hidden` con `WrapType`

Cuando una forma está oculta, Word sigue reservando el espacio que ocuparía a menos que también cambies su comportamiento de ajuste. Asignar `WrapType = WrapType.None` elimina el área de marcador de posición.

```csharp
shape.Hidden = true;
shape.WrapType = WrapType.None;
```

Esto hace que el diseño colapse como si la forma nunca hubiera existido, lo cual es útil para generar informes limpios.

## Conclusión

Ahora sabes cómo **Ocultar/Mostrar una Forma con la nueva propiedad `Hidden`** usando Aspose.Words para C#. La solución cubre cargar un documento, localizar una forma, alternar la propiedad `Hidden` y persistir el cambio. Siguiendo los consejos de buenas prácticas —comprobar nulos, manejar múltiples formas y ajustar el tipo de ajuste— puedes controlar de forma fiable la visibilidad de las formas en cualquier escenario de automatización de Word.

¿Listo para explorar más? Considera los siguientes pasos:

* **Ocultar/Mostrar múltiples formas** basadas en metadatos personalizados (utiliza la técnica “ocultar forma programáticamente”).  
* **Combinar `Hidden` con contenido condicional** usando campos de Aspose.Words para generación dinámica de informes.  
* **Explorar otras propiedades de nodos**, como `Visible` para objetos de gráfico o `IsDeleted` para control a nivel de párrafo.

¡Feliz codificación y disfruta del control granular que Aspose.Words brinda a la visibilidad de formas en documentos Word!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques alternativos en tus propios proyectos.

- [how to hide shape in Word using C# – step-by-step guide](/words/english/net/programming-with-shapes/how-to-hide-shape-in-word-using-c-step-by-step-guide/)
- [How to Hide Shape in Word with C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/how-to-hide-shape-in-word-with-c-step-by-step-guide/)
- [Create a Blank Word Document with a Hidden Ellipse Shape – Full C# Guide](/words/english/net/programming-with-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape-ful/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}