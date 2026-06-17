---
category: general
date: 2026-04-24
description: Salvar documento como txt e converter Word para LaTeX com Aspose.Words.
  Aprenda como exportar equações matemáticas do Word para LaTeX rapidamente.
draft: false
keywords:
- save document as txt
- convert word to latex
- convert word equations to latex
- export word math latex
language: pt
og_description: Salvar documento como txt e converter equações do Word para LaTeX
  usando C#. Guia completo passo a passo com código.
og_title: Salvar documento como TXT – Exportar matemática do Word para LaTeX
tags:
- Aspose.Words
- C#
- LaTeX
title: Salvar documento como TXT – Exportar matemática do Word para LaTeX em C#
url: /pt/net/programming-with-officemath/save-document-as-txt-export-word-math-to-latex-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Salvar Documento como TXT – Exportar Matemática do Word para LaTeX em C#

Já precisou **save document as txt** enquanto mantém suas equações sofisticadas intactas? Você não é o único. O recurso interno “Save as plain text” do Word descarta Office Math, deixando você com um texto ilegível. E se você pudesse manter essas equações, mas em LaTeX limpo?  

Neste tutorial, vamos percorrer os passos exatos para **convert Word to LaTeX**‑ready text usando Aspose.Words for .NET. Ao final, você terá um arquivo `.txt` onde cada equação é representada como marcação LaTeX adequada, pronta para ser inserida em um artigo ou em um arquivo markdown. Sem conversores externos, sem copiar‑colar manual—apenas algumas linhas de C#.

## O que você aprenderá

- Como carregar um arquivo `.docx` com Aspose.Words.
- Configurar `TxtSaveOptions` para que Office Math seja exportado como LaTeX.
- Salvar o resultado em um arquivo de texto simples que você pode abrir em qualquer editor.
- Tratamento de casos extremos para equações inline vs. display, e uma dica rápida para processamento em lote de vários documentos.

### Pré-requisitos

- .NET 6.0 ou superior (o código também funciona com .NET Framework 4.6+).
- Pacote NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`).
- Um documento Word que contenha ao menos uma equação (objeto Office Math).

---

## Etapa 1: Instalar Aspose.Words e Configurar o Projeto

Primeiro, adicione a biblioteca ao seu projeto. Abra um terminal na pasta da sua solução e execute:

```bash
dotnet add package Aspose.Words
```

> **Dica profissional:** Se você está usando o Visual Studio, a interface do NuGet Package Manager funciona igualmente—pesquise por “Aspose.Words” e clique em Install.

Agora crie um novo aplicativo console (ou insira o código em um existente). As diretivas `using` que você precisará são:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

Essas trazem a classe `Document` e o tipo `TxtSaveOptions` para o escopo.

## Etapa 2: Carregar o Documento Fonte

Precisamos apontar o Aspose.Words para o arquivo Word que contém as equações. Substitua `YOUR_DIRECTORY/input.docx` pelo caminho real na sua máquina.

```csharp
// Load the source .docx file
Document doc = new Document(@"C:\MyDocs\input.docx");
```

> **Por que isso importa:** Carregar o documento dá ao Aspose.Words acesso total aos objetos internos de Office Math, que de outra forma são invisíveis para um exportador de texto simples.

## Etapa 3: Configurar TxtSaveOptions para Exportação LaTeX

A mágica acontece no objeto `TxtSaveOptions`. Definindo `OfficeMathExportMode` como `LaTeX`, cada equação é transformada em seu equivalente LaTeX.

```csharp
// Configure save options to export Office Math as LaTeX
TxtSaveOptions txtOptions = new TxtSaveOptions
{
    // Export all Office Math objects as LaTeX code
    OfficeMathExportMode = OfficeMathExportMode.LaTeX,

    // Optional: keep line breaks similar to the original layout
    PreserveTableLayout = true
};
```

> **E se você precisar de MathML?** Altere `OfficeMathExportMode` para `MathML`. A mesma API suporta vários formatos de saída.

## Etapa 4: Salvar o Documento como Texto Simples

Agora gravamos o arquivo. O `Math.txt` resultante conterá texto comum mais fragmentos LaTeX para cada equação.

```csharp
// Save the document as a .txt file with LaTeX equations
doc.Save(@"C:\MyDocs\Math.txt", txtOptions);
Console.WriteLine("Document saved as txt with LaTeX equations.");
```

Executar o programa produz um arquivo que se parece com isto:

```
This is a simple paragraph.

Here is an inline equation: $E = mc^2$

