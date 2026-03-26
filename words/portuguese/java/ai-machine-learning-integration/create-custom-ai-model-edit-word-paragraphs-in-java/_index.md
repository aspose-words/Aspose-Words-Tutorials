---
category: general
date: 2026-03-25
description: Crie um modelo de IA personalizado para editar documentos Word – aprenda
  a tornar o texto mais formal, substituir o texto de parágrafos e reescrever um parágrafo
  do Word usando o Aspose.Words AI.
draft: false
keywords:
- create custom ai model
- make text more formal
- replace paragraph text
- edit paragraph with ai
- rewrite word paragraph
language: pt
og_description: Crie um modelo de IA personalizado para editar documentos Word. Aprenda
  como tornar o texto mais formal, substituir o texto de parágrafos e reescrever um
  parágrafo do Word usando a IA do Aspose.Words.
og_title: Criar Modelo de IA Personalizado – Editar Parágrafos do Word em Java
tags:
- Aspose.Words
- Java
- AI integration
title: Criar Modelo de IA Personalizado – Editar Parágrafos do Word em Java
url: /pt/java/ai-machine-learning-integration/create-custom-ai-model-edit-word-paragraphs-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar Modelo de IA Personalizado – Editar Parágrafos do Word em Java

Já precisou **criar um modelo de IA personalizado** que possa aprimorar um parágrafo dentro de um arquivo Word? Talvez você tenha um lote de contratos que soam um pouco informais demais, e gostaria de tornar o texto mais formal com uma única linha de código. A boa notícia é que você pode fazer exatamente isso — sem serviços externos, sem SDKs pesados, apenas Aspose.Words para Java e um endpoint compatível com OpenAI.

Neste tutorial vamos percorrer cada passo necessário para **criar um modelo de IA personalizado**, conectá‑lo a um servidor LLM local e, em seguida, usá‑lo para *substituir o texto do parágrafo* por uma versão mais formal. Ao final, você terá um programa Java executável que **edita parágrafos com IA**, reescreve um parágrafo do Word e salva o resultado de volta no disco. Sem enrolação, apenas uma solução prática que você pode copiar‑colar para o seu próprio projeto.

> **O que você precisará**  
> • Java 17 ou superior (o código compila em versões anteriores, mas 17 é o ponto ideal)  
> • Aspose.Words para Java 23.9 (ou a versão mais recente)  
> • Um servidor LLM compatível com OpenAI em execução (por exemplo, Ollama, LocalAI) escutando em `http://localhost:8000/v1`  
> • Um documento Word de entrada (`input.docx`) colocado em uma pasta que você controla  

Se você está se perguntando *por que construir um modelo personalizado* em vez de chamar diretamente a OpenAI, a resposta é flexibilidade: você controla o endpoint, pode trocar de modelo sem mudar o código e mantém quaisquer chaves de API fora do seu repositório de código. Vamos mergulhar.

---

## Criar Modelo de IA Personalizado – Configuração

Primeiro precisamos informar ao Aspose.Words onde nosso LLM está. A classe `AiModelEndpoint` contém a URL e a chave de API opcional. Como estamos usando um servidor local, a chave pode ser uma string vazia, mas o parâmetro é obrigatório.

```java
import com.aspose.words.ai.*;

public class LlmDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Define the LLM endpoint (OpenAI‑compatible)
        AiModelEndpoint llmEndpoint = new AiModelEndpoint(
                "http://localhost:8000/v1",   // URL of your LLM server
                "my-api-key");                // API key if required
```

> **Dica profissional:** Se você mudar para um modelo hospedado (por exemplo, Azure OpenAI), basta alterar a URL e a chave — nenhum outro ajuste de código será necessário.

---

## Carregar o Documento Word

Agora trazemos o arquivo fonte para a memória. `Document` pode ler `.docx`, `.doc`, `.rtf` e muitos outros formatos, mas para este exemplo usamos `.docx`.

```java
        // Step 2: Load the source Word document
        Document document = new Document("YOUR_DIRECTORY/input.docx");
```

Certifique‑se de que `YOUR_DIRECTORY` aponta para uma pasta real; caso contrário, você receberá um `FileNotFoundException`. Em um aplicativo real você pode passar o caminho como argumento de linha de comando ou lê‑lo de um arquivo de configuração.

---

## Inicializar o Modelo de IA Personalizado

Criamos um `AiModel` do tipo `CUSTOM` e fornecemos o endpoint que definimos anteriormente. Isso indica ao Aspose.Words que todas as chamadas de IA devem ser roteadas através do nosso próprio servidor.

```java
        // Step 3: Create a custom AI model that uses the endpoint
        AiModel llmModel = new AiModel(AiModelType.CUSTOM, llmEndpoint);
```

Nos bastidores, o Aspose.Words cria um pequeno cliente HTTP que conversa com o LLM usando o esquema padrão de chat/completion da OpenAI. Por isso o endpoint precisa ser *compatível com OpenAI*.

---

## Recuperar e Reescrever o Primeiro Parágrafo

É aqui que realmente **tornamos o texto mais formal**. Pegamos o primeiro parágrafo, enviamos seu texto bruto ao modelo com um prompt e recebemos a versão editada.

```java
        // Step 4: Retrieve the first paragraph and ask the model to rewrite it
        Paragraph firstParagraph = document.getFirstSection()
                                            .getBody()
                                            .getParagraphs()
                                            .get(0);
        String rewrittenText = llmModel.editText(
                firstParagraph.getText(),
                "Make it more formal");
```

O segundo argumento (`"Make it more formal"`) é a instrução que damos ao modelo. Você pode substituí‑lo por qualquer diretriz — **replace paragraph text**, **summarize**, **translate**, etc. O método devolve uma string simples, que inseriremos de volta no documento mais adiante.

