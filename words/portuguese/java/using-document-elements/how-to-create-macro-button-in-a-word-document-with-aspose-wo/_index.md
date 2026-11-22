---
category: general
date: 2026-11-22
description: Crie um botão de macro em um documento Word usando Java. Aprenda a inserir
  um botão de comando, definir o texto do botão e vincular a macro ao botão para documentos
  interativos.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create macro button
- insert command button
- set button text
- link macro to button
- add interactive button
language: pt
lastmod: 2026-11-22
og_description: Crie um botão de macro em um documento Word usando Java. Este tutorial
  mostra como inserir um botão de comando, definir o texto do botão e vincular a macro
  ao botão para total interatividade.
og_image_alt: Screenshot of a Word document showing a macro button created with Java
  code
og_title: Crie um botão de macro em um documento Word com Java – guia passo a passo
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Create macro button in a Word document using Java. Learn to insert
    command button, set button text, and link macro to button for interactive documents.
  headline: How to create macro button in a Word document with Aspose.Words for Java
  type: TechArticle
- description: Create macro button in a Word document using Java. Learn to insert
    command button, set button text, and link macro to button for interactive documents.
  name: How to create macro button in a Word document with Aspose.Words for Java
  steps:
  - name: Insert command button into the document
    text: '`DocumentBuilder.insertForms2OleControl` creates an OLE control of the
      specified type. The `Forms2OleControlType.COMMAND_BUTTON` constant tells Aspose.Words
      to generate a command button that can host a macro.'
  - name: Set button text (caption)
    text: The caption is the visible label on the button. Use `setCaption` to define
      what the user sees.
  - name: Link macro to button
    text: A macro is identified by its name, for example `MyMacro`. The `setOnClick`
      method stores this name in the button’s `OnClick` event handler.
  - name: Add interactive button to a Word document
    text: After configuring the OLE control, you may want to position it, resize it,
      or add surrounding text. The `DocumentBuilder` continues to operate on the document,
      so you can insert paragraphs before or after the button.
  - name: Expected output
    text: 'Running the program generates `MacroButtonDemo.docm`. Opening the file
      in Microsoft Word shows:'
  type: HowTo
tags:
- Aspose.Words
- Java
- OLE controls
- Automation
title: Como criar um botão de macro em um documento Word com Aspose.Words para Java
url: /pt/java/using-document-elements/how-to-create-macro-button-in-a-word-document-with-aspose-wo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como criar botão de macro em um documento Word com Aspose.Words para Java

Se você precisa **criar botão de macro** em um arquivo Word, este guia o conduzirá pelos passos exatos necessários. Você aprenderá como **inserir botão de comando**, **definir o texto do botão** e **vincular macro ao botão** para que o documento se torne totalmente interativo.

Os desenvolvedores costumam incorporar controles OLE para acionar macros VBA a partir de um documento. Este tutorial cobre o fluxo de trabalho completo, desde a configuração do projeto até um exemplo Java executável que adiciona um **botão interativo** a um arquivo .docx. Nenhum script externo é necessário — tudo é executado dentro do processo Java.

## Pré-requisitos

Antes de começar, certifique‑se de que você tem:

* JDK 17 ou posterior instalado.
* Maven 3.8+ (ou Gradle) para gerenciamento de dependências.
* Aspose.Words for Java 23.9 ou mais recente — a biblioteca fornece o `DocumentBuilder` e as APIs de controle OLE.
* Familiaridade básica com Java e macros VBA.

Se algum desses itens estiver faltando, instale‑o primeiro; o restante do tutorial assume que eles estão disponíveis.

## Como criar botão de macro com Aspose.Words para Java

O núcleo da solução consiste em quatro ações:

1. **Inserir botão de comando** controle OLE no documento.
2. **Definir texto do botão** (legenda) que o usuário vê.
3. **Vincular macro ao botão** para que ao clicar execute a rotina VBA desejada.
4. **Salvar o documento** com a macro incorporada.

Cada ação é explicada em sua própria seção abaixo.

### Etapa 1: Inserir botão de comando no documento

`DocumentBuilder.insertForms2OleControl` cria um controle OLE do tipo especificado. A constante `Forms2OleControlType.COMMAND_BUTTON` indica ao Aspose.Words para gerar um botão de comando que pode hospedar uma macro.

```java
import com.aspose.words.*;

public class MacroButtonDemo {
    public static void main(String[] args) throws Exception {
        // Load a blank document or create a new one
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a command button OLE control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
```

**Por que isso importa:** O controle OLE funciona como um contêiner para a macro. Sem inseri‑lo, não há elemento visual para o usuário clicar.

### Etapa 2: Definir texto do botão (legenda)

A legenda é o rótulo visível no botão. Use `setCaption` para definir o que o usuário vê.

```java
        // Set the button's caption – this is the text displayed on the button
        commandButton.setCaption("Run Report");
```

**Por que isso importa:** Texto claro no botão melhora a usabilidade. O método `setCaption` atualiza a propriedade `Caption` do controle OLE, que o Word renderiza como rótulo do botão.

### Etapa 3: Vincular macro ao botão

Uma macro é identificada pelo seu nome, por exemplo `MyMacro`. O método `setOnClick` armazena esse nome no manipulador de evento `OnClick` do botão.

```java
        // Assign a macro to run when the button is clicked
        commandButton.setOnClick("MyMacro");
```

**Por que isso importa:** Vincular uma macro cria o comportamento interativo. Quando o usuário clica no botão no Word, a rotina VBA associada é executada.

