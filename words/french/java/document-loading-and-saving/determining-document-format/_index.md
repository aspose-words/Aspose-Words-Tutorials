---
date: 2025-12-20
description: Apprenez à organiser les fichiers par type et à détecter les formats
  de documents en Java avec Aspose.Words. Prise en charge de DOC, DOCX, RTF et plus.
linktitle: Determining Document Format
second_title: Aspose.Words Java Document Processing API
title: Organiser les fichiers par type à l'aide d'Aspose.Words pour Java
url: /fr/java/document-loading-and-saving/determining-document-format/
weight: 25
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Organiser les fichiers par type avec Aspose.Words pour Java

Lorsque vous devez **organiser les fichiers par type** dans une application Java, la première étape consiste à déterminer de manière fiable le format de chaque document. Aspose.Words for Java rend cela simple, vous permettant de détecter les formats DOC, DOCX, RTF, HTML, ODT et bien d’autres – même les fichiers chiffrés ou inconnus. Dans ce guide, nous parcourrons la création de dossiers, la détection des formats de fichiers et le tri automatique de vos fichiers.

## Réponses rapides
- **Que signifie « organiser les fichiers par type » ?** Cela signifie déplacer automatiquement les documents dans des dossiers en fonction de leur format détecté (par ex., DOCX, PDF, RTF).  
- **Quelle bibliothèque aide à détecter le format de fichier en Java ?** Aspose.Words for Java fournit `FileFormatUtil.detectFileFormat()`.  
- **L'API peut‑elle identifier les types de fichiers inconnus ?** Oui – elle renvoie `LoadFormat.UNKNOWN` pour les fichiers non pris en charge ou non reconnaissables.  
- **La détection de documents chiffrés est‑elle prise en charge ?** Absolument ; le drapeau `FileFormatInfo.isEncrypted()` indique si un fichier est protégé par mot de passe.  
- **Ai‑je besoin d’une licence pour une utilisation en production ?** Une licence valide d’Aspose.Words est requise pour les déploiements commerciaux.

## Introduction : Organiser les fichiers par type avec Aspose.Words pour Java

Lorsque vous travaillez avec le traitement de documents en Java, il est crucial de déterminer le format des fichiers que vous manipulez. Aspose.Words for Java offre des fonctionnalités puissantes pour **detect file format java**, et nous vous guiderons à travers le processus d'organisation efficace de vos fichiers.

## Prérequis

Avant de commencer, assurez‑vous d’avoir les prérequis suivants :

