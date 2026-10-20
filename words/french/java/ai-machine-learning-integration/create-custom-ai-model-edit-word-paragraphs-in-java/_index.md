---
category: general
date: 2026-03-25
description: Créez un modèle d'IA personnalisé pour modifier des documents Word –
  apprenez à rendre le texte plus formel, à remplacer le texte d'un paragraphe et
  à réécrire un paragraphe Word en utilisant Aspose.Words AI.
draft: false
keywords:
- create custom ai model
- make text more formal
- replace paragraph text
- edit paragraph with ai
- rewrite word paragraph
language: fr
og_description: Créez un modèle d'IA personnalisé pour modifier des documents Word.
  Apprenez à rendre le texte plus formel, à remplacer le texte d'un paragraphe et
  à réécrire un paragraphe Word à l'aide d'Aspose.Words AI.
og_title: Créer un modèle d'IA personnalisé – Modifier des paragraphes Word en Java
tags:
- Aspose.Words
- Java
- AI integration
title: Créer un modèle d'IA personnalisé – Modifier les paragraphes Word en Java
url: /fr/java/ai-machine-learning-integration/create-custom-ai-model-edit-word-paragraphs-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer un modèle IA personnalisé – Modifier les paragraphes Word en Java

Vous avez déjà eu besoin de **créer un modèle IA personnalisé** capable de peaufiner un paragraphe dans un fichier Word ? Peut‑être avez‑vous un lot de contrats qui sonnent un peu trop familiers, et vous aimeriez rendre le texte plus formel avec une seule ligne de code. Bonne nouvelle : c’est exactement ce que vous pouvez faire—sans services externes, sans SDK lourds, juste Aspose.Words pour Java et un point d’accès compatible OpenAI.

Dans ce tutoriel, nous passerons en revue chaque étape nécessaire pour **créer un modèle IA personnalisé**, le connecter à un serveur LLM local, puis l’utiliser pour *remplacer le texte d’un paragraphe* par une version plus formelle. À la fin, vous disposerez d’un programme Java exécutable qui **modifie un paragraphe avec l’IA**, réécrit un paragraphe Word, et enregistre le résultat sur le disque. Pas de fioritures, juste une solution pratique que vous pouvez copier‑coller dans votre propre projet.

> **Ce dont vous aurez besoin**  
> • Java 17 ou supérieur (le code compile avec des versions antérieures, mais 17 est le meilleur compromis)  
> • Aspose.Words pour Java 23.9 (ou la dernière version)  
> • Un serveur LLM compatible OpenAI en cours d’exécution (par ex., Ollama, LocalAI) écoutant sur `http://localhost:8000/v1`  
> • Un document Word d’entrée (`input.docx`) placé dans un dossier que vous contrôlez  

Si vous vous demandez *pourquoi construire un modèle personnalisé* plutôt que d’appeler directement OpenAI, la réponse est la flexibilité : vous contrôlez le point d’accès, vous pouvez changer de modèle sans modifier le code, et vous gardez les clés d’API hors de votre dépôt source. Allons‑y.

---

## Créer un modèle IA personnalisé – Configuration

Tout d’abord, nous devons indiquer à Aspose.Words où se trouve notre LLM. La classe `AiModelEndpoint` contient l’URL et la clé API éventuelle. Comme nous utilisons un serveur local, la clé peut être une chaîne vide, mais le paramètre reste obligatoire.

```java
import com.aspose.words.ai.*;

public class LlmDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Define the LLM endpoint (OpenAI‑compatible)
        AiModelEndpoint llmEndpoint = new AiModelEndpoint(
                "http://localhost:8000/v1",   // URL of your LLM server
                "my-api-key");                // API key if required
```

> **Astuce :** Si vous passez un jour à un modèle hébergé (par ex., Azure OpenAI), il suffit de changer l’URL et la clé—aucune autre modification de code n’est nécessaire.

---

## Charger le document Word

Nous chargeons maintenant le fichier source en mémoire. `Document` peut lire les formats `.docx`, `.doc`, `.rtf`, et bien d’autres, mais pour cet exemple nous nous limitons à `.docx`.

