---
category: general
date: 2026-02-18
description: Aprenda a capturar avisos de fontes e detectar fontes ausentes em C#
  usando Aspose.Words. Siga este guia passo a passo para lidar com fontes ausentes
  de forma eficiente.
draft: false
keywords:
- capture font warnings
- detect missing fonts
- handle missing fonts
- list missing fonts
language: pt
og_description: Capture avisos de fontes em C# e aprenda a detectar fontes ausentes,
  lidar com fontes ausentes e listar fontes ausentes com um exemplo de código completo.
og_title: Capturar Avisos de Fonte em C# – Guia Completo
tags:
- Aspose.Words
- C#
- Font Management
title: Capturar avisos de fonte em C# – Guia completo de programação
url: /pt/net/working-with-fonts/capture-font-warnings-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Capturando Avisos de Fonte em C# – Guia Completo de Programação

Já se perguntou como **capturar avisos de fonte** quando um documento referencia uma fonte que não está instalada no servidor? Você não está sozinho. Em muitas aplicações corporativas, fontes ausentes causam falhas de layout, e a única maneira confiável de detectá‑las é ouvindo os avisos que a biblioteca gera.  

Neste tutorial mostraremos uma solução pronta‑para‑executar que não só **captura avisos de fonte**, mas também **detecta fontes ausentes**, **trata fontes ausentes** e ainda **lista fontes ausentes**, permitindo que você decida substituir, incorporar ou alertar o usuário. Nenhuma documentação externa necessária — basta copiar, colar e executar.

## O que Você Vai Aprender

- Como configurar `LoadOptions` para ativar avisos de substituição de fonte.  
- O código exato que você precisa para carregar um DOCX e extrair cada aviso.  
- Por que cada passo importa, incluindo considerações de desempenho.  
- Tratamento de casos extremos, como documentos com fontes de scripts mistos ou pastas de fontes personalizadas.  

**Pré‑requisitos**: .NET 6+ (ou .NET Framework 4.6+), uma referência ao pacote NuGet **Aspose.Words**, e conhecimento básico de C#. Se você nunca usou Aspose.Words antes, não se preocupe — este guia o conduz por cada detalhe.

![Diagram showing capture font warnings flow](image.png){alt="Diagrama mostrando o fluxo de captura de avisos de fonte"}

## Capturando Avisos de Fonte – Por que Isso Importa

Quando o Aspose.Words carrega um documento, ele silenciosamente troca qualquer fonte indisponível por uma alternativa. Essa alternativa mantém a operação de carregamento viva, mas o resultado visual pode ficar completamente desalinhado. Ao ativar a flag **SubstitutionWarningLevel.All**, a biblioteca adiciona uma entrada `WarningInfo` para cada fonte ausente, permitindo que você **detecte fontes ausentes** antes que o documento seja renderizado ou salvo.

> **Dica profissional:** Se você estiver processando centenas de arquivos em um job em lote, registrar esses avisos em um repositório central pode economizar horas de QA manual depois.

## Etapa 1: Configurar Seu Projeto

1. Abra sua IDE favorita (Visual Studio, Rider, VS Code).  
2. Crie um novo projeto de console:

```bash
dotnet new console -n FontWarningDemo
cd FontWarningDemo
```

3. Adicione o pacote Aspose.Words:

```bash
dotnet add package Aspose.Words
```

É isso — sem DLLs extras, sem interop COM. A biblioteca já inclui tudo que você precisa para **tratar fontes ausentes**.

## Etapa 2: Preparar LoadOptions para Capturar Todos os Avisos de Substituição de Fonte

Para fazer o motor **capturar avisos de fonte**, você deve instruí‑lo a registrar cada substituição. O trecho a seguir cria uma instância `LoadOptions`, habilita o nível de aviso e (opcionalmente) aponta o motor para uma pasta que contém fontes personalizadas que você possa querer usar.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // -----------------------------------------------------------------
            // Step 2.1 – Create LoadOptions and turn on font‑substitution warnings
            // -----------------------------------------------------------------
            LoadOptions loadOptions = new LoadOptions();

            // Initialise FontSettings if you need to add a custom font folder
            loadOptions.FontSettings = new FontSettings();

            // Capture *all* font substitution events (this is the key for capture font warnings)
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSettings.SubstitutionWarningLevel.All;

            // Optional: add a folder that contains corporate fonts
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", false);
```

**Por que isso importa:**  
- `SubstitutionWarningLevel.All` garante que **todos** os eventos de fonte ausente sejam registrados, não apenas o primeiro.  
- Sem essa flag, o Aspose.Words substitui a fonte silenciosamente e você nunca saberá que há um problema.

## Etapa 3: Carregar o Documento Usando as Opções Configuradas

Agora realmente abrimos o arquivo. Substitua `DocumentWithMissingFonts.docx` pelo caminho do seu documento de teste.

```csharp
            // -----------------------------------------------------------------
            // Step 2.2 – Load the document with the warning‑enabled options
            // -----------------------------------------------------------------
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFonts.docx";

            Document document = new Document(docPath, loadOptions);
