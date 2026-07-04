---
category: general
date: 2026-05-04
description: Aprenda como salvar imagens ao converter um DOCX para Markdown usando
  Aspose.Words. Este guia também mostra como extrair imagens do Word e salvar o Word
  como Markdown.
draft: false
keywords:
- how to save images
- convert docx to markdown
- extract images from word
- how to convert docx
- save word as markdown
language: pt
og_description: Como salvar imagens ao converter um DOCX para Markdown usando Aspose.Words.
  Guia passo a passo com código C# completo.
og_title: Como salvar imagens – Converter DOCX para Markdown com Aspose.Words
tags:
- Aspose.Words
- C#
- Markdown conversion
title: Como salvar imagens – Converter DOCX para Markdown com Aspose.Words
url: /pt/net/programming-with-markdownsaveoptions/how-to-save-images-convert-docx-to-markdown-with-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como Salvar Imagens – Converter DOCX para Markdown com Aspose.Words

Já se perguntou **como salvar imagens** quando precisa transformar um arquivo Word em Markdown? Você não está sozinho. Muitos desenvolvedores se deparam com um obstáculo quando a conversão coloca as imagens em um caos de links quebrados ou, pior ainda, as perde completamente. A boa notícia é que o Aspose.Words oferece controle granular, permitindo extrair imagens do Word, decidir onde elas vão e ainda obter uma saída Markdown limpa.

Neste tutorial, percorreremos um exemplo completo, pronto‑para‑executar em C#, que demonstra **como salvar imagens** em uma pasta dedicada ao converter um `.docx` para `.md`. Ao longo do caminho, também abordaremos **convert docx to markdown**, **extract images from word** e a questão mais ampla de **how to convert docx** de forma que você possa **save word as markdown** sem perder nenhum recurso.

## Pré-requisitos

