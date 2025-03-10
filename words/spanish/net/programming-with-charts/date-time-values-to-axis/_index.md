---
title: Agregar valores de fecha y hora al eje de un gráfico
linktitle: Agregar valores de fecha y hora al eje de un gráfico
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a agregar valores de fecha y hora al eje de un gráfico usando Aspose.Words para .NET en esta completa guía paso a paso.
weight: 10
url: /es/net/programming-with-charts/date-time-values-to-axis/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Agregar valores de fecha y hora al eje de un gráfico

## Introducción

La creación de gráficos en documentos puede ser una forma eficaz de visualizar datos. Cuando se trabaja con datos de series temporales, agregar valores de fecha y hora al eje de un gráfico es fundamental para lograr claridad. En este tutorial, lo guiaremos a través del proceso de agregar valores de fecha y hora al eje de un gráfico mediante Aspose.Words para .NET. Esta guía paso a paso lo ayudará a configurar su entorno, escribir el código y comprender cada parte del proceso. ¡Vamos a profundizar!

## Prerrequisitos

Antes de comenzar, asegúrese de tener los siguientes requisitos previos:

1. Visual Studio o cualquier IDE .NET: necesita un entorno de desarrollo para escribir y ejecutar su código .NET.
2.  Aspose.Words para .NET: Debe tener instalada la biblioteca Aspose.Words para .NET. Puede descargarla desde[aquí](https://releases.aspose.com/words/net/).
3. Conocimientos básicos de C#: este tutorial asume que tienes un conocimiento básico de programación en C#.
4.  Una licencia Aspose válida: Puede obtener una licencia temporal de[aquí](https://purchase.aspose.com/temporary-license/).

## Importar espacios de nombres

Para comenzar, asegúrese de haber importado los espacios de nombres necesarios en su proyecto. Este paso es fundamental para acceder a las clases y métodos de Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## Paso 1: Configurar el directorio de documentos

En primer lugar, debe definir el directorio en el que se guardará el documento. Esto es importante para organizar los archivos y garantizar que el código se ejecute correctamente.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Paso 2: Crear un nuevo documento y DocumentBuilder

 A continuación, cree una nueva instancia del`Document` clase y una`DocumentBuilder` objeto. Estos objetos le ayudarán a crear y manipular su documento.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Paso 3: Insertar un gráfico en el documento

 Ahora, inserte un gráfico en su documento usando el`DocumentBuilder` objeto. En este ejemplo, utilizamos un gráfico de columnas, pero también puedes elegir otros tipos.

```csharp
Shape shape = builder.InsertChart(ChartType.Column, 432, 252);
Chart chart = shape.Chart;
```

## Paso 4: Borrar series existentes

Borre cualquier serie existente en el gráfico para asegurarse de empezar desde cero. Este paso es esencial para los datos personalizados.

```csharp
chart.Series.Clear();
```

## Paso 5: Agregar valores de fecha y hora a la serie

Agregue los valores de fecha y hora a la serie de gráficos. Este paso implica crear matrices para las fechas y los valores correspondientes.

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

Establezca la escala y las marcas de graduación para el eje X. Esto garantiza que las fechas se muestren correctamente y en intervalos apropiados.

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

Por último, guarde el documento en el directorio especificado. Este paso concluye el proceso y el documento debería contener un gráfico con valores de fecha y hora en el eje X.

```csharp
doc.Save(dataDir + "WorkingWithCharts.DateTimeValuesToAxis.docx");
```

## Conclusión

Agregar valores de fecha y hora al eje de un gráfico en un documento es un proceso sencillo con Aspose.Words para .NET. Si sigue los pasos que se describen en este tutorial, podrá crear gráficos claros e informativos que visualicen de manera eficaz los datos de series temporales. Ya sea que esté preparando informes, presentaciones o cualquier documento que requiera una representación detallada de los datos, Aspose.Words le proporciona las herramientas que necesita para tener éxito.

## Preguntas frecuentes

### ¿Puedo utilizar otros tipos de gráficos con Aspose.Words para .NET?

Sí, Aspose.Words admite varios tipos de gráficos, incluidos líneas, barras, circulares y más.

### ¿Cómo puedo personalizar la apariencia de mi gráfico?

Puede personalizar la apariencia accediendo a las propiedades del gráfico y configurando estilos, colores y más.

### ¿Es posible agregar varias series a un gráfico?

 ¡Por supuesto! Puedes agregar varias series a tu gráfico llamando al`Series.Add` método varias veces con diferentes datos.

### ¿Qué pasa si necesito actualizar los datos del gráfico de forma dinámica?

Puede actualizar los datos del gráfico de forma dinámica manipulando las propiedades de las series y los ejes mediante programación según sus requisitos.

### ¿Dónde puedo encontrar documentación más detallada sobre Aspose.Words para .NET?

 Puede encontrar documentación más detallada[aquí](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
