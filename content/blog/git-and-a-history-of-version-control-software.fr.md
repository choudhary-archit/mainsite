---
title: "Git et l'Histoire des Logiciels de Gestion de Version"
date: 2022-12-21T23:27:37+01:00
draft: false
---

Git est un logiciel de gestion de version (LGV). C'est-à-dire, il trace
l'histoire de votre projet de code lorsque vous y faites des modifications. En
2022, les programmeurs du monde entier vivent et respirent Git. Il est très
difficile de surestimer l'ampleur de l'utilisation de Git dans le monde
d'aujourd'hui.  Pour un exemple extrême, l'intégralité du code source de Windows
est stocké dans un même dépôt Git : 350 millions de fichiers, ce qui fait que le
dépôt a une taille de 300 gigaoctets.[^1] Pour donner un exemple plus trivial,
le code source de Git lui-même est dans un dépôt Git.[^2] Mais malgré toute
l'omniprésence de Git, il n'a pas toujours été le LGV standard pour lequel les
développeurs optaient automatiquement.

À l'époque où l'ordinateur était un objet de niche et une maitrise de son
utilisation et programmation vous a valu le titre d'un « nerd », les 
développeurs n'avaient pas le privilège d'utiliser un LGV aussi puissant et
dynamique que Git. En vrai, à un certain moment dans le passé il n'y avait même
pas de LGV du tout. Comme écrit Juan Buis[^3], pour tout projet de logiciel sur
lequel l'on travaillait à l'époque, il y avait une personne désignée à qui
appartenait la version maître et vous n'étiez permis d'accéder qu'à la partie
du code base qui avait besoin de travail. Après que vous aviez terminé, vos
modifications étaient vérifiées pour détecter les erreurs et ensuite ces
modifications se faisaient directement à la version maître centrale.

Ceci signifiait, en particulier, qu'il était très difficile de suivre
l'évolution du code base. La seule façon de le faire était de stocker
constamment des copies de la version maître. Mais pour les grands projets cela
nécessitait un espace disque de plus en plus énorme, à une époque où les
disquettes de 8 pouces venaient à peine d'arriver sur le marché. Et pour
couronner le tout, si la version maître était corrompue ou supprimmée, tout
votre dur labeur serait jeté par les fenêtres.

Enfin, en 1972, le premier LGV a été développé. Il s'appelait _Source Code
Control System_ (SCCS) et a été écrit par le développeur Marc Rochkind pour
l'IBM 360 fonctionnant sous OS et le PDP-11 fonctionnant sous UNIX.[^4] Selon
Rochkind, ses principales caractéristiques peuvent être résumées en quatre
catégories.

1. _Stockage_: Chaque version d'un module est stockée dans le même fichier et
   tout code source qui apparaît dans plusieurs versions du module n'est stocké
   qu'une seule fois, ce qui économise de l'espace disque. Toutes les versions
   antérieurs peuvent être consultées à l'aide du SCCS.

2. _Protection_: L'on peut donner les contributeurs un accès restreint au
   codebase, pour qu'une personne ne soit autorisée de modifier que les modules
   qui lui sont attribué.

3. _Identification_: Le SCCS estampille les modules de chargement avec le
   numéro de version, la date, l'heure, et d'autres informations de ce type ;
   le code source qui a produit le module de chargement peut être inféré de ces
   seules informations.

4. _Documentation_: Les auteurs de chaque modification sont enregistrés avec
   d'autres informations de ce genre.

L'on peut appeler les caractéristiques ci-dessus les principes de base du gestion
de version puisque tout les LGV qui ont été crées après le SCCS, bien que beaucoup
plus puissants et flexibles, étaient basés sur ces capabilités.

