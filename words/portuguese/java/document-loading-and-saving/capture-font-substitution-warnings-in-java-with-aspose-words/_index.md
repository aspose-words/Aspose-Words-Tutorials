---
category: general
date: 2026-06-27
description: Aprenda a capturar avisos de substituição de fontes em Java usando Aspose.Words.
  Este tutorial passo a passo também aborda callbacks de avisos e o uso de LoadOptions.
draft: false
keywords:
- capture font substitution warnings
- Aspose.Words warning callback
- Java LoadOptions example
- font substitution handling
- document processing with Aspose
language: pt
og_description: Capture avisos de substituição de fontes em Java com Aspose.Words.
  Siga este guia para configurar callbacks de aviso, usar LoadOptions e lidar com
  fontes ausentes.
og_title: Capturar Avisos de Substituição de Fonte em Java – Tutorial Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Learn how to capture font substitution warnings in Java using Aspose.Words.
    This step‑by‑step tutorial also covers warning callbacks and LoadOptions usage.
  headline: Capture Font Substitution Warnings in Java with Aspose.Words – Complete
    Guide
  type: TechArticle
- questions:
  - answer: Yes. The warning callback is format‑agnostic; it fires for any document
      type that Aspose.Words loads (DOC, DOCX, RTF, HTML, etc.). The only difference
      is the set of warnings that may appear.
    question: Does this work with PDF or other formats?
  - answer: Absolutely. Inside the `warning` method, inspect `info.getWarningType()`
      for other enum values such as `WarningType.IMAGE_RESOLUTION`. Then handle them
      accordingly.
    question: Can I capture other warning types, like *image resolution* warnings?
  - answer: 'Store each `info.getDescription()` in a `List<String>` inside the callback.
      After loading, you’ll have a collection you can log, send to a monitoring service,
      or use to trigger a font‑download routine. ## Conclusion You now know **how
      to capture font substitution warnings** in Java using Aspose.Word'
    question: What if I need the list of substituted fonts after the document loads?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Document Conversion
title: Capturar avisos de substituição de fontes em Java com Aspose.Words – Guia completo
url: /pt/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Capturando Avisos de Substituição de Fonte em Java com Aspose.Words – Guia Completo

Já precisou **capturar avisos de substituição de fonte** ao carregar um DOCX que usa tipografias exóticas? Você não está sozinho. Em muitos projetos do mundo real — pense em geradores de relatórios automatizados ou conversores de documentos em lote — fontes ausentes acionam substituições silenciosas que podem arruinar a fidelidade do layout.  

Felizmente, o Aspose.Words oferece uma maneira simples de escutar esses avisos. Neste tutorial, percorreremos a configuração de **LoadOptions**, a ligação de um **callback de aviso do Aspose.Words**, e a impressão de cada aviso de *substituição de fonte* no console. Ao final, você saberá exatamente quando uma fonte foi substituída e como reagir programaticamente.

> **O que você receberá:** um trecho de código Java totalmente executável, uma explicação do *porquê* cada parte importa, e dicas para lidar com casos extremos como diretórios de fontes personalizados.

## Pré-requisitos & O que você precisará

Antes de mergulharmos, certifique‑se de que você tem:

- Java 8 ou mais recente instalado (o código funciona também com Java 11+).
- O JAR mais recente do Aspose.Words for Java (faça download no site oficial ou no Maven Central).
- Um arquivo DOCX que referencia fontes não instaladas na sua máquina (por exemplo, um *font‑rich.docx* que você pode encontrar no conjunto de demonstração da Aspose).
- Um IDE decente (IntelliJ IDEA, Eclipse ou até VS Code com extensões Java).

Nenhuma biblioteca externa além do Aspose.Words é necessária, e o exemplo roda em um método `main` simples.

## Passo 1: Configurar LoadOptions – O ponto de entrada para carregamento personalizado

