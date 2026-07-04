---
category: general
date: 2026-04-10
description: como definir sombra em uma forma em C# – aprenda como aplicar sombra
  projetada, alterar transparência, ajustar desfoque e adicionar sombra à forma usando
  Aspose.Words.
draft: false
keywords:
- how to set shadow
- apply drop shadow
- how to change transparency
- how to adjust blur
- add shape shadow
language: pt
og_description: como definir sombra em uma forma em C# – este tutorial mostra como
  aplicar sombra projetada, mudar a transparência, ajustar o desfoque e adicionar
  sombra à forma com exemplos de código claros.
og_title: Como definir sombra em uma forma no C# – Guia Completo
tags:
- Aspose.Words
- C#
- Document Automation
title: como definir sombra em uma forma no C# – guia passo a passo
url: /pt/net/programming-with-shapes/how-to-set-shadow-on-a-shape-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# como definir sombra em uma forma em C# – Guia Completo

Já se perguntou **como definir sombra** em uma forma ao criar programaticamente um documento Word? Você não está sozinho. Muitos desenvolvedores encontram dificuldades quando precisam de uma sombra sutil para uma caixa de texto, um logotipo ou uma caixa de destaque, e a documentação da API parece um pouco escassa.  

Neste tutorial vamos percorrer todo o processo: desde carregar um `.docx`, obter a primeira `Shape`, aplicar uma sombra projetada, ajustar sua transparência, modificar o raio de desfoque e, finalmente, posicioná‑la corretamente. Ao final, você terá um trecho reutilizável que funciona com Aspose.Words .NET 2023 ou posterior, e entenderá *por que* cada propriedade é importante.

## O que você precisará

- **Aspose.Words for .NET** (pacote NuGet `Aspose.Words`) – a biblioteca que fornece as classes `Document`, `Shape` e `ShadowFormat`.  
- **.NET 6+** (ou .NET Framework 4.7.2) – qualquer runtime recente serve.  
- Um arquivo Word simples (`input.docx`) que já contenha ao menos uma forma, como uma caixa de texto.  
- Visual Studio, VS Code ou sua IDE favorita.

É isso. Sem ferramentas de terceiros adicionais, sem interop COM, apenas C# puro.

![how to set shadow example](image-placeholder.png){:alt="como definir sombra em uma forma em um documento Word"}

## Como definir sombra – Visão geral

A ideia central por trás de **como definir sombra** é manipular o objeto `ShadowFormat` que pertence a uma `Shape`. Pense no `ShadowFormat` como uma mini “folha de estilo” para a própria sombra: ele informa ao renderizador se a sombra está visível, qual cor deve ter, quão transparente está, o grau de desfoque e onde ela se posiciona em relação à forma.  

Abaixo está o programa *completo* executável. Sinta‑se à vontade para copiá‑lo e colá‑lo em um aplicativo de console, pressionar **F5** e observar a sombra aparecer no `output.docx` salvo.

```csharp
using System;
using System.Drawing;               // For Color
using Aspose.Words;                 // Core document classes
using Aspose.Words.Drawing;         // Shape & ShadowFormat

class ShadowDemo
{
    static void Main()
    {
        // -------------------------------------------------
        // Step 1: Load the Word document that contains the shape.
        // -------------------------------------------------
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // -------------------------------------------------
        // Step 2: Retrieve the first shape (e.g., a textbox) from the document.
        // -------------------------------------------------
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            Console.WriteLine("No shape found – make sure input.docx has a textbox.");
            return;
        }

        // -------------------------------------------------
        // Step 3: Make the shadow visible.
        // -------------------------------------------------
        shape.ShadowFormat.Visible = true;

        // -------------------------------------------------
        // Step 4: Set the shadow colour to a dark gray.
        // -------------------------------------------------
        shape.ShadowFormat.Color = Color.DarkGray;

        // -------------------------------------------------
        // Step 5: Define the shadow's transparency (30 % transparent).
        // -------------------------------------------------
        shape.ShadowFormat.Transparency = 0.3;   // 0 = opaque, 1 = fully transparent

        // -------------------------------------------------
        // Step 6: Configure the blur radius (size) of the shadow.
        // -------------------------------------------------
        shape.ShadowFormat.Size = 6;            // Larger value = softer edges

        // -------------------------------------------------
        // Step 7: Set the offset distance and direction (angle) of the shadow.
        // -------------------------------------------------
        shape.ShadowFormat.Distance = 2;        // How far the shadow is from the shape
        shape.ShadowFormat.Angle = 45;          // Angle in degrees (0 = right, 90 = down)

        // -------------------------------------------------
        // Save the modified document.
        // -------------------------------------------------
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Shadow applied successfully! Check output.docx.");
    }
}
```

### Por que essas configurações são importantes

- **Visible** – Sem ativar este sinalizador, todas as outras propriedades são ignoradas.  
- **Color** – Um cinza escuro imita uma sombra típica de UI; você pode substituir por qualquer `Color`.  
- **Transparency** – 0.3 fornece um aspecto *suave* mantendo a forma legível.  
- **Size** – Controla o desfoque; um valor de 6 costuma ser suficiente para um aspecto profissional.  
- **Distance & Angle** – Juntos definem o *offset*; 2 pts a 45° produzem uma sombra diagonal sutil.  

