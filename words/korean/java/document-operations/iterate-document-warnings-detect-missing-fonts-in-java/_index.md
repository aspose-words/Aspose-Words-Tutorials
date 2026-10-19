---
category: general
date: 2026-04-28
description: Aspose.Words for Java를 사용하여 Word 파일의 문서 경고를 반복하면서 누락된 글꼴을 감지하고, 누락된 글꼴
  이름을 가져와 누락된 글꼴 세부 정보를 출력합니다.
draft: false
keywords:
- iterate document warnings
- detect missing fonts
- load word document
- retrieve missing font
- print missing font
language: ko
og_description: 문서 경고를 반복하여 누락된 글꼴을 찾고, 누락된 글꼴 이름을 가져오며, 전체 Java 예제를 사용하여 누락된 글꼴 세부
  정보를 출력합니다.
og_title: '문서 경고 반복: Java에서 누락된 글꼴 감지'
tags:
- Aspose.Words
- Java
- Document Processing
title: '문서 경고 반복: Java에서 누락된 글꼴 감지'
url: /ko/java/document-operations/iterate-document-warnings-detect-missing-fonts-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 문서 경고 반복 – Java에서 누락된 글꼴 감지

Word 파일을 열 때 **문서 경고를 반복**하면서 어떤 글꼴이 누락되었는지 궁금했던 적 있나요? 당신만 그런 것이 아닙니다. 누락된 글꼴은 보고서의 레이아웃을 깨뜨릴 수 있으며, 이를 찾는 방법이 없으면 원본과 전혀 다른 문서를 배포하게 될 수도 있습니다.  

이 튜토리얼에서는 Aspose.Words for Java를 사용해 Word 문서를 로드하고, 경고를 반복하면서 누락된 글꼴 이름을 가져와 최종적으로 누락된 글꼴 정보를 출력하는 **누락된 글꼴 감지** 방법을 보여드립니다.  

코드 첫 줄부터 기대되는 콘솔 출력까지 모두 다루므로, 지금 바로 프로젝트에 복사‑붙여넣기 할 수 있는 작동 예제를 얻을 수 있습니다. 별도의 문서는 필요 없습니다.

## Prerequisites

- Java 8 이상 설치
- Aspose.Words for Java 라이브러리 (2026‑04‑28 기준 최신 버전)
- 머신에 설치되지 않은 글꼴이 포함될 수 있는 Word 파일 (예: `doc-with-missing-font.docx`)

위 항목이 모두 준비되었다면, **load word document**하고 경고를 반복할 준비가 된 것입니다.

## Step 1 – 기본 옵션으로 Word 문서 로드

**문서 경고를 반복**하려면 먼저 파일을 메모리로 로드해야 합니다. Aspose.Words는 단일 생성자 호출만으로 이를 수행합니다. 기본 `LoadOptions`를 사용하는 것이 보통 충분하지만, 명확성을 위해 명시적인 생성 방법을 보여드립니다.

```java
import com.aspose.words.*;

public class MissingFontDetector {
    public static void main(String[] args) throws Exception {

        // Step 1: Prepare load options (default settings are fine for this example)
        LoadOptions loadOptions = new LoadOptions();

        // Step 2: Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/doc-with-missing-font.docx", loadOptions);
```

> **왜 중요한가:**  
> 문서를 로드하면 Aspose.Words가 로컬에 설치되지 않은 글꼴과 같이 해결할 수 없는 리소스를 스캔합니다. 이러한 문제는 **warnings**로 저장되며, 다음 단계에서 **iterate document warnings**를 통해 확인할 수 있습니다.

## Step 2 – 문서 경고를 반복하여 글꼴 문제 찾기

이제 솔루션의 핵심 단계입니다. 라이브러리가 로드 중에 수집한 모든 경고를 순회합니다. `WarningInfo` 객체는 어떤 문제가 발생했는지 알려주며, `FontSubstitutionWarning`을 필터링해 **누락된 글꼴을 감지**합니다.

```java
        // Step 3: Iterate over all warnings generated during loading
        for (WarningInfo warningInfo : document.getWarnings()) {
            // Step 4: Identify font substitution warnings
            if (warningInfo instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fontWarning = (FontSubstitutionWarning) warningInfo;

                // Step 5: Output the missing font name and the font that was used as a substitute
                System.out.println("Missing font: " + fontWarning.getMissingFontName());
                System.out.println("Substituted with: " + fontWarning.getSubstitutedFontName());
            }
        }
    }
}
```

> **팁:** `instanceof` 검사를 사용하면 이미지 로드 문제와 같은 다른 경고는 무시하고 글꼴 관련 경고만 처리할 수 있어 루프가 효율적이며, 실제로 **retrieve missing font** 정보를 얻고자 하는 글꼴에만 집중할 수 있습니다.

