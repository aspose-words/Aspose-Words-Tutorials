---
title: Inserir Data Dinâmica no Cabeçalho de Documento Word Usando Aspose.Words para .NET
weight: 110
limit:
description: Aprenda a adicionar um campo DATE dinâmico ao cabeçalho principal de um documento Word com Aspose.Words para .NET.
keywords: [Aspose.Words for .NET, insert header date, dynamic DATE field, DocumentBuilder header, Word document header automation]
url: /net/working-with-headers-and-footers/insert-header-date/
date: '2026-09-22'
lastmod: '2026-09-22'
schemas:
- author: Aspose
  dateModified: '2026-09-22'
  description: Aprenda a adicionar um campo DATE dinâmico ao cabeçalho principal de
    um documento Word com Aspose.Words para .NET.
  headline: Inserir Data Dinâmica no Cabeçalho de Documento Word Usando Aspose.Words
    para .NET
  type: TechArticle
- description: Aprenda a adicionar um campo DATE dinâmico ao cabeçalho principal de
    um documento Word com Aspose.Words para .NET.
  name: Inserir Data Dinâmica no Cabeçalho de Documento Word Usando Aspose.Words para
    .NET
  steps:
  - name: Crie um novo Document e um DocumentBuilder para editá-lo.
    text: Crie um novo Document e um DocumentBuilder para editá-lo.
  - name: Mova o cursor do builder para o cabeçalho principal para que inserções subsequentes
      afetem o cabeçalho.
    text: Mova o cursor do builder para o cabeçalho principal para que inserções subsequentes
      afetem o cabeçalho.
  - name: Escreva o rótulo estático e insira um campo DATE formatado como “MMMM d,
      yyyy” no cabeçalho, criando uma data dinâmica.
    text: Escreva o rótulo estático e insira um campo DATE formatado como “MMMM d,
      yyyy” no cabeçalho, criando uma data dinâmica.
  - name: Retorne ao corpo principal e adicione um parágrafo de exemplo, demonstrando
      o conteúdo normal do documento ao lado do cabeçalho.
    text: Retorne ao corpo principal e adicione um parágrafo de exemplo, demonstrando
      o conteúdo normal do documento ao lado do cabeçalho.
  - name: Salve o documento em um arquivo .docx.
    text: Salve o documento em um arquivo .docx.
  type: HowTo
- questions:
  - answer: A chamada `MoveToHeaderFooter(HeaderFooterType.HeaderPrimary)` posiciona
      o builder no cabeçalho principal existente, e `Write`/`InsertField` simplesmente
      acrescentam texto ao que já está lá; eles não excluem o conteúdo existente.
    question: O que acontece se o documento já possuir um cabeçalho principal – meu
      código o sobrescreverá?
  - answer: Sim – modifique o formato do switch no código do campo passado para `InsertField`,
      por exemplo `builder.InsertField(\"DATE \\\\@ \"yyyy-MM-dd\")` produzirá uma
      data como 2026-09-22.
    question: Posso alterar o formato de data usado pelo campo DATE, e como?
  - answer: Substitua `HeaderFooterType.HeaderPrimary` por `HeaderFooterType.HeaderFirst`
      ao chamar `MoveToHeaderFooter`; o restante do código funciona da mesma forma.
    question: Se eu precisar do campo de data no cabeçalho da primeira página em vez
      do cabeçalho principal, o que devo fazer?
  - answer: O campo é inserido apenas com o switch `\\@`, que indica ao Word para
      exibir a data atual sempre que o campo for atualizado (por exemplo, ao abrir
      o arquivo ou ao pressionar Ctrl+Alt+F9).
    question: O campo DATE atualiza automaticamente quando o documento é aberto posteriormente?
  type: FAQPage
images:
- /net/working-with-headers-and-footers/insert-header-date/og-image.png
og_title: Adicionar uma Data Dinâmica ao Cabeçalho do Word
og_description: Guia passo a passo para incorporar um campo de data ao vivo no seu cabeçalho Word com Aspose.Words.
og_image_alt: Captura de tela mostrando como inserir um campo DATE dinâmico no cabeçalho de um documento Word usando Aspose.Words para .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Inserir Data Dinâmica no Cabeçalho de Documento Word Usando Aspose.Words para .NET
Este tutorial demonstra como usar as classes Document e DocumentBuilder no Aspose.Words para .NET para inserir um campo DATE dinâmico no cabeçalho principal de um documento Word. O campo adicionado atualiza automaticamente para a data atual sempre que o documento é aberto, garantindo que seu cabeçalho reflita sempre a data mais recente. Siga o código passo a passo para adicionar o campo e salvar o arquivo atualizado.

---

{{< tutorial-widget sourcePath="words/net/working-with-headers-and-footers/insert-header-date" >}}


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

**Q: O que acontece se o documento já possuir um cabeçalho principal – meu código o sobrescreverá?**  
A: A chamada `MoveToHeaderFooter(HeaderFooterType.HeaderPrimary)` posiciona o builder no cabeçalho principal existente, e `Write`/`InsertField` simplesmente acrescentam texto ao que já está lá; eles não excluem o conteúdo existente.

**Q: Posso alterar o formato de data usado pelo campo DATE, e como?**  
A: Sim – modifique o formato do switch no código do campo passado para `InsertField`, por exemplo `builder.InsertField(\"DATE \\\\@ \"yyyy-MM-dd\")` produzirá uma data como 2026-09-22.

**Q: Se eu precisar do campo de data no cabeçalho da primeira página em vez do cabeçalho principal, o que devo fazer?**  
A: Substitua `HeaderFooterType.HeaderPrimary` por `HeaderFooterType.HeaderFirst` ao chamar `MoveToHeaderFooter`; o restante do código funciona da mesma forma.

**Q: O campo DATE atualiza automaticamente quando o documento é aberto posteriormente?**  
A: O campo é inserido apenas com o switch `\\@`, que indica ao Word para exibir a data atual sempre que o campo for atualizado (por exemplo, ao abrir o arquivo ou ao pressionar Ctrl+Alt+F9).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}