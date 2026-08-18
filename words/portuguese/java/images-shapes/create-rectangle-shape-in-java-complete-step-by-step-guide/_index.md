---
category: general
date: 2026-07-03
description: Crie uma forma retangular em Java e aprenda como adicionar sombra à forma,
  aplicar efeito de sombra, definir transparência da forma e criar um documento em
  branco rapidamente.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- apply shadow effect
- set shape transparency
- create blank document
language: pt
og_description: Crie uma forma retangular em Java com sombra, transparência e um documento
  em branco. Siga este guia para dominar o manuseio de formas.
og_title: Criar forma de retângulo em Java – Tutorial completo de programação
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Create rectangle shape in Java and learn how to add shadow to shape,
    apply shadow effect, set shape transparency, and create blank document quickly.
  headline: Create rectangle shape in Java – Complete Step‑by‑Step Guide
  type: TechArticle
- description: Create rectangle shape in Java and learn how to add shadow to shape,
    apply shadow effect, set shape transparency, and create blank document quickly.
  name: Create rectangle shape in Java – Complete Step‑by‑Step Guide
  steps:
  - name: What if I want a different shadow color?
    text: 'Simply change the `setColor` call:'
  - name: Can I apply the same shadow to multiple shapes?
    text: 'Yes. Create one `ShadowEffect` instance, configure it, then reuse it:'
  - name: How do I change the shadow blur dynamically?
    text: Expose a UI slider that maps to `setBlurRadius`. Values between `2` and
      `12` are typical; larger numbers produce a “glow” rather than a crisp shadow.
  - name: What if I need the shape to float rather than be inline?
    text: 'Swap the wrap type:'
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Automation
title: Criar forma de retângulo em Java – Guia completo passo a passo
url: /pt/java/images-shapes/create-rectangle-shape-in-java-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar forma de retângulo em Java – Guia Completo Passo a Passo

Já se perguntou como **criar forma de retângulo** em um documento Word usando Java? Você não está sozinho — desenvolvedores frequentemente precisam de uma maneira rápida de adicionar gráficos geométricos e, em seguida, dar a eles uma sombra sutil para que o layout pareça mais refinado. Neste tutorial vamos percorrer todo o processo: desde a criação de um **documento em branco** até **adicionar sombra à forma**, **aplicar efeito de sombra** e até **definir transparência da forma** para um visual profissional.

O trecho de código abaixo é um exemplo totalmente funcional que você pode copiar‑colar no seu projeto. Nenhuma documentação externa é necessária — basta seguir os passos, entender o “porquê” e você gerará retângulos com sombra em segundos.

## O que você aprenderá

- Como **criar forma de retângulo** programaticamente com Aspose.Words for Java.  
- As chamadas exatas necessárias para **adicionar sombra à forma** e configurar suas propriedades visuais.  
- Formas de **aplicar efeito de sombra** e ajustar parâmetros como deslocamento, raio de desfoque e cor.  
- Técnicas para **definir transparência da forma** para uma aparência mais sutil.  
- Como **criar documento em branco**, inserir a forma e salvar o resultado.

> **Dica de especialista:** Todas essas ações são realizadas em uma única instância de `Document`, o que significa que você pode encadeá‑las sem se preocupar com I/O de arquivos intermediários.

## Pré‑requisitos

Antes de mergulharmos, certifique‑se de que você tem:

- Java 17 (ou qualquer JDK recente) instalado.  
- Biblioteca Aspose.Words for Java adicionada ao seu projeto (coordenadas Maven: `com.aspose:aspose-words:23.12`).  
- Um IDE Java ou um editor de texto simples — nada sofisticado, apenas um local para compilar e executar.

Se estiver faltando algum desses itens, baixe o JDK da Oracle e inclua a dependência Aspose via Maven ou Gradle. Uma vez configurado, você está pronto para começar.

## Etapa 1: **Criar documento em branco** – a tela para tudo

A primeira coisa que você precisa é um objeto `Document` vazio. Pense nele como uma folha de papel nova; sem ele, não há onde colocar seu retângulo.

```java
// Step 1: Create a new blank document
Document document = new Document();
```

Por que começar com um documento em branco? Porque toda forma vive dentro de uma `Section`, e um `Document` recém‑instanciado já contém uma seção padrão com um corpo pronto para receber nós. Pular esta etapa forçaria a criação manual de seções mais tarde, o que adiciona complexidade desnecessária.

