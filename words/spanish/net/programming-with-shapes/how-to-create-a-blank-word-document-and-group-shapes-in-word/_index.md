---
category: general
date: 2026-10-20
description: Aprende a crear un documento de Word en blanco, agrupar formas en Word,
  establecer el color de relleno de una forma y usar el tipo de ajuste en línea con
  un ejemplo completo en C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- how to group shapes
- set shape fill color
- wrap type inline
language: es
lastmod: 2026-10-20
og_description: Crea un documento Word en blanco, agrupa formas en Word y establece
  el color de relleno de la forma con tipo de ajuste en línea usando Aspose.Words
  y C#. Sigue el tutorial completo.
og_image_alt: Screenshot of a blank Word document containing a grouped rectangle and
  text box created with Aspose.Words
og_title: Crea un documento Word en blanco y agrupa formas en Word – guía paso a paso
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Learn how to create a blank Word document, group shapes in Word, set
    shape fill color, and use wrap type inline with a complete C# example.
  headline: How to create a blank Word document and group shapes in Word using Aspose.Words
  type: TechArticle
- description: Learn how to create a blank Word document, group shapes in Word, set
    shape fill color, and use wrap type inline with a complete C# example.
  name: How to create a blank Word document and group shapes in Word using Aspose.Words
  steps:
  - name: Expected result
    text: '* A .docx file containing a single paragraph. * Inside the paragraph, an
      inline group that looks like a single composite object. * The rectangle is filled
      with light blue, and the text box displays “Grouped text”.'
  - name: What if I need the group to float rather than be inline?
    text: Replace `WrapType.Inline` with `WrapType.TopBottom` (or any other `WrapType`
      enum value). Floating groups can be positioned independently of paragraph flow,
      but they lose the automatic inline alignment.
  - name: Can I add more shapes, such as circles or images?
    text: Yes. Create additional `Shape` objects with `ShapeType.Ellipse` or `ShapeType.Image`,
      configure their properties, and call `group.AppendChild(newShape)`. The group
      will automatically expand to accommodate the new bounds if you update `group.Bounds`
      accordingly.
  - name: How do I change the group’s overall size after adding children?
    text: Adjust `group.Bounds` after all children are appended, or compute the union
      of child bounds programmatically. This ensures the group’s hit‑test area matches
      the visual content.
  - name: What if the output folder does not exist?
    text: 'Aspose.Words throws a `DirectoryNotFoundException`. Create the directory
      first:'
  - name: Does this work with .NET Framework instead of .NET Core?
    text: All APIs used (`Document`, `DocumentBuilder`, `GroupShape`, `Shape`) are
      available in the .NET Framework version of Aspose.Words, so the same code works
      unchanged.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Cómo crear un documento Word en blanco y agrupar formas en Word usando Aspose.Words
url: /es/net/programming-with-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo crear un documento Word en blanco y agrupar formas en Word

Si necesitas **crear un documento Word en blanco** que contenga varias formas actuando como una sola unidad, esta guía te muestra exactamente cómo hacerlo. Verás cómo **agrupar formas en Word**, establecer el color de relleno de una forma y aplicar **wrap type inline**, todo con un programa conciso y ejecutable en C#.

El tutorial te lleva paso a paso por cada línea de código, explica por qué cada paso es importante y destaca los errores comunes. Al final tendrás un archivo .docx que muestra un rectángulo y un cuadro de texto agrupados, listo para más automatización.

## Lo que aprenderás

* Cómo inicializar un archivo Word vacío con Aspose.Words.  
* La forma correcta de crear un **GroupShape** y añadir formas hijas.  
* Técnicas para **set shape fill color** y controlar la posición.  
* Uso de **wrap type inline** para que el grupo se comporte como un único objeto en línea.  
* Cómo guardar y verificar el resultado.

No se requiere experiencia previa con Aspose.Words, pero deberías estar cómodo con la sintaxis básica de C# y tener Visual Studio (u otro IDE) instalado.

