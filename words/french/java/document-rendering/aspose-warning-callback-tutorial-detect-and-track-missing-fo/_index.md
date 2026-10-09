---
category: general
date: 2026-03-17
description: Apprenez le tutoriel sur le rappel d’avertissement Aspose pour détecter
  et suivre les polices manquantes dans les documents Java, avec un exemple complet
  et exécutable.
draft: false
keywords:
- aspose warning callback tutorial
- detect missing fonts
- track missing fonts
language: fr
og_description: Maîtrisez le tutoriel du rappel d’avertissement Aspose pour détecter
  les polices manquantes et suivre les polices manquantes dans votre flux de travail
  de traitement de texte Java.
og_title: Tutoriel du rappel d’avertissement Aspose – Détecter les polices manquantes
tags:
- Aspose.Words
- Java
- Font Substitution
- Document Processing
title: Tutoriel sur le rappel d’avertissement Aspose – Détecter et suivre les polices
  manquantes
url: /fr/java/document-rendering/aspose-warning-callback-tutorial-detect-and-track-missing-fo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# tutoriel du rappel d'avertissement aspose – Détecter et suivre les polices manquantes

Vous vous êtes déjà demandé comment **détecter les polices manquantes** lors de la conversion ou de la modification de fichiers Word avec Aspose.Words ? Vous n'êtes pas seul. Dans de nombreux projets réels, une police errante peut provoquer des anomalies de mise en page, et vous avez besoin d'un moyen fiable pour **suivre les polices manquantes** avant qu'elles ne vous posent problème plus tard.  

Bonne nouvelle ? Le **tutoriel du rappel d'avertissement aspose** vous fournit un crochet programmatique propre qui affiche exactement les avertissements de substitution de police au moment où ils se produisent. Dans ce guide, nous parcourrons la configuration du rappel, le chargement d'un document et la visualisation des avertissements en action—tout en Java.

À la fin de cet article, vous serez capable de repérer automatiquement les polices manquantes, de les consigner, et de décider d'incorporer un remplacement ou d'ajuster vos fichiers sources. Aucun outil externe requis.

## Prérequis

