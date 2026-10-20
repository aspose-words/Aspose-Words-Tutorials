---
category: general
date: 2026-06-27
description: Registre o callback de aviso no Aspose.Words para capturar substituições
  de fontes e problemas de carregamento. Aprenda o uso passo a passo do LoadOptions
  com o Aspose.Words.
draft: false
keywords:
- register warning callback aspose.words
- aspose.words warning callback
- loadoptions font substitution warning
- document loading warning handling
- aspose.words loadoptions example
language: pt
og_description: Registre o callback de aviso no Aspose.Words para monitorar substituições
  de fontes e outros avisos de carregamento. Siga este tutorial completo para uma
  implementação robusta.
og_title: Registrar Callback de Aviso no Aspose.Words – Guia Completo
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Register warning callback in Aspose.Words to catch font substitutions
    and loading issues. Learn step‑by‑step usage of LoadOptions with Aspose.Words.
  headline: Register Warning Callback in Aspose.Words – Complete Programming Guide
  type: TechArticle
- description: Register warning callback in Aspose.Words to catch font substitutions
    and loading issues. Learn step‑by‑step usage of LoadOptions with Aspose.Words.
  name: Register Warning Callback in Aspose.Words – Complete Programming Guide
  steps:
  - name: 4.1 Logging to a File Instead of Console
    text: 'In production you rarely want console spam. Swap `Console.WriteLine` for
      a logger (e.g., `Serilog`, `NLog`) or write to a text file:'
  - name: 4.2 Providing a Custom Font Directory
    text: 'If your environment uses corporate fonts, tell Aspose.Words where to look
      before it falls back to substitution:'
  - name: 4.3 Handling Non‑Font Warnings
    text: 'You can broaden the scope to capture any loading warning:'
  - name: 5.1 Verify with a Document That Has Missing Fonts
    text: Create a small DOCX that references a font not installed on your machine
      (e.g., “Comic Sans MS” on a Linux server). Run the loader; you should see a
      substitution message.
  - name: 5.2 Benchmark Overhead
    text: The callback adds negligible overhead—roughly a few microseconds per warning.
      If you’re loading thousands of documents, you might batch log entries or disable
      the callback for non‑critical runs.
  - name: 5.3 Edge Cases
    text: '- **Multiple Substitutions for the Same Font:** Aspose.Words may fire the
      callback multiple times if the same missing font appears on different pages.
      Deduplicate in your logger if needed. - **Encrypted Documents:** If the DOCX
      is password‑protected, you must also set `loadOptions.Password`. The cal'
  type: HowTo
tags:
- aspose-words
- warning-callback
- csharp
- document-processing
title: Registrar Callback de Aviso no Aspose.Words – Guia Completo de Programação
url: /pt/net/programming-with-loadoptions/register-warning-callback-in-aspose-words-complete-programmi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Registrar Callback de Aviso no Aspose.Words – Guia de Programação Completo

Já se perguntou como **register warning callback in Aspose.Words** para ver exatamente quais fontes são substituídas quando um documento é carregado? Você não está sozinho. Muitos desenvolvedores se deparam com um problema quando a substituição silenciosa de fontes estraga o layout de um PDF ou arquivo Word gerado.  

Neste tutorial vamos percorrer uma solução prática que não só registra um callback de aviso no Aspose.Words, mas também explica *por que* você deve fazê‑lo, como o callback funciona nos bastidores e quais casos extremos você pode encontrar. Ao final, você será capaz de registrar cada substituição de fonte, capturar outros avisos de carregamento e manter seu pipeline de processamento de documentos transparente.

## O que Você Vai Aprender

- Configurar **LoadOptions** para controlar o comportamento de carregamento do documento.  
- Registrar um **warning callback** que dispara para substituição de fonte e outros tipos de aviso.  
- Carregar um DOCX com as opções configuradas e interpretar a saída do callback.  
- Armadilhas comuns (fonts ausentes, pastas de fontes personalizadas e considerações de desempenho).  

