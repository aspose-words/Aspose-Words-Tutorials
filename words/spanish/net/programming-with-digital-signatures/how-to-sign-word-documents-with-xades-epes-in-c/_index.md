---
category: general
date: 2026-09-08
description: Cómo firmar documentos Word usando un flujo de trabajo de firma digital
  docx, cargar el certificado pfx y crear una firma XAdES en C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to sign word
- digital signature docx
- load pfx certificate
- digitally sign word
- create xades signature
language: es
lastmod: 2026-09-08
og_description: Cómo firmar documentos Word usando un flujo de firma digital docx,
  cargar un certificado pfx y crear una firma XAdES en C#. Sigue el ejemplo completo.
og_image_alt: Screenshot showing a Word document signed with XAdES EPES digital signature
og_title: Cómo firmar documentos Word con XAdES EPES en C# – guía paso a paso
schemas:
- author: GroupDocs
  dateModified: '2026-09-08'
  description: How to sign word documents using a digital signature docx workflow,
    load pfx certificate, and create XAdES signature in C#.
  headline: How to sign word documents with XAdES EPES in C#
  type: TechArticle
tags:
- digital-signature
- C#
- Word
- XAdES
title: Cómo firmar documentos Word con XAdES EPES en C#
url: /es/net/programming-with-digital-signatures/how-to-sign-word-documents-with-xades-epes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo firmar documentos de Word con XAdES EPES en C#

Si necesitas **how to sign word** archivos programáticamente, esta guía te muestra una solución completa y lista para producción. Aprenderás cómo cargar un certificado PFX, configurar un **digital signature docx**, y crear una firma XAdES‑EPES que puede ser verificada por Microsoft Word y validadores de terceros.

El ejemplo utiliza la biblioteca GroupDocs.Signature para .NET, pero los conceptos se aplican a cualquier API que soporte XAdES. Al final del tutorial tendrás un `Signed_XAdES_EPES.docx` firmado listo para distribución.

## Lo que necesitarás

- .NET 6.0 o posterior (el código también funciona con .NET Framework 4.7+)
- Un archivo de certificado PFX válido (`.pfx`) que contenga una clave privada
- La contraseña del archivo PFX
- Un documento Word (`.docx`) que deseas firmar
- Paquete NuGet **GroupDocs.Signature** (instalar con `dotnet add package GroupDocs.Signature`)

## Paso 1: Instalar el paquete NuGet requerido

```bash
dotnet add package GroupDocs.Signature
```

El paquete proporciona la clase `Document`, `XadesSignatureOptions`, y tipos auxiliares para crear un archivo **digitally sign word**.

## Paso 2: Cargar el documento Word sin firmar

```csharp
using GroupDocs.Signature;
using GroupDocs.Signature.Options;
using System;
using System.Security.Cryptography.X509Certificates;

...

// Load the original Word file (must be a .docx)
var documentPath = @"C:\Docs\Unsigned.docx";
Document document = new Document(documentPath);
```

Cargar el documento te brinda un modelo de objetos que puedes manipular antes de aplicar la firma.

## Paso 3: Cargar el certificado PFX (load pfx certificate)

```csharp
// Load the certificate that holds the private key
var certPath = @"C:\Certificates\mycert.pfx";
var certPassword = "yourPassword";          // keep this secret!
X509Certificate2 certificate = new X509Certificate2(certPath, certPassword);
```

> **Consejo profesional:** Si el certificado está almacenado en el almacén de certificados de Windows, puedes recuperarlo con `X509Store` en lugar de cargar un archivo. El enfoque `load pfx certificate` funciona en cualquier plataforma, incluidos contenedores Linux.

## Paso 4: (Opcional) Añadir una línea de firma visual

Una pista visual ayuda a los destinatarios a ver dónde aparece la firma en Word.

```csharp
// Create a signature line that will be displayed in the document
SignatureLine signatureLine = new SignatureLine(document);
signatureLine.Id = Guid.NewGuid().ToString();
signatureLine.Signer = "John Smith";
signatureLine.Title = "Approved";

// Append the line to the first paragraph of the first section
document.FirstSection.Body.FirstParagraph.AppendChild(signatureLine);
```

Si prefieres una firma invisible, puedes omitir este paso. El **digital signature docx** seguirá siendo criptográficamente válido.

## Paso 5: Configurar opciones XAdES‑EPES (create xades signature)

```csharp
// Set up XAdES‑EPES options – this creates a “qualified” electronic signature
XadesSignatureOptions signOptions = new XadesSignatureOptions
{
    SignatureType = XadesSignatureType.XAdES_EPES,
    // Optional: add a custom signing reason or location
    Reason = "Document approval",
    Location = "New York, USA"
};
```

La bandera `XadesSignatureType.XAdES_EPES` indica a la biblioteca que incruste la firma según el perfil EPES (Explicit Policy-based Electronic Signature), que es ampliamente aceptado por las regulaciones EU e‑IDAS.

## Paso 6: Aplicar la firma digital

```csharp
// Sign the document with the loaded certificate and options
document.DigitalSignatures.Sign(certificate, signOptions);
```

