---
category: general
date: 2026-06-17
description: Gerencie a substituição de fontes no Aspose.Words e detecte fontes ausentes
  rapidamente com este tutorial passo a passo para desenvolvedores .NET.
draft: false
keywords:
- handle font substitution
- detect missing fonts
- how to detect missing fonts
language: pt
og_description: Gerencie a substituição de fontes no Aspose.Words e aprenda a detectar
  fontes ausentes em seus documentos com exemplos de código claros.
og_title: Gerenciar substituição de fontes no Aspose.Words – Guia completo
schemas:
- author: Aspose
  dateModified: '2026-06-17'
  description: Handle font substitution in Aspose.Words and detect missing fonts quickly
    with this step‑by‑step tutorial for .NET developers.
  headline: Handle Font Substitution in Aspose.Words – Complete Programming Guide
  type: TechArticle
- description: Handle font substitution in Aspose.Words and detect missing fonts quickly
    with this step‑by‑step tutorial for .NET developers.
  name: Handle Font Substitution in Aspose.Words – Complete Programming Guide
  steps:
  - name: '**Create a test DOCX** that references a font you know isn’t on the machine
      (e.g., “Comic Sans MS” on a minimal Docker image).'
    text: '**Create a test DOCX** that references a font you know isn’t on the machine
      (e.g., “Comic Sans MS” on a minimal Docker image).'
  - name: Run the console app or API endpoint.
    text: Run the console app or API endpoint.
  - name: Verify that the console (or HTTP response) lists the substitution warning.
    text: Verify that the console (or HTTP response) lists the substitution warning.
  - name: Optionally, open the resulting PDF and check the font properties—Aspose.Words
      should show the fallback font you configured.
    text: Optionally, open the resulting PDF and check the font properties—Aspose.Words
      should show the fallback font you configured.
  type: HowTo
tags:
- Aspose.Words
- .NET
- Font Management
title: Gerencie a Substituição de Fontes no Aspose.Words – Guia Completo de Programação
url: /pt/net/working-with-fonts/handle-font-substitution-in-aspose-words-complete-programmin/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Manipular Substituição de Fonte no Aspose.Words – Guia de Programação Completo

Já se perguntou como **manipular a substituição de fonte** quando um documento Word referencia uma fonte que não está instalada no servidor? Você não está sozinho. Em muitas aplicações reais—pense em geradores de faturas ou serviços de relatórios automatizados—fontes ausentes causam substituições silenciosas que arruinam o layout.  

A boa notícia é que o Aspose.Words oferece um sistema de avisos embutido que permite **detectar fontes ausentes** e reagir da maneira que desejar. Neste tutorial vamos percorrer o registro de um manipulador de avisos, o carregamento de um documento e a extração dos eventos exatos de substituição de fonte que você precisa conhecer. Ao final, você também verá como responder à clássica pergunta “**como detectar fontes ausentes**?” com código limpo e pronto para produção.

## O Que Este Tutorial Cobre

* Configurar o Aspose.Words para disparar avisos para cada substituição de fonte.  
* Capturar esses avisos em um manipulador personalizado para que você possa registrar, substituir ou abortar.  
* Usar os dados capturados para **detectar fontes ausentes** antes que o documento seja salvo ou renderizado.  
* Dicas para solucionar casos extremos—como quando uma fonte de fallback é escolhida silenciosamente.  
* Um exemplo completo e executável que pode ser inserido em qualquer aplicativo console .NET.

> **Pré‑requisitos** – Você precisará de um SDK .NET recente (6.0+ funciona bem), uma licença válida do Aspose.Words for .NET (ou uma chave de avaliação temporária) e um DOCX de exemplo que intencionalmente referencia uma fonte que você não tem instalada. Nenhuma outra biblioteca de terceiros é necessária.

---

## ## Manipular Substituição de Fonte com um Manipulador de Avisos Personalizado

