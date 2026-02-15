---
category: general
date: 2026-02-15
description: Apprenez comment récupérer les polices manquantes lors du chargement
  d’un document Word en Java avec Aspose.Words. Inclut les rappels d’avertissement
  et la gestion de la substitution de polices.
draft: false
keywords:
- how to get missing fonts
- Aspose.Words missing font
- font substitution warning
- Java LoadOptions warning callback
- document processing Java
language: fr
og_description: Comment obtenir les polices manquantes en Java avec Aspose.Words.
  Découvrez les rappels d’avertissement, la gestion de la substitution de polices
  et les meilleures pratiques pour le traitement des documents.
og_title: Comment obtenir les polices manquantes en Java – Guide Aspose.Words
tags:
- Aspose.Words
- Java
- Font Management
title: Comment récupérer les polices manquantes en Java – Guide Aspose.Words
url: /fr/java/document-loading-and-saving/how-to-get-missing-fonts-in-java-aspose-words-guide/
---

final content.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment obtenir les polices manquantes en Java – Guide Aspose.Words

Vous avez déjà ouvert un document Word en Java uniquement pour voir des remplacements de polices étranges et vous demander **comment obtenir les polices manquantes** ? Vous n'êtes pas le premier à rencontrer cette surprise. Dans de nombreuses applications d'entreprise, les avertissements de polices manquantes peuvent compromettre la fidélité visuelle des rapports, contrats ou supports marketing.

Bonne nouvelle : Aspose.Words vous offre un moyen propre de capturer ces avertissements via un callback, afin que vous puissiez les consigner, les remplacer ou même alerter les utilisateurs avant que le document ne soit rendu. Dans ce tutoriel, nous parcourrons un exemple complet et exécutable qui montre **comment obtenir les polices manquantes**, explique pourquoi le callback est important, et couvre quelques astuces de cas limites que vous pourriez rencontrer dans des projets réels.

> **Conseil pro :** Si vous utilisez déjà Aspose.Words 22.12 ou une version plus récente, l'API présentée ci‑dessous fonctionne immédiatement sans configuration supplémentaire.

---

![Diagramme illustrant comment obtenir les polices manquantes à l'aide du rappel d'avertissement Aspose.Words](how-to-get-missing-fonts-diagram.png "diagramme comment obtenir les polices manquantes")

## Ce que couvre ce tutoriel

- Configurer un **callback d’avertissement Java LoadOptions** pour capturer les avertissements de substitution de police.  
- Filtrer les avertissements afin de ne voir que ceux liés aux polices manquantes.  
- Afficher un rapport clair et lisible indiquant quelles polices ont été substituées et par quoi elles ont été remplacées.  
- Conseils pour gérer les gros documents, personnaliser le niveau d’avertissement et intégrer la solution dans un pipeline de traitement plus large.

À la fin de ce guide, vous pourrez répondre à la question « **comment obtenir les polices manquantes** ? » avec un extrait de code prêt à l’emploi et une compréhension solide des mécanismes sous‑jacents.

### Prérequis

- Java 8 ou version supérieure installé.  
- Bibliothèque Aspose.Words for Java (téléchargez depuis le site officiel ou ajoutez via Maven/Gradle).  
- Un document Word qui référence une police non installée sur votre machine (par ex., `MissingFont.docx`).  

Si vous ne disposez d’aucun de ces éléments, récupérez la bibliothèque dès maintenant — l’ajouter à Maven est aussi simple que :

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version> <!-- replace with the latest version -->
</dependency>
```

---

## Étape 1 : Préparer une collection pour les avertissements de substitution de police

Avant de charger le document, nous avons besoin d’un endroit où stocker les avertissements émis par Aspose.Words. Un `ArrayList<WarningInfo>` fonctionne bien car il préserve l’ordre et nous permet d’itérer plus tard.

```java
import com.aspose.words.*;
import java.util.ArrayList;
import java.util.List;

