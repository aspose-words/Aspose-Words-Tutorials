---
category: general
date: 2026-09-21
description: Criar documento Word programaticamente e aprender como salvar o botão
  de documento Word, inserir botão de comando Word e definir a legenda do botão de
  comando usando DocumentBuilder.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- save word document button
- insert command button word
- set command button caption
- how to use documentbuilder
language: pt
lastmod: 2026-09-21
og_description: Crie documentos Word programaticamente com Aspose.Words. Aprenda como
  salvar o documento Word com um botão, inserir um botão de comando, definir a legenda
  do botão de comando e usar o DocumentBuilder para formulários interativos.
og_image_alt: Screenshot of a Word file that contains an inserted CommandButton created
  programmatically
og_title: Criar documento Word programaticamente e adicionar um botão
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create word document programmatically and learn how to save word document
    button, insert command button word, and set command button caption using DocumentBuilder.
  headline: Create word document programmatically and insert a button
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word Automation
title: Criar documento Word programaticamente e inserir um botão
url: /pt/java/using-document-elements/create-word-document-programmatically-and-insert-a-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar documento Word programaticamente e inserir um botão

Se você precisa **criar documento Word programaticamente**, Aspose.Words fornece uma API fluente que permite adicionar controles interativos, como um CommandButton. Este tutorial também explica **como usar DocumentBuilder**, como **salvar documento Word com botão**, e como **definir a legenda do botão de comando** para que o botão apareça exatamente como esperado dentro do arquivo .docx.

Você aprenderá a:

* Inicializar um documento em branco com `Document`.
* Trabalhar com `DocumentBuilder` para editar o documento.
* Inserir um **CommandButton** (`insert command button word`).
* Definir o nome do botão e a legenda visível (`set command button caption`).
* Persistir o resultado em disco (`save word document button`).

Os passos são escritos para desenvolvedores .NET usando C# e a versão mais recente do Aspose.Words para .NET (v24.10). Nenhum pacote NuGet adicional é necessário além do Aspose.Words.

---

## O que você precisa antes de começar

