---
"description": "Aprenda a establecer los límites de un eje en un gráfico utilizando Aspose.Words para .NET controlando el rango de valores que se muestran en el eje."
"linktitle": "Límites del eje en un gráfico"
"second_title": "API de procesamiento de documentos de Aspose.Words"
"title": "Límites del eje en un gráfico"
"url": "/es/net/programming-with-charts/bounds-of-axis/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Límites del eje en un gráfico

## Introducción

¿Quieres crear documentos profesionales con gráficos en .NET? ¡Estás en el lugar indicado! Esta guía te guiará en el proceso de usar Aspose.Words para .NET para definir los límites de los ejes en un gráfico. Desglosaremos cada paso para que puedas seguirlo fácilmente, incluso si eres nuevo en la biblioteca. ¡Comencemos!

## Prerrequisitos

Antes de comenzar, asegúrese de tener lo siguiente:

- Aspose.Words para .NET: Puedes [descargar](https://releases.aspose.com/words/net/) la última versión o utilizar una [prueba gratuita](https://releases.aspose.com/).
- .NET Framework: asegúrese de tener .NET instalado en su sistema.
- IDE: Un entorno de desarrollo como Visual Studio.

Una vez que tengas todo listo, podemos pasar a los siguientes pasos.

## Importar espacios de nombres

Para empezar, deberá importar los espacios de nombres necesarios. Estos le permitirán acceder a la biblioteca Aspose.Words y a sus funciones de gráficos.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## Paso 1: Configure su directorio de documentos

Primero, debes configurar el directorio donde se guardará tu documento. Este paso es sencillo, pero crucial para organizar tus archivos.

```csharp
// Ruta a su directorio de documentos
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

Ahora es el momento de insertar un gráfico en el documento. En este ejemplo, usaremos un gráfico de columnas.

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

Aquí añadimos datos al gráfico. Esto incluye especificar el nombre de la serie y los puntos de datos.

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

¡Listo! Has creado correctamente un documento con un gráfico usando Aspose.Words para .NET. 

## Conclusión

Con Aspose.Words para .NET, puede crear y manipular fácilmente gráficos en sus documentos. Esta guía paso a paso le muestra cómo definir los límites de los ejes en un gráfico, lo que mejora la precisión y profesionalidad de sus presentaciones de datos. Ya sea que genere informes, presentaciones o cualquier otro documento, Aspose.Words le proporciona las herramientas que necesita.

## Preguntas frecuentes

### ¿Qué es Aspose.Words para .NET?
Aspose.Words para .NET es una biblioteca que le permite crear, modificar y convertir documentos de Word mediante programación utilizando el marco .NET.

### ¿Cómo configuro Aspose.Words para .NET?
Puedes descargarlo desde [aquí](https://releases.aspose.com/words/net/) y siga las instrucciones de instalación proporcionadas.

### ¿Puedo utilizar Aspose.Words gratis?
Sí, puedes utilizar un [prueba gratuita](https://releases.aspose.com/) o conseguir uno [licencia temporal](https://purchase.aspose.com/temporary-license/).

### ¿Dónde puedo encontrar documentación de Aspose.Words para .NET?
La documentación detallada está disponible [aquí](https://reference.aspose.com/words/net/).

### ¿Cómo puedo obtener soporte para Aspose.Words?
Puedes visitar el [foro de soporte](https://forum.aspose.com/c/words/8) para obtener ayuda.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}