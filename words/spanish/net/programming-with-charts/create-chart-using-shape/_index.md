---
title: Crear y personalizar gráficos usando formas
linktitle: Crear y personalizar gráficos usando formas
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a crear y personalizar gráficos en documentos de Word con Aspose.Words para .NET con esta guía paso a paso. Perfecto para la visualización de datos.
weight: 10
url: /es/net/programming-with-charts/create-chart-using-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear y personalizar gráficos usando formas

## Introducción

La creación y personalización de gráficos en sus documentos es una habilidad crucial en el mundo actual, impulsado por los datos. Los gráficos pueden ayudar a visualizar datos, lo que hace que la información compleja sea más digerible. Aspose.Words para .NET es una potente biblioteca que le permite crear y manipular documentos de Word mediante programación. En este tutorial, lo guiaremos a través del proceso de creación y personalización de un gráfico de líneas con Aspose.Words para .NET. Al final de esta guía, podrá crear gráficos de aspecto profesional con facilidad.

## Prerrequisitos

Antes de sumergirse en el código, asegúrese de tener lo siguiente:

-  Biblioteca Aspose.Words para .NET: puedes descargarla[aquí](https://releases.aspose.com/words/net/).
- Visual Studio: cualquier versión que admita .NET.
- Conocimientos básicos de C#: comprender los conceptos básicos de C# le ayudará a seguir el tutorial.

## Importar espacios de nombres

Para comenzar, debe importar los espacios de nombres necesarios. Este paso es esencial, ya que le permite utilizar las clases y los métodos que ofrece Aspose.Words para .NET.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## Paso 1: Crear un nuevo documento

En primer lugar, debe crear un nuevo documento de Word. Este documento servirá como lienzo para su gráfico.

```csharp
// Ruta al directorio de su documento
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Paso 2: Insertar un gráfico

 A continuación, insertará un gráfico de líneas en el documento.`DocumentBuilder.InsertChart` Para este fin se utiliza el método .

```csharp
Shape shape = builder.InsertChart(ChartType.Line, 432, 252);
Chart chart = shape.Chart;
```

## Paso 3: Personaliza el título del gráfico

Personalizar el título del gráfico puede ayudar a contextualizar los datos que se muestran. Puede mostrar el título y configurar su texto mediante el siguiente código:

```csharp
chart.Title.Show = true;
chart.Title.Text = "Line Chart Title";
chart.Title.Overlay = false;
// Tenga en cuenta que si se especifica un valor nulo o vacío como texto del título, se mostrará el título generado automáticamente.
```

## Paso 4: Ajuste la posición de la leyenda

La leyenda ayuda a identificar distintas series de datos en el gráfico. Puede personalizar su posición y la configuración de superposición de la siguiente manera:

```csharp
chart.Legend.Position = LegendPosition.Left;
chart.Legend.Overlay = true;
```

## Paso 5: Guardar el documento

Por último, debes guardar el documento. Este paso garantiza que todos los cambios se escriban en el archivo.

```csharp
doc.Save(dataDir + "WorkingWithCharts.CreateChartUsingShape.docx");
```

## Conclusión

En este tutorial, explicamos cómo crear y personalizar un gráfico de líneas en un documento de Word con Aspose.Words para .NET. Si sigue la guía paso a paso, podrá crear gráficos visualmente atractivos que comuniquen sus datos de manera eficaz. Aspose.Words para .NET ofrece una amplia gama de opciones de personalización, lo que le permite adaptar los gráficos a sus necesidades específicas.

## Preguntas frecuentes

### ¿Puedo usar Aspose.Words para .NET para crear otros tipos de gráficos?

 Sí, Aspose.Words para .NET admite varios tipos de gráficos, incluidos gráficos de barras, gráficos circulares y más. Puede explorar la documentación[aquí](https://reference.aspose.com/words/net/) Para más detalles.

### ¿Cómo puedo probar Aspose.Words para .NET antes de comprarlo?

 Puede descargar una versión de prueba gratuita desde[aquí](https://releases.aspose.com/)Esto le permite probar la biblioteca y sus funciones antes de realizar una compra.

### ¿Hay alguna manera de obtener ayuda si encuentro problemas?

 Por supuesto. Puedes acceder a soporte a través de los foros de la comunidad de Aspose.[aquí](https://forum.aspose.com/c/words/8)La comunidad y el personal de Aspose son muy receptivos.

### ¿Cómo compro una licencia para Aspose.Words para .NET?

 Puede comprar una licencia directamente desde el sitio web de Aspose[aquí](https://purchase.aspose.com/buy)Existen varias opciones de licencia para adaptarse a diferentes necesidades.

### ¿Qué pasa si necesito una licencia temporal para un proyecto a corto plazo?

 Aspose ofrece licencias temporales, que puedes solicitar[aquí](https://purchase.aspose.com/temporary-license/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
