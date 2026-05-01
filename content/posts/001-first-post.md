+++
title = 'Pourquoi je me lance à écrire mes propres articles'
date = 2026-04-30T20:00:00+02:00
draft = false
tags = ['perso', 'blog', 'journal']
+++

Ce n'est pas ma première fois. J'ai déjà écrit des articles techniques pour Slickteam — des vrais, publiés, lus par des gens. Et puis j'ai perdu le mojo. Progressivement, sans trop m'en rendre compte, j'ai arrêté de voir l'intérêt. Pire, je m'étais mis une barre ridiculement haute dans la tête : chaque article devait être parfait, complet, irréprochable. Résultat ? Je n'étais jamais satisfait, et j'écrivais de moins en moins jusqu'à ne plus écrire du tout.

Le paradoxe, c'est que je suis probablement le premier à sortir la phrase "c'est en faisant qu'on s'améliore". Sauf que je ne me l'appliquais pas — pas pour ça en tout cas.

Alors voilà. C'est reparti.

## Pourquoi maintenant ?

Je suis en transition professionnelle, et c'est exactement ce genre de fenêtre que j'avais envie d'exploiter autrement qu'en scrollant. En parallèle, je fais des travaux dans mon nouveau logement — et c'est bizarrement là, entre deux coups de peinture, que j'ai réalisé un truc : j'ai un tas de side projects en cours ou en attente, mais aucun endroit où je centralise vraiment ce que je fais et pourquoi je le fais.

L'idée s'est imposée d'elle-même : avant de me lancer tête baissée dans les projets, je commence par créer ce blog. Pas pour l'audience. Pour moi. Avoir un journal de bord où je peux me retrouver, suivre mes propres avancées, et ne pas réexpliquer de zéro dans six mois ce que j'avais fait et pourquoi.

Il y a un effet secondaire que j'apprécie aussi : écrire sur ce qu'on fait, ça force à prendre du recul. On ne peut pas expliquer quelque chose qu'on ne comprend pas vraiment — et quand on essaie, on creuse. C'est un filtre naturel contre le "ça marche, je sais pas trop pourquoi, on passe à la suite".

Le principe que je veux tenir : dès que je fais quelque chose sur un side project — un dev de feature, une méthodo que je veux appliquer, un usage de l'IA, un choix d'hébergement, une config qui m'a pris trois heures — j'en fais un billet. Court ou long, peu importe. L'important, c'est que ce soit dans le journal. Et si au passage ça aide quelqu'un d'autre, c'est un bonus.

## Ce que vous trouverez ici

Ce blog va me servir de **journal de bord et de terrain d'expérimentation**. L'idée n'est pas de publier des tutoriels léchés ou des articles "Top 10 des astuces pour devenir 10x developer" — il y en a déjà trop sur internet et je n'ai pas les chevilles pour ça.

Non, ce sera plutôt un mélange de tout ce qui gravite autour de l'IT et du génie logiciel dans mes projets perso :

- **Du dev** : parce que c'est ce que je fais, et parfois j'ai des trucs intéressants à raconter
- **Du CI/CD** : parce qu'automatiser c'est la vie, et parfois les pipelines me rendent la vie impossible
- **De la config serveur** : parce qu'il faut bien que quelqu'un souffre en silence avec les fichiers nginx
- **De la méthodologie** : ce qui marche, ce qui ne marche pas, ce que j'aurais fait différemment
- **Et le reste** : tout ce qui ne rentre pas dans une case propre mais qui mérite d'être noté quelque part

Le format sera variable : parfois court et factuel ("j'ai fait ça, voilà pourquoi"), parfois plus réflexif. L'idée c'est d'écrire pour moi en premier, et si ça aide quelqu'un d'autre, c'est un bonus.

## La question de l'hébergement : reprendre la main

Il y a un autre sujet qui me tient à cœur en lançant ce blog : celui de la **souveraineté**. Le mot fait un peu grand, mais l'idée est simple.

Pendant des années, les plateformes comme Medium ou LinkedIn ont rendu l'écriture facile — trop facile, en fait. On publie en quelques clics, on touche une audience, mais on confie ses écrits à une infrastructure qu'on ne contrôle pas, soumise à des conditions d'utilisation qui changent, des algorithmes opaques, et souvent des serveurs quelque part dans un datacenter américain.

Je veux autre chose. Je veux que mes articles m'appartiennent vraiment — techniquement, dans la durée. Que si demain une plateforme ferme ou change ses règles, mon contenu soit toujours là, intact, accessible.

Pour la stack technique, j'ai choisi [Hugo](https://gohugo.io), un générateur de site statique. Pas de base de données, pas de PHP qui tourne dans son coin, juste des fichiers Markdown transformés en HTML. Simple, rapide, compréhensible de bout en bout — exactement le genre de truc qui me plaît.

Reste la vraie question : **où héberger tout ça ?** Et c'est là que ça se complique — ou plutôt, là où j'aurais pu me compliquer la vie, mais où j'ai finalement choisi la facilité.

J'avais envisagé des options plus souveraines : un VPS chez OVH, ou mieux encore un Raspberry Pi 3 qui traîne dans un tiroir. Le Pi surtout m'attirait — coût quasi nul, contenu généré pour ce blog, projets de galère inclus. Configurer un serveur web, gérer les certificats SSL, survivre aux coupures réseau et aux redémarrages intempestifs : exactement le genre de truc que j'aime raconter.

Mais pour lancer ce blog _maintenant_ plutôt que _dans trois semaines quand le Pi sera enfin stable_, j'ai tranché autrement : **Firebase Hosting**. C'est gratuit pour un site statique de cette taille, le déploiement se fait en une commande, et ça tourne sans que j'aie à y penser. Et aussi, parce que je l'utilise déjà depuis 7 ans pour un de mes side projects. Malheureusement, je mets la souveraineté de côté pour le moment — en sachant très bien que c'est un compromis, pas une position définitive.

## Ce que ce blog ne sera pas

Je ne vais pas prétendre être expert de tout ce dont je parle. Je suis quelqu'un qui bidouille, qui apprend sur le tas, qui fait des erreurs et les corrige. Si vous cherchez une référence absolue, vous trouverez mieux ailleurs. Si vous cherchez un point de vue sincère sur des projets concrets — avec leurs aspérités — vous êtes au bon endroit.

Je n'essaierai pas non plus de plaire à tout le monde. Ce blog n'est pas un produit, c'est un espace personnel. La monétisation, le growth hacking, les call-to-action : très peu pour moi.

**À bientôt**. Ronan.
