---
category: general
date: 2026-08-23
description: Traduisez une chaîne en espagnol en C# à l'aide d'Aspose.Words AI Translator
  et du fournisseur Google. Suivez le guide étape par étape pour traduire rapidement
  une chaîne en C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- translate string to spanish
- translate string in c#
language: fr
lastmod: 2026-08-23
og_description: Traduire une chaîne en espagnol en C# avec Aspose.Words AI. Ce tutoriel
  montre comment configurer le fournisseur Google, traduire une chaîne et afficher
  le résultat.
og_image_alt: Console screenshot showing translate string to spanish output in a C#
  application
og_title: Traduire une chaîne en espagnol en C# – exemple complet de code
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Translate string to Spanish in C# using Aspose.Words AI Translator
    and Google provider. Follow the step‑by‑step guide to translate string in C# quickly.
  headline: Translate string to Spanish in C# with Aspose.Words AI
  type: TechArticle
- description: Translate string to Spanish in C# using Aspose.Words AI Translator
    and Google provider. Follow the step‑by‑step guide to translate string in C# quickly.
  name: Translate string to Spanish in C# with Aspose.Words AI
  steps:
  - name: '**Obtain an API key** from the Google Cloud Console → APIs & Services →
      Credentials.'
    text: '**Obtain an API key** from the Google Cloud Console → APIs & Services →
      Credentials.'
  - name: '**Enable the Cloud Translation API** for your project.'
    text: '**Enable the Cloud Translation API** for your project.'
  - name: Store the key securely (environment variable, secret manager, etc.). The
      example uses a literal for clarity, but production code should avoid hard‑coding
      secrets.
    text: Store the key securely (environment variable, secret manager, etc.). The
      example uses a literal for clarity, but production code should avoid hard‑coding
      secrets.
  - name: Open a terminal in the project folder.
    text: Open a terminal in the project folder.
  - name: Execute `dotnet run`.
    text: Execute `dotnet run`.
  - name: Confirm that the console displays the Spanish phrase.
    text: Confirm that the console displays the Spanish phrase.
  type: HowTo
tags:
- Aspose.Words
- C#
- Localization
title: Traduire une chaîne en espagnol en C# avec Aspose.Words IA
url: /fr/net/ai-powered-document-processing/translate-string-to-spanish-in-c-with-aspose-words-ai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Traduire une chaîne en espagnol en C# avec Aspose.Words AI

Si vous devez **traduire une chaîne en espagnol** dans une application .NET, ce guide montre exactement comment le faire. Vous verrez un exemple complet et exécutable qui crée un traducteur, appelle le service Google et affiche le texte en espagnol.

Le tutoriel couvre également **traduire une chaîne en C#** en utilisant la bibliothèque Aspose.Words AI, afin que vous puissiez intégrer la localisation directement dans votre code sans scripts externes.

## Ce dont vous avez besoin

- SDK .NET 6.0 ou ultérieur (le code se compile avec .NET Core et .NET Framework)
- Une clé API Google Cloud Translation active
- Le package NuGet `Aspose.Words.AI` (installez-le avec `dotnet add package Aspose.Words.AI`)
- Un éditeur de code ou un IDE tel que Visual Studio 2022

Ces prérequis garantissent que l’exemple fonctionne immédiatement.

## Traduire une chaîne en espagnol avec Aspose.Words AI

Cette section crée l’objet `Translator` configuré pour le fournisseur Google. Le fournisseur gère la requête HTTP vers le point d’accès de traduction de Google.

```csharp
using System;
using Aspose.Words.AI;          // Namespace for Translator
using Aspose.Words.AI.Translator; // Contains TranslationProvider and Language enums

class Program
{
    static void Main()
    {
        // Step 1: Create a translator that uses Google as the provider
        var translator = new Translator(
            provider: TranslationProvider.Google,
            apiKey: "YOUR_GOOGLE_KEY");   // Replace with your real API key

        // Step 2: Translate the source text into Spanish
        string spanishText = translator.Translate(
            "Hello world",
            Language.Spanish);

        // Step 3: Use the translated text (display it in the console)
        Console.WriteLine(spanishText);
    }
}
```

