---
category: general
date: 2026-09-14
description: Aprende cómo ocultar una forma en Word usando C#—incluyendo código para
  crear un documento de Word, insertar una forma rectangular en Word y ocultar la
  forma en Word de forma programática.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to hide shape
- hide shape in word
- create word document code
- insert rectangle shape word
language: es
lastmod: 2026-09-14
og_description: Cómo ocultar una forma en Word usando C# — guía paso a paso que también
  muestra cómo crear código de documento Word e insertar una forma rectangular en
  Word.
og_image_alt: Word document preview with a visible rectangle shape and a hidden ellipse
  shape
og_title: Cómo ocultar una forma en un documento de Word con código C#
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Learn how to hide shape in Word using C#—including create word document
    code, insert rectangle shape word, and hide shape in word programmatically.
  headline: How to hide shape in a Word document with C# code
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Cómo ocultar una forma en un documento de Word con código C#
url: /es/net/programming-with-shapes/how-to-hide-shape-in-a-word-document-with-c-code/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo ocultar una forma en un documento Word con código C#

Si necesitas **how to hide shape** en un archivo Word, este tutorial muestra la solución completa. Verás cómo crear un documento Word, insertar una forma rectangular, añadir una elipse y ocultar esa elipse para que solo el rectángulo aparezca cuando se abra el archivo.

La guía cubre todo lo que necesitas—sin referencias externas, solo el código y las explicaciones. Al final podrás incrustar gráficos ocultos en cualquier documento Word que generes programáticamente.

## Requisitos previos

- .NET 6.0 o posterior (el código también funciona con .NET Framework 4.7+)
- Aspose.Words for .NET (versión de prueba gratuita o con licencia)  
  Instálalo vía NuGet: `dotnet add package Aspose.Words`
- Familiaridad básica con C# y Visual Studio o cualquier IDE que prefieras

## Paso 1: Configurar el proyecto e importar espacios de nombres

Inicia una nueva aplicación de consola y agrega las declaraciones `using` requeridas. Estas importaciones te dan acceso a las clases `Document`, `DocumentBuilder` y de dibujo necesarias para manipular formas.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // The rest of the code follows in the next steps
        }
    }
}
```

**Por qué es importante** – Importar los espacios de nombres correctos evita errores de compilación y hace que la superficie de la API esté disponible para la creación de formas y el control de visibilidad.

## Paso 2: Crear un nuevo documento Word y un builder

Un `Document` representa el archivo, mientras que un `DocumentBuilder` proporciona una API fluida para agregar contenido. Este es el primer lugar donde aplicas la lógica de **how to hide shape**: necesitas un contexto de documento antes de que exista cualquier forma.

```csharp
// Step 2: Create a new blank document and a builder to edit it
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);
```

**Explicación** – El objeto `Document` comienza vacío. El `DocumentBuilder` está posicionado al inicio del primer párrafo, listo para insertar formas o texto.

## Paso 3: Insertar una forma rectangular visible

El rectángulo será la forma que permanecerá visible cuando se abra el documento. Puedes controlar su tamaño, posición y formato directamente a través del objeto shape.

```csharp
// Step 3: Insert a visible rectangle shape and position it
Shape visibleRectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
visibleRectangle.Left = 50;                 // 50 points from the left margin
visibleRectangle.Top = 100;                 // 100 points from the top of the page
visibleRectangle.FillColor = System.Drawing.Color.LightBlue;
visibleRectangle.LineColor = System.Drawing.Color.DarkBlue;
```

**Por qué este paso** – Añadir un rectángulo demuestra el requisito **insert rectangle shape word**. Configurar `FillColor` y `LineColor` hace que la forma sea fácil de detectar en el documento final.

## Paso 4: Insertar una forma elíptica y ocultarla

Ahora agregas la forma que deseas ocultar. La propiedad `Hidden` indica a Word que no renderice la forma en la interfaz, aunque sigue formando parte de la estructura del documento.

```csharp
// Step 4: Insert an ellipse shape, position it, and hide it from view
Shape hiddenEllipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
hiddenEllipse.Left = 200;      // Position away from the rectangle
hiddenEllipse.Top = 100;
hiddenEllipse.Hidden = true;   // This flag implements how to hide shape
```

**Explicación** – Configurar `Hidden = true` es el núcleo de **hide shape in word**. Word respeta esta bandera durante la visualización y la impresión normales, pero la forma aún puede ser accedida programáticamente si es necesario.

## Paso 5: Guardar el documento

Finalmente, escribe el documento en disco. Elige una carpeta a la que tengas acceso de escritura y asigna al archivo un nombre claro que refleje el propósito del tutorial.

```csharp
// Step 5: Save the document with both shapes
string outputPath = @"C:\Temp\ShapeVisibility.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

