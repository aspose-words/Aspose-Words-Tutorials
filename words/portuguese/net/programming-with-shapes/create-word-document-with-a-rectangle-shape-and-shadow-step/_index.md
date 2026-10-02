---
category: general
date: 2026-03-01
description: Crie um documento Word usando Aspose.Words e aprenda como adicionar uma
  forma retangular, como adicionar sombra, como definir transparência e como criar
  forma — tudo em C#.
draft: false
keywords:
- create word document
- add rectangle shape
- how to add shadow
- how to create shape
- how to set transparency
language: pt
og_description: Crie um documento Word com Aspose.Words em C#. Aprenda a adicionar
  uma forma retangular, aplicar uma sombra externa e definir transparência em apenas
  alguns passos.
og_title: Criar documento do Word com forma retangular e sombra – Guia
tags:
- Aspose.Words
- C#
- Document Generation
title: Criar documento do Word com forma de retângulo e sombra – Guia passo a passo
url: /pt/net/programming-with-shapes/create-word-document-with-a-rectangle-shape-and-shadow-step/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crie um Documento Word com uma Forma Retangular e Sombra – Guia Passo a Passo

Já precisou **criar um documento word** que contenha um retângulo com estilo personalizado? Talvez você esteja construindo um modelo de relatório e queira uma sombra sutil para realçar o layout. Você não está sozinho—desenvolvedores perguntam constantemente: “Como adiciono uma forma retangular e uma sombra programaticamente?” A boa notícia é que, com Aspose.Words, você pode fazer isso em poucas linhas.

Neste tutorial vamos percorrer todo o processo: desde a criação de um arquivo Word em branco, até a adição de uma forma retangular, passando pela configuração de uma sombra externa com transparência. Ao final, você terá um `Shadow.docx` pronto para uso, que pode abrir no Word e ver o efeito instantaneamente. Sem ferramentas externas, sem XML complicado—apenas código C# limpo e explicações claras.

## O que você aprenderá

- **Como criar objetos shape** em um documento Word usando Aspose.Words.  
- **Como adicionar shape retangular** a um parágrafo sem bagunçar o conteúdo existente.  
- **Como adicionar sombra** (sombra externa) e controlar sua cor, deslocamento, desfoque e transparência.  
- **Como definir transparência** na sombra para que ela pareça profissional.  
- Dicas, armadilhas e variações que você pode precisar em projetos reais.

### Pré‑requisitos

- .NET 6.0 ou superior (a API também funciona com .NET Framework 4.6+).  
- Aspose.Words for .NET instalado via NuGet (`Install-Package Aspose.Words`).  
- Noções básicas de sintaxe C#—nada sofisticado, apenas as instruções `using` habituais e criação de objetos.

> **Dica profissional:** Se você estiver usando o Visual Studio, habilite “nullable reference types” para capturar possíveis bugs de referência nula mais cedo.

## Etapa 1 – Crie um Documento Word em Branco

Para **criar um documento word** começamos com a classe `Document`. Pense nela como uma tela vazia; você pode adicionar seções, parágrafos, tabelas ou formas posteriormente.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Initialize a new blank document
Document document = new Document();
```

Por que precisamos de uma nova instância de `Document`? Porque cada forma, parágrafo ou estilo vive dentro de um modelo de objeto de documento (DOM). Começar com um documento limpo garante que o retângulo que você adicionar não interfira no conteúdo existente.

## Etapa 2 – Defina a Forma Retangular

Agora vamos **como criar shape** um retângulo. O construtor `Shape` recebe o documento proprietário e o tipo de forma. Também definimos sua largura e altura em pontos (1 pt ≈ 1/72 pol).

```csharp
// Create a rectangle shape
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width = 200;   // 200 pt ≈ 2.78 in
rectangleShape.Height = 100; // 100 pt ≈ 1.39 in
```

Você pode se perguntar: “Posso usar centímetros em vez de pontos?” A API aceita apenas pontos, mas você pode converter: `points = centimeters * 28.35`. Essa pequena conversão é útil quando você alinha formas às margens da página.

## Etapa 3 – Adicione uma Sombra Externa e Defina Transparência

É aqui que a mágica acontece: **como adicionar shadow** e **como definir transparency** nessa sombra. A propriedade `ShadowFormat` oferece controle total.

```csharp
// Enable shadow visibility
rectangleShape.ShadowFormat.Visible = true;

// Choose a shadow color
rectangleShape.ShadowFormat.Color = System.Drawing.Color.DarkGray;

// Set transparency (0 = opaque, 1 = fully transparent)
rectangleShape.ShadowFormat.Transparency = 0.3; // 30 % transparent

// Position the shadow relative to the shape
rectangleShape.ShadowFormat.OffsetX = 5; // horizontal offset in points
rectangleShape.ShadowFormat.OffsetY = 5; // vertical offset in points

// Blur makes the shadow look softer
rectangleShape.ShadowFormat.BlurRadius = 4;

// Specify that this is an outer shadow (instead of inner)
rectangleShape.ShadowFormat.Style = ShadowStyle.OuterShadow;
```

**Por que essas configurações?**  
- **Transparency** permite que a textura da página subjacente apareça, evitando que a sombra pareça muito pesada.  
- **OffsetX/Y** criam a ilusão de que a forma está levantada da página.  
- **BlurRadius** suaviza as bordas—sem ele a sombra seria um retângulo rígido, o que parece artificial.  

Se precisar de um efeito mais dramático, aumente `OffsetX/Y` para 10 e `BlurRadius` para 8. Por outro lado, para um toque sutil, mantenha-os em 2 e 2, respectivamente.

## Etapa 4 – Insira a Forma no Documento

Agora **add rectangle shape** ao primeiro parágrafo do documento. Se o documento não tiver conteúdo, `FirstParagraph` é criado automaticamente para você.

```csharp
// Append the rectangle to the first paragraph
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

