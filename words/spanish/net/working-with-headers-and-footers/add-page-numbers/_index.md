---
title: Agregar números de página al pie de un documento Word usando Aspose.Words para .NET
weight: 210
limit:
description: Agregar números de página que se actualizan automáticamente al pie de página primario de un documento Word usando Aspose.Words para .NET.
keywords: [Aspose.Words for .NET, add page numbers, word document footer, documentbuilder page numbers, automatic page numbering, c# aspose.words]
url: /net/working-with-headers-and-footers/add-page-numbers/
date: '2026-09-22'
lastmod: '2026-09-22'
schemas:
- author: Aspose
  dateModified: '2026-09-22'
  description: Agregar números de página que se actualizan automáticamente al pie
    de página primario de un documento Word usando Aspose.Words para .NET.
  headline: Agregar números de página al pie de un documento Word usando Aspose.Words
    para .NET
  type: TechArticle
- description: Agregar números de página que se actualizan automáticamente al pie
    de página primario de un documento Word usando Aspose.Words para .NET.
  name: Agregar números de página al pie de un documento Word usando Aspose.Words
    para .NET
  steps:
  - name: Cree un nuevo objeto Document y un DocumentBuilder asociado a él.
    text: Cree un nuevo objeto Document y un DocumentBuilder asociado a él.
  - name: Mueva el cursor del builder al pie de página primario de la primera sección.
    text: Mueva el cursor del builder al pie de página primario de la primera sección.
  - name: Establezca la alineación del párrafo en centrado para que el texto del pie
      de página quede centrado.
    text: Establezca la alineación del párrafo en centrado para que el texto del pie
      de página quede centrado.
  - name: Escriba la etiqueta "Page " e inserte un campo PAGE que muestre el número
      de página actual.
    text: Escriba la etiqueta "Page " e inserte un campo PAGE que muestre el número
      de página actual.
  - name: Escriba " of " e inserte un campo NUMPAGES que muestre el recuento total
      de páginas.
    text: Escriba " of " e inserte un campo NUMPAGES que muestre el recuento total
      de páginas.
  - name: Guarde el documento en un archivo .docx.
    text: Guarde el documento en un archivo .docx.
  type: HowTo
- questions:
  - answer: No. `MoveToHeaderFooter(HeaderFooterType.FooterPrimary)` mueve el builder
      solo al pie de página primario de la *primera* sección, por lo que los campos
      se insertan únicamente allí.
    question: Si el documento tiene más de una sección, ¿este código agregará números
      de página al pie de cada sección?
  - answer: Establezca `builder.ParagraphFormat.Alignment` a otro valor de `ParagraphAlignment`
      (p. ej., `ParagraphAlignment.Right`) antes de escribir los campos.
    question: ¿Cómo puedo cambiar la alineación del párrafo del número de página en
      el pie de página?
  - answer: '`InsertField` recibe el código del campo y un resultado opcional; pasar
      `null` indica a Aspose.Words que deje que Word calcule el resultado en tiempo
      de ejecución.'
    question: ¿Qué representa el argumento `null` en `InsertField("PAGE", null)`?
  - answer: Sí—reemplace `HeaderFooterType.FooterPrimary` por `HeaderFooterType.HeaderPrimary`
      (u otro tipo de encabezado) antes de insertar los campos.
    question: ¿Puedo colocar los mismos campos "Page X of Y" en el encabezado en lugar
      del pie de página?
  type: FAQPage
images:
- /net/working-with-headers-and-footers/add-page-numbers/og-image.png
og_title: Insertar números de página automáticos en el pie de Word
og_description: Código paso a paso para agregar números de página en vivo a un pie de Word con Aspose.Words para .NET.
og_image_alt: Guía que muestra cómo agregar números de página automáticos al pie de un documento Word usando Aspose.Words para .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Agregar números de página al pie de un documento Word usando Aspose.Words para .NET
Este tutorial muestra cómo usar Aspose.Words Document y DocumentBuilder para insertar números de página que se actualizan automáticamente en el pie de página primario de un documento Word. Al agregar números de página programáticamente, garantiza una paginación coherente en todo el archivo sin edición manual. El código de ejemplo está listo para ejecutarse en un entorno .NET.

---

{{< tutorial-widget sourcePath="words/net/working-with-headers-and-footers/add-page-numbers" >}}


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
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Si el documento tiene más de una sección, ¿este código agregará números de página al pie de cada sección?**  
A: No. `MoveToHeaderFooter(HeaderFooterType.FooterPrimary)` mueve el builder solo al pie de página primario de la *primera* sección, por lo que los campos se insertan únicamente allí.

**Q: ¿Cómo puedo cambiar la alineación del párrafo del número de página en el pie de página?**  
A: Establezca `builder.ParagraphFormat.Alignment` a otro valor de `ParagraphAlignment` (p. ej., `ParagraphAlignment.Right`) antes de escribir los campos.

**Q: ¿Qué representa el argumento `null` en `InsertField("PAGE", null)`?**  
A: `InsertField` recibe el código del campo y un resultado opcional; pasar `null` indica a Aspose.Words que deje que Word calcule el resultado en tiempo de ejecución.

**Q: ¿Puedo colocar los mismos campos "Page X of Y" en el encabezado en lugar del pie de página?**  
A: Sí—reemplace `HeaderFooterType.FooterPrimary` por `HeaderFooterType.HeaderPrimary` (u otro tipo de encabezado) antes de insertar los campos.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}