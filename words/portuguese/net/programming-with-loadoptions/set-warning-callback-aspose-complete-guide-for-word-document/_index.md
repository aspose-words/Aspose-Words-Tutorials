---
category: general
date: 2026-05-23
description: Defina o callback de aviso do Aspose para capturar avisos de substituição
  de fontes no Aspose.Words. Aprenda sobre LoadOptions, FontSettings e a implementação
  de IWarningCallback.
draft: false
keywords:
- set warning callback aspose
- aspose words loadoptions
- aspose fonts substitution
- iwarningcallback implementation
- aspose document loading
language: pt
og_description: Defina o callback de aviso Aspose para monitorar a substituição de
  fontes no Aspose.Words. Este tutorial mostra LoadOptions, FontSettings e a implementação
  do manipulador de avisos.
og_title: Definir Callback de Aviso Aspose – Guia Passo a Passo
schemas:
- author: Aspose
  dateModified: '2026-05-23'
  description: set warning callback aspose to capture font substitution warnings in
    Aspose.Words. Learn LoadOptions, FontSettings, and IWarningCallback implementation.
  headline: set warning callback aspose – Complete Guide for Word Document Loading
  type: TechArticle
- description: set warning callback aspose to capture font substitution warnings in
    Aspose.Words. Learn LoadOptions, FontSettings, and IWarningCallback implementation.
  name: set warning callback aspose – Complete Guide for Word Document Loading
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code works on .NET Framework 4.5+ as well). -
      A valid Aspose.Words for .NET license or a trial key. - Visual Studio, Rider,
      or any C# editor you prefer. - A sample DOCX (`fontTest.docx`) that references
      a missing font (optional but helpful).'
  - name: Expected console output
    text: 'If `fontTest.docx` references a font that isn’t installed, you’ll see something
      like:'
  - name: When to use a custom LoadOptions
    text: '- **Batch processing** of many files where you want a uniform logging strategy.
      - **Cloud services** that need to report missing fonts back to the caller. -
      **Testing pipelines** that verify documents adhere to a corporate font policy.'
  type: HowTo
tags:
- Aspose.Words
- C#
- FontSettings
title: Definir callback de aviso Aspose – Guia completo para carregamento de documentos
  Word
url: /pt/net/programming-with-loadoptions/set-warning-callback-aspose-complete-guide-for-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# definir callback de aviso aspose – Guia Completo para Carregamento de Documentos Word

Já se perguntou como **definir callback de aviso aspose** para nunca perder um alerta de substituição de fonte novamente? Você não está sozinho. Quando um DOCX referencia uma fonte que não está instalada, o Aspose.Words a substitui silenciosamente, e sem um callback adequado você pode nunca saber que algo mudou.

Neste tutorial, percorreremos um exemplo completo e executável que mostra exatamente como capturar esses avisos. Ao final, você entenderá **Aspose.Words LoadOptions**, como configurar **FontSettings** e por que implementar **IWarningCallback** é a maneira mais limpa de ficar informado. Sem enrolação — apenas o código que você pode inserir em um projeto .NET hoje.

## O que você aprenderá

- Como **definir callback de aviso aspose** em uma instância de `LoadOptions`.  
- O papel de **Aspose.Words LoadOptions** ao abrir um documento.  
- Configurando o tratamento de **substituição de fontes Aspose** com `FontSettings`.  
- Escrevendo uma implementação personalizada de **IWarningCallback** para registrar problemas de fontes.  
- Carregando um documento com segurança usando as melhores práticas de **carregamento de documentos Aspose**.

### Pré-requisitos

- .NET 6.0 ou superior (o código também funciona no .NET Framework 4.5+).  
- Uma licença válida do Aspose.Words for .NET ou uma chave de avaliação.  
- Visual Studio, Rider ou qualquer editor C# de sua preferência.  
- Um DOCX de exemplo (`fontTest.docx`) que referencia uma fonte ausente (opcional, mas útil).

