---
title: Inserir um Comment em um Parágrafo Específico em um Documento Word usando Aspose.Words for .NET
weight: 210
limit:
description: Guia passo a passo para adicionar um comentário de autor a um parágrafo escolhido em um documento Word e salvá‑lo como DOCX usando Aspose.Words for .NET.
keywords: [add comment Aspose.Words for .NET, insert comment Word document, comment author Aspose.Words, c# add comment to Word, save DOCX with comment]
url: /net/working-with-comments/add-comment/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Guia passo a passo para adicionar um comentário de autor a um parágrafo
    escolhido em um documento Word e salvá‑lo como DOCX usando Aspose.Words for .NET.
  headline: Inserir um Comment em um Parágrafo Específico em um Documento Word usando
    Aspose.Words for .NET
  type: TechArticle
- description: Guia passo a passo para adicionar um comentário de autor a um parágrafo
    escolhido em um documento Word e salvá‑lo como DOCX usando Aspose.Words for .NET.
  name: Inserir um Comment em um Parágrafo Específico em um Documento Word usando
    Aspose.Words for .NET
  steps:
  - name: Instancie um novo Document e um DocumentBuilder para começar a construir
      o arquivo Word.
    text: Instancie um novo Document e um DocumentBuilder para começar a construir
      o arquivo Word.
  - name: Use DocumentBuilder.Writeln para adicionar três parágrafos de texto separados
      ao documento.
    text: Use DocumentBuilder.Writeln para adicionar três parágrafos de texto separados
      ao documento.
  - name: Recupere o segundo parágrafo com segurança, recorrendo ao primeiro caso
      o documento tenha menos de dois parágrafos.
    text: Recupere o segundo parágrafo com segurança, recorrendo ao primeiro caso
      o documento tenha menos de dois parágrafos.
  - name: Crie um Comment com os detalhes do autor, defina seu texto e anexe‑o ao
      parágrafo selecionado.
    text: Crie um Comment com os detalhes do autor, defina seu texto e anexe‑o ao
      parágrafo selecionado.
  - name: Salve o documento modificado como um arquivo DOCX chamado 'sample.docx'
      na pasta atual.
    text: Salve o documento modificado como um arquivo DOCX chamado 'sample.docx'
      na pasta atual.
  type: HowTo
- questions:
  - answer: O bloco `if` recorre ao primeiro parágrafo (`paraList[0]`) quando `paraList.Count`
      é menor que 2, portanto o comentário será anexado a esse único parágrafo em
      vez do segundo ausente.
    question: O que o código faz se o documento contiver apenas um parágrafo?
  - answer: Eles são passados ao construtor `Comment` como o segundo e terceiro argumentos
      – `new Comment(wordDoc, \"Jordan\", \"JH\", DateTime.Now)` – onde \"Jordan\"
      é o nome do autor e \"JH\" são as iniciais.
    question: Como o nome do autor do comentário e as iniciais são definidos neste
      exemplo?
  - answer: Neste trecho o comentário está vinculado ao `Paragraph` inteiro via `AppendChild`,
      mas para comentar um intervalo de texto seria necessário criar um `CommentRangeStart`
      e um `CommentRangeEnd` ao redor dos nós `Run` desejados e então adicionar o
      nó `Comment` entre eles.
    question: Posso anexar um comentário a um trecho específico de texto em vez de
      todo o parágrafo?
  - answer: '`AppendChild` adiciona o nó `Comment` à coleção de filhos do parágrafo,
      e o Aspose.Words gera automaticamente os marcadores de início/fim de comentário
      necessários quando o documento é salvo.'
    question: Preciso inserir manualmente os marcadores de comentário ou o `AppendChild`
      cuida disso?
  type: FAQPage
images:
- /net/working-with-comments/add-comment/og-image.png
og_title: Inserir um comentário em um parágrafo Word
og_description: Adicionar um comentário de autor a um parágrafo específico e exportar o arquivo como DOCX com Aspose.Words.
og_image_alt: Guia que mostra como adicionar um comentário a um parágrafo em um documento Word usando Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Inserir um Comment em um Parágrafo Específico em um Documento Word usando Aspose.Words
Com Aspose.Words for .NET você pode adicionar comentários a arquivos Word programaticamente. Este tutorial demonstra a criação de um novo documento, a inserção de três parágrafos, a localização do segundo parágrafo e a anexação de um comentário que inclui informações de autor e data. Por fim, o documento é salvo como um arquivo DOCX preservando o comentário.

---

{{< tutorial-widget sourcePath="words/net/working-with-comments/add-comment" >}}


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

**Q: O que o código faz se o documento contiver apenas um parágrafo?**  
A: O bloco `if` recorre ao primeiro parágrafo (`paraList[0]`) quando `paraList.Count` é menor que 2, portanto o comentário será anexado a esse único parágrafo em vez do segundo ausente.

**Q: Como o nome do autor do comentário e as iniciais são definidos neste exemplo?**  
A: Eles são passados ao construtor `Comment` como o segundo e terceiro argumentos – `new Comment(wordDoc, \"Jordan\", \"JH\", DateTime.Now)` – onde \"Jordan\" é o nome do autor e \"JH\" são as iniciais.

**Q: Posso anexar um comentário a um trecho específico de texto em vez de todo o parágrafo?**  
A: Neste trecho o comentário está vinculado ao `Paragraph` inteiro via `AppendChild`, mas para comentar um intervalo de texto seria necessário criar um `CommentRangeStart` e um `CommentRangeEnd` ao redor dos nós `Run` desejados e então adicionar o nó `Comment` entre eles.

**Q: Preciso inserir manualmente os marcadores de comentário ou o `AppendChild` cuida disso?**  
A: `AppendChild` adiciona o nó `Comment` à coleção de filhos do parágrafo, e o Aspose.Words gera automaticamente os marcadores de início/fim de comentário necessários quando o documento é salvo.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}