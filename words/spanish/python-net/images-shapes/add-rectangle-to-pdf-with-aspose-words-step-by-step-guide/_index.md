---
category: general
date: 2026-03-01
description: Agrega un rectángulo a PDF rápidamente usando Aspose.Words. Aprende a
  insertar formas en PDF, añadir gráficos a PDF y crear documentos PDF programáticamente
  con una sombra personalizada.
draft: false
keywords:
- add rectangle to pdf
- insert shape pdf
- add graphics to pdf
- create pdf document programmatically
- create pdf with shape
language: es
og_description: Agregar rectángulo a PDF usando Aspose.Words. Este tutorial muestra
  cómo insertar una forma en PDF, añadir gráficos a PDF y crear un documento PDF programáticamente
  en C#.
og_title: Agregar rectángulo a PDF con Aspose.Words – Guía completa
tags:
- pdf
- aspnet
- csharp
- graphics
title: Agregar rectángulo a PDF con Aspose.Words – Guía paso a paso
url: /es/python/images-shapes/add-rectangle-to-pdf-with-aspose-words-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Agregar rectángulo a PDF con Aspose.Words – Guía completa

¿Alguna vez necesitaste **agregar rectángulo a PDF** pero no estabas seguro de qué llamada a la API hace el truco? No eres el único: los desarrolladores preguntan constantemente, “¿Cómo inserto una forma en PDF y mantengo el archivo liviano?” La buena noticia es que Aspose.Words lo hace muy fácil. En este tutorial recorreremos todo el proceso, desde crear un documento PDF programáticamente hasta dar estilo al rectángulo con una sombra.

También incluiremos algunos extras: aprenderás a **agregar gráficos a PDF**, verás los pasos exactos para **insertar forma PDF**, y terminarás con un ejemplo listo‑para‑ejecutar que **crea PDF con forma**. Sin referencias externas, solo una solución autocontenida que puedes copiar‑pegar hoy.

## Requisitos previos

Antes de ensuciarnos las manos, asegúrate de tener:

- .NET 6.0 o posterior (Aspose.Words funciona con .NET Standard 2.0+)
- Una licencia válida de Aspose.Words for .NET o una clave de evaluación temporal
- Visual Studio 2022 (o cualquier IDE que prefieras)
- Conocimientos básicos de C# — nada sofisticado, solo la capacidad de ejecutar una aplicación de consola

Eso es todo. Si tienes eso, estás listo para comenzar.

## Paso 1: Crear un documento PDF programáticamente

Lo primero que haces cuando quieres **agregar rectángulo a PDF** es iniciar un documento vacío. Piensa en la clase `Document` como un lienzo en blanco; todo lo que agregues después vivirá dentro de él.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1 – initialise a new empty document
        Document doc = new Document();

        // The rest of the steps follow...
```

¿Por qué comenzar con un documento vacío? Porque garantiza que tengas control total sobre cada elemento — sin encabezados o pies de página ocultos con los que lidiar después.

## Paso 2: Inicializar un DocumentBuilder para insertar forma PDF

Un `DocumentBuilder` es tu pincel de dibujo. Sabe cómo colocar texto, imágenes y, crucialmente para nosotros, formas. Sin él, tendrías que manipular el árbol de nodos de bajo nivel tú mismo — una pesadilla para la mayoría de los desarrolladores.

```csharp
        // Step 2 – create a builder that will let us add content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Observa que aún no hemos añadido páginas. El builder creará automáticamente una página la primera vez que insertes algo, lo que mantiene el código ordenado.

## Paso 3: Insertar una forma de rectángulo – el núcleo de “agregar rectángulo a PDF”

Ahora viene la parte divertida: insertar el rectángulo. El método `InsertShape` admite docenas de valores `ShapeType`; elegiremos `ShapeType.Rectangle` y le daremos un tamaño de 200 × 100 puntos.

```csharp
        // Step 3 – insert a rectangle (200 × 100 points) into the document
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

En este punto el PDF ya contiene un rectángulo simple. Si abres el archivo ahora, verás una caja sencilla en la esquina superior izquierda de la primera página. Esa es la base para **agregar gráficos a PDF**.

## Paso 4: Dar estilo al rectángulo – añadiendo una sombra personalizada

Un rectángulo sin estilo es aburrido. Le daremos una sombra sutil para que *resalte* cuando se renderice el PDF. El objeto `ShadowFormat` controla todo, desde el radio de desenfoque hasta la opacidad.

```csharp
        // Step 4 – configure a custom shadow for the shape
        ShadowFormat shadow = rectangle.ShadowFormat;
        shadow.Visible = true;
        shadow.BlurRadius = 8.0;          // pixels
        shadow.Distance = 5.0;           // points from the shape
        shadow.Direction = 45.0;         // degrees clockwise
        shadow.Opacity = 0.6;            // 0‑1 range
        shadow.Color = Color.Black;
