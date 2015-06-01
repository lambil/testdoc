Modèle de Site web 
++++++++++++++++++

Gérer le contenu d'une page
===========================

1. Créer une page
=================


` `_Après avoir doté son site d'une navigation constituée de dossiers,
il convient de créer des pages "documents"pour ajouter du contenu
(texte, photos, ...) au site Internet.




Une fois le document créé, il faut lui donner un titre et utiliser la
zone "corps du texte" pour réaliser la page web.
La barre d'outils propose les actions de base que l'on retrouve dans
un éditeur de texte classique (Openoffice, Word,...).

Quelques fonctionnalités méritent de s'y arrêter:

L'édition en "pleine page" permet d'avoir toujours le menu de
l'éditeur sous les yeux.

L'utilisation de "modèles" permet d'importer des "structures de pages"
prédéfinies.







2. Copier coller du texte
=========================



L'édition d'une page est une opération simple grâce à l'éditeur html.
Il faut cependant être attentif à éviter certains écueils.



1. Le copier coller
-------------------
Il est possible de copier du texte et de le coller dans l'éditeur. Il
faut toutefois prêter attention au fait de ne pas polluer le code html
de la page avec des balises générées par l'éditeur d'origine.

Voici un exemple de code html d'un texte copié de Word:

::

    
    <!--[if gte mso 9]><xml>
    <w:WordDocument>
    <w:View>Normal</w:View>
    <w:Zoom>0</w:Zoom>
    <w:HyphenationZone>21</w:HyphenationZone>
    <w:PunctuationKerning />
    <w:ValidateAgainstSchemas />
    <w:SaveIfXMLInvalid>false</w:SaveIfXMLInvalid>
    <w:IgnoreMixedContent>false</w:IgnoreMixedContent>
    <w:AlwaysShowPlaceholderText>false</w:AlwaysShowPlaceholderText>
    <w:Compatibility>
    <w:BreakWrappedTables />
    <w:SnapToGridInCell />
    <w:WrapTextWithPunct />
    <w:UseAsianBreakRules />
    <w:DontGrowAutofit />
    </w:Compatibility>
    <w:BrowserLevel>MicrosoftInternetExplorer4</w:BrowserLevel>
    </w:WordDocument>
    </xml><![endif]--><!--[if gte mso 9]><xml>
    <w:LatentStyles DefLockedState="false" LatentStyleCount="156">
    </w:LatentStyles>
    </xml><![endif]--><!--[if gte mso 10]>
    <style>
    /* Style Definitions */
    table.MsoNormalTable
    {mso-style-name:"Tableau Normal";
    mso-tstyle-rowband-size:0;
    mso-tstyle-colband-size:0;
    mso-style-noshow:yes;
    mso-style-parent:"";
    mso-padding-alt:0cm 5.4pt 0cm 5.4pt;
    mso-para-margin:0cm;
    mso-para-margin-bottom:.0001pt;
    mso-pagination:widow-orphan;
    font-size:10.0pt;
    font-family:"Times New Roman";
    mso-ansi-language:#0400;
    mso-fareast-language:#0400;
    mso-bidi-language:#0400;}
    </style>
    <![endif]-->
    <h1>Modalités pour obtenir une carte d'identité :</h1>
    <p class="MsoNormal"> </p>
    <p class="MsoNormal"><b style="mso-bidi-font-weight:normal">Attention, depuis le premier décembre 2005, 
     il est possible,
     via nos services, de recevoir une carte d'identité électronique en urgence</b>.</p>
    <p class="MsoNormal"> </p>
    <p style="margin-left:19.5pt;text-indent:-19.5pt;mso-list:l0 level1 lfo1;
    tab-stops:list 19.5pt" class="MsoNormal"><span style="font-size:18.0pt"><span style="mso-list:Ignore">1)
    <span style="font:7.0pt "Times New Roman"">   </span></span></span><span style="font-size:18.0pt">
    Cartes d’identité électroniques pour les personnes de plus de 12 ans.</span></p>
    <p class="MsoNormal"><span style="font-size:18.0pt"> </span></p>
    <ul type="disc" style="margin-top:0cm">
        <li style="mso-list:l1 level1 lfo2;tab-stops:list 36.0pt" class="MsoNormal">une  convocation parvient à votre
     domicile, vous invitant à vous présenter en      nos locaux.</li>
        <li style="mso-list:l1 level1 lfo2;tab-stops:list 36.0pt" class="MsoNormal">se munir d’une photo 
    d’identité sur fond blanc et de 15 €.</li>
        <li style="mso-list:l1 level1 lfo2;tab-stops:list 36.0pt" class="MsoNormal">le délai d’obtention
     est de +/- 3 semaines.</li>
    </ul>


Le même texte débarassé du code lié à l'éditeur:


::

    
    <h2>Modalités pour obtenir une carte d'identité :</h2>
    <strong>Attention, depuis le premier décembre 2005, il est possible, via nos services, 
    de recevoir une carte d'identité électronique en urgence.</strong><br />
    <br />
    1)   Cartes d’identité électroniques pour les personnes de plus de 12 ans.<br />
    <ul>
        <li> une convocation parvient à votre domicile, vous invitant à vous présenter en nos locaux.</li>
        <li> se munir d’une photo d’identité sur fond blanc et de 15 €.</li>
        <li> le délai d’obtention est de +/- 3 semaines.</li>
    </ul>


