---
category: general
date: 2026-09-08
description: Aprenda como inserir controle de conteúdo em um documento Word usando
  C# e Aspose.Words. Inclui etapas para criar o controle de conteúdo, definir o espaço
  reservado e salvar o arquivo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert content control
- create content control
language: pt
lastmod: 2026-09-08
og_description: Inserir controle de conteúdo em um arquivo Word usando C# e Aspose.Words.
  Siga este guia para criar controle de conteúdo, definir texto de espaço reservado
  e salvar o documento.
og_image_alt: Insert content control example in a Word document
og_title: Inserir controle de conteúdo no Word com C# – guia passo a passo
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to insert content control in a Word document using C# and
    Aspose.Words. Includes steps to create content control, set placeholder, and save
    the file.
  headline: How to insert content control in a Word document with C#
  type: TechArticle
tags:
- content control
- Aspose.Words
- C#
- Word automation
title: Como inserir controle de conteúdo em um documento Word com C#
url: /pt/net/programming-with-sdt/how-to-insert-content-control-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como inserir controle de conteúdo em um documento Word com C#

Se você precisar **inserir controle de conteúdo** em um documento Word, este guia mostra uma solução completa e executável. Você também aprenderá como **criar controle de conteúdo** programaticamente, definir texto de espaço reservado e gravar o arquivo no disco.

Os controles de conteúdo permitem definir regiões que os usuários podem preencher, repetir ou bloquear. Eles são amplamente usados para modelos, formulários e relatórios dinâmicos. As etapas abaixo utilizam a biblioteca Aspose.Words for .NET, que funciona com .NET 6+, .NET Framework 4.6+ e .NET Core.

## Como inserir controle de conteúdo em um documento Word

1. **Adicionar Aspose.Words ao seu projeto**  
   Abra um terminal na pasta do projeto e execute:

   ```bash
   dotnet add package Aspose.Words
   ```

   O pacote contém as classes `Document`, `DocumentBuilder` e `StructuredDocumentTag` necessárias para controles de conteúdo.

2. **Criar um novo documento vazio**  

   ```csharp
   // Step 1: Create a new empty document and a DocumentBuilder
   Document doc = new Document();
   DocumentBuilder builder = new DocumentBuilder(doc);
   ```

   O objeto `Document` representa todo o arquivo .docx, enquanto `DocumentBuilder` fornece um cursor conveniente para inserir nós.

## Criando um controle de conteúdo com Aspose.Words

Os controles de conteúdo são representados pela classe `StructuredDocumentTag` (SDT). O código a seguir cria um controle de conteúdo **plain‑text** e atribui a ele um título que pode ser consultado posteriormente.

```csharp
// Step 2: Create a plain‑text StructuredDocumentTag (content control)
//         - Set a title that can be used to identify the control
//         - Provide placeholder text that appears when the control is empty
StructuredDocumentTag sdt = new StructuredDocumentTag(
    doc,
    SdtType.PlainText,      // Plain‑text control
    MarkupLevel.Block);    // Block‑level control (behaves like a paragraph)

sdt.Title = "CustomerName";
sdt.PlaceholderName = "Enter name here";
```

*Por que isso importa:*  
- `SdtType.PlainText` garante que o controle aceite apenas caracteres simples.  
- `MarkupLevel.Block` faz com que o controle se comporte como um parágrafo completo, o que é ideal para campos de formulário.  
- A propriedade `Title` é um identificador estável que pode ser usado ao pesquisar ou vincular dados.

## Definindo texto de espaço reservado e texto padrão

Um espaço reservado orienta o usuário antes que ele digite algo. Você também pode pré‑popular o controle com conteúdo padrão.

```csharp
// Step 4: Optionally set default content for the control
sdt.XmlMapping.SetXmlFragment("<text>John Doe</text>");
```

O fragmento XML deve corresponder ao tipo de dados do controle. Para controles plain‑text, o elemento `<text>` é obrigatório. Se você omitir esta etapa, o espaço reservado definido anteriormente será exibido.

## Inserindo o controle de conteúdo no local desejado

O cursor do `DocumentBuilder` determina onde o controle aparece. Por padrão, o cursor está no início do documento.

```csharp
// Step 3: Insert the StructuredDocumentTag into the document at the builder's current position
builder.InsertNode(sdt);
```

Se precisar do controle dentro de uma tabela, cabeçalho ou após parágrafos existentes, mova o builder primeiro:

```csharp
builder.MoveToDocumentEnd();   // Example: place the control at the end of the file
builder.InsertNode(sdt);
```

## Salvando o documento com o controle de conteúdo inserido

```csharp
// Step 5: Save the document with the content control
doc.Save(@"C:\Temp\SDT.docx");
```

O arquivo `SDT.docx` agora contém um controle de conteúdo plain‑text intitulado **CustomerName** com o espaço reservado “Enter name here” e o texto padrão “John Doe”.

![Exemplo de inserção de controle de conteúdo em um documento Word](insert-content-control.png)

*Texto alternativo da imagem:* Exemplo de inserção de controle de conteúdo em um documento Word

### Resultado esperado

Ao abrir `SDT.docx` no Microsoft Word:

- Um espaço reservado cinza “Enter name here” aparece se você excluir o texto padrão.  
- O controle é destacado quando você clica dentro dele, indicando que pode ser editado.  
- A aba **Developer** (se habilitada) mostra o título do controle **CustomerName** no painel Propriedades.

## Exemplo completo em funcionamento

Abaixo está um programa único e autocontido que você pode copiar, compilar e executar. Ele demonstra cada etapa, desde a configuração do projeto até a gravação do arquivo.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

class InsertContentControlDemo
{
    static void Main()
    {
        // 1. Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Create a plain‑text content control (StructuredDocumentTag)
        StructuredDocumentTag sdt = new StructuredDocumentTag(
            doc,
            SdtType.PlainText,
            MarkupLevel.Block);

        sdt.Title = "CustomerName";          // Identifier for later use
        sdt.PlaceholderName = "Enter name here";

        // 3. Insert the control at the current cursor position
        builder.InsertNode(sdt);

        // 4. Set default text (optional)
        sdt.XmlMapping.SetXmlFragment("<text>John Doe</text>");

        // 5. Save the document
        string outputPath = @"C:\Temp\SDT.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Execute o programa com `dotnet run`. Após a execução, abra o arquivo gerado para verificar se o controle de conteúdo aparece conforme descrito.

## Dicas práticas e armadilhas comuns

| Situação | Abordagem recomendada |
|-----------|----------------------|
| **Vários controles do mesmo tipo** | Atribua a cada controle um `Title` exclusivo. Você pode recuperar um controle posteriormente com `doc.GetChildNodes(NodeType.StructuredDocumentTag, true).Cast<StructuredDocumentTag>().FirstOrDefault(s => s.Title == "YourTitle")`. |
| **Controle não visível no Word** | Certifique‑se de que salvou o documento com a extensão `.docx` e que a versão do `Aspose.Words` é compatível com a sua versão do Office. |
| **Necessita de um controle rich‑text** | Use `SdtType.RichText` em vez de `PlainText`. O fragmento XML então usa elementos `<w:richText>`. |
| **Colocando o controle dentro de uma célula de tabela** | Mova o builder para a célula primeiro: `builder.MoveTo(cell.FirstParagraph); builder.InsertNode(sdt);`. |
| **Desempenho com documentos grandes** | Crie o `StructuredDocumentTag` uma vez e reutilize‑lo se precisar de muitos controles idênticos; clone‑o via `sdt.Clone(true)`. |

## Próximos passos

- **Criar controles de conteúdo repetitivos** (`SdtType.RepeatingSection`) para tabelas que crescem dinamicamente.  
- **Vincular controles de conteúdo a dados XML** usando `sdt.XmlMapping.LoadXml(xmlString)`.  
- **Bloquear o controle** (`sdt.LockContentControl = true`) para impedir edições do usuário enquanto ainda permite atualizações programáticas.  

Explorar esses tópicos aprofundará sua capacidade de criar modelos Word robustos com Aspose.Words.

---

**Conclusão**  
Agora você sabe como **inserir controle de conteúdo** em um documento Word usando C#. O tutorial abordou a criação do controle, a definição de texto de espaço reservado e texto padrão, a inserção no local desejado e a gravação do arquivo final. Com essa base, você pode criar formulários sofisticados, modelos de mala‑direta e relatórios automatizados que aproveitam os recursos nativos de controle de conteúdo do Word.

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Definir estilo do controle de conteúdo](/words/english/net/programming-with-sdt/set-content-control-style/)
- [Definir cor do controle de conteúdo](/words/english/net/programming-with-sdt/set-content-control-color/)
- [Como criar campos de formulário e adicionar conteúdo usando DocumentBuilder no Aspose.Words para Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}