- **Java 8+** (le code se compile avec n'importe quel JDK récent)
- **Aspose.Words for Java** version 23.10 ou plus récent – téléchargez depuis le portail Aspose ou ajoutez la dépendance Maven.
- Un fichier DOCX d'exemple qui référence intentionnellement une police que vous n'avez pas installée (par ex., « Comic Sans MS » sur une machine Linux).

C’est tout—pas de bibliothèques supplémentaires, pas d'étapes de construction complexes.

## Étape 1 : Enregistrer un rappel d'avertissement – Le cœur du tutoriel du rappel d'avertissement aspose

La première chose que le tutoriel vous enseigne est comment attacher un écouteur d'avertissement. Aspose.Words génère un objet `WarningInfo` pour chaque problème rencontré, et le drapeau `WarningSource.FONT_SUBSTITUTION` nous indique exactement quand une police est remplacée.

```java
import com.aspose.words.*;

public class FontDiagnostics {
    public static void main(String[] args) throws Exception {

        // Step 1: Register a warning callback to capture font substitution warnings.
        Document.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // We only care about font‑substitution events.
                if (info.getSource() == WarningSource.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution warning:");
                    System.out.println("  Original:   " + info.getDescription());
                    System.out.println("  Substituted:" + info.getAdditionalInfo());
                }
            }
        });
```

**Pourquoi c'est important :** Sans le rappel, Aspose remplace silencieusement les polices manquantes, et vous ne savez jamais quels glyphes peuvent être altérés. En consignant l'avertissement, vous pouvez **détecter les polices manquantes** tôt et décider d'incorporer la bonne.

> **Astuce :** Si vous devez collecter les avertissements pour un rapport ultérieur, stockez‑les dans une `List<WarningInfo>` au lieu de les imprimer directement.

## Étape 2 : Charger le document – Où les polices manquantes peuvent se cacher

Nous chargeons maintenant le DOCX qui pourrait référencer des polices non présentes sur la machine. L'action de chargement déclenche le rappel d'avertissement si des polices sont manquantes.

```java
        // Step 2: Load a document that may contain missing fonts.
        Document document = new Document("YOUR_DIRECTORY/input.docx");
```

**Que se passe-t-il en coulisses ?** Aspose analyse les définitions de style du document, parcourt chaque segment de texte, et vérifie le référentiel de polices du système. Lorsqu'il ne trouve pas de correspondance exacte, il utilise une police de substitution et déclenche l'avertissement que nous venons d'attacher.

## Étape 3 : Enregistrer le document – Libérer les avertissements

Enfin, nous enregistrons le document. L'opération d'enregistrement réévalue également les polices, de sorte que les avertissements qui n'ont pas été émis lors du chargement apparaissent maintenant.

```java
        // Step 3: Save the document; any font substitution warnings will be printed by the callback.
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

Lorsque vous exécuterez le programme, vous verrez une sortie console similaire à :

```
Font substitution warning:
  Original:   Font "Comic Sans MS" not found.
  Substituted: Using "Arial" as fallback.
```

Cette sortie prouve que le **tutoriel du rappel d'avertissement aspose** fonctionne, et que vous avez **détecté les polices manquantes** avec succès et que vous **suivez maintenant les polices manquantes** via le journal.

## Comment détecter les polices manquantes dans un document Word – Au‑delà des bases

L'approche par rappel est excellente pour des exécutions ponctuelles, mais parfois vous avez besoin d'un utilitaire réutilisable. Voici un petit wrapper que vous pouvez intégrer à n'importe quel projet :

```java
public class FontMissingChecker {
    private final List<String> missingFonts = new ArrayList<>();

    public FontMissingChecker() {
        Document.setWarningCallback((WarningInfo info) -> {
            if (info.getSource() == WarningSource.FONT_SUBSTITUTION) {
                missingFonts.add(info.getDescription());
            }
        });
    }

    public List<String> check(String path) throws Exception {
        new Document(path); // triggers warnings
        return missingFonts;
    }
}
```

Appelez‑le ainsi :

```java
FontMissingChecker checker = new FontMissingChecker();
List<String> fonts = checker.check("input.docx");
if (!fonts.isEmpty()) {
    System.out.println("Missing fonts detected:");
    fonts.forEach(System.out::println);
}
```

Vous avez maintenant une méthode réutilisable **detect missing fonts** qui renvoie une liste que vous pouvez injecter dans un pipeline CI ou une interface utilisateur.

## Suivi des polices manquantes avec Aspose.Words – Reporting pour les équipes

Dans une équipe plus grande, vous pourriez vouloir produire un rapport CSV de toutes les polices manquantes à travers de nombreux documents. Combinez l'utilitaire précédent avec une simple itération de fichiers :

```java
import java.nio.file.*;
import java.io.*;

public class BulkFontReporter {
    public static void main(String[] args) throws Exception {
        Path folder = Paths.get("YOUR_DIRECTORY");
        try (BufferedWriter writer = Files.newBufferedWriter(folder.resolve("missing-fonts-report.csv"))) {
            writer.write("Document,Missing Font\n");
            Files.list(folder)
                 .filter(p -> p.toString().endsWith(".docx"))
                 .forEach(p -> {
                     try {
                         FontMissingChecker checker = new FontMissingChecker();
                         List<String> missing = checker.check(p.toString());
                         for (String msg : missing) {
                             // Extract font name from description
                             String font = msg.replaceAll("Font \"(.*?)\".*", "$1");
                             writer.write(p.getFileName() + "," + font + "\n");
                         }
                     } catch (Exception e) {
                         // In a real app, log the error
                     }
                 });
        }
        System.out.println("Report generated at missing-fonts-report.csv");
    }
}
```

L'exécution de ce script vous fournira un CSV **track missing fonts** que chaque développeur pourra consulter avant de valider un document en production.

## Pièges courants & comment les éviter

| Problème | Pourquoi cela se produit | Solution |
|----------|--------------------------|----------|
| **Rappel ne se déclenche pas** | Vous avez oublié de définir le rappel **avant** de charger le document. | Placez `Document.setWarningCallback` tout en haut de `main`. |
| **Seul le premier avertissement apparaît** | Aspose met en cache les avertissements par instance de `Document`. | Utilisez un nouvel objet `Document` pour chaque fichier, ou réinitialisez le rappel entre les exécutions. |
| **Nom de police incorrect dans le journal** | La description contient du texte supplémentaire (« Font … not found »). | Supprimez-le avec une expression régulière comme montré dans l'exemple CSV. |
| **Impact sur les performances avec de gros lots** | Le rappel s'exécute sur chaque segment de texte, ce qui peut être coûteux. | Limitez la vérification à une étape pré‑vol, sautez l'enregistrement si vous avez seulement besoin de la détection. |

## Résultats attendus & Vérification

1. **Sortie console** – Vous devriez voir au moins une ligne « Font substitution warning » pour chaque police manquante.  
2. **Rapport CSV** – Après que le script en masse se termine, ouvrez `missing-fonts-report.csv` et vérifiez que chaque ligne indique le nom du document et la police manquante exacte.  
3. **Document enregistré** – Le DOCX de sortie sera rendu avec les polices de substitution, mais la mise en page visuelle peut différer de l'original.

Si l'une de ces étapes ne se comporte pas comme décrit, vérifiez que le JAR Aspose.Words est bien dans votre classpath et que le `input.docx` référence réellement une police absente de votre système d'exploitation.

## Conclusion

Vous venez de terminer un **tutoriel du rappel d'avertissement aspose** qui montre comment **détecter les polices manquantes** et **suivre les polices manquantes** dans les applications Java. En enregistrant un écouteur d'avertissement, en chargeant le document, et éventuellement en exportant les résultats, vous obtenez une visibilité complète sur les problèmes liés aux polices avant qu'ils n'apparaissent en production.

Ensuite, vous pourriez explorer :

- Incorporer directement la police manquante avec `LoadOptions.setFontSubstitution`.
- Utiliser la classe `FontSettings` pour mapper les polices manquantes à des substituts spécifiques.
- Intégrer le rapport CSV dans un pipeline CI/CD pour faire échouer les builds lorsqu'apparaissent des polices non documentées.

Essayez-le, ajustez les rappels pour qu'ils correspondent à votre framework de journalisation, et voyez votre flux de travail documentaire devenir beaucoup plus robuste. Bon codage !

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}