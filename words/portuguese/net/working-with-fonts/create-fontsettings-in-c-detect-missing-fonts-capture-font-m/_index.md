---
category: general
date: 2026-03-01
description: Crie FontSettings em C# para detectar fontes ausentes, capturar mensagens
  de fontes e tratar fontes ausentes com Aspose.Words. Guia passo a passo para desenvolvedores.
draft: false
keywords:
- create fontsettings
- detect missing fonts
- capture font messages
- handle missing fonts
- Aspose.Words font handling
- C# document processing
language: pt
og_description: Criar FontSettings em C# para detectar fontes ausentes, capturar mensagens
  de fonte e lidar com fontes ausentes usando Aspose.Words. Tutorial completo com
  código.
og_title: Criar FontSettings em C# – Detectar fontes ausentes e capturar mensagens
  de fontes
tags:
- Aspose.Words
- C#
- Font Management
title: Criar FontSettings em C# – Detectar fontes ausentes e capturar mensagens de
  fonte
url: /pt/net/working-with-fonts/create-fontsettings-in-c-detect-missing-fonts-capture-font-m/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar FontSettings em C# – Detectar Fontes Ausentes e Capturar Mensagens de Fonte

Já precisou **criar FontSettings** em um projeto .NET, mas não sabia como identificar fontes que não estão instaladas na máquina de destino? Você não está sozinho. Em muitas aplicações reais—pense em geradores automáticos de relatórios ou conversores de documentos—fontes ausentes podem quebrar o layout silenciosamente, e você só percebe quando o PDF fica estranho.  

E se você pudesse **detectar fontes ausentes**, **capturar mensagens de fonte** e **tratar fontes ausentes** antes que estraguem sua saída? A boa notícia é que o Aspose.Words torna isso muito simples. Neste tutorial vamos percorrer todo o processo, desde a configuração do objeto `FontSettings` até a criação de um callback de aviso que informa exatamente quais glifos foram substituídos.

> **TL;DR:** Ao final, você terá um aplicativo console C# pronto‑para‑executar que registra cada substituição de fonte, permitindo decidir se incorpora um substituto ou alerta o usuário.

---

## Pré‑requisitos

- .NET 6 SDK (ou qualquer versão recente do .NET)  
- Visual Studio 2022 ou VS Code com extensões C#  
- Uma licença do Aspose.Words for .NET (a versão de avaliação gratuita funciona para esta demonstração)  
- Um DOCX de exemplo que referencia uma fonte que você não tem instalada (por exemplo, *Comic Sans MS* em um Linux)  

Nenhum pacote NuGet especial além do `Aspose.Words` é necessário.

---

## Etapa 1 – Instalar Aspose.Words e Configurar o Projeto

Primeiro, crie um novo projeto console e adicione a biblioteca Aspose.Words ao projeto.

```bash
dotnet new console -n FontSettingsDemo
cd FontSettingsDemo
dotnet add package Aspose.Words
```

> **Dica:** Se já possui uma solução, basta adicionar o pacote via a UI do NuGet Package Manager—facilita o controle de versões.

---

## Etapa 2 – Criar FontSettings (Palavra‑chave Principal Aparece Aqui)

A etapa **criar FontSettings** é a base de qualquer fluxo de trabalho relacionado a fontes. `FontSettings` informa ao Aspose.Words onde procurar fontes, se deve usar pastas do sistema e como fazer fallback quando algo está ausente.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// 1️⃣ Create a FontSettings object – this is where we’ll configure search paths.
FontSettings fontSettings = new FontSettings();

// Optional: add a custom folder that contains fallback fonts.
fontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);
```

Por que isso é importante? Sem um `FontSettings` configurado corretamente, o motor substitui silenciosamente glifos ausentes pela fonte padrão do sistema, e você nunca verá um aviso.

---

## Etapa 3 – Configurar LoadOptions com o FontSettings

`LoadOptions` permite passar o `FontSettings` para o carregador de documentos. Essa é a ponte que permite ao motor **detectar fontes ausentes** durante a fase de construção do `Document`.

```csharp
// 2️⃣ Configure LoadOptions to use the FontSettings we just created.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

Agora, toda vez que você carregar um DOCX com `loadOptions`, o Aspose.Words consultará o `FontSettings` que configuramos anteriormente.

---

## Etapa 4 – Anexar um Callback de Aviso para **Capturar Mensagens de Fonte**

O Aspose.Words emite avisos para diversas condições—substituição de fonte é uma das mais comuns. Ao fornecer uma implementação de `IWarningCallback`, você pode **capturar mensagens de fonte** em tempo real.

```csharp
// 3️⃣ Attach a warning handler that will print font‑substitution warnings.
loadOptions.WarningCallback = new FontSubstitutionWarningHandler();
```

### Classe de Manipulador de Avisos

```csharp
/// <summary>
/// Handles font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Source == WarningSource.FontSubstitution)
        {
            Console.WriteLine($"[FontSubstitution] {info.Description}");
        }
    }
}
```

O campo `info.Description` contém uma mensagem legível, como *“Font 'Comic Sans MS' was not found. Substituted with 'Arial'.”* Essa é exatamente a saída que você precisa para **tratar fontes ausentes** de forma elegante.

---

