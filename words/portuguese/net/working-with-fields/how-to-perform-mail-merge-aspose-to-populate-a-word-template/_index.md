---
category: general
date: 2026-09-11
description: O Mail Merge da Aspose permite carregar um modelo Word e preenchê-lo
  com dados, automatizando a geração de documentos para criar cartas personalizadas.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- mail merge aspose
- populate word template
- load word template
- automate document generation
- create personalized letters
language: pt
lastmod: 2026-09-11
og_description: O Mail Merge da Aspose permite carregar um modelo Word e preenchê-lo,
  simplificando a geração de documentos para que você possa criar cartas personalizadas
  rapidamente.
og_image_alt: Screenshot of C# code using Aspose.Words to perform a mail merge on
  a Word template
og_title: 'Mail merge Aspose: preencha um modelo Word em minutos'
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Mail merge aspose lets you load word template and populate word template
    with data, automating document generation for creating personalized letters.
  headline: How to perform mail merge aspose to populate a Word template
  type: TechArticle
tags:
- Aspose.Words
- C#
- document automation
title: Como realizar a mesclagem de correspondência com Aspose para preencher um modelo
  do Word
url: /pt/net/working-with-fields/how-to-perform-mail-merge-aspose-to-populate-a-word-template/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como executar mail merge Aspose para preencher um modelo Word

Se você precisa **mail merge aspose** para gerar um lote de cartas personalizadas, este guia mostra exatamente como carregar um modelo Word, preenchê‑lo com dados e automatizar a geração de documentos em algumas linhas de C#. Seja construindo um sistema de correspondência ou uma ferramenta de relatórios, o exemplo completo abaixo permite criar cartas personalizadas sem escrever nenhuma lógica manual de mesclagem.

Você aprenderá como **load word template**, usar a classe low‑code `MailMerger` e **populate word template** com uma fonte de dados anônima. Ao final do tutorial, você terá um aplicativo de console pronto‑para‑executar que produz um documento Word mesclado que pode ser enviado por e‑mail, impresso ou arquivado.

## Prerequisites

Antes de começar, certifique‑se de que você tem:

* .NET 6.0 SDK ou posterior instalado  
* Uma licença válida do Aspose.Words for .NET (ou uma chave de avaliação gratuita)  
* O pacote NuGet `Aspose.Words` (versão 23.10 ou mais recente) instalado no seu projeto  
* Um arquivo Word (`MailMergeTemplate.docx`) que contém marcadores MERGEFIELD como **«Name»** e **«Age»**  

Você pode criar o modelo no Microsoft Word inserindo *Insert → Quick Parts → Field → MergeField* e nomeando os campos exatamente como os nomes das propriedades na sua fonte de dados.

## Step 1 – Prepare the data source for the mail merge

A mesclagem low‑code funciona com qualquer coleção enumerável. Neste exemplo usamos um array de objetos anônimos, mas você também poderia passar um `DataTable`, uma lista de POCOs ou dados lidos de um banco de dados.

```csharp
using Aspose.Words;
using Aspose.Words.LowCode;

// Sample data that will replace the MERGEFIELDs in the template
var data = new[]
{
    new { Name = "Alice",   Age = 30 },
    new { Name = "Bob",     Age = 45 },
    new { Name = "Charlie", Age = 28 }
};
```

**Por que isso importa:**  
O nome da propriedade de cada objeto (`Name`, `Age`) deve corresponder a um MERGEFIELD no modelo. A classe `MailMerger` mapeia automaticamente as propriedades para os campos, eliminando a necessidade de eventos manuais `FieldMerging`.

## Step 2 – Load the Word template that contains MERGEFIELDs

Carregar o modelo é simples com a classe `Document`. O caminho pode ser absoluto ou relativo ao diretório de trabalho do executável.

```csharp
// Load the Word template that contains MERGEFIELDs
Document template = new Document("YOUR_DIRECTORY/MailMergeTemplate.docx");
```

**Dica profissional:**  
Se você executar o código a partir do Visual Studio, defina *Copy to Output Directory* para o arquivo de modelo como **Copy always**. Isso garante que o arquivo esteja disponível quando o binário compilado for executado.

## Step 3 – Create a MailMerger instance bound to the template

A classe `MailMerger` está no namespace `Aspose.Words.LowCode` e fornece um único método `Execute` que aceita a fonte de dados.

```csharp
// Bind the template to a MailMerger instance
MailMerger merger = new MailMerger(template);
```

**Por que usar MailMerger?**  
`MailMerger` abstrai as chamadas boilerplate `MailMerge.Execute`, lidando com a detecção de campos, vinculação de dados e clonagem de documentos internamente. Isso torna o código ideal para cenários de **automate document generation** onde você deseja uma solução limpa e low‑code.

## Step 4 – Execute the low‑code merge using the prepared data

Chamar `Execute` retorna um novo `Document` que contém

## What Should You Learn Next?

Os tutoriais a seguir abordam tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Renomear campos de mesclagem do Word com Aspose.Words para Java](/words/english/java/mail-merge-reporting/rename-word-merge-fields-aspose-words-java/)
- [Criar documento Word com cabeçalho e rodapé usando Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Criar e estilizar um documento Word no Aspose.Words para .NET](/words/english/net/document-styling/apply-paragraph-style/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}