---
category: general
date: 2026-03-27
description: Crear documento Word en C# y aprender cómo agregar una forma, aplicar
  sombra a la forma y establecer la distancia de la sombra. Guía paso a paso para
  Aspose.Words.
draft: false
keywords:
- create word document c#
- how to add shape
- apply shadow to shape
- how to create rectangle
- set shadow distance
language: es
og_description: Crea un documento de Word en C# con una forma rectangular y sombra
  personalizada. Sigue este tutorial completo para establecer la distancia y el estilo
  de la sombra.
og_title: Crear documento de Word C# – Añadir forma con sombra
tags:
- Aspose.Words
- C#
- Document Automation
title: Crear documento Word C# – Añadir forma con sombra
url: /es/net/programming-with-shapes/create-word-document-c-add-shape-with-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear documento Word C# – Añadir forma con sombra

¿Alguna vez necesitaste **create word document c#** que contenga un rectángulo con estilo? Tal vez estés creando una plantilla de informe y quieras una sombra sutil para que el diseño destaque. En este tutorial recorreremos exactamente eso: cómo añadir una forma, aplicar sombra a la forma e incluso ajustar la distancia de la sombra usando Aspose.Words.

Comenzaremos con un documento en blanco, insertaremos un rectángulo, le daremos una sombra predefinida y terminaremos guardando el archivo. Al final tendrás un .docx listo para usar que podrás abrir en Word y ver el efecto al instante. Sin herramientas externas, solo código C# puro.

## Requisitos previos

- .NET 6 (o cualquier .NET Framework reciente) instalado.
- Visual Studio 2022 o VS Code con la extensión C#.
- Paquete NuGet Aspose.Words para .NET (`Aspose.Words` versión 23.12 o posterior).  
  Puedes añadirlo mediante la consola del Administrador de paquetes:

  ```powershell
  Install-Package Aspose.Words
  ```

Eso es todo: no se requieren DLLs adicionales ni interop COM.

## Paso 1: Inicializar un nuevo documento y Builder – *create word document c#* conceptos básicos

Primero necesitamos un objeto `Document` que representa el archivo Word y un `DocumentBuilder` para editarlo.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create a blank Word document
Document document = new Document();

// DocumentBuilder lets us add content programmatically
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Por qué es importante este paso:** La clase `Document` es el contenedor de todas las partes de Word (páginas, estilos, imágenes). El builder es la API de alto nivel que abstrae la manipulación de nodos de bajo nivel, facilitando **create word document c#** sin tener que trabajar directamente con XML.

## Paso 2: Insertar una forma rectangular – *how to create rectangle*  

Ahora colocaremos un rectángulo en la página. El tamaño se expresa en puntos (1 pt ≈ 1/72 in).

```csharp
// Insert a rectangle 200 pt wide and 100 pt tall
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);

// Give the rectangle a light‑blue fill so we can see it clearly
rectangleShape.FillColor = Color.LightBlue;
```

> **Consejo profesional:** Si necesitas una forma diferente, simplemente cambia `ShapeType.Rectangle` por `ShapeType.Ellipse`, `ShapeType.Triangle`, etc. El mismo código funciona para **how to add shape** de cualquier tipo.

## Paso 3: Aplicar una sombra predefinida y ajustarla finamente – *apply shadow to shape*  

Aspose.Words incluye varios formatos de sombra predefinidos. Usaremos `Preset1` y luego personalizaremos la distancia, difuminado, transparencia y color.

```csharp
// Choose a predefined shadow style
rectangleShape.Shadow.Format = ShadowFormat.Preset1;

// Adjust the shadow distance – this is the offset from the shape
rectangleShape.Shadow.Distance = 5; // measured in points

// Make the edge of the shadow a little fuzzy
rectangleShape.Shadow.BlurRadius = 3;

// Set the shadow to be 40 % transparent (0 = opaque, 1 = fully transparent)
rectangleShape.Shadow.Transparency = 0.4;

// Pick a gray tone for the shadow color
rectangleShape.Shadow.Color = Color.Gray;
```

> **¿Por qué personalizar la sombra?** La propiedad `Distance` controla qué tan lejos está la sombra del rectángulo, como el “elevado” que verías en una representación 3D. Cambiar `BlurRadius` suaviza los bordes, mientras que `Transparency` te permite crear un aspecto sutil y profesional. Esto cubre el requisito de **set shadow distance** y te muestra cómo **apply shadow to shape** de forma flexible.

