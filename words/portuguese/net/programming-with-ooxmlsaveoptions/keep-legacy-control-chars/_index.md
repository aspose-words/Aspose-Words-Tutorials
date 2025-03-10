---
title: Manter os caracteres de controle legados
linktitle: Manter os caracteres de controle legados
second_title: API de processamento de documentos Aspose.Words
description: Aprenda como preservar caracteres de controle legados em documentos do Word usando o Aspose.Words para .NET com este guia passo a passo.
weight: 10
url: /pt/net/programming-with-ooxmlsaveoptions/keep-legacy-control-chars/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Manter os caracteres de controle legados

## Introdução

Já ficou intrigado com aqueles caracteres de controle estranhos e invisíveis em seus documentos do Word? Eles são como pequenos gremlins ocultos que podem atrapalhar a formatação e a funcionalidade. Felizmente, o Aspose.Words para .NET fornece um recurso útil para manter esses caracteres de controle legados intactos ao salvar documentos. Neste tutorial, vamos nos aprofundar em como gerenciar esses caracteres de controle usando o Aspose.Words para .NET. Vamos detalhar passo a passo, garantindo que você entenda cada detalhe ao longo do caminho. Pronto para começar? Vamos mergulhar!

## Pré-requisitos

Antes de começar, certifique-se de ter o seguinte:

1.  Aspose.Words para .NET: Baixe e instale em[aqui](https://releases.aspose.com/words/net/).
2.  Uma licença Aspose válida: Você pode obter uma licença temporária[aqui](https://purchase.aspose.com/temporary-license/).
3. Ambiente de desenvolvimento: Visual Studio ou qualquer outro IDE que suporte .NET.
4. Conhecimento básico de C#: Familiaridade com a linguagem de programação C# será útil.

## Importar namespaces

Antes de escrever seu código, você precisa importar os namespaces necessários. Adicione as seguintes linhas ao topo do seu arquivo C#:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Etapa 1: Configurando seu projeto

Primeiro, você precisará configurar seu projeto no Visual Studio (ou seu IDE preferido). 

1. Crie um novo projeto C#: Abra o Visual Studio e crie um novo projeto de aplicativo de console C#.
2. Instalar o Aspose.Words para .NET: Use o NuGet Package Manager para instalar o Aspose.Words para .NET. Clique com o botão direito do mouse no seu projeto no Solution Explorer, selecione "Manage NuGet Packages", pesquise por "Aspose.Words" e instale-o.

## Etapa 2: Carregue seu documento

Em seguida, você carregará o documento do Word que contém os caracteres de controle herdados.

1. Especifique o caminho do documento: Defina o caminho para o diretório do seu documento.
   
   ```csharp
   string dataDir = "YOUR DOCUMENT DIRECTORY";
   ```

2.  Carregue o documento: Use o`Document` classe para carregar seu documento.

   ```csharp
   Document doc = new Document(dataDir + "Legacy control character.doc");
   ```

## Etapa 3: Configurar opções de salvamento

Agora, vamos configurar as opções de salvamento para manter os caracteres de controle legados intactos.

1.  Criar opções de salvamento: inicializar uma instância de`OoxmlSaveOptions` e definir o`KeepLegacyControlChars`propriedade para`true`.

   ```csharp
   OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(SaveFormat.FlatOpc)
   {
       KeepLegacyControlChars = true
   };
   ```

## Etapa 4: Salve o documento

Por fim, salve o documento com as opções de salvamento configuradas.

1.  Salvar o documento: Use o`Save` método do`Document` classe para salvar o documento com as opções de salvamento especificadas.

   ```csharp
   doc.Save(dataDir + "WorkingWithOoxmlSaveOptions.KeepLegacyControlChars.docx", saveOptions);
   ```

## Conclusão

aí está! Seguindo essas etapas, você pode garantir que seus caracteres de controle legados sejam preservados ao trabalhar com documentos do Word no Aspose.Words para .NET. Esse recurso pode ser um salva-vidas, especialmente ao lidar com documentos complexos em que os caracteres de controle desempenham um papel crucial. 

## Perguntas frequentes

### O que são caracteres de controle legados?

Caracteres de controle legados são caracteres não imprimíveis usados em documentos mais antigos para controlar a formatação e o layout.

### Posso remover esses caracteres de controle em vez de mantê-los?

Sim, você pode usar o Aspose.Words for .NET para remover ou substituir esses caracteres, se necessário.

### Este recurso está disponível em todas as versões do Aspose.Words para .NET?

Este recurso está disponível em versões recentes. Certifique-se de usar a versão mais recente para acessar todas as funcionalidades.

### Preciso de uma licença para usar o Aspose.Words para .NET?

 Sim, você precisa de uma licença válida. Você pode obter uma licença temporária para fins de avaliação[aqui](https://purchase.aspose.com/temporary-license/).

### Onde posso encontrar mais documentação sobre o Aspose.Words para .NET?

 Você pode encontrar documentação detalhada[aqui](https://reference.aspose.com/words/net/).
 
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
