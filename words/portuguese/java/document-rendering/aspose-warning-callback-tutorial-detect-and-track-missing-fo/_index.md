---
category: general
date: 2026-03-17
description: Aprenda o tutorial de callback de aviso do Aspose para detectar fontes
  ausentes e rastrear fontes ausentes em documentos Java com um exemplo completo e
  executável.
draft: false
keywords:
- aspose warning callback tutorial
- detect missing fonts
- track missing fonts
language: pt
og_description: Domine o tutorial de callback de aviso do Aspose para detectar fontes
  ausentes e rastrear fontes ausentes no seu fluxo de trabalho de processamento de
  Word em Java.
og_title: Tutorial de callback de aviso do Aspose – Detectar fontes ausentes
tags:
- Aspose.Words
- Java
- Font Substitution
- Document Processing
title: Tutorial de callback de aviso do Aspose – Detectar e rastrear fontes ausentes
url: /pt/java/document-rendering/aspose-warning-callback-tutorial-detect-and-track-missing-fo/
---

next steps.

- Closing shortcodes.

Make sure to keep markdown formatting.

Let's craft translation.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# tutorial de callback de aviso do aspose – Detectar e Rastrear Fontes Ausentes

Já se perguntou como **detectar fontes ausentes** ao converter ou editar arquivos Word com Aspose.Words? Você não está sozinho. Em muitos projetos reais, uma fonte fora do lugar pode causar falhas de layout, e você precisa de uma forma confiável de **rastrear fontes ausentes** antes que elas causem problemas mais tarde.  

A boa notícia? O **aspose warning callback tutorial** oferece um hook programático limpo que imprime exatamente esses avisos de substituição de fonte à medida que ocorrem. Neste guia vamos percorrer a configuração do callback, o carregamento de um documento e a visualização dos avisos em ação — tudo em Java.

Ao final deste artigo você será capaz de identificar fontes ausentes automaticamente, registrá‑las e decidir se incorpora uma substituta ou ajusta seus arquivos de origem. Nenhuma ferramenta externa necessária.

## Pré-requisitos

- **Java 8+** (o código compila com qualquer JDK recente)
- **Aspose.Words for Java** versão 23.10 ou mais nova – faça o download no portal da Aspose ou adicione a dependência Maven.
- Um DOCX de exemplo que intencionalmente referencia uma fonte que você não tem instalada (por exemplo, “Comic Sans MS” em um ambiente Linux).

É só isso — sem bibliotecas extras, sem etapas de build complexas.

## Etapa 1: Registrar um Callback de Aviso – O Núcleo do aspose warning callback tutorial

A primeira coisa que o tutorial ensina é como anexar um listener de aviso. Aspose.Words gera um objeto `WarningInfo` para cada problema encontrado, e a bandeira `WarningSource.FONT_SUBSTITUTION` indica exatamente quando uma fonte está sendo substituída.

```java
import com.aspose.words.*;

public class FontDiagnostics {
    public static void main(String[] args) throws Exception {

        // Step 1: Register a warning callback to capture font substitution warnings.
        Document.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // We only care about font‑substitution events.
                if (info.getSource() == WarningSource.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution warning:");
                    System.out.println("  Original:   " + info.getDescription());
                    System.out.println("  Substituted:" + info.getAdditionalInfo());
                }
            }
        });
```

**Por que isso importa:** Sem o callback, Aspose substitui silenciosamente fontes ausentes, e você nunca saberá quais glifos podem ficar errados. Ao registrar o aviso, você pode **detectar fontes ausentes** cedo e decidir se incorpora a correta.

> **Dica profissional:** Se precisar coletar avisos para relatório posterior, armazene‑os em um `List<WarningInfo>` ao invés de imprimi‑los diretamente.

## Etapa 2: Carregar o Documento – Onde fontes ausentes podem se esconder

Agora carregamos o DOCX que pode estar referenciando fontes que não estão presentes na máquina. O ato de carregar aciona o callback de aviso caso alguma fonte esteja ausente.

```java
        // Step 2: Load a document that may contain missing fonts.
        Document document = new Document("YOUR_DIRECTORY/input.docx");
```

**O que está acontecendo nos bastidores?** Aspose analisa as definições de estilo do documento, varre cada trecho de texto e verifica o repositório de fontes do sistema. Quando não encontra a correspondência exata, recorre a um substituto e dispara o aviso que acabamos de conectar.

## Etapa 3: Salvar o Documento – Liberando os avisos

Por fim, salvamos o documento. A operação de salvamento também reavalia as fontes, de modo que quaisquer avisos que não foram emitidos durante o carregamento aparecerão agora.

```java
        // Step 3: Save the document; any font substitution warnings will be printed by the callback.
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

Ao executar o programa, você verá uma saída no console semelhante a:

```
Font substitution warning:
  Original:   Font "Comic Sans MS" not found.
  Substituted: Using "Arial" as fallback.
