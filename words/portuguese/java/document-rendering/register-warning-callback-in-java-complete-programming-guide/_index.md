---
category: general
date: 2026-05-23
description: Registre o callback de aviso em Java para detectar fontes ausentes e
  lidar com substituições de fontes. Aprenda passo a passo com um exemplo completo.
draft: false
keywords:
- register warning callback
- detect missing fonts
- Java font handling
- Aspose.Words warning callback
- font substitution detection
language: pt
og_description: Registre o callback de aviso em Java para detectar fontes ausentes.
  Este tutorial mostra uma solução completa com código, explicações e boas práticas.
og_title: Registrar Callback de Aviso no Java – Guia Completo
schemas:
- author: Aspose
  dateModified: '2026-05-23'
  description: Register warning callback in Java to detect missing fonts and handle
    font substitutions. Learn step‑by‑step with a full example.
  headline: Register Warning Callback in Java – Complete Programming Guide
  type: TechArticle
tags:
- Java
- Aspose.Words
- FontSettings
- DocumentProcessing
title: Registrar Callback de Aviso em Java – Guia Completo de Programação
url: /pt/java/document-rendering/register-warning-callback-in-java-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Registrar Callback de Aviso em Java – Guia de Programação Completo

Já precisou **registrar callback de aviso** em Java, mas não tinha certeza de como capturar problemas de fontes ausentes? Você não está sozinho. Quando documentos dependem de tipografias personalizadas, substituições silenciosas de fontes podem arruinar o layout, e a única maneira confiável de detectá‑las é ouvindo os avisos. Neste guia, percorreremos uma solução prática que não só **registra um callback de aviso**, mas também **detecta fontes ausentes** antes que elas quebrem silenciosamente sua saída.

Veja, o Aspose.Words for Java oferece uma API limpa para gerenciamento de fontes, mas muitos desenvolvedores pulam a etapa de callback de aviso e acabam com PDFs que não se parecem em nada com o arquivo Word original. Ao final deste tutorial, você terá um trecho pronto‑para‑executar, entenderá por que cada linha importa e saberá como estender a abordagem para cenários mais complexos.

## O que você aprenderá

* Como criar `LoadOptions` e habilitar o tratamento de fontes personalizadas.  
* Como **registrar callback de aviso** para capturar eventos `FONT_SUBSTITUTION`.  
* Como **detectar fontes ausentes** e registrar informações úteis para depuração.  
* Um exemplo Java completo e executável que você pode colar em sua IDE hoje.

Nenhuma biblioteca externa além do Aspose.Words é necessária, e o código funciona com Java 8+ e Aspose.Words 23.9 (ou posterior). Se você já tem um projeto que carrega arquivos `.docx`, só precisará adicionar algumas linhas — sem necessidade de refatoração massiva.

## Pré‑requisitos

* Java Development Kit (JDK) 8 ou mais recente.  
* Aspose.Words for Java (baixe no site oficial ou adicione a dependência Maven).  
* Acesso ao diretório que contém o documento Word que você deseja carregar.  
* Familiaridade básica com lambdas Java ou classes anônimas (usaremos uma classe anônima para clareza).

Se algum desses itens lhe for desconhecido, não entre em pânico — cada passo é explicado em inglês simples, e os comentários do código preenchem as lacunas.

---

## Etapa 1: Criar Load Options e Habilitar o Tratamento de Fonte Personalizada

Antes de podermos ouvir avisos relacionados a fontes, precisamos de uma instância `LoadOptions` que indique ao Aspose.Words para usar nosso próprio `FontSettings`. Pense em `LoadOptions` como a “bolsa de configurações” que você entrega ao carregador de documentos.

```java
// Step 1: Create load options and enable custom font handling
LoadOptions loadOptions = new LoadOptions();               // Holds loading configuration
loadOptions.setFontSettings(new FontSettings());           // Attach a fresh FontSettings object
```

**Por que isso importa:**  
`FontSettings` é a porta de entrada para tudo que a biblioteca faz com fontes — caminhos de pesquisa, regras de substituição e, crucialmente, callbacks de aviso. Ao criar um objeto `FontSettings` dedicado, você obtém controle total sobre como fontes ausentes são tratadas, em vez de depender dos padrões da biblioteca.

> **Dica profissional:** Se sua aplicação já fornece um `FontSettings` compartilhado (por exemplo, para conversão PDF), reutilize‑o aqui para manter a resolução de fontes consistente em todo o pipeline.

## Etapa 2: Registrar um Callback de Aviso para Detectar Fontes Ausentes

Agora vem o núcleo do tutorial: nós **registramos o callback de aviso** no `FontSettings` que acabamos de criar. O callback recebe um objeto `WarningInfo` para cada aviso emitido durante o carregamento do documento.

```java
// Step 2: Register a warning callback to be notified of font substitutions
loadOptions.getFontSettings().setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Filter only font substitution warnings
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            // This is where we **detect missing fonts**
            System.out.println("Substituted: " + info.getDescription());
        }
    }
});
```

**Explicação da lógica:**

* `setWarningCallback` anexa nosso ouvinte personalizado.  
* Dentro de `warning(WarningInfo info)`, verificamos `info.getWarningType()`.  
* Quando o tipo é igual a `WarningType.FONT_SUBSTITUTION`, a biblioteca está informando que não pôde encontrar a fonte original e precisou substituir por outra.  
* `info.getDescription()` contém uma mensagem legível, como *“Font 'MyCustomFont' not found, substituted with 'Arial'.”*  

Ao imprimir essa descrição, nós **detectamos fontes ausentes** instantaneamente durante a fase de carregamento, permitindo que você registre, alerte ou até interrompa a operação se a substituição for inaceitável.

