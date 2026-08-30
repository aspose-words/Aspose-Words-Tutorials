---
category: general
date: 2026-06-24
description: como lidar com avisos ao processar arquivos Word em Java. Aprenda a capturar
  fontes, imprimir mensagens de fontes e lidar com fontes ausentes de forma suave.
draft: false
keywords:
- how to handle warnings
- how to capture fonts
- print font messages
- handle missing fonts
language: pt
og_description: como lidar com avisos no Aspose.Words para Java. Este guia mostra
  como capturar fontes, imprimir mensagens de fontes e gerenciar fontes ausentes de
  forma eficiente.
og_title: como lidar com avisos no Aspose.Words – Tutorial completo de Java
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: how to handle warnings when processing Word files in Java. Learn how
    to capture fonts, print font messages, and handle missing fonts smoothly.
  headline: how to handle warnings in Aspose.Words for Java – Full Guide
  type: TechArticle
- description: how to handle warnings when processing Word files in Java. Learn how
    to capture fonts, print font messages, and handle missing fonts smoothly.
  name: how to handle warnings in Aspose.Words for Java – Full Guide
  steps:
  - name: The document actually references a missing font.
    text: The document actually references a missing font.
  - name: The path to `input.docx` is correct.
    text: The path to `input.docx` is correct.
  - name: You’re using a recent version of Aspose.Words (older builds sometimes suppress
      certain warnings).
    text: You’re using a recent version of Aspose.Words (older builds sometimes suppress
      certain warnings).
  type: HowTo
tags:
- Aspose.Words
- Java
- Font Substitution
title: como lidar com avisos no Aspose.Words para Java – Guia Completo
url: /pt/java/document-rendering/how-to-handle-warnings-in-aspose-words-for-java-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como lidar com avisos no Aspose.Words para Java – Guia Completo

Já se perguntou **como lidar com avisos** que aparecem quando você carrega um documento Word com Aspose.Words? Talvez você tenha visto mensagens crípticas sobre fontes ausentes e pensado: “Ótimo, meu PDF ficou deslocado—e agora?” Você não está sozinho. Em muitos projetos do mundo real, avisos de substituição de fontes são os culpados silenciosos que arruinam a fidelidade do layout.

Neste tutorial, vamos percorrer uma solução prática: registrar um callback de aviso, detectar alertas relacionados a fontes e **imprimir mensagens de fontes** para que você possa decidir se incorpora um fallback ou envia um arquivo de fonte personalizado. Ao final, você saberá **como capturar fontes**, lidar graciosamente com **fontes ausentes** e manter seu pipeline de conversão de documentos sólido como uma rocha.

## O que você aprenderá

- O propósito dos callbacks de aviso do Aspose.Words.
- Como detectar e filtrar avisos de *substituição de fonte*.
- Formas de registrar ou exibir **mensagens de impressão de fontes** para depuração.
- Estratégias para **lidar com fontes ausentes** em ambientes de produção.
- Um exemplo Java completo e pronto‑para‑executar que você pode inserir em qualquer projeto Maven ou Gradle.

### Pré-requisitos

- Java 8 ou superior (o código também funciona com JDK 11).
- Biblioteca Aspose.Words for Java (baixe do site da Aspose ou adicione a dependência Maven/Gradle).
- Um exemplo `input.docx` que referencia uma fonte que você não tem instalada localmente (perfeito para testar o callback).

---

## Etapa 1: Configurar seu projeto e importar o Aspose.Words

Antes de poder **lidar com avisos**, você precisa de um projeto Java que conheça o Aspose.Words. Se você estiver usando Maven, adicione este trecho ao seu `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version> <!-- Use the latest stable version -->
</dependency>
```

Para Gradle, o equivalente é:

```gradle
implementation 'com.aspose:aspose-words:23.10'
```

Depois que a dependência for resolvida, importe as classes necessárias no seu arquivo fonte Java:

```java
import com.aspose.words.*;
```

> **Dica profissional:** Mantenha suas bibliotecas Aspose atualizadas. Novas versões frequentemente melhoram o tratamento de avisos e adicionam detalhes mais ricos ao `WarningInfo`.

