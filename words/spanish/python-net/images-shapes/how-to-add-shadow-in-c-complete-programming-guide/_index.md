---
category: general
date: 2025-12-25
description: Cómo agregar sombra en C# con un ejemplo de código sencillo. Aprende
  a establecer la distancia de la sombra, personalizar el color y crear profundidad
  para tus gráficos.
draft: false
keywords:
- how to add shadow
- how to set shadow distance
language: es
og_description: Cómo agregar sombra en C# se explica paso a paso. Sigue la guía para
  establecer la distancia, el color y el desenfoque de la sombra para obtener formas
  de aspecto profesional.
og_title: Cómo agregar sombra en C# – Guía completa de programación
tags:
- C#
- graphics
- Aspose.Words
- shadows
title: Cómo agregar sombra en C# – Guía completa de programación
url: /es/python/images-shapes/how-to-add-shadow-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo agregar sombra en C# – Guía completa de programación

Agregar sombra en C# es una necesidad común cuando deseas que tus gráficos resalten en la página. En este tutorial recorreremos los pasos exactos para configurar la sombra de una forma, incluyendo cómo establecer la distancia de la sombra, ajustar el desenfoque y elegir el color correcto.  

Si alguna vez has mirado un rectángulo plano y pensado “esto podría usar un poco de profundidad”, estás en el lugar correcto. Comenzaremos con un documento en blanco, añadiremos una forma y terminaremos con una sombra pulida que parece haber sido colocada por un diseñador. Sin rodeos, solo un ejemplo práctico y ejecutable que puedes copiar‑pegar hoy.

## Qué aprenderás

- Crear un nuevo documento e insertar una forma programáticamente.  
- Aplicar un desenfoque suave a la sombra de la forma.  
- **Cómo establecer la distancia de la sombra** para que la sombra aparezca desplazada de forma natural.  
- Elegir un color de sombra que funcione en cualquier fondo.  
- Guardar el resultado como PDF (o cualquier formato que necesites).  

### Requisitos previos

- .NET 6.0 o posterior (el código funciona con .NET Core y .NET Framework).  
- Aspose.Words for .NET (versión de prueba gratuita o licenciada).  
- Un conocimiento básico de la sintaxis de C#.  

Eso es todo—sin bibliotecas adicionales, sin trucos. Vamos a sumergirnos.

