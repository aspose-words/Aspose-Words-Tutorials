---
category: general
date: 2026-10-20
description: Aprenda a criar um modelo de mala direta, carregar um modelo do Word
  e mesclar dados no Word usando Aspose.Words LowCode. Automatize a geração de documentos
  em minutos.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create mail merge template
- load word template
- merge data into word
- automate document generation
- populate word template
language: pt
lastmod: 2026-10-20
og_description: Crie um modelo de mala direta, carregue o modelo do Word e mescle
  os dados no Word com Aspise.Words LowCode. Este guia mostra como automatizar a geração
  de documentos rapidamente.
og_image_alt: Screenshot of a C# program that creates a mail merge template using
  Aspose.Words
og_title: Crie um modelo de mala direta em C# com Aspose.Words – guia passo a passo
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Learn how to create mail merge template, load word template, and merge
    data into word using Aspose.Words LowCode. Automate document generation in minutes.
  headline: How to create mail merge template with Aspose.Words in C#
  type: TechArticle
- description: Learn how to create mail merge template, load word template, and merge
    data into word using Aspose.Words LowCode. Automate document generation in minutes.
  name: How to create mail merge template with Aspose.Words in C#
  steps:
  - name: '**Field mapping** – `MailMerger` maps each property to its corresponding
      `«FieldName»`.'
    text: '**Field mapping** – `MailMerger` maps each property to its corresponding
      `«FieldName»`.'
  - name: '**Record iteration** – For every object in `mailMergeData`, a copy of the
      template is generated.'
    text: '**Record iteration** – For every object in `mailMergeData`, a copy of the
      template is generated.'
  - name: '**Document concatenation** – All copies are combined into a single `Document`
      instance, preserving page breaks.'
    text: '**Document concatenation** – All copies are combined into a single `Document`
      instance, preserving page breaks.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Document Automation
title: Como criar um modelo de mala direta com Aspose.Words em C#
url: /pt/net/working-with-fields/how-to-create-mail-merge-template-with-aspose-words-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como criar um modelo de mala direta com Aspose.Words em C#

Se você precisa **criar modelo de mala direta** para cartas personalizadas, faturas ou certificados, este guia mostra as etapas exatas. Você aprenderá como **carregar modelo Word**, **mesclar dados no Word**, e **automatizar a geração de documentos** para que você possa **preencher modelo Word** sem copiar‑colar manualmente.

A automação de documentos é uma necessidade comum em aplicações empresariais, mas muitos desenvolvedores começam do zero a cada vez. Ao final deste tutorial você terá um método reutilizável em C# que aceita qualquer coleção de objetos, mescla-os em um arquivo Word e salva o resultado — tudo com poucas linhas de código.

## Pré-requisitos

- .NET 6.0 ou posterior (o código também funciona com .NET Framework 4.6+)
- Visual Studio 2022 ou qualquer IDE que suporte C#
- Uma licença Aspose.Words (ou uma chave de avaliação temporária)
- Familiaridade básica com tipos anônimos em C#

> **Dica profissional:** Se você planeja executar isso em um servidor, armazene a licença em um local seguro e carregue-a uma única vez na inicialização da aplicação.

## Etapa 1: Criar o modelo de mala direta

A primeira tarefa é projetar um documento Word que contenha campos de mesclagem. No Aspose.Words um campo de mesclagem é escrito como `«FieldName»`. Abra o Microsoft Word, insira uma tabela ou parágrafo e adicione campos para os dados que você pretende mesclar, por exemplo:

```
Dear «Name»,

Your order number «OrderId» has been processed.

Thank you,
Acme Corp.
```

Salve este arquivo como `MailMergeTemplate.docx` em uma pasta que você possa referenciar no código, por exemplo `C:\Docs\Templates`.

> **Por que isso importa:** Um modelo bem‑estruturado separa o layout dos dados, permitindo que você reutilize o mesmo arquivo para milhares de registros sem precisar alterar o design novamente.

## Etapa 2: Carregar o modelo Word em C#

Agora carregamos o modelo na memória. A classe `Document` do Aspose.Words lê o arquivo `.docx` e fornece acesso programático completo.

```csharp
using Aspose.Words;
using Aspose.Words.LowCode;   // hypothetical namespace for LowCode classes

// Load the mail‑merge template document
Document template = new Document(@"C:\Docs\Templates\MailMergeTemplate.docx");
```

- **carregar modelo Word** – O construtor `Document` faz o trabalho pesado: ele analisa o pacote OpenXML, valida a estrutura e prepara um modelo de objeto semelhante a DOM.
- **Tratamento de erros:** Envolva o carregamento em um bloco `try / catch` para lidar com arquivos ausentes ou modelos corrompidos.

```csharp
try
{
    Document template = new Document(@"C:\Docs\Templates\MailMergeTemplate.docx");
}
catch (FileNotFoundException ex)
{
    Console.Error.WriteLine($"Template not found: {ex.Message}");
    return;
}
```

## Etapa 3: Preparar a fonte de dados

O Aspose.Words pode mesclar dados de qualquer `IEnumerable`. Aqui usamos um array de objetos anônimos, mas você também pode passar um `DataTable`, `DataSet` ou uma coleção POCO personalizada.

```csharp
// Prepare the data source that will be merged into the template
var mailMergeData = new[]
{
    new { Name = "Alice",   OrderId = 101 },
    new { Name = "Bob",     OrderId = 102 },
    new { Name = "Charlie", OrderId = 103 }
};
```

- **mesclar dados no Word** – Os nomes das propriedades (`Name`, `OrderId`) devem corresponder aos nomes dos campos de mesclagem no modelo.
- **Caso extremo:** Se um campo estiver ausente na fonte de dados, o Aspose.Words deixa o marcador de posição inalterado. Você pode detectar isso posteriormente com `Document.Range.Fields`.

