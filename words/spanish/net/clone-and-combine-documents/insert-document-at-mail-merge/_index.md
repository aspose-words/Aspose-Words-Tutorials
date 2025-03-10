---
title: Insertar documento en la combinación de correspondencia
linktitle: Insertar documento en la combinación de correspondencia
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a insertar documentos en campos de combinación de correspondencia utilizando Aspose.Words para .NET en este completo tutorial paso a paso.
weight: 10
url: /es/net/clone-and-combine-documents/insert-document-at-mail-merge/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Insertar documento en la combinación de correspondencia

## Introducción

¡Bienvenido al mundo de la automatización de documentos con Aspose.Words para .NET! ¿Alguna vez se preguntó cómo insertar documentos de forma dinámica en campos específicos dentro de un documento principal durante una operación de combinación de correspondencia? Bueno, está en el lugar correcto. Este tutorial lo guiará paso a paso a través del proceso de inserción de documentos en campos de combinación de correspondencia utilizando Aspose.Words para .NET. Es como armar un rompecabezas, donde cada pieza encaja perfectamente en su lugar. ¡Así que, vamos a sumergirnos en el proceso!

## Prerrequisitos

Antes de comenzar, asegúrese de tener lo siguiente:

1.  Aspose.Words para .NET: puedes[Descargue la última versión aquí](https://releases.aspose.com/words/net/) Si necesita comprar una licencia, puede hacerlo[aquí](https://purchase.aspose.com/buy) Alternativamente, puede obtener un[licencia temporal](https://purchase.aspose.com/temporary-license/) o pruébalo con un[prueba gratis](https://releases.aspose.com/).
2. Entorno de desarrollo: Visual Studio o cualquier otro IDE de C#.
3. Conocimientos básicos de C#: la familiaridad con la programación en C# hará que este tutorial sea muy fácil.

## Importar espacios de nombres

Lo primero es lo primero: deberás importar los espacios de nombres necesarios. Son como los componentes básicos de tu proyecto.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.MailMerging;
using System.Linq;
```

Dividamos el proceso en pasos manejables. Cada paso se basará en el anterior y lo llevará a una solución completa.

## Paso 1: Configuración de su directorio

Antes de poder comenzar a insertar documentos, debe definir la ruta a su directorio de documentos. Aquí es donde se almacenan sus documentos.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Paso 2: Cargar el documento principal

A continuación, cargará el documento principal. Este documento contiene los campos de combinación donde se insertarán otros documentos.

```csharp
Document mainDoc = new Document(dataDir + "Document insertion 1.docx");
```

## Paso 3: Configuración de la devolución de llamada de fusión de campos

Para gestionar el proceso de fusión, deberá configurar una función de devolución de llamada. Esta función será responsable de insertar documentos en los campos de fusión especificados.

```csharp
mainDoc.MailMerge.FieldMergingCallback = new InsertDocumentAtMailMergeHandler();
```

## Paso 4: Ejecutar la combinación de correspondencia

Ahora es el momento de ejecutar la combinación de correspondencia. Aquí es donde ocurre la magia. Deberá especificar el campo de combinación y el documento que se debe insertar en este campo.

```csharp
mainDoc.MailMerge.Execute(new[] { "Document_1" }, new object[] { dataDir + "Document insertion 2.docx" });
```

## Paso 5: Guardar el documento

Una vez finalizada la combinación de correspondencia, guardará el documento modificado. Este nuevo documento tendrá el contenido insertado exactamente donde lo desea.

```csharp
mainDoc.Save(dataDir + "CloneAndCombineDocuments.InsertDocumentAtMailMerge.doc");
```

## Paso 6: Creación del controlador de devolución de llamada

El controlador de devolución de llamada es una clase que realiza un procesamiento especial para el campo de combinación. Carga el documento especificado en el valor del campo y lo inserta en el campo de combinación actual.

```csharp
private class InsertDocumentAtMailMergeHandler : IFieldMergingCallback
{
    void IFieldMergingCallback.FieldMerging(FieldMergingArgs args)
    {
        if (args.DocumentFieldName == "Document_1")
        {
            DocumentBuilder builder = new DocumentBuilder(args.Document);
            builder.MoveToMergeField(args.DocumentFieldName);

            Document subDoc = new Document((string)args.FieldValue);
            InsertDocument(builder.CurrentParagraph, subDoc);

            if (!builder.CurrentParagraph.HasChildNodes)
                builder.CurrentParagraph.Remove();

            args.Text = null;
        }
    }
}
```

## Paso 7: Inserción del documento

Este método inserta el documento especificado en el párrafo o celda de la tabla actual.

```csharp
private static void InsertDocument(Node insertionDestination, Document docToInsert)
{
    if (insertionDestination.NodeType == NodeType.Paragraph || insertionDestination.NodeType == NodeType.Table)
    {
        CompositeNode destinationParent = insertionDestination.ParentNode;
        NodeImporter importer = new NodeImporter(docToInsert, insertionDestination.Document, ImportFormatMode.KeepSourceFormatting);

        foreach (Section srcSection in docToInsert.Sections.OfType<Section>())
        foreach (Node srcNode in srcSection.Body)
        {
            if (srcNode.NodeType == NodeType.Paragraph)
            {
                Paragraph para = (Paragraph)srcNode;
                if (para.IsEndOfSection && !para.HasChildNodes)
                    continue;
            }

            Node newNode = importer.ImportNode(srcNode, true);
            destinationParent.InsertAfter(newNode, insertionDestination);
            insertionDestination = newNode;
        }
    }
    else
    {
        throw new ArgumentException("The destination node should be either a paragraph or table.");
    }
}
```

## Conclusión

¡Y ya está! Ha insertado correctamente documentos en campos específicos durante una operación de combinación de correspondencia utilizando Aspose.Words para .NET. Esta potente función puede ahorrarle mucho tiempo y esfuerzo, especialmente cuando trabaja con grandes volúmenes de documentos. Piense en ello como si tuviera un asistente personal que se encarga de todo el trabajo pesado por usted. Así que, adelante, pruébelo. ¡Que disfrute codificando!

## Preguntas frecuentes

### ¿Puedo insertar varios documentos en diferentes campos de combinación?
Sí, puedes hacerlo. Simplemente especifica los campos de combinación apropiados y las rutas de documentos correspondientes en el`MailMerge.Execute` método.

### ¿Es posible formatear el documento insertado de forma diferente al documento principal?
 ¡Por supuesto! Puedes utilizar el`ImportFormatMode` parámetro en el`NodeImporter` para controlar el formato.

### ¿Qué pasa si el nombre del campo de combinación es dinámico?
Puede manejar nombres de campos de combinación dinámica pasándolos como parámetros al controlador de devolución de llamada.

### ¿Puedo utilizar este método con diferentes formatos de archivo?
Sí, Aspose.Words admite varios formatos de archivos, incluidos DOCX, PDF y más.

### ¿Cómo manejo los errores durante el proceso de inserción de documentos?
Implemente el manejo de errores en su controlador de devolución de llamada para administrar cualquier excepción que pueda ocurrir.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
