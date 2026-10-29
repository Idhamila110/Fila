# FILA — SRS / Cahier des charges fonctionnel

Version 0.2 — mise à jour 22 octobre 2026 — **RÉDIGÉ — À VÉRIFIER**. Cette première spécification transforme la mission du fondateur en exigences vérifiables. Les paramètres métier non fournis sont explicitement laissés ouverts. « À confirmer » interdit de coder un comportement supposé comme règle définitive.

## 1. Introduction

FILA est un service mobile et opérationnel pour organiser les files de salons de coiffure en Côte d’Ivoire. La présente SRS décrit le socle du MVP, ses utilisateurs, exigences, contraintes et vérifications. Elle est dérivée de la Product Bible v0.1 et du registre D-001..D-022.

## 2. Périmètre

Le système doit permettre la création et gestion de tickets par coiffeur avec application mobile, QR et ajout assisté par le coiffeur. Un moteur de file central garantit la cohérence. L’analyse de l’activité est séparée de l’ordre de passage. Android et iOS sont visés dès le lancement. La priorité payante est hors MVP.

Hors périmètre de cette version : développement logiciel, choix définitif de fournisseur, publication, transactions commerciales, recherche terrain exécutée et preuve de conformité réglementaire. Les documents décrivent le besoin, non une réalisation effective.

## 3. Utilisateurs et rôles

| Rôle | Besoins/capacités envisagés | Statut |
|---|---|---|
| Client | Créer/consulter son ticket, sélectionner coiffeur ou premier disponible, gérer sa situation active suivant règles. | Capacités à préciser. |
| Coiffeur | Voir et faire avancer sa file; assister un client; ajouter un client; corriger des erreurs autorisées. | Rôle confirmé; matrice d’accès à établir. |
| Responsable de salon | Gérer la configuration/QR et accéder aux données pertinentes. | Rôle à confirmer; ne doit pas être requis pour l’accès assisté. |
| Service FILA | Valider règles, attribuer tickets, contrôler accès, produire événements. | Système. |

## 4. Exigences fonctionnelles

**Priorité** : M = indispensable au socle MVP; C = complément à préciser avant lancement; F = futur. Chaque exigence dispose d’une méthode de vérification proposée.

