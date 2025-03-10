---
title: Definir posição horizontal ou vertical relativa
linktitle: Definir posição horizontal ou vertical relativa
second_title: API de processamento de documentos Aspose.Words
description: Aprenda a definir posições horizontais e verticais relativas para tabelas em documentos do Word usando o Aspose.Words para .NET com este guia passo a passo.
weight: 10
url: /pt/net/programming-with-tables/set-relative-horizontal-or-vertical-position/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Definir posição horizontal ou vertical relativa

## Introdução

Já se sentiu preso em como posicionar tabelas exatamente do jeito que você quer em seus documentos do Word? Bem, você não está sozinho. Não importa se você está criando um relatório profissional ou um folheto estiloso, alinhar tabelas pode fazer uma grande diferença. É aí que o Aspose.Words para .NET é útil. Este tutorial irá guiá-lo passo a passo sobre como definir posições horizontais ou verticais relativas para tabelas em seus documentos do Word. Vamos lá!

## Pré-requisitos

Antes de começar, certifique-se de ter o seguinte:

1.  Aspose.Words para .NET: Se você ainda não fez isso, você pode baixá-lo[aqui](https://releases.aspose.com/words/net/).
2. Ambiente de desenvolvimento: Visual Studio ou qualquer outro IDE compatível com .NET.
3. Conhecimento básico de C#: Este tutorial pressupõe que você esteja familiarizado com os conceitos básicos de programação em C#.

## Importar namespaces

Primeiramente, você precisa importar os namespaces necessários. Isso é essencial para acessar as funcionalidades do Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

## Etapa 1: carregue seu documento

Para começar, você precisará carregar seu documento do Word no programa. Veja como você pode fazer isso:

```csharp
// Caminho para o diretório do seu documento
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table wrapped by text.docx");
```

Este trecho de código configura o caminho para o diretório do seu documento e carrega o documento específico no qual você quer trabalhar. Certifique-se de que o caminho do seu documento esteja correto para evitar problemas de carregamento.

## Etapa 2: Acesse a tabela

Em seguida, precisamos acessar a tabela dentro do documento. Normalmente, você desejaria trabalhar com a primeira tabela na seção body.

```csharp
Table table = doc.FirstSection.Body.Tables[0];
```

Esta linha de código busca a primeira tabela do corpo do documento. Se seu documento tiver várias tabelas, você pode ajustar o índice de acordo.

## Etapa 3: Defina a posição horizontal

Agora, vamos definir a posição horizontal da tabela em relação a um elemento específico. Neste exemplo, vamos posicioná-la em relação à coluna.

```csharp
table.HorizontalAnchor = RelativeHorizontalPosition.Column;
```

 Ao definir o`HorizontalAnchor` para`RelativeHorizontalPosition.Column`, você está dizendo para a tabela se alinhar horizontalmente em relação à coluna em que ela reside.

## Etapa 4: Defina a posição vertical

Similar ao posicionamento horizontal, você também pode definir a posição vertical. Aqui, nós a posicionamos em relação à página.

```csharp
table.VerticalAnchor = RelativeVerticalPosition.Page;
```

 Definindo o`VerticalAnchor` para`RelativeVerticalPosition.Page` garante que a tabela esteja alinhada verticalmente de acordo com a página.

## Etapa 5: Salve seu documento

Por fim, salve suas alterações em um novo documento. Este é um passo crucial para garantir que suas alterações sejam preservadas.

```csharp
doc.Save(dataDir + "WorkingWithTables.SetFloatingTablePosition.docx");
```

Este comando salva o documento modificado com um novo nome, garantindo que você não substitua o arquivo original.

## Conclusão

E aí está! Você definiu com sucesso as posições horizontais e verticais relativas para uma tabela em um documento do Word usando o Aspose.Words para .NET. Com essa nova habilidade, você pode aprimorar o layout e a legibilidade dos seus documentos, fazendo com que pareçam mais profissionais e refinados. Continue experimentando diferentes posições e veja o que funciona melhor para suas necessidades.

## Perguntas frequentes

### Posso posicionar tabelas em relação a outros elementos?  
Sim, o Aspose.Words permite que você posicione tabelas em relação a vários elementos, como margens, páginas, colunas e muito mais.

### Preciso de uma licença para usar o Aspose.Words para .NET?  
 Sim, você pode comprar uma licença[aqui](https://purchase.aspose.com/buy) ou obter uma licença temporária[aqui](https://purchase.aspose.com/temporary-license/).

### Existe uma versão de avaliação gratuita disponível para o Aspose.Words para .NET?  
 Absolutamente! Você pode baixar uma versão de teste gratuita[aqui](https://releases.aspose.com/).

### Posso usar o Aspose.Words com outras linguagens de programação?  
O Aspose.Words foi projetado principalmente para .NET, mas há versões disponíveis para Java, Python e outras plataformas.

### Onde posso encontrar documentação mais detalhada?  
Para obter informações mais detalhadas, consulte a documentação do Aspose.Words[aqui](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
