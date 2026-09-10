---
title: Inserir Forma de Linha Horizontal em Documento Word Usando Aspose.Words para .NET
weight: 110
limit:
description: Guia passo a passo para inserir uma forma de linha horizontal em um documento Word com Aspose.Words para .NET.
keywords: [Aspose.Words for .NET, insert horizontal rule shape, horizontal rule shape .NET, DocumentBuilder horizontal rule, add horizontal line Word, create Word document Aspose]
url: /net/add-content-using-documentbuilder/insert-horizontal-rule-shape/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Inserir Forma de Linha Horizontal em Documento Word Usando Aspose.Words para .NET
Aprenda a usar Aspose.Words para .NET para inserir uma forma de linha horizontal em um documento Word. Este tutorial orienta você na criação de um novo documento, na adição de uma linha de texto, na colocação de uma forma de linha horizontal com DocumentBuilder e na gravação do arquivo. A linha horizontal fornece um separador visual simples para o seu conteúdo.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-horizontal-rule-shape" >}}


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

**Q: Posso alterar a aparência (cor, espessura) da linha horizontal inserida com DocumentBuilder.InsertHorizontalRule()?**
A: InsertHorizontalRule cria uma forma de linha horizontal incorporada com formatação padrão; para modificar sua aparência, você deve obter o objeto Shape inserido (builder.CurrentParagraph.LastChild) e ajustar as propriedades LineFormat.

**Q: O que acontece se eu chamar InsertHorizontalRule() após um parágrafo que já termina com uma quebra de linha?**
A: O método insere a linha como um parágrafo separado, portanto, qualquer quebra de linha anterior simplesmente cria um parágrafo vazio antes da linha; a linha ainda aparecerá em sua própria linha.

**Q: É possível inserir mais de uma linha horizontal no mesmo documento usando DocumentBuilder?**
A: Sim, cada chamada a builder.InsertHorizontalRule() adiciona uma nova forma de linha horizontal na posição atual do cursor, permitindo múltiplas linhas ao longo do documento.

**Q: O InsertHorizontalRule() funciona ao salvar o documento em formatos diferentes de DOCX, como PDF?**
A: A linha horizontal é armazenada como uma forma no modelo do documento, portanto, ao salvar em PDF, XPS ou outros formatos suportados, a linha é renderizada corretamente na saída.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}