| ID | Exigence | Priorité / statut | Vérification |
|---|---|---|---|
| FR-001 | Le système doit représenter un salon et ses coiffeurs. | M / confirmée | Test d’intégration de création et lecture des rattachements. |
| FR-002 | Le système doit maintenir une file distincte par coiffeur dans le salon. | M / confirmée | Créer tickets pour deux coiffeurs et vérifier indépendance des rangs. |
| FR-003 | Le client doit pouvoir sélectionner un coiffeur précis. | M / confirmée | Test de parcours jusqu’à ticket attribué au coiffeur choisi. |
| FR-004 | Le client doit pouvoir demander le premier coiffeur disponible. | M / confirmée; algorithme ouvert | Tests après définition des critères, égalités, pauses et compatibilité. |
| FR-005 | Le système doit prendre en compte, dans la conception, les différences de vitesse et de spécialité des coiffeurs. | M / portée fonctionnelle ouverte | Revue de conception démontrant la décision sur affichage/estimation/éligibilité; test correspondant. |
| FR-006 | Le ticket doit être créé et numéroté par le système. | M / confirmée | Test API/UI prouvant génération serveur et absence de saisie du numéro. |
| FR-007 | Le profil initial ne doit être demandé qu’une fois; pseudonyme autorisé et type de prestation facultatif. | M / confirmée | Parcours nouvel utilisateur puis retour; création sans type de prestation. |
| FR-008 | Le système doit empêcher plus d’un ticket actif par utilisateur. | M / confirmée | Tests unitaires, intégration et concurrence avec deux demandes simultanées. |
| FR-009 | Si un ticket actif existe ailleurs, le système doit empêcher la nouvelle entrée jusqu’à résolution selon les règles métier. | M / confirmée; résolution à définir | Test de blocage et de chaque action de résolution retenue. |
| FR-010 | Les entrées de l’application, du QR et du coiffeur doivent être traitées par un Queue Engine central. | M / confirmée | Tests d’intégration des trois canaux sur la même API/transaction. |
| FR-011 | Le Queue Engine doit préserver l’unicité de rang/ticket en présence de demandes concurrentes. | M / confirmée à haut niveau | Test de charge/concurrence, inspection contrainte transactionnelle et invariants post-test. |
| FR-012 | Le système doit gérer annulation, absence, fin de prestation et erreur de manipulation. | M / confirmée; détail à définir | Tests de transition et permissions pour chaque état/action approuvés. |
| FR-013 | Le coiffeur doit pouvoir assister un client, notamment sans smartphone, sans rôle de gérant obligatoire. | M / confirmée | Test de parcours complet en compte coiffeur, client sans appareil. |
| FR-014 | Le système doit enregistrer le canal d’entrée d’un ticket. | M / nécessaire aux indicateurs confirmés | Test d’événement pour les trois sources. |
| FR-015 | Le QR doit être généré et validé côté serveur et associé au salon; l’association au coiffeur doit suivre la décision produit. | M / association partiellement ouverte | Tests QR valide, invalide, révoqué et mauvais salon. |
| FR-016 | Le système doit permettre le suivi de la position/état du ticket au client. | M / visée produit; fréquence et détails à préciser | Test de synchronisation de l’état autorisé et présentation de donnée périmée. |
| FR-017 | Analytics Engine, calculs statistiques et tableaux de bord exclus de V1, reportés à V2. Les événements opérationnels de ticket V1 ne sont pas analytics et ne modifient jamais l'ordre. | V2 / D-033 | Revue du périmètre et vérification que ces fonctions ne sont pas en V1. |
| FR-018 | En V2, les indicateurs couvrent clients servis, attentes, durées, absences, annulations, sollicitations, heures de pointe et canaux selon définitions approuvées. | V2 / D-016 précisée par D-033 | Vérifier les calculs V2 sur données synthétiques. |
| FR-019 | Le système doit supporter Android et iOS au lancement. | M / confirmée | Vérification de build et parcours équivalents sur appareils/émulateurs retenus. |
| FR-020 | Les canaux ne doivent pas être supposés activés uniformément dans tous les salons; l’accès assisté reste disponible dans la conception. | M / confirmée | Test de configuration salon et chemin assisté même sans QR. |
| FR-021 | La priorité payante ne doit pas modifier l’ordre du MVP. | M / confirmée | Revue UI/API et test d’absence de voie payante dans le périmètre MVP. |
| FR-022 | Les actions de file doivent être autorisées en fonction du salon et du rôle. | M / sécurité requise, matrice à établir | Tests positifs/négatifs de chaque permission. |
| FR-023 | Les erreurs de réseau ou de validation doivent être compréhensibles et ne doivent pas laisser croire à tort qu’un ticket a été créé. | M / recommandation fonctionnelle à confirmer | Tests d’erreur; comparaison message affiché et état serveur. |
| FR-024 | Le système doit rendre visible la fraîcheur de la position consultée lorsqu’une connexion manque ou que la donnée est en cache. | C / recommandation, à confirmer | Simulation réseau; date/état périmé clairement distingué. |
| FR-025 | Chaque coiffeur ferme manuellement sa file; horaires informatifs sans fermeture automatique. | M / D-028 | Test à l'heure affichée sans fermeture automatique et fermeture isolée d'une file. |
| FR-026 | Toute opération répétée après délai réseau doit être idempotente ou présenter un résultat non ambigu. | M / mécanisme à justifier | Tests de retry avec réponse perdue et contrôle d’unicité. |
| FR-027 | Le système doit permettre à un utilisateur de consulter ou résoudre le ticket actif avant une nouvelle entrée. | M / expérience à définir | Test de navigation et contrôle serveur. |
| FR-028 | Les données d’événements requises pour audit des erreurs et analyses doivent être enregistrées sans données excessives. | M / schéma à définir | Revue de schéma, droits d’accès et tests de minimisation. |

