---
category: general
date: 2026-06-05
description: Configure as opções de carregamento de documento em C# para lidar com
  avisos de substituição de fontes e personalizar o comportamento de carregamento
  usando um callback de aviso.
draft: false
keywords:
- configure document load options
- warning callback
- font substitution warning
- LoadOptions usage
- Aspose.Words document loading
- C# document loading options
language: pt
og_description: Configure as opções de carregamento de documentos em C# para gerenciar
  avisos de substituição de fontes e ajustar finamente o carregamento do documento
  com um callback de aviso.
og_title: Configure as opções de carregamento de documentos em C# – Guia Completo
schemas:
- author: Aspose
  dateModified: '2026-06-05'
  description: Configure document load options in C# to handle font substitution warnings
    and customize loading behavior using a warning callback.
  headline: Configure document load options in C# – Complete Guide
  type: TechArticle
- description: Configure document load options in C# to handle font substitution warnings
    and customize loading behavior using a warning callback.
  name: Configure document load options in C# – Complete Guide
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code works with .NET Framework 4.6+ as well).
      - Aspose.Words for .NET installed (`dotnet add package Aspose.Words`). - Basic
      familiarity with C# syntax.'
  - name: Implement a Warning Callback for Font Substitution
    text: First things first—what’s a **warning callback**? In Aspose.Words it’s a
      delegate that gets invoked whenever the library encounters something worth flagging,
      like a missing font. By catching `WarningType.FontSubstitution` we can log the
      exact font the engine swapped out.
  - name: Set Up LoadOptions with the Callback
    text: Now that we have a callback, we need to **configure document load options**
      to actually use it. `LoadOptions` is a lightweight container that tells Aspose.Words
      how to behave during the `Document` constructor call.
  - name: Load the Document Using the Configured Options
    text: With the callback wired up, the final act is to actually **load the document**.
      The `Document` constructor accepts a file path and the `LoadOptions` we just
      prepared.
  - name: Optional – Verify Loaded Fonts (Edge Case Handling)
    text: Sometimes you might want to *pre‑validate* the document before loading it
      fully, especially in batch processing scenarios. Aspose.Words offers the `FontSettings`
      class that can enumerate required fonts.
  - name: What if the warning callback throws an exception?
    text: The callback runs on the same thread that loads the document. Throwing inside
      the delegate will abort the load and propagate the exception. Wrap your logic
      in a `try/catch` if you need resilience.
  - name: Can I suppress *all* warnings instead of handling them?
    text: Yes—set `loadOptions.WarningCallback = null;` or provide a callback that
      does nothing. Be aware you’ll lose visibility into potential problems.
  - name: Does this work with encrypted DOCX files?
    text: Absolutely. Just add `Password = "yourPassword"` to `LoadOptions` before
      creating the `Document`. The warning callback will still fire for font issues.
  - name: How does this differ from using `DocumentBuilder`?
    text: '`DocumentBuilder` is for *creating* or *modifying* a document after it’s
      loaded. **Configure document load options** influences the *initial* parsing
      stage, which is where font substitution decisions are made.'
  type: HowTo
tags:
- C#
- Aspose.Words
- LoadOptions
- DocumentProcessing
title: Configure as opções de carregamento de documentos em C# – Guia completo
url: /pt/net/programming-with-loadoptions/configure-document-load-options-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Configure opções de carregamento de documento em C# – Guia Completo

Já precisou **configurar opções de carregamento de documento** em C# porque o comportamento padrão de carregamento simplesmente não atendia? Talvez você esteja vendo substituições de fontes inesperadas ou queira registrar cada aviso que aparece durante a importação de um arquivo. Neste tutorial, vamos percorrer uma solução prática, de ponta a ponta, que não só define essas opções, mas também demonstra um **callback de aviso** para avisos de substituição de fontes.

Vamos cobrir tudo, desde o pequeno trecho de código que cria o callback até o momento em que você finalmente abre o documento com suas configurações personalizadas. Ao final, você terá um padrão reutilizável que pode inserir em qualquer projeto Aspose.Words, seja processando faturas, contratos legais ou relatórios simples.

## O que você aprenderá

