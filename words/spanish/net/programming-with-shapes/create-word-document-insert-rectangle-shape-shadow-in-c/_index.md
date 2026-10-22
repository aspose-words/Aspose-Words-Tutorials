---
category: general
date: 2026-05-26
description: Crear documento de Word en C# con Aspose.Words, insertar forma rectangular,
  establecer color de relleno y añadir efecto de sombra – guía paso a paso.
draft: false
keywords:
- create word document
- insert rectangle shape
- how to add shadow
- how to insert shape
- how to set fill
language: es
og_description: Crea un documento Word en C# usando Aspose.Words. Aprende cómo insertar
  una forma rectangular, establecer su color de relleno y agregar un efecto de sombra.
og_title: Crear documento de Word – Insertar forma de rectángulo y sombra en C#
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Create Word document in C# with Aspose.Words, insert rectangle shape,
    set fill color, and add shadow effect – step‑by‑step guide.
  headline: Create Word Document – Insert Rectangle Shape & Shadow in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Crear documento de Word – Insertar forma de rectángulo y sombra en C#
url: /es/net/programming-with-shapes/create-word-document-insert-rectangle-shape-shadow-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear documento de Word – Insertar forma rectangular y sombra en C#

¿Alguna vez te has preguntado cómo **crear un documento de Word** programáticamente sin abrir Microsoft Word primero? No eres el único. En muchos escenarios de automatización—piensa en facturas, contratos o generación masiva de informes—necesitas una forma fiable de crear un archivo .docx, colocar una forma dentro, darle un color y, quizás, incluso una sombra para lograr un aspecto pulido.

En este tutorial recorreremos exactamente eso: usar Aspose.Words for .NET para **crear documento de Word**, **insertar forma rectangular**, aplicar un relleno y **añadir sombra**. Al final tendrás un archivo listo‑para‑guardar que puedes canalizar a cualquier flujo de trabajo posterior.

También abordaremos **cómo insertar forma** de manera flexible, y por qué **cómo establecer el relleno** es importante para la consistencia visual. Sin rodeos, solo el código que puedes copiar‑pegar y ejecutar.

## Requisitos previos

Antes de sumergirnos, asegúrate de tener:

- .NET 6+ (o .NET Framework 4.7+) instalado.
- Una licencia válida de Aspose.Words for .NET (o una clave de evaluación temporal).
- Visual Studio, Rider o cualquier IDE de C# que prefieras.
- Familiaridad básica con la sintaxis de C#—no se requiere nada avanzado.

¿Los tienes? Genial, comencemos.

## Paso 1 – Crear documento de Word

Lo primero que necesitas es un objeto de documento en blanco. Este es el lienzo donde vive todo lo demás.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document and a DocumentBuilder.
Document doc = new Document();                 // The document itself.
DocumentBuilder builder = new DocumentBuilder(doc); // Helper to add content.
```

`Document` representa el archivo .docx en memoria, mientras que `DocumentBuilder` nos brinda una API cómoda para insertar texto, tablas y formas. **Crear el documento de Word** de esta manera es instantáneo—sin UI, sin interop COM, solo .NET puro.

## Paso 2 – Insertar forma rectangular

Ahora que tenemos un documento, vamos a **insertar forma rectangular**. El método `InsertShape` recibe un enum `ShapeType`, ancho y alto (en puntos). Usaremos un rectángulo de 150 × 80 puntos, lo que equivale aproximadamente a 2 × 1 pulgadas.

```csharp
// Step 2: Insert a rectangle shape of the desired size.
Shape shape = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

Detrás de escena, Aspose crea un objeto `Shape`, lo agrega al párrafo actual y devuelve una referencia que puedes estilizar. Este es el núcleo de **cómo insertar forma**—una sola línea de código, pero increíblemente poderosa.

## Paso 3 – Cómo establecer el relleno

Una forma sin relleno es invisible en una página blanca. Démosle un agradable fondo azul claro.

```csharp
// Step 3: Apply a fill color to make the shape visible.
shape.FillColor = System.Drawing.Color.LightBlue; // Any System.Drawing.Color works.
```

También podrías usar degradados, texturas o incluso un relleno de imagen, pero un color sólido mantiene el ejemplo simple. Esto demuestra **cómo establecer el relleno** en cualquier forma que crees, garantizando la pista visual que tus lectores esperan.

## Paso 4 – Cómo añadir sombra

Las sombras añaden profundidad y hacen que la forma destaque. Aspose.Words expone un objeto `ShadowFormat` donde puedes activar la visibilidad, elegir un color y afinar el desenfoque, la distancia y el ángulo.

