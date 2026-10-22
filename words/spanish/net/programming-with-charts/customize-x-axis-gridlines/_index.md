---
title: Personalice las líneas de cuadrícula del eje X en un gráfico de columnas usando Aspose.Words for .NET
weight: 610
limit:
description: Aprenda a añadir y personalizar el color de las líneas de cuadrícula principales del eje X en un gráfico de columnas de Word con Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, column chart, customize x axis gridlines, word chart gridlines, primary x axis gridlines, chart formatting .NET]
url: /net/programming-with-charts/customize-x-axis-gridlines/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aprenda a añadir y personalizar el color de las líneas de cuadrícula
    principales del eje X en un gráfico de columnas de Word con Aspose.Words for .NET.
  headline: Personalice las líneas de cuadrícula del eje X en un gráfico de columnas
    usando Aspose.Words for .NET
  type: TechArticle
- description: Aprenda a añadir y personalizar el color de las líneas de cuadrícula
    principales del eje X en un gráfico de columnas de Word con Aspose.Words for .NET.
  name: Personalice las líneas de cuadrícula del eje X en un gráfico de columnas usando
    Aspose.Words for .NET
  steps:
  - name: Cree un nuevo documento de Word y un DocumentBuilder para editarlo.
    text: Cree un nuevo documento de Word y un DocumentBuilder para editarlo.
  - name: Inserte un gráfico de columnas de 432×252 en el documento y obtenga su objeto
      Chart.
    text: Inserte un gráfico de columnas de 432×252 en el documento y obtenga su objeto
      Chart.
  - name: Elimine la serie predeterminada y añada una serie personalizada con tres
      grupos y valores.
    text: Elimine la serie predeterminada y añada una serie personalizada con tres
      grupos y valores.
  - name: Obtenga una referencia al eje horizontal (X) primario del gráfico.
    text: Obtenga una referencia al eje horizontal (X) primario del gráfico.
  - name: Habilite la visualización de las líneas de cuadrícula principales en el
      eje X primario.
    text: Habilite la visualización de las líneas de cuadrícula principales en el
      eje X primario.
  - name: Establezca el color de las líneas de cuadrícula en azul y su grosor en 2
      puntos.
    text: Establezca el color de las líneas de cuadrícula en azul y su grosor en 2
      puntos.
  - name: Guarde el documento en un archivo .docx.
    text: Guarde el documento en un archivo .docx.
  type: HowTo
- questions:
  - answer: 'Establezca la misma propiedad del eje a false: `horizontalAxis.HasMajorGridlines
      = false;` alterna la visibilidad de las líneas de cuadrícula principales del
      eje X.'
    question: ¿Cómo oculto nuevamente las líneas de cuadrícula principales después
      de habilitarlas?
  - answer: No, la configuración `Format.Stroke` se aplica solo al eje que modifica;
      para dar estilo a las líneas de cuadrícula del eje Y debe ajustar `chart.AxisY.Format.Stroke`
      por separado.
    question: ¿Cambiar `horizontalAxis.Format.Stroke.Color` también afectará a las
      líneas de cuadrícula del eje Y?
  - answer: Utilice `horizontalAxis.Format.Stroke.Weight` y asigne un valor double
      (p. ej., `0.5`) para hacer las líneas de cuadrícula más delgadas.
    question: ¿Qué propiedad controla el grosor de las líneas de cuadrícula principales
      del eje X?
  - answer: Sí, establezca `horizontalAxis.Format.Stroke.DashStyle` a un valor del
      enumerado `DashStyle`, como `DashStyle.Dash` o `DashStyle.Dot`.
    question: ¿Puedo cambiar el patrón de guiones de las líneas de cuadrícula principales
      del eje X?
  type: FAQPage
images:
- /net/programming-with-charts/customize-x-axis-gridlines/og-image.png
og_title: Estilice las líneas de cuadrícula del eje X en un gráfico de columnas de Word
og_description: Active y personalice el color de las líneas de cuadrícula del eje X primario de un gráfico de Word con Aspose.Words for .NET.
og_image_alt: Guía que muestra un documento de Word con un gráfico de columnas donde las líneas de cuadrícula principales del eje X primario están resaltadas con un color personalizado usando Aspose.Words for .NET.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Personalice las líneas de cuadrícula del eje X en un gráfico de columnas usando Aspose.Words
En este tutorial aprenderá cómo crear un documento de Word, insertar un gráfico de columnas, reemplazar sus datos predeterminados y luego habilitar las líneas de cuadrícula principales en el eje X primario. También verá cómo cambiar el color de línea de las líneas de cuadrícula para que coincida con su diseño. Siga el código paso a paso para obtener un control preciso sobre la visibilidad y el estilo de las líneas de cuadrícula del eje X.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/customize-x-axis-gridlines" >}}


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

**Q: ¿Cómo oculto nuevamente las líneas de cuadrícula principales después de habilitarlas?**  
A: Establezca la misma propiedad del eje a false: `horizontalAxis.HasMajorGridlines = false;` alterna la visibilidad de las líneas de cuadrícula principales del eje X.

**Q: ¿Cambiar `horizontalAxis.Format.Stroke.Color` también afectará a las líneas de cuadrícula del eje Y?**  
A: No, la configuración `Format.Stroke` se aplica solo al eje que modifica; para dar estilo a las líneas de cuadrícula del eje Y debe ajustar `chart.AxisY.Format.Stroke` por separado.

**Q: ¿Qué propiedad controla el grosor de las líneas de cuadrícula principales del eje X?**  
A: Utilice `horizontalAxis.Format.Stroke.Weight` y asigne un valor double (p. ej., `0.5`) para hacer las líneas de cuadrícula más delgadas.

**Q: ¿Puedo cambiar el patrón de guiones de las líneas de cuadrícula principales del eje X?**  
A: Sí, establezca `horizontalAxis.Format.Stroke.DashStyle` a un valor del enumerado `DashStyle`, como `DashStyle.Dash` o `DashStyle.Dot`.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}