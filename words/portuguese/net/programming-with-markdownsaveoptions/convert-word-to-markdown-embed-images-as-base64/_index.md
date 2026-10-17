---
category: general
date: 2026-01-03
description: Converta Word para Markdown e incorpore imagens como base64 de uma só
  vez. Aprenda como salvar Word como markdown, gerar markdown a partir do Word e usar
  URI de dados de imagem base64.
draft: false
keywords:
- convert word to markdown
- embed images as base64
- save word as markdown
- base64 image data uri
- generate markdown from word
language: pt
og_description: Converta Word para Markdown e incorpore imagens como URIs de dados
  base64. Este tutorial passo a passo mostra como salvar Word como markdown e gerar
  markdown a partir do Word.
og_title: Converter Word para Markdown – Guia de Incorporação de Imagens em Base64
tags:
- Aspose.Words
- C#
- Markdown
title: Converter Word para Markdown – Incorporar Imagens como Base64
url: /pt/net/programming-with-markdownsaveoptions/convert-word-to-markdown-embed-images-as-base64/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Converter Word para Markdown – Incorporar Imagens como Base64

Já precisou **converter Word para markdown** e ficou travado nas imagens? Você não está sozinho. O Word adora armazenar fotos como arquivos separados, enquanto o markdown prefere aquelas pequenas strings `data:image/...;base64,` que mantêm tudo organizado em um único arquivo.  

Neste tutorial vamos percorrer uma solução completa, pronta‑para‑executar que **salva Word como markdown**, **incorpora imagens como base64**, e ainda mostra como **gerar markdown a partir do Word** usando Aspose.Words for .NET. Ao final, você terá um único arquivo `.md` que renderiza exatamente como o documento original — sem pastas de imagens externas.

## O que você vai precisar

- **.NET 6.0 ou superior** (qualquer coisa que possa referenciar um pacote NuGet)
- **Aspose.Words for .NET** (a versão de avaliação gratuita funciona bem para testes)
- Um simples arquivo `.docx` com algumas imagens (vamos chamá‑lo de `input.docx`)
- Seu IDE favorito (Visual Studio, Rider, VS Code — escolha o que preferir)

Se já tem tudo isso, ótimo — vamos começar. Caso contrário, instalar o pacote NuGet é uma única linha:

```bash
dotnet add package Aspose.Words
```

## Etapa 1: Carregar o Documento Word — o ponto de partida para **converter word para markdown**

Primeiro precisamos trazer o `.docx` para a memória. É aqui que a mágica da conversão começa.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

// Load the Word file that contains the images.
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

> **Por que isso importa:**  
> Carregar o documento dá ao Aspose acesso total ao texto, estilos e a todos os recursos incorporados. Sem essa etapa, não há nada para converter.

## Etapa 2: Configurar MarkdownSaveOptions com um Callback de Salvamento de Recursos

O Aspose permite interceptar cada recurso (como imagens) que normalmente seria gravado no disco. Ao fornecer um `IResourceSavingCallback` personalizado, podemos substituir a gravação padrão baseada em arquivos por um **URI de dados de imagem base64**.

```csharp
// Configure Markdown save options so that images become Base64 URIs.
MarkdownSaveOptions markdownSaveOptions = new MarkdownSaveOptions
{
    ResourceSavingCallback = new MyResourceHandler()
};
```

### O Manipulador Personalizado – Transformando imagens em Base64

Abaixo está a implementação completa. Observe como verificamos `args.ResourceType == ResourceType.Image` e então:

1. Gravamos a imagem em um `MemoryStream`.
2. Convertemos o array de bytes para uma string Base64.
3. Construímos um URI `data:image/jpeg;base64,` e o atribuímos a `args.Uri`.

```csharp
// Custom handler that converts each image resource to a Base64 data URI.
class MyResourceHandler : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Only process images – leave other resources untouched.
        if (args.ResourceType == ResourceType.Image)
        {
            // Prepare an in‑memory stream for the image.
            using (MemoryStream ms = new MemoryStream())
            {
                // Save the image using default JPEG options.
                args.ResourceData.Save(ms, ImageSaveOptions.DefaultJpeg);
                // Build the Base64 data URI.
                string base64 = Convert.ToBase64String(ms.ToArray());
                args.Uri = $"data:image/jpeg;base64,{base64}";
                // No need to keep the stream open after we set the URI.
                args.KeepResourceStreamOpen = false;
            }
        }
    }
}
```

> **Dica profissional:** Se o seu Word de origem usa PNGs, troque `ImageSaveOptions.DefaultJpeg` por `ImageSaveOptions.DefaultPng` e altere o tipo MIME correspondente (`image/png`).

## Etapa 3: Salvar o Documento como Markdown – a etapa final de **salvar word como markdown**

Agora que o callback está pronto, a gravação propriamente dita cabe em uma única linha.

```csharp
// Save the document to a Markdown file. Images are already embedded.
document.Save("YOUR_DIRECTORY/output.md", markdownSaveOptions);
```

Ao abrir `output.md` em qualquer visualizador de markdown (pré‑visualização do VS Code, GitHub, etc.), você verá o texto exatamente como no arquivo Word original, e as imagens aparecerão embutidas sem arquivos separados.

## Saída Esperada

```markdown
# Sample Title

Here’s a paragraph that originally lived in Word.

![Embedded Image](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAkGBxISEhU...
```

