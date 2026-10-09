---
category: general
date: 2026-03-19
description: Crie um documento Word em C# com Aspose.Words, aprenda a adicionar formas,
  inserir uma forma retangular, aplicar sombra e salvar o documento como docx em minutos.
draft: false
keywords:
- create word document
- how to add shape
- add rectangle shape
- save document as docx
- add shadow to shape
language: pt
og_description: Crie um documento Word com Aspose.Words, adicione uma forma retangular,
  aplique sombra externa e salve o documento como docx. Guia passo a passo.
og_title: Criar documento do Word – Adicionar forma retangular e sombra
tags:
- Aspose.Words
- C#
- Document Automation
title: Criar documento Word – Como adicionar forma retângulo e sombra
url: /pt/net/programming-with-shapes/create-word-document-how-to-add-rectangle-shape-and-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar Documento Word – Como Adicionar Forma Retangular e Sombra

Já precisou **create word document** programaticamente e se perguntou por onde começar? Você não está sozinho. Muitos desenvolvedores enfrentam o mesmo obstáculo ao tentar gerar um arquivo .docx que contenha gráficos personalizados. Neste tutorial, percorreremos todo o processo — como adicionar forma, especificamente um **add rectangle shape**, dar a ela uma elegante **add shadow to shape**, e finalmente **save document as docx**.  

Ao final do guia, você terá um trecho de C# pronto‑para‑usar que pode inserir em qualquer projeto .NET. Sem referências vagas, apenas um exemplo completo e executável.  

## Pré-requisitos

- .NET 6.0 ou posterior (o código funciona também com .NET Framework).  
- Aspose.Words for .NET instalado (pacote NuGet `Aspose.Words`).  
- Um entendimento básico da sintaxe C# — nada sofisticado necessário.  

Se você não tem a biblioteca, execute:

```bash
dotnet add package Aspose.Words
```

É isso — sem SDKs extras, sem interop COM, apenas uma única referência NuGet.

---

## Etapa 1: Criar um Documento Word (Objetivo Principal)

A primeira coisa que precisamos é uma tela limpa. Pense na classe `Document` como uma página nova no Microsoft Word; ela contém seções, parágrafos e tudo o mais que você adicionará depois.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // For Color

// Step 1: Initialize a new blank document
Document doc = new Document();               // This creates an empty .docx in memory
```

Por que começar com um `Document` em branco? Porque garante que nenhuma formatação oculta se infiltre a partir de um modelo. Na minha experiência, começar do zero evita mudanças misteriosas de layout quando você insere formas posteriormente.

---

## Etapa 2: Inserir uma Forma Retangular – Adicionando o Elemento Visual

Agora que temos um documento, vamos **add rectangle shape** ao primeiro parágrafo. O objeto `Shape` é versátil; você pode escolher `ShapeType.Rectangle`, `Ellipse` ou até desenhos personalizados. Aqui está o código mínimo:

```csharp
// Step 2: Create a rectangle and attach it to the first paragraph
Shape rect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,               // Width in points (≈2.78 inches)
    Height = 100,              // Height in points (≈1.39 inches)
    WrapType = WrapType.Inline // Makes the shape behave like a character
};

// Append the shape to the first paragraph (creates one if missing)
Paragraph firstPara = doc.FirstSection.Body.FirstParagraph;
firstPara.AppendChild(rect);
```

> **O que está acontecendo nos bastidores?**  
> - `ShapeType.Rectangle` informa ao Aspose que queremos uma caixa simples.  
> - `WrapType.Inline` garante que o retângulo se mova com o fluxo de texto, que geralmente é o esperado em um cenário de processamento de texto.  
> - Ao anexar a `FirstParagraph`, evitamos a necessidade de inserir manualmente um novo parágrafo; o Aspose cria um para nós se o documento estiver realmente vazio.  

> **Dica profissional:** Se precisar que a forma fique *por trás* do texto, altere `WrapType` para `WrapType.Transparent`. Essa pequena mudança pode fazer uma enorme diferença visual.

---

## Etapa 3: Aplicar uma Sombra Externa – Melhorando a Aparência

Um retângulo plano é… bem, plano. Adicionar um **add shadow to shape** lhe confere profundidade sem imagens extras. O `ShadowFormat` da Aspose torna isso uma única linha.

```csharp
// Step 3: Configure an outer shadow for the rectangle
rect.ShadowFormat.Type = ShadowType.OuterShadow;
rect.ShadowFormat.Blur = 5.0;           // Softness of the shadow edge
rect.ShadowFormat.Distance = 3.0;      // How far the shadow is offset
rect.ShadowFormat.Angle = 45;          // Direction in degrees (45° = bottom‑right)
rect.ShadowFormat.Color = Color.Gray; // Classic gray shadow
```

Por que usar esses valores específicos?  
- **Blur** de `5.0` fornece uma borda suavemente esbatida que parece profissional na maioria dos monitores.  
- **Distance** de `3.0` e **Angle** de `45` criam uma fonte de luz natural a partir do canto superior esquerdo, uma convenção de design comum.  
- **Color.Gray** funciona tanto em temas claros quanto escuros; você pode trocá-lo por `Color.Black` se precisar de contraste maior.  

Se precisar de uma sombra *interna* (pense em um botão rebaixado), basta mudar `ShadowType.OuterShadow` para `ShadowType.InnerShadow`. As mesmas propriedades ainda se aplicam.

---

## Etapa 4: Salvar o Documento como DOCX – Persistindo seu Trabalho

Toda a diversão é ótima, mas você eventualmente desejará um arquivo no disco. A etapa **save document as docx** é simples:

```csharp
// Step 4: Persist the document to a .docx file
string outputPath = @"C:\Temp\ShadowedRectangle.docx";
doc.Save(outputPath, SaveFormat.Docx);
```

Algumas observações:  
- O enum `SaveFormat.Docx` garante o formato moderno Office Open XML, compatível com Word 2007+.  
- Se precisar transmitir o arquivo diretamente para uma resposta web, substitua o caminho do arquivo por um `MemoryStream` e escreva‑o na resposta HTTP.  

Depois de executar o código, abra `ShadowedRectangle.docx` no Microsoft Word. Você deverá ver um retângulo cinza com uma sombra suave, posicionado inline com o primeiro parágrafo — exatamente o que pretendíamos alcançar.

---

## Como Adicionar Forma – Abordagens Alternativas

O exemplo acima usa a abordagem *inline*, mas às vezes você quer uma forma que flutue sobre o texto. É aí que **how to add shape** com diferentes tipos de quebra de linha entra em ação.

```csharp
Shape floatingRect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 250,
    Height = 120,
    WrapType = WrapType.Square, // Allows text to wrap around the shape
    RelativeHorizontalPosition = RelativeHorizontalPosition.Page,
    HorizontalAlignment = HorizontalAlignment.Center
};

