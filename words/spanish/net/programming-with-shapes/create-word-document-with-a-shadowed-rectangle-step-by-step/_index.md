---
category: general
date: 2026-01-13
description: Crear un documento de Word usando Aspose.Words y aprender cómo insertar
  una forma rectangular, cómo agregar sombra y añadir sombra a la forma en C#. Ejemplo
  completo incluido.
draft: false
keywords:
- create word document
- insert rectangle shape
- how to add shadow
- how to insert shape
- add shape shadow
language: es
og_description: Crea un documento de Word con Aspose.Words, descubre cómo insertar
  una forma rectangular y cómo agregar sombra. Sigue el ejemplo completo en C#.
og_title: Crear documento de Word con un rectángulo sombreado – tutorial completo
tags:
- Aspose.Words
- C#
- Document Automation
title: Crear documento de Word con un rectángulo sombreado – Guía paso a paso
url: /es/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear documento Word con un rectángulo sombreado – Guía paso a paso

¿Alguna vez necesitaste **crear documento word** que contenga un rectángulo con sombra agradable, pero no sabías por dónde empezar? No eres el único: muchos desarrolladores se topan con el mismo obstáculo cuando empiezan a trabajar con Aspose.Words.  

En este tutorial recorreremos todo lo que necesitas para **crear documento word** de forma programática, **insertar forma de rectángulo**, y mostrar **cómo añadir sombra** para que la forma realmente destaque. Al final tendrás un fragmento de C# listo para ejecutar que puedes incorporar en cualquier proyecto .NET.

## Lo que aprenderás

- El código exacto para **cómo insertar forma** (un rectángulo) en un archivo Word.  
- Las propiedades que debes ajustar para **añadir sombra a la forma** y controlar su apariencia.  
- Cómo guardar el resultado y verificar que la sombra sea visible.  
- Algunos consejos prácticos y notas sobre casos límite que te ahorrarán dolores de cabeza más adelante.

No se necesita documentación externa: todo está aquí.

## Requisitos previos

Antes de sumergirnos, asegúrate de contar con:

1. **.NET 6.0** (o cualquier versión reciente de .NET) instalado.  
2. Una **licencia** de Aspose.Words para .NET, o puedes usar el modo de evaluación gratuito para pruebas.  
3. Un entorno de desarrollo—Visual Studio 2022 funciona muy bien, pero cualquier editor que pueda compilar C# servirá.

Eso es todo. No se requieren paquetes NuGet adicionales más allá de `Aspose.Words`.

## Paso 1 – Configurar el proyecto y referenciar Aspose.Words

Primero, crea una nueva aplicación de consola y agrega el paquete Aspose.Words:

```bash
dotnet new console -n ShadowRectangleDemo
cd ShadowRectangleDemo
dotnet add package Aspose.Words
```

> **Consejo profesional:** Si estás usando la versión de prueba gratuita, recuerda llamar a `License.SetLicense` con tu archivo de licencia; de lo contrario la biblioteca añadirá una marca de agua.

## Paso 2 – Inicializar el Document Builder

Ahora comenzaremos el proceso real de **crear documento word**. La clase `Document` nos brinda un lienzo en blanco, y `DocumentBuilder` nos permite pintar sobre él.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing; // For Color

// Initialise a new blank document
Document document = new Document();

// Initialise a builder to start adding content
DocumentBuilder builder = new DocumentBuilder(document);
```

¿Por qué necesitamos un builder? Abstracta los detalles de bajo nivel de OpenXML, de modo que puedas concentrarte en *qué* quieres en lugar de *cómo* está estructurado el archivo. Este es el núcleo de **cómo insertar forma** rápidamente.

## Paso 3 – Insertar forma de rectángulo

Aquí es donde realmente **insertamos forma de rectángulo**. El rectángulo medirá 150 × 100 puntos (aproximadamente 2 pulg × 1.3 pulg).

```csharp
// Insert a rectangle shape at the current cursor position
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 100);
```

El método `InsertShape` devuelve un objeto `Shape`, que podemos personalizar aún más. En este punto, el rectángulo es solo una caja blanca sólida—todavía sin sombra.

## Paso 4 – Cómo añadir sombra (Añadir sombra a la forma)

Añadir una sombra es sorprendentemente sencillo una vez que sabes qué propiedades tocar. El objeto `ShadowFormat` controla la visibilidad, color, desenfoque, desplazamiento y tamaño.

```csharp
// Make the shadow visible
rectangleShape.ShadowFormat.Visible = true;

// Choose a subtle gray tone
rectangleShape.ShadowFormat.Color = Color.Gray;

// Set 30 % transparency – the shadow will be faint but noticeable
rectangleShape.ShadowFormat.Transparency = 0.3;

// Offset the shadow 5 points right and 5 points down
rectangleShape.ShadowFormat.OffsetX = 5;
rectangleShape.ShadowFormat.OffsetY = 5;

