---
category: general
date: 2026-10-07
description: Criar botão de comando ActiveX em Java e adicionar programaticamente
  o botão de comando a documentos do Word. Aprenda como definir as posições esquerda
  e superior do botão.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex command button
- programmatically add command button
- how to set button left top
language: pt
lastmod: 2026-10-07
og_description: Crie um botão de comando ActiveX em Java para incorporar controles
  interativos em seus documentos do Word. Aprenda como adicionar programaticamente
  o botão de comando, definir sua posição e personalizar sua aparência.
og_image_alt: Screenshot showing a created ActiveX command button in a Java‑generated
  Word document
og_title: Criar botão de comando ActiveX em Java – guia passo a passo
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Create ActiveX command button in Java and programmatically add command
    button to Word docs. Learn how to set button left top positions.
  headline: How to create ActiveX command button in Java
  type: TechArticle
- description: Create ActiveX command button in Java and programmatically add command
    button to Word docs. Learn how to set button left top positions.
  name: How to create ActiveX command button in Java
  steps:
  - name: How to set button left top
    text: Positioning the button is where the secondary keyword **how to set button
      left top** becomes relevant. The `setLeft` and `setTop` methods accept values
      measured in points (1 point = 1/72 in).
  - name: Adding multiple buttons
    text: If you need several buttons, repeat **Step 2** and **Step 3** for each control.
      Remember to adjust `setLeft` and `setTop` so the buttons don’t overlap.
  - name: Changing button behavior
    text: 'ActiveX buttons can run VBA macros when clicked. To attach a macro, set
      the `setOnAction` property with the macro name:'
  - name: Compatibility notes
    text: '- The button works only in desktop versions of Word that support ActiveX
      (e.g., Word for Windows). It will appear as a static image in Word for Mac or
      online editors. - If you target a mixed environment, consider using a **content
      control** (`RichTextContentControl`) instead of an ActiveX control.'
  - name: Next steps
    text: '- Explore other ActiveX controls such as `Forms.TextBox.1` or `Forms.CheckBox.1`.
      - Combine multiple controls with a VBA module to implement full‑featured forms.
      - Replace ActiveX with content controls if you need cross‑platform compatibility.'
  type: HowTo
tags:
- ActiveX
- Java
- Aspose.Words
title: Como criar um botão de comando ActiveX em Java
url: /pt/java/using-document-elements/how-to-create-activex-command-button-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como criar um botão de comando ActiveX em Java

Se você precisa **criar um botão de comando ActiveX** em um documento Word usando Java, este guia mostra exatamente como fazer. Você verá um exemplo completo e executável que **adiciona programaticamente um botão de comando**, posiciona-o com `setLeft` e `setTop`, e salva o resultado como um arquivo `.docx`.

Incorporar um botão interativo permite que você crie formulários, automatize fluxos de trabalho ou colete entradas do usuário diretamente dentro de um arquivo Word. As etapas abaixo cobrem tudo, desde a configuração do projeto até a verificação final, para que você possa copiar o código para seu próprio projeto sem perder nenhum detalhe.

## Pré-requisitos

Antes de começar, certifique‑se de que você tem:

- JDK 17 ou mais recente instalado  
- Maven 3.8+ (ou sua ferramenta de construção preferida)  
- Aspose.Words for Java 23.9 ou posterior – a biblioteca que fornece `DocumentBuilder` e suporte a controles OLE  
- Familiaridade básica com a sintaxe Java e conceitos orientados a objetos  

Se você estiver usando Maven, adicione a dependência ao seu `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

> **Dica:** Use a versão mais recente do Aspose.Words para se beneficiar de correções de bugs e novos recursos OLE.

## Etapa 1: Criar um novo documento vazio e um DocumentBuilder

A primeira etapa para **criar um botão de comando ActiveX** é instanciar um `Document` em branco e um `DocumentBuilder`. O builder fornece uma API fluente para inserir conteúdo, incluindo controles OLE.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` representa o arquivo Word na memória, enquanto `DocumentBuilder` atua como um cursor que permite posicionar elementos exatamente onde você precisar.

## Etapa 2: Inserir um controle de botão de comando OLE

Controles ActiveX são inseridos como objetos OLE. Aspose.Words fornece a classe `Forms2OleControl` para esse propósito.

```java
        // Step 2: Insert an OLE command button control into the document
        Forms2OleControl commandButton = builder.insertForms2OleControl();
```

Ao chamar `insertForms2OleControl()`, o Aspose cria automaticamente uma forma de espaço reservado que hospedará o botão ActiveX.

## Etapa 3: Configurar as propriedades do botão

Agora você **adiciona programaticamente detalhes do botão de comando** como seu ProgID, legenda e tamanho. O ProgID mais comum para um botão de comando é `"Forms.CommandButton.1"`.