```

¿Por qué molestarse con una sombra? Además del impulso estético, una sombra puede ayudar a diferenciar gráficos superpuestos — algo que podrías necesitar al **agregar gráficos a PDF** en informes más complejos.

## Paso 5: Guardar el archivo – completando el flujo “crear PDF con forma”

La línea final escribe todo en disco. Aspose.Words elige automáticamente la versión correcta de PDF e incrusta los recursos necesarios.

```csharp
        // Step 5 – save the document as a PDF file
        doc.Save(@"C:\Temp\ShapeWithShadow.pdf");
    }
}
```

Abre `ShapeWithShadow.pdf` y verás un rectángulo con sombra bien colocado en la página. Ese es todo el flujo de **crear documento pdf programáticamente**, empaquetado en menos de 30 líneas de código.

## Ejemplo completo — crear PDF con forma de principio a fin

A continuación tienes el programa completo que puedes copiar‑pegar en un nuevo proyecto de Aplicación de Consola. Incluye todas las sentencias `using`, el método `Main` y un breve encabezado de comentarios para referencia futura.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectanglePdfDemo
{
    /// <summary>
    /// Demonstrates how to add a rectangle to PDF, configure a shadow,
    /// and save the result using Aspose.Words for .NET.
    /// </summary>
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create an empty PDF document
            Document doc = new Document();

            // 2️⃣ Initialise a DocumentBuilder – the tool that lets us add content
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert a rectangle shape (200 × 100 points) – this is the core of "add rectangle to pdf"
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);

            // 4️⃣ Apply a custom shadow – makes the graphic stand out
            ShadowFormat shadow = rect.ShadowFormat;
            shadow.Visible = true;
            shadow.BlurRadius = 8.0;   // pixels
            shadow.Distance = 5.0;    // points
            shadow.Direction = 45.0;  // degrees
            shadow.Opacity = 0.6;     // semi‑transparent
            shadow.Color = Color.Black;

            // 5️⃣ Save the document – the final step in creating a PDF with shape
            string outputPath = @"C:\Temp\ShapeWithShadow.pdf";
            doc.Save(outputPath);

            Console.WriteLine($"PDF saved successfully to {outputPath}");
        }
    }
}
```

**Resultado esperado:** un PDF de una sola página donde un rectángulo de 200 × 100 puntos se sitúa cerca de la esquina superior izquierda, adornado con una sombra suave de 45 grados. Abre el archivo en cualquier visor de PDF para verificar.

## Preguntas frecuentes y casos límite

### ¿Esto funciona con otros tipos de forma?
Absolutamente. Reemplaza `ShapeType.Rectangle` por `ShapeType.Ellipse`, `ShapeType.Triangle` o cualquiera de las más de 150 opciones que Aspose.Words soporta. Las mismas propiedades de `ShadowFormat` se aplican.

### ¿Qué pasa si necesito el rectángulo en una página específica?
Después de insertar la forma, puedes moverla a otra página ajustando la propiedad `CurrentPage` del builder antes de llamar a `InsertShape`. Por ejemplo:

```csharp
builder.MoveToPage(3);
Shape rectOnPage3 = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

### ¿Puedo cambiar el color de relleno del rectángulo?
Claro. Usa la propiedad `FillColor`:

```csharp
rect.FillColor = Color.LightBlue;
```

### ¿Cómo afecta esto al tamaño del archivo?
Agregar una forma simple y una sombra solo añade unos pocos kilobytes. Si empiezas a apilar muchos gráficos, considera comprimir imágenes o usar formas basadas en vectores para mantener el PDF ligero.

### ¿Se requiere una licencia para producción?
Aspose.Words funciona en modo de evaluación, pero el PDF de salida contendrá una marca de agua. Compra una licencia para uso sin restricciones y para eliminar la marca de agua.

## Consejos y trucos (nivel profesional)

- **Inserción por lotes:** Si necesitas docenas de rectángulos, recorre una colección de coordenadas y reutiliza el mismo `DocumentBuilder` — el rendimiento se mantiene lineal.
- **Capas:** Establece `rect.WrapType = WrapType.Inline` si deseas que el rectángulo fluya con el texto, o `WrapType.Square` para que el texto se ajuste alrededor.
- **Cumplimiento PDF/A:** Llama a `doc.CompatibilityOptions.OptimizeForPdfA = true;` antes de guardar si necesitas un PDF apto para archivo.

## Resumen visual

![add rectangle to pdf example](https://example.com/rectangle-shadow.png "add rectangle to pdf example")

La imagen ilustra el diseño final del PDF: un rectángulo limpio con una sombra sutil, exactamente lo que produce nuestro código.

## Conclusión

Ahora sabes **cómo agregar rectángulo a PDF** usando Aspose.Words, cómo **insertar forma PDF**, y cómo **agregar gráficos a PDF** con estilo personalizado — todo mientras **creas documento pdf programáticamente** y finalizas con un ejemplo de **crear PDF con forma** que puedes reutilizar mañana.  

A continuación, prueba a sustituir el rectángulo por un logotipo, o combina múltiples formas para construir un diagrama sencillo. También puedes explorar el ajuste de texto, la rotación o incluso incrustar un hipervínculo dentro de la forma. La API es lo suficientemente rica como para convertir un PDF estático en un informe interactivo y rico en gráficos sin salir de C#.

¡Siéntete libre de experimentar y, si encuentras algún obstáculo, deja un comentario abajo! ¡Feliz codificación!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}