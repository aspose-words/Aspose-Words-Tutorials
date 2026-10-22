---
category: general
date: 2026-07-16
description: Defina o tamanho do botão programaticamente em um documento Word usando
  Aspose.Words para Java. Aprenda como inserir um botão ActiveX, definir a localização
  do botão e muito mais.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button size
- insert activex button
- programmatically add button
- set button location
- create word document button
language: pt
lastmod: 2026-07-16
og_description: Defina o tamanho do botão em um documento Word usando Java. Este guia
  passo a passo mostra como inserir um botão ActiveX, definir a localização do botão
  e adicionar o botão programaticamente.
og_image_alt: Screenshot of a Word document where the button size has been set using
  Aspose.Words for Java
og_title: Defina o Tamanho do Botão no Word com Java – Tutorial Completo do Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: Set button size programmatically in a Word document using Aspose.Words
    for Java. Learn how to insert ActiveX button, set button location and more.
  headline: Set Button Size in Word with Java – Complete Aspose.Words Guide
  type: TechArticle
- description: Set button size programmatically in a Word document using Aspose.Words
    for Java. Learn how to insert ActiveX button, set button location and more.
  name: Set Button Size in Word with Java – Complete Aspose.Words Guide
  steps:
  - name: Expected Output Screenshot
    text: '![Word document showing the inserted button with the set button size](https://example.com/images/set-button-size.png
      "Screenshot of a Word file where the button size has been set using Aspose.Words
      for Java")'
  - name: “Can I set the button size using centimeters instead of points?”
    text: Word’s API only accepts points, but you can convert centimeters to points
      (`points = cm * 28.3465`). Write a small helper method if you prefer metric
      units.
  - name: “What if I need the button to appear on a specific page?”
    text: After inserting the button, you can move the cursor to a particular page
      using `builder.moveToPage(pageNumber)`. Insert the control right after the move,
      then set its location as shown above.
  - name: “Does this work with .doc (Word 97‑2003) files?”
    text: Yes—Aspose.Words automatically handles older formats. Just change the file
      extension in `doc.save("Demo.doc")`.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
title: Definir o tamanho do botão no Word com Java – Guia completo do Aspose.Words
url: /pt/java/using-document-elements/set-button-size-in-word-with-java-complete-aspose-words-guid/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Definir Tamanho do Botão no Word com Java – Guia Completo do Aspose.Words

Já se perguntou como **definir o tamanho do botão** dentro de um arquivo Word sem abrir a interface? Você não está sozinho. Quando você precisa gerar um documento preenchido com formulário em tempo real — por exemplo, um pacote de integração com um botão “Submit” — fazer isso programaticamente economiza horas de trabalho manual.

Neste tutorial, percorreremos os passos exatos para **inserir botão ActiveX**, ajustar suas dimensões, posicioná‑lo corretamente e, finalmente, salvar o arquivo. Ao final, você será capaz de **adicionar botões programaticamente** a qualquer documento Word usando Aspose.Words for Java.

## Pré‑requisitos – O que Você Precisa Antes de Começar

- **Java Development Kit (JDK) 8+** – o código roda em qualquer JDK recente.
- **Aspose.Words for Java** library (download the latest JAR from the official site).  
- Uma **IDE** de sua escolha — IntelliJ IDEA, Eclipse, ou até mesmo um editor de texto simples funciona.
- Familiaridade básica com a sintaxe Java; não é necessário conhecimento profundo de automação do Word.

> *Dica profissional:* Mantenha o JAR do Aspose.Words no classpath do seu projeto, caso contrário você encontrará `ClassNotFoundException` no momento em que tentar importar `com.aspose.words.*`.

## Etapa 1: Criar um Novo Documento Word

A primeira coisa que fazemos é criar um documento em branco e um `DocumentBuilder`. Pense no builder como uma caneta que nos permite desenhar qualquer coisa dentro do arquivo.

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create an empty document.
        Document doc = new Document();

        // DocumentBuilder gives us a fluent API to add content.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Por que isso importa:** O objeto `Document` representa o arquivo .docx completo, enquanto o `DocumentBuilder` é o motor que nos permite inserir parágrafos, tabelas e — sim — controles ActiveX.

## Etapa 2: Inserir Botão ActiveX – O Momento “Inserir Botão ActiveX”

Agora realmente **inserimos o botão activex** no documento. Aspose.Words expõe um método conveniente `insertForms2OleControl` que retorna um objeto `Forms2OleControl`.

```java
        // Insert an ActiveX CommandButton control.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        commandButton.setName("cmdSubmit");   // Programmatic name.
        commandButton.setCaption("Submit");   // Text shown on the button.
```

> *O que está acontecendo nos bastidores?* `Forms2OleControlType.COMMAND_BUTTON` indica ao Word que queremos um CommandButton clássico, o mesmo tipo que você arrastaria da guia Developer na interface.

## Etapa 3: Definir Tamanho e Localização do Botão – A Lógica Central de “Definir Tamanho do Botão”

É aqui que a palavra‑chave principal brilha. Vamos **definir o tamanho do botão** e também **definir a localização do botão** para que o controle apareça exatamente onde queremos na página.

```java
        // Position the button (distance from the left/top edges in points).
        commandButton.setLeft(100);   // 100 points from the left margin.
        commandButton.setTop(150);    // 150 points from the top margin.

        // Set the button's dimensions.
        commandButton.setWidth(80);   // Width = 80 points.
        commandButton.setHeight(30);  // Height = 30 points.
```

