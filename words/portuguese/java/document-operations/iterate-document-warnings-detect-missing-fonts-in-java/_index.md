---
category: general
date: 2026-04-28
description: Iterar avisos de documento em um arquivo Word para detectar fontes ausentes,
  recuperar os nomes das fontes ausentes e imprimir os detalhes das fontes ausentes
  usando Aspose.Words para Java.
draft: false
keywords:
- iterate document warnings
- detect missing fonts
- load word document
- retrieve missing font
- print missing font
language: pt
og_description: Iterar avisos do documento para encontrar fontes ausentes, recuperar
  os nomes das fontes faltantes e imprimir os detalhes das fontes ausentes com um
  exemplo completo em Java.
og_title: 'Iterar avisos de documento: Detectar fontes ausentes em Java'
tags:
- Aspose.Words
- Java
- Document Processing
title: 'Iterar avisos de documento: detectar fontes ausentes em Java'
url: /pt/java/document-operations/iterate-document-warnings-detect-missing-fonts-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Iterar avisos de documento – Detectar fontes ausentes em Java

Já precisou **iterar avisos de documento** ao abrir um arquivo Word e se perguntou quais fontes estão ausentes? Você não está sozinho. Fontes ausentes podem comprometer a aparência de um relatório e, sem uma forma de identificá‑las, você pode enviar um documento que não se parece em nada com o original.  

Neste tutorial, mostraremos como **detectar fontes ausentes** carregando um documento Word, iterando seus avisos, recuperando os nomes das fontes ausentes e, finalmente, imprimindo as informações das fontes ausentes — tudo com Aspose.Words for Java.  

Cobriremos tudo, desde a primeira linha de código até a saída esperada no console, para que você possa copiar‑colar uma solução funcional em seu projeto agora mesmo. Nenhuma documentação extra é necessária.

## Pré-requisitos

- Java 8 ou superior instalado.
- Biblioteca Aspose.Words for Java (a versão mais recente em 2026‑04‑28).
- Um arquivo Word que potencialmente contém fontes não instaladas na sua máquina (por exemplo, `doc-with-missing-font.docx`).

Se você já tem isso, ótimo — você está pronto para **load word document** e começar a iterar.

## Etapa 1 – Carregar documento Word com opções padrão

Antes de podermos **iterar avisos de documento**, o arquivo deve ser carregado na memória. Aspose.Words permite fazer isso com uma única chamada ao construtor. Usar o `LoadOptions` padrão geralmente é suficiente, mas vamos mostrar a criação explícita para clareza.

```java
import com.aspose.words.*;

public class MissingFontDetector {
    public static void main(String[] args) throws Exception {

        // Step 1: Prepare load options (default settings are fine for this example)
        LoadOptions loadOptions = new LoadOptions();

        // Step 2: Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/doc-with-missing-font.docx", loadOptions);
```

> **Por que isso importa:**  
> Carregar o documento faz com que o Aspose.Words escaneie o arquivo em busca de recursos que não pode resolver, como fontes que não estão instaladas localmente. Esses problemas são armazenados como **avisos**, que **iterate document warnings** na próxima etapa.

## Etapa 2 – Iterar avisos de documento para encontrar problemas de fontes

Agora vem o coração da solução: percorremos cada aviso que a biblioteca coletou durante o carregamento. Os objetos `WarningInfo` nos dizem o que deu errado, e podemos filtrar por `FontSubstitutionWarning` para **detectar fontes ausentes**.

```java
        // Step 3: Iterate over all warnings generated during loading
        for (WarningInfo warningInfo : document.getWarnings()) {
            // Step 4: Identify font substitution warnings
            if (warningInfo instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fontWarning = (FontSubstitutionWarning) warningInfo;

                // Step 5: Output the missing font name and the font that was used as a substitute
                System.out.println("Missing font: " + fontWarning.getMissingFontName());
                System.out.println("Substituted with: " + fontWarning.getSubstitutedFontName());
            }
        }
    }
}
```

