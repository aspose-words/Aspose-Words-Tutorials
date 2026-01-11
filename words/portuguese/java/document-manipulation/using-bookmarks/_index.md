---
date: 2026-01-11
description: Aprenda como exibir e ocultar marcadores e criar marcadores Java usando
  Aspose.Words para Java para navegação e manipulação eficientes de documentos.
linktitle: Using Bookmarks
second_title: Aspose.Words Java Document Processing API
title: Mostrar/Ocultar Marcadores com Aspose.Words para Java
url: /pt/java/document-manipulation/using-bookmarks/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Exibir/Ocultar Marcadores com Aspose.Words para Java

## Introdução ao Uso de Marcadores no Aspose.Words para Java

Marcadores são um recurso poderoso no Aspose.Words para Java que permite **create bookmark java**, navegar para conteúdo específico e até **show hide bookmarks** quando você precisa gerar diferentes versões de documentos. Neste guia passo a passo, percorreremos a criação, acesso, atualização, cópia e alternância da visibilidade dos marcadores, proporcionando controle total sobre a manipulação de documentos.

## Respostas Rápidas
- **Qual é o objetivo principal dos marcadores?** Marcar e posteriormente recuperar partes específicas de um documento.  
- **Posso ocultar os marcadores de bookmark na saída final?** Sim—use a API show/hide para alternar sua visibilidade.  
- **Como criar um marcador dentro de uma célula de tabela?** Inicie e finalize o marcador com `DocumentBuilder` enquanto o cursor está dentro da célula.  
- **É possível copiar texto marcado para outro documento?** Absolutamente—use `NodeImporter` para preservar a formatação.  
- **Qual versão do Aspose.Words é necessária?** Qualquer versão recente; o código funciona com a última compilação de 2026.

## O que é “show hide bookmarks”?

O recurso **show hide bookmarks** permite exibir ou ocultar programaticamente os delimitadores de marcadores no documento salvo. Isso é útil quando você deseja gerar uma saída limpa para os usuários finais, mantendo os dados de marcadores para processamento interno.

## Por que usar marcadores na automação de documentos Java?

- **Navegação eficiente** – Vá diretamente para as seções sem percorrer todo o arquivo.  
- **Geração dinâmica de conteúdo** – Insira, substitua ou remova texto vinculado a um marcador.  
- **Visibilidade condicional** – Exiba ou oculte marcadores com base nas preferências do usuário ou no formato de saída.  
- **Reutilização** – Copie fragmentos marcados entre documentos preservando estilos.

## Pré‑requisitos
- Java Development Kit (JDK) 8 ou superior.  
- Biblioteca Aspose.Words para Java adicionada ao seu projeto (Maven/Gradle ou JAR).  
- Familiaridade básica com as classes `Document` e `DocumentBuilder`.

## Guia Passo a Passo

### Passo 1: Criar um Marcador (create bookmark java)

Para adicionar um marcador, você o inicia, escreve o conteúdo e, em seguida, finaliza. Este exemplo cria um marcador simples chamado **My Bookmark**.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Start the bookmark
builder.startBookmark("My Bookmark");
builder.writeln("Text inside a bookmark.");

// End the bookmark
builder.endBookmark("My Bookmark");
```

### Passo 2: Acessar Marcadores (access bookmarks java)

Marcadores podem ser recuperados tanto por seu índice baseado em zero quanto por nome. O código abaixo demonstra ambas as abordagens.

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");

// By index:
Bookmark bookmark1 = doc.getRange().getBookmarks().get(0);

// By name:
Bookmark bookmark2 = doc.getRange().getBookmarks().get("MyBookmark3");
```

### Passo 3: Atualizar Dados do Marcador (update bookmark text)

Você pode renomear um marcador ou substituir seu conteúdo de texto. Isso é útil quando o documento subjacente é alterado.

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");
Bookmark bookmark = doc.getRange().getBookmarks().get("MyBookmark1");
String name = bookmark.getName();
String text = bookmark.getText();
bookmark.setName("RenamedBookmark");
bookmark.setText("This is new bookmarked text.");
```

### Passo 4: Trabalhar com Texto Marcado (copy bookmarked text)

Copiar um fragmento marcado para outro documento mantendo a formatação original é simples com `NodeImporter`.

```java
Document srcDoc = new Document("Your Directory Path" + "Bookmarks.docx");
Bookmark srcBookmark = srcDoc.getRange().getBookmarks().get("MyBookmark1");
Document dstDoc = new Document();
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
appendBookmarkedText(importer, srcBookmark, dstDoc.getLastSection().getBody());
dstDoc.save("Your Directory Path" + "WorkingWithBookmarks.CopyBookmarkedText.docx");
```

### Passo 5: Exibir e Ocultar Marcadores (show hide bookmarks)

O trecho a seguir demonstra como ocultar os marcadores de um bookmark no arquivo salvo. Passe `false` para ocultar, `true` para exibir.

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");
showHideBookmarkedContent(doc, "MyBookmark1", false);
doc.save("Your Directory Path" + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

### Passo 6: Desembaraçar Marcadores de Linha (bookmark table cell)

Quando marcadores abrangem linhas de tabela, podem ficar embaralhados. Os métodos utilitários abaixo desembaraçam‑nos e permitem excluir uma linha específica pelo seu marcador.

```java
Document doc = new Document("Your Directory Path" + "Table column bookmarks.docx");
untangle(doc);
deleteRowByBookmark(doc, "ROW2");
doc.save("Your Directory Path" + "WorkingWithBookmarks.UntangleRowBookmarks.docx");
```

## Problemas Comuns e Soluções

| Problema | Solução |
|----------|----------|
| **Bookmark not found** | Verifique se o nome do marcador corresponde exatamente (sensível a maiúsculas/minúsculas) e se o documento foi salvo após a criação. |
| **Copied text loses formatting** | Use `ImportFormatMode.KEEP_SOURCE_FORMATTING` com `NodeImporter` como mostrado no Passo 4. |
| **Show/hide does not affect output** | Certifique‑se de chamar `showHideBookmarkedContent` **antes** de salvar o documento. |
| **Bookmark inside a table cell is ignored** | Coloque as chamadas start/end enquanto o cursor do builder está dentro da célula alvo. |

## Perguntas Frequentes

**Q: Como crio um marcador em uma célula de tabela?**  
A: Use `DocumentBuilder` para mover o cursor para a célula desejada, então chame `startBookmark` e `endBookmark` ao redor do conteúdo da célula.

**Q: Posso copiar um marcador para outro documento?**  
A: Sim—use a classe `NodeImporter` (veja o Passo 4) para importar o nó marcado preservando sua formatação original.

**Q: Como posso excluir uma linha pelo seu marcador?**  
A: Primeiro localize a linha que contém o marcador, então chame `remove` no nó da linha (conforme demonstrado no Passo 6).

**Q: Quais são alguns casos de uso comuns para marcadores?**  
A: Gerar um índice, extrair seções específicas para relatórios e automatizar a montagem de documentos com base nas seleções do usuário.

**Q: Onde posso encontrar mais informações sobre Aspose.Words para Java?**  
A: Para documentação detalhada e downloads, visite [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/).

---

**Última atualização:** 2026-01-11  
**Testado com:** Aspose.Words for Java 24.11 (2026)  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}