# FILA — Règles métier

Version 0.2 — mise à jour 22 octobre 2026 — **RÉDIGÉ — À VÉRIFIER**. Référence : décisions D-001 à D-022 du registre. Une règle notée « à arbitrer » n’est pas une décision implicite.

## Convention

Les règles **confirmées** sont explicitement posées dans la mission principale du fondateur (SRC-001). Les règles **à arbitrer** identifient l’information nécessaire à l’implémentation sans la choisir à sa place. Les termes « actif », « disponible » et « premier » doivent recevoir des définitions opérationnelles avant développement.

## Identité et création d’un ticket

| ID | Règle | Statut | Exemple / vérification |
|---|---|---|---|
| RM-001 | Une file est liée à un coiffeur dans un salon. | Confirmée | Deux coiffeurs d’un même salon ont des séquences distinctes. |
| RM-002 | Une demande de ticket provient de l’application, d’un QR ou d’un ajout manuel par le coiffeur; les trois voies aboutissent au même moteur central. | Confirmée | Créer des tickets par chaque voie et vérifier une source de vérité commune. |
| RM-003 | Le ticket et son numéro sont créés par FILA; le client ne saisit pas son numéro. | Confirmée | Formulaire ne demande pas de numéro de ticket; numéro attribué après acceptation serveur. |
| RM-004 | Le profil initial client est complété une seule fois; un pseudonyme est permis et le type de prestation est facultatif. | Confirmée | Profil existant réutilisé; profil minimal sans type de prestation accepté. |
| RM-005 | Une personne ne possède qu’un seul ticket actif à la fois. | Confirmée; définition d’identité active à arbitrer | Deux requêtes concurrentes ne créent pas deux tickets actifs pour le même utilisateur. |
| RM-006 | Si l’utilisateur possède déjà un ticket actif ailleurs, une nouvelle entrée est retenue jusqu’à résolution de la situation précédente selon une règle explicite. | Confirmée; actions de résolution à arbitrer | Le système indique le ticket concerné et ne crée pas le second ticket tant que la règle de résolution n’est pas satisfaite. |
| RM-007 | La création confirmée doit être atomique : numéro, attribution, position et événement ne peuvent se contredire. | Déduction technique nécessaire de D-010; validation technique requise | Simulation d’échec entre étapes; aucun ticket partiel ou position double. |
| RM-008 | Les nouvelles tentatives d’une même demande ne doivent pas produire plusieurs tickets. | Recommandation technique de mise en œuvre de D-010, à confirmer en architecture | Répéter une requête avec même clé de demande renvoie le résultat initial ou un rejet explicite. |

## Attribution, ordre et disponibilité

| ID | Règle | Statut | Exemple / vérification |
|---|---|---|---|
| RM-009 | Le client peut choisir un coiffeur précis ou demander le premier disponible. | Confirmée | Les deux choix sont proposés selon contexte salon. |
| RM-010 | Les différences de vitesse et spécialités des coiffeurs doivent être prises en compte dans la conception. | Confirmée; usage opérationnel à arbitrer | Documenter si utilisé pour information, estimation, éligibilité ou ordre. |
| RM-011 | L’ordre de passage doit être explicite, cohérent et vérifiable; aucune règle de priorité payante n’est active dans le MVP. | Confirmée | Toute position peut être expliquée par la règle active; aucune option payante ne change l’ordre MVP. |
| RM-012 | « Disponible » doit reposer sur un état déclaré et compréhensible par le coiffeur. | Besoin de spécification; critères à arbitrer | Définir disponibilité, pause, prestation en cours et file fermée. |
| RM-013 | Analytics ne peut modifier le rang ni choisir le prochain client. | Confirmée | Changer un indicateur analytique ne change pas l’ordre de file. |
| RM-014 | Changement de coiffeur, égalité entre coiffeurs disponibles, client refusant une suggestion et spécialité indisponible requièrent une règle explicite. | À arbitrer | Tests couvrant chaque cas après décision. |

## Cycle de vie et exploitation

