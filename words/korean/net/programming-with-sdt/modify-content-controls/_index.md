---
title: 콘텐츠 컨트롤 수정
linktitle: 콘텐츠 컨트롤 수정
second_title: Aspose.Words 문서 처리 API
description: Aspose.Words for .NET을 사용하여 Word에서 구조화된 문서 태그를 수정하는 방법을 알아보세요. 텍스트, 드롭다운 및 이미지를 단계별로 업데이트합니다.
weight: 10
url: /ko/net/programming-with-sdt/modify-content-controls/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 콘텐츠 컨트롤 수정

## 소개

Word 문서로 작업하고 Aspose.Words for .NET을 사용하여 일반 텍스트, 드롭다운 목록 또는 그림과 같은 구조화된 콘텐츠 컨트롤을 수정해야 했다면, 당신은 올바른 곳에 있습니다! 구조화된 문서 태그(SDT)는 문서 자동화를 더 쉽고 유연하게 만드는 강력한 도구입니다. 이 튜토리얼에서는 이러한 SDT를 필요에 맞게 수정하는 방법을 자세히 살펴보겠습니다. 텍스트를 업데이트하든, 드롭다운 선택을 변경하든, 이미지를 바꾸든, 이 가이드는 단계별로 프로세스를 안내합니다.

## 필수 조건

콘텐츠 컨트롤을 수정하는 구체적인 작업에 들어가기 전에 다음 사항이 있는지 확인하세요.

