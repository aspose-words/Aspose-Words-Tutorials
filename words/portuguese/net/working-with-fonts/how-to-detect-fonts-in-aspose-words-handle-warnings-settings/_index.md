---
category: general
date: 2026-01-03
description: Como detectar fontes no Aspose.Words e lidar com avisos usando as configurações
  de fonte do Aspose – um guia passo a passo para desenvolvedores.
draft: false
keywords:
- how to detect fonts
- how to handle warnings
- aspose font settings
- how to configure warnings
language: pt
og_description: Como detectar fontes no Aspose.Words e configurar avisos com as configurações
  de fonte do Aspose. Aprenda todo o fluxo de trabalho em minutos.
og_title: Como Detectar Fontes no Aspose.Words – Tratar Avisos
tags:
- Aspose.Words
- C#
- Document Processing
title: Como Detectar Fontes no Aspose.Words – Lidar com Avisos e Configurações
url: /pt/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como Detectar Fontes no Aspose.Words – Manipular Avisos e Configurações

Já se perguntou **como detectar fontes** em um documento Word antes que ele vá para produção? Você não está sozinho. Fontes ausentes podem causar pesadelos de layout, e sem avisos adequados você pode enviar um PDF ou DOCX quebrado sem nem perceber.

Neste tutorial vamos percorrer **como detectar fontes** usando Aspose.Words, mostrar **como manipular avisos**, e ajustar **configurações de fonte do Aspose** para que você possa **configurar avisos** exatamente da maneira que precisar. Ao final você terá um trecho pronto‑para‑executar que imprime cada substituição que o Aspose realiza, e saberá como adaptá‑lo para seus próprios projetos.

## Pré-requisitos

- .NET 6+ (ou .NET Framework 4.6+).  
- Aspose.Words para .NET instalado via NuGet (`Install-Package Aspose.Words`).  
- Um arquivo Word que intencionalmente referencia uma fonte ausente (por exemplo, *DocumentWithMissingFonts.docx*).  

Se você já tem isso, ótimo—vamos mergulhar.

