---
category: general
date: 2026-01-13
description: Crie um documento Word usando Aspose.Words e aprenda como inserir uma
  forma retangular, como adicionar sombra e como adicionar sombra à forma em C#. Exemplo
  completo incluído.
draft: false
keywords:
- create word document
- insert rectangle shape
- how to add shadow
- how to insert shape
- add shape shadow
language: pt
og_description: Crie um documento Word com Aspose.Words, veja como inserir uma forma
  retangular e como adicionar sombra. Siga o exemplo completo em C#.
og_title: Criar documento Word com um retângulo sombreado – tutorial completo
tags:
- Aspose.Words
- C#
- Document Automation
title: Criar documento Word com um retângulo sombreado – Guia passo a passo
url: /pt/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar Documento Word com um Retângulo com Sombra – Guia Passo a Passo

Já precisou **criar documento word** que contenha um retângulo bem sombreado, mas não sabia por onde começar? Você não está sozinho — muitos desenvolvedores encontram o mesmo obstáculo ao começar a usar o Aspose.Words.  

Neste tutorial vamos percorrer tudo o que você precisa para **criar documento word** programaticamente, **inserir forma de retângulo**, e mostrar **como adicionar sombra** para que a forma realmente se destaque. Ao final, você terá um trecho de código C# pronto para executar que pode ser inserido em qualquer projeto .NET.

## O que você aprenderá

- O código exato para **como inserir forma** (um retângulo) em um arquivo Word.
- As propriedades que você deve ajustar para **adicionar sombra à forma** e controlar sua aparência.
- Como salvar o resultado e verificar se a sombra está visível.
- Algumas dicas práticas e notas de casos extremos que evitam dores de cabeça posteriores.

Nenhuma documentação externa necessária — tudo está aqui.

## Pré‑requisitos

Antes de mergulharmos, certifique‑se de que você tem:

1. **.NET 6.0** (ou qualquer versão recente do .NET) instalado.  
2. Uma **licença** para Aspose.Words for .NET, ou você pode usar o modo de avaliação gratuito para testes.  
3. Um ambiente de desenvolvimento — Visual Studio 2022 funciona muito bem, mas qualquer editor que possa compilar C# serve.

É isso. Nenhum pacote NuGet extra além de `Aspose.Words` é necessário.

## Etapa 1 – Configurar o Projeto e Referenciar Aspose.Words

Primeiro, crie um novo aplicativo console e adicione o pacote Aspose.Words:

```bash
dotnet new console -n ShadowRectangleDemo
cd ShadowRectangleDemo
dotnet add package Aspose.Words
```

> **Dica profissional:** Se você estiver usando a versão de avaliação gratuita, lembre‑se de chamar `License.SetLicense` com seu arquivo de licença; caso contrário, a biblioteca adicionará uma marca d'água.

## Etapa 2 – Inicializar o Document Builder

Agora vamos iniciar o processo real de **criar documento word**. A classe `Document` nos fornece uma tela em branco, e `DocumentBuilder` nos permite pintar nela.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing; // For Color

// Initialise a new blank document
Document document = new Document();

// Initialise a builder to start adding content
DocumentBuilder builder = new DocumentBuilder(document);
```

Por que precisamos de um builder? Ele abstrai os detalhes de baixo nível do OpenXML, permitindo que você se concentre no *o que* deseja em vez de *como* o arquivo está estruturado. Este é o núcleo de **como inserir forma** rapidamente.

## Etapa 3 – Inserir Forma de Retângulo

É aqui que realmente **inserimos forma de retângulo**. O retângulo terá 150 × 100 pontos (aproximadamente 2 pol × 1,3 pol).

```csharp
// Insert a rectangle shape at the current cursor position
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 100);
```

O método `InsertShape` retorna um objeto `Shape`, que podemos personalizar ainda mais. Neste ponto, o retângulo é apenas uma caixa branca sólida — ainda sem sombra.

## Etapa 4 – Como Adicionar Sombra (Adicionar Sombra à Forma)

Adicionar uma sombra é surpreendentemente simples quando você sabe quais propriedades ajustar. O objeto `ShadowFormat` controla visibilidade, cor, desfoque, deslocamento e tamanho.

```csharp
// Make the shadow visible
rectangleShape.ShadowFormat.Visible = true;

// Choose a subtle gray tone
rectangleShape.ShadowFormat.Color = Color.Gray;

// Set 30 % transparency – the shadow will be faint but noticeable
rectangleShape.ShadowFormat.Transparency = 0.3;

// Offset the shadow 5 points right and 5 points down
rectangleShape.ShadowFormat.OffsetX = 5;
rectangleShape.ShadowFormat.OffsetY = 5;

