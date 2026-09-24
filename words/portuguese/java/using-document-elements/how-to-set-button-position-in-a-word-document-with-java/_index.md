---
category: general
date: 2026-09-24
description: Defina a posição do botão em um documento Word usando Java e Aspose.Words.
  Aprenda como inserir o botão, adicionar controle ActiveX e criar um documento Word
  no estilo Java.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button position
- how to insert button
- add activex control
- add button to word
- create word document java
language: pt
lastmod: 2026-09-24
og_description: Defina a posição do botão em um documento Word usando Java. Este guia
  mostra como inserir um botão, adicionar um controle ActiveX e criar um documento
  Word em Java com Aspose.Words.
og_image_alt: Screenshot of a Word document showing a CommandButton positioned at
  100 px left and 150 px top
og_title: Defina a posição do botão em um documento Word com Java – guia completo
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Set button position in a Word document using Java and Aspose.Words.
    Learn how to insert button, add ActiveX control, and create Word document Java
    style.
  headline: How to set button position in a Word document with Java
  type: TechArticle
- description: Set button position in a Word document using Java and Aspose.Words.
    Learn how to insert button, add ActiveX control, and create Word document Java
    style.
  name: How to set button position in a Word document with Java
  steps:
  - name: Expected output
    text: '* A `.docx` file named **CommandButtonDemo.docx**. * Inside the document,
      a **CommandButton** labeled “Click Me” appears 100 px from the left margin and
      150 px from the top margin. * The button responds to clicks when the document
      is opened in Word (it will display a default ActiveX message unless y'
  - name: Adding multiple buttons
    text: If you need to **add button to Word** more than once, repeat steps 3‑5 with
      a new `Forms2OleControl` instance each time. Remember to adjust the `setTop`
      value so buttons don’t overlap.
  - name: Working without a license
    text: 'Aspose.Words adds a watermark when used without a license. For production
      code, purchase a license and apply it at the start of `main`:'
  - name: Compatibility with older Office versions
    text: 'ActiveX controls are supported in the `.doc` (Word 97‑2003) format. To
      create a legacy file, change the save format:'
  - name: Next steps
    text: '* Explore other `Forms2OleControl.ControlType` values (e.g., `CHECKBOX`,
      `TEXTBOX`) to build richer forms. * Combine the button with VBA macros for custom
      click handling. * Use Aspose.Words’ mail‑merge feature to generate personalized
      documents that already contain interactive controls.'
  type: HowTo
- questions:
  - answer: Yes. Aspose.Words is pure Java and runs on any JDK 8+ implementation,
      including OpenJDK.
    question: Does this work with OpenJDK?
  - answer: ActiveX button appearance is controlled by the host application (Word).
      You can attach VBA code to modify properties at runtime, but the static appearance
      is limited to the default style.
    question: Can I change the button’s font or color?
  - answer: 'Move the `DocumentBuilder` cursor into the cell before calling `insertForms2OleControl`.
      The control will inherit the cell’s layout, and you can still use `setLeft`/`setTop`
      for fine‑tuning. ## Conclusion You now know how to **set button position** in
      a Word document using Java, how to **how to inse'
    question: What if I need to place the button inside a table cell?
  type: FAQPage
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
- CommandButton
title: Como definir a posição do botão em um documento Word com Java
url: /pt/java/using-document-elements/how-to-set-button-position-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como definir a posição do botão em um documento Word com Java

Se você precisar **definir a posição do botão** dentro de um arquivo Word, este guia mostra uma solução completa e executável. Seja construindo um modelo que requer interação do usuário ou automatizando um formulário, você aprenderá exatamente **como inserir botão** usando Aspose.Words for Java e controlar seu posicionamento.

O tutorial cobre tudo o que você precisa para **adicionar controle ActiveX** a um documento Word, explica como **adicionar botão ao Word**, e demonstra o processo completo para **criar documento Word Java**. Nenhuma referência externa é necessária — basta copiar, executar e verificar o resultado.

