Cela fait un moment que j'ai envie d'écrire ce que je sais sur la confidentialité différentielle. Je reprends ici la plupart des explications du chapitre 1 de [The ethical algorithm](https://global.oup.com/academic/product/the-ethical-algorithm-9780190948207?cc=us&lang=en&), de Kearns et Roth.

## Motivation

Un organisme effectue un grand sondage sur la santé des élèves de collège. Afin de permettre l'étude des réponses à ce sondage par le plus grand nombre, les données sont publiées sur le site internet de l'organisme. Elles contiennent des informations sensibles, comme par exemple des questions sur la santé mentale des élèves, la prise de drogue, la vie sexuelle et sentimentale... Bien entendu, elles sont anonymisées : pour chaque réponse, seul le nom du collège, le sexe et la date de naissance de l'élève sont publiées.

Si cette dernière phrase vous fait tiquer, ce post est fait pour vous ! Le nom du collège, le sexe, et la date de naissance d'une personne ne permettent pas, prises isolément, de l'identifier. Mais prises ensemble, oui (en tout cas, si le collège n'est pas trop gros). Muni de ces informations, je peux identifier les réponses apportées au sondage par un élève de mon choix, et apprendre sur sa vie intime des choses qu'il aurait préféré garder secrètes. 

Autrement dit : l'anonymisation ne se résume pas à effacer le nom d'un jeu de données. Il existe plusieurs exemples historiques marquants d'une telle _ré-identification_ de données anonymisées, avec pour certains des répercutions légales importantes. Mais alors, comment garantir la confidentialité de données ?

C'est là que les maths viennent à notre rescousse, avec deux définitions qui permettent de formaliser le concept de confidentialité, et de pouvoir assurer aux personnes que leur anonymat sera respecté.

## Le k-anonymat

On dit qu'un jeu de données est $k$-anonyme si, toute combinaison de données non-sensibles correspond à au moins $k$ observations.

Par exemple, si notre jeu de données contient des informations démographiques comme la date de naissance, le sexe et le code postal, alors, pour qu'il soit $3$-anonmye, toute combinaison d'une date de naissance, d'un sexe et d'un code postal doit correspondre à au moins 3 individus différents.
Plus $k$ est un nombre élevé, et plus il est difficile d'identifier une personne dans un jeu de données $k$-anonyme.

Comment rend-on un jeu de données $k$-anonyme ? On peut, par exemple, supprimer toutes les observations qui représentent des combinaisons uniques de données démographiques (pour chaque date de naissance, sexe et code postal, si on obtient moins de $k$ individus correspondant à ces trois critères, on les supprime du jeu de données). Mais on peut aussi changer l'échelle des données : en remplaçant le code postal par le département, la date de naissance par une tranche d'âge, etc.

Le $k$-anonymat n'est pas une solution miracle : même si l'on ne parvient pas exactement à identifier la ligne correspondant à l'individu que l'on cherche dans le jeu de données, on réussira toujours à récupérer $k$ observations dont on est sûr qu'elles contiennent celle qui lui correspond. Cela peut permettre de récupérer certaines informations confidentielles. Mais le défaut majeur du $k$-anonymat et que la notion perd tout intérêt lorsque plusieurs jeux de données sont publiés successivement.
