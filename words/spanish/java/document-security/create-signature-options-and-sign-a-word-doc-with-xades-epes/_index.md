---
category: general
date: 2026-10-10
description: Crea opciones de firma y firma un documento Word usando XAdES EPES en
  Java. Aprende cómo firmar un documento de Office con un certificado en unos pocos
  pasos claros.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create signature options
- sign word doc
- sign office document
- how to sign docx
language: es
lastmod: 2026-10-10
og_description: Crea opciones de firma y firma un documento Word usando XAdES EPES
  en Java. Esta guía te muestra cómo firmar un documento de Office de forma segura
  con un certificado.
og_image_alt: Screenshot of Java code that creates signature options and signs a DOCX
  file
og_title: Crear opciones de firma y firmar un documento Word con XAdES EPES
schemas:
- author: GroupDocs
  dateModified: '2026-10-10'
  description: Create signature options and sign a Word doc using XAdES EPES in Java.
    Learn how to sign office document with a certificate in a few clear steps.
  headline: Create signature options and sign a Word doc with XAdES EPES
  type: TechArticle
- description: Create signature options and sign a Word doc using XAdES EPES in Java.
    Learn how to sign office document with a certificate in a few clear steps.
  name: Create signature options and sign a Word doc with XAdES EPES
  steps:
  - name: The library loads the `.pfx` file and extracts the private key using the
      supplied password.
    text: The library loads the `.pfx` file and extracts the private key using the
      supplied password.
  - name: It creates an XML‑DSig structure matching the XAdES‑EPES profile.
    text: It creates an XML‑DSig structure matching the XAdES‑EPES profile.
  - name: The signature is embedded into the DOCX package, preserving the original
      document layout.
    text: The signature is embedded into the DOCX package, preserving the original
      document layout.
  - name: Open `SignedXades.docx` in Word.
    text: Open `SignedXades.docx` in Word.
  - name: Click **File → Info → View signatures**.
    text: Click **File → Info → View signatures**.
  - name: Word should display a green checkmark indicating a valid digital signature.
    text: Word should display a green checkmark indicating a valid digital signature.
  type: HowTo
tags:
- digital signature
- Java
- XAdES
title: Crear opciones de firma y firmar un documento Word con XAdES EPES
url: /es/java/document-security/create-signature-options-and-sign-a-word-doc-with-xades-epes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear opciones de firma y firmar un documento Word con XAdES EPES

Si necesitas **crear opciones de firma** para un archivo DOCX, esta guía te muestra cómo firmar un documento Word usando el nivel XAdES‑EPES en Java. Obtendrás un ejemplo completo y ejecutable que firma un documento Office con un certificado PFX en solo unas pocas líneas de código.

Firmar documentos Office es un requisito común para flujos de trabajo legales, procesamiento automatizado de contratos e intercambio seguro de documentos. En este tutorial aprenderás:

* Cómo configurar `SignatureOptions` para XAdES‑EPES.  
* Cómo llamar a `DigitalSignatureUtil.sign` para **firmar documentos Word**.  
* Cómo manejar problemas comunes como la carga del certificado y errores de contraseña.

> **Prerequisite** – Java 17 o posterior, la biblioteca GroupDocs.Signature for Java (o una biblioteca XAdES compatible), y un archivo de certificado `.pfx` válido.

---

## Lo que necesitarás

| Elemento | Razón |
|----------|-------|
| Java 17+ | Características modernas del lenguaje y mejores API de seguridad |
| GroupDocs.Signature for Java (o equivalente) | Proporciona `SignatureOptions`, `XmlDsigLevel` y `DigitalSignatureUtil` |
| Un certificado PFX (`.pfx`) | Proporciona la clave privada para la firma digital |
| Contraseña del certificado | Necesaria para desbloquear la clave privada |
| Un archivo DOCX sin firmar (`Unsigned.docx`) | El documento fuente que deseas **firmar documento office** |

Asegúrate de que el JAR de la biblioteca esté en tu classpath:

```bash
# Example using Maven
mvn dependency:copy -Dartifact=com.groupdocs:groupdocs-signature:23.3
```

---

## Paso 1: Importar las clases requeridas

Comienza importando las clases que manejan firmas y entrada/salida de archivos.

