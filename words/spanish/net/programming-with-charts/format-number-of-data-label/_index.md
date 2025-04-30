---
"description": "Aprenda a dar formato a las etiquetas de datos en gráficos con Aspose.Words para .NET con esta guía paso a paso. Mejore sus documentos de Word sin esfuerzo."
"linktitle": "Formato del número de etiqueta de datos en un gráfico"
"second_title": "API de procesamiento de documentos de Aspose.Words"
"title": "Formato del número de etiqueta de datos en un gráfico"
"url": "/es/net/programming-with-charts/format-number-of-data-label/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Formato del número de etiqueta de datos en un gráfico

## Introducción

Crear documentos atractivos e informativos suele implicar la inclusión de gráficos con etiquetas de datos bien formateadas. Si eres desarrollador .NET y buscas mejorar tus documentos de Word con gráficos sofisticados, Aspose.Words para .NET es una biblioteca fantástica que te ayudará a lograrlo. Este tutorial te guiará paso a paso en el proceso de formatear etiquetas numéricas en un gráfico con Aspose.Words para .NET.

## Prerrequisitos

Antes de sumergirse en el código, hay algunos requisitos previos que debe tener en cuenta:

- Aspose.Words para .NET: Asegúrese de tener instalada la biblioteca Aspose.Words para .NET. Si aún no la ha instalado, puede... [Descárgalo aquí](https://releases.aspose.com/words/net/).
- Entorno de desarrollo: Debe tener configurado un entorno de desarrollo .NET. Se recomienda Visual Studio.
- Conocimientos básicos de C#: Es esencial estar familiarizado con la programación en C# ya que este tutorial implica escribir y comprender el código en C#.
- Licencia temporal: Para utilizar Aspose.Words sin ninguna limitación, puede obtener una [licencia temporal](https://purchase.aspose.com/temporary-license/).

Ahora, profundicemos en el proceso paso a paso de cómo dar formato a las etiquetas numéricas en un gráfico.

## Importar espacios de nombres

Primero, necesitamos importar los espacios de nombres necesarios para trabajar con Aspose.Words para .NET. Agregue las siguientes líneas al principio de su archivo de C#:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## Paso 1: Configure su directorio de documentos

Antes de empezar a manipular su documento de Word, debe especificar el directorio donde se guardará. Esto es esencial para guardarlo posteriormente.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Reemplazar `"YOUR DOCUMENT DIRECTORY"` con la ruta real a su directorio de documentos.

## Paso 2: Inicializar el documento y DocumentBuilder

El siguiente paso es inicializar un nuevo `Document` y un `DocumentBuilder`. El `DocumentBuilder` es una clase auxiliar que nos permite construir el contenido del documento.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Paso 3: Insertar un gráfico en el documento

Ahora, insertemos un gráfico en el documento usando el `DocumentBuilder`En este tutorial, utilizaremos un gráfico de líneas como ejemplo.

```csharp
Shape shape = builder.InsertChart(ChartType.Line, 432, 252);
Chart chart = shape.Chart;
chart.Title.Text = "Data Labels With Different Number Format";
```

Aquí, insertamos un gráfico de líneas con un ancho y alto específicos, y establecemos el título del gráfico.

## Paso 4: Borrar la serie predeterminada y agregar una nueva serie

De forma predeterminada, el gráfico tendrá algunas series pregeneradas. Debemos borrarlas y agregar nuestras propias series con datos específicos.

```csharp
// Eliminar serie generada por defecto.
chart.Series.Clear();

// Añadir nueva serie con puntos de datos personalizados.
ChartSeries series1 = chart.Series.Add("Aspose Series 1", 
	new string[] { "Category 1", "Category 2", "Category 3" }, 
	new double[] { 2.5, 1.5, 3.5 });
```

## Paso 5: Habilitar etiquetas de datos

Para mostrar las etiquetas de datos en el gráfico, necesitamos habilitarlas para nuestra serie.

```csharp
series1.HasDataLabels = true;
series1.DataLabels.ShowValue = true;
```

## Paso 6: Formatear las etiquetas de datos

El objetivo principal de este tutorial es formatear las etiquetas de datos. Podemos aplicar diferentes formatos numéricos a cada etiqueta individualmente.

```csharp
series1.DataLabels[0].NumberFormat.FormatCode = "\"$\"#,##0.00"; // Formato de moneda
series1.DataLabels[1].NumberFormat.FormatCode = "dd/mm/yyyy"; // Formato de fecha
series1.DataLabels[2].NumberFormat.FormatCode = "0.00%"; // Formato de porcentaje
```

Además, puede vincular el formato de una etiqueta de datos a una celda de origen. Al vincularla, `NumberFormat` se restablecerá a general y se heredará de la celda de origen.

```csharp
series1.DataLabels[2].NumberFormat.IsLinkedToSource = true;
```

## Paso 7: Guardar el documento

Por último, guarde el documento en el directorio especificado.

```csharp
doc.Save(dataDir + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

Esto guarda su documento con el nombre especificado y garantiza que se conserve su gráfico con etiquetas de datos formateadas.

## Conclusión

Formatear las etiquetas de datos en un gráfico con Aspose.Words para .NET puede mejorar considerablemente la legibilidad y la profesionalidad de sus documentos de Word. Siguiendo esta guía paso a paso, podrá crear un gráfico, agregar series de datos y dar formato a las etiquetas según sus necesidades. Aspose.Words para .NET es una potente herramienta que permite una amplia personalización y automatización de documentos de Word, lo que la convierte en un recurso invaluable para los desarrolladores de .NET.

## Preguntas frecuentes

### ¿Qué es Aspose.Words para .NET?
Aspose.Words para .NET es una potente biblioteca para crear, manipular y convertir documentos de Word mediante programación utilizando C#.

### ¿Puedo formatear otros tipos de gráficos con Aspose.Words para .NET?
Sí, Aspose.Words para .NET admite una variedad de tipos de gráficos, incluidos gráficos de barras, columnas, circulares y más.

### ¿Cómo puedo obtener una licencia temporal para Aspose.Words para .NET?
Puede obtener una licencia temporal [aquí](https://purchase.aspose.com/temporary-license/).

### ¿Es posible vincular etiquetas de datos a celdas de origen en Excel?
Sí, puede vincular etiquetas de datos a las celdas de origen, lo que permite heredar el formato del número de la celda de origen.

### ¿Dónde puedo encontrar documentación más detallada de Aspose.Words para .NET?
Puede encontrar documentación completa [aquí](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}