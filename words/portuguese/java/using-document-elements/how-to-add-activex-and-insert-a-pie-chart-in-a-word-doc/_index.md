---
category: general
date: 2026-08-17
description: Como adicionar controles ActiveX e inserir um gráfico de pizza em um
  documento Word usando Aspose.Words. Explodir uma fatia e salvar como DOCX em poucos
  passos.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex
- insert pie chart
- save as docx
- how to insert chart
- explode pie slice
language: pt
lastmod: 2026-08-17
og_description: Como adicionar controles ActiveX, inserir um gráfico de pizza, destacar
  uma fatia e salvar como DOCX com Aspose.Words – guia completo passo a passo.
og_image_alt: Screenshot of a Word document showing an ActiveX button and a pie chart
  with an exploded slice
og_title: Como adicionar ActiveX e inserir um gráfico de pizza em um documento do
  Word
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: How to add ActiveX controls and insert a pie chart in a Word doc using
    Aspose.Words. Explode a slice and save as DOCX in a few steps.
  headline: How to add ActiveX and insert a pie chart in a Word doc
  type: TechArticle
tags:
- Aspose.Words
- ActiveX
- Chart
- DOCX
title: Como adicionar ActiveX e inserir um gráfico de pizza em um documento do Word
url: /pt/java/using-document-elements/how-to-add-activex-and-insert-a-pie-chart-in-a-word-doc/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como adicionar ActiveX e inserir um gráfico de pizza em um documento Word

Se você precisa **how to add ActiveX** controls e incorporar um gráfico em um documento Word, este tutorial mostra uma solução completa e executável. Usando Aspose.Words você pode colocar um ActiveX CommandButton, criar um gráfico de pizza, explodir uma fatia para ênfase e, finalmente, **save as DOCX** em apenas algumas linhas de C#.

Nas seções abaixo você verá todas as importações necessárias, um código completo e explicações sobre por que cada passo é importante. Ao final, você será capaz de integrar controles interativos e dados visuais em qualquer arquivo .docx que gerar programaticamente.

## Pré-requisitos

Antes de começar, certifique‑se de que você tem:

* .NET 6.0 ou posterior (o código também funciona com .NET Framework 4.7+)
* Pacote Aspose.Words for .NET (disponível via NuGet)
* Um ambiente de desenvolvimento como Visual Studio 2022 ou VS Code
* Familiaridade básica com C# e o modelo de objetos do Word

Nenhuma biblioteca de gráficos de terceiros adicional é necessária—Aspose.Words fornece criação de gráficos incorporada.

## Como adicionar controles ActiveX com Aspose.Words

Os controles ActiveX permitem incorporar elementos de UI interativos diretamente em um arquivo Word. Neste guia adicionamos um **CommandButton** que pode ser posteriormente conectado a código VBA.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Step 1: Create a new document and a DocumentBuilder
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Step 2: Insert a group shape to hold the ActiveX control
GroupShape groupShape = builder.InsertGroupShape();

// Step 3: Insert a rectangle shape, hide it, and attach it to the group
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
groupShape.AppendChild(rectangleShape);
rectangleShape.SetHidden(true);

// Step 4: Insert a plain‑text StructuredDocumentTag (optional placeholder)
StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, "MyTag");

// Step 5: Insert the CommandButton ActiveX control
Forms2OleControl commandButton = builder.InsertForms2OleControl();
commandButton.SetActiveXControlType(Forms2OleControlType.CommandButton);
commandButton.SetCaption("Click Me");

// The CommandButton now appears in the document and can be used in VBA macros.
```

**Por que isso funciona:**  
`InsertForms2OleControl` cria um contêiner OLE que a UI do Word reconhece como um controle ActiveX. Definir o tipo de controle para `CommandButton` e atribuir uma legenda faz com que ele se comporte como um botão padrão quando o usuário abre o arquivo no Word.

## Inserir gráfico de pizza e explodir uma fatia

Gráficos são úteis para visualizar dados sem sair do documento. As etapas a seguir demonstram **how to insert chart** e, especificamente, um **pie chart** cuja primeira fatia está explodida.

```csharp
// Step 6: Insert a pie chart (400 × 300 points)
Chart pieChart = (Chart)builder.InsertChart(ChartType.Pie, 400, 300);

// Populate the chart with sample data
pieChart.Series.Clear();
ChartSeries series = pieChart.Series.Add("Sales", new[] { "Q1", "Q2", "Q3", "Q4" },
                                          new[] { 12000, 15000, 9000, 13000 });

// Step 7: Explode the first slice for emphasis
series.SetExplode(0, true);

