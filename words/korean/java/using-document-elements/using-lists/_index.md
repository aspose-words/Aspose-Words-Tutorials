---
"description": "이 단계별 튜토리얼을 통해 Aspose.Words for Java에서 목록을 사용하는 방법을 배워보세요. 문서를 효과적으로 정리하고 서식을 지정해 보세요."
"linktitle": "목록 사용"
"second_title": "Aspose.Words Java 문서 처리 API"
"title": "Java용 Aspose.Words에서 목록 사용"
"url": "/ko/java/using-document-elements/using-lists/"
"weight": 18
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Java용 Aspose.Words에서 목록 사용


이 포괄적인 튜토리얼에서는 Microsoft Word 문서를 프로그래밍 방식으로 작업할 수 있는 강력한 API인 Aspose.Words for Java에서 목록을 효과적으로 사용하는 방법을 살펴보겠습니다. 목록은 문서의 콘텐츠를 구조화하고 구성하는 데 필수적입니다. 목록 작업의 두 가지 핵심 측면, 즉 각 섹션에서 목록을 다시 시작하는 것과 목록 수준을 지정하는 것에 대해 살펴보겠습니다. 자, 시작해 볼까요!

## Java용 Aspose.Words 소개

목록 작업을 시작하기 전에 Aspose.Words for Java에 대해 알아보겠습니다. 이 API는 개발자에게 Java 환경에서 Word 문서를 생성, 수정 및 조작할 수 있는 도구를 제공합니다. 간단한 문서 생성부터 복잡한 서식 지정 및 콘텐츠 관리까지 다양한 작업에 활용할 수 있는 다재다능한 솔루션입니다.

### 환경 설정

