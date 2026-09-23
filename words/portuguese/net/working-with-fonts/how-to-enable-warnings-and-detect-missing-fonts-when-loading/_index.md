---
category: general
date: 2026-02-21
description: Aprenda como habilitar avisos, detectar fontes ausentes e como carregar
  docx com segurança usando Aspose.Words em C#. Siga o guia passo a passo.
draft: false
keywords:
- how to enable warnings
- detect missing fonts
- how to load docx
- font substitution handling
- Aspose.Words warnings
language: pt
og_description: Como habilitar avisos, detectar fontes ausentes e carregar corretamente
  arquivos docx com Aspose.Words. Exemplo de código completo incluído.
og_title: Como habilitar avisos e detectar fontes ausentes ao carregar DOCX
tags:
- C#
- Aspose.Words
- Document processing
title: Como habilitar avisos e detectar fontes ausentes ao carregar arquivos DOCX
url: /pt/net/working-with-fonts/how-to-enable-warnings-and-detect-missing-fonts-when-loading/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como habilitar avisos e detectar fontes ausentes ao carregar arquivos DOCX

Já se perguntou **como habilitar avisos** para fontes ausentes antes que elas silenciosamente estraguem a renderização do seu documento? Você não está sozinho—a maioria dos desenvolvedores assume que a biblioteca simplesmente “faça a coisa certa”, apenas para descobrir depois que uma fonte foi substituída sem nenhum indício.  

Neste tutorial, mostraremos exatamente **como habilitar avisos**, como **detectar fontes ausentes**, e a maneira correta **de carregar docx** usando Aspose.Words para .NET. Ao final, você terá um exemplo pronto‑para‑executar que imprime cada aviso de substituição de fonte no console, para que nunca mais precise adivinhar o que aconteceu dentro do arquivo.

## Pré-requisitos

- .NET 6.0 ou posterior (o código também funciona no .NET Framework 4.7+)  
- Visual Studio 2022 ou qualquer IDE C# de sua preferência  
- O pacote NuGet **Aspose.Words** (`Install-Package Aspose.Words`)  
- Um arquivo DOCX que pode conter fontes não instaladas na sua máquina (vamos chamá‑lo de `input.docx`)

> **Dica profissional:** Se você não tem um arquivo de teste, basta abrir um documento Word que use uma fonte corporativa personalizada e salvá‑lo como `input.docx`. Isso disparará o aviso que queremos capturar.

## Visão geral da solução

1. **Criar** um objeto `LoadOptions` com `FontSubstitutionWarnings` ativado.  
2. **Carregar** o arquivo DOCX usando essas opções.  
3. **Inspecionar** a coleção `WarningCallback` em busca de entradas `FontSubstitution`.  
4. **Reagir** – você pode registrar, exibir ou até substituir a fonte ausente programaticamente.

A seguir, detalhamos cada passo, explicamos *por que* ele é importante e fornecemos um trecho de código completo e executável.

---

## Etapa 1: Instalar Aspose.Words e configurar o projeto

Antes de podermos **como habilitar avisos**, precisamos da biblioteca que realmente os suporta.

```bash
# Using the .NET CLI
dotnet add package Aspose.Words
```

Ou, no Console do Gerenciador de Pacotes do Visual Studio:

```powershell
Install-Package Aspose.Words
```

> **Por que este passo?**  
> Sem o pacote, as classes `LoadOptions`, `Document` e a infraestrutura de avisos simplesmente não existem. Adicionar a referência NuGet garante que você esteja obtendo a versão estável mais recente (na data desta escrita, 24.5).

---

## Etapa 2: Criar opções de carregamento que habilitam avisos de substituição de fonte

O núcleo de **como habilitar avisos** está na classe `LoadOptions`. Definir `FontSubstitutionWarnings` como `true` indica ao motor que registre cada vez que precisar substituir uma fonte ausente.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

