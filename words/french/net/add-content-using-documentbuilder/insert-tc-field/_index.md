---
title: Ajouter un champ TC à un document Word avec Aspose.Words for .NET
weight: 310
limit:
description: Apprenez à insérer un champ TC dans un nouveau document Word avec Aspose.Words for .NET en utilisant DocumentBuilder.
keywords: [Aspose.Words for .NET, insert TC field, DocumentBuilder TC field, Word document indexing, add TC field programmatically, TC field tutorial]
url: /net/add-content-using-documentbuilder/insert-tc-field/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ajouter un champ TC à un document Word avec Aspose.Words
Dans ce tutoriel interactif, vous apprendrez comment ajouter programmétiquement un champ TC — un marqueur caché utilisé par les fonctions d’indexation et de table des matières de Word — à un document fraîchement créé en utilisant Aspose.Words for .NET. En utilisant DocumentBuilder, vous pouvez placer le champ exactement où vous le souhaitez, puis enregistrer le fichier, prêt pour un traitement ultérieur.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-tc-field" >}}


{{< /blocks/products/pf/tutorial-page-section >}}

{{< blocks/products/pf/tutorial-page-section >}}
## Installation Instructions
1. Download Aspose.Words for .NET:
   Get the latest version from the [Aspose Downloads page](https://releases.aspose.com/words/net/).

2. Install via NuGet:
   - Open your Visual Studio project.
   - Navigate to the NuGet Package Manager (Tools > NuGet Package Manager > Manage NuGet Packages for Solution).
   - Search for "Aspose.Words" and click Install.

3. Add Namespace References:
   Add the following namespace at the top of your code file:
   ```csharp
   using Aspose.Words;
   using Aspose.Words.Saving;
   using Aspose.Words.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Que fait réellement le champ \"TC\" inséré par `builder.InsertField(\\\"TC \\\"Entry Text\\\" \\\\\\f t\\\")` dans le document Word ?**
A: Il crée une entrée de table des matières avec le texte visible \"Entry Text\" et la marque comme une entrée TC (Table des matières), que Word pourra ensuite utiliser lors de la génération d’une table des matières.

**Q: Quel est le but du commutateur `\\f t` dans la chaîne du champ TC ?**
A: Le commutateur `\\f t` indique à Word de traiter l’entrée comme une entrée de texte normale (par opposition à un titre) et de l’inclure dans la table des matières lors de sa génération.

**Q: Puis-je insérer plusieurs champs TC avec des textes d’entrée différents en utilisant la même instance de `DocumentBuilder` ?**
A: Oui ; il suffit d’appeler à nouveau `builder.InsertField` avec une chaîne différente, par exemple `builder.InsertField(\\\"TC \\\"Another Entry\\\" \\\\\\f t\\\")`, et chaque appel insère un nouveau champ TC à la position actuelle du curseur.

**Q: Si le texte d’entrée doit être dynamique (par ex., provenant d’une variable), comment dois‑je formater l’appel `InsertField` ?**
A: Construisez la chaîne du champ avec l’interpolation de chaînes ou `String.Format`, par exemple : `string entry = \"Chapter 1\"; builder.InsertField($\"TC \\\"{entry}\\\" \\\\f t\");`.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}