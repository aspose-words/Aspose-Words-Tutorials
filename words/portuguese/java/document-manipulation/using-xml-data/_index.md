---
title: Usando dados XML no Aspose.Words para Java
linktitle: Usando dados XML
second_title: API de processamento de documentos Java Aspose.Words
description: Desbloqueie o poder do Aspose.Words para Java. Aprenda manipulação de dados XML, mala direta e sintaxe Mustache com tutoriais passo a passo.
weight: 12
url: /pt/java/document-manipulation/using-xml-data/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Usando dados XML no Aspose.Words para Java


## Introdução ao uso de dados XML no Aspose.Words para Java

Neste guia, exploraremos como trabalhar com dados XML usando Aspose.Words para Java. Você aprenderá como executar operações de mala direta, incluindo mala direta aninhadas, e utilizar a sintaxe Mustache com um DataSet. Forneceremos instruções passo a passo e exemplos de código-fonte para ajudar você a começar.

## Pré-requisitos

Antes de começar, certifique-se de que você tenha os seguintes pré-requisitos:
- [Aspose.Words para Java](https://products.aspose.com/words/java/) instalado.
- Arquivos de dados XML de exemplo para clientes, pedidos e fornecedores.
- Exemplos de documentos do Word para destinos de mala direta.

## Mala direta com dados XML

### 1. Mala direta básica

Para executar uma mala direta básica com dados XML, siga estas etapas:

```java
DataSet customersDs = new DataSet();
customersDs.readXml("Your Directory Path" + "Mail merge data - Customers.xml");
Document doc = new Document("Your Directory Path" + "Mail merge destinations - Registration complete.docx");
doc.getMailMerge().execute(customersDs.getTables().get("Customer"));
doc.save("Your Directory Path" + "BasicMailMerge.docx");
```

### 2. Mala direta aninhada

Para mala direta aninhadas, use o seguinte código:

```java
DataSet pizzaDs = new DataSet();
pizzaDs.readXml("Your Directory Path" + "Mail merge data - Orders.xml");
Document doc = new Document("Your Directory Path" + "Mail merge destinations - Invoice.docx");
doc.getMailMerge().setTrimWhitespaces(false);
doc.getMailMerge().executeWithRegions(pizzaDs);
doc.save("Your Directory Path" + "NestedMailMerge.docx");
```

## Sintaxe do Mustache usando DataSet

Para aproveitar a sintaxe Mustache com um DataSet, siga estas etapas:

```java
DataSet ds = new DataSet();
ds.readXml("Your Directory Path" + "Mail merge data - Vendors.xml");
Document doc = new Document("Your Directory Path" + "Mail merge destinations - Vendor.docx");
doc.getMailMerge().setUseNonMergeFields(true);
doc.getMailMerge().executeWithRegions(ds);
doc.save("Your Directory Path" + "MustacheSyntaxUsingDataSet.docx");
```

## Conclusão

Neste guia abrangente, exploramos como usar efetivamente dados XML com Aspose.Words para Java. Você aprendeu como executar várias operações de mala direta, incluindo mala direta básica, mala direta aninhada e como utilizar a sintaxe Mustache com um DataSet. Essas técnicas permitem que você automatize a geração e a personalização de documentos com facilidade.

## Perguntas frequentes

### Como posso preparar meus dados XML para mala direta?

Certifique-se de que seus dados XML sigam a estrutura necessária, com tabelas e relacionamentos definidos, conforme mostrado nos exemplos fornecidos.

### Posso personalizar o comportamento de corte para valores de mala direta?

 Sim, você pode controlar se os espaços em branco iniciais e finais são aparados durante a mala direta usando`doc.getMailMerge().setTrimWhitespaces(false)`.

### O que é a sintaxe Mustache e quando devo usá-la?

 A sintaxe Mustache permite que você formate campos de mala direta de uma forma mais flexível. Use`doc.getMailMerge().setUseNonMergeFields(true)` para habilitar a sintaxe Mustache.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
