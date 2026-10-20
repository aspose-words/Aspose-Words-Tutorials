---
category: general
date: 2026-04-01
description: Ative avisos de fontes ao carregar documentos Word com Aspose.Words.
  Aprenda como capturar eventos de substituição de fontes usando LoadOptions e Configurações
  de Fonte em C#.
draft: false
keywords:
- enable font warnings
- font substitution
- Aspose.Words
- LoadOptions
- C# document processing
- font settings
language: pt
og_description: Ative avisos de fontes ao carregar documentos Word com Aspose.Words.
  Este tutorial mostra como capturar eventos de substituição de fontes em C#.
og_title: Ativar avisos de fontes no Aspose.Words – Guia completo de C#
tags:
- Aspose.Words
- C#
- Font Management
title: Ativar Avisos de Fonte no Aspose.Words – Guia Completo de C#
url: /pt/net/working-with-fonts/enable-font-warnings-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ativar Avisos de Fonte no Aspose.Words – Guia Completo em C#

Já se perguntou por que um documento Word de repente parece diferente depois de carregá‑lo programaticamente? **Ative os Avisos de Fonte** e você saberá instantaneamente quando o Aspose.Words substituir uma fonte ausente por uma alternativa. Neste tutorial vamos percorrer um exemplo prático que não só captura essas substituições, mas também explica *por que* elas acontecem.

Cobriremos tudo o que você precisa para colocar tudo em funcionamento: o pacote NuGet necessário, a configuração exata de `LoadOptions` e uma saída de console organizada que informa quais fontes foram substituídas. Ao final, você terá um padrão sólido e reutilizável para **processamento de documentos em C#** que funciona com qualquer versão do Aspose.Words.

## O que Você Vai Aprender

- Como criar uma instância de `LoadOptions` que rastreia alterações de fonte.  
- O propósito do evento `SubstitutionWarning` e como conectá‑lo.  
- Um exemplo de código completo e executável que imprime avisos claros no console.  
- Dicas para lidar com casos extremos, como documentos que contêm apenas fontes padrão.  

Não é necessário ter experiência prévia com Aspose.Words — basta familiaridade básica com C# e .NET.

---

![diagrama de ativar avisos de fonte](placeholder-image.png "diagrama de ativar avisos de fonte")

*Texto alternativo: diagrama de ativar avisos de fonte mostrando o fluxo de evento quando uma fonte ausente é substituída.*

## Etapa 1: Configurar LoadOptions e Ativar Avisos de Fonte

A primeira coisa que você precisa é um objeto `LoadOptions`. Esse contêiner informa ao Aspose.Words como tratar o arquivo que você está prestes a carregar. Ao atribuir uma nova instância de `FontSettings` você abre a porta para eventos relacionados a fontes.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Prepare load options and enable font substitution warnings
LoadOptions loadOptions = new LoadOptions
{
    // Attach a new FontSettings object – this is where warnings are emitted.
    FontSettings = new FontSettings()
};
```

**Por que isso importa:**  
Se você pular a atribuição de `FontSettings`, o Aspose.Words ainda substituirá fontes ausentes, mas você não receberá nenhuma notificação. O mecanismo de aviso vive dentro de `FontSettings`, portanto inicializá‑lo é *crucial* para o nosso objetivo.

> **Dica profissional:** Você também pode apontar `FontSettings` para uma pasta de fontes personalizada usando `SetFontsFolder`. Isso reduz o número de avisos que você verá, porque o Aspose.Words pode realmente encontrar as tipografias ausentes.

## Etapa 2: Inscrever‑se no Evento SubstitutionWarning (substituição de fonte)

Agora que o objeto `FontSettings` existe, conectamos ao seu evento `SubstitutionWarning`. Esse evento dispara **toda vez** que o Aspose.Words substitui uma fonte solicitada por outra.

```csharp
// Step 2: Subscribe to the SubstitutionWarning event to be notified when a font is replaced
loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    // e.FontName – the name that the document asked for
    // e.SubstitutedFontName – the font that Aspose.Words actually used
    Console.WriteLine($"[Warning] Font \"{e.FontName}\" was substituted with \"{e.SubstitutedFontName}\".");
};
```

**Por que isso importa:**  
Sem esse listener você não teria visibilidade sobre o processo de substituição. A linha no console fornece um rastro de auditoria rápido, o que é especialmente útil durante builds automatizados ou ao gerar PDFs para indústrias com alta exigência de conformidade.

> **Pergunta comum:** *E se eu quiser suprimir os avisos?*  
> Você pode simplesmente desanexar o manipulador ou definir `FontSettings.SubstitutionWarning += null;`. Contudo, manter os avisos costuma ser a rota mais segura, pois substituições silenciosas podem causar falhas de layout.

## Etapa 3: Carregar Seu Documento com as Opções Configuradas (processamento de documentos C#)

Com o sistema de avisos pronto, carregar o documento torna‑se simples. Passe a instância de `LoadOptions` para o construtor `Document`, e o Aspose.Words cuidará do resto.

```csharp
// Step 3: Load the document using the configured options
string filePath = @"C:\Docs\DocumentWithMissingFont.docx";

