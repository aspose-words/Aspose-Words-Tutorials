---
category: general
date: 2026-10-26
description: Crie um gráfico de rosca e insira um gráfico de pizza em Java com código
  passo a passo. Aprenda todo o fluxo de trabalho para visualizações de gráficos flexíveis.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create doughnut chart
- insert pie chart
- Java chart library
- chart customization Java
- data visualization Java
language: pt
lastmod: 2026-10-26
og_description: Crie um gráfico de rosca em Java com este guia que também mostra como
  inserir um gráfico de pizza para visualizações flexíveis.
og_image_alt: Java code snippet creating a doughnut chart and inserting a pie chart
og_title: Criar gráfico de rosca e inserir gráfico de pizza – Guia Java
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Create doughnut chart and insert pie chart in Java with step‑by‑step
    code. Learn the full workflow for flexible chart visualizations.
  headline: How to create a doughnut chart and insert a pie chart
  type: TechArticle
tags:
- chart
- Java
- data‑visualization
title: Como criar um gráfico de rosca e inserir um gráfico de pizza
url: /pt/java/images-shapes/how-to-create-a-doughnut-chart-and-insert-a-pie-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como criar um gráfico de rosca e inserir um gráfico de pizza

Se você precisa **criar um gráfico de rosca** em Java, este tutorial o guiará passo a passo. Também mostraremos como **inserir um gráfico de pizza** usando a mesma API de builder, para que você possa alternar entre estilos visuais sem esforço. Ao final do guia, você terá um programa completo e executável que produz ambos os tipos de gráfico e demonstra personalizações comuns.

O tutorial cobre:

* Inicialização do builder de gráficos fornecido pela biblioteca escolhida.  
* Criação de um gráfico de rosca e configuração do tamanho do buraco.  
* Inserção de um gráfico de pizza e explosão de uma fatia para ênfase.  
* Dicas para lidar com casos de borda, como séries ausentes ou tipos de gráfico não suportados.

Você só precisa de um JDK recente (8 ou superior) e do JAR da biblioteca de gráficos no seu classpath. Nenhum serviço externo é necessário.

---

## Pré-requisitos

| Item | Motivo |
|------|--------|
| Java Development Kit (JDK) 8+ | Necessário para compilar e executar o exemplo. |
| Biblioteca de gráficos (ex.: **Aspose.Cells for Java** ou **JFreeChart**) | Fornece `ChartBuilder`, `ChartType` e métodos de manipulação de séries usados no código. |
| Uma IDE ou um editor de texto | Para escrever e executar o arquivo fonte Java. |

Certifique‑se de que o JAR da biblioteca esteja adicionado ao caminho de compilação do seu projeto. Se usar Maven, adicione a dependência apropriada; caso contrário, coloque o JAR na pasta `libs` e faça referência a ele durante a compilação.

---

## Etapa 1: Configurar o builder de gráficos

O primeiro passo é criar uma instância de `ChartBuilder` (ou equivalente) que gerará os objetos de gráfico. Esse objeto atua como uma fábrica e contém a planilha ou canvas onde o gráfico será colocado.

```java
import com.aspose.cells.*;

public class DoughnutAndPieDemo {
    public static void main(String[] args) throws Exception {
        // Create a new workbook to host the charts
        Workbook workbook = new Workbook();
        Worksheet sheet = workbook.getWorksheets().get(0);

        // Initialize the chart builder with the worksheet
        ChartBuilder builder = new ChartBuilder(sheet);
```

**Por que isso importa:**  
O builder vincula o gráfico a uma planilha específica, garantindo que todos os objetos de gráfico subsequentes compartilhem a mesma superfície de desenho. Pular esta etapa deixaria você sem um local de destino para os elementos visuais.

---

## Etapa 2: **Criar gráfico de rosca**

Agora geramos um gráfico de rosca com um tamanho definido. O tamanho do buraco determina quanto do centro do gráfico fica vazio, transformando um gráfico de pizza comum em um gráfico de rosca.

```java
        // Insert a doughnut chart with a width of 500 and height of 350
        Chart doughnutChart = builder.insertChart(ChartType.DOUGHNUT, 500, 350);

        // Set the hole size to 30% of the chart radius
        doughnutChart.getDoughnutChart().setHoleSize(30);

        // Add sample data series
        doughnutChart.getNSeries().add("{10, 20, 30, 40}", true);
```

**Explicação:**  

* `insertChart(ChartType.DOUGHNUT, 500, 350)` cria o objeto de gráfico e reserva espaço na planilha.  
* `setHoleSize(30)` converte a pizza em um gráfico de rosca com 30 % de centro vazio.  
* `add("{10, 20, 30, 40}", true)` fornece quatro pontos de dados; a flag `true` indica à biblioteca que os valores devem ser tratados como uma única série.

