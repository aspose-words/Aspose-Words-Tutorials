---
title: Adicionar números de página ao rodapé de um documento Word usando Aspose.Words para .NET
weight: 210
limit:
description: Adicionar números de página que são atualizados automaticamente ao rodapé primário de um documento Word usando Aspose.Words para .NET.
keywords: [Aspose.Words for .NET, add page numbers, word document footer, documentbuilder page numbers, automatic page numbering, c# aspose.words]
url: /net/working-with-headers-and-footers/add-page-numbers/
date: '2026-09-22'
lastmod: '2026-09-22'
schemas:
- author: Aspose
  dateModified: '2026-09-22'
  description: Adicionar números de página que são atualizados automaticamente ao
    rodapé primário de um documento Word usando Aspose.Words para .NET.
  headline: Adicionar números de página ao rodapé de um documento Word usando Aspose.Words
    para .NET
  type: TechArticle
- description: Adicionar números de página que são atualizados automaticamente ao
    rodapé primário de um documento Word usando Aspose.Words para .NET.
  name: Adicionar números de página ao rodapé de um documento Word usando Aspose.Words
    para .NET
  steps:
  - name: Crie um novo objeto Document e um DocumentBuilder associado a ele.
    text: Crie um novo objeto Document e um DocumentBuilder associado a ele.
  - name: Mova o cursor do builder para o rodapé primário da primeira seção.
    text: Mova o cursor do builder para o rodapé primário da primeira seção.
  - name: Defina o alinhamento do parágrafo como centralizado para que o texto do
      rodapé fique centralizado.
    text: Defina o alinhamento do parágrafo como centralizado para que o texto do
      rodapé fique centralizado.
  - name: Escreva o rótulo "Page " e insira um campo PAGE que exibe o número da página
      atual.
    text: Escreva o rótulo "Page " e insira um campo PAGE que exibe o número da página
      atual.
  - name: Escreva " of " e insira um campo NUMPAGES que mostra o total de páginas.
    text: Escreva " of " e insira um campo NUMPAGES que mostra o total de páginas.
  - name: Salve o documento em um arquivo .docx.
    text: Salve o documento em um arquivo .docx.
  type: HowTo
- questions:
  - answer: Não. `MoveToHeaderFooter(HeaderFooterType.FooterPrimary)` move o builder
      apenas para o rodapé primário da *primeira* seção, portanto os campos são inseridos
      somente lá.
    question: Se o documento tiver mais de uma seção, este código adicionará números
      de página ao rodapé de cada seção?
  - answer: Defina `builder.ParagraphFormat.Alignment` para outro valor de `ParagraphAlignment`
      (por exemplo, `ParagraphAlignment.Right`) antes de escrever os campos.
    question: Como posso alterar o alinhamento do parágrafo do número da página no
      rodapé?
  - answer: '`InsertField` recebe o código do campo e um resultado de campo opcional;
      passar `null` indica ao Aspose.Words que o Word calcule o resultado em tempo
      de execução.'
    question: O que representa o argumento `null` em `InsertField("PAGE", null)`?
  - answer: Sim—substitua `HeaderFooterType.FooterPrimary` por `HeaderFooterType.HeaderPrimary`
      (ou outro tipo de cabeçalho) antes de inserir os campos.
    question: Posso colocar os mesmos campos "Page X of Y" no cabeçalho em vez do
      rodapé?
  type: FAQPage
images:
- /net/working-with-headers-and-footers/add-page-numbers/og-image.png
og_title: Inserir números de página automáticos no rodapé do Word
og_description: Código passo a passo para adicionar números de página dinâmicos a um rodapé do Word com Aspose.Words para .NET.
og_image_alt: Guia que mostra como adicionar números de página automáticos ao rodapé de um documento Word usando Aspose.Words para .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Adicionar números de página ao rodapé de um documento Word usando Aspose.Words para .NET
Este tutorial mostra como usar Aspose.Words Document e DocumentBuilder para inserir números de página que são atualizados automaticamente no rodapé primário de um documento Word. Ao adicionar números de página programaticamente, você garante paginação consistente em todo o arquivo sem edição manual. O código de exemplo está pronto para ser executado em um ambiente .NET.

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

**Q: Se o documento tiver mais de uma seção, este código adicionará números de página ao rodapé de cada seção?**  
A: Não. `MoveToHeaderFooter(HeaderFooterType.FooterPrimary)` move o builder apenas para o rodapé primário da *primeira* seção, portanto os campos são inseridos somente lá.

**Q: Como posso alterar o alinhamento do parágrafo do número da página no rodapé?**  
A: Defina `builder.ParagraphFormat.Alignment` para outro valor de `ParagraphAlignment` (por exemplo, `ParagraphAlignment.Right`) antes de escrever os campos.

**Q: O que representa o argumento `null` em `InsertField("PAGE", null)`?**  
A: `InsertField` recebe o código do campo e um resultado de campo opcional; passar `null` indica ao Aspose.Words que o Word calcule o resultado em tempo de execução.

**Q: Posso colocar os mesmos campos "Page X of Y" no cabeçalho em vez do rodapé?**  
A: Sim—substitua `HeaderFooterType.FooterPrimary` por `HeaderFooterType.HeaderPrimary` (ou outro tipo de cabeçalho) antes de inserir os campos.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}