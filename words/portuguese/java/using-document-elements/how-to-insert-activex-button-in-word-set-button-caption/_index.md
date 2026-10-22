---
category: general
date: 2026-07-26
description: Como inserir um botão ActiveX em um documento do Word usando Aspose.Words
  – aprenda a definir a legenda, a posição e o tamanho do botão em apenas algumas
  linhas.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert activex
- set button caption
language: pt
lastmod: 2026-07-26
og_description: Como inserir um botão ActiveX em um documento Word com Aspose.Words.
  Siga este tutorial passo a passo para definir a legenda do botão, a posição e o
  tamanho.
og_image_alt: Screenshot of a Word document showing an inserted ActiveX CommandButton
  with a custom caption
og_title: Como Inserir um Botão ActiveX no Word – Guia Rápido
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: How to insert ActiveX button in a Word document using Aspose.Words
    – learn to set button caption, position, and size in just a few lines.
  headline: How to Insert ActiveX Button in Word – Set Button Caption
  type: TechArticle
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
- Document generation
title: Como Inserir um Botão ActiveX no Word – Definir a Legenda do Botão
url: /pt/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como Inserir um Botão ActiveX no Word – Definir a Legenda do Botão

Já se perguntou **como inserir ActiveX** controles em um arquivo Word sem abrir a interface do usuário? Você não está sozinho. Em muitas aplicações corporativas você precisa de um botão clicável que execute uma macro, e fazer isso programaticamente economiza horas. Este guia mostra exatamente **como inserir ActiveX** CommandButton usando Aspose.Words for Java e—sim—como **definir a legenda do botão** para que o usuário saiba o que clicar.

Vamos percorrer todo o processo: desde a configuração da biblioteca, criação de um documento novo, inserção do botão, ajuste de seu tamanho e localização, atribuição de uma legenda amigável e, finalmente, salvamento do arquivo. Ao final, você terá um `.docx` executável que abre no Word com um botão ActiveX totalmente funcional pronto para disparar sua macro.

---

## O que Você Vai Aprender

- Instalar e referenciar Aspose.Words em um projeto Java.  
- Criar um novo `Document` e `DocumentBuilder`.  
- **Inserir ActiveX** CommandButton control com uma única linha de código.  
- **Definir a legenda do botão**, ajustar sua posição e definir suas dimensões.  
- Salvar o documento e abri-lo no Word para ver o resultado.

Nenhuma experiência prévia com ActiveX é necessária; apenas conhecimento básico de Java e uma cópia do Aspose.Words.

---

## Pré-requisitos

- Java 8 ou mais recente instalado na sua máquina.  
- Maven ou Gradle para gerenciamento de dependências (mostraremos o trecho Maven).  
- Uma cópia licenciada ou de avaliação do **Aspose.Words for Java** (a versão de avaliação funciona bem para esta demonstração).  
- Microsoft Word (qualquer versão recente) para testar o arquivo gerado.

---

## Etapa 1: Configurar Aspose.Words no Seu Projeto

Primeiro de tudo—adicione a dependência do Aspose.Words. Se você usa Maven, insira isso no seu `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- check for the latest version -->
</dependency>
```

Usuários do Gradle podem adicionar:

```gradle
implementation 'com.aspose:aspose-words:24.10'
```

Depois de um rápido `mvn clean install` (ou `gradle build`) a biblioteca estará no seu classpath e você estará pronto para codificar.

---

## Etapa 2: Criar um Novo Documento e Builder

Um `Document` representa todo o arquivo Word, enquanto `DocumentBuilder` permite editá‑lo. Pense no builder como uma caneta que desenha em uma tela em branco.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank document and a builder
        Document doc = new Document();                 // creates an empty .docx
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Por que começar com um documento em branco? Ele garante que você tenha controle total sobre cada elemento que adicionar, e não há formatação oculta para surpreendê‑lo depois.

---

## Etapa 3: Inserir o Controle ActiveX CommandButton

Agora vem a estrela do show. Aspose.Words expõe `insertForms2OleControl` que pode colocar qualquer controle ActiveX que você especificar. Aqui pedimos um **CommandButton**.

```java
        // Step 3: Insert a CommandButton ActiveX control
        Forms2OleControl commandBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);
```

O método retorna um objeto `Forms2OleControl`, dando acesso programático às propriedades do botão. É aqui que **como inserir activex** se torna uma única linha—sem precisar lidar com APIs COM de baixo nível.

---

## Etapa 4: Posicionar, Redimensionar e Definir a Legenda do Botão