Document doc = new Document(filePath, loadOptions);

// Optional: Save to PDF to see the visual impact of the substitution
doc.Save(@"C:\Docs\Output.pdf");
```

**Por que isso importa:**  
O objeto `LoadOptions` é a ponte entre o arquivo bruto e a infraestrutura de avisos. Se você omiti‑lo, o documento será carregado silenciosamente e quaisquer fontes ausentes serão trocadas sem deixar rastro.

> **Caso extremo:** Alguns documentos incorporam os arquivos de fonte exatos de que precisam. Nesse cenário nenhum aviso aparecerá porque o Aspose.Words encontra a fonte incorporada. O código acima ainda funciona; você verá apenas uma saída vazia no console.

## Etapa 4: Verificar a Saída e Armadilhas Comuns

Execute o programa a partir de um prompt de comando ou do depurador da sua IDE. Se o documento fonte contiver uma fonte que não está instalada na máquina (ou não está disponível na pasta de fontes personalizada), você verá linhas como:

```
[Warning] Font "Comic Sans MS" was substituted with "Arial".
[Warning] Font "MyCustomFont" was substituted with "Times New Roman".
```

Se nada for impresso, pode ser que:

1. Todas as fontes foram encontradas, **ou**  
2. O manipulador `SubstitutionWarning` não foi anexado corretamente (verifique novamente a Etapa 2).

### Por que as Substituições de Fonte Ocorrem?

- **Fonte do sistema ausente:** O SO não possui a tipografia solicitada.  
- **Formato de fonte não suportado:** O Aspose.Words pode ler TrueType e OpenType, mas não todos os formatos proprietários.  
- **Restrições de licença:** Algumas fontes comerciais bloqueiam a incorporação, forçando um fallback.

Entender o *porquê* ajuda a decidir se você deve distribuir as fontes ausentes com seu aplicativo ou ajustar o estilo do documento.

## Bônus: Controlar a Fonte de Fallback

Se você quiser que toda fonte ausente recorra a uma família específica (por exemplo, “Calibri”), pode definir uma regra de substituição global:

```csharp
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes(
    "AnyMissingFont", // wildcard – applies to any font not found
    new[] { "Calibri" } // the preferred substitute
);
```

Agora o console ainda avisará, mas o resultado visual será consistente para todas as fontes ausentes.

---

## Recapitulação

- **Ative Avisos de Fonte** criando um `LoadOptions` com um novo `FontSettings`.  
- Conecte o evento `SubstitutionWarning` para receber alertas em tempo real sempre que uma fonte for trocada.  
- Carregue seu documento usando as opções configuradas e, opcionalmente, salve como PDF para ver o efeito visual.  
- Diagnostique por que uma substituição ocorreu e, se necessário, force uma fonte de fallback específica.

Você acabou de adicionar uma rede de segurança ao seu fluxo de trabalho **Aspose.Words** que impede alterações silenciosas de layout. Em seguida, você pode explorar **configurações de fonte** como `DefaultFontName` ou mergulhar nas opções de **renderização de documentos** para ajustar a saída em PDF.

---

### O Que Tentar a Seguir?

- **Explore outros recursos de FontSettings**: `SetFontsFolder`, `LoadFontSources` e `DefaultFontName`.  
- **Combine avisos com frameworks de logging** (Serilog, NLog) para diagnósticos de nível produção.  
- **Experimente diferentes formatos de documento** (`.doc`, `.rtf`, `.html`) para ver como cada um lida com fontes ausentes.  

Tem perguntas ou um cenário curioso? Deixe um comentário abaixo e feliz codificação!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}