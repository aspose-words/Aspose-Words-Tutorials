---
category: general
date: 2026-09-11
description: Aprende cómo crear un documento Word, agregar una forma rectangular y
  establecer las dimensiones de la forma con Aspose.Words. Guía paso a paso en C#
  para un dimensionado preciso de la forma.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- add rectangle shape
- set shape size
- create shapes in word
- set shape dimensions
language: es
lastmod: 2026-09-11
og_description: Crear documento Word con Aspose.Words en C#. Esta guía muestra cómo
  agregar una forma rectangular, establecer el tamaño de la forma y gestionar las
  dimensiones de la forma programáticamente.
og_image_alt: Screenshot of a rectangle shape inside a grouped shape in a newly created
  Word document
og_title: Crear documento Word con formas – tutorial de Aspose.Words C#
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create word document, add rectangle shape, and set shape
    dimensions with Aspose.Words. Step‑by‑step C# guide for precise shape sizing.
  headline: How to create word document with shapes using Aspose.Words in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Cómo crear un documento Word con formas usando Aspose.Words en C#
url: /es/net/programming-with-shapes/how-to-create-word-document-with-shapes-using-aspose-words-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo crear un documento Word con formas usando Aspose.Words en C#

Si necesitas **crear un documento Word** que contenga gráficos personalizados, puedes hacerlo completamente con código. Este tutorial te guía paso a paso para crear un archivo Word, añadir una forma rectangular y controlar cada dimensión de la forma. Al final tendrás un fragmento reutilizable que podrás insertar en cualquier proyecto .NET.

Aprenderás a **añadir una forma rectangular**, **establecer el tamaño de la forma** y **definir las dimensiones de la forma** dentro de un contenedor agrupado. El ejemplo usa Aspose.Words 13.9, pero los conceptos se aplican a versiones posteriores también. No se requiere experiencia previa con la API de dibujo de Aspose, solo conocimientos básicos de C#.

## Requisitos previos