> **Por que não simplesmente capturar uma exceção?**  
> Fontes ausentes raramente lançam exceções; elas emitem avisos. Sem um callback, esses avisos desaparecem no vazio, e você nunca saberá que a fidelidade visual do documento foi comprometida.

### Opcional: Usando uma Lambda (Java 8+)

Se você prefere uma sintaxe mais concisa, o mesmo callback pode ser expresso com uma lambda:

```java
loadOptions.getFontSettings().setWarningCallback(info -> {
    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
        System.out.println("Substituted: " + info.getDescription());
    }
});
```

Ambas as abordagens alcançam o mesmo objetivo — escolha o estilo que combina com sua base de código.

---

## Etapa 3: Carregar o Documento com as Opções Configuradas

Com o callback configurado, o passo final é carregar o documento. O construtor `Document` aceita o caminho e o `LoadOptions` que preparamos.

```java
// Step 3: Load the document using the configured options
Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**O que acontece nos bastidores?**  
Durante esta chamada, o Aspose.Words analisa o arquivo `.docx`, resolve cada fonte referenciada e dispara nosso callback de aviso para qualquer tipografia ausente. Se tudo estiver presente, você não verá saída no console; caso contrário, receberá linhas como:

```
Substituted: Font 'OpenSans-Regular' not found, substituted with 'Times New Roman'.
Substituted: Font 'CustomIconFont' not found, substituted with 'Arial'.
```

Essa saída é a evidência concreta de que **registramos o callback de aviso** com sucesso e estamos **detectando fontes ausentes**.

---

## Exemplo Completo Funcional

Abaixo está o programa Java completo e autocontido que você pode copiar‑colar em um arquivo `Main.java` e executar. Certifique‑se de que o JAR do Aspose.Words está no seu classpath.

```java
import com.aspose.words.*;

public class Main {
    public static void main(String[] args) {
        try {
            // 1️⃣ Create LoadOptions and enable custom font handling
            LoadOptions loadOptions = new LoadOptions();
            loadOptions.setFontSettings(new FontSettings());

            // 2️⃣ Register warning callback to detect missing fonts
            loadOptions.getFontSettings().setWarningCallback(new IWarningCallback() {
                @Override
                public void warning(WarningInfo info) {
                    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                        System.out.println("Substituted: " + info.getDescription());
                    }
                }
            });

            // 3️⃣ Load the document using the configured options
            Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

            // Optional: Save as PDF to verify visual fidelity
            doc.save("output.pdf");
            System.out.println("Document loaded and saved successfully.");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Saída esperada** (quando fontes estão ausentes):

```
Substituted: Font 'MyCustomFont' not found, substituted with 'Arial'.
Document loaded and saved successfully.
```

Se todas as fontes estiverem disponíveis, você verá apenas a mensagem de sucesso.

---

## Lidando com Casos de Borda e Armadilhas Comuns

| Situação | O que observar | Correção sugerida |
|-----------|-------------------|---------------|
| **Múltiplas fontes ausentes** | O callback pode disparar muitas vezes, poluindo os logs. | Agregue mensagens ou escreva em um arquivo para análise posterior. |
| **Impacto de desempenho** | Log excessivo pode desacelerar carregamentos em lote grandes. | Filtre avisos por severidade ou desative a saída no console em produção. |
| **Diretórios de fontes personalizados** | `FontSettings` usa apenas fontes do sistema por padrão. | Chame `fontSettings.setFontsFolder("path/to/custom/fonts", true);` antes de registrar o callback. |
| **Substituição silenciosa** | Algumas fontes podem ser substituídas sem aviso se forem consideradas semelhantes. | Defina `fontSettings.setSubstitutionSettings(new FontSubstitutionSettings());` e ajuste finamente as regras de substituição. |

---

## Estendendo a Solução

Agora que você sabe como **registrar callback de aviso** e **detectar fontes ausentes**, pode querer:

* **Abortar o carregamento** quando uma fonte crítica estiver ausente (lançar uma exceção dentro do callback).  
* **Coletar nomes de fontes ausentes** em um `Set<String>` para um relatório resumido após o carregamento do documento.  
* **Integrar com um sistema de monitoramento** (por exemplo, enviar alertas para Slack ou Azure Monitor).  

Todas essas extensões se baseiam no mesmo padrão de callback que demonstramos.

---

## Conclusão

Percorremos um exemplo completo e pronto para produção que mostra como **registrar callback de aviso** em Java, permitindo que você **detecte fontes ausentes** no momento em que um documento é carregado. Os principais pontos são:

* Criar um `LoadOptions` com `FontSettings` personalizado.  
* Anexar um `IWarningCallback` que filtra avisos `FONT_SUBstitution`.  
* Carregar o documento usando essas opções e reagir a quaisquer eventos de fonte ausente.

Com esse conhecimento, você pode proteger seus pipelines de processamento de documentos, garantir a fidelidade visual e fornecer diagnósticos claros aos usuários finais.

Pronto para o próximo passo? Tente adicionar uma pasta de fontes, experimente diferentes políticas de substituição ou conecte o callback ao seu framework de logging existente. As possibilidades são tão amplas quanto as bibliotecas de fontes que você gerencia.

Boa codificação, e que seus PDFs sempre renderizem exatamente como pretendido!

## Tutoriais Relacionados

- [Capturar Avisos de Substituição de Fonte em Java com Aspose.Words – Guia Completo](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Callback de Aviso em Documento Word](/words/english/net/programming-with-loadoptions/warning-callback/)
- [Como Carregar DOCX e Detectar Fontes Ausentes – Guia Completo em C#](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}