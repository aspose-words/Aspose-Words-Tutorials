---
category: general
date: 2026-03-19
description: Aprenda como capturar avisos no Aspose.Words for Java e detectar fontes
  ausentes. Este guia passo a passo também mostra como lidar com fontes ausentes de
  forma elegante.
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- how to detect missing fonts
- handle missing fonts
language: pt
og_description: Como capturar avisos no Aspose.Words for Java, detectar fontes ausentes
  e tratar fontes ausentes com um exemplo de código completo.
og_title: Como Capturar Avisos – Detectar Fontes Ausentes no Aspose.Words
tags:
- Aspose.Words
- Java
- Font Substitution
- Document Processing
title: Como Capturar Avisos – Detectar Fontes Ausentes no Aspose.Words
url: /pt/java/document-rendering/how-to-capture-warnings-detect-missing-fonts-in-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como Capturar Avisos – Detectar Fontes Ausentes no Aspose.Words

Já se perguntou **como capturar avisos** quando um documento Word é carregado e algumas fontes não estão disponíveis na máquina? Você não está sozinho. Em muitos projetos reais, fontes ausentes causam alterações silenciosas no layout, e a única maneira de saber o que aconteceu é ouvindo o fluxo de avisos que o Aspose.Words emite.  

Neste tutorial vamos percorrer um exemplo completo, pronto‑para‑executar, que **detecta fontes ausentes**, mostra **como detectar fontes ausentes** programaticamente e ainda dá uma dica rápida sobre **como lidar com fontes ausentes** para que sua saída permaneça previsível.

> **Nota rápida:** O código funciona com Aspose.Words 23.9 (ou superior) e requer Java 8+.

---

## O que Você Precisa

- **Aspose.Words for Java** (dependência Maven/Gradle ou JAR no classpath)  
- Um arquivo Word (`input.docx`) que faça referência a uma fonte não instalada no seu sistema (por exemplo, “Comic Sans MS”)  
- Uma IDE Java ou um simples ambiente de linha de comando `javac`/`java`  

Nenhuma outra biblioteca é necessária — todo o restante está dentro do pacote Aspose.Words.

---

## Etapa 1 – Configurar LoadOptions para Capturar Avisos  

Para começar a ouvir avisos, você deve criar uma instância de `LoadOptions`. Esse objeto indica ao carregador que ele deve acompanhar quaisquer problemas que encontrar, como fontes ausentes.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Create LoadOptions that will store warning information
        LoadOptions loadOptions = new LoadOptions();

        // ... the rest of the code follows
```

**Por que isso importa:** Sem `LoadOptions` o carregador substitui silenciosamente fontes ausentes pela fonte padrão do sistema, e você nunca saberia que uma substituição ocorreu. Habilitar avisos fornece total visibilidade.

---

## Etapa 2 – Carregar o Documento Usando o LoadOptions  

Agora realmente carregamos o documento. O `LoadOptions` que criamos é passado ao construtor, de modo que quaisquer avisos gerados durante a análise são capturados.

```java
        // Step 2: Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**Dica:** Se você estiver processando muitos arquivos em lote, reutilize a mesma instância de `LoadOptions` para evitar a criação desnecessária de objetos.

---

## Etapa 3 – Iterar Sobre os Avisos Capturados  

Aspose.Words armazena cada aviso como um objeto `WarningInfo`. Nós nos importamos apenas com avisos relacionados a fontes, então filtramos por `FontSubstitutionWarningInfo`.

```java
        // Step 3: Loop through all warnings generated while loading
        for (WarningInfo warning : document.getWarnings()) {
            // Step 3a: Keep only font substitution warnings
            if (warning instanceof FontSubstitutionWarningInfo) {
                FontSubstitutionWarningInfo fontWarning = (FontSubstitutionWarningInfo) warning;

                // Step 4: Output the requested and actual font names
                System.out.println("Requested: " + fontWarning.getRequestedFontName()
                        + " → Substituted: " + fontWarning.getActualFontName());
            }
        }
    }
}
```

**Explicação:**  
- `document.getWarnings()` devolve uma lista de todos os avisos que ocorreram durante o carregamento.  
- `FontSubstitutionWarningInfo` contém duas informações cruciais: a **fonte solicitada** (a que o DOCX pediu) e a **fonte real** que o Aspose.Words utilizou como substituta.  
- Ao imprimir ambas, você vê instantaneamente quais fontes estão ausentes e qual substituição foi feita.

---

## Etapa 4 – (Opcional) Lidar Programaticamente com Fontes Ausentes  

Capturar avisos é apenas metade da história. Depois de saber que uma fonte está ausente, você pode querer **lidar com fontes ausentes** fornecendo uma substituição personalizada ou registrando o problema para revisão posterior.

