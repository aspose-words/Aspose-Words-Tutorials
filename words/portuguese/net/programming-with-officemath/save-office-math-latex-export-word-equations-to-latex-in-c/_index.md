---
category: general
date: 2026-04-21
description: Salve rapidamente o LaTeX de matemática do Office usando Aspose.Words
  – também aprenda como salvar texto simples do Word e exportar as equações do Word
  em LaTeX de uma só vez.
draft: false
keywords:
- save office math latex
- save word plain text
- export word equations latex
- convert word math latex
- convert word equations mathml
language: pt
og_description: salve o LaTeX de matemática do Office instantaneamente; aprenda a
  exportar equações do Word em LaTeX e converter matemática do Word para LaTeX com
  Aspose.Words em C#.
og_title: salvar office math latex – Exportar equações do Word para LaTeX
tags:
- Aspose.Words
- C#
- LaTeX
title: Salvar Office Math LaTeX – Exportar equações do Word para LaTeX em C#
url: /pt/net/programming-with-officemath/save-office-math-latex-export-word-equations-to-latex-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# save office math latex – Exportar equações do Word para LaTeX com Aspose.Words

Já precisou **save office math latex** de um arquivo `.docx` mas não sabia por onde começar? Você não está sozinho, e a boa notícia é que a solução é bem simples. Neste guia vamos percorrer os passos exatos para exportar equações do Word em latex (e até MathML) usando Aspose.Words para .NET, tudo enquanto mostramos como **save word plain text** junto com a matemática.

Vamos cobrir tudo que você pode se perguntar: por que escolher LaTeX em vez de outros formatos, como configurar o `TxtSaveOptions` e o que fazer se precisar **convert word math latex** para outra representação. Ao final você terá um trecho de código executável que recebe um documento Word com objetos Office Math e gera um arquivo `.txt` limpo contendo equações em LaTeX (ou MathML). Sem ferramentas externas, sem copiar‑colar manual—apenas código C# limpo que você pode inserir em qualquer projeto.

## Pré-requisitos

