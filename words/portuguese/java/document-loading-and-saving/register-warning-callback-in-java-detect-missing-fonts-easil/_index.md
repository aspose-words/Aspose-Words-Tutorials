---
category: general
date: 2026-07-03
description: Registre o callback de aviso em Java para detectar fontes ausentes ao
  processar documentos Word. Aprenda o tratamento de avisos do Aspose.Words e a detecção
  de substituição de fontes.
draft: false
keywords:
- register warning callback
- detect missing fonts
- font substitution warning
- Aspose.Words warning callback
- Java missing font detection
- document font handling
language: pt
og_description: Registre o callback de aviso em Java para detectar fontes ausentes.
  Este guia mostra como capturar avisos de substituição de fontes com Aspose.Words.
og_title: Registrar callback de aviso em Java – Detectar fontes ausentes
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Register warning callback in Java to detect missing fonts while processing
    Word docs. Learn Aspose.Words warning handling and font substitution detection.
  headline: Register warning callback in Java – Detect missing fonts easily
  type: TechArticle
- description: Register warning callback in Java to detect missing fonts while processing
    Word docs. Learn Aspose.Words warning handling and font substitution detection.
  name: Register warning callback in Java – Detect missing fonts easily
  steps:
  - name: Why this matters
    text: '* **Visibility:** Without a callback, the substitution happens silently,
      and you might ship a document with the wrong appearance. * **Automation:** In
      batch pipelines you can log every missing‑font incident and later feed the list
      to a font‑installation script. * **Compliance:** Some industries (e.g'
  - name: Expected console output
    text: 'Assuming `input.docx` references the font *“Comic Sans MS”* which isn’t
      installed, you’ll see something like:'
  - name: Multiple missing fonts
    text: If a document references several unavailable fonts, the callback will fire
      once per font. You can aggregate the messages into a list if you need a summary
      report later.
  - name: Controlling substitution behavior
    text: 'Sometimes you *do* want to force a particular fallback font. Use `FontSettings`
      before loading the document:'
  - name: Performance considerations
    text: 'Registering a warning callback introduces a tiny overhead—only a few nanoseconds
      per warning. In high‑throughput services (e.g., converting thousands of docs
      per hour) the impact is negligible. However, if you’re processing millions,
      consider disabling warnings after you’ve verified the font set is '
  - name: Cross‑platform notes
    text: The callback works identically on Windows, macOS, and Linux. The only difference
      is the set of fonts available on each OS. If you run the same job on multiple
      agents, you might see different substitution messages. To keep results deterministic,
      ship a **custom font folder** and point Aspose.Words to
  type: HowTo
tags:
- Aspose.Words
- Java
- Fonts
title: Registrar callback de aviso em Java – Detecte fontes ausentes facilmente
url: /pt/java/document-loading-and-saving/register-warning-callback-in-java-detect-missing-fonts-easil/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Registrar callback de aviso em Java – Detecte fontes ausentes facilmente

Já se perguntou como **registrar um callback de aviso** para **detectar fontes ausentes** ao converter ou editar documentos Word? Você não está sozinho. Fontes ausentes podem corromper silenciosamente os layouts, transformar um relatório elegante em uma bagunça confusa, e a maioria dos desenvolvedores nem percebe até que o PDF final fique errado.  

Neste tutorial vamos percorrer um exemplo completo, pronto‑para‑executar, que mostra exatamente como conectar ao sistema de avisos do Aspose.Words for Java, capturar esses incômodos alertas de substituição de fonte e registrá‑los ou reagir da maneira que precisar. Sem atalhos vagos de “veja a documentação” — apenas código puro, pronto‑para‑copiar‑e‑colar e o raciocínio por trás de cada linha.

## Pré‑requisitos

Antes de mergulharmos, certifique‑se de que você tem:

* **Java 17** (ou qualquer JDK recente) instalado e `JAVA_HOME` configurado.  
* **Aspose.Words for Java** JAR (baixe do site oficial ou obtenha via Maven).  
* Um arquivo `.docx` de exemplo que faça referência a uma fonte **não** instalada na sua máquina — isso disparará o aviso.  
* Seu IDE favorito ou um editor de texto simples e ferramentas de build de linha de comando.

É só isso. Sem frameworks extras, sem serviços externos. Pronto? Vamos começar.

## Etapa 1: Configurar o projeto e adicionar Aspose.Words

Se você usa Maven, adicione a dependência a seguir no seu `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- use the latest stable version -->
</dependency>
```

Para Gradle, insira isto no `build.gradle`:

```groovy
implementation 'com.aspose:aspose-words:24.10'
```

Se preferir o caminho manual, basta colocar o `aspose-words-24.10.jar` no seu classpath.  
**Dica:** mantenha o JAR ao lado da pasta `src`; isso simplifica o comando `javac` mais adiante.

## Etapa 2: Carregar o documento que pode conter fontes ausentes

A primeira coisa que você faz é criar um objeto `Document` apontando para o arquivo fonte. Essa etapa é direta, mas também é onde a biblioteca analisa o arquivo e *potencialmente* descobre fontes ausentes.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {
        // Adjust the path to point at your test document
        String inputPath = "YOUR_DIRECTORY/input.docx";

        // Load the document – Aspose.Words will start parsing it now
        Document doc = new Document(inputPath);
```

Aqui, `Document` é o ponto de entrada para todas as operações do Aspose.Words. Quando o construtor é executado, a biblioteca analisa o XML do documento, resolve as fontes e, se alguma fonte não estiver disponível, *enfileira* um aviso que podemos capturar depois.

## Etapa 3: Registrar um callback de aviso para capturar alertas de substituição de fonte

Agora vem a estrela do show: **registrar callback de aviso**. O Aspose.Words permite que você conecte uma implementação da interface `IWarningCallback`. Cada vez que o motor encontra uma situação que vale a pena sinalizar — como uma fonte ausente — ele invoca seu método `warning`.

```java
        // Register the warning callback
        doc.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // We’re only interested in font substitution warnings
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("⚠️ Font substituted: " + info.getDescription());
                }
            }
        });
