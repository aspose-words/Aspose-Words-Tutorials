---
category: general
date: 2026-06-02
description: como lidar com fontes no .NET – detectar fontes ausentes e rastrear alterações
  de fontes usando LoadOptions e FontSettings. Aprenda uma solução completa e executável.
draft: false
keywords:
- how to handle fonts
- detect missing fonts
- track font changes
language: pt
og_description: como lidar com fontes no .NET – detectar fontes ausentes e acompanhar
  alterações de fontes. Siga este guia passo a passo para uma solução completa, pronta
  para usar.
og_title: como lidar com fontes no .NET – detectar fontes ausentes
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: how to handle fonts in .NET – detect missing fonts and track font changes
    using LoadOptions and FontSettings. Learn a complete, runnable solution.
  headline: how to handle fonts in .NET – detect missing fonts
  type: TechArticle
tags:
- .NET
- Aspose.Words
- FontSettings
title: como lidar com fontes no .NET – detectar fontes ausentes
url: /pt/net/working-with-fonts/how-to-handle-fonts-in-net-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# como lidar com fontes no .NET – detectar fontes ausentes

Já se perguntou **como lidar com fontes** quando um documento Word referencia uma tipografia que não está instalada na máquina? Você não está sozinho. Fontes ausentes podem transformar um relatório bem elaborado em uma bagunça ilegível, e sem avisos adequados você pode nunca saber o que foi substituído.  

Neste tutorial vamos mostrar exatamente **como lidar com fontes** detectando fontes ausentes **e** rastreando alterações de fontes em tempo de execução. Ao final você terá um aplicativo console autônomo que registra cada substituição, para nunca mais ser surpreendido por um misterioso Helvetica aparecendo onde deveria estar Times New Roman.

> **O que você receberá:** um exemplo de código completo, pronto para copiar‑e‑colar, uma explicação de cada linha, dicas para projetos reais e uma visão rápida dos casos limites que você pode encontrar.

## Pré‑requisitos

- .NET 6.0 ou superior (o exemplo usa um `Program.cs` de nível superior para simplificar)  
- Aspose.Words for .NET 23.9 ou mais recente – você pode obtê‑lo via NuGet com `dotnet add package Aspose.Words`  
- Um documento Word que intencionalmente referencia uma fonte que você não possui (por exemplo, `MissingFont.docx`)  

Nenhuma outra biblioteca é necessária.

![Diagrama mostrando como o LoadOptions flui para FontSettings e o evento de aviso de substituição – exemplo de como lidar com fontes no .NET](https://example.com/images/font‑handling‑flow.png "exemplo de como lidar com fontes no .NET")

## Etapa 1: Configurar LoadOptions com FontSettings  

A primeira coisa que precisamos é de um objeto `LoadOptions` que indique ao Aspose.Words para observar problemas de fontes.  

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System;

// Create LoadOptions and attach a fresh FontSettings instance.
var loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};
```

**Por que isso importa:** `LoadOptions` é o guardião quando um documento é lido do disco. Ao fornecer um `FontSettings` personalizado, ganhamos um ponto de intercepção no mecanismo interno de resolução de fontes, que é a única forma de **detectar fontes ausentes** antes que o documento seja renderizado.

## Etapa 2: Inscrever‑se no evento SubstitutionWarning  

Aspose.Words dispara um evento `SubstitutionWarning` toda vez que não consegue encontrar a fonte exata solicitada. Vamos registrar os detalhes para que você possa ver quais fontes foram solicitadas e quais foram realmente usadas.

```csharp
// Hook into the warning event – this is where we “track font changes”.
loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    // e.RequestedFontName – the name the document asked for.
    // e.SubstitutedFontName – the name Aspose.Words fell back to.
    // e.WarningType – tells you why the substitution happened.
    Console.WriteLine(
        $"[Font Substitution] Requested: {e.RequestedFontName}, " +
        $"Used: {e.SubstitutedFontName}, Reason: {e.WarningType}");
};
```

**Por que escutamos:** Sem esse listener você nunca saberia que uma substituição ocorreu. O evento fornece um histórico completo, atendendo ao requisito de “rastrear alterações de fontes”.

## Etapa 3: Carregar o Documento usando Nossas Opções Configuradas  

Agora realmente lemos o arquivo. Como passamos o `loadOptions`, o Aspose.Words disparará o evento de aviso para qualquer fonte ausente que encontrar.

```csharp
// Replace the path with the location of your test document.
string docPath = @"YOUR_DIRECTORY\MissingFont.docx";

