---
date: 2025-12-27
description: Aprenda a definir a direção, carregar arquivos txt, remover espaços e
  converter txt para docx usando Aspose.Words para Java.
linktitle: Loading Text Files with
second_title: Aspose.Words Java Document Processing API
title: Como definir a direção e carregar arquivos de texto com Aspose.Words para Java
url: /pt/java/document-loading-and-saving/loading-text-files/
weight: 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Como Definir Direção e Carregar Arquivos de Texto com Aspose.Words para Java

## Introdução ao Carregamento de Arquivos de Texto com Aspose.Words para Java

Neste guia, você descobrirá **como definir a direção** ao carregar documentos de texto simples e verá maneiras práticas de **carregar txt**, **remover espaços** e **converter txt para docx** usando Aspose.Words para Java. Seja você quem está construindo um serviço de conversão de documentos ou precisa de controle detalhado sobre a detecção de listas, este tutorial o conduz passo a passo com explicações claras e código pronto‑para‑executar.

## Respostas Rápidas
- **Como definir a direção do texto para um arquivo TXT carregado?** Use `TxtLoadOptions.setDocumentDirection(DocumentDirection.AUTO)` ou especifique `LEFT_TO_RIGHT` / `RIGHT_TO_LEFT`.
- **O Aspose.Words pode detectar listas numeradas em texto simples?** Sim – habilite `DetectNumberingWithWhitespaces` em `TxtLoadOptions`.
- **Como remover espaços iniciais e finais?** Defina `TxtLeadingSpacesOptions.TRIM` e `TxtTrailingSpacesOptions.TRIM`.
- **É possível converter um arquivo TXT para DOCX em uma única linha?** Carregue o TXT com `TxtLoadOptions` e chame `Document.save("output.docx")`.
- **Qual versão do Java é necessária?** Java 8+ é suficiente para Aspose.Words 24.x.

## O que é “definir direção” no Aspose.Words?
Quando um arquivo de texto contém scripts da direita‑para‑esquerda (por exemplo, hebraico ou árabe), a biblioteca precisa saber a ordem de leitura. O enum `DocumentDirection` permite **definir a direção** manualmente ou deixar o Aspose detectá‑la automaticamente, garantindo layout correto e formatação bidi.

## Por que usar Aspose.Words para carregar arquivos TXT?
- **Detecção precisa de listas** – lida com listas numeradas, com marcadores e delimitadas por espaços.
- **Manipulação granular de espaços** – remove ou preserva espaços iniciais/finais.
- **Detecção automática de direção de texto** – ideal para documentos multilíngues.
- **Conversão em um passo** – carregue um `.txt` e salve como `.docx`, `.pdf` ou qualquer formato suportado.

## Pré‑requisitos
- Java 8 ou superior.
- Biblioteca Aspose.Words para Java (adicione a dependência Maven/Gradle ou o JAR ao seu projeto).
- Conhecimento básico de streams de I/O em Java.

## Guia Passo a Passo

### Etapa 1: Detectando Listas (como carregar txt)
Para carregar um documento de texto e detectar listas automaticamente, crie uma instância de `TxtLoadOptions` e habilite a detecção de listas. O código abaixo mostra vários estilos de lista e habilita a numeração sensível a espaços em branco.

