---
category: general
date: 2026-01-06
description: Aprenda como receber avisos ao carregar documentos e como monitorar fontes
  usando Aspose.Words. Este guia aborda callbacks de avisos e o rastreamento de substituição
  de fontes.
draft: false
keywords:
- how to get warnings
- how to monitor fonts
- Aspose.Words warning callback
- font substitution detection
- document load options
language: pt
og_description: Como obter avisos no Aspose.Words? Siga este tutorial passo a passo
  para monitorar fontes e capturar mensagens de substituição ao carregar documentos.
og_title: Como obter avisos no Aspose.Words – Monitorar fontes
tags:
- Aspose.Words
- C#
- Font Monitoring
title: Como obter avisos no Aspose.Words – Monitorar fontes em C#
url: /pt/net/working-with-fonts/how-to-get-warnings-in-aspose-words-monitor-fonts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como Obter Avisos no Aspose.Words – Monitorar Fontes em C#

Já se perguntou **como obter avisos** quando um documento Word contém fontes que você não tem instaladas? É um problema comum—seu aplicativo troca silenciosamente fontes ausentes e você nunca sabe o que mudou. A boa notícia é que você pode conectar ao sistema de avisos do Aspose.Words e **monitorar fontes** em tempo real.

Neste tutorial vamos mostrar exatamente como capturar esses avisos de substituição de fonte, por que isso importa e o que fazer com a informação assim que a tiver. Sem documentação externa, apenas um exemplo completo e executável que você pode colar no Visual Studio agora mesmo.

> **Dica profissional:** Se você está construindo um pipeline de conversão de documentos, registrar fontes ausentes cedo evita surpresas desagradáveis de layout mais adiante.

---

## O Que Você Precisa

- **Aspose.Words for .NET** (última versão; a API não mudou desde a v23.10)
- Um ambiente de desenvolvimento .NET (Visual Studio, Rider ou VS Code com a extensão C#)
- Um arquivo `.docx` de exemplo que referencia uma fonte que você não tem instalada (por exemplo, **“NonExistentFont”**)

É só isso—nenhum pacote NuGet extra além do Aspose.Words.

---

## Etapa 1 – Configurar um Coletor de Avisos (Palavra‑Chave Principal no Cabeçalho)

A primeira coisa que você precisa é um local para armazenar os avisos à medida que ocorrem. O Aspose.Words fornece a propriedade `WarningCallback` em `LoadOptions` exatamente para esse propósito.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using Aspose.Words.Loading;

// Create a collection that will receive every warning emitted during load.
WarningInfoCollection warningCollector = new WarningInfoCollection();

// Attach the collector to LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = warningCollector
};
```

**Por que isso importa:**  
Quando a biblioteca encontra uma fonte ausente, ela não lança uma exceção; ela emite um objeto `WarningInfo`. Ao conectar um coletor, você ganha total visibilidade de cada evento de substituição, permitindo **monitorar fontes** sem poluir seu console com mensagens irrelevantes.

---

## Etapa 2 – Carregar o Documento com as Opções de Aviso Ativadas

Agora realmente lemos o arquivo. As `LoadOptions` que preparamos na etapa anterior garantem que quaisquer avisos relacionados a fontes sejam capturados.

```csharp
// Replace the path with the location of your test document.
string docPath = @"C:\Docs\unknownFont.docx";

Document doc = new Document(docPath, loadOptions);
```

**O que está acontecendo nos bastidores?**  
O Aspose.Words analisa o arquivo Word, resolve as fontes e, sempre que não consegue encontrar uma fonte solicitada, recorre a uma substituta (geralmente Arial). A substituição dispara um aviso `WarningType.FontSubstitution`, que vai para `warningCollector`.

---

## Etapa 3 – Inspecionar os Avisos Coletados (Palavra‑Chave Principal Aparece Novamente)

Depois que o documento é carregado, simplesmente iteramos sobre o `warningCollector` e imprimimos quaisquer mensagens de substituição de fonte.

```csharp
foreach (WarningInfo warning in warningCollector)
{
    if (warning.WarningType == WarningType.FontSubstitution)
    {
        // The Description contains a readable message like:
        // "Font 'NonExistentFont' was not found. Substituted with 'Arial'."
        Console.WriteLine($"Substituted font: {warning.Description}");
    }
}
```

**Saída esperada** (supondo que a fonte ausente seja *“FancyScript”*):

```
Substituted font: Font 'FancyScript' was not found. Substituted with 'Arial'.
```

Se o documento contiver várias fontes desconhecidas, você verá uma linha por substituição—perfeito para registro ou alerta.

---

## Etapa 4 – Opcional: Registrar ou Persistir as Informações de Aviso

Em produção você provavelmente quer algo mais robusto que um `Console.WriteLine`. Aqui está um exemplo rápido que grava os avisos em um arquivo JSON para análise posterior.

```csharp
using System.IO;
using System.Text.Json;

// Build a simple DTO.
var warnings = warningCollector
    .Where(w => w.WarningType == WarningType.FontSubstitution)
    .Select(w => new { FontMessage = w.Description })
    .ToList();

string json = JsonSerializer.Serialize(warnings, new JsonSerializerOptions { WriteIndented = true });
File.WriteAllText(@"C:\Logs\font-warnings.json", json);

