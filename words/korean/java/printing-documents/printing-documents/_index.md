---
title: Java용 Aspose.Words에서 문서 인쇄
linktitle: 문서 인쇄
second_title: Aspose.Words Java 문서 처리 API
description: Aspose.Words for Java를 사용하여 문서를 인쇄하는 방법을 알아보세요. Java 애플리케이션에서 원활하게 인쇄하기 위한 단계별 가이드입니다.
weight: 10
url: /ko/java/printing-documents/printing-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java용 Aspose.Words에서 문서 인쇄


Aspose.Words for Java를 사용하여 문서를 인쇄하려는 경우 올바른 위치에 있습니다. 이 단계별 가이드에서는 제공된 소스 코드를 사용하여 Aspose.Words for Java로 문서를 인쇄하는 과정을 안내합니다.

## 소개

문서 인쇄는 많은 애플리케이션에서 일반적인 작업입니다. Aspose.Words for Java는 Word 문서 작업을 위한 강력한 API를 제공하며 여기에는 인쇄 기능도 포함됩니다. 이 튜토리얼에서는 Word 문서를 단계별로 인쇄하는 과정을 안내해 드리겠습니다.

## 환경 설정하기

코드를 살펴보기 전에 다음과 같은 전제 조건이 충족되었는지 확인하세요.

- Java Development Kit (JDK) 설치됨
- Aspose.Words for Java 라이브러리가 다운로드되어 프로젝트에 추가되었습니다.

## 문서 로딩

 시작하려면 인쇄하려는 Word 문서를 로드해야 합니다. 바꾸기`"Your Document Directory"` 문서 경로와 함께`"Your Output Directory"` 원하는 출력 디렉토리로.

```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Rendering.docx");
```

## 인쇄 작업 생성

다음으로, 로드된 문서를 인쇄하기 위한 인쇄 작업을 만들겠습니다. 아래 코드 조각은 인쇄 작업을 초기화하고 원하는 프린터 설정을 설정합니다.

```java
// 문서를 인쇄할 인쇄 작업을 생성합니다.
PrinterJob pj = PrinterJob.getPrinterJob();
// 문서의 페이지 수로 속성 집합을 초기화합니다.
PrintRequestAttributeSet attributes = new HashPrintRequestAttributeSet();
attributes.add(new PageRanges(1, doc.getPageCount()));
// 다른 매개변수와 함께 프린터 설정을 인쇄 문서에 전달합니다.
MultipagePrintDocument awPrintDoc = new MultipagePrintDocument(doc, 4, true, attributes);
```

## 문서 인쇄

이제 인쇄 작업을 설정했으니 문서를 인쇄할 차례입니다. 다음 코드 조각은 문서를 인쇄 작업과 연결하고 인쇄 프로세스를 시작합니다.

