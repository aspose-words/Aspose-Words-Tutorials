---
category: general
date: 2026-01-11
description: Aspose.Words for Java를 사용하여 글꼴 대체 경고를 캡처하는 방법을 배웁니다. 이 단계별 튜토리얼에서는 LoadOptions와
  경고 콜백도 다룹니다.
draft: false
keywords:
- capture font substitution warnings
- Aspose.Words font substitution
- Java warning callback
- LoadOptions usage
- document loading warnings
language: ko
og_description: Aspose.Words for Java를 사용하여 글꼴 대체 경고를 포착하세요. 신뢰할 수 있는 문서 로드를 위해 LoadOptions와
  경고 콜백을 설정하는 방법을 따라보세요.
og_title: Java에서 글꼴 대체 경고 포착 – 전체 튜토리얼
tags:
- Aspose.Words
- Java
- Document Processing
title: Java와 Aspose.Words를 사용한 글꼴 대체 경고 캡처 – 완전 가이드
url: /ko/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 글꼴 대체 경고 캡처 – 전체 Java 튜토리얼

Word 문서를 열 때 누락된 글꼴이 있을 경우 **capture font substitution warnings** 를 캡처해야 했던 적이 있나요? 특히 PDF를 생성하거나 모든 글꼴이 설치되지 않은 서버에서 인쇄할 때 흔히 겪는 문제입니다. 좋은 소식은 Aspose.Words for Java 를 사용하면 간단히 `LoadOptions` 객체를 설정하고 경고 콜백을 연결하기만 하면 된다는 것입니다. 이 가이드에서는 정확히 어떻게 하는지, 왜 중요한지, 경고가 발생했을 때 어떤 결과가 나오는지를 보여드립니다.

또한 **Aspose.Words font substitution**, **Java warning callback** 사용법, **LoadOptions 사용**에 대한 모범 사례도 다룹니다. 마지막에는 누락된 글꼴 이벤트를 모두 기록하는 실행 가능한 코드 스니펫을 제공하므로, 이후 처리 과정에서 예기치 않은 상황이 발생하지 않게 됩니다.

## 사전 요구 사항

시작하기 전에 다음이 준비되어 있는지 확인하세요:

- Java 17(또는 최신 JDK) 설치 및 설정
- 클래스패스에 Aspose.Words for Java 23.10(또는 최신 버전) 추가
- 로컬에 없는 글꼴을 참조하는 Word 문서(예: `DocWithMissingFont.docx`)
- Java try/catch 블록에 대한 기본 지식—특별한 내용은 필요 없습니다

위 항목 중 익숙하지 않은 것이 있다면 잠시 멈추고 Maven Central에서 라이브러리를 설치하세요:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
</dependency>
```

준비가 끝났다면 코드 작성을 시작합니다.

## Step 1: **Capture Font Substitution Warnings** 를 위한 경고 콜백 설정

먼저 누락된 글꼴을 만나면 Aspose.Words 가 호출할 콜백이 필요합니다. 여기서 **capture font substitution warnings** 를 수행합니다. 콜백은 `IWarningCallback` 인터페이스를 구현하고 `WarningType`을 확인합니다.

```java
import com.aspose.words.*;

public class FontSubstitutionInfo {

    // Custom callback that prints details of each font substitution warning
    private static class FontWarningCallback implements IWarningCallback {
        @Override
        public void warning(WarningInfo info) {
            // Only act on font‑substitution warnings
            if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                System.out.println("Font substitution warning:");
                System.out.println("  Original font: " + info.getSource());
                System.out.println("  Substituted by: " + info.getDescription());
            }
        }
    }

    public static void main(String[] args) throws Exception {
        // Code continues in the next steps...
    }
}
```

**왜 중요한가:** 콜백이 없으면 Aspose.Words 가 누락된 글꼴을 기본 글꼴로 조용히 교체하고, 시각적 출력이 바뀐 사실을 알 수 없습니다. 경고를 캡처하면 로그를 남기거나 알림을 보내거나, 중요한 글꼴이라면 로드를 중단할 수도 있습니다.

## Step 2: **LoadOptions** 구성 및 콜백 등록

이제 `LoadOptions` 인스턴스를 만들고 `FontWarningCallback` 을 연결합니다. 이 단계는 **LoadOptions 사용**에 필수이며, 모든 문서 로드가 동일한 경고 필터를 통과하도록 보장합니다.

```java
public static void main(String[] args) throws Exception {
    // Step 2: Prepare LoadOptions and hook the warning callback
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new FontWarningCallback());

    // Continue to load the document in the next step...
}
```

**팁:** 동일한 `LoadOptions` 객체를 여러 문서에 재사용하면 보일러플레이트 코드를 줄이고, 애플리케이션 전반에 걸쳐 일관된 **document loading warnings** 처리를 보장합니다.

## Step 3: 문서 로드 및 출력 확인

콜백을 연결한 상태에서 Word 파일을 로드하면 됩니다. 문서가 설치되지 않은 글꼴을 참조하고 있다면 콜백이 실행되어 콘솔에 상세 정보를 출력합니다.

```java
    // Step 3: Load the document using the configured LoadOptions
    Document doc = new Document("YOUR_DIRECTORY/DocWithMissingFont.docx", loadOptions);

    // Step 4: Confirm that the load completed
    System.out.println("Document loaded; check console for any font‑substitution warnings.");
}
```

### 예상 콘솔 출력

`DocWithMissingFont.docx` 가 누락된 글꼴 *“Comic Sans MS”* 를 참조한다고 가정하면 다음과 같은 출력이 나타납니다:

```
Font substitution warning:
  Original font: Comic Sans MS
  Substituted by: Arial
