---
category: general
date: 2026-06-20
description: Ative avisos de substituição de fontes em C# usando Aspose.Words. Aprenda
  como configurar LoadOptions, capturar avisos e lidar eficientemente com fontes ausentes.
draft: false
keywords:
- enable font substitution warnings
- Aspose.Words LoadOptions
- C# font substitution warnings
- document warning handling
- font substitution messages
language: pt
og_description: Ative avisos de substituição de fontes em C# com Aspose.Words. Este
  guia mostra como configurar LoadOptions, ler WarningInfo e exibir mensagens de fontes
  ausentes.
og_title: Ativar Avisos de Substituição de Fonte no C# – Guia Completo
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: Enable font substitution warnings in C# using Aspose.Words. Learn how
    to configure LoadOptions, capture warnings, and handle missing fonts efficiently.
  headline: Enable Font Substitution Warnings in C# with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Font Substitution
- Warnings
title: Ativar avisos de substituição de fontes no C# com Aspose.Words
url: /pt/net/programming-with-loadoptions/enable-font-substitution-warnings-in-c-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Habilitar Avisos de Substituição de Fonte em C# com Aspose.Words

Já se perguntou como **habilitar avisos de substituição de fonte** quando um documento Word referencia uma fonte que não está instalada no servidor? Você não está sozinho. Fontes ausentes podem corromper silenciosamente o layout de PDFs ou imagens gerados, e a única maneira de detectar isso cedo é ouvir os avisos emitidos pelo Aspose.Words.

Neste tutorial, percorreremos um exemplo prático que mostra exatamente como ativar esses avisos, extrair eles da coleção `WarningInfo` e imprimir mensagens significativas no console. Ao final, você saberá como configurar **Aspose.Words LoadOptions**, lidar com **avisos de substituição de fonte em C#** e manter seu pipeline de processamento de documentos à prova de falhas.

Também abordaremos alguns casos extremos — o que acontece se você suprimir os avisos, ou se precisar registrá‑los em vez de imprimi‑los — e forneceremos um exemplo de código completo, pronto para copiar e colar, que funciona com a versão mais recente do Aspose.Words para .NET (a partir da versão 24.10).

## O que você precisará

- .NET 6.0 ou superior (o código também funciona no .NET Framework 4.7+)
- Uma referência NuGet ao `Aspose.Words` (instale via `dotnet add package Aspose.Words`)
- Um arquivo Word que referencia uma fonte que você **não** tem instalada (por exemplo, `DocumentWithMissingFont.docx`)
- Um IDE decente (Visual Studio, Rider ou VS Code)

É isso — sem serviços extras, sem ferramentas proprietárias. Pronto? Vamos mergulhar.

## Etapa 1: Habilitar Avisos de Substituição de Fonte

A primeira coisa que você precisa fazer é informar ao Aspose.Words que deseja ser notificado quando ele substituir uma fonte ausente. Isso é feito através da propriedade `FontSettings` de um objeto `LoadOptions`. Por padrão, os avisos estão **desativados** para manter a API silenciosa, então precisamos ativá‑los manualmente.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

// Create LoadOptions and enable detailed font‑substitution warnings.
LoadOptions loadOpts = new LoadOptions
{
    // FontSettings is the gateway for all font‑related behavior.
    FontSettings = new FontSettings()
    // No extra code needed here; simply having a FontSettings instance
    // makes Aspose.Words collect font‑substitution warnings.
};
```

> **Por que isso funciona:** Quando `FontSettings` não é `null`, a biblioteca preenche automaticamente `Document.WarningInfo` com quaisquer entradas `WarningType.FontSubstitution` que encontrar ao carregar um documento. Pense nisso como ativar um “modo de depuração” para fontes.

## Etapa 2: Carregar o Documento com Opções Configuradas

Agora que a coleção de avisos está ativa, carregue seu documento usando o `LoadOptions` que acabamos de preparar. Se o documento contiver uma fonte ausente, o Aspose.Words substituirá por uma fonte padrão e enviará um aviso para a lista `WarningInfo`.

```csharp
// Path to a DOCX that references a font not present on the machine.
string docPath = @"C:\Samples\DocumentWithMissingFont.docx";

// Load the document while respecting the LoadOptions we set up.
Document doc = new Document(docPath, loadOpts);
```

> **Dica profissional:** Se você estiver processando muitos arquivos em um loop, reutilize a mesma instância de `LoadOptions` — criá‑la uma única vez economiza alguns milissegundos por iteração.

## Etapa 3: Iterar sobre WarningInfo e Exibir Mensagens de Substituição de Fonte

Depois que o documento for carregado, a coleção `WarningInfo` contém todos os avisos que ocorreram durante o carregamento. Estamos interessados apenas em `WarningType.FontSubstitution`, então filtramos adequadamente.

```csharp
foreach (WarningInfo warning in doc.WarningInfo)
{
    if (warning.Type == WarningType.FontSubstitution)
        Console.WriteLine($"Substituted: {warning.Description}");
}
```

Executar o trecho acima em um documento que referencia a fonte ausente “Papyrus” pode gerar uma saída semelhante a:

```
Substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
Substituted: Font 'Comic Sans MS' is not installed. Substituted with 'Times New Roman'.
```

Essas são as **mensagens de substituição de fonte** que você procurava — claras, acionáveis e prontas para serem registradas ou enviadas a um sistema de alerta.

## Exemplo Completo Funcional

Abaixo está um programa de console autônomo que reúne tudo. Copie‑e‑cole em um novo `.csproj` e clique em **Run**.

```csharp
// ---------------------------------------------------------------
// Enable Font Substitution Warnings – Complete Example
// ---------------------------------------------------------------

