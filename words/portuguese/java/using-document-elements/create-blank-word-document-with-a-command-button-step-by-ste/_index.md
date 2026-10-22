---
category: general
date: 2026-08-04
description: Crie um documento Word em branco e insira um botão de comando usando
  Aspose.Words. Aprenda a definir o tamanho do botão e adicionar um botão clicável
  em C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert command button
- add clickable button
- set button size
- create command button
language: pt
lastmod: 2026-08-04
og_description: Crie um documento Word em branco com Aspose.Words e insira um botão
  de comando. Este guia mostra como definir o tamanho do botão, adicionar um botão
  clicável e salvar o arquivo.
og_image_alt: Screenshot of a Word document containing a clickable command button
  created with C#
og_title: Crie um documento Word em branco e adicione um botão de comando – tutorial
  completo de C#
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Create blank word document and insert command button using Aspose.Words.
    Learn to set button size and add clickable button in C#.
  headline: Create blank word document with a command button – step‑by‑step guide
  type: TechArticle
- description: Create blank word document and insert command button using Aspose.Words.
    Learn to set button size and add clickable button in C#.
  name: Create blank word document with a command button – step‑by‑step guide
  steps:
  - name: The ProgID of the OLE control – `"CommandButton"` for a standard button.
    text: The ProgID of the OLE control – `"CommandButton"` for a standard button.
  - name: A `Rectangle` that defines the **set button size** and position.
    text: A `Rectangle` that defines the **set button size** and position.
  - name: The caption that appears on the button.
    text: The caption that appears on the button.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Criar documento Word em branco com um botão de comando – guia passo a passo
url: /pt/java/using-document-elements/create-blank-word-document-with-a-command-button-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crie um documento Word em branco com um botão de comando – guia passo a passo

Se você precisa **criar um documento Word em branco** que contenha um botão interativo, este tutorial mostra exatamente como fazer isso com Aspose.Words para .NET. Você aprenderá a **inserir botão de comando**, ajustar sua aparência e torná‑lo clicável — tudo em algumas linhas de C#.

O guia cobre tudo, desde a configuração do projeto até a gravação do arquivo final, para que você possa copiar‑colar a solução completa em sua própria aplicação. Ao longo do caminho também explicaremos como **adicionar botão clicável**, **definir o tamanho do botão** e **criar botão de comando** programaticamente.

## Pré‑requisitos

Antes de começar, certifique‑se de que você tem:

* .NET 6.0 SDK ou versão posterior instalada.
* Visual Studio 2022 (ou qualquer IDE que suporte .NET).
* Pacote NuGet Aspose.Words para .NET (`Aspose.Words` versão 23.12 ou mais recente).
* Familiaridade básica com C# e programação orientada a objetos.

Nenhum assembly adicional de interop do Office é necessário porque o Aspose.Words funciona de forma totalmente independente do Microsoft Word.

## Etapa 1: Configurar o projeto .NET

Crie um aplicativo de console que hospedará o código de automação do Word.

```bash
dotnet new console -n WordButtonDemo
cd WordButtonDemo
dotnet add package Aspose.Words
```

Este comando cria uma nova pasta `WordButtonDemo` com um `Program.cs` pronto para execução e adiciona a biblioteca Aspose.Words.

## Etapa 2: Criar documento Word em branco

A primeira operação é **criar um documento Word em branco**. O Aspose.Words fornece a classe `Document` que representa um arquivo Word vazio pronto para uso.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create a new, empty Word document.
Document doc = new Document();
```

Criar um documento em branco fornece uma tela limpa na qual você pode adicionar parágrafos, tabelas ou, neste caso, um botão de comando OLE.

## Etapa 3: Inicializar DocumentBuilder

`DocumentBuilder` é o auxiliar que permite inserir conteúdo no documento. Você precisa vinculá‑lo ao documento que acabou de criar.

```csharp
// Attach a DocumentBuilder to the empty document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

O builder mantém a posição atual do cursor, de modo que qualquer inserção subsequente ocorre exatamente onde você deseja.

## Etapa 4: Inserir botão de comando

Agora **inserimos o botão de comando** (um OLE `Forms2OleControl`) no documento. O método `InsertForms2OleControl` requer três argumentos:

1. O ProgID do controle OLE – `"CommandButton"` para um botão padrão.
2. Um `Rectangle` que define o **definir tamanho do botão** e a posição.
3. A legenda que aparece no botão.

```csharp
// Define the button's position (x, y) and size (width, height).
Rectangle buttonRect = new Rectangle(0, 0, 120, 30); // 120 px wide, 30 px high

// Insert the command button with the desired caption.
Forms2OleControl cmdButton = builder.InsertForms2OleControl(
    "CommandButton",   // ProgID for a CommandButton control
    buttonRect,        // Position and size
    "Click Me");       // Caption displayed on the button
```

