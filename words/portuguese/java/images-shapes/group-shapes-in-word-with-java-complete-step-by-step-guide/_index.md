---
category: general
date: 2026-08-01
description: Agrupe formas no Word com Java usando Aspose.Words. Aprenda como agrupar
  formas e inserir rapidamente uma forma retangular com um exemplo de código completo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- how to group shapes
- insert rectangle shape
- Aspose.Words Java
- shape grouping tutorial
- Word document automation
language: pt
lastmod: 2026-08-01
og_description: Agrupar formas no Word usando Java. Este guia mostra como agrupar
  formas, inserir forma de retângulo e salvar um DOCX com Aspose.Words.
og_image_alt: Screenshot of grouped shapes in a Word document created with Java
og_title: Agrupar Formas no Word com Java – Guia Completo de Programação
schemas:
- author: Aspose
  dateModified: '2026-08-01'
  description: Group shapes in Word with Java using Aspose.Words. Learn how to group
    shapes and insert rectangle shape quickly with a full code example.
  headline: Group Shapes in Word with Java – Complete Step-by-Step Guide
  type: TechArticle
- description: Group shapes in Word with Java using Aspose.Words. Learn how to group
    shapes and insert rectangle shape quickly with a full code example.
  name: Group Shapes in Word with Java – Complete Step-by-Step Guide
  steps:
  - name: 1. Can I group more than two shapes?
    text: 'Absolutely. Just pass a larger array to `insertGroupShape`:'
  - name: 2. What if I need to change the group’s position after creation?
    text: 'Use the group’s `setLeft` and `setTop` methods, just like any other shape:'
  - name: 3. How do I apply a border or fill to the whole group?
    text: The group itself can have formatting, but it doesn’t affect the children
      directly. If you want a common border, wrap the shapes in a rectangle shape
      first, then group everything. Alternatively, iterate over each child shape and
      set the same `fillColor` or `strokeWeight`.
  - name: 4. Does `setHidden(true)` affect printing?
    text: Hidden shapes are **not** printed by default in Word, which can be useful
      for watermarks or template markers. If you need the shape to print but stay
      invisible on screen, you’ll have to use a different approach (e.g., set its
      opacity to 0%).
  type: HowTo
tags:
- Aspose.Words
- Java
- Word Automation
title: Agrupar formas no Word com Java – Guia completo passo a passo
url: /pt/java/images-shapes/group-shapes-in-word-with-java-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Agrupar Formas no Word com Java – Guia Completo Passo a Passo

Se você precisa **agrupar formas no Word** usando Java, este guia tem tudo o que você precisa. Seja para criar um gerador de relatórios ou um mecanismo de templates dinâmico, agrupar formas deixa seus documentos mais polidos e mantém os gráficos relacionados juntos.

Nos próximos minutos você verá exatamente **como agrupar formas** e **inserir objetos de forma retangular** com Aspose.Words, além de algumas dicas práticas que evitam armadilhas comuns. Pronto para transformar aqueles retângulos e elipses soltos em um grupo organizado? Vamos lá.

## O Que Este Tutorial Cobre

* Os pré‑requisitos mínimos (Java 17+, Aspose.Words 24.10 ou superior).  
* Um programa Java completo e executável que cria um documento Word, insere um retângulo e uma elipse, os agrupa, oculta o grupo se desejar e salva o arquivo.  
* Por que cada chamada de API importa, não apenas o que ela faz.  
* Tratamento de casos extremos para versões mais antigas do Aspose.Words e para agrupar mais de duas formas.  
* Saída esperada e uma forma rápida de verificar o resultado.

Ao final, você poderá inserir este trecho em qualquer projeto Java e começar a agrupar formas no Word sem precisar vasculhar documentação espalhada.

---

## Pré‑requisitos

| Requisito | Por que é importante |
|-----------|----------------------|
| **Java 17+** | Recursos modernos da linguagem e melhor desempenho. |
| **Aspose.Words for Java 24.10+** | O método `setHidden` usado mais adiante só existe a partir desta versão. |
| **Um build Maven ou Gradle** | Torna o gerenciamento de dependências simples. |
| **Uma IDE (IntelliJ, Eclipse, VS Code)** | Útil para testes rápidos, mas qualquer editor de texto funciona. |