## 5. Exigences non fonctionnelles

Les seuils numériques restent à fixer après pilote et choix de service; ne pas substituer des objectifs arbitraires.

| ID | Exigence | Vérification |
|---|---|---|
| NFR-001 | Une transaction confirmée de file doit préserver les invariants même lorsque plusieurs entrées arrivent simultanément. | Tests de concurrence répétés, contraintes base et inspection de transactions. |
| NFR-002 | Les écritures d’ordre et de statut doivent avoir une autorité serveur; le client mobile ne peut imposer son rang. | Revue API/RLS et tests de requête falsifiée. |
| NFR-003 | Les pannes du composant analytique ne doivent pas empêcher ni réordonner une écriture de file. | Test de panne de l’analytics pendant création/changement d’état. |
| NFR-004 | Les accès aux données doivent suivre le moindre privilège et être cloisonnés par salon. | Tests RLS d’accès inter-salon et rôle. |
| NFR-005 | Les données personnelles doivent être minimisées, protégées en transit et au repos selon les capacités de la plateforme retenue. | Revue de menace, configuration et tests de sécurité. |
| NFR-006 | Toute création/modification exige Internet et confirmation serveur; hors ligne l'affichage indique son ancienneté, les écritures sont interdites, et à reconnexion la lecture se synchronise. Pas de conflit hors ligne en V1. | Test perte réseau, écriture refusée, état périmé et resynchronisation. |
| NFR-007 | L’interface coiffeur doit réduire les interruptions, la saisie et les erreurs pendant une prestation. | Test d’utilisabilité chronométré; objectifs après mesures de référence. |
| NFR-008 | Les opérations critiques doivent être journalisées avec horodatage et acteur sans exposer de secrets. | Inspection logs et tests de permissions/rédaction des logs. |
| NFR-009 | Les sauvegardes et restaurations doivent être documentées et exercées avant lancement. | Exercice de restauration et compte rendu daté. |
| NFR-010 | Les décisions techniques doivent prendre en compte les compétences React du fondateur, la disponibilité Android/iOS et la priorité de fiabilité. | ADR comparatif revu avant sélection. |
| NFR-011 | Les données doivent pouvoir être exportées ou supprimées selon règles de conservation et obligations applicables à définir. | Tests d’export/suppression après politique documentée et revue compétente. |
| NFR-012 | Les interfaces et messages doivent être compréhensibles et testés auprès des publics visés; langues et normes d’accessibilité restent à déterminer. | Protocole de tests terrain; revue accessibilité. |

## 6. Règles métier et cas d’utilisation

Les règles numérotées RM-001 à RM-030 se trouvent dans `../04-regles-metier/REGLES_METIER.md`. Cas d’utilisation minimum : UC-01 rejoindre par mobile; UC-02 rejoindre par QR; UC-03 entrée assistée; UC-04 choisir coiffeur; UC-05 premier disponible; UC-06 consulter ticket; UC-07 appeler/faire avancer; UC-08 terminer, annuler ou marquer absent; UC-09 corriger erreur; UC-10 consulter indicateurs salon.

### UC-03 — Ajout assisté (résumé)

- Acteur principal : coiffeur.
- Précondition : coiffeur autorisé dans le salon; file ouverte selon politique à définir.
- Flux nominal : sélectionner « ajouter/assister client », recueillir seulement l’information minimale, choisir coiffeur ou premier disponible selon demande, confirmer création auprès du Queue Engine, communiquer le numéro/état au client.
- Alternatives : conflit d’un ticket actif, file fermée, réseau absent, mauvais coiffeur, demande répétée. Chaque alternative doit produire un résultat explicite et ne pas créer de doublon.
- Postcondition : un ticket unique est associé à la bonne file et au canal assisté, ou aucun ticket n’est créé et l’erreur est expliquée.

## 7. Sécurité, confidentialité et gestion des erreurs

