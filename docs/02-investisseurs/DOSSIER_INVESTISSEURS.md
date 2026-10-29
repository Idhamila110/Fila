# FILA — Dossier de présentation investisseurs

Version 0.2 — mise à jour 22 octobre 2026 — **RÉDIGÉ — À VÉRIFIER**. Dossier de thèse produit, pas de levée de fonds active. Aucun chiffre de clients, de revenus, de marché adressable, de croissance ou de conversion n’est inventé. Sources publiques consultées le 17 octobre 2026; celles-ci ne remplacent pas une recherche terrain.

## 1. Résumé exécutif

FILA vise à rendre la file d’attente des salons de coiffure plus lisible et plus simple à gérer en Côte d’Ivoire. Le produit organise les tickets par coiffeur et accepte l’entrée par application mobile, QR code navigateur ou ajout assisté par le coiffeur. Un Queue Engine central maintient l’ordre. En V1, FILA conserve uniquement les événements opérationnels des tickets; l’Analytics Engine, les statistiques et tableaux de bord sont reportés à V2.

Le problème et la solution sont une thèse du fondateur à valider auprès des salons et clients. La documentation n’établit encore ni adoption, ni avantage concurrentiel démontré, ni modèle économique final, ni preuve de volonté de payer. Le MVP exclut toute priorité payante; celle-ci est reportée en V2.

## 2. Problème et contexte

