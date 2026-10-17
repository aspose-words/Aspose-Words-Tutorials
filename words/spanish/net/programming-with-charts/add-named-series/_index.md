---
title: Agregar una Serie de Datos Nombrada a un Gráfico de Histograma en Word usando Aspose.Words para .NET
weight: 610
limit:
description: Aprende cómo incrustar un gráfico de histograma en un documento Word y agregar una serie de datos nombrada con Aspose.Words para .NET.
keywords: [Aspose.Words for .NET, add named series chart, histogram chart in Word, ChartSeriesCollection Add overload, DocumentBuilder chart example, named data series Word]
url: /net/programming-with-charts/add-named-series/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aprende cómo incrustar un gráfico de histograma en un documento Word
    y agregar una serie de datos nombrada con Aspose.Words para .NET.
  headline: Agregar una Serie de Datos Nombrada a un Gráfico de Histograma en Word
    usando Aspose.Words para .NET
  type: TechArticle
- description: Aprende cómo incrustar un gráfico de histograma en un documento Word
    y agregar una serie de datos nombrada con Aspose.Words para .NET.
  name: Agregar una Serie de Datos Nombrada a un Gráfico de Histograma en Word usando
    Aspose.Words para .NET
  steps:
  - name: Crea un nuevo documento Word vacío y un DocumentBuilder para editarlo.
    text: Crea un nuevo documento Word vacío y un DocumentBuilder para editarlo.
  - name: Inserta una forma de gráfico de histograma de tamaño 500×300 en el documento
      y obtén su objeto Chart.
    text: Inserta una forma de gráfico de histograma de tamaño 500×300 en el documento
      y obtén su objeto Chart.
  - name: Elimina la serie de marcador de posición predeterminada que Aspose.Words
      agrega a los gráficos nuevos.
    text: Elimina la serie de marcador de posición predeterminada que Aspose.Words
      agrega a los gráficos nuevos.
  - name: Agrega una serie con nombre llamada \"Demo Series\" con los puntos de datos
      especificados al gráfico de histograma.
    text: Agrega una serie con nombre llamada \"Demo Series\" con los puntos de datos
      especificados al gráfico de histograma.
  - name: Guarda el documento en un archivo .docx que contiene la serie de gráfico
      etiquetada.
    text: Guarda el documento en un archivo .docx que contiene la serie de gráfico
      etiquetada.
  type: HowTo
- questions:
  - answer: '`InsertChart` crea una serie de marcador de posición predeterminada;
      al borrarla se elimina esa serie vacía, de modo que el gráfico solo muestra
      los datos que agregas con `Series.Add`.'
    question: ¿Por qué necesito llamar a `histogramChart.Series.Clear()` antes de
      agregar mi propia serie?
  - answer: Sí, llama a `histogramChart.Series.Add` varias veces, cada una con un
      nombre distinto y valores `double[]`; cada serie se listará en la leyenda del
      gráfico con el nombre proporcionado.
    question: ¿Puedo agregar más de una serie usando la misma sobrecarga, y aparecerá
      cada una con su propia etiqueta?
  - answer: La sobrecarga espera un `double[]`; si tienes `int[]` u otras matrices
      numéricas, conviértelas o cámbialas a `double[]` antes de pasarlas.
    question: ¿Es el argumento `double[]` el único tipo aceptado para los puntos de
      datos?
  - answer: La cadena pasada como primer argumento (p. ej., \"Demo Series\") se usa
      como título de la serie y se muestra en la leyenda del gráfico de forma predeterminada.
    question: ¿Aparecerá el nombre de la serie que suministro en el gráfico automáticamente?
  type: FAQPage
images:
- /net/programming-with-charts/add-named-series/og-image.png
og_title: Agregar una Serie Nombrada a un Gráfico de Histograma en Word
og_description: Etiqueta rápidamente una serie de gráfico en Word con Aspose.Words y véala renderizada al instante.
og_image_alt: Captura de pantalla que muestra un documento Word con un gráfico de histograma que incluye una serie de datos etiquetada creada usando Aspose.Words para .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Agregar una Serie de Datos Nombrada a un Gráfico de Histograma en Word usando Aspose.Words para .NET
Este tutorial demuestra cómo crear un documento Word con Aspose.Words para .NET, insertar un gráfico de histograma y agregar una serie de datos etiquetada usando la sobrecarga ChartSeriesCollection.Add que acepta un nombre y valores. Al nombrar la serie puedes identificar claramente cada conjunto de datos dentro del gráfico, lo que facilita la lectura e interpretación del resultado visual.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/add-named-series" >}}


{{< /blocks/products/pf/tutorial-page-section >}}

{{< blocks/products/pf/tutorial-page-section >}}
## Installation Instructions
1. Download Aspose.Words for .NET:
   Get the latest version from the [Aspose Downloads page](https://releases.aspose.com/words/net/).

2. Install via NuGet:
   - Open your Visual Studio project.
   - Navigate to the NuGet Package Manager (Tools > NuGet Package Manager > Manage NuGet Packages for Solution).
   - Search for "Aspose.Words" and click Install.

3. Add Namespace References:
   Add the following namespace at the top of your code file:
   ```csharp
   using Aspose.Words;
   using Aspose.Words.Saving;
   using Aspose.Words.Drawing;
   using Aspose.Words.Fields;
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: ¿Por qué necesito llamar a `histogramChart.Series.Clear()` antes de agregar mi propia serie?**  
A: `InsertChart` crea una serie de marcador de posición predeterminada; al borrarla se elimina esa serie vacía, de modo que el gráfico solo muestra los datos que agregas con `Series.Add`.

**Q: ¿Puedo agregar más de una serie usando la misma sobrecarga, y aparecerá cada una con su propia etiqueta?**  
A: Sí, llama a `histogramChart.Series.Add` varias veces, cada una con un nombre distinto y valores `double[]`; cada serie se listará en la leyenda del gráfico con el nombre proporcionado.

**Q: ¿Es el argumento `double[]` el único tipo aceptado para los puntos de datos?**  
A: La sobrecarga espera un `double[]`; si tienes `int[]` u otras matrices numéricas, conviértelas o cámbialas a `double[]` antes de pasarlas.

**Q: ¿Aparecerá el nombre de la serie que suministro en el gráfico automáticamente?**  
A: La cadena pasada como primer argumento (p. ej., \"Demo Series\") se usa como título de la serie y se muestra en la leyenda del gráfico de forma predeterminada.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}