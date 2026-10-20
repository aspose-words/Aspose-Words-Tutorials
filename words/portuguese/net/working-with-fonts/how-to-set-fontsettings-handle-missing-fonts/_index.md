---
category: general
date: 2026-05-29
description: Aprenda a definir FontSettings no Aspose.Words e lidar com fontes ausentes
  de forma elegante. Guia passo a passo com código completo e boas práticas.
draft: false
keywords:
- how to set fontsettings
- handle missing fonts
language: pt
og_description: Como definir FontSettings no Aspose.Words e lidar rapidamente com
  fontes ausentes. Siga este guia para uma solução completa e executável.
og_title: Como definir FontSettings – lidar com fontes ausentes
schemas:
- author: Aspose
  dateModified: '2026-05-29'
  description: Learn how to set FontSettings in Aspose.Words and handle missing fonts
    gracefully. Step-by-step guide with complete code and best practices.
  headline: How to Set FontSettings – Handle Missing Fonts
  type: TechArticle
tags:
- Aspose.Words
- FontSettings
- C#
- Document Processing
title: Como definir FontSettings – lidar com fontes ausentes
url: /pt/net/working-with-fonts/how-to-set-fontsettings-handle-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como Configurar FontSettings – Lidar com Fontes Ausentes

Já se perguntou **como configurar FontSettings** ao trabalhar com Aspose.Words e, de repente, encontrar um documento que referencia uma fonte que você não tem instalada? É um obstáculo comum, especialmente ao processar arquivos fornecidos por clientes em um servidor que possui apenas um conjunto mínimo de fontes. A boa notícia? Você pode detectar essas lacunas e **lidar com fontes ausentes** sem que seu aplicativo trave ou gere PDFs feios.

Neste tutorial, vamos percorrer um cenário real: carregar um DOCX que solicita “Calibri” enquanto seu contêiner Linux só inclui “DejaVu Sans”. Você verá exatamente como configurar FontSettings, assinar avisos de substituição e fornecer fontes de fallback para que o documento seja renderizado exatamente como o autor pretendia. Sem enrolação — apenas o código que você pode inserir no seu projeto hoje.

## Pré‑requisitos

- .NET 6.0 ou superior (a API funciona da mesma forma no .NET Framework 4.7+)
- Aspose.Words for .NET 23.10 ou mais recente (o nome do pacote NuGet é `Aspose.Words`)
- Um ambiente básico de desenvolvimento C# (Visual Studio, Rider ou VS Code)

Se você tem isso, vamos começar.

## Etapa 1: Criar FontSettings e Ouvir Eventos de Substituição

O coração da solução é o objeto `FontSettings`. Ao anexar um manipulador ao evento `FontSubstitutionWarning`, você receberá um relatório em tempo real sempre que o Aspose.Words precisar substituir uma fonte ausente.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1 – initialize FontSettings
FontSettings fontSettings = new FontSettings();

// Subscribe to the warning event so we can log substitutions
fontSettings.FontSubstitutionWarning += (sender, e) =>
{
    // e.FontFamilyName – the name requested in the source document
    // e.SubstitutedFontFamilyName – the font actually used by the engine
    Console.WriteLine(
        $"Font '{e.FontFamilyName}' substituted with '{e.SubstitutedFontFamilyName}'.");
};
```

**Por que isso importa:**  
Quando o motor não encontra *Calibri*, ele pode recair silenciosamente para *Arial*. Ao ouvir o aviso, você mantém um registro transparente — perfeito para depuração ou relatórios de conformidade.

> **Dica profissional:** Se você executar isso em um servidor de CI, direcione a saída para um arquivo de log para revisar quais fontes estavam ausentes após uma execução em lote.

## Etapa 2: Anexar FontSettings a LoadOptions

`LoadOptions` é a porta de entrada para controlar como um documento é analisado. Ao atribuir o `FontSettings` que acabamos de configurar, cada carregamento subsequente de `Document` respeitará nossa lógica de substituição.

```csharp
// Step 2 – wire FontSettings into LoadOptions
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

**O que está acontecendo nos bastidores?**  
Durante o construtor `Document`, o Aspose.Words lê o XML do DOCX, resolve as referências de fonte e — se uma fonte não for encontrada — dispara o aviso que configuramos anteriormente. Sem esse gancho, você nunca saberia que uma substituição ocorreu.

## Etapa 3: Carregar o Documento e (Opcionalmente) Definir Fontes de Fallback

Agora finalmente trazemos o arquivo para a memória. Se você já tem uma pasta de fontes de fallback (por exemplo, um diretório de fontes OpenType distribuído com seu aplicativo), informe ao `FontSettings` onde procurar. Esta etapa é opcional, mas costuma ser a maneira mais limpa de *lidar com fontes ausentes*.

```csharp
// Optional: add a folder that contains fallback fonts
fontSettings.SetFontsFolder(@"C:\MyApp\FallbackFonts", true);

// Step 3 – load the document using the prepared LoadOptions
Document doc = new Document(@"C:\Docs\DocWithMissingFonts.docx", loadOptions);
```

**Alerta de caso extremo:**  
Se o documento contiver uma fonte personalizada incorporada como um fluxo binário, o Aspose.Words a usará automaticamente — nenhuma substituição será necessária. O aviso só é disparado para *fontes do sistema* ausentes.

