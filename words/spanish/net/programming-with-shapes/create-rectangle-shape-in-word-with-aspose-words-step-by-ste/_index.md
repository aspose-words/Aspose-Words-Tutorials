---
category: general
date: 2025-12-29
description: Crea una forma rectangular en un documento de Word usando Aspose.Words
  C#. Aprende a establecer la transparencia de la forma, definir el color de la sombra
  y guardar el documento de Word sin esfuerzo.
draft: false
keywords:
- create rectangle shape
- set shape transparency
- set shadow color
- save word document
- create word document
language: es
og_description: Crea una forma rectangular en un documento de Word con Aspose.Words
  C#. Esta guía muestra cómo establecer la transparencia de la forma, definir el color
  de la sombra y guardar el documento de Word.
og_title: Crear forma de rectángulo en Word – Tutorial completo de Aspose.Words
tags:
- Aspose.Words
- C#
- Word Automation
title: Crear forma rectangular en Word con Aspose.Words – Guía paso a paso
url: /es/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear forma rectangular en Word – Tutorial completo de Aspose.Words

¿Alguna vez necesitaste **crear una forma rectangular** en un documento Word pero no sabías por dónde empezar? No estás solo; muchos desarrolladores se topan con este obstáculo al automatizar informes o facturas. En esta guía recorreremos paso a paso los pasos exactos para crear una forma rectangular, establecer la transparencia de la forma, definir el color de la sombra y, finalmente, **guardar el documento Word** usando Aspose.Words para .NET.

Cubriremos todo, desde el objeto de documento inicial hasta el archivo final `.docx` en disco, de modo que al terminar podrás **crear documentos Word** programáticamente sin adivinar. Sin referencias externas, solo una solución autocontenida que puedes copiar‑pegar en tu proyecto.

## Requisitos previos

- .NET 6.0 o superior (el código también funciona con .NET Framework 4.7+)
- Paquete NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)
- Familiaridad básica con la sintaxis de C#
- Un IDE de tu elección (Visual Studio, Rider, VS Code, etc.)

> **Consejo profesional:** Si estás usando una versión de prueba gratuita de Aspose.Words, la biblioteca añadirá una marca de agua al archivo de salida. Para producción necesitarás una licencia válida.

## Paso 1: Inicializar el Document y el Builder

Lo primero que hacemos es crear un documento Word nuevo y vacío y un `DocumentBuilder` que nos permite insertar contenido. Piensa en el builder como un lápiz virtual que dibuja en la página.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();

// The builder provides methods to add text, tables, shapes, etc.
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Por qué es importante:** Sin un `DocumentBuilder` tendrías que manipular el árbol de nodos de bajo nivel directamente, lo que es propenso a errores y más difícil de leer.

## Paso 2: Crear forma rectangular

Ahora realmente **creamos la forma rectangular**. El método `InsertShape` recibe un enum `ShapeType`, ancho y alto (en puntos). El objeto `Shape` devuelto nos permite ajustar propiedades visuales más adelante.

```csharp
// Insert a rectangle 150 pts wide and 80 pts tall
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

En este punto el rectángulo es una caja negra sólida anclada al párrafo actual. Puedes moverlo, cambiar su tamaño o incluso rotarlo más tarde si lo necesitas.

![create rectangle shape with shadow](/images/rectangle-shadow.png "A Word document showing a rectangle shape with a gray shadow")

*Texto alternativo de la imagen: crear forma rectangular con sombra en un documento Word*

## Paso 3: Establecer la transparencia de la forma

La transparencia es el nivel de “ver a través” del relleno de la forma. Aspose.Words usa una propiedad `Transparency` que varía de `0.0` (opaco) a `1.0` (totalmente transparente). Aquí **establecemos la transparencia de la forma** al 40 % para que el texto subyacente siga siendo legible.

```csharp
// Make the rectangle 40 % transparent
rectangleShape.Fill.Transparency = 0.4; // 0.0 = opaque, 1.0 = invisible
```

> **Caso límite:** Si necesitas una forma completamente invisible pero que la sombra siga apareciendo, establece `Transparency` a `1.0` y asigna a la forma un ancho de contorno distinto de cero.

## Paso 4: Configurar la sombra

Una sombra sutil agrega profundidad. **Estableceremos el color de la sombra** a un gris medio, ajustaremos su radio de desenfoque y la desplazaremos unos puntos tanto horizontal como verticalmente.

```csharp
// Enable the shadow effect
rectangleShape.Shadow.Enabled = true;

// Shadow color – a neutral gray
rectangleShape.Shadow.Color = System.Drawing.Color.Gray;

// 40 % transparent shadow (same as shape's fill)
rectangleShape.Shadow.Transparency = 0.4;