```java
                // Optional: Replace the missing font with a known fallback
                FontSettings fontSettings = new FontSettings();
                fontSettings.getSubstitutionSettings().getTableSubstitution()
                    .addSubstitutes(fontWarning.getRequestedFontName(), "Arial");
                document.setFontSettings(fontSettings);
```

**Por que fazer isso?**  
- Garante renderização consistente entre máquinas.  
- Impede alterações inesperadas de layout em PDFs ou imagens geradas posteriormente.  

Você também pode armazenar os detalhes do aviso em um banco de dados, enviar um e‑mail para a equipe de conteúdo ou até abortar o processo se uma fonte crítica estiver ausente.

---

## Exemplo Completo Funcional  

Abaixo está o programa completo e executável. Basta substituir `YOUR_DIRECTORY/input.docx` pelo caminho do seu arquivo de teste, adicionar o JAR do Aspose.Words ao classpath e executar.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // 1️⃣ Create LoadOptions to capture warnings
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // 3️⃣ Iterate through all warnings
        for (WarningInfo warning : document.getWarnings()) {
            // 3a️⃣ Filter only font substitution warnings
            if (warning instanceof FontSubstitutionWarningInfo) {
                FontSubstitutionWarningInfo fontWarning = (FontSubstitutionWarningInfo) warning;

                // 4️⃣ Display the requested and actual font names
                System.out.println("Requested: " + fontWarning.getRequestedFontName()
                        + " → Substituted: " + fontWarning.getActualFontName());

                // 5️⃣ (Optional) Provide a custom fallback
                FontSettings fontSettings = new FontSettings();
                fontSettings.getSubstitutionSettings().getTableSubstitution()
                    .addSubstitutes(fontWarning.getRequestedFontName(), "Arial");
                document.setFontSettings(fontSettings);
            }
        }

        // 6️⃣ Save the document if you need to see the result with the fallback applied
        document.save("output.docx");
    }
}
```

**Saída esperada** (quando “Comic Sans MS” está ausente):

```
Requested: Comic Sans MS → Substituted: Arial
```

Depois que o código opcional de fallback for executado, o `output.docx` salvo será renderizado usando **Arial** onde “Comic Sans MS” era referenciada originalmente.

---

## Perguntas Frequentes & Casos Limite  

| Pergunta | Resposta |
|----------|----------|
| *E se o documento tiver várias fontes ausentes?* | O loop emitirá um aviso para cada uma. Você pode coletá‑las em um `Map<String, String>` para processamento em lote. |
| *Isso funciona para PDFs gerados a partir do documento?* | Absolutamente. A substituição de fontes ocorre durante a fase de carregamento, então qualquer exportação posterior (PDF, HTML, imagem) usa as fontes resolvidas. |
| *Posso suprimir os avisos ao invés de capturá‑los?* | Sim — defina `loadOptions.setWarningCallback(null);` mas você perderá a visibilidade sobre fontes ausentes. |
| *A lista de avisos é limpa após salvar?* | A coleção de avisos pertence à instância `Document`. Depois de chamar `document.save()`, a lista permanece inalterada a menos que você crie um novo `Document`. |
| *E quanto às fontes personalizadas incorporadas no DOCX?* | Fontes incorporadas são tratadas como disponíveis; o Aspose.Words as usará mesmo que não estejam instaladas no sistema host. |

---

## Dicas Profissionais para Uso em Produção  

- **Cache de FontSettings:** Se você processa centenas de arquivos, crie um único `FontSettings` com suas substituições preferidas e reutilize‑o para evitar sobrecarga.  
- **Log de Dados Estruturados:** Em vez de usar `System.out` puro, grave os avisos em um log JSON — isso torna a análise posterior (ex.: “fontes mais ausentes”) trivial.  
- **Validação Antecipada:** Execute um “dry‑load” rápido com `LoadOptions` antes do processamento pesado; abortar cedo se fontes críticas estiverem ausentes.  
- **Segurança de Thread:** Objetos `Document` não são thread‑safe. Mantenha o processamento de cada arquivo em sua própria thread ou use um `LoadOptions` thread‑local.  

---

## Conclusão  

Agora você sabe **como capturar avisos** no Aspose.Words para Java, **detectar fontes ausentes** e **lidar com fontes ausentes** usando uma estratégia de fallback limpa. Ao aproveitar `LoadOptions` e iterar sobre `document.getWarnings()`, você obtém total insight sobre eventos de substituição de fontes, garantindo que os documentos gerados tenham exatamente a aparência esperada em todos os ambientes.

Pronto para o próximo passo? Experimente estender esse padrão para **detectar imagens ausentes**, **rastrear recursos não suportados** ou até **incorporar automaticamente fontes ausentes** ao arquivo de saída. A mesma abordagem de captura de avisos funciona para muitos outros cenários de processamento de documentos, tornando seu código robusto e preparado para o futuro.

Happy coding, and may your documents always render beautifully!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}