| Pré-requisito | Motivo |
|--------------|--------|
| Visual Studio 2022 (ou qualquer IDE C#) | Para compilar e executar o código de exemplo. |
| .NET 6.0 SDK ou posterior | Fornece o runtime para o exemplo. |
| Aspose.Words for .NET (v24.10 ou mais recente) | A biblioteca que permite **criar documento Word programaticamente** e manipular controles de formulário. |
| Familiaridade básica com C# e conceitos de OOP | Necessário para entender o fluxo do código. |

Você pode instalar Aspose.Words via NuGet:

```bash
dotnet add package Aspose.Words
```

---

## Criar documento Word programaticamente

O primeiro passo é instanciar um `Document` vazio. Este objeto representa todo o arquivo Word na memória.

```csharp
// Step 1: Create a new blank document
Document doc = new Document();
```

Criar o documento programaticamente fornece uma tela limpa na qual você pode adicionar parágrafos, tabelas ou controles interativos.  

---

## Como usar DocumentBuilder

`DocumentBuilder` é a classe principal para editar um `Document`. Ela fornece métodos para inserir texto, imagens e campos de formulário. Neste tutorial a utilizamos para posicionar um CommandButton.

```csharp
// Step 2: Initialize a DocumentBuilder to edit the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

O builder mantém um cursor interno que aponta para a localização atual de inserção. Por padrão ele começa no início da primeira seção, o que é ideal para nosso exemplo.

---

## Inserir botão de comando no Word

Aspose.Words trata um CommandButton como um controle ActiveX. O método `InsertForms2OleControl` cria um controle OLE genérico que então configuramos como um botão.

```csharp
// Step 3: Insert an ActiveX Forms2OleControl (a CommandButton)
Forms2OleControl commandButton = builder.InsertForms2OleControl();
```

Neste ponto o controle existe no documento, mas não tem representação visual até definirmos seu tipo.

---

## Definir legenda do botão de comando

Agora informamos ao controle OLE que ele deve se comportar como um CommandButton e atribuímos a ele um rótulo amigável.

```csharp
// Step 4: Define the control as a CommandButton
commandButton.SetControlType(Forms2OleControlType.COMMANDBUTTON);

// Step 5: Set a unique name for the button (used for identification)
commandButton.SetName("btnSubmit");

// Step 6: Set the visible caption that appears on the button
commandButton.SetCaption("Submit");
```

Definir a **legenda do botão de comando** é essencial porque o Word exibe esse texto na superfície do botão. Se você omitir `SetCaption`, o botão aparecerá com um rótulo genérico.

---

## Salvar documento Word com botão

Por fim, persista o documento em disco. O método `Save` grava todo o pacote Word, incluindo o botão recém‑inserido, em um arquivo .docx.

```csharp
// Step 7: Save the document containing the CommandButton
doc.Save("YOUR_DIRECTORY/CommandButton.docx");
```

O arquivo `CommandButton.docx` agora contém um botão totalmente funcional rotulado **Submit**. Quando o usuário abre o arquivo no Microsoft Word e clica no botão, a ação padrão (que você pode vincular posteriormente via VBA) será disparada.

---

## Exemplo completo em funcionamento

Abaixo está o programa completo que você pode copiar, colar e executar. Ele demonstra todo o fluxo, desde a criação do documento até a gravação do botão.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Initialize DocumentBuilder (how to use DocumentBuilder)
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a CommandButton (insert command button word)
        Forms2OleControl commandButton = builder.InsertForms2OleControl();

        // 4. Define the control type as CommandButton
        commandButton.SetControlType(Forms2OleControlType.COMMANDBUTTON);

        // 5. Give the button a unique name (optional but useful)
        commandButton.SetName("btnSubmit");

        // 6. Set the visible caption (set command button caption)
        commandButton.SetCaption("Submit");

        // 7. Save the document (save word document button)
        string outputPath = @"C:\Temp\CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Resultado esperado**

* Um arquivo chamado `CommandButton.docx` localizado no caminho que você especificou.
* Ao abrir o arquivo no Microsoft Word, um único botão **Submit** aparece na primeira página.
* O botão pode ser selecionado, redimensionado ou vinculado a uma macro na aba **Developer** do Word.

---

## Perguntas comuns e tratamento de casos extremos

| Pergunta | Resposta |
|----------|----------|
| *E se eu precisar de mais de um botão?* | Repita os passos 3–6 com nomes e legendas diferentes. Cada botão deve ter um valor `SetName` exclusivo. |
| *Posso definir o tamanho do botão?* | Sim. Após inserir o controle, você pode modificar as propriedades `Width` e `Height` via o objeto `OleFormat`. |
| *O botão funcionará em todas as versões do Word?* | Controles ActiveX são suportados na versão desktop do Word (Windows). Eles não são renderizados no Word Online ou no macOS. |
| *Como adicionar um manipulador de clique?* | Você precisa escrever código VBA que faça referência ao nome do botão (`btnSubmit`). A macro VBA pode ser incorporada usando `doc.VbaProject`. |
| *E se eu precisar inserir o botão dentro de uma célula de tabela?* | Mova o cursor do builder para a célula desejada (`builder.MoveTo(cell.FirstParagraph)`) antes de chamar `InsertForms2OleControl`. |

---

## Dicas profissionais

* **Dica Pro:** Sempre defina um nome significativo com `SetName`. Isso simplifica a automação VBA e facilita a depuração.
* **Cuidado com:** Esquecer de chamar `SetControlType`. Sem essa chamada o objeto OLE aparece como um placeholder genérico em vez de um botão clicável.
* **Dica de desempenho:** Se você estiver gerando muitos documentos em um loop, reutilize uma única instância de `DocumentBuilder` e chame `builder.MoveToDocumentEnd()` antes de cada inserção para evitar redefinições desnecessárias do cursor.

---

## Próximos passos

Agora que você sabe como **criar documento Word programaticamente**, **inserir botão de comando no Word**, **definir a legenda do botão de comando** e **salvar documento Word com botão**, pode explorar cenários mais avançados:

* Adicionar controles **TextFormField** para entrada do usuário.
* Combinar botões com campos **MacroButton** para executar VBA diretamente.
* Usar **DocumentBuilder.InsertImage** para colocar ícones nos seus botões.
* Integrar com ASP.NET para gerar formulários Word em

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Create New Word Document](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}