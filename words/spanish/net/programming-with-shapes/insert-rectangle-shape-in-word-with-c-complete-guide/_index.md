---
category: general
date: 2026-08-10
description: Insertar una forma rectangular en Word usando C#. Aprende cómo ocultar
  la forma, ocultar la forma en Word y crear una forma oculta con Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to hide shape
- hide shape in word
- create hidden shape
language: es
lastmod: 2026-08-10
og_description: Insertar forma de rectángulo en Word usando C#. Este tutorial explica
  cómo ocultar la forma, ocultar la forma en Word y crear una forma oculta con ejemplos
  de código completos.
og_image_alt: Screenshot showing a hidden rectangle shape inserted into a Word document
  using C#
og_title: Insertar forma de rectángulo en Word con C# – guía paso a paso
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Insert rectangle shape in Word using C#. Learn how to hide shape, hide
    shape in Word, and create hidden shape with Aspose.Words.
  headline: Insert rectangle shape in Word with C# – complete guide
  type: TechArticle
- description: Insert rectangle shape in Word using C#. Learn how to hide shape, hide
    shape in Word, and create hidden shape with Aspose.Words.
  name: Insert rectangle shape in Word with C# – complete guide
  steps:
  - name: Can I hide only the outline but keep the fill visible?
    text: Yes. Instead of setting `Hidden = true`, you can set `rectangle.LineFormat.Visible
      = false` to hide the border while keeping the fill color. This is a variation
      of **how to hide shape** that preserves part of the visual appearance.
  - name: Does the hidden flag work in older Word versions (2003, 2007)?
    text: The hidden attribute is part of the Open XML specification introduced with
      Word 2007. Documents saved in the older binary `.doc` format will not preserve
      the flag. To support legacy formats, save the document as `.docx` and, if needed,
      convert it later using Aspose.Words’ `SaveFormat.Doc`.
  - name: What if I need to hide multiple shapes at once?
    text: Iterate over the `Document.GetChildNodes(NodeType.Shape, true)` collection
      and set `Hidden = true` on each shape that meets your criteria (e.g., a specific
      `ShapeType` or a custom `AlternativeText` value).
  - name: Is there a performance impact when hiding shapes?
    text: The hidden flag adds a tiny XML attribute; it does not affect rendering
      speed. However, a very large number of hidden objects can increase file size
      marginally. Remove shapes you never need to keep the document lean.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Insertar forma de rectángulo en Word con C# – guía completa
url: /es/net/programming-with-shapes/insert-rectangle-shape-in-word-with-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Insertar forma de rectángulo en Word con C# – guía completa

Si necesitas **insertar forma de rectángulo** en un documento de Word usando C#, esta guía te muestra los pasos exactos. También aprenderás **cómo ocultar una forma** para que no aparezca en el archivo final, lo que responde a la consulta común **hide shape in Word** y demuestra cómo **crear una forma oculta** programáticamente.

El tutorial cubre todo, desde la configuración del SDK Aspose.Words hasta la verificación de que la forma está oculta. Al final del artículo tendrás un fragmento de código reutilizable que podrás insertar en cualquier proyecto .NET.

## Requisitos previos

Antes de comenzar, asegúrate de tener:

