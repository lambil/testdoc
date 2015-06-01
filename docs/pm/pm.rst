
Application de gestion des organes délibératoires (version 3.3)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Ce manuel explique le fonctionnement général du produit
"PloneMeeting", son utilisation et sa configuration. Les illustrations
proposées se rapportent à une configuration par défaut et ne sont pas
exhaustives. Les éléments affichés dans les écrans sont renseignés à
titre d'exemple. Il est possible de paramétrer en profondeur
l'application à travers l'interface d'administration prévue à cet
effet et d'adapter si besoin les workflows proposés par défaut.



1. Description fonctionnelle
============================

En quoi consiste l'application ?

Le produit "PloneMeeting" permet à une institution de gérer ses
organes délibératoires à travers la gestion :


+ de types de séances délibératoires avec chacune leurs
  caractéristiques
+ de points, qui sont proposés pour un ordre du jour d'une séance,
  avec leurs annexes et avis
+ d'ordres du jour qui incluent des points créés par des utilisateurs
  ainsi que des points récurrents
+ de décisions qui sont prises lors du déroulement de la séance et
  faisant suite si nécessaire à des votes
+ de procès-verbaux qui contiennent les délibérations




L'outil permet donc par exemple de gérer pour une commune le collège
et le conseil communal, pour un CPAS le bureau permanent et le conseil
d'action sociale, pour la région wallonne ou bruxelloise les séances
du gouvernement, pour n'importe quel organisme ou société le conseil
d'administration, etc.

Le principe général est le suivant :


+ un membre d'un service crée un point qui devra être discuté lors
  d'une séance prochaine. Il y indique une description et déjà
  éventuellement une proposition de délibération. Il peut également y
  inclure des annexes et choisir de demander un avis sur le point à
  d'autres services. Lorsque son point est rédigé, il le propose (pour
  une séance précise si les séances ont déjà été définies).
+ le chef de ce service peut également créer des points et les
  proposer mais aussi valider les points proposés par les membres de son
  service.
+ la personne (dénommée ici secrétaire) qui s'occupe de la gestion de
  la séance peut créer un ordre du jour et y rajouter les points qui ont
  été validés . Il organise le contenu de la séance avec ses différents
  points et peut modifier les propositions de délibérations. Il peut
  générer, dans différents formats, un document présentant les points de
  la séance ainsi que leurs annexes. Ce document pourra servir de
  support de travail lors de la séance.
+ pendant ou après la séance, le secrétaire modifie les délibérations
  des points discutés . Il peut y intégrer des points et/ou des
  documents additionnels. Lorsque les délibérations sont finalisées, il
  peut à nouveau produire un document contenant le procès-verbal de la
  séance. Il est possible pour chaque point d'indiquer une décision afin
  que les différents services puissent accéder à cette décision. Après
  validation du PV lors de la séance suivante, celui-ci pourra être
  clôturé.



Un outil complémentaire, en cours de développement, permettra de gérer
les tâches faisant suite aux décisions.




2. Caractéristiques de l'application
====================================

Description des fonctionnalités générales



2.1. Organisation en groupes
============================




L'outil est organisé suivant des groupes.

La notion de groupe est utilisée pour permettre de gérer les points
suivant l'organisation structurelle.
Par exemple dans une commune le groupe correspondra à un service
tandis qu'au gouvernement wallon le groupe correspondra à un cabinet
ministériel.

A chaque groupe correspondent des personnes qui vont pouvoir créer et
gérer des points d'une séance.
Les personnes du groupe ne vont pas toutes avoir le même rôle :
certaines peuvent créer des points, d'autres les valider, donner un
avis ou alors seulement les consulter.

Les différents rôles, que peuvent avoir les utilisateurs, sont
présentés au point suivant.





2.2. Rôles prédéfinis
=====================

Présentation des rôles définis dans l'application

A travers l'explication fonctionnelle, différents profils
d'utilisation ont été présentés. Ces profils sont appelés rôles.
Un rôle reprend en fait un ensemble d'actions réalisables par un
utilisateur. A un rôle sont associés des permissions (lecture,
écriture, ajout, ...). Par exemple, seul le rôle secrétaire peut créer
un ordre du jour.
Un ou plusieurs rôles peuvent être donnés à un ou plusieurs
utilisateurs qui reçoivent dès lors les permissions correspondantes.



Les rôles suivants sont présents dans l'application :


+ rédacteur de point du groupe (MeetingMember) : qui peut créer un
  point et le modifier
+ pré-validateur d'un point du groupe (MeetingPreReviewer) : qui peut
  pré-valider les points du groupe afin de les proposer à un validateur
  final. Ce rôle de pré-validateur est optionnel est peut être activé ou
  désactivé dans la configuration de la séance
+ validateur d'un point du groupe (MeetingReviewer) : qui peut valider
  les points du groupe afin de les proposer pour un ordre du jour
+ lecteur d'un point du groupe (MeetingObserverLocal) : qui peut
  seulement visualiser les points du groupe
+ émetteur d'avis pour un groupe : qui peut donner un avis sur un
  point au nom du groupe
+ super observateurs : qui peut voir tous les points et séances
  lorsque ceux-ci sont dans des états définis dans la configuration
  ("`Section avis et accès`_")
+ secrétaire de séance (MeetingManager) : qui peut gérer les points à
  partir du moment où ils sont validés (proposés à la séance), les
  ordres du jour et les PV




Si un utilisateur doit pouvoir créer des points et donner un avis au
nom du groupe, il suffira de lui donner les rôles "rédacteur de point
du groupe" et "émetteur d'avis du groupe".
Dans l'application, les rôles sont donnés à des utilisateurs en
plaçant ces utilisateurs dans des groupes Plone spécifiques (`voir les
explications sur la configuration`_).



Il est possible, pour l'administrateur de l'application, d'adapter les
permissions associées à chaque rôle en modifiant les workflows du
produit. Un workflow constitue l'ensemble des étapes de traitement
d'un élément . Ces étapes sont appelées "état" et le fait de passer
d'un état à un autre est appelé une "transition ".
Par exemple, le début du workflow par défaut d'un point pour l'ordre
du jour est le suivant :



état "en création" ===========================> état "proposé"
===========================>

transition "proposer" transition "valider"



On définit pour chaque état et chaque transition des permissions
données à certains rôles.

Par exemple pour l'état "en création", on définit que seul le créateur
et le validateur peuvent voir et modifier le point. Pour la transition
"proposer", on définit que seul le créateur et le validateur peuvent
l'effectuer pour faire passer le point à l'état "proposé". Dans l'état
"proposé", on définit que le créateur ne peut plus modifier (mais peut
toujours voir) et que le validateur peut modifier et valider le point,
etc...





2.3. Interface générale
=======================

Comment se présente l'outil ?

Une fois l'utilisateur connecté, l'interface affichée (par défaut) se
présente comme suit :




Un série d'onglet (dans la partie supérieure) permet de naviguer parmi
les différents types de séances disponibles : collège communal,
conseil communal, ... En effet, il est possible de paramétrer
plusieurs types de séance de façons différentes mais de les utiliser
en même temps! Ceci permettra par exemple de transférer des points
d'un type de séance à un autre.

Une zone de recherche "full-text" apparaît en haut à droite et permet
d'effectuer une recherche à travers tous les éléments encodés et que
le membre en cours peut consulter. Cette recherche est insensible aux
accents et permet d'encoder un début de mot, donc par exemple une
recherche sur "budget" ramènera les points contenant également le
terme "budgétaire". Cette recherche globale ne tient pas compte du
type de séance (collège comunal ou conseil communal), pour se faire,
`une recherche avancée est disponible`_.

La boîte de menu "Gestion" regroupe différentes actions concernant:


+ un `accès à la recherche avancée `_ via l'icône et un accès à la
  page d'accueil de la configuration de séance en cours via l'icône