```java
import com.groupdocs.signature.SignatureOptions;
import com.groupdocs.signature.XmlDsigLevel;
import com.groupdocs.signature.DigitalSignatureUtil;
import java.io.IOException;
```

Estas importaciones te dan acceso a la API usada para **crear opciones de firma** y para realizar la operación de firma real.

---

## Paso 2: Crear opciones de firma

El objeto `SignatureOptions` contiene toda la configuración necesaria para el proceso de firma, como el nivel de firma, la apariencia visual y la configuración de marca de tiempo.

```java
// Step 2: Create signature options
SignatureOptions signatureOptions = new SignatureOptions();
```

Crear una nueva instancia de `SignatureOptions` es el primer paso en **cómo firmar docx** porque aísla cada solicitud de firma, evitando efectos secundarios entre documentos.

---

## Paso 3: Especificar el nivel de firma XAdES EPES

XAdES‑EPES (Firma Electrónica basada en Política Explícita) es una política ampliamente aceptada para firmas de documentos Office. Establecer el nivel indica a la biblioteca qué perfil criptográfico usar.

```java
// Step 3: Specify the XAdES EPES signature level
signatureOptions.setXmlDsigLevel(XmlDsigLevel.XAdES_EPES);
```

¿Por qué XAdES‑EPES? Inserta la política de firma directamente en la firma, haciendo que el documento firmado sea autónomo y cumpla con muchas regulaciones de firma electrónica.

---

## Paso 4: Firmar el archivo DOCX

Ahora invoca `DigitalSignatureUtil.sign`. Este método lee el archivo fuente, aplica la firma y escribe la salida firmada.

```java
// Step 4: Sign the document using the provided certificate
try {
    DigitalSignatureUtil.sign(
        "YOUR_DIRECTORY/Unsigned.docx",   // input file
        "YOUR_DIRECTORY/SignedXades.docx", // output file
        "YOUR_DIRECTORY/mycert.pfx",      // certificate file
        "password",                       // certificate password
        signatureOptions                  // options configured above
    );
    System.out.println("Document signed successfully: SignedXades.docx");
} catch (IOException e) {
    System.err.println("Failed to sign the document: " + e.getMessage());
}
```

**¿Qué ocurre internamente?**  
1. La biblioteca carga el archivo `.pfx` y extrae la clave privada usando la contraseña proporcionada.  
2. Crea una estructura XML‑DSig que coincide con el perfil XAdES‑EPES.  
3. La firma se incrusta en el paquete DOCX, preservando el diseño original del documento.  

Si la contraseña del certificado es incorrecta o el archivo no se puede leer, se lanza una `IOException`, que deberías manejar como se muestra.

---

## Paso 5: Verificar el documento firmado (opcional)

Después de firmar, puede que quieras confirmar que la firma está presente y es válida. GroupDocs ofrece una API de verificación, pero una rápida comprobación manual se puede hacer con Microsoft Word:

1. Abre `SignedXades.docx` en Word.  
2. Haz clic en **Archivo → Información → Ver firmas**.  
3. Word debería mostrar una marca de verificación verde que indica una firma digital válida.

La verificación automatizada con la biblioteca se ve así:

```java
import com.groupdocs.signature.VerificationResult;

VerificationResult result = DigitalSignatureUtil.verify(
    "YOUR_DIRECTORY/SignedXades.docx",
    signatureOptions
);

if (result.isSuccessful()) {
    System.out.println("Signature verification succeeded.");
} else {
    System.out.println("Signature verification failed: " + result.getErrorMessage());
}
```

Ejecutar el paso de verificación te brinda confianza programática de que **firmar documento office** se completó con éxito.

---

## Ejemplo completo y ejecutable

Uniendo todas las piezas, aquí tienes una clase Java autónoma que puedes copiar, pegar y ejecutar.

