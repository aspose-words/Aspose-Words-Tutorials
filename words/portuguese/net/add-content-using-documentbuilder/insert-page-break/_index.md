---
title: Inserir quebra de página em um documento Word com Aspose.Words for .NET
weight: 110
limit:
description: Aprenda a adicionar quebras de página a um arquivo Word com Aspose.Words for .NET usando Document e DocumentBuilder.
keywords: [Aspose.Words for .NET, insert page break, documentbuilder page break, c# add page break, word document pagination]
url: /net/add-content-using-documentbuilder/insert-page-break/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Inserir quebra de página em um documento Word com Aspose.Words
Neste tutorial interativo, você aprenderá como adicionar programaticamente quebras de página a um documento Word usando Aspose.Words for .NET. Ao criar um objeto Document e usar o DocumentBuilder, você pode controlar onde as novas páginas começam, o que é essencial para formatar relatórios, faturas ou qualquer documento com várias seções. Siga o exemplo passo a passo para ver o código em ação e visualizar o arquivo resultante.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-page-break" >}}


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

**Q: Posso usar InsertBreak para adicionar uma quebra de linha ou uma quebra de seção em vez de uma quebra de página?**
A: Sim, InsertBreak aceita qualquer valor do enum BreakType, como BreakType.LineBreak ou BreakType.SectionBreakContinuous, para inserir a quebra correspondente.

**Q: Preciso chamar InsertBreak antes ou depois de escrever o texto para a nova página?**
A: InsertBreak deve ser chamado após o conteúdo que você deseja na página atual; o próximo Writeln então começará na nova página criada pela quebra.

**Q: O que acontece se o caminho dataDir não terminar com um separador de diretório?**
A: Se dataDir não possuir uma barra final, o nome do arquivo será concatenado diretamente (por exemplo, "C:\\DocsAddContentUsingDocumentBuilder.InsertBreak.docx"), o que pode gerar um caminho inválido; certifique‑se de que o caminho termine com "\\" ou use Path.Combine.

**Q: Posso reutilizar a mesma instância de DocumentBuilder para inserir várias quebras ao longo do documento?**
A: Sim, o mesmo DocumentBuilder pode ser usado repetidamente; cada chamada a InsertBreak insere uma quebra na posição atual do cursor do builder.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}