---
"description": "Aprenda a gestionar firmas digitales y garantizar la autenticidad de documentos con Aspose.Words para Python. Guía paso a paso con código fuente."
"linktitle": "Gestión de firmas digitales y autenticidad"
"second_title": "API de gestión de documentos de Python de Aspose.Words"
"title": "Gestión de firmas digitales y autenticidad"
"url": "/es/python-net/document-combining-and-comparison/manage-digital-signatures/"
"weight": 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Gestión de firmas digitales y autenticidad

## Introducción a las firmas digitales

Las firmas digitales son el equivalente electrónico de las firmas manuscritas. Permiten verificar la autenticidad, integridad y origen de los documentos electrónicos. Cuando un documento se firma digitalmente, se genera un hash criptográfico basado en su contenido. Este hash se cifra con la clave privada del firmante, creando así la firma digital. Cualquier persona con la clave pública correspondiente puede verificar la firma y comprobar la autenticidad del documento.

## Configuración de Aspose.Words para Python

Para comenzar a administrar firmas digitales con Aspose.Words para Python, siga estos pasos:

1. Instalar Aspose.Words: puedes instalar Aspose.Words para Python usando pip con el siguiente comando:
   
   ```python
   pip install aspose-words
   ```

2. Importe los módulos necesarios: Importe los módulos necesarios en su script de Python:
   
   ```python
   import aspose.words as aw
   ```

## Carga y acceso a documentos

Antes de agregar o verificar firmas digitales, debe cargar el documento utilizando Aspose.Words:

```python
document = aw.Document("document.docx")
```

## Cómo agregar firmas digitales a los documentos

Para agregar una firma digital a un documento, necesitará un certificado digital:

```python
certificate_holder = aw.digitalsignatures.CertificateHolder.create("certificate.pfx", "password")
```

Ahora, firma el documento:

```python
aw.digitalsignatures.DigitalSignatureUtil.sign(MY_DIR + "Digitally signed.docx",
            ARTIFACTS_DIR + "Document.encrypted_document.docx", cert_holder, sign_options)
```

## Verificación de firmas digitales

Verifique la autenticidad de un documento firmado usando Aspose.Words:

```python
for signature in document.digital_signatures:
    if signature.is_valid:
        print("Signature is valid.")
    else:
        print("Signature is invalid.")
```

## Personalización de la apariencia de la firma digital

Puede personalizar la apariencia de las firmas digitales:

```python
sign_options = aw.digitalsignatures.SignOptions()
sign_options.comments = 'Comment'
sign_options.sign_time = datetime.datetime.now()
```

## Conclusión

Gestionar firmas digitales y garantizar la autenticidad de los documentos es fundamental en el panorama digital actual. Aspose.Words para Python simplifica el proceso de añadir, verificar y personalizar firmas digitales, lo que permite a los desarrolladores mejorar la seguridad y la fiabilidad de sus documentos.

## Preguntas frecuentes

### ¿Cómo funcionan las firmas digitales?

Las firmas digitales utilizan criptografía para generar un hash único basado en el contenido del documento, cifrado con la clave privada del firmante.

### ¿Se puede manipular un documento firmado digitalmente?

No, alterar un documento firmado digitalmente invalidaría la firma, lo que indicaría posibles cambios no autorizados.

### ¿Se pueden agregar varias firmas a un solo documento?

Sí, puedes agregar varias firmas digitales a un solo documento, cada una de un firmante diferente.

### ¿Qué tipos de certificados son compatibles?

Aspose.Words admite certificados X.509, incluidos archivos PFX, que se utilizan comúnmente para firmas digitales.

### ¿Son legalmente válidas las firmas digitales?

Sí, las firmas digitales son legalmente válidas en muchos países y a menudo se consideran equivalentes a las firmas manuscritas.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}