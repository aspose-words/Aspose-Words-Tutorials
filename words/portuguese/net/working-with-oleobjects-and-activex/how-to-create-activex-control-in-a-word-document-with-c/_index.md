---
category: general
date: 2026-09-14
description: Crie um controle ActiveX em um documento Word com C#. Aprenda como inserir
  ActiveX, adicionar um botão interativo e gerar o arquivo .docx programaticamente.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex control
- how to insert activex
- add interactive button
- create word document
- create button with code
language: pt
lastmod: 2026-09-14
og_description: Crie um controle ActiveX em um documento Word com C#. Siga este exemplo
  completo para inserir ActiveX, adicionar um botão interativo e salvar o arquivo.
og_image_alt: Screenshot of a Word document containing a newly created ActiveX CommandButton
og_title: Criar controle ActiveX no Word usando C# – guia passo a passo
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Create ActiveX control in a Word document with C#. Learn how to insert
    ActiveX, add interactive button, and generate the .docx file programmatically.
  headline: How to create ActiveX control in a Word document with C#
  type: TechArticle
tags:
- ActiveX
- C#
- Word automation
title: Como criar um controle ActiveX em um documento do Word com C#
url: /pt/net/working-with-oleobjects-and-activex/how-to-create-activex-control-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como criar controle ActiveX em um documento Word com C#

Se você precisar **criar controle ActiveX** dentro de um arquivo Microsoft Word, este guia mostra uma solução completa, pronta‑para‑executar. Você verá exatamente como inserir um ActiveX CommandButton, definir suas propriedades e salvar o arquivo `.docx` resultante usando apenas código C#.

Adicionar um botão interativo a um documento Word é uma necessidade comum quando você deseja que os usuários finais acionem macros ou lógica personalizada diretamente da interface do documento. O exemplo abaixo demonstra **como inserir ActiveX** sem depender de ferramentas de terceiros, e também cobre **como criar documento Word** programaticamente.

Ao final deste tutorial você será capaz de **criar botão com código**, personalizar sua legenda e produzir um arquivo Word portátil que preserva o controle ActiveX.

## Pré-requisitos

- .NET 6.0 ou posterior (a biblioteca Aspose.Words for .NET funciona com .NET Core e .NET Framework)
- Uma referência ao pacote NuGet `Aspose.Words`  
  ```bash
  dotnet add package Aspose.Words
  ```
- Conhecimento básico de C# e programação orientada a objetos

## Etapa 1: Configurar o projeto e importar namespaces

Crie um novo projeto de console (ou integre o código em qualquer aplicação C# existente). Importe os namespaces necessários para que o compilador possa localizar as classes de processamento de Word.

```csharp
using System;
using System.Drawing;               // Provides RectangleF
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
```

> **Por que esta etapa importa** – A API `Aspose.Words` fornece as classes `Document`, `DocumentBuilder` e `Forms2OleControl` que permitem manipular arquivos Word ao nível de objeto. Sem essas referências o restante do código não compilaria.

## Etapa 2: Criar um novo documento Word e um DocumentBuilder

O objeto `Document` representa todo o pacote `.docx`, enquanto `DocumentBuilder` oferece uma API fluente para inserção de conteúdo.

```csharp
// Step 2: Initialize a fresh Word document
Document document = new Document();

// Attach a builder to the document – the builder knows where to write next
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Explicação** – Instanciar um novo `Document` fornece uma tela limpa. O cursor do builder começa no início da primeira seção, pronto para a próxima inserção.

## Etapa 3: Inserir o ActiveX CommandButton

Use `InsertForms2OleControl` para colocar um controle ActiveX em uma localização específica. O método requer o tipo de controle e um `RectangleF` que define as coordenadas X/Y e o tamanho (em pontos).

```csharp
// Step 3: Add an ActiveX CommandButton at (100,100) with width 120 and height 30
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,
    new RectangleF(100, 100, 120, 30));