Le fondateur décrit de longues attentes lors des périodes de forte affluence, notamment les fêtes, et cible des zones densément peuplées comme Abobo et Yopougon. L’INS donne au RGPH 2021 une population recensée de **1 340 083 à Abobo** et **1 571 065 à Yopougon**; cela renseigne le contexte démographique des zones, mais ne mesure pas le nombre de salons, leur capacité d’achat ou la demande pour FILA ([RGPH 2021, résultats globaux, INS](https://ins.ci/RGPH2021/RGPH2021-RESULTATS%20GLOBAUX_VF.pdf)).

Le besoin opérationnel présumé : suivre l’ordre de passage alors que plusieurs coiffeurs travaillent à des vitesses différentes, que les clients arrivent par plusieurs canaux et que certains n’ont pas de smartphone. Les coûts actuels de ce problème (temps, clients perdus, erreurs, attente) ne sont pas quantifiés.

## 3. Solution et fonctionnement

1. Le client rejoint une file par coiffeur, en choisissant un coiffeur ou en demandant le premier disponible.
2. Le ticket est créé côté système et partagé entre l’application, le QR et l’ajout assisté.
3. Le coiffeur voit et fait progresser sa file avec une interface courte.
4. Le client peut connaître sa position et l’évolution de l’attente; toute estimation doit être présentée avec ses limites.
5. Les événements alimentent des indicateurs salon, sans que l’analyse décide de l’ordre de passage.

## 4. Utilisateurs et proposition de valeur

- **Client :** réduire l’incertitude et voir sa place sans imposer l’installation d’une application au client ponctuel.
- **Coiffeur :** réduire l’ambiguïté sur le prochain passage et enregistrer aussi les clients qu’il assiste.
- **Salon :** obtenir une vue d’activité et d’attente, sous réserve d’une conception qui n’alourdit pas l’exploitation.

Les bénéfices seront mesurés au pilote : temps de traitement d’un ajout, taux d’erreur/doublon, compréhension de l’ordre, utilisation régulière du salon et satisfaction. Aucune valeur de ces indicateurs n’est disponible à ce jour.

## 5. Marché : faits disponibles et limites

- Le RGPH 2021 chiffre la population des communes ciblées à 1,34 million pour Abobo et 1,57 million pour Yopougon. Ces chiffres datent du recensement de 2021 et ne sont pas un décompte de clientèle cible.
- L’ARTCI rapporte pour 2025 38,5 millions d’abonnements actifs à l’internet mobile et 60,7 millions d’abonnements actifs à la téléphonie mobile. Les abonnements sont des lignes, pas des individus uniques, et l’ARTCI indique des données déclaratives des opérateurs dans son rapport ([rapport annuel ARTCI 2025](https://www.artci.ci/images/stories/pdf/qualite_service/DEP/RAPPORT_ARTCI_-_Annuel_2025_030426.pdf)).
- L’ARTCI affiche 41,2 millions d’abonnements au haut débit mobile au T2 2026; cette mesure porte sur les abonnements et ne garantit ni accès individuel, ni données abordables, ni réseau dans chaque salon ([marché ivoirien des communications électroniques, ARTCI, mise à jour 2 septembre 2026](https://artci.ci/?Itemid=78&catid=75%3Aanalyse-des-marches&id=676%3Atableau-synoptique-des-operateurs-fournisseurs-de-services-puissants-identifies-sur-les-marches-pertinents-pour-2015-a-2024&option=com_content&view=article)).
- DataReportal estimait 12,8 millions d’internautes (39,6 % de la population) en janvier 2025, avec des limites liées au délai de production et à la définition de l’accès internet ([Digital 2025: Côte d’Ivoire](https://datareportal.com/reports/digital-2025-cote-divoire)). La série et la définition diffèrent des abonnements opérateurs ARTCI; les chiffres ne doivent pas être additionnés ou assimilés.
- Aucune source examinée ne fournit un nombre actuel et vérifiable de salons de coiffure adressables à Abobo/Yopougon. Le marché adressable doit être construit par recensement terrain et segmentation, pas extrapolé de la population.

### Calcul de marché à compléter (sans hypothèse chiffrée présentée comme fait)

- **TAM** = nombre vérifié de salons correspondant au profil cible dans les géographies prévues × dépense annuelle potentielle par salon.
- **SAM** = salons accessibles compte tenu des canaux, moyens de paiement, langues, connectivité, modèle de vente et capacités d’opération.
- **SOM** = salons réellement activables sur l’horizon de lancement selon capacité de prospection, conversion et rétention mesurées.

Aucune valeur n’est insérée avant d’avoir la méthode de décompte, les hypothèses documentées et un modèle de prix validé.

## 6. Concurrence et alternatives

Scan exploratoire du 17-10-2026 : pages de Nyuman, Planify, Zuri, OnTime et Sheka/Lilix présentent des offres de réservation, découverte beauté ou gestion de rendez-vous. Elles constituent des concurrents ou substituts potentiels sur l’acquisition client, le carnet, la planification et le contact. Les pages consultées ne suffisent pas à prouver qu’elles ne gèrent pas la file sans rendez-vous, leur couverture, leur nombre d’utilisateurs ou leur activité commerciale actuelle.

Alternatives directes à observer : attente dans le salon, carnet papier, mémoire du coiffeur, appels, messages WhatsApp et arrangements de voisinage. Elles ont l’avantage d’être connues et peu coûteuses; FILA doit démontrer un gain supérieur au coût d’apprentissage et de gestion.

Différenciation à tester, non revendiquée comme unique : la file par coiffeur, la coordination centrale multi-canal, l’accès assisté intégré au rôle du coiffeur et l’analytics séparé de la décision d’ordre. Avant présentation externe, effectuer des tests produits, entretiens de salons et audit des offres/prix.

## 7. Modèle économique envisagé

Options à comparer pour les salons : abonnement, prix par salon/coiffeur, installation/accompagnement ou financement partenaire. Aucun modèle n’est choisi. En V1, le client ne paie pas pour prendre ou suivre un ticket.

Le choix doit prendre en compte la valeur mesurée pour le salon, la capacité et fréquence de paiement, les frais de support, connectivité, acquisition, taxes, éventuelles commissions et sensibilité à l’adoption client. La voie rapide payante est hors MVP et ne doit pas être présentée comme moteur de revenus initial.

## 8. Stratégie de lancement proposée

1. Entretiens et observation à Abobo/Yopougon auprès de plusieurs types de salons, avant le développement complet.
2. Prototype des parcours client, QR et coiffeur; tests de compréhension et de saisie.
3. Pilote contrôlé dans quelques salons volontaires, durée et nombre à définir selon capacité réelle; assistance et suivi quotidien.
4. Mesure des indicateurs de fiabilité, temps de tâche, tickets assistés, erreurs, rétention salon et retours clients.
5. Ajustement du prix et du périmètre selon des engagements ou paiements observés, pas des intentions déclarées seules.
6. Extension progressive si les critères de sortie sont atteints et support opérationnel maîtrisé.

## 9. Roadmap indicative

| Phase | Résultat attendu | Condition de passage |
|---|---|---|
| Recherche & cadrage | Règles confirmées, besoins et limites réseau documentés. | Problème et parcours essentiels observés; questions critiques arbitrées. |
| Prototype | Flux client/coiffeur testés, modèle d’identité compris. | Réussite tâches prioritaires et défauts bloquants corrigés. |
| MVP technique | Moteur transactionnel, canaux retenus, journal opérationnel minimum et sécurité. Analytics et tableaux de bord sont V2. | Tests de concurrence, rôles, reprise, Android/iOS et restauration réussis. |
| Pilote | Usage réel et support mesurés. | Seuils décidés à partir d’une référence; pas de blocage sécurité/fiabilité. |
| Extension | Déploiement élargi et modèle économique testé. | Rétention/adoption et coûts unitaires suffisamment documentés. |
| V2 | Évolution commerciale dont priorité payante à étudier séparément. | Décision explicite, validation équité/acceptabilité et faisabilité. |

Les seuils, calendrier et budget ne sont pas encore connus; dates non estimées.

## 10. Indicateurs et besoins de financement

Indicateurs de suivi du pilote : salons activés/hebdomadairement actifs; tickets par canal; taux d’échec/doublon; temps d’ajout assisté; tickets terminés/absents/annulés; compréhension client; coûts variables et support; disposition à payer observée. Les statistiques produit et tableaux de bord relèvent de V2, pas du MVP.

Aucun montant de financement n’est avancé sans roadmap technique, coûts de fournisseurs, salaires/temps fondateur, terrain, publication et support. Un dossier de demande devra lier chaque poste à une étape et un jalon vérifiable.

## 11. Risques

- Adoption faible si la file papier est suffisante ou l’interface ralentit le service.
- Fracture d’accès si une application, un smartphone personnel ou des notifications sont indispensables.
- Erreurs et perte de confiance si une opération concurrente crée plusieurs tickets ou si l’estimation change sans explication.
- Modèle économique non viable si la valeur salon ne couvre pas vente, support et coûts de service.
- Concurrence de réservation et messagerie déjà adoptées.
- Risque de données, mineurs, QR copié ou accès inter-salon.
- Coûts et fiabilité des notifications et réseaux.

## 12. Plan du PowerPoint professionnel

1. Titre FILA — la file de salon, plus lisible.
2. Le problème observé — à illustrer avec récit terrain réel après collecte, aucun témoignage fictif.
3. Le contexte — Abobo/Yopougon (RGPH 2021) et accès numérique (chiffres ARTCI avec définition).
4. Fonctionnement — diagramme des trois canaux et Queue Engine.
5. Produit — maquette client et coiffeur (à concevoir/tester).
6. Pourquoi FILA — différences produit à valider par benchmark.
7. Utilisateurs et cas d’usage.
8. Marché — calcul ascendant après décompte de salons, sans TAM spéculatif.
9. Modèle économique — options et résultats des tests à venir.
10. Lancement — recherche, prototype, pilote, extension.
11. Mesures et preuves — compléter uniquement par données datées et méthode.
12. Risques, équipe et ressources nécessaires.
13. Montant demandé et jalons — laisser en attente des coûts réels.

Pas de PowerPoint livré dans cette phase; ce plan est une trame à compléter quand les preuves et les chiffres seront disponibles.

## Sources publiques consultées

- INS Côte d’Ivoire, *RGPH 2021 — Résultats globaux*, publié 22 juillet 2022 : https://ins.ci/RGPH2021/RGPH2021-RESULTATS%20GLOBAUX_VF.pdf
- ARTCI, *Principaux indicateurs du marché ivoirien des télécommunications en 2025*, rapport annuel 2025 : https://www.artci.ci/images/stories/pdf/qualite_service/DEP/RAPPORT_ARTCI_-_Annuel_2025_030426.pdf
- ARTCI, tableau du marché électronique, T2 2026, mise à jour 02-09-2026 : https://artci.ci/?Itemid=78&catid=75%3Aanalyse-des-marches&id=676%3Atableau-synoptique-des-operateurs-fournisseurs-de-services-puissants-identifies-sur-les-marches-pertinents-pour-2015-a-2024&option=com_content&view=article
- DataReportal, Simon Kemp, *Digital 2025: Côte d’Ivoire*, 03-03-2025 : https://datareportal.com/reports/digital-2025-cote-divoire
- Pages fournisseurs consultées pour le scan concurrentiel, 17-10-2026 : https://www.nyuman.app/ ; https://planify-ci.com/ ; https://zuri-asp.com/ ; https://on-time.pro/logiciel-rendez-vous-cote-divoire ; https://www.sheka.store/.


## 13. Décisions de périmètre intégrées le 22 octobre 2026

La V1 ne comporte pas d’Analytics Engine, de statistiques ou de tableaux de bord. Elle garde seulement les événements opérationnels nécessaires au ticket. Analytics est V2 et ne commande jamais l’ordre. Le client ne paie pas pour prendre ou suivre son ticket V1; la tarification salon reste à décider. Les règles de numéro vérifié, profils salon-only, OTP, fermeture manuelle, expiration, notifications limitées et accès Internet sont décrites dans la Product Bible et la SRS v0.2.

Le deck ne doit donc pas présenter le dashboard comme une capacité MVP. Le périmètre et les formules commerciales restent à valider; aucun revenu ou modèle n’est démontré.

