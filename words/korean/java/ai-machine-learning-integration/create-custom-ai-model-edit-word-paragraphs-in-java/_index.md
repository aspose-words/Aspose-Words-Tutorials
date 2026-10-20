---
category: general
date: 2026-03-25
description: Word 문서를 편집하기 위한 맞춤형 AI 모델 만들기 – 텍스트를 더 격식 있게 만드는 방법, 단락 텍스트를 교체하는 방법,
  그리고 Aspose.Words AI를 사용해 Word 단락을 다시 쓰는 방법을 배워보세요.
draft: false
keywords:
- create custom ai model
- make text more formal
- replace paragraph text
- edit paragraph with ai
- rewrite word paragraph
language: ko
og_description: Word 문서를 편집하기 위한 맞춤형 AI 모델을 생성하세요. 텍스트를 더 격식 있게 만드는 방법, 단락 텍스트를 교체하는
  방법, 그리고 Aspose.Words AI를 사용하여 Word 단락을 다시 작성하는 방법을 배워보세요.
og_title: 맞춤형 AI 모델 만들기 – Java에서 Word 단락 편집
tags:
- Aspose.Words
- Java
- AI integration
title: 맞춤형 AI 모델 만들기 – Java로 워드 단락 편집
url: /ko/java/ai-machine-learning-integration/create-custom-ai-model-edit-word-paragraphs-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 맞춤형 AI 모델 만들기 – Java에서 Word 단락 편집

Word 파일 안의 단락을 다듬는 **맞춤형 AI 모델**을 만들고 싶었던 적이 있나요? 예를 들어, 계약서가 조금은 격식에 맞지 않게 느껴져서 한 줄의 코드만으로 텍스트를 더 공식적으로 바꾸고 싶을 때 말이죠. 좋은 소식은 바로 가능합니다—외부 서비스도, 무거운 SDK도 필요 없으며, Aspose.Words for Java와 OpenAI 호환 엔드포인트만 있으면 됩니다.

이 튜토리얼에서는 **맞춤형 AI 모델**을 만들고, 로컬 LLM 서버에 연결한 뒤, *단락 텍스트를* 더 공식적인 버전으로 **교체**하는 전체 과정을 단계별로 안내합니다. 최종적으로 AI를 사용해 **단락을 편집**하고, Word 문단을 재작성한 뒤 결과를 디스크에 저장하는 실행 가능한 Java 프로그램을 얻을 수 있습니다. 불필요한 내용은 없으며, 바로 프로젝트에 복사‑붙여넣기 할 수 있는 실용적인 솔루션만 제공합니다.

> **필요한 준비물**  
> • Java 17 이상 (코드는 이전 버전에서도 컴파일되지만, 17이 가장 적합합니다)  
> • Aspose.Words for Java 23.9 (또는 최신 버전)  
> • `http://localhost:8000/v1`에서 동작 중인 OpenAI‑호환 LLM 서버 (예: Ollama, LocalAI)  
> • 프로젝트 폴더에 위치한 입력 Word 문서 (`input.docx`)  

OpenAI를 직접 호출하는 대신 **맞춤형 모델**을 구축하는 이유가 궁금하시다면, 답은 유연성입니다: 엔드포인트를 직접 제어하고, 코드 변경 없이 모델을 교체할 수 있으며, API 키를 소스 저장소에 남기지 않을 수 있습니다. 이제 시작해 보겠습니다.

---

## 맞춤형 AI 모델 – 설정 및 구성

먼저 Aspose.Words에 LLM이 어디에 있는지 알려줘야 합니다. `AiModelEndpoint` 클래스는 URL과 선택적인 API 키를 보관합니다. 로컬 서버를 사용하므로 키는 빈 문자열로 두어도 되지만, 파라미터 자체는 필요합니다.

```java
import com.aspose.words.ai.*;

public class LlmDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Define the LLM endpoint (OpenAI‑compatible)
        AiModelEndpoint llmEndpoint = new AiModelEndpoint(
                "http://localhost:8000/v1",   // URL of your LLM server
                "my-api-key");                // API key if required
```

> **프로 팁:** 호스팅된 모델(예: Azure OpenAI)로 전환할 경우 URL과 키만 바꾸면 됩니다—다른 코드 수정은 필요 없습니다.

---

## Word 문서 로드

이제 소스 파일을 메모리로 가져옵니다. `Document`는 `.docx`, `.doc`, `.rtf` 등 다양한 포맷을 읽을 수 있지만, 이번 예제에서는 `.docx`만 사용합니다.

