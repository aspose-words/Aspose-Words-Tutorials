---
category: general
date: 2026-06-20
description: Agrega sombra a la forma rápidamente y aprende cómo cambiar la transparencia
  de la sombra, añadir sombra a la forma y aplicar sombra difusa usando Aspose.Words
  para .NET.
draft: false
keywords:
- add shadow to shape
- how to change shadow transparency
- how to add shape shadow
- how to apply blur shadow
language: es
og_description: Añade sombra a una forma en un archivo de Word, descubre cómo cambiar
  la transparencia de la sombra, agrega sombra a la forma y aplica una sombra difusa
  con ejemplos de código claros.
og_title: Añadir sombra a la forma – Tutorial paso a paso de C#
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: Add shadow to shape quickly and learn how to change shadow transparency,
    add shape shadow, and apply blur shadow using Aspose.Words for .NET.
  headline: Add Shadow to Shape in Word Documents – Complete C# Guide
  type: TechArticle
- description: Add shadow to shape quickly and learn how to change shadow transparency,
    add shape shadow, and apply blur shadow using Aspose.Words for .NET.
  name: Add Shadow to Shape in Word Documents – Complete C# Guide
  steps:
  - name: What if the shape has no existing shadow object?
    text: Aspose.Words automatically creates a `Shadow` object when you first access
      `targetShape.Shadow`. No extra initialization is required.
  - name: Does this work with other shape types, like circles or pictures?
    text: Absolutely. The shadow API is shape‑agnostic. Just retrieve the appropriate
      `Shape` node, and the same properties apply.
  - name: How to make the shadow invisible again?
    text: Set `targetShape.Shadow.Visible = false;` or simply omit the shadow configuration.
  - name: Compatibility with older .NET versions?
    text: The code uses only features available in Aspose.Words 23.x and .NET Standard
      2.0+, so it runs on .NET Framework 4.6.1 and newer.
  type: HowTo
tags:
- Aspose.Words
- C#
- Document Automation
- Shapes
title: Agregar sombra a una forma en documentos de Word – Guía completa de C#
url: /es/net/programming-with-shapes/add-shadow-to-shape-in-word-documents-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Agregar sombra a una forma en documentos Word – Guía completa en C#

¿Alguna vez te has preguntado cómo **agregar sombra a una forma** en un archivo Word sin tener que manipular la interfaz? No estás solo. Muchos desarrolladores necesitan mejorar estéticamente los documentos de forma programática, y la buena noticia es que Aspose.Words lo hace muy sencillo.

En este tutorial recorreremos paso a paso **cómo agregar sombra a una forma**, te mostraremos **cómo cambiar la transparencia de la sombra**, cubriremos **cómo agregar sombra a una forma** en varios escenarios, e incluso explicaremos **cómo aplicar sombra difusa** para lograr ese efecto profesional de profundidad. Al final tendrás un fragmento reutilizable que podrás insertar en cualquier proyecto .NET.

## Lo que aprenderás

- Cargar un DOCX, localizar una forma y configurar sus propiedades de sombra.
- Ajustar la opacidad de la sombra con `Transparency`.
- Aplicar desenfoque y desplazamiento para crear una sombra realista.
- Guardar el documento modificado y verificar el resultado.
- Consejos para manejar múltiples formas, diferentes tipos de forma y casos especiales.

> **Requisitos previos:** .NET 6 o superior, Aspose.Words para .NET (paquete NuGet `Aspose.Words`) y conocimientos básicos de C#. No se requieren herramientas UI.

![add shadow to shape example](image.png){ alt="ejemplo de agregar sombra a forma" }

## Paso 1: Configura tu proyecto y carga el documento

Antes de poder **agregar sombra a una forma**, necesitas un objeto documento con el que trabajar. Este paso es sencillo pero esencial: sin cargar el archivo, no hay nada que modificar.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Load an existing DOCX that already contains a shape (e.g., a rectangle)
Document document = new Document(@"C:\Docs\input.docx");
```

*Por qué es importante:*  
`Document` es el punto de entrada para todas las operaciones de Aspose.Words. Al cargar el archivo al principio, garantizas que cualquier manipulación posterior de la forma se realice sobre el árbol de nodos correcto.

## Paso 2: Recupera la forma objetivo

Ahora que el documento está en memoria, debemos localizar la forma que queremos realzar. Si tienes varias formas, puedes ajustar el índice o usar un selector más sofisticado.

```csharp
// Grab the first shape in the document – change the index if needed
Shape targetShape = (Shape)document.GetChild(NodeType.Shape, 0, true);
```

> **Consejo:** Usa `document.GetChild(NodeType.Shape, index, true)` para buscar de forma recursiva. Si necesitas una forma específica por nombre, revisa `targetShape.Name`.

## Paso 3: Habilita la sombra y establece su color básico

Una sombra no aparecerá a menos que sea visible y tenga un color. Le daremos un gris oscuro sutil que funciona bien sobre fondos claros.

```csharp
// Make sure the shadow is turned on
targetShape.Shadow.Visible = true;

