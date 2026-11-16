---
category: general
date: 2026-11-15
description: Edite um documento do Word programaticamente para inserir um botão de
  comando. Aprenda como adicionar o botão, definir o nome do botão de comando e criar
  um botão de formulário no Word em minutos.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- edit word document programmatically
- how to add button
- insert command button word
- create form button word
- set command button name
language: pt
lastmod: 2026-11-15
og_description: Edite documentos do Word programaticamente e insira um botão de comando.
  Este guia mostra como adicionar o botão, definir o nome do botão de comando e criar
  rapidamente um botão de formulário no Word.
og_image_alt: Screenshot of a Word document edited programmatically with a command
  button
og_title: Editar documento Word programaticamente – adicionar um botão de comando
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Edit Word document programmatically to insert a command button. Learn
    how to add button, set command button name, and create form button Word in minutes.
  headline: Edit Word document programmatically and add a command button
  type: TechArticle
- description: Edit Word document programmatically to insert a command button. Learn
    how to add button, set command button name, and create form button Word in minutes.
  name: Edit Word document programmatically and add a command button
  steps:
  - name: Expected output
    text: 'When you open the saved file:'
  - name: How to add button to a specific paragraph?
    text: '```java builder.moveToParagraph(2, true); // moves to third paragraph (0‑based
      index) Forms2OleControl btn = builder.insertForms2OleControl(); btn.setName("btnThirdParagraph");
      btn.setCaption("Click Me"); ```'
  - name: How to insert a button inside a table cell?
    text: '```java Table table = builder.startTable(); builder.insertCell(); builder.insertCell();
      builder.endTable();'
  - name: What if I need a larger button?
    text: '```java cmdBtn.setWidth(100); // width in points cmdBtn.setHeight(30);
      // height in points ```'
  - name: How to **insert command button word** using a different language (e.g.,
      C#)?
    text: 'The same logic applies; replace Java syntax with C# equivalents:'
  type: HowTo
tags:
- Word automation
- Aspose.Words
- Java
title: Editar documento Word programaticamente e adicionar um botão de comando
url: /pt/java/document-manipulation/edit-word-document-programmatically-and-add-a-command-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Editar documento Word programaticamente e adicionar um botão de comando

Se você precisa **editar documento Word programaticamente**, a maneira mais rápida é usar a API Aspose.Words. Este tutorial mostra exatamente **como adicionar botões** de controle, configurar sua legenda e **definir o nome do botão de comando** para que o documento possa atuar como um formulário simples. Ao final, você terá um *.docx* totalmente editável que contém um botão de comando funcional pronto para processamento posterior.

Você aprenderá como **inserir palavra de botão de comando**, **criar palavra de botão de formulário**, e gerenciar propriedades do botão sem abrir o Word manualmente. O único pré-requisito é um ambiente básico de desenvolvimento Java e a biblioteca Aspose.Words for Java.

## Pré-requisitos

- Java 17 ou superior (o código também funciona com Java 8+)
- Aspose.Words for Java (download em [Aspose.Words for Java](https://products.aspose.com/words/java/))
- Um documento Word existente (`input.docx`) que você deseja modificar
- Familiaridade com Maven ou Gradle para adicionar a dependência Aspose.Words

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

## Etapa 1: Carregar o documento Word

A primeira operação ao **editar documento Word programaticamente** é carregar o arquivo fonte em um objeto `Document`. Esse objeto representa todo o arquivo Word na memória, permitindo que você manipule seu conteúdo.

```java
import com.aspose.words.*;

public class WordButtonDemo {
    public static void main(String[] args) throws Exception {
        // Load the existing Word file
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **Por que isso importa:** Carregar o documento cria uma estrutura semelhante a DOM que o Aspose.Words pode percorrer e modificar. Pular esta etapa deixaria você sem um alvo para a inserção do botão.

## Etapa 2: Criar um `DocumentBuilder` para editar o documento

Um `DocumentBuilder` funciona como um cursor dentro do arquivo Word. Ele permite inserir texto, imagens e controles de formulário na posição atual.

```java
        // Initialize a builder positioned at the start of the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Dica:** Se você precisar do botão em um parágrafo específico, mova o builder primeiro com `builder.moveToParagraph(index, true);`.

## Etapa 3: Inserir um Forms2OleControl (botão de comando)

Agora respondemos à questão central **como adicionar botão** em um arquivo Word. O método `insertForms2OleControl()` cria um botão de comando *Forms2.0* legado, que é o controle mais compatível entre as versões do Word.

```java
        // Insert the command button at the builder's current cursor location
        Forms2OleControl cmdBtn = builder.insertForms2OleControl();
```

> **Caso extremo:** O controle Forms2.0 é visível apenas no *Modo de Design* do Word. Se você precisar de um botão ActiveX mais recente, considere usar `insertOleControl()` em vez disso, mas o controle legado funciona na maioria dos cenários de automação.

## Etapa 4: Configurar as propriedades do botão

Depois de inserir o controle, você pode **definir o nome do botão de comando** e **inserir palavra de botão de comando** (legenda) para torná-lo amigável ao usuário.

```java
        // Set the internal name used by automation scripts
        cmdBtn.setName("cmdSubmit");

        // Set the text that appears on the button
        cmdBtn.setCaption("Submit");
```

> **Por que essas propriedades?**  
> - `setName` fornece ao botão um identificador que VBA ou ferramentas externas podem referenciar.  
> - `setCaption` é o rótulo visível, efetivamente **criando palavra de botão de formulário** que os usuários finais clicam.

Você também pode ajustar tamanho, posição ou adicionar uma macro acessando o objeto OLE subjacente, mas esses tópicos estão fora do escopo deste guia rápido.

## Etapa 5: Salvar o documento modificado

Finalmente, persista as alterações em um novo arquivo. Esta etapa **cria palavra de botão de formulário** no documento de saída.

```java
        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

> **Resultado:** Ao abrir `output.docx` no Microsoft Word, você verá um botão rotulado “Submit”. Quando mudar o Word para *Modo de Design* (Developer → Design Mode), você pode clicar duas vezes no botão para anexar uma macro ou simplesmente usá-lo como um espaço reservado em um formulário.

### Saída esperada

Ao abrir o arquivo salvo:

- O ponto de inserção do cursor é substituído por um botão.
- O botão exibe a legenda **Submit**.
- O nome interno do botão é **cmdSubmit**, que você pode referenciar em VBA ou scripts de automação externos.

## Perguntas comuns e variações

### Como adicionar botão a um parágrafo específico?

```java
builder.moveToParagraph(2, true); // moves to third paragraph (0‑based index)
Forms2OleControl btn = builder.insertForms2OleControl();
btn.setName("btnThirdParagraph");
btn.setCaption("Click Me");
```

### Como inserir um botão dentro de uma célula de tabela?

```java
Table table = builder.startTable();
builder.insertCell();
builder.insertCell();
builder.endTable();

builder.moveToCell(0, 0, 0, 0, true); // first row, first cell
Forms2OleControl cellBtn = builder.insertForms2OleControl();
cellBtn.setCaption("Cell Button");
```

### E se eu precisar de um botão maior?

```java
cmdBtn.setWidth(100);   // width in points
cmdBtn.setHeight(30);   // height in points
```

### Como **inserir palavra de botão de comando** usando uma linguagem diferente (por exemplo, C#)?

A mesma lógica se aplica; substitua a sintaxe Java por equivalentes C#:

```csharp
Document doc = new Document("input.docx");
DocumentBuilder builder = new DocumentBuilder(doc);
Forms2OleControl btn = builder.InsertForms2OleControl();
btn.Name = "cmdSubmit";
btn.Caption = "Submit";
doc.Save("output.docx");
```

## Dicas profissionais e armadilhas

- **Dica profissional:** Sempre chame `builder.moveToDocumentEnd()` antes de inserir um botão se você quiser que ele fique no final do documento.  
- **Cuidado com:** Salvar no mesmo arquivo que você abriu pode corromper o documento se ocorrer uma exceção. Use um caminho de saída separado como mostrado.  
- **Compatibilidade:** O botão legado Forms2.0 funciona no Word 2007‑2021. Para Word na web, considere usar controles de conteúdo.  
- **Desempenho:** Carregar documentos muito grandes (>100 MB) pode consumir muita memória. Use `Document.load(InputStream, LoadOptions)` com `LoadOptions.setLoadFormat(LoadFormat.DOCX)` para limitar o uso de recursos.

## Exemplo completo em funcionamento

Abaixo está o programa Java completo, pronto para execução. Copie-o para uma classe chamada `WordButtonDemo.java`, ajuste os caminhos dos arquivos e execute `mvn compile exec:java`.

```java
import com.aspose.words.*;

public class WordButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1. Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Create a builder positioned at the start
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a command button (Forms2OleControl)
        Forms2OleControl cmdBtn = builder.insertForms2OleControl();

        // 4. Set button properties – this is where we **set command button name**
        cmdBtn.setName("cmdSubmit");   // internal identifier
        cmdBtn.setCaption("Submit");   // visible text (creates form button word)

        // 5. Save the edited document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

Execute o programa e abra `output.docx` para verificar se o botão aparece como esperado.

## Conclusão

Agora você sabe como **editar documento Word programaticamente** para **inserir palavra de botão de comando**, **criar palavra de botão de formulário**, e **definir o nome do botão de comando** usando Aspose.Words for Java. Esta abordagem elimina a edição manual, permite o processamento em lote de formulários e integra-se perfeitamente a fluxos de trabalho automatizados.

Em seguida, você pode explorar:

- Adicionar macros VBA ao botão (`cmdBtn.getOleFormat().setMacroName("MyMacro")`)  
- Usar **controles de conteúdo** para experiências de formulário mais ricas (`builder.insertCheckBox()` etc.)  
- Automatizar inserção em massa em vários documentos com um loop  

Sinta-se à vontade para experimentar o tamanho, posição e tratamento de eventos do botão para se adequar ao seu cenário específico. Feliz codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos estreitamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá-lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Como adicionar um botão de comando programaticamente em um documento Word](/words/english/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/)
- [Criar documento Word programaticamente e adicionar botão ActiveX](/words/english/net/working-with-oleobjects-and-activex/create-word-document-programmatically-and-add-activex-button/)
- [Adicionar Botão de Comando ao Documento Word com Aspose.Words – Guia Completo](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}