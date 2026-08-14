---
category: general
date: 2026-08-14
description: Como adicionar um botão ActiveX em um documento Word usando Aspose.Words
  – aprenda a criar um documento Word vazio e inserir um botão ActiveX programaticamente.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex
- insert activex button
- create empty word document
- create word document aspose
language: pt
lastmod: 2026-08-14
og_description: Como adicionar um botão ActiveX em um documento Word com Aspose.Words.
  Este tutorial mostra como criar um documento Word vazio, inserir um botão ActiveX
  e salvar o resultado.
og_image_alt: Screenshot of an ActiveX button inserted into a Word document using
  Aspose.Words
og_title: Como adicionar um botão ActiveX no Word – Guia Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to add ActiveX button in a Word document using Aspose.Words – learn
    to create an empty Word document and insert an ActiveX button programmatically.
  headline: How to add ActiveX button in a Word document with Aspose.Words
  type: TechArticle
- description: How to add ActiveX button in a Word document using Aspose.Words – learn
    to create an empty Word document and insert an ActiveX button programmatically.
  name: How to add ActiveX button in a Word document with Aspose.Words
  steps:
  - name: Does the button work in all Word versions?
    text: ActiveX controls are supported in the desktop version of Word on Windows.
      They are not rendered in Word Online, Word for macOS, or mobile clients. If
      you need cross‑platform interactivity, consider using content controls or HTML‑based
      solutions instead.
  - name: What if I need a different size or position?
    text: '`InsertForms2OleControl` places the control at the current builder cursor.
      To move it, adjust the cursor with `builder.MoveTo` before insertion, or modify
      the control’s `Left` and `Top` properties after creation:'
  - name: Can I add other ActiveX types?
    text: Yes. The `Forms2OleControlType` enumeration includes `CheckBox`, `OptionButton`,
      `ListBox`, and more. Replace `CommandButton` with the desired enum value and
      adjust properties accordingly.
  - name: Is a macro required for the button to do something?
    text: The button itself does nothing until you attach VBA code. In Word, press
      **Alt+F11** to open the VBA editor, locate `btnSubmit_Click`, and write the
      desired logic. The generated document will retain the VBA project if you enable
      the **SaveFormat.Doc** (legacy `.doc`) format, but `.docx` files cannot
  type: HowTo
tags:
- Aspose.Words
- ActiveX
- Word automation
- C#
title: Como adicionar um botão ActiveX em um documento Word com Aspose.Words
url: /pt/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como adicionar um botão ActiveX em um documento Word com Aspose.Words

Se você precisa **como adicionar ActiveX** controls a um arquivo Word gerado, este guia mostra os passos exatos. Você aprenderá a **inserir botão ActiveX** programaticamente, começando a partir de um **criar documento Word vazio** e terminando com um arquivo salvo que pode ser aberto no Microsoft Word.

Adicionar um botão que executa código VBA ou dispara uma macro é um requisito comum para geradores automáticos de relatórios, modelos de formulários ou contratos interativos. Usar Aspose.Words para .NET permite que você construa o documento sem iniciar o Office, mantendo o processo rápido e adequado para servidores.

## Pré-requisitos

Antes de começar, certifique‑se de que você tem:

* .NET 6.0 (ou posterior) SDK instalado.  
* Visual Studio 2022 ou qualquer IDE compatível com C#.  
* Pacote NuGet Aspose.Words for .NET (`Aspose.Words` versão 24.9 ou mais recente).  
  Instale-o com:
  ```bash
  dotnet add package Aspose.Words
  ```
* Um ambiente Windows se você planeja testar o botão ActiveX, pois controles ActiveX requerem a versão Windows do Microsoft Word.

## Etapa 1: Criar um documento Word vazio

A primeira tarefa é **criar documento Word vazio** na memória. Aspose.Words fornece a classe `Document` para esse propósito.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new, blank Word document.
Document doc = new Document();
```

`Document` representa todo o arquivo .docx. Neste ponto o documento não contém páginas, mas você pode começar a adicionar conteúdo imediatamente.

## Etapa 2: Inicializar um DocumentBuilder

`DocumentBuilder` é um auxiliar que permite inserir texto, imagens e outros objetos no documento. Ele funciona na instância `Document` que você acabou de criar.

```csharp
// Initialise the builder with the blank document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

O builder mantém uma posição de cursor; tudo o que você inserir após esta linha aparecerá no início da primeira página.

## Etapa 3: Inserir um controle ActiveX CommandButton

