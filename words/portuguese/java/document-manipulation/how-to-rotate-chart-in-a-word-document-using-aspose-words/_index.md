---
category: general
date: 2026-10-10
description: Aprenda como girar o gráfico em um arquivo Word e modificar o gráfico
  no Word para alterar o tamanho do gráfico de rosca com um exemplo completo em Java.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to rotate chart
- modify chart in word
- change doughnut chart size
- Aspose.Words chart manipulation
- Java chart API
language: pt
lastmod: 2026-10-10
og_description: Como girar o gráfico em um arquivo Word e modificar o gráfico no Word
  para alterar o tamanho do gráfico de rosca usando Aspose.Words for Java.
og_image_alt: Screenshot showing a rotated doughnut chart after applying how to rotate
  chart steps
og_title: Como girar um gráfico em um documento Word – guia Java passo a passo
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Learn how to rotate chart in a Word file and modify chart in Word to
    change doughnut chart size with a complete Java example.
  headline: How to rotate chart in a Word document using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Como girar um gráfico em um documento Word usando Aspose.Words
url: /pt/java/document-manipulation/how-to-rotate-chart-in-a-word-document-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como girar um gráfico em um documento Word usando Aspose.Words

Se você precisa **girar um gráfico** dentro de um arquivo Microsoft Word, este guia mostra os passos exatos. Você também aprenderá como **modificar gráfico no Word** para **alterar o tamanho do gráfico de rosca** sem sair do seu código Java.

A automação do Word costuma parecer uma série de chamadas de API desconexas, mas com Aspose.Words você pode tratar um gráfico como qualquer outro nó do documento. Ao final deste tutorial você terá um programa executável que carrega um `.docx` existente, gira um gráfico de rosca em 45°, reduz o buraco para 50 % do raio e salva o resultado como um novo arquivo.

## Pré-requisitos

Antes de começar, certifique‑se de que você tem:

* Java 17 ou superior instalado.
* Maven (ou Gradle) para gerenciar dependências.
* Um documento Word de entrada (`input.docx`) que já contenha um gráfico de rosca.
* Uma licença válida do Aspose.Words for Java (ou use o modo de avaliação).

## Etapa 1: Configurar o projeto Maven

Crie um novo projeto Maven ou adicione a dependência a seguir ao seu `pom.xml` existente:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest version available -->
</dependency>
```

Executar `mvn clean install` baixará a biblioteca e tornará as classes disponíveis no seu classpath.

## Etapa 2: Carregar o documento Word que contém um gráfico

A primeira operação é abrir o documento existente. A classe `Document` representa o arquivo inteiro.

```java
import com.aspose.words.*;

public class RotateDoughnutChart {
    public static void main(String[] args) throws Exception {
        // Load a document that already contains a chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

Carregar o arquivo **não** o modifica; ele simplesmente cria uma representação em memória que você pode consultar e editar.

## Etapa 3: Criar um DocumentBuilder para navegação

`DocumentBuilder` fornece uma API tipo cursor para percorrer a árvore do documento. Usaremos ele para localizar a primeira forma de gráfico.

```java
        // Create a DocumentBuilder for the loaded document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

O builder inicia no começo do documento, mas você pode movê‑lo para qualquer nó posteriormente, se necessário.

## Etapa 4: Recuperar a primeira forma de gráfico

Gráficos são armazenados como nós `Shape`. Ao filtrar nós filhos do tipo `NodeType.SHAPE` podemos extrair o objeto de gráfico.

```java
        // Retrieve the first chart shape from the document
        Shape chartShape = (Shape) builder.getCurrentParagraph()
                .getChildNodes(NodeType.SHAPE, true)
                .get(0);

        // Cast the shape's renderer to a Chart object
        Chart chart = chartShape.getChart();
```

Se o documento contiver vários gráficos, você pode iterar sobre `getChildNodes` e verificar cada `Shape` com `hasChart()` antes de fazer o cast.

## Etapa 5: Girar o gráfico (como girar gráfico)

Um gráfico de rosca é essencialmente um gráfico de pizza com um buraco. Girá‑lo altera o ângulo inicial da primeira fatia.

```java
        // Rotate the chart by setting its start angle to 45 degrees
        chart.setStartAngle(45.0);
```

O método `setStartAngle` espera um `double` representando graus. Valores positivos giram no sentido horário, enquanto valores negativos giram no sentido anti‑horário.

## Etapa 6: Alterar o tamanho do buraco da rosca (alterar tamanho do gráfico de rosca)

O tamanho do buraco é expresso como fração do raio do gráfico. Um valor de `0.5` significa que o buraco ocupa 50 % do raio total.

```java
        // Adjust the doughnut hole size to 50 %
        chart.setDoughnutHoleSize(0.5);
```

**Dica:** O intervalo válido vai de `0.0` (sem buraco, ou seja, uma pizza normal) até `0.9` (anel muito fino). Valores fora desse intervalo lançarão uma `IllegalArgumentException`.

## Etapa 7: Salvar o documento modificado

Por fim, grave as alterações no disco.

```java
        // Save the modified document
        doc.save("YOUR_DIRECTORY/DoughnutFormatted.docx");
    }
}
```

Ao abrir `DoughnutFormatted.docx` no Microsoft Word, você verá o gráfico de rosca girado 45° e o buraco reduzido à metade do tamanho original.

## Exemplo completo e executável

Juntando todas as partes, aqui está o programa completo que você pode copiar‑colar no seu IDE:

```java
import com.aspose.words.*;

