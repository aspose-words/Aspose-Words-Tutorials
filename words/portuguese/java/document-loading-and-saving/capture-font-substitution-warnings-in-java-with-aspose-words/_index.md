---
category: general
date: 2026-01-11
description: Aprenda a capturar avisos de substituição de fontes usando Aspose.Words
  para Java. Este tutorial passo a passo também aborda LoadOptions e callbacks de
  aviso.
draft: false
keywords:
- capture font substitution warnings
- Aspose.Words font substitution
- Java warning callback
- LoadOptions usage
- document loading warnings
language: pt
og_description: Capture avisos de substituição de fontes com Aspose.Words para Java.
  Siga este guia para configurar LoadOptions e um callback de aviso para um carregamento
  de documento confiável.
og_title: Capturar Avisos de Substituição de Fonte em Java – Tutorial Completo
tags:
- Aspose.Words
- Java
- Document Processing
title: Captura de Avisos de Substituição de Fonte em Java com Aspose.Words – Guia
  Completo
url: /pt/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Capturar Avisos de Substituição de Fonte – Tutorial Completo em Java

Já precisou **capturar avisos de substituição de fonte** ao abrir um documento Word com fontes ausentes? É uma dor de cabeça comum, especialmente quando você gera PDFs ou imprime em um servidor que não tem todas as tipografias instaladas. A boa notícia? Aspose.Words for Java torna isso simples — basta configurar um objeto `LoadOptions` e conectar um callback de aviso. Neste guia você verá exatamente como fazer isso, por que isso importa e o que esperar quando o aviso é disparado.

Também abordaremos tópicos relacionados como **substituição de fonte do Aspose.Words**, uso de um **callback de aviso em Java** e boas práticas para **uso do LoadOptions**. Ao final, você terá um trecho pronto‑para‑executar que registra cada evento de fonte ausente, para que seu processamento posterior nunca lhe surpreenda.

## Pré‑requisitos

Antes de mergulharmos, certifique‑se de que você tem:

- Java 17 (ou qualquer JDK recente) instalado e configurado.  
- Aspose.Words for Java 23.10 (ou mais recente) no seu classpath.  
- Um documento Word que faça referência a uma fonte que você não possui localmente (por exemplo, `DocWithMissingFont.docx`).  
- Familiaridade básica com blocos `try/catch` em Java — nada sofisticado.

Se algum desses itens lhe for desconhecido, faça uma pausa e instale a biblioteca a partir do Maven Central:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
</dependency>
```

Agora que a base está pronta, vamos ao código.

## Etapa 1: Configurar um Callback de Aviso para **Capturar Avisos de Substituição de Fonte**

A primeira coisa que você precisa é um callback que o Aspose.Words invocará sempre que encontrar uma fonte ausente. É aqui que **capturamos avisos de substituição de fonte**. O callback implementa a interface `IWarningCallback` e verifica o `WarningType`.

```java
import com.aspose.words.*;

public class FontSubstitutionInfo {

    // Custom callback that prints details of each font substitution warning
    private static class FontWarningCallback implements IWarningCallback {
        @Override
        public void warning(WarningInfo info) {
            // Only act on font‑substitution warnings
            if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                System.out.println("Font substitution warning:");
                System.out.println("  Original font: " + info.getSource());
                System.out.println("  Substituted by: " + info.getDescription());
            }
        }
    }

    public static void main(String[] args) throws Exception {
        // Code continues in the next steps...
    }
}
```

**Por que isso importa:** Sem um callback, o Aspose.Words troca silenciosamente a fonte ausente por uma padrão, e você nunca sabe que a saída visual mudou. Ao capturar o aviso, você pode registrar, alertar ou até abortar o carregamento se a fonte ausente for crítica.

## Etapa 2: Configurar **LoadOptions** e Registrar o Callback

Agora criamos uma instância de `LoadOptions` e anexamos nosso `FontWarningCallback`. Esta etapa é essencial para **uso do LoadOptions** e garante que todo carregamento de documento passe pelo mesmo filtro de avisos.

```java
public static void main(String[] args) throws Exception {
    // Step 2: Prepare LoadOptions and hook the warning callback
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new FontWarningCallback());

    // Continue to load the document in the next step...
}
```

**Dica:** Você pode reutilizar o mesmo objeto `LoadOptions` para vários documentos, o que economiza algumas linhas de código repetitivo e garante tratamento consistente de **avisos de carregamento de documento** em toda a sua aplicação.

## Etapa 3: Carregar o Documento e Observar a Saída

Com o callback conectado, basta carregar seu arquivo Word. Se o documento fizer referência a uma fonte que não está instalada, o callback será disparado e imprimirá detalhes no console.

```java
    // Step 3: Load the document using the configured LoadOptions
    Document doc = new Document("YOUR_DIRECTORY/DocWithMissingFont.docx", loadOptions);

    // Step 4: Confirm that the load completed
    System.out.println("Document loaded; check console for any font‑substitution warnings.");
}
```

### Saída Esperada no Console

Assumindo que `DocWithMissingFont.docx` referencia a fonte ausente *“Comic Sans MS”*, você verá algo como:

```
Font substitution warning:
  Original font: Comic Sans MS
  Substituted by: Arial
