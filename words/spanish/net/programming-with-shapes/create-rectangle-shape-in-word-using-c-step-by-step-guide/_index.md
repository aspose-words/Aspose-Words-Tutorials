---
category: general
date: 2026-01-03
description: Crear una forma rectangular en Word con C# y añadir sombra a la forma.
  Aprende cómo insertar una forma en Word, añadir sombra a la forma y generar documentos
  de Word programáticamente.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- insert shape in word
- how to add shape
- c# generate word document
language: es
og_description: Crear una forma rectangular en Word con C# y agregar sombra a la forma.
  Sigue esta guía para insertar una forma en Word, configurar sombras y generar documentos
  programáticamente.
og_title: Crear forma de rectángulo en Word usando C# – Tutorial completo
tags:
- C#
- Word Automation
- Aspose.Words
title: Crear forma de rectángulo en Word usando C# – Guía paso a paso
url: /es/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear forma rectangular en Word usando C# – Tutorial completo

¿Alguna vez necesitaste **crear forma rectangular** en un documento de Word pero no sabías por dónde empezar? No estás solo—muchos desarrolladores se encuentran con el mismo problema cuando quieren **agregar sombra a la forma** para lograr un aspecto pulido. En este tutorial recorreremos los pasos exactos para **insertar una forma en Word**, aplicar una sombra sutil y, finalmente, **c# generar documentos Word** que puedes distribuir a los usuarios.

Cubriremos todo, desde la configuración del proyecto hasta el ajuste de las propiedades de la sombra, y terminaremos con un ejemplo de código listo para ejecutar. Sin rodeos, solo lo práctico que hace el trabajo.

## Lo que aprenderás

- Cómo **crear forma rectangular** con Aspose.Words (o Open XML) en C#
- Las propiedades exactas que necesitas para **agregar sombra a la forma** y darle profundidad
- Dónde colocar la forma usando `DocumentBuilder`
- Cómo guardar el archivo para que se abra correctamente en Microsoft Word
- Consejos, trampas y variaciones para escenarios del mundo real

### Requisitos previos

- .NET 6.0 o posterior (el código funciona en .NET Core y .NET Framework)
- Un paquete NuGet que pueda manipular archivos Word – usaremos **Aspose.Words for .NET** porque su API es concisa. Si prefieres Open XML SDK, los conceptos son los mismos, solo cambian las clases.
- Visual Studio, VS Code o cualquier IDE de C# que prefieras

> **Consejo profesional:** Si tienes un presupuesto limitado, Aspose ofrece una prueba gratuita que es perfecta para aprender. Simplemente reemplaza la línea de licencia con un comentario cuando pruebes.

## Paso 1: Instalar la biblioteca de procesamiento de Word

Primero, agrega la biblioteca a tu proyecto. Abre una terminal en la carpeta de tu solución y ejecuta:

```bash
dotnet add package Aspose.Words
```

Si estás usando el Open XML SDK, el comando sería `dotnet add package DocumentFormat.OpenXml`. El resto de esta guía asume Aspose.Words, pero cambiar las llamadas a la API es sencillo.

## Paso 2: Crear un nuevo documento en blanco

Ahora que la biblioteca está lista, podemos **crear forma rectangular** comenzando con un objeto `Document` limpio. Piensa en esto como un lienzo nuevo.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 2: Initialize a blank Word document
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);
```

El `DocumentBuilder` nos brinda una forma de alto nivel para insertar contenido sin sumergirnos en árboles de nodos de bajo nivel.

## Paso 3: Insertar la forma rectangular

Con el builder en mano, podemos **insertar una forma en Word**. El método `InsertShape` recibe el tipo de forma y sus dimensiones (ancho, alto) en puntos.

```csharp
// Step 3: Insert a rectangle shape – 150pt wide, 80pt high
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

En este punto el rectángulo aparece en el documento, pero se ve un poco plano. Ahí es donde entra el siguiente paso.

## Paso 4: Agregar sombra a la forma

Las sombras le dan a la forma una sensación de profundidad. El objeto `Shadow` nos permite ajustar finamente el desenfoque, la distancia, el ángulo, el color y la transparencia. A continuación se muestra una configuración completa que funciona bien para la mayoría de los informes.

```csharp
// Step 4: Configure a subtle shadow
rectangle.Shadow = new Shadow
{
    BlurRadius = 5.0,          // Soft edges
    Distance = 4.0,            // How far the shadow is offset
    Angle = 45,                // Direction in degrees (45° = down‑right)
    Color = Color.Black,       // Shadow color
    Transparency = 0.3         // 30 % transparent for a gentle look
};
```

**¿Por qué estos valores?**  
- **BlurRadius** de `5.0` mantiene el borde suave sin verse borroso.  
- **Distance** de `4.0` desplaza la sombra lo justo para ser perceptible.  
- **Angle** `45` imita la iluminación natural desde la esquina superior izquierda, una convención común en UI.  
- **Transparency** `0.3` evita que la sombra domine el relleno de la forma.  

