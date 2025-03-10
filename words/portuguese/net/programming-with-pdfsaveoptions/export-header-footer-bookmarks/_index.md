---
title: Exportar marcadores de cabeçalho e rodapé de documento do Word para documento PDF
linktitle: Exportar marcadores de cabeçalho e rodapé de documento do Word para documento PDF
second_title: API de processamento de documentos Aspose.Words
description: Aprenda como exportar marcadores de cabeçalho e rodapé de um documento do Word para PDF usando o Aspose.Words para .NET com nosso guia passo a passo.
weight: 10
url: /pt/net/programming-with-pdfsaveoptions/export-header-footer-bookmarks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Exportar marcadores de cabeçalho e rodapé de documento do Word para documento PDF

## Introdução

Converter documentos do Word para PDF é uma tarefa comum, especialmente quando você quer compartilhar ou arquivar documentos preservando sua formatação. Às vezes, esses documentos contêm marcadores importantes dentro dos cabeçalhos e rodapés. Neste tutorial, vamos percorrer o processo de exportação desses marcadores de um documento do Word para um PDF usando o Aspose.Words para .NET.

## Pré-requisitos

Antes de começarmos, certifique-se de ter o seguinte:

- Aspose.Words para .NET: Você precisa ter o Aspose.Words para .NET instalado. Você pode baixá-lo em[aqui](https://releases.aspose.com/words/net/).
- Ambiente de desenvolvimento: Configure seu ambiente de desenvolvimento. Você pode usar o Visual Studio ou qualquer outro IDE compatível com .NET.
- Conhecimento básico de C#: É necessário ter familiaridade com programação em C# para acompanhar os exemplos de código.

## Importar namespaces

Primeiro, você precisa importar os namespaces necessários no seu projeto C#. Adicione estas linhas no topo do seu arquivo de código:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Vamos dividir o processo em etapas fáceis de seguir.

## Etapa 1: Inicializar o documento

primeiro passo é carregar seu documento do Word. Veja como você pode fazer isso:

```csharp
// O caminho para o diretório de documentos.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks in headers and footers.docx");
```

Nesta etapa, você simplesmente especifica o caminho para o diretório do documento e carrega o documento do Word.

## Etapa 2: Configurar opções de salvamento de PDF

Em seguida, você precisa configurar as opções de salvamento de PDF para garantir que os marcadores nos cabeçalhos e rodapés sejam exportados corretamente.

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.OutlineOptions.DefaultBookmarksOutlineLevel = 1;
saveOptions.HeaderFooterBookmarksExportMode = HeaderFooterBookmarksExportMode.First;
```

 Aqui, estamos configurando o`PdfSaveOptions` . O`DefaultBookmarksOutlineLevel` propriedade define o nível de estrutura para marcadores e o`HeaderFooterBookmarksExportMode` propriedade garante que apenas a primeira ocorrência de marcadores em cabeçalhos e rodapés seja exportada.

## Etapa 3: Salve o documento como PDF

Por fim, salve seu documento como PDF com as opções configuradas.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.ExportHeaderFooterBookmarks.pdf", saveOptions);
```

Nesta etapa, você salva o documento no caminho especificado com as opções configuradas.

## Conclusão

aí está! Seguindo esses passos, você pode facilmente exportar marcadores dos cabeçalhos e rodapés de um documento do Word para um PDF usando o Aspose.Words para .NET. Esse método garante que importantes auxílios de navegação dentro do seu documento sejam preservados no formato PDF, facilitando a navegação dos leitores pelo seu documento.

## Perguntas frequentes

### Posso exportar todos os favoritos do documento do Word para PDF?

 Sim, você pode. No`PdfSaveOptions`, você pode ajustar as configurações para incluir todos os favoritos, se necessário.

### E se eu quiser exportar também os favoritos do corpo do documento?

 Você pode configurar o`OutlineOptions` em`PdfSaveOptions` para incluir marcadores do corpo do documento.

### É possível personalizar os níveis de marcadores no PDF?

 Absolutamente! Você pode personalizar o`DefaultBookmarksOutlineLevel` propriedade para definir diferentes níveis de contorno para seus favoritos.

### Como lidar com documentos sem marcadores?

Se o seu documento não tiver marcadores, o PDF será gerado sem nenhum esboço de marcador. Certifique-se de que seu documento contenha marcadores se precisar deles no PDF.

### Posso usar esse método para outros tipos de documentos, como DOCX ou RTF?

Sim, o Aspose.Words para .NET suporta vários tipos de documentos, incluindo DOCX, RTF e outros.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