## Etapa 2: **Criar forma de retângulo** e definir seu tamanho

Agora que temos uma tela, vamos **criar forma de retângulo**. A classe `Shape` recebe a referência ao documento e um `ShapeType`. Aqui escolhemos `RECTANGLE` e definimos largura/altura em pontos (1 pt ≈ 1/72 polegada).

```java
// Step 2: Insert a rectangle shape and define its size and layout
Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
rectangleShape.setWidth(200);   // 200 pt ≈ 2.78 inches
rectangleShape.setHeight(100);  // 100 pt ≈ 1.39 inches
rectangleShape.setWrapType(WrapType.INLINE);
```

Por que definir `WrapType.INLINE`? O empacotamento inline faz a forma se comportar como um caractere no parágrafo, garantindo que ela se mova junto ao texto ao redor. Se precisar de comportamento flutuante, troque para `WrapType.SQUARE` ou `WrapType.TOP_BOTTOM`.

## Etapa 3: **Aplicar efeito de sombra** – dar profundidade ao retângulo

Um retângulo plano parece… bem, plano. Adicionar uma sombra faz com que ele se destaque. Vamos **aplicar efeito de sombra** criando uma instância de `ShadowEffect` e ajustando suas propriedades visuais.

```java
// Step 3: Create a shadow effect and configure its visual properties
ShadowEffect shadowEffect = new ShadowEffect();
shadowEffect.setColor(Color.getGray(0.5));   // medium gray
shadowEffect.setOffsetX(5);                  // horizontal offset (points)
shadowEffect.setOffsetY(5);                  // vertical offset (points)
shadowEffect.setBlurRadius(8);               // softness of the shadow
shadowEffect.setTransparency(0.3);           // 30 % transparent
```

Vamos detalhar um pouco:

- **Color** – `Color.getGray(0.5)` gera um cinza de 50 %, que é neutro e funciona na maioria dos fundos.  
- **OffsetX/Y** – Valores positivos empurram a sombra para a direita e para baixo; valores negativos a moveriam para a esquerda/acima.  
- **BlurRadius** – Valores maiores criam uma sombra mais suave e difusa.  
- **Transparency** – Varia de `0` (opaco) a `1` (totalmente transparente). Aqui escolhemos `0.3` para um efeito sutil.

## Etapa 4: **Adicionar sombra à forma** – vincular o efeito

Criar o efeito não basta; precisamos **adicionar sombra à forma** atribuindo o objeto `ShadowEffect` ao retângulo.

```java
// Step 4: Apply the shadow effect to the rectangle shape
rectangleShape.setShadowEffect(shadowEffect);
```

Nos bastidores, esta chamada atualiza a marcação OpenXML subjacente (`<w:shdw>`) que o Word usa para renderizar sombras. Se você inspecionar o `.docx` salvo, verá um elemento `<w:effect>` preenchido com os parâmetros que definimos.

## Etapa 5: **Definir transparência da forma** – opcional, mas frequentemente útil

Às vezes você quer que o próprio retângulo seja semitransparente, permitindo que o texto de fundo apareça. A classe `Shape` expõe `setFillColor` e `setFillTransparency`. Aqui está um exemplo rápido que torna o retângulo 40 % transparente:

```java
// Optional: make the rectangle partially transparent
rectangleShape.setFillColor(Color.getWhite());
rectangleShape.setFillTransparency(0.4); // 40 % transparent
```

Por que fazer isso? Imagine uma marca d'água ou um destaque onde o conteúdo subjacente deve permanecer legível. Ajuste o valor de transparência conforme a linguagem de design que você deseja.

## Etapa 6: Inserir a forma no documento

Construímos o retângulo, adicionamos a sombra e (opcionalmente) definimos sua transparência. O passo final é **adicionar a forma à primeira seção do documento**.

```java
// Step 5: Add the shape to the first section of the document
document.getFirstSection().getBody().appendChild(rectangleShape);
```

Anexar a forma ao corpo a coloca ao final do primeiro parágrafo. Se precisar de um ponto de inserção específico, recupere o `Paragraph` alvo e use `insertBefore` ou `insertAfter`.

## Etapa 7: Salvar o documento – ver o resultado