```csharp
// Step 4: Configure the shadow effect – enable it, set color, blur, distance and angle.
shape.ShadowFormat.Visible = true;                     // Turn the shadow on.
shape.ShadowFormat.Color = System.Drawing.Color.Gray; // Shadow color.
shape.ShadowFormat.BlurRadius = 4.0;                  // Softness in pixels.
shape.ShadowFormat.Distance = 3.0;                    // How far the shadow is offset.
shape.ShadowFormat.Angle = 45;                        // Direction of the offset (degrees).
```

¿Por qué estos valores en particular? Un ángulo de 45° brinda una fuente de luz natural desde la parte superior‑derecha, un desenfoque moderado mantiene la sombra sutil y una distancia corta evita que la forma parezca desprendida. Siéntete libre de experimentar—cambiar el ángulo a 135° hará que la sombra caiga hacia la parte inferior‑izquierda, por ejemplo.

## Paso 5 – Guardar el documento

Todo el trabajo está hecho; ahora escribimos el archivo en disco. Elige cualquier ruta que prefieras; solo asegúrate de que la carpeta exista.

```csharp
// Step 5: Save the document with the shaped shadow.
doc.Save("YOUR_DIRECTORY/ShadowShape.docx");
```

Cuando abras `ShadowShape.docx` en Microsoft Word, verás un rectángulo azul claro con una sombra gris suave—exactamente lo que programamos.

## Ejemplo completo

Juntándolo todo, aquí tienes el programa completo, listo para copiar‑pegar:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a rectangle shape (150 × 80 points).
        Shape shape = builder.InsertShape(ShapeType.Rectangle, 150, 80);

        // 3️⃣ Set a solid fill color so the shape is visible.
        shape.FillColor = System.Drawing.Color.LightBlue;

        // 4️⃣ Add a subtle shadow for depth.
        shape.ShadowFormat.Visible = true;
        shape.ShadowFormat.Color = System.Drawing.Color.Gray;
        shape.ShadowFormat.BlurRadius = 4.0;   // pixels
        shape.ShadowFormat.Distance = 3.0;     // pixels
        shape.ShadowFormat.Angle = 45;        // degrees

        // 5️⃣ Persist the document.
        doc.Save("ShadowShape.docx");
    }
}
```

### Resultado esperado

- Un archivo llamado **ShadowShape.docx** aparece en la carpeta de destino.
- Al abrirlo en Word se muestra un rectángulo azul claro centrado en la primera página.
- El rectángulo proyecta una sombra gris en un ángulo de 45°, proporcionando un sutil efecto 3‑D.

## Preguntas frecuentes y casos límite

**¿Qué pasa si necesito una forma diferente?**  
Reemplaza `ShapeType.Rectangle` por cualquier otro valor del enum (`Ellipse`, `Star`, `Arrow`, etc.). El resto del código permanece igual.

**¿Puedo añadir texto dentro de la forma?**  
Sí—después de crear la forma, llama a `shape.AppendChild(new Paragraph(doc))` y luego inserta un `Run` con tu texto. Recuerda establecer las propiedades `shape.TextBox` si deseas ajuste de texto.

**¿Qué hay de DPI o unidades de medida?**  
Aspose trabaja en puntos (1 pt = 1/72 pulgada). Si prefieres centímetros, multiplica por 28.35 (ya que 1 cm ≈ 28.35 pt).

**¿Necesito una licencia para que esto funcione?**  
La versión de evaluación añade una marca de agua en la primera página. Una licencia adecuada la elimina y desbloquea la API completa.

## Consejos y advertencias

- **Consejo profesional:** Llama a `builder.MoveToDocumentEnd()` antes de insertar una forma si deseas que esté al final del documento.
- **Cuidado con:** Guardar en una carpeta de solo lectura lanzará una `UnauthorizedAccessException`. Asegúrate de que tu aplicación tenga permisos de escritura.
- **Nota de rendimiento:** Para generación masiva (cientos de documentos), reutiliza una única instancia de `Document` como plantilla y clónala con `doc.Clone(true)` para evitar la sobrecarga de inicialización repetida.

## Conclusión

Ahora sabes cómo **crear documento de Word**, **insertar forma rectangular**, **establecer el relleno** y **añadir sombra** usando Aspose.Words for .NET. El fragmento anterior es una solución autónoma que puedes incorporar a cualquier proyecto C#, ya sea una aplicación de consola, una API web o un servicio en segundo plano.

A partir de aquí podrías explorar:

- Agregar múltiples formas con colores variados.
- Usar degradados o rellenos de imagen (`shape.FillColor = ...` → `shape.FillPattern`).
- Combinar formas con tablas para diseños de informes complejos.

¡Pruébalo, ajusta los parámetros y observa cómo tus archivos de Word automatizados se ven más profesionales con solo unas pocas líneas de código. ¡Feliz codificación!

## Tutoriales relacionados

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}