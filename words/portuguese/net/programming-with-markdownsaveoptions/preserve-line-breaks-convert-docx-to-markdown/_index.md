---
category: general
date: 2026-02-13
description: "Preserve quebras de linha ao converter DOCX para markdown.  \nAprenda
  como salvar Word como markdown, exportar parágrafos vazios e manter a formatação
  intacta."
draft: false
keywords:
- preserve line breaks
- convert docx to markdown
- save word as markdown
- how to export empty
- how to preserve breaks
language: pt
og_description: "Preserve quebras de linha ao converter DOCX para markdown.  \nEste
  guia mostra como salvar o Word como markdown e exportar parágrafos vazios corretamente."
og_title: 'Preservar quebras de linha: converter DOCX para Markdown'
tags:
- Aspose.Words
- C#
- Markdown
title: 'Preservar Quebras de Linha: Converter DOCX para Markdown'
url: /pt/net/programming-with-markdownsaveoptions/preserve-line-breaks-convert-docx-to-markdown/
---

need to keep them.

Now produce final output.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Preservar Quebras de Linha: Converter DOCX para Markdown

Já precisou **preservar quebras de linha** ao converter um arquivo DOCX para Markdown? É um problema comum—seu belo documento Word acaba como um bloco de texto, e aquelas linhas em branco intencionais desaparecem. A boa notícia? Você pode manter cada quebra de linha, até mesmo os parágrafos vazios, com algumas configurações simples.

Neste tutorial vamos percorrer todo o processo de **salvar Word como Markdown**, cobrindo tudo, desde o carregamento do documento fonte até a configuração do modo de exportação correto. Ao final, você saberá *como exportar parágrafos vazios*, *como preservar quebras* em layouts complexos, e terá um exemplo de código completo, pronto para copiar e colar. Sem peças faltando, sem caminhos “consulte a documentação” sem saída.

## O que você aprenderá

- Por que preservar quebras de linha importa para a legibilidade e ferramentas subsequentes.  
- Como **converter DOCX para markdown** usando Aspose.Words for .NET.  
- Quais configurações de `MarkdownSaveOptions` controlam o tratamento de parágrafos vazios.  
- Dicas práticas para lidar com casos extremos como tabelas, listas e blocos de código.  
- Um exemplo completo e executável que você pode inserir em qualquer projeto C# hoje.

### Pré-requisitos

- .NET 6+ (ou .NET Framework 4.7.2+) instalado.  
- Uma licença para **Aspose.Words for .NET** (a versão de avaliação gratuita funciona para esta demonstração).  
- Familiaridade básica com C# e o conceito de Markdown.  

Se você já tem isso pronto, vamos mergulhar.

![Diagrama de preservação de quebras de linha](preserve-line-breaks.png "Diagrama ilustrando como parágrafos vazios se tornam quebras de linha no Markdown")

## Preservar Quebras de Linha – Por que é Importante

Quando um documento Word contém linhas em branco intencionais—pense nelas como separadores visuais entre seções—essas linhas em branco costumam ser removidas durante a conversão. O Markdown, por design, trata uma única quebra de linha como continuação do mesmo parágrafo, portanto uma linha vazia precisa ser representada explicitamente. Se você não **preservar quebras de linha**, sua saída pode ficar apertada, e analisadores subsequentes (como geradores de sites estáticos) podem mesclar seções inadvertidamente.

Manter essas quebras não é apenas uma questão estética; também ajuda ferramentas que dependem dos limites de parágrafos para coisas como posicionamento de notas de rodapé, estilos personalizados ou até extração de títulos amigáveis ao SEO. Em resumo, uma conversão fiel respeita a intenção do autor.

## Converter DOCX para Markdown com Aspose.Words

O Aspose.Words oferece controle detalhado sobre o processo de conversão. A classe principal é `MarkdownSaveOptions`, que permite decidir como os parágrafos vazios são exportados. A seguir, definiremos `EmptyParagraphExportMode` como `EmptyLine`, um modo que traduz um parágrafo Word em branco para uma linha vazia em Markdown.

