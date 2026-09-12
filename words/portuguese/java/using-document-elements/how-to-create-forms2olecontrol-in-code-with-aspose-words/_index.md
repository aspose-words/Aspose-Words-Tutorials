---
category: general
date: 2026-09-11
description: Aprenda a criar forms2olecontrol em código usando Aspose.Words DocumentBuilder.
  Este guia passo a passo cobre a inserção de botão de comando ActiveX, o uso de setOleClassName
  e o dimensionamento.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create forms2olecontrol in code
- ActiveX command button
- Aspose.Words DocumentBuilder
- setOleClassName method
- Forms2OleControl size
language: pt
lastmod: 2026-09-11
og_description: Crie forms2olecontrol no código com Aspose.Words. Siga este guia para
  inserir um botão de comando ActiveX, definir seu nome de classe e ajustar seu tamanho.
og_image_alt: Screenshot of a Word document showing a newly created ActiveX command
  button inserted via code
og_title: Criar forms2olecontrol no código – guia completo do Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create forms2olecontrol in code using Aspose.Words DocumentBuilder.
    This step‑by‑step guide covers ActiveX command button insertion, setOleClassName
    usage, and sizing.
  headline: How to create forms2olecontrol in code with Aspose.Words
  type: TechArticle
- description: Learn how to create forms2olecontrol in code using Aspose.Words DocumentBuilder.
    This step‑by‑step guide covers ActiveX command button insertion, setOleClassName
    usage, and sizing.
  name: How to create forms2olecontrol in code with Aspose.Words
  steps:
  - name: Initialise the DocumentBuilder
    text: The `DocumentBuilder` class is the entry point for most document‑generation
      tasks in Aspose.Words. It gives you methods to add text, images, tables, and,
      importantly for this tutorial, OLE controls.
  - name: Insert the Forms2OleControl
    text: The `insertForms2OleControl` method returns a `Forms2OleControl` object.
      This object represents the OLE control placeholder that Word will render as
      an ActiveX button.
  - name: Specify the ActiveX class with setOleClassName
    text: Word needs to know which type of ActiveX control to render. The class name
      for a standard command button is `"Forms.CommandButton.1"`.
  - name: Adjust the Forms2OleControl size
    text: A button that is too small or too large looks unprofessional. You can control
      its dimensions with `setWidth` and `setHeight`.
  - name: Save the document and test
    text: After configuring the control, save the document to a location of your choice.
  - name: When to use Forms2OleControl vs. Content Controls
    text: If you only need simple data entry (e.g., a plain text field), Word’s built‑in
      content controls are lighter weight. Use `Forms2OleControl` when you require
      full ActiveX functionality such as event handling or custom VBA interaction.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: Como criar forms2olecontrol no código com Aspose.Words
url: /pt/java/using-document-elements/how-to-create-forms2olecontrol-in-code-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como criar forms2olecontrol em código com Aspose.Words

Se você precisar **criar forms2olecontrol em código**, este guia mostra exatamente como fazer isso usando a API Aspose.Words .NET. Seja automatizando um modelo que requer um botão de comando ActiveX ou simplesmente querendo enriquecer um documento Word programaticamente, os passos abaixo cobrem tudo, desde a inserção do controle até a configuração de sua aparência.

Neste tutorial você aprenderá como usar o **Aspose.Words DocumentBuilder** para inserir um **ActiveX command button**, definir sua classe com o **setOleClassName method**, e ajustar seu **Forms2OleControl size**. Nenhuma ferramenta externa é necessária — apenas um ambiente de desenvolvimento .NET e a biblioteca Aspose.Words.

## Pré-requisitos

* .NET 6.0 ou posterior instalado (o código também funciona com .NET Framework 4.7+)
* Uma versão recente do pacote NuGet Aspose.Words para .NET
* Familiaridade básica com C# e o conceito de controles ActiveX em documentos Word

If any of these are missing, install the NuGet package with:

```bash
dotnet add package Aspose.Words
```

## O que este tutorial cobre

* Criar uma instância de `DocumentBuilder`
* Inserir um `Forms2OleControl` (o objeto subjacente para um botão de comando ActiveX)
* Atribuir o nome de classe correto com `setOleClassName`
* Definir a largura e altura visuais usando as propriedades **Forms2OleControl size**
* Salvar o documento e verificar o resultado

