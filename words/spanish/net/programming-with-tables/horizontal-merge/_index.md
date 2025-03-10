---
title: Fusión horizontal
linktitle: Fusión horizontal
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a combinar celdas horizontalmente en un documento de Word usando Aspose.Words para .NET con este tutorial detallado paso a paso.
weight: 10
url: /es/net/programming-with-tables/horizontal-merge/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Fusión horizontal

## Introducción

¡Hola! ¿Estás listo para sumergirte en el mundo de Aspose.Words para .NET? Hoy abordaremos una función muy útil: la combinación horizontal en tablas. Puede que esto suene un poco técnico, pero no te preocupes, te ayudaré. Al final de este tutorial, serás un profesional en la combinación de celdas en tus documentos de Word mediante programación. ¡Así que, manos a la obra y comencemos!

## Prerrequisitos

Antes de entrar en materia, hay algunas cosas que necesitarás tener en cuenta:

1. Biblioteca Aspose.Words para .NET: si aún no lo ha hecho, descargue la biblioteca Aspose.Words para .NET. Puede descargarla[aquí](https://releases.aspose.com/words/net/).
2. Entorno de desarrollo: asegúrese de tener configurado un entorno de desarrollo adecuado, como Visual Studio.
3. Conocimientos básicos de C#: será beneficioso tener conocimientos básicos de programación en C#.

¡Una vez que tengas todo esto resuelto, estarás listo para comenzar!

## Importar espacios de nombres

Antes de sumergirnos en el código, asegurémonos de que hemos importado los espacios de nombres necesarios. En su proyecto de C#, asegúrese de incluir lo siguiente:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Muy bien, analicemos el proceso de fusión horizontal de celdas de tabla en un documento de Word usando Aspose.Words para .NET.

## Paso 1: Configuración del documento

 Lo primero es lo primero, necesitamos crear un nuevo documento de Word e inicializarlo.`DocumentBuilder`:

```csharp
// Ruta al directorio de su documento
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Este fragmento de código configura un nuevo documento y prepara el`DocumentBuilder` para la acción.

## Paso 2: Insertar la primera celda

A continuación, comenzamos insertando la primera celda y marcándola para la fusión horizontal:

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.First;
builder.Write("Text in merged cells.");
```

 Aquí, insertamos una nueva celda y configuramos su`HorizontalMerge`propiedad a`CellMerge.First`, indicando que esta celda es el inicio de una secuencia de celdas fusionadas.

## Paso 3: Insertar la celda fusionada

Ahora, insertamos la celda que se fusionará con la anterior:

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.Previous;
builder.EndRow();
```

 Esta celda está configurada para fusionarse con la celda anterior mediante`CellMerge.Previous` . Observa cómo terminamos la fila con`builder.EndRow()`.

## Paso 4: Insertar celdas no fusionadas

Para ilustrar la diferencia, insertemos un par de celdas no fusionadas:

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.None;
builder.Write("Text in one cell.");
builder.InsertCell();
builder.Write("Text in another cell.");
builder.EndRow();
```

Aquí, insertamos dos celdas sin fusión horizontal. Esto muestra cómo se comportan las celdas cuando no forman parte de una secuencia fusionada.

## Paso 5: Terminar la mesa

Finalmente finalizamos la tabla y guardamos el documento:

```csharp
builder.EndTable();
doc.Save(dataDir + "WorkingWithTables.HorizontalMerge.docx");
```

Este fragmento de código completa la tabla y guarda el documento en el directorio especificado.

## Conclusión

¡Y ya está! Acaba de dominar el arte de fusionar celdas horizontalmente en un documento de Word con Aspose.Words para .NET. Si sigue estos pasos, podrá crear estructuras de tablas complejas con facilidad. Siga experimentando y explorando las capacidades de Aspose.Words para que sus documentos sean tan dinámicos y flexibles como necesite. ¡Que disfrute codificando!

## Preguntas frecuentes

### ¿Qué es Aspose.Words para .NET?
Aspose.Words para .NET es una potente biblioteca que permite a los desarrolladores crear, editar y manipular documentos de Word mediante programación en aplicaciones .NET.

### ¿Puedo fusionar celdas verticalmente con Aspose.Words para .NET?
 Sí, también puedes fusionar celdas verticalmente usando el`CellFormat.VerticalMerge` propiedad.

### ¿Aspose.Words para .NET es de uso gratuito?
 Aspose.Words para .NET ofrece una versión de prueba gratuita, pero para disfrutar de todas sus funciones, deberá adquirir una licencia. Puede obtener una licencia temporal[aquí](https://purchase.aspose.com/temporary-license/).

### ¿Cómo puedo obtener más información sobre Aspose.Words para .NET?
 Puede explorar la documentación detallada[aquí](https://reference.aspose.com/words/net/).

### ¿Dónde puedo obtener soporte para Aspose.Words para .NET?
 Para cualquier consulta o problema, puede visitar el foro de soporte de Aspose[aquí](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