Um botão que flutua no meio da página não é muito útil. Você vai querer colocá‑lo onde os usuários esperam, dar‑lhe um tamanho sensato e—mais importante—**definir a legenda do botão** para que saibam o que o clique fará.

```java
        // Step 4a: Position the button (coordinates are in points)
        commandBtn.setLeft(100);   // distance from the left margin
        commandBtn.setTop(150);    // distance from the top margin

        // Step 4b: Define width and height
        commandBtn.setWidth(120);
        commandBtn.setHeight(30);

        // Step 4c: Set the button caption (the text that appears on the button)
        commandBtn.setCaption("Click Me");
```

**Por que esses números?** O Word usa pontos (1 pt ≈ 1/72 polegada). `100 pt` ≈ 1,4 pol. da esquerda, `150 pt` ≈ 2,1 pol. do topo—aproximadamente o centro de uma página A4 padrão. Ajuste conforme o layout desejado.

Definir a legenda é crucial; sem ela o botão parece um retângulo vazio. O método `setCaption` aceita qualquer string, então você pode localizá‑la depois, se necessário.

---

## Etapa 5: Salvar o Documento

Finalmente, escreva o documento no disco. Você pode escolher qualquer pasta que desejar; apenas certifique‑se de que o caminho exista.

```java
        // Step 5: Save the document to a .docx file
        String outputPath = "C:/Temp/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Ao abrir `ActiveXButton.docx` no Word, você verá um botão bem posicionado rotulado **“Click Me.”** Se você der duplo‑clique nele, o Word solicitará que habilite macros (já que controles ActiveX são considerados habilitados para macro). A partir daí, você pode vincular uma rotina VBA ao evento `Click` do botão.

---

## Casos de Borda e Dicas que Você Pode Perder

- **Formato Macro‑Enabled**: O Word desabilita controles ActiveX em arquivos `.docx` simples, a menos que o usuário habilite macros. Se precisar que o botão funcione imediatamente, considere salvar como `.docm` (macro‑enabled) usando `doc.save(outputPath, SaveFormat.DOCM);`.
- **Compatibilidade**: Versões mais antigas do Word (pré‑2007) usam o formato binário `.doc`. Aspose.Words pode salvar nesse formato, mas as propriedades do controle podem ser renderizadas de forma ligeiramente diferente.
- **Configurações de Segurança**: Alguns ambientes corporativos bloqueiam ActiveX. Se o seu botão não aparecer, verifique o Centro de Confiabilidade do Word → Configurações de ActiveX.
- **Múltiplos Botões**: Quer mais de um? Basta repetir a chamada `insertForms2OleControl` e ajustar os valores `Left`/`Top` de cada botão. Mantenha o controle dos objetos retornados para definir legendas individuais.
- **Estilizando a Legenda**: A legenda herda a fonte padrão. Para alterá‑la, seria necessário editar o XML subjacente ou aplicar um estilo Word após a inserção—fora do escopo deste guia rápido, mas viável com a API `ParagraphFormat` do Aspose.Words.

---

## Exemplo Completo Funcional

Abaixo está a classe Java completa, pronta‑para‑executar. Copie‑e‑cole no seu IDE, ajuste o caminho de saída e pressione **Run**.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control
        Forms2OleControl commandBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Position the button (points from the left/top margins)
        commandBtn.setLeft(100);
        commandBtn.setTop(150);

        // Set size (width × height in points)
        commandBtn.setWidth(120);
        commandBtn.setHeight(30);

        // Set the button caption – this is the visible text
        commandBtn.setCaption("Click Me");

        // Save the document; you may also use SaveFormat.DOCM for macro‑enabled files
        String outputPath = "C:/Temp/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

**Saída esperada**: Após a execução, o console imprime o local de salvamento. Abrindo o arquivo gerado no Word, você verá um botão posicionado aproximadamente no meio da página, rotulado “Click Me”. Clicar nele disparará o evento padrão de clique do ActiveX (você precisará anexar uma macro VBA para responder).

---

## Conclusão

Agora você sabe **como inserir ActiveX** CommandButton controls em um documento Word programaticamente com Aspose.Words, e viu exatamente como **definir a legenda do botão**, posicionar e dimensionar o controle. Essa abordagem elimina o trabalho manual de UI, integra‑se perfeitamente a geradores de relatórios automatizados e lhe dá controle total sobre o

## O que Você Deve Aprender a Seguir?

Os tutoriais a seguir cobrem tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Inserir Formas em Documentos Word Usando Aspose.Words para .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Inserir Imagem Inline em Documento Word usando Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Inserir uma Imagem no Cabeçalho de Documento Word | Aspose.Words para .NET](/words/english/net/header-footer-formatting/insert-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}