- Como **configurar opções de carregamento de documento** com `LoadOptions`.
- Como implementar um **callback de aviso** que captura alertas de `FontSubstitution`.
- Por que tratar um **aviso de substituição de fonte** cedo pode evitar surpresas de layout.
- Tratamento de casos extremos para fontes ausentes e como fazer fallback de forma elegante.
- Um exemplo de código completo, pronto para copiar e colar, que você pode executar hoje.

### Pré-requisitos

- .NET 6.0 ou posterior (o código também funciona com .NET Framework 4.6+).
- Aspose.Words para .NET instalado (`dotnet add package Aspose.Words`).
- Familiaridade básica com a sintaxe C#.

Se você tem isso, vamos mergulhar.

## Configurar opções de carregamento de documento – Passo a passo

A seguir está o fluxo completo dividido em quatro etapas claras. Cada etapa é explicada e seguida por um bloco de código conciso que você pode colar diretamente no Visual Studio.

### Etapa 1: Implementar um Callback de Aviso para Substituição de Fonte

Primeiro de tudo—o que é um **callback de aviso**? No Aspose.Words é um delegate que é invocado sempre que a biblioteca encontra algo que vale a pena sinalizar, como uma fonte ausente. Ao capturar `WarningType.FontSubstitution` podemos registrar a fonte exata que o motor substituiu.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Step 1: Define a warning callback that reports font substitution warnings
var fontWarningCallback = new IWarningCallback(
    warningInfo =>
    {
        // Check if the warning is about font substitution
        if (warningInfo.WarningType == WarningType.FontSubstitution)
        {
            // Log the warning – you could also write to a file or telemetry system
            Console.WriteLine($"Font substitution detected: {warningInfo.Description}");
        }
    });
```

**Por que isso importa:** Sem um callback, a biblioteca substitui silenciosamente fontes ausentes, o que pode gerar texto corrompido no PDF ou DOCX final. Ao expor o aviso você ganha visibilidade e pode decidir se incorpora a fonte ausente, troca por um fallback ou alerta o usuário.

> **Dica profissional:** Se precisar capturar *todos* os avisos, remova a verificação `if`. Basta registrar `warningInfo.Description` para cada evento.

### Etapa 2: Configurar LoadOptions com o Callback

Agora que temos um callback, precisamos **configurar opções de carregamento de documento** para realmente usá-lo. `LoadOptions` é um contêiner leve que informa ao Aspose.Words como se comportar durante a chamada ao construtor `Document`.

```csharp
// Step 2: Attach the callback to the LoadOptions object
var loadOptions = new LoadOptions
{
    WarningCallback = fontWarningCallback,
    // Optional: enforce strict loading mode (throws on any warning)
    // LoadFormat = LoadFormat.Docx,
    // LoadOptions.LoadFormat can be left null to auto-detect based on file extension
};
```

**Por que isso importa:** Ao atribuir `WarningCallback`, cada aviso emitido durante a fase de carregamento passa pelo nosso delegate. Você também pode ajustar outras propriedades de `LoadOptions` aqui—como `LoadFormat` se souber o tipo exato de arquivo, ou `Password` para documentos criptografados.

### Etapa 3: Carregar o Documento usando as Opções Configuradas

Com o callback conectado, o ato final é realmente **carregar o documento**. O construtor `Document` aceita um caminho de arquivo e o `LoadOptions` que acabamos de preparar.

```csharp
// Step 3: Load the document with our custom options
string inputPath = @"C:\Docs\input.docx";   // Adjust to your environment
Document doc = new Document(inputPath, loadOptions);
```

Se o arquivo de origem referencia uma fonte que não está instalada na máquina, você verá uma linha como:

```
Font substitution detected: Font 'Calibri' was substituted with 'Arial'.
```

no console. Esse feedback imediato permite que você decida se inclui a fonte ausente junto com seu aplicativo ou se a substitui programaticamente.

### Etapa 4: Opcional – Verificar Fontes Carregadas (Tratamento de Caso Extremo)

Às vezes você pode querer *pré‑validar* o documento antes de carregá‑lo completamente, especialmente em cenários de processamento em lote. Aspose.Words oferece a classe `FontSettings` que pode enumerar as fontes necessárias.

```csharp
// Optional: Check required fonts before full load
var fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);
loadOptions.FontSettings = fontSettings;