A linha `![Embedded Image]` é um **URI de dados de imagem base64** — a imagem inteira está codificada ali mesmo. Sem pastas extras, sem links quebrados.

## Casos Limite & Como Lidar com Eles

| Situação | O que fazer |
|-----------|------------|
| **Imagens Grandes** – Base64 aumenta o tamanho em ~33% | Considere redimensionar antes da conversão: `args.ResourceData.Save(ms, new ImageSaveOptions { ImageResolution = 72 })`. |
| **Imagens Não‑JPEG** (PNG, GIF) | Detecte o formato original via `args.ResourceData.ImageType` e defina o MIME correto (`image/png`, `image/gif`). |
| **Documentos Muito Longos** (centenas de imagens) | Fique de olho no uso de memória; você pode fazer streaming de cada imagem para o disco temporariamente se o processo ficar sem RAM. |
| **Precisa de Arquivos de Imagem Separados** (ex.: para um site estático) | Retorne `false` do callback para as imagens que deseja manter como arquivos, e deixe o Aspose gravá‑las em uma pasta. |

## Perguntas Frequentes (Respondidas Antecipadamente)

- **Isso funciona com arquivos .doc?** Sim — o Aspose.Words pode carregar arquivos legados `.doc` da mesma forma que carrega `.docx`. Basta apontar `new Document("myfile.doc")` para ele.
- **E quanto a tabelas e notas de rodapé?** Elas são totalmente suportadas pelo exportador de Markdown. Tabelas se tornam tabelas markdown; notas de rodapé se tornam referências inline.
- **Posso mudar o sabor do markdown?** `MarkdownSaveOptions` tem a propriedade `MarkdownVersion` (CommonMark, GitHub, etc.). Defina‑a antes de salvar se precisar de uma sintaxe específica.

## Exemplo Completo e Pronto para Executar

A seguir está o programa completo que você pode copiar‑colar em um aplicativo console. Ele inclui todas as declarações `using`, a classe do handler e tratamento de erros.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

namespace WordToMarkdownDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            try
            {
                // 1️⃣ Load the source Word document.
                Document doc = new Document("YOUR_DIRECTORY/input.docx");

                // 2️⃣ Prepare Markdown options with our custom image handler.
                MarkdownSaveOptions options = new MarkdownSaveOptions
                {
                    ResourceSavingCallback = new MyResourceHandler()
                };

                // 3️⃣ Save as Markdown – images become Base64 URIs.
                string outputPath = "YOUR_DIRECTORY/output.md";
                doc.Save(outputPath, options);

                Console.WriteLine($"✅ Success! Markdown saved to {outputPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"❌ Conversion failed: {ex.Message}");
            }
        }
    }

    // Custom callback that embeds images as Base64 data URIs.
    class MyResourceHandler : IResourceSavingCallback
    {
        public void ResourceSaving(ResourceSavingArgs args)
        {
            if (args.ResourceType == ResourceType.Image)
            {
                using (MemoryStream ms = new MemoryStream())
                {
                    // Preserve original format if you prefer PNG/GIF.
                    args.ResourceData.Save(ms, ImageSaveOptions.DefaultJpeg);
                    string base64 = Convert.ToBase64String(ms.ToArray());
                    args.Uri = $"data:image/jpeg;base64,{base64}";
                    args.KeepResourceStreamOpen = false;
                }
            }
        }
    }
}
```

Execute o programa, abra o `output.md` gerado, e você verá uma réplica perfeita em markdown do seu arquivo Word — **converter word para markdown** nunca foi tão simples.

## Recapitulação

Começamos com o problema de **converter word para markdown** mantendo as imagens embutidas. Carregando o documento, configurando um callback de `MarkdownSaveOptions` e salvando o arquivo, conseguimos uma solução limpa de **salvar word como markdown** que produz strings **base64 image data uri**. Agora você também sabe como **incorporar imagens como base64**, lidar com casos limite e ajustar o processo para diferentes tipos de imagem.

## O que vem a seguir?

- **Gerar HTML em vez de markdown** — troque `MarkdownSaveOptions` por `HtmlSaveOptions` e reutilize o mesmo callback.
- **Conversão em lote de múltiplos arquivos** — envolva a lógica em um loop `foreach` sobre uma pasta.
- **Integrar em um pipeline de CI** — automatize a geração de documentação para sites estáticos.

Sinta‑se à vontade para experimentar, ajustar a qualidade das imagens ou até mesmo adicionar seu próprio tratamento de recursos (ex.: fazer upload das imagens para um CDN e inserir a URL). O céu é o limite quando você combina Aspose.Words com um pouco de engenhosidade em C#.

Feliz codificação, e que seu markdown sempre renderize perfeitamente! 

![Diagrama mostrando fluxo de converter word para markdown – incorporar imagens como base64](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iNjAwIiBoZWlnaHQ9IjQwMCIgdmlld0JveD0iMCAwIDYwMCA0MDAiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyI+PHJlY3Qgd2lkdGg9IjYwMCIgaGVpZ2h0PSI0MDAiIGZpbGw9IiNmZmYiIHN0cm9rZT0iI2NjYyIgLz48dGV4dCB4PSI1MCIgeT0iMjAwIiBmb250LXNpemU9IjM2IiBmaWxsPSIjMDAwIj5JbWFnZSBJbWFnZSBJbWFnZSBJbWFnZTwvdGV4dD48L3N2Zz4= "convert word to markdown flow diagram")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}