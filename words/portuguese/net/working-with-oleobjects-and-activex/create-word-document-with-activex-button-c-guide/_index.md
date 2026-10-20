---
category: general
date: 2026-07-19
description: Crie um documento Word usando Aspose.Words C# e aprenda como adicionar
  um botão de comando ActiveX, definir o tamanho do botão e inserir o botão programaticamente.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- how to add activex
- insert command button
- set button size
- how to insert button
language: pt
lastmod: 2026-07-19
og_description: Crie um documento Word com Aspose.Words C# e incorpore um botão de
  comando ActiveX em segundos. Siga o guia passo a passo para definir o tamanho do
  botão e inseri‑lo facilmente.
og_image_alt: Screenshot of a Word document showing an ActiveX command button inserted
  via C#
og_title: Criar documento Word com botão ActiveX – Tutorial C#
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Create Word Document using Aspose.Words C# and learn how to add ActiveX
    command button, set button size, and insert button programmatically.
  headline: Create Word Document with ActiveX Button – C# Guide
  type: TechArticle
- description: Create Word Document using Aspose.Words C# and learn how to add ActiveX
    command button, set button size, and insert button programmatically.
  name: Create Word Document with ActiveX Button – C# Guide
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code also works on .NET Framework 4.7+). - A valid
      Aspose.Words for .NET license (or a free evaluation key). - Visual Studio 2022
      (or any IDE you like). - Basic familiarity with C# and object‑oriented programming.'
  - name: Platform Limitations
    text: '- ActiveX controls only run on the Windows version of Word. If your audience
      includes macOS or Word Online users, the button will appear as a static image.
      - Some corporate environments disable ActiveX for security; you may need to
      sign the document or inform users to enable content.'
  - name: VBA Interaction (Optional)
    text: If you want the button to execute a macro, you’ll have to add a VBA project
      to the document after saving. Aspose.Words does not generate VBA code automatically,
      but you can use the `Document.VbaProject` API to inject it.
  - name: Naming Collisions
    text: Always give each control a unique `Name`. Re‑using the same name can cause
      runtime errors when Word tries to resolve the control.
  - name: Performance Tip
    text: When inserting many controls, reuse a single `DocumentBuilder` instance
      and avoid calling `doc.Save` inside a loop. Batch the inserts and save once
      at the end.
  - name: What’s Next?
    text: '- **Style the button** – change fonts, colors, or add an image background.
      - **Attach VBA macros** – make the button perform calculations or launch external
      programs. - **Combine with other controls** – checkboxes, list boxes, or even
      embedded Excel sheets.'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Criar Documento Word com Botão ActiveX – Guia C#
url: /pt/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crie Documento Word com Botão ActiveX – Guia Completo em C#

Já se perguntou como **criar documento word** que contenha um botão ActiveX funcional? Talvez você esteja automatizando um relatório e precise de um controle “Aprovar” clicável dentro do arquivo. Neste tutorial vamos percorrer exatamente isso—usando Aspose.Words para .NET para adicionar um botão de comando ActiveX, definir seu tamanho e inseri‑lo onde for necessário.  

Se você já se perguntou *como adicionar activex* sem abrir o Word manualmente, está no lugar certo. Ao final você terá um exemplo executável, uma explicação clara de cada passo e dicas para lidar com armadilhas comuns.

## O que você vai aprender

- Como configurar Aspose.Words em um projeto C#  
- O código exato para **criar documento word** e incorporar um botão de comando ActiveX  
- Formas de **definir tamanho do botão** e personalizar sua legenda e nome  
- O método correto para **inserir botão de comando** e **como inserir botão** em qualquer local do documento  
- Considerações de casos extremos (versão do Word, limites de plataforma, avisos de segurança)

### Pré‑requisitos

- .NET 6.0 ou superior (o código também funciona em .NET Framework 4.7+).  
- Uma licença válida do Aspose.Words para .NET (ou uma chave de avaliação gratuita).  
- Visual Studio 2022 (ou qualquer IDE de sua preferência).  
- Familiaridade básica com C# e programação orientada a objetos.

Nenhuma outra biblioteca de terceiros é necessária.

---

## Etapa 1: Criar Documento Word – Configuração do Projeto

Antes de podermos **inserir botão de comando**, precisamos de um arquivo Word em branco para trabalhar. Esta etapa também mostra o padrão clássico de “criar documento word” usando Aspose.Words.

```csharp
// Add the Aspose.Words NuGet package first:
//   dotnet add package Aspose.Words
using Aspose.Words;
using Aspose.Words.Drawing.Ole;

// 1️⃣  Initialize a new blank document.
Document doc = new Document();

// 1️⃣  Create a DocumentBuilder – it lets us place content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Por que isso importa:** `Document` representa todo o arquivo .docx, enquanto `DocumentBuilder` acompanha a posição atual do cursor. Todas as inserções subsequentes (incluindo nosso controle ActiveX) ocorrem em relação a esse builder.

---

## Etapa 2: Como Adicionar ActiveX – Construindo o Controle CommandButton

Agora que o documento existe, vamos abordar a parte **como adicionar activex**. Aspose.Words expõe a classe `Forms2OleControl` para objetos ActiveX. Aqui criaremos um botão de comando e configuraremos suas propriedades, incluindo a exigência de **definir tamanho do botão**.

```csharp
// 2️⃣  Create the ActiveX command button.
Forms2OleControl commandButton = new Forms2OleControl(
    doc,                     // Parent document
    Forms2OleControlType.CommandButton); // Control type

