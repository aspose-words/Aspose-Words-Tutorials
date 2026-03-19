---
category: general
date: 2026-03-19
description: Crear documento Word en C# con Aspose.Words, aprender a añadir una forma,
  agregar una forma rectangular, aplicar sombra y guardar el documento como docx en
  minutos.
draft: false
keywords:
- create word document
- how to add shape
- add rectangle shape
- save document as docx
- add shadow to shape
language: es
og_description: Crear documento de Word con Aspose.Words, agregar una forma rectangular,
  aplicar sombra externa y guardar el documento como docx. Guía paso a paso.
og_title: Crear documento de Word – Añadir forma rectangular y sombra
tags:
- Aspose.Words
- C#
- Document Automation
title: Crear documento de Word – Cómo agregar una forma rectangular y sombra
url: /es/net/programming-with-shapes/create-word-document-how-to-add-rectangle-shape-and-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear documento Word – Cómo agregar forma rectangular y sombra

¿Alguna vez necesitaste **create word document** programáticamente y te preguntaste por dónde empezar? No estás solo. Muchos desarrolladores se topan con el mismo obstáculo cuando intentan generar un archivo .docx que contiene gráficos personalizados. En este tutorial recorreremos todo el proceso: cómo agregar una forma, específicamente un **add rectangle shape**, darle una elegante **add shadow to shape**, y finalmente **save document as docx**.  

Al final de la guía tendrás un fragmento de C# listo para usar que puedes insertar en cualquier proyecto .NET. Sin referencias vagas, solo un ejemplo completo y ejecutable.  

## Prerequisites

- .NET 6.0 o posterior (el código también funciona con .NET Framework).  
- Aspose.Words para .NET instalado (paquete NuGet `Aspose.Words`).  
- Un conocimiento básico de la sintaxis de C# — no se requiere nada avanzado.  

Si te falta la biblioteca, ejecuta:

```bash
dotnet add package Aspose.Words
```

Eso es todo — sin SDKs adicionales, sin interop COM, solo una referencia NuGet única.

---

## Step 1: Create a Word Document (Primary Goal)

Lo primero que necesitamos es un lienzo limpio. Piensa en la clase `Document` como una página nueva en Microsoft Word; contiene secciones, párrafos y todo lo que agregarás después.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // For Color

// Step 1: Initialize a new blank document
Document doc = new Document();               // This creates an empty .docx in memory
```

¿Por qué comenzar con un `Document` vacío? Porque garantiza que no se infiltre formato oculto de una plantilla. En mi experiencia, empezar desde cero evita cambios misteriosos de diseño cuando más adelante insertas formas.

---

## Step 2: Insert a Rectangle Shape – Adding the Visual Element

Ahora que tenemos un documento, vamos a **add rectangle shape** al primer párrafo. El objeto `Shape` es versátil; puedes elegir `ShapeType.Rectangle`, `Ellipse` o incluso dibujos personalizados. Aquí tienes el código mínimo:

```csharp
// Step 2: Create a rectangle and attach it to the first paragraph
Shape rect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,               // Width in points (≈2.78 inches)
    Height = 100,              // Height in points (≈1.39 inches)
    WrapType = WrapType.Inline // Makes the shape behave like a character
};

// Append the shape to the first paragraph (creates one if missing)
Paragraph firstPara = doc.FirstSection.Body.FirstParagraph;
firstPara.AppendChild(rect);
```

**What’s happening under the hood?**  
- `ShapeType.Rectangle` indica a Aspose que queremos una caja simple.  
- `WrapType.Inline` asegura que el rectángulo se mueva con el flujo del texto, que es lo que normalmente esperas en un escenario de procesamiento de texto.  
- Al añadirlo a `FirstParagraph`, evitamos la necesidad de insertar manualmente un nuevo párrafo; Aspose crea uno por nosotros si el documento está realmente vacío.

> **Pro tip:** Si necesitas que la forma quede *detrás* del texto, cambia `WrapType` a `WrapType.Transparent`. Ese pequeño ajuste puede producir una gran diferencia visual.

---

## Step 3: Apply an Outer Shadow – Enhancing the Look

Un rectángulo plano es… bueno, plano. Añadir un **add shadow to shape** le da profundidad sin imágenes adicionales. `ShadowFormat` de Aspose lo convierte en una sola línea.

```csharp
// Step 3: Configure an outer shadow for the rectangle
rect.ShadowFormat.Type = ShadowType.OuterShadow;
rect.ShadowFormat.Blur = 5.0;           // Softness of the shadow edge
rect.ShadowFormat.Distance = 3.0;      // How far the shadow is offset
rect.ShadowFormat.Angle = 45;          // Direction in degrees (45° = bottom‑right)
rect.ShadowFormat.Color = Color.Gray; // Classic gray shadow
```

¿Por qué usar esos valores específicos?  
- **Blur** de `5.0` brinda un borde sutilmente difuminado que se ve profesional en la mayoría de los monitores.  
- **Distance** de `3.0` y **Angle** de `45` crean una fuente de luz natural desde la esquina superior izquierda, una convención de diseño común.  
- **Color.Gray** funciona tanto en temas claros como oscuros; puedes cambiarlo a `Color.Black` si necesitas mayor contraste.

Si alguna vez necesitas una sombra *interior* (como un botón hundido), simplemente cambia `ShadowType.OuterShadow` a `ShadowType.InnerShadow`. Las mismas propiedades siguen aplicándose.

---

## Step 4: Save the Document as DOCX – Persisting Your Work

Todo lo divertido está bien, pero eventualmente querrás un archivo en disco. El paso **save document as docx** es directo:

```csharp
// Step 4: Persist the document to a .docx file
string outputPath = @"C:\Temp\ShadowedRectangle.docx";
doc.Save(outputPath, SaveFormat.Docx);
```

Un par de notas:  
- El enumerado `SaveFormat.Docx` garantiza el formato moderno Office Open XML, compatible con Word 2007+.  
- Si necesitas transmitir el archivo directamente a una respuesta web, reemplaza la ruta del archivo por un `MemoryStream` y escríbelo en la respuesta HTTP.

Después de ejecutar el código, abre `ShadowedRectangle.docx` en Microsoft Word. Deberías ver un rectángulo gris con una sombra suave, alineado en línea con el primer párrafo — exactamente lo que nos propusimos lograr.

---

## How to Add Shape – Alternative Approaches

El ejemplo anterior usa el enfoque *inline*, pero a veces deseas una forma que flote sobre el texto. Ahí es donde entra **how to add shape** con diferentes tipos de ajuste.

```csharp
Shape floatingRect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 250,
    Height = 120,
    WrapType = WrapType.Square, // Allows text to wrap around the shape
    RelativeHorizontalPosition = RelativeHorizontalPosition.Page,
    HorizontalAlignment = HorizontalAlignment.Center
};

