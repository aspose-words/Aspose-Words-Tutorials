---
category: general
date: 2026-02-24
description: Crea una forma rectangular en C# usando Aspose.Words, agrega sombra a
  la forma y guarda el documento como PDF. Aprende cómo agregar sombra y cómo guardar
  el PDF en minutos.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shadow
- how to save pdf
language: es
og_description: 'Crea una forma rectangular en C# con Aspose.Words, luego agrega sombra
  a la forma y guarda el documento como PDF: una guía completa paso a paso.'
og_title: Crear forma rectangular, agregar sombra y guardar PDF
tags:
- Aspose.Words
- C#
- PDF generation
title: Crear forma de rectángulo, añadir sombra y guardar PDF
url: /es/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/
---

craft final answer.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear forma rectangular, agregar sombra y guardar PDF

¿Alguna vez necesitaste **crear una forma rectangular** en un documento de Word pero también querías una sombra agradable y una salida en PDF? No eres el único. En muchos proyectos de generación de informes o facturas, el acabado visual —como una sombra sutil— marca la diferencia entre “solo otro archivo” y “documento de nivel profesional”.  

En este tutorial recorreremos exactamente eso: usar **Aspose.Words for .NET** para crear una forma rectangular, agregar sombra a la forma y, finalmente, **guardar el documento como PDF**. Al final tendrás una aplicación de consola en C# lista para ejecutar que produce un PDF con un rectángulo sombreado, y comprenderás cómo ajustar la sombra o cambiar las opciones de exportación.

## Lo que necesitarás

- .NET 6 SDK (o cualquier versión reciente de .NET) – la API funciona igual en .NET Framework 4.x.  
- Paquete NuGet Aspose.Words for .NET (`Aspose.Words`) – instálalo con `dotnet add package Aspose.Words`.  
- Un editor de código – Visual Studio, VS Code o Rider sirven.  

No se requieren pasos de licencia adicionales para este ejemplo; el modo de evaluación gratuito es suficiente para ver la salida en PDF.

## Paso 1: Configurar el proyecto e importar espacios de nombres

Lo primero, vamos a crear un proyecto de consola y a traer las clases que necesitaremos.

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectangleShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // The rest of the code lives here – see the following steps.
        }
    }
}
```

*Por qué es importante:* `Document` y `DocumentBuilder` nos proporcionan el lienzo, mientras que `Shape` y `ShadowFormat` nos permiten dibujar y dar estilo al rectángulo. Importarlos al inicio mantiene el código posterior ordenado.

## Paso 2: **Crear forma rectangular** con las dimensiones deseadas

Ahora creamos realmente un documento en blanco e insertamos un rectángulo. Observa cómo el método `InsertShape` devuelve un objeto `Shape` que podemos estilizar de inmediato.

```csharp
// Inside Main()
Document document = new Document();               // blank Word document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a rectangle of 200x100 points (≈2.78" × 1.39")
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
rectangle.FillColor = System.Drawing.Color.LightBlue;
```

*Explicación*: El tamaño se expresa en puntos (1 pt = 1/72 in). Ajusta los números para que encajen en tu diseño. También le damos a la forma un relleno azul claro para que la sombra destaque.

## Paso 3: **Agregar sombra a la forma** – afinar el efecto

Una sombra no es solo “encendido/apagado”. Puedes controlar su color, desenfoque, distancia, dirección e incluso transparencia. Aquí tienes una configuración práctica que funciona bien para la mayoría de los informes.

```csharp
// Access the shape's shadow format
ShadowFormat shadow = rectangle.ShadowFormat;
shadow.Visible = true;                     // turn the shadow on
shadow.Color = System.Drawing.Color.Gray;  // shadow colour
shadow.BlurRadius = 5.0;                    // soft edges (higher = blurrier)
shadow.Distance = 4.0;                      // how far the shadow is from the shape
shadow.Direction = 45;                     // angle in degrees (45° = down‑right)
shadow.Transparency = 0.3;                  // 30 % transparent for a subtle look
```

*Por qué podrías cambiar estos valores:*  
- **BlurRadius** – aumenta para un efecto difuso, disminuye para un borde nítido.  
- **Direction** – 0° apunta a la derecha, 90° hacia abajo, 180° a la izquierda, etc. Rótala para que coincida con el diseño de tu página.  
- **Transparency** – pon `0` para una sombra sólida, `0.5` para mitad transparente, etc.

### Cómo agregar sombra – enfoques alternativos

Si necesitas una **sombra de múltiples capas** (por ejemplo, una sombra exterior más oscura y una interior más clara), puedes crear una segunda forma, desplazarla y establecer un `ShadowFormat` diferente. O, para un aspecto rápido “sin desenfoque”, establece `BlurRadius = 0`.

## Paso 4: **Guardar documento como PDF** – la exportación final

Con el rectángulo y su sombra listos, el último paso es escribir el archivo como PDF. Aspose.Words maneja la conversión internamente; solo llamas a `Save` con el formato deseado.

```csharp
// Define the output path – adjust to your environment
string outputPath = @"C:\Temp\ShadowRectangle.pdf";

