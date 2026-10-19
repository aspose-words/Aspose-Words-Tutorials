---
category: general
date: 2026-02-15
description: Aprenda como obter fontes ausentes ao carregar um documento Word em Java
  usando Aspose.Words. Inclui callbacks de aviso e tratamento de substituição de fontes.
draft: false
keywords:
- how to get missing fonts
- Aspose.Words missing font
- font substitution warning
- Java LoadOptions warning callback
- document processing Java
language: pt
og_description: Como obter fontes ausentes em Java com Aspose.Words. Descubra callbacks
  de aviso, tratamento de substituição de fontes e as melhores práticas para o processamento
  de documentos.
og_title: Como Obter Fontes Ausentes no Java – Guia Aspose.Words
tags:
- Aspose.Words
- Java
- Font Management
title: Como obter fontes ausentes no Java – Guia Aspose.Words
url: /pt/java/document-loading-and-saving/how-to-get-missing-fonts-in-java-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como Obter Fontes Ausentes em Java – Guia Aspose.Words

Já abriu um documento Word em Java e viu substituições estranhas de fontes, perguntando‑se **como obter fontes ausentes**? Você não é o primeiro a enfrentar essa surpresa. Em muitas aplicações corporativas, avisos de fontes ausentes podem comprometer a fidelidade visual de relatórios, contratos ou materiais de marketing.

A boa notícia? Aspose.Words oferece uma maneira simples de capturar esses avisos por meio de um callback, permitindo que você registre, substitua ou até alerte os usuários antes que o documento seja renderizado. Neste tutorial, percorreremos um exemplo completo e executável que mostra **como obter fontes ausentes**, explica por que o callback é importante e aborda alguns truques de casos extremos que você pode precisar em projetos reais.

> **Dica profissional:** Se você já está usando Aspose.Words 22.12 ou mais recente, a API mostrada abaixo funciona imediatamente, sem configuração adicional.

---

![Diagrama ilustrando como obter fontes ausentes usando o callback de aviso do Aspose.Words](how-to-get-missing-fonts-diagram.png "diagrama de como obter fontes ausentes")

## O que este tutorial cobre

- Configurar um **callback de aviso Java LoadOptions** para capturar avisos de substituição de fontes.  
- Filtrar os avisos para que você veja apenas os relacionados a fontes ausentes.  
- Imprimir um relatório claro e legível sobre quais fontes foram substituídas e por quais foram substituídas.  
- Dicas para lidar com documentos grandes, personalizar o nível de aviso e integrar a solução em um pipeline de processamento maior.

Ao final deste guia, você será capaz de responder à pergunta “**como obter fontes ausentes**?” com um trecho de código pronto para execução e um entendimento sólido da mecânica subjacente.

### Pré‑requisitos

- Java 8 ou superior instalado.  
- Biblioteca Aspose.Words for Java (download do site oficial ou adição via Maven/Gradle).  
- Um documento Word que faça referência a uma fonte não instalada na sua máquina (por exemplo, `MissingFont.docx`).  

Se estiver faltando algum desses itens, obtenha a biblioteca agora—adicioná‑la ao Maven é tão simples quanto:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version> <!-- replace with the latest version -->
</dependency>
```

---

## Etapa 1: Preparar uma coleção para avisos de substituição de fontes

Antes de carregar o documento, precisamos de um local para armazenar quaisquer avisos que o Aspose.Words emita. Um `ArrayList<WarningInfo>` funciona bem porque preserva a ordem e permite iteração posterior.

```java
import com.aspose.words.*;
import java.util.ArrayList;
import java.util.List;

