---
category: general
date: 2026-09-05
description: Aprenda como criar um grupo de formas docx, inserir um botão de comando
  ActiveX e carregar Markdown em um documento Word com um exemplo completo em C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create group shape docx
- insert activex command button
- load markdown into word document
language: pt
lastmod: 2026-09-05
og_description: Crie um documento docx com forma de grupo, insira um botão de comando
  ActiveX e carregue Markdown em um documento Word usando C#. Siga este tutorial passo
  a passo.
og_image_alt: Screenshot of a Word document showing a grouped shape and an ActiveX
  button
og_title: Criar forma de grupo em docx e incorporar controles ActiveX – Guia C#
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Learn how to create group shape docx, insert ActiveX command button,
    and load Markdown into a Word document with a complete C# example.
  headline: How to create group shape docx and add interactive controls in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document automation
title: Como criar um grupo de shapes docx e adicionar controles interativos em C#
url: /pt/java/images-shapes/how-to-create-group-shape-docx-and-add-interactive-controls/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como criar group shape docx e adicionar controles interativos em C#

Se você precisa **create group shape docx** arquivos programaticamente, este guia mostra exatamente como. Você também verá como **insert ActiveX command button** controles e **load Markdown into a Word document** sem perder a formatação de sublinhado. Ao final do tutorial você terá um `.docx` totalmente funcional que combina gráficos vetoriais, elementos de UI interativos e conteúdo baseado em markdown.

Este tutorial assume que você tem um ambiente básico de desenvolvimento C# e a biblioteca Aspose.Words for .NET instalada. Nenhuma ferramenta externa é necessária — tudo roda dentro de um console ou aplicativo desktop .NET padrão.

## Pré-requisitos

- .NET 6.0 SDK ou posterior (o código também funciona com .NET Framework 4.7+)
- Aspose.Words for .NET (pacote NuGet `Aspose.Words`)
- Um certificado X.509 válido (`.pfx`) se você quiser testar a etapa de assinatura
- Um arquivo de imagem (ex., `logo.png`) e um arquivo markdown (`sample.md`) colocados em uma pasta conhecida

> **Dica profissional:** Mantenha todos os arquivos de entrada em uma única pasta *resources* para simplificar caminhos relativos.

## Etapa 1: Configurar o projeto e importar namespaces

Crie um novo projeto de console e adicione as diretivas `using` necessárias. Este bloco também demonstra como referenciar as classes Aspose.Words que você usará mais tarde.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Loading;
using Aspose.Words.Saving;
using Aspose.Words.Saving.XpsSaveOptions; // only needed for signing example
using Aspose.Words.Saving.Signature;

// Ensure the license is applied if you have one
// Aspose.Words.License license = new Aspose.Words.License();
// license.SetLicense("Aspose.Words.lic");
```

As instruções `using` dão acesso direto a `Document`, `DocumentBuilder`, `GroupShape`, `Forms2OleControl` e outros tipos usados ao longo do tutorial.

## Etapa 2: **Create group shape docx** – adicionar uma forma agrupada com elementos filhos

Um *group shape* permite tratar múltiplos objetos de desenho como uma única unidade. Isso é útil para mover ou redimensionar gráficos relacionados juntos.

```csharp
// Initialize a new empty document
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a group shape container
GroupShape group = builder.InsertGroupShape();

// Add a rectangle (100 × 50 points) as the first child
Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);
group.AppendChild(rect);

// Add an ellipse (80 × 40 points) as the second child
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 40);
group.AppendChild(ellipse);

// Optional: set a fill color for visual distinction
rect.FillColor = System.Drawing.Color.LightBlue;
ellipse.FillColor = System.Drawing.Color.LightCoral;

// Save the intermediate document so you can inspect the group
document.Save("Output/GroupShape.docx");
```

**Por que um group shape?**  
Agrupar mantém o retângulo e a elipse alinhados quando o usuário os arrasta no Word. Também simplifica operações posteriores, como aplicar uma borda comum ou mover todo o gráfico programaticamente.

## Etapa 3: Inserir um controle de conteúdo plain‑text (marcador de posição para entrada do usuário)

Controles de conteúdo fornecem aos usuários finais uma área estruturada para digitar texto. O texto do marcador de posição desaparece assim que o usuário começa a digitar.

```csharp
// Insert a plain‑text StructuredDocumentTag (SDT) after the group shape
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    SdtType.PlainText, "MyTag");

