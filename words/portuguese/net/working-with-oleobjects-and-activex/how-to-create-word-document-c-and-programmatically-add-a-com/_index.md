---
category: general
date: 2026-09-11
description: Aprenda como criar um documento Word em C# e adicionar programaticamente
  um botão de comando usando Aspose.Words em alguns passos simples.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- programmatically add command button
language: pt
lastmod: 2026-09-11
og_description: Crie um documento Word em C# e adicione programaticamente um botão
  de comando com Aspose.Words. Siga este guia completo para obter uma solução funcional.
og_image_alt: Screenshot of a Word document containing a Submit command button created
  with C#
og_title: Criar documento Word em C# – adicionar um botão de comando programaticamente
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create word document c# and programmatically add a command
    button using Aspose.Words in a few simple steps.
  headline: How to create word document c# and programmatically add a command button
  type: TechArticle
- description: Learn how to create word document c# and programmatically add a command
    button using Aspose.Words in a few simple steps.
  name: How to create word document c# and programmatically add a command button
  steps:
  - name: Launch Word and open `CommandButton.docx`.
    text: Launch Word and open `CommandButton.docx`.
  - name: You should see a button labeled **Submit** in the document body.
    text: You should see a button labeled **Submit** in the document body.
  - name: Hovering over the button reveals the name `btnSubmit` in the **Properties**
      pane (Developer tab → Properties).
    text: Hovering over the button reveals the name `btnSubmit` in the **Properties**
      pane (Developer tab → Properties).
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- ActiveX
title: Como criar um documento Word em C# e adicionar programaticamente um botão de
  comando
url: /pt/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-and-programmatically-add-a-com/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como criar documento Word c# e adicionar programaticamente um botão de comando

Se você precisa **criar documento word c#** e incorporar um botão interativo, este guia mostra exatamente como fazer isso. Usando Aspose.Words, você pode adicionar programaticamente um botão de comando em apenas algumas linhas de código, eliminando a necessidade de trabalho manual de UI no Word.

Neste tutorial você aprenderá como:

* Inicializar um arquivo Word em branco com C#.
* Inserir um controle ActiveX **CommandButton**.
* Definir as propriedades do botão, como nome e legenda.
* Salvar o documento para que o botão apareça quando o arquivo for aberto no Microsoft Word.

Nenhuma ferramenta externa é necessária além da biblioteca Aspose.Words for .NET, e os passos funcionam com .NET 6+ ou .NET Framework 4.6.2 e posteriores.

## Prerequisites

Antes de começar, certifique‑se de que você tem:

| Requisito | Motivo |
|------------|--------|
| .NET 6 SDK (ou .NET Framework 4.6.2+) | Fornece o runtime para o projeto C#. |
| Visual Studio 2022 (ou qualquer IDE C#) | Facilita escrever, compilar e executar o código. |
| Pacote NuGet Aspose.Words for .NET | Fornece as classes `Document`, `DocumentBuilder` e `Forms2OleControl` usadas no exemplo. |
| Conhecimento básico da sintaxe C# | Permite que você siga o código sem curvas de aprendizado adicionais. |

Você pode adicionar o pacote Aspose.Words via o console NuGet:

```powershell
Install-Package Aspose.Words
```

## Etapa 1: Configurar um novo projeto console C#

Crie uma aplicação console que irá gerar o arquivo Word. Abra um terminal e execute:

```bash
dotnet new console -n WordButtonDemo
cd WordButtonDemo
dotnet add package Aspose.Words
```

O arquivo `Program.cs` gerado hospedará o código mostrado nas etapas seguintes.

## Etapa 2: Criar um documento em branco e um DocumentBuilder

A primeira operação é instanciar um objeto `Document`, que representa um arquivo `.docx` vazio, e um `DocumentBuilder` que permite editar o conteúdo do documento.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Step 2: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Por que isso importa:**  
`Document` é o contêiner para todos os elementos do Word (parágrafos, tabelas, controles). `DocumentBuilder` fornece uma API fluente para inserir objetos na posição atual do cursor sem lidar com coleções de nós de baixo nível.

## Etapa 3: Inserir um controle ActiveX CommandButton

Aspose.Words suporta a inserção de controles ActiveX legados através do método `InsertForms2OleControl`. O método requer o tipo de controle e o tamanho desejado em pontos.

```csharp
        // Step 3: Insert an ActiveX CommandButton control (size: 100x30 points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            ControlType.CommandButton, 100, 30);
```

**O que acontece nos bastidores:**  
O Word trata um controle ActiveX como um objeto OLE (Object Linking and Embedding). A classe `Forms2OleControl` encapsula os dados OLE e expõe propriedades como `Name` e `Caption`.

## Etapa 4: Configurar o nome e a legenda do botão

Depois que o controle é colocado, você pode personalizar suas propriedades de tempo de execução. Definir um `Name` significativo ajuda a identificar o botão posteriormente, enquanto `Caption` define o texto exibido no botão.

```csharp
        // Step 4: Set the button's name and displayed caption
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";
```

**Dica profissional:**  
Se você planeja tratar o evento de clique do botão com VBA, o `Name` torna‑se o nome da macro que você referencia, por exemplo, `Sub btnSubmit_Click()`.

## Etapa 5: Salvar o documento no disco

Finalmente, grave o documento em um arquivo `.docx`. Escolha uma pasta na qual você tenha permissão de escrita; o exemplo usa um caminho relativo, que resolve para o diretório de saída do projeto.

```csharp
        // Step 5: Save the document containing the button
        string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Executar o programa produz `CommandButton.docx`. Abrir o arquivo no Microsoft Word exibe um botão **Submit** clicável:

![Documento Word com um botão de comando Submit](/images/command-button.png "Captura de tela de um documento Word contendo um botão de comando Submit criado com C#")

*Texto alternativo da imagem (og_image_alt):* `Captura de tela de um documento Word contendo um botão de comando Submit criado com C#`

## Verificando o resultado

1. Abra o Word e abra `CommandButton.docx`.  
2. Você deve ver um botão rotulado **Submit** no corpo do documento.  
3. Passar o mouse sobre o botão revela o nome `btnSubmit` no painel **Properties** (aba Desenvolvedor → Propriedades).  

Se o botão não aparecer, certifique‑se de que a aba **Developer** está habilitada no Word (File → Options → Customize Ribbon → marque *Developer*). Controles ActiveX ficam ocultos quando a aba está desativada.

## Lidando com variações comuns e casos de borda

| Situação | Ajuste recomendado |
|-----------|------------------------|
| **Tamanho de botão diferente** | Altere os argumentos de largura e altura em `InsertForms2OleControl`. Por exemplo, `150, 40` cria um botão maior. |
| **Múltiplos botões** | Chame `InsertForms2OleControl` repetidamente, movendo o cursor do builder entre as chamadas (`builder.Writeln();`). |
| **Botão sem ActiveX** | Use `InsertFormField` para adicionar um campo de formulário legado (por exemplo, uma caixa de seleção) se precisar de compatibilidade com versões mais antigas do Word que bloqueiam ActiveX. |
| **Uso multiplataforma** | Controles ActiveX funcionam apenas nas versões Windows do Word. Para Mac ou visualizadores baseados na web, considere inserir um hyperlink estilizado como botão. |
| **Avisos de segurança** | O Word pode exibir um aviso de segurança ao abrir um documento contendo controles ActiveX. Assinar o documento com um certificado confiável reduz esse atrito. |

## Exemplo completo e executável

A seguir está o programa completo que você pode copiar‑colar em `Program.cs`. Ele compila e executa sem modificações após adicionar o pacote NuGet Aspose.Words.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control (size: 100x30 points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            ControlType.CommandButton, 100, 30);

        // Set the button's name and displayed caption
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";

        // Save the document containing the button
        string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Saída esperada no console:**

```
Document saved to C:\Path\To\WordButtonDemo\bin\Debug\net6.0\CommandButton.docx
```

Abrir o arquivo gerado mostra o botão **Submit** pronto para interação.

## Conclusão

Agora você sabe como **criar documento word c#** e **adicionar programaticamente botões de comando** usando Aspose.Words. O processo se resume a inicializar um `Document`, inserir um `Forms2OleControl`, configurar suas propriedades e salvar o arquivo. A partir daqui você pode:

* Adicionar mais controles (por exemplo, caixas de seleção, campos de texto) alterando `ControlType`.
* Anexar macros VBA ao botão para lógica personalizada.
* Combinar esta técnica com outros recursos do Aspose.Words, como mesclagem de correspondência ou preenchimento de modelo.

Experimente diferentes tamanhos, legendas e múltiplos botões para adequar ao seu cenário de automação. Happy coding!

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Criar documento Word com cabeçalho e rodapé usando Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Criar documento Word com Aspose.Words para .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Criar forma de grupo em documento Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}