- .NET 6.0 ou posterior (a API funciona da mesma forma no .NET Framework 4.7+)
- Uma licença ativa do Aspose.Words ou um teste gratuito (a versão gratuita adiciona uma marca d'água à saída, mas o código funciona da mesma forma)
- Um documento Word que já contém imagens (por exemplo, `DocWithImages.docx`)
- Visual Studio 2022 ou qualquer editor que possa compilar projetos C#

> **Dica profissional:** Se você estiver usando uma versão de avaliação, ainda pode testar a lógica de salvamento de imagens; apenas lembre-se de que o PDF/MD final conterá a marca d'água da avaliação.

## Visão Geral da Solução

Em alto nível, o processo se parece com isto:

1. Carregue o `.docx` de origem com `Document`.
2. Crie um objeto `MarkdownSaveOptions` e conecte um `IResourceSavingCallback`.
3. No callback, decida a pasta e o nome do arquivo para cada imagem.
4. Salve o documento como Markdown; o callback grava cada imagem no disco.

Esse é o núcleo de **como salvar imagens** durante uma conversão. O mesmo padrão funciona para outros tipos de recursos (fonts, CSS, etc.) caso você precise deles.

## Etapa 1 – Carregar o DOCX que Contém Imagens

Primeiro, precisamos de uma instância `Document` que aponte para o arquivo Word que você deseja converter. Nada sofisticado aqui; apenas uma chamada direta ao construtor.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

// Adjust the path to where your .docx lives
string sourcePath = @"C:\Docs\DocWithImages.docx";

Document sourceDoc = new Document(sourcePath);
```

> **Por que isso importa:** Carregar o documento é o único momento em que o Aspose analisa o XML do Word, portanto, quaisquer fontes ausentes ou partes corrompidas lançarão uma exceção imediatamente—antes mesmo de começarmos a salvar imagens.

## Etapa 2 – Configurar MarkdownSaveOptions com um Callback de Salvamento de Imagem

A classe `MarkdownSaveOptions` permite que você se conecte ao processo de salvamento via `ResourceSavingCallback`. Esse callback recebe um objeto `ResourceSavingArgs` para cada recurso externo (imagens, CSS, etc.) que o Aspose precisa gravar.

```csharp
// Define where the Markdown file will be written
string markdownPath = @"C:\Docs\Doc.md";

// Create the options object and attach the callback
MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
{
    // This is the heart of how to save images
    ResourceSavingCallback = new ImageSavingCallback()
};
```

### Implementação do Callback

Abaixo está a implementação completa de `ImageSavingCallback`. Ela cria uma sub‑pasta `Images` ao lado do arquivo Markdown, atribui a cada imagem um nome sequencial (`img_0.png`, `img_1.jpg`, …) e, opcionalmente, permite que você envie a imagem para outro local (por exemplo, para um bucket na nuvem).

```csharp
class ImageSavingCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Only handle images; other resources (like CSS) are ignored here
        if (args.ResourceType != ResourceType.Image)
            return;

        // Build a folder called "Images" right next to the markdown file
        string markdownDir = Path.GetDirectoryName(args.DestinationFileName);
        string imagesFolder = Path.Combine(markdownDir, "Images");
        Directory.CreateDirectory(imagesFolder);

        // Compose a safe file name: img_<index>.<original extension>
        string newFileName = $"img_{args.Index}{Path.GetExtension(args.FileName)}";
        args.FileName = Path.Combine(imagesFolder, newFileName);

        // If you wanted to push the image to a remote store, you could replace args.Stream here.
        // For now we just let Aspose write to the local file system.
    }
}
```

> **Como isso ajuda:** Ao personalizar `args.FileName` você controla exatamente **como salvar imagens**—seja em uma pasta única, em uma hierarquia baseada em datas ou até mesmo em um BLOB de banco de dados. O callback é executado para cada imagem, então você nunca precisará pós‑processar o arquivo Markdown depois.

## Etapa 3 – Salvar o Documento como Markdown

Agora que as opções e o callback estão prontos, a conversão real é feita em uma única linha.

```csharp
// Save the document; the callback will fire for each image automatically
sourceDoc.Save(markdownPath, markdownOptions);
```

Quando a linha terminar, você terá:

- `Doc.md` – a representação Markdown do seu conteúdo Word.
- `Images\img_0.png`, `Images\img_1.jpg`, … – cada imagem extraída do DOCX original.

## Exemplo Completo, Pronto‑para‑Executar

Juntando tudo, aqui está um aplicativo de console autônomo que você pode copiar e colar em um novo projeto C#.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

namespace DocxToMarkdownDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // -----------------------------------------------------------------
            // 1️⃣ Load the source DOCX that contains images
            // -----------------------------------------------------------------
            string sourcePath = @"C:\Docs\DocWithImages.docx";
            Document sourceDoc = new Document(sourcePath);

            // -----------------------------------------------------------------
            // 2️⃣ Prepare Markdown options with a custom image‑saving callback
            // -----------------------------------------------------------------
            string markdownPath = @"C:\Docs\Doc.md";
            MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
            {
                ResourceSavingCallback = new ImageSavingCallback()
            };

            // -----------------------------------------------------------------
            // 3️⃣ Perform the conversion – this is where we actually learn
            //     how to save images while converting docx to markdown
            // -----------------------------------------------------------------
            sourceDoc.Save(markdownPath, markdownOptions);

            Console.WriteLine("Conversion complete!");
            Console.WriteLine($"Markdown file: {markdownPath}");
            Console.WriteLine("Images folder: " + Path.Combine(Path.GetDirectoryName(markdownPath), "Images"));
        }
    }

    // -----------------------------------------------------------------
    // 4️⃣ Callback that decides where each image ends up
    // -----------------------------------------------------------------
    class ImageSavingCallback : IResourceSavingCallback
    {
        public void ResourceSaving(ResourceSavingArgs args)
        {
            if (args.ResourceType != ResourceType.Image)
                return;

            string markdownDir = Path.GetDirectoryName(args.DestinationFileName);
            string imagesFolder = Path.Combine(markdownDir, "Images");
            Directory.CreateDirectory(imagesFolder);

            string newFileName = $"img_{args.Index}{Path.GetExtension(args.FileName)}";
            args.FileName = Path.Combine(imagesFolder, newFileName);

            // Optional: redirect the image stream elsewhere (e.g., cloud storage)
            // args.Stream = new MemoryStream(); // your custom stream here
        }
    }
}
```

