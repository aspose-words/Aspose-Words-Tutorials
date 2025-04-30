---
"description": "Aprenda a convertir DOCX a MHTML y a enviar correos electrónicos con Aspose.Words para .NET con esta guía paso a paso. Aumente su productividad con una automatización sencilla."
"linktitle": "Convertir DOCX a MHTML y enviar correo electrónico"
"second_title": "API de procesamiento de documentos de Aspose.Words"
"title": "Convertir DOCX a MHTML y enviar correo electrónico"
"url": "/es/net/basic-conversions/docx-to-mhtml-and-sending-email/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Convertir DOCX a MHTML y enviar correo electrónico

## Introducción

En la era digital actual, convertir documentos de un formato a otro y enviarlos por correo electrónico es una tarea común. Este artículo te guiará en el proceso de convertir un archivo DOCX a formato MHTML y luego enviarlo por correo electrónico usando Aspose.Words para .NET. Desglosaremos cada paso en una guía detallada y fácil de seguir, para que comprendas el proceso de principio a fin. ¡Comencemos!

## Prerrequisitos

Antes de comenzar, asegúrese de tener los siguientes requisitos previos:

1. Aspose.Words para .NET: Descargue e instale la biblioteca Aspose.Words para .NET desde [Página de lanzamiento de Aspose](https://releases.aspose.com/words/net/).
2. Aspose.Email para .NET: Descargue e instale la biblioteca Aspose.Email para .NET desde [Página de lanzamiento de Aspose](https://releases.aspose.com/email/net/).
3. .NET Framework: asegúrese de tener .NET Framework instalado en su máquina.
4. Servidor SMTP: necesita acceso a un servidor SMTP para enviar correos electrónicos.

## Importar espacios de nombres

Para usar Aspose.Words y Aspose.Email en su proyecto, debe importar los espacios de nombres necesarios. Agregue las siguientes directivas using al inicio de su archivo de C#:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Clients.Smtp;
```

Dividiremos el proceso en varios pasos para asegurarnos de que comprenda cada parte claramente.

## Paso 1: Cargue el documento DOCX

Primero, debe cargar el documento DOCX que desea convertir. Utilice el `Document` clase de Aspose.Words para cargar su archivo DOCX.

```csharp
// La ruta al directorio de documentos.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

## Paso 2: Guarde el documento como MHTML

A continuación, guarde el documento cargado como un archivo MHTML. Esto se hace usando el `Save` método de la `Document` clase.

```csharp
Stream stream = new MemoryStream();
doc.Save(stream, SaveFormat.Mhtml);

// Rebobine la transmisión hasta el principio para que Aspose.Email pueda leerla.
stream.Position = 0;
```

## Paso 3: Crear un mensaje de correo electrónico

Ahora, crea un mensaje de correo electrónico desde la secuencia MHTML usando Aspose.Email. Usarás el `MailMessage` clase para este propósito.

```csharp
// Crea un mensaje de correo electrónico MIME Aspose.Email desde la transmisión.
MailMessage message = MailMessage.Load(stream, new MhtmlLoadOptions());
message.From = "your_from@email.com";
message.To = "your_to@email.com";
message.Subject = "Aspose.Words + Aspose.Email MHTML Test Message";
```

## Paso 4: Enviar el correo electrónico

Finalmente, envíe el correo electrónico mediante un cliente SMTP. Configure el cliente SMTP con los datos de su servidor SMTP y utilice el `Send` método para enviar el mensaje.

```csharp
// Envíe el mensaje utilizando Aspose.Email.
SmtpClient client = new SmtpClient();
client.Host = "your_smtp.com";
client.Send(message);
```

## Conclusión

¡Felicitaciones! Ha convertido correctamente un documento DOCX a MHTML y lo ha enviado por correo electrónico con Aspose.Words para .NET. Este proceso implica cargar el documento, convertirlo a MHTML, crear un mensaje de correo electrónico y enviarlo mediante un cliente SMTP. Con estos pasos, puede automatizar fácilmente la conversión y el envío de documentos por correo electrónico en sus aplicaciones.

## Preguntas frecuentes

### ¿Puedo utilizar este método para convertir otros formatos de documentos?
Sí, Aspose.Words admite varios formatos y puedes convertir documentos como DOC, DOCX, RTF y más a MHTML.

### ¿Cómo puedo agregar archivos adjuntos al correo electrónico?
Puedes utilizar el `Attachments` propiedad de la `MailMessage` Clase para agregar archivos adjuntos a su correo electrónico.

### ¿Es Aspose.Words compatible con .NET Core?
Sí, Aspose.Words es compatible con .NET Core. También puedes usarlo en aplicaciones .NET Core.

### ¿Necesito una licencia para Aspose.Words y Aspose.Email?
Sí, ambas bibliotecas requieren licencias. Puede obtener una licencia temporal en [Página de compra de Aspose](https://purchase.aspose.com/temporary-license/) para fines de evaluación.

### ¿Dónde puedo encontrar más documentación?
Puede encontrar documentación detallada de Aspose.Words [aquí](https://reference.aspose.com/words/net/) y para Aspose.Email [aquí](https://reference.aspose.com/email/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}