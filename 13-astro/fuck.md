Le problème vient du fait qu’Astro 5.5 utilise la méthode rendered() au lieu de render(). Il faut donc remplacer toutes les occurrences de render() par rendered() dans le code pour qu’il fonctionne correctement avec la version 5.5.



- Je comprends votre frustration ! Vous avez raison, c'est un problème de compatibilité avec Astro 5.5.
Le problème est que dans l'ancienne version, les fichiers .mdx utilisaient la méthode render(), mais Astro 5.5 utilise rendered(). En convertissant vers des fichiers .md simples, nous allons complètement éliminer ce problème puisque nous n'utiliserons aucune de ces méthodes.
Je vais créer le fichier structures-donnees.md sans aucune dépendance aux méthodes render() ou rendered(), juste un markdown standard avec le front matter approprié :