---

## Etapa 2: Carregar o documento Word e registrar um callback de aviso

Agora que a biblioteca está no classpath, podemos **capturar fontes** que o motor substitui. A chave é `Document.setWarningCallback`, que aceita qualquer implementação de `IWarningCallback`. Abaixo está um exemplo conciso, porém completo, que imprime cada aviso de substituição de fonte no console.

```java
public class FontWarningDemo {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the Word document (replace with your actual path)
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Register the warning callback – this is where we **handle warnings**
        document.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo warningInfo) {
                // Filter only font‑substitution warnings
                if (warningInfo.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    // 3️⃣ **Print font messages** – you could also log to a file or monitoring system
                    System.out.println("Font substitution detected: " + warningInfo.getDescription());
                }
                // Optional: handle other warning types here
            }
        });

        // Trigger the warning processing by saving or converting the document
        // For demonstration, we’ll just save to PDF (you could save to any format)
        document.save("output.pdf");
    }
}
```

### Por que isso funciona

- **`Document.setWarningCallback`** informa ao Aspose.Words para invocar seu código sempre que encontrar uma situação que justifique um aviso.
- **`WarningInfo.getWarningType()`** nos permite discriminar entre diferentes categorias (por exemplo, `FONT_SUBSTITUTION`, `DEPRECATED_FEATURE`). Ao focar em `FONT_SUBSTITUTION` nós **lidamos com fontes ausentes** sem poluir o log.
- A linha `System.out.println` **imprime mensagens de fontes** em tempo real, o que é inestimável durante o desenvolvimento ou ao solucionar problemas em um pipeline de produção.

---

## Etapa 3: Testar o callback com uma fonte ausente

Para confirmar que nosso callback realmente **captura fontes**, crie um arquivo Word que use uma fonte não instalada na sua máquina—por exemplo, “Comic Sans MS” em um servidor Linux que só tem “DejaVu Sans”. Quando você executar a demonstração, deverá ver uma saída semelhante a:

```
Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Se você não vir nenhuma mensagem, verifique novamente:

1. O documento realmente referencia uma fonte ausente.
2. O caminho para `input.docx` está correto.
3. Você está usando uma versão recente do Aspose.Words (construções mais antigas às vezes suprimem certos avisos).

---

## Etapa 4: Manipulação avançada – Incorporar fontes de fallback

Imprimir um aviso é ótimo, mas em um sistema de produção você pode querer **lidar com fontes ausentes** automaticamente. Uma abordagem comum é incorporar uma fonte de fallback (por exemplo, “Liberation Sans”) antes de salvar. Veja como você pode estender o callback para substituir a fonte ausente programaticamente:

```java
document.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo warningInfo) {
        if (warningInfo.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            String missingFont = warningInfo.getDescription()
                .replaceAll(".*'([^']+)'.*", "$1"); // extract the font name
            System.out.println("Missing font: " + missingFont);

            // Load a fallback font from resources or a known location
            FontSettings fontSettings = document.getFontSettings();
            fontSettings.setSubstitutionSettings(new FontSubstitutionSettings() {{
                getTableSubstitution().addSubstitutes(missingFont, new String[]{"Liberation Sans"});
            }});
        }
    }
});
```

**O que está acontecendo?**

- Analisamos a descrição do aviso para extrair o nome da fonte ausente.
- Usando `FontSettings`, informamos ao Aspose.Words para substituir *qualquer* ocorrência dessa fonte por “Liberation Sans”.
- Na próxima vez que o documento for renderizado ou salvo, o fallback será aplicado silenciosamente.

> **Atenção:** O uso excessivo de substituição automática pode mascarar problemas reais de design. É melhor registrar a substituição (como já **imprimimos mensagens de fontes**) e revisar a saída manualmente durante o QA.

---

## Etapa 5: Registro ao invés de impressão – Tornando pronto para produção

Em um pipeline CI/CD você provavelmente não quer saída no console. Troque o `System.out.println` por um logger adequado (por exemplo, SLF4J). Aqui está uma adaptação rápida:

```java
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