- Authentification client et coiffeur, récupération de compte/ticket, données requises des enfants et durée de conservation sont des décisions ouvertes.
- L’autorisation doit être vérifiée côté serveur pour chaque salon et action.
- QR ne doit pas contenir de secret d’administration; privilégier une référence non devinable et révocable après revue de conception.
- Éviter d’inscrire téléphone, nom ou contenu d’authentification dans les journaux analytiques.
- Les erreurs doivent distinguer refus métier, indisponibilité réseau, conflit de ticket et erreur serveur, sans déclarer une opération réussie avant confirmation.
- Politique de confidentialité, incidents, suppression, obligations applicables et responsabilités doivent être revues avant pilote public.

## 8. Dépendances et contraintes

- Choix final React Native/Expo, Supabase/PostgreSQL, auth, notifications et déploiement à justifier.
- Android/iOS au premier lancement.
- Recherche d’usage et connectivité au terrain nécessaire pour les seuils de performance, UX et mode dégradé.
- Notifications, coûts et prestataires non confirmés; elles ne doivent pas être une condition de cohérence du moteur.

## 9. Éléments requis avant réalisation

1. Définir états actifs/terminaux et transitions/acteurs.
2. Définir identité et preuve anti-doublon des parcours client et assisté.
3. Définir l’algorithme « premier disponible » et cas de changement.
4. Définir résolution d’un ticket ailleurs, absence, correction et fermeture/reprise.
5. Définir association, révocation et parcours QR.
6. Établir matrice rôles/permissions, politique données et conservation.
7. Définir formules analytiques et seuils NFR avec les données du pilote.

La suite des exigences et leur traçabilité technique/écran/test seront détaillées dans les livrables dédiés et la matrice d’audit final. Aucun test logiciel n’est déclaré exécuté à ce stade.


## 10. Exigences ajoutées et décisions intégrées — 22 octobre 2026

Source SRC-008; décisions D-023..D-037. Elles remplacent toute formulation antérieure de cette SRS qui les contredit. Méthodes de vérification prévues, non exécutées.