public class RotateDoughnutChart {
    public static void main(String[] args) throws Exception {
        // Load a document that already contains a chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Create a DocumentBuilder for the loaded document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Retrieve the first chart shape from the document
        Shape chartShape = (Shape) builder.getCurrentParagraph()
                .getChildNodes(NodeType.SHAPE, true)
                .get(0);

        // Ensure the shape actually contains a chart
        if (!chartShape.hasChart()) {
            System.out.println("No chart found in the first shape.");
            return;
        }

        // Cast the shape's renderer to a Chart object
        Chart chart = chartShape.getChart();

        // Rotate the chart by setting its start angle to 45 degrees
        chart.setStartAngle(45.0);

        // Adjust the doughnut hole size to 50 %
        chart.setDoughnutHoleSize(0.5);

        // Save the modified document
        doc.save("YOUR_DIRECTORY/DoughnutFormatted.docx");

        System.out.println("Chart rotated and doughnut size changed successfully.");
    }
}
```

### Saída esperada

Executar o programa imprime:

```
Chart rotated and doughnut size changed successfully.
```

Abrir `DoughnutFormatted.docx` mostra um gráfico de rosca cuja primeira fatia começa na posição 45° e cujo raio interno ocupa metade do raio externo.

## Variações comuns e casos de borda

| Situação | O que ajustar | Por que importa |
|-----------|----------------|----------------|
| **Múltiplos gráficos** | Percorra `getChildNodes(NodeType.SHAPE, true)` e verifique `shape.hasChart()` para cada um | Garante que você modifique o gráfico desejado em vez do primeiro |
| **Gráfico de barras ou linhas** | `setStartAngle` não se aplica; use `chart.getSeries().get(0).setFillFormat(...)` para outras alterações visuais | Nem todos os tipos de gráfico suportam rotação; apenas gráficos de rosca/pizza têm ângulo inicial |
| **Gráfico sem buraco de rosca** | Pule `setDoughnutHoleSize` ou converta primeiro o tipo de gráfico para rosca via `chart.setChartType(ChartType.DONUT)` | Alterar o tamanho do buraco em um gráfico que não é rosca gera exceção |
| **Documentos grandes** | Use `DocumentBuilder.moveToDocumentStart()` e `builder.moveToNode(chartShape)` para navegação direcionada | Melhora o desempenho ao evitar percorrer nós não relacionados |

## Dicas avançadas para manipulação confiável de gráficos

* **Cache a referência do gráfico** – Se você pretende modificar várias propriedades, mantenha uma variável local `Chart` ao invés de chamar repetidamente `chartShape.getChart()`.
* **Valide os valores de entrada** – Antes de chamar `setStartAngle` ou `setDoughnutHoleSize`, verifique se estão dentro do intervalo permitido para evitar erros em tempo de execução.
* **Use uma licença** – O modo de avaliação insere uma marca d'água na primeira página. Aplicar uma licença (`License license = new License(); license.setLicense("Aspose.Words.lic");`) a remove.

## Próximos passos

Agora que você sabe **como girar gráfico** e **alterar o tamanho do gráfico de rosca**, pode explorar outros cenários de **modificar gráfico no Word**:

* Alterar cores das fatias com `chart.getSeries().get(0).getDataPoints().get(i).getFillFormat().setForeColor(Color.getRed())`.
* Adicionar rótulos de dados chamando `chart.getSeries().get(0).setHasDataLabel(true)`.
* Exportar o gráfico como imagem usando `chart.toImage(300, 300, ImageType.PNG)`.

Cada uma dessas extensões segue o mesmo padrão: obter o objeto `Chart`, chamar o setter apropriado e salvar o documento.

---

**Você acabou de dominar a rotação e o redimensionamento de gráficos de rosca no Word usando Java.** Sinta‑se à vontade para adaptar o código a outros tipos de gráfico, integrá‑lo a um pipeline maior de geração de documentos ou combiná‑lo com Aspose.Slides para automação de PowerPoint. Boa codificação!


## O que você deve aprender a seguir?


Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Hide Chart Axis In A Word Document](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Insert Bubble Chart In Word Document](/words/english/net/programming-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}