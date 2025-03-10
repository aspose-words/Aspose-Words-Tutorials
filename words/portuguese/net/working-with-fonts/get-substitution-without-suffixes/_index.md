---
title: Obtenha Substituição Sem Sufixos
linktitle: Obtenha Substituição Sem Sufixos
second_title: API de processamento de documentos Aspose.Words
description: Aprenda a gerenciar a substituição de fontes sem sufixos no Aspose.Words para .NET. Siga nosso guia passo a passo para garantir que seus documentos tenham uma aparência perfeita sempre.
weight: 10
url: /pt/net/working-with-fonts/get-substitution-without-suffixes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Obtenha Substituição Sem Sufixos

## Introdução

Bem-vindo a este guia abrangente sobre como gerenciar a substituição de fontes usando o Aspose.Words para .NET. Se você já teve problemas com fontes que não apareciam corretamente em seus documentos, você veio ao lugar certo. Este tutorial o levará por um processo passo a passo para lidar com a substituição de fontes sem sufixos de forma eficiente.

## Pré-requisitos

Antes de mergulhar no tutorial, certifique-se de ter o seguinte:

- Conhecimento básico de C#: entender a programação em C# tornará mais fácil seguir e implementar as etapas.
-  Biblioteca Aspose.Words para .NET: Baixe e instale a biblioteca do[link para download](https://releases.aspose.com/words/net/).
- Ambiente de desenvolvimento: configure um ambiente de desenvolvimento como o Visual Studio para escrever e executar seu código.
-  Documento de amostra: Um documento de amostra (por exemplo,`Rendering.docx`) para trabalhar durante este tutorial.

## Importar namespaces

Primeiro, precisamos importar os namespaces necessários para acessar as classes e métodos fornecidos pelo Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System.Collections.Generic;
```

## Etapa 1: Defina o diretório do documento

Para começar, especifique o diretório onde seu documento está localizado. Isso ajuda a localizar o documento no qual você quer trabalhar.

```csharp
// Caminho para o diretório do seu documento
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Etapa 2: Configurar o manipulador de aviso de substituição

Em seguida, precisamos configurar um manipulador de avisos que nos notificará sempre que uma substituição de fonte ocorrer durante o processamento do documento. Isso é crucial para capturar e lidar com quaisquer problemas de fonte.

```csharp
DocumentSubstitutionWarnings substitutionWarningHandler = new DocumentSubstitutionWarnings();
Document doc = new Document(dataDir + "Rendering.docx");
doc.WarningCallback = substitutionWarningHandler;
```

## Etapa 3: Adicionar fontes de fontes personalizadas

Nesta etapa, adicionaremos fontes de fontes personalizadas para garantir que o Aspose.Words possa localizar e usar as fontes corretas. Isso é particularmente útil se você tiver fontes específicas armazenadas em diretórios personalizados.

```csharp
List<FontSourceBase> fontSources = new List<FontSourceBase>(FontSettings.DefaultInstance.GetFontsSources());

FolderFontSource folderFontSource = new FolderFontSource("C:\\MyFonts\\", true);
fontSources.Add(folderFontSource);

FontSourceBase[] updatedFontSources = fontSources.ToArray();
FontSettings.DefaultInstance.SetFontsSources(updatedFontSources);
```

Neste código:
-  Recuperamos as fontes de fonte atuais e adicionamos uma nova`FolderFontSource` apontando para nosso diretório de fontes personalizadas (`C:\\MyFonts\\`).
- Em seguida, atualizamos as fontes de fontes com essa nova lista.

## Etapa 4: Salve o documento

Por fim, salve o documento após aplicar as configurações de substituição de fonte. Para este tutorial, salvaremos como PDF.

```csharp
doc.Save(dataDir + "WorkingWithFonts.GetSubstitutionWithoutSuffixes.pdf");
```

## Etapa 5: Crie a classe do manipulador de avisos

 Para lidar com avisos de forma eficaz, crie uma classe personalizada que implemente o`IWarningCallback` interface. Esta classe irá capturar e registrar quaisquer avisos de substituição de fonte.

```csharp
public class DocumentSubstitutionWarnings : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
            FontWarnings.Warning(info);
    }

    public WarningInfoCollection FontWarnings = new WarningInfoCollection();
}
```

Nesta aula:
-  O`Warning` método captura avisos relacionados à substituição de fontes.
-  O`FontWarnings` a coleção armazena esses avisos para inspeção ou registro posterior.

## Conclusão

Agora você domina o processo de lidar com substituição de fontes sem sufixos usando o Aspose.Words para .NET. Esse conhecimento garantirá que seus documentos mantenham a aparência pretendida, independentemente das fontes disponíveis no sistema. Continue experimentando diferentes configurações e fontes para aproveitar totalmente o poder do Aspose.Words.

## Perguntas frequentes

### Como posso usar fontes de vários diretórios personalizados?

 Você pode adicionar vários`FolderFontSource` instâncias para o`fontSources` liste e atualize as fontes de acordo.

### Onde posso baixar uma versão de avaliação gratuita do Aspose.Words para .NET?

 Você pode baixar uma versão de avaliação gratuita em[Página de teste gratuito do Aspose](https://releases.aspose.com/).

###  Posso lidar com vários tipos de avisos usando`IWarningCallback`?

 Sim, o`IWarningCallback` A interface permite que você lide com vários tipos de avisos, não apenas com a substituição de fontes.

### Onde posso obter suporte para o Aspose.Words?

 Para obter suporte, visite o[Fórum de suporte Aspose.Words](https://forum.aspose.com/c/words/8).

### É possível comprar uma licença temporária?

 Sim, você pode obter uma licença temporária do[página de licença temporária](https://purchase.aspose.com/temporary-license/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