Console.WriteLine("Font warnings saved to font-warnings.json");
```

Agora você tem um registro permanente que pode alimentar um painel de monitoramento, ou até mesmo disparar uma solicitação automática pelos arquivos de fonte ausentes.

---

## Etapa 5 – Verificar o Resultado e Limpar

Execute o programa. Se você vir as mensagens de substituição, obteve **avisos** com sucesso e agora está ativamente **monitorando fontes**. Se nada aparecer, verifique novamente se o documento de teste realmente referencia uma fonte que não está instalada na máquina.

```csharp
// Quick sanity check – print the total number of warnings captured.
Console.WriteLine($"Total warnings captured: {warningCollector.Count}");
```

Uma contagem zero geralmente significa que:

1. Todas as fontes foram resolvidas (talvez a fonte *esteja* instalada localmente), ou
2. O documento não continha referências de fonte que precisassem de substituição.

---

## Armadilhas Comuns & Como Evitá‑las

| Armadilha | Por Que Acontece | Solução |
|-----------|------------------|---------|
| **Nenhum aviso aparece** | A fonte realmente existe no sistema, ou o documento usa apenas fontes internas. | Renomeie a fonte no arquivo fonte para algo impossível (ex.: `XYZ123`) e tente novamente. |
| **Avisos demais (ruído)** | Você está carregando muitos documentos em um loop sem limpar o coletor. | Reinstancie `WarningInfoCollection` para cada documento, ou chame `warningCollector.Clear()` após o processamento. |
| **Impacto de desempenho** | Registro excessivo em disco pode desacelerar o processamento em lote. | Armazene avisos em memória e grave em lote, ou use I/O assíncrono. |
| **Falta `using Aspose.Words.Loading;`** | A classe `LoadOptions` está nesse namespace. | Adicione a diretiva `using` ausente, como mostrado na Etapa 1. |

---

## Expandindo a Solução – Monitorando Outros Tipos de Aviso

Embora a substituição de fonte seja a mais visível, o Aspose.Words pode emitir avisos para:

- **Recursos obsoletos** (`WarningType.Deprecated`),
- **Possível perda de dados** (`WarningType.DataLoss`),
- **Formatos de arquivo não suportados** (`WarningType.UnsupportedFileFormat`).

Você pode ampliar o filtro na Etapa 3 para capturar esses também:

```csharp
if (warning.WarningType != WarningType.None)
{
    Console.WriteLine($"{warning.WarningType}: {warning.Description}");
}
```

Dessa forma você não está apenas **como monitorar fontes**, mas também **como obter avisos** para qualquer cenário que sua aplicação possa encontrar.

---

## Exemplo Completo Funcional (Pronto para Copiar‑Colar)

```csharp
using System;
using System.IO;
using System.Linq;
using System.Text.Json;
using Aspose.Words;
using Aspose.Words.Fonts;
using Aspose.Words.Loading;

class Program
{
    static void Main()
    {
        // Step 1 – Prepare a warning collector.
        WarningInfoCollection warningCollector = new WarningInfoCollection();
        LoadOptions loadOptions = new LoadOptions { WarningCallback = warningCollector };

        // Step 2 – Load the document (adjust the path to your file).
        string docPath = @"C:\Docs\unknownFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // Step 3 – Output font substitution warnings.
        foreach (WarningInfo warning in warningCollector)
        {
            if (warning.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Substituted font: {warning.Description}");
            }
        }

        // Optional Step 4 – Persist warnings to JSON.
        var fontWarnings = warningCollector
            .Where(w => w.WarningType == WarningType.FontSubstitution)
            .Select(w => new { Message = w.Description })
            .ToList();

        string json = JsonSerializer.Serialize(fontWarnings, new JsonSerializerOptions { WriteIndented = true });
        File.WriteAllText(@"C:\Logs\font-warnings.json", json);
        Console.WriteLine("Font warnings saved to font-warnings.json");

        // Step 5 – Quick sanity check.
        Console.WriteLine($"Total warnings captured: {warningCollector.Count}");
    }
}
```

**Execute:** Compile o projeto, execute, e você verá os avisos impressos e salvos. Essa é a resposta completa para **como obter avisos** e **como monitorar fontes** com Aspose.Words.

---

## Conclusão

Agora você sabe **como obter avisos** do Aspose.Words, especificamente para cenários de substituição de fonte, e aprendeu **como monitorar fontes** ao longo do processo de carregamento do documento. Ao anexar um `WarningCallback`, iterar os objetos `WarningInfo` coletados e, opcionalmente, persistir os dados, você obtém total transparência sobre eventos de fontes ausentes—uma capacidade essencial para qualquer pipeline de processamento de documentos.

Próximos passos? Experimente expandir o filtro de avisos para cobrir perdas de dados ou avisos de recursos obsoletos, ou integre o log JSON em um painel de monitoramento como Grafana. O mesmo padrão funciona para todos os tipos de aviso, então você estará bem preparado para ficar de olho em qualquer problema que o Aspose.Words lançar.

Feliz codificação, e que seus documentos sempre renderizem exatamente como você espera! 

---

<img src="font-warnings.png" alt="como obter avisos no Aspose.Words" style="max-width:100%;">

---

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}