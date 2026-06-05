---
category: general
date: 2026-06-05
description: Detectar substituição de fonte ausente em Java usando Aspose.Words. Aprenda
  como configurar LoadOptions, FontSettings e callbacks de aviso para um processamento
  de documentos confiável.
draft: false
keywords:
- detect missing font substitution
- Java Aspose.Words
- LoadOptions configuration
- FontSettings warning callback
- document loading Java
language: pt
og_description: Detectar substituição de fonte ausente em Java com Aspose.Words. Este
  guia mostra passo a passo como configurar LoadOptions, FontSettings e um callback
  de aviso para capturar fontes ausentes.
og_title: detectar substituição de fonte ausente em Java – Tutorial completo do Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-05'
  description: detect missing font substitution in Java using Aspose.Words. Learn
    how to configure LoadOptions, FontSettings, and warning callbacks for reliable
    document processing.
  headline: detect missing font substitution in Java – Complete Aspose.Words Guide
  type: TechArticle
- description: detect missing font substitution in Java using Aspose.Words. Learn
    how to configure LoadOptions, FontSettings, and warning callbacks for reliable
    document processing.
  name: detect missing font substitution in Java – Complete Aspose.Words Guide
  steps:
  - name: 4.1 Quick verification
    text: Run the program from your IDE or via `java -cp .;aspose-words-23.12.jar
      MissingFontDetector`. If the document references a font you don’t have, you’ll
      see the warning message printed. If the console stays silent, either the font
      exists on your machine or the document doesn’t request any missing font
  - name: 4.2 Logging instead of `System.out`
    text: 'In production code you probably want a logger:'
  - name: 4.3 Handling other warning types
    text: 'The callback receives *all* warnings, not just font issues. If you’d like
      to keep an eye on other problems (e.g., `UNKNOWN_STYLE`), add extra `if` branches.
      Here’s a quick example:'
  type: HowTo
tags:
- Aspose.Words
- Java
- Font handling
title: detectar substituição de fonte ausente em Java – Guia Completo do Aspose.Words
url: /pt/java/document-loading-and-saving/detect-missing-font-substitution-in-java-complete-aspose-wor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# detectar substituição de fonte ausente em Java – Guia Completo do Aspose.Words

Já se perguntou como **detectar substituição de fonte ausente** ao carregar um documento Word em Java? Você não está sozinho. Fontes ausentes podem estragar silenciosamente seus PDFs ou páginas renderizadas, e identificá‑las cedo economiza horas de depuração. Neste tutorial vamos percorrer uma solução prática que não só carrega um documento, mas também informa exatamente quando ocorre uma substituição de fonte.

Vamos cobrir tudo, desde a criação de `LoadOptions` até a configuração de um `WarningCallback` que imprime uma mensagem clara sempre que o Aspose.Words troca uma fonte ausente. Ao final, você terá um trecho reutilizável que funciona com qualquer arquivo `.docx` e entenderá *por que* cada parte é importante. Sem bibliotecas extras, apenas Java puro e Aspose.Words.

## O que você aprenderá

- Como configurar **LoadOptions** para usar **FontSettings** personalizados.  
- Como implementar um **IWarningCallback** que captura avisos `FONT_SUBSTITUTION`.  
- Como carregar um documento monitorando com segurança fontes ausentes.  
- Saída esperada no console e como adaptar o código para frameworks de logging.  

**Pré‑requisitos**: Java 8+ instalado, Aspose.Words for Java (v23.12 ou mais recente) no seu classpath e um arquivo `.docx` de exemplo que faça referência a uma fonte que você não tenha instalada. É só isso — nenhuma ferramenta de build extra necessária.

---

## Etapa 1: Configurar o Projeto e Adicionar Aspose.Words

Antes de mergulharmos no código, certifique‑se de que o Aspose.Words está disponível. Se você usa Maven, adicione a dependência a seguir ao seu `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

Se preferir Gradle, o equivalente é:

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

Com a biblioteca no classpath, você está pronto para **detectar substituição de fonte ausente** em uma única chamada de método.

---

## Etapa 2: Criar LoadOptions e Anexar FontSettings

O coração da solução está em preparar uma instância de `LoadOptions` que saiba como observar problemas de fonte. Aqui está o código linha por linha.

```java
import com.aspose.words.*;

public class MissingFontDetector {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Prepare load options – this object controls how the document is read.
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Create FontSettings – it holds font‑related configuration.
        FontSettings fontSettings = new FontSettings();

        // 3️⃣ Register a warning callback that will be invoked on font substitution.
        fontSettings.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // We only care about FONT_SUBSTITUTION warnings.
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("⚠️ Font substitution detected: " + info.getMessage());
                }
            }
        });

        // 4️⃣ Attach the FontSettings to the LoadOptions.
        loadOptions.setFontSettings(fontSettings);
```

**Por que isso importa**: `LoadOptions` indica ao Aspose.Words *como* interpretar o arquivo de entrada. Ao conectar um `FontSettings` customizado, fornecemos ao carregador um hook (`IWarningCallback`) que dispara **exatamente quando uma fonte ausente é substituída**. Sem esse callback, o Aspose.Words substituiria a fonte silenciosamente e você nunca saberia.

---

## Etapa 3: Carregar o Documento com as Opções Configuradas

Agora que o sistema de avisos está configurado, carregar o documento torna‑se simples.

```java
        // 5️⃣ Load the document using the prepared options.
        // Replace the path with the location of your test file.
        String docPath = "YOUR_DIRECTORY/docWithMissingFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // Optional: do something with the document (e.g., save as PDF).
        // doc.save("output.pdf");
    }
}
```

Quando a chamada `new Document(...)` é executada, o Aspose.Words lê o arquivo, verifica cada referência de fonte e, se não encontrar uma fonte correspondente no sistema, aciona o método `warning` que definimos anteriormente. O console exibirá imediatamente uma linha como:

```
⚠️ Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Essa linha é a saída de **detectar substituição de fonte ausente** que você estava procurando.

