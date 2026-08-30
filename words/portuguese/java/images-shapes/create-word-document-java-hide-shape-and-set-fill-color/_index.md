---
category: general
date: 2026-08-07
description: 'Criar documento Word em Java com Aspose.Words: inserir uma elipse, definir
  a cor de preenchimento da forma e ocultar a forma no Word usando um exemplo conciso.'
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document java
- how to hide shape
- how to insert shape
- hide shape in word
- set shape fill color
language: pt
lastmod: 2026-08-07
og_description: Crie um documento Word em Java com Aspose.Words. Aprenda a inserir
  uma forma, definir sua cor de preenchimento e ocultar a forma no Word — tudo em
  um único exemplo executável.
og_image_alt: Screenshot showing a hidden ellipse shape in a Word document created
  with Java
og_title: Criar documento Word em Java – ocultar forma e definir cor de preenchimento
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: 'Create word document java with Aspose.Words: insert an ellipse, set
    shape fill color, and hide shape in Word using a concise example.'
  headline: Create word document java – hide shape and set fill color
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
- Shape handling
title: Criar documento Word em Java – ocultar forma e definir cor de preenchimento
url: /pt/java/images-shapes/create-word-document-java-hide-shape-and-set-fill-color/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar documento Word java – ocultar forma e definir cor de preenchimento

Se você precisar **create word document java** com manipulação programática de formas, este tutorial mostra como. Você aprenderá a inserir uma forma, definir sua cor de preenchimento e ocultar a forma no Word usando Aspose.Words for Java.

O guia cobre cada passo, desde a inicialização de um objeto `Document` até a verificação de que a forma está invisível quando o arquivo é aberto. Nenhum recurso externo é necessário além da biblioteca Aspose.Words, e o código‑fonte completo é fornecido para que você possa executá‑lo imediatamente.

**Pré-requisitos**

- Java 8 ou mais recente
- Maven ou Gradle para gerenciar dependências (ou o JAR Aspose.Words no classpath)
- Familiaridade básica com a sintaxe Java
- Uma IDE ou editor de texto para desenvolvimento Java

O tutorial também explica **how to hide shape** em um arquivo Word, **how to insert shape** com dimensões precisas e **set shape fill color** para estilização visual.

---

![Criar documento Word java – visualização da forma oculta](image-placeholder.png){.align-center width=600 alt="Criar documento Word java – visualização da forma oculta"}

## Criar documento Word java – inicializar documento e builder

O primeiro passo é criar um documento Word em branco e um `DocumentBuilder` que permite adicionar conteúdo. Inicializar esses objetos aloca as estruturas internas que o Aspose.Words precisa para rastrear páginas, parágrafos e formas.

```java
import com.aspose.words.*;

public class ShapeVisibilityDemo {
    public static void main(String[] args) throws Exception {
        // Create an empty document
        Document doc = new Document();

        // DocumentBuilder provides methods to insert elements
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Por que isso importa:* Sem um `DocumentBuilder` você não pode inserir formas, texto ou outros objetos. O builder trabalha contra a instância `Document` na memória, garantindo que todas as alterações sejam capturadas antes de salvar.

## Como inserir forma com Aspose.Words

Aspose.Words suporta muitas formas geométricas. Aqui inserimos uma elipse com largura de 150 pt e altura de 100 pt. O método `insertShape` retorna um objeto `Shape` que você pode configurar ainda mais.

```java
        // Insert an ellipse shape (width: 150pt, height: 100pt)
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 150, 100);
```

*Por que isso importa:* Usar `insertShape` garante que a forma seja ancorada corretamente dentro do fluxo do documento. O `Shape` retornado permite modificar propriedades como cor de preenchimento, estilo de linha e visibilidade.

## Definir cor de preenchimento da forma no Word

Uma forma sem preenchimento parece transparente. Definir uma cor de preenchimento faz a forma se destacar quando está visível. O exemplo usa `java.awt.Color.GREEN` para demonstrar **set shape fill color**.

```java
        // Apply a green fill to the ellipse
        ellipse.setFillColor(java.awt.Color.GREEN);
```

*Por que isso importa:* A cor de preenchimento é armazenada na definição XML da forma. Alterá‑la em tempo de execução permite gerar documentos com cores específicas da marca ou destacar regiões importantes.

## Como ocultar forma no Word

Às vezes você precisa de uma forma que controla o layout ou atua como placeholder, mas não deve aparecer para o usuário final. A chamada `setHidden(true)` implementa **how to hide shape** e satisfaz o requisito de **hide shape in word**.

```java
        // Hide the shape so it will not be visible when the document is opened
        ellipse.setHidden(true);
```

*Por que isso importa:* Formas ocultas ainda fazem parte do modelo de objetos do documento, o que significa que podem ser referenciadas posteriormente (por exemplo, para marcadores ou manipulação programática) sem desordenar o layout visual.

## Salvar o documento e verificar resultados

Depois de configurar a forma, salve o arquivo no disco. O `.docx` salvo pode ser aberto no Microsoft Word; a elipse ficará invisível, mas sua presença pode ser confirmada ao inspecionar o XML do documento ou usando Aspose.Words para enumerar formas.

```java
        // Save the document to the desired location
        doc.save("YOUR_DIRECTORY/ShapeVisibilityDemo.docx");
    }
}
```

*Resultado esperado:* Ao abrir `ShapeVisibilityDemo.docx` mostra uma página normal sem gráficos visíveis. Se você inspecionar o documento com um visualizador ZIP e abrir `word/document.xml`, encontrará um elemento `<w:shape>` com `hidden="true"` e um `<v:fillcolor>` de `#00FF00`.

---

## Variações comuns e casos de borda

- **Tipos diferentes de forma:** Substitua `ShapeType.ELLIPSE` por `ShapeType.RECTANGLE`, `ShapeType.CLOUD` ou qualquer outro valor de enum suportado para obter a geometria desejada.
- **Visibilidade condicional:** Você pode alternar `ellipse.setHidden(false)` com base em lógica de tempo de execução, permitindo geração dinâmica de documentos.
- **Preenchimentos complexos:** Em vez de uma cor sólida, use `ellipse.getFill().setTextureImage(...)` para preenchimentos de padrão. O mesmo método `setHidden` ainda controla a visibilidade.
- **Múltiplas formas:** Crie um array ou lista de objetos `Shape`, configure cada um independentemente e oculte apenas aqueles que atendem a critérios específicos.

*Dica profissional:* Ao gerar documentos grandes, reutilize uma única instância de `DocumentBuilder` em vez de criar uma nova para cada forma. Isso reduz o consumo de memória e melhora o desempenho.

---

## Conclusão

Agora você sabe como **create word document java** que insere uma elipse, **set shape fill color** e **hide shape in word** usando Aspose.Words. O exemplo completo e executável demonstra cada chamada de API, explica por que cada passo é necessário e mostra o resultado esperado.

Em seguida, explore tópicos relacionados, como **how to insert shape** com quebra de texto, adicionar hiperlinks às formas e exportar o documento para PDF preservando elementos ocultos. Experimente diferentes cores, tamanhos e bandeiras de visibilidade para adaptar a automação do Word às necessidades do seu projeto.

Pronto para automatizar mais recursos do Word? Confira a documentação do Aspose.Words for Java sobre [working with shapes](https://docs.aspose.com/words/java/working-with-shapes/) e comece a criar documentos mais ricos, gerados programaticamente, hoje.

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Criar documento Word Java – adicionar forma retangular com efeito de sombra](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Tutorial de sombra de forma Aspose.Words – adicionar sombra a forma Word em C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Criar forma de grupo em documento Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}