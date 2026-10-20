---
title: Inserte un gráfico de columnas de muestra en un documento Word usando Aspose.Words for .NET
weight: 410
limit:
description: Guía paso a paso para crear un archivo Word, insertar un gráfico de columnas predeterminado con DocumentBuilder.InsertChart, acceder al objeto Chart y guardar como .docx.
keywords: [Aspose.Words for .NET, insert column chart, documentbuilder inserchart, create word document with chart, save chart to docx, chart object Aspose.Words]
url: /net/programming-with-charts/insert-sample-column-chart/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Guía paso a paso para crear un archivo Word, insertar un gráfico de
    columnas predeterminado con DocumentBuilder.InsertChart, acceder al objeto Chart
    y guardar como .docx.
  headline: Inserte un gráfico de columnas de muestra en un documento Word usando
    Aspose.Words for .NET
  type: TechArticle
- description: Guía paso a paso para crear un archivo Word, insertar un gráfico de
    columnas predeterminado con DocumentBuilder.InsertChart, acceder al objeto Chart
    y guardar como .docx.
  name: Inserte un gráfico de columnas de muestra en un documento Word usando Aspose.Words
    for .NET
  steps:
  - name: Cree un documento Word vacío y un DocumentBuilder para editarlo.
    text: Cree un documento Word vacío y un DocumentBuilder para editarlo.
  - name: Inserte un gráfico de columnas de tamaño 432 × 252 puntos en el documento.
    text: Inserte un gráfico de columnas de tamaño 432 × 252 puntos en el documento.
  - name: Recupere el objeto Chart de la forma insertada para una personalización
      adicional si es necesario.
    text: Recupere el objeto Chart de la forma insertada para una personalización
      adicional si es necesario.
  - name: Guarde el documento, que ahora contiene el gráfico de columnas insertado,
      en un archivo .docx.
    text: Guarde el documento, que ahora contiene el gráfico de columnas insertado,
      en un archivo .docx.
  type: HowTo
- questions:
  - answer: Las dimensiones se especifican en puntos (1 punto = 1/72 de pulgada),
      por lo que 432 pt ≈ 6 in y 252 pt ≈ 3,5 in.
    question: ¿Qué unidades se utilizan para los parámetros de ancho y alto (432,
      252) en InsertChart?
  - answer: Sí—después de la inserción dispone del objeto Chart a través de `chartContainer.Chart`;
      puede modificar su SeriesCollection, Categories y Values para reemplazar los
      datos de muestra.
    question: ¿Puedo cambiar los datos del gráfico después de llamar a InsertChart
      con el conjunto de datos predeterminado?
  - answer: Simplemente reemplace `ChartType.Column` por otro valor de enumeración
      como `ChartType.Line` en la llamada a `InsertChart`.
    question: ¿Es posible insertar un tipo de gráfico diferente (p. ej., un gráfico
      de líneas) usando el mismo código?
  - answer: No—`docBuilder.InsertChart` incrusta automáticamente el gráfico en un
      `Shape`; al llamar a `wordDoc.Save` se escribe el gráfico junto con el documento.
    question: ¿Necesito llamar a algún método adicional para incrustar el gráfico
      antes de guardar el documento?
  type: FAQPage
images:
- /net/programming-with-charts/insert-sample-column-chart/og-image.png
og_title: Inserte un gráfico de columnas de muestra en un documento Word
og_description: Agregue un gráfico de columnas listo para usar a un documento Word con Aspose.Words for .NET en minutos.
og_image_alt: Captura de pantalla que muestra un documento Word con un gráfico de columnas de muestra insertado usando Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Inserte un gráfico de columnas de muestra en un documento Word usando Aspose.Words
Este tutorial le guía paso a paso para crear un nuevo documento Word e insertar un gráfico de columnas predeterminado con DocumentBuilder.InsertChart. También verá cómo recuperar el objeto Chart incrustado para una manipulación adicional. Finalmente, la guía muestra cómo guardar el documento como un archivo .docx.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/insert-sample-column-chart" >}}


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

**Q: ¿Qué unidades se utilizan para los parámetros de ancho y alto (432, 252) en InsertChart?**  
A: Las dimensiones se especifican en puntos (1 punto = 1/72 de pulgada), por lo que 432 pt ≈ 6 in y 252 pt ≈ 3,5 in.

**Q: ¿Puedo cambiar los datos del gráfico después de llamar a InsertChart con el conjunto de datos predeterminado?**  
A: Sí—después de la inserción dispone del objeto Chart a través de `chartContainer.Chart`; puede modificar su SeriesCollection, Categories y Values para reemplazar los datos de muestra.

**Q: ¿Es posible insertar un tipo de gráfico diferente (p. ej., un gráfico de líneas) usando el mismo código?**  
A: Simplemente reemplace `ChartType.Column` por otro valor de enumeración como `ChartType.Line` en la llamada a `InsertChart`.

**Q: ¿Necesito llamar a algún método adicional para incrustar el gráfico antes de guardar el documento?**  
A: No—`docBuilder.InsertChart` incrusta automáticamente el gráfico en un `Shape`; al llamar a `wordDoc.Save` se escribe el gráfico junto con el documento.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}