---
category: general
date: 2026-07-29
description: 'tutorial de Java para definir tamanho de botão: aprenda como inserir
  um botão de comando ActiveX em um documento Word usando Java e Aspose.Words, além
  de dimensionamento e criação de documento em branco.'
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button size java
- how to insert activex
- how to set button
- java create blank word
- insert command button word
language: pt
lastmod: 2026-07-29
og_description: Guia de definição de tamanho de botão em Java mostra como inserir
  um botão de comando ActiveX em um arquivo Word usando Java, ajustar seu tamanho
  e salvar o documento programaticamente.
og_image_alt: set button size java example showing a Word document with an ActiveX
  command button
og_title: definir tamanho do botão java – adicionar botão de comando ActiveX ao Word
  com Java
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: 'set button size java tutorial: learn how to insert ActiveX command
    button in a Word document using Java and Aspose.Words, plus sizing and blank document
    creation.'
  headline: set button size java – Insert ActiveX Command Button in Word
  type: TechArticle
- description: 'set button size java tutorial: learn how to insert ActiveX command
    button in a Word document using Java and Aspose.Words, plus sizing and blank document
    creation.'
  name: set button size java – Insert ActiveX Command Button in Word
  steps:
  - name: 1. Set Up the Project and Import Aspose.Words
    text: 'First, create a new Maven (or Gradle) project and add the Aspose.Words
      dependency shown above. Then, import the required classes in your Java source
      file:'
  - name: 2. java create blank word Document
    text: Now we actually **java create blank word** document. This is the foundation
      on which we’ll later **insert command button word**.
  - name: 3. Initialize DocumentBuilder and Insert the ActiveX Control
    text: 'The `DocumentBuilder` is a helper that lets us add content, paragraphs,
      tables, and, yes, ActiveX controls. Here’s where we answer **how to insert activex**:'
  - name: 4. How to Set Button Size Java – Adjust Width and Height
    text: 'Now comes the heart of the tutorial: **how to set button size java**. The
      control exposes several layout properties—`Left`, `Top`, `Width`, and `Height`.
      Setting them directly controls the button’s appearance on the page.'
  - name: 5. Save the Document
    text: 'Finally, persist the document to disk:'
  - name: What if the button doesn’t appear in Word?
    text: '- **Check the Word version.** ActiveX controls require the desktop version
      of Word; Word Online strips them out. - **Make sure the Aspose.Words license
      is applied** (if you’re using a paid edition). An unlicensed evaluation version
      may embed a watermark but still shows the control.'
  - name: Can I change the button’s font or color?
    text: Yes. After inserting the control, you can access its underlying OLE object
      and manipulate the VBA properties. That’s a more advanced topic—look into `commandButton.getOleObject().setProperty("ForeColor",
      0xFF0000)` for a red caption, for example.
  - name: How do I handle the button’s click event?
    text: ActiveX command buttons fire a VBA `Click` event. To make the button functional,
      you’ll need to embed a macro in the same document. Aspose.Words can add a macro
      module via the `Document.getMacros()` API, but the macro code itself must be
      written in VBA.
  - name: What about different button types?
    text: 'Aspose.Words supports many `Forms2OleControlType` values: `CHECKBOX`, `OPTIONBUTTON`,
      `LISTBOX`, etc. Swap the enum constant in the `insertForms2OleControl` call
      to experiment.'
  type: HowTo
tags:
- Java
- Aspose.Words
- ActiveX
- Word Automation
title: Definir tamanho do botão Java – Inserir botão de comando ActiveX no Word
url: /pt/java/using-document-elements/set-button-size-java-insert-activex-command-button-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# set button size java – Inserir Botão de Comando ActiveX no Word

Já se perguntou **how to set button size java** quando está automatizando documentos Word? Talvez você esteja construindo uma ferramenta de relatórios que precisa de um botão “Submit” clicável dentro do arquivo .docx. Neste tutorial, percorreremos todo o processo — criar um documento Word em branco, inserir um botão de comando ActiveX e definir explicitamente sua largura e altura — tudo com Java e Aspose.Words.

