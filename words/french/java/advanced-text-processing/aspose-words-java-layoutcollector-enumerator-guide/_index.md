---
date: '2025-11-12'
description: Apprenez à utiliser le LayoutCollector et le LayoutEnumerator d’Aspose.Words
  for Java pour analyser la pagination, parcourir la mise en page du document, implémenter
  des rappels de mise en page et redémarrer la numérotation des pages dans les sections
  continues.
keywords:
- Aspose.Words Java LayoutCollector
- Java document layout management
- LayoutEnumerator traversal
- analyze pagination java
- use layoutcollector page span
- traverse document layout
- restart page numbering sections
- implement layout callback
language: fr
title: Analyse de la pagination Java avec les outils de mise en page Aspose.Words
url: /java/advanced-text-processing/aspose-words-java-layoutcollector-enumerator-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Analyse de la pagination Java avec les outils de mise en page Aspose.Words

## Introduction  

Si vous devez **analyser la pagination** ou **parcourir la mise en page d’un document** dans une application Java, Aspose.Words for Java vous propose deux API puissantes : **`LayoutCollector`** et **`LayoutEnumerator`**. Ces classes vous permettent de découvrir combien de pages occupe un nœud, de parcourir chaque entité de mise en page, de réagir aux événements de mise en page, et même de redémarrer la numérotation des pages dans les sections continues. Dans ce guide, nous passerons en revue chaque fonctionnalité pas à pas, présenterons des extraits de code concrets et expliquerons les résultats attendus afin que vous puissiez les appliquer immédiatement.

Vous apprendrez à :

* **utiliser LayoutCollector** pour obtenir la page de début et de fin de n’importe quel nœud (use layoutcollector page span)  
* **parcourir la mise en page du document** avec LayoutEnumerator (traverse document layout)  
* **implémenter des callbacks de mise en page** pour réagir aux événements de pagination (implement layout callback)  
* **redémarrer la numérotation des pages** dans les sections continues (restart page numbering sections)  

Commençons.

## Prérequis  

### Bibliothèques requises  

| Outil de construction | Dépendance |
|------------|------------|
| **Maven** | ```xml<br><dependency><groupId>com.aspose</groupId><artifactId>aspose-words</artifactId><version>25.3</version></dependency>``` |
| **Gradle** | ```gradle<br>implementation 'com.aspose:aspose-words:25.3'``` |

> **Remarque :** Le numéro de version est conservé pour la compatibilité ; le code fonctionne avec n’importe quelle version récente d’Aspose.Words for Java.

### Environnement  

* JDK 8 ou supérieur  
* Un IDE tel qu’IntelliJ IDEA ou Eclipse  

### Connaissances  

Une connaissance de base de la programmation Java et une familiarité avec Maven/Gradle suffisent pour suivre les exemples.

## Installation d’Aspose.Words  

Avant de pouvoir appeler une API de mise en page, la bibliothèque doit être licenciée (ou utilisée en mode d’évaluation). L’extrait ci‑dessous montre l’initialisation minimale :

```java
import com.aspose.words.*;

public class SetupAsposeWords {
    public static void main(String[] args) throws Exception {
        // Load your license file – skip this line for a trial evaluation
        License license = new License();
        license.setLicense("path/to/your/license.lic");

        System.out.println("Aspose.Words is ready to use!");
    }
}
```

*Le code ne modifie aucun document ; il prépare simplement l’environnement Aspose.*  

Nous pouvons maintenant plonger dans les fonctionnalités principales.

## Fonctionnalité 1 : Utilisation de **LayoutCollector** pour analyser la pagination  

`LayoutCollector` associe chaque nœud d’un `Document` aux pages qu’il occupe. C’est la méthode la plus fiable pour **use layoutcollector page span** lors de l’analyse de la pagination.

### Implémentation pas à pas  

