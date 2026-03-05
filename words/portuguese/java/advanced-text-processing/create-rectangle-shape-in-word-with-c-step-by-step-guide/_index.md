---
category: general
date: 2026-03-04
description: Aprenda a criar uma forma retangular, adicionar sombra à forma e aplicar
  o efeito de sombra em um documento do Word, e então salvar o documento do Word automaticamente.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- apply shadow effect
- save word document
- create blank document
language: pt
og_description: Create rectangle shape, add shadow to shape and apply shadow effect
  in a Word document using C#. Follow this guide to save Word document effortlessly.
og_title: Criar forma de retângulo no Word – Tutorial completo de C#
tags:
- C#
- Aspose.Words
- Document Automation
title: Create rectangle shape in Word with C# – Step‑by‑Step Guide
url: /pt/java/advanced-text-processing/create-rectangle-shape-in-word-with-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar forma retangular no Word com C# – Tutorial de Programação Completo

Já precisou **criar forma retangular** em um arquivo Word mas não sabia por onde começar? Você não está sozinho—muitos desenvolvedores encontram essa barreira ao iniciar a geração programática de documentos. A boa notícia é que, com algumas linhas de C#, você pode inserir um retângulo, **adicionar sombra à forma**, e **aplicar efeito de sombra** sem nunca abrir o Word. Neste guia percorreremos todo o processo, desde um **criar documento em branco** até salvar o **salvar documento Word** final no disco.

Cobriremos tudo que você precisa: o pacote NuGet necessário, as APIs exatas, por que cada propriedade importa, e algumas dicas para evitar os erros mais comuns. Ao final, você terá um exemplo totalmente executável que pode ser inserido em qualquer projeto .NET.

## Pré‑requisitos

- .NET 6.0 ou superior (o código também funciona com .NET Framework 4.7+)
- Visual Studio 2022 ou qualquer IDE de sua preferência
- **Aspose.Words for .NET** instalado via NuGet (`Install-Package Aspose.Words`)
- Familiaridade básica com a sintaxe C#

Nenhuma biblioteca adicional de interoperação com Word é necessária—Aspose.Words cuida de tudo na memória.

## Etapa 1 – Criar um documento em branco

A primeira coisa que fazemos é **criar documento em branco**. Pense nele como a tela vazia onde mais tarde **criaremos forma retangular**.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1: Initialize a new blank document
Document doc = new Document();   // This gives us a fresh Word file
```

> **Por que isso importa:** Começar com um objeto `Document` limpo garante que nenhum estilo ou seção ocultos interfiram no posicionamento da forma posteriormente.

## Etapa 2 – Inserir uma forma retangular no documento

Agora realmente **criaremos forma retangular**. Definiremos seu tamanho, posicionamento e diremos ao Word para não envolver texto ao seu redor.

```csharp
// Step 2: Add a rectangle shape
Shape rectangle = new Shape(doc, ShapeType.Rectangle);
rectangle.Width = 200;          // Width in points (1 point = 1/72 inch)
rectangle.Height = 100;         // Height in points
rectangle.WrapType = WrapType.None; // No text wrapping
```

> **Dica profissional:** Se precisar que o retângulo fique dentro de uma célula de tabela, altere `WrapType` para `WrapType.Inline`. Na maioria dos relatórios, `None` mantém a forma flutuando acima do texto.

## Etapa 3 – Adicionar sombra à forma e configurar sua aparência

É aqui que a mágica acontece: **adicionamos sombra à forma** e **aplicamos efeito de sombra**. A sombra faz o retângulo se destacar na página, especialmente quando impresso.

```csharp
// Step 3: Enable shadow and set its properties
rectangle.ShadowFormat.Visible = true;          // Turn on the shadow
rectangle.ShadowFormat.BlurRadius = 5.0;        // Softness of the shadow edge
rectangle.ShadowFormat.Transparency = 0.3;      // 30 % transparent
rectangle.ShadowFormat.OffsetX = 8;             // Horizontal shift
rectangle.ShadowFormat.OffsetY = 8;             // Vertical shift
rectangle.ShadowFormat.Color = Color.Blue;     // Shadow colour
```

> **Por que esses valores?**  
> - **BlurRadius** controla o quão desfocados ficam os limites; um valor em torno de `5` oferece um aspecto sutil e profissional.  
> - **Transparency** permite que o texto subjacente permaneça legível.  
> - **OffsetX/Y** deslocam a sombra da forma, criando profundidade.  
> - Usar um tom **azul** é apenas um exemplo—qualquer `System.Drawing.Color` funciona.

## Etapa 4 – Adicionar a forma configurada ao corpo do documento

Com o retângulo totalmente estilizado, agora **adicionamos forma retangular** à primeira seção do documento. Esta etapa realmente coloca a forma no arquivo.

```csharp
// Step 4: Append the shape to the first section's body
doc.FirstSection.Body.AppendChild(rectangle);
```

> **Caso extremo:** Se seu documento já contém seções, talvez queira direcionar uma específica (`doc.Sections[2]`, por exemplo). O código acima funciona para um documento de seção única, que é comum em relatórios rápidos.

## Etapa 5 – Salvar o documento Word

Finalmente, **salvamos documento Word** no disco. O arquivo conterá o retângulo com sua sombra, pronto para ser aberto no Microsoft Word.

```csharp
// Step 5: Persist the document
string outputPath = @"C:\Temp\shadowed_rectangle.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

