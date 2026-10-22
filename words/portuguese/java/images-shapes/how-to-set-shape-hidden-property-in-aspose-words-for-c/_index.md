---
category: general
date: 2026-08-20
description: Aprenda como definir a propriedade Hidden de uma forma no Aspose.Words
  para C#. Este guia mostra como inserir uma imagem e ocultar a forma para que ela
  nunca apareça na interface do usuário ou na saída de impressão.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set shape hidden property
- insert image into document
- hide shape in Aspose.Words
- C# shape hidden property
- Aspose.Words DocumentBuilder
- prevent shape from printing
language: pt
lastmod: 2026-08-20
og_description: Defina a propriedade hidden da forma no Aspose.Words com C#. Insira
  uma imagem, oculte a forma e garanta que ela nunca apareça na interface do usuário
  ou na saída de impressão.
og_image_alt: Diagram illustrating set shape hidden property on a Word document shape
og_title: Definir a propriedade oculta de forma no Aspose.Words – guia completo em
  C#
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to set shape hidden property in Aspose.Words for C#. This
    guide shows inserting an image and hiding the shape so it never appears in the
    UI or print output.
  headline: How to set shape hidden property in Aspose.Words for C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document Automation
- Shape Handling
title: Como definir a propriedade Oculto da forma no Aspose.Words para C#
url: /pt/java/images-shapes/how-to-set-shape-hidden-property-in-aspose-words-for-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como definir a propriedade hidden de forma no Aspose.Words para C#

Se você precisar **definir a propriedade hidden de forma** em um documento Word, este tutorial mostra os passos exatos usando Aspose.Words para .NET. Seja construindo um mecanismo de templates, gerando relatórios ou incorporando um logotipo que deve permanecer invisível, você aprenderá como inserir uma imagem e ocultar a forma para que ela nunca apareça na interface do usuário ou na saída impressa.

Neste guia também abordamos **inserir imagem no documento**, explicamos por que ocultar uma forma é importante para impressão e percorremos o código completo e executável. Nenhuma referência externa é necessária — basta copiar, colar e executar.

## Pré‑requisitos

Antes de começar, certifique‑se de que você tem:

* .NET 6.0 ou superior (a versão mais recente do Aspose.Words tem como alvo .NET 6+)
* Uma licença válida do Aspose.Words para .NET (ou use o modo de avaliação gratuito)
* Visual Studio 2022 ou qualquer IDE C# de sua preferência
* Um arquivo de imagem (por exemplo, `logo.png`) colocado em uma pasta que você possa referenciar a partir do código

## Etapa 1: Criar um novo Document e DocumentBuilder

A classe `DocumentBuilder` é o ponto de entrada para construir conteúdo Word programaticamente. Ela permite inserir parágrafos, tabelas e formas como imagens.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Initialize a new blank document
        Document doc = new Document();
        // DocumentBuilder provides methods to add content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Por que esta etapa?*  
Criar um `Document` fornece uma representação em memória de um arquivo .docx, enquanto o `DocumentBuilder` oferece a API fluente que insere objetos. Sem esses objetos você não pode colocar uma forma no documento.

## Etapa 2: Inserir a imagem como uma forma

Aspose.Words trata cada foto como um `Shape`. O método `InsertImage` devolve essa instância de `Shape`, que você pode manipular posteriormente.

```csharp
        // Step 2: Insert an image into the document
        // The returned Shape object lets us modify properties like size, rotation, and visibility.
        Shape picture = builder.InsertImage(@"YOUR_DIRECTORY\logo.png");
```

*Por que esta etapa?*  
Usar `InsertImage` não apenas adiciona a foto ao fluxo de texto, mas também fornece uma referência (`picture`) que você pode configurar. Isso é essencial para a **propriedade hidden da forma em C#** que definiremos a seguir.

## Etapa 3: Definir a propriedade hidden da forma

A propriedade `Hidden` controla se a forma participa da UI e da impressão. Defini‑la como `true` torna a forma invisível na UI do Word e garante que não será impressa.

```csharp
        // Step 3: Hide the inserted shape so it won't appear in the UI or print output
        picture.Hidden = true;
```

*Por que esta etapa?*  
Quando uma forma é marcada como oculta, o Word a trata como um comentário — presente na estrutura do documento, mas nunca renderizada. Este é o núcleo de **definir a propriedade hidden de forma**.

## Etapa 4: Salvar o documento

Por fim, grave o documento no disco. Você pode escolher qualquer formato suportado pelo Aspose.Words (`.docx`, `.pdf`, `.html`, etc.).