O Aspose.Words gera um objeto `WarningInfo` toda vez que não consegue encontrar a fonte solicitada. Por padrão esses avisos são ignorados, e é por isso que você muitas vezes nunca percebe uma substituição. Para **manipular a substituição de fonte**, você substitui o manipulador de avisos padrão por um que realmente faça algo.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // Register a custom warning handler that prints font‑substitution events.
        FontSettings.DefaultWarningHandler = new WarningInfoCollectionHandler(
            (sender, args) =>
            {
                // We're only interested in font‑substitution warnings.
                if (args.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ Font substituted: {args.Description}");
                }
            });

        // Load a document that deliberately references an unavailable font.
        Document doc = new Document("Samples/MissingFont.docx");

        // Force a save to trigger any pending warnings (e.g., PDF conversion).
        doc.Save("Output/Result.pdf");
    }
}
```

### Por Que Isso Funciona

* `FontSettings.DefaultWarningHandler` é uma propriedade estática global—uma vez que você a define, **todas** as operações do Aspose.Words no AppDomain atual usam seu delegate.  
* O `WarningInfoCollectionHandler` recebe um objeto `WarningInfo` que contém `WarningType` e uma `Description` legível por humanos. Filtrar por `WarningType.FontSubstitution` garante que você veja apenas os eventos que lhe interessam.  
* Chamar `doc.Save` força a biblioteca a resolver todas as fontes, momento em que os avisos são disparados. Se você precisar apenas inspecionar o documento sem salvar, pode chamar `doc.UpdatePageLayout()` em vez disso.

**Saída esperada no console** (supondo que a fonte ausente seja “Papyrus”):

```
⚠️ Font substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
```

Essa linha é a prova de que a biblioteca **detectou fontes ausentes** e escolheu um fallback.

---

## ## Detectar Fontes Ausentes Antes da Renderização

Às vezes você quer interromper o processo completamente se uma fonte necessária estiver ausente—talvez porque as diretrizes de marca exijam tipografia exata. O manipulador de avisos pode ser estendido para coletar todas as mensagens de fontes ausentes em uma lista, e então você pode tomar uma decisão.

```csharp
using System.Collections.Generic;

// ...

static List<string> missingFonts = new List<string>();

static void Main()
{
    FontSettings.DefaultWarningHandler = new WarningInfoCollectionHandler(
        (sender, args) =>
        {
            if (args.WarningType == WarningType.FontSubstitution)
            {
                // Store the description for later analysis.
                missingFonts.Add(args.Description);
                Console.WriteLine($"⚠️ Font substituted: {args.Description}");
            }
        });

    Document doc = new Document("Samples/MissingFont.docx");
    doc.UpdatePageLayout();   // Triggers warnings without saving.

    if (missingFonts.Count > 0)
    {
        Console.WriteLine("\n❗ Detected missing fonts:");
        foreach (var msg in missingFonts)
            Console.WriteLine($" - {msg}");

        // Optionally abort the operation.
        // throw new InvalidOperationException("Missing required fonts.");
    }
    else
    {
        Console.WriteLine("\n✅ No font substitution detected.");
    }

    // Continue with saving or further processing if you wish.
    doc.Save("Output/Result.pdf");
}
```

### Como Isso Responde “como detectar fontes ausentes”

* A lista `missingFonts` funciona como um registro de cada evento de substituição.  
* Após `UpdatePageLayout`, você pode inspecionar a lista e decidir se continua, registra ou lança uma exceção.  
* Esse padrão funciona para qualquer formato de saída (PDF, HTML, imagens) porque o sistema de avisos é agnóstico ao formato.

---

## ## Dica Avançada: Substituir Fontes Ausentes por um Substituto Específico

Se você tem uma fonte corporativa que deve ser usada, pode instruir o Aspose.Words a substituir qualquer fonte ausente pelo seu fallback automaticamente. Isso é útil quando você quer que o documento *continue* apresentável sem pós‑processamento manual.

```csharp
// Configure a fallback font collection.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes(
    "AnyMissingFont", new string[] { "Calibri", "Arial" });

