---
category: general
date: 2026-02-18
description: Crie opções de carregamento em Java para detectar fontes ausentes e aprenda
  como carregar arquivos DOCX com um callback de aviso.
draft: false
keywords:
- create load options
- detect missing fonts
- how to load docx
- Aspose.Words warning callback
- Java document processing
language: pt
og_description: Crie opções de carregamento em Java para detectar fontes ausentes
  e aprenda como carregar arquivos DOCX com um callback de aviso.
og_title: Criar Opções de Carregamento em Java – Detectar Fontes Ausentes e Como Carregar
  DOCX
tags:
- java
- aspose-words
- document-processing
title: Criar Opções de Carregamento em Java – Detectar Fontes Ausentes e Como Carregar
  DOCX
url: /pt/java/document-loading-and-saving/create-load-options-in-java-detect-missing-fonts-how-to-load/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar Opções de Carregamento em Java – Detectar Fontes Ausentes e Como Carregar DOCX

Já se perguntou como **criar opções de carregamento** que não apenas leiam um DOCX, mas também avisem quando uma fonte está ausente? Você não está sozinho. Fontes ausentes podem transformar um documento perfeitamente formatado em uma bagunça ilegível, e detectá‑las cedo economiza horas de depuração. Neste tutorial vamos percorrer os passos exatos para **detectar fontes ausentes** enquanto mostramos **como carregar arquivos DOCX** com um callback de aviso personalizado.

## O que você aprenderá

- Como instanciar `LoadOptions` e configurar um manipulador de avisos.  
- Por que o callback de aviso é essencial para capturar problemas de substituição de fontes.  
- O código exato necessário para **carregar um DOCX** com segurança, além de algumas dicas práticas para projetos do mundo real.  
- Tratamento de casos extremos, como lidar com outros tipos de avisos ou carregar PDFs com a mesma abordagem.

Nenhuma documentação externa necessária — tudo que você precisa está aqui.

## Pré‑requisitos

- Java 17 ou superior (a API funciona em versões mais antigas, mas 17 é o ponto ideal).  
- Biblioteca Aspose.Words for Java adicionada ao seu projeto (`aspose-words-x.x.jar`).  
- Um entendimento básico de tratamento de exceções em Java.  

Se você tem isso, vamos mergulhar.

![Diagrama mostrando o fluxo de criação de opções de carregamento, definição de um callback de aviso e carregamento de um arquivo DOCX](/images/create-load-options-diagram.png){: .center-image alt="Diagrama do fluxo de criação de opções de carregamento"}

## Passo 1: Criar Opções de Carregamento (Como Carregar DOCX)

A primeira coisa que você precisa fazer é **criar opções de carregamento**. Esse objeto informa ao Aspose.Words como se comportar ao abrir um arquivo. Pense nele como um conjunto de instruções que você entrega à biblioteca antes que ela veja o DOCX.

```java
// Step 1: Instantiate LoadOptions
LoadOptions loadOptions = new LoadOptions();
```

Por que não simplesmente chamar `new Document("file.docx")`? Porque sem `LoadOptions` você perde a capacidade de reagir a avisos — como fontes ausentes — até depois que o documento já foi carregado, o que pode ser tarde demais para certos fluxos de trabalho.

## Passo 2: Configurar um Callback de Aviso para Detectar Fontes Ausentes

Agora anexamos um callback que será invocado sempre que o Aspose.Words encontrar uma situação que deseja avisar. No nosso caso, estamos interessados em `WarningType.FONT_SUBSTITUTION`.

```java
// Step 2: Register a warning callback
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // React only to font substitution warnings
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("Missing font detected: " + info.getDescription());
        }
    }
});
```

Alguns pontos a observar:

- **Por que um callback?** Ele é executado *durante* o processo de carregamento, dando a chance de registrar ou até abortar a operação antes que o documento seja totalmente materializado.  
- **Por que verificar `WarningType.FONT_SUBSTITUTION`?** Esse é o valor exato do enum que o Aspose.Words usa para cenários de fontes ausentes. Outros tipos de aviso (por exemplo, `TABLE_STRUCTURE`) podem ser filtrados de forma semelhante, se necessário.  
- **Dica de desempenho:** O callback é leve; evite I/O pesado dentro dele. Se precisar gravar em um arquivo, enfileire as mensagens e descarregue‑as após o carregamento.

## Passo 3: Carregar o Arquivo DOCX com as Opções Configuradas