```csharp
        // Step 4: Save the document to a .docx file
        doc.Save(@"OUTPUT\HiddenImageDocument.docx");
        // Optional: Save as PDF to verify the shape really stays hidden when printed
        doc.Save(@"OUTPUT\HiddenImageDocument.pdf");
    }
}
```

*Por que esta etapa?*  
Salvar finaliza as alterações em memória. Abrir o `.docx` resultante no Microsoft Word não mostra nenhuma imagem visível, e a exportação para PDF confirma que a forma nunca aparece na saída impressa.

## Exemplo completo e executável

Juntando tudo, aqui está o programa completo que você pode compilar e executar:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeHiddenDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Initialize a blank document and a builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert an image as a shape
            // Replace YOUR_DIRECTORY with the actual folder that contains logo.png
            Shape picture = builder.InsertImage(@"YOUR_DIRECTORY\logo.png");

            // 3️⃣ Set the shape hidden property
            picture.Hidden = true; // This hides the shape in UI and when printing

            // 4️⃣ Save the document in both DOCX and PDF formats
            doc.Save(@"OUTPUT\HiddenImageDocument.docx");
            doc.Save(@"OUTPUT\HiddenImageDocument.pdf");

            Console.WriteLine("Document created successfully. The image is hidden.");
        }
    }
}
```

**Saída esperada**

* Ao abrir `HiddenImageDocument.docx` no Microsoft Word, nenhuma imagem será visível.
* Exportar ou imprimir o documento (ou abrir o PDF) também não mostrará a imagem.
* A forma oculta ainda existe no XML do documento, o que pode ser verificado abrindo o `.docx` como um zip e inspecionando `word/document.xml` — você verá um elemento `<w:pict>` com `w:hidden="true"`.

## Variações comuns e casos de borda

| Situação | O que fazer | Por que isso importa |
|-----------|------------|----------------------|
| **Arquivo de imagem ausente** | Envolva `InsertImage` em um `try/catch` e trate `FileNotFoundException`. | Impede que a aplicação trave e permite registrar um erro claro. |
| **Múltiplas formas ocultas** | Chame `picture.Hidden = true` para cada `Shape` que inserir, ou itere sobre `doc.GetChildNodes(NodeType.Shape, true)`. | Garante que todo elemento visual indesejado permaneça invisível. |
| **Precisar que a forma seja visível apenas no modo de edição** | Defina `picture.Hidden = false` após a edição, depois volte a marcar antes de salvar. | Permite trabalhar com a forma na UI enquanto mantém a saída final limpa. |
| **Impressão em versões antigas do Word** | Verifique o documento com Word 2010 ou posterior; a flag hidden é suportada em todas as versões modernas. | Assegura compatibilidade para toda a sua base de usuários. |
| **Usar um formato de arquivo diferente (por exemplo, PDF direto)** | A flag `Hidden` funciona da mesma forma; o Aspose.Words a respeita durante a conversão para PDF. | Confirma que **impedir a forma de ser impressa** funciona para todos os destinos de exportação. |

## Dica profissional: Verificar a flag hidden programaticamente

Se precisar confirmar que uma forma está oculta antes de salvar, você pode inspecionar a propriedade:

```csharp
bool isHidden = picture.Hidden;
Console.WriteLine($"Shape hidden? {isHidden}");
```

Esta verificação simples é útil em pipelines automatizados onde é necessário garantir conformidade com políticas de geração de documentos.

## Conclusão

Agora você sabe como **definir a propriedade hidden de forma** no Aspose.Words para C#. Inserindo uma imagem, aplicando `picture.Hidden = true` e salvando o documento, a forma permanece fora da UI e nunca aparece na saída impressa. Essa técnica é essencial quando você precisa de marcadores de posição, marcas d'água ou elementos de branding que devem permanecer invisíveis para os usuários finais.

### O que vem a seguir?

* Explore outras propriedades de forma como `picture.WrapType`, `picture.Rotation` e `picture.RelativeHorizontalPosition`.
* Aprenda a **ocultar forma no Aspose.Words** de forma condicional com base na entrada do usuário ou em configurações.
* Combine formas ocultas com loops de **inserir imagem no documento** para gerar marcadores invisíveis dinâmicos para processamento posterior (por exemplo, campos de mala‑direta).

Sinta‑se à vontade para experimentar diferentes formatos de imagem, layouts de documento e destinos de exportação. Ocultar formas oferece controle granular sobre o que seus leitores realmente veem — e o que permanece nos bastidores. Boa codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Criar forma retangular no Word com Aspose.Words – Guia passo a passo](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Criar Group Shape em documento Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Inserir imagem inline em documento Word usando Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}