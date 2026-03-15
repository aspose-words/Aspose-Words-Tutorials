---
category: general
date: 2026-03-14
description: Añade sombra a una forma rápidamente y aprende cómo cambiar el ángulo
  de la sombra, guardar el documento con sombra y más en este tutorial paso a paso
  de C#.
draft: false
keywords:
- add shadow to shape
- change shadow angle
- how to add shape shadow
- save document with shadow
language: es
og_description: Agrega sombra a la forma rápidamente, aprende cómo cambiar el ángulo
  de la sombra y guarda el documento con sombra usando Aspose.Words para .NET.
og_title: Agregar sombra a una forma en C# – Guía completa de Aspose.Words
tags:
- Aspose.Words
- C#
- Document Automation
title: Agregar sombra a una forma en C# – Guía completa de Aspose.Words
url: /es/net/programming-with-shapes/add-shadow-to-shape-in-c-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Añadir sombra a una forma en C# – Guía completa de Aspose.Words

¿Alguna vez necesitaste **añadir sombra a una forma** pero no sabías qué propiedades modificar? No estás solo; muchos desarrolladores se topan con ese obstáculo al dar estilo a documentos Word de forma programática. La buena noticia es que con Aspose.Words puedes habilitar una sombra realista, ajustar su ángulo y guardar los cambios en un flujo de trabajo único y ordenado.  

En este tutorial repasaremos todo lo que necesitas saber: desde cargar un documento, habilitar la sombra, afinar su apariencia, hasta **guardar el documento con sombra**. Al final podrás responder “cómo añadir sombra a una forma” sin tener que buscar en foros dispersos.

## Lo que necesitarás

- **Aspose.Words for .NET** (v23.10 o posterior – la API que usamos no ha cambiado desde entonces)
- Un IDE compatible con .NET (Visual Studio, Rider o VS Code)
- Un archivo Word sencillo (`input.docx`) que ya contenga al menos una forma (un rectángulo, imagen o SmartArt sirve)
- Conocimientos básicos de C# – si ya has escrito un “Hello World”, estás listo

> **Consejo profesional:** Si no tienes un documento listo, crea uno rápidamente en Word, inserta una forma mediante *Insertar → Formas*, y guárdalo como `input.docx` en la carpeta de tu proyecto.

## Paso 1 – Cargar el documento y obtener la forma objetivo

Lo primero es cargar el archivo Word en memoria y localizar la forma que deseas decorar. Aspose.Words trata cada elemento de dibujo como un nodo `Shape`, que puedes obtener con `GetChild`.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Load the Word document that contains a shape.
Document doc = new Document("YOUR_DIRECTORY/input.docx");

// Retrieve the first shape in the document (index 0). 
// If you have multiple shapes, change the index or loop through them.
Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
```

**Por qué es importante:**  
`Document` es el punto de entrada para cualquier manipulación. La llamada a `GetChild` recorre el árbol de nodos en profundidad, asegurando que obtengas la primera forma sin importar dónde se encuentre (encabezado, pie de página, cuerpo). Si omites este paso y tratas de acceder a `shape` directamente, obtendrás una `NullReferenceException`.

## Paso 2 – Habilitar el efecto de sombra

Las sombras están desactivadas por defecto, así que debes activarlas antes de modificar cualquier propiedad visual. Es una sola línea, pero desbloquea toda una gama de opciones.

```csharp
// Turn the shadow on.
shape.Shadow.Enabled = true;
```

> **¿Lo sabías?** El objeto `Shadow` existe incluso cuando la función está desactivada, por lo que puedes preconfigurarlo y habilitarlo más tarde sin código adicional.

## Paso 3 – Configurar las propiedades principales de la sombra

Ahora llega la parte divertida: establecer color, transparencia, desenfoque, distancia y tamaño. Estos valores se expresan en puntos o porcentajes, reflejando la interfaz de Word.

```csharp
// Basic visual settings
shape.Shadow.Color = Color.Black;          // Shadow colour
shape.Shadow.Transparency = 0.3f;          // 30 % transparent
shape.Shadow.BlurRadius = 5.0f;            // Softness of the edge
shape.Shadow.Distance = 3.0f;              // Gap between shape and shadow
shape.Shadow.Size = 100;                   // Scale of the shadow (percent)
```

**Explicación:**  
- **Color** determina el tono; el negro funciona en la mayoría de los casos, pero puedes usar los colores de tu marca.  
- **Transparency** es un número flotante entre `0` (opaco) y `1` (totalmente invisible).  
- **BlurRadius** controla cuán “difusa” aparece la sombra; números mayores dan un aspecto más suave.  
- **Distance** aleja la sombra de la forma, creando profundidad.  
- **Size** escala la sombra proporcionalmente – 100 % significa que la sombra coincide con el tamaño de la forma.

## Paso 4 – Cambiar el ángulo de la sombra (Palabra clave secundaria)

Si deseas que la fuente de luz parezca venir de otra dirección, ajusta la propiedad `Angle`. Aquí es donde brilla la palabra clave **cambiar ángulo de sombra**.

```csharp
// Rotate the light source – 45 degrees is a common default.
shape.Shadow.Angle = 45;   // Angle in degrees (0‑360)
```

> **¿Qué pasa si necesitas un efecto dramático?** Prueba `0` para una luz de izquierda a derecha, `90` para luz de arriba a abajo, o `180` para una sombra invertida. Recuerda que los ángulos se envuelven, así que `360` equivale a `0`.

## Paso 5 – Guardar el documento con sombra

Una vez que la sombra tiene el aspecto deseado, persiste los cambios. El método `Save` escribe un nuevo archivo sin tocar el original.

```csharp
// Save the modified document.
doc.Save("YOUR_DIRECTORY/output.docx");
```

Ahora tienes un `output.docx` donde la forma muestra una sombra pulida. Ábrelo en Word para verificar – deberías ver un halo sutil y semitransparente desplazado según el ángulo que configuraste.

## Ejemplo completo funcionando

A continuación tienes el programa completo, listo para copiar y pegar en una aplicación de consola. Los comentarios explican cada bloque.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the source document.
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Grab the first shape (adjust index if needed).
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            System.Console.WriteLine("No shape found in the document.");
            return;
        }

        // 3️⃣ Enable shadow.
        shape.Shadow.Enabled = true;

        // 4️⃣ Set visual properties.
        shape.Shadow.Color = Color.Black;
        shape.Shadow.Transparency = 0.3f;
        shape.Shadow.BlurRadius = 5.0f;
        shape.Shadow.Distance = 3.0f;
        shape.Shadow.Size = 100;

        // 5️⃣ Change shadow angle (how to add shape shadow from a different direction).
        shape.Shadow.Angle = 45; // Try 0, 90, 180, etc.

        // 6️⃣ Save the result – this is the step that lets you **save document with shadow**.
        doc.Save("YOUR_DIRECTORY/output.docx");

        System.Console.WriteLine("Shadow applied and document saved successfully!");
    }
}
```

