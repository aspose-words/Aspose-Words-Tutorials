---
category: general
date: 2026-10-04
description: Aprenda como inicializar o DocumentBuilder para um novo documento e adicionar
  um botão ActiveX com Aspose.Words em Java. Guia passo a passo com código completo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- initialize DocumentBuilder for new document
- insert ActiveX button
- Forms2OleControl command button
- Aspose.Words DocumentBuilder example
- create Word document with ActiveX
language: pt
lastmod: 2026-10-04
og_description: Inicialize o DocumentBuilder para um novo documento e incorpore um
  botão de comando ActiveX usando a API Aspose.Words Java. Siga este tutorial conciso.
og_image_alt: Screenshot showing DocumentBuilder initialized for a new document with
  an ActiveX button
og_title: Inicializar DocumentBuilder para novo documento – guia completo do Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to initialize DocumentBuilder for new document and add an
    ActiveX button with Aspose.Words in Java. Step‑by‑step guide with full code.
  headline: How to initialize DocumentBuilder for new document using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- Java
- DocumentBuilder
- ActiveX
title: Como inicializar DocumentBuilder para um novo documento usando Aspose.Words
url: /pt/java/using-document-elements/how-to-initialize-documentbuilder-for-new-document-using-asp/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como inicializar DocumentBuilder para novo documento usando Aspose.Words

Se você precisar **inicializar DocumentBuilder para novo documento** em um projeto Java, este tutorial mostra as etapas exatas. Você verá como criar um arquivo Word em branco, anexar um botão de comando ActiveX e salvar o resultado — tudo com um único exemplo de código autônomo.

Trabalhar programaticamente com documentos Word costuma envolver detalhes de baixo nível, como controles de formulário. Ao final deste guia, você será capaz de incorporar um botão ActiveX sem sair da sua IDE, o que é útil para gerar modelos, relatórios automatizados ou formulários interativos.

## Pré-requisitos

Antes de começar, certifique‑se de que você tem:

* Java 17 ou posterior instalado  
* Maven 3.8+ (ou Gradle, se preferir)  
* Uma licença do Aspose.Words for Java (a versão de avaliação gratuita funciona para testes)  
* Familiaridade básica com a sintaxe Java  

Se você é novo no Aspose.Words, a biblioteca fornece uma API de alto nível para criar, editar e salvar documentos Word. A classe `DocumentBuilder` é o ponto de entrada principal para construir o conteúdo do documento.

## Etapa 1: Configurar o projeto Maven

Crie um novo projeto Maven (ou adicione a um existente) e inclua a dependência do Aspose.Words:

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>activex-demo</artifactId>
    <version>1.0.0</version>
    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- Use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

> **Dica profissional:** Mantenha a versão da biblioteca atualizada; lançamentos mais recentes adicionam suporte a controles de formulário adicionais e melhoram o desempenho.

## Etapa 2: Inicializar `DocumentBuilder` para novo documento

O núcleo do tutorial é a operação **inicializar DocumentBuilder para novo documento**. Primeiro você cria uma instância vazia de `Document`, depois a passa ao construtor de `DocumentBuilder`.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a new empty document
        Document doc = new Document();

        // Step 2.2: Initialize DocumentBuilder for new document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Por que isso importa:* Inicializar `DocumentBuilder` vincula o builder a um objeto `Document` específico, permitindo que você adicione parágrafos, tabelas ou controles de formulário diretamente a esse documento. Sem essa etapa, o builder não teria nenhum alvo para trabalhar.

## Etapa 3: Inserir um controle de botão de comando ActiveX

Aspose.Words expõe a classe `Forms2OleControl` para incorporar controles ActiveX legados. O código a seguir adiciona um **botão de comando Forms2OleControl** na posição atual do cursor.

```java
        // Step 3.1: Insert an ActiveX command button control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 3.2: Set the button caption (the text displayed on the button)
        commandButton.setCaption("Click Me");
```

### O que é um botão de comando ActiveX?

Um botão de comando ActiveX é um elemento de UI legado que pode executar macros ou disparar eventos quando o usuário clica nele dentro de um documento Word. Embora versões modernas do Office favoreçam Content Controls, muitos modelos corporativos ainda dependem de ActiveX por compatibilidade retroativa.

