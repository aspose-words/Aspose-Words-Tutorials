---
"description": "Aprenda a exportar recursos como CSS e fontes enquanto salva documentos do Word como HTML usando o Aspose.Words para .NET. Siga nosso guia passo a passo."
"linktitle": "Recursos de Exportação"
"second_title": "API de processamento de documentos Aspose.Words"
"title": "Recursos de Exportação"
"url": "/pt/net/programming-with-htmlsaveoptions/export-resources/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Recursos de Exportação

## Introdução

Olá, caro entusiasta de tecnologia! Se você já precisou converter documentos do Word para HTML, está no lugar certo. Hoje, vamos mergulhar no maravilhoso mundo do Aspose.Words para .NET. Esta poderosa biblioteca facilita o trabalho com documentos do Word programaticamente. Neste tutorial, mostraremos os passos para exportar recursos, como fontes e CSS, ao salvar um documento do Word como HTML usando o Aspose.Words para .NET. Apertem os cintos para uma jornada divertida e informativa!

## Pré-requisitos

Antes de mergulharmos no código, vamos garantir que você tenha tudo o que precisa para começar. Aqui está uma lista de verificação rápida:

1. Visual Studio: Certifique-se de ter o Visual Studio instalado em sua máquina. Você pode baixá-lo do site [Site do Visual Studio](https://visualstudio.microsoft.com/).
2. Aspose.Words para .NET: Você precisará da biblioteca Aspose.Words para .NET. Se ainda não a possui, faça um teste gratuito em [Lançamentos Aspose](https://releases.aspose.com/words/net/) ou comprá-lo no [Loja Aspose](https://purchase.aspose.com/buy).
3. Conhecimento básico de C#: uma compreensão fundamental de C# ajudará você a acompanhar os exemplos de código.

Entendeu tudo? Ótimo! Vamos prosseguir com a importação dos namespaces necessários.

## Importar namespaces

Para usar o Aspose.Words para .NET, você precisa incluir os namespaces relevantes no seu projeto. Veja como fazer:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Esses namespaces são cruciais para acessar as classes e métodos Aspose.Words que usaremos em nosso tutorial.

Vamos detalhar o processo de exportação de recursos ao salvar um documento do Word como HTML. Faremos isso passo a passo para facilitar o acompanhamento.

## Etapa 1: configure seu diretório de documentos

Antes de mais nada, você precisa especificar o caminho para o diretório dos seus documentos. É lá que o seu documento do Word está localizado e onde o arquivo HTML será salvo.

```csharp
// O caminho para o diretório de documentos.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Substituir `"YOUR DOCUMENT DIRECTORY"` com o caminho real para seu diretório.

## Etapa 2: Carregue o documento do Word

Em seguida, vamos carregar o documento do Word que você deseja converter para HTML. Para este tutorial, usaremos um documento chamado `Rendering.docx`.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

Esta linha de código carrega o documento do diretório especificado.

## Etapa 3: Configurar opções de salvamento de HTML

Para exportar recursos como CSS e fontes, você precisa configurar o `HtmlSaveOptions`. Esta etapa é crucial para garantir que sua saída HTML seja bem estruturada e inclua os recursos necessários.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    CssStyleSheetType = CssStyleSheetType.External,
    ExportFontResources = true,
    ResourceFolder = dataDir + "Resources",
    ResourceFolderAlias = "http://example.com/recursos"
};
```

Vamos analisar o que cada opção faz:
- `CssStyleSheetType = CssStyleSheetType.External`: Esta opção especifica que os estilos CSS devem ser salvos em uma folha de estilo externa.
- `ExportFontResources = true`: Isso permite a exportação de recursos de fonte.
- `ResourceFolder = dataDir + "Resources"`: Especifica a pasta local onde os recursos (como fontes e arquivos CSS) serão salvos.
- `ResourceFolderAlias = "http://example.com/resources"`: Define um alias para a pasta de recursos, que será usado no arquivo HTML.

## Etapa 4: Salve o documento como HTML

Com as opções de salvamento configuradas, a etapa final é salvar o documento como um arquivo HTML. Veja como fazer:

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ExportResources.html", saveOptions);
```

Esta linha de código salva o documento no formato HTML, junto com os recursos exportados.

## Conclusão

E pronto! Você exportou recursos com sucesso ao salvar um documento do Word como HTML usando o Aspose.Words para .NET. Com esta poderosa biblioteca, manipular documentos do Word programaticamente se torna muito fácil. Seja trabalhando em um aplicativo web ou apenas convertendo documentos para uso offline, o Aspose.Words tem tudo o que você precisa.

## Perguntas frequentes

### Posso exportar imagens junto com fontes e CSS?
Sim, você pode! O Aspose.Words para .NET também suporta a exportação de imagens. Apenas certifique-se de configurar o `HtmlSaveOptions` de acordo.

### Existe uma maneira de incorporar CSS em vez de usar uma folha de estilo externa?
Com certeza. Você pode definir `CssStyleSheetType` para `CssStyleSheetType.Embedded` se você preferir estilos incorporados.

### Como posso personalizar o nome do arquivo HTML de saída?
Você pode especificar qualquer nome de arquivo que desejar no `doc.Save` método. Por exemplo, `doc.Save(dataDir + "CustomFileName.html", saveOptions);`.

### O Aspose.Words suporta outros formatos além de HTML?
Sim, ele suporta vários formatos, incluindo PDF, DOCX, TXT e mais. Confira o [documentação](https://reference.aspose.com/words/net/) para uma lista completa.

### Onde posso obter mais suporte e recursos?
Para obter mais ajuda, visite o [Fórum de Suporte Aspose.Words](https://forum.aspose.com/c/words/8). Você também pode encontrar documentação detalhada e exemplos no [Site Aspose](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}