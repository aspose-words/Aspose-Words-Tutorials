---
category: general
date: 2026-04-28
description: Aprenda como definir um caminho relativo de imagem em markdown ao converter
  Word para markdown, extrair imagens do Word e criar uma pasta de recursos para as
  imagens exportadas.
draft: false
keywords:
- markdown image relative path
- convert word to markdown
- extract images from word
- create resources folder
- export images from docx
language: pt
og_description: Defina um caminho relativo de imagem em markdown ao converter Word
  para markdown, extraia imagens do Word e crie uma pasta de recursos para as imagens
  exportadas.
og_title: caminho relativo da imagem markdown – Converter Word para Markdown
tags:
- Aspose.Words
- C#
- Markdown
- Image Export
title: Caminho relativo da imagem em Markdown – Converter Word para Markdown
url: /pt/net/programming-with-markdownsaveoptions/markdown-image-relative-path-convert-word-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# caminho relativo de imagem markdown – Converter Word para Markdown

Já precisou de um **caminho relativo de imagem markdown** enquanto **converte Word para markdown**? Você não está sozinho. A maioria dos desenvolvedores encontra um obstáculo quando o Markdown gerado aponta para imagens em uma pasta plana, quebrando a estrutura de links relativos que você espera em um site estático ou em um repositório GitHub.

Neste tutorial, percorreremos uma solução completa, de ponta a ponta, que **extrai imagens do Word**, **cria uma pasta de recursos** e reescreve as referências de imagem para que usem um *caminho relativo de imagem markdown* limpo. Ao final, você terá um arquivo `.md` pronto para publicação e um diretório `Resources` organizadamente estruturado contendo todas as imagens extraídas do `.docx` original.

> **O que você receberá:** um único programa C# (sem scripts externos), uma explicação clara do *porquê* cada parte importa, e um conjunto de dicas práticas que você pode copiar‑colar em seus próprios projetos.

---

## Pré-requisitos

- **.NET 6.0** ou posterior instalado (você também pode direcionar o .NET Framework 4.7+, mas o .NET 6 é a escolha ideal para novos projetos).
- **Aspose.Words for .NET** (o pacote NuGet mais recente no momento da escrita, versão 23.12). Instale com:
  ```bash
  dotnet add package Aspose.Words
  ```
- Um documento Word que realmente contém imagens — vamos chamá‑lo de `WithImages.docx`.
- Uma pasta onde você deseja que o markdown de saída e as imagens fiquem, por exemplo `C:\Projects\MarkdownExport`.

Nenhuma biblioteca adicional é necessária; todo o resto é tratado pelo Aspose.Words.

---

## Etapa 1: Carregar o documento Word de origem (ponto de partida para converter Word para markdown)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Adjust the path to point at your own .docx file.
        string sourcePath = @"C:\Projects\MarkdownExport\WithImages.docx";

        // Load the document – this is where Aspose.Words parses the Word file.
        Document doc = new Document(sourcePath);
        
        // The rest of the workflow follows…
    }
}
```

*Por que isso importa:* Carregar o documento nos dá acesso à árvore interna de nós, que inclui as partes de imagem que mais tarde precisamos **exportar imagens do docx**. Se o carregamento falhar, nenhuma das etapas posteriores será executada, então verifique novamente o caminho e as permissões de arquivo.

---

## Etapa 2: Configurar `MarkdownSaveOptions` com um callback personalizado (o coração da criação da pasta de recursos)

O `ResourceSavingCallback` nos permite intervir toda vez que o Aspose.Words quiser gravar um arquivo de imagem. Dentro do callback, **criaremos uma sub‑pasta Resources** e ajustaremos a referência para que o markdown gerado use um *caminho relativo de imagem markdown*.

```csharp
// Inside Main(), after loading the document:
string outputFolder = @"C:\Projects\MarkdownExport";
string resourcesFolder = Path.Combine(outputFolder, "Resources");

// Make sure the folder exists before we start saving anything.
Directory.CreateDirectory(resourcesFolder);

// Set up the Markdown save options.
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    // Hook that runs for every image resource.
    ResourceSavingCallback = new MyMarkdownResourceCallback(resourcesFolder)
};

// Save the document as Markdown.
string markdownPath = Path.Combine(outputFolder, "Doc.md");
doc.Save(markdownPath, mdOptions);
```

Observe que passamos `resourcesFolder` para o construtor do callback — isso mantém o caminho da pasta flexível e evita codificar strings diretamente no código.

---

## Etapa 3: Implementar o callback que **cria a pasta de recursos** e reescreve o caminho

```csharp
/// <summary>
/// Handles image extraction and path rewriting for markdown export.
/// </summary>
class MyMarkdownResourceCallback : IResourceSavingCallback
{
    private readonly string _resourcesFolder;

