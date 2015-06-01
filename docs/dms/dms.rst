Gestion de courriers (version 0.2)
++++++++++++++++++++++++++++++++++

Note: Ceci est une impression contenant toutes les pages du Manuel de
référence sur une seule page. La version paginée est disponible ici.

L'application permet la gestion de courriers, dont l'encodage et la
transmission à leurs destinataires... Il est nécessaire d'être
CONNECTÉ pour visualiser l'entièreté du manuel.



1. Introduction
===============





1.1. Présentation fonctionnelle
===============================

En quoi consiste l'outil ?

L'activité s'articule autour du processus de gestion des courriers,
dans un premier temps les courriers entrants, ensuite les courriers
sortants.

L'application contient actuellement les fonctionnalités suivantes :


+ Encodage du courrier entrant
+ Association des pièces scannées
+ Recherches prédéfinies suivant l'état des courriers
+ Gestion des contacts (expéditeurs, destinataires)
+ Choix des services concernés et du service traitant
+ Workflow de validation du courrier
+ Workflow de traitement sur tous les courriers




Les fonctionnalités à venir :


+ Gestion des courriers sortants
+ Création automatique de courrier entrant à partir de fichiers
  scannés avec séparateur
+ Ajout de tableau de bord




1.2. Prérequis utilisateur
==========================



Afin de pouvoir utiliser correctement l'application, il est nécessaire
d'installer et configurer différents outils sur le poste de
l'utilisateur:


+ le navigateur `Firefox`_, permettant d'utiliser l'application




2. Utilisation de l'outil gestion du courrier
=============================================





2.1. Premiers pas
=================



Afin de pouvoir utiliser l'outil, il est nécessaire de disposer d'un
compte utilisateur, à demander à l'administrateur du système.

Quand vous disposez de vos données d'authentification, vous pouvez
accéder à l'application en utilisant un des deux liens ("Se connecter"
en haut à droite ou "Cliquez ici pour accéder à l'application" en bas
de page).





2.2. Visualisation des éléments
===============================



Une fois dans l'application, on peut lister le courrier entrant en
cliquant sur le premier onglet.





Un menu situé à gauche permet également de rechercher les courriers
dans les différents états disponibles, et en fonction des droits de
l'utilisateur connecté.





2.3. Encodage
=============

Encodage des courriers, uniquement pour les personnes faisant partie
du groupe "Encodeurs courrier"



Ajout d'un courrier entrant par l'encodeur
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Cliquer sur le lien courrier entrant sous la rubrique Ajouter.




Encodage des données
~~~~~~~~~~~~~~~~~~~~

Le formulaire propose une série de champs à compléter.
Ceux marqués par un carré rouge sont obligatoires.

Le choix ou la création d'un expéditeur est possible sans quitter le
formulaire de base.

Afin de rechercher un contact, il suffit de taper les lettres de début
d'un mot faisant partie de l'intitulé d'un contact ("Prénom Nom",
"Organisation", etc.).
Dès le deuxième caractère, une recherche dynamique dans la base de
donnée propose quelques résultats.

Si le contact n'existe pas, il peut être créé en cliquant sur le lien
"Créer Contact".



Un contact peut être une organisation ou une personne, ou une
combinaison: une fonction d'un organisation, une personne d'une
organisation, une personne d'une organisation occupant une fonction.
Il est à chaque fois possible de retrouver une organisation ou une
personne existante en encodant le début de son intitulé. Pour créer
une nouvelle organisation, cliquer sur "Créer Organisation".



Compléter les champs et sauvegarder.



Pour créer une personne dans l'organisation cliquer sur créer
Personne.



Compléter les champs et sauvegarder.



Pour créer une fonction de la personne dans l'organisation cliquer sur
créer Fonction.



Compléter les champs et sauvegarder.



Cliquer sur ajouter pour créer le contact.



Une fois le contact créé ou sélectionné, on peut visualiser une
information plus complète au survol de la souris



Compléter les autres champs nécessaires du formulaire, et cliquer sur
sauvegarder.




Association du fichier scanné
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Cliquer sur Fichier ged, disponible dans le menu lorsque l'on
visualise un courrier.




Sélectionner le fichier ged
~~~~~~~~~~~~~~~~~~~~~~~~~~~

Cliquer sur parcourir, selectionner le fichier ged, puis cliquer sur
sauvegarder.



Après la sauvegarde, le fichier ged apparait en prévisualisation.

