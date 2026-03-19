---
category: general
date: 2026-03-19
description: Apprenez à capturer les avertissements dans Aspose.Words pour Java et
  à détecter les polices manquantes. Ce guide étape par étape montre également comment
  gérer les polices manquantes gracieusement.
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- how to detect missing fonts
- handle missing fonts
language: fr
og_description: Comment capturer les avertissements dans Aspose.Words for Java, détecter
  les polices manquantes et gérer les polices manquantes avec un exemple de code complet.
og_title: Comment capturer les avertissements – détecter les polices manquantes dans
  Aspose.Words
tags:
- Aspose.Words
- Java
- Font Substitution
- Document Processing
title: Comment capturer les avertissements – détecter les polices manquantes dans
  Aspose.Words
url: /fr/java/document-rendering/how-to-capture-warnings-detect-missing-fonts-in-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment capturer les avertissements – détecter les polices manquantes dans Aspose.Words

Vous vous êtes déjà demandé **comment capturer les avertissements** lorsqu'un document Word se charge et que certaines polices ne sont pas disponibles sur la machine ? Vous n'êtes pas seul. Dans de nombreux projets réels, les polices manquantes provoquent des changements de mise en page silencieux, et la seule façon de savoir ce qui s'est passé est d'écouter le flux d'avertissements émis par Aspose.Words.  

Dans ce tutoriel, nous parcourrons un exemple complet, prêt à l'exécution, qui **détecte les polices manquantes**, vous montre **comment détecter les polices manquantes** de façon programmatique, et donne même un conseil rapide sur **la gestion des polices manquantes** afin que votre sortie reste prévisible.

> **Note rapide :** Le code fonctionne avec Aspose.Words 23.9 (ou plus récent) et nécessite Java 8+.

---

## Ce dont vous aurez besoin

- **Aspose.Words for Java** (dépendance Maven/Gradle ou JAR sur le classpath)  
- Un fichier Word (`input.docx`) qui référence une police non installée sur votre système (par ex., “Comic Sans MS”)  
- Un IDE Java ou une configuration simple en ligne de commande `javac`/`java`  

Aucune autre bibliothèque n'est requise — tout le reste se trouve dans le package Aspose.Words.

---

## Étape 1 – Configurer LoadOptions pour capturer les avertissements  

Pour commencer à écouter les avertissements, vous devez créer une instance de `LoadOptions`. Cet objet indique au chargeur de suivre tous les problèmes qu'il rencontre, comme les polices manquantes.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Create LoadOptions that will store warning information
        LoadOptions loadOptions = new LoadOptions();

        // ... the rest of the code follows
```

**Pourquoi c'est important :** Sans `LoadOptions`, le chargeur remplace silencieusement les polices manquantes par la police système par défaut, et vous ne sauriez jamais qu'une substitution a eu lieu. Activer les avertissements vous donne une visibilité totale.

---

## Étape 2 – Charger le document en utilisant LoadOptions  

Nous chargeons maintenant réellement le document. Le `LoadOptions` que nous venons de créer est passé au constructeur, de sorte que tous les avertissements générés pendant l'analyse sont capturés.

```java
        // Step 2: Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**Astuce :** Si vous traitez de nombreux fichiers en lot, réutilisez la même instance de `LoadOptions` pour éviter la création d'objets inutiles.

---

## Étape 3 – Parcourir les avertissements capturés  

Aspose.Words stocke chaque avertissement sous forme d'un objet `WarningInfo`. Nous ne nous intéressons qu'aux avertissements liés aux polices, nous filtrons donc pour `FontSubstitutionWarningInfo`.

```java
        // Step 3: Loop through all warnings generated while loading
        for (WarningInfo warning : document.getWarnings()) {
            // Step 3a: Keep only font substitution warnings
            if (warning instanceof FontSubstitutionWarningInfo) {
                FontSubstitutionWarningInfo fontWarning = (FontSubstitutionWarningInfo) warning;

                // Step 4: Output the requested and actual font names
                System.out.println("Requested: " + fontWarning.getRequestedFontName()
                        + " → Substituted: " + fontWarning.getActualFontName());
            }
        }
    }
}
```

**Explication :**  
- `document.getWarnings()` renvoie une liste de tous les avertissements survenus lors du chargement.  
- `FontSubstitutionWarningInfo` contient deux éléments cruciaux : la **police demandée** (celle demandée par le DOCX) et la **police réelle** à laquelle Aspose.Words a recours.  
- En affichant les deux, vous voyez immédiatement quelles polices sont manquantes et quelle substitution a eu lieu.

---

## Étape 4 – (Optionnel) Gérer les polices manquantes de façon programmatique  

Capturer les avertissements n'est que la moitié de l'histoire. Une fois que vous savez qu'une police est manquante, vous pouvez vouloir **gérer les polices manquantes** en fournissant une substitution personnalisée ou en consignant le problème pour une révision ultérieure.

