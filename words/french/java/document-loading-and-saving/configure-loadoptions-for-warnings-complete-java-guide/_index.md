---
category: general
date: 2026-06-30
description: Configurez les LoadOptions pour les avertissements dans Aspose.Words
  Java. Apprenez à mettre en place un rappel d’avertissement pour la substitution
  de police et les autres avertissements liés aux options de chargement.
draft: false
keywords:
- configure loadoptions for warnings
- Aspose.Words font substitution
- Java warning callback
- document loading options
- handle font warnings
language: fr
og_description: Configurez LoadOptions pour les avertissements dans Aspose.Words Java.
  Ce guide montre comment capturer les alertes de substitution de police avec un rappel
  d’avertissement.
og_title: Configurer LoadOptions pour les avertissements – Tutoriel Java
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: Configure LoadOptions for warnings in Aspose.Words Java. Learn to set
    up a warning callback for font substitution and other load‑options warnings.
  headline: Configure LoadOptions for Warnings – Complete Java Guide
  type: TechArticle
tags:
- aspose-words
- java
- warnings
- font-substitution
title: Configurer les LoadOptions pour les avertissements – Guide complet Java
url: /fr/java/document-loading-and-saving/configure-loadoptions-for-warnings-complete-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Configurer LoadOptions pour les avertissements – Guide complet Java

Vous avez déjà eu besoin de **configurer LoadOptions pour les avertissements** lors de l'ouverture d'un document Word avec Aspose.Words for Java ? Vous n'êtes pas seul. De nombreux développeurs rencontrent un problème lorsqu'une police manquante est remplacée silencieusement, laissant le PDF final avec une apparence non conforme à la marque. La bonne nouvelle ? En branchant un **callback d'avertissement Java** dans votre `LoadOptions`, vous pouvez capturer chaque alerte de substitution de police dès qu'elle se produit.

Dans ce tutoriel, nous parcourrons un exemple pratique qui montre non seulement comment configurer le callback mais explique également *pourquoi* chaque élément est important. À la fin, vous serez capable de **gérer les avertissements de police**, les consigner, ou même remplacer les polices à la volée — sans aucune supposition.

## Ce que vous en retirerez

- Un programme Java entièrement exécutable qui affiche chaque avertissement de substitution de police.
- Une compréhension du fonctionnement de la **substitution de police Aspose.Words**.
- Des astuces pour personnaliser la gestion des avertissements pour des projets plus importants.
- Un aperçu des **options de chargement de document** et du moment où les ajuster.

> **Prérequis :** Java 8+ et la bibliothèque Aspose.Words for Java (version 23.9 ou ultérieure). Aucune autre dépendance externe n'est requise.

---

## Étape 1 : Configurer LoadOptions pour les avertissements

La première chose dont vous avez besoin est une instance de `LoadOptions` qui sait qu'elle doit signaler les avertissements. Considérez `LoadOptions` comme la boîte à outils que vous remettez à Aspose.Words avant même qu'il n'ouvre le fichier.

```java
// Step 1: Create LoadOptions and attach a warning callback.
LoadOptions loadOptions = new LoadOptions();
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Only react to font‑substitution warnings.
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("Font substitution detected: " + info.getDescription());
        }
    }
});
```

**Pourquoi c'est important :**  
`LoadOptions` contrôle la façon dont la bibliothèque lit le document. En assignant un `IWarningCallback`, vous indiquez à Aspose.Words d'appeler votre code chaque fois qu'il rencontre quelque chose d'important — comme une police manquante. Sans cela, la bibliothèque substituerait silencieusement la police et vous ne le sauriez jamais.

> **Astuce :** Si vous souhaitez capturer *tous* les avertissements, supprimez la condition `if`. Pour l'instant, nous nous concentrons sur les problèmes de police car ils sont la source la plus courante de surprises de mise en page.

---

## Étape 2 : Charger le document en utilisant les options configurées

