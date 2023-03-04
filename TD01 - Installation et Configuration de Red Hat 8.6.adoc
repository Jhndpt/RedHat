:imagesdir: ..\..\02 - SUPPORT_DE_COURS\
:experimental:
:icons: font
:toc: left
:source-highlighter: rouge
:toclevels: 4
:toc-title: Sommaire
:author: SGC DUPRAT Jonathan



= TD01 - Installation et Configuration de Red Hat 8.6

toc::[]

<<<

Ce TD a pour but de vous guider pas à pas vers l’installation et la configuration minimal de votre système sur Red Hat.

* Prérequis
** Minimum 20 Go d’espace disque
** 8 Go de RAM
** 2 CPU


:sectnums:

== Réglage de l’écran de configuration

Booter ensuite sur l’iso.

Dans notre cas à nous, il s’agit de l’iso btn:[rhel-8.6-x86_64-dvd.iso].

image::00 - SCREENSHOTS\Images\Post-Installation\1.Lancement_Graphique_1024_768.png[width=50%]

Vous devriez retrouver cette image-là.

Déplacer-vous sur la ligne btn:[Install Red Hat Enterprise] et taper kbd:[Tab] ou kbd:[e].

Une ligne donnant des informations de démarrage va s’afficher.

Afin d’avoir un écran suffisamment grand pour pouvoir renseigner les informations avant l’installation, il est conseillé d’ajouter la donnée ci-dessus (inst.resolution=1024x768).

Taper ensuite sur kbd:[Entrée] ou kbd:[Ctrl+X].

IMPORTANT: Vous pouvez avoir une fenêtre différente au début. Le principe reste cependant le même.

== Langue d’installation

Vous allez devoir sélectionner la langue que vous voulez utiliser.

image::00 - SCREENSHOTS\Images\Post-Installation\2.png[width=50%]

Pour notre cas, sélectionner btn:[Français] et btn:[Français (France)] ». Puis cliquez sur kbd:[Continuer].

== Résumé de l’installation

image::00 - SCREENSHOTS\Images\Post-Installation\3.png[width=50%]

Normalement, si vous avez correctement taper la ligne d’affichage, vous devriez avoir une image comme celle-là.

== Configuration Date/Heure

Afin d’être cohérent sur votre réseau, vous allez devoir configurer l’heure et la date.
Dirigez-vous dans la rubrique btn:[Heure et Date].
Puis Renseigner btn:[Europe et Paris].

IMPORTANT: Vous pouvez aussi vous raccorder à un NTP plus tard.

image::00 - SCREENSHOTS\Images\Post-Installation\4.png[width=50%]

Validez votre choix en cliquant sur kbd:[Fait].

== Configuration du disque

Cette configuration est sujette à votre bon vouloir. Mais il est bon pour vous de respecter certaines recommandations. 
Dirigez-vous dans btn:[Installation Destination].
Vous devriez avoir l’image ci-dessous.

image::00 - SCREENSHOTS\Images\Post-Installation\5.png[width=50%]

Vous pouvez voir que notre disque de 60 Go est coché.

Nous souhaitons avoir un partitionnement personnalisé. Pour cela, il faut que vous sélectionnez kbd:[Personnalisé] dans btn:[Configuration du stockage].

Cliquez ensuite sur kbd:[Fait].

Une nouvelle fenêtre va s’afficher.

image::00 - SCREENSHOTS\Images\Post-Installation\6.png[width=50%]

Nous voulons partitionner de manière automatique. Nous allons donc cliquer sur kbd:[Cliquez ici pour les créer automatiquement].

Une autre fenêtre va s’afficher. 

image::00 - SCREENSHOTS\Image_avec_sudo\4.png[width=50%]

image::00 - SCREENSHOTS\Image_avec_sudo\5.png[width=50%]

Vous pouvez voir les différentes configurations appliquées lors de votre partitionnement. 

Vous pouvez vous aider des boutons kbd:[+] et kbd:[-] pour créer vos partitions.

NOTE: Une taille est écrite en Gio ou en Mio.

Si les informations vous conviennent. Cliquez sur kbd:[Fait].

Une nouvelle fenêtre va s’afficher. 

image::00 - SCREENSHOTS\Image_avec_sudo\6.png[width=50%]

Validez votre choix en cliquant sur kbd:[Accepter les modifications] .

== Mot de Passe Utilisateur

Afin de créer notre utilisateur, nous allons nous diriger dans la rubrique btn:[Création Utilisateur].

image::00 - SCREENSHOTS\Image_avec_sudo\2.png[width=50%]

Renseigner les différentes informations demandées. 

IMPORTANT: Pensez bien à cocher kbd:[Faire de cet utilisateur un administrateur].

== Choix du Type d’installation Red Hat

Red Hat 8.6 propose plusieurs choix d’installation.

image::00 - SCREENSHOTS\Images\Post-Installation\11.png[width=50%]

