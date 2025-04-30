---
"description": "Aprenda a insertar documentos en campos de combinación de correspondencia utilizando Aspose.Words para .NET en este completo tutorial paso a paso."
"linktitle": "Insertar documento en la combinación de correspondencia"
"second_title": "API de procesamiento de documentos de Aspose.Words"
"title": "Insertar documento en la combinación de correspondencia"
"url": "/es/net/clone-and-combine-documents/insert-document-at-mail-merge/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Insertar documento en la combinación de correspondencia

## Introducción

¡Bienvenido al mundo de la automatización de documentos con Aspose.Words para .NET! ¿Alguna vez te has preguntado cómo insertar documentos dinámicamente en campos específicos de un documento principal durante una operación de combinación de correspondencia? Estás en el lugar correcto. Este tutorial te guiará paso a paso en el proceso de inserción de documentos en campos de combinación de correspondencia usando Aspose.Words para .NET. Es como armar un rompecabezas, donde cada pieza encaja a la perfección. ¡Vamos a ello!

## Prerrequisitos

Antes de comenzar, asegúrese de tener lo siguiente:

1. Aspose.Words para .NET: Puedes [Descargue la última versión aquí](https://releases.aspose.com/words/net/)Si necesita comprar una licencia, puede hacerlo [aquí](https://purchase.aspose.com/buy)Alternativamente, puede obtener un [licencia temporal](https://purchase.aspose.com/temporary-license/) pruébalo con un [prueba gratuita](https://releases.aspose.com/).
2. Entorno de desarrollo: Visual Studio o cualquier otro IDE de C#.
3. Conocimientos básicos de C#: la familiaridad con la programación en C# hará que este tutorial sea muy sencillo.

## Importar espacios de nombres

Primero, deberás importar los espacios de nombres necesarios. Estos son los componentes básicos de tu proyecto.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.MailMerging;
using System.Linq;
```

Dividamos el proceso en pasos manejables. Cada paso se basará en el anterior, lo que le llevará a una solución completa.

## Paso 1: Configuración de su directorio

Antes de empezar a insertar documentos, debe definir la ruta de acceso a su directorio de documentos. Aquí es donde se almacenan.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Paso 2: Cargar el documento principal

A continuación, cargará el documento principal. Este documento contiene los campos de combinación donde se insertarán otros documentos.

```csharp
Document mainDoc = new Document(dataDir + "Document insertion 1.docx");
```

## Paso 3: Configuración de la devolución de llamada de fusión de campos

Para gestionar el proceso de fusión, deberá configurar una función de devolución de llamada. Esta función se encargará de insertar los documentos en los campos de fusión especificados.

```csharp
mainDoc.MailMerge.FieldMergingCallback = new InsertDocumentAtMailMergeHandler();
```

## Paso 4: Ejecución de la combinación de correspondencia

Ahora es el momento de ejecutar la combinación de correspondencia. Aquí es donde ocurre la magia. Especificarás el campo de combinación y el documento que se insertará en él.

```csharp
mainDoc.MailMerge.Execute(new[] { "Document_1" }, new object[] { dataDir + "Document insertion 2.docx" });
```

## Paso 5: Guardar el documento

Una vez finalizada la combinación de correspondencia, guardará el documento modificado. Este nuevo documento tendrá el contenido insertado justo donde lo desee.

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

¡Y listo! Has insertado documentos correctamente en campos específicos durante una operación de combinación de correspondencia con Aspose.Words para .NET. Esta potente función puede ahorrarte mucho tiempo y esfuerzo, especialmente al trabajar con grandes volúmenes de documentos. Piensa en ello como si tuvieras un asistente personal que se encarga de todo el trabajo pesado por ti. Así que, adelante, pruébalo. ¡Que disfrutes programando!

## Preguntas frecuentes

### ¿Puedo insertar varios documentos en diferentes campos de combinación?
Sí, puedes. Simplemente especifica los campos de combinación apropiados y las rutas de los documentos correspondientes en el `MailMerge.Execute` método.

### ¿Es posible formatear el documento insertado de forma diferente al documento principal?
¡Por supuesto! Puedes usar el `ImportFormatMode` parámetro en el `NodeImporter` para controlar el formato.

### ¿Qué pasa si el nombre del campo de combinación es dinámico?
Puede manejar nombres de campos de combinación dinámica pasándolos como parámetros al controlador de devolución de llamada.

### ¿Puedo utilizar este método con diferentes formatos de archivos?
Sí, Aspose.Words admite varios formatos de archivos, incluidos DOCX, PDF y más.

### ¿Cómo manejo los errores durante el proceso de inserción de documentos?
Implemente el manejo de errores en su controlador de devolución de llamada para administrar cualquier excepción que pueda ocurrir.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}