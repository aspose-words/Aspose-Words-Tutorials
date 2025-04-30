---
"description": "Aprenda a configurar as configurações de fallback de fonte no Aspose.Words para .NET. Este guia completo garante que todos os caracteres em seus documentos sejam exibidos corretamente."
"linktitle": "Definir configurações de fallback de fonte"
"second_title": "API de processamento de documentos Aspose.Words"
"title": "Definir configurações de fallback de fonte"
"url": "/pt/net/working-with-fonts/set-font-fallback-settings/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Definir configurações de fallback de fonte

## Introdução

Ao trabalhar com documentos que contêm elementos de texto diversos, como idiomas diferentes ou caracteres especiais, é crucial garantir que esses elementos sejam exibidos corretamente. O Aspose.Words para .NET oferece um recurso poderoso chamado Configurações de Fallback de Fontes, que ajuda a definir regras para substituição de fontes quando a fonte original não suporta determinados caracteres. Neste guia, exploraremos como configurar as Configurações de Fallback de Fontes usando o Aspose.Words para .NET em um tutorial passo a passo.

## Pré-requisitos

Antes de começar o tutorial, certifique-se de ter os seguintes pré-requisitos:

- Conhecimento básico de C#: Familiaridade com a linguagem de programação C# e o framework .NET.
- Aspose.Words para .NET: Baixe e instale a partir do [link para download](https://releases.aspose.com/words/net/).
- Ambiente de desenvolvimento: uma configuração como o Visual Studio para escrever e executar seu código.
- Documento de exemplo: Tenha um documento de exemplo (por exemplo, `Rendering.docx`) pronto para teste.
- Regras de fallback de fonte XML: prepare um arquivo XML definindo as regras de fallback de fonte.

## Importar namespaces

Para usar o Aspose.Words, você precisa importar os namespaces necessários. Isso permite acesso a diversas classes e métodos necessários para o processamento de documentos.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System;
```

## Etapa 1: definir o diretório de documentos

Primeiro, defina o diretório onde seu documento está armazenado. Isso é essencial para localizar e processar seu documento.

```csharp
// O caminho para o diretório de documentos
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Etapa 2: Carregue o documento

Carregue seu documento em um Aspose.Words `Document` objeto. Esta etapa permite que você trabalhe com o documento programaticamente.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Etapa 3: Configurar as configurações de fonte

Criar um novo `FontSettings` objeto e carregue as configurações de fallback de fonte de um arquivo XML. Este arquivo XML contém as regras para fallback de fonte.

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.FallbackSettings.Load(dataDir + "Font fallback rules.xml");
```

## Etapa 4: aplicar configurações de fonte ao documento

Atribuir o configurado `FontSettings` ao documento. Isso garante que as regras de fallback de fonte sejam aplicadas ao renderizar o documento.

```csharp
doc.FontSettings = fontSettings;
```

## Etapa 5: Salve o documento

Por fim, salve o documento. As configurações de fallback de fonte serão usadas durante a operação de salvamento para garantir a substituição correta das fontes.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontFallbackSettings.pdf");
```

## Arquivo XML: Regras de fallback de fonte

Aqui está um exemplo de como deve ficar o arquivo XML que define as regras de fallback de fonte:

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<FontFallbackSettings xmlns="Aspose.Words">
    <FallbackTable>
        <Rule Ranges="0B80-0BFF" FallbackFonts="Vijaya"/>
        <Rule Ranges="1F300-1F64F" FallbackFonts="Segoe UI Emoji, Segoe UI Symbol"/>
        <Rule Ranges="2000-206F, 2070-209F, 20B9" FallbackFonts="Arial" />
        <Rule Ranges="3040-309F" FallbackFonts="MS Gothic" BaseFonts="Times New Roman"/>
        <Rule Ranges="3040-309F" FallbackFonts="MS Mincho"/>
        <Rule FallbackFonts="Arial Unicode MS"/>
    </FallbackTable>
</FontFallbackSettings>
```

## Conclusão

Seguindo estes passos, você poderá configurar e usar com eficiência as Configurações de Fallback de Fonte no Aspose.Words para .NET. Isso garante que seus documentos exibam todos os caracteres corretamente, mesmo que a fonte original não suporte determinados caracteres. A implementação dessas configurações aumentará significativamente a qualidade e a legibilidade dos seus documentos.

## Perguntas frequentes

### T1: O que é Font Fallback?

Font Fallback é um recurso que permite a substituição de fontes quando a fonte original não suporta determinados caracteres, garantindo a exibição correta de todos os elementos de texto.

### P2: Posso especificar várias fontes alternativas?

Sim, você pode especificar várias fontes alternativas nas regras XML. O Aspose.Words verificará cada fonte na ordem especificada até encontrar uma que suporte o caractere.

### Q3: Onde posso baixar o Aspose.Words para .NET?

Você pode baixá-lo do [Página de download do Aspose](https://releases.aspose.com/words/net/).

### T4: Como crio o arquivo XML para regras de fallback de fontes?

O arquivo XML pode ser criado usando qualquer editor de texto. Ele deve seguir a estrutura mostrada no exemplo fornecido neste tutorial.

### P5: Há suporte disponível para o Aspose.Words?

Sim, você pode encontrar suporte no [Fórum de suporte Aspose.Words](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}