---
category: general
date: 2026-10-23
description: Crie um documento Word em branco com C# e aprenda a inserir controles
  ActiveX, incluindo um botão, usando Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert activex
- create activex control
- word document activex button
language: pt
lastmod: 2026-10-23
og_description: Crie um documento Word em branco com C# e aprenda como inserir controles
  ActiveX, incluindo um botão, usando Aspose.Words.
og_image_alt: Result of creating a blank Word document with an ActiveX Submit button
og_title: Crie um documento Word em branco e adicione um botão ActiveX em C#
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Create blank Word document with C# and learn how to insert ActiveX
    controls, including a button, using Aspose.Words.
  headline: Create a blank Word document and add an ActiveX button in C#
  type: TechArticle
- description: Create blank Word document with C# and learn how to insert ActiveX
    controls, including a button, using Aspose.Words.
  name: Create a blank Word document and add an ActiveX button in C#
  steps:
  - name: Instantiate a `Document`.
    text: Instantiate a `Document`.
  - name: Use `DocumentBuilder` to work with the file.
    text: Use `DocumentBuilder` to work with the file.
  - name: Call `InsertForms2OleControl` to **how to insert activex** controls.
    text: Call `InsertForms2OleControl` to **how to insert activex** controls.
  - name: Configure the control’s properties (**create activex control**).
    text: Configure the control’s properties (**create activex control**).
  - name: Save the file, yielding a **word document activex button** ready for VBA
      integration.
    text: Save the file, yielding a **word document activex button** ready for VBA
      integration.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: Criar um documento Word em branco e adicionar um botão ActiveX em C#
url: /pt/java/document-manipulation/create-a-blank-word-document-and-add-an-activex-button-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar um documento Word em branco e adicionar um botão ActiveX em C#

Se você precisar **criar documento Word em branco** programaticamente, este guia mostra exatamente como fazer. Você verá um exemplo completo e executável que cria um novo documento, insere um ActiveX CommandButton e salva o arquivo — tudo com Aspose.Words for .NET.

Trabalhar com arquivos Word frequentemente requer mais do que texto simples. Adicionar um **botão ActiveX** permite incorporar funcionalidade interativa que pode ser usada em modelos habilitados para macro ou soluções apenas para Windows. Ao final deste tutorial você será capaz de inserir qualquer controle ActiveX, mas nos concentramos no cenário mais comum: um **botão activex em documento Word** que envia um formulário.

## Pré-requisitos

* .NET 6.0 ou posterior (o código também funciona com .NET Framework 4.7+)
* Visual Studio 2022 (ou qualquer IDE C#)
* **Aspose.Words for .NET** pacote NuGet  
  ```bash
  dotnet add package Aspose.Words
  ```
* Familiaridade básica com a sintaxe C#

> **Dica profissional:** Aspose.Words é uma biblioteca comercial, mas oferece uma licença temporária gratuita para testes. Instale a licença cedo para evitar a marca d'água de avaliação.

## Etapa 1: Criar um documento Word em branco com Aspose.Words

O primeiro passo é instanciar um objeto `Document`. Ele representa um arquivo `.docx` vazio na memória.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();
```

`Document` começa sem seções, páginas ou conteúdo. É a tela em branco que você precisa para cenários de **criar documento Word em branco**, como gerar relatórios do zero.

## Etapa 2: Obter um DocumentBuilder para editar o documento

`DocumentBuilder` fornece uma API conveniente para adicionar texto, imagens e controles. Usaremos para posicionar o controle ActiveX.

```csharp
// Obtain a DocumentBuilder tied to the blank document
DocumentBuilder builder = new DocumentBuilder(document);
```

O builder adiciona automaticamente uma seção padrão e uma primeira página, para que você possa começar a inserir objetos imediatamente.

## Etapa 3: Como inserir controles ActiveX no documento

Aspose.Words expõe `InsertForms2OleControl` para incorporar objetos OLE/ActiveX. O método requer o tipo de controle, largura e altura (em pontos). Abaixo inserimos um **CommandButton** — o botão de formulário clássico que você vê em modelos Word legados.

```csharp
// Insert an ActiveX CommandButton control (100 × 30 points)
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.COMMANDBUTTON, 100, 30);
```

> **Por que isso funciona:** `Forms2OleControlType.COMMANDBUTTON` indica ao Word para criar um botão que pode responder a eventos de clique quando o documento é aberto em um ambiente Windows que suporta ActiveX.

## Etapa 4: Criar um controle ActiveX – definir suas propriedades

Agora damos ao botão um nome programático e uma legenda visível. Esta é a parte de **criar controle activex** que os desenvolvedores costumam ignorar.

```csharp
// Set the button's name (used in VBA) and the text shown to users
commandButton.Name = "btnSubmit";
commandButton.Caption = "Submit";
```

* `Name` é o identificador que você referenciará nas macros VBA (`ActiveDocument.InlineShapes("btnSubmit")`).
* `Caption` é o rótulo exibido no próprio botão.

## Etapa 5: Salvar o documento Word com o botão ActiveX

Finalmente, grave o documento no disco. A extensão do arquivo deve ser `.docx` (ou `.docm` se você planeja adicionar macros depois). O exemplo salva em uma pasta placeholder — substitua pelo seu próprio caminho.

```csharp
// Save the document containing the ActiveX button
string outputPath = @"C:\Temp\ActiveXButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Quando você abrir o arquivo resultante no Microsoft Word (somente Windows), verá um **botão activex em documento Word** funcional que pode ser conectado a código VBA.