- **Aspose.Words for .NET** (v23.10 ou posterior). O pacote NuGet é `Aspose.Words`.
- Um ambiente de desenvolvimento .NET (Visual Studio, Rider ou VS Code com a extensão C#).
- Um arquivo Word (`.docx`) que contenha ao menos uma equação criada com o editor Office Math.
- Familiaridade básica com a sintaxe C#—nada sofisticado, apenas as declarações `using` habituais.

Se você já tem esses itens marcados, ótimo—vamos mergulhar.

## Passo 1 – Configurar as opções **save office math latex**

A primeira coisa que você precisa fazer é dizer ao Aspose.Words como deseja que o conteúdo matemático seja renderizado. A classe `TxtSaveOptions` possui a propriedade `OfficeMathExportMode` que aceita três valores: `LaTeX`, `MathML` ou `Text`. Para nosso objetivo principal, escolheremos `LaTeX`.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Configure TXT save options to export equations as LaTeX
TxtSaveOptions txtOptions = new TxtSaveOptions
{
    // This line makes the library output LaTeX for every Office Math object
    OfficeMathExportMode = OfficeMathExportMode.LaTeX
    // You could also use OfficeMathExportMode.MathML or .Text here
};
```

**Por que isso importa:** Quando você define `OfficeMathExportMode` como `LaTeX`, cada equação é transformada em seu código LaTeX bruto. Esse código pode ser compilado posteriormente com qualquer engine LaTeX, proporcionando tipografia pixel‑perfect sem a necessidade de reescrever as fórmulas.

> **Dica profissional:** Se você precisar **convert word equations mathml**, basta trocar o valor do enum para `OfficeMathExportMode.MathML`. O restante do código permanece o mesmo.

## Passo 2 – Carregar o documento Word (o cenário **save word plain text**)

Em seguida, carregamos o `.docx` de origem. Esta etapa é idêntica, seja você interessado apenas na extração de texto puro ou também quiser as equações em LaTeX.

```csharp
// Load the document that contains Office Math objects
Document doc = new Document(@"C:\MyDocs\input.docx");

// Optional: verify that the document actually has equations
bool hasMath = doc.GetChildNodes(NodeType.OfficeMath, true).Count > 0;
if (!hasMath)
{
    Console.WriteLine("Warning: No Office Math objects found in the document.");
}
```

**O que está acontecendo aqui?** O construtor `Document` lê o arquivo para a memória. A verificação rápida com `GetChildNodes` ajuda a detectar um caso comum—tentar exportar LaTeX de um arquivo que não contém equações. É uma pequena salvaguarda que evita um resultado vazio e confuso mais tarde.

## Passo 3 – **save office math latex** para um arquivo de texto simples

Agora finalmente gravamos o arquivo. O método `Save` respeita o `TxtSaveOptions` que configuramos anteriormente, então o `.txt` resultante conterá tanto o texto normal quanto trechos LaTeX para cada equação.

```csharp
// Define the output path
string outputPath = @"C:\MyDocs\Equations.txt";

// Save the document as plain text, with LaTeX equations embedded
doc.Save(outputPath, txtOptions);

Console.WriteLine($"Document saved successfully to {outputPath}");
```

Ao abrir `Equations.txt` você verá algo como:

```
This is a sample paragraph.

\begin{equation}
E = mc^2
\end{equation}

Another paragraph follows.
```

Os blocos LaTeX são automaticamente envoltos em `\begin{equation}` … `\end{equation}`, o que os deixa prontos para inclusão em qualquer documento LaTeX.

## Passo 4 – Alternativa: **convert word equations mathml** em vez de LaTeX

Se sua cadeia de ferramentas downstream preferir MathML (por exemplo, uma página web que renderiza equações com MathJax), basta mudar o modo de exportação:

```csharp
txtOptions.OfficeMathExportMode = OfficeMathExportMode.MathML;
doc.Save(@"C:\MyDocs\EquationsMathML.txt", txtOptions);
```

A saída agora conterá tags MathML no estilo XML, como:

```xml
<math xmlns="http://www.w3.org/1998/Math/MathML">
  <mi>E</mi>
  <mo>=</mo>
  <mi>m</mi>
  <msup><mi>c</mi><mn>2</mn></msup>
</math>
```

Essa é a maneira rápida de **convert word equations mathml** sem escrever um analisador personalizado.

## Passo 5 – Bônus: **save word plain text** mantendo as equações separadas

Às vezes você quer uma versão limpa do texto do documento *sem* nenhum LaTeX ou MathML embutido. Você pode conseguir isso mudando o modo de exportação para `Text` e executando uma segunda passagem de salvamento:

```csharp
// Export pure plain text (no math markup)
txtOptions.OfficeMathExportMode = OfficeMathExportMode.Text;
doc.Save(@"C:\MyDocs\PlainDocument.txt", txtOptions);
```

Agora você tem três arquivos lado a lado:

| File                         | Contents                               |
|------------------------------|----------------------------------------|
| `Equations.txt`              | Texto simples **+** equações LaTeX       |
| `EquationsMathML.txt`        | Texto simples **+** equações MathML       |
| `PlainDocument.txt`          | Texto puro, equações removidas          |

Esse padrão é útil quando você precisa alimentar o texto simples em um índice de busca enquanto ainda preserva a matemática original para publicação acadêmica.

## Exemplo Completo (Pronto para Copiar‑Colar)

Abaixo está o programa completo que você pode compilar e executar como está. Ele demonstra **save office math latex**, **export word equations latex**, **convert word math latex**, e **save word plain text**—tudo em um script organizado.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Configure TXT save options for LaTeX export
        TxtSaveOptions txtOptions = new TxtSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };

        // 2️⃣ Load the source Word document
        string inputPath = @"C:\MyDocs\input.docx";
        Document doc = new Document(inputPath);

        // Quick sanity check for equations
        if (doc.GetChildNodes(NodeType.OfficeMath, true).Count == 0)
        {
            Console.WriteLine("No equations found – proceeding with plain‑text export only.");
        }

        // 3️⃣ Save with LaTeX equations embedded
        string latexPath = @"C:\MyDocs\Equations.txt";
        doc.Save(latexPath, txtOptions);
        Console.WriteLine($"LaTeX export saved to {latexPath}");

        // 4️⃣ Switch to MathML and save (optional)
        txtOptions.OfficeMathExportMode = OfficeMathExportMode.MathML;
        string mathmlPath = @"C:\MyDocs\EquationsMathML.txt";
        doc.Save(mathmlPath, txtOptions);
        Console.WriteLine($"MathML export saved to {mathmlPath}");

        // 5️⃣ Finally, pure plain‑text export (no math markup)
        txtOptions.OfficeMathExportMode = OfficeMathExportMode.Text;
        string plainPath = @"C:\MyDocs\PlainDocument.txt";
        doc.Save(plainPath, txtOptions);
        Console.WriteLine($"Plain‑text export saved to {plainPath}");
    }
}
```

**Resultado esperado:** Após a execução, você encontrará três arquivos de texto em `C:\MyDocs`. Abra `Equations.txt` e verá blocos LaTeX; `EquationsMathML.txt` conterá MathML; `PlainDocument.txt` estará livre de qualquer marcação de equação.

## Perguntas Comuns & Casos de Borda

- **E se eu precisar de LaTeX apenas para um subconjunto de equações?**  
  Use a API de nós `OfficeMath` para iterar sobre cada equação, exportá‑la manualmente com `MathConverter` e substituir o texto placeholder onde desejar. Essa abordagem oferece controle granular, mas adiciona algumas linhas extras de código.

- **Isso funciona com .NET Core / .NET 5+?**  
  Absolutamente. Aspose.Words é multiplataforma, então o mesmo código roda no Windows, Linux e macOS, desde que a versão do runtime corresponda aos requisitos da biblioteca.

- **Posso mudar o wrapper LaTeX (`\begin{equation}`) para outra coisa?**  
  Sim. Defina `txtOptions.OfficeMathExportMode = OfficeMathExportMode.LaTeX` e então modifique `txtOptions.MathExportSettings` (disponível em versões mais recentes) para personalizar os delimitadores.

- **Preocupações de desempenho para documentos enormes?**  
  A biblioteca faz streaming da saída, então o uso de memória permanece modesto. Contudo

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}