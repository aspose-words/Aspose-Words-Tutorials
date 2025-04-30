---
"description": "Reduce el tamaño de tus PDF desactivando las fuentes incrustadas con Aspose.Words para .NET. Sigue nuestra guía paso a paso para optimizar tus documentos y optimizar su almacenamiento y uso compartido."
"linktitle": "Reducir el tamaño del PDF deshabilitando las fuentes incrustadas"
"second_title": "API de procesamiento de documentos de Aspose.Words"
"title": "Reducir el tamaño del PDF deshabilitando las fuentes incrustadas"
"url": "/es/net/programming-with-pdfsaveoptions/disable-embed-windows-fonts/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Reducir el tamaño del PDF deshabilitando las fuentes incrustadas

## Introducción

Reducir el tamaño de los archivos PDF puede ser crucial para un almacenamiento eficiente y un uso compartido rápido. Una forma eficaz de hacerlo es deshabilitar las fuentes incrustadas, especialmente cuando las fuentes estándar ya están disponibles en la mayoría de los sistemas. En este tutorial, exploraremos cómo reducir el tamaño de un PDF deshabilitando las fuentes incrustadas con Aspose.Words para .NET. Le guiaremos paso a paso para que pueda implementarlo fácilmente en sus proyectos.

## Prerrequisitos

Antes de sumergirse en el código, asegúrese de tener lo siguiente:

- Aspose.Words para .NET: Si aún no lo ha hecho, descárguelo e instálelo desde [Enlace de descarga](https://releases.aspose.com/words/net/).
- Un entorno de desarrollo .NET: Visual Studio es una opción popular.
- Un documento de Word de muestra: tenga listo un archivo DOCX que desee convertir a PDF.

## Importar espacios de nombres

Para comenzar, asegúrese de haber importado los espacios de nombres necesarios a su proyecto. Esto le permitirá acceder a las clases y métodos necesarios para nuestra tarea.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Desglosemos el proceso en pasos sencillos y manejables. Cada paso te guiará a través de la tarea, asegurándote de que comprendes lo que sucede en cada momento.

## Paso 1: Inicialice su documento

Primero, necesitamos cargar el documento de Word que quieres convertir a PDF. Aquí es donde empieza el proceso.

```csharp
// La ruta al directorio de documentos.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

Aquí, `dataDir` es un marcador de posición para el directorio donde se encuentra su documento. Reemplazar `"YOUR DOCUMENT DIRECTORY"` con la ruta actual.

## Paso 2: Configurar las opciones de guardado de PDF

A continuación, configuraremos las opciones de guardado del PDF. Aquí especificamos que no queremos incrustar las fuentes estándar de Windows.

```csharp
// El PDF de salida se guardará sin incrustar fuentes estándar de Windows.
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    FontEmbeddingMode = PdfFontEmbeddingMode.EmbedNone
};
```

Mediante la configuración `FontEmbeddingMode` a `EmbedNone`Le indicamos a Aspose.Words que no incluya estas fuentes en el PDF, reduciendo así el tamaño del archivo.

## Paso 3: Guardar el documento como PDF

Finalmente, guardamos el documento como PDF con las opciones de guardado configuradas. Este es el momento clave: tu DOCX se transforma en un PDF compacto.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.DisableEmbedWindowsFonts.pdf", saveOptions);
```

Reemplazar `"YOUR DOCUMENT DIRECTORY"` Con la ruta de directorio actual nuevamente. El PDF de salida se guardará en el directorio especificado sin fuentes estándar incrustadas.

## Conclusión

Siguiendo estos pasos, puede reducir significativamente el tamaño de sus archivos PDF. Deshabilitar las fuentes incrustadas es una forma sencilla y eficaz de reducir el tamaño de sus documentos y facilitar su uso compartido. Aspose.Words para .NET simplifica este proceso, garantizando la optimización de sus archivos con el mínimo esfuerzo.

## Preguntas frecuentes

### ¿Por qué debería desactivar las fuentes incrustadas en un PDF?
Deshabilitar las fuentes incrustadas puede reducir significativamente el tamaño del archivo PDF, lo que lo hace más eficiente para almacenar y más rápido para compartir.

### ¿El PDF se seguirá mostrando correctamente sin fuentes incrustadas?
Sí, siempre que las fuentes sean estándar y estén disponibles en el sistema donde se visualiza el PDF, se mostrará correctamente.

### ¿Puedo incrustar selectivamente sólo determinadas fuentes en un PDF?
Sí, Aspose.Words para .NET le permite personalizar qué fuentes se incorporan, lo que proporciona flexibilidad en la forma de reducir el tamaño del archivo.

### ¿Necesito Aspose.Words para .NET para deshabilitar las fuentes incrustadas en archivos PDF?
Sí, Aspose.Words para .NET proporciona la funcionalidad necesaria para configurar las opciones de incrustación de fuentes en archivos PDF.

### ¿Cómo puedo obtener ayuda si encuentro problemas?
Puedes visitar el [Foro de soporte](https://forum.aspose.com/c/words/8) para obtener ayuda con cualquier problema que encuentre.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}