### Implementação Passo a Passo

### 1️⃣ Carregar o Documento Fonte

Primeiro, aponte a biblioteca para o seu arquivo `.docx`. O construtor `Document` faz todo o trabalho pesado—analisando estilos, imagens e informações de layout.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Adjust the path to match your environment
string inputPath  = @"C:\Docs\MyReport.docx";
Document doc = new Document(inputPath);
```

> **Por que isso importa:** Carregar o documento antecipadamente lhe dá acesso à sua estrutura interna, permitindo ajustar opções com base no que você descobrir (por exemplo, detectar se o arquivo realmente contém parágrafos vazios).

### 2️⃣ Configurar Opções de Salvamento Markdown

Aqui é onde respondemos à pergunta **“como exportar vazios”** parágrafos. O enum `EmptyParagraphExportMode` oferece três opções:

| Modo | Resultado em Markdown |
|------|------------------------|
| `EmptyLine` | Insere uma linha em branco (`\n\n`). |
| `PreserveLineBreaks` | Converte cada quebra de linha em uma quebra rígida (`  \n`). |
| `None` | Omiti o parágrafo vazio completamente. |

Para a maioria dos cenários onde você simplesmente quer um espaço visual, `EmptyLine` resolve.

```csharp
MarkdownSaveOptions mdOpts = new MarkdownSaveOptions
{
    // Export empty paragraphs as a single empty line.
    // This is the most intuitive way to keep visual spacing.
    EmptyParagraphExportMode = MarkdownEmptyParagraphExportMode.EmptyLine,

    // Optional: keep original line breaks inside paragraphs.
    // Uncomment if you need finer control.
    // PreserveLineBreaks = true
};
```

> **Dica profissional:** Se você também precisar manter quebras de linha manuais (Shift + Enter no Word), defina `PreserveLineBreaks = true`. Dessa forma, tanto os parágrafos vazios quanto as quebras suaves sobrevivem à ida e volta.

### 3️⃣ Salvar o Documento como Markdown

Agora gravamos o arquivo de saída. Você pode escolher qualquer pasta que desejar; apenas certifique-se de que a extensão seja `.md`.

```csharp
string outputPath = @"C:\Docs\MyReport.md";
doc.Save(outputPath, mdOpts);
Console.WriteLine($"✅ Conversion complete! Markdown saved to {outputPath}");
```

Esse é todo o pipeline. Execute o programa, abra o arquivo `.md` e você verá linhas em branco exatamente onde estavam no arquivo Word original.

### Exemplo Completo em Funcionamento

Juntando tudo, aqui está um aplicativo de console autônomo que você pode compilar instantaneamente:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the source DOCX
        string inputPath = @"C:\Docs\input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Set up Markdown options to preserve empty paragraphs
        MarkdownSaveOptions mdOpts = new MarkdownSaveOptions
        {
            EmptyParagraphExportMode = MarkdownEmptyParagraphExportMode.EmptyLine,
            // PreserveLineBreaks = true   // Uncomment if you need soft line breaks
        };

        // 3️⃣ Save as Markdown
        string outputPath = @"C:\Docs\WithEmptyParas.md";
        doc.Save(outputPath, mdOpts);

        Console.WriteLine($"✅ Document converted! Check: {outputPath}");
    }
}
```

**Saída esperada:** Abra `WithEmptyParas.md` em qualquer editor. Você notará que cada linha em branco de `input.docx` aparece como uma linha vazia no arquivo Markdown, preservando a separação visual que você projetou.

## Salvar Word como Markdown – Cenários Avançados

### Manipulação de Tabelas e Listas

As tabelas no Word se tornam tabelas Markdown automaticamente, mas linhas vazias podem ser complicadas. Se uma linha da tabela contém apenas uma célula vazia, o Aspose.Words a trata como um parágrafo vazio. O `EmptyParagraphExportMode` ainda se aplica, então você obterá uma linha em branco **fora** da tabela—não dentro dela. Para manter um espaço visual *dentro* da tabela, insira um espaço não‑quebrável (`&nbsp;`) na célula.

