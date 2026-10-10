---
category: general
date: 2026-10-10
description: Crie um documento Word em branco, insira a imagem no Word, adicione um
  grupo de imagens e oculte a forma no arquivo salvo. Siga este guia passo a passo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert image into word
- add image group
- hide shape word document
language: pt
lastmod: 2026-10-10
og_description: Crie um documento Word em branco, insira uma imagem no Word, adicione
  um grupo de imagens e oculte a forma. Este guia mostra o código C# completo.
og_image_alt: Screenshot of a blank Word document with a hidden image group
og_title: Criar um documento Word em branco, adicionar um grupo de imagens, ocultar
  forma
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Create a blank Word document, insert image into Word, add an image
    group, and hide shape in the saved file. Follow this step‑by‑step guide.
  headline: Create a blank Word document, add an image group, hide shape
  type: TechArticle
tags:
- Word automation
- Aspose.Words
- C#
- Document processing
title: Criar um documento Word em branco, adicionar um grupo de imagens, ocultar forma
url: /pt/java/images-shapes/create-a-blank-word-document-add-an-image-group-hide-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar um documento Word em branco, adicionar um grupo de imagens, ocultar forma

Se você precisa **criar um documento Word em branco** e posteriormente ocultar elementos visuais, este tutorial mostra exatamente como fazer. Você aprenderá a inserir imagem no Word, adicionar um grupo de imagens e ocultar a forma no documento Word em uma única rotina reutilizável em C#.

Usaremos a biblioteca Aspose.Words for .NET, que permite manipular arquivos .docx sem que o Microsoft Word esteja instalado. Ao final deste guia você terá um programa executável que produz um arquivo Word contendo um grupo de imagens oculto, pronto para processamento posterior ou exibição condicional.

## Pré-requisitos

- .NET 6.0 ou posterior (o código também funciona com .NET Framework 4.6+)
- Pacote NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)
- Uma pasta no disco onde você possa ler um arquivo de imagem e gravar o documento de saída
- Familiaridade básica com C# e Visual Studio (ou qualquer IDE de sua preferência)

## Criar um documento Word em branco com Aspose.Words

O primeiro passo é **criar um documento Word em branco**. Aspose.Words fornece a classe `Document` que representa um arquivo Word em memória. Instanciá‑la sem argumentos fornece um documento vazio pronto para receber conteúdo.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document doc = new Document();                 // blank .docx container
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Por que isso importa:* Começar com um documento em branco garante que nenhuma formatação oculta ou seções residuais interfiram na forma que você adicionará posteriormente.

## Inserir imagem no Word usando DocumentBuilder

Em seguida, **inserimos imagem no Word** criando primeiro uma forma de grupo que conterá a imagem. Formas de grupo permitem tratar vários objetos de desenho como uma única unidade, o que é útil quando você quiser ocultá‑los ou movê‑los juntos mais tarde.

```csharp
        // Step 2: Insert a group shape with the desired size (width: 300, height: 200)
        GroupShape group = builder.InsertGroupShape(300, 200);
```

O método `InsertGroupShape` cria um contêiner vazio. As dimensões são em pontos (1 ponto = 1/72 polegada). Ajuste o tamanho para corresponder à resolução da imagem que você pretende incorporar.

## Adicionar grupo de imagens ao documento

Agora **adicionamos o grupo de imagens** movendo o cursor do builder para dentro do grupo recém‑criado e inserindo a foto. Todas as inserções subsequentes farão parte do grupo.

```csharp
        // Step 3: Position the builder inside the group so subsequent inserts go into it
        builder.MoveTo(group);

        // Step 4: Add an image to the group shape
        // Replace the path with the actual location of your PNG/JPEG file
        builder.InsertImage(@"YOUR_DIRECTORY\photo1.png");
```

*Dica:* Use um caminho absoluto ou um caminho relativo corretamente escapado; caso contrário `InsertImage` lançará uma `FileNotFoundException`.

## Ocultar forma em um documento Word