// Step 1: Create a list that will hold warning information.
List<WarningInfo> fontWarnings = new ArrayList<>();
```

*Pourquoi c’est important :* Le callback d’avertissement peut se déclencher des dizaines de fois pour un même fichier — pensez à chaque glyphe manquant, chaque problème d’image incorporée, etc. En les collectant d’abord, vous gardez la phase de chargement rapide et différer le traitement à une boucle contrôlée.

---

## Étape 2 : Configurer LoadOptions avec un callback d’avertissement

Aspose.Words vous permet d’insérer un `IWarningCallback`. À l’intérieur du callback, nous ajouterons chaque `WarningInfo` à notre liste de l’étape 1.

```java
// Step 2: Set up LoadOptions with a custom warning callback.
LoadOptions loadOptions = new LoadOptions();
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Capture every warning; we'll filter later.
        fontWarnings.add(info);
    }
});
```

*Explication :* La méthode `warning` est invoquée **synchroniquement** pendant le chargement du document. En ajoutant simplement le `WarningInfo` dans `fontWarnings`, nous évitons tout I/O lourd (comme l’écriture dans un fichier) qui pourrait ralentir le chargement. Ce schéma — collecter‑puis‑traiter — est la façon recommandée de gérer de gros lots d’avertissements.

---

## Étape 3 : Charger le document en utilisant les options configurées

Nous lisons maintenant réellement le fichier Word. Si le document contient des polices qui ne sont pas installées, Aspose.Words les substituera automatiquement et déclenchera le callback d’avertissement que nous venons de brancher.

```java
// Step 3: Load the document with the warning‑aware LoadOptions.
String filePath = "YOUR_DIRECTORY/MissingFont.docx"; // adjust to your environment
Document doc = new Document(filePath, loadOptions);
```

*Ce qui se passe en coulisses :* Aspose.Words analyse la table des polices du fichier, la compare aux polices disponibles sur le système hôte, et pour chaque entrée manquante crée un `WarningInfo` avec `WarningSource.FontSubstitution`. Cette source sera la clé que nous utiliserons pour isoler les avertissements de police manquante.

---

## Étape 4 : Filtrer et afficher uniquement les avertissements de substitution de police

Après le chargement, `fontWarnings` peut contenir un mélange de messages (par ex., fonctionnalités obsolètes, problèmes d’image). Nous ne nous intéressons qu’aux polices manquantes, donc nous parcourons la liste et imprimons un rapport concis.

```java
// Step 4: Output any font‑substitution warnings that were captured.
for (WarningInfo warning : fontWarnings) {
    if (warning.getSource() == WarningSource.FontSubstitution) {
        System.out.println("Substituted '" + warning.getDescription() + "' with '" +
                           warning.getAdditionalInfo() + "'");
    }
}
```

**Exemple de sortie**

```
Substituted 'Comic Sans MS' with 'Arial'
Substituted 'Times New Roman PS' with 'Times New Roman'
```

*Pourquoi c’est utile :* Le champ `description` indique quelle police le document a demandée, tandis que `additionalInfo` indique quelle police Aspose.Words a réellement utilisée. Fort de ces données, vous pouvez :

- Inviter l'utilisateur à installer la police manquante.  
- Intégrer programmétiquement une police de substitution dans le document (`doc.getFontInfos().add(...)`).  
- Enregistrer l'événement pour les audits de conformité.

---

## Gestion des cas limites et des variations courantes

### 1. Supprimer les avertissements non liés aux polices

Si vous ne voulez que les messages relatifs aux polices, vous pouvez resserrer le callback :

```java
loadOptions.setWarningCallback(info -> {
    if (info.getSource() == WarningSource.FontSubstitution) {
        fontWarnings.add(info);
    }
});
```

Cela réduit la consommation de mémoire lors du traitement de très gros lots.

### 2. Ajuster la sévérité des avertissements

Aspose.Words catégorise les avertissements par `WarningType`. Pour les polices manquantes, vous verrez généralement `WarningType.FontSubstitution`. Si vous devez les traiter comme des erreurs (par ex., interrompre le chargement), lancez une exception à l’intérieur du callback :

```java
loadOptions.setWarningCallback(info -> {
    if (info.getSource() == WarningSource.FontSubstitution) {
        throw new RuntimeException("Missing font detected: " + info.getDescription());
    }
});
```

### 3. Travailler avec des flux au lieu de fichiers

Parfois, les documents proviennent d’une base de données ou d’une requête HTTP. La même approche fonctionne avec un `InputStream` :

```java
InputStream docStream = new ByteArrayInputStream(bytesFromDb);
Document doc = new Document(docStream, loadOptions);
```

N’oubliez pas de fermer le flux après le chargement.

### 4. Utiliser un dossier de polices personnalisé

Si vous disposez d’une collection de polices d’entreprise stockées sur un lecteur partagé, pointez Aspose.Words vers ce dossier :

```java
loadOptions.setFontSettings(new FontSettings());
loadOptions.getFontSettings().setFontsFolder("C:/CorporateFonts", true);
```

La bibliothèque recherchera alors ce répertoire *avant* de revenir aux polices système, réduisant considérablement le nombre d’avertissements de police manquante.

---

## Exemple complet fonctionnel

En rassemblant tous les éléments, voici une classe autonome que vous pouvez insérer dans n’importe quel projet Java :

```java
import com.aspose.words.*;
import java.util.ArrayList;
import java.util.List;

