---
category: general
date: 2026-04-10
description: cómo establecer sombra en una forma en C# – aprende a aplicar sombra
  paralela, cambiar la transparencia, ajustar el desenfoque y agregar sombra a la
  forma usando Aspose.Words.
draft: false
keywords:
- how to set shadow
- apply drop shadow
- how to change transparency
- how to adjust blur
- add shape shadow
language: es
og_description: cómo establecer sombra en una forma en C# – este tutorial muestra
  cómo aplicar sombra paralela, cambiar la transparencia, ajustar el desenfoque y
  añadir sombra a la forma con ejemplos de código claros.
og_title: Cómo establecer sombra en una forma en C# – Guía completa
tags:
- Aspose.Words
- C#
- Document Automation
title: Cómo establecer una sombra en una forma en C# – guía paso a paso
url: /es/net/programming-with-shapes/how-to-set-shadow-on-a-shape-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# cómo establecer sombra en una forma en C# – Guía completa

¿Alguna vez te has preguntado **cómo establecer sombra** en una forma cuando estás creando programáticamente un documento Word? No estás solo. Muchos desarrolladores se topan con un obstáculo cuando necesitan una sombra sutil para un cuadro de texto, un logotipo o un recuadro de llamada, y la documentación de la API resulta un poco escasa.  

En este tutorial recorreremos todo el proceso: desde cargar un `.docx`, obtener la primera `Shape`, hasta aplicar una sombra, ajustar su transparencia, modificar el radio de desenfoque y, finalmente, posicionarla correctamente. Al final tendrás un fragmento reutilizable que funciona con Aspose.Words .NET 2023 o posterior, y comprenderás *por qué* cada propiedad es importante.

## Lo que necesitarás

- **Aspose.Words for .NET** (paquete NuGet `Aspose.Words`) – la biblioteca que nos proporciona las clases `Document`, `Shape` y `ShadowFormat`.  
- **.NET 6+** (o .NET Framework 4.7.2) – cualquier runtime reciente servirá.  
- Un archivo Word sencillo (`input.docx`) que ya contenga al menos una forma, como un cuadro de texto.  
- Visual Studio, VS Code, o tu IDE favorito.

Eso es todo. Sin herramientas de terceros adicionales, sin interop COM, solo C# puro.

![how to set shadow example](image-placeholder.png){:alt="cómo establecer sombra en una forma en un documento Word"}

## Cómo establecer sombra – Visión general

La idea central detrás de **cómo establecer sombra** es manipular el objeto `ShadowFormat` que pertenece a una `Shape`. Piensa en `ShadowFormat` como una mini “hoja de estilo” para la propia sombra: le indica al renderizador si la sombra es visible, de qué color debe ser, cuán transparente es, cuán difusa, y dónde se sitúa en relación con la forma.  

A continuación se muestra el programa *completo* ejecutable. Siéntete libre de copiar‑pegarlo en una aplicación de consola, pulsar **F5**, y observar cómo la sombra aparece en el `output.docx` guardado.

```csharp
using System;
using System.Drawing;               // For Color
using Aspose.Words;                 // Core document classes
using Aspose.Words.Drawing;         // Shape & ShadowFormat

class ShadowDemo
{
    static void Main()
    {
        // -------------------------------------------------
        // Step 1: Load the Word document that contains the shape.
        // -------------------------------------------------
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // -------------------------------------------------
        // Step 2: Retrieve the first shape (e.g., a textbox) from the document.
        // -------------------------------------------------
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            Console.WriteLine("No shape found – make sure input.docx has a textbox.");
            return;
        }

        // -------------------------------------------------
        // Step 3: Make the shadow visible.
        // -------------------------------------------------
        shape.ShadowFormat.Visible = true;

        // -------------------------------------------------
        // Step 4: Set the shadow colour to a dark gray.
        // -------------------------------------------------
        shape.ShadowFormat.Color = Color.DarkGray;

        // -------------------------------------------------
        // Step 5: Define the shadow's transparency (30 % transparent).
        // -------------------------------------------------
        shape.ShadowFormat.Transparency = 0.3;   // 0 = opaque, 1 = fully transparent

        // -------------------------------------------------
        // Step 6: Configure the blur radius (size) of the shadow.
        // -------------------------------------------------
        shape.ShadowFormat.Size = 6;            // Larger value = softer edges

        // -------------------------------------------------
        // Step 7: Set the offset distance and direction (angle) of the shadow.
        // -------------------------------------------------
        shape.ShadowFormat.Distance = 2;        // How far the shadow is from the shape
        shape.ShadowFormat.Angle = 45;          // Angle in degrees (0 = right, 90 = down)

        // -------------------------------------------------
        // Save the modified document.
        // -------------------------------------------------
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Shadow applied successfully! Check output.docx.");
    }
}
```

### Por qué estas configuraciones importan

- **Visible** – Sin activar esta bandera, todas las demás propiedades se ignoran.  
- **Color** – Un gris oscuro imita una sombra típica de UI; puedes cambiar a cualquier `Color`.  
- **Transparency** – 0.3 brinda un aspecto *suave* manteniendo la forma legible.  
- **Size** – Controla el desenfoque; un valor de 6 suele ser suficiente para una sensación profesional.  
- **Distance & Angle** – Juntos definen el *offset*; 2 pts a 45° produce una sombra diagonal sutil.