    public MyMarkdownResourceCallback(string resourcesFolder)
    {
        _resourcesFolder = resourcesFolder;
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // 1️⃣ Build the full file system path where the image will be stored.
        string targetPath = Path.Combine(_resourcesFolder, args.ResourceFileName);
        
        // 2️⃣ Ensure the directory exists (in case Aspose creates sub‑folders).
        Directory.CreateDirectory(Path.GetDirectoryName(targetPath));

        // 3️⃣ Write the image stream to disk.
        using (FileStream fileStream = File.Create(targetPath))
        {
            args.Stream.CopyTo(fileStream);
        }

        // 4️⃣ Update the markdown reference to use a relative path.
        // This is the crucial line that gives us the markdown image relative path.
        args.ResourceFileName = Path.Combine("Resources", args.ResourceFileName);
    }
}
```

*Por que isso funciona:* `args.Stream` contém os bytes brutos da imagem. Ao copiá‑los para um arquivo dentro da nossa pasta `Resources`, **exportamos imagens do docx** com segurança. Em seguida, substituímos `args.ResourceFileName` por uma URL relativa (`Resources/image.png`). Quando o Aspose.Words posteriormente grava o markdown, ele injeta exatamente essa string, nos proporcionando o *caminho relativo de imagem markdown* desejado.

---

## Etapa 4: Verificar o Markdown gerado (como a saída final se parece)

Abra `Doc.md` em qualquer editor de texto. Você deverá ver algo semelhante a:

```markdown
# Sample Heading

Here is an inline picture:

![Image 0](Resources/Image_0.png)

And a picture inside a table:

![Image 1](Resources/Image_1.jpg)
```

A parte importante é que cada referência de imagem aponta para `Resources/...` – esse é o **caminho relativo de imagem markdown** que buscávamos.

![exemplo de caminho relativo de imagem markdown](example.png "exemplo de caminho relativo de imagem markdown")

*Dica:* Se você abrir o markdown em um visualizador que respeita links relativos (visualização do VS Code, GitHub ou um gerador de site estático), as imagens serão renderizadas corretamente sem nenhuma configuração adicional.

---

## Etapa 5: Armadilhas comuns e dicas avançadas

| Problema | Por que acontece | Como corrigir |
|----------|------------------|---------------|
| Imagens acabam na pasta raiz em vez de `Resources` | O callback não foi anexado ou `args.ResourceFileName` não foi sobrescrito. | Verifique novamente se `ResourceSavingCallback` está definido **antes** de chamar `doc.Save`. |
| Nomes de arquivos contêm caracteres ilegais | O Word às vezes nomeia imagens com espaços ou símbolos Unicode. | Use `Path.GetInvalidFileNameChars()` para sanitizar `args.ResourceFileName` dentro do callback. |
| Documentos grandes demoram muito para processar | Cada imagem é gravada de forma síncrona. | Altere para I/O assíncrono (`await args.Stream.CopyToAsync(fileStream)`) se você estiver no .NET 6+ e precisar de desempenho. |
| Caminhos relativos quebram quando o markdown é movido | O caminho é relativo à localização do arquivo markdown. | Mantenha `Doc.md` e a pasta `Resources` juntos, ou ajuste o callback para usar um prefixo relativo diferente (por exemplo, `../assets`). |

---

## Etapa 6: Expandindo a solução (e se você precisar de mais controle?)

- **Múltiplos formatos de saída:** Substitua `MarkdownSaveOptions` por `HtmlSaveOptions` ou `PdfSaveOptions` mantendo o mesmo callback — o Aspose.Words o invocará para cada imagem, independentemente do formato.
- **Nomeação personalizada de imagens:** Se quiser renomear imagens (por exemplo, `figure-01.png`), modifique `args.ResourceFileName` dentro do callback antes de gravar o arquivo.
- **Incorporar imagens como Base64:** Defina `args.ResourceFileName` como um data URI (`data:image/png;base64,...`) e pule a gravação do arquivo. Isso é útil para exportações de markdown em um único arquivo.

---

## Conclusão

Agora você tem um programa C# totalmente funcional que **converte Word para markdown**, **extrai imagens do word**, **cria uma pasta de recursos**, e garante um **caminho relativo de imagem markdown** limpo para cada imagem. O código é autônomo, funciona com a versão mais recente do Aspose.Words e pode ser inserido em qualquer projeto .NET com esforço mínimo.

Próximos passos? Experimente alimentar o markdown gerado em um gerador de site estático como Hugo ou Jekyll, ou experimente o callback para incorporar imagens diretamente como strings Base64. Se você encontrar casos extremos — por exemplo, imagens SVG ou arquivos incomumente grandes — consulte a tabela “Armadilhas comuns”; um pequeno ajuste geralmente resolve o problema.

Feliz codificação, e que seu markdown sempre aponte para a pasta correta!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}