### Etapa 4: Adicionar botão interativo a um documento Word

Depois de configurar o controle OLE, você pode querer posicioná‑lo, redimensioná‑lo ou adicionar texto ao redor. O `DocumentBuilder` continua operando no documento, permitindo inserir parágrafos antes ou depois do botão.

```java
        // Add a descriptive paragraph before the button
        builder.moveToDocumentStart();
        builder.writeln("Click the button below to generate the report:");

        // Move the cursor back to the button location (optional)
        builder.moveTo(commandButton.getNode());

        // Optionally, resize the button (width and height in points)
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        // Save the document with the macro-enabled format
        doc.save("MacroButtonDemo.docm", SaveFormat.DOCM);
    }
}
```

**Por que isso importa:** Salvar como `.docm` preserva o código da macro. Se salvar como `.docx`, a referência à macro é perdida.

## Exemplo completo executável

A seguir está o programa Java completo, incluindo importações, tratamento de exceções e comentários que explicam cada passo. Copie o código para um projeto Maven com a dependência Aspose.Words e execute‑o.

```java
// Maven dependency (add to pom.xml):
// <dependency>
//   <groupId>com.aspose</groupId>
//   <artifactId>aspose-words</artifactId>
//   <version>23.9</version>
// </dependency>

import com.aspose.words.*;

public class MacroButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a new empty document
        Document doc = new Document();

        // 2. Initialize DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Write an introductory paragraph
        builder.writeln("Press the button to execute the macro:");

        // 4. Insert the command button OLE control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // 5. Set the visual caption of the button
        commandButton.setCaption("Run Report");

        // 6. Link the button to a VBA macro named MyMacro
        commandButton.setOnClick("MyMacro");

        // 7. Resize the button for better appearance
        commandButton.setWidth(120);   // points
        commandButton.setHeight(30);   // points

        // 8. Save the document as a macro‑enabled file
        doc.save("MacroButtonDemo.docm", SaveFormat.DOCM);
    }
}
```

### Saída esperada

Executar o programa gera `MacroButtonDemo.docm`. Abrir o arquivo no Microsoft Word mostra:

* Um parágrafo que contém *“Press the button to execute the macro:”*.
* Um botão rotulado **Run Report** diretamente abaixo do parágrafo.
* Ao clicar no botão, o Word tenta executar a macro `MyMacro`. (Você deve adicionar o código VBA real ao documento manualmente ou via outra etapa de automação.)

Se a macro não existir, o Word exibe um aviso de segurança, que é o comportamento padrão para documentos habilitados para macro.

## Variações comuns e casos de borda

| Cenário | Como adaptar o código |
|----------|-----------------------|
| **Legenda de botão diferente** | Alterar a string passada para `setCaption`. |
| **Múltiplos botões** | Chamar `insertForms2OleControl` repetidamente, cada um com seu próprio `setCaption` e `setOnClick`. |
| **Nomes de macro personalizados** | Substituir `"MyMacro"` por qualquer nome de procedimento VBA válido, por exemplo, `"ExportToExcel"`. |
| **Restrições de tamanho do botão** | Ajustar os valores de `setWidth` e `setHeight`; o Word respeita os pontos fornecidos. |
| **Incorporar a macro programaticamente** | Usar `Document.getBuiltInDocumentProperties().add("Macros", …)` ou uma etapa separada de injeção VBA; o Aspose.Words não grava código VBA por si. |

**Dica profissional:** Sempre teste o `.docm` gerado em uma máquina com a segurança de macro configurada para *Enable all macros* (Habilitar todas as macros) durante o desenvolvimento. Em produção, assine a macro com um certificado confiável para evitar prompts de segurança.

## Lista de verificação de solução de problemas

* **O botão não aparece** – Verifique se o documento está salvo como `.docm` e aberto em uma versão do Word que suporte controles OLE.
* **A macro não executa** – Certifique‑se de que o nome da macro corresponde exatamente, incluindo maiúsculas/minúsculas, e que a macro exista no projeto VBA do documento.
* **A legenda do botão está truncada** – Aumente a largura do botão usando `setWidth` para acomodar texto mais longo.
* **Deslocamento inesperado de layout** – Use `builder.moveTo` para posicionar o cursor precisamente antes de inserir o controle.

## Conclusão

Agora você sabe como **criar botão de macro** em um documento Word usando Java, **inserir botão de comando**, **definir texto do botão** e **vincular macro ao botão** para total interatividade. O exemplo completo demonstra todas as chamadas de API necessárias, explica por que cada passo importa e fornece orientações para variações comuns.

Em seguida, você pode explorar:

* **Adicionar botão interativo** a modelos existentes em vez de um novo documento.
* **Injetar código VBA programaticamente** usando o Open XML SDK ou uma ferramenta de automação secundária.
* **Combinar múltiplos controles OLE** (caixas de seleção, caixas de lista) para criar formulários avançados.

Experimente diferentes legendas, nomes de macro e tamanhos de botão para adequar ao seu caso de uso específico. Feliz codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Como inserir botão de comando em um documento Word usando Java](/words/english/java/using-document-elements/how-to-insert-command-button-in-a-word-document-using-java/)
- [Como definir a posição do botão em um documento Word com Java](/words/english/java/using-document-elements/how-to-set-button-position-in-a-word-document-with-java/)
- [Como inserir botão ActiveX no Word – Definir legenda do botão](/words/english/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}