```java
        // Step 2: Load the source Word document
        Document document = new Document("YOUR_DIRECTORY/input.docx");
```

Assurez‑vous que `YOUR_DIRECTORY` pointe vers un vrai dossier ; sinon vous obtiendrez une `FileNotFoundException`. Dans une application réelle, vous pourriez passer le chemin en argument de ligne de commande ou le lire depuis un fichier de configuration.

---

## Initialiser le modèle IA personnalisé

Nous créons un `AiModel` de type `CUSTOM` et lui attribuons le point d’accès défini précédemment. Cela indique à Aspose.Words d’acheminer tous les appels IA via notre propre serveur.

```java
        // Step 3: Create a custom AI model that uses the endpoint
        AiModel llmModel = new AiModel(AiModelType.CUSTOM, llmEndpoint);
```

En coulisses, Aspose.Words construit un petit client HTTP qui communique avec le LLM en utilisant le schéma standard de chat/completion d’OpenAI. C’est pourquoi le point d’accès doit être *compatible OpenAI*.

---

## Récupérer et réécrire le premier paragraphe

C’est ici que nous **rendons le texte plus formel**. Nous récupérons le premier paragraphe, envoyons son texte brut au modèle avec une invite, et recevons la version éditée.

```java
        // Step 4: Retrieve the first paragraph and ask the model to rewrite it
        Paragraph firstParagraph = document.getFirstSection()
                                            .getBody()
                                            .getParagraphs()
                                            .get(0);
        String rewrittenText = llmModel.editText(
                firstParagraph.getText(),
                "Make it more formal");
```

Le deuxième argument (`"Make it more formal"`) est l’instruction que nous donnons au modèle. Vous pouvez le remplacer par n’importe quelle directive — **replace paragraph text**, **summarize**, **translate**, etc. La méthode renvoie une chaîne de caractères simple, que nous réinsérerons plus tard dans le document.

> **Pourquoi cela fonctionne :** `editText` envoie une charge JSON comme `{ "model": "...", "messages": [{ "role":"user", "content":"<text>\nMake it more formal"}] }`. Le LLM voit le paragraphe original et l’instruction, puis répond avec le texte révisé.

---

## Remplacer le contenu original du paragraphe

Nous **remplaçons le texte du paragraphe** dans le modèle d’objet Word. Nous vidons les `Run` existants (les morceaux de texte de bas niveau) et insérons un nouveau `Run` contenant la chaîne générée par l’IA.

```java
        // Step 5: Replace the original paragraph content with the rewritten text
        firstParagraph.removeAllChildren();
        firstParagraph.appendChild(new Run(document, rewrittenText));
```

Attention à ne pas appeler `firstParagraph.setText()`—cette méthode supprimerait toute mise en forme. L’utilisation de `Run` préserve le style du paragraphe (titre, puce, etc.) tout en échangeant les caractères réels.

---

## Enregistrer le document modifié

Enfin, nous écrivons le document modifié sur le disque. Vous pouvez écraser le fichier original ou, comme nous le faisons ici, créer une nouvelle copie.

```java
        // Step 6: Save the edited document
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

Lorsque vous ouvrirez `output.docx`, vous devriez voir le premier paragraphe désormais nettement plus formel. Si le LLM n’a pas suivi parfaitement l’instruction, vous pouvez ajuster l’invite ou essayer une version de modèle différente.

---

## Exemple complet fonctionnel

Voici le programme complet—copiez‑le dans `LlmDemo.java`, ajustez les chemins, puis exécutez‑le avec `javac` + `java`.

```java
import com.aspose.words.*;
import com.aspose.words.ai.*;

