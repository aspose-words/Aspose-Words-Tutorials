---
"description": "Aprenda a crear y firmar digitalmente una línea de firma en un documento de Word con Aspose.Words para .NET con este tutorial paso a paso. Ideal para la automatización de documentos."
"linktitle": "Creación y firma de una nueva línea de firma"
"second_title": "API de procesamiento de documentos de Aspose.Words"
"title": "Creación y firma de una nueva línea de firma"
"url": "/es/net/programming-with-digital-signatures/creating-and-signing-new-signature-line/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Creación y firma de una nueva línea de firma

## Introducción

¡Hola! Tienes un documento de Word y necesitas añadir una línea de firma y firmarlo digitalmente. ¿Suena complicado? ¡Para nada! Gracias a Aspose.Words para .NET, puedes lograrlo fácilmente con solo unas pocas líneas de código. En este tutorial, te guiaremos por todo el proceso, desde la configuración de tu entorno hasta guardar tu documento con una firma impecable. ¿Listo? ¡Comencemos!

## Prerrequisitos

Antes de pasar al código, asegurémonos de que tienes todo lo que necesitas:
1. Aspose.Words para .NET - Puedes [Descárgalo aquí](https://releases.aspose.com/words/net/).
2. Un entorno de desarrollo .NET: Visual Studio es muy recomendable.
3. Un documento para firmar: cree un documento de Word simple o utilice uno existente.
4. Un archivo de certificado: es necesario para las firmas digitales. Puede usar un `.pfx` archivo.
5. Imágenes para la línea de firma: opcionalmente, un archivo de imagen para la firma.

## Importar espacios de nombres

Primero, necesitamos importar los espacios de nombres necesarios. Este paso es crucial, ya que configura el entorno para usar las funcionalidades de Aspose.Words.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
using Aspose.Words.Signing;
```

## Paso 1: Configuración del directorio de documentos

Todo proyecto necesita un buen comienzo. Vamos a configurar la ruta a tu directorio de documentos. Aquí es donde se guardarán y recuperarán tus documentos.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Paso 2: Crear un nuevo documento

Ahora, creemos un nuevo documento de Word con Aspose.Words. Este será nuestro lienzo donde agregaremos la línea de firma.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Paso 3: Inserción de la línea de firma

Aquí es donde ocurre la magia. Insertamos una línea de firma en nuestro documento usando el `DocumentBuilder` clase.

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(new SignatureLineOptions()).SignatureLine;
```

## Paso 4: Guardar el documento con la línea de firma

Una vez que la línea de firma esté colocada, debemos guardar el documento. Este es un paso intermedio antes de proceder a firmarlo.

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLine.docx");
```

## Paso 5: Configuración de las opciones de firma

Ahora, configuremos las opciones para firmar el documento. Esto incluye especificar el ID de la línea de firma y la imagen que se usará.

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    SignatureLineImage = File.ReadAllBytes(dataDir + "Enhanced Windows MetaFile.emf")
};
```

## Paso 6: Carga del certificado

Las firmas digitales requieren un certificado. Aquí cargamos el archivo del certificado que se usará para firmar el documento.

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

## Paso 7: Firma del documento

Este es el paso final. Usamos el `DigitalSignatureUtil` Clase para firmar el documento. El documento firmado se guarda con un nuevo nombre.

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLine.docx",
    dataDir + "SignDocuments.NewSignatureLine.docx", certHolder, signOptions);
```

## Conclusión

¡Y listo! Con estos pasos, has creado un nuevo documento de Word, has añadido una línea de firma y lo has firmado digitalmente con Aspose.Words para .NET. Es una herramienta potente que facilita la automatización de documentos. Ya sea que trabajes con contratos, acuerdos o cualquier documento formal, este método garantiza su firma y autenticación seguras.

## Preguntas frecuentes

### ¿Puedo utilizar otros formatos de imagen para la línea de firma?
Sí, puedes utilizar varios formatos de imagen como PNG, JPG, BMP, etc.

### ¿Es necesario utilizar un? `.pfx` ¿archivo para el certificado?
Sí, una `.pfx` El archivo es un formato común para almacenar información criptográfica, incluidos certificados y claves privadas.

### ¿Puedo agregar varias líneas de firma en un solo documento?
¡Claro! Puedes insertar varias líneas de firma repitiendo el paso para cada una.

### ¿Qué pasa si no tengo un certificado digital?
Necesitará obtener un certificado digital de una autoridad de certificación confiable o generar uno utilizando herramientas como OpenSSL.

### ¿Cómo verificar la firma digital en el documento?
Puede abrir el documento firmado en Word e ir a los detalles de la firma para verificar la autenticidad e integridad de la firma.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}