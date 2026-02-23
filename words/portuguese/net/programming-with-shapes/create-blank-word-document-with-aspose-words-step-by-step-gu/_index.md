---
category: general
date: 2026-02-23
description: Crie um documento Word em branco usando C# e Aspose.Words. Aprenda como
  adicionar uma forma retangular, aplicar sombra ao texto e salvar o Word com a forma
  em minutos.
draft: false
keywords:
- create blank word document
- add rectangle shape
- how to add shape
- add shadow word
- save word with shape
language: pt
og_description: Crie rapidamente um documento Word em branco. Este guia mostra como
  adicionar uma forma retangular, aplicar sombra ao texto e salvar o documento Word
  com a forma usando o Aspose.Words.
og_title: Criar documento Word em branco – Tutorial completo de C#
tags:
- Aspose.Words
- C#
- Document Automation
title: Criar documento Word em branco com Aspose.Words – Guia passo a passo
url: /pt/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar documento Word em branco – Tutorial completo em C#

Já se perguntou como **create blank word document** programaticamente sem abrir o Microsoft Word? Você não está sozinho. Em muitos projetos de automação precisamos de um arquivo .docx novo, inserir uma forma nele, dar a essa forma uma sombra agradável e então **save word with shape** para uso futuro.  

Neste guia, vamos percorrer exatamente isso — começando de um documento vazio, **adding a rectangle shape**, configurando um efeito **add shadow word**, e finalmente persistindo o arquivo. Ao final, você terá um trecho completo e executável que pode colar em qualquer aplicativo console .NET. Sem mistério, sem peças faltando.

## O que você precisará

- **Aspose.Words for .NET** (qualquer versão recente, por exemplo, 24.10).  
- .NET 6 ou superior (o código também funciona com .NET Framework 4.7+).  
- Um IDE básico de C# — Visual Studio, Rider ou até VS Code com a extensão C#.  

É isso. Nenhum pacote NuGet extra além do Aspose.Words, e nenhuma instalação do Word necessária.

---

## Etapa 1: Criar um documento Word em branco

A primeira coisa que você faz quando deseja **create blank word document** é instanciar a classe `Document`. Pense nela como uma tela limpa que o Aspose.Words fornece.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1 – initialize an empty document
Document document = new Document();   // this is a brand‑new, blank Word file
```

> **Por que isso importa:** O objeto `Document` contém todas as seções, parágrafos e formas. Começar com uma instância vazia garante que você controle cada elemento que será adicionado posteriormente.

---

## Etapa 2: Adicionar uma forma retangular ao documento

Agora que temos um documento limpo, vamos **add rectangle shape**. Um retângulo é um `Shape` simples com `ShapeType.Rectangle`. É claro que você pode escolher outros tipos, mas um retângulo funciona muito bem para demonstração.

```csharp
// Step 2 – create a rectangle shape
Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
{
    Width = 200,   // width in points (≈2.78 inches)
    Height = 100   // height in points (≈1.39 inches)
};
```

> **Dica profissional:** Se você alguma vez se perguntar **how to add shape** que não seja um retângulo, basta mudar `ShapeType.Rectangle` para qualquer outro valor de enumeração, como `ShapeType.Ellipse` ou `ShapeType.Polygon`. O resto do código permanece o mesmo.

---

## Etapa 3: Configurar uma sombra personalizada para a forma

Um retângulo simples parece um pouco sem graça, então vamos **add shadow word** para destacá-lo. O Aspose.Words expõe um objeto `ShadowFormat` com várias propriedades.

```csharp
// Step 3 – enable and style the shadow
rectangleShape.ShadowFormat.Enabled = true;                // turn on the shadow
rectangleShape.ShadowFormat.Color = Color.Gray;           // shadow color
rectangleShape.ShadowFormat.OffsetX = 5;                  // horizontal offset (points)
rectangleShape.ShadowFormat.OffsetY = 5;                  // vertical offset (points)
rectangleShape.ShadowFormat.Transparency = 0.3;           // 30 % transparent
rectangleShape.ShadowFormat.BlurRadius = 4;               // soft edge blur
```

> **Por que isso importa:** A sombra fornece uma indicação sutil de profundidade, especialmente quando o documento será visualizado na tela. Ajuste `OffsetX`, `OffsetY` e `BlurRadius` para adequar ao seu estilo de design.

---

## Etapa 4: Inserir a forma no documento

Com a forma pronta, precisamos posicioná‑la em algum lugar. O ponto mais simples é o primeiro parágrafo da primeira seção. Se o documento ainda não tiver parágrafos, o Aspose cria um automaticamente.

```csharp
// Step 4 – put the rectangle into the first paragraph
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

