# Protocole pour photographie des fleurs de Gesneria s.l.
*Étienne Léveillé-Bourret, 13 août 2012*

## Préparation du matériel
### Préparation du matériel végétal 
 1. Sélectionner au moins 2 fleurs en début d'anthèse par spécimen (la forme est différente avant l'anthèse, et la fleur est trop molle en fin d'anthèse).
 1. Retirer l'hypanthium et jeter, conserver seulement la corolle avec les étamines épipétales.
 1. Monter chaque corolle avec 2 aiguilles entomologique de calibre 0 ou plus petit (00 ou 000) sur un bloc de styromousse. Attention à ne pas déformer la corolle.
 1. Placer chaque fleur toujours dans la même orientation et parallèle au plan d'intérêt pour les analyses morphométriques.

### Préparation du support et de l'appareil photographique (de Simon)
 1. Placer les deux lampes au niveau le plus bas.
 1. Placer le support à appareil photo à 32 cm en lisant le niveau au point le plus haut du support.
 1. Utiliser la lentille macro (1:2.8, 60 mm).
 1. Mettre en mode manuel et utiliser F/20 (ouverture), ISO100 (sensibilité), S=0"5 (temps d'exposition) ou bien ajuster le temps d'exposition selon la luminosité de façon à ce que l'appareil détecte un niveau d'exposition 1 ou 2 points de moins que 0 (« optimal »).
 1. Sauver images en format RAW si possible.

### Prise de photo
Ne pas bouger durant la prise de photo, le temps d'exposition assez long rend l'appareil très sensible à tout mouvement. Prendre au moins 2 photos par spécimen pour être certain d'en avoir une bonne.