`LoadOptions` é o contêiner de configuração do Aspose.Words que indica à biblioteca *como* ler um documento. Por padrão, ele substitui silenciosamente fontes ausentes, mas você pode mudar esse comportamento com um callback de aviso.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Create LoadOptions to customize loading behavior
        LoadOptions loadOptions = new LoadOptions();
```

**Por que isso importa:** Sem `LoadOptions`, o documento é carregado silenciosamente, e você perde a visibilidade das fontes ausentes. Ao criar uma instância, você obtém um ponto de conexão para o sistema de avisos.

## Passo 2: Definir um Callback de Aviso para *Capturar Avisos de Substituição de Fonte*

O Aspose.Words envia eventos de aviso através da interface `IWarningCallback`. Implemente‑a inline (ou como uma classe separada) e filtre por `WarningType.FONT_SUBSTITUTION`.

```java
        // Step 2: Define a warning callback to capture font substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // Only react to font substitution warnings
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });
```

**Explicação:**  
- `info.getWarningType()` informa a categoria do aviso.  
- `WarningType.FONT_SUBSTITUTION` é o valor enum que nos interessa.  
- `info.getDescription()` contém uma mensagem legível, por exemplo, *“Font 'Comic Sans MS' not found, substituted with 'Arial'.”*  

Ao imprimir a descrição, você **captura avisos de substituição de fonte** em tempo real.

## Passo 3: Carregar o Documento usando o LoadOptions Configurado

Agora que o callback está configurado, carregue seu DOCX. O callback de aviso é disparado automaticamente durante a análise.

```java
        // Step 3: Load the document using the configured LoadOptions
        Document document = new Document("YOUR_DIRECTORY/font-rich.docx", loadOptions);
```

Substitua `YOUR_DIRECTORY` pelo caminho real do seu arquivo de teste. Quando o construtor `Document` for executado, qualquer fonte ausente acionará o callback definido anteriormente, e você verá as mensagens de substituição no console.

## Passo 4: Verificar o Documento Carregado (Opcional, mas Útil)

Após o carregamento, você pode querer confirmar a integridade do documento — contagem de páginas, extração de texto, etc. Esta etapa não é necessária para capturar avisos, mas ajuda a ver o impacto das substituições.

```java
        // Optional: Output basic document info
        System.out.println("Document loaded successfully.");
        System.out.println("Page count: " + document.getPageCount());
```

Se uma fonte foi substituída, o layout pode mudar levemente; verificar a contagem de páginas pode revelar tais alterações.

## Passo 5: Avançado – Manipulando Fontes Substituídas Programaticamente

Às vezes você não quer apenas registrar o aviso — pode ser necessário incorporar uma fonte de fallback ou ajustar o estilo. Abaixo está um padrão rápido que você pode adotar.

```java
        // Advanced: Register a fallback font folder to reduce substitutions
        FontSettings fontSettings = new FontSettings();
        // Point to a folder that contains the missing fonts
        fontSettings.setFontsFolder("YOUR_DIRECTORY/custom-fonts", true);
        loadOptions.setFontSettings(fontSettings);
```

Ao apontar o Aspose.Words para uma pasta que contém as fontes originais, você pode *evitar* a substituição completamente. Se a pasta estiver ausente, o callback de aviso ainda captura o evento, fornecendo uma estratégia de fallback.

## Exemplo Completo Funcional

Juntando tudo, aqui está o programa completo, pronto‑para‑executar:

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Initialize LoadOptions
        LoadOptions loadOptions = new LoadOptions();

        // Set up warning callback to capture font substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });

        // OPTIONAL: Register a custom fonts folder to avoid substitution
        FontSettings fontSettings = new FontSettings();
        fontSettings.setFontsFolder("YOUR_DIRECTORY/custom-fonts", true);
        loadOptions.setFontSettings(fontSettings);

        // Load the document – warnings will be printed automatically
        Document doc = new Document("YOUR_DIRECTORY/font-rich.docx", loadOptions);

        // Verify basic info
        System.out.println("Document loaded successfully.");
        System.out.println("Page count: " + doc.getPageCount());
    }
}
```