// Step 1: Create a list that will hold warning information.
List<WarningInfo> fontWarnings = new ArrayList<>();
```

*Por que isso importa:* O callback de aviso pode ser disparado dezenas de vezes para um único arquivo—pense em cada glifo ausente, cada problema de imagem incorporada, etc. Ao coletá‑los primeiro, você mantém a fase de carregamento rápida e adia o processamento para um loop controlado.

---

## Etapa 2: Configurar LoadOptions com um callback de aviso

Aspose.Words permite que você conecte um `IWarningCallback`. Dentro do callback, adicionaremos cada `WarningInfo` à nossa lista da Etapa 1.

```java
// Step 2: Set up LoadOptions with a custom warning callback.
LoadOptions loadOptions = new LoadOptions();
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Capture every warning; we'll filter later.
        fontWarnings.add(info);
    }
});
```

*Explicação:* O método `warning` é invocado **síncronamente** durante o carregamento do documento. Ao simplesmente inserir o `WarningInfo` em `fontWarnings`, evitamos qualquer I/O pesado (como gravação em arquivo) que poderia desacelerar o carregamento. Esse padrão—coletar‑então‑processar—é a forma recomendada de lidar com grandes lotes de avisos.

---

## Etapa 3: Carregar o documento usando as opções configuradas

Agora realmente lemos o arquivo Word. Se o documento contiver fontes que não estejam instaladas, o Aspose.Words substituirá‑as automaticamente e disparará o callback de aviso que configuramos.

```java
// Step 3: Load the document with the warning‑aware LoadOptions.
String filePath = "YOUR_DIRECTORY/MissingFont.docx"; // adjust to your environment
Document doc = new Document(filePath, loadOptions);
```

*O que acontece nos bastidores?* O Aspose.Words analisa a tabela de fontes do arquivo, compara‑a com as fontes disponíveis no sistema operacional host e, para cada entrada ausente, cria um `WarningInfo` com `WarningSource.FontSubstitution`. Essa fonte é a chave que usaremos para isolar os avisos de fontes ausentes.

---

## Etapa 4: Filtrar e exibir apenas avisos de substituição de fontes

Após o carregamento, `fontWarnings` pode conter uma mistura de mensagens (por exemplo, recursos obsoletos, problemas de imagem). Só nos interessam as fontes ausentes, então percorremos a lista e imprimimos um relatório conciso.

```java
// Step 4: Output any font‑substitution warnings that were captured.
for (WarningInfo warning : fontWarnings) {
    if (warning.getSource() == WarningSource.FontSubstitution) {
        System.out.println("Substituted '" + warning.getDescription() + "' with '" +
                           warning.getAdditionalInfo() + "'");
    }
}
```

**Saída de exemplo**

```
Substituted 'Comic Sans MS' with 'Arial'
Substituted 'Times New Roman PS' with 'Times New Roman'
```

*Por que isso é útil:* O campo `description` indica qual fonte o documento solicitou, enquanto `additionalInfo` informa qual fonte o Aspose.Words realmente utilizou. Com esses dados, você pode:

- Solicitar ao usuário que instale a fonte ausente.  
- Incorporar programaticamente uma fonte substituta no documento (`doc.getFontInfos().add(...)`).  
- Registrar o evento para auditorias de conformidade.

---

## Lidando com casos de borda e variações comuns

### 1. Suprimindo avisos que não são de fonte

Se você quiser apenas mensagens relacionadas a fontes, pode apertar o callback:

```java
loadOptions.setWarningCallback(info -> {
    if (info.getSource() == WarningSource.FontSubstitution) {
        fontWarnings.add(info);
    }
});
```

Isso reduz o consumo de memória ao processar lotes enormes.

### 2. Ajustando a severidade dos avisos

Aspose.Words categoriza avisos por `WarningType`. Para fontes ausentes, você normalmente verá `WarningType.FontSubstitution`. Se precisar tratá‑los como erros (por exemplo, abortar o carregamento), lance uma exceção dentro do callback:

```java
loadOptions.setWarningCallback(info -> {
    if (info.getSource() == WarningSource.FontSubstitution) {
        throw new RuntimeException("Missing font detected: " + info.getDescription());
    }
});
```

### 3. Trabalhando com streams em vez de arquivos

Às vezes, documentos vêm de um banco de dados ou de uma requisição HTTP. A mesma abordagem funciona com um `InputStream`:

```java
InputStream docStream = new ByteArrayInputStream(bytesFromDb);
Document doc = new Document(docStream, loadOptions);
```

Apenas lembre‑se de fechar o stream após o carregamento.

### 4. Usando uma pasta de fontes personalizada

Se você possui uma coleção de fontes corporativas armazenada em um drive compartilhado, aponte o Aspose.Words para essa pasta:

```java
loadOptions.setFontSettings(new FontSettings());
loadOptions.getFontSettings().setFontsFolder("C:/CorporateFonts", true);
```

Agora a biblioteca procurará lá *antes* de recorrer às fontes do sistema, reduzindo drasticamente o número de avisos de fontes ausentes.

---

## Exemplo completo em funcionamento

Juntando tudo, aqui está uma classe autônoma que você pode inserir em qualquer projeto Java:

```java
import com.aspose.words.*;
import java.util.ArrayList;
import java.util.List;

public class MissingFontDetector {

    public static void main(String[] args) {
        // 1️⃣ Prepare a collection for warnings.
        List<WarningInfo> fontWarnings = new ArrayList<>();

        // 2️⃣ Create LoadOptions with a warning callback.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(info -> fontWarnings.add(info));

        // (Optional) Point to a custom font folder.
        // FontSettings fontSettings = new FontSettings();
        // fontSettings.setFontsFolder("C:/CorporateFonts", true);
        // loadOptions.setFontSettings(fontSettings);

        // 3️⃣ Load the document.
        String docPath = "YOUR_DIRECTORY/MissingFont.docx";
        Document doc;
        try {
            doc = new Document(docPath, loadOptions);
        } catch (Exception e) {
            System.err.println("Failed to load document: " + e.getMessage());
            return;
        }

        // 4️⃣ Print missing‑font warnings.
        System.out.println("=== Missing Font Report ===");
        for (WarningInfo warning : fontWarnings) {
            if (warning.getSource() == WarningSource.FontSubstitution) {
                System.out.println("Substituted '" + warning.getDescription() + "' with '" +
                                   warning.getAdditionalInfo() + "'");
            }
        }
        System.out.println("=== End of Report ===");
    }
}
```

Execute este programa e você verá uma lista organizada de cada fonte que o Aspose.Words teve que substituir. Sem bibliotecas extras, sem mágica oculta—apenas Java puro e o poder da API de **fonte ausente do Aspose.Words**.

---

## Conclusão

Respondemos à questão central **como obter fontes ausentes** em um ambiente Java usando Aspose.Words. Ao anexar um callback de aviso ao `LoadOptions`, coletar objetos `WarningInfo` e filtrar por fontes de `FontSubstitution`, você obtém visibilidade total sobre problemas de fontes antes de qualquer renderização. A abordagem escala de utilitários de arquivo único a processadores de lote massivos, e é flexível o suficiente para acomodar pastas de fontes personalizadas, tratamento de severidade ou entradas baseadas em streams.

Próximos passos? Tente incorporar as fontes substituídas diretamente no documento (`doc.getFontInfos().add(...)`) para que o arquivo final seja realmente autocontido, ou integre o relatório de avisos a um painel de monitoramento. Você também pode explorar tópicos relacionados, como **processamento de documentos Java**, **aviso de substituição de fonte Aspose.Words** e **callback de aviso Java LoadOptions**, para aprofundar sua expertise.

Feliz codificação, e que seus documentos sempre renderizem com as fontes que você espera!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}