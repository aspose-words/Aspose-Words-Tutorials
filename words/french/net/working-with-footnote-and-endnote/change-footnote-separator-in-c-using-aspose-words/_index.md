---
category: general
date: 2026-08-04
description: Modifier le séparateur de note de bas de page en C# avec Aspose.Words
  – apprenez comment éditer le séparateur de note de bas de page et changer le séparateur
  de note de fin dans les documents Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- change footnote separator
- edit footnote separator
- how to change footnote separator
- change endnote separator
language: fr
lastmod: 2026-08-04
og_description: Modifiez le séparateur de note de bas de page en C# avec Aspose.Words.
  Ce guide vous montre comment modifier le séparateur de note de bas de page, personnaliser
  le séparateur de note de fin et enregistrer le document mis à jour.
og_image_alt: Screenshot showing the changed footnote separator in a Word document
og_title: Modifier le séparateur de notes de bas de page en C# – guide complet d’Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Change footnote separator in C# using Aspose.Words – learn how to edit
    footnote separator and change endnote separator in Word documents.
  headline: Change footnote separator in C# using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Footnotes
- Document processing
title: Modifier le séparateur de note de bas de page en C# avec Aspose.Words
url: /fr/net/working-with-footnote-and-endnote/change-footnote-separator-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Modifier le séparateur de note de bas de page en C# avec Aspose.Words

Si vous devez **modifier le séparateur de note de bas de page** dans un document Word, ce tutoriel vous guide pas à pas avec Aspose.Words pour .NET. Que vous souhaitiez remplacer la ligne par défaut par un symbole, ou appliquer un style différent aux séparateurs de notes de fin, le code ci‑dessous couvre l’ensemble du flux de travail.

Vous apprendrez également à **modifier le séparateur de note de bas de page** et l’opération associée **modifier le séparateur de note de fin**, afin que le même document puisse avoir un style cohérent pour les notes de bas de page et les notes de fin. Aucun outil externe n’est requis — juste quelques lignes de C#.

## Ce que vous allez réaliser

À la fin de ce guide, vous serez capable de :

* Charger un fichier *.docx* existant contenant des notes de bas de page et des notes de fin.  
* Accéder aux nœuds séparateurs pour les notes de bas de page, les continuations de notes de bas de page et les notes de fin.  
* Remplacer le caractère séparateur (par exemple, changer la ligne par défaut en astérisque).  
* Enregistrer le document modifié sans perdre aucun autre contenu.  

Le tutoriel suppose que vous avez une compréhension de base du C# et que vous avez installé le package NuGet **Aspose.Words** (version 24.9 ou ultérieure).  

---

## Prérequis

| Exigence | Raison |
|----------|--------|
| .NET 6.0+ ou .NET Framework 4.7.2+ | Runtime requis pour Aspose.Words |
| Bibliothèque Aspose.Words for .NET | Fournit les API `Document` et `FootnoteOptions` |
| Un fichier Word d’entrée (`input.docx`) contenant au moins une note de bas de page ou une note de fin | Illustre le changement de séparateur |

Vous pouvez ajouter Aspose.Words à votre projet avec la commande CLI suivante :

```bash
dotnet add package Aspose.Words --version 24.9.0
```

---

## Étape 1 : Charger le document contenant des notes de bas de page

La première opération consiste à lire le fichier source dans un objet `Document`. Cet objet représente l’ensemble du fichier Word en mémoire et vous donne accès à tous ses nœuds.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

// Load the .docx file that contains footnotes and endnotes.
Document document = new Document(@"C:\Docs\input.docx");
```

**Pourquoi c’est important :** Le chargement du document est le point d’entrée pour toute manipulation. Si le fichier est introuvable, Aspose.Words lève une `FileNotFoundException`, assurez‑vous donc que le chemin est correct avant de continuer.

---

## Étape 2 : Accéder aux nœuds séparateurs de notes de bas de page et de notes de fin

`Document.FootnoteOptions` expose trois nœuds séparateurs :

* `Separator` – la ligne qui apparaît après la collection de notes de bas de page sur la première page.  
* `ContinuationSeparator` – la ligne utilisée lorsque les notes de bas de page se poursuivent sur la page suivante.  
* `EndnoteSeparator` – la ligne qui sépare le texte principal de la liste des notes de fin.

Vous récupérez ces nœuds sous forme d’objets génériques `Node`, puis vous les convertissez en `Run` pour modifier le texte.

```csharp
// Retrieve the three separator nodes.
Node footnoteSeparator = document.FootnoteOptions.Separator;
Node footnoteContinuation = document.FootnoteOptions.ContinuationSeparator;
Node endnoteSeparator = document.FootnoteOptions.EndnoteSeparator;
```

**Pourquoi c’est important :** Ces nœuds sont les seuls emplacements où le caractère visuel du séparateur est stocké. Modifier tout autre nœud (par ex., un paragraphe ordinaire) n’affectera pas le format des notes de bas de page.

---

## Étape 3 : Modifier le caractère du séparateur de note de bas de page

Le besoin le plus fréquent est de remplacer la ligne par défaut par un symbole tel qu’un astérisque (`*`). Comme le séparateur est stocké sous forme de `Run`, vous pouvez modifier en toute sécurité sa propriété `Text`.

```csharp
// Change the primary footnote separator to an asterisk.
if (footnoteSeparator is Run footnoteRun)
{
    footnoteRun.Text = "*";
}

