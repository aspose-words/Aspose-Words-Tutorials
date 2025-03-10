---
title: Agregar forma de grupo
linktitle: Agregar forma de grupo
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a agregar formas de grupo a documentos de Word usando Aspose.Words para .NET con este completo tutorial paso a paso.
weight: 10
url: /es/net/programming-with-shapes/add-group-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Agregar forma de grupo

## Introducción

Crear documentos complejos con elementos visuales enriquecidos puede ser a veces una tarea abrumadora, especialmente cuando se trata de formas de grupo. ¡Pero no temas! Aspose.Words para .NET simplifica este proceso, haciéndolo muy fácil. En este tutorial, te guiaremos por los pasos para agregar formas de grupo a tus documentos de Word. ¿Listo para comenzar? ¡Comencemos!

## Prerrequisitos

Antes de comenzar, asegúrese de tener lo siguiente:

1.  Aspose.Words para .NET: Puedes descargarlo desde[Página de lanzamiento de Aspose](https://releases.aspose.com/words/net/).
2. Entorno de desarrollo: Visual Studio o cualquier otro IDE compatible con .NET.
3. Comprensión básica de C#: la familiaridad con la programación en C# es una ventaja.

## Importar espacios de nombres

Para comenzar, debemos importar los espacios de nombres necesarios en nuestro proyecto. Estos espacios de nombres brindan acceso a las clases y métodos necesarios para manipular documentos de Word con Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Paso 1: Inicializar el documento

Lo primero es lo primero: vamos a inicializar un nuevo documento de Word. Piense en esto como si estuviéramos creando un lienzo en blanco donde agregaremos las formas de nuestro grupo.

```csharp
// Ruta al directorio de su documento
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
doc.EnsureMinimum();
```

 Aquí,`EnsureMinimum()` Agrega un conjunto mínimo de nodos necesarios para el documento.

## Paso 2: Crear el objeto GroupShape

 A continuación, necesitamos crear un`GroupShape`objeto. Este objeto servirá como contenedor para otras formas, permitiéndonos agruparlas.

```csharp
GroupShape groupShape = new GroupShape(doc);
```

## Paso 3: Agregar formas al GroupShape

 Ahora, agreguemos formas individuales a nuestro`GroupShape` Contenedor. Comenzaremos con una forma de borde acentuado y luego agregaremos una forma de botón de acción.

### Cómo agregar una forma de borde con acento

```csharp
Shape accentBorderShape = new Shape(doc, ShapeType.AccentBorderCallout1)
{
    Width = 100,
    Height = 100
};
groupShape.AppendChild(accentBorderShape);
```

 Este fragmento de código crea una forma de borde de acento con un ancho y una altura de 100 unidades y la agrega a la`GroupShape`.

### Cómo agregar una forma de botón de acción

```csharp
Shape actionButtonShape = new Shape(doc, ShapeType.ActionButtonBeginning)
{
    Left = 100,
    Width = 100,
    Height = 200
};
groupShape.AppendChild(actionButtonShape);
```

 Aquí, creamos una forma de botón de acción, la posicionamos y la agregamos a nuestro`GroupShape`.

## Paso 4: Defina las dimensiones de GroupShape

 Para garantizar que nuestras formas encajen bien dentro del grupo, necesitamos establecer las dimensiones de las`GroupShape`.

```csharp
groupShape.Width = 200;
groupShape.Height = 200;
groupShape.CoordSize = new Size(200, 200);
```

 Esto define el ancho y la altura de la`GroupShape` como 200 unidades y establece el tamaño de las coordenadas en consecuencia.

## Paso 5: Insertar la GroupShape en el documento

 Ahora, insertemos nuestro`GroupShape` en el documento usando`DocumentBuilder`.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
builder.InsertNode(groupShape);
```

`DocumentBuilder` Proporciona una forma sencilla de agregar nodos, incluidas formas, al documento.

## Paso 6: Guardar el documento

Por último, guarde el documento en el directorio especificado.

```csharp
doc.Save(dataDir + "WorkingWithShapes.AddGroupShape.docx");
```

¡Y ya lo tienes! Tu documento con formas de grupo está listo.

## Conclusión

Agregar formas de grupo a sus documentos de Word no tiene por qué ser un proceso complicado. Con Aspose.Words para .NET, puede crear y manipular formas con facilidad, lo que hará que sus documentos sean visualmente más atractivos y funcionales. Siga los pasos que se describen en este tutorial y se convertirá en un profesional en poco tiempo.

## Preguntas frecuentes

### ¿Puedo agregar más de dos formas a un GroupShape?
 Sí, puedes agregar tantas formas como necesites a un`GroupShape` . Solo usa el`AppendChild` método para cada forma.

### ¿Es posible aplicar estilo a las formas dentro de un GroupShape?
 ¡Por supuesto! Cada forma se puede diseñar individualmente utilizando las propiedades disponibles en el`Shape` clase.

### ¿Cómo posiciono el GroupShape dentro del documento?
 Puedes posicionar el`GroupShape` estableciendo su`Left` y`Top` propiedades.

### ¿Puedo agregar texto a las formas dentro de GroupShape?
 Sí, puedes agregar texto a las formas usando el`AppendChild` método para agregar un`Paragraph` que contiene`Run` nodos con texto.

### ¿Es posible agrupar formas dinámicamente según la entrada del usuario?
Sí, puedes crear y agrupar formas dinámicamente según la entrada del usuario ajustando las propiedades y los métodos en consecuencia.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