Le texte tel que vu dans l'éditeur dans les deux cas (code "pollué",
code propre)





Modalités pour obtenir une carte d'identité :
---------------------------------------------
Attention, depuis le premier décembre 2005, il est possible, via nos
services, de recevoir une carte d'identité électronique en urgence.

1) Cartes d’identité électroniques pour les personnes de plus de 12
ans.

+ une convocation parvient à votre domicile, vous invitant à vous
  présenter en nos locaux.
+ se munir d’une photo d’identité sur fond blanc et de 15 €.
+ le délai d’obtention est de +/- 3 semaines.




3. Créer un modèle de document
==============================

Un modèle de document peut être inséré dans un document, une
actualité, un événement,...

Certains blocs d'information font appel à la même mise en forme. Ce
peut être la partie "coordonnées" d'une page, la présentation des
élus,...


A titre d'exemple, voici comment apparaissent les coordonnées des
services communaux à Herstal:



Le modèle ayant servit à l'élaboration de cette page est le suivant:




Une fois un modèle créé, il suffit de cliquer sur l'icone "Modèle" de
l'éditeur html.



Il est possible d'utiliser plusieurs modèles dans la même page.
Insérer un modèle n'affecte pas le contenu existant.

Comment créer un modèle de document?

Il faut que le produit "CPFCKTemplates" soit installé. Si ce n'est
fait, procédez à l'installation dans Configuration du site -->
Produits d'extension

Lorsque le produit est installé, il est possible d'ajouter un élément
"modèlefckeditor" par le menu "ajout d'un élément" après avoir créé un
dossier "Modèles" (pour y ranger les modèles et les images utilisées
dans ceux-ci).

Un modèle doit être "activé" pour être disponible dans l'éditeur.





4. Exemple de mise en forme d'un texte
======================================



Nous avons vu précédemment comment obtenir un texte "brut", sans mise
en forme et balises héritées d'un éditeur de texte (word) ou d'une
version précédente de site.

Voici un exemple de texte brut:

Modalités pour obtenir une carte d'identité :

Attention, depuis le premier décembre 2005, il est possible, via nos
services, de recevoir une carte d'identité électronique en urgence.

1) Cartes d’identité électroniques pour les personnes de plus de 12
ans.

une convocation parvient à votre domicile, vous invitant à vous
présenter en nos locaux.
se munir d’une photo d’identité sur fond blanc et de 15 €.
le délai d’obtention est de +/- 3 semaines.


En cas de perte ou de vol :

Pendant les heures d’ouverture, il faut :
- faire une déclaration à la police ou à la gendarmerie.
- le signaler à notre administration communale.
En dehors des heures d’ouverture, il faut le signaler au Helpdesk,
service ouvert 24h/24, au numéro 02/518.21.16.


2) Cartes d’identité pour enfants de moins de 12 ans.

Il est maintenant possible d'obtenir une carte électronique pour les
enfants belges de moins de 12 ans: se présenter avec l'enfant, se
munir d'une photo d'identité fond blanc et de 3 euros. délai
d'obtention: 3 semaines.

3) Cartes d’identité pour les étrangers.

Depuis le mois d'août 2008, il est possible d'obtenir une carte
électronique pour les étrangers. Se munir de l'ancienne carte, de 3
photos et de 15 euros.

Et un exemple de texte mis en forme:




Modalités pour obtenir une carte d'identité : (titre 2)
-------------------------------------------------------


Attention, depuis le premier décembre 2005, il est possible, via nos
services, de recevoir une carte d'identité électronique en urgence.



1) Cartes d’identité électroniques pour les personnes de plus de 12
ans. (titre 3)
~~~~~~~~~~~~~~




+ une convocation parvient à votre domicile, vous invitant à vous
  présenter en nos locaux.
+ se munir d’une photo d’identité sur fond blanc et de 15 €.


le délai d’obtention est de +/- 3 semaines.


En cas de perte ou de vol :