doc.FirstSection.Body.FirstParagraph.AppendChild(floatingRect);
```

Aqui alteramos `WrapType` para `Square` e centralizamos a forma na página. Esse padrão é útil para capas ou banners decorativos. Lembre‑se: formas flutuantes aumentam ligeiramente o tamanho do arquivo porque o Word armazena dados de posicionamento adicionais.

---

## Saída Esperada & Verificação

Ao abrir o arquivo gerado, você deverá ver:

- Um único parágrafo contendo um retângulo cinza.  
- O retângulo medindo aproximadamente 2,8 × 1,4 polegadas.  
- Uma sutil sombra externa deslocada para a parte inferior‑direita.  

Se a forma aparecer *fora* do parágrafo, verifique novamente o `WrapType`. Se a sombra parecer muito forte, diminua o valor de `Blur` ou troque o `Color` por um tom mais claro.

---

## Armadilhas Comuns & Como Evitá‑las

| Problema | Por que acontece | Correção |
|----------|------------------|----------|
| Forma desaparece após salvar | `WrapType` definido como `Inline` mas o parágrafo foi removido | Garanta que o parágrafo exista; use `doc.FirstSection.Body.FirstParagraph` para assegurá‑lo. |
| Sombra parece pixelada | Uso de um valor de `Blur` muito baixo | Aumente `Blur` para pelo menos `3.0` para bordas suaves. |
| Tamanho do arquivo inflaciona | Adicionar muitas imagens de alta resolução junto com formas | Use `doc.RemoveUnusedResources()` antes de salvar se você adicionou imagens. |
| Cor não aparece no modo escuro | Uso de um `Color` escuro para a própria forma | Escolha uma cor contrastante (ex.: `Color.White`) para melhor visibilidade. |

---

## Exemplo Completo Funcional

Abaixo está o código completo, pronto para copiar e colar, que incorpora tudo o que discutimos. Sinta‑se à vontade para executá‑lo como um aplicativo de console.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank Word document
        Document doc = new Document();

        // 2️⃣ Add a rectangle shape to the first paragraph
        Shape rect = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 200,
            Height = 100,
            WrapType = WrapType.Inline
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(rect);

        // 3️⃣ Apply an outer shadow to the rectangle
        rect.ShadowFormat.Type = ShadowType.OuterShadow;
        rect.ShadowFormat.Blur = 5.0;
        rect.ShadowFormat.Distance = 3.0;
        rect.ShadowFormat.Angle = 45;
        rect.ShadowFormat.Color = Color.Gray;

        // 4️⃣ Save the document as a .docx file
        string outPath = @"C:\Temp\ShadowShape.docx";
        doc.Save(outPath, SaveFormat.Docx);

        // Optional: Let the user know we’re done
        System.Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**Explicação de cada bloco** está inline como comentários, atendendo tanto leitores de SEO quanto assistentes de IA que adoram respostas autossuficientes.

---

## Conclusão

Acabamos de **create word document** do zero, aprendemos **how to add shape**, especificamente um **add rectangle shape**, lhe demos um **add shadow to shape**, e finalmente **save document as docx**. Os passos são simples, o código é compacto, e o resultado parece refinado.  

Se você está pronto para avançar, experimente substituir o retângulo por uma imagem personalizada, experimente diferentes cores de sombra, ou gere um relatório completo com várias seções em forma. A API Aspose.Words é flexível o suficiente para lidar com tudo, desde faturas até brochuras de marketing.  

Tem perguntas sobre outros tipos de forma ou precisa de ajuda para integrar isso em um serviço ASP.NET Core? Deixe um comentário abaixo, e feliz codificação! 

![create word document with rectangle shape and shadow](placeholder-image.png "create word document with rectangle shape and shadow

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}