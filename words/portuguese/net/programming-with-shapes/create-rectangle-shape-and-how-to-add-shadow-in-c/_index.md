---
category: general
date: 2026-04-04
description: Crie uma forma retangular em C# com Aspose.Words e aprenda como adicionar
  sombra, aplicar desfoque à sombra e tornar a sombra transparente – guia passo a
  passo.
draft: false
keywords:
- create rectangle shape
- how to add shadow
- how to create document
- apply blur to shadow
- make shadow transparent
language: pt
og_description: Crie uma forma retangular em C# com Aspose.Words. Aprenda a adicionar
  sombra, aplicar desfoque à sombra e tornar a sombra transparente em um tutorial
  conciso.
og_title: Criar forma de retângulo e como adicionar sombra em C#
tags:
- Aspose.Words
- C#
- Document Automation
title: Criar forma retangular e como adicionar sombra em C#
url: /pt/net/programming-with-shapes/create-rectangle-shape-and-how-to-add-shadow-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar forma retangular e como adicionar sombra em C#

Já precisou **criar forma retangular** em um documento Word, mas não sabia como dar a ela uma sombra sutil? Você não está sozinho. Em muitos cenários de relatórios ou branding, um simples retângulo com uma sombra suave e semitransparente pode deixar o layout mais refinado sem muito esforço.

Neste tutorial vamos percorrer **como criar documento** usando Aspose.Words, depois mostrar **como adicionar sombra**, **aplicar desfoque à sombra** e até **tornar a sombra transparente**. Ao final, você terá um trecho de código C# pronto‑para‑executar que produz um arquivo *.docx* com um retângulo bem sombreado — tudo em poucos minutos.

## O que você vai precisar

- .NET 6 ou superior (a API também funciona com .NET Framework 4.6+)
- Aspose.Words for .NET (a versão de avaliação gratuita serve para este exemplo)
- Um editor de código – Visual Studio, VS Code, Rider, ou o que preferir
- Conhecimento básico de C# – nada avançado, apenas a capacidade de executar um aplicativo de console

Se você tem tudo isso, podemos ir direto à solução.

## Etapa 1 – Como criar documento e inicializar a tela

Primeiro de tudo: você precisa de um objeto `Document` em branco. Pense nele como uma folha de papel vazia que o Aspose.Words transformará posteriormente em um arquivo Word.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // For Color