## Paso 4: Guardar el documento – *create word document c#* finalización

Finalmente, escribe el documento en disco. Ajusta la ruta a una carpeta donde tengas permisos de escritura.

```csharp
// Save the document as a .docx file
string outputPath = @"C:\Temp\ShadowShape.docx";
document.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

Abre el archivo resultante en Microsoft Word y verás un rectángulo azul claro con una sombra gris suave desplazada 5 pt. Esa es la prueba visual de que has **create word document c#** con una forma con estilo.

![Create Word Document C# with Shadowed Shape](shadow-example.png){: .img alt="ejemplo de crear documento Word c# mostrando rectángulo con sombra"}

## Variaciones opcionales y casos límite

| Escenario | Qué cambiar | Por qué es importante |
|----------|----------------|----------------|
| **Estilo de sombra diferente** | `rectangleShape.Shadow.Format = ShadowFormat.Preset3;` | Te brinda un aspecto más dramático sin código adicional. |
| **Sin predefinido – sombra personalizada** | Omit `Format` and set `OffsetX`, `OffsetY` manually. | Control total sobre la dirección y profundidad. |
| **Múltiples formas** | Call `builder.InsertShape` again before saving. | Útil para plantillas complejas con íconos, logotipos, etc. |
| **Compatibilidad con versiones antiguas de Aspose** | Use `ShadowEffect` class (available in v20.x). | Garantiza que tu código se ejecute en proyectos heredados. |
| **Guardar como PDF** | `document.Save("ShadowShape.pdf");` | El mismo renderizado de sombra aparece en la salida PDF. |

> **Pregunta frecuente:** *¿Qué pasa si la sombra no aparece en Word?*  
> Asegúrate de estar usando una versión reciente de Aspose.Words (≥ 22.9). Las versiones anteriores tenían soporte limitado de sombras. También verifica que el documento se abra en una versión reciente de Word (2016+).

## Ejemplo completo funcional

A continuación está el programa completo, listo para copiar y pegar. Incluye todas las directivas `using`, comentarios y manejo de errores para una experiencia fluida.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShadowShapeDemo
{
    class Program
    {
        static void Main()
        {
            try
            {
                // 1️⃣ Create a new blank document and a builder
                Document doc = new Document();
                DocumentBuilder builder = new DocumentBuilder(doc);

                // 2️⃣ Insert a rectangle (200 pt × 100 pt) and fill it
                Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
                rect.FillColor = Color.LightBlue;

                // 3️⃣ Apply a preset shadow and tweak its properties
                rect.Shadow.Format = ShadowFormat.Preset1;   // predefined style
                rect.Shadow.Distance = 5;                    // set shadow distance
                rect.Shadow.BlurRadius = 3;                  // soften edges
                rect.Shadow.Transparency = 0.4;              // semi‑transparent
                rect.Shadow.Color = Color.Gray;              // shadow color

                // 4️⃣ Save the document
                string outPath = @"C:\Temp\ShadowShape.docx";
                doc.Save(outPath);

                Console.WriteLine($"✅ Document created successfully at {outPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"❌ Error: {ex.Message}");
            }
        }
    }
}
```

Ejecuta el programa, navega a `C:\Temp\ShadowShape.docx` y verás el rectángulo con la sombra exacta que configuramos.

## Recapitulación y próximos pasos

- Ahora sabes cómo **create word document c#**, insertar un rectángulo y **apply shadow to shape** con una **set shadow distance** personalizada.  
- El ejemplo usa Aspose.Words, que abstrae las complejidades de OpenXML y garantiza un renderizado consistente en todas las versiones de Word.  
- ¿Quieres ir más allá? Prueba combinar múltiples formas, añadir texto dentro del rectángulo o exportar el mismo documento como PDF para ver cómo se traslada la sombra.

### Temas relacionados que podrías explorar

- **How to add shape** a un encabezado/pie de página para branding.  
- Usar **Aspose.Words** para insertar gráficos y tablas programáticamente.  
- Personalizar **shadow effects** en imágenes en lugar de formas vectoriales.  
- Automatizar la generación masiva de documentos para facturas o certificados.

Siéntete libre de experimentar, romper el código y luego reconstruirlo: esa es la forma más rápida de interiorizar los conceptos. Si encuentras un problema, deja un comentario abajo o consulta la documentación oficial de Aspose.Words para obtener información más profunda de la API.

¡Feliz codificación y disfruta haciendo que tus archivos Word luzcan un poco más pulidos!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}