---
category: general
date: 2025-12-29
description: Crie uma forma retangular em um documento Word usando Aspose.Words C#.
  Aprenda a definir a transparência da forma, definir a cor da sombra e salvar o documento
  Word sem esforço.
draft: false
keywords:
- create rectangle shape
- set shape transparency
- set shadow color
- save word document
- create word document
language: pt
og_description: Crie uma forma retangular em um documento Word com Aspose.Words C#.
  Este guia mostra como definir a transparência da forma, definir a cor da sombra
  e salvar o documento Word.
og_title: Criar forma de retângulo no Word – Tutorial completo do Aspose.Words
tags:
- Aspose.Words
- C#
- Word Automation
title: Criar forma retangular no Word com Aspose.Words – Guia passo a passo
url: /pt/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar forma retangular no Word – Tutorial Completo do Aspose.Words

Já precisou **criar uma forma retangular** em um documento Word, mas não sabia por onde começar? Você não está sozinho; muitos desenvolvedores encontram essa dificuldade ao automatizar relatórios ou faturas. Neste guia, vamos percorrer passo a passo como criar uma forma retangular, definir a transparência da forma, definir a cor da sombra e, finalmente, **salvar o documento Word** usando Aspose.Words para .NET.

Cobriremos tudo, desde o objeto inicial do documento até o arquivo final `.docx` no disco, de modo que, ao final, você será capaz de **criar documentos Word** programaticamente sem adivinhações. Sem referências externas, apenas uma solução autônoma que você pode copiar‑colar no seu projeto.

## Pré‑requisitos

- .NET 6.0 ou superior (o código também funciona com .NET Framework 4.7+)
- Pacote NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)
- Familiaridade básica com a sintaxe C#
- Uma IDE de sua escolha (Visual Studio, Rider, VS Code, etc.)

> **Dica profissional:** Se você estiver usando uma avaliação gratuita do Aspose.Words, a biblioteca adicionará uma marca d'água ao arquivo de saída. Para produção, será necessário uma licença válida.

## Etapa 1: Inicializar o Document e o Builder

A primeira coisa que fazemos é criar um documento Word vazio e um `DocumentBuilder` que nos permite inserir conteúdo. Pense no builder como uma caneta virtual que desenha na página.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();

// The builder provides methods to add text, tables, shapes, etc.
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Por que isso importa:** Sem um `DocumentBuilder`, você teria que manipular a árvore de nós de baixo nível diretamente, o que é propenso a erros e mais difícil de ler.

## Etapa 2: Criar forma retangular

Agora realmente **criamos a forma retangular**. O método `InsertShape` recebe um enum `ShapeType`, largura e altura (em pontos). O objeto `Shape` retornado nos permite ajustar propriedades visuais posteriormente.

```csharp
// Insert a rectangle 150 pts wide and 80 pts tall
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

Neste ponto, o retângulo é uma caixa preta sólida ancorada ao parágrafo atual. Você pode movê‑lo, redimensioná‑lo ou até girá‑lo depois, se precisar.

![create rectangle shape with shadow](/images/rectangle-shadow.png "Um documento Word mostrando uma forma retangular com uma sombra cinza")

*Texto alternativo da imagem: criar forma retangular com sombra em um documento Word*

## Etapa 3: Definir transparência da forma

Transparência é o nível de “ver‑através” do preenchimento da forma. Aspose.Words usa a propriedade `Transparency` que varia de `0.0` (opaco) a `1.0` (totalmente transparente). Aqui **definimos a transparência da forma** para 40 % para que o texto subjacente permaneça legível.

```csharp
// Make the rectangle 40 % transparent
rectangleShape.Fill.Transparency = 0.4; // 0.0 = opaque, 1.0 = invisible
```

> **Caso extremo:** Se precisar de uma forma completamente invisível, mas ainda quiser que a sombra apareça, defina `Transparency` como `1.0` e atribua à forma uma largura de contorno diferente de zero.

## Etapa 4: Configurar a sombra

Uma sombra sutil adiciona profundidade. Vamos **definir a cor da sombra** para um cinza médio, ajustar seu raio de desfoque e deslocá‑la alguns pontos tanto horizontal quanto verticalmente.

```csharp
// Enable the shadow effect
rectangleShape.Shadow.Enabled = true;

// Shadow color – a neutral gray
rectangleShape.Shadow.Color = System.Drawing.Color.Gray;

// 40 % transparent shadow (same as shape's fill)
rectangleShape.Shadow.Transparency = 0.4;