// Re-load the document now that we have a custom font folder
Document docWithCustomFonts = new Document(inputPath, loadOptions);
```

**Quando usar isso:** Se você mantém um repositório privado de fontes (por exemplo, fontes da marca corporativa), apontar `FontSettings` para essa pasta garante que o motor encontre as tipografias corretas sem recorrer a genéricas.

## Exemplo completo em funcionamento

A seguir está o programa inteiro—basta copiar, colar e executar. Ele demonstra tudo, desde a criação do callback até o carregamento final do documento.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;

class Program
{
    static void Main()
    {
        // 1️⃣ Define the warning callback
        var fontWarningCallback = new IWarningCallback(
            warningInfo =>
            {
                if (warningInfo.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"Font substitution detected: {warningInfo.Description}");
                }
            });

        // 2️⃣ Configure LoadOptions with the callback
        var loadOptions = new LoadOptions
        {
            WarningCallback = fontWarningCallback,
            // Uncomment the next line to point to a custom font folder
            // FontSettings = new FontSettings { SetFontsFolder(@"C:\MyFonts", true) }
        };

        // 3️⃣ Load the document using the custom options
        string inputFile = @"YOUR_DIRECTORY/input.docx";
        Document doc = new Document(inputFile, loadOptions);

        // 4️⃣ (Optional) Save as PDF to verify everything works
        string outputFile = @"YOUR_DIRECTORY/output.pdf";
        doc.Save(outputFile);
        Console.WriteLine($"Document loaded and saved to {outputFile}");
    }
}
```

**Saída esperada**

```
Font substitution detected: Font 'Times New Roman' was substituted with 'Arial'.
Document loaded and saved to C:\Your\Path\output.pdf
```

Se não houver fontes ausentes, o callback simplesmente permanece silencioso—não há com o que se preocupar.

## Perguntas comuns & casos extremos

### E se o callback de aviso lançar uma exceção?

O callback é executado na mesma thread que carrega o documento. Lançar uma exceção dentro do delegate abortará o carregamento e propagará a exceção. Envolva sua lógica em um `try/catch` se precisar de resiliência.

### Posso suprimir *todos* os avisos ao invés de tratá‑los?

Sim—defina `loadOptions.WarningCallback = null;` ou forneça um callback que não faça nada. Esteja ciente de que perderá visibilidade sobre possíveis problemas.

### Isso funciona com arquivos DOCX criptografados?

Com certeza. Basta adicionar `Password = "yourPassword"` ao `LoadOptions` antes de criar o `Document`. O callback de aviso ainda será disparado para questões de fontes.

### Como isso difere do uso do `DocumentBuilder`?

`DocumentBuilder` serve para *criar* ou *modificar* um documento após ele ser carregado. **Configurar opções de carregamento de documento** influencia a fase de *análise inicial*, onde as decisões de substituição de fontes são tomadas.

## Visão geral visual

![Diagram showing configure document load options flow](https://example.com/images/load-options-flow.png "Diagram showing configure document load options flow")

*A imagem ilustra o fluxo: callback → LoadOptions → construtor Document → tratamento de avisos.*

## Conclusão

Agora você sabe como **configurar opções de carregamento de documento** em C# para capturar avisos de substituição de fontes, injetar pastas de fontes personalizadas e manter controle total sobre o processo de carregamento. Esse padrão lhe dá a confiança de que toda fonte ausente será relatada, permitindo que você mantenha a fidelidade do documento em qualquer ambiente.

Próximos passos? Experimente substituir o registro no console por um sistema de telemetria mais robusto, ou combine esta abordagem com `DocumentBuilder` para substituir automaticamente fontes ausentes por um padrão corporativo. Você também pode explorar outros valores de `WarningType` como `DocumentStructure` para obter ainda mais detalhes.

Feliz codificação, e que seus documentos sempre sejam renderizados exatamente como você pretende!

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Domine as opções de carregamento Markdown do Aspose.Words em Python para processamento avançado de documentos](/words/english/python-net/document-operations/aspose-words-markdown-load-options-python/)
- [Otimizando o carregamento de documentos com opções HTML, RTF e TXT](/words/english/java/word-processing/optimizing-document-loading-options/)
- [Usando opções e configurações de documento no Aspose.Words para Java](/words/english/java/document-manipulation/using-document-options-and-settings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}