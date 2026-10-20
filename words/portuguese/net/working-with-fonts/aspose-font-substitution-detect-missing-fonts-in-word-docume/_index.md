---
category: general
date: 2026-04-05
description: Guia de substituição de fontes da Aspose para detectar fontes ausentes
  ao carregar um documento Word. Aprenda a configurar as configurações de fontes e
  lidar com fontes ausentes de forma eficiente.
draft: false
keywords:
- aspose font substitution
- detect missing fonts
- load word document
- configure font settings
- handle missing fonts
language: pt
og_description: Guia de substituição de fontes da Aspose para detectar fontes ausentes
  ao carregar um documento Word. Aprenda a configurar as definições de fonte e lidar
  com fontes ausentes de forma eficiente.
og_title: Substituição de Fontes Aspose – Detectar Fontes Ausentes em Documentos Word
tags:
- Aspose.Words
- C#
- Font Management
title: Substituição de Fonte Aspose – Detectar Fontes Ausentes em Documentos Word
url: /pt/net/working-with-fonts/aspose-font-substitution-detect-missing-fonts-in-word-docume/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Substituição de Fonte Aspose – Detectar Fontes Ausentes em Documentos Word

Já se deparou com um arquivo Word que parece perfeito em uma máquina, mas apresenta alterações estranhas de fonte em outra? Esse é o clássico problema de **aspose font substitution**, e geralmente significa que algumas fontes estão ausentes no sistema de destino. Neste tutorial, mostraremos, passo a passo, como **detectar fontes ausentes** ao **carregar um documento Word**, como **configurar as definições de fonte**, e o que fazer para **tratar fontes ausentes** de forma elegante.

Vamos percorrer um exemplo completo e executável em C#, explicar por que cada linha importa e até mostrar a saída do console que você deve esperar. Ao final, você será capaz de identificar substituições de fonte no instante em que um documento é carregado — sem adivinhações.

## O que Você Vai Aprender

- Como habilitar o coletor diagnóstico do Aspose.Words para avisos de fonte.  
- O código exato necessário para **carregar um documento Word** com **definições de fonte** personalizadas.  
- Como iterar sobre objetos `WarningInfo` para listar cada fonte substituída.  
- Dicas para suprimir avisos indesejados ou fornecer fontes alternativas.  
- Um exemplo pronto‑para‑executar que você pode copiar‑colar no Visual Studio.

### Pré‑requisitos

- .NET 6.0 ou superior (a API funciona da mesma forma no .NET Framework).  
- Aspose.Words for .NET (pacote NuGet `Aspose.Words`).  
- Um arquivo Word que faça referência a uma fonte que você não tenha instalada (por exemplo, `MissingFont.docx`).  

Se você tem tudo isso, vamos mergulhar.

## Etapa 1 – Habilitar o Coletor Diagnóstico (Configurar Definições de Fonte)

Primeiro de tudo: o Aspose.Words só registra avisos de substituição de fonte se você o instruir a fazê‑lo. Isso é feito criando um objeto `FontSettings` e atribuindo‑o a uma instância de `LoadOptions`. Pense nisso como ligar as “luzes de depuração” para o tratamento de fontes.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Prepare load options with a fresh FontSettings instance.
LoadOptions loadOptions = new LoadOptions
{
    // The FontSettings object is the hub for all font‑related configuration.
    FontSettings = new FontSettings()
};
```

**Por quê?**  
Sem um objeto `FontSettings` o coletor de avisos permanece silencioso, e você nunca saberá quais fontes foram trocadas. Ao inicializá‑lo vazio, deixamos o Aspose usar as fontes padrão do sistema *e* acompanhar quaisquer substituições.

> **Dica profissional:** Se você souber que uma pasta específica contém fontes corporativas, aponte `FontSettings` para ela com `SetFontsFolder("caminho")`. Isso pode reduzir o número de avisos de fontes ausentes.

## Etapa 2 – Carregar o Documento com as Opções Configuradas (Carregar Documento Word)

Agora que o coletor está ativo, carregue seu arquivo `.docx` usando o mesmo `LoadOptions`. Este é o momento em que o Aspose analisa o documento, procura cada referência de fonte e decide se uma substituição é necessária.

```csharp
// Step 2: Load the Word file while applying the previously defined load options.
Document document = new Document(@"C:\Docs\MissingFont.docx", loadOptions);
```

**Por que isso importa?**  
Se você simplesmente chamar `new Document("MissingFont.docx")`, as configurações padrão seriam aplicadas *e* a lista de avisos ficaria vazia. Passar `loadOptions` garante que o coletor diagnóstico esteja conectado ao pipeline de carregamento.

## Etapa 3 – Recuperar e Exibir Avisos de Substituição de Fonte (Detectar Fontes Ausentes)

Depois que o documento estiver na memória, o Aspose armazena quaisquer avisos em `document.WarningCallback.Warnings`. Percorra essa coleção, filtre por `WarningType.FontSubstitution` e imprima a descrição. Cada descrição informa qual fonte estava ausente e qual foi usada em seu lugar.

```csharp
// Step 3: Examine the warning list for any font substitution entries.
foreach (WarningInfo warningInfo in document.WarningCallback.Warnings)
{
    if (warningInfo.Type == WarningType.FontSubstitution)
    {
        // The Description contains a human‑readable message, e.g.,
        // "Font 'Comic Sans MS' was not found. Substituted with 'Arial'."
        Console.WriteLine($"Substituted font: {warningInfo.Description}");
    }
}
```

**Saída esperada no console**

```
Substituted font: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
Substituted font: Font 'Times New Roman' was not found. Substituted with 'Calibri'.
```

Essa saída indica exatamente quais fontes estão ausentes na máquina que executa o código. Agora você pode decidir se instala as fontes faltantes, as incorpora ao documento ou mantém a substituição.

![Saída do console mostrando avisos de substituição de fonte Aspose](/images/aspose-font-substitution-console.png)

*Texto alternativo da imagem:* substituição de fonte Aspose – saída do console listando fontes substituídas

## Etapa 4 – Opcional: Personalizar o Comportamento de Substituição (Tratar Fontes Ausentes)

Às vezes você não quer apenas saber *que* uma substituição ocorreu — você quer controlar *como* ela acontece. O Aspose.Words permite registrar uma regra personalizada `IFontSubstitutionRule`. A seguir, um exemplo rápido que força qualquer fonte ausente a recair em `Tahoma`.

```csharp
// Optional Step 4 – Define a custom substitution rule.
class TahomaFallbackRule : IFontSubstitutionRule
{
    public FontInfo Substitute(FontInfo fontInfo, FontSubstitutionInfo substitutionInfo)
    {
        // Always return Tahoma regardless of the missing font.
        return new FontInfo("Tahoma");
    }
}