Também responderemos à persistente pergunta “how to insert activex” que surge para muitos desenvolvedores. Ao final, você terá um programa executável que gera um arquivo Word contendo um botão de comando perfeitamente dimensionado, pronto para personalizações adicionais.

---

## O que você precisará

- **Java Development Kit (JDK) 8 ou mais recente** – o código compila com qualquer JDK recente.
- **Aspose.Words for Java** (a versão mais recente até julho 2026). Baixe o JAR no [site da Aspose](https://products.aspose.com/words/java) ou via Maven:
  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.10</version>
  </dependency>
  ```
- Uma IDE ou editor de texto simples — IntelliJ IDEA, Eclipse ou VS Code servem.
- Uma pasta onde você deseja que o **CommandButton.docx** gerado seja salvo.

É isso. Sem bibliotecas extras de interop Office, sem truques COM, apenas Java puro.

---

## Implementação passo a passo

Dividiremos a solução em cinco etapas lógicas. Cada etapa tem um cabeçalho H2 dedicado; uma delas contém nossa **palavra‑chave principal** para atender ao SEO.

### 1. Configurar o Projeto e Importar Aspose.Words

Primeiro, crie um novo projeto Maven (ou Gradle) e adicione a dependência Aspose.Words mostrada acima. Em seguida, importe as classes necessárias no seu arquivo Java:

```java
import com.aspose.words.*;
```

> **Dica profissional:** Se você estiver usando uma IDE, deixe-a auto‑importar as classes. Isso economiza muito digitação e evita erros.

### 2. java create blank word Document

Agora realmente **java create blank word** documento. Esta é a base sobre a qual mais tarde **insert command button word**.

```java
// Step 2: Create a new blank document
Document document = new Document();          // Starts with a clean, empty .docx
```

O objeto `Document` representa todo o arquivo Word na memória. Neste ponto, o arquivo não tem páginas, nem texto — apenas uma tela limpa.

### 3. Inicializar DocumentBuilder e Inserir o Controle ActiveX

O `DocumentBuilder` é um auxiliar que nos permite adicionar conteúdo, parágrafos, tabelas e, sim, controles ActiveX. É aqui que respondemos **how to insert activex**:

```java
// Step 3: Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert an ActiveX command button (COMMANDBUTTON is a built‑in type)
Forms2OleControl commandButton = builder.insertForms2OleControl(
        Forms2OleControlType.COMMANDBUTTON);
```

`Forms2OleControl` é o wrapper da Aspose para um objeto OLE. Ao especificar `COMMANDBUTTON` informamos ao Word para incorporar um botão de comando ActiveX clássico.

### 4. How to Set Button Size Java – Ajustar Largura e Altura

Agora vem o coração do tutorial: **how to set button size java**. O controle expõe várias propriedades de layout — `Left`, `Top`, `Width` e `Height`. Defini‑las diretamente controla a aparência do botão na página.

```java
// Step 4: Set button properties, including size
commandButton.setCaption("Click Me"); // Text shown on the button
commandButton.setLeft(100);           // Distance from the left margin (points)
commandButton.setTop(200);            // Distance from the top margin (points)
commandButton.setWidth(120);          // Width in points (≈1.67 inches)
commandButton.setHeight(30);          // Height in points (≈0.42 inches)
```

Por que esses números? No Word, um ponto equivale a 1/72 de polegada. Portanto, uma largura de `120` pontos corresponde a cerca de 1,67 polegadas — grande o suficiente para um rótulo legível, mas não excessivo. Ajuste os valores para se adequar ao seu layout; as mesmas propriedades também respondem à consulta **how to set button** que você pode ter.

> **Nota:** Se precisar de um tipo de botão diferente (por exemplo, uma caixa de seleção), substitua `Forms2OleControlType.COMMANDBUTTON` pelo valor enum apropriado.

### 5. Salvar o Documento

Finalmente, persista o documento no disco:

```java
// Step 5: Save the document with the embedded ActiveX control
document.save("YOUR_DIRECTORY/CommandButton.docx");
```

Substitua `YOUR_DIRECTORY` por um caminho absoluto ou relativo na sua máquina. Após executar o programa, abra o arquivo gerado no Microsoft Word. Você verá um botão rotulado “Click Me” posicionado 100 pts da esquerda e 200 pts do topo, dimensionado exatamente como definimos.

---

## Exemplo Completo Funcional

Abaixo está a classe Java completa, pronta para execução. Copie‑e‑cole em `CommandButtonActiveX.java`, ajuste o caminho de saída e clique em **Run**.

```java
import com.aspose.words.*;

public class CommandButtonActiveX {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document (java create blank word)
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 3: Insert an ActiveX command button (how to insert activex)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 4: Set button properties – this is how to set button size java
        commandButton.setCaption("Click Me"); // Button text
        commandButton.setLeft(100);           // Left position (points)
        commandButton.setTop(200);            // Top position (points)
        commandButton.setWidth(120);          // Width (points)
        commandButton.setHeight(30);          // Height (points)

        // Step 5: Save the document (insert command button word)
        document.save("YOUR_DIRECTORY/CommandButton.docx");
    }
}
```

**Saída esperada:** Ao abrir `CommandButton.docx` no Word, será exibida uma única página com um botão clicável “Click Me” posicionado aproximadamente ao meio da página. As dimensões do botão correspondem aos valores definidos, confirmando que **set button size java** funciona como esperado.

---

## Perguntas Frequentes & Casos Limite

### E se o botão não aparecer no Word?

- **Verifique a versão do Word.** Controles ActiveX requerem a versão desktop do Word; o Word Online os remove.
- **Certifique‑se de que a licença do Aspose.Words está aplicada** (se estiver usando uma edição paga). Uma versão de avaliação sem licença pode inserir uma marca d'água, mas ainda exibe o controle.

### Posso mudar a fonte ou a cor do botão?

Sim. Após inserir o controle, você pode acessar seu objeto OLE subjacente e manipular as propriedades VBA. Isso é um tópico mais avançado — veja `commandButton.getOleObject().setProperty("ForeColor", 0xFF0000)` para um rótulo vermelho, por exemplo.

### Como lidar com o evento de clique do botão?

Botões de comando ActiveX disparam um evento VBA `Click`. Para tornar o botão funcional, você precisará incorporar uma macro no mesmo documento. Aspose.Words pode adicionar um módulo de macro via a API `Document.getMacros()`, mas o código da macro deve ser escrito em VBA.

### E quanto a diferentes tipos de botão?

Aspose.Words suporta vários valores de `Forms2OleControlType`: `CHECKBOX`, `OPTIONBUTTON`, `LISTBOX`, etc. Troque a constante enum em `insertForms2OleControl` para experimentar.

---

## Dicas Profissionais para Código Pronto para Produção

1. **Use constantes para valores de layout** – facilita ajustes futuros.
2. **Envolva o caminho de salvamento em um objeto `Path`** para evitar separadores específicos da plataforma.
3. **Descarte o Document** (ou use try‑with‑resources) se estiver processando muitos arquivos em um loop.
4. **Valide a pasta de saída** antes de chamar `save` para evitar `FileNotFoundException`.

---

## Conclusão

Você acabou de aprender **set button size java** criando um arquivo Word em branco, inserindo um botão de comando ActiveX e configurando precisamente suas dimensões — tudo com algumas linhas de código Java. Isso cobre o núcleo de **how to insert activex**, **how to set button**, **java create blank word** e **insert command button word** em um único exemplo autônomo.

Próximos passos? Experimente personalizar a legenda do botão, adicionar uma macro para responder a cliques ou incorporar múltiplos controles na mesma página. Você também pode explorar a conversão do .docx resultante para PDF com Aspose.Words, preservando o botão como uma imagem estática.

Sinta‑se à vontade para experimentar e, se encontrar algum problema, deixe um comentário abaixo. Feliz codificação!

## O que Você Deve Aprender a Seguir?

Os tutoriais a seguir abordam tópicos estreitamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Como criar campos de formulário e adicionar conteúdo usando DocumentBuilder no Aspose.Words para Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Como Carregar Documentos Word com Aspose.Words Java: Guia Abrangente](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [Como salvar documento como PDF com Aspose.Words para Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}