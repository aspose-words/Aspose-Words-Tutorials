---
category: general
date: 2026-06-08
description: Encontre fontes ausentes rapidamente usando Aspose.Words para Java. Aprenda
  a diagnosticar avisos de substituição de fontes e a corrigir problemas de fontes
  ausentes em apenas alguns passos.
draft: false
keywords:
- find missing fonts
- Aspose.Words for Java
- FontSubstitutionWarning
- LoadOptions
- document warnings
language: pt
og_description: Encontre fontes ausentes em seus arquivos DOCX com Aspose.Words para
  Java. Este tutorial mostra como habilitar diagnósticos, ler eventos FontSubstitutionWarning
  e exibir os nomes das fontes originais versus as substituídas.
og_title: Encontrar fontes ausentes em Java – Aspose.Words passo a passo
schemas:
- author: Aspose
  dateModified: '2026-06-08'
  description: Find missing fonts quickly using Aspose.Words for Java. Learn to diagnose
    font substitution warnings and fix missing font issues in just a few steps.
  headline: Find Missing Fonts in Java with Aspose.Words – Complete Guide
  type: TechArticle
- description: Find missing fonts quickly using Aspose.Words for Java. Learn to diagnose
    font substitution warnings and fix missing font issues in just a few steps.
  name: Find Missing Fonts in Java with Aspose.Words – Complete Guide
  steps:
  - name: Expected Console Output
    text: '``` Font substituted: Comic Sans MS → Arial Font substituted: MyCustomFont
      → Times New Roman ```'
  - name: Missing Font but No Warning
    text: Sometimes a font is embedded in the DOCX, but the embedding is corrupted.
      Aspose will still raise a `FontSubstitutionWarning` because it cannot render
      the text. To differentiate, check `fsWarning.isFontEmbedded()` (available in
      newer versions).
  - name: Multiple Substitutions for the Same Font
    text: A single missing font may be substituted multiple times across different
      runs if the fallback hierarchy changes (e.g., first tries Arial, then falls
      back to Helvetica). Keep a `Set<String>` of `getOriginalFontName()` to deduplicate
      if you only need a list of unique missing fonts.
  - name: Performance Considerations
    text: Loading very large DOCX files (hundreds of MB) while collecting warnings
      can add overhead. If you only need font diagnostics, set `loadOptions.setValidateStructure(false)`
      to skip deep validation. This speeds up the process without affecting warning
      generation.
  type: HowTo
tags:
- Java
- Aspose.Words
- fonts
- diagnostics
title: Encontre fontes ausentes no Java com Aspose.Words – Guia completo
url: /pt/java/document-rendering/find-missing-fonts-in-java-with-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Encontrar fontes ausentes em Java com Aspose.Words – Guia Completo

Já se perguntou como **encontrar fontes ausentes** em um documento Word antes que ele quebre o layout? Você não está sozinho—desenvolvedores constantemente se deparam com trocas silenciosas de fontes que arruinam PDFs ou relatórios impressos. A boa notícia é que o Aspose.Words for Java oferece uma API de diagnóstico integrada que facilita a identificação dessas fontes ausentes.

Neste tutorial vamos percorrer um exemplo do mundo real que carrega um DOCX, habilita a coleta de avisos e imprime cada *FontSubstitutionWarning* que você precisa conhecer. Ao final, você poderá registrar o nome da fonte original, a fonte de fallback que o Aspose escolheu e decidir se incorpora a fonte ausente você mesmo.

## O que você precisará

Antes de mergulharmos, certifique‑se de que tem:

* **Aspose.Words for Java** (versão mais recente 23.x) no seu classpath.  
* Um ambiente de desenvolvimento Java 8+ (IDE de sua escolha, Maven/Gradle funciona bem).  
* Um DOCX de exemplo que intencionalmente referencia uma fonte não instalada em sua máquina—vamos chamá‑lo de `MissingFonts.docx`.

Isso é tudo. Nenhuma biblioteca extra, nenhuma configuração complexa, apenas Java puro e Aspose.

![Diagrama de fontes ausentes](https://example.com/find-missing-fonts.png "Diagrama de fontes ausentes")

*A imagem acima ilustra o fluxo: carregar → diagnóstico → avisos → saída.*

## Etapa 1: Preparar LoadOptions e especificar o formato do documento

A primeira coisa que fazemos é criar um objeto **LoadOptions**. Ele informa ao Aspose.Words como interpretar o arquivo de entrada e, crucialmente, habilita a coleta de *avisos de documento*.

```java
import com.aspose.words.*;

