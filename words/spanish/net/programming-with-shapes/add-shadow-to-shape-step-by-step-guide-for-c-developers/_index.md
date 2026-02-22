---
category: general
date: 2026-02-21
description: Añadir sombra a una forma en C# y aprender cómo personalizar la sombra,
  aplicar el efecto de sombra y establecer la opacidad de la sombra con un ejemplo
  completo y ejecutable.
draft: false
keywords:
- add shadow to shape
- how to customize shadow
- apply shadow effect
- how to add shadow
- set shadow opacity
language: es
og_description: Añade sombra a una forma en C# con esta guía. Aprende cómo personalizar
  la sombra, aplicar el efecto de sombra y establecer la opacidad de la sombra en
  solo unas pocas líneas de código.
og_title: Añadir sombra a la forma – Tutorial completo de C#
tags:
- C#
- Aspose.Words
- Graphics
- Shadow Effect
title: Agregar sombra a la forma – Guía paso a paso para desarrolladores de C#
url: /es/net/programming-with-shapes/add-shadow-to-shape-step-by-step-guide-for-c-developers/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Añadir sombra a una forma – Tutorial completo en C#

¿Alguna vez necesitaste **añadir sombra a una forma** en un documento de Word pero no sabías por dónde empezar? No eres el único: muchos desarrolladores se topan con este obstáculo al pulir informes o folletos de marketing. ¿La buena noticia? En unos pocos pasos puedes convertir un rectángulo plano en un elemento pulido y tridimensional que destaca en la página.

En esta guía recorreremos un **ejemplo completo y ejecutable** que muestra cómo personalizar la sombra, aplicar el efecto de sombra e incluso establecer la opacidad de la sombra para cualquier forma. Al final tendrás un fragmento reutilizable que puedes insertar en cualquier proyecto de Aspose.Words, sin referencias misteriosas.

## Requisitos previos

Antes de sumergirnos, asegúrate de tener:

* **.NET 6.0** (o posterior) instalado – el código también funciona con .NET Framework 4.6+.
* **Aspose.Words for .NET** paquete NuGet – se recomienda la versión 23.9 o más reciente.
* Un conocimiento básico de C# y programación orientada a objetos.

Si te falta el paquete NuGet, ejecuta:

```bash
dotnet add package Aspose.Words
```

Ahora que la base está lista, pongámonos manos a la obra.

## Paso 1 – Cargar o crear un documento y obtener la primera forma

Lo primero que necesitamos es un objeto `Document` que realmente contenga una forma. Para el ejemplo crearemos un documento nuevo, insertaremos un rectángulo sencillo y luego lo obtendremos.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // 1️⃣ Create a blank document
        Document doc = new Document();

        // 2️⃣ Add a new shape (a rectangle) to the first paragraph
        Shape rect = new Shape(doc, ShapeType.Rectangle);
        rect.Width = 150;
        rect.Height = 100;
        rect.WrapType = WrapType.Inline;
        rect.StrokeColor = Color.DarkBlue;
        rect.FillColor = Color.LightBlue;
        rect.StrokeWeight = 2.0;

        // Insert the shape into the document body
        doc.FirstSection.Body.FirstParagraph.AppendChild(rect);

        // 3️⃣ Retrieve the shape we just added (demonstrates add shadow to shape)
        Shape firstShape = doc.GetChild(NodeType.Shape, 0, true) as Shape;
        if (firstShape == null)
        {
            Console.WriteLine("No shape found – aborting.");
            return;
        }

        // The remaining steps modify the shadow of firstShape
```

**Por qué lo hacemos:**  
Obtener la forma mediante `GetChild` imita escenarios del mundo real donde la forma ya existe (p. ej., cargada desde una plantilla). También garantiza que el código de sombra posterior trabaje sobre un objeto válido, evitando excepciones de referencia nula.

> **Consejo profesional:** Si trabajas con varias formas, usa `GetChild(NodeType.Shape, index, true)` o recorre `doc.GetChildNodes(NodeType.Shape, true)`.

## Paso 2 – Activar el efecto de sombra

La sombra de una forma está desactivada por defecto. Habilitarla es el primer requisito para cualquier personalización posterior.

```csharp
        // 4️⃣ Enable the shadow
        firstShape.Shadow.Enabled = true;
```

**Por qué es importante:**  
Sin establecer `Enabled = true`, cualquier cambio posterior de propiedades (color, desenfoque, desplazamiento) se ignora. Es como encender un interruptor antes de poder ajustar el brillo de una lámpara.

## Paso 3 – Elegir un color de sombra (y por qué el negro es un buen punto de partida)

La elección del color influye drásticamente en la profundidad percibida. El negro (o gris muy oscuro) es el más común porque funciona sobre cualquier fondo.

```csharp
        // 5️⃣ Set the shadow color – black gives a classic look
        firstShape.Shadow.Color = Color.Black;
```

**Alternativa:**  
Si tu documento tiene un fondo oscuro, prueba con un tono más claro:

```csharp
        // firstShape.Shadow.Color = Color.FromArgb(150, 150, 150); // light gray
```

## Paso 4 – Establecer la opacidad de la sombra

La opacidad se expresa como un valor entre `0.0` (totalmente transparente) y `1.0` (completamente opaco). Una sombra con un 40 % de transparencia se siente natural para la mayoría de los diseños de UI.

```csharp
        // 6️⃣ Make the shadow 40 % transparent
        firstShape.Shadow.Transparency = 0.4; // 0 = opaque, 1 = invisible
