---
title: 글꼴 폴더 여러 폴더 설정
linktitle: 글꼴 폴더 여러 폴더 설정
second_title: Aspose.Words 문서 처리 API
description: Aspose.Words for .NET을 사용하여 Word 문서에 여러 글꼴 폴더를 설정하는 방법을 알아보세요. 이 단계별 가이드는 문서에서 필요한 정확한 글꼴을 사용하도록 보장합니다.
weight: 10
url: /ko/net/working-with-fonts/set-fonts-folders-multiple-folders/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 글꼴 폴더 여러 폴더 설정

## 소개

Word 문서에서 여러 글꼴 소스를 관리하는 방법에 대해 궁금해 본 적이 있나요? 여러 폴더에 흩어져 있는 글꼴 모음이 있고 문서에서 이를 원활하게 사용할 수 있는 방법이 필요할 수 있습니다. 글쎄요, 운이 좋으시네요! 오늘은 Aspose.Words for .NET을 사용하여 글꼴 폴더를 설정하는 방법을 알아보겠습니다. 이 가이드에서는 프로세스를 단계별로 안내하여 문서가 원하는 대로 보이도록 합니다.

## 필수 조건

시작하기 전에 필요한 모든 것을 가지고 있는지 확인해 보겠습니다. 따라야 할 내용은 다음과 같습니다.

-  Aspose.Words for .NET: 아직 다운로드하지 않았다면 Aspose.Words for .NET을 다운로드하여 설치하세요. 받을 수 있습니다.[여기](https://releases.aspose.com/words/net/).
- 개발 환경: Visual Studio 또는 기타 .NET 호환 개발 환경.
- C#에 대한 기본 지식: C#에 대한 약간의 지식은 예제를 따라가는 데 도움이 됩니다.
- 글꼴 파일: 쉽게 접근할 수 있는 디렉토리에 글꼴 파일을 저장해 두세요.

## 네임스페이스 가져오기

우선, C# 프로젝트에 필요한 네임스페이스를 임포트해 보겠습니다. 이렇게 하면 필요한 모든 Aspose.Words 기능에 액세스할 수 있습니다.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

이제 Aspose.Words for .NET에서 글꼴 폴더를 설정하는 단계별 가이드를 살펴보겠습니다.

## 1단계: 문서 로드

좋습니다. 작업하려는 Word 문서를 로드하는 것으로 시작하겠습니다. 문서 경로가 준비되었는지 확인하세요. 이 예에서는 "Rendering.docx"라는 문서를 사용하겠습니다.

```csharp
// 문서 디렉토리 경로
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

여기서, 우리는 지정된 디렉토리에서 문서를 로드합니다. 충분히 간단하죠?

## 2단계: FontSettings 개체 생성

 다음으로, 우리는 다음을 생성해야 합니다.`FontSettings` 객체. 이 객체를 사용하면 문서의 글꼴 소스를 관리할 수 있습니다.

```csharp
FontSettings fontSettings = new FontSettings();
```

 이것`FontSettings`객체는 어떤 글꼴 폴더를 사용할지 정의하는 데 도움이 됩니다.

## 3단계: 글꼴 폴더 설정

이제 중요한 부분인 글꼴 폴더 설정에 들어갑니다. 여기서 글꼴이 있는 디렉토리를 지정합니다. 이 예에서 우리는 "C:\MyFonts"에 글꼴을 둡니다.\" 및 "D:\Misc\Fonts\".

```csharp
fontSettings.SetFontsFolders(new[] { @"C:\MyFonts\", @"D:\Misc\Fonts\" }, true);
```

두 번째 매개변수(`true` )는 이러한 폴더가 모든 기본 글꼴 소스를 재정의함을 나타냅니다. 시스템 글꼴 소스도 유지하려면 다음 조합을 사용할 수 있습니다.`GetFontSources` 그리고`SetFontSources`.

## 4단계: 문서에 글꼴 설정 적용

글꼴 폴더가 설정되면 이러한 설정을 문서에 적용해야 합니다. 이렇게 하면 렌더링 중에 문서가 지정된 글꼴을 사용하도록 할 수 있습니다.

```csharp
doc.FontSettings = fontSettings;
```

## 5단계: 문서 저장

마지막으로 문서를 저장해 보겠습니다. PDF로 저장해서 글꼴이 실제로 어떻게 동작하는지 살펴보겠습니다.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersMultipleFolders.pdf");
```

이제 다 됐어요! 문서에 여러 개의 글꼴 폴더를 성공적으로 설정했습니다.

## 결론

문서에서 글꼴을 관리하는 것은 어려운 일처럼 보일 수 있지만 Aspose.Words for .NET을 사용하면 아주 간단합니다! 이 간단한 단계를 따르면 문서가 전문적으로 보이고 필요한 정확한 글꼴을 사용할 수 있습니다. 특정 브랜딩이 필요한 프로젝트를 진행 중이든 문서의 모양을 더 많이 제어하고 싶든 글꼴 폴더 설정은 익혀야 할 기술입니다.

## 자주 묻는 질문

### 글꼴 폴더에 네트워크 경로를 사용할 수 있나요?
네, 글꼴 폴더에 네트워크 경로를 사용할 수 있습니다. 경로가 애플리케이션에서 액세스 가능한지 확인하기만 하면 됩니다.

### 지정된 폴더에 글꼴이 없으면 어떻게 되나요?
글꼴이 누락된 경우 Aspose.Words는 지정된 기본 글꼴을 사용하거나 대체 글꼴을 사용합니다.

### 시스템 글꼴을 재정의하지 않고 글꼴 폴더를 추가할 수 있나요?
 물론입니다! 사용하세요`FontSettings.GetFontSources` 기존 소스를 검색하고 사용자 정의 폴더와 결합하려면 다음을 사용합니다.`FontSettings.SetFontSources`.

### 추가할 수 있는 글꼴 폴더의 수에 제한이 있나요?
글꼴 폴더의 수에 대한 엄격한 제한은 없습니다. 그러나 폴더가 많을수록 글꼴 로딩 시간이 길어질 수 있으므로 성능에 유의하세요.

### 내 문서에 어떤 글꼴이 사용되었는지 어떻게 확인할 수 있나요?
 당신은 사용할 수 있습니다`FontSettings.GetFontsSources` 현재 문서에 설정된 글꼴 소스를 검색하고 검사하는 방법입니다.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
