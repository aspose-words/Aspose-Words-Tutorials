---
title: Unidad de medida
linktitle: Unidad de medida
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a configurar la función de unidad de medida en Aspose.Words para .NET para preservar el formato del documento durante la conversión de ODT.
weight: 10
url: /es/net/programming-with-odtsaveoptions/measure-unit/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Unidad de medida

## Introducción

¿Alguna vez ha tenido que convertir sus documentos de Word a diferentes formatos pero necesitaba una unidad de medida específica para su diseño? Ya sea que trabaje con pulgadas, centímetros o puntos, es fundamental garantizar que su documento mantenga su integridad durante el proceso de conversión. En este tutorial, le explicaremos cómo configurar la función de unidad de medida en Aspose.Words para .NET. Esta potente función garantiza que el formato de su documento se conserve exactamente como lo necesita al convertirlo al formato ODT (Open Document Text).

## Prerrequisitos

Antes de sumergirte en el código, hay algunas cosas que necesitarás para comenzar:

1. Aspose.Words para .NET: Asegúrate de tener instalada la última versión de Aspose.Words para .NET. Si aún no la tienes, puedes descargarla desde[aquí](https://releases.aspose.com/words/net/).
2. Entorno de desarrollo: un IDE como Visual Studio para escribir y ejecutar su código C#.
3. Conocimientos básicos de C#: comprender los conceptos básicos de C# le ayudará a seguir el tutorial.
4. Un documento de Word: tenga listo un documento de Word de muestra que pueda usar para la conversión.

## Importar espacios de nombres

Antes de comenzar a codificar, asegurémonos de que hemos importado los espacios de nombres necesarios. Agregue estas directivas using en la parte superior del archivo de código:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Paso 1: Configurar el directorio de documentos

En primer lugar, debe definir la ruta al directorio de su documento. Aquí es donde se encuentra su documento de Word y donde se guardará el archivo convertido.

```csharp
// Ruta a su directorio de documentos
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

 Reemplazar`"YOUR DOCUMENTS DIRECTORY"` con la ruta real a su directorio. Esto garantiza que su código sepa dónde encontrar su documento de Word.

## Paso 2: Cargue el documento de Word

 A continuación, debe cargar el documento de Word que desea convertir. Esto se hace mediante el`Document` clase de Aspose.Words.

```csharp
// Cargar el documento de Word
Document doc = new Document(dataDir + "Document.docx");
```

Asegúrese de que su documento de Word, llamado "Document.docx", esté presente en el directorio especificado.

## Paso 3: Configurar la unidad de medida

 Ahora, configuremos la unidad de medida para la conversión de ODT. Aquí es donde ocurre la magia. Configuraremos la`OdtSaveOptions` utilizar pulgadas como unidad de medida.

```csharp
// Configuración de opciones de backup con la función “Unidad de medida”
OdtSaveOptions saveOptions = new OdtSaveOptions { MeasureUnit = OdtSaveMeasureUnit.Inches };
```

 En este ejemplo, configuramos la unidad de medida en pulgadas. También puedes elegir otras unidades como`OdtSaveMeasureUnit.Centimeters` o`OdtSaveMeasureUnit.Points` dependiendo de sus necesidades.

## Paso 4: Convertir el documento a ODT

 Finalmente, convertiremos el documento de Word al formato ODT utilizando el formato configurado.`OdtSaveOptions`.

```csharp
// Convertir el documento a ODT
doc.Save(dataDir + "WorkingWithOdtSaveOptions.MeasureUnit.odt", saveOptions);
```

Esta línea de código guarda el documento convertido en el directorio especificado con la nueva unidad de medida aplicada.

## Conclusión

¡Y ya está! Si sigue estos pasos, podrá configurar fácilmente la función de unidad de medida en Aspose.Words para .NET para garantizar que el diseño de su documento se conserve durante la conversión. Ya sea que trabaje con pulgadas, centímetros o puntos, este tutorial le ha mostrado cómo controlar el formato de su documento con facilidad.

## Preguntas frecuentes

### ¿Qué es Aspose.Words para .NET?
Aspose.Words para .NET es una potente biblioteca para trabajar con documentos de Word de forma programada. Permite a los desarrolladores crear, modificar, convertir y procesar documentos de Word sin necesidad de Microsoft Word.

### ¿Puedo utilizar otras unidades de medida además de pulgadas?
 Sí, Aspose.Words para .NET admite otras unidades de medida, como centímetros y puntos. Puede especificar la unidad deseada mediante el botón`OdtSaveMeasureUnit` enumeración.

### ¿Hay una prueba gratuita disponible para Aspose.Words para .NET?
 Sí, puedes descargar una versión de prueba gratuita de Aspose.Words para .NET desde[aquí](https://releases.aspose.com/).

### ¿Dónde puedo encontrar documentación de Aspose.Words para .NET?
 Puede acceder a la documentación completa de Aspose.Words para .NET en[Este enlace](https://reference.aspose.com/words/net/).

### ¿Cómo puedo obtener soporte para Aspose.Words para .NET?
 Para obtener ayuda, puede visitar el foro de Aspose.Words en[Este enlace](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
