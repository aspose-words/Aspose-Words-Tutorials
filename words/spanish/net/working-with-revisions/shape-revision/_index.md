---
"description": "Aprenda a gestionar las revisiones de formas en documentos de Word con Aspose.Words para .NET con esta guía completa. Domine el seguimiento de cambios, la inserción de formas y mucho más."
"linktitle": "Revisión de la forma"
"second_title": "API de procesamiento de documentos de Aspose.Words"
"title": "Revisión de la forma"
"url": "/es/net/working-with-revisions/shape-revision/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Revisión de la forma

## Introducción

Editar documentos de Word mediante programación puede ser una tarea abrumadora, especialmente al gestionar formas. Ya sea que esté creando informes, diseñando plantillas o simplemente automatizando la creación de documentos, la capacidad de rastrear y administrar las revisiones de formas es crucial. Aspose.Words para .NET ofrece una potente API para que este proceso sea fluido y eficiente. En este tutorial, profundizaremos en los detalles de la revisión de formas en documentos de Word, asegurándonos de que cuente con las herramientas y los conocimientos necesarios para gestionar sus documentos con facilidad.

## Prerrequisitos

Antes de sumergirnos en el código, asegurémonos de que tienes todo lo que necesitas:

- Aspose.Words para .NET: Asegúrate de tener instalada la biblioteca Aspose.Words. Puedes... [Descárgalo aquí](https://releases.aspose.com/words/net/).
- Entorno de desarrollo: debe tener configurado un entorno de desarrollo, como Visual Studio.
- Comprensión básica de C#: familiaridad con el lenguaje de programación C# y conceptos básicos de programación orientada a objetos.
- Documento de Word: un documento de Word con el que trabajar, o puedes crear uno durante el tutorial.

## Importar espacios de nombres

Primero, importemos los espacios de nombres necesarios. Estos nos darán acceso a las clases y métodos necesarios para gestionar documentos y formas de Word.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Paso 1: Configuración del directorio de documentos

Antes de empezar a trabajar con formas, debemos definir la ruta de acceso a nuestro directorio de documentos. Aquí guardaremos los documentos modificados.

```csharp
// La ruta al directorio de documentos.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Paso 2: Crear un nuevo documento

Creemos un nuevo documento de Word donde insertaremos y revisaremos formas.

```csharp
Document doc = new Document();
```

## Paso 3: Insertar una forma en línea

Comenzaremos insertando una forma en línea en nuestro documento sin seguimiento de revisiones. Una forma en línea se adapta al texto.

```csharp
Shape shape = new Shape(doc, ShapeType.Cube);
shape.WrapType = WrapType.Inline;
shape.Width = 100.0;
shape.Height = 100.0;
doc.FirstSection.Body.FirstParagraph.AppendChild(shape);
```

## Paso 4: Comenzar a realizar un seguimiento de las revisiones

Para rastrear los cambios en nuestro documento, necesitamos habilitar el seguimiento de revisiones. Esto es esencial para identificar las modificaciones realizadas en las formas.

```csharp
doc.StartTrackRevisions("John Doe");
```

## Paso 5: Insertar otra forma con revisiones

Ahora que el seguimiento de revisiones está habilitado, insertemos otra forma. Esta vez, se registrarán todos los cambios.

```csharp
shape = new Shape(doc, ShapeType.Sun);
shape.WrapType = WrapType.Inline;
shape.Width = 100.0;
shape.Height = 100.0;
doc.FirstSection.Body.FirstParagraph.AppendChild(shape);
```

## Paso 6: Recuperar y modificar formas

Podemos recuperar todas las formas del documento y modificarlas según sea necesario. Aquí, obtendremos las formas y eliminaremos la primera.

```csharp
List<Shape> shapes = doc.GetChildNodes(NodeType.Shape, true).Cast<Shape>().ToList();
shapes[0].Remove();
```

## Paso 7: Guardar el documento

Después de realizar los cambios, debemos guardar el documento. Esto garantiza que se guarden todas las revisiones y modificaciones.

```csharp
doc.Save(dataDir + "Revision shape.docx");
```

## Paso 8: Manejo de revisiones de movimientos de forma

Cuando se mueve una forma, Aspose.Words lo registra como una revisión. Esto significa que habrá dos instancias de la forma: una en su ubicación original y otra en su nueva ubicación.

```csharp
doc = new Document(dataDir + "Revision shape.docx");
shapes = doc.GetChildNodes(NodeType.Shape, true).Cast<Shape>().ToList();
```

## Conclusión

¡Y listo! Has aprendido a gestionar las revisiones de formas en documentos de Word con Aspose.Words para .NET. Ya sea que administres plantillas de documentos, automatices informes o simplemente realices un seguimiento de los cambios, estas habilidades son invaluables. Siguiendo esta guía paso a paso, no solo dominarás los conceptos básicos, sino que también adquirirás conocimientos sobre técnicas más avanzadas de gestión de documentos.

## Preguntas frecuentes

### ¿Qué es Aspose.Words para .NET?
Aspose.Words para .NET es una potente biblioteca que permite a los desarrolladores crear, modificar y convertir documentos de Word mediante programación utilizando C#.

### ¿Puedo realizar un seguimiento de los cambios realizados en otros elementos de un documento de Word?
Sí, Aspose.Words para .NET admite el seguimiento de cambios en varios elementos, incluidos texto, tablas y más.

### ¿Cómo puedo obtener una prueba gratuita de Aspose.Words para .NET?
Puede obtener una prueba gratuita de Aspose.Words para .NET [aquí](https://releases.aspose.com/).

### ¿Es posible aceptar o rechazar revisiones programáticamente?
Sí, Aspose.Words para .NET proporciona métodos para aceptar o rechazar revisiones mediante programación.

### ¿Puedo usar Aspose.Words para .NET con otros lenguajes .NET además de C#?
¡Por supuesto! Aspose.Words para .NET se puede usar con cualquier lenguaje .NET, incluyendo VB.NET y F#.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}