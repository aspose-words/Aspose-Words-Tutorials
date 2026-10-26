---
category: general
date: 2026-10-26
description: Aprenda a criar documentos Word programaticamente, adicionar uma forma
  e ocultar objetos no Word usando Aspose.Words for Java – guia passo a passo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- how to hide shape
- how to add shape
- hide object in word
language: pt
lastmod: 2026-10-26
og_description: Crie documento Word programaticamente, aprenda como adicionar forma
  e ocultar objeto no Word com Aspose.Words para Java. Exemplo completo e executável.
og_image_alt: Screenshot of a Word document created programmatically with a hidden
  ellipse shape
og_title: Criar documento Word programaticamente – adicionar e ocultar formas em Java
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn how to create Word document programmatically, add a shape, and
    hide object in Word using Aspose.Words for Java – step‑by‑step guide.
  headline: Create Word document programmatically and add a shape in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Criar documento Word programaticamente e adicionar uma forma em Java
url: /pt/java/images-shapes/create-word-document-programmatically-and-add-a-shape-in-jav/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar documento Word programaticamente e adicionar uma forma em Java

Se você precisa **criar documento Word programaticamente**, este tutorial mostra exatamente como fazer isso, adicionar uma forma e, em seguida, ocultar o objeto no Word. Seja você quem esteja construindo um gerador de relatórios ou um sistema automatizado de contratos, obterá uma solução completa, pronta‑para‑executar em apenas alguns minutos.

Você aprenderá a:

* Inicializar um documento Word com Aspose.Words for Java.  
* Inserir uma elipse (ou qualquer outra forma) usando a técnica **como adicionar forma**.  
* Ocultar essa forma para que nunca apareça quando o arquivo for aberto, respondendo à pergunta **como ocultar forma**.  

Nenhuma ferramenta externa é necessária além da biblioteca Aspose.Words, e o código funciona com Java 17 ou posterior.

## Pré‑requisitos

Antes de começar, certifique‑se de que você tem:

* Java Development Kit (JDK) 17 ou mais recente instalado.  
* Maven ou Gradle para gerenciar dependências (o exemplo usa Maven).  
* Uma licença válida do Aspose.Words for Java (a avaliação gratuita funciona para testes).  

Se você é novo no Aspose.Words, consulte o guia oficial Getting Started, mas não precisará lê‑lo para seguir este tutorial.

## Dependência Maven

Adicione a seguinte dependência ao seu `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest stable version -->
</dependency>
```

> **Dica:** Mantenha o número da versão atualizado; lançamentos mais recentes contêm correções de bugs para manipulação de formas.

## Etapa 1: Criar documento Word programaticamente – inicializando o documento

A primeira coisa que você faz ao **criar documento Word programaticamente** é instanciar um objeto `Document`. Esse objeto representa todo o arquivo .docx na memória.

```java
import com.aspose.words.*;

public class WordShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new empty document
        Document doc = new Document();

        // Create a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Por que esta etapa importa*: A classe `Document` é o ponto de entrada para todas as operações de processamento de Word. Sem ela, você não pode adicionar páginas, parágrafos ou formas.

## Etapa 2: Como adicionar forma – inserindo uma elipse

Agora abordamos a parte **como adicionar forma** do tutorial. Aspose.Words suporta muitos tipos de forma (Ellipse, Rectangle, TextBox, etc.). Abaixo inserimos uma elipse com largura e altura de 50 pontos.

```java
        // Insert an ellipse shape of size 50x50 points
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 50.0, 50.0);

        // Position the shape (optional)
        ellipse.setLeft(100);
        ellipse.setTop(100);
```

O método `insertShape` devolve um objeto `Shape` que você pode personalizar ainda mais — cor, estilo de linha, rotação e mais. As coordenadas são medidas em pontos (1/72 polegada).

*Por que você pode querer adicionar uma forma*: Formas são úteis para marcas d'água, elementos decorativos ou marcadores de posição que você posteriormente oculta ou substitui.

## Etapa 3: Como ocultar forma – tornando o objeto invisível no Word

Para responder à pergunta **como ocultar forma**, basta definir a propriedade `Hidden` da forma como `true`. Isso indica ao Word que a forma deve ser tratada como um objeto oculto, de modo que nunca seja renderizada na visualização ou impressão do documento.

```java
        // Hide the shape so it does not appear in the rendered document
        ellipse.setHidden(true);