## Programmes à installer
 1. Installer la version la plus à jour de R (http://cran.r-project.org/).
 1. Télécharger le programme [[attachment:tpsdig2-v2.16.exe|tpsDig version 2.16]] (garder toujours cette version pour assurer la stabilité du script d'importation de R).
 1. Télécharger le programme [[attachment:tpsUtil-v1.5.exe|tpsUtil version 1.50]] (garder toujours cette version pour assurer la stabilité du script d'importation de R).

## Numérisation des photos
### Préparation des photos pour la numérisation
 1. Copier toutes les photos dans un dossier. Transformer en jpg avec le logiciel UFRaw (fonction {{{ufraw-batch}}}). Utiliser une compression minimale pour une qualité maximale
 1. Trier les photos pour conserver une seule photo par spécimen (la plus belle). Lui donner un nom logique (ex.: {{{{s34_f2.jpg}}} pour le spécimen 34, 2e fleur).
 1. Utiliser un script pour faire deux copies de chaque photo avec un numéro différent à la fin (voir exemple de script {{{2copies.script}}} pour Ubuntu, Annexe 1). [Ça donne, par ex., {{{s34_f2_n1.jpg}}} et {{{s34_f2_n2.jpg}}}]
 1. Mettre les photos obtenues en #3 dans un dossier unique.
 1. Ouvrir tpsUtil et sélectionner Operation -> Build tps file from images.
 1. Dans Input, sélectionner une des photos dans le dossier unique.
 1. Dans output, donner un nom de fichier logique pour recevoir les coordonnées des landmarks (par ex., {{{etude1_version1.tps}}}).
 1. Cliquer sur Setup.
 1. S'assurer que toutes les photos du dossier unique sont sélectionnées, puis cliquer sur Create.
 1. Operation -> Randomly order specimens.
 1. Choisir le fichier tps créé précemment pour Input (ex.: {{{etude1_version1.tps}}}).
 1. Dans output, donner un nom logique (par ex., {{{etude1_alea_version1.tps}}}).
 1. Cliquer sur Create.
 1. Fermer la fenêtre de tpsUtil.

### Numérisation des landmarks et semilandmarks
Tout au long de l'opération de numérisation, se rappeler de faire des sauvegardes fréquentes (File -> Save data as...   puis changer le nom du fichier, par exemple {{{version1.tps}}}, puis {{{version2.tps}}} etc.). Il arrive fréquemment qu'un faux mouvement place un landmark à un mauvais endroit, et le logiciel semble ne pas donner facilement l'option d'annuler la dernière opération. Ainsi, un mauvais mouvement peut nous faire perdre plusieurs heures de travail si on oubli de faire des sauvegardes fréquentes.

 1. Ouvrir tpsDig2.
 1. Cliquer sur File -> Input source -> File...  Puis sélectionner le fichier avec ordre aléatoire des photos (par ex., {{{etude1_alea_version1.tps}}}).
 1. Aller sélectionner Options -> Mouse wheel zooms   pour pouvoir naviguer plus facilement dans la photo.
 1. Sélectionner Options -> Image tools -> Measure, puis écrire la mesure de référence (en fonction de l'échelle utilisée dans la photo) dans Reference length et sélectionner la bonne unité.
 1. Cliquer sur Set scale.
 1. Cliquer sur le début de l'échelle de référence sur la photo, puis sur la fin de l'échelle, afin de former une ligne qui correspond à la taille de l'échelle.
 1. Dans le fenêtre Image tools, cliquer sur OK, puis fermer la fenêtre.
 1. Commencer la numérisation. Placer des vrais landmarks avec l'outil rond+ bleu, et placer des semilandmarks avec l'outil crayon jaune.
 1. Plusieurs configurations de semi/landmarks sont possibles, j'en propose une simple:
 1. Avec le crayon jaune, cliquer sur la bordure de la silhouette de la corolle au niveau de l'insertion des lobes supérieurs. Cliquer ensuite à intervalle régulier pour suivre la silhouette, jusqu'à arriver au niveau de l'insertion de la corolle sur le calice (correspond à l'insertion des sépales supérieurs si le calice n'a pas été retiré de la fleur avant la photo).
 1. Faire un clique droit sur la courbe.
 1. Sélectionner Resample curve, puis écrire 15 dans Number of points.
 1. Sélectionner By length, puis OK.
 1. Répéter les étapes 10 à 13 pour la partie inférieure de la silhouette de la corolle.
 1. Faire une sauvegarde (Save data as...), puis passer à la prochaine photo avec l'outil flèche rouge vers la droite (->).

## Analyses statistiques avec R
### Préparation du fichier NTS
 1. Ouvrir tpsUtil.
 1. Sélectionner Operation -> Restore original order.
 1. Dans Input, sélectionner le fichier contenant toutes les configurations numérisées (par ex., {{{etude1_alea_version43.tps}}}).
 1. Dans Output, donner un nom logique au fichier (par exemple, {{{etude1_restored_version43.tps}}}).
 1. Cliquer sur Create.
 1. Sélectionner Operation -> Append tps Curve to landmarks
 1. Dans Input, sélectionner le dernier fichier créé (par exemple, {{{etude1_restored_version43.tps}}}).
 1. Dans Output, donner un nom logique au fichier (par exemple, {{{etude1_final_version43.tps}}}).
 1. Cliquer sur Create
 1. Sélectionner Operation -> Convert tps/nts file.
 1. Dans Input, sélectionner le dernier fichier créé (par ex., {{{etude1_final_version43.tps}}}).
 1. Dans Output, donner le même nom au fichier, mais sélectionner l'extension NTS file (.NTS).
 1. Cliquer sur Create.
 1. Dans la nouvelle fenêtre, cocher Use scale factor (dans Options, surtout important s'il y avait une échelle dans l'image), cocher 2D landmarks (dans No. dimensions), cocher Image name (dans NTS label name).
 1. Cliquer sur Create et fermer tpsUtil.

### Analyses dans R
 1. Ouvrir R.
 1. Sourcer la fonction '''read.nts''' (voir Annexe 2).
 1. Télécharger le paquet shapes.
 1. Pour des exemples d'analyses, se référer à l'Annexe 3 (exemple d'analyses).

## ANNEXE 1 : 2copies.script
[[attachment:2copies.sh]]

Script pour le Bash d'Ubuntu: Pour créer deux copies de chaque photo en changeant le nom, très utile lorsqu'un grand nombre de photographies doivent être préparées.

```sh
#!/bin/bash

# Aller à l'emplacement des photos dans la
#ligne suivante, par exemple:
cd /home/etienne/IRBV/Gesneria/photos/test1/

# Faire une boucle qui copie (“move”) chaque photo
# dans un nouveau fichier avec un nouveau nom.
# Dans cet exemple, les photos sont au format jpeg:
for i in $(ls *.jpg)
do
 for n in 1 2
 do
  cp $i ./doubles/$(echo $i | cut -d'.' -f 1)-n$n.jpg
 done
done
```

## ANNEXE 2 : read.nts.R
[[attachment:read.nts.R]]

Script pour R: Sert à importer les données d'un fichier NTS dans un objet data.frame de R prêt pour les analyses.

```python
### Fonction pour lire les fichiers NTS dans R
#
# file: Donner le nom et le chemin du fichier à lire comme
#       argument.
#
# L'objet retourné est une liste de deux éléments:
# 1. spnam: Un vecteur contenant le nom des photos
#           numérisées
# 2. landmarks: Un tableau 3-dimensionnel de l x d x n
#               dimensions où l correspond au nombre de
#               semi/landmarks, d au nombre de dimensions
#               (2 ou 3) et n au nombre de photos
#               numérisées.

read.nts <- function(file) {
   job <- scan(file,what="char",quote="",sep="\n"
               , strip.white=T, comment.char="\""
               , quiet=T)
   header <- unlist(strsplit(job[1]," "))
   if (header[1]!=1) {
     stop("Il y a un problème avec le format du fichier")
   }
   if (header[4]!=0) {
     stop("Il y a un problème avec le format du fichier")
   }
   if (length(header)>4) {
     dimp <- grep("DIM=",header)
     if (length(dimp)!=1) {
       stop("Il y a un problème avec la spécification
             du nombre de dimensions")
     } else {
       ndim <- as.numeric(unlist(strsplit(header[dimp]
                          , "="))[2])
     }
   } else {
     ndim <- 2
   }
   nsp <- as.numeric(unlist(strsplit(head[2],"L")[1]))
   nl <- as.numeric(header[3])/ndim
   job2 <- as.character(unlist(strsplit(job[-1], " ")))
   rownam <- as.character(job2[1:nsp])
   if (length(grep("X",job2))==0) {
     landmarks <- as.numeric(job2[(nsp+1):length(job2)])
   } else {
     landmarks <- as.numeric(job2[(nsp+nl*ndim+1):length(job2)])
   }
   data.arr <- aperm(array(landmarks[1:(nsp*ndim*nl)]
                     , dim=c(ndim,nl,nsp)), c(2,1,3))
   tps.data <- list(spname=rownam,landmarks=data.arr)
   return(tps.data)
}
```

## ANNEXE 3 : Exemple d'Analyses morphométriques dans R
Script pour R. Cet exemple d'analyses morphométriques dans R utilise un jeu de données inclus dans le paquet shapes, le jeu de données gorf.dat, qui correspond à des crânes de gorilles femelles.  Aller chercher le script en format texte dans le fichier [[attachment:ExempleAnalysesMorpho.R]].
