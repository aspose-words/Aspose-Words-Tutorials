---
category: general
date: 2026-06-20
description: Comment définir un rappel dans Aspose.Words Java pour détecter les polices
  manquantes et personnaliser le chargement du document. Apprenez, étape par étape,
  à gérer les avertissements de substitution de police.
draft: false
keywords:
- how to set callback
- detect missing fonts
- handle missing fonts
- customize document loading
language: fr
og_description: Comment définir un rappel dans Aspose.Words Java pour détecter les
  polices manquantes, gérer les substitutions et personnaliser le chargement du document.
  Guide complet avec code.
og_title: Comment définir le callback – Détecter les polices manquantes dans Aspose.Words
  Java
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: how to set callback in Aspose.Words Java to detect missing fonts and
    customize document loading. Learn step‑by‑step handling of font substitution warnings.
  headline: how to set callback in Aspose.Words Java – Detect and Handle Missing Fonts
  type: TechArticle
- description: how to set callback in Aspose.Words Java to detect missing fonts and
    customize document loading. Learn step‑by‑step handling of font substitution warnings.
  name: how to set callback in Aspose.Words Java – Detect and Handle Missing Fonts
  steps:
  - name: What if I want the program to stop loading when a font is missing?
    text: 'Throw an exception inside the `warning` method:'
  - name: Does this work for PDFs generated from DOCX?
    text: Absolutely. The callback fires during the **loading** phase, which is identical
      for all output formats (`save` to PDF, DOCX, HTML, etc.). As long as you load
      the source document with the same `LoadOptions`, you’ll catch missing fonts
      before they affect the final PDF.
  - name: Can I capture other warning types (e.g., image conversion)?
    text: Yes—`WarningInfo.getWarningType()` can be compared against other enums like
      `WarningType.IMAGE_CONVERSION`. Just add more `if` branches in the callback.
  - name: Is there a performance impact?
    text: Negligible. The callback runs synchronously during loading, and the extra
      checks are lightweight. If you’re loading thousands of documents, you might
      want to disable warnings in production by setting `loadOptions.setWarningCallback(null);`.
  - name: What’s Next?
    text: '- Explore **font substitution tables** for bulk mapping of many missing
      fonts. - Combine this callback with **document validation** to enforce style
      guides. - Try **custom warning callbacks** that write to a log file or a monitoring
      system instead of `System.out`.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Document Processing
title: Comment définir un rappel dans Aspose.Words Java – Détecter et gérer les polices
  manquantes
url: /fr/java/document-loading-and-saving/how-to-set-callback-in-aspose-words-java-detect-and-handle-m/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# comment définir un rappel dans Aspose.Words Java – Détecter et gérer les polices manquantes

Vous vous êtes déjà demandé **comment définir un rappel** dans Aspose.Words Java afin de repérer les polices manquantes avant qu'elles ne ruinent votre PDF ou DOCX ? Vous n'êtes pas le seul. Les avertissements de police manquante peuvent corrompre silencieusement la mise en page, et sans un rappel d'avertissement approprié vous pourriez ne jamais le remarquer jusqu'à ce que le document final soit déformé.  

Dans ce tutoriel, nous parcourrons un exemple complet, prêt à l'exécution, qui **détecte les polices manquantes**, **gère les polices manquantes** avec élégance, et vous montre comment **personnaliser le chargement du document** avec un rappel d'avertissement. À la fin, vous disposerez d'une classe Java autonome que vous pourrez intégrer à n'importe quel projet—sans recherche supplémentaire dans la documentation.

## Ce dont vous aurez besoin

- Java 8 ou supérieur (le code fonctionne également avec Java 11+)
- Bibliothèque Aspose.Words for Java (version 23.9 ou ultérieure)
- Un fichier DOCX qui référence une police que vous n’avez pas installée (par ex., une police d’entreprise personnalisée)

Si vous n’avez pas encore ajouté Aspose.Words à votre projet Maven, il suffit d’inclure :

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

C’est tout—pas de plugins supplémentaires, pas de dépendances natives.

---

## Étape 1 : Comprendre le mécanisme WarningCallback