### Expected Console Output

```
Missing font: Arial Black
Substituted with: Liberation Sans
Missing font: Calibri
Substituted with: Liberation Sans
```

문서에 누락된 글꼴이 없으면 루프는 조용히 종료됩니다— **print missing font**할 것이 없습니다.

## Step 3 – 예외를 잡는 것만으로는 왜 안 될까?

“`new Document(...)` 호출을 try‑catch 로 감싸고 예외를 확인하면 되지 않을까?” 라고 생각할 수 있습니다. 답은 두 가지입니다:

1. **세부 정보 제공:** 예외는 무언가 실패했음을 알려줄 뿐입니다. 경고는 정확한 글꼴 이름과 Aspose.Words가 선택한 대체 글꼴을 제공합니다.
2. **비치명적 문제:** 누락된 글꼴은 보통 치명적이지 않아 문서는 여전히 로드되지만 시각적 정확도가 떨어집니다. **iterate document warnings**를 사용하면 파일의 나머지 부분을 계속 처리할 수 있습니다.

## Step 4 – 예제 확장: 누락된 글꼴을 리스트에 수집

때때로 누락된 글꼴을 추가 처리해야 할 때가 있습니다—예를 들어 글꼴을 임베드하거나 UI를 통해 사용자에게 알릴 때 말이죠. 아래와 같이 이름을 `Set<String>`에 모으는 간단한 수정 예시를 보여드립니다.

```java
        // Collect missing fonts for later use
        Set<String> missingFonts = new HashSet<>();

        for (WarningInfo warningInfo : document.getWarnings()) {
            if (warningInfo instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fontWarning = (FontSubstitutionWarning) warningInfo;
                missingFonts.add(fontWarning.getMissingFontName());

                // Still print for immediate feedback
                System.out.println("Missing font: " + fontWarning.getMissingFontName());
                System.out.println("Substituted with: " + fontWarning.getSubstitutedFontName());
            }
        }

        // Example of using the collected data
        System.out.println("Total missing fonts: " + missingFonts.size());
```

이제 프로그램matically **retrieve missing font** 데이터를 깔끔하게 얻을 수 있으며, 이를 보고 모듈이나 글꼴 설치 마법사에 전달할 수 있습니다.

## Step 5 – 실제 적용 시 고려 사항

- **다중 대체:** 하나의 누락된 글꼴이 문서의 서로 다른 부분에서 서로 다른 글꼴로 대체될 수 있습니다. 경고 리스트에는 각 발생이 포함되므로 중복된 누락 글꼴 항목이 보일 수 있습니다.
- **성능:** 매우 큰 문서를 로드하면 수천 개의 경고가 생성될 수 있습니다. 글꼴만 필요하다면 앞서 보여준 대로 초기에 필터링해 루프를 빠르게 유지하세요.
- **크로스‑플랫폼 글꼴:** Linux에서는 기본 대체 글꼴이 보통 *Liberation Sans*이며, Windows에서는 *Arial*이 될 수 있습니다. 어떤 대체 글꼴이 사용되는지 알면 애플리케이션에 맞춤 글꼴을 포함시켜야 할지 판단하는 데 도움이 됩니다.

## Step 6 – Visual Aid

아래는 콘솔 출력 스크린샷입니다 (alt 텍스트에 주요 키워드 포함).

![Iterate document warnings console output showing missing fonts and their substitutes](/images/iterate-document-warnings.png)

*Alt text:* *iterate document warnings example displaying missing font names and substitution details.*

## Conclusion

이제 Aspose.Words for Java에서 **iterate document warnings**를 사용해 **누락된 글꼴을 감지**, **load word document**를 안전하게 수행하고, **retrieve missing font** 정보를 얻으며, 콘솔에 **print missing font** 상세 정보를 출력하는 방법을 배웠습니다. 전체 코드 스니펫은 그대로 실행 가능하며, 파일에 로그를 남기거나 UI 대화상자를 표시하거나 누락된 글꼴을 자동으로 임베드하도록 확장할 수 있습니다.

다음 단계로는 **load word document**에 사용자 지정 글꼴 소스(예: 기업 글꼴 폴더 추가)를 적용하거나, 누락된 글꼴을 파일에 직접 임베드해 머신 간 레이아웃을 유지하는 방법을 탐색해 보세요. 두 주제 모두 여기서 다룬 내용에 자연스럽게 이어집니다.

행복한 코딩 되세요, 그리고 PDF가 언제나 의도한 대로 보이길 바랍니다!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}