---

## Etapa 4: Verificar o Resultado e Ajustar o Callback (Avançado)

### 4.1 Verificação rápida

Execute o programa a partir da sua IDE ou via `java -cp .;aspose-words-23.12.jar MissingFontDetector`. Se o documento fizer referência a uma fonte que você não possui, verá a mensagem de aviso impressa. Se o console permanecer silencioso, a fonte existe na sua máquina ou o documento não solicita fontes ausentes.

### 4.2 Logging em vez de `System.out`

Em código de produção você provavelmente desejará um logger:

```java
import java.util.logging.Logger;

private static final Logger logger = Logger.getLogger(MissingFontDetector.class.getName());

fontSettings.setWarningCallback(info -> {
    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
        logger.warning("Font substitution: " + info.getMessage());
    }
});
```

Essa pequena mudança faz com que o mecanismo de **detectar substituição de fonte ausente** funcione bem com pipelines de logging existentes.

### 4.3 Tratando outros tipos de aviso

O callback recebe *todos* os avisos, não apenas problemas de fonte. Se quiser monitorar outros problemas (por exemplo, `UNKNOWN_STYLE`), adicione ramificações `if` extras. Aqui vai um exemplo rápido:

```java
if (info.getWarningType() == WarningType.UNKNOWN_STYLE) {
    logger.info("Unknown style encountered: " + info.getMessage());
}
```

---

## Etapa 5: Armadilhas Comuns e Dicas Profissionais

| Armadilha | Por que acontece | Solução |
|----------|------------------|---------|
| **Nenhum aviso aparece** | A fonte realmente existe no SO, ou o documento usa um fallback que o Aspose.Words considera “encontrado”. | Exclua temporariamente a fonte do sistema ou use um nome de fonte realmente ausente no documento de origem. |
| **Callback nunca chamado** | `setWarningCallback` foi chamado em uma instância *diferente* de `FontSettings` da que está anexada ao `LoadOptions`. | Garanta que você chame `loadOptions.setFontSettings(fontSettings)` **depois** de configurar o callback. |
| **Desaceleração de desempenho** | Carregar muitos documentos grandes com callbacks pode acrescentar sobrecarga. | Armazene em cache uma única instância de `FontSettings` e reutilize‑a entre carregamentos se estiver processando lotes. |
| **Múltiplas threads** | `FontSettings` não é thread‑safe por padrão. | Crie um `FontSettings` separado por thread ou sincronize o acesso. |

**Dica profissional**: Se você estiver gerando PDFs para um serviço web, pode ser interessante coletar todos os avisos de substituição em uma lista e retorná‑los na resposta da API, em vez de imprimir no console.

---

## Exemplo Completo (Pronto para Copiar‑Colar)

```java
import com.aspose.words.*;

public class MissingFontDetector {
    public static void main(String[] args) throws Exception {
        // Prepare load options
        LoadOptions loadOptions = new LoadOptions();

        // Configure font settings with a warning callback
        FontSettings fontSettings = new FontSettings();
        fontSettings.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("⚠️ Font substitution detected: " + info.getMessage());
                }
            }
        });

        // Attach font settings to load options
        loadOptions.setFontSettings(fontSettings);

        // Path to the document that contains a missing font
        String docPath = "YOUR_DIRECTORY/docWithMissingFont.docx";

        // Load the document – this triggers the callback if needed
        Document doc = new Document(docPath, loadOptions);

        // Optional: save as PDF to verify visual output
        // doc.save("output.pdf");

        System.out.println("Document loaded successfully.");
    }
}
```

**Saída esperada no console** (supondo que o arquivo faça referência a uma fonte ausente):

```
⚠️ Font substitution detected: Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
Document loaded successfully.
```

Se não houver fontes ausentes, você verá apenas a linha final “Document loaded successfully.”.

---

## Conclusão

Acabamos de demonstrar como **detectar substituição de fonte ausente** em Java usando Aspose.Words. Ao configurar `LoadOptions`, criar uma instância de `FontSettings` e conectar um `IWarningCallback`, você obtém total visibilidade sobre cada fonte que a biblioteca troca nos bastidores. Essa abordagem não só evita falhas silenciosas de renderização, como também fornece um ponto de extensão para logging, alertas ou até mesmo incorporação automática de fontes alternativas.

A partir daqui você pode:

- Expandir o callback para coletar avisos em uma lista para respostas de API.  
- Combinar essa técnica com **configuração de LoadOptions** para outros cenários (por exemplo, carregamento de recursos personalizados).  
- Explorar o ecossistema mais amplo do **Java Aspose.Words**: conversão para PDF, extração de texto ou execução de mail merges.

Experimente, ajuste o logger e deixe suas aplicações avisarem quando uma fonte desaparecer. Boa codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos estreitamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Using Document Options and Settings in Aspose.Words for Java](/words/english/java/document-manipulation/using-document-options-and-settings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}