**Caso de borda:** Se o tipo de gráfico selecionado não suportar um buraco (ex.: um gráfico de barras), chamar `getDoughnutChart()` lança uma exceção. Sempre verifique o tipo de gráfico antes de ajustar o tamanho do buraco.

---

## Etapa 3: **Inserir gráfico de pizza**

Depois que o gráfico de rosca estiver pronto, demonstramos como **inserir um gráfico de pizza** usando o mesmo builder. Esta etapa destaca a semelhança entre os dois tipos de gráfico e mostra como enfatizar uma fatia.

```java
        // Insert a pie chart next to the doughnut
        Chart pieChart = builder.insertChart(ChartType.PIE, 400, 300);

        // Add the same data series for consistency
        pieChart.getNSeries().add("{10, 20, 30, 40}", true);

        // Explode the first slice by 10% to draw attention
        pieChart.getSeries().get(0).setExplode(10);
```

**Explicação:**  

* `ChartType.PIE` indica ao builder que deve criar um gráfico de pizza clássico.  
* `setExplode(10)` desloca a primeira fatia em 10 % do raio, técnica comum para destacar um ponto de dados importante.  

**Dica:** O método `setExplode` funciona apenas na primeira série de um gráfico de pizza. Se houver várias séries, você deve direcionar o índice correto.

---

## Etapa 4: Salvar a pasta de trabalho

Por fim, grave a pasta de trabalho em um arquivo para que você possa visualizar os gráficos no Excel ou em qualquer visualizador compatível.

```java
        // Save the workbook to a file
        workbook.save("DoughnutAndPieChart.xlsx");
        System.out.println("Workbook created with doughnut and pie charts.");
    }
}
```

**Por que salvar agora:** Persistir a pasta de trabalho finaliza todas as operações de desenho. Tentar visualizar o arquivo antes de salvá‑lo resulta em um documento vazio ou incompleto.

**Resultado:** Ao abrir *DoughnutAndPieChart.xlsx* você verá um gráfico de rosca com 30 % de buraco à esquerda e um gráfico de pizza com a primeira fatia explodida à direita.

---

## Etapa 5: Variações comuns e solução de problemas

| Situação | Ajuste |
|-----------|------------|
| **Dimensões diferentes do gráfico** | Altere os argumentos de largura e altura em `insertChart`. |
| **Múltiplas séries de dados** | Chame `add` várias vezes ou passe uma string de array 2‑D. |
| **Tamanho de buraco dinâmico** | Calcule o tamanho do buraco com base no intervalo de dados e então chame `setHoleSize`. |
| **Explodir várias fatias** | Percorra `chart.getSeries().get(i).setExplode(percent)` para cada fatia que desejar deslocar. |
| **Biblioteca que não suporta rosca** | Use um gráfico de pizza e desenhe manualmente um círculo branco sobreposto, embora isso seja menos preciso. |

**Dica profissional:** Sempre chame `builder.flush()` (se disponível) após inserir gráficos ao trabalhar com pastas de trabalho grandes. Isso libera buffers internos e evita vazamentos de memória.

---

![Java code creating a doughnut chart and inserting a pie chart](https://example.com/images/doughnut-pie-java.png "exemplo de criação de gráfico de rosca em Java")

*A imagem ilustra o layout final da pasta de trabalho com ambos os gráficos lado a lado.*

---

## Conclusão

Agora você sabe como **criar um gráfico de rosca** e **inserir um gráfico de pizza** em Java usando uma API de builder fluente. O exemplo completo cobre inicialização, configuração de tamanho, dimensionamento do buraco, explosão de fatias e saída de arquivo. A partir daqui, você pode explorar personalizações adicionais, como cores, legendas e rótulos de dados, para atender aos requisitos dos seus relatórios.

**Próximos passos**

* Experimente recursos de **customização de gráficos Java** como preenchimentos em gradiente e rótulos de dados.  
* Integre a geração de gráficos em um serviço web que devolva a pasta de trabalho sob demanda.  
* Compare a abordagem de builder com outras bibliotecas (ex.: JFreeChart) para escolher a melhor solução para seu projeto.

Boa criação de gráficos!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Como criar um gráfico de rosca em um documento Word com Java](/words/english/java/images-shapes/how-to-create-doughnut-chart-in-a-word-document-with-java/)
- [Salvar documento Word após editar gráfico de rosca em Java](/words/english/java/using-document-elements/save-word-document-after-editing-doughnut-chart-in-java/)
- [Inserir gráfico de pizza em Java – Explodir, girar e destacar fatias](/words/english/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}