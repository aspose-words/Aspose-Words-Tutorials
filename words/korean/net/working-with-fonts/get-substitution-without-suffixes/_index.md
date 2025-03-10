---
title: 접미사 없이 대체 가져오기
linktitle: 접미사 없이 대체 가져오기
second_title: Aspose.Words 문서 처리 API
description: Aspose.Words for .NET에서 접미사 없이 글꼴 대체를 관리하는 방법을 알아보세요. 단계별 가이드를 따라 문서가 항상 완벽하게 보이도록 하세요.
weight: 10
url: /ko/net/working-with-fonts/get-substitution-without-suffixes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 접미사 없이 대체 가져오기

## 소개

Aspose.Words for .NET을 사용하여 글꼴 대체를 관리하는 방법에 대한 포괄적인 가이드에 오신 것을 환영합니다. 문서에서 글꼴이 올바르게 표시되지 않는 문제로 어려움을 겪은 적이 있다면 올바른 곳에 왔습니다. 이 튜토리얼은 접미사 없이 효율적으로 글꼴 대체를 처리하는 단계별 프로세스를 안내합니다.

## 필수 조건

튜토리얼을 시작하기 전에 다음 사항이 있는지 확인하세요.

- C#에 대한 기본 지식: C# 프로그래밍을 이해하면 단계를 따르고 구현하기가 더 쉬워집니다.
-  Aspose.Words for .NET 라이브러리: 라이브러리를 다운로드하여 설치하세요.[다운로드 링크](https://releases.aspose.com/words/net/).
- 개발 환경: Visual Studio와 같은 개발 환경을 설정하여 코드를 작성하고 실행하세요.
-  샘플 문서: 샘플 문서(예:`Rendering.docx`이 튜토리얼에서 사용할 수 있는 항목은 다음과 같습니다.

## 네임스페이스 가져오기

먼저, Aspose.Words가 제공하는 클래스와 메서드에 액세스하는 데 필요한 네임스페이스를 가져와야 합니다.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System.Collections.Generic;
```

## 1단계: 문서 디렉토리 정의

시작하려면 문서가 있는 디렉토리를 지정하세요. 이렇게 하면 작업하려는 문서를 찾는 데 도움이 됩니다.

```csharp
// 문서 디렉토리 경로
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 2단계: 대체 경고 핸들러 설정

다음으로, 문서 처리 중에 글꼴 대체가 발생할 때마다 알려주는 경고 핸들러를 설정해야 합니다. 이는 글꼴 문제를 포착하고 처리하는 데 필수적입니다.

```csharp
DocumentSubstitutionWarnings substitutionWarningHandler = new DocumentSubstitutionWarnings();
Document doc = new Document(dataDir + "Rendering.docx");
doc.WarningCallback = substitutionWarningHandler;
```

## 3단계: 사용자 정의 글꼴 소스 추가

이 단계에서는 Aspose.Words가 올바른 글꼴을 찾아 사용할 수 있도록 사용자 지정 글꼴 소스를 추가합니다. 이는 사용자 지정 디렉토리에 특정 글꼴이 저장된 경우 특히 유용합니다.

```csharp
List<FontSourceBase> fontSources = new List<FontSourceBase>(FontSettings.DefaultInstance.GetFontsSources());

FolderFontSource folderFontSource = new FolderFontSource("C:\\MyFonts\\", true);
fontSources.Add(folderFontSource);

FontSourceBase[] updatedFontSources = fontSources.ToArray();
FontSettings.DefaultInstance.SetFontsSources(updatedFontSources);
```

이 코드에서는:
-  현재 글꼴 소스를 검색하여 새 글꼴 소스를 추가합니다.`FolderFontSource` 사용자 정의 글꼴 디렉토리를 가리킴(`C:\\MyFonts\\`).
- 그런 다음 이 새로운 목록을 사용하여 글꼴 소스를 업데이트합니다.

## 4단계: 문서 저장

마지막으로 글꼴 대체 설정을 적용한 후 문서를 저장합니다. 이 튜토리얼에서는 PDF로 저장합니다.

```csharp
doc.Save(dataDir + "WorkingWithFonts.GetSubstitutionWithoutSuffixes.pdf");
```

## 5단계: 경고 처리기 클래스 생성

 경고를 효과적으로 처리하려면 다음을 구현하는 사용자 정의 클래스를 만듭니다.`IWarningCallback` 인터페이스. 이 클래스는 모든 글꼴 대체 경고를 캡처하고 기록합니다.

```csharp
public class DocumentSubstitutionWarnings : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
            FontWarnings.Warning(info);
    }

    public WarningInfoCollection FontWarnings = new WarningInfoCollection();
}
```

이 수업에서는:
-  그만큼`Warning`이 방법은 글꼴 대체와 관련된 경고를 캡처합니다.
-  그만큼`FontWarnings` 컬렉션은 이러한 경고를 추가 검사 또는 로깅을 위해 저장합니다.

## 결론

이제 Aspose.Words for .NET을 사용하여 접미사 없이 글꼴 대체를 처리하는 프로세스를 마스터했습니다. 이 지식은 시스템에서 사용 가능한 글꼴에 관계없이 문서가 의도한 모양을 유지하도록 보장합니다. Aspose.Words의 힘을 최대한 활용하기 위해 다양한 설정과 소스를 계속 실험하세요.

## 자주 묻는 질문

### 여러 사용자 정의 디렉토리의 글꼴을 어떻게 사용할 수 있나요?

 여러개를 추가할 수 있습니다`FolderFontSource` 인스턴스에`fontSources` 글꼴 소스를 나열하고 이에 따라 업데이트합니다.

### Aspose.Words for .NET의 무료 평가판은 어디에서 다운로드할 수 있나요?

 무료 평가판을 다운로드할 수 있습니다.[Aspose 무료 체험 페이지](https://releases.aspose.com/).

###  여러 유형의 경고를 사용하여 처리할 수 있습니까?`IWarningCallback`?

 네,`IWarningCallback` 인터페이스를 사용하면 글꼴 대체뿐 아니라 다양한 유형의 경고를 처리할 수 있습니다.

### Aspose.Words에 대한 지원은 어디서 받을 수 있나요?

 지원을 받으려면 다음을 방문하세요.[Aspose.Words 지원 포럼](https://forum.aspose.com/c/words/8).

### 임시 면허를 구매할 수 있나요?

 네, 임시 면허증을 받을 수 있습니다.[임시 라이센스 페이지](https://purchase.aspose.com/temporary-license/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