// Choose a neutral color for the shadow
targetShape.Shadow.Color = Color.DarkGray;
```

*Explicación:*  
Establecer `Visible` a `true` activa el efecto, mientras que `Color.DarkGray` proporciona un tono neutro que no choca con la mayoría de los temas del documento.

## Paso 4: Cómo cambiar la transparencia de la sombra

La transparencia es la clave para que una sombra se sienta natural. Un valor de `0` es totalmente opaco; `1` es completamente invisible. Aquí tienes **cómo cambiar la transparencia de la sombra** al 30 %:

```csharp
// 30 % transparent (0.3 means 30 % see‑through)
targetShape.Shadow.Transparency = 0.3;
```

*¿Por qué 0.3?*  
Una sombra con un 30 % de transparencia imita la iluminación del mundo real sin abrumar los bordes de la forma. Puedes experimentar: `0.5` produce un aspecto más suave, mientras que `0.1` hace la sombra más pronunciada.

## Paso 5: Cómo aplicar sombra difusa para profundidad

Una sombra nítida y de bordes duros se ve plana. Añadir desenfoque le da profundidad. Aquí respondemos **cómo aplicar sombra difusa** en código.

```csharp
// Define the blur radius (in points). Larger values = softer shadow.
targetShape.Shadow.BlurRadius = 5;   // 5 pt blur

// Offset determines where the shadow falls relative to the shape.
targetShape.Shadow.OffsetX = 3;      // 3 pt to the right
targetShape.Shadow.OffsetY = 3;      // 3 pt downwards
```

*¿Qué está sucediendo?*  
`BlurRadius` suaviza los bordes, mientras que `OffsetX/Y` posicionan la sombra como si una fuente de luz estuviera arriba‑a la izquierda. Ajusta estos valores para que coincidan con tu lenguaje de diseño.

## Paso 6: Cómo agregar sombra a varias formas (Opcional)

Si tu documento contiene varias formas, probablemente querrás **agregar sombra a la forma** en cada una de ellas. Un bucle rápido hace el trabajo:

```csharp
// Iterate over every shape in the document
foreach (Shape shape in document.GetChildNodes(NodeType.Shape, true))
{
    shape.Shadow.Visible = true;
    shape.Shadow.Color = Color.DarkGray;
    shape.Shadow.Transparency = 0.3;
    shape.Shadow.BlurRadius = 5;
    shape.Shadow.OffsetX = 3;
    shape.Shadow.OffsetY = 3;
}
```

*Consejo profesional:*  
Si solo deseas afectar a los rectángulos, verifica `shape.ShapeType == ShapeType.Rectangle` dentro del bucle.

## Paso 7: Guarda el documento modificado

Todo el trabajo pesado está hecho—ahora persiste los cambios. Puedes sobrescribir el archivo original o escribir en una nueva ubicación.

```csharp
// Save to a new file to keep the original untouched
document.Save(@"C:\Docs\output.docx");
```

Al abrir `output.docx` en Word, verás el rectángulo (o cualquier forma que hayas seleccionado) con una sombra sutil, semitransparente y difusa.

## Preguntas frecuentes y casos especiales

### ¿Qué pasa si la forma no tiene un objeto de sombra existente?
Aspose.Words crea automáticamente un objeto `Shadow` cuando accedes por primera vez a `targetShape.Shadow`. No se requiere inicialización adicional.

### ¿Funciona con otros tipos de forma, como círculos o imágenes?
Absolutamente. La API de sombra es independiente del tipo de forma. Simplemente recupera el nodo `Shape` correspondiente y las mismas propiedades se aplican.

### ¿Cómo volver a hacer invisible la sombra?
Establece `targetShape.Shadow.Visible = false;` o simplemente omite la configuración de la sombra.

### ¿Compatibilidad con versiones anteriores de .NET?
El código usa solo características disponibles en Aspose.Words 23.x y .NET Standard 2.0+, por lo que funciona en .NET Framework 4.6.1 y versiones posteriores.

## Ejemplo completo y funcional

A continuación tienes el programa completo, listo para ejecutar, que reúne todo:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // Load the document that contains the shape
        Document doc = new Document(@"C:\Docs\input.docx");

        // Retrieve the first shape (e.g., a rectangle) from the document
        Shape rect = (Shape)doc.GetChild(NodeType.Shape, 0, true);

        // Enable shadow and set its basic properties
        rect.Shadow.Visible = true;
        rect.Shadow.Color = Color.DarkGray;

        // How to change shadow transparency – 30 % transparent
        rect.Shadow.Transparency = 0.3;

        // How to apply blur shadow – add depth with blur and offset
        rect.Shadow.BlurRadius = 5;   // 5 pt blur radius
        rect.Shadow.OffsetX = 3;      // horizontal offset
        rect.Shadow.OffsetY = 3;      // vertical offset

        // Save the modified document
        doc.Save(@"C:\Docs\output.docx");
    }
}
```

**Salida esperada:** Abre `output.docx` y verás el rectángulo original ahora renderizado con una sombra gris oscura, 30 % transparente, difusa y ligeramente desplazada hacia la esquina inferior‑derecha.

## Conclusión

Hemos cubierto todo lo que necesitas para **agregar sombra a una forma** de forma programática, desde cargar el archivo hasta ajustar la transparencia y el desenfoque. Ahora sabes **cómo cambiar la transparencia de la sombra**, **cómo agregar sombra a la forma** en varios elementos y **cómo aplicar sombra difusa** para lograr un aspecto pulido.

¿Listo para el siguiente paso? Prueba experimentando con:

- Diferentes colores de sombra (`Color.Black`, `Color.FromArgb(128, 0, 0, 0)`) para efectos más oscuros.
- Desplazamientos dinámicos basados en el tamaño de la forma para mantener la proporción.
- Combinar sombras con degradados o reflejos para un estilo avanzado.

¡Deja un comentario si encuentras algún problema y feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Tutorial de sombra de forma en Aspose.Words – Agregar una sombra a una forma de Word en C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Crear documento Word en Java – Agregar forma rectangular con efecto de sombra](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Agregar forma de grupo](/words/english/net/programming-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}