```

> **Por que isso funciona** – `OleControlType.CommandButton` indica à API que deve criar um CommandButton padrão do Windows. O retângulo posiciona o botão em relação ao canto superior esquerdo da página, permitindo que você **adicione botão interativo** exatamente onde precisar.

## Etapa 4: Configurar as propriedades do botão

Agora defina o texto visível do botão (`Caption`) e seu nome interno (`Name`). Essas propriedades são o que os usuários veem e o que o código VBA pode referenciar posteriormente.

```csharp
// Step 4: Define the button’s caption and programmatic name
commandButton.Caption = "Click Me";
commandButton.Name = "btnClick";
```

> **Dica prática** – O `Name` deve ser único dentro do documento; caso contrário, macros VBA podem referenciar o controle errado.

## Etapa 5: Salvar o documento

Finalmente, grave o arquivo no disco. O controle ActiveX é armazenado dentro do pacote Word, portanto o arquivo salvo manterá a funcionalidade completa ao ser aberto no Microsoft Word.

```csharp
// Step 5: Persist the document – the ActiveX control stays embedded
string outputPath = @"C:\Temp\CommandButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

> **Resultado** – Abrir `CommandButton.docx` no Word exibe um CommandButton clicável rotulado “Click Me”. O controle pode ser vinculado a uma macro via a interface do Word (`Developer → Design Mode → Properties`).

## Listagem completa do código-fonte

Juntando todas as etapas resulta em um único programa autônomo que você pode copiar, colar e executar.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Create a new document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert an ActiveX CommandButton at the desired location
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new RectangleF(100, 100, 120, 30));

        // Set the button's caption and internal name
        commandButton.Caption = "Click Me";
        commandButton.Name = "btnClick";

        // Save the document – the control is preserved
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### Saída esperada

Executar o programa imprime uma linha de confirmação:

```
Document saved to C:\Temp\CommandButton.docx
```

Ao abrir o arquivo gerado no Microsoft Word, você verá um **CommandButton** posicionado nas coordenadas especificadas. Clicar no botão no modo de design o destaca; no modo de execução ele se comporta como qualquer botão ActiveX padrão.

## Variações comuns e casos extremos

| Cenário | Ajuste |
|----------|------------|
| **Tipo de controle diferente** | Substitua `OleControlType.CommandButton` por `OleControlType.CheckBox`, `OleControlType.OptionButton`, etc. |
| **Múltiplos botões** | Chame `InsertForms2OleControl` repetidamente, atualizando as coordenadas `RectangleF` para cada novo botão. |
| **Dimensionamento dinâmico** | Calcule as dimensões do retângulo com base no tamanho da página (`builder.PageSetup.PageWidth`). |
| **Salvar em um stream** | Use `document.Save(stream, SaveFormat.Docx)` quando precisar retornar o arquivo de uma API web. |
| **Formato Word 97‑2003** | Altere o formato de salvamento para `SaveFormat.Doc` para produzir um arquivo `.doc` que ainda incorpora o controle ActiveX. |

> **Dica profissional:** Sempre teste o documento gerado na versão alvo do Word, pois versões mais antigas podem impor configurações de segurança que desativam controles ActiveX por padrão.

## Perguntas frequentes

**Isso funciona com .NET Core?**  
Sim. A biblioteca Aspose.Words é multiplataforma e totalmente compatível com .NET Core e .NET 5/6+.

**Posso atribuir uma macro ao botão programaticamente?**  
A API não incorpora código VBA diretamente. Após o documento ser gerado, abra-o no Word, habilite a guia Developer e grave ou escreva uma macro que referencie `btnClick`.

**E se o botão não aparecer?**  
Verifique se a guia `Developer` está habilitada no Word e se o documento não está aberto em **Protected View**. Também confirme se as coordenadas do retângulo estão dentro das margens da página.

## Conclusão

Agora você sabe como **criar controle ActiveX** dentro de um arquivo Word usando C#. O tutorial abordou **como inserir ActiveX**, demonstrou **adicionar botão interativo**, mostrou **criar documento Word** do zero e ilustrou **criar botão com código** que persiste após a gravação.

A partir daqui você pode explorar tipos adicionais de ActiveX, conectar o botão a macros VBA ou incorporar a lógica em um serviço maior de geração de documentos. Experimente diferentes tamanhos, posições e propriedades de controle para adequar a experiência do usuário que você precisa.

---

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá-lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Criar novo documento Word](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Criar projeto VBA em documento Word](/words/english/net/working-with-vba-macros/create-vba-project/)
- [Criar e estilizar um documento Word no Aspose.Words para .NET](/words/english/net/document-styling/apply-paragraph-style/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}