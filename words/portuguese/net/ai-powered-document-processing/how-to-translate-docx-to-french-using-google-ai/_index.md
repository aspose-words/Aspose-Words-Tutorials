---
category: general
date: 2026-11-18
description: Aprenda a traduzir arquivos docx para o francês com a tradução de IA
  do Google, traduza o documento inteiro e salve o documento traduzido em apenas três
  etapas.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- translate docx to french
- google ai translation
- translate entire document
- save translated document
- how to translate docx
language: pt
lastmod: 2026-11-18
og_description: traduza docx para francês instantaneamente usando a tradução de IA
  do Google. siga este guia para traduzir todo o documento e salvar o documento traduzido
  sem esforço.
og_image_alt: Screenshot showing a DOCX file translated to French using Google AI
og_title: Traduzir docx para francês com Google AI – guia rápido
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Learn how to translate docx to French with Google AI translation, translate
    entire document, and save translated document in just three steps.
  headline: How to translate docx to French using Google AI
  type: TechArticle
- description: Learn how to translate docx to French with Google AI translation, translate
    entire document, and save translated document in just three steps.
  name: How to translate docx to French using Google AI
  steps:
  - name: 'Create a new console project:'
    text: 'Create a new console project:'
  - name: 'Add the NuGet packages that the tutorial relies on:'
    text: 'Add the NuGet packages that the tutorial relies on:'
  - name: '(Optional) If you prefer a higher‑level wrapper, you can also install `GroupDocs.Translator`:'
    text: '(Optional) If you prefer a higher‑level wrapper, you can also install `GroupDocs.Translator`:'
  type: HowTo
tags:
- C#
- Google AI
- Document translation
- Localization
title: Como traduzir docx para francês usando a IA do Google
url: /pt/net/ai-powered-document-processing/how-to-translate-docx-to-french-using-google-ai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como traduzir docx para francês usando Google AI

Se você precisa **traduzir docx para francês**, a tradução da Google AI permite traduzir todo o documento com apenas algumas linhas de código C#. Este tutorial mostra exatamente como traduzir um arquivo DOCX, traduzir o conteúdo completo do documento e salvar o documento traduzido de forma confiável.

Você aprenderá a configurar o cliente Google Cloud Translation, carregar um arquivo Word, chamar a API para traduzir cada parágrafo e, finalmente, escrever a etapa de **salvar documento traduzido**. Nenhum script externo ou cópia‑colagem manual é necessário — tudo roda dentro da sua aplicação .NET.

## O que você precisará

Antes de começar, certifique‑se de que tem:

* .NET 6.0 SDK ou superior instalado  
* Um projeto Google Cloud com a **Cloud Translation API** habilitada  
* Um arquivo de chave JSON de conta de serviço (baixado do console do Google Cloud)  
* Visual Studio 2022 (ou qualquer IDE C# de sua preferência)  

Esses pré‑requisitos garantem que as chamadas de **google ai translation** sejam bem‑sucedidas e que você possa ler/escrever arquivos DOCX com o Open XML SDK.

## Configurar o projeto e instalar os SDKs necessários

1. Crie um novo projeto de console:

   ```bash
   dotnet new console -n DocxFrenchTranslator
   cd DocxFrenchTranslator
   ```

2. Adicione os pacotes NuGet dos quais o tutorial depende:

   ```bash
   dotnet add package Google.Cloud.Translate.V3
   dotnet add package DocumentFormat.OpenXml
   ```

   *`Google.Cloud.Translate.V3`* fornece o cliente de **google ai translation**, enquanto *`DocumentFormat.OpenXml`* permite trabalhar com arquivos DOCX sem precisar do Microsoft Office instalado.

3. (Opcional) Se preferir um wrapper de nível superior, você também pode instalar `GroupDocs.Translator`:

   ```bash
   dotnet add package GroupDocs.Translator
   ```

   Os exemplos de código abaixo funcionam com qualquer uma das abordagens; a versão Open XML é mostrada completa para transparência.

## Carregar o arquivo DOCX de origem

A primeira etapa funcional é ler o documento Word que você deseja traduzir. Usando o Open XML SDK, você pode extrair o texto de cada parágrafo para uma lista.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using DocumentFormat.OpenXml.Packaging;
using DocumentFormat.OpenXml.Wordprocessing;

namespace DocxFrenchTranslator
{
    /// <summary>
    /// Reads all paragraph texts from a DOCX file.
    /// </summary>
    public static class DocxReader
    {
        public static List<string> GetParagraphs(string path)
        {
            var paragraphs = new List<string>();

            using (WordprocessingDocument wordDoc = WordprocessingDocument.Open(path, false))
            {
                Body body = wordDoc.MainDocumentPart.Document.Body;
                foreach (Paragraph para in body.Elements<Paragraph>())
                {
                    paragraphs.Add(para.InnerText);
                }
            }

            return paragraphs;
        }
    }
}
```

**Por que isso importa:** Carregar o arquivo uma única vez e manter o texto na memória permite **traduzir todo o documento** com uma única chamada de API por parágrafo, evitando I/O de arquivo repetido.

## Executar a tradução Google AI

Agora que você tem os parágrafos originais, chame a Translation API para converter cada string do inglês (ou qualquer idioma de origem) para francês. O cliente detecta automaticamente o idioma de origem se você passar `null`.

```csharp
using Google.Cloud.Translate.V3;
using System.Collections.Generic;
using System.Threading.Tasks;

namespace DocxFrenchTranslator
{
    /// <summary>
    /// Handles translation using Google Cloud Translation (v3).
    /// </summary>
    public static class Translator
    {
        private static readonly TranslationServiceClient client;

        static Translator()
        {
            // The GOOGLE_APPLICATION_CREDENTIALS environment variable should point to your JSON key.
            client = TranslationServiceClient.Create();
        }

        /// <summary>
        /// Translates a list of strings to French.
        /// </summary>
        public static async Task<List<string>> TranslateToFrenchAsync(List<string> texts)
        {
            var request = new TranslateTextRequest
            {
                Parent = $"projects/{client.ProjectId}/locations/global",
                TargetLanguageCode = "fr",
                // SourceLanguageCode can be omitted for auto‑detection.
            };

            // Add all texts to the request.
            request.Contents.AddRange(texts);

            // Execute the translation.
            TranslateTextResponse response = await client.TranslateTextAsync(request);

            var translated = new List<string>();
            foreach (Translation translation in response.Translations)
            {
                translated.Add(translation.TranslatedText);
            }

            return translated;
        }
    }
}
```

**Por que isso importa:** Usar **google ai translation** em uma solicitação em lote reduz latência e custo comparado a loops de uma chamada por parágrafo. O método também demonstra o **como traduzir docx** programaticamente.

## Criar um novo DOCX com o texto traduzido

Depois de receber as strings em francês, escreva‑as de volta em um novo arquivo DOCX. A classe auxiliar a seguir cria um novo documento a partir dos parágrafos traduzidos.

```csharp
using DocumentFormat.OpenXml.Packaging;
using DocumentFormat.OpenXml.Wordprocessing;

namespace DocxFrenchTranslator
{
    /// <summary>
    /// Writes a list of paragraphs to a new DOCX file.
    /// </summary>
    public static class DocxWriter
    {
        public static void Write(string outputPath, List<string> frenchParagraphs)
        {
            // Ensure the directory exists.
            Directory.CreateDirectory(Path.GetDirectoryName(outputPath)!);

            // Create a new document.
            using (WordprocessingDocument wordDoc = WordprocessingDocument.Create(outputPath, DocumentFormat.OpenXml.WordprocessingDocumentType.Document))
            {
                MainDocumentPart mainPart = wordDoc.AddMainDocumentPart();
                mainPart.Document = new Document();
                Body body = mainPart.Document.AppendChild(new Body());

                foreach (string paraText in frenchParagraphs)
                {
                    Paragraph para = new Paragraph(new Run(new Text(paraText)));
                    body.AppendChild(para);
                }

                mainPart.Document.Save();
            }
        }
    }
}
```

## Montar tudo – o programa completo

Abaixo está a aplicação console completa e executável que reúne os trechos anteriores. Ela demonstra **translate docx to french**, executa **google ai translation** e, finalmente, **save translated document**.

```csharp
using System;
using System.IO;
using System.Threading.Tasks;

namespace DocxFrenchTranslator
{
    class Program
    {
        static async Task Main(string[] args)
        {
            // ------------------------------------------------------------------
            // 1️⃣ Load the source document
            // ------------------------------------------------------------------
            string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
            if (!File.Exists(inputPath))
            {
                Console.WriteLine($"Input file not found: {inputPath}");
                return;
            }

            var originalParagraphs = DocxReader.GetParagraphs(inputPath);
            Console.WriteLine($"Loaded {originalParagraphs.Count} paragraphs from input.docx.");

            // ------------------------------------------------------------------
            // 2️⃣ Translate the entire document to French using Google AI
            // ------------------------------------------------------------------
            var frenchParagraphs = await Translator.TranslateToFrenchAsync(originalParagraphs);
            Console.WriteLine("Translation completed – document is now in French.");

            // ------------------------------------------------------------------
            // 3️⃣ Save the translated document
            // ------------------------------------------------------------------
            string outputPath = Path.Combine(Environment.CurrentDirectory, "output_fr.docx");
            DocxWriter.Write(outputPath, frenchParagraphs);
            Console.WriteLine($"Saved translated document to: {outputPath}");
        }
    }
}
```

### Saída esperada

Ao executar o programa (`dotnet run`), o console exibirá algo semelhante a:

```
Loaded 12 paragraphs from input.docx.
Translation completed – document is now in French.
Saved translated document to: C:\Path\To\Your\Project\output_fr.docx
```

Abra `output_fr.docx` com Word, LibreOffice ou qualquer visualizador, e você verá o conteúdo original em inglês substituído pelas traduções em francês.

## Traduzir docx para francês – visão geral passo a passo

### 1. Configurar credenciais do Google com segurança

* Coloque o arquivo JSON da conta de serviço em um local seguro, por exemplo

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que expandem as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [How to save translated Word document in C# with Google AI](/words/english/net/ai-powered-document-processing/how-to-save-translated-word-document-in-c-with-google-ai/)
- [How to translate DOCX to French and automate document translation](/words/english/net/ai-powered-document-processing/how-to-translate-docx-to-french-and-automate-document-transl/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}