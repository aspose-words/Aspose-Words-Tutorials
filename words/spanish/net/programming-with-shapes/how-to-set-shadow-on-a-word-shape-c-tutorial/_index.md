---
category: general
date: 2026-03-30
description: Aprende cómo aplicar sombra a una forma de Word usando C#. Esta guía
  también muestra cómo agregar sombra a una forma, ajustar la transparencia de la
  forma y agregar sombra a un rectángulo.
draft: false
keywords:
- how to set shadow
- adjust shape transparency
- add shape shadow
- how to add shadow
- add rectangle shadow
language: es
og_description: ¿Cómo establecer sombra en una forma de Word en C#? Sigue esta guía
  paso a paso para añadir sombra a la forma, ajustar la transparencia de la forma
  y agregar sombra al rectángulo.
og_title: Cómo establecer sombra en una forma de Word – Tutorial de C#
tags:
- Aspose.Words
- C#
- Word Automation
- Shapes
title: Cómo establecer sombra en una forma de Word – Tutorial de C#
url: /es/net/programming-with-shapes/how-to-set-shadow-on-a-word-shape-c-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo establecer sombra en una forma de Word – Tutorial C#

¿Alguna vez te has preguntado **cómo establecer sombra** en una forma dentro de un documento de Word sin tener que manipular la interfaz? No eres el único. En muchos informes o presentaciones de marketing, una sombra sutil hace que un rectángulo destaque, y hacerlo programáticamente ahorra horas.

En esta guía recorreremos un ejemplo completo, listo para ejecutar, que no solo muestra **cómo establecer sombra**, sino que también cubre **añadir sombra a la forma**, **ajustar la transparencia de la forma**, e incluso **añadir sombra al rectángulo** para esas clásicas cajas de llamado. Al final tendrás un archivo Word (`output.docx`) con un aspecto pulido, y comprenderás por qué cada propiedad es importante.

## Requisitos previos

- .NET 6+ (o .NET Framework 4.7.2) con un compilador C#  
- Paquete NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)  
- Familiaridad básica con C# y el modelo de objetos de Word  

No se requieren bibliotecas adicionales; todo reside dentro de Aspose.Words.

---

## Cómo establecer sombra en una forma de Word en C#

A continuación se muestra el archivo fuente completo. Guárdalo como `Program.cs` y ejecútalo desde tu IDE o con `dotnet run`. El código carga un `.docx` existente, encuentra la primera forma (un rectángulo por defecto), activa su sombra, ajusta algunos parámetros visuales y guarda el resultado.

```csharp
// Program.cs
using System;
using System.Drawing;               // For Color
using Aspose.Words;                // Core document API
using Aspose.Words.Drawing;        // Shape and shadow classes

class ShadowDemo
{
    static void Main()
    {
        // 1️⃣ Load the Word document that contains the shape.
        // Replace YOUR_DIRECTORY with the folder where your files live.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Retrieve the first shape in the document.
        // If you have multiple shapes, you can loop or use GetChild with a different index.
        Shape rectangleShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (rectangleShape == null)
        {
            Console.WriteLine("No shape found – make sure input.docx contains at least one shape.");
            return;
        }

        // 3️⃣ Enable the shape's shadow and choose a base color.
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = Color.Black;   // You can pick any System.Drawing.Color

        // 4️⃣ Fine‑tune the shadow appearance.
        rectangleShape.ShadowFormat.Transparency = 0.3;     // 30 % transparent (adjust shape transparency)
        rectangleShape.ShadowFormat.OffsetX = 5;           // Horizontal offset in points
        rectangleShape.ShadowFormat.OffsetY = 5;           // Vertical offset in points
        rectangleShape.ShadowFormat.BlurRadius = 4;       // Soft edge radius

        // 5️⃣ Save the updated document.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Shadow applied! Check {outputPath}");
    }
}
```

> **Lo que verás** – El rectángulo ahora muestra una sombra negra con un 30 % de transparencia, desplazada 5 pt a la derecha y hacia abajo, con un suave desenfoque. Abre `output.docx` en Word para comprobarlo.

## Ajustar la transparencia de la forma – Por qué es importante

La transparencia no es solo un control estético; influye en la legibilidad. Un valor de 0.0 hace que la sombra sea totalmente opaca, mientras que 1.0 la oculta por completo. En el fragmento anterior usamos `0.3` para lograr un efecto sutil que funciona tanto en fondos claros como oscuros. Siéntete libre de experimentar:

```csharp
rectangleShape.ShadowFormat.Transparency = 0.1; // Almost solid shadow
rectangleShape.ShadowFormat.Transparency = 0.6; // Very faint
```

