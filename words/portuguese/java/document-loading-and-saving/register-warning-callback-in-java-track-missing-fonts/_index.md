---
category: general
date: 2026-05-30
description: Registre um callback de aviso em Java para rastrear fontes ausentes e
  personalizar o carregamento de documentos com Aspose.Words. Aprenda a solução completa
  passo a passo.
draft: false
keywords:
- register warning callback
- track missing fonts
- customize document loading
language: pt
og_description: Registre o callback de aviso em Java para rastrear fontes ausentes
  e personalizar o carregamento de documentos. Guia completo com código e explicações.
og_title: Registrar callback de aviso em Java – Rastrear fontes ausentes
schemas:
- author: Aspose
  dateModified: '2026-05-30'
  description: Register warning callback in Java to track missing fonts and customize
    document loading with Aspose.Words. Learn the full step‑by‑step solution.
  headline: Register warning callback in Java – Track missing fonts
  type: TechArticle
- description: Register warning callback in Java to track missing fonts and customize
    document loading with Aspose.Words. Learn the full step‑by‑step solution.
  name: Register warning callback in Java – Track missing fonts
  steps:
  - name: '**Get real‑time insight** – every `FONT_SUBSTITUTION` warning is delivered
      instantly.'
    text: '**Get real‑time insight** – every `FONT_SUBSTITUTION` warning is delivered
      instantly.'
  - name: '**Log or react** – you could log to a file, raise an alert, or even replace
      the font programmatically.'
    text: '**Log or react** – you could log to a file, raise an alert, or even replace
      the font programmatically.'
  - name: '**Maintain clean output** – knowing which fonts are missing lets you fix
      the source document before publishing.'
    text: '**Maintain clean output** – knowing which fonts are missing lets you fix
      the source document before publishing.'
  type: HowTo
- questions:
  - answer: It’s the interface Aspose.Words uses for all warning types, giving you
      a single entry point for many possible issues.
    question: Why `IWarningCallback`?
  - answer: Aspose.Words only allows one warning handler. If you need to log to both
      a file and the console, implement a composite callback that forwards the warning
      to multiple destinations.
    question: Multiple callbacks?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Font handling
title: Registrar callback de aviso em Java – Rastrear fontes ausentes
url: /pt/java/document-loading-and-saving/register-warning-callback-in-java-track-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Registrar callback de aviso em Java – Rastrear fontes ausentes

Já se perguntou como **rastrear fontes ausentes** ao carregar um documento Word com Aspose.Words for Java? Talvez você tenha visto aquelas substituições silenciosas de fontes e pensado: “O que aconteceu com o meu layout?” A boa notícia é que você não precisa adivinhar. Ao **registrar um callback de aviso**, você pode capturar cada evento de substituição de fonte no momento em que o documento é lido, e também pode **personalizar o carregamento do documento** para se adequar ao seu pipeline.

Neste tutorial vamos percorrer um exemplo do mundo real que mostra exatamente como configurar o callback, por que isso importa e como manter o restante do seu pipeline de processamento limpo. Ao final, você terá uma classe Java pronta para executar que imprime cada aviso de fonte ausente e salva uma cópia processada do documento. Nenhuma referência externa necessária — apenas código puro e executável.

> **O que você receberá:**  
> • Um programa Java completo usando Aspose.Words  
> • Explicações passo a passo de cada linha  
> • Dicas para lidar com casos extremos como arquivos criptografados ou lotes grandes  
> • Um rápido teste de sanidade que você pode executar em qualquer arquivo `.docx`

## Pré‑requisitos

Antes de mergulharmos, certifique‑se de que você tem:

- **Java 17** (ou qualquer JDK recente) instalado e a variável `JAVA_HOME` configurada.  
- **Aspose.Words for Java** JAR no seu classpath. Você pode obter a versão mais recente no repositório Maven Central:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- replace with the newest -->
</dependency>
```

- Um documento Word de exemplo (`input.docx`) que você suspeita conter fontes não instaladas na sua máquina.  
- Uma IDE ou ferramenta de build de linha de comando (Maven/Gradle) com a qual você se sinta confortável.

É só isso. Sem fontes extras, sem serviços adicionais — apenas Java puro e Aspose.Words.

## Por que registrar um callback de aviso?

Pense no **callback de aviso** como uma câmera de segurança para o processo de carregamento do seu documento. Quando o Aspose.Words encontra um glifo ausente, ele não lança uma exceção; ele silenciosamente troca por uma fonte de fallback. Essa substituição silenciosa pode quebrar o layout, especialmente em PDFs ou faturas críticos para a identidade visual. Ao registrar um callback você:

1. **Obter insight em tempo real** – cada aviso `FONT_SUBSTITUTION` é entregue instantaneamente.  
2. **Registrar ou reagir** – você pode registrar em um arquivo, disparar um alerta ou até substituir a fonte programaticamente.  
3. **Manter a saída limpa** – saber quais fontes estão ausentes permite corrigir o documento fonte antes da publicação.

Em resumo, o callback transforma um problema oculto em um problema visível, tornando seu pipeline de documentos muito mais confiável.

## Etapa 1 – Criar `LoadOptions` para personalizar como o documento é carregado

A primeira coisa que fazemos é instanciar `LoadOptions`. Esse objeto é a porta de entrada para cada ajuste de tempo de carregamento que você possa precisar, desde tratamento de senha até nosso recurso de **registrar callback de aviso**.

```java
// Step 1: Prepare LoadOptions for custom loading behavior
LoadOptions loadOptions = new LoadOptions();
```

Por que não chamar simplesmente `new Document("file.docx")`? Porque sem `LoadOptions` você perde a chance de interceptar os eventos de carregamento. `LoadOptions` é o único lugar onde o Aspose.Words permite que você **personalize o carregamento do documento**.

## Etapa 2 – Registrar um callback de aviso para rastrear fontes ausentes

Agora vem a estrela do show: nós **registramos um callback de aviso** que implementa `IWarningCallback`. Dentro do método `warning` filtramos por `WarningType.FONT_SUBSTITUTION` e imprimimos uma mensagem útil.

```java
// Step 2: Register a warning handler that reports font substitution events
loadOptions.setFontSubstitutionWarningHandler(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Only react to font substitution warnings
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("Font substitution detected: " + info.getDescription());
        }
    }
});
```

Alguns pontos a observar:

- **Por que `IWarningCallback`?** É a interface que o Aspose.Words usa para todos os tipos de aviso, oferecendo um ponto de entrada único para diversas possíveis questões.  
- **Filtragem é crucial** – sem a verificação `if` você veria avisos sobre imagens ausentes, recursos obsoletos etc., o que poluiria seus logs.  
- **Segurança de thread** – o callback é executado na mesma thread que carrega o documento, então você pode atualizar estruturas compartilhadas com segurança caso precise agregar resultados posteriormente.

Esse trecho **registra o callback de aviso**, e a partir deste ponto cada evento de fonte ausente será impresso no `stdout`. Este é o núcleo do **rastreio de fontes ausentes**.

## Etapa 3 – Carregar o documento usando o `LoadOptions` configurado

Com o callback em vigor, finalmente carregamos o arquivo. Se o documento referenciar uma fonte que você não possui, o callback será disparado antes que o objeto `Document` seja totalmente construído.

```java
// Step 3: Load the document with our custom LoadOptions
Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

Substitua `YOUR_DIRECTORY` pelo caminho real na sua máquina. O construtor `Document` lê o arquivo, aplica qualquer senha (se você definiu uma em `loadOptions`) e dispara o callback de aviso para cada fonte ausente. Você verá uma saída semelhante a:

```
Font substitution detected: Font 'Calibri' was substituted with 'Arial'.
```

Essa linha prova que você **rastreou fontes ausentes** com sucesso.

## Etapa 4 – Continuar processando o documento (opcional)

Nesta fase você pode manipular o documento como quiser — substituir texto, inserir imagens ou até trocar programaticamente as fontes substituídas. O callback já forneceu uma lista das fontes problemáticas, então você poderia, por exemplo, incorporar uma fonte de fallback:

```java
// Optional: Replace missing fonts with a known fallback (e.g., Liberation Sans)
FontSettings fontSettings = new FontSettings();
fontSettings.setSubstitutionSettings(new FontSubstitutionSettings());
fontSettings.getSubstitutionSettings().getDefaultFontSubstitutes()
    .add("Calibri", "Liberation Sans");
document.setFontSettings(fontSettings);
```

Sinta‑se à vontade para pular este bloco se você precisar apenas **rastrear fontes ausentes**. O importante é que agora você tem as informações necessárias para tomar uma decisão informada.

## Etapa 5 – Salvar o documento processado

