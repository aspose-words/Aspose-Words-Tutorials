---
title: Definir fontes, pastas, sistema e pasta personalizada
linktitle: Definir fontes, pastas, sistema e pasta personalizada
second_title: API de processamento de documentos Aspose.Words
description: Aprenda a definir pastas de fontes personalizadas e do sistema em documentos do Word usando o Aspose.Words para .NET, garantindo que seus documentos sejam exibidos corretamente em diferentes ambientes.
weight: 10
url: /pt/net/working-with-fonts/set-fonts-folders-system-and-custom-folder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Definir fontes, pastas, sistema e pasta personalizada

## Introdução

Imagine que você está criando um documento com um estilo de fonte exclusivo, apenas para descobrir que as fontes não são exibidas corretamente em outra máquina. Frustrante, certo? É aqui que a configuração de pastas de fontes entra em jogo. Com o Aspose.Words para .NET, você pode definir pastas de fontes personalizadas e do sistema para garantir que seus documentos sempre tenham a aparência pretendida. Vamos mergulhar em como você pode conseguir isso.

## Pré-requisitos

Antes de começar, certifique-se de ter o seguinte:

-  Biblioteca Aspose.Words para .NET: Se você ainda não fez, baixe-a[aqui](https://releases.aspose.com/words/net/).
- Ambiente de desenvolvimento: Um IDE como o Visual Studio.
- Conhecimento básico de C#: A familiaridade com C# ajudará você a acompanhar os exemplos de código.

## Importar namespaces

Primeiro, importe os namespaces necessários no seu projeto:

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Agora, vamos dividir o processo em etapas simples.

## Etapa 1: Carregue o documento

 Para começar, carregue seu documento do Word em um Aspose.Words`Document` objeto. Este documento será aquele onde você deseja definir as pastas de fontes.

```csharp
// Caminho para o diretório do seu documento
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Rendering.docx");
```

## Etapa 2: inicializar as configurações de fonte

 Crie uma nova instância de`FontSettings`. Este objeto permitirá que você gerencie fontes de fontes.

```csharp
FontSettings fontSettings = new FontSettings();
```

## Etapa 3: recuperar fontes de fontes do sistema

Recuperar as fontes de fonte do sistema padrão. Em uma máquina Windows, isso normalmente inclui o "Windows\Fonts\" diretório.

```csharp
List<FontSourceBase> fontSources = new List<FontSourceBase>(fontSettings.GetFontsSources());
```

## Etapa 4: adicione uma pasta de fontes personalizada

Adicione uma pasta personalizada que contenha suas fontes adicionais. Isso é útil se você tiver fontes específicas não instaladas no diretório de fontes do sistema.

```csharp
FolderFontSource folderFontSource = new FolderFontSource("C:\\MyFonts\\", true);
fontSources.Add(folderFontSource);
```

## Etapa 5: Atualizar fontes de fonte

 Converta a lista de fontes de volta para uma matriz e defina-a como`FontSettings` objeto.

```csharp
FontSourceBase[] updatedFontSources = fontSources.ToArray();
fontSettings.SetFontsSources(updatedFontSources);
```

## Etapa 6: aplicar configurações de fonte ao documento

 Por fim, aplique o configurado`FontSettings` para o seu documento e salve-o no formato desejado, como PDF.

```csharp
doc.FontSettings = fontSettings;
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersSystemAndCustomFolder.pdf");
```

## Conclusão

aí está! Seguindo essas etapas, você pode garantir que seus documentos do Word usem as fontes corretas, sejam elas fontes do sistema ou personalizadas armazenadas em um diretório específico. Essa configuração ajuda a manter a integridade da aparência do seu documento em diferentes ambientes.

## Perguntas frequentes

### O que acontece se uma fonte estiver faltando nas pastas do sistema e personalizadas?

O Aspose.Words usará uma fonte padrão para substituir a fonte ausente, garantindo que o documento permaneça legível.

### Posso adicionar várias pastas de fontes personalizadas?

 Sim, você pode adicionar várias pastas de fontes personalizadas repetindo o processo de criação`FolderFontSource` objetos e adicioná-los à lista de fontes de fontes.

### É possível usar caminhos de rede para pastas de fontes personalizadas?

 Sim, você pode especificar um caminho de rede no`FolderFontSource` construtor.

### Quais formatos de arquivo o Aspose.Words suporta para salvar documentos?

O Aspose.Words suporta vários formatos, incluindo DOCX, PDF, HTML e muito mais.

### Como lidar com notificações de substituição de fonte?

 Você pode manipular notificações de substituição de fonte usando o`FontSettings` classe`FontSubstitutionWarning`evento.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
