---
category: general
date: 2026-02-15
description: Crie uma forma retangular em um documento Word usando Java. Aprenda como
  adicionar sombra à forma, salvar o documento Word e adicionar uma forma retangular
  com Aspose.Words.
draft: false
keywords:
- create rectangle shape
- save word document
- how to shadow shape
- add shape shadow
- add rectangle shape
language: pt
og_description: Criar forma de retângulo em um arquivo Word com Java. Este guia mostra
  como adicionar sombra à forma, salvar o documento Word e inserir a forma de retângulo
  passo a passo.
og_title: Criar forma retangular – Tutorial Java Aspose.Words
tags:
- Aspose.Words
- Java
- Document Automation
title: Criar forma de retângulo no Word com Java – Guia Completo
url: /pt/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/
---

com sombra criada usando Aspose.Words". Title: "criar forma retangular com sombra". Keep URL unchanged.

Now translate all paragraphs.

Let's produce final.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar forma retangular no Word com Java – Guia Completo

Já precisou **criar forma retangular** em um arquivo Word, mas não sabia por onde começar? Você não está sozinho—muitos desenvolvedores encontram essa barreira ao automatizar relatórios ou faturas. A boa notícia? Com Aspose.Words for Java você pode gerar um retângulo, aplicar uma sombra agradável e salvar o documento Word em poucas linhas.

Neste tutorial vamos percorrer tudo que você precisa: desde a inicialização de um documento em branco, até a configuração da sombra e, finalmente, a gravação do arquivo. Ao final, você saberá **como aplicar sombra a shapes**, como **adicionar sombra a shapes**, e como **adicionar forma retangular** a qualquer documento Word que gerar. Nenhuma documentação externa necessária—apenas código puro e executável.

## Pré‑requisitos

- Java 8 ou superior (a API funciona também com Java 11+).  
- Biblioteca Aspose.Words for Java (versão 23.9 ou posterior).  
- Uma IDE como IntelliJ IDEA ou Eclipse—qualquer uma serve.  
- Familiaridade básica com a sintaxe Java.

> **Dica profissional:** Se você usa Maven, adicione a dependência Aspose.Words ao seu `pom.xml` e deixe a IDE cuidar do resto.

---

## Etapa 1: Inicializar um Novo Documento – Como **criar forma retangular**  

Primeiro passo: você precisa de uma tela limpa. No Aspose.Words, essa tela é um objeto `Document`.

```java
import com.aspose.words.*;

public class ShadowShapeExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();
```

A classe `Document` representa o arquivo .docx completo. Pense nela como o caderno onde você mais tarde **adicionará forma retangular** e sua sombra.

## Etapa 2: Construir o Retângulo – **Adicionar forma retangular**  

Agora realmente construímos o retângulo. Definiremos seu tamanho, layout e cor de preenchimento.

```java
        // Step 2: Create a rectangle shape and set its size and layout
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(200);
        rectangleShape.setHeight(100);
        rectangleShape.setWrapType(WrapType.INLINE);
        rectangleShape.setFillColor(java.awt.Color.LIGHT_GRAY);
```

Por que `INLINE`? Porque queremos que a shape se comporte como um parágrafo—perfeito para relatórios simples. Você pode mudar para `TOPBOTTOM` se precisar que o texto flua ao redor da shape posteriormente.

## Etapa 3: Aplicar uma Sombra – **Como aplicar sombra a shapes**  

Um retângulo plano parece um pouco sem graça. Adicionar uma sombra dá profundidade e deixa o documento mais polido. É aqui que respondemos “**como aplicar sombra a shapes**” na prática.

```java
        // Step 3: Configure the shape's shadow appearance
        rectangleShape.getShadowFormat().setVisible(true);
        rectangleShape.getShadowFormat().setColor(java.awt.Color.DARK_GRAY);
        rectangleShape.getShadowFormat().setBlurRadius(5.0);
        rectangleShape.getShadowFormat().setOffsetX(4.0);
        rectangleShape.getShadowFormat().setOffsetY(4.0);
        rectangleShape.getShadowFormat().setTransparency(0.3);
```

