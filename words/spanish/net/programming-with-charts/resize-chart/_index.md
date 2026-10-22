---
title: Redimensionar el gráfico proporcionalmente al cambiar el tamaño de página en Word usando Aspose.Words for .NET
weight: 210
limit:
description: Aprenda a redimensionar automáticamente un gráfico de columnas de Word al cambiar el documento a A4 usando Aspose.Words for .NET.
keywords: [chart resizing, Aspose.Words for .NET, Word column chart, automatic chart scaling, A4 page size, resize chart in Word]
url: /net/programming-with-charts/resize-chart/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aprenda a redimensionar automáticamente un gráfico de columnas de Word
    al cambiar el documento a A4 usando Aspose.Words for .NET.
  headline: Redimensionar el gráfico proporcionalmente al cambiar el tamaño de página
    en Word usando Aspose.Words for .NET
  type: TechArticle
- description: Aprenda a redimensionar automáticamente un gráfico de columnas de Word
    al cambiar el documento a A4 usando Aspose.Words for .NET.
  name: Redimensionar el gráfico proporcionalmente al cambiar el tamaño de página
    en Word usando Aspose.Words for .NET
  steps:
  - name: Cree un nuevo objeto Document y un DocumentBuilder para editarlo.
    text: Cree un nuevo objeto Document y un DocumentBuilder para editarlo.
  - name: Inserte un gráfico de columnas de tamaño 432×252 puntos y obtenga su objeto
      Chart.
    text: Inserte un gráfico de columnas de tamaño 432×252 puntos y obtenga su objeto
      Chart.
  - name: Establezca el texto del título del gráfico a "Quarterly Revenue" y hágalo
      visible.
    text: Establezca el texto del título del gráfico a "Quarterly Revenue" y hágalo
      visible.
  - name: Guarde el documento en un archivo mostrando el tamaño original del gráfico.
    text: Guarde el documento en un archivo mostrando el tamaño original del gráfico.
  - name: Cambie el tamaño de papel del documento a A4 y actualice el diseño.
    text: Cambie el tamaño de papel del documento a A4 y actualice el diseño.
  - name: Calcule un nuevo ancho de gráfico igual al 80 % del ancho de la página mientras
      conserva la relación de aspecto original.
    text: Calcule un nuevo ancho de gráfico igual al 80 % del ancho de la página mientras
      conserva la relación de aspecto original.
  - name: Si la forma contiene un gráfico, aplique el ancho y alto calculados para
      redimensionarla.
    text: Si la forma contiene un gráfico, aplique el ancho y alto calculados para
      redimensionarla.
  - name: Guarde el documento después de que el gráfico haya sido redimensionado para
      reflejar el nuevo tamaño de página.
    text: Guarde el documento después de que el gráfico haya sido redimensionado para
      reflejar el nuevo tamaño de página.
  type: HowTo
- questions:
  - answer: Sí. Cambiar `docBuilder.PageSetup.PaperSize` no ajusta automáticamente
      las formas existentes, por lo que debe recalcular y asignar `chartContainer.Width`
      y `Height` usted mismo, como se muestra.
    question: ¿Necesito redimensionar manualmente el gráfico después de cambiar el
      tamaño de papel del documento?
  - answer: Almacena `originalAspectRatio = chartContainer.Height / chartContainer.Width`
      y luego calcula `newChartHeight = newChartWidth * originalAspectRatio` después
      de determinar el nuevo ancho.
    question: ¿Cómo mantiene el código la relación original de ancho a alto del gráfico
      al redimensionarlo?
  - answer: '`UpdatePageLayout()` obliga al motor de diseño a reevaluar las dimensiones
      de la página, asegurando que `docBuilder.PageSetup.PageWidth` refleje el nuevo
      ancho A4 antes de que se recalcule el tamaño del gráfico.'
    question: ¿Por qué se llama a `myDoc.UpdatePageLayout()` después de establecer
      el tamaño de papel a A4?
  - answer: La condición `if (chartContainer.HasChart)` evita que el código asigne
      `Width` y `Height` cuando no hay un gráfico presente, evitando una excepción
      en tiempo de ejecución.
    question: ¿Qué ocurre si la forma insertada no contiene realmente un gráfico?
  - answer: Absolutamente—reemplace el multiplicador `0.8` por cualquier proporción
      que prefiera; el resto de la lógica de redimensionado seguirá conservando la
      relación de aspecto original.
    question: ¿Puedo cambiar el factor de escala del 80 % a otro valor?
  type: FAQPage
images:
- /net/programming-with-charts/resize-chart/og-image.png
og_title: Redimensionar un gráfico de Word al cambiar a A4
og_description: Mantenga su gráfico proporcional redimensionándolo automáticamente después de cambiar el documento a A4.
og_image_alt: Captura de pantalla que muestra un gráfico de columnas redimensionado automáticamente para ajustarse a un documento de Word de tamaño A4 usando Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Redimensionar el gráfico proporcionalmente al cambiar el tamaño de página en Word usando Aspose.Words
Este tutorial muestra cómo insertar un gráfico de columnas en un documento de Word, cambiar el tamaño de página del documento a A4 y hacer que el gráfico se redimensione automáticamente para que mantenga la proporción con el nuevo ancho de página. Al seguir los pasos, verá que el gráfico ajusta sus dimensiones sin escalado manual, garantizando un diseño consistente en diferentes formatos de página.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/resize-chart" >}}


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

**Q: ¿Necesito redimensionar manualmente el gráfico después de cambiar el tamaño de papel del documento?**  
A: Sí. Cambiar `docBuilder.PageSetup.PaperSize` no ajusta automáticamente las formas existentes, por lo que debe recalcular y asignar `chartContainer.Width` y `Height` usted mismo, como se muestra.

**Q: ¿Cómo mantiene el código la relación original de ancho a alto del gráfico al redimensionarlo?**  
A: Almacena `originalAspectRatio = chartContainer.Height / chartContainer.Width` y luego calcula `newChartHeight = newChartWidth * originalAspectRatio` después de determinar el nuevo ancho.

**Q: ¿Por qué se llama a `myDoc.UpdatePageLayout()` después de establecer el tamaño de papel a A4?**  
A: `UpdatePageLayout()` obliga al motor de diseño a reevaluar las dimensiones de la página, asegurando que `docBuilder.PageSetup.PageWidth` refleje el nuevo ancho A4 antes de que se recalcule el tamaño del gráfico.

**Q: ¿Qué ocurre si la forma insertada no contiene realmente un gráfico?**  
A: La condición `if (chartContainer.HasChart)` evita que el código asigne `Width` y `Height` cuando no hay un gráfico presente, evitando una excepción en tiempo de ejecución.

**Q: ¿Puedo cambiar el factor de escala del 80 % a otro valor?**  
A: Absolutamente—reemplace el multiplicador `0.8` por cualquier proporción que prefiera; el resto de la lógica de redimensionado seguirá conservando la relación de aspecto original.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}