// Optionally, change the continuation separator as well.
if (footnoteContinuation is Run continuationRun)
{
    continuationRun.Text = "*";
}
```

**Pourquoi c’est important :** Modifier directement `Run.Text` met à jour la représentation visuelle dans le document final sans toucher au reste du contenu des notes de bas de page. Le même schéma peut être utilisé pour appliquer n’importe quelle chaîne, y compris des symboles Unicode.

---

## Étape 4 : Modifier le séparateur de note de fin (facultatif)

Si vous devez également **modifier le séparateur de note de fin**, le processus reflète celui de la note de bas de page. Remplacez le texte de `endnoteSeparator` par le caractère souhaité.

```csharp
// Change the endnote separator to a dash.
if (endnoteSeparator is Run endnoteRun)
{
    endnoteRun.Text = "-";
}
```

**Pourquoi c’est important :** Les notes de fin sont souvent stylisées différemment des notes de bas de page. Fournir un séparateur distinct vous permet de conserver la cohérence visuelle avec les directives de conception de votre document.

---

## Étape 5 : Enregistrer le document modifié

Après toutes les modifications, persistez les changements avec `Document.Save`. Vous pouvez écraser le fichier original ou écrire vers un nouvel emplacement.

```csharp
// Save the updated document.
document.Save(@"C:\Docs\ModifiedSeparators.docx");
```

**Pourquoi c’est important :** `Save` écrit la représentation en mémoire sur le disque, en préservant tous les autres éléments (styles, images, tableaux) intacts.

---

## Exemple complet et exécutable

En rassemblant tous les éléments, voici une application console autonome qui démontre l’ensemble du flux de travail :

```csharp
using System;
using Aspose.Words;

namespace FootnoteSeparatorDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source document.
            string inputPath = @"C:\Docs\input.docx";
            Document doc = new Document(inputPath);

            // 2️⃣ Access separator nodes.
            Node footnoteSep = doc.FootnoteOptions.Separator;
            Node footnoteCont = doc.FootnoteOptions.ContinuationSeparator;
            Node endnoteSep = doc.FootnoteOptions.EndnoteSeparator;

            // 3️⃣ Change footnote separator to an asterisk.
            if (footnoteSep is Run footnoteRun)
                footnoteRun.Text = "*";

            // Optional: also change the continuation separator.
            if (footnoteCont is Run contRun)
                contRun.Text = "*";

            // 4️⃣ Change endnote separator to a dash.
            if (endnoteSep is Run endnoteRun)
                endnoteRun.Text = "-";

            // 5️⃣ Save the result.
            string outputPath = @"C:\Docs\ModifiedSeparators.docx";
            doc.Save(outputPath);

            Console.WriteLine("Document saved to " + outputPath);
        }
    }
}
```

**Résultat attendu :** Ouvrez *ModifiedSeparators.docx* dans Microsoft Word. La ligne du séparateur de note de bas de page en bas de la première page de notes sera désormais un astérisque unique (`*`). Si le document contient des notes de fin, la ligne séparant le texte principal de la liste des notes de fin apparaîtra sous forme de tiret (`-`). Tout le reste du contenu (texte, images, tableaux) reste inchangé.

---

## Questions fréquentes & gestion des cas particuliers

| Question | Réponse |
|----------|---------|
| **Et si le document ne contient aucune note de bas de page ?** | `FootnoteOptions.Separator` renvoie toujours un nœud `Run`, mais son texte peut être vide. Le code vérifie en toute sécurité le type du nœud avant de le modifier. |
| **Puis‑je utiliser une chaîne de plusieurs caractères (par ex., "***") ?** | Oui. La propriété `Run.Text` accepte n’importe quelle chaîne, y compris les caractères Unicode. |
| **Le changement du séparateur affecte‑t‑il la numérotation des notes ?** | Non. Le séparateur est indépendant du schéma de numérotation. |
| **Dois‑je libérer l’objet `Document` ?** | `Document` implémente implicitement `IDisposable` via `Node`. Dans une petite application console c’est optionnel, mais pour des services de longue durée vous pouvez l’envelopper dans un bloc `using`. |
| **Comment cela fonctionne‑t‑il avec .NET Core vs .NET Framework ?** | L’API est identique sur les deux runtimes ; seule la version cible du framework doit être prise en charge par le package Aspose.Words. |

**Astuce :** Si vous devez appliquer des séparateurs différents selon les sections, vous pouvez parcourir `doc.GetChildNodes(NodeType.Footnote, true)` et ajuster individuellement la propriété `Separator` de chaque note. C’est plus avancé mais très utile pour les documents complexes.

---

## Conclusion

Vous savez maintenant comment **modifier le séparateur de note de bas de page** et **modifier le séparateur de note de fin** dans un fichier Word en utilisant Aspose.Words pour C#. Le guide a couvert le chargement du document, l’accès aux nœuds séparateurs pertinents, la modification de leur texte et l’enregistrement du résultat—le tout dans un programme autonome.

À partir d’ici, vous pouvez explorer des sujets connexes tels que **modifier le style du séparateur de note de bas de page**, personnaliser la numérotation des notes, ou appliquer un formatage conditionnel en fonction de la mise en page. Le même modèle (récupérer un nœud, le convertir en `Run`, modifier `Text`) fonctionne pour de nombreux autres scénarios de traitement Word.

Bon codage, et n’hésitez pas à expérimenter avec différents symboles ou même à intégrer des images comme séparateurs pour un rendu de document vraiment unique !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource inclut des exemples de code complets avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et à explorer des approches d’implémentation alternatives dans vos projets.

- [Words Processing with Footnote and Endnote](/words/english/net/working-with-footnote-and-endnote/)
- [Get Paragraph Style Separator In Word Document](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [Insert Document Style Separator in Word](/words/english/net/programming-with-styles-and-themes/insert-style-separator/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}