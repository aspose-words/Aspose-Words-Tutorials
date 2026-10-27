---
category: general
date: 2026-10-26
description: Aprenda como criar um documento Word em C# e adicionar um botão ActiveX
  programaticamente. Este guia passo a passo cobre a inserção de um botão de comando,
  ocultá‑lo no tempo de design e salvar o arquivo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- how to add activex button
- create command button word
- programmatically add command button
language: pt
lastmod: 2026-10-26
og_description: Crie um documento Word em C# e adicione programaticamente um botão
  ActiveX. Siga este tutorial completo para incorporar um botão de comando que aparece
  apenas em tempo de execução.
og_image_alt: Screenshot of a Word document created with C# that contains an ActiveX
  command button
og_title: Criar um documento Word em C# com um botão de comando ActiveX – guia completo
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn how to create Word document C# and add an ActiveX button programmatically.
    This step‑by‑step guide covers inserting a command button, hiding it at design
    time, and saving the file.
  headline: How to create Word document C# with an ActiveX command button
  type: TechArticle
tags:
- C#
- Aspose.Words
- ActiveX
- Word automation
title: Como criar um documento Word em C# com um botão de comando ActiveX
url: /pt/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-with-an-activex-command-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como criar documento Word C# com um botão de comando ActiveX

Se você precisa **criar documento Word C#** que contenha um botão interativo, este guia mostra exatamente como fazer. Ao final das duas primeiras frases você entenderá a abordagem geral, e os passos seguintes o conduzirão linha a linha pelo código que deve ser escrito.

Você aprenderá a adicionar um botão ActiveX, ocultá‑lo durante o design e torná‑lo visível apenas quando o usuário abrir o arquivo. O tutorial também aborda armadilhas comuns, como avisos de segurança e compatibilidade de versões, para que você possa distribuir documentos confiáveis.

## Pré‑requisitos

Antes de começar, certifique‑se de que você tem:

* .NET 6.0 ou superior instalado  
* Uma cópia licenciada do **Aspose.Words for .NET** (a versão de avaliação gratuita serve para experimentação)  
* Familiaridade básica com C# e Visual Studio (qualquer IDE que suporte .NET serve)  

Nenhum pacote NuGet adicional é necessário além do `Aspose.Words`.

## Etapa 1: Criar um documento Word C# e inicializar o DocumentBuilder

O primeiro passo é instanciar um objeto `Document` e um `DocumentBuilder`. O `Document` representa o arquivo .docx completo, enquanto o `DocumentBuilder` fornece métodos fluentes para adicionar conteúdo.

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Create a new empty document.
        Document document = new Document();

        // Attach a builder to the document so we can insert nodes.
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Por que isso importa:** Sem um `DocumentBuilder` você teria que manipular o DOM OpenXML manualmente, o que é propenso a erros e mais difícil de ler. O builder abstrai esses detalhes e garante um arquivo Word bem‑formado.

## Etapa 2: Como adicionar botão ActiveX – inserir um controle CommandButton

Agora inserimos um **controle ActiveX CommandButton** em um local específico. O retângulo define a posição do botão (X, Y) e o tamanho (largura, altura) em pontos.

```csharp
        // Define the button's position and size.
        RectangleF buttonRect = new RectangleF(100, 100, 120, 30);

        // Insert the ActiveX CommandButton control.
        builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,   // Type of ActiveX control
            buttonRect,                          // Geometry
            "ClickMe");                          // Caption shown at design time
```

**Por que isso importa:** `InsertForms2OleControl` é o único método do Aspose.Words que cria um verdadeiro objeto OLE ActiveX. O valor enum `Forms2OleControlType.CommandButton` indica ao Word que deve incorporar um botão clicável em vez de um contêiner OLE genérico.

## Etapa 3: Adicionar programaticamente o botão de comando – ocultá‑lo até a execução

O Word trata qualquer forma inserida como visível por padrão. Para manter o botão invisível enquanto você projeta o modelo, defina a propriedade `Hidden` na forma que o builder acabou de criar.

```csharp
        // Retrieve the shape that represents the newly added control.
        Shape oleShape = (Shape)builder.CurrentParagraph.GetChildNodes(NodeType.Shape, true)[0];

        // Hide the shape; it will become visible when the document is opened.
        oleShape.Hidden = true;
```

**Por que isso importa:** Definir `Hidden = true` impede que o botão atrapalhe a visualização de design. Quando o documento for aberto no Word, o ambiente de tempo de execução revela automaticamente o controle, preservando a experiência de usuário pretendida.

## Etapa 4: Salvar o arquivo – criar documento Word com botão de comando

Por fim, grave o documento no disco. Escolha um caminho que sua aplicação possa gravar e use a extensão `.docx` para garantir compatibilidade moderna.

```csharp
        // Save the document containing the ActiveX button.
        document.Save(@"C:\Temp\ActiveXButton.docx");
    }
}
```

