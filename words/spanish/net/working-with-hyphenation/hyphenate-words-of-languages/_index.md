---
title: Palabras con guiones en los idiomas
linktitle: Palabras con guiones en los idiomas
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a separar palabras con guiones en distintos idiomas con Aspose.Words para .NET. Siga esta guía detallada paso a paso para mejorar la legibilidad de sus documentos.
weight: 10
url: /es/net/working-with-hyphenation/hyphenate-words-of-languages/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Palabras con guiones en los idiomas

## Introducción

¡Hola! ¿Alguna vez intentaste leer un documento con palabras largas y sin interrupciones y sentiste que se te agarrotaba el cerebro? Todos hemos pasado por eso. Pero, ¿adivina qué? ¡La separación de palabras es tu salvación! Con Aspose.Words para .NET, puedes hacer que tus documentos se vean profesionales separando las palabras con guiones correctamente de acuerdo con las reglas del lenguaje. Veamos cómo puedes lograr esto sin problemas.

## Prerrequisitos

Antes de comenzar, asegúrese de tener lo siguiente:

-  Aspose.Words para .NET está instalado. Si aún no lo tienes, descárgalo[aquí](https://releases.aspose.com/words/net/).
-  Una licencia válida para Aspose.Words. Puedes comprar una[aquí](https://purchase.aspose.com/buy) o obtener una licencia temporal[aquí](https://purchase.aspose.com/temporary-license/).
- Conocimientos básicos de C# y .NET framework.
- Un editor de texto o un IDE como Visual Studio.

## Importar espacios de nombres

Lo primero es lo primero: importemos los espacios de nombres necesarios. Esto ayuda a acceder a las clases y métodos necesarios para la separación de palabras.

```csharp
using Aspose.Words;
using Aspose.Words.Hyphenation;
```

## Paso 1: Cargue su documento

 Necesitará especificar el directorio donde se encuentra su documento. Reemplazar`"YOUR DOCUMENT DIRECTORY"` con la ruta real a su documento.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "German text.docx");
```

## Paso 3: Registrar diccionarios de separación de palabras

 Aspose.Words requiere diccionarios de separación de palabras para diferentes idiomas. Asegúrese de tener los`.dic`archivos para los idiomas que desea dividir en sílabas. Registre estos diccionarios utilizando el`Hyphenation.RegisterDictionary` método.

```csharp
Hyphenation.RegisterDictionary("en-US", dataDir + "hyph_en_US.dic");
Hyphenation.RegisterDictionary("de-CH", dataDir + "hyph_de_CH.dic");
```

## Paso 4: Guardar el documento

Por último, guarde el documento con guiones en el formato deseado. En este caso, lo guardaremos como PDF.

```csharp
doc.Save(dataDir + "TreatmentByCesure.pdf");
```

## Conclusión

¡Y ya está! Con solo unas pocas líneas de código, puede mejorar significativamente la legibilidad de sus documentos al separar palabras con guiones según las reglas específicas del lenguaje. Aspose.Words para .NET hace que este proceso sea sencillo y eficiente. ¡Así que adelante y brinde a sus lectores una experiencia de lectura más fluida!

## Preguntas frecuentes

### ¿Qué es la separación de palabras en los documentos?
La separación de palabras es el proceso de separar palabras al final de las líneas para mejorar la alineación y la legibilidad del texto.

### ¿Dónde puedo conseguir diccionarios de separación de palabras para diferentes idiomas?
Puedes encontrar diccionarios de separación de palabras en línea, a menudo proporcionados por institutos de idiomas o proyectos de código abierto.

### ¿Puedo usar Aspose.Words para .NET sin una licencia?
 Sí, pero la versión sin licencia tendrá limitaciones. Se recomienda obtener una[licencia temporal](https://purchase.aspose.com/temporary-license) para funciones completas.

### ¿Aspose.Words para .NET es compatible con .NET Core?
Sí, Aspose.Words para .NET es compatible con .NET Framework y .NET Core.

### ¿Cómo puedo manejar varios idiomas en un solo documento?
Puede registrar varios diccionarios de separación de palabras como se muestra en el ejemplo, y Aspose.Words los manejará en consecuencia.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
