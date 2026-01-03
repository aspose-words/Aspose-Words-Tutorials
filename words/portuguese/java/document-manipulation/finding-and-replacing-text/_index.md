---
date: 2026-01-03
description: Aprenda a substituir texto por HTML em documentos Word usando Aspose.Words
  para Java. Guia passo a passo com exemplos de código, dicas de substituição de texto
  com regex em Java e muito mais.
linktitle: Finding and Replacing Text
second_title: Aspose.Words Java Document Processing API
title: substituir texto por HTML usando Aspose.Words para Java
url: /pt/java/document-manipulation/finding-and-replacing-text/
weight: 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# substituir texto por html no Aspose.Words para Java

## Introdução à Busca e Substituição de Texto no Aspose.Words para Java

Aspose.Words for Java é uma poderosa API Java que permite manipular documentos Word programaticamente. Uma das tarefas mais comuns é **replace text with html**, seja atualizando marcadores em um modelo, inserindo conteúdo formatado ou realizando transformações em massa de texto. Neste guia, vamos percorrer como substituir texto, como usar regex replace text java e até como substituir texto em cabeçalhos — tudo mantendo seu código limpo e eficiente.

## Respostas Rápidas
- **Qual é o método principal para replace text with html?** Use `FindReplaceOptions` com um callback personalizado como `ReplaceWithHtmlEvaluator`.  
- **Posso ignorar campos ao substituir?** Sim – defina `options.setIgnoreFields(true)`.  
- **Preciso de uma licença para uso em produção?** Uma licença válida do Aspose.Words é necessária para implantações comerciais.  
- **Qual versão do Java é suportada?** Aspose.Words para Java funciona com Java 8 ou superior.  
- **O regex replace text java é suportado?** Absolutamente – passe um objeto `Pattern` para o método `replace`.

## O que é “replace text with html”?

Substituir texto por HTML significa trocar um placeholder de texto simples por marcação HTML rica (tabelas, listas, estilos) enquanto preserva a estrutura do documento Word ao redor. Aspose.Words analisa o HTML e insere os objetos Word correspondentes, oferecendo controle total sobre o layout final.

## Por que usar Aspose.Words para esta tarefa?

- **Fidelidade total ao Word** – a biblioteca mantém toda a formatação, cabeçalhos, rodapés e alterações rastreadas intactas.  
- **Suporte interno a regex** – perfeito para padrões de busca complexos (`regex replace text java`).  
- **Controle granular** – opções como `IgnoreFields`, `IgnoreDeleted` e `UseLegacyOrder` permitem adaptar a operação às suas necessidades exatas.  
- **Multiplataforma** – funciona em qualquer SO que execute Java.

## Pré-requisitos

