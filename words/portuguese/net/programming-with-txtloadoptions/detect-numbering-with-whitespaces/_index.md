---
title: Detectar numeração com espaços em branco
linktitle: Detectar numeração com espaços em branco
second_title: API de processamento de documentos Aspose.Words
description: Descubra como usar o Aspose.Words para .NET para detectar numeração com espaços em branco em documentos de texto simples e garantir que suas listas sejam reconhecidas corretamente.
weight: 10
url: /pt/net/programming-with-txtloadoptions/detect-numbering-with-whitespaces/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Detectar numeração com espaços em branco

## Introdução

Aspose.Words para entusiastas do .NET! Hoje, estamos mergulhando em um recurso fascinante que pode tornar o manuseio de listas em documentos de texto simples uma brisa. Você já lidou com arquivos de texto onde algumas linhas deveriam ser listas, mas elas simplesmente não parecem corretas quando carregadas em um documento do Word? Bem, temos um truque bacana na manga: detectar numeração com espaços em branco. Este tutorial mostrará como usar o`DetectNumberingWithWhitespaces` opção no Aspose.Words para .NET para garantir que suas listas sejam reconhecidas corretamente, mesmo quando houver espaços em branco entre os números e o texto.

## Pré-requisitos

Antes de começar, certifique-se de ter o seguinte:

-  Aspose.Words para .NET: Você pode baixá-lo do[Lançamentos Aspose](https://releases.aspose.com/words/net/) página.
- Ambiente de desenvolvimento: Visual Studio ou qualquer outro IDE C#.
- .NET Framework instalado na sua máquina.
- Conhecimento básico de C#: entender os conceitos básicos ajudará você a acompanhar os exemplos.

## Importar namespaces

Antes de pular para o código, certifique-se de ter os namespaces necessários importados no seu projeto. Aqui está um snippet rápido para você começar:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;
```

Vamos dividir o processo em etapas simples e gerenciáveis. Cada etapa guiará você pelo código necessário e explicará o que está acontecendo.

## Etapa 1: Defina seu diretório de documentos

Primeiro, vamos configurar o caminho para o diretório do seu documento. É aqui que seus arquivos de entrada e saída serão armazenados.

```csharp
// Caminho para o diretório do seu documento
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Etapa 2: Crie um documento de texto simples

Em seguida, criaremos um documento de texto simples como uma string. Este documento conterá partes que podem ser interpretadas como listas.

```csharp
const string textDoc = "Full stop delimiters:\n" +
                       "1. First list item 1\n" +
                       "2. First list item 2\n" +
                       "3. First list item 3\n\n" +
                       "Right bracket delimiters:\n" +
                       "1) Second list item 1\n" +
                       "2) Second list item 2\n" +
                       "3) Second list item 3\n\n" +
                       "Bullet delimiters:\n" +
                       "• Third list item 1\n" +
                       "• Third list item 2\n" +
                       "• Third list item 3\n\n" +
                       "Whitespace delimiters:\n" +
                       "1 Fourth list item 1\n" +
                       "2 Fourth list item 2\n" +
                       "3 Fourth list item 3";
```

## Etapa 3: Configurar LoadOptions

 Para detectar numeração com espaços em branco, precisamos definir o`DetectNumberingWithWhitespaces` opção para`true` em um`TxtLoadOptions` objeto.

```csharp
TxtLoadOptions loadOptions = new TxtLoadOptions { DetectNumberingWithWhitespaces = true };
```

## Etapa 4: Carregue o documento

 Agora, vamos carregar o documento usando o`TxtLoadOptions` como um parâmetro. Isso garante que a quarta lista (com espaços em branco) seja detectada corretamente.

```csharp
Document doc = new Document(new MemoryStream(Encoding.UTF8.GetBytes(textDoc)), loadOptions);
```

## Etapa 5: Salve o documento

Por fim, salve o documento no diretório especificado. Isso produzirá um documento Word com listas detectadas corretamente.

```csharp
doc.Save(dataDir + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

## Conclusão

aí está! Com apenas algumas linhas de código, você dominou a arte de detectar numeração com espaços em branco em documentos de texto simples usando o Aspose.Words para .NET. Esse recurso pode ser incrivelmente útil ao lidar com vários formatos de texto e garantir que suas listas sejam representadas com precisão em seus documentos do Word. Então, da próxima vez que você encontrar essas listas complicadas, saberá exatamente o que fazer.

## Perguntas frequentes

###  O que é`DetectNumberingWithWhitespaces` in Aspose.Words for .NET?
`DetectNumberingWithWhitespaces` é uma opção em`TxtLoadOptions` que permite que o Aspose.Words reconheça listas mesmo quando há espaço em branco entre a numeração e o texto do item da lista.

### Posso usar esse recurso para outros delimitadores, como marcadores e colchetes?
 Sim, o Aspose.Words detecta automaticamente listas com delimitadores comuns, como marcadores e colchetes. O`DetectNumberingWithWhitespaces` ajuda especificamente com listas que possuem espaços em branco.

###  O que acontece se eu não usar`DetectNumberingWithWhitespaces`?
Sem essa opção, listas com espaços em branco entre a numeração e o texto podem não ser reconhecidas como listas, e os itens podem aparecer como parágrafos simples.

### Esse recurso está disponível em outros produtos Aspose?
Este recurso específico é personalizado para o Aspose.Words para .NET, projetado para lidar com o processamento de documentos do Word.

### Como posso obter uma licença temporária para o Aspose.Words para .NET?
 Você pode obter uma licença temporária no[Licença temporária Aspose](https://purchase.aspose.com/temporary-license/) página.


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