+ les points: les éléments affichés dépendent de l'utilisateur
  connecté. Si l'utilisateur peut créer des points, une icône (créer un
  point) apparaît à droite de l'intitulé " Points ". Si des modèles de
  points sont définis dans la configuration, l'icône apparaît. Au clic
  sur celle-ci, un écran affichera les modèles disponibles pour
  l'utilisateur (pour plus d'infos à ce sujet, voir bas de `cette
  page`_). Sous l'intitulé, différentes recherches permettent de
  retrouver les points selon divers critères : "mes points" (les points
  créés par l'utilisateur), "tous les points" (tous les points que
  l'utilisateur peut voir, en général tous les points de son service),
  "points en copie" (les points pour lesquels l'utilisateur est mis en
  copie), etc.
+ les séances: prévues à une date prochaine mais qui n'ont pas encore
  eu lieu. Si l'utilisateur a le rôle global de gestionnaire de séance
  (MeetingManager), une icône (créer une séance) apparaît à droite de
  l'intitulé " Séances ".
+ les décisions: les séances qui ont eu lieu et pour lesquelles un
  procès verbal est en cours de rédaction ou a été finalisé.



Des actions propres à l'utilisateur se trouvent à droite de l'intitulé
de la boîte de menu "Gestion":


+ l'icône "maison" permet de retourner sur la page d'accueil du type
  de séance en cours
+ l'icône "loupe" affiche une recherche avancée permettant de
  rechercher des points dans l'application



La boîte "à faire" montre à l'utilisateur les actions qu'il doit faire
en fonction de son rôle: les *avis à donner*, les *points à valider*,
les *points pour lesquels il est en copie*, ... Toutes ces recherches
sont configurables et apparaîtront en fonction des rôles de
l'utilisateur courant. En outre, il est possible de configurer
d'autres recherches qui apparaîtront dans cette boîte.

L'icône permet de cacher un maximum d'informations sur un point afin
de faciliter la navigation. Les informations affichées sous le titre
du point sont alors cachées et le tableau n'affiche que les
informations nécessaires (titre du point) dans la colonne "Titre".





2.4. Écrans de gestion d'un point
=================================

Les écrans de création et de gestion d'un point



2.4.1. Création d'un point
==========================




Lorsqu'un utilisateur choisit d'ajouter un point, il peut soit ajouter
un point vierge en cliquant sur l'icône à droite de l'intitulé "
Points " ou ajouter un point basé sur un modèle en cliquant sur
l'icône . Si l'utilisateur choisit de créer un point sur base d'un
modèle, l'écran suivant est affiché et lui permet de sélectionner le
modèle à utiliser :



Il est possible d'organiser les modèles par dossiers et sous-dossiers,
ainsi que de les rendre disponibles à certains groupes et pas
d'autres. *

Lorsque le modèle est sélectionné, le point est créé et, par défaut,
les champs suivants sont affichés (dont certains pré-remplis puisque
le point est créé sur base d'un modèle) :




Les champs suivants sont proposés :


+ Objet (anciennement "Titre") : intitulé du point tel qu'il
  apparaîtra dans l'application. Ce dernier doit être clair et concis
+ Description : zone texte riche (1) contenant une description
  complète du point proposé. Cette zone est affichée lorsque l'on
  visualise le point ou l'ordre du jour
+ Description détaillée : cette zone texte riche (1) est optionnelle
  (2). Elle est utilisée lorsque la zone "Description dans l'ordre du
  jour" est destinée à contenir une brève présentation du point. La
  "Description détaillée" contiendra elle une version plus complète de
  la description
+ Groupe proposant : ce champ obligatoire permettra à l'utilisateur en
  cours de définir pour quel groupe (service) il souhaite encoder le
  point (utile dans le cas où un utilisateur appartient à plusieurs
  groupes). Par défaut, tous les membres de ce groupe auront accès au
  point (en lecture) et en fonction de leurs permissions, pourront
  également le modifier, le supprimer, le proposer au validateur, ...
+ Groupe(s) associé(s) (2) : ce champ permet de donner une
  informations sur les autres groupes associés au point
+ Catégorie (2) : ce champ optionnel affiché sous forme de liste
  déroulante permet de lier une catégorie à un point (marché public,
  engagement de personnel, ...). Ces catégories peuvent être définies
  par service si nécessaire. Les points insérés dans une séance pourront
  être automatiquement trié sur base de cette catégorie
+ Classificateur (2) : cette fonctionnalité proche de la catégorie
  (voir champ "Catégorie ci-dessus") mais permet de par sa présentation
  de gérer des centaines voire des milliers de catégories (listing des
  catégories, recherche d'une catégorie sur base d'un mot clé, ...)
+ Émetteurs d'avis optionnels (2) : cette liste propose à
  l'utilisateur en cours de sélectionner des services auxquels un avis
  sur le point doit être demandé. Ces avis dits "optionnels" peuvent
  être complété par des avis demandés automatiquement en fonction de la
  configuration. Cette zone n'apparaît que si on a choisi d'utiliser la
  gestion des avis
+ Groupes en copie (2) : liste des services à sélectionner pour leur
  donner un accès en lecture au point. Cette zone n'apparaît que si on a
  choisi d'utiliser la gestion des points en copie
+ Des informations budgétaires sont liées (2) : si les informations
  budgétaires liées à un point doivent être mise en évidence, ce champ
  peut alors être utilisé. Lorsque la case est cochée, un champ texte
  supplémentaire apparaît pour encoder lesdites informations budgétaires
+ Séance souhaitée : si des séances futures ont déjà été encodées, il
  est possible de choisir une séance souhaitée dans laquelle ce point
  devrait être inclus. En choisissant "Pas de préférence", l'utilisateur
  spécifie que le gestionnaire de séance peut l'insérer dans la séance
  qu'il souhaite. Sélectionner une séance dans le futur signifie que le
  point ne pourra pas être présenté dans une séance avant cette date,
  mais le sera à partir de cette séance et pour toutes les séances
  suivantes
+ A envoyer vers (2) : si la fonctionnalité est activée dans la
  configuration, l'utilisateur pourra spécifier si ce point doit être
  envoyé vers un autre type de séance lorsqu'il aura été décidé. Cette
  fonctionnalité est utilisée pour passer des points de séances en
  séances (collège communal vers conseil communal, bureau permanent du
  CPAS vers Conseil de l'Action Sociale, ...)
+ Niveau de confidentialité (2) : cette zone permet de montrer quel
  est le niveau de confidentialité lié à ce point. Cette fonctionnalité
  permet de limiter l'accès à certains points et pourra être utilisée
  pour trier les points "par niveau de confidentialité" sur une séance
+ Ce point est une question orale (2) : case à cocher qui permet de
  spécifier si le point est de type "question orale". Cette notion
  pourra alors être utilisée lors de l'impression du point, de l'ordre
  du jour ou du procès-verbal de la séance
+ A l'initiative de ce point (2) : liste à choix multiples qui permet
  de sélectionner la ou les personne(s) réellement à l'initiative du
  point encodé. Ceci permet à un agent de spécifier qui est la personne
  à l'origine du point en cours
+ Motivation (2) : zone de texte riche (1) pouvant être utilisée
  conjointement avec la zone "Extrait du procès-verbal (Décision)" si on
  souhaite pouvoir encoder la délibération en 2 parties "Motivation" et
  "Décision"
+ Décision (anciennement "Extrait du Procès-verbal") : zone texte
  riche (1) contenant une proposition de délibération pour le point.
  Cette zone n'apparaît pas automatiquement pour tous les utilisateurs
  (dépendant du paramétrage de l'application). Elle sera utilisée pour
  établir le procès-verbal de la séance
+ Observations (2) : zone de texte riche (1) contenant des
  observations concernant le point. Au besoin, cette zone peut n'être
  accessible que par certains rôles (gestionnaire de séances, validateur
  de points, ...)
+ Assemblée spécifique liée à ce point (2) : au cours de la séance, si
  l'assemblée présente change pour ce point (un membre doit sortir par
  exemple), il est possible de définir l'assemblée qui devra être prise
  en compte lors de l'impression de la délibération de ce point
+ Signatures spécifiques liées à ce point (2) : au cours de la séance,
  si un des signataires désignés pour la séance est absent (par exemple
  si le point le concerne), un autre signataire sera désigné et son nom
  apparaîtra alors ici. Cette zone pourra alors être utilisée lors de
  l'impression de la délibération liée à ce point



Quelques champs optionnels supplémentaires non exposés sur l'image ci-
dessus :
~~~~~~~~


+ Catégorie (2) : par défaut, l'élément catégorisant un point est son
  groupe proposant (point du service untel). Si çà ne suffit pas, des
  catégories peuvent être ajoutées (par exemple "marché public",
  "engagement de personnel", ...). Affichées sous forme d'une liste
  déroulante à choix unique, ces catégories peuvent être définies par
  services de sorte que chaque service puissent utiliser ses propres
  catégories. En outre, cette catégorie pourra être utilisée pour trier
  les points sur la séance
+ Marqueur (2) : les marqueurs sont des éléments permettant de
  catégoriser les points. Il s'agit à nouveau de la notion de catégorie
  mais dans un champ de texte libre
+ Urgence : ce champ permet à un groupe proposant de demander
  l'urgence sur un point. Cet indicateur pourra être utilisé par exemple
  pour demander qu'un point soit inséré dans une séance en urgence *
+ A évoquer en séance : ce champ booléen (oui ou non) permet de gérer
  le cas o certains point ne sont pas discutés en séance
+ A transmettre à la tutelle? : champ booléen (oui ou non) permettant
  d'indiquer que le point doit être envoyé à la tutelle *
+ Complétude : ce champ indicatif permet à un niveau de validation ou
  à un gestionnaire de séance de formaliser l'analyse de complétude d'un
  dossier. La complétude peut être évaluée, le point peut être marqué
  complet, incomplet, ... une historisation est gardée et des
  commentaires peuvent être laissés *
+ Point signé? : ce champ sert d'indicateur pour les gestionnaires de
  séances pour savoir si la délibération d'un point a été signée
  manuellement
+ Pris en charge par : ce champ permet à n'importe quel intervenant
  sur un point qui à la main sur le point (qui peut donc le modifier) de
  spécifier qu'il a pris ce point en charge. Ceci est utile dans les
  organisations où plusieurs personnes ont le même rôles pour éviter que
  deux personnes ne travaillent sur le même dossier sans le savoir par
  exemple *


(1) Les boutons de l'éditeur lié aux zones de textes riches peuvent
être configurés de sorte que certaines fonctionnalités ne soient pas
disponibles aux utilisateurs (changer la taille du texte, changer la
couleur du texte, ...). Seuls les boutons utiles apparaissent, ce qui
permettra de garder une cohérence de point en point lors de la
génération des différents documents
(2) Les champs optionnels peuvent être activés ou désactivés dans la
configuration en fonction du besoin
* nouveau dans la version 3.3



2.4.2. Visualisation d'un point existant
========================================




Une fois un point créé, il est possible de le visualiser.
Un écran semblable est alors affiché.



Les onglets supérieurs permettent d'effectuer des actions
supplémentaires sur le point :


+ Modifier : pour accéder au formulaire de modification du point
+ Annexes : pour associer des documents annexes au point
+ Annexes (après décision) : pour associer des documents annexes
  faisant suite à la délibération sur le point



La zone "État" se trouvant en haut à droite indique l'état actuel du
point. Dans l'exemple affiché : "En création". Si l'option est activée
(par défaut), une couleur spécifique sera utilisée pour chaque état ce
qui permettra de rapidement identifier l'état d'un point en lisant le
titre (qui sera colorisé en fonction de l'état de l'élément)

Cet état dépend du workflow associé au type de séance. Les états
peuvent donc être différents suivant que l'utilisateur se trouve dans
le collège communal, le conseil communal ou tout autre type de séance.

Les icônes en haut à droite permettent également d'effectuer certaines
actions sur le point. Le fait de laisser le pointeur de la souris sur
l'icône affiche le nom de l'action associée.

Par exemple, dans le cas affiché :


+ Imprimer le point dans un format bureautique suivant le modèle
  proposé : "Projet délibération" au format OpenOffice ou Word dans
  l'exemple



Plusieurs formats bureautiques peuvent être proposés à l'utilisateur
(suivant `la configuration des canevas de documents`_) :


+ génération au format PDF
+ génération au format ODT (OpenOffice)
+ génération au format DOC (Microsoft Word)
+ génération au format RTF (Rich Text Format)



La génération en document bureautique est possible pour les points,
les ordres du jour et les procès-verbaux.

Au bas du point se trouve un résumé des annexes ajoutées et des avis à
rendre/rendus sur le point. Dans l'exemple ci-dessus, il reste 1 avis
à donner.

Les boutons affichés en bas de la page permettent d'effectuer
certaines actions sur le point : dupliquer le point (en faire une
copie pour repartir sur une base lors de la création d'un nouveau
point) ou supprimer le point par exemple. Toutes ces actions étant
fonction de l'utilisateur en cours et de ses permissions.




Accès à l'historique d'un point
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

C'est dans l'historique du point (accessible via le lien "Historique"
affiché sous le titre d'un point ou depuis les tableaux de bord
affichant des points) qu'on peut retrouver les informations liées aux
changements d'états du point et aux commentaires qui peuvent être
ajoutés lors de ces changements d'états :





2.4.3. Ajout d'annexes
======================



Les utilisateurs pouvant modifier le point peuvent y adjoindre des
annexes en cliquant sur l'onglet "Annexes" ou "Annexes (après
décision)".

L'écran suivant est alors affiché :



Le cadre inférieur affiche des informations sur les annexes déjà liées
au point.

En cliquant sur le titre d'une annexe, il est possible de la
visualiser. Si l'utilisateur en a la permission (définie dans
l'application), il peut également supprimer une annexe existante.

Certaines fonctionnalités liées aux annexes peuvent être activées dans
la configuration comme la possibilité de rendre des annexes
confidentielles * ou de spécifier qu'une annexe doit être imprimée
dans un document * (une délibération ou un Ordre du jour par exemple).
La fonctionnalité d'impression des annexes permet d'imprimer
automatiquement n'importe quel type d'annexe dans un document
bureautique (PDF par exemple).

Le cadre supérieur permet d'ajouter une annexe.

Il est nécessaire de choisir le type d'annexe, d'indiquer un titre
représentatif et de sélectionner un fichier. Si un seul type d'annexe
est disponible, la liste déroulante permettant de choisir un type
d'annexe n'apparaîtra pas. Un "titre par défaut" peut être défini par
type d'annexe dans la configuration afin d'harmoniser les titres qui
seront encodés par les différents utilisateurs.

Dans le cadre orange est présenté une fonctionnalité de l'application
: " l'invalidation des avis ". En effet, si un groupe a donné un avis
sur un point, on peut spécifier `dans la configuration`_ que lors de
la modification du point (ajout d'une annexe, édition de la
délibération, ...) tous les avis soient invalidés.

Les "Annexes (à la décision)" permettent de gérer l'après décision en
liant au point des annexes produites suite à la décision.

* nouveau dans la version 3.3



2.4.4. Gestion des avis
=======================



Si des avis ont été demandés manuellement par les créateurs du point
ou automatiquement par l'application, les utilisateurs sélectionnés
comme "Emetteurs d'avis" dans les groupes auxquels on a demandé un
avis pourront le rendre. Par défaut, un groupe ne peut rendre son avis
sur un point que si cet avis lui a été demandé, il est toutefois
possible de définir dans `la configuration des avis`_ certains groupes
qui pourront rendre leur avis même si celui-ci n'a pas été demandé.

La gestion des avis est accessible notamment sur un point, via
l'onglet "Voir", dans la zone "Avis" :




Les icônes affichées représentent le type d'avis, ici par exemple
"Positif", "Commenté" et "Non rendu". En cliquant sur une de ces
icônes, l'avis peut être visualisé sous forme d'info-bulle. Par
défaut, si le point est dans l'état proposé ou validé , l'avis peut
encore être supprimé ou modifié (les états dans lesquels un avis peut
être donné, modifié ou supprimé sont `définis dans la configuration`_)
par les personnes ayant donné l'avis :


Un avis peut être rendu dans certains états du point et s'il a été
demandé au service. Si des avis sont demandés mais pas encore rendus,
il apparaîtront au clic sur l'icône . La liste des avis non rendus
ainsi que certaines informations (comme par exemple le fait que l'avis
peut être rendu ou non, des informations sur le `délai pour rendre
l'avis`_, ...) sont affichées :



Lorsque l'utilisateur en cours peut ajouter un avis, une petite icône
apparaît ...



... ce qui permet d'accéder à l'écran suivant :



Si un utilisateur peut modifier un avis donné, le même écran est
affiché.

Les champs suivants sont proposés :


+ Groupe : groupe pour lequel l'utilisateur émet un avis. Si
  l'utilisateur peut donner son avis au nom de différents groupes et que
  l'avis de ces différents groupes est demandé
+ Type d'avis : choix entre les types d'avis configurés (par exemple,
  "positif", "commenté", "négatif" ou "néant")
+ Cacher l'avis pendant sa rédaction : cette case à cocher permet de
  montrer que l'avis est en cours de rédaction par le service émetteur.
  Pour plus d'infos, consultez le message d'aide renseigné sur l'image
  ci-dessus
+ Motivation : contiendra l'avis officiel remis sur le point
+ Observations : zone optionnelle permettant d'ajouter un commentaire
+ Référence : une référence peut être renseignée pour un avis si
  nécessaire et pourra être reprise dans l'un ou l'autre document le cas
  échéant




Une fois encodé, il est possible pour le créateur de l'avis ainsi que
pour les personnes ayant un accès en lecture à l'avis de le consulter
complètement en passant par le lien "Accéder à l'avis en détail", en
effet, par défaut, seul un extrait de l'avis est affiché :

*Extrait :*



*Avis en détail :*





2.4.5. Gestion des avis : ajout d'annexes
=========================================



Depuis la version 3.2 de PloneMeeting, il est possible d'adjoindre des
annexes à un avis.

Pour cela, une fois l'avis ajouté, dans les actions de l'avis apparaît
l'icône .



Au clic sur l'icône, un formulaire d'ajout d'annexes apparaît. Les
types d'annexes sont paramétrables dans la configuration.



Les annexes déjà ajoutées à l'avis auparavant sont également listées.
Cette fonctionnalité est similaire à l'ajout d'annexes sur un point.



2.4.6. Gestion des avis : avis avec délai
=========================================



Il est possible de `définir dans la configuration des délais`_ qui
devront être respectés pour rendre un avis. Le délai démarre à partir
du moment où l'avis est demandé et que le point est visible par le
service auquel l'avis est demandé.

Si des avis avec délai sont configurés, ils apparaîtront comme ceci
sur le formulaire d'édition d'un point :



Une fois sélectionné, un avis avec délai apparaîtra dans la liste des
avis avec des informations supplémentaires (délai pour rendre l'avis
et un libellé supplémentaire d'aide concernant l'avis, ici "Incidence
financière >= 22.000€"), si l'avis peut déjà être rendu, la date
limite pour rendre l'avis est également affichée :



Lorsqu'un avis avec délai n'a pas pu être rendu dans le délai imparti,
il ne sera plus possible de le rendre et un message clair sera affiché
:



La manière de rendre l'avis est identique à un avis "normal" sans
délai.



2.4.7. Tableau récapitulatif affichant des points
=================================================



Via le boîte d'informations (portlet) située à gauche et intitulée
"Gestion", dans la partie "Points", il est possible d'afficher des
points suivant différents critères.

L'écran suivant est un exemple de tableau récapitulatif utilisé pour
afficher une liste de points, ici sont affichés tous les points
auxquels l'utilisateur courant a accès.




Parmi les colonnes affichées, seule la colonne "Objet" est
obligatoirement affichée. Au niveau de cette première colonne, un
filtre de recherche est disponible. Il suffit d'encoder un terme de
recherche, de cliquer sur l'icône et le tableau est automatiquement
filtré en fonction du terme entré. La recherche est faite à travers
tous les champs du point (recherche "full-text"), donc l'objet du
point, sa description, sa décision, ... De plus, depuis la version
3.1+, la recherche n'est plus sensible aux accents et un début de mot
peut être considéré : par exemple une recherche sur "budget" ramènera
aussi des points contenant le mot "budgétaire".

Les "Actions", toujours affichées dans la dernière colonne montre les
actions que l'utilisateur en cours peut effectuer sur le point.

Les autres colonnes sont optionnelles. Toutes les colonnes
optionnelles ne sont pas montrées ici, mais en passant par la
configuration, il est possible de montrer les colonnes : "Créateur",
"Créé le", "Modifié le", "Etat", "Catégorie (ou groupe proposant)",
"Groupe proposant", "Acronyme du groupe proposant", "Groupe(s)
associé(s)", "Acronymes des groupes associés", "Annexes", "Annexes (à
la décision)", "Avis", "Niveau de confidentialité", "Informations
budgétaires", "Actions", "Séance", "Séance souhaitée", "Point signé?"
et "A évoquer en séance?"

Suivant l'état du point, le titre peut être coloré différemment.

Le fait de laisser le pointeur de la souris sur une icône affiche le
nom de l'action associée.

Par exemple :


+ Corriger : remet le point dans l'état du workflow précédent. Par
  exemple, un point "validé" serait remis dans l'état "proposé"
+ Éditer : pour accéder au formulaire de modification du point
+ Dupliquer : permet de "copier/coller" un point pour repartir sur une
  certaine base au cas où un nouveau point ressemble fortement à un
  point existant
+ Dupliquer et garder le lien : même chose que "Dupliquer" mais garde
  un lien entre les points afin de pouvoir passer d'un point à l'autre
  facilement
+ Supprimer : permet de supprimer définitivement un point de
  l'application
+ Historique du point : permet d'accéder à l'historique du point
  (changements d'état et commentaires)
+ Proposer : permet pour un créateur de point d'envoyer celui-ci à un
  validateur
+ Valider : permet pour les validateurs de "valider" le point
+ Renvoyer au groupe proposant pour correction : permet de renvoyer un
  point présenté dans une séance au groupe proposant afin que ce dernier
  y apporte des corrections mais sans enlever le point de la séance
+ Retirer de la séance : permet de retirer un point présenté d'une
  séance, il sera remis dans l'état "validé" (proposé à la séance)
+ ...


Diverses icônes peuvent également être affichées devant le titre du
point, cela donne une information supplémentaire sur certains aspects,
par exemple:


+ Accepté avec modification : par défaut, un point "Accepté" apparaît
  avec un titre de couleur verte, ici, un point "Accepté avec
  modifications" apparaît également en vert et cette icône permet de le
  différencier
+ Va être envoyé vers ... : permet de savoir que le point va être
  envoyé une fois qu'il aura été accepté vers une autre séance (comme
  par exemple un Point Collège communal envoyé au Conseil communal)
+ Ce point repasse à nouveau par cette étape dans le workflow : permet
  de savoir qu'un point dans un état donné (par exemple "proposé" à un
  validateur) a déjà été dans cet état auparavant
+ Ce point redescend le workflow : permet de savoir qu'un point est
  dans un état parce qu'il redescend le workflow. En effet, normalement
  un point "monte" un workflow, par exemple via les états en
  création/proposé/validé. Si un point est dans l'état "proposé" parce
  qu'il redescend de l'état "validé", alors cette icône est affichée
+ ...




2.4.8. Evolution du point dans l'application
============================================



Le point évoluera dans l'application en fonction de son `workflow`_.

Différents types de workflows sont proposés (comme un workflow pour le
`Collège communal ou le Conseil communal`_) et peuvent même être
configurés sur mesure, cependant, certaines transitions/états sont
considérés comme clés dans le fonctionnement de l'application :


+ l'état "en création" aussi bien pour les points que les séances
  représente l'état initial de l'élément
+ l'état "validé" est l'état qui représente le point pouvant être
  présentés dans une séance
+ l'état "présent" est un état qui représente un point franchement
  inséré dans une séance et donc lié à celle-ci
+ les états "décidés" sur les points comme "accepté", "refusé",
  "reporté", ...
+ l'état "clôturé" pour la séance qui ne permet plus aucune
  modification par qui que ce soit (sauf l'administrateur) sur les
  séances dans cet état et tous ses points liés



En outre, peu importe le workflow utilisé, il est possible d'`activer
lors de certaines transitions`_ (passage d'un état à un autre) que
celles-ci doivent être confirmées. Un popup apparaît alors et permet à
l'utilisateur d'annuler la transition ou d'effectuer la transition en
laissant un commentaire. Par exemple, en activant cette confirmation
sur la transition "reporter" d'un point, voici l'écran qui apparaît à
l'utilisateur (gestionnaire de séances) :





2.4.9. Interventions de plusieurs utilisateurs sur le même point
================================================================





Fonctionnalité de verrouillage
------------------------------

Dans l'application, le workflow (cheminement du point dans
l'application) permettra à plusieurs profils d'utilisateurs
d'intervenir successivement sur le point. Cependant, il se peut que
dans un groupe, plusieurs utilisateurs aient le même profil et
veuillent par exemple collaborer sur le même point (s'il s'agit de
créateurs de points) ou modifier un point à valider s'il s'agit de
validateurs. Dans tous les cas, si un utilisateur est en train de
travailler sur un point, ce dernier est "verrouillé", ce qui évite à
des utilisateurs de se "marcher sur les pieds" et de modifier le même
point ce qui pourrait provoquer des pertes de données.

Un écran de ce type est affiché à un utilisateur pouvant éditer un
point qui est déjà en cours d'édition par un autre utilisateur :



Ici par exemple, le nouvel utilisateur qui arrive sur le point est
prévenu qu'un utilisateur est déjà en train de modifier le point. Il
pourra par exemple contacter ledit utilisateur. S'il en a le droit (ce
qui est le cas ici), le nouvel utilisateur peut "Déverrouiller" le
document et le modifier. On peut aussi définir que l'utilisateur qui
arrive sur un point en cours de modification ne puisse pas le
déverrouiller.

Cette fonctionnalité de verrouillage est également activée sur les
éléments de type "Avis", si un émetteur d'avis est en train d'éditer
un avis, l'avis ne peut pas être éditer par un autre utilisateur.


Fonctionnalité de prise en charge d'un point
--------------------------------------------

Cette nouvelle fonctionnalité permet de formaliser le fait qu'un
utilisateur déclare avoir pris en charge un dossier. Si le champ est
activé sur les points, une zone spécifique apparaît dans laquelle un
utilisateur qui a la main sur le point (qui peut le modifier) peut
déclarer qu'il prend en charge le point. Dès qu'il perd la main sur le
point (par exemple un validateur a validé un point et ne peut donc
plus le modifier), la prise en charge est enlevée automatiquement.



L'information est également affichée dans les tableaux de bords afin
d'identifier rapidement un point pris en charge par une autre personne
(icône ) ou que l'utilisateur courant a pris en charge (icône ).



* nouveau dans la version 3.3



2.5. Écrans de gestion d'une séance
===================================

Les écrans de création et de gestion d'une séance



2.5.1. Création d'une séance
============================



Lorsque l'utilisateur qui en a la permission (rôle "Gestionnaire de
séances" - MeetingManager) choisit d'ajouter une séance, le formulaire
suivant est affiché :





La seule zone obligatoire et non optionnelle dans la configuration est
la date et heure de la séance qui identifie une séance. En effet la
date est indicative pour différencier les séances. Mais elle est aussi
utilisée comme garde-fou pour éviter de clôturer une séance qui n'est
pas encore passée par exemple. Deux séances différentes ne pourront
avoir la même date et heure de la séance

Les autres zones optionnelles peuvent être sélectionnées dans la
configuration et apparaître alors sur le formulaire d'ajout ou de
modification d'une séance :


+ le lieu ou se déroulera la séance. Plusieurs valeurs peuvent être
  définies dans la configuration, la valeur "Autre" permettant d'encoder
  une autre valeur au cas où
+ la date et heure effective de début permet d'encoder la date précise
  à laquelle a commencé la séance
+ la date et heure effective de fin permet d'encoder la date précise à
  laquelle s'est terminé une séance
+ la date de fin de la première partie peut être utilisée si la séance
  est divisée en deux parties (séance publique et séance à huis clos par
  exemple)
+ la date d' échéance pour valider les points permet de définir avant
  quelle date un point doit être validé pour pouvoir être présenté dans
  la séance. Au cours de la gestion de la séance, si un point a été
  validé en retard, l'icône le montrera. Cependant, il sera quand même
  possible pour le gestionnaire de séance de présenter le point validé
  en retard dans la séance
+ la date d' échéance pour valider les points en retard permet de
  définir avant quelle date un point doit être validé pour pouvoir être
  présenté dans la séance comme point en retard (c'est-à-dire après que
  la séance ai été gelée et n'accepte théoriquement plus de points, si
  ce n'est les points "en retard" ou "en urgence"). De la même manière
  que pour un point normal validé en retard, l'icône sera affichée
  devant les points validés hors échéance
+ les champs signatures et assemblée (ainsi que 'Absents' et
  'Excusés') permettent d'encoder sous forme de texte libre quelles sont
  les signatures à utiliser lors de l'impression de la séance et quels
  sont les membres présents lors de la séance. Ces zones de texte libre
  `peuvent être remplacées`_ par des cases à cocher permettant de
  définir les présents, absents (non excusés), absents (excusés) et
  signataires . Ces listes de cases à cocher reposent sur des
  utilisateurs spécifiquement décrits dans l'application (`configuration
  des utilisateurs spéciaux`_)
+ la zone réunion préparatoire permet d'encoder la date et le lieu
  d'une éventuelle séance qui se passe avant la séance officielle et qui
  permet de préparer la séance finale
+ des observations pourront également être notées sur la séance. La
  zone observations pour la réunion préparatoire pourra être activée si
  une réunion préparatoire doit avoir lieu


Ces zones peuvent être modifiées par un gestionnaire de séance par la
suite. En effet, les absents, les heures de début et de fin par
exemple ne sont pas connues lors de la création de la séance





2.5.2. Visualisation d'une séance par un gestionnaire de séance
===============================================================



Pour un utilisateur ayant le rôle de "Gestionnaire de séance"
(MeetingManager), l'affichage est le suivant:



Le cadre supérieur " Points disponibles pour cette séance " affiche
les points qui peuvent être ajoutés (présentés) à la séance,
c'est-à-dire les points qui ont été validés.

Pour *présenter le point dans la séance* , il suffit de cliquer sur
l'icône .

Il est également possible de *présenter plusieurs points en même
temps* . Pour cela, il est nécessaire de sélectionner les points à
ajouter à la séance en les cochant/décochant dans la colonne la plus à
droite et ensuite de cliquer sur l'icône se trouvant en haut de cette
colonne.

Ici, si activée, la fonctionnalité de gestion de l' *échéance pour
valider un point* affichera l'icône devant le titre du point à
présenter pour montrer que le point a été validé après la date limite
de validation des points. Les gestionnaires de séances peuvent choisir
de présenter le point ou non.

Le cadre inférieur " Points présentés à cette séance " affiche les
points qui sont déjà inclus dans la séance.

Des *points récurrents* définis dans la configuration seront
automatiquement présentés dans la séance à la création de celle-ci.

Un point peut être retiré de la séance en cliquant sur l'icône .

De la même manière que pour présenter plusieurs points en une fois, il
est également possible via l'icône d'enlever plusieurs points de la
séance en une fois. Il faut au préalable sélectionner les points qu'on
souhaite enlever de la séance.

L'ordre des points affichés dans le tableau est pris en compte lors de
la génération des documents. Il est possible de changer cet ordre de
deux façons:


+ en cliquant sur les icônes et
+ en changeant directement la numérotation d'un point dans la colonne
  qui affiche les numéros de points



Pour la génération de la séance en format bureautique, il est possible
de sélectionner les points que l'on veut voir apparaître dans le
document.
Par défaut tous les points de la séance sont imprimés dans le
document, mais si nécessaire, il est possible de décocher des points
dans la dernière colonne. Pour générer le document, il suffit de
cliquer sur l'icône du format désiré en haut à droite (sous la ligne
de titre de la séance).

Dans la page de gestion de la séance, par défaut, seul le titre de
chaque point est affiché. Il est possible d'activer/désactiver
l'affichage de la description de chaque point en cliquant sur l'icône
se trouvant en haut à droite (dans la ligne de titre de la séance).
Les informations affichées au clic sur les lunettes est configurable
dans la partie "`Interface utilisateur`_" dans le champ "Champs des
points à Afficher/masquer lors de l'utilisation de l'icône 'Lunettes'"

Les liens sur les points peuvent être colorés soit suivant leur état,
soit suivant le fait qu'une modification a eu lieu dans le point
depuis la dernière visualisation du point. Ces fonctionnalités
supplémentaires doivent être activées dans la configuration (voir
`Colorisation des intitulés`_).

Lorsque les points nécessaires ont été présentés, le gestionnaire de
séance peut geler la séance afin de fixer l'ordre du jour et
distinguer par la suite des points qui seraient rajoutés en urgence.





2.5.3. Visualisation d'une séance par un créateur de point
==========================================================




Par défaut, les services ne voient que les points de leur service. Si
un utilisateur accède à une séance, il ne verra sur cette dernière que
les points auxquels il peut accéder :



Le point peut être visible par un utilisateur pour plusieurs raisons :


+ il fait partie du groupe proposant;
+ il fait partie d'un groupe qui a été mis en copie;
+ il a donné ou doit donner son avis sur le point;
+ il fait partie du groupe "super observateurs" ou "super observateurs
  (restreints)";
+ ...






2.5.4. Modification des points d'une séance
===========================================



Une fois inséré dans une séance, un "widget" de navigation entre
points apparaît sur la vue d'un point :



Cet outil permet aux Gestionnaires de séance (MeetingManager) de
passer facilement d'un point à l'autre ou même d'atteindre un point
spécifiquement en encodant son numéro.

Une fois que le point souhaité est atteint (en utilisant ce "widget"
ou en passant par la séance), il y a 2 moyens de modifier un point :


+ soit en passant par l'onglet "Modifier", l'ensemble des champs
  modifiables est alors affiché comme `lors de la création d'un point`_
+ soit en utilisant la fonctionnalité d'édition rapide d'une zone de
  texte riche (comme la zone Description ou Extrait du Procès-verbal),
  en cliquant sur l'icône à côté du nom de la zone à éditer, la zone se
  change en zone éditable très rapidement et des modifications peuvent
  être apportées :




Après avoir effectué les changements, un clic sur l'icône sauvegardera
les changements et remettra la zone en mode "visualisation". Si vous
souhaitez fermer la zone d'édition rapide sans enregistrer, cliquez
sur l'icône . En outre la fonctionnalité d'invalidation des avis est
utilisée ici : ` *si cette fonctionnalité est activée dans la
configuration*`_, lors de la modification d'une zone sur le point, les
avis sont invalidés car un changement a été apporté.




2.5.5. Ajout d'un point "en urgence"
====================================




Lorsque l'ordre du jour de la séance est finalisé, la séance peut être
"gelée" par le gestionnaire de séance. Elle ne peut alors
théoriquement plus recevoir de points, c'est pourquoi plus aucun point
n'apparaît dans la zone "Points disponibles pour cette séance". Malgré
tout, il arrive que des points complémentaires (appelés aussi "en
retard", "en urgence", "supplémentaire", ...) non prévus dans l'ordre
du jour initial doivent être ajoutés. L'application permet de rajouter
ces points à la séance et de les distinguer des points originellement
prévus à l'ordre du jour.

Les points complémentaires peuvent être créés comme vu précédemment
mais, pour être considérés comme des points en retard pour la séance,
il est nécessaire :


+ de choisir comme *séance souhaitée* la séance qui est gelée
+ que le point soit validé après le gel de la séance : pour simplifier
  la gestion des points en retard, cette condition a été supprimée *


Le point apparaîtra alors comme disponible pour cette séance, même si
celle ci est gelée. L'icône prévient que le point est considéré comme
un point "en retard".




Une fois que le point a été rajouté à la séance, il apparaît dans un
cadre spécifique destiné aux points complémentaires. Ceci permettra de
distinguer les points présentés de manière standard par rapport aux
points présentés en urgence.



Une fois que tous les points ont été rajoutés à la séance, le(s)
gestionnaire(s) de séance(s) peu(ven)t rédiger le procès-verbal. Il
doi(ven)t pour cela faire passer la séance dans son état de rédaction
de PV en cliquant sur le bouton "rédiger le PV".

Si un point "en retard" doit être inséré avec les points "normaux", il
suffit de remettre la séance "en création" avant de l'insérer.

* nouveau dans la version 3.3



2.5.6. Gestion des assemblée et signatures par points en mode "zones
de texte libre"
===============

Il est possible de redéfinir sur un point l'assemblée ainsi que les
signatures. Ainsi, si pour un point en particulier un membre de
l'assemblée était absent, il sera possible de le définir, idem
concernant les signatures qui pourront être définies spécifiquement
sur chaque point.

Deux modes de gestion de l'assemblée et des signatures sont
disponibles : les zones de texte libre (recommandées pour leur
souplesse), et les zones de cases à cocher (nécessite la `définition
d'utilisateurs spéciaux dans la configuration`_, pour pouvoir `gérer
les assemblées et signatures par points avec ces utilisateurs
spéciaux`_).

En mode de texte libre, il sera possible si l'utilisateur en cours en
a le droit (par défaut il s'agit uniquement des gestionnaires de
séance tant que la séance à laquelle les points sont liés n'est pas
"clôturée"), de redéfinir rapidement l'assemblée et les signatures de
plusieurs points en une seule fois.

En effet, prenons par exemple le cas d'une séance de 50 points qu'une
personne de l'assemblée a quitté à partir du point 25. Il sera
nécessaire de redéfinir l'assemblée spécifique des points 25 à 50,
pour ceci, il suffit de se positionner sur le point 25 et de cliquer
le crayon jaune qui sera affiché à côté du libellé "Assemblée pour ce
point" s'il est modifiable par l'utilisateur en cours :



Lorsque l'assemblée ou les signatures d'un point ont été redéfinis
pour le point en cours, le libellé "Assemblée pour ce point" ou
"Signatures" est affiché en rouge. Au clic sur le crayon jaune à côté
du libellé "Assemblée pour ce point", un écran de gestion est affiché
:



Il suffit donc de définir dans la zone "Assemblée à appliquer"
l'assemblée qui devra être spécifiquement utilisée pour le point en
cours. On peut procéder par copier/coller de la zone "Assemblée
définie sur la séance" et modifier les présents. S'il est nécessaire
d'appliquer jusqu'au point 50 (dans notre exemple), il suffira dans la
zone "Appliquer jsuqu'au point numéro" d'encoder "50" et l'assemblée
des points 25 à 50 sera adaptée lorsque l'utilisateur cliquera sur le
bouton "Appliquer". Un écran similaire apparaît pour la gestion des
signatures spécifiques du point.

Une fois adaptée, l'assemblée pour le point en cours est affichée et
le libellé est affiché en rouge pour montrer clairement que
l'assemblée est différente de l'assemblée définie sur la séance. Comme
il s'agit d'une zone de texte libre, on pourra y encoder le texte que
l'on souhaite, et faire paraître par exemple le fait que telle
personne était absente de tel à tel point :





2.6. Fonctionnalités supplémentaires apportées par les "utilisateurs
spéciaux"
=========





2.6.1. Caractéristiques des utilisateurs spéciaux
=================================================



La notion d'utilisateurs spéciaux représente la "personnification"
dans l'application différents intervenants liés à la gestion
délibératoire. Ceci signifie que pour chaque intervenant dans
l'application (signataire, présent à la séance, absent à la séance,
...) un utilisateur spécial correspondant doit être géré dans la
partie configuration. Les utilisateurs spéciaux sont configurables par
type de séance (voir `Configuration des utilisateurs spéciaux`_)

L'activation des utilisateurs spéciaux permettra de gérer de manière
plus structurée :


+ les présences lors de l'assemblée (fonction principale et fonction
  de remplaçant)
+ les votes par points
+ les personnes à l'initiative d'un point
+ les remplaçants
+ les signataires d'une séance (ou spécifiques à un point)
+ les signatures scannées d'un signataire



Cette fonctionnalité avancée permet de gérer plus finement certains
aspects mais demande par contre un travail de gestion de tous ces
utilisateurs dans la configuration (gestion des anciens et nouveaux
membres, gestion des remplaçants, ...). On utilisera donc cette
fonctionnalité à bon escient.

L'activation des utilisateurs spéciaux se fait `dans la
configuration`_ en spécifiant sur les données utilisées sur la séance
qu'on utilise les champs "Signataires" et "Présents" (ainsi que
"Excusés" et "Absents (non excusés") si nécessaire), plutôt que
"Signatures" et "Assemblée". En effet, ces paramètres sont exclusifs.




2.6.2. Gestion de l'assemblée et des signataires de la séance
=============================================================




Avec les utilisateurs spéciaux, les zones "Assemblée" et "Signatures"
qui sont des zones de texte libre `utilisées par défaut`_ sont
remplacées par des listes de cases à cocher affichées dans un tableau
comme celui-ci :



Le gestionnaire de séance pourra donc spécifier une assemblée par
défaut et adapter par la suite les présences en spécifiant qui était
présent, et qui était absent. En fonction de ce qui est défini dans la
configuration et des rôles ("usages") des utilisateurs spéciaux, il
est donc possible de définir :


+ les "présents" pendant la séance
+ les "présents, mais pas au début?" pendant la séance (il sera
  possible de définir à partir de quel point le membre a pris part à la
  séance)
+ les "absents (excusés)" pour la séance
+ les "Absents" non excusés pendant la séance
+ les "signataires"
+ un "remplaçant" pour une personne absente. La zone "remplacé par"
  permet de spécifier si le membre a été remplacé par une personne
  spécifique pour cette séance


A chaque fois, les utilisateurs sélectionnables le seront en fonction
de leur "usages" définis dans la configuration : membre d'assemblée,
signataire, votant, ...



2.6.3. Gestion de l'assemblée et des signataires par point
==========================================================



Lorsque l'assemblée par défaut a été définie sur la séance, il sera
possible, point par point de spécifier qui était présent, qui était
absent et quels étaient les signataires pour le point. Dans le cadre
de la gestion des présences par points, l'écran suivant est affiché
sur un point :



Pour ce point par exemple, on voit que :


+ "Henry Secrétaire" a quitté la séance à partir du point numéro 2 (
  2)
+ "Echevin du Personnel" est sorti pour ce point uniquement ( )
+ On peut accueillir "Echevin des travaux" à partir de ce point (il
  avait été défini comme "Présent mais pas au début?" sur la séance) en
  cliquant sur l'icône
+ Les membres présents et signataires pour ce point sont marqués d'un


Au survol d'un membre (ici "Pierre Bourgmestre") l'icône apparaît
montrant qu'on peut modifier la présence pour ce point. Au clic,
l'écran suivant est affiché :



Il est donc possible de facilement spécifier que le membre sélectionné
était absent pour le point en cours uniquement ou s'il a quitté la
séance définitivement...

Concernant l'adaptation des signataires spécifiques à un point, cela
se fait en passant par l'onglet "modifier" sur un point et en adaptant
la zone "Signataires pour ce point". Si aucun signataire spécifique
n'est défini pour ce point, les signataires définis sur la séance sont
utilisés.




2.6.4. Personne à l'initiative d'un point
=========================================



Lors de la rédaction d'un point, si le champ "A l'initiative de ce
point" est activé, une liste à choix multiples d'utilisateurs spéciaux
ayant l'usage "A l'initiative d'un point" sera affichée. Le créateur
du point peut alors sélectionner le ou les utilisateurs spéciaux à
l'initiative de ce point. Ceci permet de spécifier qu'un point est
créé au nom d'une personne n'ayant pas accès à l'application. Il peut
par exemple s'agir d'un point créé au nom d'un haut responsable
(échevin, ministre, chef de bureau, ...).

En outre, si le champ "Ce champ est une question orale?" est activé,
les 2 champs peuvent être utilisés conjointement pour spécifier qui
est à l'initiative de la question orale. Ceci pourra alors être
utilisé lors de l'impression d'un document par exemple :







2.6.5. Votes en séance
======================





Pour utiliser la gestion des votes il faut :


+ que la fonctionnalité de gestion des votes soit activée dans la
  configuration de la séance
+ que les utilisateurs spéciaux soient utilisés et que certains soient
  définis comme "votants"
+ que la séance soit démarrée ("date de la séance" ou "date de début
  de séance" si l'attribut est utilisé doit être antérieur à la date
  actuelle)
+ que la séance ne soit pas clôturée




Les valeurs de votes sont affichés sur le point :



Les différentes valeurs de vote sont configurables : pour, contre,
abstention, ... Une valeur par défaut de vote est également
sélectionnable dans la configuration. Le votant peut voir les votes
des autres s'il en a la permission et ne peut évidemment voter qu'en
son nom. Le gestionnaire de séance pourra, si cela a été défini dans
la configuration, voter pour tout le monde. Après le vote, ces
derniers sont visibles par les utilisateurs pouvant voir le point :



Le système de gestion des votes est également sécurisé, ce qui permet
de définir qui peut voir les votes sur le point.
Le gestionnaire de séance et les votants pourraient par exemple voir
les votes alors que la personne ayant créé le point ne pourrait pas.
La valeur "Non consultable" apparaît alors dans la colonne "Vote".
On peut aller très loin car une personne pourrait par exemple voir
certains votes mais pas tous...





2.6.6. Votes par le gestionnaire de séance
==========================================




On peut aussi donner la possibilité au gestionnaire de séance de voter
pour tout le monde :



Ceci permet d'utiliser la fonctionnalité "voter" même si les votes ne
sont pas encodés en séance.

D'une manière générale, l'intérêt d'automatiser les votes est de
gagner du temps : si les membres de l'assemblée votent en séance, ceci
permettra de générer automatiquement le résultat des votes lors de
l'impression de la délibération. Si les votes sont systématiquement
encodés par une seule personne, il peut être plus intéressant d'écrire
le résultat des votes au début de la délibération, sauf si on souhaite
par exemple que les votes et votants ne soient visibles que par
certains utilisateurs...


Votes secrets ou non secrets
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Le gestionnaire de séance pourra activer la notion de "votes secrets".
Si les votes sont secrets, seuls les gestionnaires de séances peuvent
les encoder. Au clic sur l'icône les votes pour le point bascule entre
les modes "secret / non secret" si aucun vote n'a encore été encodé!
Si c'est le cas, l'icône apparaîtra grisée ( ) et un message
d'explication apparaîtra au survol. En mode "secret", les votes sont
encodés en "nombre de voix", et plus par votant :







2.7. Écrans de gestion d'un procès-verbal
=========================================

Les écrans de gestion d'un procès-verbal



2.7.1. Gestion du procès-verbal
===============================





Après avoir fait passer la séance dans son état de rédaction du
procès-verbal, l'écran de gestion se présente comme suit :




Cet écran de gestion est similaire à l'écran de gestion d'un ordre du
jour, les informations affichées sous l'objet du point (dans notre
exemple, les champs "Description" et "Décision") peuvent être choisies
`dans la configuration, onglet "Interface utilisateur"`_.

Le procès-verbal présente, pour chaque point, quelques icônes
supplémentaires permettant de décider le point. Ces décisions sont en
réalité liées au workflow, comme par exemple "reporter", "accepter",
"accepter provisoirement", "refuser", etc.
Il est possible de décider plusueurs points en une seule fois en les
sélectionnant et, au bas de la page, en sélectionnant *"Pour les
points sélectionnés, effectuer l'action suivante :"*.



2.7.2. Afficher le procès-verbal de manière optimale
====================================================



En mode "Procès-verbal", de `nombreuses informations sont affichées à
l'écran`_ c'est pourquoi l'icône permettant de cacher les informations
concernant l'assemblée et l'icône permettant de cacher les champs
"description" et "décision" sur un point sont très utiles dans ce
cadre. Si on cache l'assemblée et les détails sur les points, voici ce
qui est affiché :



En outre, si le procès-verbal contient beaucoup de points, on peut
définir `dans la configuration`_ combien de points seront affichés à
la fois et une pagination apparaîtra sur la vue d'une séance
permettant par exemple de montrer les 25 premiers points et de passer
aux 25 suivants.

Imaginons par exemple une limite fixée à "5 points affichés par page",
les points présentés dans la séance serait affichés comme ceci :







2.7.3. Rédaction du procès-verbal
=================================



La rédaction des décisions sur les points lorsque la séance est en
Procès-verbal est `identique à celle utilisée lorsque la séance est en
ordre du jour`_.



2.8. Recherche avancée
======================

Lorsque la zone de recherche "full-text" retourne trop de résultat, il
est possible de filtrer d'avantage en utilisant la recherche avancée

Voici l'écran proposé (cet écran peut être différent en fonction de la
configuration, en effet, le champ "Groupe(s) associé(s)" par exemple
n'apparaîtra que si la fonctionnalité "Groupe(s) associé(s)" est
activée dans la configuration) au clic sur l'icône du portlet
"Gestion" (voir la page `Interface générale`_) :



Par défaut, si aucune option n'est définie, la recherche avancée se
comporte comme la recherche "full-text" mais il sera possible ici de
définir des filtres, par exemple de ne rechercher que les points de
tels groupes proposant, et/ou les points de telles catégories, il est
également possible de définir une plage temporelle de recherche, utile
à partir du moment ou l'application est utilisée depuis plusieurs
années, ... La recherche est insensible aux accents et un début de mot
peut être encodé dans la zone "mots-clé" pour effectuer la recherche,
ainsi une recherche sur "budget" ramènera aussi les éléments contenant
le mot "budgétaire".



3. Particularités par type de délibération
==========================================

Particularités des configuration prédéfinies



3.1. Gestion du Collège Communal
================================

Explication de la configuration par défaut du Collège Communal
(produit "MeetingCommunes")



3.1.1. Caractéristiques
=======================




Les caractéristiques de l'application de gestion du Collège Communal
sont identiques aux caractéristiques générales présentées
précédemment.

La particularité est que les champs nécessaires à la gestion des
aspects propres au Collège Communal ont été activés par défaut :


Sur le point :
~~~~~~~~~~~~~~


+ Informations budgétaires : champ de texte riche permettant de
  stocker les informations propres à l'aspect budgétaire
+ A évoquer en séance? : permet de spécifier si le point doit être
  discuté en séance ou s'il s'agit d'un point récurrent
+ A envoyer vers : si la configuration de séance "Collège Communal"
  est utilisée conjointement avec la configuration de séance "Conseil
  Communal", il est possible dans la zone "A envoyer vers" de cocher
  "Conseil Communal". De la sorte, celà permet de définir qu'un point
  Collège Communal doit passer au Conseil Communal. Pratiquement, le
  point sera automatiquement envoyé vers le Conseil Communal lorsqu'il
  sera "accepté" ou "accepté avec modifications"



Sur la séance :
~~~~~~~~~~~~~~~

Les champs par défaut sont utilisés


Le cheminement du point dans l'application aussi appelé "workflow" est
le suivant :
------------


Point en création : le point est en cours d'élaboration et est
visible/modifiable par tous les membres du service. L'ajout d'annexe
est activé pour tous. Lorsque tout est rempli, on peut "proposer" le
point

Point proposé : le point a été rédigé par un agent qui le propose
alors au validateur de point du service (souvent le chef de service).
A cette étape, il n'y a plus que les validateurs qui peuvent modifier
le point et y ajouter des annexes, les autres peuvent cependant
toujours le voir. Si le validateur estime qu'il y a un problème et
qu'il souhaite rendre la main au créateur du point pour qu'il le
modifie, il peut le "corriger". Si tout est OK, le validateur peut
"valider" le point

Point validé : le point est maintenant visible par les personnes
gérant les séances. Ils voient le point et peuvent l'insérer dans une
séance en création

Point présenté : ceci signifie que le point a été inséré dans une
séance en création. A ce moment là, la séance est création n'est pas
encore visible

Point gelé : ceci signifie que le point est maintenant dans une séance
qui a été gelée. Une séance est gelée la veille de la séance du
collège communal. cela signifie que plus aucun point ne peut y être
ajouté (sauf point en urgence). A partir de ce moment, la séance est
visible et apparaît dans la liste des ordres du jour. En outre un lien
vers la séance est disponible sur l'écran de visualisation du point

Point décidés : après la séance, les décisions pour chaque point
seront écrites par les gestionnaires de la séance. Lorsque la décision
(délibération) est complète (et visible dans la zone "Décision" sur
l'écran de visualisation 'un point), une décision peut être mise sur
ce point. Les différentes décisions possibles sont :


+ point accepté : le point a été accepté par le collège communal sans
  que le projet de délibération n'ai du être modifié dans la zone
  "Décision". Si le point devait être envoyé vers une autre séance
  (Point Collège communal vers Point Conseil communal par exemple), il
  est automatiquement envoyé
+ point accepté avec modification : le point a été accepté mais la
  délibération finale est différente du projet de délibération proposé
  dans la zone "Décision". Si le point devait être envoyé vers une autre
  séance (Point Collège communal vers Point Conseil communal par
  exemple), il est automatiquement envoyé
+ point accepté provisoirement : le point a été accepté durant la
  séance mais le secrétariat communal n'a pas encore corrigé le projet
  de délibération pour en faire la délibération finale
+ point refusé : si un point est refusé, la zone "Décision" en
  contient la raison
+ point reporté : un point reporté sera automatiquement dupliqué chez
  l'utilisateur ayant créé le point afin qu'il soit plus facile de le
  présenter à nouveau






3.2. Gestion du Conseil Communal
================================

Explication de la configuration par défaut du Conseil Communal
(produit "MeetingCommunes")



3.2.1. Caractéristiques
=======================



Les caractéristiques de l'application de gestion du Conseil Communal
sont similaires aux caractéristiques générales présentées dans `la
configuration Collège communal`_.


Les champs
~~~~~~~~~~

Quelques champs nécessaires à la gestion des aspects propres au
Conseil Communal ont été activés par défaut :

* Sur le point : *


+ Niveau de confidentialité : permet de définir si le point doit être
  discuté en séance publique ou à huis clos
+ Ce point est une question orale? : permet de gérer les questions
  orales ajoutées après publication de l'ordre du jour par les
  conseillers
+ A l'initiative de ce point : permet de spécifier quels acteurs
  (échevins ou conseillers par exemple) sont à l'initiative du point
  (peut être utilisé conjointement avec le champ "Ce point est une
  question orale?")


* Sur la séance : *


+ Date de fin de la première partie : cette date et heure peut être
  utilisée pour spécifier à quelle heure s'est terminée la première
  partie de la séance (séance publique ou à huis clos)




Le workflow
~~~~~~~~~~~

Le workflow est proche du workflow proposé par la `configuration
"Collège Communal"`_ excepté * qu'une notion de "publication" est
ajoutée *.

Après le gel de la séance, celle-ci peut être publiée (les points liés
sont alors publiés également). A partir de ce moment, tous les points
sont visibles par tout le monde, y compris lorsqu'ils seront décidés
(accepté, refusé, reporté, ...). Cette notion permet à un type de
séance d'être visible par tous à partir de la publication ce qui peut
être le cas pour le conseil (publication de l'ordre du jour). * Si on
ne souhaite pas que le conseil soit publié à tous *, il est évidemment
possible dans la configuration du type de séance Conseil communal,
`section "workflows"`_ d'utiliser le même workflow que celui utilisé
pour le collège. La notion de "publication" disparaît alors...




3.2.2. Définir l'accès pour les conseillers : les "super observateurs"
et les "super observateurs restreints"
======================================



Deux groupes particuliers d'utilisateurs appelés "super observateurs"
et "super observateurs restreints" sont créés dans l'application par
type de séance (collège communal, conseil communal, ...). Ces
utilisateurs ont la possibilités d'accéder à tous les points et
séances de ce type de séance lorsque ces derniers sont dans certains
états.

Il faudra donc pour ces "super observateurs" et "super observateurs
restreints" :


+ configurer les états dans lesquels les séances et points seront
  visibles
+ mettre à jour les accès des "super observateurs" et "super
  observateurs restreints"
+ ajouter dans le groupe adéquat les utilisateurs qui devront obtenir
  ce rôle



Configurer les états dans lesquels les séances et points seront
visibles
~~~~~~~~

Dans la configuration de séance souhaitée (par exemple "Collège
communal"), onglet "Avis et accès", définir les états adéquats dans
les zones :


+ Etats des points dans lesquels les 'Super observateurs' peuvent les
  voir
+ Etats des séances dans lesquels les 'Super observateurs' peuvent les
  voir
+ Etats des points dans lesquels les 'Super observateurs restreints'
  peuvent les voir
+ Etats des séances dans lesquels les 'Super observateurs restreints'
  peuvent les voir


Plus d'informations sur la configuration et l'onglet `Section "Avis et
accès"`_


Mettre à jour les accès des "super observateurs (restreints)"
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Si des changements interviennent dans la configuration, comme par
exemple le fait de changer les états des points visibles par les
"super observateurs (restreints)", il est nécessaire de "Mettre à jour
les 'Super observateurs (restreints)'" en passant par Configuration du
site-->PloneMeeting et en cliquant sur le bouton adéquat en bas de
page. Ceci n'est à effectuer que si la configuration liée au "super
observateurs (restreints)" a changé.

Plus d'informations sur l'`écran principal de configuration de
PloneMeeting`_


Ajouter dans le groupe adéquat les utilisateurs qui devront obtenir ce
rôle
~~~~

A chaque configuration de séance est liée un groupe Plone appelé "Nom
de la configuration de séance (Super observateurs)" et un groupe Plone
appelé "Nom de la configuration de séance (Super observateurs
restreints)", donc par exemple "Collège communal (Super observateurs)"
et "Collège communal (Super observateurs restreints)". Ces groupes
peuvent être facilement trouvé dans la Configuration du
site-->Utilisateurs et Groupes-->onglet "Groupes" en effectuant une
recherche sur le terme "super".

Placez y les utilisateurs qui devront voir les points qui sont dans
les états définis dans l'étape ci-dessus.





3.3. Adaptation spécifiques du workflow
=======================================



Le workflow comme celui utilisé pour la `gestion du Collège communal`_
permet de définir le cheminement du point ou de la séance dans
l'application. Le cheminement du point est défini au début de
l'utilisation de l'application et peut évoluer par la suite.

L'application propose néanmoins quelques `adaptations au workflow qui
pourront être activées dans la configuration`_.

On pourra par exemple choisir :


+ de renvoyer un point au groupe proposant pour correction . En effet,
  par défaut dès qu'un point est présenté à une séance, seuls les
  gestionnaires de séances peuvent le modifier. Cet fonctionnalité
  permet lorsque le point est dans une séance, de le renvoyer au groupe
  proposant (le groupe proposant reprend alors la main sur le point pour
  le modifier) sans le retirer de la séace. Une fois corrigé, le point
  est renvoyé par le groupe proposant vers les gestionnaires de séances
  qui reprennent alors la main sur ce dernier. Pendant tout ce temps, le
  point est bien resté dans la séance à la position qui était la sienne
+ d'avoir un état "publié" supplémentaire dans le workflow de la
  séance. Ceci permet par exemple de publier (montrer à tous) les points
  de la séance à un certain moment. Ceci peut être le cas pour le
  conseil communal (non activé par défaut) par exemple
+ d'ajouter une étape de pré-validation des points : en plus du
  validateur, une autre personne intervient avant pour pré-valider le
  point
+ de ne pas avoir à proposer les points , les points sont directement
  validés par l'agent créateur
+ que le service ne puisse pas encoder la décision sur le point , ce
  sera la tâche des gestionnaires de séances uniquement
+ de cacher la décision aux groupes proposants lorsque la séance est
  en "rédaction du Procès-verbal" et que les gestionnaires de séance
  l'adaptent, une transition supplémentaire "publier les decisions aux
  groupes proposants" apparaît alors dans le workflow de la séance et
  permet aux gestionnaires de séances de montrer les décision aux agents
  ayant proposés les points
+ ...






4. Configuration de l'application
=================================

Comment configurer l'application



4.1. Panneau de configuration général
=====================================





Un administrateur peut accéder à la configuration des outils installés
via le lien "Configuration du site".

Il peut alors sélectionner dans le menu de gauche (partie inférieure)
l'entrée " PloneMeeting", ce qui lui permet d'accéder à la
configuration de l'application.

L'écran de configuration regroupe 3 parties:


+ des paramètres spécifiques liés aux différentes configurations de
  séances (par exemple "Collège Communal", "Conseil Communal", ...)
+ les paramètres liés à la gestion des groupes
+ des paramètres globaux de l'application concernant la production des
  documents bureautiques, les recherches, ...




1. Configurations de séances





2. Gestion des groupes :




3. Paramètres globaux de l'application



Certains écrans disposent de boutons ou de liens qui renvoient vers
des écrans secondaires.

La modification des paramètres globaux se fait via l'onglet
"Modifier".

Les différents paramètres sont expliqués en détail dans les écrans.
Nous conseillons cependant de ne pas modifier les réglages par défaut
sans en connaître la portée.

Les actions ("Recalculer les index des annexes", "Convertir les
annexes pour la prévisualisation", "Mettre à jour les avis", "Mettre à
jour les 'Super observateurs'", ...) sont des actions que
l'administrateur peut exécuter lorsque certains paramètres sont
modifiés (un libellé rouge à côté d'un paramètre prévient si la
modification de ce paramètre nécessitera l'exécution d'une de ces
actions). Cela permet de mettre à jour ces informations sur les points
existants dans l'application. Comme ces actions peuvent prendre du
temps en fonction du nombre de points existants, il ne faut les lancer
qu'en connaissance de cause (et si nécessaire) et lorsque
l'application n'est pas utilisée (hors période de forte utilisation).




4.2. Écrans de gestion des groupes PloneMeeting
===============================================




Lors de la configuration de l'application, la première étape est de
définir les groupes qui seront utilisés. Cette configuration se fait
dans la deuxième partie de l'écran de configuration général.



La manière dont fonctionne les groupes est expliquée dans le point
"`Organisation en groupes`_".

Différentes opérations peuvent être effectuées sur les groupes.
Il est possible de les ordonner avec les flèches "haut/bas" (ce qui
permettra de définir par exemple l'ordre de préséance), de les
modifier et de les supprimer.
Dans ce dernier cas, le système vérifiera si aucun point n'est lié à
ce groupe et si plus aucun utilisateur n'est dans les groupes Plone
liés.
Si le groupe a déjà créé des points mais qu'on ne souhaite plus
l'utiliser, la solution est de le désactiver. Lorsqu'un groupe est
désactivé, tous les membres des sous-groupes (créateurs, validateurs,
...) sont déplacés dans le sous-groupe "observateurs" afin que les
membres puissent tjs voir les points créés auparavant mais ne puisse
plus en créer/valider/donner un avis au nom de ce groupe/...

Pour créer un nouveau groupe, il suffit de cliquer sur l'icône :




Le titre est l'intitulé du groupe tel qu'il apparaît dans l'écran de
configuration principal. L' acronyme est un diminutif qui peut être
utilisé à différents niveaux pour représenter le groupe qui propose un
point (comme dans la référence du point par exemple).

Les gestion des avis peut être ici finement configurée groupe par
groupe. En effet comme le montre les zones " États des points dans
lesquels on peut donner son avis" et " États des points dans lesquels
on peut modifier ou supprimer un avis donné" , il est possible de
définir groupe par groupe comment la gestion des avis se comportera.
Si rien n'est défini sur le groupe concernant les avis, les
`paramètres globaux définis sur les avis`_ seront utilisés

Une fois le nouveau groupe PloneMeeting créé, 5 groupes Plone sont
automatiquement ajoutés :


+ "nom_du_groupe_Plonemeeting ( * créateurs *)" : destiné à contenir
  les membres qui peuvent créer des points pour le groupe PloneMeeting
  correspondant
+ "nom_du_groupe_Plonemeeting ( * pré-validateurs *)" : destiné à
  contenir les membres qui peuvent pré-valider les points du groupe
  PloneMeeting correspondant
+ "nom_du_groupe_Plonemeeting ( * observateurs *)" : destiné à
  contenir les membres qui peuvent uniquement voir les points du groupe
  PloneMeeting correspondant
+ "nom_du_groupe_Plonemeeting ( * validateurs *)" : destiné à contenir
  les membres qui peuvent valider les points du groupe PloneMeeting
  correspondant
+ "nom_du_groupe_Plonemeeting ( * émetteurs d'avis *)" : destiné à
  contenir les membres qui peuvent donner un avis au nom du groupe
  PloneMeeting correspondant



Une même personne peut être membre de plusieurs groupes Plone, que ce
soit pour un même groupe PloneMeeting ou plusieurs.

ATTENTION : Dans la * gestion des utilisateurs * (Configuration du
site --> Administration des utilisateurs et des groupes), une série de
rôles liés à cette application apparaissent: Gestionnaire de séance,
MeetingObserverGlobal, MeetingMember, ... Tous ces rôles sont listés
mais il ne faut pas les donner directement à un utilisateur sous peine
de dysfonctionnement ! Les rôles sont attribués par l'application à
l'utilisateur via les groupes dans lesquels il est ajouté.

Concrètement, après avoir créé les différents groupes PloneMeeting,
l'administrateur doit donc :


#. ajouter les utilisateurs dans les bons groupes (dans l'écran de
   gestion des utilisateurs, faire une recherche sur un utilisateur ou
   afficher la liste complète, cliquer sur le nom d'un utilisateur,
   cliquer sur l'onglet " *Groupes de l'utilisateur* " et ajouter
   l'utilisateur dans des groupes)(pour d'avantage d'explications sur
   l'ajout des utilisateurs, se reporter à la documentation concernant
   `la gestion des utilisateurs et des groupes`_)
#. définir les gestionnaires de séances en les ajoutant dans le groupe
   " *Gestionnaires de séance* " pour chaque configuration de séance dans
   laquelle l'utilisateur pourra gérer les séances. Pour cela, dans la
   configuration des utilisateurs et groupes, il suffit de faire une
   recherche sur "Gestionnaires de séances".
#. ajouter dans les groupes "Nom de ma configuration de séance (
   *Super observateurs* )" et "Nom de ma configuration de séance ( *
   Super observateurs restreints *)" les utilisateurs (échevins,
   conseillers, ...) qui pourront voir tous les points et séances à
   partir d'un certain état (ces états sont à définir dans la "`Section
   avis et accès`_" de la configuration de séance)
#. ajouter dans le groupe "Nom de ma configuration de séance
   (Gestionnaires d'informations budgétaires)" les utilisateurs
   (Directeur financier, chef de la comptabilité, ...) qui pourront
   éditer les informations budgétaires des points lorsque ceux-ci sont
   dans certains états (ces états sont à définir dans la "`Section avis
   et accès`_" de la configuration de séance)




4.3. Écrans de gestion des configurations de séance
===================================================





4.3.1. Résumé des types de séance définis
=========================================




Le premier cadre présent dans l'écran de configuration général permet
de gérer les configurations de séance, c'est-à-dire différents types
de séance qui apparaîtront dans des onglets différents pour
l'utilisateur.
Dans cet exemple, les configurations de séance "Collège Communal" et
"Conseil Communal" sont affichées.




Un clic sur l'icône permet de créer un nouveau type de séance et de le
configurer. Une configuration de séance ne pourra être supprimée que
si plus aucun point ni séance n'y sont liés.

En cliquant sur le nom d'un type de séance, l'administrateur accède à
différents paramètres supplémentaires défini "par configuration de
séance". Il est donc possible d'avoir des paramètres différents en
fonction de la configuration de séance choisie.

La colonne "active" affiche si le type de séance est activé ou non.
Pour activer ou désactiver un type de séance, il faut changer son
état.




4.3.2. Vue des paramètres d'une séance
======================================




Après voir sélectionné un type de séance (en cliquant sur son titre),
l'écran suivant est affiché :





L'écran principal est subdivisé en sections regroupant les paramètres
:


+ Général : paramètres généraux
+ Assemblée et signatures : rassemble les paramètres liés à la gestion
  de l'assemblée et des signatures, *ces paramètres sont éditables par
  les gestionnaires de séances*
+ Données : paramètres concernant les champs optionnels sur les
  séances et points, les types d'annexes, les catégories de points, les
  classificateurs, les points récurrents et les utilisateurs spéciaux
+ Workflows : paramètres concernant les flux (workflows) utilisés sur
  les points, les séances et les avis
+ Interface utilisateur : paramètres influant sur l'interface
  graphique telles que les écrans de recherche (boîte d'informations
  "points", "séances", ...)
+ Courriels : paramètres permettant de sélectionner les cas où un
  courriel doit être envoyé pour prévenir certains utilisateurs de
  l'évolution de certains éléments dans l'application
+ Avis et accès : permet d'activer ou non la gestion des avis et des
  points en copie, de configurer qui pourra donner un avis et quels sont
  les niveaux d'accord. La gestion des émetteurs d'avis automatiques se
  fait via la `gestion des groupes`_
+ Votes : permet d'activer ou non la gestion des votes et de définir
  qui pourra voter et quelles seront les valeurs de vote différentes
+ Utilisateurs : permet d'accéder et configurer les caractéristiques
  et préférences de chaque utilisateur qui sont spécifiques à cette
  séance.
+ Documents : permet de gérer les documents qui seront utilisés pour
  les impressions des points et séances




Tous ces écrans sont expliqués dans les pages suivantes.




4.3.3. Section "Général"
========================

Description des différents paramètres accessible dans la section
"Général"


Cette section reprend les paramètres généraux de l'application :




+ Valeur par défaut du champ 'Informations budgétaires' : ce champ
  contiendra la valeur par défaut à utiliser pour le champ optionnel
  "Informations budgétaires" si ce dernier est activé sur les points
+ Valeur par défaut du champ 'Motivation' : ce champ contiendra la
  valeur par défaut à utiliser pour le champ optionnel "Motivation" si
  ce dernier est activé sur les points
+ Lieux pour la séance : ce champ permet de définir une liste de
  valeur qui génèrera une liste déroulante sur la séance lorsqu'il
  s'agira de définir où se déroule la séance. Ce champ n'est à remplir
  que si le champ optionnel "Lieu" est activé sur la séance
+ Nom du répertoire lié à cette configuration : il s'agit du nom
  apparaissant sur l'onglet lié à cette configuration de séance. Lors de
  la création d'une configuration de séance, le nom est le même que le
  titre de la configuration, mais on peut le changer. Cette opération
  doit être idéalement faite avant la mise en production de
  l'application.
+ Nom court pour la configuration de séance : il s'agit d'un
  identifiant pour la configuration de séance. A nouveau, ce paramètre
  ne doit pas être changé au cours de l'utilisation d'une "configuration
  de séance"
+ Cette configuration est celle par défaut : cette valeur booléenne
  (vrai/faux) permet de spécifier si la configuration de séance est
  celle par défaut. Dans le cadre où plusieurs configurations de séance
  sont définies, on peut par exemple rediriger l'utilisateur connecté
  vers la configuration de séance par défaut
+ Numéro de la dernière séance de cette configuration : cette valeur
  contient le numéro de la dernière séance clôturée de cette
  configuration de séance. Ce numéro peut être utilisé par exemple dans
  la référence du point
+ Réinitialiser le numéro de séance chaque année? : dans le cadre ou
  le champ "Numéro de la dernière séance de cette configuration" est
  utilisé (pour être imprimé dans un document par exemple), ce numéro
  peut être automatiquement remis à zéro chaque année
+ Identifiant de la version de cette configuration : dans le cadre où
  une configuration de séance évolue fortement, on peut créer plusieurs
  configuration de séance du même nom et spécifier quelles séances et
  quels points sont liés à quelle configuration de séance
+ Les points sont créés uniquement depuis un modèle : si cette option
  est activée, il n'est plus possible de créer un point depuis un
  formulaire vierge, un point devra obligatoirement être créé en
  utilisant un modèle de point *
+ Activer l'impression des annexes : s'il est nécessaire de pouvoir
  imprimer des annexes dans un document généré (Délibération, Ordre du
  jour, PV, ...) alors il faut activer l'impression des annexes. Chaque
  annexe sera convertie dans un format qui permettra de l'insérer dans
  un document généré. Une zone supplémentaire "A imprimer?" apparaît
  alors sur le tableau affichant les annexes, l'utilisateur pouvant
  modifier les annexes pourra spécifier quelle annexe est "à imprimer"
+ Marquer les annexes comme 'à imprimer?' par défaut : dans le cadre
  ou l'impression des annexes est activée, les annexes peuvent être "à
  imprimer" par défaut, ou non
+ Marquer les annexes à la décision comme 'à imprimer?' par défaut :
  dans le cadre ou l'impression des annexes est activée, les annexes à
  la décision peuvent être "à imprimer" par défaut, ou non
+ Marquer les annexes à un avis comme 'à imprimer?' par défaut : dans
  le cadre ou l'impression des annexes est activée, les annexes à un
  avis peuvent être "à imprimer" par défaut, ou non
+ Actions d'initialisation de la confidentialité des annexes et avis :
  ceci permet lorsque la confidentialité des annexes ou avis est activée
  sur une configuration de séance qui contient déjà des avis et annexes
  d'initialiser tous les avis et annexes existants à la valeur par
  défaut définie dans la configuration de séance



* nouveau dans la version 3.3



4.3.4. Section "Assemblée et signatures"
========================================

Description des différents paramètres accessible dans la section
"Assemblée et signatures"

Cette section regroupe les différents paramètres qui sont éditables
par les gestionnaires de séances :




+ Assemblée par défaut : définit l'assemblée présente à la séance par
  défaut. Cette valeur sera la valeur par défaut de la zone "Assemblée"
  lors de la création d'une séance si le champ "Assemblée par défaut" a
  été sélectionné dans les champs optionnels sur une séance
+ Signatures par défaut : définit les signatures qui devront
  apparaître sur les documents liés à cette séance.
+ Signatures certifiées conformes : définit les signatures certifiées
  conformes courantes qui pourront être utilisées lors de la génération
  de documents. Les signatures certifiées conformes peuvent être
  définies à l'avance si on sait quand les signataires seront présents,
  on peut en effet définir une période au cours de laquelle une
  signature sera valide.


Pour ces 3 champs : ces valeurs sont utilisées uniquement si
l'assemblée et les signatures des séances et points ne sont pas gérés
par les "Utilisateurs spéciaux". Si ces champs ne sont pas utilisés,
une remarque apparaît en rouge.

* nouveau dans la version 3.3



4.3.5. Section "Données"
========================




Cette section reprend les paramètres liés aux données et champs
utilisés dans la configuration de séance :



Une partie des paramètres est modifiable via l'icône [ Données ] :


+ Attributs utilisés pour caractériser un point : présente la liste
  des champs optionnels que l'on peut activer sur un point : Description
  détaillée, Informations budgétaires, Classificateur, Groupe(s)
  associé(s), Marqueurs, Mots-clé, Ce point est une question orale?, A
  l'initiative de ce point, Observations, A évoquer en séance, Assemblée
  spécifique liée à ce point, Niveau de confidentialité, Questions,
  Réponses, Point signé?
+ Attributs des points pour lesquels l'historique doit être conservé :
  présente la liste des champs du points qui doivent être historisés
  (versioning). Chaque champ disponible sur le point peut être
  sélectionné
+ Etat des points dans lesquels l'historisation est active : permet de
  sélectionner les états (workflow) du point dans lesquels la
  fonctionnalité d'historisation sera activée
+ Attributs utilisés pour caractériser une séance : présente la liste
  des champs optionnels que l'on peut activer sur une séance : Date et
  heure effective de début, Date et heure effective de fin, Date de fin
  de la première partie, Signatures, Signataires, Assemblée, Présents,
  Excusés, Absents (non excusés), Présents (mais pas au début), Lieu,
  Observations, Date de la séance préparatoire, Lieu de la séance
  préparatoire, Observations pour la séance préparatoire, Point
  présentés à cette séance (y compris après publication de celle-ci),
  Echéance pour valider les points, Echéance pour valider les points en
  retard
+ Attributs des séances pour lesquels l'historique doit être conservé
  : présente la liste des champs de la séance qui doivent être
  historisés (versioning). Chaque champ disponible sur le point peut
  être sélectionné
+ Etat des séances dans lesquels l'historisation est active : permet
  de sélectionner les états (workflow) de la séance dans lesquels la
  fonctionnalité d'historisation sera activée
+ Utiliser les groupes comme catégorie : il faut un élément pour
  "catégoriser" un point. Si les catégories ne sont pas utilisées, on
  peut spécifier que c'est le "groupe proposant" qui catégorise le point
+ Affecter une valeur au champ 'à discuter' quand un point est inséré
  dans une séance : permet de définir si la valeur du champ "à discuter"
  est encodée automatiquement lors de l'insertion dans une séance en
  fonction des 2 paramètres ci-dessous ou si c'est le créateur du point
  qui définit cette valeur
+ Valeur par défaut de l'attribut 'à discuter' pour les points normaux
  : si l'attribut optionnel "A discuter?" est activé sur les points,
  comme il s'agit d'un booléen, on peut spécifier ici s'il sera "A
  discuter" par défaut à non. En outre, cette valeur concerne les
  "Points normaux", c'est-à-dire les points qui ne sont pas ajoutés en
  retard
+ Valeur par défaut de l'attribut 'à discuter' pour les points en
  retard : si l'attribut optionnel "A discuter?" est activé sur les
  points, comme il s'agit d'un booléen, on peut spécifier ici s'il sera
  "A discuter" par défaut à non. En outre, cette valeur concerne les
  "Points en retard", c'est-à-dire les points qui sont ajoutés après la
  date limite d'ajout des points avant que la séance ait lieu
+ Montrer le champ 'à discuter' pour les points en retard : permet de
  spécifier si l'option "points à discuter" doit être utilisable sur les
  points en retard
+ Format de la référence d'un point : cette zone contient une
  expression qui permettra de générer une référence pour le point. Par
  défaut, la référence est de type "Ref. 45" ou 45 est le numéro du
  point, mais on peut adapter l'expression
+ Méthode(s) de tri lors de l'ajout d'un point dans une séance :
  lorsqu'un gestionnaire de séance ajoute un point dans une séance
  comportant déjà des points, il est possible de spécifier où ira se
  placer le point par défaut. Il est possible de sélectionner des
  méthodes de tri successives, par exemple, trier un point inséré par
  groupe proposant puis par catégorie *
+ Marqueurs : éléments qui pourront être sélectionnés pour
  caractériser un point. Il s'agit de la notion de "tag". Cette dernière
  est plus complète que la catégorie simple mais moins que les marqueurs
  qui peuvent être hiérarchisés
+ Trier les marqueurs par ordre alphabétique : si les marqueurs sont
  utilisés, on peut les trier automatiquement par ordre alphabétique,
  quel que soit l'ordre défini dans le champs "Marqueurs". Sinon, il
  apparaîtront dans l'ordre défini dans ce dernier
+ Champs de texte riche qui doivent être transformés : chaque champ
  que vous sélectionnez dans cette liste subira, lors de chaque création
  ou modification de l'objet qui le contient, la (les) transformation(s)
  définie(s) dans le champ suivant
+ Types de transformations pour les champs de texte riche :
  sélectionnez ici le(s) type(s) de transformation(s) à appliquer aux
  champs de texte riche sélectionnés ci-dessus. Les transformations
  disponibles sont : Supprimer les paragraphes vides et Eviter les
  signatures seules sur les dernières pages
+ Echéance par défaut pour valider les points pour une séance donnée :
  permet de spécifier une échéance en fonction de la date de la séance
  avant laquelle les points doivent être validés
+ Echéance par défaut pour valider les points en retard pour une
  séance donnée : permet de spécifier une échéance en fonction de la
  date de la séance avant laquelle les points en retard doivent être
  validés
+ Date par défaut pour la séance préparatoire : permet de spécifier
  une date par défaut à utiliser pour la séance préparatoire par rapport
  à la date de la séance
+ Activer la gestion des remplaçants : la gestion des remplaçants vous
  permet de sélectionner un remplaçant pour tout membre d'assemblée
  absent à une séance
+ Configurations de séance vers lesquelles les points de cette séance
  peuvent être envoyés : permet de spécifier vers quelles autres types
  de séance les points de la configuration de séance en cours pourront
  être envoyés. En outre, une fois qu'un point est envoyé vers un autre
  type de séance, il est possible de spécifier que le point doit être
  mis automatiquement dans un état particulier, par exemple "validé" *





Ensuite, des tableaux reprennent différents éléments configurables :
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


+ Types d'annexes : lors de l'ajout d'une annexe à un point, il est
  possible de sélectionner le type d'annexe. Ceci permet de classer
  l'annexe adjointe au point. Un type d'annexe définit un titre, une
  icône et le fait qu'il s'agit d'un type lié aux "annexes", aux
  "annexes (à la décision)" d'un point ou aux "annexes à un avis". Si la
  confidentialité des annexes est activée, il sera possible de définir
  par type d'annexe la valeur par défaut de la confidentialité des
  annexes. Sur un type d'annexe, il est également possible de définir
  des sous-types d'annexes, ceci permet dans les organisations utilisant
  beaucoup de types d'annexes d'en rassembler plusieurs sous la même
  icône
+ Catégories de point : si on le souhaite, on peut utiliser les
  catégories pour caractériser un point. Il sera possible de restreindre
  l'utilisation d'une catégorie à certains groupes
+ Classificateurs : les classificateurs permettent d'étendre
  l'utilisation des catégories et marqueurs. Leur utilisation est
  recommandée lorsque vous avez beaucoup de catégories. En effet, grâce
  à une interface utilisateur adaptée, vous allez pouvoir hiérarchiser,
  rechercher et sélectionner les classificateurs et ce de multiples
  manières
+ Points récurrents : il est possible de définir dans la configuration
  des * "points récurrents" * qui s'insèreront automatiquement dans une
  séance au moment voulu. Il s'agit de point revenant systématiquement
  dans une séance ("Approbation du PV de la séance antérieure" par
  exemple). On peut par exemple faire en sorte qu'à la création d'une
  séance, 3 points soient automatiquement insérés. Les points récurrents
  peuvent être insérés à la création de la séance ou lors d'une
  transition du workflow de cette dernière (lorsque la séance est
  "gelée", lorsque la séance est "clôturée", ...)
+ Modèles de points : cette partie permet d'accéder à un écran où
  seront définis des modèles de points. Ces modèles peuvent être
  `sélectionnés par un utilisateur lors de la création d'un point`_. Ces
  modèles peuvent être organisés de manière hiérarchique dans des
  dossiers et sous-dossiers * :








* nouveau dans la version 3.3



4.3.6. Section "Workflows"
==========================




L'écran permet de gérer les workflows liés aux séances, points et avis
:



Il est ici possible de sélectionner le workflow qui régira les séances
et les points de cette configuration de séance.


+ Les champs Workflow gouvernant le cycle de vie de chaque point de
  cette configuration , Interface permettant d'utiliser un adapter Zope3
  spécifique pour modifier les conditions définies sur les transitions
  du workflow gouvernant les points , Interface permettant d'utiliser un
  adapter Zope3 spécifique pour modifier les actions définies sur les
  transitions du workflow gouvernant les points , Workflow gouvernant le
  cycle de vie de chaque séance de cette configuration , Interface
  permettant d'utiliser un adapter Zope3 spécifique pour modifier les
  conditions définies sur les transitions du workflow gouvernant les
  séances , Interface permettant d'utiliser un adapter Zope3 spécifique
  pour modifier les actions définies sur les transitions du workflow
  gouvernant les séances permettent de définir les paramètres techniques
  liés aux workflows. Nous conseillons de ne pas modifier ces paramètres
  à moins d'une connaissance précise du fonctionnement
+ Adaptation(s) aux workflows : permet de modifier le workflow proposé
  au besoin. Les adaptations possibles sont : Pas d'observations globale
  des points, Les décisions d'un point sont pré-encodées par le créateur
  du point, Seuls les créateurs de points peuvent supprimer des points,
  Pré-validation des points, Les points arrivent validés, Sauter l'étape
  de publication, Sauter l'étape de proposition des points, Tout le
  monde peut tout consulter dans tout état, Le créateur d'un point peut
  modifier à moins que la séance soit clôturée, Gestionnaires de séance
  locaux, Renvoyer au groupe proposant pour corrections lorsque le point
  est dans une séance, Cacher les décisions au service pendant la
  rédaction du PV.
+ Etats des points décidés : permet de spécifier quels sont les états
  dans lesquels les points sont considérés comme "décidés". Ceci
  permettra de générer la liste des boutons permettant de décider
  plusieurs points d'une fois sur la vue d'une séance (voir bas de la
  page `Gestion du PV`_) et de spécifier dans quels états un point peut
  être "signé" si cette fonctionnalité est activée (voir `configuration
  de la Section "données"`_)
+ Transitions à confirmer : permet de sélectionner les transitions
  (sur le point et sur la séance) qui devront être confirmée. `Un
  "popup" apparaîtra et permettra de confirmer`_ qu'on souhaite bien
  effectuer la transition (par exemple "valider" un point), de plus, un
  commentaire pourra être encodé
+ Succession de transitions à effectuer pour présenter un point :
  permet de définir les étapes (transitions) a effectuer dans le
  workflow pour qu'un point se retrouve dans l'état "présenté",
  c'est-à-dire inséré dans une séance. Ceci est utile à certaines
  fonctionnalités de l'application
+ Adaptations à appliquer aux zones de texte riche d'un point lors
  d'une transition de workflow : via cette fonctionnalité, il est
  possible d'appliquer des changements à certaines zones de texte riche
  d'un point lorsque ce point change d'état. Par exemple lorsqu'un point
  est "reporté", ceci permet d'insérer automatiquement dans le champ
  "décision" une phrase par exemple "Les membres de la séance décident
  de reporter ce point."
+ Transitions à déclencher sur les points d'une séance lorsqu'une
  transition est déclenchée sur cette séance : cette fonctionnalité
  permet de déclencher des transitions sur les points lorsqu'une
  transition (changement d'état) est déclenchée sur une séance. Ceci va
  par exemple permettre de geler tous les points lorsque la séance est
  gelée ou d'accepter tous les points (non décidés) lorsqu'une séance
  est clôturée




4.3.7. Section "Interface utilisateur"
======================================




Cet écran permet de modifier des éléments qui influent sur l'interface
qu'aura l'utilisateur utilisant l'application :



Différents paramètres sont modifiable en cliquant sur l'icône [
Interface utilisateur ] :


+ États des séances conditionnant l'affichage de celles-ci dans la
  portlet 'séances' : états dans lesquels une séance apparaîtra dans la
  boîte d'informations "Séances" (ordres du jour).
+ États des séances conditionnant l'affichage de celles-ci dans la
  portlet 'décisions' : états dans lesquels une séance apparaîtra dans
  la boîte d'informations "Décisions" (PVs)
+ Nombre maximal de séances s'affichant dans les portlets 'séances' et
  'décisions' : nombre de séances s'affichant l'une en dessous de
  l'autre dans la boîte d'informations "Ordres du jour". Si le nombre
  est dépassé, une liste déroulante les affichera alors
+ Nombre maximum de jours durant lesquels les décisions apparaissent
  directement dans la portlet 'décisions' : nombre de jours durant
  lesquels un procès-verbal apparaîtra dans la boîte "PVs". Si le délai
  écoulé depuis la date d'une séance dépasse ce nombre de jours, la
  séance sera alors disponible via la lien "Tous les PVs" accessible au
  bas de la boîte "PloneMeeting" affichée lors de l'utilisation de
  l'application
+ Page d'accueil : lorsqu'un utilisateur clique sur l'onglet lié à la
  configuration de séance, il arrive sur la vue qui est sélectionnée
  dans cette liste déroulante. La liste propose toutes les recherches
  disponibles ("mes points", "tous les points", "les séances", ...)
  ainsi que certaines vues spécifiques
+ Colonnes à afficher dans les tableaux présentant des points :
  lorsqu'un utilisateur accède à une séance, des colonnes présentent des
  informations disponibles sur les points. Il est possible ici de
  sélectionner les colonnes qui seront affichées parmi : Point signé?, A
  évoquer en séance?, Créateur, Créé(e) le, Etat, Catégorie (ou groupe
  proposant), Groupe proposant, Acronyme du groupe proposant, Groupe(s)
  associé(s), Acronymes des groupes associés, Annexes, Annexes (à la
  décision), Avis, Niveau de confidentialité, Informations budgétaires
  et Actions. La colonne "Titre, description et décision" est affichée
  d'office
+ Colonnes à afficher sur les listes de points : lorsqu'un utilisateur
  accède à un tableau récapitulatif présentant des points ("mes points",
  "tous les points", ...), il est possible de définir quelles seront les
  colonnes affichées parmi : Point signé?, A évoquer en séance?,
  Créateur, Créé(e) le, Etat, Catégorie (ou groupe proposant), Groupe
  proposant, Acronyme du groupe proposant, Groupe(s) associé(s),
  Acronymes des groupes associés, Annexes, Annexes à la décision, Avis,
  Niveau de confidentialité, Informations budgétaires, Actions, Séance
  et Séance souhaitée
+ Nombre maximal de points à afficher dans la liste 'Points à
  présenter' : c'est le nombre de point maximum à afficher lorsqu'un
  gestionnaire de séance sélectionne les points à présenter dans une
  séance. Au delà, une `pagination apparaîtra`_. Si on ne souhaite pas
  de pagination, il suffit de mettre un nombre très élevé comme 999
+ Nombre maximal de points à afficher dans la liste 'Points présentés'
  : c'est le nombre maximum de points présentés dans une séance à
  afficher. Au delà, une pagination apparaîtra. Si on ne souhaite pas de
  pagination, il suffit de mettre un nombre très élevé comme 999
+ Nombre maximal de points à afficher dans la liste 'Points en retard'
  : c'est le nombre maximum de points en retard présentés dans une
  séance à afficher. Au delà, une pagination apparaîtra. Si on ne
  souhaite pas de pagination, il suffit de mettre un nombre très élevé
  comme 999
+ Activer la fonctionnalité 'Aller à la page' : cette fonctionnalité
  `fera apparaître un outil`_ permettant de naviguer facilement de page
  en page d'une séance. Ceci est utile si les séances comportent
  beaucoup de points (plus de 200 par exemple) et que la pagination les
  affiche par 50
+ Activer la fonctionnalité 'Aller au point' : cette fonctionnalité
  activera le `menu de navigation entre points`_ où c'est nécessaire
+ Ouvrir les annexes dans des fenêtres séparées : en activant cette
  fonctionnalité, toutes les annexes seront affichées dans des fenêtres
  séparées, ce qui permet d'éviter qu'une annexe s'ouvrant dans le
  navigateur (un fichier PDF par exemple) ne cache l'application
+ Champs des points à Afficher/masquer lors de l'utilisation de
  l'icône 'Lunettes' : cette zone permet de sélectionner les champs qui
  seront affichés dans les tableaux de points lors de l'utilisation de
  l'icône
+ Dossiers automatiques à afficher dans le portlet 'A faire' : une
  boîte d'informations "A faire" permet d'afficher aux utilisateurs des
  actions à effectuer. Il est ici possible de sélectionner des
  recherches (Dossiers automatiques) qui apparaîtront dans cette boîte.
  Il est par exemple possible d'afficher la recherche "Points à valider"
  aux validateurs de points, "Avis à donner" aux donneurs d'avis, ... Si
  aucune recherche n'est sélectionnée, la boîte est désactivée dans
  l'interface. Elle n'apparaît que si l'utilisateur en cours a une
  recherche le concernant




Ensuite, un tableau reprend les "Recherches pré-configurées" utilisées
dans les portlets "Gestion" :
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Un "recherche pré-configurée" affiche les résultats d'une recherche en
fonction de critères spécifiques : les points validés, avis à donner,
points en copie, ...
Ces dossiers automatiques sont affichés dans :


+ la boîte "Gestion", dans les Sections "Points", "Ordres du jour" et
  "Procès-verbaux"
+ la boîte "A faire"


Lors de l'ajout d'une recherche pré-configurée, il est possible de
définir les paramètres suivants :


+ Titre : c'est le titre qui apparaîtra dans les boîtes idoines
+ Se rapporte à (point ou séance) : il faut spécifier si c'est une
  recherche qui concerne des séances ou des points
+ Script de recherche : les dossiers automatiques permettent
  d'effectuer des recherches simples. Afin d'effectuer des recherches
  plus complexes, il est possible d'utiliser un script qui effectuera la
  recherche à la place du dossier automatique. Le dossier automatique se
  chargera de tout (titre, colonnes à afficher, ...) sauf de la
  recherche
+ Condition d'affichage : une condition d'affichage complexe. Ceci
  permettra par exemple d'afficher une recherche "Avis à donner" aux
  donneurs d'avis seulement et pas à tout le monde


*Attention, pour ces 3 derniers points, il faut passer par la ZMI. En
ajoutant "/manage_main" à un nouveau dossier automatique créé, on
passe dans la ZMI. Là, via l'onglet "Properties" (ou en ajoutant
"manage_propertiesForm" à la fin de l'url à la place de "manage_main"
si l'onglet "Properties" n'est pas visible), on peut ajouter une
propriété de type "string" nommée "meeting_topic_type" prenant les
valeurs "Meeting" ou "MeetingItem", ce qui spécifiera à quoi la
recherche se rapporte (recherche de "séances" ou de "points"). Le
script de recherche doit être ajouté dans une propriété de type string
nommée "topic_search_script". Quant à la condition d'affichage, elle
sera définie dans une propriété de type "string" nommée
topic_tal_expression.*




4.3.8. Section "Courriels"
==========================




Les notifications permettent de prévenir des utilisateurs en fonction
d'un événement survenu.





Des courriels peuvent être envoyé en fonction d'un événement
particulier survenant * sur un point * :


+ un point en retard vient d'être validé : dans ce cas, le
  gestionnaire de séance recevra un courriel le prévenant
+ un point a été inséré dans une séance : dans ce cas, le groupe
  proposant recevra un courriel
+ un point a été retiré d'une séance : dans ce cas, le groupe
  proposant recevra un courriel
+ un point a été reporté : dans ce cas, le groupe proposant recevra un
  courriel
+ une annexe a été ajoutée à un point qui était déjà présenté dans un
  ordre du jour : dans ce cas, tous les utilisateurs pouvant voir le
  point sont prévenus
+ un avis doit être rendu sur un point : dans ce cas, tous les
  utilisateurs pouvant donner un avis sur le point sont prévenus
+ un avis sur un point a été rendu ou modifié : dans ce cas, tous les
  utilisateurs pouvant voir le point sont prévenus
+ un avis a été invalidé sur un point : dans ce cas, tous les
  utilisateurs pouvant voir le point sont prévenus
+ un validateur souhaite évoquer un point : si un point utilisant
  l'attribut "A discuter?" n'était pas à discuter mais qu'il le devient,
  tous les utilisateurs pouvant voir le point sont prévenus
+ un point vient d'être envoyé vers cette configuration de séance : si
  la `fonctionnalité d'envoi d'un point d'un type de séance à l'autre`_
  (par exemple Collège communal vers Conseil communal) a été activée,
  lorsqu'un point est effectivement envoyé d'une séance à l'autre, les
  utilisateurs pouvant voir le point sont prévenus
+ une erreur est survenue lors de la conversion d'une annexe : si la
  fonctionnalité de prévisualisation des annexes est activée, si une
  erreur s'est produite lors de la conversion d'une annexe dans un
  format prévisualisable, les personnes pouvant ajouter des annexes à ce
  point sont prévenues
+ un point a été renvoyé pour correction au groupe proposant : `si
  l'adaptation du workflow "Renvoyer au groupe proposant pour
  corrections lorsque le point est dans une séance" est activée pour
  cette configuration de séance`_, un e-mail est envoyé au groupe
  proposant si un point leur est renvoyé pour correction
+ Un point corrigé par le groupe proposant a été renvoyé aux
  gestionnaires de séances : `si l'adaptation du workflow "Renvoyer au
  groupe proposant pour corrections lorsque le point est dans une
  séance" est activée pour cette configuration de séance`_, un e-mail
  est envoyé aux gestionnaires de séances lorsqu'un point qu'il avait
  renvoyé vers un groupe proposant pour correction leur revient corrigé
+ toutes les transitions possibles dans le workflow d'un point :
  "refuser", "retirer", "accepter", "remettre en proposé", ...




Des courriels peuvent être envoyé en fonction d'un événement
particulier survenant * sur une séance * :


+ toutes les transitions possibles dans le workflow d'une séance :
  "geler la séance", "clôturer la séance", ...






4.3.9. Section "Avis et accès"
==============================




Des avis peuvent être rendus par des services sélectionnés
(automatiquement ou non) sur des points :





+ Utiliser la gestion des avis : en cas d'activation, les "avis"
  apparaîtront en bas du point à côté des annexes et sur tous les
  tableaux affichant des points si la colonne "avis" a été sélectionnée
  dans la `configuration de séance, section "Interface utilisateur"`_
+ Etats des points dans lesquels on peut donner un avis : liste des
  états des points dans lesquels les avis demandés pourront être rendu
+ Etats des points dans lesquels on peut modifier ou supprimé un avis
  donné : liste des états des points dans lesquels les avis déjà rendus
  peuvent toujours être modifiés ou supprimés par le service ayant rendu
  l'avis
+ Etats des points dans lesquels les donneurs d'avis de ces points
  peuvent continuer à les voir : lorsqu'un avis a été donné par un
  groupe, il faut définir jusque quand le groupe peut continuer à voir
  le point. En effet, on pourrait par exemple montrer le point aux
  donneurs d'avis dans un certain état (validé par exemple) et le leur
  cacher par la suite ou lorsque le point est décidé
+ Types d'avis utilisés : liste des types d'avis qui pourront être
  utilisés : Positif, Positif avec remarques, Négatif et Néant
+ Type d'avis par défaut : le type d'avis qui sera sélectionné par
  défaut lorsqu'un avis sera rendu
+ Appliquer le caractère obligatoire des avis : quand le caractère
  obligatoire des avis est d'application, un point ne peut être inséré
  dans une séance à moins que tous les avis obligatoires n'aient été
  rendus et soient positifs
+ Activer l'invalidation des avis : quand l'invalidation des avis est
  activée, tout changement sur un point pour lequel au moins un avis a
  été rendu invalidera tous les avis rendus sur ce point. Par
  'changement', nous entendons toute modification du titre ou de la
  description du point ainsi que tout ajout et toute suppression
  d'annexe
+ Etats des points dans lesquels l'invalidation des avis est active :
  quand l'invalidation des avis est activée, cela l'est uniquement pour
  les points qui sont dans un des états sélectionnés ici
+ Styles des avis : permet de sélectionner le style des icônes à
  utiliser pour les avis
+ Transition qui remet à zéro les délais des avis avec délai :
  sélectionnez dans la liste une transition du WF du point qui permettra
  de remettre à zéro les délais déjà démarrés. Par exemple, si les
  délais ont démarré et que le point "retourne en arrière" dans le WF,
  par exemple en passant de l'état "validé" (où on peut rendre un avis)
  à l'état "proposé" (où on en peut pas rendre d'avis), cette transition
  "remettre en proposé" pourrait déclencher la remise à zéro des délais
  déjà démarrés
+ Configuration des avis particuliers : permet de définir les avis
  automatiquement demandés par l'application ainsi que les avis avec
  délai. Consultez l'aide affichée au dessus du champ dans l'interface
  utilisateur
+ Etats des points dans lesquels les 'Super observateurs' peuvent les
  voir : quand un point est dans un de ces états, les utilisateurs
  présents dans le groupe "Nom de ma configuration de séance (Super
  observateurs)" (dans la gestion des Utilisateurs et Groupes) pourront
  voir ce point
