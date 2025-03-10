---
title: Gestione delle firme digitali e dell'autenticità
linktitle: Gestione delle firme digitali e dell'autenticità
second_title: API di gestione dei documenti Python Aspose.Words
description: Scopri come gestire le firme digitali e garantire l'autenticità dei documenti utilizzando Aspose.Words per Python. Guida passo passo con codice sorgente.
weight: 17
url: /it/python-net/document-combining-and-comparison/manage-digital-signatures/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Gestione delle firme digitali e dell'autenticità

## Introduzione alle firme digitali

Le firme digitali servono come equivalenti elettronici delle firme manoscritte. Forniscono un modo per verificare l'autenticità, l'integrità e l'origine dei documenti elettronici. Quando un documento è firmato digitalmente, viene generato un hash crittografico basato sul contenuto del documento. Questo hash viene quindi crittografato utilizzando la chiave privata del firmatario, creando la firma digitale. Chiunque abbia la chiave pubblica corrispondente può verificare la firma e accertare l'autenticità del documento.

## Impostazione di Aspose.Words per Python

Per iniziare a gestire le firme digitali utilizzando Aspose.Words per Python, segui questi passaggi:

1. Installa Aspose.Words: puoi installare Aspose.Words per Python utilizzando pip con il seguente comando:
   
   ```python
   pip install aspose-words
   ```

2. Importa i moduli necessari: importa i moduli necessari nel tuo script Python:
   
   ```python
   import aspose.words as aw
   ```

## Caricamento e accesso ai documenti

Prima di aggiungere o verificare le firme digitali, è necessario caricare il documento utilizzando Aspose.Words:

```python
document = aw.Document("document.docx")
```

## Aggiungere firme digitali ai documenti

Per aggiungere una firma digitale a un documento, avrai bisogno di un certificato digitale:

```python
certificate_holder = aw.digitalsignatures.CertificateHolder.create("certificate.pfx", "password")
```

Ora firma il documento:

```python
aw.digitalsignatures.DigitalSignatureUtil.sign(MY_DIR + "Digitally signed.docx",
            ARTIFACTS_DIR + "Document.encrypted_document.docx", cert_holder, sign_options)
```

## Verifica delle firme digitali

Verificare l'autenticità di un documento firmato utilizzando Aspose.Words:

```python
for signature in document.digital_signatures:
    if signature.is_valid:
        print("Signature is valid.")
    else:
        print("Signature is invalid.")
```

## Personalizzazione dell'aspetto della firma digitale

È possibile personalizzare l'aspetto delle firme digitali:

```python
sign_options = aw.digitalsignatures.SignOptions()
sign_options.comments = 'Comment'
sign_options.sign_time = datetime.datetime.now()
```

## Conclusione

La gestione delle firme digitali e la garanzia dell'autenticità dei documenti sono essenziali nel panorama digitale odierno. Aspose.Words per Python semplifica il processo di aggiunta, verifica e personalizzazione delle firme digitali, consentendo agli sviluppatori di migliorare la sicurezza e l'affidabilità dei loro documenti.

## Domande frequenti

### Come funzionano le firme digitali?

Le firme digitali utilizzano la crittografia per generare un hash univoco basato sul contenuto del documento, crittografato con la chiave privata del firmatario.

### Un documento firmato digitalmente può essere manomesso?

No, la manomissione di un documento firmato digitalmente invaliderebbe la firma, il che indica potenziali modifiche non autorizzate.

### È possibile aggiungere più firme a un singolo documento?

Sì, è possibile aggiungere più firme digitali a un singolo documento, ciascuna da un firmatario diverso.

### Quali tipi di certificati sono compatibili?

Aspose.Words supporta i certificati X.509, inclusi i file PFX, comunemente utilizzati per le firme digitali.

### Le firme digitali sono legalmente valide?

Sì, le firme digitali sono legalmente valide in molti Paesi e sono spesso considerate equivalenti alle firme autografe.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