| ID | Règle | Statut | Exemple / vérification |
|---|---|---|---|
| RM-015 | Le système doit traiter au minimum annulation, absence, prestation terminée et erreurs de manipulation. | Confirmée; transitions/acteurs à arbitrer | Définir transitions, permissions, confirmations et événements historisés. |
| RM-016 | Chaque changement d’état est validé côté serveur et rattaché à son acteur et heure. | Recommandation d’architecture, pas décision produit déjà détaillée | Vérification par journal d’événements et tests d’autorisation. |
| RM-017 | Une erreur de manipulation doit être corrigée selon des actions autorisées et traçables; l’historique ne doit pas être silencieusement réécrit. | Recommandation de contrôle; à valider techniquement | Cas d’erreur simulé, action de correction visible dans l’historique. |
| RM-018 | Fermeture temporaire, pauses, reprise après incident et comportement lors de file interrompue doivent être définis avant développement. | Question ouverte | Scénarios sans nouveau ticket, tickets déjà actifs et réouverture documentés. |
| RM-019 | Un client sans smartphone ou un enfant peut accéder au service avec l’aide du coiffeur. | Confirmée | Parcours assisté testable sans appareil client et sans rôle gérant obligatoire. |
| RM-020 | L’ajout assisté ne doit pas créer un contournement des règles d’unicité ou une identité fictive non contrôlée. | Conséquence à spécifier de D-005/D-012 | Tester doublon assisté et attribution à un client sans téléphone personnel. |

## QR code et canaux

| ID | Règle | Statut | Exemple / vérification |
|---|---|---|---|
| RM-021 | Le QR est généré côté serveur et affiché/posé par le salon. | Confirmée | QR inconnu ou invalide rejeté par le serveur. |
| RM-022 | Le QR doit être associé à un salon et peut nécessiter une association à un coiffeur. | Confirmée pour besoin d’association; portée à arbitrer | Vérifier le contexte affiché après scan; mauvais salon ne peut être rejoint silencieusement. |
| RM-023 | Tous les salons ne sont pas supposés utiliser les canaux de la même manière; l’accès assisté reste pris en compte dans la conception globale. | Confirmée | Parcours salon sans QR disponible demeure possible par assistance. |
| RM-024 | Le QR ne doit pas exposer d’information personnelle ou conférer des droits privilégiés. | Recommandation de sécurité à valider en conception | Inspection du contenu du QR et tests d’accès. |

## Mesure et données

| ID | Règle | Statut | Exemple / vérification |
|---|---|---|---|
| RM-025 | L’Analytics Engine est distinct du Queue Engine. | Confirmée | Dépendance unidirectionnelle d’événements; moteur de file ne consulte pas les métriques pour ordonner. |
| RM-026 | Les indicateurs visés couvrent clients servis, attente moyenne, durée moyenne, absences, annulations, sollicitation par coiffeur, heures de pointe et canal d’entrée. | Confirmée; formules à définir | Chaque indicateur a événements, bornes temporelles, unités et cas exclusifs spécifiés. |
| RM-027 | Les événements analytiques ne doivent pas contenir plus de données personnelles que nécessaire. | Recommandation de minimisation à traiter dans spécification sécurité | Revue du schéma d’événement et des autorisations. |
| RM-028 | Durées, fuseau local, données incomplètes, tickets réouverts et périodes de calcul doivent être définis. | À arbitrer/ spécifier | Jeu d’événements connu permet de recalculer la valeur attendue. |

## Évolutions commerciales

| ID | Règle | Statut | Exemple / vérification |
|---|---|---|---|
| RM-029 | La voie rapide ou priorité payante est reportée à V2 et exclue du MVP. | Confirmée | Ni UI ni API ni règles MVP ne permettent de payer pour changer le rang. |
| RM-030 | Une éventuelle conception V2 peut être documentée séparément sans changer le comportement MVP. | Confirmée | Toute proposition V2 est marquée future et n’est pas prise en compte dans les tests MVP. |

## Cas à spécifier avant implémentation

1. Deux clients et un coiffeur disponible en même temps; plusieurs demandes « premier disponible » simultanées.
2. Ticket actif lié à un autre salon/appareil, personne sans téléphone, téléphone partagé ou ticket assisté.
3. Coiffeur en pause, file fermée, salon fermé, coiffeur indisponible après affectation.
4. Client arrivé mais absent lors de l’appel; délai et nombre de rappels; retour en file ou annulation.
5. Mauvaise action du coiffeur, demande répétée après réseau lent, réponse serveur perdue après création.
6. QR imprimé périmé, QR partagé hors salon, association incorrecte salon/coiffeur.
7. Interruption réseau pendant lecture, écriture et prestation; récupération sans créer de doublon.

