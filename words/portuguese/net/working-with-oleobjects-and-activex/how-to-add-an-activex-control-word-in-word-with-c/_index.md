---
category: general
date: 2026-09-30
description: Adicione um controle ActiveX a um documento do Word usando C#. Aprenda
  a inserir um botão ActiveX, adicionar um botão de comando e torná‑lo clicável.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- activex control word
- how to insert activex
- how to add command button
- insert activex button
- add clickable button word
language: pt
lastmod: 2026-09-30
og_description: Adicione um controle ActiveX a um documento do Word com C#. Siga este
  guia completo para inserir um botão ActiveX, adicionar um botão de comando e torná‑lo
  clicável.
og_image_alt: Word document displaying an inserted ActiveX command button
og_title: Adicionar um controle ActiveX de palavra aos documentos do Word – guia passo
  a passo em C#
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Add an ActiveX control word to a Word document using C#. Learn how
    to insert an ActiveX button, add a command button, and make it clickable.
  headline: How to add an ActiveX control word in Word with C#
  type: TechArticle
tags:
- ActiveX
- Aspose.Words
- C#
- Word automation
title: Como adicionar um controle ActiveX no Word com C#
url: /pt/net/working-with-oleobjects-and-activex/how-to-add-an-activex-control-word-in-word-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como adicionar uma palavra de controle ActiveX no Word com C#

Se você precisar incorporar uma **palavra de controle ActiveX** dentro de um arquivo Microsoft Word, este guia mostra exatamente como fazer isso. Você verá um exemplo completo e executável que insere um botão clicável, salva o documento e funciona com a versão mais recente do Aspose.Words para .NET.

Adicionar uma palavra de controle ActiveX permite criar formulários interativos, diálogos personalizados ou elementos de UI simples que se comportam como controles nativos do Word. Seja para construir um modelo de contrato que requer interação do usuário ou um relatório que precisa de um botão “Executar”, as etapas abaixo cobrem tudo o que você precisa.

## Pré‑requisitos

Antes de começar, certifique‑se de que você tem:

