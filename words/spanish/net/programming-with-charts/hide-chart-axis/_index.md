---
title: Ocultar el eje de un gráfico en un documento de Word
linktitle: Ocultar el eje de un gráfico en un documento de Word
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a ocultar el eje del gráfico en un documento de Word usando Aspose.Words para .NET con nuestro tutorial detallado paso a paso.
weight: 10
url: /es/net/programming-with-charts/hide-chart-axis/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ocultar el eje de un gráfico en un documento de Word

## Introducción

La creación de documentos de Word dinámicos y visualmente atractivos suele implicar la incorporación de gráficos y tablas. Uno de estos casos podría requerir ocultar el eje del gráfico para lograr una presentación más clara. Aspose.Words para .NET ofrece una API completa y fácil de usar para dichas tareas. Este tutorial le guiará a través de los pasos para ocultar un eje de gráfico en un documento de Word utilizando Aspose.Words para .NET.

## Prerrequisitos

Antes de sumergirnos en el tutorial, asegúrese de tener los siguientes requisitos previos:

-  Aspose.Words para .NET: Puedes descargarlo desde[aquí](https://releases.aspose.com/words/net/).
- Entorno de desarrollo: cualquier IDE que admita el desarrollo .NET, como Visual Studio.
- .NET Framework: asegúrese de tener .NET Framework instalado en su máquina.
- Conocimientos básicos de C#: será beneficioso estar familiarizado con el lenguaje de programación C#.

## Importar espacios de nombres

Para comenzar a trabajar con Aspose.Words para .NET, debe importar los espacios de nombres necesarios en su proyecto. A continuación, le indicamos cómo hacerlo:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

Dividamos el proceso en pasos simples y fáciles de seguir.

## Paso 1: Inicializar el documento y DocumentBuilder

El primer paso implica crear un nuevo documento de Word e inicializar el objeto DocumentBuilder.

```csharp
// Ruta al directorio de su documento
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 En este paso definimos la ruta donde se guardará el documento. Luego creamos un nuevo`Document` objeto y un`DocumentBuilder` objeto para comenzar a construir nuestro documento.

## Paso 2: Insertar un gráfico

 A continuación, insertaremos un gráfico en el documento utilizando el`DocumentBuilder` objeto.

```csharp
Shape shape = builder.InsertChart(ChartType.Column, 432, 252);
Chart chart = shape.Chart;
```

 Aquí, insertamos un gráfico de columnas con dimensiones específicas.`InsertChart` El método devuelve un`Shape` objeto que contiene el gráfico.

## Paso 3: Borrar series existentes

Antes de agregar nuevos datos al gráfico, debemos borrar cualquier serie existente.

```csharp
chart.Series.Clear();
```

Este paso garantiza que se eliminen todos los datos predeterminados del gráfico, dejando lugar para los nuevos datos que agregaremos a continuación.

## Paso 4: Agregar datos de la serie

Ahora, agreguemos nuestra propia serie de datos al gráfico.

```csharp
chart.Series.Add("Aspose Series 1",
    new string[] { "Item 1", "Item 2", "Item 3", "Item 4", "Item 5" },
    new double[] { 1.2, 0.3, 2.1, 2.9, 4.2 });
```

En este paso, agregamos una serie titulada "Serie Aspose 1" con las categorías y valores correspondientes.

## Paso 5: Ocultar el eje Y

 Para ocultar el eje Y del gráfico, simplemente configuramos el`Hidden` propiedad del eje Y para`true`.

```csharp
chart.AxisY.Hidden = true;
```

Esta línea de código oculta el eje Y, haciéndolo invisible en el gráfico.

## Paso 6: Guardar el documento

Por último, guarde el documento en el directorio especificado.

```csharp
doc.Save(dataDir + "WorkingWithCharts.HideChartAxis.docx");
```

Este comando guarda el documento de Word con el gráfico en la ruta especificada.

## Conclusión

¡Felicitaciones! Aprendió a ocultar un eje de gráfico en un documento de Word con Aspose.Words para .NET. Esta potente biblioteca facilita la manipulación de documentos de Word mediante programación. Si sigue estos pasos, podrá crear documentos personalizados y de aspecto profesional con un mínimo esfuerzo.

## Preguntas frecuentes

### ¿Qué es Aspose.Words para .NET?
Aspose.Words para .NET es una potente API para crear, editar, convertir y manipular documentos de Word dentro de aplicaciones .NET.

### ¿Puedo ocultar los ejes X e Y en un gráfico?
 Sí, puedes ocultar ambos ejes configurando el`Hidden` propiedad de ambos`AxisX` y`AxisY` a`true`.

### ¿Hay una prueba gratuita disponible para Aspose.Words para .NET?
 Sí, puedes obtener una prueba gratuita[aquí](https://releases.aspose.com/).

### ¿Dónde puedo encontrar más documentación?
 Puede encontrar documentación detallada sobre Aspose.Words para .NET[aquí](https://reference.aspose.com/words/net/).

### ¿Cómo puedo obtener soporte para Aspose.Words para .NET?
 Puede obtener soporte de la comunidad Aspose[aquí](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