> **Dica profissional:** A verificação `instanceof` garante que tratemos apenas avisos relacionados a fontes, ignorando outros, como problemas de carregamento de imagens. Isso torna o loop eficiente e mantém a saída focada nas fontes das quais você realmente precisa **retrieve missing font** informações.

### Saída esperada no console

```
Missing font: Arial Black
Substituted with: Liberation Sans
Missing font: Calibri
Substituted with: Liberation Sans
```

Se o documento não contiver fontes ausentes, o loop simplesmente termina silenciosamente — nada a **print missing font**.

## Etapa 3 – Por que não simplesmente capturar uma exceção?

Você pode se perguntar: “Por que não envolver a chamada `new Document(...)` em um try‑catch e procurar uma exceção?” A resposta tem duas partes:

1. **Informação granular:** Exceções apenas informam que algo falhou. Avisos fornecem o nome exato da fonte e a alternativa que o Aspose.Words escolheu.
2. **Problemas não fatais:** Fontes ausentes geralmente não são fatais; o documento ainda carrega, mas a fidelidade visual é comprometida. Ao **iterating document warnings**, você preserva a capacidade de processar o restante do arquivo.

## Etapa 4 – Extendendo o exemplo: coletando fontes ausentes em uma lista

Às vezes você precisa das fontes ausentes para processamento adicional — talvez para incorporá‑las ou alertar um usuário via UI. Aqui está um ajuste rápido que coleta os nomes em um `Set<String>`.

```java
        // Collect missing fonts for later use
        Set<String> missingFonts = new HashSet<>();

        for (WarningInfo warningInfo : document.getWarnings()) {
            if (warningInfo instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fontWarning = (FontSubstitutionWarning) warningInfo;
                missingFonts.add(fontWarning.getMissingFontName());

                // Still print for immediate feedback
                System.out.println("Missing font: " + fontWarning.getMissingFontName());
                System.out.println("Substituted with: " + fontWarning.getSubstitutedFontName());
            }
        }

        // Example of using the collected data
        System.out.println("Total missing fonts: " + missingFonts.size());
```

Agora você tem uma maneira limpa de **retrieve missing font** programaticamente, que pode ser alimentada em um módulo de relatórios ou em um assistente de instalação de fontes.

## Etapa 5 – Considerações do mundo real

- **Substituições múltiplas:** Uma única fonte ausente pode ser substituída por fontes diferentes em partes distintas do documento. A lista de avisos conterá cada ocorrência, portanto você pode ver entradas duplicadas de fontes ausentes.
- **Desempenho:** Carregar documentos muito grandes pode gerar milhares de avisos. Se você se preocupa apenas com fontes, filtre cedo como mostrado para manter o loop rápido.
- **Fontes multiplataforma:** No Linux, a fonte de substituição padrão costuma ser *Liberation Sans*. No Windows, pode ser *Arial*. Conhecer a alternativa ajuda a decidir se você precisa distribuir fontes personalizadas com sua aplicação.

## Etapa 6 – Ajuda visual

Abaixo está uma captura de tela da saída do console (o texto alternativo inclui a palavra‑chave principal para SEO).

![Saída do console ao iterar avisos de documento mostrando fontes ausentes e seus substitutos](/images/iterate-document-warnings.png)

*Texto alternativo:* *exemplo de iterar avisos de documento exibindo nomes de fontes ausentes e detalhes de substituição.*

## Conclusão

Você acabou de aprender como **iterate document warnings** no Aspose.Words for Java, **detect missing fonts**, **load word document** com segurança, **retrieve missing font** informações e **print missing font** detalhes no console. O trecho de código completo funciona como está, e você pode adaptá‑lo para registrar em um arquivo, exibir um diálogo de UI ou até mesmo incorporar as fontes ausentes automaticamente.

Em seguida, você pode querer explorar como **load word document** com fontes personalizadas (por exemplo, adicionando uma pasta de fontes corporativas) ou como incorporar fontes ausentes diretamente no arquivo para preservar o layout em diferentes máquinas. Ambos os tópicos se desenvolvem naturalmente a partir do que cobrimos aqui.

Feliz codificação, e que seus PDFs sempre pareçam exatamente como você pretende!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}