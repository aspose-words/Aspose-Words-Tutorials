---
category: general
date: 2026-06-30
description: Configure as opções de carregamento (LoadOptions) para avisos no Aspose.Words
  Java. Aprenda a definir um callback de aviso para substituição de fontes e outros
  avisos de opções de carregamento.
draft: false
keywords:
- configure loadoptions for warnings
- Aspose.Words font substitution
- Java warning callback
- document loading options
- handle font warnings
language: pt
og_description: Configure LoadOptions para avisos no Aspose.Words Java. Este guia
  mostra como capturar alertas de substituição de fontes com um callback de aviso.
og_title: Configurar LoadOptions para Avisos – Tutorial de Java
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: Configure LoadOptions for warnings in Aspose.Words Java. Learn to set
    up a warning callback for font substitution and other load‑options warnings.
  headline: Configure LoadOptions for Warnings – Complete Java Guide
  type: TechArticle
tags:
- aspose-words
- java
- warnings
- font-substitution
title: Configurar LoadOptions para Avisos – Guia Completo de Java
url: /pt/java/document-loading-and-saving/configure-loadoptions-for-warnings-complete-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Configurar LoadOptions para Avisos – Guia Completo em Java

Já precisou **configurar LoadOptions para avisos** ao abrir um documento Word com Aspose.Words for Java? Você não está sozinho. Muitos desenvolvedores se deparam com um problema quando uma fonte ausente é substituída silenciosamente, fazendo o PDF final ficar fora da identidade visual. A boa notícia? Ao conectar um **callback de aviso Java** ao seu `LoadOptions`, você pode capturar cada alerta de substituição de fonte no instante em que ocorre.

Neste tutorial vamos percorrer um exemplo prático que não apenas mostra como configurar o callback, mas também explica *por que* cada parte importa. Ao final, você será capaz de **lidar com avisos de fonte**, registrá‑los ou até substituir fontes em tempo real — sem adivinhações.

## O que você levará consigo

- Um programa Java totalmente executável que imprime cada aviso de substituição de fonte.
- Uma compreensão dos mecanismos de **substituição de fonte do Aspose.Words**.
- Dicas para personalizar o tratamento de avisos em projetos maiores.
- Visão sobre **opções de carregamento de documento** e quando ajustá‑las.

> **Pré‑requisito:** Java 8+ e a biblioteca Aspose.Words for Java (versão 23.9 ou posterior). Nenhuma outra dependência externa é necessária.

---

## Etapa 1: Configurar LoadOptions para Avisos

A primeira coisa que você precisa é uma instância de `LoadOptions` que saiba que deve relatar avisos. Pense no `LoadOptions` como a caixa de ferramentas que você entrega ao Aspose.Words antes mesmo de ele abrir o arquivo.

```java
// Step 1: Create LoadOptions and attach a warning callback.
LoadOptions loadOptions = new LoadOptions();
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Only react to font‑substitution warnings.
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("Font substitution detected: " + info.getDescription());
        }
    }
});
```

**Por que isso importa:**  
`LoadOptions` controla como a biblioteca lê o documento. Ao atribuir um `IWarningCallback`, você indica ao Aspose.Words que invoque seu código sempre que encontrar algo relevante — como uma fonte ausente. Sem isso, a biblioteca substituiria a fonte silenciosamente e você nunca saberia.

> **Dica de especialista:** Se quiser capturar *todos* os avisos, remova a verificação `if`. Por enquanto, focamos em problemas de fonte porque são a fonte mais comum de surpresas de layout.

## Etapa 2: Carregar o Documento Usando as Opções Configuradas

Agora que o callback está pronto, carregue seu `.docx` (ou qualquer formato suportado) com o mesmo `LoadOptions`. É aqui que as **opções de carregamento de documento** realmente entram em ação.

```java
// Step 2: Load the document with the warning‑aware LoadOptions.
Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**Nos bastidores:**  
Quando o Aspose.Words analisa `input.docx`, ele varre as tabelas de fontes. Se uma fonte referenciada no documento não estiver instalada na máquina host, o motor gera um aviso `FONT_SUBSTITUTION`, que imediatamente dispara o callback que definimos anteriormente.

## Etapa 3: Salvar o Documento – Os Avisos Já Foram Impressos

Salvar o documento é simples, mas é o momento em que você pode verificar se o callback foi disparado corretamente. Todos os avisos são impressos durante a etapa de carregamento, então a operação de salvamento é apenas uma limpeza.

```java
// Step 3: Save the document. Any warnings were already printed in Step 1.
document.save("YOUR_DIRECTORY/output.docx");
```

**Saída esperada no console:**  

```
Font substitution detected: Font 'Calibri' is not installed. Substituted with 'Arial'.
Font substitution detected: Font 'Times New Roman' is not installed. Substituted with 'Liberation Serif'.
```

Se nada aparecer, ou o documento usou apenas fontes instaladas, ou o callback não foi conectado corretamente — verifique a Etapa 1.

## Etapa 4: Expandir o Callback para **Lidar com Avisos de Fonte** de Forma Elegante

Imprimir no console serve para demonstrações, mas o código de produção costuma precisar de um tratamento mais robusto: registro em arquivo, envio de alertas ou até troca de fontes programaticamente.

```java
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            // Log to a file (simple example)
            try (FileWriter fw = new FileWriter("font-warnings.log", true)) {
                fw.write("WARN: " + info.getDescription() + System.lineSeparator());
            } catch (IOException e) {
                e.printStackTrace();
            }
            // Optionally replace the missing font with a fallback.
            FontSettings.getDefaultInstance().setSubstitutionSettings(
                new FontSubstitutionSettings() {{
                    getTableSubstitution().addSubstitutes("Calibri", "Arial");
                }}
            );
        }
    }
});
```

**Por que fazer isso:**  
Um arquivo de log fornece insights pós‑mortem, especialmente ao processar lotes de documentos. O bloco opcional de substituição demonstra como **configurar LoadOptions para avisos** *e* intervir para aplicar uma política corporativa de fontes.

## Avançado: Controlando Outros Cenários de **Substituição de Fonte do Aspose.Words**

O callback de aviso não se limita a fontes ausentes. Você também pode capturar:

- **Caracteres Unicode não suportados** (`WarningType.UNSUPPORTED_CHAR`).
- **Problemas de script complexo** (`WarningType.COMPLEX_SCRIPT`).

Basta expandir a instrução `if`:

```java
if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
    // handle fonts
} else if (info.getWarningType() == WarningType.UNSUPPORTED_CHAR) {
    System.out.println("Unsupported character: " + info.getDescription());
}
```

Isso torna sua solução robusta para documentos multilíngues, um caso de borda comum em aplicações globais.

## Exemplo Completo Funcional

Abaixo está o programa completo, pronto para ser executado. Cole-o em qualquer IDE Java, substitua os marcadores `YOUR_DIRECTORY` e pressione *Run*.

```java
import com.aspose.words.*;