// Soften the edges with a blur radius of 4 points
rectangleShape.ShadowFormat.BlurRadius = 4;

// Scale the shadow to 75 % of the shape size (percentage)
rectangleShape.ShadowFormat.Size = 75;
```

Esse bloco responde **como adicionar sombra** em linguagem simples: habilite, escolha uma cor, ajuste a transparência, deslocamento, desfoque e tamanho. Você pode experimentar esses valores para obter uma sombra pesada ou uma sombra sutil.

### Variações Comuns

- **Cores diferentes:** Use `Color.Black` para uma sombra clássica, ou `Color.BlueViolet` para um efeito estilizado.  
- **Desfoque zero:** Defina `BlurRadius = 0` para uma borda nítida e afiada.  
- **Deslocamentos maiores:** Aumente `OffsetX`/`OffsetY` para afastar a sombra da forma.

## Etapa 5 – Salvar o Documento e Verificar

Finalmente, grave o documento no disco. O arquivo será um `.docx` padrão que qualquer processador de texto moderno pode abrir.

```csharp
// Save the document to the desired folder
string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowRectangle.docx");
document.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

Abra o *ShadowRectangle.docx* resultante no Microsoft Word. Você deverá ver um retângulo com uma sombra cinza suave deslocada para a parte inferior‑direita — exatamente o que o código especificou.

> **Saída esperada:** Um arquivo Word de uma única página contendo um retângulo de 150 × 100 pontos com uma sombra cinza 30 % transparente, deslocada 5 pts, desfocada 4 pts, e dimensionada em 75 % da forma.

## Exemplo Completo Funcional

Juntando tudo, aqui está o programa completo, pronto para executar:

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialise a new blank document
        Document document = new Document();

        // 2️⃣ Create a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Insert a rectangle shape (150 × 100 points)
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 100);

        // 4️⃣ How to add shadow – configure the ShadowFormat
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = Color.Gray;
        rectangleShape.ShadowFormat.Transparency = 0.3; // 30 % transparent
        rectangleShape.ShadowFormat.OffsetX = 5;        // horizontal offset
        rectangleShape.ShadowFormat.OffsetY = 5;        // vertical offset
        rectangleShape.ShadowFormat.BlurRadius = 4;    // softer edge
        rectangleShape.ShadowFormat.Size = 75;         // size as a percentage

        // 5️⃣ Save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowRectangle.docx");
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Execute o programa (`dotnet run`) e você terá um novo arquivo Word com um retângulo bem sombreado — perfeito para relatórios, certificados ou qualquer indicação visual que precisar.

## Perguntas Frequentes (FAQs)

**Q: Posso inserir outras formas (elipse, estrela) e ainda usar o mesmo código de sombra?**  
A: Absolutamente. O método `InsertShape` aceita qualquer valor do enum `ShapeType`. Uma vez que você tem uma instância `Shape`, as propriedades `ShadowFormat` funcionam de forma idêntica, portanto **como adicionar sombra** é independente da forma.

**Q: E se eu precisar da sombra em ambos os lados da forma?**  
A: O Aspose.Words suporta apenas uma sombra projetada por forma. Para simular um efeito de sombra dupla, duplique a forma, deslocando cada cópia de forma diferente, e defina `ShadowFormat.Visible` de uma como `false` enquanto mantém a sombra da outra visível.

**Q: Isso funciona no .NET Framework 4.8?**  
A: Sim. A API é independente de versão; basta referenciar o DLL Aspose.Words apropriado para o seu framework de destino.

## Dicas & Armadilhas

- **Não se esqueça de definir `Visible = true`** — as propriedades da sombra são ignoradas caso contrário.  
- **Os valores de transparência variam de 0.0 (opaco) a 1.0 (totalmente transparente).** Um erro comum é usar `30` em vez de `0.3`.  
- **Salvar em uma pasta somente‑leitura gera uma exceção.** Certifique‑se de que o diretório de saída seja gravável.

## Próximos Passos

Agora que você sabe **como inserir forma**, **adicionar sombra à forma**, e **criar documento word** com Aspose.Words, talvez queira explorar:

- Adicionar **texto dentro do retângulo** usando `builder.InsertParagraph()` antes de inserir a forma.  
- Aplicar **preenchimentos em gradiente** ou **bordas padronizadas** para um estilo visual mais rico.  
- Automatizar a geração de múltiplas páginas, cada uma com uma forma sombreada diferente, para criar relatórios dinâmicos.

Sinta‑se à vontade para experimentar — mudar a cor, o desfoque ou o tamanho da sombra pode alterar drasticamente a aparência do seu documento.

---

*Pronto para colocar isso em produção? Pegue o código, ajuste os parâmetros e veja seus arquivos Word ganharem um acabamento profissional em segundos.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}