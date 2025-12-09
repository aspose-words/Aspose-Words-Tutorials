---
category: general
date: 2025-12-08
description: Agrega sombra a una forma rápidamente con Aspose.Words. Aprende cómo
  crear un documento Word usando Aspose, cómo agregar sombra a una forma y aplicar
  transparencia de sombra en C#.
draft: false
keywords:
- add shadow to shape
- create word document using aspose
- how to add shape shadow
- apply shadow transparency
language: es
og_description: Agrega sombra a una forma en un archivo de Word usando Aspose.Words.
  Esta guía paso a paso muestra cómo crear un documento, añadir una forma y aplicar
  transparencia a la sombra.
og_title: Añadir sombra a la forma – Tutorial de Aspose.Words C#
tags:
- Aspose.Words
- C#
- Word Automation
title: Agregar sombra a una forma en un documento de Word – Guía completa de Aspose.Words
url: /spanish/net/images-and-shapes/add-shadow-to-shape-in-a-word-document-complete-aspose-words/
---

{{< layout-start >}}

{{< layout-start >}}

# Agregar sombra a forma – Guía completa de Aspose.Words

¿Alguna vez necesitaste **agregar sombra a forma** en un archivo Word pero no estabas seguro de qué llamadas a la API usar? No estás solo. Muchos desarrolladores se topan con un obstáculo cuando intentan por primera vez dar a un rectángulo o cualquier elemento de dibujo una sombra adecuada, especialmente cuando trabajan con Aspose.Words para .NET.

En este tutorial repasaremos todo lo que necesitas saber: desde **crear un documento Word usando Aspose** hasta configurar la sombra, ajustar su desenfoque, distancia, ángulo e incluso **aplicar transparencia a la sombra**. Al final tendrás un programa C# listo para ejecutar que produce un archivo `.docx` con un rectángulo bien sombreado—sin necesidad de manipular manualmente Word.

---

## Lo que aprenderás

- Cómo configurar un proyecto Aspose.Words en Visual Studio.  
- Los pasos exactos para **crear documento Word usando Aspose** e insertar una forma.  
- **Cómo agregar sombra a una forma** con control total sobre desenfoque, distancia, ángulo y transparencia.  
- Consejos para solucionar problemas comunes (p. ej., licencia faltante, unidades incorrectas).  
- Un ejemplo completo de código copy‑and‑paste que puedes ejecutar hoy.

> **Requisitos previos:** .NET 6+ (o .NET Framework 4.7.2+), una licencia válida de Aspose.Words (o la prueba gratuita), y una familiaridad básica con C#.

## Paso 1 – Configura tu proyecto y agrega Aspose.Words

Primero lo primero. Abre Visual Studio, crea una nueva **Aplicación de consola (.NET Core)** y agrega el paquete NuGet Aspose.Words:

```bash
dotnet add package Aspose.Words
```

> **Consejo profesional:** Si tienes un archivo de licencia (`Aspose.Words.lic`), cópialo al directorio raíz del proyecto y cárgalo al iniciar. Esto evita la marca de agua que aparece en el modo de evaluación gratuito.

```csharp
// Load the license (optional but recommended)
var license = new Aspose.Words.License();
license.SetLicense("Aspose.Words.lic");
```

## Paso 2 – Crear un nuevo documento en blanco

Ahora realmente **creamos un documento Word usando Aspose**. Este objeto servirá como lienzo para nuestra forma.

```csharp
// Step 2: Initialize a new blank document
Document doc = new Document();   // Represents an empty .docx file
```

La clase `Document` es el punto de entrada para todo lo demás—párrafos, secciones y, por supuesto, objetos de dibujo.

## Paso 3 – Insertar una forma rectangular

Con el documento listo, podemos agregar una forma. Aquí elegimos un rectángulo simple, pero la misma lógica funciona para círculos, líneas o polígonos personalizados.

```csharp
// Step 3: Create a rectangular shape that will hold the shadow
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width  = 150,   // Width in points (1 point = 1/72 inch)
    Height = 100    // Height in points
};
```

> **¿Por qué una forma?** En Aspose.Words un objeto `Shape` puede contener texto, imágenes o simplemente actuar como un elemento decorativo. Agregar una sombra a una forma es mucho más fácil que intentar manipular un marco de imagen.

## Paso 4 – Configurar la sombra (Agregar sombra a forma)

Este es el corazón del tutorial—**cómo agregar sombra a una forma** y afinar su apariencia. La propiedad `ShadowFormat` te brinda control total.

```csharp
// Step 4: Enable the shadow and configure its appearance
rectangle.ShadowFormat.Visible       = true;   // Turn the shadow on
rectangle.ShadowFormat.Blur          = 5.0;    // Blur radius – higher = softer edges
rectangle.ShadowFormat.Distance      = 3.0;    // Offset distance from the shape
rectangle.ShadowFormat.Angle         = 45;     // Direction in degrees (0 = right, 90 = down)
rectangle.ShadowFormat.Transparency  = 0.3;    // 30 % transparent – this is how we **apply shadow transparency**
```

### Qué hace cada propiedad