using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

class Program
{
    static void Main()
    {
        // 1️⃣ Configure LoadOptions to capture font‑substitution warnings.
        LoadOptions loadOpts = new LoadOptions
        {
            FontSettings = new FontSettings()   // Enabling warning collection.
        };

        // 2️⃣ Load the target document (adjust the path to match your environment).
        string docPath = @"C:\Samples\DocumentWithMissingFont.docx";
        Document doc = new Document(docPath, loadOpts);

        // 3️⃣ Process the warning collection.
        Console.WriteLine("=== Font Substitution Warnings ===");
        bool anyWarnings = false;

        foreach (WarningInfo warning in doc.WarningInfo)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                anyWarnings = true;
                Console.WriteLine($"Substituted: {warning.Description}");
            }
        }

        if (!anyWarnings)
            Console.WriteLine("No font substitution warnings were generated.");

        // Optional: keep the console window open.
        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

### Saída Esperada

Se o documento referenciar fontes que não estão instaladas, você verá algo semelhante a:

```
=== Font Substitution Warnings ===
Substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
Substituted: Font 'Courier New' is not installed. Substituted with 'Times New Roman'.
Press any key to exit...
```

Se todas as fontes estiverem presentes na máquina, o programa simplesmente imprimirá:

```
=== Font Substitution Warnings ===
No font substitution warnings were generated.
Press any key to exit...
```

## Armadilhas Comuns e Dicas Profissionais

| Problema | Por que acontece | Como corrigir / evitar |
|----------|------------------|------------------------|
| **Avisos desaparecem** | Você limpou `FontSettings` ou usou um `LoadOptions` sem ele. | Sempre instancie `FontSettings` mesmo que não modifique nenhuma propriedade. |
| **Muitos avisos** | O documento usa muitas fontes exóticas. | Considere adicionar uma pasta de fontes personalizada ao `FontSettings` via `SetFontsFolder` para reduzir substituições. |
| **Queda de desempenho em loop apertado** | Recriar `LoadOptions` a cada iteração adiciona sobrecarga. | Reutilize uma única instância de `LoadOptions` em todos os documentos. |
| **Saída de console ausente** | Executando dentro de um aplicativo GUI onde `Console.WriteLine` é ignorado. | Redirecione os avisos para um logger (`ILogger`) ou escreva em um arquivo. |

### Tratando Avisos em um Serviço Real‑World

Em uma API web você provavelmente não quer escrever no console. Em vez disso, canalize os avisos para um log estruturado:

```csharp
var logger = LoggerFactory.Create(builder => builder.AddConsole()).CreateLogger<Program>();

foreach (WarningInfo warning in doc.WarningInfo)
{
    if (warning.Type == WarningType.FontSubstitution)
        logger.LogWarning("Font substitution: {Description}", warning.Description);
}
```

Dessa forma você mantém o **tratamento de avisos de documento** enquanto mantém seu serviço limpo.

## Extendendo o Exemplo

- **Capture outros tipos de aviso** (por exemplo, `WarningType.UnknownFileFormat`) removendo o filtro `if`.
- **Salve um relatório** de todos os avisos em JSON para análises posteriores.
- **Forçar uma fonte de fallback específica** definindo `FontSettings.SubstitutionSettings.DefaultFontName`.

Todas essas são extensões naturais depois que você domina **habilitar avisos de substituição de fonte**.

## Conclusão

Mostramos como **habilitar avisos de substituição de fonte** em C# usando Aspose.Words, desde a configuração de `LoadOptions` até a iteração sobre `WarningInfo` e a impressão de mensagens amigáveis. Seguindo os passos acima, você pode proteger seus pipelines de processamento de documentos contra alterações silenciosas de layout causadas por fontes ausentes.

Em seguida, tente adicionar uma pasta de fontes personalizada, registrar os avisos em um arquivo ou até enviá‑los para um painel de monitoramento. O mesmo padrão funciona para qualquer cenário de **tratamento de avisos de documento**, seja convertendo para PDF, renderizando imagens ou realizando mesclagem de correspondência.

Tem perguntas sobre **avisos de substituição de fonte em C#** ou quer compartilhar uma solução engenhosa? Deixe um comentário abaixo — feliz codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Habilitar Avisos de Substituição de Fonte no Aspose.Words – Guia Completo](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [Como Detectar Fontes no Aspose.Words – Lidar com Avisos e Configurações](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Capturar Avisos de Substituição de Fonte em Java com Aspose.Words – Guia Completo](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}