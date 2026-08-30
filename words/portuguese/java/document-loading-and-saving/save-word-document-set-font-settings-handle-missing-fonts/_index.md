---
category: general
date: 2026-04-24
description: Aprenda a salvar documentos Word usando Aspose.Words, configurando as
  fontes e tratando fontes ausentes com código Java fácil de seguir.
draft: false
keywords:
- save word document
- set font settings
- how to set font settings
- aspose words font substitution
- handle missing fonts
language: pt
og_description: Salve documento Word com Aspose.Words definindo configurações de fonte
  e lidando com fontes ausentes. Guia completo em Java para desenvolvedores.
og_title: Salvar documento do Word – Definir configurações de fonte, lidar com fontes
  ausentes
tags:
- Aspose.Words
- Java
- Font Substitution
- Document Processing
title: Salvar documento do Word – Definir configurações de fonte, lidar com fontes
  ausentes
url: /pt/java/document-loading-and-saving/save-word-document-set-font-settings-handle-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Salvar Documento Word – Definir Configurações de Fonte, Tratar Fontes Ausentes

Já precisou **salvar documento Word** mas o arquivo de origem usa fontes que seu servidor não possui? É um problema comum que pode transformar uma pipeline de automação tranquila em uma dor de cabeça.  

A boa notícia? Com Aspose.Words você pode **definir configurações de fonte** em tempo real, capturar avisos de fontes ausentes e ainda assim obter um documento Word perfeitamente salvo. Neste tutorial vamos percorrer um exemplo completo em Java que mostra **como definir configurações de fonte**, tratar os temidos avisos de *substituição de fonte* e, finalmente, **salvar documento Word** sem surpresas.

## O que você aprenderá

- Como configurar `LoadOptions` com um objeto `FontSettings` personalizado.  
- Como registrar um callback de aviso que relata eventos de **substituição de fonte aspose words**.  
- Como carregar um DOCX, deixar o Aspose substituir fontes ausentes e **salvar documento Word** em um novo local.  
- Dicas para lidar com casos extremos, como arquivos criptografados ou documentos com fontes incorporadas.  

Nenhuma biblioteca extra além do Aspose.Words é necessária, e o código funciona com a versão mais recente 24.x (a partir de abril de 2026).  

---

![Diagrama ilustrando o fluxo de salvar documento Word com configurações de fonte e callback de aviso](font-workflow.png "Diagrama mostrando o fluxo de salvar documento Word")

## Salvar Documento Word com Configurações de Fonte Personalizadas

O primeiro passo é dizer ao Aspose.Words o que fazer quando ele não encontra uma fonte referenciada pelo documento de origem. É aqui que **definir configurações de fonte** entra em ação.

```java
import com.aspose.words.*;

public class FontDiagnostics {
    public static void main(String[] args) throws Exception {
        // -----------------------------------------------------------------
        // Step 1: Prepare LoadOptions with a fresh FontSettings instance.
        // -----------------------------------------------------------------
        LoadOptions loadOptions = new LoadOptions();
        // By default FontSettings uses system fonts, but we can add folders later.
        loadOptions.setFontSettings(new FontSettings());

        // -----------------------------------------------------------------
        // Step 2: Register a warning callback to catch FONT_SUBSTITUTION alerts.
        // -----------------------------------------------------------------
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // We only care about missing‑font warnings.
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution: " + info.getDescription());
                }
            }
        });

        // -----------------------------------------------------------------
        // Step 3: Load the source document using the configured options.
        // -----------------------------------------------------------------
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // -----------------------------------------------------------------
        // Step 4: Save the processed document – fonts have been substituted.
        // -----------------------------------------------------------------
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

**Por que isso funciona:**  
- `LoadOptions` informa ao Aspose.Words para usar o `FontSettings` fornecido ao analisar o arquivo.  
- O `IWarningCallback` intercepta quaisquer mensagens de **substituição de fonte aspose words**, fornecendo um registro em tempo real de quais fontes estavam ausentes.  
- Quando você chama `document.save(...)`, o Aspose substitui automaticamente as fontes ausentes pelas correspondências mais próximas do sistema ou das pastas que você adicionou ao `FontSettings`.

### Resultado Esperado

Executar o programa imprime linhas como:

```
Font substitution: Font 'Calibri' was not found. Substituted with 'Arial'.
Font substitution: Font 'Cambria' was not found. Substituted with 'Times New Roman'.
```

E você obtém `output.docx` que tem a mesma aparência do original — exceto que as fontes ausentes foram substituídas, e o arquivo foi **salvo documento Word** com sucesso no disco.

## Como Definir Configurações de Fonte no Aspose.Words

Se precisar de mais controle — por exemplo, apontar o Aspose para uma pasta de fontes personalizada ou incorporar uma fonte de fallback — basta ajustar o objeto `FontSettings` antes de atribuí‑lo ao `LoadOptions`.

```java
// Create a FontSettings instance.
FontSettings fontSettings = new FontSettings();