```csharp
// Example: Adding a placeholder to an empty cell
Table table = doc.GetChild(NodeType.Table, 0, true) as Table;
Cell emptyCell = table.Rows[2].Cells[1];
emptyCell.AppendChild(new Paragraph(doc));
emptyCell.FirstParagraph.AppendChild(new Run(doc, "\u00A0")); // non‑breaking space
```

### Blocos de Código e Texto Pré‑Formatado

Se o seu DOCX contém código pré‑formatado, o Aspose.Words o envolverá em três crases. Linhas vazias dentro de um bloco de código são preservadas automaticamente, independentemente do `EmptyParagraphExportMode`. Contudo, se você notar linhas em branco ausentes, verifique se o estilo de parágrafo original no Word está definido como “No Spacing”. Dessa forma, a biblioteca trata cada linha como um parágrafo separado.

### Quando Usar `PreserveLineBreaks` Em vez Disso

Às vezes você precisa de uma quebra de linha rígida (`  `) em vez de um parágrafo totalmente vazio. Por exemplo, poesias ou blocos de endereço frequentemente dependem de quebras de linha simples. Altere a opção:

```csharp
mdOpts.PreserveLineBreaks = true;   // Turns soft breaks into Markdown hard breaks
mdOpts.EmptyParagraphExportMode = MarkdownEmptyParagraphExportMode.None; // optional
```

Agora cada `Shift+Enter` no Word se torna `  \n` no Markdown, enquanto parágrafos realmente vazios desaparecem (a menos que você também mantenha `EmptyLine`).

## Como Exportar Parágrafos Vazios Corretamente

A resposta curta: defina `EmptyParagraphExportMode = MarkdownEmptyParagraphExportMode.EmptyLine`. A resposta longa envolve entender *por que* isso funciona.

- **EmptyParagraphExportMode** informa ao serializador *o que* fazer com um parágrafo que não contém runs (texto).  
- **EmptyLine** insere uma dupla quebra de linha, que o Markdown interpreta como separador de parágrafos.  
- Outros modos ou colapsam o parágrafo (`None`) ou tratam quebras de linha como quebras rígidas (`PreserveLineBreaks`).

Se você esquecer essa configuração, o comportamento padrão é `None`, e todas as linhas em branco desaparecem—exatamente o problema que estamos tentando resolver.

## Como Preservar Quebras em Documentos Complexos

Documentos complexos frequentemente misturam títulos, imagens e notas de rodapé. Aqui está uma lista de verificação para garantir que você não perca nenhuma quebra de linha:

| Item da Lista de Verificação | Por que é Importante |
|------------------------------|----------------------|
| **Validar parágrafos vazios** | Use `doc.GetChildNodes(NodeType.Paragraph, true)` para contar vazios antes da conversão. |
| **Habilitar `PreserveLineBreaks` para poesia** | Garante que quebras de linha simples sobrevivam. |
| **Verificar legendas de imagens** | Legendas são parágrafos separados; precisam do mesmo modo de exportação. |
| **Executar um diff pós‑conversão** | Compare o texto original (extraído via `doc.GetText()`) com a saída Markdown. |
| **Testar com um visualizador de Markdown** | Alguns renderizadores tratam múltiplas linhas vazias de forma diferente; verifique o resultado visual. |

### Código de Validação de Exemplo

```csharp
// Count empty paragraphs before saving
int emptyCount = 0;
NodeCollection paragraphs = doc.GetChildNodes(NodeType.Paragraph, true);
foreach (Paragraph p in paragraphs)
{
    if (p.GetText().Trim().Length == 0)
        emptyCount++;
}
Console.WriteLine($"Document contains {emptyCount} empty paragraph(s).");
```

Executar isso antes da etapa de salvamento lhe dá confiança de que a conversão lidará com o número exato de quebras de linha que você espera.

## Armadilhas Comuns e Dicas Profissionais

Pitfall:

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}