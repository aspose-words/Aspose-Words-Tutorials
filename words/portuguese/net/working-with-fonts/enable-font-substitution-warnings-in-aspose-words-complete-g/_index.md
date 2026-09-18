---
category: general
date: 2026-01-11
description: Ative avisos de substituição de fontes para detectar fontes ausentes
  em seus documentos .NET. Aprenda como obter o nome da fonte ausente e listar fontes
  ausentes com Aspose.Words.
draft: false
keywords:
- enable font substitution warnings
- detect missing fonts
- get missing font name
- list missing fonts
language: pt
og_description: Ative avisos de substituição de fontes no Aspose.Words para detectar
  fontes ausentes, obter o nome da fonte ausente e listar fontes ausentes em seus
  documentos.
og_title: Habilitar Avisos de Substituição de Fonte – Tutorial C# Passo a Passo
tags:
- Aspose.Words
- C#
- Document Processing
title: Ativar Avisos de Substituição de Fonte no Aspose.Words – Guia Completo
url: /pt/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ativar Avisos de Substituição de Fonte – Guia Completo

Já se perguntou por que um documento Word parece um pouco diferente depois de carregá‑lo em um servidor? É provável que uma fonte usada pelo autor original não esteja disponível na sua máquina, e o Aspose.Words a substituiu silenciosamente pela mais próxima. **Ativar avisos de substituição de fonte** e você saberá instantaneamente quais fontes estão ausentes, por que foram substituídas e como agir com base nessas informações.

Neste tutorial, percorreremos um exemplo prático, de ponta a ponta, que mostra como **detectar fontes ausentes**, obter o **get missing font name**, e até **listar fontes ausentes** para relatórios. Sem enrolação, apenas uma solução clara que você pode inserir em qualquer projeto .NET hoje.

---

## O que você aprenderá

- Como configurar `LoadOptions` para que o Aspose.Words emita avisos detalhados.
- O código exato necessário para carregar um documento e enumerar avisos relacionados a fontes.
- Formas de extrair o nome da fonte ausente e sua substituição, e então gerar um relatório organizado.
- Dicas para lidar com casos extremos, como documentos com dezenas de fontes ausentes ou pastas de fontes personalizadas.

### Pré‑requisitos

- .NET 6+ (o código também funciona com .NET Framework 4.7+)
- Aspose.Words for .NET 23.10 ou mais recente (você pode obtê‑lo via NuGet)
- Um DOCX de exemplo que referencia uma fonte que você não tem instalada (vamos chamá‑lo de `MissingFont.docx`)

Se você tem esses requisitos, vamos mergulhar.

---

## Etapa 1: Configurar LoadOptions para Ativar Avisos de Substituição de Fonte  

A primeira coisa que você precisa fazer é dizer ao Aspose.Words que você se importa com fontes ausentes. Por padrão, a biblioteca registra avisos apenas internamente. Definir `SubstitutionWarningLevel` como `Typical` (ou `All` para a saída mais detalhada) ativa o recurso.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Create a new LoadOptions instance
LoadOptions loadOptions = new LoadOptions();

// Attach a FontSettings object so we can tweak font‑related behavior
loadOptions.FontSettings = new FontSettings();

// Enable warnings for typical font substitutions (covers most real‑world cases)
loadOptions.FontSettings.SubstitutionWarningLevel = FontSubstitutionWarningLevel.Typical;
```

**Por que isso importa:**  
Quando `SubstitutionWarningLevel` está definido, toda vez que o Aspose.Words não consegue encontrar uma fonte referenciada ele adiciona um `FontSubstitutionWarning` à coleção `Warnings` do documento. Essa coleção é a única maneira confiável de **detectar fontes ausentes** sem analisar o documento manualmente.

> **Dica de especialista:** Se você está lidando com um lote de documentos e quer ter absoluta certeza de capturar todas as substituições, use `FontSubstitutionWarningLevel.All`. É um pouco mais verboso, mas garante que nenhum aviso passe despercebido.

## Etapa 2: Carregar o Documento usando as Opções Configuradas  

Agora que o sistema de avisos está preparado, carregue seu DOCX com o `LoadOptions` que acabamos de configurar. O caminho pode ser absoluto ou relativo; apenas certifique‑se de que o arquivo exista.

```csharp
// Path to the DOCX that references a font you don’t have
string docPath = @"C:\Docs\MissingFont.docx";

