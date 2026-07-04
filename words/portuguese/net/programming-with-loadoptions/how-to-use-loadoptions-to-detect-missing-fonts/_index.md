---
category: general
date: 2026-06-08
description: Aprenda a usar LoadOptions no Aspose.Words para detectar fontes ausentes
  durante a importação de documentos. Guia passo a passo com código, explicações e
  boas práticas.
draft: false
keywords:
- how to use loadoptions
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
- C# document loading
language: pt
og_description: Como usar LoadOptions no Aspose.Words e detectar fontes ausentes ao
  carregar um documento. Guia completo com código e dicas práticas.
og_title: Como usar LoadOptions para detectar fontes ausentes
schemas:
- author: Aspose
  dateModified: '2026-06-08'
  description: Learn how to use LoadOptions in Aspose.Words to detect missing fonts
    during document import. Step-by-step guide with code, explanations, and best practices.
  headline: How to Use LoadOptions to Detect Missing Fonts
  type: TechArticle
- description: Learn how to use LoadOptions in Aspose.Words to detect missing fonts
    during document import. Step-by-step guide with code, explanations, and best practices.
  name: How to Use LoadOptions to Detect Missing Fonts
  steps:
  - name: Create a Warning Handler
    text: Aspose.Words uses the `IWarningCallback` interface to notify you about non‑critical
      issues, such as font substitution. Implement the interface and decide what to
      do when a warning arrives.
  - name: Attach the Handler to LoadOptions
    text: Now we create a `LoadOptions` instance and tell it to use our `FontWarningHandler`.
      This is the point where **how to use LoadOptions** really shines.
  - name: Load the Document Using the Configured Options
    text: Finally, we feed the `LoadOptions` into the `Document` constructor. If the
      source file references a font that isn’t installed, Aspose.Words will fire the
      warning and your handler will print a message.
  - name: Multiple Documents in a Loop
    text: Often you’ll process a batch of files. The same `LoadOptions` instance can
      be reused, but remember that the `WarningCallback` persists across loads. If
      you need per‑document isolation, instantiate a fresh `LoadOptions` for each
      iteration.
  - name: Custom Font Substitution Logic
    text: 'Instead of merely logging, you might want to substitute a specific missing
      font with a corporate‑approved alternative. Extend the handler:'
  - name: Silencing Unwanted Warnings
    text: If you only care about font issues and want to suppress everything else,
      filter by `WarningType` as shown. Conversely, to log *all* warnings, drop the
      `if` check and output `info.WarningType` alongside `info.Description`.
  type: HowTo
tags:
- Aspose.Words
- C#
- Font Management
title: Como usar LoadOptions para detectar fontes ausentes
url: /pt/net/programming-with-loadoptions/how-to-use-loadoptions-to-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como usar LoadOptions para Detectar Fontes Ausentes

Já se perguntou **como usar LoadOptions** ao carregar um documento Word com Aspose.Words? Neste tutorial vamos mostrar exatamente **como usar LoadOptions** para **detectar fontes ausentes** e tratá‑las de forma elegante. Seja você quem está construindo um serviço de conversão de documentos ou um mecanismo de relatórios, fontes ausentes podem causar surpresas de layout, portanto detectá‑las cedo é essencial.

Vamos percorrer cada passo — desde conectar um callback de aviso até interpretar os resultados — para que você termine com um exemplo C# totalmente funcional que pode ser inserido em qualquer projeto .NET. Sem documentação externa, apenas uma solução autônoma. Ao final você saberá por que o sistema de avisos existe, como habilitá‑lo e o que fazer quando o callback é disparado.

## Pré‑requisitos

Antes de mergulharmos, certifique‑se de que você tem:

