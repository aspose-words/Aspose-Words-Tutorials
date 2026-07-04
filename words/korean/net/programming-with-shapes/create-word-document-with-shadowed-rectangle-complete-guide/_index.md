---
category: general
date: 2026-04-21
description: 스타일이 적용된 사각형과 그림자가 포함된 워드 문서를 만들세요. C#에서 그림자를 추가하고, 사각형 도형을 삽입하며, 그림자
  색상을 설정하는 방법 등을 배워보세요.
draft: false
keywords:
- create word document
- how to add shadow
- insert rectangle shape
- create rectangle in word
- set shadow color
language: ko
og_description: C#에서 워드 문서를 만들고 그림자 사각형 도형을 추가하세요. 이 가이드를 따라 그림자 색상, 블러 및 오프셋을 쉽게
  설정할 수 있습니다.
og_title: 그림자 사각형이 있는 워드 문서 만들기 – 단계별
tags:
- Aspose.Words
- C#
- Document Automation
title: 그림자 사각형이 포함된 워드 문서 만들기 – 완전 가이드
url: /ko/net/programming-with-shapes/create-word-document-with-shadowed-rectangle-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 그림자 사각형이 있는 Word 문서 만들기 – 완전 가이드

평범한 텍스트 페이지보다 조금 더 깔끔하게 보이는 **Word 문서 만들기**가 필요하셨나요? 보고서 템플릿이나 전단지를 만들 때, 은은한 그림자가 있는 간단한 사각형만 있으면 충분할 때가 있습니다. 이 튜토리얼에서는 사각형 도형을 삽입하고, 그림자를 켜고, 색상·흐림·오프셋을 커스터마이징하는 과정을 C#과 Aspose.Words를 사용해 단계별로 안내합니다.

또한 **그림자 추가 방법**을 Word 2016, 2019, 최신 Office 365 빌드 모두에서 동작하도록 설명합니다. 최종적으로는 그림자가 적용된 사각형을 포함한 *.docx* 파일을 저장할 수 있게 되며, 각 속성을 설정하는 이유도 이해하게 됩니다.

## 전제 조건

- .NET 6 (또는 최신 .NET Framework 버전)  
- Aspose.Words for .NET NuGet 패키지 (`Install-Package Aspose.Words`)  
- C# 문법에 대한 기본적인 이해  
- Visual Studio 같은 IDE (다른 편집기라도 무방)

추가 라이브러리는 필요하지 않으며, 모든 기능은 Aspose.Words 안에 포함되어 있습니다.

## 1단계 – 문서와 Builder 초기화 (Create Word Document)

프로그램matically **Word 문서 만들기**는 `Document` 클래스로 시작합니다. `DocumentBuilder`는 페인트 브러시와 같으며, 텍스트·도형·기타 요소를 추가할 수 있게 해줍니다.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowRectangleDemo
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

*왜 중요한가:* `Document` 객체는 전체 .docx 파일을 나타냅니다. 이 객체가 없으면 사각형이나 그림자를 붙일 위치가 없습니다.

## 2단계 – 사각형 도형 삽입 (Insert Rectangle Shape)

이제 실제로 **사각형 도형 삽입**을 합니다. `InsertShape` 메서드는 `ShapeType` 열거형과 너비·높이를 포인트 단위로 받습니다.

```csharp
        // Step 2: Insert a rectangle shape of the desired size (200x100 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

*팁:* 1 포인트는 ≈ 1/72 인치이므로, 200 pts는 대략 2.78 인치 폭에 해당합니다. 레이아웃에 맞게 값을 조정하세요.

## 3단계 – 그림자 활성화 (How to Add Shadow)

그림자는 기본적으로 비활성화되어 있습니다. `Visible` 플래그를 켜서 활성화합니다.

```csharp
        // Step 3: Turn on the shadow for the shape
        rectangle.ShadowFormat.Visible = true;
```

*무슨 일이 일어나나요?* `Visible`이 `true`이면, Word는 다음에 설정할 다른 속성을 기반으로 드롭‑쉐도우를 렌더링합니다.

## 4단계 – 그림자 모양 커스터마이징 (Set Shadow Color, Blur, Offsets)

여기서 **그림자 색상**, 흐림 반경, X/Y 오프셋을 **설정**합니다. 다양한 값을 실험해 보세요—부드러운 빛, 깊은 드롭, 혹은 “떠 있는” 효과를 만들 수 있습니다.

```csharp
        // Step 4: Define the shadow appearance – colour, blur radius and offsets
        rectangle.ShadowFormat.Color = Color.Gray;   // shadow colour
        rectangle.ShadowFormat.Blur = 5.0;           // blur radius (points)
        rectangle.ShadowFormat.OffsetX = 4.0;        // horizontal offset (points)
        rectangle.ShadowFormat.OffsetY = 4.0;        // vertical offset (points)
