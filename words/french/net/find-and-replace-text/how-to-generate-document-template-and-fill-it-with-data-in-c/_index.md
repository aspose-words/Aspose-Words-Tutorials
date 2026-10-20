---
category: general
date: 2026-09-21
description: Apprenez à générer un modèle de document, à remplir un modèle Word et
  à remplacer les espaces réservés dans un fichier DOCX en utilisant C# – guide étape
  par étape.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- generate document template
- populate word template
- how to replace placeholder
- fill docx template
- replace text docx
language: fr
lastmod: 2026-09-21
og_description: Générez un modèle de document en C# en remplissant un modèle Word,
  en remplaçant les espaces réservés, puis en enregistrant le fichier DOCX rempli.
  Suivez ce guide complet.
og_image_alt: Screenshot of a C# program generating and filling a DOCX template
og_title: Générer un modèle de document en C# – remplir les fichiers DOCX avec des
  données
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to generate document template, populate word template and
    replace placeholders in a DOCX file using C# – step‑by‑step guide.
  headline: How to generate document template and fill it with data in C#
  type: TechArticle
tags:
- C#
- DOCX
- template processing
title: Comment générer un modèle de document et le remplir avec des données en C#
url: /fr/net/find-and-replace-text/how-to-generate-document-template-and-fill-it-with-data-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment générer un modèle de document et le remplir avec des données en C#

Si vous avez besoin de **générer des modèles de document** réutilisables pour des factures, des contrats ou des rapports, ce guide vous montre exactement comment faire. Vous apprendrez à **remplir le modèle Word** les espaces réservés, à les remplacer par de vraies valeurs, et enfin à **remplir le modèle docx** de façon programmatique.

Créer un modèle réutilisable élimine le copier‑coller manuel et garantit la cohérence de tous les documents générés. Les étapes ci‑dessous fonctionnent avec n'importe quel fichier `.docx` contenant des jetons d'espace réservé simples tels que `{{Name}}`.

## Prérequis

* SDK .NET 6.0 ou version ultérieure installé  
* Visual Studio 2022 (ou tout IDE de votre choix)  
* Le package NuGet **Aspose.Words for .NET** – il fournit la classe `Document` utilisée dans l'exemple  

Vous pouvez ajouter le package avec la commande suivante :

```bash
dotnet add package Aspose.Words
```

## Étape 1 : Préparer le modèle Word

Créez un document Word (`Template.docx`) contenant des espaces réservés où les données dynamiques doivent apparaître. Une convention courante est d'utiliser des accolades doubles :

```
Dear {{Name}},

Your order #{{OrderId}} has been shipped on {{ShipDate}}.
```

Enregistrez le fichier dans un dossier que vous pouvez référencer depuis le code, par exemple `C:\Docs\Template.docx`.

## Étape 2 : Charger le document modèle

La première action programmatique consiste à charger le modèle en mémoire. Le constructeur `Document` lit le fichier et construit un modèle d'objet que vous pouvez manipuler.

```csharp
using System;
using Aspose.Words;

class Program
{
    static void Main()
    {
        // Load the template document from disk
        string templatePath = @"C:\Docs\Template.docx";
        Document doc = new Document(templatePath);
```

**Pourquoi c'est important :** Charger le fichier crée une copie propre à chaque fois, de sorte que le modèle original reste intact pour les exécutions futures.

## Étape 3 : Remplacer les espaces réservés par des données réelles

Aspose.Words fournit une méthode simple `Range.Replace` qui parcourt le document à la recherche d'une chaîne spécifique et la remplace. Enveloppez l'appel dans une méthode d'assistance pour garder le flux principal ordonné.

```csharp
        // Helper to replace a single placeholder
        void ReplacePlaceholder(string placeholder, string value)
        {
            // The placeholder includes the curly braces exactly as they appear in the template
            doc.Range.Replace(placeholder, value, new FindReplaceOptions());
        }

        // Populate the template with real values
        ReplacePlaceholder("{{Name}}", "John Doe");
        ReplacePlaceholder("{{OrderId}}", "A12345");
        ReplacePlaceholder("{{ShipDate}}", DateTime.Today.ToString("MMMM d, yyyy"));
```

**Comment ça fonctionne :** `Range.Replace` parcourt chaque paragraphe, cellule de tableau, en‑tête et pied de page, garantissant que toutes les occurrences du jeton sont mises à jour. C'est la méthode la plus fiable pour **remplacer les espaces réservés** dans un fichier DOCX.

### Gestion des occurrences multiples et des jetons manquants

* Si un espace réservé apparaît plusieurs fois, `Replace` met automatiquement à jour toutes les instances.  
* Si un espace réservé est absent, la méthode ne fait simplement rien — aucune exception n'est levée.  
* Pour les documents volumineux, vous pouvez améliorer les performances en désactivant `doc.UpdateFields()` jusqu'à ce que toutes les remplacements soient terminés.

