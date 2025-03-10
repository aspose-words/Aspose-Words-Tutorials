---
title: Personalizar la etiqueta de datos del gráfico
linktitle: Personalizar la etiqueta de datos del gráfico
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a personalizar las etiquetas de datos de gráficos con Aspose.Words para .NET en una guía paso a paso. Perfecta para desarrolladores de .NET.
weight: 10
url: /es/net/programming-with-charts/chart-data-label/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Personalizar la etiqueta de datos del gráfico

## Introducción

¿Está buscando mejorar sus aplicaciones .NET con capacidades de procesamiento de documentos dinámicas y personalizadas? ¡Aspose.Words para .NET podría ser la respuesta! En esta guía, profundizaremos en la personalización de las etiquetas de datos de gráficos mediante Aspose.Words para .NET, una potente biblioteca para crear, modificar y convertir documentos de Word. Ya sea que sea un desarrollador experimentado o recién esté comenzando, este tutorial lo guiará paso a paso, asegurándose de que comprenda cómo utilizar esta herramienta de manera eficaz.

## Prerrequisitos

Antes de comenzar, asegúrese de tener lo siguiente:

1. Visual Studio: instale Visual Studio 2019 o posterior.
2. .NET Framework: asegúrese de tener .NET Framework 4.0 o posterior.
3.  Aspose.Words para .NET: Descargue e instale Aspose.Words para .NET desde[enlace de descarga](https://releases.aspose.com/words/net/).
4. Conocimientos básicos de C#: Es esencial estar familiarizado con la programación en C#.
5.  Una licencia válida: Obtenga una[licencia temporal](https://purchase.aspose.com/temporary-license/) o compre uno en el[enlace de compra](https://purchase.aspose.com/buy).

## Importar espacios de nombres

Para comenzar, debe importar los espacios de nombres necesarios en su proyecto de C#. Este paso es crucial, ya que garantiza que tenga acceso a todas las clases y métodos proporcionados por Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
using Aspose.Words.Charts;
```

## Paso 1: Inicializar el documento y DocumentBuilder

Para crear y manipular documentos de Word, primero necesitamos inicializar una instancia del`Document` clase y una`DocumentBuilder` objeto.

```csharp
// Ruta al directorio de su documento
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Explicación

- Documento doc: crea una nueva instancia de la clase Documento.
- Generador DocumentBuilder: DocumentBuilder ayuda a insertar contenido en el objeto Documento.

## Paso 2: Insertar un gráfico

 A continuación, insertaremos un gráfico de barras en el documento utilizando el`DocumentBuilder` objeto.

```csharp
Shape shape = builder.InsertChart(ChartType.Bar, 432, 252);
Chart chart = shape.Chart;
```

### Explicación

- Forma forma: representa el gráfico como una forma en el documento.
- builder.InsertChart(ChartType.Bar, 432, 252): Inserta un gráfico de barras con las dimensiones especificadas.

## Paso 3: Acceda a la serie de gráficos

Para personalizar las etiquetas de datos, primero necesitamos acceder a las series en el gráfico.

```csharp
ChartSeries series0 = shape.Chart.Series[0];
```

### Explicación

- ChartSeries series0: recupera la primera serie del gráfico, que personalizaremos.

## Paso 4: Personalizar las etiquetas de datos

Las etiquetas de datos se pueden personalizar para mostrar información variada. Configuraremos las etiquetas para que muestren la clave de leyenda, el nombre de la serie y el valor, mientras ocultamos el nombre de la categoría y el porcentaje.

```csharp
ChartDataLabelCollection labels = series0.DataLabels;
labels.ShowLegendKey = true;
labels.ShowLeaderLines = true;
labels.ShowCategoryName = false;
labels.ShowPercentage = false;
labels.ShowSeriesName = true;
labels.ShowValue = true;
labels.Separator = "/";
```

### Explicación

- Etiquetas de ChartDataLabelCollection: accede a las etiquetas de datos de la serie.
- etiquetas.ShowLegendKey: Muestra la clave de la leyenda.
- labels.ShowLeaderLines: muestra líneas guía para etiquetas de datos ubicadas lejos de los puntos de datos.
- etiquetas.ShowCategoryName: Oculta el nombre de la categoría.
- etiquetas.ShowPercentage: oculta el valor del porcentaje.
- etiquetas.ShowSeriesName: Muestra el nombre de la serie.
- etiquetas.ShowValue: Muestra el valor de los puntos de datos.
- etiquetas.Separador: Establece el separador para las etiquetas de datos.

## Paso 5: Guardar el documento

Por último, guarde el documento en el directorio especificado.

```csharp
doc.Save(dataDir + "WorkingWithCharts.ChartDataLabel.docx");
```

### Explicación

- doc.Save: guarda el documento con el nombre especificado en el directorio proporcionado.

## Conclusión

 ¡Felicitaciones! Ha personalizado con éxito las etiquetas de datos de gráficos con Aspose.Words para .NET. Esta biblioteca ofrece una solución sólida para manejar documentos de Word de manera programática, lo que facilita a los desarrolladores la creación de aplicaciones de procesamiento de documentos dinámicas y sofisticadas.[documentación](https://reference.aspose.com/words/net/) para explorar más características y capacidades.

## Preguntas frecuentes

### ¿Qué es Aspose.Words para .NET?
Aspose.Words para .NET es una potente biblioteca de procesamiento de documentos que permite a los desarrolladores crear, modificar y convertir documentos de Word mediante programación.

### ¿Cómo instalo Aspose.Words para .NET?
 Puedes descargarlo e instalarlo desde[enlace de descarga](https://releases.aspose.com/words/net/). Siga las instrucciones de instalación proporcionadas.

### ¿Puedo probar Aspose.Words para .NET gratis?
 Sí, puedes obtener una[prueba gratis](https://releases.aspose.com/) o un[licencia temporal](https://purchase.aspose.com/temporary-license/)para evaluar el producto.

### ¿Aspose.Words para .NET es compatible con .NET Core?
Sí, Aspose.Words para .NET es compatible con .NET Core, .NET Standard y .NET Framework.

### ¿Dónde puedo obtener soporte para Aspose.Words para .NET?
 Puedes visitar el[foro de soporte](https://forum.aspose.com/c/words/8) para obtener ayuda y asistencia de la comunidad y los expertos de Aspose.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
