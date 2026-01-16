---
date: 2026-01-16
description: Aprenda a converter polegadas em pontos, ler metadados de documentos
  em Java, adicionar propriedades personalizadas em Java e definir margens de página
  em Java com Aspose.Words para Java.
linktitle: Using Document Properties
second_title: Aspose.Words Java Document Processing API
title: Converter polegadas em pontos – Usando propriedades de documento no Aspose.Words
  para Java
url: /pt/java/document-manipulation/using-document-properties/
weight: 32
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Converter Polegadas em Pontos – Usando Propriedades de Documento no Aspose.Words para Java

Neste tutorial você descobrirá como **converter polegadas em pontos** ao definir margens de página, ler metadados de documento Java, adicionar propriedades personalizadas Java e trabalhar com propriedades de documento integradas usando o Aspose.Words para Java. Seja gerando relatórios, faturas ou documentos legais, dominar essas técnicas oferece controle detalhado sobre a aparência e os metadados dos seus arquivos Word.

## Respostas Rápidas
- **Como converto polegadas em pontos?** Use `ConvertUtil.inchToPoint(value)` do Aspose.Words.
- **Posso ler metadados de documento em Java?** Sim – chame `doc.getBuiltInDocumentProperties()` ou `doc.getCustomDocumentProperties()`.
- **Como adiciono uma propriedade personalizada em Java?** Use `doc.getCustomDocumentProperties().add(name, value)`.
- **Qual método define margens de página em pontos?** `PageSetup.setTopMargin`, `setBottomMargin`, etc., aceitam valores em pontos.
- **É possível vincular a um marcador?** Sim – use `addLinkToContent` na coleção de propriedades personalizadas.

## Introdução às Propriedades de Documento

As propriedades de documento são uma parte vital de qualquer arquivo Word. Elas armazenam informações como título, autor, assunto, palavras‑chave e quaisquer metadados personalizados necessários para processamento posterior. No Aspose.Words para Java você pode manipular tanto propriedades integradas quanto personalizadas, e também controlar detalhes de layout como margens convertendo unidades de medida (por exemplo, **converter polegadas em pontos**).

## O que é “converter polegadas em pontos”?

No Word, as medidas de layout são expressas em pontos (1 ponto = 1/72 de polegada). Converter polegadas em pontos permite definir margens, recuos e espaçamentos usando unidades imperiais familiares enquanto a API trabalha internamente com pontos.

## Por que gerenciar metadados de documento em Java?

Incorporar metadados facilita a busca, categorização e automação de fluxos de trabalho. Por exemplo, você pode marcar um contrato com a flag “Authorized” ou armazenar um número de revisão para auditoria. Ler e gravar essas informações programaticamente garante consistência em grandes lotes de documentos.

## Pré‑requisitos
- Java 17+ (ou JDK compatível)
- Biblioteca Aspose.Words para Java adicionada ao seu projeto (Maven/Gradle)
- Um arquivo `.docx` de exemplo (por exemplo, `Properties.docx`) colocado em um diretório acessível

## Guia Passo a Passo

### Enumerando Propriedades de Documento Integradas
Abaixo está um teste simples que abre um documento e imprime todas as propriedades integradas, como Title, Author e Keywords.

```java
@Test
public void enumerateProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    System.out.println(MessageFormat.format("1. Document name: {0}", doc.getOriginalFileName()));
    System.out.println("2. Built-in Properties");
    for (DocumentProperty prop : doc.getBuiltInDocumentProperties())
        System.out.println(MessageFormat.format("{0} : {1}", prop.getName(), prop.getValue()));
}
```

> **Dica profissional:** Use este trecho para verificar se seus metadados foram gravados corretamente nas etapas anteriores.

### Adicionando Propriedades de Documento Personalizadas (add custom properties java)
Propriedades personalizadas permitem armazenar qualquer tipo de dado que você precisar — boolean, string, date, number, etc.

```java
@Test
public void addCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    CustomDocumentProperties customDocumentProperties = doc.getCustomDocumentProperties();

    if (customDocumentProperties.get("Authorized") != null) return;

    customDocumentProperties.add("Authorized", true);
    customDocumentProperties.add("Authorized By", "John Smith");
    customDocumentProperties.add("Authorized Date", new Date());
    customDocumentProperties.add("Authorized Revision", doc.getBuiltInDocumentProperties().getRevisionNumber());
    customDocumentProperties.add("Authorized Amount", 123.45);
}
```

> **Por que isso importa:** Adicionar uma flag como **Authorized** pode acionar fluxos de aprovação posteriores sem alterar o conteúdo do documento.

### Removendo uma Propriedade Personalizada
Se uma propriedade não for mais necessária, você pode excluí‑la de forma limpa.

```java
@Test
public void removeCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    doc.getCustomDocumentProperties().remove("Authorized Date");
}
```

### Configurando um Link para Conteúdo (bookmark linking)
Você pode criar um marcador e então adicionar uma propriedade personalizada que aponta para esse marcador, habilitando referências cruzadas dinâmicas.