> **Dica profissional:** Se você não tem um DOCX com fonte ausente, basta renomear uma fonte no estilo do documento e observar o aviso disparar.

---

## Como definir callback de aviso aspose para carregamento de documentos

Abaixo está o programa completo e autocontido. Salve-o como `Program.cs`, restaure os pacotes NuGet e execute. O console imprimirá cada aviso de substituição de fonte que o Aspose.Words gerar ao carregar o arquivo.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// ------------------------------------------------------------
// Step 1: Create a warning handler that implements IWarningCallback
// ------------------------------------------------------------
class FontSubstitutionWarningHandler : IWarningCallback
{
    // This method is called by Aspose.Words for each warning.
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // The Description property tells you which font was substituted.
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

// ------------------------------------------------------------
// Step 2: Prepare FontSettings (default works for most cases)
// ------------------------------------------------------------
FontSettings fontSettings = new FontSettings();
// You could add custom font folders here if you want to avoid substitution:
// fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

// ------------------------------------------------------------
// Step 3: Build LoadOptions and attach our warning callback
// ------------------------------------------------------------
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = new FontSubstitutionWarningHandler()
};

// ------------------------------------------------------------
// Step 4: Load the document using the configured LoadOptions
// ------------------------------------------------------------
try
{
    // Replace the path with the location of your test document.
    Document doc = new Document("YOUR_DIRECTORY/fontTest.docx", loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"Error loading document: {ex.Message}");
}
```

### Saída esperada no console

Se o `fontTest.docx` referencia uma fonte que não está instalada, você verá algo como:

```
Font substitution: Font 'Comic Sans MS' was substituted with 'Arial'.
Document loaded successfully.
```

Se todas as fontes estiverem presentes, a única linha impressa será *Document loaded successfully* — sem avisos, sem ruído.

![set warning callback aspose example](image.png "set warning callback aspose example")

---

## Entendendo LoadOptions no Aspose.Words

`LoadOptions` é a porta de entrada para todos os ajustes que você pode fazer no **carregamento de documentos aspose**. Ele permite:

1. **Especificar um `FontSettings` personalizado** – útil quando seu aplicativo inclui suas próprias fontes.  
2. **Anexar um callback de aviso** – exatamente o que fizemos para capturar substituições de fontes.  
3. Controlar a detecção de formato de documento, manipulação de senha e mais.

Como `LoadOptions` é passado ao construtor `Document`, as configurações são aplicadas **uma única vez**, exatamente no momento em que o arquivo é analisado. Por isso podemos garantir que nosso manipulador de avisos verá cada substituição antes que o documento seja construído na memória.

### Quando usar um LoadOptions personalizado

- **Processamento em lote** de muitos arquivos onde você deseja uma estratégia de registro uniforme.  
- **Serviços em nuvem** que precisam relatar fontes ausentes ao chamador.  
- **Pipelines de teste** que verificam se os documentos aderem a uma política corporativa de fontes.

---

## Configurando FontSettings para substituição de fontes Aspose

O objeto `FontSettings` controla como o Aspose.Words resolve fontes. Por padrão, ele procura nas pastas de fontes do sistema e, em seguida, recorre a substitutos internos. Você pode ajustar finamente esse comportamento:

```csharp
FontSettings fontSettings = new FontSettings();

// Add a folder that contains your corporate fonts.
fontSettings.SetFontsFolder(@"C:\Corporate\Fonts", recursive: true);

// Optionally, map a missing font to a specific substitute.
fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes(
    "MissingFont", new[] { "Arial", "Times New Roman" });