Recuerda, **ajustar la transparencia de la forma** también puede aplicarse al color de relleno de la forma si necesitas un rectángulo semitransparente.

## Añadir sombra a la forma en diferentes objetos

El código que usamos apunta a un objeto `Shape`, pero las mismas propiedades de `ShadowFormat` existen en objetos **Image**, **Chart** e incluso **TextBox**. Aquí tienes un patrón rápido que puedes copiar‑pegar:

```csharp
// Assuming 'image' is an Aspose.Words.Drawing.Image object
image.ShadowFormat.Visible = true;
image.ShadowFormat.Color = Color.Gray;
image.ShadowFormat.OffsetX = 3;
image.ShadowFormat.OffsetY = 3;
image.ShadowFormat.BlurRadius = 2;
```

Así que, ya sea que estés **añadiendo sombra a la forma** a un logotipo o a un ícono decorativo, el enfoque sigue siendo idéntico.

## Cómo añadir sombra a cualquier forma – Casos límite

1. **Forma sin cuadro delimitador** – Algunas formas de Word (como garabatos libres) no admiten sombras. Intentar establecer `ShadowFormat.Visible` fallará silenciosamente. Verifica `shape.IsShadowSupported` si necesitas seguridad.  
2. **Versiones antiguas de Word** – Las propiedades de sombra se corresponden con funciones de Word 2007+. Si debes soportar Word 2003, la sombra será ignorada al abrir el archivo.  
3. **Múltiples sombras** – Actualmente Aspose.Words admite una sola sombra por forma. Si necesitas un efecto de doble capa, duplica la forma, desplázala y aplica diferentes configuraciones de sombra.

## Añadir sombra al rectángulo – Un caso de uso real

Imagina que estás generando un informe trimestral y cada encabezado de sección es un rectángulo coloreado. Añadir una **sombra al rectángulo** le da a la página un aspecto de “tarjeta”. Los pasos son idénticos al ejemplo base; solo asegúrate de que la forma que apuntas sea realmente un rectángulo (`shape.ShapeType == ShapeType.Rectangle`). Si necesitas crear el rectángulo desde cero, consulta el fragmento a continuación:

```csharp
// Create a new rectangle shape programmatically
Shape newRect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,
    Height = 50,
    WrapType = WrapType.Inline
};
newRect.FillColor = Color.LightBlue;

// Apply shadow (same settings as before)
newRect.ShadowFormat.Visible = true;
newRect.ShadowFormat.Color = Color.Black;
newRect.ShadowFormat.Transparency = 0.25;
newRect.ShadowFormat.OffsetX = 4;
newRect.ShadowFormat.OffsetY = 4;
newRect.ShadowFormat.BlurRadius = 3;

// Insert into the first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(newRect);
```

Ejecutar el programa completo con esta adición te proporcionará un rectángulo nuevo que ya lleva el efecto deseado de **sombra al rectángulo**.

---

![Word shape with shadow](placeholder-image.png){alt="cómo establecer sombra en una forma en Word"}

*Figura: El rectángulo después de aplicar la configuración de sombra.*

## Resumen rápido (Hoja de trucos en viñetas)

- **Cargar** el documento con `new Document(path)`.  
- **Localizar** la forma mediante `doc.GetChild(NodeType.Shape, index, true)`.  
- **Habilitar** la sombra: `shape.ShadowFormat.Visible = true;`.  
- **Establecer** el color con cualquier `System.Drawing.Color`.  
- **Ajustar** la transparencia (`0.0–1.0`) para controlar la opacidad.  
- **OffsetX / OffsetY** mueven la sombra horizontal/verticalmente (puntos).  
- **BlurRadius** suaviza el borde: valores mayores = sombra más difusa.  
- **Guardar** el archivo y ábrelo en Word para ver el resultado.

## ¿Qué probar a continuación?

- **Colores dinámicos** – Obtén el color de la sombra de un tema o de la entrada del usuario.  
- **Sombras condicionales** – Aplica una sombra solo cuando el ancho de la forma supera un umbral.  
- **Procesamiento por lotes** – Recorre todas las formas de un documento y **añade sombra a la forma** automáticamente.  

Si has seguido los pasos, ahora sabes **cómo establecer sombra**, cómo **ajustar la transparencia de la forma**, y cómo **añadir sombra al rectángulo** para lograr un acabado profesional. Experimenta, rompe cosas y luego arréglalas: la codificación es el mejor maestro.

---

*¡Feliz codificación! Si este tutorial te resultó útil, deja un comentario o comparte tus propios trucos de sombra. Cuanto más aprendamos unos de otros, más bonitos serán nuestros documentos de Word.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}