Essa é a essência de **como definir sombra**. Em seguida, vamos detalhar cada parte para que você possa **aplicar drop shadow**, **alterar transparência**, **ajustar desfoque** e **adicionar sombra à forma** isoladamente.

---

## Aplicar Drop Shadow a uma Forma

Quando as pessoas perguntam “como faço para **aplicar drop shadow** em C#?”, geralmente precisam apenas da alternância de visibilidade e de uma cor. O trecho a seguir isola essas duas linhas:

```csharp
shape.ShadowFormat.Visible = true;          // Turns the shadow on
shape.ShadowFormat.Color   = Color.Black;   // Classic black drop shadow
```

> **Dica de especialista:** Se você estiver direcionando versões mais antigas do Word (2003‑2007), mantenha cores padrão. Alguns valores ARGB exóticos podem ser ignorados pelo renderizador legado.

---

## Como alterar a transparência da sombra

A transparência é expressa como um **float entre 0 e 1**. Um valor de **0** significa uma sombra completamente opaca; **1** a torna invisível. A maioria dos designers costuma usar entre **0.2‑0.4** para um aspecto natural.

```csharp
shape.ShadowFormat.Transparency = 0.35; // 35 % transparent
```

### Casos de borda

- **Negative values** – Aspose.Words limitará a 0, mas é melhor validar a entrada.  
- **Values > 1** – Limitado a 1, ocultando efetivamente a sombra.  

Se precisar permitir que os usuários escolham uma porcentagem, converta‑a primeiro:

```csharp
float percent = 30;                     // User enters 30 %
shape.ShadowFormat.Transparency = percent / 100f;
```

---

## Como ajustar o desfoque (Size) da sombra

A propriedade **Size** controla o raio de desfoque. Números maiores produzem uma sombra mais suave e difusa. É medida em pontos (pt), não em pixels.

```csharp
shape.ShadowFormat.Size = 10;  // A generous blur for a “soft” effect
```

#### Quando usar um desfoque pequeno vs. grande

- **Small blur (2‑4 pt)** – Boa para chamadas de estilo UI onde se deseja uma borda nítida.  
- **Large blur (8‑12 pt)** – Funciona bem para relatórios impressos ou quando a forma está distante do plano de fundo.

---

## Adicionar sombra à forma – Posicionamento e direção

A última peça de **add shape shadow** é o offset. Duas propriedades trabalham juntas:

| Propriedade | Significado |
|-------------|-------------|
| **Distance** | Quão longe a sombra fica da forma (em pontos). |
| **Angle**    | Direção do offset (0° = direita, 90° = baixo, 180° = esquerda, 270° = cima). |

Exemplo que cria uma sombra sutil inferior‑direita:

```csharp
shape.ShadowFormat.Distance = 1.5; // Slight lift
shape.ShadowFormat.Angle    = 135; // Down‑left direction (135°)
```

Você pode experimentar ângulos para simular luz vindo de diferentes fontes. Um truque comum é permitir que o usuário escolha uma “fonte de luz” em um menu suspenso e mapeá‑la para um valor de ângulo.

---

## Exemplo completo em funcionamento (Todas as etapas combinadas)

Abaixo está o mesmo programa de antes, mas com **comentários extras** que deixam a lógica cristalina. Copie isso para `Program.cs` e execute; o arquivo de saída conterá uma caixa de texto com uma sombra perfeitamente ajustada.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeShadowDemo
{
    class Program
    {
        static void Main()
        {
            // Load the source document (must contain at least one shape)
            Document doc = new Document("YOUR_DIRECTORY/input.docx");

            // Grab the first shape we encounter – usually a textbox or picture
            Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
            if (shape == null)
            {
                Console.WriteLine("No shape found in the document.");
                return;
            }

            // ---------- Apply Drop Shadow ----------
            shape.ShadowFormat.Visible = true;          // Turn it on
            shape.ShadowFormat.Color   = Color.DarkGray; // Soft dark colour

            // ---------- How to Change Transparency ----------
            shape.ShadowFormat.Transparency = 0.3; // 30 % transparent – looks natural

            // ---------- How to Adjust Blur ----------
            shape.ShadowFormat.Size = 6; // Moderate blur for a professional feel

            // ---------- Add Shape Shadow (position) ----------
            shape.ShadowFormat.Distance = 2; // Slight offset
            shape.ShadowFormat.Angle    = 45; // Diagonal down‑right

            // Save the result
            doc.Save("YOUR_DIRECTORY/output.docx");
            Console.WriteLine("Document saved with shadow. Open output.docx to verify.");
        }
    }
}
```

**Resultado esperado:** Abra `output.docx`. A primeira caixa de texto exibirá uma sombra cinza escura, 30 % transparente, levemente desfocada (size = 6) e deslocada 2 pt em um ângulo de 45°. O efeito é sutil, mas perceptível — exatamente o que a maioria dos designers de UI busca.

---

## Perguntas frequentes e armadilhas

- **“Isso funciona com imagens também?”**  
  Sim. Qualquer `Shape` — seja caixa de texto, imagem ou auto‑forma — expõe `ShadowFormat`. Basta substituir a lógica de obtenção da forma pelo índice ou nome apropriado.

- **“E se o documento tiver várias formas?”**  
  Percorra `doc.GetChildNodes(NodeType.Shape, true)` e aplique as mesmas configurações a cada uma. Você também pode filtrar por `shape.Name` ou `shape

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}