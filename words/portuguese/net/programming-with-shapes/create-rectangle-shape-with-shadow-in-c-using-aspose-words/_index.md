---
category: general
date: 2026-03-22
description: Crie uma forma retangular em C# e adicione sombra à forma com Aspose.Words.
  Aprenda como adicionar sombra, como criar um retângulo e como definir as propriedades
  da sombra.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- how to add shadow
- how to create rectangle
- how to set shadow
language: pt
og_description: Crie uma forma retangular em C# e adicione sombra à forma usando Aspose.Words.
  Guia passo a passo que cobre como adicionar sombra, como criar um retângulo e como
  definir a sombra.
og_title: Criar forma de retângulo com sombra em C# – Guia completo
tags:
- Aspose.Words
- C#
- Document Automation
title: Criar forma retangular com sombra em C# usando Aspose.Words
url: /pt/net/programming-with-shapes/create-rectangle-shape-with-shadow-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create rectangle shape with shadow in C# using Aspose.Words

Já precisou **criar uma forma retangular** em um documento Word, mas não sabia como dar a ela uma sombra sutil? Você não está sozinho — muitos desenvolvedores encontram esse obstáculo ao começar a trabalhar com automação de documentos. Neste guia vamos mostrar passo a passo como **adicionar sombra a uma forma** usando Aspose.Words, e também responder “**como adicionar sombra**”, “**como criar retângulo**” e “**como definir sombra**” ao longo do caminho.

Começaremos com um `Document` vazio, desenharemos um retângulo, ativaremos sua sombra, ajustaremos o desfoque, a distância, o ângulo e a cor, e, por fim, salvaremos o arquivo. Ao final, você terá um `.docx` pronto para uso que mostra um retângulo em tom de cinza flutuando logo acima da página. Sem mistério, apenas código direto que você pode copiar‑colar em qualquer projeto .NET.

## Prerequisites

Antes de mergulharmos, certifique‑se de que você tem:

* **Aspose.Words for .NET** (a versão mais recente até março 2026). Você pode obtê‑la via NuGet com `Install-Package Aspose.Words`.
* Um ambiente de desenvolvimento .NET — Visual Studio, Rider ou até VS Code com a extensão C# funciona bem.
* Conhecimento básico de C# — nada sofisticado, apenas a capacidade de criar um aplicativo console ou WinForms.

É isso. Nenhuma biblioteca extra, nenhum passo oculto. Pronto? Vamos começar.

## Step 1: Initialize a new empty document

Para **criar forma retangular**, primeiro precisamos de um contêiner — um objeto `Document` — que representa o arquivo Word.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new empty document
Document document = new Document();
```

A classe `Document` é o ponto de entrada para tudo que o Aspose.Words faz. Pense nela como uma tela em branco; sem ela você não pode adicionar formas, tabelas ou texto.

## Step 2: Create the rectangle that will hold the shadow

Agora vamos **como criar retângulo** instanciando um `Shape` do tipo `Rectangle`. Também definimos seu tamanho em pontos (1 ponto ≈ 1/72 polegada).

```csharp
// Step 2: Create a rectangular shape that will hold the shadow
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 200; // width in points
rectangleShape.Height = 100; // height in points
```

Por que escolher 200 × 100 pontos? É um tamanho decente para demonstração — grande o suficiente para ver a sombra claramente, mas não tão grande a ponto de sobrecarregar a página. Sinta‑se à vontade para ajustar esses valores conforme seu layout.

## Step 3: Enable the shadow effect and configure its appearance

Aqui está o coração do tutorial: **como adicionar sombra** e **como definir sombra**. O Aspose.Words expõe um objeto `Shadow` em cada forma, permitindo ativar o efeito e ajustar parâmetros visuais.

```csharp
// Step 3: Enable the shadow effect and configure its appearance
rectangleShape.Shadow.Enabled    = true;                     // turn the shadow on
rectangleShape.Shadow.BlurRadius = 5;                       // blur radius in pixels
rectangleShape.Shadow.Distance   = 8;                       // distance from the shape in pixels
rectangleShape.Shadow.Angle      = 45;                      // direction of the light source (degrees)
rectangleShape.Shadow.Color      = System.Drawing.Color.Gray; // shadow color
```

* **BlurRadius** suaviza as bordas — um valor maior deixa a sombra mais difusa.
* **Distance** afasta a sombra do retângulo.
* **Angle** determina de onde a luz parece vir; 45° gera uma sombra diagonal, de aspecto natural.
* **Color** permite escolher qualquer `System.Drawing.Color`. Cinza é um padrão seguro, mas você pode usar `Color.Black` para algo forte ou `Color.LightGray` para algo sutil.

Dica profissional: se você definir `Enabled = false`, todas as outras configurações de sombra são ignoradas, portanto verifique sempre essa flag.

## Step 4: Insert the shape into the document body

Com o retângulo pronto e sua sombra configurada, precisamos inseri‑lo no documento. A maneira mais simples é anexá‑lo ao primeiro parágrafo da primeira seção.

```csharp
// Step 4: Insert the shape into the first paragraph of the document body
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