FontSettings.DefaultFontSettings = fontSettings;
```

Coloque o trecho acima **antes** de carregar o documento. Agora qualquer fonte ausente—não importa o nome original—será trocada por “Calibri” (ou “Arial” se Calibri não estiver presente). Você ainda receberá o aviso, mas o documento será renderizado com a fonte que você controla.

---

## ## Armadilhas Comuns & Como Evitá‑las

| Armadilha | Por Que Acontece | Solução |
|----------|------------------|---------|
| **Avisos desaparecem após a primeira chamada** | O `DefaultWarningHandler` estático é sobrescrito mais tarde na aplicação. | Defina o manipulador **uma única vez** na inicialização da aplicação, ou armazene uma referência e reatribua se precisar alterá‑lo. |
| **Só a primeira fonte ausente é reportada** | Algumas APIs agrupam avisos; é necessário chamar `UpdatePageLayout` ou `Save` para esvaziar a fila. | Forçe uma atualização de layout ou salve no formato que pretende gerar. |
| **A substituição ainda ocorre mesmo após abortar** | O manipulador de avisos roda *depois* que a substituição já aconteceu. | Use o manipulador para **registrar** e então lance uma exceção para interromper o processamento adicional. |
| **Fontes ausentes em contêineres Linux** | Linux costuma não ter o catálogo de fontes do Windows, levando a muitas substituições. | Monte as fontes necessárias no contêiner ou use `FontSettings.SetFontsFolder` para apontar para um diretório de fontes customizado. |

---

## ## Detectar Substituição de Fonte em um Cenário Web API

Se você está servindo documentos via ASP.NET Core, provavelmente não quer gravações no console. Em vez disso, colete os avisos e retorne‑os como parte da resposta HTTP.

```csharp
[ApiController]
[Route("api/[controller]")]
public class DocumentController : ControllerBase
{
    [HttpPost("convert")]
    public IActionResult Convert(IFormFile file)
    {
        var missingFonts = new List<string>();

        FontSettings.DefaultWarningHandler = new WarningInfoCollectionHandler(
            (s, e) =>
            {
                if (e.WarningType == WarningType.FontSubstitution)
                    missingFonts.Add(e.Description);
            });

        using var stream = file.OpenReadStream();
        var doc = new Document(stream);
        doc.UpdatePageLayout();

        if (missingFonts.Any())
        {
            return BadRequest(new { message = "Missing fonts detected", details = missingFonts });
        }

        // Convert to PDF and stream back.
        var pdfStream = new MemoryStream();
        doc.Save(pdfStream, SaveFormat.Pdf);
        pdfStream.Position = 0;
        return File(pdfStream, "application/pdf", "result.pdf");
    }
}
```

Agora a API **detecta fontes ausentes** e devolve um payload JSON claro antes de gerar qualquer PDF. Esta é uma ilustração prática de “como detectar fontes ausentes” em um serviço de nível de produção.

---

## ## Testando Sua Implementação

1. **Crie um DOCX de teste** que referencia uma fonte que você sabe que não está na máquina (por exemplo, “Comic Sans MS” em uma imagem Docker mínima).  
2. Execute o aplicativo console ou o endpoint da API.  
3. Verifique se o console (ou a resposta HTTP) lista o aviso de substituição.  
4. Opcionalmente, abra o PDF resultante e confira as propriedades da fonte—o Aspose.Words deve mostrar a fonte de fallback que você configurou.

Se você vir o aviso mas o PDF ainda usar uma fonte inesperada, verifique a ordem das `SubstitutionSettings`; a primeira correspondência vence.

---

## ## Conclusão

Cobremos tudo o que você precisa para **manipular substituição de fonte** no Aspose.Words, desde registrar um manipulador de avisos até programaticamente **detectar fontes ausentes** e até substituí‑las por uma tipografia corporativa. Ao aproveitar o sistema de avisos embutido, você obtém total visibilidade em cada evento de “fonte não encontrada”, respondendo diretamente à pergunta “**como detectar fontes ausentes**?” que todo desenvolvedor faz ao automatizar a geração de documentos.

Qual o próximo passo? Experimente combinar essa lógica com **carregamento dinâmico de fontes** (`FontSettings.SetFontsFolder`) para suportar fontes enviadas por usuários em tempo real, ou estenda o manipulador de avisos para gravar entradas em um serviço central de logging como o Serilog. Quanto mais você instrumentar o tratamento de fontes, mais confiável se tornará seu pipeline de documentos.

Tem um cenário complicado de substituição de fonte que está lhe dando dor de cabeça? Deixe um comentário abaixo e vamos solucionar juntos. Feliz codificação!

## O Que Você Deve Aprender a Seguir?


Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Enable Font Substitution Warnings in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [How to Load DOCX and Detect Missing Fonts – Complete C# Guide](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}