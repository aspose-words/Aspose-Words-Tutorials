---
category: general
date: 2026-10-16
description: Crie um documento Word em branco com Java e aprenda a adicionar um botão
  ActiveX, definir sua legenda e ajustar suas dimensões usando o Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add activex button
- set button caption
- set button dimensions
language: pt
lastmod: 2026-10-16
og_description: Crie um documento Word em branco com Java, adicione um botão ActiveX,
  defina sua legenda e estabeleça suas dimensões usando Aspose.Words.
og_image_alt: Screenshot showing a blank Word document with an ActiveX button inserted
og_title: Crie um documento Word em branco e incorpore um botão ActiveX – Guia Java
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Create a blank Word document with Java and learn how to add an ActiveX
    button, set its caption, and adjust its dimensions using Aspose.Words.
  headline: Create a blank Word document and add an ActiveX button (Java)
  type: TechArticle
tags:
- Aspose.Words
- Java
- ActiveX
title: Crie um documento Word em branco e adicione um botão ActiveX (Java)
url: /pt/java/using-document-elements/create-a-blank-word-document-and-add-an-activex-button-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crie um documento Word em branco e adicione um botão ActiveX (Java)

Se você precisa **criar um documento Word em branco** programaticamente, este guia mostra como fazer isso com Java e Aspose.Words. Você também aprenderá como **adicionar um botão ActiveX**, **definir a legenda do botão** e **definir as dimensões do botão** para que o controle tenha exatamente a aparência esperada.

Este tutorial cobre:

* Inicializar um arquivo Word vazio com Aspose.Words para Java.  
* Inserir um controle ActiveX `CommandButton`.  
* Configurar a legenda e o tamanho do botão.  
* Salvar o arquivo final `.docx`.

Você deve ter conhecimentos básicos de Java e uma versão recente da biblioteca Aspose.Words para Java (o código funciona com 23.9 e posteriores). Nenhuma dependência adicional é necessária.

![Create a blank Word document with an ActiveX button](/images/activex-button-example.png){: .align-center alt="Criar um documento Word em branco com um botão ActiveX"}

## Crie um documento Word em branco com Aspose.Words

O primeiro passo é instanciar um objeto `Document` vazio. Esse objeto representa todo o arquivo Word na memória e fornece a classe `DocumentBuilder` para edição.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // creates an empty .docx structure
        DocumentBuilder builder = new DocumentBuilder(doc);
        
        // The rest of the steps follow here...
```

**Por que isso importa:**  
Criar um documento em branco fornece uma tela limpa, evitando estilos ou seções ocultas que possam interferir nos cálculos de layout posteriores.

## Adicione um botão ActiveX ao documento

Aspose.Words permite incorporar controles ActiveX legados via a classe `Forms2OleControl`. O código a seguir insere um controle `CommandButton` na posição atual do cursor.

```java
        // Step 2: Insert an ActiveX CommandButton control
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Define the exact ActiveX class name (CommandButton)
        commandButton.setOleClassName("Forms.CommandButton.1");
```

**Dica:** O valor `setOleClassName` `"Forms.CommandButton.1"` é o ProgID do botão padrão do Microsoft Forms. Usar um ProgID diferente (por exemplo, `"Forms.CheckBox.1"`) inseriria um tipo de controle diferente.

## Defina a legenda do botão

A legenda é o texto que aparece na face do botão. Você pode alterá‑la a qualquer momento antes de salvar o documento.

```java
        // Step 3: Set the button's caption
        commandButton.setCaption("Click Me");
```

**Por que você precisa disso:**  
Os usuários só compreendem um controle quando seu propósito está claro. Definir uma legenda significativa melhora a usabilidade, especialmente quando o documento é aberto no Word no Windows.

## Defina as dimensões do botão

A posição e o tamanho são especificados em pontos (1 ponto = 1/72 polegada). Ajuste os valores para se adequar ao seu layout.

```java
        // Step 4: Define button size and location
        commandButton.setLeft(100);    // distance from the left edge of the page
        commandButton.setTop(200);     // distance from the top edge of the page
        commandButton.setWidth(120);   // width of the button
        commandButton.setHeight(30);   // height of the button