## Requisitos previos

| Requisito | Motivo |
|-------------|--------|
| .NET 6.0 o posterior | Proporciona el runtime para el proyecto C#. |
| Aspose.Words for .NET (última versión) | Suministra las clases `Document`, `DocumentBuilder` y de formas usadas en el ejemplo. |
| Una ruta de carpeta con permisos de escritura | La llamada `doc.Save` necesita un directorio válido para escribir el archivo de salida. |
| Conocimientos básicos de C# | Te permite seguir el código y modificarlo para tus propios escenarios. |

Instala Aspose.Words vía NuGet:

```bash
dotnet add package Aspose.Words
```

---

## Paso 1: Crear un documento Word en blanco

La primera operación es **crear un documento Word en blanco**. La clase `Document` de Aspose.Words representa un archivo Word en memoria, y `DocumentBuilder` ofrece una API cómoda para editarlo.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Initialize a new empty document.
Document doc = new Document();

// Attach a builder to the document for easy content insertion.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Por qué es importante*: Comenzar con un documento limpio garantiza que la forma grupal que añadas será el único contenido, facilitando la verificación.

## Paso 2: Definir un GroupShape con wrap type inline

Un **GroupShape** actúa como contenedor de otras formas. Establecer su `WrapType` a `Inline` asegura que el grupo se comporte como un único objeto en línea dentro del flujo del párrafo.

```csharp
// Create a group shape that will hold the rectangle and text box.
GroupShape group = new GroupShape(doc, WrapType.Inline);

// Define the bounding rectangle of the group (x, y, width, height).
group.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
```

*Por qué es importante*: Usar **wrap type inline** evita que el grupo flote fuera del texto circundante, lo cual es esencial cuando deseas que el grupo se mueva como una unidad.

## Paso 3: Añadir un rectángulo y establecer el color de relleno de la forma

Un rectángulo es un elemento visual común. El constructor `Shape` recibe un `ShapeType`; luego especificamos dimensiones y color de relleno.

```csharp
// Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width = 150,
    Height = 100,
    FillColor = System.Drawing.Color.LightBlue
};

// Append the rectangle to the group.
group.AppendChild(rectangle);
```

*Por qué es importante*: La propiedad `FillColor` demuestra **set shape fill color** en la práctica, dando al rectángulo un fondo azul claro que destaca en el documento final.

## Paso 4: Añadir un cuadro de texto – cómo agrupar formas eficazmente

Un cuadro de texto proporciona texto editable dentro del grupo. Posiciónalo relativo al sistema de coordenadas del grupo ajustando la propiedad `Top`.

```csharp
// Create a text box shape.
Shape textBox = new Shape(doc, ShapeType.TextBox)
{
    Width = 120,
    Height = 60,
    TextBoxText = "Grouped text",
    Top = 110 // Position below the rectangle inside the group.
};

// Append the text box to the group.
group.AppendChild(textBox);
```

*Por qué es importante*: Este paso responde a **how to group shapes** — añadiendo cada forma hija a la misma instancia de `GroupShape`. El desplazamiento `Top` asegura que el cuadro de texto aparezca debajo del rectángulo, demostrando un control preciso del diseño.

## Paso 5: Insertar el GroupShape completado en el documento

Ahora que el grupo contiene ambas formas hijas, insértalo en la posición actual del builder.

```csharp
// Insert the group shape at the builder’s cursor location.
builder.InsertNode(group);
```

*Por qué es importante*: Insertar el grupo como un solo nodo garantiza que Word trate al rectángulo y al cuadro de texto como un objeto lógico único, preservando sus posiciones relativas durante la edición.

## Paso 6: Guardar el documento y verificar la salida

Finalmente, escribe el documento en disco. Reemplaza `YOUR_DIRECTORY` con una ruta real en tu máquina.

