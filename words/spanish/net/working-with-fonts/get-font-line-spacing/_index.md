---
title: Obtener el espaciado entre líneas de fuente
linktitle: Obtener el espaciado entre líneas de fuente
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a obtener el interlineado de fuentes con Aspose.Words para .NET con este tutorial paso a paso. Perfecto para desarrolladores.
weight: 10
url: /es/net/working-with-fonts/get-font-line-spacing/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Obtener el espaciado entre líneas de fuente

## Introducción

Aspose.Words para .NET es una potente biblioteca que permite crear, manipular y convertir documentos de Word mediante programación. Una tarea habitual que puede necesitar realizar es recuperar el interlineado de una fuente específica en un documento. En este tutorial, le guiaremos por el proceso paso a paso, asegurándonos de que pueda obtener fácilmente el interlineado de fuentes con Aspose.Words para .NET. 

## Prerrequisitos

Antes de sumergirnos en el código, asegúrese de tener los siguientes requisitos previos:

1.  Biblioteca Aspose.Words para .NET: Descargue e instale la última versión desde[aquí](https://releases.aspose.com/words/net/).
2. Entorno de desarrollo: asegúrese de tener configurado un IDE como Visual Studio.
3. Conocimientos básicos de C#: este tutorial asume que tienes un conocimiento básico de programación en C#.

## Importar espacios de nombres

En primer lugar, debe importar los espacios de nombres necesarios en su proyecto de C#. Estos espacios de nombres le permitirán acceder a las funcionalidades de Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Dividamos el proceso para obtener el interlineado de fuente en pasos simples y manejables.

## Paso 1: Crear un nuevo documento

El primer paso es crear una nueva instancia de documento de Word utilizando Aspose.Words para .NET.

```csharp
Document doc = new Document();
```

## Paso 2: Inicializar DocumentBuilder

 continuación, necesitamos inicializar el`DocumentBuilder` objeto. Este objeto nos ayudará a construir y manipular el contenido del documento.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Paso 3: Establezca las propiedades de la fuente

Ahora, configuramos las propiedades de fuente para el texto que queremos insertar. Para este ejemplo, utilizaremos la fuente "Calibri".

```csharp
builder.Font.Name = "Calibri";
```

## Paso 4: Escribe texto en el documento

 Usando el`DocumentBuilder` objeto, escribe un texto en el documento. Este texto utilizará las propiedades de fuente que configuramos en el paso anterior.

```csharp
builder.Writeln("Sample Text");
```

## Paso 5: Recuperar el objeto de fuente

Para obtener el interlineado, debemos acceder al objeto de fuente del texto que acabamos de agregar. Esto se puede hacer navegando por la estructura del documento hasta el primer párrafo.

```csharp
Font font = builder.Document.FirstSection.Body.FirstParagraph.Runs[0].Font;
```

## Paso 6: Obtenga el espaciado entre líneas

Finalmente, recuperamos el interlineado del objeto fuente y lo imprimimos en la consola.

```csharp
Console.WriteLine($"lineSpacing = {font.LineSpacing}");
```

## Conclusión

¡Y ya está! Recuperar el interlineado de la fuente con Aspose.Words para .NET es muy sencillo si se divide en estos sencillos pasos. Tanto si está creando un documento nuevo como si está trabajando con uno existente, Aspose.Words le proporciona todas las herramientas que necesita para gestionar las propiedades de las fuentes de forma eficiente.

## Preguntas frecuentes

### ¿Qué es Aspose.Words para .NET?
Aspose.Words para .NET es una potente biblioteca que permite a los desarrolladores crear, manipular y convertir documentos de Word mediante programación utilizando C#.

### ¿Puedo usar Aspose.Words para .NET en otros lenguajes .NET?
Sí, puede utilizar Aspose.Words para .NET con cualquier lenguaje .NET, incluidos VB.NET y F#.

### ¿Cómo puedo descargar Aspose.Words para .NET?
 Puede descargar la última versión de Aspose.Words para .NET desde[aquí](https://releases.aspose.com/words/net/).

### ¿Hay una prueba gratuita disponible para Aspose.Words para .NET?
 Sí, puedes obtener una prueba gratuita desde[aquí](https://releases.aspose.com/).

### ¿Dónde puedo encontrar la documentación de Aspose.Words para .NET?
 La documentación de Aspose.Words para .NET está disponible[aquí](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
