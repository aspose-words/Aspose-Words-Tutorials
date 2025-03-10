---
title: Usando opções de limpeza no Aspose.Words para Java
linktitle: Usando opções de limpeza
second_title: API de processamento de documentos Java Aspose.Words
description: Melhore a clareza do documento com as opções de limpeza do Aspose.Words para Java. Aprenda a remover parágrafos vazios, regiões não utilizadas e muito mais.
weight: 10
url: /pt/java/document-manipulation/using-cleanup-options/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Usando opções de limpeza no Aspose.Words para Java


## Introdução ao uso de opções de limpeza no Aspose.Words para Java

Neste tutorial, exploraremos como usar opções de limpeza no Aspose.Words para Java para manipular e limpar documentos durante o processo de mala direta. As opções de limpeza permitem que você controle vários aspectos da limpeza do documento, como remover parágrafos vazios, regiões não utilizadas e muito mais.

## Pré-requisitos

 Antes de começar, certifique-se de ter a biblioteca Aspose.Words for Java integrada ao seu projeto. Você pode baixá-la em[aqui](https://releases.aspose.com/words/java/).

## Etapa 1: Removendo parágrafos vazios

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Inserir campos de mesclagem
FieldMergeField mergeFieldOption1 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_1");
mergeFieldOption1.setFieldName("Option_1");
builder.write(" ? ");
FieldMergeField mergeFieldOption2 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_2");
mergeFieldOption2.setFieldName("Option_2");

// Definir opções de limpeza
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS);

// Habilitar parágrafos de limpeza com sinais de pontuação
doc.getMailMerge().setCleanupParagraphsWithPunctuationMarks(true);

// Executar mala direta
doc.getMailMerge().execute(new String[] { "Option_1", "Option_2" }, new Object[] { null, null });

// Salvar o documento
doc.save("WorkingWithCleanupOptions.CleanupParagraphsWithPunctuationMarks.docx");
```

Neste exemplo, criamos um novo documento, inserimos campos de mesclagem e definimos as opções de limpeza para remover parágrafos vazios. Além disso, habilitamos a remoção de parágrafos com sinais de pontuação. Após executar a mala direta, o documento é salvo com a limpeza especificada aplicada.

## Etapa 2: Removendo regiões não mescladas

```java
Document doc = new Document("Your Directory Path" + "Mail merge destination - Northwind suppliers.docx");
DataSet data = new DataSet();

// Defina opções de limpeza para remover regiões não utilizadas
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS);

// Executar mala direta com regiões
doc.getMailMerge().executeWithRegions(data);

// Salvar o documento
doc.save("WorkingWithCleanupOptions.RemoveUnmergedRegions.docx");
```

Neste exemplo, abrimos um documento existente com regiões de mesclagem, definimos as opções de limpeza para remover regiões não utilizadas e, em seguida, executamos a mala direta com dados vazios. Esse processo remove automaticamente as regiões não utilizadas do documento.

## Etapa 3: Removendo campos vazios

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Defina opções de limpeza para remover campos vazios
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_FIELDS);

// Executar mala direta
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Salvar o documento
doc.save("WorkingWithCleanupOptions.RemoveEmptyFields.docx");
```

Neste exemplo, abrimos um documento com campos de mesclagem, definimos as opções de limpeza para remover campos vazios e executamos a mala direta com dados. Após a mesclagem, todos os campos vazios serão removidos do documento.

## Etapa 4: Removendo campos não utilizados

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Defina opções de limpeza para remover campos não utilizados
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS);

// Executar mala direta
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Salvar o documento
doc.save("WorkingWithCleanupOptions.RemoveUnusedFields.docx");
```

Neste exemplo, abrimos um documento com campos de mesclagem, definimos as opções de limpeza para remover campos não utilizados e executamos a mala direta com dados. Após a mesclagem, todos os campos não utilizados serão removidos do documento.

## Etapa 5: Removendo campos de contenção

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Defina opções de limpeza para remover campos de contenção
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS);

// Executar mala direta
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Salvar o documento
doc.save("WorkingWithCleanupOptions.RemoveContainingFields.docx");
```