// Create a new blank document
Document doc = new Document();
```

Por que instanciamos `Document` em vez de carregar um modelo? Começar do zero garante que nenhum estilo ou seção ocultos interfiram na nossa forma. Também mantém o tamanho do arquivo pequeno – um bom hábito ao gerar muitos documentos em um loop.

## Etapa 2 – Criar forma retangular (o núcleo da nossa palavra‑chave principal)

Agora realmente **criar forma retangular**. A classe `Shape` é flexível; você informa o tipo (Rectangle), o tamanho e como ela deve envolver o texto ao redor.

```csharp
// Define a rectangular shape
Shape rect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,               // Width in points (≈2.8 inches)
    Height = 100,              // Height in points (≈1.4 inches)
    WrapType = WrapType.Inline // Makes the shape behave like a character
};
```

Observe o uso da sintaxe de inicializador de objeto – é conciso e reduz a chance de esquecer de definir uma propriedade depois. O retângulo ficará dentro do primeiro parágrafo, que adicionaremos na próxima etapa.

## Etapa 3 – Como adicionar sombra e personalizar sua aparência

Adicionar uma sombra não é apenas uma linha única; há várias propriedades para ajustar. É aqui que as palavras‑chave secundárias **aplicar desfoque à sombra** e **tornar a sombra transparente** entram em ação.

```csharp
// Configure the shadow
rect.Shadow.Format.Color = Color.DarkGray;   // Shadow colour
rect.Shadow.Format.BlurRadius = 5.0;         // Apply blur to shadow (points)
rect.Shadow.Format.OffsetX = 3;              // Horizontal offset
rect.Shadow.Format.OffsetY = 3;              // Vertical offset
rect.Shadow.Format.Transparency = 0.3;       // 30 % transparent (make shadow transparent)
```

Uma observação rápida sobre os números: `BlurRadius` de 5 gera um leve feathering; aumente para 10 para um aspecto mais suave, ou reduza para 2 para uma borda mais nítida. O valor de `Transparency` varia de 0 (opaco) a 1 (invisível). Ajuste conforme os requisitos de contraste da sua marca.

### Dica profissional

Se precisar de uma sombra colorida (por exemplo, um azul corporativo), basta substituir `Color.DarkGray` por `Color.FromArgb(80, 0, 120, 215)`. O primeiro argumento é o canal alfa – mantenha‑o baixo para sutileza.

## Etapa 4 – Inserir a forma no documento

Com o retângulo e sua sombra prontos, agora o colocamos no primeiro parágrafo do documento. Esta etapa garante que a forma apareça no topo do arquivo.

```csharp
// Append the shape to the first paragraph of the first section
doc.FirstSection.Body.FirstParagraph.AppendChild(rect);
```

Por que o primeiro parágrafo? É um padrão seguro que funciona mesmo quando o documento está completamente vazio. Se você tiver um local específico (por exemplo, após um título), localize esse nó e insira a forma lá.

## Etapa 5 – Salvar o arquivo e verificar o resultado

Por fim, persistimos o documento no disco. Você pode escolher qualquer caminho que desejar; apenas certifique‑se de que a pasta exista.

```csharp
// Save the document
doc.Save(@"C:\Temp\ShadowRectangle.docx");
```

Ao abrir *ShadowRectangle.docx* no Microsoft Word, você deverá ver um retângulo de 200 × 100 pontos com uma sombra cinza‑escura, levemente desfocada, 30 % transparente, deslocada três pontos para a direita e para baixo. O efeito é sutil, mas adiciona profundidade a layouts que seriam planos.

![criar forma retangular com sombra no Aspose.Words](https://example.com/placeholder-image.png "criar forma retangular com sombra no Aspose.Words")

*Texto alternativo da imagem:* **criar forma retangular com sombra no Aspose.Words** – a imagem mostra o documento final com o retângulo sombreado.

## Variações comuns e casos de borda

### Alterar a cor da sombra dinamicamente

Se sua aplicação suporta temas, você pode obter a cor da sombra a partir de um arquivo de configuração:

```csharp
Color themeShadow = ColorTranslator.FromHtml(ConfigurationManager.AppSettings["ShadowColor"]);
rect.Shadow.Format.Color = themeShadow;
```

### Tornar a forma não‑inline

Às vezes você quer que o retângulo flutue sobre o texto. Troque `WrapType` para `WrapType.Square` e defina `RelativeHorizontalPosition` como `RelativeHorizontalPosition.Margin` para ter mais controle.

```csharp
rect.WrapType = WrapType.Square;
rect.RelativeHorizontalPosition = RelativeHorizontalPosition.Margin;
rect.Left = 72; // 1 inch from the left margin
```

### Manipular múltiplas páginas

Se precisar de um retângulo em cada página, percorra `doc.Sections` e anexe uma forma clonada ao primeiro parágrafo de cada seção. Lembre‑se de chamar `rect.Clone(true)` para duplicar também as configurações da sombra.

## Recapitulação – O que conseguimos

- **Criar forma retangular** usando Aspose.Words
- **Como adicionar sombra** com cor, deslocamento, desfoque e transparência
- Demonstrado **aplicar desfoque à sombra** e **tornar a sombra transparente**
- Salvar um arquivo Word que pode ser aberto instantaneamente

Tudo isso foi alcançado com apenas algumas linhas, provando que ajustes visuais sofisticados não exigem sempre bibliotecas gráficas pesadas.

## O que vem a seguir?

- Experimente outros `ShapeType`s (Ellipse, Cloud, etc.) e veja como as sombras se comportam.
- Combine o retângulo com caixas de texto para criar chamadas rotuladas.
- Aprofunde‑se em **como criar documento** modelos que já contenham espaços reservados para formas e, então, preencha‑os programaticamente.

Sinta‑se à vontade para ajustar o raio do desfoque, a cor ou a transparência até que a sombra fique exatamente como deseja para a sua linguagem de design. A API é permissiva, e as alterações são visíveis instantaneamente ao reexecutar o aplicativo de console.

Feliz codificação, e que seus documentos tenham sempre aquele toque extra de profundidade!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}