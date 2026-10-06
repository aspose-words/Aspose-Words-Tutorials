---
category: general
date: 2026-01-14
description: Registre avisos de substituição de fontes ao carregar documentos do Word
  com Aspose.Words. Aprenda a detectar fontes ausentes e como capturar fontes ausentes
  em C#.
draft: false
keywords:
- log font substitution warnings
- detect missing fonts
- how to capture missing fonts
language: pt
og_description: Registre avisos de substituição de fontes ao carregar documentos Word
  com Aspose.Words. Descubra como detectar fontes ausentes e capturá‑las em C#.
og_title: Registrar avisos de substituição de fontes – Guia completo do Aspose.Words
tags:
- Aspose.Words
- C#
- Document Processing
title: Registro de Avisos de Substituição de Fonte – Guia Completo do Aspose.Words
url: /pt/net/working-with-fonts/log-font-substitution-warnings-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Registro de Avisos de Substituição de Fonte – Guia Completo do Aspose.Words

Registrar avisos de substituição de fonte é essencial quando você precisa garantir que um documento Word tenha exatamente a mesma aparência depois de carregado pelo Aspose.Words. Se você já se perguntou como **detectar fontes ausentes** ou quer saber **como capturar fontes ausentes**, está no lugar certo.  

Neste tutorial percorreremos um cenário real, mostraremos o código C# completo e explicaremos por que cada linha é importante. Ao final, você será capaz de registrar cada evento de substituição de fonte e agir sobre ele — sem avisos misteriosos restantes.

![Exemplo de registro de avisos de substituição de fonte](/images/font-warnings.png "Captura de tela mostrando a saída do console ao registrar avisos de substituição de fonte")

## O Que Você Vai Aprender

- Como configurar `LoadOptions` para que o Aspose.Words emita avisos tipados para substituição de fonte.  
- Os passos exatos para **detectar fontes ausentes** durante o carregamento do documento.  
- Uma forma limpa de **capturar fontes ausentes** e gravá‑las no seu próprio log ou sistema de monitoramento.  
- Tratamento de casos extremos (por exemplo, quando um documento contém uma fonte que não está instalada no servidor).  

### Pré‑requisitos

- .NET 6.0 ou superior (o código também funciona com .NET Framework 4.6+).  
- Uma licença válida do Aspose.Words for .NET (ou a versão de avaliação).  
- Familiaridade básica com C# e aplicações de console.  

Se você já tem isso, vamos começar.

## Etapa 1 – Configurar LoadOptions para Emitir Avisos Tipados

O coração da solução está em `LoadOptions.FontSubstitutionWarning`. Ao alterá‑lo para `RaiseTypedWarnings` você indica ao Aspose.Words que dispare um evento **toda vez** que não encontrar a fonte exata solicitada.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class Program
{
    static void Main()
    {
        // Step 1: Create a LoadOptions instance that will raise warnings.
        var loadOptions = new LoadOptions
        {
            // This flag makes Aspose.Words emit detailed warnings instead of silently substituting.
            FontSubstitutionWarning = LoadOptions.FontSubstitutionWarningOption.RaiseTypedWarnings
        };
```

> **Por que isso importa:**  
> O comportamento padrão troca silenciosamente uma fonte ausente pela mais próxima, o que pode gerar falhas de layout que você nunca percebe. Emitir avisos tipados fornece total visibilidade.

## Etapa 2 – Inscrever‑se no Evento de Aviso

Agora conectamos ao `loadOptions.FontSubstitutionWarning`. A expressão lambda recebe um objeto `e` que informa exatamente qual fonte estava ausente e qual foi usada em seu lugar.

```csharp
        // Step 2: Attach an event handler to capture each substitution.
        loadOptions.FontSubstitutionWarning += (sender, e) =>
        {
            // Log to console – replace with your own logger if needed.
            Console.WriteLine($"Missing font: {e.FontName} – substituted with {e.SubstitutedFontName}");
        };
```

> **Dica profissional:** Se você executar isso em um servidor web, substitua `Console.WriteLine` por um logger estruturado (Serilog, NLog, etc.) para poder consultar os dados posteriormente.

## Etapa 3 – Carregar o Documento Usando as Opções Configuradas

Com o mecanismo de aviso configurado, basta carregar o documento como de costume. O evento é disparado automaticamente para cada fonte ausente.

```csharp
        // Step 3: Load the target document while the warning handler is active.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath, loadOptions);

        // Optional: do something with the document – e.g., save as PDF.
        // doc.Save(@"YOUR_DIRECTORY\output.pdf");
    }
}
```

### Saída Esperada no Console

Se `input.docx` referencia uma fonte chamada *MyFancyFont* que não está instalada, você verá:

```
Missing font: MyFancyFont – substituted with Arial
Missing font: AnotherMissingFont – substituted with Times New Roman
```

Cada linha corresponde a um evento de **detectar fontes ausentes**, fornecendo um registro completo.

## Etapa 4 – Tratamento de Casos Extremos e Cenários Avançados

### 4.1 Quando Nenhuma Substituição Ocorre

Às vezes um documento usa apenas fontes do sistema que já estão presentes. Nesse caso o evento de aviso nunca dispara, e o console fica limpo, sem saída. Isso é um bom sinal — seu ambiente já possui todas as fontes necessárias.

### 4.2 Capturando Avisos para Análise Posterior

Se precisar armazenar os avisos para um relatório noturno, cole‑os em uma lista:

```csharp
        var missingFonts = new List<(string Original, string Substituted)>();
        loadOptions.FontSubstitutionWarning += (s, e) =>
        {
            missingFonts.Add((e.FontName, e.SubstitutedFontName));
            Console.WriteLine($"Missing font: {e.FontName} – substituted with {e.SubstitutedFontName}");
        };
