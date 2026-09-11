---
title: Inserir HTML Alinhado em Documento Word Usando Aspose.Words for .NET
weight: 210
limit:
description: Aprenda a inserir HTML com alinhamento específico em um documento Word usando Aspose.Words for .NET.
keywords: [insert aligned html, Aspose.Words for .NET, documentbuilder html insertion, html alignment in word, c# insert html word]
url: /net/add-content-using-documentbuilder/insert-aligned-html/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Inserir HTML Alinhado em Documento Word Usando Aspose.Words
Este tutorial demonstra como usar o DocumentBuilder do Aspose.Words for .NET para incorporar marcação HTML em um documento Word e controlar seu alinhamento. Você verá como inserir o HTML, definir o alinhamento do parágrafo (esquerda, centro ou direita) e, em seguida, salvar o documento resultante. O exemplo é ideal para desenvolvedores que precisam preservar a formatação estilo web ao gerar arquivos Word programaticamente.

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

**Q: O InsertHtml pode ser usado para adicionar HTML em um documento Word existente em vez de um novo?**  
A: Sim. Crie um Document a partir do arquivo existente, posicione o cursor do DocumentBuilder onde você deseja inserir o HTML (por exemplo, usando builder.MoveToDocumentEnd()) e, em seguida, chame builder.InsertHtml com sua marcação.

**Q: Quais atributos HTML são respeitados pelo InsertHtml para alinhamento?**  
A: O InsertHtml respeita o atributo "align" em elementos de nível de bloco como &lt;p&gt;, &lt;div&gt; e tags de título, aplicando o alinhamento de parágrafo correspondente no documento Word resultante.

**Q: O que acontece se a string HTML contiver tags ou CSS não suportados?**  
A: Tags não suportadas são ignoradas e seu texto interno é inserido como texto simples; estilos CSS inline que o Aspose.Words não reconhece também são ignorados, portanto apenas o subconjunto suportado de HTML é renderizado.

**Q: Preciso fechar o DocumentBuilder antes de salvar o documento?**  
A: Não é necessário fechar explicitamente; após inserir o HTML, você pode chamar diretamente doc.Save com o nome e formato de arquivo desejados, e os recursos do builder são liberados automaticamente.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}