---
category: general
date: 2026-06-17
description: Registre avisos de substituição de fontes em Java usando Aspose.Words
  – capture fontes ausentes ao carregar o documento e mantenha sua saída consistente.
draft: false
keywords:
- log font substitution warnings
- Aspose.Words Java
- font substitution
- warning callback
- LoadOptions
- document loading
language: pt
og_description: Registre avisos de substituição de fontes em Java com Aspose.Words.
  Aprenda a capturar alertas de fontes ausentes durante o carregamento do documento
  e mantenha seus PDFs impecáveis.
og_title: Registro de Avisos de Substituição de Fonte no Java – Guia Completo
schemas:
- author: Aspose
  dateModified: '2026-06-17'
  description: Log font substitution warnings in Java using Aspose.Words – capture
    missing fonts during document load and keep your output consistent.
  headline: Log Font Substitution Warnings in Java with Aspose.Words
  type: TechArticle
- description: Log font substitution warnings in Java using Aspose.Words – capture
    missing fonts during document load and keep your output consistent.
  name: Log Font Substitution Warnings in Java with Aspose.Words
  steps:
  - name: Prerequisites
    text: '- Java 8 or newer (the code works with Java 11+ as well). - Aspose.Words
      for Java library (version 23.10 or later is recommended). - A sample `.docx`
      that references a font not installed on your machine (e.g., `MissingFont.docx`).'
  - name: Logging to a File Instead of the Console
    text: 'If you prefer a persistent log, replace the `System.out.println` call with
      a `FileWriter`:'
  - name: Capturing Multiple Documents in a Loop
    text: 'When processing a folder of documents, you can reuse the same callback:'
  - name: Dealing with Embedded Fonts
    text: 'Aspose.Words can embed missing fonts if you enable it:'
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Processing
title: Registrar avisos de substituição de fontes em Java com Aspose.Words
url: /pt/java/document-loading-and-saving/log-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Registrar Avisos de Substituição de Fonte em Java – Guia Completo

Já se perguntou como **registrar avisos de substituição de fonte** quando um documento Word tenta usar uma fonte que não está disponível no servidor? Você não é o único a coçar a cabeça diante de fontes ausentes que são trocadas silenciosamente. A boa notícia? O Aspose.Words for Java oferece uma maneira simples de capturar essas substituições no instante em que o documento é carregado.

Neste tutorial, vamos percorrer um exemplo prático que mostra exatamente como registrar um callback de aviso, filtrar alertas de **substituição de fonte** e gravá‑los no console (ou em qualquer logger que preferir). Ao final, você terá um trecho reutilizável que pode ser inserido em qualquer projeto Java que use **Aspose.Words Java**.

## O que Você Vai Aprender

- Como configurar **LoadOptions** para capturar avisos.
- Como implementar um **IWarningCallback** que reage apenas a eventos de **substituição de fonte**.
- Como carregar um documento com segurança mantendo um registro claro das fontes ausentes.
- Dicas para estender a solução para logs baseados em arquivo ou sistemas de monitoramento.

### Pré‑requisitos

- Java 8 ou superior (o código funciona também com Java 11+).
- Biblioteca Aspose.Words for Java (versão 23.10 ou posterior é recomendada).
- Um arquivo `.docx` de exemplo que faça referência a uma fonte não instalada na sua máquina (por exemplo, `MissingFont.docx`).

Nenhum framework adicional é necessário — apenas Java puro e os Aspose.JARs.

---

## Etapa 1: Configurar LoadOptions para Aspose.Words Java

Antes de interceptar quaisquer avisos, você precisa de uma instância **LoadOptions**. Esse objeto indica ao Aspose.Words como se comportar ao analisar o arquivo de entrada.

```java
// Step 1: Create LoadOptions to enable warning capture
LoadOptions loadOptions = new LoadOptions();
```

Por que essa etapa é crucial? Sem um objeto `LoadOptions`, a biblioteca substitui silenciosamente as fontes ausentes e você nunca vê nenhum rastreamento. Ao criar explicitamente um, você abre a porta para um **callback de aviso** personalizado que pode registrar exatamente o que lhe interessa.

> **Dica profissional:** Se você estiver carregando muitos documentos em lote, reutilize uma única instância de `LoadOptions` para evitar criação desnecessária de objetos.

---

## Etapa 2: Implementar um Callback de Aviso para Substituição de Fonte

O Aspose.Words fornece a interface `IWarningCallback`. Implementá‑la permite decidir o que fazer quando o motor gera um `WarningInfo`. No nosso caso, queremos reagir apenas ao `WarningType.FONT_SUBSTITUTION`.

```java
// Step 2: Register a warning callback that logs only font‑substitution warnings
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Filter for font‑substitution warnings only
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            // Simple console output – replace with a logger if you prefer
            System.out.println("Font substitution: " + info.getMessage());
        }
    }
});
```

Alguns pontos a observar:

1. **Filtragem** – A instrução `if` garante que ignoramos avisos não relacionados (como problemas de layout) e mantemos o log organizado.
2. **Segurança de thread** – O callback é executado na mesma thread que carrega o documento, portanto não é necessário sincronização extra para saída simples no console. Se você escrever em um logger compartilhado, certifique‑se de que ele seja thread‑safe.
3. **Extensibilidade** – Quer gravar em um arquivo? Substitua `System.out.println` por `java.util.logging.Logger` ou por um framework de logging de terceiros.

---

## Etapa 3: Carregar o Documento Usando as Opções Configuradas

Agora que o callback está definido, carregue seu arquivo Word. No momento em que o Aspose.Words analisar o documento, qualquer fonte ausente acionará o callback definido acima.