```java
// 인쇄 작업을 사용하여 인쇄할 문서를 전달합니다.
pj.setPrintable(awPrintDoc);
pj.print();
```
## 완전한 소스 코드
```java
string dataDir = "Your Document Directory";
Document doc = new Document(dataDir + "Rendering.docx");
// 문서를 인쇄할 인쇄 작업을 생성합니다.
PrinterJob pj = PrinterJob.getPrinterJob();
// 문서의 페이지 수로 속성 집합을 초기화합니다.
PrintRequestAttributeSet attributes = new HashPrintRequestAttributeSet();
attributes.add(new PageRanges(1, doc.getPageCount()));
// 다른 매개변수와 함께 프린터 설정을 인쇄 문서에 전달합니다.
MultipagePrintDocument awPrintDoc = new MultipagePrintDocument(doc, 4, true, attributes);
// 인쇄 작업을 사용하여 인쇄할 문서를 전달합니다.
pj.setPrintable(awPrintDoc);
pj.print();
```
MultipagePrintDocument의 소스 코드
```java
class MultipagePrintDocument implements Printable
{
    private final Document mDocument;
    private final int mPagesPerSheet;
    private final boolean mPrintPageBorders;
    private final AttributeSet mAttributeSet;
    /// <요약>
    /// 사용자 정의 PrintDocument 클래스의 생성자입니다.
    // / </요약>
    public MultipagePrintDocument(Document document, int pagesPerSheet, boolean printPageBorders,
                                  AttributeSet attributes) {
        if (document == null)
            throw new IllegalArgumentException("document");
        mDocument = document;
        mPagesPerSheet = pagesPerSheet;
        mPrintPageBorders = printPageBorders;
        mAttributeSet = attributes;
    }
    public int print(Graphics g, PageFormat pf, int page) {
        //속성 집합에 정의된 페이지 시작 및 종료 인덱스입니다.
        int[][] pageRanges = ((PageRanges) mAttributeSet.get(PageRanges.class)).getMembers();
        int fromPage = pageRanges[0][0] - 1;
        int toPage = pageRanges[0][1] - 1;
        Dimension thumbCount = getThumbCount(mPagesPerSheet, pf);
        // 다음에 렌더링될 페이지 인덱스를 계산합니다.
        int pagesOnCurrentSheet = (int) (page * (thumbCount.getWidth() * thumbCount.getHeight()));
        // 페이지 인덱스가 전체 페이지 범위보다 큰 경우에는 아무것도 없습니다.
        // 렌더링할 것이 더 많습니다.
        if (pagesOnCurrentSheet > (toPage - fromPage))
            return Printable.NO_SUCH_PAGE;
        // 각 썸네일 플레이스홀더의 크기를 포인트 단위로 계산합니다.
        Point2D.Float thumbSize = new Point2D.Float((float) (pf.getImageableWidth() / thumbCount.getWidth()),
                (float) (pf.getImageableHeight() / thumbCount.getHeight()));
        // 이 종이에 인쇄될 첫 페이지 번호를 계산하세요.
        int startPage = pagesOnCurrentSheet + fromPage;
        // 이 용지에 인쇄될 마지막 페이지 번호를 선택하세요.
        int pageTo = Math.max(startPage + mPagesPerSheet - 1, toPage);
        // 저장된 현재 페이지에서 계산된 페이지까지 선택한 페이지를 반복합니다.
        // 마지막 페이지.
        for (int pageIndex = startPage; pageIndex <= pageTo; pageIndex++) {
            // 열과 행 인덱스를 계산합니다.
            int rowIdx = (int) Math.floor((pageIndex - startPage) / thumbCount.getWidth());
            int columnIdx = (int) Math.floor((pageIndex - startPage) % thumbCount.getWidth());
            // 세계 좌표(이 경우에는 점)로 썸네일 위치를 정의합니다.
            float thumbLeft = columnIdx * thumbSize.x;
            float thumbTop = rowIdx * thumbSize.y;
            try {
                // 왼쪽과 위쪽 시작 위치를 계산합니다.
                int leftPos = (int) (thumbLeft + pf.getImageableX());
                int topPos = (int) (thumbTop + pf.getImageableY());
                // 계산된 좌표를 사용하여 문서 페이지를 Graphics 개체에 렌더링합니다.
                // 및 썸네일 플레이스홀더 크기.
                // 유용한 반환 값은 페이지가 렌더링된 크기입니다.
                float scale = mDocument.renderToSize(pageIndex, (Graphics2D) g, leftPos, topPos, (int) thumbSize.x,
                        (int) thumbSize.y);
                //페이지 테두리를 그립니다(페이지 축소판은 축소판보다 작을 수 있음)
                // 플레이스홀더 크기).
                if (mPrintPageBorders) {
                    // 페이지의 실제 100% 크기를 포인트로 확인하세요.
                    Point2D.Float pageSize = mDocument.getPageInfo(pageIndex).getSizeInPoints();
                    // 알려진 축척 비율을 사용하여 크기가 조정된 페이지 주위에 테두리를 그립니다.
                    g.setColor(Color.black);
                    g.drawRect(leftPos, topPos, (int) (pageSize.x * scale), (int) (pageSize.y * scale));
                    // 축소판 그림 자리 표시자 주위에 테두리를 그립니다.
                    g.setColor(Color.red);
                    g.drawRect(leftPos, topPos, (int) thumbSize.x, (int) thumbSize.y);
                }
            } catch (Exception e) {
                // 렌더링 중에 오류가 발생하면 아무것도 하지 마세요.
                // 렌더링 중에 오류가 발생하면 빈 페이지가 그려집니다.
            }
        }
        return Printable.PAGE_EXISTS;
    }
    private Dimension getThumbCount(int pagesPerSheet, PageFormat pf) {
        Dimension size;
        // 시트의 열과 행의 수를 정의합니다.
        // 가로형 용지.
        switch (pagesPerSheet) {
            case 16:
                size = new Dimension(4, 4);
                break;
            case 9:
                size = new Dimension(3, 3);
                break;
            case 8:
                size = new Dimension(4, 2);
                break;
            case 6:
                size = new Dimension(3, 2);
                break;
            case 4:
                size = new Dimension(2, 2);
                break;
            case 2:
                size = new Dimension(2, 1);
                break;
            default:
                size = new Dimension(1, 1);
                break;
        }
        // 용지가 세로 방향인 경우 너비와 높이를 바꾸세요.
        if ((pf.getWidth() - pf.getImageableX()) < (pf.getHeight() - pf.getImageableY()))
            return new Dimension((int) size.getHeight(), (int) size.getWidth());
        return size;
	}
}
```

