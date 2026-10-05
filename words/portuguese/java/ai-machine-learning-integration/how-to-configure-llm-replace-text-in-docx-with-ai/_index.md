---
category: general
date: 2026-03-04
description: How to configure LLM for Document AI and replace text in DOCX using AI
  – step‑by‑step guide with full Java code.
draft: false
keywords:
- how to configure llm
- replace text in docx
- how to replace text
- how to use document ai
- replace phrase with ai
language: pt
og_description: Como configurar LLM para Document AI e substituir texto em DOCX usando
  IA – guia completo com código Java executável.
og_title: Como Configurar LLM – Substituir Texto em DOCX com IA
tags:
- LLM
- Document AI
- Java
- DOCX
title: Como Configurar LLM – Substituir Texto em DOCX com IA
url: /pt/java/ai-machine-learning-integration/how-to-configure-llm-replace-text-in-docx-with-ai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como Configurar LLM – Substituir Texto em DOCX com IA

Já se perguntou **como configurar LLM** para que ele possa editar um arquivo Word para você? Você não está sozinho. Muitos desenvolvedores encontram um obstáculo quando precisam substituir programaticamente uma frase dentro de um `.docx` sem abrir o Microsoft Word. A boa notícia? Com um LLM local e um pequeno wrapper Document AI, você pode trocar texto em um arquivo DOCX em apenas algumas linhas de Java.

Neste tutorial vamos percorrer todo o processo: desde conectar o LLM, carregar um DOCX, até usar **Document AI** para substituir uma frase alvo. Ao final, você terá um exemplo autônomo e executável que pode ser inserido em qualquer projeto Maven ou Gradle. Sem chaves de API externas, sem custos de nuvem — apenas seu próprio modelo escutando em `http://localhost:8080/v1`.

> **Quick win:** Se você já tem um LLM local (como Llama 3 ou Mistral) expondo um endpoint compatível com OpenAI, o código abaixo funciona imediatamente.

---

![Diagram of how to configure LLM for Document AI](/images/configure-llm-diagram.png){: .center-image alt="how to configure llm diagram"}

## O que Você Precisa

- **Java 17** (ou qualquer JDK recente)  
- Um **local LLM** expondo um endpoint estilo OpenAI `/v1` (ex.: Ollama, LMStudio)  
- A **biblioteca Document AI Java** (suponha `com.example:document-ai:1.2.0` no Maven Central)  
- Um arquivo DOCX de exemplo (`input.docx`) colocado em uma pasta conhecida  

Se estiver faltando algum desses, inicie o Ollama rapidamente:

```bash
ollama serve &
ollama run llama3
```

Isso iniciará um servidor em `http://localhost:8080/v1` pronto para aceitar requisições.

---

## Como Configurar LLM para Document AI

A primeira coisa que fazemos é informar ao cliente `DocumentAi` onde encontrar o modelo e qual modelo usar. Este é o passo **como configurar LLM** que muitos tutoriais deixam de lado.

```java
// Step 1: Set up the LLM connection details
AiModelConfig modelConfig = new AiModelConfig();
modelConfig.setBaseUrl("http://localhost:8080/v1");   // Local server address
modelConfig.setApiKey("dummy");                       // Not needed for local models, but the client expects a value
modelConfig.setModelName("local-llm");                // Replace with your model's identifier
```

*Por que isso importa:*  
O objeto `AiModelConfig` abstrai os detalhes HTTP, permitindo que `DocumentAi` se concentre no conteúdo. Se você mudar para um provedor hospedado, basta alterar `baseUrl` e `apiKey` — o resto do seu código permanece intacto.

---

## Carregar e Preparar o Documento DOCX

Em seguida, trazemos o arquivo Word para a memória. A classe `Document` lida tanto com `.docx` quanto com `.pdf` internamente, mas aqui nos importamos apenas com DOCX.

```java
// Step 2: Load the DOCX you want to edit
Path docPath = Paths.get("YOUR_DIRECTORY/input.docx");
Document inputDocument = new Document(docPath.toFile());
```

*Dica de especialista:* Use um caminho absoluto durante a depuração para evitar a surpresa “arquivo não encontrado”. Quando estiver confiante, volte a usar um caminho relativo para portabilidade.

---

## Substituir Texto em DOCX Usando IA

Agora vem o coração do tutorial — **como substituir texto** em um arquivo DOCX com assistência de IA. O método `replaceText` envia o conteúdo do documento ao LLM, pede que ele faça a substituição e devolve o texto revisado.

```java
// Step 3: Initialise the Document AI client
DocumentAi documentAi = new DocumentAi(modelConfig);

// Step 4: Ask the LLM to replace the target phrase
String oldPhrase = "old phrase";
String newPhrase = "new phrase";

String revisedText = documentAi.replaceText(
        inputDocument,
        oldPhrase,
        newPhrase
);
```

