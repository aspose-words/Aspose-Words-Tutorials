---
title: Inserir Forma de Regra Horizontal em Documento Word Usando Aspose.Words for .NET
weight: 110
limit:
description: Aprenda a adicionar uma forma de regra horizontal a um documento Word com Aspose.Words for .NET usando DocumentBuilder.
keywords: [Aspose.Words for .NET, insert horizontal rule shape, documentbuilder horizontal line, create Word document .NET, horizontal rule shape tutorial]
url: /net/add-content-using-documentbuilder/insert-horizontal-rule-shape/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Inserir Forma de Regra Horizontal em Documento Word Usando Aspose.Words
Neste tutorial você aprenderá como inserir programaticamente uma forma de regra horizontal em um documento Word com Aspose.Words for .NET. Usando as classes Document e DocumentBuilder criamos um novo documento, adicionamos um parágrafo de texto e, em seguida, posicionamos uma forma de linha horizontal no local desejado. A regra horizontal fornece um separador visual que pode ser útil para quebras de seção ou ênfase visual.

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

**Q: Onde exatamente `builder.InsertHorizontalRule()` coloca a linha no documento?**
A: `InsertHorizontalRule` insere uma forma de regra horizontal na posição atual do cursor do `DocumentBuilder`; se você quiser que ela fique em sua própria linha, chame `builder.Writeln()` antes da inserção.

**Q: Posso alterar a espessura, cor ou largura da regra horizontal inserida?**
A: `InsertHorizontalRule` adiciona uma regra com estilo padrão e não expõe opções de formatação; para personalizar essas propriedades, você precisa inserir um `Shape` manualmente (por exemplo, `builder.InsertShape(ShapeType.HorizontalLine)`) e então definir as propriedades `LineFormat`.

**Q: É possível adicionar mais de uma regra horizontal no mesmo documento?**
A: Sim—basta chamar `builder.InsertHorizontalRule()` sempre que precisar de uma nova regra; cada chamada cria uma forma separada na localização atual do builder.

**Q: A regra horizontal será visível quando o .docx salvo for aberto no Microsoft Word?**
A: Com certeza; a regra é salva como uma forma dentro do arquivo .docx, então o Word a exibe exatamente como aparece no documento gerado.

**Q: O que acontece se a pasta `dataDir` não existir antes de chamar `doc.Save(...)`?**
A: `doc.Save` lançará uma `DirectoryNotFoundException`; assegure que o diretório de destino exista ou crie-o programaticamente antes de salvar.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}