Document loaded; check console for any font‑substitution warnings.
```

문서에 **누락된 글꼴이 없는 경우**, 콘솔에는 최종 라인만 표시되어 콜백이 잘못된 양성 반응을 내지 않았음을 확인할 수 있습니다.

## Step 4: 엣지 케이스 및 일반적인 함정 처리

### 여러 개의 누락된 글꼴

문서에 사용 가능한 글꼴이 여러 개 없을 경우, 콜백은 글꼴당 한 번씩 실행됩니다. 각각의 `source`와 `description`을 포함한 일련의 메시지를 받게 됩니다. 별도의 코드는 필요 없으며, 로깅 시스템이 연속 호출을 처리할 수 있도록만 하면 됩니다.

### 경고 억제

특정 대체가 허용된다는 것을 알고 있어 경고를 무시하고 싶을 때가 있습니다. 콜백 로직을 확장하세요:

```java
if (info.getWarningType() == WarningType.FONT_SUBSTITUTION &&
    !info.getSource().equalsIgnoreCase("SomeFontYouAccept")) {
    // Log or act on the warning
}
```

### 스레드 안전성

Aspose.Words `LoadOptions` 는 기본적으로 스레드‑안전하지 않습니다. 병렬로 문서를 로드한다면 스레드당 별도의 `LoadOptions` 인스턴스를 만들거나, 콜백을 동기화하여 레이스 컨디션을 방지하세요.

## Step 5: 결과 문서에서 대체된 글꼴 확인

로드 후 실제로 대체가 이루어졌는지 확인하고 싶을 수 있습니다. API 를 사용해 모든 Run 을 순회하면서 실제 적용된 글꼴 이름을 검사할 수 있습니다:

```java
for (Run run : (Iterable<Run>) doc.getFirstSection().getBody().getChildNodes(NodeType.RUN, true)) {
    System.out.println("Run text: \"" + run.getText() + "\" uses font: " + run.getFont().getName());
}
```

이 스니펫은 각 텍스트 Run 과 최종 글꼴을 출력합니다. 자동화된 PDF 변환 파이프라인을 구축할 때 유용한 검증 단계입니다.

## 전체 작업 예제

모든 내용을 하나로 합치면 다음과 같은 완전한 실행 프로그램이 됩니다:

```java
import com.aspose.words.*;

public class FontSubstitutionInfo {

    private static class FontWarningCallback implements IWarningCallback {
        @Override
        public void warning(WarningInfo info) {
            if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                System.out.println("Font substitution warning:");
                System.out.println("  Original font: " + info.getSource());
                System.out.println("  Substituted by: " + info.getDescription());
            }
        }
    }

    public static void main(String[] args) throws Exception {
        // Prepare LoadOptions and register the warning callback
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new FontWarningCallback());

        // Load the document (replace with your actual path)
        Document doc = new Document("YOUR_DIRECTORY/DocWithMissingFont.docx", loadOptions);

        // Optional: verify effective fonts in the document
        for (Run run : (Iterable<Run>) doc.getFirstSection().getBody().getChildNodes(NodeType.RUN, true)) {
            System.out.println("Run text: \"" + run.getText() + "\" uses font: " + run.getFont().getName());
        }

        System.out.println("Document loaded; check console for any font‑substitution warnings.");
    }
}
```

`FontSubstitutionInfo.java` 로 저장하고 `javac` 로 컴파일한 뒤 `java FontSubstitutionInfo` 로 실행하세요. 경고 메시지(있는 경우)와 함께 각 Run 과 최종 글꼴 목록이 출력됩니다.

## 시각 자료

![누락된 글꼴 경고를 보여주는 콘솔 출력 스크린샷](/images/font-substitution-warning.png "capture font substitution warnings example")

*Alt text:* **capture font substitution warnings** – 누락된 글꼴이 있는 문서를 로드한 후 콘솔에 표시되는 출력.

## 결론

이제 Aspose.Words for Java 를 사용해 **capture font substitution warnings** 를 캡처하는 방법을 알게 되었습니다. `LoadOptions` 객체를 구성하고 맞춤형 `IWarningCallback` 을 제공함으로써, 문서 외관에 조용히 영향을 줄 수 있는 누락된 글꼴 이벤트를 완전히 가시화할 수 있습니다. 이 기술은 **Aspose.Words font substitution** 처리와 직접 연결되며, 신뢰할 수 있는 **document loading warnings** 를 보장하고, 비즈니스 규칙에 따라 로그, 알림 또는 로드 중단을 자유롭게 구현할 수 있게 합니다.

### 다음 단계

- 다른 경고 유형(예: `DEPRECATED_FEATURE`)에 대한 **Java warning callback** 패턴 탐색
- **PDF 변환**과 결합해 대체된 글꼴이 레이아웃을 깨뜨리지 않도록 보장
- `Password`, `Encoding`, `ResourceLoadingCallback` 등을 활용한 **LoadOptions 사용** 심화 실험

콜백을 자유롭게 커스터마이징하고, 경고를 로깅 프레임워크로 라우팅하거나, 중요한 글꼴이 누락되면 사용자 정의 예외를 발생시키는 등 다양한 활용이 가능합니다. 이제 탄탄한 기반을 갖추었으니, 원하는 대로 확장해 보세요.

행복한 코딩 되시고, 문서가 언제나 기대한 대로 렌더링되길 바랍니다!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}