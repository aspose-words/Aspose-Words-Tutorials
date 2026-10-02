---
category: general
date: 2026-03-06
description: Crie uma forma retangular no Word e adicione sombra à forma com Aspose.Words.
  Aprenda como inserir um retângulo no Word e como adicionar sombra à forma em C#.
draft: false
keywords:
- create rectangle shape
- add shape shadow
- how to insert rectangle in word
- how to add shadow to shape
language: pt
og_description: Crie uma forma retangular no Word e adicione sombra à forma com Aspose.Words.
  Guia passo a passo sobre como inserir um retângulo no Word e como adicionar sombra
  à forma.
og_title: Criar forma retangular com sombra no Word usando Aspose.Words
tags:
- Aspose.Words
- C#
- Word Automation
title: Criar forma retangular com sombra no Word usando Aspose.Words
url: /pt/net/programming-with-shapes/create-rectangle-shape-with-shadow-in-word-using-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar forma retangular com sombra no Word usando Aspose.Words

Já precisou **criar forma retangular** em um documento Word, mas não sabia como dar a ele um aspecto refinado? Você não está sozinho—a maioria dos desenvolvedores encontra o mesmo obstáculo ao tentar adicionar um toque visual a documentos automatizados. A boa notícia? Com Aspose.Words para .NET você pode tanto **criar forma retangular** quanto **adicionar sombra à forma** em apenas algumas linhas de C#.

Neste tutorial vamos percorrer exatamente **como inserir um retângulo no Word**, depois mostrar **como adicionar sombra à forma** para que ela se destaque na página. Ao final você terá um `Shadow.docx` pronto‑para‑salvar que pode abrir no Word e verá um retângulo com tonalidade cinza e uma sombra suave. Sem arquivos de imagem extras, sem ajustes manuais—apenas código.

## O que você aprenderá

- As declarações exatas em C# necessárias para **criar forma retangular** com Aspose.Words.  
- Como habilitar e configurar uma sombra usando o objeto `Shadow`.  
- Por que cada propriedade importa (por exemplo, `Transparency`, `Blur`, `Angle`).  
- Armadilhas comuns (unidades, compatibilidade de versão) e correções rápidas.  
- Um programa completo, pronto para copiar e colar, que você pode executar hoje.

### Pré-requisitos

- .NET 6+ (ou .NET Framework 4.7+).  
- Aspose.Words para .NET 23.10 ou posterior (o pacote NuGet é `Aspose.Words`).  
- Um entendimento básico de C# e Visual Studio (ou qualquer IDE de sua preferência).  

Se você já tem isso, vamos direto ao ponto.

---

## Etapa 1: Configurar o projeto e importar namespaces

Primeiro, crie um novo aplicativo console (ou reutilize um existente) e adicione o pacote NuGet Aspose.Words:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

Agora importe os namespaces necessários no seu `Program.cs`:

```csharp
using System.Drawing;               // For Color
using Aspose.Words;                  // Core document classes
using Aspose.Words.Drawing;          // Shape and Shadow types
```

> **Dica profissional:** Se você está direcionando o .NET 6+, pode habilitar diretivas globais `using` para evitar repetir essas linhas em cada arquivo.

---

## Etapa 2: **Criar forma retangular** em um documento Word em branco

Começaremos com um novo objeto `Document` e um `DocumentBuilder` para manipulá-lo. O método `InsertShape` do builder é onde a mágica acontece.

```csharp
// Step 2: Initialize a new document and builder
Document document = new Document();                     // Blank Word file
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a rectangle – 200 × 100 points (≈2.78 × 1.39 inches)
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

Por que 200 × 100 pontos? No Word, um ponto equivale a 1/72 de polegada, então o retângulo fica aproximadamente 2,8 × 1,4 polegadas—grande o suficiente para ser notado, mas não excessivo. Você pode mudar esses números para se adequar ao seu layout; apenas lembre‑se de que eles são medidos em **pontos**, não em pixels.

---

## Etapa 3: **Adicionar sombra à forma** – configurando a aparência

Agora que temos um retângulo, vamos dar-lhe uma sombra cinza sutil. O objeto `Shadow` está associado ao `Shape` e expõe várias propriedades úteis.

```csharp
// Step 3: Turn on the shadow and tweak its appearance
rectangle.Shadow.Enabled = true;               // Switch the shadow on
rectangle.Shadow.Color = Color.Gray;           // Shadow hue
rectangle.Shadow.Transparency = 0.3;           // 30 % transparent – looks softer
rectangle.Shadow.Blur = 5;                     // Blur radius (points)
rectangle.Shadow.Distance = 4;                 // How far the shadow sits from the shape
rectangle.Shadow.Angle = 45;                   // Direction in degrees (45° = down‑right)
rectangle.Shadow.Size = 100;                   // 100 % of the original shape size
```

### O que cada propriedade faz

| Propriedade | Efeito | Valores típicos |
|-------------|--------|-----------------|
| **Enabled** | Liga ou desliga a sombra | `true` ou `false` |
| **Color** | Cor base da sombra | Qualquer `System.Drawing.Color` |
| **Transparency** | Opacidade (0 = sólido, 1 = invisível) | 0.0 – 1.0 |
| **Blur** | Suavidade da borda | 0 – 10 (mais alto = mais suave) |
| **Distance** | Espaço entre a forma e a sombra | 0 – 20 pontos |
| **Angle** | Direção da luz aparente | 0 – 360 graus |
| **Size** | Escala da sombra em relação à forma | 0 – 200 % |

> **Por que se preocupar com essas configurações?**  
> Ajustar finamente a sombra permite que você siga as diretrizes de identidade visual da empresa (por exemplo, 20 % de transparência sutil para um visual profissional) sem precisar de editores de imagem externos.

---

## Etapa 4: Salvar o documento e verificar o resultado

Finalmente, escreva o arquivo no disco. Você pode escolher qualquer pasta que desejar; basta substituir `YOUR_DIRECTORY` por um caminho real.

```csharp
// Step 4: Persist the document
string outputPath = Path.Combine(Environment.CurrentDirectory, "Shadow.docx");
document.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

