---
category: general
date: 2026-09-30
description: Word에서 C#으로 도형 그룹화 – 도형을 그룹화하고, 사각형 및 타원을 추가하며, 프로그래밍으로 Word 문서에 사각형
  도형을 삽입하는 방법을 배웁니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- how to group shapes
- how to add rectangle
- how to add ellipse
- insert rectangle shape word
language: ko
lastmod: 2026-09-30
og_description: C#와 Aspose.Words를 사용하여 Word에서 도형을 그룹화합니다. 사각형 추가, 타원 추가 방법을 따라하고 도형을
  효율적으로 그룹화하는 방법을 배워보세요.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  shape
og_title: C#로 Word에서 도형 그룹화 – 단계별 가이드
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: group shapes in Word with C# – learn how to group shapes, add rectangle
    and ellipse, and insert rectangle shape Word documents programmatically.
  headline: How to group shapes in Word using C# and Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: C#와 Aspose.Words를 사용하여 Word에서 도형을 그룹화하는 방법
url: /ko/net/programming-with-shapes/how-to-group-shapes-in-word-using-c-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#와 Aspose.Words를 사용하여 Word에서 도형을 그룹화하는 방법

프로그램matically **group shapes in Word** 해야 한다면, 이 가이드는 정확히 어떻게 하는지 보여줍니다. 사각형을 추가하고, 타원을 추가한 다음, .NET용 Aspose.Words 라이브러리를 사용하여 단일 그룹 도형으로 결합하는 방법을 확인할 수 있습니다.

도형을 다루는 것은 보고서, 계약서 또는 마케팅 자료를 자동으로 생성할 때 흔히 요구되는 작업입니다. 이 튜토리얼을 마치면 DOCX 파일을 로드하고, 사각형과 타원을 삽입하고, 이를 그룹화한 뒤 결과를 저장하는 재사용 가능한 C# 메서드를 갖게 됩니다—Word를 직접 열 필요 없이 모두 수행됩니다.

## 사전 요구 사항

시작하기 전에 다음이 설치되어 있는지 확인하세요:

* .NET 6.0 SDK 또는 그 이후 버전이 설치됨  
* Visual Studio 2022와 같은 개발 환경 (Community 에디션도 사용 가능)  
* Aspose.Words for .NET 라이선스 또는 무료 평가판 복사본 (라이선스 없이도 API는 동작하지만 워터마크가 추가됩니다)  

또한 코드에서 참조할 수 있는 폴더에 소스 Word 문서(`input.docx`)가 있어야 합니다. 문서는 비어 있어도 무방합니다; 이 튜토리얼은 도형 처리에 초점을 맞춥니다.

## Step 1: 새 콘솔 프로젝트 생성 및 Aspose.Words 추가

터미널이나 Visual Studio 명령 프롬프트를 열고 다음을 실행합니다:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

이 명령은 **WordShapeDemo**라는 새 콘솔 애플리케이션을 만들고, Word 파일을 조작하는 데 사용되는 `Document`와 `DocumentBuilder` 클래스를 포함하는 `Aspose.Words` NuGet 패키지를 추가합니다.

## Step 2: 문서 로드 또는 생성

**group shapes in Word** 작업을 시작할 때 첫 번째 작업은 `Document` 객체를 얻는 것입니다. 기존 DOCX 파일을 로드하거나 빈 문서에서 시작할 수 있습니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Load an existing document (replace the path with your own)
        Document document = new Document(@"YOUR_DIRECTORY\input.docx");

        // If you prefer a brand‑new document, uncomment the next line:
        // Document document = new Document();
```

`Document` 클래스는 전체 Word 파일을 나타냅니다. 파일을 로드하면 도형을 삽입할 준비가 된 캔버스를 얻게 됩니다.

## Step 3: 그룹 도형 시작

*그룹 도형*은 여러 개의 독립적인 도형을 하나의 단위로 취급하게 해 주어, 함께 이동하거나 크기를 조정할 때 편리합니다. 그룹을 시작하려면 `DocumentBuilder`에서 `StartGroupShape()`를 호출합니다.

```csharp
        // Create a builder to edit the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Begin a group shape that will contain multiple shapes
        builder.StartGroupShape();
