# logements_vacants
Analyses sur les logements vacants en France, à l'aide de Tableau, en utilisant les données de https://ecologie.data.gouv.fr/datasets/61816c6e23197bb34835228e

On se concentre sur le nombre de logements vacants en 2020.

### Communes
On affiche les 10 premières communes qui ont le plus de logements vacants.
Pour ce faire, on effectue un tri sur le nom de la commune.
<img width="2114" height="1382" alt="Feuille 14" src="https://github.com/user-attachments/assets/ce4887bc-e7dc-4f35-a63b-a67f15cacef7" />
Il est étonnant de voir une commune avec 33 logements vacants en Occitanie. Elle n'aurait pas dû apparaître.
On jette un oeil aux données pour comprendre.

<img width="921" height="660" alt="Capture d’écran 2026-03-19 à 15 25 43" src="https://github.com/user-attachments/assets/2965aac8-f4aa-4c28-b6f8-b83376a1acb2" />

On voit qu'il y a plusieurs communes qui portent le nom de Saint-Denis et que la somme de leurs logements vacants vaut 14946.
Ainsi le nom des communes n'est pas un bon paramètre pour les discerner.
On utilise donc le _code commune_ à ne pas confondre avec le code postal qui lui peut être partagé par plusieurs communes.

<img width="2114" height="1382" alt="Feuille 1 (2)" src="https://github.com/user-attachments/assets/41b31441-b5a7-476b-b292-3f90035ba964" />

On peut tracer ces résultats également sous la forme d'un histogramme. On trie sur le nombre de logements vacants et on filtre pour ne garder que les plus grands nombres de logements vacants.
<img width="1642" height="1144" alt="Feuille 4-2" src="https://github.com/user-attachments/assets/45a71561-34ec-4138-9cd6-38724763ad34" />


### Régions
On affiche la somme de tous les logements vacants dans chaque région.
<img width="2112" height="1296" alt="Feuille 12" src="https://github.com/user-attachments/assets/2ba84c17-e4ce-4f53-93be-0187e2a9a6e5" />


On affiche la valeur maximale de logements vacants dans une commune, pour chaque région de France métropolitaine.
<img width="2114" height="1382" alt="Feuille 12 attention paris arrondissement distincts" src="https://github.com/user-attachments/assets/4aa8f1d9-f324-4a31-af86-c7daa8d5b580" />
Il faut faire attention au cas particulier de Paris qui, dans la base de données de ecologie.data.gouv.fr, est présente via ses arrondissements ; ici 13550 correspond au nombre de logements vacants dans le 15ème arrondissement de Paris ; les arrondissements de Paris sont considérés comme des communes.

### Taux de vacance
On peut calculer le taux de vacance par commune en créant un nouveau champ calculé à partir du nombre de logements vacants et du nombre de logements total par commune. On trie sur le taux de vacance et on filtre pour ne garder que les plus grands taux de vacance.
<img width="1686" height="1348" alt="Feuille 3 (2)" src="https://github.com/user-attachments/assets/aeb8ace0-3e9b-4ee4-a77d-180151fafd3a" />