// Load the document while respecting our warning configuration
Document document = new Document(docPath, loadOptions);
```

**O que está acontecendo nos bastidores?**  
O Aspose.Words analisa o XML do documento, resolve cada elemento `<w:font>` e verifica o catálogo de fontes do sistema (além de quaisquer pastas personalizadas que você possa ter adicionado ao `FontSettings`). Quando não consegue localizar uma fonte, registra um aviso — exatamente o que precisamos para **listar fontes ausentes** mais tarde.

## Etapa 3: Iterar sobre os Avisos e Extrair Detalhes da Fonte Ausente  

Com o documento na memória, a coleção `Warnings` contém cada `FontSubstitutionWarning`. Vamos percorrê‑la, filtrar pelo tipo correto e imprimir um relatório amigável.

```csharp
Console.WriteLine("=== Missing Font Report ===");
foreach (WarningInfo warning in document.Warnings)
{
    // Only interested in font substitution warnings
    if (warning is FontSubstitutionWarning fontWarning)
    {
        // The name of the font that was missing
        string missingFont = fontWarning.FontName;

        // The font Aspose.Words used instead
        string substitutedFont = fontWarning.SubstitutedFontName;

        Console.WriteLine($"Missing font: {missingFont}");
        Console.WriteLine($"Substituted with: {substitutedFont}");
        Console.WriteLine(new string('-', 30));
    }
}
```

**Saída esperada** (supondo que o documento de origem referencia `MyCustomFont` que não está instalado):

```
=== Missing Font Report ===
Missing font: MyCustomFont
Substituted with: Arial
------------------------------
Missing font: FancyScript
Substituted with: Times New Roman
------------------------------
```

Observe como cada entrada fornece tanto o **get missing font name** (`MyCustomFont`) quanto a fonte de substituição (`Arial`). Essa é exatamente a informação que você precisa para decidir se deve incorporar a fonte original, solicitar ao autor uma substituição ou simplesmente aceitar a substituição.

## Etapa 4: Opcional – Coletar os Dados em uma Lista para Processamento Posterior  

Se precisar exportar o relatório para CSV, enviá‑lo via API, ou apenas mantê‑lo na memória para uso futuro, você pode armazenar os avisos em uma lista fortemente tipada.

```csharp
// Define a simple DTO to hold the warning details
public class MissingFontInfo
{
    public string MissingFont { get; set; }
    public string SubstitutedFont { get; set; }
}

// Build the list
List<MissingFontInfo> missingFonts = new List<MissingFontInfo>();

foreach (WarningInfo warning in document.Warnings)
{
    if (warning is FontSubstitutionWarning fsw)
    {
        missingFonts.Add(new MissingFontInfo
        {
            MissingFont = fsw.FontName,
            SubstitutedFont = fsw.SubstitutedFontName
        });
    }
}

// Example: write to a CSV (requires System.IO)
var csvLines = missingFonts.Select(f => $"{f.MissingFont},{f.SubstitutedFont}");
File.WriteAllLines(@"C:\Docs\MissingFontsReport.csv", csvLines);
```

Agora você tem **list missing fonts** em um formato que qualquer sistema downstream pode consumir. Seja alimentando um painel ou gerando um log de auditoria, os dados estão prontos.

## Etapa 5: Lidando com Casos Limite e Armadilhas Comuns  

### Várias Fontes Ausentes em uma Única Execução  

Modelos corporativos grandes frequentemente referenciam dezenas de fontes personalizadas. A coleção de avisos pode ficar grande, mas o padrão de iteração mostrado acima escala linearmente, portanto o desempenho não é um problema. Apenas lembre‑se de manter a saída legível — agrupar por página ou estilo pode ser útil se precisar de uma análise mais profunda.

### Pastas de Fontes Personalizadas  

Se você armazena fontes em um diretório não padrão (por exemplo, um compartilhamento de rede), informe ao Aspose.Words onde procurar:

```csharp
loadOptions.FontSettings.SetFontsFolder(@"\\fileserver\SharedFonts", recursive: true);
```

Definir isso *antes* de carregar o documento dá à biblioteca a chance de encontrar as fontes, o que pode eliminar alguns avisos completamente.

### Suprimindo Avisos Específicos  

Às vezes você sabe que uma substituição específica é aceitável (por exemplo, uma fonte decorativa que você não se importa de substituir). Você pode filtrá‑las depois:

```csharp
missingFonts = missingFonts
    .Where(f => f.MissingFont != "DecorativeFont")
    .ToList();
