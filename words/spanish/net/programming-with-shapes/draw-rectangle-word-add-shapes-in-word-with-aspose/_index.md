---
category: general
date: 2026-07-29
description: Dibujar un rectángulo en Word usando Aspose.Words. Aprende cómo agregar
  una forma de rectángulo, agregar una forma de línea y gestionar múltiples formas
  en un solo documento.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- draw rectangle word
- add rectangle shape
- add line shape
- how to add shapes
- multiple shapes word
language: es
lastmod: 2026-07-29
og_description: Dibuja un rectángulo en Word con Aspose.Words. Sigue esta guía paso
  a paso para agregar una forma de rectángulo, agregar una forma de línea y trabajar
  sin esfuerzo con múltiples formas en Word.
og_image_alt: Screenshot showing a Word document with a grouped rectangle and line
  shape – draw rectangle word example
og_title: Dibujar rectángulo en Word – Domina la adición de formas en Word
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: draw rectangle word using Aspose.Words. Learn how to add rectangle
    shape, add line shape, and manage multiple shapes word in a single document.
  headline: draw rectangle word – Add Shapes in Word with Aspose
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word Automation
title: Dibujar rectángulo en Word – Añadir formas en Word con Aspose
url: /es/net/programming-with-shapes/draw-rectangle-word-add-shapes-in-word-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# draw rectangle word – Guía completa para agregar formas en Word

¿Alguna vez te has preguntado cómo **draw rectangle word** documentos sin abrir la interfaz cada vez? No estás solo. Muchos desarrolladores necesitan generar archivos Word al vuelo, y la forma más fácil es dejar que una biblioteca haga el trabajo pesado. En este tutorial te mostraremos exactamente **cómo agregar formas** —específicamente un rectángulo y una línea— usando Aspose.Words para .NET, y mantendremos el foco en la frase *draw rectangle word* para que nunca te pierdas.

Piénsalo como un mini‑estudio de arte que vive dentro de tu código. Al final podrás **add rectangle shape**, **add line shape**, e incluso combinarlos en grupos **multiple shapes word**. Sin UI, sin manipulaciones manuales, solo C# limpio y repetible.

## Lo que aprenderás

- Configurar un nuevo documento Word con Aspose.Words.  
- Crear un **GroupShape** que pueda contener varios objetos.  
- **Add rectangle shape** y **add line shape** dentro de ese grupo.  
- Insertar las formas agrupadas en el cuerpo del documento.  
- Guardar el archivo y ver el resultado al instante.  

Si te sientes cómodo con C# básico y tienes una copia de Aspose.Words, estás listo. No se requieren paquetes NuGet adicionales más allá de la biblioteca principal.

> **Consejo profesional:** Aspose.Words funciona con .NET 6, .NET 7 y .NET Framework 4.6+. Elige el runtime que coincida con tu proyecto.

![draw rectangle word example](https://example.com/placeholder-image.png "draw rectangle word – grouped shapes in a Word file")

## draw rectangle word – Configuración del documento

Antes de que podamos **draw rectangle word** necesitamos un lienzo limpio. La clase `Document` es ese lienzo; el `DocumentBuilder` es nuestra brocha.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty Word document.
Document doc = new Document();

// DocumentBuilder lets us insert nodes, paragraphs, tables, etc.
DocumentBuilder builder = new DocumentBuilder(doc);
```

Las dos líneas anteriores nos dan un `.docx` nuevo, en memoria. No se escribe nada en disco todavía, lo que significa que podemos experimentar sin ensuciar el sistema de archivos.

## Cómo agregar formas – Creando un contenedor GroupShape

Cuando deseas que **multiple shapes word** se comporte como una sola unidad—moverse juntas, rotarse juntas—las envuelves en un `GroupShape`. Piensa en un grupo como una carpeta que contiene otras formas.

```csharp
// Define a GroupShape that will act as a container for other shapes.
// Width = 300 pts, Height = 200 pts (roughly 4.2" x 2.8").
GroupShape group = new GroupShape(doc, 300, 200)
{
    Left = 100,   // Position from the left margin.
    Top  = 100    // Position from the top margin.
};
```

¿Por qué un grupo? Porque más adelante podrías querer **add rectangle shape** y **add line shape** y luego moverlas juntas. Sin un grupo, tendrías que reposicionar cada forma individualmente.

## add rectangle shape – Insertando un rectángulo dentro del grupo

Ahora que el contenedor existe, vamos a **add rectangle shape**. Un rectángulo es un `Shape` cuyo `ShapeType` es `Rectangle`.

```csharp
// Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width  = 120,   // 120 points ≈ 1.67 inches.
    Height = 80,    // 80 points ≈ 1.11 inches.
    Left   = 10,    // Offset inside the group.
    Top    = 10
};