// Apply the rule to the FontSettings we created earlier.
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRules.Add(new TahomaFallbackRule());
```

**Quando usar isso?**  
Se você gera PDFs para um serviço web e sabe que todos os clientes conseguem renderizar `Tahoma`, forçar o fallback garante consistência visual sem precisar distribuir dezenas de arquivos de fonte.

## Exemplo Completo em Funcionamento (Todas as Etapas Combinadas)

Aqui está o programa inteiro que você pode colar em um novo projeto de console. Ele compila como‑está, assumindo que o pacote NuGet Aspose.Words foi instalado.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // Step 1 – Enable diagnostic collector (configure font settings)
        // -------------------------------------------------
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // -------------------------------------------------
        // Optional: Force all missing fonts to Tahoma
        // -------------------------------------------------
        loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRules.Add(
            new TahomaFallbackRule());

        // -------------------------------------------------
        // Step 2 – Load the document (load word document)
        // -------------------------------------------------
        Document doc = new Document(@"C:\Docs\MissingFont.docx", loadOptions);

        // -------------------------------------------------
        // Step 3 – List any font substitutions (detect missing fonts)
        // -------------------------------------------------
        foreach (WarningInfo warning in doc.WarningCallback.Warnings)
        {
            if (warning.Type == WarningType.FontSubstitution)
                Console.WriteLine($"Substituted font: {warning.Description}");
        }
    }
}

// -------------------------------------------------
// Optional custom rule class (handle missing fonts)
// -------------------------------------------------
class TahomaFallbackRule : IFontSubstitutionRule
{
    public FontInfo Substitute(FontInfo fontInfo, FontSubstitutionInfo substitutionInfo)
    {
        return new FontInfo("Tahoma");
    }
}
```

Execute o programa, observe o console e você verá cada evento de fonte ausente impresso. A partir daí, pode decidir se instala as fontes faltantes, as incorpora ou mantém o fallback.

## Perguntas Frequentes

**P: Isso funciona com conversão para PDF?**  
Sim. Quando você posteriormente chamar `doc.Save("output.pdf")`, quaisquer fontes que foram substituídas durante o carregamento serão as que serão incorporadas ao PDF. Portanto, capturar os avisos antecipadamente ajuda a evitar mudanças inesperadas de fonte no PDF final.

**P: E se eu tiver muitos documentos para processar?**  
Envolva a lógica de carregamento em um bloco try‑catch e reutilize uma única instância de `FontSettings` entre os documentos. Isso reduz a sobrecarga e mantém o coletor de avisos ativo para cada arquivo.

**P: Posso suprimir os avisos completamente?**  
Você pode definir `loadOptions.WarningCallback = null;` antes de carregar, mas perderá a capacidade de **detectar fontes ausentes** — o que geralmente não é o que se deseja.

## Conclusão

Cobrimos tudo o que você precisa para dominar a **aspose font substitution**: habilitar o coletor diagnóstico, carregar um arquivo Word com **definições de fonte** personalizadas, extrair a lista de fontes ausentes e até substituir a regra padrão de substituição para **tratar fontes ausentes** da sua maneira. Com apenas algumas linhas de C# você obtém total visibilidade sobre problemas de fonte que, de outra forma, ficariam ocultos por sutis alterações de layout.

Próximos passos? Experimente incorporar as fontes originais ao documento com `FontSettings.SetFontsFolder` ou explore `FontSourceBase` para carregar fontes a partir de um banco de dados. Você também pode brincar com a coleção `Document.BuiltInStyle` para ver como alterações de fonte em nível de estilo se propagam.

Tem mais perguntas sobre Aspose.Words ou gerenciamento de fontes? Deixe um comentário, explore a documentação oficial da Aspose ou inicie um novo projeto e experimente o código acima. Boa codificação, e que seus documentos sempre sejam renderizados exatamente como pretendido!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}