Pendant les heures d’ouverture, il faut :


+ faire une déclaration à la police ou à la gendarmerie.
+ le signaler à notre administration communale. (liste à puce)


En dehors des heures d’ouverture, il faut le signaler au Helpdesk,
service ouvert 24h/24, au numéro 02/518.21.16.




2) Cartes d’identité pour enfants de moins de 12 ans.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Il est maintenant possible d'obtenir une carte électronique pour les
enfants belges de moins de 12 ans: se présenter avec l'enfant, se
munir d'une photo d'identité fond blanc et de 3 euros. délai
d'obtention: 3 semaines.



3) Cartes d’identité pour les étrangers.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Depuis le mois d'août 2008, il est possible d'obtenir une carte
électronique pour les étrangers. Se munir de l'ancienne carte, de 3
photos et de 15 euros.



5. La mise en forme
===================



La mise en forme d'un texte peut être faite de deux manières
différentes. La première consiste à utiliser des balises et des styles
prédéfinis. La seconde, qui est à proscrire, consiste à utiliser des
styles "locaux"; c'est à dire, définis dans la page html elle-même.



Observons ces deux modes de mise en forme pour le texte "Modalités
pour obtenir une carte d'identité" mis en forme à la page précédente :





1- Utilisation du menu "Format" application du "titre 2" pour obtenir
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~



>> Modalités pour obtenir une carte d'identité : <<
---------------------------------------------------










2. Utilisation du menu "Size" et de la taille de police "medium"
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~



ainsi que du menu "text color" et de la couleur #1A5C8F
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~



pour obtenir
~~~~~~~~~~~~

>> Modalités pour obtenir une carte d'identité : <<







Le résultat est quasi identique et ne demanderait qu'une adaptation de
la taille du texte pour être parfaitement identique.

Les deux méthodes parraissent donc valables.
Observons maintenant le code html pour chacune des phrases.



1. Utilisation du format "titre2"
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


::

    
    <h2>Modalités pour obtenir une carte d'identité :</h2>


Le texte est balisé avec la balise "h2", la valeur de la balise est
définie en CSS. Le webmaster peut décider à tout moment de changer les
valeurs CSS définies pour la balise "h2" en quelques minutes.
L'opéraiton effectuée, la mise en forme de tous les textes balisés
avec la balise "h2" sera actualisée en fonction des modifications
effectuées dans le code CSS. Cette méthode est la bonne.

La façon de procéder pour définir ou modifier des styles de l'éditeur
est expliquée dans le document "`Comment modifier ou ajouter des
styles dans l'éditeur`_".




2. Utilisation de la taille de police "medium" et de la couleur de
texte #1A5C8F
~~~~~~~~~~~~~


::

    
    <span style="color: rgb(26, 92, 143);"><span style="font-size: medium;">Modalités pour obtenir une carte d'identité :  </span></span>


La mise en forme du texte est directement définie dans le code html;
ce qui signifie que toute modification ultérieure devra être faite
manuellement dans chaque page du site.

Le code source est beaucoup plus chargé; ce qui augmente le risque
d'avoir des interférences.

Cette deuxième méthode est totalement à proscrire . Normalement, les
options "Size" et "Text color" ont été déactivées de l'éditeur. Si ce
n'est le cas, il faut changer les paramètres dans configuration du
site/configuration de Fckeditor et sélectionner la " Barre de menu
Plone par défaut".




6. Insérer une image
====================



Utilisons l'icône insérer une image et cliquons sur le bouton
"Parcourir le serveur"


L'image peut être "stockée" dans le dossier courant, mais l'interface
d'ajout d'images permet aussi de créer un dossier que l'on pourrait
nommer "images" pour y stocker les images.

Ainsi, si je me situe sur la page d'accueil d'un service communal et
que je souhaite insérer les photos des membres du service, je peux, en
mode édition d'un document, insérer des images. Par défaut, les images
ajoutées seront "stockées" dans le dossier parent du document. Il est
préférable de créer un dossier "images" soit à l'avance soit au moment
ou l'on insère l'image de telle sorte que les images n'apparaissent
pas au même niveau que les éléments du dossier du service.




Créer un dossier "images" permet de ne pas "surcharger" la vue
"contenus" du dossier.


Une fois l'image insérée dans l'éditeur, il reste à lui appliquer un
style en cliquant sur l'image et en sélectionant dans le menu "Style"
de l'éditeur l'option "image à gauche" ou "image à droite" de telle
sorte que le texte puisse "habiller" l'image.









7. Générer une table des matières automatiquement
=================================================



Pour afficher une table des matières, il faut baliser les en-têtes de
paragraphe en "titre 2" et, alors que l'on est en mode modification,
cocher la case "table des matières" sous l'onglet "paramètres.

