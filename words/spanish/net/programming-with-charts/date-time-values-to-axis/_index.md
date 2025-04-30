---
"description": "Aprenda a agregar valores de fecha y hora al eje de un gráfico usando Aspose.Words para .NET en esta completa guía paso a paso."
"linktitle": "Agregar valores de fecha y hora al eje de un gráfico"
"second_title": "API de procesamiento de documentos de Aspose.Words"
"title": "Agregar valores de fecha y hora al eje de un gráfico"
"url": "/es/net/programming-with-charts/date-time-values-to-axis/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Agregar valores de fecha y hora al eje de un gráfico

## Introducción

Crear gráficos en documentos puede ser una forma eficaz de visualizar datos. Al trabajar con datos de series temporales, añadir valores de fecha y hora al eje del gráfico es crucial para mayor claridad. En este tutorial, le guiaremos por el proceso de añadir valores de fecha y hora al eje de un gráfico con Aspose.Words para .NET. Esta guía paso a paso le ayudará a configurar su entorno, escribir el código y comprender cada parte del proceso. ¡Comencemos!

## Prerrequisitos

Antes de comenzar, asegúrese de tener los siguientes requisitos previos:

1. Visual Studio o cualquier IDE .NET: necesita un entorno de desarrollo para escribir y ejecutar su código .NET.
2. Aspose.Words para .NET: Debe tener instalada la biblioteca Aspose.Words para .NET. Puede descargarla desde [aquí](https://releases.aspose.com/words/net/).
3. Conocimientos básicos de C#: este tutorial asume que tienes un conocimiento básico de programación en C#.
4. Una licencia Aspose válida: Puede obtener una licencia temporal de [aquí](https://purchase.aspose.com/temporary-license/).

## Importar espacios de nombres

Para comenzar, asegúrese de haber importado los espacios de nombres necesarios en su proyecto. Este paso es crucial para acceder a las clases y métodos de Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## Paso 1: Configure su directorio de documentos

Primero, debe definir el directorio donde se guardará su documento. Esto es importante para organizar sus archivos y garantizar que su código se ejecute correctamente.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Paso 2: Crear un nuevo documento y DocumentBuilder

A continuación, cree una nueva instancia del `Document` clase y una `DocumentBuilder` objeto. Estos objetos le ayudarán a crear y manipular su documento.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Paso 3: Insertar un gráfico en el documento

Ahora, inserte un gráfico en su documento usando el `DocumentBuilder` Objeto. En este ejemplo, usamos un gráfico de columnas, pero también puedes elegir otros tipos.

```csharp
Shape shape = builder.InsertChart(ChartType.Column, 432, 252);
Chart chart = shape.Chart;
```

## Paso 4: Borrar las series existentes

Borre cualquier serie existente en el gráfico para asegurarse de empezar desde cero. Este paso es esencial para los datos personalizados.

```csharp
chart.Series.Clear();
```

## Paso 5: Agregar valores de fecha y hora a la serie

Agregue los valores de fecha y hora a la serie del gráfico. Este paso implica crear matrices para las fechas y sus valores correspondientes.

```csharp
chart.Series.Add("Aspose Series 1",
    new[]
    {
        new DateTime(2017, 11, 06), new DateTime(2017, 11, 09), new DateTime(2017, 11, 15),
        new DateTime(2017, 11, 21), new DateTime(2017, 11, 25), new DateTime(2017, 11, 29)
    },
    new double[] { 1.2, 0.3, 2.1, 2.9, 4.2, 5.3 });
```

## Paso 6: Configurar el eje X

Establezca la escala y las marcas de verificación para el eje X. Esto garantiza que las fechas se muestren correctamente y en intervalos apropiados.

```csharp
ChartAxis xAxis = chart.AxisX;
xAxis.Scaling.Minimum = new AxisBound(new DateTime(2017, 11, 05).ToOADate());
xAxis.Scaling.Maximum = new AxisBound(new DateTime(2017, 12, 03).ToOADate());
xAxis.MajorUnit = 7;
xAxis.MinorUnit = 1;
xAxis.MajorTickMark = AxisTickMark.Cross;
xAxis.MinorTickMark = AxisTickMark.Outside;
```

## Paso 7: Guardar el documento

Finalmente, guarde el documento en el directorio especificado. Con este paso, concluye el proceso y el documento debería contener un gráfico con valores de fecha y hora en el eje X.

```csharp
doc.Save(dataDir + "WorkingWithCharts.DateTimeValuesToAxis.docx");
```

## Conclusión

Añadir valores de fecha y hora al eje de un gráfico en un documento es un proceso sencillo con Aspose.Words para .NET. Siguiendo los pasos de este tutorial, podrá crear gráficos claros e informativos que visualicen eficazmente datos de series temporales. Ya sea que prepare informes, presentaciones o cualquier documento que requiera una representación detallada de datos, Aspose.Words le proporciona las herramientas necesarias para lograrlo.

## Preguntas frecuentes

### ¿Puedo utilizar otros tipos de gráficos con Aspose.Words para .NET?

Sí, Aspose.Words admite varios tipos de gráficos, incluidos gráficos de líneas, de barras, circulares y más.

### ¿Cómo puedo personalizar la apariencia de mi gráfico?

Puede personalizar la apariencia accediendo a las propiedades del gráfico y configurando estilos, colores y más.

### ¿Es posible agregar varias series a un gráfico?

¡Por supuesto! Puedes agregar varias series a tu gráfico llamando al `Series.Add` método varias veces con diferentes datos.

### ¿Qué pasa si necesito actualizar los datos del gráfico dinámicamente?

Puede actualizar los datos del gráfico de forma dinámica manipulando las propiedades de las series y los ejes mediante programación según sus requisitos.

### ¿Dónde puedo encontrar documentación más detallada de Aspose.Words para .NET?

Puede encontrar documentación más detallada [aquí](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}