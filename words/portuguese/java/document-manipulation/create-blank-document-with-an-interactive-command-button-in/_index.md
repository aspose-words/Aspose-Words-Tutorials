---
category: general
date: 2026-09-18
description: Crie um documento em branco em Java e adicione um botão ActiveX. Aprenda
  como inserir um botão de comando, construir um formulário interativo e salvar um
  documento do Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- create interactive form
- add activex button
- how to insert command button
- create word document
language: pt
lastmod: 2026-09-18
og_description: Crie um documento em branco em Java e incorpore um botão de comando
  ActiveX. Siga este guia passo a passo para criar um formulário interativo e salvar
  o arquivo Word.
og_image_alt: Screenshot of a Word document showing a clickable ActiveX command button
og_title: Criar documento em branco com um botão de comando interativo no Word
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank document in Java and add an ActiveX button. Learn how
    to insert command button, build an interactive form, and save a Word document.
  headline: Create blank document with an interactive command button in Word using
    Java
  type: TechArticle
- description: Create blank document in Java and add an ActiveX button. Learn how
    to insert command button, build an interactive form, and save a Word document.
  name: Create blank document with an interactive command button in Word using Java
  steps:
  - name: 'Load the existing document: `Document doc = new Document("ExistingForm.docx");`'
    text: 'Load the existing document: `Document doc = new Document("ExistingForm.docx");`'
  - name: 'Move the builder to the desired location: `builder.moveToParagraph(5, 0);
      // 6th paragraph, first node`'
    text: 'Move the builder to the desired location: `builder.moveToParagraph(5, 0);
      // 6th paragraph, first node`'
  - name: Insert the button as shown in Step 3.
    text: Insert the button as shown in Step 3.
  - name: Adjust the button’s `Top`/`Left` based on the paragraph’s layout.
    text: Adjust the button’s `Top`/`Left` based on the paragraph’s layout.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
title: Criar documento em branco com um botão de comando interativo no Word usando
  Java
url: /pt/java/document-manipulation/create-blank-document-with-an-interactive-command-button-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar documento em branco com um botão de comando interativo no Word usando Java

Se você precisa **criar documento em branco** que contenha um botão clicável, este guia mostra exatamente como fazer isso com Aspose.Words for Java. Você aprenderá a construir um formulário interativo, adicionar um botão ActiveX e, finalmente, salvar o arquivo Word — tudo em alguns passos concisos.

Incorporar um botão de comando transforma um .docx estático em um formulário funcional que os usuários finais podem interagir diretamente dentro do Microsoft Word. Este tutorial também cobre **como inserir botão de comando**, lidando com armadilhas comuns e estendendo a solução para formulários mais complexos.

## Pré-requisitos

* Java 17 ou posterior (o código compila com JDK 17+)
* Aspose.Words for Java 23.9 ou mais recente – a biblioteca fornece `Document`, `DocumentBuilder` e `Forms2OleControl`.
* Uma IDE ou ferramenta de build (Maven/Gradle) que possa adicionar a dependência Aspose.Words.
* Conhecimento básico de sintaxe Java e conceitos de documentos Word.

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

## Etapa 1: Criar um documento em branco

A primeira operação é instanciar um novo objeto `Document`. Esse objeto representa um arquivo Word vazio pronto para receber conteúdo.

```java
// Step 1: Create a new blank document
Document doc = new Document();
```

Criar um documento em branco fornece uma tela limpa, o que é essencial quando você deseja **criar documento Word** programaticamente sem nenhum modelo pré‑existente.

## Etapa 2: Inicializar um DocumentBuilder

`DocumentBuilder` é a classe principal para adicionar texto, tabelas e controles de formulário. Ela funciona no `Document` que você acabou de criar.

```java
// Step 2: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(doc);
```

O builder mantém o ponto de inserção atual, portanto, comandos subsequentes afetam a localização correta no arquivo.

## Etapa 3: Inserir um controle de botão de comando Forms2Ole

Aspose.Words expõe a classe `Forms2OleControl` para controles ActiveX. Para **adicionar botão activex**, você solicita um tipo `COMMANDBUTTON` ao builder.

```java
// Step 3: Insert a Forms2Ole command button control
Forms2OleControl commandButton = builder.insertForms2OleControl(OleControlType.COMMANDBUTTON);
```

O método `insertForms2OleControl` insere o controle na posição atual do cursor do builder. Como o controle é um objeto ActiveX, ele funciona apenas na versão desktop do Microsoft Word, não no Word Online.

## Etapa 4: Configurar a aparência e a posição do botão

Você pode definir a legenda, o tamanho e a localização do botão usando os setters do controle. Os valores de posição são medidos em pontos (1 ponto = 1/72 polegada).

```java
// Step 4: Configure the button's appearance and position
commandButton.setCaption("Click Me");   // Text shown on the button
commandButton.setTop(100);              // Distance from the top edge of the page (points)
commandButton.setLeft(100);             // Distance from the left edge of the page (points)
commandButton.setWidth(120);            // Optional: set button width
commandButton.setHeight(30);            // Optional: set button height
```

