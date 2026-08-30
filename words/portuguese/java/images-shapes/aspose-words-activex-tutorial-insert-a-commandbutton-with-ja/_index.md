---
category: general
date: 2026-08-07
description: O tutorial Aspose.Words ActiveX mostra como adicionar um controle CommandButton
  a um documento Word usando Java. Aprenda o código completo, a configuração e as
  etapas de salvamento.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose words activex tutorial
- aspose.words java
- activeX control java
- documentbuilder insert control
- forms2olecontrol usage
language: pt
lastmod: 2026-08-07
og_description: O tutorial Aspose.Words ActiveX explica como incorporar um controle
  ActiveX CommandButton em um documento Word usando Java. Siga o exemplo completo
  para criar, configurar e salvar o documento.
og_image_alt: Screenshot of a Word document with a CommandButton added via Aspose.Words
  ActiveX tutorial
og_title: Tutorial Aspose.Words ActiveX – Guia passo a passo em Java
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Aspose.Words ActiveX tutorial shows how to add a CommandButton control
    to a Word document using Java. Learn the full code, configuration, and saving
    steps.
  headline: Aspose.Words ActiveX tutorial – insert a CommandButton with Java
  type: TechArticle
- description: Aspose.Words ActiveX tutorial shows how to add a CommandButton control
    to a Word document using Java. Learn the full code, configuration, and saving
    steps.
  name: Aspose.Words ActiveX tutorial – insert a CommandButton with Java
  steps:
  - name: Initialize a `Document` and `DocumentBuilder`.
    text: Initialize a `Document` and `DocumentBuilder`.
  - name: Insert a `Forms2OleControl` of type `COMMAND_BUTTON`.
    text: Insert a `Forms2OleControl` of type `COMMAND_BUTTON`.
  - name: Set the button’s name, caption, size, and position.
    text: Set the button’s name, caption, size, and position.
  - name: Save the document as a .docx file that contains the ActiveX control.
    text: Save the document as a .docx file that contains the ActiveX control.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
title: Tutorial Aspose.Words ActiveX – inserir um botão de comando com Java
url: /pt/java/images-shapes/aspose-words-activex-tutorial-insert-a-commandbutton-with-ja/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tutorial Aspose.Words ActiveX – inserir um CommandButton com Java

Se você precisar incorporar um controle ActiveX em um arquivo Word, este **tutorial Aspose.Words ActiveX** o guiará por todo o processo. Você verá como criar um documento em branco, inserir um CommandButton, definir suas propriedades e salvar o resultado — tudo com código Java puro.

O exemplo usa a API Aspose.Words for Java, que elimina a necessidade do Microsoft Office no servidor de compilação. Ao final deste guia você poderá gerar arquivos .docx que contêm controles CommandButton totalmente funcionais, prontos para uso em ambientes Windows.

## Pré-requisitos

- Java Development Kit (JDK) 8 ou mais recente instalado.
- Maven ou outra ferramenta de build para gerenciar dependências.
- Uma licença Aspose.Words for Java (ou uma chave de avaliação temporária) para evitar marcas d'água de avaliação.
- Familiaridade básica com a sintaxe Java e programação orientada a objetos.

> **Dica profissional:** Adicione a dependência Maven do Aspose.Words ao seu `pom.xml` para que a IDE resolva as classes automaticamente:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest version -->
</dependency>
```

## Etapa 1: Criar um novo documento em branco e um `DocumentBuilder`

A classe `Document` representa o arquivo Word na memória, enquanto `DocumentBuilder` fornece uma API fluente para editar o documento. Inicializar ambos os objetos prepara o documento para modificações posteriores.

```java
import com.aspose.words.*;