- .NET 6.0 o posterior instalado  
- Paquete NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)  
- Un IDE como Visual Studio 2022 (cualquier editor que soporte C# funciona)  

Tener estas herramientas listas te permite ejecutar el código inmediatamente sin configuración adicional.

## Paso 1: Inicializar el documento y el builder – conceptos básicos para crear un documento Word

La primera operación es instanciar un objeto `Document` y un `DocumentBuilder`. El `Document` representa el archivo en sí, mientras que el `DocumentBuilder` proporciona una API fluida para insertar contenido.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // Create a new, empty Word document
        Document doc = new Document();

        // DocumentBuilder gives us a cursor to insert nodes
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Por qué es importante:**  
Crear el documento al inicio te brinda un lienzo limpio. El cursor del builder comienza en el primer párrafo, que es donde más adelante **crearemos formas en Word**.

## Paso 2: Construir un GroupShape para contener varios gráficos

Un `GroupShape` actúa como un contenedor; puedes mover, rotar o cambiar el tamaño de todo el grupo como una sola unidad. Aquí definimos el ancho y alto del contenedor en puntos (1 pt ≈ 1/72 in).

```csharp
        // Define a group that is 300 pt wide and 200 pt high
        GroupShape group = new GroupShape(doc, 300, 200);

        // Position the group 50 pt from the left and top margins
        group.Left = 50;
        group.Top  = 50;
```

**Por qué es importante:**  
Agrupar formas simplifica la gestión del diseño. Si más adelante necesitas añadir más formas (p. ej., círculos o cuadros de texto), heredarán la posición y escala del grupo.

## Paso 3: Crear una forma rectangular y configurar sus dimensiones

Ahora añadimos el rectángulo real. El constructor `Shape` requiere la referencia al documento y el tipo de forma. Después de crearla, establecemos explícitamente **el tamaño de la forma** y **las dimensiones de la forma**.

```csharp
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);

        // Set the rectangle’s width to 100 pt and height to 50 pt
        rectangle.Width  = 100;   // set shape width
        rectangle.Height = 50;    // set shape height

        // Position the rectangle 10 pt from the group’s left/top edges
        rectangle.Left = 10;
        rectangle.Top  = 10;
```

**Por qué es importante:**  
Especificar ancho, alto, izquierda y arriba te brinda un control pixel‑perfecto sobre la forma. Esto es esencial cuando el documento debe coincidir con una especificación de diseño o un formulario impreso.

## Paso 4: Ensamblar el grupo añadiendo el rectángulo

Añadir el rectángulo al `GroupShape` lo convierte en un nodo hijo. Puedes agregar tantos hijos como necesites antes de insertar el grupo en el documento.

```csharp
        // Add the rectangle to the group
        group.AppendChild(rectangle);
```

**Consejo:** Si planeas añadir una segunda forma, créala de la misma manera y llama a `group.AppendChild(secondShape)`. Todos los hijos comparten el sistema de coordenadas del grupo.

## Paso 5: Insertar la forma agrupada en el documento y guardar

Con el grupo completamente construido, lo colocamos en el párrafo actual. La propiedad `CurrentParagraph` del builder brinda acceso directo al árbol de nodos subyacente.

```csharp
        // Insert the group into the first paragraph of the document
        builder.CurrentParagraph.AppendChild(group);

        // Save the document to disk (adjust the path as needed)
        doc.Save("GroupShape.docx");

        // Optional: open the file automatically (Windows only)
        System.Diagnostics.Process.Start(new System.Diagnostics.ProcessStartInfo
        {
            FileName = "GroupShape.docx",
            UseShellExecute = true
        });
    }
}
```

**Por qué es importante:**  
Añadir el grupo a un párrafo asegura que la forma aparezca en línea con el flujo de texto. Guardar el documento finaliza la operación de **crear documento Word**.

## Variaciones comunes y casos límite

| Escenario | Ajuste |
|----------|------------|
| **Orientación de página diferente** | Establece `doc.FirstSection.PageSetup.Orientation = Orientation.Landscape;` antes de crear el grupo. |
| **Múltiples rectángulos** | Crea objetos `Shape` adicionales y llama a `group.AppendChild(newRect)` para cada uno. |
| **Tamaño dinámico basado en el contenido** | Calcula ancho/alto a partir de las dimensiones de la imagen o métricas de texto, luego asigna a `rectangle.Width` / `rectangle.Height`. |
| **Exportar a PDF** | Después de `doc.Save`, llama a `doc.Save("GroupShape.pdf", SaveFormat.Pdf);`. |
| **Compatibilidad con versiones antiguas de Word** | Guarda usando `SaveFormat.Doc` en lugar de `Docx` para compatibilidad con Word 97‑2003. |

Estas variaciones ilustran cómo la misma lógica central puede adaptarse a muchos requisitos del mundo real.

## Ejemplo completo y ejecutable

A continuación se muestra el programa completo que puedes copiar, pegar y ejecutar. Incluye todas las directivas `using`, un punto de entrada `Main` y comentarios que explican cada línea.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // 1️⃣ Create a new document and a builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Define a group shape (300 pt × 200 pt) positioned at (50, 50)
        GroupShape group = new GroupShape(doc, 300, 200);
        group.Left = 50;
        group.Top  = 50;

        // 3️⃣ Create a rectangle (100 pt × 50 pt) positioned at (10, 10) inside the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width  = 100;   // set shape width
        rectangle.Height = 50;    // set shape height
        rectangle.Left = 10;
        rectangle.Top  = 10;

        // 4️⃣ Add the rectangle to the group
        group.AppendChild(rectangle);

        // 5️⃣ Insert the group into the first paragraph and save the file
        builder.CurrentParagraph.AppendChild(group);
        doc.Save("GroupShape.docx");

        // Open the resulting file automatically (optional)
        System.Diagnostics.Process.Start(new System.Diagnostics.ProcessStartInfo
        {
            FileName = "GroupShape.docx",
            UseShellExecute = true
        });
    }
}
```

**Salida esperada:**  
Al abrir *GroupShape.docx*, la primera página muestra un rectángulo con borde gris posicionado a 50 pt del margen izquierdo/superior, con el propio rectángulo desplazado 10 pt dentro del grupo. Las dimensiones coinciden con los valores establecidos en el código.

## Conclusión

Ahora sabes cómo **crear un documento Word**, **añadir una forma rectangular** y establecer con precisión **el tamaño de la forma** y **las dimensiones de la forma** usando Aspose.Words. El enfoque de forma agrupada mantiene tu diseño flexible y listo para futuras extensiones, como gráficos adicionales o cuadros de texto.

A continuación, explora temas relacionados como **crear formas en Word** para círculos, flechas o rutas SVG personalizadas, y aprende a **establecer el color de relleno de la forma** o **aplicar rotación**. Experimenta con diferentes medidas para ver cómo Word renderiza puntos frente a centímetros, e integra el código en pipelines más amplios de generación de documentos.

¡Feliz codificación, y siéntete libre de adaptar este patrón a cualquier escenario de generación automática de informes o llenado de formularios que encuentres!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Crear forma rectangular en Word usando C# – Guía paso a paso](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Crear documento Word en blanco con forma rectangular con sombra – Guía paso a paso](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Tutorial de sombra de forma Aspose.Words – Añadir una sombra a una forma Word en C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}