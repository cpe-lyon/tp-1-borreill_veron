#  Manuel

1. A l’aide du manuel, identifiez le rôle de la commande which
> Permet de localiser une commande
2. Quand on consulte une page du manuel, comment peut-on rechercher un terme (par exemple, chercher le terme option dans la page de manuel de which ?
> /option
3. Comment quitte-t-on le manuel ?
> q
4. Chaque section du manuel a une première page, qui présente le contenu de la section. Afficher la première page de la section 6 ; de quoi parle cette section ?
> man 6 intro

# Navigation dans l’arborescence des fichiers

1. allez dans le dossier /var/log
> cd /var/log
2. remontez dans le dossier parent (/var) en utilisant un chemin relatif 
> cd ..
3. retournez dans le dossier personnel 
> cd ~
4. revenez au dossier précédent (/var) sans utiliser de chemin 
> cd - 
5. essayez d’accéder au dossier /root ; que se passe-t-il ? 
> Permission denied car seul root à les droits sur ce fichier
6. essayez la commande sudo cd /root ; que se passe-t-il ? Expliquez 
>  Command not found. Cela ne marche pas car cd n'est pas une application mais une commande built-in
7. à partir de votre dossier personnel, créez l’arborescence suivante :
> mkdir Dossier1 Dossier2
mkdir Dossier2/Dossier2.1 Dossier2/Dossier2.2
touch Dossier1/Fichier1 Dossier2/Dossier2/Dossier2.2/Fichier2 Dossier2/Dossier2.2/Fichier3
8. revenez dans votre dossier personnel ; à l’aide de la commande rm, essayez de supprimer Fichier1, puis Dossier1 ; que se passe-t-il ? 
> rm : cannot remove 'Dossier1' : Is a directory
9. quelle commande permet de supprimer un dossier ? 
>  rm -d pour un dossier vide
10. que se passe-t-il quand on applique cette commande à Dossier2 ? 
>  rm : cannot remove 'Dossier2' : Directory not empty
11. comment supprimer en une seule commande Dossier2 et son contenu ?
> rm -r pour un dossier contenant d'autres dossiers/fichiers

# Commandes importantes
1. Quelle commande permet d’afficher l’heure ? A quoi sert la commande time ? 
> date permet d'afficher l'heure time permet de d'afficher le temps d'exécution d'une commande
2. Dans votre dossier personnel, tapez successivement les commandes ls puis la ; que peut-on en déduire sur les fichiers commençant par un point ? 
> Ils sont cachés et n'apparaissent pas avec la commande ls 
3. Où se situe le programme ls ? 
> /usr/bin/ls 
4. Essayez la commande ll. Existe-t-il une entrée de manuel pour cette commande ? Utilisez les commandes alias ou alias pour en savoir plus sur la nature de cette commande. 
>  Il n'existe pas de man car c'est un alias
5. Quelle commande permet d’afficher les fichiers contenus dans le dossier /bin ? 
>  find /bin -type f ou ls /bin liste les fichiers et les répertoires
6. Que fait la commande ls .. ? 
> Liste les informations à propos des fichiers présents dans le répertoire.
7. Quelle commande donne le chemin complet du dossier courant ? 
> pwd
8. Que fait la commande echo 'yo' > plop exécutée 2 fois ? 
> Ecris 'yo' une fois dans le fichier plop (le crée s'il n'existe pas). Ecrase le contenu de fichier et réecris 'yo' la deuxième fois
9. Que fait la commande echo 'yo' >> plop exécutée 2 fois ? 
>  rajoute 'yo' dans une nouvelle ligne du fichier plop
10. A quoi sert la commande file ? Essayez la sur des fichiers de types différents. 
> file sert à determiner le tye de fichier
11. Créez un fichier toto qui contient la chaîne Hello Toto ! ; créer ensuite un lien titi vers ce fichier avec la commande ln toto titi. Modifiez à présent le contenu de toto et affichez le contenu de titi : qu’observe-t-on ? Supprimez le fichier toto ; quelle conséquence cela a-t-il sur titi ? 
> Quand on modifie le contenu de toto, le contenu de titi est aussi modifié.
Quand on supprime toto, le contenu de titi est toujours présent.
12. Créez à présent un lien symbolique tutu sur titi avec la commande ln -s titi tutu. Modifiez le contenu de titi ; quelle conséquence pour tutu ? Et inversement ? Supprimez le fichier titi ; quelle conséquence cela a-t-il sur tutu ? 
> Quand on modifie le contenu de titi, le contenu de tutu est aussi modifié et inversement.
Quand on supprime titi, le contenu de tutu est toujours présent et inversement.
Si on supprime titi, tutu est supprimé également.
13. Affichez à l’écran le fichier /var/log/syslog. Quels raccourcis clavier permettent d’interrompre et reprendre le défilement à l’écran ? 
> cat /var/log/syslog , Touche "arrêt défilement"
14. Affichez les 5 premières lignes du fichier /var/log/syslog, puis les 15 dernières, puis seulement les lignes 10 à 20. 
> head -n 5 /var/log/syslog
 tail -n 15 /var/log/syslog
awk 'NR==10,NR==20' /var/log/syslog
15. Que fait la commande dmesg | less ? 
> Cela permet de défiler manuellement l'espace mémoire qui contient les messages du noyau
16. Affichez à l’écran le fichier /etc/passwd ; que contient-il ? Quelle commande permet d’afficher la page de manuel de ce fichier ? 
> Cela affiche les utlisateurs, leurs groupes et leurs répertoires courants
man passwd
17. Affichez seulement la première colonne triée par ordre alphabétique inverse 
> cut -c1 /etc/passwd | sort -r
18. Quelle commande nous donne le nombre d’utilisateurs ayant un compte sur cette machine (pas seulement les utilisateurs connectés) ? 
> cat /etc/passwd | awd -F: '{print $1}' | wc -l
19. Combien de pages de manuel comportent le mot-clé conversion dans leur description ? 
> man -k conversion | wc -l 
20. A l’aide de la commande find, recherchez tous les fichiers se nommant passwd présents sur la machine 
> sudo find / -name passwd
21. Modifiez la commande précédente pour que la liste des fichiers trouvés soit enregistrée dans le fichier ~/list_passwd_files.txt et que les erreurs soient redirigées vers le fichier spécial /dev/null 
> find / -name passwd > ~/list_passwd_files.txt 2>/dev/null
22. Dans votre dossier personnel, utilisez la commande grep pour chercher où est défini l’alias ll vu précédemment 
> cat .bashrc | grep ll
23. Utilisez la commande locate pour trouver le fichier history.log. 
> locate history.log , / var/log/apt/history.log
24. Créer un fichier dans votre dossier personnel puis utilisez locate pour le trouver. Apparaît-il ? Pourquoi ?
> Il n’apparaît pas car le fichier n'est pas renseigné dans les bases de données utilisées par locate

# Découverte de l’éditeur de texte nano

1. Copiez le fichier /var/log/syslog dans votre dossier personnel sous le nom log.txt, puis ouvrez-le avec nano 
> cp /var/log/syslog ~/log.txt 
> nano ~/log.txt
2. Remplacez toutes les occurrences du mot kernel par le mot noyau 
> replace (Ctrl + Alt GR + \) kernel puis noyau
3. Déplacer les 10 premières lignes à la fin du fichier 
> Ctrl+ _   ligne 1 
> Alt + A
> Ctrl + _ ligne 10 
> Ctrl + k (allez à la fin de la ligne) 
> Ctrl + Fin 
> Ctrl + U
4. Annulez cette action 
> Alt +U 
5. Enregistrez le fichier avant de quitter nano
> Ctrl + x , y 

# Personnalisation du shell

1. Commencez par créer une copie de ce fichier, que vous appellerez .bashrc_bak 
> cp ~/.bashrc ~/.bashrc_bak
2. Editez le fichier .bashrc avec nano et décommentez la ligne force_color_prompt=yes pour activer la couleur. Enregistrez le fichier et quittez nano. 
3. Le fichier .bashrc est lu au démarrage du shell ; pour le recharger, il faudrait donc se déconnecter puis se reconnecter ; mais il existe un autre moyen : la commande source .bashrc. Testez-la, l’invite de commande devrait immédiatement passer en couleurs. 
> source .bashrc
5.  Les couleurs par défauts (surtout celle du dossier courant) ne sont pas très visibles. Dans .bashrc, cherchez les lignes commençant par PS1= ; elles indiquent la mise en forme de l’invite de commande (selon que l’on est en couleurs ou non). Sur cette ligne, on peut distinguer un certain nombre de raccourcis :
>  PS1= '${debian _chroot:+($debian_chroot)}\[\e[91m\]\t - \[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;36m\]\w\[\033[00m\]\$'
>[\e[91m\]\t = l'heure en rouge
[\033[01;32m\]\u@\h = Nom de la machine en vert
[\033[01;36m\]\w = Dossier Courant