public class ActiveXDemo {
    public static void main(String[] args) throws Exception {
        // Create an empty Word document
        Document document = new Document();

        // DocumentBuilder lets you add text, tables, and controls
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Por que isso importa:**  
`DocumentBuilder` acompanha a posição atual do cursor, de modo que qualquer operação de inserção subsequente — como adicionar um controle — aparece exatamente onde você pretende.

## Etapa 2: Inserir um controle ActiveX CommandButton

Aspose.Words expõe `Forms2OleControl` para objetos ActiveX. O método `insertForms2OleControl` requer o tipo de controle, que você especifica através da enumeração `Forms2OleControlType`.

```java
        // Insert a CommandButton ActiveX control at the current cursor location
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
```

**Explicação:**  
O controle inserido é um objeto baseado em COM que o Word renderizará como um botão clicável quando o documento for aberto em um ambiente Windows.

## Etapa 3: Configurar as propriedades do botão

Após a inserção, você pode ajustar o nome, a legenda, o tamanho e a posição do botão. Essas propriedades afetam como o controle aparece e se comporta dentro do Word.

```java
        // Set the logical name used by VBA or external scripts
        commandButton.setName("cmdSubmit");

        // Text displayed on the button face
        commandButton.setCaption("Submit");

        // Position the button 100 points from the left margin and 150 points from the top
        commandButton.setLeft(100);
        commandButton.setTop(150);

        // Define the button’s dimensions (width × height) in points
        commandButton.setWidth(80);
        commandButton.setHeight(30);
```

**Por que essas configurações são importantes:**  

- **Name** – Permite que macros VBA referenciem o controle (`ActiveDocument.Forms("cmdSubmit")`).
- **Caption** – Determina o rótulo visível que os usuários clicam.
- **Left / Top** – Controla a colocação em relação às margens da página.
- **Width / Height** – Garante um tamanho visual consistente em diferentes resoluções de tela.

## Etapa 4: Salvar o documento

Chamar `save` grava a representação em memória em um arquivo físico. Você pode escolher qualquer formato suportado (`.docx`, `.doc`, `.pdf`, etc.). Para este tutorial, mantemos o formato nativo do Word.

```java
        // Persist the document with the embedded ActiveX control
        document.save("output/ActiveXDemo.docx");
    }
}
```

**Resultado:**  
Abrir `ActiveXDemo.docx` no Microsoft Word exibe um CommandButton rotulado **Submit** posicionado nas coordenadas especificadas. Clicar no botão aciona o comportamento padrão (nenhum código VBA anexado por padrão).

## Código-fonte completo

Juntando as peças, o programa completo e executável fica assim:

```java
import com.aspose.words.*;
import com.aspose.words.forms.*;

public class ActiveXDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a CommandButton ActiveX control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // Step 3: Configure the button's properties
        commandButton.setName("cmdSubmit");
        commandButton.setCaption("Submit");
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // Step 4: Save the document with the ActiveX control
        document.save("output/ActiveXDemo.docx");
    }
}
```

### Saída esperada

- Um arquivo chamado **ActiveXDemo.docx** localizado na pasta `output`.
- Ao ser aberto no Microsoft Word (Windows), o documento mostra um botão **Submit** clicável na posição definida.
- O botão pode ser selecionado, movido ou vinculado a código VBA via a interface do Word (Developer → Properties).

## Lidando com variações comuns

| Cenário | Ajuste |
|----------|------------|
| **Save as .doc** (formato legado) | `document.save("ActiveXDemo.doc", SaveFormat.DOC);` |
| **Adicionar um manipulador de evento** | O Word não expõe eventos ActiveX através do Aspose.Words. Você deve adicionar código VBA manualmente após o documento ser gerado. |
| **Múltiplos controles** | Repita o bloco de inserção/configuração com diferentes valores de `setName` e `setCaption`. |
| **Tipo de controle diferente (ex.: CheckBox)** | Use `Forms2OleControlType.CHECKBOX` na chamada `insertForms2OleControl`. |
| **Plataformas não Windows** | Controles ActiveX são renderizados apenas no Word para Windows. Para soluções multiplataforma, considere controles de conteúdo (`StructuredDocumentTag`). |

## Melhores práticas e armadilhas

- **License early** – Registre sua licença Aspose.Words antes de criar o `Document` para evitar prompts de avaliação.
- **Coordinate system** – As posições são medidas em pontos (1 pt = 1/72 in). Converta de pixels ou centímetros se o design da sua UI usar essas unidades.
- **File paths** – Use caminhos absolutos ou a API `Paths` do Java para evitar `FileNotFoundException` quando o diretório de saída não existir.
- **Thread safety** – `Document` e `DocumentBuilder` não são seguros para threads. Crie instâncias separadas por thread se gerar documentos em paralelo.
- **Testing** – Verifique o documento gerado na versão alvo do Word (ex.: Word 2016, Word 365) pois versões mais antigas podem exibir controles ActiveX de forma diferente.

## Conclusão

Este **tutorial Aspose.Words ActiveX** demonstra como adicionar programaticamente um controle CommandButton a um documento Word usando Java. Você aprendeu como:

1. Inicializar um `Document` e um `DocumentBuilder`.
2. Inserir um `Forms2OleControl` do tipo `COMMAND_BUTTON`.
3. Definir o nome, a legenda, o tamanho e a posição do botão.
4. Salvar o documento como um arquivo .docx que contém o controle ActiveX.

A partir daqui você pode explorar tipos de controle adicionais, automatizar a injeção de macros VBA, ou combinar controles ActiveX com outros recursos do Aspose.Words, como mesclagem de correspondência e controles de conteúdo. Experimente diferentes layouts e integre os documentos gerados ao seu pipeline de relatórios maior baseado em Java.

---

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Usando objetos OLE e controles ActiveX no Aspose.Words para Java](/words/english/java/using-document-elements/using-ole-objects-and-activex/)
- [Como criar campos de formulário e adicionar conteúdo usando DocumentBuilder no Aspose.Words para Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Converter Word para RTF com tutorial Aspose.Words para Java](/words/english/java/document-loading-and-saving/saving-documents-as-rtf-format/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}