---
title: Disposición en celda
linktitle: Disposición en celda
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a configurar el diseño de una celda con Aspose.Words para .NET con esta guía completa. Perfecta para desarrolladores que buscan personalizar documentos de Word.
weight: 10
url: /es/net/programming-with-shapes/layout-in-cell/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Disposición en celda

## Introducción

Si alguna vez ha deseado ajustar el diseño de las celdas de una tabla en documentos de Word mediante programación, está en el lugar correcto. Hoy, analizaremos en profundidad cómo configurar el diseño de una celda mediante Aspose.Words para .NET. Repasaremos un ejemplo práctico, desglosándolo paso a paso para que pueda seguirlo con facilidad.

## Prerrequisitos

Antes de pasar al código, asegurémonos de que tienes todo lo que necesitas:

1.  Aspose.Words para .NET: asegúrese de tener instalada la biblioteca Aspose.Words para .NET. Si no la tiene, puede[Descárgalo aquí](https://releases.aspose.com/words/net/).
2. Entorno de desarrollo: necesitará un entorno de desarrollo configurado con .NET. Visual Studio es una excelente opción si busca recomendaciones.
3. Conocimientos básicos de C#: si bien explicaré cada paso, una comprensión básica de C# te ayudará a seguir el proceso más fácilmente.
4.  Directorio de documentos: prepara una ruta de directorio donde guardarás tus documentos. Nos referiremos a esto como`YOUR DOCUMENT DIRECTORY`.

## Importar espacios de nombres

Para comenzar, asegúrese de importar los espacios de nombres necesarios en su proyecto:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

Dividamos el proceso en pasos manejables.

## Paso 1: Crear un nuevo documento

 Primero, crearemos un nuevo documento de Word e inicializaremos un`DocumentBuilder` objeto que nos ayude a construir nuestro contenido.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Paso 2: Iniciar una tabla y establecer el formato de fila

Comenzaremos a construir una tabla y especificaremos la altura y la regla de altura para las filas.

```csharp
builder.StartTable();
builder.RowFormat.Height = 100;
builder.RowFormat.HeightRule = HeightRule.Exactly;
```

## Paso 3: Insertar celdas y rellenarlas con contenido

A continuación, hacemos un bucle para insertar celdas en la tabla. Por cada 7 celdas, finalizaremos la fila para crear una nueva.

```csharp
for (int i = 0; i < 31; i++)
{
    if (i != 0 && i % 7 == 0) builder.EndRow();
    builder.InsertCell();
    builder.Write("Cell contents");
}
builder.EndTable();
```

## Paso 4: Agregar una forma de marca de agua

 Ahora, agreguemos una marca de agua a nuestro documento. Crearemos una`Shape` objeto y establecer sus propiedades.

```csharp
Shape watermark = new Shape(doc, ShapeType.TextPlainText)
{
    RelativeHorizontalPosition = RelativeHorizontalPosition.Page,
    RelativeVerticalPosition = RelativeVerticalPosition.Page,
    IsLayoutInCell = true, // Muestra la forma fuera de la celda de la tabla si se colocará dentro de una celda.
    Width = 300,
    Height = 70,
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
    Rotation = -40
};
```

## Paso 5: Personalizar la apariencia de la marca de agua

Personalizaremos aún más la apariencia de la marca de agua configurando sus propiedades de color y texto.

```csharp
watermark.FillColor = Color.Gray;
watermark.StrokeColor = Color.Gray;
watermark.TextPath.Text = "watermarkText";
watermark.TextPath.FontFamily = "Arial";
watermark.Name = $"WaterMark_{Guid.NewGuid()}";
watermark.WrapType = WrapType.None;
```

## Paso 6: Insertar marca de agua en el documento

Encontraremos la última ejecución en el documento e insertaremos la marca de agua en esa posición.

```csharp
Run run = doc.GetChildNodes(NodeType.Run, true)[doc.GetChildNodes(NodeType.Run, true).Count - 1] as Run;
builder.MoveTo(run);
builder.InsertNode(watermark);
```

## Paso 7: Optimizar el documento para Word 2010

Para garantizar la compatibilidad, optimizaremos el documento para Word 2010.

```csharp
doc.CompatibilityOptions.OptimizeFor(MsWordVersion.Word2010);
```

## Paso 8: Guardar el documento

Finalmente, guardaremos nuestro documento en el directorio especificado.

```csharp
doc.Save(dataDir + "WorkingWithShapes.LayoutInCell.docx");
```

## Conclusión

¡Y ya está! Ha creado con éxito un documento de Word con un diseño de tabla personalizado y ha añadido una marca de agua utilizando Aspose.Words para .NET. Este tutorial tiene como objetivo proporcionar una guía clara, paso a paso, para ayudarle a comprender cada parte del proceso. Con estas habilidades, ahora puede crear documentos de Word más sofisticados y personalizados mediante programación.

## Preguntas frecuentes

### ¿Puedo utilizar una fuente diferente para el texto de la marca de agua?
 Sí, puedes cambiar la fuente configurando la`watermark.TextPath.FontFamily` propiedad a la fuente deseada.

### ¿Cómo ajusto la posición de la marca de agua?
 Puedes modificar el`RelativeHorizontalPosition`, `RelativeVerticalPosition`, `HorizontalAlignment` , y`VerticalAlignment` Propiedades para ajustar la posición de la marca de agua.

### ¿Es posible utilizar una imagen en lugar de texto para la marca de agua?
 ¡Por supuesto! Puedes crear un`Shape` con el tipo`ShapeType.Image` y establece su imagen usando el`ImageData.SetImage` método.

### ¿Puedo crear tablas con diferentes alturas de fila?
Sí, puedes establecer diferentes alturas para cada fila cambiando el`RowFormat.Height` propiedad antes de insertar celdas en esa fila.

### ¿Cómo elimino una marca de agua del documento?
 Puede eliminar la marca de agua ubicándola en la colección de formas del documento y llamando al método`Remove` método.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
