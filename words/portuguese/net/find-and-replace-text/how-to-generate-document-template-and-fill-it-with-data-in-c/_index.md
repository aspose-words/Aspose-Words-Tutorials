---
category: general
date: 2026-09-21
description: Aprenda a gerar modelo de documento, preencher modelo do Word e substituir
  marcadores em um arquivo DOCX usando C# – guia passo a passo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- generate document template
- populate word template
- how to replace placeholder
- fill docx template
- replace text docx
language: pt
lastmod: 2026-09-21
og_description: Gere um modelo de documento em C# preenchendo um modelo do Word, substituindo
  marcadores de posição e salvando um arquivo DOCX preenchido. Siga este guia completo.
og_image_alt: Screenshot of a C# program generating and filling a DOCX template
og_title: Gerar modelo de documento em C# – preencher arquivos DOCX com dados
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to generate document template, populate word template and
    replace placeholders in a DOCX file using C# – step‑by‑step guide.
  headline: How to generate document template and fill it with data in C#
  type: TechArticle
tags:
- C#
- DOCX
- template processing
title: Como gerar um modelo de documento e preenchê-lo com dados em C#
url: /pt/net/find-and-replace-text/how-to-generate-document-template-and-fill-it-with-data-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como gerar modelo de documento e preenchê-lo com dados em C#

Se você precisa **gerar modelo de documento** que podem ser reutilizados para faturas, contratos ou relatórios, este guia mostra exatamente como fazer. Você aprenderá a **preencher modelo Word** placeholders, substituí‑los por valores reais e, finalmente, **preencher arquivos docx template** programaticamente.

Criar um modelo reutilizável elimina a cópia‑e‑cola manual e garante consistência em todos os documentos gerados. As etapas abaixo funcionam com qualquer arquivo `.docx` que contenha tokens de placeholder simples, como `{{Name}}`.

## Pré-requisitos

* .NET 6.0 SDK ou posterior instalado  
* Visual Studio 2022 (ou qualquer IDE de sua preferência)  
* O pacote NuGet **Aspose.Words for .NET** – ele fornece a classe `Document` usada no exemplo  

Você pode adicionar o pacote com o seguinte comando:

```bash
dotnet add package Aspose.Words
```

## Etapa 1: Preparar o modelo Word

Crie um documento Word (`Template.docx`) que contenha placeholders onde os dados dinâmicos devem aparecer. Uma convenção comum são chaves duplas:

```
Dear {{Name}},

Your order #{{OrderId}} has been shipped on {{ShipDate}}.
```

Salve o arquivo em uma pasta que você possa referenciar no código, por exemplo `C:\Docs\Template.docx`.

## Etapa 2: Carregar o documento modelo

A primeira ação programática é carregar o modelo na memória. O construtor `Document` lê o arquivo e constrói um modelo de objeto que você pode manipular.

```csharp
using System;
using Aspose.Words;

class Program
{
    static void Main()
    {
        // Load the template document from disk
        string templatePath = @"C:\Docs\Template.docx";
        Document doc = new Document(templatePath);
```

**Por que isso importa:** Carregar o arquivo cria uma cópia limpa a cada vez, de modo que o modelo original permanece intacto para execuções futuras.

## Etapa 3: Substituir placeholders por dados reais

Aspose.Words fornece um método simples `Range.Replace` que varre o documento em busca de uma string específica e a substitui. Envolva a chamada em um método auxiliar para manter o fluxo principal organizado.

```csharp
        // Helper to replace a single placeholder
        void ReplacePlaceholder(string placeholder, string value)
        {
            // The placeholder includes the curly braces exactly as they appear in the template
            doc.Range.Replace(placeholder, value, new FindReplaceOptions());
        }

        // Populate the template with real values
        ReplacePlaceholder("{{Name}}", "John Doe");
        ReplacePlaceholder("{{OrderId}}", "A12345");
        ReplacePlaceholder("{{ShipDate}}", DateTime.Today.ToString("MMMM d, yyyy"));
```

**Como funciona:** `Range.Replace` percorre cada parágrafo, célula de tabela, cabeçalho e rodapé, garantindo que todas as ocorrências do token sejam atualizadas. Esta é a maneira mais confiável de **como substituir placeholder** texto em um arquivo DOCX.

### Lidando com múltiplas ocorrências e tokens ausentes

* Se um placeholder aparecer mais de uma vez, `Replace` atualiza todas as instâncias automaticamente.  
* Se um placeholder estiver ausente, o método simplesmente não faz nada — nenhuma exceção é lançada.  
* Para documentos grandes, você pode melhorar o desempenho desativando `doc.UpdateFields()` até que todas as substituições estejam concluídas.

