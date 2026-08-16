---
category: general
date: 2026-06-20
description: Como definir um callback no Aspose.Words Java para detectar fontes ausentes
  e personalizar o carregamento de documentos. Aprenda passo a passo como lidar com
  avisos de substituição de fontes.
draft: false
keywords:
- how to set callback
- detect missing fonts
- handle missing fonts
- customize document loading
language: pt
og_description: como definir um callback no Aspose.Words Java para detectar fontes
  ausentes, lidar com substituições e personalizar o carregamento de documentos. Guia
  completo com código.
og_title: como definir callback – Detectar fontes ausentes no Aspose.Words Java
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: how to set callback in Aspose.Words Java to detect missing fonts and
    customize document loading. Learn step‑by‑step handling of font substitution warnings.
  headline: how to set callback in Aspose.Words Java – Detect and Handle Missing Fonts
  type: TechArticle
- description: how to set callback in Aspose.Words Java to detect missing fonts and
    customize document loading. Learn step‑by‑step handling of font substitution warnings.
  name: how to set callback in Aspose.Words Java – Detect and Handle Missing Fonts
  steps:
  - name: What if I want the program to stop loading when a font is missing?
    text: 'Throw an exception inside the `warning` method:'
  - name: Does this work for PDFs generated from DOCX?
    text: Absolutely. The callback fires during the **loading** phase, which is identical
      for all output formats (`save` to PDF, DOCX, HTML, etc.). As long as you load
      the source document with the same `LoadOptions`, you’ll catch missing fonts
      before they affect the final PDF.
  - name: Can I capture other warning types (e.g., image conversion)?
    text: Yes—`WarningInfo.getWarningType()` can be compared against other enums like
      `WarningType.IMAGE_CONVERSION`. Just add more `if` branches in the callback.
  - name: Is there a performance impact?
    text: Negligible. The callback runs synchronously during loading, and the extra
      checks are lightweight. If you’re loading thousands of documents, you might
      want to disable warnings in production by setting `loadOptions.setWarningCallback(null);`.
  - name: What’s Next?
    text: '- Explore **font substitution tables** for bulk mapping of many missing
      fonts. - Combine this callback with **document validation** to enforce style
      guides. - Try **custom warning callbacks** that write to a log file or a monitoring
      system instead of `System.out`.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Document Processing
title: como definir callback no Aspose.Words Java – Detectar e lidar com fontes ausentes
url: /pt/java/document-loading-and-saving/how-to-set-callback-in-aspose-words-java-detect-and-handle-m/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# como definir callback no Aspose.Words Java – Detectar e Tratar Fontes Ausentes

Já se perguntou **como definir callback** no Aspose.Words Java para identificar fontes ausentes antes que elas estraguem seu PDF ou DOCX? Você não está sozinho. Avisos de fontes ausentes podem corromper silenciosamente o layout, e sem um callback de aviso adequado você pode nunca perceber até que o documento final pareça errado.  

Neste tutorial vamos percorrer um exemplo completo, pronto‑para‑executar que **detecta fontes ausentes**, **trata fontes ausentes** de forma elegante e mostra como **personalizar o carregamento de documentos** com um callback de aviso. Ao final você terá uma classe Java autônoma que pode ser inserida em qualquer projeto—sem necessidade de buscar documentação extra.

## O que você precisará

- Java 8 ou mais recente (o código também funciona com Java 11+)  
- Biblioteca Aspose.Words for Java (versão 23.9 ou posterior)  
- Um arquivo DOCX que faça referência a uma fonte que você não tem instalada (por exemplo, uma fonte corporativa personalizada)  

Se ainda não adicionou o Aspose.Words ao seu projeto Maven, basta incluir:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

É isso—sem plugins extras, sem dependências nativas.

---

## Etapa 1: Entender o Mecanismo WarningCallback