```

### Compatibilidade de Versão  

O enum `FontSubstitutionWarningLevel` tem sido estável desde o Aspose.Words 20.12. Se você estiver em uma versão mais antiga, pode ser necessário atualizar para acessar o recurso de nível de aviso.

## Exemplo Completo Funcional  

Abaixo está o programa completo, pronto‑para‑executar, que incorpora todas as etapas acima. Cole‑o em um novo projeto de console, adicione o pacote NuGet Aspose.Words e aponte `docPath` para um documento que referencia uma fonte ausente.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    // DTO for storing missing font info
    public class MissingFontInfo
    {
        public string MissingFont { get; set; }
        public string SubstitutedFont { get; set; }
    }

    class Program
    {
        static void Main()
        {
            // 1️⃣ Configure LoadOptions to enable font substitution warnings
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSubstitutionWarningLevel.Typical;

            // Optional: add a custom fonts folder
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", true);

            // 2️⃣ Load the document with the above options
            string docPath = @"C:\Docs\MissingFont.docx";
            Document doc = new Document(docPath, loadOptions);

            // 3️⃣ Gather warnings into a list
            List<MissingFontInfo> missingFonts = new List<MissingFontInfo>();
            foreach (WarningInfo warning in doc.Warnings)
            {
                if (warning is FontSubstitutionWarning fsw)
                {
                    missingFonts.Add(new MissingFontInfo
                    {
                        MissingFont = fsw.FontName,
                        SubstitutedFont = fsw.SubstitutedFontName
                    });
                }
            }

            // 4️⃣ Output a human‑readable report
            Console.WriteLine("=== Missing Font Report ===");
            foreach (var info in missingFonts)
            {
                Console.WriteLine($"Missing font: {info.MissingFont}");
                Console.WriteLine($"Substituted with: {info.SubstitutedFont}");
                Console.WriteLine(new string('-', 30));
            }

            // 5️⃣ (Optional) Export to CSV for further analysis
            var csvLines = missingFonts.Select(f => $"{f.MissingFont},{f.SubstitutedFont}");
            File.WriteAllLines(@"C:\Docs\MissingFontsReport.csv", csvLines);

            Console.WriteLine("Report saved to C:\\Docs\\MissingFontsReport.csv");
        }
    }
}
```

Executar este programa **ativará avisos de substituição de fonte**, **detectará fontes ausentes**, **obterá o nome da fonte ausente** e **listará fontes ausentes** tanto no console quanto em um arquivo CSV.

## Conclusão  

Acabamos de cobrir tudo o que você precisa para **ativar avisos de substituição de fonte** no Aspose.Words, desde a configuração inicial até a extração de uma lista limpa de fontes ausentes. Seguindo as etapas acima, você poderá auditar seus documentos, garantir a fidelidade visual e evitar surpresas desagradáveis ao renderizar em um servidor.

Em seguida, você pode querer explorar:

- **Incorporar fontes ausentes** diretamente no PDF ou DOCX de saída (use `FontSettings.EmbeddedFonts`).
- **Automatizar a instalação de fontes** em agentes de build com base no relatório gerado.
- **Integrar com pipelines de CI** para falhar builds quando fontes críticas estiverem ausentes.

Experimente isso, e você transformará um simples sistema de avisos em um fluxo de trabalho completo de gerenciamento de fontes.

Feliz codificação, e que todas as suas fontes sejam encontradas!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}