Aspose.Words expõe o método `InsertForms2OleControl` para adicionar controles de formulário legados, incluindo ActiveX. O método requer o tipo de controle e seu tamanho em pontos.

```csharp
// Insert an ActiveX CommandButton (150x30 points).
Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton, 150, 30);
```

O objeto `Forms2OleControl` retornado permite que você configure propriedades como o nome e a legenda do controle.

## Etapa 4: Configurar as propriedades do botão

Definir um `Name` significativo permite que você faça referência ao controle a partir do código VBA posteriormente. O `Caption` é o texto que o usuário vê no botão.

```csharp
// Set the button’s programmatic name (used in VBA) and displayed caption.
cmdBtn.Name = "btnSubmit";
cmdBtn.Caption = "Submit";
```

> **Dica profissional:** Mantenha o nome curto e alfanumérico; o Word rejeitará nomes que contenham espaços ou caracteres especiais.

## Etapa 5: Salvar o documento

Finalmente, grave o documento no disco. Use a extensão `.docx` para arquivos Word modernos; o botão ActiveX funciona da mesma forma em arquivos `.doc`, mas `.docx` é o formato preferido para novos projetos.

```csharp
// Save the document containing the ActiveX button.
doc.Save(@"C:\Temp\ActiveXButton.docx");
```

Ao abrir `ActiveXButton.docx` no Microsoft Word, você verá um botão **Submit** clicável. Se você habilitar macros, pode anexar código VBA a `btnSubmit_Click` e fazê‑lo executar quando o usuário clicar no botão.

## Exemplo completo e executável

Juntando todas as peças, você obtém um programa autocontido que pode copiar, colar e executar.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create an empty Word document.
            Document doc = new Document();

            // Step 2: Initialise DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Insert an ActiveX CommandButton control.
            Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, 150, 30);

            // Step 4: Set button properties.
            cmdBtn.Name = "btnSubmit";
            cmdBtn.Caption = "Submit";

            // Step 5: Save the document.
            string outputPath = @"C:\Temp\ActiveXButton.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Saída esperada** – Após executar o programa, o console imprime o local de salvamento, e ao abrir o arquivo gerado no Word aparece um botão rotulado **Submit** posicionado no topo da primeira página.

## Lidando com perguntas comuns e casos extremos

### O botão funciona em todas as versões do Word?

Controles ActiveX são suportados na versão desktop do Word no Windows. Eles não são renderizados no Word Online, Word para macOS ou clientes móveis. Se precisar de interatividade multiplataforma, considere usar controles de conteúdo ou soluções baseadas em HTML.

### E se eu precisar de um tamanho ou posição diferentes?

`InsertForms2OleControl` coloca o controle no cursor atual do builder. Para movê‑lo, ajuste o cursor com `builder.MoveTo` antes da inserção, ou modifique as propriedades `Left` e `Top` do controle após a criação:

```csharp
cmdBtn.Left = 100;   // points from the left margin
cmdBtn.Top = 200;    // points from the top margin
```

### Posso adicionar outros tipos de ActiveX?

Sim. A enumeração `Forms2OleControlType` inclui `CheckBox`, `OptionButton`, `ListBox` e mais. Substitua `CommandButton` pelo valor enum desejado e ajuste as propriedades conforme necessário.

### É necessário uma macro para que o botão faça algo?

O próprio botão não faz nada até que você anexe código VBA. No Word, pressione **Alt+F11** para abrir o editor VBA, localize `btnSubmit_Click` e escreva a lógica desejada. O documento gerado manterá o projeto VBA se você usar o formato **SaveFormat.Doc** (legado `.doc`), mas arquivos `.docx` não podem armazenar macros VBA. Use o formato `.doc` se precisar de VBA incorporado.

## Conclusão

Agora você sabe **como adicionar ActiveX** controls a um arquivo Word usando Aspose.Words. Seguindo os passos para **criar documento Word vazio**, inicializar um `DocumentBuilder`, **inserir botão ActiveX**, configurar suas propriedades e salvar o arquivo, você pode gerar modelos Word interativos diretamente do seu código .NET.

Em seguida, explore tópicos relacionados como manipulação de eventos do **insert ActiveX button**, adicionando **create word document aspose** para tabelas ou imagens, e protegendo documentos habilitados para macro para implantação corporativa. Experimente diferentes tipos de controle e opções de layout para adaptar a experiência do usuário às necessidades da sua aplicação.

Feliz codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Criar documento Word com cabeçalho e rodapé usando Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Criar forma de grupo em documento Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Criar um documento Word com tabela usando Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}