+ Etats des séances dans lesquels les 'Super observateurs' peuvent les
  voir : quand une séance est dans un de ces états, les utilisateurs
  présents dans le groupe "Nom de ma configuration de séance (Super
  observateurs)" (dans la gestion des Utilisateurs et Groupes) pourront
  voir cette séance
+ Etats des points dans lesquels les 'Gestionnaires d'informations
  budgétaires' peuvent modifier les informations budgétaires : quand un
  point est dans un de ces états, les utilisateurs présents dans le
  groupe "Nom de ma configuration de séance (Gestionnaires
  d'informations budgétaires)" pourront modifier le champ "Informations
  budgétaires"
+ Groupes considérés comme 'Super émetteurs d'avis' : les groupes
  PloneMeeting sélectionnés dans ce champ pourront rendre un avis sur un
  point même si leur avis n'a pas été demandé
+ Utiliser la gestion des points en copie : en cas d'activation,
  l'utilisateur pourra choisir des groupes auxquels donner une vue
  (lecture seule) à son point à un moment donné (défini dans le
  workflow).
+ Groupes qui pourront être mis en copie : les groupes sélectionnés
  ici pourront être choisis par un utilisateur lors de l'édition d'un
  point
+ Etats des points dans lesquels les groupes en copie peuvent les voir
  : quand un point est dans un de ces états, les groupes mis en copie
  sur le point peuvent alors y accéder en lecture seule