**Pourquoi cela fonctionne :**  
- `Translator` abstrait l’appel HTTP, gérant l’authentification avec la clé API que vous fournissez.  
- `TranslationProvider.Google` indique au SDK d’acheminer la requête vers Google Cloud Translation.  
- `Language.Spanish` sélectionne le code de langue cible (`es`).  
- La méthode `Translate` renvoie la chaîne traduite, que vous pouvez utiliser n’importe où dans votre application.

## Configurer le fournisseur de traduction Google

1. **Obtenez une clé API** depuis la Google Cloud Console → APIs & Services → Credentials.  
2. **Activez l’API Cloud Translation** pour votre projet.  
3. Stockez la clé de façon sécurisée (variable d’environnement, gestionnaire de secrets, etc.). L’exemple utilise une valeur littérale pour plus de clarté, mais le code de production doit éviter de coder les secrets en dur.

## Traduire la chaîne en C# – étape par étape

| Étape | Action | Raison |
|------|--------|--------|
| 1 | Instancier `Translator` avec `TranslationProvider.Google` | Connecte le SDK au service Google |
| 2 | Appeler `Translate(source, Language.Spanish)` | Envoie le texte source et reçoit le résultat en espagnol |
| 3 | Afficher le résultat avec `Console.WriteLine` | Vérifie la traduction et montre l’utilisation |

Exécuter le programme affiche :

```
¡Hola mundo!
```

> **Remarque :** La sortie exacte peut varier légèrement selon le modèle de traduction de Google (par ex., « Hola mundo » vs. « ¡Hola mundo! »). Les deux sont des équivalents valides en espagnol.

## Exécuter et vérifier la sortie

1. Ouvrez un terminal dans le dossier du projet.  
2. Exécutez `dotnet run`.  
3. Vérifiez que la console affiche la phrase en espagnol.

Si la console montre une erreur telle que *« 401 Unauthorized »*, revérifiez que la clé API est correcte et que l’API Cloud Translation est bien activée pour le projet.

## Problèmes courants et bonnes pratiques

- **Limites de quota API** – Google impose des limites de requêtes par compte de facturation. Surveillez l’utilisation dans la Cloud Console pour éviter un throttling inattendu.  
- **Latence réseau** – Les appels de traduction sont des requêtes HTTP distantes. Envisagez de mettre en cache les chaînes fréquemment traduites pour réduire la latence.  
- **Problèmes d’encodage** – Le SDK travaille avec des chaînes UTF‑8 ; assurez‑vous que vos fichiers sources sont enregistrés en UTF‑8 afin de préserver les caractères spéciaux.  
- **Gestion des erreurs** – Enveloppez l’appel `Translate` dans un bloc try‑catch pour gérer `ApiException` et fournir un texte de secours.

```csharp
try
{
    string spanishText = translator.Translate("Hello world", Language.Spanish);
    Console.WriteLine(spanishText);
}
catch (ApiException ex)
{
    Console.Error.WriteLine($"Translation failed: {ex.Message}");
    // Fallback to original text
    Console.WriteLine("Hello world");
}
```

## Étendre l’exemple

- **Traduire vers d’autres langues** – Remplacez `Language.Spanish` par `Language.French`, `Language.German`, etc.  
- **Traduction par lots** – Appelez `Translate` dans une boucle pour traiter une liste de chaînes.  
- **Intégrer à l’UI** – Utilisez la chaîne traduite dans les pages Razor ASP.NET Core, Windows Forms ou les applications WPF.

## Conclusion

Vous savez maintenant comment **traduire une chaîne en espagnol** en C# en utilisant Aspose.Words AI et le service Google Translation. La solution complète couvre la configuration du fournisseur, l’appel de traduction, la gestion des erreurs et la vérification de la sortie.

À partir d’ici, expérimentez avec d’autres langues, mettez en cache les résultats pour améliorer les performances et intégrez le traducteur dans des pipelines de localisation plus larges.

--- 

*Prêt à localiser davantage de contenu ? Consultez le prochain tutoriel sur **traduire une chaîne en C# avec Azure Cognitive Services** pour une alternative de fournisseur cloud.*

## Que devriez‑vous apprendre ensuite ?


Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource inclut des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Remplacer par une chaîne](/words/spanish/net/find-and-replace-text/replace-with-string/)
- [Remplacer par une chaîne](/words/english/net/find-and-replace-text/replace-with-string/)
- [Créer un document Word avec Aspose.Words – Guide étape par étape](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}