```java
// Step 3: Load the document with the warning‑aware LoadOptions
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

Se o arquivo de origem fizer referência a uma fonte que não está instalada, você verá uma saída semelhante a:

```
Font substitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Essa linha é o **registro de avisos de substituição de fonte** que você procurava. Agora você pode agir sobre ele — talvez alertar um usuário, mudar para uma folha de estilos alternativa ou simplesmente manter um registro para conformidade.

---

## Etapa 4: Continuar o Processamento Normal

Após o carregamento, o documento se comporta como qualquer outro objeto `Document`. Sinta‑se à vontade para inspecionar seções, extrair texto ou converter para PDF. O registro de avisos ocorre automaticamente durante a etapa de carregamento, portanto não é necessário código extra.

```java
// Example: Print the number of sections – just to prove the doc is usable
System.out.println("Document has " + doc.getSections().getCount() + " sections.");
```

O console exibirá agora tanto o aviso de substituição de fonte (se houver) **quanto** a contagem de seções, confirmando que o documento está totalmente funcional.

---

## Dicas Avançadas & Casos de Borda

### Registrando em um Arquivo ao Invés do Console

Se preferir um log persistente, substitua a chamada `System.out.println` por um `FileWriter`:

```java
private static final String LOG_PATH = "logs/font_substitutions.txt";

loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            try (FileWriter fw = new FileWriter(LOG_PATH, true)) {
                fw.write("Font substitution: " + info.getMessage() + System.lineSeparator());
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
});
```

Lembre‑se de tratar `IOException` adequadamente em código de produção.

### Capturando Vários Documentos em um Loop

Ao processar uma pasta de documentos, você pode reutilizar o mesmo callback:

```java
File[] files = new File("input").listFiles((dir, name) -> name.endsWith(".docx"));
for (File f : files) {
    Document d = new Document(f.getAbsolutePath(), loadOptions);
    // Additional processing...
}
```

Como o callback está anexado ao `loadOptions`, cada iteração registra automaticamente quaisquer eventos de substituição de fonte.

### Lidando com Fontes Incorporadas

O Aspose.Words pode incorporar fontes ausentes se você habilitar essa opção:

```java
loadOptions.setLoadFormat(LoadFormat.DOCX);
loadOptions.setEnableFontSubstitution(true); // default is true
```

Mesmo com a incorporação ativada, o callback de aviso ainda é disparado, fornecendo visibilidade sobre o que foi substituído.

---

## Exemplo Completo Funcional

Abaixo está o programa completo, pronto para ser executado. Copie‑o para uma classe chamada `FontSubstitutionDiagnostics.java`, ajuste o caminho do arquivo e execute.

```java
import com.aspose.words.*;

import java.io.FileWriter;
import java.io.IOException;

/**
 * Demonstrates how to log font substitution warnings using Aspose.Words for Java.
 */
public class FontSubstitutionDiagnostics {

    // Optional: path to a persistent log file
    private static final String LOG_FILE = "font_substitution_log.txt";

    public static void main(String[] args) throws Exception {
        // 1️⃣ Create LoadOptions to capture warnings
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Register a warning callback that logs only font‑substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    String message = "Font substitution: " + info.getMessage();
                    // Log to console
                    System.out.println(message);
                    // Also append to a file (optional)
                    try (FileWriter fw = new FileWriter(LOG_FILE, true)) {
                        fw.write(message + System.lineSeparator());
                    } catch (IOException e) {
                        // In a real app, use a proper logging framework
                        e.printStackTrace();
                    }
                }
            }
        });

        // 3️⃣ Load the document with the configured LoadOptions
        Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);

        // 4️⃣ Continue normal processing – e.g., print section count
        System.out.println("Document has " + doc.getSections().getCount() + " sections.");
    }
}
```

**Saída esperada** (supondo que o documento de origem referencie uma fonte ausente):

```
Font substitution: Font 'Times New Roman' was not found. Substituted with 'Arial'.
Document has 3 sections.
```

Tanto o console quanto o `font_substitution_log.txt` conterão o aviso, proporcionando um registro confiável.

---

## Conclusão

Acabamos de mostrar como **registrar avisos de substituição de fonte** em Java usando Aspose.Words. Ao configurar `LoadOptions`, conectar um `IWarningCallback` e carregar o documento, você obtém total visibilidade sobre quaisquer eventos de fontes ausentes que poderiam passar despercebidos. A partir daqui, você pode:

- Direcionar avisos para um serviço central de logging.
- Disparar alertas em pipelines de controle de qualidade.
- Combinar essa técnica com outras estratégias de **carregamento de documentos**, como conversão para PDF ou mesclagem de correspondência.

Sinta‑se livre para experimentar — troque o logger de console por SLF4J, adicione timestamps ou até envie alertas para um painel de monitoramento. O padrão central permanece o mesmo, e agora você tem uma base sólida para um tratamento robusto de fontes em qualquer fluxo de trabalho de documentos baseado em Java.

Tem alguma variação que gostaria de compartilhar? Talvez você já tenha integrado isso ao Spring Boot ou a uma função em nuvem. Deixe um comentário abaixo e vamos manter a conversa fluindo. Boa codificação!

## O Que Você Deve Aprender a Seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas em seus próprios projetos.

- [Capturar Avisos de Substituição de Fonte em Java com Aspose.Words – Guia Completo](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Usando Opções e Configurações de Documento no Aspose.Words para Java](/words/english/java/document-manipulation/using-document-options-and-settings/)
- [Habilitar Avisos de Substituição de Fonte no Aspose.Words – Guia Completo](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}