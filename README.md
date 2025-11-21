# Mobilité en Wallonie avant et pendant la pandémie COVID-19

Ce projet s'étale sur deux projets (module 4 et 5) du cours de science des données biologiques 3. Il est indispensable d'avoir assimilé l'ensemble des notions de ces modules. Il correspond au dépôt GitHub <https://github.com/BioDataScience-Course/C04Ga_tseries>.

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

Dans ce travail, nous nous focaliserons sur la période de 2020, qui est la plus impactée d'un point de vue économique en Belgique à cause de la pandémie, ainsi que 2021, qui continue de subir la COVID-19, mais avec des règles moins contraignantes au niveau économique et des déplacements. L'année 2022 est la période la moins affectée par les mesures associées au COVID-19.

## Consignes

À partir des informations dont vous disposez dans le fichier `data/mobility_wallonia.rds` et considérant que l'enjeu est de quantifier l'impact de la COVID-19 sur les déplacements de personnes en Wallonie, expliquez, grâce aux techniques statistiques d'analyse des séries spatio-temporelles, ce qui s'est passé.

Vous effectuerez vos essais documentés dans le carnet de notes `covid_notebook.Qmd`. Ensuite, vous retirerez les éléments clés qui vous permettent de répondre à la question dans le rapport `covid_report.Qmd`. Attention, le rapport de synthèse ne doit pas dépasser 10-15 pages (graphiques compris) et les deux documents doivent être compilables en version HTML sans erreurs.

Les données ont été mises à disposition par Google pour une période de temps limitée. Une sauvegarde locale des données wallonnes a déjà été faite pour vous dans le dossier `data`. Le script `R/import_mobility.R` vous est fourni pour vous montrer comment cela a été réalisé. **Vous ne devez pas exécuter ce code.** Vous pouvez directement importer le fichier `.rds` du dossier `data` dans vos fichiers Rmd et Qmd.

Note : voici un exemple de code qui permet de ne retenir que les jours de la semaine (il est évidemment possible de ne retenir, à l'inverse, que les week-ends), et d'ensuite agréger la série temporelle à une observation moyenne par semaine.

```r
# Copie de la série initiale sous une autre nom
mobw <- mob
# Calcul des jours de la semaine
mobw$weekdays <- weekdays(as.POSIXct(mobw$date))
# Les données du week-end sont remplacées par des valeurs manquantes
mobw[mobw$weekdays == "Saturday" | mobw$weekdays == "Sunday" , 2:7] <- NA 
# La série temporelle est créée (début le 15 février 2020 = 46e jour de l'année 2020)
mobw_ts <- ts(mobw$parks_percent_change_from_baseline, start = c(2020, 46), frequency = 365)
plot(mobw_ts)
# Aggrégation par moyenne des valeurs par semaine
mobw_ts2 <- aggregate(mobw_ts, 52, FUN = collapse::fmean, ts.eps = 1/52)
plot(mobw_ts2)
```


## Important

Faites des commit - pull - push réguliers et gérez les conflits éventuels immédiatement.

Effectuez un 'Rendu' des documents finaux en HTML ou PDF et assurez-vous que ce rendu se fait sans erreurs à la fin de votre travail (c'est très important, car c'est en effet ce document final que l'on souhaite obtenir en éditant un fichier Quarto) !

À la fin, vérifiez que le dernier commit soit bien pris en compte dans votre dépôt sur GitHub. Vos enseignants ne voient que la version GitHub et c'est cette dernière qui sera corrigée et évaluée. Il est donc crucial que vos dépôts locaux soient bien synchronisés avec GitHub à la fin de votre travail.

## Utilisation de l’IA

Dans le cadre de votre travail, vous avez le droit d’être aidé par l’intelligence artificielle. Le chatbot SciViews est disponible dans votre RStudio sur Saturn Cloud via l’addin Help. Il répond aux questions concernant le langage R, les statistiques et la science des données.