**Resultado** – Al abrir `ShapeVisibility.docx` en Microsoft Word solo se muestra el rectángulo azul‑claro. La elipse oculta no aparece, confirmando que has dominado con éxito **how to hide shape** en un archivo Word.

## Ejemplo completo funcional

Unir todos los fragmentos te brinda un programa único y ejecutable:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a new document and builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // Insert a visible rectangle
            Shape visibleRectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            visibleRectangle.Left = 50;
            visibleRectangle.Top = 100;
            visibleRectangle.FillColor = System.Drawing.Color.LightBlue;
            visibleRectangle.LineColor = System.Drawing.Color.DarkBlue;

            // Insert a hidden ellipse
            Shape hiddenEllipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
            hiddenEllipse.Left = 200;
            hiddenEllipse.Top = 100;
            hiddenEllipse.Hidden = true; // hides the shape

            // Save the document
            string outputPath = @"C:\Temp\ShapeVisibility.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Resultado esperado

- **Visual**: Al abrir `ShapeVisibility.docx`, ves un rectángulo azul‑claro ubicado cerca del margen izquierdo. No se ve ninguna elipse.
- **Programático**: La elipse oculta permanece en el XML del documento (elemento `<w:drawing>`) con el atributo `w:hidden` establecido, lo que puedes verificar abriendo el archivo como zip e inspeccionando `document.xml`.

## Preguntas frecuentes y casos límite

| Question | Answer |
|----------|--------|
| *¿Puedo ocultar múltiples formas?* | Sí. Establece `Hidden = true` en cada forma que quieras ocultar. |
| *¿Se imprimirán las formas ocultas?* | Por defecto Word no imprime los objetos ocultos. Si necesitas que se impriman, elimina la bandera `Hidden` antes de imprimir. |
| *¿La propiedad hidden es compatible con versiones anteriores de Word?* | El atributo `Hidden` forma parte del estándar Office Open XML y funciona en Word 2007 y posteriores. |
| *¿Qué pasa si necesito alternar la visibilidad en tiempo de ejecución?* | Obtén la forma mediante `document.GetChildNodes(NodeType.Shape, true)` y cambia la propiedad `Hidden` según tu lógica. |

## Consejos profesionales

- **Performance**: Si generas muchos documentos, reutiliza una única instancia de `DocumentBuilder` en lugar de crear una nueva para cada archivo.
- **Control de versiones**: Almacena los archivos `.docx` generados en una carpeta bajo control de versiones; las formas ocultas pueden actuar como marcadores de metadatos para el procesamiento posterior.
- **Pruebas**: Automatiza una prueba visual rápida convirtiendo el DOCX a PDF con Aspose.Words (`document.Save("out.pdf")`). El PDF también ocultará la elipse, confirmando que la bandera hidden se propaga a través de las conversiones de formato.

## Conclusión

Ahora sabes **how to hide shape** en un documento Word usando C#. El tutorial mostró cómo crear un documento, **insert rectangle shape word**, añadir una elipse y aplicar la bandera `Hidden` para lograr el comportamiento **hide shape in word**. Con el código completo y ejecutable puedes integrar gráficos ocultos en cualquier flujo de trabajo de generación de informes o plantillas automatizado.

### Próximos pasos

- Explora otras propiedades de las formas, como rotación, sombra y ajuste de texto.  
- Combina formas ocultas con propiedades de documento personalizadas para incrustar datos legibles por máquinas.  
- Investiga los patrones **create word document code** para tablas, gráficos y controles de contenido y amplía tu conjunto de herramientas de automatización.

¡Siéntete libre de experimentar con diferentes tipos de formas y configuraciones de visibilidad—tu próximo proyecto de automatización de Word está a solo unas líneas de código!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}