+ Cacher les commentaires dans l'historique d'un point aux
  utilisateurs ne faisant pas partie du groupe proposant : ceci permet
  de restreindre l'accès aux commentaires laissés lors d'un changement
  d'état d'un point aux membres du groupe proposant
+ Restreindre l'accès aux points à huis clos? : si activé, un point à
  huis clos ne sera accessible qu'aux utilisateurs qui ont reçu un accès
  spécifiquement : les super observateurs, les gestionnaires de séances,
  les groupes mis en copie, les groupes auxquels l'avis a été demandé,
  ...
+ Activer la confidentialité des annexes : si activé, il sera possible
  pour les gestionnaires de séances de spécifier si certaines annexes
  doivent être considérées "confidentielles" pour les niveaux de "super
  observateurs" sélectionnés dans le champ "Une annexe marquée
  'Confidentielle' ne sera pas visible par"
+ Activer la confidentialité des avis : si activé, un gestionnaire de
  séance pourra rendre confidentiel un avis rendu sur un point. Ceci
  cachera l'avis aux niveaux de "super observateurs" sélectionnés dans
  le champ "Un avis marqué 'Confidentiel' ne sera pas visible par"
+ Valeur par défaut du champ 'Confidentiel?' des avis créés : si la
  confidentialité des avis est utilisée, ceci permettra de spécifier si
  un nouvel avis est confidentiel ou non par défaut



