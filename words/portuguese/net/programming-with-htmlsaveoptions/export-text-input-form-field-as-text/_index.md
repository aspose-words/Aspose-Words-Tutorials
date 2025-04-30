---
"description": "Aprenda como exportar campos de formulário de entrada de texto como texto simples usando o Aspose.Words para .NET com este guia passo a passo abrangente."
"linktitle": "Exportar campo de formulário de entrada de texto como texto"
"second_title": "API de processamento de documentos Aspose.Words"
"title": "Exportar campo de formulário de entrada de texto como texto"
"url": "/pt/net/programming-with-htmlsaveoptions/export-text-input-form-field-as-text/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Exportar campo de formulário de entrada de texto como texto

## Introdução

Então, você está mergulhando no mundo do Aspose.Words para .NET? Ótima escolha! Se você quer aprender a exportar um campo de formulário de entrada de texto como texto, está no lugar certo. Seja você iniciante ou aprimorando suas habilidades, este guia explicará tudo o que você precisa saber. Vamos começar?

## Pré-requisitos

Antes de começarmos, vamos garantir que você tenha tudo o que precisa para seguir em frente sem problemas:

- Aspose.Words para .NET: Baixe e instale a versão mais recente de [aqui](https://releases.aspose.com/words/net/).
- IDE: Visual Studio ou qualquer ambiente de desenvolvimento C#.
- Conhecimento básico de C#: compreensão da sintaxe básica de C# e conceitos de programação orientada a objetos.
- Documento: Um documento Word de exemplo (`Rendering.docx`) com campos de formulário de entrada de texto.

## Importar namespaces

Antes de mais nada, você precisa importar os namespaces necessários. Eles são como os blocos de construção que fazem tudo funcionar perfeitamente.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;
```

Certo, agora que nossos namespaces estão prontos, vamos à ação!

## Etapa 1: Configurar o projeto

Antes de entrarmos no código, vamos garantir que nosso projeto esteja configurado corretamente.

## Criando o Projeto

1. Abra o Visual Studio: comece abrindo o Visual Studio ou seu ambiente de desenvolvimento C# preferido.
2. Criar um novo projeto: Navegue até `File > New > Project`Selecione `Console App (.NET Core)` ou qualquer outro tipo de projeto relevante.
3. Dê um nome ao seu projeto: Dê ao seu projeto um nome significativo, algo como `AsposeWordsExportExample`.

## Adicionando Aspose.Words

1. Gerenciar pacotes NuGet: clique com o botão direito do mouse no seu projeto no Solution Explorer e selecione `Manage NuGet Packages`.
2. Pesquise por Aspose.Words: No Gerenciador de Pacotes NuGet, pesquise por `Aspose.Words`.
3. Instalar Aspose.Words: Clique em `Install` para adicionar a biblioteca Aspose.Words ao seu projeto.

## Etapa 2: Carregue o documento do Word

Agora que nosso projeto está configurado, vamos carregar o documento do Word que contém os campos do formulário de entrada de texto.

1. Especifique o diretório do documento: defina o caminho para o diretório onde seu documento está armazenado.
2. Carregar o documento: Use o `Document` classe para carregar seu documento do Word.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

## Etapa 3: preparar o diretório de exportação

Antes de exportar, vamos garantir que nosso diretório de exportação esteja pronto. É lá que nosso arquivo HTML e imagens serão salvos.

1. Definir o diretório de exportação: especifique o caminho onde os arquivos exportados serão salvos.
2. Verifique e limpe o diretório: certifique-se de que o diretório existe e está vazio.

```csharp
string imagesDir = Path.Combine(dataDir, "Images");

if (Directory.Exists(imagesDir))
    Directory.Delete(imagesDir, true);

Directory.CreateDirectory(imagesDir);
```

## Etapa 4: Configurar opções de salvamento

É aqui que a mágica acontece. Precisamos configurar nossas opções de salvamento para exportar o campo de entrada de texto do formulário como texto simples.

1. Criar opções de salvamento: Inicializar um novo `HtmlSaveOptions` objeto.
2. Definir opção de exportação de texto: Configurar o `ExportTextInputFormFieldAsText` propriedade para `true`.
3. Definir pasta de imagens: defina a pasta onde as imagens serão salvas.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.Html)
{
    ExportTextInputFormFieldAsText = true,
    ImagesFolder = imagesDir
};
```

## Etapa 5: Salve o documento como HTML

Por fim, vamos salvar o documento do Word como um arquivo HTML usando nossas opções de salvamento configuradas.

1. Definir o caminho de saída: especifique o caminho onde o arquivo HTML será salvo.
2. Salvar o documento: Use o `Save` método do `Document` classe para exportar o documento.

```csharp
doc.Save(dataDir + "ExportedDocument.html", saveOptions);
```

## Conclusão

pronto! Você exportou com sucesso um campo de formulário de entrada de texto como texto simples usando o Aspose.Words para .NET. Este guia deve ter lhe dado uma abordagem clara e passo a passo para realizar essa tarefa. Lembre-se: a prática leva à perfeição, então continue experimentando diferentes opções e configurações para ver o que mais você pode fazer com o Aspose.Words.

## Perguntas frequentes

### Posso exportar outros tipos de campos de formulário usando o mesmo método?

Sim, você pode exportar outros tipos de campos de formulário configurando diferentes propriedades do `HtmlSaveOptions` aula.

### E se meu documento tiver imagens?

As imagens serão salvas na pasta de imagens especificada. Certifique-se de definir o `ImagesFolder` propriedade no `HtmlSaveOptions`.

### Preciso de uma licença para o Aspose.Words?

Sim, você pode obter um teste gratuito [aqui](https://releases.aspose.com/) ou comprar uma licença [aqui](https://purchase.aspose.com/buy).

### Posso personalizar o HTML exportado?

Com certeza! O Aspose.Words oferece várias opções para personalizar a saída HTML. Consulte o [documentação](https://reference.aspose.com/words/net/) para mais detalhes.

### O Aspose.Words é compatível com o .NET Core?

Sim, o Aspose.Words é compatível com .NET Core, .NET Framework e outras plataformas .NET.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}