---
category: general
date: 2026-08-04
description: Alterar o separador de nota de rodapé em C# usando Aspose.Words – aprenda
  como editar o separador de nota de rodapé e mudar o separador de nota de fim em
  documentos Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- change footnote separator
- edit footnote separator
- how to change footnote separator
- change endnote separator
language: pt
lastmod: 2026-08-04
og_description: Altere o separador de nota de rodapé em C# com Aspose.Words. Este
  guia mostra como editar o separador de nota de rodapé, personalizar o separador
  de nota de fim e salvar o documento atualizado.
og_image_alt: Screenshot showing the changed footnote separator in a Word document
og_title: Alterar separador de nota de rodapé em C# – guia completo do Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Change footnote separator in C# using Aspose.Words – learn how to edit
    footnote separator and change endnote separator in Word documents.
  headline: Change footnote separator in C# using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Footnotes
- Document processing
title: Alterar separador de nota de rodapé em C# usando Aspose.Words
url: /pt/net/working-with-footnote-and-endnote/change-footnote-separator-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Alterar separador de nota de rodapé em C# usando Aspose.Words

Se você precisa **alterar o separador de nota de rodapé** em um documento Word, este tutorial orienta passo a passo usando o Aspose.Words para .NET. Seja para substituir a linha padrão por um símbolo ou aplicar um estilo diferente aos separadores de nota final, o código abaixo cobre todo o fluxo de trabalho.

Você também aprenderá a **editar o separador de nota de rodapé** e a operação relacionada **alterar separador de nota final**, de modo que o mesmo documento possa ter estilo consistente para notas de rodapé e notas finais. Nenhuma ferramenta externa é necessária — apenas algumas linhas de C#.

## O que você vai conseguir

Ao final deste guia você será capaz de:

* Carregar um arquivo *.docx* existente que contém notas de rodapé e notas finais.  
* Acessar os nós separadores para notas de rodapé, continuações de notas de rodapé e notas finais.  
* Substituir o caractere separador (por exemplo, mudar a linha padrão para um asterisco).  
* Salvar o documento modificado sem perder nenhum outro conteúdo.  

O tutorial pressupõe que você tem conhecimento básico de C# e já instalou o pacote **Aspose.Words** via NuGet (versão 24.9 ou superior).  

---

## Pré‑requisitos

| Requisito | Motivo |
|-----------|--------|
| .NET 6.0+ ou .NET Framework 4.7.2+ | Runtime necessário para Aspose.Words |
| Biblioteca Aspose.Words for .NET | Fornece as APIs `Document` e `FootnoteOptions` |
| Um arquivo Word de entrada (`input.docx`) com ao menos uma nota de rodapé ou nota final | Demonstra a alteração do separador |

Você pode adicionar o Aspose.Words ao seu projeto com o seguinte comando CLI:

```bash
dotnet add package Aspose.Words --version 24.9.0
```

---

## Etapa 1: Carregar o documento que contém notas de rodapé

A primeira operação é ler o arquivo fonte em um objeto `Document`. Esse objeto representa todo o arquivo Word na memória e permite acesso a todos os seus nós.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

// Load the .docx file that contains footnotes and endnotes.
Document document = new Document(@"C:\Docs\input.docx");
```

**Por que isso importa:** Carregar o documento é o ponto de entrada para qualquer manipulação. Se o arquivo não for encontrado, o Aspose.Words lança uma `FileNotFoundException`, portanto verifique se o caminho está correto antes de prosseguir.

---

## Etapa 2: Acessar os nós separadores de nota de rodapé e nota final

`Document.FootnoteOptions` expõe três nós separadores:

* `Separator` – a linha que aparece após a coleção de notas de rodapé na primeira página.  
* `ContinuationSeparator` – a linha usada quando as notas de rodapé continuam na página seguinte.  
* `EndnoteSeparator` – a linha que separa o texto principal da lista de notas finais.

Você obtém esses nós como objetos genéricos `Node`, e então faz cast para `Run` para modificar o texto.

```csharp
// Retrieve the three separator nodes.
Node footnoteSeparator = document.FootnoteOptions.Separator;
Node footnoteContinuation = document.FootnoteOptions.ContinuationSeparator;
Node endnoteSeparator = document.FootnoteOptions.EndnoteSeparator;
```

**Por que isso importa:** Esses nós são os únicos lugares onde o caractere visual do separador está armazenado. Alterar qualquer outro nó (por exemplo, um parágrafo comum) não afetará a formatação das notas de rodapé.

---

## Etapa 3: Alterar o caractere separador da nota de rodapé

A necessidade mais comum é substituir a linha padrão por um símbolo, como um asterisco (`*`). Como o separador é armazenado como um `Run`, você pode modificar com segurança sua propriedade `Text`.

```csharp
// Change the primary footnote separator to an asterisk.
if (footnoteSeparator is Run footnoteRun)
{
    footnoteRun.Text = "*";
}