El método `Sign` realiza todo el trabajo criptográfico: genera los hashes de las partes del documento, crea la estructura XML‑DSig y inserta el sobre XAdES en el archivo Word.

## Paso 7: Guardar el documento firmado

```csharp
// Save the signed file – you can overwrite or create a new file
var signedPath = @"C:\Docs\Signed_XAdES_EPES.docx";
document.Save(signedPath);
Console.WriteLine($"Document signed and saved to: {signedPath}");
```

Después de guardar, abre `Signed_XAdES_EPES.docx` en Microsoft Word. Deberías ver una línea de firma (si añadiste una) y una barra de estado **digitally sign word** que indica que el archivo está firmado y la firma es válida.

## Ejemplo completo y ejecutable

A continuación se muestra el programa completo que puedes copiar y pegar en una aplicación de consola.

```csharp
using System;
using System.Security.Cryptography.X509Certificates;
using GroupDocs.Signature;
using GroupDocs.Signature.Options;

namespace WordXadesSigner
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the unsigned Word document
            string docPath = @"C:\Docs\Unsigned.docx";
            Document document = new Document(docPath);

            // 2️⃣ Load the signing certificate (load pfx certificate)
            string pfxPath = @"C:\Certificates\mycert.pfx";
            string pfxPassword = "yourPassword";
            X509Certificate2 cert = new X509Certificate2(pfxPath, pfxPassword);

            // 3️⃣ (Optional) Add a visual signature line
            SignatureLine sigLine = new SignatureLine(document)
            {
                Id = Guid.NewGuid().ToString(),
                Signer = "John Smith",
                Title = "Approved"
            };
            document.FirstSection.Body.FirstParagraph.AppendChild(sigLine);

            // 4️⃣ Configure XAdES‑EPES options (create xades signature)
            XadesSignatureOptions xadesOptions = new XadesSignatureOptions
            {
                SignatureType = XadesSignatureType.XAdES_EPES,
                Reason = "Document approval",
                Location = "New York, USA"
            };

            // 5️⃣ Apply the digital signature (digitally sign word)
            document.DigitalSignatures.Sign(cert, xadesOptions);

            // 6️⃣ Save the signed document
            string signedPath = @"C:\Docs\Signed_XAdES_EPES.docx";
            document.Save(signedPath);

            Console.WriteLine($"Signed document saved to: {signedPath}");
        }
    }
}
```

### Salida esperada

```
Signed document saved to: C:\Docs\Signed_XAdES_EPES.docx
```

Al abrir el archivo en Word se muestra una pancarta verde “Signed” y, si añadiste la línea visual, la línea de firma aparece en la ubicación que especificaste.

## Manejo de problemas comunes

| Problema | Por qué ocurre | Solución |
|----------|----------------|----------|
| **La contraseña del certificado es incorrecta** | El constructor `X509Certificate2` lanza una `CryptographicException`. | Verifica la contraseña, o usa un gestor de secretos seguro (Azure Key Vault, AWS Secrets Manager). |
| **Word muestra “Signature is invalid”** | El documento fue alterado después de la firma, o falta la política de firma. | Asegúrate de que el archivo se guarde **después** de firmar y no se edite nuevamente. Inserta la política XAdES correcta si tu regulador lo requiere. |
| **La línea de firma no es visible** | El documento usa un diseño de sección diferente. | Añade el `SignatureLine` al párrafo correcto o crea un nuevo párrafo antes de agregarlo. |
| **Ralentización del rendimiento en documentos grandes** | Las firmas XAdES generan hash de cada parte del paquete. | Usa APIs de streaming (`SignAsync`) o incrementa los recursos de la máquina para archivos muy grandes (>50 MB). |

## Extender la solución

- **Multiple signers** – llama a `Sign` repetidamente con diferentes certificados y establece `SignatureId` para diferenciar cada firmante.
- **Timestamping** – añade un objeto `TimestampOptions` a `XadesSignatureOptions` para incrustar una marca de tiempo confiable.
- **Custom policies** – proporciona un archivo de política XML mediante `XadesSignatureOptions.PolicyFilePath` para cumplir con estándares específicos.

## Conclusión

Ahora sabes **how to sign word** documentos programáticamente, cómo **load pfx certificate**, y cómo **create xades signature** usando GroupDocs.Signature. El tutorial cubrió cada paso, desde cargar el documento hasta guardar la salida firmada, con consejos prácticos para casos comunes.  

A continuación, explora temas relacionados como PDFs **digitally sign word**, integrar la verificación **digital signature docx**, o añadir soporte de **timestamp** para cumplir con requisitos de cumplimiento avanzados. ¡Feliz firma!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Detect Digital Signature on Word Document](/words/english/net/programming-with-fileformat/detect-document-signatures/)
- [Signing Existing Signature Line In Word Document](/words/english/net/programming-with-digital-signatures/signing-existing-signature-line/)
- [Access And Verify Signature In Word Document](/words/english/net/programming-with-digital-signatures/access-and-verify-signature/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}