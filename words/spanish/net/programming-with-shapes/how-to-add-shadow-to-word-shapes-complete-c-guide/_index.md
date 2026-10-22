---
category: general
date: 2026-06-30
description: Cómo agregar sombra en C# usando Aspose.Words. Aprende a cambiar el color
  de la sombra, ajustar la transparencia de la sombra, agregar sombra a una forma
  y guardar el documento modificado.
draft: false
keywords:
- how to add shadow
- change shadow color
- save modified document
- add shadow to shape
- adjust shadow transparency
language: es
og_description: Cómo agregar sombra en C# con Aspose.Words. Este tutorial muestra
  cómo agregar sombra a una forma, cambiar el color de la sombra, ajustar la transparencia
  de la sombra y guardar el documento modificado.
og_title: Cómo agregar sombra a las formas de Word – Guía completa de C#
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: How to add shadow in C# using Aspose.Words. Learn to change shadow
    color, adjust shadow transparency, add shadow to shape, and save modified document.
  headline: How to Add Shadow to Word Shapes – Complete C# Guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word Automation
title: Cómo agregar sombra a las formas de Word – Guía completa de C#
url: /es/net/programming-with-shapes/how-to-add-shadow-to-word-shapes-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo agregar sombra a formas de Word – Guía completa en C#

¿Alguna vez te has preguntado **cómo agregar sombra** a una forma de Word usando C#? No eres el único. Los desarrolladores a menudo necesitan ese sutil efecto de profundidad para informes, folletos o cualquier documento que deba verse un poco más pulido. ¿La buena noticia? Con unas pocas líneas de código puedes habilitar una sombra, ajustar su color e incluso modificar su transparencia, todo mientras mantienes el flujo de trabajo totalmente automatizado.

En este tutorial recorreremos **cómo agregar sombra** a una forma, **cambiar el color de la sombra**, **ajustar la transparencia de la sombra** y, finalmente, **guardar el documento modificado** para que los cambios persistan. Al final tendrás un fragmento reutilizable que podrás insertar en cualquier proyecto de Aspose.Words.

## Requisitos previos

Antes de sumergirnos, asegúrate de contar con:

* **Aspose.Words for .NET** (versión 23.11 o superior). Puedes obtenerlo desde NuGet con `Install-Package Aspose.Words`.
* Un entorno de desarrollo **.NET 6+** (Visual Studio, Rider o VS Code).
* Un archivo Word de entrada (`input.docx`) que ya contenga al menos una forma (por ejemplo, un rectángulo, una estrella o una imagen).

Eso es todo, sin bibliotecas adicionales, sin pasos manuales en la UI. ¿Listo? Comencemos.

## Paso 1 – Cargar el documento Word (Cómo agregar sombra)

Lo primero que debes saber **cómo agregar sombra** es que debes cargar el documento en un objeto `Aspose.Words.Document`. Esto te brinda acceso programático a cada nodo, incluidas las formas.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // Load the source document that contains the shape.
        Document doc = new Document(@"C:\Docs\input.docx");
```

> **Por qué es importante:** Cargar el archivo es la puerta de entrada a cualquier manipulación. Sin una instancia de `Document` no puedes alcanzar el árbol de formas y, por lo tanto, no puedes aplicar una sombra.

## Paso 2 – Obtener la forma objetivo (Agregar sombra a la forma)

Ahora que el documento está en memoria, localicemos la forma que queremos estilizar. Este paso muestra **agregar sombra a la forma** para la primera forma encontrada, pero puedes ampliarlo fácilmente para seleccionar por nombre o índice.

```csharp
        // Retrieve the first shape in the document (searches recursively).
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

        if (shape == null)
        {
            Console.WriteLine("No shape found in the document.");
            return;
        }
```

> **Consejo:** Si tu documento contiene varias formas, reemplaza el `0` por el índice correspondiente o recorre `doc.GetChildNodes(NodeType.Shape, true)`.

## Paso 3 – Habilitar la sombra y configurar su apariencia (Cambiar color de sombra y ajustar transparencia)

Aquí está el corazón de **cómo agregar sombra**: activamos la sombra, establecemos su desplazamiento, desenfoque, color y transparencia. Siéntete libre de experimentar con los valores numéricos para obtener el aspecto exacto que necesitas.

```csharp
        // Turn the shadow on.
        shape.ShadowFormat.Visible = true;

        // Position the shadow 4 points to the right and 4 points down.
        shape.ShadowFormat.OffsetX = 4; // Horizontal offset in points.
        shape.ShadowFormat.OffsetY = 4; // Vertical offset in points.

        // Adjust shadow transparency – this demonstrates **adjust shadow transparency**.
        shape.ShadowFormat.Transparency = 0.3; // 30 % transparent.

        // Change the shadow color – this is the **change shadow color** part.
        shape.ShadowFormat.Color = Color.Gray; // You can use any System.Drawing.Color.

        // Add a subtle blur to soften the edges.
        shape.ShadowFormat.BlurRadius = 5; // Blur radius in points.