Document loaded; check console for any font‑substitution warnings.
```

Se o documento **não contiver fontes ausentes**, o console mostrará apenas a linha final, confirmando que seu callback não gerou falsos positivos.

## Etapa 4: Tratando Casos Limite e Armadilhas Comuns

### Múltiplas Fontes Ausentes

Se um documento usar várias fontes indisponíveis, o callback será executado uma vez por fonte. Você receberá uma série de mensagens, cada uma com seu próprio `source` e `description`. Nenhum código extra é necessário — apenas garanta que seu sistema de registro consiga lidar com chamadas sucessivas rápidas.

### Suprimindo Avisos

Em casos raros você pode querer ignorar certas substituições (por exemplo, sabe que um fallback específico é aceitável). Amplie a lógica do callback:

```java
if (info.getWarningType() == WarningType.FONT_SUBSTITUTION &&
    !info.getSource().equalsIgnoreCase("SomeFontYouAccept")) {
    // Log or act on the warning
}
```

### Segurança em Threads

`LoadOptions` do Aspose.Words não é thread‑safe por padrão. Se você estiver carregando documentos em paralelo, crie uma instância separada de `LoadOptions` por thread, ou sincronize o callback para evitar condições de corrida.

## Etapa 5: Verificando a Fonte Substituída no Documento Resultante

Após o carregamento, pode ser útil confirmar que a substituição realmente ocorreu. A API permite iterar sobre todas as *runs* e inspecionar o nome da fonte efetiva:

```java
for (Run run : (Iterable<Run>) doc.getFirstSection().getBody().getChildNodes(NodeType.RUN, true)) {
    System.out.println("Run text: \"" + run.getText() + "\" uses font: " + run.getFont().getName());
}
```

Este trecho imprime cada *run* de texto com sua fonte final. É uma verificação prática quando você está construindo pipelines automatizados de conversão para PDF.

## Exemplo Completo Funcional

Juntando tudo, aqui está o programa completo, pronto‑para‑executar:

```java
import com.aspose.words.*;

public class FontSubstitutionInfo {

    private static class FontWarningCallback implements IWarningCallback {
        @Override
        public void warning(WarningInfo info) {
            if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                System.out.println("Font substitution warning:");
                System.out.println("  Original font: " + info.getSource());
                System.out.println("  Substituted by: " + info.getDescription());
            }
        }
    }

    public static void main(String[] args) throws Exception {
        // Prepare LoadOptions and register the warning callback
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new FontWarningCallback());

        // Load the document (replace with your actual path)
        Document doc = new Document("YOUR_DIRECTORY/DocWithMissingFont.docx", loadOptions);

        // Optional: verify effective fonts in the document
        for (Run run : (Iterable<Run>) doc.getFirstSection().getBody().getChildNodes(NodeType.RUN, true)) {
            System.out.println("Run text: \"" + run.getText() + "\" uses font: " + run.getFont().getName());
        }

        System.out.println("Document loaded; check console for any font‑substitution warnings.");
    }
}
```

Salve como `FontSubstitutionInfo.java`, compile com `javac` e execute `java FontSubstitutionInfo`. Você deverá ver as mensagens de aviso (se houver) seguidas da lista de *runs* e suas fontes finais.

## Ajuda Visual

![Captura de tela da saída do console mostrando avisos de substituição de fonte](/images/font-substitution-warning.png "exemplo de captura de avisos de substituição de fonte")

*Texto alternativo:* **captura de avisos de substituição de fonte** – saída do console após carregar um documento com fontes ausentes.

## Conclusão

Agora você sabe como **capturar avisos de substituição de fonte** usando Aspose.Words for Java. Ao configurar um objeto `LoadOptions` e fornecer um `IWarningCallback` personalizado, você obtém total visibilidade sobre quaisquer eventos de fonte ausente que poderiam, de outra forma, afetar silenciosamente a aparência do seu documento. Essa técnica se integra diretamente ao **manuseio de substituição de fonte do Aspose.Words**, garante avisos confiáveis de **carregamento de documento** e oferece flexibilidade para registrar, alertar ou abortar conforme suas regras de negócio.

### O que vem a seguir?

- Explore padrões de **callback de aviso em Java** para outros tipos de aviso (por exemplo, `DEPRECATED_FEATURE`).  
- Combine esta abordagem com **conversão para PDF** para garantir que fontes substituídas não quebrem o layout.  
- Aprofunde‑se no **uso do LoadOptions** — experimente `Password`, `Encoding` e `ResourceLoadingCallback` para cenários mais avançados.

Sinta‑se à vontade para ajustar o callback, encaminhar avisos para um framework de logging ou até lançar uma exceção personalizada se uma fonte crítica estiver ausente. O céu é o limite, e agora você tem uma base sólida para construir.

Feliz codificação, e que seus documentos sempre sejam renderizados exatamente como você espera!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}