```java
// Create a plaintext document in the form of a string with parts that may be interpreted as lists.
// Upon loading, the first three lists will always be detected by Aspose.Words,
// and List objects will be created for them after loading.
final String TEXT_DOC = "Full stop delimiters:\n" +
        "1. First list item 1\n" +
        "2. First list item 2\n" +
        "3. First list item 3\n\n" +
        "Right bracket delimiters:\n" +
        "1) Second list item 1\n" +
        "2) Second list item 2\n" +
        "3) Second list item 3\n\n" +
        "Bullet delimiters:\n" +
        "• Third list item 1\n" +
        "• Third list item 2\n" +
        "• Third list item 3\n\n" +
        "Whitespace delimiters:\n" +
        "1 Fourth list item 1\n" +
        "2 Fourth list item 2\n" +
        "3 Fourth list item 3";
// The fourth list, with whitespace in between the list number and list item contents,
// will only be detected as a list if "DetectNumberingWithWhitespaces" in a LoadOptions object is set to true,
// to avoid paragraphs that start with numbers being mistakenly detected as lists.
TxtLoadOptions loadOptions = new TxtLoadOptions();
{
    loadOptions.setDetectNumberingWithWhitespaces(true);
}
// Load the document while applying LoadOptions as a parameter and verify the result.
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

> **Dica de especialista:** Se você precisar apenas da detecção básica de listas, pode pular a opção de espaços em branco – o Aspose ainda reconhecerá os padrões padrão `1.` e `1)`.

### Etapa 2: Opções de Manipulação de Espaços (como remover espaços)
Espaços iniciais e finais costumam causar falhas de formatação. Use `TxtLeadingSpacesOptions` e `TxtTrailingSpacesOptions` para controlar esse comportamento.

```java
@Test
public void handleSpacesOptions() throws Exception {
    final String TEXT_DOC = "      Line 1 \n" +
            "    Line 2   \n" +
            " Line 3       ";
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    {
        loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
        loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);
    }
    Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
    doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.HandleSpacesOptions.docx");
}
```

> **Por que isso importa:** Remover espaços evita indentação indesejada no DOCX resultante, deixando o documento limpo sem necessidade de pós‑processamento manual.

### Etapa 3: Controlando a Direção do Texto (como definir direção)
Para idiomas da direita‑para‑esquerda, defina a direção do documento antes de carregar. O exemplo abaixo carrega um arquivo de texto em hebraico e imprime a bandeira bidi para confirmar a direção.

```java
@Test
public void documentTextDirection() throws Exception {
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    {
        loadOptions.setDocumentDirection(DocumentDirection.AUTO);
    }
    Document doc = new Document("Your Directory Path" + "Hebrew text.txt", loadOptions);
    Paragraph paragraph = doc.getFirstSection().getBody().getFirstParagraph();
    System.out.println(paragraph.getParagraphFormat().getBidi());
    doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
}
```

> **Armadilha comum:** Esquecer de definir `DocumentDirection` pode gerar texto árabe/hebraico embaralhado, onde os caracteres aparecem na ordem errada.

### Código‑Fonte Completo para Carregar Arquivos de Texto com Aspose.Words para Java
A seguir está o código completo, pronto‑para‑executar, que combina detecção de listas, manipulação de espaços e controle de direção. Você pode copiar‑colar em uma única classe e executar os três métodos de teste individualmente.

```java
public void detectNumberingWithWhitespaces() throws Exception {
	// Create a plaintext document in the form of a string with parts that may be interpreted as lists.
	// Upon loading, the first three lists will always be detected by Aspose.Words,
	// and List objects will be created for them after loading.
	final String TEXT_DOC = "Full stop delimiters:\n" +
			"1. First list item 1\n" +
			"2. First list item 2\n" +
			"3. First list item 3\n\n" +
			"Right bracket delimiters:\n" +
			"1) Second list item 1\n" +
			"2) Second list item 2\n" +
			"3) Second list item 3\n\n" +
			"Bullet delimiters:\n" +
			"• Third list item 1\n" +
			"• Third list item 2\n" +
			"• Third list item 3\n\n" +
			"Whitespace delimiters:\n" +
			"1 Fourth list item 1\n" +
			"2 Fourth list item 2\n" +
			"3 Fourth list item 3";
	// The fourth list, with whitespace inbetween the list number and list item contents,
	// will only be detected as a list if "DetectNumberingWithWhitespaces" in a LoadOptions object is set to true,
	// to avoid paragraphs that start with numbers being mistakenly detected as lists.
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDetectNumberingWithWhitespaces(true);
	}
	// Load the document while applying LoadOptions as a parameter and verify the result.
	Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
}
@Test
public void handleSpacesOptions() throws Exception {
	final String TEXT_DOC = "      Line 1 \n" +
			"    Line 2   \n" +
			" Line 3       ";
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
		loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);
	}
	Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.HandleSpacesOptions.docx");
}
@Test
public void documentTextDirection() throws Exception {
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDocumentDirection(DocumentDirection.AUTO);
	}
	Document doc = new Document("Your Directory Path" + "Hebrew text.txt", loadOptions);
	Paragraph paragraph = doc.getFirstSection().getBody().getFirstParagraph();
	System.out.println(paragraph.getParagraphFormat().getBidi());
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
	}
