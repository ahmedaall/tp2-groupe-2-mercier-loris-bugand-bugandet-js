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

# Programmation Bash
* Pour créer le dossier **script** il suffit de renseigner la commande suivante : _`cd`_ puis _`mkdir script`_
* Pour renseigner le chemin du dossier **script** dans la variable **PATH** il sufit d'ajouter le chemin de celui-ci depuis la racine faisant : _`sudo nano /etc/environnement`_

## Exercice 2. Contrôle de mot de passe
Pour créer le script **testpwd.sh**, il faut d'abord se déplacer dans le dossier /home/.../script (_`cd \home\...\script `_) et faire un _`touch testpwd.sh`_. Ensuite, il faut donner au fichier les droit d'execution : `_sudo chmod +x testpwd.sh_`.
Pour finir, entrez dans le fichier **testpwd.sh** ( _`nano testpwd.sh`_ ) et entre le code suivant :
```bash
#!/bin/bash
echo "Entrez votre mot de passe :"
read -s mdp
if [ $mdp == "loris" ]
then
        echo "mot de passe correct"
else
        echo "mot de passe incorrect"  
fi
```

## Exercice 3. Expressions rationnelles
Pour créer le script **testnombre.sh**, il faut d'abord se déplacer dans le dossier /home/.../script (_`cd \home\...\script `_) et faire un _`touch testnombre.sh`_. Ensuite, il faut donner au fichier les droit d'execution : _`sudo chmod +x testnombre.sh`_.
Pour finir, entrez dans le fichier **testnombre.sh** ( _`nano testnombre.sh`_ ) et entre le code suivant :
```bash
#!/bin/bash
function is_number()
{
        re='^[+-]?[0-9]+([.][0-9]+)?$'
        if ! [[ $1 =~ $re ]] ; then
                return 1
        else
                return 0
        fi
}
is_number $1
if [ "$?" == "0" ]
then
        echo "L'argument est bien un nombre réel"                                                                               
else
        echo "ERROR !!!"
fi
```

## Exercice 4. Contrôle d’utilisateur
Pour créer le script **testuser.sh**, il faut d'abord se déplacer dans le dossier /home/.../script (_`cd \home\...\script`_) et faire un _`touch testuser.sh`_. Ensuite, il faut donner au fichier les droit d'execution : _`sudo chmod +x testuser.sh`_.
Pour finir, entrez dans le fichier **testnombre.sh** ( _`nano testuser.sh`_ ) et entre le code suivant :
```bash
#!/bin/bash
if [ "$#" == "1" ]
then
 if grep "$1" /etc/passwd > /dev/null
    then
        echo "l'utilisateur existe"
    else
        echo "l'utilisateur n'existe pas"
    fi
else
 echo "Utilisation : ./${0##*/} nom_utilisateur"
fi
```

## Exercice 5. Factorielle
Pour créer le script **fact.sh**, il faut d'abord se déplacer dans le dossier /home/.../script (_`cd \home\...\script`_) et faire un _`touch fact.sh`_. Ensuite, il faut donner au fichier les droit d'execution : _`sudo chmod +x fact.sh`_.
Pour finir, entrez dans le fichier **fact.sh** ( _`nano fact.sh`_ ) et entre le code suivant :
```bash
#!/bin/sh 
 
fact() { 
        n=$1 
        if [ $n -eq 0 ] 
        then 
                echo 1 
        else 
                echo $(( n * `fact $(( n - 1 ))` )) 
        fi 
} 
echo `fact $1`
```
# Exercice 6. Le juste prix
Pour créer le script **devine.sh**, il faut d'abord se déplacer dans le dossier /home/.../script (_`cd \home\...\script`_) et faire un _`touch devine.sh`_. Ensuite, il faut donner au fichier les droit d'execution : _`sudo chmod +x devine.sh`_.
Pour finir, entrez dans le fichier **devine.sh** ( _`nano devine.sh`_ ) et entre le code suivant :
```bash
l
```
