---
category: general
date: 2026-03-04
description: Aprende cómo crear una forma rectangular, agregar sombra a la forma y
  aplicar el efecto de sombra en un documento de Word, y luego guarda el documento
  de Word automáticamente.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- apply shadow effect
- save word document
- create blank document
language: es
og_description: Create rectangle shape, add shadow to shape and apply shadow effect
  in a Word document using C#. Follow this guide to save Word document effortlessly.
og_title: Create rectangle shape in Word – Complete C# Tutorial
tags:
- C#
- Aspose.Words
- Document Automation
title: Crear forma de rectángulo en Word con C# – Guía paso a paso
url: /es/java/advanced-text-processing/create-rectangle-shape-in-word-with-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear forma rectangular en Word con C# – Tutorial de programación completo

¿Alguna vez necesitaste **create rectangle shape** en un archivo Word pero no sabías por dónde empezar? No estás solo—muchos desarrolladores se topan con esa barrera cuando se sumergen por primera vez en la generación programática de documentos. La buena noticia es que con unas pocas líneas de C# puedes insertar un rectángulo, **add shadow to shape**, y **apply shadow effect** sin abrir Word. En esta guía recorreremos todo el proceso, desde un **create blank document** recién creado hasta guardar el **save word document** final en disco.

Cubrirémos todo lo que necesitas: el paquete NuGet requerido, las APIs exactas, por qué cada propiedad es importante y un puñado de consejos para evitar los errores más comunes. Al final tendrás un ejemplo completamente ejecutable que puedes insertar en cualquier proyecto .NET.

## Requisitos previos

- .NET 6.0 o posterior (el código también funciona con .NET Framework 4.7+)
- Visual Studio 2022 o cualquier IDE que prefieras
- **Aspose.Words for .NET** instalado vía NuGet (`Install-Package Aspose.Words`)
- Familiaridad básica con la sintaxis de C#

No se necesitan bibliotecas adicionales de interop de Word—Aspose.Words maneja todo en memoria.

## Paso 1 – Crear un documento en blanco

Lo primero que hacemos es **create blank document**. Piensa en ello como el lienzo vacío en el que más adelante **create rectangle shape**.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1: Initialize a new blank document
Document doc = new Document();   // This gives us a fresh Word file
```

> **Por qué es importante:** Comenzar con un objeto `Document` limpio garantiza que no haya estilos o secciones ocultas que interfieran con la posición de la forma más adelante.

## Paso 2 – Insertar una forma rectangular en el documento

Ahora realmente **create rectangle shape**. Configuraremos su tamaño, posición y le diremos a Word que no envuelva el texto a su alrededor.

```csharp
// Step 2: Add a rectangle shape
Shape rectangle = new Shape(doc, ShapeType.Rectangle);
rectangle.Width = 200;          // Width in points (1 point = 1/72 inch)
rectangle.Height = 100;         // Height in points
rectangle.WrapType = WrapType.None; // No text wrapping
```

> **Consejo profesional:** Si necesitas que el rectángulo esté dentro de una celda de tabla, cambia `WrapType` a `WrapType.Inline`. Para la mayoría de los informes, `None` mantiene la forma flotando sobre el texto.

## Paso 3 – Añadir sombra a la forma y configurar su apariencia

Aquí es donde ocurre la magia: **add shadow to shape** y **apply shadow effect**. La sombra hace que el rectángulo destaque en la página, especialmente al imprimir.

```csharp
// Step 3: Enable shadow and set its properties
rectangle.ShadowFormat.Visible = true;          // Turn on the shadow
rectangle.ShadowFormat.BlurRadius = 5.0;        // Softness of the shadow edge
rectangle.ShadowFormat.Transparency = 0.3;      // 30 % transparent
rectangle.ShadowFormat.OffsetX = 8;             // Horizontal shift
rectangle.ShadowFormat.OffsetY = 8;             // Vertical shift
rectangle.ShadowFormat.Color = Color.Blue;     // Shadow colour
```

> **¿Por qué estos valores?**  
> - **BlurRadius** controla cuán difusas aparecen los bordes; un valor alrededor de `5` brinda un aspecto sutil y profesional.  
> - **Transparency** permite que el texto subyacente siga siendo legible.  
> - **OffsetX/Y** desplazan la sombra lejos de la forma, creando profundidad.  
> - Usar un tono **blue** es solo un ejemplo—cualquier `System.Drawing.Color` funciona.

## Paso 4 – Añadir la forma configurada al cuerpo del documento

Con el rectángulo totalmente estilizado, ahora **add rectangle shape** a la primera sección del documento. Este paso realmente coloca la forma en el archivo.

```csharp
// Step 4: Append the shape to the first section's body
doc.FirstSection.Body.AppendChild(rectangle);
```

> **Caso límite:** Si tu documento ya contiene secciones, puede que quieras dirigirte a una específica (`doc.Sections[2]` por ejemplo). El código anterior funciona para un documento de una sola sección, lo cual es común en informes rápidos.

## Paso 5 – Guardar el documento Word

Finalmente, **save word document** en disco. El archivo contendrá el rectángulo con su sombra, listo para abrirse en Microsoft Word.

```csharp
// Step 5: Persist the document
string outputPath = @"C:\Temp\shadowed_rectangle.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

