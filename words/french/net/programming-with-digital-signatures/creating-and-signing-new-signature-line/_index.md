---
title: Créer et signer une nouvelle ligne de signature
linktitle: Créer et signer une nouvelle ligne de signature
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment créer et signer numériquement une ligne de signature dans un document Word à l'aide d'Aspose.Words pour .NET grâce à ce didacticiel étape par étape. Idéal pour l'automatisation des documents.
weight: 10
url: /fr/net/programming-with-digital-signatures/creating-and-signing-new-signature-line/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer et signer une nouvelle ligne de signature

## Introduction

Bonjour ! Vous avez un document Word et vous devez ajouter une ligne de signature, puis le signer numériquement. Cela vous semble compliqué ? Pas du tout ! Grâce à Aspose.Words pour .NET, vous pouvez y parvenir en toute transparence avec seulement quelques lignes de code. Dans ce tutoriel, nous vous guiderons tout au long du processus, de la configuration de votre environnement à l'enregistrement de votre document avec une nouvelle signature brillante. Prêt ? Plongeons-nous dans le vif du sujet !

## Prérequis

Avant de passer au code, assurons-nous que vous disposez de tout ce dont vous avez besoin :
1.  Aspose.Words pour .NET - Vous pouvez[téléchargez-le ici](https://releases.aspose.com/words/net/).
2. Un environnement de développement .NET - Visual Studio est fortement recommandé.
3. Un document à signer - Créez un document Word simple ou utilisez-en un existant.
4.  Un fichier de certificat - Il est nécessaire pour les signatures numériques. Vous pouvez utiliser un`.pfx` déposer.
5. Images pour la ligne de signature - En option, un fichier image pour la signature.

## Importer des espaces de noms

Tout d’abord, nous devons importer les espaces de noms nécessaires. Cette étape est cruciale car elle permet de configurer l’environnement d’utilisation des fonctionnalités d’Aspose.Words.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
using Aspose.Words.Signing;
```

## Étape 1 : Configuration du répertoire de documents

Tout projet a besoin d'un bon départ. Définissons le chemin d'accès à votre répertoire de documents. C'est là que vos documents seront enregistrés et récupérés.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Étape 2 : Créer un nouveau document

Maintenant, créons un nouveau document Word en utilisant Aspose.Words. Ce sera notre toile sur laquelle nous ajouterons la ligne de signature.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Étape 3 : Insertion de la ligne de signature

 C'est ici que la magie opère. Nous insérons une ligne de signature dans notre document en utilisant la`DocumentBuilder` classe.

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(new SignatureLineOptions()).SignatureLine;
```

## Étape 4 : Enregistrer le document avec la ligne de signature

Une fois la ligne de signature en place, il faut enregistrer le document. Il s'agit d'une étape intermédiaire avant de procéder à sa signature.

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLine.docx");
```

## Étape 5 : Configuration des options de signature

Maintenant, configurons les options de signature du document. Cela inclut la spécification de l'ID de la ligne de signature et de l'image à utiliser.

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    SignatureLineImage = File.ReadAllBytes(dataDir + "Enhanced Windows MetaFile.emf")
};
```

## Étape 6 : chargement du certificat

Les signatures numériques nécessitent un certificat. Ici, nous chargeons le fichier de certificat qui sera utilisé pour signer le document.

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

## Étape 7 : Signature du document

 C'est la dernière étape. Nous utilisons le`DigitalSignatureUtil`classe pour signer le document. Le document signé est enregistré sous un nouveau nom.

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLine.docx",
    dataDir + "SignDocuments.NewSignatureLine.docx", certHolder, signOptions);
```

## Conclusion

Et voilà ! Grâce à ces étapes, vous avez réussi à créer un nouveau document Word, à ajouter une ligne de signature et à le signer numériquement à l'aide d'Aspose.Words pour .NET. Il s'agit d'un outil puissant qui simplifie l'automatisation des documents. Qu'il s'agisse de contrats, d'accords ou de tout autre document officiel, cette méthode garantit qu'ils sont signés et authentifiés en toute sécurité.

## FAQ

### Puis-je utiliser d’autres formats d’image pour la ligne de signature ?
Oui, vous pouvez utiliser différents formats d'image tels que PNG, JPG, BMP, etc.

###  Est-il nécessaire d'utiliser un`.pfx` file for the certificate?
 Oui, un`.pfx` Un fichier est un format courant pour stocker des informations cryptographiques, notamment des certificats et des clés privées.

### Puis-je ajouter plusieurs lignes de signature dans un seul document ?
Absolument ! Vous pouvez insérer plusieurs lignes de signature en répétant l'étape d'insertion pour chaque signature.

### Que faire si je n’ai pas de certificat numérique ?
Vous devrez obtenir un certificat numérique auprès d'une autorité de certification de confiance ou en générer un à l'aide d'outils tels qu'OpenSSL.

### Comment vérifier la signature numérique dans le document ?
Vous pouvez ouvrir le document signé dans Word et accéder aux détails de la signature pour vérifier l’authenticité et l’intégrité de la signature.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