```csharp
// Save the document to the specified folder.
doc.Save("YOUR_DIRECTORY/GroupShape.docx");
```

Al abrir `GroupShape.docx` en Microsoft Word, deberías ver un rectángulo azul claro con un cuadro de texto etiquetado “Grouped text” posicionado directamente debajo. Seleccionar cualquiera de las formas seleccionará todo el grupo, confirmando que **group shapes in Word** funciona como se espera.

### Resultado esperado

* Un archivo .docx que contiene un solo párrafo.  
* Dentro del párrafo, un grupo en línea que parece un único objeto compuesto.  
* El rectángulo está relleno de azul claro, y el cuadro de texto muestra “Grouped text”.

![Screenshot of the generated Word document](grouped_shapes.png){.center width=600 alt="Screenshot of a blank Word document with grouped rectangle and text box created using Aspose.Words"}

## Preguntas frecuentes y manejo de casos límite

### ¿Qué pasa si necesito que el grupo flote en lugar de estar en línea?

Reemplaza `WrapType.Inline` por `WrapType.TopBottom` (u otro valor del enum `WrapType`). Los grupos flotantes pueden posicionarse independientemente del flujo del párrafo, pero pierden la alineación automática en línea.

### ¿Puedo añadir más formas, como círculos o imágenes?

Sí. Crea objetos `Shape` adicionales con `ShapeType.Ellipse` o `ShapeType.Image`, configura sus propiedades y llama a `group.AppendChild(newShape)`. El grupo se expandirá automáticamente para acomodar los nuevos límites si actualizas `group.Bounds` en consecuencia.

### ¿Cómo cambio el tamaño total del grupo después de añadir hijos?

Ajusta `group.Bounds` después de haber añadido todos los hijos, o calcula la unión de los límites de los hijos programáticamente. Esto asegura que el área de detección del grupo coincida con el contenido visual.

### ¿Qué ocurre si la carpeta de salida no existe?

Aspose.Words lanza una `DirectoryNotFoundException`. Crea la carpeta primero:

```csharp
string outputPath = "YOUR_DIRECTORY";
Directory.CreateDirectory(outputPath);
doc.Save(Path.Combine(outputPath, "GroupShape.docx"));
```

### ¿Esto funciona con .NET Framework en lugar de .NET Core?

Todas las API usadas (`Document`, `DocumentBuilder`, `GroupShape`, `Shape`) están disponibles en la versión de Aspose.Words para .NET Framework, por lo que el mismo código funciona sin cambios.

## Consejos profesionales

* **Consejo de rendimiento** – Reutiliza una única instancia de `DocumentBuilder` cuando insertes muchos grupos; crear un nuevo builder por grupo añade sobrecarga.  
* **Consistencia visual** – Establece `rectangle.StrokeColor` para que coincida con `FillColor` y lograr un aspecto uniforme, o pon `rectangle.LineWidth = 0` para ocultar el borde.  
* **Depuración** – Llama a `doc.UpdatePageLayout()` antes de guardar si modificas muchas formas; esto fuerza a Word a recalcular el diseño y puede evitar recortes inesperados.

## Conclusión

Ahora sabes cómo **crear un documento Word en blanco**, **agrupar formas en Word**, **set shape fill color** y aplicar **wrap type inline** usando Aspose.Words para .NET. El ejemplo completo muestra el enfoque estándar para construir gráficos compuestos que se comportan como un solo objeto en Word.

A partir de aquí puedes explorar:

* Añadir formas adicionales como imágenes o gráficos.  
* Experimentar con diferentes valores de `WrapType` para grupos flotantes.  
* Automatizar la generación por lotes de diagramas agrupados en múltiples documentos.

¡Siéntete libre de adaptar el código a tus propios escenarios de automatización y comparte tus resultados en los comentarios!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [How to Save PDF from Word with Inline Shapes – Complete Guide](/words/english/java/document-conversion-and-export/how-to-save-pdf-from-word-with-inline-shapes-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}