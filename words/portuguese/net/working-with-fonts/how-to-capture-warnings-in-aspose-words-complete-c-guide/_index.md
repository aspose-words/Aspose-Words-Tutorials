---
category: general
date: 2026-03-28
description: Como capturar avisos ao carregar um DOCX com Aspose.Words e obter mensagens
  de aviso para fontes ausentes. Aprenda a lidar com fontes ausentes de forma eficiente.
draft: false
keywords:
- how to capture warnings
- get warning messages
- handle missing fonts
- Aspose.Words warning callback
- font substitution warning
language: pt
og_description: Como capturar avisos ao carregar um DOCX com Aspose.Words, obter mensagens
  de aviso e lidar com fontes ausentes com exemplos de código práticos.
og_title: Como Capturar Avisos no Aspose.Words – Guia Completo em C#
tags:
- Aspose.Words
- C#
- Document Processing
title: Como Capturar Avisos no Aspose.Words – Guia Completo em C#
url: /pt/net/working-with-fonts/how-to-capture-warnings-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como Capturar Avisos no Aspose.Words – Guia Completo em C#

Já se perguntou **como capturar avisos** que aparecem ao carregar um documento Word com Aspose.Words? Talvez você esteja vendo alterações estranhas de fonte e precise saber exatamente o porquê. Em resumo, você pode conectar‑se ao sistema de avisos da biblioteca, **obter mensagens de aviso** e até **lidar com fontes ausentes** antes que elas estraguem seu layout.  

Neste tutorial vamos percorrer um cenário real: carregar um DOCX, coletar cada aviso que o motor gera e imprimir detalhes sobre qualquer substituição de fonte que ocorra. Ao final você terá um exemplo de código pronto‑para‑executar, entenderá o “porquê” de cada passo e saberá como estender a abordagem para seus próprios projetos.

## O que Você Vai Aprender

- Como configurar `LoadOptions` para que os avisos sejam capturados automaticamente.  
- A forma exata de **obter mensagens de aviso** a partir da `WarningInfoCollection`.  
- Como identificar e reagir a **fonts ausentes** via a flag `WarningType.FontSubstitution`.  
- Dicas para solucionar casos extremos, como documentos com fontes incorporadas ou pastas de fontes personalizadas.  

Nenhuma referência externa necessária – tudo que você precisa está aqui.

---

## Pré‑requisitos

- .NET 6.0 ou superior (o código também funciona no .NET Framework 4.7+).  
- Pacote NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`).  
- Um DOCX de exemplo (`input.docx`) que ou não contenha algumas fontes ou use fontes que não estejam instaladas na sua máquina.  

É só isso. Se você já está confortável com C# e Visual Studio, pode copiar‑colar o código e executá‑lo imediatamente.

---

## Etapa 1: Preparar Load Options e um Callback de Aviso

A primeira coisa que o Aspose.Words faz quando você chama `new Document(path, loadOptions)` é analisar o arquivo. Durante a análise ele pode encontrar fontes ausentes, recursos não suportados ou marcação obsoleta. Para capturar esses eventos você precisa de um objeto **callback de aviso**.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Step 1: Create a collection that will hold all warnings.
WarningInfoCollection warningCollector = new WarningInfoCollection();

// Step 2: Wire the collection into LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    // The library will push every warning into this collection.
    WarningCallback = warningCollector
};
```

**Por que isso importa:** Sem um callback, o Aspose.Words registra silenciosamente os avisos no console (ou os descarta), deixando você no escuro quanto a substituições de fonte que podem afetar o layout. Ao fornecer uma `WarningInfoCollection` dedicada, você ganha total visibilidade.

> **Dica profissional:** Se você se importa apenas com avisos relacionados a fontes, pode filtrá‑los depois – mas coletar *todos* os avisos lhe dá uma rede de segurança para problemas futuros.

---

## Etapa 2: Carregar o Documento com as Opções Configuradas

Agora que o callback está pronto, carregue o arquivo. O construtor `Document` invocará automaticamente o callback para quaisquer problemas que encontrar.

```csharp
// Step 3: Load the DOCX while capturing warnings.
string filePath = @"YOUR_DIRECTORY/input.docx";
Document doc = new Document(filePath, loadOptions);
```

**O que está acontecendo nos bastidores?** O Aspose.Words analisa o Open XML, resolve estilos e tenta mapear cada referência de fonte para uma fonte instalada no sistema. Se não houver correspondência, ele cria uma entrada `WarningInfo` do tipo `FontSubstitution`.

---

## Etapa 3: Recuperar e Inspecionar os Avisos Coletados

Depois que o carregamento termina, seu `warningCollector` contém todos os avisos que ocorreram. Vamos extraí‑los e focar nas mensagens de substituição de fonte.

```csharp
// Step 4: Iterate through the collected warnings.
foreach (WarningInfo warning in warningCollector)
{
    // Only interested in font‑substitution warnings?
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Font substituted: {warning.Description}");
    }
}
```

**Saída de exemplo** (seu console pode mostrar algo como):

```
Font substituted: Font "Comic Sans MS" was not found. Substituted with "Arial".
Font substituted: Font "Times New Roman" was not found. Substituted with "Liberation Serif".
```

Se quiser *todos* os avisos, basta remover a verificação `if` ou registrar `warning.Type` para cada entrada.

---

## Etapa 4: Lidando com Fonts Ausentes – Mais do que Apenas Logar

Capturar avisos é útil, mas muitas vezes você precisa **tratar fontes ausentes** programaticamente. Aqui estão duas estratégias comuns:

### 4.1 Substituir Fonts Ausentes por um Fallback Específico

```csharp
// Define a fallback font that you know is available.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Calibri";

// Apply the settings before loading (or after, if you reload).
loadOptions.FontSettings = fontSettings;
```

Agora qualquer fonte ausente será trocada por *Calibri* em vez do fallback padrão da biblioteca.

### 4.2 Incorporar uma Fonte Substituta Dinamicamente

Se você tem um arquivo de fonte personalizado (por exemplo, `MyFallback.ttf`) pode registrá‑lo em tempo de execução:

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyFonts", true); // true = recursive search
loadOptions.FontSettings = fontSettings;
```

Essa abordagem é prática quando você distribui uma fonte corporativa específica com sua aplicação.

> **Caso extremo:** Documentos que já incorporam a fonte necessária ignorarão as regras de substituição do sistema. Nesse cenário, a coleção de avisos ficará vazia para essa fonte, que é exatamente o que você deseja.

---

## Etapa 5: Exemplo Completo (Pronto para Copiar‑Colar)

Abaixo está um programa autocontido que demonstra tudo, do início ao fim. Basta substituir `YOUR_DIRECTORY/input.docx` pelo caminho do seu arquivo de teste.

```csharp
// ------------------------------------------------------------
// Complete example: Capture warnings and handle missing fonts
// ------------------------------------------------------------
using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare a warning collector.
        WarningInfoCollection warningCollector = new WarningInfoCollection();

        // 2️⃣ Configure LoadOptions with the collector.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = warningCollector
        };

        // OPTIONAL: Set a global fallback font (e.g., Calibri).
        FontSettings fontSettings = new FontSettings();
        fontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Calibri";
        loadOptions.FontSettings = fontSettings;

        // 3️⃣ Load the document.
        string filePath = @"YOUR_DIRECTORY/input.docx";
        Document doc = new Document(filePath, loadOptions);

        // 4️⃣ Process warnings – focus on font substitution.
        Console.WriteLine("=== Font Substitution Warnings ===");
        foreach (WarningInfo warning in warningCollector)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine($"⚠️ {warning.Description}");
            }
        }

        // 5️⃣ (Optional) Save the document to verify that the fallback was applied.
        string outPath = @"YOUR_DIRECTORY/output.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**O que esperar**

- O console imprime cada aviso de substituição de fonte, precedido por um emoji de aviso para maior visibilidade.  
- O DOCX de saída (`output.docx`) usa *Calibri* onde quer que uma fonte ausente tenha sido detectada.  
- Nenhuma exceção não tratada – o sistema de avisos lida graciosamente com qualquer fonte desconhecida.

---

## Perguntas Frequentes

**P: Isso funciona com PDFs gerados a partir do Word?**  
R: Sim. O Aspose.Words trata PDFs como outro formato de saída. A captura de avisos ocorre durante a fase de *load*, portanto é independente da exportação final.

**P: E se eu precisar capturar avisos para **todas** as operações de documento (salvar, converter, etc.)?**  
R: Você pode reutilizar a mesma `WarningInfoCollection` atribuindo‑a a `Document.WarningCallback` após a instância do documento ser criada. Cada operação subsequente adicionará novas entradas à mesma coleção.

**P: O callback de aviso afeta o desempenho?**  
R: De forma insignificante. A coleção apenas armazena objetos; a menos que você esteja processando milhares de avisos em um loop apertado, não notará desaceleração.

**P: Como suprimir avisos que não me interessam?**  
R: Implemente uma classe customizada que herde de `IWarningCallback` e filtre dentro do método `Warning`. O `WarningInfoCollection` embutido apenas armazena, não filtra.

---

## Dicas Profissionais & Armadilhas

- **Dica profissional:** Sempre inspecione `Warning.Description` – ele contém o nome exato da fonte que estava faltando. Isso pode ajudar a decidir se você deve distribuir a fonte com seu app.  
- **Fique atento às fontes incorporadas:** Se o DOCX de origem já incorpora a fonte necessária, o Aspose.Words não emitirá um aviso de substituição, mesmo que a fonte não esteja instalada localmente.  
- **Segurança em threads:** `WarningInfoCollection` não é thread‑safe. Se você carregar vários documentos simultaneamente, dê a cada thread sua própria coleção.  
- **Verificação de versão:** A API de avisos está estável desde o Aspose.Words 20.8. Certifique‑se de estar usando uma versão recente para não perder novos tipos de aviso.

---

## Conclusão

Cobrimos **como capturar avisos** do Aspose.Words, demonstramos como **obter mensagens de aviso** e mostramos maneiras práticas de **lidar com fontes ausentes** por meio de fontes fallback ou pastas de fontes personalizadas. O exemplo completo está pronto para ser inserido em qualquer projeto .NET, e os conceitos escalam para pipelines de automação maiores.

Próximos passos sugeridos:

- Usar `Document.WarningCallback` para capturar avisos durante operações de **salvar**.  
- Registrar avisos em um arquivo ou sistema de telemetria para monitoramento em produção.  
- Estender o callback para substituir automaticamente fontes ausentes por tipografias específicas da sua marca.

Sinta‑se à vontade para experimentar – troque a fonte fallback, adicione mais documentos ao lote ou integre o coletor de avisos a um pipeline CI que sinalize regressões relacionadas a fontes. Boa codificação, e que seus documentos sempre renderizem exatamente como você espera!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}