## 결론

축하합니다! Aspose.Words for Java를 사용하여 Word 문서를 성공적으로 인쇄했습니다. 이 단계별 가이드는 Java 애플리케이션에 문서 인쇄를 원활하게 통합하는 데 도움이 될 것입니다.

## 자주 묻는 질문

### 질문 1: Aspose.Words for Java를 사용하여 문서의 특정 페이지를 인쇄할 수 있나요?

 네, 문서를 인쇄할 때 페이지 범위를 지정할 수 있습니다. 코드 예제에서는 다음을 사용했습니다.`attributes.add(new PageRanges(1, doc.getPageCount()))`모든 페이지를 인쇄합니다. 필요에 따라 페이지 범위를 조정할 수 있습니다.

### 질문 2: Aspose.Words for Java는 일괄 인쇄에 적합합니까?

물론입니다! Aspose.Words for Java는 일괄 인쇄 작업에 적합합니다. 문서 목록을 반복하고 비슷한 코드를 사용하여 하나씩 인쇄할 수 있습니다.

### 질문 3: 인쇄 오류나 예외가 발생하면 어떻게 처리할 수 있나요?

인쇄 프로세스 중에 발생할 수 있는 모든 잠재적 예외를 처리해야 합니다. 예외 처리에 대한 정보는 Aspose.Words for Java 설명서를 확인하세요.

### 질문 4: 인쇄 설정을 더욱 세부적으로 사용자 지정할 수 있나요?

네, 특정 요구 사항에 맞게 인쇄 설정을 사용자 지정할 수 있습니다. Aspose.Words for Java 설명서를 탐색하여 사용 가능한 인쇄 옵션에 대해 자세히 알아보세요.

### 질문 5: Aspose.Words for Java에 대한 추가 도움말과 지원은 어디에서 받을 수 있나요?

 추가 지원 및 도움이 필요하면 다음을 방문하세요.[Aspose.Words for Java 포럼](https://forum.aspose.com/).

---

이제 Aspose.Words for Java를 사용하여 문서를 인쇄하는 방법을 성공적으로 배웠으므로 Java 애플리케이션에서 이 기능을 구현할 수 있습니다. 즐거운 코딩 되세요!
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
