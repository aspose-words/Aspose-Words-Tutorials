---
"description": "Aprenda a exportar fontes como Base64 usando o Aspose.Words para .NET neste tutorial detalhado. Garanta que as fontes sejam incorporadas e exibidas corretamente em arquivos HTML."
"linktitle": "Exportar fontes como Base 64"
"second_title": "API de processamento de documentos Aspose.Words"
"title": "Exportar fontes como Base 64"
"url": "/pt/net/programming-with-htmlsaveoptions/export-fonts-as-base-64/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Exportar fontes como Base 64

## Introdução

Quando se trata de manipular documentos do Word programaticamente, o Aspose.Words para .NET é um recurso poderoso. Um de seus recursos interessantes é a exportação de fontes como Base64 em arquivos HTML, garantindo que as fontes sejam incorporadas e exibidas corretamente em diferentes navegadores e sistemas. Neste tutorial, veremos como você pode fazer isso. Pronto para tornar as fontes do seu documento do Word compatíveis com a web? Vamos começar!

## Pré-requisitos

Antes de começarmos a codificação, vamos garantir que você tenha tudo o que precisa:

- Biblioteca Aspose.Words para .NET: Você pode baixá-la do [Lançamentos Aspose](https://releases.aspose.com/words/net/) página.
- Ambiente de desenvolvimento .NET: qualquer IDE como o Visual Studio funcionará perfeitamente.
- Conhecimento básico de C#: você não precisa ser um profissional, mas um conhecimento básico ajudará.

## Importar namespaces

Para usar o Aspose.Words para .NET, você precisará importar os namespaces necessários no seu código C#. Isso torna todas as classes e métodos disponíveis para uso.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Etapa 1: Configure seu projeto

Primeiro, vamos configurar seu projeto e instalar a biblioteca Aspose.Words.

### 1.1 Criar um novo projeto

Abra o Visual Studio e crie um novo projeto de Aplicativo de Console. Dê a ele um nome significativo, como "ExportFontsBase64".

### 1.2 Instalar Aspose.Words

Você pode instalar o Aspose.Words para .NET por meio do Gerenciador de Pacotes NuGet:

1. Clique com o botão direito do mouse no seu projeto no Solution Explorer.
2. Selecione "Gerenciar pacotes NuGet".
3. Procure por "Aspose.Words" e instale-o.

Como alternativa, você pode executar o seguinte comando no Console do Gerenciador de Pacotes:

```sh
Install-Package Aspose.Words
```

## Etapa 2: carregue seu documento do Word

Agora que seu projeto está configurado, vamos carregar o documento do Word do qual você deseja exportar as fontes.

### 2.1 Definir o Diretório de Documentos

Primeiro, defina o diretório onde seu documento do Word está localizado:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Substituir `"YOUR DOCUMENT DIRECTORY"` com o caminho real para o diretório do seu documento.

### 2.2 Carregar o documento

Em seguida, carregue seu documento usando o `Document` aula:

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

Certifique-se de que "Rendering.docx" esteja no diretório especificado.

## Etapa 3: Configurar opções de salvamento de HTML

Para exportar fontes como Base64, precisamos configurar o `HtmlSaveOptions`.


Crie uma instância de `HtmlSaveOptions` e definir o `ExportFontsAsBase64` propriedade para `true`:

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions { ExportFontsAsBase64 = true };
```

## Etapa 4: Salve o documento como HTML

Por fim, vamos salvar o documento com as opções configuradas.


Use o `Save` método do `Document` classe para salvar seu documento:

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ExportFontsAsBase64.html", saveOptions);
```

Esta linha salvará seu documento como um arquivo HTML com fontes exportadas como Base64, garantindo que elas sejam incorporadas ao HTML.

## Conclusão

Parabéns! Você exportou com sucesso fontes como Base64 de um documento do Word usando o Aspose.Words para .NET. Isso garante que suas fontes sejam preservadas e exibidas corretamente em diferentes plataformas. Seja preparando documentos para exibição na web ou simplesmente garantindo compatibilidade, esse recurso é extremamente útil.

## Perguntas frequentes

### O que é codificação Base64?
Base64 é um método de codificação de dados binários (como fontes) em um formato de texto. Isso garante compatibilidade com formatos baseados em texto, como HTML.

### Por que devo usar Base64 para fontes em HTML?
Usar Base64 garante que as fontes sejam incorporadas diretamente no HTML, evitando problemas com arquivos de fonte ausentes e garantindo uma exibição consistente.

### Posso usar esse método para outros recursos, como imagens?
Com certeza! O Aspose.Words para .NET permite que você incorpore vários recursos, incluindo imagens, como Base64 em seus arquivos HTML.

### E se meu documento tiver várias fontes?
Sem problemas! O Aspose.Words para .NET incorporará todas as fontes usadas no seu documento como Base64 no arquivo HTML resultante.

### O Aspose.Words para .NET é gratuito?
Aspose.Words para .NET é uma biblioteca comercial. No entanto, você pode baixar uma versão de avaliação gratuita em [Lançamentos Aspose](https://releases.aspose.com/) página.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}