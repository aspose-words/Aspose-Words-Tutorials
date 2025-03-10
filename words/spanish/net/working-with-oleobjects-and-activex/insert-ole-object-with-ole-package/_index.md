---
title: Insertar objeto Ole en Word con el paquete Ole
linktitle: Insertar objeto Ole en Word con el paquete Ole
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a insertar objetos OLE en documentos de Word con Aspose.Words para .NET. Siga nuestra guía detallada paso a paso para incrustar archivos sin problemas.
weight: 10
url: /es/net/working-with-oleobjects-and-activex/insert-ole-object-with-ole-package/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Insertar objeto Ole en Word con el paquete Ole

## Introducción

Si alguna vez ha deseado incrustar un archivo en un documento de Word, está en el lugar correcto. Ya sea un archivo ZIP, una hoja de Excel o cualquier otro tipo de archivo, incrustarlo directamente en su documento de Word puede ser increíblemente útil. Piense en ello como si tuviera un compartimento secreto en su documento donde puede guardar todo tipo de tesoros. Y hoy, vamos a explicar cómo hacerlo usando Aspose.Words para .NET. ¿Está listo para convertirse en un mago de Word? ¡Vamos a sumergirnos en ello!

## Prerrequisitos

Antes de comenzar, asegúrese de tener lo siguiente:

1. Aspose.Words para .NET: Si aún no lo ha hecho, descárguelo desde[aquí](https://releases.aspose.com/words/net/).
2. Un entorno de desarrollo: Visual Studio o cualquier otro entorno de desarrollo .NET.
3. Comprensión básica de C#: no es necesario ser un experto, pero conocer C# le ayudará.
4. Un directorio de documentos: una carpeta donde puedes almacenar y recuperar documentos.

## Importar espacios de nombres

Lo primero es lo primero: pongamos en orden nuestros espacios de nombres. Debes incluir los siguientes espacios de nombres en tu proyecto:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
```

Vamos a dividirlo en pasos pequeños para que sea fácil de seguir.

## Paso 1: Configura tu documento

Imagina que eres un artista con un lienzo en blanco. Primero, necesitamos nuestro lienzo en blanco, que es nuestro documento de Word. Así es como lo configuras:

```csharp
// Ruta al directorio de su documento
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Este código inicializa un nuevo documento de Word y configura un DocumentBuilder, que usaremos para insertar contenido en nuestro documento.

## Paso 2: Lee tu objeto Ole

A continuación, leamos el archivo que desea insertar. Piense en esto como si estuviera buscando el tesoro que desea ocultar en su compartimento secreto:

```csharp
byte[] bs = File.ReadAllBytes(dataDir + "Zip file.zip");
```

Esta línea lee todos los bytes de su archivo ZIP y los almacena en una matriz de bytes.

## Paso 3: Insertar el objeto Ole

Ahora viene la parte mágica. Vamos a incrustar el archivo en nuestro documento de Word:

```csharp
using (Stream stream = new MemoryStream(bs))
{
    Shape shape = builder.InsertOleObject(stream, "Package", true, null);
    OlePackage olePackage = shape.OleFormat.OlePackage;
    olePackage.FileName = "filename.zip";
    olePackage.DisplayName = "displayname.zip";
}
```

 Aquí, creamos un flujo de memoria a partir de la matriz de bytes y usamos el`InsertOleObject` Método para incrustarlo en el documento. También establecemos el nombre del archivo y el nombre para mostrar del objeto incrustado.

## Paso 4: Guarde su documento

Por último, guardemos nuestra obra maestra:

```csharp
doc.Save(dataDir + "WorkingWithOleObjectsAndActiveX.InsertOleObjectWithOlePackage.docx");
```

Esto guarda el documento con el archivo incrustado en el directorio especificado.

## Conclusión

¡Y ya está! Ha incorporado con éxito un objeto OLE en un documento de Word con Aspose.Words para .NET. Es como añadir una joya oculta dentro de su documento que puede descubrirse en cualquier momento. Esta técnica puede resultar increíblemente útil para una variedad de aplicaciones, desde documentación técnica hasta informes dinámicos. 

## Preguntas frecuentes

### ¿Puedo incrustar otros tipos de archivos usando este método?
Sí, puedes incrustar varios tipos de archivos, como hojas de Excel, archivos PDF e imágenes.

### ¿Necesito una licencia para Aspose.Words?
 Sí, necesitas una licencia válida. Puedes obtener una[licencia temporal](https://purchase.aspose.com/temporary-license/) para evaluación.

### ¿Cómo puedo personalizar el nombre para mostrar del objeto OLE?
 Puedes configurar el`DisplayName` propiedad de la`OlePackage` Para personalizarlo.

### ¿Aspose.Words es compatible con .NET Core?
Sí, Aspose.Words es compatible con .NET Framework y .NET Core.

### ¿Puedo editar el objeto OLE incrustado dentro del documento de Word?
No, no puedes editar el objeto OLE directamente en Word. Debes abrirlo en su aplicación nativa.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
