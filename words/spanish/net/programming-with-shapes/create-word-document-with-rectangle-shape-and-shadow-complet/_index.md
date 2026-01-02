---
category: general
date: 2026-01-02
description: Crear un documento de Word con una forma rectangular, establecer el color
  de relleno de la forma y guardar el archivo docx usando Aspose.Words. Aprenda a
  crear un rectángulo con sombra en minutos.
draft: false
keywords:
- create word document
- add rectangle shape
- set shape fill color
- save docx file
- how to create rectangle
language: es
og_description: Crear documento de Word con un rectángulo personalizado, establecer
  su color de relleno, agregar una sombra y guardarlo como DOCX. Código completo y
  explicaciones.
og_title: Crear documento de Word con forma de rectángulo – paso a paso
tags:
- Aspose.Words
- C#
- Document Generation
title: Crear documento de Word con forma rectangular y sombra – Guía completa
url: /es/net/programming-with-shapes/create-word-document-with-rectangle-shape-and-shadow-complet/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear documento de Word con forma de rectángulo y sombra – Guía completa

¿Alguna vez te has preguntado cómo **crear documento de Word** que contenga un rectángulo con buen estilo? Tal vez necesites un marcador de posición para un logotipo, una pancarta de color o simplemente una pista visual en un informe. En este tutorial **agregaremos una forma de rectángulo**, le daremos un color de relleno, aplicaremos una sombra sutil y, finalmente, **guardaremos el archivo docx** – todo con Aspose.Words para .NET.

Te quedarás con un fragmento de C# listo para ejecutar, una explicación clara de cada línea y un puñado de consejos que puedes reutilizar en tus propios proyectos. Sin rodeos, solo una solución práctica que puedes copiar y pegar.

## Lo que necesitarás

- .NET 6 o posterior (el código también funciona en .NET Framework)  
- Visual Studio 2022 (o cualquier editor que prefieras)  
- **Aspose.Words** paquete NuGet (`Install-Package Aspose.Words`)  

Si ya tienes eso, genial – vamos a sumergirnos.

## Paso 1 – Inicializar un nuevo documento (Cómo crear documento de Word)

Lo primero que debes hacer es **crear documento de Word** en memoria. Piensa en ello como abrir un lienzo en blanco donde luego dibujarás tu rectángulo.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // for Color struct

// Create a fresh, empty document
Document document = new Document();

// DocumentBuilder helps us add content step‑by‑step
DocumentBuilder builder = new DocumentBuilder(document);

// Write a simple heading so you can see something when you open the file
builder.Writeln("Shadow Demo");
```

> **Por qué es importante:** `Document` representa todo el archivo DOCX, mientras que `DocumentBuilder` es un asistente conveniente que te permite insertar texto, tablas, imágenes y formas sin manejar manualmente el árbol de nodos subyacente.

## Paso 2 – Insertar una forma de rectángulo (Agregar forma de rectángulo)

Ahora **agregaremos una forma de rectángulo** al documento. El método `InsertShape` recibe el tipo de forma y sus dimensiones en puntos (1 punto = 1/72 pulgada).

```csharp
// Insert a rectangle that will later receive a custom shadow
Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);

// Give the rectangle a light‑blue background so it stands out
rect.FillColor = Color.LightBlue;
```

> **Consejo profesional:** Si alguna vez necesitas crear una geometría diferente (elipse, triángulo, etc.), simplemente cambia `ShapeType.Rectangle` al valor de enumeración deseado.

## Paso 3 – Configurar la sombra (Establecer color de relleno y sombra de la forma)

Una sombra puede hacer que una forma plana parezca más tridimensional. Aquí habilitamos la sombra y ajustamos su apariencia.

```csharp
// Turn the shadow on
rect.ShadowFormat.Enabled = true;

// Choose a subtle gray for the shadow color
rect.ShadowFormat.Color = Color.Gray;

// Blur softens the edge of the shadow – 8 points looks nice
rect.ShadowFormat.BlurRadius = 8;

// Distance controls how far the shadow is offset from the shape
rect.ShadowFormat.Distance = 5;

// Angle determines the direction; 45° gives a bottom‑right offset
rect.ShadowFormat.Angle = 45;

// Transparency makes the shadow partially see‑through (0 = opaque, 1 = invisible)
rect.ShadowFormat.Transparency = 0.3; // 30 % transparent
```

> **¿Por qué estos valores?** Un radio de desenfoque modesto y una distancia de 5 puntos evitan que la sombra abrume la forma, mientras que 45° imita una fuente de luz que proviene de la esquina superior izquierda – una convención UI común.

## Paso 4 – Guardar el documento (Guardar archivo docx)

Finalmente, **guardamos el archivo docx** en disco. Ajusta la ruta según tu entorno.

```csharp
// Replace with the folder you actually want to use
string outputPath = @"C:\Temp\ShadowDemo.docx";