Si necesitas un efecto más dramático, aumenta `BlurRadius` y disminuye `Transparency`. Para un levantamiento sutil, casi invisible, invierte esos números.

## Paso 5: Guardar el documento

Finalmente, escribe el archivo en disco. El método `Save` detecta el formato a partir de la extensión del archivo, por lo que `.docx` te da el formato moderno de Word.

```csharp
// Step 5: Persist the document
string outputPath = @"C:\Temp\ShadowRectangle.docx";
document.Save(outputPath);
```

Abre `ShadowRectangle.docx` en Microsoft Word, y verás un rectángulo nítido con una sombra suave—exactamente lo que querías cuando preguntaste “**cómo agregar forma**” con un acabado profesional.

![Crear forma rectangular con sombra en Word](placeholder-image.png "Crear forma rectangular con sombra en Word")

*Texto alternativo de la imagen: crear forma rectangular con sombra en Word*

## Ejemplo completo funcional

Juntándolo todo, aquí tienes el programa completo, listo para ejecutar. Copia y pega en una aplicación de consola y pulsa **F5**.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a new blank document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a rectangle shape (150pt × 80pt)
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 150, 80);

            // 3️⃣ Add a subtle shadow
            rect.Shadow = new Shadow
            {
                BlurRadius = 5.0,
                Distance = 4.0,
                Angle = 45,
                Color = Color.Black,
                Transparency = 0.3
            };

            // 4️⃣ Save the file
            string filePath = @"C:\Temp\ShadowRectangle.docx";
            doc.Save(filePath);

            System.Console.WriteLine($"Document saved to {filePath}");
        }
    }
}
```

### Resultado esperado

- El `ShadowRectangle.docx` generado contiene **una forma rectangular** centrada donde estaba el cursor.  
- El rectángulo muestra una **sombra negra suave, 30 % transparente** desplazada a un ángulo de 45°.  
- No se agrega otro contenido, manteniendo el archivo ligero y fácil de incrustar en informes más grandes.

## Preguntas comunes y casos límite

### ¿Qué pasa si necesito una forma diferente?

Reemplaza `ShapeType.Rectangle` con cualquier otro valor del enum `ShapeType` (p. ej., `Ellipse`, `Triangle`). La API de sombra funciona de la misma manera, por lo que puedes reutilizar la configuración.

### ¿Cómo cambio el color de relleno?

```csharp
rect.FillColor = Color.LightBlue;   // or any System.Drawing.Color
```

### ¿Puedo agregar la forma a un párrafo específico?

Sí. Mueve el `DocumentBuilder` al párrafo objetivo con `builder.MoveToParagraph(index)` antes de llamar a `InsertShape`. Esto asegura que la forma aparezca exactamente donde la necesitas.

### ¿Qué pasa con los formatos Word más antiguos (.doc)?

Simplemente cambia la extensión:

```csharp
doc.Save(@"C:\Temp\ShadowRectangle.doc", SaveFormat.Doc);
```

La función de sombra es compatible con Word 2003 y posteriores, por lo que aún verás el efecto.

### ¿Usar Open XML SDK en lugar de Aspose?

Los pasos siguen siendo los mismos: crear un `WordprocessingDocument`, agregar un elemento `Drawing`, establecer las propiedades `<a:shadow>`. El XML es más verboso, pero se aplican los mismos conceptos (tamaño, desenfoque, distancia, ángulo).

## Consejos para evitar errores

- **No olvides la licencia** si estás usando una versión paga de Aspose; de lo contrario obtendrás una marca de agua.  
- **Las unidades son puntos**, no píxeles. Un píxel típico de pantalla ≈ 0.75 pt, así que ajusta las dimensiones en consecuencia.  
- **Las propiedades de sombra se ignoran** si el `WrapType` de la forma está configurado como `Inline`. Usa `WrapType = WrapType.Square` para formas flotantes que respeten el renderizado de la sombra.  
- **Guardar en una unidad de red** puede requerir permisos adecuados; siempre prueba la ruta primero.

## Conclusión

Ahora sabes cómo **crear forma rectangular** en un documento de Word usando C#, **agregar sombra a la forma**, y **c# generar documentos Word** que se ven pulidos desde el primer momento. Los pasos principales—instalar la biblioteca, instanciar `Document`, insertar la forma, configurar la sombra y guardar—son fáciles de recordar y adaptables a otras formas, colores o incluso datos dinámicos.

¿Qué sigue? Prueba a superponer múltiples formas, incrustar imágenes o generar un informe completo con tablas y gráficos. También puedes explorar el formato condicional—cambiar la intensidad de la sombra según los valores de los datos—para que tus documentos no solo sean funcionales sino también visualmente atractivos.

Siéntete libre de experimentar, y si encuentras algún problema, deja un comentario abajo. ¡Feliz codificación, y que tus documentos Word siempre tengan esa sombra perfecta!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}