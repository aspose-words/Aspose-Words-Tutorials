---
title: Signature d'un document Word crypté
linktitle: Signature d'un document Word crypté
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment signer des documents Word chiffrés à l'aide d'Aspose.Words pour .NET grâce à ce guide détaillé, étape par étape. Idéal pour les développeurs.
weight: 10
url: /fr/net/programming-with-digital-signatures/signing-encrypted-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Signature d'un document Word crypté

## Introduction

Vous êtes-vous déjà demandé comment signer un document Word chiffré ? Aujourd'hui, nous allons parcourir ce processus à l'aide d'Aspose.Words pour .NET. Attachez vos ceintures et préparez-vous pour un tutoriel détaillé, engageant et amusant !

## Prérequis

Avant de plonger dans le code, assurons-nous que vous disposez de tout ce dont vous avez besoin :

1.  Aspose.Words pour .NET : téléchargez et installez depuis[ici](https://releases.aspose.com/words/net/).
2. Visual Studio : assurez-vous de l’avoir installé.
3. Un certificat valide : vous aurez besoin d’un fichier de certificat .pfx.
4. Connaissances de base en C# : comprendre les bases rendra ce didacticiel plus fluide.

## Importer des espaces de noms

Commençons par importer les espaces de noms nécessaires. Ceux-ci sont essentiels pour accéder aux fonctionnalités d'Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Words.DigitalSignatures;
```

Maintenant, décomposons le processus en étapes simples et gérables.

## Étape 1 : Configuration de votre projet

Tout d'abord, configurez votre projet Visual Studio. Ouvrez Visual Studio et créez une nouvelle application console C#. Nommez-la de manière descriptive, comme « SignEncryptedWordDoc ».

## Étape 2 : Ajout d'Aspose.Words à votre projet

Ensuite, nous devons ajouter Aspose.Words à votre projet. Il existe plusieurs façons de procéder, mais l'utilisation de NuGet est la plus simple. 

1. Ouvrez la console du gestionnaire de packages NuGet à partir de Outils > Gestionnaire de packages NuGet > Console du gestionnaire de packages.
2. Exécutez la commande suivante :

```powershell
Install-Package Aspose.Words
```

## Étape 3 : Préparation du répertoire de documents

Vous aurez besoin d'un répertoire pour stocker vos documents Word et vos certificats. Créons-en un.

1. Créez un répertoire sur votre ordinateur. Pour simplifier, appelons-le « DocumentDirectory ».
2. Placez votre document Word (par exemple, « Document.docx ») et votre certificat .pfx (par exemple, « morzal.pfx ») dans ce répertoire.

## Étape 4 : Écriture du code

 Maintenant, plongeons dans le code. Ouvrez votre`Program.cs` fichier et commencez par configurer le chemin d'accès à votre répertoire de documents et initialiser le`SignOptions` avec le mot de passe de décryptage.

```csharp
// Le chemin vers le répertoire des documents.
string dataDir = "YOUR DOCUMENTS DIRECTORY";
SignOptions signOptions = new SignOptions { DecryptionPassword = "decryptionPassword" };
```

## Étape 5 : Chargement du certificat

 Ensuite, chargez votre certificat en utilisant le`CertificateHolder`classe. Cela nécessitera le chemin d'accès à votre fichier .pfx et le mot de passe du certificat.

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

## Étape 6 : Signature du document

 Enfin, utilisez le`DigitalSignatureUtil.Sign` méthode pour signer votre document Word chiffré. Cette méthode nécessite les options de fichier d'entrée, de fichier de sortie, de titulaire de certificat et de signature.

```csharp
DigitalSignatureUtil.Sign(
    dataDir + "Document.docx",
    dataDir + "DigitallySignedDocument.docx",
    certHolder,
    signOptions);
```

## Étape 7 : Exécution du code

Enregistrez votre fichier et exécutez le projet. Si tout est configuré correctement, vous devriez voir votre document signé dans le répertoire spécifié.

## Conclusion

Et voilà ! Vous avez signé avec succès un document Word chiffré à l'aide d'Aspose.Words pour .NET. Grâce à cette puissante bibliothèque, la signature numérique devient un jeu d'enfant, même pour les fichiers chiffrés. Bon codage !

## FAQ

### Puis-je utiliser un autre type de certificat ?
Oui, Aspose.Words prend en charge différents types de certificats, à condition qu'ils soient au format correct.

### Est-il possible de signer plusieurs documents à la fois ?
Absolument ! Vous pouvez parcourir une collection de documents et signer chacun d'eux par programmation.

### Que faire si j'oublie le mot de passe de décryptage ?
Malheureusement, sans le mot de passe de décryptage, vous ne pourrez pas signer le document.

### Puis-je ajouter une signature visible au document ?
Oui, Aspose.Words vous permet également d'ajouter des signatures numériques visibles.

### Existe-t-il un moyen de vérifier la signature ?
 Oui, vous pouvez utiliser le`DigitalSignatureUtil.Verify` méthode pour vérifier les signatures.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