> **Por que isso funciona:** `editText` envia um payload JSON como `{ "model": "...", "messages": [{ "role":"user", "content":"<text>\nMake it more formal"}] }`. O LLM vê o parágrafo original e a instrução, então responde com o texto revisado.

---

## Substituir o Conteúdo Original do Parágrafo

Agora **substituímos o texto do parágrafo** dentro do modelo de objeto Word. Limpamos quaisquer `Run` existentes (as peças de texto de baixo nível) e inserimos um novo `Run` contendo a string gerada pela IA.

```java
        // Step 5: Replace the original paragraph content with the rewritten text
        firstParagraph.removeAllChildren();
        firstParagraph.appendChild(new Run(document, rewrittenText));
```

Tenha cuidado para não chamar `firstParagraph.setText()` — esse método removeria toda a formatação. Usar `Run` preserva o estilo do parágrafo (título, marcador, etc.) enquanto troca os caracteres reais.

---

## Salvar o Documento Editado

Por fim, gravamos o documento modificado de volta no disco. Você pode sobrescrever o arquivo original ou, como fazemos aqui, criar uma cópia nova.

```java
        // Step 6: Save the edited document
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

Ao abrir `output.docx` você deverá ver o primeiro parágrafo agora soando consideravelmente mais formal. Se o LLM não seguiu a instrução perfeitamente, ajuste o prompt ou experimente outra versão do modelo.

---

## Exemplo Completo Funcional

Abaixo está o programa completo — copie‑o para `LlmDemo.java`, ajuste os caminhos e execute com `javac` + `java`.

```java
import com.aspose.words.*;
import com.aspose.words.ai.*;

public class LlmDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Define the LLM endpoint (OpenAI‑compatible)
        AiModelEndpoint llmEndpoint = new AiModelEndpoint(
                "http://localhost:8000/v1",   // URL of your LLM server
                "my-api-key");                // API key if required

        // Step 2: Load the source Word document
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // Step 3: Create a custom AI model that uses the endpoint
        AiModel llmModel = new AiModel(AiModelType.CUSTOM, llmEndpoint);

        // Step 4: Retrieve the first paragraph and ask the model to rewrite it
        Paragraph firstParagraph = document.getFirstSection()
                                            .getBody()
                                            .getParagraphs()
                                            .get(0);
        String rewrittenText = llmModel.editText(
                firstParagraph.getText(),
                "Make it more formal");

        // Step 5: Replace the original paragraph content with the rewritten text
        firstParagraph.removeAllChildren();
        firstParagraph.appendChild(new Run(document, rewrittenText));

        // Step 6: Save the edited document
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

**Saída esperada:** Abra `output.docx` e você verá o parágrafo original transformado. Por exemplo, uma frase casual como “We’ll get the thing done soon.” pode virar “We shall complete the task promptly.” A redação exata depende do modelo que você está usando.

---

## Perguntas Frequentes & Casos de Borda

### E se o documento tiver várias seções?

O código acima toca apenas o *primeiro* parágrafo da *primeira* seção. Para **edit paragraph with AI** em todo o arquivo, itere sobre `document.getSections()` e depois sobre cada `section.getBody().getParagraphs()`. Lembre‑se de pular parágrafos vazios, caso contrário o LLM receberá uma string vazia e não retornará nada.

### Como lidar com parágrafos grandes que excedem o limite de tokens?

A maioria dos LLMs limita a entrada a cerca de 4 000 tokens. Se um parágrafo for excepcionalmente longo, divida‑o em blocos menores antes de chamar `editText`. Você pode reutilizar a mesma instância de `AiModel`; apenas fique atento aos limites de taxa do seu servidor local.

### Posso usar outra instrução, como “summarize” ou “translate to French”?

Com certeza. O segundo argumento de `editText` é livre. Para um resumo, você poderia passar `"Summarize in one sentence"`. Para tradução, `"Translate to French, keep the tone formal"` funciona igualmente bem. Essa flexibilidade permite **replace paragraph text** em diversos cenários sem mudar código.

### O modelo preserva a formatação do parágrafo (fontes, cores)?

Como substituímos apenas o `Run` dentro do mesmo objeto `Paragraph`, os estilos existentes (nível de título, lista com marcadores, recuo) permanecem intactos. Se precisar mudar o estilo em si, manipule `Paragraph.getParagraphFormat()` após a substituição.

### E se o meu servidor LLM exigir HTTPS com certificado auto‑assinado?

`AiModelEndpoint` aceita URLs com `https://`. Se o certificado não for confiável, será necessário configurar o contexto SSL do Java para aceitá‑lo, ou executar o servidor com um certificado válido. Essa configuração está fora do escopo deste tutorial, mas bem documentada nos guias de SSL para Java.

---

## Dicas para Integração Pronta para Produção

| Dica | Por que é importante |
|------|----------------------|
| **Cachear o endpoint** | Recriar `AiModelEndpoint` a cada requisição adiciona overhead. |
| **Edições em lote** | Se houver muitos parágrafos, envie‑os em uma única requisição (ex.: array JSON) para reduzir latência. |
| **Validar a saída do LLM** | Sempre verifique se a string retornada não é nula ou vazia antes de inseri‑la. |
| **Logar prompts e respostas** | Útil para depuração e para conformidade ao reescrever textos legais. |
| **Fallback elegante** | Se o LLM estiver indisponível, volte ao parágrafo original ou use uma heurística simples de reescrita. |

---

## Conclusão

Mostramos como **criar um modelo de IA personalizado** com Aspose.Words, conectá‑lo a um endpoint compatível com OpenAI e então **editar parágrafos com IA** para **tornar o texto mais formal**. Seguindo os seis passos — definir o endpoint, carregar o documento, inicializar o modelo,

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}