Adicione a dependência Maven do Aspose.Words ao seu `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version>
</dependency>
```

Se preferir Gradle, o equivalente é:

```gradle
implementation 'com.aspose:aspose-words:24.10'
```

---

## Etapa 1: Criar um Novo Documento e Builder

Primeiro criamos um `Document` vazio e um `DocumentBuilder`. O builder é o motor que nos permite inserir formas, texto e muito mais.

```java
// Step 1: Create a new empty document and a builder to work with it.
Document doc = new Document();                     // The container for all Word content.
DocumentBuilder builder = new DocumentBuilder(doc); // Fluent API to add elements.
```

*Por que esta etapa?*  
`Document` representa o arquivo DOCX completo, enquanto `DocumentBuilder` fornece uma API baseada em cursor conveniente. Sem um builder, você teria que manipular coleções de nós de baixo nível manualmente — algo fácil de errar.

---

## Etapa 2: Inserir uma Forma Retangular (e uma Elipse)

Agora adicionamos as duas formas básicas que queremos agrupar. Observe a chamada **insert rectangle shape** — esta é exatamente a palavra‑chave secundária que você está procurando.

```java
// Step 2: Insert two simple shapes – a rectangle and an ellipse.
Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
Shape ellipseShape   = builder.insertShape(ShapeType.ELLIPSE, 100, 50);
```

Alguns pontos a ter em mente:

* A largura (`100`) e a altura (`50`) são medidas em pontos (1 pt ≈ 1/72 in). Ajuste‑as conforme seu layout.  
* O retângulo é desenhado primeiro, portanto fica atrás da elipse por padrão. Se precisar da ordem inversa, insira a elipse primeiro.  
* Ambas as formas herdam a formatação atual do builder (cor, estilo de linha). Você pode personalizá‑las antes de agrupar, se desejar.

---

## Etapa 3: Como Agrupar Formas com Aspose.Words

Aqui está o núcleo do tutorial — **como agrupar formas**. A API `insertGroupShape` recebe um array de formas existentes e devolve um novo `Shape` que representa o grupo.

```java
// Step 3: Group the two shapes together using the InsertGroupShape API.
Shape groupShape = builder.insertGroupShape(new Shape[] { rectangleShape, ellipseShape });
```

Por que usar um grupo?  

* Um grupo se move como uma única unidade, preservando o posicionamento relativo.  
* Você pode aplicar transformações (rotação, escala) a todo o conjunto com uma única chamada.  
* Agrupar simplifica edições posteriores — desagrupe depois se precisar ajustar elementos individuais.

---

## Etapa 4 (Opcional): Ocultar o Grupo na Visualização do Documento

Se você não quiser que o grupo apareça quando o usuário abrir o documento no Word, pode ocultá‑lo. Esta etapa é opcional, mas útil para gráficos de fundo ou marcas d'água.

```java
// Step 4: (Optional) Hide the group so it does not appear in the document view.
groupShape.setHidden(true);   // Requires Aspose.Words 24.10 or later
```

**E se você estiver usando uma versão mais antiga do Aspose.Words?**  
O método `setHidden` não compilará. Nesse caso, você pode obter um efeito semelhante definindo o `WrapType` da forma como `NONE` e movendo‑a para trás da camada de texto:

```java
groupShape.setWrapType(WrapType.NONE);
groupShape.getParagraph().getParagraphFormat().setStyleIdentifier(StyleIdentifier.BACKGROUND);
```

É um pouco mais verboso, mas ainda mantém o grupo fora do caminho do leitor.

---

## Etapa 5: Salvar o Documento

Por fim, grave o documento no disco. Altere o caminho para onde você quiser que o arquivo seja salvo.

```java
// Step 5: Save the document with the grouped shapes.
doc.save("YOUR_DIRECTORY/GroupShapeResult.docx");
```

