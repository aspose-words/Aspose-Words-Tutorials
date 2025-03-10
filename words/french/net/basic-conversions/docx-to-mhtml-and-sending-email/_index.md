---
title: Convertir Docx en Mhtml et envoyer un e-mail
linktitle: Convertir Docx en Mhtml et envoyer un e-mail
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment convertir DOCX en MHTML et envoyer des e-mails à l'aide d'Aspose.Words pour .NET dans ce guide étape par étape. Boostez votre productivité grâce à une automatisation facile.
weight: 10
url: /fr/net/basic-conversions/docx-to-mhtml-and-sending-email/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Convertir Docx en Mhtml et envoyer un e-mail

## Introduction

À l'ère du numérique, convertir des documents d'un format à un autre et les envoyer par courrier électronique est une tâche courante. Cet article vous guidera tout au long du processus de conversion d'un fichier DOCX au format MHTML, puis de son envoi par courrier électronique à l'aide d'Aspose.Words pour .NET. Nous détaillerons chaque étape dans un guide détaillé et facile à suivre, afin que vous compreniez le processus du début à la fin. Plongeons-nous dans le vif du sujet !

## Prérequis

Avant de commencer, assurez-vous que les conditions préalables suivantes sont remplies :

1.  Aspose.Words pour .NET : téléchargez et installez la bibliothèque Aspose.Words pour .NET à partir du[Page de sortie d'Aspose](https://releases.aspose.com/words/net/).
2.  Aspose.Email pour .NET : téléchargez et installez la bibliothèque Aspose.Email pour .NET à partir du[Page de sortie d'Aspose](https://releases.aspose.com/email/net/).
3. .NET Framework : assurez-vous que .NET Framework est installé sur votre ordinateur.
4. Serveur SMTP : Vous devez avoir accès à un serveur SMTP pour envoyer des e-mails.

## Importer des espaces de noms

Pour utiliser Aspose.Words et Aspose.Email dans votre projet, vous devez importer les espaces de noms nécessaires. Ajoutez les directives using suivantes en haut de votre fichier C# :

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Clients.Smtp;
```

Décomposons le processus en plusieurs étapes pour nous assurer que vous comprenez clairement chaque partie.

## Étape 1 : Charger le document DOCX

 Tout d'abord, vous devez charger le document DOCX que vous souhaitez convertir. Utilisez le`Document` classe de Aspose.Words pour charger votre fichier DOCX.

```csharp
// Le chemin vers le répertoire des documents.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

## Étape 2 : enregistrer le document au format MHTML

 Ensuite, enregistrez le document chargé en tant que fichier MHTML. Cela se fait à l'aide de l'`Save` méthode de la`Document` classe.

```csharp
Stream stream = new MemoryStream();
doc.Save(stream, SaveFormat.Mhtml);

// Rembobinez le flux jusqu'au début pour qu'Aspose.Email puisse le lire.
stream.Position = 0;
```

## Étape 3 : Créer un message électronique

 Créez maintenant un message électronique à partir du flux MHTML à l'aide d'Aspose.Email. Vous utiliserez le`MailMessage` classe à cet effet.

```csharp
// Créez un message électronique MIME Aspose.Email à partir du flux.
MailMessage message = MailMessage.Load(stream, new MhtmlLoadOptions());
message.From = "your_from@email.com";
message.To = "your_to@email.com";
message.Subject = "Aspose.Words + Aspose.Email MHTML Test Message";
```

## Étape 4 : Envoyer l'e-mail

 Enfin, envoyez l'e-mail à l'aide d'un client SMTP. Configurez le client SMTP avec les détails de votre serveur SMTP et utilisez le`Send` méthode pour envoyer le message.

```csharp
// Envoyez le message en utilisant Aspose.Email.
SmtpClient client = new SmtpClient();
client.Host = "your_smtp.com";
client.Send(message);
```

## Conclusion

Félicitations ! Vous avez converti avec succès un document DOCX en MHTML et l'avez envoyé par courrier électronique à l'aide d'Aspose.Words pour .NET. Ce processus implique le chargement du document, sa conversion en MHTML, la création d'un message électronique et son envoi à l'aide d'un client SMTP. Grâce à ces étapes, vous pouvez facilement automatiser la conversion et l'envoi par courrier électronique de documents dans vos applications.

## FAQ

### Puis-je utiliser cette méthode pour convertir d’autres formats de documents ?
Oui, Aspose.Words prend en charge différents formats et vous pouvez convertir des documents tels que DOC, DOCX, RTF et plus en MHTML.

### Comment puis-je ajouter des pièces jointes à l'e-mail ?
 Vous pouvez utiliser le`Attachments` propriété de la`MailMessage` classe pour ajouter des pièces jointes à votre email.

### Aspose.Words est-il compatible avec .NET Core ?
Oui, Aspose.Words est compatible avec .NET Core. Vous pouvez également l'utiliser dans les applications .NET Core.

### Ai-je besoin d'une licence pour Aspose.Words et Aspose.Email ?
 Oui, les deux bibliothèques nécessitent des licences. Vous pouvez obtenir une licence temporaire auprès de[Page d'achat Aspose](https://purchase.aspose.com/temporary-license/) à des fins d'évaluation.

### Où puis-je trouver plus de documentation ?
 Vous pouvez trouver une documentation détaillée pour Aspose.Words[ici](https://reference.aspose.com/words/net/) et pour Aspose.Email[ici](https://reference.aspose.com/email/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