- .NET 6.0 o posterior instalado (el código también funciona con .NET Framework 4.6+)
- Una licencia válida de Aspose.Words for .NET o una clave de evaluación temporal
- Visual Studio 2022 (o cualquier IDE que soporte C#)
- Familiaridad básica con la sintaxis de C# y el Document Object Model (DOM) de los archivos Word

No se requieren paquetes NuGet adicionales más allá de `Aspose.Words`.

## Paso 1: Crear un nuevo documento en blanco y un DocumentBuilder

La primera operación es instanciar un objeto `Document`. El `DocumentBuilder` proporciona una API conveniente para insertar contenido como formas, párrafos y tablas.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty Word document.
Document document = new Document();

// DocumentBuilder lets you add elements to the document.
DocumentBuilder builder = new DocumentBuilder(document);
```

**Por qué es importante:** `Document` representa todo el archivo .docx, mientras que `DocumentBuilder` mantiene un cursor que rastrea dónde se colocará el siguiente elemento. Inicializar ambos objetos es la base para cualquier tarea de automatización de Word.

## Paso 2: Insertar forma de rectángulo

Ahora insertas el rectángulo. El método `InsertShape` requiere el tipo de forma y sus dimensiones en puntos (1 punto ≈ 1/72 pulgada). Un tamaño de **200 × 100 puntos** produce un rectángulo de aproximadamente 2.78 × 1.39 pulgadas.

```csharp
// Insert a rectangle of 200x100 points.
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

**Por qué es importante:** El objeto `Shape` que recibes es totalmente configurable: color, borde, texto y visibilidad pueden modificarse antes de guardar el documento.

## Paso 3: Ocultar la forma

Para evitar que el rectángulo se muestre o imprima, establece su propiedad `Hidden` en `true`. Esta propiedad se corresponde directamente con el atributo “Hidden” de Word, que Word respeta tanto en la vista como en el modo de impresión.

```csharp
// Hide the shape so it never appears.
rectangle.Hidden = true;
```

**Por qué es importante:** Establecer `Hidden` es la forma estándar de **hide shape in Word** sin eliminarla de la estructura del documento. La forma sigue siendo accesible para el código, lo que permite manipulaciones posteriores como formato condicional o cambios de visibilidad basados en datos.

## Paso 4: Guardar el documento

Finalmente, persiste el documento en disco. Elige cualquier carpeta que desees; el ejemplo usa una ruta de marcador de posición que deberías reemplazar por una real.

```csharp
// Save the document with the hidden rectangle.
document.Save(@"C:\Temp\HiddenShape.docx");
```

**Por qué es importante:** Guardar finaliza el archivo y escribe la bandera oculta en el Open XML subyacente. Cuando abras el documento en Microsoft Word, el rectángulo será invisible, confirmando que has **creado una forma oculta** con éxito.

## Paso 5: Verificar la forma oculta

Abre el `HiddenShape.docx` generado en Microsoft Word:

1. Ve a **File → Options → Display** y asegúrate de que *“Show hidden text”* esté **desmarcado**.  
2. El rectángulo no debería ser visible en ninguna página.  
3. Para verificar, habilita *“Show hidden text”*; el rectángulo aparecerá con un contorno punteado tenue, demostrando que la forma existe pero está oculta.

Si el rectángulo sigue visible, verifica que hayas guardado el archivo después de establecer `Hidden = true` y que estés abriendo el archivo correcto.

## Ejemplo completo ejecutable

A continuación tienes el programa completo que puedes copiar, pegar y ejecutar directamente.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a rectangle shape of 200x100 points.
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // Step 3: Hide the shape so it does not appear when viewed or printed.
        rectangle.Hidden = true;

        // Step 4: Save the document with the hidden shape.
        string outputPath = @"C:\Temp\HiddenShape.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
        Console.WriteLine("Open the file in Word to verify that the rectangle is hidden.");
    }
}
```

**Salida esperada:** La consola imprime la ruta del archivo y un breve recordatorio. Cuando el archivo se abre en Word, el rectángulo es invisible a menos que se habilite el texto oculto.

## Preguntas comunes y casos límite

### ¿Puedo ocultar solo el contorno pero mantener el relleno visible?

Sí. En lugar de establecer `Hidden = true`, puedes establecer `rectangle.LineFormat.Visible = false` para ocultar el borde mientras mantienes el color de relleno. Esta es una variación de **how to hide shape** que preserva parte de la apariencia visual.

### ¿Funciona la bandera oculta en versiones antiguas de Word (2003, 2007)?

El atributo oculto es parte de la especificación Open XML introducida con Word 2007. Los documentos guardados en el formato binario `.doc` más antiguo no conservarán la bandera. Para soportar formatos heredados, guarda el documento como `.docx` y, si es necesario, conviértelo después usando `SaveFormat.Doc` de Aspose.Words.

### ¿Qué pasa si necesito ocultar varias formas a la vez?

Itera sobre la colección `Document.GetChildNodes(NodeType.Shape, true)` y establece `Hidden = true` en cada forma que cumpla tus criterios (p. ej., un `ShapeType` específico o un valor personalizado de `AlternativeText`).

```csharp
foreach (Shape shp in document.GetChildNodes(NodeType.Shape, true))
{
    if (shp.AlternativeText == "HideMe")
        shp.Hidden = true;
}
```

### ¿Hay un impacto en el rendimiento al ocultar formas?

La bandera oculta añade un atributo XML diminuto; no afecta la velocidad de renderizado. Sin embargo, un número muy grande de objetos ocultos puede aumentar ligeramente el tamaño del archivo. Elimina las formas que nunca necesites para mantener el documento ligero.

## Consejos y buenas prácticas

- **Asigna a la forma un nombre significativo** usando `rectangle.Name = "MyHiddenRectangle"`; esto ayuda cuando luego busques la forma en el DOM.
- **Establece `AlternativeText`** a una etiqueta personalizada (p.ej., `"HiddenShape"`). Esto te permite localizar la forma sin depender de su índice.
- **Envuelve el código en un bloque try‑catch** para manejar errores de licencia o excepciones de E/S de forma elegante.
- **Libera el Document** después de guardar si estás procesando muchos archivos en un bucle para liberar recursos no administrados: `document.Dispose();`.

## Conclusión

Ahora sabes cómo **insertar forma de rectángulo** en un documento de Word con C#, cómo **hide shape in Word** y cómo **crear una forma oculta** que permanece como parte de la estructura del documento pero invisible para los usuarios finales. El ejemplo completo y ejecutable muestra todo el flujo de trabajo, desde la creación del documento hasta la verificación.

A continuación, podrías explorar **how to hide shape** basado en la entrada del usuario, o combinar formas ocultas con controles de contenido para generación dinámica de documentos. También puedes aplicar la misma técnica a otros tipos de forma como elipses, flechas o dibujos personalizados.

Siéntete libre de experimentar con diferentes dimensiones, colores y configuraciones de visibilidad. Si encuentras algún problema, revisa los pasos anteriores o consulta la documentación de Aspose.Words para obtener detalles más profundos de la API. ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Crear forma de rectángulo en Word usando C# – Guía paso a paso](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Crear forma de rectángulo en Word con Aspose.Words – Guía paso a paso](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Tutorial de sombra de forma Aspose.Words – Añadir una sombra a una forma de Word en C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}