public class MissingFontDetector {

    public static void main(String[] args) {
        // 1️⃣ Prepare a collection for warnings.
        List<WarningInfo> fontWarnings = new ArrayList<>();

        // 2️⃣ Create LoadOptions with a warning callback.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(info -> fontWarnings.add(info));

        // (Optional) Point to a custom font folder.
        // FontSettings fontSettings = new FontSettings();
        // fontSettings.setFontsFolder("C:/CorporateFonts", true);
        // loadOptions.setFontSettings(fontSettings);

        // 3️⃣ Load the document.
        String docPath = "YOUR_DIRECTORY/MissingFont.docx";
        Document doc;
        try {
            doc = new Document(docPath, loadOptions);
        } catch (Exception e) {
            System.err.println("Failed to load document: " + e.getMessage());
            return;
        }

        // 4️⃣ Print missing‑font warnings.
        System.out.println("=== Missing Font Report ===");
        for (WarningInfo warning : fontWarnings) {
            if (warning.getSource() == WarningSource.FontSubstitution) {
                System.out.println("Substituted '" + warning.getDescription() + "' with '" +
                                   warning.getAdditionalInfo() + "'");
            }
        }
        System.out.println("=== End of Report ===");
    }
}
```

Exécutez ce programme, et vous verrez une liste ordonnée de chaque police qu’Aspose.Words a dû remplacer. Aucun bibliothèque supplémentaire, aucune magie cachée — juste du Java pur et la puissance de l’**API Aspose.Words missing font**.

---

## Conclusion

Nous avons répondu à la question fondamentale **comment obtenir les polices manquantes** dans un environnement Java en utilisant Aspose.Words. En attachant un callback d’avertissement `LoadOptions`, en collectant les objets `WarningInfo` et en filtrant les sources `FontSubstitution`, vous obtenez une visibilité complète sur les problèmes liés aux polices avant tout rendu. L’approche passe d’utilitaires mono‑fichier à des processeurs de lots massifs, et elle reste suffisamment flexible pour accueillir des dossiers de polices personnalisés, la gestion de la sévérité ou des entrées basées sur des flux.

Prochaines étapes ? Essayez d’intégrer les polices substituées directement dans le document (`doc.getFontInfos().add(...)`) afin que le fichier final soit réellement autonome, ou intégrez le rapport d’avertissement dans un tableau de bord de surveillance. Vous pouvez également explorer des sujets connexes tels que **document processing Java**, **Aspose.Words font substitution warning** et **Java LoadOptions warning callback** pour approfondir votre expertise.

Bon codage, et que vos documents s’affichent toujours avec les polices que vous attendez !

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}