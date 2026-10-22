---
category: general
date: 2026-09-05
description: Criar documento Word com Aspose.Words, definir texto de espaço reservado,
  adicionar controle e salvar o documento como docx em C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- set placeholder text
- save document as docx
- how to add control
- how to create tag
language: pt
lastmod: 2026-09-05
og_description: Crie um documento Word usando Aspose.Words para .NET, defina texto
  de espaço reservado, adicione controle e salve o documento como docx. Siga este
  tutorial completo.
og_image_alt: Screenshot showing a word document created with a content control placeholder
og_title: Criar um documento Word com controles de conteúdo em C# – guia passo a passo
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create word document with Aspose.Words, set placeholder text, add control,
    and save document as docx in C#.
  headline: How to create word document with content controls in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Content Control
- Document Generation
title: Como criar documento Word com controles de conteúdo em C#
url: /pt/net/programming-with-sdt/how-to-create-word-document-with-content-controls-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como criar documento Word com controles de conteúdo em C#

Se você precisa **criar documento Word** que inclua controles de conteúdo estruturados, este guia mostra como adicionar uma tag de texto simples, **definir texto de espaço reservado**, e **salvar o documento como docx** usando Aspose.Words for .NET. O exemplo é totalmente executável e demonstra a abordagem recomendada para geração programática de Word.

Você aprenderá a:

* Inicializar um arquivo Word vazio com `Document` e `DocumentBuilder`.
* **Como adicionar controle** (um `StructuredDocumentTag`) ao corpo do documento.
* **Como criar tag** com um título e espaço reservado que orienta o usuário final.
* Persistir o resultado com `document.Save`, garantindo que o arquivo seja um `.docx` válido.

O tutorial pressupõe que você tenha um ambiente básico de desenvolvimento C# e uma licença para Aspose.Words (a avaliação gratuita funciona para fins de aprendizado).

---

## Pré-requisitos

| Requisito | Motivo |
|-------------|--------|
| .NET 6.0 ou posterior | Provides the runtime for Aspose.Words for .NET. |
| Pacote NuGet Aspose.Words for .NET | Supplies `Document`, `DocumentBuilder`, and `StructuredDocumentTag` classes. |
| IDE como Visual Studio 2022 | Makes it easy to run and debug the sample. |

Instale o pacote com a CLI do .NET:

```bash
dotnet add package Aspose.Words
```

---

## Etapa 1: Configurar o projeto para **criar documento Word**

Crie um novo projeto de console (ou adicione o código a um existente). As primeiras linhas instanciam um arquivo Word em branco e um `DocumentBuilder` que permite escrever conteúdo.

```csharp
using Aspose.Words;
using Aspose.Words.Markup;

// Initialize a new empty document.
Document document = new Document();

// Obtain a builder positioned at the start of the document.
DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` representa a estrutura do arquivo, enquanto `DocumentBuilder` rastreia o ponto de inserção. Esse padrão é a base para qualquer cenário de geração de Word.

---

## Etapa 2: **Como adicionar controle** – criar um controle de conteúdo de texto simples (tag)

Um controle de conteúdo no Word é chamado de *structured document tag* (SDT). O código a seguir cria um SDT de texto simples, atribui um título e define o espaço reservado que aparece quando o documento é aberto.

```csharp
// Create a plain‑text StructuredDocumentTag (SDT) at block level.
StructuredDocumentTag contentControl = new StructuredDocumentTag(
    document, SdtType.PlainText, MarkupLevel.Block);

// Assign a meaningful title – useful for later retrieval.
contentControl.Title = "CustomerName";

// Define the placeholder text that prompts the user.
contentControl.PlaceholderName = "Enter name";

// Insert the tag at the builder's current cursor location.
builder.InsertNode(contentControl);
```

**Por que isso importa:**  
* A propriedade `Title` funciona como um identificador estável, permitindo localizar ou substituir o controle programaticamente mais tarde.  
* `PlaceholderName` fornece orientação visual ao consumidor do documento sem exigir código UI adicional.

![Criar documento Word com placeholder de controle de conteúdo](image.png)

*Texto alternativo da imagem: Criar documento Word com um controle de conteúdo que mostra texto de placeholder.*

---

## Etapa 3: Mover o cursor para dentro do controle e escrever texto padrão

Após inserir o controle, o cursor do builder ainda aponta para fora dele. Mova o cursor para dentro da tag para que as gravações subsequentes façam parte do conteúdo do controle.

```csharp
// Position the builder inside the newly added content control.
builder.MoveTo(contentControl);

// Write default text that appears when the placeholder is cleared.
builder.Write("John Doe");
```