```

Após o carregamento, você pode serializar `missingFonts` para JSON, gravar em um banco de dados ou enviar um resumo por e‑mail.

### 4.3 Trabalhando com PDFs ou Outros Formatos

A mesma abordagem de `LoadOptions` funciona para chamadas `Load` em PDFs, RTF e até arquivos HTML. Basta passar a mesma instância de opções, e o Aspose.Words emitirá avisos para qualquer fonte que não puder corresponder.

## Etapa 5 – Verificar o Resultado Programaticamente

Se preferir um teste automatizado em vez de observar o console, verifique se a lista contém as entradas esperadas:

```csharp
        // Simple verification (use a testing framework in real projects)
        if (missingFonts.Count == 0)
        {
            Console.WriteLine("All fonts were available – no substitution warnings.");
        }
        else
        {
            Console.WriteLine($"Total missing fonts detected: {missingFonts.Count}");
        }
```

Este trecho demonstra **como capturar fontes ausentes** no código, não apenas nos logs.

## Armadilhas Comuns & Como Evitá‑las

| Armadilha | Por que Acontece | Solução |
|-----------|------------------|---------|
| Esquecer de definir `RaiseTypedWarnings` | O padrão é `DoNotRaise`, então nenhum evento é disparado. | Defina explicitamente `FontSubstitutionWarning` como mostrado na Etapa 1. |
| Usar `Console.WriteLine` em uma aplicação web | A saída do console desaparece no IIS/ASP.NET Core. | Troque por um logger persistente (ex.: Serilog). |
| Carregar um documento com caminho relativo | O diretório de trabalho pode ser diferente em tempo de execução. | Use caminhos absolutos ou `Path.Combine(AppContext.BaseDirectory, "input.docx")`. |
| Ignorar `SubstitutedFontName` | Você perde a visão de qual fonte de fallback foi escolhida. | Sempre registre tanto `FontName` quanto `SubstitutedFontName`. |

## Bônus: Automatizando a Instalação de Fontes

Se você controla o ambiente de implantação, pode pré‑instalar as fontes ausentes usando um script PowerShell:

```powershell
$fonts = @("MyFancyFont.ttf", "AnotherMissingFont.otf")
foreach ($font in $fonts) {
    $dest = "$env:SystemRoot\Fonts\$font"
    Copy-Item -Path ".\fonts\$font" -Destination $dest -Force
}
```

Executar isso antes da sua aplicação iniciar elimina a maioria dos avisos de **detectar fontes ausentes**.

## Conclusão

Cobremos tudo o que você precisa para **registrar avisos de substituição de fonte** ao carregar documentos Word com Aspose.Words. Configurando `LoadOptions`, inscrevendo‑se no evento de aviso e, opcionalmente, persistindo os resultados, você pode detectar fontes ausentes de forma confiável e entender **como capturar fontes ausentes** em qualquer projeto .NET.

Pegue o código, ajuste o logger ao seu stack e nunca mais será surpreendido por uma troca silenciosa de fonte. Próximos passos podem incluir:

- Integrar a lista de avisos ao seu pipeline CI/CD para falhar builds quando fontes críticas estiverem ausentes.  
- Expandir a abordagem para monitorar o uso de fontes em um grande volume de documentos.  
- Explorar a API `FontSettings` do Aspose.Words para fornecer fontes de fallback personalizadas.

Tem dúvidas ou um cenário complicado? Deixe um comentário e vamos solucionar juntos. Boa codificação!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}