```

Se o arquivo contiver referências a fontes que não estão na máquina (ou na pasta opcional que você adicionou), a `document.WarningInfoCollection` será preenchida.

## Etapa 4: Encontrar e Exibir Qualquer Aviso de Substituição de Fonte

Aqui está o coração do tutorial: iterar sobre a `WarningInfoCollection` para **listar fontes ausentes**. Vamos filtrar por `WarningType.FontSubstitution` e imprimir uma mensagem amigável.

```csharp
            // -----------------------------------------------------------------
            // Step 2.3 – Enumerate and output font substitution warnings
            // -----------------------------------------------------------------
            var fontWarnings = document.WarningInfoCollection
                                         .Where(w => w.WarningType == WarningType.FontSubstitution);

            if (!fontWarnings.Any())
            {
                Console.WriteLine("✅ No missing fonts detected – all good!");
            }
            else
            {
                Console.WriteLine("⚠️ Missing fonts detected:");
                foreach (WarningInfo warning in fontWarnings)
                {
                    // The Description property already contains a readable message
                    Console.WriteLine($"- {warning.Description}");
                }
            }

            // Keep console window open when debugging
            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

### Saída Esperada

```
⚠️ Missing fonts detected:
- Missing font: "Comic Sans MS"
- Missing font: "Calibri Light"
```

Se o documento usar apenas fontes instaladas, você verá a linha “✅ No missing fonts detected”.

## Etapa 5: Avançado – Como **Tratar Fontes Ausentes** Programaticamente

Imprimir apenas uma lista pode ser suficiente para uma ferramenta de diagnóstico, mas muitos sistemas de produção precisam **tratar fontes ausentes** automaticamente. Abaixo estão duas estratégias comuns:

### 5.1 Substituir por um Fallback Conhecido

```csharp
loadOptions.FontSettings.DefaultFontSubstitution = new FontSettings.FontSubstitution
{
    // Replace any missing font with Arial, which is universally available
    SubstituteFont = "Arial"
};
```

### 5.2 Incorporar uma Fonte Personalizada em Tempo de Execução

Se você tem um arquivo de fonte corporativa (`MyBrand.ttf`), pode incorporá‑la quando uma fonte ausente for detectada:

```csharp
foreach (WarningInfo warning in fontWarnings)
{
    string missingFontName = warning.Description.Split('"')[1]; // crude extraction
    // Load your custom font (ensure the path is correct)
    string customFontPath = $@"C:\MyCompany\Fonts\{missingFontName}.ttf";

    if (File.Exists(customFontPath))
    {
        loadOptions.FontSettings.SetFontsFolder(Path.GetDirectoryName(customFontPath), false);
        Console.WriteLine($"🔧 Embedded custom font for \"{missingFontName}\"");
    }
}
```

> **Observação:** Incorporar fontes pode aumentar o tamanho do arquivo de saída, portanto pese o trade‑off entre fidelidade e largura de banda.

## Armadilhas Comuns e Como Evitá‑las

| Sintoma | Causa Provável | Solução |
|---------|----------------|---------|
| Nenhum aviso aparece mesmo que o documento pareça errado | `SubstitutionWarningLevel` não definido como `All` | Garanta que a Etapa 2 configure a flag exatamente como mostrado |
| Avisos listam a mesma fonte várias vezes | O documento contém a fonte em vários estilos | Des‑duplique se precisar apenas de uma lista única: `fontWarnings.Select(w => w.Description).Distinct()` |
| Aplicação falha em arquivos DOCX grandes | Carregamento com configurações de memória padrão | Use `LoadOptions.LoadFormat` ou faça streaming do arquivo para reduzir a pressão de memória |

## Exemplo Completo Funcional (Pronto para Copiar‑Colar)

```csharp
using System;
using System.IO;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // ---------------------------------------------------------------
            // Configure LoadOptions to capture font warnings
            // ---------------------------------------------------------------
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSettings.SubstitutionWarningLevel.All;

            // OPTIONAL: add a folder with custom fonts
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", false);

            // ---------------------------------------------------------------
            // Load the document
            // ---------------------------------------------------------------
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFonts.docx";
            Document doc = new Document(docPath, loadOptions);

            // ---------------------------------------------------------------
            // Retrieve and display missing‑font warnings
            // ---------------------------------------------------------------
            var fontWarnings = doc.WarningInfoCollection
                                  .Where(w => w.WarningType == WarningType.FontSubstitution);

            if (!fontWarnings.Any())
            {
                Console.WriteLine("✅ No missing fonts detected – all good!");
            }
            else
            {
                Console.WriteLine("⚠️ Missing fonts detected:");
                foreach (WarningInfo warning in fontWarnings)
                {
                    Console.WriteLine($"- {warning.Description}");
                }
            }

            // ---------------------------------------------------------------
            // OPTIONAL: automatic handling (fallback or embedding)
            // ---------------------------------------------------------------
            // Example: substitute everything with Arial
            // loadOptions.FontSettings.DefaultFontSubstitution = new FontSettings.FontSubstitution { SubstituteFont = "Arial" };

            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

Execute o programa com `dotnet run`. Você deverá ver a lista de fontes ausentes impressa no console, confirmando que você capturou com sucesso os **avisos de fonte**.

## Conclusão

Agora você tem um padrão completo e pronto para produção para **capturar avisos de fonte**, **detectar fontes ausentes**, **tratar fontes ausentes** e **listar fontes ausentes** usando Aspose.Words em C#. A abordagem é leve, requer apenas algumas linhas de código e pode ser inserida em qualquer pipeline existente — seja você

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}