## Etapa 5 – Carregar o Documento e Deixar o Callback Fazer Seu Trabalho

Com tudo configurado, o carregamento do documento torna‑se simples. Se o arquivo fonte referencia uma fonte ausente do sistema, nosso manipulador de avisos será acionado.

```csharp
// 4️⃣ Load a document that may contain unknown fonts.
Document doc = new Document(@"C:\Docs\UnknownFont.docx", loadOptions);

// Optional: you can now save the document to PDF or any other format.
doc.Save(@"C:\Docs\Result.pdf");
```

Ao executar o programa, você verá uma saída no console semelhante a:

```
[FontSubstitution] Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
[FontSubstitution] Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
```

Essa saída corresponde à parte **capturar mensagens de fonte** do nosso fluxo. Você pode estender o manipulador para registrar em um arquivo, enviar telemetria ou até abortar a conversão se fontes críticas estiverem ausentes.

---

## Etapa 6 – Exemplo Completo (Todas as Peças Juntas)

Abaixo está um programa completo, pronto para copiar e colar. Cole-o em `Program.cs`, ajuste os caminhos dos arquivos e execute `dotnet run`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSettingsDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // ----- Step 1: Create FontSettings -----
            FontSettings fontSettings = new FontSettings();
            // Add any custom folder with fallback fonts (optional)
            fontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);

            // ----- Step 2: Configure LoadOptions -----
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new FontSubstitutionWarningHandler()
            };

            // ----- Step 3: Load the document -----
            string inputPath = @"C:\Docs\UnknownFont.docx";
            Document doc = new Document(inputPath, loadOptions);

            // ----- Step 4: Save the result (optional) -----
            string outputPath = @"C:\Docs\Result.pdf";
            doc.Save(outputPath);

            Console.WriteLine("Document processed. Check console for any font substitution warnings.");
        }
    }

    // ----- Warning handler that captures font messages -----
    class FontSubstitutionWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Source == WarningSource.FontSubstitution)
            {
                Console.WriteLine($"[FontSubstitution] {info.Description}");
            }
        }
    }
}
```

### Saída Esperada

Executar o programa em uma máquina que não possui *Comic Sans MS* imprimirá algo como:

```
[FontSubstitution] Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Document processed. Check console for any font substitution warnings.
```

Você também obterá `Result.pdf` que usa as fontes substituídas, garantindo que a conversão nunca falhe.

---

## Perguntas Frequentes & Casos de Borda

| Pergunta | Resposta |
|----------|----------|
| **E se eu quiser que a conversão falhe em vez de substituir?** | Dentro de `FontSubstitutionWarningHandler`, lance uma exceção quando `info.Description` contiver o nome de uma fonte crítica. |
| **Posso incorporar automaticamente uma fonte de substituição?** | Sim. Após detectar uma fonte ausente, você pode carregar um `FontInfo` de um caminho conhecido e adicioná‑lo ao `fontSettings` via `fontSettings.SetFontsFolder`. |
| **Isso funciona em Linux/macOS?** | Absolutamente. `FontSettings` funciona em todas as plataformas; basta garantir que a pasta de fallback contenha os arquivos `.ttf` ou `.otf` apropriados. |
| **O callback de aviso é thread‑safe?** | O callback roda na mesma thread que carrega o documento, portanto não é necessário sincronização extra para logs no console. Em cenários multithread, proteja recursos compartilhados. |
| **Como registro avisos em um arquivo?** | Substitua `Console.WriteLine` por `File.AppendAllText("font_warnings.log", ...)` ou use qualquer framework de logging (Serilog, NLog). |

---

## Dicas Profissionais para Manipulação de Fontes em Produção

1. **Cache de Busca de Fontes** – Reutilizar a mesma instância de `FontSettings` em múltiplos carregamentos evita varreduras repetidas no sistema de arquivos.  
2. **Lista Branca de Fontes Críticas** – Se sua marca exige uma fonte específica, verifique sua presença logo no início e abortar com uma mensagem de erro clara.  
3. **Use `SetFontFolder` Recursivamente** – Definir `recursive: true` garante que subpastas sejam escaneadas, útil quando você distribui uma coleção completa de fontes.  
4. **Combine com `FontSubstitutionSettings`** – Você pode refinar regras de substituição (por exemplo, preferir fontes com o mesmo nome de família).  

---

## Conclusão

Acabamos de **criar FontSettings**, configurar `LoadOptions` para **detectar fontes ausentes**, anexar um callback que **captura mensagens de fonte** e demonstrar como **tratar fontes ausentes** de maneira limpa e pronta para produção. Todo o fluxo cabe em poucas dezenas de linhas de C#, mas oferece total visibilidade sobre o cenário de fontes de qualquer DOCX que você processe.

Próximos passos sugeridos:

- **Incorporar fontes de fallback** diretamente no PDF de saída (`PdfSaveOptions.FontEmbeddingMode`).  
- **Substituir fontes programaticamente** com base em regras de branding corporativo.  
- **Integrar a um pipeline CI** para sinalizar automaticamente documentos que utilizam fontes não autorizadas.

Experimente, ajuste o manipulador de avisos conforme suas necessidades e deixe seus pipelines de documentos rodarem com confiança—chega de glitches de layout misteriosos causados por trocas invisíveis de fonte.

Bom código! 🚀

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}