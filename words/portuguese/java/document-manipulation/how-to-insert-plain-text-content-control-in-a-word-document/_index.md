---
category: general
date: 2026-10-26
description: Aprenda a inserir controle de conteúdo de texto simples usando Aspose.Words
  em C#. Guia passo a passo que cobre StructuredDocumentTag, títulos e IDs de tags.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert plain text content control
- structured document tag
- Aspose.Words DocumentBuilder
- C# content control
- SDT appearance
language: pt
lastmod: 2026-10-26
og_description: Insira um controle de conteúdo de texto simples usando Aspose.Words
  em C#. Siga este guia para adicionar títulos, IDs de tags e personalizar a aparência.
og_image_alt: Screenshot of a Word document showing an inserted plain text content
  control
og_title: Inserir controle de conteúdo de texto simples no Word com C# – guia completo
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn to insert plain text content control using Aspose.Words in C#.
    Step‑by‑step guide covering StructuredDocumentTag, titles, and tag IDs.
  headline: How to insert plain text content control in a Word document with C#
  type: TechArticle
- description: Learn to insert plain text content control using Aspose.Words in C#.
    Step‑by‑step guide covering StructuredDocumentTag, titles, and tag IDs.
  name: How to insert plain text content control in a Word document with C#
  steps:
  - name: Initialize the document and builder
    text: '```csharp using System; using Aspose.Words; using Aspose.Words.Markup;'
  - name: Insert the plain‑text content control (SDT)
    text: '```csharp // Insert a plain‑text Structured Document Tag (SDT) with the
      default appearance. StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
      SdtType.PlainText, // The control type – plain text. SdtAppearance.Default);
      // Visual style; Default shows a light gray shading. ```'
  - name: Set a title and a tag identifier
    text: '```csharp // Give the SDT a friendly title that appears in the Content
      Controls pane. sdt.Title = "MyTag";'
  - name: Variations you might need
    text: '| Scenario | Code change | |----------|-------------| | **No visual shading**
      (border‑less) | Use `SdtAppearance.Hidden` instead of `Default`. | | **Read‑only
      field** | After insertion, set `sdt.LockContentControl = true`. | | **Pre‑populate
      with data** | Set `sdt.Text = "John Doe";` after creating '
  - name: What’s next?
    text: '- Explore other SDT types such as `RichText` or `ComboBox` for dropdowns.
      - Combine multiple content controls inside tables or repeat them using `RepeatingSection`.
      - Use `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` to read or modify
      control values programmatically.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Como inserir controle de conteúdo de texto simples em um documento Word com
  C#
url: /pt/java/document-manipulation/how-to-insert-plain-text-content-control-in-a-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Inserir controle de conteúdo de texto simples em um documento Word com C#

Se você precisa **inserir um controle de conteúdo de texto simples** em um arquivo Word, este tutorial mostra exatamente como fazer isso usando Aspose.Words para .NET. Seja você quem está construindo um serviço de geração de documentos ou automatizando a criação de formulários, os passos abaixo permitem adicionar uma região reutilizável e editável que os usuários finais podem preencher.

Você aprenderá como criar um `Document`, usar `DocumentBuilder` para colocar um Structured Document Tag (SDT) de texto simples, definir um título amigável e atribuir um identificador de tag exclusivo. O guia também explica variações comuns — como mudar a aparência ou aninhar controles — para que você possa adaptar a solução a qualquer projeto.

## Pré‑requisitos

Antes de começar, certifique‑se de que você tem:

- .NET 6.0 ou posterior (o código também funciona com .NET Framework 4.6+)
- Uma licença válida do Aspose.Words para .NET (ou uma chave de avaliação gratuita)
- Visual Studio 2022 ou qualquer IDE compatível com C#
- Familiaridade básica com a sintaxe C#

> **Dica profissional:** Se você estiver usando a avaliação gratuita, lembre‑se de que o documento de saída conterá uma marca d’água. Uma versão licenciada a remove automaticamente.

## Como inserir controle de conteúdo de texto simples usando Aspose.Words