And a displayed equation:
\[
\int_{0}^{\infty} e^{-x} \, dx = 1
\]
```

Observe como a equação inline usa `$…$` enquanto a equação display é envolvida por `\[` e `\]`. Essa é a convenção padrão do LaTeX, e o Aspose.Words faz isso automaticamente.

## Etapa 5: Verificar a Saída (Opcional)

Se quiser confirmar que o LaTeX está válido, você pode alimentar o `.txt` em um compilador LaTeX como `pdflatex` ou em um renderizador online como Overleaf. O texto deve compilar sem erros, e as equações aparecerão exatamente como no Word.

```bash
pdflatex Math.txt
```

Se receber “Undefined control sequence”, certifique-se de que os pacotes LaTeX necessários (por exemplo, `amsmath`) estejam incluídos no seu preâmbulo ao inserir o texto em um documento LaTeX maior.

## Lidando com Variações Comuns

### Convertendo Vários Arquivos em uma Pasta

```csharp
string[] files = Directory.GetFiles(@"C:\MyDocs\", "*.docx");
foreach (var file in files)
{
    Document d = new Document(file);
    d.Save(Path.ChangeExtension(file, ".txt"), txtOptions);
}
Console.WriteLine("Batch conversion complete.");
```

### Lidando com Equações Inline vs. Display

O Aspose.Words detecta automaticamente o tipo de equação com base em seu layout no Word. Se precisar forçar um estilo específico, você pode pós‑processar a saída:

```csharp
string txt = File.ReadAllText(@"C:\MyDocs\Math.txt");
txt = txt.Replace("$", "\\(").Replace("$", "\\)"); // forces inline math delimiters
File.WriteAllText(@"C:\MyDocs\Math_fixed.txt", txt);
```

### Exportando para Outros Formatos

Se LaTeX não for seu objetivo, basta mudar o modo de exportação:

```csharp
txtOptions.OfficeMathExportMode = OfficeMathExportMode.MathML; // for MathML
```

Ou use `HtmlSaveOptions` se preferir MathML embutido em HTML.

---

## Exemplo Completo Funcionando

Abaixo está o programa completo, pronto‑para‑executar. Copie‑e‑cole em `Program.cs` de um projeto console .NET.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

namespace WordToLatexTxt
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the source document
            Document doc = new Document(@"C:\MyDocs\input.docx");

            // 2️⃣ Set up save options to export Office Math as LaTeX
            TxtSaveOptions saveOptions = new TxtSaveOptions
            {
                OfficeMathExportMode = OfficeMathExportMode.LaTeX,
                PreserveTableLayout = true
            };

            // 3️⃣ Save as plain‑text with LaTeX equations
            string outputPath = @"C:\MyDocs\Math.txt";
            doc.Save(outputPath, saveOptions);

            Console.WriteLine($"✅ Saved document as txt at: {outputPath}");
            Console.WriteLine("Open the file to see LaTeX‑formatted equations.");
        }
    }
}
```

Execute o programa (`dotnet run`), abra `Math.txt` e você verá o conteúdo do Word com as equações LaTeX intactas.

---

## Perguntas Frequentes

**Q: Isso funciona com arquivos .doc antigos?**  
A: Sim—Aspose.Words pode abrir arquivos `.doc` legados, mas equações complexas podem ser armazenadas como imagens. Nesse caso o exportador recorre a um comentário placeholder.

**Q: E se uma equação contiver símbolos personalizados?**  
A: Aspose.Words mapeia a maioria dos símbolos Office Math para comandos LaTeX padrão. Para símbolos realmente personalizados, pode ser necessário editar manualmente o LaTeX gerado.

**Q: A saída é codificada em UTF‑8?**  
A: Por padrão, `TxtSaveOptions` grava em UTF‑8, que é seguro para a maioria dos idiomas e símbolos.

## Conclusão

Agora você sabe como **save document as txt** preservando cada equação como marcação LaTeX limpa. Essa abordagem permite **convert Word to LaTeX** sem ferramentas de terceiros, e escala de um único arquivo a pastas inteiras. Em seguida, você pode explorar **convert word equations to LaTeX** para processamento em lote, ou mergulhar em **export word math latex** para pipelines HTML ou Markdown.

Sinta-se à vontade para experimentar—troque `OfficeMathExportMode` por MathML, ajuste o tratamento de quebras de linha, ou integre este trecho em um fluxo de trabalho maior de geração de documentos. Boa codificação, e que suas equações sempre sejam renderizadas perfeitamente!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}