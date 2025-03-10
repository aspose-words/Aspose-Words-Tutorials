---
title: Establecer carpeta de imágenes
linktitle: Establecer carpeta de imágenes
second_title: API de procesamiento de documentos Aspose.Words
description: Convierta documentos de Word a Markdown con la alineación de tablas adecuada utilizando Aspose.Words para .NET. Siga nuestra guía detallada para obtener resultados perfectos.
weight: 10
url: /es/net/programming-with-markdownsaveoptions/set-images-folder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Establecer carpeta de imágenes

## Introducción

¿Alguna vez ha deseado exportar su documento de Word al formato Markdown y asegurarse de que las tablas y el contenido se alineen perfectamente? Aspose.Words para .NET es la solución ideal para esta tarea. En este artículo, lo guiaremos a través del proceso de configuración de Aspose.Words, preparación de su documento y exportación a Markdown con la alineación adecuada del contenido de las tablas. Desglosaremos cada paso para que sea fácil de seguir y comprender. Entonces, ¡profundicemos y transformemos sus documentos de Word en archivos Markdown perfectamente alineados!

## Prerrequisitos

Antes de comenzar, asegúrese de tener lo siguiente:

-  Aspose.Words para .NET: Puedes descargarlo[aquí](https://releases.aspose.com/words/net/).
-  Una licencia válida: Obtenga una prueba gratuita[aquí](https://releases.aspose.com/) o una licencia temporal[aquí](https://purchase.aspose.com/temporary-license/).
- Visual Studio: o cualquier otro IDE que admita el desarrollo .NET.
- Conocimientos básicos de C#: Comprensión del lenguaje de programación C#.

## Importar espacios de nombres

Para comenzar, deberá importar los espacios de nombres necesarios en su proyecto de C#. Estos espacios de nombres le permitirán acceder a la funcionalidad de Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;
```

## Paso 1: Configura tu proyecto

Lo primero es lo primero: configure su proyecto .NET en su IDE. Cree una nueva aplicación de consola y agregue una referencia a Aspose.Words para .NET.

### 1.1 Crear un nuevo proyecto

Abra Visual Studio y cree un nuevo proyecto de aplicación de consola. Asígnele el nombre "MarkdownExporter" o algo similar.

### 1.2 Añadir referencia de Aspose.Words

 Para agregar Aspose.Words a su proyecto, puede descargar la DLL desde[Sitio web de Aspose](https://releases.aspose.com/words/net/) y agréguelo manualmente o use el Administrador de paquetes NuGet:

```bash
Install-Package Aspose.Words
```

## Paso 2: Escribe el código para exportar como Markdown

Ahora, escribamos el código para leer el documento de Word y guardarlo como un archivo Markdown con la alineación de tabla adecuada.

### 2.1 Defina la ruta a su documento

Establezca la ruta de su documento de Word y la carpeta donde desea guardar las imágenes.

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY";
```

### 2.2 Cargar el documento

Cargue su documento de Word usando Aspose.Words.

```csharp
Document doc = new Document(dataDir + "Image bullet points.docx");
```

### 2.3 Configurar las opciones de guardado de Markdown

 Configurar el`MarkdownSaveOptions` para especificar dónde se deben almacenar las imágenes.

```csharp
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions
{
    ImagesFolder = dataDir + "Images"
};
```

### 2.4 Guardar el documento como Markdown

 Utilice un`MemoryStream` para guardar el documento en formato Markdown.

```csharp
using (MemoryStream stream = new MemoryStream())
{
    doc.Save(stream, saveOptions);
}
```

## Conclusión

Exportar un documento de Word a Markdown con el contenido de la tabla alineado con Aspose.Words para .NET es sencillo si sigue estos pasos. Con unas pocas líneas de código, puede automatizar el proceso de conversión y asegurarse de que su contenido esté bien formateado. Ahora, puede compartir fácilmente sus documentos en formato Markdown, sabiendo que se verán bien y mantendrán su estructura.

## Preguntas frecuentes

### ¿Puedo usar Aspose.Words para .NET con otros lenguajes de programación?

Sí, Aspose.Words para .NET se puede utilizar con cualquier lenguaje compatible con .NET, como VB.NET, F# y más.

### ¿Cómo obtengo una licencia temporal para Aspose.Words?

Puede obtener una licencia temporal[aquí](https://purchase.aspose.com/temporary-license/).

### ¿Qué tipos de documentos puedo convertir a Markdown?

Puede convertir varios documentos de Word, incluidos .doc, .docx, .rtf y más.

### ¿Existe alguna limitación en la versión de prueba de Aspose.Words?

La versión de prueba tiene algunas limitaciones, como marcas de agua en los archivos de salida. Puedes obtener una versión de prueba gratuita[aquí](https://releases.aspose.com/).

### ¿Dónde puedo encontrar más ejemplos y documentación para Aspose.Words?

 Puede encontrar documentación detallada y ejemplos en[Sitio web de Aspose](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