Eso es la esencia de **cómo establecer sombra**. A continuación, desglosaremos cada parte para que puedas **aplicar sombra**, **cambiar la transparencia**, **ajustar el desenfoque**, y **agregar sombra a la forma** de forma aislada.

---

## Aplicar sombra a una forma

Cuando la gente pregunta “¿cómo **aplico drop shadow** en C#?”, a menudo solo necesitan el interruptor de visibilidad y un color. El siguiente fragmento aísla esas dos líneas:

```csharp
shape.ShadowFormat.Visible = true;          // Turns the shadow on
shape.ShadowFormat.Color   = Color.Black;   // Classic black drop shadow
```

> **Consejo profesional:** Si estás apuntando a versiones antiguas de Word (2003‑2007), utiliza colores estándar. Algunos valores ARGB exóticos pueden ser ignorados por el renderizador heredado.

---

## Cómo cambiar la transparencia de la sombra

La transparencia se expresa como un **float entre 0 y 1**. Un valor de **0** significa una sombra completamente opaca; **1** la hace invisible. La mayoría de los diseñadores se sitúan alrededor de **0.2‑0.4** para un aspecto natural.

```csharp
shape.ShadowFormat.Transparency = 0.35; // 35 % transparent
```

### Casos límite

- **Negative values** – Aspose.Words los limitará a 0, pero es mejor validar la entrada.  
- **Values > 1** – Se limitarán a 1, ocultando efectivamente la sombra.  

Si necesitas que los usuarios elijan un porcentaje, conviértelo primero:

```csharp
float percent = 30;                     // User enters 30 %
shape.ShadowFormat.Transparency = percent / 100f;
```

---

## Cómo ajustar el desenfoque (Size) de la sombra

La propiedad **Size** controla el radio de desenfoque. Números mayores producen una sombra más suave y difusa. Se mide en puntos (pt), no en píxeles.

```csharp
shape.ShadowFormat.Size = 10;  // A generous blur for a “soft” effect
```

#### Cuándo usar un desenfoque pequeño vs. grande

- **Small blur (2‑4 pt)** – Bueno para recuadros de estilo UI donde deseas un borde nítido.  
- **Large blur (8‑12 pt)** – Funciona bien para informes impresos o cuando la forma está lejos del fondo.

---

## Agregar sombra a la forma – Posicionamiento y dirección

La pieza final de **add shape shadow** es el desplazamiento. Dos propiedades trabajan juntas:

| Propiedad | Significado |
|----------|-------------|
| **Distance** | Qué tan lejos se sitúa la sombra de la forma (en puntos). |
| **Angle**    | Dirección del desplazamiento (0° = derecha, 90° = abajo, 180° = izquierda, 270° = arriba). |

Ejemplo que crea una sombra sutil inferior‑derecha:

```csharp
shape.ShadowFormat.Distance = 1.5; // Slight lift
shape.ShadowFormat.Angle    = 135; // Down‑left direction (135°)
```

Puedes experimentar con ángulos para simular luz proveniente de diferentes fuentes. Un truco común es permitir que el usuario elija una “fuente de luz” de un menú desplegable y la asocie a un valor de ángulo.

---

## Ejemplo completo (todos los pasos combinados)

A continuación está el mismo programa que antes, pero con **comentarios extra** que hacen la lógica cristalina. Copia esto en `Program.cs` y ejecútalo; el archivo de salida contendrá un cuadro de texto con una sombra perfectamente ajustada.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeShadowDemo
{
    class Program
    {
        static void Main()
        {
            // Load the source document (must contain at least one shape)
            Document doc = new Document("YOUR_DIRECTORY/input.docx");

            // Grab the first shape we encounter – usually a textbox or picture
            Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
            if (shape == null)
            {
                Console.WriteLine("No shape found in the document.");
                return;
            }

            // ---------- Apply Drop Shadow ----------
            shape.ShadowFormat.Visible = true;          // Turn it on
            shape.ShadowFormat.Color   = Color.DarkGray; // Soft dark colour

            // ---------- How to Change Transparency ----------
            shape.ShadowFormat.Transparency = 0.3; // 30 % transparent – looks natural

            // ---------- How to Adjust Blur ----------
            shape.ShadowFormat.Size = 6; // Moderate blur for a professional feel

            // ---------- Add Shape Shadow (position) ----------
            shape.ShadowFormat.Distance = 2; // Slight offset
            shape.ShadowFormat.Angle    = 45; // Diagonal down‑right

            // Save the result
            doc.Save("YOUR_DIRECTORY/output.docx");
            Console.WriteLine("Document saved with shadow. Open output.docx to verify.");
        }
    }
}
```

**Resultado esperado:** Abre `output.docx`. El primer cuadro de texto mostrará una sombra gris oscuro, 30 % transparente, ligeramente difusa (size = 6) y desplazada 2 pt a 45°. El efecto es sutil pero perceptible—exactamente lo que la mayoría de los diseñadores UI buscan.

---

## Preguntas comunes y trampas

- **“¿Esto funciona también con imágenes?”**  
  Sí. Cualquier `Shape`—ya sea un cuadro de texto, una imagen o una auto‑forma—expone `ShadowFormat`. Simplemente reemplaza la lógica de obtención de la forma por el índice o nombre apropiado.

- **“¿Qué pasa si el documento tiene múltiples formas?”**  
  Recorre `doc.GetChildNodes(NodeType.Shape, true)` y aplica la misma configuración a cada una. También puedes filtrar por `shape.Name` o `shape

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}