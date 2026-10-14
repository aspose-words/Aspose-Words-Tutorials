---
category: general
date: 2026-10-13
description: Crie um botão de campo de formulário no Word usando Aspose.Words para
  Java. Aprenda como inserir campos de formulário de botão de comando no Word e definir
  a legenda do botão de comando em alguns passos simples.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create form field button
- insert command button word
- set command button caption
language: pt
lastmod: 2026-10-13
og_description: Crie um botão de campo de formulário no Word com Aspose.Words para
  Java. Este tutorial mostra como inserir campos de botão de comando no Word e definir
  a legenda do botão de comando rapidamente.
og_image_alt: Screenshot of a Word document containing an inserted command button
  form field created with Aspose.Words Java
og_title: Criar botão de campo de formulário no Word – Guia Aspose.Words Java
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Create form field button in Word using Aspose.Words for Java. Learn
    how to insert command button word form fields and set command button caption in
    a few easy steps.
  headline: Create form field button in Word with Aspose.Words Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Criar botão de campo de formulário no Word com Aspose.Words Java
url: /pt/java/using-document-elements/create-form-field-button-in-word-with-aspose-words-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar botão de campo de formulário no Word com Aspose.Words Java

Se você precisa **create form field button** em um documento Word, este guia o conduz pelo processo completo usando Aspose.Words for Java. Seja construindo um modelo de formulário preenchível ou adicionando controles interativos a um relatório, você aprenderá como **insert command button word** campos de formulário e **set command button caption** com código mínimo.

O tutorial cobre tudo, desde a configuração do Maven até um exemplo totalmente executável, para que você possa copiar‑colar o código, executá‑lo e ver um arquivo `.docx` que contém um botão clicável pronto para personalização adicional.

## Pré-requisitos

- Java 17 (ou mais recente) instalado e configurado em sua máquina.
- Maven 3.6+ para gerenciamento de dependências.
- Uma IDE ou editor de texto de sua escolha (por exemplo, IntelliJ IDEA, VS Code).
- Uma licença válida do Aspose.Words for Java (a avaliação gratuita funciona para avaliação).

## Etapa 1: Adicionar Aspose.Words ao seu projeto Maven

Crie um `pom.xml` (ou edite o existente) e inclua a dependência do Aspose.Words:

```xml
<dependencies>
    <dependency>
        <groupId>com.aspose</groupId>
        <artifactId>aspose-words</artifactId>
        <version>24.9</version> <!-- Use the latest version available -->
    </dependency>
</dependencies>
```

> **Dica profissional:** Mantenha o número da versão atualizado. Novas versões adicionam suporte aos recursos mais recentes do Word e melhoram o desempenho.

## Etapa 2: Inicializar um documento em branco e um `DocumentBuilder`

A classe `DocumentBuilder` fornece uma API fluente para editar um documento Word. Nesta etapa, criamos um `Document` vazio e anexamos um builder a ele.

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // DocumentBuilder lets us add content programmatically
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Criar o documento é a base para os objetos **create form field button** mais adiante no tutorial.

## Etapa 3: Inserir um campo de formulário de botão de comando

Aspose.Words expõe a classe `Forms2OleControl` para controles de formulário OLE. Para **insert command button word** campos de formulário, chame `insertForms2OleControl` com o valor enum `COMMANDBUTTON`.

```java
        // Insert a Command Button form field at the current cursor position
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);
```

O método retorna uma instância `Forms2OleControl` que podemos configurar antes de salvar.

## Etapa 4: Definir tamanho e posição do botão

Um botão de comando precisa de dimensões e posicionamento explícitos na página. Ajuste a largura, altura e coordenadas de acordo com seu layout.

```java
        // Set the button's visual size (in points)
        commandButton.setWidth(120);   // 120 points ≈ 1.67 inches
        commandButton.setHeight(30);   // 30 points ≈ 0.42 inches

        // Position the button relative to the page margins
        commandButton.setLeft(50);   // 50 points from the left margin
        commandButton.setTop(100);   // 100 points from the top margin
```

