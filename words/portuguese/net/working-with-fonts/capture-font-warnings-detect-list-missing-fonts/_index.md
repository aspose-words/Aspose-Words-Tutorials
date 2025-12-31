---
category: general
date: 2025-12-31
description: Capture avisos de fontes no Aspose.Words para detectar fontes ausentes
  e listar as fontes ausentes em seu aplicativo .NET. Aprenda uma solução passo a
  passo em C#.
draft: false
keywords:
- capture font warnings
- detect missing fonts
- list missing fonts
- Aspose.Words font warnings
- C# document loading
language: pt
og_description: Capture avisos de fontes no Aspose.Words para detectar fontes ausentes
  e listar fontes ausentes. Guia completo em C# com código e dicas.
og_title: Capturar avisos de fonte – detectar e listar fontes ausentes
tags:
- Aspose.Words
- C#
- .NET
- Font Substitution
title: Capturar Avisos de Fonte – Detectar e Listar Fontes Ausentes
url: /pt/net/working-with-fonts/capture-font-warnings-detect-list-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Capturar Avisos de Fonte – Detectar e Listar Fontes Ausentes

Já precisou **capturar avisos de fonte** ao carregar um documento Word, mas não sabia como expor os detalhes das fontes ausentes? Você não está sozinho. Em muitos projetos reais, fontes ausentes causam falhas de layout, e sem avisos adequados você acaba perseguindo bugs fantasmas.  

Neste tutorial vamos mostrar como **detectar fontes ausentes** e **listar fontes ausentes** usando Aspose.Words para .NET. Ao final, você terá um trecho de C# pronto‑para‑executar que imprime cada aviso de substituição, para que você possa registrar, alertar ou até substituir fontes automaticamente.

---

## Por que Capturar Avisos de Fonte é Importante

Quando o Aspose.Words abre um DOCX que referencia uma fonte não instalada no servidor, ele silenciosamente substitui por uma alternativa. O documento parece estar ok, mas a fidelidade visual é comprometida — imagine o logotipo da sua marca corporativa renderizado com a tipografia errada.  

Capturar esses avisos permite que você:

* **Mantenha a consistência da marca** – você sabe exatamente quais fontes estão faltando.  
* **Automatize a remediação** – substitua fontes ausentes programaticamente.  
* **Audite a conformidade** – gere relatórios para revisões legais ou de design.  

Em resumo, **capturar avisos de fonte** é a primeira linha de defesa contra substituições silenciosas de fontes.

---

## Configurar LoadOptions para Detectar Fontes Ausentes

A chave para expor os avisos é a propriedade `LoadOptions.FontSubstitutionWarning`. Por padrão ela está definida como `None`, o que significa que o Aspose.Words engole as mensagens. Alterá‑la para `All` indica à biblioteca que registre cada evento de substituição.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Configure LoadOptions so every font‑substitution warning is stored
LoadOptions loadOptions = new LoadOptions
{
    // Provide a fresh FontSettings instance – you can also pre‑load custom fonts here
    FontSettings = new FontSettings(),

    // This flag tells Aspose.Words to capture *all* font‑related warnings
    FontSubstitutionWarning = FontSubstitutionWarning.All
};
```

> **Dica:** Se você já possui uma pasta de fontes personalizada, atribua‑a a `FontSettings.SetFontsFolder("path")` antes de carregar o documento. Dessa forma, você pode **detectar fontes ausentes** que não estejam no diretório do sistema.

---

## Carregar o Documento e Listar Fontes Ausentes

Agora que o `LoadOptions` está configurado, o próximo passo é carregar o arquivo Word. O construtor aceita o objeto de opções, e qualquer substituição será registrada na `WarningInfoCollection` do documento.

```csharp
// Path to the DOCX that may contain unknown fonts
string docPath = @"C:\Docs\UnknownFonts.docx";

// Load the document with the warning‑capture options
Document document = new Document(docPath, loadOptions);
```

Se o arquivo referencia fontes que não estão disponíveis, cada fonte ausente gera uma entrada `WarningInfo`. Você pode **listar fontes ausentes** iterando sobre essa coleção.

```csharp
// Iterate through the warnings and output them to the console
foreach (WarningInfo warning in document.WarningInfoCollection)
{
    // The warning.Type will be FontSubstitution, and Description contains details
    Console.WriteLine($"{warning.Type}: {warning.Description}");
}
```

A saída típica se parece com:

```
FontSubstitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
FontSubstitution: Font 'MyCustomFont' was not found. Substituted with 'Times New Roman'.
```

Cada linha informa exatamente qual fonte estava ausente, atendendo ao requisito de **listar fontes ausentes**.

---

## Ler e Interpretar a WarningInfoCollection

A `WarningInfoCollection` pode conter diferentes tipos de aviso (por exemplo, `DocumentStructure`, `ImageLoading`). Para focar apenas em questões de fonte, filtre por `WarningType.FontSubstitution`.

```csharp
var fontWarnings = document.WarningInfoCollection
                           .Where(w => w.Type == WarningType.FontSubstitution);

