---
category: general
date: 2026-03-01
description: Adicione um retângulo ao PDF rapidamente usando Aspose.Words. Aprenda
  a inserir formas no PDF, adicionar gráficos ao PDF e criar documentos PDF programaticamente
  com uma sombra personalizada.
draft: false
keywords:
- add rectangle to pdf
- insert shape pdf
- add graphics to pdf
- create pdf document programmatically
- create pdf with shape
language: pt
og_description: Adicionar retângulo ao PDF usando Aspose.Words. Este tutorial mostra
  como inserir forma no PDF, adicionar gráficos ao PDF e criar documento PDF programaticamente
  em C#.
og_title: Adicionar retângulo ao PDF com Aspose.Words – Guia Completo
tags:
- pdf
- aspnet
- csharp
- graphics
title: Adicionar retângulo ao PDF com Aspose.Words – Guia passo a passo
url: /pt/python/images-shapes/add-rectangle-to-pdf-with-aspose-words-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Adicionar retângulo ao PDF com Aspose.Words – Guia Completo

Já precisou **adicionar retângulo ao PDF** mas não sabia qual chamada de API faz isso? Você não está sozinho—desenvolvedores perguntam constantemente: “Como inserir uma forma no PDF e ainda manter o arquivo leve?” A boa notícia é que o Aspose.Words torna isso muito simples. Neste tutorial vamos percorrer todo o processo, desde a criação programática de um documento PDF até a estilização do retângulo com sombra.

Também vamos incluir alguns extras: você aprenderá como **adicionar gráficos ao PDF**, verá os passos exatos para **inserir forma PDF**, e terminará com um exemplo pronto‑para‑executar que **cria PDF com forma**. Sem referências externas, apenas uma solução autocontida que você pode copiar‑colar hoje.

## Pré-requisitos

Antes de colocar a mão na massa, certifique‑se de que você tem:

- .NET 6.0 ou superior (Aspose.Words funciona com .NET Standard 2.0+)
- Uma licença válida do Aspose.Words for .NET ou uma chave de avaliação temporária
- Visual Studio 2022 (ou qualquer IDE de sua preferência)
- Conhecimento básico de C#—nada sofisticado, apenas a capacidade de executar um aplicativo console

É só isso. Se você tem tudo isso, está pronto para começar.

## Etapa 1: Criar um documento PDF programaticamente

A primeira coisa que você faz quando quer **adicionar retângulo ao PDF** é iniciar um documento vazio. Pense na classe `Document` como uma tela em branco; tudo o que você adicionar depois viverá dentro dela.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1 – initialise a new empty document
        Document doc = new Document();

        // The rest of the steps follow...
```

Por que começar com um documento vazio? Porque isso garante controle total sobre cada elemento—sem cabeçalhos ou rodapés ocultos para lidar depois.

## Etapa 2: Inicializar um DocumentBuilder para inserir forma PDF

Um `DocumentBuilder` é sua ferramenta de desenho. Ele sabe como posicionar texto, imagens e, crucialmente para nós, formas. Sem ele, você teria que manipular a árvore de nós de baixo nível manualmente—um pesadelo para a maioria dos desenvolvedores.

```csharp
        // Step 2 – create a builder that will let us add content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Observe que ainda não adicionamos nenhuma página. O builder criará automaticamente uma página na primeira inserção, mantendo o código limpo.

## Etapa 3: Inserir uma forma retângulo – o núcleo de “adicionar retângulo ao PDF”

Agora vem a parte divertida: inserir o retângulo. O método `InsertShape` suporta dezenas de valores `ShapeType`; vamos escolher `ShapeType.Rectangle` e definir um tamanho de 200 × 100 pontos.

```csharp
        // Step 3 – insert a rectangle (200 × 100 points) into the document
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

Neste ponto o PDF já contém um retângulo simples. Se você abrir o arquivo agora, verá uma caixa simples no canto superior esquerdo da primeira página. Essa é a base para **adicionar gráficos ao PDF**.

## Etapa 4: Estilizar o retângulo – adicionando uma sombra personalizada

Um retângulo sem estilo é entediante. Vamos dar a ele uma sombra sutil para que *se destaque* quando o PDF for renderizado. O objeto `ShadowFormat` controla tudo, desde o raio de desfoque até a opacidade.

```csharp
        // Step 4 – configure a custom shadow for the shape
        ShadowFormat shadow = rectangle.ShadowFormat;
        shadow.Visible = true;
        shadow.BlurRadius = 8.0;          // pixels
        shadow.Distance = 5.0;           // points from the shape
        shadow.Direction = 45.0;         // degrees clockwise
        shadow.Opacity = 0.6;            // 0‑1 range
        shadow.Color = Color.Black;