> **Por que isso importa:** Pontos são a unidade de medida nativa no Word (1 ponto = 1/72 polegada). Ajustando `setLeft`, `setTop`, `setWidth` e `setHeight` você obtém controle pixel‑perfect — nada de “parece certo na minha tela, mas não na impressora”.

> *Armadilha comum:* Esquecer de definir a largura ou a altura deixará o botão no tamanho padrão, que pode ser muito pequeno para clicar. Sempre especifique ambos.

## Etapa 4: Salvar o Documento – “Criar Botão de Documento Word” Concluído

Finalmente, gravamos o arquivo no disco. O nome sugere que estamos **criando um botão de documento Word** dentro de um .docx.

```java
        // Persist the document to the file system.
        doc.save("CommandButtonDemo.docx");
    }
}
```

Quando você abrir `CommandButtonDemo.docx` no Microsoft Word, verá um botão **Submit** posicionado a 100 pt da borda esquerda e 150 pt do topo, com tamanho de 80 × 30 pt. Clicá‑lo na interface disparará o comportamento padrão do ActiveX (que você pode conectar posteriormente com VBA, se necessário).

### Captura de Tela do Resultado Esperado

![Documento Word mostrando o botão inserido com o tamanho definido](https://example.com/images/set-button-size.png "Screenshot of a Word file where the button size has been set using Aspose.Words for Java")

*Texto alternativo:* definir tamanho do botão em um documento Word usando Java

## Etapa 5 (Opcional): Adicionar Mais Controles ou Estilizar o Botão

Se você precisar **adicionar botões programaticamente** além de um único botão Submit, basta repetir o bloco de inserção com novos nomes e legendas. Você também pode ajustar a fonte, cor de fundo ou até mesmo vincular macros VBA posteriormente.

```java
        // Example: Adding a Cancel button next to Submit.
        Forms2OleControl cancelBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        cancelBtn.setName("cmdCancel");
        cancelBtn.setCaption("Cancel");
        cancelBtn.setLeft(190);   // Position it 90 points to the right of Submit.
        cancelBtn.setTop(150);
        cancelBtn.setWidth(80);
        cancelBtn.setHeight(30);
```

> *Dica:* Mantenha todas as dimensões dos botões consistentes para um visual profissional. Uma maneira rápida é armazenar largura/altura em constantes.

## Perguntas Frequentes & Casos Limítrofes

### “Posso definir o tamanho do botão usando centímetros em vez de pontos?”

A API do Word aceita apenas pontos, mas você pode converter centímetros para pontos (`points = cm * 28.3465`). Escreva um pequeno método auxiliar se preferir unidades métricas.

### “E se eu precisar que o botão apareça em uma página específica?”

Depois de inserir o botão, você pode mover o cursor para uma página específica usando `builder.moveToPage(pageNumber)`. Insira o controle logo após o movimento, então defina sua localização como mostrado acima.

### “Isso funciona com arquivos .doc (Word 97‑2003)?”

Sim — Aspose.Words lida automaticamente com formatos antigos. Basta mudar a extensão do arquivo em `doc.save("Demo.doc")`.

## Exemplo Completo e Executável

Abaixo está o programa completo que você pode copiar‑colar em uma classe Java e executar imediatamente (desde que o JAR do Aspose.Words esteja no classpath).

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert the first ActiveX CommandButton.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        commandButton.setName("cmdSubmit");
        commandButton.setCaption("Submit");

        // 3️⃣ Set button location and size – the core set button size logic.
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // 4️⃣ (Optional) Add a second button for illustration.
        Forms2OleControl cancelBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        cancelBtn.setName("cmdCancel");
        cancelBtn.setCaption("Cancel");
        cancelBtn.setLeft(190);
        cancelBtn.setTop(150);
        cancelBtn.setWidth(80);
        cancelBtn.setHeight(30);

        // 5️⃣ Save the document – you’ve now created a Word document button.
        doc.save("CommandButtonDemo.docx");
    }
}
```

Execute o programa, abra o `CommandButtonDemo.docx` gerado, e você verá dois botões com tamanho adequado prontos para interação.

## Conclusão – Você Dominou a Definição do Tamanho do Botão no Word

Acabamos de percorrer uma solução completa, de ponta a ponta, para **definir o tamanho do botão** e **definir a localização do botão** usando Aspose.Words for Java. Seguindo os passos, você pode **inserir botão activex**, **adicionar botões programaticamente**, e, finalmente, **criar elementos de botão em documentos Word** que se comportam exatamente como você precisa.

Qual o próximo passo? Tente incorporar o botão dentro de uma célula de tabela, ou anexar uma macro VBA que valide os campos do formulário antes da submissão. O mesmo padrão funciona para outros controles ActiveX como caixas de seleção ou caixas de combinação — basta trocar `Forms2OleControlType.COMMAND_BUTTON` pelo valor enum apropriado.

Se encontrar algum problema, deixe um comentário abaixo. Boa codificação, e aproveite o poder da criação automatizada de documentos Word!

## O Que Você Deve Aprender a Seguir?

Os tutoriais a seguir cobrem tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Como Definir LoadOptions no Aspose.Words para Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Como remover rodapés de documentos Word usando Aspose.Words para Java](/words/english/java/document-manipulation/removing-content-from-documents/)
- [Aspose.Words Java&#58; Guia Abrangente de Processamento de Documentos Word](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}