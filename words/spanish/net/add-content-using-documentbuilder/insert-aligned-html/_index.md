---
title: Insertar HTML alineado en un documento Word usando Aspose.Words para .NET
weight: 210
limit:
description: Aprenda a insertar HTML sin procesar con alineación izquierda, centrada o derecha en un documento Word usando Aspose.Words para .NET.
keywords: [Aspose.Words for .NET, insert html word document, html alignment, documentbuilder html, c# insert html, aligned html in word]
url: /net/add-content-using-documentbuilder/insert-aligned-html/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Insertar HTML alineado en un documento Word usando Aspose.Words para .NET
Este tutorial interactivo muestra cómo incrustar HTML sin procesar en un documento Word mientras se controla su alineación—izquierda, centrado o derecha—usando Aspose.Words para .NET. Aprovechando Document y DocumentBuilder, puede insertar una cadena HTML y aplicar la alineación de párrafo deseada en solo unas pocas líneas de código. El ejemplo es ideal cuando necesita conservar el formato HTML y colocar el contenido de manera precisa dentro de su documento.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-aligned-html" >}}


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
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: ¿Qué ocurre si la cadena HTML pasada a DocumentBuilder.InsertHtml contiene etiquetas que Aspose.Words no admite, como <script> o <iframe>?**
A: Las etiquetas no compatibles se ignoran; Aspose.Words analiza solo el subconjunto de HTML que puede renderizar, por lo que <script>, <iframe> y elementos similares se eliminan mientras el resto del contenido se inserta.

**Q: ¿Se conservarán los estilos CSS en línea (p. ej., <span style="color:red;">) al usar InsertHtml?**
A: Sí, InsertHtml respeta muchas propiedades CSS en línea como color, font‑size y background, convirtiéndolas al formato Word correspondiente.

**Q: ¿InsertHtml crea automáticamente un nuevo párrafo para elementos de nivel de bloque como <div> o <h1>?**
A: Los elementos de nivel de bloque se asignan a párrafos de Word, de modo que cada <div>, <p>, <h1>, etc., se convierte en un párrafo separado en el documento.

**Q: ¿Cómo puedo insertar HTML en una ubicación específica de un documento existente en lugar de al principio?**
A: Mueva el cursor del DocumentBuilder al nodo deseado (p. ej., builder.MoveToDocumentEnd() o builder.MoveToParagraph(index)) antes de llamar a InsertHtml; el HTML se insertará en la posición actual del cursor.

**Q: Si el documento ya contiene texto, ¿llamar a InsertHtml sobrescribirá el contenido existente?**
A: No, InsertHtml inserta el HTML analizado en la posición actual del builder sin eliminar los nodos existentes, a menos que usted mueva explícitamente el cursor dentro de esos nodos o los elimine previamente.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}