Ao final do guia, você terá um arquivo Word totalmente funcional contendo um botão clicável que pode ser personalizado ainda mais ou vinculado a macros VBA.

---

## Como criar forms2olecontrol em código – passo a passo

### Etapa 1: Inicializar o DocumentBuilder

A classe `DocumentBuilder` é o ponto de entrada para a maioria das tarefas de geração de documentos no Aspose.Words. Ela fornece métodos para adicionar texto, imagens, tabelas e, importante para este tutorial, controles OLE.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document doc = new Document();

// Initialise the builder for the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Por que isso importa:**  
`DocumentBuilder` mantém a posição atual do cursor dentro do documento. Ao criá-lo cedo, você garante que qualquer inserção subsequente — como o **ActiveX command button** — apareça exatamente onde você deseja.

### Etapa 2: Inserir o Forms2OleControl

O método `insertForms2OleControl` retorna um objeto `Forms2OleControl`. Esse objeto representa o placeholder do controle OLE que o Word renderizará como um botão ActiveX.

```csharp
// Insert the Forms2OleControl at the current cursor location
Forms2OleControl commandButton = builder.InsertForms2OleControl();
```

**Por que isso importa:**  
Sem essa chamada você não pode manipular as propriedades do controle. O `Forms2OleControl` retornado fornece acesso total ao **setOleClassName method**, atributos de tamanho e outras configurações específicas de OLE.

### Etapa 3: Especificar a classe ActiveX com setOleClassName

O Word precisa saber qual tipo de controle ActiveX renderizar. O nome da classe para um botão de comando padrão é `"Forms.CommandButton.1"`.

```csharp
// Tell Word that this OLE control is a CommandButton
commandButton.SetOleClassName("Forms.CommandButton.1");
```

**Por que isso importa:**  
O método `setOleClassName` é a ponte entre o placeholder genérico OLE e o **ActiveX command button** concreto. Usar o nome de classe errado resulta em um objeto em branco ou em um erro de tempo de execução ao abrir o documento.

### Etapa 4: Ajustar o tamanho do Forms2OleControl

Um botão que é muito pequeno ou muito grande parece pouco profissional. Você pode controlar suas dimensões com `setWidth` e `setHeight`.

```csharp
// Set the visual dimensions (points) of the button
commandButton.SetWidth(80);   // width in points
commandButton.SetHeight(30);  // height in points
```

**Por que isso importa:**  
Essas propriedades constituem o **Forms2OleControl size**. Elas afetam como o botão aparece na interface do Word e garantem que qualquer macro anexada tenha área clicável suficiente.

### Etapa 5: Salvar o documento e testar

After configuring the control, save the document to a location of your choice.

```csharp
// Save the document as a .docx file
doc.Save("ActiveXButton.docx");
```

Abra `ActiveXButton.docx` no Microsoft Word. Você deverá ver um botão rotulado “CommandButton1” (a legenda padrão). Clicá‑lo não fará nada a menos que você adicione uma macro VBA, mas o controle em si está totalmente funcional.

**Expected output:**  

![Documento Word com um botão de comando ActiveX inserido](/images/activeX-button.png "Captura de tela de um documento Word mostrando um novo botão de comando ActiveX inserido via código")

*O texto alternativo da imagem contém a palavra‑chave principal para acessibilidade e SEO.*

---

## Entendendo a classe ActiveX Forms2OleControl

A classe `Forms2OleControl` encapsula a infraestrutura OLE de baixo nível que o Word usa para elementos ActiveX. Ela herda de `Shape`, o que significa que você também pode aplicar formatação típica de formas (por exemplo, bordas, rotação) se necessário.

* **ActiveX command button** – O caso de uso mais comum; você pode vinculá‑lo a uma macro via ferramentas de desenvolvedor do Word.
* **setOleClassName method** – Determina qual classe COM o Word carrega; outros valores válidos incluem `"Forms.TextBox.1"` e `"Forms.ComboBox.1"`.
* **Forms2OleControl size** – Controlado através de `SetWidth`/`SetHeight`. Esses métodos aceitam pontos (1 pt = 1/72 pol).

### Quando usar Forms2OleControl vs. Content Controls