## Conditions préalables

Avant tout codage de file, faire approuver ou documenter les paramètres Q-001 à Q-008 du registre. Les règles confirmées peuvent être implémentées uniquement quand leurs termes nécessaires sont définis et testables. Les exigences de sécurité et conservation sont à préciser avec une revue compétente avant lancement.

## Règles intégrées à partir des décisions du 22 octobre 2026

La présente section complète et remplace les formulations antérieures incompatibles. Source et IDs stables : SRC-008 et D-023 à D-037 dans le registre. Les anciennes RM-001..030 sont conservées; quand leur statut indiquait « à arbitrer », l’arbitrage ci-dessous prévaut.

| ID | Règle intégrée | Exemple / vérification documentaire |
|---|---|---|
| RM-031 | Compte avec numéro vérifié : identité reconnue entre salons. Sans compte, identité assistée/accompagnée limitée au salon; aucune reconnaissance inter-salon garantie. Le salon peut créer une fiche minimale sans téléphone/compte. | Tests de portée identité globale vs salon-only. |
| RM-032 | OTP au premier enregistrement app ou QR web; pas de nouveau code lors des visites suivantes tant que compte et session valides. Sans numéro utilisable : accès assisté. | Parcours première inscription, session valide, numéro indisponible. |
| RM-033 | Le choix explicite d’un coiffeur est respecté; aucune réaffectation silencieuse. | File choisie fermée : informer, laisser choisir un autre coiffeur ou revenir plus tard. |
| RM-034 | « Premier disponible » ne considère que coiffeurs acceptant tickets et capables de la prestation. Choisir la file avec le moins de clients devant le client; égalité : coiffeur dont la dernière attribution est la plus ancienne. Vitesse estimée uniquement pour estimation d’attente, jamais affectation ou promesse. | Cas d’éligibilité, charge, égalité temporelle et estimation séparés. |
| RM-035 | QR propre au salon ouvre un parcours navigateur sans installation; le client choisit coiffeur précis ou premier disponible. | Scan sur navigateur sans app; salon identifié. |
| RM-036 | Ticket global actif ailleurs : demander au client de le conserver ou annuler pour rejoindre la nouvelle file. Ne pas annuler l’ancien avant succès de création du nouveau; si création échoue, ancien inchangé. Pour identité salon-only, pas de prétention à détecter un autre salon. | Échec création laisse l’ancien actif; succès remplace l’ancien sans ticket actif durable en double. |
| RM-037 | Aucune absence automatique V1. Seul le coiffeur peut marquer absent après avoir appelé le client. | Ticket reste appelé tant qu’aucune action manuelle n’est faite. |
| RM-038 | Horaires affichés informatifs; heure prévue n’entraîne fermeture ni blocage automatique. | À l’heure configurée, file ouverte continue d’accepter selon son état réel. |
| RM-039 | Chaque coiffeur ferme sa file manuellement et indépendamment. À fermeture effective, ses tickets non servis expirent, y compris appelés/non démarrés; prestation déjà commencée continue. Les autres files ne changent pas. | Fermeture d’une file ne change pas les autres; état en service conservé. |
| RM-040 | Si le coiffeur choisi a fermé sa file, le client choisit explicitement un autre ouvert ou revient plus tard; pas d’affectation automatique. | Vérification de l’écran de choix alternatif. |
| RM-041 | Avant fermeture effective et le même jour, le coiffeur responsable peut réactiver un ticket. Son action lance les contrôles automatiques; réussite réactive sans deuxième confirmation. Il décide de l’acceptabilité de la justification; si acceptée, rang initial repris. Aucun détail sensible requis. Une prestation en cours n’est jamais interrompue. Les tickets en attente, absents ou non servis expirent à la fermeture; expiré la veille = nouveau ticket requis. | Tests de contrôle automatique, rang conservé, action/auteur journalisés et impossibilité le lendemain. |
| RM-042 | Changement demandé avant appel : ticket en fin de file du nouveau coiffeur. Après appel : demande au coiffeur; seule son action explicite retenue détermine la suite. | Contrôler l’absence de transfert automatique après appel. |
| RM-043 | Aucun compte enfant en V1; ne pas demander téléphone/date de naissance de l’enfant. L’adulte peut gérer un profil d’affichage séparé. Sans compte adulte, profil assisté minimal salon-only. | Formulaires et schéma n’exigent pas données enfant interdites. |
| RM-044 | Analytics Engine, statistiques et tableaux de bord sont V2. En V1, conserver seulement les événements opérationnels nécessaires au ticket/historique (création, appel, absence, réactivation, fin, annulation, expiration). Pas de produit analytique en V1; événements sans effet sur l’ordre. | Pas de dashboard ou calcul statistique au backlog V1. |
| RM-045 | Historique client : 30 jours; opérationnel salon : 90 jours. Après, effacer ou anonymiser les données identifiantes, sous réserve de validation juridique avant essais réels/lancement. Historique chargé à la demande, limité et paginé. | Vérifier droits temporels et pagination; ne pas affirmer conformité légale. |
| RM-046 | Notifications V1 uniquement : création confirmée, approche du tour, appel, annulation, expiration. Promotions/statistiques hors V1, à revoir en V2. | Vérifier que chaque type hors liste est exclu V1. |
| RM-047 | Prendre et suivre un ticket est gratuit pour le client en V1; prix salon à décider séparément et ne bloque pas les règles de file. | Aucun paiement client ne conditionne création/suivi. |
| RM-048 | Création/modification V1 requiert Internet et confirmation serveur. La panne de connexion d’un usager n’empêche pas les autres d’accéder au serveur. Hors connexion : affichage marqué potentiellement ancien, aucune écriture; resynchronisation de lecture à la reconnexion. Serveur injoignable : échec explicite, jamais de faux ticket créé. Pas d’écriture/synchronisation hors ligne ni résolution de conflits en V1. | Tests de lectures périmées, refus écriture offline, sync en ligne et panne serveur explicite. |