Maintenant que le callback est prêt, chargez votre `.docx` (ou tout autre format supporté) avec les mêmes `LoadOptions`. C'est ici que les **options de chargement de document** prennent réellement effet.

```java
// Step 2: Load the document with the warning‑aware LoadOptions.
Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**Dans les coulisses :**  
Lorsque Aspose.Words analyse `input.docx`, il parcourt les tables de polices. Si une police référencée dans le document n'est pas installée sur la machine hôte, le moteur génère un avertissement `FONT_SUBSTITUTION`, qui déclenche immédiatement le callback que nous avons défini précédemment.

---

## Étape 3 : Enregistrer le document – Les avertissements ont déjà été affichés

Enregistrer le document est simple, mais c'est le moment où vous pouvez vérifier que le callback s'est déclenché correctement. Tous les avertissements sont affichés pendant l'étape de chargement, donc l'opération d'enregistrement n'est qu'un nettoyage.

```java
// Step 3: Save the document. Any warnings were already printed in Step 1.
document.save("YOUR_DIRECTORY/output.docx");
```

**Sortie console attendue :**  

```
Font substitution detected: Font 'Calibri' is not installed. Substituted with 'Arial'.
Font substitution detected: Font 'Times New Roman' is not installed. Substituted with 'Liberation Serif'.
```

Si vous ne voyez rien, soit le document n'utilise que des polices installées, soit le callback n'a pas été correctement branché — revérifiez l'étape 1.

---

## Étape 4 : Étendre le callback pour **gérer les avertissements de police** de manière élégante

Afficher dans la console convient pour les démonstrations, mais le code de production nécessite souvent une gestion plus riche : journalisation dans un fichier, envoi d'alertes, ou même remplacement des polices de façon programmatique.

```java
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            // Log to a file (simple example)
            try (FileWriter fw = new FileWriter("font-warnings.log", true)) {
                fw.write("WARN: " + info.getDescription() + System.lineSeparator());
            } catch (IOException e) {
                e.printStackTrace();
            }
            // Optionally replace the missing font with a fallback.
            FontSettings.getDefaultInstance().setSubstitutionSettings(
                new FontSubstitutionSettings() {{
                    getTableSubstitution().addSubstitutes("Calibri", "Arial");
                }}
            );
        }
    }
});
```

**Pourquoi le faire :**  
Un fichier de journal vous offre une visibilité post‑mortem, surtout lors du traitement de lots de documents. Le bloc de substitution optionnel montre comment **configurer LoadOptions pour les avertissements** *et* intervenir pour appliquer une politique de police d'entreprise.

---

## Avancé : Contrôler d'autres scénarios de **substitution de police Aspose.Words**

Le callback d'avertissement n'est pas limité aux polices manquantes. Vous pouvez également capturer :

- **Caractères Unicode non pris en charge** (`WarningType.UNSUPPORTED_CHAR`).
- **Problèmes de scripts complexes** (`WarningType.COMPLEX_SCRIPT`).

Il suffit d'étendre la condition `if` :

```java
if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
    // handle fonts
} else if (info.getWarningType() == WarningType.UNSUPPORTED_CHAR) {
    System.out.println("Unsupported character: " + info.getDescription());
}
```

Cela rend votre solution robuste pour les documents multilingues, un cas limite courant dans les applications mondiales.

---

## Exemple complet fonctionnel

Ci-dessous le programme complet, prêt à être exécuté. Copiez‑le dans n'importe quel IDE Java, remplacez les espaces réservés `YOUR_DIRECTORY`, et cliquez sur *Run*.

```java
import com.aspose.words.*;

import java.io.FileWriter;
import java.io.IOException;