Quando o documento é aberto no Word, o botão se comporta como qualquer controle de formulário nativo — você pode clicá‑lo, e o Word disparará a macro associada (se houver). Isso satisfaz o requisito de **adicionar botão clicável**.

### Por que usar Forms2OleControl?

`Forms2OleControl` incorpora um objeto OLE diretamente no arquivo DOCX, preservando as propriedades do controle sem precisar do assembly Interop do Word. É a forma mais confiável de **criar botão de comando** que funciona em diferentes versões do Word.

## Etapa 5: Personalizar o botão (opcional)

Talvez você queira **definir o tamanho do botão** com mais precisão ou alterar propriedades adicionais, como fonte ou cor de fundo. O Aspose.Words expõe o objeto OLE subjacente, permitindo ajustes finos.

```csharp
// Example: change the button's background color (requires OLE automation).
// Note: This step is optional and demonstrates additional customization.
cmdButton.OleFormat.Icon = true; // Show an icon instead of the default appearance.
```

Se precisar de um tamanho diferente, basta ajustar os valores do `Rectangle` na Etapa 4. As coordenadas são medidas em pontos (1 pt = 1/72 polegada), portanto `120` corresponde a aproximadamente 1,67 polegadas de largura.

## Etapa 6: Salvar o documento

Por fim, grave o documento no disco. O arquivo resultante contém um **documento Word em branco** com um botão de comando totalmente funcional.

```csharp
// Save the document as a .docx file.
doc.Save("CommandButtonDemo.docx");
```

Ao abrir `CommandButtonDemo.docx` no Microsoft Word, você verá um botão rotulado “Click Me”. Clicar no botão exibirá a caixa de diálogo de macro padrão, a menos que você anexe uma macro personalizada.

## Código‑fonte completo

Abaixo está o programa completo que você pode copiar para `Program.cs`. Ele inclui todas as etapas descritas acima e compila sem modificações.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordButtonDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Step 2: Create a blank word document.
            Document doc = new Document();

            // Step 3: Initialize DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 4: Define button size and insert command button.
            Rectangle buttonRect = new Rectangle(0, 0, 120, 30);
            Forms2OleControl cmdButton = builder.InsertForms2OleControl(
                "CommandButton",
                buttonRect,
                "Click Me");

            // Optional: further customization (e.g., set icon).
            // cmdButton.OleFormat.Icon = true;

            // Step 6: Save the document.
            doc.Save("CommandButtonDemo.docx");

            System.Console.WriteLine("Document created successfully.");
        }
    }
}
```

### Resultado esperado

Executar o programa gera `CommandButtonDemo.docx`. Ao abrir o arquivo no Word, você verá:

* Uma única página contendo um botão rotulado **Click Me**.
* O botão respeita o **definir tamanho do botão** (120 × 30 pontos).
* Clicar no botão aciona o comportamento padrão de botão de comando do Word, confirmando que a operação de **adicionar botão clicável** foi bem‑sucedida.

## Perguntas frequentes e casos especiais

| Pergunta | Resposta |
|----------|----------|
| **Isso funciona com arquivos .doc?** | Sim. Altere a extensão do arquivo em `doc.Save("file.doc")`. O controle OLE também é armazenado no formato binário legado. |
| **E se eu precisar de vários botões?** | Chame `InsertForms2OleControl` repetidamente, ajustando o `Rectangle` para cada novo botão a fim de evitar sobreposição. |
| **Posso anexar uma macro ao botão?** | O botão em si não contém código de macro. Você deve adicionar uma macro VBA ao documento manualmente ou via a coleção `Modules` do objeto `Document`. |
| **O botão é visível na exportação para PDF?** | Ao exportar o DOCX para PDF usando Aspose.Words, o botão é renderizado como uma imagem estática, não como controle interativo. |
| **Quais versões do Word são suportadas?** | O botão de comando OLE funciona no Word 2007 e posteriores, pois segue a especificação padrão Forms2.0. |

## Conclusão

Agora você sabe como **criar um documento Word em branco**, **inserir botão de comando**, **adicionar botão clicável** e **definir o tamanho do botão** usando Aspose.Words para .NET. O exemplo completo demonstra o fluxo de **criar botão de comando** do início ao fim, proporcionando uma base sólida para tarefas de automação Word mais avançadas.

## Próximos passos

* Explore outros controles OLE (por exemplo, `CheckBox`, `ListBox`) alterando o ProgID em `InsertForms2OleControl`.
* Combine o botão com uma macro VBA para executar ações personalizadas quando o usuário clicar nele.
* Use o `DocumentBuilder` do Aspose.Words para adicionar conteúdo adicional, como tabelas, imagens ou notas de rodapé, antes de inserir o botão.
* Experimente valores de **definir tamanho do botão** para adequar ao layout do seu documento.

Boa codificação e aproveite a criação de documentos Word mais ricos com controles interativos!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que expandem as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}