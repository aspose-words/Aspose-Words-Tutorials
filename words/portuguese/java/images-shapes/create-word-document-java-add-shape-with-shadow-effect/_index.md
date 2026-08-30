---
category: general
date: 2026-06-30
description: Criar exemplo em Java para documento Word que mostre como adicionar forma
  ao documento, definir a cor de preenchimento da forma e aplicar efeito de sombra
  à forma em apenas algumas linhas.
draft: false
keywords:
- create word document java
- how to add shadow to shape
- add shape to word document
- set shape fill color
- apply shadow effect shape
language: pt
og_description: Criar tutorial Java para documento Word mostrando como adicionar forma
  ao documento Word, definir a cor de preenchimento da forma e aplicar efeito de sombra
  à forma.
og_title: Criar documento Word em Java – Adicionar forma com efeito de sombra
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: Create word document java example that shows how to add shape to word
    document, set shape fill color, and apply shadow effect shape in just a few lines.
  headline: Create Word Document Java – Add Shape with Shadow Effect
  type: TechArticle
- description: Create word document java example that shows how to add shape to word
    document, set shape fill color, and apply shadow effect shape in just a few lines.
  name: Create Word Document Java – Add Shape with Shadow Effect
  steps:
  - name: Creates the shape object.
    text: Creates the shape object.
  - name: Positions it at the current cursor location (top‑left of the page by default).
    text: Positions it at the current cursor location (top‑left of the page by default).
  - name: Adds it to the document’s internal node collection.
    text: Adds it to the document’s internal node collection.
  type: HowTo
tags:
- Java
- Aspose.Words
- Word Automation
- Shapes
title: Criar documento Word em Java – Adicionar forma com efeito de sombra
url: /pt/java/images-shapes/create-word-document-java-add-shape-with-shadow-effect/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar Documento Word Java – Adicionar Forma com Efeito de Sombra

Já precisou de código **create word document java** que desenha um retângulo e lhe dá uma sombra sutil? Você não é o único. Seja gerando relatórios, faturas ou um simples folheto, poder **add shape to word document** programaticamente economiza horas de ajustes manuais.  

Neste guia, percorreremos um exemplo completo, pronto‑para‑executar, que não só cria um novo arquivo Word, mas também **set shape fill color**, **how to add shadow to shape**, e finalmente **apply shadow effect shape** com Aspose.Words for Java. Sem enrolação — apenas os passos exatos que você pode copiar‑colar no seu IDE.

> **Dica profissional:** Se você é novo no Aspose.Words, certifique‑se de que tem o JAR mais recente no seu classpath. A API que usamos funciona com a versão 23.10 e posteriores.

## O que você vai construir

Ao final deste tutorial, você terá um arquivo `.docx` que contém:

* Um documento Word em branco criado do zero.
* Um retângulo amarelo (150 × 80 pts) inserido na primeira página.
* Uma sombra cinza suave deslocada alguns pontos, dando à forma um aspecto elevado.
* Tudo isso alcançado com apenas algumas instruções Java.

Sem modelos externos, sem XML complicado — código Java puro que qualquer pessoa pode executar.

## Criar Documento Word Java – Inserir uma Forma

A primeira coisa que precisamos é um novo objeto `Document` e um `DocumentBuilder`. Pense no builder como uma caneta que nos permite desenhar dentro do documento.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a builder to add content.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Por que isso importa:* `Document` representa o arquivo inteiro, enquanto `DocumentBuilder` nos fornece métodos convenientes como `insertShape`. Sem o builder, teríamos que manipular nós de baixo nível diretamente — muito mais trabalho.

## Adicionar Forma ao Documento Word – Inserindo o Retângulo

Agora realmente **add shape to word document**. No nosso caso é um retângulo, mas você poderia escolher qualquer `ShapeType` que o Aspose suporte (elipse, seta, etc.).

```java
        // Step 2: Insert a rectangle shape of size 150x80 points.
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 150, 80);
```

