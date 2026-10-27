---
category: general
date: 2026-07-16
description: Crie um gráfico de pizza em Java usando Aspose.Words. Aprenda como adicionar
  linhas de ligação, exibir a legenda do gráfico e destacar uma fatia em um único
  tutorial.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- add leader lines
- show chart legend
- how to explode slice
- how to add legend
language: pt
lastmod: 2026-07-16
og_description: Crie um gráfico de pizza em Java usando Aspose.Words. Este guia mostra
  como adicionar linhas de ligação, exibir a legenda do gráfico e destacar uma fatia,
  proporcionando uma visualização refinada em minutos.
og_image_alt: Screenshot of a Java‑generated pie chart with an exploded slice and
  visible legend
og_title: Criar Gráfico de Pizza com Aspose.Words Java – Tutorial Completo de Formatação
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: Create pie chart in Java using Aspose.Words. Learn how to add leader
    lines, show chart legend, and explode a slice in a single tutorial.
  headline: Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide
  type: TechArticle
- description: Create pie chart in Java using Aspose.Words. Learn how to add leader
    lines, show chart legend, and explode a slice in a single tutorial.
  name: Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide
  steps:
  - name: Java 17 (or later) installed.
    text: Java 17 (or later) installed.
  - name: Aspose.Words for Java JAR on your classpath.
    text: Aspose.Words for Java JAR on your classpath.
  - name: A basic IDE or text editor—IntelliJ IDEA, Eclipse, VS Code, whatever you
      prefer.
    text: A basic IDE or text editor—IntelliJ IDEA, Eclipse, VS Code, whatever you
      prefer.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart Formatting
- Data Visualization
title: Criar Gráfico de Pizza com Aspose.Words Java – Guia Completo Passo a Passo
url: /pt/java/using-document-elements/create-pie-chart-with-aspose-words-java-full-step-by-step-gu/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar Gráfico de Pizza com Aspose.Words Java – Guia Completo Passo a Passo

Já se perguntou como **criar um gráfico de pizza** programaticamente em Java sem lutar com APIs de desenho de baixo nível? Você não está sozinho. Muitos desenvolvedores precisam de uma visualização rápida para relatórios, painéis ou documentos automatizados, e recorrem ao Aspose.Words porque ele cuida do trabalho pesado.  

Neste tutorial vamos percorrer um exemplo completo, pronto‑para‑executar, que não só **cria um gráfico de pizza** como também mostra como **adicionar linhas de ligação**, **exibir a legenda do gráfico** e até **explodir uma fatia** para ênfase. Ao final você terá um arquivo `.docx` com aparência tão polida que impressionará o cliente.

> **Quick win:** O trecho de código abaixo funciona imediatamente com Aspose.Words for Java 23.9 (ou qualquer versão mais recente). Sem dependências extras, apenas o JAR.

## O que você aprenderá

- Configurar um documento Word em branco com `DocumentBuilder`.
- Inserir um **gráfico de pizza** de tamanho personalizado.
- Usar o recurso **explodir fatia** para destacar um ponto de dados.
- Habilitar **linhas de ligação** para que a fatia explodida permaneça conectada ao rótulo.
- Ativar a **legenda do gráfico** para que os leitores identifiquem instantaneamente cada fatia.
- Salvar o resultado em um arquivo `.docx` que você pode abrir no Microsoft Word ou LibreOffice.

**Pré‑requisitos** – Você precisará:

1. Java 17 (ou superior) instalado.
2. JAR do Aspose.Words for Java no seu classpath.
3. Um IDE ou editor de texto básico—IntelliJ IDEA, Eclipse, VS Code, o que preferir.

Agora, vamos mergulhar.

## Etapa 1: Inicializar o Documento e o Builder – Preparando para **criar gráfico de pizza**

Primeiro, precisamos de uma tela limpa para o documento. `Document` representa todo o arquivo Word, enquanto `DocumentBuilder` é o auxiliar que nos permite adicionar conteúdo.

```java
import com.aspose.words.*;

public class PieChartFormattingDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();               // the container for our Word file
        DocumentBuilder builder = new DocumentBuilder(doc); // convenient API for adding elements
```

> **Por que isso importa:** Começar com um `Document` novo garante que não haja estilos ocultos ou objetos residuais que possam interferir na renderização do gráfico.

## Etapa 2: Inserir o **gráfico de pizza** – O tamanho importa

Aspose.Words torna a inserção de gráficos uma única linha de código. Aqui solicitamos um gráfico de pizza de 400 × 300 pontos—aproximadamente 5,5 × 4,2 polegadas em uma tela típica.

```java
        // Step 2: Insert a pie chart of size 400x300 points
        Shape chartShape = builder.insertChart(ChartType.PIE, 400, 300);
        Chart chart = chartShape.getChart(); // the underlying chart object we will format
```

> **Pro tip:** Se precisar de um tamanho diferente, basta alterar os dois argumentos numéricos. A API trabalha em pontos, onde 72 pontos = 1 polegada.

## Etapa 3: **Como explodir uma fatia** – Enfatizando um ponto de dados chave

Explodir uma fatia a retira do restante da pizza, atraindo o olhar do leitor. O método `setExplosion` recebe um inteiro que representa a distância em pontos.

```java
        // Step 3: Explode the first slice to emphasize it
        chart.getSeries().get(0).setExplosion(10); // 10 points outward
```