// Append the rectangle to the group.
group.AppendChild(rectangle);
```

Observa que los valores `Left` y `Top` son relativos al origen del grupo, no a la página. Esto facilita alinear las formas con precisión. El rectángulo aparecerá cerca de la esquina superior‑izquierda del grupo.

## add line shape – Agregando una línea al mismo grupo

Una línea es simplemente otro `Shape`, pero su `ShapeType` es `Line`. La posicionaremos debajo del rectángulo.

```csharp
// Create a line shape.
Shape line = new Shape(doc, ShapeType.Line)
{
    Width  = 150,   // Length of the line.
    Height = 0,     // Height is zero for a straight line.
    Left   = 10,
    Top    = 110    // Position it a bit lower than the rectangle.
};

// Append the line to the group.
group.AppendChild(line);
```

Debido a que la altura de la línea es cero, la propiedad `Top` determina dónde se sitúa verticalmente. La `Width` controla cuán larga se extiende horizontalmente.

## multiple shapes word – Insertando el grupo en el cuerpo del documento

Tenemos un grupo que ahora contiene **add rectangle shape** y **add line shape**. El paso final es colocar todo en el documento.

```csharp
// Insert the completed group into the document body at the current cursor position.
builder.InsertNode(group);
```

`InsertNode` coloca el grupo exactamente donde el `DocumentBuilder` está posicionado actualmente. Si lo necesitas en un párrafo específico, mueve el builder con `builder.MoveToParagraph(index)` primero.

## Guardando el resultado – Viendo la salida de draw rectangle word

```csharp
// Save the document to disk. Change the path to a location that exists on your machine.
doc.Save("C:/Temp/GroupShape.docx");
```

Abre el archivo generado en Microsoft Word y verás un único grupo que contiene un rectángulo y una línea. Puedes hacer clic en el grupo, arrastrarlo o incluso cambiar su tamaño—todas las formas se mueven juntas. Ese es el poder de **multiple shapes word**.

### Resultado esperado

- Un archivo `.docx` llamado `GroupShape.docx`.  
- Una página con un rectángulo agrupado (120 × 80 pt) cerca de la esquina superior‑izquierda.  
- Una línea horizontal (150 pt de largo) posicionada justo debajo del rectángulo.  
- Ambas formas son seleccionables como un solo objeto.

Si haces doble clic en el grupo, Word te permitirá editar cada forma individualmente—perfecto para ajustes finos.

## Preguntas frecuentes y casos límite

**¿Qué pasa si necesito más de dos formas?**  
Simplemente sigue llamando a `group.AppendChild(yourShape)` para cada objeto adicional. El grupo puede contener cualquier número de formas, lo que lo hace ideal para diagramas complejos.

**¿Puedo cambiar el color de relleno del rectángulo?**  
Claro. Después de crear el rectángulo, establece `rectangle.FillColor = System.Drawing.Color.LightBlue;`. Esto funciona para cualquier forma que admita relleno.

**¿Debo establecer `Height = 0` para una línea?**  
Sí, para una línea horizontal recta la altura debe ser cero. Para una línea vertical, establece `Width = 0` y asigna a `Height` un valor positivo.

**¿Funcionará esto con archivos .doc (Word 97‑2003)?**  
Aspose.Words puede guardar en el formato `.doc` más antiguo, pero algunas funciones modernas de formas pueden estar limitadas. Usa `.docx` para obtener la máxima fidelidad.

**¿Cómo rotar todo el grupo?**  
Puedes establecer `group.Rotation = 45;` (grados) antes de insertarlo. La rotación se aplica a cada forma hija.

## Resumen – Cómo agregar formas en Word programáticamente

- **draw rectangle word** comienza creando un `Document` y `DocumentBuilder`.  
- Construye un **GroupShape** para contener **multiple shapes word**.  
- **add rectangle shape** y **add line shape** se añaden al grupo.  
- Inserta el grupo en el cuerpo con `builder.InsertNode`.  
- Guarda el archivo y ábrelo para verificar el resultado visual.

Ese es todo el flujo de trabajo, envuelto en una única lista de código fácil de leer.

## Próximos pasos y temas relacionados

Ahora que sabes **how to add shapes**, considera explorar:

- **add rectangle shape** con esquinas redondeadas (`ShapeType.Rectangle` + `CornerRadius`).  
- Estilizar líneas con diferentes patrones de guiones (`line.LineFormat.DashStyle`).  
- Incrustar imágenes junto a las formas para informes más ricos.  
- Usar **multiple shapes word** para crear diagramas de flujo o diagramas UML simples.  

---

¡Feliz codificación! Si encuentras algún problema o tienes un caso de uso interesante para compartir, deja un comentario abajo. Tu feedback nos ayuda a todos a dominar el arte de **draw rectangle word** y más allá.

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Crear forma de rectángulo en Word usando C# – Guía paso a paso](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Crear forma de rectángulo en Word con Aspose.Words – Guía paso a paso](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Insertar formas en documentos Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/insert-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}