---
date: 2026-01-11
description: Aprenda a limpar documentos Word usando as opções de limpeza do Aspose.Words
  para Java, incluindo a remoção de parágrafos vazios, linhas de tabela vazias e campos
  não utilizados.
linktitle: Using Cleanup Options
second_title: Aspose.Words Java Document Processing API
title: Limpar documento Word usando as opções de limpeza do Aspose.Words (Java)
url: /pt/java/document-manipulation/using-cleanup-options/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Limpar Documento Word Usando Opções de Limpeza do Aspose.Words (Java)

Neste tutorial você descobrirá como **limpar documentos Word** com o Aspose.Words para Java. Seja gerando faturas, contratos ou relatórios de mala‑direta em massa, parágrafos vazios indesejados, campos não utilizados ou linhas de tabela em branco podem fazer o resultado final parecer pouco profissional. Vamos percorrer cada opção de limpeza passo a passo, mostrar o código exato que você precisa e explicar *por que* cada configuração importa para que você produza documentos bem acabados todas as vezes.

## Respostas Rápidas
- **O que significa “limpar documento Word”?** Remover parágrafos vazios, regiões de mesclagem não usadas, linhas de tabela vazias e outros elementos redundantes após uma operação de mala‑direta.  
- **Qual opção de limpeza remove parágrafos vazios?** `MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS`.  
- **Como excluir linhas de tabela vazias?** Use `MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS`.  
- **Posso eliminar campos que nunca foram preenchidos?** Sim – `MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS` ou `REMOVE_EMPTY_FIELDS`.  
- **Preciso de licença para executar esses exemplos?** Uma avaliação gratuita funciona para testes; uma licença comercial é necessária para uso em produção.

## O Que Significa “Limpar Documento Word” no Contexto de Mala‑Direta?
Quando você realiza uma mala‑direta, o Aspose.Words insere dados em campos e regiões de mesclagem. Se alguns campos recebem `null` ou strings vazias, o documento pode acabar com parágrafos soltos, tabelas vazias ou regiões de espaço reservado. As **opções de limpeza** removem automaticamente esses artefatos, deixando um documento limpo e pronto para impressão.

## Por Que Usar Opções de Limpeza?
- **Aparência profissional:** Sem linhas em branco ou tabelas órfãs.  
- **Tamanho de arquivo menor:** Remover elementos não usados reduz o peso do documento.  
- **Processamento subsequente simplificado:** Documentos limpos são mais fáceis de converter para PDF, HTML ou outros formatos.  
- **Economia de tempo:** Configurações de uma linha substituem scripts manuais de pós‑processamento.

## Pré‑requisitos
- Ambiente de desenvolvimento Java (JDK 8+).  
- Biblioteca Aspose.Words para Java – faça o download [aqui](https://releases.aspose.com/words/java/).  
- Familiaridade básica com conceitos de mala‑direta.

## Guia Passo a Passo

### Etapa 1: Como Remover Parágrafos Vazios (Java)
Primeiro, vamos mostrar como eliminar parágrafos que não contêm texto visível. Isso é especialmente útil quando um campo de mesclagem resolve para `null`.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert merge fields
FieldMergeField mergeFieldOption1 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_1");
mergeFieldOption1.setFieldName("Option_1");
builder.write(" ? ");
FieldMergeField mergeFieldOption2 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_2");
mergeFieldOption2.setFieldName("Option_2");

// Set cleanup options
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS);

// Enable cleanup of paragraphs that contain only punctuation marks
doc.getMailMerge().setCleanupParagraphsWithPunctuationMarks(true);

// Execute mail merge (both fields are null, so they become empty)
doc.getMailMerge().execute(new String[] { "Option_1", "Option_2" }, new Object[] { null, null });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.CleanupParagraphsWithPunctuationMarks.docx");
```

**O que acontece aqui?**  
- `REMOVE_EMPTY_PARAGRAPHS` indica ao Aspose.Words que elimine qualquer parágrafo que fique vazio após a mesclagem.  
- Habilitar `cleanupParagraphsWithPunctuationMarks` também remove parágrafos que consistem apenas de pontuação (por exemplo, “?”).

### Etapa 2: Como Remover Regiões Não Mescladas
Se uma região de mala‑direta não tem dados correspondentes, você pode descartá‑la completamente.

```java
Document doc = new Document("Your Directory Path" + "Mail merge destination - Northwind suppliers.docx");
DataSet data = new DataSet();

