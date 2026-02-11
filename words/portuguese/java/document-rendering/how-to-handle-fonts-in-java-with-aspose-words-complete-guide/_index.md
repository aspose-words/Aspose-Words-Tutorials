---
category: general
date: 2026-02-10
description: Como lidar com fontes em Java usando Aspose.Words. Aprenda avisos de
  substituição de fontes, callbacks de LoadOptions e tratamento de fontes ausentes
  em algumas etapas.
draft: false
keywords:
- how to handle fonts
- font substitution warnings
- Aspose.Words Java
- LoadOptions warning callback
- MissingFont.docx handling
language: pt
og_description: Como lidar com fontes em Java com Aspose.Words. Este guia mostra passo
  a passo o tratamento de substituição de fontes, callbacks de aviso e gerenciamento
  de fontes ausentes.
og_title: Como lidar com fontes em Java – Tutorial completo do Aspose.Words
tags:
- Java
- Aspose.Words
- Document Processing
title: Como lidar com fontes em Java com Aspose.Words – Guia completo
url: /pt/java/document-rendering/how-to-handle-fonts-in-java-with-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como lidar com fontes em Java – Guia completo

Já se perguntou **como lidar com fontes** quando um documento Word referencia uma tipografia que não está instalada no seu servidor? É um cenário que confunde muitos desenvolvedores, especialmente quando você está automatizando a geração ou conversão de documentos com Aspose.Words. A boa notícia? Você pode capturar cada evento de substituição de fonte e reagir a ele — sem adivinhações.

Neste tutorial vamos percorrer um exemplo do mundo real que mostra **como lidar com fontes** usando Aspose.Words para Java. Vamos conectar um callback de aviso, filtrar apenas avisos de substituição de fonte e imprimir uma mensagem amigável para cada fonte ausente. Ao final, você entenderá por que isso importa, como implementá‑lo de forma limpa e o que esperar quando o código for executado.

> **O que você receberá:** uma classe Java completa, pronta‑para‑executar, uma explicação de cada linha, dicas para uso em produção e uma maneira rápida de verificar a saída.

---

## Pré-requisitos

Antes de mergulharmos, certifique‑se de que você tem:

- **Java 8** (ou mais recente) instalado na sua máquina.  
- **Aspose.Words for Java** JAR (a versão mais recente em 2026‑02, por exemplo, `aspose-words-23.11.jar`).  
- Um documento de exemplo (`MissingFont.docx`) que referencia uma fonte que você não tem instalada.  
- Um ambiente de desenvolvimento (IntelliJ IDEA, Eclipse ou até mesmo um editor de texto simples + linha de comando).

Nenhum framework adicional é necessário — apenas Java puro e o JAR do Aspose.Words.

