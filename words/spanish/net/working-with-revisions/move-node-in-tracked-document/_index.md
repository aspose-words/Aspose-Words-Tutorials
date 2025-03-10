---
title: Mover nodo en documento rastreado
linktitle: Mover nodo en documento rastreado
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a mover nodos en un documento de Word con seguimiento mediante Aspose.Words para .NET con nuestra guía detallada paso a paso. Perfecta para desarrolladores.
weight: 10
url: /es/net/working-with-revisions/move-node-in-tracked-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Mover nodo en documento rastreado

## Introducción

¡Hola, entusiastas de Aspose.Words! Si alguna vez necesitaron mover un nodo en un documento de Word mientras hacían un seguimiento de las revisiones, están en el lugar correcto. Hoy, profundizaremos en cómo lograr esto usando Aspose.Words para .NET. No solo aprenderán el proceso paso a paso, sino que también obtendrán algunos consejos y trucos para que la manipulación de documentos sea fluida y eficiente.

## Prerrequisitos

Antes de ponernos manos a la obra con el código, asegurémonos de que tienes todo lo que necesitas:

-  Aspose.Words para .NET: Descárgalo[aquí](https://releases.aspose.com/words/net/).
- Entorno .NET: asegúrese de tener configurado un entorno de desarrollo .NET compatible.
- Conocimientos básicos de C#: este tutorial asume que tienes un conocimiento básico de C#.

¿Lo tienes todo? ¡Genial! Pasemos a los espacios de nombres que necesitamos importar.

## Importar espacios de nombres

Lo primero es lo primero: debemos importar los espacios de nombres necesarios. Son esenciales para trabajar con Aspose.Words y manejar nodos de documentos.

```csharp
using Aspose.Words;
using System;
```

Bien, vamos a dividir el proceso en pasos manejables. Cada paso se explicará en detalle para garantizar que comprendas lo que sucede en cada punto.

## Paso 1: Inicializar el documento

 Para comenzar, necesitamos inicializar un nuevo documento y utilizar un`DocumentBuilder` para añadir algunos párrafos.

```csharp
// La ruta al directorio de documentos.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Añadiendo algunos párrafos
builder.Writeln("Paragraph 1");
builder.Writeln("Paragraph 2");
builder.Writeln("Paragraph 3");
builder.Writeln("Paragraph 4");
builder.Writeln("Paragraph 5");
builder.Writeln("Paragraph 6");

// Comprueba el recuento de párrafos iniciales
Body body = doc.FirstSection.Body;
Console.WriteLine("Paragraph count: {0}", body.Paragraphs.Count);
```

## Paso 2: Comience a realizar un seguimiento de las revisiones

A continuación, debemos comenzar a realizar un seguimiento de las revisiones. Esto es fundamental, ya que nos permite ver los cambios realizados en el documento.

```csharp
// Comience a realizar un seguimiento de las revisiones
doc.StartTrackRevisions("Author", new DateTime(2020, 12, 23, 14, 0, 0));
```

## Paso 3: Mover nodos

Ahora viene la parte principal de nuestra tarea: mover un nodo de una ubicación a otra. Moveremos el tercer párrafo y lo colocaremos antes del primer párrafo.

```csharp
// Define el nodo que se va a mover y su rango final
Node node = body.Paragraphs[3];
Node endNode = body.Paragraphs[5].NextSibling;
Node referenceNode = body.Paragraphs[0];

// Mueva los nodos dentro del rango definido
while (node != endNode)
{
    Node nextNode = node.NextSibling;
    body.InsertBefore(node, referenceNode);
    node = nextNode;
}
```

## Paso 4: Detener el seguimiento de las revisiones

Una vez que hayamos movido los nodos, debemos dejar de rastrear revisiones.

```csharp
// Detener el seguimiento de las revisiones
doc.StopTrackRevisions();
```

## Paso 5: Guardar el documento

Por último, guardemos nuestro documento modificado en el directorio especificado.

```csharp
// Guardar el documento modificado
doc.Save(dataDir + "WorkingWithRevisions.MoveNodeInTrackedDocument.docx");

// Generar el recuento final de párrafos
Console.WriteLine("Paragraph count: {0}", body.Paragraphs.Count);
```

## Conclusión

¡Y ya está! Has movido con éxito un nodo en un documento con seguimiento mediante Aspose.Words para .NET. Esta potente biblioteca facilita la manipulación programática de documentos de Word. Ya sea que estés creando, editando o haciendo un seguimiento de los cambios, Aspose.Words te ayudará. Así que, adelante, pruébalo. ¡Que disfrutes codificando!

## Preguntas frecuentes

### ¿Qué es Aspose.Words para .NET?

Aspose.Words para .NET es una biblioteca de clases para trabajar con documentos de Word de forma programática. Permite a los desarrolladores crear, editar, convertir e imprimir documentos de Word dentro de aplicaciones .NET.

### ¿Cómo puedo realizar un seguimiento de las revisiones en un documento de Word usando Aspose.Words?

 Para realizar un seguimiento de las revisiones, utilice el`StartTrackRevisions` método en el`Document` objeto. Esto permitirá el seguimiento de revisiones, mostrando cualquier cambio realizado en el documento.

### ¿Puedo mover varios nodos en Aspose.Words?

Sí, puedes mover varios nodos iterándolos y usando métodos como`InsertBefore` o`InsertAfter` para colocarlos en el lugar deseado.

### ¿Cómo puedo dejar de realizar un seguimiento de las revisiones en Aspose.Words?

 Utilice el`StopTrackRevisions` método en el`Document` objeto de detener el seguimiento de revisiones.

### ¿Dónde puedo encontrar más documentación sobre Aspose.Words para .NET?

 Puede encontrar documentación detallada[aquí](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