1.  .NET용 Aspose.Words 설치: Aspose.Words 라이브러리가 설치되어 있는지 확인하세요. 그렇지 않은 경우 다음을 수행할 수 있습니다.[여기서 다운로드하세요](https://releases.aspose.com/words/net/).

2. C#에 대한 기본 지식: 이 튜토리얼에서는 독자가 기본 C# 프로그래밍 개념에 익숙하다고 가정합니다.

3. .NET 개발 환경: .NET 애플리케이션을 실행하려면 Visual Studio와 같은 IDE가 설정되어 있어야 합니다.

4. 샘플 문서: 다양한 유형의 SDT가 있는 샘플 Word 문서를 사용합니다. 예제에서 하나를 사용하거나 직접 만들 수 있습니다.

5.  Aspose 문서에 대한 액세스: 자세한 내용은 다음을 확인하세요.[Aspose.Words 문서](https://reference.aspose.com/words/net/).

## 네임스페이스 가져오기

Aspose.Words 작업을 시작하려면 관련 네임스페이스를 C# 프로젝트로 가져와야 합니다. 방법은 다음과 같습니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

이러한 네임스페이스를 사용하면 Word 문서에서 구조화된 문서 태그를 조작하는 데 필요한 클래스와 메서드에 액세스할 수 있습니다.

## 1단계: 문서 경로 설정

 변경하기 전에 문서 경로를 지정해야 합니다. 바꾸기`"YOUR DOCUMENT DIRECTORY"` 문서가 저장된 실제 경로를 사용합니다.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Structured document tags.docx");
```

## 2단계: 구조화된 문서 태그 루프

 SDT를 수정하려면 먼저 문서의 모든 SDT를 반복해야 합니다. 이는 다음을 사용하여 수행됩니다.`GetChildNodes` 모든 유형의 노드를 가져오는 방법`StructuredDocumentTag`.

```csharp
foreach (StructuredDocumentTag sdt in doc.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
    // 유형에 따라 SDT 수정
}
```

## 3단계: 일반 텍스트 SDT 수정

SDT가 일반 텍스트 유형인 경우 해당 내용을 바꿀 수 있습니다. 먼저 기존 내용을 지운 다음 새 텍스트를 추가합니다.

```csharp
if (sdt.SdtType == SdtType.PlainText)
{
    sdt.RemoveAllChildren();
    Paragraph para = sdt.AppendChild(new Paragraph(doc)) as Paragraph;
    Run run = new Run(doc, "new text goes here");
    para.AppendChild(run);
}
```

 설명: 여기,`RemoveAllChildren()`SDT의 기존 콘텐츠를 지웁니다. 그런 다음 새`Paragraph` 그리고`Run` 새로운 텍스트를 삽입할 개체입니다.

## 4단계: 드롭다운 목록 SDT 수정

 드롭다운 목록 SDT의 경우 선택한 항목을 변경하려면 다음을 수행하세요.`ListItems` 컬렉션. 여기서, 우리는 목록에서 세 번째 항목을 선택합니다.

```csharp
if (sdt.SdtType == SdtType.DropDownList)
{
    SdtListItem secondItem = sdt.ListItems[2];
    sdt.ListItems.SelectedValue = secondItem;
}
```

설명: 이 코드 조각은 드롭다운 목록에서 인덱스 2(세 번째 항목)의 항목을 선택합니다. 필요에 따라 인덱스를 조정하세요.

## 5단계: 그림 SDT 수정

그림 SDT 내의 이미지를 업데이트하려면 기존 이미지를 새 이미지로 바꾸면 됩니다.

```csharp
if (sdt.SdtType == SdtType.Picture)
{
    Shape shape = (Shape) sdt.GetChild(NodeType.Shape, 0, true);
    if (shape.HasImage)
    {
        shape.ImageData.SetImage(ImagesDir + "Watermark.png");
    }
}
```

 설명: 이 코드는 모양에 이미지가 포함되어 있는지 확인한 다음 해당 이미지를 다음 위치에 있는 새 이미지로 바꿉니다.`ImagesDir`.

## 6단계: 수정된 문서 저장

필요한 모든 변경을 한 후 수정된 문서를 새 이름으로 저장하면 원본 문서가 그대로 유지됩니다.

```csharp
doc.Save(dataDir + "WorkingWithSdt.ModifyContentControls.docx");
```

설명: 이렇게 하면 문서가 새 파일 이름으로 저장되어 원본과 쉽게 구별할 수 있습니다.

## 결론

Aspose.Words for .NET을 사용하여 Word 문서의 콘텐츠 컨트롤을 수정하는 것은 관련 단계를 이해하면 간단합니다. 텍스트를 업데이트하든, 드롭다운 선택을 변경하든, 이미지를 바꾸든 Aspose.Words는 이러한 작업에 대한 강력한 API를 제공합니다. 이 튜토리얼을 따르면 문서의 구조화된 콘텐츠 컨트롤을 효과적으로 관리하고 사용자 정의하여 문서를 더욱 동적으로 만들고 필요에 맞게 조정할 수 있습니다.

## 자주 묻는 질문

1. 구조화된 문서 태그(SDT)란 무엇입니까?

SDT는 텍스트 상자, 드롭다운 목록, 그림 등 문서 콘텐츠를 관리하고 서식을 지정하는 데 도움이 되는 Word 문서의 요소입니다.

2. SDT에 새로운 드롭다운 항목을 추가하려면 어떻게 해야 하나요?

 새 항목을 추가하려면 다음을 사용하세요.`ListItems` 속성을 추가하고 새로 추가`SdtListItem` 컬렉션에 추가.

3. Aspose.Words를 사용하여 문서에서 SDT를 제거할 수 있나요?

네, 문서의 노드에 접근하여 원하는 SDT를 삭제하면 SDT를 제거할 수 있습니다.

4. 다른 요소 내에 중첩된 SDT를 어떻게 처리합니까?

 사용하세요`GetChildNodes` 중첩된 SDT에 접근하기 위한 적절한 매개변수를 갖춘 메서드.

5. 수정해야 하는 SDT가 문서에 보이지 않는 경우 어떻게 해야 합니까?

SDT가 숨겨지거나 보호되지 않았는지 확인하세요. 문서 설정을 확인하고 코드가 SDT 유형을 올바르게 타겟팅하고 있는지 확인하세요.


### .NET용 Aspose.Words를 사용하여 콘텐츠 컨트롤 수정을 위한 예제 소스 코드 

```csharp
// 문서 디렉토리 경로
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Structured document tags.docx");
foreach (StructuredDocumentTag sdt in doc.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
	switch (sdt.SdtType)
	{
		case SdtType.PlainText:
		{
			sdt.RemoveAllChildren();
			Paragraph para = sdt.AppendChild(new Paragraph(doc)) as Paragraph;
			Run run = new Run(doc, "new text goes here");
			para.AppendChild(run);
			break;
		}
		case SdtType.DropDownList:
		{
			SdtListItem secondItem = sdt.ListItems[2];
			sdt.ListItems.SelectedValue = secondItem;
			break;
		}
		case SdtType.Picture:
		{
			Shape shape = (Shape) sdt.GetChild(NodeType.Shape, 0, true);
			if (shape.HasImage)
			{
				shape.ImageData.SetImage(ImagesDir + "Watermark.png");
			}
			break;
		}
	}
}
doc.Save(dataDir + "WorkingWithSdt.ModifyContentControls.docx");

```

다 됐어요! Aspose.Words for .NET을 사용하여 Word 문서에서 다양한 유형의 콘텐츠 컨트롤을 성공적으로 수정했습니다.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
