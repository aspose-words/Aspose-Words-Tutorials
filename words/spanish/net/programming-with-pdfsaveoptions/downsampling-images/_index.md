---
title: Reducir el tamaño de un documento PDF con reducción de resolución de imágenes
linktitle: Reducir el tamaño de un documento PDF con reducción de resolución de imágenes
second_title: API de procesamiento de documentos Aspose.Words
description: Reduzca el tamaño de los documentos PDF reduciendo el tamaño de las imágenes con Aspose.Words para .NET. Optimice sus archivos PDF para tiempos de carga y descarga más rápidos.
weight: 10
url: /es/net/programming-with-pdfsaveoptions/downsampling-images/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Reducir el tamaño de un documento PDF con reducción de resolución de imágenes

## Introducción

Los archivos PDF son un elemento básico en el mundo digital y se utilizan para todo, desde compartir documentos hasta crear libros electrónicos. Sin embargo, su tamaño a veces puede ser un obstáculo, especialmente cuando se trata de contenido rico en imágenes. Aquí es donde entra en juego la reducción de resolución de las imágenes. Al reducir la resolución de las imágenes dentro del PDF, puede disminuir significativamente el tamaño del archivo sin comprometer demasiado la calidad. En este tutorial, repasaremos los pasos para lograrlo utilizando Aspose.Words para .NET.

## Prerrequisitos

Antes de pasar al código, asegurémonos de que tienes todo lo que necesitas:

1.  Aspose.Words para .NET: Asegúrese de tener instalada la biblioteca Aspose.Words. Si no es así, puede descargarla[aquí](https://releases.aspose.com/words/net/).
2. Entorno de desarrollo: cualquier entorno de desarrollo .NET como Visual Studio.
3. Conocimientos básicos de C#: será útil comprender los conceptos básicos de la programación en C#.
4.  Un documento de muestra: un documento de Word (por ejemplo,`Rendering.docx`) con imágenes para convertir a PDF.

## Importar espacios de nombres

Lo primero es lo primero: debes importar los espacios de nombres necesarios. Añádelos en la parte superior del archivo de código:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Ahora, dividamos el proceso en pasos manejables.

## Paso 1: Cargue el documento

El primer paso es cargar el documento de Word. Aquí es donde se especifica la ruta al directorio del documento.

```csharp
// La ruta al directorio de documentos.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

En este paso, cargamos el documento de Word desde el directorio especificado. Asegúrese de reemplazar`"YOUR DOCUMENT DIRECTORY"` con la ruta real donde se encuentra su documento.

## Paso 2: Configurar las opciones de submuestreo

A continuación, debemos configurar las opciones de reducción de resolución. Esto implica configurar la resolución y el umbral de resolución de las imágenes.

```csharp
// Podemos establecer un umbral mínimo para el submuestreo.
// Este valor evitará que se remuestree menos la segunda imagen del documento de entrada.
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    DownsampleOptions = { Resolution = 36, ResolutionThreshold = 128 }
};
```

 Aquí, estamos creando una nueva instancia de`PdfSaveOptions` y estableciendo el`Resolution` a 36 DPI y el`ResolutionThreshold` a 128 DPI. Esto significa que cualquier imagen con una resolución superior a 128 DPI se reducirá a 36 DPI.

## Paso 3: Guardar el documento como PDF

Por último, guardamos el documento como PDF con las opciones configuradas.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.DownsamplingImages.pdf", saveOptions);
```

En este paso final, guardaremos el documento como PDF en el mismo directorio con las opciones de reducción de resolución especificadas.

## Conclusión

¡Y ya lo tienes! Has logrado reducir el tamaño de tu PDF reduciendo el tamaño de las imágenes con Aspose.Words para .NET. Esto no solo hace que tus PDF sean más manejables, sino que también ayuda a que las cargas y descargas sean más rápidas y las experiencias de visualización sean más fluidas.

## Preguntas frecuentes

### ¿Qué es el downsampling?
La reducción de resolución es el proceso de reducir la resolución de las imágenes, lo que ayuda a disminuir el tamaño de archivo de los documentos que contienen esas imágenes.

### ¿La disminución de resolución afectará la calidad de las imágenes?
Sí, la reducción de resolución reducirá la calidad de la imagen. Sin embargo, el impacto depende del grado de reducción de la resolución. Es un equilibrio entre el tamaño del archivo y la calidad de la imagen.

### ¿Puedo elegir qué imágenes quiero reducir de resolución?
 Sí, configurando el`ResolutionThreshold`, puedes controlar qué imágenes se reducen en función de su resolución original.

### ¿Cuál es la resolución ideal para el submuestreo?
La resolución ideal depende de tus necesidades específicas. Normalmente, se utilizan 72 DPI para imágenes web, mientras que para la calidad de impresión se utilizan resoluciones más altas.

### ¿Aspose.Words para .NET es gratuito?
 Aspose.Words para .NET es un producto comercial, pero puedes descargar una versión de prueba gratuita[aquí](https://releases.aspose.com/) o solicitar una[licencia temporal](https://purchase.aspose.com/temporary-license/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