Ao abrir `GroupShapeResult.docx` no Microsoft Word, você verá um retângulo e uma elipse agrupados de forma ordenada. Se você definiu `setHidden(true)`, o grupo ficará invisível no editor, mas ainda presente no arquivo (útil para processamento programático posterior).

---

## Exemplo Completo Funcional

Juntando tudo, aqui está a classe Java completa e autônoma que você pode copiar‑colar no seu projeto:

```java
import com.aspose.words.*;

public class GroupShapeTutorial {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a builder to work with it.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert two simple shapes – a rectangle and an ellipse.
        Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        Shape ellipseShape   = builder.insertShape(ShapeType.ELLIPSE, 100, 50);

        // Step 3: Group the two shapes together using the InsertGroupShape API.
        Shape groupShape = builder.insertGroupShape(new Shape[] { rectangleShape, ellipseShape });

        // Step 4: (Optional) Hide the group so it does not appear in the document view.
        groupShape.setHidden(true);   // Requires Aspose.Words 24.10 or later

        // Step 5: Save the document with the grouped shapes.
        doc.save("YOUR_DIRECTORY/GroupShapeResult.docx");
    }
}
```

**Saída esperada:** Um arquivo chamado `GroupShapeResult.docx` contendo um único grupo que possui um retângulo preenchido de azul e uma elipse contornada de vermelho (cores padrão). Se você abrir o documento, selecionar o grupo e clicar com o botão direito → **Group → Ungroup**, verá as duas formas originais reaparecerem.

---

## Perguntas Frequentes & Casos de Borda

### 1. Posso agrupar mais de duas formas?

Com certeza. Basta passar um array maior para `insertGroupShape`:

```java
Shape triangle = builder.insertShape(ShapeType.TRIANGLE, 80, 80);
Shape[] manyShapes = new Shape[] { rectangleShape, ellipseShape, triangle };
Shape bigGroup = builder.insertGroupShape(manyShapes);
```

A API escala linearmente; a única limitação é a memória para grupos extremamente grandes.

### 2. E se eu precisar mudar a posição do grupo após a criação?

Use os métodos `setLeft` e `setTop` do grupo, assim como em qualquer outra forma:

```java
groupShape.setLeft(150);
groupShape.setTop(200);
```

Como o grupo se comporta como uma única forma, todas as formas filhas se movem juntas.

### 3. Como aplicar uma borda ou preenchimento ao grupo inteiro?

O próprio grupo pode ter formatação, mas isso não afeta diretamente os filhos. Se quiser uma borda comum, envolva as formas em um retângulo primeiro e então agrupe tudo. Alternativamente, itere sobre cada forma filha e defina o mesmo `fillColor` ou `strokeWeight`.

### 4. `setHidden(true)` afeta a impressão?

Formas ocultas **não** são impressas por padrão no Word, o que pode ser útil para marcas d'água ou marcadores de template. Se precisar que a forma seja impressa mas permaneça invisível na tela, será necessário usar outra abordagem (por exemplo, definir a opacidade para 0%).

---

## Dicas de Profissional da Linha de Frente

* **Nomeie suas formas** – `groupShape.setName("HeaderGraphics");` facilita a depuração quando você precisar recuperar formas pelo nome.  
* **Reutilize o builder** – Após inserir um grupo, o cursor do builder permanece onde o grupo foi colocado, permitindo que você continue adicionando parágrafos logo após o grupo sem redefinir a posição.  
* **Proteção de versão** – Se você distribuir uma biblioteca que pode rodar em versões mais antigas do Aspose.Words, envolva a chamada `setHidden` em um try‑catch para `NoSuchMethodError` e recorra ao truque `WrapType.NONE` mostrado anteriormente.  
* **Dica de desempenho** – Ao gerar milhares

## O Que Você Deve Aprender a Seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas em seus próprios projetos.

- [Using Document Shapes in Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-document-shapes/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Rendering Shapes in Aspose.Words for Java](/words/english/java/rendering-documents/rendering-shapes/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}