// Soften the edges with a blur radius of 4 points
rectangleShape.ShadowFormat.BlurRadius = 4;

// Scale the shadow to 75 % of the shape size (percentage)
rectangleShape.ShadowFormat.Size = 75;
```

Ese bloque responde **cómo añadir sombra** en lenguaje sencillo: actívala, elige un color, ajusta la transparencia, el desplazamiento, el desenfoque y el tamaño. Puedes experimentar con estos valores para obtener una sombra pesada o una sombra sutil.

### Variaciones comunes

- **Colores diferentes:** Usa `Color.Black` para una sombra clásica, o `Color.BlueViolet` para un efecto estilizado.  
- **Sin desenfoque:** Establece `BlurRadius = 0` para un borde nítido y definido.  
- **Desplazamientos mayores:** Incrementa `OffsetX`/`OffsetY` para alejar más la sombra de la forma.

## Paso 5 – Guardar el documento y verificar

Finalmente, escribe el documento en disco. El archivo será un `.docx` estándar que cualquier procesador de Word moderno puede abrir.

```csharp
// Save the document to the desired folder
string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowRectangle.docx");
document.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

Abre el *ShadowRectangle.docx* resultante en Microsoft Word. Deberías ver un rectángulo con una sombra gris suave desplazada hacia la esquina inferior derecha—exactamente lo que especificó el código.

> **Salida esperada:** Un archivo Word de una sola página que contiene un rectángulo de 150 × 100 puntos con una sombra gris 30 % transparente, desplazada 5 pts, desenfocada 4 pts y con un tamaño del 75 % de la forma.

## Ejemplo completo y funcional

Juntando todo, aquí tienes el programa completo, listo para ejecutar:

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialise a new blank document
        Document document = new Document();

        // 2️⃣ Create a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Insert a rectangle shape (150 × 100 points)
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 100);

        // 4️⃣ How to add shadow – configure the ShadowFormat
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = Color.Gray;
        rectangleShape.ShadowFormat.Transparency = 0.3; // 30 % transparent
        rectangleShape.ShadowFormat.OffsetX = 5;        // horizontal offset
        rectangleShape.ShadowFormat.OffsetY = 5;        // vertical offset
        rectangleShape.ShadowFormat.BlurRadius = 4;    // softer edge
        rectangleShape.ShadowFormat.Size = 75;         // size as a percentage

        // 5️⃣ Save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowRectangle.docx");
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Ejecuta el programa (`dotnet run`) y tendrás un nuevo archivo Word con un rectángulo agradablemente sombreado—perfecto para informes, certificados o cualquier indicación visual que necesites.

## Preguntas frecuentes (FAQs)

**P: ¿Puedo insertar otras formas (elipse, estrella) y seguir usando el mismo código de sombra?**  
R: Absolutamente. El método `InsertShape` acepta cualquier valor del enum `ShapeType`. Una vez que tienes una instancia de `Shape`, las propiedades de `ShadowFormat` funcionan idénticamente, por lo que **cómo añadir sombra** es independiente de la forma.

**P: ¿Qué pasa si necesito la sombra en ambos lados de la forma?**  
R: Aspose.Words solo admite una sombra de caída por forma. Para simular un efecto de doble sombra, duplica la forma, desplaza cada copia de manera diferente y establece `ShadowFormat.Visible` en `false` para una mientras mantienes la sombra visible en la otra.

**P: ¿Esto funciona en .NET Framework 4.8?**  
R: Sí. La API es independiente de la versión; solo debes referenciar el DLL de Aspose.Words correspondiente a tu framework objetivo.

## Consejos y trampas

- **No olvides establecer `Visible = true`**—las propiedades de sombra se ignoran de lo contrario.  
- **Los valores de transparencia van de 0.0 (opaco) a 1.0 (totalmente transparente).** Un error común es usar `30` en lugar de `0.3`.  
- **Guardar en una carpeta de solo lectura lanza una excepción.** Asegúrate de que el directorio de salida tenga permisos de escritura.

## Próximos pasos

Ahora que sabes **cómo insertar forma**, **añadir sombra a la forma**, y **crear documento word** con Aspose.Words, podrías explorar:

- Añadir **texto dentro del rectángulo** usando `builder.InsertParagraph()` antes de insertar la forma.  
- Aplicar **rellenos degradados** o **bordes con patrones** para un estilo visual más rico.  
- Automatizar la generación de múltiples páginas, cada una con una forma sombreada diferente, para crear informes dinámicos.

Siéntete libre de experimentar—cambiar el color, el desenfoque o el tamaño de la sombra puede alterar drásticamente el aspecto de tu documento.

---

*¿Listo para llevar esto a producción? Toma el código, ajusta los parámetros y observa cómo tus archivos Word adquieren un acabado profesional en segundos.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}