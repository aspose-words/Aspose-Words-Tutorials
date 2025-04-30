---
"description": "Optimice el tamaño de sus archivos PDF omitiendo las fuentes Arial y Times Roman incrustadas con Aspose.Words para .NET. Siga esta guía paso a paso para optimizar sus archivos PDF."
"linktitle": "Optimice el tamaño de PDF con fuentes Arial y Times Roman incrustadas"
"second_title": "API de procesamiento de documentos de Aspose.Words"
"title": "Optimice el tamaño de PDF con fuentes Arial y Times Roman incrustadas"
"url": "/es/net/programming-with-pdfsaveoptions/skip-embedded-arial-and-times-roman-fonts/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Optimice el tamaño de PDF con fuentes Arial y Times Roman incrustadas

## Introducción

¿Alguna vez te has encontrado en una situación en la que tu archivo PDF es demasiado grande? Es como preparar la maleta para unas vacaciones y darte cuenta de que está a reventar. Sabes que necesitas bajar de peso, pero ¿qué haces? Al trabajar con archivos PDF, especialmente los convertidos desde documentos de Word, las fuentes incrustadas pueden aumentar el tamaño del archivo. Por suerte, Aspose.Words para .NET ofrece una solución elegante para mantener tus PDF con un diseño compacto y elegante. En este tutorial, te explicaremos cómo optimizar el tamaño de tu PDF omitiendo las fuentes Arial y Times Roman incrustadas. ¡Comencemos!

## Prerrequisitos

Antes de entrar en materia, hay algunas cosas que necesitarás:
- Aspose.Words para .NET: Asegúrate de tener instalada esta potente biblioteca. Si no es así, puedes descargarla desde [aquí](https://releases.aspose.com/words/net/).
- Un conocimiento básico de C#: esto le ayudará a seguir los fragmentos de código.
- Un documento de Word: utilizaremos un documento de muestra para demostrar el proceso. 

## Importar espacios de nombres

Primero, asegúrese de haber importado los espacios de nombres necesarios. Esto prepara el terreno para acceder a las funcionalidades de Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Muy bien, vamos a desglosar el proceso paso a paso.

## Paso 1: Configure su entorno

Para empezar, necesitas configurar tu entorno de desarrollo. Abre tu IDE de C# favorito (como Visual Studio) y crea un nuevo proyecto.

## Paso 2: Cargue el documento de Word

El siguiente paso es cargar el documento de Word que desea convertir a PDF. Asegúrese de que el documento esté en el directorio correcto.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

En este fragmento, reemplace `"YOUR DOCUMENT DIRECTORY"` con la ruta al directorio de su documento.

## Paso 3: Configurar las opciones de guardado de PDF

Ahora, debemos configurar las opciones de guardado del PDF para controlar cómo se incrustan las fuentes. Por defecto, todas las fuentes están incrustadas, lo que puede aumentar el tamaño del archivo. Cambiaremos esta configuración.

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
};
```

## Paso 4: Guardar el documento como PDF

Finalmente, guarde el documento como PDF con las opciones de guardado especificadas. Aquí es donde ocurre la magia.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.SkipEmbeddedArialAndTimesRomanFonts.pdf", saveOptions);
```

Este comando guarda su documento como un PDF llamado "OptimizedPDF.pdf" en el directorio especificado.

## Conclusión

¡Y listo! Acabas de aprender a optimizar el tamaño de tus archivos PDF omitiendo la incrustación de fuentes Arial y Times Roman con Aspose.Words para .NET. Esta sencilla modificación puede reducir significativamente el tamaño de tus archivos, facilitando su uso compartido y almacenamiento. Es como ir al gimnasio por tus PDF: eliminando peso innecesario y conservando todo lo esencial.

## Preguntas frecuentes

### ¿Por qué debería omitir la incrustación de fuentes Arial y Times Roman?
Omitir estas fuentes comunes puede reducir el tamaño del archivo PDF, ya que la mayoría de los sistemas ya tienen estas fuentes instaladas.

### ¿Esto afectará la apariencia de mi PDF?
No, no lo hará. Dado que Arial y Times Roman son fuentes estándar, la apariencia se mantiene uniforme en diferentes sistemas.

### ¿Puedo omitir la incrustación de otras fuentes también?
Sí, puedes configurar las opciones de guardado para omitir la incrustación de otras fuentes si es necesario.

### ¿Aspose.Words para .NET es gratuito?
Aspose.Words para .NET ofrece una prueba gratuita que puedes descargar [aquí](https://releases.aspose.com/), pero para tener acceso completo, necesitas comprar una licencia [aquí](https://purchase.aspose.com/buy).

### ¿Dónde puedo encontrar más tutoriales sobre Aspose.Words para .NET?
Puede encontrar documentación completa y tutoriales. [aquí](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}