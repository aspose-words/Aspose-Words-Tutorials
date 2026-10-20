---
category: general
date: 2026-09-11
description: Carregue o arquivo a partir do diretório com Aspose.Words usando as opções
  de carregamento padrão e aprenda como definir a codificação do documento ou personalizar
  as opções de carregamento em C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- load file from directory
- default load options
- set document encoding
- set load options
language: pt
lastmod: 2026-09-11
og_description: Carregue o arquivo do diretório com Aspose.Words usando as opções
  de carregamento padrão, defina a codificação do documento e personalize as opções
  de carregamento para qualquer documento Word.
og_image_alt: Diagram illustrating load file from directory process with Aspose.Words
og_title: Carregar arquivo de um diretório com Aspose.Words – guia completo em C#
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Load file from directory with Aspose.Words using default load options
    and learn how to set document encoding or customize load options in C#.
  headline: How to load file from directory using Aspose.Words in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document processing
title: Como carregar arquivo de diretório usando Aspose.Words em C#
url: /pt/java/document-loading-and-saving/how-to-load-file-from-directory-using-aspose-words-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como carregar um arquivo de um diretório usando Aspose.Words em C#

Se você precisa **carregar um arquivo de um diretório** em um fluxo de trabalho de processamento de Word, o Aspose.Words torna isso simples. Este guia mostra como usar as **opções de carregamento padrão**, **definir a codificação do documento** e **definir opções de carregamento** para atender ao seu cenário específico.

O carregamento de documentos costuma ser um ponto crítico para desenvolvedores quando o arquivo fonte está em uma pasta personalizada ou usa uma codificação que não é UTF‑8. Ao final deste tutorial você será capaz de carregar qualquer arquivo `.docx` de qualquer diretório, controlar sua codificação e ajustar o comportamento de carregamento sem escrever código adicional.

## O que você vai conseguir

- Carregar um documento Word de um diretório arbitrário usando uma única linha de código.  
- Entender o que as **opções de carregamento padrão** fornecem e quando é necessário alterá‑las.  
- Aplicar **definir a codificação do documento** para interpretar corretamente conjuntos de caracteres legados como Big5.  
- Personalizar **definir opções de carregamento** para ajustar uso de memória, tratamento de senha e mais.  

### Pré‑requisitos

- .NET 6.0 ou superior (o exemplo tem como alvo o .NET 6, mas qualquer versão recente do .NET funciona).  
- Aspose.Words for .NET 23.9 ou mais recente – adicione o pacote NuGet `Aspose.Words`.  
- Familiaridade básica com C# e Visual Studio ou sua IDE preferida.

---

## Como carregar um arquivo de um diretório com Aspose.Words

O núcleo da operação é um único construtor `Document` que aceita um caminho de arquivo e uma instância opcional de `LoadOptions`. Quando você omite o `LoadOptions`, o Aspose.Words aplica automaticamente as **opções de carregamento padrão**, que são suficientes para a maioria dos documentos modernos.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;

class Program
{
    static void Main()
    {
        // Step 1: Define the absolute path to the .docx file you want to load.
        string filePath = @"C:\MyDocuments\big5.docx";

        // Step 2: Load the document using the default load options.
        Document doc = new Document(filePath, new LoadOptions());

        // Verify that the document loaded by outputting the page count.
        Console.WriteLine($"Document loaded. Page count: {doc.PageCount}");
    }
}
```

**Por que isso funciona:**  
- O construtor `Document` lê o arquivo localizado em `filePath`.  
- Passar `new LoadOptions()` indica ao Aspose.Words que use as **opções de carregamento padrão**, que detectam automaticamente o formato do arquivo, escolhem a codificação apropriada e aplicam verificações de segurança padrão.  

Executar o programa imprime a contagem de páginas, confirmando que a operação de **carregar arquivo de diretório** foi bem‑sucedida.

---

## Usando opções de carregamento padrão

Mesmo que você possa pular totalmente o argumento `LoadOptions`, criar explicitamente um objeto `LoadOptions` esclarece a intenção e prepara você para personalizações futuras.

```csharp
// Create a LoadOptions instance with the default configuration.
LoadOptions loadOptions = new LoadOptions();

// Load the document with those options.
Document doc = new Document(@"C:\MyDocuments\sample.docx", loadOptions);
```

**Pontos principais sobre as opções de carregamento padrão**

| Recurso | Comportamento padrão |
|---------|----------------------|
| **Detecção de formato** | Detecta automaticamente DOC, DOCX, ODT, RTF, HTML e muitos outros formatos. |
| **Codificação** | Detecta UTF‑8, UTF‑16 e codificações legadas comuns; recorre a UTF‑8 se necessário. |
| **Manipulação de senha** | Lança `IncorrectPasswordException` se o arquivo estiver protegido por senha. |
| **Uso de memória** | Carrega todo o documento na memória, o que é ideal para arquivos menores que 100 MB. |

Se o seu documento estiver codificado em um conjunto de caracteres legado (por exemplo, Big5) e a detecção automática falhar, você deve **definir a codificação do documento** manualmente.

---

## Definindo a codificação do documento

Quando um arquivo contém fontes ou texto codificado com uma página de código legada, você pode informar ao Aspose.Words qual codificação usar por meio da propriedade `LoadOptions.Encoding`. Esta é a forma típica de **definir a codificação do documento** para arquivos que o detector padrão não consegue resolver.

```csharp
using System.Text;

// Step 1: Create LoadOptions and specify the encoding.
LoadOptions loadOptions = new LoadOptions
{
    // Big5 is code page 950.
    Encoding = Encoding.GetEncoding(950)
};

