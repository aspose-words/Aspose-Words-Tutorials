---
category: general
date: 2026-10-10
description: Crea un documento de Word en blanco, inserta una imagen en Word, agrega
  un grupo de imágenes y oculta la forma en el archivo guardado. Sigue esta guía paso
  a paso.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert image into word
- add image group
- hide shape word document
language: es
lastmod: 2026-10-10
og_description: Crea un documento de Word en blanco, inserta una imagen en Word, agrega
  un grupo de imágenes y oculta la forma. Esta guía muestra el código completo en
  C#.
og_image_alt: Screenshot of a blank Word document with a hidden image group
og_title: Crear un documento de Word en blanco, agregar un grupo de imágenes, ocultar
  la forma
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Create a blank Word document, insert image into Word, add an image
    group, and hide shape in the saved file. Follow this step‑by‑step guide.
  headline: Create a blank Word document, add an image group, hide shape
  type: TechArticle
tags:
- Word automation
- Aspose.Words
- C#
- Document processing
title: Crear un documento de Word en blanco, añadir un grupo de imágenes, ocultar
  la forma
url: /es/java/images-shapes/create-a-blank-word-document-add-an-image-group-hide-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear un documento Word en blanco, agregar un grupo de imágenes, ocultar forma

Si necesitas **crear un documento Word en blanco** y luego ocultar elementos visuales, este tutorial te muestra exactamente cómo hacerlo. Aprenderás a insertar una imagen en Word, agregar un grupo de imágenes y ocultar la forma en un documento Word mediante una rutina reutilizable en C#.

Usaremos la biblioteca Aspose.Words para .NET, que permite manipular archivos .docx sin necesidad de tener Microsoft Word instalado. Al final de esta guía tendrás un programa ejecutable que genera un archivo Word que contiene un grupo de imágenes oculto, listo para procesamiento posterior o visualización condicional.

## Requisitos previos

- .NET 6.0 o posterior (el código también funciona con .NET Framework 4.6+)
- Paquete NuGet Aspose.Words para .NET (`Install-Package Aspose.Words`)
- Una carpeta en disco donde puedas leer un archivo de imagen y escribir el documento de salida
- Familiaridad básica con C# y Visual Studio (o cualquier IDE que prefieras)

## Crear un documento Word en blanco con Aspose.Words

El primer paso es **crear un documento Word en blanco**. Aspose.Words proporciona la clase `Document` que representa un archivo Word en memoria. Instanciarla sin argumentos te da un documento vacío listo para recibir contenido.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document doc = new Document();                 // blank .docx container
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Por qué es importante:* Comenzar con un documento en blanco garantiza que no haya formato oculto ni secciones residuales que interfieran con la forma que agregarás después.

## Insertar imagen en Word usando DocumentBuilder

A continuación, **insertamos una imagen en Word** creando primero una forma de grupo que contendrá la foto. Las formas de grupo te permiten tratar varios objetos de dibujo como una única unidad, lo cual es útil cuando luego deseas ocultarlos o moverlos juntos.

```csharp
        // Step 2: Insert a group shape with the desired size (width: 300, height: 200)
        GroupShape group = builder.InsertGroupShape(300, 200);
```

El método `InsertGroupShape` crea un contenedor vacío. Las dimensiones están en puntos (1 punto = 1/72 de pulgada). Ajusta el tamaño para que coincida con la resolución de la imagen que planeas incrustar.

## Agregar grupo de imágenes al documento

Ahora **agregamos el grupo de imágenes** moviendo el cursor del builder dentro del grupo recién creado e insertando la foto. Todas las inserciones posteriores formarán parte del grupo.

```csharp
        // Step 3: Position the builder inside the group so subsequent inserts go into it
        builder.MoveTo(group);

        // Step 4: Add an image to the group shape
        // Replace the path with the actual location of your PNG/JPEG file
        builder.InsertImage(@"YOUR_DIRECTORY\photo1.png");
```

*Consejo:* Usa una ruta absoluta o una ruta relativa correctamente escapada; de lo contrario `InsertImage` lanzará una `FileNotFoundException`.

## Ocultar forma en un documento Word

