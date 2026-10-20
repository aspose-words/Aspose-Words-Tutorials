---
category: general
date: 2026-10-20
description: Crie um DOCX em branco programaticamente e incorpore um botão de comando
  usando Java. Aprenda o código completo para criar um documento Word, salvar o Word
  com o botão e definir a legenda do botão de comando.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank docx programmatically
- create word document code
- save word with button
- add command button word
- set command button caption
language: pt
lastmod: 2026-10-20
og_description: Crie um DOCX em branco programaticamente e incorpore um botão de comando.
  Siga este guia passo a passo em Java para salvar o Word com o botão e definir a
  legenda do botão de comando.
og_image_alt: Screenshot of a blank DOCX file with an inserted command button created
  programmatically
og_title: Criar um DOCX em branco programaticamente – adicionar um botão de comando
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create a blank DOCX programmatically and embed a command button using
    Java. Learn the full create word document code to save Word with button and set
    command button caption.
  headline: Create a blank DOCX programmatically and add a command button
  type: TechArticle
- description: Create a blank DOCX programmatically and embed a command button using
    Java. Learn the full create word document code to save Word with button and set
    command button caption.
  name: Create a blank DOCX programmatically and add a command button
  steps:
  - name: Initialize a new blank document
    text: A blank document is the canvas on which you’ll place the command button.
      Aspose.Words provides the `Document` class for this purpose.
  - name: Set up a `DocumentBuilder`
    text: '`DocumentBuilder` is a helper that lets you insert content, including OLE
      controls, without dealing with low‑level node manipulation.'
  - name: Insert an OLE command button
    text: Word treats interactive controls as OLE (Object Linking and Embedding) objects.
      Aspose.Words exposes `Forms2OleControl` for this.
  - name: Configure the button – type, caption, and location
    text: You must define the control’s type (`COMMANDBUTTON`), set a user‑visible
      caption, and place it on the page.
  - name: Save the document with the embedded button
    text: Finally, write the file to disk. The resulting file can be opened in Microsoft
      Word, where the button will be fully functional.
  - name: Expected result
    text: 'When you open `CommandButton.docx` in Microsoft Word:'
  type: HowTo
tags:
- Java
- DOCX
- Aspose.Words
- Command button
- Automation
title: Criar um DOCX em branco programaticamente e adicionar um botão de comando
url: /pt/java/document-manipulation/create-a-blank-docx-programmatically-and-add-a-command-butto/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar um DOCX em branco programaticamente e adicionar um botão de comando

Se você precisar **criar um blank DOCX programmatically**, este tutorial mostra como incorporar um botão de comando diretamente no arquivo. Você obterá o código completo *create word document code* que salva um documento Word com um botão, permite que você **set command button caption**, e funciona com a versão mais recente da biblioteca Aspose.Words for Java.

Incorporar controles interativos em um arquivo DOCX é útil quando você deseja distribuir modelos que acionam macros, iniciam programas externos ou simplesmente orientam os usuários com um botão clicável “Click Me”. As etapas abaixo cobrem tudo, desde a inicialização de um documento em branco até a persistência do arquivo final no disco.

## Pré-requisitos

* Java 17 ou mais recente instalado.
* Maven (ou sua ferramenta de construção preferida) para gerenciar dependências.
* Aspose.Words for Java 23.9 ou posterior. Adicione a dependência ao seu `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

* Uma IDE como IntelliJ IDEA ou VS Code (qualquer editor que suporte Java funciona).

## Criar um DOCX em branco programaticamente – passo a passo

As seções a seguir dividem o processo em etapas claras e numeradas. Cada etapa explica **por que** é necessária, não apenas **o que** digitar.

### Etapa 1: Inicializar um novo documento em branco

Um documento em branco é a tela onde você colocará o botão de comando. Aspose.Words fornece a classe `Document` para esse propósito.

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();
```

*Por que isso importa*: Começar com um `Document` vazio garante que nenhuma formatação oculta ou controles existentes interfiram no botão que você adicionará posteriormente.

### Etapa 2: Configurar um `DocumentBuilder`

`DocumentBuilder` é um auxiliar que permite inserir conteúdo, incluindo controles OLE, sem lidar com manipulação de nós de baixo nível.

```java
        // Step 2: Initialize a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Por que isso importa*: O builder mantém a posição atual do cursor, portanto o botão será colocado exatamente onde você especificar.

### Etapa 3: Inserir um botão de comando OLE

O Word trata controles interativos como objetos OLE (Object Linking and Embedding). Aspose.Words expõe `Forms2OleControl` para isso.

```java
        // Step 3: Insert an OLE command button into the document
        com.aspose.words.forms.Forms2OleControl commandButton = builder.insertForms2OleControl();
