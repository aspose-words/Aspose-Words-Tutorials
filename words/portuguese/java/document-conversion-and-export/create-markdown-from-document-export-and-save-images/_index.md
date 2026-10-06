---
category: general
date: 2026-02-18
description: Crie markdown a partir de um documento com passos fáceis para exportar
  o documento para markdown e salvar imagens em uma subpasta. Aprenda como salvar
  o documento como markdown em C#.
draft: false
keywords:
- create markdown from document
- export document to markdown
- save document as markdown
- save images to subfolder
language: pt
og_description: Crie markdown a partir de um documento em C# e aprenda como exportar
  o documento para markdown enquanto salva as imagens em uma subpasta. Siga o guia
  passo a passo.
og_title: Criar markdown a partir do documento – Exportar e salvar imagens
tags:
- C#
- Aspose.Words
- Markdown export
title: Criar markdown a partir do documento – Exportar e salvar imagens
url: /pt/java/document-conversion-and-export/create-markdown-from-document-export-and-save-images/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar markdown a partir do documento – Exportar e salvar imagens

Já precisou **criar markdown a partir do documento** mas não sabia como manter as imagens incorporadas organizadas? Você não está sozinho. Em muitos projetos geramos relatórios, manuais ou rascunhos de blog programaticamente, e a última coisa que queremos é uma bagunça de arquivos de imagem espalhados pela pasta de saída.  

Neste tutorial vamos percorrer uma solução completa, pronta‑para‑executar, que **exporta o documento para markdown**, armazena cada imagem em uma sub‑pasta dedicada *md‑resources*, e finalmente **salva o documento como markdown** usando a API Aspose.Words for .NET. Ao final você terá um único método que pode inserir em qualquer base de código C#, além de algumas dicas para lidar com casos extremos.

> **Visão rápida:**  
> • Configure `MarkdownSaveOptions`  
> • Forneça um `IResourceSavingCallback` que redireciona imagens para uma subpasta  
> • Chame `Document.Save` com as opções configuradas  

Se você está curioso sobre por que escolhemos um callback em vez de pós‑processamento, continue lendo – o raciocínio é explicado passo a passo.

---

## Pré-requisitos

- .NET 6.0 ou posterior (o código também funciona com .NET Framework 4.7+)  
- Aspose.Words for .NET (pacote NuGet `Aspose.Words`)  
- Um objeto `Document` de origem (pode ser .docx, .pdf, .rtf, etc.)  

Nenhuma biblioteca adicional é necessária; a API de callback está integrada ao Aspose.Words.

---

## Etapa 1: Criar markdown a partir do documento – configurar opções de salvamento

A primeira coisa que fazemos é instanciar `MarkdownSaveOptions`. Este objeto informa ao Aspose.Words como a conversão deve se comportar, como qual sabor de Markdown usar, se deve incorporar imagens como Base64 e onde colocar os arquivos gerados.

```csharp
// Step 1: Initialize Markdown save options
var markdownSaveOptions = new Aspose.Words.Saving.MarkdownSaveOptions();
```

> **Por que isso importa:**  
> Sem criar explicitamente `MarkdownSaveOptions`, a biblioteca recorre às configurações padrão que incorporam imagens diretamente no arquivo Markdown como strings Base64. Isso deixa o arquivo enorme e anula o objetivo de ter uma pasta *images* limpa.

---

## Etapa 2: Exportar documento para markdown e definir o tratamento de recursos

Agora informamos ao salvador **onde** colocar cada imagem. A interface `IResourceSavingCallback` nos fornece um hook que dispara para cada recurso (imagem, SVG, etc.) descoberto durante a exportação. Dentro do callback nós:

1. Garantimos que a pasta de destino exista (`md-resources/`).  
2. Definimos `OutputFileName` para a pasta mais o nome original do recurso.  

```csharp
// Step 2: Hook into the resource‑saving pipeline
markdownSaveOptions.ResourceSavingCallback = new Aspose.Words.Saving.IResourceSavingCallback(
    (args) =>
    {
        // All images will be placed in "md-resources" relative to the output .md file
        const string folder = "md-resources/";
        Directory.CreateDirectory(folder);          // Create folder if it doesn’t exist

        // Preserve the original file name (e.g., image001.png) but prepend the folder path
        args.OutputFileName = Path.Combine(folder, args.ResourceFileName);

        // Optional: you could also change the format here (e.g., convert BMP to PNG)
        // args.ResourceFileName = Path.ChangeExtension(args.ResourceFileName, ".png");
    });
```

> **Pergunta comum:** *E se eu quiser incorporar imagens em vez de salvá‑las?*  
> Basta pular o callback ou definir `args.OutputFileName = null;` – o salvador incorporará a imagem como uma string Base64 automaticamente.

> **Caso extremo:** Alguns documentos antigos contêm nomes de imagem duplicados. O callback acima sobrescreverá o arquivo anterior. Para evitar isso, você pode acrescentar um GUID:

```csharp
args.OutputFileName = Path.Combine(folder,
    $"{Path.GetFileNameWithoutExtension(args.ResourceFileName)}_{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}");
```

---

## Etapa 3: Salvar documento como markdown e verificar as imagens salvas

Com as opções totalmente configuradas, a chamada final é uma única linha que grava o arquivo Markdown e as imagens associadas no disco.

```csharp
// Step 3: Perform the actual export
string outputPath = @"C:\Exports\MyReport.md";
doc.Save(outputPath, markdownSaveOptions);
```

Se tudo correr bem, você verá:

- `MyReport.md` – a representação Markdown do seu documento de origem.  
- `md-resources/` – uma pasta ao lado do arquivo .md contendo cada imagem extraída (ex.: `image001.png`, `image002.jpg`).  

**Trecho de Markdown de exemplo** (gerado automaticamente pelo Aspose.Words):

```markdown
# Sample Report

Here is an introductory paragraph.

![Sample image](md-resources/image001.png)

More text follows...
```

> **Dica profissional:** Abra o arquivo `.md` gerado no VS Code ou em qualquer visualizador de Markdown; as imagens devem ser renderizadas instantaneamente porque os caminhos relativos correspondem à estrutura de pastas.

---

## Exemplo completo, executável

Abaixo está um programa console autocontido que você pode colar em um novo projeto .NET e executar. Ele cria um documento Word simples, adiciona uma imagem e então **cria markdown a partir do documento** enquanto armazena a imagem em uma subpasta.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a sample Word document with an image
        var doc = new Document();
        var builder = new DocumentBuilder(doc);
        builder.Writeln("Hello, this is a test document.");
        builder.InsertImage("sample-image.png"); // Ensure this file exists next to exe

        // 2️⃣ Configure markdown export options (see Step 1 & 2 above)
        var markdownOptions = new MarkdownSaveOptions();
        markdownOptions.ResourceSavingCallback = new IResourceSavingCallback(
            (args) =>
            {
                const string folder = "md-resources/";
                Directory.CreateDirectory(folder);
                args.OutputFileName = Path.Combine(folder, args.ResourceFileName);
            });

        // 3️⃣ Save as markdown (Step 3)
        string outputFolder = Path.Combine(Environment.CurrentDirectory, "output");
        Directory.CreateDirectory(outputFolder);
        string markdownPath = Path.Combine(outputFolder, "ExportedDoc.md");
        doc.Save(markdownPath, markdownOptions);

        Console.WriteLine($"✅ Markdown saved to: {markdownPath}");
        Console.WriteLine("📂 Images saved in: md-resources/");
    }
}
```

**O que você deverá ver** após a execução:

```
✅ Markdown saved to: C:\MyProject\output\ExportedDoc.md
📂 Images saved in: md-resources/
```

Abra `ExportedDoc.md` – a referência da imagem apontará para `md-resources/sample-image.png`, e a foto será exibida corretamente em qualquer visualizador de Markdown.

---

## Variações frequentemente perguntadas

| Cenário | Como adaptar o código |
|----------|----------------------|
| **Ignorar exportação de imagem** (incorporar como Base64) | Omitir `ResourceSavingCallback` completamente, ou definir `args.OutputFileName = null;` dentro do callback. |
| **Alterar formato da imagem** (ex.: todas PNG) | Dentro do callback, modifique `args.ResourceFileName` e, opcionalmente, converta o stream antes de gravar. |
| **Nome de pasta personalizado** | Substitua `"md-resources/"` por qualquer caminho relativo ou absoluto que preferir. |
| **Vários documentos em lote** | Percorra uma coleção de objetos `Document`, reutilizando a mesma instância de `MarkdownSaveOptions` (apenas garanta que a pasta seja limpa ou nomeada de forma única por execução). |

---

## Conclusão

Acabamos de mostrar como **criar markdown a partir do documento**, **exportar o documento para markdown** e **salvar imagens em subpasta** usando uma abordagem limpa, orientada por callbacks. Os principais aprendizados são:

- Use `MarkdownSaveOptions` para obter controle granular sobre a exportação.  
- Implemente `IResourceSavingCallback` para direcionar imagens a uma pasta dedicada, mantendo seu Markdown organizado.  
- O mesmo padrão funciona para outros tipos de recurso (SVG, áudio) – basta inspecionar `args.ResourceType`.  

Em seguida, você pode explorar **salvar documento como markdown** com estilos de cabeçalho personalizados, ou integrar essa rotina em uma API ASP.NET Web que devolve um ZIP contendo o arquivo `.md` e seus recursos. De qualquer forma, os blocos de construção agora estão na sua caixa de ferramentas.

Tem perguntas ou encontrou um caso que não cobrimos? Deixe um comentário abaixo, e boa codificação!

---

![exemplo de criar markdown a partir do documento](placeholder.png "exemplo de criar markdown a partir do documento")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}