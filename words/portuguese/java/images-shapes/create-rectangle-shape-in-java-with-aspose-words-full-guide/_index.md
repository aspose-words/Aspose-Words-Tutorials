---
category: general
date: 2026-07-06
description: Crie uma forma retangular em Java usando Aspose.Words – aprenda como
  adicionar sombra à forma, definir a transparência da forma e salvar o documento
  como PDF.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- set shape transparency
- save document as pdf
- how to add shadow
language: pt
og_description: Crie uma forma retangular em Java com Aspose.Words. Este guia mostra
  como adicionar sombra à forma, definir a transparência da forma e salvar o documento
  como PDF.
og_title: Criar forma retangular em Java – Tutorial Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-06'
  description: Create rectangle shape in Java using Aspose.Words – learn how to add
    shadow to shape, set shape transparency, and save document as PDF.
  headline: Create rectangle shape in Java with Aspose.Words – Full Guide
  type: TechArticle
- description: Create rectangle shape in Java using Aspose.Words – learn how to add
    shadow to shape, set shape transparency, and save document as PDF.
  name: Create rectangle shape in Java with Aspose.Words – Full Guide
  steps:
  - name: 1️⃣ What if I need a larger rectangle?
    text: Just change the width and height parameters in `insertShape`. Remember that
      72 pt = 1 in, so `400.0, 200.0` would give you a 5.5 × 2.8 inch rectangle.
  - name: 2️⃣ Can I use a different color for the shadow?
    text: Absolutely. The `ShadowFormat` class also exposes `setColor(java.awt.Color)`.
      For a subtle gray shadow, try `shadow.setColor(java.awt.Color.DARK_GRAY);`.
  - name: 3️⃣ Does `save document as pdf` work on all platforms?
    text: Yes. Aspose.Words for Java is platform‑agnostic; the same code runs on Windows,
      macOS, and Linux as long as you have a compatible JRE.
  - name: 4️⃣ How do I remove the shadow later?
    text: Call `rect.getShadowFormat().clear();` or set the `Visible` property to
      `false` (`shadow.setVisible(false);`).
  - name: 5️⃣ What about DPI and image quality?
    text: When saving to PDF, Aspose automatically uses 300 DPI for vector graphics
      like shapes, so you get crisp results regardless of zoom level.
  type: HowTo
tags:
- Aspose.Words
- Java
- PDF
- Shape
- Shadow
title: Criar forma retangular em Java com Aspose.Words – Guia Completo
url: /pt/java/images-shapes/create-rectangle-shape-in-java-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar forma retangular em Java com Aspose.Words – Guia Completo

Já se perguntou como **criar forma retangular** em Java sem lutar com APIs de desenho de baixo nível? Você não está sozinho. Muitos desenvolvedores precisam de uma maneira rápida e confiável de inserir um retângulo em um documento Word, dar a ele uma sombra sutil, ajustar sua transparência e, em seguida, gerar o resultado como PDF.  

Neste tutorial vamos percorrer exatamente isso—passo a passo, com código completo e executável. Ao final, você saberá **como adicionar sombra** a uma forma, como **definir a transparência da forma** e como **salvar o documento como PDF** usando Aspose.Words para Java. Sem enrolação, apenas orientações práticas que você pode copiar‑colar para o seu projeto hoje.

## O que você aprenderá

- A configuração mínima necessária para trabalhar com Aspose.Words em um projeto Java.  
- Como **criar forma retangular** programaticamente.  
- As chamadas exatas necessárias para **adicionar sombra à forma** e ajustar seu desfoque, deslocamento e opacidade.  
- Formas de **definir a transparência da forma** para que o retângulo se misture bem ao conteúdo ao redor.  
- O método mais simples para **salvar o documento como PDF** sem etapas de conversão adicionais.  

Se você está confortável com Java básico e tem um build Maven ou Gradle, está pronto para começar.

## Pré‑requisitos

