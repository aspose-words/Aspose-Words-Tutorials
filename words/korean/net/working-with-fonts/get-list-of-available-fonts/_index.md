---
"description": "이 자세한 단계별 튜토리얼을 통해 Aspose.Words for .NET을 사용하여 사용 가능한 글꼴 목록을 얻는 방법을 알아보세요. 글꼴 관리 기술을 향상시켜 보세요."
"linktitle": "사용 가능한 글꼴 목록 가져오기"
"second_title": "Aspose.Words 문서 처리 API"
"title": "사용 가능한 글꼴 목록 가져오기"
"url": "/ko/net/working-with-fonts/get-list-of-available-fonts/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 사용 가능한 글꼴 목록 가져오기

## 소개

Word 문서에서 글꼴 관리에 어려움을 겪어 보신 적이 있으신가요? .NET 개발자라면 Aspose.Words for .NET이 해결책이 될 수 있습니다! 이 강력한 라이브러리는 Word 문서를 프로그래밍 방식으로 만들고 조작하는 데 도움이 될 뿐만 아니라 광범위한 글꼴 관리 기능도 제공합니다. 이 가이드에서는 Aspose.Words for .NET을 사용하여 사용 가능한 글꼴 목록을 가져오는 방법을 단계별로 안내합니다. 쉽게 따라 할 수 있도록 이해하기 쉬운 단계로 나누어 설명하겠습니다. 자, 이제 글꼴 관리를 더욱 쉽게 만들어 볼까요?

## 필수 조건

시작하기 전에 몇 가지 필요한 것이 있습니다.

- Aspose.Words for .NET: Aspose.Words for .NET 라이브러리가 설치되어 있는지 확인하세요. 다음에서 다운로드할 수 있습니다. [여기](https://releases.aspose.com/words/net/).
- Visual Studio: 이 예제에서는 Visual Studio를 개발 환경으로 사용합니다.
- .NET Framework: 컴퓨터에 .NET Framework가 설치되어 있는지 확인하세요.
- 문서 디렉토리: 문서가 저장되는 디렉토리 경로입니다.

## 네임스페이스 가져오기

먼저, 프로젝트에 필요한 네임스페이스를 가져옵니다.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;
```

## 1단계: 글꼴 설정 초기화

첫 번째 단계는 글꼴 설정을 초기화하는 것입니다. 이를 통해 문서의 글꼴 소스를 관리할 수 있습니다.

```csharp
FontSettings fontSettings = new FontSettings();
List<FontSourceBase> fontSources = new List<FontSourceBase>(fontSettings.GetFontsSources());
```

- FontSettings: 이 클래스는 글꼴 대체 및 글꼴 소스에 대한 설정을 지정하는 데 사용됩니다.
- fontSources: 현재 글꼴 설정에서 기존 글꼴 소스 목록을 만듭니다.

## 2단계: 문서 디렉토리 정의

다음으로, 문서 디렉터리 경로를 지정하세요. Aspose.Words가 글꼴을 검색할 디렉터리입니다.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

- dataDir: 이 문자열 변수는 글꼴이 있는 디렉터리 경로를 저장합니다. `"YOUR DOCUMENT DIRECTORY"` 실제 경로와 함께.

## 3단계: 사용자 정의 글꼴 폴더 추가

이제 Aspose.Words가 이 폴더에서 글꼴을 검색하도록 지시하기 위해 새 폴더 소스를 추가합니다.

```csharp
FolderFontSource folderFontSource = new FolderFontSource(dataDir, true);
```

- FolderFontSource: 이 클래스는 폴더 글꼴 소스를 나타냅니다. 두 번째 매개변수(`true`)는 하위 폴더에서 글꼴을 재귀적으로 검색할지 여부를 나타냅니다.

## 4단계: 글꼴 소스 업데이트

기존 글꼴 소스 목록에 사용자 정의 글꼴 폴더를 추가하고 글꼴 설정을 업데이트합니다.

```csharp
fontSources.Add(folderFontSource);
FontSourceBase[] updatedFontSources = fontSources.ToArray();
```

- fontSources.Add(folderFontSource): 기존 글꼴 소스에 사용자 정의 글꼴 폴더를 추가합니다.
- updatedFontSources: 글꼴 소스 목록을 배열로 변환합니다.

## 5단계: 글꼴 검색 및 표시

마지막으로, 사용 가능한 글꼴을 검색하여 세부 정보를 표시합니다.

```csharp
foreach (PhysicalFontInfo fontInfo in updatedFontSources[0].GetAvailableFonts())
{
    Console.WriteLine("FontFamilyName : " + fontInfo.FontFamilyName);
    Console.WriteLine("FullFontName  : " + fontInfo.FullFontName);
    Console.WriteLine("Version  : " + fontInfo.Version);
    Console.WriteLine("FilePath : " + fontInfo.FilePath);
}
```

- GetAvailableFonts(): 업데이트된 목록의 첫 번째 글꼴 소스에서 사용 가능한 글꼴 목록을 검색합니다.
- fontInfo: 인스턴스 `PhysicalFontInfo` 각 글꼴에 대한 세부 정보가 포함되어 있습니다.

## 결론

축하합니다! Aspose.Words for .NET을 사용하여 사용 가능한 글꼴 목록을 성공적으로 가져오셨습니다. 이 튜토리얼에서는 글꼴 설정 초기화부터 글꼴 세부 정보 표시까지 각 단계를 안내해 드렸습니다. 이 지식을 바탕으로 이제 Word 문서에서 글꼴을 쉽게 관리할 수 있습니다. Aspose.Words for .NET은 문서 처리 능력을 크게 향상시킬 수 있는 강력한 도구입니다. 개발 프로세스를 더욱 효율적으로 만들어 줄 더 많은 기능을 살펴보세요.

## 자주 묻는 질문

### Aspose.Words for .NET을 다른 .NET 프레임워크와 함께 사용할 수 있나요?
네, Aspose.Words for .NET은 .NET Core 및 .NET 5+를 포함한 다양한 .NET 프레임워크와 호환됩니다.

### Aspose.Words for .NET을 어떻게 설치하나요?
Visual Studio에서 NuGet 패키지 관리자를 통해 "Aspose.Words"를 검색하여 설치할 수 있습니다.

### 여러 개의 사용자 정의 글꼴 폴더를 추가할 수 있나요?
예, 여러 개의 사용자 정의 글꼴 폴더를 생성하여 여러 개의 사용자 정의 글꼴 폴더를 추가할 수 있습니다. `FolderFontSource` 인스턴스를 만들고 이를 글꼴 소스 목록에 추가합니다.

### 특정 글꼴 소스에서 글꼴 세부 정보를 검색할 수 있나요?
예, 글꼴 소스의 인덱스를 지정하여 모든 글꼴 소스에서 글꼴 세부 정보를 검색할 수 있습니다. `updatedFontSources` 정렬.

### Aspose.Words for .NET은 글꼴 대체를 지원합니까?
네, 원래 글꼴을 사용할 수 없더라도 텍스트가 올바르게 렌더링되도록 글꼴 대체를 지원합니다.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}