**Pré‑requisitos:** Visual Studio 2022 (ou qualquer IDE C#), runtime .NET 6+ e uma licença ativa do Aspose.Words (a versão de avaliação gratuita serve para experimentação). Não são necessários pacotes NuGet adicionais além de `Aspose.Words`.

---

![Diagrama ilustrando o fluxo de registro de um callback de aviso no Aspose.Words e o tratamento de avisos de substituição de fontes](register-warning-callback-aspose-words.png "diagrama de registro de callback de aviso aspose.words")

## Etapa 1: Criar LoadOptions – O Ponto de Entrada para o Tratamento de Avisos  

Antes que o callback possa disparar, você precisa de uma instância de **LoadOptions**. Pense nele como o painel de controle que você entrega ao Aspose.Words quando diz “carregue este arquivo, mas avise se algo parecer errado.”  

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Loading.Warning;

// Initialize LoadOptions – this object will carry our warning callback.
var loadOptions = new LoadOptions();
```

> **Por que isso importa:** `LoadOptions` permite ajustar tudo, desde senhas de criptografia até diretórios de fontes. Ao anexar um warning callback a esse objeto, você transforma um processo silencioso em observável.

## Etapa 2: Registrar o Warning Callback – Capturar Substituições de Fonte  

Agora vem a estrela do show: o **warning callback**. Vamos registrar um método anônimo (uma lambda) que o Aspose.Words invoca para cada aviso de carregamento. Dentro do callback filtramos por `WarningType.FontSubstitution` e exibimos uma mensagem amigável.

```csharp
// Register a warning callback to be notified of font substitutions.
loadOptions.WarningCallback = (sender, args) =>
{
    // The callback runs for each loading warning; we care about font substitution warnings.
    if (args.WarningType == WarningType.FontSubstitution)
    {
        // Cast to the more specific warning info type.
        var fontWarning = (FontSubstitutionWarningInfo)args;
        Console.WriteLine(
            $"Font '{fontWarning.FontName}' was substituted with '{fontWarning.SubstitutedFontName}'.");
    }
    // Optional: handle other warning types here (e.g., MissingResource, UnsupportedFeature).
};
```

> **Dica de especialista:** Se também quiser registrar imagens ausentes ou recursos não suportados, adicione ramificações `if` adicionais verificando `args.WarningType`. Isso transforma sua **register warning callback in Aspose.Words** em um ponto único para todos os diagnósticos de carregamento.

## Etapa 3: Carregar o Documento Usando as LoadOptions Configuradas  

Com o callback conectado, o próximo passo é simplesmente carregar o documento. Passe a instância `loadOptions` ao construtor `Document`. Cada vez que o Aspose.Words encontrar uma fonte que não consegue localizar, seu callback disparará e escreverá no console.

```csharp
// Load the DOCX while the warning callback is active.
var doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

Execute o programa e você verá uma saída semelhante a:

```
Font 'Calibri' was substituted with 'Arial'.
Font 'Times New Roman' was substituted with 'Liberation Serif'.
```

Esse é o núcleo do **register warning callback aspose.words** — um padrão de três etapas que pode ser reutilizado em qualquer projeto.

## Etapa 4: Estendendo o Callback para Cenários do Mundo Real  

### 4.1 Registrando em Arquivo ao Invés do Console  

Em produção você raramente quer spam no console. Substitua `Console.WriteLine` por um logger (por exemplo, `Serilog`, `NLog`) ou grave em um arquivo de texto:

```csharp
loadOptions.WarningCallback = (sender, args) =>
{
    if (args.WarningType == WarningType.FontSubstitution)
    {
        var info = (FontSubstitutionWarningInfo)args;
        File.AppendAllText("font-warnings.log",
            $"[WARN] {DateTime.Now}: Font '{info.FontName}' → '{info.SubstitutedFontName}'{Environment.NewLine}");
    }
};
```

### 4.2 Fornecendo um Diretório de Fontes Personalizado  

Se seu ambiente usa fontes corporativas, informe ao Aspose.Words onde procurar antes que ele recorra à substituição:

```csharp
loadOptions.FontSettings = new FontSettings();
loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", recursive: true);
```

Agora o callback pode disparar *menos* vezes, pois o mecanismo encontra as fontes corretas.

### 4.3 Tratando Avisos Não Relacionados a Fontes  

Você pode ampliar o escopo para capturar qualquer aviso de carregamento:

```csharp
loadOptions.WarningCallback = (sender, args) =>
{
    switch (args.WarningType)
    {
        case WarningType.FontSubstitution:
            var f = (FontSubstitutionWarningInfo)args;
            Log($"Font '{f.FontName}' → '{f.SubstitutedFontName}'");
            break;
        case WarningType.MissingResource:
            var m = (MissingResourceWarningInfo)args;
            Log($"Missing resource: {m.ResourceType} - {m.ResourceName}");
            break;
        // Add more cases as needed.
    }
};
```

## Etapa 5: Testando Sua Implementação – O Que Esperar  

### 5.1 Verificar com um Documento que Possui Fontes Ausentes  

Crie um pequeno DOCX que referencie uma fonte não instalada na sua máquina (por exemplo, “Comic Sans MS” em um servidor Linux). Execute o carregador; você deverá ver uma mensagem de substituição.  

### 5.2 Medir a Sobrecarga  

O callback adiciona uma sobrecarga insignificante — aproximadamente alguns microssegundos por aviso. Se você estiver carregando milhares de documentos, pode agrupar as entradas de log ou desativar o callback em execuções não críticas.  

### 5.3 Casos de Borda  

- **Múltiplas substituições para a mesma fonte:** o Aspose.Words pode disparar o callback várias vezes se a mesma fonte ausente aparecer em páginas diferentes. Desduplicar no seu logger, se necessário.  
- **Documentos criptografados:** se o DOCX estiver protegido por senha, você também deve definir `loadOptions.Password`. O callback ainda disparará após a descriptografia.  
- **Carregamento assíncrono:** a API é síncrona, mas você pode envolver a chamada de carregamento em `Task.Run` para processamento em segundo plano; o callback permanece thread‑safe.

## Armadilhas Comuns & Como Evitá‑las  

| Armadilha | Por que acontece | Solução |
|-----------|------------------|---------|
| **Nenhuma saída** | Callback não atribuído *ou* `WarningCallback` sobrescrito depois. | Garanta que você atribua o callback **uma única vez** antes do carregamento e não reatribua `loadOptions` após a atribuição. |
| **Exceção de cast incorreto** | Tentativa de converter um aviso que não é `FontSubstitutionWarningInfo`. | Sempre verifique `args.WarningType` antes de fazer o cast. |
| **Desaceleração de desempenho** | Log síncrono para um destino de I/O lento. | Use frameworks de log assíncronos ou faça buffer das gravações. |
| **Fontes personalizadas ausentes** | Pasta de fontes não adicionada ao `FontSettings`. | Adicione `SetFontsFolder` conforme mostrado na Etapa 4.2. |

## Exemplo Completo – Copiar‑e‑Colar  

A seguir, um programa autocontido que você pode copiar para um novo projeto Console App. Ele demonstra todo o fluxo do início ao fim.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Loading.Warning;

class Program
{
    static void Main()
    {
        // 1️⃣ Create LoadOptions.
        var loadOptions = new LoadOptions();

        // 2️⃣ Register the warning callback (register warning callback Aspose.Words).
        loadOptions.WarningCallback = (sender, args) =>
        {
            if (args.WarningType == WarningType.FontSubstitution)
            {
                var fontInfo = (FontSubstitutionWarningInfo)args;
                Console.WriteLine(
                    $"Font '{fontInfo.FontName}' was substituted with '{fontInfo.SubstitutedFontName}'.");
            }
            // Optional: handle other warnings here.
        };

        // Optional: tell Aspose where to find corporate fonts.
        // loadOptions.FontSettings = new FontSettings();
        // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", true);

        // 3️⃣ Load the document using the configured options.
        string filePath = Path.Combine(Environment.CurrentDirectory, "input.docx");
        var doc = new Document(filePath, loadOptions);

        // At this point the document is loaded, and any font substitutions have been printed.
        Console.WriteLine("Document loaded successfully.");
    }
}
```

**Saída esperada no console** (supondo fontes ausentes):

```
Font 'Calibri' was substituted with 'Arial'.
Font 'Times New Roman' was substituted with 'Liberation Serif'.
Document loaded successfully.
```

Execute o programa e você verá exatamente quais fontes o Aspose.Words substituiu, proporcionando total visibilidade do processo de carregamento.

---

## Conclusão  

Acabamos de cobrir **how to register warning callback in Aspose.Words**, por que isso é uma prática recomendada para qualquer fluxo de trabalho de processamento de documentos e como estender o padrão para logging, fontes personalizadas e tratamento mais amplo de avisos. Com apenas três linhas de código, você transforma uma operação de carregamento de caixa‑preta em uma etapa auditável e depurável — nada mais de mudanças misteriosas de layout.

Qual o próximo passo? Experimente combinar esse callback com **Aspose.Words SaveOptions** para registrar avisos tanto no carregamento *quanto* na gravação, ou conecte o callback a uma API web que processe uploads em tempo real. Você também pode explorar as outras palavras‑chave secundárias que introduzimos — como *loadoptions font substitution warning* — para ajustar desempenho ou integrar a um painel de monitoramento.

Tem dúvidas ou um cenário complicado? Deixe um comentário e vamos solucionar juntos. Boa codificação, e que seus PDFs sempre renderizem com as fontes corretas!

## O Que Você Deve Aprender a Seguir?


Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Aspose Words Java Callback Custom Savings](/words/german/java/images-shapes/aspose-words-java-callback-custom-savings/)
- [Aspose Words Java Callback Custom Savings](/words/french/java/images-shapes/aspose-words-java-callback-custom-savings/)
- [Aspose Words Java Callback Custom Savings](/words/spanish/java/images-shapes/aspose-words-java-callback-custom-savings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}