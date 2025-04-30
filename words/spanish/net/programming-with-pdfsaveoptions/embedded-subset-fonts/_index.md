---
"description": "Reduce el tamaño de tus archivos PDF incrustando solo los subconjuntos de fuentes necesarios con Aspose.Words para .NET. Sigue nuestra guía paso a paso para optimizar tus archivos PDF de forma eficiente."
"linktitle": "Incrustar subconjuntos de fuentes en un documento PDF"
"second_title": "API de procesamiento de documentos de Aspose.Words"
"title": "Incrustar subconjuntos de fuentes en un documento PDF"
"url": "/es/net/programming-with-pdfsaveoptions/embedded-subset-fonts/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Incrustar subconjuntos de fuentes en un documento PDF

## Introducción

¿Has notado que algunos archivos PDF son mucho más grandes que otros, incluso con contenido similar? El problema suele estar en las fuentes. Incrustar fuentes en un PDF garantiza que se vea igual en cualquier dispositivo, pero también puede aumentar el tamaño del archivo. Por suerte, Aspose.Words para .NET ofrece una práctica función para incrustar solo los subconjuntos de fuentes necesarios, manteniendo tus PDF optimizados y eficientes. Este tutorial te guiará paso a paso en el proceso.

## Prerrequisitos

Antes de comenzar, asegúrese de tener lo siguiente:

- Aspose.Words para .NET: Puedes descargarlo [aquí](https://releases.aspose.com/words/net/).
- Entorno .NET: asegúrese de tener un entorno de desarrollo .NET en funcionamiento.
- Conocimientos básicos de C#: Estar familiarizado con la programación en C# le ayudará a seguir adelante.

## Importar espacios de nombres

Para usar Aspose.Words para .NET, debe importar los espacios de nombres necesarios en su proyecto. Añádalos al principio de su archivo de C#:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Paso 1: Cargar el documento

Primero, necesitamos cargar el documento de Word que queremos convertir a PDF. Esto se hace usando el `Document` clase proporcionada por Aspose.Words.

```csharp
// La ruta al directorio de documentos.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

Este fragmento de código carga el documento ubicado en `dataDir`Asegúrese de reemplazar `"YOUR DOCUMENT DIRECTORY"` con la ruta real a su documento.

## Paso 2: Configurar las opciones de guardado de PDF

A continuación, configuramos el `PdfSaveOptions` para garantizar que solo se incrusten los subconjuntos de fuentes necesarios. Al configurar `EmbedFullFonts` a `false`Le indicamos a Aspose.Words que incruste solo los glifos utilizados en el documento.

```csharp
// El PDF de salida contendrá subconjuntos de las fuentes del documento.
// En las fuentes PDF sólo se incluyen los glifos utilizados en el documento.
PdfSaveOptions saveOptions = new PdfSaveOptions { EmbedFullFonts = false };
```

Este pequeño pero crucial paso ayuda a reducir significativamente el tamaño del archivo PDF.

## Paso 3: Guardar el documento como PDF

Finalmente, guardamos el documento como PDF usando el `Save` método, aplicando el configurado `PdfSaveOptions`.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.EmbedSubsetFonts.pdf", saveOptions);
```

Este código generará un archivo PDF con el nombre `WorkingWithPdfSaveOptions.EmbedSubsetFonts.pdf` en el directorio especificado, con solo los subconjuntos de fuentes necesarios integrados.

## Conclusión

¡Listo! Siguiendo estos sencillos pasos, puedes reducir eficazmente el tamaño de tus archivos PDF incrustando solo los subconjuntos de fuentes necesarios con Aspose.Words para .NET. Esto no solo ahorra espacio de almacenamiento, sino que también garantiza tiempos de carga más rápidos y un mejor rendimiento, especialmente para documentos con muchas fuentes.

## Preguntas frecuentes

### ¿Por qué debería incrustar sólo subconjuntos de fuentes en un PDF?
Incrustar solo los subconjuntos de fuentes necesarios puede reducir significativamente el tamaño del archivo PDF sin comprometer la apariencia ni la legibilidad del documento.

### ¿Puedo volver a incrustar fuentes completas si es necesario?
Sí, puedes. Simplemente configura el `EmbedFullFonts` propiedad a `true` en el `PdfSaveOptions`.

### ¿Aspose.Words para .NET admite otras funciones de optimización de PDF?
¡Por supuesto! Aspose.Words para .NET ofrece diversas opciones para optimizar archivos PDF, como la compresión de imágenes y la eliminación de objetos no utilizados.

### ¿Qué tipos de fuentes se pueden incrustar en subconjuntos utilizando Aspose.Words para .NET?
Aspose.Words para .NET admite la incrustación de subconjuntos para todas las fuentes TrueType utilizadas en el documento.

### ¿Cómo puedo verificar qué fuentes están incrustadas en mi PDF?
Puede abrir el PDF en Adobe Acrobat Reader y verificar las propiedades en la pestaña Fuentes para ver las fuentes incorporadas.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}