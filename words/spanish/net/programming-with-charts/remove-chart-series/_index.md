---
title: Eliminar una serie de gráfico de un Word Document usando Aspose.Words for .NET
weight: 510
limit:
description: Aprende cómo eliminar una serie de datos específica de un gráfico de columnas en un Word document con Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, remove chart series, ChartSeriesCollection.RemoveAt, column chart manipulation, Word document chart editing, C# chart series removal]
url: /net/programming-with-charts/remove-chart-series/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aprende cómo eliminar una serie de datos específica de un gráfico de
    columnas en un Word document con Aspose.Words for .NET.
  headline: Eliminar una serie de gráfico de un Word Document usando Aspose.Words
    for .NET
  type: TechArticle
- description: Aprende cómo eliminar una serie de datos específica de un gráfico de
    columnas en un Word document con Aspose.Words for .NET.
  name: Eliminar una serie de gráfico de un Word Document usando Aspose.Words for
    .NET
  steps:
  - name: Crea un nuevo Word Document y un DocumentBuilder vinculado a él.
    text: Crea un nuevo Word Document y un DocumentBuilder vinculado a él.
  - name: Inserta un gráfico de columnas de tamaño 432×252 puntos y obtén el objeto
      Chart para manipularlo posteriormente.
    text: Inserta un gráfico de columnas de tamaño 432×252 puntos y obtén el objeto
      Chart para manipularlo posteriormente.
  - name: Define el índice basado en cero de la serie que debe eliminarse (la segunda
      serie).
    text: Define el índice basado en cero de la serie que debe eliminarse (la segunda
      serie).
  - name: Si el índice es válido, llama a RemoveAt en la colección Series del gráfico
      para eliminar esa serie.
    text: Si el índice es válido, llama a RemoveAt en la colección Series del gráfico
      para eliminar esa serie.
  - name: Guarda el documento actualizado en un archivo .docx.
    text: Guarda el documento actualizado en un archivo .docx.
  type: HowTo
- questions:
  - answer: La condición `if` (`targetSeriesIdx < columnChart.Series.Count`) fallará,
      por lo que `RemoveAt` nunca se llamará y el gráfico permanecerá sin cambios.
    question: ¿Qué ocurre si paso un índice que es igual al número de series en el
      gráfico?
  - answer: Sí, después de `columnChart.Series.RemoveAt` la leyenda se regenera para
      reflejar las series restantes, por lo que la entrada eliminada desaparece de
      la leyenda.
    question: ¿Eliminar una serie actualiza automáticamente la leyenda del gráfico?
  - answer: El código funciona para cualquier tipo de gráfico que admita una colección
      `Series`; solo cambia `ChartType.Column` al tipo deseado al insertar el gráfico.
    question: ¿Puedo usar el mismo código para eliminar una serie de un gráfico de
      líneas o de pastel?
  - answer: Un gráfico sin series sigue siendo un `Shape` válido y se guardará, pero
      aparecerá vacío en el documento resultante.
    question: Si elimino la única serie de un gráfico, ¿el gráfico seguirá guardándose
      correctamente?
  type: FAQPage
images:
- /net/programming-with-charts/remove-chart-series/og-image.png
og_title: Eliminar una serie de gráfico en un Word Document
og_description: Guía paso a paso para eliminar una serie de datos de un gráfico de Word usando Aspose.Words for .NET.
og_image_alt: Guía que muestra cómo eliminar una serie de datos específica de un gráfico de columnas en un Word document usando Aspose.Words for .NET.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Eliminar una serie de gráfico de un Word Document usando Aspose.Words
Este tutorial muestra cómo crear un Word document, agregar un gráfico de columnas con DocumentBuilder y luego eliminar una serie de datos específica de ese gráfico usando el método ChartSeriesCollection.RemoveAt. Al final, tendrás un documento guardado con la serie no deseada eliminada, lo que te brinda un control preciso sobre el contenido del gráfico directamente desde código .NET.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/remove-chart-series" >}}


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

**Q: ¿Qué ocurre si paso un índice que es igual al número de series en el gráfico?**  
A: La condición `if` (`targetSeriesIdx < columnChart.Series.Count`) fallará, por lo que `RemoveAt` nunca se llamará y el gráfico permanecerá sin cambios.

**Q: ¿Eliminar una serie actualiza automáticamente la leyenda del gráfico?**  
A: Sí, después de `columnChart.Series.RemoveAt` la leyenda se regenera para reflejar las series restantes, por lo que la entrada eliminada desaparece de la leyenda.

**Q: ¿Puedo usar el mismo código para eliminar una serie de un gráfico de líneas o de pastel?**  
A: El código funciona para cualquier tipo de gráfico que admita una colección `Series`; solo cambia `ChartType.Column` al tipo deseado al insertar el gráfico.

**Q: Si elimino la única serie de un gráfico, ¿el gráfico seguirá guardándose correctamente?**  
A: Un gráfico sin series sigue siendo un `Shape` válido y se guardará, pero aparecerá vacío en el documento resultante.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}