---
category: general
date: 2026-04-21
description: Aprenda como detectar fontes, capturar avisos, configurar callbacks e
  enumerar avisos com Aspose.Words em C#. Guia passo a passo para um gerenciamento
  confiável de fontes.
draft: false
keywords:
- how to detect fonts
- how to capture warnings
- how to configure callback
- how to enumerate warnings
- Aspose.Words font handling
language: pt
og_description: Como detectar fontes no Aspose.Words? Este tutorial mostra como capturar
  avisos, configurar um callback e enumerar avisos em C#.
og_title: Como Detectar Fontes no Aspose.Words – Guia Completo
tags:
- Aspose.Words
- C#
- Document Processing
title: Como Detectar Fontes no Aspose.Words – Guia Completo
url: /pt/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como Detectar Fontes no Aspose.Words – Guia Completo

Já se perguntou **como detectar fontes** que estão ausentes ao carregar um documento Word? É um cenário que aparece mais vezes do que gostaríamos, especialmente ao lidar com arquivos legados ou implantações multiplataforma. Neste tutorial, vamos percorrer um exemplo completo e executável que **captura avisos**, **configura um callback** e **enumera avisos** para que você sempre saiba quais fontes foram substituídas.

Usaremos Aspose.Words for .NET (v24.9 na data de escrita) e C# puro. Sem serviços externos, sem mágica — apenas a API e algumas linhas de código. Ao final, você será capaz de identificar cada substituição de fonte, registrá‑la e até decidir abortar o carregamento se uma fonte crítica estiver ausente.  

### O que você precisará
- **Aspose.Words for .NET** (instale via NuGet: `Install-Package Aspose.Words`)
- .NET 6.0 ou superior (o código também funciona no .NET Framework)
- Um DOCX de exemplo que faça referência a uma fonte que não esteja presente na máquina (por exemplo, “MyCustomFont.ttf”)
- Visual Studio, Rider ou qualquer editor C# de sua preferência

> **Dica de especialista:** Se você não tem um documento com fontes ausentes, basta renomear um arquivo de fonte no seu sistema ou editar o XML do DOCX para referenciar uma família de fonte inexistente.

---

## Como Detectar Fontes com Aspose.Words

A ideia central é conectar‑se ao sistema de avisos do Aspose.Words. Quando a biblioteca não encontra uma fonte solicitada, ela emite um aviso `WarningType.FontSubstitution`. Ao fornecer uma implementação personalizada de `IWarningCallback`, você pode **detectar fontes** que foram trocadas durante o processo de carregamento.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// 1️⃣ Create a collector that implements IWarningCallback
public class FontWarningCollector : IWarningCallback
{
    public List<WarningInfo> Warnings { get; } = new();

    public void Warning(WarningInfo info)
    {
        // Store every warning – we’ll filter later
        Warnings.Add(info);
    }
}
```

> **Por que isso funciona:** Aspose.Words chama o método `Warning` para cada problema não crítico. Ao armazenar os objetos `WarningInfo` você tem acesso total ao tipo, mensagem e contexto, que é exatamente o que você precisa para **detectar fontes** que foram substituídas.

---

## Como Capturar Avisos ao Carregar um Documento

Agora que temos um coletor, precisamos instruir o `LoadOptions` a usá‑lo. Esta é a parte de **como capturar avisos** do quebra‑cabeça.

```csharp
// 2️⃣ Prepare LoadOptions with our warning collector
var warningCollector = new FontWarningCollector();
var loadOptions = new LoadOptions
{
    // Assign the callback – this is where warnings are captured
    WarningCallback = warningCollector
};

