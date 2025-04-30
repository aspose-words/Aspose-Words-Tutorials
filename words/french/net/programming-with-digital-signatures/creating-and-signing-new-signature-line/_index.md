---
"description": "Apprenez à créer et signer numériquement une ligne de signature dans un document Word avec Aspose.Words pour .NET grâce à ce tutoriel étape par étape. Idéal pour l'automatisation de vos documents."
"linktitle": "Création et signature d'une nouvelle ligne de signature"
"second_title": "API de traitement de documents Aspose.Words"
"title": "Création et signature d'une nouvelle ligne de signature"
"url": "/fr/net/programming-with-digital-signatures/creating-and-signing-new-signature-line/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Création et signature d'une nouvelle ligne de signature

## Introduction

Salut ! Vous avez un document Word et vous devez ajouter une ligne de signature, puis le signer numériquement. Ça vous paraît compliqué ? Pas du tout ! Grâce à Aspose.Words pour .NET, vous pouvez y parvenir facilement en quelques lignes de code. Dans ce tutoriel, nous vous guiderons tout au long du processus, de la configuration de votre environnement à l'enregistrement de votre document avec une nouvelle signature. Prêt ? C'est parti !

## Prérequis

Avant de passer au code, assurons-nous que vous disposez de tout ce dont vous avez besoin :
1. Aspose.Words pour .NET - Vous pouvez [téléchargez-le ici](https://releases.aspose.com/words/net/).
2. Un environnement de développement .NET - Visual Studio est fortement recommandé.
3. Un document à signer - Créez un document Word simple ou utilisez-en un existant.
4. Un fichier de certificat : nécessaire aux signatures numériques. Vous pouvez utiliser un `.pfx` déposer.
5. Images pour la ligne de signature - En option, un fichier image pour la signature.

## Importer des espaces de noms

Tout d'abord, nous devons importer les espaces de noms nécessaires. Cette étape est cruciale car elle permet de configurer l'environnement d'utilisation des fonctionnalités d'Aspose.Words.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
using Aspose.Words.Signing;
```

## Étape 1 : Configuration du répertoire de documents

Tout projet nécessite un bon départ. Définissons le chemin d'accès à votre répertoire de documents. C'est là que vos documents seront enregistrés et récupérés.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Étape 2 : Création d'un nouveau document

Créons maintenant un nouveau document Word avec Aspose.Words. Ce sera notre canevas où nous ajouterons la ligne de signature.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Étape 3 : Insertion de la ligne de signature

C'est là que la magie opère. Nous insérons une ligne de signature dans notre document à l'aide de `DocumentBuilder` classe.

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(new SignatureLineOptions()).SignatureLine;
```

## Étape 4 : Enregistrement du document avec la ligne de signature

Une fois la ligne de signature en place, nous devons enregistrer le document. Il s'agit d'une étape intermédiaire avant de procéder à la signature.

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLine.docx");
```

## Étape 5 : Configuration des options de signature

Maintenant, configurons les options de signature du document. Cela inclut la spécification de l'identifiant de la ligne de signature et de l'image à utiliser.

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    SignatureLineImage = File.ReadAllBytes(dataDir + "Enhanced Windows MetaFile.emf")
};
```

## Étape 6 : Chargement du certificat

Les signatures numériques nécessitent un certificat. Nous chargeons ici le fichier de certificat qui servira à signer le document.

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

## Étape 7 : Signature du document

C'est la dernière étape. Nous utilisons le `DigitalSignatureUtil` classe pour signer le document. Le document signé est enregistré sous un nouveau nom.

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLine.docx",
    dataDir + "SignDocuments.NewSignatureLine.docx", certHolder, signOptions);
```

## Conclusion

Et voilà ! Grâce à ces étapes, vous avez créé un document Word, ajouté une ligne de signature et signé numériquement avec Aspose.Words pour .NET. Cet outil puissant simplifie l'automatisation des documents. Qu'il s'agisse de contrats, d'accords ou de tout autre document officiel, cette méthode garantit leur signature et leur authentification sécurisées.

## FAQ

### Puis-je utiliser d’autres formats d’image pour la ligne de signature ?
Oui, vous pouvez utiliser différents formats d'image comme PNG, JPG, BMP, etc.

### Est-il nécessaire d'utiliser un `.pfx` fichier pour le certificat ?
Oui, un `.pfx` Un fichier est un format courant pour stocker des informations cryptographiques, notamment des certificats et des clés privées.

### Puis-je ajouter plusieurs lignes de signature dans un seul document ?
Absolument ! Vous pouvez insérer plusieurs lignes de signature en répétant l'étape d'insertion pour chaque signature.

### Que faire si je n’ai pas de certificat numérique ?
Vous devrez obtenir un certificat numérique auprès d'une autorité de certification de confiance ou en générer un à l'aide d'outils tels qu'OpenSSL.

### Comment vérifier la signature numérique dans le document ?
Vous pouvez ouvrir le document signé dans Word et accéder aux détails de la signature pour vérifier l’authenticité et l’intégrité de la signature.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}