- [Aspose.Words for Java](https://releases.aspose.com/words/java/)
- Kit de développement Java (JDK) installé sur votre système
- Connaissances de base en programmation Java

## Étape 1 : Configuration des répertoires

Tout d'abord, nous devons configurer les répertoires nécessaires pour organiser nos fichiers efficacement. Nous créerons des répertoires pour différents types de documents.

```java
File supportedDir = new File("Your Directory Path" + "Supported");
File unknownDir = new File("Your Directory Path" + "Unknown");
File encryptedDir = new File("Your Directory Path" + "Encrypted");
File pre97Dir = new File("Your Directory Path" + "Pre97");

// Create the directories if they do not already exist.
if (!supportedDir.exists())
    supportedDir.mkdir();
if (!unknownDir.exists())
    unknownDir.mkdir();
if (!encryptedDir.exists())
    encryptedDir.mkdir();
if (!pre97Dir.exists())
    pre97Dir.mkdir();
```

Nous avons créé des répertoires pour les types de documents pris en charge, inconnus, chiffrés et pré‑97.

## Étape 2 : Détection du format du document

Maintenant, détectons le format des documents dans nos répertoires. Nous utiliserons Aspose.Words for Java pour cela.

```java
Set<String> listFiles = Stream.of(new File("Your Directory Path").listFiles())
    .filter(file -> !file.getName().endsWith("Corrupted document.docx") && !Files.isDirectory(file.toPath()))
    .map(File::getPath)
    .collect(Collectors.toSet());

for (String fileName : listFiles) {
    String nameOnly = Paths.get(fileName).getFileName().toString();
    System.out.println(nameOnly);
    FileFormatInfo info = FileFormatUtil.detectFileFormat(fileName);

    // Display the document type
    switch (info.getLoadFormat()) {
        case LoadFormat.DOC:
            System.out.println("\tMicrosoft Word 97-2003 document.");
            break;
        // Add cases for other document formats as needed
    }

    // Handle encrypted documents
    if (info.isEncrypted()) {
        System.out.println("\tAn encrypted document.");
        FileUtils.copyFile(new File(fileName), new File(encryptedDir, nameOnly));
    } else {
        // Handle other document types
        switch (info.getLoadFormat()) {
            case LoadFormat.DOC_PRE_WORD_60:
                FileUtils.copyFile(new File(fileName), new File(pre97Dir, nameOnly));
                break;
            case LoadFormat.UNKNOWN:
                FileUtils.copyFile(new File(fileName), new File(unknownDir, nameOnly));
                break;
            default:
                FileUtils.copyFile(new File(fileName), new File(supportedDir, nameOnly));
                break;
        }
    }
}
```

Dans cet extrait, nous parcourons les fichiers, **detect file format java**, et les organisons dans les dossiers appropriés.

## Code source complet pour déterminer le format du document avec Aspose.Words pour Java

```java
        File supportedDir = new File("Your Directory Path" + "Supported");
        File unknownDir = new File("Your Directory Path" + "Unknown");
        File encryptedDir = new File("Your Directory Path" + "Encrypted");
        File pre97Dir = new File("Your Directory Path" + "Pre97");
        // Create the directories if they do not already exist.
        if (supportedDir.exists() == false)
            supportedDir.mkdir();
        if (unknownDir.exists() == false)
            unknownDir.mkdir();
        if (encryptedDir.exists() == false)
            encryptedDir.mkdir();
        if (pre97Dir.exists() == false)
            pre97Dir.mkdir();
        Set<String> listFiles = Stream.of(new File("Your Directory Path").listFiles())
                .filter(file -> !file.getName().endsWith("Corrupted document.docx") && !Files.isDirectory(file.toPath()))
                .map(File::getPath)
                .collect(Collectors.toSet());
        for (String fileName : listFiles) {
            String nameOnly = Paths.get(fileName).getFileName().toString();
            System.out.println(nameOnly);
            FileFormatInfo info = FileFormatUtil.detectFileFormat(fileName);
            // Display the document type
            switch (info.getLoadFormat()) {
                case LoadFormat.DOC:
                    System.out.println("\tMicrosoft Word 97-2003 document.");
                    break;
                case LoadFormat.DOT:
                    System.out.println("\tMicrosoft Word 97-2003 template.");
                    break;
                case LoadFormat.DOCX:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Free Document.");
                    break;
                case LoadFormat.DOCM:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Enabled Document.");
                    break;
                case LoadFormat.DOTX:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Free Template.");
                    break;
                case LoadFormat.DOTM:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Enabled Template.");
                    break;
                case LoadFormat.FLAT_OPC:
                    System.out.println("\tFlat OPC document.");
                    break;
                case LoadFormat.RTF:
                    System.out.println("\tRTF format.");
                    break;
                case LoadFormat.WORD_ML:
                    System.out.println("\tMicrosoft Word 2003 WordprocessingML format.");
                    break;
                case LoadFormat.HTML:
                    System.out.println("\tHTML format.");
                    break;
                case LoadFormat.MHTML:
                    System.out.println("\tMHTML (Web archive) format.");
                    break;
                case LoadFormat.ODT:
                    System.out.println("\tOpenDocument Text.");
                    break;
                case LoadFormat.OTT:
                    System.out.println("\tOpenDocument Text Template.");
                    break;
                case LoadFormat.DOC_PRE_WORD_60:
                    System.out.println("\tMS Word 6 or Word 95 format.");
                    break;
                case LoadFormat.UNKNOWN:
                    System.out.println("\tUnknown format.");
                    break;
            }
            if (info.isEncrypted()) {
                System.out.println("\tAn encrypted document.");
                FileUtils.copyFile(new File(fileName), new File(encryptedDir, nameOnly));
            } else {
                switch (info.getLoadFormat()) {
                    case LoadFormat.DOC_PRE_WORD_60:
                        FileUtils.copyFile(new File(fileName), new File(pre97Dir, nameOnly));
                        break;
                    case LoadFormat.UNKNOWN:
                        FileUtils.copyFile(new File(fileName), new File(unknownDir, nameOnly));
                        break;
                    default:
                        FileUtils.copyFile(new File(fileName), new File(supportedDir, nameOnly));
                        break;
                }
            }
        }

```

## Comment détecter le format de fichier Java

La méthode `FileFormatUtil.detectFileFormat()` examine l’en‑tête du fichier et renvoie un objet `FileFormatInfo`. Cet objet vous indique le **load format**, si le fichier est chiffré, et d’autres métadonnées utiles. En utilisant ces informations, vous pouvez programmatique **identify unknown file types** et décider comment traiter chaque fichier.

## Identifier les types de fichiers inconnus

Lorsque l'API renvoie `LoadFormat.UNKNOWN`, le fichier est soit corrompu, soit utilise un format que Aspose.Words ne prend pas en charge. Dans notre exemple de code, nous déplaçons ces fichiers vers le dossier **Unknown** afin que vous puissiez les examiner plus tard.

## Problèmes courants et solutions

| Problème | Raison | Solution |
|----------|--------|----------|
| Les fichiers sont toujours placés dans le dossier *Supported* | `FileFormatUtil` n’a pas pu lire l’en‑tête (par ex., fichier vide) | Assurez‑vous de fournir le chemin de fichier correct et que le fichier n’est pas de taille zéro. |
| Les fichiers chiffrés génèrent une exception | Tentative de lecture sans gérer le chiffrement | Utilisez la vérification `info.isEncrypted()` avant tout traitement supplémentaire, comme indiqué dans le code. |
| Les documents Word pré‑97 non détectés | Les anciens formats nécessitent le cas `DOC_PRE_WORD_60` | Conservez le bloc `case LoadFormat.DOC_PRE_WORD_60` pour les diriger vers le dossier *Pre97*. |

## Questions fréquentes

### Comment installer Aspose.Words pour Java ?

Vous pouvez télécharger Aspose.Words pour Java depuis le [lien ici](https://releases.aspose.com/words/java/) et suivre les instructions d’installation fournies.

### Quels sont les formats de documents pris en charge ?

Aspose.Words pour Java prend en charge divers formats de documents, notamment DOC, DOCX, RTF, HTML, ODT, et plus encore. Consultez la documentation officielle pour la liste complète.

### Comment détecter les documents chiffrés avec Aspose.Words pour Java ?

Utilisez la méthode `FileFormatUtil.detectFileFormat()` ; le drapeau `FileFormatInfo.isEncrypted()` retourné indique le chiffrement, comme démontré dans ce guide.

### Existe‑t‑il des limitations lors du travail avec d’anciens formats de documents ?

Les anciens formats comme MS Word 6 ou Word 95 peuvent manquer de fonctionnalités modernes et présenter des problèmes de compatibilité. Envisagez de les convertir vers des formats plus récents lorsque cela est possible.

### Puis‑je automatiser la détection du format de document dans mon application Java ?

Oui, intégrez le code fourni dans le pipeline de traitement de votre application. Cela permet un tri et une gestion automatiques en fonction des formats détectés.

---

**Dernière mise à jour :** 2025-12-20  
**Testé avec :** Aspose.Words for Java 24.12 (latest)  
**Auteur :** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}