Cada propriedade faz algo específico:

- `setVisible(true)` liga a sombra.  
- `setColor` escolhe um cinza escuro para um efeito sutil.  
- `setBlurRadius` controla o quão suaves ficam as bordas.  
- `setOffsetX/Y` desloca a sombra para a direita e para baixo, simulando uma fonte de luz.  
- `setTransparency` a torna levemente translúcida, para que a shape continue sendo o destaque.

> **Observação:** Se precisar de uma sombra colorida, basta passar um `java.awt.Color` diferente para `setColor`.

## Etapa 4: Inserir a Shape no Documento  

Com o retângulo e sua sombra prontos, inserimos na primeira seção do documento.

```java
        // Step 4: Add the shape to the first section of the document
        document.getFirstSection().getBody().appendChild(rectangleShape);
```

Adicionar ao corpo coloca a shape onde um novo parágrafo seria inserido. Se quiser o retângulo em um local específico, pode usar `insertBefore` ou manipular a coleção `Paragraph`.

## Etapa 5: **Salvar documento Word** – Persistir seu trabalho  

O passo final é gravar o arquivo no disco. Este é o momento em que você realmente **salva documento Word**.

```java
        // Step 5: Save the document with the shadowed shape
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

Substitua `YOUR_DIRECTORY` por um caminho absoluto ou relativo na sua máquina. Após executar o programa, abra `ShadowShape.docx` no Microsoft Word—você deverá ver um retângulo cinza‑claro com uma sombra escura suave.

![Diagrama mostrando uma forma retangular com sombra criada usando Aspose.Words](https://example.com/rectangle-shadow.png "criar forma retangular com sombra")

---

## Perguntas Frequentes & Casos de Borda  

### E se eu precisar de vários retângulos?  

Basta repetir **Etapa 2** e **Etapa 3** dentro de um loop, ajustando `setWidth`, `setHeight` ou `setFillColor` a cada iteração. Lembre‑se de dar a cada shape um nome de variável único ou armazená‑las em uma lista.

### Posso exportar para PDF em vez de DOCX?  

Com certeza. Depois que a shape for adicionada, chame `document.save("output.pdf")`. O Aspose.Words cuidará da conversão, preservando a sombra.

### E quanto a versões mais antigas do Word?  

Use a sobrecarga `document.save("file.doc", SaveFormat.DOC)`. A API rebaixa automaticamente os recursos, mas observe que alguns estilos de sombra podem ficar ligeiramente diferentes em formatos legados.

### Como mudar a direção da sombra?  

Manipule `setOffsetX` e `setOffsetY`. Valor positivo em X move a sombra para a direita, negativo para a esquerda. Valor positivo em Y move para baixo, negativo para cima. Brinque com esses números para simular uma fonte de luz de qualquer ângulo.

---

## Dicas para Trabalhar com Shapes  

- **Agrupar shapes**: Se precisar de um rótulo ao lado do retângulo, crie um `GroupShape` e adicione tanto o retângulo quanto um `TextBox`.  
- **Ordem Z importa**: Use `shape.moveToFront()` ou `shape.moveToBack()` para controlar qual shape aparece acima.  
- **Desempenho**: Adicionar centenas de shapes pode ser lento. Agrupe‑as em uma única seção e chame `document.updatePageLayout()` apenas uma vez ao final.

---

## Recapitulação  

Cobremos como **criar forma retangular** em um documento Word usando Java, como **adicionar sombra a shapes**, e como **salvar documento Word** com o resultado. O código completo e executável está nos trechos acima, e agora você entende o “porquê” de cada propriedade—para que possa ajustar cores, desfoque e deslocamentos conforme qualquer design.

Pronto para o próximo desafio? Experimente combinar o retângulo com um gráfico, ou exporte o arquivo como PDF e veja como a sombra é renderizada. Você também pode explorar **adicionar forma retangular** dentro de tabelas para layouts de relatórios mais sofisticados.

Bom código, e que seus documentos estejam sempre tão nítidos quanto seu código!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}