```

Por que se preocupar com sombra? Além do ganho estético, uma sombra pode ajudar a diferenciar gráficos sobrepostos—algo que você pode precisar ao **adicionar gráficos ao PDF** em relatórios mais complexos.

## Etapa 5: Salvar o arquivo – concluindo o fluxo “criar PDF com forma”

A linha final grava tudo no disco. O Aspose.Words escolhe automaticamente a versão correta do PDF e incorpora os recursos necessários.

```csharp
        // Step 5 – save the document as a PDF file
        doc.Save(@"C:\Temp\ShapeWithShadow.pdf");
    }
}
```

Abra `ShapeWithShadow.pdf` e você verá um retângulo bem sombreado ocupando orgulhosamente a página. Esse é todo o fluxo de **criar documento PDF programaticamente**, resumido em menos de 30 linhas de código.

## Exemplo completo – criar PDF com forma do início ao fim

Abaixo está o programa completo que você pode copiar‑colar em um novo projeto de Console App. Ele inclui todas as instruções `using`, o método `Main` e um breve cabeçalho de comentário para referência futura.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectanglePdfDemo
{
    /// <summary>
    /// Demonstrates how to add a rectangle to PDF, configure a shadow,
    /// and save the result using Aspose.Words for .NET.
    /// </summary>
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create an empty PDF document
            Document doc = new Document();

            // 2️⃣ Initialise a DocumentBuilder – the tool that lets us add content
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert a rectangle shape (200 × 100 points) – this is the core of "add rectangle to pdf"
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);

            // 4️⃣ Apply a custom shadow – makes the graphic stand out
            ShadowFormat shadow = rect.ShadowFormat;
            shadow.Visible = true;
            shadow.BlurRadius = 8.0;   // pixels
            shadow.Distance = 5.0;    // points
            shadow.Direction = 45.0;  // degrees
            shadow.Opacity = 0.6;     // semi‑transparent
            shadow.Color = Color.Black;

            // 5️⃣ Save the document – the final step in creating a PDF with shape
            string outputPath = @"C:\Temp\ShapeWithShadow.pdf";
            doc.Save(outputPath);

            Console.WriteLine($"PDF saved successfully to {outputPath}");
        }
    }
}
```

**Resultado esperado:** um PDF de página única onde um retângulo de 200 × 100 pontos está próximo ao canto superior esquerdo, adornado com uma sombra suave de 45 graus. Abra o arquivo em qualquer visualizador de PDF para verificar.

## Perguntas frequentes e casos de borda

### Isso funciona com outros tipos de forma?
Absolutamente. Substitua `ShapeType.Rectangle` por `ShapeType.Ellipse`, `ShapeType.Triangle` ou qualquer uma das mais de 150 opções suportadas pelo Aspose.Words. As mesmas propriedades de `ShadowFormat` se aplicam.

### E se eu precisar do retângulo em uma página específica?
Depois de inserir a forma, você pode movê‑la para outra página ajustando a propriedade `CurrentPage` do builder antes de chamar `InsertShape`. Por exemplo:

```csharp
builder.MoveToPage(3);
Shape rectOnPage3 = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

### Posso mudar a cor de preenchimento do retângulo?
Claro. Use a propriedade `FillColor`:

```csharp
rect.FillColor = Color.LightBlue;
```

### Como isso afeta o tamanho do arquivo?
Adicionar uma forma simples e uma sombra acrescenta apenas alguns kilobytes. Se você começar a empilhar muitos gráficos, considere comprimir imagens ou usar formas vetoriais para manter o PDF leve.

### É necessária uma licença para produção?
O Aspose.Words funciona em modo de avaliação, mas o PDF de saída conterá uma marca d'água. Adquira uma licença para uso ilimitado e para remover a marca d'água.

## Dicas e truques (nível Pro)

- **Inserção em lote:** Se precisar de dezenas de retângulos, faça um loop sobre uma coleção de coordenadas e reutilize o mesmo `DocumentBuilder`—o desempenho permanece linear.
- **Camadas:** Defina `rect.WrapType = WrapType.Inline` se quiser que o retângulo flua com o texto, ou `WrapType.Square` para que o texto o contorne.
- **Conformidade PDF/A:** Chame `doc.CompatibilityOptions.OptimizeForPdfA = true;` antes de salvar se precisar de um PDF amigável para arquivamento.

## Resumo visual

![exemplo de adicionar retângulo ao pdf](https://example.com/rectangle-shadow.png "exemplo de adicionar retângulo ao pdf")

A imagem ilustra o layout final do PDF: um retângulo limpo com uma sombra sutil, exatamente o que nosso código produz.

## Conclusão

Agora você sabe **como adicionar retângulo ao PDF** usando Aspose.Words, como **inserir forma PDF**, e como **adicionar gráficos ao PDF** com estilização personalizada—tudo enquanto **cria documento PDF programaticamente** e finaliza com um exemplo de **criar PDF com forma** que você pode reutilizar amanhã.  

Em seguida, experimente trocar o retângulo por um logotipo, ou combine várias formas para construir um diagrama simples. Você também pode explorar quebra de texto, rotação ou até mesmo incorporar um hyperlink dentro da forma. A API é rica o suficiente para transformar um PDF estático em um relatório interativo e rico em gráficos sem jamais sair do C#.

Sinta‑se à vontade para experimentar e, se encontrar algum obstáculo, deixe um comentário abaixo. Feliz codificação!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}