O **warning callback** é a forma que o Aspose.Words tem de alertá‑lo quando algo inesperado acontece ao carregar ou salvar um documento. Ao implementar `IWarningCallback` você obtém controle total sobre o que é registrado, ignorado ou até transformado em exceção.

> **Por que isso importa:**  
> Quando uma fonte está ausente, o Aspose substitui por uma fonte de fallback. O resultado visual pode ser drasticamente diferente, especialmente em PDFs com forte identidade de marca. Ao capturar `WarningType.FONT_SUBSTITUTION`, você pode registrar o nome exato da fonte, decidir se aborta ou substituir sua própria fonte personalizada programaticamente.

---

## Etapa 2: Criar uma Instância de LoadOptions

`LoadOptions` é o ponto de entrada para personalizar o carregamento de documentos. Você anexará o callback a esse objeto antes de realmente carregar o arquivo.

```java
// Step 2: Prepare LoadOptions
LoadOptions loadOptions = new LoadOptions();
```

Neste ponto `loadOptions` é apenas um contêiner simples—nada acontece ainda. A verdadeira mágica começa quando conectamos o callback.

---

## Etapa 3: Implementar e Anexar o Callback

Abaixo está uma classe anônima compacta que implementa `IWarningCallback`. Ela imprime uma linha amigável no console sempre que ocorre uma substituição de fonte.

```java
// Step 3: Attach a warning callback to capture font substitution warnings
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Detect missing fonts
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("[Missing Font] " + info.getDescription());
            // Optional: you could throw an exception here to abort loading
            // throw new RuntimeException("Font missing: " + info.getDescription());
        }
    }
});
```

> **Dica profissional:** Se quiser **tratar fontes ausentes** fornecendo uma substituição, também pode definir `FontSettings` em `LoadOptions` e mapear fontes ausentes para um fallback conhecido.

---

## Etapa 4: Carregar o Documento com suas Opções Personalizadas

Agora que o callback está configurado, carregue o documento. Se o arquivo fizer referência a uma fonte que você não possui, o aviso será impresso.

```java
// Step 4: Load the document using the configured LoadOptions
String docPath = "YOUR_DIRECTORY/doc-with-missing-font.docx";
Document document = new Document(docPath, loadOptions);
```

Ao executar o programa, o console pode exibir:

```
[Missing Font] Font substitution: The font "MyCustomFont" was not found. Substituted with "Arial".
```

Essa linha prova que você **detectou fontes ausentes** com sucesso e está agora em posição de **tratar fontes ausentes** da maneira que preferir.

---

## Etapa 5: Opcional – Substituir Fontes Ausentes por uma Fonte Conhecida

Se preferir substituir automaticamente qualquer fonte ausente por, por exemplo, `Times New Roman`, pode adicionar um objeto `FontSettings`:

```java
// Optional Step 5: Map missing fonts to a fallback
FontSettings fontSettings = new FontSettings();
fontSettings.setMissingFontNotification(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // This will be called for each missing font
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("[Auto‑Replace] " + info.getDescription());
        }
    }
});
// Force substitution to Times New Roman
fontSettings.getSubstitutionSettings().getTableSubstitution().addSubstitutes("MyCustomFont", new String[]{"Times New Roman"});
loadOptions.setFontSettings(fontSettings);
```

Agora o documento carrega, e qualquer referência a `MyCustomFont` é silenciosamente trocada por `Times New Roman`. O console ainda informará o que foi substituído, mantendo você atualizado.

---

## Exemplo Completo Funcional

Abaixo está uma única classe Java que incorpora todas as etapas acima. Copie‑e‑cole no seu IDE, ajuste `docPath` e execute.

