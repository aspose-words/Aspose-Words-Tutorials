---
title: Actualizar los datos de las series del gráfico en un documento Word usando Aspose.Words for .NET
weight: 610
limit:
description: Aprenda a modificar los puntos de datos de las series del gráfico en un documento Word y a actualizar el gráfico usando Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, modify chart series, update chart data points, Word chart manipulation, C# chart editing, column chart in Word]
url: /net/programming-with-charts/modify-chart-series/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aprenda a modificar los puntos de datos de las series del gráfico en
    un documento Word y a actualizar el gráfico usando Aspose.Words for .NET.
  headline: Actualizar los datos de las series del gráfico en un documento Word usando
    Aspose.Words for .NET
  type: TechArticle
- description: Aprenda a modificar los puntos de datos de las series del gráfico en
    un documento Word y a actualizar el gráfico usando Aspose.Words for .NET.
  name: Actualizar los datos de las series del gráfico en un documento Word usando
    Aspose.Words for .NET
  steps:
  - name: Cree un nuevo Document, inserte un gráfico de columnas con DocumentBuilder
      y guárdelo como el archivo inicial.
    text: Cree un nuevo Document, inserte un gráfico de columnas con DocumentBuilder
      y guárdelo como el archivo inicial.
  - name: Abra el archivo guardado y localice la forma del gráfico para obtener el
      objeto Chart existente.
    text: Abra el archivo guardado y localice la forma del gráfico para obtener el
      objeto Chart existente.
  - name: Borre los valores de la primera serie y añada nuevos puntos, luego ajuste
      la segunda serie eliminando su primer punto y añadiendo uno nuevo.
    text: Borre los valores de la primera serie y añada nuevos puntos, luego ajuste
      la segunda serie eliminando su primer punto y añadiendo uno nuevo.
  - name: Guarde el documento modificado en un nuevo archivo que contenga el gráfico
      actualizado.
    text: Guarde el documento modificado en un nuevo archivo que contenga el gráfico
      actualizado.
  type: HowTo
- questions:
  - answer: Use `document.GetChildNodes(NodeType.Shape, true)` para obtener todas
      las formas, luego filtre con `s.HasChart` y seleccione la primera (o la que
      necesite); esto evita seleccionar imágenes o cuadros de texto no relacionados.
    question: ¿Cómo puedo localizar de forma fiable la forma del gráfico en un documento
      que puede contener otras formas?
  - answer: '`ClearValues()` elimina los puntos de datos existentes; sin él, los nuevos
      puntos se añaden a los antiguos, lo que puede generar categorías duplicadas
      o totales incorrectos.'
    question: ¿Por qué necesito llamar a `ClearValues()` antes de añadir nuevos puntos
      a una serie?
  - answer: Use `FromString` cuando las categorías del eje X del gráfico son textuales
      (p.\u00e9., "Group A"), y `FromDouble` cuando el eje espera valores numéricos
      como fechas o mediciones.
    question: ¿Cuándo debo usar `ChartXValue.FromString` en lugar de `ChartXValue.FromDouble`
      para los valores del eje X?
  - answer: Intentar acceder a una serie inexistente lanza una `ArgumentOutOfRangeException`;
      siempre verifique `existingChart.Series.Count` antes de referenciar un índice
      específico.
    question: ¿Qué ocurre si el gráfico tiene solo una serie y trato de acceder a
      `existingChart.Series[1]`?
  - answer: Guardar `openedDoc` es suficiente porque es la instancia del documento
      que contiene el gráfico modificado; el `document` original solo se usó para
      crear el archivo inicial.
    question: ¿Necesito volver a guardar el `document` original después de modificar
      el gráfico, o es suficiente guardar `openedDoc`?
  type: FAQPage
images:
- /net/programming-with-charts/modify-chart-series/og-image.png
og_title: Editar datos de series del gráfico en Word
og_description: Guía paso a paso para cambiar los valores de las series de un gráfico en un archivo Word con Aspose.Words for .NET.
og_image_alt: Guía que muestra un documento Word con un gráfico de columnas antes y después de actualizar sus datos de series usando Aspose.Words for .NET.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Actualizar los datos de las series del gráfico en un documento Word usando Aspose.Words
Este tutorial muestra cómo crear un documento Word que contiene un gráfico de columnas, luego volver a abrir el archivo, obtener las series de gráfico existentes, modificar sus puntos de datos y guardar el documento para que el gráfico muestre los nuevos valores. Siga el código paso a paso para ver lo sencillo que es ajustar programáticamente los datos del gráfico con Aspose.Words for .NET.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/modify-chart-series" >}}


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

**Q: ¿Cómo puedo localizar de forma fiable la forma del gráfico en un documento que puede contener otras formas?**  
A: Use `document.GetChildNodes(NodeType.Shape, true)` para obtener todas las formas, luego filtre con `s.HasChart` y seleccione la primera (o la que necesite); esto evita seleccionar imágenes o cuadros de texto no relacionados.

**Q: ¿Por qué necesito llamar a `ClearValues()` antes de añadir nuevos puntos a una serie?**  
A: `ClearValues()` elimina los puntos de datos existentes; sin él, los nuevos puntos se añaden a los antiguos, lo que puede generar categorías duplicadas o totales incorrectos.

**Q: ¿Cuándo debo usar `ChartXValue.FromString` en lugar de `ChartXValue.FromDouble` para los valores del eje X?**  
A: Use `FromString` cuando las categorías del eje X del gráfico son textuales (p.\u00e9., "Group A"), y `FromDouble` cuando el eje espera valores numéricos como fechas o mediciones.

**Q: ¿Qué ocurre si el gráfico tiene solo una serie y trato de acceder a `existingChart.Series[1]`?**  
A: Intentar acceder a una serie inexistente lanza una `ArgumentOutOfRangeException`; siempre verifique `existingChart.Series.Count` antes de referenciar un índice específico.

**Q: ¿Necesito volver a guardar el `document` original después de modificar el gráfico, o es suficiente guardar `openedDoc`?**  
A: Guardar `openedDoc` es suficiente porque es la instancia del documento que contiene el gráfico modificado; el `document` original solo se usó para crear el archivo inicial.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}