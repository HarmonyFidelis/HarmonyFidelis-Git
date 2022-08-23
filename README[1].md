# GIT

---

Quand nous créons un projet de développement on initialise un projet Git.

Git permmet d'intéragir avec un gestinnaire de version comme Github ou Gitlab. Il nous sert à évitez les pertes, mais également travailliez à plusieurs sur un projet, il existera une version local du projet (votre ordinateur) et une version distante sur un serveur( Github ou GitLab)

---

![](git.png)

## Commande de configuration

Pour configurer git suite à sont installation

Identity :

```code
git config --global user.name "votre_nom_git"
git config --global user.email email@exemple.com
```

Merge :

```code
git config --global core.editor "C:\paths\visua\VSC.exe -w"                     // Votre editeur de code
git config --global merge.tool "C:\paths\visua\VSC.exe -w"                      // Votre editeur de merge
```

Verification :

```code
git config –-list
```

---

## Commande de projet

### Initialisation Git

Lors de la création d'un projet on fait une _initialisation Git_ dans le repertoire du fichier.

```code
git init                    // Initialisation avec une branche main
git flow init               // Initialisation avec plusieurs branch dev
```

### Gitignore

On créer également un fichier .gitignore et README.md :

 - GITIGNORE contient les fichiers ne devant pas etre envoyer sur Github ou Gitlab
 - README permet de décrit le projet en langage MARKDOWN.

```code
touch .gitignore            // Ajouter nom_fichier.extension dans votre fichier .gitignore pour ignorer ce fichier.
touch README.md             // Permet de décrire le projet en langage MARKDOWN.
```

### Branche & Déplacement

Le workflow de branche de fonctionnalité suppose l'existence d'un dépôt centralisé, et la branche main représente toujours l'historique officiel du projet.

Au lieu de faire des commits directement sur leur branche main locale, les développeurs créent une branche dès qu'ils commencent à travailler sur une nouvelle fonctionnalité. Les branches de fonctionnalité doivent avoir des noms descriptifs, comme « animated-menu-items » ou « issue-#1061 ».

```code
GIT :
git branch name_branch                    // Permet de crée une branche
git checkout name_branch                  // Permet de changer de branche
git merge name_branch_fusion              // Permet la fusion de la branch active avec la branch selectionner
git branch -d name_branch                 // Permet de supprimer une branche
git branch –-list                         // Permet de visualiser les branches existantes

GITFLOW :
git flow nom_branch start <name>          // Permet de créer une fonction ou correctif
git flow nom_branch finish <name>         // Permet de finir une fonction ou correctif
git flow nom_branch publish <name>
git flow nom_branch track <name>
git flow nom_branch diff <name>
git flow nom_branch rebase <name>
git flow nom_branch checkout <name>
git flow nom_branch pull <name>
git flow nom_branch delete <name>

# Production [main]                       // Branche de production, version actuelle du projet
# Développement [develop]                 // Branche de développement, centralise fonctionnalités prochaine version
# Feature [name_function]                 // Branche de fonctionnalité. Ont développera dans branche et RELEASE
# Release [name_function]                 // Branche de teste. Si test ok merge DEVELOP sinon HOTFIX
# Bugfix [name_request]                   // Branche de correction bug en developpement
# Hotfix branch [name_request]            // Branche de correction bug en production
# Support branch []                       // Branche de support supplementaire
```

### Pré-sauvegarde
```
git status                              // Visualisation des choses à sauvegarder

git add nom_fichier.extension			// Ajoute un fichier à la liste des choses à sauvegarder.
git add .					            // Ajoute tous les fichiers à la liste [ .gitignore list ] 
git add *.extension				        // Ajoute fichiers se terminant par l’extension des choses à sauvegarder.
git add *.extension *.extension		    // Ajoute fichiers se terminant par les extensions des choses à sauvegarder.

git rm –-cached nom_fichier.extension	// Enlève le fichier de la liste des choses à sauvegarder.
git rm -r –-cached .				    // Enlève tous les fichiers de la liste des choses à sauvegarde

git checkout nom_fichier.extension      // Permet de restaurer le fichier supprimer, mais en cache.
git checkout .                          // Permet de restaurer tous les fichiers supprimer, mais en cache.
```
### Sauvegarde
```
git log                                 // Visualisation des commits [Référencecommit : ca83a6df(8first_caractère)] 
git log référencecommit			        // Permet de voir qui à commit le fichier
git blame nom_fichier.extension		    // Permet de voir qui à commit le fichier

                     
git commit -m “ message ”               // Permet de sauvegarde définitivement la liste des choses à sauvegarder.
git commit –amend -m “nouveau message”  // Permet de modifier message du dernier commit 

git checkout référencecommit		    // Permet de basculer sur ceux commit.

git reset référencecommit –-soft		// Permet de retourner sur commit sans effacer commit
git reset référencecommit –-mixed		// Permet de retourner sur un commit en mettant commit précédent de côté
git reset référencecommit --hard 		// Permet de supprimer tous les commits jusqu’au commit choisit.

git cherry-pick référencecommit		    // Permet fusionner la branche ou nous somme avec un autre commit

git stash nom_fichier.extension         // Permet de mettre de côté fichier modifié sans prendre en compte dans commit
git stash list                          // Permet de voir les fichiers mis de côté.
git stash apply nom_stash({stash@1})    // Permet de restitué les fichiers mis de côté.

_Rebase_
git rebase [COMMAND] [SHA]              // Permet d’organiser commit en modif, deplacer et supprime certain 
git rebase [COMMAND] [BRANCH]           // Permet d’organiser commit en modif, deplacer et supprime certain 

# COMMAND : 
# i, info   =   Permet d'avoir information relative au commit
# p, pick   =   Permet d'utilisez le commit
# r, reword =   Permet d'utilisez le commit, mais éditez le message de commit
# e, edit   =   Permet d'utilisez le commit, mais arrêtez-vous pour apporter des changements
# s, squash =   Permet de regrouper les commits en un commit et regroupera tous vos message
# f, fixup  =   Commande similaire à "squash", mais qui permet d'annuler le message de log de ce commit
# x, exec   =   Exécutez la commande (le reste de la ligne) à l'aide de Shell 
# d, drop   =   supprimez le commit
```
### Envoie
```
git push -u origin name_branch
```

### Mise à jour 
```
git pull                                            // MAJ sur votre dépôt local avec dépôt distant.
git fetch
```
### Communication avec GITHUB ou GITLAB

```code
git remote add nom_association [Adresse HTTP]       // Permet d’associer repos local à un repos distant
git clone [Adresse HTTP]                            // Permet de cloner le dépôt distant sur le dépôt local.
```

### Débogage
```
git bisect start SHA(sans bug) SHA (avec le bug)    // Permet de retrouvez les commits présentant le bug 

# git bisect good                                   
# git bisect bad                            
```
### Other command
```
git reflog                                          // Permet de voir l’historique des actions effectués.
```
```
# Supprimez les branches qui sont inactives depuis plus de 3 mois (ATTENTION ! )
# Rebasage des commits pour que l’historique soit plus clair.
# Modifier les messages des commits pour qu’il soit plus cohérent
```