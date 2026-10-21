---
category: general
date: 2026-03-25
description: Crea un documento PDF en C# y aprende cómo agregar una forma rectangular,
  establecer el color de relleno, ajustar el tamaño de la forma y definir la transparencia
  de la forma en solo unos pocos pasos.
draft: false
keywords:
- create pdf document
- set shape transparency
- add rectangle shape
- set fill color
- set shape size
language: es
og_description: Crea un documento PDF en C# y descubre cómo añadir un rectángulo,
  establecer su color de relleno, tamaño y transparencia para obtener un PDF pulido.
og_title: Crear documento PDF con una forma rectangular – Tutorial de C#
tags:
- C#
- PDF
- Aspose.Words
title: Crear documento PDF con una forma rectangular – Guía completa de C#
url: /es/java/images-shapes/create-pdf-document-with-a-rectangle-shape-full-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear documento PDF con una forma rectangular – Guía completa en C#

¿Alguna vez necesitaste **crear un documento PDF** que contenga una forma con estilo personalizado, pero no sabías por dónde empezar? No estás solo. Ya sea que estés construyendo un generador de informes o un folleto de marketing, poder dibujar programáticamente un rectángulo, establecer su color de relleno, ajustar su tamaño e incluso modificar su transparencia puede hacer que tus PDFs se vean mucho más profesionales.

En este tutorial recorreremos un ejemplo completo, listo para ejecutar en C# que **crea un documento PDF**, **añade una forma rectangular**, **establece el color de relleno**, **define el tamaño de la forma** y **configura la transparencia de la forma** para una sombra exterior sutil. Al final tendrás un único archivo PDF (`shadow.pdf`) que podrás abrir para ver el resultado.

> **Consejo profesional:** El mismo enfoque funciona con otros tipos de forma (elipse, línea, etc.) — simplemente cambia `ShapeType.RECTANGLE` por el que necesites.

---

## Qué necesitarás

| Prerrequisito | Por qué es importante |
|---------------|-----------------------|
| **.NET 6+** (o .NET Framework 4.6+) | La biblioteca Aspose.Words está dirigida a entornos de ejecución modernos. |
| **Paquete NuGet Aspose.Words for .NET** | Proporciona `Document`, `Shape`, `ShadowEffect` y clases relacionadas. |
| **Un IDE de C#** (Visual Studio, Rider, VS Code) | Facilita la depuración y ejecución del ejemplo sin complicaciones. |
| **Conocimientos básicos de C#** | Entenderás la sintaxis sin necesidad de profundizar demasiado. |

Puedes instalar la biblioteca desde la línea de comandos:

```bash
dotnet add package Aspose.Words
```

Eso es todo — sin DLLs adicionales, sin dependencias nativas. Una vez que el paquete esté instalado, el código a continuación se compilará y ejecutará.

---

## Implementación paso a paso

A continuación dividimos el proceso en cinco pasos lógicos. Cada paso tiene un encabezado claro (para que los modelos de IA lo indexen) y un bloque de código corto que puedes copiar‑pegar directamente.

### ## 1. Crear documento PDF y preparar el lienzo

Lo primero que hacemos es instanciar un `Document`. Piensa en él como un lienzo en blanco que eventualmente se convertirá en tu archivo PDF.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new empty document – this is the PDF document we will build.
        Document document = new Document();

        // The rest of the steps follow inside this method.
```

> **¿Por qué?** `Document` contiene todas las secciones, párrafos y formas. Comenzar con un objeto limpio garantiza que no haya artefactos ocultos de ejecuciones anteriores.

### ## 2. Añadir forma rectangular – establecer color de relleno y tamaño de la forma

Ahora creamos un rectángulo, le asignamos un relleno amarillo brillante y definimos sus dimensiones. Esto cubre **añadir forma rectangular**, **establecer color de relleno** y **definir tamaño de la forma**.

```csharp
        // Step 2: Create a rectangle shape.
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);

        // Set the width and height – this is where we set the shape size.
        rectangle.Width = 200;   // 200 points (≈2.78 inches)
        rectangle.Height = 100;  // 100 points (≈1.39 inches)

        // Apply a fill color – here we use a vivid yellow.
        rectangle.FillColor = Color.Yellow;
```

> **Nota:** El ancho/alto se miden en puntos (1 punto = 1/72 de pulgada). Ajusta estos números para que encajen en tu diseño.

### ## 3. Aplicar una sombra exterior y establecer la transparencia de la forma

Las sombras añaden profundidad, y controlar su opacidad es la esencia de **establecer transparencia de la forma**. A continuación configuramos una sombra gris exterior con un 30 % de transparencia.

```csharp
        // Step 3: Configure the outer shadow effect.
        ShadowEffect shadow = rectangle.ShadowEffect;
        shadow.Color = Color.Gray;          // Shadow hue
        shadow.BlurRadius = 5.0;            // How fuzzy the shadow appears
        shadow.DistanceX = 4;               // Horizontal offset
        shadow.DistanceY = 4;               // Vertical offset
        shadow.Transparency = 0.3;          // 0 = opaque, 1 = fully transparent
        shadow.Style = ShadowStyle.Outer;   // Make it an outer shadow
