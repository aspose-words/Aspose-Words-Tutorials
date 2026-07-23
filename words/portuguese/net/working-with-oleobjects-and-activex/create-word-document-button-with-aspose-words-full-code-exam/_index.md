---
category: general
date: 2026-07-23
description: criar botão de documento Word usando Aspose.Words – guia passo a passo
  para inserir um CommandButton ActiveX em um arquivo .docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document button
- ActiveX CommandButton
- DocumentBuilder
- InsertForms2OleControl
- Aspose.Words
language: pt
lastmod: 2026-07-23
og_description: 'crie botão de documento Word com Aspose.Words: aprenda a incorporar
  um CommandButton ActiveX em um arquivo Word em minutos.'
og_image_alt: Screenshot of a Word document showing an inserted CommandButton control
og_title: Botão Criar Documento Word – Guia Completo do Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-23'
  description: create word document button using Aspose.Words – step‑by‑step guide
    to insert an ActiveX CommandButton into a .docx file.
  headline: create word document button with Aspose.Words – Full Code Example
  type: TechArticle
- description: create word document button using Aspose.Words – step‑by‑step guide
    to insert an ActiveX CommandButton into a .docx file.
  name: create word document button with Aspose.Words – Full Code Example
  steps:
  - name: '**Creates** an OLE object inside the Word file.'
    text: '**Creates** an OLE object inside the Word file.'
  - name: '**Registers** it as an ActiveX CommandButton, which Word will render as
      a clickable UI element.'
    text: '**Registers** it as an ActiveX CommandButton, which Word will render as
      a clickable UI element.'
  - name: '**Positions** it according to the rectangle we supplied.'
    text: '**Positions** it according to the rectangle we supplied.'
  - name: Launch Microsoft Word.
    text: Launch Microsoft Word.
  - name: Navigate to **File → Open** and select `CommandButton.docx`.
    text: Navigate to **File → Open** and select `CommandButton.docx`.
  - name: You should see a rectangular button labeled “CommandButton1”.
    text: You should see a rectangular button labeled “CommandButton1”.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- ActiveX
- CommandButton
title: Botão para criar documento Word com Aspose.Words – Exemplo completo de código
url: /pt/net/working-with-oleobjects-and-activex/create-word-document-button-with-aspose-words-full-code-exam/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# criar botão de documento Word com Aspose.Words – Guia de Programação Completo

Já precisou **criar botão de documento Word** mas não tinha certeza de qual API usar? Você não está sozinho—a maioria dos desenvolvedores encontra um obstáculo ao tentar incorporar controles interativos em um arquivo .docx. A boa notícia? Com Aspose.Words para .NET você pode inserir um ActiveX CommandButton totalmente funcional em um documento Word em apenas algumas linhas de código.

Neste tutorial vamos percorrer todo o processo: desde a configuração do projeto, inicialização de um `DocumentBuilder`, inserção do botão com `InsertForms2OleControl` e, finalmente, salvar o arquivo para que o Word reconheça o controle. Ao final, você terá um arquivo Word pronto‑para‑uso que contém um botão clicável—sem necessidade de acrobacias de COM interop.

## O que você precisará

- **.NET 6.0** ou posterior (o código também funciona com .NET Framework 4.6+).  
- Pacote NuGet **Aspose.Words for .NET** (versão 23.9 ou mais recente).  
- Um entendimento básico de C# (manteremos a sintaxe amigável para iniciantes).  
- Visual Studio 2022 ou qualquer IDE de sua preferência.

É isso—sem referências COM adicionais, sem interop do Office, apenas código gerenciado puro.

## Etapa 1: Configurar Aspose.Words para **criar botão de documento Word**

Primeiro, adicione o pacote Aspose.Words ao seu projeto:

```bash
dotnet add package Aspose.Words
```

Ou, se estiver usando a UI do NuGet no Visual Studio, procure por “Aspose.Words” e clique em **Install**. Esta única linha lhe dá acesso ao `Document`, `DocumentBuilder` e ao método `InsertForms2OleControl` que precisaremos mais adiante.

> **Dica profissional:** Mantenha seus pacotes NuGet atualizados; versões mais recentes frequentemente incluem correções de bugs para o tratamento de ActiveX.

## Etapa 2: Inicializar **DocumentBuilder** para um **ActiveX CommandButton**

Agora criamos um novo documento Word e instanciamos um `DocumentBuilder`. Pense no `DocumentBuilder` como o pincel que permite desenhar conteúdo na tela.