```

Essas linhas são opcionais para o cenário básico de “definir callback de aviso aspose”, mas ilustram como você pode **reduzir** o número de avisos de substituição fornecendo as fontes corretas antecipadamente.

---

## Implementando IWarningCallback para avisos de substituição de fontes

A interface `IWarningCallback` é pequena — apenas um único método `Warning`. Ainda assim, ela lhe dá **controle total** sobre como os avisos são tratados:

- **Registrar em um arquivo** em vez do console.  
- **Coletar avisos** em uma lista para análise posterior.  
- **Lançar exceções** para avisos críticos (por exemplo, quando uma fonte necessária está ausente).

Aqui está um exemplo rápido que armazena avisos em um `List<string>`:

```csharp
class CollectingWarningHandler : IWarningCallback
{
    public List<string> Messages { get; } = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Messages.Add(info.Description);
    }
}
```

Você poderia então inspecionar `handler.Messages` após carregar o documento para decidir se aborta o processamento.

---

## Carregando um documento com tratamento de aviso personalizado (fluxo completo)

Juntando tudo, o padrão final que você provavelmente reutilizará tem a seguinte aparência:

```csharp
// 1️⃣ Create the warning handler.
CollectingWarningHandler handler = new CollectingWarningHandler();

// 2️⃣ Set up FontSettings (add custom fonts if needed).
FontSettings fs = new FontSettings();
fs.SetFontsFolder(@"C:\MyApp\Fonts", true);

// 3️⃣ Build LoadOptions with both FontSettings and the handler.
LoadOptions opts = new LoadOptions
{
    FontSettings = fs,
    WarningCallback = handler
};

// 4️⃣ Load the document.
Document doc = new Document("input.docx", opts);

// 5️⃣ React to any font‑substitution warnings.
if (handler.Messages.Any())
{
    Console.WriteLine("The following fonts were substituted:");
    foreach (var msg in handler.Messages)
        Console.WriteLine("- " + msg);
}
else
{
    Console.WriteLine("No font issues detected.");
}
```

Este trecho demonstra o fluxo de **carregamento de documentos aspose** que você usará em produção: configure, carregue e então reaja. O padrão escala bem, seja processando um único arquivo ou percorrendo milhares.

---

## Perguntas Frequentes & Casos Limítrofes

**E se o documento estiver protegido por senha?**  
Adicione `Password = "secret"` ao inicializador de `LoadOptions`. O callback de aviso ainda funciona depois que o arquivo é descriptografado.

**O callback será disparado para outros tipos de aviso?**  
Sim — `WarningInfo.Type` pode ser `DocumentStructure`, `UnsupportedFileFormat`, etc. No nosso exemplo filtramos por `FontSubstitution`, mas você pode registrar tudo removendo a verificação `if`.

**Isso afeta o desempenho?**  
Negligentemente. O callback é invocado apenas quando ocorre um aviso, o que é muito menos frequente que as etapas normais de análise.

**Posso desativar a substituição de fontes completamente?**  
Você pode definir `fontSettings.SubstitutionSettings.DefaultFontSubstitution = false;`, mas então o Aspose.Words lançará uma exceção para fontes ausentes em vez de substituí‑las.

---

## Conclusão

Agora você sabe exatamente como **definir callback de aviso aspose** para monitorar eventos de substituição de fontes durante o processamento de **Aspose.Words LoadOptions**. Configurando `FontSettings`, implementando um `IWarningCallback` leve e carregando o documento com essas opções, você obtém total visibilidade sobre quaisquer alterações de fontes que o Aspose faça nos bastidores.

A partir daqui, você pode:

- Estender o manipulador de avisos para gravar em um serviço de registro central.  
- Combinar o callback com uma estratégia personalizada de fallback de fontes.  
- Usar o padrão ao construir uma API em nuvem que valida documentos enviados por clientes.

Experimente com seus próprios arquivos DOCX, ajuste o `FontSettings` e observe o console dizer exatamente quais fontes foram substituídas. Boa codificação, e que seus documentos sempre sejam renderizados como esperado!

## Tutoriais Relacionados

- [Capturar Avisos de Substituição de Fonte em Java com Aspose.Words – Guia Completo](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Habilitar Avisos de Substituição de Fonte no Aspose.Words – Guia Completo](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [Como Definir LoadOptions no Aspose.Words para Java](/words/english/java/document-loading-and-saving/using-load-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}