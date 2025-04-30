---
"description": "Aspose.Words for .NET을 사용하여 일반 텍스트 문서에서 공백이 포함된 번호 매기기를 감지하고 목록이 올바르게 인식되는지 확인하는 방법을 알아보세요."
"linktitle": "공백이 있는 번호 매기기 감지"
"second_title": "Aspose.Words 문서 처리 API"
"title": "공백이 있는 번호 매기기 감지"
"url": "/ko/net/programming-with-txtloadoptions/detect-numbering-with-whitespaces/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 공백이 있는 번호 매기기 감지

## 소개

.NET 애호가를 위한 Aspose.Words! 오늘은 일반 텍스트 문서에서 목록 처리를 간편하게 해주는 흥미로운 기능을 살펴보겠습니다. 텍스트 파일에서 일부 줄이 목록이어야 하는데 Word 문서에 불러오면 제대로 보이지 않는 문제를 겪어본 적이 있으신가요? 공백이 포함된 번호 매기기를 감지하는 멋진 방법을 소개합니다. 이 튜토리얼에서는 `DetectNumberingWithWhitespaces` Aspose.Words for .NET의 이 옵션을 사용하면 숫자와 텍스트 사이에 공백이 있는 경우에도 목록이 올바르게 인식됩니다.

## 필수 조건

시작하기에 앞서 다음 사항이 있는지 확인하세요.

- Aspose.Words for .NET: 다음에서 다운로드할 수 있습니다. [Aspose 릴리스](https://releases.aspose.com/words/net/) 페이지.
- 개발 환경: Visual Studio 또는 기타 C# IDE.
- 컴퓨터에 .NET Framework가 설치되어 있어야 합니다.
- C#에 대한 기본 지식: 기본 사항을 이해하면 예제를 따라가는 데 도움이 됩니다.

## 네임스페이스 가져오기

코드 작업을 시작하기 전에 프로젝트에 필요한 네임스페이스를 가져왔는지 확인하세요. 다음은 간단한 코드 조각입니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;
```

이 과정을 간단하고 관리하기 쉬운 단계로 나누어 보겠습니다. 각 단계에서 필요한 코드를 안내하고 진행 상황을 설명하겠습니다.

## 1단계: 문서 디렉터리 정의

먼저, 문서 디렉터리 경로를 설정해 보겠습니다. 여기에 입력 및 출력 파일이 저장됩니다.

```csharp
// 문서 디렉토리 경로
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 2단계: 일반 텍스트 문서 만들기

다음으로, 문자열 형태의 일반 텍스트 문서를 생성하겠습니다. 이 문서에는 목록으로 해석될 수 있는 부분이 포함됩니다.

```csharp
const string textDoc = "Full stop delimiters:\n" +
                       "1. First list item 1\n" +
                       "2. First list item 2\n" +
                       "3. First list item 3\n\n" +
                       "Right bracket delimiters:\n" +
                       "1) Second list item 1\n" +
                       "2) Second list item 2\n" +
                       "3) Second list item 3\n\n" +
                       "Bullet delimiters:\n" +
                       "• Third list item 1\n" +
                       "• Third list item 2\n" +
                       "• Third list item 3\n\n" +
                       "Whitespace delimiters:\n" +
                       "1 Fourth list item 1\n" +
                       "2 Fourth list item 2\n" +
                       "3 Fourth list item 3";
```

## 3단계: LoadOptions 구성

공백이 포함된 번호 매기기를 감지하려면 다음을 설정해야 합니다. `DetectNumberingWithWhitespaces` 옵션 `true` 에서 `TxtLoadOptions` 물체.

```csharp
TxtLoadOptions loadOptions = new TxtLoadOptions { DetectNumberingWithWhitespaces = true };
```

## 4단계: 문서 로드

이제 다음을 사용하여 문서를 로드해 보겠습니다. `TxtLoadOptions` 매개변수로 사용합니다. 이렇게 하면 네 번째 목록(공백 포함)이 올바르게 감지됩니다.

```csharp
Document doc = new Document(new MemoryStream(Encoding.UTF8.GetBytes(textDoc)), loadOptions);
```

## 5단계: 문서 저장

마지막으로, 문서를 지정한 디렉터리에 저장합니다. 그러면 목록이 올바르게 감지된 Word 문서가 출력됩니다.

```csharp
doc.Save(dataDir + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

## 결론

자, 이제 완성했습니다! Aspose.Words for .NET을 사용하여 몇 줄의 코드만으로 일반 텍스트 문서에서 공백이 포함된 번호 매기기를 감지하는 기술을 익혔습니다. 이 기능은 다양한 텍스트 형식을 처리하고 Word 문서에서 목록이 정확하게 표현되도록 할 때 매우 유용합니다. 다음에 까다로운 목록을 마주치게 되면 어떻게 해야 할지 정확히 알 수 있을 것입니다.

## 자주 묻는 질문

### 무엇인가요 `DetectNumberingWithWhitespaces` Aspose.Words에서 .NET을 사용할 수 있나요?
`DetectNumberingWithWhitespaces` 옵션입니다 `TxtLoadOptions` 이를 통해 Aspose.Words는 번호와 목록 항목 텍스트 사이에 공백이 있는 경우에도 목록을 인식할 수 있습니다.

### 이 기능을 글머리 기호나 대괄호와 같은 다른 구분 기호에도 사용할 수 있나요?
네, Aspose.Words는 글머리 기호나 대괄호와 같은 일반적인 구분 기호가 있는 목록을 자동으로 감지합니다. `DetectNumberingWithWhitespaces` 특히 공백이 있는 목록에 도움이 됩니다.

### 내가 사용하지 않으면 어떻게 되나요? `DetectNumberingWithWhitespaces`?
이 옵션이 없으면 번호와 텍스트 사이에 공백이 있는 목록은 목록으로 인식되지 않을 수 있으며, 해당 항목이 일반 문단으로 표시될 수 있습니다.

### 이 기능은 다른 Aspose 제품에서도 사용할 수 있나요?
이 특정 기능은 Word 문서 처리를 위해 설계된 Aspose.Words for .NET에 맞춰 제작되었습니다.

### Aspose.Words for .NET에 대한 임시 라이선스를 어떻게 얻을 수 있나요?
임시면허를 취득할 수 있습니다. [Aspose 임시 면허](https://purchase.aspose.com/temporary-license/) 페이지.




{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}