## Étape 4 : Enregistrer le document rempli

Une fois tous les espaces réservés remplacés, écrivez le résultat dans un nouveau fichier. Conserver la sortie séparée préserve le modèle original pour les exécutions futures.

```csharp
        // Save the filled document to a new file
        string outputPath = @"C:\Docs\FilledTemplate.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Résultat :** `FilledTemplate.docx` contient désormais le contenu personnalisé :

```
Dear John Doe,

Your order #A12345 has been shipped on September 21, 2026.
```

## Étape 5 : Vérifier la sortie (optionnel)

Si vous souhaitez confirmer de manière programmatique que les remplacements ont réussi, vous pouvez relire le fichier enregistré et rechercher les valeurs attendues :

```csharp
        Document verifyDoc = new Document(outputPath);
        bool nameReplaced = verifyDoc.Range.Text.Contains("John Doe");
        Console.WriteLine($"Name replacement successful: {nameReplaced}");
```

L'exécution de l'étape de vérification affiche `true` lorsque l'espace réservé a été correctement remplacé.

## Pièges courants et conseils de bonnes pratiques

| Problème | Pourquoi cela se produit | Solution recommandée |
|----------|--------------------------|----------------------|
| **Les espaces réservés contiennent des espaces supplémentaires** | `"{{ Name }}"` ne correspond pas à `"{{Name}}"`. | Conservez les jetons d'espace réservé sans espaces, ou supprimez les espaces des deux côtés avant le remplacement. |
| **Word ajoute un formatage caché** | Word peut stocker l'espace réservé découpé en plusieurs runs, ce qui fait que `Replace` le manque. | Utilisez `Document.Range.Replace` avec `FindReplaceOptions` configuré avec `MatchCase = false` et `FindWholeWordsOnly = false`. |
| **Les documents volumineux ralentissent** | Remplacer les jetons un par un déclenche une analyse complète du document à chaque fois. | Regroupez les remplacements en un seul passage en appelant `Range.Replace` pour chaque jeton avant d'enregistrer. |
| **Enregistrement dans un dossier en lecture‑seule** | `doc.Save` lève une `UnauthorizedAccessException`. | Assurez‑vous que le répertoire cible possède les permissions d'écriture, ou choisissez un chemin accessible à l'utilisateur (par ex., `%TEMP%`). |

## Exemple complet fonctionnel

Voici le programme complet et autonome que vous pouvez copier, coller et exécuter.

```csharp
using System;
using Aspose.Words;

class Program
{
    static void Main()
    {
        // Paths – adjust to your environment
        string templatePath = @"C:\Docs\Template.docx";
        string outputPath   = @"C:\Docs\FilledTemplate.docx";

        // 1️⃣ Load the template document
        Document doc = new Document(templatePath);

        // 2️⃣ Replace placeholders
        void Replace(string placeholder, string value) =>
            doc.Range.Replace(placeholder, value, new FindReplaceOptions());

        Replace("{{Name}}", "John Doe");
        Replace("{{OrderId}}", "A12345");
        Replace("{{ShipDate}}", DateTime.Today.ToString("MMMM d, yyyy"));

        // 3️⃣ Save the filled document
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");

        // 4️⃣ (Optional) Verify replacement
        Document verify = new Document(outputPath);
        Console.WriteLine($"Verification – name found: {verify.Range.Text.Contains("John Doe")}");
    }
}
```

**Sortie console attendue**

```
Document saved to C:\Docs\FilledTemplate.docx
Verification – name found: True
```

Ouvrez `FilledTemplate.docx` dans Microsoft Word pour voir le texte personnalisé.

## Conclusion

Vous savez maintenant comment **générer des modèles de document**, **remplir le modèle Word**, et **remplir le modèle docx** en **remplaçant les espaces réservés** par de vraies données. Cette approche fonctionne pour n'importe quel nombre d'espaces réservés et s'adapte aux documents volumineux lorsque vous suivez les conseils de bonnes pratiques.

### Et après ?

* **Tables dynamiques :** Utilisez `DocumentBuilder` pour insérer des lignes à partir de collections.  
* **Sections conditionnelles :** Masquez ou affichez des parties du modèle avec des champs `IF`.  
* **Export PDF :** Appelez `doc.Save("output.pdf")` pour créer une version PDF du document rempli.  

Expérimentez ces variantes pour créer un moteur de génération de documents complet pour les factures, les contrats ou tout rapport récurrent.

---

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s'appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d'implémentation alternatives dans vos propres projets.

- [Document Word - Rechercher et remplacer du texte](/words/english/net/find-and-replace-text/)
- [Générer un document Word](/words/english/java/word-processing/generate-word-document/)
- [Récupérer un DOCX corrompu – Ouvrir & charger un document Word](/words/english/python-net/document-operations/recover-corrupted-docx-open-load-word-document/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}