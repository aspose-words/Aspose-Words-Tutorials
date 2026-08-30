---
category: general
date: 2026-08-23
description: Aprenda como inserir um botão de comando em um documento Word usando
  Java e Aspose.Words. Este guia mostra como adicionar um controle de formulário,
  definir o nome do botão e incorporar um botão ActiveX.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert command button
- add form control
- how to add button
- set button name
- add activex button
language: pt
lastmod: 2026-08-23
og_description: Inserir botão de comando em um documento Word usando Java. Siga este
  guia para adicionar controle de formulário, definir o nome do botão e incorporar
  um botão ActiveX com Aspose.Words.
og_image_alt: Screenshot of a Word document showing an inserted ActiveX command button
og_title: Inserir botão de comando no Word com Java – guia passo a passo
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Learn how to insert command button in a Word document using Java and
    Aspose.Words. This guide shows how to add form control, set button name, and embed
    an ActiveX button.
  headline: How to insert command button in a Word document using Java
  type: TechArticle
- description: Learn how to insert command button in a Word document using Java and
    Aspose.Words. This guide shows how to add form control, set button name, and embed
    an ActiveX button.
  name: How to insert command button in a Word document using Java
  steps:
  - name: Open `CommandButtonDemo.docx` with Microsoft Word (2016 or later).
    text: Open `CommandButtonDemo.docx` with Microsoft Word (2016 or later).
  - name: The **Submit** button appears where the cursor was positioned during insertion.
    text: The **Submit** button appears where the cursor was positioned during insertion.
  - name: Right‑click the button and choose **Properties** to see that the **Name**
      field contains `btnSubmit`.
    text: Right‑click the button and choose **Properties** to see that the **Name**
      field contains `btnSubmit`.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Como inserir um botão de comando em um documento do Word usando Java
url: /pt/java/using-document-elements/how-to-insert-command-button-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como inserir um botão de comando em um documento Word usando Java

Se você precisa **inserir command button** em um arquivo Word, este tutorial mostra uma solução completa com Aspose.Words for Java. Você verá como adicionar um controle de formulário, configurar sua legenda e definir o nome do botão sem sair do seu IDE.

O guia cobre tudo o que você precisa para criar um `.docx` que contém um botão ActiveX pronto para uso no Microsoft Word. Nenhuma ferramenta adicional é necessária, e o exemplo funciona em Java 8+.

## O que você aprenderá

* Como adicionar um controle de formulário do tipo **CommandButton** a um documento Word.  
* As etapas exatas para **set button name** e **add activex button** propriedades.  
* Como salvar o documento para que o botão apareça corretamente ao ser aberto no Word.  

Você deve ter um ambiente básico de desenvolvimento Java e um projeto Maven ou Gradle que possa importar a biblioteca Aspose.Words.

## Pré-requisitos

| Requisito | Motivo |
|-------------|--------|
| Java 8 ou mais recente | Aspose.Words for Java funciona em Java 8+. |
| Ferramenta de build Maven ou Gradle | Simplifica a adição da dependência Aspose.Words. |
| Licença Aspose.Words for Java (ou avaliação gratuita) | Necessária para o conjunto completo de recursos; a API funciona em modo de avaliação. |
| Uma IDE como IntelliJ IDEA ou Eclipse | Facilita a edição e execução do exemplo. |

## Etapa 1: Adicionar Aspose.Words ao seu projeto

Se você usa Maven, adicione a seguinte dependência ao `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Use the latest version -->
</dependency>
```

Para Gradle, coloque esta linha em `build.gradle`:

```gradle
implementation 'com.aspose:aspose-words:24.9'
```

Depois que a dependência for resolvida, você pode importar as classes da biblioteca no seu arquivo fonte Java.

## Etapa 2: Inserir command button – o código principal