Se preferir deixar o controle vazio, omita a chamada `Write`. O placeholder permanece visível até que o usuário digite um valor.

---

## Etapa 4: **Definir texto de placeholder** (abordagem alternativa)

Às vezes é necessário alterar o placeholder após a tag ter sido criada. Você pode modificar a propriedade `PlaceholderName` diretamente:

```csharp
contentControl.PlaceholderName = "Type the customer's full name here";
```

Alterar o placeholder **não** afeta o conteúdo existente, tornando seguro atualizar dicas de UI sem alterar os dados inseridos pelo usuário.

---

## Etapa 5: **Salvar documento como docx**

Persistir o documento em memória para um arquivo físico. O método `Save` determina automaticamente o formato a partir da extensão do arquivo.

```csharp
// Save the document in DOCX format.
document.Save("YOUR_DIRECTORY/SdtExample.docx");
```

Se precisar de um formato diferente (por exemplo, PDF ou HTML), forneça um valor enum `SaveFormat`:

```csharp
document.Save("SdtExample.pdf", SaveFormat.Pdf);
```

---

## Etapa 6: Exemplo completo e executável

Juntando as peças, obtém-se um programa conciso que demonstra **como criar tag**, definir seu placeholder e **salvar o documento como docx**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // 1. Initialize document and builder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2. Create a plain‑text content control (tag).
        StructuredDocumentTag sdt = new StructuredDocumentTag(
            document, SdtType.PlainText, MarkupLevel.Block);
        sdt.Title = "CustomerName";
        sdt.PlaceholderName = "Enter name";

        // 3. Insert the control and move inside it.
        builder.InsertNode(sdt);
        builder.MoveTo(sdt);

        // 4. Write default text (optional).
        builder.Write("John Doe");

        // 5. Save the file as DOCX.
        document.Save("SdtExample.docx");
        Console.WriteLine("Word document created successfully.");
    }
}
```

**Saída esperada:**  
Executar o programa cria `SdtExample.docx` contendo um único parágrafo com um controle de conteúdo de texto simples intitulado *CustomerName*. O controle exibe “John Doe” como seu conteúdo inicial; se o texto padrão for removido, o placeholder “Enter name” aparece em cinza claro quando o arquivo é aberto no Microsoft Word.

---

## Variações comuns e casos de borda

| Cenário | Ajuste recomendado |
|----------|------------------------|
| **Múltiplos controles** | Repita as etapas 2‑4 para cada campo, atribuindo a cada um um `Title` exclusivo. |
| **Controle de rich‑text** | Use `SdtType.RichText` em vez de `PlainText`. |
| **Seção repetitiva** | Escolha `SdtType.RepeatingSection` e adicione controles filhos dentro da seção. |
| **Documento existente** | Carregue um arquivo existente com `new Document("template.docx")` e insira controles no local desejado. |
| **Placeholder Unicode** | Defina `PlaceholderName` para qualquer string Unicode; o Word a renderiza corretamente. |
| **Documentos grandes** | Descarte o `DocumentBuilder` após o uso para liberar memória (`builder.Dispose();`). |

**Dica profissional:** Quando precisar recuperar o valor inserido pelo usuário posteriormente, chame `StructuredDocumentTag.GetText()` após o documento ser salvo e reaberto. Esse método retorna o texto interno sem o placeholder.

**Cuidado:** Usar um placeholder que coincida com o texto padrão pode causar confusão, pois o Word oculta o placeholder quando há qualquer texto presente. Mantenha-os distintos.

---

## Conclusão

Agora você sabe como **criar documento Word** programaticamente, **como adicionar controle**, **como criar tag**, **definir texto de placeholder** e **salvar documento como docx** usando Aspose.Words for .NET. O exemplo completo pode ser copiado para qualquer projeto C# e estendido para suportar tipos de controle adicionais, seções repetitivas ou integração com fontes de dados.

Próximos passos que você pode explorar incluem:

* Adicionar **controles de conteúdo de imagem** (`SdtType.Picture`) para incorporar gráficos fornecidos pelo usuário.  
* Usar **binding** para mapear SDTs a dados XML para cenários de mala direta.  
* Converter o DOCX gerado para PDF (`SaveFormat.Pdf`) para distribuição.

Experimente diferentes tipos de tag e mensagens de placeholder para adequar ao fluxo de trabalho da sua aplicação. Feliz codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá-lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Criar documento Word com Aspose.Words para .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Criar um documento Word com tabela usando Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)
- [Criar documento Word com cabeçalho e rodapé usando Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}