```java
        // Step 3: Configure the button's properties (type, position, size, caption)
        commandButton.setProgId("Forms.CommandButton.1"); // ActiveX class identifier
        commandButton.setCaption("Click Me");            // Text shown on the button
        commandButton.setWidth(80);                      // Width in points
        commandButton.setHeight(30);                     // Height in points
```

### Como definir a posição esquerda e superior do botão

Posicionar o botão é onde a palavra‑chave secundária **how to set button left top** se torna relevante. Os métodos `setLeft` e `setTop` aceitam valores medidos em pontos (1 ponto = 1/72 pol).

```java
        // Position the button 100 points from the left margin and 150 points from the top
        commandButton.setLeft(100);   // Horizontal offset
        commandButton.setTop(150);    // Vertical offset
```

Ajuste esses números para se adequar ao seu layout. Por exemplo, para alinhar o botão com uma célula de tabela, calcule as coordenadas da célula e passe‑as para `setLeft`/`setTop`.

## Etapa 4: Salvar o documento

Finalmente, grave o documento no disco. O arquivo conterá o botão ActiveX pronto para interação quando aberto no Microsoft Word.

```java
        // Step 4: Save the document containing the button
        doc.save("CommandButton.docx");
        System.out.println("Document saved successfully.");
    }
}
```

Executar o método `main` produz `CommandButton.docx`. Abra o arquivo no Word, habilite o conteúdo se solicitado, e você verá um botão clicável rotulado **Click Me** posicionado nas coordenadas especificadas.

![Criar botão de comando ActiveX em Java](/images/activex-button-screenshot.png){.center width=600 alt="Captura de tela de criação de botão de comando ActiveX em Java mostrando o botão dentro do documento Word"}

## Variações comuns e casos de borda

### Adicionando vários botões

Se você precisar de vários botões, repita **Etapa 2** e **Etapa 3** para cada controle. Lembre‑se de ajustar `setLeft` e `setTop` para que os botões não se sobreponham.

### Alterando o comportamento do botão

Botões ActiveX podem executar macros VBA quando clicados. Para anexar uma macro, defina a propriedade `setOnAction` com o nome da macro:

```java
commandButton.setOnAction("MyMacro");
```

Certifique‑se de que o documento de destino contém o módulo VBA correspondente; caso contrário, o Word exibirá um erro.

### Notas de compatibilidade

- O botão funciona apenas nas versões desktop do Word que suportam ActiveX (por exemplo, Word para Windows). Aparecerá como uma imagem estática no Word para Mac ou em editores online.  
- Se você direcionar um ambiente misto, considere usar um **controle de conteúdo** (`RichTextContentControl`) em vez de um controle ActiveX.

## Código-fonte completo para referência

Abaixo está o exemplo completo e autocontido que você pode copiar para um novo projeto Maven e executar imediatamente.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an OLE command button control
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Configure the button
        commandButton.setProgId("Forms.CommandButton.1");
        commandButton.setCaption("Click Me");
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // How to set button left top – position the control
        commandButton.setLeft(100);   // Horizontal offset in points
        commandButton.setTop(150);    // Vertical offset in points

        // Save the resulting document
        doc.save("CommandButton.docx");
        System.out.println("Document saved successfully.");
    }
}
```

**Saída esperada:** Após a execução, você encontrará `CommandButton.docx` no diretório de trabalho do seu projeto. Abrir o arquivo no Microsoft Word mostra um botão na localização especificada com a legenda “Click Me”.

## Conclusão

Agora você sabe como **criar um botão de comando ActiveX** em Java, **adicionar programaticamente um botão de comando** a um documento Word, e controlar precisamente seu layout usando os métodos **how to set button left top**. Essa técnica abre a porta para formulários Word ricos e interativos que podem disparar macros, iniciar aplicações externas ou coletar entradas do usuário diretamente dentro do documento.

### Próximos passos

- Explore outros controles ActiveX como `Forms.TextBox.1` ou `Forms.CheckBox.1`.  
- Combine vários controles com um módulo VBA para implementar formulários completos.  
- Substitua ActiveX por controles de conteúdo se precisar de compatibilidade multiplataforma.  

Sinta‑se à vontade para experimentar tamanho, legenda e posicionamento para combinar com o design da sua UI. Se encontrar problemas, verifique novamente se a versão do Aspose.Words que você está usando suporta controles OLE, e confirme que as configurações de segurança do Word permitem a execução de ActiveX. Feliz codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Incorporando objetos OLE e controles ActiveX em documentos Word](/words/english/python-net/document-structure-and-content-manipulation/document-ole-objects-active-x/)
- [Como criar campos de formulário e adicionar conteúdo usando DocumentBuilder no Aspose.Words para Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Criar forma retangular no Word com Java – Guia completo](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}