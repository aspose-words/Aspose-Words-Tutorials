---
category: general
date: 2026-06-02
description: crie documento compatível com PDF/UA-2 usando Aspose.Words em C#. Tutorial
  passo a passo cobrindo conformidade PDF/UA-2, PdfSaveOptions e acessibilidade.
draft: false
keywords:
- create pdf/ua-2 compliant document
- Aspose.Words PDF/UA
- C# document conversion
- PDF accessibility
- PdfSaveOptions
language: pt
og_description: Aprenda como criar documentos compatíveis com PDF/UA‑2 usando Aspose.Words
  para .NET. Código completo, dicas de conformidade e acessibilidade em PDF explicados.
og_title: Criar documento compatível com pdf/ua-2 – Guia completo de C#
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: create pdf/ua-2 compliant document with Aspose.Words in C#. Step‑by‑step
    tutorial covering PDF/UA‑2 compliance, PdfSaveOptions and accessibility.
  headline: Create pdf/ua-2 compliant document – Complete C# Guide
  type: TechArticle
- description: create pdf/ua-2 compliant document with Aspose.Words in C#. Step‑by‑step
    tutorial covering PDF/UA‑2 compliance, PdfSaveOptions and accessibility.
  name: Create pdf/ua-2 compliant document – Complete C# Guide
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code works with .NET Core, .NET Framework 4.7+,
      and .NET 5+). - A licensed copy of **Aspose.Words for .NET** (the free trial
      works for testing). - Basic familiarity with C# and Visual Studio (or your favourite
      IDE).'
  - name: Why These Settings Matter
    text: '- **Compliance = PdfUa2** – This flag adds the *PDF/UA* metadata and logical
      structure tree. - **EmbedFullFonts** – PDF/UA requires that all glyphs used
      in the document are embedded, otherwise a screen reader might miss characters.
      - **ExportDocumentStructure** – Tags the PDF so assistive technologi'
  - name: Quick Validation with the PDF/UA Validator
    text: 1. Download the free **PDF/UA‑2 validator** from the PDF Association (search
      “PDF/UA validator”). 2. Drag `Doc_UA.pdf` onto the validator window. 3. The
      tool will report “No errors” if the document meets the standard.
  - name: Custom Fonts
    text: If your source uses a font that isn’t installed on the server, enable `FontEmbeddingMode
      = FontEmbeddingMode.Always` to force embedding.
  - name: Complex Tables
    text: PDF/UA‑2 requires that tables have proper structure. Ensure every table
      in the Word file has header rows defined (`Table Tools → Layout → Repeat Header
      Rows`). Aspose.Words respects this setting automatically.
  - name: Images Without Alt Text
    text: 'Screen readers rely on alternative text. If an image lacks alt text, Aspose.Words
      will insert an empty description, which may cause a compliance warning. Add
      alt text in Word (`Picture Tools → Alt Text`) or programmatically:'
  type: HowTo
tags:
- PDF
- C#
- Aspose.Words
- Accessibility
title: Criar documento compatível com pdf/ua-2 – Guia completo de C#
url: /pt/net/programming-with-pdfsaveoptions/create-pdf-ua-2-compliant-document-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar documento compatível com pdf/ua-2 – Guia Completo em C#

Precisa **criar documento compatível com pdf/ua-2** mas não sabe por onde começar? Neste tutorial vamos guiá‑lo passo a passo sobre como criar um documento compatível com pdf/ua-2 usando Aspose.Words para .NET, garantindo acessibilidade em PDF e conformidade total com PDF/UA‑2.  

Se você já lidou com requisitos de acessibilidade para PDFs, vai apreciar a simplicidade da abordagem que vamos apresentar. Ao final, você terá um trecho de código C# pronto para uso, entenderá por que cada configuração é importante e saberá como verificar se o resultado realmente atende ao padrão PDF/UA‑2.

## O que você aprenderá

- Como configurar o suporte **Aspose.Words PDF/UA** em um projeto C#.
- O papel exato do **PdfSaveOptions** ao direcionar para PDF/UA‑2.
- Dicas para lidar com casos extremos como fontes personalizadas e tabelas complexas.
- Um método rápido para validar o arquivo gerado com validadores gratuitos de PDF/UA.

