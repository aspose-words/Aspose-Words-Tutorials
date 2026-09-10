---
title: Adicionar um Campo de Formulário de Caixa de Seleção a um Documento Word com Aspose.Words for .NET
weight: 210
limit:
description: Aprenda como adicionar programaticamente um campo de formulário de caixa de seleção a um novo documento Word usando Aspose.Words for .NET e salvar o arquivo.
keywords: [Aspose.Words for .NET, insert check box, check box form field, .NET DocumentBuilder, Word document automation, add form field programmatically]
url: /net/add-content-using-documentbuilder/insert-check-box/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Adicionar um Campo de Formulário de Caixa de Seleção a um Documento Word com Aspose.Words
Este tutorial mostra como criar um novo documento Word e usar o DocumentBuilder do Aspose.Words for .NET para inserir um campo de formulário de caixa de seleção. Ao seguir os passos, você verá o código exato necessário para adicionar o elemento interativo e, em seguida, salvar o documento em um arquivo. É uma maneira rápida de criar arquivos Word com formulários habilitados programaticamente.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-check-box" >}}


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

**Q: O que representa o quarto argumento (0) em InsertCheckBox?**
A: Ele especifica o tamanho visual da caixa de seleção em pontos; um valor 0 indica ao Aspose.Words que use o tamanho padrão.

**Q: Posso inserir mais de uma caixa de seleção com o mesmo nome?**
A: Não – cada nome de campo de formulário deve ser exclusivo; tentar inserir outra caixa de seleção chamada "CheckBox" lançará uma ArgumentException.

**Q: Como adiciono uma caixa de seleção a um documento existente em vez de um novo?**
A: Carregue o documento primeiro (por exemplo, `Document doc = new Document("Existing.docx");`) então crie um DocumentBuilder para esse documento e chame `InsertCheckBox` na posição de cursor desejada.

**Q: Como posso ler o estado da caixa de seleção inserida após o documento ser salvo?**
A: Recupere o campo de formulário via `doc.Range.FormFields["CheckBox"]` e inspecione sua propriedade `Checked` para ver se está marcado.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}