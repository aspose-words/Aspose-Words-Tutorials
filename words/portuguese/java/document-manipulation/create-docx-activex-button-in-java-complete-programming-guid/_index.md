---
category: general
date: 2026-08-14
description: Crie um botão ActiveX em docx usando Java com Aspose.Words. Aprenda como
  adicionar um botão de formulário no Word programaticamente e salvar o documento.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create docx ActiveX button
- add form button word
language: pt
lastmod: 2026-08-14
og_description: Crie um botão ActiveX em docx usando Java e Aspose.Words. Este guia
  mostra como adicionar um botão de formulário no Word, configurá‑lo e salvar o arquivo.
og_image_alt: Screenshot of a Word document containing an ActiveX CommandButton created
  with Java
og_title: Criar botão ActiveX docx em Java – tutorial passo a passo
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Create docx ActiveX button in Java with Aspose.Words. Learn how to
    add a form button in Word programmatically and save the document.
  headline: Create docx ActiveX button in Java – complete programming guide
  type: TechArticle
- description: Create docx ActiveX button in Java with Aspose.Words. Learn how to
    add a form button in Word programmatically and save the document.
  name: Create docx ActiveX button in Java – complete programming guide
  steps:
  - name: Set up the project and import Aspose.Words
    text: 'Add the Aspose.Words dependency to your `pom.xml` if you use Maven:'
  - name: Create a new blank document
    text: Instantiate a `Document` object, which represents an empty Word file ready
      to receive content.
  - name: Initialize a DocumentBuilder
    text: '`DocumentBuilder` provides a fluent interface for inserting text, images,
      and controls. Attach it to the document you just created.'
  - name: Insert an ActiveX CommandButton control
    text: Use the `insertForms2OleControl` method to embed an ActiveX `CommandButton`.
      This method returns a `Forms2OleControl` instance that you can further configure.
  - name: Configure the button’s properties
    text: Set the control’s name, caption, and layout attributes. These values determine
      how the button appears in Word and how you can reference it later via VBA or
      automation scripts.
  - name: Save the document
    text: Finally, write the document to disk. Use the `.docx` extension to keep the
      file in the modern Office Open XML format.
  type: HowTo
tags:
- ActiveX
- Java
- Aspose.Words
- Word automation
title: Criar botão ActiveX docx em Java – guia completo de programação
url: /pt/java/document-manipulation/create-docx-activex-button-in-java-complete-programming-guid/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar botão ActiveX docx em Java – guia completo de programação

Se você precisa **criar botão ActiveX docx** em Java, este guia o conduzirá por todo o processo. Você verá como adicionar um botão de formulário no Word, configurar suas propriedades e gerar um arquivo .docx pronto‑para‑uso.

Trabalhar com controles ActiveX é uma necessidade comum ao automatizar formulários Word legados. Neste tutorial, você aprenderá a **adicionar botão de formulário word** em documentos usando a biblioteca Aspose.Words for Java, para que possa incorporar controles interativos sem edição manual.

## O que você precisará

* Java 17 ou superior (o código compila com versões anteriores, mas Java 17 é recomendado).
* Aspose.Words for Java 23.10 ou mais recente – faça o download do JAR no site da Aspose ou adicione a dependência Maven.
* Uma IDE (IntelliJ IDEA, Eclipse ou VS Code) ou um editor de texto simples e ferramentas de compilação via linha de comando.
* Conhecimento básico de sintaxe Java e programação orientada a objetos.

## Como criar botão ActiveX docx com Aspose.Words

Os passos a seguir mostram a sequência exata necessária para **criar botão ActiveX docx** objetos e incorporá‑los em um documento Word.

### Etapa 1: Configurar o projeto e importar Aspose.Words

Add the Aspose.Words dependency to your `pom.xml` if you use Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
    <classifier>jdk17</classifier>
</dependency>
```

Or, if you prefer Gradle:

```gradle
implementation 'com.aspose:aspose-words:23.10:jdk17'
```

After the dependency resolves, import the required classes in your Java source file:

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.Forms2OleControlType;
```

Essas importações dão acesso a `Document`, `DocumentBuilder` e à API `Forms2OleControl` usada para inserir controles ActiveX.

### Etapa 2: Criar um novo documento em branco

Instantiate a `Document` object, which represents an empty Word file ready to receive content.

```java
// Step 2: Create a new blank document
Document document = new Document();
```

Criar o documento primeiro garante que o construtor subsequente opere sobre uma tela limpa.

### Etapa 3: Inicializar um DocumentBuilder

`DocumentBuilder` provides a fluent interface for inserting text, images, and controls. Attach it to the document you just created.

```java
// Step 3: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(document);
```

O builder rastreia a posição atual do cursor dentro do documento, de modo que a próxima inserção ocorra exatamente onde você precisa.

### Etapa 4: Inserir um controle ActiveX CommandButton

Use the `insertForms2OleControl` method to embed an ActiveX `CommandButton`. This method returns a `Forms2OleControl` instance that you can further configure.