// Set a friendly placeholder that appears in the UI
sdt.PlaceholderName = "Enter text here";

// Optionally, lock the content control to prevent deletion
sdt.LockContents = false;
sdt.LockContentControl = false;
```

A propriedade `PlaceholderName` é o que o Word mostra como uma dica em cinza‑claro. Os usuários podem substituí‑la pelo próprio texto, e o XML subjacente permanece bem‑formado.

## Etapa 4: **Insert ActiveX command button** – adicionar UI interativa ao documento

Controles ActiveX ainda são suportados em arquivos Word modernos e podem disparar macros ou automação externa. Abaixo adicionamos um *command button* e definimos sua legenda.

```csharp
// Insert an ActiveX Forms2OleControl at the current cursor position
Forms2OleControl commandBtn = builder.InsertForms2OleControl();

// Define the control type as a command button
commandBtn.ControlType = Forms2OleControl.ControlType.CommandButton;

// Set the visible caption
commandBtn.Caption = "Click Me";

// Position the button relative to the page (optional)
commandBtn.Left = 150;   // points from the left margin
commandBtn.Top = 300;    // points from the top margin
```

**Quando usar um botão ActiveX?**  
Se você distribuir o documento em um ambiente corporativo que depende de macros VBA, um botão ActiveX pode iniciar uma macro ou abrir um aplicativo externo. Para interatividade puramente baseada em HTML, considere usar *content controls* com *Office.js* em vez disso.

## Etapa 5: Inserir uma imagem oculta (ex., um logo) para branding ou acesso posterior por script

Formas ocultas não são exibidas no documento impresso, mas permanecem no XML, permitindo que você as recupere programaticamente mais tarde.

```csharp
// Insert an image from disk
Shape logo = builder.InsertImage("Resources/logo.png");

// Hide the image from the view/layout
logo.Hidden = true;

// You can still reference the image via its ShapeId if needed
string logoId = logo.Name;
```

## Etapa 6: **Load markdown into a Word document** enquanto preserva a formatação de sublinhado

Aspose.Words pode importar Markdown diretamente. Ativar `ImportUnderlineFormatting` garante que sublinhados do markdown (`<u>` ou `__texto__`) se tornem estilos de sublinhado do Word em vez de texto simples.

```csharp
// Configure markdown load options
MarkdownLoadOptions mdOptions = new MarkdownLoadOptions
{
    ImportUnderlineFormatting = true
};

// Load the markdown file into a new Document instance
Document markdownDoc = new Document("Resources/sample.md", mdOptions);

// Append the markdown content to the main document after the previous elements
builder.MoveToDocumentEnd();
builder.InsertDocument(markdownDoc, ImportFormatMode.KeepSourceFormatting);
```

**Caso extremo:** Se o arquivo markdown contiver tabelas, elas são convertidas automaticamente em tabelas do Word. Se precisar de estilo de tabela personalizado, aplique um `DocumentBuilder` após a inserção.

## Etapa 7: Assinar o documento com XAdES‑EPES (etapa de segurança opcional)

Assinaturas digitais garantem a integridade do documento. O código a seguir assina o arquivo **create group shape docx** usando um perfil XAdES‑EPES.

```csharp
// Initialize the signature object for the current document
Signature signature = new Signature(document);

// Choose the XAdES‑EPES level
signature.XmlDsigLevel = XmlDsigLevel.XAdES_EPES;

// Sign using a .pfx certificate (replace path and password)
signature.Sign("Resources/cert.pfx", "password");