*O que está acontecendo nos bastidores?*  
`DocumentAi` serializa o DOCX em texto puro, cria um prompt como:

> “No documento a seguir, substitua todas as ocorrências de ‘old phrase’ por ‘new phrase’ e retorne apenas o texto atualizado.”

O LLM processa a solicitação e devolve o conteúdo modificado. Essa abordagem funciona mesmo quando a frase abrange múltiplas execuções ou parágrafos — algo que a simples substituição de strings costuma perder.

---

## Verificar e Exibir o Texto Revisado

Por fim, imprimimos o texto revisado pela IA no console. Em um aplicativo real você provavelmente gravaria o resultado em um novo DOCX, mas imprimir permite verificar rapidamente.

```java
// Step 5: Show the AI‑revised output
System.out.println("AI‑revised text:");
System.out.println("-----------------------------------");
System.out.println(revisedText);
```

**Saída esperada** (supondo que o DOCX original continha “This is the old phrase we want to change.”):

```
AI‑revised text:
-----------------------------------
This is the new phrase we want to change.
```

Se você vir a nova frase aparecer, parabéns — **você acabou de aprender a usar Document AI para substituir uma frase com IA**.

---

## Exemplo Completo Funcionando

Juntando tudo, aqui está uma classe Java completa, pronta‑para‑executar. Sinta‑se à vontade para copiar‑colar em `src/main/java/com/example/ReplaceInDocx.java`.

```java
package com.example;

import com.example.documentai.AiModelConfig;
import com.example.documentai.DocumentAi;
import com.example.documentai.Document;

import java.nio.file.Path;
import java.nio.file.Paths;

/**
 * Demonstrates how to configure LLM, load a DOCX, and replace a phrase using Document AI.
 */
public class ReplaceInDocx {

    public static void main(String[] args) {
        // 1️⃣ Configure the local LLM connection
        AiModelConfig modelConfig = new AiModelConfig();
        modelConfig.setBaseUrl("http://localhost:8080/v1");
        modelConfig.setApiKey("dummy");               // Not required for local models
        modelConfig.setModelName("local-llm");        // Change if needed

        // 2️⃣ Load the DOCX you want to modify
        Path docPath = Paths.get("YOUR_DIRECTORY/input.docx");
        Document inputDocument = new Document(docPath.toFile());

        // 3️⃣ Create the Document AI client using the configuration
        DocumentAi documentAi = new DocumentAi(modelConfig);

        // 4️⃣ Replace the target phrase with the new phrase using the AI model
        String oldPhrase = "old phrase";
        String newPhrase = "new phrase";

        String revisedText = documentAi.replaceText(
                inputDocument,
                oldPhrase,
                newPhrase
        );

        // 5️⃣ Output the AI‑revised text
        System.out.println("AI‑revised text:");
        System.out.println("-----------------------------------");
        System.out.println(revisedText);
    }
}
```

### Como Executar

```bash
# Compile
mvn clean compile

# Execute
mvn exec:java -Dexec.mainClass="com.example.ReplaceInDocx"
```

Certifique‑se de que o servidor LLM esteja ativo antes de executar o programa; caso contrário, você receberá um timeout de conexão.

---

## Casos Limite & Armadilhas Comuns

| Situação | O que observar | Correção sugerida |
|-----------|-------------------|---------------|
| **Frase não encontrada** | O LLM devolve o texto original sem alterações. | Verifique a ortografia e sensibilidade a maiúsculas/minúsculas; você pode adicionar `ignoreCase:true` ao prompt se seu wrapper suportar. |
| **Documentos grandes (>5 MB)** | O tamanho do prompt pode exceder o limite de tokens do modelo. | Divida o DOCX em seções, processe cada uma separadamente e depois concatene os resultados. |
| **LLM local retorna erros** | Frequentemente causado por nome de modelo incompatível. | Verifique se o nome do modelo na UI do LLM (`ollama list`) corresponde ao configurado em `modelConfig.setModelName`. |
| **Caracteres Unicode ficam corrompidos** | Problemas de codificação ao ler o DOCX. | Garanta que sua runtime Java use UTF‑8 (adicione `-Dfile.encoding=UTF-8` aos argumentos da JVM). |

---

## Próximos Passos

Agora que você sabe **como substituir texto em DOCX** com IA, pode explorar:

- **Como usar Document AI** para tarefas mais complexas como extração de tabelas ou preservação de estilos.  
- **Substituir frase com IA** em PDFs trocando o argumento do construtor `Document`.  
- **Processamento em lote**: percorrer um diretório de arquivos DOCX e aplicar a mesma substituição.  

Cada um desses itens se baseia na mesma fundação `AiModelConfig` e `DocumentAi`, então você não precisará começar do zero

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}