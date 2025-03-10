---
title: Listar Mantener formato de fuente
linktitle: Listar Mantener formato de fuente
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a combinar documentos de Word conservando el formato con Aspose.Words para .NET. Este tutorial ofrece instrucciones paso a paso para combinar documentos sin problemas.
weight: 10
url: /es/net/join-and-append-documents/list-keep-source-formatting/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Listar Mantener formato de fuente

## Introducción

En este tutorial, exploraremos cómo utilizar Aspose.Words para .NET para fusionar documentos y, al mismo tiempo, conservar el formato original. Esta capacidad es esencial para situaciones en las que es fundamental mantener la apariencia original de los documentos.

## Prerrequisitos

Antes de continuar, asegúrese de tener los siguientes requisitos previos:

- Visual Studio instalado en su máquina.
-  Tienes instalado Aspose.Words para .NET. Puedes descargarlo desde[aquí](https://releases.aspose.com/words/net/).
- Familiaridad básica con programación C# y entorno .NET.

## Importar espacios de nombres

Primero, importe los espacios de nombres necesarios en su proyecto C#:

```csharp
using Aspose.Words;
```

## Paso 1: Configura tu proyecto

Comience por crear un nuevo proyecto de C# en Visual Studio. Asegúrese de que se haga referencia a Aspose.Words para .NET en su proyecto. De lo contrario, puede agregarlo a través del Administrador de paquetes NuGet.

## Paso 2: Inicializar las variables del documento

```csharp
// Ruta al directorio de su documento
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Cargar documentos de origen y destino
Document srcDoc = new Document(dataDir + "Document source.docx");
Document dstDoc = new Document(dataDir + "Document destination with list.docx");
```

## Paso 3: Configurar los ajustes de la sección

Para mantener un flujo continuo en el documento fusionado, ajuste el inicio de la sección:

```csharp
srcDoc.FirstSection.PageSetup.SectionStart = SectionStart.Continuous;
```

## Paso 4: Fusionar documentos

Añade el contenido del documento fuente (`srcDoc`) al documento de destino (`dstDoc`) conservando el formato original:

```csharp
dstDoc.AppendDocument(srcDoc, ImportFormatMode.KeepSourceFormatting);
```

## Paso 5: Guardar el documento fusionado

Por último, guarde el documento fusionado en el directorio especificado:

```csharp
dstDoc.Save(dataDir + "JoinAndAppendDocuments.ListKeepSourceFormatting.docx");
```

## Conclusión

En conclusión, fusionar documentos conservando su formato original es sencillo con Aspose.Words para .NET. Este tutorial lo ha guiado a través del proceso, asegurándose de que su documento fusionado mantenga el diseño y el estilo del documento original.

## Preguntas frecuentes

### ¿Qué pasa si mis documentos tienen diferentes estilos?
Aspose.Words maneja diferentes estilos con elegancia, conservando el formato original lo más fielmente posible.

### ¿Puedo fusionar documentos de diferentes formatos?
Sí, Aspose.Words admite la fusión de documentos de varios formatos, incluidos DOCX, DOC, RTF y otros.

### ¿Aspose.Words es compatible con .NET Core?
Sí, Aspose.Words es totalmente compatible con .NET Core, lo que permite el desarrollo multiplataforma.

### ¿Cómo puedo gestionar documentos grandes de manera eficiente?
Aspose.Words proporciona API eficientes para la manipulación de documentos, optimizadas para el rendimiento incluso con documentos grandes.

### ¿Dónde puedo encontrar más ejemplos y documentación?
 Puede explorar más ejemplos y documentación detallada en[Documentación de Aspose.Words](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