| Propiedad | Efecto | Valores típicos |
|----------|--------|----------------|
| **Visible** | Activa o desactiva la sombra. | `true` / `false` |
| **Blur** | Suaviza los bordes de la sombra. | `0` (duro) a `10` (muy suave) |
| **Distance** | Aleja la sombra de la forma. | `1`–`5` puntos es común |
| **Angle** | Controla la dirección del desplazamiento. | `0`–`360` grados |
| **Transparency** | Hace que la sombra sea parcialmente translúcida. | `0` (opaco) a `1` (invisible) |

> **Caso límite:** Si estableces `Transparency` a `1`, la sombra desaparece por completo—útil para alternarla programáticamente.

## Paso 5 – Añadir la forma al documento

Ahora adjuntamos la forma al primer párrafo del cuerpo del documento. Aspose crea automáticamente un párrafo si no existe.

```csharp
// Step 5: Append the shape to the first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(rectangle);
```

Si tu documento ya contiene contenido, puedes insertar la forma en cualquier nodo usando `InsertAfter` o `InsertBefore`.

## Paso 6 – Guardar el documento

Finalmente, escribe el archivo en disco. Puedes elegir cualquier formato compatible (`.docx`, `.pdf`, `.odt`, etc.), pero para este tutorial nos quedaremos con el formato nativo de Word.

```csharp
// Step 6: Save the document with the shadowed shape
string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowedShape.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Abre el `ShadowedShape.docx` resultante en Microsoft Word, y verás un rectángulo con una sombra suave de 45 grados que es 30 % transparente—exactamente lo que configuramos.

## Ejemplo completo funcional

A continuación está el programa **completo, listo para copiar y pegar** que incorpora todos los pasos anteriores. Guárdalo como `Program.cs` y ejecútalo con `dotnet run`.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // OPTIONAL: Load Aspose.Words license (remove if using trial)
        // -------------------------------------------------
        try
        {
            var license = new License();
            license.SetLicense("Aspose.Words.lic");
        }
        catch (Exception ex)
        {
            Console.WriteLine("License not found – running in evaluation mode: " + ex.Message);
        }

        // -------------------------------------------------
        // 1. Create a new blank document
        // -------------------------------------------------
        Document doc = new Document();

        // -------------------------------------------------
        // 2. Insert a rectangle shape
        // -------------------------------------------------
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width  = 150,
            Height = 100
        };

        // -------------------------------------------------
        // 3. Configure the shadow – this is where we **add shadow to shape**
        // -------------------------------------------------
        rectangle.ShadowFormat.Visible      = true;   // Show the shadow
        rectangle.ShadowFormat.Blur         = 5.0;    // Soft edges
        rectangle.ShadowFormat.Distance     = 3.0;    // Offset distance
        rectangle.ShadowFormat.Angle        = 45;     // Direction in degrees
        rectangle.ShadowFormat.Transparency = 0.3;    // 30 % transparent (apply shadow transparency)

        // -------------------------------------------------
        // 4. Add the shape to the document
        // -------------------------------------------------
        doc.FirstSection.Body.FirstParagraph.AppendChild(rectangle);

        // -------------------------------------------------
        // 5. Save the file
        // -------------------------------------------------
        string outFile = Path.Combine(Environment.CurrentDirectory, "ShadowedShape.docx");
        doc.Save(outFile);
        Console.WriteLine($"Document created successfully: {outFile}");
    }
}
```

**Salida esperada:** Un archivo llamado `ShadowedShape.docx` que contiene un solo rectángulo con una sombra discreta, semi‑transparente, inclinada a 45°.

## Variaciones y consejos avanzados

### Cambiar el color de la sombra

Por defecto la sombra hereda el color de relleno de la forma, pero puedes establecer un color personalizado:

```csharp
rectangle.ShadowFormat.Color = System.Drawing.Color.Gray;
```

### Múltiples formas con sombras diferentes

Si necesitas varias formas, simplemente repite los pasos de creación y configuración. Recuerda dar a cada forma un nombre único si planeas referenciarlas más tarde.

### Exportar a PDF con sombras preservadas

Aspose.Words conserva los efectos de sombra al guardar en PDF:

```csharp
doc.Save("ShadowedShape.pdf");
```

### Problemas comunes

| Síntoma | Causa probable | Solución |
|---------|----------------|----------|
| La sombra no es visible | `ShadowFormat.Visible` dejado como `false` | Establecer a `true`. |
| La sombra parece demasiado dura | `Blur` establecido en `0` | Incrementar `Blur` a 3–6. |
| La sombra desaparece en PDF | Uso de una versión antigua de Aspose.Words (< 22.9) | Actualizar a la última biblioteca. |

## Conclusión

Hemos cubierto **cómo agregar sombra a una forma** usando Aspose.Words, desde la inicialización de un documento hasta afinar desenfoque, distancia, ángulo y **aplicar transparencia a la sombra**. El ejemplo completo muestra un enfoque limpio y listo para producción que puedes adaptar a cualquier forma o diseño de documento.

¿Tienes preguntas sobre **crear documento Word usando Aspose** para escenarios más complejos—como tablas con sombras o formas impulsadas por datos dinámicos? Deja un comentario abajo o revisa los tutoriales relacionados sobre manejo de imágenes y formato de párrafos en Aspose.Words.

¡Feliz codificación, y disfruta dando a tus documentos Word ese toque visual extra!

--- 

![ejemplo de agregar sombra a forma](shadowed_shape.png "ejemplo de agregar sombra a forma")

{{< layout-end >}}

{{< layout-end >}}