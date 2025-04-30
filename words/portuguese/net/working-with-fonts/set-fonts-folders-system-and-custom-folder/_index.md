---
"description": "Aprenda a definir pastas de fontes personalizadas e do sistema em documentos do Word usando o Aspose.Words para .NET, garantindo que seus documentos sejam exibidos corretamente em diferentes ambientes."
"linktitle": "Definir fontes, pastas, sistema e pasta personalizada"
"second_title": "API de processamento de documentos Aspose.Words"
"title": "Definir fontes, pastas, sistema e pasta personalizada"
"url": "/pt/net/working-with-fonts/set-fonts-folders-system-and-custom-folder/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Definir fontes, pastas, sistema e pasta personalizada

## Introdução

Imagine que você está criando um documento com um estilo de fonte exclusivo e descobre que as fontes não são exibidas corretamente em outra máquina. Frustrante, não é? É aí que entra a configuração de pastas de fontes. Com o Aspose.Words para .NET, você pode definir pastas de fontes do sistema e personalizadas para garantir que seus documentos sempre tenham a aparência desejada. Vamos ver como você pode fazer isso.

## Pré-requisitos

Antes de começar, certifique-se de ter o seguinte:

- Biblioteca Aspose.Words para .NET: Se você ainda não fez o download, faça o download [aqui](https://releases.aspose.com/words/net/).
- Ambiente de desenvolvimento: um IDE como o Visual Studio.
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

Para começar, carregue seu documento do Word em um Aspose.Words `Document` objeto. Este será o documento onde você desejará definir as pastas de fontes.

```csharp
// Caminho para o diretório do seu documento
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Rendering.docx");
```

## Etapa 2: inicializar as configurações de fonte

Crie uma nova instância de `FontSettings`. Este objeto permitirá que você gerencie fontes.

```csharp
FontSettings fontSettings = new FontSettings();
```

## Etapa 3: recuperar fontes de fontes do sistema

Recupere as fontes padrão do sistema. Em uma máquina Windows, isso normalmente inclui o diretório "Windows\Fonts".

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

Converta a lista de fontes de volta para uma matriz e defina-a como `FontSettings` objeto.

```csharp
FontSourceBase[] updatedFontSources = fontSources.ToArray();
fontSettings.SetFontsSources(updatedFontSources);
```

## Etapa 6: aplicar configurações de fonte ao documento

Por fim, aplique o configurado `FontSettings` para o seu documento e salve-o no formato desejado, como PDF.

```csharp
doc.FontSettings = fontSettings;
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersSystemAndCustomFolder.pdf");
```

## Conclusão

Pronto! Seguindo esses passos, você garante que seus documentos do Word usem as fontes corretas, sejam elas do sistema ou personalizadas, armazenadas em um diretório específico. Essa configuração ajuda a manter a integridade da aparência do seu documento em diferentes ambientes.

## Perguntas frequentes

### O que acontece se uma fonte estiver faltando nas pastas do sistema e personalizadas?

O Aspose.Words usará uma fonte padrão para substituir a fonte ausente, garantindo que o documento permaneça legível.

### Posso adicionar várias pastas de fontes personalizadas?

Sim, você pode adicionar várias pastas de fontes personalizadas repetindo o processo de criação `FolderFontSource` objetos e adicioná-los à lista de fontes de fontes.

### É possível usar caminhos de rede para pastas de fontes personalizadas?

Sim, você pode especificar um caminho de rede no `FolderFontSource` construtor.

### Quais formatos de arquivo o Aspose.Words suporta para salvar documentos?

Aspose.Words suporta vários formatos, incluindo DOCX, PDF, HTML e muito mais.

### Como lidar com notificações de substituição de fonte?

Você pode manipular notificações de substituição de fonte usando o `FontSettings` classe `FontSubstitutionWarning` evento.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}