Por fim, **ocultamos a forma no documento Word** definindo a propriedade `Hidden` do grupo como `true`. Formas ocultas não são exibidas quando o documento é aberto no Word, mas permanecem no arquivo e podem ser reveladas programaticamente depois.

```csharp
        // Step 5: Hide the entire group (the image will not be visible in the saved document)
        group.Hidden = true;

        // Step 6: Save the document with the hidden group
        doc.Save(@"YOUR_DIRECTORY\GroupHidden.docx");
    }
}
```

Ao abrir *GroupHidden.docx* no Microsoft Word, você verá uma página completamente em branco porque o grupo de imagens está oculto. O arquivo ainda contém os dados da imagem, que podem ser revelados posteriormente com `group.Hidden = false`, se necessário.

## Exemplo completo e executável

Abaixo está o programa completo que você pode copiar‑colar em um novo projeto de console:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a blank Word document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a group shape (300 pt × 200 pt)
            GroupShape group = builder.InsertGroupShape(300, 200);

            // 3️⃣ Move inside the group so inserts become part of it
            builder.MoveTo(group);

            // 4️⃣ Insert the image (replace with your own file)
            builder.InsertImage(@"YOUR_DIRECTORY\photo1.png");

            // 5️⃣ Hide the group so the image is not shown
            group.Hidden = true;

            // 6️⃣ Save the result
            doc.Save(@"YOUR_DIRECTORY\GroupHidden.docx");

            Console.WriteLine("Document created successfully.");
        }
    }
}
```

**Saída esperada**

- Um arquivo chamado `GroupHidden.docx` aparece em `YOUR_DIRECTORY`.
- Ao abrir o arquivo no Word, uma página vazia é exibida.
- A imagem oculta pode ser revelada alterando `group.Hidden = false` e salvando novamente.

## Variações comuns e casos de borda

| Situação | Como adaptar o código |
|-----------|----------------------|
| **Múltiplas imagens** | Insira chamadas adicionais de `InsertImage` após `builder.MoveTo(group)`. Todas as imagens permanecem dentro do mesmo grupo e compartilham a flag hidden. |
| **Formatos de imagem diferentes** | Aspose.Words suporta PNG, JPEG, BMP, GIF, TIFF. Basta mudar a extensão do arquivo; nenhuma alteração no código é necessária. |
| **Visibilidade condicional** | Armazene uma variável de documento personalizada (`doc.Variables.Add("ShowImages", "true")`) e altere `group.Hidden` com base no seu valor em tempo de execução. |
| **Documentos grandes** | Crie o grupo em uma página específica (`builder.InsertBreak(BreakType.PageBreak)`) antes de inserir o grupo para evitar deslocamentos de layout. |
| **Compatibilidade com versões antigas do Word** | Salve como `doc.Save("output.doc", SaveFormat.Doc)` se precisar do formato legado `.doc`; formas ocultas se comportam da mesma forma. |

**Dica profissional:** Sempre defina `group.Hidden = true` *depois* de inserir todos os elementos filhos. Alterar a flag antes de adicionar o conteúdo pode fazer com que alguns elementos sejam renderizados inesperadamente em versões mais antigas do Word.

## Conclusão

Agora você sabe como **criar um documento Word em branco**, **inserir imagem no Word**, **adicionar um grupo de imagens** e **ocultar forma no documento Word** usando Aspose.Words for .NET. O exemplo completo demonstra cada passo, desde a inicialização do documento até a gravação de um arquivo que contém um grupo de imagens oculto.

Em seguida, você pode explorar:

- Adicionar caixas de texto ou gráficos ao mesmo grupo
- Usar `DocumentBuilder.StartBookmark` / `EndBookmark` para marcar seções ocultas
- Alternar a visibilidade programaticamente com base na entrada do usuário ou em variáveis de documento

Sinta‑se à vontade para experimentar diferentes formas, tamanhos e regras de visibilidade para adequar ao seu cenário de automação. Boa codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document with Floating Image in .NET](/words/english/net/add-content-using-documentbuilder/insert-floating-image/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}