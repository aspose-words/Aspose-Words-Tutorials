---
category: general
date: 2026-08-07
description: Compare documentos Word em C# com Aspose.Words. Aprenda como comparar
  arquivos docx, gerar um relatório de comparação e lidar com revisões de forma eficiente.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- compare word documents
- word document comparison
- how to compare docx
- compare docx files
- compare word files
language: pt
lastmod: 2026-08-07
og_description: Compare documentos Word em C# usando Aspose.Words. Este tutorial mostra
  como comparar arquivos docx, incluir revisões e salvar um relatório detalhado para
  revisão.
og_image_alt: Comparison report when you compare word documents using Aspose.Words
og_title: Compare documentos Word em C# com Aspose.Words – guia completo
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Compare word documents in C# with Aspose.Words. Learn how to compare
    docx files, generate a comparison report, and handle revisions efficiently.
  headline: Compare word documents in C# using Aspose.Words
  type: TechArticle
- description: Compare word documents in C# with Aspose.Words. Learn how to compare
    docx files, generate a comparison report, and handle revisions efficiently.
  name: Compare word documents in C# using Aspose.Words
  steps:
  - name: '**Define comparison options** – decide whether to show revisions, ignore
      formatting, etc.'
    text: '**Define comparison options** – decide whether to show revisions, ignore
      formatting, etc.'
  - name: '**Execute the comparison** – the library returns a `ComparisonResult` object.'
    text: '**Execute the comparison** – the library returns a `ComparisonResult` object.'
  - name: '**Save the report** – the result can be saved as a new `.docx` that highlights
      insertions, deletions, and moves.'
    text: '**Save the report** – the result can be saved as a new `.docx` that highlights
      insertions, deletions, and moves.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Document Comparison
- docx
title: Comparar documentos Word em C# usando Aspose.Words
url: /pt/net/compare-documents/compare-word-documents-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Compare word documents in C# using Aspose.Words

Se você precisar **comparar documentos Word** programaticamente, o Aspose.Words torna isso simples. Este guia mostra **como comparar arquivos docx**, gerar um relatório de comparação e personalizar opções, como exibir revisões.

A comparação de documentos é uma necessidade comum para revisões jurídicas, negociações de contratos e versionamento de conteúdo. Ao final deste tutorial você será capaz de:

* Carregar dois arquivos `.docx` e executar uma **comparação de documentos Word**.  
* Incluir ou excluir revisões na saída.  
* Salvar o resultado como um novo arquivo Word que destaca as alterações.  

Nenhum serviço externo é necessário — tudo é executado localmente em uma aplicação .NET.

## Prerequisites

Antes de começar, certifique‑se de que você tem:

* .NET 6.0 ou superior instalado.  
* Uma cópia licenciada do **Aspose.Words for .NET** (a avaliação gratuita funciona para testes).  
* Dois arquivos Word (`Original.docx` e `Modified.docx`) colocados em um diretório conhecido.  

Se ainda não adicionou o Aspose.Words ao seu projeto, execute:

```bash
dotnet add package Aspose.Words
```

## Compare word documents – overall workflow

O processo de comparação consiste em três etapas lógicas:

1. **Definir opções de comparação** – decidir se exibe revisões, ignora formatação, etc.  
2. **Executar a comparação** – a biblioteca devolve um objeto `ComparisonResult`.  
3. **Salvar o relatório** – o resultado pode ser salvo como um novo `.docx` que destaca inserções, exclusões e movimentações.

Abaixo está um exemplo completo e executável que segue essas etapas.

```csharp
using Aspose.Words.LowCode;

namespace DocumentComparisonDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Define comparison options (e.g., include revisions in the result)
            ComparisonOptions comparisonOptions = new ComparisonOptions
            {
                ShowRevisions = true // Show insertions/deletions as tracked changes
            };

            // Step 2: Compare the original and modified documents
            // This is the core of the word document comparison.
            ComparisonResult comparisonResult = Comparer.Compare(
                "YOUR_DIRECTORY/Original.docx",   // path to the original file
                "YOUR_DIRECTORY/Modified.docx",   // path to the modified file
                comparisonOptions);

            // Step 3: Save the comparison report
            // The report will be a new .docx that visually marks all differences.
            comparisonResult.SaveReport("YOUR_DIRECTORY/ComparisonReport.docx");

            // Optional: Inform the user that the process completed.
            System.Console.WriteLine("Comparison report created successfully.");
        }
    }
}
```

### Why each part matters

* **ComparisonOptions** – controla a granularidade da comparação. Definir `ShowRevisions = true` reproduz a visualização nativa “Controlar Alterações” do Word, essencial para revisores que precisam ver cada edição.  
* **Comparer.Compare** – realiza o trabalho pesado. O método lê ambos os arquivos de origem, constrói um modelo interno de diff e devolve um `ComparisonResult`.  
* **SaveReport** – grava um novo `.docx` que contém o diff como alterações controladas, facilitando a abertura no Microsoft Word ou em qualquer visualizador compatível.

## Word document comparison options

Aspose.Words fornece diversas flags adicionais que podem ser combinadas com `ComparisonOptions`:

| Option | Description | Typical use case |
|--------|-------------|------------------|
| `ShowRevisions` | Mantém as alterações como revisões controladas. | Equipes jurídicas revisando alterações de contrato. |
| `IgnoreFormatting` | Ignora diferenças de fonte, estilo ou espaçamento. | Comparação apenas de conteúdo onde o layout não é importante. |
| `IgnoreHeadersFooters` | Ignora alterações em cabeçalhos/rodapés. | Quando apenas o texto do corpo importa. |
| `IgnoreCaseChanges` | Trata mudanças de maiúsculas/minúsculas como equivalentes. | Rascunhos onde a capitalização não é significativa. |

Você pode habilitar várias opções assim:

```csharp
ComparisonOptions options = new ComparisonOptions
{
    ShowRevisions = true,
    IgnoreFormatting = true,
    IgnoreHeadersFooters = true
};
```

## How to compare docx files with revisions

Quando você precisar **comparar arquivos docx** e manter um registro completo de auditoria, a flag `ShowRevisions` é indispensável. O relatório resultante conterá as barras de alteração nativas do Word, tornando‑o instantaneamente reconhecível pelos usuários finais.

```csharp
ComparisonOptions revOptions = new ComparisonOptions { ShowRevisions = true };
ComparisonResult revResult = Comparer.Compare("A.docx", "B.docx", revOptions);
revResult.SaveReport("RevisionReport.docx");
```

Abra `RevisionReport.docx` no Microsoft Word e você verá inserções destacadas em verde e exclusões em vermelho, exatamente como se tivesse usado o recurso “Comparar” interno do Word.

## Compare docx files in bulk

Se você tem muitos pares de documentos para avaliar, envolva a lógica de comparação em um loop:

```csharp
string[] originals = Directory.GetFiles("Originals", "*.docx");
string[] modified  = Directory.GetFiles("Modified", "*.docx");

for (int i = 0; i < originals.Length; i++)
{
    var result = Comparer.Compare(originals[i], modified[i], comparisonOptions);
    string reportPath = Path.Combine("Reports", $"Report_{i + 1}.docx");
    result.SaveReport(reportPath);
    Console.WriteLine($"Report {i + 1} saved.");
}
```

Esse padrão permite que você **compare arquivos docx** em grandes lotes sem intervenção manual.

## Compare word files – best practices and pitfalls

* **Os caminhos de arquivo devem ser absolutos ou relativos ao processo em execução.** Usar um caminho relativo como `"YOUR_DIRECTORY/Original.docx"` funciona quando o diretório de trabalho está configurado corretamente; caso contrário, forneça `Path.GetFullPath`.  
* **Documentos grandes (>100 MB) podem consumir memória significativa.** Considere fazer streaming dos arquivos ou aumentar o limite de memória do processo se encontrar `OutOfMemoryException`.  
* **Garanta que ambos os arquivos usem a mesma versão docx.** Misturar arquivos `.doc` antigos pode gerar resultados inesperados; converta‑os para `.docx` primeiro com `Document.Save(..., SaveFormat.Docx)`.  
* **Quando `ShowRevisions` está false, o resultado é um documento limpo sem marcadores de alteração.** Use esse modo se precisar apenas de um resumo das diferenças (por exemplo, um relatório de diff em texto simples).  

## Expected output

Depois de executar o código de exemplo, você encontrará `ComparisonReport.docx` na pasta de destino. Ao abri‑lo no Word, serão exibidos:

* **Inserções** – destacadas em verde com uma barra de alteração à esquerda.  
* **Exclusões** – mostradas em texto tachado vermelho.  
* **Texto movido** – indicado com um marcador de seta dupla.

![Comparison report showing differences between original and modified documents](comparison-report.png "Comparison report when you compare word documents using Aspose.Words")

*A imagem acima ilustra o layout típico de um relatório de comparação gerado pelo código.*

## Conclusion

Agora você sabe como **comparar documentos Word** em C# usando Aspose.Words, desde a configuração das opções de comparação até a geração de um relatório refinado que destaca cada mudança. Essa abordagem funciona tanto para pares individuais de arquivos quanto para operações em lote, e você pode ajustar a comparação para ignorar formatação, cabeçalhos ou alterações de caixa conforme necessário.

Próximos passos que você pode explorar:

* Integrar a rotina de comparação a uma API web para que usuários façam upload de dois arquivos e recebam um relatório instantaneamente.  
* Combinar **compare docx files** com SharePoint ou OneDrive para governança automatizada de documentos.  
* Usar a API `ComparisonResult` para extrair um resumo em texto simples das diferenças para registro ou notificações.

Ao dominar essas técnicas, você poderá automatizar fluxos de revisão de documentos, reduzindo o esforço manual.

## What Should You Learn Next?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Compare Options In Word Document](/words/english/net/compare-documents/compare-options/)
- [Compare For Equal In Word Document](/words/english/net/compare-documents/compare-for-equal/)
- [How to Compare Two Word Files with Aspose.Words for Java](/words/english/java/document-manipulation/comparing-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}