### Resultado Esperado

Depois de executar o programa:

- Abra `C:\Docs\Doc.md` em qualquer editor de texto. Você verá links de imagem Markdown como `![](Images/img_0.png)`.
- A pasta `Images` conterá cada imagem extraída, nomeada sequencialmente.
- O arquivo Markdown será renderizado corretamente em qualquer visualizador que suporte imagens locais (pré‑visualização do VS Code, GitHub, etc.).

## Perguntas Frequentes (FAQs)

### Isso funciona com outros formatos de imagem (SVG, TIFF)?

Sim. `Path.GetExtension(args.FileName)` preserva a extensão original, portanto SVG, TIFF, BMP e até EMF são salvos sem alterações. A única ressalva é que alguns renderizadores de Markdown podem não exibir SVG inline; nesse caso, você pode converter SVG para PNG previamente.

### E se eu precisar incorporar imagens como Base64 em vez de arquivos separados?

Dentro de `ResourceSaving`, você pode substituir a gravação física do arquivo por um stream de memória e então modificar o link Markdown manualmente. O Aspose não expõe um interruptor direto de “incorporar como Base64”, mas o callback lhe dá controle total sobre `args.Stream`.

### Como isso difere do método interno `ExportImages`?

`ExportImages` extrai todas as imagens para uma pasta **sem** gerar Markdown. Nosso callback combina as duas ações, garantindo que os nomes dos arquivos de imagem correspondam às referências dentro do `.md`. Esse alinhamento é a chave para **como salvar imagens** corretamente durante a conversão.

### Posso converter vários arquivos DOCX em lote?

Com certeza. Envolva a lógica principal em um loop `foreach (var file in Directory.GetFiles(..., "*.docx"))`, ajuste os caminhos de saída e reutilize o mesmo `ImageSavingCallback`. Apenas lembre-se de criar um novo `MarkdownSaveOptions` para cada documento, pois `args.DestinationFileName` muda a cada iteração.

## Casos de Borda & Melhores Práticas

| Situação | O que observar | Correção Recomendada |
|-----------|----------------------|-----------------|
| **Grande DOCX (centenas de MB)** | Pressão de memória ao carregar | Use `LoadOptions` com `LoadFormat.Docx` e defina `LoadOptions.LoadFormat = LoadFormat.Docx` para carregar partes em streaming |
| **Nomes de imagens colidem** | Se a origem já tem `img_0.png` na pasta de destino, você pode sobrescrever | Anexe um GUID: `newFileName = $"img_{args.Index}_{Guid.NewGuid():N}{Path.GetExtension(args.FileName)}"` |
| **Pasta de saída somente leitura** | Salvar lança `UnauthorizedAccessException` | Garanta que o processo execute com permissões adequadas ou escolha um caminho gravável |
| **Recursos não‑imagem (CSS, fontes)** | O callback também os recebe | Proteja com `if (args.ResourceType != ResourceType.Image) return;` (já mostrado) |
| **Nomes de arquivos Unicode** | Alguns sistemas de arquivos tratam mal caracteres | Use `Path.GetInvalidFileNameChars()` para sanitizar `args.FileName` antes de atribuir |

## Tópicos Relacionados que Você Pode Explorar a Seguir

- **convert docx to markdown** com estilos de título personalizados (use `MarkdownSaveOptions.ExportImagesAsBase64` para imagens embutidas)
- **extract images from word** usando o `Document.GetChildNodes(NodeType.Shape,

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}