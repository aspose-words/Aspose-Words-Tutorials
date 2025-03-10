---
title: Optimice el tamaño de PDF con las fuentes Arial y Times Roman integradas Skip
linktitle: Optimice el tamaño de PDF con las fuentes Arial y Times Roman integradas Skip
second_title: API de procesamiento de documentos Aspose.Words
description: Optimice el tamaño de los archivos PDF omitiendo las fuentes Arial y Times Roman incrustadas con Aspose.Words para .NET. Siga esta guía paso a paso para optimizar sus archivos PDF.
weight: 10
url: /es/net/programming-with-pdfsaveoptions/skip-embedded-arial-and-times-roman-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Optimice el tamaño de PDF con las fuentes Arial y Times Roman integradas Skip

## Introducción

¿Alguna vez te has encontrado en una situación en la que el tamaño de tu archivo PDF es demasiado grande? Es como preparar el equipaje para unas vacaciones y darte cuenta de que tu maleta está a punto de estallar. Sabes que necesitas perder algo de peso, pero ¿qué haces? Al trabajar con archivos PDF, especialmente aquellos convertidos a partir de documentos de Word, las fuentes incrustadas pueden aumentar el tamaño del archivo. Afortunadamente, Aspose.Words para .NET ofrece una solución elegante para mantener tus archivos PDF simples y eficientes. En este tutorial, profundizaremos en cómo optimizar el tamaño de tu PDF omitiendo las fuentes Arial y Times Roman incrustadas. ¡Comencemos!

## Prerrequisitos

Antes de entrar en materia, hay algunas cosas que necesitarás:
-  Aspose.Words para .NET: Asegúrate de tener instalada esta potente biblioteca. Si no es así, puedes descargarla desde[aquí](https://releases.aspose.com/words/net/).
- Un conocimiento básico de C#: esto le ayudará a seguir los fragmentos de código.
- Un documento de Word: utilizaremos un documento de muestra para demostrar el proceso. 

## Importar espacios de nombres

Lo primero es asegurarse de haber importado los espacios de nombres necesarios. Esto prepara el terreno para acceder a las funcionalidades de Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Muy bien, vamos a desglosar el proceso paso a paso.

## Paso 1: Configura tu entorno

Para comenzar, debes configurar tu entorno de desarrollo. Abre tu IDE de C# favorito (como Visual Studio) y crea un nuevo proyecto.

## Paso 2: Cargue el documento de Word

El siguiente paso es cargar el documento de Word que desea convertir a PDF. Asegúrese de que el documento se encuentre en el directorio correcto.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

 En este fragmento, reemplace`"YOUR DOCUMENT DIRECTORY"` con la ruta al directorio de su documento.

## Paso 3: Configurar las opciones para guardar PDF

Ahora, debemos configurar las opciones de guardado del PDF para controlar cómo se incrustan las fuentes. De forma predeterminada, todas las fuentes están incrustadas, lo que puede aumentar el tamaño del archivo. Cambiaremos esta configuración.

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
};
```

## Paso 4: Guardar el documento como PDF

Por último, guarde el documento como PDF con las opciones de guardado especificadas. Aquí es donde ocurre la magia.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.SkipEmbeddedArialAndTimesRomanFonts.pdf", saveOptions);
```

Este comando guarda su documento como un PDF llamado "OptimizedPDF.pdf" en el directorio especificado.

## Conclusión

¡Y ya lo tienes! Acabas de aprender a optimizar el tamaño de tus archivos PDF omitiendo la incorporación de fuentes Arial y Times Roman con Aspose.Words para .NET. Este sencillo ajuste puede reducir significativamente el tamaño de tus archivos, lo que hace que sea más fácil compartirlos y almacenarlos. Es como ir al gimnasio a por tus archivos PDF, deshacerte de un peso innecesario y mantener intactos todos los elementos esenciales.

## Preguntas frecuentes

### ¿Por qué debería omitir la incrustación de fuentes Arial y Times Roman?
Omitir estas fuentes comunes puede reducir el tamaño del archivo PDF, ya que la mayoría de los sistemas ya tienen estas fuentes instaladas.

### ¿Esto afectará la apariencia de mi PDF?
No, no lo hará. Dado que Arial y Times Roman son fuentes estándar, la apariencia permanece uniforme en los distintos sistemas.

### ¿Puedo omitir la incrustación de otras fuentes también?
Sí, puedes configurar las opciones de guardado para omitir la incrustación de otras fuentes si es necesario.

### ¿Aspose.Words para .NET es gratuito?
 Aspose.Words para .NET ofrece una prueba gratuita que puedes descargar[aquí](https://releases.aspose.com/) , pero para tener acceso completo, necesitas comprar una licencia[aquí](https://purchase.aspose.com/buy).

### ¿Dónde puedo encontrar más tutoriales sobre Aspose.Words para .NET?
Puede encontrar documentación completa y tutoriales.[aquí](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