Crie uma nova classe Java chamada `InsertCommandButtonDemo`. O código abaixo executa as quatro ações necessárias para **insert command button**:

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Add form control – an ActiveX CommandButton – to the document
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // 3️⃣ Set button name and displayed caption (this answers the "set button name" need)
        commandButton.setName("btnSubmit");
        commandButton.setCaption("Submit");

        // 4️⃣ Save the document with the embedded button
        doc.save("CommandButtonDemo.docx");
    }
}
```

### Por que cada linha importa

* **Document & DocumentBuilder** – Eles fornecem a representação em memória de um arquivo Word e a API para modificar seu conteúdo.  
* **insertForms2OleControl** – Este método **adds form control** do tipo `COMMAND_BUTTON`. O objeto `Forms2OleControl` retornado representa o controle ActiveX.  
* **setName** – Atribui um identificador programático (`btnSubmit`). Macros do Word ou VBA podem referenciar este nome posteriormente.  
* **setCaption** – Define o texto que o usuário vê no botão, respondendo à pergunta “como adicionar botão”.  
* **save** – Grava o `.docx` no disco, preservando o botão ActiveX incorporado.  

Executar o programa cria `CommandButtonDemo.docx` no diretório de trabalho. Abrir o arquivo no Microsoft Word mostra um botão rotulado **Submit** que você pode clicar (ele exibirá uma caixa de diálogo ActiveX padrão no modo de avaliação).

## Etapa 3: Verificar o botão inserido no Word

1. Abra `CommandButtonDemo.docx` com o Microsoft Word (2016 ou posterior).  
2. O botão **Submit** aparece onde o cursor estava posicionado durante a inserção.  
3. Clique com o botão direito no botão e escolha **Properties** para ver que o campo **Name** contém `btnSubmit`.  

Se o botão não aparecer, certifique‑se de que os **ActiveX controls** estejam habilitados nas configurações do Trust Center do Word.

## Etapa 4: Personalizando o botão (opcional)

Você pode personalizar ainda mais o botão ajustando seu tamanho, posição ou adicionando uma macro VBA. A classe `Forms2OleControl` expõe propriedades adicionais como `setWidth`, `setHeight` e `setLeft`. Abaixo está um exemplo que aumenta o botão:

```java
commandButton.setWidth(100);   // Width in points
commandButton.setHeight(30);   // Height in points
commandButton.setLeft(50);     // Horizontal offset from the left margin
```

Essas linhas podem ser colocadas após a chamada `setCaption`. Elas demonstram a personalização **add activex button** além da inserção básica.

## Armadilhas comuns e como evitá‑las

| Sintoma | Causa | Correção |
|---------|-------|----------|
| O botão não aparece no Word | Documento salvo antes de o controle ser adicionado | Garanta que `insertForms2OleControl` seja chamado antes de `doc.save`. |
| A legenda do botão está vazia | `setCaption` não foi chamado ou foi chamado com uma string vazia | Forneça uma string não vazia, por exemplo, `"Submit"`. |
| VBA não consegue encontrar o botão | Incompatibilidade de nome entre o código VBA e o valor de `setName` | Mantenha o nome consistente; use `setName("btnSubmit")` e referencie `btnSubmit` no VBA. |
| Aviso de segurança ao abrir o arquivo | A segurança de macro do Word bloqueia controles ActiveX | Ajuste Trust Center > Configurações de Macro, ou assine o documento com um certificado confiável. |

## Exemplo completo e executável

Abaixo está o arquivo fonte completo, pronto para copiar e colar no seu IDE. Ele inclui as declarações de importação, tratamento de exceções e um bloco de comentários que explica cada passo principal.

```java
// InsertCommandButtonDemo.java
// Demonstrates how to insert an ActiveX CommandButton into a Word document using Aspose.Words for Java.

import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Add a CommandButton form control (ActiveX) to the document.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // Step 3: Configure the button – set its programmatic name and visible caption.
        commandButton.setName("btnSubmit");   // This answers the "set button name" requirement.
        commandButton.setCaption("Submit");   // This is the text the user sees.

        // Optional: Resize and reposition the button (demonstrates add activex button customization).
        commandButton.setWidth(100);
        commandButton.setHeight(30);
        commandButton.setLeft(50);

        // Step 4: Save the document. The button is now embedded and will appear in Word.
        doc.save("CommandButtonDemo.docx");
    }
}
```

**Resultado esperado:** Após executar o programa, `CommandButtonDemo.docx` contém um único botão **Submit**. Abrir o arquivo no Word mostra o botão exatamente onde o cursor do `DocumentBuilder` estava localizado.

## Próximos passos

* **Add more form controls** – Use `Forms2OleControlType.CHECK_BOX`, `RADIO_BUTTON` ou `TEXT_BOX` para criar formulários Word completos.  
* **Combine with mail merge** – Insira botões em um documento de mala direta para criar formulários interativos personalizados.  
* **Attach VBA macros** – Incorpore programaticamente VBA que reage ao evento `Click` do botão para automação avançada.  

Esses tópicos ampliam naturalmente a técnica **add form control** que você acabou de dominar.

---

### Recapitulação

Agora você sabe como **insert command button** em um documento Word usando Java, como **add form control**, como **set button name**, e como personalizar **add activex button**. O exemplo completo funciona pronto para uso, e você pode adaptá‑lo a qualquer fluxo de geração de documentos. Feliz codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Como criar campos de formulário e adicionar conteúdo usando DocumentBuilder no Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Inserir campo de formulário Combo Box em documento Word](/words/english/net/working-with-form-fields/insert-form-fields/)
- [Inserir campo de formulário Check Box em documento Word](/words/english/net/add-content-using-documentbuilder/insert-check-box-form-field/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}