```

*Por que isso importa*: Inserir o controle cria um espaço reservado que você pode configurar posteriormente (tipo, legenda, posição).

### Etapa 4: Configurar o botão – tipo, legenda e localização

Você deve definir o tipo do controle (`COMMANDBUTTON`), definir uma legenda visível ao usuário e posicioná-lo na página.

```java
        // Step 4: Configure the command button's type, caption, and position
        commandButton.setOleControlType(com.aspose.words.forms.OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");               // set command button caption
        commandButton.setLeft(100);                         // distance from the left margin (points)
        commandButton.setTop(200);                          // distance from the top margin (points)
```

*Por que isso importa*:  
* **Type** informa ao Word que o controle se comporta como um botão clicável.  
* **Caption** é o texto que o usuário vê; alterá‑lo é como você **set command button caption**.  
* **Left** e **Top** controlam o posicionamento exato, o que é essencial quando você **add command button word** documentos que precisam de layout preciso.

### Etapa 5: Salvar o documento com o botão incorporado

Finalmente, escreva o arquivo no disco. O arquivo resultante pode ser aberto no Microsoft Word, onde o botão estará totalmente funcional.

```java
        // Step 5: Save the document with the embedded command button
        String outputPath = "YOUR_DIRECTORY/CommandButton.docx";
        document.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

*Por que isso importa*: Esta etapa **saves Word with button** para que o controle persista entre máquinas. O arquivo pode ser distribuído como um modelo ou usado em pipelines automatizados de geração de relatórios.

## Exemplo completo em funcionamento

Copie a classe inteira abaixo para um arquivo chamado `CommandButtonDemo.java`, ajuste `YOUR_DIRECTORY` para um caminho real e execute‑lo com `mvn compile exec:java`.

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.OleControlType;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document document = new Document();

        // Initialize a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert an OLE command button into the document
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Configure the command button
        commandButton.setOleControlType(OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");   // set command button caption
        commandButton.setLeft(100);             // points from left margin
        commandButton.setTop(200);              // points from top margin

        // Save the document with the embedded command button
        String outputPath = "YOUR_DIRECTORY/CommandButton.docx";
        document.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

### Resultado esperado

Quando você abrir `CommandButton.docx` no Microsoft Word:

* O documento está completamente em branco, exceto por um botão rotulado **Click Me**.
* Clicar no botão exibirá o comportamento padrão do Word (não faz nada a menos que uma macro esteja anexada), confirmando que o controle OLE foi incorporado corretamente.

## Perguntas comuns & casos extremos

| Pergunta | Resposta |
|----------|----------|
| **Posso mudar o tamanho do botão?** | Sim. Use `commandButton.setWidth(double)` e `commandButton.setHeight(double)` para ajustar as dimensões em pontos. |
| **E se eu precisar de uma macro anexada ao botão?** | O próprio botão é apenas um controle OLE. Você deve adicionar uma macro VBA ao documento manualmente ou via as utilidades `addMacro` da API `Document` do Aspose.Words. |
| **O botão funcionará no LibreOffice?** | O LibreOffice oferece suporte limitado a controles OLE. O botão aparece, mas seu comportamento ao clicar pode ser diferente. |
| **Como adicionar vários botões?** | Repita as Etapas 3‑4 com uma nova instância de `Forms2OleControl`. Ajuste `setLeft`/`setTop` para cada botão para evitar sobreposição. |
| **O código é compatível com .NET?** | A mesma lógica se aplica, mas você usaria as classes do `Aspose.Words` para .NET (`Document`, `DocumentBuilder`, `Forms2OleControl`). |

## Dicas do campo

* **Dica profissional:** Use `builder.moveToDocumentEnd()` antes de inserir o botão se você quiser que ele fique no final do documento, independentemente do conteúdo anterior.
* **Cuidado:** Valores muito pequenos de `Left`/`Top` podem posicionar o botão fora da área imprimível, tornando‑o invisível na visualização de layout do Word.
* **Nota de desempenho:** Inserir muitos controles OLE pode aumentar o tamanho do arquivo. Se você precisar apenas de um indicativo visual, considere usar um `Shape` simples com um hyperlink.

## Conclusão

Agora você sabe como **create a blank DOCX programmatically** e incorporar um botão de comando totalmente funcional usando Java. O tutorial cobriu todo o fluxo de trabalho *create word document code*, demonstrou como **save Word with button**, mostrou a maneira correta de **add command button word** elementos, e explicou como **set command button caption**.

A partir daqui você pode:

* Adicionar mais controles OLE (caixas de seleção, caixas de combinação) para formulários mais ricos.
* Anexar macros VBA para fazer o botão executar ações personalizadas.
* Combinar esta técnica com mesclagem de documentos (mail‑merge) para modelos dinâmicos e interativos.

Sinta‑se à vontade para experimentar estilos de botão, posições e controles adicionais para atender aos requisitos específicos do seu negócio. Feliz codificação

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Create blank word document with a command button – step‑by‑step guide](/words/english/java/using-document-elements/create-blank-word-document-with-a-command-button-step-by-ste/)
- [How to Insert ActiveX Button in Word – Set Button Caption](/words/english/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/)
- [Create Blank Word Document with Java – Full Aspose.Words Guide](/words/english/java/document-loading-and-saving/create-blank-word-document-with-java-full-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}