```

### Por que isso importa

* **Visibilidade:** Sem um callback, a substituição ocorre silenciosamente, e você pode entregar um documento com aparência errada.  
* **Automação:** Em pipelines em lote você pode registrar cada incidente de fonte ausente e, depois, alimentar a lista a um script de instalação de fontes.  
* **Conformidade:** Alguns setores (por exemplo, jurídico) exigem prova de que as fontes originais foram usadas ou substituídas corretamente.

Observe que filtramos por `WarningType.FONT_SUBSTITUTION`. O Aspose.Words emite muitos tipos de aviso — estouro de layout, recursos obsoletos, etc. — mas nos interessam apenas aqueles que indicam que uma fonte estava faltando. Isso mantém o console limpo e foca no objetivo de **detectar fontes ausentes**.

## Etapa 4: Salvar o documento e deixar o callback disparar

Quando você finalmente chama `save`, o motor finaliza qualquer carregamento preguiçoso e dispara o callback de aviso para cada fonte ausente que descobriu durante a operação de salvamento.

```java
        // Save the document – this is where the warning callback gets invoked
        String outputPath = "YOUR_DIRECTORY/output.docx";
        doc.save(outputPath);

        System.out.println("✅ Document saved to " + outputPath);
    }
}
```

### Saída esperada no console

Supondo que `input.docx` faça referência à fonte *“Comic Sans MS”* que não está instalada, você verá algo como:

```
⚠️ Font substituted: Font 'Comic Sans MS' is not available. Substituted with 'Arial'.
✅ Document saved to YOUR_DIRECTORY/output.docx
```

Se o documento fonte já contiver apenas fontes instaladas, a linha de aviso simplesmente nunca aparecerá — o que significa que **detectar fontes ausentes** foi concluído silenciosamente.

![Saída do console mostrando o registro de callback de aviso em ação e detecção de fontes ausentes](register-warning-callback-output.png)

*Texto alternativo da imagem: saída do callback de aviso mostrando a detecção de fontes ausentes*

## Etapa 5: Tratando casos de borda e dicas de boas práticas

### Múltiplas fontes ausentes

Se um documento referencia várias fontes indisponíveis, o callback será disparado uma vez por fonte. Você pode agregar as mensagens em uma lista caso precise de um relatório resumido depois.

```java
List<String> missingFonts = new ArrayList<>();
doc.setWarningCallback(info -> {
    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
        missingFonts.add(info.getDescription());
    }
});
// After saving
if (!missingFonts.isEmpty()) {
    System.out.println("Missing fonts detected:");
    missingFonts.forEach(System.out::println);
}
```

### Controlando o comportamento de substituição

Às vezes você *quer* forçar uma fonte de fallback específica. Use `FontSettings` antes de carregar o documento:

```java
FontSettings settings = new FontSettings();
settings.setSubstitutionSettings(new FontSubstitutionSettings()
        .addSubstitutes("Comic Sans MS", "Times New Roman"));
