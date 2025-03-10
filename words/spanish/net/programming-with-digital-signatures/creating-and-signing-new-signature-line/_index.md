---
title: Creación y firma de una nueva línea de firma
linktitle: Creación y firma de una nueva línea de firma
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a crear y firmar digitalmente una línea de firma en un documento de Word con Aspose.Words para .NET con este tutorial paso a paso. Perfecto para la automatización de documentos.
weight: 10
url: /es/net/programming-with-digital-signatures/creating-and-signing-new-signature-line/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Creación y firma de una nueva línea de firma

## Introducción

¡Hola! Tienes un documento de Word y necesitas agregar una línea de firma y luego firmarlo digitalmente. ¿Suena complicado? ¡Para nada! Gracias a Aspose.Words para .NET, puedes lograrlo sin problemas con solo unas pocas líneas de código. En este tutorial, te guiaremos a través de todo el proceso, desde la configuración de tu entorno hasta el guardado de tu documento con una nueva y brillante firma. ¿Listo? ¡Comencemos!

## Prerrequisitos

Antes de pasar al código, asegurémonos de que tienes todo lo que necesitas:
1.  Aspose.Words para .NET: puedes[Descárgalo aquí](https://releases.aspose.com/words/net/).
2. Un entorno de desarrollo .NET: se recomienda Visual Studio.
3. Un documento para firmar: cree un documento de Word simple o utilice uno existente.
4.  Un archivo de certificado: es necesario para las firmas digitales. Puede utilizar un`.pfx` archivo.
5. Imágenes para la línea de firma: Opcionalmente, un archivo de imagen para la firma.

## Importar espacios de nombres

En primer lugar, debemos importar los espacios de nombres necesarios. Este paso es crucial, ya que configura el entorno para utilizar las funcionalidades de Aspose.Words.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
using Aspose.Words.Signing;
```

## Paso 1: Configuración del directorio de documentos

Todo proyecto necesita un buen comienzo. Vamos a configurar la ruta hacia el directorio de documentos. Aquí es donde se guardarán y recuperarán los documentos.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Paso 2: Crear un nuevo documento

Ahora, vamos a crear un nuevo documento de Word con Aspose.Words. Este será nuestro lienzo donde agregaremos la línea de firma.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Paso 3: Insertar la línea de firma

 Aquí es donde ocurre la magia. Insertamos una línea de firma en nuestro documento usando el`DocumentBuilder` clase.

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(new SignatureLineOptions()).SignatureLine;
```

## Paso 4: Guardar el documento con la línea de firma

Una vez que la línea de firma está en su lugar, debemos guardar el documento. Este es un paso intermedio antes de proceder a firmarlo.

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLine.docx");
```

## Paso 5: Configuración de las opciones de firma

Ahora, configuremos las opciones para firmar el documento. Esto incluye especificar el ID de la línea de firma y la imagen que se utilizará.

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    SignatureLineImage = File.ReadAllBytes(dataDir + "Enhanced Windows MetaFile.emf")
};
```

## Paso 6: Carga del certificado

Las firmas digitales requieren un certificado. Aquí cargamos el archivo del certificado que se utilizará para firmar el documento.

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

## Paso 7: Firma del documento

 Este es el paso final. Usamos el`DigitalSignatureUtil`Clase para firmar el documento. El documento firmado se guarda con un nuevo nombre.

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLine.docx",
    dataDir + "SignDocuments.NewSignatureLine.docx", certHolder, signOptions);
```

## Conclusión

¡Y ya está! Con estos pasos, ha creado con éxito un nuevo documento de Word, ha añadido una línea de firma y lo ha firmado digitalmente con Aspose.Words para .NET. Es una herramienta potente que facilita la automatización de documentos. Ya sea que se trate de contratos, acuerdos o cualquier documento formal, este método garantiza que estén firmados y autenticados de forma segura.

## Preguntas frecuentes

### ¿Puedo utilizar otros formatos de imagen para la línea de firma?
Sí, puedes utilizar varios formatos de imagen como PNG, JPG, BMP, etc.

###  ¿Es necesario utilizar un?`.pfx` file for the certificate?
 Sí, una`.pfx` El archivo es un formato común para almacenar información criptográfica, incluidos certificados y claves privadas.

### ¿Puedo agregar varias líneas de firma en un solo documento?
¡Por supuesto! Puedes insertar varias líneas de firma repitiendo el paso de inserción para cada firma.

### ¿Qué pasa si no tengo un certificado digital?
Necesitará obtener un certificado digital de una autoridad de certificación confiable o generar uno utilizando herramientas como OpenSSL.

### ¿Cómo verificar la firma digital en el documento?
Puede abrir el documento firmado en Word e ir a los detalles de la firma para verificar la autenticidad e integridad de la firma.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
