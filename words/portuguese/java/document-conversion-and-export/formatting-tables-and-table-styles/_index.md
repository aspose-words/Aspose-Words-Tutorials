---
date: 2025-11-28
description: Aprenda a alterar as bordas das células e formatar tabelas usando Aspose.Words
  para Java. Este guia passo a passo cobre a definição de bordas, a aplicação do estilo
  de primeira coluna, o ajuste automático do conteúdo da tabela e a aplicação de estilos
  de tabela.
language: pt
linktitle: How to Change Cell Borders in Tables – Aspose.Words for Java
second_title: Aspose.Words Java Document Processing API
title: Como Alterar as Bordas das Células em Tabelas – Aspose.Words para Java
url: /java/document-conversion-and-export/formatting-tables-and-table-styles/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Como Alterar as Bordas das Células em Tabelas – Aspose.Words para Java

## Introdução

Quando se trata de formatação de documentos, as tabelas desempenham um papel crucial, e **saber como alterar as bordas das células** é essencial para criar layouts claros e profissionais. Se você está desenvolvendo com Java e Aspose.Words, já tem um conjunto de ferramentas poderoso ao seu alcance. Neste tutorial vamos percorrer todo o processo de formatação de tabelas, alteração das bordas das células, aplicação do *estilo da primeira coluna* e uso do *auto‑fit do conteúdo da tabela* para que seus documentos tenham um aspecto refinado.

## Respostas Rápidas
- **Qual é a classe principal para criar tabelas?** `DocumentBuilder` cria tabelas e células programaticamente.  
- **Como altero a espessura da borda de uma única célula?** Use `builder.getCellFormat().getBorders().getLeft().setLineWidth(value)`.  
- **Posso aplicar um estilo de tabela predefinido?** Sim – chame `table.setStyleIdentifier(StyleIdentifier.YOUR_STYLE)`.  
- **Qual método ajusta automaticamente a tabela ao seu conteúdo?** `table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)`.  
- **Preciso de licença para produção?** Uma licença válida do Aspose.Words é necessária para uso não‑trial.

## O que significa “como alterar bordas de células” no Aspose.Words?

Alterar as bordas das células significa personalizar as linhas visuais que separam as células — cor, largura e estilo da linha. O Aspose.Words expõe uma API rica que permite ajustar essas propriedades na tabela, na linha ou na célula individual, oferecendo controle detalhado sobre a aparência dos seus documentos.

## Por que usar Aspose.Words para Java na estilização de tabelas?

- **Aparência consistente em todas as plataformas** – o mesmo código de estilização funciona no Windows, Linux e macOS.  
- **Sem dependência do Microsoft Word** – gere ou modifique documentos no lado do servidor.  
- **Biblioteca de estilos rica** – estilos de tabela embutidos (por exemplo, *estilo da primeira coluna*) e recursos completos de auto‑fit.  

## Pré‑requisitos

1. **Java Development Kit (JDK) 8+** – certifique‑se de que `java` está no seu PATH.  
2. **IDE** – IntelliJ IDEA, Eclipse ou qualquer editor de sua preferência.  
3. **Aspose.Words para Java** – faça o download do JAR mais recente no [site oficial](https://releases.aspose.com/words/java/).  
4. **Conhecimento básico de Java** – você deve estar confortável criando um projeto Maven/Gradle e adicionando JARs externos.

## Importar Pacotes

Para começar a trabalhar com tabelas, você precisa das classes principais do Aspose.Words:

```java
import com.aspose.words.*;
```

Esta única importação lhe dá acesso a `Document`, `DocumentBuilder`, `Table`, `StyleIdentifier` e muitas outras utilidades.

## Como Alterar as Bordas das Células

A seguir criaremos uma tabela simples, alteraremos suas bordas gerais e, depois, personalizaremos células individuais.

### Etapa 1: Carregar um Novo Documento

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Etapa 2: Criar a Tabela e Definir Bordas Globais

```java
Table table = builder.startTable();
builder.insertCell();

// Set the borders for the entire table.
table.setBorders(LineStyle.SINGLE, 2.0, Color.BLACK);
        
// Set the cell shading for this cell.
builder.getCellFormat().getShading().setBackgroundPatternColor(Color.RED);
builder.writeln("Cell #1");

builder.insertCell();
        
// Specify a different cell shading for the second cell.
builder.getCellFormat().getShading().setBackgroundPatternColor(Color.GREEN);
builder.writeln("Cell #2");

builder.endRow();
```

### Etapa 3: Alterar as Bordas de uma Única Célula

```java
// Clear the cell formatting from previous operations.
builder.getCellFormat().clearFormatting();

builder.insertCell();

// Create larger borders for the first cell of this row.
builder.getCellFormat().getBorders().getLeft().setLineWidth(4.0);
builder.getCellFormat().getBorders().getRight().setLineWidth(4.0);
builder.getCellFormat().getBorders().getTop().setLineWidth(4.0);
builder.getCellFormat().getBorders().getBottom().setLineWidth(4.0);
builder.writeln("Cell #3");

builder.insertCell();
builder.getCellFormat().clearFormatting();
builder.writeln("Cell #4");
        
doc.save("FormatTableAndCellWithDifferentBorders.docx");
```

#### O que o código faz
- **Bordas globais** – `table.setBorders` aplica à tabela inteira uma linha preta de 2 pontos.  
- **Sombras de célula** – Demonstra como colorir células individuais (vermelho e verde).  
- **Bordas personalizadas de célula** – A terceira célula recebe uma borda de 4 pontos em todos os lados, destacando‑se.

## Aplicando Estilos de Tabela (incluindo o Estilo da Primeira Coluna)

Os estilos de tabela permitem aplicar uma aparência consistente com uma única chamada. Também mostraremos como habilitar o *estilo da primeira coluna* e ajustar automaticamente a tabela ao seu conteúdo.

### Etapa 4: Criar um Novo Documento para Estilização

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Table table = builder.startTable();
        
// We must insert at least one row first before setting any table formatting.
builder.insertCell();
```

### Etapa 5: Aplicar um Estilo Predefinido e Habilitar a Formatação da Primeira Coluna

```java
// Set the table style based on a unique style identifier.
table.setStyleIdentifier(StyleIdentifier.MEDIUM_SHADING_1_ACCENT_1);
        
// Apply which features should be formatted by the style.
table.setStyleOptions(TableStyleOptions.FIRST_COLUMN | TableStyleOptions.ROW_BANDS | TableStyleOptions.FIRST_ROW);

// Auto‑fit the table so columns shrink or expand to fit the content.
table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS);
```

### Etapa 6: Preencher a Tabela com Dados

```java
builder.writeln("Item");
builder.getCellFormat().setRightPadding(40.0);
builder.insertCell();
builder.writeln("Quantity (kg)");
builder.endRow();