Que permet la fonctionnalité de gestion des avis?

Les groupes sont sélectionnés soit manuellement par le créateur du
point soit automatiquement par l'application. Au moment opportun
(lorsque, par exemple, le point a été validé par le validateur de
points du groupe), les `avis pourront être rendus sur un point`_.

En outre, c'est dans cette partie de la configuration que les "Niveaux
d'accord" peuvent être spécifiés. Un niveau d'accord permet d'évaluer
rapidement les différents avis rendus (évaluation globalement positive
ou négative).

Que permet la fonctionnalité de mise en copie d'un point?

Les groupes mis en copie lors de la rédaction du point pourront voir
ce point au moment voulu (idéalement lorsqu'il a été validé par le
validateur du groupe). Cet accès est un accès en lecture seule ,
l'utilisateur ne pourra donc pas changer quoi que ce soit concernant
le point. Il peut par contre tout voir, annexes et avis compris.




4.3.10. Section "Votes"
=======================





La gestion des votes peut se faire en séance par les `utilisateurs
spéciaux votants`_ sélectionnés ou à tout moment par le gestionnaire
de séance :




Les paramètres modifiables sont :


+ Activer le système de vote : une fois activé, un écran de `gestion
  des votes apparaîtra sur les points`_ au moment adéquat
+ Qui encode les votes? : permet de spécifier si on souhaite que "Le
  votant lui-même" et/ou "Un gestionnaire de séance" puisse encoder les
  votes. Si "Le votant lui-même" est sélectionné, les votes pourront se
  faire en séance, si "Un gestionnaire de séance" gère les votes, il
  pourra le faire à tout moment