> **E se você tiver várias séries?** Você pode chamar `setExplosion` em qualquer índice de série (`get(1)`, `get(2)`, …) para explodir fatias diferentes.

## Etapa 4: **Adicionar linhas de ligação** e **exibir legenda do gráfico** – Conectando os pontos

Quando uma fatia é explodida, o rótulo pode se afastar. As linhas de ligação mantêm o rótulo preso, preservando a legibilidade. Ao mesmo tempo, uma legenda oferece uma chave rápida para todas as fatias.

```java
        // Step 4: Enable leader lines for the exploded slice and show the legend
        chart.getSeries().get(0).setLeaderLines(true); // draws a line from slice to its label
        chart.setShowLegend(true);                     // makes the legend visible below the chart
```

> **Por que habilitar linhas de ligação?** Sem elas, o rótulo pode parecer flutuante, confundindo os usuários sobre a qual fatia ele pertence.  
> **Precisa de uma posição de legenda personalizada?** Use `chart.getLegend().setPosition(LegendPosition.TOP)` ou qualquer outro valor de enumeração.

## Etapa 5: Salvar o Documento – A etapa final de **criar gráfico de pizza**

Finalmente, persistimos o documento no disco. Ajuste o caminho para uma pasta onde você tenha permissão de gravação.

```java
        // Step 5: Save the document with the formatted pie chart
        doc.save("YOUR_DIRECTORY/PieChartDemo.docx");
    }
}
```

Execute o programa, abra o `PieChartDemo.docx` gerado, e você deverá ver um gráfico de pizza bem formatado com a primeira fatia explodida, linhas de ligação e uma legenda visível.

![Exemplo de gráfico de pizza mostrando fatia explodida e legenda](pie-chart-example.png){: .center-image alt="Exemplo de criação de gráfico de pizza com fatia explodida, linhas de ligação e legenda"}

### Saída Esperada

Ao abrir o arquivo Word, o gráfico se parece aproximadamente com isto:

- Um gráfico de pizza de 400 × 300 pt.
- A primeira fatia está deslocada em 10 pt.
- Uma linha de ligação fina conecta a fatia explodida ao seu rótulo.
- Uma legenda abaixo do gráfico lista o nome de cada série.

Se você não vir a linha de ligação, verifique novamente se `setLeaderLines(true)` é chamado *depois* da configuração de explosão—a ordem importa.

## Armadilhas Comuns e Como Evitá‑las

| Problema | Por que acontece | Solução |
|----------|------------------|---------|
| **Nenhuma legenda aparece** | `setShowLegend(true)` foi omitido ou chamado no objeto de gráfico errado. | Certifique‑se de chamar `chart.setShowLegend(true)` **depois** de obter o `Chart` a partir da forma. |
| **Linha de ligação ausente** | A fatia não foi explodida, ou o tipo de gráfico não suporta linhas de ligação. | Apenas `ChartType.PIE` (ou `PIE_3D`) suporta linhas de ligação. Chame `setExplosion` primeiro, depois `setLeaderLines(true)`. |
| **A fatia não se move** | Valor de explosão muito baixo (0‑2 pt). | Aumente o inteiro, por exemplo, `setExplosion(10)` ou maior para um efeito mais dramático. |
| **Gráfico parece distorcido** | Usar um tamanho não quadrado (largura ≠ altura) pode achatar a pizza. | Mantenha largura e altura iguais ou próximas; 400 × 300 funciona, mas 400 × 400 dá um círculo perfeito. |

## Ajustes Avançados (Opcional)

Se quiser ir além do básico, considere:

- **Cores personalizadas**: `chart.getSeries().get(0).getDataPoints().get(i).getFormat().getFill().setForeColor(Color.RED);`
- **Rótulos de dados**: `chart.getSeries().get(0).setDataLabelType(ChartDataLabelType.CATEGORY);`
- **Efeito 3‑D**: Substitua `ChartType.PIE` por `ChartType.PIE_3D`.

Essas opções permitem ajustar finamente o visual para combinar com as diretrizes de identidade visual da empresa.

## Recapitulação – O que Conquistamos

Começamos com um documento Word em branco, **criamos um gráfico de pizza**, **explodimos a primeira fatia**, **adicionamos linhas de ligação** e **exibimos a legenda do gráfico**. Todo o fluxo cabe em um método `main` conciso, facilitando a incorporação em pipelines de relatórios maiores.

## Próximos Passos

- **Adicionar mais séries**: Preencha o gráfico com dados reais de um banco de dados ou CSV.
- **Exportar para PDF**: Use `doc.save("output.pdf", SaveFormat.PDF);` para gerar uma versão PDF.
- **Combinar com outras formas**: Insira tabelas, imagens ou gráficos adicionais para um relatório completo.

Se você estiver curioso sobre outros tipos de gráficos—coluna, barra, linha—basta substituir `ChartType.PIE` pelo enum apropriado e seguir os mesmos passos de formatação.

---

*Feliz criação de gráficos!* Sinta‑se à vontade para deixar um comentário se algo não funcionou como esperado, ou compartilhe como você personalizou a posição da legenda. Seu feedback ajuda a todos a construir documentos automatizados melhores.

## O que Você Deve Aprender a Seguir?

Os tutoriais a seguir cobrem tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Como criar gráfico de colunas usando Aspose.Words para Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Como Criar Documentos PDF com Aspose.Words para Java | Document Processing API](/words/english/java/)
- [Como Adicionar Marca d'Água a Documentos Usando Aspose.Words para Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}