// Save the signed document
document.Save("Output/SignedGroupShape.docx");
```

> **Nota de segurança:** Mantenha a senha do certificado fora do controle de versão. Use variáveis de ambiente ou um cofre seguro em produção.

## Exemplo completo executável

Juntando todas as etapas resulta em um programa único e autocontido. Salve o arquivo como `Program.cs` e execute‑o a partir da linha de comando.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Loading;
using Aspose.Words.Saving.Signature;

class Program
{
    static void Main()
    {
        // 1️⃣ Create the document and group shape
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        GroupShape group = builder.InsertGroupShape();
        group.AppendChild(builder.InsertShape(ShapeType.Rectangle, 100, 50));
        group.AppendChild(builder.InsertShape(ShapeType.Ellipse, 80, 40));

        // 2️⃣ Add a plain‑text content control
        StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
            SdtType.PlainText, "MyTag");
        sdt.PlaceholderName = "Enter text here";

        // 3️⃣ Insert an ActiveX command button
        Forms2OleControl btn = builder.InsertForms2OleControl();
        btn.ControlType = Forms2OleControl.ControlType.CommandButton;
        btn.Caption = "Click Me";

        // 4️⃣ Insert a hidden logo image
        Shape logo = builder.InsertImage("Resources/logo.png");
        logo.Hidden = true;

        // 5️⃣ Load markdown while keeping underline formatting
        MarkdownLoadOptions mdOpts = new MarkdownLoadOptions
        {
            ImportUnderlineFormatting = true
        };
        Document mdDoc = new Document("Resources/sample.md", mdOpts);
        builder.MoveToDocumentEnd();
        builder.InsertDocument(mdDoc, ImportFormatMode.KeepSourceFormatting);

        // 6️⃣ Sign the document (optional)
        Signature sig = new Signature(doc);
        sig.XmlDsigLevel = XmlDsigLevel.XAdES_EPES;
        sig.Sign("Resources/cert.pfx", "password");

        // Save the final file
        doc.Save("Output/CompleteGroupShape.docx");
        Console.WriteLine("Document created successfully.");
    }
}
```

Executar o programa gera `CompleteGroupShape.docx` contendo:

- Um retângulo + elipse agrupados (o núcleo **create group shape docx**)
- Um controle de conteúdo plain‑text com texto de marcador de posição
- Um **insert ActiveX command button** rotulado “Click Me”
- Uma imagem de logo oculta
- Conteúdo Markdown com sublinhados preservados
- Uma assinatura digital XAdES‑EPES (se o certificado for fornecido)

## Perguntas comuns e solução de problemas

| Pergunta | Resposta |
|---|---|
| **O botão ActiveX funcionará no Word macOS?** | O Word para macOS não suporta controles ActiveX. O botão aparecerá como uma imagem estática. Use content controls com Office.js para interatividade multiplataforma. |
| **E se o arquivo markdown contiver CSS personalizado?** | Aspose.Words ignora CSS; apenas a sintaxe padrão de markdown é processada. Converta os elementos estilizados com CSS para estilos do Word manualmente após a importação. |
| **Posso adicionar mais formas ao mesmo grupo mais tarde?** | Sim. Recupere o `GroupShape` pelo nome ou índice, então chame `AppendChild(newShape)`. Lembre‑se de salvar o documento novamente após as modificações. |
| **Como mudar o algoritmo de assinatura?** | Defina `signature.SignatureAlgorithm` antes de chamar `Sign`. O padrão é SHA‑256, que atende à maioria dos requisitos de conformidade. |
| **A imagem oculta é visível na interface do Word?** | Não, mas pode ser exibida ao ativar *Show hidden text* nas opções do Word. Isso é útil para armazenar metadados sem poluir o layout. |

## Próximos passos

Agora que você pode **create group shape docx**, **insert ActiveX command button** e **load markdown into a Word document**, você pode explorar:

- **Embedding VBA macros** que reagem ao clique do botão ActiveX.
- **Applying custom styles** aos parágrafos gerados a partir do markdown.
- **Generating PDFs** a partir do mesmo documento usando `doc.Save("output.pdf", SaveFormat.Pdf)`.
- **Automating batch processing** de múltiplos arquivos markdown em um único relatório compilado.

Essas extensões permitem construir pipelines de documentos totalmente automatizados que combinam gráficos ricos, controles interativos e autoria baseada em markdown — tudo a partir de C#.

---

*Feliz codificação! Se você achou este tutorial

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Criar Group Shape em Documento Word Usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Criar forma retangular no Word usando C# – Guia passo a passo](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Criar markdown a partir do Word – Guia completo em C#](/words/english/java/document-conversion-and-export/create-markdown-from-word-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}