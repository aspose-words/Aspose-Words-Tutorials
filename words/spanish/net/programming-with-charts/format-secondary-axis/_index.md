---
title: Formatear el eje X secundario y establecer unidades de visualización en miles en gráficos de líneas de Word usando Aspose.Words para .NET
weight: 710
limit:
description: Cree un gráfico de líneas de Word, agregue un eje X secundario, establezca su unidad de visualización en miles y aplique un formato numérico personalizado con Aspose.Words para .NET.
keywords: [secondary axis formatting, Aspose.Words for .NET, line chart axis units, display units thousands, custom numeric format axis, Word chart secondary X axis]
url: /net/programming-with-charts/format-secondary-axis/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Cree un gráfico de líneas de Word, agregue un eje X secundario, establezca
    su unidad de visualización en miles y aplique un formato numérico personalizado
    con Aspose.Words para .NET.
  headline: Formatear el eje X secundario y establecer unidades de visualización en
    miles en gráficos de líneas de Word usando Aspose.Words para .NET
  type: TechArticle
- description: Cree un gráfico de líneas de Word, agregue un eje X secundario, establezca
    su unidad de visualización en miles y aplique un formato numérico personalizado
    con Aspose.Words para .NET.
  name: Formatear el eje X secundario y establecer unidades de visualización en miles
    en gráficos de líneas de Word usando Aspose.Words para .NET
  steps:
  - name: Cree un nuevo Document y un DocumentBuilder para comenzar a construir el
      archivo de Word.
    text: Cree un nuevo Document y un DocumentBuilder para comenzar a construir el
      archivo de Word.
  - name: Inserte un gráfico de líneas de tamaño 500×300 en el documento y obtenga
      el objeto Chart.
    text: Inserte un gráfico de líneas de tamaño 500×300 en el documento y obtenga
      el objeto Chart.
  - name: Elimine la serie de demostración predeterminada que Aspose.Words agrega
      automáticamente.
    text: Elimine la serie de demostración predeterminada que Aspose.Words agrega
      automáticamente.
  - name: Defina una matriz de etiquetas de categoría que se utilizará para el eje
      X.
    text: Defina una matriz de etiquetas de categoría que se utilizará para el eje
      X.
  - name: Agregue la serie de datos primaria llamada "Main Data" usando las etiquetas
      y los valores.
    text: Agregue la serie de datos primaria llamada "Main Data" usando las etiquetas
      y los valores.
  - name: Cree un grupo de series secundario de tipo Line y asígnelo al grupo de eje
      secundario.
    text: Cree un grupo de series secundario de tipo Line y asígnelo al grupo de eje
      secundario.
  - name: Establezca la unidad de visualización del eje X secundario en miles para
      que los valores se muestren en K.
    text: Establezca la unidad de visualización del eje X secundario en miles para
      que los valores se muestren en K.
  - name: Aplique un formato numérico personalizado "#,##0.0" a las etiquetas de marcas
      del eje X secundario.
    text: Aplique un formato numérico personalizado "#,##0.0" a las etiquetas de marcas
      del eje X secundario.
  - name: Opcionalmente, agregue una serie de datos auxiliar al grupo secundario.
    text: Opcionalmente, agregue una serie de datos auxiliar al grupo secundario.
  - name: Guarde el documento en un archivo .docx.
    text: Guarde el documento en un archivo .docx.
  type: HowTo
- questions:
  - answer: 'No: la configuración `AxisX` pertenece a `ChartSeriesGroup`, por lo que
      puede establecer `secondaryGroup.AxisX.DisplayUnit.Unit` y `secondaryGroup.AxisX.NumberFormat.FormatCode`
      antes o después de agregar series; la configuración se aplicará al eje del grupo
      en cualquier caso.'
    question: ¿Tengo que agregar la serie secundaria antes de establecer la unidad
      de visualización y el formato numérico en el eje X secundario?
  - answer: 'Sí: asigne cualquier valor de `AxisBuiltInUnit`, por ejemplo `secondaryGroup.AxisX.DisplayUnit.Unit
      = AxisBuiltInUnit.Millions;` para mostrar los valores del eje en millones en
      lugar de miles.'
    question: ¿Puedo usar una unidad incorporada diferente, como millones, para el
      eje X secundario?
  - answer: 'No: el código de formato se aplica solo al eje que modifica (`secondaryGroup.AxisX.NumberFormat.FormatCode`),
      por lo que el eje X primario conserva su formato predeterminado.'
    question: ¿El formato personalizado "#,##0.0" afectará las etiquetas del eje X
      primario?
  - answer: El gráfico contendrá la serie de demostración predeterminada además de
      las que agregue, lo que puede generar líneas extra y categorías desajustadas;
      limpiar la colección garantiza que solo aparezcan los datos que desea.
    question: ¿Qué ocurre si olvido limpiar la serie de demostración con `lineChart.Series.Clear();`?
  type: FAQPage
images:
- /net/programming-with-charts/format-secondary-axis/og-image.png
og_title: Formatear eje X secundario y establecer unidades en miles
og_description: Agregue un eje X secundario a un gráfico de líneas de Word y formatee sus etiquetas en miles con un patrón personalizado.
og_image_alt: Guía que muestra cómo agregar un eje X secundario a un gráfico de líneas de Word y formatear sus etiquetas para mostrar unidades en miles usando Aspose.Words para .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Formatear el eje X secundario y establecer unidades de visualización en miles en gráficos de líneas de Word usando Aspose.Words para .NET
Este tutorial le guía paso a paso para crear un documento de Word que contiene un gráfico de líneas, agregar un eje X secundario y configurar ese eje para mostrar valores en miles. También aprenderá cómo aplicar un formato numérico personalizado a las etiquetas del eje secundario, lo que le brinda un control preciso sobre cómo se presentan los datos. Siga los pasos para mejorar la legibilidad de los gráficos de varios ejes en sus informes de Word.

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

**Q: ¿Tengo que agregar la serie secundaria antes de establecer la unidad de visualización y el formato numérico en el eje X secundario?**  
A: No: la configuración `AxisX` pertenece a `ChartSeriesGroup`, por lo que puede establecer `secondaryGroup.AxisX.DisplayUnit.Unit` y `secondaryGroup.AxisX.NumberFormat.FormatCode` antes o después de agregar series; la configuración se aplicará al eje del grupo en cualquier caso.

**Q: ¿Puedo usar una unidad incorporada diferente, como millones, para el eje X secundario?**  
A: Sí: asigne cualquier valor de `AxisBuiltInUnit`, por ejemplo `secondaryGroup.AxisX.DisplayUnit.Unit = AxisBuiltInUnit.Millions;` para mostrar los valores del eje en millones en lugar de miles.

**Q: ¿El formato personalizado "#,##0.0" afectará las etiquetas del eje X primario?**  
A: No: el código de formato se aplica solo al eje que modifica (`secondaryGroup.AxisX.NumberFormat.FormatCode`), por lo que el eje X primario conserva su formato predeterminado.

**Q: ¿Qué ocurre si olvido limpiar la serie de demostración con `lineChart.Series.Clear();`?**  
A: El gráfico contendrá la serie de demostración predeterminada además de las que agregue, lo que puede generar líneas extra y categorías desajustadas; limpiar la colección garantiza que solo aparezcan los datos que desea.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}