// Persist the document as a .docx file
document.Save(outputPath);
```

Cuando abras `ShadowDemo.docx` en Word, deberías ver un rectángulo azul claro con una sombra gris suave, justo como la captura de pantalla a continuación.

![Crear documento de Word con forma de rectángulo y sombra](https://example.com/images/rectangle-shadow.png "Crear documento de Word con forma de rectángulo y sombra")

*Texto alternativo de la imagen:* **Crear documento de Word** mostrando una forma de rectángulo con una sombra.

## Ejemplo completo, listo para ejecutar (Cómo crear rectángulo y guardar)

Juntando todo, aquí tienes el programa completo que puedes copiar en una aplicación de consola:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace AsposeRectangleDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Step 1: Initialize the document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);
            builder.Writeln("Shadow Demo");

            // Step 2: Insert the rectangle
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
            rect.FillColor = Color.LightBlue;   // set shape fill color

            // Step 3: Apply shadow formatting
            rect.ShadowFormat.Enabled = true;
            rect.ShadowFormat.Color = Color.Gray;
            rect.ShadowFormat.BlurRadius = 8;
            rect.ShadowFormat.Distance = 5;
            rect.ShadowFormat.Angle = 45;
            rect.ShadowFormat.Transparency = 0.3;

            // Step 4: Save the file
            string output = @"C:\Temp\ShadowDemo.docx";
            doc.Save(output);

            System.Console.WriteLine($"Document saved to {output}");
        }
    }
}
```

### Resultado esperado

- Aparece un archivo llamado **ShadowDemo.docx** en la carpeta de destino.  
- Al abrirlo en Microsoft Word muestra una sola página con el texto “Shadow Demo” seguido de un rectángulo azul claro.  
- El rectángulo proyecta una sombra gris suave en un ángulo de 45°, dándole una ligera sensación 3‑D.

## Preguntas frecuentes y casos límite

### ¿Qué pasa si necesito un tamaño diferente?

Simplemente cambia los argumentos `200, 100` en `InsertShape`. Esos números son el ancho y la altura en puntos. Para un cuadrado, usa valores idénticos.

### ¿Puedo hacer la sombra más pronunciada?

Incrementa `BlurRadius` para un borde más suave, aumenta `Distance` para un desplazamiento mayor, o reduce `Transparency` (p. ej., `0.1`) para que sea más oscura.

### ¿Cómo agrego un borde alrededor del rectángulo?

```csharp
rect.LineColor = Color.DarkBlue;   // border color
rect.LineWidth = 2;                // thickness in points
```

### ¿Es compatible con versiones anteriores de Aspose.Words?

Sí. La clase `ShadowFormat` existe desde las versiones de principios de 2020. Si estás en una versión muy antigua, puede que necesites actualizar para acceder a todas las propiedades.

## Consejos y trampas

- **Consejo profesional:** Siempre elimina (dispose) los documentos grandes (`doc.Dispose()`) cuando termines, especialmente en aplicaciones web, para liberar recursos nativos.  
- **Cuidado con:** Usar una ruta relativa sin los permisos adecuados puede causar `UnauthorizedAccessException`. Prefiere rutas absolutas o asegura que el pool de la aplicación tenga acceso de escritura.  
- **Recuerda:** La propiedad `FillColor` acepta cualquier `System.Drawing.Color`. Si lo deseas, usa `Color.FromArgb(255, 173, 216, 230)` para un tono pastel personalizado.

## Próximos pasos

Ahora que sabes cómo **crear documento de Word**, **agregar forma de rectángulo**, **establecer color de relleno de la forma**, y **guardar archivo docx**, puedes experimentar más:

- Inserta múltiples formas y organízalas con `RelativeHorizontalPosition` y `RelativeVerticalPosition`.  
- Combina el rectángulo con texto usando `Shape.TextBox` para subtítulos.  
- Exporta el mismo documento a PDF (`doc.Save("output.pdf")`) para distribución.

Si tienes curiosidad por gráficos más avanzados, revisa el soporte de Aspose.Words para **WordArt**, **gráficos**, y **imágenes en línea**. Cada uno sigue el mismo patrón: crear un nodo, configurar sus propiedades y guardar.

---

### TL;DR

- Usa `Document` y `DocumentBuilder` para **crear documento de Word**.  
- Llama a `InsertShape(ShapeType.Rectangle, …)` para **agregar forma de rectángulo**.  
- Establece `FillColor` para el fondo deseado.  
- Habilita `ShadowFormat` y ajusta sus propiedades para un aspecto pulido.  
- Termina con `document.Save("yourPath.docx")` para **guardar archivo docx**.

¡Feliz codificación, y disfruta haciendo que tus archivos de Word se vean un poco más elegantes!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}