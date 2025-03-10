---
title: Správa digitálních podpisů a pravosti
linktitle: Správa digitálních podpisů a pravosti
second_title: Aspose.Words Python Document Management API
description: Naučte se spravovat digitální podpisy a zajistit pravost dokumentů pomocí Aspose.Words pro Python. Průvodce krok za krokem se zdrojovým kódem.
weight: 17
url: /cs/python-net/document-combining-and-comparison/manage-digital-signatures/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Správa digitálních podpisů a pravosti

## Úvod do digitálních podpisů

Digitální podpisy slouží jako elektronické ekvivalenty vlastnoručních podpisů. Poskytují způsob, jak ověřit pravost, integritu a původ elektronických dokumentů. Když je dokument digitálně podepsán, je na základě obsahu dokumentu vygenerován kryptografický hash. Tento hash je poté zašifrován pomocí soukromého klíče podepisujícího, čímž se vytvoří digitální podpis. Každý, kdo má odpovídající veřejný klíč, může ověřit podpis a zjistit pravost dokumentu.

## Nastavení Aspose.Words pro Python

Chcete-li začít se správou digitálních podpisů pomocí Aspose.Words pro Python, postupujte takto:

1. Instalace Aspose.Words: Aspose.Words pro Python můžete nainstalovat pomocí pip s následujícím příkazem:
   
   ```python
   pip install aspose-words
   ```

2. Import požadovaných modulů: Importujte potřebné moduly do skriptu Python:
   
   ```python
   import aspose.words as aw
   ```

## Načítání a přístup k dokumentům

Před přidáním nebo ověřením digitálních podpisů musíte načíst dokument pomocí Aspose.Words:

```python
document = aw.Document("document.docx")
```

## Přidávání digitálních podpisů do dokumentů

Chcete-li do dokumentu přidat digitální podpis, budete potřebovat digitální certifikát:

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

Správa digitálních podpisů a zajištění pravosti dokumentů jsou v dnešním digitálním prostředí zásadní. Aspose.Words for Python zjednodušuje proces přidávání, ověřování a přizpůsobení digitálních podpisů a umožňuje vývojářům zvýšit bezpečnost a důvěryhodnost jejich dokumentů.

## FAQ

### Jak fungují digitální podpisy?

Digitální podpisy využívají kryptografii ke generování jedinečného hash na základě obsahu dokumentu, zašifrovaného soukromým klíčem podepisujícího.

### Lze s digitálně podepsaným dokumentem manipulovat?

Ne, manipulace s digitálně podepsaným dokumentem by zneplatnila podpis, což by znamenalo možné neoprávněné změny.

### Lze k jednomu dokumentu přidat více podpisů?

Ano, k jednomu dokumentu můžete přidat více digitálních podpisů, každý od jiného podepisujícího.

### Jaké typy certifikátů jsou kompatibilní?

Aspose.Words podporuje certifikáty X.509, včetně souborů PFX, které se běžně používají pro digitální podpisy.

### Jsou digitální podpisy právně platné?

Ano, digitální podpisy jsou v mnoha zemích právně platné a často jsou považovány za rovnocenné s vlastnoručním podpisem.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
