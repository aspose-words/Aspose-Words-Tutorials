---
title: PDF 문서에 하위 집합 글꼴 포함
linktitle: PDF 문서에 하위 집합 글꼴 포함
second_title: Aspose.Words 문서 처리 API
description: Aspose.Words for .NET을 사용하여 필요한 글꼴 하위 집합만 임베드하여 PDF 파일 크기를 줄이세요. 단계별 가이드를 따라 PDF를 효율적으로 최적화하세요.
weight: 10
url: /ko/net/programming-with-pdfsaveoptions/embedded-subset-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# PDF 문서에 하위 집합 글꼴 포함

## 소개

비슷한 내용을 포함하고 있어도 일부 PDF 파일이 다른 파일보다 훨씬 큰 것을 알아차린 적이 있습니까? 원인은 종종 글꼴에 있습니다. PDF에 글꼴을 포함하면 모든 기기에서 동일하게 보이지만 파일 크기가 커질 수도 있습니다. 다행히도 Aspose.Words for .NET은 필요한 글꼴 하위 집합만 포함하는 편리한 기능을 제공하여 PDF를 간결하고 효율적으로 유지합니다. 이 튜토리얼은 단계별로 프로세스를 안내합니다.

## 필수 조건

시작하기 전에 다음 사항이 있는지 확인하세요.

-  .NET용 Aspose.Words: 다운로드할 수 있습니다.[여기](https://releases.aspose.com/words/net/).
- .NET 환경: 작동하는 .NET 개발 환경이 있는지 확인하세요.
- C#에 대한 기본 지식: C# 프로그래밍에 익숙하면 따라하는 데 도움이 됩니다.

## 네임스페이스 가져오기

Aspose.Words for .NET을 사용하려면 프로젝트에 필요한 네임스페이스를 가져와야 합니다. C# 파일 맨 위에 다음을 추가합니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## 1단계: 문서 로드

 먼저 PDF로 변환하려는 Word 문서를 로드해야 합니다. 이는 다음을 사용하여 수행됩니다.`Document` Aspose.Words가 제공하는 클래스입니다.

```csharp
// 문서 디렉토리의 경로입니다.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

 이 코드 조각은 다음 위치에 있는 문서를 로드합니다.`dataDir` . 교체를 꼭 하세요`"YOUR DOCUMENT DIRECTORY"` 문서의 실제 경로를 입력합니다.

## 2단계: PDF 저장 옵션 구성

 다음으로, 우리는 다음을 구성합니다.`PdfSaveOptions` 필요한 글꼴 하위 집합만 포함되도록 합니다. 설정하여`EmbedFullFonts` 에게`false`, Aspose.Words에게 문서에서 사용된 문자만 포함하라고 말합니다.

```csharp
// 출력 PDF에는 문서에 있는 글꼴의 하위 집합이 포함됩니다.
// PDF 글꼴에는 문서에 사용된 문자만 포함됩니다.
PdfSaveOptions saveOptions = new PdfSaveOptions { EmbedFullFonts = false };
```

이 작지만 중요한 단계는 PDF 파일 크기를 크게 줄이는 데 도움이 됩니다.

## 3단계: 문서를 PDF로 저장

 마지막으로 다음을 사용하여 문서를 PDF로 저장합니다.`Save` 방법, 구성된 것을 적용`PdfSaveOptions`.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.EmbedSubsetFonts.pdf", saveOptions);
```

 이 코드는 다음 이름의 PDF 파일을 생성합니다.`WorkingWithPdfSaveOptions.EmbedSubsetFonts.pdf` 지정된 디렉토리에 필요한 글꼴 하위 집합만 포함됩니다.

## 결론

이제 알겠습니다! 이 간단한 단계를 따르면 Aspose.Words for .NET을 사용하여 필요한 글꼴 하위 집합만 임베드하여 PDF 파일의 크기를 효율적으로 줄일 수 있습니다. 이렇게 하면 저장 공간을 절약할 수 있을 뿐만 아니라 로드 시간이 더 빠르고 성능이 더 좋아집니다. 특히 글꼴이 많은 문서의 경우 더욱 그렇습니다.

## 자주 묻는 질문

### PDF에 글꼴 하위 세트만 포함해야 하는 이유는 무엇입니까?
필요한 글꼴 하위 집합만 포함하면 문서의 모양과 가독성을 손상시키지 않고도 PDF 파일 크기를 크게 줄일 수 있습니다.

### 필요한 경우 전체 글꼴을 내장하도록 되돌릴 수 있나요?
 네, 가능합니다. 간단히 설정하세요.`EmbedFullFonts`재산에`true` 에서`PdfSaveOptions`.

### Aspose.Words for .NET은 다른 PDF 최적화 기능을 지원합니까?
물론입니다! Aspose.Words for .NET은 이미지 압축 및 사용하지 않는 객체 제거를 포함하여 PDF를 최적화하기 위한 다양한 옵션을 제공합니다.

### Aspose.Words for .NET을 사용하여 어떤 유형의 글꼴을 하위 집합으로 포함할 수 있습니까?
.NET용 Aspose.Words는 문서에 사용된 모든 TrueType 글꼴에 대한 하위 집합 포함을 지원합니다.

### 내 PDF에 어떤 글꼴이 포함되어 있는지 어떻게 확인할 수 있나요?
Adobe Acrobat Reader에서 PDF를 열고 [글꼴] 탭에서 속성을 확인하여 포함된 글꼴을 확인할 수 있습니다.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