Com as opções e o callback prontos, você pode finalmente carregar o DOCX. Esta é a parte que responde **como carregar docx** respeitando os avisos que você configurou.

```java
// Step 3: Load the document using the configured LoadOptions
try {
    Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
    System.out.println("Document loaded successfully.");
} catch (Exception e) {
    System.err.println("Failed to load document: " + e.getMessage());
}
```

**O que acontece nos bastidores?** À medida que o arquivo é transmitido, o Aspose.Words verifica cada referência de fonte. Se uma fonte referenciada não estiver instalada, ele dispara o callback de aviso que definimos anteriormente. Você verá uma saída como:

```
Missing font detected: Font 'Calibri' is not installed. Substituted with 'Arial'.
Document loaded successfully.
```

Esse feedback imediato vale ouro quando você está processando lotes de arquivos em um servidor.

## Exemplo Completo Funcional

Juntando tudo, aqui está um programa autocontido que você pode copiar‑colar no seu IDE.

```java
import com.aspose.words.*;

public class DetectMissingFonts {
    public static void main(String[] args) {
        // 1️⃣ Create LoadOptions
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Register warning callback to detect missing fonts
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Missing font: " + info.getDescription());
                }
            }
        });

        // 3️⃣ Load the DOCX using the configured options
        try {
            Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
            System.out.println("DOCX loaded – you can now work with it.");
        } catch (Exception ex) {
            System.err.println("Error loading DOCX: " + ex.getMessage());
        }
    }
}
```

**Saída esperada**

```
Missing font: Font 'Times New Roman' is not installed. Substituted with 'Arial'.
DOCX loaded – you can now work with it.
```

Se o arquivo não contiver fontes ausentes, o callback simplesmente permanece silencioso e a linha “DOCX loaded” aparece.

## Dicas Profissionais & Casos de Borda

| Situação | O que Fazer |
|-----------|------------|
| **Múltiplas fontes ausentes** | O callback dispara para cada uma, então você receberá uma linha por fonte. Agregue‑as em um `List<String>` se precisar de um resumo depois. |
| **Você também quer capturar outros avisos** | Adicione ramificações `else if` para `WarningType.TABLE_STRUCTURE`, `WarningType.UNKNOWN_FILE_FORMAT`, etc. |
| **Carregando arquivos DOCX grandes** | Use `LoadOptions.setLoadFormat(LoadFormat.DOCX)` para indicar o formato e acelerar a detecção. |
| **Executando em um serviço web** | Evite `System.out.println`; em vez disso, injete um logger (`SLF4J`, `Log4j`) dentro do callback. |
| **Fontes são instaladas em tempo de execução** | Após detectar uma fonte ausente, você pode carregá‑la programaticamente via `GraphicsEnvironment.registerFont(...)` e recarregar o documento. |

## Por que esta Abordagem Supera o Método “Apenas Try‑Catch”

Muitos desenvolvedores simplesmente envolvem `new Document(...)` em um bloco try‑catch, esperando que uma exceção informe sobre fontes ausentes. Infelizmente, o Aspose.Words trata a substituição de fontes como um *aviso*, não como erro, portanto nenhuma exceção é lançada. Ao **criar opções de carregamento** e anexar um callback de aviso, você obtém insight determinístico sobre problemas de fontes sem sacrificar desempenho.

## Próximos Passos

- **Detectar fontes ausentes em PDFs** – o mesmo padrão de `LoadOptions` funciona para PDFs, basta mudar o caminho do arquivo e o formato de carregamento.  
- **Automatizar a instalação de fontes** – combine o callback com um script que busque fontes ausentes em um repositório compartilhado.  
- **Explorar outros tipos de aviso** – o Aspose.Words pode alertar sobre tags obsoletas, tabelas complexas e muito mais.  

Sinta‑se à vontade para experimentar: troque o construtor `Document` por um stream (`new Document(InputStream, loadOptions)`) se estiver lidando com dados em memória, ou encadeie múltiplos callbacks usando um padrão composto para pipelines de processamento em larga escala.

---

### TL;DR

Mostramos como **criar opções de carregamento** em Java, configurar um callback que **detecta fontes ausentes** e, finalmente, **carregar um DOCX** com segurança. Com apenas três passos concisos você agora tem um padrão reutilizável que pode ser inserido em qualquer projeto Aspose.Words.

Tem perguntas sobre outros formatos de arquivo ou precisa de ajuda para ajustar o callback ao seu ambiente específico? Deixe um comentário abaixo e feliz codificação!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}