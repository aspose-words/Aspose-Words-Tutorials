---
title: Creación de una sección repetida de tabla asignada a una parte XML personalizada
linktitle: Creación de una sección repetida de tabla asignada a una parte XML personalizada
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a crear una tabla con una sección repetida asignada a un CustomXmlPart en un documento de Word usando Aspose.Words para .NET.
weight: 10
url: /es/net/programming-with-sdt/creating-table-repeating-section-mapped-to-custom-xml-part/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Creación de una sección repetida de tabla asignada a una parte XML personalizada

## Introducción

En este tutorial, repasaremos el proceso de creación de una tabla con una sección repetida que se asigna a una parte XML personalizada mediante Aspose.Words para .NET. Esto resulta particularmente útil para generar documentos de forma dinámica basados en datos estructurados.

## Prerrequisitos

Antes de comenzar, asegúrese de tener lo siguiente:
1.  Biblioteca Aspose.Words para .NET instalada. Puede descargarla desde[Sitio web de Aspose](https://releases.aspose.com/words/net/).
2. Un conocimiento básico de C# y XML.

## Importar espacios de nombres

Asegúrese de incluir los espacios de nombres necesarios en su proyecto:

```csharp
using Aspose.Words;
using Aspose.Words.Markup;
using Aspose.Words.Tables;
```

## Paso 1: Inicializar el documento y DocumentBuilder

 Primero, cree un nuevo documento e inicialice un`DocumentBuilder`:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Paso 2: Agregar parte XML personalizada

Agregue una parte XML personalizada al documento. Este XML contiene los datos que queremos asignar a nuestra tabla:

```csharp
CustomXmlPart xmlPart = doc.CustomXmlParts.Add("Books",
    "<books><book><title>Everyday Italian</title><author>Giada De Laurentiis</author></book>" +
    "<book><title>Harry Potter</title><author>J K. Rowling</author></book>" +
    "<book><title>Learning XML</title><author>Erik T. Ray</author></book></books>");
```

## Paso 3: Crear la estructura de la tabla

 A continuación, utilice el`DocumentBuilder` Para crear el encabezado de la tabla:

```csharp
Table table = builder.StartTable();
builder.InsertCell();
builder.Write("Title");
builder.InsertCell();
builder.Write("Author");
builder.EndRow();
builder.EndTable();
```

## Paso 4: Crear una sección repetida

 Crear un`StructuredDocumentTag` (SDT) para la sección repetida y asignarla a los datos XML:

```csharp
StructuredDocumentTag repeatingSectionSdt = new StructuredDocumentTag(doc, SdtType.RepeatingSection, MarkupLevel.Row);
repeatingSectionSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book", "");
table.AppendChild(repeatingSectionSdt);
```

## Paso 5: Crear un elemento de sección repetida

Cree un SDT para el elemento de sección repetida y agréguelo a la sección repetida:

```csharp
StructuredDocumentTag repeatingSectionItemSdt = new StructuredDocumentTag(doc, SdtType.RepeatingSectionItem, MarkupLevel.Row);
repeatingSectionSdt.AppendChild(repeatingSectionItemSdt);
Row row = new Row(doc);
repeatingSectionItemSdt.AppendChild(row);
```

## Paso 6: Asignar datos XML a celdas de tabla

Cree SDT para el título y el autor, asígnelos a los datos XML y añádalos a la fila:

```csharp
StructuredDocumentTag titleSdt = new StructuredDocumentTag(doc, SdtType.PlainText, MarkupLevel.Cell);
titleSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book[1]/title[1]", "");
row.AppendChild(titleSdt);

StructuredDocumentTag authorSdt = new StructuredDocumentTag(doc, SdtType.PlainText, MarkupLevel.Cell);
authorSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book[1]/author[1]", "");
row.AppendChild(authorSdt);
```

## Paso 7: Guardar el documento

Por último, guarde el documento en el directorio especificado:

```csharp
doc.Save(dataDir + "WorkingWithSdt.CreatingTableRepeatingSectionMappedToCustomXmlPart.docx");
```

## Conclusión

Si sigue estos pasos, habrá creado con éxito una tabla con una sección repetida asignada a una parte XML personalizada mediante Aspose.Words para .NET. Esto permite la generación de contenido dinámico basado en datos estructurados, lo que hace que la creación de documentos sea más flexible y eficaz.

## Preguntas frecuentes

### ¿Qué es un StructuredDocumentTag (SDT)?
Un SDT, también conocido como control de contenido, es una región delimitada en un documento que se utiliza para contener datos estructurados.

### ¿Puedo utilizar otros tipos de datos en la parte XML personalizada?
Sí, puedes estructurar tu parte XML personalizada con cualquier tipo de datos y mapearlos en consecuencia.

### ¿Cómo agrego más filas a la sección repetida?
La sección de repetición replica automáticamente la estructura de filas para cada elemento en la ruta XML asignada.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