E se você quiser a forma dentro de uma célula de tabela específica ou em um parágrafo posterior? Basta localizar esse nó (`doc.GetChild(NodeType.Paragraph, index, true)`) e chamar `AppendChild` nele. O mesmo objeto `Shape` pode ser clonado caso precise de várias cópias.

## Etapa 5 – Salve o Documento

Finalmente, **create word document** no disco. Use um caminho que se adeque ao seu ambiente; o exemplo usa um placeholder.

```csharp
// Save the document as a .docx file
document.Save(@"YOUR_DIRECTORY/Shadow.docx");
```

Ao abrir `Shadow.docx` no Microsoft Word, você verá um retângulo cinza‑claro com uma sombra externa suave deslocada para a parte inferior‑direita. A transparência de 30 % da sombra garante que ela não domine a página.

---

![crie um documento word com uma forma retangular sombreada](image.png "Crie um documento word com uma forma retangular sombreada")

*Texto alternativo da imagem: crie um documento word com uma forma retangular sombreada*

## Código Completo, Pronto‑para‑Executar

Abaixo está o programa completo que você pode copiar‑colar em um aplicativo de console. Sem peças faltando, sem “veja a documentação para mais”.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Step 2: Add a rectangular shape and define its size
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width = 200;   // width in points
        rectangleShape.Height = 100;  // height in points

        // Step 3: Configure an outer shadow for the shape
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = System.Drawing.Color.DarkGray;
        rectangleShape.ShadowFormat.Transparency = 0.3;   // 30 % transparent
        rectangleShape.ShadowFormat.OffsetX = 5;          // horizontal offset
        rectangleShape.ShadowFormat.OffsetY = 5;          // vertical offset
        rectangleShape.ShadowFormat.BlurRadius = 4;
        rectangleShape.ShadowFormat.Style = ShadowStyle.OuterShadow;

        // Step 4: Insert the shape into the first paragraph of the document
        document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

        // Step 5: Save the document with the shadowed shape
        document.Save(@"YOUR_DIRECTORY/Shadow.docx");

        Console.WriteLine("Word document created successfully at YOUR_DIRECTORY/Shadow.docx");
    }
}
```

### Resultado Esperado

- Um arquivo chamado **Shadow.docx** aparece na pasta de destino.  
- Ao abri‑lo no Word, aparece um retângulo (200 × 100 pt) com uma sombra externa cinza‑escura.  
- A sombra está deslocada 5 pt horizontal e verticalmente, desfocada e com 30 % de transparência.

## Perguntas Frequentes & Casos Limite

| Pergunta | Resposta |
|----------|----------|
| **Posso mudar a cor da sombra para combinar com a minha marca?** | Absolutamente—basta substituir `System.Drawing.Color.DarkGray` por qualquer `Color` que preferir, por exemplo `Color.FromArgb(255, 0, 120, 215)` para um destaque azul. |
| **E se eu precisar de uma sombra interna em vez de externa?** | Defina `ShadowFormat.Style = ShadowStyle.InnerShadow`. O resto das propriedades funciona da mesma forma. |
| **A transparência é suportada em versões antigas do Word?** | Sim. Aspose.Words grava o XML apropriado que o Word 2007+ entende. Versões mais antigas podem ignorar o valor de transparência, mas ainda mostrarão a sombra. |
| **Posso adicionar várias formas com sombras diferentes?** | Claro—basta criar novas instâncias de `Shape`, configurar cada sombra independentemente e anexá‑las aos nós desejados. |
| **E quanto ao desempenho com centenas de formas?** | Criar muitas formas pode aumentar o uso de memória. Reutilize uma única instância de `Document` e adicione as formas em um loop; descarte objetos temporários se houver pressão de recursos. |

## Dicas para Projetos Reais

- **Geração em lote:** Ao gerar relatórios para muitos usuários, instancie um único modelo `Document` e clone‑o para cada iteração. Substitua marcadores antes de anexar as formas.  
- **Dimensionamento dinâmico:** Use as dimensões da página (`document.FirstSection.PageSetup.PageWidth`) para calcular o tamanho da forma em relação à página, garantindo layout consistente em diferentes tamanhos de papel.  
- **Testes:** Sempre abra o `.docx` gerado no Word após alterar os parâmetros da sombra. O feedback visual é mais rápido que adivinhar números.

## Próximos Passos

Agora que você sabe **como adicionar shape retangular**, **como adicionar shadow** e **como definir transparency**, considere explorar:

- Adicionar **preenchimentos gradientes** às formas (`Shape.FillFormat`).  
- Incorporar **imagens** dentro das formas para efeitos de marca‑d’água.  
- Usar **tabelas** para alinhar várias formas sombreadas em grade.  
- Exportar o mesmo documento para PDF (`document.Save("output.pdf")`) mantendo as sombras.

Cada um desses itens se baseia nos mesmos conceitos centrais, então você se sentirá confortável em estender o código.

---

### Recapitulação

Começamos **criando um documento word** com Aspose.Words, depois **como criar shape** um retângulo, aplicamos **como adicionar shadow**, ajustamos **como definir transparency**, e salvamos o resultado. Todo o processo cabe em um padrão compacto e reutilizável que você pode adaptar a qualquer cenário de automação.

Sinta‑se à vontade para experimentar—alterar cores, brincar com deslocamentos ou empilhar várias formas. Quando encontrar algum obstáculo, volte às seções acima; elas foram projetadas como referência rápida. Boa codificação, e que seus documentos estejam sempre impecáveis!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}