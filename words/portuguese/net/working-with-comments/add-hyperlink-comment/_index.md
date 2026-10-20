---
title: Adicionar Comentário com Hiperlink e Exportar como Anotação PDF Usando Aspose.Words for .NET
weight: 110
limit:
description: Aprenda a adicionar um comentário com hiperlink em um arquivo Word e exportá‑lo como uma anotação PDF com Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, add hyperlink comment, PDF annotation, export Word to PDF, comment with hyperlink, verify PDF output]
url: /net/working-with-comments/add-hyperlink-comment/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aprenda a adicionar um comentário com hiperlink em um arquivo Word
    e exportá‑lo como uma anotação PDF com Aspose.Words for .NET.
  headline: Adicionar Comentário com Hiperlink e Exportar como Anotação PDF Usando
    Aspose.Words for .NET
  type: TechArticle
- description: Aprenda a adicionar um comentário com hiperlink em um arquivo Word
    e exportá‑lo como uma anotação PDF com Aspose.Words for .NET.
  name: Adicionar Comentário com Hiperlink e Exportar como Anotação PDF Usando Aspose.Words
    for .NET
  steps:
  - name: Crie um novo objeto Document vazio e um DocumentBuilder para trabalhar com
      ele.
    text: Crie um novo objeto Document vazio e um DocumentBuilder para trabalhar com
      ele.
  - name: Escreva uma linha de texto visível que hospedará o próximo comentário.
    text: Escreva uma linha de texto visível que hospedará o próximo comentário.
  - name: Crie um Comment escrito por Jane Doe e anexe‑o ao primeiro parágrafo do
      documento.
    text: Crie um Comment escrito por Jane Doe e anexe‑o ao primeiro parágrafo do
      documento.
  - name: Dentro do comentário, adicione um parágrafo e insira um hiperlink azul,
      sublinhado, para o site da Aspose.Words Library.
    text: Dentro do comentário, adicione um parágrafo e insira um hiperlink azul,
      sublinhado, para o site da Aspose.Words Library.
  - name: Configure o documento para renderizar comentários como anotações PDF e atualize
      o layout.
    text: Configure o documento para renderizar comentários como anotações PDF e atualize
      o layout.
  - name: Crie uma pasta "Output" no diretório atual para armazenar o PDF gerado.
    text: Crie uma pasta "Output" no diretório atual para armazenar o PDF gerado.
  - name: Salve o documento preparado como um arquivo PDF usando PdfSaveOptions.
    text: Salve o documento preparado como um arquivo PDF usando PdfSaveOptions.
  - name: Verifique se o arquivo PDF existe e contém dados, então exiba o resultado
      no console.
    text: Verifique se o arquivo PDF existe e contém dados, então exiba o resultado
      no console.
  type: HowTo
- questions:
  - answer: O terceiro parâmetro de `InsertHyperlink` especifica se o link deve ser
      tratado como um campo; defini‑lo como `false` insere um hiperlink simples que
      funciona na anotação PDF sem precisar de um código de campo.
    question: O que controla o terceiro argumento (`false`) em `InsertHyperlink`?
  - answer: Defina `myDocument.LayoutOptions.CommentDisplayMode` como `CommentDisplayMode.ShowInBalloons`
      antes de chamar `Save`; o PDF então conterá o comentário como um comentário
      Word normal, em vez de uma anotação.
    question: Como posso fazer o comentário aparecer como um balão no documento Word
      em vez de uma anotação PDF?
  - answer: Sim—cada `Comment` que você anexa a um parágrafo pode conter sua própria
      chamada `InsertHyperlink`, e todos os hiperlinks serão preservados como anotações
      PDF separadas quando o documento for salvo.
    question: Se eu adicionar mais de um comentário, cada hiperlink funcionará no
      PDF exportado?
  - answer: Abra o PDF gerado, localize a anotação de comentário (geralmente exibida
      como um ícone de nota), clique nela para revelar o texto do comentário e, em
      seguida, clique no link azul sublinhado; ele deve abrir a URL de destino em
      um navegador web.
    question: Como verifico se o hiperlink dentro do comentário realmente funciona
      após a geração do PDF?
  type: FAQPage
images:
- /net/working-with-comments/add-hyperlink-comment/og-image.png
og_title: Inserir Comentário com Hiperlink & Exportar para PDF
og_description: Aprenda a incorporar um link clicável em um comentário Word e transformá‑lo em uma anotação PDF.
og_image_alt: Guia que mostra como adicionar um comentário com um hiperlink clicável a um documento Word e exportá‑lo como uma anotação PDF usando Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Adicionar Comentário com Hiperlink e Exportar como Anotação PDF Usando Aspose.Words
Neste tutorial você verá como criar um documento Word, inserir um comentário que contém um hiperlink clicável para um site externo, configurar esse comentário para aparecer como uma anotação PDF, exportar o documento para PDF e verificar o arquivo PDF resultante. O código passo a passo permite adicionar comentários ricos e habilitados com links e preservá‑los ao converter para PDF, facilitando o compartilhamento de notas interativas com os leitores.

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

**Q: O que controla o terceiro argumento (`false`) em `InsertHyperlink`?**  
A: O terceiro parâmetro de `InsertHyperlink` especifica se o link deve ser tratado como um campo; defini‑lo como `false` insere um hiperlink simples que funciona na anotação PDF sem precisar de um código de campo.

**Q: Como posso fazer o comentário aparecer como um balão no documento Word em vez de uma anotação PDF?**  
A: Defina `myDocument.LayoutOptions.CommentDisplayMode` como `CommentDisplayMode.ShowInBalloons` antes de chamar `Save`; o PDF então conterá o comentário como um comentário Word normal, em vez de uma anotação.

**Q: Se eu adicionar mais de um comentário, cada hiperlink funcionará no PDF exportado?**  
A: Sim—cada `Comment` que você anexa a um parágrafo pode conter sua própria chamada `InsertHyperlink`, e todos os hiperlinks serão preservados como anotações PDF separadas quando o documento for salvo.

**Q: Como verifico se o hiperlink dentro do comentário realmente funciona após a geração do PDF?**  
A: Abra o PDF gerado, localize a anotação de comentário (geralmente exibida como um ícone de nota), clique nela para revelar o texto do comentário e, em seguida, clique no link azul sublinhado; ele deve abrir a URL de destino em um navegador web.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}