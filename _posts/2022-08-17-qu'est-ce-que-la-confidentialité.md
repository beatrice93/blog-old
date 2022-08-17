---
layout: post
title: Qu'est-ce que la confidentialité ?
---

Cet article fait partie d'une série sur la confidentialité des données, que j'écris dans le désordre. Celui-ci fait office d'introduction et de motivation du problème.

## Contexte
En 2007, Netflix lance une compétition internationale, avec un prix d'un million de dollars à qui arrivera à améliorer son algorithme de recommandation. Pour ce faire, les participants doivent entraîner un modèle d'intelligence artificielle sur un jeu de données public d'utilisateurs de Netflix. Le jeu de données contient des films visionnés et notés par 500 000 utilisateurs anonymes (dont le nom a été remplacé par une suite de chiffres), avec pour chaque film, la date à laquelle il a été visionné, et la note de l'utilisateur. 

En 2008, une équipe de chercheurs de l'Université du Texas [démontre](https://arxiv.org/pdf/cs/0610105.pdf) que malgré l'anonymat de la base de données, il est possible d'identifier une partie des utilisateurs présents dans la base de données, à partir de connaissances partielles : il suffit par exemple de connaître la date à laquelle une personne a visionné 3 films à deux semaines près, pour retrouver la ligne qui lui correspond dans la base de données Netflix, et ainsi connaître l'intégralité des films que cette personne a vus et aimé. L'équipe va même jusqu'à croiser la base de données Netflix avec le site imdb (internet movie database) pour trouver les noms des personnes en question. S'ensuit un procès qui entraînera l'annulation de la seconde édition de la compétition.

## Confidentialité et sécurité
On distingue la confidentialité des données de la sécurité des données. La sécurité des données (souvent associée au chiffrage) permet de s'assurer que seul un utilisateur de confiance peut accéder aux données, pour les lire, les modifier, ou les supprimer. Lorsque, par exemple, on protège une base de données (des photos, des textes, son profil facebook) avec un mot de passe, c'est pour des raisons de sécurité : on veut éviter que quelqu'un d'autre que les utilisateurs de confiance (la famille, les amis, soi-même) ait accès aux données.

La confidentialité des données, c'est la garantie que n'importe quel utilisateur qui a accès à des données qui contiennent des informations sur moi-même (par exemple, une enquête à laquelle j'ai participé, les données publiques d'un hôpital où j'ai séjourné...) ne peut pas obtenir des informations compromettantes sur moi. Si un enquêteur ou un hôpital me garantit que mes données sont confidentielles, je ne risque rien à participer à l'enquête, ou à séjourner dans cet hôpital.