O núcleo da solução é um processo de três etapas:

1. **Criar um `Document` e um `DocumentBuilder`.**  
2. **Inserir um Structured Document Tag (SDT) de texto simples com aparência padrão.**  
3. **Atribuir um título e um identificador de tag ao SDT.**  

Cada etapa é explicada abaixo, com código completo e executável.

### Etapa 1: Inicializar o documento e o builder

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Create a new empty document.
        Document doc = new Document();

        // DocumentBuilder lets you insert content into the document.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` representa todo o arquivo Word, enquanto `DocumentBuilder` fornece métodos como `InsertParagraph`, `InsertImage` e, crucialmente para este tutorial, `InsertStructuredDocumentTag`. Inicializá‑los primeiro fornece uma tela onde você pode colocar o **controle de conteúdo de texto simples**.

### Etapa 2: Inserir o controle de conteúdo de texto simples (SDT)

```csharp
        // Insert a plain‑text Structured Document Tag (SDT) with the default appearance.
        StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
            SdtType.PlainText,          // The control type – plain text.
            SdtAppearance.Default);    // Visual style; Default shows a light gray shading.
```

`SdtType.PlainText` indica ao Aspose.Words que crie um **controle de conteúdo de texto simples**, que se comporta como uma caixa de texto simples que os usuários podem editar. O `SdtAppearance.Default` renderiza o controle com um fundo sutil, tornando óbvio no documento que a região é editável.

> **Por que usar `SdtAppearance.Default`?**  
> A aparência padrão é o estilo mais universalmente compatível entre versões do Word. Se você precisar de um visual sem bordas, pode mudar para `SdtAppearance.Hidden` mais tarde.

### Etapa 3: Definir um título e um identificador de tag

```csharp
        // Give the SDT a friendly title that appears in the Content Controls pane.
        sdt.Title = "MyTag";

        // Assign a unique tag identifier; this is useful for programmatic access later.
        sdt.Tag = "TagId";

        // (Optional) Add placeholder text inside the control.
        sdt.PlaceholderName = "Enter your text here";

        // Save the document to verify the result.
        doc.Save("output.docx");
    }
}
```

- **Title** (`sdt.Title`) aparece no painel *Content Controls* do Word, ajudando os usuários finais a entender o propósito do campo.  
- **Tag** (`sdt.Tag`) é um identificador voltado ao desenvolvedor que você pode consultar mais tarde via `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`.  
- **PlaceholderName** fornece um texto de orientação em cinza, melhorando a experiência do usuário.

O trecho de código completo acima forma um programa autocontido que você pode compilar e executar. Após a execução, `output.docx` conterá um único controle de conteúdo de texto simples com o título *MyTag* e a tag *TagId*.

![Diagrama mostrando inserção de controle de conteúdo de texto simples em um documento Word](image.png){alt="inserir controle de conteúdo de texto simples"}

## Entendendo StructuredDocumentTag (SDT) e suas propriedades

Um **Structured Document Tag** (SDT) é o modelo de objeto subjacente aos controles de conteúdo do Word. As propriedades mais relevantes para inserir um controle de texto simples são:

| Propriedade | Finalidade | Valores típicos |
|-------------|------------|-----------------|
| `SdtType` | Determina o tipo de controle (texto simples, texto rico, imagem, etc.) | `PlainText`, `RichText`, `ComboBox`, `DatePicker` |
| `SdtAppearance` | Estilo visual do controle | `Default`, `Hidden`, `BoundingBox`, `Tags` |
| `Title` | Nome legível exibido no painel *Content Controls* | Qualquer string curta |
| `Tag` | Identificador legível por máquina usado no código | String alfanumérica |
| `PlaceholderName` | Texto exibido quando o controle está vazio | Texto de dica personalizado |

Quando você define `SdtType.PlainText`, o Word restringe o conteúdo a caracteres simples, impedindo formatação rica. Isso torna o controle ideal para campos de formulário simples, como *Nome*, *E‑mail* ou *Número de Telefone*.

### Variações que você pode precisar

