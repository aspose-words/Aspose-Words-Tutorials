---
"description": "Aprenda a crear una nueva línea de firma y a configurar el ID del proveedor en documentos de Word con Aspose.Words para .NET. Guía paso a paso."
"linktitle": "Crear una nueva línea de firma y establecer el ID del proveedor"
"second_title": "API de procesamiento de documentos de Aspose.Words"
"title": "Crear una nueva línea de firma y establecer el ID del proveedor"
"url": "/es/net/programming-with-digital-signatures/create-new-signature-line-and-set-provider-id/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Crear una nueva línea de firma y establecer el ID del proveedor

## Introducción

¡Hola, entusiastas de la tecnología! ¿Alguna vez se han preguntado cómo agregar una línea de firma en sus documentos de Word mediante programación? Hoy profundizaremos en eso usando Aspose.Words para .NET. Esta guía los guiará paso a paso, facilitando enormemente la creación de una nueva línea de firma y la configuración del ID del proveedor en sus documentos de Word. Ya sea que estén automatizando el procesamiento de documentos o simplemente buscando optimizar su flujo de trabajo, este tutorial los ayudará.

## Prerrequisitos

Antes de ensuciarnos las manos, asegurémonos de que tenemos todo lo que necesitamos:

1. Aspose.Words para .NET: Si aún no lo has hecho, descárgalo [aquí](https://releases.aspose.com/words/net/).
2. Entorno de desarrollo: Visual Studio o cualquier otro entorno de desarrollo de C#.
3. .NET Framework: asegúrese de tener .NET Framework instalado.
4. Certificado PFX: Para firmar documentos, necesitará un certificado PFX. Puede obtenerlo de una autoridad de certificación de confianza.

## Importar espacios de nombres

Primero lo primero, importemos los espacios de nombres necesarios en su proyecto C#:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Signing;
using System;
```

Bien, vayamos al grano. Aquí tienes un desglose detallado de cada paso para crear una nueva línea de firma y configurar el ID del proveedor.

## Paso 1: Crear un nuevo documento

Para empezar, necesitamos crear un nuevo documento de Word. Este será el lienzo para nuestra línea de firma.

```csharp
// La ruta al directorio de documentos.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

En este fragmento, estamos inicializando un nuevo `Document` y un `DocumentBuilder`. El `DocumentBuilder` nos ayuda a agregar elementos a nuestro documento.

## Paso 2: Definir las opciones de la línea de firma

A continuación, definimos las opciones para nuestra línea de firma. Esto incluye el nombre, el cargo, el correo electrónico y otros datos del firmante.

```csharp
SignatureLineOptions signatureLineOptions = new SignatureLineOptions
{
    Signer = "vderyushev",
    SignerTitle = "QA",
    Email = "vderyushev@aspose.com",
    ShowDate = true,
    DefaultInstructions = false,
    Instructions = "Please sign here.",
    AllowComments = true
};
```

Estas opciones personalizan la línea de la firma, haciéndola clara y profesional.

## Paso 3: Insertar la línea de firma

Con nuestras opciones configuradas, ahora podemos insertar la línea de firma en el documento.

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(signatureLineOptions).SignatureLine;
signatureLine.ProviderId = Guid.Parse("CF5A7BB4-8F3C-4756-9DF6-BEF7F13259A2");
```

Aquí, el `InsertSignatureLine` El método agrega la línea de firma y le asignamos un ID de proveedor único.

## Paso 4: Guardar el documento

Después de insertar la línea de firma, guardemos el documento.

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLineProviderId.docx");
```

Esto guarda su documento con la línea de firma recién agregada.

## Paso 5: Configurar las opciones de firma

Ahora, debemos configurar las opciones para firmar el documento. Esto incluye el ID de la línea de firma, el ID del proveedor, los comentarios y la hora de firma.

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    ProviderId = signatureLine.ProviderId,
    Comments = "Document was signed by vderyushev",
    SignTime = DateTime.Now
};
```

Estas opciones garantizan que el documento esté firmado con los detalles correctos.

## Paso 6: Crear el titular del certificado

Para firmar el documento, usaremos un certificado PFX. Vamos a crear un titular de certificado para él.

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

Asegúrese de reemplazar `"morzal.pfx"` con su archivo de certificado real y `"aw"` con la contraseña de su certificado.

## Paso 7: Firmar el documento

Finalmente, firmamos el documento utilizando la utilidad de firma digital.

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLineProviderId.docx", 
    dataDir + "SignDocuments.CreateNewSignatureLineAndSetProviderId.docx", certHolder, signOptions);
```

Esto firma el documento y lo guarda como un archivo nuevo.

## Conclusión

¡Y listo! Has creado correctamente una nueva línea de firma y has configurado el ID del proveedor en un documento de Word con Aspose.Words para .NET. Esta potente biblioteca facilita enormemente la gestión y automatización del procesamiento de documentos. Pruébala y descubre cómo puede optimizar tu flujo de trabajo.

## Preguntas frecuentes

### ¿Puedo personalizar la apariencia de la línea de firma?
¡Por supuesto! Puedes ajustar varias opciones en el `SignatureLineOptions` para adaptarse a sus necesidades.

### ¿Qué pasa si no tengo un certificado PFX?
Necesitará obtener uno de una autoridad de certificación confiable. Es esencial para firmar documentos digitalmente.

### ¿Puedo agregar varias líneas de firma a un documento?
Sí, puede agregar tantas líneas de firma como necesite repitiendo el proceso de inserción con diferentes opciones.

### ¿Aspose.Words para .NET es compatible con .NET Core?
Sí, Aspose.Words para .NET es compatible con .NET Core, lo que lo hace versátil para diferentes entornos de desarrollo.

### ¿Qué tan seguras son las firmas digitales?
Las firmas digitales creadas con Aspose.Words son altamente seguras, siempre que utilice un certificado válido y confiable.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}