- Ambiente de Desenvolvimento Java (JDK 8+)  
- Biblioteca Aspose.Words para Java – faça o download em [here](https://releases.aspose.com/words/java/).  
- Um documento Word de exemplo (`.docx`) para experimentar.

## Encontrando e Substituindo Texto Simples

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a DocumentBuilder
DocumentBuilder builder = new DocumentBuilder(doc);

// Find and replace text
builder.getRange().replace("old-text", "new-text", new FindReplaceOptions());

// Save the modified document
doc.save("modified-document.docx");
```

Este exemplo básico demonstra **como replace text** usando o método `replace`. É a base para cenários mais avançados.

## Usando Expressões Regulares (regex replace text java)

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a DocumentBuilder
DocumentBuilder builder = new DocumentBuilder(doc);

// Use regular expressions for finding and replacing text
Pattern regex = Pattern.compile("your-pattern");
builder.getRange().replace(regex, "replacement-text", new FindReplaceOptions());

// Save the modified document
doc.save("modified-document.docx");
```

Expressões regulares fornecem correspondência de padrões poderosa, ideal para placeholders dinâmicos ou limites de palavras complexos.

## Ignorando Texto Dentro de Campos (aspose words replace text)

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance and set IgnoreFields to true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreFields(true);

// Use options when replacing text
doc.getRange().replace("text-to-replace", "new-text", options);

// Save the modified document
doc.save("modified-document.docx");
```

Defina `IgnoreFields` para manter campos de mesclagem, números de página ou outros códigos de campo intactos enquanto substitui o conteúdo ao redor.

## Ignorando Texto Dentro de Revisões de Exclusão

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance and set IgnoreDeleted to true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreDeleted(true);

// Use options when replacing text
doc.getRange().replace("text-to-replace", "new-text", options);

// Save the modified document
doc.save("modified-document.docx");
```

Isso impede que texto marcado para exclusão (alterações rastreadas) seja alterado.

## Ignorando Texto Dentro de Revisões de Inserção

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance and set IgnoreInserted to true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreInserted(true);

// Use options when replacing text
doc.getRange().replace("text-to-replace", "new-text", options);

// Save the modified document
doc.save("modified-document.docx");
```

Útil quando você deseja manter o texto recém‑inserido intacto durante uma substituição em massa.

## Substituindo Texto por HTML

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance with a custom replacing callback
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceWithHtmlEvaluator(options));

// Use options when replacing text
doc.getRange().replace("text-to-replace", "new-html-content", options);

// Save the modified document
doc.save("modified-document.docx");
```

Aqui nós **replace text with html** fornecendo um avaliador personalizado que analisa a string HTML e insere os nós Word apropriados.

## Substituindo Texto em Cabeçalhos e Rodapés (replace text in headers)

```java
// Load the document
Document doc = new Document("your-document.docx");

// Get the collection of headers and footers
HeaderFooterCollection headersFooters = doc.getFirstSection().getHeadersFooters();

// Choose the header or footer type you want to replace text in (e.g., HeaderFooterType.FOOTER_PRIMARY)
HeaderFooter footer = headersFooters.getByHeaderFooterType(HeaderFooterType.FOOTER_PRIMARY);

// Create a FindReplaceOptions instance and apply it to the footer's range
FindReplaceOptions options = new FindReplaceOptions();
footer.getRange().replace("text-to-replace", "new-text", options);

// Save the modified document
doc.save("modified-document.docx");
```

A substituição direcionada em cabeçalhos ou rodapés garante que a identidade visual do documento permaneça consistente.

## Exibindo Alterações nas Ordens de Cabeçalhos e Rodapés

```java
// Load the document
Document doc = new Document("your-document.docx");

// Get the first section
Section firstPageSection = doc.getFirstSection();

// Create a FindReplaceOptions instance and apply it to the document's range
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceLog());

// Replace text that affects header and footer orders
doc.getRange().replace(Pattern.compile("(header|footer)"), "", options);

// Save the modified document
doc.save("modified-document.docx");
```

Este exemplo registra alterações, ajudando a auditar modificações na ordem de cabeçalhos/rodapés.

## Substituindo Texto por Campos

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance and set a custom replacing callback for fields
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceTextWithFieldHandler(FieldType.FIELD_MERGE_FIELD));

// Use options when replacing text
doc.getRange().replace(Pattern.compile("PlaceHolder(\\d+)"), "", options);

// Save the modified document
doc.save("modified-document.docx");
```

Injetar campos (por exemplo, campos de mesclagem) permite criar documentos dinâmicos que podem ser preenchidos posteriormente.

## Substituindo com um Avaliador

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance and set a custom replacing callback
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new MyReplaceEvaluator());

// Use options when replacing text
doc.getRange().replace(Pattern.compile("[s|m]ad"), "", options);

// Save the modified document
doc.save("modified-document.docx");
```

Avaliadores personalizados dão controle programático total sobre o texto de substituição.

## Substituindo com Regex (regex replace text java)

```java
// Load the document
Document doc = new Document("your-document.docx");

// Use regular expressions for finding and replacing text
doc.getRange().replace(Pattern.compile("[s|m]ad"), "bad", new FindReplaceOptions());

// Save the modified document
doc.save("modified-document.docx");
```

