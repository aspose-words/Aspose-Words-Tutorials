---
category: general
date: 2026-07-03
description: Cómo establecer sombra en una forma en C# usando Aspose.Words. Aprende
  a agregar sombra a una forma, cambiar el desenfoque, ajustar la transparencia y
  guardar el documento como PDF.
draft: false
keywords:
- how to set shadow
- add shadow to shape
- save document as pdf
- how to change blur
- how to adjust transparency
language: es
og_description: Cómo aplicar sombra a una forma en C# con Aspose.Words. Esta guía
  muestra cómo agregar sombra a una forma, cambiar el desenfoque, ajustar la transparencia
  y guardar el documento como PDF.
og_title: Cómo establecer sombra en formas en C# – Tutorial completo de Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: How to set shadow on a shape in C# using Aspose.Words. Learn to add
    shadow to shape, change blur, adjust transparency, and save document as PDF.
  headline: How to Set Shadow on Shapes in C# – Complete Aspose.Words Guide
  type: TechArticle
- description: How to set shadow on a shape in C# using Aspose.Words. Learn to add
    shadow to shape, change blur, adjust transparency, and save document as PDF.
  name: How to Set Shadow on Shapes in C# – Complete Aspose.Words Guide
  steps:
  - name: – Load the Word Document
    text: '```csharp using System; using System.Drawing; // For Color using Aspose.Words;
      using Aspose.Words.Drawing; // Shape and shadow types'
  - name: – Retrieve the Target Shape
    text: '```csharp // Grab the first shape in the document (index 0). Shape shape
      = (Shape)doc.GetChild(NodeType.Shape, 0, true); if (shape == null) { Console.WriteLine("No
      shape found – make sure your .docx contains a drawing."); return; } ```'
  - name: – Add Shadow to Shape (Core of “how to set shadow”)
    text: '```csharp // Enable shadow and set its basic properties. shape.ShadowFormat.Visible
      = true; // Turn the shadow on. shape.ShadowFormat.Distance = 4.0; // Distance
      from the shape (in points). shape.ShadowFormat.BlurRadius = 6.0; // Softness
      of the shadow. shape.ShadowFormat.Transparency = 0.3; // 30 %'
  - name: – How to Change Blur on the Shadow
    text: '```csharp // Increase blur for a softer look, or decrease for a crisp edge.
      shape.ShadowFormat.BlurRadius = 12.0; // Example of a heavier blur. ```'
  - name: – How to Adjust Transparency of the Shadow
    text: '```csharp // Make the shadow more subtle. shape.ShadowFormat.Transparency
      = 0.6; // 60 % transparent (more see‑through). ```'
  - name: – Save Document as PDF to View the Shadow Effect
    text: '```csharp // Export the modified document to PDF so you can see the shadow.
      doc.Save("YOUR_DIRECTORY/ShadowAdjusted.pdf", SaveFormat.Pdf); Console.WriteLine("PDF
      saved – open ShadowAdjusted.pdf to see the shadow."); ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- PDF generation
title: Cómo establecer sombra en formas en C# – Guía completa de Aspose.Words
url: /es/net/programming-with-shapes/how-to-set-shadow-on-shapes-in-c-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo establecer sombra en formas en C# – Guía completa de Aspose.Words

¿Alguna vez te has preguntado **cómo establecer sombra** en una forma al generar documentos programáticamente? En mi experiencia, el acabado visual de una sombra sutil puede convertir un diagrama aburrido en algo que realmente *destaca* en la página. ¿La buena noticia? Con Aspose.Words puedes **agregar sombra a una forma** en solo unas pocas líneas de código C#, ajustar el desenfoque, controlar la transparencia y luego **guardar el documento como PDF** para ver el efecto al instante.

En este tutorial recorreremos cada paso que necesitas para dominar el estilo de sombras: cargar un archivo Word, localizar una forma, configurar su `ShadowFormat` y, finalmente, exportar el resultado como PDF. Al final sabrás **cómo cambiar el desenfoque**, comprenderás **cómo ajustar la transparencia** y tendrás un fragmento listo‑para‑ejecutar que puedes insertar en cualquier proyecto .NET.

## Cómo establecer sombra en una forma en Aspose.Words

Lo primero que necesitas es una referencia a la biblioteca Aspose.Words. Si aún no la has instalado, ejecuta:

```bash
dotnet add package Aspose.Words
```

Ahora sumergámonos en el código. Dividiremos el proceso en pasos pequeños para que puedas ver exactamente por qué cada línea es importante.

### Paso 1 – Cargar el documento Word

```csharp
using System;
using System.Drawing;               // For Color
using Aspose.Words;
using Aspose.Words.Drawing;        // Shape and shadow types

// Load a document that already contains at least one shape.
Document doc = new Document("YOUR_DIRECTORY/Shapes.docx");
```

*Por qué es importante:*  
`Document` es el punto de entrada para cada operación en Aspose.Words. Al cargar un archivo que ya contiene una forma, evitamos el código adicional de crear una forma desde cero—perfecto para una demostración enfocada en “cómo establecer sombra”.

### Paso 2 – Recuperar la forma objetivo

```csharp
// Grab the first shape in the document (index 0). 
Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
if (shape == null)
{
    Console.WriteLine("No shape found – make sure your .docx contains a drawing.");
    return;
}
```

*¿Qué está sucediendo aquí?*  
`GetChild` recorre el árbol DOM y devuelve el primer nodo de tipo `Shape`. La bandera `true` indica a la API que busque recursivamente, lo cual es útil cuando la forma está dentro de un encabezado, pie de página o cuadro de texto.

### Paso 3 – Agregar sombra a la forma (Núcleo de “cómo establecer sombra”)

```csharp
// Enable shadow and set its basic properties.
shape.ShadowFormat.Visible = true;          // Turn the shadow on.
shape.ShadowFormat.Distance = 4.0;          // Distance from the shape (in points).
shape.ShadowFormat.BlurRadius = 6.0;        // Softness of the shadow.
shape.ShadowFormat.Transparency = 0.3;      // 30 % transparent.
shape.ShadowFormat.Color = Color.Black;    // Shadow color.
```

**Cómo agregar sombra a una forma** – esa es la línea que estabas buscando. Establecer `Visible` a `true` activa el efecto; todo lo demás ajusta finamente su apariencia. Siéntete libre de experimentar con otros colores o distancias para que coincidan con tu marca.

#### Consejo profesional
Si necesitas una sombra paralela que imite una fuente de luz desde la esquina superior‑izquierda, también establece `shape.ShadowFormat.Angle = 45;` y `shape.ShadowFormat.Distance = 2.0;`. Este pequeño ajuste agrega realismo sin código adicional.

### Paso 4 – Cómo cambiar el desenfoque de la sombra

```csharp
// Increase blur for a softer look, or decrease for a crisp edge.
shape.ShadowFormat.BlurRadius = 12.0;   // Example of a heavier blur.
```

Cambiar `BlurRadius` responde directamente a **cómo cambiar el desenfoque**. El valor se mide en puntos; números mayores producen una sombra más difusa. Ten en cuenta que valores de desenfoque muy altos pueden aumentar ligeramente el tamaño del archivo PDF porque el renderizador necesita almacenar más información gráfica.

### Paso 5 – Cómo ajustar la transparencia de la sombra

```csharp
// Make the shadow more subtle.
shape.ShadowFormat.Transparency = 0.6;   // 60 % transparent (more see‑through).
```

La propiedad `Transparency` acepta un double entre `0.0` (totalmente opaco) y `1.0` (completamente invisible). Esta es la respuesta exacta a **cómo ajustar la transparencia** de la sombra de una forma. Usa un valor más bajo para elementos de UI audaces, y uno más alto para decoraciones de fondo.

### Paso 6 – Guardar el documento como PDF para ver el efecto de sombra

```csharp
// Export the modified document to PDF so you can see the shadow.
doc.Save("YOUR_DIRECTORY/ShadowAdjusted.pdf", SaveFormat.Pdf);
Console.WriteLine("PDF saved – open ShadowAdjusted.pdf to see the shadow.");
```

Aquí finalmente **guardamos el documento como PDF**, que es la forma más fiable de verificar los cambios visuales en distintas plataformas. PDF conserva la representación exacta de Aspose.Words, a diferencia de la vista previa de Word que podría ocultar efectos sutiles.

## Agregar sombra a una forma con configuraciones personalizadas (Avanzado)

A veces quieres una sombra que coincida con la paleta de colores de una marca. Puedes combinar los pasos anteriores en un método reutilizable:

```csharp
/// <summary>
/// Applies a customized shadow to the provided shape.
/// </summary>
static void ApplyCustomShadow(Shape shape, double distance, double blur, double transparency, Color color)
{
    shape.ShadowFormat.Visible = true;
    shape.ShadowFormat.Distance = distance;
    shape.ShadowFormat.BlurRadius = blur;
    shape.ShadowFormat.Transparency = transparency;
    shape.ShadowFormat.Color = color;
}

// Usage example:
ApplyCustomShadow(shape, 5.0, 8.0, 0.25, Color.FromArgb(80, 0, 0, 0));
```

*¿Por qué encapsularlo?*  
La encapsulación mantiene tu flujo de trabajo principal limpio y te permite **agregar sombra a una forma** con una sola llamada donde lo necesites—perfecto para procesar en lote decenas de documentos.

## Guardar documento como PDF – Errores comunes

- **Problemas con la ruta del archivo:** Siempre usa rutas absolutas o `Path.Combine` para evitar errores de “archivo no encontrado”.
- **Restricciones de licencia:** Si estás usando la versión de evaluación gratuita de Aspose.Words, el PDF generado contendrá una marca de agua. Compra una licencia para obtener una salida limpia.
- **Incrustación de fuentes:** Asegúrate de que las fuentes usadas en el `.docx` original estén disponibles en el servidor; de lo contrario el PDF puede sustituirlas, afectando la apariencia de la sombra.

## Cambiar el radio de desenfoque dinámicamente (Escenario del mundo real)

Imagina que estás generando un catálogo donde las imágenes de productos necesitan una sombra más fuerte para enfatizar. Podrías calcular `BlurRadius` en función del tamaño de la imagen:

```csharp
double ComputeBlur(double imageWidth)
{
    // Larger images get a softer shadow.
    return Math.Max(4.0, imageWidth / 50.0);
}

// Later in the pipeline:
double blur = ComputeBlur(shape.Width);
shape.ShadowFormat.BlurRadius = blur;
```

Este fragmento demuestra **cómo cambiar el desenfoque** programáticamente, adaptándose a contenido variable sin ajustes manuales.

## Ajustar la transparencia según el fondo (Consejo práctico)

Si el fondo del documento es oscuro, una sombra de color claro puede ser más visible. Aquí tienes una forma rápida de decidir la transparencia:

```csharp
double DetermineTransparency(Color background)
{
    // Dark backgrounds → lighter (more transparent) shadows.
    return background.GetBrightness() < 0.5 ? 0.5 : 0.2;
}

// Apply:
shape.ShadowFormat.Transparency = DetermineTransparency(Color.White);
```

Ahora has dominado **cómo ajustar la transparencia** según el contexto, un matiz a menudo pasado por alto en demostraciones rápidas.

## Ejemplo completo y funcional

A continuación se muestra el programa completo, listo‑para‑ejecutar, que une todo. Copia‑pega el código en una aplicación de consola, reemplaza `YOUR_DIRECTORY` con una carpeta real y observa cómo aparece el PDF.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the source document.
        Document doc = new Document("YOUR_DIRECTORY/Shapes.docx");

        // 2️⃣ Find the first shape.
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            Console.WriteLine("No shape found in the document.");
            return;
        }

        // 3️⃣ Apply a custom shadow (how to set shadow).
        ApplyCustomShadow(shape, distance: 4.0, blur: 10.0, transparency: 0.35, color: Color.Black);

        // 4️⃣ Save as PDF (save document as pdf) to view the result.
        doc.Save("YOUR_DIRECTORY/ShadowAdjusted.pdf", SaveFormat.Pdf);
        Console.WriteLine("Shadow applied and PDF saved successfully.");
    }

    /// <summary>
    /// Configures shadow properties for a shape.
    /// </summary>
    static void ApplyCustomShadow(Shape shape, double distance, double blur, double transparency, Color color)
    {
        shape.ShadowFormat.Visible = true;
        shape.ShadowFormat.Distance = distance;          // distance from shape
        shape.ShadowFormat.BlurRadius = blur;            // how to change blur
        shape.ShadowFormat.Transparency = transparency; // how to adjust transparency
        shape.ShadowFormat.Color = color;                // shadow color
    }
}
```

**Salida esperada:** Abre `ShadowAdjusted.pdf`. Verás la forma original (a menudo un rectángulo o imagen) ahora renderizada con una sombra negra suave y semi‑transparente desplazada 4 pt. El desenfoque debería verse suave, y el PDF mostrará exactamente lo que verías en la vista previa de impresión de Word.

## Conclusión

Hemos cubierto **cómo establecer sombra** en una forma usando Aspose.Words, demostrado **agregar sombra a una forma**, explicado **cómo cambiar el desenfoque**, mostrado **cómo ajustar la transparencia**, y finalmente **guardar el documento como PDF** para verificar el efecto. El enfoque es modular, por lo que puedes reutilizar el asistente `ApplyCustomShadow` en varios proyectos, ajustar los parámetros al vuelo e incluso ampliarlo para soportar múltiples formas por documento.

¿Próximos pasos? Intenta superponer múltiples sombras, experimentar con diferentes colores, o combinar esta técnica con el estilo de tablas para un informe pulido. Si te interesa una manipulación gráfica más profunda, explora las propiedades `ShapeBase` de Aspose.Words como `OutlineFormat` o investiga las opciones de renderizado PDF para un control aún más fino.

¡Feliz codificación, y que tus documentos siempre tengan la cantidad justa de profundidad!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Tutorial de sombra de forma Aspose.Words – Agregar una sombra a una forma Word en C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Cómo agregar sombra en C# – Guía completa de programación](/words/english/python-net/images-shapes/how-to-add-shadow-in-c-complete-programming-guide/)
- [Crear documento Word Java – Agregar forma rectangular con efecto de sombra](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}