```

*왜 이런 숫자인가?* 흐림 5 pts는 부드러운 가장자리를 제공하고, 오프셋 4 pts는 그림자를 오른쪽 아래로 이동시켜 왼쪽 위에서 빛이 오는 듯한 효과를 냅니다. `Color`를 `Color.Black`으로 바꾸면 대비가 강해지고, `Color.FromArgb(128, 0, 0, 0)`을 사용하면 반투명 검은색이 됩니다.

### 엣지 케이스 및 변형

- **흐림 없음:** `Blur = 0`으로 설정하면 선명하고 날카로운 그림자가 됩니다.  
- **음수 오프셋:** `OffsetX = -4`로 설정하면 그림자를 왼쪽으로 이동시킵니다.  
- **다른 도형:** 동일한 그림자 속성은 원, 삼각형, 자유형 도형에도 적용됩니다—단지 2단계에서 `ShapeType`만 바꾸면 됩니다.  
- **호환성:** Aspose.Words는 그림자 데이터를 Office Open XML 형식으로 기록하므로 Word 2010‑2021 및 Office 365에서 모두 동작합니다.

## 5단계 – 문서 저장 (Create Word Document)

마지막으로 파일을 디스크에 저장합니다. 지원되는 형식(`.docx`, `.pdf`, `.odt`, …) 중 원하는 것을 선택할 수 있지만, 이 가이드에서는 클래식 Word 형식인 `.docx`를 사용합니다.

```csharp
        // Step 5: Save the document with the shaped shadow
        document.Save("ShadowRectangle.docx");
    }
}
```

**ShadowRectangle.docx**를 Microsoft Word에서 열면, 회색 사각형에 오른쪽 아래로 약간 흐린 그림자가 적용된 모습을 확인할 수 있습니다—우리가 코딩한 그대로입니다.

### 기대 출력

- 한 페이지짜리 *.docx* 파일.  
- `InsertShape` 호출 시 커서 위치에 중심을 잡은 200 pt × 100 pt 사각형.  
- 오른쪽 4 pts, 아래쪽 4 pts 오프셋에 5 pt 흐림이 적용된 회색 그림자.

도형이 중앙에 맞지 않으면 `builder.MoveTo`로 커서를 이동하거나, 삽입 후 도형의 `Left`와 `Top` 속성을 조정하면 됩니다.

## 자주 묻는 질문 및 문제 해결

**Q: Word에서 그림자가 보이지 않아요.**  
A: `ShadowFormat.Visible`이 `true`인지 확인하세요. 또한 최신 버전의 Aspose.Words를 사용하고 있는지도 점검하세요(그림자 기능은 버전 20.3부터 추가됨).

**Q: 그림자에 그라데이션을 적용할 수 있나요?**  
A: `ShadowFormat`만으로는 직접 적용할 수 없습니다. Word UI에서는 그라데이션 그림자를 지원하지만, Open XML 스키마(및 Aspose.Words)가 제공하는 것은 단색 그림자뿐입니다. XML을 직접 편집해야 하는 고급 시나리오입니다.

**Q: 투명한 사각형에 그림자만 적용하고 싶어요.**  
A: 삽입 후 `rectangle.FillColor = Color.Transparent;`로 설정하면 됩니다. 그림자는 채우기와 무관하게 렌더링됩니다.

## 프로덕션 코드용 팁

- **Builder 재사용:** 여러 도형을 추가한다면 같은 `DocumentBuilder` 인스턴스를 유지하세요—도형마다 새 Builder를 만들면 불필요한 오버헤드가 발생합니다.  
- **배치 저장:** 모든 수정이 끝난 뒤 한 번만 저장하세요. 빈번한 I/O는 대용량 문서 생성 속도를 저하시킵니다.  
- **예외 처리:** 전체 블록을 `try / catch`로 감싸고 `Aspose.Words` 예외를 로깅하세요. 템플릿이 손상된 경우 라인 번호 등 유용한 정보를 제공합니다.

## 다음 단계 (Related Topics)

- **그림자 추가**를 사진이나 텍스트 상자에 적용하기(`ShadowFormat` 활용).  
- **표 셀 안에 사각형 삽입**하여 맞춤 셀 스타일링하기.  
- **Word에서 사각형 만들기**를 원시 Open XML로 직접 구현하기(원시 XML 선호자용).  
- **그림자 색상 동적 설정**을 사용자 입력이나 테마 색에 따라 적용하기.

다양한 색상, 흐림 반경, 오프셋을 실험해 보세요—기업 보고서에는 부드러운 파란색 빛, 드라마틱한 전단지에는 짙은 검은 그림자 등 무한한 가능성이 있습니다. 코드 변경은 최소에 불과합니다.

---

### 빠른 요약

- 우리는 **Word 문서 만들기**를 처음부터 수행했습니다.  
- **사각형 도형 삽입** 후 그림자를 켰습니다.  
- **그림자 색상**, 흐림, 오프셋을 설정해 전문적인 외관을 구현했습니다.  
- 파일을 저장해 배포 준비를 마쳤습니다.

이제 Word 자동화 프로젝트에 시각적 멋을 더할 탄탄한 기반을 갖추었습니다. 더 좋은 아이디어가 있나요? 댓글로 남겨 주세요. 계속 이야기를 나눠요. Happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}