Finalmente, **ocultamos la forma en el documento Word** estableciendo la propiedad `Hidden` del grupo a `true`. Las formas ocultas no se muestran cuando el documento se abre en Word, pero permanecen en el archivo y pueden revelarse programáticamente más tarde.

```csharp
        // Step 5: Hide the entire group (the image will not be visible in the saved document)
        group.Hidden = true;

        // Step 6: Save the document with the hidden group
        doc.Save(@"YOUR_DIRECTORY\GroupHidden.docx");
    }
}
```

Cuando abras *GroupHidden.docx* en Microsoft Word, verás una página completamente en blanco porque el grupo de imágenes está oculto. El archivo sigue conteniendo los datos de la imagen, que puedes volver a mostrar más adelante con `group.Hidden = false` si lo necesitas.

## Ejemplo completo y ejecutable

A continuación tienes el programa completo que puedes copiar y pegar en un nuevo proyecto de consola:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a blank Word document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a group shape (300 pt × 200 pt)
            GroupShape group = builder.InsertGroupShape(300, 200);

            // 3️⃣ Move inside the group so inserts become part of it
            builder.MoveTo(group);

            // 4️⃣ Insert the image (replace with your own file)
            builder.InsertImage(@"YOUR_DIRECTORY\photo1.png");

            // 5️⃣ Hide the group so the image is not shown
            group.Hidden = true;

            // 6️⃣ Save the result
            doc.Save(@"YOUR_DIRECTORY\GroupHidden.docx");

            Console.WriteLine("Document created successfully.");
        }
    }
}
```

**Salida esperada**

- Aparece un archivo llamado `GroupHidden.docx` en `YOUR_DIRECTORY`.
- Al abrir el archivo en Word se muestra una página vacía.
- La imagen oculta puede revelarse cambiando `group.Hidden = false` y volviendo a guardar.

## Variaciones comunes y casos límite

| Situación | Cómo adaptar el código |
|-----------|------------------------|
| **Múltiples imágenes** | Inserta llamadas adicionales a `InsertImage` después de `builder.MoveTo(group)`. Todas las imágenes permanecen dentro del mismo grupo y comparten la bandera de ocultación. |
| **Diferentes formatos de imagen** | Aspose.Words soporta PNG, JPEG, BMP, GIF, TIFF. Simplemente cambia la extensión del archivo; no se necesita modificar el código. |
| **Visibilidad condicional** | Almacena una variable personalizada del documento (`doc.Variables.Add("ShowImages", "true")`) y alterna `group.Hidden` según su valor en tiempo de ejecución. |
| **Documentos grandes** | Crea el grupo en una página específica (`builder.InsertBreak(BreakType.PageBreak)`) antes de insertar el grupo para evitar desplazamientos de diseño. |
| **Compatibilidad con versiones antiguas de Word** | Guarda como `doc.Save("output.doc", SaveFormat.Doc)` si necesitas el formato legado `.doc`; las formas ocultas se comportan de la misma manera. |

**Consejo profesional:** Siempre establece `group.Hidden = true` *después* de haber insertado todos los elementos hijos. Cambiar la bandera antes de agregar contenido puede provocar que algunos elementos se rendericen inesperadamente en versiones antiguas de Word.

## Conclusión

Ahora sabes cómo **crear un documento Word en blanco**, **insertar una imagen en Word**, **agregar un grupo de imágenes** y **ocultar una forma en un documento Word** usando Aspose.Words para .NET. El ejemplo completo muestra cada paso, desde la inicialización del documento hasta el guardado de un archivo que contiene un grupo de imágenes oculto.

A continuación, podrías explorar:

- Añadir cuadros de texto o gráficos al mismo grupo
- Usar `DocumentBuilder.StartBookmark` / `EndBookmark` para marcar secciones ocultas
- Alternar la visibilidad programáticamente según la entrada del usuario o variables del documento

¡Siéntete libre de experimentar con diferentes formas, tamaños y reglas de visibilidad para adaptarlas a tu escenario de automatización! ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document with Floating Image in .NET](/words/english/net/add-content-using-documentbuilder/insert-floating-image/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}