> **Caso extremo:** Se você pretende inserir a forma em um local específico (por exemplo, após um determinado título), localize o `Paragraph` alvo via `document.GetChildNodes(NodeType.Paragraph, true)` e use `InsertAfter` ou `InsertBefore` conforme necessário.

---

## Etapa 5: Salvar o documento Word com a forma

Finalmente, vamos **save word with shape** no disco. O método `Save` determina automaticamente o formato a partir da extensão do arquivo.

```csharp
// Step 5 – persist the document
string outputPath = @"C:\Temp\shadowedRectangle.docx";
document.Save(outputPath);
```

> **O que você verá:** Abra `shadowedRectangle.docx` no Word (ou em qualquer visualizador compatível) e você verá um retângulo cinza com uma sombra suave na parte superior da primeira página.

---

## Exemplo completo em funcionamento

Abaixo está o programa completo que você pode copiar‑colar em um aplicativo console. Ele inclui todas as diretivas `using`, comentários e as etapas exatas que discutimos.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace AsposeWordShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a blank word document
            Document document = new Document();

            // 2️⃣ Add a rectangle shape
            Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
            {
                Width = 200,
                Height = 100
            };

            // 3️⃣ Configure a custom shadow (add shadow word)
            rectangleShape.ShadowFormat.Enabled = true;
            rectangleShape.ShadowFormat.Color = Color.Gray;
            rectangleShape.ShadowFormat.OffsetX = 5;
            rectangleShape.ShadowFormat.OffsetY = 5;
            rectangleShape.ShadowFormat.Transparency = 0.3;
            rectangleShape.ShadowFormat.BlurRadius = 4;

            // 4️⃣ Insert the shape into the first paragraph
            document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

            // 5️⃣ Save the document (save word with shape)
            string outputFile = @"YOUR_DIRECTORY\shadow.docx";
            document.Save(outputFile);

            // Confirmation
            System.Console.WriteLine($"Document saved to {outputFile}");
        }
    }
}
```

Execute o programa, navegue até `YOUR_DIRECTORY` e abra o `shadow.docx` gerado. Você deverá ver o retângulo com uma sombra cinza sutil — exatamente o que pretendíamos alcançar.

---

## Perguntas Frequentes & Dicas

### Como mudar a cor da forma?
```csharp
rectangleShape.FillColor = Color.LightBlue;
```
Basta definir `FillColor` antes de anexar a forma.

### E se eu precisar de múltiplas formas na mesma página?
Crie objetos `Shape` adicionais e anexe cada um ao mesmo parágrafo ou a parágrafos diferentes. Você também pode controlar o layout usando `WrapType` e `RelativeHorizontalPosition`.

### Posso exportar para PDF mantendo a sombra?
Com certeza. Use `document.Save("output.pdf")` — o Aspose.Words preserva o efeito de sombra na conversão para PDF.

### Isso funciona no .NET Core?
Sim. O Aspose.Words é multiplataforma; o mesmo código funciona no .NET Core, .NET 5+ e .NET Framework.

### Como adicionar uma forma sem um parágrafo?
Você pode adicionar a forma diretamente a um `Run` ou a um `Story`. Para posicionamento mais preciso, defina `rectangleShape.RelativeHorizontalPosition = RelativeHorizontalPosition.Page` e ajuste as propriedades `Left`/`Top`.

---

## Resultado visual

![Forma retangular com sombra cinza em um documento Word – add shadow word example](https://example.com/placeholder-image.png "add shadow word example")

*O texto alternativo da imagem inclui a palavra‑chave secundária **add shadow word** para atender ao SEO.*

---

## Conclusão

Acabamos de demonstrar como **create blank word document**, **add rectangle shape**, aplicar um efeito **add shadow word** e, finalmente, **save word with shape** usando Aspose.Words para .NET. O processo é simples: instanciar um `Document`, criar um `Shape`, ajustar seu `ShadowFormat`, inseri‑lo e chamar `Save`.  

A partir daqui você pode experimentar — tentar diferentes tipos de forma, brincar com cores ou sobrepor várias formas. Se precisar mesclar este documento com conteúdo existente, basta carregar o arquivo existente via `new Document("existing.docx")` e seguir as mesmas etapas.  

Tem mais perguntas? Deixe um comentário, e feliz codificação!

---

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}