1. **Créer un nouveau document et y attacher un LayoutCollector.**  
2. **Insérer du contenu qui force la pagination** (par ex., des sauts de page, des sauts de section).  
3. **Actualiser la mise en page** avec `updatePageLayout()`.  
4. **Interroger le collecteur** pour obtenir la page de début, la page de fin et le nombre total de pages couvertes.

#### 1️⃣ Initialiser le Document et le LayoutCollector  

```java
Document doc = new Document();                 // Empty document
LayoutCollector layoutCollector = new LayoutCollector(doc);
```

#### 2️⃣ Remplir le Document  

```java
DocumentBuilder builder = new DocumentBuilder(doc);
builder.write("Section 1");
builder.insertBreak(BreakType.PAGE_BREAK);
builder.insertBreak(BreakType.SECTION_BREAK_EVEN_PAGE);
builder.write("Section 2");
builder.insertBreak(BreakType.PAGE_BREAK);
```

#### 3️⃣ Mettre à jour la mise en page et récupérer les métriques  

```java
layoutCollector.clear();          // Reset any previous mappings
doc.updatePageLayout();           // Force pagination calculation

int pagesSpanned = layoutCollector.getNumPagesSpanned(doc);
assert pagesSpanned == 5;         // Expected: the document occupies 5 pages
System.out.println("Document spans " + pagesSpanned + " pages.");
```

**Sortie attendue**

```
Document spans 5 pages.
```

> **Pourquoi cela fonctionne :** `updatePageLayout()` force Aspose.Words à recomputer la mise en page, après quoi `LayoutCollector` peut rapporter avec précision les intervalles de pages.

## Fonctionnalité 2 : Parcourir la mise en page du document avec **LayoutEnumerator**  

Lorsque vous devez **traverse document layout** (par ex., pour un rendu personnalisé ou une analyse), `LayoutEnumerator` fournit une vue arborescente des pages, paragraphes, lignes et mots.

### Implémentation pas à pas  

1. Charger un document existant contenant des entités de mise en page.  
2. Créer une instance de `LayoutEnumerator`.  
3. Se positionner sur l’entité racine `PAGE`.  
4. Parcourir la mise en page en avant et en arrière à l’aide de méthodes auxiliaires récursives.

#### 1️⃣ Charger le Document et créer l’énumérateur  

```java
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Layout entities.docx");
LayoutEnumerator layoutEnumerator = new LayoutEnumerator(doc);
```

#### 2️⃣ Positionner au niveau de la Page  

```java
layoutEnumerator.moveParent(LayoutEntityType.PAGE);
```

#### 3️⃣ Parcours avant (profondeur d’abord)  

```java
traverseLayoutForward(layoutEnumerator, 1);
```

#### 4️⃣ Parcours arrière  

```java
traverseLayoutBackward(layoutEnumerator, 1);
```

> **Méthodes auxiliaires** (`traverseLayoutForward` / `traverseLayoutBackward`) sont implémentées de façon récursive pour visiter chaque entité enfant et afficher son type ainsi que son indice de page. Vous pouvez les adapter pour collecter des statistiques, rendre des graphiques ou modifier des propriétés de mise en page.

## Fonctionnalité 3 : Implémentation des **Layout Callbacks**  

Parfois, vous devez réagir lorsque Aspose.Words a fini de mettre en page une partie du document. Implémenter `IPageLayoutCallback` vous permet de **implement layout callback** une logique telle que l’enregistrement de chaque page sous forme d’image.

### Implémentation pas à pas  

1. Assigner une instance de callback aux `LayoutOptions` du document.  
2. Dans le callback, gérer les événements `PART_REFLOW_FINISHED` et `CONVERSION_FINISHED`.  
3. Rendre la page courante en PNG à l’aide de `ImageSaveOptions`.

#### 1️⃣ Enregistrer le Callback  

```java
doc.getLayoutOptions().setCallback(new RenderPageLayoutCallback());
doc.updatePageLayout();                     // Triggers the callback events
```

#### 2️⃣ Classe de Callback  

