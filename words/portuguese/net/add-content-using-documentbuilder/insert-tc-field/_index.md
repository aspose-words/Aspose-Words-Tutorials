---
title: Inserir campo TC em documento Word usando Aspose.Words for .NET
weight: 110
limit:
description: Aprenda a inserir um campo TC com texto personalizado em um documento Word usando Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, insert TC field, TC field Word, DocumentBuilder TC field, Word document index, table of contents field]
url: /net/add-content-using-documentbuilder/insert-tc-field/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Inserir campo TC em documento Word usando Aspose.Words
Este tutorial mostra como usar Aspose.Words for .NET para inserir um campo TC (Table of Contents) em um documento Word recém‑criado. Usando DocumentBuilder, você pode adicionar um campo TC com texto de entrada personalizado, o que é útil para criar um índice pesquisável para um sumário. O exemplo também demonstra como salvar o documento no disco.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-tc-field" >}}


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

**Q: O que significa a opção "\f t" no código do campo TC?**
A: A opção "\f t" indica ao Word que trate a entrada como uma entrada de tabela, fazendo com que ela apareça em um Sumário gerado com a opção \f.

**Q: Como posso alterar o texto que aparece no campo TC?**
A: Substitua "Entry Text" na chamada InsertField por qualquer string que desejar, por exemplo, builder.InsertField("TC \"Chapter 1\" \f t");

**Q: Posso inserir múltiplos campos TC no mesmo documento?**
A: Sim; basta chamar builder.InsertField com textos de entrada diferentes nos locais desejados antes de salvar o documento.

**Q: Este código funciona para formatos diferentes de .docx, como .pdf?**
A: O documento é salvo como .docx no exemplo, mas Aspose.Words pode salvar em outros formatos (por exemplo, .pdf) alterando a extensão do arquivo em doc.Save e garantindo que o formato de saída apropriado seja suportado.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}