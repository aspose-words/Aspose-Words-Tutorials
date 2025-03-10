---
title: 글꼴 폴더 설정
linktitle: 글꼴 폴더 설정
second_title: Aspose.Words 문서 처리 API
description: Aspose.Words for .NET에서 사용자 지정 글꼴 폴더를 설정하는 방법을 알아보세요. 이렇게 하면 Word 문서에서 글꼴이 누락되지 않고 올바르게 렌더링됩니다.
weight: 10
url: /ko/net/working-with-fonts/set-fonts-folder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 글꼴 폴더 설정

## 소개

.NET 애플리케이션에서 Word 문서로 작업하는 동안 글꼴이 누락되는 문제에 직면한 적이 있습니까? 글쎄요, 당신만 그런 것은 아닙니다. 올바른 글꼴 폴더를 설정하면 이 문제를 완벽하게 해결할 수 있습니다. 이 가이드에서는 Aspose.Words for .NET을 사용하여 글꼴 폴더를 설정하는 방법을 안내해 드리겠습니다. 시작해 볼까요!

## 필수 조건

시작하기 전에 다음 사항이 있는지 확인하세요.

- 컴퓨터에 설치된 Visual Studio
- .NET Framework 설정
-  .NET 라이브러리용 Aspose.Words. 아직 다운로드하지 않았다면 다음에서 다운로드할 수 있습니다.[여기](https://releases.aspose.com/words/net/).

## 네임스페이스 가져오기

먼저 Aspose.Words에서 작업하는 데 필요한 네임스페이스를 가져와야 합니다. 코드 파일의 맨 위에 다음 줄을 추가합니다.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

이러한 단계를 주의 깊게 따르면 글꼴 폴더를 설정하는 것은 간단합니다.

## 1단계: 문서 디렉토리 정의

무엇보다도 먼저 문서 디렉토리 경로를 정의하세요. 이 디렉토리에는 Word 문서와 사용하고 싶은 글꼴이 들어 있습니다.

```csharp
// 문서 디렉토리 경로
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 교체를 꼭 해주세요`"YOUR DOCUMENT DIRECTORY"` 디렉토리의 실제 경로를 포함합니다.

## 2단계: FontSettings 초기화

 이제 초기화해야 합니다.`FontSettings` 객체. 이 객체를 사용하면 사용자 정의 글꼴 폴더를 지정할 수 있습니다.

```csharp
FontSettings fontSettings = new FontSettings();
```

## 3단계: 글꼴 폴더 설정

 사용하여`SetFontsFolder` 의 방법`FontSettings` 개체에서 사용자 정의 글꼴이 저장된 폴더를 지정합니다.

```csharp
fontSettings.SetFontsFolder(dataDir + "Fonts", false);
```

 여기,`dataDir + "Fonts"` 문서 디렉토리 내의 "Fonts"라는 폴더를 가리킵니다. 두 번째 매개변수는`false`, 폴더가 재귀적이지 않음을 나타냅니다.

## 4단계: LoadOptions 생성

 다음으로 인스턴스를 생성합니다.`LoadOptions` 클래스. 이 클래스는 지정된 글꼴 설정으로 문서를 로드하는 데 도움이 됩니다.

```csharp
LoadOptions loadOptions = new LoadOptions();
loadOptions.FontSettings = fontSettings;
```

## 5단계: 문서 로드

 마지막으로 다음을 사용하여 Word 문서를 로드합니다.`Document` 클래스와`LoadOptions` 물체.

```csharp
Document doc = new Document(dataDir + "Rendering.docx", loadOptions);
```

 확인해주세요`"Rendering.docx"` 는 Word 문서의 이름입니다. 파일 이름으로 바꿀 수 있습니다.

## 결론

이제 다 됐어요! 다음 단계를 따르면 Aspose.Words for .NET에서 사용자 정의 글꼴 폴더를 쉽게 설정하여 모든 글꼴이 올바르게 렌더링되도록 할 수 있습니다. 이 간단한 설정으로 많은 골치 아픈 일을 덜 수 있고 문서를 원하는 대로 정확하게 보이게 할 수 있습니다.

## 자주 묻는 질문

### 사용자 정의 글꼴 폴더를 설정해야 하는 이유는 무엇입니까?
사용자 지정 글꼴 폴더를 설정하면 Word 문서에서 사용된 모든 글꼴이 올바르게 렌더링되어 글꼴 누락 문제를 방지할 수 있습니다.

### 여러 개의 글꼴 폴더를 설정할 수 있나요?
 네, 사용할 수 있습니다`SetFontsFolders` 여러 폴더를 지정하는 방법.

### 글꼴을 찾을 수 없으면 어떻게 되나요?
Aspose.Words는 누락된 글꼴을 시스템 글꼴 중 비슷한 글꼴로 대체하려고 시도합니다.

### Aspose.Words는 .NET Core와 호환됩니까?
네, Aspose.Words는 .NET Framework와 함께 .NET Core도 지원합니다.

### 문제가 발생하면 어디에서 지원을 받을 수 있나요?
 당신은에서 지원을 받을 수 있습니다[Aspose.Words 지원 포럼](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
