---
category: general
date: 2026-02-15
description: O modo de recuperação permite carregar o documento com recuperação, facilitando
  a recuperação de documentos do Word corrompidos e corrigindo erros de recuperação
  de documentos do Word.
draft: false
keywords:
- set recovery mode
- recover broken word document
- load document with recovery
- recover word document errors
language: pt
og_description: Configurar o modo de recuperação é a chave para carregar um documento
  com recuperação, permitindo que você recupere erros de documentos Word corrompidos
  em Java.
og_title: ativar modo de recuperação – Recupere rapidamente documentos Word corrompidos
tags:
- Aspose.Words
- Java
- Document Recovery
title: Definir modo de recuperação para recuperar documento Word corrompido
url: /pt/java/document-loading-and-saving/set-recovery-mode-to-recover-broken-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# set recovery mode – Como Recuperar um Documento Word Corrompido com Aspose.Words

Já tentou abrir um arquivo Word que de repente se recusa a carregar? Você pode estar olhando para um *.docx* corrompido e se perguntando se precisa começar do zero. A boa notícia? **set recovery mode** no Aspose.Words oferece uma maneira elegante de *load document with recovery* e manter a maior parte do conteúdo intacta.  

Neste tutorial você aprenderá exatamente como **set recovery mode**, por que a opção *RELAXED* costuma ser a melhor escolha para arquivos quebrados e como lidar com os ocasionais *recover word document errors* que ainda escapam. Sem ferramentas externas, apenas Java puro e algumas linhas de código.

> **O que você levará consigo:** um exemplo completo e executável que carrega um arquivo Word corrompido, ignora as partes ilegíveis e deixa você com um objeto `Document` utilizável pronto para processamento adicional.

---

## Pré-requisitos

Antes de começarmos, certifique-se de que você tem:

- **Aspose.Words for Java** (v24.9 ou mais recente) adicionado ao seu projeto via Maven ou JAR manual.
- Um arquivo **corrupted .docx** que você deseja testar (vamos chamá‑lo de `Corrupted.docx`).
- Conhecimento básico de Java – não é preciso ser um mago do processamento de Word, apenas estar confortável com um método `main`.

