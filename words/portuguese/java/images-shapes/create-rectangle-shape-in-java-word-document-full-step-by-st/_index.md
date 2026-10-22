---
category: general
date: 2026-05-26
description: Crie uma forma retangular em um documento Word em Java e aplique o efeito
  de sombra. Aprenda como adicionar sombra à forma, definir a distância da sombra
  e salvar o arquivo.
draft: false
keywords:
- create rectangle shape
- apply shadow effect
- create word document java
- add shape shadow
- set shadow distance
language: pt
og_description: Crie uma forma retangular em um documento Word Java, aplique o efeito
  de sombra, adicione sombra à forma e defina a distância da sombra com Aspose.Words.
og_title: Criar Forma Retangular em Documento Word Java – Guia Completo
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Create rectangle shape in a Java Word document and apply shadow effect.
    Learn how to add shape shadow, set shadow distance, and save the file.
  headline: Create Rectangle Shape in Java Word Document – Full Step‑by‑Step Guide
  type: TechArticle
- description: Create rectangle shape in a Java Word document and apply shadow effect.
    Learn how to add shape shadow, set shadow distance, and save the file.
  name: Create Rectangle Shape in Java Word Document – Full Step‑by‑Step Guide
  steps:
  - name: “Can I use a different shape?”
    text: Absolutely. Replace `ShapeType.RECTANGLE` with `ShapeType.OVAL`, `ShapeType.LINE`,
      or any other supported enum. The rest of the shadow code stays the same.
  - name: “What if I need multiple shadows?”
    text: Aspose.Words only supports a single shadow per shape. To simulate multiple
      shadows, duplicate the shape, offset each copy, and adjust the transparency.
  - name: “Is the shadow visible in LibreOffice?”
    text: Yes—Aspose.Words writes standard OOXML, which LibreOffice interprets correctly.
      The shadow may look slightly different due to rendering engines, but the effect
      persists.
  - name: “How do I change the shadow color to match my brand?”
    text: Just swap `java.awt.Color.GRAY` with any `java.awt.Color` you prefer, such
      as `new java.awt.Color(0, 120, 215)` for a corporate blue.
  type: HowTo
tags:
- Java
- Aspose.Words
- Word Automation
title: Criar Forma Retangular em Documento Word Java – Guia Completo Passo a Passo
url: /pt/java/images-shapes/create-rectangle-shape-in-java-word-document-full-step-by-st/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar Forma Retangular em Documento Word Java – Guia Completo Passo a Passo

Já precisou **criar forma retangular** em um documento Word Java, mas não sabia por onde começar? Você não está sozinho—muitos desenvolvedores encontram esse obstáculo ao gerar relatórios ou faturas programaticamente. Neste tutorial vamos percorrer exatamente como **criar forma retangular**, aplicar uma sombra refinada e ajustar a distância da sombra para que o resultado pareça profissional.

Usaremos o Aspose.Words for Java, uma biblioteca robusta que permite manipular arquivos Word sem precisar do Microsoft Office instalado. Ao final deste guia você será capaz de criar projetos **word document java** que **add shape shadow**, **apply shadow effect** e **set shadow distance** com apenas algumas linhas de código.

---

## O Que Você Vai Construir

- Um novo arquivo `.docx` contendo um retângulo ciano.
- Uma sombra realista que é desfocada, inclinada e parcialmente transparente.
- Controle total sobre a distância da sombra em relação à forma.
- Uma classe Java pronta‑para‑executar que pode ser inserida em qualquer projeto Maven ou Gradle.

Sem ferramentas externas, sem etapas manuais de UI—apenas código puro.

---

## Pré‑requisitos

- Java 8 ou superior (o código funciona em Java 11, Java 17, etc.).
- Biblioteca Aspose.Words for Java (disponível via Maven Central).
- Uma IDE ou editor de texto de sua preferência (IntelliJ IDEA, Eclipse, VS Code…).
- Familiaridade básica com a sintaxe Java.

Se você nunca adicionou uma dependência Maven antes, aqui está o snippet rápido:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest stable version -->
</dependency>
```

Agora, vamos mergulhar.

---

## Etapa 1: Criar Forma Retangular em um Documento Word

A primeira coisa que precisamos é de um documento em branco e de um `DocumentBuilder`. Pense no builder como uma caneta que escreve no documento. Depois de tê‑lo, podemos **create rectangle shape** com uma única chamada de método.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new empty document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a rectangle shape of 150x80 points.
        Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 150, 80);
        // Make the shape visible by filling it with cyan.
        rectangleShape.setFillColor(java.awt.Color.CYAN);
```

> **Por que isso importa:** O método `insertShape` não só cria a geometria, como também adiciona a forma à coleção interna do documento, permitindo que você comece a estilizar imediatamente.

---

## Etapa 2: Aplicar Efeito de Sombra à Forma

Agora que o retângulo está na página, vamos **apply shadow effect**. Sombras dão profundidade, fazendo a forma parecer levantada da página—uma melhoria sutil de UI que pode aumentar a legibilidade em relatórios.

```java
        // Retrieve the shadow format object.
        ShadowFormat shadowFormat = rectangleShape.getShadowFormat();

        // Enable the shadow and configure its appearance.
        shadowFormat.setVisible(true);          // Turn the shadow on.
        shadowFormat.setBlur(5.0);              // Soft blur radius.
        shadowFormat.setAngle(45.0);            // Direction of the shadow.
        shadowFormat.setColor(java.awt.Color.GRAY); // Shadow color.
        shadowFormat.setTransparency(0.3);     // 30% transparent.
```