```java
import com.aspose.words.*;

public class DetectMissingFontsDemo {
    public static void main(String[] args) {
        try {
            // 1️⃣ Create LoadOptions
            LoadOptions loadOptions = new LoadOptions();

            // 2️⃣ Attach warning callback (detect missing fonts)
            loadOptions.setWarningCallback(new IWarningCallback() {
                @Override
                public void warning(WarningInfo info) {
                    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                        System.out.println("[Missing Font] " + info.getDescription());
                    }
                }
            });

            // 3️⃣ (Optional) Set up automatic font substitution
            FontSettings fontSettings = new FontSettings();
            fontSettings.getSubstitutionSettings()
                        .getTableSubstitution()
                        .addSubstitutes("MyCustomFont", new String[]{"Times New Roman"});
            loadOptions.setFontSettings(fontSettings);

            // 4️⃣ Load the document with custom loading behavior
            String docPath = "YOUR_DIRECTORY/doc-with-missing-font.docx";
            Document doc = new Document(docPath, loadOptions);

            // 5️⃣ Save to PDF to see the final result (optional)
            doc.save("output.pdf");
            System.out.println("Document loaded and saved successfully.");

        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Saída esperada**

```
[Missing Font] Font substitution: The font "MyCustomFont" was not found. Substituted with "Times New Roman".
Document loaded and saved successfully.
```

Agora você tem um método reproduzível para **detectar fontes ausentes**, **tratar fontes ausentes** e **personalizar o carregamento de documentos**—tudo aprendendo **como definir callback** corretamente.

---

## Perguntas Frequentes

### E se eu quiser que o programa pare de carregar quando uma fonte estiver ausente?

Lance uma exceção dentro do método `warning`:

```java
throw new RuntimeException("Critical: Missing font - " + info.getDescription());
```

O bloco `catch` ao final capturará a exceção, e você pode decidir como registrar ou alertar o usuário.

### Isso funciona para PDFs gerados a partir de DOCX?

Absolutamente. O callback é disparado durante a fase de **carregamento**, que é idêntica para todos os formatos de saída (`save` para PDF, DOCX, HTML, etc.). Desde que você carregue o documento fonte com o mesmo `LoadOptions`, você capturará fontes ausentes antes que afetem o PDF final.

### Posso capturar outros tipos de aviso (por exemplo, conversão de imagem)?

Sim—`WarningInfo.getWarningType()` pode ser comparado a outros enums como `WarningType.IMAGE_CONVERSION`. Basta adicionar mais ramificações `if` no callback.

### Há impacto de desempenho?

Negligível. O callback roda de forma síncrona durante o carregamento, e as verificações adicionais são leves. Se você estiver carregando milhares de documentos, pode desativar avisos em produção definindo `loadOptions.setWarningCallback(null);`.

---

## Visão Geral Visual

![exemplo de como definir callback no Aspose.Words Java](https://example.com/images/callback-diagram.png "como definir callback")

*O diagrama ilustra o fluxo: `LoadOptions` → `IWarningCallback` → Carregamento do documento → Manipulação de substituição de fonte.*

---

## Conclusão

Cobrimos **como definir callback** no Aspose.Words Java, demonstramos **detectar fontes ausentes**, mostramos maneiras práticas de **tratar fontes ausentes** e explicamos como **personalizar o carregamento de documentos** com `LoadOptions`.  

Com esse conhecimento, você pode proteger seus pipelines de documentos contra trocas silenciosas de fontes, manter a identidade visual intacta e oferecer aos usuários feedback claro quando algo sai errado.

### O que vem a seguir?

- Explore **tabelas de substituição de fontes** para mapeamento em massa de várias fontes ausentes.  
- Combine este callback com **validação de documentos** para impor guias de estilo.  
- Experimente **callbacks de aviso personalizados** que escrevem em um arquivo de log ou em um sistema de monitoramento ao invés de `System.out`.  

Sinta‑se à vontade para experimentar e nos conte como você personalizou o callback nos seus próprios projetos. Feliz codificação!

---


## O que você deve aprender a seguir?


Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Como definir LoadOptions no Aspose.Words para Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Como detectar fontes no Aspose.Words – Tratar avisos e configurações](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Como capturar fontes no Aspose.Words – Guia completa](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}