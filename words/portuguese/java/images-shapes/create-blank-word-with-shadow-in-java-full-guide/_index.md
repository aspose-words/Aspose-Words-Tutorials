---
category: general
date: 2026-05-04
description: Crie um documento Word em branco em Java e aprenda como definir a cor
  da sombra, o desfoque e o deslocamento para formas – tutorial rápido.
draft: false
keywords:
- create blank word
- set shadow color
- how to add shadow
- how to set blur
- how to set offset
language: pt
og_description: Crie um documento Word em branco em Java e aprenda como definir a
  cor da sombra, o desfoque e o deslocamento para formas. Siga este tutorial passo
  a passo.
og_title: Criar palavra em branco com sombra em Java – Guia completo
tags:
- Aspose.Words
- Java
- Document Automation
title: Criar palavra em branco com sombra em Java – Guia completo
url: /pt/java/images-shapes/create-blank-word-with-shadow-in-java-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar documento Word em branco com sombra em Java – Guia completo

Já precisou **criar documento Word em branco** a partir do código e deixá‑lo um pouco mais elegante? Você não está sozinho. Em muitos projetos de relatórios ou geração de modelos, a primeira coisa que se faz é criar um documento Word vazio e, em seguida, adicionar uma forma com sombra para dar aquele toque refinado.  

Neste tutorial vamos percorrer exatamente isso — como criar um documento Word em branco usando Aspose.Words for Java, **como adicionar sombra** a uma forma, e os detalhes de **definir cor da sombra**, **como definir desfoque** e **como definir deslocamento**. Ao final você terá um arquivo `.docx` pronto para uso que exibe um retângulo com uma sombra vermelha levemente desfocada e semitransparente.

## O que você vai precisar

- **Aspose.Words for Java** (qualquer versão recente; o código funciona com 23.9+)
- JDK 8 ou superior
- Uma IDE ou editor de texto simples mais um terminal
- Conhecimento básico de Java — nada sofisticado, apenas a capacidade de executar um método `main`

Nenhuma configuração extra de Maven ou Gradle é necessária para a demonstração; basta colocar o JAR da Aspose no seu classpath e você está pronto para começar.

---

![exemplo de documento Word em branco com sombra](image-placeholder.png){: .center alt="exemplo de documento Word em branco com sombra"}

## Criar documento Word em branco – Inicializando o Document

O primeiro passo é criar um novo arquivo Word vazio. Pense nele como uma tela limpa onde você poderá desenhar formas, tabelas ou texto posteriormente.

```java
import com.aspose.words.*;

public class ShadowDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank Word document
        Document document = new Document();

        // Step 2: Initialise a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(document);
```

> **Por que isso importa:** `Document` representa todo o pacote `.docx`. Ao criá‑lo com o construtor padrão você está efetivamente **criar documento Word em branco** – não há conteúdo, nem seções, apenas a estrutura do arquivo pronta para ser preenchida.

## Como adicionar sombra a uma forma

Agora que temos um documento limpo, vamos inserir um retângulo que receberá nossa sombra. É aqui que a magia visual começa.

```java
        // Step 3: Insert a rectangle shape that will receive a custom shadow
        Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 150, 80);
```

> **Dica profissional:** A chamada `insertShape` adiciona automaticamente a forma ao parágrafo atual, portanto você não precisa gerenciar o posicionamento manualmente, a menos que deseje um posicionamento absoluto.

## Definir cor da sombra – fazendo a sombra se destacar

Uma sombra sem cor é apenas um borrão cinza, que pode parecer plana. Definindo a cor da sombra você pode combinar com a identidade visual ou simplesmente fazê‑la sobressair.

```java
        // Step 4a: Make the shadow visible and set its color
        rectangleShape.getShadowFormat().setVisible(true);
        rectangleShape.getShadowFormat().setColor(java.awt.Color.RED); // set shadow color
```

> **O que está acontecendo:** `ShadowFormat` controla todos os aspectos visuais da sombra. Ativar `setVisible(true)` liga o efeito, e `setColor` permite escolher qualquer `java.awt.Color`. No nosso exemplo escolhemos vermelho para demonstrar claramente **definir cor da sombra**.

## Como definir desfoque para um efeito sutil

Uma sombra nítida e de bordas duras pode parecer agressiva. Adicionar desfoque suaviza as bordas, proporcionando um aspecto mais natural.

```java
        // Step 4b: Define how fuzzy the shadow should be
        rectangleShape.getShadowFormat().setBlur(5.0); // how to set blur
```

