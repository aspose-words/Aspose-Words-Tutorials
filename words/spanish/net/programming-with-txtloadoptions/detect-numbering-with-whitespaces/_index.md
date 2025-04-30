---
"description": "Descubra cómo utilizar Aspose.Words para .NET para detectar numeraciones con espacios en blanco en documentos de texto sin formato y garantizar que sus listas se reconozcan correctamente."
"linktitle": "Detectar numeración con espacios en blanco"
"second_title": "API de procesamiento de documentos de Aspose.Words"
"title": "Detectar numeración con espacios en blanco"
"url": "/es/net/programming-with-txtloadoptions/detect-numbering-with-whitespaces/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Detectar numeración con espacios en blanco

## Introducción

¡Aspose.Words para entusiastas de .NET! Hoy profundizamos en una función fascinante que facilita la gestión de listas en documentos de texto plano. ¿Alguna vez has trabajado con archivos de texto donde algunas líneas se supone que son listas, pero no se ven bien al cargarlas en un documento de Word? Pues bien, tenemos un truco ingenioso: detectar numeración con espacios. Este tutorial te mostrará cómo usar... `DetectNumberingWithWhitespaces` opción en Aspose.Words para .NET para garantizar que sus listas se reconozcan correctamente, incluso cuando haya espacios en blanco entre los números y el texto.

## Prerrequisitos

Antes de comenzar, asegúrese de tener lo siguiente:

- Aspose.Words para .NET: Puedes descargarlo desde [Lanzamientos de Aspose](https://releases.aspose.com/words/net/) página.
- Entorno de desarrollo: Visual Studio o cualquier otro IDE de C#.
- .NET Framework instalado en su máquina.
- Conocimientos básicos de C#: comprender los conceptos básicos le ayudará a seguir los ejemplos.

## Importar espacios de nombres

Antes de empezar con el código, asegúrate de haber importado los espacios de nombres necesarios en tu proyecto. Aquí tienes un breve fragmento para empezar:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;
```

Desglosemos el proceso en pasos sencillos y manejables. Cada paso te guiará a través del código necesario y te explicará qué sucede.

## Paso 1: Defina su directorio de documentos

Primero, configuremos la ruta al directorio de documentos. Aquí se almacenarán los archivos de entrada y salida.

```csharp
// Ruta a su directorio de documentos
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Paso 2: Crear un documento de texto sin formato

A continuación, crearemos un documento de texto plano como cadena. Este documento contendrá partes que pueden interpretarse como listas.

```csharp
const string textDoc = "Full stop delimiters:\n" +
                       "1. First list item 1\n" +
                       "2. First list item 2\n" +
                       "3. First list item 3\n\n" +
                       "Right bracket delimiters:\n" +
                       "1) Second list item 1\n" +
                       "2) Second list item 2\n" +
                       "3) Second list item 3\n\n" +
                       "Bullet delimiters:\n" +
                       "• Third list item 1\n" +
                       "• Third list item 2\n" +
                       "• Third list item 3\n\n" +
                       "Whitespace delimiters:\n" +
                       "1 Fourth list item 1\n" +
                       "2 Fourth list item 2\n" +
                       "3 Fourth list item 3";
```

## Paso 3: Configurar LoadOptions

Para detectar la numeración con espacios en blanco, necesitamos configurar el `DetectNumberingWithWhitespaces` opción a `true` en un `TxtLoadOptions` objeto.

```csharp
TxtLoadOptions loadOptions = new TxtLoadOptions { DetectNumberingWithWhitespaces = true };
```

## Paso 4: Cargar el documento

Ahora, carguemos el documento usando el `TxtLoadOptions` como parámetro. Esto garantiza que la cuarta lista (con espacios) se detecte correctamente.

```csharp
Document doc = new Document(new MemoryStream(Encoding.UTF8.GetBytes(textDoc)), loadOptions);
```

## Paso 5: Guardar el documento

Finalmente, guarde el documento en el directorio especificado. Esto generará un documento de Word con las listas detectadas correctamente.

```csharp
doc.Save(dataDir + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

## Conclusión

¡Y listo! Con solo unas pocas líneas de código, dominarás el arte de detectar numeraciones con espacios en blanco en documentos de texto plano usando Aspose.Words para .NET. Esta función puede ser increíblemente útil al trabajar con varios formatos de texto y garantizar que tus listas se representen con precisión en tus documentos de Word. Así, la próxima vez que te encuentres con esas listas complicadas, sabrás exactamente qué hacer.

## Preguntas frecuentes

### Qué es `DetectNumberingWithWhitespaces` ¿en Aspose.Words para .NET?
`DetectNumberingWithWhitespaces` es una opción en `TxtLoadOptions` que permite a Aspose.Words reconocer listas incluso cuando hay espacios en blanco entre la numeración y el texto del elemento de la lista.

### ¿Puedo utilizar esta función para otros delimitadores como viñetas y corchetes?
Sí, Aspose.Words detecta automáticamente listas con delimitadores comunes como viñetas y corchetes. `DetectNumberingWithWhitespaces` Ayuda específicamente con listas que tienen espacios en blanco.

### ¿Qué pasa si no lo uso? `DetectNumberingWithWhitespaces`?
Sin esta opción, las listas con espacios en blanco entre la numeración y el texto podrían no reconocerse como listas y los elementos podrían aparecer como párrafos simples.

### ¿Esta función está disponible en otros productos Aspose?
Esta característica específica está diseñada para Aspose.Words para .NET y está diseñada para manejar el procesamiento de documentos de Word.

### ¿Cómo puedo obtener una licencia temporal de Aspose.Words para .NET?
Puede obtener una licencia temporal en la [Licencia temporal de Aspose](https://purchase.aspose.com/temporary-license/) página.




{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}