// Set cleanup options to remove unused regions
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS);

// Execute mail merge with regions (the DataSet is empty)
doc.getMailMerge().executeWithRegions(data);

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveUnmergedRegions.docx");
```

**Por que isso importa:**  
Regiões não usadas costumam deixar seções em branco ou cabeçalhos soltos. O sinalizador `REMOVE_UNUSED_REGIONS` as limpa automaticamente.

### Etapa 3: Como Remover Campos Vazios
Quando um campo recebe uma string vazia, pode ser desejável remover todo o campo ao invés de deixar um espaço em branco.

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove empty fields
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_FIELDS);

// Execute mail merge with a mix of populated and empty values
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveEmptyFields.docx");
```

### Etapa 4: Como Remover Campos Não Utilizados
Se certos campos nunca são referenciados durante a mesclagem, você pode eliminá‑los totalmente.

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove unused fields
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS);

// Execute mail merge
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveUnusedFields.docx");
```

### Etapa 5: Como Remover Campos Contenedores
Às vezes um campo de mesclagem está dentro de um parágrafo que você também deseja descartar.

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove containing fields
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS);

// Execute mail merge
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveContainingFields.docx");
```

### Etapa 6: Como Remover Linhas de Tabela Vazias
Tabelas frequentemente terminam com linhas que contêm apenas campos vazios. Esta opção poda essas linhas.

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove empty table rows
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS);

// Execute mail merge
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveEmptyTableRows.docx");
```

## Problemas Comuns & Solução de Problemas
- **Parágrafos não removidos:** Certifique‑se de que `setCleanupParagraphsWithPunctuationMarks(true)` seja chamado *depois* de definir a opção de limpeza.  
- **Linhas de tabela vazias persistem:** Verifique se as células da tabela realmente contêm strings vazias (não apenas espaços em branco).  
- **Campos não usados permanecem:** Verifique se você está usando o enum correto (`REMOVE_UNUSED_FIELDS`) e se os campos de mesclagem não são preenchidos acidentalmente em outro lugar.

## Perguntas Frequentes

**P: Qual a diferença entre `REMOVE_EMPTY_FIELDS` e `REMOVE_UNUSED_FIELDS`?**  
R: `REMOVE_EMPTY_FIELDS` exclui campos que recebem uma string vazia ou `null` durante a mesclagem, enquanto `REMOVE_UNUSED_FIELDS` remove campos que nunca foram referenciados pela operação de mesclagem.

**P: Posso combinar várias opções de limpeza?**  
R: Sim. O método `setCleanupOptions` aceita um OR bit a bit dos valores do enum, permitindo limpar parágrafos, tabelas e regiões em uma única chamada.

**P: Habilitar `cleanupParagraphsWithPunctuationMarks` afeta texto normal?**  
R: Ele remove apenas parágrafos que consistem exclusivamente de caracteres de pontuação (por exemplo, “?” ou “---”). Sentenças regulares permanecem intactas.

**P: É possível personalizar quais sinais de pontuação são considerados?**  
R: A API atual usa um conjunto predefinido de caracteres de pontuação. Para comportamento customizado, seria necessário pós‑processar o documento após a mesclagem.

**P: Essas opções de limpeza funcionam com conversão para PDF?**  
R: Absolutamente. Depois que o documento Word é limpo, você pode convertê‑lo para PDF, HTML ou qualquer outro formato suportado sem transportar os elementos indesejados.

## Conclusão
Agora você possui um conjunto completo de ferramentas para **limpar documentos Word** durante a mala‑direta com o Aspose.Words para Java. Selecionando as `MailMergeCleanupOptions` adequadas, você pode remover automaticamente parágrafos vazios, linhas de tabela vazias, campos não usados e muito mais — entregando um documento elegante e pronto para produção a cada execução.

---

**Última atualização:** 2026-01-11  
**Testado com:** Aspose.Words para Java 24.11  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}