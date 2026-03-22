---
category: general
date: 2026-03-22
description: Crear una forma rectangular en C# y agregar sombra a la forma con Aspose.Words.
  Aprende cómo añadir sombra, cómo crear un rectángulo y cómo establecer las propiedades
  de la sombra.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- how to add shadow
- how to create rectangle
- how to set shadow
language: es
og_description: Crear una forma rectangular en C# y añadir sombra a la forma usando
  Aspose.Words. Guía paso a paso que cubre cómo añadir sombra, cómo crear un rectángulo
  y cómo configurar la sombra.
og_title: Crear forma de rectángulo con sombra en C# – Guía completa
tags:
- Aspose.Words
- C#
- Document Automation
title: Crear forma de rectángulo con sombra en C# usando Aspose.Words
url: /es/net/programming-with-shapes/create-rectangle-shape-with-shadow-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear forma rectangular con sombra en C# usando Aspose.Words

¿Alguna vez necesitaste **crear una forma rectangular** en un documento Word pero no sabías cómo darle una sombra sutil? No estás solo: muchos desarrolladores se topan con ese problema cuando se inician en la automatización de documentos. En esta guía veremos paso a paso cómo **añadir sombra a una forma** usando Aspose.Words, y también responderemos a “**cómo añadir sombra**”, “**cómo crear un rectángulo**” y “**cómo establecer la sombra**” a lo largo del camino.

Comenzaremos con un `Document` limpio, dibujaremos un rectángulo, activaremos su sombra, ajustaremos el desenfoque, la distancia, el ángulo y el color, y finalmente guardaremos el archivo. Al final tendrás un `.docx` listo para usar que muestra un rectángulo de tono gris flotando justo sobre la página. Sin misterios, solo código directo que puedes copiar‑pegar en cualquier proyecto .NET.

## Requisitos previos

Antes de sumergirnos, asegúrate de tener:

* **Aspose.Words for .NET** (la última versión a partir de marzo 2026). Puedes obtenerlo desde NuGet con `Install-Package Aspose.Words`.
* Un entorno de desarrollo .NET – Visual Studio, Rider o incluso VS Code con la extensión C# funciona perfectamente.
* Conocimientos básicos de C# – nada sofisticado, solo la capacidad de crear una aplicación de consola o WinForms.

Eso es todo. Sin bibliotecas extra, sin pasos ocultos. ¿Listo? Vamos a comenzar.

## Paso 1: Inicializar un nuevo documento vacío

Para **crear una forma rectangular**, primero necesitamos un contenedor – un objeto `Document` – que represente el archivo Word.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new empty document
Document document = new Document();
```

La clase `Document` es el punto de entrada para todo lo que hace Aspose.Words. Piensa en ella como un lienzo en blanco; sin ella no puedes añadir formas, tablas o texto.

## Paso 2: Crear el rectángulo que contendrá la sombra

Ahora **cómo crear un rectángulo** instanciando un `Shape` de tipo `Rectangle`. También establecemos su tamaño en puntos (1 punto ≈ 1/72 de pulgada).

```csharp
// Step 2: Create a rectangular shape that will hold the shadow
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 200; // width in points
rectangleShape.Height = 100; // height in points
```

¿Por qué elegir 200 × 100 puntos? Es un tamaño decente para una demo: lo suficientemente grande para ver la sombra claramente, pero no tan enorme que abrume la página. Siéntete libre de ajustar esos números según tu diseño.

## Paso 3: Habilitar el efecto de sombra y configurar su apariencia

Aquí está el corazón del tutorial: **cómo añadir sombra** y **cómo establecer la sombra**. Aspose.Words expone un objeto `Shadow` en cada forma, permitiéndote activar el efecto y ajustar los parámetros visuales.

```csharp
// Step 3: Enable the shadow effect and configure its appearance
rectangleShape.Shadow.Enabled    = true;                     // turn the shadow on
rectangleShape.Shadow.BlurRadius = 5;                       // blur radius in pixels
rectangleShape.Shadow.Distance   = 8;                       // distance from the shape in pixels
rectangleShape.Shadow.Angle      = 45;                      // direction of the light source (degrees)
rectangleShape.Shadow.Color      = System.Drawing.Color.Gray; // shadow color
```

* **BlurRadius** suaviza los bordes – un valor mayor hace que la sombra se vea más difusa.
* **Distance** aleja la sombra más lejos del rectángulo.
* **Angle** determina de dónde parece venir la luz; 45° produce una sombra diagonal y natural.
* **Color** te permite elegir cualquier `System.Drawing.Color`. El gris es un valor predeterminado seguro, pero podrías usar `Color.Black` para un contraste fuerte o `Color.LightGray` para algo sutil.

Consejo profesional: Si estableces `Enabled = false`, se ignoran todas las demás configuraciones de sombra, así que verifica siempre esa bandera.

## Paso 4: Insertar la forma en el cuerpo del documento

Con el rectángulo listo y su sombra configurada, debemos colocarlo dentro del documento. La forma más sencilla es añadirlo al primer párrafo de la primera sección.

```csharp
// Step 4: Insert the shape into the first paragraph of the document body
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