| Cenário | Alteração no código |
|---------|---------------------|
| **Sem sombreamento visual** (sem bordas) | Use `SdtAppearance.Hidden` em vez de `Default`. |
| **Campo somente‑leitura** | Após a inserção, defina `sdt.LockContentControl = true`. |
| **Pré‑preencher com dados** | Defina `sdt.Text = "John Doe";` depois de criar a tag. |
| **Múltiplos controles em uma tabela** | Insira o SDT dentro de uma célula de tabela usando `builder.InsertCell();` antes da chamada `InsertStructuredDocumentTag`. |

## Armadilhas comuns e como evitá‑las

1. **Esquecer de definir um título** – O Word ainda criará o controle, mas os usuários não verão uma descrição significativa no painel *Content Controls*. Sempre atribua `sdt.Title`.  
2. **Usar o `SdtType` errado** – Se precisar de texto simples e escolher acidentalmente `RichText`, o controle permitirá formatação, o que pode quebrar o processamento posterior. Verifique o valor do enum.  
3. **Salvar em uma pasta somente‑leitura** – A chamada `doc.Save` lançará uma `UnauthorizedAccessException`. Garanta que o diretório de destino seja gravável ou use `Path.GetTempPath()` para testes.  
4. **Licença não aplicada** – Sem uma licença válida, o documento de saída contém uma marca d’água de avaliação. Aplique a licença no início do programa:  

```csharp
License lic = new License();
lic.SetLicense("Aspose.Words.lic");
```

## Exemplo completo e executável

Abaixo está o programa inteiro, pronto para copiar‑colar em um novo projeto de console.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace InsertPlainTextContentControl
{
    class Program
    {
        static void Main()
        {
            // Apply license (optional for evaluation)
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            // 1️⃣ Create a new document and a builder to edit it
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a plain‑text Structured Document Tag (SDT) with default appearance
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                SdtType.PlainText,          // Plain text control
                SdtAppearance.Default);    // Light gray shading

            // 3️⃣ Assign a title and a tag identifier to the SDT
            sdt.Title = "MyTag";          // Human‑readable title
            sdt.Tag = "TagId";            // Unique machine identifier
            sdt.PlaceholderName = "Enter your text here";

            // (Optional) Add some introductory text before the control
            builder.MoveToDocumentStart();
            builder.Writeln("Please fill in the following field:");

            // 4️⃣ Save the document
            string outputPath = "output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Saída esperada:** Ao abrir `output.docx` no Microsoft Word, você verá uma linha de texto *“Please fill in the following field:”* seguida de uma região em caixa cinza‑clara rotulada *MyTag*. O placeholder *Enter your text here* aparece em cinza claro até que o usuário digite.

## Conclusão

Agora você sabe como **inserir controle de conteúdo de texto simples** em um documento Word usando Aspose.Words para .NET. O tutorial abordou a inicialização de um `Document`, a inserção de um `StructuredDocumentTag` do tipo `PlainText` e a personalização de seu título, tag e placeholder. Ao compreender as opções de `SdtAppearance` e as armadilhas comuns, você pode criar formulários, modelos e relatórios automatizados que dependem de controles de conteúdo editáveis com confiança.

### O que vem a seguir?

- Explore outros tipos de SDT, como `RichText` ou `ComboBox` para listas suspensas.  
- Combine múltiplos controles de conteúdo dentro de tabelas ou repita‑os usando `RepeatingSection`.  
- Use `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` para ler ou modificar valores de controle programaticamente.

Sinta‑se à vontade para experimentar as variações mostradas anteriormente e integrar o padrão em seus pipelines de geração de documentos maiores. Boa codificação!


## O que você deve aprender a seguir?


Os tutoriais a seguir cobrem tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [How to create content control in C# with Aspose.Words](/words/english/net/programming-with-sdt/how-to-create-content-control-in-c-with-aspose-words/)
- [Create new Word document and insert content control in C#](/words/english/net/programming-with-sdt/create-new-word-document-and-insert-content-control-in-c/)
- [Add Content Using Document Builder in Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}