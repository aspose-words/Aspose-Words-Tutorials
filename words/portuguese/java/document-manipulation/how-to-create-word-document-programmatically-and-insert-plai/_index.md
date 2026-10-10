---
category: general
date: 2026-10-10
description: Criar documento Word programaticamente com Aspose.Words e inserir controle
  de conteúdo de texto simples – um guia passo a passo para desenvolvedores .NET.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- insert plain text content control
language: pt
lastmod: 2026-10-10
og_description: Crie um documento Word programaticamente com Aspose.Words e adicione
  um controle de conteúdo de texto simples que exibe texto de espaço reservado, permitindo
  campos de formulário dinâmicos em arquivos .docx.
og_image_alt: Screenshot of a Word document displaying a plain text content control
  placeholder
og_title: Criar documento Word programaticamente e adicionar um controle de conteúdo
  de texto simples
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Create word document programmatically with Aspose.Words and insert
    plain text content control – a step‑by‑step guide for .NET developers.
  headline: How to create word document programmatically and insert plain text content
    control
  type: TechArticle
tags:
- word
- document automation
- content control
- Aspose.Words
- C#
title: Como criar um documento Word programaticamente e inserir um controle de conteúdo
  de texto simples
url: /pt/java/document-manipulation/how-to-create-word-document-programmatically-and-insert-plai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como criar documento Word programaticamente e inserir controle de conteúdo de texto simples

Se você precisa **criar documento Word programaticamente**, este guia mostra exatamente como fazer isso com Aspose.Words for .NET. Em apenas algumas linhas de código, você também aprenderá a **inserir controle de conteúdo de texto simples** (também chamado de Structured Document Tag) para que o documento possa funcionar como um formulário preenchível.

Você percorrerá todo o fluxo de trabalho — desde a inicialização de um novo objeto `Document` até a gravação do arquivo .docx final. Nenhuma ferramenta externa é necessária, e o exemplo funciona com .NET 6, .NET 7 ou qualquer runtime .NET recente.

## Pré-requisitos

* Uma licença válida do Aspose.Words for .NET (ou use o modo de avaliação gratuito).  
* SDK .NET 6+ instalado.  
* Uma IDE como Visual Studio 2022, Rider ou VS Code.  

Se você ainda não instalou o pacote NuGet Aspose.Words, execute:

```bash
dotnet add package Aspose.Words
```

## Etapa 1: Criar um documento Word programaticamente

O primeiro passo é instanciar um `Document` vazio e um `DocumentBuilder`. O builder fornece uma API conveniente para adicionar conteúdo, páginas e Structured Document Tags (SDTs).

```csharp
using Aspose.Words;
using Aspose.Words.BuildingBlocks;
using Aspose.Words.Markup;

// Create an empty document and a builder attached to it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Por que isso importa** – `Document` representa todo o arquivo .docx na memória. Ao criá‑lo programaticamente, você evita a sobrecarga de abrir um arquivo modelo, o que é útil para gerar relatórios, faturas ou qualquer documento gerado sob demanda.

## Etapa 2: Inserir um controle de conteúdo de texto simples

Um **controle de conteúdo de texto simples** (SDT) permite que os usuários digitem texto em uma região predefinida. Ele também suporta texto de espaço reservado que aparece quando o controle está vazio.

```csharp
// Insert a plain‑text Structured Document Tag (SDT) with an identifier "MyTag"
StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, "MyTag");

// Set placeholder text that shows inside the control when it is empty
plainTextTag.PlaceholderName = "Enter name";
```

**Explicação** – `InsertStructuredDocumentTag` cria o SDT na posição atual do cursor do `DocumentBuilder`. O valor enum `StructuredDocumentTagType.PlainText` indica ao Aspose.Words que renderize uma caixa de texto simples em vez de uma caixa de combinação ou seletor de data. A propriedade `PlaceholderName` fornece uma pista visual para o usuário, semelhante ao texto de sugestão cinza que você vê em formulários modernos do Word.

### Variações comuns

| Variação | Como alcançar |
|-----------|-------------------|
| **Rich‑text content control** | Use `StructuredDocumentTagType.RichText` instead of `PlainText`. |
| **Seção repetitiva** | Use `StructuredDocumentTagType.Group` and nest other tags inside. |
| **Mapeamento XML personalizado** | Call `plainTextTag.SetXmlMapping(xmlPart, xpath, false)` after creating an `XmlPart`. |

## Etapa 3: Adicionar conteúdo adicional ao documento (opcional)

Você pode adicionar parágrafos regulares, tabelas ou imagens antes ou depois do controle de conteúdo. Aqui está um exemplo rápido que adiciona um título e um parágrafo:

```csharp
// Add a heading above the content control
builder.Font.Size = 16;
builder.Font.Bold = true;
builder.Writeln("Employee Information");

