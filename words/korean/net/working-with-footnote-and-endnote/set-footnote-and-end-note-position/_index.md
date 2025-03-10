---
title: 각주 및 미주 위치 설정
linktitle: 각주 및 끝주 위치 설정
second_title: Aspose.Words 문서 처리 API
description: 이 자세한 단계별 가이드를 통해 Aspose.Words for .NET을 사용하여 Word 문서에서 각주와 미주 위치를 설정하는 방법을 알아보세요.
weight: 10
url: /ko/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 각주 및 미주 위치 설정

## 소개

Word 문서로 작업하고 각주와 미주를 효과적으로 관리해야 하는 경우 Aspose.Words for .NET이 바로 그 라이브러리입니다. 이 튜토리얼은 Aspose.Words for .NET을 사용하여 Word 문서에서 각주와 미주 위치를 설정하는 방법을 안내합니다. 각 단계를 나누어 쉽게 따라하고 구현할 수 있도록 하겠습니다.

## 필수 조건

튜토리얼을 시작하기 전에 다음 사항이 있는지 확인하세요.

-  Aspose.Words for .NET 라이브러리: 여기에서 다운로드할 수 있습니다.[여기](https://releases.aspose.com/words/net/).
- Visual Studio: 최신 버전이라면 무엇이든 잘 작동합니다.
- C#에 대한 기본 지식: 기본 사항을 이해하면 쉽게 따라갈 수 있습니다.

## 네임스페이스 가져오기

먼저, C# 프로젝트에 필요한 네임스페이스를 가져옵니다.

```csharp
using System;
using Aspose.Words;
```

## 1단계: Word 문서 로드

시작하려면 Aspose.Words Document 객체에 Word 문서를 로드해야 합니다. 그러면 문서의 내용을 조작할 수 있습니다.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

이 코드에서 다음을 바꾸세요.`"YOUR DOCUMENT DIRECTORY"` 문서가 위치한 실제 경로를 사용합니다.

## 2단계: 각주 위치 설정

다음으로, 각주의 위치를 설정합니다. Aspose.Words for .NET을 사용하면 각주를 페이지 하단이나 텍스트 아래에 배치할 수 있습니다.

```csharp
doc.FootnoteOptions.Position = FootnotePosition.BeneathText;
```

 여기서, 우리는 각주가 텍스트 아래에 나타나도록 설정했습니다. 페이지 하단에 표시되도록 하려면 다음을 사용하세요.`FootnotePosition.BottomOfPage`.

## 3단계: 각주 위치 설정

마찬가지로, 각주의 위치를 설정할 수 있습니다. 각주는 섹션의 끝이나 문서의 끝에 위치할 수 있습니다.

```csharp
doc.EndnoteOptions.Position = EndnotePosition.EndOfSection;
```

 이 예에서 각주는 각 섹션의 끝에 배치됩니다. 문서의 끝에 배치하려면 다음을 사용합니다.`EndnotePosition.EndOfDocument`.

## 4단계: 문서 저장

마지막으로 문서를 저장하여 변경 사항을 적용합니다. 출력 문서에 대한 올바른 파일 경로와 이름을 지정해야 합니다.

```csharp
doc.Save(dataDir + "WorkingWithFootnotes.SetFootnoteAndEndNotePosition.docx");
```

이 줄은 수정된 문서를 지정된 디렉토리에 저장합니다.

## 결론

Aspose.Words for .NET을 사용하여 Word 문서에서 각주와 미주 위치를 설정하는 것은 단계를 알고 나면 간단합니다. 이 가이드를 따르면 필요에 맞게 문서를 사용자 지정하여 각주와 미주가 원하는 위치에 정확히 배치되도록 할 수 있습니다.

## 자주 묻는 질문

### 각주나 미주 각각에 대해 다른 위치를 설정할 수 있나요?

아니요, Aspose.Words for .NET은 문서의 모든 각주와 미주의 위치를 동일하게 설정합니다.

### Aspose.Words for .NET은 모든 버전의 Word 문서와 호환됩니까?

네, Aspose.Words for .NET은 DOC, DOCX, RTF 등 다양한 Word 문서 형식을 지원합니다.

### Aspose.Words for .NET을 다른 프로그래밍 언어와 함께 사용할 수 있나요?

Aspose.Words for .NET은 .NET 애플리케이션용으로 설계되었지만 C#, VB.NET 등 .NET을 지원하는 모든 언어와 함께 사용할 수 있습니다.

### Aspose.Words for .NET에 대한 무료 평가판이 있나요?

 네, 무료 체험판을 받으실 수 있습니다.[여기](https://releases.aspose.com/).

### Aspose.Words for .NET에 대한 더 자세한 문서는 어디에서 찾을 수 있나요?

 자세한 문서가 제공됩니다.[여기](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