```

`StartGroupShape`를 호출하면 이후 삽입되는 모든 도형이 동일한 논리적 그룹에 속하게 되며, `EndGroupShape`를 호출할 때까지 그룹에 포함됩니다.

## Step 4: Word에서 사각형 도형 추가 방법

그룹이 열려 있으므로 이제 사각형을 삽입합니다. `InsertShape` 메서드는 `ShapeType` 열거형을 첫 번째 인수로 받고, 이어서 너비와 높이(포인트 단위)를 받습니다.

```csharp
        // Add a rectangle shape to the group (100 pt wide, 50 pt high)
        builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

사각형은 그룹의 첫 번째 멤버가 됩니다. 필요에 따라 채우기, 외곽선 또는 텍스트를 나중에 커스터마이즈할 수 있습니다.

## Step 5: Word에서 타원 도형 추가 방법

다음으로 타원을 추가합니다(너비와 높이가 같으면 원이 됩니다). 동일한 `DocumentBuilder`를 사용하여 **how to add ellipse**를 시연합니다.

```csharp
        // Add an ellipse shape to the same group (80 pt wide, 80 pt high)
        builder.InsertShape(ShapeType.Ellipse, 80, 80);
```

두 도형은 이제 그룹 내부의 동일 좌표 공간을 공유하므로 시각적으로 정렬하기가 쉽습니다.

## Step 6: 그룹 도형 정의 닫기

원하는 모든 멤버를 추가했으면 그룹을 닫습니다. 이렇게 하면 Word가 이 도형들을 하나의 객체로 취급하도록 컬렉션이 최종 확정됩니다.

```csharp
        // End the group shape definition
        builder.EndGroupShape();
```

이 시점에서 문서에는 사각형과 타원으로 구성된 단일 그룹 도형이 포함됩니다.

## Step 7: 수정된 문서 저장

마지막으로 변경 사항을 디스크에 기록합니다. 원본 파일을 덮어쓰거나 새 파일을 만들 수 있습니다.

```csharp
        // Save the document with the grouped shapes
        document.Save(@"YOUR_DIRECTORY\output.docx");

        Console.WriteLine("Document saved with grouped shapes.");
    }
}
```

프로그램을 실행하면 `output.docx`가 생성됩니다. Microsoft Word에서 파일을 열고 도형을 선택하면 사각형과 타원이 함께 움직이는 것을 확인할 수 있습니다—**group shapes in Word** 작업이 성공했음을 증명합니다.

### 예상 결과

* Word 파일에 단일 그룹 객체가 포함됩니다.  
* 그룹을 선택하면 사각형과 타원을 동시에 끌어다 놓거나, 크기를 조정하거나, 회전할 수 있습니다.  
* Word와의 수동 상호작용이 전혀 필요 없으며, 모든 작업이 C# 코드로 수행됩니다.

![Word 문서에서 그룹화된 도형](grouped-shapes.png "그룹화된 사각형과 타원 도형을 보여주는 Word 문서 스크린샷")

*Image alt text: “그룹화된 사각형과 타원 도형을 보여주는 Word 문서 스크린샷”* (이미지 alt‑text 요구 사항을 충족합니다).

## 그룹화된 도형이 중요한 이유

그룹화는 단순히 시각적인 편의성을 넘어선 기능을 제공합니다. 다음과 같은 이점을 얻을 수 있습니다:

* **레이아웃 일관성 유지** – 그룹을 이동하면 상대적인 위치가 그대로 유지됩니다.  
* **변환을 한 번에 적용** – 각 도형을 개별적으로 회전하거나 확대/축소하는 대신 전체 그룹을 한 번에 변형할 수 있습니다.  
* **후속 처리 간소화** – 다른 도구가 DOCX를 읽을 때 단일 복합 도형으로 인식되므로 복잡성이 감소합니다.