doc.setFontSettings(settings);
```

Agora o callback ainda será disparado, mas você sabe exatamente qual fonte será usada.

### Considerações de desempenho

Registrar um callback de aviso introduz uma pequena sobrecarga — apenas alguns nanossegundos por aviso. Em serviços de alta taxa (por exemplo, convertendo milhares de documentos por hora) o impacto é insignificante. Contudo, se você estiver processando milhões, considere desativar os avisos após verificar que o conjunto de fontes está completo:

```java
doc.setWarningCallback(null); // turn off after initial scan
```

### Observações multiplataforma

O callback funciona de forma idêntica no Windows, macOS e Linux. A única diferença são as fontes disponíveis em cada SO. Se você executar o mesmo trabalho em vários agentes, poderá ver mensagens de substituição diferentes. Para manter os resultados determinísticos, distribua uma **pasta de fontes personalizada** e aponte o Aspose.Words para ela via `FontSettings.setFontsFolder("path/to/fonts", true);`.

## Exemplo completo, executável

Abaixo está a classe Java inteira que você pode copiar‑colar em `src/main/java/FontWarningDemo.java`. Ela inclui todas as importações, tratamento de erros e comentários necessários para executá‑la imediatamente.

```java
import com.aspose.words.*;
import java.util.ArrayList;
import java.util.List;

/**
 * Demonstrates how to register a warning callback in Aspose.Words for Java
 * to detect missing fonts during document processing.
 */
public class FontWarningDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Paths – adjust to your environment
        String inputPath = "YOUR_DIRECTORY/input.docx";
        String outputPath = "YOUR_DIRECTORY/output.docx";

        // 2️⃣ Load the document (parsing begins here)
        Document doc = new Document(inputPath);

        // 3️⃣ Optional: set a custom font folder if you ship fonts with your app
        // FontSettings fs = new FontSettings();
        // fs.setFontsFolder("fonts", true);
        // doc.setFontSettings(fs);

        // 4️⃣ Register the warning callback to catch missing‑font warnings
        List<String> missingFonts = new ArrayList<>();
        doc.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    // Log to console
                    System.out.println("⚠️ Font substituted: " + info.getDescription());
                    // Collect for later reporting
                    missingFonts.add(info.getDescription());
                }
            }
        });

        // 5️⃣ Save the document – triggers the callback
        doc.save(outputPath);
        System.out.println("✅ Document saved to " + outputPath);

        // 6️⃣ Post‑save reporting (if any fonts were missing)
        if (!missingFonts.isEmpty()) {
            System.out.println("\nSummary of missing fonts:");
            missingFonts.forEach(System.out::println);
        } else {
            System.out.println("\nNo missing fonts detected.");
        }
    }
}
```

Compilar e executar:

```bash
javac -cp "aspose-words-24.10.jar" FontWarningDemo.java
java -cp ".:aspose-words-24.10.jar" FontWarningDemo
```

Você deverá ver as linhas de aviso (se houver) seguidas da mensagem de sucesso.

## Conclusão

Você acabou de aprender **como registrar um callback de aviso** em Java para **detectar fontes ausentes** ao trabalhar com Aspose.Words. Ao conectar ao sistema de avisos da biblioteca você ganha total visibilidade sobre eventos de substituição de fonte, pode registrá‑los para conformidade e até substituir programaticamente fontes quando necessário.  

A partir daqui você pode explorar:

* **Detectar fontes ausentes** em lote usando um loop ou streams paralelos.  
* Integrar o callback a um framework de logging (SLF4J, Log4j) para relatórios de nível produção.  
* Usar `FontSettings` para impor uma paleta de fontes corporativa e evitar substituições indesejadas.

Experimente — troque o documento de entrada, teste diferentes cenários de fontes ausentes e veja como o callback se comporta. Se encontrar alguma peculiaridade, deixe um comentário abaixo; feliz codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Warning Callback In Word Document](/words/english/net/programming-with-loadoptions/warning-callback/)
- [Aspose Words Java Callback Custom Savings](/words/hindi/java/images-shapes/aspose-words-java-callback-custom-savings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}