---
title: Agregar comentario con hipervínculo y exportar como anotación PDF usando Aspose.Words for .NET
weight: 110
limit:
description: Aprenda a agregar un comentario con hipervínculo en un archivo Word y exportarlo como una anotación PDF con Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, add hyperlink comment, PDF annotation, export Word to PDF, comment with hyperlink, verify PDF output]
url: /net/working-with-comments/add-hyperlink-comment/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aprenda a agregar un comentario con hipervínculo en un archivo Word
    y exportarlo como una anotación PDF con Aspose.Words for .NET.
  headline: Agregar comentario con hipervínculo y exportar como anotación PDF usando
    Aspose.Words for .NET
  type: TechArticle
- description: Aprenda a agregar un comentario con hipervínculo en un archivo Word
    y exportarlo como una anotación PDF con Aspose.Words for .NET.
  name: Agregar comentario con hipervínculo y exportar como anotación PDF usando Aspose.Words
    for .NET
  steps:
  - name: Cree un nuevo objeto Document vacío y un DocumentBuilder para trabajar con
      él.
    text: Cree un nuevo objeto Document vacío y un DocumentBuilder para trabajar con
      él.
  - name: Escriba una línea de texto visible que alojará el próximo comentario.
    text: Escriba una línea de texto visible que alojará el próximo comentario.
  - name: Cree un Comment creado por Jane Doe y adjúntelo al primer párrafo del documento.
    text: Cree un Comment creado por Jane Doe y adjúntelo al primer párrafo del documento.
  - name: Dentro del comentario, agregue un párrafo e inserte un hipervínculo azul
      y subrayado al sitio web de Aspose.Words Library.
    text: Dentro del comentario, agregue un párrafo e inserte un hipervínculo azul
      y subrayado al sitio web de Aspose.Words Library.
  - name: Configure el documento para que renderice los comentarios como anotaciones
      PDF y actualice el diseño.
    text: Configure el documento para que renderice los comentarios como anotaciones
      PDF y actualice el diseño.
  - name: Cree una carpeta "Output" en el directorio actual para almacenar el PDF
      generado.
    text: Cree una carpeta "Output" en el directorio actual para almacenar el PDF
      generado.
  - name: Guarde el documento preparado como un archivo PDF usando PdfSaveOptions.
    text: Guarde el documento preparado como un archivo PDF usando PdfSaveOptions.
  - name: Verifique que el archivo PDF exista y contenga datos, luego muestre el resultado
      en la consola.
    text: Verifique que el archivo PDF exista y contenga datos, luego muestre el resultado
      en la consola.
  type: HowTo
- questions:
  - answer: El tercer parámetro de `InsertHyperlink` especifica si el enlace debe
      tratarse como un campo; establecerlo en `false` inserta un hipervínculo simple
      que funciona en la anotación PDF sin necesitar un código de campo.
    question: ¿Qué controla el tercer argumento (`false`) en `InsertHyperlink`?
  - answer: Establezca `myDocument.LayoutOptions.CommentDisplayMode` a `CommentDisplayMode.ShowInBalloons`
      antes de llamar a `Save`; el PDF contendrá entonces el comentario como un comentario
      Word normal en lugar de una anotación.
    question: ¿Cómo puedo hacer que el comentario aparezca como un globo en el documento
      Word en lugar de una anotación PDF?
  - answer: Sí—cada `Comment` que añada a un párrafo puede contener su propia llamada
      a `InsertHyperlink`, y todos los hipervínculos se conservarán como anotaciones
      PDF separadas cuando se guarde el documento.
    question: Si agrego más de un comentario, ¿funcionará cada hipervínculo en el
      PDF exportado?
  - answer: Abra el PDF generado, localice la anotación del comentario (generalmente
      mostrada como un ícono de nota), haga clic en ella para revelar el texto del
      comentario y luego haga clic en el enlace azul subrayado; debería abrir la URL
      de destino en un navegador web.
    question: ¿Cómo verifico que el hipervínculo dentro del comentario funcione realmente
      después de generar el PDF?
  type: FAQPage
images:
- /net/working-with-comments/add-hyperlink-comment/og-image.png
og_title: Insertar comentario con hipervínculo y exportar a PDF
og_description: Aprenda a incrustar un enlace clicable en un comentario Word y convertirlo en una anotación PDF.
og_image_alt: Guía que muestra cómo agregar un comentario con un hipervínculo clicable a un documento Word y exportarlo como una anotación PDF usando Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Agregar comentario con hipervínculo y exportar como anotación PDF usando Aspose.Words
En este tutorial verá cómo crear un documento Word, insertar un comentario que contiene un hipervínculo clicable a un sitio web externo, configurar ese comentario para que aparezca como una anotación PDF, exportar el documento a PDF y verificar el archivo PDF resultante. El código paso a paso le permite agregar comentarios enriquecidos y con enlaces y preservarlos al convertir a PDF, facilitando compartir notas interactivas con los lectores.

---

{{< tutorial-widget sourcePath="words/net/working-with-comments/add-hyperlink-comment" >}}


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

**Q: ¿Qué controla el tercer argumento (`false`) en `InsertHyperlink`?**  
A: El tercer parámetro de `InsertHyperlink` especifica si el enlace debe tratarse como un campo; establecerlo en `false` inserta un hipervínculo simple que funciona en la anotación PDF sin necesitar un código de campo.

**Q: ¿Cómo puedo hacer que el comentario aparezca como un globo en el documento Word en lugar de una anotación PDF?**  
A: Establezca `myDocument.LayoutOptions.CommentDisplayMode` a `CommentDisplayMode.ShowInBalloons` antes de llamar a `Save`; el PDF contendrá entonces el comentario como un comentario Word normal en lugar de una anotación.

**Q: Si agrego más de un comentario, ¿funcionará cada hipervínculo en el PDF exportado?**  
A: Sí—cada `Comment` que añada a un párrafo puede contener su propia llamada a `InsertHyperlink`, y todos los hipervínculos se conservarán como anotaciones PDF separadas cuando se guarde el documento.

**Q: ¿Cómo verifico que el hipervínculo dentro del comentario funcione realmente después de generar el PDF?**  
A: Abra el PDF generado, localice la anotación del comentario (generalmente mostrada como un ícono de nota), haga clic en ella para revelar el texto del comentario y luego haga clic en el enlace azul subrayado; debería abrir la URL de destino en un navegador web.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}