Essa única linha faz três coisas:

1. Cria o objeto shape.  
2. Posiciona‑o na localização atual do cursor (canto superior‑esquerdo da página por padrão).  
3. Adiciona‑o à coleção interna de nós do documento.  

Se você já se perguntou *how to add shadow to shape* depois disso, continue lendo — porque vamos chegar lá a seguir.

## Definir Cor de Preenchimento da Forma – Personalizando a Aparência

Um retângulo branco simples não é muito empolgante, então vamos **set shape fill color** para algo vibrante. Usaremos a classe `java.awt.Color` do Java, que o Aspose aceita diretamente.

```java
        // Step 3: Set the shape's fill color to yellow.
        rectangle.setFillColor(java.awt.Color.YELLOW);
```

Sinta‑se à vontade para trocar `YELLOW` por `RED`, `GREEN`, ou qualquer valor RGB personalizado (`new Color(123, 45, 67)`). A cor de preenchimento é a superfície que você verá antes que a sombra entre em ação.

## Como Adicionar Sombra à Forma – Configurando a Sombra

É aqui que a mágica acontece. Aspose.Words expõe um objeto `ShadowEffect` que nos permite ajustar finamente a aparência da sombra.

```java
        // Step 4: Configure a custom shadow effect for the shape.
        ShadowEffect shadow = rectangle.getShadowEffect();
        shadow.setColor(java.awt.Color.GRAY);      // Shadow color
        shadow.setBlurRadius(5.0);                 // Softness of the shadow
        shadow.setOffsetX(4.0);                    // Horizontal offset
        shadow.setOffsetY(4.0);                    // Vertical offset
        shadow.setTransparency(0.3);               // Shadow opacity (0 = opaque, 1 = fully transparent)
```

**Por que cada propriedade importa:**

| Property | O que faz | Valores típicos |
|----------|-----------|----------------|
| `setColor` | Determina o tom da sombra. Cinza funciona na maioria dos casos, mas você pode usar algo ousado como `Color.BLUE`. | Qualquer `java.awt.Color` |
| `setBlurRadius` | Controla o quão suaves as bordas aparecem. Números maiores dão um aspecto mais difuso. | 0 – 10 (float) |
| `setOffsetX` / `setOffsetY` | Move a sombra para a direita/esquerda e para cima/baixo. Valores positivos deslocam a sombra para baixo‑e‑direita. | -10 – 10 |
| `setTransparency` | Define a opacidade; 0 é sólido, 1 é invisível. | 0.0 – 1.0 |

Se você está se perguntando **how to add shadow to shape** sem bagunçar o layout, a chave é manter os deslocamentos modestos. Muito grandes e a sombra pode vazar para a próxima página.

## Aplicar Sombra à Forma – Salvando o Documento

Com a forma estilizada e a sombra configurada, só precisamos persistir o arquivo.