// Add a custom folder that contains your private fonts.
fontSettings.setFontsFolder("C:/MyCustomFonts", true);

// Optionally, set a default substitution font (e.g., "Arial").
fontSettings.setDefaultFontName("Arial");

// Attach the configured FontSettings to LoadOptions.
loadOptions.setFontSettings(fontSettings);
```

**Quando usar isso:**  
- Sua aplicação roda em um contêiner que inclui apenas um conjunto mínimo de fontes do sistema.  
- Você tem fontes de branding corporativo que estão em um compartilhamento de rede seguro.  
- Você quer garantir que uma fonte de fallback específica (como “Arial”) seja sempre usada, evitando substituições imprevisíveis.

## Tratando Fontes Ausentes – Callback de Substituição de Fonte

O callback de aviso que registramos anteriormente é o coração da lógica de **tratar fontes ausentes**. Você pode estendê‑lo para:

1. **Coletar avisos** em uma lista para relatório posterior.  
2. **Lançar uma exceção** se uma fonte crítica estiver ausente (por exemplo, a fonte do logotipo).  
3. **Registrar em um sistema de monitoramento** (Splunk, ELK, etc.) para trilhas de auditoria.

```java
loadOptions.setWarningCallback(new IWarningCallback() {
    private final List<String> missingFonts = new ArrayList<>();

    @Override
    public void warning(WarningInfo info) {
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            String msg = "Missing font: " + info.getDescription();
            System.out.println(msg);
            missingFonts.add(msg);
        }
    }

    // Helper to retrieve all missing‑font messages after loading.
    public List<String> getMissingFonts() {
        return missingFonts;
    }
});
```

**Dica profissional:** Se precisar abortar a operação quando uma fonte específica estiver ausente, compare `info.getDescription()` com uma lista branca e lance uma `RuntimeException` quando a correspondência falhar.

## Exemplo Java Completo – Do Início ao Fim

Juntando tudo, aqui está um programa autônomo que você pode copiar e colar em sua IDE. Certifique‑se de que o JAR do Aspose.Words for Java esteja no seu classpath.

```java
import com.aspose.words.*;
import java.util.*;

public class SaveWordWithFontHandling {
    public static void main(String[] args) throws Exception {
        // ------------------- Configure FontSettings -------------------
        FontSettings fontSettings = new FontSettings();
        // Point to a folder that contains any custom fonts you might need.
        fontSettings.setFontsFolder("C:/CustomFonts", true);
        // Ensure a safe fallback.
        fontSettings.setDefaultFontName("Arial");

        // ------------------- Prepare LoadOptions -------------------
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setFontSettings(fontSettings);

        // ------------------- Warning callback (handle missing fonts) -------------------
        loadOptions.setWarningCallback(new IWarningCallback() {
            private final List<String> missing = new ArrayList<>();

            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBstitution) {
                    String msg = "Font substitution: " + info.getDescription();
                    System.out.println(msg);
                    missing.add(msg);
                }
            }

            public List<String> getMissing() {
                return missing;
            }
        });

        // ------------------- Load the source DOCX -------------------
        Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // ------------------- Save the result -------------------
        doc.save("YOUR_DIRECTORY/output.docx");
        System.out.println("Document saved successfully.");
    }
}
```

Run the program, watch the console for any **font

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}