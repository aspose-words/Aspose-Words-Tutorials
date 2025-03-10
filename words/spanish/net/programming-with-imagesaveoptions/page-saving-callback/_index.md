---
title: Devolución de llamada para guardar página
linktitle: Devolución de llamada para guardar página
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a guardar cada página de un documento de Word como una imagen PNG separada usando Aspose.Words para .NET con nuestra guía detallada paso a paso.
weight: 10
url: /es/net/programming-with-imagesaveoptions/page-saving-callback/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Devolución de llamada para guardar página

## Introducción

¡Hola! ¿Alguna vez has sentido la necesidad de guardar cada página de un documento de Word como imágenes independientes? Quizás quieras dividir un informe grande en elementos visuales fáciles de digerir o quizás necesites crear miniaturas para una vista previa. Cualquiera sea tu motivo, usar Aspose.Words para .NET hace que esta tarea sea muy sencilla. En esta guía, te guiaremos a través del proceso de configuración de una devolución de llamada para guardar páginas y guardar cada página de un documento como una imagen PNG individual. ¡Vamos a profundizar!

## Prerrequisitos

Antes de comenzar, asegúrese de tener lo siguiente:

1.  Aspose.Words para .NET: si aún no lo ha hecho, descárguelo e instálelo desde[aquí](https://releases.aspose.com/words/net/).
2. Visual Studio: cualquier versión debería funcionar, pero usaré Visual Studio 2019 para esta guía.
3. Conocimientos básicos de C#: necesitarás un conocimiento básico de C# para seguir.

## Importar espacios de nombres

Primero, debemos importar los espacios de nombres necesarios. Esto nos ayuda a acceder a las clases y métodos requeridos sin tener que escribir el espacio de nombres completo cada vez.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Paso 1: Configurar el directorio de documentos

Bien, comencemos por definir la ruta al directorio de documentos. Aquí es donde se encuentra el documento de Word de entrada y donde se guardarán las imágenes de salida.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Paso 2: Cargue su documento

A continuación, cargaremos el documento que desea procesar. Asegúrese de que su documento ("Rendering.docx") se encuentre en el directorio especificado.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Paso 3: Configurar las opciones para guardar imágenes

Necesitamos configurar las opciones para guardar imágenes. En este caso, guardaremos las páginas como archivos PNG.

```csharp
ImageSaveOptions imageSaveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(new PageRange(0, doc.PageCount - 1)),
    PageSavingCallback = new HandlePageSavingCallback()
};
```

 Aquí,`PageSet` especifica el rango de páginas a guardar, y`PageSavingCallback` apunta a nuestra clase de devolución de llamada personalizada.

## Paso 4: Implementar la devolución de llamada para guardar la página

Ahora, implementemos la clase de devolución de llamada que maneja cómo se guarda cada página.

```csharp
private class HandlePageSavingCallback : IPageSavingCallback
{
    public void PageSaving(PageSavingArgs args)
    {
        args.PageFileName = string.Format(dataDir + "Page_{0}.png", args.PageIndex);
    }
}
```

 Esta clase implementa el`IPageSavingCallback` interfaz, y dentro de la`PageSaving` método, definimos el patrón de nombres para cada página guardada.

## Paso 5: Guardar el documento como imágenes

Por último, guardamos el documento utilizando las opciones configuradas.

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.PageSavingCallback.png", imageSaveOptions);
```

## Conclusión

¡Y ya está! Ha configurado correctamente una devolución de llamada para guardar páginas y guardar cada página de un documento de Word como una imagen PNG independiente mediante Aspose.Words para .NET. Esta técnica es increíblemente útil para diversas aplicaciones, desde la creación de vistas previas de páginas hasta la generación de imágenes de páginas individuales para informes. 

¡Feliz codificación!

## Preguntas frecuentes

### ¿Puedo guardar páginas en formatos distintos a PNG?  
 Sí, puedes guardar páginas en diferentes formatos como JPEG, BMP y TIFF cambiando el`SaveFormat` en`ImageSaveOptions`.

### ¿Qué pasa si quiero guardar sólo páginas específicas?  
 Puede especificar las páginas que desea guardar ajustando la`PageSet` parámetro en`ImageSaveOptions`.

### ¿Es posible personalizar la calidad de la imagen?  
 ¡Por supuesto! Puedes configurar propiedades como`ImageSaveOptions.JpegQuality` para controlar la calidad de las imágenes de salida.

### ¿Cómo puedo gestionar documentos grandes de manera eficiente?  
Para documentos grandes, considere procesar páginas en lotes para administrar el uso de memoria de manera efectiva.

### ¿Dónde puedo encontrar más información sobre Aspose.Words para .NET?  
 Echa un vistazo a la[documentación](https://reference.aspose.com/words/net/) para guías completas y ejemplos.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
