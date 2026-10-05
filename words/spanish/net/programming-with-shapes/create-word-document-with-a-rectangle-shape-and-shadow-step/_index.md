---
category: general
date: 2026-03-01
description: Crear documento de Word usando Aspose.Words y aprender cómo agregar una
  forma rectangular, cómo añadir sombra, cómo establecer transparencia y cómo crear
  una forma, todo en C#.
draft: false
keywords:
- create word document
- add rectangle shape
- how to add shadow
- how to create shape
- how to set transparency
language: es
og_description: Crea un documento Word con Aspose.Words en C#. Aprende a agregar una
  forma rectangular, aplicar una sombra externa y establecer la transparencia en solo
  unos pocos pasos.
og_title: Crear documento de Word con una forma rectangular y sombra – Guía
tags:
- Aspose.Words
- C#
- Document Generation
title: Crear documento de Word con una forma rectangular y sombra – Guía paso a paso
url: /es/net/programming-with-shapes/create-word-document-with-a-rectangle-shape-and-shadow-step/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear documento de Word con una forma rectangular y sombra – Guía paso a paso

¿Alguna vez necesitaste **crear un documento de Word** que contenga un rectángulo con estilo personalizado? Tal vez estés construyendo una plantilla de informe y quieras una sombra sutil que haga que el diseño destaque. No eres el único: los desarrolladores preguntan constantemente, “¿Cómo añado una forma rectangular y una sombra de forma programática?” La buena noticia es que con Aspose.Words puedes hacerlo en unas pocas líneas.

En este tutorial recorreremos todo el proceso: desde crear un archivo Word en blanco, hasta añadir una forma rectangular, configurar una sombra externa con transparencia. Al final tendrás un `Shadow.docx` listo para usar que podrás abrir en Word y ver el efecto al instante. Sin herramientas externas, sin XML complicado—solo código C# limpio y explicaciones claras.

## Qué aprenderás

- **Cómo crear objetos shape** en un documento de Word usando Aspose.Words.  
- **Cómo añadir una forma rectangular** a un párrafo sin desordenar el contenido existente.  
- **Cómo agregar sombra** (sombra externa) y controlar su color, desplazamiento, difuminado y transparencia.  
- **Cómo establecer transparencia** en la sombra para que se vea profesional.  
- Consejos, trampas y variaciones que podrías necesitar en proyectos del mundo real.

### Requisitos previos

- .NET 6.0 o superior (la API también funciona con .NET Framework 4.6+).  
- Aspose.Words para .NET instalado vía NuGet (`Install-Package Aspose.Words`).  
- Un conocimiento básico de la sintaxis de C#—nada elegante, solo las habituales sentencias `using` y la creación de objetos.

> **Consejo profesional:** Si usas Visual Studio, habilita “nullable reference types” para detectar posibles errores de referencia nula temprano.

## Paso 1 – Crear un documento de Word en blanco

Para **crear un documento de Word** empezamos con la clase `Document`. Piensa en ella como un lienzo vacío; luego podrás añadir secciones, párrafos, tablas o formas.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Initialize a new blank document
Document document = new Document();
```

¿Por qué necesitamos una instancia fresca de `Document`? Porque cada forma, párrafo o estilo vive dentro de un modelo de objetos del documento (DOM). Comenzar con un documento limpio garantiza que el rectángulo que añadas no interfiera con contenido existente.

## Paso 2 – Definir la forma rectangular

Ahora veremos **cómo crear una forma** rectangular. El constructor `Shape` recibe el documento propietario y el tipo de forma. También establecemos su ancho y alto en puntos (1 pt ≈ 1/72 in).

```csharp
// Create a rectangle shape
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width = 200;   // 200 pt ≈ 2.78 in
rectangleShape.Height = 100; // 100 pt ≈ 1.39 in
```

Podrías preguntarte, “¿Puedo usar centímetros en lugar de puntos?” La API solo acepta puntos, pero puedes convertir: `points = centimeters * 28.35`. Esta pequeña conversión es útil cuando alineas formas con los márgenes de la página.

## Paso 3 – Añadir una sombra externa y establecer transparencia

Aquí es donde ocurre la magia: **cómo añadir sombra** y **cómo establecer transparencia** en esa sombra. La propiedad `ShadowFormat` te brinda control total.

```csharp
// Enable shadow visibility
rectangleShape.ShadowFormat.Visible = true;