![how to detect fonts screenshot](https://example.com/detect-fonts.png "how to detect fonts example output")

## Como Detectar Fontes com Aspose.Words

O primeiro passo é informar ao Aspose.Words que você se importa com eventos de substituição de fontes. Isso é feito fornecendo um callback de aviso personalizado através das **configurações de fonte do Aspose**. O callback recebe um objeto `WarningInfo` para cada substituição, permitindo que você **detecte fontes** em tempo de execução.

### Etapa 1: Criar uma Classe de Callback de Aviso

Implemente a interface `IWarningCallback`. Dentro do método `Warning`, filtre por `WarningType.FontSubstitution` e registre os detalhes.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Receives warnings from Aspose.Words during document loading.
/// </summary>
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Only act on font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // This is where we **detect fonts** that were missing.
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

> **Dica profissional:** A string `info.Description` contém tanto o nome da fonte ausente quanto a fonte substituta escolhida pelo Aspose. Você pode analisá‑la se precisar de um relatório estruturado.

### Etapa 2: Configurar LoadOptions com Configurações de Fonte do Aspose

Crie uma instância de `LoadOptions`, anexe um novo objeto `FontSettings` e aponte `WarningCallback` para o manipulador que acabamos de construir. Isso informa ao Aspose **como configurar avisos**.

```csharp
// Prepare load options – this is where we **configure warnings**.
LoadOptions loadOptions = new LoadOptions
{
    // FontSettings can be further customized (e.g., add a custom folder).
    FontSettings = new FontSettings(),
    WarningCallback = new FontSubstitutionWarningHandler()
};
```

Se você tem uma pasta de fontes privada, pode adicioná‑la assim:

```csharp
loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", false);
```

Essa linha mostra outra perspectiva das **configurações de fonte do Aspose**—você controla exatamente onde o Aspose procura fontes antes de decidir substituir.

### Etapa 3: Carregar o Documento e Acionar o Callback

Agora carregue o documento alvo com o `loadOptions`. À medida que o Aspose analisa o arquivo, qualquer fonte ausente aciona o manipulador de avisos, detectando **fontes** dinamicamente.

```csharp
// The document contains missing fonts, which will fire our warning handler.
Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFonts.docx", loadOptions);
```

Ao executar o programa, você verá uma saída semelhante a:

```
Font substituted: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Font substituted: Font 'Times New Roman' was not found. Substituted with 'Calibri'.
```

### Etapa 4: (Opcional) Coletar Avisos para Uso Posterior

Se precisar armazenar os dados de substituição para um relatório, modifique o manipulador para acumular mensagens em uma lista.

```csharp
class FontSubstitutionWarningHandler : IWarningCallback
{
    public List<string> Substitutions { get; } = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Substitutions.Add(info.Description);
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

Depois, você pode gravar `handler.Substitutions` em um arquivo JSON, enviá‑lo para um serviço de log ou exibi‑lo em uma interface de usuário.

### Etapa 5: Verificar o Resultado Programaticamente

Às vezes você quer garantir que *nenhuma* substituição ocorreu (por exemplo, em uma build de CI). Aqui está uma verificação rápida:

```csharp
var handler = new FontSubstitutionWarningHandler();
loadOptions.WarningCallback = handler;

Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFonts.docx", loadOptions);

if (handler.Substitutions.Count == 0)
{
    Console.WriteLine("All fonts were found – no substitutions.");
}
else
{
    Console.WriteLine($"Detected {handler.Substitutions.Count} missing fonts.");
}
```

Esse trecho demonstra **como manipular avisos** de forma determinística, dando controle total sobre o pipeline de build.

## Perguntas Frequentes (e Casos Limítrofes)

**E se eu precisar ignorar certas substituições?**  
Você pode adicionar lógica condicional dentro de `Warning` e simplesmente retornar sem registrar para fontes que considerar aceitáveis.

**Posso suprimir todos os avisos e obter apenas um resultado booleano?**  
Sim—defina `loadOptions.WarningCallback = null` e então inspecione `doc.FontInfo` após o carregamento (embora você perca o log detalhado).

**Isso funciona com conversão para PDF?**  
Absolutamente. O mesmo mecanismo de aviso é disparado quando você chama `doc.Save("out.pdf")`. O callback capturará quaisquer trocas de fontes realizadas durante a etapa de conversão.

**Existe impacto de desempenho?**  
O overhead é mínimo—apenas algumas chamadas de método extras por fonte ausente. Para lotes grandes, pode ser interessante armazenar em cache os resultados.

## Conclusão: O Que Cobrimos

- **Como detectar fontes** implementando um `IWarningCallback` personalizado.  
- **Como manipular avisos** através de `LoadOptions.WarningCallback`.  
- Ajustando **configurações de fonte do Aspose** (adicionando pastas de fontes personalizadas, habilitando/desabilitando avisos).  
- **Como configurar avisos** tanto para saída imediata no console quanto para análise posterior.  

Com essas peças em mãos, você pode processar documentos Word com confiança, garantir que fontes ausentes sejam sinalizadas e manter sua saída consistente em diferentes ambientes.

## Próximos Passos

- Explore `FontSettings.SubstitutionSettings` para um controle mais granular (por exemplo, mapeando fontes ausentes específicas para substitutos escolhidos).  
- Combine esta abordagem com Aspose.PDF para gerar PDFs que mantêm a tipografia exata.  
- Automatize a verificação de avisos em um pipeline CI/CD para bloquear lançamentos que contenham problemas de fontes—perfeito para equipes que **manipulam avisos** como parte dos portões de qualidade.

Tem mais perguntas sobre **configurações de fonte do Aspose** ou precisa de ajuda para integrar isso em um serviço maior? Deixe um comentário abaixo, e feliz codificação!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}