public class FontSubstitutionDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Configure LoadOptions for warnings.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution: " + info.getDescription());

                    // Optional: Log to a file.
                    try (FileWriter fw = new FileWriter("font-warnings.log", true)) {
                        fw.write("WARN: " + info.getDescription() + System.lineSeparator());
                    } catch (IOException e) {
                        e.printStackTrace();
                    }

                    // Optional: Force a specific fallback font.
                    FontSettings.getDefaultInstance().setSubstitutionSettings(
                        new FontSubstitutionSettings() {{
                            getTableSubstitution().addSubstitutes("Calibri", "Arial");
                        }}
                    );
                }
            }
        });

        // Step 2: Load the document using the configured LoadOptions.
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // Step 3: Save the document. Warnings have already been printed.
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### Résultat attendu

- La console affiche les avertissements de substitution de police.
- `font-warnings.log` contient une liste horodatée (si vous avez conservé la journalisation optionnelle).
- `output.docx` est enregistré avec les polices substituées, correspondant au remplacement que vous avez défini.

---

## Pièges courants et comment les éviter

| Piège | Pourquoi cela se produit | Solution |
|-------|--------------------------|----------|
| **Aucun avertissement n'apparaît** | Le callback n'a pas été attaché, ou le document n'utilise que des polices installées. | Vérifiez que `loadOptions.setWarningCallback(...)` est appelé *avant* de charger le document. |
| **FileNotFoundException** sur `input.docx` | Le chemin est incorrect ou le fichier n'est pas inclus dans le projet. | Utilisez un chemin absolu ou placez le fichier dans le dossier resources du projet. |
| **Ralentissement des performances** lors du traitement de milliers de documents | Journalisation excessive sur disque pour chaque avertissement. | Mettez en mémoire tampon les journaux et écrivez par lots, ou limitez la journalisation aux avertissements critiques uniquement. |
| **Substitution de police inattendue** malgré le fallback | La table de substitution n'a pas été appliquée assez tôt. | Définissez les paramètres de substitution **avant** de charger le document, ou utilisez `FontSettings.setSubstitutionSettings` globalement. |

---

## Prochaines étapes

Maintenant que vous avez maîtrisé **configurer LoadOptions pour les avertissements**, envisagez ces sujets complémentaires :

- **Traitement par lots** : Parcourir un répertoire de documents, agrégant tous les avertissements de police dans un rapport unique.
- **Fournisseurs de polices personnalisés** : Charger les polices depuis un partage réseau ou des ressources intégrées au lieu du système d'exploitation local.
- **Intégrer avec des frameworks de journalisation** comme Log4j pour une traçabilité de niveau entreprise.
- Explorer d'autres **options de chargement de document** telles que la détection `LoadFormat` ou la gestion `Password` pour les fichiers protégés.

Chacune de ces options repose sur le même schéma — créez un objet `LoadOptions`, attachez les callbacks appropriés, et laissez Aspose.Words faire le travail lourd.

---

## Conclusion

Nous avons exploré en profondeur comment **configurer LoadOptions pour les avertissements** dans Aspose.Words for Java, mettre en place un **callback d'avertissement Java**, et utiliser ces informations pour **gérer les avertissements de police** de manière intelligente. Le code est concis, les concepts sont clairs, et vous disposez désormais d'une base solide pour étendre la gestion des avertissements à d'autres scénarios comme les caractères non pris en charge ou les scripts complexes.

Essayez-le, ajustez la table de substitution pour correspondre aux polices de votre marque, et voyez ces remplacements de police silencieux disparaître. Bon codage !

--- 

![Diagramme montrant le flux de configuration de LoadOptions pour les avertissements, le chargement d'un document, la capture des événements de substitution de police et l'enregistrement du résultat](configure-loadoptions-for-warnings-diagram.png "Flux de configuration de LoadOptions pour les avertissements")


## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s'appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités supplémentaires de l'API et explorer des approches d'implémentation alternatives dans vos propres projets.

- [Capturer les avertissements de substitution de police en Java avec Aspose.Words – Guide complet](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Comment définir LoadOptions dans Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Comment charger des documents RTF en configurant les options de chargement RTF dans Aspose.Words for Java](/words/english/java/document-loading-and-saving/configuring-rtf-load-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}