```

Essa saída comprova que o **aspose warning callback tutorial** funciona, e que você **detectou fontes ausentes** e agora está **rastreando fontes ausentes** através do log.

## Como Detectar Fontes Ausentes em um Documento Word – Além do Básico

A abordagem com callback é ótima para execuções pontuais, mas às vezes você precisa de uma utilidade reutilizável. Aqui está um wrapper rápido que pode ser inserido em qualquer projeto:

```java
public class FontMissingChecker {
    private final List<String> missingFonts = new ArrayList<>();

    public FontMissingChecker() {
        Document.setWarningCallback((WarningInfo info) -> {
            if (info.getSource() == WarningSource.FONT_SUBSTITUTION) {
                missingFonts.add(info.getDescription());
            }
        });
    }

    public List<String> check(String path) throws Exception {
        new Document(path); // triggers warnings
        return missingFonts;
    }
}
```

Chame‑o assim:

```java
FontMissingChecker checker = new FontMissingChecker();
List<String> fonts = checker.check("input.docx");
if (!fonts.isEmpty()) {
    System.out.println("Missing fonts detected:");
    fonts.forEach(System.out::println);
}
```

Agora você tem um método reutilizável de **detect missing fonts** que devolve uma lista que pode ser alimentada a um pipeline CI ou a uma interface de usuário.

## Rastreando Fontes Ausentes com Aspose.Words – Relatórios para Equipes

Em equipes maiores, pode ser útil gerar um relatório CSV de todas as fontes ausentes em vários documentos. Combine a utilidade anterior com iteração simples de arquivos:

```java
import java.nio.file.*;
import java.io.*;

public class BulkFontReporter {
    public static void main(String[] args) throws Exception {
        Path folder = Paths.get("YOUR_DIRECTORY");
        try (BufferedWriter writer = Files.newBufferedWriter(folder.resolve("missing-fonts-report.csv"))) {
            writer.write("Document,Missing Font\n");
            Files.list(folder)
                 .filter(p -> p.toString().endsWith(".docx"))
                 .forEach(p -> {
                     try {
                         FontMissingChecker checker = new FontMissingChecker();
                         List<String> missing = checker.check(p.toString());
                         for (String msg : missing) {
                             // Extract font name from description
                             String font = msg.replaceAll("Font \"(.*?)\".*", "$1");
                             writer.write(p.getFileName() + "," + font + "\n");
                         }
                     } catch (Exception e) {
                         // In a real app, log the error
                     }
                 });
        }
        System.out.println("Report generated at missing-fonts-report.csv");
    }
}
```

Executar este script gerará um CSV de **track missing fonts** que todo desenvolvedor pode consultar antes de enviar um documento para produção.

## Armadilhas Comuns & Como Evitá‑las

| Armadilha | Por que acontece | Solução |
|-----------|------------------|---------|
| **Callback não dispara** | Você esqueceu de definir o callback **antes** de carregar o documento. | Coloque `Document.setWarningCallback` no início do `main`. |
| **Aparece apenas o primeiro aviso** | Aspose mantém cache de avisos por instância de `Document`. | Use um novo objeto `Document` para cada arquivo, ou redefina o callback entre execuções. |
| **Nome da fonte errado no log** | A descrição contém texto extra (“Font … not found”). | Remova usando regex como mostrado no exemplo CSV. |
| **Impacto de desempenho em lotes grandes** | O callback roda em cada trecho de texto, o que pode ser custoso. | Limite a verificação a uma etapa pré‑voo; pule o salvamento se precisar apenas da detecção. |

## Resultados Esperados & Verificação

1. **Saída no console** – Você deve ver ao menos uma linha “Font substitution warning” para cada fonte ausente.  
2. **Relatório CSV** – Após o script em lote terminar, abra `missing-fonts-report.csv` e verifique se cada linha lista o nome do documento e a fonte ausente exata.  
3. **Documento salvo** – O DOCX de saída será renderizado usando as fontes de substituição, mas o layout visual pode diferir do original.

Se algum desses passos não se comportar como descrito, verifique se o JAR do Aspose.Words está no seu classpath e se o `input.docx` realmente referencia uma fonte ausente no seu SO.

## Conclusão

Você acabou de concluir um **aspose warning callback tutorial** que demonstra como **detectar fontes ausentes** e **rastrear fontes ausentes** em aplicações Java. Ao registrar um listener de aviso, carregar o documento e, opcionalmente, exportar os resultados, você obtém total visibilidade sobre problemas relacionados a fontes antes que eles apareçam em produção.

Próximos passos sugeridos:

- Incorporar a fonte ausente diretamente com `LoadOptions.setFontSubstitution`.  
- Usar a classe `FontSettings` para mapear fontes ausentes a substitutos específicos.  
- Integrar o relatório CSV em um pipeline CI/CD para falhar builds quando fontes não documentadas aparecerem.

Teste, ajuste os callbacks para se adequar ao seu framework de logging e veja seu fluxo de documentos se tornar muito mais robusto. Boa codificação!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}