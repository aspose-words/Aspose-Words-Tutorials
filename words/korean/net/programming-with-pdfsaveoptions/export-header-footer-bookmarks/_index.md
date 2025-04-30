---
"description": "Aspose.Words for .NET을 사용하여 Word 문서에서 머리글과 바닥글 북마크를 PDF로 내보내는 방법을 단계별 가이드를 통해 알아보세요."
"linktitle": "Word 문서 머리글, 바닥글, 북마크를 PDF 문서로 내보내기"
"second_title": "Aspose.Words 문서 처리 API"
"title": "Word 문서 머리글, 바닥글, 북마크를 PDF 문서로 내보내기"
"url": "/ko/net/programming-with-pdfsaveoptions/export-header-footer-bookmarks/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Word 문서 머리글, 바닥글, 북마크를 PDF 문서로 내보내기

## 소개

Word 문서를 PDF로 변환하는 것은 일반적인 작업이며, 특히 서식을 유지하면서 문서를 공유하거나 보관하려는 경우 더욱 그렇습니다. 이러한 문서의 머리글과 바닥글에 중요한 북마크가 포함되어 있는 경우가 있습니다. 이 튜토리얼에서는 Aspose.Words for .NET을 사용하여 Word 문서의 북마크를 PDF로 내보내는 과정을 살펴보겠습니다.

## 필수 조건

자세히 알아보기 전에 다음 사항이 있는지 확인하세요.

- Aspose.Words for .NET: Aspose.Words for .NET이 설치되어 있어야 합니다. 다음에서 다운로드할 수 있습니다. [여기](https://releases.aspose.com/words/net/).
- 개발 환경: 개발 환경을 설정하세요. Visual Studio 또는 기타 .NET 호환 IDE를 사용할 수 있습니다.
- C#에 대한 기본 지식: 코드 예제를 따라가려면 C# 프로그래밍에 대한 지식이 필요합니다.

## 네임스페이스 가져오기

먼저, C# 프로젝트에 필요한 네임스페이스를 가져와야 합니다. 코드 파일 맨 위에 다음 줄을 추가합니다.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

이 과정을 쉽게 따를 수 있는 단계로 나누어 보겠습니다.

## 1단계: 문서 초기화

첫 번째 단계는 Word 문서를 불러오는 것입니다. 방법은 다음과 같습니다.

```csharp
// 문서 디렉토리의 경로입니다.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks in headers and footers.docx");
```

이 단계에서는 문서 디렉터리 경로를 지정하고 Word 문서를 로드하기만 하면 됩니다.

## 2단계: PDF 저장 옵션 구성

다음으로, 머리글과 바닥글의 책갈피가 올바르게 내보내지도록 PDF 저장 옵션을 구성해야 합니다.

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.OutlineOptions.DefaultBookmarksOutlineLevel = 1;
saveOptions.HeaderFooterBookmarksExportMode = HeaderFooterBookmarksExportMode.First;
```

여기서 우리는 다음을 설정하고 있습니다. `PdfSaveOptions`. 그 `DefaultBookmarksOutlineLevel` 속성은 북마크의 개요 수준을 설정합니다. `HeaderFooterBookmarksExportMode` 이 속성은 헤더와 푸터에서 처음 나타나는 북마크만 내보내도록 보장합니다.

## 3단계: 문서를 PDF로 저장

마지막으로, 구성된 옵션을 사용하여 문서를 PDF로 저장합니다.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.ExportHeaderFooterBookmarks.pdf", saveOptions);
```

이 단계에서는 귀하가 구성한 옵션을 사용하여 지정된 경로에 문서를 저장합니다.

## 결론

자, 이제 완료되었습니다! 다음 단계를 따라 Aspose.Words for .NET을 사용하여 Word 문서의 머리글과 바닥글에 있는 북마크를 PDF로 쉽게 내보낼 수 있습니다. 이 방법을 사용하면 문서 내 중요한 탐색 도구가 PDF 형식으로 유지되어 사용자가 문서를 더 쉽게 탐색할 수 있습니다.

## 자주 묻는 질문

### Word 문서의 모든 책갈피를 PDF로 내보낼 수 있나요?

네, 가능합니다. `PdfSaveOptions`필요한 경우 모든 북마크를 포함하도록 설정을 조정할 수 있습니다.

### 문서 본문에서도 북마크를 내보내고 싶다면 어떻게 해야 하나요?

구성할 수 있습니다 `Outl~에eOptions` in `PdfSaveOptions` 문서 본문에서 북마크를 포함합니다.

### PDF에서 책갈피 수준을 사용자 정의할 수 있나요?

물론입니다! 사용자 정의가 가능합니다. `DefaultBookmarksOutlineLevel` 북마크에 대해 다양한 개요 수준을 설정하는 속성입니다.

### 북마크가 없는 문서는 어떻게 처리하나요?

문서에 북마크가 없으면 PDF는 북마크 윤곽선 없이 생성됩니다. PDF에 북마크가 필요한 경우 문서에 북마크가 포함되어 있는지 확인하세요.

### DOCX나 RTF 등 다른 문서 유형에도 이 방법을 사용할 수 있나요?

네, Aspose.Words for .NET은 DOCX, RTF 등 다양한 문서 유형을 지원합니다.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}