public class FontSubstitutionDiagnostics {
    public static void main(String[] args) throws Exception {
        // Create LoadOptions and force DOCX format (helps when the file extension is misleading)
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setLoadFormat(LoadFormat.DOCX);
```

*Por que usar LoadOptions?*  
Sem ele, o Aspose ainda carrega o arquivo, mas pode pular alguns dados de diagnóstico. Ao definir explicitamente o formato, você garante a geração consistente de avisos, especialmente ao lidar com arquivos mais antigos ou corrompidos.

## Etapa 2: Carregar o documento com diagnóstico habilitado

Agora lemos o arquivo de fato. O construtor `Document` inicia automaticamente a coleta de avisos, que mais tarde incluirá quaisquer instâncias de **FontSubstitutionWarning**.

```java
        // Load the document located in your project folder
        Document doc = new Document("YOUR_DIRECTORY/MissingFonts.docx", loadOptions);
```

> **Dica profissional:** Se você estiver usando Maven, adicione a dependência Aspose.Words ao seu `pom.xml`. Dessa forma o JAR será incluído automaticamente e você não precisará gerenciar o classpath manualmente.

## Etapa 3: Analisar os avisos do documento para eventos de substituição de fonte

O Aspose armazena cada aviso em uma coleção que pode ser percorrida. Filtramos objetos `FontSubstitutionWarning` porque eles indicam especificamente uma fonte ausente que foi substituída.

```java
        // Iterate over all warnings generated during load
        for (WarningInfo warning : doc.getWarnings()) {
            if (warning instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fsWarning = (FontSubstitutionWarning) warning;
```

*O que está acontecendo aqui?*  
`doc.getWarnings()` retorna um `List<WarningInfo>`. Ao verificar `instanceof FontSubstitutionWarning` isolamos apenas as entradas relacionadas a fontes, ignorando outros avisos como “recurso não suportado” ou “conversão de imagem”.

## Etapa 4: Exibir os nomes da fonte original e substituída

Finalmente, imprimimos tanto o nome da fonte ausente (original) quanto a fonte que o Aspose escolheu como substituta. Essa saída é perfeita para logs ou para alimentar uma verificação em um pipeline de build.

```java
                // Print the original font and the font Aspose substituted it with
                System.out.println("Font substituted: " + fsWarning.getOriginalFontName()
                        + " → " + fsWarning.getSubstitutedFontName());
            }
        }
    }
}
```

### Saída esperada no console

```
Font substituted: Comic Sans MS → Arial
Font substituted: MyCustomFont → Times New Roman
```

Se nada for impresso, isso significa que **nenhuma fonte ausente foi detectada**—seu documento já contém fontes que existem na máquina onde o código está sendo executado.

## Etapa 5: Lidando com casos extremos e armadilhas comuns

### Fonte ausente, mas sem aviso

Às vezes uma fonte está incorporada no DOCX, mas a incorporação está corrompida. O Aspose ainda gerará um `FontSubstitutionWarning` porque não consegue renderizar o texto. Para diferenciar, verifique `fsWarning.isFontEmbedded()` (disponível em versões mais recentes).

### Substituições múltiplas para a mesma fonte

Uma única fonte ausente pode ser substituída várias vezes em execuções diferentes se a hierarquia de fallback mudar (por exemplo, primeiro tenta Arial, depois recorre a Helvetica). Mantenha um `Set<String>` de `getOriginalFontName()` para desduplicar caso você precise apenas de uma lista de fontes ausentes únicas.

### Considerações de desempenho

Carregar arquivos DOCX muito grandes (centenas de MB) enquanto coleta avisos pode acrescentar sobrecarga. Se você precisar apenas de diagnóstico de fontes, defina `loadOptions.setValidateStructure(false)` para pular a validação profunda. Isso acelera o processo sem afetar a geração de avisos.

## Bônus: Automatizando a incorporação de fontes

Depois de saber quais fontes estão ausentes, você pode incorporá‑las programaticamente:

```java
for (String missingFont : missingFontsSet) {
    // Assume you have the TTF file for the missing font in a known folder
    FontSettings.getDefaultInstance().setFontsFolder("YOUR_FONTS_FOLDER", true);
}
```

Incorporar garante que o PDF final ou o DOCX salvo seja renderizado exatamente como pretendido em qualquer máquina—sem surpresas de fallback.

## Recapitulação: Como encontrar fontes ausentes com Aspose.Words

- **Criar LoadOptions** e definir o formato de carregamento.  
- **Carregar o documento** enquanto o Aspose captura avisos.  
- **Iterar sobre `doc.getWarnings()`**, filtrando por `FontSubstitutionWarning`.  
- **Imprimir** `getOriginalFontName()` e `getSubstitutedFontName()` para ver quais fontes estão ausentes.  
- **Opcional:** desduplicar, verificar o status de incorporação ou incorporar automaticamente as fontes ausentes.

Essa é a solução completa para **encontrar fontes ausentes** em uma aplicação Java usando Aspose.Words. Agora você tem um método confiável para detectar problemas de fonte cedo, manter seus PDFs consistentes e evitar surpresas desagradáveis em produção.

## O que explorar a seguir?

* **Incorporar fontes** automaticamente (veja o trecho bônus).  
* **Gerar um PDF** após corrigir as fontes para verificar a saída visual.  
* **Usar FontSettings** do Aspose.Words para definir uma cadeia de fallback personalizada.  
* **Executar o mesmo diagnóstico** em arquivos DOC, RTF ou HTML—basta mudar `LoadFormat` conforme necessário.

Sinta‑se à vontade para experimentar diferentes tipos de documentos e famílias de fontes. Se encontrar algum obstáculo, deixe um comentário abaixo ou consulte a documentação oficial da API Java da Aspose para personalizações mais avançadas.

Feliz codificação, e que seus documentos sempre sejam renderizados com as fontes que você pretendia!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos estreitamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Usando fontes no Aspose.Words para Java](/words/english/java/using-document-elements/using-fonts/)
- [Capturar avisos de substituição de fonte em Java com Aspose.Words – Guia Completo](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Como detectar fontes no Aspose.Words – Manipular avisos e configurações](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}