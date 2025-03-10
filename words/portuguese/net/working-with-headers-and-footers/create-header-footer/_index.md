---
title: Criar Cabeçalho Rodapé
linktitle: Criar Cabeçalho Rodapé
second_title: API de processamento de documentos Aspose.Words
description: Aprenda como adicionar e personalizar cabeçalhos e rodapés em documentos do Word usando o Aspose.Words para .NET. Este guia passo a passo garante formatação profissional de documentos.
weight: 10
url: /pt/net/working-with-headers-and-footers/create-header-footer/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar Cabeçalho Rodapé

## Introdução

Adicionar cabeçalhos e rodapés aos seus documentos pode aumentar seu profissionalismo e legibilidade. Com o Aspose.Words para .NET, você pode facilmente criar e personalizar cabeçalhos e rodapés para seus documentos do Word. Neste tutorial, nós o guiaremos pelo processo passo a passo, garantindo que você possa implementar esses recursos perfeitamente.

## Pré-requisitos

Antes de começar, certifique-se de ter o seguinte:

-  Aspose.Words para .NET: Baixe e instale a partir do[link para download](https://releases.aspose.com/words/net/).
- Ambiente de desenvolvimento: como o Visual Studio, para escrever e executar seu código.
- Conhecimento básico de C#: compreensão do C# e do framework .NET.
- Documento de exemplo: Um documento de exemplo para aplicar cabeçalhos e rodapés, ou criar um novo, conforme mostrado no tutorial.

## Importar namespaces

Primeiro, você precisa importar os namespaces necessários para acessar as classes e métodos do Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System;
```

## Etapa 1: Defina o diretório do documento

Defina o diretório onde seu documento será salvo. Isso ajuda a gerenciar o caminho de forma eficaz.

```csharp
// O caminho para o diretório de documentos
string dataDir = "YOUR_DIRECTORY_OF_DOCUMENTS";
```

## Etapa 2: Crie um novo documento

 Crie um novo documento e um`DocumentBuilder`para facilitar a adição de conteúdo.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Etapa 3: Configurar a configuração da página

Defina as configurações da página, incluindo se a primeira página terá um cabeçalho/rodapé diferente.

```csharp
Section currentSection = builder.CurrentSection;
PageSetup pageSetup = currentSection.PageSetup;

pageSetup.DifferentFirstPageHeaderFooter = true;
pageSetup.HeaderDistance = 20;
```

## Etapa 4: adicione um cabeçalho à primeira página

Vá para a seção de cabeçalho da primeira página e configure o texto do cabeçalho.

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.HeaderFirst);
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;

builder.Font.Name = "Arial";
builder.Font.Bold = true;
builder.Font.Size = 14;

builder.Write("Aspose.Words Header/Footer Creation Primer - Title Page.");
```

## Etapa 5: Adicionar um cabeçalho primário

Vá para a seção de cabeçalho principal e insira uma imagem e um texto.

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.HeaderPrimary);

// Insira uma imagem no cabeçalho
builder.InsertImage(dataDir + "Graphics Interchange Format.gif", 
    RelativeHorizontalPosition.Page, 10, RelativeVerticalPosition.Page, 10, 50, 50, WrapType.Through);

builder.ParagraphFormat.Alignment = ParagraphAlignment.Right;
builder.Write("Aspose.Words Header/Footer Creation Primer.");
```

## Etapa 6: Adicionar um rodapé primário

Vá para a seção de rodapé principal e crie uma tabela para formatar o conteúdo do rodapé.

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.FooterPrimary);

builder.StartTable();
builder.CellFormat.ClearFormatting();
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 / 3);

// Adicionar numeração de página
builder.Write("Page ");
builder.InsertField("PAGE", "");
builder.Write(" of ");
builder.InsertField("NUMPAGES", "");

builder.CurrentParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Left;
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 * 2 / 3);

builder.Write("(C) 2001 Aspose Pty Ltd. All rights reserved.");
builder.CurrentParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Right;

builder.EndRow();
builder.EndTable();
```

## Etapa 7: Adicionar conteúdo e quebras de página

Vá para o final do documento, adicione uma quebra de página e crie uma nova seção com configurações de página diferentes.

```csharp
builder.MoveToDocumentEnd();
builder.InsertBreak(BreakType.PageBreak);
builder.InsertBreak(BreakType.SectionBreakNewPage);

currentSection = builder.CurrentSection;
pageSetup = currentSection.PageSetup;
pageSetup.Orientation = Orientation.Landscape;
pageSetup.DifferentFirstPageHeaderFooter = false;

currentSection.HeadersFooters.LinkToPrevious(false);
CopyHeadersFootersFromPreviousSection(currentSection);

HeaderFooter primaryFooter = currentSection.HeadersFooters[HeaderFooterType.FooterPrimary];
Row row = primaryFooter.Tables[0].FirstRow;
row.FirstCell.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 / 3);
row.LastCell.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 * 2 / 3);

doc.Save(dataDir + "WorkingWithHeadersAndFooters.CreateHeaderFooter.docx");
```

## Etapa 8: Copie os cabeçalhos e rodapés da seção anterior

Se você quiser reutilizar cabeçalhos e rodapés de uma seção anterior, copie-os e aplique as modificações necessárias.

```csharp
private static void CopyHeadersFootersFromPreviousSection(Section section)
{
    Section previousSection = (Section)section.PreviousSibling;
    if (previousSection == null) return;

    section.HeadersFooters.Clear();

    foreach (HeaderFooter headerFooter in previousSection.HeadersFooters)
    {
        section.HeadersFooters.Add(headerFooter.Clone(true));
    }
}
```

## Conclusão

Seguindo essas etapas, você pode efetivamente adicionar e personalizar cabeçalhos e rodapés em seus documentos do Word usando o Aspose.Words para .NET. Isso melhora a aparência e o profissionalismo do seu documento, tornando-o mais legível e envolvente.

## Perguntas frequentes

### O que é Aspose.Words para .NET?

Aspose.Words para .NET é uma biblioteca que permite aos desenvolvedores criar, editar e converter documentos do Word programaticamente em aplicativos .NET.

### Posso adicionar imagens ao cabeçalho ou rodapé?

 Sim, você pode adicionar facilmente imagens ao cabeçalho ou rodapé usando o`DocumentBuilder.InsertImage` método.

### Como defino cabeçalhos e rodapés diferentes para a primeira página?

 Você pode definir diferentes cabeçalhos e rodapés para a primeira página usando o`DifferentFirstPageHeaderFooter` propriedade do`PageSetup` aula.

### Onde posso encontrar mais documentação sobre o Aspose.Words?

 Você pode encontrar documentação abrangente sobre o[Página de documentação da API Aspose.Words](https://reference.aspose.com/words/net/).

### Há suporte disponível para o Aspose.Words?

 Sim, a Aspose oferece suporte por meio de seu[fórum de suporte](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