> **Por que o desfoque importa:** O valor de `setBlur` é medido em pontos. Um valor de `5.0` cria uma difusão suave; aumente para uma sombra mais nebulosa, diminua para um contorno mais definido.

## Como definir deslocamento – posicionando a sombra

Deslocamentos determinam onde a sombra aparece em relação à forma. Pense neles como deslocamentos em X e Y.

```java
        // Step 4c: Position the shadow horizontally and vertically
        rectangleShape.getShadowFormat().setOffsetX(8.0); // how to set offset (horizontal)
        rectangleShape.getShadowFormat().setOffsetY(8.0); // how to set offset (vertical)
```

> **Explicação do deslocamento:** X positivo move a sombra para a direita, Y positivo move-a para baixo. Experimente números negativos se quiser que a sombra apareça do lado oposto.

## Ajustando a transparência

Se quiser que a sombra seja menos dominante, ajuste sua transparência. Esta etapa não é um requisito de palavra‑chave, mas completa o controle visual.

```java
        // Optional: Make the shadow semi‑transparent (30 % transparent)
        rectangleShape.getShadowFormat().setTransparency(0.3);
```

## Salvando o documento – veja o resultado

Por fim, grave o documento no disco. Você terá um `.docx` que pode ser aberto no Word, LibreOffice ou qualquer visualizador que suporte o formato.

```java
        // Step 5: Save the document with the shaped shadow
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

> **O que você deve ver:** Abra `ShadowShape.docx`. Uma única página mostrará um retângulo de 150 × 80 pt com uma sombra vermelha levemente desfocada deslocada 8 pt para baixo e para a direita. A sombra tem 30 % de transparência, de modo que o retângulo permanece claramente visível.

---

## Perguntas comuns e casos de borda

### E se eu precisar de uma forma diferente?

Substitua `ShapeType.RECTANGLE` por qualquer outro valor do enum (`ELLIPSE`, `CLOUD`, `CALLOUT`, etc.). As configurações de sombra funcionam da mesma forma em todas as formas.

### Posso aplicar a mesma sombra a várias formas sem repetir código?

Com certeza. Crie um método auxiliar:

```java
private static void applyShadow(Shape shape, java.awt.Color color,
                                double blur, double offsetX, double offsetY,
                                double transparency) {
    shape.getShadowFormat().setVisible(true);
    shape.getShadowFormat().setColor(color);
    shape.getShadowFormat().setBlur(blur);
    shape.getShadowFormat().setOffsetX(offsetX);
    shape.getShadowFormat().setOffsetY(offsetY);
    shape.getShadowFormat().setTransparency(transparency);
}
```

Então chame `applyShadow(rectangleShape, Color.RED, 5.0, 8.0, 8.0, 0.3);` para qualquer forma.

### Isso funciona com versões mais antigas do Aspose?

A API `ShadowFormat` tem sido estável desde a versão 19.8, então você deve estar bem com a maioria das releases recentes. Se estiver usando uma build muito antiga, verifique o Javadoc de `ShadowFormat` para confirmar os nomes dos métodos.

### Como exportar para PDF mantendo a sombra?

Basta chamar `document.save("output.pdf");` após a criação da forma. Aspose.Words renderiza sombras corretamente em PDF, preservando desfoque e transparência.

---

## Recapitulação – criar documento Word em branco com sombra personalizada

Começamos **criando documento Word em branco** usando `new Document()`, inserimos um retângulo, **definimos cor da sombra**, aprendemos **como adicionar sombra**, ajustamos **como definir desfoque** e, por fim, configuramos **como definir deslocamento** para posicioná‑la corretamente. O código completo e executável está no snippet acima, e o arquivo resultante demonstra o efeito claramente.

---

## O que vem a seguir?

- **Experimente outras propriedades de sombra** como `ShadowFormat.setStyle(ShadowStyle.OUTER)` para estilos visuais diferentes.
- **Combine múltiplas formas**, cada uma com sua própria sombra, para construir diagramas complexos.
- **Adicione texto dentro da forma** usando `builder.insertHtml("<b>Hello</b>")` antes de inserir a forma, e então aplique a mesma lógica de sombra.
- **Explore outras opções de formatação** como estilo de linha, cor de preenchimento ou preenchimentos em gradiente — Aspose.Words oferece uma API rica para tudo isso.

Sinta‑se à vontade para ajustar o raio de desfoque, deslocamentos ou cores até que a sombra fique exatamente como deseja para a linguagem visual do seu documento. Boa codificação, e que seus arquivos Word gerados estejam sempre um pouco mais polidos!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}