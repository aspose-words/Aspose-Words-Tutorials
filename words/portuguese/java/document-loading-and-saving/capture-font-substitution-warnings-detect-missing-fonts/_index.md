---
category: general
date: 2026-04-04
description: Capture avisos de substituição de fontes ao carregar documentos Word
  com Aspose.Words for Java e detecte fontes ausentes automaticamente. Siga este guia
  passo a passo.
draft: false
keywords:
- capture font substitution warnings
- detect missing fonts
language: pt
og_description: Capture avisos de substituição de fontes ao carregar documentos Word
  com Aspose.Words para Java e detecte fontes ausentes em poucos passos simples.
og_title: Capturar Avisos de Substituição de Fonte – Detectar Fontes Ausentes
tags:
- Aspose.Words
- Java
- Document Processing
title: Capturar Avisos de Substituição de Fonte – Detectar Fontes Ausentes
url: /pt/java/document-loading-and-saving/capture-font-substitution-warnings-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Capturar Avisos de Substituição de Fonte – Detectar Fontes Ausentes

Já precisou **capturar avisos de substituição de fonte** ao abrir um arquivo Word, apenas para descobrir que uma tipografia crucial está ausente? Você não está sozinho. Em muitos fluxos de trabalho corporativos, uma fonte ausente pode transformar um relatório perfeitamente formatado em uma bagunça ilegível, e a única pista que você tem é um aviso silencioso que a maioria dos desenvolvedores nunca vê.

A boa notícia é que o Aspose.Words for Java permite que você se conecte ao processo de carregamento e **detecte fontes ausentes** antes que elas causem problemas. Neste tutorial, percorreremos um exemplo completo e executável que imprime cada aviso de substituição diretamente no console, para que você possa decidir se incorpora a fonte correta, a substitui ou alerta o usuário.

Até o final deste guia, você saberá como:

* Configurar um objeto `LoadOptions` com um callback de aviso personalizado.
* Filtrar o callback para que ele reaja apenas a eventos de substituição de fonte.
* Carregar qualquer arquivo `.docx` e ver os avisos instantaneamente.
* Expandir a solução para registrar avisos, lançar exceções ou até mesmo instalar automaticamente fontes ausentes.

Não é necessária documentação externa — apenas algumas linhas de Java e o JAR do Aspose.Words.

## Pré-requisitos

Antes de mergulharmos, certifique-se de que você tem:

* Java 8 ou superior instalado (a versão LTS mais recente funciona melhor).
* Aspose.Words for Java 23.11 ou posterior – você pode obter o artefato Maven ou o JAR simples no site da Aspose.
* Um documento Word que referencia uma fonte que você não possui na sua máquina de desenvolvimento (por exemplo, “MyFancyFont”).  
* Uma IDE ou editor de texto de sua escolha – eu estou usando IntelliJ IDEA, mas Eclipse ou VS Code funcionam bem.

Se algum desses itens for desconhecido, pause e instale-os primeiro; o restante do tutorial assume que eles estão prontos.

---

## Capturar Avisos de Substituição de Fonte Usando Aspose.Words

O núcleo da solução reside em uma instância de `LoadOptions`. Ao atribuir um `IWarningCallback` podemos interceptar cada aviso que a biblioteca emite durante a fase de carregamento.

```java
import com.aspose.words.*;

public class FontDiagnosticsTutorial {
    public static void main(String[] args) throws Exception {

        // Step 1️⃣: Create LoadOptions and set a warning callback.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // Capture only font substitution warnings.
                if (info.getWarningType() == WarningType.SUBSTITUTED_FONT) {
                    System.out.println("Font substitution: " + info.getDescription());
                }
            }
        });

        // Step 2️⃣: Load the document. The callback runs automatically.
        Document doc = new Document("YOUR_DIRECTORY/document-with-missing-font.docx", loadOptions);

        // Step 3️⃣: If you reach this line, the document is loaded.
        // Any missing‑font warnings have already been printed to the console.
        System.out.println("Document loaded successfully.");
    }
}
```