// Optionally, change the continuation separator as well.
if (footnoteContinuation is Run continuationRun)
{
    continuationRun.Text = "*";
}
```

**Por que isso importa:** Editar diretamente `Run.Text` atualiza a representação visual no documento final sem afetar outro conteúdo da nota de rodapé. O mesmo padrão pode ser usado para aplicar qualquer string, inclusive símbolos Unicode.

---

## Etapa 4: Alterar o separador de nota final (opcional)

Se também precisar **alterar o separador de nota final**, o processo espelha a alteração da nota de rodapé. Substitua o texto de `endnoteSeparator` pelo caractere desejado.

```csharp
// Change the endnote separator to a dash.
if (endnoteSeparator is Run endnoteRun)
{
    endnoteRun.Text = "-";
}
```

**Por que isso importa:** Notas finais costumam ter estilo diferente das notas de rodapé. Fornecer um separador separado permite manter a consistência visual com as diretrizes de design do seu documento.

---

## Etapa 5: Salvar o documento modificado

Após todas as modificações, persista as alterações usando `Document.Save`. Você pode sobrescrever o arquivo original ou gravar em um novo local.

```csharp
// Save the updated document.
document.Save(@"C:\Docs\ModifiedSeparators.docx");
```

**Por que isso importa:** `Save` grava a representação em memória no disco, preservando todos os demais elementos (estilos, imagens, tabelas) inalterados.

---

## Exemplo completo e executável

Juntando todas as partes, aqui está um aplicativo console autocontido que demonstra todo o fluxo de trabalho:

```csharp
using System;
using Aspose.Words;

namespace FootnoteSeparatorDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source document.
            string inputPath = @"C:\Docs\input.docx";
            Document doc = new Document(inputPath);

            // 2️⃣ Access separator nodes.
            Node footnoteSep = doc.FootnoteOptions.Separator;
            Node footnoteCont = doc.FootnoteOptions.ContinuationSeparator;
            Node endnoteSep = doc.FootnoteOptions.EndnoteSeparator;

            // 3️⃣ Change footnote separator to an asterisk.
            if (footnoteSep is Run footnoteRun)
                footnoteRun.Text = "*";

            // Optional: also change the continuation separator.
            if (footnoteCont is Run contRun)
                contRun.Text = "*";

            // 4️⃣ Change endnote separator to a dash.
            if (endnoteSep is Run endnoteRun)
                endnoteRun.Text = "-";

            // 5️⃣ Save the result.
            string outputPath = @"C:\Docs\ModifiedSeparators.docx";
            doc.Save(outputPath);

            Console.WriteLine("Document saved to " + outputPath);
        }
    }
}
```

**Resultado esperado:** Abra *ModifiedSeparators.docx* no Microsoft Word. A linha separadora da nota de rodapé na parte inferior da primeira página de notas agora será um único asterisco (`*`). Se o documento contiver notas finais, a linha que separa o texto principal da lista de notas finais aparecerá como um traço (`-`). Todo o restante do conteúdo (texto, imagens, tabelas) permanece intacto.

---

## Perguntas frequentes & tratamento de casos especiais

| Pergunta | Resposta |
|----------|----------|
| **E se o documento não tiver notas de rodapé?** | `FootnoteOptions.Separator` ainda retorna um nó `Run`, mas seu texto pode estar vazio. O código verifica o tipo do nó com segurança antes de modificá‑lo. |
| **Posso usar uma string com vários caracteres (ex.: "***")?** | Sim. A propriedade `Run.Text` aceita qualquer string, incluindo caracteres Unicode. |
| **A alteração do separador afeta a numeração das notas existentes?** | Não. O separador é independente do esquema de numeração. |
| **Preciso descartar o objeto `Document`?** | `Document` implementa `IDisposable` implicitamente via `Node`. Em um aplicativo console de curta duração é opcional, mas em serviços de longa execução você pode envolvê‑lo em um bloco `using`. |
| **Como isso funciona no .NET Core vs .NET Framework?** | A API é idêntica entre os runtimes; apenas a versão do framework alvo importa (deve ser suportada pelo pacote Aspose.Words). |

**Dica profissional:** Se precisar aplicar separadores diferentes para seções distintas, você pode iterar por `doc.GetChildNodes(NodeType.Footnote, true)` e ajustar individualmente a propriedade `Separator` de cada nota. Isso é mais avançado, mas útil para documentos complexos.

---

## Conclusão

Agora você sabe como **alterar o separador de nota de rodapé** e **alterar o separador de nota final** em um arquivo Word usando Aspose.Words para C#. O guia abordou carregamento do documento, acesso aos nós separadores relevantes, modificação do texto e salvamento do resultado — tudo em um único programa autocontido.

A partir daqui, explore tópicos relacionados como **editar estilo do separador de nota de rodapé**, personalizar a numeração de notas ou aplicar formatação condicional baseada no layout da página. O mesmo padrão (recuperar um nó, fazer cast para `Run`, modificar `Text`) funciona em muitas outras situações de processamento de Word.

Bom código, e sinta‑se à vontade para experimentar diferentes símbolos ou até mesmo inserir imagens como separadores para um layout de documento verdadeiramente único!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas em seus próprios projetos.

- [Words Processing with Footnote and Endnote](/words/english/net/working-with-footnote-and-endnote/)
- [Get Paragraph Style Separator In Word Document](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [Insert Document Style Separator in Word](/words/english/net/programming-with-styles-and-themes/insert-style-separator/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}