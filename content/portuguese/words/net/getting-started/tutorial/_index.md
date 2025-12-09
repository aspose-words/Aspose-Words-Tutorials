---
language: pt
url: /portuguese/net/getting-started/tutorial/
---

{{< layout-start >}}

{{< layout-start >}}

```yaml
---
title: "Detect Missing Fonts in Aspose.Words Documents – Complete C# Guide"
description: "Detect missing fonts in your Aspose.Words documents using a warning callback. Learn how to log font substitutions with C# and keep your PDFs looking right."
date: 2025-12-08
draft: false
language: "en"
category: "general"
url: "PLACEHOLDER_URL"
keywords:
  - detect missing fonts
  - Aspose.Words warning callback
  - font substitution
  - LoadOptions C#
  - document loading C#
  - missing font detection
tags:
  - Aspose.Words
  - C#
  - Font Management
og_title: "Detect Missing Fonts in Aspose.Words – Step‑by‑Step C# Guide"
og_description: "Detect missing fonts in Aspose.Words documents instantly. Follow this guide to set up a warning callback and capture font substitution events in C#."
---
```

# Detectar Fontes Ausentes em Documentos Aspose.Words – Guia Completo em C#  

Já se perguntou como **detectar fontes ausentes** ao carregar um arquivo Word com Aspose.Words? No meu dia a dia, encontrei alguns PDFs que pareciam estranhos porque o documento original usava uma fonte que eu não tinha instalada. A boa notícia? Aspose.Words pode dizer exatamente quando substitui uma fonte, e você pode capturar essa informação com um simples callback de aviso.  

Neste tutorial, percorreremos um **exemplo completo e executável** que mostra como registrar cada substituição de fonte, por que o callback é importante e alguns truques extras para uma detecção robusta de fontes ausentes. Sem enrolação, apenas o código e o raciocínio que você precisa para fazê-lo funcionar hoje.

---

## O que você aprenderá

- Como implementar **Aspose.Words warning callback** para capturar eventos de substituição de fonte.  
- Como configurar **LoadOptions C#** para que o callback seja invocado ao carregar um documento.  
- Como verificar se a detecção de fontes ausentes realmente funcionou e como é a saída no console.  
- Ajustes opcionais para lotes grandes ou ambientes sem interface gráfica.  

**Pré-requisitos** – Você precisa de uma versão recente do Aspose.Words para .NET (o código foi testado com 23.12), .NET 6 ou posterior, e um conhecimento básico de C#. Se você tem isso, está pronto para começar.

---

## Detectar Fontes Ausentes com um Callback de Aviso

O núcleo da solução é uma implementação de `IWarningCallback`. Aspose.Words dispara um objeto `WarningInfo` para muitas situações, mas nos interessamos apenas em `WarningType.FontSubstitution`. Vamos ver como conectar a isso.