Se estiver faltando algum desses itens, obtenha o JAR mais recente do Aspose.Words no [official site](https://products.aspose.com/words/java) e adicione‑o ao seu classpath. É só isso—nenhuma dependência extra.

---

## Etapa 1: Entender os Modos de Recuperação

Aspose.Words oferece duas estratégias de recuperação:

| Modo | Comportamento | Quando usar |
|------|----------------|--------------|
| **RELAXED** | Ignora partes ilegíveis, mantém o resto. | A maioria dos arquivos corrompidos – você quer **recover broken word document** sem exceção. |
| **STRICT** | Lança uma exceção em qualquer erro. | Quando você precisa garantir um carregamento perfeito e sem erros (raro para fontes corrompidas). |

> **Dica profissional:** *RELAXED* é o padrão para cenários de “apenas obter algo de volta”, enquanto *STRICT* é útil em pipelines automatizados onde uma falha deve interromper o processo.

---

## Etapa 2: Criar um Objeto `LoadOptions` e **set recovery mode**

É aqui que a palavra‑chave principal aparece no código. Definimos explicitamente **set recovery mode** em uma instância de `LoadOptions` antes de carregar o arquivo.

```java
import com.aspose.words.*;

public class RecoverWordDocument {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create LoadOptions and choose a recovery mode.
        // RELAXED will skip unreadable parts, while STRICT throws an exception.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RELAXED); // <-- set recovery mode

        // 2️⃣ Load the potentially corrupted document using the configured options.
        Document doc = new Document("YOUR_DIRECTORY/Corrupted.docx", loadOptions);

        // 3️⃣ Verify that the document loaded and optionally save a cleaned copy.
        System.out.println("Document loaded successfully. Page count: " + doc.getPageCount());
        doc.save("Recovered.docx");
    }
}
```

**Por que isso importa:** Ao chamar `setRecoveryMode`, você informa ao Aspose.Words quão agressivamente ele deve tentar salvar o arquivo. Sem essa chamada, a biblioteca usa *STRICT* por padrão, o que abortaria ao primeiro sinal de problema—anulando o objetivo de um fluxo de *recover broken word document*.

---

## Etapa 3: Verificar o Carregamento – Realmente **recover broken word document**?

Depois do carregamento, você pode inspecionar o objeto `Document`:

```java
// Check if any sections were dropped
int sections = doc.getSections().getCount();
System.out.println("Sections recovered: " + sections);
```

Se o console mostrar um número razoável de seções, você realizou com sucesso o *load document with recovery*. Na prática, perceberá que a maior parte do texto, tabelas e imagens sobrevive, enquanto os trechos corrompidos simplesmente desaparecem.

---

## Etapa 4: Tratar Graficamente os **recover word document errors** Restantes

Mesmo com o modo *RELAXED*, alguns casos extremos ainda podem gerar avisos. Envolva o carregamento em um try‑catch para manter seu aplicativo ativo:

```java
try {
    Document doc = new Document("Corrupted.docx", loadOptions);
    // Continue processing...
} catch (Exception ex) {
    System.err.println("Recovery failed: " + ex.getMessage());
    // Optionally fallback to a backup copy or notify the user.
}
```

**Quando isso pode acontecer?** Se o arquivo estiver tão danificado que até um analisador relaxado não consiga identificar uma estrutura de documento válida, o Aspose.Words ainda lançará uma exceção. Nesses raros momentos, pode ser necessário solicitar ao usuário que forneça uma cópia diferente.

---

## Etapa 5: Salvar o Arquivo Recuperado (Opcional)

A maioria dos desenvolvedores deseja uma versão limpa para entregar a sistemas downstream. A chamada `save` abaixo grava um novo `.docx` que não contém mais os fragmentos corrompidos.

```java
doc.save("Recovered.docx");
System.out.println("Recovered file saved as Recovered.docx");
```

Agora você tem um **recover broken word document** que pode ser aberto no Microsoft Word, Google Docs ou qualquer outro visualizador—sem diálogos de erro.

---

## Visão Geral Visual (Imagem)

![Diagrama mostrando o fluxo de set recovery mode – do arquivo corrompido ao documento recuperado](https://example.com/images/recovery-flow.png "diagrama do fluxo de set recovery mode")

*O texto alternativo contém explicitamente a palavra‑chave principal, ajudando tanto os mecanismos de busca quanto os leitores de tela.*

---

## Perguntas Frequentes & Casos de Borda

| Pergunta | Resposta |
|----------|----------|
| *E se eu precisar manter as partes corrompidas para análise forense?* | Use `LoadOptions.setRecoverMode(LoadOptions.RecoveryMode.STRICT)` e capture a exceção. A mensagem da exceção contém detalhes sobre as partes problemáticas. |
| *Posso alternar entre RELAXED e STRICT em tempo de execução?* | Absolutamente—basta criar uma nova instância de `LoadOptions` com o modo desejado antes de cada carregamento. |
| *Isso funciona com arquivos .doc mais antigos?* | Sim. O mesmo `LoadOptions` se aplica tanto a formatos `.doc` quanto `.docx`. |
| *Existe algum impacto de desempenho?* | Mínimo. O overhead extra de análise é insignificante comparado ao custo de um carregamento completo do documento. |

---

## Exemplo Completo (Pronto para Copiar‑Colar)

```java
import com.aspose.words.*;

public class RecoverWordDocument {
    public static void main(String[] args) {
        try {
            // Step 1 – configure recovery mode
            LoadOptions loadOptions = new LoadOptions();
            loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RELAXED); // set recovery mode

            // Step 2 – load the corrupted file
            Document doc = new Document("Corrupted.docx", loadOptions);

            // Step 3 – optional verification
            System.out.println("Loaded! Pages: " + doc.getPageCount());

            // Step 4 – save a clean copy
            doc.save("Recovered.docx");
            System.out.println("Saved recovered document as Recovered.docx");
        } catch (Exception e) {
            System.err.println("Failed to recover document: " + e.getMessage());
        }
    }
}
```

Execute o programa, aponte‑o para o seu arquivo quebrado e observe a saída. Se tudo correr bem, você verá a contagem de páginas impressa e um novo `Recovered.docx` aparecer ao lado da sua fonte.

---

## Conclusão

Cobrimos tudo o que você precisa para **set recovery mode** no Aspose.Words, desde a escolha do enum `RecoveryMode` correto até o tratamento dos poucos *recover word document errors* que ainda podem surgir. Seguindo os passos acima, você pode carregar documentos com recuperação de forma confiável, manter as partes boas de um arquivo corrompido e gerar uma versão limpa pronta para qualquer processamento downstream.

Pronto para o próximo desafio? Experimente combinar **set recovery mode** com as APIs de **document cleaning** do Aspose.Words—removendo parágrafos ocultos, corrigindo hyperlinks quebrados ou até convertendo o arquivo recuperado para PDF em um único passo. As possibilidades são infinitas, e agora você tem uma base sólida para enfrentar arquivos Word corrompidos de frente.

Feliz codificação, e que seus documentos permaneçam saudáveis!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}