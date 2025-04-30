---
"description": "Guia passo a passo para reduzir o tamanho do PDF com fontes wmf em escala para o tamanho do metafile ao converter para PDF com o Aspose.Words para .NET."
"linktitle": "Reduza o tamanho do PDF com fontes WMF em escala para o tamanho do metarquivo"
"second_title": "API de processamento de documentos Aspose.Words"
"title": "Reduza o tamanho do PDF com fontes WMF em escala para o tamanho do metarquivo"
"url": "/pt/net/programming-with-pdfsaveoptions/scale-wmf-fonts-to-metafile-size/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Reduza o tamanho do PDF com fontes WMF em escala para o tamanho do metarquivo

## Introdução

Ao trabalhar com arquivos PDF, especialmente aqueles gerados a partir de documentos do Word que contêm gráficos WMF (Windows Metafile), o gerenciamento de tamanho pode se tornar um aspecto crucial do processamento de documentos. Uma maneira de controlar o tamanho do PDF é ajustar a forma como as fontes WMF são renderizadas no documento. Neste tutorial, exploraremos como reduzir o tamanho do PDF dimensionando as fontes WMF para o tamanho do metafile usando o Aspose.Words para .NET.

## Pré-requisitos

Antes de começar as etapas, certifique-se de ter o seguinte:

1. Aspose.Words para .NET: Certifique-se de ter a biblioteca Aspose.Words instalada. Caso contrário, você pode [baixe aqui](https://releases.aspose.com/words/net/).
2. Ambiente de desenvolvimento: Este tutorial pressupõe que você tenha um ambiente de desenvolvimento .NET configurado (como o Visual Studio), onde você pode escrever e executar código C#.
3. Noções básicas de programação .NET: familiaridade com conceitos básicos de programação .NET e sintaxe C# será útil.
4. Documento do Word com gráficos WMF: você precisará de um documento do Word contendo gráficos WMF. Você pode usar seu próprio documento ou criar um para teste.

## Importar namespaces

Primeiro, você precisa importar os namespaces necessários para o seu projeto C#. Isso lhe dará acesso às classes e métodos necessários para trabalhar com Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Etapa 1: Carregue o documento do Word

Para começar, carregue o documento do Word que contém os gráficos WMF. Isso é feito usando o `Document` classe do Aspose.Words.

```csharp
// O caminho para o diretório de documentos.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Carregar o documento
Document doc = new Document(dataDir + "WMF with text.docx");
```

Aqui, `dataDir` é um espaço reservado para o caminho do diretório do seu documento. Criamos uma instância do `Document` classe, passando o caminho para o arquivo do Word. Isso carrega o documento na memória, pronto para processamento posterior.

## Etapa 2: Configurar opções de renderização de metarquivo

Em seguida, você precisa configurar as opções de renderização do metarquivo. Especificamente, defina o `ScaleWmfFontsToMetafileSize` propriedade para `false`. Isso controla se as fontes WMF são dimensionadas para corresponder ao tamanho do metarquivo.

```csharp
// Crie uma nova instância de MetafileRenderingOptions
MetafileRenderingOptions metafileRenderingOptions = new MetafileRenderingOptions
{
    ScaleWmfFontsToMetafileSize = false
};
```

O `MetafileRenderingOptions` A classe fornece opções de como os metarquivos (como WMF) são renderizados. Ao definir `ScaleWmfFontsToMetafileSize` para `false`, você está instruindo o Aspose.Words a não dimensionar as fontes de acordo com o tamanho do metarquivo, o que pode ajudar a reduzir o tamanho geral do PDF.

## Etapa 3: definir opções de salvamento de PDF

Agora, configure as opções de salvamento do PDF para usar as opções de renderização de metarquivos que você acabou de definir. Isso informa ao Aspose.Words como lidar com metarquivos ao salvar o documento como PDF.

```csharp
// Crie uma nova instância de PdfSaveOptions
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    MetafileRenderingOptions = metafileRenderingOptions
};
```

O `PdfSaveOptions` A classe permite que você especifique várias configurações para salvar o documento como PDF. Ao atribuir as configurações previamente configuradas `MetafileRenderingOptions` para o `MetafileRenderingOptions` propriedade de `PdfSaveOptions`, você garante que o documento seja salvo de acordo com as configurações de renderização de metarquivo desejadas.

## Etapa 4: Salve o documento como PDF

Por fim, salve o documento do Word como PDF usando as opções de salvamento configuradas. Isso aplicará todas as configurações, incluindo as opções de renderização de metarquivos, ao PDF de saída.


```csharp
// Salvar o documento como PDF
doc.Save(dataDir + "WorkingWithPdfSaveOptions.ScaleWmfFontsToMetafileSize.pdf", saveOptions);
```

Nesta etapa, o `Save` método do `Document` A classe é usada para exportar o documento para um arquivo PDF. O caminho onde o PDF será salvo é especificado, juntamente com o `PdfSaveOptions` que incluem as configurações de renderização do metarquivo.

## Conclusão

Ao dimensionar fontes WMF para o tamanho de metarquivo, você pode reduzir significativamente o tamanho dos seus arquivos PDF gerados a partir de documentos do Word. Essa técnica ajuda a otimizar o armazenamento e a distribuição de documentos sem comprometer a qualidade do conteúdo visual. Seguir os passos descritos acima garante que seus arquivos PDF sejam mais gerenciáveis e tenham um tamanho mais eficiente.

## Perguntas frequentes

### O que é WMF e por que ele é importante para o tamanho do PDF?

WMF (Windows Metafile) é um formato gráfico usado no Microsoft Windows. Ele pode conter dados vetoriais e bitmap. Como os dados vetoriais podem ser redimensionados e manipulados, é importante manipulá-los adequadamente para evitar arquivos PDF desnecessariamente grandes.

### Como o dimensionamento de fontes WMF para o tamanho do metarquivo afeta o PDF?

Dimensionar fontes WMF para o tamanho do metarquivo pode ajudar a reduzir o tamanho geral do PDF, evitando a renderização de fontes de alta resolução que pode aumentar o tamanho do arquivo.

### Posso usar outros formatos de metarquivo com o Aspose.Words?

Sim, o Aspose.Words suporta vários formatos de metarquivo, incluindo EMF (Enhanced Metafile), além de WMF.

### Essa técnica é aplicável a todos os tipos de documentos do Word?

Sim, essa técnica pode ser aplicada a qualquer documento do Word que contenha gráficos WMF, ajudando a otimizar o tamanho do PDF gerado.

### Onde posso encontrar mais informações sobre o Aspose.Words?

Você pode explorar mais sobre Aspose.Words no [Documentação do Aspose.Words](https://reference.aspose.com/words/net/)Para downloads, testes e suporte, visite o [Página de download do Aspose.Words](https://releases.aspose.com/words/net/), [Compre Aspose.Words](https://purchase.aspose.com/buy), [Teste grátis](https://releases.aspose.com/), [Licença Temporária](https://purchase.aspose.com/temporary-license/), e [Apoiar](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}