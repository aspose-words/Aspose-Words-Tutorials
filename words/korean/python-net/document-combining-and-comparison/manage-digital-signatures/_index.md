---
"description": "Aspose.Words for Python을 사용하여 디지털 서명을 관리하고 문서의 진위성을 보장하는 방법을 알아보세요. 소스 코드가 포함된 단계별 가이드입니다."
"linktitle": "디지털 서명 및 진위성 관리"
"second_title": "Aspose.Words Python 문서 관리 API"
"title": "디지털 서명 및 진위성 관리"
"url": "/ko/python-net/document-combining-and-comparison/manage-digital-signatures/"
"weight": 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 디지털 서명 및 진위성 관리

## 디지털 서명 소개

디지털 서명은 수기 서명과 동일한 전자적 기능을 합니다. 디지털 서명은 전자 문서의 진위성, 무결성, 그리고 출처를 확인하는 방법을 제공합니다. 문서에 디지털 서명이 이루어지면 문서의 내용을 기반으로 암호화 해시가 생성됩니다. 이 해시는 서명자의 개인 키를 사용하여 암호화되어 디지털 서명을 생성합니다. 해당 공개 키를 가진 사람은 누구나 서명을 검증하고 문서의 진위 여부를 확인할 수 있습니다.

## Python용 Aspose.Words 설정

Python용 Aspose.Words를 사용하여 디지털 서명 관리를 시작하려면 다음 단계를 따르세요.

1. Aspose.Words 설치: 다음 명령어를 사용하여 pip를 사용하여 Python용 Aspose.Words를 설치할 수 있습니다.
   
   ```python
   pip install aspose-words
   ```

2. 필수 모듈 가져오기: Python 스크립트에 필요한 모듈을 가져옵니다.
   
   ```python
   import aspose.words as aw
   ```

## 문서 로딩 및 액세스

디지털 서명을 추가하거나 확인하기 전에 Aspose.Words를 사용하여 문서를 로드해야 합니다.

```python
document = aw.Document("document.docx")
```

## 문서에 디지털 서명 추가

문서에 디지털 서명을 추가하려면 디지털 인증서가 필요합니다.

```python
certificate_holder = aw.digitalsignatures.CertificateHolder.create("certificate.pfx", "password")
```

이제 문서에 서명하세요.

```python
aw.digitalsignatures.DigitalSignatureUtil.sign(MY_DIR + "Digitally signed.docx",
            ARTIFACTS_DIR + "Document.encrypted_document.docx", cert_holder, sign_options)
```

## 디지털 서명 확인

Aspose.Words를 사용하여 서명된 문서의 진위 여부를 확인하세요.

```python
for signature in document.digital_signatures:
    if signature.is_valid:
        print("Signature is valid.")
    else:
        print("Signature is invalid.")
```

## 디지털 서명 모양 사용자 지정

디지털 서명의 모양을 사용자 정의할 수 있습니다.

```python
sign_options = aw.digitalsignatures.SignOptions()
sign_options.comments = 'Comment'
sign_options.sign_time = datetime.datetime.now()
```

## 결론

오늘날의 디지털 환경에서는 디지털 서명을 관리하고 문서의 신뢰성을 보장하는 것이 매우 중요합니다. Aspose.Words for Python은 디지털 서명을 추가, 검증 및 사용자 지정하는 과정을 간소화하여 개발자가 문서의 보안과 신뢰성을 강화할 수 있도록 지원합니다.

## 자주 묻는 질문

### 디지털 서명은 어떻게 작동하나요?

디지털 서명은 암호화를 사용하여 서명자의 개인 키로 암호화된 문서의 내용을 기반으로 고유한 해시를 생성합니다.

### 디지털로 서명된 문서가 변조될 수 있나요?

아니요. 디지털로 서명된 문서를 변조하면 서명이 무효화되어 무단 변경이 발생할 가능성이 있습니다.

### 하나의 문서에 여러 개의 서명을 추가할 수 있나요?

네, 하나의 문서에 다른 서명자의 여러 디지털 서명을 추가할 수 있습니다.

### 어떤 유형의 인증서가 호환됩니까?

Aspose.Words는 디지털 서명에 일반적으로 사용되는 PFX 파일을 포함한 X.509 인증서를 지원합니다.

### 디지털 서명은 법적으로 유효합니까?

네, 디지털 서명은 많은 국가에서 법적으로 유효하며 종종 손으로 쓴 서명과 동일한 것으로 간주됩니다.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}