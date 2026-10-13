---
title: Formatear el eje Y secundario como moneda en un gráfico Word usando Aspose.Words for .NET
weight: 710
limit:
description: Aprenda a añadir y formatear un eje Y secundario como moneda en un gráfico de líneas Word con Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, format secondary axis, currency axis formatting, Word line chart secondary series, secondary Y axis .NET, chart axis number format]
url: /net/programming-with-charts/format-secondary-axis/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aprenda a añadir y formatear un eje Y secundario como moneda en un
    gráfico de líneas Word con Aspose.Words for .NET.
  headline: Formatear el eje Y secundario como moneda en un gráfico Word usando Aspose.Words
    for .NET
  type: TechArticle
- description: Aprenda a añadir y formatear un eje Y secundario como moneda en un
    gráfico de líneas Word con Aspose.Words for .NET.
  name: Formatear el eje Y secundario como moneda en un gráfico Word usando Aspose.Words
    for .NET
  steps:
  - name: Cree un nuevo documento Word vacío y un DocumentBuilder para editarlo.
    text: Cree un nuevo documento Word vacío y un DocumentBuilder para editarlo.
  - name: Inserte un gráfico de líneas de tamaño 450×250 puntos en el documento y
      obtenga su objeto Chart.
    text: Inserte un gráfico de líneas de tamaño 450×250 puntos en el documento y
      obtenga su objeto Chart.
  - name: Elimine la serie de marcador de posición predeterminada que Aspose agrega
      a un gráfico nuevo.
    text: Elimine la serie de marcador de posición predeterminada que Aspose agrega
      a un gráfico nuevo.
  - name: Defina etiquetas de trimestres y añada una serie de datos primaria con valores
      de ejemplo al gráfico.
    text: Defina etiquetas de trimestres y añada una serie de datos primaria con valores
      de ejemplo al gráfico.
  - name: Cree un grupo de series secundario de tipo Line y asígnelo al grupo de ejes
      secundarios.
    text: Cree un grupo de series secundario de tipo Line y asígnelo al grupo de ejes
      secundarios.
  - name: Oculte el eje X secundario para que solo sea visible el eje Y secundario.
    text: Oculte el eje X secundario para que solo sea visible el eje Y secundario.
  - name: Muestre el título del eje Y secundario y establezca su texto a "Sales (USD)".
    text: Muestre el título del eje Y secundario y establezca su texto a "Sales (USD)".
  - name: Establezca el formato numérico del eje Y secundario a un patrón de moneda
      con dos decimales y desvínculelo del formato de origen.
    text: Establezca el formato numérico del eje Y secundario a un patrón de moneda
      con dos decimales y desvínculelo del formato de origen.
  - name: Añada una serie auxiliar al grupo secundario, proporcionando datos que se
      trazarán contra el eje Y secundario.
    text: Añada una serie auxiliar al grupo secundario, proporcionando datos que se
      trazarán contra el eje Y secundario.
  - name: Guarde el documento final en un archivo llamado ProfitChart.docx en el directorio
      actual.
    text: Guarde el documento final en un archivo llamado ProfitChart.docx en el directorio
      actual.
  type: HowTo
- questions:
  - answer: El gráfico conservará la serie de marcador de posición predeterminada
      que Aspose.Words inserta, por lo que su "Main Series" personalizada aparecerá
      junto a puntos de datos no deseados.
    question: ¿Qué ocurre si omito la llamada `lineChart.Series.Clear()`?
  - answer: Establezca `secondarySeriesGroup.AxisX.Hidden = false;` (o simplemente
      omita la línea que lo establece a `true`).
    question: ¿Cómo puedo mostrar el eje X secundario en lugar de ocultarlo?
  - answer: Sí – cambie la cadena de formato, por ejemplo `secondarySeriesGroup.AxisY.NumberFormat.FormatCode
      = "\"€\"#,##0.00";` para euros o ajuste el patrón según su configuración regional.
    question: ¿Puedo usar un símbolo de moneda o formato diferente para el eje Y secundario?
  - answer: Cuando `IsLinkedToSource` es true, el eje hereda el formato numérico de
      la fuente de datos subyacente, sobrescribiendo cualquier `FormatCode` personalizado;
      establecerlo en false obliga al gráfico a usar el formato que usted especifica.
    question: ¿Por qué es necesario establecer `IsLinkedToSource = false` al aplicar
      un formato numérico personalizado?
  - answer: Sí, asigne `secondarySeriesGroup.AxisY.Position = AxisPosition.Left;`
      (o `Right` para el valor predeterminado) para controlar en qué lado se dibuja
      el eje.
    question: ¿Es posible mover el eje Y secundario al lado izquierdo del gráfico?
  type: FAQPage
images:
- /net/programming-with-charts/format-secondary-axis/og-image.png
og_title: Formatear el eje secundario de un Chart como moneda
og_description: Aprenda a añadir un eje Y secundario a un gráfico de líneas Word y a darle estilo de moneda con dos decimales.
og_image_alt: Captura de pantalla que muestra un gráfico de líneas Word con un eje Y secundario formateado como moneda usando Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Formatear el eje Y secundario como moneda en un gráfico Word usando Aspose.Words
En este tutorial verá cómo crear un documento Word, insertar un gráfico de líneas, añadir un eje Y secundario, formatear ese eje como moneda con dos decimales y vincularle una serie de datos secundaria usando Aspose.Words for .NET. Formatear el eje secundario como moneda le permite presentar claramente datos financieros junto a la serie primaria. Siga el código paso a paso para ver el gráfico renderizado directamente en el documento generado.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/format-secondary-axis" >}}


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

**Q: ¿Qué ocurre si omito la llamada `lineChart.Series.Clear()`?**  
A: El gráfico conservará la serie de marcador de posición predeterminada que Aspose.Words inserta, por lo que su "Main Series" personalizada aparecerá junto a puntos de datos no deseados.

**Q: ¿Cómo puedo mostrar el eje X secundario en lugar de ocultarlo?**  
A: Establezca `secondarySeriesGroup.AxisX.Hidden = false;` (o simplemente omita la línea que lo establece a `true`).

**Q: ¿Puedo usar un símbolo de moneda o formato diferente para el eje Y secundario?**  
A: Sí – cambie la cadena de formato, por ejemplo `secondarySeriesGroup.AxisY.NumberFormat.FormatCode = "\"€\"#,##0.00";` para euros o ajuste el patrón según su configuración regional.

**Q: ¿Por qué es necesario establecer `IsLinkedToSource = false` al aplicar un formato numérico personalizado?**  
A: Cuando `IsLinkedToSource` es true, el eje hereda el formato numérico de la fuente de datos subyacente, sobrescribiendo cualquier `FormatCode` personalizado; establecerlo en false obliga al gráfico a usar el formato que usted especifica.

**Q: ¿Es posible mover el eje Y secundario al lado izquierdo del gráfico?**  
A: Sí, asigne `secondarySeriesGroup.AxisY.Position = AxisPosition.Left;` (o `Right` para el valor predeterminado) para controlar en qué lado se dibuja el eje.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}