```java
import com.groupdocs.signature.SignatureOptions;
import com.groupdocs.signature.XmlDsigLevel;
import com.groupdocs.signature.DigitalSignatureUtil;
import com.groupdocs.signature.VerificationResult;
import java.io.IOException;

/**
 * Demonstrates how to create signature options and sign a DOCX file with XAdES EPES.
 */
public class XadesSignatureDemo {

    public static void main(String[] args) {
        // Paths – update these to match your environment
        String inputPath = "YOUR_DIRECTORY/Unsigned.docx";
        String outputPath = "YOUR_DIRECTORY/SignedXades.docx";
        String certPath = "YOUR_DIRECTORY/mycert.pfx";
        String certPassword = "password";

        // 1️⃣ Create signature options
        SignatureOptions signatureOptions = new SignatureOptions();

        // 2️⃣ Set XAdES EPES level
        signatureOptions.setXmlDsigLevel(XmlDsigLevel.XAdES_EPES);

        // 3️⃣ Sign the document
        try {
            DigitalSignatureUtil.sign(inputPath, outputPath, certPath, certPassword, signatureOptions);
            System.out.println("Document signed successfully: " + outputPath);
        } catch (IOException e) {
            System.err.println("Signing failed: " + e.getMessage());
            return;
        }

        // 4️⃣ (Optional) Verify the signature
        VerificationResult verification = DigitalSignatureUtil.verify(outputPath, signatureOptions);
        if (verification.isSuccessful()) {
            System.out.println("Signature verification succeeded.");
        } else {
            System.out.println("Signature verification failed: " + verification.getErrorMessage());
        }
    }
}
```

**Salida esperada**

```
Document signed successfully: YOUR_DIRECTORY/SignedXades.docx
Signature verification succeeded.
```

Si ocurre algún error, la consola mostrará un mensaje claro, ayudándote a solucionar problemas de certificado o rutas de archivo.

---

## Preguntas frecuentes y manejo de casos límite

| Pregunta | Respuesta |
|----------|-----------|
| **¿Puedo usar un nivel de firma diferente?** | Sí. Reemplaza `XmlDsigLevel.XAdES_EPES` por `XAdES_BES`, `XAdES_T`, etc., según los requisitos de cumplimiento. |
| **¿Qué pasa si mi certificado está almacenado en un keystore en lugar de un archivo .pfx?** | Carga el `KeyStore` manualmente, extrae el `PrivateKey` y el `Certificate`, y luego pásalos a una sobrecarga de `sign` que acepte un objeto `KeyStore`. |
| **¿Cómo añado una imagen de firma visible?** | Usa `signatureOptions.setSignatureImage("path/to/image.png")` antes de llamar a `sign`. |
| **¿Es el proceso de firma seguro para hilos?** | El método `DigitalSignatureUtil.sign` es sin estado; puedes llamarlo de forma segura desde varios hilos siempre que cada hilo use su propia instancia de `SignatureOptions`. |
| **¿Qué ocurre si el DOCX contiene firmas existentes?** | La biblioteca añadirá una nueva entrada de paquete de firma, preservando las firmas anteriores. Verifica que la política de firma permita múltiples firmas si es necesario. |

---

## Consejos y mejores prácticas (E‑E‑A‑T)

* **Consejo profesional:** Almacena la contraseña de tu certificado en una bóveda segura (p.ej., Azure Key Vault) en lugar de codificarla directamente.  
* **Cuidado con:** los separadores de ruta en Windows (`\`) vs. Unix (`/`). Usa `Paths.get(...)` para construir rutas independientes de la plataforma.  
* **Rendimiento:** Firmar archivos DOCX grandes puede estar limitado por I/O; considera transmitir el archivo de entrada si procesas muchos documentos en lote.  
* **Cumplimiento:** XAdES‑EPES cumple con la regulación EU eIDAS; verifica los requisitos legales locales antes de elegir un nivel de firma.  

---

## Conclusión

En este tutorial aprendiste cómo **crear opciones de firma** y **firmar un documento Word** con el nivel XAdES‑EPES usando Java. El ejemplo completo cubre la carga del certificado, la configuración de opciones, la llamada de firma y la verificación opcional, brindándote una solución lista para usar para **cómo firmar docx** en producción.

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Crear opciones de carga en Java – Detectar fuentes faltantes y cómo cargar DOCX](/words/english/java/document-loading-and-saving/create-load-options-in-java-detect-missing-fonts-how-to-load/)
- [Uso de opciones y configuraciones de documento en Aspose.Words para Java](/words/english/java/document-manipulation/using-document-options-and-settings/)
- [Cómo crear rangos editables en documentos de solo lectura usando Aspose.Words para Java](/words/english/java/security-protection/editable-ranges-aspose-words-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}