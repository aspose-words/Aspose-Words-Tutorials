---
date: 2026-01-16
description: Aprenda como destacar erros ortográficos no Word usando Aspose.Words
  para Java e descubra como definir caracteres por linha, personalizar opções de visualização
  e limpar estilos.
linktitle: Using Document Options and Settings
second_title: Aspose.Words Java Document Processing API
title: Destacar erros ortográficos no Word com Aspose.Words Java
url: /pt/java/document-manipulation/using-document-options-and-settings/
weight: 31
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Usando Opções e Configurações de Documento no Aspose.Words para Java

## Introdução ao Uso de Opções e Configurações de Documento no Aspose.Words para Java

Neste guia abrangente, você aprenderá **como destacar erros ortográficos no Word** usando Aspose.Words para Java, além de dominar configurações relacionadas, como opções de visualização, layout de página e limpeza de estilos. Seja você um desenvolvedor experiente ou esteja começando agora, os exemplos abaixo ajudarão a criar documentos robustos e conscientes de erros que funcionam em diferentes versões do Word.

## Respostas Rápidas
- **Como posso destacar erros ortográficos no Word?** Use `setShowSpellingErrors(true)` no objeto `Document`.  
- **Posso também mostrar erros gramaticais?** Sim—chame `setShowGrammaticalErrors(true)`.  
- **Qual método define caracteres por linha?** `getPageSetup().setCharactersPerLine(int)`.  
- **Qual API otimiza para uma versão específica do Word?** `doc.getCompatibilityOptions().optimizeFor(MsWordVersion)`.  
- **Existe uma maneira de limpar estilos não utilizados?** Use `CleanupOptions` com `setUnusedStyles(true)` e chame `doc.cleanup(options)`.

## Como destacar erros ortográficos no Word?

Aspose.Words torna simples ativar o destaque de erros ortográficos. Quando o documento é aberto no Microsoft Word, palavras com erros aparecem sublinhadas em vermelho, ajudando os usuários finais a identificar problemas instantaneamente.

## Como definir caracteres por linha

Controlar o número de caracteres por linha é essencial para layouts de largura fixa (por exemplo, listagens de código ou formulários legados). A classe `PageSetup` fornece `setCharactersPerLine(int)`, que permite definir esse valor com precisão.

## Como mostrar erros gramaticais

Além da ortografia, você também pode habilitar a exibição de erros gramaticais. Isso é útil ao redigir conteúdo que deve seguir guias de estilo ou ao criar ferramentas de revisão.

