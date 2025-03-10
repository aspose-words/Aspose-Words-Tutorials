---
title: 문서 텍스트 방향
linktitle: 문서 텍스트 방향
second_title: Aspose.Words 문서 처리 API
description: 이 단계별 가이드를 통해 Aspose.Words for .NET을 사용하여 Word에서 문서 텍스트 방향을 설정하는 방법을 알아보세요. 오른쪽에서 왼쪽으로 쓰는 언어를 처리하는 데 완벽합니다.
weight: 10
url: /ko/net/programming-with-txtloadoptions/document-text-direction/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 문서 텍스트 방향

## 소개

Word 문서, 특히 여러 언어나 특수 서식 요구 사항이 포함된 문서로 작업할 때 텍스트 방향을 설정하는 것이 중요할 수 있습니다. 예를 들어 히브리어나 아랍어와 같이 오른쪽에서 왼쪽으로 쓰는 언어를 다룰 때 텍스트 방향을 그에 맞게 조정해야 할 수도 있습니다. 이 가이드에서는 Aspose.Words for .NET을 사용하여 문서 텍스트 방향을 설정하는 방법을 살펴보겠습니다. 

## 필수 조건

코드를 살펴보기 전에 다음 사항이 있는지 확인하세요.

-  Aspose.Words for .NET 라이브러리: Aspose.Words for .NET이 설치되어 있는지 확인하세요. 다음에서 다운로드할 수 있습니다.[Aspose 웹사이트](https://releases.aspose.com/words/net/).
- Visual Studio: C# 코드를 작성하고 실행하기 위한 개발 환경입니다.
- C#에 대한 기본 지식: C# 프로그래밍에 익숙하면 코드를 작성할 때 도움이 됩니다.

## 네임스페이스 가져오기

시작하려면 프로젝트에서 Aspose.Words를 사용하는 데 필요한 네임스페이스를 가져와야 합니다. 방법은 다음과 같습니다.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
```

이러한 네임스페이스는 Word 문서를 조작하는 데 필요한 클래스와 메서드에 대한 액세스를 제공합니다.

## 1단계: 문서 디렉토리 경로 정의

먼저, 문서가 있는 곳의 경로를 설정합니다. 이는 파일을 올바르게 로드하고 저장하는 데 중요합니다.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 바꾸다`"YOUR DOCUMENT DIRECTORY"` 문서가 저장된 실제 경로를 사용합니다.

## 2단계: 문서 방향 설정을 사용하여 TxtLoadOptions 만들기

 다음으로 인스턴스를 생성해야 합니다.`TxtLoadOptions` 그리고 그것을 설정`DocumentDirection` 속성. 이것은 Aspose.Words에게 문서의 텍스트 방향을 처리하는 방법을 알려줍니다.

```csharp
TxtLoadOptions loadOptions = new TxtLoadOptions { DocumentDirection = DocumentDirection.Auto };
```

 이 예에서 우리는 다음을 사용합니다.`DocumentDirection.Auto` Aspose.Words가 콘텐츠에 따라 자동으로 방향을 결정하도록 합니다.

## 3단계: 문서 로드

 이제 다음을 사용하여 문서를 로드하세요.`Document` 클래스와 이전에 정의된`loadOptions`.

```csharp
Document doc = new Document(dataDir + "Hebrew text.txt", loadOptions);
```

 여기,`"Hebrew text.txt"` 는 텍스트 파일의 이름입니다. 이 파일이 지정된 디렉토리에 있는지 확인하세요.

## 4단계: 문단의 양방향 서식에 액세스하고 확인합니다.

텍스트 방향이 올바르게 설정되었는지 확인하려면 문서의 첫 번째 문단에 접근하여 양방향 서식을 확인하세요.

```csharp
Paragraph paragraph = doc.FirstSection.Body.FirstParagraph;
Console.WriteLine(paragraph.ParagraphFormat.Bidi);
```

이 단계는 디버깅과 문서의 텍스트 방향이 예상대로 적용되었는지 확인하는 데 유용합니다.

## 5단계: 새 설정으로 문서 저장

마지막으로, 변경 사항을 적용하고 유지하려면 문서를 저장하세요.

```csharp
doc.Save(dataDir + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
```

 여기,`"WorkingWithTxtLoadOptions.DocumentTextDirection.docx"` 출력 파일의 이름입니다. 변경한 내용을 반영하는 이름을 선택해야 합니다.

## 결론

Aspose.Words for .NET을 사용하면 Word 문서에서 텍스트 방향을 설정하는 것은 간단한 프로세스입니다. 이러한 단계를 따르면 문서에서 오른쪽에서 왼쪽으로 또는 왼쪽에서 오른쪽으로 텍스트를 처리하는 방식을 쉽게 구성할 수 있습니다. 다국어 문서로 작업하든 특정 언어에 대한 텍스트 방향을 포맷해야 하든 Aspose.Words는 요구 사항을 충족하는 강력한 솔루션을 제공합니다.

## 자주 묻는 질문

###  무엇입니까?`DocumentDirection` property used for?

 그만큼`DocumentDirection` 속성`TxtLoadOptions` 문서의 텍스트 방향을 결정합니다. 다음으로 설정할 수 있습니다.`DocumentDirection.Auto`, `DocumentDirection.LeftToRight` , 또는`DocumentDirection.RightToLeft`.

### 문서 전체가 아닌 특정 문단의 텍스트 방향을 설정할 수 있나요?

 예, 다음을 사용하여 특정 문단의 텍스트 방향을 설정할 수 있습니다.`ParagraphFormat.Bidi` 재산이지만`TxtLoadOptions.DocumentDirection` 속성은 전체 문서의 기본 방향을 설정합니다.

###  로딩이 지원되는 파일 형식은 무엇입니까?`TxtLoadOptions`?

`TxtLoadOptions` 주로 텍스트 파일(.txt)을 로드하는 데 사용됩니다. 다른 파일 형식의 경우 다음과 같은 다른 클래스를 사용합니다.`DocLoadOptions` 또는`DocxLoadOptions`.

### 혼합된 텍스트 지시사항이 있는 문서를 어떻게 처리할 수 있나요?

 혼합된 텍스트 방향이 있는 문서의 경우 문단별로 서식을 처리해야 할 수 있습니다. 다음을 사용하십시오.`ParagraphFormat.Bidi` 필요에 따라 각 문단의 방향을 조정하는 속성입니다.

### Aspose.Words for .NET에 대한 자세한 정보는 어디에서 찾을 수 있나요?

 자세한 내용은 다음을 확인하세요.[.NET 설명서를 위한 Aspose.Words](https://reference.aspose.com/words/net/) . 또한 다음과 같은 추가 리소스를 탐색할 수도 있습니다.[다운로드 링크](https://releases.aspose.com/words/net/), [구입하다](https://purchase.aspose.com/buy), [무료 체험](https://releases.aspose.com/), [임시 라이센스](https://purchase.aspose.com/temporary-license/) , 그리고[지원하다](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
