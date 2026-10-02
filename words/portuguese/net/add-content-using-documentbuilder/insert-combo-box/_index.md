---
title: Adicionar um Campo de Formulário Combo Box a um Documento Word com Aspose.Words for .NET
weight: 310
limit:
description: Aprenda a adicionar um campo de formulário combo box com itens predefinidos a um documento Word usando Aspose.Words for .NET.
keywords: [combo box form field, Aspose.Words for .NET, documentbuilder combo box, add combo box word, word document form field]
url: /net/add-content-using-documentbuilder/insert-combo-box/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Adicionar um Campo de Formulário Combo Box a um Documento Word com Aspose.Words
Este tutorial demonstra como usar o DocumentBuilder do Aspose.Words for .NET para criar um novo documento Word e inserir um campo de formulário combo box preenchido com itens predefinidos. Ao seguir o código passo a passo, você verá como configurar as opções do combo box e, em seguida, salvar o documento para uso em formulários interativos.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-combo-box" >}}


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

**Q: O que representa o array `items` passado para `InsertComboBox`?**
A: Ele define a lista de strings que aparecem como opções selecionáveis no menu suspenso do combo box.

**Q: Como posso alterar qual item é selecionado por padrão quando o documento é aberto?**
A: Defina o terceiro argumento (`selectedIndex`) de `InsertComboBox` como o índice baseado em zero do item padrão desejado (por exemplo, `2` para "Three").

**Q: É possível posicionar o combo box em um local específico no documento?**
A: Sim—mova o cursor do `DocumentBuilder` para o local desejado usando métodos como `MoveToParagraph`, `InsertParagraph` ou `Write` antes de chamar `InsertComboBox`.

**Q: Qual formato de arquivo é criado por este código e ele pode ser aberto em versões mais antigas do Word?**
A: O código salva um arquivo `.docx`, que pode ser aberto pelo Word 2007 e versões posteriores, bem como por qualquer aplicativo que suporte o formato OpenXML.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}