## Otimizando Documentos para Compatibilidade

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.OptimizeForMsWord.docx");
```

Um aspecto fundamental da gestão de documentos é garantir compatibilidade com diferentes versões do Microsoft Word. Aspose.Words para Java oferece uma maneira direta de otimizar documentos para versões específicas do Word. No exemplo acima, otimizamos um documento para Word 2016, assegurando compatibilidade perfeita.

## Identificando Erros Gramaticais e Ortográficos

```java
@Test
public void showGrammaticalAndSpellingErrors() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    doc.setShowGrammaticalErrors(true);
    doc.setShowSpellingErrors(true);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.ShowGrammaticalAndSpellingErrors.docx");
}
```

A precisão é fundamental ao lidar com documentos. Aspose.Words para Java permite destacar erros gramaticais e ortográficos dentro dos seus documentos, tornando a revisão e edição mais eficientes.

## Limpando Estilos e Listas Não Utilizados

```java
@Test
public void cleanupUnusedStylesAndLists() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Unused styles.docx");
    // Define cleanup options
    CleanupOptions cleanupOptions = new CleanupOptions();
    cleanupOptions.setUnusedLists(false);
    cleanupOptions.setUnusedStyles(true);
    doc.cleanup(cleanupOptions);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.CleanupUnusedStylesAndLists.docx");
}
```

Gerenciar estilos e listas de forma eficiente é essencial para manter a consistência do documento. Aspose.Words para Java permite limpar estilos e listas não utilizados, garantindo uma estrutura de documento organizada e enxuta.

## Removendo Estilos Duplicados

```java
@Test
public void cleanupDuplicateStyle() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    // Clean duplicate styles
    CleanupOptions options = new CleanupOptions();
    options.setDuplicateStyle(true);
    doc.cleanup(options);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.CleanupDuplicateStyle.docx");
}
```

Estilos duplicados podem gerar confusão e inconsistência nos documentos. Com Aspose.Words para Java, você pode remover estilos duplicados facilmente, mantendo a clareza e coerência do documento.

## Personalizando Opções de Visualização do Documento

```java
@Test
public void viewOptions() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    // Customize viewing options
    doc.getViewOptions().setViewType(ViewType.PAGE_LAYOUT);
    doc.getViewOptions().setZoomPercent(50);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.ViewOptions.docx");
}
```

Adaptar a experiência de visualização dos documentos é crucial. Aspose.Words para Java permite definir várias opções de visualização, como layout de página e percentual de zoom, para melhorar a legibilidade do documento.

## Configurando a Configuração de Página do Documento

```java
@Test
public void documentPageSetup() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    // Configure page setup options
    doc.getFirstSection().getPageSetup().setLayoutMode(SectionLayoutMode.GRID);
    doc.getFirstSection().getPageSetup().setCharactersPerLine(30);
    doc.getFirstSection().getPageSetup().setLinesPerPage(10);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.DocumentPageSetup.docx");
}
```

Uma configuração de página precisa é vital para a formatação de documentos. Aspose.Words para Java capacita você a definir modos de layout, **caracteres por linha** e linhas por página, garantindo que seus documentos sejam visualmente atraentes.

## Definindo Idiomas de Edição

```java
@Test
public void addJapaneseAsEditingLanguages() throws Exception
{
    LoadOptions loadOptions = new LoadOptions();
    // Set language preferences for editing
    loadOptions.getLanguagePreferences().addEditingLanguage(EditingLanguage.JAPANESE);
    Document doc = new Document("Your Directory Path" + "No default editing language.docx", loadOptions);
    // Check the overridden editing language
    int localeIdFarEast = doc.getStyles().getDefaultFont().getLocaleIdFarEast();
    System.out.println(localeIdFarEast == (int) EditingLanguage.JAPANESE
            ? "The document either has no any FarEast language set in defaults or it was set to Japanese originally."
            : "The document default FarEast language was set to another than Japanese language originally, so it is not overridden.");
}
```

Os idiomas de edição desempenham um papel importante no processamento de documentos. Com Aspose.Words para Java, você pode definir e personalizar os idiomas de edição para atender às necessidades linguísticas do seu documento.

## Conclusão

Neste guia, exploramos as diversas opções e configurações de documento disponíveis no Aspose.Words para Java. Desde otimização e exibição de erros até limpeza de estilos e opções de visualização, esta poderosa biblioteca oferece recursos extensos para gerenciar e personalizar seus documentos.

## Perguntas Frequentes

### Como otimizo um documento para uma versão específica do Word?

Para otimizar um documento para uma versão específica do Word, use o método `optimizeFor` e especifique a versão desejada. Por exemplo, para otimizar para Word 2016:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
doc.save("Your Directory Path" + "OptimizedForWord2016.docx");
```

### Como posso destacar erros gramaticais e ortográficos em um documento?

Você pode habilitar a exibição de erros gramaticais e ortográficos em um documento usando o código a seguir:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.setShowGrammaticalErrors(true);
doc.setShowSpellingErrors(true);
doc.save("Your Directory Path" + "ShowErrors.docx");
```

### Qual é o objetivo de limpar estilos e listas não utilizados?

Limpar estilos e listas não utilizados ajuda a manter uma estrutura de documento limpa e organizada. Remove elementos desnecessários, melhorando a legibilidade e a consistência do documento.

### Como removo estilos duplicados de um documento?

Para remover estilos duplicados de um documento, utilize o método `cleanup` com a opção `duplicateStyle` definida como `true`. Veja um exemplo:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
CleanupOptions options = new CleanupOptions();
options.setDuplicateStyle(true);
doc.cleanup(options);
doc.save("Your Directory Path" + "CleanedDocument.docx");
```

### Como personalizo as opções de visualização de um documento?

Você pode personalizar as opções de visualização do documento usando a classe `ViewOptions`. Por exemplo, para definir o tipo de visualização como layout de página e zoom para 50%:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getViewOptions().setViewType(ViewType.PAGE_LAYOUT);
doc.getViewOptions().setZoomPercent(50);
doc.save("Your Directory Path" + "CustomView.docx");
```

## Dicas Adicionais & Armadilhas Comuns

- **Habilite tanto a verificação ortográfica quanto a gramatical** quando precisar de revisão completa. Esquecer uma das flags (`setShowGrammaticalErrors` ou `setShowSpellingErrors`) pode deixar erros despercebidos.  
- **Ao definir caracteres por linha**, lembre‑se de que o valor interage com a fonte selecionada e as margens da página. Teste com o layout real do documento para evitar quebras de linha inesperadas.  
- **Operações de limpeza são irreversíveis** no arquivo original. Sempre trabalhe em uma cópia ou use controle de versão para preservar o estilo original.  
- **Preferências de idioma de edição** afetam o comportamento da verificação ortográfica. Se você trabalha com documentos multilíngues, adicione todos os idiomas relevantes a `LanguagePreferences`.

---

**Última atualização:** 2026-01-16  
**Testado com:** Aspose.Words para Java 24.12  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}