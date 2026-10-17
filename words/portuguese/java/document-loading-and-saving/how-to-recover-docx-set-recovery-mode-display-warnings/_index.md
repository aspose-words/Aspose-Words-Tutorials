---
category: general
date: 2026-03-04
description: Como recuperar arquivos DOCX usando Java – aprenda a definir o modo de
  recuperação e exibir avisos de carregamento para documentos corrompidos em alguns
  passos fáceis.
draft: false
keywords:
- how to recover docx
- set recovery mode
- use recovery mode
- recover corrupted docx
- display load warnings
language: pt
og_description: How to recover DOCX files using Java. This guide shows how to set
  recovery mode and display load warnings when loading corrupted documents.
og_title: Como Recuperar DOCX – Definir Modo de Recuperação e Exibir Avisos
tags:
- Java
- Aspose.Words
- Document Recovery
title: Como recuperar DOCX – Definir modo de recuperação e exibir avisos
url: /pt/java/document-loading-and-saving/how-to-recover-docx-set-recovery-mode-display-warnings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como Recuperar DOCX – Definir Modo de Recuperação e Exibir Avisos

Já abriu um arquivo **DOCX** e viu texto embaralhado ou um parágrafo ausente? É nesse momento que você começa a se perguntar *como recuperar docx* sem perder horas de trabalho. A boa notícia é que o Aspose.Words for Java oferece um modo de recuperação embutido que identifica problemas, mantém as partes boas e ainda informa o que deu errado.

Neste tutorial vamos percorrer os passos exatos para **definir o modo de recuperação**, **usar o modo de recuperação** ao carregar um documento corrompido e **exibir avisos de carregamento** para que você saiba exatamente o que foi reparado. Ao final, você terá um trecho pronto‑para‑executar que recupera um DOCX quebrado e informa quantos avisos foram gerados.

> **Pré‑requisito:** Você precisa do Aspose.Words for Java (v23.9 ou superior) no seu classpath. Se ainda não o tem, obtenha o artefato Maven `com.aspose:aspose-words:23.9` ou faça o download do JAR no site da Aspose.

![como recuperar docx](/images/recover-docx.png)

---

## O Que Este Guia Cobre

* Como configurar **LoadOptions** para controlar o comportamento da recuperação.  
* A diferença entre `RECOVER_WITH_WARNINGS` e `RECOVER_SILENTLY`.  
* Como **exibir avisos de carregamento** após o documento ser aberto.  
* Um programa Java completo e executável que você pode copiar‑colar no seu IDE.

Vamos direto ao ponto—sem enrolação, apenas o que realmente faz o trabalho.

---

## Etapa 1: Preparar Load Options – Escolher o Modo de Recuperação Correto

Antes de tocar no arquivo, você precisa dizer ao Aspose.Words como se comportar ao encontrar dados corrompidos. É aqui que **definir o modo de recuperação** entra em ação.

```java
import com.aspose.words.LoadOptions;
import com.aspose.words.LoadOptions.RecoveryMode;

// Create a LoadOptions instance
LoadOptions loadOptions = new LoadOptions();

// Choose a recovery strategy
// 1️⃣ Recover with warnings – you’ll get a list of issues.
// 2️⃣ Recover silently – the library fixes everything quietly.
loadOptions.setRecoveryMode(RecoveryMode.RECOVER_WITH_WARNINGS);
// Or, if you prefer no output:
// loadOptions.setRecoveryMode(RecoveryMode.RECOVER_SILENTLY);
```

*Por que isso importa:* `RECOVER_WITH_WARNINGS` é perfeito quando você precisa auditar o processo de correção, enquanto `RECOVER_SILENTLY` é útil para jobs em lote onde você não quer ruído no console.

---

## Etapa 2: Carregar o DOCX Corrompido Usando as Opções Configuradas

Agora que as **opções de carregamento** estão prontas, abrir o arquivo é simples. Observe como passamos o objeto `loadOptions` para o construtor `Document`—esta é a etapa de **usar o modo de recuperação**.

```java
import com.aspose.words.Document;

// Path to the potentially corrupted file
String corruptedPath = "C:/Docs/corrupted.docx";

// Load the document with the previously defined options
Document document = new Document(corruptedPath, loadOptions);
```

Se o arquivo estiver além do reparo, o Aspose.Words ainda lançará uma `FileCorruptedException`. Na maioria dos cenários reais, porém, a biblioteca salva as partes legíveis e sinaliza o restante.

---

## Etapa 3: Exibir Avisos de Carregamento – Saber Exatamente O Que Foi Corrigido

Depois que o documento é carregado, você pode consultar a coleção de avisos. Esta é a parte de **exibir avisos de carregamento** do nosso tutorial.

```java
// Retrieve the warning collection
int warningCount = document.getWarningInfo().size();

// Print a friendly message
System.out.println("Document loaded with warnings: " + warningCount);

// Optional: iterate and print each warning for deeper insight
document.getWarningInfo().forEach(w -> System.out.println("- " + w.getDescription()));
```