// Choose a shadow color
rectangleShape.ShadowFormat.Color = System.Drawing.Color.DarkGray;

// Set transparency (0 = opaque, 1 = fully transparent)
rectangleShape.ShadowFormat.Transparency = 0.3; // 30 % transparent

// Position the shadow relative to the shape
rectangleShape.ShadowFormat.OffsetX = 5; // horizontal offset in points
rectangleShape.ShadowFormat.OffsetY = 5; // vertical offset in points

// Blur makes the shadow look softer
rectangleShape.ShadowFormat.BlurRadius = 4;

// Specify that this is an outer shadow (instead of inner)
rectangleShape.ShadowFormat.Style = ShadowStyle.OuterShadow;
```

**¿Por qué estos ajustes?**  
- **Transparency** permite que la textura subyacente de la página se vea, evitando que la sombra parezca demasiado pesada.  
- **OffsetX/Y** crean la ilusión de que la forma está levantada de la página.  
- **BlurRadius** suaviza los bordes—sin él la sombra sería un rectángulo duro, lo que se ve antinatural.  

Si necesitas un efecto más dramático, aumenta `OffsetX/Y` a 10 y `BlurRadius` a 8. Por el contrario, para una pista sutil, mantenlos en 2 y 2 respectivamente.

## Paso 4 – Insertar la forma en el documento

Ahora **añadimos la forma rectangular** al primer párrafo del documento. Si el documento no tiene contenido, `FirstParagraph` se crea automáticamente para ti.

```csharp
// Append the rectangle to the first paragraph
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

¿Qué pasa si deseas la forma dentro de una celda de tabla específica o en un párrafo posterior? Simplemente localiza ese nodo (`doc.GetChild(NodeType.Paragraph, index, true)`) y llama a `AppendChild` sobre él. El mismo objeto `Shape` puede clonarse si necesitas varias copias.

## Paso 5 – Guardar el documento

Finalmente, **creamos el documento de Word** en disco. Usa una ruta que se ajuste a tu entorno; el ejemplo utiliza un marcador de posición.

```csharp
// Save the document as a .docx file
document.Save(@"YOUR_DIRECTORY/Shadow.docx");
```

Al abrir `Shadow.docx` en Microsoft Word, verás un rectángulo gris claro con una sombra externa suave desplazada hacia la esquina inferior derecha. La transparencia del 30 % de la sombra asegura que no domine la página.

---

![Create word document with a shadowed rectangle shape](image.png "Create word document with a shadowed rectangle")

*Texto alternativo de la imagen: crear documento de Word con una forma rectangular sombreada*

## Código completo, listo para ejecutar

