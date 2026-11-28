---
category: general
date: 2026-04-10
description: Como definir DPI ao converter Word para PNG. Aprenda a exportar Word
  para PNG com um layout de grade personalizado e alta resolução.
draft: false
keywords:
- how to set dpi
- convert word to png
- how to export word
- export word to png
- create png grid
language: pt
og_description: como definir dpi ao exportar um documento Word. Este tutorial mostra
  como converter Word para PNG, exportar Word para PNG e criar uma grade PNG com C#.
og_title: Como definir DPI – Guia completo para exportar Word para PNG
tags:
- C#
- Aspose.Words
- ImageExport
title: como definir dpi – Exportar Word para grade PNG em C#
url: /pt/net/programming-with-imagesaveoptions/how-to-set-dpi-export-word-to-png-grid-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# como definir dpi – Exportar Word para PNG em grade em C#

Já se perguntou **como definir dpi** para uma conversão de Word‑para‑PNG sem perder a cabeça? Você não está sozinho. Em muitos projetos — pense em geradores automáticos de relatórios ou pipelines de miniaturas — você precisa de um PNG nítido que respeite um DPI específico, e frequentemente também quer várias páginas compactadas em uma única imagem em grade. Neste guia, vamos percorrer uma solução completa, pronta‑para‑executar que **converte Word para PNG**, permite que você **exporte Word para PNG** com configuração de 300 DPI, e ainda **cria uma grade PNG** de uma só vez.

> **Resultado rápido:** Ao final deste artigo, você terá uma única linha de C# que recebe `input.docx` e gera `output.png` com 300 DPI, organizada em uma grade 2 × 2. Sem ferramentas extras, sem edição manual de imagens.

## O que você aprenderá

- Como **definir DPI** usando Aspose.Words `ImageSaveOptions`.
- Os passos exatos para **exportar Word para PNG** com um layout de página personalizado.
- Como **criar uma grade PNG** (quatro páginas por linha/coluna) em um único arquivo.
- Armadilhas comuns ao converter documentos grandes e como evitá‑las.
- Algumas variações: exportar páginas individuais, mudar o tamanho da grade e trocar PNG por JPEG.

### Pré‑requisitos

| Requisito | Por que importa |
|-------------|----------------|
| **Aspose.Words for .NET** (v23.12 ou mais recente) | Fornece as classes `Document` e `ImageSaveOptions` nas quais nos baseamos. |
| **.NET 6+** (ou .NET Framework 4.7.2) | Garante compatibilidade com a superfície de API mais recente. |
| **Conhecimento básico de C#** | Você precisará entender namespaces e caminhos de arquivos. |
| **Um arquivo Word** (`input.docx`) | O documento fonte que converteremos. |

Se ainda não instalou o Aspose.Words, execute:

```bash
dotnet add package Aspose.Words
```

Agora que o cenário está preparado, vamos mergulhar no código.

## Etapa 1 – Carregar o Documento Fonte (como exportar word)

A primeira coisa que você faz é carregar o arquivo Word na memória. É aqui que **como exportar word** começa.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Load the source .docx
Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
```

> **Dica profissional:** Use um caminho absoluto ou `Path.Combine` para evitar surpresas em diferentes sistemas operacionais.

## Etapa 2 – Configurar Opções de Salvamento de Imagem (como definir dpi & criar grade png)

Aqui está o coração do tutorial. Dizemos ao Aspose.Words exatamente como queremos que o PNG pareça: 300 DPI, formato PNG, e um **layout de grade** que agrupa quatro páginas em uma única imagem.

```csharp
// Create PNG save options with a grid layout
ImageSaveOptions imgOptions = new ImageSaveOptions(SaveFormat.Png)
{
    // Arrange pages in a grid (2 columns × 2 rows = 4 pages)
    PageLayout = ImageSaveOptions.PageLayoutType.Grid,
    
    // Number of columns in the grid – 2 columns => 2 rows for 4 pages
    PageCount = 4,
    
    // Set the DPI – this is where we *how to set dpi*
    HorizontalResolution = 300,
    VerticalResolution = 300
};
```

### Por que essas configurações são importantes

- **`PageLayout = Grid`** – Sem isso, cada página seria salva como um PNG separado. A opção de grade as mescla, economizando uma etapa de pós‑processamento.
- **`PageCount = 4`** – Controla quantas páginas a grade conterá. Se seu documento tiver mais de quatro páginas, o Aspose criará linhas adicionais automaticamente.
- **Configurações de DPI** – `HorizontalResolution` e `VerticalResolution` são os controles que respondem à pergunta **como definir dpi**. Uma imagem de 300 DPI está pronta para impressão e parece nítida em telas retina.

## Etapa 3 – Salvar o Documento como um PNG Único (exportar word para png)

Agora executamos a operação de salvamento. Esta única linha faz o trabalho pesado.

```csharp
// Save the document pages as one PNG image
doc.Save(@"YOUR_DIRECTORY\output.png", imgOptions);
```

Depois que esta linha for executada, você encontrará `output.png` na pasta especificada. Abra‑o, e deverá ver uma grade 2 × 2 das quatro primeiras páginas, cada uma renderizada a 300 DPI.

![exemplo de como definir dpi](https://example.com/placeholder.png "como definir dpi ao exportar Word para PNG")

*Texto alternativo da imagem: como definir dpi ao exportar Word para PNG – mostra um PNG em grade 2×2.*

## Etapa 4 – Verificar o Resultado (criar grade png)

Uma verificação rápida de sanidade evita dores de cabeça depois. Você pode confirmar programaticamente o DPI e as dimensões:

```csharp
using System.Drawing;