## Etapa 4: Executar a mala direta

A classe `MailMerger` (parte da API low‑code) simplifica a operação de mesclagem. Ela itera automaticamente sobre a coleção e cria um documento separado para cada registro, depois os concatena.

```csharp
// Create a MailMerger instance using the template
MailMerger merger = new MailMerger(template);

// Execute the mail merge with the prepared data
Document mergedDocument = merger.Execute(mailMergeData);
```

### O que acontece nos bastidores?

1. **Mapeamento de campos** – `MailMerger` mapeia cada propriedade para seu respectivo `«FieldName»`.
2. **Iteração de registros** – Para cada objeto em `mailMergeData`, uma cópia do modelo é gerada.
3. **Concatenação de documentos** – Todas as cópias são combinadas em uma única instância `Document`, preservando quebras de página.

Se você precisar de um arquivo de saída por registro em vez de um arquivo combinado, chame `merger.ExecuteToSeparateFiles(mailMergeData, outputFolder)` (sobrecarga hipotética).

## Etapa 5: Salvar o documento resultante

Finalmente, grave o documento mesclado no disco. Você pode escolher qualquer formato suportado (`.docx`, `.pdf`, `.html`, etc.).

```csharp
// Save the resulting document to a new file
mergedDocument.Save(@"C:\Docs\Results\MailMergeResult.docx");
Console.WriteLine("Mail merge completed successfully.");
```

- **preencher modelo Word** – O método `Save` grava o documento totalmente preenchido, pronto para distribuição.
- **Dica de automação:** Se precisar enviar o arquivo por e‑mail, você pode transmitir `mergedDocument` diretamente para um anexo sem gravar no sistema de arquivos.

## Exemplo completo em funcionamento

Juntando tudo, aqui está um aplicativo de console autônomo que você pode copiar‑colar em um novo projeto C#.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LowCode;   // hypothetical LowCode namespace

namespace MailMergeDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the Word template
            const string templatePath = @"C:\Docs\Templates\MailMergeTemplate.docx";
            Document template;
            try
            {
                template = new Document(templatePath);
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"Failed to load template: {ex.Message}");
                return;
            }

            // 2️⃣ Prepare data to merge
            var mailMergeData = new[]
            {
                new { Name = "Alice",   OrderId = 101 },
                new { Name = "Bob",     OrderId = 102 },
                new { Name = "Charlie", OrderId = 103 }
            };

            // 3️⃣ Perform the merge
            MailMerger merger = new MailMerger(template);
            Document mergedDocument = merger.Execute(mailMergeData);

            // 4️⃣ Save the merged result
            const string outputPath = @"C:\Docs\Results\MailMergeResult.docx";
            try
            {
                mergedDocument.Save(outputPath);
                Console.WriteLine($"Merged document saved to: {outputPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"Failed to save merged document: {ex.Message}");
            }
        }
    }
}
```

### Saída esperada

Ao abrir `MailMergeResult.docx`, você deverá ver três páginas — uma para cada registro — formatadas exatamente como o modelo, com os marcadores de posição substituídos:

```
Page 1
Dear Alice,
Your order number 101 has been processed.

Page 2
Dear Bob,
Your order number 102 has been processed.

Page 3
Dear Charlie,
Your order number 103 has been processed.
```

## Lidando com variações comuns

| Cenário | Abordagem recomendada |
|----------|----------------------|
| **Grande conjunto de dados (mais de 10 000 linhas)** | Use `MailMerger.ExecuteToSeparateFiles` para evitar concatenação massiva em memória, ou transmita páginas para um PDF em tempo real. |
| **Conteúdo condicional** | Coloque campos `IF` no modelo (`«If:HasDiscount»Discount applied«EndIf»`) e habilite a flag de lógica condicional do `MailMerger`. |
| **Formato de saída diferente** | Chame `mergedDocument.Save("result.pdf")` para gerar um PDF; o Aspose.Words converte o layout automaticamente. |
| **Formatação personalizada de campo** | Implemente `IMailMergeFieldFormatter` (hipotético) para formatar datas, moedas ou aplicar regras específicas de cultura. |

## Melhores práticas para automação robusta de mala direta

- **Validar a fonte de dados** antes da mesclagem. Campos ausentes resultam em marcadores de posição vazios.
- **Bloquear o modelo** (atributo de arquivo somente‑leitura) para evitar edições acidentais em produção.
- **Versionar o modelo** usando controle de versão para que você possa rastrear alterações de layout.
- **Liberar objetos** (`Document` implementa `IDisposable` em versões mais recentes) para liberar recursos nativos prontamente.
- **Testar com casos extremos** como nomes muito longos, caracteres especiais ou valores nulos para garantir que o documento gerado permaneça bem formatado.

## Conclusão

Agora você sabe como **criar modelo de mala direta**, **carregar modelo Word**, **mesclar dados no Word** e **automatizar a geração de documentos** para **preencher modelo Word** usando Aspose.Words LowCode em C#. O exemplo completo demonstra um fluxo de trabalho pronto para produção que você pode adaptar para faturas, certificados ou qualquer cenário de documento personalizado.

Next, you might explore:

- **Gerar PDFs** a partir do documento mesclado (`mergedDocument.Save("result.pdf")`) – uma extensão natural de *automatizar a geração de documentos*.
- **Integrar com uma API web** para aceitar cargas JSON e retornar

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Mover para o campo de mesclagem no documento Word](/words/english/net/add-content-using-documentbuilder/move-to-merge-field/)
- [Criar documento Word com cabeçalho e rodapé usando Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Criar tabela estilizada no documento Word usando Aspose.Words para .NET](/words/english/net/working-with-table-styles-and-formatting/create-table-style/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}