// Blur radius makes the edge softer
rectangleShape.Shadow.Blur = 6;

// Horizontal and vertical offsets (in points)
rectangleShape.Shadow.OffsetX = 5;
rectangleShape.Shadow.OffsetY = 5;
```

> **Por qué es importante:** Una sombra demasiado nítida o demasiado oscura puede parecer un artefacto de impresión. Ajusta `Blur` y `Transparency` hasta que se vea natural.

## Paso 5: Guardar el documento Word

Finalmente **guardamos el documento Word** en disco. El método `Save` determina automáticamente el formato del archivo a partir de la extensión; `.docx` es el formato OpenXML moderno.

```csharp
// Save the document to the desired folder
document.Save(@"C:\Temp\ShadowRectangle.docx");
```

Si la carpeta no existe, Aspose.Words lanzará una `ArgumentException`. Asegúrate de que la ruta sea válida o crea el directorio con antelación.

## Ejemplo completo funcional

A continuación tienes el programa completo, listo para ejecutar, que combina todos los pasos. Copia esto en un nuevo proyecto de consola y pulsa **F5**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace AsposeRectangleDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Initialize document and builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // 2️⃣ Insert rectangle shape
            Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 80);

            // 3️⃣ Set shape transparency (40 % transparent)
            rectangleShape.Fill.Transparency = 0.4;

            // 4️⃣ Configure shadow (color, blur, offset, transparency)
            rectangleShape.Shadow.Enabled = true;
            rectangleShape.Shadow.Color = System.Drawing.Color.Gray;
            rectangleShape.Shadow.Transparency = 0.4;
            rectangleShape.Shadow.Blur = 6;
            rectangleShape.Shadow.OffsetX = 5;
            rectangleShape.Shadow.OffsetY = 5;

            // 5️⃣ Save the document
            string outputPath = @"C:\Temp\ShadowRectangle.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Resultado esperado

Abre `ShadowRectangle.docx` en Microsoft Word. Deberías ver un rectángulo gris claro con una sombra suave y ligeramente desplazada, ambos renderizados al 40 % de transparencia. La forma se sitúa en una página en blanco, lista para contenido adicional.

## Preguntas frecuentes y variaciones

**¿Qué pasa si necesito una forma diferente?**  
Reemplaza `ShapeType.Rectangle` por cualquier otro valor del enum (`Ellipse`, `Triangle`, `Star`, etc.). El resto del código permanece igual.

**¿Puedo cambiar el color del contorno?**  
Sí—usa `rectangleShape.StrokeColor = System.Drawing.Color.Blue;` y opcionalmente establece `rectangleShape.StrokeWeight = 1.5;`.

**¿Cómo coloco la forma en una ubicación específica de la página?**  
Configura `rectangleShape.WrapType = WrapType.None;` y luego ajusta las propiedades `rectangleShape.Left` y `rectangleShape.Top` (los valores están en puntos).

**¿Es posible añadir texto dentro del rectángulo?**  
Absolutamente. Después de crear la forma, puedes llamar a `rectangleShape.AppendChild(new Paragraph(document))` y luego añadir un `Run` con tu texto. Recuerda establecer las propiedades `rectangleShape.TextBox` si deseas un formato más rico.

## Consejos profesionales y trampas comunes

- **Licencia temprana:** Si olvidas aplicar una licencia, Aspose.Words insertará una marca de agua en la primera página, lo que puede resultar confuso durante las pruebas.
- **Consejo de rendimiento:** Al generar muchos documentos en un bucle, reutiliza una única instancia de `Document` y llama a `document.RemoveAllChildren();` después de cada guardado para evitar una presión excesiva del GC.
- **Visibilidad de la sombra:** En pantallas de baja resolución una sombra sutil puede parecer invisible. Incrementa `Blur` o `OffsetX/Y` para depurar, luego vuelve a reducirlo para producción.

## Próximos pasos

Ahora que sabes cómo **crear una forma rectangular**, **establecer la transparencia de la forma**, **definir el color de la sombra** y **guardar el documento Word**, considera ampliar el tutorial:

- Añadir múltiples formas y agruparlas.
- Insertar el rectángulo dentro de una celda de tabla para un diseño de informe.
- Combinar la forma con `DocumentBuilder.InsertHtml` para superponer contenido con estilo HTML.
- Explorar otros efectos visuales como `Glow` o `Reflection` para documentos más ricos visualmente.

Experimenta, rompe cosas y luego refina—la generación programática de documentos es un patio de juegos donde el diseño visual se encuentra con el código.

---

*¡Feliz codificación! Si te encontraste con algún problema, deja un comentario abajo y lo solucionaremos juntos.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}