## Exemplo completo em funcionamento

Abaixo está o programa completo que você pode copiar e colar em um novo projeto de console.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXButtonDemo
{
    class Program
    {
        static void Main()
        {
            // 1. Create a blank Word document
            Document document = new Document();

            // 2. Get a builder to edit the document
            DocumentBuilder builder = new DocumentBuilder(document);

            // 3. Insert an ActiveX CommandButton (100 × 30 points)
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);

            // 4. Configure the button
            commandButton.Name = "btnSubmit";
            commandButton.Caption = "Submit";

            // 5. Save the file
            string outputPath = @"C:\Temp\ActiveXButton.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Saída esperada ao executar o programa**

```
Document saved to C:\Temp\ActiveXButton.docx
```

Abra o `ActiveXButton.docx` gerado no Word, e você verá um botão rotulado **Submit** posicionado no topo da primeira página.

## Casos de borda e armadilhas comuns

| Situação | O que observar | Recomendação |
|-----------|-------------------|----------------|
| Executando no macOS ou Linux | ActiveX é uma tecnologia somente para Windows, então o botão aparecerá como um placeholder. | Use o tutorial apenas para modelos direcionados ao Windows. |
| Documento aberto no Word Online | Controles ActiveX não são suportados na visualização do navegador. | Forneça uma UI alternativa ou instrua os usuários a abrir o arquivo no cliente desktop. |
| Necessita de um arquivo habilitado para macro | Arquivos `.docx` não podem armazenar código VBA. | Salve como `.docm` (`document.Save("MyFile.docm", SaveFormat.Docm)`) e adicione a macro separadamente. |
| Descompasso de tamanho do controle | Valores de largura/altura estão em pontos (1 pt ≈ 1/72 pol). | Ajuste os valores numéricos para obter o tamanho visual desejado. |

## Perguntas frequentes

**Como inserir controles ActiveX diferentes de um botão?**  
Use o mesmo método `InsertForms2OleControl`, mas passe um valor diferente do enum `Forms2OleControlType`, como `COMBOBOX` ou `LISTBOX`.

**Posso alterar a fonte ou a cor do botão?**  
A aparência do botão ActiveX é controlada pelo aplicativo host (Word) e pelo tema do Windows subjacente. Você pode modificar propriedades como `ForeColor` e `BackColor` via VBA após o documento ser aberto.

**Existe uma maneira de adicionar um manipulador de clique diretamente do C#?**  
Não. O evento de clique deve ser tratado por VBA ou um add‑in do Word, pois o botão roda dentro do processo do Word, não da sua aplicação .NET.

## Conclusão

Agora você sabe como **criar documento Word em branco** programaticamente e incorporar um **botão ActiveX** usando Aspose.Words for .NET. As etapas abordadas:

1. Instanciar um `Document`.
2. Usar `DocumentBuilder` para trabalhar com o arquivo.
3. Chamar `InsertForms2OleControl` para **como inserir controles activex**.
4. Configurar as propriedades do controle (**criar controle activex**).
5. Salvar o arquivo, resultando em um **botão activex em documento Word** pronto para integração VBA.

A partir daqui você pode explorar a adição de outros tipos de controle, conectar macros VBA ou converter o documento para PDF preservando o botão (como uma imagem estática). Experimente diferentes tamanhos, legendas e nomes.

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá-lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Como adicionar botão ActiveX em um documento Word com Aspose.Words](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)
- [Criar documento Word com botão ActiveX – Guia C#](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}