### Règles antérieures remplacées

- RM-006 : remplacée par RM-036 (conservation/annulation avec création réussie avant annulation).
- RM-012/RM-014 : remplacées par RM-034 et RM-040 pour disponibilité et égalités d’affectation.
- RM-018 : remplacée par RM-038/RM-039; pas de fermeture prévue par horaire.
- RM-026/RM-028 et section indicateurs de l’Analytics Engine : périmètre de réalisation V1 remplacé par RM-044; indicateurs basculés en V2.
- Ancienne proposition de délai automatique NoShow : remplacée par RM-037.
- Toute recommandation d’écriture hors ligne : remplacée par RM-048.


## Règles intégrées à partir des décisions du 22 octobre 2026

Cette section complète et remplace les formulations antérieures incompatibles. Source : SRC-008, décisions D-023..D-037. Les anciennes RM-001..030 sont conservées; leurs questions arbitrables sont résolues par les règles ci-dessous.

| ID | Règle intégrée | Exemple / vérification documentaire |
|---|---|---|
| RM-031 | Compte avec numéro vérifié : identité reconnue entre salons. Sans compte, identité assistée/accompagnée limitée au salon; aucune reconnaissance inter-salon garantie. Le salon peut créer une fiche minimale sans téléphone/compte. | Tests de portée identité globale vs salon-only. |
| RM-032 | OTP au premier enregistrement app ou QR web; pas de nouveau code aux visites suivantes tant que compte et session valides. Sans numéro utilisable : accès assisté. | Parcours première inscription, session valide, numéro indisponible. |
| RM-033 | Le choix explicite d’un coiffeur est respecté; aucune réaffectation silencieuse. | File choisie fermée : informer, laisser choisir un autre coiffeur ou revenir plus tard. |
| RM-034 | « Premier disponible » ne considère que coiffeurs acceptant tickets et capables de la prestation. Choisir la file avec le moins de clients devant le client; égalité : coiffeur dont la dernière attribution est la plus ancienne. Vitesse estimée uniquement pour estimation d’attente, jamais affectation ou promesse. | Cas d’éligibilité, charge, égalité temporelle et estimation séparés. |
| RM-035 | QR propre au salon ouvre un parcours navigateur sans installation; le client choisit coiffeur précis ou premier disponible. | Scan sur navigateur sans app; salon identifié. |
| RM-036 | Ticket global actif ailleurs : demander au client de le conserver ou annuler pour rejoindre la nouvelle file. Ne pas annuler l’ancien avant succès de création du nouveau; si création échoue, ancien inchangé. Pour identité salon-only, pas de prétention à détecter un autre salon. | Échec création laisse l’ancien actif; succès remplace l’ancien sans ticket actif durablement en double. |
| RM-037 | Aucune absence automatique V1. Seul le coiffeur peut marquer absent après avoir appelé le client. | Temps écoulé seul ne fait pas changer l’état. |
| RM-038 | Horaires affichés informatifs; heure prévue n’entraîne fermeture ni blocage automatique. | À l’heure configurée, file ouverte continue à accepter selon son état réel. |
| RM-039 | Chaque coiffeur ferme sa file manuellement et indépendamment. À fermeture effective, ses tickets non servis expirent, y compris appelés/non démarrés; prestation déjà commencée continue. Les autres files ne changent pas. | Fermeture d’une file ne change pas les autres; état en service conservé. |
| RM-040 | Si le coiffeur choisi a fermé sa file, le client choisit explicitement un autre ouvert ou revient plus tard; pas d’affectation automatique. | Vérification de l’écran de choix alternatif. |
| RM-041 | Avant fermeture effective et le même jour, le coiffeur responsable peut réactiver un ticket. Son action lance les contrôles automatiques; réussite réactive sans deuxième confirmation. Il décide de l’acceptabilité de la justification; si acceptée, rang initial repris. Action/auteur journalisés sans détail sensible. Une prestation en cours n’est jamais interrompue. Les tickets non servis, en attente ou absents expirent à la fermeture; expiré la veille = nouveau ticket requis. | Tests de contrôles, rang conservé, action/auteur sans données sensibles, impossibilité le lendemain. |
| RM-042 | Changement demandé avant appel : ticket en fin de file du nouveau coiffeur. Après appel : demande au coiffeur; seule son action explicite choisit la suite. | Contrôler l’absence de transfert automatique après appel. |
| RM-043 | Aucun compte enfant en V1; ne pas demander téléphone/date de naissance de l’enfant. L’adulte peut gérer un profil d’affichage séparé. Sans compte adulte, profil assisté minimal salon-only. | Formulaires et schéma n’exigent pas les données enfant interdites. |
| RM-044 | Analytics Engine, statistiques et tableaux de bord sont V2. En V1, conserver seulement les événements opérationnels nécessaires au ticket/historique. Pas de produit analytique V1; événements sans effet sur l’ordre. | Aucun dashboard/calcul statistique au backlog V1. |
| RM-045 | Historique client consultable 30 jours; historique opérationnel salon 90 jours. Après, effacer ou anonymiser les données identifiantes, sous réserve de validation juridique avant essais réels/lancement. Historique chargé à la demande, limité et paginé. | Vérifier limites temporelles et pagination; ne pas affirmer conformité juridique. |
| RM-046 | Notifications V1 uniquement : création confirmée, approche du tour, appel, annulation, expiration. Promotions/statistiques hors V1, à revoir en V2. | Vérifier exclusion des autres types V1. |
| RM-047 | Prendre et suivre un ticket est gratuit pour le client en V1; prix salon à décider séparément et ne bloque pas les règles de file. | Aucun paiement client ne conditionne création/suivi. |
| RM-048 | Création/modification V1 requiert Internet et confirmation serveur. La panne de connexion d’un usager n’empêche pas les autres d’accéder au serveur. Hors connexion : affichage marqué potentiellement ancien, aucune écriture; resynchronisation de lecture à la reconnexion. Serveur injoignable : échec explicite, jamais de faux ticket créé. Pas d’écriture/synchronisation hors ligne ni résolution de conflits en V1. | Tests de lecture périmée, refus écriture hors ligne, synchronisation en ligne et échec explicite. |

### Règles antérieures remplacées

- RM-006 : remplacée par RM-036 (conservation/annulation avec création réussie avant annulation).
- RM-012/RM-014 : remplacées par RM-034 et RM-040 pour disponibilité et égalités d’affectation.
- RM-018 : remplacée par RM-038/RM-039; pas de fermeture prévue par horaire.
- RM-026/RM-028 et section indicateurs : réalisation basculée en V2 par RM-044.
- Toute proposition de délai automatique NoShow est remplacée par RM-037.
- Toute recommandation d’écriture hors ligne est remplacée par RM-048.