Por fim, persista o documento. Você pode sobrescrever o original, salvar em um novo local ou exportar para PDF — tudo sem perder os dados de aviso capturados anteriormente.

```java
// Step 5: Save the processed document
document.save("YOUR_DIRECTORY/processed.docx");
System.out.println("Document saved successfully.");
```

Executar a classe completa produzirá saída no console para cada fonte ausente e um novo arquivo chamado `processed.docx` na mesma pasta.

## Exemplo completo em funcionamento

A seguir está a classe Java completa que você pode copiar‑colar na sua IDE. Ela inclui tudo o que discutimos, além de um pequeno wrapper `main`.

```java
import com.aspose.words.*;

public class FontDiagnostic {
    public static void main(String[] args) throws Exception {
        // Step 1: Create LoadOptions to customize how the document is loaded
        LoadOptions loadOptions = new LoadOptions();

        // Step 2: Register a warning handler that reports font substitution events
        loadOptions.setFontSubstitutionWarningHandler(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution detected: " + info.getDescription());
                }
            }
        });

        // Step 3: Load the document using the configured LoadOptions
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // Optional Step 4: Replace missing fonts with a fallback (if desired)
        // FontSettings fontSettings = new FontSettings();
        // fontSettings.getSubstitutionSettings().getDefaultFontSubstitutes()
        //     .add("Calibri", "Liberation Sans");
        // document.setFontSettings(fontSettings);

        // Step 5: Save the processed document
        document.save("YOUR_DIRECTORY/processed.docx");
        System.out.println("Document saved successfully.");
    }
}
```

### Saída esperada

Ao executar o programa contra um documento que usa uma fonte não instalada no seu sistema, você verá algo como:

```
Font substitution detected: Font 'Times New Roman' was substituted with 'Arial'.
Font substitution detected: Font 'Cambria Math' was substituted with 'Arial Unicode MS'.
Document saved successfully.
```

Se o documento **não contiver fontes ausentes**, o console permanecerá silencioso até a linha final “Document saved successfully.” — exatamente o que se espera de uma implementação bem‑comportada de **registro de callback de aviso**.

## Dicas avançadas & armadilhas comuns

- **Múltiplos callbacks?** O Aspose.Words permite apenas um manipulador de aviso. Se precisar registrar tanto em um arquivo quanto no console, implemente um callback composto que encaminhe o aviso para múltiplos destinos.  
- **Lotes grandes** – ao processar centenas de arquivos, considere reutilizar uma única instância de `LoadOptions`; criá‑la por arquivo gera overhead desnecessário.  
- **Docs criptografados** – defina a senha em `LoadOptions` antes de carregar, caso contrário você receberá uma `IncorrectPasswordException` antes que o callback seja disparado.  
- **Desempenho** – o callback roda de forma síncrona. Se você estiver registrando em um serviço remoto, faça buffer das mensagens e descarregue‑as após a carga concluir para evitar gargalos de I/O.  
- **Fallback de fonte** – você também pode fornecer uma coleção personalizada de `FontSource` caso possua fontes proprietárias que o Aspose.Words deva considerar antes de recorrer às fontes do sistema.

## Conclusão

Você acabou de aprender como **registrar callback de aviso** em Java, rastrear efetivamente **fontes ausentes** e **personalizar o carregamento do documento** com Aspose.Words. A solução é autocontida, roda com um único método `main` e fornece visibilidade imediata sobre qualquer substituição de fonte que de outra forma passaria despercebida.

Próximos passos? Experimente estender o callback para gravar avisos em um arquivo CSV para fins de auditoria, ou combine‑o com um processador em lote que incorpore automaticamente as fontes ausentes. Você também pode explorar outros tipos de aviso como `IMAGE_SUBSTITUTION` ou `DEPRECATED_FEATURE` — o mesmo padrão se aplica.

Happy coding, and may your documents always render exactly as you intended!

![Diagrama de registro de callback de aviso](register-warning-callback.png "Fluxo de registro de callback de aviso")


## O que você deve aprender a seguir?

- [Callback de Aviso em Documento Word](/words/english/net/programming-with-loadoptions/warning-callback/)
- [Personalizar Cores de Tema & Fontes no Aspose.Words Java: Um Guia Abrangente](/words/english/java/formatting-styles/customize-theme-colors-fonts-aspose-words-java/)
- [Rastrear Alterações em Documentos Word Usando Aspose.Words Java: Um Guia Completo sobre Revisões de Documentos](/words/english/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}