시작하려면 Aspose.Words for Java가 개발 환경에 설치되어 있는지 확인하세요. 다운로드할 수 있습니다. [여기](https://releases.aspose.com/words/java/). 

## 각 섹션에서 목록 다시 시작

많은 경우 문서의 각 섹션마다 목록을 다시 작성해야 할 수 있습니다. 이는 보고서, 매뉴얼, 학술 논문 등 여러 섹션으로 구성된 구조화된 문서를 만들 때 유용할 수 있습니다.

다음은 Aspose.Words for Java를 사용하여 이를 달성하는 방법에 대한 단계별 가이드입니다.

### 문서 초기화: 
먼저 새로운 문서 객체를 만듭니다.

```java
Document doc = new Document();
```

### 번호 매기기 목록 추가: 
문서에 번호 매기기 목록을 추가하세요. 기본 번호 매기기 스타일을 사용하겠습니다.

```java
doc.getLists().add(ListTemplate.NUMBER_DEFAULT);
```

### 목록 설정 구성: 
\각 섹션에서 목록을 다시 시작할 수 있도록 설정합니다.

```java
List list = doc.getLists().get(0);
list.isRestartAtEachSection(true);
```

### DocumentBuilder 설정: 
문서에 내용을 추가하려면 DocumentBuilder를 만듭니다.

```java
DocumentBuilder builder = new DocumentBuilder(doc);
builder.getListFormat().setList(list);
```

### 목록 항목 추가: 
루프를 사용하여 문서에 목록 항목을 추가합니다. 15번째 항목 뒤에 구역 나누기를 삽입합니다.

```java
for (int i = 1; i < 45; i++) {
    builder.writeln(MessageFormat.format("List Item {0}", i));
    if (i == 15)
        builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
}
```

### 문서 저장: 
원하는 옵션을 사용하여 문서를 저장합니다.

```java
OoxmlSaveOptions options = new OoxmlSaveOptions();
options.setCompliance(OoxmlCompliance.ISO_29500_2008_TRANSITIONAL);
doc.save(outPath + "RestartListAtEachSection.docx", options);
```

이러한 단계를 따르면 각 섹션으로 다시 시작되는 목록이 있는 문서를 만들 수 있으며, 명확하고 체계적인 콘텐츠 구조를 유지할 수 있습니다.

## 목록 수준 지정

Aspose.Words for Java를 사용하면 목록 수준을 지정할 수 있는데, 이는 문서 내에서 다양한 목록 형식이 필요할 때 특히 유용합니다. 그 방법을 살펴보겠습니다.

### 문서 초기화: 
새로운 문서 객체를 만듭니다.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### 번호 매기기 목록 만들기: 
Microsoft Word에서 번호 매기기 목록 템플릿을 적용합니다.

```java
builder.getListFormat().setList(doc.getLists().add(ListTemplate.NUMBER_ARABIC_DOT));
```

### 목록 수준 지정: 
다양한 목록 수준을 반복하고 콘텐츠를 추가합니다.

```java
for (int i = 0; i < 9; i++) {
    builder.getListFormat().setListLevelNumber(i);
    builder.writeln("Level " + i);
}
```

### 요점별 목록 만들기: 
이제 요점별 목록을 만들어 보겠습니다.

```java
builder.getListFormat().setList(doc.getLists().add(ListTemplate.BULLET_DIAMONDS));
```

### 글머리 기호 목록 수준 지정: 
번호가 매겨진 목록과 비슷하게 수준을 지정하고 콘텐츠를 추가합니다.

```java
for (int i = 0; i < 9; i++) {
    builder.getListFormat().setListLevelNumber(i);
    builder.writeln("Level " + i);
}
```

### 정지 목록 형식: 
목록 서식을 중지하려면 목록을 null로 설정합니다.

```java
builder.getListFormat().setList(null);
```

### 문서 저장: 
문서를 저장합니다.

```java
builder.getDocument().save(outPath + "SpecifyListLevel.docx");
```

이러한 단계를 따르면 사용자 지정 목록 수준이 있는 문서를 만들 수 있으며, 이를 통해 문서의 목록 서식을 제어할 수 있습니다.

## 완전한 소스 코드
```java
	string outPath = "Your Output Directory";
 public void restartListAtEachSection() throws Exception
    {
        Document doc = new Document();
        doc.getLists().add(ListTemplate.NUMBER_DEFAULT);
        List list = doc.getLists().get(0);
        list.isRestartAtEachSection(true);
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.getListFormat().setList(list);
        for (int i = 1; i < 45; i++)
        {
            builder.writeln(MessageFormat.format("List Item {0}", i));
            if (i == 15)
                builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
        }
        // IsRestartAtEachSection은 규정 준수가 OoxmlComplianceCore.Ecma376보다 높은 경우에만 작성됩니다.
        OoxmlSaveOptions options = new OoxmlSaveOptions(); { options.setCompliance(OoxmlCompliance.ISO_29500_2008_TRANSITIONAL); }
        doc.save(outPath + "WorkingWithList.RestartListAtEachSection.docx", options);
    }
    @Test
    public void specifyListLevel() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Microsoft Word 목록 템플릿 중 하나를 기반으로 번호 매기기 목록을 만듭니다.
        // 이를 문서 작성기의 현재 문단에 적용합니다.
        builder.getListFormat().setList(doc.getLists().add(ListTemplate.NUMBER_ARABIC_DOT));
        // 이 목록에는 9개의 레벨이 있습니다. 모두 시도해 보겠습니다.
        for (int i = 0; i < 9; i++)
        {
            builder.getListFormat().setListLevelNumber(i);
            builder.writeln("Level " + i);
        }
        // Microsoft Word 목록 템플릿 중 하나를 기반으로 글머리 기호 목록을 만듭니다.
        // 이를 문서 작성기의 현재 문단에 적용합니다.
        builder.getListFormat().setList(doc.getLists().add(ListTemplate.BULLET_DIAMONDS));
        for (int i = 0; i < 9; i++)
        {
            builder.getListFormat().setListLevelNumber(i);
            builder.writeln("Level " + i);
        }
        // 이는 목록 서식을 중지하는 방법입니다.
        builder.getListFormat().setList(null);
        builder.getDocument().save(outPath + "WorkingWithList.SpecifyListLevel.docx");
    }
    @Test
    public void restartListNumber() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // 템플릿을 기반으로 목록을 만듭니다.
        List list1 = doc.getLists().add(ListTemplate.NUMBER_ARABIC_PARENTHESIS);
        list1.getListLevels().get(0).getFont().setColor(Color.RED);
        list1.getListLevels().get(0).setAlignment(ListLevelAlignment.RIGHT);
        builder.writeln("List 1 starts below:");
        builder.getListFormat().setList(list1);
        builder.writeln("Item 1");
        builder.writeln("Item 2");
        builder.getListFormat().removeNumbers();
        // 첫 번째 목록을 재사용하려면 원본 목록 서식의 복사본을 만들어 번호 매기기를 다시 시작해야 합니다.
        List list2 = doc.getLists().addCopy(list1);
        // 새로운 목록은 새로운 시작 번호를 설정하는 것을 포함하여 어떤 방법으로든 수정할 수 있습니다.
        list2.getListLevels().get(0).setStartAt(10);
        builder.writeln("List 2 starts below:");
        builder.getListFormat().setList(list2);
        builder.writeln("Item 1");
        builder.writeln("Item 2");
        builder.getListFormat().removeNumbers();
        builder.getDocument().save(outPath + "WorkingWithList.RestartListNumber.docx");
	}
```

## 결론

축하합니다! Aspose.Words for Java에서 목록을 효과적으로 사용하는 방법을 익히셨습니다. 목록은 문서의 콘텐츠를 구성하고 표현하는 데 매우 중요합니다. 각 섹션별로 목록을 다시 시작하거나 목록 수준을 지정해야 하는 경우, Aspose.Words for Java는 전문적인 문서를 만드는 데 필요한 도구를 제공합니다.

이제 이러한 기능을 사용하여 문서 생성 및 서식 지정 작업을 더욱 효율적으로 수행할 수 있습니다. 궁금한 점이 있거나 추가 지원이 필요하시면 언제든지 문의해 주세요. [Aspose 커뮤니티 포럼](https://forum.aspose.com/) 지원을 위해.

## 자주 묻는 질문

### Java용 Aspose.Words를 어떻게 설치하나요?
Aspose.Words for Java는 다음에서 다운로드할 수 있습니다. [여기](https://releases.aspose.com/words/java/) 설명서의 설치 지침을 따르세요.

### 목록의 번호 매기기 형식을 사용자 지정할 수 있나요?
네, Aspose.Words for Java는 목록 번호 매기기 형식을 사용자 정의할 수 있는 다양한 옵션을 제공합니다. 자세한 내용은 API 문서를 참조하세요.

### Aspose.Words for Java는 최신 Word 문서 표준과 호환됩니까?
네, ISO 29500을 포함한 다양한 Word 문서 표준을 준수하도록 Aspose.Words for Java를 구성할 수 있습니다.

### Aspose.Words for Java를 사용하여 표와 이미지가 포함된 복잡한 문서를 생성할 수 있나요?
물론입니다! Aspose.Words for Java는 표, 이미지 등 고급 문서 서식을 지원합니다. 설명서에서 예시를 확인하세요.

### Aspose.Words for Java에 대한 임시 라이센스는 어디서 받을 수 있나요?
임시면허를 취득할 수 있습니다 [여기](https://purchase.aspose.com/temporary-license/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}