Neste exemplo, abrimos um documento com campos de mesclagem, definimos as opções de limpeza para remover campos de contenção e executamos a mala direta com dados. Após a mesclagem, os próprios campos serão removidos do documento.

## Etapa 6: Removendo linhas de tabela vazias

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Defina opções de limpeza para remover linhas de tabela vazias
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS);

// Executar mala direta
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Salvar o documento
doc.save("WorkingWithCleanupOptions.RemoveEmptyTableRows.docx");
```

Neste exemplo, abrimos um documento com uma tabela e mesclamos campos, definimos as opções de limpeza para remover linhas de tabela vazias e executamos a mala direta com dados. Após a mesclagem, quaisquer linhas de tabela vazias serão removidas do documento.

## Conclusão

Neste tutorial, você aprendeu como usar opções de limpeza no Aspose.Words para Java para manipular e limpar documentos durante o processo de mala direta. Essas opções fornecem controle refinado sobre a limpeza de documentos, permitindo que você crie documentos refinados e personalizados com facilidade.

## Perguntas frequentes

### Quais são as opções de limpeza no Aspose.Words para Java?

As opções de limpeza no Aspose.Words para Java são configurações que permitem que você controle vários aspectos da limpeza do documento durante o processo de mala direta. Elas permitem que você remova elementos desnecessários, como parágrafos vazios, regiões não utilizadas e muito mais, garantindo que seu documento final seja bem estruturado e polido.

### Como posso remover parágrafos vazios do meu documento?

 Para remover parágrafos vazios do seu documento usando o Aspose.Words para Java, você pode definir o`MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS` opção para true. Isso eliminará automaticamente os parágrafos que não têm conteúdo, resultando em um documento mais limpo.

###  Qual é o propósito do`REMOVE_UNUSED_REGIONS` cleanup option?

 O`MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS` A opção é usada para remover regiões em um documento que não têm dados correspondentes durante o processo de mala direta. Ela ajuda a manter seu documento organizado, livrando-se de espaços reservados não utilizados.

### Posso remover linhas de tabela vazias de um documento usando o Aspose.Words para Java?

 Sim, você pode remover linhas de tabela vazias de um documento definindo o`MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS`opção cleanup para true. Isso excluirá automaticamente quaisquer linhas de tabela que não contenham dados, garantindo uma tabela bem estruturada em seu documento.

###  O que acontece quando eu defino o`REMOVE_CONTAINING_FIELDS` option?

 Definindo o`MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS` opção removerá todo o campo de mesclagem, incluindo o parágrafo que o contém, do documento durante o processo de mala direta. Isso é útil quando você deseja eliminar campos de mesclagem e seu texto associado.

### Como posso remover campos de mesclagem não utilizados do meu documento?

 Para remover campos de mesclagem não utilizados de um documento, você pode definir o`MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS` opção para true. Isso eliminará automaticamente os campos de mesclagem que não forem preenchidos durante a mala direta, resultando em um documento mais limpo.

###  Qual é a diferença entre`REMOVE_EMPTY_FIELDS` and `REMOVE_UNUSED_FIELDS` cleanup options?

 O`REMOVE_EMPTY_FIELDS` opção remove campos de mesclagem que não têm dados ou estão vazios durante o processo de mala direta. Por outro lado, a`REMOVE_UNUSED_FIELDS`opção remove campos de mesclagem que não são preenchidos com dados durante a mesclagem. A escolha entre eles depende se você deseja remover campos sem conteúdo ou aqueles que não são usados na operação de mesclagem específica.

### Como posso habilitar a remoção de parágrafos com sinais de pontuação?

 Para habilitar a remoção de parágrafos com sinais de pontuação, você pode definir o`cleanupParagraphsWithPunctuationMarks` opção para true e especifique os sinais de pontuação a serem considerados para limpeza. Isso permite que você crie um documento mais refinado removendo parágrafos desnecessários somente de pontuação.

### Posso personalizar as opções de limpeza no Aspose.Words para Java?

Sim, você pode personalizar as opções de limpeza de acordo com suas necessidades específicas. Você pode escolher quais opções de limpeza aplicar e configurá-las de acordo com seus requisitos de limpeza de documentos, garantindo que seu documento final atenda aos seus padrões desejados.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