public class LlmDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Define the LLM endpoint (OpenAI‑compatible)
        AiModelEndpoint llmEndpoint = new AiModelEndpoint(
                "http://localhost:8000/v1",   // URL of your LLM server
                "my-api-key");                // API key if required

        // Step 2: Load the source Word document
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // Step 3: Create a custom AI model that uses the endpoint
        AiModel llmModel = new AiModel(AiModelType.CUSTOM, llmEndpoint);

        // Step 4: Retrieve the first paragraph and ask the model to rewrite it
        Paragraph firstParagraph = document.getFirstSection()
                                            .getBody()
                                            .getParagraphs()
                                            .get(0);
        String rewrittenText = llmModel.editText(
                firstParagraph.getText(),
                "Make it more formal");

        // Step 5: Replace the original paragraph content with the rewritten text
        firstParagraph.removeAllChildren();
        firstParagraph.appendChild(new Run(document, rewrittenText));

        // Step 6: Save the edited document
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

**Sortie attendue :** Ouvrez `output.docx` et vous verrez le paragraphe original transformé. Par exemple, une phrase familière comme « We’ll get the thing done soon. » pourrait devenir « We shall complete the task promptly. ». Le libellé exact dépend du modèle que vous utilisez.

---

## Questions fréquentes & cas particuliers

### Et si mon document comporte plusieurs sections ?

Le code ci‑dessus ne touche que le *premier* paragraphe de la *première* section. Pour **edit paragraph with AI** sur l’ensemble du fichier, parcourez `document.getSections()` puis chaque `section.getBody().getParagraphs()`. N’oubliez pas d’ignorer les paragraphes vides, sinon le LLM recevra une chaîne vide et ne renverra rien.

### Comment gérer les paragraphes très longs qui dépassent les limites de tokens ?

La plupart des LLM limitent l’entrée à environ 4 000 tokens. Si un paragraphe est exceptionnellement long, découpez‑le en morceaux plus petits avant d’appeler `editText`. Vous pouvez réutiliser la même instance `AiModel` ; il suffit de rester attentif aux limites de débit de votre serveur local.

### Puis‑je utiliser une instruction différente, comme « summarize » ou « translate to French » ?

Absolument. Le deuxième argument de `editText` est libre. Pour un résumé, vous pourriez passer `"Summarize in one sentence"`. Pour une traduction, `"Translate to French, keep the tone formal"` fonctionne tout aussi bien. Cette flexibilité vous permet de **replace paragraph text** dans de nombreux scénarios sans changer le code.

### Le modèle conserve‑t‑il le style du paragraphe (polices, couleurs) ?

Comme nous ne remplaçons que le `Run` à l’intérieur du même objet `Paragraph`, les styles existants (niveau de titre, puce, indentation) restent intacts. Si vous devez modifier le style lui‑même, vous pouvez manipuler `Paragraph.getParagraphFormat()` après le remplacement.

### Et si mon serveur LLM nécessite HTTPS avec un certificat auto‑signé ?

`AiModelEndpoint` accepte une URL avec `https://`. Si le certificat n’est pas de confiance, vous devrez configurer le contexte SSL de Java pour l’accepter, ou exécuter le serveur avec un certificat valide. Cette configuration dépasse le cadre de ce tutoriel mais est bien documentée dans les guides Java SSL.

---

## Conseils pour une intégration prête pour la production

| Conseil | Pourquoi c’est important |
|-----|----------------|
| **Mettre en cache le endpoint** | Recréer `AiModelEndpoint` à chaque requête ajoute du surcoût. |
| **Regrouper les éditions** | Si vous avez de nombreux paragraphes, envoyez‑les en une seule requête (par ex., tableau JSON) pour réduire la latence. |
| **Valider la sortie du LLM** | Vérifiez toujours que la chaîne renvoyée n’est pas nulle ou vide avant de l’insérer. |
| **Journaliser les invites et réponses** | Utile pour le débogage et la conformité lorsqu’on réécrit du texte juridique. |
| **Mécanisme de secours gracieux** | Si le LLM est indisponible, revenez au paragraphe original ou à une réécriture heuristique simple. |

---

## Conclusion

Nous vous avons montré comment **créer un modèle IA personnalisé** avec Aspose.Words, le connecter à un point d’accès compatible OpenAI, puis **edit paragraph with AI** pour **rendre le texte plus formel**. En suivant les six étapes—définir le endpoint, charger le document, initialiser le modèle,

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}