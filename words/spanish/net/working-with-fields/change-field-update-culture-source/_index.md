---
title: Cambiar campo Actualizar cultura Fuente
linktitle: Cambiar campo Actualizar cultura Fuente
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a cambiar la fuente de la cultura de actualización de campos en Aspose.Words para .NET con esta guía. Controle fácilmente el formato de fecha en función de diferentes culturas.
weight: 10
url: /es/net/working-with-fields/change-field-update-culture-source/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cambiar campo Actualizar cultura Fuente

## Introducción

En este tutorial, nos adentraremos en el mundo de Aspose.Words para .NET y exploraremos cómo cambiar la fuente de la cultura de actualización de campos. Si trabaja con documentos de Word que incluyen campos de fecha y necesita controlar cómo se formatean estas fechas en función de las diferentes culturas, esta guía es para usted. Repasemos el proceso paso a paso, para asegurarnos de que comprenda cada concepto y pueda aplicarlo de manera eficaz en sus proyectos.

## Prerrequisitos

Antes de pasar al código, asegúrese de tener lo siguiente:

-  Aspose.Words para .NET: Puedes descargarlo desde[aquí](https://releases.aspose.com/words/net/).
- Entorno de desarrollo: cualquier IDE compatible con .NET (por ejemplo, Visual Studio).
- Conocimientos básicos de C#: este tutorial asume que tienes un conocimiento fundamental de la programación en C#.

## Importar espacios de nombres

Primero, importemos los espacios de nombres necesarios para nuestro proyecto. Esto garantizará que tengamos acceso a todas las clases y métodos requeridos que proporciona Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
```

Ahora, desglosemos el ejemplo en varios pasos para ayudarlo a comprender cómo cambiar la fuente de cultura de actualización de campo en Aspose.Words para .NET.

## Paso 1: Inicializar el documento

 El primer paso es crear una nueva instancia del`Document` clase y una`DocumentBuilder`Esto establece las bases para crear y manipular nuestro documento de Word.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Paso 2: Insertar campos con una configuración regional específica

A continuación, debemos insertar campos en el documento. En este ejemplo, insertaremos dos campos de fecha. Estableceremos la configuración regional de la fuente en alemán (LocaleId = 1031) para demostrar cómo la cultura afecta el formato de fecha.

```csharp
builder.Font.LocaleId = 1031; // Alemán
builder.InsertField("MERGEFIELD Date1 \\@ \"dddd, d MMMM yyyy\"");
builder.Write(" - ");
builder.InsertField("MERGEFIELD Date2 \\@ \"dddd, d MMMM yyyy\"");
```

## Paso 3: Establecer la fuente de cultura para la actualización del campo

 Para controlar la cultura utilizada al actualizar los campos, configuramos el`FieldUpdateCultureSource` propiedad de la`FieldOptions`Clase. Esta propiedad determina si la cultura se toma del código de campo o del documento.

```csharp
doc.FieldOptions.FieldUpdateCultureSource = FieldUpdateCultureSource.FieldCode;
```

## Paso 4: Ejecutar la combinación de correspondencia

Ahora necesitamos ejecutar una combinación de correspondencia para completar los campos con datos reales. En este ejemplo, estableceremos el segundo campo de fecha (`Date2`) al 1 de enero de 2011.

```csharp
doc.MailMerge.Execute(new string[] { "Date2" }, new object[] { new DateTime(2011, 1, 1) });
```

## Paso 5: Guardar el documento

Por último, guardamos el documento en el directorio especificado. Este paso completa el proceso de cambio de la fuente cultural de actualización de campos.

```csharp
doc.Save(dataDir + "WorkingWithFields.ChangeFieldUpdateCultureSource.docx");
```

## Conclusión

¡Y ya está! Has cambiado correctamente la fuente de la cultura de actualización de campos en Aspose.Words para .NET. Si sigues estos pasos, podrás asegurarte de que tus documentos de Word muestren las fechas y otros valores de campo según la configuración cultural especificada. Esto puede resultar especialmente útil al generar documentos para un público internacional.

## Preguntas frecuentes

###  ¿Cuál es el propósito de establecer el`LocaleId`?
 El`LocaleId` especifica la configuración cultural del texto, lo que afecta cómo se formatean las fechas y otros datos sensibles a la configuración regional.

### ¿Puedo utilizar una configuración regional distinta al alemán?
 Sí, puedes configurar el`LocaleId` cualquier identificador de configuración regional válido. Por ejemplo, 1033 para inglés (Estados Unidos).

###  ¿Qué pasa si no configuro el`FieldUpdateCultureSource` property?
Si esta propiedad no está configurada, se utilizará la configuración cultural predeterminada del documento al actualizar los campos.

### ¿Es posible actualizar campos según la cultura del documento en lugar del código de campo?
 Sí, puedes configurarlo`FieldUpdateCultureSource` a`FieldUpdateCultureSource.Document` para utilizar la configuración cultural del documento.

### ¿Cómo puedo formatear fechas con un patrón diferente?
 Puede cambiar el patrón de formato de fecha en el`InsertField` método modificando el`\\@` valor del interruptor
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