## Pré-requisitos

* Java 17 (ou qualquer runtime Java 8+) instalado.
* Maven ou Gradle para gerenciar dependências.
* Uma licença Aspose.Words for Java (a versão de avaliação gratuita funciona para avaliação).
* Um entendimento básico da sintaxe Java.

> **Dica profissional:** Mantenha seus JARs do Aspose.Words em uma pasta `libs/` e adicione-os ao classpath do seu projeto para evitar conflitos de versão.

## Etapa 1: Configurar o projeto Maven

Crie um projeto Maven simples (ou use Gradle) e adicione a dependência Aspose.Words:

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word-button-demo</artifactId>
    <version>1.0.0</version>
    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- latest at time of writing -->
        </dependency>
    </dependencies>
</project>
```

Executar `mvn clean compile` baixa a biblioteca e prepara o caminho de compilação.

## Etapa 2: Criar um novo documento Word

A primeira operação é **criar documento Word java**. Você instancia um objeto `Document` e um `DocumentBuilder` que permite editar o arquivo.

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

A classe `Document` representa o arquivo .docx completo, enquanto `DocumentBuilder` fornece uma API fluente para inserção de conteúdo.

## Etapa 3: Como inserir botão – adicionar controle ActiveX

Aspose.Words expõe a classe `Forms2OleControl` para inserir controles ActiveX legados, como um CommandButton. Esta etapa mostra a maneira exata de **como inserir botão** no documento.

```java
        // Insert a CommandButton ActiveX control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);
```

O método `insertForms2OleControl` retorna uma instância `Forms2OleControl` que você pode configurar. Este é o núcleo do processo de **adicionar controle ActiveX**.

## Etapa 4: Definir a posição do botão

Agora realmente **definimos a posição do botão**. Os métodos `setLeft` e `setTop` do controle aceitam valores em pontos (1 pt = 1/72 in). Para alinhar o botão com coordenadas de tela típicas, você pode converter pixels para pontos (1 px ≈ 0.75 pt). No exemplo, posicionamos o botão a 100 px da borda esquerda e 150 px da borda superior.

```java
        // Position the button on the page
        commandButton.setLeft(100 * 0.75);   // 75 pt ≈ 100 px
        commandButton.setTop(150 * 0.75);    // 112.5 pt ≈ 150 px
```

Como a lógica de **definir a posição do botão** está encapsulada aqui, você pode reutilizar estas linhas sempre que precisar mover um controle. Ajuste os números para atender aos requisitos do seu layout.

## Etapa 5: Definir tamanho e legenda

Um botão sem rótulo é confuso. Use `setWidth`, `setHeight` e `setCaption` para dar-lhe uma aparência visível.

```java
        // Define size and caption
        commandButton.setWidth(120 * 0.75);   // 90 pt width
        commandButton.setHeight(30 * 0.75);   // 22.5 pt height
        commandButton.setCaption("Click Me");
```

O tamanho também é expresso em pontos, portanto convertemos de pixels para consistência.

## Etapa 6: Salvar o documento – concluir o fluxo de criar documento Word java

Finalmente, persista o arquivo no disco. O caminho pode ser absoluto ou relativo à raiz do projeto.

```java
        // Save the document containing the CommandButton
        doc.save("output/CommandButtonDemo.docx");
    }
}
```

Executar o programa gera `CommandButtonDemo.docx` dentro da pasta `output`. Abrir o arquivo no Microsoft Word mostra um botão clicável posicionado exatamente onde você o definiu.

### Saída esperada

* Um arquivo `.docx` chamado **CommandButtonDemo.docx**.
* Dentro do documento, um **CommandButton** rotulado “Click Me” aparece 100 px da margem esquerda e 150 px da margem superior.
* O botão responde a cliques quando o documento é aberto no Word (ele exibirá uma mensagem padrão do ActiveX a menos que você anexe código VBA personalizado).

## Etapa 7: Variações comuns e casos de borda

### Adicionando múltiplos botões

Se você precisar **adicionar botão ao Word** mais de uma vez, repita as etapas 3‑5 com uma nova instância `Forms2OleControl` a cada vez. Lembre-se de ajustar o valor de `setTop` para que os botões não se sobreponham.

```java
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);
        secondButton.setLeft(200 * 0.75);
        secondButton.setTop(250 * 0.75);
        secondButton.setWidth(120 * 0.75);
        secondButton.setHeight(30 * 0.75);
        secondButton.setCaption("Second");