import java.io.FileWriter;
import java.io.IOException;

public class FontSubstitutionDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Configure LoadOptions for warnings.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution: " + info.getDescription());

                    // Optional: Log to a file.
                    try (FileWriter fw = new FileWriter("font-warnings.log", true)) {
                        fw.write("WARN: " + info.getDescription() + System.lineSeparator());
                    } catch (IOException e) {
                        e.printStackTrace();
                    }

                    // Optional: Force a specific fallback font.
                    FontSettings.getDefaultInstance().setSubstitutionSettings(
                        new FontSubstitutionSettings() {{
                            getTableSubstitution().addSubstitutes("Calibri", "Arial");
                        }}
                    );
                }
            }
        });

        // Step 2: Load the document using the configured LoadOptions.
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // Step 3: Save the document. Warnings have already been printed.
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### Resultado Esperado

- O console imprime quaisquer avisos de substituição de fonte.
- `font-warnings.log` contém uma lista com carimbo de data/hora (se você manteve o registro opcional).
- `output.docx` é salvo com fontes substituídas, correspondendo ao fallback que você definiu.

## Armadilhas Comuns & Como Evitá‑las

| Armadilha | Por que acontece | Solução |
|-----------|------------------|---------|
| **Nenhum aviso aparece** | O callback não foi anexado, ou o documento usa apenas fontes instaladas. | Verifique se `loadOptions.setWarningCallback(...)` é chamado *antes* de carregar o documento. |
| **FileNotFoundException** ao acessar `input.docx` | O caminho está errado ou o arquivo não está incluído no projeto. | Use um caminho absoluto ou coloque o arquivo na pasta de recursos do projeto. |
| **Desempenho lento** ao processar milhares de documentos | Registro excessivo em disco a cada aviso. | Armazene logs em buffer e escreva em lotes, ou limite o registro a avisos críticos apenas. |
| **Substituição de fonte inesperada** apesar do fallback | A tabela de substituição não foi aplicada cedo o suficiente. | Defina as configurações de substituição **antes** de carregar o documento, ou use `FontSettings.setSubstitutionSettings` globalmente. |

## Próximos Passos

Agora que você dominou **configurar LoadOptions para avisos**, considere estes tópicos de continuação:

- **Processamento em lote**: percorrer um diretório de documentos, agregando todos os avisos de fonte em um único relatório.
- **Provedores de fonte personalizados**: carregar fontes de um compartilhamento de rede ou recursos incorporados em vez do SO local.
- **Integração com frameworks de registro** como Log4j para rastreabilidade de nível empresarial.
- Explore outras **opções de carregamento de documento**, como detecção de `LoadFormat` ou tratamento de `Password` para arquivos protegidos.

Cada um desses itens segue o mesmo padrão — criar um objeto `LoadOptions`, anexar os callbacks apropriados e deixar o Aspose.Words fazer o trabalho pesado.

## Conclusão

Fizemos um mergulho profundo em como **configurar LoadOptions para avisos** no Aspose.Words for Java, configuramos um **callback de aviso Java** e usamos essa informação para **lidar inteligentemente com avisos de fonte**. O código é compacto, os conceitos são claros, e agora você tem uma base sólida para estender o tratamento de avisos a outros cenários, como caracteres não suportados ou scripts complexos.

Experimente, ajuste a tabela de substituição para combinar com as fontes da sua marca e veja esses swaps silenciosos desaparecerem. Feliz codificação!

--- 

![Diagrama mostrando o fluxo de configuração de LoadOptions para avisos, carregamento de um documento, captura de eventos de substituição de fonte e salvamento da saída](configure-loadoptions-for-warnings-diagram.png "Fluxo de Configuração de LoadOptions para avisos")


## O que você deve aprender a seguir?


Os tutoriais a seguir abordam tópicos estreitamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Capturar Avisos de Substituição de Fonte em Java com Aspose.Words – Guia Completo](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Como Definir LoadOptions no Aspose.Words para Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Como Carregar Documentos RTF Configurando Opções de Carregamento RTF no Aspose.Words para Java](/words/english/java/document-loading-and-saving/configuring-rtf-load-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}