```java
        // Step 2: Load the source Word document
        Document document = new Document("YOUR_DIRECTORY/input.docx");
```

`YOUR_DIRECTORY`가 실제 폴더를 가리키도록 설정하세요. 그렇지 않으면 `FileNotFoundException`이 발생합니다. 실제 애플리케이션에서는 경로를 명령줄 인수로 전달하거나 설정 파일에서 읽어올 수도 있습니다.

---

## 맞춤형 AI 모델 초기화

`CUSTOM` 유형의 `AiModel`을 생성하고 앞서 정의한 엔드포인트를 전달합니다. 이렇게 하면 Aspose.Words가 모든 AI 호출을 우리 서버를 통해 라우팅합니다.

```java
        // Step 3: Create a custom AI model that uses the endpoint
        AiModel llmModel = new AiModel(AiModelType.CUSTOM, llmEndpoint);
```

내부적으로 Aspose.Words는 표준 OpenAI 채팅/완성 스키마를 사용해 LLM과 통신하는 작은 HTTP 클라이언트를 구축합니다. 그래서 엔드포인트는 반드시 *OpenAI‑호환*이어야 합니다.

---

## 첫 번째 단락 가져와서 재작성

이제 **텍스트를 더 공식적으로** 만들 차례입니다. 첫 번째 단락을 가져와 원본 텍스트와 프롬프트를 모델에 전달하고, 편집된 버전을 받습니다.

```java
        // Step 4: Retrieve the first paragraph and ask the model to rewrite it
        Paragraph firstParagraph = document.getFirstSection()
                                            .getBody()
                                            .getParagraphs()
                                            .get(0);
        String rewrittenText = llmModel.editText(
                firstParagraph.getText(),
                "Make it more formal");
```

두 번째 인수(`"Make it more formal"`)가 모델에 전달하는 지시문입니다. 이를 **단락 텍스트 교체**, **요약**, **번역** 등 원하는 명령으로 바꿀 수 있습니다. 메서드는 문자열을 반환하며, 이후 문서에 다시 삽입합니다.

> **동작 원리:** `editText`는 `{ "model": "...", "messages": [{ "role":"user", "content":"<text>\nMake it more formal"}] }`와 같은 JSON 페이로드를 전송합니다. LLM은 원본 단락과 지시문을 보고 수정된 텍스트를 반환합니다.

---

## 원본 단락 내용 교체

이제 Word 객체 모델 안에서 **단락 텍스트를 교체**합니다. 기존 `Run`(텍스트 조각)들을 모두 삭제하고, AI가 생성한 문자열을 포함하는 새로운 `Run`을 삽입합니다.

```java
        // Step 5: Replace the original paragraph content with the rewritten text
        firstParagraph.removeAllChildren();
        firstParagraph.appendChild(new Run(document, rewrittenText));
```

`firstParagraph.setText()`를 호출하면 서식이 모두 사라지니 주의하세요. `Run`을 사용하면 단락의 스타일(제목, 글머리표 등)은 유지하면서 실제 문자만 교체할 수 있습니다.

---

## 편집된 문서 저장

마지막으로 수정된 문서를 디스크에 기록합니다. 원본 파일을 덮어쓸 수도 있지만, 여기서는 새 파일을 생성합니다.

```java
        // Step 6: Save the edited document
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

`output.docx`를 열면 첫 번째 단락이 훨씬 더 공식적인 어조로 바뀐 것을 확인할 수 있습니다. LLM이 지시를 완벽히 따르지 않았다면 프롬프트를 조정하거나 다른 모델 버전을 시도해 보세요.

---

## 전체 작업 예제

아래는 완전한 프로그램 코드입니다—`LlmDemo.java`에 복사하고 경로만 수정한 뒤 `javac`와 `java`로 실행하면 됩니다.

```java
import com.aspose.words.*;
import com.aspose.words.ai.*;