## Etapa 4: Salvar o documento preenchido

Depois que todos os placeholders forem substituídos, grave o resultado em um novo arquivo. Manter a saída separada preserva o modelo original para execuções futuras.

```csharp
        // Save the filled document to a new file
        string outputPath = @"C:\Docs\FilledTemplate.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Resultado:** `FilledTemplate.docx` agora contém o conteúdo personalizado:

```
Dear John Doe,

Your order #A12345 has been shipped on September 21, 2026.
```

## Etapa 5: Verificar a saída (opcional)

Se você quiser confirmar programaticamente que as substituições foram bem‑sucedidas, pode ler o arquivo salvo novamente e procurar pelos valores esperados:

```csharp
        Document verifyDoc = new Document(outputPath);
        bool nameReplaced = verifyDoc.Range.Text.Contains("John Doe");
        Console.WriteLine($"Name replacement successful: {nameReplaced}");
```

Executar a etapa de verificação imprime `true` quando o placeholder foi substituído corretamente.

## Armadilhas comuns e dicas de boas práticas

| Problema | Por que acontece | Correção recomendada |
|----------|------------------|----------------------|
| **Placeholders contêm espaços extras** | `"{{ Name }}"` não corresponde a `"{{Name}}"`. | Mantenha os tokens de placeholder sem espaços em branco, ou faça trim em ambos os lados antes da substituição. |
| **Word adiciona formatação oculta** | O Word pode armazenar o placeholder dividido em várias runs, fazendo com que `Replace` não o encontre. | Use `Document.Range.Replace` com `FindReplaceOptions` configurado para `MatchCase = false` e `FindWholeWordsOnly = false`. |
| **Documentos grandes causam lentidão** | Substituir tokens um a um dispara uma varredura completa do documento a cada vez. | Faça substituições em lote em uma única passagem chamando `Range.Replace` para cada token antes de salvar. |
| **Salvar em pasta somente‑leitura** | `doc.Save` lança uma `UnauthorizedAccessException`. | Garanta que o diretório de destino tenha permissões de escrita, ou escolha um caminho gravável pelo usuário (por exemplo, `%TEMP%`). |

## Exemplo completo funcionando

Abaixo está o programa completo e autocontido que você pode copiar, colar e executar.

```csharp
using System;
using Aspose.Words;

class Program
{
    static void Main()
    {
        // Paths – adjust to your environment
        string templatePath = @"C:\Docs\Template.docx";
        string outputPath   = @"C:\Docs\FilledTemplate.docx";

        // 1️⃣ Load the template document
        Document doc = new Document(templatePath);

        // 2️⃣ Replace placeholders
        void Replace(string placeholder, string value) =>
            doc.Range.Replace(placeholder, value, new FindReplaceOptions());

        Replace("{{Name}}", "John Doe");
        Replace("{{OrderId}}", "A12345");
        Replace("{{ShipDate}}", DateTime.Today.ToString("MMMM d, yyyy"));

        // 3️⃣ Save the filled document
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");

        // 4️⃣ (Optional) Verify replacement
        Document verify = new Document(outputPath);
        Console.WriteLine($"Verification – name found: {verify.Range.Text.Contains("John Doe")}");
    }
}
```

**Saída esperada no console**

```
Document saved to C:\Docs\FilledTemplate.docx
Verification – name found: True
```

Abra `FilledTemplate.docx` no Microsoft Word para ver o texto personalizado.

## Conclusão

Agora você sabe como **gerar modelo de documento**, **preencher modelo Word**, e **preencher arquivos docx template** por meio de tokens **como substituir placeholder** com dados reais. A abordagem funciona para qualquer número de placeholders e escala para documentos grandes quando você segue as dicas de boas práticas.

### O que vem a seguir?

* **Tabelas dinâmicas:** Use `DocumentBuilder` para inserir linhas com base em coleções.  
* **Seções condicionais:** Oculte ou exiba partes do modelo com campos `IF`.  
* **Exportação para PDF:** Chame `doc.Save("output.pdf")` para criar uma versão PDF do documento preenchido.  

Experimente essas variações para construir um mecanismo completo de geração de documentos para faturas, contratos ou qualquer relatório repetitivo.

---


## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Documento Word - Encontrar e Substituir Texto](/words/english/net/find-and-replace-text/)
- [Gerar Documento Word](/words/english/java/word-processing/generate-word-document/)
- [Recuperar DOCX Corrompido – Abrir e Carregar Documento Word](/words/english/python-net/document-operations/recover-corrupted-docx-open-load-word-document/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}