```

## Problemas Comuns e Soluções
| Problema | Causa | Solução |
|----------|-------|----------|
| Listas não detectadas | `DetectNumberingWithWhitespaces` deixado `false` para listas delimitadas por espaços | Habilite `loadOptions.setDetectNumberingWithWhitespaces(true)` |
| Indentação extra após o carregamento | Espaços iniciais foram preservados | Defina `TxtLeadingSpacesOptions.TRIM` |
| Texto em hebraico aparece invertido | Direção do documento não definida ou definida como `LEFT_TO_RIGHT` | Use `DocumentDirection.AUTO` ou `RIGHT_TO_LEFT` |
| DOCX de saída está vazio | Fluxo de entrada não foi reiniciado antes do segundo carregamento | Recrie `ByteArrayInputStream` para cada chamada de carregamento |

## Perguntas Frequentes

### Q: O que é Aspose.Words para Java?
A: Aspose.Words para Java é uma biblioteca poderosa de processamento de documentos que permite aos desenvolvedores criar, manipular e converter documentos Word programaticamente em aplicações Java. Ela suporta uma ampla gama de recursos, desde o simples carregamento de texto até formatação complexa e conversão.

### Q: Como posso começar a usar Aspose.Words para Java?
A: 1. Baixe e instale a biblioteca Aspose.Words para Java. 2. Consulte a documentação em [Aspose.Words for Java API Reference](https://reference.aspose.com/words/java/) para informações detalhadas e exemplos. 3. Explore o código de exemplo e tutoriais para aprender a usar a biblioteca de forma eficaz.

### Q: Como faço para carregar um documento de texto usando Aspose.Words para Java?
A: Use a classe `TxtLoadOptions` junto com o construtor `Document`. Especifique opções como detecção de listas, manipulação de espaços ou direção do texto conforme demonstrado nas seções passo a passo acima.

### Q: Posso converter um documento de texto carregado para outros formatos?
A: Sim. Após carregar o arquivo TXT em um objeto `Document`, chame `doc.save("output.pdf")`, `doc.save("output.docx")` ou qualquer outro formato suportado.

### Q: Como manipulo espaços em documentos de texto carregados?
A: Controle os espaços iniciais e finais com `TxtLeadingSpacesOptions` e `TxtTrailingSpacesOptions`. Defina‑os como `TRIM` para remover espaços indesejados ou como `PRESERVE` se precisar manter a formatação original.

### Q: Qual a importância da direção do texto no Aspose.Words para Java?
A: A direção do texto garante a renderização correta de scripts da direita‑para‑esquerda (hebraico, árabe, etc.). Ao definir `DocumentDirection`, você assegura que o texto bidi seja exibido adequadamente no documento resultante.

### Q: Onde encontro mais recursos e suporte para Aspose.Words para Java?
A: Visite a [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/) para referências de API, exemplos de código e guias detalhados. Você também pode participar dos fóruns da comunidade Aspose ou contatar o suporte da Aspose para perguntas específicas.

### Q: O Aspose.Words para Java é adequado para projetos comerciais?
A: Sim. Ele oferece opções de licenciamento tanto para uso pessoal quanto comercial. Revise os termos de licenciamento no site da Aspose para escolher o plano adequado ao seu projeto.

## Conclusão
Você agora tem um conjunto completo de ferramentas para **carregar arquivos txt**, **detectar listas**, **remover espaços** e **definir direção** ao converter texto simples em documentos Word ricos com Aspose.Words para Java. Aplique esses padrões para automatizar fluxos de trabalho de documentos, melhorar o suporte multilíngue e garantir uma saída limpa e profissional a cada vez.

---

**Last Updated:** 2025-12-27  
**Tested With:** Aspose.Words for Java 24.12  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}