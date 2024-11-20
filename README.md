# Mobilité en Wallonie avant et pendant la pandémie COVID-19

## Avant-propos

Ce projet s'étale sur deux projets (module 4 et 5) du cours de Science des données Biologiques 3. Il est indispensable d'avoir assimilé l'ensemble des notions de ces modules. Il correspond au dépôt GitHub <https://github.com/BioDataScience-Course/C04Ga_tseries>.

## Objectifs

Ce projet est **libre** et à réaliser en **équipe**. Il permettra de nous démontrer que vous avez acquis les compétences suivantes :

-   Être capable de manipuler et de décrire une série spatio-temporelle.

-   Maîtriser l'analyse de séries spatio-temporelles.

-   Comprendre et appliquer la décomposition de séries spatio-temporelles.

## Informations sur les données employées

Google met à disposition des données sur la mobilité des communautés durant le COVID-19 <https://www.google.com/covid19/mobility/>. Les données ne sont plus actualisées depuis le 15 octobre 2022. Une application interactive accessible depuis <https://dimiter.shinyapps.io/covid-19_mobility/> vous permet de visualiser les données nationales de manière interactive (et vous pouvez lisser ces données à l'aide d'une moyenne mobile jusqu'à 7 jours dans cette application). Google propose des rapports descriptifs des données. Trois rapports vous sont proposés ci-dessous :

-   <https://www.gstatic.com/covid19/mobility/2020-11-13_BE_Wallonia_Mobility_Report_fr.pdf>
-   <https://www.gstatic.com/covid19/mobility/2021-11-26_BE_Wallonia_Mobility_Report_fr.pdf>
-   <https://www.gstatic.com/covid19/mobility/2022-10-15_BE_Wallonia_Mobility_Report_fr.pdf>

Dans ce travail, nous nous focaliserons sur la période de 2020, qui est la plus impactée d'un point de vue économique en Belgique à cause de la pandémie, ainsi que 2021, qui continue de subir le COVID-19, mais avec des règles moins contraignantes au niveau économique et des déplacements. L'année 2022 est la période la moins affectée par les mesures associées au COVID-19.

## Consignes

À partir des informations dont vous disposez dans le fichier `data/mobility_wallonia.rds` et considérant que l'enjeu est de quantifier l'impact de la COVID-19 sur les déplacements de personnes en Wallonie, expliquez, grâce aux techniques statistiques d'analyse des séries spatio-temporelles, ce qui s'est passé.

Vous effectuerez vos essais documentés dans le carnet de notes `docs/mobility_notebook.Qmd`. Ensuite, vous retirerez les éléments clés qui vous permettent de répondre à la question dans le rapport `docs/mobility_report.Rmd`. Attention, le rapport de synthèse ne doit pas dépasser 10-15 pages (graphiques compris) et les deux documents doivent être compilables en version HTML sans erreurs.

Les données ont été mises à disposition par Google pour une période de temps limitée. Une sauvegarde locale des données wallonnes a déjà été faite pour vous dans le dossier `data`. Le script `R/import_mobility.R` vous est fourni pour vous montrer comment cela a été réalisé. **Vous ne devez pas exécuter ce code.** Vous pouvez directement importer le fichier `.rds` du dossier `data` dans vos fichiers Rmd et Qmd.

Voici quelques éléments ou questions qui doivent vous permettre d'alimenter votre réflexion sur l'analyse de cette série spatio-temporelle :

-   Le gouvernement a imposé des mesures de confinement plus ou moins fortes. Est-il intéressant de découper la série en plusieurs parties afin de tenir compte des mesures de confinement ?

-   La mobilité est influencée par l'effet semaine/week-end. Est-il intéressant de réaliser différentes agrégations des données ou encore des découpages dans les données ?

## Important

Faites des commit - pull - push réguliers et gérez les conflits éventuels immédiatement.

Effectuez un 'Rendu' des documents finaux en HTML ou PDF et assurez-vous que ce rendu se fait sans erreurs à la fin de votre travail (c'est très important car c'est en effet ce document final que l'on souhaite obtenir en éditant un fichier Quarto) !

À la fin, vérifiez que le dernier commit soit bien pris en compte dans votre dépôt sur GitHub. Vos enseignants ne voient que la version GitHub et c'est cette dernière qui sera corrigée et évaluée. Il est donc crucial que vos dépôts locaux soient bien synchronisés avec GitHub à la fin de votre travail.
