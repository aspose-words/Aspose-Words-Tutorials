---
"description": "Aspose.Words for .NET에서 사용자 지정 글꼴 폴더를 설정하는 방법을 알아봅니다. 이렇게 하면 Word 문서에서 글꼴이 누락되지 않고 올바르게 렌더링됩니다."
"linktitle": "글꼴 폴더 설정"
"second_title": "Aspose.Words 문서 처리 API"
"title": "글꼴 폴더 설정"
"url": "/ko/net/working-with-fonts/set-fonts-folder/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 글꼴 폴더 설정

## 소개

.NET 애플리케이션에서 Word 문서 작업 시 글꼴 누락 문제를 경험해 보신 적 있으신가요? 여러분만 그런 게 아닙니다. 올바른 글꼴 폴더를 설정하면 이 문제를 완벽하게 해결할 수 있습니다. 이 가이드에서는 Aspose.Words for .NET을 사용하여 글꼴 폴더를 설정하는 방법을 안내해 드리겠습니다. 자세히 살펴보겠습니다!

## 필수 조건

시작하기에 앞서 다음 사항이 있는지 확인하세요.

- 컴퓨터에 Visual Studio가 설치되어 있습니다
- .NET Framework 설정
- Aspose.Words for .NET 라이브러리입니다. 아직 다운로드하지 않으셨다면 다음에서 다운로드할 수 있습니다. [여기](https://releases.aspose.com/words/net/).

## 네임스페이스 가져오기

먼저 Aspose.Words를 사용하는 데 필요한 네임스페이스를 가져와야 합니다. 코드 파일 맨 위에 다음 줄을 추가하세요.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

이러한 단계를 주의 깊게 따르면 글꼴 폴더를 설정하는 것은 간단합니다.

## 1단계: 문서 디렉토리 정의

무엇보다 먼저 문서 디렉터리 경로를 정의하세요. 이 디렉터리에는 Word 문서와 사용할 글꼴이 저장됩니다.

```csharp
// 문서 디렉토리 경로
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

교체를 꼭 해주세요 `"YOUR DOCUMENT DIRECTORY"` 디렉토리의 실제 경로를 사용합니다.

## 2단계: FontSettings 초기화

이제 초기화해야 합니다. `FontSettings` 객체입니다. 이 객체를 사용하면 사용자 정의 글꼴 폴더를 지정할 수 있습니다.

```csharp
FontSettings fontSettings = new FontSettings();
```

## 3단계: 글꼴 폴더 설정

를 사용하여 `SetFontsFolder` 방법 `FontSettings` 개체에서 사용자 정의 글꼴이 저장된 폴더를 지정합니다.

```csharp
fontSettings.SetFontsFolder(dataDir + "Fonts", false);
```

여기, `dataDir + "Fonts"` 문서 디렉터리 내의 "Fonts"라는 폴더를 가리킵니다. 두 번째 매개변수는 `false`, 폴더가 재귀적이지 않음을 나타냅니다.

## 4단계: LoadOptions 만들기

다음으로 인스턴스를 생성합니다. `LoadOptions` 클래스입니다. 이 클래스는 지정된 글꼴 설정으로 문서를 로드하는 데 도움이 됩니다.

```csharp
LoadOptions loadOptions = new LoadOptions();
loadOptions.FontSettings = fontSettings;
```

## 5단계: 문서 로드

마지막으로 다음을 사용하여 Word 문서를 로드합니다. `Document` 수업과 `LoadOptions` 물체.

```csharp
Document doc = new Document(dataDir + "Rendering.docx", loadOptions);
```

확인해주세요 `"Rendering.docx"` 는 Word 문서의 이름입니다. 파일 이름으로 바꿔도 됩니다.

## 결론

자, 이제 완료되었습니다! 다음 단계를 따라 Aspose.Words for .NET에서 사용자 지정 글꼴 폴더를 쉽게 설정하여 모든 글꼴이 올바르게 렌더링되도록 할 수 있습니다. 이 간단한 설정으로 많은 번거로움을 덜고 문서를 원하는 대로 정확하게 표현할 수 있습니다.

## 자주 묻는 질문

### 사용자 정의 글꼴 폴더를 설정해야 하는 이유는 무엇입니까?
사용자 지정 글꼴 폴더를 설정하면 Word 문서에 사용된 모든 글꼴이 올바르게 렌더링되어 글꼴 누락 문제를 방지할 수 있습니다.

### 여러 개의 글꼴 폴더를 설정할 수 있나요?
네, 사용할 수 있습니다 `SetFontsFolders` 여러 폴더를 지정하는 방법.

### 글꼴을 찾을 수 없으면 어떻게 되나요?
Aspose.Words는 누락된 글꼴을 시스템 글꼴 중 유사한 글꼴로 대체하려고 시도합니다.

### Aspose.Words는 .NET Core와 호환됩니까?
네, Aspose.Words는 .NET Framework와 함께 .NET Core도 지원합니다.

### 문제가 발생하면 어디에서 지원을 받을 수 있나요?
당신은에서 지원을 받을 수 있습니다 [Aspose.Words 지원 포럼](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}