+ Valeurs de votes utilisées : il est possible d'activer différentes
  valeurs de vote : Pas encore encodé, Pour, Contre, Abstention, Ne vote
  pas, Bulletin non trouvé dans l'urne, Bulletin de vote invalide et
  Blanc
+ Valeur de vote par défaut : une des valeurs disponibles dans les
  "Valeurs de votes utilisées" peut être sélectionnée comme valeur par
  défaut. La valeur "Pas encore encodé" est utilisée par défaut
+ Condition de vote : permet d'ajouter une condition complexe
  d'activation des votes sur le point






4.3.11. Section "Utilisateurs" spéciaux
=======================================




Les `utilisateurs spéciaux de l'application permettent de personnifier
les membres`_ ayant un rôle spécifique sur une séance, par exemple un
membre d'assemblée, un signataire, un votant, ...



Via le bouton "En ajouter un(e)", on peut ajouter un utilisateur
spécial qui doit obligatoirement être lié à un utilisateur existant
dans Plone. Les paramètres enregistrés sur un utilisateur spécial sont
de 2 types et se retrouvent dans 2 onglets :


Paramètres définis si l'utilisateur a une fonction spécifique
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~



Un utilisateur spécial est caractérisé par :


+ Identifiant de l'utilisateur Plone correspondant : entré lors de la
  création de l'utilisateur spécial. Cet utilisateur aura alors des
  fonctionnalités supplémentaires dans l'application lorsqu'il sera
  connecté