// Blur radius makes the edge softer
rectangleShape.Shadow.Blur = 6;

// Horizontal and vertical offsets (in points)
rectangleShape.Shadow.OffsetX = 5;
rectangleShape.Shadow.OffsetY = 5;
```

> **Por que isso importa:** Uma sombra muito nítida ou escura pode parecer um artefato de impressão. Ajuste `Blur` e `Transparency` até que pareça natural.

## Etapa 5: Salvar o documento Word

Finalmente **salvamos o documento Word** no disco. O método `Save` determina automaticamente o formato do arquivo a partir da extensão; `.docx` é o formato OpenXML moderno.

```csharp
// Save the document to the desired folder
document.Save(@"C:\Temp\ShadowRectangle.docx");
```

Se a pasta não existir, Aspose.Words lançará uma `ArgumentException`. Certifique‑se de que o caminho seja válido ou crie o diretório antes.

## Exemplo Completo Funcional

Abaixo está o programa completo, pronto‑para‑executar, que reúne todas as etapas. Copie isso para um novo projeto de console e pressione **F5**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace AsposeRectangleDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Initialize document and builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // 2️⃣ Insert rectangle shape
            Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 80);

            // 3️⃣ Set shape transparency (40 % transparent)
            rectangleShape.Fill.Transparency = 0.4;

            // 4️⃣ Configure shadow (color, blur, offset, transparency)
            rectangleShape.Shadow.Enabled = true;
            rectangleShape.Shadow.Color = System.Drawing.Color.Gray;
            rectangleShape.Shadow.Transparency = 0.4;
            rectangleShape.Shadow.Blur = 6;
            rectangleShape.Shadow.OffsetX = 5;
            rectangleShape.Shadow.OffsetY = 5;

            // 5️⃣ Save the document
            string outputPath = @"C:\Temp\ShadowRectangle.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Resultado esperado

Abra `ShadowRectangle.docx` no Microsoft Word. Você deverá ver um retângulo cinza‑claro com uma sombra suave e ligeiramente deslocada, ambos renderizados com 40 % de transparência. A forma fica em uma página em branco, pronta para conteúdo adicional.

## Perguntas Frequentes & Variações

**E se eu precisar de outra forma?**  
Substitua `ShapeType.Rectangle` por qualquer outro valor do enum (`Ellipse`, `Triangle`, `Star`, etc.). O restante do código permanece igual.

**Posso mudar a cor do contorno?**  
Sim—use `rectangleShape.StrokeColor = System.Drawing.Color.Blue;` e, opcionalmente, defina `rectangleShape.StrokeWeight = 1.5;`.

**Como posicionar a forma em um local específico da página?**  
Defina `rectangleShape.WrapType = WrapType.None;` e então ajuste as propriedades `rectangleShape.Left` e `rectangleShape.Top` (os valores são em pontos).

**É possível adicionar texto dentro do retângulo?**  
Absolutamente. Após criar a forma, você pode chamar `rectangleShape.AppendChild(new Paragraph(document))` e então adicionar um `Run` com seu texto. Lembre‑se de definir as propriedades `rectangleShape.TextBox` se quiser formatação mais avançada.

## Dicas Profissionais & Armadilhas

- **Licença antecipada:** Se esquecer de aplicar uma licença, Aspose.Words inserirá uma marca d'água na primeira página, o que pode ser confuso durante os testes.
- **Dica de desempenho:** Ao gerar muitos documentos em um loop, reutilize uma única instância de `Document` e chame `document.RemoveAllChildren();` após cada salvamento para evitar pressão excessiva no GC.
- **Visibilidade da sombra:** Em telas de baixa resolução, uma sombra sutil pode parecer invisível. Aumente `Blur` ou `OffsetX/Y` para depuração, depois reduza para produção.

## Próximos Passos

Agora que você sabe como **criar forma retangular**, **definir transparência da forma**, **definir cor da sombra** e **salvar documento Word**, considere expandir o tutorial:

- Adicionar múltiplas formas e agrupá‑las.
- Inserir o retângulo dentro de uma célula de tabela para layout de relatório.
- Combinar a forma com `DocumentBuilder.InsertHtml` para sobrepor conteúdo HTML estilizado.
- Explorar outros efeitos visuais como `Glow` ou `Reflection` para documentos mais ricos visualmente.

Experimente, quebre coisas e depois refine—a geração programática de documentos é um playground onde design visual encontra código.

---

*Feliz codificação! Se encontrou algum problema, deixe um comentário abaixo e vamos solucionar juntos.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}