```

**Cómo personalizar:**  
- **Más sutil:** `0.2` (20 % transparente)  
- **Muy tenue:** `0.7` (70 % transparente)

## Paso 5 – Definir desenfoque y suavidad de los bordes

El desenfoque controla cuán suaves aparecen los bordes de la sombra. Un valor de `4.0` funciona bien para formas de tamaño medio.

```csharp
        // 7️⃣ Soften the edges with a blur radius
        firstShape.Shadow.Blur = 4.0;
```

**Casos límite:**  
Si estableces `Blur` a `0`, la sombra se convierte en una silueta de bordes duros, lo que puede resultar agresivo. Por el contrario, valores superiores a `10` pueden hacer que la sombra parezca un resplandor.

## Paso 6 – Posicionar la sombra respecto a la forma

Los valores de desplazamiento mueven la sombra horizontalmente (`OffsetX`) y verticalmente (`OffsetY`). Los números positivos desplazan la sombra hacia abajo y a la derecha.

```csharp
        // 8️⃣ Position the shadow 5 points right and 5 points down
        firstShape.Shadow.OffsetX = 5;
        firstShape.Shadow.OffsetY = 5;
```

**Experimenta:**  
- **Sombra caída:** `OffsetX = 0`, `OffsetY = 10`  
- **Efecto elevado:** `OffsetX = -5`, `OffsetY = -5`

## Paso 7 – Guardar y verificar el resultado

Finalmente, escribe el documento en disco y ábrelo en Microsoft Word (o cualquier visor compatible) para ver la sombra en acción.

```csharp
        // 9️⃣ Save the document
        string outPath = "ShadowedShape.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}. Open it to see the shadow.");
    }
}
```

Al abrir **ShadowedShape.docx**, deberías ver un rectángulo azul claro con una sombra negra suave y semitransparente desplazada cinco puntos. Si la sombra no aparece, verifica que `firstShape.Shadow.Enabled` sea `true` y que estés usando una versión reciente de Aspose.Words.

### Código fuente completo (listo para copiar y pegar)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class ShadowDemo
{
    static void Main()
    {
        Document doc = new Document();
        Shape rect = new Shape(doc, ShapeType.Rectangle);
        rect.Width = 150;
        rect.Height = 100;
        rect.WrapType = WrapType.Inline;
        rect.StrokeColor = Color.DarkBlue;
        rect.FillColor = Color.LightBlue;
        rect.StrokeWeight = 2.0;
        doc.FirstSection.Body.FirstParagraph.AppendChild(rect);

        Shape firstShape = doc.GetChild(NodeType.Shape, 0, true) as Shape;
        if (firstShape == null)
        {
            Console.WriteLine("No shape found – aborting.");
            return;
        }

        // Enable shadow
        firstShape.Shadow.Enabled = true;

        // Choose shadow color
        firstShape.Shadow.Color = Color.Black;

        // Set opacity (40 % transparent)
        firstShape.Shadow.Transparency = 0.4;

        // Soften edges
        firstShape.Shadow.Blur = 4.0;

        // Position shadow
        firstShape.Shadow.OffsetX = 5;
        firstShape.Shadow.OffsetY = 5;

        // Save document
        string outPath = "ShadowedShape.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}. Open it to see the shadow.");
    }
}
```

## Preguntas frecuentes y casos especiales

| Pregunta | Respuesta |
|----------|-----------|
| **¿Qué pasa si la forma es una imagen en lugar de un rectángulo?** | Se aplican las mismas propiedades de sombra; solo asegúrate de que `ShapeType` de la forma sea `Picture`. |
| **¿Puedo animar la sombra?** | Aspose.Words no soporta animación, pero puedes generar varias páginas con desplazamientos incrementales y usar PowerPoint para la animación. |
| **¿La sombra funciona en exportaciones a PDF?** | Sí. Cuando guardas el documento como PDF (`doc.Save("out.pdf")`), Aspose.Words conserva el efecto de sombra. |
| **¿Cómo elimino la sombra más adelante?** | Establece `firstShape.Shadow.Enabled = false;` o simplemente asigna `firstShape.Shadow = null`. |
| **¿Existe un límite para los valores de desenfoque?** | Prácticamente, valores superiores a `15` hacen que la sombra parezca un halo y pueden aumentar el tamaño del archivo. |

## Próximos pasos – Mantén el impulso

Ahora que sabes **cómo añadir sombra** y **establecer la opacidad de la sombra**, considera explorar:

* **Cómo personalizar aún más la sombra** con `Shadow.Distance` para un desplazamiento más pronunciado.
* **Aplicar el efecto de sombra** a marcos de texto o WordArt para diseños de documento más ricos.
* **Combinar múltiples sombras** (p. ej., interna + externa) para lograr un aspecto en capas.
* **Exportar a HTML** y observar cómo `box‑shadow` de CSS refleja la misma configuración.

Si estás construyendo un generador de informes, agrega sombras a encabezados, gráficos o recuadros de llamado para guiar la mirada del lector. Experimenta con diferentes colores y transparencias—quizá una sombra azul sutil para un tema corporativo.

---

### TL;DR

Recorrimos un **ejemplo completo y autónomo** que muestra cómo **añadir sombra a una forma**, **personalizar la sombra**, **aplicar el efecto de sombra** y **establecer la opacidad de la sombra** usando Aspose.Words en C#. El código está listo para ejecutarse, las explicaciones cubren tanto el *qué* como el *por qué*, y ahora tienes una base sólida para estilizar formas en cualquier proyecto de automatización de Word.

¡Feliz codificación, y que tus documentos siempre tengan ese toque extra‑dimensional!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}