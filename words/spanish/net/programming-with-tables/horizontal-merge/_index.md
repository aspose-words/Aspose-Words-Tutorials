---
"description": "Aprenda a combinar celdas horizontalmente en un documento de Word usando Aspose.Words para .NET con este tutorial detallado paso a paso."
"linktitle": "Fusión horizontal"
"second_title": "API de procesamiento de documentos de Aspose.Words"
"title": "Fusión horizontal"
"url": "/es/net/programming-with-tables/horizontal-merge/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Fusión horizontal

## Introducción

¡Hola! ¿Listo para sumergirte en el mundo de Aspose.Words para .NET? Hoy vamos a abordar una función súper útil: la combinación horizontal en tablas. Puede que suene un poco técnico, pero no te preocupes, te apoyo. Al final de este tutorial, serás un experto en la combinación de celdas en tus documentos de Word mediante programación. ¡Así que, manos a la obra!

## Prerrequisitos

Antes de entrar en materia, hay algunas cosas que necesitarás tener en cuenta:

1. Biblioteca Aspose.Words para .NET: Si aún no lo ha hecho, descargue la biblioteca Aspose.Words para .NET. Puede descargarla. [aquí](https://releases.aspose.com/words/net/).
2. Entorno de desarrollo: asegúrese de tener configurado un entorno de desarrollo adecuado, como Visual Studio.
3. Conocimientos básicos de C#: será beneficioso tener una comprensión básica de la programación en C#.

¡Una vez que tengas todo esto resuelto, estarás listo para comenzar!

## Importar espacios de nombres

Antes de profundizar en el código, asegurémonos de haber importado los espacios de nombres necesarios. En su proyecto de C#, asegúrese de incluir:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Muy bien, analicemos el proceso de fusión horizontal de celdas de tabla en un documento de Word usando Aspose.Words para .NET.

## Paso 1: Configuración del documento

Lo primero es lo primero, necesitamos crear un nuevo documento de Word e inicializarlo. `DocumentBuilder`:

```csharp
// Ruta a su directorio de documentos 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Este fragmento de código configura un nuevo documento y prepara el `DocumentBuilder` para la acción.

## Paso 2: Insertar la primera celda

A continuación, comenzamos insertando la primera celda y marcándola para la fusión horizontal:

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.First;
builder.Write("Text in merged cells.");
```

Aquí insertamos una nueva celda y la configuramos. `HorizontalMerge` propiedad a `CellMerge.First`, lo que indica que esta celda es el comienzo de una secuencia de celdas fusionadas.

## Paso 3: Insertar la celda fusionada

Ahora, insertamos la celda que se fusionará con la anterior:

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.Previous;
builder.EndRow();
```

Esta celda está configurada para fusionarse con la celda anterior mediante `CellMerge.Previous`. Observa cómo terminamos la fila con `builder.EndRow()`.

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

¡Y listo! Acabas de dominar el arte de combinar celdas horizontalmente en un documento de Word con Aspose.Words para .NET. Siguiendo estos pasos, podrás crear estructuras de tabla complejas fácilmente. Sigue experimentando y explorando las capacidades de Aspose.Words para que tus documentos sean tan dinámicos y flexibles como necesites. ¡Que disfrutes programando!

## Preguntas frecuentes

### ¿Qué es Aspose.Words para .NET?
Aspose.Words para .NET es una potente biblioteca que permite a los desarrolladores crear, editar y manipular documentos de Word mediante programación en aplicaciones .NET.

### ¿Puedo fusionar celdas verticalmente con Aspose.Words para .NET?
Sí, también puedes fusionar celdas verticalmente usando el `CellFormat.VerticalMerge` propiedad.

### ¿Aspose.Words para .NET es de uso gratuito?
Aspose.Words para .NET ofrece una prueba gratuita, pero para obtener la funcionalidad completa, necesitará adquirir una licencia. Puede obtener una licencia temporal. [aquí](https://purchase.aspose.com/temporary-license/).

### ¿Cómo puedo obtener más información sobre Aspose.Words para .NET?
Puede explorar la documentación detallada [aquí](https://reference.aspose.com/words/net/).

### ¿Dónde puedo obtener soporte para Aspose.Words para .NET?
Para cualquier consulta o problema, puede visitar el foro de soporte de Aspose [aquí](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}