* .NET 6.0 SDK ou posterior (o código também funciona com .NET Framework 4.8)
* Visual Studio 2022 (ou qualquer IDE que suporte C#)
* Aspose.Words para .NET instalado (`dotnet add package Aspose.Words`)
* Um entendimento básico de C# e da estrutura de documentos Word

> **Dica profissional:** O método `InsertForms2OleControl` funciona apenas com os controles legados “Forms 2.0”, que são os controles ActiveX que o Word usa para campos de formulário. Se você direcionar versões mais recentes do Office, o controle ainda será renderizado corretamente no cliente desktop.

## Etapa 1: Configurar o projeto e importar namespaces

Crie um novo projeto de console e adicione as declarações `using` necessárias. Isso garante que o compilador encontre as classes `Document`, `DocumentBuilder` e `OleControlType`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

O namespace `Aspose.Words` fornece APIs de alto nível para processamento de Word, enquanto `Aspose.Words.Drawing` contém a enumeração `OleControlType` necessária para especificar o tipo de controle ActiveX.

## Etapa 2: Carregar o documento Word de origem

Você deve começar com um arquivo Word que deseja modificar. O código a seguir carrega `input.docx` a partir de uma pasta que você especificar.

```csharp
// Step 2: Load the Word document you want to modify
string inputPath = @"C:\Docs\input.docx";
Document doc = new Document(inputPath);
```

Se o arquivo não existir, o Aspose.Words lançará uma `FileNotFoundException`. Envolva a chamada em um bloco `try/catch` se precisar de tratamento de erro mais elegante.

## Etapa 3: Criar um DocumentBuilder para editar o documento

`DocumentBuilder` é a ferramenta principal para inserir texto, imagens e controles. Ele mantém um cursor que aponta para a localização onde o próximo elemento será colocado.

```csharp
// Step 3: Create a DocumentBuilder to work with the document's content
DocumentBuilder builder = new DocumentBuilder(doc);
```

Por padrão, o cursor do builder está posicionado no início da primeira seção. Você pode movê‑lo com métodos como `MoveToDocumentEnd()` ou `MoveToParagraph(index)` se quiser o botão em outro lugar.

## Etapa 4: Inserir um controle ActiveX CommandButton

Agora vem o núcleo do tutorial: inserir uma **palavra de controle ActiveX** que aparece como um botão clicável. O método `InsertForms2OleControl` recebe dois argumentos — o tipo de controle e uma legenda (ou nome) para o controle.

```csharp
// Step 4: Insert an ActiveX CommandButton control with the caption "ClickMe"
builder.InsertForms2OleControl(OleControlType.CommandButton, "ClickMe");
```

* **Por que usar `OleControlType.CommandButton`?**  
  Ele indica ao Word que crie um botão clássico Forms 2.0, que exibe uma legenda e pode ser conectado a uma macro ou script VBA posteriormente.

* **O que a legenda faz?**  
  A string `"ClickMe"` torna‑se o texto visível do botão. Você pode alterá‑la para qualquer coisa que se encaixe na sua UI.

### Inserindo o botão em um local específico

Se precisar do botão após um parágrafo específico, mova o builder primeiro:

```csharp
builder.MoveToParagraph(2); // moves to the third paragraph (zero‑based index)
builder.InsertParagraph(); // optional: add a blank line before the button
builder.InsertForms2OleControl(OleControlType.CommandButton, "Submit");
```

## Etapa 5: Salvar o documento modificado

Depois de inserir o controle, persista as alterações em um novo arquivo (ou sobrescreva o original).

```csharp
// Step 5: Save the modified document
string outputPath = @"C:\Docs\output.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Ao abrir `output.docx` na versão desktop do Word, você verá o botão rotulado **ClickMe** (ou **Submit**, dependendo da legenda que você usou). Clicar no botão no modo de design não faz nada por padrão; você pode atribuir uma macro mais tarde via aba “Developer” do Word.

## Exemplo completo e executável

Abaixo está um programa autocontido que demonstra todo o fluxo de trabalho. Copie‑o para `Program.cs` de um novo aplicativo de console e execute‑o.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXControlWordDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Paths – adjust to your environment
            string inputPath = @"C:\Docs\input.docx";
            string outputPath = @"C:\Docs\output.docx";

            // 1️⃣ Load the source document
            Document doc = new Document(inputPath);

            // 2️⃣ Create a builder to edit the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Optional: move to the end of the document
            builder.MoveToDocumentEnd();
            builder.Writeln(); // add a blank line before the button

            // 3️⃣ Insert the ActiveX CommandButton (the core of the activex control word)
            builder.InsertForms2OleControl(OleControlType.CommandButton, "ClickMe");

            // 4️⃣ Save the result
            doc.Save(outputPath);
            Console.WriteLine($"Successfully saved the document with an ActiveX button to: {outputPath}");
        }
    }
}
```

### Saída esperada

* O console imprime a mensagem de sucesso com o caminho de saída.
* Ao abrir `output.docx` aparece um botão **ClickMe** no local onde o builder o inseriu.
* O botão pode ser selecionado, redimensionado ou ter uma macro atribuída via **Developer → Design Mode** do Word.

## Perguntas frequentes e tratamento de casos limites

| Pergunta | Resposta |
|----------|----------|
| **Como inserir um botão ActiveX no cabeçalho/rodapé?** | Mova o builder para o cabeçalho/rodapé com `builder.MoveToHeaderFooter(HeaderFooterType.HeaderPrimary)` antes de chamar `InsertForms2OleControl`. |
| **E se eu precisar de uma caixa de seleção em vez de um botão?** | Use `OleControlType.CheckBox` e forneça uma legenda como `"Agree"`. |
| **O botão funciona no Word Online?** | Não. O Word Online não suporta controles legados Forms 2.0 ActiveX. O botão só é renderizado no cliente desktop. |
| **Posso definir o tamanho do botão programaticamente?** | Após a inserção, recupere o objeto `Shape` via `builder.CurrentParagraph.Runs[0].GetShape()` e ajuste `Width`/`Height`. |
| **Existe uma forma de atribuir uma macro via código?** | O Aspose.Words não expõe edição de macros. Você deve abrir o documento no Word e anexar a macro manualmente ou usar a API Office Interop. |

## Dicas para uso em produção

* **Evite caminhos codificados** – use `Path.Combine` e arquivos de configuração.
* **Dispose do `Document`** – envolva‑o em uma instrução `using` se trabalhar com arquivos grandes para liberar memória rapidamente.
* **Valide a saída** – verifique programaticamente se o documento contém uma forma do tipo `OleControl` iterando `doc.GetChildNodes(NodeType.Shape, true)`.
* **Nota de segurança** – controles ActiveX podem executar código na máquina do cliente. Distribua documentos apenas para usuários confiáveis e considere assinaturas digitais.

## Conclusão

Agora você sabe como adicionar uma **palavra de controle ActiveX** a um documento Word usando C#. Carregando um documento, criando um `DocumentBuilder`, inserindo um botão de comando com `InsertForms2OleControl` e salvando o arquivo, você pode automatizar a criação de formulários Word interativos. Experimente outros valores de `OleControlType`, posicione controles em cabeçalhos ou tabelas e combine‑os com macros para experiências de usuário mais ricas.

---

*Próximos passos*: explore **como inserir controles ActiveX** de outros tipos, aprenda **como adicionar manipuladores de evento ao botão de comando** via VBA e leia sobre as **melhores práticas para inserir botões ActiveX** visando compatibilidade entre plataformas.

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas em seus próprios projetos.

- [Embedding OLE Objects and ActiveX Controls in Word Documents](/words/english/python-net/document-structure-and-content-manipulation/document-ole-objects-active-x/)
- [Add a Combo Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Add a Check Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}