// Save as PDF (the format is inferred from the extension)
document.Save(outputPath);
Console.WriteLine($"PDF saved to {outputPath}");
```

*Consejo*: Si necesitas controlar el cumplimiento del PDF (PDF/A, PDF/X) o incrustar fuentes, usa una sobrecarga:

```csharp
PdfSaveOptions options = new PdfSaveOptions
{
    Compliance = PdfCompliance.PdfA1b,
    EmbedFullFonts = true
};
document.Save(outputPath, options);
```

Ese es el **cómo guardar PDF** en resumidas cuentas.

## Ejemplo completo, ejecutable

A continuación tienes el programa completo que puedes copiar y pegar en `Program.cs`. Compila y se ejecuta tal cual (solo asegúrate de que la carpeta de salida exista).

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectangleShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a blank document and a builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // 2️⃣ Insert a rectangle shape
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
            rectangle.FillColor = System.Drawing.Color.LightBlue;

            // 3️⃣ Add a shadow to the shape
            ShadowFormat shadow = rectangle.ShadowFormat;
            shadow.Visible = true;
            shadow.Color = System.Drawing.Color.Gray;
            shadow.BlurRadius = 5.0;
            shadow.Distance = 4.0;
            shadow.Direction = 45;
            shadow.Transparency = 0.3;

            // 4️⃣ Save the document as PDF
            string outputPath = @"C:\Temp\ShadowRectangle.pdf";
            document.Save(outputPath);
            Console.WriteLine($"PDF saved to {outputPath}");
        }
    }
}
```

### Resultado esperado

Abre el `ShadowRectangle.pdf` generado. Verás una sola página con un rectángulo azul claro, una sombra gris suave desplazada 45° hacia abajo‑derecha y bordes limpios. El PDF debería poder verse en cualquier lector moderno (Adobe Acrobat, Edge, Chrome).

![Crear forma rectangular con sombra en PDF](/images/shadow-rectangle.png "Crear forma rectangular con sombra en PDF")

*(El texto alternativo de la imagen incluye la palabra clave principal para SEO.)*

## Preguntas frecuentes y manejo de casos límite

**¿Qué pasa si la sombra desaparece en el PDF?**  
Asegúrate de estar usando una versión reciente de Aspose.Words (≥23.3). Las versiones anteriores tenían un error donde ciertas propiedades de sombra se ignoraban durante la conversión a PDF.

**¿Puedo cambiar el color de la sombra para que coincida con mi marca?**  
Claro, solo reemplaza `System.Drawing.Color.Gray` por cualquier `Color` que desees, por ejemplo `Color.FromArgb(128, 0, 0, 255)` para un azul semitransparente.

**¿Cómo añado sombra a otras formas (elipse, estrella, etc.)?**  
El mismo `ShadowFormat` funciona para cualquier objeto `Shape`. Después de crear la forma, obtén su `ShadowFormat` y establece las propiedades.

**¿Qué pasa con DPI o problemas de escalado?**  
El renderizado del PDF respeta el tamaño en puntos de la forma. Si necesitas una salida de mayor resolución (para impresión), ajusta las dimensiones de la forma o establece `PdfSaveOptions.ImageResolution`.

**¿Puedo exportar a otros formatos, como PNG?**  
Sí, solo llama `document.Save("output.png", SaveFormat.Png)`. La sombra se renderizará de la misma manera.

## Consejos profesionales y buenas prácticas

- **Reutiliza el builder**: Si vas a añadir múltiples formas, mantén una única instancia de `DocumentBuilder`; es más barato que crear muchas.
- **Guardado por lotes**: Cuando generes muchos PDFs en un bucle, reutiliza el objeto `PdfSaveOptions` para evitar asignaciones repetidas.
- **Pruebas**: Siempre abre el PDF después de guardarlo para verificar que la sombra aparezca como esperas. Algunos visores de PDF renderizan sombras ligeramente diferente; Adobe Acrobat es la referencia más fiable.
- **Rendimiento**: Para documentos grandes, desactiva los saltos de página automáticos de `DocumentBuilder.InsertShape` estableciendo `builder.PageSetup.DifferentFirstPageHeaderFooter = false` si no los necesitas.

## Conclusión

Hemos cubierto todo lo que necesitas para **crear una forma rectangular**, **agregar sombra a la forma** y **guardar el documento como PDF** usando Aspose.Words for .NET. El código es compacto, los conceptos están explicados y ahora tienes una base sólida para experimentar con otras formas, estilos de sombra y opciones de exportación.  

¿Próximos pasos? Prueba a sustituir el rectángulo por un rectángulo con esquinas redondeadas…

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}