```java
// Step 4: Insert an ActiveX CommandButton control into the document
Forms2OleControl commandButton = builder.insertForms2OleControl(
        Forms2OleControlType.COMMAND_BUTTON);
```

Neste ponto o arquivo .docx contém um espaço reservado para um botão, mas ainda não possui legenda visual ou tamanho.

### Etapa 5: Configurar as propriedades do botão

Set the control’s name, caption, and layout attributes. These values determine how the button appears in Word and how you can reference it later via VBA or automation scripts.

```java
// Step 5: Configure the button's properties (name, caption, size, and position)
commandButton.setName("btnSubmit");          // internal name used by VBA
commandButton.setCaption("Submit");          // text shown on the button
commandButton.setTop(100);                  // distance from the top of the page (points)
commandButton.setLeft(150);                 // distance from the left margin (points)
commandButton.setWidth(80);                 // button width (points)
commandButton.setHeight(30);                // button height (points)
```

> **Dica profissional:** O Word mede posições em pontos (1 pt ≈ 1/72 pol). Ajuste `setTop` e `setLeft` para alinhar o botão com o conteúdo ao redor.

### Etapa 6: Salvar o documento

Finally, write the document to disk. Use the `.docx` extension to keep the file in the modern Office Open XML format.

```java
// Step 6: Save the document containing the ActiveX button
String outputPath = "C:/temp/ActiveXButton.docx";
document.save(outputPath);
System.out.println("Document saved to " + outputPath);
```

Ao abrir o arquivo resultante no Microsoft Word, você verá um botão **Submit** posicionado nas coordenadas especificadas. Clicar no botão no Word não acionará nenhuma ação a menos que você anexe código VBA, mas o controle está totalmente funcional para fluxos de trabalho baseados em formulários.

## Perguntas comuns e casos extremos

| Pergunta | Resposta |
|----------|----------|
| **Preciso de uma versão especial do Word?** | Os controles ActiveX são suportados na versão desktop do Microsoft Word no Windows. Não estão disponíveis no Word para Mac ou no Word Online. |
| **Posso usar isso com arquivos `.doc`?** | Sim. Salve o documento com a extensão `.doc` (`document.save("ActiveXButton.doc")`). A mesma API funciona para o formato binário mais antigo. |
| **E se o botão não aparecer?** | Certifique‑se de que **File → Options → Trust Center → Trust Center Settings → ActiveX Settings** permite controles ActiveX. Também verifique se o documento não está aberto em “Protected View”. |
| **Posso adicionar outros controles ActiveX?** | Absolutamente. Substitua `Forms2OleControlType.COMMAND_BUTTON` por `Forms2OleControlType.CHECK_BOX`, `RADIO_BUTTON`, etc. |
| **Existe um limite de tamanho?** | O tamanho do controle é limitado apenas pelo layout da página. Dimensões muito grandes podem causar estouro de layout. |

## Exemplo completo e executável

A seguir está uma classe Java completa que você pode copiar, compilar e executar. Ela inclui todas as importações, o método main e comentários inline para clareza.

```java
package com.example.wordactive;

import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.Forms2OleControlType;

public class ActiveXButtonDemo {
    public static void main(String[] args) {
        try {
            // Create a new blank document
            Document document = new Document();

            // Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(document);

            // Insert an ActiveX CommandButton control
            Forms2OleControl commandButton = builder.insertForms2OleControl(
                    Forms2OleControlType.COMMAND_BUTTON);

            // Configure button properties
            commandButton.setName("btnSubmit");
            commandButton.setCaption("Submit");
            commandButton.setTop(100);   // points from top
            commandButton.setLeft(150);  // points from left
            commandButton.setWidth(80);  // width in points
            commandButton.setHeight(30); // height in points

            // Save the document
            String outputPath = "ActiveXButton.docx";
            document.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Resultado esperado:** Após executar o programa, `ActiveXButton.docx` aparece no diretório de trabalho. Ao abri‑lo no Microsoft Word, ele mostra um botão **Submit** clicável posicionado próximo ao canto superior‑esquerdo da primeira página.

## Conclusão

Agora você sabe como **criar botão ActiveX docx** objetos em Java usando Aspose.Words, e viu como **adicionar botão de formulário word** documentos programaticamente. As etapas — configurar o projeto, criar um documento, inserir o controle, configurar suas propriedades e salvar — cobrem todo o fluxo de trabalho do início ao fim.

Em seguida, você pode explorar:

* Adicionar macros VBA que respondam ao clique do botão.
* Incorporar outros controles ActiveX como caixas de seleção ou caixas de lista.
* Automatizar a geração de formulários de várias páginas com vários elementos interativos.

Sinta‑se à vontade para experimentar tamanhos, posições e legendas para atender aos requisitos específicos do seu design de formulário. Feliz codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Como criar campos de formulário e adicionar conteúdo usando DocumentBuilder no Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Como carregar HTML e salvar como DOCX usando Aspose.Words for Java](/words/english/java/document-loading-and-saving/loading-and-saving-html-documents/)
- [Como criar documentos PDF com Aspose.Words for Java | API de Processamento de Documentos](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}