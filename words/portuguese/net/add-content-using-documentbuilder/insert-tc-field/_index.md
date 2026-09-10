---
title: Adicionar um campo TC a um documento Word com Aspose.Words for .NET
weight: 310
limit:
description: Aprenda a inserir um campo TC em um novo documento Word com Aspose.Words for .NET usando DocumentBuilder.
keywords: [Aspose.Words for .NET, insert TC field, DocumentBuilder TC field, Word document indexing, add TC field programmatically, TC field tutorial]
url: /net/add-content-using-documentbuilder/insert-tc-field/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Adicionar um campo TC a um documento Word com Aspose.Words
Neste tutorial interativo, você aprenderá como adicionar programaticamente um campo TC — um marcador oculto usado pelos recursos de indexação e tabela de conteúdo do Word — a um documento recém‑criado usando Aspose.Words for .NET. Ao usar o DocumentBuilder, você pode posicionar o campo exatamente onde precisar e, em seguida, salvar o arquivo, pronto para processamento adicional.

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

**Q: O que o campo "TC" inserido por `builder.InsertField(\"TC \\\"Entry Text\\\" \\\\f t\")` realmente faz no documento Word?**
A: Ele cria uma entrada na Tabela de Conteúdo com o texto visível "Entry Text" e a marca como uma entrada TC (Tabela de Conteúdo), que o Word pode usar posteriormente ao gerar a TOC.

**Q: Qual é o propósito da opção `\\f t` na string do campo TC?**
A: A opção `\\f t` indica ao Word que trate a entrada como um texto normal (em vez de um título) e que a inclua na Tabela de Conteúdo quando a TOC for criada.

**Q: Posso inserir múltiplos campos TC com textos de entrada diferentes usando a mesma instância de `DocumentBuilder`?**
A: Sim; basta chamar `builder.InsertField` novamente com uma string diferente, por exemplo, `builder.InsertField(\"TC \\\"Another Entry\\\" \\\\f t\")`, e cada chamada insere um novo campo TC na posição atual do cursor.

**Q: Se eu precisar que o texto da entrada seja dinâmico (por exemplo, proveniente de uma variável), como devo formatar a chamada `InsertField`?**
A: Construa a string do campo usando interpolação de strings ou `String.Format`, por exemplo: `string entry = \"Chapter 1\"; builder.InsertField($\"TC \\\"{entry}\\\" \\\\f t\");`.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}