---
category: general
date: 2026-10-04
description: Crie um documento Word usando Java que inclua um controle de conteúdo
  de texto simples e um placeholder. Aprenda como adicionar placeholder à tag e como
  inserir sdt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- plain text content control
- docx with placeholder
- add placeholder to tag
- how to insert sdt
language: pt
lastmod: 2026-10-04
og_description: Crie um documento Word com um controle de conteúdo de texto simples
  e um marcador de posição. Este tutorial mostra como adicionar o marcador de posição
  à tag e como inserir sdt usando Aspose.Words para Java.
og_image_alt: Screenshot of a generated DOCX showing a plain text content control
  with placeholder
og_title: Criar documento Word com controle de conteúdo – guia passo a passo
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Create word document using Java that includes a plain text content
    control and a placeholder. Learn how to add placeholder to tag and how to insert
    sdt.
  headline: Create word document with a plain text content control
  type: TechArticle
- description: Create word document using Java that includes a plain text content
    control and a placeholder. Learn how to add placeholder to tag and how to insert
    sdt.
  name: Create word document with a plain text content control
  steps:
  - name: Initialise the document and builder
    text: '```java import com.aspose.words.*;'
  - name: Insert a plain‑text Structured Document Tag (SDT)
    text: '```java private static void insertPlainTextControl(DocumentBuilder builder)
      throws Exception { // Step 2 – create a plain text content control (SDT) with
      a unique tag name StructuredDocumentTag sdt = builder.insertStructuredDocumentTag(
      StructuredDocumentTagType.PLAIN_TEXT, "MyTag");'
  - name: Add regular content after the SDT
    text: '```java private static void addTrailingContent(DocumentBuilder builder)
      throws Exception { // Step 3 – write a line after the SDT to prove the control
      is correctly positioned builder.writeln("After SDT"); } ```'
  - name: Save the resulting file
    text: '```java private static void saveDocument(Document doc) throws Exception
      { // Step 4 – persist the document as a DOCX with placeholder String outPath
      = "SdtDemo.docx"; doc.save(outPath); System.out.println("Document saved to "
      + outPath); } ```'
  - name: Expected output
    text: 'Running the program creates `SdtDemo.docx`. Opening the file in Word shows:'
  - name: Next steps
    text: '* Explore **how to insert sdt** inside tables for form‑like layouts. *
      Combine this technique with **docx with placeholder** merging to build automated
      report generators. * Experiment with other control types (`RICH_TEXT`, `CHECKBOX`)
      to create richer Word forms.'
  type: HowTo
tags:
- Word
- Java
- Aspose.Words
title: Criar documento do Word com um controle de conteúdo de texto simples
url: /pt/java/document-manipulation/create-word-document-with-a-plain-text-content-control/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar documento Word com um controle de conteúdo de texto simples

Se você precisa **criar documento Word** que contenha uma região editável pelo usuário, um controle de conteúdo de texto simples é a abordagem mais confiável. Este tutorial mostra exatamente como inserir uma Structured Document Tag (SDT), definir um placeholder e salvar o resultado como um **docx com placeholder**. Você verá um exemplo completo e executável em Java que funciona com Aspose.Words for Java 23.8.

O guia cobre todos os pré‑requisitos, explica por que cada chamada de API é importante e fornece dicas para lidar com casos extremos, como placeholders multilíngues ou tags aninhadas. Ao final, você poderá gerar um arquivo Word que solicita aos usuários que “Enter text…” diretamente dentro do documento.

## Pré-requisitos

Antes de começar, certifique‑se de que você tem:

* Java 17 (ou superior) instalado e configurado no seu PATH.  
* Maven 3.8+ para gerenciar dependências.  
* Uma licença do Aspose.Words for Java (avaliação funciona para testes).  
* Um IDE de desenvolvimento (IntelliJ IDEA, Eclipse ou VS Code).

Adicione o Aspose.Words ao seu `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.8</version>
</dependency>
```

## Criar documento Word com um controle de conteúdo de texto simples

O fluxo de trabalho principal consiste em quatro etapas lógicas. Cada etapa está encapsulada em um método com nome claro, para que você possa reutilizar a lógica em projetos maiores.

### Etapa 1: Inicializar o documento e o builder

```java
import com.aspose.words.*;

public class SdtDemo {
    public static void main(String[] args) throws Exception {
        // Step 1 – create an empty Document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        insertPlainTextControl(builder);
        addTrailingContent(builder);
        saveDocument(doc);
    }
}
```

**Por que isso importa:** `Document` representa o arquivo Word em memória. `DocumentBuilder` é a API fluente que permite inserir parágrafos, tabelas e SDTs. Começar com um documento vazio garante que o placeholder apareça logo no início, o que é útil para modelos.

### Etapa 2: Inserir um Structured Document Tag (SDT) de texto simples

```java
private static void insertPlainTextControl(DocumentBuilder builder) throws Exception {
    // Step 2 – create a plain text content control (SDT) with a unique tag name
    StructuredDocumentTag sdt = builder.insertStructuredDocumentTag(
            StructuredDocumentTagType.PLAIN_TEXT, "MyTag");

    // Step 2.1 – add a placeholder that appears when the tag is empty
    sdt.setPlaceholderName("Enter text…");   // add placeholder to tag
}
```

**Por que isso importa:** `StructuredDocumentTagType.PLAIN_TEXT` cria um controle de conteúdo que aceita apenas caracteres simples, evitando formatação acidental. A chamada `setPlaceholderName` preenche o texto de dica cinza que os usuários veem antes de digitar — esta é a operação **add placeholder to tag** que faz o documento parecer um formulário.

### Etapa 3: Adicionar conteúdo regular após o SDT

```java
private static void addTrailingContent(DocumentBuilder builder) throws Exception {
    // Step 3 – write a line after the SDT to prove the control is correctly positioned
    builder.writeln("After SDT");
}
```

**Por que isso importa:** Adicionar conteúdo após o controle verifica que o SDT não consome todo o fluxo do documento. Também demonstra como misturar tags estruturadas com parágrafos comuns, uma necessidade frequente ao criar modelos.

### Etapa 4: Salvar o arquivo resultante

```java
private static void saveDocument(Document doc) throws Exception {
    // Step 4 – persist the document as a DOCX with placeholder
    String outPath = "SdtDemo.docx";
    doc.save(outPath);
    System.out.println("Document saved to " + outPath);
}
```

**Por que isso importa:** O método `save` grava o modelo em memória em um arquivo físico **docx com placeholder**. O arquivo gerado pode ser aberto no Microsoft Word, LibreOffice ou em qualquer biblioteca que suporte o formato OpenXML.

## Código‑fonte completo

Juntando as peças, você obtém um programa autônomo que pode ser compilado e executado:

```java
import com.aspose.words.*;

public class SdtDemo {
    public static void main(String[] args) throws Exception {
        // Initialise document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert plain‑text content control and set placeholder
        StructuredDocumentTag sdt = builder.insertStructuredDocumentTag(
                StructuredDocumentTagType.PLAIN_TEXT, "MyTag");
        sdt.setPlaceholderName("Enter text…");   // add placeholder to tag

        // Add normal text after the control
        builder.writeln("After SDT");

        // Save the file
        String outPath = "SdtDemo.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### Saída esperada

Executar o programa cria `SdtDemo.docx`. Abrir o arquivo no Word mostra:

* Um placeholder cinza “Enter text…” dentro de um controle de conteúdo de texto simples rotulado **MyTag**.  
* A linha **After SDT** imediatamente abaixo do controle.

O placeholder desaparece assim que o usuário digita, preservando a formatação original.

## Variações comuns e casos de borda

| Cenário | Alteração recomendada |
|----------|--------------------|
| **Multilingual placeholder** | Use caracteres Unicode em `setPlaceholderName`, por exemplo, `sdt.setPlaceholderName("Введите текст…");`. |
| **Nested content controls** | Insira um segundo SDT dentro do primeiro chamando `builder.moveTo(sdt.getParagraph());` antes do segundo `insertStructuredDocumentTag`. |
| **Read‑only control** | Chame `sdt.setLockContentControl(true);` para impedir que os usuários excluam a tag. |
| **Rich‑text instead of plain text** | Substitua `StructuredDocumentTagType.PLAIN_TEXT` por `StructuredDocumentTagType.RICH_TEXT`. |
| **Saving to a stream** | Use `doc.save(OutputStream, SaveFormat.DOCX);` quando precisar enviar o arquivo via HTTP. |

## Dicas profissionais

* **Reuse tag IDs** – Se você gera muitos documentos a partir do mesmo modelo, mantenha o nome da tag (`"MyTag"`) consistente para que o processamento subsequente (por exemplo, mail‑merge) possa localizá‑la de forma confiável.  
* **Performance** – Para modelos grandes, crie o `DocumentBuilder` uma única vez e reutilize‑o; inserir muitos SDTs em um loop é mais rápido do que recriar o builder a cada iteração.  
* **Testing** – Após gerar o DOCX, verifique programaticamente se o placeholder existe com `doc.getRange().getStructuredDocumentTags().getCount()`.

## Conclusão

Agora você sabe como **criar documento Word** que contém um **controle de conteúdo de texto simples** com um placeholder personalizado, produzindo efetivamente um **docx com placeholder** pronto para a entrada do usuário. O exemplo demonstra todo o ciclo, desde a inicialização do documento, **como inserir sdt**, **adicionar placeholder to tag**, adicionar conteúdo regular e, finalmente, salvar o arquivo.

### Próximos passos

* Explore **how to insert sdt** dentro de tabelas para layouts semelhantes a formulários.  
* Combine esta técnica com a mesclagem de **docx with placeholder** para construir geradores de relatórios automatizados.  
* Experimente outros tipos de controle (`RICH_TEXT`, `CHECKBOX`) para criar formulários Word mais ricos.

Sinta‑se à vontade para adaptar o código ao seu próprio motor de templates e compartilhar seus resultados nos comentários!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Como criar campos de formulário e adicionar conteúdo usando DocumentBuilder no Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Criar documento Word Java – Adicionar forma retangular com efeito de sombra](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Como criar documentos PDF com Aspose.Words for Java | API de Processamento de Documentos](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}