// 3️⃣ Load the document (replace the path with your own file)
Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFont.docx", loadOptions);
```

> **Caso especial:** Se você carregar um documento a partir de um stream (`new Document(stream, loadOptions)`), o mesmo callback funciona — basta passar o stream em vez do caminho do arquivo.

Neste ponto o documento está totalmente carregado, mas quaisquer avisos de substituição de fonte estão armazenados com segurança dentro de `warningCollector.Warnings`.

---

## Como Enumerar Avisos e Relatar Substituições de Fontes

Por fim, percorrermos os avisos coletados e **enumeramos avisos** que são especificamente sobre substituição de fonte. Esta etapa transforma os dados brutos em um relatório legível.

```csharp
// 4️⃣ Iterate over the collected warnings
foreach (var warning in warningCollector.Warnings)
{
    // We're only interested in font substitution warnings
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Substituted font: {warning.Message}");
    }
}
```

**Saída esperada** (exemplo):

```
Substituted font: Font 'Calibri' not found. Substituted with 'Arial'.
Substituted font: Font 'MyCustomFont' not found. Substituted with 'Times New Roman'.
```

Se o documento não contiver fontes ausentes, o loop simplesmente não produz saída — nada com que se preocupar.

---

## Exemplo Completo (Todas as Etapas em Um Arquivo)

A seguir está o programa completo que você pode copiar‑colar em um projeto de console. Ele une **como detectar fontes**, **como capturar avisos**, **como configurar o callback** e **como enumerar avisos** em um fluxo coeso.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontDetectionDemo
{
    // Custom warning collector (captures all warnings)
    public class FontWarningCollector : IWarningCallback
    {
        public List<WarningInfo> Warnings { get; } = new();

        public void Warning(WarningInfo info)
        {
            Warnings.Add(info);
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // -------------------------------------------------
            // Step 1: Set up the warning collector (how to configure callback)
            var collector = new FontWarningCollector();
            var loadOptions = new LoadOptions
            {
                WarningCallback = collector
            };

            // -------------------------------------------------
            // Step 2: Load the document (how to detect fonts)
            string filePath = "YOUR_DIRECTORY/DocumentWithMissingFont.docx";
            Document doc;
            try
            {
                doc = new Document(filePath, loadOptions);
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Failed to load document: {ex.Message}");
                return;
            }

            // -------------------------------------------------
            // Step 3: Enumerate warnings (how to enumerate warnings)
            bool anySubstitutions = false;
            foreach (var warning in collector.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    anySubstitutions = true;
                    Console.WriteLine($"Substituted font: {warning.Message}");
                }
            }

            if (!anySubstitutions)
            {
                Console.WriteLine("No font substitutions detected – all fonts are available.");
            }

            // Optional: Continue processing the document...
        }
    }
}
```

**Executar este programa** imprimirá cada fonte que o Aspose.Words teve que substituir. Você pode redirecionar a saída para um arquivo de log, disparar um alerta ou até abortar o carregamento se uma fonte crítica estiver ausente.

---

## Perguntas Frequentes & Armadilhas

### E se eu precisar interromper o carregamento quando uma fonte necessária estiver ausente?
Você pode inspecionar os objetos `WarningInfo` dentro do callback e lançar uma exceção quando um nome de fonte específico aparecer. A exceção abortará o carregamento, dando controle total.

```csharp
public void Warning(WarningInfo info)
{
    if (info.Type == WarningType.FontSubstitution &&
        info.Message.Contains("MyCriticalFont"))
    {
        throw new InvalidOperationException("Critical font missing – aborting load.");
    }
    Warnings.Add(info);
}
```

### Isso funciona com PDFs ou outros formatos?
Sim. Aspose.Words usa a mesma infraestrutura de avisos para PDFs, RTF e HTML. Basta substituir a extensão do arquivo e o restante do código permanece idêntico.

### Como posso registrar avisos em um arquivo ao invés do console?
Substitua `Console.WriteLine` por qualquer framework de logging que preferir (`Serilog`, `NLog`, etc.). A classe `WarningInfo` expõe `Message`, `Source` e `Exception` para logs detalhados.

### Isso afetará o desempenho?
O overhead é insignificante — o Aspose.Words já gera os avisos internamente. Adicionar um callback simplesmente os armazena em uma lista, o que é O(n) no número de avisos. Para documentos típicos, o impacto fica muito abaixo de 1 % do tempo total de carregamento.

---

## Resumo Visual

![How to Detect Fonts in Aspose.Words – warning flow diagram](https://example.com/images/font-detection-diagram.png "how to detect fonts")

*Texto alternativo:* **como detectar fontes** – diagrama mostrando callback de aviso, coleta e etapas de enumeração.

---

## Conclusão

Cobremos **como detectar fontes** no Aspose.Words por meio de **captura de avisos**, **configuração de callback** e **enumeração de avisos**. O exemplo completo demonstra um padrão pronto para produção que você pode inserir em qualquer aplicação .NET.  

A seguir, você pode explorar:

- **Como capturar avisos** para outros problemas (por exemplo, falhas na conversão de imagens)
- **Como configurar callback** para frameworks de logging personalizados
- **Como enumerar avisos** em múltiplos documentos em um job em lote
- Usar **Aspose.Words.Fonts.FontSettings** para fornecer pastas de fontes de fallback, o que pode reduzir o número de substituições desde o início.

Experimente, ajuste o coletor para se adequar ao seu estilo de logging e nunca mais seja surpreendido por uma troca de fonte inesperada. Se encontrar alguma particularidade, deixe um comentário abaixo — feliz codificação!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}