builder.insertCell();
builder.writeln("Apples");
builder.insertCell();
builder.writeln("20");
builder.endRow();

builder.insertCell();
builder.writeln("Bananas");
builder.insertCell();
builder.writeln("40");
builder.endRow();

builder.insertCell();
builder.writeln("Carrots");
builder.insertCell();
builder.writeln("50");
builder.endRow();

doc.save("BuildTableWithStyle.docx");
```

#### Por que isso importa
- **Identificador de estilo** – `MEDIUM_SHADING_1_ACCENT_1` confere à tabela uma aparência limpa e sombreada.  
- **Estilo da primeira coluna** – Destacar a primeira coluna melhora a legibilidade, especialmente em relatórios.  
- **Faixas de linhas** – Cores alternadas nas linhas facilitam a visualização de tabelas extensas.  
- **Auto‑fit** – Garante que a largura da tabela se ajuste ao conteúdo, evitando texto cortado.

## Problemas Comuns & Solução de Problemas

| Problema | Causa Típica | Correção Rápida |
|----------|--------------|-----------------|
| Bordas não aparecem | Uso de `clearFormatting()` após definir bordas | Defina as bordas **depois** de limpar a formatação, ou reaplique‑as. |
| Sombreamento ignorado em células mescladas | Sombreamento aplicado antes da mesclagem | Aplique o sombreamento **depois** de mesclar as células. |
| Largura da tabela excede as margens da página | Nenhum auto‑fit aplicado | Chame `table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)` ou defina uma largura fixa. |
| Estilo não aplicado | Valor de `StyleIdentifier` incorreto | Verifique se o identificador existe na versão do Aspose.Words que você está usando. |

## Perguntas Frequentes

**P: Posso usar estilos de tabela personalizados que não estão nas opções padrão?**  
R: Sim, você pode criar e aplicar estilos personalizados programaticamente. Consulte a [documentação do Aspose.Words](https://reference.aspose.com/words/java/) para detalhes.

**P: Como aplicar formatação condicional às células?**  
R: Use lógica Java padrão para inspecionar os valores das células e, em seguida, chame os métodos de formatação apropriados (por exemplo, altere a cor de fundo se um valor ultrapassar um limite).

**P: É possível formatar células mescladas da mesma forma que células normais?**  
R: Absolutamente. Após mesclar as células, aplique sombreamento ou bordas usando as mesmas APIs `CellFormat`.

**P: E se eu precisar que a tabela redimensione dinamicamente com base na entrada do usuário?**  
R: Ajuste as larguras das colunas ou chame `autoFit` novamente após inserir novos dados para recalcular o layout.

**P: Onde posso encontrar mais exemplos de estilização de tabelas?**  
R: O [Aspose.Words API documentation](https://reference.aspose.com/words/java/) oficial contém um conjunto abrangente de amostras.

## Conclusão

Agora você possui um conjunto completo de ferramentas para **alterar as bordas das células**, aplicar o *estilo da primeira coluna* e **ajustar automaticamente o conteúdo da tabela** usando Aspose.Words para Java. Ao dominar essas técnicas, você pode produzir documentos ricos em dados e visualmente atraentes — perfeitos para relatórios, faturas e qualquer outra saída crítica para negócios.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**Última atualização:** 2025-11-28  
**Testado com:** Aspose.Words para Java 24.12 (mais recente no momento da escrita)  
**Autor:** Aspose