// Optional: Customize colors or labels here if needed
```

**Por que explodir a fatia:**  
Chamar `SetExplode(0, true)` indica ao Aspose.Words para deslocar o primeiro ponto de dados, atraindo o olhar do observador para esse segmento. Essa é uma técnica comum em apresentações para destacar um valor chave.

## Salvar como DOCX

Depois de adicionar o botão ActiveX e o gráfico, persista o documento no disco. Esta etapa demonstra **save as DOCX** usando o método padrão.

```csharp
// Step 8: Save the document in DOCX format
document.Save("Output.docx", SaveFormat.Docx);
```

O arquivo `Output.docx` agora contém um botão interativo, um gráfico de pizza com uma fatia explodida e pode ser aberto no Microsoft Word sem plugins adicionais.

## Exemplo completo executável

Juntando tudo, aqui está um programa autocontido que você pode copiar para uma aplicação console e executar imediatamente.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Create document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert group shape and hidden rectangle (required for ActiveX positioning)
        GroupShape group = builder.InsertGroupShape();
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        group.AppendChild(rect);
        rect.SetHidden(true);

        // Optional placeholder tag
        builder.InsertStructuredDocumentTag(StructuredDocumentTagType.PlainText, "MyTag");

        // Insert CommandButton ActiveX control
        Forms2OleControl button = builder.InsertForms2OleControl();
        button.SetActiveXControlType(Forms2OleControlType.CommandButton);
        button.SetCaption("Click Me");

        // Insert pie chart and explode first slice
        Chart chart = (Chart)builder.InsertChart(ChartType.Pie, 400, 300);
        chart.Series.Clear();
        ChartSeries series = chart.Series.Add("Revenue", new[] { "Jan", "Feb", "Mar" },
                                               new[] { 5000, 7000, 3000 });
        series.SetExplode(0, true); // explode pie slice

        // Save the document
        doc.Save("Output.docx", SaveFormat.Docx);

        Console.WriteLine("Document created successfully: Output.docx");
    }
}
```

**Resultado esperado:**  
Abrir `Output.docx` no Word mostra um botão rotulado *Click Me* e um gráfico de pizza onde a primeira fatia (January) está deslocada das demais. O botão está pronto para manipulação de eventos VBA, e o gráfico pode ser editado usando as ferramentas de gráfico nativas do Word.

## Perguntas comuns e casos de borda

* **Posso adicionar outros tipos de ActiveX?**  
  Sim. Substitua `Forms2OleControlType.CommandButton` por qualquer valor do enum `Forms2OleControlType` (por exemplo, `CheckBox`, `OptionButton`). O mesmo padrão de inserção se aplica.

* **E se eu precisar de um tipo de gráfico diferente?**  
  Use `ChartType.Bar`, `ChartType.Line`, etc., na chamada `InsertChart`. A etapa **how to insert chart** permanece idêntica; apenas o valor do enum muda.

* **Como controlar o tamanho da fatia explodida?**  
  O Aspose.Words atualmente suporta apenas uma flag binária de explosão (true/false). Para controle mais fino (por exemplo, distância de deslocamento) seria necessário editar o OOXML subjacente após a gravação.

* **O documento é compatível com versões mais antigas do Word?**  
  Salvar como DOCX garante compatibilidade com Word 2007 e posteriores. Para Word 2003 você poderia mudar para `SaveFormat.Doc`, mas o suporte a ActiveX é limitado nesse formato.

* **Preciso referenciar `System.Drawing`?**  
  Não. Todos os objetos de desenho são fornecidos pelo Aspose.Words, portanto o único pacote NuGet necessário é `Aspose.Words`.

## Conclusão

Agora você sabe **how to add ActiveX**, **insert a pie chart**, **explode a pie slice** e **save as DOCX** usando Aspose.Words para .NET. O exemplo completo cobre cada passo, desde a criação do documento até a persistência final, e explica o raciocínio por trás de cada chamada de API.

Em seguida, você pode explorar:

* Adicionar macros VBA que respondam ao clique do CommandButton (**how to insert chart** e automatizar atualizações de dados)
* Personalizar a aparência do gráfico (cores, rótulos de dados) para combinar com a identidade corporativa
* Incorporar controles ActiveX adicionais, como **ComboBox** ou **ListBox**, para formulários mais ricos

Sinta‑se à vontade para experimentar o código, substituir os dados de exemplo e integrar a solução em seus próprios pipelines de geração de documentos. Feliz codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Inserir Gráfico de Colunas no Word Usando Aspose.Words para .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Inserir um Gráfico de Colunas Simples no Word Usando Aspose.Words para .NET](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [Inserir um Gráfico de Bolhas no Word Usando Aspose.Words para .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}