> **Dica de especialista:** Um desfoque de `5.0` parece natural na maioria dos documentos exibidos em tela. Se você for imprimir, talvez queira um valor ligeiramente menor para evitar uma aparência borrada.

---

## Etapa 3: Definir Distância da Sombra – Ajuste Fino da Posicionamento

Sombras não são apenas sobre desfoque; elas também precisam do deslocamento correto. É aqui que **set shadow distance** entra. Uma distância de `7.0` pontos cria um deslocamento modesto que é perceptível, mas não excessivo.

```java
        // Define how far the shadow sits from the shape.
        shadowFormat.setDistance(7.0); // Distance in points.
```

> **E se você precisar de um deslocamento maior?** Aumente o valor; diminua para um visual mais compacto. Lembre‑se de que a distância trabalha em conjunto com o ângulo para posicionar a sombra corretamente.

---

## Etapa 4: Salvar o Documento – Persistir Seu Trabalho

Por fim, gravamos o documento no disco. Altere o caminho para onde você quiser que o arquivo seja salvo.

```java
        // Save the document with the rectangle and its shadow.
        doc.save("YOUR_DIRECTORY/shadow.docx");
    }
}
```

Executar a classe cria um arquivo `shadow.docx` que, ao ser aberto no Microsoft Word ou LibreOffice, mostra um retângulo ciano com uma sombra cinza suave inclinada a 45° e deslocada em 7 pontos.

---

## Exemplo Completo Funcionando

Abaixo está o código completo, pronto para copiar e colar. Inclui todas as importações, comentários e a chamada final de `save`.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a rectangle shape of the desired size.
        Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 150, 80);
        // Step 3: Apply a fill color to make the shape visible.
        rectangleShape.setFillColor(java.awt.Color.CYAN);

        // Step 4: Configure the shape's shadow effect.
        ShadowFormat shadowFormat = rectangleShape.getShadowFormat();
        shadowFormat.setVisible(true);          // Enable the shadow.
        shadowFormat.setBlur(5.0);              // Set the blur radius.
        shadowFormat.setDistance(7.0);          // Define how far the shadow is from the shape.
        shadowFormat.setAngle(45.0);            // Set the direction of the shadow.
        shadowFormat.setColor(java.awt.Color.GRAY); // Choose the shadow color.
        shadowFormat.setTransparency(0.3);      // Make the shadow partially transparent.

        // Step 5: Save the document with the shaped shadow.
        doc.save("YOUR_DIRECTORY/shadow.docx");
    }
}
```

**Saída esperada:** Abra `shadow.docx` → você verá um retângulo ciano centralizado na primeira página, projetando uma sombra cinza sutil ligeiramente deslocada para a parte inferior‑direita. O desfoque e a transparência da sombra dão a impressão de iluminação natural.

---

## Perguntas Frequentes & Casos de Borda

### “Posso usar uma forma diferente?”

Com certeza. Substitua `ShapeType.RECTANGLE` por `ShapeType.OVAL`, `ShapeType.LINE` ou qualquer outro enum suportado. O restante do código de sombra permanece igual.

### “E se eu precisar de várias sombras?”

O Aspose.Words suporta apenas uma sombra por forma. Para simular múltiplas sombras, duplique a forma, desloque cada cópia e ajuste a transparência.

### “A sombra é visível no LibreOffice?”

Sim—o Aspose.Words grava OOXML padrão, que o LibreOffice interpreta corretamente. A sombra pode parecer ligeiramente diferente devido aos motores de renderização, mas o efeito persiste.

### “Como mudar a cor da sombra para combinar com a minha marca?”

Basta trocar `java.awt.Color.GRAY` por qualquer `java.awt.Color` que preferir, como `new java.awt.Color(0, 120, 215)` para um azul corporativo.

---

## Ilustração da Imagem

![create rectangle shape in Java Word document](https://example.com/images/rectangle-shadow.png)

*Alt text:* **create rectangle shape** illustration showing a cyan rectangle with a gray drop shadow in a Word document.

---

## Recapitulação & Próximos Passos

Cobrimos como **create rectangle shape**, **apply shadow effect**, **add shape shadow** e **set shadow distance** usando Aspose.Words for Java. O código é autocontido, roda em qualquer JDK moderno e produz um arquivo `.docx` polido pronto para distribuição.

Quer ir além? Experimente:

- Adicionar texto dentro do retângulo com `builder.moveTo(rectangleShape.getAbsolutePosition())`.
- Criar uma tabela de formas para montar um diagrama.
- Exportar o documento para PDF (`doc.save("output.pdf", SaveFormat.PDF);`).

Cada um desses itens se baseia nos mesmos fundamentos que acabamos de explorar, então você se sentirá confortável em estender o exemplo.

---

## Considerações Finais

Dominar tarefas **create word document java** como modelagem e sombreamento dá a você uma grande vantagem ao automatizar relatórios, contratos ou materiais de marketing. A abordagem mostrada aqui é limpa, mantível e—o mais importante—fácil de ajustar para qualquer estilo visual que você precise.

Teste o código, ajuste o desfoque, ângulo e distância, e veja seus documentos se transformarem de simples a sofisticados. Se encontrar algum obstáculo, deixe um comentário abaixo; ficarei feliz em ajudar.

Happy coding!

## Tutoriais Relacionados

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Create PDF from Word with Barcode Generation – Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-barcode-generation/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}