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

**5.** La commande bash ouvre un nouveau niveau sur le shell. La variable MY_VAR n'existe pas car c'est une variable locale 

**6.** Je transforme MY_VAR en une variable d’environnement.
`export MY_VAR="yes"` puis `printenv MY_VAR` et je vois yes qui apparait

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
#!/bin/bash
result=$(( $RANDOM % 1000 + 1 ))
echo $result
var=11000
while [ $var -ne $result ]
do
        echo "Entrez un nombre entre 1 et 1000 :"
        read var
        if [ $var -lt $result ]
        then
                echo"Cest plus !"
        elif [ $var -gt  $result ]
        then
                echo "C'est moins !"
        elif [ $var -eq $result ]
        then
                echo "C'est Gagné !"
        fi
done
exit
```

# Exercice 7. Statistiques
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

arrayValues=()

while :
do
        echo "Veuillez saisir un nombre à ajouter ou taper \"next\" pour passer à la suite:"
        read value

        if [ "$value" = "next" ]; then
                break
        fi

        arrayValues+=($value)

done

max=-100
min=100
total=0

for var in "${arrayValues[@]}"
do
        if [ "$var" -gt "100" ] || [ "$var" -lt "-100" ]; then
                echo "Veuillez utiliser 3 nombres réelle entre 100 et -100"
                exit 1
        fi

        if [ $var -gt $max ]; then
                let max=$var
        fi

        if [ $var -lt $min ]; then
                let min=$var
        fi
        
        let total=total+$var
done

let average=$total/${#arrayValues[@]}
echo "Max: $max; Min: $min; Moyenne: $average"
```

# Exercice 8. Pour les plus rapides
```bash
#!/bin/bash

s="               by js et lolo"
echo "FG \ BG      40  41  42  43  44  45  46  47"
for aaa in `seq 1 13`
do
        if [ $aaa -eq 1 ]; then
                var2="1"
        elif [ $aaa -eq 2 ]; then
                var2="1"
        elif [ $aaa -eq 3 ]; then
                var2="4"
        elif [ $aaa -eq 4 ]; then
                var2="5"
        elif [ $aaa -eq 5 ]; then
                var2="7"
        elif [ $aaa -eq 6 ]; then
                var2="30"
        elif [ $aaa -eq 7 ]; then
                var2="31"
        elif [ $aaa -eq 7 ]; then
                var2="31"
        elif [ $aaa -eq 8 ]; then
                var2="32"
        elif [ $aaa -eq 9 ]; then
                var2="33"
        elif [ $aaa -eq 10 ]; then
                var2="34"
        elif [ $aaa -eq 11 ]; then
                var2="35"
        elif [ $aaa -eq 12 ]; then
                var2="36"
        elif [ $aaa -eq 13 ]; then
                var2="37"
        fi

        echo -e "$var2       \c"
        for var in `seq 39 47`
        do

                couleur="\e["
                couleur="${couleur}${var2}"
                couleur="${couleur};${var}"
                couleur="${couleur}m"
                C="$couleur"
                if [ $var -eq 39 ]; then
                var="40"
                couleur="\e["
                couleur="${couleur}${var2}"
                couleur="${couleur};${var}"
                couleur="${couleur}m"
                C="$couleur"
                echo -e "${C}Bash\e[0m\c"
                else
                echo -e "${C}Bash\e[0m\c"
                fi
        done
        echo ""
done
echo ""
echo "$s"
            
```
