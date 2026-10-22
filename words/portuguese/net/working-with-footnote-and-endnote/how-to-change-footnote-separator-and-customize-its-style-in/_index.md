---
category: general
date: 2026-10-13
description: Como alterar o separador de nota de rodapé em um documento Word usando
  Aspose.Words. Aprenda a mudar a cor da fonte em um documento Word programaticamente.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to change footnote separator
- change font color in word document
- style footnote separator programmatically
- Aspose.Words footnote formatting
- C# Word automation
language: pt
lastmod: 2026-10-13
og_description: Como alterar o separador de notas de rodapé em um documento Word com
  Aspose.Words. Este tutorial mostra como mudar a cor da fonte em um documento Word
  usando C#.
og_image_alt: Screenshot of a Word document showing red footnote separator and blue
  endnote separator
og_title: Como alterar o separador de notas de rodapé em um documento Word – guia
  passo a passo
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: How to change footnote separator in a Word document using Aspose.Words.
    Learn to change font color in Word document programmatically.
  headline: How to change footnote separator and customize its style in a Word document
  type: TechArticle
- description: How to change footnote separator in a Word document using Aspose.Words.
    Learn to change font color in Word document programmatically.
  name: How to change footnote separator and customize its style in a Word document
  steps:
  - name: Why each line matters
    text: '* **Loading the document** (`new Document`) gives you an in‑memory representation
      that Aspose.Words can manipulate. * **`GetChild` with `ParagraphNodeType.FootnoteSeparator`**
      returns the hidden paragraph that Word uses to draw the line separating footnotes
      from the main text. The same method works '
  - name: Expected output
    text: 'When you open `FootnoteSeparatorsStyled.docx` in Microsoft Word:'
  - name: 1. Install Aspose.Words
    text: 'Open a terminal in your project folder and run:'
  - name: 2. Prepare the input file
    text: Place `Footnotes.docx` in a known directory (e.g., `C:\Docs`). Ensure the
      file contains at least one footnote and one endnote so the separator nodes exist.
  - name: 3. Write the C# program
    text: Create a new console project (`dotnet new console -n FootnoteStyler`) and
      replace the generated `Program.cs` with the full code block from the **How to
      change footnote separator** section. Remember to adjust the file paths to match
      your environment.
  - name: 4. Run and verify
    text: 'Execute the program:'
  - name: 5. Extend the solution
    text: '* **Different colors:** Use any `System.Drawing.Color` value, e.g., `Color.FromArgb(255,
      128, 0)` for orange. * **Custom line style:** Instead of changing the color,
      you can modify `ParagraphFormat` properties such as `LineSpacing`, `Shading`,
      or even replace the separator character. * **Multiple do'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- footnotes
- document styling
title: Como alterar o separador de notas de rodapé e personalizar seu estilo em um
  documento do Word
url: /pt/net/working-with-footnote-and-endnote/how-to-change-footnote-separator-and-customize-its-style-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como alterar o separador de nota de rodapé e personalizar seu estilo em um documento Word

Se você precisa **como alterar o separador de nota de rodapé** em um documento Word, este guia oferece uma solução completa e pronta‑para‑usar. Usando Aspose.Words para .NET, você também pode **alterar a cor da fonte em documento Word** em elementos como separadores de nota de rodapé e nota de fim, fazendo com que o arquivo final corresponda à sua identidade visual ou guia de estilo.

Os autores de documentos frequentemente perguntam: *Por que o separador de nota de rodapé padrão parece simples, e como posso fazê-lo se destacar?* A resposta é acessar diretamente os objetos de parágrafo do separador, ajustar suas propriedades de fonte e salvar o resultado. Este tutorial guia você por cada etapa, desde o carregamento de um arquivo .docx até a persistência da saída estilizada.

Você aprenderá a:

* Carregar um arquivo Word que já contém notas de rodapé e notas de fim.  
* Localizar os parágrafos separadores de nota de rodapé e nota de fim.  
* Alterar a cor da fonte de cada separador (vermelho para notas de rodapé, azul para notas de fim).  
* Salvar o documento modificado sem perder nenhum conteúdo existente.

Nenhuma ferramenta externa é necessária além da biblioteca Aspose.Words e de um ambiente de desenvolvimento .NET.

## Pré-requisitos

* .NET 6.0 SDK ou posterior (o código também funciona com .NET Framework 4.7+).  
* Visual Studio 2022, Rider ou qualquer editor C# de sua preferência.  
* Pacote NuGet Aspose.Words for .NET (`Aspose.Words`).  
* Um arquivo Word de exemplo (`Footnotes.docx`) que contenha ao menos uma nota de rodapé e uma nota de fim.

> **Pro tip:** Se você não tem um arquivo de exemplo, crie um novo documento Word, insira uma nota de rodapé (`References → Insert Footnote`) e uma nota de fim (`References → Insert Endnote`). Salve-o como `Footnotes.docx` em uma pasta que você possa referenciar a partir do código.

## Como alterar o separador de nota de rodapé com Aspose.Words

O núcleo da tarefa é recuperar os parágrafos especiais que o Aspose.Words expõe como nós *separator*. Esses nós são do tipo `Paragraph` e podem ser formatados como qualquer outro parágrafo.

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

class FootnoteSeparatorStyler
{
    static void Main()
    {
        // Step 1: Load the source document that already contains footnotes/endnotes.
        Document doc = new Document(@"C:\Docs\Footnotes.docx");

        // Step 2: Get the footnote separator paragraph.
        Paragraph footnoteSeparator = (Paragraph)doc.GetChild(
            NodeType.Paragraph, (int)ParagraphNodeType.FootnoteSeparator, true);

        // Step 3: Get the endnote separator paragraph.
        Paragraph endnoteSeparator = (Paragraph)doc.GetChild(
            NodeType.Paragraph, (int)ParagraphNodeType.EndnoteSeparator, true);

        // Step 4: Change the font color of the footnote separator to red.
        footnoteSeparator.Font.Color = Color.Red;

        // Step 5: Change the font color of the endnote separator to blue.
        endnoteSeparator.Font.Color = Color.Blue;

        // Step 6: Save the modified document.
        doc.Save(@"C:\Docs\FootnoteSeparatorsStyled.docx");
    }
}
```

