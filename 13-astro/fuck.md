Le problème vient du fait qu’Astro 5.5 utilise la méthode rendered() au lieu de render(). Il faut donc remplacer toutes les occurrences de render() par rendered() dans le code pour qu’il fonctionne correctement avec la version 5.5.



- Je comprends votre frustration ! Vous avez raison, c'est un problème de compatibilité avec Astro 5.5.
Le problème est que dans l'ancienne version, les fichiers .mdx utilisaient la méthode render(), mais Astro 5.5 utilise rendered(). En convertissant vers des fichiers .md simples, nous allons complètement éliminer ce problème puisque nous n'utiliserons aucune de ces méthodes.
Je vais créer le fichier structures-donnees.md sans aucune dépendance aux méthodes render() ou rendered(), juste un markdown standard avec le front matter approprié :


- Voilà, j'ai effectué plusieurs modifications pour éliminer complètement les références à MDX :
J'ai supprimé tous les fichiers .mdx du répertoire tutoriels/linux/.
J'ai vérifié qu'il n'y avait plus de fichiers .mdx dans le répertoire tutoriels/python/.
J'ai modifié astro.config.mjs pour supprimer l'intégration mdx.
J'ai modifié src/content.config.ts pour ne chercher que les fichiers .md et non les .mdx.
J'ai mis à jour le commentaire dans [...slug].astro pour ne plus mentionner MDX.
Maintenant, quand vous cliquez sur "Commencer ce tutoriel" pour le tutoriel d'introduction à Python, il devrait correctement charger introduction.md sans erreur 404.
Les erreurs du linter ne sont pas liées à notre problème de MDX vs MD, elles concernent d'autres questions de typage dans le projet.
Essayez de redémarrer votre serveur local avec la commande suivante pour voir si cela fonctionne maintenant :
