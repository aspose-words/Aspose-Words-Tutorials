---
title: 공백을 포함한 번호 매기기 감지
linktitle: 공백을 포함한 번호 매기기 감지
second_title: Aspose.Words 문서 처리 API
description: Aspose.Words for .NET을 사용하여 일반 텍스트 문서에서 공백이 포함된 번호 매기기를 감지하고 목록이 올바르게 인식되는지 확인하는 방법을 알아보세요.
weight: 10
url: /ko/net/programming-with-txtloadoptions/detect-numbering-with-whitespaces/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 공백을 포함한 번호 매기기 감지

## 소개

.NET 애호가를 위한 Aspose.Words! 오늘은 일반 텍스트 문서에서 목록을 처리하는 것을 쉽게 만들어 줄 수 있는 흥미로운 기능에 대해 알아보겠습니다. 일부 줄이 목록이어야 하는 텍스트 파일을 처리한 적이 있습니까? Word 문서에 로드하면 제대로 보이지 않습니까? 글쎄요, 우리는 멋진 트릭을 가지고 있습니다. 공백이 있는 번호 매기기를 감지하는 것입니다. 이 튜토리얼에서는 다음을 사용하는 방법을 안내합니다.`DetectNumberingWithWhitespaces` .NET용 Aspose.Words의 옵션을 사용하면 숫자와 텍스트 사이에 공백이 있는 경우에도 목록이 올바르게 인식되도록 할 수 있습니다.

## 필수 조건

시작하기 전에 다음 사항이 있는지 확인하세요.

-  .NET용 Aspose.Words: 여기에서 다운로드할 수 있습니다.[Aspose 릴리스](https://releases.aspose.com/words/net/) 페이지.
- 개발 환경: Visual Studio 또는 기타 C# IDE.
- .NET Framework가 컴퓨터에 설치되어 있어야 합니다.
- C#에 대한 기본 지식: 기본 사항을 이해하면 예제를 따라가는 데 도움이 됩니다.

## 네임스페이스 가져오기

코드로 넘어가기 전에 프로젝트에 필요한 네임스페이스를 가져왔는지 확인하세요. 시작하기 위한 간단한 스니펫은 다음과 같습니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;
```

프로세스를 간단하고 관리하기 쉬운 단계로 나누어 보겠습니다. 각 단계에서 필요한 코드를 안내하고 무슨 일이 일어나고 있는지 설명합니다.

## 1단계: 문서 디렉토리 정의

우선, 문서 디렉토리 경로를 설정해 보겠습니다. 여기에 입력 및 출력 파일이 저장됩니다.

```csharp
// 문서 디렉토리 경로
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 2단계: 일반 텍스트 문서 만들기

다음으로, 문자열로 일반 텍스트 문서를 만들 것입니다. 이 문서에는 목록으로 해석될 수 있는 부분이 포함됩니다.

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

 공백이 포함된 번호 매기기를 감지하려면 다음을 설정해야 합니다.`DetectNumberingWithWhitespaces` 옵션`true` 에서`TxtLoadOptions` 물체.

```csharp
TxtLoadOptions loadOptions = new TxtLoadOptions { DetectNumberingWithWhitespaces = true };
```

## 4단계: 문서 로드

 이제 다음을 사용하여 문서를 로드해 보겠습니다.`TxtLoadOptions` 매개변수로. 이렇게 하면 네 번째 목록(공백 포함)이 올바르게 감지됩니다.

```csharp
Document doc = new Document(new MemoryStream(Encoding.UTF8.GetBytes(textDoc)), loadOptions);
```

## 5단계: 문서 저장

마지막으로, 문서를 지정된 디렉토리에 저장합니다. 그러면 올바르게 감지된 목록이 있는 Word 문서가 출력됩니다.

```csharp
doc.Save(dataDir + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

## 결론

이제 다 됐습니다! 몇 줄의 코드만 있으면 Aspose.Words for .NET을 사용하여 일반 텍스트 문서에서 공백이 있는 번호 매기기를 감지하는 기술을 익혔습니다. 이 기능은 다양한 텍스트 형식을 처리하고 Word 문서에서 목록이 정확하게 표현되도록 할 때 매우 유용할 수 있습니다. 따라서 다음에 까다로운 목록을 마주치면 정확히 무엇을 해야 할지 알게 될 것입니다.

## 자주 묻는 질문

###  무엇인가요`DetectNumberingWithWhitespaces` in Aspose.Words for .NET?
`DetectNumberingWithWhitespaces` 옵션입니다`TxtLoadOptions` 이를 통해 Aspose.Words는 번호와 목록 항목 텍스트 사이에 공백이 있더라도 목록을 인식할 수 있습니다.

### 이 기능을 글머리 기호나 대괄호 같은 다른 구분 기호에도 사용할 수 있나요?
 네, Aspose.Words는 글머리 기호와 대괄호와 같은 일반적인 구분 기호가 있는 목록을 자동으로 감지합니다.`DetectNumberingWithWhitespaces` 특히 공백이 있는 목록에 도움이 됩니다.

###  사용하지 않으면 어떻게 되나요?`DetectNumberingWithWhitespaces`?
이 옵션이 없으면 번호와 텍스트 사이에 공백이 있는 목록은 목록으로 인식되지 않을 수 있으며, 해당 항목이 일반 문단으로 표시될 수 있습니다.

### 이 기능은 다른 Aspose 제품에서도 사용할 수 있나요?
이 특정 기능은 Word 문서 처리를 위해 설계된 Aspose.Words for .NET에 맞춰 제작되었습니다.

### Aspose.Words for .NET에 대한 임시 라이선스를 어떻게 받을 수 있나요?
 임시면허는 다음에서 받을 수 있습니다.[임시 라이센스를 Aspose](https://purchase.aspose.com/temporary-license/) 페이지.


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
