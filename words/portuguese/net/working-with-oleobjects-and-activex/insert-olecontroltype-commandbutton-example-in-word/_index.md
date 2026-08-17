---
category: general
date: 2026-08-17
description: Inserir exemplo OleControlType.CommandButton no Word usando Aspose.Words.
  Aprenda como adicionar controles de formulário a um documento Word programaticamente.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert olecontroltype.commandbutton example
- how to add form controls to word document
- Aspose.Words ActiveX button
- C# Word automation
- programmatic form controls
language: pt
lastmod: 2026-08-17
og_description: Inserir exemplo OleControlType.CommandButton no Word com Aspose.Words.
  Siga este guia para adicionar controles de formulário a um documento Word.
og_image_alt: Screenshot showing an ActiveX CommandButton inserted into a Word document
  using Aspose.Words
og_title: Inserir exemplo de OleControlType.CommandButton no Word
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: Insert OleControlType.CommandButton example in Word using Aspose.Words.
    Learn how to add form controls to a Word document programmatically.
  headline: Insert OleControlType.CommandButton example in Word
  type: TechArticle
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Inserir exemplo de OleControlType.CommandButton no Word
url: /pt/net/working-with-oleobjects-and-activex/insert-olecontroltype-commandbutton-example-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Inserir exemplo OleControlType.CommandButton no Word

Se você precisa **inserir OleControlType.CommandButton example** em um arquivo Word, este guia mostra como fazer. Você aprenderá **como adicionar controles de formulário a um documento Word** usando Aspose.Words, com um programa C# completo e executável.

Controles de formulário, como botões ActiveX, permitem criar modelos Word interativos — úteis para contratos, questionários ou ferramentas internas. As etapas abaixo cobrem tudo, desde a configuração do projeto até a verificação de que o botão aparece corretamente no arquivo `.docx` salvo.

## Pré‑requisitos

Antes de começar, certifique‑se de que você tem:

- .NET 6.0 SDK ou versão posterior instalada  
- Visual Studio 2022 (ou qualquer IDE C#)  
- Uma licença do Aspose.Words para .NET ou uma licença temporária gratuita  
- Familiaridade básica com C# e conceitos de arquivos Word  

> **Dica profissional:** Se estiver usando a versão de avaliação gratuita, coloque o arquivo de licença na mesma pasta do executável e carregue‑o no início do `Main`.

## Etapa 1: Criar um novo projeto de console e adicionar Aspose.Words

Abra um terminal e execute:

```bash
dotnet new console -n OleCommandButtonDemo
cd OleCommandButtonDemo
dotnet add package Aspose.Words
```

Isso cria um projeto limpo e baixa o pacote mais recente do Aspose.Words, que fornece as APIs `Document`, `DocumentBuilder` e `InsertForms2OleControl` necessárias para o **insert OleControlType.CommandButton example**.

## Etapa 2: Escrever o programa completo

Crie ou substitua o arquivo `Program.cs` com o código a seguir. Ele contém todas as diretivas `using` necessárias, o carregamento da licença e o fluxo de trabalho de quatro etapas mostrado no trecho original.

```csharp
using System;
using System.Drawing;               // For Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;          // For OleControlType

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // Optional: load a trial or commercial license.
        // -------------------------------------------------
        // var license = new Aspose.Words.License();
        // license.SetLicense("Aspose.Words.lic");

        // -------------------------------------------------
        // Step 1: Create a new blank document
        // -------------------------------------------------
        Document doc = new Document();

        // -------------------------------------------------
        // Step 2: Initialize a DocumentBuilder to work with the document
        // -------------------------------------------------
        DocumentBuilder builder = new DocumentBuilder(doc);

        // -------------------------------------------------
        // Step 3: Insert an ActiveX CommandButton control
        // -------------------------------------------------
        // OleControlType.CommandButton creates a CommandButton.
        // "ClickMe" is the control's name.
        // The Rectangle defines the button's position (x, y) and size (width, height).
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            "ClickMe",
            new Rectangle(100, 100, 80, 30));

        // -------------------------------------------------
        // Step 4: Save the document containing the ActiveX button
        // -------------------------------------------------
        string outputPath = "ActiveXButton.docx";
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### Por que cada linha importa

* **Carregamento da licença** – garante que você não fique limitado pelas restrições da avaliação.  
* **`Document doc = new Document();`** – cria o contêiner para todo o conteúdo Word; esta é a base do **insert OleControlType.CommandButton example**.  
* **`DocumentBuilder builder = new DocumentBuilder(doc);`** – fornece uma API fluente para adicionar texto, imagens e controles.  
* **`InsertForms2OleControl`** – o método principal que implementa **how to add form controls to a Word document**. O valor enum `OleControlType.CommandButton` indica ao Aspose.Words que deve criar um botão ActiveX.  
* **`new Rectangle(100, 100, 80, 30)`** – posiciona o botão a 100 pts da margem esquerda e superior, com largura de 80 pts e altura de 30 pts. Ajuste esses números conforme o layout desejado.  
* **`doc.Save`** – grava o arquivo .docx no **disco**; o arquivo agora contém o botão incorporado.

## Etapa 3: Compilar e executar o programa

Na pasta do projeto, execute:

```bash
dotnet run
```

Você deverá ver a mensagem no console:

```
Document saved to ActiveXButton.docx
```

Abra `ActiveXButton.docx` no Microsoft Word. Você verá um botão rotulado **ClickMe** posicionado aproximadamente no centro da página. Clicar no botão aciona o comportamento padrão do ActiveX (geralmente sem ação, a menos que você associe uma macro).

![exemplo de insert olecontroltype.commandbutton](/images/activex-button.png "CommandButton ActiveX inserido em um documento Word")

*Texto alternativo da imagem:* exemplo de insert olecontroltype.commandbutton – um CommandButton ActiveX exibido em um documento Word.

## Etapa 4: Personalizando o botão (opcional)

O exemplo básico **insert OleControlType.CommandButton example** cria um botão padrão. Você pode modificar sua legenda, fonte ou até mesmo anexar uma macro editando o objeto OLE subjacente. Abaixo está uma forma concisa de alterar a legenda do botão após a inserção:

```csharp
// Retrieve the first shape (our button) from the document
Shape buttonShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

// Access the OLE format and set the caption
buttonShape.OleFormat.GetControl().SetProperty("Caption", "Submit");
```

> **Observação:** A manipulação direta das propriedades OLE requer compreensão da interface COM subjacente. Na maioria dos cenários, a legenda padrão é suficiente.

## Etapa 5: Armadilhas comuns e como evitá‑las

| Problema | Por que acontece | Solução |
|----------|------------------|---------|
| O botão não aparece no Word | O documento foi salvo como `.docx` mas aberto em um visualizador que remove controles OLE (ex.: Google Docs). | Abra o arquivo no Microsoft Word ou no Word Online com permissões de edição. |
| Erro de tempo de execução `ArgumentOutOfRangeException` | As coordenadas do `Rectangle` estão fora das margens da página. | Use valores dentro do tamanho da página (ex.: 0‑500 para A4). |
| Exceção de licença | Uma licença de avaliação expira após 30 dias. | Carregue um arquivo de licença válido ou solicite uma avaliação estendida à Aspose. |

## Etapa 6: Como esse exemplo se encaixa em projetos de automação maiores

Quando precisar **how to add form controls to Word document** em escala — como gerar centenas de modelos de contrato — encapsule a lógica de inserção em um método reutilizável:

```csharp
static void AddCommandButton(DocumentBuilder builder, string name, Rectangle bounds)
{
    builder.InsertForms2OleControl(OleControlType.CommandButton, name, bounds);
}
```

Assim, você pode chamar `AddCommandButton` dentro de loops que processam linhas de dados, garantindo que cada documento gerado contenha um botão com nome exclusivo (ex.: `Approve_001`, `Approve_002`).

## Conclusão

Agora você tem um **insert OleControlType.CommandButton example** completo que demonstra **how to add form controls to a Word document** usando Aspose.Words para .NET. O tutorial abordou a configuração do projeto, código‑fonte completo, dicas de personalização e passos de solução de problemas comuns.

A partir daqui, você pode explorar:

- Adicionar outros tipos de controle, como **CheckBox** ou **ComboBox** (`OleControlType.CheckBox`, `OleControlType.ComboBox`).  
- Vincular o botão a uma macro VBA para maior interatividade.  
- Gerar PDFs a partir do mesmo documento preservando os campos de formulário.

Experimente diferentes tamanhos, posições e nomes de controle para atender ao seu caso de uso específico. Boa codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas em seus próprios projetos.

- [Insert Combo Box Form Field In Word Document](/words/english/net/add-content-using-documentbuilder/insert-combo-box-form-field/)
- [Insert Check Box Form Field In Word Document](/words/english/net/add-content-using-documentbuilder/insert-check-box-form-field/)
- [Insert Text Input Form Field In Word Document](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}