![Ejemplo de una forma con una sombra negra suave – cómo agregar sombra](https://example.com/placeholder-shadow.png "ejemplo de cómo agregar sombra")

## Paso 1: Configurar el proyecto e importar espacios de nombres

Primero, crea una nueva aplicación de consola (o cualquier proyecto C#) y agrega el paquete NuGet Aspose.Words:

```bash
dotnet new console -n ShadowDemo
cd ShadowDemo
dotnet add package Aspose.Words
```

Ahora abre `Program.cs` y trae los espacios de nombres requeridos al alcance:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shadows;
using Aspose.Words.Drawing.Shapes;
using Aspose.Words.Saving;
```

> **Consejo profesional:** Si estás usando Visual Studio, el IDE sugerirá las declaraciones `using` por ti mientras escribes `Document`.

## Paso 2: Crear un nuevo documento y añadir una forma

Con las bibliotecas listas, podemos instanciar un objeto `Document` y colocar un rectángulo simple en la primera página.

```csharp
// Step 2: Initialize the document
Document doc = new Document();

// Add a blank page (Aspose.Words creates one automatically)
Section section = doc.FirstSection;

// Insert a rectangle shape – this will be the object we give a shadow
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    // Size the shape (width, height) in points (1 point = 1/72 inch)
    Width = 200,
    Height = 100,
    
    // Position the shape 100 points from the left and 150 from the top
    Left = 100,
    Top = 150,
    
    // Fill the shape with a light gray so the shadow stands out
    FillColor = System.Drawing.Color.LightGray
};

// Add the shape to the document's first page
section.Body.FirstParagraph.AppendChild(rectangle);
```

¿Por qué un rectángulo? Es un lienzo neutral que permite juzgar el efecto de la sombra sin distracciones. Puedes reemplazar `ShapeType.Rectangle` por `Ellipse` o `Star`; la lógica de la sombra permanece igual.

## Paso 3: Cómo agregar sombra – aplicar desenfoque, distancia y color

Ahora llega el corazón del tutorial: **cómo agregar sombra** a ese rectángulo. Aspose.Words expone un objeto `Shadow` en cada forma, permitiéndote ajustar el desenfoque, la distancia y el color.

```csharp
// Step 3: Access the shape's shadow settings
Shadow shadow = rectangle.Shadow;

// 3a) Apply a soft blur – larger values make the shadow fuzzier
shadow.Blur = 5.0;          // 5 points blur gives a subtle, professional look

// 3b) Set the shadow's offset distance – this determines how far the shadow is displaced
shadow.Distance = 3.0;      // 3 points offset is enough to suggest depth without looking detached

// 3c) Choose a shadow color – black works on most backgrounds, but you can experiment
shadow.Color = Color.Black; // Solid black; you could use Color.FromArgb(128, 0, 0, 0) for semi‑transparent

// OPTIONAL: Rotate the shadow to match a light source direction (45 degrees works well)
shadow.Angle = 45.0;
```

Observa el comentario `// 3b) Set the shadow's offset distance`. Esa línea responde directamente **cómo establecer la distancia de la sombra**. Al ajustar `shadow.Distance`, controlas la brecha visual entre la forma y su sombra, imitando una fuente de luz colocada en un ángulo específico.

### Por qué estos valores?

- **Blur = 5.0** – Un desenfoque suave evita una silueta dura mientras sigue siendo visible.  
- **Distance = 3.0** – Mantiene la sombra lo suficientemente cerca para que parezca proyectada por la propia forma.  
- **Color = Black** – Garantiza contraste tanto en fondos claros como oscuros.  

Siéntete libre de ajustar estos números; la API acepta cualquier valor `double` que necesites.

## Paso 4: Guardar el documento y verificar el resultado

Con la sombra configurada, simplemente escribimos el archivo en disco. Aspose.Words puede generar muchos formatos; PDF es una opción común para compartir.

```csharp
// Step 4: Save the document as a PDF (you could also use .docx, .png, etc.)
string outputPath = "ShadowedShape.pdf";
doc.Save(outputPath, SaveFormat.Pdf);

Console.WriteLine($"Document saved to {outputPath}. Open it to see the shadow effect.");
```

Abre `ShadowedShape.pdf` y deberías ver un rectángulo gris con una sombra negra suave desplazada ligeramente hacia la parte inferior‑derecha. Si la sombra parece demasiado tenue, aumenta `shadow.Blur` o `shadow.Distance` y vuelve a ejecutar.

## Preguntas frecuentes y casos límite

### ¿Qué pasa si necesito una sombra transparente?

Utiliza un color ARGB con un canal alfa inferior a 255:

```csharp
shadow.Color = Color.FromArgb(80, 0, 0, 0); // 80/255 opacity = ~31% transparent
```

### ¿Puedo aplicar la misma sombra a múltiples formas?

Absolutamente. Crea un método auxiliar:

```csharp
static void ApplyStandardShadow(Shape shape)
{
    shape.Shadow.Blur = 5.0;
    shape.Shadow.Distance = 3.0;
    shape.Shadow.Color = Color.Black;
}
```

Llama a `ApplyStandardShadow(rectangle);` para cada forma que añadas.

### ¿Esto funciona con versiones anteriores de .NET Framework?

Sí. Aspose.Words 22.9+ soporta .NET Framework 4.5 y superiores. Simplemente ajusta tu archivo de proyecto en consecuencia.

## Ejemplo completo funcional

A continuación se muestra el programa completo que puedes copiar en `Program.cs`. Compila y se ejecuta sin problemas (asumiendo que el paquete NuGet está instalado).

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shadows;
using Aspose.Words.Drawing.Shapes;
using Aspose.Words.Saving;

namespace ShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Initialize the document
            Document doc = new Document();
            Section section = doc.FirstSection;

            // Create a rectangle shape
            Shape rectangle = new Shape(doc, ShapeType.Rectangle)
            {
                Width = 200,
                Height = 100,
                Left = 100,
                Top = 150,
                FillColor = System.Drawing.Color.LightGray
            };
            section.Body.FirstParagraph.AppendChild(rectangle);

            // Apply shadow – this is the core of "how to add shadow"
            Shadow shadow = rectangle.Shadow;
            shadow.Blur = 5.0;                // Soft blur
            shadow.Distance = 3.0;            // How to set shadow distance
            shadow.Color = Color.Black;       // Classic black shadow
            shadow.Angle = 45.0;              // Light source direction

            // Save as PDF
            string outputPath = "ShadowedShape.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);

            Console.WriteLine($"Document saved to {outputPath}. Open it to see the shadow effect.");
        }
    }
}
```

Ejecuta el programa:

```bash
dotnet run
```

Encontrarás `ShadowedShape.pdf` en la carpeta del proyecto. Ábrelo con cualquier visor de PDF para confirmar que la sombra se ve como se describe.

## Conclusión

Hemos cubierto **cómo agregar sombra** a una forma en C# de principio a fin, y hemos mostrado **cómo establecer la distancia de la sombra** junto con el desenfoque y el color. Con solo unas pocas líneas de código puedes darle a tus gráficos una sensación profesional y tridimensional—sin necesidad de herramientas de diseño externas.

Ahora que dominas los conceptos básicos, prueba a experimentar:

- Cambia el color de la sombra a un azul sutil para un ambiente más fresco.  
- Aumenta el desenfoque para un efecto onírico y difuso.  
- Aplica la misma técnica a gráficos, imágenes o cuadros de texto.  

Cada variación refuerza los mismos conceptos básicos, por lo que te sentirás cómodo personalizando sombras para cualquier escenario.  

¿Tienes más preguntas? Deja un comentario, ¡y feliz codificación!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}