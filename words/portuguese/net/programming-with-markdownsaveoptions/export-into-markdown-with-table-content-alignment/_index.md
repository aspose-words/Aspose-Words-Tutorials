---
"description": "Aprenda a exportar documentos do Word para Markdown com tabelas alinhadas usando o Aspose.Words para .NET. Siga nosso guia passo a passo para tabelas Markdown perfeitas."
"linktitle": "Exportar para Markdown com alinhamento de conteúdo de tabela"
"second_title": "API de processamento de documentos Aspose.Words"
"title": "Exportar para Markdown com alinhamento de conteúdo de tabela"
"url": "/pt/net/programming-with-markdownsaveoptions/export-into-markdown-with-table-content-alignment/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Exportar para Markdown com alinhamento de conteúdo de tabela

## Introdução

Olá! Já se perguntou como exportar seu documento do Word para o formato Markdown com tabelas perfeitamente alinhadas? Seja você um desenvolvedor trabalhando em documentação ou apenas alguém que ama Markdown, este guia é para você. Vamos nos aprofundar nos detalhes do uso do Aspose.Words para .NET para conseguir isso. Pronto para transformar suas tabelas do Word em tabelas Markdown perfeitamente alinhadas? Vamos começar!

## Pré-requisitos

Antes de mergulharmos no código, há algumas coisas que você precisa ter em mãos:

1. Biblioteca Aspose.Words para .NET: Certifique-se de ter a biblioteca Aspose.Words para .NET. Você pode baixá-la do site [Página de lançamentos da Aspose](https://releases.aspose.com/words/net/).
2. Ambiente de desenvolvimento: configure seu ambiente de desenvolvimento. O Visual Studio é uma escolha popular para desenvolvimento .NET.
3. Conhecimento básico de C#: Entender C# é essencial, pois escreveremos código nessa linguagem.
4. Exemplo de documento do Word: tenha um documento do Word que você possa usar para testes.

## Importar namespaces

Antes de começarmos a programar, vamos importar os namespaces necessários. Eles nos darão acesso às classes e métodos Aspose.Words que usaremos.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Etapa 1: Inicializar o Documento e o DocumentBuilder

Primeiramente, precisamos criar um novo documento do Word e inicializar um `DocumentBuilder` objeto para começar a construir nosso documento.

```csharp
// O caminho para o diretório de documentos.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Crie um novo documento.
Document doc = new Document();

// Inicialize o DocumentBuilder.
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Etapa 2: inserir células e alinhar conteúdo

Em seguida, inseriremos algumas células no nosso documento e definiremos o alinhamento delas. Isso é crucial para garantir que a exportação em Markdown mantenha o alinhamento correto.

```csharp
// Insira uma célula e defina o alinhamento para a direita.
builder.InsertCell();
builder.ParagraphFormat.Alignment = ParagraphAlignment.Right;
builder.Write("Cell1");

// Insira outra célula e defina o alinhamento para o centro.
builder.InsertCell();
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;
builder.Write("Cell2");
```

## Etapa 3: definir o alinhamento do conteúdo da tabela para exportação em Markdown

Agora é hora de configurar o `MarkdownSaveOptions` para controlar o alinhamento do conteúdo da tabela no arquivo Markdown exportado. Salvaremos o documento com diferentes configurações de alinhamento para ver como funciona.

```csharp
// Crie o objeto MarkdownSaveOptions.
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions
{
    TableContentAlignment = TableContentAlignment.Left
};

// Salvar documento com alinhamento à esquerda.
doc.Save(dataDir + "LeftTableContentAlignment.md", saveOptions);

// Altere o alinhamento para a direita e salve.
saveOptions.TableContentAlignment = TableContentAlignment.Right;
doc.Save(dataDir + "RightTableContentAlignment.md", saveOptions);

// Altere o alinhamento para centralizar e salve.
saveOptions.TableContentAlignment = TableContentAlignment.Center;
doc.Save(dataDir + "CenterTableContentAlignment.md", saveOptions);
```

## Etapa 4: use o alinhamento automático de conteúdo da tabela

O `Auto` A opção de alinhamento assume o alinhamento do primeiro parágrafo na coluna correspondente da tabela. Isso pode ser útil quando você tem alinhamentos mistos em uma única tabela.

```csharp
// Defina o alinhamento como Automático.
saveOptions.TableContentAlignment = TableContentAlignment.Auto;

// Salvar documento com alinhamento automático.
doc.Save(dataDir + "AutoTableContentAlignment.md", saveOptions);
```

## Conclusão

E pronto! Exportar documentos do Word para Markdown com tabelas alinhadas usando o Aspose.Words para .NET é muito fácil quando você sabe como fazer. Esta poderosa biblioteca facilita o controle da formatação e do alinhamento das suas tabelas, garantindo que seus documentos Markdown tenham a aparência que você deseja. Boa programação!

## Perguntas frequentes

### O que é Aspose.Words para .NET?
Aspose.Words para .NET é uma biblioteca poderosa que permite aos desenvolvedores criar, modificar, converter e exportar documentos do Word programaticamente.

### Posso definir alinhamentos diferentes para colunas diferentes na mesma tabela?
Sim, usando o `Auto` opção de alinhamento, você pode ter alinhamentos diferentes com base no primeiro parágrafo de cada coluna.

### Preciso de uma licença para usar o Aspose.Words para .NET?
Sim, o Aspose.Words para .NET requer uma licença para funcionalidade completa. Você pode obter uma [licença temporária](https://purchase.aspose.com/temporary-license/) para avaliação.

### É possível exportar outros elementos do documento para Markdown usando o Aspose.Words?
Sim, o Aspose.Words suporta a exportação de vários elementos como títulos, listas e imagens para o formato Markdown.

### Onde posso obter suporte se tiver problemas?
Você pode obter suporte do [Fórum de Suporte Aspose.Words](https://forum.aspose.com/c/words/8).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}