```

Se precisar **ocultar objeto no Word** para um usuário ou condição específica, você pode alternar essa propriedade em tempo de execução com base na sua lógica de negócios.

> **Observação:** Formas ocultas ainda fazem parte da estrutura XML do documento. Elas podem ser reveladas posteriormente definindo `setHidden(false)`.

## Etapa 4: Salvar o documento

Depois de adicionar e ocultar a forma, grave o documento no disco.

```java
        // Save the document as a .docx file
        doc.save("HiddenShapeDemo.docx");
        System.out.println("Document created successfully.");
    }
}
```

Ao abrir `HiddenShapeDemo.docx` no Microsoft Word, você verá uma página em branco porque a elipse está oculta. O documento se comporta como qualquer arquivo Word normal.

## Exemplo completo em funcionamento

Juntando todas as peças, aqui está o programa completo e executável:

```java
import com.aspose.words.*;

public class WordShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a document programmatically
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: How to add shape – insert an ellipse (50x50 points)
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 50.0, 50.0);
        ellipse.setLeft(100);
        ellipse.setTop(100);

        // Step 3: How to hide shape – hide the ellipse so it never appears
        ellipse.setHidden(true);

        // Step 4: Save the file
        doc.save("HiddenShapeDemo.docx");
        System.out.println("Document created successfully.");
    }
}
```

**Saída esperada**

```
Document created successfully.
```

Abrir `HiddenShapeDemo.docx` mostra uma página vazia; a elipse oculta não é renderizada, confirmando que a operação **ocultar objeto no Word** foi bem‑sucedida.

## Casos de borda e variações

| Situação | O que mudar | Por quê |
|-----------|----------------|-----|
| Ocultar um retângulo em vez de uma elipse | Use `ShapeType.RECTANGLE` em `insertShape` | Marcador de posição visual diferente |
| Ocultar várias formas de uma vez | Percorra `doc.getChildNodes(NodeType.SHAPE, true)` e defina `setHidden(true)` | Útil para processamento em lote |
| Mostrar a forma apenas na visualização de impressão | Defina `shape.setVisible(false)` e `shape.setPrint(true)` | O Word distingue entre visibilidade na tela e na impressão |
| Usar outra unidade de medida | Chame `builder.getDocument().getCompatibilityOptions().setMeasureUnit(MeasureUnit.INCHES)` | Alinha-se aos requisitos de layout |

## Armadilhas comuns

* **Esquecer de chamar `setHidden(true)`** – a forma aparecerá normalmente.  
* **Salvar o documento antes de ocultar a forma** – a ordem importa; oculte primeiro, depois salve.  
* **Usar uma versão desatualizada do Aspose.Words** – versões antigas podem não ter a API `setHidden`.  

Sempre teste o arquivo gerado na versão alvo do Microsoft Word para garantir que o estado oculto se comporte como esperado.

## Conclusão

Neste guia você aprendeu como **criar documento Word programaticamente**, **adicionar forma** e **ocultar objeto no Word** usando Aspose.Words for Java. O exemplo completo demonstra os passos exatos, desde a inicialização do documento até a gravação de um arquivo onde a forma nunca aparece.  

A partir daqui você pode:

* Experimentar outros tipos de forma (`ShapeType.LINE`, `ShapeType.TEXT_BOX`).  
* Combinar formas ocultas com bookmarks para criar modelos dinâmicos.  
* Explorar as propriedades `setVisible` e `setPrint` para controle mais granular da visibilidade de objetos.

Boa codificação e aproveite a automação dos seus documentos Word!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [How to create blank word document with Aspose.Words for Java](/words/english/java/document-manipulation/how-to-create-blank-word-document-with-aspose-words-for-java/)
- [How to hide shape in a Word document using Java](/words/english/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}