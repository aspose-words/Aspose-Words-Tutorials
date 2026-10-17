---
title: Actualizar el título del gráfico y alternar la visibilidad de la leyenda en Word usando Aspose.Words for .NET
weight: 810
limit:
description: Aprende a cambiar el título de un gráfico y controlar la visibilidad de la leyenda en un documento Word con Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, update chart title, toggle legend visibility, word chart manipulation, c# chart title, aspose words chart legend]
url: /net/programming-with-charts/update-chart-title/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aprende a cambiar el título de un gráfico y controlar la visibilidad
    de la leyenda en un documento Word con Aspose.Words for .NET.
  headline: Actualizar el título del gráfico y alternar la visibilidad de la leyenda
    en Word usando Aspose.Words for .NET
  type: TechArticle
- description: Aprende a cambiar el título de un gráfico y controlar la visibilidad
    de la leyenda en un documento Word con Aspose.Words for .NET.
  name: Actualizar el título del gráfico y alternar la visibilidad de la leyenda en
    Word usando Aspose.Words for .NET
  steps:
  - name: Define el título del gráfico suministrado por el usuario y si la leyenda
      debe mostrarse.
    text: Define el título del gráfico suministrado por el usuario y si la leyenda
      debe mostrarse.
  - name: Crea un nuevo documento Word y un DocumentBuilder para añadir contenido.
    text: Crea un nuevo documento Word y un DocumentBuilder para añadir contenido.
  - name: Inserta un gráfico de columnas de 432 × 252 pt en el documento y verifica
      que la forma realmente contenga un gráfico.
    text: Inserta un gráfico de columnas de 432 × 252 pt en el documento y verifica
      que la forma realmente contenga un gráfico.
  - name: Obtén el objeto chart, establece su texto de título al valor del usuario
      y asegura que el título se muestre.
    text: Obtén el objeto chart, establece su texto de título al valor del usuario
      y asegura que el título se muestre.
  - name: 'Configura la leyenda: muéstrala a la derecha si se solicita, de lo contrario
      ocúltala, y permite que se superponga al área del gráfico.'
    text: 'Configura la leyenda: muéstrala a la derecha si se solicita, de lo contrario
      ocúltala, y permite que se superponga al área del gráfico.'
  - name: Guarda el documento modificado en disco como CustomChart.docx.
    text: Guarda el documento modificado en disco como CustomChart.docx.
  type: HowTo
- questions:
  - answer: Cuando `displayLegend` es `true`, el código establece `chartLegend.Position`
      en `LegendPosition.Right`, haciendo que la leyenda sea visible en el lado derecho
      del área del gráfico; la propiedad `Overlay` permanece en `true`, por lo que
      la leyenda puede superponerse al gráfico para ahorrar espacio.
    question: ¿Qué cambia al establecer `displayLegend` en `true` en el gráfico generado?
  - answer: Establece `chartTitle.Show = false` (o simplemente omite establecer `Show`
      en `true`) después de asignar `chartTitle.Text`; el título no se renderizará
      en el documento Word.
    question: ¿Cómo puedo ocultar el título del gráfico si el usuario no proporciona
      uno?
  - answer: Sí—`InsertChart` devuelve un `Shape` que debería contener un gráfico,
      pero verificar `HasChart` asegura que la forma realmente posea un objeto `Chart`;
      de lo contrario, el código lanza una `InvalidOperationException`.
    question: ¿Es necesario comprobar `chartContainer.HasChart` después de llamar
      a `InsertChart`?
  - answer: Absolutamente; asigna cualquier valor del enum `LegendPosition` (p. ej.,
      `LegendPosition.Top`, `LegendPosition.Bottom`, `LegendPosition.Left`) a `chartLegend.Position`
      para reposicionar la leyenda según sea necesario.
    question: ¿Puedo colocar la leyenda en otro lugar que no sea el lado derecho?
  type: FAQPage
images:
- /net/programming-with-charts/update-chart-title/og-image.png
og_title: Cambiar título del gráfico y leyenda en Word
og_description: Aprende a establecer un título de gráfico personalizado y controlar la visualización de la leyenda en un documento Word con Aspose.Words for .NET.
og_image_alt: Guía que muestra código que actualiza el título de un gráfico y alterna la leyenda en un documento Word usando Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Actualizar el título del gráfico y alternar la visibilidad de la leyenda en Word usando Aspose.Words
Este tutorial muestra cómo modificar programáticamente un gráfico dentro de un documento Word con Aspose.Words for .NET. Aprenderás a insertar un gráfico de columnas, reemplazar su título con texto suministrado por el usuario y controlar la visibilidad y superposición de la leyenda según las preferencias del usuario. Estos pasos te permiten personalizar la presentación del gráfico de forma dinámica sin edición manual.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/update-chart-title" >}}


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

**Q: ¿Qué cambia al establecer `displayLegend` en `true` en el gráfico generado?**  
A: Cuando `displayLegend` es `true`, el código establece `chartLegend.Position` en `LegendPosition.Right`, haciendo que la leyenda sea visible en el lado derecho del área del gráfico; la propiedad `Overlay` permanece en `true`, por lo que la leyenda puede superponerse al gráfico para ahorrar espacio.

**Q: ¿Cómo puedo ocultar el título del gráfico si el usuario no proporciona uno?**  
A: Establece `chartTitle.Show = false` (o simplemente omite establecer `Show` en `true`) después de asignar `chartTitle.Text`; el título no se renderizará en el documento Word.

**Q: ¿Es necesario comprobar `chartContainer.HasChart` después de llamar a `InsertChart`?**  
A: Sí—`InsertChart` devuelve un `Shape` que debería contener un gráfico, pero verificar `HasChart` asegura que la forma realmente posea un objeto `Chart`; de lo contrario, el código lanza una `InvalidOperationException`.

**Q: ¿Puedo colocar la leyenda en otro lugar que no sea el lado derecho?**  
A: Absolutamente; asigna cualquier valor del enum `LegendPosition` (p. ej., `LegendPosition.Top`, `LegendPosition.Bottom`, `LegendPosition.Left`) a `chartLegend.Position` para reposicionar la leyenda según sea necesario.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}