- **Aspose.Words for .NET** (qualquer versão recente; a API que usamos é estável desde 2022).
- Um ambiente de desenvolvimento .NET (Visual Studio, Rider ou VS Code com a extensão C#).
- Um arquivo Word de exemplo (`input.docx`) que referencia uma fonte que você *não* tem instalada na máquina.

É só isso — nenhum pacote NuGet extra além do Aspose.Words.

## Como usar LoadOptions com Aspose.Words

A classe **LoadOptions** é a porta de entrada para personalizar a forma como um documento é lido. Ao conectar um callback de aviso a ela, você pode **detectar fontes ausentes** no instante em que o Aspose.Words analisa o arquivo. Vamos detalhar.

### Etapa 1: Criar um Manipulador de Avisos

Aspose.Words usa a interface `IWarningCallback` para notificar sobre questões não críticas, como substituição de fontes. Implemente a interface e decida o que fazer quando um aviso chegar.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Warnings;

// Step 1: Define a warning handler that will be notified of font substitutions.
class FontWarningHandler : IWarningCallback
{
    // The Process method is called for every warning Aspose.Words generates.
    public void Process(WarningInfo info)
    {
        // We're only interested in font substitution warnings.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write a helpful message to the console.
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

**Por que isso importa:**  
Sem um callback, o Aspose.Words troca silenciosamente fontes ausentes por uma padrão (geralmente Arial). Capturando o aviso `FontSubstitution` você pode registrar o problema, alertar o usuário ou até substituir a fonte ausente por um fallback personalizado.

### Etapa 2: Anexar o Manipulador ao LoadOptions

Agora criamos uma instância de `LoadOptions` e instruímos a usar nosso `FontWarningHandler`. É neste ponto que **como usar LoadOptions** realmente brilha.

```csharp
using Aspose.Words.LoadOptions;

// Step 2: Create LoadOptions and attach the warning handler.
var loadOptions = new LoadOptions
{
    // The WarningCallback property accepts any IWarningCallback implementation.
    WarningCallback = new FontWarningHandler()
};
```

**Por que isso importa:**  
`LoadOptions` é um ponto único para muitas configurações de importação (codificação, senha etc.). Ao definir `WarningCallback`, você habilita um mecanismo leve, orientado a eventos, que funciona para qualquer documento carregado com essas opções.

### Etapa 3: Carregar o Documento Usando as Opções Configuradas

Por fim, passamos o `LoadOptions` para o construtor `Document`. Se o arquivo de origem referencia uma fonte que não está instalada, o Aspose.Words disparará o aviso e seu manipulador imprimirá uma mensagem.

```csharp
// Step 3: Load the document using the configured LoadOptions.
// Any missing fonts will trigger the FontWarningHandler.
Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**O que você verá:**  
Assumindo que `input.docx` usa uma fonte chamada *“MyCustomFont”* que não está na máquina, a saída no console será semelhante a:

```
Font substituted: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
```

Se todas as fontes estiverem presentes, o callback permanecerá silencioso — sem saída, sem impacto de desempenho.

## Detectar Fontes Ausentes com um Callback de Aviso (Palavra‑chave Secundária em Ação)

A frase **detect missing fonts** aparece naturalmente no cabeçalho acima, reforçando a palavra‑chave secundária. Vamos explorar algumas variações que você pode encontrar em projetos reais.

### Vários Documentos em um Loop

Frequentemente você processará um lote de arquivos. A mesma instância de `LoadOptions` pode ser reutilizada, mas lembre‑se de que o `WarningCallback` persiste entre carregamentos. Se precisar de isolamento por documento, crie um novo `LoadOptions` a cada iteração.

```csharp
string[] files = Directory.GetFiles(@"C:\Docs", "*.docx");
foreach (var file in files)
{
    var options = new LoadOptions { WarningCallback = new FontWarningHandler() };
    var document = new Document(file, options);
    // Perform further processing...
}
```

### Lógica Personalizada de Substituição de Fonte

Em vez de apenas registrar, você pode querer substituir uma fonte ausente específica por uma alternativa aprovada pela empresa. Expanda o manipulador:

```csharp
class FontWarningHandler : IWarningCallback
{
    public void Process(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Extract the missing font name from the description.
            string missingFont = info.Description.Split('\'')[1];
            // Choose a fallback based on your policy.
            string fallback = missingFont.Equals("MyCustomFont") ? "Calibri" : "Arial";
            Console.WriteLine($"Missing '{missingFont}'. Using fallback '{fallback}'.");
            // You could also modify FontSettings here if needed.
        }
    }
}
```

Agora você não só **detecta fontes ausentes**, como também decide como substituí‑las.

### Silenciando Avisos Indesejados

Se você se importa apenas com questões de fonte e deseja suprimir todo o resto, filtre por `WarningType` como mostrado. Por outro lado, para registrar *todos* os avisos, remova a verificação `if` e exiba `info.WarningType` junto com `info.Description`.

## Exemplo Completo e Executável

Juntando tudo, aqui está um programa completo que você pode compilar e executar. Substitua `"YOUR_DIRECTORY/input.docx"` pelo caminho do seu arquivo de teste.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningHandler : IWarningCallback
{
    public void Process(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Ensure the Aspose.Words license is set if you have one.
        // License license = new License();
        // license.SetLicense("Aspose.Words.lic");

        var loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningHandler()
        };

        string docPath = Path.Combine("YOUR_DIRECTORY", "input.docx");

        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
            // You can now work with 'doc' – save, modify, export, etc.
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**Saída esperada no console (quando uma fonte está ausente):**

```
Font substituted: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
Document loaded successfully.
```

Se nenhuma fonte estiver ausente, você verá simplesmente:

```
Document loaded successfully.
```

## Armadilhas Comuns & Dicas Profissionais

- **Armadilha:** Esquecer de definir `WarningCallback`. A API ainda substituirá fontes, mas você nunca saberá que isso aconteceu.  
  **Dica profissional:** Sempre anexe um manipulador quando precisar de fidelidade tipográfica; o custo é praticamente nulo.

- **Armadilha:**  
  **Dica profissional:**  

## O que Você Deve Aprender a Seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Como Detectar Fontes no Aspose.Words – Manipular Avisos e Configurações](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Como Capturar Fontes no Aspose.Words – Guia Completo](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)
- [Como Carregar DOCX e Detectar Fontes Ausentes – Guia Completo em C#](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}