+ Genre : permet de définir si l'utilisateur est un homme ou une femme
+ Fonction : il s'agit ici d'une zone de texte libre informative sur
  la fonction de la personne
+ Usages : l'utilisateur peut être * * *Membre de l'assemblée* ce qui
  permettra de le sélectionner dans les zones "Présents", "Absents (non
  excusés)" et "Excusés" d'une séance si ces champs optionnels sont
  activés. L'utilisateur peut également être * Signataire * et donc être
  sélectionnable pour apparaître dans les signataires possibles d'une
  séance (les signatures peuvent être inclues dans une impression de
  document). L'utilisateur peut être *Votant* . Si la fonctionnalité de
  gestion des votes est activée, et que les membres votants peuvent
  voter en séance, cet utilisateur en sera alors capable. L'utilisateur
  peut être défini comme A l'initiative d'un point , ce qui le fera
  apparaître dans la liste déroulante "A l'initiative d'un point"
  activable sur un point (champ optionnel du point)
+ Fonction des remplaçants de cet utilisateur : si cet utilisateur
  doit être remplacé pendant une séance, l'utilisateur remplaçant pourra
  obtenir une fonction temporaire lors de ce remplacement. C'est dans
  cette zone que cette fonction sera définie. Par exemple, si
  l'utilisateur est "Secrétaire communal", l'utilisateur remplaçant
  pourrait être "Secrétaire communal ff"
+ Signature scannée : dans le cadre ou l'utilisateur est signataire,
  on peut insérer une image (scan) de sa signature, ce qui permettra de
  la faire apparaître à l'endroit souhaité
+ Cette signature est la signature par défaut : permet de spécifier si
  cet utilisateur doit être sélectionné comme signataire d'office pour
  la séance


Ces paramètre sont utilisés dans l'application pour la gestion des
membres (assemblée, signataires, votes, ...)



Préférences
~~~~~~~~~~~

`Si elles sont activées dans la configuration générale de
l'application`_, lorsqu'un utilisateur connecté dans l'application
accèdera à ses préférences via l'icône qui apparaît dans la boîte
"PloneMeeting", un Utilisateur spécial sera alors créé et permettra à
l'utilisateur de définir ses préférences. Cet utilisateur n'ayant
aucun "Usage" par défaut, il ne sera pas sélectionnable dans les
listings du type "Présents", "Signataires", ... Sauf si nécessaire. En
effet, un membre d'assemblée pourrait également être un utilisateur de
l'application avec des préférences personnelles... Les préférences de
l'utilisateur surchargeront certains paramètres définis dans la
configuration :







4.3.12. Section "Génération de documents"
=========================================




Différents documents peuvent être générés sur les points et les
séances d'une configuration de séance :



Les documents sont des modèles `OpenOffice`_ intégrant des expressions
liées à la librairie `appy.pod`_.

Lorsqu'un modèle a été écrit, on peut alors l'ajouter ici et définir
certaines zones qui permettront de savoir où, quand et par qui la
possibilité de générer ce document doit être disponible.

Lors de l'ajout, il faudra définir :


+ Titre : libellé du document ("Ordre du jour" par exemple)
+ Description : description qui sera affichée au survol du modèle sur
  un point ou une séance
+ Canevas POD : le modèle de document au format OpenOffice
+ Format dans lequel vous pouvez générer des documents depuis ce
  canevas : il est possible de spécifier si on souhaite que le document
  généré le soit au format PDF, au format ODT (OpenOffice), au format
  Word ou au format RTF. Ceci pourrait encore être étendu si nécessaire
  car la librairie est capable de générer tous les format qu'OpenOffice
  est capable de produire
+ Condition : une expression qui permet de spécifier quand le modèle
  doit apparaître. Le modèle ne doit apparaître par exemple que sur un
  point, ou que sur une séance en création, ou uniquement si
  l'utilisateur à tel rôle, ...
+ Permission(s) : une permission que l'utilisateur doit avoir pour
  générer : par exemple, l'utilisateur doit pouvoir modifier une séance
  pour imprimer l'Ordre du jour
+ Événement provoquant le gel des documents : il est possible de geler
  un document dans un état particulier pour être certain d'en obtenir la
  version voulue même si certaines données ont été modifiées dans le
  système par après. On pourrait par exemple geler l'Ordre du jour à un
  moment précis mais permettre via un autre Canevas d'imprimer une
  version courante de l'Ordre du jour
+ Listes de diffusion : définissez ici des listes de personnes à qui
  envoyer par courriel les fichiers générés depuis ce canevas. L'icône
  apparaîtra à côté du canevas de document à générer sur le point ou la
  séance. Au clic, le modèle généré sera alors envoyé aux utilisateurs
  définis dans cette liste de diffusion






4.4. Points particuliers dans la configuration
==============================================

Mise en évidence de différents points de la configuration



4.4.1. Colorisation des intitulés
=================================




Il est possible de coloriser les points :


