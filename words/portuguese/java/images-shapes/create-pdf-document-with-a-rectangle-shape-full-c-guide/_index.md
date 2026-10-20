---
category: general
date: 2026-03-25
description: Crie um documento PDF em C# e aprenda a adicionar uma forma retangular,
  definir a cor de preenchimento, ajustar o tamanho da forma e definir a transparência
  da forma em apenas alguns passos.
draft: false
keywords:
- create pdf document
- set shape transparency
- add rectangle shape
- set fill color
- set shape size
language: pt
og_description: Crie um documento PDF em C# e veja como adicionar um retângulo, definir
  sua cor de preenchimento, tamanho e transparência para um PDF refinado.
og_title: Criar documento PDF com forma retangular – Tutorial C#
tags:
- C#
- PDF
- Aspose.Words
title: Criar documento PDF com forma retangular – Guia completo em C#
url: /pt/java/images-shapes/create-pdf-document-with-a-rectangle-shape-full-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar Documento PDF com uma Forma Retangular – Guia Completo em C#

Já precisou **criar um documento PDF** que contenha uma forma com estilo personalizado, mas não sabia por onde começar? Você não está sozinho. Seja construindo um gerador de relatórios ou um folheto de marketing, poder desenhar programaticamente um retângulo, definir sua cor de preenchimento, ajustar seu tamanho e ainda controlar sua transparência pode deixar seus PDFs muito mais profissionais.

Neste tutorial vamos percorrer um exemplo completo, pronto‑para‑executar em C# que **cria um documento PDF**, **adiciona uma forma retangular**, **define a cor de preenchimento**, **especifica o tamanho da forma** e **configura a transparência da forma** para uma sombra externa sutil. Ao final você terá um único arquivo PDF (`shadow.pdf`) que pode abrir para ver o resultado.

> **Dica profissional:** A mesma abordagem funciona com outros tipos de forma (elipse, linha, etc.) — basta trocar `ShapeType.RECTANGLE` pelo tipo desejado.

---

## O que você precisará

| Pré-requisito | Por que isso importa |
|--------------|----------------------|
| **.NET 6+** (ou .NET Framework 4.6+) | A biblioteca Aspose.Words tem como alvo runtimes modernos. |
| **Aspose.Words for .NET** pacote NuGet | Fornece `Document`, `Shape`, `ShadowEffect` e classes relacionadas. |
| **Um IDE C#** (Visual Studio, Rider, VS Code) | Torna a depuração e a execução do exemplo mais simples. |
| **Conhecimento básico de C#** | Você entenderá a sintaxe sem precisar de um mergulho profundo. |

Você pode instalar a biblioteca via linha de comando:

```bash
dotnet add package Aspose.Words
```

É isso — sem DLLs extras, sem dependências nativas. Uma vez que o pacote esteja instalado, o código abaixo compilará e será executado.

---

## Implementação passo a passo

A seguir dividimos o processo em cinco etapas lógicas. Cada etapa tem um título claro (para que modelos de IA possam indexá‑las) e um pequeno bloco de código que você pode copiar‑colar diretamente.

### ## 1. Criar Documento PDF e Preparar a Tela

A primeira coisa que fazemos é instanciar um `Document`. Pense nele como uma tela em branco que, ao final, se tornará seu arquivo PDF.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new empty document – this is the PDF document we will build.
        Document document = new Document();

        // The rest of the steps follow inside this method.
```

> **Por quê?** `Document` contém todas as seções, parágrafos e formas. Começar com um objeto limpo garante que não haja artefatos ocultos de execuções anteriores.

### ## 2. Adicionar Forma Retangular – Definir Cor de Preenchimento e Tamanho da Forma

Agora criamos um retângulo, atribuímos a ele um preenchimento amarelo vibrante e definimos suas dimensões. Isso cobre **add rectangle shape**, **set fill color** e **set shape size**.

```csharp
        // Step 2: Create a rectangle shape.
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);

        // Set the width and height – this is where we set the shape size.
        rectangle.Width = 200;   // 200 points (≈2.78 inches)
        rectangle.Height = 100;  // 100 points (≈1.39 inches)

        // Apply a fill color – here we use a vivid yellow.
        rectangle.FillColor = Color.Yellow;
```

> **Observação:** Largura/altura são medidas em pontos (1 ponto = 1/72 polegada). Ajuste esses valores para se adequar ao seu layout.

### ## 3. Aplicar uma Sombra Externa e Definir Transparência da Forma

Sombras adicionam profundidade, e controlar sua opacidade é a essência de **set shape transparency**. Abaixo configuramos uma sombra externa cinza com 30 % de transparência.

```csharp
        // Step 3: Configure the outer shadow effect.
        ShadowEffect shadow = rectangle.ShadowEffect;
        shadow.Color = Color.Gray;          // Shadow hue
        shadow.BlurRadius = 5.0;            // How fuzzy the shadow appears
        shadow.DistanceX = 4;               // Horizontal offset
        shadow.DistanceY = 4;               // Vertical offset
        shadow.Transparency = 0.3;          // 0 = opaque, 1 = fully transparent
        shadow.Style = ShadowStyle.Outer;   // Make it an outer shadow