// Move the cursor back to the placeholder location (already set by InsertStructuredDocumentTag)
builder.Font.Size = 12;
builder.Font.Bold = false;
builder.Writeln(); // Adds a line break after the control
```

**Dica** – O cursor do builder move‑se automaticamente para o final do SDT inserido, portanto, quaisquer chamadas subsequentes a `Writeln` aparecerão após o controle.

## Etapa 4: Salvar o documento contendo o controle de conteúdo

Finalmente, grave o documento no disco. Você pode escolher qualquer formato suportado (`.docx`, `.pdf`, `.html`, etc.). Para este tutorial, salvamos como um arquivo Word.

```csharp
// Save the document to the specified path
string outputPath = Path.Combine(Environment.CurrentDirectory, "SdtExample.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

### Saída esperada

Ao abrir *SdtExample.docx* no Microsoft Word, você verá:

1. Um título **Informações do Funcionário**.  
2. Um controle de conteúdo de texto simples com o espaço reservado cinza **Digite o nome**.  

Se você clicar dentro do controle, o espaço reservado desaparece e você pode digitar qualquer texto. O identificador de tag do controle (`MyTag`) pode ser acessado programaticamente posteriormente para extração ou validação de dados.

## Exemplo completo e executável

Abaixo está um aplicativo de console autônomo que reúne todas as etapas. Copie o código para um novo projeto de console .NET e execute‑o.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordContentControlDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create an empty document and a DocumentBuilder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a plain‑text content control (SDT) with a tag identifier
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "MyTag");

            // 3️⃣ Set placeholder text that appears when the control is empty
            sdt.PlaceholderName = "Enter name";

            // Optional: add a heading above the control
            builder.MoveToDocumentStart(); // Ensure heading appears before the control
            builder.Font.Size = 16;
            builder.Font.Bold = true;
            builder.Writeln("Employee Information");

            // Move back to the end of the control to continue writing
            builder.MoveToDocumentEnd();
            builder.Font.Size = 12;
            builder.Font.Bold = false;
            builder.Writeln(); // Adds a line break after the control

            // 4️⃣ Save the document
            string outputPath = Path.Combine(Environment.CurrentDirectory, "SdtExample.docx");
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

Executar o programa imprime o caminho completo do arquivo gerado. Abra o arquivo no Word para verificar se o **controle de conteúdo de texto simples** aparece com seu espaço reservado.

## Solução de problemas e casos extremos

| Problema | Causa | Correção |
|----------|-------|----------|
| Texto de espaço reservado não aparece | O controle já está preenchido com texto ou o documento está aberto em um modo que oculta espaços reservados. | Garanta que o SDT esteja vazio antes de salvar, ou defina `sdt.IsShowingPlaceholder = true` (disponível em versões mais recentes do Aspose.Words). |
| Controle de conteúdo desaparece após salvar como PDF | A exportação para PDF não mantém campos de formulário interativos por padrão. | Use `PdfSaveOptions` com `SaveFormat.Pdf` e defina `ExportDocumentStructure = true`. |
| Identificador de tag não encontrado durante o processamento posterior | O nome da tag foi digitado incorretamente ou sobrescrito. | Verifique se o identificador passado para `InsertStructuredDocumentTag` corresponde ao nome que você consulta posteriormente (`MyTag`). |

## Melhores práticas para criar documentos Word programaticamente

* **Reutilize um único `DocumentBuilder`** por documento para evitar alocações de memória desnecessárias.  
* **Defina fontes e estilos antes de escrever texto**; alterá‑los depois que o conteúdo é adicionado pode causar formatação inconsistente.  
* **Libere objetos grandes** (por exemplo, `MemoryStream` se você transmitir o documento) usando instruções `using`.  
* **Valide o documento** com `doc.UpdateFields()` e `doc.UpdatePageLayout()` antes de salvar, especialmente ao adicionar tabelas ou imagens.  

## Conclusão

Agora você sabe como **criar documento Word programaticamente** e **inserir controle de conteúdo de texto simples** usando Aspose.Words for .NET. O exemplo completo demonstra a inicialização do documento, inserção de SDT com texto de espaço reservado, conteúdo adicional opcional e salvamento em um arquivo .docx.

A partir daqui, você pode:

* Substituir o controle de texto simples por controles de **texto rico** ou **seletor de data**.  
* Preencher o documento com dados de um banco de dados e depois extrair os valores inseridos posteriormente usando `StructuredDocumentTag.GetText()`.  
* Exportar o mesmo documento para PDF, HTML ou formatos OpenXML preservando os campos de formulário.

Experimente diferentes tipos de tags e explore a API do Aspose.Words para criar modelos Word sofisticados e preenchíveis que se integrem perfeitamente às suas aplicações .NET. Feliz codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que expandem as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Adicionar um campo de formulário Combo Box a um documento Word com Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Inserir campo de formulário de entrada de texto em documento Word](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)
- [Adicionar um campo de formulário Check Box a um documento Word com Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}