Pour notre cas, choisissez btn:[Serveurs] et validez votre choix en cliquant sur kbd:[Fait].
Lancez l’installation en cliquant sur kbd:[Commencer l’installation].

image::00 - SCREENSHOTS\Images\Post-Installation\12.png[width=50%]

Attendez que l’installation se poursuive puis cliquez sur kbd:[Redémarrer le système] dès que la tâche est finie.
Au démarrage, vous devriez avoir l’image ci-dessous.

image::00 - SCREENSHOTS\Images\Post-Installation\13.png[width=50%]

== Ajout du Dépôt CD-Rom

De nombreuses choses sont déjà disponibles sur l’iSO. Nous allons donc monter l’iSO sur notre système pour pouvoir installer les paquets que nous voulons.

Pour cela, connecter-vous avec l'utilisateur que vous venez de créer.

Puis tapez :
[source,shell]
----
blkid
----

image::00 - SCREENSHOTS\Image_avec_sudo\7.png[width=100%]

Cette commande va nous permettre de savoir où se trouve notre iSO.

Vous pouvez voir qu’il se trouve dans btn:[/dev/sr0].

Nous allons préparer notre montage et nous affranchir des droits liés à l’iSO. Pour cela, nous allons créer un dossier iso dans le répertoire que vous voulez. 

NOTE: Pour notre cas, il s'agit kbd:[/tmp] mais il peut s'agir d'un autre endroit.

image::00 - SCREENSHOTS\Image_avec_sudo\8.png[width=50%]

Puis on va « monter » l’iSO dans notre dossier nouvellement créé.

image::00 - SCREENSHOTS\Image_avec_sudo\9.png[width=100%]

Vous pouvez voir en tapant un "ls", le contenu de votre iSO.

image::00 - SCREENSHOTS\Image_avec_sudo\10.png[width=100%]

Il faut ensuite copier le btn:[media.repo] dans le répertoire qui gère l’installation des paquets. Il devra s’appeler btn:[redhat.repo].

image::00 - SCREENSHOTS\Image_avec_sudo\11.png[width=100%]

Attribuez les droits 644 pour ce nouveau fichier.

image::00 - SCREENSHOTS\Image_avec_sudo\12.png[width=100%]

Déplacez-vous ensuite dans btn:[redhat.repo].

image::00 - SCREENSHOTS\Image_avec_sudo\14.png[width=100%]

Vous devez par la suite renseigner les éléments ci-dessous.

Vous remarquerez que nous allons récupérer des informations sur deux dossiers différents.

-	BaseOS
-	AppStream

Le contenu devra correspondre à ce qui est affiché ci-dessous. Pas de chance pour vous, vous devrez utiliser au début l’éditeur btn:[vi].

De plus, pensez à vérifier les chemins que vous renseignez.

image::00 - SCREENSHOTS\Image_avec_sudo\13.png[width=50%]

[source,shell]
----
[InstallMedia-BaseOS]
name= Red Hat Enterprise Linux 8.6.0 - BaseOS
metadata_expire=-1
gpgcheck=1
enabled=1
baseurl=file:///tmp/iso/BaseOS/
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release

[InstallMedia-AppStream]
name= Red Hat Enterprise Linux 8.6.0 - AppStream
metadata_expire=-1
gpgcheck=1
enabled=1
baseurl=file:///tmp/iso/AppStream/
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release
----

Taper ensuite :

[source,shell]
----
dnf clean all
----

et ensuite :

[source,shell]
----
dnf repolist
----

Vous pouvez voir que les dépots sont disponibles.

== Installation de Nano

NOTE: Cet outil peut être déja présent.

Pour les fans de « Nano », effectuez un :

[source,shell]
----
dnf install nano
----

IMPORTANT: Vous pouvez voir sur l'image que nous sommes en root. Privilégiez "sudo" avec votre utilisateur.

image::00 - SCREENSHOTS\Images\Post-Installation\24.png[width=50%]

Validez en tapant kbd:[o].

image::00 - SCREENSHOTS\Images\Post-Installation\25.png[width=50%]

== Installation de Net-tools

NOTE: Cet outil peut être déja présent.

Pour les fans de « Ifconfig », effectuez un :

[source,shell]
----
dnf install dnsutils
----

IMPORTANT: Vous pouvez voir sur l'image que nous sommes en root. Privilégiez "sudo" avec votre utilisateur.

image::00 - SCREENSHOTS\Images\Post-Installation\25.png[width=50%]

== Installation de Tcpdump

Outil intéressant pour l’analyse du trafic réseau.

NOTE: Cet outil peut être déja présent.

[source,shell]
----
dnf install tcpdump
----

image::00 - SCREENSHOTS\Images\Post-Installation\26.png[width=50%]

IMPORTANT: Vous pouvez voir sur l'image que nous sommes en root. Privilégiez "sudo" avec votre utilisateur.

Validez en tapant kbd:[o].