Pour revenir au courrier, cliquer sur l'intitulé du courrier dans le
fil d'ariane (breadcrumb).



Le courrier apparait alors avec la visualisation de son fichier ged à
droite




Changement d'état du workflow
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Une fois l'encodage terminée, l'encodeur peut proposer le courrier au
DG.





2.4. Workflows
==============

Le workflow définit non seulement les étapes de traitement d'un
élément mais aussi permet d'avoir des droits différents suivant
l'état.

Le cycle de vie d'un courrier représente les différents états par
lesquels le courrier transite depuis sa création, jusqu'à sa clôture.


+ En création (après encodage): visible et éditable par les personnes
  du groupe "Encodeurs courrier".







+ A valider par le DG (après avoir été proposé au DG): visible par les
  encodeurs et éditable par les utilisateurs qui ont le rôle "Directeur
  général".







+ A valider par le chef de service (après avoir été proposé au chef de
  service): visible par les précédents et éditable par les personnes du
  groupe correspondant au service traitant avec le rôle validateur.







+ A traiter (après avoir été proposé à l'agent): visible par les
  précédents et éditable par les personnes du groupe correspondant au
  service traitant avec le rôle éditeur.







+ En cours de traitement (après avoir été mis en traitement): droits
  identiques.







+ Clôturé (après avoir été clôturé): droits identiques.








3. Configuration de l'outil Gestion du courrier
===============================================





3.1. Gestion des utilisateurs
=============================



Il est nécessaire de créer un utilisateur dans le système pour chaque
personne qui doit se connecter à l'outil.
Chaque personne doit donc avoir ses propres données
d'authentification.
Il est également nécessaire de définir les droits qu'il va avoir. Cela
se fait soit en donnant un rôle particulier, soit en rajoutant
l'utilisateur dans un groupe particulier (voir plus bas), au moment de
sa création ou par après.

La création d'un utilisateur doit se faire par un administrateur du
système, via la configuration du site.
La documentation nommée "`Gestion des utilisateurs et groupes`_"
explique, dans le premier point, comment ajouter un utilisateur. Le
reste n'est pas utile.

A l'exception du directeur général qui bénéficient de rôles globaux
(celui de "Directeur général"), il est nécessaire de placer les
utilisateurs dans les groupes correspondant aux services activés dans
l'organisation et aux fonctions configurées d'encodeur, lecteur,
éditeur ou validateur. (voir la partie "`gestion de ses services`_"
pour créer ces groupes).

Actuellement, seul le groupe général "Encodeurs courrier" est utilisé
pour y placer les personnes qui pourront créer des courriers entrants.
Les groupes suffixés par "encodeur" ne le sont pas encore.

Même si le groupe n'a pas été sélectionné lors de la création de
l'utilisateur, l'appartenance d'un utilisateur à un groupe peut
toujours être modifiée à n'importe quel moment par l'administrateur
dans la partie "Utilisateurs et groupes" de la configuration du site.



3.2. Gestion de ses services
============================



La gestion de ses services se fait dans l'onglet "Contacts".
On y retrouve également tous les contacts qui ont été ajoutés lors de
la création des courriers.

Dans l'élément intitulé "Mon organisation", on va pouvoir créer une
hiérarchie de département / service. Ceux-ci seront utilisés comme
base de création pour les groupes plone dans lesquels on placera les
utilisateurs.

La documentation intitulée "`Comment configurer la génération
automatique des groupes plone via contact`_" explique comment faire.



3.3. Options propres aux courriers
==================================



Dans la configuration du site se trouve deux liens de configuration de
l'outil




Configuration du courrier
~~~~~~~~~~~~~~~~~~~~~~~~~

Permet de configurer la référence interne qui va être utilisée dans
chaque nouveau courrier.




Configuration du courrier 2
~~~~~~~~~~~~~~~~~~~~~~~~~~~

Permet de définir le vocabulaire des types de courrier qui vont être
utilisés dans la liste déroulante du formulaire d'encodage d'un
courrier entrant.







4. Utilisation du webservice (1ère version) (Obsolète)
======================================================

Le webservice json permet d'envoyer des documents scannés dans la ged



4.1. Accès au webservice
========================



Le webservice de communication avec une instance Plone est accessible
via le nom de domaine de l'outil suffixé par "@@API" (ex: "http
://webservice-ged.communesplone.be/@@API").

Différentes routes (fonctions) sont disponibles dans le webservice.
Elles doivent être renseignées dans l'url derrière "@@API" (ex: "http
://webservice-ged.communesplone.be/@@API/get_schema").

Certaines routes nécessitent le passage de paramètres http en get ou
en post.
Une route configurée en "get" est appelée en spécifiant la route dans
l'url et en passant dans l'url les paramètres nécessaires (ex: "http
://webservice-
ged.communesplone.be/@@API/get_schema?schema=send_dmsfile_in").
Une route configurée en "post" est appelée en spécifiant la route dans
l'url et en passant dans la requête les paramètres nécessaires en post
(ex: "http://webservice-ged.communesplone.be/@@API/send_dmsfile").

Certaines routes demandent une authentification basique pour être
utilisées.

Afin de valider les structures de données échangées, le webservice
implémente des schémas de validation json au format spécifié sur le
site `http://json-schema.org`_.
Les schémas de validation existants sont disponibles via la route
"get_schema" du webservice.



4.2. Route send_dmsfile
=======================



Cette route permet d'envoyer un document scanné.
Elle nécessite une authentification.

L'envoi est constitué d'une requête post qui contient le paramètre
json.
Le contenu du paramètre json est constitué d'une structure de données
json contenant les métadonnées du document ainsi que son contenu
encodé en base64.
Cette structure de données est validée par le schéma obtenu via "http
://webservice-
ged.communesplone.be/@@API/get_schema?schema=send_dmsfile_in".

Le webservice répond au format json afin de fournir un statut de la
requête.
La structure de données renvoyée est validée par le schéma obtenu via
"http://webservice-
ged.communesplone.be/@@API/get_schema?schema=send_dmsfile_out".


`Présentation`_

+ `Présentation`_
+ `Nos atouts`_
+ `Comment adhérer`_
+ `Contributions`_
+ `Comité de gestion`_
+ `Conseil d'administration`_
+ `Dans les médias`_

`Produits`_

+ `Gestion des délibérations`_
+ `Gestion de projet (PST)`_
+ `Gestion de l'urbanisme`_
+ `Gestion électronique de documents`_
+ `Gestion des activités extra-scolaires`_
+ `Site Internet`_
+ `Guichet en ligne`_
+ `Gestion des services techniques`_
+ `Emplois et compétences`_
+ `Processus et simplification administrative `_

`Services`_

+ `Offre All in One`_
+ `Prestations complémentaires`_

`Solutions`_

+ `Logiciels Libres & mutualisation`_
+ `Centrale d'achat`_
+ `Conseil, audit et processus`_

`Support`_

+ `Demande d'assistance (Trac)`_
+ `Documentation`_
+ `Forums`_

`Contact`_

+ `Contactez-nous`_
+ `L'équipe`_

Site officiel de l'Intercommunale de Mutualisation Informatique et
Organisationnelle IMIO 2012 - Avec le soutien de la Wallonie
.. _Prestations complémentaires: http://www.imio.be/services/prestations-complementaires
.. _Firefox: http://www.mozilla.org/fr/firefox/new/
.. _Contenus: http://www.imio.be/support/documentation/manual/gestion-de-courriers/folder_contents
.. _Guichet en ligne: http://www.imio.be/produits/guichet-en-ligne
.. _Manuels de référence: http://www.imio.be/support/documentation/manual
.. _FAQs: http://www.imio.be/support/documentation/faqs
.. _Produits: /imio/imio/produits
.. _Gestion de l'urbanisme: http://www.imio.be/produits/gestion-de-lurbanisme
.. _Contributions: http://www.imio.be/presentation/contributions
.. _Présentation: /imio/imio/presentation
.. _admin: http://www.imio.be/useractions
.. _How-tos: http://www.imio.be/support/documentation/how-to
.. _Dans les médias: http://www.imio.be/presentation/dans-les-medias
.. _Liens: http://www.imio.be/support/documentation/link
.. _Nos atouts: http://www.imio.be/presentation/nos-atouts
.. _Liens: http://www.imio.be/support/documentation/liens
.. _Gestion électronique de documents: http://www.imio.be/produits/gestion-electronique-de-documents
.. _Gestion des activités extra-scolaires: http://www.imio.be/produits/gestion-des-activites-extra-scolaires
.. _Aller au contenu.: http://www.imio.be/support/documentation/manual/gestion-de-courriers/referencemanual-all-pages#content
.. _Contact: http://www.imio.be/contact
.. _Tutoriels vidéo: http://www.imio.be/support/documentation/tutoriels-video
.. _Services: /imio/imio/services
.. _Produits: http://www.imio.be/produits
.. _Conseil d'administration: http://www.imio.be/presentation/conseil-dadministration
.. _Demande d'assistance (Trac): http://www.imio.be/support/demande-dassistance-trac
.. _Offre All in One: http://www.imio.be/services/all-in-one
.. _Comité de gestion: http://www.imio.be/presentation/comite-de-gestion
.. _Processus et simplification administrative : http://www.imio.be/produits/processus-et-simplification-administrative
.. _Site Internet: http://www.imio.be/produits/site-internet
.. _Contactez-nous: http://www.imio.be/contact/contact
.. _FAQs: http://www.imio.be/support/documentation/faq
.. _Voir: http://www.imio.be/support/documentation/manual/gestion-de-courriers/
.. _Comment adhérer: http://www.imio.be/presentation/adherer
.. _Gestion des délibérations: http://www.imio.be/produits/gestion-des-deliberations
.. _Gestion des utilisateurs et groupes: http://www.imio.be/support/documentation/tutoriels/gerer-les-utilisateurs-les-roles-les-permissions-et-le-workflow/gestion-des-utilisateurs-et-groupes
.. _Solutions: /imio/imio/solutions
.. _Emplois et compétences: http://www.imio.be/produits/emplois-et-competences
.. _Accueil: http://www.imio.be
.. _gestion de ses services: http://www.imio.be/support/documentation/manual/gestion-de-courriers/configuration-de-loutil-gestion-du-courrier/gestion-de-ses-services
.. _Tableau de bord: http://www.imio.be/dashboard
.. _Fichiers: http://www.imio.be/support/documentation/fichiers
.. _Se déconnecter: http://www.imio.be/logout
.. _Références erreurs: http://www.imio.be/support/documentation/error
.. _Comment configurer la génération automatique des groupes plone via contact: http://www.imio.be/support/documentation/how-to/comment-configurer-la-generation-automatique-des-groupes-plone-via-contact-1
.. _Glossaires de définitions: http://www.imio.be/support/documentation/glossary
.. _Configuration du site: http://www.imio.be/@@overview-controlpanel
.. _Préférences: http://www.imio.be/@@personal-preferences
.. _Tutoriels: http://www.imio.be/support/documentation/tutoriels
.. _Forums: http://www.imio.be/support/forums
.. _Support: http://www.imio.be/support
.. _http://json-schema.org: http://json-schema.org
.. _Références d'erreur: http://www.imio.be/support/documentation/references-derreur
.. _Conseil, audit et processus: http://www.imio.be/solutions/conseil-audit
.. _books: http://www.imio.be/support/documentation/books
.. _Contact: /imio/imio/contact
.. _Vidéos: http://www.imio.be/support/documentation/videos
.. _Annuler: http://www.imio.be/undo_form
.. _ mutualisation: http://www.imio.be/solutions/logiciels-libres
.. _Règles: http://www.imio.be/support/documentation/manual/gestion-de-courriers/@@manage-content-rules
.. _Aller à la navigation: http://www.imio.be/support/documentation/manual/gestion-de-courriers/referencemanual-all-pages#portal-globalnav
.. _Admin: http://www.imio.be/admin
.. _Modifier: http://www.imio.be/support/documentation/manual/gestion-de-courriers/edit
.. _Partage: http://www.imio.be/support/documentation/manual/gestion-de-courriers/@@sharing
.. _Support: /imio/imio/support
.. _Centrale d'achat: http://www.imio.be/solutions/centrale-dachat
.. _Documentation: http://www.imio.be/support/documentation
.. _Présentation: http://www.imio.be/presentation
.. _Syndication: http://www.imio.be/support/documentation/manual/gestion-de-courriers/synPropertiesForm
.. _Solutions: http://www.imio.be/solutions
.. _Gestion de projet (PST): http://www.imio.be/produits/gestion-de-projet
.. _Services: http://www.imio.be/services
.. _Gestion des services techniques: http://www.imio.be/produits/gestion-des-services-techniques
.. _L'équipe: http://www.imio.be/contact/lequipe
.. _Présentation: http://www.imio.be/presentation/presentation
.. _Recherche avancée…: http://www.imio.be/search_form
.. _image: http://www.imio.be/support/documentation/image


