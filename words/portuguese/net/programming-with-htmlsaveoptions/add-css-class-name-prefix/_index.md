---
"description": "Aprenda a adicionar um prefixo de nome de classe CSS ao salvar documentos do Word como HTML usando o Aspose.Words para .NET. Guia passo a passo, trechos de código e perguntas frequentes incluídos."
"linktitle": "Adicionar prefixo de nome de classe CSS"
"second_title": "API de processamento de documentos Aspose.Words"
"title": "Adicionar prefixo de nome de classe CSS"
"url": "/pt/net/programming-with-htmlsaveoptions/add-css-class-name-prefix/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Adicionar prefixo de nome de classe CSS

## Introdução

Bem-vindo! Se você está se aprofundando no mundo do Aspose.Words para .NET, vai se surpreender. Hoje, vamos explorar como adicionar um prefixo de nome de classe CSS ao salvar um documento do Word como HTML usando o Aspose.Words para .NET. Esse recurso é muito útil quando você quer evitar conflitos de nomes de classe em seus arquivos HTML.

## Pré-requisitos

Antes de começar, certifique-se de ter o seguinte:

- Aspose.Words para .NET: Se você ainda não o instalou, [baixe aqui](https://releases.aspose.com/words/net/).
- Ambiente de desenvolvimento: Visual Studio ou qualquer outro IDE C#.
- Um documento do Word: usaremos um documento chamado `Rendering.docx`. Coloque-o no diretório do seu projeto.

## Importar namespaces

Primeiro, certifique-se de ter os namespaces necessários importados para o seu projeto C#. Adicione-os no início do seu arquivo de código:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

Agora, vamos mergulhar no guia passo a passo!

## Etapa 1: Configure seu projeto

Antes de começarmos a adicionar um prefixo de nome de classe CSS, vamos configurar nosso projeto.

### Etapa 1.1: Criar um novo projeto

Abra o Visual Studio e crie um novo projeto de aplicativo de console. Dê a ele um nome chamativo, como `AsposeCssPrefixExample`.

### Etapa 1.2: Adicionar Aspose.Words para .NET

Se ainda não o fez, adicione o Aspose.Words para .NET ao seu projeto via NuGet. Basta abrir o Console do Gerenciador de Pacotes do NuGet e executar:

```bash
Install-Package Aspose.Words
```

Ótimo! Agora estamos prontos para começar a programar.

## Etapa 2: carregue seu documento

A primeira coisa que precisamos fazer é carregar o documento do Word que queremos converter para HTML.

### Etapa 2.1: Definir o caminho do documento

Configure o caminho para o diretório do seu documento. Para este tutorial, vamos supor que seu documento esteja em uma pasta chamada `Documents` dentro do diretório do seu projeto.

```csharp
string dataDir = @"C:\YourProject\Documents\";
```

### Etapa 2.2: Carregar o documento

Agora, vamos carregar o documento usando o Aspose.Words:

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Etapa 3: Configurar opções de salvamento de HTML

Em seguida, precisamos configurar as opções de salvamento de HTML para incluir um prefixo de nome de classe CSS.

### Etapa 3.1: Criar opções de salvamento em HTML

Instanciar o `HtmlSaveOptions` objeto e defina o tipo de folha de estilo CSS para `External`.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    CssStyleSheetType = CssStyleSheetType.External
};
```

### Etapa 3.2: Definir prefixo do nome da classe CSS

Agora, vamos definir o `CssClassNamePrefix` propriedade para o prefixo desejado. Para este exemplo, usaremos `"pfx_"`.

```csharp
saveOptions.CssClassNamePrefix = "pfx_";
```

## Etapa 4: Salve o documento como HTML

Por fim, vamos salvar o documento como um arquivo HTML com nossas opções configuradas.


Especifique o caminho do arquivo HTML de saída e salve o documento.

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
```

## Etapa 5: verificar a saída

Depois de executar seu projeto, navegue até seu `Documents` pasta. Você deve encontrar um arquivo HTML chamado `WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html`. Abra este arquivo em um editor de texto ou navegador para verificar se as classes CSS têm o prefixo `pfx_`.

## Conclusão

E pronto! Seguindo esses passos, você adicionou com sucesso um prefixo de nome de classe CSS à sua saída HTML usando o Aspose.Words para .NET. Este recurso simples, porém poderoso, pode ajudar você a manter estilos limpos e sem conflitos em seus documentos HTML.

## Perguntas frequentes

### Posso usar um prefixo diferente para cada operação de salvamento?
Sim, você pode personalizar o prefixo sempre que salvar um documento, alterando o `CssClassNamePrefix` propriedade.

### Este método suporta CSS embutido?
O `CssClassNamePrefix` A propriedade funciona com CSS externo. Para CSS embutido, você precisará de uma abordagem diferente.

### Como posso incluir outras opções de salvamento de HTML?
Você pode configurar várias propriedades de `HtmlSaveOptions` para personalizar sua saída HTML. Verifique o [documentação](https://reference.aspose.com/words/net/) para mais detalhes.

### É possível salvar o HTML em um fluxo?
Com certeza! Você pode salvar o documento em um fluxo passando o objeto de fluxo para o `Save` método.

### Como obtenho suporte se tiver problemas?
Você pode obter suporte do [Fórum Aspose](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}