같은 논리 단위에 추가 도형(예: 선이나 텍스트 상자)을 넣어야 할 경우, `EndGroupShape` 전에 다시 `InsertShape`를 호출하기만 하면 됩니다.

## 일반적인 변형 및 엣지 케이스

| 상황 | 처리 방법 |
|-----------|-----------------|
| **다른 단위** – 센티미터 단위로 측정값이 있는 경우 | `InsertShape` 호출 전에 센티미터를 포인트(`1 cm ≈ 28.35 pt`)로 변환합니다. |
| **텍스트 레이블 추가** – 그룹 안에 캡션을 넣고 싶은 경우 | 사각형과 타원 뒤에 `ShapeType.TextBox`를 삽입하고 `Text` 속성을 설정합니다. |
| **채우기 색상 적용** – 파란색 사각형이 필요한 경우 | `InsertShape` 후 `builder.CurrentParagraph.Runs[0].Font`를 통해 마지막 도형을 가져와 `shape.FillColor = System.Drawing.Color.Blue;`를 설정합니다. |
| **다른 문서 형식 사용** – `.docx` 대신 `.doc`을 목표로 하는 경우 | 코드 자체는 동일하게 동작합니다; `Save` 호출 시 파일 확장자만 변경하면 됩니다. Aspose.Words가 자동으로 형식을 처리합니다. |

## 전문가 팁

* **Builder 재사용** – 동일 문서에서 여러 그룹을 시작·종료할 수 있으며, `EndGroupShape` 뒤에 다시 `StartGroupShape`를 호출하면 됩니다.  
* **성능** – 하나의 `StartGroupShape/EndGroupShape` 블록 안에 도형을 배치해 일괄 삽입하면, 그룹 외부에 개별적으로 삽입하는 것보다 빠릅니다.  
* **라이선스** – 평가 라이선스는 첫 페이지에 워터마크를 추가합니다. 프로덕션 환경에서는 정식 라이선스를 설치해 워터마크를 제거하세요.

## 결론

이제 C#로 **group shapes in Word** 하는 방법, **add rectangle**, **add ellipse**, 그리고 Aspose.Words를 사용해 Word 문서에 **insert rectangle shape Word** 하는 방법을 모두 알게 되었습니다. 완전하고 실행 가능한 예제는 프로젝트 설정부터 최종 파일 저장까지 모든 단계를 보여줍니다.

여기서부터는 추가 도형 유형을 탐색하고, 스타일을 적용하거나, 그룹화된 도형을 표와 이미지와 결합해 복잡하고 프로그래밍 방식으로 생성된 문서를 만들 수 있습니다.

---

**다음 단계**

* **그룹화된 도형 회전** 방법 배우기: 그룹을 닫은 뒤 `Shape.RotationAngle`을 사용합니다.  
* 사각형과 타원의 **채우기 및 외곽선 커스터마이징** 탐색.  
* 이 로직을 ASP.NET Core API에 통합해 필요 시 보고서를 실시간으로 생성하도록 구현합니다.  

행복한 코딩 되세요!

## 다음에 배워야 할 내용은?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하며, 밀접하게 연관된 주제를 다룹니다. 각 리소스는 완전한 코드 예제와 단계별 설명을 포함해 추가 API 기능을 마스터하고 프로젝트에 적용할 수 있도록 돕습니다.

- [Aspose.Words for .NET을 사용하여 Word 문서에 그룹 도형 만들기](/words/english/net/working-with-shapes/add-group-shape/)
- [Aspose.Words for .NET을 사용하여 Word 문서에 도형 삽입](/words/english/net/working-with-shapes/insert-shape/)
- [Word에서 사각형 도형 만들기 – 전체 Aspose.Words 가이드](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-full-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}