---
"description": "Naučte se, jak spravovat digitální podpisy a zajistit pravost dokumentů pomocí Aspose.Words pro Python. Podrobný návod se zdrojovým kódem."
"linktitle": "Správa digitálních podpisů a autenticity"
"second_title": "API pro správu dokumentů Aspose.Words v Pythonu"
"title": "Správa digitálních podpisů a autenticity"
"url": "/cs/python-net/document-combining-and-comparison/manage-digital-signatures/"
"weight": 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Správa digitálních podpisů a autenticity

## Úvod do digitálních podpisů

Digitální podpisy slouží jako elektronické ekvivalenty ručně psaných podpisů. Poskytují způsob, jak ověřit pravost, integritu a původ elektronických dokumentů. Když je dokument digitálně podepsán, vygeneruje se na základě jeho obsahu kryptografický hash. Tento hash je poté zašifrován pomocí soukromého klíče podepisujícího, čímž vznikne digitální podpis. Kdokoli s odpovídajícím veřejným klíčem může ověřit podpis a zjistit pravost dokumentu.

## Nastavení Aspose.Words pro Python

Chcete-li začít se správou digitálních podpisů pomocí Aspose.Words pro Python, postupujte takto:

1. Instalace Aspose.Words: Aspose.Words pro Python můžete nainstalovat pomocí pipu s následujícím příkazem:
   
   ```python
   pip install aspose-words
   ```

2. Importujte požadované moduly: Importujte potřebné moduly do svého skriptu v Pythonu:
   
   ```python
   import aspose.words as aw
   ```

## Načítání a přístup k dokumentům

Před přidáním nebo ověřením digitálních podpisů je třeba načíst dokument pomocí Aspose.Words:

```python
document = aw.Document("document.docx")
```

## Přidávání digitálních podpisů do dokumentů

Chcete-li k dokumentu přidat digitální podpis, budete potřebovat digitální certifikát:

```python
certificate_holder = aw.digitalsignatures.CertificateHolder.create("certificate.pfx", "password")
```

Nyní podepište dokument:

```python
aw.digitalsignatures.DigitalSignatureUtil.sign(MY_DIR + "Digitally signed.docx",
            ARTIFACTS_DIR + "Document.encrypted_document.docx", cert_holder, sign_options)
```

## Ověřování digitálních podpisů

Ověřte pravost podepsaného dokumentu pomocí Aspose.Words:

```python
for signature in document.digital_signatures:
    if signature.is_valid:
        print("Signature is valid.")
    else:
        print("Signature is invalid.")
```

## Přizpůsobení vzhledu digitálního podpisu

Vzhled digitálních podpisů si můžete přizpůsobit:

```python
sign_options = aw.digitalsignatures.SignOptions()
sign_options.comments = 'Comment'
sign_options.sign_time = datetime.datetime.now()
```

## Závěr

Správa digitálních podpisů a zajištění pravosti dokumentů jsou v dnešní digitální krajině klíčové. Aspose.Words pro Python zjednodušuje proces přidávání, ověřování a úpravy digitálních podpisů a umožňuje vývojářům zvýšit zabezpečení a důvěryhodnost jejich dokumentů.

## Často kladené otázky

### Jak fungují digitální podpisy?

Digitální podpisy používají kryptografii k vygenerování jedinečného hashe na základě obsahu dokumentu, zašifrovaného soukromým klíčem podepisujícího.

### Lze digitálně podepsaný dokument pozměnit?

Ne, manipulace s digitálně podepsaným dokumentem by zneplatnila podpis, což by naznačovalo možné neoprávněné změny.

### Lze do jednoho dokumentu přidat více podpisů?

Ano, do jednoho dokumentu můžete přidat více digitálních podpisů, každý od jiného podepisujícího.

### Jaké typy certifikátů jsou kompatibilní?

Aspose.Words podporuje certifikáty X.509, včetně souborů PFX, které se běžně používají pro digitální podpisy.

### Jsou digitální podpisy právně platné?

Ano, digitální podpisy jsou v mnoha zemích právně platné a často jsou považovány za rovnocenné ručně psaným podpisům.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}