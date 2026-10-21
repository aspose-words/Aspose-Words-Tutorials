---
category: general
date: 2026-10-07
description: Aprenda como adicionar um controle de conteúdo em um documento Word com
  Aspose.Words. Este guia também explica como criar um controle de conteúdo para o
  campo de ID de funcionário.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add content control word
- how to create content control
- add employee id field
- Aspose.Words content control
- C# Structured Document Tag
language: pt
lastmod: 2026-10-07
og_description: Adicione um controle de conteúdo em um documento Word usando Aspose.Words.
  Siga este tutorial completo para aprender como criar um controle de conteúdo e adicionar
  um campo de ID de funcionário.
og_image_alt: Screenshot of a Word document showing an employee ID content control
  created with Aspose.Words
og_title: Adicionar palavra de controle de conteúdo no Word com Aspose.Words – guia
  passo a passo
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to add content control word in a Word document with Aspose.Words.
    This guide also explains how to create content control for an employee ID field.
  headline: How to add content control word in a Word document using Aspose.Words
  type: TechArticle
- description: Learn how to add content control word in a Word document with Aspose.Words.
    This guide also explains how to create content control for an employee ID field.
  name: How to add content control word in a Word document using Aspose.Words
  steps:
  - name: Open `EmployeeForm.docx` in Word.
    text: Open `EmployeeForm.docx` in Word.
  - name: Click the gray box that says **Enter ID** – it should be replaced by **12345**.
    text: Click the gray box that says **Enter ID** – it should be replaced by **12345**.
  - name: Open the **Developer** tab → **Design Mode** to see the control’s properties
      (Title = *EmployeeID*).
    text: Open the **Developer** tab → **Design Mode** to see the control’s properties
      (Title = *EmployeeID*).
  type: HowTo
tags:
- Aspose.Words
- content control
- C#
title: Como adicionar um controle de conteúdo em um documento Word usando Aspose.Words
url: /pt/net/programming-with-sdt/how-to-add-content-control-word-in-a-word-document-using-asp/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como adicionar controle de conteúdo word em um documento Word usando Aspose.Words

Se você precisa **adicionar controle de conteúdo word** a um arquivo Word, este tutorial mostra exatamente como fazer isso com a biblioteca Aspose.Words para .NET. Seja construindo um documento tipo formulário ou automatizando a inserção de dados, você aprenderá **como criar controle de conteúdo** que captura o ID de um funcionário em um único passo.

Neste guia você irá:

* Criar um documento Word em branco programaticamente.  
* Inserir uma Structured Document Tag (SDT) de texto simples que funciona como um controle de conteúdo.  
* Preencher o controle com o ID de um funcionário e salvar o arquivo.  

Os únicos pré‑requisitos são uma versão recente do .NET (recomendado 4.6+ ) e uma licença Aspose.Words (ou o teste gratuito). Nenhum pacote NuGet adicional é necessário além de `Aspose.Words`.

## Adicionar controle de conteúdo word com Aspose.Words

O primeiro passo importante é criar o próprio controle de conteúdo. No Aspose.Words um **controle de conteúdo** é representado pela classe `StructuredDocumentTag`. Ao adicionar um SDT ao documento, você está efetivamente **adicionando controle de conteúdo word** que pode ser editado posteriormente no Microsoft Word ou processado programaticamente.

```csharp
using Aspose.Words;
using Aspose.Words.Markup;

// 1️⃣ Create a new blank document and a DocumentBuilder to edit it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Por que isso importa*: `DocumentBuilder` fornece uma interface semelhante a um cursor que permite inserir nós (parágrafos, tabelas, SDTs etc.) na posição atual. Começar com um documento limpo garante que o controle de conteúdo apareça exatamente onde você pretende.

## Como criar controle de conteúdo para um campo de ID de funcionário

Em seguida, configure o SDT para atuar como um controle de conteúdo de texto simples que armazenará o identificador do funcionário. A propriedade `Title` é o que o Word mostra no painel de **Propriedades**, enquanto `PlaceholderName` fornece uma dica ao usuário.

```csharp
// 2️⃣ Create a plain‑text Structured Document Tag (SDT) and set its metadata
StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PlainText, true);
sdt.Title = "EmployeeID";            // Visible title in Word's UI
sdt.PlaceholderName = "Enter ID";    // Placeholder text shown when empty
```

*Por que isso importa*: Definir `Title` como **EmployeeID** torna o controle auto‑descritivo, o que é útil quando você extrair valores mais tarde com `StructuredDocumentTag.GetText()`. O placeholder melhora a experiência do usuário final ao indicar o formato esperado.

### Adicionar campo de ID de funcionário dentro do controle de conteúdo

Agora insira o SDT no documento na localização atual do builder e escreva o número padrão do funcionário.

```csharp
// 3️⃣ Insert the SDT into the document at the current builder position
builder.InsertNode(sdt);