+ en fonction de l'état du workflow défini sur l'élément ("en
  rédaction", "proposé", etc.)
+ en fonction des modifications effectuées sur l'élément depuis la
  dernière visualisation de celui-ci
+ de ne pas coloriser : tous les éléments apparaissent alors en bleu
  (couleur lien par défaut)



Afin d'activer la colorisation et de choisir le mode désiré, il faut
se positionner dans la `configuration générale de PloneMeeting`_,
cliquer sur l'onglet "Modifier" et adapter le paramètre "Système de
colorisation utilisé".

Il est également possible de désactiver la colorisation pour certains
utilisateurs. Il faut dès lors entrer dans la zone du dessous
l'identifiant de ceux-ci.

Si le mode de colorisation suivant l'état est choisi, les intitulés de
points sont alors colorisés dans tous les écrans suivant leur état
("en création" en rouge, "proposé" en orange, "accepté" en vert, ...).
Il s'agit du mode de colorisation recommandé :



Les couleurs des états sont adaptables via des fichiers de
configuration CSS.


Si le mode de colorisation suivant les modifications est choisi, les
intitulés de points sont dès lors colorisés dans tous les écrans en
fonction d'une modification éventuelle sur le point depuis la dernière
visualisation par l'utilisateur courant. Un point ayant reçu une
modification apparaîtra en rouge, les autres en bleu. Idem concernant
les annexes :






4.4.2. Utiliser les catégories
==============================




Il est possible de catégoriser les points suivant différents modes, en
fonction du niveau de catégorisation souhaité :


+ catégoriser en fonction du groupe proposant
+ catégoriser en fonction de catégories définies dans la configuration
+ catégoriser en fonction des classificateurs , système utilisé si
  vous avez beaucoup de catégories





Catégorisation simple via le groupe proposant ou les catégories
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

La catégorisation en fonction du groupe proposant est le mode activé
par défaut.

La catégorisation par groupe ou par catégorie est configurable dans
`la partie "Données" `_ d'une configuration de séance. Le paramètre à
prendre en compte est "Utiliser les groupes comme catégories"

Si les groupes sont utilisés comme catégories, les "Catégories de
points" définies dans la partie "Données" d'une configuration de
séance ne seront pas activées lors de la création d'un point et c'est
le groupe proposant seul qui catégorisera le point.

En décochant le paramètre "Utiliser les groupes comme catégories", une
catégorie peut alors être sélectionnée lors de la création ou
l'édition de chaque point dans une liste déroulante. Cette catégorie
apparaît également dans les écrans récapitulatifs affichant des
points. Ce fonctionnement est adapté si vous avez peu de catégories.
L'utilisation des classificateurs (voir ci-dessous) sera adaptée si
vous avez beaucoup de catégories à utiliser.

Certains paramètres dépendent du type de catégorisation choisi tels
que la `"Méthode de tri utilisée lors de l'ajout d'un point dans une
séance"`_ ou la `génération en format bureautique`_ qui peut également
tenir compte des catégories dans l'expression liée.



Catégorisation complexe grâce aux classificateurs
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Si on souhaite une gestion avancée de la catégorisation, on pourra
alors utiliser les classificateurs.

A cette fin, il faudra d'abord `activer l'attribut "Classificateur"`_
dans la liste des "Attributs utilisés pour caractériser un point" et
définir alors les classificateurs à utiliser.

Il suffit d'ajouter des classificateurs dans la partie "Données" de la
configuration de séance via le . La différence avec les catégories est
le "widget" (représentation graphique dans l'application lorsque
l'utilisateur créateur de point sélectionnera un "classificateur") qui
est adapté lorsque beaucoup de catégories (classificateurs dans ce
cas) sont disponibles. Une pagination, une zone de recherche "full-
text", ... permettent de trouver rapidement la catégorie à laquelle
lier l'élément :



Le niveau de catégorisation peut évoluer au fil de l'utilisation de
l'application. On pourra par exemple commencer avec une catégorisation
simple sous forme de groupe proposant et utiliser par la suite les
catégories de points ou les classificateurs si le besoin apparaît.




4.4.3. Canevas de documents
===========================




Les canevas de documents sont utilisés pour définir des modèles
d'impression utilisés lors de la génération en format bureautique.
`Ces canevas peuvent être ajoutés et modifiés dans la configuration
d'une séance, dans la partie "Documents"`_

Il est également possible de changer l'état du canevas pour le rendre
inactif, afin de ne plus afficher ce canevas.

Les canevas apparaissent dans la zone supérieure droite des écrans de
visualisation d'un point ou d'une séance (voir `Visualisation d'un
point`_ ou les canevas "Projet délibération" au format PDF et
OpenOffice apparaissent).

Le fichier .odt (écrit avec OpenOffice) qui est chargé doit inclure
des fonctions spéciales qui permettent d'insérer automatiquement par
après les éléments voulus.
Ces fonctionnalités particulières du document .odt utilisent la
librairie python "appy.pod" décrite sur `http://appyframework.org`_.




4.4.4. Gestion des points prédéfinis (points récurrents et modèles de
points)
=======



Les points prédéfinis permettent de gérer 2 aspects :


+ les points récurrents (`insérés automatiquement dans une séance`_)
+ les modèles de points (`utilisés lors de la création d'un nouveau
  point`_)





Les points récurrents
~~~~~~~~~~~~~~~~~~~~~

Les points récurrents sont définis au bas de la `section "Données"`_.
Une zone particulière apparaîtra au bas du formulaire du point
récurrent, il s'agit de la zone "Transition de la séance qui déclenche
l'ajout de ce point en tant que point récurrent". Il faudra
sélectionner dans cette liste la transition déclenchée sur la séance
qui va induire l'insertion du point récurrent. Par exemple, "Lors de
la création" ou lors de la transition "Geler".


Les modèles de points
~~~~~~~~~~~~~~~~~~~~~

Un lien vers la gestion des modèles de points est disponible au bas de
la `section "Données"`_. Une zone particulière apparaîtra au bas du
formulaire du modèle de point permettant de restreindre ce modèle à
l'un ou l'autre groupe. Si aucun groupe n'est sélectionné, le modèle
de point sera utilisable par tous les services.





4.4.5. Désactivation de certains éléments de la configuration
=============================================================



Lorsque l'application vit, petit à petit, certains éléments dans la
configuration pourront être désactivés pour refléter l'évolution des
besoins.

Dans la configuration, il sera possible de supprimer ou de désactiver
:


+ les configuration de séance (Collège, Conseil, ...)
+ les groupes PloneMeeting
+ les types d'annexes (onglet "Données" d'une configuration de séance)
+ les catégories (onglet "Données" d'une configuration de séance)
+ les classificateurs (onglet "Données" d'une configuration de séance)
+ les points prédéfinis (onglet "Données" d'une configuration de
  séance)
+ les recherches préconfigurées (onglet "Interface" d'une
  configuration de séance)
+ les utilisateurs (onglet "Utilisateurs" d'une configuration de
  séance)


Dès qu'un élément est utilisé, il ne sera plus possible de le
supprimer . Par exemple, si un groupe PloneMeeting a déjà créé un
point ou si une catégorie a déjà été utilisée sur un point, cet
élément ne pourra plus être supprimé, par contre il pourra toujours
être désactivé .


Désactiver un élément
`````````````````````

L'intérêt de désactiver un élément plutôt que de le supprimer ou de le
modifier est de garder un historique cohérent. Par exemple, si un
groupe s'appelait "Secrétariat communal", si son nom change au profit
de "Direction générale", il ne faudra idéalement pas le renommer mais
plutôt le désactiver, afin que les anciens points continuent à
utiliser l'ancienne appellation et en créer un nouveau qui pourra être
utilisé pour la suite.

Lorsqu'un groupe est désactivé , tous les membres de ses sous-groupes
Plone (le sous-groupe "créateurs", le sous-groupe "validateurs", ...)
sont automatiquement transférés dans le sous-groupe "Observateurs"
afin que les membres de ces groupes puissent toujours voir les anciens
points mais ne puissent plus en créer ou donner un avis au nom de cet
ancien groupe.



5. Accès à PloneMeeting par Web Services
========================================





5.1. Qu'est ce que les Web Services PloneMeeting?
=================================================



Les Web Services dans PloneMeeting permettent à n'importe quelle
application externe d'accéder à PloneMeeting. En fonction de
l'utilisateur défini pour se connecter à PloneMeeting, il sera
possible de visualiser, chercher ou créer un point. Le standard
SOAP/WSDL est utilisé. Il s'agit du standard Web Services le plus
répandu et il permet donc d'offir un accès à PloneMeeting depuis le
plus large panel de technologies existantes.

Actuellement, les Web Services sont utilisés par différentes
applications pour accéder à PloneMeeting, qu'il s'agisse
d'applications Plone ou autre (.net, C#, ...)

Voici quelques cas d'utilisation possibles pour différentes
applications appelantes :


+ PloneMeeting : envoyer un point vers un autre PloneMeeting, comme
  par exemple le passage d'un point du BP du CPAS vers le Collège
  Communal
+ 3P : passage d'un marché public au Collège ou Conseil Communal
+ urban : dans la procédure "Permis d'urbanisme" par exemple, un
  passage au Collège Communal est requis
+ GED : pouvoir passer un courrier entrant au Collège ou Conseil
  Communal
+ ...




5.2. Accès aux méthodes publiées SOAP/WSDL du serveur Web Services
==================================================================





5.2.1. Présentation
===================



Il est possible d'accéder à PloneMeeting via Web Services utilisant le
standard SOAP/WSDL.

Pour cela, l'application PloneMeeting doit être configurée pour
accepter des connexions entrantes (appels aux méthodes publiées) et
publier un descriptif WSDL d'accès à ces méthodes. Techniquement, le
package imio.pm.ws doit être configuré et installé.

Une fois le package installé, le fichier WSDL (ws4pm.wsdl) est
disponible et décrit l'accès aux méthodes suivantes :


+ ` test de connexion (testConnection)`_ : permet de tester si le
  paramètres d'identification renseigné (nom d'utilisateur/mot de passe)
  sont corrects
+ ` obtention d'informations sur la configuration (getConfigInfos)`_ :
  retourne différentes informations sur la configuration utilisée
+ ` obtention d'informations sur un utilisateur (getUserInfos)`_ :
  retourne des informations concernant l'accès de cet utilisateur
+ ` obtention d'informations sur un point (getItemInfos)`_ : retourne
  des informations pour un point en particulier
+ ` recherche de points (searchItems)`_ : effectue une recherche de
  points
+ ` savoir si un élément a déjà été envoyé (checkIsLinked)`_ : permet
  de savoir si un élément à déjà été créé
+ ` obtenir un document généré (getItemTemplate)`_ : permet de
  déclencher la production d'un document dans PloneMeeting
+ ` créer un point (createItem)`_ : permet de créer un point dans
  PloneMeeting




Toutes ces méthodes ne sont accessibles que si l'appel au Web Service
contient les informations de connexion d'un utilisateur PloneMeeting.
Les différentes actions ne pourront être faites que si l'utilisateur
renseigné dans l'authentification en a le droit dans PloneMeeting...



5.2.2. Test de connexion (testConnection)
=========================================



Cette méthode permet de vérifier si les données de connexion
renseignées pour accéder au Web Services sont correctes.

Paramètres d'entrées :

Aucun

Sortie :

Retourne "1" si la connexion a pu être établie, "0" sinon



5.2.3. Obtention d'informations sur la configuration (getConfigInfos)
=====================================================================



Cette méthode permet d'obtenir des informations concernant la
configuration mise en place sur PloneMeeting. Ceci permet de connaître
notamment les identifiants à utiliser lors du passage de certains
paramètres pour les méthodes de `création de point`_, `recherche de
points`_, ...

Paramètres d'entrées :

*showCategories* : (obligatoire) "1" pour montrer les catégories et
"0" pour ne pas les montrer. En fonction de la configuration, la
catégorie utilisée pour un point est soit le groupe proposant, soit
une catégorie supplémentaire. Si les catégories supplémentaires sont
utilisées, elles seront affichées, sinon, rien ne sera affiché au
niveau des catégories. *Si les catégories sont utilisées/affichées, le
passage de l'identifiant de la catégorie à utiliser est obligatoire
lors de la création d'un point.*
*userToShowCategoriesFor* : (optionnel) dans PloneMeeting, certaines
catégories peuvent être restreintes à certains groupes d'utilisateurs.
Pour être sûr qu'un utilisateur peut utiliser une catégorie donnée, on
peut passer "l'identifiant de cet utilisteur" à la méthode pour
retourner la liste exhaustive que l'utilisateur peut effectivement
utiliser.

Sortie :

Retourne la liste des Configuration de séances (MeetingConfig), des
groupes PloneMeeting (MeetingGroup) et des catégories (categories) si
le paramètre "showCategories" était à "1" lors de l'appel et si elles
sont effectivement utilisées par la Configuration de séance.



5.2.4. Obtention d'informations sur un utilisateur (getUserInfos)
=================================================================



Cette méthode permet d'obtenir des informations sur un utilisateur.

Paramètres d'entrées :

*userId* : (obligatoire) l'identifiant de l'utilisateur.
* showGroups * : (obligatoire) montrer les groupes PloneMeeting
auxquels l'utilisateur appartient (tous "sous-groupes Plone"
confondus). "1" pour montrer les groupes et "0" pour ne pas les
montrer.
* suffix * : (optionnel) paramètre utilisé conjointement avec le
paramètre "showGroups" à "1". Le suffixe d'un "sous-groupe Plone" doit
être renseigné. Les groupes retournés pour l'utilisateur seront ceux
pour lesquels l'utilisateur est dans le sous-groupe mentionné.
Les suffixes par défaut sont :


+ creators : retourne les groupes pour lesquels l'utilisteur est un
  créateur de points
+ reviewers : retourne les groupes pour lesquels l'utilisateur est un
  validateur de points
+ advisers : retourne les groupes pour lesquels l'utilisateur est un
  donneur d'avis


D'autres suffixes peuvent exister en fonction de la configuration
spécifique de PloneMeeting

Sortie :

Retourne les infos sur l'utilisateur : "Nom complet" et "Adresse
e-mail". Si "showGroups" était à "1", retourne également la liste des
groupes PloneMeeting (MeetingGroup) adéquats.



5.2.5. Obtention d'informations sur un point (getItemInfos)
===========================================================



Cette méthode permet d'obtenir des informations sur un point. A
utiliser si on connaît l'UID du point pour lequel on souhaite des
informations. On connaît l'UID d'un point si on a `créé ce point via
la méthode createItem`_ des Web Services ou lors d'une `recherche de
points`_.

Paramètres d'entrées :

*UID* : (obligatoire) l'identifiant universel du point.
*showExtraInfos* : (obligatoire) valeur à "0" ou "1". Montre
d'avantages d'informations concernant le point. Laisser à "0" si ces
informations supplémentaires ne sont pas nécessaires.
* showAnnexes * : (obligatoire) valeur à "0" ou "1". Montre les
annexes du point. Laisser à "0" si pas nécessaire car les fichiers
annexes retournés peuvent ralentir la réponse en fonction de la taille
de ceux-ci...
* showTemplates * : (obligatoire) valeur à "0" ou "1". Montre les
documents générables pour ce point.

Sortie :

Retourne les infos sur le point (informations principales + étendues
si spécifié). Affiche la liste des annexes si spécifié (avec fichier).
Affiche la liste des document générables (sans le fichier, passer par
`l'obtention d'un document généré (getItemTemplate)`_ pour obtenir le
fichier).



5.2.6. Recherche de points (searchItems)
========================================



Cette méthode permet d'effectuer une recherche de point sur base de
plusieurs critères de recherche.

Paramètres d'entrées :

*Critères de recherche* : (obligatoire) différents critères peuvent
être utilisés : créateur, titre, description du point, décision du
point, ...
*externalIdentifier* : (optionnel) ce paramètre permet de passer un
identifiant externe. Lorsqu'un `point est créé (createItem)`_ par une
application externe via ces Web Services, un "identifiant externe"
peut être spécifié et permet dès lors de retrouver le point par la
suite. Plusieurs points peuvent recevoir le même "identifiant
externe".
* inTheNameOf * : (optionnel) effectuer la recherche "au nom d'un
utilisateur". Nécessite d'être connecté en tant que
"Manager/MeetingManager" au Web Services. Effectue une recherche avec
les privilèges de l'utilisateur donné.

Sortie :

Retourne les infos sur le point (informations principales uniquement).

Si on a besoin de plus d'informations sur le point, il faut passer par
la méthode `d'obtention d'informations sur un point (getItemInfos)`_ :


+ effectuer une recherche
+ récupérer les UIDs des éléments trouvés
+ les passer à `getItemInfos`_.






5.2.7. Savoir si un élément a déjà été envoyé (checkIsLinked)
=============================================================



Cette méthode permet de savoir si un élément appelant a déjà été
envoyé vers PloneMeeting, à condition que `lors de la création du
point`_ dans PloneMeeting, l'élément appelant ai soit passé un
"identifiant externe", soit stocké l'UID du point créé.

Paramètres d'entrées :

*meetingConfigId* : (optionnel) l'identifiant d'une Configuration de
séance. Permet de savoir par exemple si un élement a été envoyé vers
un type de séance et pas un autre...
*externalIdentifier* : (obligatoire) il s'agit de la clé qui lie le
point créé dans PloneMeeting à la procédure ayant créé ce point.

Sortie :

Retourne "isLinked" à "1" si un point correspondant a été trouvé, "0"
sinon.





5.2.8. Obtenir un document généré (getItemTemplate)
===================================================



Cette méthode permet d'obtenir un document généré pour un point donné.

Paramètres d'entrées :

*itemUID* : (obligatoire) l'identifiant UID du point pour lequel
générer le document. Cet identifiant peut être connu en passant par la
`recherche de points`_ ou lorsque le point a été créé via les Web
Services.
*templateId* : (obligatoire) l'identifiant du document à générer. Cet
identifiant peut être connu lors de` l'obtention d'informations sur un
point`_ si le paramètre "showTemplates" est à "1".
* inTheNameOf * : (optionnel) utiliser la méthode "au nom d'un
utilisateur". Nécessite d'être connecté en tant que
"Manager/MeetingManager" au Web Services.

Sortie :

Retourne le document généré.





5.2.9. Créer un point (createItem)
==================================



Cette méthode permet de créer un nouveau point dans PloneMeeting.

Paramètres d'entrées :

*meetingConfigId* : (obligatoire) l'identifiant de la configuration de
séance dans laquelle créer le point.
*proposingGroupId* : (obligatoire) l'identifiant du groupe proposant
avec lequel créer le point.
* creationData * : une série de données de base pour créer le point :
titre (obligatoire), catégorie (obligatoire si catégories utilisées
par la meetingConfigIf), description (optionnel), décision
(optionnel), identifiant externe (optionnel), annexes (optionnel).
* inTheNameOf * : (optionnel) utiliser la méthode "au nom d'un
utilisateur". Nécessite d'être connecté en tant que
"Manager/MeetingManager" au Web Services.

Sortie :

Retourne l'UID du point créé. Cette informations pourra être stockée
par la procédure appelante afin de pouvoir retrouver le point par la
suite. Si la procédure appelante ne souhaite pas stocker cet UID, un
"identifiant externe" passé dans le creationData ci-dessus à la même
utilité mais stocke alors dans PloneMeeting un identifiant provenant
de la procédure appelante... Une série d'avertissements (warnings)
peut également être retournée : HTML utilisé non valide (donc
corrigé), annexe passée non valide, ...



5.3. Utilisation du client Web Services Plone
=============================================





5.3.1. Présentation
===================



Un client de connexion aux Web Services PloneMeeting a été développé
pour faciliter l'intégration d'une application * Plone * appelante. Ce
module, imio.pm.wsclient permet donc à une application * Plone *
souhaitant créer/obtenir de l'informations/... sur un point dans un
PloneMeeting distant de le faire de manière transparente :


+ un panneau de configuration permet de spécifier les données de
  connexion et les données à envoyer au PloneMeeting
+ une action est automatiquement configurée pour créer un point dans
  PloneMeeting
+ une zone affiche localement les informations récupérées dans
  PloneMeeting si disponibles




Techniquement, ce client SOAP/WSDL utilise la librairie python *suds*
pour accéder au PloneMeeting distant.



5.3.2. Panneau de configuration
===============================



Le client se caractérise principalement par un panneau de
configuration :



La partie configuration permet de définir d'une part les informations
de connexion, et d'autre part, comment vont être extraite de
l'application Plone courante, les informations à envoyer à
PloneMeeting. Sur chaque zone de la configuration, un message d'aide
explique comment l'utiliser.


+ URL du fichier WSDL PloneMeeting : il s'agit de l'adresse de
  PloneMeeting sur lequel est activé les Web Services. Pour obtenir
  l'url du WSDL, il suffit d'ajouter à la suite de l'URL de base de
  PloneMeeting, le nom du fichier WSDL "ws4pm.wsdl"
+ Timeout de connexion à PloneMeeting : entrez le timeout de connexion
  à PloneMeeting. Si sur une page de l'application appelant
  PloneMeeting, des informations doivent être affichées, ceci permet de
  ne pas attendre plus que le nombre de secondes définies si
  éventuellement le PloneMeeting distant était inaccessible
  momentanément.
+ Nom d'utilisateur à utiliser dans PloneMeeting : nom d'utilisateur
  pour la connexion. L'utilisateur doit pouvoir accéder à suffisamment
  de fonctionnalités dans PloneMeeting en fonction de ce que
  l'application appelante souhaite pouvoir envoyer. Il n'est pas
  nécessaire qu'il s'agisse d'un administrateur dans PloneMeeting mais
  un utilisateur ayant le rôle "MeetingManager". Il peut être utile
  d'ajouter un utilisateur dans PloneMeeting destiné à être utilisé
  uniquement pour la connexion Web Services. Par exemple ajouter un
  utilisateur "wsmanager" dans PloneMeeting et lui donner le rôle
  "MeetingManager".
+ Mot de passe à utiliser dans PloneMeeting : mot de passe de
  l'utilisateur renseigné au champ précédent.
+ Condition d'affichage du viewlet : le viewlet est la zone dans
  l'application appelante dans laquelle seront affichées les
  informations relatives à PloneMeeting s'il y en a. Vous pouvez définir
  ici une condition qui permet de cacher la zone à certains utilisateurs
  par exemple. Par défaut, si laissée vide, la zone s'affichera si la
  page appelante est liée à un point dans PloneMeeting, elle ne sera pas
  affichée si aucune information provenant de PloneMeeting n'est à
  afficher.
+ Correspondances pour les champs : pour chaque données à envoyer,
  vous pouvez définir une expression TAL qui fait correspondre à
  l'élément à envoyer, la valeur à utiliser pour un champ dans
  PloneMeeting. Ceci signifie que pour le contexte appelant, il faudra
  définir quelles méthodes retourne les données à envoyer dans
  PloneMeeting.
+ Correspondances pour les nom d'utilisateurs : comme les noms
  d'utilisateurs dans l'application appelante peuvent être différents
  des noms d'utilisateurs dans PloneMeeting, ce champ permet de définir
  une correspondance de noms d'utilisateurs. Par facilité, essayez de
  définir dans l'application appelante et dans PloneMeeting des
  utilisateurs avec la même logique : par exemple première lettre du
  prénom + nom le tout en majusucule : "Philippe Durant" devenant
  "pdurant"...
+ Actions générées : permet de générer une action dans l'application
  appelante qui pourra être facilement déclenchée (apparaîtra dans le
  menu déroulant "Actions"). Cette action peut être en outre protégée
  par une condition, une permission, et renseignera aussi dans quelle
  configuration de séance le point sera créé




A l'enregistrement de la configuration, les actions disponibles dans
l'interface utilisateur et basées sur le champ "Actions générées" sont
mises à jour : créées, modifiées ou supprimées.





5.3.3. Envoyer vers PloneMeeting
================================





Actions générées
~~~~~~~~~~~~~~~~

Lorsque la configuration a été sauvegardée et que des "`Actions
générées`_" ont été définies, celle-ci apparaîtront, dans le menu
"Actions" à l'endroit souhaité, dépendant de la condition et de la
permission renseignées dans l'action générée. Ici par exemple, deux
actions ont été définies :




Envoyer vers un type de séance
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Au clic sur une de ces actions, un formulaire apparaît et montre à
l'utilisateur les données qui vont être envoyées vers PloneMeeting
pour créer le point. En fonction de ce qui est défini dans la
configuration dans la partie "`Correspondance pour les champs`_", les
données sont extraites de l'élément appelant pour être envoyées à
PloneMeeting. Un écran intermédiaire montre à l'utilisateur ce qui va
être envoyé à PloneMeeting :



En fonction de la manière dont le type de séance (Conseil Communal
dans notre exemple) est configuré dans PloneMeeting, divers champs
peuvent apparaître ou non. C'est le cas par exemple du champ
"Catégorie" qui n'apparaît que si la configuration de séance dans
PloneMeeting utilise les catégories...

Un fois envoyé dans PloneMeeting, les infos provenant de PloneMeeting
sont affichées au dessus de l'élément depuis lequel le point a été
créé.



5.3.4. Visualiser le point créé dans PloneMeeting depuis l'application
appelante
=========



Une fois que le point a été créé dans PloneMeeting, un lien est gardé
avec ce dernier et les informations concernant ce point sont affichées
dans une zone (viewlet) au dessus de l'élément ayant déclenché l'envoi
du point. Dans notre exemple il s'agit d'une page par défaut
(Document) d'un site Plone de base, mais il pourrait s'agir d'un type
de contenu spécifique d'une application (urban, PloneMeeting, GED,
...).

Lorsqu'un élément est lié à un(des) point(s) dans PloneMeeting, les
informations concernant ce(s) dernier(s) sont affichées :



Différentes informations clés sont affichées et un lien direct vers le
point dans PloneMeeting est disponible en cliquant sur le "Titre". Il
est en outre possible de voir directement dans quel état est le point,
s'il est dans une séance et de générer un document bureautique lié
(Projet de délibération, Délibération, ...)