Document doc = new Document(docPath, loadOptions);
```

É isso – o documento está carregado e quaisquer problemas de fontes já foram impressos no console.

## Etapa 4: (Opcional) Verificar as Fontes Substituídas no Documento  

Se quiser confirmar quais fontes terminaram no PDF ou DOCX final, você pode percorrer a coleção de fontes do documento:

```csharp
Console.WriteLine("\n--- Fonts actually used in the document ---");
foreach (FontInfo fontInfo in doc.FontInfos)
{
    Console.WriteLine($"{fontInfo.FontFamilyName} – {fontInfo.FontStyle}");
}
```

Executar isso após o carregamento listará cada fonte que o mecanismo decidiu incorporar ou referenciar. Útil quando precisar gerar um relatório para equipes de QA.

## Exemplo Completo Funcional  

Copie o bloco abaixo para um novo projeto console (`dotnet new console`) e execute. O programa exibirá cada substituição e, em seguida, listará as fontes que sobreviveram ao carregamento.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // Step 1: Prepare LoadOptions with FontSettings.
        // -------------------------------------------------
        var loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // -------------------------------------------------
        // Step 2: Hook the substitution warning event.
        // -------------------------------------------------
        loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
        {
            Console.WriteLine(
                $"[Font Substitution] Requested: {e.RequestedFontName}, " +
                $"Used: {e.SubstitutedFontName}, Reason: {e.WarningType}");
        };

        // -------------------------------------------------
        // Step 3: Load the document (this triggers warnings).
        // -------------------------------------------------
        string docPath = @"YOUR_DIRECTORY\MissingFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // -------------------------------------------------
        // Step 4 (optional): List fonts actually used.
        // -------------------------------------------------
        Console.WriteLine("\n--- Fonts actually used in the document ---");
        foreach (FontInfo fontInfo in doc.FontInfos)
        {
            Console.WriteLine($"{fontInfo.FontFamilyName} – {fontInfo.FontStyle}");
        }

        Console.WriteLine("\nDone. Press any key to exit.");
        Console.ReadKey();
    }
}
```

### Saída Esperada  

Se `MissingFont.docx` solicitar *“Comic Sans MS”* (que não está instalada) você verá algo como:

```
[Font Substitution] Requested: Comic Sans MS, Used: Arial, Reason: FontNotFound
[Font Substitution] Requested: Times New Roman, Used: Times New Roman, Reason: None

--- Fonts actually used in the document ---
Arial – Regular
Times New Roman – Regular
```

A primeira linha prova que **detectamos fontes ausentes** e **rastreamos alterações de fontes**. A segunda linha mostra uma substituição que não precisou acontecer (nenhum aviso, porque a fonte existia).

## Armadilhas Comuns & Dicas Profissionais  

| Armadilha | O que Acontece | Como Corrigir / Evitar |
|-----------|----------------|------------------------|
| **Nenhum evento de aviso é disparado** | Você pode achar que a API está quebrada. | Certifique‑se de *atribuir* o `FontSettings` ao `LoadOptions` **antes** de carregar o documento. O hook do evento deve ser anexado **antes** da chamada `new Document(...)`. |
| **Fontes substituídas ainda ficam erradas** | Aspose.Words recorre a uma fonte genérica que não combina com o estilo. | Forneça uma pasta de fontes personalizada via `fontSettings.SetFontsFolder(@"C:\MyFonts", true)`. Isso dá ao mecanismo mais opções antes de usar a fonte genérica. |
| **Impacto de desempenho em documentos grandes** | A varredura de cada fonte pode acrescentar alguns milissegundos. | Cache o objeto `FontSettings` se você carregar muitos documentos em sequência. Reutilizar a mesma instância evita reler as tabelas de fontes do sistema. |
| **Saída do console se perde em apps GUI** | Você não verá os avisos. | Redirecione o evento para um logger (ex.: `Serilog`) ou grave em um arquivo: `File.AppendAllText("font-warnings.log", …)`. |

## Expandindo a Solução  

- **Exportar para PDF com fontes incorporadas** – após o carregamento, chame `doc.Save("output.pdf", SaveOptions.CreateSaveOptions(SaveFormat.Pdf));` e assegure‑se de definir `PdfSaveOptions.FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll;`.  
- **Processamento em lote** – envolva a lógica de carregamento em um `foreach` sobre uma pasta de arquivos DOCX. Registre os avisos de cada arquivo em um CSV para fins de auditoria.  
- **Interface amigável** – exponha a mesma lógica por trás de um botão em um app WinForms/WPF, exibindo os avisos em um `ListBox`.

## Conclusão  

Percorremos **como lidar com fontes** no .NET configurando `LoadOptions`, inscrevendo‑nos no evento `SubstitutionWarning` e, finalmente, carregando o documento. O exemplo não só **detecta fontes ausentes** como também **rastreia alterações de fontes**, permitindo auditar cada substituição.  

Teste com seus próprios documentos, ajuste o caminho da pasta de fontes e nunca mais seja surpreendido por uma troca inesperada de fontes. Se este guia foi útil, considere explorar tópicos relacionados como *“incorporar fontes personalizadas em PDF com Aspose.Words”* ou *“criar uma estratégia de fallback de fontes para apps .NET multiplataforma.”*  

Bom código, e que seus documentos sempre renderizem exatamente como você pretende!

## O que Você Deve Aprender a Seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [How to Load DOCX and Detect Missing Fonts – Complete C# Guide](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)
- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [How to Use LoadOptions in Aspose.Words – Complete Guide](/words/english/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}