### Pré‑requisitos

- .NET 6.0 ou posterior (o código funciona com .NET Core, .NET Framework 4.7+ e .NET 5+).  
- Uma cópia licenciada do **Aspose.Words for .NET** (a versão de avaliação gratuita serve para testes).  
- Familiaridade básica com C# e Visual Studio (ou sua IDE favorita).  

Se você marcou esses itens, vamos mergulhar — sem necessidade de ferramentas extras.

![exemplo de documento compatível com pdf/ua-2](images/pdf-ua2-example.png "exemplo de documento compatível com pdf/ua-2")

## Etapa 1: Instalar Aspose.Words e Adicionar Referências  

Primeiro de tudo, você precisa da biblioteca Aspose.Words. Abra um terminal na pasta do seu projeto e execute:

```bash
dotnet add package Aspose.Words
```

Alternativamente, use o NuGet Package Manager no Visual Studio. Isso adiciona os recursos **Aspose.Words PDF/UA**, incluindo a classe `PdfSaveOptions` que usaremos mais adiante.  

> **Dica profissional:** Se você planeja distribuir o recurso de geração de PDF para um cliente, adicione o arquivo de licença (`Aspose.Words.lic`) ao seu projeto e chame `License license = new License(); license.SetLicense("Aspose.Words.lic");` logo no início de `Main()` — isso remove a marca d'água de avaliação.

## Etapa 2: Carregar o Documento Fonte  

Nosso objetivo é transformar um arquivo Word (`.docx`) em um documento compatível com PDF/UA‑2. A origem pode ser qualquer documento Word, mas para uma auditoria de acessibilidade limpa, comece com um arquivo simples que inclua títulos, texto alternativo para imagens e estruturas de tabela adequadas.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