**Por que isso funciona:**  
`LoadOptions` informa ao Aspose.Words como tratar o arquivo de entrada. A interface `IWarningCallback` é um hook que recebe um objeto `WarningInfo` para *cada* aviso. Ao verificar `info.getWarningType()` filtramos tudo exceto `SUBSTITUTED_FONT`. A propriedade `description` contém uma mensagem legível como “Font 'MyFancyFont' was substituted with 'Arial'`.

### Saída esperada no console

Se o documento de origem referencia uma fonte que não está instalada, você verá algo como:

```
Font substitution: Font 'MyFancyFont' was substituted with 'Arial'.
Document loaded successfully.
```

Se o documento usa apenas fontes que existem na máquina, o callback permanece silencioso e você recebe apenas a linha final “Document loaded successfully.”.

---

## Detectar Fontes Ausentes no Seu Documento

Você pode se perguntar, *“Um aviso de substituição é o mesmo que uma fonte ausente?”* Na maioria dos casos, sim — o Aspose.Words substitui uma fonte ausente por uma alternativa e relata isso via `SUBSTITUTED_FONT`. Contudo, há casos extremos em que a fonte está presente, mas o estilo exato (negrito‑itálico, recursos OpenType específicos) não está, levando a uma substituição sutil.

Para ter absoluta certeza de que você capturou todas as lacunas, você pode combinar o callback de aviso com uma inspeção pós‑carregamento:

```java
// After loading the document, iterate through all runs.
for (Paragraph para : (Iterable<Paragraph>) doc.getFirstSection().getBody().getChildNodes(NodeType.PARAGRAPH, true)) {
    for (Run run : (Iterable<Run>) para.getChildNodes(NodeType.RUN, true)) {
        Font font = run.getFont();
        if (font.getName().equalsIgnoreCase("MyFancyFont")) {
            System.out.println("Run still uses the missing font: " + font.getName());
        }
    }
}
```

**Dica profissional:** Se você encontrar trechos ainda referenciando a fonte ausente, pode substituí‑los em tempo real:

```java
font.setName("Arial"); // fallback
```

Dessa forma você garante um resultado visual consistente, mesmo que o aviso original tenha sido suprimido.

---

## Armadilhas Comuns & Como Evitá‑las

| Armadilha | Por que acontece | Correção |
|----------|------------------|----------|
| **Esquecer de definir o callback** | `LoadOptions` tem como padrão um callback no‑op, então os avisos desaparecem. | Sempre chame `loadOptions.setWarningCallback(...)` antes de carregar. |
| **Usar o tipo de aviso errado** | `WarningType.SUBSTITUTED_FONT` é o único enum que sinaliza fontes ausentes. | Filtre exatamente em `WarningType.SUBSTITUTED_FONT`; outros tipos (por exemplo, `UNKNOWN_FILE_FORMAT`) não são relacionados. |
| **Codificar caminhos de arquivo** | Funciona localmente, mas falha em pipelines CI/CD. | Use um caminho relativo ou passe a localização do arquivo como argumento de linha de comando. |
| **Ignorar fontes Unicode** | Algumas fontes ausentes são problemáticas apenas para certos caracteres. | Teste com um documento contendo todo o conjunto de caracteres que você espera suportar. |
| **Executar em um servidor sem interface gráfica sem configuração de fontes** | O servidor pode não ter fontes de fallback, causando substituições inesperadas. | Instale um conjunto mínimo de fontes comuns (Arial, Times New Roman) no servidor. |

---

## Expandindo a Solução

Agora que você pode **capturar avisos de substituição de fonte**, pode querer:

* **Registrar avisos em um arquivo** – substituir `System.out.println` por um logger como SLF4J.
* **Lançar uma exceção** – útil em pipelines automatizados onde uma fonte ausente deve falhar a compilação:

```java
if (info.getWarningType() == WarningType.SUBSTITUTED_FONT) {
    throw new RuntimeException("Missing font detected: " + info.getDescription());
}
```

* **Instalar automaticamente fontes ausentes** – baixar o TTF/OTF necessário em tempo de execução e adicioná‑lo ao `GraphicsEnvironment` do Java. Esse é um cenário mais avançado, mas totalmente viável.

---

## Diagrama (opcional)

![Diagrama de fluxo de captura de avisos de substituição de fonte mostrando LoadOptions → WarningCallback → Saída no console, ilustrando como o Aspose.Words encaminha avisos de fonte ausente para um callback personalizado](capture-font-substitution-warnings-diagram.png)

*Texto alternativo:* “Diagrama de fluxo de captura de avisos de substituição de fonte ilustrando como o Aspose.Words encaminha avisos de fonte ausente para um callback personalizado.”

---

## Conclusão

Acabamos de abordar como **capturar avisos de substituição de fonte** e **detectar fontes ausentes** ao carregar documentos Word com Aspose.Words for Java. Configurando um objeto `LoadOptions` e implementando um pequeno `IWarningCallback`, você obtém total visibilidade do processo de fallback de fontes, permitindo registrar, substituir ou abortar em caso de tipografias ausentes.

Em resumo: defina o callback, filtre por `SUBSTITUTED_FONT`, carregue o documento e trate a saída da maneira que sua aplicação precisar. A partir daqui, você pode expandir para frameworks de registro, verificações de CI ou até mesmo provisionamento automatizado de fontes.

Quer ir além? Experimente:

* **Incorporar fontes** diretamente no documento salvo (`doc.save(..., SaveOptions.createSaveOptions(SaveFormat.DOCX))` com `FontEmbeddingMode.EMBED_ALL`).
* **Gerar um PDF** após corrigir as fontes, garantindo que a saída final fique exatamente como esperado.
* **Escanear uma pasta inteira** de documentos em busca de fontes ausentes e produzir um relatório resumido.

Isso é tudo por enquanto — feliz codificação, e que seus documentos sempre sejam renderizados com a tipografia correta!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}