### Verificando o Resultado

Após o carregamento, você pode querer salvar o documento em PDF ou Word para confirmar que tudo está correto.

```csharp
// Save as PDF to see the final rendering
doc.Save(@"C:\Docs\Output.pdf", SaveFormat.Pdf);
```

Ao executar o programa, o console exibirá linhas como:

```
Font 'Calibri' substituted with 'DejaVu Sans'.
Font 'Cambria Math' substituted with 'Arial Unicode MS'.
```

Se você vir essas mensagens, **lidou com fontes ausentes** com sucesso e sabe exatamente quais substituições ocorreram.

## Etapa 4: Avançado – Regras Personalizadas de Substituição de Fonte (Opcional)

Às vezes é necessário um mapeamento determinístico, por exemplo, sempre substituir *Times New Roman* por *Liberation Serif*. Você pode conseguir isso com `FontSettings.SubstitutionTable`.

```csharp
// Define explicit substitution pairs
fontSettings.SubstitutionTable.AddSubstitutes("Times New Roman", new[] { "Liberation Serif" });
fontSettings.SubstitutionTable.AddSubstitutes("Calibri", new[] { "DejaVu Sans", "Arial" });
```

**Por que se preocupar?**  
Regras explícitas dão controle sobre a tipografia, garantindo consistência de marca nos PDFs gerados, especialmente quando você produz material de marketing.

## Armadilhas Comuns & Como Evitá‑las

| Armadilha | Sintoma | Solução |
|-----------|----------|----------|
| **Nenhum aviso de substituição** | Você pensa que as fontes estão corretas, mas o documento fica errado. | Certifique‑se de que `FontSubstitutionWarning` está anexado **antes** de carregar o documento. |
| **Pasta de fallback não escaneada** | As substituições ainda caem para as fontes padrão do sistema. | Chame `SetFontsFolder(path, true)` com o segundo argumento `true` para percorrer subpastas. |
| **Queda de desempenho em lotes grandes** | Carregar 10 mil documentos fica lento. | Cacheie uma única instância de `FontSettings` e reutilize‑a entre os carregamentos; evite recriá‑la a cada vez. |
| **Fontes incorporadas ignoradas** | Você esperava que uma fonte incorporada fosse usada, mas ocorre substituição. | Verifique se o DOCX de origem realmente incorpora a fonte (confira no Word → Arquivo → Informações → Fontes). |

## Exemplo Completo Funcional

Abaixo está o programa completo, pronto para copiar e colar. Ele demonstra tudo, desde o tratamento de eventos até a gravação do PDF final.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Set up FontSettings with a warning handler
        FontSettings fontSettings = new FontSettings();
        fontSettings.FontSubstitutionWarning += (sender, e) =>
        {
            Console.WriteLine(
                $"Font '{e.FontFamilyName}' substituted with '{e.SubstitutedFontFamilyName}'.");
        };

        // Optional: point to a folder that contains fallback fonts
        fontSettings.SetFontsFolder(@"C:\MyApp\FallbackFonts", true);

        // 2️⃣ Attach FontSettings to LoadOptions
        LoadOptions loadOptions = new LoadOptions { FontSettings = fontSettings };

        // 3️⃣ Load the document that may have missing fonts
        Document doc = new Document(@"C:\Docs\DocWithMissingFonts.docx", loadOptions);

        // 4️⃣ (Optional) Define explicit substitution rules
        fontSettings.SubstitutionTable.AddSubstitutes("Times New Roman", new[] { "Liberation Serif" });
        fontSettings.SubstitutionTable.AddSubstitutes("Calibri", new[] { "DejaVu Sans", "Arial" });

        // 5️⃣ Save the result – PDF is a common target format
        doc.Save(@"C:\Docs\Output.pdf", SaveFormat.Pdf);

        Console.WriteLine("Document processed and saved successfully.");
    }
}
```

**Saída esperada no console** (exemplo):

```
Font 'Calibri' substituted with 'DejaVu Sans'.
Font 'Cambria Math' substituted with 'Arial Unicode MS'.
Document processed and saved successfully.
```

Execute o programa, abra `Output.pdf` e você verá o texto renderizado com as fontes de fallback — sem quadrados de glifos ausentes, sem travamentos.

## Conclusão

Agora você tem um padrão sólido e pronto para produção para **como configurar FontSettings** no Aspose.Words e **lidar com fontes ausentes** de forma elegante. Ao conectar o evento `FontSubstitutionWarning`, apontar para um diretório de fontes de fallback e (se necessário) definir regras explícitas de substituição, você obtém total visibilidade e controle sobre a tipografia em pipelines automatizados de documentos.

Qual o próximo passo? Experimente adicionar uma coleção de fontes personalizada para tipografias específicas da marca, ou explore a API `FontSourceBase` para carregar fontes de um banco de dados ou armazenamento em nuvem. Os mesmos princípios se aplicam — basta conectar uma fonte diferente ao `FontSettings`.

Tem dúvidas sobre casos extremos, como lidar com scripts da direita‑para‑esquerda ou fontes de emoji? Deixe um comentário abaixo e feliz codificação!

## O Que Você Deve Aprender a Seguir?

- [How to Capture Fonts in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)
- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [How to Load DOCX and Detect Missing Fonts – Complete C# Guide](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}