Exemple de page avec une table des matières




Baliser les en-têtes de paragraphe en "titre 2" (h2)



Activer le paramètre "table des matières"



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
.. _Produits: http://www.imio.be/imio/imio/produits
.. _Gestion de l'urbanisme: http://www.imio.be/produits/gestion-de-lurbanisme
.. _Guichet en ligne: http://www.imio.be/produits/guichet-en-ligne
.. _Manuels de référence: http://www.imio.be/support/documentation/manual
.. _FAQs: http://www.imio.be/support/documentation/faqs
.. _Support: http://www.imio.be/imio/imio/support
.. _Prestations complémentaires: http://www.imio.be/services/prestations-complementaires
.. _Tutoriels vidéo: http://www.imio.be/support/documentation/tutoriels-video
.. _How-tos: http://www.imio.be/support/documentation/how-to
.. _Dans les médias: http://www.imio.be/presentation/dans-les-medias
.. _Liens: http://www.imio.be/support/documentation/link
.. _Présentation: http://www.imio.be/imio/imio/presentation
.. _Nos atouts: http://www.imio.be/presentation/nos-atouts
.. _Liens: http://www.imio.be/support/documentation/liens
.. _Gestion électronique de documents: http://www.imio.be/produits/gestion-electronique-de-documents
.. _Gestion des activités extra-scolaires: http://www.imio.be/produits/gestion-des-activites-extra-scolaires
.. _L'équipe: http://www.imio.be/contact/lequipe
.. _Aller au contenu.: http://www.imio.be/support/documentation/manual/site-internet/gerer-le-contenu-d-une-page/referencemanual-all-pages#content
.. _Se connecter: http://www.imio.be/login
.. _Conseil d'administration: http://www.imio.be/presentation/conseil-dadministration
.. _Demande d'assistance (Trac): http://www.imio.be/support/demande-dassistance-trac
.. _Offre All in One: http://www.imio.be/services/all-in-one
.. _Comité de gestion: http://www.imio.be/presentation/comite-de-gestion
.. _Conseil, audit et processus: http://www.imio.be/solutions/conseil-audit
.. _Site Internet: http://www.imio.be/produits/site-internet
.. _Site Internet: http://www.imio.be/support/documentation/manual/site-internet
.. _FAQs: http://www.imio.be/support/documentation/faq
.. _Aller à la navigation: http://www.imio.be/support/documentation/manual/site-internet/gerer-le-contenu-d-une-page/referencemanual-all-pages#portal-globalnav
.. _Gestion des délibérations: http://www.imio.be/produits/gestion-des-deliberations
.. _Accueil: http://www.imio.be
.. _Contact: http://www.imio.be/imio/imio/contact
.. _Fichiers: http://www.imio.be/support/documentation/fichiers
.. _Forums: http://www.imio.be/support/forums
.. _Références erreurs: http://www.imio.be/support/documentation/error
.. _Glossaires de définitions: http://www.imio.be/support/documentation/glossary
.. _Emplois et compétences: http://www.imio.be/produits/emplois-et-competences
.. _Tutoriels: http://www.imio.be/support/documentation/tutoriels
.. _Comment adhérer: http://www.imio.be/presentation/adherer
.. _Support: http://www.imio.be/support
.. _Comment modifier ou ajouter des styles dans l'éditeur: http://www.imio.be/support/documentation/how-to/modifier-des-styles-dans-lediteur
.. _Services: http://www.imio.be/imio/imio/services
.. _Contactez-nous: http://www.imio.be/contact/contact
.. _Processus et simplification administrative : http://www.imio.be/produits/processus-et-simplification-administrative
.. _Contributions: http://www.imio.be/presentation/contributions
.. _ mutualisation: http://www.imio.be/solutions/logiciels-libres
.. _Solutions: http://www.imio.be/imio/imio/solutions
.. _Contact: http://www.imio.be/contact
.. _Centrale d'achat: http://www.imio.be/solutions/centrale-dachat
.. _Documentation: http://www.imio.be/support/documentation
.. _Présentation: http://www.imio.be/presentation
.. _Solutions: http://www.imio.be/solutions
.. _Gestion de projet (PST): http://www.imio.be/produits/gestion-de-projet
.. _Services: http://www.imio.be/services
.. _Gestion des services techniques: http://www.imio.be/produits/gestion-des-services-techniques
.. _Présentation: http://www.imio.be/presentation/presentation
.. _Produits: http://www.imio.be/produits
.. _Recherche avancée…: http://www.imio.be/search_form
.. _image: http://www.imio.be/support/documentation/image


