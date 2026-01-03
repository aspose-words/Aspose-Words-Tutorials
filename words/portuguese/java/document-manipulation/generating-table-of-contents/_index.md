---
date: 2026-01-03
description: Aprenda a ajustar números de página ao inserir um índice usando Aspose.Words
  para Java. Personalize os estilos do índice e crie documentos sem esforço.
linktitle: Generating Table of Contents
second_title: Aspose.Words Java Document Processing API
title: Ajustar Números de Página e Gerar Sumário com Aspose.Words para Java
url: /pt/java/document-manipulation/generating-table-of-contents/
weight: 21
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ajustar Números de Página e Gerar Sumário no Aspose.Words para Java

Neste tutorial você descobrirá como **ajustar números de página** e **inserir um sumário** (TOC) com Aspose.Words para Java. Um sumário bem estruturado facilita a navegação em documentos extensos, e o ajuste fino do alinhamento dos números de página oferece aos leitores uma experiência profissional. Vamos percorrer a criação de um documento, a personalização dos estilos do sumário e a modificação das tabulações para que os números de página se alinhem exatamente onde você deseja.

## Respostas Rápidas
- **O que significa “ajustar números de página”?** Modificar as tabulações que alinham os números de página em um sumário.  
- **Posso inserir um sumário automaticamente?** Sim – use a classe `FieldToc`.  
- **Preciso de licença para executar o código?** Uma avaliação gratuita funciona para desenvolvimento; uma licença é necessária para produção.  
- **Qual versão do Aspose é suportada?** Os exemplos funcionam com a versão mais recente do Aspose.Words para Java.  
- **É possível personalizar os estilos do sumário?** Absolutamente – você pode alterar fontes, negrito e muito mais.

## O que é um Sumário no Aspose.Words?
Um sumário é um campo que varre o documento em busca de estilos de título (por exemplo, Heading 1, Heading 2) e gera uma lista de entradas com números de página. Aspose.Words permite inserir esse campo programaticamente e controlar totalmente sua aparência.

## Por que ajustar números de página em um sumário?
Ajustar as tabulações oferece controle preciso sobre onde os números de página aparecem, o que é essencial para:

- Manter um layout limpo e alinhado em colunas.  
- Atender a guias de estilo corporativo.  
- Melhorar a legibilidade em documentos impressos e digitais.

## Pré‑requisitos
- Aspose.Words para Java adicionado ao seu projeto (Maven/Gradle).  
- Familiaridade básica com a sintaxe Java.  

## Guia Passo a Passo

### Etapa 1: Criar um novo documento
Primeiro, instancie um objeto `Document` vazio que conterá seu conteúdo e o sumário.

```java
Document doc = new Document();
```

### Etapa 2: Personalizar estilos do sumário
Você pode mudar a aparência de cada nível do sumário. Neste exemplo, tornamos as entradas de primeiro nível em negrito, que é uma solicitação de formatação comum.

```java
doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_1).getFont().setBold(true);
```

### Etapa 3: Adicionar conteúdo ao seu documento
Insira títulos (por exemplo, `Heading1`, `Heading2`) e parágrafos regulares. O campo de sumário capturará esses títulos automaticamente. *(Código omitido por brevidade – o foco está na geração do sumário.)*

### Etapa 4: Inserir o campo de sumário
Coloque o sumário onde desejar — tipicamente no início do documento.

```java
// Insert a TOC field at the desired location in your document.
FieldToc fieldToc = new FieldToc();
doc.getFirstSection().getBody().getFirstParagraph().appendChild(fieldToc);
```

### Etapa 5: Salvar o documento
Persista o documento no disco. Você pode escolher qualquer formato suportado, como DOCX, PDF ou HTML.

```java
doc.save("your_output_path_here");
```

## Personalizando Tabulações no Sumário (Ajustar Números de Página)
Se a tabulação padrão não alinhar os números de página da maneira que você precisa, pode iterar por todos os parágrafos do sumário e modificar suas posições de tabulação.

```java
Document doc = new Document("Table of contents.docx");

for (Paragraph para : (Iterable<Paragraph>) doc.getChildNodes(NodeType.PARAGRAPH, true))
{
    if (para.getParagraphFormat().getStyle().getStyleIdentifier() >= StyleIdentifier.TOC_1 &&
        para.getParagraphFormat().getStyle().getStyleIdentifier() <= StyleIdentifier.TOC_9)
    {
        // Get the first tab used in this paragraph, which aligns the page numbers.
        TabStop tab = para.getParagraphFormat().getTabStops().get(0);
        
        // Remove the old tab.
        para.getParagraphFormat().getTabStops().removeByPosition(tab.getPosition());
        
        // Insert a new tab at a modified position (e.g., 50 units to the left).
        para.getParagraphFormat().getTabStops().add(tab.getPosition() - 50.0, tab.getAlignment(), tab.getLeader());
    }
}

doc.save("output.docx");
```

Agora as entradas do sumário exibem os números de página exatamente onde você quer, conferindo ao documento um aspecto refinado.

## Problemas Comuns & Dicas
- **Títulos ausentes no sumário:** Certifique‑se de que seus títulos utilizem estilos incorporados (`Heading1`, `Heading2`, etc.) ou mapeie estilos personalizados para níveis do sumário.  
- **Tabulação não aplicada:** Verifique se o parágrafo realmente pertence a um estilo de sumário (`TOC_1`‑`TOC_9`).  
- **Desempenho em documentos grandes:** Chame `doc.updateFields()` após inserir o sumário para atualizar as entradas em uma única passagem.

## Perguntas Frequentes

**P: Como altero a formatação das entradas do sumário?**  
R: Use `doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_X)`, onde *X* é o nível (1‑9), e modifique sua fonte, cor ou configurações de parágrafo.

**P: Como adiciono mais níveis ao meu sumário?**  
R: Ajuste a opção `\o "1-3"` da classe `FieldToc` (por exemplo) para incluir níveis de título adicionais, depois atualize os estilos correspondentes `TOC_X`.

**P: Posso mudar as posições das tabulações para entradas específicas do sumário?**  
R: Sim – itere pelos parágrafos conforme mostrado na seção “Personalizando Tabulações” e modifique cada tabulação individualmente.

**P: É possível gerar um sumário em saída PDF?**  
R: Absolutamente. Salve o documento como PDF (`doc.save("output.pdf")`) após gerar o sumário; o campo é renderizado automaticamente.

**P: Preciso chamar `updateFields()` manualmente?**  
R: Quando você insere um `FieldToc`, o Aspose.Words o atualiza ao salvar, mas chamar `doc.updateFields()` fornece resultados imediatos para depuração.

## Conclusão
Você aprendeu como **ajustar números de página**, **inserir um sumário** e **personalizar estilos do sumário** usando Aspose.Words para Java. Essas técnicas permitem criar documentos limpos, navegáveis e formatados profissionalmente, atendendo a qualquer padrão de publicação.

---  

**Última atualização:** 2026-01-03  
**Testado com:** Aspose.Words para Java (última versão)  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}