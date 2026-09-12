---
category: general
date: 2026-09-11
description: Como editar gráfico em um documento Word com Java – aprenda a atualizar
  as configurações do gráfico, habilitar linhas de grade, alterar opções do gráfico
  e salvar o documento atualizado.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit chart
- update chart settings
- save updated document
- change chart options
- enable chart gridlines
language: pt
lastmod: 2026-09-11
og_description: Como editar gráfico em um documento Word com Java. Siga este guia
  para atualizar as configurações do gráfico, habilitar linhas de grade, alterar opções
  do gráfico e salvar o documento atualizado.
og_image_alt: Screenshot of a Word document showing a chart with gridlines enabled
og_title: Como editar gráfico em um documento Word usando Java – guia completo
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: How to edit chart in a Word document with Java – learn to update chart
    settings, enable chart gridlines, change chart options, and save the updated document.
  headline: How to edit chart in a Word document using Java
  type: TechArticle
- description: How to edit chart in a Word document with Java – learn to update chart
    settings, enable chart gridlines, change chart options, and save the updated document.
  name: How to edit chart in a Word document using Java
  steps:
  - name: Expected result
    text: 'When you open `output.docx`:'
  - name: What if the document has no chart?
    text: 'Attempting to cast a non‑chart shape will throw a `ClassCastException`.
      Guard against this by checking the shape type:'
  - name: How to edit a specific chart instead of the first one?
    text: 'Iterate through `shapes` and match a known title or an alternative identifier:'
  - name: Can I disable gridlines again later?
    text: 'Yes, simply set the property to `false`:'
  - name: Does this work with `.doc` (binary) files?
    text: Aspose.Words abstracts the file format, so the same code works for `.doc`
      and `.docx`. However, some newer chart features (like graduations) are only
      stored in the OOXML format, so you’ll see the effect only when saving as `.docx`.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart manipulation
title: Como editar um gráfico em um documento Word usando Java
url: /pt/java/using-document-elements/how-to-edit-chart-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como editar gráfico em um documento Word usando Java

Se você precisa **editar um gráfico** em um arquivo Word, este guia mostra os passos exatos. Você aprenderá a atualizar as configurações do gráfico, habilitar linhas de grade, alterar opções do gráfico e, finalmente, **salvar o documento atualizado** sem perder nenhuma formatação.

Trabalhar com gráficos programaticamente costuma parecer uma operação de caixa‑preta, especialmente quando você quer ajustar detalhes visuais como graduações ou linhas de grade. Este tutorial cobre tudo o que você precisa saber, desde o carregamento do documento até a persistência das alterações. Nenhuma ferramenta externa é necessária — apenas a biblioteca Aspose.Words for Java (versão 24.9 ou posterior).

Ao final deste artigo você será capaz de:

* Carregar um arquivo `.docx` que contém um gráfico.
* Localizar a forma do gráfico e modificar suas propriedades.
* Habilitar linhas de grade (graduações) e ajustar outras opções.
* **Salvar o documento atualizado** em um novo arquivo.

## Pré‑requisitos

* Java 17 ou posterior instalado na sua máquina.  
* Maven ou Gradle para gerenciar dependências.  
* Aspose.Words for Java 24.9+ (a versão que introduziu `setShowGraduations`).  
* Um documento Word (`input.docx`) que já contenha ao menos um gráfico.

Se você não está familiarizado com Aspose.Words, pense nele como uma API completa que permite ler, modificar e gravar documentos Word programaticamente — similar ao que você faria ao manipular um DOM em um navegador web.

## Etapa 1: Configurar o projeto e importar a biblioteca

Crie um novo projeto Maven ou adicione a dependência a um projeto existente:

```xml
<!-- pom.xml -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

> **Dica profissional:** Use a versão estável mais recente para garantir que você tenha o método `setShowGraduations`. Versões mais antigas não compilarão.

## Etapa 2: Carregar o documento Word que contém um gráfico

A primeira ação em qualquer fluxo **como editar gráfico** é carregar o arquivo fonte. Aspose.Words representa todo o documento com a classe `Document`.

```java
import com.aspose.words.*;

public class ChartEditor {
    public static void main(String[] args) throws Exception {
        // Replace with the actual path to your input file
        String inputPath = "YOUR_DIRECTORY/input.docx";

        // Load the document into memory
        Document doc = new Document(inputPath);
```

O objeto `Document` fornece acesso a cada nó dentro do arquivo, incluindo formas, tabelas e parágrafos.  

## Etapa 3: Localizar a primeira forma de gráfico no documento

Gráficos são armazenados como nós `Shape` cujo renderizador é um `Chart`. Para editar um gráfico você deve primeiro recuperar esse nó.

```java
        // Find all shape nodes (including charts)
        NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);

        // Assume the first shape is a chart; adjust the index if needed
        Shape chartShape = (Shape) shapes.get(0);

        // Cast the shape renderer to Chart
        Chart chart = (Chart) chartShape.getChart();
```

Se o documento contiver vários gráficos, itere sobre `shapes` e verifique `chartShape.getChart() != null` antes de fazer o cast. Isso evita `ClassCastException` e garante que você **altere opções do gráfico** apenas em objetos de gráfico válidos.

## Etapa 4: Habilitar linhas de grade do gráfico (graduações) – uma nova propriedade na versão 24.9

A propriedade `setShowGraduations` alterna a visibilidade das linhas de grade menores no eixo de valores. Habilitá‑las costuma melhorar a legibilidade para conjuntos de dados densos.

```java
        // Turn on gridlines (graduations) for the value axis
        chart.setShowGraduations(true);
```

> **Por que isso importa:** Linhas de grade dão ao observador uma referência visual para cada ponto de dados, facilitando a identificação de tendências. O padrão é `false`, portanto você deve habilitá‑las explicitamente quando necessário.

Você também pode personalizar outros aspectos, como as linhas de grade principais, títulos dos eixos ou a posição da legenda. Abaixo está um exemplo de alteração do título do gráfico e da posição da legenda — ambos fazem parte de **alterar opções do gráfico**.

```java
        // Change the chart title
        chart.getTitle().setText("Sales Overview 2026");
        chart.getTitle().setOverlay(false);