// Step 2: Load the document from the target directory.
Document doc = new Document(@"C:\MyDocuments\big5.docx", loadOptions);

// Step 3: Verify that the special characters are preserved.
Console.WriteLine($"First paragraph text: {doc.FirstSection.Body.Paragraphs[0].GetText()}");
```

**Por que isso é necessário:**  
- Sem definir explicitamente `Encoding`, o Aspose.Words pode interpretar os bytes como UTF‑8, resultando em caracteres corrompidos.  
- Ao fornecer a página de código correta, a biblioteca lê o texto exatamente como o autor pretendia.

**Dica:** Use `Encoding.GetEncoding("big5")` ou o código numérico da página (`950`) para documentos em Chinês Tradicional (Big5).

---

## Personalizando opções de carregamento (definir opções de carregamento)

Além da codificação, `LoadOptions` expõe diversas propriedades que permitem **definir opções de carregamento** para cenários avançados:

```csharp
// Create a LoadOptions object with several custom settings.
LoadOptions loadOptions = new LoadOptions
{
    // Force the document to be treated as a DOCX file, even if the extension is wrong.
    LoadFormat = LoadFormat.Docx,

    // Limit memory usage for very large files (e.g., 200 MB+).
    LoadOptionsMemoryUsage = LoadOptionsMemoryUsage.LowMemory,

    // Provide a password if the file is encrypted.
    Password = "MySecretPassword"
};

// Load the document using the customized options.
Document doc = new Document(@"C:\MyDocuments\protected.docx", loadOptions);
```

**Explicação das propriedades selecionadas**

| Propriedade | Finalidade |
|-------------|------------|
| `LoadFormat` | Força um formato específico, ignorando a detecção automática. Útil quando extensões de arquivo são enganosas. |
| `LoadOptionsMemoryUsage` | Escolhe uma estratégia de economia de memória (`LowMemory`) para documentos muito grandes. |
| `Password` | Fornece a senha para arquivos criptografados, evitando uma exceção. |
| `ValidateDocumentStructure` | Quando `true`, o carregador valida a estrutura XML interna e lança exceção se estiver corrompida. |

Você pode combinar qualquer uma dessas com **definir a codificação do documento** para atender às pipelines de importação mais exigentes.

---

## Exemplo completo executável

A seguir, um programa autocontido que demonstra todos os conceitos em um único fluxo:

```csharp
using System;
using System.Text;
using Aspose.Words;
using Aspose.Words.Loading;

class LoadFileDemo
{
    static void Main()
    {
        // ------------------------------------------------------------------
        // 1️⃣ Define the directory and file name.
        // ------------------------------------------------------------------
        string directory = @"C:\MyDocuments";
        string fileName   = "big5.docx";               // Change as needed.
        string fullPath   = System.IO.Path.Combine(directory, fileName);

        // ------------------------------------------------------------------
        // 2️⃣ Create LoadOptions with explicit encoding (Big5) and low‑memory mode.
        // ------------------------------------------------------------------
        LoadOptions loadOptions = new LoadOptions
        {
            Encoding = Encoding.GetEncoding(950), // Big5 code page.
            LoadOptionsMemoryUsage = LoadOptionsMemoryUsage.LowMemory
        };

        // ------------------------------------------------------------------
        // 3️⃣ Load the document from the directory using the custom options.
        // ------------------------------------------------------------------
        Document doc = new Document(fullPath, loadOptions);

        // ------------------------------------------------------------------
        // 4️⃣ Verify the load succeeded.
        // ------------------------------------------------------------------
        Console.WriteLine($"Document loaded from \"{fullPath}\"");
        Console.WriteLine($"Page count: {doc.PageCount}");
        Console.WriteLine($"First paragraph: {doc.FirstSection.Body.Paragraphs[0].GetText().Trim()}");

        // ------------------------------------------------------------------
        // 5️⃣ (Optional) Save as PDF to confirm visual fidelity.
        // ------------------------------------------------------------------
        string pdfPath = System.IO.Path.ChangeExtension(fullPath, ".pdf");
        doc.Save(pdfPath);
        Console.WriteLine($"Saved PDF version to \"{pdfPath}\"");
    }
}
```

**Saída esperada no console**

```
Document loaded from "C:\MyDocuments\big5.docx"
Page count: 3
First paragraph: 這是一個測試文件
Saved PDF version to "C:\MyDocuments\big5.pdf"
```

Executar o programa demonstra como **carregar um arquivo de diretório**, **definir a codificação do documento** e **definir opções de carregamento** em um fluxo claro e único.

---

## Armadilhas comuns e como evitá‑las

| Sintoma | Causa provável | Solução |
|---------|----------------|--------|
| Caracteres chineses corrompidos | Codificação não definida ou página de código errada | **Defina a codificação do documento** para `Encoding.GetEncoding(950)` para Big5. |
| `IncorrectPasswordException` mesmo quando o arquivo não tem senha | O carregador detectou erroneamente um arquivo binário como criptografado | Defina explicitamente `LoadFormat` para o tipo correto (por exemplo, `LoadFormat.Docx`). |
| Out |  |  |

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [recover damaged docx with Aspose.Words – set recovery mode and load options](/words/english/net/programming-with-loadoptions/recover-damaged-docx-with-aspose-words-set-recovery-mode-and/)
- [How to Load RTF Documents with Configuring RTF Load Options in Aspose.Words for Java](/words/english/java/document-loading-and-saving/configuring-rtf-load-options/)
- [Master Markdown Load Options with Aspose.Words for Java](/words/english/java/document-operations/master-markdown-load-options-aspose-words-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}