![Diagrama mostrando como lidar com fontes em Java com Aspose.Words](https://example.com/handle-fonts-diagram.png "diagrama de como lidar com fontes")

*Texto alternativo da imagem: diagrama de como lidar com fontes*

---

## Etapa 1 – Configurar um Callback de Aviso (o núcleo de **como lidar com fontes**)

Quando o Aspose.Words carrega um documento, ele gera uma série de objetos `WarningInfo` para tudo que não está perfeito. Ao anexar um `IWarningCallback`, você pode interceptar esses avisos em tempo real.

```java
import com.aspose.words.*;

public class FontSubstitutionDemo {

    public static void main(String[] args) throws Exception {

        // 1️⃣ Create LoadOptions and register a warning callback.
        LoadOptions loadOptions = new LoadOptions();

        // The callback will be invoked for every warning Aspose.Words emits.
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // 2️⃣ Filter for FONT_SUBSTITUTION warnings only.
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Substituted font: " + info.getDescription());
                }
                // Other warning types are ignored – you could log them here if you wish.
            }
        });
```

**Por que isso importa:**  
Se você pular o callback, o Aspose.Words troca silenciosamente fontes ausentes por uma padrão, e você nunca saberá quais fontes estavam faltando. Ao tratar o aviso, você ganha visibilidade e pode decidir se incorpora uma fonte de fallback, registra o problema ou até aborta a operação.

---

## Etapa 2 – Carregar o Documento Usando o `LoadOptions` Configurado

Agora que o callback está pronto, simplesmente carregamos o documento. A instância de `LoadOptions` que criamos acima é passada diretamente ao construtor `Document`.

```java
        // 3️⃣ Load a document that may contain missing fonts.
        // Replace the path with the actual location of your test file.
        Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);

        // At this point the warning callback runs automatically.
        // Any font substitution will be printed to the console.
```

**O que esperar:**  
Quando `MissingFont.docx` referencia, por exemplo, *Comic Sans MS* mas o servidor tem apenas *Arial*, o callback imprime algo como:

```
Substituted font: Font 'Comic Sans MS' was substituted with 'Arial'.
```

Se o documento for carregado sem fontes ausentes, nada será impresso — exatamente o que você deseja ao **lidar com fontes** de forma elegante.

---

## Etapa 3 – (Opcional) Verificar a Tabela de Fontes do Documento

Às vezes é necessário inspecionar quais fontes o documento realmente usa após o carregamento. O Aspose.Words facilita isso.

```java
        // Optional: List all fonts the document thinks it has.
        FontInfoCollection fonts = document.getFontInfos();
        System.out.println("\n--- Fonts used in the document ---");
        for (FontInfo font : fonts) {
            System.out.println(font.getFullName());
        }
    }
}
```

**Quando usar isso:**  
Se você está construindo um processador em lote que deve relatar fontes ausentes antes de publicar um PDF, imprimir a tabela de fontes fornece uma verificação final de sanidade.

---

## Exemplo Completo e Executável

Juntando tudo, aqui está a classe completa que você pode copiar‑colar em `FontSubstitutionDemo.java` e executar:

```java
import com.aspose.words.*;

public class FontSubstitutionDemo {
    public static void main(String[] args) throws Exception {

        // Step 1 – Create LoadOptions with a warning callback.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // Handle only font‑substitution warnings.
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Substituted font: " + info.getDescription());
                }
            }
        });

        // Step 2 – Load the document that may contain missing fonts.
        Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);

        // Step 3 – (Optional) List the fonts the document finally uses.
        FontInfoCollection fonts = document.getFontInfos();
        System.out.println("\n--- Fonts used in the document ---");
        for (FontInfo font : fonts) {
            System.out.println(font.getFullName());
        }
    }
}
```

**Executando o código:**  

```bash
javac -cp "aspose-words-23.11.jar" FontSubstitutionDemo.java
java -cp ".:aspose-words-23.11.jar" FontSubstitutionDemo
```

Você deverá ver as mensagens de substituição seguidas da lista final de fontes.

---

## Perguntas Frequentes & Casos Limite

### E se eu precisar substituir a fonte eu mesmo?

O callback de aviso apenas informa *o que* foi substituído. Se quiser forçar um fallback específico, pode usar `FontSettings`:

```java
FontSettings fontSettings = new FontSettings();
fontSettings.setSubstitutionSettings(new FontSubstitutionSettings() {{
    getTableSubstitution().addSubstitutes("MissingFont", "Arial");
}});
loadOptions.setFontSettings(fontSettings);
```

Agora qualquer ocorrência de “MissingFont” será substituída por “Arial” antes do documento ser carregado.

### Isso funciona ao salvar em PDF?

Absolutamente. O mesmo callback é disparado durante `document.save("out.pdf")` se o renderizador PDF também precisar substituir fontes. Basta manter o mesmo `LoadOptions` ou anexar um novo callback a `PdfSaveOptions`.

### Como isso se comporta em um ambiente multi‑thread?

`LoadOptions` **não** é thread‑safe, portanto crie uma nova instância por thread. O próprio callback pode ser sem estado (como mostrado) ou você pode injetar um logger que seja consciente de threads.

### E se a fonte ausente for uma fonte corporativa personalizada?

Normalmente você incorpora essa fonte na pasta de fontes do servidor e aponta o Aspose.Words para ela via `FontSettings.setFontsFolder("path/to/fonts", true)`. O callback então deixará de disparar para essa fonte, pois ela não estará mais ausente.

---

## Dicas Profissionais para Manipulação de Fontes em Produção

- **Registre, não apenas `System.out.println`** – use um framework de logging adequado (SLF4J, Log4j) para capturar avisos no seu sistema de monitoramento.  
- **Cache de buscas de fontes** – se estiver processando milhares de documentos, evite escanear repetidamente o diretório de fontes do SO. Carregue as fontes uma vez em uma instância de `FontSettings` e reutilize‑a.  
- **Falhe rápido quando fontes críticas estiverem ausentes** – você pode lançar uma exceção dentro do callback se uma fonte específica for mandatória para conformidade de branding.  
- **Teste com uma variedade de documentos** – inclua PDFs, DOCX e arquivos DOC; cada formato pode disparar tipos diferentes de avisos.  

---

## Conclusão

Cobrimos **como lidar com fontes** em Java usando Aspose.Words do início ao fim:

1. Anexe um `IWarningCallback` para capturar avisos de substituição de fonte.  
2. Carregue o documento com `LoadOptions` para que o callback seja executado automaticamente.  
3. (Opcional) Inspecione a lista final de fontes para confirmar o resultado.  

Seguindo esses passos, você obtém total visibilidade sobre fontes ausentes, pode aplicar políticas corporativas de fontes e evita substituições silenciosas que poderiam arruinar a aparência dos PDFs ou arquivos Word gerados.

Pronto para o próximo desafio? Experimente trocar o callback para registrar *todos* os avisos, teste `FontSettings` para regras de substituição personalizadas ou integre essa lógica em um microserviço Spring‑Boot que processa documentos em tempo real.

Feliz codificação, e que seus documentos sempre sejam renderizados com a tipografia correta!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}