```

> **¿Por qué estos ajustes?**  
> *`Visible`* activa el efecto.  
> *`OffsetX`/`OffsetY`* simulan una fuente de luz, proporcionando profundidad.  
> *`Transparency`* te permite hacer la sombra más clara u oscura sin cambiar el color, una forma clásica de **ajustar la transparencia de la sombra**.  
> *`Color`* te permite **cambiar el color de la sombra**; el gris funciona para la mayoría de documentos empresariales, pero puedes usar `Color.Black` o cualquier `Color.FromArgb(...)` personalizado.  
> *`BlurRadius`* añade realismo; las sombras nítidas se ven artificiales.

## Paso 4 – Guardar el documento modificado (Guardar documento modificado)

Finalmente, persistimos los cambios. Este paso responde **guardar documento modificado** sin intervención manual.

```csharp
        // Save the updated document to a new file.
        doc.Save(@"C:\Docs\output.docx");

        Console.WriteLine("Shadow applied and document saved successfully.");
    }
}
```

> **¿Qué ocurre tras bambalinas?** Aspose.Words escribe las partes XML actualizadas, incluido el elemento `<w:shadow>` con todos los atributos que acabas de establecer. El `output.docx` resultante se abrirá en Word con la sombra ya aplicada.

## Ejemplo completo funcionando

Juntándolo todo, aquí tienes el programa completo listo para copiar y pegar:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // 1️⃣ Load the Word document that contains the shape.
        Document doc = new Document(@"C:\Docs\input.docx");

        // 2️⃣ Retrieve the first shape (add shadow to shape).
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            Console.WriteLine("No shape found in the document.");
            return;
        }

        // 3️⃣ Enable the shadow and configure its appearance.
        shape.ShadowFormat.Visible = true;
        shape.ShadowFormat.OffsetX = 4;
        shape.ShadowFormat.OffsetY = 4;
        shape.ShadowFormat.Transparency = 0.3;      // Adjust shadow transparency.
        shape.ShadowFormat.Color = Color.Gray;      // Change shadow color.
        shape.ShadowFormat.BlurRadius = 5;

        // 4️⃣ Save the modified document (save modified document).
        doc.Save(@"C:\Docs\output.docx");

        Console.WriteLine("Shadow applied and document saved successfully.");
    }
}
```

### Resultado esperado

Abre `output.docx` en Microsoft Word. La primera forma que tenías en `input.docx` mostrará ahora una sombra gris suave, desplazada 4 pt, con un 30 % de transparencia y un ligero desenfoque. El resto del documento permanece sin cambios.

## Variaciones comunes y casos límite

| Situación | Qué ajustar | Por qué |
|-----------|-------------|---------|
| **Múltiples formas** | Recorrer `doc.GetChildNodes(NodeType.Shape, true)` y aplicar los mismos ajustes a cada una. | Garantiza que cada gráfico obtenga la misma profundidad visual. |
| **Colores de sombra diferentes** | Usar `shape.ShadowFormat.Color = Color.FromArgb(255, 100, 100);` para un tono rojizo. | Permite coherencia de marca o temática. |
| **No se necesita sombra en una forma concreta** | Omitir la forma basándose en `shape.Name` o `shape.ShapeType`. | Evita efectos no deseados en logotipos o íconos. |
| **Mayor transparencia** | Establecer `Transparency = 0.7` para una sombra tenue tipo fantasma. | Útil para fondos sutiles. |
| **Rendimiento en documentos grandes** | Cargar el documento con `LoadOptions` que omitan fuentes innecesarias. | Reduce la huella de memoria al procesar muchos archivos. |

## Consejos y trucos (Pro Tips)

* **Pro tip:** Si necesitas una *sombra paralela* que imite Photoshop, aumenta `BlurRadius` a 10‑12 y establece `Transparency` en 0.2 para un aspecto más definido.  
* **Cuidado con:** Formas que son *en línea* vs *flotantes*. Las formas en línea heredan el formato del párrafo y su sombra puede no renderizarse exactamente igual. Usa `shape.IsInline` para decidir si primero debes convertirla a forma flotante.  
* **Método reutilizable:** Encapsula la lógica de sombra en un método auxiliar:

```csharp
static void ApplyShadow(Shape s, int offset = 4, double transparency = 0.3,
                        Color? color = null, int blur = 5)
{
    s.ShadowFormat.Visible = true;
    s.ShadowFormat.OffsetX = offset;
    s.ShadowFormat.OffsetY = offset;
    s.ShadowFormat.Transparency = transparency;
    s.ShadowFormat.Color = color ?? Color.Gray;
    s.ShadowFormat.BlurRadius = blur;
}
```

Ahora puedes llamar `ApplyShadow(shape);` donde lo necesites.

## Conclusión

Acabamos de cubrir **cómo agregar sombra** a una forma de Word usando C#. Los pasos te mostraron cómo **agregar sombra a la forma**, **cambiar el color de la sombra**, **ajustar la transparencia de la sombra** y, finalmente, **guardar el documento modificado**. Con este conocimiento puedes enriquecer cualquier informe automatizado, folleto de marketing o memorando interno con un toque visual de nivel profesional.

¿Qué sigue? Prueba combinar esto con otras características de formato, como rellenos degradados o efectos 3‑D, para crear documentos realmente llamativos. O explora la API de Aspose.Words para tablas, gráficos y combinación de correspondencia y crea pipelines de documentos de extremo a extremo.

¿Tienes alguna pregunta sobre un tipo de forma específico o necesitas aplicar sombras de forma condicional? Deja un comentario abajo y sigamos la conversación. ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques alternativos de implementación en tus propios proyectos.

- [Tutorial de sombra de forma en Aspose.Words – Añadir una sombra a una forma de Word en C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Agregar contenido usando Document Builder en Aspose.Words para .NET](/words/english/net/add-content-using-document-builder/)
- [Agregar marca de agua de texto en documento Word usando Aspose.Words para .NET](/words/english/net/working-with-watermark/add-text-watermark/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}