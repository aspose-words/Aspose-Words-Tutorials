---
category: general
date: 2026-05-01
description: Cómo mover la sombra en una forma en Aspose.Words usando C#. Aprende
  a agregar sombra a una forma, cambiar el desenfoque, establecer la transparencia
  y rotar la sombra en minutos.
draft: false
keywords:
- how to move shadow
- add shadow to shape
- how to change blur
- how to set transparency
- how to rotate shadow
language: es
og_description: Cómo mover la sombra en una forma en Aspose.Words usando C#. Este
  tutorial muestra cómo agregar sombra a una forma, cambiar el desenfoque, establecer
  la transparencia y rotar la sombra.
og_title: Cómo mover la sombra en Aspose.Words – Guía completa de C#
tags:
- Aspose.Words
- C#
- Document Automation
title: Cómo mover la sombra en Aspose.Words – Guía completa en C#
url: /es/net/programming-with-shapes/how-to-move-shadow-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo mover la sombra en Aspose.Words – Guía completa en C#

¿Alguna vez te has preguntado **cómo mover la sombra** de una forma dentro de un documento Word sin abrir Word manualmente? En mi trabajo diario, a menudo he necesitado ajustar la sombra de una forma de forma programática—ya sea para un informe pulido o una plantilla dinámica. ¿La buena noticia? Con Aspose.Words puedes hacerlo en unas pocas líneas, y también aprenderás **añadir sombra a una forma**, **cómo cambiar el desenfoque**, **cómo establecer la transparencia** y **cómo rotar la sombra** en el mismo paso.

En este tutorial recorreremos un escenario del mundo real: cargar un DOCX existente que ya contiene una forma, ajustar la posición, suavidad, opacidad y dirección de la sombra, y finalmente guardar el resultado. Al final tendrás un fragmento reutilizable que puedes insertar en cualquier proyecto .NET, y comprenderás por qué cada propiedad es importante.

## Prerrequisitos – Lo que necesitas antes de comenzar

- **Aspose.Words for .NET** (versión 23.12 o posterior). Puedes obtenerlo desde NuGet con `Install-Package Aspose.Words`.
- Un entorno de desarrollo .NET 6+ (Visual Studio, VS Code, Rider—lo que prefieras).
- Un archivo Word de entrada (`input.docx`) que ya contenga al menos una forma (un rectángulo, círculo o imagen sirve).
- Familiaridad básica con la sintaxis de C#—nada complicado.

Si te falta alguno de estos, haz una pausa e instala la biblioteca; el resto de la guía asume que el paquete ya está referenciado.

## Paso 1: Cargar el documento y obtener la forma objetivo – **Cómo mover la sombra** comienza aquí

Lo primero que hacemos es cargar el documento fuente y localizar la forma que queremos modificar. Aspose.Words trata cada objeto (párrafos, tablas, formas) como un nodo en un árbol, por lo que podemos consultarlo directamente.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // 📂 Load the source DOCX that already contains a shape with a shadow.
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

        // 🎯 Retrieve the first shape in the document.
        // The GetChild method walks the node tree; the third argument (true) means “search deep”.
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

        // If no shape is found, bail out early.
        if (shape == null)
        {
            System.Console.WriteLine("No shape found in the document.");
            return;
        }

        // -------------------------------------------------
        // The next sections show **how to move shadow**,
        // **add shadow to shape**, **how to change blur**,
        // **how to set transparency**, and **how to rotate shadow**.
        // -------------------------------------------------
```

> **Por qué importa:** Cargar el documento una sola vez y reutilizar la misma instancia de `Document` es eficiente. La llamada a `GetChild` es segura porque devuelve `null` si el índice está fuera de rango, lo que nos permite manejar formas ausentes de forma elegante.

## Paso 2: Ajustar el radio de desenfoque – Maestro **Cómo cambiar el desenfoque**

Una sombra suave se ve profesional, mientras que un borde duro puede resultar barato. La propiedad `BlurRadius` controla la suavidad en puntos (1 pt ≈ 1/72 pulgada). Vamos a aumentarla a 8 pt.

```csharp
        // Increase the blur radius to soften the shadow edges.
        shape.ShadowFormat.BlurRadius = 8.0; // 8 points ≈ 0.11 inches
```

> **Consejo profesional:** El desenfoque predeterminado es 0.5 pt. Cualquier valor superior a 5 pt suele ser perceptible, pero ten cuidado de no hacerlo demasiado grande—puede hacer que la forma parezca desprendida de la página.

## Paso 3: Establecer la transparencia – La respuesta a **Cómo establecer la transparencia**

La transparencia determina cuán translúcida es la sombra. Un valor de `0` significa totalmente opaco; `1` significa completamente invisible. Para un efecto sutil usaremos `0.3` (30 % transparente).

```csharp
        // Make the shadow semi‑transparent so the shape remains visible through it.
        shape.ShadowFormat.Transparency = 0.3; // 30% transparent
