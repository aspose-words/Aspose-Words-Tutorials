---
category: general
date: 2026-03-19
description: Aprenda como capturar avisos no Aspose.Words, definir configurações de
  fonte padrão e detectar fontes ausentes ao carregar um documento do Word.
draft: false
keywords:
- how to capture warnings
- set default font settings
- load word document
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
language: pt
og_description: Como capturar avisos no Aspose.Words, definir configurações de fonte
  padrão e detectar fontes ausentes ao carregar um documento Word.
og_title: Como Capturar Avisos – Definir Configurações de Fonte Padrão
tags:
- Aspose.Words
- C#
- Document Processing
title: Como Capturar Avisos – Definir Configurações de Fonte Padrão
url: /pt/net/working-with-fonts/how-to-capture-warnings-set-default-font-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como Capturar Avisos – Definir Configurações de Fonte Padrão

**Como capturar avisos** é uma necessidade comum ao trabalhar com Aspose.Words, especialmente se seus documentos dependem de fontes específicas que podem não estar presentes na máquina de destino. Já abriu um DOCX e se perguntou por que o layout ficou estranho? A resposta costuma estar escondida em um aviso sobre uma fonte ausente.  

Neste guia vamos percorrer **como capturar avisos** enquanto você **carrega documento Word**, configura **definir configurações de fonte padrão**, e finalmente **detecta fontes ausentes** para que possa reagir programaticamente. Sem enrolação — apenas um exemplo completo e executável e o raciocínio por trás de cada linha.

> *Dica de especialista:* Capturar avisos cedo salva você de depurar falhas misteriosas de layout depois.

---

## O Que Você Precisa

- **Aspose.Words for .NET** (última versão em 2026).  
- Um ambiente de desenvolvimento .NET (Visual Studio, Rider ou VS Code).  
- Um DOCX de exemplo que faça referência a uma fonte que você *não* tem instalada (por exemplo, *Comic Sans MS* em um Linux).  

É só isso. Nenhum pacote NuGet adicional é necessário além do Aspose.Words.

---

## Etapa 1 – Entenda Por Que Você Precisa Capturar Avisos

Quando o Aspose.Words analisa um documento, ele pode encontrar fontes que não estão disponíveis no host. Por padrão, a biblioteca substitui silenciosamente por uma fonte de fallback, o que pode mudar quebras de linha, espaçamento e até fazer o texto desaparecer.  

Usar o **WarningCallback** junto com um objeto **FontSettings** oferece duas coisas:

1. **Visibilidade** – você recebe uma entrada `WarningInfo` para cada substituição.  
2. **Controle** – pode pré‑configurar uma fonte padrão para minimizar surpresas visuais.

Pense nisso como instalar um “cão de guarda” que grita toda vez que o motor troca uma peça sob o capô.

---

## Etapa 2 – Definir Configurações de Fonte Padrão

A primeira palavra‑chave secundária, **set default font settings**, aparece aqui. Você cria uma instância `FontSettings` e, opcionalmente, aponta para uma pasta que contém suas fontes de fallback.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

// Create a FontSettings object and point it to a folder with fallback fonts (optional)
var fontSettings = new FontSettings();
// Example: fontSettings.SetFontsFolder(@"C:\MyFallbackFonts", true);
```

> **Por quê?**  
> Se você não especificar um fallback, o Aspose.Words escolhe a primeira fonte do sistema que corresponde ao estilo, o que pode ser muito diferente. Ao definir um padrão conhecido, você garante renderização consistente entre máquinas.

---

## Etapa 3 – Preparar um Warning Callback para Capturar Avisos

Agora vamos **how to capture warnings** anexando um `WarningInfoCollection` às opções de carregamento. Essa coleção armazenará cada aviso emitido durante o processo de carregamento.

```csharp
// Step 3: Prepare a list that will collect warning information
var warningInfos = new List<WarningInfo>();

// Create a WarningInfoCollection that forwards warnings to our list
var warningCallback = new WarningInfoCollection(warningInfos);
```

O `WarningInfoCollection` implementa `IWarningCallback`, então o Aspose.Words envia automaticamente cada aviso para `warningInfos`. Nenhuma sondagem necessária.

---

## Etapa 4 – Carregar Documento Word com as Opções Configuradas

Aqui é onde a segunda palavra‑chave secundária, **load word document**, brilha. Passamos tanto o `FontSettings` quanto o `WarningCallback` através de uma instância `LoadOptions`.

```csharp
// Step 4: Build LoadOptions with our font settings and warning callback
var loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = warningCallback
};

// Load the DOCX – this is the moment we actually **load word document**
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

Se o documento fizer referência a uma fonte que não está instalada, o callback de aviso capturará uma entrada `WarningType.FontSubstitution`.

---

## Etapa 5 – Detectar Fontes Ausentes a Partir dos Avisos Coletados

Por fim, respondemos à terceira palavra‑chave secundária, **detect missing fonts**, iterando sobre os avisos coletados.

```csharp
// Step 5: Examine the collected warnings for any font substitution events
foreach (var warning in warningInfos)
{
    if (warning.WarningType == WarningType.FontSubstitution)
    {
        Console.WriteLine($"⚠️ Font substitution detected: {warning.Description}");
    }
}
```

A saída típica se parece com:

```
⚠️ Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Essa linha informa exatamente qual fonte está ausente e qual fallback foi usado — informação que você pode registrar, exibir ao usuário ou até mesmo acionar uma rotina personalizada de instalação de fontes.

---

## Exemplo Completo Executável

Abaixo está o programa completo que você pode copiar‑colar em uma aplicação console. Ele demonstra **como capturar avisos**, **definir configurações de fonte padrão**, **carregar documento Word** e **detectar fontes ausentes** tudo em um único fluxo.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace CaptureWarningsDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Prepare a list to collect warning information during loading
            var warningInfos = new List<WarningInfo>();

            // 2️⃣ Configure load options – this is where we **set default font settings**
            var fontSettings = new FontSettings();
            // Uncomment and adjust the line below if you have a fallback folder:
            // fontSettings.SetFontsFolder(@"C:\MyFallbackFonts", true);

            var loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new WarningInfoCollection(warningInfos)
            };

            // 3️⃣ **Load word document** with the configured options
            string docPath = @"YOUR_DIRECTORY/MissingFont.docx";
            Document document = new Document(docPath, loadOptions);

            // 4️⃣ **Detect missing fonts** by scanning the collected warnings
            Console.WriteLine("Scanning for font substitution warnings...");
            foreach (var warning in warningInfos)
            {
                if (warning.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ {warning.Description}");
                }
            }

            // Optional: keep console window open
            Console.WriteLine("Done. Press any key to exit.");
            Console.ReadKey();
        }
    }
}
```

**Resultado esperado:** Quando o DOCX especificado referenciar uma fonte que não está instalada, o console imprimirá um aviso para cada substituição. Se todas as fontes estiverem presentes, o laço não produzirá saída.

---

## Armadilhas Comuns & Casos de Borda

| Situação | Por que acontece | Como lidar |
|-----------|----------------|------------------|
| **Nenhum aviso aparece** mesmo que o layout esteja errado | O documento pode estar usando fontes *incorporadas*, que o Aspose.Words renderiza sem substituição. | Verifique `Document.HasEmbeddedFonts` e considere extrair as fontes incorporadas se precisar delas em outra máquina. |
| **Múltiplos avisos para o | 

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}