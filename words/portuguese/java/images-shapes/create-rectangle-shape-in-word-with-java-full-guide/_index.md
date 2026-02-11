---
category: general
date: 2026-02-10
description: Crie uma forma retangular em um documento Word usando Aspose.Words para
  Java. Aprenda como definir a cor da sombra, como adicionar sombra e como criar um
  documento Word programaticamente.
draft: false
keywords:
- create rectangle shape
- set shadow color
- create word document
- how to add shadow
- how to create shape
language: pt
og_description: Crie uma forma retangular em um documento Word usando Aspose.Words
  para Java. Siga este tutorial passo a passo para definir a cor da sombra, adicionar
  sombra e criar o documento Word.
og_title: Crie forma de retângulo no Word com Java – Guia Completo
tags:
- Aspose.Words
- Java
- Document Automation
title: Criar forma retangular no Word com Java – Guia Completo
url: /pt/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/
---

ar forma retangular no Word com Java – Guia Completo"

Then paragraph: "Ever needed to **create rectangle shape** in a Word document but weren't sure where to start? ..." translate.

We must keep bold formatting.

Proceed step by step.

Also note "RTL formatting if needed" but Portuguese LTR, fine.

Let's produce final content.

Be careful with tables: translate column headers and content.

Also list items.

Also alt text.

Also "Image alt text: ..." translate.

Also "Expected Result" table.

Also "Pro Tips & Common Pitfalls" heading.

Make sure to keep code block placeholders unchanged.

Let's craft translation.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar forma retangular no Word com Java – Guia Completo

Já precisou **criar forma retangular** em um documento Word, mas não sabia por onde começar? Você não está sozinho — muitos desenvolvedores encontram essa barreira ao tentar desenhar gráficos programaticamente no Word. A boa notícia? Com Aspose.Words for Java você pode inserir um retângulo em uma página, aplicar uma sombra agradável e salvar o arquivo em segundos. Neste tutorial vamos percorrer exatamente **como adicionar sombra**, **definir a cor da sombra** e **criar documento Word** do zero.  

Vamos cobrir tudo que você precisa: as bibliotecas necessárias, cada linha de código, por que certas configurações são importantes e alguns truques que você pode não encontrar na documentação oficial. Ao final, você terá um exemplo pronto‑para‑executar que cria uma forma retangular com uma sombra cinza suave, salvo como *Shadow.docx*.

## Pré‑requisitos – O que você precisa antes de começar

Antes de mergulharmos no código, certifique‑se de que tem o seguinte:

| Requisito | Motivo |
|-----------|--------|
| Java Development Kit (JDK) 8 ou superior | Aspose.Words funciona em qualquer JDK moderno. |
| Maven ou Gradle (opcional) | Simplifica a adição da dependência Aspose.Words. |
| Licença Aspose.Words for Java (ou um teste gratuito) | A biblioteca é comercial; um teste funciona para testes. |
| Uma IDE (IntelliJ IDEA, Eclipse, VS Code, etc.) | Ajuda a executar e depurar o exemplo rapidamente. |