// Configure appearance – this is where we **set button size**.
commandButton.Width = 120;          // Width in points (≈1.67 inches)
commandButton.Height = 30;          // Height in points (≈0.42 inches)

// Set the text the user sees.
commandButton.Caption = "Click Me";

// Give the control a unique name for later reference.
commandButton.Name = "cmdButton1";
```

> **Dica de especialista:** O tamanho é medido em pontos (1 ponto = 1/72 polegada). Ajuste os valores para se adequar ao seu layout; para um botão típico de barra de ferramentas, 120 × 30 funciona bem.

---

## Etapa 3: Inserir Botão de Comando – O Núcleo de **Inserir Botão de Comando**

Com o controle pronto, agora **inserimos botão de comando** no documento na posição atual do builder. Você pode mover o builder para qualquer lugar (por exemplo, após um parágrafo) antes de chamar este método.

```csharp
// 3️⃣  Insert the prepared ActiveX control into the document.
builder.InsertForms2OleControl(commandButton);
```

Se precisar **como inserir botão** em um marcador específico, basta mover o builder primeiro:

```csharp
builder.MoveToBookmark("MyPlace"); // Ensure a bookmark named 'MyPlace' exists
builder.InsertForms2OleControl(commandButton);
```

> **O que acontece nos bastidores?** Aspose.Words grava os fluxos de objetos OLE necessários no pacote .docx, de modo que o Word pode renderizar o botão sem macros adicionais.

---

## Etapa 4: Salvar o Documento – Finalizando o ciclo de **Criar Documento Word**

A etapa final é simples: persistir o arquivo no disco. Isso completa o ciclo de **criar documento word**, incorporar o ActiveX e salvar.

```csharp
// 4️⃣  Save the document where you want it.
string outputPath = @"C:\Temp\CommandButton.docx";
doc.Save(outputPath);
```

Abra o arquivo resultante no Microsoft Word (somente Windows). Você deverá ver um botão clicável rotulado “Click Me”. Clicar nele acionará a Ação padrão de um CommandButton—nada acontece a menos que você anexe código VBA, mas o controle está totalmente funcional.

> **Saída esperada:** Um arquivo .docx com uma única página, um botão centralizado no ponto de inserção, tamanho 120 × 30 pt, legenda “Click Me”.  
> ![Botão ActiveX inserido em um documento Word](placeholder-image.png)  
> *Texto alternativo da imagem:* **Botão ActiveX inserido em um documento Word usando C#** (matches `og_image_alt`).

---

## Etapa 5: Casos Extremos, Segurança e Boas Práticas

### Limitações de Plataforma
- Controles ActiveX só funcionam na versão Windows do Word. Se seu público inclui usuários macOS ou Word Online, o botão aparecerá como uma imagem estática.
- Alguns ambientes corporativos desativam ActiveX por segurança; pode ser necessário assinar o documento ou instruir os usuários a habilitar o conteúdo.

### Interação com VBA (Opcional)
Se quiser que o botão execute uma macro, será necessário adicionar um projeto VBA ao documento após a gravação. Aspose.Words não gera código VBA automaticamente, mas você pode usar a API `Document.VbaProject` para injetá‑lo.

### Colisões de Nomes
Sempre dê a cada controle um `Name` exclusivo. Reutilizar o mesmo nome pode causar erros em tempo de execução quando o Word tenta resolver o controle.

### Dica de Performance
Ao inserir muitos controles, reutilize uma única instância de `DocumentBuilder` e evite chamar `doc.Save` dentro de um loop. Agrupe as inserções e salve uma única vez ao final.

---

## Exemplo Completo Funcional

Juntando tudo, aqui está um programa completo, pronto para copiar e colar:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Create and configure the ActiveX command button.
        Forms2OleControl commandButton = new Forms2OleControl(
            doc, Forms2OleControlType.CommandButton);
        commandButton.Width = 120;          // Set button size – width
        commandButton.Height = 30;          // Set button size – height
        commandButton.Caption = "Click Me";
        commandButton.Name = "cmdButton1";

        // Insert the button at the current cursor position.
        builder.InsertForms2OleControl(commandButton);

        // Save the document.
        string outputPath = @"C:\Temp\CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Execute o programa, abra o arquivo salvo e você verá o botão exatamente onde o builder estava posicionado.

---

## Conclusão

Acabamos de **criar documento word** do zero, aprendemos **como adicionar activex** configurando um `Forms2OleControl`, dominamos as propriedades de **definir tamanho do botão**, e demonstramos a forma correta de **inserir botão de comando** e **como inserir botão** em qualquer ponto do arquivo.  

A partir de um único exemplo de código, você agora tem uma base sólida para automação Word mais avançada—seja criando modelos com formulários interativos, gerando contratos que exigem reconhecimento do usuário, ou simplesmente espalhando alguns controles úteis ao longo de um relatório.

### O que vem a seguir?

- **Estilizar o botão** – alterar fontes, cores ou adicionar uma imagem de fundo.  
- **Anexar macros VBA** – fazer o botão executar cálculos ou lançar programas externos.  
- **Combinar com outros controles** – caixas de seleção, listas suspensas ou até planilhas Excel incorporadas.  

Sinta‑se à vontade para experimentar e, se encontrar algum obstáculo, deixe um comentário abaixo. Boa codificação e aproveite a automação do Word com Aspose.Words!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que expandem as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas em seus próprios projetos.

- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}