---
title: Crear un marcador en un documento de Word
linktitle: Crear un marcador en un documento de Word
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a crear marcadores en documentos de Word con Aspose.Words para .NET con esta guía detallada paso a paso. Perfecta para la navegación y organización de documentos.
weight: 10
url: /es/net/programming-with-bookmarks/create-bookmark/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear un marcador en un documento de Word

## Introducción

Crear marcadores en un documento de Word puede ser un gran cambio, especialmente cuando desea navegar por documentos grandes sin esfuerzo. Hoy, repasaremos el proceso de creación de marcadores con Aspose.Words para .NET. Este tutorial lo guiará paso a paso, asegurándose de que comprenda cada parte del proceso. ¡Así que, vamos directo al grano!

## Prerrequisitos

Antes de comenzar, necesitas tener lo siguiente:

1.  Biblioteca Aspose.Words para .NET: descargar e instalar desde[aquí](https://releases.aspose.com/words/net/).
2. Entorno de desarrollo: Visual Studio o cualquier otro entorno de desarrollo .NET.
3. Conocimientos básicos de C#: comprensión de los conceptos básicos de programación de C#.

## Importar espacios de nombres

Para trabajar con Aspose.Words para .NET, debe importar los espacios de nombres necesarios:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Paso 1: Configurar el documento y DocumentBuilder

Inicializar el documento

Primero, necesitamos crear un nuevo documento e inicializarlo.`DocumentBuilder`Este es el punto de partida para agregar contenido y marcadores a su documento.

```csharp
// La ruta al directorio de documentos.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Explicación: El`Document` El objeto es tu lienzo.`DocumentBuilder` Es como tu bolígrafo, que te permite escribir contenido y crear marcadores en el documento.

## Paso 2: Crea el marcador principal

Iniciar y finalizar el marcador principal

Para crear un marcador, es necesario especificar los puntos de inicio y fin. Aquí, crearemos un marcador llamado "Mi marcador".

```csharp
builder.StartBookmark("My Bookmark");
builder.Writeln("Text inside a bookmark.");
```

 Explicación: El`StartBookmark` El método marca el comienzo del marcador y`Writeln` Agrega texto dentro del marcador.

## Paso 3: Crear un marcador anidado

Agregar un marcador anidado dentro del marcador principal

Puedes anidar marcadores dentro de otros marcadores. Aquí, agregamos "Marcador anidado" dentro de "Mi marcador".

```csharp
builder.StartBookmark("Nested Bookmark");
builder.Writeln("Text inside a NestedBookmark.");
builder.EndBookmark("Nested Bookmark");
```

 Explicación: La anidación de marcadores permite una organización de contenido más estructurada y jerárquica.`EndBookmark` El método cierra el marcador actual.

## Paso 4: Agregar texto fuera del marcador anidado

Continuar añadiendo contenido

Después del marcador anidado, podemos continuar agregando más contenido dentro del marcador principal.

```csharp
builder.Writeln("Text after Nested Bookmark.");
builder.EndBookmark("My Bookmark");
```

Explicación: Esto garantiza que el marcador principal abarque tanto el marcador anidado como el texto adicional.

## Paso 5: Configurar las opciones para guardar PDF

Configurar opciones de guardado de PDF para marcadores

Al guardar el documento como PDF, podemos configurar opciones para incluir marcadores.

```csharp
PdfSaveOptions options = new PdfSaveOptions();
options.OutlineOptions.BookmarksOutlineLevels.Add("My Bookmark", 1);
options.OutlineOptions.BookmarksOutlineLevels.Add("Nested Bookmark", 2);
```

 Explicación: El`PdfSaveOptions` La clase le permite especificar cómo se debe guardar el documento como PDF.`BookmarksOutlineLevels` La propiedad define la jerarquía de los marcadores en el PDF.

## Paso 6: Guardar el documento

Guardar el documento como PDF

Por último, guarde el documento con las opciones especificadas.

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.CreateBookmark.pdf", options);
```

 Explicación: El`Save` El método guarda el documento en el formato y la ubicación especificados. El PDF incluirá ahora los marcadores que creamos.

## Conclusión

Crear marcadores en un documento de Word con Aspose.Words para .NET es sencillo y sumamente útil para la navegación y organización de documentos. Ya sea que esté generando informes, creando libros electrónicos o administrando documentos grandes, los marcadores le facilitan la vida. Siga los pasos que se describen en este tutorial y tendrá un PDF con marcadores listo en poco tiempo.

## Preguntas frecuentes

### ¿Puedo crear varios marcadores en diferentes niveles?

¡Por supuesto! Puedes crear tantos marcadores como necesites y definir sus niveles jerárquicos al guardar el documento como PDF.

### ¿Cómo actualizo el texto de un marcador?

 Puedes navegar hasta el marcador usando`DocumentBuilder.MoveToBookmark` y luego actualizar el texto.

### ¿Es posible eliminar un marcador?

 Sí, puedes eliminar un marcador usando el`Bookmarks.Remove` método especificando el nombre del marcador.

### ¿Puedo crear marcadores en otros formatos además de PDF?

Sí, Aspose.Words admite marcadores en varios formatos, incluidos DOCX, HTML y EPUB.

### ¿Cómo puedo asegurarme de que los marcadores aparezcan correctamente en el PDF?

 Asegúrese de definir el`BookmarksOutlineLevels` apropiadamente en el`PdfSaveOptions`Esto garantiza que los marcadores estén incluidos en el esquema del PDF.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