| ID | Exigence | Priorité/statut | Vérification |
|---|---|---|---|
| FR-029 | Compte avec numéro vérifié reconnu entre salons; profil sans compte/assisté limité au salon, sans garantie inter-salon. | M / D-023 | Parcours multi-salon compte et profil salon-only isolé. |
| FR-030 | Numéro vérifié par OTP à la première inscription app ou QR web; pas de nouveau code aux visites tant que compte/session valides. | M / D-032 | Test première inscription et nouvelle visite avec session valide. |
| FR-031 | Salon peut créer fiche minimale pour client sans téléphone/compte. | M / D-023/D-032 | Test assisté sans numéro ni compte, isolé au salon. |
| FR-032 | « Premier disponible » filtre coiffeurs acceptant tickets et aptes à la prestation, choisit le moins de clients devant; égalité par attribution la plus ancienne. | M / D-024 | Tests d’éligibilité, charge, égalité et concurrence. |
| FR-033 | Coiffeur choisi précisément respecté; aucune réaffectation silencieuse. | M / D-024 | File fermée présente les options et attend le choix du client. |
| FR-034 | Vitesse estimée sert seulement à afficher estimation d’attente, sans effet sur affectation et sans promesse. | M / D-024 | Modification vitesse ne change pas affectation; libellé indique estimation. |
| FR-035 | QR salon ouvre un navigateur sans installation et donne choix de coiffeur ou premier disponible. | M / D-025 | Parcours sans app installée, salon affiché et ticket centralisé. |
| FR-036 | Ticket actif global ailleurs : proposer conserver l’ancien ou l’annuler pour rejoindre la nouvelle file; annuler l’ancien uniquement après création réussie du nouveau. | M / D-026 | Échec conserve l’ancien; succès remplace sans double ticket actif durable. |
| FR-037 | Aucune absence automatique; le coiffeur ne peut marquer absent qu’après avoir appelé. | M / D-027 | Temps seul ne change pas statut; appel préalable requis. |
| FR-038 | Horaires visibles informatifs; pas de fermeture/blocage automatique à l’heure prévue. | M / D-028 | Test après l’heure sans fermeture manuelle. |
| FR-039 | Chaque coiffeur ferme sa file manuellement et indépendamment. À fermeture, attente/absence/appel non démarré expirent; prestation en cours continue. | M / D-028 | Test isolement des files et conservation état en cours. |
| FR-040 | File choisie fermée : informer et laisser choisir un autre coiffeur ou revenir plus tard; pas de transfert automatique. | M / D-028 | Test du parcours sans réaffectation. |
| FR-041 | Coiffeur responsable peut réactiver le même jour avant fermeture; son action lance les contrôles, réussite réactive sans seconde confirmation; il juge la justification, et si acceptée le ticket retrouve sa place. Action/auteur consignés sans détail sensible. | M / D-029 | Contrôle autorisation, résultats, position et journal sans données sensibles. |
| FR-042 | À fermeture, tickets en attente, absents et non servis expirent. Aucune réactivation le lendemain; le client prend un nouveau ticket. Service en cours jamais interrompu. | M / D-028/D-029 | Test fermeture/date locale et maintien prestation commencée. |
| FR-043 | Changement demandé avant appel place en fin de file du nouveau coiffeur; après appel, demande et action explicite du coiffeur. | M / D-030 | Vérifier fin de file pré-appel et absence de transfert silencieux après appel. |
| FR-044 | Pas de compte enfant ni numéro/date de naissance enfant; l’adulte peut gérer profil d’affichage séparé; sans compte adulte, salon crée profil minimal salon-only. | M / D-031 | Revue formulaire et test parcours assisté; examen juridique séparé. |
| FR-045 | V1 garde seulement les événements opérationnels nécessaires au ticket; aucun calcul statistique ou tableau de bord avant V2. | M / D-033 | Revue du périmètre fonctionnel et des écrans/API. |
| FR-046 | Historique client 30 jours, salon 90 jours, sur demande/paginé; données identifiantes supprimées ou anonymisées ensuite, sous réserve de validation juridique avant essais réels/lancement. | M / D-034 | Tests de pagination/rétention après règle juridiquement vérifiée. |
| FR-047 | Notifications V1 limitées à création confirmée, approche du tour, appel, annulation et expiration; promotion/statistique hors V1. | M / D-035 | Revue des événements de notification. |
| FR-048 | Le client ne paie pas pour prendre/suivre un ticket en V1. | M / D-036 | Aucun paiement exigé dans app, navigateur ou API ticket. |
| FR-049 | Panne de connexion individuelle n’empêche pas les autres usagers joignables au serveur; serveur autoritaire pour ordre et état. | M / D-037 | Test d’isolation connexion par usager. |
| FR-050 | Hors ligne afficher ancienneté et interdire écritures; reconnexion synchronise l’affichage; panne serveur = erreur explicite, pas de faux ticket créé. | M / D-037 | Tests hors ligne, réponse perdue et état à reconnexion. |
| NFR-013 | Portée compte global/profil salon-only isolée; le salon ne lit pas les identités d’autres établissements. | D-023 | Tests accès et isolation inter-salon. |
| NFR-014 | Appliquer rétention 30/90 jours puis anonymisation/suppression, sous réserve de validation juridique avant essai/lancement. | D-034 | Avis juridique puis vérification d’effacement/anonymisation. |
| NFR-015 | Pas d’écriture hors ligne ou fusion hors ligne en V1; état en cache porte sa fraîcheur. | D-037 | Tests réseau dégradé; aucune écriture locale mise en file. |

### Questions réellement ouvertes après arbitrage

Fournisseur, coût et délivrabilité OTP/notifications; durée/révocation QR; obligations applicables à valider avant essais réels/lancement; réouverture d’une file après fermeture effective et sort des tickets expirés; catalogue des prestations/aptitude; durée de session; mécanisme technique de remplacement atomique d’un ticket inter-salon; disponibilité serveur. Ces sujets ne remettent pas en cause les décisions de cadrage ci-dessus.