// Step 2: Build the options object
LoadOptions loadOptions = new LoadOptions
{
    // This flag makes the library emit warnings for any font it cannot find.
    FontSubstitutionWarnings = true
};
```

> **Por que habilitar esta flag?**  
> Por padrão, o Aspose.Words troca silenciosamente fontes ausentes por uma alternativa (geralmente Arial). Isso pode causar alterações de layout, caracteres invisíveis ou violações de identidade visual. Ativar a flag fornece total visibilidade.

---

## Etapa 3: Carregar o arquivo DOCX usando as opções configuradas

Agora que sabemos **como carregar docx** com avisos ativados, realmente realizamos o carregamento.

```csharp
// Step 3: Load the document – replace the path with your own file location.
string docPath = @"YOUR_DIRECTORY\input.docx";
Document document = new Document(docPath, loadOptions);
```

> **O que acontece nos bastidores?**  
> Ao analisar o DOCX, o Aspose.Words verifica cada elemento `<w:rFonts>`. Se a fonte especificada não estiver instalada, ele registra um aviso `FontSubstitution` e recorre a uma fonte padrão. Como habilitamos os avisos, essas entradas acabam em `document.WarningCallback.Warnings`.

---

## Etapa 4: Recuperar e exibir avisos de substituição de fonte

A propriedade `WarningCallback` contém uma `WarningInfoCollection`. Percorra‑a, filtre por `WarningType.FontSubstitution` e exiba as mensagens.

```csharp
// Step 4: Iterate over warnings and print font‑substitution details.
foreach (WarningInfo warning in document.WarningCallback.Warnings)
{
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"⚠️ Font substituted: {warning.Message}");
    }
}
```

**Saída esperada** (exemplo):

```
⚠️ Font substituted: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
⚠️ Font substituted: Font 'CorporateLogo' was not found. Substituted with 'Times New Roman'.
```

> **O que fazer com essas mensagens?**  
> Você pode registrá‑las em um arquivo, exibí‑las em uma interface ou até disparar uma rotina personalizada de fallback de fonte. O importante é que agora você *detecta fontes ausentes* em vez de adivinhar depois.

---

## Etapa 5: (Opcional) Substituir fontes ausentes por um fallback específico

Se você tem uma fonte corporativa que deseja impor, pode tratar os avisos e substituí‑las em tempo real.

```csharp
// Optional: Custom fallback font
string fallbackFont = "Calibri";

foreach (WarningInfo warning in document.WarningCallback.Warnings)
{
    if (warning.Type == WarningType.FontSubstitution)
    {
        // Extract the missing font name from the warning message
        string missingFont = warning.Message.Split('\'')[1];
        Console.WriteLine($"Replacing missing font '{missingFont}' with '{fallbackFont}'");
        document.FontInfos[missingFont].SubstitutedFont = fallbackFont;
    }
}
```

> **Por que considerar isso?**  
> Garante consistência visual em todos os documentos gerados, o que é crucial para a conformidade da marca.

---

## Exemplo completo e executável

Abaixo está um único arquivo C# que você pode copiar‑colar em um aplicativo console. Ele cobre tudo—desde a instalação do pacote até a impressão dos avisos.

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create LoadOptions with warnings enabled
            LoadOptions loadOptions = new LoadOptions
            {
                FontSubstitutionWarnings = true
            };

            // 2️⃣ Load the DOCX (adjust the path as needed)
            string docPath = @"YOUR_DIRECTORY\input.docx";
            Document doc = new Document(docPath, loadOptions);

            // 3️⃣ Show all font‑substitution warnings
            Console.WriteLine("=== Font Substitution Warnings ===");
            foreach (WarningInfo warning in doc.WarningCallback.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ {warning.Message}");
                }
            }

            // 4️⃣ (Optional) Replace missing fonts with Calibri
            string fallback = "Calibri";
            foreach (WarningInfo warning in doc.WarningCallback.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    string missingFont = warning.Message.Split('\'')[1];
                    Console.WriteLine($"Replacing '{missingFont}' with '{fallback}'");
                    doc.FontInfos[missingFont].SubstitutedFont = fallback;
                }
            }

            // 5️⃣ Save the corrected document (optional)
            string outPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

**Execute**: `dotnet run` a partir da pasta do projeto. Se houver fontes ausentes, você verá os avisos impressos, e a substituição opcional será aplicada antes de salvar o arquivo.

---

## Perguntas frequentes

### Isso funciona também com conversão para PDF?

Sim. Depois de tratar os avisos, você pode chamar `doc.Save("output.pdf")` e as fontes substituídas aparecerão no PDF assim como no DOCX.

### E se eu precisar suprimir avisos para uma fonte específica?

Você pode filtrá‑los no loop—basta pular o `WarningInfo` cuja `Message` contenha o nome da fonte que deseja ignorar.

### O `FontSubstitutionWarnings` está disponível em versões mais antigas do Aspose.Words?

Foi introduzido na versão 20.5. Se você estiver preso a uma versão mais antiga, atualize via NuGet; a mudança na API é compatível com versões anteriores.

---

## Conclusão

Percorremos **como habilitar avisos**, mostramos **como detectar fontes ausentes**, e demonstramos a maneira correta **de carregar docx** com Aspose.Words enquanto mantemos total visibilidade das substituições de fonte. Ao inspecionar `document.WarningCallback.Warnings` você obtém um registro confiável—chega de substituições silenciosas.

Próximos passos? Experimente conectar a lógica de avisos a um framework de logging como Serilog, ou construir uma interface que destaque fontes ausentes antes de enviar o documento aos usuários. Você também pode explorar a classe `FontSettings` para um controle mais granular das políticas de substituição de fontes.

Feliz codificação, e que seus documentos sempre sejam renderizados exatamente como você pretende! 

![Diagrama ilustrando o fluxo de carregamento de um arquivo DOCX até a captura de avisos de substituição de fonte – como habilitar avisos no Aspose.Words](/images/font-warning-flow.png)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}