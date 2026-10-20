---
category: general
date: 2026-10-20
description: Como agrupar formas no Aspose.Words para Java – aprenda a inserir forma
  retangular, agrupá‑las e salvar o documento em um único guia.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert rectangle shape
- how to insert rectangle
language: pt
lastmod: 2026-10-20
og_description: Como agrupar formas no Aspose.Words for Java. Este tutorial mostra
  como inserir uma forma retangular, agrupá‑las e exportar o resultado.
og_image_alt: Screenshot of a Word document showing two grouped rectangle shapes created
  with Aspose.Words for Java
og_title: Como agrupar formas no Aspose.Words para Java – guia passo a passo
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: How to group shapes in Aspose.Words for Java – learn how to insert
    rectangle shape, group them, and save the document in a single guide.
  headline: How to group shapes in Aspose.Words for Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- shape manipulation
title: Como agrupar formas no Aspose.Words para Java
url: /pt/java/images-shapes/how-to-group-shapes-in-aspose-words-for-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como agrupar formas no Aspose.Words para Java

Se você precisa **como agrupar formas** em um documento Word usando Aspose.Words para Java, este guia mostra o fluxo de trabalho completo. Você aprenderá como **inserir forma retangular**, adicionar um segundo retângulo, agrupar as duas formas e, finalmente, salvar o arquivo — tudo com código claro e executável.

Agrupar formas é útil quando você deseja mover, girar ou estilizar vários desenhos como uma única unidade. Seja você quem está criando um modelo de relatório, um diagrama ou um folheto personalizado, dominar o agrupamento de formas economiza tempo e mantém seu layout consistente.

Neste tutorial você vai:

* Criar um novo `Document` e um `DocumentBuilder`.
* **Como inserir retângulo** formas com dimensões precisas.
* Agrupar os retângulos em um `GroupShape`.
* Salvar o documento e verificar o resultado.

> **Pré-requisito** – Você deve ter Aspose.Words para Java (v23.12 ou posterior) adicionado ao seu projeto. Usuários Maven podem incluir a dependência mostrada abaixo.

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

---

## O que você precisará

| Item | Motivo |
|------|--------|
| Java 17+ | Recursos modernos da linguagem e melhor desempenho |
| Aspose.Words for Java | Fornece as APIs `DocumentBuilder`, `Shape` e `GroupShape` |
| An IDE (IntelliJ IDEA, Eclipse, VS Code, etc.) | Para compilar e executar o exemplo |
| Write permission to a folder | O documento será salvo em disco |

---

## Como inserir forma retangular

O primeiro passo é criar um `Document` e um `DocumentBuilder`. O builder fornece métodos como `insertShape` para inserir objetos de desenho.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert the first rectangle (100 × 50 points).
        Shape rectangle1 = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        // Optional: give the rectangle a fill color for visibility.
        rectangle1.getFill().setForeColor(java.awt.Color.BLUE);

        // Step 3: Insert the second rectangle (80 × 40 points).
        Shape rectangle2 = builder.insertShape(ShapeType.RECTANGLE, 80, 40);
        rectangle2.getFill().setForeColor(java.awt.Color.GREEN);

        // The two rectangles are currently independent objects.
        // Below we will group them together.
```

> **Por que isso importa** – Usar `insertShape` é a forma padrão **como inserir retângulo** objetos no Aspose.Words. Ele adiciona automaticamente a forma ao parágrafo atual do documento, então você não precisa gerenciar OpenXML de baixo nível.

---

## Ajustando posições do retângulo (opcional)

Se o segundo retângulo precisar de uma localização personalizada em relação ao primeiro, você pode modificar suas propriedades `left` e `top`. Esta etapa é opcional, mas frequentemente necessária para um layout de diagrama preciso.

```java
        // Optional: reposition the second rectangle 20 points to the right.
        rectangle2.setLeft(rectangle1.getLeft() + 20);
        // Optional: align the top edges.
        rectangle2.setTop(rectangle1.getTop());
```

> **Dica profissional:** Todas as medidas estão em pontos (1 pt ≈ 1/72 in). Use `convertPointsToPixels` se precisar de valores em pixels para cálculos baseados em UI.

---

## Como agrupar formas

Agora que os retângulos existem, você pode colocá‑los dentro de um `GroupShape`. O agrupamento faz com que os dois retângulos se comportem como um único objeto — mover, girar ou formatar o grupo afetará ambas as formas.

```java
        // Step 4: Insert an empty GroupShape.
        GroupShape group = builder.insertGroupShape();

        // Step 5: Add the rectangles to the group.
        group.appendChild(rectangle1);
        group.appendChild(rectangle2);

        // Optional: set a border for the whole group.
        group.getStroke().setColor(java.awt.Color.RED);
        group.getStroke().setWeight(1.5);
