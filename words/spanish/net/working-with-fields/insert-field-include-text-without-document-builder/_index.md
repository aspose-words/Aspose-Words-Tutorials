---
title: Insertar campo Incluir texto sin generador de documentos
linktitle: Insertar campoIncludeText sin el generador de documentos
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a insertar un FieldIncludeText sin usar DocumentBuilder en Aspose.Words para .NET con nuestra guía detallada paso a paso.
weight: 10
url: /es/net/working-with-fields/insert-field-include-text-without-document-builder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Insertar campo Incluir texto sin generador de documentos

## Introducción

En el mundo de la automatización y manipulación de documentos, Aspose.Words para .NET se destaca como una herramienta poderosa. Hoy, profundizaremos en una guía detallada sobre cómo insertar un FieldIncludeText sin usar DocumentBuilder. Este tutorial lo guiará a través del proceso paso a paso, asegurándose de que comprenda cada parte del código y su propósito.

## Prerrequisitos

Antes de sumergirnos en el código, asegurémonos de que tienes todo lo que necesitas:

1.  Aspose.Words para .NET: Asegúrate de tener instalada la última versión. Puedes descargarla desde[aquí](https://releases.aspose.com/words/net/).
2. Entorno de desarrollo .NET: cualquier IDE compatible con .NET como Visual Studio.
3. Conocimientos básicos de C#: la familiaridad con la programación en C# le ayudará a seguir adelante.

## Importar espacios de nombres

Lo primero es lo primero: debemos importar los espacios de nombres necesarios. Estos espacios de nombres proporcionan acceso a las clases y métodos necesarios para manipular documentos de Word.

```csharp
using Aspose.Words;
using Aspose.Words.Fields;
```

Ahora, dividiremos el ejemplo en varios pasos. Explicaremos cada paso en detalle para garantizar la claridad.

## Paso 1: Establezca la ruta del directorio

El primer paso es definir la ruta al directorio de documentos. Allí se almacenarán y accederán sus documentos de Word.

```csharp
// La ruta al directorio de documentos.
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

## Paso 2: Crear el documento y el párrafo

A continuación, creamos un nuevo documento y un párrafo dentro de ese documento. Este párrafo contendrá el campo FieldIncludeText.

```csharp
// Crea el documento y el párrafo.
Document doc = new Document();
Paragraph para = new Paragraph(doc);
```

## Paso 3: Insertar campo FieldIncludeText

Ahora, insertamos el campo FieldIncludeText en el párrafo. Este campo permite incluir el texto de otro documento.

```csharp
// Insertar campo FieldIncludeText.
FieldIncludeText fieldIncludeText = (FieldIncludeText)para.AppendField(FieldType.FieldIncludeText, false);
```

## Paso 4: Establecer propiedades del campo

Necesitamos especificar las propiedades del campo FieldIncludeText. Esto incluye configurar el nombre del marcador y la ruta completa del documento de origen.

```csharp
fieldIncludeText.BookmarkName = "bookmark";
fieldIncludeText.SourceFullName = dataDir + "IncludeText.docx";
```

## Paso 5: Agregar párrafo al documento

Con el campo configurado, agregamos el párrafo al cuerpo de la primera sección del documento.

```csharp
doc.FirstSection.Body.AppendChild(para);
```

## Paso 6: Actualizar campo

Antes de guardar el documento, debemos actualizar FieldIncludeText para garantizar que extraiga el contenido correcto del documento de origen.

```csharp
fieldIncludeText.Update();
```

## Paso 7: Guardar el documento

Finalmente, guardamos el documento en el directorio especificado.

```csharp
doc.Save(dataDir + "InsertionFieldFieldIncludeTextWithoutDocumentBuilder.docx");
```

## Conclusión

¡Y ya está! Si sigue estos pasos, podrá insertar fácilmente un FieldIncludeText sin utilizar DocumentBuilder en Aspose.Words para .NET. Este enfoque proporciona una forma simplificada de incluir contenido de un documento en otro, lo que simplifica enormemente las tareas de automatización de documentos.

## Preguntas frecuentes

### ¿Qué es Aspose.Words para .NET?  
Aspose.Words para .NET es una potente biblioteca para trabajar con documentos de Word en aplicaciones .NET. Permite crear, editar y convertir documentos de forma programática.

### ¿Por qué utilizar FieldIncludeText?  
FieldIncludeText es útil para incluir dinámicamente contenido de un documento en otro, lo que permite documentos más modulares y fáciles de mantener.

### ¿Puedo utilizar este método para incluir texto de otros formatos de archivo?  
FieldIncludeText funciona específicamente con documentos de Word. Para otros formatos, es posible que necesites métodos o clases diferentes proporcionados por Aspose.Words.

### ¿Aspose.Words para .NET es compatible con .NET Core?  
Sí, Aspose.Words para .NET es compatible con .NET Framework, .NET Core y .NET 5/6.

### ¿Cómo puedo obtener una prueba gratuita de Aspose.Words para .NET?  
 Puede obtener una prueba gratuita desde[aquí](https://releases.aspose.com/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