// 4️⃣ Add default content inside the SDT (e.g., an employee ID)
builder.Writeln("12345");   // This text becomes the initial value of the control
```

*Por que isso importa*: `InsertNode` coloca o SDT na árvore do documento. O `Writeln` subsequente grava conteúdo **dentro** do controle porque o cursor do builder ainda está dentro do nó SDT. Se você chamar `Writeln` antes de inserir o SDT, o texto aparecerá fora do controle.

## Salvar o documento e verificar o controle de conteúdo

Finalmente, persista o documento no disco. O arquivo `.docx` salvo conterá o controle de conteúdo que você pode abrir no Microsoft Word para ver o placeholder e o ID padrão do funcionário.

```csharp
// 5️⃣ Save the document with the SDT to a file
doc.Save(@"C:\Temp\EmployeeForm.docx");
```

*Por que isso importa*: Usar um caminho absoluto ou relativo permite controlar onde o arquivo será salvo. Aspose.Words grava automaticamente as partes XML necessárias para o controle de conteúdo, portanto, nenhuma etapa extra é necessária.

### Etapas rápidas de verificação

1. Abra `EmployeeForm.docx` no Word.  
2. Clique na caixa cinza que diz **Enter ID** – ela deve ser substituída por **12345**.  
3. Abra a aba **Developer** → **Design Mode** para ver as propriedades do controle (Title = *EmployeeID*).

Se o controle não aparecer, verifique novamente se você está usando Aspose.Words ≥ 23.10; versões anteriores tinham uma assinatura de construtor diferente para `StructuredDocumentTag`.

## Variações opcionais e casos de borda

| Cenário | Como adaptar o código |
|----------|-----------------------|
| **Usar um controle rich‑text** em vez de texto simples | Altere `SdtType.PlainText` para `SdtType.RichText`. |
| **Adicionar o controle a um documento existente** | Carregue o arquivo com `new Document("Existing.docx")` e posicione o builder no marcador desejado antes de inserir o SDT. |
| **Bloquear o controle de conteúdo para que os usuários não possam editar o valor** | Defina `sdt.LockContentControl = true;` após criar o SDT. |
| **Aplicar uma tag personalizada para extração posterior** | Use `sdt.Tag = "EmpIdTag";` e depois recupere-o com `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`. |
| **Definir um controle de conteúdo repetitivo (vários IDs)** | Crie o SDT dentro de uma linha de tabela e duplique a linha conforme necessário. |

**Dica profissional**: Sempre descarte o objeto `Document` (ou encapsule‑o em um bloco `using`) ao trabalhar em um serviço de longa duração para liberar recursos nativos prontamente.

## Conclusão

Agora você sabe como **adicionar controle de conteúdo word** a um documento Word usando Aspose.Words, como **criar controle de conteúdo** que captura um identificador de funcionário e como **adicionar campo de ID de funcionário** programaticamente. Seguindo os passos acima, você pode incorporar campos estruturados e editáveis em qualquer documento gerado, facilitando a coleta ou exibição de dados em um formato consistente.

Em seguida, explore tópicos relacionados como **vincular controles de conteúdo a dados XML**, **criar controles de conteúdo repetitivos para tabelas** ou **usar a API Aspose.Words para extrair valores de controles preenchidos**. Essas extensões permitem que você construa formulários Word completos e orientados a dados sem nunca abrir o arquivo manualmente. Feliz codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Adicionar conteúdo usando Document Builder no Aspose.Words para .NET](/words/english/net/add-content-using-document-builder/)
- [Adicionar um campo de formulário Combo Box a um documento Word com Aspose.Words para .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Adicionar um campo de formulário Check Box a um documento Word com Aspose.Words para .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}