doc.FirstSection.Body.FirstParagraph.AppendChild(floatingRect);
```

Aquí cambiamos `WrapType` a `Square` y centramos la forma en la página. Este patrón es útil para portadas o banners decorativos. Recuerda: las formas flotantes aumentan ligeramente el tamaño del archivo porque Word almacena datos de posicionamiento adicionales.

---

## Expected Output & Verification

Al abrir el archivo generado, deberías ver:

- Un solo párrafo que contiene un rectángulo gris.  
- El rectángulo mide aproximadamente 2.8 × 1.4 pulgadas.  
- Una sombra externa sutil desplazada hacia la esquina inferior derecha.  

Si la forma aparece *fuera* del párrafo, verifica el `WrapType`. Si la sombra se ve demasiado dura, reduce el valor de `Blur` o cambia el `Color` a un tono más claro.

---

## Common Pitfalls & How to Avoid Them

| Issue | Why it Happens | Fix |
|-------|----------------|-----|
| Shape disappears after saving | `WrapType` set to `Inline` but paragraph was removed | Ensure the paragraph exists; use `doc.FirstSection.Body.FirstParagraph` to guarantee it. |
| Shadow looks pixelated | Using a very low `Blur` value | Increase `Blur` to at least `3.0` for smooth edges. |
| File size balloons | Adding many high‑resolution images alongside shapes | Use `doc.RemoveUnusedResources()` before saving if you added images. |
| Color not showing on dark mode | Using a dark `Color` for the shape itself | Choose a contrasting color (e.g., `Color.White`) for better visibility. |

---

## Full Working Example

A continuación tienes el código completo, listo para copiar y pegar, que incorpora todo lo que hemos discutido. Siéntete libre de ejecutarlo como una aplicación de consola.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank Word document
        Document doc = new Document();

        // 2️⃣ Add a rectangle shape to the first paragraph
        Shape rect = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 200,
            Height = 100,
            WrapType = WrapType.Inline
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(rect);

        // 3️⃣ Apply an outer shadow to the rectangle
        rect.ShadowFormat.Type = ShadowType.OuterShadow;
        rect.ShadowFormat.Blur = 5.0;
        rect.ShadowFormat.Distance = 3.0;
        rect.ShadowFormat.Angle = 45;
        rect.ShadowFormat.Color = Color.Gray;

        // 4️⃣ Save the document as a .docx file
        string outPath = @"C:\Temp\ShadowShape.docx";
        doc.Save(outPath, SaveFormat.Docx);

        // Optional: Let the user know we’re done
        System.Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**Explanation of each block** is inline as comments, satisfying both SEO readers and AI assistants that love self‑contained answers.

---

## Conclusion

Acabamos de **create word document** desde cero, aprendimos **how to add shape**, específicamente un **add rectangle shape**, le dimos una **add shadow to shape**, y finalmente **save document as docx**. Los pasos son simples, el código es compacto y el resultado se ve pulido.  

Si estás listo para ir más allá, prueba a sustituir el rectángulo por una imagen personalizada, experimenta con diferentes colores de sombra, o genera un informe completo con múltiples secciones con formas. La API de Aspose.Words es lo suficientemente flexible como para manejar desde facturas hasta folletos de marketing.

¿Tienes preguntas sobre otros tipos de forma o necesitas ayuda para integrar esto en un servicio ASP.NET Core? ¡Deja un comentario abajo y feliz codificación! 

![crear documento word con forma rectangular y sombra](placeholder-image.png "crear documento word con forma rectangular y sombra

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}