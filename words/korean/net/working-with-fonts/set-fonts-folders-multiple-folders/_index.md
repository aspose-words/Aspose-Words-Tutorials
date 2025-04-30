---
"description": "Aspose.Words for .NET을 사용하여 Word 문서에 여러 글꼴 폴더를 설정하는 방법을 알아보세요. 이 단계별 가이드를 통해 문서에 필요한 글꼴을 정확하게 사용할 수 있습니다."
"linktitle": "글꼴 폴더 여러 폴더 설정"
"second_title": "Aspose.Words 문서 처리 API"
"title": "글꼴 폴더 여러 폴더 설정"
"url": "/ko/net/working-with-fonts/set-fonts-folders-multiple-folders/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 글꼴 폴더 여러 폴더 설정

## 소개

Word 문서에서 여러 글꼴 원본을 관리하는 방법을 궁금해하신 적 있으신가요? 여러 폴더에 글꼴이 흩어져 있고, 문서에서 글꼴을 원활하게 사용할 수 있는 방법이 필요하신가요? 이제 잘 오셨습니다! 오늘은 Aspose.Words for .NET을 사용하여 글꼴 폴더를 설정하는 방법을 자세히 알아보겠습니다. 이 가이드에서는 이 과정을 단계별로 안내하여 문서가 원하는 대로 보이도록 보장합니다.

## 필수 조건

시작하기 전에 필요한 모든 것을 준비했는지 확인해 보세요. 따라야 할 내용은 다음과 같습니다.

- Aspose.Words for .NET: 아직 Aspose.Words for .NET을 다운로드하지 않으셨다면 다운로드하여 설치하세요. [여기](https://releases.aspose.com/words/net/).
- 개발 환경: Visual Studio 또는 기타 .NET 호환 개발 환경.
- C#에 대한 기본 지식: C#에 대한 약간의 지식이 있으면 예제를 따라가는 데 도움이 됩니다.
- 글꼴 파일: 쉽게 접근할 수 있는 디렉토리에 글꼴 파일을 저장해 두세요.

## 네임스페이스 가져오기

먼저, C# 프로젝트에 필요한 네임스페이스를 가져오겠습니다. 이렇게 하면 필요한 모든 Aspose.Words 기능을 사용할 수 있습니다.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

이제 Aspose.Words for .NET에서 글꼴 폴더를 설정하는 단계별 가이드를 살펴보겠습니다.

## 1단계: 문서 로드

좋습니다. 작업할 Word 문서를 불러오는 것부터 시작해 보겠습니다. 문서 경로가 준비되었는지 확인하세요. 이 예시에서는 "Rendering.docx"라는 이름의 문서를 사용하겠습니다.

```csharp
// 문서 디렉토리 경로
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

여기서는 지정된 디렉터리에서 문서를 불러옵니다. 간단하죠?

## 2단계: FontSettings 개체 만들기

다음으로, 우리는 다음을 만들어야 합니다. `FontSettings` 객체입니다. 이 객체를 사용하면 문서의 글꼴 소스를 관리할 수 있습니다.

```csharp
FontSettings fontSettings = new FontSettings();
```

이것 `FontSettings` 객체는 어떤 글꼴 폴더를 사용할지 정의하는 데 도움이 됩니다.

## 3단계: 글꼴 폴더 설정

이제 중요한 부분, 글꼴 폴더 설정입니다. 글꼴이 있는 디렉터리를 지정하는 단계입니다. 이 예시에서는 "C:\MyFonts"와 "D:\Misc\Fonts"에 글꼴이 있습니다.

```csharp
fontSettings.SetFontsFolders(new[] { @"C:\MyFonts\", @"D:\Misc\Fonts\" }, true);
```

두 번째 매개변수(`true`)는 이러한 폴더가 기본 글꼴 소스를 재정의함을 나타냅니다. 시스템 글꼴 소스도 유지하려면 다음 조합을 사용할 수 있습니다. `GetFontSources` 그리고 `SetFontSources`.

## 4단계: 문서에 글꼴 설정 적용

글꼴 폴더가 설정되었으므로 이 설정을 문서에 적용해야 합니다. 이렇게 하면 렌더링 시 문서가 지정된 글꼴을 사용하게 됩니다.

```csharp
doc.FontSettings = fontSettings;
```

## 5단계: 문서 저장

마지막으로 문서를 저장해 보겠습니다. 글꼴이 실제로 어떻게 적용되는지 확인하기 위해 PDF로 저장해 보겠습니다.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersMultipleFolders.pdf");
```

자, 이제 문서에 여러 개의 글꼴 폴더가 성공적으로 설정되었습니다.

## 결론

문서에서 글꼴을 관리하는 것은 어려운 일처럼 보일 수 있지만, Aspose.Words for .NET을 사용하면 아주 간단합니다! 간단한 단계를 따라 하면 문서가 전문적으로 보이고 필요한 글꼴을 정확하게 사용할 수 있습니다. 특정 브랜딩이 필요한 프로젝트를 진행 중이든 문서의 모양을 더욱 세밀하게 제어하고 싶든, 글꼴 폴더 설정은 반드시 익혀야 할 기술입니다.

## 자주 묻는 질문

### 글꼴 폴더에 네트워크 경로를 사용할 수 있나요?
네, 글꼴 폴더에 네트워크 경로를 사용할 수 있습니다. 단, 애플리케이션에서 해당 경로에 접근할 수 있는지 확인하세요.

### 지정된 폴더에 글꼴이 없으면 어떻게 되나요?
글꼴이 없으면 Aspose.Words는 지정된 기본 글꼴을 사용하거나 대체 글꼴을 사용합니다.

### 시스템 글꼴을 재정의하지 않고 글꼴 폴더를 추가할 수 있나요?
물론입니다! 사용하세요 `FontSettings.GetFontSources` 기존 소스를 검색하고 사용자 정의 폴더와 결합하려면 다음을 사용합니다. `FontSettings.SetFontSources`.

### 추가할 수 있는 글꼴 폴더의 수에 제한이 있나요?
글꼴 폴더 개수에는 제한이 없습니다. 하지만 폴더가 많아질수록 글꼴 로딩 시간이 길어질 수 있으므로 성능에 유의하세요.

### 내 문서에 어떤 글꼴이 사용되었는지 어떻게 확인할 수 있나요?
당신은 사용할 수 있습니다 `FontSettings.GetFontsSources` 현재 문서에 설정된 글꼴 소스를 검색하고 검사하는 방법입니다.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}