```java
private static class RenderPageLayoutCallback implements IPageLayoutCallback {
    public void notify(PageLayoutCallbackArgs a) throws Exception {
        if (a.getEvent() == PageLayoutEvent.PART_REFLOW_FINISHED) {
            notifyPartFinished(a);
        } else if (a.getEvent() == PageLayoutEvent.CONVERSION_FINISHED) {
            notifyConversionFinished(a);
        }
    }

    private void renderPage(PageLayoutCallbackArgs a, int pageIndex) throws Exception {
        ImageSaveOptions saveOptions = new ImageSaveOptions(SaveFormat.PNG);
        saveOptions.setPageSet(new PageSet(pageIndex));

        try (FileOutputStream stream = new FileOutputStream(
                "YOUR_ARTIFACTS_DIR/PageLayoutCallback.page-" + (pageIndex + 1) + ".png")) {
            a.getDocument().save(stream, saveOptions);
        }
    }

    // You can add custom logic here for partFinished / conversionFinished
}
```

**Ce qui se passe :** Chaque fois qu’une partie de mise en page termine son reflow, le callback rend cette page en fichier PNG, vous offrant ainsi une trace visuelle du processus de pagination.

## Fonctionnalité 4 : Redémarrage de la numérotation des pages dans les **sections continues**  

Lorsqu’un document contient des sections continues, il peut être souhaitable que la numérotation des pages redémarre uniquement sur une nouvelle page physique. Cela s’obtient grâce au paramètre `ContinuousSectionRestart`.

### Implémentation pas à pas  

1. Charger le document cible.  
2. Modifier l’option `ContinuousSectionPageNumberingRestart`.  
3. Réexécuter `updatePageLayout()` pour appliquer la modification.

#### 1️⃣ Charger le Document  

```java
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Continuous section page numbering.docx");
```

#### 2️⃣ Configurer le comportement de redémarrage  

```java
doc.getLayoutOptions()
   .setContinuousSectionPageNumberingRestart(ContinuousSectionRestart.FROM_NEW_PAGE_ONLY);
doc.updatePageLayout();            // Apply the new numbering rule
```

**Résultat :** Les numéros de page redémarreront désormais uniquement lorsqu’une nouvelle page physique commence, offrant un rendu propre et professionnel pour les rapports ou les livres.

## Applications pratiques  

| Scénario | API utilisée | Avantage |
|----------|--------------|----------|
| **Audit de longs contrats** | `LayoutCollector` | Identifier rapidement les clauses qui s’étendent sur plusieurs pages. |
| **Rendu PDF personnalisé** | `LayoutEnumerator` | Parcourir l’arbre de mise en page pour exporter chaque ligne sous forme de graphiques vectoriels. |
| **Aperçu en temps réel du document** | Layout callbacks | Générer des images de pages à la volée pendant que l’utilisateur modifie le contenu. |
| **Rapports multi‑sections** | Redémarrage de la numérotation des sections continues | Conserver une numérotation logique sans ajustements manuels. |

## Conseils de performance  

* **Élaguer les nœuds inutilisés** avant d’appeler `updatePageLayout()` — moins d’éléments, pagination plus rapide.  
* **Réutiliser un seul LayoutCollector** pour plusieurs requêtes plutôt que d’en créer un à chaque fois.  
* **Limiter la profondeur de parcours** avec LayoutEnumerator si vous ne avez besoin que des données au niveau page.  
* **Libérer les flux** (comme montré dans l’exemple de callback) pour éviter les fuites de mémoire sur de gros documents.

## Conclusion  

En maîtrisant `LayoutCollector`, `LayoutEnumerator`, les callbacks de mise en page et la numérotation des sections continues, vous disposez désormais d’une boîte à outils complète pour **analyze pagination java**, **traverse document layout** et **restart page numbering sections**. Ces API vous permettent de créer des pipelines de traitement de texte robustes et performants, délivrant des résultats professionnels à chaque exécution.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}