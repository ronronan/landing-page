+++
title = 'Pourquoi je me lance à écrire mes propres articles'
date = 2026-04-30T20:00:00+02:00
draft = false
tags = ['meta', 'blog', 'souveraineté']
+++

Ça fait un moment que j'y pense. Longtemps que je consomme des articles, des threads, des notes de blog écrites par d'autres — des gens qui partagent ce qu'ils font, ce qu'ils apprennent, ce qu'ils ratent aussi. Et longtemps que je me dis : _moi aussi j'ai des choses à dire._

Alors voilà. C'est parti.

## Pourquoi maintenant ?

Il n'y a pas de moment parfait pour commencer à écrire. J'attendais sans trop le formuler une sorte de légitimité — l'impression d'en savoir assez, d'avoir assez de projets aboutis, d'avoir une audience prête à m'accueillir. Mais c'est une fausse piste.

Ce qui m'a finalement décidé, c'est que je suis en train de changer de boulot. Et quand on se retrouve entre deux postes, on a cette fenêtre magique où on se dit qu'on va "profiter pour faire des trucs". En général ça dure trois jours avant de retomber dans Netflix. Mais là, j'ai tenu bon — probablement parce que lancer un blog demande moins d'efforts physiques que d'apprendre le piano ou de finir ce side project qui dort sur GitHub depuis 2021.

Bonne occasion, donc. On écrit pour clarifier sa pensée autant que pour la partager. Et on n'a pas besoin d'une audience pour commencer.

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

Pendant des années, les plateformes comme Medium, Substack ou LinkedIn ont rendu l'écriture facile — trop facile, en fait. On publie en quelques clics, on touche une audience, mais on confie ses écrits à une infrastructure qu'on ne contrôle pas, soumise à des conditions d'utilisation qui changent, des algorithmes opaques, et souvent des serveurs quelque part dans un datacenter américain.

Je veux autre chose. Je veux que mes articles m'appartiennent vraiment — techniquement, dans la durée. Que si demain une plateforme ferme ou change ses règles, mon contenu soit toujours là, intact, accessible.

Pour la stack technique, j'ai choisi [Hugo](https://gohugo.io), un générateur de site statique. Pas de base de données, pas de PHP qui tourne dans son coin, juste des fichiers Markdown transformés en HTML. Simple, rapide, compréhensible de bout en bout — exactement le genre de truc qui me plaît.

Reste la vraie question : **où héberger tout ça ?** Et c'est là que ça se complique, parce que la réponse se résume en réalité à une question de budget.

**Option A : un VPS chez OVH à 5€/mois.** C'est en France, c'est fiable, c'est gérable sans se prendre la tête. Le genre de solution raisonnable que je recommanderais à n'importe qui. Mais voilà, je suis moi, et "raisonnable" n'a jamais été ma première réaction face à un problème technique.

**Option B : un Raspberry Pi 3 qui traîne dans un tiroir chez moi.** Même pas besoin d'en acheter un, j'en ai déjà un. Le coût marginal serait quasi nul — juste l'électricité, soit à peu près "moins d'un café par mois". Par contre, il y a quelques petits détails à régler : exposer un port sur ma box, gérer les coupures réseau, survivre aux redémarrages intempestifs, et expliquer à mon entourage pourquoi j'ai branché "encore un truc" derrière la télé.

Le charme de l'option B, c'est que c'est exactement le genre de projet qui va générer du contenu pour ce blog. Configurer un serveur web sur un Pi, gérer les certificats SSL, mettre en place un déploiement automatique... Autant de sujets sur lesquels j'aurai des choses à raconter, probablement avec quelques anecdotes de galère incluses. Je n'ai pas encore tranché — mais j'y travaille.

## Ce que ce blog ne sera pas

Je ne vais pas prétendre être expert de tout ce dont je parle. Je suis quelqu'un qui bidouille, qui apprend sur le tas, qui fait des erreurs et les corrige. Si vous cherchez une référence absolue, vous trouverez mieux ailleurs. Si vous cherchez un point de vue sincère sur des projets concrets — avec leurs aspérités — vous êtes au bon endroit.

Je n'essaierai pas non plus de plaire à tout le monde. Ce blog n'est pas un produit, c'est un espace personnel. La monétisation, le growth hacking, les call-to-action : très peu pour moi.

## La suite

Le prochain article parlera probablement de la décision finale sur l'hébergement — et de comment j'ai mis ce blog en place techniquement. Je ne veux pas trop en dévoiler maintenant, pas parce que c'est secret, mais parce que j'ai envie d'avoir quelque chose de concret à montrer avant d'en parler.

À bientôt.