```

### Trabalhando sem licença

Aspose.Words adiciona uma marca d'água quando usado sem licença. Para código de produção, compre uma licença e aplique-a no início do `main`:

```java
        License license = new License();
        license.setLicense("Aspose.Words.lic");
```

### Compatibilidade com versões antigas do Office

Controles ActiveX são suportados no formato `.doc` (Word 97‑2003). Para criar um arquivo legado, altere o formato de salvamento:

```java
        doc.save("CommandButtonDemo.doc", SaveFormat.DOC);
```

## Código-fonte completo (executável)

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Optional: apply a license if you have one
        // License license = new License();
        // license.setLicense("Aspose.Words.lic");

        // Step 1: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a CommandButton ActiveX control (how to insert button)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);

        // Step 3: Position the button on the page (set button position)
        commandButton.setLeft(100 * 0.75);   // distance from the left edge (points)
        commandButton.setTop(150 * 0.75);    // distance from the top edge (points)

        // Step 4: Define the button's size and caption
        commandButton.setWidth(120 * 0.75);   // width in points
        commandButton.setHeight(30 * 0.75);   // height in points
        commandButton.setCaption("Click Me");

        // Step 5: Save the document containing the CommandButton (create word document java)
        doc.save("output/CommandButtonDemo.docx");
    }
}
```

Salve o arquivo como `src/main/java/CommandButtonDemo.java`, execute `mvn exec:java -Dexec.mainClass=CommandButtonDemo` e abra o documento gerado para ver o resultado.

## Perguntas frequentes

**Q: Isso funciona com OpenJDK?**  
A: Sim. Aspose.Words é puro Java e roda em qualquer implementação JDK 8+, incluindo OpenJDK.

**Q: Posso mudar a fonte ou a cor do botão?**  
A: A aparência do botão ActiveX é controlada pelo aplicativo host (Word). Você pode anexar código VBA para modificar propriedades em tempo de execução, mas a aparência estática é limitada ao estilo padrão.

**Q: E se eu precisar colocar o botão dentro de uma célula de tabela?**  
A: Mova o cursor do `DocumentBuilder` para a célula antes de chamar `insertForms2OleControl`. O controle herdará o layout da célula, e você ainda pode usar `setLeft`/`setTop` para ajustes finos.

## Conclusão

Agora você sabe como **definir a posição do botão** em um documento Word usando Java, como **como inserir botão**, como **adicionar controle ActiveX**, e como **adicionar botão ao Word** seguindo as melhores práticas para projetos **criar documento Word java**. O exemplo completo demonstra todo o fluxo de trabalho — desde a configuração do projeto até um arquivo `.docx` salvo contendo um CommandButton funcional.

### Próximos passos

* Explore outros valores `Forms2OleControl.ControlType` (por exemplo, `CHECKBOX`, `TEXTBOX`) para criar formulários mais ricos.
* Combine o botão com macros VBA para tratamento de cliques personalizado.
* Use o recurso de mala‑direta do Aspose.Words para gerar documentos personalizados que já contenham controles interativos.

Feliz codificação, e aproveite a automação de documentos Word com Java!

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá-lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Como criar campos de formulário e adicionar conteúdo usando DocumentBuilder no Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Adicionar um campo de formulário Combo Box a um documento Word com Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Como carregar documentos Word com Aspose.Words Java: Guia abrangente](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}