- Java 8 ou superior.  
- Aspose.Words for Java 23.x (ou a versão mais recente disponível no momento da leitura).  
- Uma IDE ou ferramenta de linha de comando (IntelliJ, Eclipse, Maven, Gradle—escolha a que preferir).  

> **Dica de especialista:** A Aspose oferece uma licença temporária gratuita para avaliação. Pegue-a no portal da sua conta e coloque o arquivo `license.xml` no classpath; caso contrário, aparecerá uma marca d'água no PDF.

---

## Etapa 1: **Criar forma retangular** com Aspose.Words

A primeira coisa que precisamos é de um `Document` vazio e de um `DocumentBuilder`. O builder é o motor que nos permite inserir formas diretamente no fluxo do documento.

```java
import com.aspose.words.*;

public class RectangleShadowDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new empty Word document
        Document doc = new Document();

        // 2️⃣ Create a builder attached to the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3️⃣ Insert a rectangle shape – 200 points wide, 100 points tall
        Shape rect = builder.insertShape(ShapeType.RECTANGLE, 200.0, 100.0);
        // Optional: give the rectangle a light gray fill so the shadow is visible
        rect.getFillColor().setColor(java.awt.Color.LIGHT_GRAY);
```

**Por que isso importa:** `ShapeType.RECTANGLE` indica à Aspose que queremos um retângulo perfeito. A largura e a altura são expressas em pontos (1 pt ≈ 1/72 pol), o que oferece controle granular sobre o tamanho final.

---

## Etapa 2: **Adicionar sombra à forma**

Agora que temos um retângulo, vamos dar a ele uma sombra discreta. O objeto `ShadowFormat` expõe tudo que precisamos—raio de desfoque, deslocamento X/Y e até transparência.

```java
        // 4️⃣ Configure the shadow effect
        ShadowFormat shadow = rect.getShadowFormat();
        shadow.setBlur(5.0);          // Softness of the shadow edge
        shadow.setOffsetX(3.0);       // Horizontal shift (points)
        shadow.setOffsetY(3.0);       // Vertical shift (points)
        shadow.setTransparency(0.3); // 30 % transparent – makes it look natural
```

**Por que isso importa:** Uma sombra sem desfoque parece uma linha dura, o que raramente é o desejado pelos designers. A chamada `setBlur` suaviza as bordas, enquanto `setTransparency` permite que a sombra desapareça no fundo. Ajuste esses valores para atender às diretrizes da sua UI.

---

## Etapa 3: **Definir a transparência da forma**

Às vezes você precisa que o próprio retângulo seja semitransparente—talvez para sobrepor um logotipo ou marca d'água. A Aspose torna isso uma linha única.

```java
        // 5️⃣ Make the rectangle partially transparent (optional)
        rect.getFillFormat().setTransparency(0.2); // 20 % transparent fill
```

**Por que isso importa:** A transparência pode ser um salva‑vidas ao sobrepor formas. Observe que a transparência da sombra é independente, de modo que você pode ter uma forma tênue com uma sombra mais escura, se isso se adequar ao seu design.

---

## Etapa 4: **Salvar o documento como PDF**

Todo o trabalho visual está concluído; o passo final é persistir o documento. Aspose.Words pode gravar diretamente em PDF, eliminando a necessidade de uma biblioteca de conversão separada.

```java
        // 6️⃣ Persist the document as a PDF file
        String outPath = "output/RectangleWithShadow.pdf";
        doc.save(outPath, SaveFormat.PDF);
        System.out.println("PDF saved to: " + outPath);
    }
}
```

**Por que isso importa:** Ao especificar `SaveFormat.PDF`, a biblioteca cuida do embed de fontes, compressão de imagens e conformidade PDF/A nos bastidores. O arquivo resultante está pronto para distribuição, impressão ou arquivamento.

---

## Exemplo completo em funcionamento

Juntando tudo, aqui está a classe completa, pronta para ser executada. Copie‑cole, ajuste a pasta de saída e você terá um PDF com um retângulo que projeta uma sombra realista.