La seconde génération des LGV a ensuite apporté des améliorations. L'un d'entre
eux, _Concurrent Versioning System_ (CVS), a été crée par Dick Grune en
juillet 1986 afin de pouvoir travailler ensemble avec ses élèves sur le
developpment du « [ACK C
compiler](https://en.wikipedia.org/wiki/Amsterdam_Compiler_Kit) ». Le problème
était qu'ils avaient tous des agendas très différents : l'un travaillait «
nine-to-five », l'autre travaillait irrégulièrement, et Grune ne pouvait y
travailler que les soirs ; le CVS leur a permis de valider des modifications
selon leur aise.[^6] Il s'agissait au départ d'une collection des scripts Shell
écrits par Grune, qui s'appelait _cmt_, qui est devenue le CVS quand Brian
Berliner a traduit en C une version nettoyée de cmt. Le CVS a continué à
devenir le LGV standard pendant longtemps après que Jim Kingdon l'ait adapté
pour qu'il fonctionne à distance via TCP/IP, ce qui a permis à la communauté
open-source l'utilisation d'utiliser CVS. Il a gagné le Prix STUG en 2003.[^7]

Le prochain grand LGV open-source qui est apparu était Subversion. Il a été
créé par CollabNet, Inc. en 2000 pour être une amélioration de CVS qui a
supprimé quelques bogues et ajouté plus de fonctionnalités, qui, en 2001, était
suffisamment avancé pour héberger son propre code source.[^8] La version 1.0 a
été publiée en 2004, et elle a été acceptée comme un projet Apache de premier
niveau en 2010.  Subversion a été très largement préféré à CVS en raison des
améliorations qu'il apportait : le déplacement et le renommage des fichiers
étaient plus propres, les commits concernaient l'ensemble de l'arbre et non
seulement les fichiers individuels, et ainsi de suite. À peu près au moment où
Subversion a été publié, ses principaux rivaux contemporains sont nés :
Mercurial et Git.

Mercurial et Git sont tous deux issus du projet de noyau Linux lancé par Linus
Torvalds. Le projet utilisait initialement BitKeeper pour suivre l'historique
du code source, un LGV propriétaire créé par la société BitMover. La raison
pour laquelle Linus a opté pour BitKeeper était qu'il était gratuit sous une
licence communautaire. Jusqu'à ce qu'Andrew Tridgell décide de faire de
l'ingénierie inverse sur BitKeeper pour créer son propre outil qui permettrait
aux non-contributeurs d'accéder aux sources du noyau Linux ; le contenu d'un
dépôt BitKeeper ne pouvait être vérifié qu'en utilisant le client propriétaire.
Il a ensuite été accusé par BitMover de violer la licence communautaire, qui a
donc été supprimée : la seule façon d'utiliser BitKeeper était de payer.[^9]

Puisqu'il n'y avait aucun autre LGV libre en 2005 qui pouvait égaler la
fonctionnalité distributive et la vitesse de BitKeeper qui était essentielle
dans le développement du noyau Linux, Linus a décidé d'écrire le sien ; c'est
devenu Git. Presque en même temps que l'annonce du projet Git, un autre
développeur du noyau, Olivia Mackall, a commencé à travailler sur un autre LGV
appelé Mercurial en réponse à l'arrêt de l'utilisation gratuite de BitKeeper
par BitMover dans le projet du noyau.  Ces noms, autrement évidents, peuvent
être compris à partir des citations suivantes :

> Shortly before the first release, I read an article about the ongoing
> Bitkeeper debacle that described Larry McVoy as mercurial (in the sense
> of 'fickle'). Given the multiple meanings, the convenient abbreviation,
> and the good fit with my pre-existing naming scheme (see my email
> address), it clicked instantly. Mercurial is thus named in Larry's
> honor. I do not know if the same is true of Git.[^10]
>
> _[Peu de temps avant la première version, j'ai lu un article sur la débâcle de
> Bitkeeper qui décrivait Larry McVoy comme mercuriel (dans le sens de
> "inconstant"). Étant donné les multiples significations, l'abréviation pratique
> et la bonne adéquation avec mon schéma de dénomination préexistant (voir mon
> adresse électronique), le déclic s'est fait instantanément. Mercurial est donc
> nommé en l'honneur de Larry. Je ne sais pas s'il en est de même pour Git.[^15]]_
>
> -- _Olivia Mackall_

> I'm an egotistical bastard, so I name all my projects after myself. First
> Linux, now Git.[^11]
>
> _[Je suis un salaud égoïste, alors je donne mon nom à tous mes projets. D'abord
> Linux, maintenant Git.[^16]]_ 
>
> -- _Linus Torvalds_

Selon Linus, Git est meilleur que Mercurial[^12], mais selon la plupart des
gens normaux, bien qu'il y ait quelques différences, ils sont très proches en
termes de performances et tous deux sont très rapides. Cela dit, les
performances ne se traduisent pas toujours par une facilité d'utilisation. Je
n'ai jamais utilisé Mercurial et ne peux donc pas dire si un utilisateur
quotidien de Mercurial trouvera difficile de revenir sur des modifications et
d'effectuer d'autres actions de contrôle de version. En fait, je ne serais pas
surpris si l'utilisateur moyen de Mercurial en savait plus sur le
fonctionnement de Mercurial que l'utilisateur moyen de Git qui ne sait pas
comment fonctionne Git, simplement parce que beaucoup, beaucoup plus de
personnes utilisent Git que Mercurial[^13] et cela inclut des personnes qui ne
sont pas des programmeurs professionnels.  Mais Git, d'après mon expérience,
n'est pas facile à utiliser ; ceci est résumé au mieux par la bande dessinée
XKCD suivante :[^14]

{{< image src="https://imgs.xkcd.com/comics/git_2x.png" width="50%" >}}

La gestion de version a donc eu une longue et riche histoire qui s'étend sur
plus de cinquante ans. Peut-être que tout cela culmine dans Git et Mercurial,
et qu'aucun meilleur système de gestion de révision ne sera jamais créé. Cela
ne serait pas surprenant puisque leur polyvalence dépasse de loin tout autre
système imaginable.  Ou peut-être cette polyvalence n'est-elle qu'une illusion,
comme pour tous les autres grands LGV qui sont apparus et ont perdu leur
popularité en l'espace de quelques décennies. Seul le temps nous le dira.

[^1]: Harry, Brian. "The Largest Git Repo on the Planet." _Brian Harry’s Blog_, 28 fevrier 2019, [https://devblogs.microsoft.com/bharry/the-largest-git-repo-on-the-planet](https://devblogs.microsoft.com/bharry/the-largest-git-repo-on-the-planet). Consulté le 22 décembre 2022.

[^2]: On peut le retrouver à [https://git.kernel.org/pub/scm/git/git.git/](https://git.kernel.org/pub/scm/git/git.git/). 

[^3]: Juan Luis. "How Git Changed the History of Software Version Control." _HackerNoon_, 11 juin 2018, [https://hackernoon.com/how-git-changed-the-history-of-software-version-control-5f2c0a0850df](https://hackernoon.com/how-git-changed-the-history-of-software-version-control-5f2c0a0850df). Consulté le 22 décembre 2022.

[^4]: Rochkind, Marc J. "The Source Code Control System." _IEEE Transactions on Software Engineering_, vol. SE-1, no. 4, 1975, p. 364–70. Crossref, https://doi.org/10.1109/tse.1975.6312866. Un PDF scanné peut être retrouvé [ici](https://basepath.com/aup/talks/SCCS-Slideshow.pdf).

[^5]: Les modules de chargement sont quelque chose spécifique à la programmation de l'IBM OS/360 ou du PDP-11 dont je ne connais rien. Les pages Wikipédia (qui font apparamment l'objet de recherches approfondies) pour la serie des [IBM System/360](https://en.wikipedia.org/wiki/IBM_System/360) et le [PDP-11](https://en.wikipedia.org/wiki/PDP-11) seront peut-être un bon point de départ.

[^6]: Grune, Dick. "Concurrent Versions System CVS." _Dick Grune’s Website_, [https://dickgrune.com/Programs/CVS.orig](https://dickgrune.com/Programs/CVS.orig). Consulté le 22 décembre 2022.

[^7]: "STUG Award." _USENIX_, 7 May 2020, [https://www.usenix.org/about/stug/](https://www.usenix.org/about/stug/). Consulté le 22 décembre 2022.

[^8]: "What Is Subversion?" _Red Bean_, [https://svnbook.red-bean.com/en/1.7/svn.intro.whatis.html](https://svnbook.red-bean.com/en/1.7/svn.intro.whatis.html). Consulté le 22 décembre 2022.

[^9]: McAllister, Neil. "Linus Torvalds’ BitKeeper Blunder." _InfoWorld_, 2 May 2005, [https://www.infoworld.com/article/2670360/linus-torvalds--bitkeeper-blunder.html](https://www.infoworld.com/article/2670360/linus-torvalds--bitkeeper-blunder.html). Consulté le 22 décembre 2022.

[^10]: Mackall, Olivia. "Why Did Matt Choose the Name Mercurial?" _Mercurial_, 2012, [https://lists.mercurial-scm.org/pipermail/mercurial/2012-February/041807.html](https://lists.mercurial-scm.org/pipermail/mercurial/2012-February/041807.html). Consulté le 22 décembre 2022. À noter qu'Olivia Mackall était antérieurement Matt Mackall ; je ne sais pas la raison derrière son utilisation d'un autre nom.

[^11]: McMillan, Robert. "After Controversy, Torvalds Begins Work on 'Git.'" _PC World_, 20 Apr. 2005, [https://www.pcworld.idg.com.au/article/129776/after_controversy_torvalds_begins_work_git_/](https://www.pcworld.idg.com.au/article/129776/after_controversy_torvalds_begins_work_git_/). Consulté le 22 décembre 2022. 

[^12]: He says this in Google. "Tech Talk: Linus Torvalds on Git." _YouTube_, 14 May 2007, [www.youtube.com/watch?v=4XpnKHJAok8](https://www.youtube.com/watch?v=4XpnKHJAok8). Consulté le 22 décembre 2022. 

[^13]: "Version Control Systems Popularity in 2016." _RhodeCode_, 2016, [https://rhodecode.com/insights/version-control-systems-2016](https://rhodecode.com/insights/version-control-systems-2016). Consulté le 22 décembre 2022.

[^14]: Bande dessinée tirée de [https://xkcd.com/1597/](https://xkcd.com/1597/). Au cours de mes recherches pour ce blogpost, j'ai trouvé [Oh Shit, Git!?!](https://ohshitgit.com/) ; essayez ce site si vous faites une erreur dans la gestion de votre dépôt Git. J'ai également trouvé [cette](https://hackaday.com/wp-content/uploads/2017/04/flowgit.png) image qui aide vraiment à comprendre les actions de base de Git.

[^15]: La dernière phrase illustre un jeu de mots. Elle veut suggérer que McCoy soit un « git », ce qui est un mot vulgaire en anglais d'Angleterre signifiant « connard ».

[^16]: Ici Linus tente d'être humoureux en suggérant qu'il soit lui-même un « git », ou un connard.
