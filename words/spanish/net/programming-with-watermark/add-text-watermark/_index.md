---
title: Agregar marca de agua de texto diagonal roja a documentos Word usando Aspose.Words para .NET
weight: 110
limit:
description: Aplicar automáticamente una marca de agua de texto diagonal roja a cada archivo Word generado en un lote usando Aspose.Words para .NET.
keywords: [Aspose.Words for .NET, text watermark, red diagonal watermark, batch document generation, DocumentBuilder watermark, automated report]
url: /net/programming-with-watermark/add-text-watermark/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Aplicar automáticamente una marca de agua de texto diagonal roja a
    cada archivo Word generado en un lote usando Aspose.Words para .NET.
  headline: Agregar marca de agua de texto diagonal roja a documentos Word usando
    Aspose.Words para .NET
  type: TechArticle
- description: Aplicar automáticamente una marca de agua de texto diagonal roja a
    cada archivo Word generado en un lote usando Aspose.Words para .NET.
  name: Agregar marca de agua de texto diagonal roja a documentos Word usando Aspose.Words
    para .NET
  steps:
  - name: Cree la carpeta "GeneratedReports" donde se guardarán los archivos de salida.
    text: Cree la carpeta "GeneratedReports" donde se guardarán los archivos de salida.
  - name: Inicie un bucle que generará tres documentos separados.
    text: Inicie un bucle que generará tres documentos separados.
  - name: Cree un nuevo objeto de documento Word vacío.
    text: Cree un nuevo objeto de documento Word vacío.
  - name: Utilice DocumentBuilder para escribir una línea de título y una descripción
      en el documento.
    text: Utilice DocumentBuilder para escribir una línea de título y una descripción
      en el documento.
  - name: Defina la apariencia de la marca de agua, incluyendo fuente, tamaño, color
      y disposición diagonal.
    text: Defina la apariencia de la marca de agua, incluyendo fuente, tamaño, color
      y disposición diagonal.
  - name: Aplique la marca de agua diagonal roja configurada con el texto "PROTECTED"
      al documento.
    text: Aplique la marca de agua diagonal roja configurada con el texto "PROTECTED"
      al documento.
  - name: Guarde el documento con marca de agua en la carpeta "GeneratedReports" con
      un nombre de archivo único.
    text: Guarde el documento con marca de agua en la carpeta "GeneratedReports" con
      un nombre de archivo único.
  - name: Cierre el bucle después de procesar el documento actual.
    text: Cierre el bucle después de procesar el documento actual.
  type: HowTo
- questions:
  - answer: IsSemitrasparent determina si la marca de agua se renderiza con opacidad
      parcial; establecerla en **true** hace que el texto sea semitransparente, de
      modo que el contenido subyacente siga siendo más legible.
    question: ¿Qué controla la opción **IsSemitrasparent** y qué efecto tiene establecerla
      en **true**?
  - answer: Sí—establezca la propiedad **Layout** a **WatermarkLayout.Horizontal**
      en **TextWatermarkOptions** antes de llamar a **document.Watermark.SetText**.
    question: ¿Puedo cambiar la orientación de la marca de agua a horizontal en lugar
      de diagonal?
  - answer: El fragmento crea una nueva instancia de **Document**, pero puede abrir
      cualquier archivo existente (p. ej., `new Document("Existing.docx")`) y luego
      llamar a **document.Watermark.SetText** para aplicar la misma marca de agua.
    question: ¿Este código agregará una marca de agua a un archivo Word existente
      o solo a documentos recién creados?
  - answer: Asigne un color personalizado con **Color.FromArgb(red, green, blue)**
      a la propiedad **Color** de **TextWatermarkOptions**, por ejemplo, `Color =
      Color.FromArgb(128, 0, 128)` para púrpura.
    question: ¿Cómo puedo usar un color RGB personalizado para la marca de agua en
      lugar del **Color.Red** predefinido?
  type: FAQPage
images:
- /net/programming-with-watermark/add-text-watermark/og-image.png
og_title: Agregar una marca de agua de texto diagonal roja a documentos Word
og_description: Vea cómo aplicar automáticamente una marca de agua diagonal roja a cada documento Word en un lote con Aspose.Words.
og_image_alt: Guía que muestra cómo agregar una marca de agua de texto diagonal roja a documentos Word usando Aspose.Words para .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Agregar marca de agua de texto diagonal roja a documentos Word usando Aspose.Words para .NET
Este tutorial demuestra cómo incrustar automáticamente una marca de agua de texto diagonal roja en cada documento Word creado durante la generación de informes por lotes. Utilizando las clases Document y DocumentBuilder de Aspose.Words para .NET, la marca de agua se aplica programáticamente a medida que se generan los archivos, garantizando que cada documento lleve la misma marca o aviso de confidencialidad sin esfuerzo manual.

---

{{< tutorial-widget sourcePath="words/net/programming-with-watermark/add-text-watermark" >}}


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

**Q: ¿Qué controla la opción **IsSemitrasparent** y qué efecto tiene establecerla en **true**?**  
A: IsSemitrasparent determina si la marca de agua se renderiza con opacidad parcial; establecerla en **true** hace que el texto sea semitransparente, de modo que el contenido subyacente siga siendo más legible.

**Q: ¿Puedo cambiar la orientación de la marca de agua a horizontal en lugar de diagonal?**  
A: Sí—establezca la propiedad **Layout** a **WatermarkLayout.Horizontal** en **TextWatermarkOptions** antes de llamar a **document.Watermark.SetText**.

**Q: ¿Este código agregará una marca de agua a un archivo Word existente o solo a documentos recién creados?**  
A: El fragmento crea una nueva instancia de **Document**, pero puede abrir cualquier archivo existente (p. ej., `new Document("Existing.docx")`) y luego llamar a **document.Watermark.SetText** para aplicar la misma marca de agua.

**Q: ¿Cómo puedo usar un color RGB personalizado para la marca de agua en lugar del **Color.Red** predefinido?**  
A: Asigne un color personalizado con **Color.FromArgb(red, green, blue)** a la propiedad **Color** de **TextWatermarkOptions**, por ejemplo, `Color = Color.FromArgb(128, 0, 128)` para púrpura.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}