### Etapa 1: Criar um Coletor de Avisos de Fonte

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Collects font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontWarningCollector : IWarningCallback
{
    // The Warning method is called automatically by the library.
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // Write a helpful message to the console.
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

*Por que isso importa*: Ao filtrar por `WarningType.FontSubstitution` evitamos ruído de avisos não relacionados (como recursos obsoletos). O `info.Description` já contém o nome da fonte original e a fonte de substituição usada, fornecendo um registro de auditoria claro.

---

## Configurar LoadOptions para Usar o Callback

Agora informamos ao Aspose.Words para usar nosso coletor ao carregar um arquivo.

### Etapa 2: Configurar LoadOptions

```csharp
// Create a LoadOptions instance – this controls how the document is read.
LoadOptions loadOptions = new LoadOptions
{
    // Assign our custom warning callback.
    WarningCallback = new FontWarningCollector()
};
```

*Por que isso importa*: `LoadOptions` é o único local onde você pode conectar o callback, senhas de criptografia e outros comportamentos de carregamento. Mantê‑lo separado do construtor `Document` torna o código reutilizável em vários arquivos.

---

## Carregar o Documento e Capturar Fontes Ausentes

Com o callback configurado, o próximo passo é simplesmente carregar o documento.

### Etapa 3: Carregar seu DOCX (ou qualquer formato suportado)

```csharp
// Replace the path with the location of your test document.
string inputPath = @"C:\Docs\input.docx";

try
{
    // The warning callback fires automatically during this call.
    Document doc = new Document(inputPath, loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    // Handle file‑not‑found, access‑denied, etc.
    Console.WriteLine($"Error loading document: {ex.Message}");
}
```

Quando o construtor `Document` analisa o arquivo, qualquer fonte ausente aciona nosso `FontWarningCollector`. O console exibirá linhas como:

```
Font substituted: Arial (substituted with Liberation Sans)
Document loaded successfully.
```

Essa linha é a evidência concreta de que **detectar fontes ausentes** funcionou.

---

## Verificar a Saída – O que Esperar

Execute o programa a partir de um terminal ou do Visual Studio. Se o documento fonte contiver uma fonte que você não tem instalada, verá ao menos uma linha “Font substituted”. Se o documento usar apenas fontes instaladas, o callback permanecerá silencioso e você verá apenas a mensagem “Document loaded successfully.”.  

**Dica**: Para confirmar, abra o arquivo Word no Microsoft Word e verifique a lista de fontes. Qualquer fonte que apareça em *Replace Fonts* sob o grupo *Home → Font* é candidata à substituição.

---

## Avançado: Detectar Fontes Ausentes em Lote

Frequentemente você precisa analisar dezenas de arquivos. O mesmo padrão escala bem:

```csharp
string[] files = Directory.GetFiles(@"C:\Docs\Batch", "*.docx");

foreach (var file in files)
{
    Console.WriteLine($"\nProcessing: {Path.GetFileName(file)}");
    Document doc = new Document(file, loadOptions);
}
```

Como o `FontWarningCollector` grava no console a cada invocação, você obterá um relatório por arquivo sem necessidade de infraestrutura extra. Para cenários de produção, talvez queira registrar em um arquivo ou banco de dados – basta substituir `Console.WriteLine` pelo seu logger preferido.

---

## Armadilhas Comuns & Dicas Profissionais

| Problema | Por que acontece | Solução |
|----------|------------------|---------|
| **Nenhum aviso aparece** | O documento realmente contém apenas fontes instaladas. | Verifique abrindo o arquivo no Word ou removendo deliberadamente uma fonte do seu sistema. |
| **Callback não chamado** | `LoadOptions.WarningCallback` nunca foi atribuído ou uma nova instância de `LoadOptions` foi usada posteriormente. | Mantenha um único objeto `LoadOptions` e reutilize‑o para cada carregamento. |
| **Muitos avisos não relacionados** | Você não filtrou por `WarningType.FontSubstitution`. | Adicione a verificação `if (info.Type == WarningType.FontSubstitution)` conforme mostrado. |
| **Desempenho reduzido em arquivos grandes** | O callback é executado em cada aviso, o que pode ser muitos em documentos grandes. | Desative outros tipos de aviso via `LoadOptions.WarningCallback` ou defina `LoadOptions.LoadFormat` para um tipo específico se você souber. |

---

## Exemplo Completo Funcional (Pronto para Copiar‑Colar)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Step 2 – configure LoadOptions with our warning callback.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningCollector()
        };

        // Path to a single document or a folder for batch processing.
        string inputPath = @"C:\Docs\input.docx";

        try
        {
            // Step 3 – load the document; warnings are emitted automatically.
            Document doc = new Document(inputPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**Saída esperada no console** (quando uma fonte ausente é encontrada):

```
Font substituted: Times New Roman (substituted with Liberation Serif)
Document loaded successfully.
```

Se nenhuma substituição ocorrer, você verá apenas a linha de sucesso.

---

## Conclusão

Agora você tem uma **solução completa e pronta para produção para detectar fontes ausentes** em qualquer documento processado pelo Aspose.Words. Ao aproveitar o **callback de aviso do Aspose.Words** e configurar **LoadOptions C#**, você pode registrar cada substituição de fonte, solucionar problemas de layout e garantir que seus PDFs mantenham a aparência pretendida.  

De um único arquivo a um lote massivo, o padrão permanece o mesmo — implemente `IWarningCallback`, conecte‑o ao `LoadOptions` e deixe o Aspose.Words fazer o trabalho pesado.  

Pronto para o próximo passo? Tente combinar isso com **incorporação de fontes** ou **famílias de fontes de fallback** para corrigir o problema automaticamente, ou explore a API **DocumentVisitor** para uma análise de conteúdo mais profunda. Feliz codificação, e que todas as suas fontes permaneçam onde você espera!

---

![Detectar fontes ausentes em Aspose.Words – captura de tela da saída do console](https://example.com/images/detect-missing-fonts.png "saída do console de detecção de fontes ausentes")

{{< layout-end >}}

{{< layout-end >}}