### Resultado esperado

- Al abrir `output.docx` la forma original aparece ahora rodeada por una sombra suave y negra.  
- Cambiar `Angle` a `90` hará que la sombra aparezca directamente debajo de la forma, imitando una iluminación superior.  
- Ajustar `Transparency` a `0.0f` produce una sombra opaca, mientras que `1.0f` la vuelve invisible (útil para alternar).

## Problemas comunes y cómo evitarlos

| Problema | Por qué ocurre | Solución |
|----------|----------------|----------|
| **`shape` es `null`** | El documento no tiene formas o el índice es incorrecto. | Verifica que el archivo Word contenga una forma, o recorre `doc.GetChildNodes(NodeType.Shape, true)` para encontrar la correcta. |
| **La sombra no aparece en Word** | `Shadow.Enabled` quedó en `false` o el tipo de forma no admite sombras (p. ej., texto plano). | Asegúrate de estar trabajando con un objeto `Shape` (imágenes, dibujos, SmartArt) y que `Enabled = true`. |
| **Color inesperado** | `Color` se estableció a algo distinto de lo que ves en Word debido a sobrescrituras de tema. | Usa `Color.FromArgb(0,0,0)` para un negro puro, o iguala el tema del documento con `shape.Shadow.ThemeColor`. |
| **Ralentización del rendimiento** | Modificar muchas formas en un documento grande sin agrupar. | Envuelve los cambios en `doc.BeginUpdateWords()` / `doc.EndUpdateWords()` (Aspose.Words v24+). |

## Extender el ejemplo

- **Múltiples formas:** Recorre todas las formas y aplica una sombra uniforme, o varía `Angle` por forma para lograr un efecto 3‑D.  
- **Colores dinámicos:** Obtén los valores de color de un archivo de configuración para coincidir con la identidad corporativa.  
- **Sombras condicionales:** Añade sombra solo si el ancho de la forma supera un umbral determinado – ideal para resaltar diagramas grandes.

```csharp
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    if (s.Width > 200) // width in points
    {
        s.Shadow.Enabled = true;
        s.Shadow.Color = Color.Gray;
        s.Shadow.Angle = 30;
    }
}
```

## Conclusión

Hemos cubierto todo el ciclo de vida de **añadir sombra a una forma** usando Aspose.Words para .NET: cargar el documento, habilitar la sombra, personalizar color, desenfoque, distancia, **cambiar el ángulo de sombra**, y finalmente **guardar el documento con sombra**. El código es autónomo, funciona con cualquier versión reciente de Aspose.Words y muestra tanto el “cómo” como el “por qué” detrás de cada propiedad.

¿Listo para el siguiente paso? Prueba experimentar con sombras degradadas, o combina esta técnica con efectos de texto para crear informes llamativos. Si te encuentras con casos extremos —como formas dentro de encabezados o pies de página— recuerda los trucos de recorrido del árbol de nodos que discutimos.  

¡Feliz codificación, y que tus documentos siempre tengan la profundidad perfecta!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}