// Load the generated PNG
using (Bitmap bmp = new Bitmap(@"YOUR_DIRECTORY\output.png"))
{
    Console.WriteLine($"Width: {bmp.Width}px, Height: {bmp.Height}px");
    Console.WriteLine($"Horizontal DPI: {bmp.HorizontalResolution}");
    Console.WriteLine($"Vertical DPI: {bmp.VerticalResolution}");
}
```

Se o console imprimir `300` para ambos os valores de DPI, você configurou **como definir dpi** com sucesso. A largura e altura refletirão o tamanho combinado das quatro páginas.

## Variações avançadas

### Converter Word para PNG – Um arquivo por página

Às vezes você precisa de arquivos PNG separados em vez de uma grade. Basta mudar `PageLayout` para `SinglePage` e percorrer as páginas:

```csharp
for (int i = 0; i < doc.PageCount; i++)
{
    imgOptions.PageIndex = i;               // Export only this page
    imgOptions.PageLayout = ImageSaveOptions.PageLayoutType.SinglePage;
    doc.Save($@"YOUR_DIRECTORY\page_{i + 1}.png", imgOptions);
}
```

Agora você tem `page_1.png`, `page_2.png`, … – perfeito para galerias de miniaturas.

### Exportar Word para PNG com um Tamanho de Grade Diferente

Se precisar de uma grade 3 × 3 (nove páginas), basta ajustar `PageCount`:

```csharp
imgOptions.PageCount = 9;          // 3 columns × 3 rows
imgOptions.PageLayout = ImageSaveOptions.PageLayoutType.Grid;
```

O Aspose calculará automaticamente as linhas necessárias.

### Trocar PNG por JPEG (se o tamanho do arquivo importar)

Alterar o formato é tão simples quanto trocar `SaveFormat.Png` por `SaveFormat.Jpeg`. Você também pode controlar a qualidade JPEG:

```csharp
ImageSaveOptions jpegOptions = new ImageSaveOptions(SaveFormat.Jpeg)
{
    PageLayout = ImageSaveOptions.PageLayoutType.Grid,
    PageCount = 4,
    HorizontalResolution = 300,
    VerticalResolution = 300,
    JpegQuality = 90   // 0‑100, higher = better quality
};

doc.Save(@"YOUR_DIRECTORY\output.jpg", jpegOptions);
```

### Manipulando documentos grandes

Ao lidar com documentos com mais de 100 páginas, considere transmitir a saída para evitar pressão de memória:

```csharp
using (FileStream fs = new FileStream(@"YOUR_DIRECTORY\large_output.png", FileMode.Create))
{
    doc.Save(fs, imgOptions);
}
```

A transmissão garante que o processo permaneça leve, mesmo em servidores modestos.

## Armadilhas comuns & como evitá‑las

| Sintoma | Causa | Correção |
|---------|-------|----------|
| PNG parece borrado | DPI deixado no padrão 96 | **Defina `HorizontalResolution` e `VerticalResolution` para 300** (ou mais). |
| Apenas a primeira página aparece | `PageLayout` ainda definido como `SinglePage` | Mude para `ImageSaveOptions.PageLayoutType.Grid`. |
| Arquivo de saída é enorme | Formato PNG com 300 DPI pode ser grande | Use JPEG com `JpegQuality` < 90, ou reduza o DPI se a qualidade de impressão não for necessária. |
| Grade corta as margens da página | Manipulação padrão de margens | Ajuste `ImageSaveOptions.PageMargins` se necessário. |

## Recapitulação – O que cobrimos

- **como definir dpi** – configurando `HorizontalResolution` e `VerticalResolution`.
- **converter word para png** – usando `ImageSaveOptions` com `SaveFormat.Png`.
- **como exportar word** – carregando o documento com `Document` e chamando `Save`.
- **exportar word para png** – uma linha única que produz um PNG de alta resolução.
- **criar grade png** – definindo `PageLayout = Grid` e `PageCount` para controlar o layout.

Tudo isso cabe em um trecho compacto e autocontido de C# que você pode inserir em qualquer projeto .NET.

## O que vem a seguir?

- Experimente **valores de DPI diferentes** (150, 600) para ver como o tamanho do arquivo varia.
- Combine esta abordagem com **Aspose.PDF** para mesclar a grade PNG em um relatório PDF.
- Explore **conversão de espaço de cor** (RGB → CMYK) se você estiver enviando o PNG para uma impressora profissional.
- Investigue **salvamento assíncrono** (`doc.SaveAsync`) para aplicações responsivas na UI.

Tem perguntas sobre casos extremos — como exportar arquivos DOCX criptografados ou lidar com fontes incorporadas? Deixe um comentário, e eu ficarei feliz em aprofundar.

*Feliz codificação! Se este tutorial ajudou você a **como definir dpi** e exportar seus documentos Word para uma elegante grade PNG, dê uma estrela ou compartilhe com um colega que está enfrentando o mesmo problema.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}