```java
                // Optional: Replace the missing font with a known fallback
                FontSettings fontSettings = new FontSettings();
                fontSettings.getSubstitutionSettings().getTableSubstitution()
                    .addSubstitutes(fontWarning.getRequestedFontName(), "Arial");
                document.setFontSettings(fontSettings);
```

**Pourquoi faire cela ?**  
- Garantit un rendu cohérent sur toutes les machines.  
- Empêche les changements de mise en page inattendus dans les PDF ou images générés ultérieurement.  

Vous pouvez également stocker les détails de l'avertissement dans une base de données, envoyer un e‑mail à l'équipe de contenu, ou même interrompre le processus si une police critique est manquante.

---

## Exemple complet fonctionnel  

Voici le programme complet et exécutable. Remplacez simplement `YOUR_DIRECTORY/input.docx` par le chemin de votre fichier de test, ajoutez le JAR Aspose.Words à votre classpath, puis exécutez.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // 1️⃣ Create LoadOptions to capture warnings
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // 3️⃣ Iterate through all warnings
        for (WarningInfo warning : document.getWarnings()) {
            // 3a️⃣ Filter only font substitution warnings
            if (warning instanceof FontSubstitutionWarningInfo) {
                FontSubstitutionWarningInfo fontWarning = (FontSubstitutionWarningInfo) warning;

                // 4️⃣ Display the requested and actual font names
                System.out.println("Requested: " + fontWarning.getRequestedFontName()
                        + " → Substituted: " + fontWarning.getActualFontName());

                // 5️⃣ (Optional) Provide a custom fallback
                FontSettings fontSettings = new FontSettings();
                fontSettings.getSubstitutionSettings().getTableSubstitution()
                    .addSubstitutes(fontWarning.getRequestedFontName(), "Arial");
                document.setFontSettings(fontSettings);
            }
        }

        // 6️⃣ Save the document if you need to see the result with the fallback applied
        document.save("output.docx");
    }
}
```

**Sortie attendue** (lorsque “Comic Sans MS” est manquant) :

```
Requested: Comic Sans MS → Substituted: Arial
```

Après l'exécution du code de repli optionnel, le `output.docx` enregistré sera rendu en utilisant **Arial** partout où “Comic Sans MS” était initialement référencé.

---

## Questions fréquentes & cas limites  

| Question | Réponse |
|----------|--------|
| *Et si le document comporte plusieurs polices manquantes ?* | La boucle émettra un avertissement pour chacune. Vous pouvez les collecter dans un `Map<String, String>` pour un traitement par lot. |
| *Est‑ce que cela fonctionne pour les PDF générés à partir du document ?* | Absolument. La substitution de police se produit pendant la phase de chargement, donc toute exportation ultérieure (PDF, HTML, image) utilise les polices résolues. |
| *Puis‑je supprimer les avertissements au lieu de les capturer ?* | Oui — définissez `loadOptions.setWarningCallback(null);` mais vous perdrez la visibilité sur les polices manquantes. |
| *La liste des avertissements est‑elle vidée après l’enregistrement ?* | La collection d’avertissements appartient à l’instance `Document`. Après avoir appelé `document.save()`, la liste reste inchangée sauf si vous créez un nouveau `Document`. |
| *Qu’en est‑il des polices personnalisées incorporées dans le DOCX ?* | Les polices incorporées sont considérées comme disponibles ; Aspose.Words les utilisera même si elles ne sont pas installées sur le système hôte. |

---

## Astuces pro pour la production  

- **Cache FontSettings :** Si vous traitez des centaines de fichiers, créez un seul `FontSettings` avec vos substitutions préférées et réutilisez‑le pour éviter les surcoûts.  
- **Log Structured Data :** Au lieu de `System.out` simple, écrivez les avertissements dans un journal JSON — cela rend l’analyse en aval (ex. : « polices les plus manquantes ») triviale.  
- **Validate Early :** Effectuez un « dry‑load » rapide avec `LoadOptions` avant un traitement lourd ; arrêtez‑vous tôt si des polices critiques sont manquantes.  
- **Thread Safety :** Les objets `Document` ne sont pas thread‑safe. Gardez le traitement de chaque fichier dans son propre thread ou utilisez un `LoadOptions` thread‑local.  

---

## Conclusion  

Vous savez maintenant **comment capturer les avertissements** dans Aspose.Words pour Java, **détecter les polices manquantes**, et **gérer les polices manquantes** avec une stratégie de repli propre. En exploitant `LoadOptions` et en parcourant `document.getWarnings()`, vous obtenez une visibilité complète sur les événements de substitution de police, garantissant que vos documents générés apparaissent exactement comme prévu sur tous les environnements.

Prêt pour l’étape suivante ? Essayez d’étendre ce modèle pour **détecter les images manquantes**, **suivre les fonctionnalités non prises en charge**, ou même **intégrer automatiquement les polices manquantes** dans le fichier de sortie. La même approche de capture d’avertissements fonctionne pour de nombreux autres scénarios de traitement de documents, rendant votre code robuste et pérenne.

Bonne programmation, et que vos documents s'affichent toujours magnifiquement !

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}