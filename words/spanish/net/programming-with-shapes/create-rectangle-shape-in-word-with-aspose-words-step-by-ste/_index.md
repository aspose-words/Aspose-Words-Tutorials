---
category: general
date: 2026-02-18
description: Crea una forma rectangular usando Aspose.Words y aprende cómo agregar
  sombra, establecer el tamaño de la forma y guardar el documento de Word en unos
  minutos.
draft: false
keywords:
- create rectangle shape
- how to add shadow
- save word document
- set shape size
- how to create document
language: es
og_description: Crea una forma rectangular en un archivo de Word, aprende cómo agregar
  sombra, establecer el tamaño de la forma y guardar el documento con Aspose.Words
  en C#.
og_title: Crear forma de rectángulo en Word – Tutorial completo de Aspose.Words
tags:
- Aspose.Words
- C#
- Word automation
title: Crear forma rectangular en Word con Aspose.Words – Guía paso a paso
url: /es/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear forma rectangular en Word con Aspose.Words – Guía paso a paso

¿Alguna vez necesitaste **crear una forma rectangular** en un archivo Word pero no sabías por dónde empezar? No eres el único—los desarrolladores a menudo preguntan: “¿cómo agrego una sombra a una forma y sigo manteniendo el documento editable?” En este tutorial responderemos eso y también te mostraremos **cómo agregar sombra**, **establecer el tamaño de la forma** y **guardar el documento Word** todo en un flujo continuo.

Recorreremos todo lo que necesitas, desde inicializar un nuevo documento (sí, ese es el primer paso para **cómo crear documento**) hasta persistir el *.docx* final en disco. Sin referencias externas, solo un ejemplo autocontenido que puedes copiar‑pegar en Visual Studio y ejecutar hoy.

---

## Prerrequisitos

- .NET 6+ (o .NET Framework 4.7+). Aspose.Words funciona con cualquier runtime .NET reciente.
- Una licencia válida de Aspose.Words (o la clave de evaluación gratuita) – de lo contrario verás una marca de agua.
- Visual Studio, Rider o cualquier editor de C# que prefieras.
- Conocimientos básicos de C#—nada sofisticado, solo la capacidad de ejecutar una aplicación de consola.

> **Consejo profesional:** Si estás en Mac, el mismo código se ejecuta bajo .NET 6 con VS Code—solo asegúrate de referenciar el paquete NuGet `Aspose.Words`.

---

## Paso 1: Inicializar el documento – la base de **cómo crear documento**

Antes de poder dibujar cualquier cosa, necesitamos un lienzo en blanco. Aspose.Words llama a esto un `Document`.  

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1: Create a new blank document
Document document = new Document();
```

> **Por qué importa:** El objeto `Document` representa todo el archivo *.docx*. Todas las formas, párrafos y secciones que agregues se convierten en hijos de este objeto. Comenzar con un documento limpio garantiza que no haya estilos ocultos que interfieran con tu rectángulo.

---

## Paso 2: Definir el rectángulo y **establecer el tamaño de la forma**

Un rectángulo es simplemente un `Shape` con `ShapeType.Rectangle`. Le daremos dimensiones explícitas para que se vea exactamente como se pretende.

```csharp
// Step 2: Create a rectangular shape and define its size
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 200; // width in points (≈2.78 inches)
rectangleShape.Height = 100; // height in points (≈1.39 inches)
```

> **Qué significan los números:** Aspose.Words usa puntos (1 pt = 1/72 in). Ajusta los valores para que encajen en tu diseño; para una página A4 típica, 200 pt es un ancho cómodo.

---

## Paso 3: **Cómo agregar sombra** – haciendo que la forma destaque

Las sombras dan una pista visual de que la forma está “levemente elevada” de la página. La propiedad `Shadow` te permite ajustar color, distancia, transparencia y desenfoque.

```csharp
// Step 3: Apply a shadow to the shape
rectangleShape.Shadow.Color        = Color.Black; // Shadow color
rectangleShape.Shadow.Distance    = 5;           // Offset distance in points
rectangleShape.Shadow.Transparency = 0.4;        // 40 % transparent
rectangleShape.Shadow.BlurRadius  = 8;           // Soft edge radius
```

> **¿Por qué usar transparencia?** Una sombra totalmente opaca puede resultar dura. Configurarla a 0.4 hace que el efecto sea sutil y profesional.

---

## Paso 4: Posicionar el rectángulo – flujo en línea con el texto circundante

Si deseas que la forma se comporte como un carácter dentro de un párrafo, establece su `WrapType` a `Inline`. Esto mantiene el diseño predecible, especialmente cuando el documento se edita más tarde.

```csharp
// Step 4: Set the shape to flow inline with the surrounding text
rectangleShape.WrapType = WrapType.Inline;
```

> **Caso extremo:** Si necesitas que el rectángulo flote sobre el texto (p. ej., una marca de agua), cambia `WrapType` a `Square` o `BehindText`.

---

## Paso 5: Insertar la forma en el cuerpo del documento

Ahora realmente colocamos el rectángulo en el primer párrafo. Si el documento aún no tiene contenido, `FirstParagraph` se crea automáticamente.

```csharp
// Step 5: Insert the shape into the first paragraph of the document
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