Si tu documento ya contiene texto, podrías localizar un `Paragraph` específico o incluso una celda de `Table` e insertar la forma allí. El método `AppendChild` es versátil – funciona con cualquier tipo de `Node`.

## Paso 5: Guardar el documento y verificar el resultado

Finalmente, escribimos el archivo en disco. Cambia la ruta a donde prefieras; la carpeta debe existir, de lo contrario obtendrás una excepción.

```csharp
// Step 5: Save the document with the shadowed shape
document.Save(@"C:\Temp\ShadowedRectangle.docx");
```

Abre el `ShadowedRectangle.docx` resultante en Microsoft Word (o LibreOffice) y deberías ver un rectángulo gris con una sombra nítida y diagonal que se desplaza hacia abajo‑derecha. Si la sombra parece demasiado tenue, aumenta `BlurRadius` o `Distance` y vuelve a ejecutar el código – la experimentación es parte de la diversión.

![Create rectangle shape with shadow example](rectangle-shadow.png){alt="Ejemplo de forma rectangular con sombra"}

### Resultado esperado

* Un documento Word de una sola página.
* Un rectángulo gris de 200 × 100 puntos posicionado en la esquina superior izquierda de la página.
* Una sombra gris sutil desplazada 8 píxeles a 45°, difuminada 5 píxeles.

## Cómo añadir sombra a una forma – inmersión profunda

Quizás te preguntes, *“¿Puedo animar la sombra o hacer que cambie según la entrada del usuario?”* Aunque Aspose.Words no soporta animación, puedes ajustar programáticamente las propiedades de la sombra antes de guardar, creando efectivamente múltiples versiones del mismo documento con diferentes apariencias. Por ejemplo, iterando sobre una colección de colores:

```csharp
Color[] shadowColors = { Color.Gray, Color.Black, Color.DarkSlateGray };
foreach (var col in shadowColors)
{
    rectangleShape.Shadow.Color = col;
    document.Save($@"C:\Temp\Shadow_{col.Name}.docx");
}
```

Ese pequeño fragmento muestra **cómo establecer la sombra** de forma dinámica—ideal para generar informes temáticos.

## Cómo crear un rectángulo – formas alternativas

Si necesitas un rectángulo con esquinas redondeadas, simplemente cambia el `ShapeType`:

```csharp
Shape rounded = new Shape(document, ShapeType.RoundRectangle);
rounded.Width  = 200;
rounded.Height = 100;
rounded.Shadow.Enabled = true; // shadow works the same way
```

O, para un cuadrado perfecto, establece `Width` igual a `Height`. Las mismas propiedades de sombra se aplican, así que ya estás cubierto en **cómo añadir sombra** para cualquier forma que elijas.

## Problemas comunes y solución de errores

| Síntoma | Causa probable | Solución |
|---------|----------------|----------|
| La sombra no aparece | `Shadow.Enabled` quedó en `false` | Establece `rectangleShape.Shadow.Enabled = true;` |
| La sombra se ve demasiado nítida | `BlurRadius` está en 0 | Incrementa `BlurRadius` al menos a 3 |
| El documento lanza `FileNotFoundException` al guardar | La carpeta de destino no existe | Crea la carpeta primero o usa una ruta válida |
| La forma es invisible | Ancho/Alto establecidos en 0 | Asegúrate de que ambas dimensiones sean > 0 |

Mantener la vista en estos problemas te ahorra el clásico momento de “¿por qué no se muestra mi forma?”.

## Recapitulación – lo que hemos logrado

* **Crear forma rectangular** en un nuevo documento Word usando Aspose.Words.  
* **Añadir sombra a la forma** activando la bandera `Shadow.Enabled` y ajustando desenfoque, distancia, ángulo y color.  
* Demostrado **cómo añadir sombra**, **cómo crear un rectángulo** y **cómo establecer la sombra** en un fragmento de código limpio y reutilizable.  
* Proporcionado un ejemplo completo, listo para ejecutar, que puedes pegar en cualquier proyecto C#.

## ¿Qué sigue?

Ahora que dominas lo básico, considera explorar:

* **Cómo añadir sombra a imágenes** – la misma API `Shadow` funciona para `ShapeType.Image`.
* **Combinar múltiples formas** – crea diagramas de flujo o infografías directamente en Word.
* **Exportar a PDF** – llama a `document.Save("output.pdf")` después de añadir sombras para una versión imprimible.

Siéntete libre de experimentar con diferentes colores, ángulos o incluso rellenos degradados. La API es lo suficientemente flexible como para que puedas crear documentos de aspecto profesional sin abrir Word manualmente.

---

¡Feliz codificación! Si encuentras algún inconveniente, deja un comentario abajo o visita los foros de Aspose.Words – la comunidad responde rápido.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}