```java
import com.aspose.words.*;

public class RectangleShadowDemo {
    public static void main(String[] args) throws Exception {
        // Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert rectangle shape (200×100 points)
        Shape rect = builder.insertShape(ShapeType.RECTANGLE, 200.0, 100.0);
        rect.getFillColor().setColor(java.awt.Color.LIGHT_GRAY);

        // Add shadow effect
        ShadowFormat shadow = rect.getShadowFormat();
        shadow.setBlur(5.0);
        shadow.setOffsetX(3.0);
        shadow.setOffsetY(3.0);
        shadow.setTransparency(0.3);

        // Optional: make the rectangle itself partially transparent
        rect.getFillFormat().setTransparency(0.2);

        // Save as PDF
        String outPath = "output/RectangleWithShadow.pdf";
        doc.save(outPath, SaveFormat.PDF);
        System.out.println("PDF saved to: " + outPath);
    }
}
```

**Saída esperada:** Ao abrir `RectangleWithShadow.pdf`, você verá um retângulo cinza‑claro centralizado na primeira página, levemente elevado da página por uma sombra suave e semitransparente. A própria forma tem 20 % de transparência, permitindo que qualquer texto subjacente (se houver) apareça por trás dela.

---

## Perguntas frequentes & Casos de borda

### 1️⃣ E se eu precisar de um retângulo maior?

Basta alterar os parâmetros de largura e altura em `insertShape`. Lembre‑se de que 72 pt = 1 pol, então `400.0, 200.0` resultaria em um retângulo de 5,5 × 2,8 polegadas.

### 2️⃣ Posso usar uma cor diferente para a sombra?

Com certeza. A classe `ShadowFormat` também expõe `setColor(java.awt.Color)`. Para uma sombra cinza sutil, experimente `shadow.setColor(java.awt.Color.DARK_GRAY);`.

### 3️⃣ O `save document as pdf` funciona em todas as plataformas?

Sim. Aspose.Words for Java é independente de plataforma; o mesmo código roda no Windows, macOS e Linux, contanto que você tenha um JRE compatível.

### 4️⃣ Como removo a sombra mais tarde?

Chame `rect.getShadowFormat().clear();` ou defina a propriedade `Visible` como `false` (`shadow.setVisible(false);`).

### 5️⃣ E quanto a DPI e qualidade de imagem?

Ao salvar em PDF, a Aspose usa automaticamente 300 DPI para gráficos vetoriais como formas, garantindo resultados nítidos independentemente do nível de zoom.

---

## Dicas avançadas & Boas práticas

- **Processamento em lote:** Se precisar gerar dezenas de PDFs, reutilize uma única instância de `Document` e limpe apenas suas seções entre as iterações para reduzir a pressão do GC.  
- **Licenciamento:** Insira `License license = new License(); license.setLicense("license.xml");` no início do `main` para evitar a marca d'água de avaliação.  
- **Desempenho:** Renderizar sombras é barato para formas simples, mas caminhos complexos podem desacelerar a geração de PDFs. Faça profiling se estiver processando lotes grandes.  
- **Testes:** Use `Document.save(..., SaveFormat.DOCX)` primeiro para verificar se a forma aparece corretamente no Word antes de converter para PDF.

---

## Conclusão

Agora você sabe como **criar forma retangular** em Java com Aspose.Words, **adicionar sombra à forma**, **definir a transparência da forma** e, finalmente, **salvar o documento como PDF**. O código é autocontido, funciona com a versão mais recente da biblioteca Aspose e demonstra as chamadas de API essenciais que você precisará na maioria dos cenários de automação de documentos.

Pronto para o próximo desafio? Experimente trocar o retângulo por uma elipse, brincar com preenchimentos gradientes ou explorar como **adicionar sombra** a quadros de texto. Os mesmos princípios se aplicam, e a API da Aspose faz tudo parecer simples como um bolo.

Feliz codificação, e sinta‑se à vontade para deixar um comentário se encontrar algum obstáculo!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais, com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}