**Saída esperada no console** (quando uma fonte ausente é encontrada):

```
Font substituted: Font 'Pacifico' not found, substituted with 'Arial'.
Document loaded successfully.
Page count: 3
```

Se todas as fontes estiverem presentes, o callback permanece silencioso — nada é impresso, que é exatamente o esperado.

## Armadilhas Comuns & Dicas Profissionais

| Armadilha | Por que acontece | Correção |
|----------|------------------|----------|
| **Callback nunca dispara** | Você esqueceu de anexar o callback ao `LoadOptions` **ou** usou o construtor padrão de `Document` sem passar `loadOptions`. | Sempre chame `loadOptions.setWarningCallback(...)` **e** use a sobrecarga `new Document(path, loadOptions)`. |
| **Muitos avisos poluem o log** | Documentos grandes com muitas fontes ausentes geram um aviso por substituição. | Filtre ainda mais verificando `info.getDescription()` para nomes de fontes específicos, ou agregue avisos em uma lista para processamento posterior. |
| **Fontes substituídas afetam o layout** | A fonte de fallback pode ter métricas diferentes (tamanho, espaçamento). | Forneça uma pasta de fontes personalizada (veja o Passo 5) ou ajuste o estilo do documento após o carregamento. |
| **Executando em um servidor sem interface gráfica** | O fallback de fonte padrão pode depender de fontes do sistema que não estão instaladas no servidor. | Inclua as fontes necessárias com sua aplicação e aponte `FontSettings` para essa pasta. |

## Perguntas Frequentes

**Q: Isso funciona com PDF ou outros formatos?**  
A: Sim. O callback de aviso é independente de formato; ele dispara para qualquer tipo de documento que o Aspose.Words carregue (DOC, DOCX, RTF, HTML, etc.). A única diferença são os avisos que podem aparecer.

**Q: Posso capturar outros tipos de aviso, como avisos de *resolução de imagem*?**  
A: Absolutamente. Dentro do método `warning`, inspecione `info.getWarningType()` para outros valores enum como `WarningType.IMAGE_RESOLUTION`. Então trate‑os adequadamente.

**Q: E se eu precisar da lista de fontes substituídas após o carregamento do documento?**  
A: Armazene cada `info.getDescription()` em um `List<String>` dentro do callback. Após o carregamento, você terá uma coleção que pode registrar, enviar para um serviço de monitoramento ou usar para disparar uma rotina de download de fontes.

## Conclusão

Agora você sabe **como capturar avisos de substituição de fonte** em Java usando Aspose.Words, por que cada parte do quebra‑cabeça importa, e como estender a solução para cenários reais. Ao aproveitar `LoadOptions`, um `callback de aviso do Aspose.Words` e opcionalmente `FontSettings`, você obtém total visibilidade das fontes ausentes e pode manter seus pipelines de conversão de documentos confiáveis.

Pronto para o próximo passo? Experimente substituir o `System.out.println` por um logger como SLF4J, ou integre a lista de avisos em uma UI que alerte os usuários antes de finalizarem uma conversão em lote. Você também pode explorar o **callback de aviso do Aspose.Words** para outros tipos de aviso, como *recursos não suportados* ou alertas de *imagem de alta resolução*.  

Feliz codificação, e que seus PDFs nunca sofram trocas inesperadas de fonte novamente! 

![Screenshot showing console output of captured font substitution warnings](image-placeholder.png "capture font substitution warnings")


## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Ativar Avisos de Substituição de Fonte no Aspose.Words – Guia Completo](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [Como Definir LoadOptions no Aspose.Words para Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Como Criar Documentos PDF com Aspose.Words para Java | API de Processamento de Documentos](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}