public class LlmDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Define the LLM endpoint (OpenAI‑compatible)
        AiModelEndpoint llmEndpoint = new AiModelEndpoint(
                "http://localhost:8000/v1",   // URL of your LLM server
                "my-api-key");                // API key if required

        // Step 2: Load the source Word document
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // Step 3: Create a custom AI model that uses the endpoint
        AiModel llmModel = new AiModel(AiModelType.CUSTOM, llmEndpoint);

        // Step 4: Retrieve the first paragraph and ask the model to rewrite it
        Paragraph firstParagraph = document.getFirstSection()
                                            .getBody()
                                            .getParagraphs()
                                            .get(0);
        String rewrittenText = llmModel.editText(
                firstParagraph.getText(),
                "Make it more formal");

        // Step 5: Replace the original paragraph content with the rewritten text
        firstParagraph.removeAllChildren();
        firstParagraph.appendChild(new Run(document, rewrittenText));

        // Step 6: Save the edited document
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

**예상 출력:** `output.docx`를 열면 원본 단락이 변형된 것을 볼 수 있습니다. 예를 들어 “We’ll get the thing done soon.”이라는 캐주얼한 문장은 “We shall complete the task promptly.”와 같이 바뀔 수 있습니다. 정확한 문구는 사용 중인 모델에 따라 달라집니다.

---

## 자주 묻는 질문 및 예외 상황

### 문서에 섹션이 여러 개 있으면 어떻게 하나요?

위 코드는 *첫 번째 섹션*의 *첫 번째* 단락만 처리합니다. 전체 파일에 걸쳐 **AI로 단락 편집**을 수행하려면 `document.getSections()`를 순회하고, 각 `section.getBody().getParagraphs()`를 반복하세요. 빈 단락은 건너뛰어야 합니다—그렇지 않으면 LLM에 빈 문자열이 전달돼 아무 결과도 반환되지 않습니다.

### 토큰 제한을 초과하는 큰 단락은 어떻게 처리하나요?

대부분의 LLM은 입력을 약 4 000 토큰으로 제한합니다. 단락이 지나치게 길 경우, `editText` 호출 전에 작은 청크로 나누세요. 같은 `AiModel` 인스턴스를 재사용할 수 있지만, 로컬 서버의 속도 제한(rate limit)을 고려해야 합니다.

### “summarize”나 “translate to French” 같은 다른 지시문도 사용할 수 있나요?

물론입니다. `editText`의 두 번째 인수는 자유 형식입니다. 요약을 원한다면 `"Summarize in one sentence"`를, 번역을 원한다면 `"Translate to French, keep the tone formal"`과 같이 전달하면 됩니다. 이 유연성을 통해 **단락 텍스트 교체**를 다양한 시나리오에 적용할 수 있습니다.

### 모델이 단락 스타일(폰트, 색상)을 유지하나요?

우리는 동일한 `Paragraph` 객체 안의 `Run`만 교체하기 때문에 기존 스타일(제목 수준, 글머리표, 들여쓰기 등)은 그대로 유지됩니다. 스타일 자체를 바꾸고 싶다면 교체 후 `Paragraph.getParagraphFormat()`을 조작하면 됩니다.

### LLM 서버가 자체 서명 인증서가 있는 HTTPS를 요구한다면?

`AiModelEndpoint`는 `https://` URL을 허용합니다. 인증서가 신뢰되지 않을 경우 Java SSL 컨텍스트를 설정해 인증서를 신뢰하도록 하거나, 유효한 인증서를 가진 서버를 실행해야 합니다. 이 설정은 본 튜토리얼 범위를 벗어나지만, Java SSL 가이드에 잘 문서화되어 있습니다.

---

## 프로덕션 수준 통합을 위한 팁

| 팁 | 이유 |
|-----|------|
| **엔드포인트 캐시** | 매 요청마다 `AiModelEndpoint`를 새로 만들면 오버헤드가 발생합니다. |
| **배치 편집** | 단락이 많을 경우 단일 요청(예: JSON 배열)으로 보내면 지연 시간이 감소합니다. |
| **LLM 출력 검증** | 삽입 전에 반환된 문자열이 null이거나 비어 있는지 항상 확인하세요. |
| **프롬프트와 응답 로그** | 디버깅 및 법률 텍스트 재작성 시 컴플라이언스에 유용합니다. |
| **우아한 폴백** | LLM이 다운되면 원본 단락이나 간단한 휴리스틱 재작성으로 대체합니다. |

---

## 결론

Aspose.Words와 OpenAI‑호환 엔드포인트를 활용해 **맞춤형 AI 모델**을 만들고, **AI로 단락 편집**하여 텍스트를 더 공식적으로 바꾸는 방법을 살펴보았습니다. 엔드포인트 정의, 문서 로드, 모델 초기화, 첫 번째 단락 재작성, 내용 교체, 저장의 6단계를 따라 하면 됩니다.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}