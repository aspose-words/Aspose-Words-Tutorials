---
category: general
date: 2026-10-16
description: Aprenda a agrupar formas no Word usando Java. Este tutorial mostra como
  adicionar uma forma retangular, definir o tamanho e as dimensões da forma e salvar
  o documento.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- set shape size
- set shape dimensions
- rectangle shape code
language: pt
lastmod: 2026-10-16
og_description: Agrupe formas no Word usando Java. Adicione uma forma retangular,
  defina o tamanho e as dimensões da forma e crie documentos profissionais programaticamente.
og_image_alt: Screenshot of a Word document showing grouped rectangle and ellipse
  shapes created with Java
og_title: Agrupar formas no Word com Java – guia passo a passo
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Learn how to group shapes in Word using Java. This tutorial shows how
    to add rectangle shape, set shape size and dimensions, and save the document.
  headline: How to group shapes in Word with Java – complete guide
  type: TechArticle
- description: Learn how to group shapes in Word using Java. This tutorial shows how
    to add rectangle shape, set shape size and dimensions, and save the document.
  name: How to group shapes in Word with Java – complete guide
  steps:
  - name: Expected output
    text: '- A file named **GroupShapeDemo.docx** appears in the project folder. -
      Opening the file in Word shows two shapes (a rectangle and an ellipse) that
      are grouped together. - Dragging either shape moves the whole group, confirming
      that **group shapes in word** works as intended.'
  - name: Pro tip
    text: 'When you need to **set shape dimensions** based on dynamic data (e.g.,
      a barcode length), calculate the width/height in points first:'
  - name: What’s next?
    text: '- Explore **add rectangle shape** variations such as rounded corners (`ShapeType.RECTANGLE`
      with `setCornerRadius`). - Combine **group shapes in word** with tables or charts
      for richer documents. - Look into the Aspose.Words API for **text wrapping**
      (`shape.setWrapType(WrapType.SQUARE)`) to control'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Como agrupar formas no Word com Java – guia completo
url: /pt/java/images-shapes/how-to-group-shapes-in-word-with-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como agrupar formas no Word com Java – guia completo

Se você precisa **agrupar formas no Word** programaticamente, este tutorial oferece uma solução pronta‑para‑executar. Você verá como **adicionar forma retangular**, ajustar seu tamanho, definir as dimensões da forma e, finalmente, salvar um arquivo DOCX que contém um retângulo agrupado e uma elipse.

Agrupar formas no Word é útil para criar diagramas complexos, gerar componentes gráficos reutilizáveis ou simplesmente manter objetos relacionados juntos quando o documento for editado posteriormente. O código usa a biblioteca Aspose.Words for Java, que funciona com qualquer JDK recente e não requer a instalação do Microsoft Word.

## Pré‑requisitos

Antes de começar, certifique‑se de que você tem:

| Requisito | Motivo |
|-----------|--------|
| Java 17 (ou superior) | A biblioteca tem como alvo runtimes Java modernos. |
| Aspose.Words for Java (versão mais recente) | Fornece as classes `Document`, `DocumentBuilder`, `GroupShape` e `Shape` usadas no exemplo. |
| Uma IDE ou ferramenta de build (Maven/Gradle) | Para compilar e executar o exemplo. |
| Conhecimento básico de sintaxe Java | Necessário para entender o fluxo do código. |

Adicione a dependência do Aspose.Words ao seu projeto. Para Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version> <!-- Use the latest version -->
</dependency>
```

Ou para Gradle:

```gradle
implementation 'com.aspose:aspose-words:23.10'
```

## Visão geral da solução

O tutorial segue um padrão claro de **problema → solução → explicação**:

1. **Criar um novo documento Word** e obter um `DocumentBuilder`.  
2. **Inserir um contêiner `GroupShape`** que armazenará várias formas.  
3. **Adicionar um retângulo**, definir sua largura/altura (etapa **definir tamanho da forma**), e anexá‑lo ao grupo.  
4. **Adicionar uma elipse**, posicioná‑la dentro do mesmo grupo e também definir suas dimensões.  
5. **Salvar** o documento no disco.

Cada passo inclui o **porquê** por trás do código, para que você entenda o que a API faz e como pode adaptá‑la a outros cenários.

## Etapa 1: Criar o documento e um DocumentBuilder

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to work with it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Por que isso importa:** `Document` representa todo o arquivo DOCX, enquanto `DocumentBuilder` é um auxiliar que permite inserir conteúdo sem lidar com o gerenciamento de nós de baixo nível. Criá‑los primeiro fornece uma tela limpa para todas as operações de forma subsequentes.

## Etapa 2: Inserir um contêiner GroupShape

```java
        // Step 2: Insert a GroupShape container that will hold multiple shapes
        GroupShape groupShape = builder.insertGroupShape();
```

Um `GroupShape` funciona como uma **pasta** para objetos de desenho. Quando você move, gira ou exclui o grupo, todas as formas filhas seguem automaticamente. Este é o núcleo de **agrupamento de formas no Word**.

## Etapa 3: Adicionar uma forma retangular – o código da forma retangular

```java
        // Step 3: Create a rectangle, set its size, and add it to the group
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // set shape width in points
        rectangleShape.setHeight(50);   // set shape height in points
        groupShape.appendChild(rectangleShape);
