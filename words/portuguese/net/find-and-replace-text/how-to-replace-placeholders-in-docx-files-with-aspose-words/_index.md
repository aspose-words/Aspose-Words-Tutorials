---
category: general
date: 2026-10-13
description: substitua marcadores de posição em docx usando Aspose.Words e aprenda
  a preencher modelo Word com dados em poucos minutos
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- replace placeholders in docx
- fill word template with data
language: pt
lastmod: 2026-10-13
og_description: substitua marcadores de posição em docx com Aspose.Words e preencha
  o modelo Word com dados. Siga este tutorial passo a passo para automatizar a geração
  de documentos.
og_image_alt: Illustration of a Word document where {{FirstName}} and {{LastName}}
  have been replaced with real values
og_title: Substitua marcadores de posição em docx – guia rápido para desenvolvedores
  C#
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: replace placeholders in docx using Aspose.Words and learn to fill word
    template with data in a few minutes
  headline: How to replace placeholders in docx files with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Como substituir marcadores de posição em arquivos docx com Aspose.Words
url: /pt/net/find-and-replace-text/how-to-replace-placeholders-in-docx-files-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como substituir marcadores em arquivos docx com Aspose.Words

Se você precisa **substituir marcadores em arquivos docx**, este guia mostra como fazer isso com Aspose.Words para .NET. Você também aprenderá a **preencher modelo Word com dados** para gerar documentos personalizados automaticamente.

A automação de documentos é uma necessidade comum em faturamento, integração de RH e relatórios. Ao final deste tutorial você terá um aplicativo console completo e executável que carrega um modelo Word, substitui quaisquer tokens `{{Placeholder}}` e salva o resultado como um novo arquivo.

## Prerequisites

Antes de começar, certifique‑se de que você tem:

* .NET 6.0 SDK ou posterior instalado  
* Visual Studio 2022 (ou qualquer IDE que suporte .NET)  
* Uma licença do Aspose.Words para .NET ou uma cópia de avaliação gratuita (a API funciona sem licença, mas adiciona uma marca d'água)  
* Um modelo Word (`Template.docx`) que contém tokens de marcador como `{{FirstName}}` e `{{LastName}}`

Esses itens são suficientes para executar o código exatamente como mostrado.

## Etapa 1: Criar um novo projeto console

Abra um terminal e execute o comando a seguir para gerar um aplicativo console mínimo:

```bash
dotnet new console -n DocxPlaceholderReplacer
cd DocxPlaceholderReplacer
```

Adicione o pacote NuGet Aspose.Words:

```bash
dotnet add package Aspose.Words
dotnet add package Aspose.Words.LowCode
```

O projeto agora referencia as bibliotecas necessárias para a substituição de marcadores.

## Etapa 2: Carregar o modelo DOCX

Crie um arquivo chamado `Program.cs` (ou substitua o existente) e adicione as diretivas using:

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.LowCode;
```

O primeiro passo lógico é carregar o documento modelo. Esta operação cria uma representação em memória do arquivo Word, que pode ser manipulada programaticamente.

```csharp
// Step 2: Load the DOCX template
string templatePath = @"YOUR_DIRECTORY/Template.docx";
Document template = new Document(templatePath);
Console.WriteLine($"Loaded template from '{templatePath}'.");
```

**Por que isso importa:** Carregar o arquivo uma única vez mantém a sobrecarga de I/O baixa e fornece acesso total à árvore de nós do documento, que a classe `Replacer` percorrerá para encontrar marcadores.

## Etapa 3: Configurar o Replacer

Aspose.Words.LowCode fornece a utilidade `Replacer`, que escaneia automaticamente o documento em busca de marcadores `{{…}}` e os substitui pelos valores fornecidos.

```csharp
// Step 3: Create a Replacer instance for the loaded document
Replacer replacer = new Replacer(template);
Console.WriteLine("Replacer initialized.");
```

**Dica profissional:** O `Replacer` funciona com qualquer forma que contenha texto (parágrafos, tabelas, cabeçalhos, rodapés, etc.). Não é necessário percorrer manualmente a árvore de nós.

## Etapa 4: Definir os valores dos marcadores

Prepare um dicionário onde cada chave corresponde exatamente a um token de marcador como aparece no modelo, e cada valor é o texto que você deseja inserir.

```csharp
// Step 4: Define placeholder values to insert
var placeholderValues = new Dictionary<string, string>
{
    { "{{FirstName}}", "Alice" },
    { "{{LastName}}", "Smith" },
    // Add more entries as required, e.g.:
    // { "{{Date}}", DateTime.Today.ToShortDateString() }
};

Console.WriteLine("Placeholder values prepared:");
foreach (var kvp in placeholderValues)
{
    Console.WriteLine($"  {kvp.Key} => {kvp.Value}");
}
```

**Por que isso importa:** Usar um dicionário permite escalar a solução para dezenas de campos sem alterar a lógica de substituição.

## Etapa 5: Executar a substituição

Chame o método `Replace`, passando o dicionário. O método itera sobre cada nó de texto, detecta o padrão `{{…}}` e o substitui pelo valor correspondente.

```csharp
// Step 5: Replace placeholders with actual data
replacer.Replace(placeholderValues);
Console.WriteLine("All placeholders have been replaced.");
```

**Tratamento de casos extremos:** Se um marcador no documento não existir no dicionário, o `Replacer` o deixa inalterado. Esse comportamento evita perda acidental de dados e torna o código seguro para modelos parcialmente preenchidos.

## Etapa 6: Salvar o documento preenchido

Finalmente, grave o documento modificado em um novo arquivo. Manter o modelo original inalterado permite reutilizá‑lo em execuções subsequentes.

```csharp
// Step 6: Save the filled document
string outputPath = @"YOUR_DIRECTORY/FilledTemplate.docx";
template.Save(outputPath);
Console.WriteLine($"Filled document saved to '{outputPath}'.");
```

Ao abrir `FilledTemplate.docx`, você deverá ver:

```
Alice Smith
```

em vez dos tokens originais `{{FirstName}} {{LastName}}`.

## Código-fonte completo

Abaixo está o programa completo e autônomo. Copie‑o para `Program.cs`, substitua `YOUR_DIRECTORY` por um caminho de pasta real e execute `dotnet run`.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.LowCode;

class Program
{
    static void Main()
    {
        // Load the template
        string templatePath = @"YOUR_DIRECTORY/Template.docx";
        Document template = new Document(templatePath);
        Console.WriteLine($"Loaded template from '{templatePath}'.");

        // Initialize the replacer
        Replacer replacer = new Replacer(template);
        Console.WriteLine("Replacer initialized.");

        // Prepare placeholder values
        var placeholderValues = new Dictionary<string, string>
        {
            { "{{FirstName}}", "Alice" },
            { "{{LastName}}", "Smith" }
        };

        Console.WriteLine("Placeholder values prepared:");
        foreach (var kvp in placeholderValues)
        {
            Console.WriteLine($"  {kvp.Key} => {kvp.Value}");
        }

        // Perform replacement
        replacer.Replace(placeholderValues);
        Console.WriteLine("All placeholders have been replaced.");

        // Save the result
        string outputPath = @"YOUR_DIRECTORY/FilledTemplate.docx";
        template.Save(outputPath);
        Console.WriteLine($"Filled document saved to '{outputPath}'.");
    }
}
```

### Saída esperada no console

```
Loaded template from 'YOUR_DIRECTORY/Template.docx'.
Replacer initialized.
Placeholder values prepared:
  {{FirstName}} => Alice
  {{LastName}} => Smith
All placeholders have been replaced.
Filled document saved to 'YOUR_DIRECTORY/FilledTemplate.docx'.
```

### Conteúdo esperado em `FilledTemplate.docx`

Se o modelo original continha a linha:

```
{{FirstName}} {{LastName}}
```

o arquivo salvo exibirá:

```
Alice Smith
```

## Perguntas comuns e variações

**Posso substituir marcadores dentro de tabelas?**  
Sim. O `Replacer` escaneia todos os nós que contêm texto, incluindo células, cabeçalhos e rodapés. Nenhum código adicional é necessário.

**E se eu precisar de lógica condicional (por exemplo, ocultar um parágrafo quando um valor está vazio)?**  
Você pode remover nós antes de chamar `Replace`:

```csharp
if (string.IsNullOrEmpty(placeholderValues["{{OptionalField}}"]))
{
    // Find the paragraph that contains the placeholder and remove it
    Node paragraph = template.GetChildNodes(NodeType.Paragraph, true)
                             .FirstOrDefault(p => p.GetText().Contains("{{OptionalField}}"));
    paragraph?.Remove();
}
```

**A substituição diferencia maiúsculas de minúsculas?**  
A correspondência padrão é exata, incluindo maiúsculas/minúsculas. Certifique‑se de que as chaves do seu dicionário correspondam exatamente aos tokens do modelo.

**Como trabalhar com documentos grandes sem uso excessivo de memória?**  
Aspose.Words processa documentos de forma streaming ao salvar. Para arquivos extremamente grandes, considere usar a classe `LoadOptions` com `LoadFormat.Docx` e a propriedade `LoadFormat` para ajustar o consumo de memória.

## Conclusão

Agora você sabe como **substituir marcadores em arquivos docx** e **preencher modelo Word com dados** usando Aspose.Words para .NET. O tutorial abordou o carregamento de um modelo, a configuração de um `Replacer`, o fornecimento de um dicionário de valores, a execução da substituição e a gravação do resultado. Esse padrão escala para qualquer número de marcadores e funciona em todas as estruturas de documentos Word.

## Próximos passos

* Explore opções de formatação, como aplicar estilos ao texto inserido.  
* Combine esta abordagem com dados de um banco de dados para gerar cartas personalizadas em massa.  
* Investigue outras utilidades low‑code como `SmartTagProcessor` para cenários de modelo mais avançados.  

Sinta‑se à vontade para experimentar marcadores adicionais, seções condicionais ou inserção de imagens para ampliar as capacidades do seu fluxo de automação Word. Feliz codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Inserir imagem inline em documento Word usando Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Inserir data dinâmica no cabeçalho do documento Word usando Aspose.Words para .NET](/words/english/net/working-with-headers-and-footers/insert-header-date/)
- [Criar documento Word em branco com Aspose.Words – Guia passo a passo](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}