### Por que cada linha importa

* **Carregar o documento** (`new Document`) fornece uma representação em memória que o Aspose.Words pode manipular.  
* **`GetChild` com `ParagraphNodeType.FootnoteSeparator`** devolve o parágrafo oculto que o Word usa para desenhar a linha que separa as notas de rodapé do texto principal. O mesmo método funciona para o separador de nota de fim.  
* **Alterar `Font.Color`** afeta diretamente a aparência da linha porque o Word renderiza o separador como um parágrafo com um único caractere “‑”. Definir a cor para `Color.Red` (ou qualquer `System.Drawing.Color`) atualiza o estilo visual.  
* **Salvar** grava as alterações de volta a um arquivo .docx que qualquer processador de texto pode abrir.

### Saída esperada

Ao abrir `FootnoteSeparatorsStyled.docx` no Microsoft Word:

* A linha do separador de nota de rodapé aparece **vermelha**.  
* A linha do separador de nota de fim aparece **azul**.  

Todo o conteúdo original das notas de rodapé e notas de fim permanece intacto.

## Alterar a cor da fonte em documento Word usando C#

A operação demonstrada acima é um caso específico de uma capacidade mais ampla: **alterar a cor da fonte em documento Word** programaticamente. Uma vez que você tem um `Paragraph`, `Run` ou qualquer `Node` que contenha texto, pode ajustar sua propriedade `Font.Color`.

```csharp
// Example: Change the color of all headings (style "Heading 1") to dark green.
foreach (Paragraph para in doc.GetChildNodes(NodeType.Paragraph, true))
{
    if (para.ParagraphFormat.StyleIdentifier == StyleIdentifier.Heading1)
        para.Font.Color = Color.DarkGreen;
}
```

* Este trecho itera sobre cada parágrafo, verifica se ele usa o estilo `Heading 1` e define a cor da fonte.  
* Você pode adaptar a condição para direcionar notas de rodapé, tabelas ou qualquer outro tipo de nó.

## Divisão passo a passo

### 1. Instalar Aspose.Words

Abra um terminal na pasta do seu projeto e execute:

```bash
dotnet add package Aspose.Words
```

O pacote inclui todas as assemblies necessárias para o código mostrado anteriormente.

### 2. Preparar o arquivo de entrada

Coloque `Footnotes.docx` em um diretório conhecido (por exemplo, `C:\Docs`). Certifique‑se de que o arquivo contém ao menos uma nota de rodapé e uma nota de fim para que os nós separadores existam.

### 3. Escrever o programa C#