Le **warning callback** est la façon dont Aspose.Words vous alerte lorsqu'un événement inattendu se produit lors du chargement ou de l'enregistrement d'un document. En implémentant `IWarningCallback`, vous obtenez le contrôle total sur ce qui est journalisé, ignoré ou même transformé en exception.

> **Pourquoi c’est important :**  
> Lorsqu’une police est manquante, Aspose substitue une police de secours. Le résultat visuel peut être radicalement différent, surtout pour les PDF fortement marqués. En interceptant `WarningType.FONT_SUBSTITUTION`, vous pouvez consigner le nom exact de la police, décider d’abandonner le processus, ou remplacer la police par votre propre police personnalisée de façon programmatique.

---

## Étape 2 : Créer une instance de LoadOptions

`LoadOptions` est le point d’entrée pour personnaliser le chargement du document. Vous attacherez le rappel à cet objet avant de charger réellement le fichier.

```java
// Step 2: Prepare LoadOptions
LoadOptions loadOptions = new LoadOptions();
```

À ce stade, `loadOptions` n’est qu’un simple conteneur—rien ne se passe encore. La vraie magie commence lorsque nous branchons le rappel.

---

## Étape 3 : Implémenter et attacher le rappel

Voici une classe anonyme compacte qui implémente `IWarningCallback`. Elle imprime une ligne conviviale dans la console chaque fois qu’une substitution de police se produit.

```java
// Step 3: Attach a warning callback to capture font substitution warnings
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Detect missing fonts
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("[Missing Font] " + info.getDescription());
            // Optional: you could throw an exception here to abort loading
            // throw new RuntimeException("Font missing: " + info.getDescription());
        }
    }
});
```

> **Astuce :** Si vous souhaitez **gérer les polices manquantes** en fournissant un remplacement, vous pouvez également définir `FontSettings` sur le `LoadOptions` et mapper les polices manquantes à une police de secours connue.

---

## Étape 4 : Charger le document avec vos options personnalisées

Maintenant que le rappel est en place, chargez le document. Si le fichier référence une police que vous n’avez pas, vous verrez l’avertissement affiché.

```java
// Step 4: Load the document using the configured LoadOptions
String docPath = "YOUR_DIRECTORY/doc-with-missing-font.docx";
Document document = new Document(docPath, loadOptions);
```

Lorsque vous exécutez le programme, la console peut afficher :

```
[Missing Font] Font substitution: The font "MyCustomFont" was not found. Substituted with "Arial".
```

Cette ligne prouve que vous avez **détecté les polices manquantes** avec succès et que vous êtes maintenant en mesure de **gérer les polices manquantes** comme vous le souhaitez.

---

## Étape 5 : Optionnel – Remplacer les polices manquantes par une police connue

Si vous préférez remplacer automatiquement toute police manquante par, par exemple, `Times New Roman`, vous pouvez ajouter un objet `FontSettings` :

```java
// Optional Step 5: Map missing fonts to a fallback
FontSettings fontSettings = new FontSettings();
fontSettings.setMissingFontNotification(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // This will be called for each missing font
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("[Auto‑Replace] " + info.getDescription());
        }
    }
});
// Force substitution to Times New Roman
fontSettings.getSubstitutionSettings().getTableSubstitution().addSubstitutes("MyCustomFont", new String[]{"Times New Roman"});
loadOptions.setFontSettings(fontSettings);
```

Le document se charge maintenant, et toute référence à `MyCustomFont` est silencieusement remplacée par `Times New Roman`. La console vous indiquera toujours ce qui a été remplacé, vous tenant informé.

---

## Exemple complet fonctionnel

Voici une classe Java unique qui intègre toutes les étapes ci‑dessus. Copiez‑collez‑la dans votre IDE, ajustez `docPath`, puis exécutez.