        // Move the legend to the bottom
        chart.getLegend().setPosition(LegendPosition.BOTTOM);
```

## Etapa 5: Salvar o documento com as configurações de gráfico atualizadas

Depois de modificar o gráfico, persista as alterações. Esta etapa completa a fase de **salvar documento atualizado**.

```java
        // Replace with the desired output path
        String outputPath = "YOUR_DIRECTORY/output.docx";

        // Save the modified document
        doc.save(outputPath);
        System.out.println("Chart edited and document saved to: " + outputPath);
    }
}
```

Executar o programa gerará `output.docx` onde o gráfico agora exibe linhas de grade, um novo título e uma legenda reposicionada. Abra o arquivo no Microsoft Word para verificar as alterações visuais.

## Código‑fonte completo (executável)

```java
import com.aspose.words.*;

public class ChartEditor {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the Word document that contains a chart
        String inputPath = "YOUR_DIRECTORY/input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Locate the first chart shape in the document
        NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);
        Shape chartShape = (Shape) shapes.get(0);
        Chart chart = (Chart) chartShape.getChart();

        // 3️⃣ Enable chart gridlines (graduations)
        chart.setShowGraduations(true);

        // 4️⃣ Change chart options (title and legend)
        chart.getTitle().setText("Sales Overview 2026");
        chart.getTitle().setOverlay(false);
        chart.getLegend().setPosition(LegendPosition.BOTTOM);

        // 5️⃣ Save the document with the updated chart settings
        String outputPath = "YOUR_DIRECTORY/output.docx";
        doc.save(outputPath);

        System.out.println("Chart edited and document saved to: " + outputPath);
    }
}
```

### Resultado esperado

Ao abrir `output.docx`:

* O gráfico exibe linhas de grade menores no eixo de valores.  
* O título mostra **“Sales Overview 2026”**.  
* A legenda aparece na parte inferior do gráfico.

Se o gráfico original já possuía linhas de grade, a aparência visual permanece inalterada, confirmando que o código é **idempotente**.

## Perguntas comuns e tratamento de casos‑limite

### E se o documento não contiver gráfico?

Tentar fazer cast de uma forma que não seja de gráfico lançará uma `ClassCastException`. Proteja‑se verificando o tipo da forma:

```java
if (chartShape.getShapeType() == ShapeType.CHART) {
    Chart chart = (Chart) chartShape.getChart();
    // proceed with modifications
}
```

### Como editar um gráfico específico em vez do primeiro?

Itere através de `shapes` e compare com um título conhecido ou outro identificador alternativo:

```java
for (Node node : shapes) {
    Shape shape = (Shape) node;
    if (shape.getShapeType() == ShapeType.CHART) {
        Chart c = (Chart) shape.getChart();
        if ("Revenue Q1".equals(c.getTitle().getText())) {
            // modify this chart
        }
    }
}
```

### Posso desabilitar as linhas de grade novamente mais tarde?

Sim, basta definir a propriedade como `false`:

```java
chart.setShowGraduations(false);
```

### Isso funciona com arquivos `.doc` (binários)?

Aspose.Words abstrai o formato do arquivo, portanto o mesmo código funciona para `.doc` e `.docx`. Contudo, alguns recursos mais recentes de gráfico (como graduações) são armazenados apenas no formato OOXML, então você verá o efeito somente ao salvar como `.docx`.

## Dicas para código pronto para produção

* **Validar caminhos de entrada** – use `Files.exists(Paths.get(inputPath))` antes de carregar.  
* **Envolver chamadas de API** em blocos try‑catch para expor detalhes de `Exception`, especialmente ao lidar com documentos corrompidos.  
* **Liberar recursos** – embora Aspose.Words gerencie a memória, chamar `doc.close()` (ou usar try‑with‑resources, se disponível) pode liberar manipuladores nativos mais cedo.  
* **Verificar versão** – assegure que a versão da biblioteca em tempo de execução seja ≥ 24.9 antes de chamar `setShowGraduations`. Você pode consultar `License.getVersion()` se precisar de uma verificação programática.

## Conclusão

Agora você sabe **como editar gráficos** em um documento Word usando Java. O processo — carregar o documento, localizar o gráfico, habilitar linhas de grade, alterar opções do gráfico e **salvar o documento atualizado** — cobre os cenários mais comuns de manipulação programática de gráficos.  

A partir daqui, você pode explorar personalizações adicionais, como mudar cores das séries de dados, aplicar estilos ao gráfico ou exportar o gráfico como imagem. Cada uma dessas tarefas segue o mesmo padrão: obter a instância `Chart`, ajustar suas propriedades e **salvar o documento atualizado**.

Boa codificação, e sinta‑se à vontade para experimentar outras configurações de gráfico que atendam às suas necessidades de relatório!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas em seus próprios projetos.

- [Como criar gráfico de colunas usando Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Como salvar documento como PDF com Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Definir opções padrão para rótulos de dados em um gráfico](/words/english/net/programming-with-charts/default-options-for-data-labels/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}