```

> **¿Por qué establecer transparencia?** Una sombra con 30 % de transparencia se ve sutil, evitando que el rectángulo parezca “plano” en la página.

### ## 4. Insertar la forma en el cuerpo del documento

Ahora colocamos el rectángulo en el primer párrafo de la primera sección del documento. Este paso une todo.

```csharp
        // Step 4: Insert the rectangle into the first paragraph.
        // If the document has no paragraphs yet, Aspose creates one automatically.
        Paragraph firstParagraph = document.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(rectangle);
```

> **Caso límite:** Si necesitas la forma en una nueva página, antepone `document.Sections[0].PageSetup.SectionStart = SectionStart.NewPage;` antes de añadir la forma.

### ## 5. Guardar el documento como archivo PDF

Finalmente, persistimos la estructura en memoria en un archivo PDF físico. El archivo se escribirá en la carpeta que especifiques.

```csharp
        // Step 5: Save the document as a PDF.
        string outputPath = @"YOUR_DIRECTORY\shadow.pdf";
        document.Save(outputPath, SaveFormat.Pdf);

        Console.WriteLine($"PDF saved successfully to {outputPath}");
    }
}
```

Al ejecutar el programa, aparecerá un archivo llamado `shadow.pdf`. Al abrirlo verás un rectángulo amarillo con una sombra gris suave desplazada 4 puntos — exactamente lo que describió nuestro código.

> **Salida esperada:** Un PDF de una sola página donde el rectángulo se sitúa cerca de la esquina superior‑izquierda, relleno de amarillo, con un tamaño de 200 × 100 puntos y una sombra exterior semitransparente.

---

## Ejemplo completo (listo para copiar‑pegar)

A continuación tienes todo el archivo fuente, listo para que lo insertes en un nuevo proyecto de consola.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new empty document – this will become the PDF.
        Document document = new Document();

        // 2️⃣ Add a rectangle shape, set its size and fill color.
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.Width = 200;          // shape size – width
        rectangle.Height = 100;         // shape size – height
        rectangle.FillColor = Color.Yellow; // set fill color

        // 3️⃣ Apply an outer shadow and adjust transparency.
        ShadowEffect shadow = rectangle.ShadowEffect;
        shadow.Color = Color.Gray;
        shadow.BlurRadius = 5.0;
        shadow.DistanceX = 4;
        shadow.DistanceY = 4;
        shadow.Transparency = 0.3;      // set shape transparency
        shadow.Style = ShadowStyle.Outer;

        // 4️⃣ Insert the shape into the first paragraph of the document.
        Paragraph firstParagraph = document.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(rectangle);

        // 5️⃣ Save everything as a PDF.
        string outputPath = @"YOUR_DIRECTORY\shadow.pdf";
        document.Save(outputPath, SaveFormat.Pdf);

        Console.WriteLine($"PDF created at: {outputPath}");
    }
}
```

> **Consejo:** Reemplaza `YOUR_DIRECTORY` por una ruta absoluta como `C:\Temp` o una ruta relativa como `.\output`. El programa creará la carpeta si aún no existe.

---

## Preguntas frecuentes (FAQ)

**P: ¿Puedo cambiar la posición del rectángulo en la página?**  
R: Por supuesto. Establece `rectangle.Left` y `rectangle.Top` (ambos medidos en puntos) antes de añadirlo al párrafo.

**P: ¿Qué pasa si necesito un relleno transparente en lugar de una sombra transparente?**  
R: Usa `rectangle.FillColor = Color.FromArgb(128, Color.Yellow);` — el primer argumento es el canal alfa (0‑255), donde 128 produce aproximadamente un 50 % de transparencia.

**P: ¿Esto funciona con .NET Core?**  
R: Sí. Aspose.Words es compatible con .NET Standard 2.0+, por lo que puedes ejecutar el mismo código en .NET 6, .NET 7 o .NET Framework 4.6+.

**P: ¿Cómo puedo añadir varias formas?**  
R: Simplemente repite los pasos 2‑4 para cada forma, insertándolas en diferentes párrafos o secciones según necesites.

---

## Conclusión

Acabamos de **crear un documento PDF** desde cero, **añadir una forma rectangular**, **establecer su color de relleno**, **definir su tamaño** y **ajustar la transparencia de la forma** para lograr un efecto de sombra pulido. El código de ejemplo es autónomo, se ejecuta en menos de un minuto y demuestra los conceptos clave que necesitarás para diseños PDF más elaborados.

¿Listo para el siguiente reto? Prueba cambiar el rectángulo por una forma con esquinas redondeadas, incrusta una imagen dentro de la forma o genera automáticamente una tabla de contenidos. La misma API te permite combinar texto, imágenes y vectores — el cielo es el límite.

Si encontraste útil esta guía, dale una estrella en GitHub, compártela con un compañero o deja un comentario con tus propias variaciones. ¡Feliz codificación!

---

![create pdf document with rectangle shape example](/images/rectangle-shadow.png "Screenshot showing the created PDF with a yellow rectangle and gray outer shadow")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}