*Por que configurar essas propriedades?* Definir `Top` e `Left` garante que o botão apareça onde você espera na página, enquanto `Caption` define o rótulo visível ao usuário. Se você omitir largura/altura, o Word atribui dimensões padrão, que podem não corresponder ao seu design.

### Dica profissional
Se você planeja adicionar vários controles, chame `builder.moveToDocumentEnd()` antes de cada inserção para evitar sobreposição de objetos.

## Etapa 5: Salvar o documento com o botão de comando incorporado

Finalmente, grave o documento no disco. A extensão do arquivo deve ser `.docx` (ou `.doc` para versões mais antigas do Word) para preservar o controle ActiveX.

```java
// Step 5: Save the document with the embedded command button
String outputPath = "C:/temp/CommandButton.docx";
doc.save(outputPath);
System.out.println("Document saved to: " + outputPath);
```

Ao abrir `CommandButton.docx` no Microsoft Word, você verá um botão rotulado **Click Me**. Clicá‑lo acionará a ação padrão do ActiveX (que, por padrão, não faz nada). Você pode posteriormente anexar uma macro ou script VBA para definir um comportamento personalizado.

## Como inserir botão de comando em um formulário existente (opcional)

Se você já tem um formulário com campos de texto e deseja **criar formulário interativo** que inclua um botão, siga estas etapas adicionais:

1. Carregue o documento existente: `Document doc = new Document("ExistingForm.docx");`
2. Mova o builder para a localização desejada: `builder.moveToParagraph(5, 0); // 6º parágrafo, primeiro nó`
3. Insira o botão como mostrado na Etapa 3.
4. Ajuste o `Top`/`Left` do botão com base no layout do parágrafo.

Essa abordagem permite enriquecer qualquer modelo Word pré‑construído com um botão ActiveX sem recriar todo o arquivo.

## Casos de borda e solução de problemas

| Situação | O que verificar | Correção recomendada |
|-----------|----------------|----------------------|
| O botão não aparece no Word | Certifique‑se de que abriu o arquivo na versão desktop do Word (Word Online remove ActiveX). | Abra o arquivo no Word 2016+ desktop. |
| Legenda está truncada | Verifique se a largura do botão é suficientemente grande para conter o texto. | Aumente `setWidth` até que a legenda caiba. |
| Salvar lança `IOException` | Confirme que o diretório de saída existe e que você tem permissões de gravação. | Crie o diretório ou execute o programa com privilégios elevados. |
| Múltiplos botões se sobrepõem | O cursor do builder pode não ter se movido após a inserção anterior. | Chame `builder.moveToDocumentEnd()` antes de inserir cada novo controle. |

## Exemplo completo executável

Abaixo está um programa Java completo e autocontido que você pode copiar, compilar e executar. Ele demonstra **criar documento em branco**, **adicionar botão activex** e **salvar documento Word** em um único fluxo.

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) {
        try {
            // 1. Create a new blank document
            Document doc = new Document();

            // 2. Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3. Insert an ActiveX command button
            Forms2OleControl commandButton = builder.insertForms2OleControl(OleControlType.COMMANDBUTTON);

            // 4. Configure button properties
            commandButton.setCaption("Click Me");
            commandButton.setTop(100);   // points from top
            commandButton.setLeft(100);  // points from left
            commandButton.setWidth(120);
            commandButton.setHeight(30);

            // 5. Save the document
            String outPath = "CommandButton.docx";
            doc.save(outPath);
            System.out.println("Document created: " + outPath);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Saída esperada**

```
Document created: CommandButton.docx
```

Abrir `CommandButton.docx` mostra uma única página com um botão rotulado **Click Me** posicionado a 100 pt da borda superior e esquerda.

## Conclusão

Agora você sabe como **criar documento em branco**, incorporar um **botão ActiveX** e transformar um arquivo Word simples em um **formulário interativo**. Ao dominar **como inserir botão de comando**, você pode estender esse padrão para adicionar caixas de seleção, caixas de combinação ou até lógica personalizada controlada por VBA.

Em seguida, considere explorar estes tópicos relacionados:

* **Criar formulário interativo** com campos de texto (`builder.insertField`)  
* **Adicionar botão activex** que executa uma macro VBA (`builder.insertOleObject`)  
* **Criar documento Word** a partir de um modelo usando `Document(docTemplatePath)`  
* Converter o .docx resultante para PDF preservando o botão (observação: o PDF renderizará o botão como uma imagem estática).

Sinta‑se à vontade para experimentar o tamanho, a posição e a legenda do botão para combinar com o design da sua UI. Boa codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Como criar campos de formulário e adicionar conteúdo usando DocumentBuilder no Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Criar Projeto Vba em Documento Word](/words/english/net/working-with-vba-macros/create-vba-project/)
- [Criar Novo Documento Word](/words/english/net/add-content-using-documentbuilder/create-new-document/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}