```

- **add rectangle shape** – O construtor `Shape` recebe `ShapeType.RECTANGLE`, que indica ao Aspose.Words que deve renderizar um contorno retangular.  
- **set shape size** – `setWidth` e `setHeight` definem as **dimensões da forma** em pontos (1 pt = 1/72 in). Esta é a forma mais comum de controlar o tamanho visual.  
- **Why we use `appendChild`** – Ele anexa o retângulo ao `GroupShape` para que ele se mova junto com o grupo.

## Etapa 4: Adicionar uma elipse e posicioná‑la dentro do grupo

```java
        // Step 4: Create an ellipse, set its size and position inside the group, then add it
        Shape ellipseShape = new Shape(document, ShapeType.ELLIPSE);
        ellipseShape.setWidth(80);      // set shape width
        ellipseShape.setHeight(80);     // set shape height (making it a circle)
        ellipseShape.setLeft(120);      // position relative to the group container
        groupShape.appendChild(ellipseShape);
```

A elipse demonstra **definir dimensões da forma** além de um simples retângulo. Ao chamar `setLeft`, controlamos o deslocamento horizontal dentro do grupo, o que é útil ao organizar múltiplos objetos.

## Etapa 5: Salvar o documento

```java
        // Step 5: Save the document with the grouped shapes
        document.save("GroupShapeDemo.docx");
    }
}
```

Ao abrir *GroupShapeDemo.docx* no Microsoft Word, você verá um retângulo e uma elipse bloqueados juntos dentro de um único grupo. Selecionar qualquer forma selecionará todo o grupo — exatamente o que se espera ao **agrupar formas no Word**.

## Exemplo completo, executável

Juntando todas as peças, aqui está o arquivo‑fonte completo que você pode copiar para sua IDE:

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a GroupShape that will hold the rectangle and ellipse
        GroupShape groupShape = builder.insertGroupShape();

        // Add a rectangle (add rectangle shape) and define its size (set shape size)
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // width in points
        rectangleShape.setHeight(50);   // height in points
        groupShape.appendChild(rectangleShape);

        // Add an ellipse, set its dimensions, and position it inside the group
        Shape ellipseShape = new Shape(document, ShapeType.ELLIPSE);
        ellipseShape.setWidth(80);
        ellipseShape.setHeight(80);
        ellipseShape.setLeft(120);      // horizontal offset relative to the group
        groupShape.appendChild(ellipseShape);

        // Save the document to the local file system
        document.save("GroupShapeDemo.docx");
    }
}
```

### Saída esperada

- Um arquivo chamado **GroupShapeDemo.docx** aparece na pasta do projeto.  
- Ao abrir o arquivo no Word, são exibidas duas formas (um retângulo e uma elipse) que estão agrupadas.  
- Arrastar qualquer forma move todo o grupo, confirmando que **agrupar formas no Word** funciona como esperado.

## Variações comuns e casos de borda

| Cenário | O que mudar | Por quê |
|----------|--------------|--------|
| **Tipos de forma diferentes** (ex.: triângulo) | Use `ShapeType.TRIANGLE` ou qualquer outro valor enum ao construir `Shape`. | Permite criar diagramas mais complexos. |
| **Definir cor de preenchimento** | Chame `shape.getFillColor().setColor(Color.BLUE);` após criar a forma. | Melhora a aparência visual sem afetar o agrupamento. |
| **Rotacionar o grupo** | `groupShape.setRotationAngle(45);` | Rotaciona todas as formas filhas juntas, útil para ícones. |
| **Adicionar texto dentro de uma forma** | `shape.appendChild(new Paragraph(document));` então adicione um `Run` com texto. | Faz a forma agir como um rótulo ou balão de chamada. |
| **Salvar em um stream** | `ByteArrayOutputStream out = new ByteArrayOutputStream(); document.save(out, SaveFormat.DOCX);` | Útil para serviços web que retornam o documento diretamente. |

### Dica profissional

Quando precisar **definir dimensões da forma** com base em dados dinâmicos (ex.: comprimento de código de barras), calcule a largura/altura em pontos primeiro:

```java
double inches = 2.5;
int points = (int)(inches * 72); // 1 inch = 72 points
shape.setWidth(points);
```

Isso evita valores codificados e mantém seu código adaptável.

## Conclusão

Agora você sabe como **agrupar formas no Word** usando Java, como **adicionar forma retangular**, e como **definir tamanho da forma** e **definir dimensões da forma** com código conciso e pronto para produção. Seguindo os passos acima, você pode criar grupos gráficos reutilizáveis, incorporá‑los em relatórios automatizados ou construir ferramentas de diagramas personalizadas sem nunca abrir o Word manualmente.

### O que vem a seguir?

- Explore variações de **add rectangle shape** como cantos arredondados (`ShapeType.RECTANGLE` com `setCornerRadius`).  
- Combine **agrupamento de formas no Word** com tabelas ou gráficos para documentos mais ricos.  
- Consulte a API Aspose.Words para **text wrapping** (`shape.setWrapType(WrapType.SQUARE)`) a fim de controlar como o texto ao redor interage com seus gráficos agrupados.

Sinta‑se à vontade para experimentar, adaptar o **código da forma retangular**, e compartilhar seus resultados.

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}