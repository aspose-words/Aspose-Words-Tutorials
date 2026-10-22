---
title: Criar Tabela com Texto Rotacionado em Documento Word Usando Aspose.Words para .NET
weight: 110
limit:
description: Aprenda a criar uma tabela Word com larguras de coluna fixas, texto rotacionado, alturas de linha precisas e células preenchidas usando Aspose.Words para .NET.
keywords: [Aspose.Words for .NET, rotated text table, fixed column widths, vertical alignment Aspose.Words, set row height Word, populate table cells .NET]
url: /net/add-content-using-documentbuilder/create-rotated-text-table/
date: '2026-09-16'
lastmod: '2026-09-16'
schemas:
- author: Aspose
  dateModified: '2026-09-16'
  description: Aprenda a criar uma tabela Word com larguras de coluna fixas, texto
    rotacionado, alturas de linha precisas e células preenchidas usando Aspose.Words
    para .NET.
  headline: Criar Tabela com Texto Rotacionado em Documento Word Usando Aspose.Words
    para .NET
  type: TechArticle
- description: Aprenda a criar uma tabela Word com larguras de coluna fixas, texto
    rotacionado, alturas de linha precisas e células preenchidas usando Aspose.Words
    para .NET.
  name: Criar Tabela com Texto Rotacionado em Documento Word Usando Aspose.Words para
    .NET
  steps:
  - name: Instancie um novo Document e um DocumentBuilder que serão usados para construir
      a tabela.
    text: Instancie um novo Document e um DocumentBuilder que serão usados para construir
      a tabela.
  - name: Inicie uma nova tabela, insira a primeira célula e fixe as larguras das
      colunas para que não se ajustem automaticamente.
    text: Inicie uma nova tabela, insira a primeira célula e fixe as larguras das
      colunas para que não se ajustem automaticamente.
  - name: Alinhe o conteúdo verticalmente ao centro na célula atual e escreva o texto
      da primeira célula da primeira linha.
    text: Alinhe o conteúdo verticalmente ao centro na célula atual e escreva o texto
      da primeira célula da primeira linha.
  - name: Insira a segunda célula da primeira linha e escreva seu texto.
    text: Insira a segunda célula da primeira linha e escreva seu texto.
  - name: Feche a primeira linha, finalizando seu layout.
    text: Feche a primeira linha, finalizando seu layout.
  - name: Inicie a primeira célula da segunda linha, defina a altura da linha para
      exatamente 100 pontos, gire o texto para cima e escreva o texto da célula.
    text: Inicie a primeira célula da segunda linha, defina a altura da linha para
      exatamente 100 pontos, gire o texto para cima e escreva o texto da célula.
  - name: Insira a segunda célula da segunda linha, gire seu texto para baixo e escreva
      o texto da célula.
    text: Insira a segunda célula da segunda linha, gire seu texto para baixo e escreva
      o texto da célula.
  - name: Feche a segunda linha, completando a segunda linha da tabela.
    text: Feche a segunda linha, completando a segunda linha da tabela.
  - name: Finalize a construção da tabela, selando a estrutura da tabela.
    text: Finalize a construção da tabela, selando a estrutura da tabela.
  - name: Salve o documento concluído em um arquivo .docx.
    text: Salve o documento concluído em um arquivo .docx.
  type: HowTo
- questions:
  - answer: Depois de fixar as larguras das colunas, atribua uma largura a cada célula
      usando `builder.CellFormat.Width = <valueInPoints>;` antes de inserir a próxima
      célula; a tabela manterá essas larguras exatas.
    question: Como posso definir larguras de coluna específicas após chamar `table.AutoFit(AutoFitBehavior.FixedColumnWidths)`?
  - answer: '`builder.CellFormat.VerticalAlignment` é uma configuração ao nível da
      célula, portanto você precisa defini‑la novamente para as células da segunda
      linha (por exemplo, `builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;`)
      antes de escrever seu conteúdo.'
    question: Por que o alinhamento vertical afeta apenas a primeira linha e não a
      segunda linha?
  - answer: Sim — defina `builder.RowFormat.Height` e `builder.RowFormat.HeightRule
      = HeightRule.Exactly` antes de cada chamada `builder.EndRow();`; a próxima linha
      pode ter um valor de altura diferente.
    question: Posso definir uma altura exata diferente para cada linha e, em caso
      afirmativo, como fazer isso?
  - answer: Redefina a orientação atribuindo `builder.CellFormat.Orientation = TextOrientation.Horizontal;`
      antes de escrever na próxima célula.
    question: Como reverto a orientação do texto para o padrão após usar `TextOrientation.Upward`
      ou `Downward`?
  type: FAQPage
images:
- /net/add-content-using-documentbuilder/create-rotated-text-table/og-image.png
og_title: Criar Tabela com Texto Rotacionado no Word com Aspose.Words
og_description: Código passo a passo para criar uma tabela de largura fixa com texto rotacionado verticalmente e alturas de linha exatas.
og_image_alt: Captura de tela mostrando um documento Word com uma tabela que tem larguras de coluna fixas, texto rotacionado nas células e alturas de linha definidas, criada usando Aspose.Words para .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Criar Tabela com Texto Rotacionado em Documento Word Usando Aspose.Words para .NET
Este tutorial mostra como gerar um documento Word e adicionar uma tabela cujas colunas têm larguras fixas, as linhas têm alturas exatas e o texto das células é rotacionado verticalmente. Você aprenderá a definir o alinhamento vertical, aplicar a orientação de texto, preencher cada célula com conteúdo e, finalmente, salvar o documento — tudo com Aspose.Words para .NET.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/create-rotated-text-table" >}}


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

**Q: Como posso definir larguras de coluna específicas após chamar `table.AutoFit(AutoFitBehavior.FixedColumnWidths)`?**  
A: Depois de fixar as larguras das colunas, atribua uma largura a cada célula usando `builder.CellFormat.Width = <valueInPoints>;` antes de inserir a próxima célula; a tabela manterá essas larguras exatas.

**Q: Por que o alinhamento vertical afeta apenas a primeira linha e não a segunda linha?**  
A: `builder.CellFormat.VerticalAlignment` é uma configuração ao nível da célula, portanto você precisa defini‑la novamente para as células da segunda linha (por exemplo, `builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;`) antes de escrever seu conteúdo.

**Q: Posso definir uma altura exata diferente para cada linha e, em caso afirmativo, como fazer isso?**  
A: Sim — defina `builder.RowFormat.Height` e `builder.RowFormat.HeightRule = HeightRule.Exactly` antes de cada chamada `builder.EndRow();`; a próxima linha pode ter um valor de altura diferente.

**Q: Como reverto a orientação do texto para o padrão após usar `TextOrientation.Upward` ou `Downward`?**  
A: Redefina a orientação atribuindo `builder.CellFormat.Orientation = TextOrientation.Horizontal;` antes de escrever na próxima célula.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}