```

> **Por que o agrupamento funciona** – `GroupShape` herda de `Shape`, então você pode tratar o grupo exatamente como qualquer outro objeto de desenho. Quando você chama `appendChild`, as formas são removidas de sua localização original e se tornam filhas do grupo.

---

## Salvando o documento contendo as formas agrupadas

Por fim, grave o documento no disco. O arquivo conterá um único `GroupShape` com dois retângulos dentro.

```java
        // Step 6: Save the document.
        String outPath = "output/GroupShape.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### Resultado esperado

Abra `GroupShape.docx` no Microsoft Word:

* Você verá dois retângulos (azul e verde) posicionados lado a lado.
* Selecionar qualquer retângulo seleciona todo o grupo — arrastar move ambos juntos.
* O grupo tem uma borda vermelha fina, confirmando que as propriedades do `GroupShape` foram aplicadas.

Se você clicar com o botão direito no grupo e escolher **Group → Ungroup**, os retângulos retornam a formas independentes, demonstrando que a operação de agrupamento é reversível.

---

## Variações comuns e casos de borda

| Situação | Como lidar |
|-----------|------------|
| **Mais de duas formas** | Insira cada forma, depois anexe todas ao mesmo `GroupShape`. |
| **Tipos diferentes de forma** (por exemplo, elipse, imagem) | Use `builder.insertShape(ShapeType.ELLIPSE, …)` ou `builder.insertImage(...)` antes de anexar. |
| **Dimensionando o grupo** | Chame `group.setWidth(newWidth)` ou `group.setHeight(newHeight)`; os filhos são dimensionados proporcionalmente. |
| **Rotacionando o grupo** | `group.setRotationAngle(45);` gira toda a coleção ao redor do seu centro. |
| **Preservando posições originais** | Armazene `left`/`top` de cada forma antes de agrupar e restaure após desagrupar, se necessário. |

---

## Exemplo completo e executável

Abaixo está a classe Java completa que você pode copiar‑colar no seu IDE. Ela inclui todas as importações, tratamento de erros e comentários para clareza.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert the first rectangle (100 × 50 points) and give it a blue fill.
        Shape rectangle1 = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        rectangle1.getFill().setForeColor(java.awt.Color.BLUE);

        // Insert the second rectangle (80 × 40 points) with a green fill.
        Shape rectangle2 = builder.insertShape(ShapeType.RECTANGLE, 80, 40);
        rectangle2.getFill().setForeColor(java.awt.Color.GREEN);

        // Optional positioning – move the second rectangle 20 pt to the right.
        rectangle2.setLeft(rectangle1.getLeft() + 20);
        rectangle2.setTop(rectangle1.getTop());

        // Insert an empty group shape.
        GroupShape group = builder.insertGroupShape();

        // Add both rectangles to the group.
        group.appendChild(rectangle1);
        group.appendChild(rectangle2);

        // Style the group (red border, 1.5 pt weight).
        group.getStroke().setColor(java.awt.Color.RED);
        group.getStroke().setWeight(1.5);

        // Save the document.
        String outPath = "output/GroupShape.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

Execute o programa, abra o `GroupShape.docx` resultante e você verá os retângulos agrupados exatamente como descrito.

---

## Conclusão

Agora você sabe **como agrupar formas** no Aspose.Words para Java, desde a criação de um documento até a inserção de formas retangulares, ajuste de suas posições e, finalmente, o agrupamento com `GroupShape`. Essa técnica permite tratar vários desenhos como uma única entidade, simplificando ajustes de layout e consistência visual.

**Próximos passos**

* Explore **como inserir retângulo** formas com diferentes padrões de preenchimento ou bordas.  
* Combine **inserir forma retangular** com caixas de texto para criar diagramas rotulados.  
* Experimente girar ou dimensionar o grupo para produzir gráficos mais complexos.

Sinta‑se à vontade para adaptar o código para outros tipos de forma, grupos maiores ou cenários de geração dinâmica de documentos. Feliz codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que expandem as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Inserir forma retangular em Java – Agrupar e posicionar formas](/words/english/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/)
- [como inserir forma de grupo em Java – Guia completo](/words/english/java/images-shapes/how-to-insert-group-shape-in-java-complete-guide/)
- [Como definir sombra em uma forma no Aspose.Words – Guia completo](/words/english/java/images-shapes/how-to-set-shadow-on-a-shape-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}