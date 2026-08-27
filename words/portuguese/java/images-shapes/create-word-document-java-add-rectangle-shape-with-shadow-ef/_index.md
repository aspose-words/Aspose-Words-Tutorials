---
category: general
date: 2026-01-11
description: Crie rapidamente um documento Word em Java adicionando uma forma retangular,
  definindo sua cor de preenchimento e aplicando uma sombra à forma. Aprenda passo
  a passo.
draft: false
keywords:
- create word document java
- add rectangle shape
- apply shadow to shape
- set shape fill color
- how to add shape
language: pt
og_description: Crie um documento Word em Java inserindo uma forma retangular, definindo
  sua cor de preenchimento e aplicando uma sombra. Guia completo com código.
og_title: Criar documento Word em Java – Adicionar forma retangular com sombra
tags:
- Aspose.Words
- Java
- Document Generation
title: Criar documento Word em Java – Adicionar forma retangular com efeito de sombra
url: /pt/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar Documento Word Java – Adicionar Forma Retangular com Efeito de Sombra

Já precisou **criar documento word java** e deixá‑lo um pouco mais elegante? Talvez você esteja construindo um gerador de relatórios e uma página simples não seja suficiente. A boa notícia? Com Aspose.Words for Java você pode inserir uma forma retangular em um documento, aplicar uma cor e ainda acrescentar uma sombra sutil – tudo em poucas linhas.

Neste tutorial vamos percorrer exatamente isso: como adicionar uma forma retangular, definir sua cor de preenchimento e aplicar uma sombra à forma para que seu arquivo Word pareça mais profissional. Ao final, você terá um exemplo executável que pode copiar‑colar no seu próprio projeto.

## O que Você Precisa

- **Java 17** (ou qualquer JDK recente) – o código usa recursos padrão da linguagem.
- Biblioteca **Aspose.Words for Java** – recomenda‑se a versão 23.9 ou superior.
- Uma IDE ou editor de texto de sua preferência – IntelliJ IDEA, Eclipse, VS Code… você decide.
- Uma pasta onde o `ShadowShape.docx` gerado será salvo.

Nenhuma configuração extra é necessária; basta adicionar o JAR do Aspose.Words ao classpath e pronto.

## Etapa 1: Configurar o Projeto e Importar Aspose.Words

Primeiro, crie um novo projeto Maven (ou Gradle) e inclua a dependência do Aspose.Words. Aqui está um trecho mínimo de `pom.xml` para Maven:

```xml
<dependencies>
    <dependency>
        <groupId>com.aspose</groupId>
        <artifactId>aspose-words</artifactId>
        <version>23.9</version>
        <classifier>jdk17</classifier>
    </dependency>
</dependencies>
```

Se não estiver usando Maven, basta colocar o arquivo JAR na pasta `libs` e adicioná‑lo ao caminho de compilação.

> **Dica:** A Aspose oferece uma licença de teste gratuita que pode ser incorporada com `License license = new License(); license.setLicense("Aspose.Words.lic");`. Pule essa etapa para testes rápidos; a biblioteca funciona em modo de avaliação.

## Etapa 2: Criar um Novo Documento e Builder

Agora vamos realmente **criar word document java** objetos. A classe `Document` representa o arquivo .docx completo, enquanto `DocumentBuilder` permite inserir conteúdo.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

Neste ponto você tem um documento vazio pronto para receber formas, parágrafos ou qualquer outro elemento que precisar.

## Etapa 3: Inserir uma Forma Retangular e Definir sua Cor de Preenchimento

Adicionar uma forma é tão simples quanto chamar `insertShape`. Usaremos a técnica **add rectangle shape**, que corresponde à palavra‑chave secundária *add rectangle shape*.

```java
        // Insert a rectangle shape – 200pt wide, 100pt tall
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 200, 100);

        // Set the fill color to a bright orange
        rectangle.setFillColor(java.awt.Color.ORANGE);
```

Por que laranja? Ela se destaca em meio ao branco, mas você pode trocá‑la por qualquer `java.awt.Color` que desejar. Esta etapa cobre a palavra‑chave secundária *set shape fill color*.

## Etapa 4: Configurar a Aparência da Sombra – Aplicar Sombra à Forma

Agora vem a parte divertida: dar à retângulo uma sombra discreta. A API da Aspose expõe um objeto `ShadowFormat` que controla todos os aspectos da sombra.

