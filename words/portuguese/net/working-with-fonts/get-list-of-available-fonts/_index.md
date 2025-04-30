---
"description": "Descubra como obter uma lista de fontes disponíveis usando o Aspose.Words para .NET neste tutorial passo a passo detalhado. Aprimore suas habilidades de gerenciamento de fontes."
"linktitle": "Obtenha a lista de fontes disponíveis"
"second_title": "API de processamento de documentos Aspose.Words"
"title": "Obtenha a lista de fontes disponíveis"
"url": "/pt/net/working-with-fonts/get-list-of-available-fonts/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Obtenha a lista de fontes disponíveis

## Introdução

Já teve dificuldades para gerenciar fontes em seus documentos do Word? Se você é um desenvolvedor .NET, o Aspose.Words para .NET está aqui para te ajudar! Esta poderosa biblioteca não só ajuda você a criar e manipular documentos do Word programaticamente, como também oferece amplos recursos de gerenciamento de fontes. Neste guia, mostraremos passo a passo como obter uma lista de fontes disponíveis usando o Aspose.Words para .NET. Dividiremos o tutorial em etapas fáceis de entender para garantir que você possa acompanhar com facilidade. Então, vamos começar e tornar o gerenciamento de fontes muito mais fácil!

## Pré-requisitos

Antes de começar, você precisa de algumas coisas:

- Aspose.Words para .NET: Certifique-se de ter a biblioteca Aspose.Words para .NET instalada. Você pode baixá-la em [aqui](https://releases.aspose.com/words/net/).
- Visual Studio: Este exemplo usa o Visual Studio como ambiente de desenvolvimento.
- .NET Framework: certifique-se de ter o .NET Framework instalado na sua máquina.
- Diretório de documentos: um caminho de diretório onde seus documentos são armazenados.

## Importar namespaces

Primeiro, importe os namespaces necessários para o seu projeto:

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;
```

## Etapa 1: inicializar as configurações de fonte

O primeiro passo é inicializar as configurações de fonte. Isso permitirá que você gerencie as fontes dos seus documentos.

```csharp
FontSettings fontSettings = new FontSettings();
List<FontSourceBase> fontSources = new List<FontSourceBase>(fontSettings.GetFontsSources());
```

- FontSettings: Esta classe é usada para especificar as configurações de substituição de fontes e fontes.
- fontSources: Criamos uma lista de fontes existentes a partir das configurações de fonte atuais.

## Etapa 2: Definir diretório de documentos

Em seguida, especifique o caminho para o diretório do seu documento. É lá que o Aspose.Words buscará fontes.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

- dataDir: Esta variável de string contém o caminho para o diretório onde suas fontes estão localizadas. Substituir `"YOUR DOCUMENT DIRECTORY"` com o caminho real.

## Etapa 3: Adicionar pasta de fontes personalizadas

Agora, adicione uma nova pasta source para instruir o Aspose.Words a pesquisar fontes nessa pasta.

```csharp
FolderFontSource folderFontSource = new FolderFontSource(dataDir, true);
```

- FolderFontSource: Esta classe representa uma fonte de pasta. O segundo parâmetro (`true`indica se as fontes devem ser pesquisadas recursivamente em subpastas.

## Etapa 4: Atualizar fontes de fonte

Adicione a pasta de fontes personalizadas à lista de fontes existentes e atualize as configurações de fonte.

```csharp
fontSources.Add(folderFontSource);
FontSourceBase[] updatedFontSources = fontSources.ToArray();
```

- fontSources.Add(folderFontSource): Adiciona a pasta de fontes personalizadas às fontes de fontes existentes.
- updatedFontSources: Converte a lista de fontes de fontes em uma matriz.

## Etapa 5: recuperar e exibir fontes

Por fim, recupere as fontes disponíveis e exiba seus detalhes.

```csharp
foreach (PhysicalFontInfo fontInfo in updatedFontSources[0].GetAvailableFonts())
{
    Console.WriteLine("FontFamilyName : " + fontInfo.FontFamilyName);
    Console.WriteLine("FullFontName  : " + fontInfo.FullFontName);
    Console.WriteLine("Version  : " + fontInfo.Version);
    Console.WriteLine("FilePath : " + fontInfo.FilePath);
}
```

- GetAvailableFonts(): recupera a lista de fontes disponíveis da primeira fonte na lista atualizada.
- fontInfo: Uma instância de `PhysicalFontInfo` contendo detalhes sobre cada fonte.

## Conclusão

Parabéns! Você recuperou com sucesso uma lista de fontes disponíveis usando o Aspose.Words para .NET. Este tutorial o guiou por cada etapa, desde a inicialização das configurações de fonte até a exibição dos detalhes da fonte. Com esse conhecimento, agora você pode gerenciar fontes em seus documentos do Word com facilidade. Lembre-se: o Aspose.Words para .NET é uma ferramenta poderosa que pode aprimorar significativamente suas capacidades de processamento de documentos. Então, vá em frente e explore mais recursos para tornar seu processo de desenvolvimento ainda mais eficiente.

## Perguntas frequentes

### Posso usar o Aspose.Words para .NET com outras estruturas .NET?
Sim, o Aspose.Words para .NET é compatível com vários frameworks .NET, incluindo .NET Core e .NET 5+.

### Como instalo o Aspose.Words para .NET?
Você pode instalá-lo por meio do Gerenciador de Pacotes NuGet no Visual Studio pesquisando por "Aspose.Words".

### É possível adicionar várias pastas de fontes personalizadas?
Sim, você pode adicionar várias pastas de fontes personalizadas criando várias `FolderFontSource` instâncias e adicioná-las à lista de fontes de fontes.

### Posso recuperar detalhes de uma fonte específica?
Sim, você pode recuperar detalhes da fonte de qualquer fonte especificando o índice da fonte no `updatedFontSources` variedade.

### O Aspose.Words para .NET suporta substituição de fontes?
Sim, ele suporta substituição de fonte para garantir que o texto seja renderizado corretamente, mesmo que a fonte original não esteja disponível.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}