A continuación tienes el programa completo que puedes copiar y pegar en una aplicación de consola. Sin piezas faltantes, sin “ver documentación para más”.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Step 2: Add a rectangular shape and define its size
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width = 200;   // width in points
        rectangleShape.Height = 100;  // height in points

        // Step 3: Configure an outer shadow for the shape
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = System.Drawing.Color.DarkGray;
        rectangleShape.ShadowFormat.Transparency = 0.3;   // 30 % transparent
        rectangleShape.ShadowFormat.OffsetX = 5;          // horizontal offset
        rectangleShape.ShadowFormat.OffsetY = 5;          // vertical offset
        rectangleShape.ShadowFormat.BlurRadius = 4;
        rectangleShape.ShadowFormat.Style = ShadowStyle.OuterShadow;

        // Step 4: Insert the shape into the first paragraph of the document
        document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

        // Step 5: Save the document with the shadowed shape
        document.Save(@"YOUR_DIRECTORY/Shadow.docx");

        Console.WriteLine("Word document created successfully at YOUR_DIRECTORY/Shadow.docx");
    }
}
```

### Resultado esperado

- Aparece un archivo llamado **Shadow.docx** en la carpeta de destino.  
- Al abrirlo en Word se muestra un rectángulo (200 × 100 pt) con una sombra externa gris oscuro.  
- La sombra está desplazada 5 pt horizontal y verticalmente, difuminada y con un 30 % de transparencia.

## Preguntas frecuentes y casos límite

| Pregunta | Respuesta |
|----------|-----------|
| **¿Puedo cambiar el color de la sombra para que coincida con mi marca?** | Por supuesto—simplemente reemplaza `System.Drawing.Color.DarkGray` por cualquier `Color` que prefieras, por ejemplo `Color.FromArgb(255, 0, 120, 215)` para un acento azul. |
| **¿Qué pasa si necesito una sombra interna en lugar de externa?** | Establece `ShadowFormat.Style = ShadowStyle.InnerShadow`. El resto de las propiedades se comportan igual. |
| **¿La transparencia es compatible con versiones antiguas de Word?** | Sí. Aspose.Words escribe el XML apropiado que Word 2007+ entiende. Las versiones más antiguas pueden ignorar el valor de transparencia pero aún mostrarán la sombra. |
| **¿Puedo añadir varias formas con sombras diferentes?** | Claro—solo crea nuevas instancias de `Shape`, configura cada sombra de forma independiente y añádelas a los nodos deseados. |
| **¿Qué pasa con el rendimiento al manejar cientos de formas?** | Crear muchas formas puede aumentar el uso de memoria. Reutiliza una única instancia de `Document` y agrega las formas dentro de un bucle; libera los objetos temporales si encuentras presión de recursos. |

## Consejos para proyectos del mundo real

- **Generación por lotes:** Cuando generes informes para muchos usuarios, instancia una única plantilla `Document` y clónala para cada iteración. Sustituye marcadores de posición antes de añadir formas.  
- **Tamaño dinámico:** Usa las dimensiones de la página (`document.FirstSection.PageSetup.PageWidth`) para calcular el tamaño de la forma relativo a la página, garantizando un diseño consistente en diferentes tamaños de papel.  
- **Pruebas:** Siempre abre el `.docx` generado en Word después de cambiar los parámetros de la sombra. La retroalimentación visual es más rápida que adivinar números.

## Próximos pasos

Ahora que sabes **cómo añadir una forma rectangular**, **cómo añadir sombra** y **cómo establecer transparencia**, considera explorar:

- Añadir **rellenos degradados** a las formas (`Shape.FillFormat`).  
- Incrustar **imágenes** dentro de formas para efectos de marca de agua.  
- Usar **tablas** para alinear múltiples formas sombreadas en una cuadrícula.  
- Exportar el mismo documento a PDF (`document.Save("output.pdf")`) manteniendo las sombras.

Cada uno de estos se basa en los mismos conceptos centrales, por lo que te sentirás cómodo ampliando el código.

---

### Recapitulación

Comenzamos **creando un documento de Word** con Aspose.Words, luego **creamos una forma rectangular**, aplicamos **una sombra externa**, ajustamos **la transparencia**, y guardamos el resultado. Todo el proceso encaja en un patrón compacto y reutilizable que puedes adaptar a cualquier escenario de automatización.

Siéntete libre de experimentar—cambia colores, juega con los desplazamientos o apila varias formas juntas. Cuando encuentres un obstáculo, vuelve a consultar las secciones anteriores; están diseñadas como referencia rápida. ¡Feliz codificación, y que tus documentos siempre luzcan pulidos!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}