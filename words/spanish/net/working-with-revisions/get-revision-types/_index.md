---
title: Obtenga tipos de palabras de revisión
linktitle: Obtenga tipos de palabras de revisión
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a obtener tipos de revisión de palabras en un documento de Word con Aspose.Words para .NET. Esta guía paso a paso le ayuda a gestionar las revisiones de documentos de forma eficiente.
weight: 10
url: /es/net/working-with-revisions/get-revision-types/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Obtenga tipos de palabras de revisión

## Introducción

¿Alguna vez te has encontrado sumergido en un mar de revisiones de documentos y te has preguntado quién movió qué y cuándo? No estás solo. Gestionar las revisiones de documentos puede ser una tarea tediosa, especialmente cuando se trata de documentos extensos. ¡Pero no te preocupes! Con Aspose.Words para .NET, puedes identificar y gestionar fácilmente estas revisiones. En esta guía, te guiaremos paso a paso a través de un proceso sobre cómo obtener tipos de revisión de palabras en un documento de Word usando Aspose.Words para .NET. ¡Abróchate el cinturón y adentrémonos en el tema!

## Prerrequisitos

Antes de ponernos manos a la obra con el código, hay algunas cosas que necesitarás:

1.  Biblioteca Aspose.Words para .NET: si aún no lo ha hecho, descárguela desde[aquí](https://releases.aspose.com/words/net/).
2. Entorno de desarrollo: Visual Studio o cualquier otro IDE compatible con .NET.
3. Conocimientos básicos de C#: será beneficioso comprender el lenguaje de programación C#.
4.  Un documento de Word con revisiones: asegúrese de tener una`.docx`Archivo con cambios registrados para probar el código.

## Importar espacios de nombres

Para comenzar, deberá importar los espacios de nombres necesarios en su proyecto de C#. Esto le permitirá acceder a las funcionalidades proporcionadas por Aspose.Words para .NET.

```csharp
using Aspose.Words;
using Aspose.Words.Revision;
using System;
```

Dividamos el ejemplo en varios pasos para una mejor comprensión e implementación.

## Paso 1: Configurar el directorio de documentos

Lo primero es lo primero: debes definir la ruta al directorio de tus documentos. Aquí es donde se ubicará tu documento de Word con las revisiones.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Reemplazar`"YOUR DOCUMENT DIRECTORY"` con la ruta real a su carpeta de documentos.

## Paso 2: Cargue su documento de Word

A continuación, debes cargar el documento de Word en tu proyecto. Este documento debe contener las revisiones que deseas analizar.

```csharp
Document doc = new Document(dataDir + "Revisions.docx");
```

 Asegúrese de que el archivo`Revisions.docx` existe en el directorio especificado.

## Paso 3: Acceda a la colección de párrafos

Ahora que el documento está cargado, debe acceder a los párrafos dentro de la primera sección del cuerpo del documento. Esto le ayudará a iterar por cada párrafo para verificar las revisiones.

```csharp
ParagraphCollection paragraphs = doc.FirstSection.Body.Paragraphs;
```

## Paso 4: Recorrer los párrafos y comprobar si hay revisiones

Aquí es donde ocurre la magia. Repasaremos cada párrafo y comprobaremos si se ha movido (eliminado o insertado).

```csharp
for (int i = 0; i < paragraphs.Count; i++)
{
    if (paragraphs[i].IsMoveFromRevision)
        Console.WriteLine("Paragraph {0} has been moved (deleted).", i);
    if (paragraphs[i].IsMoveToRevision)
        Console.WriteLine("Paragraph {0} has been moved (inserted).", i);
}
```

 Este bucle recorre cada párrafo y utiliza el`IsMoveFromRevision` y`IsMoveToRevision` propiedades para determinar si el párrafo fue movido (eliminado) o movido (insertado).

## Conclusión

¡Y ya está! Con solo unas pocas líneas de código, puede identificar fácilmente los tipos de revisiones en su documento de Word utilizando Aspose.Words para .NET. Esta potente biblioteca facilita la gestión de las revisiones de documentos, lo que le permite centrarse en tareas más importantes. 

## Preguntas frecuentes

### ¿Puedo usar Aspose.Words para .NET para realizar un seguimiento de los cambios realizados por usuarios específicos?

Sí, Aspose.Words para .NET proporciona funcionalidad para acceder a los detalles de la revisión, incluido el autor de los cambios.

### ¿Hay una prueba gratuita disponible para Aspose.Words para .NET?

 ¡Por supuesto! Puedes obtener una prueba gratuita[aquí](https://releases.aspose.com/).

### ¿Cómo puedo solicitar una licencia temporal para Aspose.Words para .NET?

 Puede solicitar y solicitar una licencia temporal desde[aquí](https://purchase.aspose.com/temporary-license/).

### ¿Dónde puedo encontrar documentación más detallada sobre Aspose.Words para .NET?

 La documentación detallada está disponible en[Sitio web de Aspose](https://reference.aspose.com/words/net/).

### ¿Puedo usar Aspose.Words para .NET en un proyecto no comercial?

Sí, Aspose.Words para .NET se puede utilizar en proyectos comerciales y no comerciales, pero asegúrese de verificar los términos de la licencia.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
