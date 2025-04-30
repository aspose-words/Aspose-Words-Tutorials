---
"description": "Aprenda como exportar marcadores de cabeçalho e rodapé de um documento do Word para PDF usando o Aspose.Words para .NET com nosso guia passo a passo."
"linktitle": "Exportar marcadores de cabeçalho e rodapé de documento do Word para documento PDF"
"second_title": "API de processamento de documentos Aspose.Words"
"title": "Exportar marcadores de cabeçalho e rodapé de documento do Word para documento PDF"
"url": "/pt/net/programming-with-pdfsaveoptions/export-header-footer-bookmarks/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Exportar marcadores de cabeçalho e rodapé de documento do Word para documento PDF

## Introdução

Converter documentos do Word para PDF é uma tarefa comum, especialmente quando você deseja compartilhar ou arquivar documentos preservando sua formatação. Às vezes, esses documentos contêm marcadores importantes nos cabeçalhos e rodapés. Neste tutorial, mostraremos o processo de exportação desses marcadores de um documento do Word para um PDF usando o Aspose.Words para .NET.

## Pré-requisitos

Antes de começarmos, certifique-se de ter o seguinte:

- Aspose.Words para .NET: Você precisa ter o Aspose.Words para .NET instalado. Você pode baixá-lo em [aqui](https://releases.aspose.com/words/net/).
- Ambiente de desenvolvimento: configure seu ambiente de desenvolvimento. Você pode usar o Visual Studio ou qualquer outro IDE compatível com .NET.
- Conhecimento básico de C#: é necessário ter familiaridade com programação em C# para acompanhar os exemplos de código.

## Importar namespaces

Antes de mais nada, você precisa importar os namespaces necessários para o seu projeto C#. Adicione estas linhas no início do seu arquivo de código:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Vamos dividir o processo em etapas fáceis de seguir.

## Etapa 1: Inicializar o documento

O primeiro passo é carregar seu documento do Word. Veja como fazer isso:

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

Aqui, estamos configurando o `PdfSaveOptions`. O `DefaultBookmarksOutlineLevel` A propriedade define o nível de estrutura para marcadores e o `HeaderFooterBookmarksExportMode` propriedade garante que somente a primeira ocorrência de marcadores em cabeçalhos e rodapés seja exportada.

## Etapa 3: Salve o documento como PDF

Por fim, salve seu documento como PDF com as opções configuradas.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.ExportHeaderFooterBookmarks.pdf", saveOptions);
```

Nesta etapa, você salva o documento no caminho especificado com as opções configuradas.

## Conclusão

Pronto! Seguindo estes passos, você pode exportar facilmente os marcadores dos cabeçalhos e rodapés de um documento do Word para um PDF usando o Aspose.Words para .NET. Este método garante que os recursos de navegação importantes do seu documento sejam preservados no formato PDF, facilitando a navegação dos leitores.

## Perguntas frequentes

### Posso exportar todos os favoritos do documento do Word para PDF?

Sim, você pode. No `PdfSaveOptions`, você pode ajustar as configurações para incluir todos os favoritos, se necessário.

### E se eu quiser exportar também os marcadores do corpo do documento?

Você pode configurar o `OutlemeOptions` in `PdfSaveOptions` para incluir marcadores do corpo do documento.

### É possível personalizar os níveis de marcadores no PDF?

Com certeza! Você pode personalizar o `DefaultBookmarksOutlineLevel` propriedade para definir diferentes níveis de contorno para seus favoritos.

### Como lidar com documentos sem marcadores?

Se o seu documento não tiver marcadores, o PDF será gerado sem nenhum contorno de marcador. Certifique-se de que o documento contenha marcadores, caso precise deles no PDF.

### Posso usar esse método para outros tipos de documentos, como DOCX ou RTF?

Sim, o Aspose.Words para .NET suporta vários tipos de documentos, incluindo DOCX, RTF e outros.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}