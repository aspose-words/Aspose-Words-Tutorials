---
title: Límites de los ejes en un gráfico
linktitle: Límites de los ejes en un gráfico
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a establecer los límites de un eje en un gráfico utilizando Aspose.Words para .NET controlando el rango de valores que se muestran en el eje.
weight: 10
url: /es/net/programming-with-charts/bounds-of-axis/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Límites de los ejes en un gráfico

## Introducción

¿Está buscando crear documentos profesionales con gráficos en .NET? ¡Está en el lugar correcto! Esta guía lo guiará a través del proceso de uso de Aspose.Words para .NET para establecer los límites del eje en un gráfico. Desglosaremos cada paso para asegurarnos de que pueda seguirlo fácilmente, incluso si es nuevo en la biblioteca. ¡Así que, profundicemos y comencemos!

## Prerrequisitos

Antes de comenzar, asegúrese de tener lo siguiente:

-  Aspose.Words para .NET: puedes[descargar](https://releases.aspose.com/words/net/) la última versión o utilizar una[prueba gratis](https://releases.aspose.com/).
- .NET Framework: asegúrese de tener .NET instalado en su sistema.
- IDE: Un entorno de desarrollo como Visual Studio.

Una vez que tengamos todo listo, podemos pasar a los siguientes pasos.

## Importar espacios de nombres

Para comenzar, deberá importar los espacios de nombres necesarios. Estos le permitirán acceder a la biblioteca Aspose.Words y a sus funciones de creación de gráficos.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## Paso 1: Configurar el directorio de documentos

Lo primero que debes hacer es configurar el directorio en el que se guardará tu documento. Es un paso sencillo, pero fundamental para organizar tus archivos.

```csharp
// Ruta al directorio de su documento
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Paso 2: Crear un nuevo documento

A continuación, cree un nuevo objeto de documento. Este documento servirá como contenedor para su gráfico.

```csharp
Document doc = new Document();
```

## Paso 3: Inicializar el generador de documentos

La clase DocumentBuilder proporciona una forma rápida y sencilla de crear documentos. Inicialícela con su documento.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Paso 4: Insertar un gráfico

Ahora es el momento de insertar un gráfico en el documento. En este ejemplo, utilizaremos un gráfico de columnas.

```csharp
Shape shape = builder.InsertChart(ChartType.Column, 432, 252);
Chart chart = shape.Chart;
```

## Paso 5: Borrar series existentes

Para asegurarse de comenzar desde cero, borre cualquier serie existente del gráfico.

```csharp
chart.Series.Clear();
```

## Paso 6: Agregar datos al gráfico

Aquí agregamos datos al gráfico. Esto incluye especificar el nombre de la serie y los puntos de datos.

```csharp
chart.Series.Add("Aspose Series 1",
    new string[] { "Item 1", "Item 2", "Item 3", "Item 4", "Item 5" },
    new double[] { 1.2, 0.3, 2.1, 2.9, 4.2 });
```

## Paso 7: Establecer límites de ejes

Establecer los límites para el eje Y garantiza que el gráfico tenga la escala correcta.

```csharp
chart.AxisY.Scaling.Minimum = new AxisBound(0);
chart.AxisY.Scaling.Maximum = new AxisBound(6);
```

## Paso 8: Guardar el documento

Por último, guarde el documento en el directorio especificado.

```csharp
doc.Save(dataDir + "WorkingWithCharts.BoundsOfAxis.docx");
```

¡Y eso es todo! Has creado con éxito un documento con un gráfico utilizando Aspose.Words para .NET. 

## Conclusión

Con Aspose.Words para .NET, puede crear y manipular fácilmente gráficos en sus documentos. Esta guía paso a paso le ha mostrado cómo establecer los límites del eje en un gráfico, lo que hace que la presentación de sus datos sea más precisa y profesional. Ya sea que esté generando informes, presentaciones o cualquier otro documento, Aspose.Words le proporciona las herramientas que necesita.

## Preguntas frecuentes

### ¿Qué es Aspose.Words para .NET?
Aspose.Words para .NET es una biblioteca que le permite crear, modificar y convertir documentos de Word mediante programación utilizando el marco .NET.

### ¿Cómo configuro Aspose.Words para .NET?
 Puedes descargarlo desde[aquí](https://releases.aspose.com/words/net/) siga las instrucciones de instalación proporcionadas.

### ¿Puedo utilizar Aspose.Words gratis?
 Sí, puedes utilizar un[prueba gratis](https://releases.aspose.com/) o conseguir uno[licencia temporal](https://purchase.aspose.com/temporary-license/).

### ¿Dónde puedo encontrar documentación de Aspose.Words para .NET?
 La documentación detallada está disponible[aquí](https://reference.aspose.com/words/net/).

### ¿Cómo puedo obtener soporte para Aspose.Words?
 Puedes visitar el[foro de soporte](https://forum.aspose.com/c/words/8) para solicitar ayuda.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
