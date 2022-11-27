# Exercice 1 : Les differents types d'attaque contre les bases de données  
Les 10 principales menaces de sécurité des bases de données

## 1. Abus de privilège excessif  

Lorsque les utilisateurs (ou les applications) ont des privilèges d'accès à une base de données excédant les exigences de 
leur fonction professionnelle, ils peuvent abuser de ces privilèges à des fins malveillantes. Par exemple, un directeur 
d'université dont la fonction n'exige que la capacité à modifier les coordonnées des étudiants peut profiter de 
privilèges de mise à jour de bases de données excessifs pour modifier les notes.
L'utilisateur d'une base de données peut se retrouver avec des privilèges excessifs pour la simple raison que les 
administrateurs de bases de données n'ont pas le temps de définir ni de mettre à jour des mécanismes de contrôle 
granulaire des privilèges d'accès pour chaque utilisateur. Par conséquent, tous les utilisateurs ou les grands groupes 
d'utilisateurs ont des privilèges d'accès génériques définis par défaut qui excèdent largement les exigences de leur 
fonction spécifique.  
## 2. Abus de privilège légitime  
Les utilisateurs peuvent également abuser de privilèges légitimes d'accès à une base de données à des fins non 
autorisées. Imaginez un éventuel fonctionnaire de la santé malveillant ayant des privilèges pour visualiser les dossiers 
médicaux des patients grâce à une application Web personnalisée. La structure de l'application Web limite 
normalement les privilèges des utilisateurs à la visualisation du dossier médical d'un seul patient. Les dossiers multiples 
ne peuvent pas être visualisés de manière simultanée et les copies électroniques ne sont pas autorisées. Cependant, le 
fonctionnaire malveillant peut contourner ces limitations en se connectant à la base de données en utilisant un client 
alternatif tel que MS-Excel. En utilisant MS-Excel et ses propres identifiants de connexion légitimes, le fonctionnaire 
peut récupérer et sauvegarder les dossiers médicaux des patients. Il y a peu de chances pour que de telles copies 
personnelles des bases de données des dossiers de patients respectent les règles sur la protection des données des 
patients définies par les institutions médicales. Il existe deux risques à prendre en considération. Le premier est le 
fonctionnaire malveillant qui tente de revendre les dossiers médicaux des patients. Le second (et peut-être le plus 
commun) est l'employé négligent qui récupère et sauvegarde un grand nombre de données surson ordinateur client à 
des fins professionnelles légitimes. Une fois que ces données sont sauvegardées sur un autre ordinateur, elles 
deviennent vulnérables aux chevaux de Troie, au vol d'ordinateurs portables, etc. 
## 3. Elévation de privilège  
Les auteurs d'attaques peuvent profiter des vulnérabilités des logiciels plate-forme de bases de données pour 
transformer les privilèges d'accès d'un utilisateur ordinaire en ceux d'un administrateur. Les vulnérabilités peuvent se 
trouver dans les procédures enregistrées, les fonctionsintégrées, les implémentations de protocoles, voire même dans 
les données SQL. Par exemple, un développeur de logiciels travaillant dans une institution financière peut profiter 
d'une fonction vulnérable pour s'attribuer des privilèges administrateur d'accès aux bases de données. Avec des 
privilèges administrateur, le développeur malveillant peut désactiver les mécanismes d'audit, créer des comptes 
fantômes, transférer des fonds, etc.
## 4. Exploitation de failles des bases de données vulnérables ou mal configurées   
Les bases de données sont souvent vulnérables, non corrigées ou disposent de comptes et d'une configuration 
toujours définis par défaut. L'auteur d'une attaque qui tente d'exploiter la base de données test généralement les 
systèmes sur ces vulnérabilités, ce qui peut entraîner une violation de sécurité. Alors que les fournisseurs développent 
des packs de correction pour corriger les systèmes au niveau d'une vulnérabilité spécifique, les bases de données des 
entreprises demeurent librement exploitables. Lorsqu'un correctif est lancé, il n'est pas disponible immédiatement. Il 
existe différents aspects à prendre en considération au moment d'appliquer un correctif sur une base de données. Tout 
d'abord, l'organisation doit au préalable évaluer la procédure de correction du système avec le correctif en question, 
en tentant de comprendre comment le correctif affecterait le système. Parfois, un correctif peut être en contradiction 
avec un code déjà existant, ou il peut impliquer d'autres opérations. Ensuite, le système subit un temps d'arrêt lorsque 
le serveur de bases de données ne parvient pas à fournir aux utilisateurs un service afin de le corriger. Enfin, les 
grandes entreprises ayant des dizaines voire des centaines de bases de données doivent prévoir un plan de correction, 
en traitant en priorité les bases de données, celles-ci devant être corrigées en premier. Par conséquent, il n'est pas 
surprenant de voir que pour de nombreuses entreprises, la procédure de correction dure plusieurs mois, généralement 
entre 6 à 9 mois (durée établie sur la base des recherches menées par le groupe indépendant des utilisateurs d'Oracle 
ou IOUG*). Les accès aux bases de données, les administrateurs système et les administrateurs informatiques, les 
développeurs, tous jouent un rôle dans la procédure de correction. Alors que les ressources et le temps sont limités, les 
serveurs demeurent vulnérables pendant des mois aprèsle lancement d'un correctif. 
Des paramètres de compte et de configuration toujours définis par défaut sur une base de données de production 
peuvent être exploités par l'auteur d'une attaque. L'auteur d'une attaque peut tenter d'accéder à la base de données 
en utilisant un compte défini par défaut. Un paramètre d'audit faible peut permettre à l'auteur d'une attaque de 
contourner les contrôles d'audit ou de supprimer toutes traces de ses activités. Des modèles d'identification faibles 
permettent aux auteurs d'attaques de s'identifier comme les utilisateurs légitimes de bases de données en volant ou 
en obtenant les identifiants de connexion.
## 5. Injection SQL  
Dans une attaque par injection SQL, l'auteur insère généralement (ou « injecte ») des informations de bases de 
données non autorisées dans une chaîne de données SQL vulnérable. Généralement les chaînes de données visées 
incluent les procédures enregistrées et les paramètres d'entrée des applications Web. Ces informations injectées sont 
ensuite envoyées vers la base de données où elles sont exécutées. En utilisant l'injection SQL, les auteurs d'attaques 
peuvent obtenir l'accès illimité à l'ensemble d'une base de données.
Prévention de l'injection SQL. Trois techniques peuvent être combinées pour lutter efficacement contre l'injection SQL : 
La technologie de prévention des intrusions (IPS), le contrôle d'accès des requêtes (voir la section Abus de privilège 
excessif), et la corrélation d'événements. La technologie IPS peut identifier les procédures enregistrées vulnérables ou 
les chaînes d'injection SQL. Cependant, la technologie IPS seule n'est pas fiable puisque les chaînes d'injection SQL sont 
sujettes à des faux positifs. Les responsables de la sécurité qui compteraient uniquement sur la technologie IPS seraient 
bombardés d'alertes au sujet de « possibles » injections SQL. Cependant, en établissant une corrélation entre une 
signature d'injection SQL et un autre type de violation tel qu'une violation du contrôle d'accès de requête, une réelle 
attaque peut être identifiée de manière très précise. Une signature d'injection SQL et un autre type de violation ont 
peu de chance d'apparaître dans la même requête au cours d'une opération professionnelle classique.
## 6. Faiblesse de l’audit natif  
Un enregistrement automatique de toutes les transactions de bases de données sensibles et/ou inhabituelles devrait 
être la base sous-jacente de tout déploiement de base de données. Une faible règle d'audit des bases de données 
représente un sérieux risque organisationnel à plusieurs niveaux.  
» Risque au niveau des réglementations – les organisations utilisant de faibles mécanismes d'audit des bases de 
données (ou parfois inexistants) réaliseront de plus en plus qu'elles ne respectent pas les réglementations 
gouvernementales. La réglementation Sarbanes-Oxley (SOX) dans le domaine des services financiers et le Healthcare 
Information Portability and Accountability Act ou HIPAA (loi sur la portabilité et la comptabilité des soins de santé) dans 
le domaine de la santé ne sont que deux exemples de réglementations gouvernementales imposant des exigences 
claires au niveau de l'audit des bases de données.  
» Dissuasion – à l'instar des caméras vidéo qui enregistrent les visages des personnes entrant dans une banque, les 
mécanismes d'audit des bases de données servent à dissuader les auteurs d'attaques qui savent que le suivi des audits 
des bases de données fournit aux enquêteurs des informations criminalistiques sur les auteurs d'un crime.  
» Détection et récupération – les mécanismes d'audit représentent la dernière ligne de défense des bases de données. 
Si l'auteur d'une attaque parvient à contourner d'autres systèmes de défense, les résultats des audits peuvent identifier 
l'existence d'une violation après l'attaque. Les résultats des audits peuvent ensuite être utilisés pour faire un lien entre 
une violation et un utilisateur en particulier et/ou réparer le système.
Les plateformes de logiciels de bases de données intègrent généralement des fonctionnalités d'audit basiques mais 
elles présentent de multiples faiblesses qui limitent ou empêchent leur déploiement.  
» Manque d'imputabilité des utilisateurs – lorsque les utilisateurs accèdent à une base de données via des applications 
Web (telles que SAP, Oracle E-Business Suite, ou PeopleSoft), les mécanismes d'audits natifs ne connaissent pas les 
identités des utilisateurs spécifiques. Dans ce cas, toutes les activités d'un utilisateur sont associées au nom de compte 
de l'application Web. Par conséquent, lorsque les résultats des audits natifs révèlent l'existence de transactions de 
bases de données frauduleuses, aucun lien ne peut être effectué avec l'utilisateur responsable.  
» Dégradation des performances – les mécanismes d'audit de bases de données natives sont connus pour consommer les 
ressources de l'unité centrale et du disque dur. La dégradation des performances observée lorsque les fonctionnalités 
d'audit sont activées force de nombreuses organisations à réduire le nombre d'audits ou simplement à les supprimer.
» Séparation des fonctions – les utilisateurs ayant des droits d'accès administrateur (obtenus soit de façon légitime ou 
malveillante – voir la section Elévation de privilège) au serveur de bases de données peut facilement désactiver la 
fonctionnalité d'audit pour dissimuler une activité frauduleuse. Idéalement, les fonctions d'audit devraient être séparées 
de celles des administrateurs de bases de données et de celles de la plate-forme du serveur de bases de données.  
» Granularité limité – de nombreux mécanismes d'audit natifs n'enregistrent pas les informations nécessaires pour 
prendre en charge la détection des attaques, les enquêtes criminalistiques et la récupération.
Par exemple, l'application client des bases de données, les adresses IP sources, les éléments de réponse des requêtes, 
et les requêtes ayant échoué (un indicateur important de reconnaissance d'attaque) ne sont pas enregistrés par de 
nombreux mécanismes natifs.  
» Propriétaire – les mécanismes d'audit sont propres à la plate-forme du serveur de bases de données. Les résultats 
d'Oracle sont différents des résultats de MS-SQL, les résultats de MS-SQL sont à leur tour différents des résultats de 
Sybase, etc. Pour les organisations qui combinent les environnements de bases de données, cela élimine littéralement 
l'implémentation de procédures d'audit uniformes et évolutives dans l'entreprise.
## 7. Déni de service  
Le déni de service (DOS - Denial Of Service) est une catégorie d'attaque générale par laquelle l'accès aux applications 
réseau est refusé à certains utilisateurs. Les conditions de déni de service peuvent être créées par de nombreuses 
techniques, parmi lesquelles beaucoup sont liées aux vulnérabilités mentionnées précédemment. Par exemple, le déni 
de service peut être obtenu en profitant de la vulnérabilité d'une plate-forme de bases de données pour faire tomber 
un serveur. D'autres techniques communes de déni de service incluent la corruption de données, l'engorgement du 
réseau, et la surcharge en ressources du serveur (mémoire, unité centrale, etc.). La surcharge desressources est une 
technique très commune dans les environnements de bases de données. Les motivations qui se cachent derrière les 
attaques par déni de service sont aussi diverses. Les attaques par déni de service sont souvent liées aux tentatives 
d'extorsion par lesquelles un pirate informatique fait planter des serveurs à distance et de manière répétée jusqu'à ce 
que la victime place ses fonds sur un compte bancaire international. Le déni de service peut également être lié à une 
infection par un ver informatique. Quelle que soit la source, le déni de service représente une menace sérieuse pour de 
nombreuses organisations.
## 8. Vulnérabilités des protocoles de communication des bases de données  
Un nombre croissant de vulnérabilités de sécurité sont identifiées dans les protocoles de communication des bases de 
données conçus par tous les fournisseurs de bases de données. Quatre des sept correctifs de sécurité inclus dans les 
deux derniers packs de correction IBM DB2 traitent des vulnérabilités des protocoles de type 1. De la même façon, 11 
des 23 vulnérabilités de bases de données corrigées dans le dernier correctif trimestriel d'Oracle ont un rapport avec 
les protocoles. Les activités frauduleuses prenant pour cible ces vulnérabilités peuvent aller de l'accès aux données non 
autorisées, à la corruption de données, en passant par le déni de service. Le ver informatique SQL Slammer2, par 
exemple, a profité d'une faille sur le protocole du serveur Microsoft SQL pour forcer un déni de service. Pour rendre la 
situation plus difficile, aucun enregistrement de ces vecteurs de fraude n'existe dans la piste d'audit native puisque les 
opérations de protocole ne sont pas couvertes par les mécanismes d'audit de bases de données natives. Prévention 
des attaques de protocoles de communication des bases de données. Les attaques de protocoles de communication 
des bases de données peuvent être vaincues grâce à une technologie communément appelée validation de protocole. 
La technologie de validation de protocole décompose (désassemble) essentiellement le trafic des bases de données et 
le compare aux prévisions de trafic. Dans le cas où le trafic réel ne correspond pas aux prévisions, des alertes ou des 
actions de blocage peuvent être mises en place. 
SecureSphere Database Communication Protocol Validation (technologie de validation de protocole de 
communication)
La technologie SecureSphere Database Communication Protocol Validation vérifie et protège contre les menaces de 
protocoles en comparant les protocoles de communications des bases de données réels aux structures de protocoles 
attendues. Aucune autre solution de sécurité ou d'audit de bases de données ne fournit cette possibilité. Elle est 
dérivée des recherches en cours du centre de défense des applications d’Imperva (ADC) sur les vulnérabilités et les 
protocoles de communication des bases de données propriétaires. Des fournisseurs d'applications et de bases de 
données y compris Oracle, Microsoft, et IBM ont attribué au centre de défense des applications d’Imperva la 
découverte de sérieuses vulnérabilités et de techniques de limitation ayant contribué à augmenter la sécurité de leurs 
produits. Sur la base de ces recherches, Imperva est capable d'intégrer des connaissances techniques sur les protocoles 
inégalées dans ses solutions SecureSphere. 

## 9. Copies non autorisées de données sensibles  
De nombreuses entreprises s'efforcent de localiser et maintenir de manière appropriée un inventaire de toutes leurs 
bases de données. De nouvelles bases de données peuvent être créées sans que l'équipe responsable de la sécurité 
soit au courant et les données sensibles copiées dans ces bases de données peuvent être exposées si les contrôles 
nécessaires ne sont pas appliqués. Ces bases de données « cachées » peuvent contenir des données potentiellement 
sensibles telles que les détails des transactions, ainsi que les coordonnées des clients et des employés. Cependant, si les 
personnes chargées de la sécurité des données ne connaissent pas le contenu de ces bases de données, il est difficile 
de s'assurer que les contrôles nécessaires ont été appliqués. Que ce soit de manière intentionnelle ou non, les 
employés ou les pirates informatiques peuvent alors accéder illégalement aux données sensibles. Les anciennes bases 
de données qui ont été oubliées et laissées hors du champ d'évaluation sont un autre exemple. Si personne ne gère ces 
bases de données, les données sont laissées sans surveillance à la vue des regards indiscrets qui ne devraient pas 
accéder à ces données. 
## 10. Exposition de données de sauvegarde  
Les dispositifs de sauvegarde de bases de données auxiliaires ne sont généralement pas protégés contre d'éventuelles 
attaques. Par conséquent, plusieurs violations de sécurité importantes ont vu le jour, y compris le vol de disques durs 
et de bandes de sauvegarde de bases de données.  



# Exercice 2 : Les extensions des fichiers des SGBD suivants  
## MySql
 Chaque fois que l’installation de la base de données MySQL est terminée, toutes les données et métadonnées liées à la base de données sont stockées dans un dossier. Il s’agit du schéma de base de données réel avec certaines valeurs. Laissez-nous explorer plus à ce sujet. 
Les extensions de fichier sont les suivantes : 
 

.frm – Il s’agit de l’extension du fichier qui contient le schéma ou la définition de la table.  
.myd – Il s’agit de l’extension du fichier qui contient les données de la table MyISAM.  
.myi – Il s’agit de l’extension du fichier qui contient les index de table MyISAM.  
Dans le dossier MySQL Server 5.5/data/mysql , certains des fichiers sont *.frm , *.MYD et *.MYI , 
où les astérisques sont des noms de table réels. Si le moteur MyISAM est utilisé, le dossier de données contiendra tous les fichiers ci-dessus, sinon dans le cas d’InnoDB, le dossier contient des fichiers .frm .   

Ces fichiers de base de données sont utilisés à des fins de sauvegarde pour sécuriser le schéma, les données et les index pour une migration ou une mise à niveau de la base de données. Les fichiers de configuration de MySQL pour Windows et Linux sont respectivement my.ini et my.conf 

## Oracle  
Les extensions du gestionnaire de fichiers sont installées par l'administrateur système.

Voici certaines extensions populaires du gestionnaire de fichiers :

nautilus-actions : vous permet d'affecter des actions en fonction du type de fichier.

nautilus-send-to : propose une méthode simple pour envoyer un fichier ou un dossier par courrier électronique, messagerie instantanée ou Bluetooth.

nautilus-open-terminal : propose une méthode simple pour ouvrir un terminal à l'emplacement de démarrage sélectionné

## Postgresql

Cette section décrit le format de stockage au niveau des fichiers et répertoires.

Traditionnellement, les fichiers de configuration et les fichiers de données utilisés par une instance du serveur sont stockés ensemble dans le répertoire des données, habituellement référencé en tant que PGDATA (d'après le nom de la variable d'environnement qui peut être utilisé pour le définir). Un emplacement courant pour PGDATA est /var/lib/pgsql/data. Plusieurs groupes, gérés par différentes instances du serveur, peuvent exister sur la même machine.

Le répertoire PGDATA contient plusieurs sous-répertoires et fichiers de contrôle. En plus de ces éléments requis, les fichiers de configuration du groupe, postgresql.conf, pg_hba.conf et pg_ident.conf sont traditionnellement stockés dans PGDATA 

# Exercice 3: Definition de la politique de sécurité de l'ITSEC

Les ITSEC définissent la politique de sécurité conne l'ensemble des lois règles ou pratiques qui régissent la facon dont l'information sensible et les autres ressources sont gérées, protégées et distribuées à l'intérieur d'un système d'Information