---
title: Datatable에서 테이블 생성
linktitle: Datatable에서 테이블 생성
second_title: Aspose.Words Java 문서 처리 API
description: Aspose.Words for Java를 사용하여 DataTable에서 테이블을 생성하는 방법을 알아보세요. 포맷된 테이블로 전문적인 Word 문서를 손쉽게 만드세요.
weight: 11
url: /ko/java/table-processing/generate-table-from-datatable/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Datatable에서 테이블 생성

## 소개

데이터 소스에서 동적으로 테이블을 만드는 것은 많은 애플리케이션에서 일반적인 작업입니다. 보고서, 송장 또는 데이터 요약을 생성하든, 프로그래밍 방식으로 테이블에 데이터를 채울 수 있다면 많은 시간과 노력을 절약할 수 있습니다. 이 튜토리얼에서는 Aspose.Words for Java를 사용하여 DataTable에서 테이블을 생성하는 방법을 살펴보겠습니다. 프로세스를 관리 가능한 단계로 나누어 각 부분을 명확하게 이해할 수 있도록 하겠습니다.

## 필수 조건

코드를 살펴보기 전에 시작하는 데 필요한 모든 것이 있는지 확인해 보겠습니다.

1.  Java Development Kit(JDK): 컴퓨터에 JDK가 설치되어 있는지 확인하세요. 다음에서 다운로드할 수 있습니다.[오라클 웹사이트](https://www.oracle.com/java/technologies/javase-jdk11-downloads.html).
   
2.  Java용 Aspose.Words: Aspose.Words 라이브러리가 필요합니다. 최신 버전은 다음에서 다운로드할 수 있습니다.[Aspose의 릴리스 페이지](https://releases.aspose.com/words/java/).

3. IDE: IntelliJ IDEA나 Eclipse와 같은 통합 개발 환경(IDE)을 사용하면 코딩이 더 쉬워집니다.

4. Java에 대한 기본 지식: Java 프로그래밍 개념에 익숙하면 코드 조각을 더 잘 이해하는 데 도움이 됩니다.

5. 샘플 데이터: 이 튜토리얼에서는 "List of people.xml"이라는 XML 파일을 사용하여 데이터 소스를 시뮬레이션합니다. 테스트를 위해 샘플 데이터로 이 파일을 만들 수 있습니다.

## 1단계: 새 문서 만들기

먼저, 테이블이 위치할 새 문서를 만들어야 합니다. 이것이 우리 작업의 캔버스입니다.

```java
Document doc = new Document();
```

 여기서 우리는 새로운 것을 인스턴스화합니다`Document` 객체입니다. 이것은 우리가 테이블을 만들 작업 문서 역할을 할 것입니다.

## 2단계: DocumentBuilder 초기화

 다음으로, 우리는 다음을 사용할 것입니다.`DocumentBuilder` 문서를 더 쉽게 조작할 수 있게 해주는 클래스입니다.

```java
DocumentBuilder builder = new DocumentBuilder(doc);
```

 그만큼`DocumentBuilder` 객체는 문서에 표, 텍스트 및 기타 요소를 삽입하는 방법을 제공합니다.

## 3단계: 페이지 방향 설정

우리는 테이블이 넓을 것으로 예상하므로 페이지 방향을 가로로 설정합니다.

```java
doc.getFirstSection().getPageSetup().setOrientation(Orientation.LANDSCAPE);
```

이 단계는 표가 잘리지 않고 페이지에 꼭 맞는지 확인하는 데 매우 중요합니다.

## 4단계: XML에서 데이터 로드

 이제 XML 파일에서 데이터를 로드해야 합니다.`DataTable`. 이것이 바로 우리의 데이터가 나오는 곳입니다.

```java
DataSet ds = new DataSet();
ds.readXml(getMyDir() + "List of people.xml");
DataTable dataTable = ds.getTables().get(0);
```

 여기서 우리는 XML 파일을 읽고 데이터 세트에서 첫 번째 테이블을 검색합니다.`DataTable` 문서에 표시하려는 데이터를 보관합니다.

## 5단계: DataTable에서 테이블 가져오기

이제 흥미로운 단계가 시작됩니다. 데이터를 표 형태로 문서에 가져오는 것입니다.

```java
Table table = importTableFromDataTable(builder, dataTable, true);
```

 우리는 이 방법을 호출합니다`importTableFromDataTable` , 통과`DocumentBuilder` , 우리의`DataTable`, 열 제목을 포함할지 여부를 나타내는 부울 값입니다.

## 6단계: 테이블 스타일 지정

테이블이 완성되면 스타일을 적용해 보기 좋게 만들 수 있습니다.

```java
table.setStyleIdentifier(StyleIdentifier.MEDIUM_LIST_2_ACCENT_1);
table.setStyleOptions(TableStyleOptions.FIRST_ROW | TableStyleOptions.ROW_BANDS | TableStyleOptions.LAST_COLUMN);
```

이 코드는 표에 미리 정의된 스타일을 적용해 시각적 매력과 가독성을 향상시킵니다.

## 7단계: 원치 않는 세포 제거

이미지 열 등 표시하고 싶지 않은 열이 있는 경우 쉽게 제거할 수 있습니다.

```java
table.getFirstRow().getLastCell().removeAllChildren();
```

이 단계를 거치면 표에 관련 정보만 표시됩니다.

## 8단계: 문서 저장

마지막으로 생성된 표와 함께 문서를 저장합니다.

```java
doc.save(getArtifactsDir() + "WorkingWithTables.BuildTableFromDataTable.docx");
```

이 줄은 지정된 디렉토리에 문서를 저장하여 결과를 검토할 수 있도록 합니다.

## importTableFromDataTable 메서드

 좀 더 자세히 살펴보겠습니다.`importTableFromDataTable` 방법. 이 방법은 테이블 구조를 만들고 데이터로 채우는 역할을 합니다.

### 1단계: 테이블 시작

먼저, 문서에서 새 표를 시작해야 합니다.

```java
Table table = builder.startTable();
```

이렇게 하면 문서에 새로운 표가 초기화됩니다.

### 2단계: 열 제목 추가

 열 제목을 포함하려면 다음을 확인합니다.`importColumnHeadings` 깃발.

```java
if (importColumnHeadings) {
    // 원래 포맷을 저장하세요
    boolean boldValue = builder.getFont().getBold();
    int paragraphAlignmentValue = builder.getParagraphFormat().getAlignment();

    // 제목 서식 설정
    builder.getFont().setBold(true);
    builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);

    // 열 이름 삽입
    for (DataColumn column : dataTable.getColumns()) {
        builder.insertCell();
        builder.writeln(column.getColumnName());
    }

    builder.endRow();

    // 원래 서식 복원
    builder.getFont().setBold(boldValue);
    builder.getParagraphFormat().setAlignment(paragraphAlignmentValue);
}
```

 이 코드 블록은 제목 행을 포맷하고 열 이름을 삽입합니다.`DataTable`.

### 3단계: 데이터로 표 채우기

 이제 각 행을 반복합니다.`DataTable` 테이블에 데이터를 삽입합니다.

```java
for (DataRow dataRow : (Iterable<DataRow>) dataTable.getRows()) {
    for (Object item : dataRow.getItemArray()) {
        builder.insertCell();
        switch (item.getClass().getName()) {
            case "DateTime":
                Date dateTime = (Date) item;
                SimpleDateFormat simpleDateFormat = new SimpleDateFormat("MMMM d, yyyy");
                builder.write(simpleDateFormat.format(dateTime));
                break;
            default:
                builder.write(item.toString());
                break;
        }
    }
    builder.endRow();
}
```

이 섹션에서는 다양한 데이터 유형을 처리하고 날짜를 적절히 형식화하며 다른 데이터를 텍스트로 삽입합니다.

### 4단계: 테이블 종료

마지막으로 모든 데이터를 삽입하면 표를 완성합니다.

```java
builder.endTable();
```

 이 줄은 테이블의 끝을 표시하여 다음을 허용합니다.`DocumentBuilder` 이 섹션이 끝났음을 알려드립니다.

## 결론

이제 다 봤습니다! Aspose.Words for Java를 사용하여 DataTable에서 테이블을 생성하는 방법을 성공적으로 배웠습니다. 이러한 단계를 따르면 다양한 데이터 소스를 기반으로 문서에서 동적 테이블을 쉽게 만들 수 있습니다. 보고서나 송장을 생성하든 이 방법은 워크플로를 간소화하고 문서 생성 프로세스를 향상시킵니다.

## 자주 묻는 질문

### Java용 Aspose.Words란 무엇인가요?
Aspose.Words for Java는 Word 문서를 프로그래밍 방식으로 만들고, 조작하고, 변환하기 위한 강력한 라이브러리입니다.

### Aspose.Words를 무료로 사용할 수 있나요?
 네, Aspose는 무료 체험판을 제공합니다. 여기에서 다운로드할 수 있습니다.[여기](https://releases.aspose.com/).

### Aspose.Words에서 표 스타일을 어떻게 지정하나요?
라이브러리에서 제공하는 미리 정의된 스타일 식별자와 옵션을 사용하여 스타일을 적용할 수 있습니다.

### 어떤 유형의 데이터를 표에 삽입할 수 있나요?
텍스트, 숫자, 날짜 등 다양한 데이터 유형을 삽입할 수 있으며, 이에 따라 형식을 지정할 수 있습니다.

### Aspose.Words에 대한 지원은 어디서 받을 수 있나요?
 지원을 받고 질문할 수 있습니다.[Aspose 포럼](https://forum.aspose.com/c/words/8/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
