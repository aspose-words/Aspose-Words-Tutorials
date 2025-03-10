---
title: Posición de la mesa flotante
linktitle: Posición de la mesa flotante
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a controlar la posición flotante de las tablas en documentos de Word usando Aspose.Words para .NET con nuestra guía detallada paso a paso.
weight: 10
url: /es/net/programming-with-tables/floating-table-position/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Posición de la mesa flotante

## Introducción

¿Estás listo para sumergirte en el mundo de la manipulación de posiciones de tablas en documentos de Word con Aspose.Words para .NET? Abróchate el cinturón, porque hoy vamos a explorar cómo controlar la posición flotante de las tablas con facilidad. ¡Te convertiremos en un experto en posicionamiento de tablas en un abrir y cerrar de ojos!

## Prerrequisitos

Antes de embarcarnos en este apasionante viaje, asegurémonos de tener todo lo que necesitamos:

1. Biblioteca Aspose.Words para .NET: asegúrese de tener la versión más reciente. Si no la tiene,[Descárgalo aquí](https://releases.aspose.com/words/net/).
2. .NET Framework: asegúrese de que su entorno de desarrollo esté configurado con .NET.
3. Entorno de desarrollo: Visual Studio o cualquier IDE preferido.
4. Un documento de Word: Tenga listo un documento de Word que contenga una tabla.

## Importar espacios de nombres

Para comenzar, debe importar los espacios de nombres necesarios en su proyecto .NET. Este es el fragmento que debe incluir en la parte superior de su archivo C#:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Tables;
```

## Guía paso a paso

Ahora, vamos a dividir el proceso en pasos simples y digeribles.

## Paso 1: Cargue el documento

Lo primero es lo primero: debes cargar tu documento de Word. Aquí es donde se encuentra tu tabla.

```csharp
// Ruta al directorio de su documento
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table wrapped by text.docx");
```

Imagina que tu documento de Word es un lienzo y que tu tabla es una obra de arte sobre él. Nuestro objetivo es colocar esta obra de arte exactamente donde queremos en el lienzo.

## Paso 2: Acceda a la tabla

A continuación, debemos acceder a la tabla dentro del documento. Normalmente, trabajaremos con la primera tabla del cuerpo del documento.

```csharp
Table table = doc.FirstSection.Body.Tables[0];
```

Piense en este paso como si estuviera buscando la tabla con la que desea trabajar en un documento físico. Debe saber exactamente dónde se encuentra para realizar cambios.

## Paso 3: Establecer la posición horizontal

Ahora, establezcamos la posición horizontal de la tabla. Esto determina a qué distancia del borde izquierdo del documento se colocará la tabla.

```csharp
table.AbsoluteHorizontalDistance = 10;
```

 Visualice esto como mover la tabla horizontalmente a lo largo de su documento.`AbsoluteHorizontalDistance` es la distancia exacta desde el borde izquierdo.

## Paso 4: Establecer la alineación vertical

También debemos configurar la alineación vertical de la tabla. Esto centrará la tabla verticalmente dentro del texto que la rodea.

```csharp
table.RelativeVerticalAlignment = VerticalAlignment.Center;
```

Imagina colgar un cuadro en una pared. Quieres asegurarte de que esté centrado verticalmente para que resulte atractivo estético. Este paso lo consigue.

## Paso 5: Guardar el documento modificado

Finalmente, después de posicionar la tabla, guarde el documento modificado.

```csharp
doc.Save(dataDir + "WorkingWithTables.FloatingTablePosition.docx");
```

Es como pulsar "Guardar" en el documento editado. Ahora se conservan todos los cambios.

## Conclusión

¡Y ya está! Acaba de aprender a controlar la posición flotante de las tablas en un documento de Word con Aspose.Words para .NET. Con estas habilidades, puede asegurarse de que sus tablas estén perfectamente posicionadas para mejorar la legibilidad y la estética de sus documentos. Siga experimentando y explorando las amplias capacidades de Aspose.Words para .NET.

## Preguntas frecuentes

### ¿Puedo configurar la distancia vertical de la tabla desde la parte superior de la página?

 Sí, puedes utilizar el`AbsoluteVerticalDistance` propiedad para establecer la distancia vertical de la tabla desde el borde superior de la página.

### ¿Cómo alineo la tabla a la derecha del documento?

 Para alinear la tabla a la derecha, puede configurar el`HorizontalAlignment` propiedad de la tabla a`HorizontalAlignment.Right`.

### ¿Es posible posicionar varias tablas de forma diferente en el mismo documento?

 ¡Por supuesto! Puedes acceder y establecer posiciones para varias tablas individualmente iterando a través de la`Tables` colección en el documento.

### ¿Puedo utilizar el posicionamiento relativo para la alineación horizontal?

Sí, Aspose.Words admite el posicionamiento relativo tanto para alineaciones horizontales como verticales utilizando propiedades como`RelativeHorizontalAlignment`.

### ¿Aspose.Words admite tablas flotantes en diferentes secciones de un documento?

Sí, puedes posicionar tablas flotantes en diferentes secciones accediendo a la sección específica y sus tablas dentro de tu documento.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