foreach (var fw in fontWarnings)
{
    Console.WriteLine($"Missing font detected: {fw.Description}");
}
```

Por que filtrar? Porque um documento grande pode também gerar avisos sobre imagens corrompidas ou recursos não suportados. Ao reduzir a coleção, você elimina ruído e mantém a saída de **capturar avisos de fonte** limpa.

---

## Exemplo Completo – Capturando Avisos de Fonte em Ação

Abaixo está o programa completo e autocontido que você pode inserir em qualquer projeto console .NET. Ele demonstra cada passo, desde a configuração de `LoadOptions` até a impressão de uma lista organizada de fontes ausentes.

```csharp
// ------------------------------------------------------------
// Complete C# example: Capture Font Warnings, Detect & List Missing Fonts
// ------------------------------------------------------------
using System;
using System.Linq;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare LoadOptions to capture all font‑substitution warnings
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings(),
            FontSubstitutionWarning = FontSubstitutionWarning.All
        };

        // OPTIONAL: If you have a custom font folder, point Aspose.Words to it
        // loadOptions.FontSettings.SetFontsFolder(@"C:\MyFonts", true);

        // 2️⃣ Load the document with the configured options
        string docPath = @"C:\Docs\UnknownFonts.docx";
        Document doc = new Document(docPath, loadOptions);

        // 3️⃣ Filter only font‑substitution warnings
        var fontWarnings = doc.WarningInfoCollection
                               .Where(w => w.Type == WarningType.FontSubstitution);

        // 4️⃣ Output the missing‑font details
        Console.WriteLine("=== Missing Font Report ===");
        foreach (var warning in fontWarnings)
        {
            Console.WriteLine(warning.Description);
        }

        // 5️⃣ If no warnings were found, let the user know
        if (!fontWarnings.Any())
            Console.WriteLine("All referenced fonts are available – no warnings captured.");
    }
}
```

**Saída esperada no console**

```
=== Missing Font Report ===
Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Font 'MyCustomFont' was not found. Substituted with 'Times New Roman'.
```

Se o documento não contiver fontes ausentes, você verá:

```
All referenced fonts are available – no warnings captured.
```

---

## Casos de Borda Comuns & Como Lidar com Eles

| Situação | Por que Acontece | Correção Recomendada |
|-----------|----------------|-----------------|
| **Documento usa uma fonte OpenType incorporada** | O Aspose.Words pode ler fontes incorporadas, mas somente se o arquivo não estiver corrompido. | Verifique o DOCX no Word primeiro; re‑incorpore a fonte se necessário. |
| **Grande quantidade de avisos** (ex.: 200+ fontes ausentes) | Importações em massa de sistemas legados costumam referenciar um amplo conjunto de fontes. | Processar os avisos em lote: armazená‑los em um banco de dados e, depois, executar um script de instalação de fontes. |
| **WarningInfoCollection está vazia** | Ou o documento tem todas as fontes, ou `FontSubstitutionWarning` ficou em `None`. | Verifique novamente a configuração de `LoadOptions` e assegure‑se de estar carregando o caminho de arquivo correto. |
| **Fontes personalizadas localizadas em um compartilhamento de rede** | Latência de rede pode causar timeouts durante a busca de fontes. | Pré‑carregue as fontes em `FontSettings` usando `SetFontsFolder` e defina `CacheFontData = true`. |

Essas dicas ajudam você a **detectar fontes ausentes** de forma confiável, mesmo em ambientes complexos.

---

## Ilustração

![exemplo de captura de avisos de fonte](https://example.com/images/capture-font-warnings.png "exemplo de captura de avisos de fonte")

*A captura de tela mostra uma execução no console onde duas fontes ausentes são relatadas.*

---

## Próximos Passos – Indo Além do Relatório Simples

Agora que você pode **capturar avisos de fonte**, considere automatizar a remediação:

1. **Substituição Automática de Fonte** – Substitua fontes ausentes por um fallback aprovado pela empresa modificando `FontSettings.SubstitutionSettings`.  
2. **Log para um Sistema de Monitoramento** – Direcione as mensagens de aviso para Serilog, ELK ou Azure Application Insights.  
3. **Relatórios para Usuários** – Gere um resumo em HTML ou PDF para que designers revisem quais fontes precisam ser instaladas.  

Todas essas extensões se baseiam na mesma fundação que abordamos: configurar `LoadOptions`, carregar o documento e ler `WarningInfoCollection`.

---

## Conclusão

Você acabou de aprender como **capturar avisos de fonte** no Aspose.Words, **detectar fontes ausentes** e **listar fontes ausentes** com uma saída limpa e amigável ao console. A abordagem é direta, requer apenas algumas linhas de C#, e funciona com qualquer versão .NET que suporte Aspose.Words 23.x ou posterior.  

Experimente em um DOCX de exemplo que referencia uma fonte que você desinstalou deliberadamente – você verá os avisos aparecerem instantaneamente. A partir daí, pode decidir instalar as tipografias faltantes, substituí‑las programaticamente ou simplesmente registrar o problema para revisão posterior.

Boa codificação, e que seus documentos sempre renderizem com as fontes corretas!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}