## Etapa 4: Salvar o documento

Depois de inserir o controle, basta chamar `save`. O arquivo conterá o botão ActiveX e poderá ser aberto no Microsoft Word.

```java
        // Step 4: Save the document containing the ActiveX button
        String outputPath = "output/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Ao abrir `ActiveXButton.docx` no Word, você verá um botão rotulado **Click Me**. Clicar no botão não fará nada a menos que você anexe uma macro, mas o controle em si está totalmente funcional.

## Exemplo completo e executável

Abaixo está o programa completo que você pode copiar‑colar em `src/main/java/com/example/ActiveXButtonDemo.java`. Ele inclui todas as importações e tratamento de erros necessários para um teste rápido.

```java
package com.example;

import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) {
        try {
            // Step 1: Create a new empty document
            Document doc = new Document();

            // Step 2: Initialize DocumentBuilder for new document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Insert an ActiveX command button control
            Forms2OleControl commandButton = builder.insertForms2OleControl(
                    Forms2OleControlType.COMMANDBUTTON);
            commandButton.setCaption("Click Me");

            // Step 4: Save the document
            String outputPath = "output/ActiveXButton.docx";
            doc.save(outputPath);
            System.out.println("Document saved to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error creating document: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**Saída esperada**

```
Document saved to output/ActiveXButton.docx
```

Abra o arquivo gerado no Microsoft Word 2016 ou posterior; você deverá ver um botão rotulado *Click Me* posicionado no topo da primeira página.

## Variações comuns e casos de borda

| Cenário | Ajuste |
|----------|------------|
| **Adicionar o botão a um parágrafo específico** | Mova o cursor do builder com `builder.moveToParagraph(index, NodeType.PARAGRAPH);` antes de chamar `insertForms2OleControl`. |
| **Definir o tamanho do botão** | Use `commandButton.setWidth(100);` e `commandButton.setHeight(30);` para definir as dimensões em pontos. |
| **Adicionar uma macro ao botão** | Depois de salvar o documento, abra‑o no Word, habilite a guia Desenvolvedor e anexe manualmente uma macro VBA ao botão (controles ActiveX não podem ser scriptados diretamente pelo Aspose.Words). |
| **Alvo formato .doc (binário)** | Altere `doc.save(outputPath, SaveFormat.DOC);` para gerar um arquivo Word 97‑2003 legado. |
| **Executar no Android** | Use Aspose.Words para Android via sua API Java; o mesmo código funciona enquanto a biblioteca estiver incluída no APK. |

## Dicas de solução de problemas

* **`java.lang.NoClassDefFoundError`** – Certifique‑se de que o JAR do Aspose.Words está no classpath. O Maven o adiciona automaticamente; para compilações manuais, coloque o JAR em `libs/` e adicione‑o às bibliotecas do seu IDE.  
* **Button does not appear in Word** – Verifique se a opção *Show legacy forms* está habilitada no Centro de Confiabilidade do Word (`File → Options → Trust Center → Trust Center Settings → Macro Settings`).  
* **License exception** – Se você executar o código sem uma licença válida, o Aspose.Words inserirá uma marca d'água. Registre uma avaliação gratuita ou adquira uma licença para removê‑la.

## Conclusão

Agora você sabe como **inicializar DocumentBuilder para novo documento**, inserir um botão de comando ActiveX e salvar o resultado com Aspose.Words para Java. Esse padrão permite gerar modelos Word interativos programaticamente, o que é especialmente útil para relatórios automatizados ou fluxos de trabalho baseados em formulários.

A partir daqui, você pode explorar controles de formulário adicionais (`Forms2OleControlType.CHECKBOX`, `COMBOBOX`, etc.), combinar o botão com macros VBA personalizadas ou gerar documentos completos que incluam tabelas, imagens e estilos — tudo usando o mesmo fluxo de trabalho do `DocumentBuilder`.

---

*Pronto para criar automações Word mais complexas? Confira nossos guias sobre **insert table with DocumentBuilder**, **apply styles programmatically** e **export to PDF with Aspose.Words**.*

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Como criar campos de formulário e adicionar conteúdo usando DocumentBuilder no Aspose.Words para Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Como salvar documento como PDF com Aspose.Words para Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Adicionar marca d'água a um documento usando Aspose.Words para Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}