Se o seu documento já contém texto, você pode localizar um `Paragraph` específico ou até uma célula de `Table` e inserir a forma lá. O método `AppendChild` é versátil — funciona com qualquer tipo de `Node`.

## Step 5: Save the document and verify the result

Por fim, gravamos o arquivo no disco. Altere o caminho para onde desejar; a pasta deve existir, caso contrário você receberá uma exceção.

```csharp
// Step 5: Save the document with the shadowed shape
document.Save(@"C:\Temp\ShadowedRectangle.docx");
```

Abra o `ShadowedRectangle.docx` resultante no Microsoft Word (ou LibreOffice) e você deverá ver um retângulo cinza com uma sombra nítida, diagonal, deslocada para baixo‑direita. Se a sombra parecer muito fraca, aumente `BlurRadius` ou `Distance` e execute o código novamente — experimentar faz parte da diversão.

![Create rectangle shape with shadow example](rectangle-shadow.png){alt="Exemplo de forma retangular com sombra"}

### Expected output

* Um documento Word de uma única página.
* Um retângulo cinza de 200 × 100 pontos posicionado no canto superior esquerdo da página.
* Uma sombra cinza sutil deslocada 8 pixels em um ângulo de 45°, desfocada em 5 pixels.

## How to add shadow to shape – deeper dive

Você pode se perguntar: *“Posso animar a sombra ou fazê‑la mudar com base na entrada do usuário?”* Embora o Aspose.Words não suporte animação, você pode ajustar programaticamente as propriedades da sombra antes de salvar, criando efetivamente várias versões do mesmo documento com aparências diferentes. Por exemplo, iterando sobre uma coleção de cores:

```csharp
Color[] shadowColors = { Color.Gray, Color.Black, Color.DarkSlateGray };
foreach (var col in shadowColors)
{
    rectangleShape.Shadow.Color = col;
    document.Save($@"C:\Temp\Shadow_{col.Name}.docx");
}
```

Esse pequeno trecho demonstra **como definir sombra** dinamicamente — ótimo para gerar relatórios temáticos.

## How to create rectangle – alternative shapes

Se precisar de um retângulo arredondado, basta mudar o `ShapeType`:

```csharp
Shape rounded = new Shape(document, ShapeType.RoundRectangle);
rounded.Width  = 200;
rounded.Height = 100;
rounded.Shadow.Enabled = true; // shadow works the same way
```

Ou, para um quadrado perfeito, defina `Width` igual a `Height`. As mesmas propriedades de sombra se aplicam, então você já está coberto sobre **como adicionar sombra** para qualquer forma que escolher.

## Common pitfalls and troubleshooting

| Symptom | Likely cause | Fix |
|---------|--------------|-----|
| A sombra não aparece | `Shadow.Enabled` deixado como `false` | Defina `rectangleShape.Shadow.Enabled = true;` |
| A sombra parece muito nítida | `BlurRadius` definido como 0 | Aumente `BlurRadius` para pelo menos 3 |
| O documento lança `FileNotFoundException` ao salvar | Pasta de destino não existe | Crie a pasta primeiro ou use um caminho válido |
| A forma está invisível | Largura/Altura definidas como 0 | Garanta que ambas as dimensões sejam > 0 |

Ficar atento a esses detalhes evita o clássico “por que minha forma não está aparecendo?” moment.

## Recap – what we’ve accomplished

* **Criar forma retangular** em um novo documento Word usando Aspose.Words.  
* **Adicionar sombra à forma** ativando a flag `Shadow.Enabled` e ajustando desfoque, distância, ângulo e cor.  
* Demonstrado **como adicionar sombra**, **como criar retângulo** e **como definir sombra** em um snippet de código limpo e reutilizável.  
* Fornecido um exemplo completo, pronto‑para‑executar, que você pode colar em qualquer projeto C#.

## What’s next?

Agora que você domina o básico, considere explorar:

* **Como adicionar sombra a imagens** — a mesma API `Shadow` funciona para `ShapeType.Image`.
* **Combinando múltiplas formas** — crie fluxogramas ou infográficos diretamente no Word.
* **Exportando para PDF** — chame `document.Save("output.pdf")` após adicionar sombras para uma versão imprimível.

Sinta‑se à vontade para experimentar diferentes cores, ângulos ou até preenchimentos em gradiente. A API é flexível o suficiente para que você crie documentos com aparência profissional sem nunca abrir o Word manualmente.

---

Happy coding! If you run into any hiccups, drop a comment below or check the Aspose.Words forums – the community is quick to help.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}