Crie um novo projeto de console (`dotnet new console -n FootnoteStyler`) e substitua o `Program.cs` gerado pelo bloco de código completo da seção **Como alterar o separador de nota de rodapé**. Lembre‑se de ajustar os caminhos dos arquivos para corresponder ao seu ambiente.

### 4. Executar e verificar

Execute o programa:

```bash
dotnet run
```

Após a execução, abra `FootnoteSeparatorsStyled.docx`. Você deverá ver as linhas separadoras vermelha e azul conforme descrito.

### 5. Expandir a solução

* **Cores diferentes:** Use qualquer valor `System.Drawing.Color`, por exemplo, `Color.FromArgb(255, 128, 0)` para laranja.  
* **Estilo de linha personalizado:** Em vez de mudar a cor, você pode modificar propriedades de `ParagraphFormat` como `LineSpacing`, `Shading` ou até substituir o caractere do separador.  
* **Múltiplos documentos:** Envolva a lógica em um método que aceita caminhos de entrada e saída e chame‑o em um loop para processamento em lote.

## Armadilhas comuns e como evitá‑las

| Sintoma | Causa | Correção |
|---------|-------|----------|
| `GetChild` returns `null` | O documento de origem não possui separador de nota de rodapé/fim (ex.: nenhuma nota). | Adicione ao menos uma nota de rodapé ou nota de fim, ou verifique `null` antes de acessar `Font`. |
| Alteração de cor não visível | O separador é renderizado como linha em vez de caractere em algumas versões do Word. | Defina `ParagraphFormat.LineSpacingRule = LineSpacingRule.Exactly` e `ParagraphFormat.LineSpacing = 1` para forçar um caractere visível. |
| Exceção em tempo de execução `FileNotFoundException` | Caminho do arquivo incorreto. | Use caminhos absolutos ou `Path.Combine` com `Environment.CurrentDirectory`. |

## Exemplo completo e executável

Abaixo está o programa completo que você pode copiar‑colar em um aplicativo de console. Ele inclui tratamento de erros e comentários que explicam cada operação.

```csharp
using System;
using System.Drawing;
using Aspose.Words;

namespace FootnoteSeparatorStyler
{
    class Program
    {
        static void Main()
        {
            // Paths – update these to match your environment.
            const string inputPath = @"C:\Docs\Footnotes.docx";
            const string outputPath = @"C:\Docs\FootnoteSeparatorsStyled.docx";

            // Load the document.
            Document doc = new Document(inputPath);

            // Retrieve footnote separator.
            Paragraph footnoteSeparator = (Paragraph)doc.GetChild(
                NodeType.Paragraph, (int)ParagraphNodeType.FootnoteSeparator, true);

            // Retrieve endnote separator.
            Paragraph endnoteSeparator = (Paragraph)doc.GetChild(
                NodeType.Paragraph, (int)ParagraphNodeType.EndnoteSeparator, true);

            // Guard against missing separators.
            if (footnoteSeparator == null || endnoteSeparator == null)
            {
                Console.WriteLine("The document does not contain footnote or endnote separators.");
                return;
            }

            // Change colors – this is the core of “change font color in word document”.
            footnoteSeparator.Font.Color = Color.Red;   // Footnote separator → red
            endnoteSeparator.Font.Color = Color.Blue; // Endnote separator → blue

            // Save the result.
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Executar este programa gera um arquivo Word onde a linha do separador de nota de rodapé fica vermelha e a linha do separador de nota de fim fica azul, atendendo ao requisito **como alterar o separador de nota de rodapé** enquanto demonstra **alterar a cor da fonte em documento Word**.

## Conclusão

Agora você sabe **como alterar o separador de nota de rodapé** em um documento Word usando Aspose.Words para .NET e como **alterar a cor da fonte em documento Word** programaticamente. O procedimento é:

1. Carregar o documento.  
2. Recuperar os parágrafos ocultos do separador.  
3. Definir suas propriedades `Font.Color`.  
4. Salvar o arquivo modificado.

A partir daqui, você pode explorar estilos mais avançados — ajustar a espessura da linha, aplicar fontes diferentes ou automatizar o processo em vários arquivos. Dominar essas técnicas lhe dá controle granular sobre a aparência de documentos Word diretamente a partir do código C#.

---

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Obter separador de estilo de parágrafo em documento Word](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [Criar documento Word com cabeçalho e rodapé usando Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Adicionar números de página ao rodapé de um documento Word usando Aspose.Words para .NET](/words/english/net/working-with-headers-and-footers/add-page-numbers/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}