> **Consejo:** También puedes crear un nuevo párrafo primero y luego anexar la forma—útil cuando necesitas texto alrededor.

---

## Paso 6: **Guardar documento Word** – el paso final

Con todo en su lugar, persistir el archivo es una sola línea. Elige cualquier ruta que desees; el ejemplo usa un marcador de posición que deberías reemplazar con tu propio directorio.

```csharp
// Step 6: Save the document with the shadowed shape
document.Save(@"C:\Temp\ShadowShape.docx");
```

> **Resultado:** Abre el *.docx* generado en Microsoft Word. Verás un rectángulo con sombra negra, 200 pt de ancho y 100 pt de alto, alineado en línea con el primer párrafo.

---

## Salida esperada

Al abrir **ShadowShape.docx**, el documento muestra:

- Un solo párrafo que contiene una forma rectangular.
- El rectángulo tiene una sombra negra sutil desplazada 5 pt.
- El tamaño de la forma coincide con las dimensiones establecidas en el Paso 2.
- No aparece texto extra a menos que lo añadas manualmente.

Si la forma no aparece, verifica que hayas referenciado la versión correcta de Aspose.Words y que tu licencia (o prueba) esté activa.

---

## Preguntas frecuentes y variaciones

| Pregunta | Respuesta |
|----------|-----------|
| *¿Puedo cambiar el color de la sombra a algo distinto del negro?* | Por supuesto—establece `rectangleShape.Shadow.Color = Color.Blue;` o cualquier `System.Drawing.Color`. |
| *¿Qué pasa si necesito un rectángulo más grande?* | Ajusta los valores de `Width` y `Height`. Recuerda que están en puntos; 72 pt = 1 in. |
| *¿Es posible colocar la forma en una posición absoluta?* | Sí—usa `WrapType = WrapType.Absolute` y establece las propiedades `Top`/`Left`. |
| *¿Esto funciona con .NET Core?* | Funciona. Aspose.Words es multiplataforma; solo instala el paquete NuGet para .NET Standard. |
| *¿Puedo agregar texto dentro del rectángulo?* | No directamente; tendrías que insertar una forma `TextBox` en lugar de un rectángulo simple. |

---

## Ejemplo completo (listo para copiar‑pegar)

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize a new document
        Document document = new Document();

        // 2️⃣ Create rectangle and set its size
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width  = 200;
        rectangleShape.Height = 100;

        // 3️⃣ Add a subtle black shadow
        rectangleShape.Shadow.Color         = Color.Black;
        rectangleShape.Shadow.Distance     = 5;
        rectangleShape.Shadow.Transparency = 0.4;
        rectangleShape.Shadow.BlurRadius   = 8;

        // 4️⃣ Make the shape flow inline with text
        rectangleShape.WrapType = WrapType.Inline;

        // 5️⃣ Insert the shape into the first paragraph
        document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

        // 6️⃣ Persist the file
        document.Save(@"C:\Temp\ShadowShape.docx");

        System.Console.WriteLine("Document saved successfully!");
    }
}
```

Ejecuta el programa, navega a `C:\Temp\ShadowShape.docx` y verás el rectángulo con sombra exactamente como se describió.

---

## Conclusión

Ahora sabes cómo **crear una forma rectangular** en un archivo Word usando Aspose.Words, cómo **establecer el tamaño de la forma**, **agregar sombra**, y finalmente **guardar el documento Word** con los cambios. Todo el proceso—desde **cómo crear documento** hasta persistir el resultado—cabe en unas cuantas líneas de C# y puede ampliarse para diseños más complejos.

¿Listo para el próximo desafío? Prueba a sustituir el rectángulo por una forma con esquinas redondeadas, experimenta con diferentes colores de sombra, o incrusta la forma dentro de una celda de tabla. Cada ajuste refuerza los mismos conceptos básicos que cubrimos aquí.

Si encontraste útil esta guía, compártela, deja un comentario con tus propias variaciones, o explora nuestros otros tutoriales sobre automatización de Word, como insertar imágenes o generar tablas con Aspose.Words. ¡Feliz codificación!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}