```

> **Por qué te puede importar:** Si la forma es oscura, una sombra totalmente opaca puede ahogar el texto subyacente. Ajustar la transparencia mantiene el documento legible mientras sigue proporcionando profundidad.

## Paso 4: Mover la sombra – El núcleo de **Cómo mover la sombra**

La propiedad `Distance` define qué tan lejos está la sombra de la forma, medida en puntos. Una distancia mayor desplaza la sombra más lejos, creando un efecto más dramático.

```csharp
        // Move the shadow farther from the shape for a more pronounced effect.
        shape.ShadowFormat.Distance = 4.0; // 4 points ≈ 0.055 inches
```

> **¿Qué pasa si necesitas un desplazamiento mínimo?** Establecer `Distance` a `0` hará que la sombra quede justo detrás de la forma, lo que puede ser útil para efectos de relieve.

## Paso 5: Rotar la fuente de luz – Resolviendo **Cómo rotar la sombra**

Las sombras no siempre van directamente hacia abajo; siguen el ángulo de la fuente de luz. La propiedad `Angle` (en grados) rota la sombra alrededor de la forma. Inclinémosla 45°.

```csharp
        // Rotate the light source to change the shadow direction.
        shape.ShadowFormat.Angle = 45; // 45 degrees clockwise from the vertical axis
```

> **Experimento rápido:** Prueba `90` para una sombra a la derecha o `-30` para una inclinada a la izquierda. El cambio visual es inmediato.

## Paso 6: Guardar el documento – Ver el resultado de **Añadir sombra a una forma**

Ahora que hemos ajustado la sombra, escribiremos el documento de nuevo en disco. Puedes sobrescribir el original o crear un nuevo archivo; el ejemplo usa un archivo de salida nuevo.

```csharp
        // Save the modified document with the adjusted shadow.
        doc.Save(@"YOUR_DIRECTORY\output.docx");

        System.Console.WriteLine("Shadow adjustments applied and saved to output.docx");
    }
}
```

> **Salida esperada:** Abre `output.docx`. La sombra de la forma aparecerá más suave, ligeramente desplazada, semi‑transparente y con un ángulo de 45°. Si la comparas lado a lado con `input.docx`, la diferencia es inconfundible.

### Ejemplo completo (listo para copiar y pegar)

A continuación tienes todo el programa en un solo bloque. Pégalo en un nuevo proyecto de consola, reemplaza `YOUR_DIRECTORY` con una ruta de carpeta real y ejecútalo.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // Load the source document that already contains a shape with a shadow.
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

        // Retrieve the first shape in the document (the one we will modify).
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

        if (shape == null)
        {
            System.Console.WriteLine("No shape found in the document.");
            return;
        }

        // 1️⃣ Change blur – soften the edges.
        shape.ShadowFormat.BlurRadius = 8.0;

        // 2️⃣ Set transparency – make it 30% see‑through.
        shape.ShadowFormat.Transparency = 0.3;

        // 3️⃣ Move the shadow – increase distance from the shape.
        shape.ShadowFormat.Distance = 4.0;

        // 4️⃣ Rotate the shadow – change light direction.
        shape.ShadowFormat.Angle = 45;

        // Save the result.
        doc.Save(@"YOUR_DIRECTORY\output.docx");
        System.Console.WriteLine("Shadow adjustments applied and saved to output.docx");
    }
}
```

## Preguntas frecuentes y casos límite

### ¿Qué pasa si el documento tiene múltiples formas?

Puedes iterar sobre todas las formas:

```csharp
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    // Apply the same shadow settings or customize per shape.
}
```

### ¿Puedo añadir una sombra a una forma que actualmente no tiene ninguna?

Claro. El objeto `ShadowFormat` siempre está presente; solo necesitas habilitarlo:

```csharp
shape.ShadowFormat.Enabled = true;
```

### ¿Funciona con imágenes y SmartArt?

Sí. Cualquier nodo que derive de `Shape`—incluyendo imágenes, gráficos y SmartArt—expondrá `ShadowFormat`. Las mismas propiedades se aplican.

### ¿Cómo controlo el color de la sombra?

Usa la propiedad `Color`:

```csharp
shape.ShadowFormat.Color = System.Drawing.Color.Gray;
```

### ¿Problemas de compatibilidad?

Aspose.Words 23.12+ soporta .NET 6, .NET Core 3.1 y .NET Framework 4.6.2+. La API mostrada es estable en estas versiones.

## Conclusión

Acabamos de cubrir **cómo mover la sombra** de una forma usando Aspose.Words, y en el proceso también demostramos **añadir sombra a una forma**, **cómo cambiar el desenfoque**, **cómo establecer la transparencia** y **cómo rotar la sombra**. El ejemplo completo y ejecutable te permite ajustar la sombra de cualquier forma en cuestión de segundos, dando a tus documentos un aspecto pulido y profesional sin abrir Word.

¿Listo para el siguiente paso? Prueba combinar estos ajustes de sombra con **formato condicional**—por ejemplo, aplicar una sombra más profunda solo a encabezados o a gráficos que superen cierto tamaño. O explora **rellenos degradados** para la propia forma y crea un diseño realmente llamativo.

Si encuentras algún obstáculo, deja un comentario abajo. ¡Feliz codificación, y que tus sombras siempre caigan justo donde deseas!

![Diagrama que muestra el efecto de mover una sombra en una forma – ejemplo de cómo mover la sombra](https://example.com/images/shadow-demo.png "ejemplo de cómo mover la sombra")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}