```java
import com.aspose.words.*;

public class DetectMissingFontsDemo {
    public static void main(String[] args) {
        try {
            // 1️⃣ Create LoadOptions
            LoadOptions loadOptions = new LoadOptions();

            // 2️⃣ Attach warning callback (detect missing fonts)
            loadOptions.setWarningCallback(new IWarningCallback() {
                @Override
                public void warning(WarningInfo info) {
                    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                        System.out.println("[Missing Font] " + info.getDescription());
                    }
                }
            });

            // 3️⃣ (Optional) Set up automatic font substitution
            FontSettings fontSettings = new FontSettings();
            fontSettings.getSubstitutionSettings()
                        .getTableSubstitution()
                        .addSubstitutes("MyCustomFont", new String[]{"Times New Roman"});
            loadOptions.setFontSettings(fontSettings);

            // 4️⃣ Load the document with custom loading behavior
            String docPath = "YOUR_DIRECTORY/doc-with-missing-font.docx";
            Document doc = new Document(docPath, loadOptions);

            // 5️⃣ Save to PDF to see the final result (optional)
            doc.save("output.pdf");
            System.out.println("Document loaded and saved successfully.");

        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Sortie attendue**

```
[Missing Font] Font substitution: The font "MyCustomFont" was not found. Substituted with "Times New Roman".
Document loaded and saved successfully.
```

Vous disposez désormais d’une méthode reproductible pour **détecter les polices manquantes**, **gérer les polices manquantes**, et **personnaliser le chargement du document**—tout cela en apprenant à **définir correctement un rappel**.

---

## Questions fréquentes

### Que faire si je veux que le programme arrête le chargement lorsqu’une police est manquante ?

Lancez une exception à l’intérieur de la méthode `warning` :

```java
throw new RuntimeException("Critical: Missing font - " + info.getDescription());
```

Le bloc `catch` en bas le capturera, et vous pourrez décider comment le consigner ou alerter l'utilisateur.

### Cette solution fonctionne‑t‑elle pour les PDF générés à partir de DOCX ?

Absolument. Le rappel s’active pendant la phase de **chargement**, qui est identique pour tous les formats de sortie (`save` en PDF, DOCX, HTML, etc.). Tant que vous chargez le document source avec les mêmes `LoadOptions`, vous intercepterez les polices manquantes avant qu’elles n’affectent le PDF final.

### Puis‑je capturer d’autres types d’avertissement (par ex., conversion d’image) ?

Oui—`WarningInfo.getWarningType()` peut être comparé à d’autres énumérations comme `WarningType.IMAGE_CONVERSION`. Il suffit d’ajouter d’autres branches `if` dans le rappel.

### Y a‑t‑il un impact sur les performances ?

Négligeable. Le rappel s’exécute de façon synchrone pendant le chargement, et les vérifications supplémentaires sont légères. Si vous chargez des milliers de documents, vous pourriez désactiver les avertissements en production en définissant `loadOptions.setWarningCallback(null);`.

---

## Aperçu visuel

![exemple de définition de rappel dans Aspose.Words Java](https://example.com/images/callback-diagram.png "définir un rappel")

*Le diagramme illustre le flux : `LoadOptions` → `IWarningCallback` → Chargement du document → Gestion de la substitution de police.*

---

## Conclusion

Nous avons couvert **comment définir un rappel** dans Aspose.Words Java, démontré **la détection des polices manquantes**, présenté des méthodes pratiques pour **gérer les polices manquantes**, et expliqué comment **personnaliser le chargement du document** avec `LoadOptions`.  

Armé de ces connaissances, vous pouvez désormais protéger vos pipelines de documents contre les substitutions de police silencieuses, préserver l’intégrité de votre identité visuelle, et offrir à vos utilisateurs un retour clair lorsqu’un problème survient.

### Et après ?

- Explorez les **tables de substitution de police** pour cartographier en masse de nombreuses polices manquantes.  
- Combinez ce rappel avec la **validation de documents** afin d’appliquer les guides de style.  
- Essayez des **rappels d’avertissement personnalisés** qui écrivent dans un fichier de log ou un système de surveillance au lieu de `System.out`.  

N’hésitez pas à expérimenter, et dites‑nous comment vous avez personnalisé le rappel pour vos propres projets. Bon codage !

---


## Que devriez‑vous apprendre ensuite ?


Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications pas à pas pour vous aider à maîtriser des fonctionnalités supplémentaires de l’API et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [Comment définir LoadOptions dans Aspose.Words pour Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Comment détecter les polices dans Aspose.Words – Gérer les avertissements et les paramètres](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Comment capturer les polices dans Aspose.Words – Guide complet](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}