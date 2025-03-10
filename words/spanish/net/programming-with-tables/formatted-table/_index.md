---
title: Tabla formateada
linktitle: Tabla formateada
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a crear y formatear tablas en documentos de Word usando Aspose.Words para .NET con esta guía detallada paso a paso.
weight: 10
url: /es/net/programming-with-tables/formatted-table/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tabla formateada

## Introducción

Crear y formatear tablas en documentos de Word mediante programación puede parecer una tarea abrumadora, pero con Aspose.Words para .NET, se vuelve sencillo y manejable. En este tutorial, le mostraremos cómo crear una tabla con formato en un documento de Word utilizando Aspose.Words para .NET. Cubriremos todo, desde la configuración de su entorno hasta cómo guardar su documento con una tabla con un formato atractivo.

## Prerrequisitos

Antes de sumergirnos en el código, asegurémonos de que tienes todo lo que necesitas:

1. Biblioteca Aspose.Words para .NET: Descárguela desde[aquí](https://releases.aspose.com/words/net/).
2. Entorno de desarrollo: un IDE como Visual Studio.
3. .NET Framework: asegúrese de tener .NET Framework instalado en su máquina.

## Importar espacios de nombres

Antes de escribir el código real, debes importar los espacios de nombres necesarios:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Tables;
```

## Paso 1: Configurar el directorio de documentos

Primero debes definir la ruta donde se guardará tu documento.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Reemplazar`"YOUR DOCUMENT DIRECTORY"` con la ruta real donde desea guardar el documento.

## Paso 2: Inicializar el documento y DocumentBuilder

Ahora, inicialice un nuevo documento y un objeto DocumentBuilder.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 El`DocumentBuilder` es una clase auxiliar que simplifica el proceso de creación de documentos.

## Paso 3: Iniciar la tabla

 A continuación, comience a crear la tabla utilizando el`StartTable` método.

```csharp
Table table = builder.StartTable();
builder.InsertCell();
```

Insertar una celda es necesario para comenzar la tabla.

## Paso 4: Aplicar formato a toda la tabla

Puede aplicar un formato que afecte a toda la tabla. Por ejemplo, establecer la sangría izquierda:

```csharp
table.LeftIndent = 20.0;
```

## Paso 5: Formatear la fila del encabezado

Establezca la altura, la alineación y otras propiedades para la fila del encabezado.

```csharp
builder.RowFormat.Height = 40.0;
builder.RowFormat.HeightRule = HeightRule.AtLeast;
builder.CellFormat.Shading.BackgroundPatternColor = Color.FromArgb(198, 217, 241);
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;
builder.Font.Size = 16;
builder.Font.Name = "Arial";
builder.Font.Bold = true;
builder.CellFormat.Width = 100.0;
builder.Write("Header Row,\n Cell 1");
```

En este paso, hacemos que la fila del encabezado se destaque estableciendo un color de fondo, un tamaño de fuente y una alineación.

## Paso 6: Insertar celdas de encabezado adicionales

Insertar más celdas para la fila de encabezado:

```csharp
builder.InsertCell();
builder.Write("Header Row,\n Cell 2");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Header Row,\n Cell 3");
builder.EndRow();
```

## Paso 7: Dar formato a las filas del cuerpo

Después de configurar el encabezado, formatee el cuerpo de la tabla:

```csharp
builder.CellFormat.Shading.BackgroundPatternColor = Color.White;
builder.CellFormat.Width = 100.0;
builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;
builder.RowFormat.Height = 30.0;
builder.RowFormat.HeightRule = HeightRule.Auto;
```

## Paso 8: Insertar filas del cuerpo

Insertar las filas del cuerpo con contenido:

```csharp
builder.InsertCell();
builder.Font.Size = 12;
builder.Font.Bold = false;
builder.Write("Row 1, Cell 1 Content");
builder.InsertCell();
builder.Write("Row 1, Cell 2 Content");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Row 1, Cell 3 Content");
builder.EndRow();
```

Repita para filas adicionales:

```csharp
builder.InsertCell();
builder.CellFormat.Width = 100.0;
builder.Write("Row 2, Cell 1 Content");
builder.InsertCell();
builder.Write("Row 2, Cell 2 Content");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Row 2, Cell 3 Content.");
builder.EndRow();
builder.EndTable();
```

## Paso 9: Guardar el documento

Por último, guarde el documento en el directorio especificado:

```csharp
doc.Save(dataDir + "WorkingWithTables.FormattedTable.docx");
```

Esto creará y guardará un documento de Word con la tabla formateada.

## Conclusión

¡Y ya está! Siguiendo estos pasos, puedes crear una tabla con el formato correcto en un documento de Word usando Aspose.Words para .NET. Esta potente biblioteca facilita la manipulación programática de documentos de Word, lo que te permite ahorrar tiempo y esfuerzo.

## Preguntas frecuentes

### ¿Qué es Aspose.Words para .NET?
Aspose.Words para .NET es una potente biblioteca para crear, editar y convertir documentos de Word mediante programación.

### ¿Puedo usar diferentes colores para diferentes filas?
Sí, puede aplicar diferentes formatos, incluidos colores, a diferentes filas o celdas.

### ¿Aspose.Words para .NET es gratuito?
 Aspose.Words para .NET es una biblioteca paga, pero puedes obtener una[prueba gratis](https://releases.aspose.com/).

### ¿Cómo puedo obtener soporte para Aspose.Words para .NET?
 Puede obtener ayuda de la[Foros de la comunidad Aspose](https://forum.aspose.com/c/words/8).

### ¿Puedo crear otros tipos de documentos con Aspose.Words para .NET?
Sí, Aspose.Words para .NET admite varios formatos de documentos, incluidos PDF, HTML y TXT.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
