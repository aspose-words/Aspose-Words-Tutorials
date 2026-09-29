---
title: Substituir Dados de Código de Barras em Documentos Word Usando Aspose.Words para .NET
weight: 110
limit:
description: Aprenda como inserir um campo DISPLAYBARCODE e substituir sua string de dados com Aspose.Words para .NET.
keywords: [Aspose.Words for .NET, barcode field, replace barcode data, Document.Range.Replace, DISPLAYBARCODE, Word barcode update]
url: /net/working-with-fields/replace-barcode-data/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Aprenda como inserir um campo DISPLAYBARCODE e substituir sua string
    de dados com Aspose.Words para .NET.
  headline: Substituir Dados de Código de Barras em Documentos Word Usando Aspose.Words
    para .NET
  type: TechArticle
- description: Aprenda como inserir um campo DISPLAYBARCODE e substituir sua string
    de dados com Aspose.Words para .NET.
  name: Substituir Dados de Código de Barras em Documentos Word Usando Aspose.Words
    para .NET
  steps:
  - name: Crie um novo objeto Document e um DocumentBuilder para construir seu conteúdo.
    text: Crie um novo objeto Document e um DocumentBuilder para construir seu conteúdo.
  - name: Insira um campo DISPLAYBARCODE e defina seu tipo, valor inicial e caracteres
      de início/fim, depois adicione uma quebra de linha.
    text: Insira um campo DISPLAYBARCODE e defina seu tipo, valor inicial e caracteres
      de início/fim, depois adicione uma quebra de linha.
  - name: Chame UpdateFields para renderizar o campo de código de barras recém‑inserido.
    text: Chame UpdateFields para renderizar o campo de código de barras recém‑inserido.
  - name: Use o mecanismo de Localizar/Substituir para mudar a string de dados do
      código de barras de INIT123 para NEWVAL.
    text: Use o mecanismo de Localizar/Substituir para mudar a string de dados do
      código de barras de INIT123 para NEWVAL.
  - name: Atualize os campos novamente para que o DISPLAYBARCODE reflita a nova string
      de dados.
    text: Atualize os campos novamente para que o DISPLAYBARCODE reflita a nova string
      de dados.
  - name: Salve o documento em um arquivo .docx.
    text: Salve o documento em um arquivo .docx.
  type: HowTo
- questions:
  - answer: '`Range.Replace` altera apenas o texto subjacente; o resultado visual
      do campo DISPLAYBARCODE é regenerado somente quando `UpdateFields()` é chamado,
      portanto o novo código de barras aparece no documento salvo.'
    question: Por que preciso chamar `myDocument.UpdateFields()` após executar o `Range.Replace`?
  - answer: Sim, `Document.Range.Replace` funciona em todo o intervalo do documento,
      portanto qualquer texto correspondente em outro lugar será substituído, a menos
      que você restrinja a pesquisa usando `FindReplaceOptions` (por exemplo, definindo
      um `Range` específico ou usando `.MatchWholeWord`).
    question: A chamada `Replace(\"INIT123\", \"NEWVAL\", ...)` afetará outras ocorrências
      de "INIT123" fora do campo de código de barras?
  - answer: Você pode atribuir um novo valor a `displayBarcode.BarcodeType` a qualquer
      momento, mas deve chamar `myDocument.UpdateFields()` em seguida para que a alteração
      seja refletida no código de barras renderizado.
    question: Posso mudar o tipo de código de barras (por exemplo, de CODE39 para
      QR) depois que o campo foi inserido?
  - answer: Quando `AddStartStopChar` está true, Aspose.Words adiciona automaticamente
      os caracteres de início/fim necessários (`*`) ao redor do valor do código de
      barras, o que é exigido pelo CODE39; defina como false se sua simbologia não
      precisar deles.
    question: O que a propriedade `AddStartStopChar = true` faz para códigos de barras
      CODE39?
  - answer: Nenhuma configuração especial é necessária para uma correspondência exata
      simples, mas você pode habilitar `.MatchCase` ou `.MatchWholeWord` em `FindReplaceOptions`
      para evitar substituições parciais acidentais.
    question: Preciso configurar alguma opção especial em `FindReplaceOptions` para
      substituir o valor do código de barras com segurança?
  type: FAQPage
images:
- /net/working-with-fields/replace-barcode-data/og-image.png
og_title: Atualizar um Campo de Código de Barras no Word com Aspose.Words
og_description: Troque a string de dados de um código de barras e atualize-a instantaneamente em um arquivo Word.
og_image_alt: Captura de tela mostrando um documento Word com um campo DISPLAYBARCODE antes e depois da substituição de dados usando Aspose.Words para .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Substituir Dados de Código de Barras em Documentos Word Usando Aspose.Words para .NET
Este tutorial demonstra como inserir um campo DISPLAYBARCODE em um documento Word e então usar o método Document.Range.Replace para alterar a string de dados do código de barras. Após a substituição, o campo é atualizado para que o código de barras atualizado apareça no arquivo salvo. Siga os passos para ver a atualização do código de barras instantaneamente sem recriar o campo.

---

{{< tutorial-widget sourcePath="words/net/working-with-fields/replace-barcode-data" >}}


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

**Q: Por que preciso chamar `myDocument.UpdateFields()` após executar o `Range.Replace`?**  
A: `Range.Replace` altera apenas o texto subjacente; o resultado visual do campo DISPLAYBARCODE é regenerado somente quando `UpdateFields()` é chamado, portanto o novo código de barras aparece no documento salvo.

**Q: A chamada `Replace(\"INIT123\", \"NEWVAL\", ...)` afetará outras ocorrências de "INIT123" fora do campo de código de barras?**  
A: Sim, `Document.Range.Replace` funciona em todo o intervalo do documento, portanto qualquer texto correspondente em outro lugar será substituído, a menos que você restrinja a pesquisa usando `FindReplaceOptions` (por exemplo, definindo um `Range` específico ou usando `.MatchWholeWord`).

**Q: Posso mudar o tipo de código de barras (por exemplo, de CODE39 para QR) depois que o campo foi inserido?**  
A: Você pode atribuir um novo valor a `displayBarcode.BarcodeType` a qualquer momento, mas deve chamar `myDocument.UpdateFields()` em seguida para que a alteração seja refletida no código de barras renderizado.

**Q: O que a propriedade `AddStartStopChar = true` faz para códigos de barras CODE39?**  
A: Quando `AddStartStopChar` está true, Aspose.Words adiciona automaticamente os caracteres de início/fim necessários (`*`) ao redor do valor do código de barras, o que é exigido pelo CODE39; defina como false se sua simbologia não precisar deles.

**Q: Preciso configurar alguma opção especial em `FindReplaceOptions` para substituir o valor do código de barras com segurança?**  
A: Nenhuma configuração especial é necessária para uma correspondência exata simples, mas você pode habilitar `.MatchCase` ou `.MatchWholeWord` em `FindReplaceOptions` para evitar substituições parciais acidentais.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}