```

> **Por que definir transparência?** Uma sombra com 30 % de transparência fica sutil, evitando que o retângulo pareça “plano” na página.

### ## 4. Inserir a Forma no Corpo do Documento

Agora colocamos o retângulo no primeiro parágrafo da primeira seção do documento. Esta etapa une tudo.

```csharp
        // Step 4: Insert the rectangle into the first paragraph.
        // If the document has no paragraphs yet, Aspose creates one automatically.
        Paragraph firstParagraph = document.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(rectangle);
```

> **Caso especial:** Se precisar da forma em uma nova página, adicione `document.Sections[0].PageSetup.SectionStart = SectionStart.NewPage;` antes de anexar a forma.

### ## 5. Salvar o Documento como Arquivo PDF

Por fim, persistimos a estrutura em memória em um arquivo PDF físico. O arquivo será gravado na pasta que você especificar.

```csharp
        // Step 5: Save the document as a PDF.
        string outputPath = @"YOUR_DIRECTORY\shadow.pdf";
        document.Save(outputPath, SaveFormat.Pdf);

        Console.WriteLine($"PDF saved successfully to {outputPath}");
    }
}
```

Ao executar o programa, um arquivo chamado `shadow.pdf` aparecerá. Ao abri‑lo, você verá um retângulo amarelo com uma sombra cinza suave deslocada em 4 pontos — exatamente o que nosso código descreveu.

> **Saída esperada:** Um PDF de página única onde o retângulo está próximo ao canto superior‑esquerdo da página, preenchido de amarelo, com tamanho de 200 × 100 pontos, e com uma sombra externa semi‑transparente.

---

## Exemplo Completo Funcional (Pronto para Copiar e Colar)

A seguir está o arquivo fonte completo, pronto para ser inserido em um novo projeto de console.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new empty document – this will become the PDF.
        Document document = new Document();

        // 2️⃣ Add a rectangle shape, set its size and fill color.
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.Width = 200;          // shape size – width
        rectangle.Height = 100;         // shape size – height
        rectangle.FillColor = Color.Yellow; // set fill color

        // 3️⃣ Apply an outer shadow and adjust transparency.
        ShadowEffect shadow = rectangle.ShadowEffect;
        shadow.Color = Color.Gray;
        shadow.BlurRadius = 5.0;
        shadow.DistanceX = 4;
        shadow.DistanceY = 4;
        shadow.Transparency = 0.3;      // set shape transparency
        shadow.Style = ShadowStyle.Outer;

        // 4️⃣ Insert the shape into the first paragraph of the document.
        Paragraph firstParagraph = document.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(rectangle);

        // 5️⃣ Save everything as a PDF.
        string outputPath = @"YOUR_DIRECTORY\shadow.pdf";
        document.Save(outputPath, SaveFormat.Pdf);

        Console.WriteLine($"PDF created at: {outputPath}");
    }
}
```

> **Dica:** Substitua `YOUR_DIRECTORY` por um caminho absoluto como `C:\Temp` ou um caminho relativo como `.\output`. O programa criará a pasta caso ela ainda não exista.

---

## Perguntas Frequentes (FAQ)

**Q: Posso mudar a posição do retângulo na página?**  
A: Claro. Defina `rectangle.Left` e `rectangle.Top` (ambos medidos em pontos) antes de anexá‑lo ao parágrafo.

**Q: E se eu precisar de um preenchimento transparente em vez de uma sombra transparente?**  
A: Use `rectangle.FillColor = Color.FromArgb(128, Color.Yellow);` — o primeiro argumento é o canal alfa (0‑255), onde 128 gera aproximadamente 50 % de transparência.

**Q: Isso funciona com .NET Core?**  
A: Sim. Aspose.Words suporta .NET Standard 2.0+, então você pode executar o mesmo código no .NET 6, .NET 7 ou .NET Framework 4.6+.

**Q: Como adicionar várias formas?**  
A: Basta repetir as etapas 2‑4 para cada forma, inserindo‑as em diferentes parágrafos ou seções, se desejar.

---

## Conclusão

Acabamos de **criar um documento PDF** do zero, **adicionar uma forma retangular**, **definir sua cor de preenchimento**, **especificar seu tamanho** e **ajustar a transparência da forma** para obter um efeito de sombra refinado. O código de exemplo é autocontido, roda em menos de um minuto e demonstra os conceitos principais que você precisará para layouts PDF mais elaborados.

Pronto para o próximo desafio? Experimente trocar o retângulo por uma forma com cantos arredondados, inserir uma imagem dentro da forma ou gerar um índice automaticamente. A mesma API permite sobrepor texto, imagens e vetores — o céu é o limite.

Se este guia foi útil, dê uma estrela no GitHub, compartilhe com um colega ou deixe um comentário com suas próprias variações. Boa codificação! 

---

![criar documento pdf com exemplo de forma retangular](/images/rectangle-shadow.png "Captura de tela mostrando o PDF criado com um retângulo amarelo e sombra externa cinza")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}