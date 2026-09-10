---
title: Inserir HTML alinhado em documento Word usando Aspose.Words for .NET
weight: 210
limit:
description: Aprenda a inserir HTML bruto com alinhamento à esquerda, centro ou direita em um documento Word usando Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, insert html word document, html alignment, documentbuilder html, c# insert html, aligned html in word]
url: /net/add-content-using-documentbuilder/insert-aligned-html/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Inserir HTML alinhado em documento Word usando Aspose.Words
Este tutorial interativo mostra como incorporar HTML bruto em um documento Word enquanto controla seu alinhamento—esquerda, centro ou direita—usando Aspose.Words for .NET. Aproveitando Document e DocumentBuilder, você pode inserir uma string HTML e aplicar o alinhamento de parágrafo desejado em apenas algumas linhas de código. O exemplo é ideal quando você precisa preservar a formatação HTML e posicionar o conteúdo precisamente dentro do seu documento.

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

**Q: O que acontece se a string HTML passada para DocumentBuilder.InsertHtml contiver tags que o Aspose.Words não suporta, como <script> ou <iframe>?**
A: Tags não suportadas são ignoradas; o Aspose.Words analisa apenas o subconjunto de HTML que pode renderizar, portanto <script>, <iframe> e elementos semelhantes são removidos enquanto o restante do conteúdo é inserido.

**Q: Os estilos CSS inline (por exemplo, <span style=\"color:red;\">) serão preservados ao usar InsertHtml?**
A: Sim, InsertHtml respeita muitas propriedades CSS inline como cor, tamanho da fonte e plano de fundo, convertendo-as para a formatação correspondente no Word.

**Q: O InsertHtml cria automaticamente um novo parágrafo para elementos de bloco como <div> ou <h1>?**
A: Elementos de bloco são mapeados para parágrafos do Word, de modo que cada <div>, <p>, <h1>, etc., se torna um parágrafo separado no documento.

**Q: Como posso inserir HTML em um local específico de um documento existente em vez de no início?**
A: Mova o cursor do DocumentBuilder para o nó desejado (por exemplo, builder.MoveToDocumentEnd() ou builder.MoveToParagraph(index)) antes de chamar InsertHtml; o HTML será inserido na posição atual do cursor.

**Q: Se o documento já contém texto, a chamada a InsertHtml sobrescreverá o conteúdo existente?**
A: Não, InsertHtml insere o HTML analisado na posição atual do builder sem excluir nós existentes, a menos que você mova explicitamente o cursor para dentro desses nós ou os exclua previamente.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}