```

**Variações comuns:**

| Cenário | Ajuste |
|----------|------------|
| Botão maior para telas sensíveis ao toque | Aumentar `setWidth` e `setHeight` proporcionalmente |
| Botão centralizado na página | Calcular `left = (pageWidth - width) / 2` |
| Vários botões em uma coluna | Incrementar `setTop` para cada novo botão |

## Salve o documento contendo o botão ActiveX

Finalmente, grave o documento no disco. O formato `.docx` preserva o controle ActiveX para as versões Windows do Microsoft Word.

```java
        // Step 5: Save the document
        doc.save("ActiveXCommandButton.docx");
    }
}
```

**Resultado esperado:**  
Abrir `ActiveXCommandButton.docx` no Word (Windows) exibe uma página em branco com um botão clicável rotulado **Click Me** posicionado a 100 pt da margem esquerda e 200 pt da margem superior.

## Exemplo completo e executável

Copie a classe completa abaixo para sua IDE, adicione o JAR do Aspose.Words para Java ao classpath do projeto e execute‑a.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control
        Forms2OleControl commandButton = builder.insertForms2OleControl();
        commandButton.setOleClassName("Forms.CommandButton.1");

        // Set button caption
        commandButton.setCaption("Click Me");

        // Set button dimensions and position
        commandButton.setLeft(100);    // points from left edge
        commandButton.setTop(200);     // points from top edge
        commandButton.setWidth(120);   // width in points
        commandButton.setHeight(30);   // height in points

        // Save the document
        doc.save("ActiveXCommandButton.docx");
    }
}
```

Executar o programa gera `ActiveXCommandButton.docx` no diretório de trabalho. Abra‑o com o Microsoft Word (Windows) para verificar se o botão aparece exatamente como configurado.

## Por que esta abordagem é recomendada

* **Simplicidade:** Apenas a API principal do Aspose.Words é usada; não há necessidade de interop COM ou bibliotecas adicionais.  
* **Portabilidade:** O código roda em qualquer plataforma que suporte Java, embora o controle ActiveX funcione apenas nas versões Windows do Word.  
* **Manutenibilidade:** Todas as propriedades (legenda, dimensões, posição) são definidas por meio de métodos claros e auto‑documentáveis, facilitando ajustes futuros.

## Armadilhas comuns e como evitá‑las

| Armadilha | Resolução |
|-----------|------------|
| O botão não aparece no Word em macOS ou Linux | Controles ActiveX são apenas para Windows. Use um controle diferente (por exemplo, um controle de conteúdo) para documentos multiplataforma. |
| A legenda é truncada | Garanta que a largura do botão seja suficiente para o texto; aumente `setWidth` ou use uma legenda mais curta. |
| O botão sobrepõe outro conteúdo | Ajuste os valores `setTop` e `setLeft`, ou insira um novo parágrafo antes do controle para dar‑lhe seu próprio espaço. |

## Próximos passos

Agora que você pode **criar um documento Word em branco**, **adicionar um botão ActiveX**, **definir a legenda do botão** e **definir as dimensões do botão**, você pode explorar:

* Adicionar código de tratamento de eventos via macros VBA (requer a incorporação de um módulo de macro).  
* Inserir múltiplos controles em um layout de tabela para documentos semelhantes a formulários.  
* Usar as APIs **FormField** do Aspose.Words para soluções de formulário multiplataforma.

Experimente diferentes tamanhos, posições e legendas para adequar ao design específico do seu documento. Boa codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Criar documento Word Java – Adicionar forma retangular com efeito de sombra](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Como criar campos de formulário e adicionar conteúdo usando DocumentBuilder no Aspose.Words para Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Adicionar marca d'água a um documento usando Aspose.Words para Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}