---
title: Insertar gráfico de dispersión en un documento de Word
linktitle: Insertar gráfico de dispersión en un documento de Word
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a insertar un gráfico de dispersión en Word con Aspose.Words para .NET. Pasos sencillos para integrar representaciones visuales de datos en sus documentos.
weight: 10
url: /es/net/programming-with-charts/insert-scatter-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Insertar gráfico de dispersión en un documento de Word

## Introducción

En este tutorial, aprenderá a aprovechar Aspose.Words para .NET para insertar un gráfico de dispersión en su documento de Word. Los gráficos de dispersión son herramientas visuales eficaces que pueden mostrar puntos de datos de manera eficaz en función de dos variables, lo que hace que sus documentos sean más atractivos e informativos.

## Prerrequisitos

Antes de profundizar en la creación de gráficos de dispersión con Aspose.Words para .NET, asegúrese de tener los siguientes requisitos previos:

1.  Instalación de Aspose.Words para .NET: Descargue e instale Aspose.Words para .NET desde[aquí](https://releases.aspose.com/words/net/).
   
2. Conocimientos básicos de C#: será beneficioso estar familiarizado con el lenguaje de programación C# y el marco .NET.

## Importar espacios de nombres

Para comenzar, debe importar los espacios de nombres necesarios en su proyecto de C#:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
```

Ahora, analicemos el proceso de inserción de un gráfico de dispersión en su documento de Word usando Aspose.Words para .NET:

## Paso 1: Inicializar el documento y DocumentBuilder

 Primero, inicialice una nueva instancia del`Document` clase y`DocumentBuilder` clase para comenzar a construir su documento.

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Paso 2: Insertar el gráfico de dispersión

 Utilice el`InsertChart` método de la`DocumentBuilder` clase para insertar un gráfico de dispersión en el documento.

```csharp
Shape shape = builder.InsertChart(ChartType.Scatter, 432, 252);
Chart chart = shape.Chart;
```

## Paso 3: Agregar series de datos al gráfico

Ahora, agregue series de datos a su gráfico de dispersión. Este ejemplo demuestra cómo agregar una serie con puntos de datos específicos.

```csharp
chart.Series.Add("Aspose Series 1", new double[] { 0.7, 1.8, 2.6 }, new double[] { 2.7, 3.2, 0.8 });
```

## Paso 4: Guardar el documento

 Finalmente, guarde el documento modificado en la ubicación deseada utilizando el`Save` método de la`Document` clase.

```csharp
doc.Save(dataDir + "WorkingWithCharts.InsertScatterChart.docx");
```

## Conclusión

¡Felicitaciones! Aprendió a insertar un gráfico de dispersión en su documento de Word con Aspose.Words para .NET. Los gráficos de dispersión son excelentes herramientas para visualizar relaciones entre datos y, con Aspose.Words, puede integrarlos sin esfuerzo en sus documentos para mejorar la claridad y la comprensión.

## Preguntas frecuentes

### ¿Puedo personalizar la apariencia del gráfico de dispersión usando Aspose.Words?
Sí, Aspose.Words permite una amplia personalización de las propiedades del gráfico, como colores, ejes y etiquetas.

### ¿Aspose.Words es compatible con diferentes versiones de Microsoft Word?
Aspose.Words admite varias versiones de Microsoft Word, lo que garantiza la compatibilidad entre plataformas.

### ¿Aspose.Words proporciona soporte para otros tipos de gráficos?
Sí, Aspose.Words admite una amplia gama de tipos de gráficos, incluidos gráficos de barras, gráficos de líneas y gráficos circulares.

### ¿Puedo actualizar dinámicamente los datos en el gráfico de dispersión mediante programación?
Por supuesto, puedes actualizar los datos del gráfico dinámicamente mediante llamadas a la API de Aspose.Words.

### ¿Dónde puedo obtener más ayuda o soporte para Aspose.Words?
 Para obtener más ayuda, visite el sitio[Foro de soporte de Aspose.Words](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