```java
@Test
public void configuringLinkToContent() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.startBookmark("MyBookmark");
    builder.writeln("Text inside a bookmark.");
    builder.endBookmark("MyBookmark");

    CustomDocumentProperties customProperties = doc.getCustomDocumentProperties();

    // Add linked to content property.
    DocumentProperty customProperty = customProperties.addLinkToContent("Bookmark", "MyBookmark");
    customProperty = customProperties.get("Bookmark");
    boolean isLinkedToContent = customProperty.isLinkToContent();
    String linkSource = customProperty.getLinkSource();
    String customPropertyValue = customProperty.getValue().toString();
}
```

### Convertendo Entre Unidades de Medida (set page margins java)
É aqui que a palavra‑chave principal brilha. Definimos margens em polegadas e então **convertimos polegadas em pontos** usando `ConvertUtil`.

```java
@Test
public void convertBetweenMeasurementUnits() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    PageSetup pageSetup = builder.getPageSetup();

    // Set margins in inches.
    pageSetup.setTopMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setBottomMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setLeftMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setRightMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setHeaderDistance(ConvertUtil.inchToPoint(0.2));
    pageSetup.setFooterDistance(ConvertUtil.inchToPoint(0.2));
}
```

> **Observação:** `ConvertUtil` também fornece `pointToInch`, `mmToPoint`, etc., para um manuseio flexível de layout.

### Usando Caracteres de Controle (read document metadata java)
Caracteres de controle ajudam a limpar fluxos de texto. Este exemplo substitui um retorno de carro (`\r`) pela sequência de quebra de linha do Windows (`\r\n`).

```java
@Test
public void useControlCharacters()
{
    final String TEXT = "test\r";

    // Replace "\r" control character with "\r\n".
    String replace = TEXT.replace(ControlChar.CR, ControlChar.CR_LF);
}
```

## Problemas Comuns & Soluções
| Problema | Causa | Solução |
|----------|-------|---------|
| Margens ficam erradas após a conversão | Unidade incorreta (ex.: cm em vez de polegadas) | Verifique se você chama `ConvertUtil.inchToPoint` para valores em polegadas |
| Propriedade personalizada não aparece | Propriedade adicionada após salvar o documento | Chame `doc.save(...)` depois de adicionar as propriedades |
| Link de marcador quebrado | Erro de digitação no nome do marcador | Garanta que o nome do marcador corresponda exatamente em `addLinkToContent` |

## Perguntas Frequentes

### Como acesso as propriedades de documento integradas?

Para acessar as propriedades de documento integradas no Aspose.Words para Java, use o método `getBuiltInDocumentProperties` no objeto `Document`. Esse método devolve uma coleção de propriedades integradas que podem ser iteradas.

### Posso adicionar propriedades de documento personalizadas a um documento?

Sim, você pode adicionar propriedades de documento personalizadas usando a coleção `CustomDocumentProperties`. É possível definir propriedades personalizadas com vários tipos de dados, incluindo strings, booleans, dates e valores numéricos.

### Como removo uma propriedade de documento personalizada específica?

Para remover uma propriedade de documento personalizada específica, use o método `remove` na coleção `CustomDocumentProperties`, passando o nome da propriedade que deseja excluir como parâmetro.

### Qual é o objetivo de vincular a conteúdo dentro de um documento?

Vincular a conteúdo dentro de um documento permite criar referências dinâmicas para partes específicas do documento. Isso pode ser útil para criar documentos interativos ou referências cruzadas entre seções.

### Como converto entre diferentes unidades de medida no Aspose.Words para Java?

Você pode converter entre diferentes unidades de medida no Aspose.Words para Java usando a classe `ConvertUtil`. Ela fornece métodos para converter unidades como polegadas para pontos, pontos para centímetros e muito mais.

## Perguntas Frequentes (FAQ)

**Q: Como leio metadados de documento Java sem carregar todo o arquivo?**  
A: Use `DocumentInfo` para recuperar propriedades principais sem carregar completamente o conteúdo do documento.

**Q: Posso definir programaticamente margens de página Java para documentos existentes?**  
A: Sim — abra o documento, modifique as margens de `PageSetup` (converta polegadas em pontos se necessário) e salve.

**Q: É possível exportar propriedades personalizadas para metadados PDF?**  
A: Ao salvar em PDF, o Aspose.Words mapeia automaticamente propriedades de documento personalizadas para metadados personalizados do PDF.

**Q: Caracteres de controle afetam a conversão para PDF?**  
A: Eles são preservados durante a conversão; porém, pode ser desejável normalizar quebras de linha para consistência.

**Q: Qual versão do Aspose.Words é necessária para `ConvertUtil`?**  
A: `ConvertUtil` está disponível desde o Aspose.Words 16.5; qualquer versão recente o suporta.

## Conclusão

Ao dominar **converter polegadas em pontos**, ler metadados de documento Java e adicionar propriedades personalizadas Java, você obtém controle total tanto sobre o layout visual quanto sobre os dados ocultos dos seus arquivos Word. Essas capacidades permitem construir pipelines automatizados de documentos, garantir conformidade e criar relatórios ricamente formatados — tudo com o Aspose.Words para Java.

---

**Última atualização:** 2026-01-16  
**Testado com:** Aspose.Words para Java 24.11  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}