---
title: Ocultar el borde del área de trazado en un gráfico de columnas con Aspose.Words para .NET
weight: 410
limit:
description: Aprenda a ocultar el borde del área de trazado de un gráfico mientras mantiene visibles las líneas de los ejes en un gráfico de columnas Word usando Aspose.Words para .NET.
keywords: [aspose.words for .net, hide plot border, column chart, chart formatting, word document chart, plot area border removal]
url: /net/programming-with-charts/hide-plot-border/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aprenda a ocultar el borde del área de trazado de un gráfico mientras
    mantiene visibles las líneas de los ejes en un gráfico de columnas Word usando
    Aspose.Words para .NET.
  headline: Ocultar el borde del área de trazado en un gráfico de columnas con Aspose.Words
    para .NET
  type: TechArticle
- description: Aprenda a ocultar el borde del área de trazado de un gráfico mientras
    mantiene visibles las líneas de los ejes en un gráfico de columnas Word usando
    Aspose.Words para .NET.
  name: Ocultar el borde del área de trazado en un gráfico de columnas con Aspose.Words
    para .NET
  steps:
  - name: Cree un nuevo documento Word vacío y un DocumentBuilder para editarlo.
    text: Cree un nuevo documento Word vacío y un DocumentBuilder para editarlo.
  - name: Inserte un gráfico de columnas de 432×252 en el documento y obtenga su objeto
      Chart.
    text: Inserte un gráfico de columnas de 432×252 en el documento y obtenga su objeto
      Chart.
  - name: Elimine cualquier serie existente, defina tres etiquetas de categoría y
      añada una serie con valores de ejemplo al gráfico.
    text: Elimine cualquier serie existente, defina tres etiquetas de categoría y
      añada una serie con valores de ejemplo al gráfico.
  - name: Establezca el grosor del trazo del área de trazado a cero, eliminando su
      borde mientras se mantienen visibles las líneas de los ejes.
    text: Establezca el grosor del trazo del área de trazado a cero, eliminando su
      borde mientras se mantienen visibles las líneas de los ejes.
  - name: Guarde el documento modificado en un archivo .docx.
    text: Guarde el documento modificado en un archivo .docx.
  type: HowTo
- questions:
  - answer: La propiedad `Stroke` pertenece al formato general del objeto `Chart`,
      que dibuja el borde rectangular alrededor del área de trazado; las líneas de
      los ejes son objetos `Axis` independientes y no se ven afectadas por la configuración
      `Stroke` del gráfico.
    question: ¿Por qué al establecer `columnChart.Format.Stroke.Weight = 0` se elimina
      el borde del área de trazado pero se dejan visibles las líneas de los ejes?
  - answer: No, la propiedad `Stroke` controla todo el borde del área de trazado como
      un único rectángulo, por lo que no se pueden ocultar bordes parciales mediante
      Aspose.Words; tendría que superponer formas personalizadas o editar el gráfico
      manualmente.
    question: ¿Puedo ocultar solo un lado del borde del área de trazado (p. ej., el
      lado izquierdo) mientras mantengo los otros tres lados visibles?
  - answer: Sí, la propiedad `Stroke` es independiente de `ChartType`, por lo que
      establecer su `Weight` en 0 elimina el borde del área de trazado para gráficos
      de Línea, Circular o cualquier otro tipo de gráfico compatible.
    question: Si cambio el tipo de gráfico a Línea o Circular, ¿`columnChart.Format.Stroke.Weight
      = 0` seguirá ocultando el borde del área de trazado?
  - answer: No se requiere una actualización adicional; al eliminar las series y añadir
      una nueva se actualiza el gráfico internamente, y `wordDoc.Save(...)` escribe
      el estado actual en el archivo .docx.
    question: Después de llamar a `columnChart.Series.Clear()`, ¿es necesario actualizar
      el gráfico antes de guardar el documento?
  type: FAQPage
images:
- /net/programming-with-charts/hide-plot-border/og-image.png
og_title: Ocultar el borde del área de trazado en un gráfico de columnas Word
og_description: Elimine el borde del área de trazado mientras mantiene visibles las líneas de los ejes en un gráfico de columnas Word usando Aspose.Words para .NET.
og_image_alt: Guía que muestra un documento Word con un gráfico de columnas donde el borde del área de trazado está oculto pero las líneas de los ejes permanecen visibles usando Aspose.Words para .NET.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ocultar el borde del área de trazado en un gráfico de columnas con Aspose.Words para .NET
En este tutorial aprenderá a generar un documento Word, insertar un gráfico de columnas, rellenarlo con datos de ejemplo y luego ocultar el borde del área de trazado del gráfico mientras se mantienen visibles las líneas de los ejes. El código paso a paso muestra cada operación y finaliza guardando el documento, para que pueda ver el resultado de inmediato.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/hide-plot-border" >}}


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

**Q: ¿Por qué al establecer `columnChart.Format.Stroke.Weight = 0` se elimina el borde del área de trazado pero se dejan visibles las líneas de los ejes?**  
A: La propiedad `Stroke` pertenece al formato general del objeto `Chart`, que dibuja el borde rectangular alrededor del área de trazado; las líneas de los ejes son objetos `Axis` independientes y no se ven afectadas por la configuración `Stroke` del gráfico.

**Q: ¿Puedo ocultar solo un lado del borde del área de trazado (p. ej., el lado izquierdo) mientras mantengo los otros tres lados visibles?**  
A: No, la propiedad `Stroke` controla todo el borde del área de trazado como un único rectángulo, por lo que no se pueden ocultar bordes parciales mediante Aspose.Words; tendría que superponer formas personalizadas o editar el gráfico manualmente.

**Q: Si cambio el tipo de gráfico a Línea o Circular, ¿`columnChart.Format.Stroke.Weight = 0` seguirá ocultando el borde del área de trazado?**  
A: Sí, la propiedad `Stroke` es independiente de `ChartType`, por lo que establecer su `Weight` en 0 elimina el borde del área de trazado para gráficos de Línea, Circular o cualquier otro tipo de gráfico compatible.

**Q: Después de llamar a `columnChart.Series.Clear()`, ¿es necesario actualizar el gráfico antes de guardar el documento?**  
A: No se requiere una actualización adicional; al eliminar las series y añadir una nueva se actualiza el gráfico internamente, y `wordDoc.Save(...)` escribe el estado actual en el archivo .docx.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}