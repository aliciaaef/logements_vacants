# logements_vacants
Analyses sur les logements vacants en France, à l'aide de Tableau, en utilisant les données de https://ecologie.data.gouv.fr/datasets/61816c6e23197bb34835228e

On se concentre sur le nombre de logements vacants en 2020.

### Communes
On affiche les 10 premières communes qui ont le plus de logements vacants.
Pour ce faire, on effectue un tri sur le nom de la commune.
<img width="2114" height="1382" alt="Feuille 14" src="https://github.com/user-attachments/assets/ce4887bc-e7dc-4f35-a63b-a67f15cacef7" />
Il est étonnant de voir une commune avec 33 logements vacants en Occitanie. Elle n'aurait pas dû apparaître.
On jette un oeil aux données pour comprendre.

<img height="500" alt="Capture d’écran 2026-03-19 à 15 25 43" src="https://github.com/user-attachments/assets/2965aac8-f4aa-4c28-b6f8-b83376a1acb2" />

On voit qu'il y a plusieurs communes qui portent le nom de Saint-Denis et que la somme de leurs logements vacants vaut 14946.
Ainsi le nom des communes n'est pas un bon paramètre pour les discerner.
On utilise donc le _code commune_ à ne pas confondre avec le code postal qui lui peut être partagé par plusieurs communes.

<img height="500" alt="Feuille 1 (2)" src="https://github.com/user-attachments/assets/41b31441-b5a7-476b-b292-3f90035ba964" />

On peut tracer ces résultats également sous la forme d'un histogramme. On trie sur le nombre de logements vacants et on filtre pour ne garder que les plus grands nombres de logements vacants.

<img height="500" alt="Feuille 4-2" src="https://github.com/user-attachments/assets/45a71561-34ec-4138-9cd6-38724763ad34" />


### Régions
On affiche la somme de tous les logements vacants dans chaque région.

<img height="500" alt="Feuille 12" src="https://github.com/user-attachments/assets/2ba84c17-e4ce-4f53-93be-0187e2a9a6e5" />


On affiche la valeur maximale de logements vacants dans une commune, pour chaque région de France métropolitaine.

<img height="500" alt="Feuille 12 attention paris arrondissement distincts" src="https://github.com/user-attachments/assets/4aa8f1d9-f324-4a31-af86-c7daa8d5b580" />
Il faut faire attention au cas particulier de Paris qui, dans la base de données de ecologie.data.gouv.fr, est présente via ses arrondissements ; ici 13550 correspond au nombre de logements vacants dans le 15ème arrondissement de Paris ; les arrondissements de Paris sont considérés comme des communes.

### Nombre de logements vacants vs nombre de logements total
On trace le nombre de logements vacants en fonction du nombre de logement total, par commune.

<img height="500" alt="image" src="https://github.com/user-attachments/assets/a1cff36f-5307-459e-81da-febdaf36308d" />

On voit que les deux sont très corrélés. En effet, le coefficient $R^2$ de la régression linéaire est de $0.94$.
Ce résultat était attendu étant donné que plus la ville a de logements plus il y a potentiellement de logements vacants.

Il est plus pertinent d'étudier le taux de vacance, c'est-à-dire la proportion de logements vacants au sein d'une commune, afin de comparer les communes entre elles peu importe leur taille.

Il est intéressant d'étudier le nombre de logements vacants en absolu car l'objectif est que les logements soient en majorité sur le territoire français d'avantage occupés afin de par exemple réduire le besoin de construire des logements neufs.

Il est également intéressant d'étudier le taux de vacance à l'échelle d'une commune car c'est lui qui reflète la "vie" d'une commune, son animation.

### Villes les plus vacantes
On peut calculer le taux de vacance par commune en créant un nouveau champ calculé à partir du nombre de logements vacants et du nombre de logements total par commune. On trie sur le taux de vacance et on filtre pour ne garder que les plus grands taux de vacance.

<img height="500" alt="Feuille 3 (2)" src="https://github.com/user-attachments/assets/aeb8ace0-3e9b-4ee4-a77d-180151fafd3a" />

La ville la plus vacante est Valouse avec près de 7 logements sur 10 vacants.

### Influence de la taille des communes sur leur vacance
On trace le taux de vacance en fonction du nombre de logements total, par commune.

<img height="500" alt="image" src="https://github.com/user-attachments/assets/da43e260-c6dd-43b3-b3fe-01701c212d56" />

On remarque un pic proche de 0 ce qui signifie que les communes les plus vacantes sont aussi celles avec le moins de logements (donc petites).

### Comparaison de la vacance des régions
On compare la vacance des région avec un diagramme en boîtes à moustache du taux de vacance de chaque commune, par région, trié par la moyenne du taux de vacance par région.

<img height="500" alt="image" src="https://github.com/user-attachments/assets/843ffe2a-18f8-4ae4-afac-89064f237d8e" />

On voit que les îles (Mayotte, Guadeloupe, Corse, Guyane, Martinique) ont en moyenne les villes avec les plus hauts taux de vacance.

### Effet de la localisation
On peut tracer le taux de vacance en fonction de la latitude et de la longitude :

<img height="500" alt="image" src="https://github.com/user-attachments/assets/10310e82-f10e-4a1c-8f17-6c0b863774f1" />

On remarque que communes les plus vacantes sont situées principalement vers les basses latitudes c'est-à-dire vers le Sud ce qui correspond aux Alpes, aux Pyrénées et à la Corse.

<img height="500" alt="image" src="https://github.com/user-attachments/assets/3c130e72-4416-45a7-a6a8-13baa099cb92" />

On voit que les communes les plus vacantes sont situées principalement vers les grandes longitudes, c'est-à-dire vers l'Est, ce qui correspond une nouvelle fois à la Corse et aux Alpes.

### Tableau de bord dynamique
On peut créer un tableau de bord dynamique qui affiche une carte, un histogramme et un diagramme en boîte à moustaches. En sélectionnant une région dans le diagramme en boîte à moustaches, la tableau de bord affiche uniquement les données de cette région sur la carte et sur l'histogramme.

Pour la région Nouvelle-Aquitaine :

<img width="800" alt="image" src="https://github.com/user-attachments/assets/0b2d0b45-aa4f-43c6-ab52-aa9f72fd0512" />

Pour la région Bourgogne-Franche-Comté :

<img width="800" alt="image" src="https://github.com/user-attachments/assets/20895431-4606-439b-aa5d-ce5d5f71d493" />

On peut se demander pourquoi si peu de communes apparaissent sur les cartes et la raison est qu'il y a beaucoup de données manquantes sur le nombre total de logements par commune, qui intervient dans le calcul du taux de vacance de chaque commune.

Ainsi, il faut prendre en compte que les résultats présentés précédemment sur le taux de vacance ne sont pas entièrement représentatifs de la situation sur le territoire français.