> **Consejo:** Usa `doc.Save(outputPath, SaveFormat.Docx)` si necesitas ser explícito sobre el formato. El método `Save` detecta automáticamente la extensión, pero ser explícito puede evitar confusiones cuando la ruta se genera programáticamente.

## Ejemplo completo y ejecutable

A continuación tienes el programa completo que puedes copiar y pegar en una aplicación de consola. Incluye todas las declaraciones `using` y el método `Main`, para que puedas ejecutarlo de inmediato.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a blank document
            Document doc = new Document();

            // 2️⃣ Create a rectangle shape
            Shape rectangle = new Shape(doc, ShapeType.Rectangle);
            rectangle.Width = 200;
            rectangle.Height = 100;
            rectangle.WrapType = WrapType.None;

            // 3️⃣ Apply shadow effect
            rectangle.ShadowFormat.Visible = true;
            rectangle.ShadowFormat.BlurRadius = 5.0;
            rectangle.ShadowFormat.Transparency = 0.3;
            rectangle.ShadowFormat.OffsetX = 8;
            rectangle.ShadowFormat.OffsetY = 8;
            rectangle.ShadowFormat.Color = Color.Blue;

            // 4️⃣ Insert the shape into the document body
            doc.FirstSection.Body.AppendChild(rectangle);

            // 5️⃣ Save the document
            string outputPath = @"C:\Temp\shadowed_rectangle.docx";
            doc.Save(outputPath);
            Console.WriteLine($"✅ Document saved at {outputPath}");
        }
    }
}
```

### Resultado esperado

Cuando abras *shadowed_rectangle.docx* en Microsoft Word, verás un rectángulo con borde azul flotando cerca de la parte superior de la primera página, con una sombra azul suave desplazada 8 pt a la derecha y abajo. No hay texto adicional a su alrededor porque configuramos `WrapType.None`.

## Preguntas frecuentes y variaciones

| Question | Answer |
|----------|--------|
| **¿Puedo cambiar la forma a una elipse?** | Sí—reemplaza `ShapeType.Rectangle` por `ShapeType.Ellipse`. Todas las propiedades de sombra permanecen igual. |
| **¿Qué pasa si necesito múltiples formas?** | Simplemente repite los Pasos 2‑4 para cada nueva instancia de `Shape`, ajustando `OffsetX/Y` o `Left/Top` para evitar superposiciones. |
| **¿Hay alguna forma de que el color de la sombra coincida con el relleno de la forma?** | Absolutamente. Establece primero `rectangle.FillColor`, luego asigna `rectangle.ShadowFormat.Color = rectangle.FillColor;`. |
| **¿Cómo inserto la forma en una celda de tabla?** | Usa `cell.FirstParagraph.AppendChild(rectangle);` después de localizar el objeto `Cell` deseado. |
| **¿Funcionará esto en .NET Core?** | Sí—Aspose.Words es multiplataforma. Solo asegúrate de referenciar la versión adecuada del paquete NuGet para .NET Core/5/6. |

## Errores comunes y consejos profesionales

- **Error:** Olvidar establecer `ShadowFormat.Visible = true`. Las propiedades de sombra se ignorarán silenciosamente.  
  **Solución:** Siempre habilita la visibilidad antes de ajustar otros parámetros de sombra.

- **Error:** Usar un `BlurRadius` muy grande (p.ej., 20) puede hacer que la sombra se vea difusa y poco profesional.  
  **Solución:** Mantén valores entre `3` y `8` para la mayoría de los documentos empresariales.

- **Consejo profesional:** Si necesitas que la forma sea seleccionable más tarde (p.ej., para edición del usuario final), evita establecer `WrapType.Inline`. Las formas flotantes (`WrapType.None`) son más fáciles de mover programáticamente.

- **Consejo profesional:** Al generar muchos documentos en un bucle, reutiliza una única instancia de `Document` y llama a `doc.Clone(true)` en cada iteración para mejorar el rendimiento.

## Temas relacionados que podrías explorar a continuación

- **Añadir texto dentro de una forma rectangular** – aprende a usar `Shape.TextPath` para etiquetas.  
- **Crear diagramas complejos** – combina múltiples formas, conectores y agrupaciones.  
- **Exportar a PDF** – convierte el mismo documento a PDF con un solo `doc.Save("output.pdf")`.  
- **Aplicar diferentes estilos de relleno** – degradados, texturas o incluso imágenes dentro de las formas.

## Conclusión

Hemos acabado de **create rectangle shape**, **add shadow to shape**, y **apply shadow effect** en un archivo Word usando C#. Siguiendo los cinco pasos concisos ahora tienes un patrón reutilizable para cualquier escenario de automatización de documentos, y sabes cómo **save word document** de forma fiable. Siéntete libre de ajustar dimensiones, colores o incluso cambiar el rectángulo por otra geometría—Aspose.Words lo hace todo sencillo.

Si encontraste útil este tutorial, dale una estrella en GitHub o comparte tus propias variaciones en los comentarios. ¡Feliz codificación, y que tus documentos siempre luzcan tan pulidos como este rectángulo con sombra!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}