Se já possui um projeto Java, basta adicionar a coordenada Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Replace with the latest version -->
</dependency>
```

Nenhuma configuração complicada além disso — apenas um método `public static void main` simples já basta.

![create rectangle shape example](https://example.com/rectangle-shadow.png "create rectangle shape with shadow in Word")

*Texto alternativo da imagem: exemplo de criação de forma retangular mostrando um retângulo ciano com sombra cinza.*

## Etapa 1 – Criar um novo documento Word

A primeira coisa que precisamos fazer é iniciar um documento em branco. Pense nisso como abrir um arquivo Word novo que você pintará depois.

```java
// Step 1: Initialize a blank Document object
Document document = new Document();
```

Por que começar com um `Document` vazio? Porque o Aspose.Words trata a classe `Document` como a tela para todas as operações subsequentes — adicionar parágrafos, tabelas ou formas. Se pular esta etapa, você receberá um `NullPointerException` no momento em que tentar inserir qualquer coisa.

## Etapa 2 – Configurar um DocumentBuilder

Um `DocumentBuilder` é sua caneta amigável que escreve dentro do `Document`. É a forma recomendada de adicionar conteúdo porque gerencia automaticamente a posição do cursor.

```java
// Step 2: Create a DocumentBuilder tied to our document
DocumentBuilder builder = new DocumentBuilder(document);
```

Você pode se perguntar: “Por que não manipular o documento diretamente?” A resposta: o builder abstrai detalhes de baixo nível, como o gerenciamento de seções, tornando o código mais limpo e menos propenso a erros.

## Etapa 3 – Inserir a forma retangular

Agora vem a parte divertida — **como criar forma**. Inseriremos um retângulo de 100 × 50 pontos e aplicaremos um preenchimento ciano para que você realmente o veja.

```java
// Step 3: Insert a rectangle shape of size 100x50 points
Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);

// Apply a solid fill color to make the shape visible
rectangle.setFillColor(java.awt.Color.CYAN);
```

Algumas observações:

* `ShapeType.RECTANGLE` indica ao Aspose que queremos um retângulo; você pode trocar por `OVAL`, `LINE`, etc.
* As dimensões são expressas em pontos (1 pt ≈ 1/72 pol). Ajuste‑as conforme sua diagramação.
* Sem uma cor de preenchimento a forma ficaria invisível em uma página branca — por isso o ciano.

## Etapa 4 – Adicionar uma sombra e **definir a cor da sombra**

Aqui respondemos à parte **como adicionar sombra** do quebra‑cabeça. O objeto `ShadowFormat` controla cada aspecto visual da sombra, da cor ao raio de desfoque.

```java
// Step 4: Enable the shape's shadow and configure its appearance
rectangle.getShadowFormat().setVisible(true);                     // Turn the shadow on
rectangle.getShadowFormat().setColor(java.awt.Color.GRAY);      // **set shadow color** to gray
rectangle.getShadowFormat().setBlurRadius(5.0);                  // Soft blur for realism
rectangle.getShadowFormat().setOffsetX(4.0);                     // Horizontal offset
rectangle.getShadowFormat().setOffsetY(4.0);                     // Vertical offset
rectangle.getShadowFormat().setTransparency(0.3);               // 30 % transparent
```

Por que esses valores específicos?

* **Visibilidade** – Sem `setVisible(true)` o restante das configurações é ignorado.
* **Cor** – Cinza é uma escolha neutra que funciona tanto em fundos claros quanto escuros. Sinta‑se à vontade para substituir `java.awt.Color.GRAY` por qualquer `java.awt.Color` que desejar.
* **Raio de desfoque** – Um valor de `5.0` gera um efeito suave; valores maiores deixam a sombra mais difusa.
* **OffsetX/Y** – Os deslocamentos movem a sombra para a direita e para baixo, simulando uma fonte de luz no canto superior esquerdo.
* **Transparência** – Uma sombra semitransparente se mistura melhor com a página, especialmente ao imprimir.

Se precisar de um visual mais nítido, reduza o raio de desfoque para `0` e aumente o deslocamento. Experimente — sombras são altamente visuais, e as configurações ideais dependem do design do seu documento.

## Etapa 5 – Salvar o documento

Por fim, persistimos tudo em um arquivo `.docx`. Você pode escolher qualquer caminho; apenas certifique‑se de que o diretório exista.

```java
// Step 5: Save the document with the shaped shadow to a file
document.save("YOUR_DIRECTORY/Shadow.docx");
```

Ao abrir *Shadow.docx* no Microsoft Word, você verá um retângulo ciano com uma sombra cinza sutil deslocada 4 pts para a direita e para baixo. Esse é o fluxo completo de **criar documento Word**.

### Resultado esperado

| Elemento | Aparência |
|----------|-----------|
| Retângulo | Preenchimento ciano, tamanho 100 × 50 pt |
| Sombra | Cinza, 30 % transparente, desfoque 5 pt, deslocamento (4, 4) |
| Arquivo | `Shadow.docx` armazenado no caminho que você forneceu |

Se a forma não aparecer, verifique se a cor de preenchimento não é a mesma do fundo da página e se a sombra está definida como visível.

## Dicas avançadas & armadilhas comuns

* **Dica avançada:** Use `rectangle.setStrokeColor(java.awt.Color.BLACK);` se quiser uma borda ao redor da forma. Isso faz o retângulo se destacar mais em uma página impressa.
* **Cuidado com:** Salvar em uma pasta somente‑leitura lançará um `IOException`. Escolha um local gravável ou ajuste as permissões do arquivo.
* **Caso especial:** Se precisar de preenchimento transparente (sem cor), chame `rectangle.setFillColor(java.awt.Color.WHITE); rectangle.setFillOpacity(0.0);`. A forma ainda projetará sombra, o que pode ser útil para gráficos estilo marca‑d’água.
* **Observação de desempenho:** Adicionar centenas de formas em um loop pode aumentar o uso de memória. Chame `document.save` apenas uma vez após todas as formas serem inseridas.

## Exemplo completo funcionando

Abaixo está o programa inteiro que você pode copiar‑colar em uma classe Java chamada `ShadowDemo`. Ele compila e executa como‑está (desde que o JAR do Aspose.Words esteja no classpath).

```java
import com.aspose.words.*;

