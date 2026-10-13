---
title: Establecer etiquetas de datos uniformes en un gráfico de columnas usando Aspose.Words for .NET
weight: 110
limit:
description: Aprenda a crear un gráfico de columnas Word y aplicar un tamaño y color de fuente uniformes a las etiquetas de datos de todas las series con Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, uniform data labels, chart data label formatting, column chart Word SDK, default data label style, Word document chart customization]
url: /net/programming-with-charts/uniform-data-labels/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aprenda a crear un gráfico de columnas Word y aplicar un tamaño y color
    de fuente uniformes a las etiquetas de datos de todas las series con Aspose.Words
    for .NET.
  headline: Establecer etiquetas de datos uniformes en un gráfico de columnas usando
    Aspose.Words for .NET
  type: TechArticle
- description: Aprenda a crear un gráfico de columnas Word y aplicar un tamaño y color
    de fuente uniformes a las etiquetas de datos de todas las series con Aspose.Words
    for .NET.
  name: Establecer etiquetas de datos uniformes en un gráfico de columnas usando Aspose.Words
    for .NET
  steps:
  - name: Cree un nuevo documento Word vacío y un DocumentBuilder para editarlo.
    text: Cree un nuevo documento Word vacío y un DocumentBuilder para editarlo.
  - name: Inserte un gráfico de columnas de 500×300 en el documento y obtenga su objeto
      Chart.
    text: Inserte un gráfico de columnas de 500×300 en el documento y obtenga su objeto
      Chart.
  - name: Elimine la serie de muestra predeterminada que Aspose.Words agrega a un
      gráfico nuevo.
    text: Elimine la serie de muestra predeterminada que Aspose.Words agrega a un
      gráfico nuevo.
  - name: Defina las etiquetas de categoría y agregue dos series de datos (Item Alpha
      y Item Beta) con sus valores al gráfico.
    text: Defina las etiquetas de categoría y agregue dos series de datos (Item Alpha
      y Item Beta) con sus valores al gráfico.
  - name: Establezca el tamaño y color de fuente base que se aplicará a todas las
      etiquetas de datos.
    text: Establezca el tamaño y color de fuente base que se aplicará a todas las
      etiquetas de datos.
  - name: Habilite las etiquetas de datos para cada serie, muestre el valor numérico
      y aplique el tamaño y color de fuente predefinidos.
    text: Habilite las etiquetas de datos para cada serie, muestre el valor numérico
      y aplique el tamaño y color de fuente predefinidos.
  - name: Guarde el documento en un archivo .docx.
    text: Guarde el documento en un archivo .docx.
  type: HowTo
- questions:
  - answer: '`InsertChart` crea un gráfico con una serie de muestra predeterminada;
      al borrarla se elimina ese marcador de posición, de modo que el gráfico solo
      muestra las series que usted agrega (`Item Alpha` y `Item Beta`).'
    question: ¿Por qué necesito llamar a `chart.Series.Clear()` antes de agregar mis
      propias series?
  - answer: Reemplace `Color.White` por cualquier valor de `System.Drawing.Color`,
      por ejemplo, `Color.Black` o `Color.FromArgb(255, 30, 144, 255)`; el nuevo color
      se aplica mediante `series.DataLabels.Font.Color` dentro del bucle.
    question: ¿Cómo puedo cambiar el color de la etiqueta de datos a algo distinto
      de blanco?
  - answer: Las etiquetas de datos se ocultarán, por lo que la configuración de fuente
      que aplicó quedará invisible; debe mantener `HasDataLabels` en `true` para que
      las etiquetas (y su estilo) aparezcan.
    question: ¿Qué ocurre si establezco `series.HasDataLabels = false` después de
      configurar el tamaño y color de la fuente?
  - answer: 'Sí: cada `ChartSeries` tiene su propio objeto `DataLabels`, por lo que
      cualquier serie añadida después del bucle inicial también debe tener `HasDataLabels`,
      `ShowValue` y las propiedades de fuente configuradas, ya sea recorriendo nuevamente
      o extrayendo el estilo a un método auxiliar.'
    question: ¿Necesito recorrer nuevamente las series si agrego otra serie más adelante
      en el código?
  type: FAQPage
images:
- /net/programming-with-charts/uniform-data-labels/og-image.png
og_title: Aplicar etiquetas de datos uniformes a un gráfico Word
og_description: Asigne rápidamente a cada etiqueta del gráfico el mismo tamaño de fuente y color con Aspose.Words for .NET.
og_image_alt: Guía que muestra un documento Word con un gráfico de columnas donde todas las etiquetas de datos comparten el mismo tamaño de fuente y color, creado con Aspose.Words for .NET.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Establecer etiquetas de datos uniformes en un gráfico de columnas usando Aspose.Words
Este tutorial muestra cómo generar un documento Word, insertar un gráfico de columnas y agregar series de datos personalizadas con Aspose.Words for .NET. Luego demuestra cómo definir el tamaño y color de fuente predeterminados de las etiquetas de datos para que cada serie del gráfico muestre etiquetas idénticas. Al aplicar un único estilo, garantiza una apariencia visual coherente en todo el gráfico.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/uniform-data-labels" >}}


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

**Q: ¿Por qué necesito llamar a `chart.Series.Clear()` antes de agregar mis propias series?**  
A: `InsertChart` crea un gráfico con una serie de muestra predeterminada; al borrarla se elimina ese marcador de posición, de modo que el gráfico solo muestra las series que usted agrega (`Item Alpha` y `Item Beta`).

**Q: ¿Cómo puedo cambiar el color de la etiqueta de datos a algo distinto de blanco?**  
A: Reemplace `Color.White` por cualquier valor de `System.Drawing.Color`, por ejemplo, `Color.Black` o `Color.FromArgb(255, 30, 144, 255)`; el nuevo color se aplica mediante `series.DataLabels.Font.Color` dentro del bucle.

**Q: ¿Qué ocurre si establezco `series.HasDataLabels = false` después de configurar el tamaño y color de la fuente?**  
A: Las etiquetas de datos se ocultarán, por lo que la configuración de fuente que aplicó quedará invisible; debe mantener `HasDataLabels` en `true` para que las etiquetas (y su estilo) aparezcan.

**Q: ¿Necesito recorrer nuevamente las series si agrego otra serie más adelante en el código?**  
A: Sí: cada `ChartSeries` tiene su propio objeto `DataLabels`, por lo que cualquier serie añadida después del bucle inicial también debe tener `HasDataLabels`, `ShowValue` y las propiedades de fuente configuradas, ya sea recorriendo nuevamente o extrayendo el estilo a un método auxiliar.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}