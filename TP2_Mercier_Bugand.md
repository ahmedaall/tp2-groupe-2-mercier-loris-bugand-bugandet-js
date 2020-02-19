# TP 2 - Bash
## Exercice 1. Variables d’environnement

**1.** Les dossiers bash dans lesquels il y a les commandes tapées par l’utilisateur : `printenv PATH` et on a ce chemin comme résultat **/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin
:/bin:/usr/games:/usr/local/games:/snap/bin**


**2.** La variable **$HOME** contient le chemin absolu vers le répertoire personnel de l'utilisateur connecté.

**3.** 
* La variable **$LANG** est utilisée par les différents programmes pour déterminer la langue des messages à afficher. 

**Par exemple :** _`LANG=fr ls fff`_ => _ls: fff: Aucun fichier ou répertoire de ce type_ **|** _`LANG=en ls fff`_ => _ls: fff: No such file or directory_
* La variable **$PWD** contient le chemin absolu vers le répertoire courant (permet de savoir où on est dans l'arborescence).
* La variable **$OLDPWD** contient le chemin absolu vers le répertoire courant précédent (permet de savoir d'où on vient).
* La variable **$SHELL** indique l'interpréteur shell utilisé par défaut. La valeur habituelle sous linux est /bin/bash (plus rarement /bin/sh).
* La variable **$_** contient le dernier argument placé dans la dernière commande shells.

**4.** Pour créer la variable **My_Var** en bash il suffit de taper la commande _`MyVar='la valeur de la variable'`_. Nous pouvons vérifier son existance en utilisant la commande _`echo $My_Var`_.

**5.** 

**6.** 

**7.** Pour créer la variable d'environnement **NOMS** on utilise la commande _`export NOMS='Mercier Bugand-Bugandet'`_ Ensuite il suffit de rentrer la commande _`echo $NOMS`_ pour verifier.

**8.** La commande qui permet d'écrire ”Bonjour à vous deux, binôme1 binôme2 !” (où binôme1 et binôme2
sont vos deux noms) en utilisant la variable NOMS est la suivante : _`echo "Bonjour à vous deux, $NOMS"`_.

**9.** Donner une valeur vide à une varible permet de supprimer son contenu. Utiliser la commande _`unset`_ permet de supprimer compètement la variable des fichiers d'environnement.

**10.** la commande echo pour écrire exactement la phrase : $HOME = chemin (où chemin est votre
dossier personnel d’après bash) est la suivante : _` echo "\$HOME = $HOME"`_
