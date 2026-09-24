---
date: 2026-02-22
description: Apprenez à détecter le format de document Java avec Aspose.Words et à
  déplacer automatiquement les fichiers selon leur format. Identifiez les fichiers
  DOC, DOCX et plus encore.
linktitle: Determining Document Format
second_title: Aspose.Words Java Document Processing API
title: Détecter le format du document Java à l'aide d'Aspose.Words pour Java
url: /fr/java/document-loading-and-saving/determining-document-format/
weight: 25
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# détecter le format de document java avec Aspose.Words for Java

Lorsque vous devez **detect document format java** dans un lot de fichiers, la capacité de les trier automatiquement dans les bons dossiers peut vous faire gagner des heures de travail manuel. Dans ce tutoriel, nous vous montrerons comment Aspose.Words for Java facilite l’identification des formats Word, RTF, HTML, ODT et bien d’autres, puis **move files by format** dans des répertoires organisés.

## Réponses rapides
- **What does “detect document format java” mean?** C’est le processus d’identification programmatique du format de traitement de texte d’un fichier (DOC, DOCX, RTF, etc.) à l’aide de code Java.  
- **Which library provides this capability?** Aspose.Words for Java offre l’API `FileFormatUtil.detectFileFormat`.  
- **Can the utility also handle encrypted files?** Oui – le drapeau `FileFormatInfo.isEncrypted()` indique si un document est protégé par mot de passe.  
- **Do I need a license for production use?** Une licence commerciale Aspose.Words est requise pour les déploiements non‑évaluatifs.  
- **Is it possible to move files automatically after detection?** Absolument – combinez le résultat de la détection avec `FileUtils.copyFile` pour trier les fichiers dans des dossiers personnalisés.

## Qu’est-ce que detect document format java ?
`detect document format java` fait référence à l’utilisation de code Java pour inspecter l’en‑tête binaire d’un fichier et déterminer à quel format de traitement de texte il appartient (par ex., DOC, DOCX, ODT). Aspose.Words lit le fichier sans le charger complètement, rendant l’opération rapide et efficace en mémoire.

## Pourquoi déplacer les fichiers par format ?
Organiser les documents par leur format natif simplifie le traitement en aval :

- **Batch conversions** deviennent simples lorsque tous les fichiers DOCX se trouvent dans un même dossier.  
- **Legacy support** : vous pouvez isoler les fichiers Word antérieurs à 97 pour un traitement spécial.  
- **Security** : les documents chiffrés peuvent être mis en quarantaine automatiquement.  

## Prérequis

Avant de commencer, assurez-vous d’avoir :

- [Aspose.Words for Java](https://releases.aspose.com/words/java/) (téléchargez la dernière version)  
- Java Development Kit (JDK) 8 ou supérieur installé  
- Familiarité de base avec Java I/O et les flux  

## Étape 1 : Configurer les répertoires pour chaque format

Nous créons d’abord une structure de dossiers propre où les fichiers détectés seront déplacés. Cela garde le flux de travail ordonné et facilite l’ajout de nouvelles catégories de formats ultérieurement.

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

> **Conseil pro :** Utilisez des chemins absolus ou configurez le répertoire de base via un fichier de propriétés pour éviter le codage en dur des chemins dans le code de production.

## Étape 2 : Détecter le format du document et déplacer les fichiers

Le cœur de **detect document format java** se trouve dans la boucle ci‑dessous. Elle parcourt chaque fichier, détermine son type et le copie dans le dossier approprié.

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

Le bloc `switch` peut être étendu pour couvrir tous les formats qui vous intéressent. Chaque cas affiche un message convivial puis déplace le fichier vers le dossier correspondant.

## Code source complet pour détecter le format de document java

Ci‑dessous se trouve l’exemple complet, prêt à l’exécution, qui combine la configuration des répertoires et la logique de détection. Copiez‑le dans une classe Java, ajustez le chemin de base, et exécutez‑le sur un dossier contenant des documents mixtes.

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

## Problèmes courants et dépannage

| Issue | Why it happens | How to fix |
|-------|----------------|------------|
| **`FileFormatUtil.detectFileFormat` returns `UNKNOWN`** | Le fichier est corrompu ou utilise un format non‑Word. | Vérifiez l’extension du fichier, ou ajoutez un repli pour le déplacer vers le dossier *Unknown* (déjà présent dans l’exemple). |
| **Encrypted files throw an exception** | L’API tente de lire le contenu avant de vérifier le chiffrement. | Appelez toujours `info.isEncrypted()` avant toute autre opération sur le document. |
| **Directory creation fails on Linux** | Permissions insuffisantes ou dossier parent manquant. | Assurez‑vous que le processus Java a les droits d’écriture et que le chemin de base existe. |

## Questions fréquentes

**Q : Comment installer Aspose.Words for Java ?**  
R : Vous pouvez télécharger Aspose.Words for Java depuis le [here](https://releases.aspose.com/words/java/) et suivre les instructions d’installation fournies.

**Q : Quels formats de documents sont pris en charge pour la détection ?**  
R : Aspose.Words peut détecter DOC, DOCX, DOT, DOTX, DOCM, DOTM, RTF, HTML, MHTML, ODT, OTT, FLAT_OPC, WORD_ML, ainsi que les anciens formats antérieurs à 97, entre autres.

**Q : Ce code peut‑il gérer les documents protégés par mot de passe ?**  
R : Oui. Le drapeau `FileFormatInfo.isEncrypted()` identifie les fichiers chiffrés, vous permettant de les déplacer vers un dossier sécurisé sans les ouvrir.

**Q : Y a‑t‑il un impact sur les performances lors de l’analyse de gros dossiers ?**  
R : La détection ne lit que l’en‑tête du fichier, ainsi même des milliers de fichiers sont traités rapidement. Pour des lots très volumineux, envisagez l’utilisation de flux parallèles.

**Q : Comment étendre le script pour convertir les formats non pris en charge ?**  
R : Après la détection, vous pouvez appeler `Document.save` avec le format de sortie souhaité pour tout type source supporté.

## Conclusion

En utilisant **detect document format java** avec Aspose.Words, vous obtenez un moyen fiable de trier, mettre en quarantaine ou convertir automatiquement les fichiers liés à Word. Le code d’exemple montre comment créer une hiérarchie de dossiers propre, identifier le format de chaque fichier et le déplacer en conséquence—vous faisant gagner du temps et réduisant les erreurs manuelles.

---

**Dernière mise à jour :** 2026-02-22  
**Testé avec :** Aspose.Words for Java 24.12 (latest)  
**Auteur :** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}