> **Dica:** Use `doc.Save(outputPath, SaveFormat.Docx)` se precisar ser explícito quanto ao formato. O método `Save` detecta a extensão automaticamente, mas ser explícito pode evitar confusões quando o caminho é gerado programaticamente.

## Exemplo Completo e Executável

Abaixo está o programa completo que você pode copiar‑colar em uma aplicação console. Ele inclui todas as instruções `using` e o método `Main`, para que você possa executá‑lo imediatamente.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a blank document
            Document doc = new Document();

            // 2️⃣ Create a rectangle shape
            Shape rectangle = new Shape(doc, ShapeType.Rectangle);
            rectangle.Width = 200;
            rectangle.Height = 100;
            rectangle.WrapType = WrapType.None;

            // 3️⃣ Apply shadow effect
            rectangle.ShadowFormat.Visible = true;
            rectangle.ShadowFormat.BlurRadius = 5.0;
            rectangle.ShadowFormat.Transparency = 0.3;
            rectangle.ShadowFormat.OffsetX = 8;
            rectangle.ShadowFormat.OffsetY = 8;
            rectangle.ShadowFormat.Color = Color.Blue;

            // 4️⃣ Insert the shape into the document body
            doc.FirstSection.Body.AppendChild(rectangle);

            // 5️⃣ Save the document
            string outputPath = @"C:\Temp\shadowed_rectangle.docx";
            doc.Save(outputPath);
            Console.WriteLine($"✅ Document saved at {outputPath}");
        }
    }
}
```

### Resultado Esperado

Ao abrir *shadowed_rectangle.docx* no Microsoft Word, você verá um retângulo com borda azul flutuando próximo ao topo da primeira página, com uma sombra azul suave deslocada 8 pt para a direita e para baixo. Nenhum texto extra o rodeia porque definimos `WrapType.None`.

## Perguntas Frequentes & Variações

| Pergunta | Resposta |
|----------|----------|
| **Posso mudar a forma para uma elipse?** | Sim—substitua `ShapeType.Rectangle` por `ShapeType.Ellipse`. Todas as propriedades de sombra permanecem iguais. |
| **E se eu precisar de várias formas?** | Basta repetir as Etapas 2‑4 para cada nova instância de `Shape`, ajustando `OffsetX/Y` ou `Left/Top` para evitar sobreposição. |
| **Existe como fazer a cor da sombra combinar com o preenchimento da forma?** | Absolutamente. Defina `rectangle.FillColor` primeiro, depois atribua `rectangle.ShadowFormat.Color = rectangle.FillColor;`. |
| **Como inserir a forma em uma célula de tabela?** | Use `cell.FirstParagraph.AppendChild(rectangle);` após localizar o objeto `Cell` desejado. |
| **Isso funciona no .NET Core?** | Sim—Aspose.Words é multiplataforma. Apenas certifique‑se de referenciar a versão correta do pacote NuGet para .NET Core/5/6. |

## Armadilhas Comuns & Dicas Profissionais

- **Armadilha:** Esquecer de definir `ShadowFormat.Visible = true`. As propriedades de sombra serão ignoradas silenciosamente.  
  **Correção:** Sempre habilite a visibilidade antes de ajustar outros parâmetros de sombra.

- **Armadilha:** Usar um `BlurRadius` muito grande (ex.: 20) pode deixar a sombra excessivamente desfocada e pouco profissional.  
  **Correção:** Mantenha valores entre `3` e `8` para a maioria dos documentos corporativos.

- **Dica profissional:** Se precisar que a forma seja selecionável posteriormente (ex.: para edição pelo usuário final), evite definir `WrapType.Inline`. Formas flutuantes (`WrapType.None`) são mais fáceis de mover programaticamente.

- **Dica profissional:** Ao gerar muitos documentos em um loop, reutilize uma única instância de `Document` e chame `doc.Clone(true)` para cada iteração, melhorando o desempenho.

## Tópicos Relacionados que Você Pode Explorar a Seguir

- **Adicionar texto dentro de uma forma retangular** – aprenda a usar `Shape.TextPath` para rótulos.  
- **Criar diagramas complexos** – combine múltiplas formas, conectores e agrupamentos.  
- **Exportar para PDF** – converta o mesmo documento para PDF com um único `doc.Save("output.pdf")`.  
- **Aplicar diferentes estilos de preenchimento** – gradientes, texturas ou até imagens dentro das formas.

## Conclusão

Acabamos de **criar forma retangular**, **adicionar sombra à forma**, e **aplicar efeito de sombra** em um arquivo Word usando C#. Seguindo as cinco etapas concisas, você agora tem um padrão reutilizável para qualquer cenário de automação de documentos, e sabe como **salvar documento Word** de forma confiável. Sinta‑se à vontade para ajustar dimensões, cores ou até trocar o retângulo por outra geometria—Aspose.Words torna tudo isso simples.

Se este tutorial foi útil, dê uma estrela no GitHub ou compartilhe suas próprias variações nos comentários. Boa codificação, e que seus documentos estejam sempre tão polidos quanto este retângulo sombreado!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}