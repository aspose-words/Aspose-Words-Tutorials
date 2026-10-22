---
category: general
date: 2026-09-21
description: Crie um documento Word em branco com uma elipse oculta usando C#. Aprenda
  como ocultar formas no Word e gerar uma forma oculta programaticamente.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to create ellipse
- hide shape in word
- create hidden shape
language: pt
lastmod: 2026-09-21
og_description: Criar documento Word em branco com uma elipse oculta usando C#. Este
  guia mostra como ocultar formas no Word e criar formas ocultas programaticamente.
og_image_alt: Screenshot of a blank Word document that contains a hidden ellipse shape
  created with C#
og_title: Criar documento Word em branco com uma forma elipse oculta em C#
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create blank Word document with a hidden ellipse using C#. Learn how
    to hide shape in Word and generate a hidden shape programmatically.
  headline: How to create blank Word document and add a hidden ellipse shape in C#
  type: TechArticle
- questions:
  - answer: The shape’s XML adds a few hundred bytes, which is negligible for most
      use cases. The file remains essentially the same size as a truly empty document.
    question: Does hiding a shape affect document size?
  - answer: Yes. Load the document, locate the shape (`doc.GetChildNodes(NodeType.Shape,
      true)`), and set `shape.Hidden = false`.
    question: Can I unhide the shape later programmatically?
  - answer: No. Hidden objects are excluded from the print layout, so the printed
      page stays blank.
    question: Will the hidden shape appear when printing?
  - answer: 'The `Hidden` property is part of the OOXML spec, so any Word processor
      that fully implements OOXML (Word, LibreOffice, Google Docs) will respect the
      hidden flag. --- ## Conclusion You now know how to **create blank Word document**,
      **how to create ellipse**, **hide shape in Word**, and **create hidd'
    question: Is this approach compatible with Office Open XML (OOXML) only?
  type: FAQPage
tags:
- Aspose.Words
- C#
- Word automation
title: Como criar um documento Word em branco e adicionar uma forma de elipse oculta
  em C#
url: /pt/java/images-shapes/how-to-create-blank-word-document-and-add-a-hidden-ellipse-s/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como criar um documento Word em branco e adicionar uma forma de elipse oculta em C#

Se você precisa **criar um documento Word em branco** que contém um gráfico invisível, este guia mostra exatamente como fazer. Ao final do tutorial, você terá um arquivo .docx que parece vazio, mas que realmente armazena uma forma de elipse oculta no layout.

Usaremos Aspose.Words for .NET para construir o documento, inserir uma elipse, ocultá‑la e salvar o arquivo. As etapas também cobrem **como criar elipse** objetos, a forma correta de **ocultar forma no Word**, e como **criar forma oculta** código que funciona com qualquer projeto .NET.

## Pré-requisitos

Antes de começar, certifique‑se de que você tem:

* .NET 6.0 SDK ou posterior instalado  
* Visual Studio 2022 (ou qualquer editor C#)  
* Uma licença Aspose.Words for .NET ou uma cópia de avaliação gratuita  
* Familiaridade básica com a sintaxe C#  

Nenhum pacote NuGet adicional é necessário além de `Aspose.Words`.

## Criar documento Word em branco com Aspose.Words

A primeira etapa é gerar um arquivo Word vazio. Isso nos fornece uma tela limpa onde podemos inserir gráficos ocultos posteriormente.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document doc = new Document();

        // The document is currently empty – it contains no paragraphs or shapes.
        // This is the foundation for all further operations.
```

**Por que começamos com um documento em branco** – Começar a partir de um arquivo vazio garante que nenhum conteúdo indesejado interfira na forma oculta. Também mantém o tamanho do arquivo mínimo, o que é útil quando o documento é usado posteriormente como modelo.

## Como criar elipse dentro do documento em branco

Em seguida, precisamos de um `DocumentBuilder` para adicionar conteúdo. O builder nos permite posicionar formas exatamente onde desejamos.

```csharp
        // Step 2: Initialize a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert an ellipse shape (width: 100 points, height: 50 points)
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

        // The ellipse now exists on the page, but it is visible by default.
```

**Explicação** – `ShapeType.Ellipse` indica ao Aspose.Words que desenhe uma figura aproximadamente circular. A largura e a altura são medidas em pontos (1 pt ≈ 1/72 polegada). Você pode ajustar esses valores para atender às necessidades do seu design.

## Ocultar forma no Word para que não apareça no layout

Uma forma que está oculta ainda permanece no XML do documento, o que pode ser útil para metadados, formatação condicional ou modificações programáticas posteriores. Para ocultá‑la, definimos a propriedade `Hidden` como `true`.

```csharp
        // Step 4: Hide the shape so it does not appear in the layout
        ellipse.Hidden = true;

        // When Hidden = true, Word treats the shape as if it were not there.
        // The shape remains in the document’s DOM, allowing you to retrieve or modify it later.
```

**Por que ocultar a forma** – Formas ocultas são ignoradas pelo mecanismo de layout, portanto a página parece completamente em branco. No entanto, os dados da forma persistem, o que pode ser útil para armazenar marcadores, bookmarks ou XML personalizado que processos subsequentes podem ler.

## Salvar o documento com a forma oculta

Finalmente, gravamos o arquivo no disco. O `.docx` salvo abrirá no Microsoft Word sem conteúdo visível, porém a elipse oculta ainda estará presente.

```csharp
        // Step 5: Save the document with the hidden shape
        doc.Save(@"C:\Temp\HiddenEllipse.docx");

        // The file now contains a hidden ellipse and appears empty when opened.
    }
}
```

**Verificação** – Abra o arquivo gerado no Word, então pressione `Alt+F9` para alternar códigos de campo e `Ctrl+A` → `Ctrl+Shift+F9` para visualizar objetos ocultos. Você verá a elipse no XML do documento (`word/document.xml`), mas nada na página.

---

## Exemplo completo, executável

Abaixo está o programa completo que você pode copiar‑colar em um novo projeto de console. Ele inclui todas as diretivas `using` e o método `Main` para que você possa executá‑lo sem scaffolding adicional.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace HiddenShapeDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a new blank Word document
            Document doc = new Document();

            // 2️⃣ Prepare a builder to insert content
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert an ellipse (100 pt × 50 pt)
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

            // 4️⃣ Hide the ellipse so the page stays empty
            ellipse.Hidden = true;

            // 5️⃣ Save the file
            string outPath = @"C:\Temp\HiddenEllipse.docx";
            doc.Save(outPath);

            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

**Saída esperada** – Quando você executar o programa, o console imprime o caminho do arquivo, e o arquivo Word resultante não contém objetos visíveis. Se você inspecionar o documento com uma ferramenta zip (`.docx` é um arquivo zip), encontrará o elemento `<w:pict>` descrevendo a elipse dentro de `word/document.xml`.

---

## Variações comuns e casos de borda

| Cenário | O que mudar | Por que importa |
|----------|----------------|----------------|
| **Forma diferente** | Substitua `ShapeType.Ellipse` por `ShapeType.Rectangle`, `ShapeType.Line`, etc. | Permite ocultar outras imagens mantendo o mesmo fluxo de trabalho. |
| **Múltiplas formas ocultas** | Chame `InsertShape` várias vezes e defina `Hidden = true` em cada uma. | Útil para incorporar uma coleção de marcadores ou placeholders. |
| **Visibilidade condicional** | Use `shape.Visible = false` junto com `shape.Hidden = true` para maior segurança. | Algumas versões mais antigas do Word tratam `Visible` de forma diferente; definir ambos cobre todos os casos. |
| **Salvar em um stream** | Substitua `doc.Save(path)` por `doc.Save(stream, SaveFormat.Docx)`. | Permite enviar o documento diretamente via HTTP ou armazená‑lo em um banco de dados. |
| **Aplicar um estilo** | Após a inserção, modifique `ellipse.FillColor`, `ellipse.LineWeight`, etc. antes de ocultar. | A estilização da forma é mantida no XML, o que pode ser útil para desocultar posteriormente. |

**Dica profissional:** Sempre teste a forma oculta na versão alvo do Word (por exemplo, Word 2019, Word 365) porque peculiaridades de renderização podem surgir ocasionalmente quando objetos ocultos interagem com layouts de página complexos.

---

## Perguntas frequentes

**Q: Ocultar uma forma afeta o tamanho do documento?**  
A: O XML da forma adiciona algumas centenas de bytes, o que é negligenciável na maioria dos casos. O arquivo permanece essencialmente do mesmo tamanho que um documento realmente vazio.

**Q: Posso desocultar a forma posteriormente programaticamente?**  
A: Sim. Carregue o documento, localize a forma (`doc.GetChildNodes(NodeType.Shape, true)`) e defina `shape.Hidden = false`.

**Q: A forma oculta aparecerá ao imprimir?**  
A: Não. Objetos ocultos são excluídos do layout de impressão, portanto a página impressa permanece em branco.

**Q: Essa abordagem é compatível apenas com Office Open XML (OOXML)?**  
A: A propriedade `Hidden` faz parte da especificação OOXML, portanto qualquer processador de texto que implemente totalmente OOXML (Word, LibreOffice, Google Docs) respeitará a flag oculta.

---

## Conclusão

Agora você sabe como **criar documento Word em branco**, **criar elipse**, **ocultar forma no Word**, e **criar forma oculta** usando Aspose.Words for .NET. O tutorial cobriu todo o ciclo de vida — desde a inicialização de um arquivo vazio até a inserção, ocultação e salvamento da forma — além de etapas de verificação e variações comuns.

Em seguida, você pode explorar:

* Adicionar caixas de texto ocultas para metadados (técnica `hide shape in word` aplicada a texto)  
* Usar partes XML personalizadas para armazenar dados estruturados ao lado de formas ocultas  
* Converter o documento com forma oculta para PDF preservando os elementos ocultos  

Experimente diferentes formas e configurações de visibilidade para ver como conteúdo oculto pode servir como um armazenamento de dados leve dentro de arquivos Word.

Feliz codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Criar forma retangular no Word usando C# – Guia passo a passo](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Criar forma de grupo em documento Word usando Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Criar documento Word com um retângulo sombreado – Guia passo a passo](/words/english/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}