```csharp
using System;
using System.Drawing;               // For Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 2.1: Create a new empty document
        Document document = new Document();

        // Step 2.2: Initialize DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

Observe como importamos `System.Drawing`—a estrutura `Rectangle` define a localização e o tamanho do botão. É aqui que o **ActiveX CommandButton** viverá.

## Etapa 3: Usar **InsertForms2OleControl** para **adicionar um CommandButton**

Aqui está o coração do tutorial: inserir o próprio botão. O método `InsertForms2OleControl` recebe três argumentos—tipo de controle, um `Rectangle` e, opcionalmente, um nome. Usaremos `OleControlType.CommandButton` para especificar o controle exato que desejamos.

```csharp
        // Step 3: Insert an ActiveX CommandButton at (0,0) with width=100, height=30
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new Rectangle(0, 0, 100, 30));
```

Essa única chamada faz muito:

1. **Cria** um objeto OLE dentro do arquivo Word.  
2. **Registra** como um ActiveX CommandButton, que o Word renderizará como um elemento de UI clicável.  
3. **Posiciona** de acordo com o retângulo fornecido.

Se precisar alterar a legenda do botão ou outras propriedades, você pode fazê‑lo após a inserção acessando o `OleFormat` subjacente. Para a maioria dos cenários, a legenda padrão (“CommandButton1”) é suficiente.

## Etapa 4: Salvar o Documento Word contendo o **CommandButton**

Salvar é simples—basta apontar para uma pasta onde você tenha permissão de escrita. A extensão do arquivo deve ser `.docx` para que o botão sobreviva ao processo.

```csharp
        // Step 4: Save the document with the embedded button
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Ao abrir `CommandButton.docx` no Microsoft Word, você verá um pequeno botão no canto superior esquerdo da primeira página. Clicá‑lo não faz nada por padrão (isso exigiria VBA), mas o controle está totalmente funcional e pode ser configurado posteriormente.

> **Por que isso funciona:** Aspose.Words grava o fluxo OLE diretamente no pacote DOCX, contornando a necessidade de o Word gerar o controle em tempo de execução. Isso garante que o botão apareça exatamente onde você o posicionou.

## Etapa 5: Verificar o Botão no Word

Abra o arquivo gerado:

1. Inicie o Microsoft Word.  
2. Navegue até **File → Open** e selecione `CommandButton.docx`.  
3. Você deverá ver um botão retangular rotulado “CommandButton1”.

Se não vir o botão, certifique‑se de que o **Design Mode** está habilitado (Developer → Design Mode). Isso alterna a representação visual dos controles ActiveX.

## Etapa 6: Opções Avançadas – Personalizando o **ActiveX CommandButton**

Abaixo estão alguns ajustes rápidos que podem ser úteis:

| Objetivo | Trecho de Código |
|------|--------------|
| Alterar legenda | ```csharp<br/>OleFormat ole = builder.CurrentParagraph.Runs[0].OleFormat;<br/>ole.OleControlCaption = "Submit";``` |
| Definir nome da macro (requer suporte a macros do Word) | ```csharp<br/>ole.OleControlMacroName = "MyMacro";``` |
| Redimensionar após inserção | ```csharp<br/>builder.MoveToDocumentEnd();<br/>builder.InsertForms2OleControl(OleControlType.CommandButton, new Rectangle(0,0,150,40));``` |

Esses trechos demonstram a flexibilidade do `InsertForms2OleControl`. Você pode até incorporar outros controles ActiveX como `CheckBox` ou `ListBox` trocando o enum `OleControlType`.

## Exemplo Completo Funcional

Abaixo está o programa completo, pronto para copiar e colar, que **cria um botão de documento Word** do zero:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class CreateWordDocumentButton
{
    static void Main()
    {
        // 1️⃣ Create a new empty document
        Document document = new Document();

        // 2️⃣ Initialize DocumentBuilder – the tool that lets us edit the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Insert an ActiveX CommandButton at position (0,0) with size 100x30
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new Rectangle(0, 0, 100, 30));

        // 4️⃣ Save the .docx file – this is where the button lives
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);

        Console.WriteLine($"✅ Document with button saved to: {outputPath}");
    }
}
```

**Saída esperada ao executar o programa:**

```
✅ Document with button saved to: C:\Temp\CommandButton.docx
```

Abra o arquivo resultante e você verá o botão exatamente onde o código o posicionou.

## Armadilhas Comuns & Como Evitá‑las

- **Referência `System.Drawing` ausente** – A estrutura `Rectangle` está lá; sem ela o compilador reclamará.  
- **Uso de uma versão antiga do Aspose.Words** – As versões iniciais não suportavam totalmente `InsertForms2OleControl`. Atualize para o pacote estável mais recente.  
- **Salvar como `.doc` em vez de `.docx`** – O fluxo OLE é removido no formato binário mais antigo, fazendo o botão desaparecer.  
- **Executar em um servidor sem interface (headless) sem o Word instalado** – O botão ainda estará no arquivo, mas você não poderá visualizá‑lo sem o Word. Isso é aceitável para pipelines de geração automatizada.

## Próximos Passos – Expandindo o fluxo de trabalho de **criar botão de documento Word**

Agora que você dominou o básico, considere estas ideias avançadas:

- **Anexar macros VBA** ao botão para lógica de negócios personalizada.  
- **Gerar múltiplos botões** em um loop para formulários dinâmicos.  
- **Combinar com Aspose.PDF** para exportar o mesmo documento para PDF preservando o layout visual (o botão se torna uma imagem estática no PDF).  
- **

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Criar Documento Word com Aspose.Words para .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Criar forma retangular no Word com Aspose.Words – Guia passo a passo](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Inserir imagem inline em documento Word usando Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}