class PdfUaGenerator
{
    static void Main()
    {
        // Load the source .docx file
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
        
        // Proceed to configure PDF/UA‑2 options
        SaveAsPdfUa2(doc);
    }
}
```

Por que carregar o documento primeiro? O Aspose.Words analisa o arquivo Word em um modelo de objetos, permitindo inspecionar ou modificar o conteúdo antes da conversão — útil se for necessário inserir tags de acessibilidade posteriormente.

## Etapa 3: Configurar PdfSaveOptions para PDF/UA‑2  

A classe **PdfSaveOptions** é onde a mágica acontece. Definir `Compliance = PdfCompliance.PdfUa2` indica ao Aspose.Words que ele deve incorporar as tags necessárias, elementos de estrutura lógica e definir a versão correta do PDF.  

```csharp
static void SaveAsPdfUa2(Document doc)
{
    // Create a new PdfSaveOptions instance
    PdfSaveOptions pdfOptions = new PdfSaveOptions
    {
        // Enforce PDF/UA‑2 compliance
        Compliance = PdfCompliance.PdfUa2,

        // Optional but recommended: embed all fonts to avoid substitution issues
        EmbedFullFonts = true,

        // Ensure the document is tagged (required for PDF/UA)
        ExportDocumentStructure = true,

        // Preserve hyperlinks and bookmarks for better navigation
        ExportHyperlinks = true,
        ExportBookmarks = true
    };

    // Save the PDF/UA‑2 file
    doc.Save(@"YOUR_DIRECTORY\Doc_UA.pdf", pdfOptions);
}
```

### Por que essas configurações são importantes  

- **Compliance = PdfUa2** – Esta flag adiciona os metadados *PDF/UA* e a árvore de estrutura lógica.  
- **EmbedFullFonts** – O PDF/UA exige que todos os glifos usados no documento sejam incorporados, caso contrário um leitor de tela pode perder caracteres.  
- **ExportDocumentStructure** – Marca o PDF para que tecnologias assistivas possam interpretar corretamente títulos, parágrafos e tabelas.  
- **ExportHyperlinks / ExportBookmarks** – Melhora a navegação para usuários que dependem de atalhos de teclado ou de leitores de tela.  

## Etapa 4: Executar o Código e Verificar o Resultado  

Compile e execute o projeto. Se tudo estiver configurado corretamente, você encontrará `Doc_UA.pdf` na pasta de destino. Abra-o no Adobe Acrobat Reader e verifique **File → Properties → Description** — você deverá ver *PDF/UA‑2* listado no campo “PDF/A”.  

### Validação rápida com o Validador PDF/UA  

1. Baixe o **validador PDF/UA‑2** gratuito da PDF Association (pesquise “PDF/UA validator”).  
2. Arraste `Doc_UA.pdf` para a janela do validador.  
3. A ferramenta exibirá “No errors” se o documento atender ao padrão.  

Se você encontrar avisos sobre tags de idioma ausentes, adicione um atributo de idioma ao documento Word (`Review → Language → Set Proofing Language`) antes da conversão.

## Etapa 5: Tratar Casos Limítrofes Comuns  

### Fontes Personalizadas  

Se sua origem usar uma fonte que não está instalada no servidor, habilite `FontEmbeddingMode = FontEmbeddingMode.Always` para forçar a incorporação.  

```csharp
pdfOptions.FontEmbeddingMode = FontEmbeddingMode.Always;
```

### Tabelas Complexas  

O PDF/UA‑2 exige que as tabelas tenham estrutura adequada. Certifique‑se de que cada tabela no arquivo Word tenha linhas de cabeçalho definidas (`Table Tools → Layout → Repeat Header Rows`). O Aspose.Words respeita essa configuração automaticamente.

### Imagens sem Texto Alternativo  

Leitores de tela dependem do texto alternativo. Se uma imagem não possuir texto alternativo, o Aspose.Words inserirá uma descrição vazia, o que pode gerar um aviso de conformidade. Adicione texto alternativo no Word (`Picture Tools → Alt Text`) ou programaticamente:

```csharp
foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
{
    if (shape.HasImage && string.IsNullOrEmpty(shape.AlternativeText))
    {
        shape.AlternativeText = "Descriptive text for accessibility";
    }
}
```

## Etapa 6: Melhores Práticas para Projetos PDF/UA‑2 Contínuos  

- **Automatizar a validação**: Integre o validador PDF/UA ao seu pipeline de CI para que cada PDF gerado seja verificado antes do lançamento.  
- **Manter as bibliotecas atualizadas**: O Aspose.Words lança atualizações frequentes que aprimoram o suporte a PDF/UA — atualize pelo menos uma vez por ano.  
- **Documentar seu fluxo de trabalho**: Mantenha uma lista de verificação (incorporação de fontes, texto alternativo, cabeçalhos de tabela) para garantir que membros não técnicos da equipe possam manter a conformidade.  

---

## Conclusão  

Agora você sabe exatamente como **criar documento compatível com pdf/ua-2** usando C# e Aspose.Words. Ao configurar `PdfSaveOptions` com as flags corretas, incorporar fontes e garantir que seu arquivo Word de origem siga as melhores práticas de acessibilidade, você pode gerar PDFs que passam na validação oficial PDF/UA‑2 sem problemas.  

Pronto para o próximo desafio? Experimente adicionar recursos de **acessibilidade em PDF** como ordem de leitura lógica para layouts de múltiplas colunas, ou explore a **conversão de documentos C#** para outros formatos como EPUB, preservando os mesmos metadados de acessibilidade.  

Se encontrar algum problema, deixe um comentário abaixo — feliz codificação e aproveite a criação de PDFs inclusivos!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos estreitamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Criar PDF acessível – Guia passo a passo para conformidade PDF/UA](/words/english/net/programming-with-pdfsaveoptions/create-accessible-pdf-step-by-step-guide-for-pdf-ua-complian/)
- [Criar PDF acessível em C# – Tutorial de acessibilidade em PDF](/words/english/net/programming-with-pdfsaveoptions/create-accessible-pdf-in-c-pdf-accessibility-tutorial/)
- [Converter Word para PDF em C# usando Aspose.Words – Guia](/words/english/net/basic-conversions/convert-word-to-pdf-in-c-using-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}