Abra `Shadow.docx` no Microsoft Word e você deverá ver um retângulo cinza com uma sombra suave deslocada em um ângulo de 45°. Esse detalhe visual faz a forma parecer “elevada” da página—exatamente o que se espera de um relatório ou fatura bem acabados.

---

## Exemplo completo em funcionamento

Abaixo está o programa completo que você pode copiar e colar em `Program.cs`. Nenhuma parte está faltando; ele compila e executa como está.

```csharp
using System;
using System.Drawing;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Insert a rectangle shape (200 × 100 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // 3️⃣ Enable the shape's shadow and configure its appearance
        rectangle.Shadow.Enabled = true;               // Turn the shadow on
        rectangle.Shadow.Color = Color.Gray;           // Shadow colour
        rectangle.Shadow.Transparency = 0.3;           // 30 % transparent
        rectangle.Shadow.Blur = 5;                     // Blur radius
        rectangle.Shadow.Distance = 4;                 // Offset from the shape
        rectangle.Shadow.Angle = 45;                   // Direction in degrees
        rectangle.Shadow.Size = 100;                   // Shadow size as a percentage

        // 4️⃣ Save the document with the shadowed shape
        string outputPath = Path.Combine(Environment.CurrentDirectory, "Shadow.docx");
        document.Save(outputPath);
        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

### Saída esperada

- **Arquivo:** `Shadow.docx` colocado na pasta de execução do projeto.  
- **Visual:** Um único retângulo centralizado na página, preenchido com o branco padrão, e uma sombra cinza deslocada 4 pontos para a parte inferior‑direita, levemente desfocada para um aspecto natural.

---

## Perguntas comuns e casos limites

### 1. E se eu precisar de outra unidade (por exemplo, centímetros)?

Aspose.Words trabalha em pontos, mas você pode converter centímetros para pontos com a fórmula simples:  
`points = centimeters * 28.3465`.  

```csharp
double cmWidth = 5.0; // 5 cm
double cmHeight = 2.5; // 2.5 cm
Shape rectCm = builder.InsertShape(ShapeType.Rectangle,
                                   (float)(cmWidth * 28.3465),
                                   (float)(cmHeight * 28.3465));
```

### 2. Isso funciona com versões mais antigas do Aspose.Words?

A API `Shadow` foi introduzida na versão 14.0. Se você estiver usando uma versão mais antiga, precisará atualizar via NuGet. O restante do código (criação de formas) tem sido estável por muitos anos, portanto você não encontrará mudanças incompatíveis.

### 3. Posso adicionar sombra a outras formas (por exemplo, círculos)?

Absolutamente—qualquer objeto `Shape` expõe a propriedade `Shadow`. Basta substituir `ShapeType.Rectangle` por `ShapeType.Ellipse` ou `ShapeType.Cloud`, e então aplicar as mesmas configurações de sombra.

### 4. E se eu precisar de uma sombra colorida (por exemplo, azul para uma marca)?

Troque `Color.Gray` por qualquer `Color` que desejar:

```csharp
rectangle.Shadow.Color = Color.FromArgb(30, 0, 120); // Dark blue
```

Lembre‑se de ajustar `Transparency` para que a cor não se torne dominante.

---

## 🎨 Resumo visual

![criar forma retangular com sombra no Word usando Aspose.Words](image-placeholder.png "criar forma retangular com sombra no Word usando Aspose.Words")

*Texto alternativo: criar forma retangular com sombra no Word usando Aspose.Words*

A captura de tela (marcador) mostra o documento final—apenas o retângulo e sua sombra cinza suave.

---

## Conclusão

Agora você sabe como **criar forma retangular** em um arquivo Word, **adicionar sombra à forma**, e ajustar finamente cada aspecto visual usando Aspose.Words para .NET. O pequeno programa que construímos cobre todo o fluxo de trabalho—from

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}