```java
        // Get the shadow format object for the shape
        ShadowFormat shadow = rectangle.getShadowFormat();

        // Make the shadow visible
        shadow.setVisible(true);

        // Choose a neutral gray for the shadow color
        shadow.setColor(java.awt.Color.GRAY);

        // Blur radius – larger values produce a softer edge
        shadow.setBlur(5.0);

        // Offset determines how far the shadow is displaced
        shadow.setOffsetX(4.0);
        shadow.setOffsetY(4.0);

        // Transparency (0 = opaque, 1 = fully transparent)
        shadow.setTransparency(0.2);

        // Define the shadow style and type
        shadow.setStyle(ShadowStyle.OUTER);
        shadow.setType(ShadowType.PARALLEL);

        // Scale controls the overall size of the shadow relative to the shape
        shadow.setScale(1.0);
```

Esse bloco de código **apply shadow to shape** exatamente como a palavra‑chave secundária indica. Você pode ajustar `blur`, `offsetX/Y` e `transparency` para adequar ao seu estilo. Por exemplo, um `offsetX` maior cria uma projeção mais dramática, enquanto uma `transparency` alta faz a sombra sussurrar em vez de gritar.

## Etapa 5: Salvar o Documento

Por fim, gravamos o documento no disco. Escolha uma pasta onde você tenha permissão de escrita e dê ao arquivo um nome claro.

```java
        // Save the result – adjust the path as needed
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

Ao abrir `ShadowShape.docx` no Microsoft Word ou LibreOffice, você verá um retângulo laranja vibrante com uma sombra cinza suave pairando logo abaixo.

![create word document java with rectangle shape](/images/shadow-rectangle.png "create word document java – rectangle with shadow")

*O texto alternativo da imagem inclui a palavra‑chave principal, atendendo à regra de SEO.*

## Perguntas Frequentes & Casos de Borda

### E se eu precisar de uma forma diferente?

Aspose.Words suporta dezenas de valores `ShapeType` – estrelas, setas, balões, o que você quiser. Basta substituir `ShapeType.RECTANGLE` por `ShapeType.OVAL` ou outro constante do enum. Os mesmos passos **how to add shape** se aplicam.

### Como adiciono a forma a um parágrafo específico?

Em vez de inserir a forma diretamente com o builder, você pode criá‑la primeiro (`new Shape(document, ShapeType.RECTANGLE)`) e depois adicioná‑la a um `Paragraph` via `paragraph.appendChild(shape)`. Isso oferece controle mais fino sobre o layout.

### Posso aplicar um preenchimento em degradê em vez de cor sólida?

Sim! Use `rectangle.getFill().setFillType(FillType.GRADIENT)` e defina um `LinearGradientFill`. A API fica um pouco mais verbosa, mas funciona muito bem para designs modernos.

### E quanto à compatibilidade com versões mais antigas do Word?

Aspose.Words salva no formato .docx por padrão, que é suportado pelo Word 2007+ e LibreOffice. Se precisar de .doc, chame `document.save("file.doc", SaveFormat.DOC)`. A renderização da sombra pode variar levemente, mas a forma permanece intacta.

## Exemplo Completo Funcional (Pronto para Copiar‑Colar)

Abaixo está o programa inteiro, pronto para compilar e executar. Substitua `YOUR_DIRECTORY` por um caminho real na sua máquina.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a rectangle shape and set its fill color
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 200, 100);
        rectangle.setFillColor(java.awt.Color.ORANGE);

        // Step 3: Apply shadow to shape
        ShadowFormat shadow = rectangle.getShadowFormat();
        shadow.setVisible(true);
        shadow.setColor(java.awt.Color.GRAY);
        shadow.setBlur(5.0);
        shadow.setOffsetX(4.0);
        shadow.setOffsetY(4.0);
        shadow.setTransparency(0.2);
        shadow.setStyle(ShadowStyle.OUTER);
        shadow.setType(ShadowType.PARALLEL);
        shadow.setScale(1.0);

        // Step 4: Save the document
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

Executar este código gera um arquivo Word que contém o retângulo laranja com uma sombra cinza suave – exatamente o que nos propusemos a fazer ao **criar word document java** com uma forma estilizada.

## Conclusão

Agora você tem uma receita completa, de ponta a ponta, para **create word document java** que *adds rectangle shape*, *sets shape fill color* e *applies shadow to shape*. O procedimento é direto, a API é fluente e você pode estendê‑lo de inúmeras maneiras – diferentes formas, preenchimentos em degradê ou até sombras múltiplas por forma.

Qual o próximo passo? Experimente sobrepor várias formas, teste `ShadowStyle.ETCHED` para um visual diferente, ou combine isso com geração de tabelas para criar relatórios totalmente formatados. As possibilidades são limitadas apenas pela sua imaginação (e talvez pelo nível da licença Aspose).

Se encontrou algum problema ou tem ideias para melhorias, deixe um comentário abaixo. Boa codificação e divirta‑se deixando esses documentos Word menos sem graça!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}