Uma saída típica pode ser assim:

```
Document loaded with warnings: 3
- Warning: Missing end tag for <w:p>.
- Warning: Invalid hyperlink target.
- Warning: Unsupported bitmap format.
```

Ver a lista permite decidir se você precisa corrigir algo manualmente depois ou se o documento recuperado já está bom o suficiente para o seu caso de uso.

---

## Exemplo Completo – Do Início ao Fim

Abaixo está uma classe Java autônoma que você pode inserir em qualquer projeto. Ela demonstra **como recuperar docx**, **definir o modo de recuperação**, **usar o modo de recuperação** e **exibir avisos de carregamento**—tudo em um único passo.

```java
import com.aspose.words.*;

public class DocxRecoveryDemo {

    public static void main(String[] args) {
        try {
            // 1️⃣ Prepare LoadOptions with the desired recovery strategy
            LoadOptions loadOptions = new LoadOptions();
            loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RECOVER_WITH_WARNINGS);
            // Uncomment the line below to suppress warnings
            // loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RECOVER_SILENTLY);

            // 2️⃣ Load the potentially corrupted DOCX file
            String filePath = "C:/Docs/corrupted.docx";
            Document doc = new Document(filePath, loadOptions);

            // 3️⃣ Show how many warnings were generated
            int warnings = doc.getWarningInfo().size();
            System.out.println("Document loaded with warnings: " + warnings);

            // Optional: print each warning for debugging
            for (WarningInfo wi : doc.getWarningInfo()) {
                System.out.println("- " + wi.getDescription());
            }

            // 4️⃣ Save the recovered document (optional)
            String outputPath = "C:/Docs/recovered.docx";
            doc.save(outputPath);
            System.out.println("Recovered document saved to: " + outputPath);

        } catch (Exception e) {
            System.err.println("Failed to recover document: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**Resultado esperado:** O programa imprime o número de avisos, lista cada um e grava um `recovered.docx` limpo no disco. Mesmo que o arquivo original estivesse meio quebrado, a saída conterá todo o conteúdo recuperável.

---

## Perguntas Frequentes & Casos de Borda

### E se eu precisar recuperar um DOCX a partir de um stream em vez de um caminho de arquivo?
Basta passar um `InputStream` para o construtor `Document` junto com o mesmo `LoadOptions`. A API funciona de forma idêntica.

```java
InputStream is = new FileInputStream("corrupted.docx");
Document doc = new Document(is, loadOptions);
```

### Posso mudar o modo de recuperação depois que o documento já foi carregado?
Não. O modo é somente leitura durante a fase de carregamento. Se precisar de uma estratégia diferente, recarregue o arquivo com uma nova instância de `LoadOptions`.

### Como **recuperar docx corrompido** difere de simplesmente abri‑lo no Microsoft Word?
O Word tenta auto‑reparar, mas costuma ocultar os detalhes. O Aspose.Words fornece uma lista programática de cada problema via **exibir avisos de carregamento**, o que é inestimável para pipelines automatizados.

### Há penalidade de desempenho ao usar `RECOVER_WITH_WARNINGS`?
Um pouco—coletar avisos adiciona overhead, mas é insignificante para a maioria dos arquivos (<5 MB). Para processamento em massa onde a velocidade importa, troque para `RECOVER_SILENTLY`.

---

## Dicas Profissionais & Armadilhas

* **Dica profissional:** Sempre registre os avisos em um arquivo ao processar lotes. Assim você pode auditar arquivos problemáticos depois sem poluir o console.
* **Cuidado com:** Arquivos DOCX muito grandes (>100 MB) podem causar `OutOfMemoryError` se você também habilitar `RECOVER_WITH_WARNINGS`. Considere aumentar o heap da JVM ou usar `RECOVER_SILENTLY` nesses casos.
* **Sugestão:** Após a recuperação, execute uma verificação rápida de sanidade—por exemplo, `doc.getSections().size()`—para garantir que a estrutura do documento está íntegra antes de entregá‑la a serviços downstream.

---

## Conclusão

Acabamos de cobrir **como recuperar docx** configurando **opções de carregamento**, **definindo o modo de recuperação**, **usando o modo de recuperação** e **exibindo avisos de carregamento** para qualquer DOCX corrompido que você encontrar. O exemplo completo acima está pronto para copiar‑colar, executar e adaptar aos seus fluxos de trabalho.

Próximos passos? Experimente trocar `RECOVER_WITH_WARNINGS` por `RECOVER_SILENTLY` em um job de alto volume, ou integre a lista de avisos ao seu sistema de monitoramento. Você também pode explorar outros recursos do Aspose.Words, como **proteção de documento** ou **conversão de formato**—todos respeitando as mesmas configurações de recuperação.

Tem mais perguntas sobre recuperação de documentos, manipulação de outros formatos Office ou ajustes nas configurações do Aspose.Words? Deixe um comentário, e feliz codificação!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}