```java
        // Step 5: Save the document with the shaped shadow.
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

Substitua `YOUR_DIRECTORY` por um caminho absoluto ou relativo que exista na sua máquina. Após executar o programa, abra `ShadowShape.docx` no Microsoft Word ou LibreOffice — você deverá ver um retângulo amarelo flutuando acima da página, graças à sombra cinza que aplicamos.

## Verificar o Resultado – O que observar

Ao abrir o arquivo gerado:

* O retângulo deve estar centralizado onde o cursor começou (canto superior‑esquerdo da página por padrão).  
* Seu preenchimento é amarelo brilhante.  
* Um leve desfoque cinza está 4 pts à direita e para baixo, com cerca de 30 % de transparência.  

Se a sombra parecer muito forte, diminua o `BlurRadius` ou aumente a `Transparency`. Se a forma em si não estiver visível, verifique novamente a chamada `setFillColor` — talvez a cor escolhida se misture ao fundo da página.

## Armadilhas Comuns & Casos de Borda

| Issue | Causa | Correção |
|-------|-------|----------|
| **Shadow disappears** | `Transparency` definido como `1.0` (totalmente transparente). | Use um valor menor, por exemplo, `0.3`. |
| **Shape not visible** | A cor de preenchimento combina com o fundo da página (geralmente branco). | Escolha uma cor contrastante com `setFillColor`. |
| **Shadow clips on page margin** | Deslocamentos empurram a sombra fora da área imprimível. | Reduza `OffsetX`/`OffsetY` ou aumente as margens da página via `PageSetup`. |
| **Compilation error: `cannot find symbol ShadowEffect`** | Uso de uma versão mais antiga do Aspose.Words que não possui suporte a sombra. | Atualize para Aspose.Words 23.10+ (a API introduziu `ShadowEffect` em 22.12). |

## Próximos Passos – Indo Além do Básico

Agora que você sabe como **create word document java**, **add shape to word document**, **set shape fill color**, **how to add shadow to shape**, e **apply shadow effect shape**, pode se perguntar o que mais pode fazer. Aqui estão algumas ideias:

* **Cores dinâmicas** – Obtenha valores RGB de um banco de dados para colorir formas com base no status.  
* **Múltiplas sombras** – Empilhe duas configurações `ShadowEffect` clonando a forma e deslocando cada cópia.  
* **Texto dentro das formas** – Use `Shape.getTextFrame()` para inserir uma legenda ou rótulo.  
* **Exportar para PDF** – Chame `document.save("output.pdf", SaveFormat.PDF)` para obter uma versão pronta para impressão com a mesma fidelidade visual.  

Cada um desses se baseia no mesmo padrão central que demonstramos: criar um documento, inserir uma forma, estilizar e salvar.

## Exemplo Completo Funcional (Pronto para Copiar‑Colar)

```java
import com.aspose.words.*;
import java.awt.Color;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a new blank document and a builder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Insert a rectangle shape (150 × 80 pts).
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 150, 80);

        // 3️⃣ Set the shape's fill color to yellow.
        rectangle.setFillColor(Color.YELLOW);

        // 4️⃣ Configure the shadow effect.
        ShadowEffect shadow = rectangle.getShadowEffect();
        shadow.setColor(Color.GRAY);        // Shadow color
        shadow.setBlurRadius(5.0);          // Softness
        shadow.setOffsetX(4.0);             // Horizontal offset
        shadow.setOffsetY(4.0);             // Vertical offset
        shadow.setTransparency(0.3);        // 30 % transparent

        // 5️⃣ Save the document.
        document.save("ShadowShape.docx");
    }
}
```

Executar a classe produz `ShadowShape.docx` no diretório de trabalho atual. Abra‑o, e você verá o resultado exato descrito anteriormente.

## Conclusão

Acabamos de mostrar como **create word document java** do zero, **add shape to word document**, **set shape fill color**, **how to add shadow to shape**, e finalmente **apply shadow effect shape** — tudo com um exemplo de código compacto e fácil de entender.  

A abordagem é deliberadamente simples para que você possa adaptá‑la a cenários mais complexos — seja precisando de múltiplas formas, cores diferentes ou sombras estilo animado. Lembre‑se de ficar atento à compatibilidade de versões da API, e não hesite em ajustar os parâmetros da sombra para adequar ao seu estilo de design.

Tem alguma variação que tentou? Talvez você tenha colocado uma imagem atrás do retângulo ou adicionado uma tabela dentro da forma. Deixe um comentário abaixo; adoro saber como os desenvolvedores levam esses exemplos adiante. Feliz codificação


## O que Você Deve Aprender a Seguir?

Os tutoriais a seguir cobrem tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Criar Documento Word Java – Adicionar Forma Retangular com Efeito de Sombra](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Como Criar Documentos PDF com Aspose.Words para Java | API de Processamento de Documentos](/words/english/java/)
- [Aspose.Words Java: Guia Abrangente de Processamento de Documentos Word](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}