**Por que isso importa:** Salvar como `.docx` garante que o controle ActiveX incorporado esteja em conformidade com o padrão Office Open XML, suportado pelo Word 2007 e posteriores. Se precisar de suporte ao formato legado `.doc`, troque a extensão e use `SaveFormat.Doc`.

## Exemplo completo funcional

Juntando tudo, aqui está o programa completo que você pode copiar, colar e executar:

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Step 1: Create a new document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a CommandButton ActiveX control.
        RectangleF commandButtonRect = new RectangleF(100, 100, 120, 30);
        builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,
            commandButtonRect,
            "ClickMe");

        // Step 3: Hide the control so it appears only at runtime.
        Shape oleShape = (Shape)builder.CurrentParagraph
                                         .GetChildNodes(NodeType.Shape, true)[0];
        oleShape.Hidden = true;

        // Step 4: Save the document containing the ActiveX control.
        document.Save(@"C:\Temp\ActiveX.docx");
    }
}
```

**Saída esperada:** Após executar o programa, abra `C:\Temp\ActiveX.docx` no Microsoft Word. Você verá um documento em branco; o botão não está visível no modo de design. Pressione **Alt + F9** para alternar códigos de campo, então clique na área do botão — o Word renderizará o controle ActiveX e você poderá interagir com ele (por exemplo, dar duplo‑clique para ver suas propriedades).

## Casos limites e dicas de boas práticas

| Situação | O que observar | Correção recomendada |
|-----------|-------------------|-----------------|
| **Usuário desabilita ActiveX** | O Word pode exibir um aviso de segurança ou bloquear o controle. | Instrua os usuários finais a habilitar “Controles ActiveX” no Centro de Confiabilidade, ou forneça uma alternativa assinada por macro. |
| **Documento aberto no Word Online** | O Word Online não suporta ActiveX; o botão será omitido. | Use um hyperlink de fallback ou um controle de conteúdo se precisar de compatibilidade na nuvem. |
| **Configurações de DPI diferentes** | O tamanho do retângulo pode aparecer maior ou menor em telas de alta DPI. | Use `GraphicsUnit.Point` (padrão) e teste nas configurações de DPI mais comuns (96 dpi, 120 dpi). |
| **Múltiplos botões** | A chamada `GetChildNodes(NodeType.Shape, true)[0]` recupera apenas a primeira forma. | Percorra `builder.CurrentParagraph.GetChildNodes(NodeType.Shape, true)` e defina `Hidden` para cada forma que você adicionar. |
| **Formato legado .doc** | Algumas propriedades do ActiveX são perdidas ao salvar como `.doc`. | Prefira `.docx` a menos que tenha um requisito estrito de legado. |

**Dica de especialista:** Após inserir o botão, você pode atribuir uma macro à propriedade `OnAction` via a interface do Word. Isso permite definir um comportamento de clique personalizado sem escrever código C# adicional.

## Perguntas frequentes

* **Isso funciona com .NET Core?**  
  Sim. Aspose.Words for .NET é totalmente compatível com .NET 5, .NET 6 e versões posteriores. Basta referenciar o mesmo pacote NuGet.

* **Posso alterar a legenda do botão depois que o documento for gerado?**  
  A legenda definida em `InsertForms2OleControl` torna‑se o texto padrão em tempo de design. Os usuários podem editá‑la no Word, mas você também pode atualizar a legenda programaticamente acessando as propriedades do objeto OLE via API `Shape.OleFormat`.

* **E se eu precisar de um tamanho diferente para o botão?**  
  Ajuste os valores de `RectangleF`. Os dois primeiros parâmetros são as coordenadas X e Y; os dois últimos são largura e altura em pontos (1 pt = 1/72 polegada).

## Conclusão

Agora você sabe como **criar documento Word C#** e **adicionar programaticamente um botão de comando** usando Aspose.Words. O tutorial abordou a inicialização do documento, inserção de um botão ActiveX, ocultação até o tempo de execução e salvamento do arquivo final. Com esses blocos de construção, você pode incorporar controles interativos em qualquer modelo Word que gerar.

Em seguida, explore tópicos relacionados como **como adicionar evento ao botão ActiveX**, **estilizar botão de comando Word** com VBA, e **adicionar programaticamente botão de comando** a documentos existentes. Estender esse padrão para caixas de seleção, caixas de combinação ou objetos OLE personalizados segue os mesmos passos — basta mudar o valor do enum `Forms2OleControlType`.

Comece a experimentar: troque a legenda, ajuste a posição ou encadeie múltiplos controles. Quanto mais praticar, mais fluente ficará ao entregar documentos Word ricos e interativos a partir de C#. Feliz codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas em seus próprios projetos.

- [How to add a command button programmatically in a Word document](/words/english/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/)
- [How to add ActiveX button in a Word document with Aspose.Words](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)
- [Create Word Document with ActiveX Button – C# Guide](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}