Se você precisar apenas de entrada de dados simples (por exemplo, um campo de texto simples), os controles de conteúdo nativos do Word são mais leves. Use `Forms2OleControl` quando precisar de funcionalidade completa de ActiveX, como tratamento de eventos ou interação VBA personalizada.

---

## Definindo propriedades adicionais (opcional)

Embora os passos principais sejam suficientes para **criar forms2olecontrol em código**, muitas vezes você deseja ajustar finamente a aparência ou o comportamento do botão.

```csharp
// Change the button caption (requires a VBA macro to read it)
commandButton.SetOleData("Caption", "Submit");

// Disable the button initially
commandButton.SetOleData("Enabled", false);

// Add a tooltip
commandButton.SetOleData("ToolTipText", "Click to submit the form");
```

**Por que isso importa:**  
`SetOleData` permite escrever valores de propriedades arbitrárias diretamente no fluxo OLE. Esta é a maneira mais flexível de personalizar um **ActiveX command button** sem recorrer ao VBA.

---

## Armadilhas comuns e solução de problemas

| Sintoma | Causa provável | Correção |
|--------|----------------|----------|
| Botão aparece como uma caixa cinza | Nome de classe incorreto passado para `setOleClassName` | Verifique se a string é exatamente `"Forms.CommandButton.1"` (sensível a maiúsculas/minúsculas) |
| Tamanho não muda | Largura/Altura definidas antes de inserir o controle | Sempre chame `SetWidth`/`SetHeight` **depois** de `InsertForms2OleControl` |
| Documento lança “OLE object not found” ao abrir | Licença do Aspose.Words ausente (versão de avaliação pode limitar OLE) | Aplique uma licença válida ou use o teste gratuito com suporte total a OLE |
| Legenda do botão permanece “CommandButton1” | `SetOleData` não usado ou macro não lê a propriedade | Use uma macro VBA para ler a propriedade `"Caption"` ou defina a legenda via UI do Word |

---

## Exemplo completo e executável

Abaixo está um aplicativo console completo que você pode copiar, colar e executar. Ele demonstra tudo o que foi abordado neste tutorial.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace Forms2OleControlDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1. Create a new document and a DocumentBuilder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2. Insert the Forms2OleControl (ActiveX placeholder)
            Forms2OleControl commandButton = builder.InsertForms2OleControl();

            // 3. Set the ActiveX class to CommandButton
            commandButton.SetOleClassName("Forms.CommandButton.1");

            // 4. Define the visual size of the button
            commandButton.SetWidth(80);   // 80 points = ~1.11 inches
            commandButton.SetHeight(30);  // 30 points = ~0.42 inches

            // Optional: set a custom caption via OLE data (requires VBA to read)
            commandButton.SetOleData("Caption", "Submit");

            // 5. Save the document
            string outputPath = "ActiveXButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Explicação de cada seção**

* **Using directives** – Importa o namespace Aspose.Words necessário para `Document`, `DocumentBuilder` e `Forms2OleControl`.
* **Document creation** – Instancia um arquivo Word vazio.
* **InsertForms2OleControl** – Posiciona o controle OLE no cursor atual do builder.
* **SetOleClassName** – Informa ao Word que o controle é um **ActiveX command button**.
* **SetWidth / SetHeight** – Ajusta o **Forms2OleControl size** para uma aparência profissional.
* **SetOleData (optional)** – Demonstra como escrever propriedades extras, como uma legenda.
* **Save** – Grava o arquivo `.docx` final no disco.

Execute o programa (`dotnet run`) e abra `ActiveXButton.docx`. Você deverá ver um botão que pode ser vinculado a uma macro posteriormente.

---

## Conclusão

Agora você sabe como **criar forms2olecontrol em código** usando Aspose.Words, desde a inicialização do `DocumentBuilder` até a configuração do **ActiveX command button** com `setOleClassName` e o controle do seu **Forms2OleControl size**. Essa abordagem permite automatizar documentos Word complexos, incorporar elementos de UI interativos e manter toda a lógica dentro

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Como criar campos de formulário e adicionar conteúdo usando DocumentBuilder no Aspose.Words para Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Criar Group Shape em documento Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Criar forma retangular no Word com Aspose.Words – Guia passo a passo](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}