Uma forma concisa de executar substituições baseadas em padrões em todo o documento.

## Reconhecendo e Substituições Dentro de Padrões de Substituição

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance with UseSubstitutions set to true
FindReplaceOptions options = new FindReplaceOptions();
options.setUseSubstitutions(true);

// Use options when replacing text with a pattern
doc.getRange().replace(Pattern.compile("([A-z]+) give money to ([A-z]+)"), "$2 take money from $1", options);

// Save the modified document
doc.save("modified-document.docx");
```

Habilite `UseSubstitutions` para referenciar grupos de captura diretamente na string de substituição.

## Substituindo com uma String (replace text word java)

```java
// Load the document
Document doc = new Document("your-document.docx");

// Replace text with a string
doc.getRange().replace("text-to-replace", "new-string", new FindReplaceOptions());

// Save the modified document
doc.save("modified-document.docx");
```

A forma mais simples de substituição — perfeita para placeholders estáticos.

## Usando Ordem Legada

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance and set UseLegacyOrder to true
FindReplaceOptions options = new FindReplaceOptions();
options.setUseLegacyOrder(true);

// Use options when replacing text
doc.getRange().replace(Pattern.compile("\\[(.*?)\\]"), "", options);

// Save the modified document
doc.save("modified-document.docx");
```

A ordem legada pode ser necessária ao lidar com documentos antigos que dependem da sequência de travessia original.

## Substituindo Texto em uma Tabela

```java
// Load the document
Document doc = new Document("your-document.docx");

// Get a specific table (e.g., the first table)
Table table = (Table) doc.getChild(NodeType.TABLE, 0, true);

// Use FindReplaceOptions for replacing text in the table
table.getRange().replace("old-text", "new-text", new FindReplaceOptions());

// Save the modified document
doc.save("modified-document.docx");
```

Substituições direcionadas dentro de tabelas evitam alterações indesejadas em outras partes do documento.

## Problemas Comuns e Soluções

- **HTML não está renderizando corretamente** – Certifique-se de que seu HTML esteja bem‑formado e inclua tags necessárias (por exemplo, `<p>`, `<table>`).  
- **Regex não corresponde** – Lembre‑se de escapar caracteres especiais e usar `Pattern.CASE_INSENSITIVE` se necessário.  
- **Campos sendo substituídos inadvertidamente** – Defina `options.setIgnoreFields(true)` para protegê‑los.  
- **Desempenho em documentos grandes** – Use `UseLegacyOrder` ou processe seções individualmente para reduzir o consumo de memória.

## Perguntas Frequentes

**Q: Como faço o download do Aspose.Words para Java?**  
A: Você pode baixar o Aspose.Words para Java no site visitando [this link](https://releases.aspose.com/words/java/).

**Q: Posso usar expressões regulares para substituição de texto?**  
A: Sim, você pode usar expressões regulares para substituição de texto no Aspose.Words para Java. Isso permite executar operações de busca e substituição mais avançadas e flexíveis.

**Q: Como posso ignorar texto dentro de campos durante a substituição?**  
A: Defina a propriedade `IgnoreFields` de `FindReplaceOptions` como `true`. Isso exclui o conteúdo de campos, como campos de mesclagem, de ser substituído.

**Q: É possível substituir texto dentro de cabeçalhos e rodapés?**  
A: Absolutamente. Acesse o cabeçalho ou rodapé desejado via `HeaderFooterCollection` e aplique o método `replace` com as opções apropriadas.

**Q: O que a opção `UseLegacyOrder` faz?**  
A: `UseLegacyOrder` força o mecanismo de busca/substituição a percorrer os nós na ordem original usada por versões mais antigas do Aspose.Words, o que pode ser útil para compatibilidade com documentos legados.

---

**Última Atualização:** 2026-01-03  
**Testado com:** Aspose.Words for Java 24.12  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}