Todo esse trabalho culmina em uma única chamada `save`. Escolha um caminho que faça sentido para o seu ambiente.

```java
// Step 6: Save the document with the shadowed shape
document.save("YOUR_DIRECTORY/ShadowShape.docx");
```

Abra o `ShadowShape.docx` resultante no Microsoft Word ou LibreOffice, e você verá um retângulo nítido com uma sombra cinza suave, levemente transparente se você manteve a etapa opcional. O visual corresponde aos parâmetros que definimos programaticamente.

---

![create rectangle shape with shadow in a Word document](https://example.com/images/rectangle-shadow.png "create rectangle shape with shadow")

*Texto alternativo da imagem:* **criar forma de retângulo com sombra** – representação visual do resultado final.

## Perguntas Frequentes & Casos de Borda

### E se eu quiser uma cor de sombra diferente?

Basta mudar a chamada `setColor`:

```java
shadowEffect.setColor(Color.getRed()); // bright red shadow
```

Lembre‑se de que sombras excessivamente vivas podem parecer pouco profissionais; tons sutis geralmente funcionam melhor.

### Posso aplicar a mesma sombra a várias formas?

Sim. Crie uma instância de `ShadowEffect`, configure‑a e reutilize‑a:

```java
Shape circle = new Shape(document, ShapeType.OVAL);
circle.setShadowEffect(shadowEffect); // same effect as rectangle
```

Apenas evite mutar o `ShadowEffect` depois de tê‑lo anexado a outras formas, a menos que você queira atualizar todas elas.

### Como mudar o desfoque da sombra dinamicamente?

Exponha um controle deslizante na UI que mapeie para `setBlurRadius`. Valores entre `2` e `12` são típicos; números maiores produzem um “brilho” em vez de uma sombra nítida.

### E se eu precisar que a forma flutue em vez de ficar inline?

Troque o tipo de empacotamento:

```java
rectangleShape.setWrapType(WrapType.SQUARE);
rectangleShape.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
rectangleShape.setHorizontalAlignment(HorizontalAlignment.CENTER);
```

Formas flutuantes dão mais liberdade de layout, mas exigem lógica extra de posicionamento.

## Exemplo Completo Funcional

Abaixo está o programa completo, pronto para copiar‑colar, que incorpora todas as etapas discutidas. Execute‑o como uma aplicação Java padrão.

```java
import com.aspose.words.*;

public class ShadowRectangleDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a blank document
        Document document = new Document();

        // 2. Build the rectangle shape
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(200);
        rectangleShape.setHeight(100);
        rectangleShape.setWrapType(WrapType.INLINE);

        // 3. Configure shadow effect
        ShadowEffect shadowEffect = new ShadowEffect();
        shadowEffect.setColor(Color.getGray(0.5));
        shadowEffect.setOffsetX(5);
        shadowEffect.setOffsetY(5);
        shadowEffect.setBlurRadius(8);
        shadowEffect.setTransparency(0.3);

        // 4. Apply shadow to the rectangle
        rectangleShape.setShadowEffect(shadowEffect);

        // 5. (Optional) Make rectangle semi‑transparent
        rectangleShape.setFillColor(Color.getWhite());
        rectangleShape.setFillTransparency(0.4);

        // 6. Insert shape into the document
        document.getFirstSection().getBody().appendChild(rectangleShape);

        // 7. Save the file
        document.save("ShadowShape.docx");
    }
}
```

**Saída esperada:** Ao abrir `ShadowShape.docx`, você verá um retângulo branco, 200 × 100 pt, centralizado no primeiro parágrafo, com uma sombra cinza‑média deslocada 5 pt, desfocada com raio 8 e 30 % transparente. O próprio retângulo tem 40 % de transparência, permitindo que qualquer texto subjacente apareça.

## Conclusão

Acabamos de **criar forma de retângulo** do zero, **adicionar sombra à forma**, **aplicar efeito de sombra** e ainda **definir transparência da forma** — tudo enquanto **criamos documento em branco** como base. A abordagem é direta, depende da API fluente da Aspose.Words e pode ser estendida para círculos, estrelas ou polígonos personalizados.

Qual será o próximo passo no seu roadmap? Experimente trocar `ShapeType.RECTANGLE` por `ShapeType.OVAL` para gerar círculos com sombra, ou experimente preenchimentos gradientes para

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}