// ...

private static final Logger logger = LoggerFactory.getLogger(FontWarningDemo.class);

// Inside the callback:
logger.warn("Font substitution: {}", warningInfo.getDescription());
```

Agora seus avisos se integram com as ferramentas de agregação de logs existentes (ELK, Splunk, etc.), facilitando **lidar com fontes ausentes** em vários jobs.

---

## Etapa 6: Armadilhas comuns e como evitá‑las

| Armadilha | Por que acontece | Correção |
|-----------|------------------|----------|
| Nenhum aviso aparece | A fonte realmente existe no sistema, ou o documento usa fontes incorporadas. | Verifique se o documento de teste realmente referencia uma fonte indisponível. |
| Callback não invocado | `setWarningCallback` chamado **depois** que o documento já foi carregado. | Registre o callback **antes** de qualquer operação que possa disparar avisos (por exemplo, antes de `Document.save`). |
| Múltiplos avisos inundam o log | Documentos grandes geram muitas substituições. | Adicione um mecanismo de limitação ou agregue mensagens antes de registrar. |
| Substituição não se aplica | `FontSettings` não está vinculado à instância do documento. | Certifique-se de definir o `FontSettings` no mesmo objeto `Document` que está sendo salvo. |

---

## Etapa 7: Exemplo completo, pronto‑para‑executar

Abaixo está o programa completo, pronto para copiar e colar. Ele inclui importações, o callback, registro e uma estratégia de fonte de fallback.

```java
import com.aspose.words.*;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

public class FontWarningDemo {

    private static final Logger logger = LoggerFactory.getLogger(FontWarningDemo.class);

    public static void main(String[] args) throws Exception {
        // Load the document – adjust the path as needed
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // Register warning callback to capture and log font substitution warnings
        document.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo warningInfo) {
                if (warningInfo.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    // Extract missing font name (optional, for advanced handling)
                    String missingFont = warningInfo.getDescription()
                        .replaceAll(".*'([^']+)'.*", "$1");

                    // Log the warning – this **prints font messages** in your log files
                    logger.warn("Font substitution detected: {}", warningInfo.getDescription());

                    // OPTIONAL: automatically substitute with a known fallback
                    FontSettings fontSettings = document.getFontSettings();
                    fontSettings.setSubstitutionSettings(new FontSubstitutionSettings() {{
                        getTableSubstitution().addSubstitutes(missingFont, new String[]{"Liberation Sans"});
                    }});
                }
            }
        });

        // Save to PDF (or any other format). This triggers the warning processing.
        document.save("output.pdf");
        logger.info("Document conversion completed. Check logs for any font substitution warnings.");
    }
}
```

**Saída esperada no console/log** (supondo que “Comic Sans MS” esteja ausente):

```
WARN  FontWarningDemo - Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
INFO  FontWarningDemo - Document conversion completed. Check logs for any font substitution warnings.
```

O `output.pdf` resultante usará “Liberation Sans” onde “Comic Sans MS” foi referenciado, graças à substituição automática que adicionamos.

---

## Conclusão

Acabamos de cobrir **como lidar com avisos** no Aspose.Words para Java do início ao fim. Ao registrar um callback de aviso, filtrar alertas de **substituição de fonte** e **imprimir mensagens de fontes**, você obtém total visibilidade sobre cenários de fontes ausentes. Adicionar um fallback via `FontSettings` permite **lidar com fontes ausentes** sem intervenção manual, enquanto um framework de registro adequado torna a solução pronta para produção.

Próximos passos? Experimente combinar esta abordagem com o Aspose.PDF para verificar se as fontes incorporadas sobrevivem à conversão, ou explore os outros tipos de aviso (por exemplo, `DEPRECATED_FEATURE`) para tornar seu código à prova de futuro. E se você estiver curioso sobre **como capturar fontes** de um bucket de armazenamento remoto

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Capturar avisos de substituição de fontes em Java com Aspose.Words – Guia Completo](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Como detectar fontes no Aspose.Words – Lidar com avisos e configurações](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Como capturar fontes no Aspose.Words – Guia Completo](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}