Ajustar finamente esses valores garante que o botão apareça exatamente onde você deseja no documento final.

## Etapa 5: **Set command button caption**

O texto visível no botão é controlado pelo método `setCaption`. É aqui que **set command button caption** para orientar o usuário.

```java
        // Define the text that appears on the button
        commandButton.setCaption("Click Me");
```

Você pode substituir `"Click Me"` por qualquer rótulo que corresponda à intenção do seu formulário, como `"Submit"` ou `"Approve"`.

## Etapa 6: Salvar o documento

Finalmente, grave o documento no disco. O arquivo resultante contém o botão interativo e pode ser aberto no Microsoft Word ou no LibreOffice.

```java
        // Save the document with the embedded command button
        doc.save("CommandButtonDemo.docx");
    }
}
```

Executar o programa produz `CommandButtonDemo.docx`. Abrindo‑o no Word, você vê um botão rotulado **Click Me** posicionado 50 pts da esquerda e 100 pts do topo da página.

### Saída esperada

- Um arquivo `.docx` chamado `CommandButtonDemo.docx`.
- O documento contém uma única página com um campo de formulário de botão de comando.
- O botão exibe a legenda que você definiu (por exemplo, **Click Me**).

## Variações comuns e casos extremos

| Situação | Como adaptar |
|-----------|--------------|
| **Multiple buttons** | Chame `insertForms2OleControl` repetidamente, ajustando `setLeft`/`setTop` para cada novo botão. |
| **Different caption per button** | Use `setCaption` com uma string única após cada inserção. |
| **Button inside a table cell** | Mova o cursor para a célula desejada com `builder.moveTo(cell.getFirstParagraph())` antes de inserir o controle. |
| **Legacy Word formats (.doc)** | Salve usando `doc.save("Demo.doc", SaveFormat.DOC);` – o botão de comando é preservado. |
| **Read‑only forms** | Após a inserção, defina `commandButton.setEnabled(false);` para impedir a interação do usuário. |

## Dicas para uma implementação robusta

- **Validate dimensions**: Larguras extremamente grandes podem fazer o botão transbordar a margem da página.
- **License enforcement**: Sem uma licença válida, Aspose.Words adiciona uma marca d'água ao documento gerado. Aplique sua licença cedo com `License license = new License(); license.setLicense("Aspose.Words.lic");`.
- **Testing**: Abra o arquivo gerado no Word e alterne **Design Mode** (Developer → Design Mode) para ver as propriedades do botão.

## Recapitulação do código-fonte completo

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a Command Button form field
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 3: Define the button's size and position on the page
        commandButton.setWidth(120);
        commandButton.setHeight(30);
        commandButton.setLeft(50);
        commandButton.setTop(100);

        // Step 4: Set the text that appears on the button
        commandButton.setCaption("Click Me");

        // Step 5: Save the document with the embedded command button
        doc.save("CommandButtonDemo.docx");
    }
}
```

Copie o código para um arquivo chamado `InsertCommandButtonDemo.java`, compile com Maven (`mvn compile`) e execute (`mvn exec:java -Dexec.mainClass=InsertCommandButtonDemo`). O documento gerado aparecerá na pasta raiz do seu projeto.

## Conclusão

Agora você sabe como **create form field button** no Word usando Aspose.Words for Java, como **insert command button word** campos de formulário e como **set command button caption** programaticamente. Este exemplo completo fornece uma base sólida para criar documentos Word mais ricos e interativos — seja você precisar de um único botão de envio ou de um conjunto completo de controles de formulário.

### O que vem a seguir?

- [Como criar campos de formulário e adicionar conteúdo usando DocumentBuilder no Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Adicionar um campo de formulário Combo Box a um documento Word com Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Adicionar um campo de formulário Check Box a um documento Word com Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}