public class ShadowDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to construct the document content
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 3: Insert a rectangle shape of size 100x50 points
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        // Apply a solid fill color to make the shape visible
        rectangle.setFillColor(java.awt.Color.CYAN);

        // Step 4: Enable the shape's shadow and configure its appearance
        rectangle.getShadowFormat().setVisible(true);
        rectangle.getShadowFormat().setColor(java.awt.Color.GRAY); // set shadow color
        rectangle.getShadowFormat().setBlurRadius(5.0);
        rectangle.getShadowFormat().setOffsetX(4.0);
        rectangle.getShadowFormat().setOffsetY(4.0);
        rectangle.getShadowFormat().setTransparency(0.3);

        // Step 5: Save the document with the shaped shadow to a file
        document.save("YOUR_DIRECTORY/Shadow.docx");
    }
}
```

Execute o programa, abra o *Shadow.docx* resultante e verá o retângulo com sua sombra exatamente como descrito.

## E se precisar de mais formas?

Você pode se perguntar: “Posso **criar forma retangular** várias vezes ou usar outras formas?” Absolutamente. Basta colocar o código de inserção dentro de um loop e ajustar as coordenadas usando `builder.moveTo` ou `builder.insertParagraph`. As mesmas configurações de sombra podem ser reutilizadas extraindo‑as para um método auxiliar:

```java
private static void applyStandardShadow(Shape shape) {
    shape.getShadowFormat().setVisible(true);
    shape.getShadowFormat().setColor(java.awt.Color.GRAY);
    shape.getShadowFormat().setBlurRadius(5.0);
    shape.getShadowFormat().setOffsetX(4.0);
    shape.getShadowFormat().setOffsetY(4.0);
    shape.getShadowFormat().setTransparency(0.3);
}
```

Chame `applyStandardShadow(rectangle);` após cada inserção de forma para manter seu código DRY (Don’t Repeat Yourself).

## Próximos passos – Indo além do básico

Agora que você sabe **como adicionar sombra**, considere explorar estes tópicos relacionados:

* **Como definir a cor da sombra** para trechos de texto – dá aos títulos um leve relevo.
* **Criar documento Word** com tabelas e imagens – combine formas com outros conteúdos.
* **Como criar animações de forma** usando os recursos nativos do Word

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}