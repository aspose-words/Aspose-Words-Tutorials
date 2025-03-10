---
title: Asignación de rango de etiquetas XML de inicio de documento estructurado
linktitle: Asignación de rango de etiquetas XML de inicio de documento estructurado
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a vincular dinámicamente datos XML a etiquetas de documentos estructurados en Word con Aspose.Words para .NET. Siga nuestra guía paso a paso.
weight: 10
url: /es/net/programming-with-sdt/structured-document-tag-range-start-xml-mapping/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Asignación de rango de etiquetas XML de inicio de documento estructurado

## Introducción

¿Alguna vez ha deseado insertar dinámicamente datos XML en un documento de Word? ¡Pues está de suerte! Aspose.Words para .NET facilita esta tarea. En este tutorial, profundizaremos en la asignación de XML de inicio de rango de etiquetas de documentos estructurados. Esta función le permite vincular partes XML personalizadas a controles de contenido, lo que garantiza que el contenido de su documento se actualice sin problemas con sus datos XML. Listo para transformar sus documentos en obras maestras dinámicas.

## Prerrequisitos

Antes de pasar a la parte de codificación, asegurémonos de que tienes todo lo que necesitas:

1.  Biblioteca Aspose.Words para .NET: asegúrese de tener la última versión. Puede descargarla[aquí](https://releases.aspose.com/words/net/).
2. Entorno de desarrollo: Visual Studio o cualquier otro IDE que admita C#.
3. Conocimientos básicos de C#: Es imprescindible estar familiarizado con la programación en C#.
4. Documento de Word: un documento de Word de muestra con el que trabajar.

## Importar espacios de nombres

Lo primero es lo primero: importemos los espacios de nombres necesarios. Esto garantizará que tengamos acceso a todas las clases y métodos necesarios en Aspose.Words para .NET.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
using System.Text;
```

## Paso 1: Configurar el directorio de documentos

Todo proyecto necesita una base, ¿no? Aquí, configuramos la ruta hacia el directorio de documentos.

```csharp
// Ruta al directorio de su documento
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Paso 2: Cargue el documento de Word

A continuación, cargamos el documento de Word. Este es el documento en el que insertaremos nuestros datos XML.

```csharp
Document doc = new Document(dataDir + "Multi-section structured document tags.docx");
```

## Paso 3: Agregar parte XML personalizada

Necesitamos construir una parte XML que contenga los datos que queremos insertar y agregarla a la colección CustomXmlPart del documento. Esta parte XML personalizada servirá como fuente de datos para las etiquetas de nuestro documento estructurado.

### Creación de una parte XML

Primero, genere un ID único para la parte XML y defina su contenido.

```csharp
// Construya una parte XML que contenga datos y agréguela a la colección CustomXmlPart del documento.
string xmlPartId = Guid.NewGuid().ToString("B");
string xmlPartContent = "<root><text>Text element #1</text><text>Text element #2</text></root>";
CustomXmlPart xmlPart = doc.CustomXmlParts.Add(xmlPartId, xmlPartContent);
```

### Verificar el contenido de la parte XML

Para garantizar que la parte XML se agregue correctamente, imprimimos su contenido.

```csharp
Console.WriteLine(Encoding.UTF8.GetString(xmlPart.Data));
```

## Paso 4: Crear una etiqueta de documento estructurado

Una etiqueta de documento estructurado (SDT) es un control de contenido que se puede vincular a una parte XML. Aquí, creamos una SDT que mostrará el contenido de nuestra parte XML personalizada.

Primero, localice el inicio del rango SDT en el documento.

```csharp
StructuredDocumentTagRangeStart sdtRangeStart = (StructuredDocumentTagRangeStart)doc.GetChild(NodeType.StructuredDocumentTagRangeStart, 0, true);
```

## Paso 5: Establecer la asignación XML para el SDT

Ahora es el momento de vincular nuestra parte XML al SDT. Al establecer una asignación XML, especificamos qué parte de los datos XML se deben mostrar en el SDT.

 El XPath apunta al elemento específico de la parte XML que queremos mostrar. Aquí, apuntamos al segundo`<text>` elemento dentro de la`<root>` elemento.

```csharp
// Establezca una asignación para nuestro StructuredDocumentTag
sdtRangeStart.XmlMapping.SetMapping(xmlPart, "/root[1]/text[2]", null);
```

## Paso 6: Guardar el documento

Por último, guarde el documento para ver los cambios realizados. El SDT del documento de Word mostrará ahora el contenido XML especificado.

```csharp
doc.Save(dataDir + "WorkingWithSdt.StructuredDocumentTagRangeStartXmlMapping.docx");
```

## Conclusión

¡Y ya está! Ha asignado correctamente una parte XML a una etiqueta de documento estructurado en un documento de Word mediante Aspose.Words para .NET. Esta potente función le permite crear documentos dinámicos y basados en datos sin esfuerzo. Ya sea que esté generando informes, facturas o cualquier otro tipo de documento, la asignación de XML puede agilizar significativamente su flujo de trabajo.

## Preguntas frecuentes

### ¿Qué es una etiqueta de documento estructurado en Word?
Las etiquetas de documentos estructurados, también conocidas como controles de contenido, son contenedores para tipos específicos de contenido en documentos de Word. Se pueden utilizar para vincular datos, restringir la edición o guiar a los usuarios en la creación de documentos.

### ¿Cómo puedo actualizar el contenido de la parte XML dinámicamente?
 Puede actualizar el contenido de la parte XML modificando el`xmlPartContent` cadena antes de agregarla al documento. Simplemente actualice la cadena con los nuevos datos y agréguela al documento.`CustomXmlParts` recopilación.

### ¿Puedo vincular varias partes XML a diferentes SDT en el mismo documento?
Sí, puedes vincular varias partes XML a diferentes SDT en el mismo documento. Cada SDT puede tener su propia parte XML y asignación XPath.

### ¿Es posible mapear estructuras XML complejas a SDT?
¡Por supuesto! Puede asignar estructuras XML complejas a SDT mediante expresiones XPath detalladas que apunten con precisión a los elementos deseados dentro de la parte XML.

### ¿Cómo puedo eliminar una parte XML de un documento?
 Puede eliminar una parte XML llamando al método`Remove` método en el`CustomXmlParts` colección, pasando el`xmlPartId` de la parte XML que desea eliminar.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
