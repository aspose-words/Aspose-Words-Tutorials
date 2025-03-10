---
title: Usando revisões no Aspose.Words para Java
linktitle: Usando revisões
second_title: API de processamento de documentos Java Aspose.Words
description: Aprenda a usar o Aspose.Words para revisão do Java de forma eficiente. Guia passo a passo para desenvolvedores. Otimize seu gerenciamento de documentos.
weight: 22
url: /pt/java/using-document-elements/using-revisions/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Usando revisões no Aspose.Words para Java


Se você é um desenvolvedor Java procurando trabalhar com documentos e precisa implementar controles de revisão, o Aspose.Words para Java fornece um poderoso conjunto de ferramentas para ajudar você a gerenciar revisões de forma eficaz. Neste tutorial, nós o guiaremos pelo uso da revisão no Aspose.Words para Java passo a passo. 

## 1. Introdução ao Aspose.Words para Java

Aspose.Words para Java é uma API Java robusta que permite que você crie, modifique e manipule documentos do Word sem a necessidade do Microsoft Word. É particularmente útil quando você precisa implementar revisão em seus documentos.

## 2. Configurando seu ambiente de desenvolvimento

Antes de mergulharmos no uso do Aspose.Words para Java, você precisa configurar seu ambiente de desenvolvimento. Certifique-se de ter as ferramentas de desenvolvimento Java necessárias e a biblioteca Aspose.Words para Java instalada.

## 3. Criando um novo documento

Vamos começar criando um novo documento do Word usando Aspose.Words para Java. Veja como você pode fazer isso:

```java
string outPath = "Your Output Directory";
Document doc = new Document();
Body body = doc.getFirstSection().getBody();
Paragraph para = body.getFirstParagraph();
```

## 4. Adicionando conteúdo ao documento

Agora que você tem um documento em branco, você pode adicionar conteúdo a ele. Neste exemplo, adicionaremos três parágrafos:

```java
para.appendChild(new Run(doc, "Paragraph 1. "));
body.appendParagraph("Paragraph 2. ");
body.appendParagraph("Paragraph 3. ");
```

## 5. Iniciando o Rastreamento de Revisão

Para rastrear revisões em seu documento, você pode usar o seguinte código:

```java
doc.startTrackRevisions("John Doe", new Date());
```

## 6. Fazendo revisões

Vamos fazer uma revisão adicionando outro parágrafo:

```java
para = body.appendParagraph("Paragraph 4. ");
```

## 7. Aceitando e rejeitando revisões

Você pode aceitar ou rejeitar revisões em seu documento usando o Aspose.Words para Java. As revisões podem ser facilmente gerenciadas no Microsoft Word após o documento ser gerado.

## 8. Parando o Rastreamento de Revisões

Para parar de rastrear revisões, use o seguinte código:

```java
doc.stopTrackRevisions();
```

## 9. Salvando o documento

Por fim, salve seu documento:

```java
doc.save(outPath + "WorkingWithRevisions.AcceptRevisions.docx");
```

## 10. Conclusão

Neste tutorial, cobrimos os conceitos básicos de uso de revisão no Aspose.Words para Java. Você aprendeu como criar um documento, adicionar conteúdo, iniciar e parar o rastreamento de revisão e salvar seu documento.

Agora você tem as ferramentas necessárias para gerenciar efetivamente as revisões em seus aplicativos Java usando o Aspose.Words para Java.

## Código fonte completo
```java
string outPath = "Your Output Directory";
Document doc = new Document();
Body body = doc.getFirstSection().getBody();
Paragraph para = body.getFirstParagraph();
// Adicione texto ao primeiro parágrafo e depois adicione mais dois parágrafos.
para.appendChild(new Run(doc, "Paragraph 1. "));
body.appendParagraph("Paragraph 2. ");
body.appendParagraph("Paragraph 3. ");
// Temos três parágrafos, nenhum dos quais registrado como qualquer tipo de revisão
// Se adicionarmos/removermos qualquer conteúdo no documento durante o rastreamento de revisões,
// elas serão exibidas como tal no documento e podem ser aceitas/rejeitadas.
doc.startTrackRevisions("John Doe", new Date());
// Este parágrafo é uma revisão e terá o sinalizador "IsInsertRevision" correspondente definido.
para = body.appendParagraph("Paragraph 4. ");
Assert.assertTrue(para.isInsertRevision());
// Obtenha a coleção de parágrafos do documento e remova um parágrafo.
ParagraphCollection paragraphs = body.getParagraphs();
Assert.assertEquals(4, paragraphs.getCount());
para = paragraphs.get(2);
para.remove();
// Como estamos rastreando revisões, o parágrafo ainda existe no documento e terá o conjunto "IsDeleteRevision"
// e será exibido como uma revisão no Microsoft Word, até que aceitemos ou rejeitemos todas as revisões.
Assert.assertEquals(4, paragraphs.getCount());
Assert.assertTrue(para.isDeleteRevision());
// O parágrafo de revisão de exclusão será removido quando aceitarmos as alterações.
doc.acceptAllRevisions();
Assert.assertEquals(3, paragraphs.getCount());
Assert.assertEquals(para.getRuns().getCount(), 0); //era Is.Empty
// Interromper o rastreamento de revisões faz com que este texto apareça como texto normal.
//As revisões não são contadas quando o documento é alterado.
doc.stopTrackRevisions();
// Salve o documento.
doc.save(outPath + "WorkingWithRevisions.AcceptRevisions.docx");
  
```

## Perguntas frequentes

### 1. Posso usar o Aspose.Words para Java com outras linguagens de programação?

Não, o Aspose.Words para Java foi projetado especificamente para desenvolvimento Java.

### 2. O Aspose.Words para Java é compatível com todas as versões do Microsoft Word?

Sim, o Aspose.Words para Java foi projetado para ser compatível com várias versões do Microsoft Word.

### 3. Posso rastrear revisões em documentos do Word existentes?

Sim, você pode usar o Aspose.Words para Java para rastrear revisões em documentos existentes do Word.

### 4. Há algum requisito de licenciamento para usar o Aspose.Words para Java?

 Sim, você precisará adquirir uma licença para usar o Aspose.Words para Java em seus projetos. Você pode[tenha acesso a uma licença aqui](https://purchase.aspose.com/buy).

### 5. Onde posso encontrar suporte para Aspose.Words para Java?

 Para quaisquer dúvidas ou problemas, você pode visitar o[Fórum de suporte Aspose.Words para Java](https://forum.aspose.com/).

Comece a usar o Aspose.Words para Java hoje mesmo e simplifique seus processos de gerenciamento de documentos.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
