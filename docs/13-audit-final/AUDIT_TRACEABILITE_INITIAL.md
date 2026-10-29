# FILA — Audit de cohérence et matrice de traçabilité (initiale)

Version 0.2 — mise à jour 22 octobre 2026 — **RÉDIGÉ — À VÉRIFIER**. Audit initial des livrables créés dans cette phase; ce n’est pas l’audit final exigé une fois toute la documentation et les tests disponibles.

## 1. Sources et périmètre audité

Sources de décision : mission du fondateur du 17-10 (SRC-001), instruction de mémoire persistante (SRC-002), audits documentaires du 15-10 (SRC-003/004). Documents croisés : Product Bible, SRS, règles métier, architecture, modèle de données, Queue/Analytics Engines, UX Research, UX/UI, dossier investisseurs, business model, roadmap/tests et prompts. Pas de code, prototype fonctionnel ou test logiciel présent.

## 2. Résultat de cohérence initial

- **Cohérent :** file par coiffeur; choix coiffeur/primaire disponible; trois canaux; Queue Engine central; ticket unique actif; accès assisté; analytics séparé; priorité payante hors MVP; Android/iOS; React/Supabase comme orientations à justifier.
- **Questions non contradictoires mais bloquantes avant implémentation :** algorithme premier disponible; identité utilisateur commune aux trois canaux; portée « ticket actif » et absence; transitions/rôles; QR salon/coiffeur; mode hors connexion; fonctions client/notifications; formules d’indicateurs.
- **Historique :** absence d’archive intégrale. Les états et dates des décisions antérieures à la mission du 17-10 ne sont pas reconstitués; les audits du 15-10 restent des documents de phase précédente.
- **Marché :** données démographiques et connectivité sourcées, mais elles ne déterminent pas le nombre de salons, le SAM/SOM ou la volonté de payer. Aucun chiffre commercial inventé.
- **Sécurité :** modèle de données propose unicité partielle et RLS par salon, mais sans matrice d’identité/rôle final; ne pas appliquer comme migration.
- **UX :** wireframes textuels seulement; personas et carte d’empathie sont explicitement provisoires; aucun résultat de recherche ou fichier Figma.
- **Tests :** plan produit; aucun test logiciel déclaré exécuté.

## 3. Matrice de traçabilité initiale

| Exigence | Règle métier | Composant | Écran/parcours | Vérification prévue |
|---|---|---|---|---|
| FR-002 file par coiffeur | RM-001 | Queue Engine / DB `queues` | File coiffeur; choix client | Intégration deux coiffeurs, rangs indépendants. |
| FR-003 choix coiffeur | RM-009 | API/Queue Engine | Sélection coiffeur | Test parcours + attribution serveur. |
| FR-004 premier disponible | RM-009..014 | Queue Engine | Sélection / suggestion | À définir après Q-001; cas concurrence/égalité. |
| FR-006 numéro généré système | RM-003 | API/DB tickets | Confirmation/ticket | API crée numéro; interface ne demande pas numéro. |
| FR-008 un actif par personne | RM-005 | Identité + DB/transaction | Profil et conflit ticket existant | Test parallèle identité reconnue; échec deuxième création. |
| FR-009 résolution ticket ailleurs | RM-006 | Queue Engine | Écran conflit | Test chaque action après arbitrage Q-003. |
| FR-010 trois canaux centralisés | RM-002 | App, QR/web, coiffeur, API | Entrée mobile/QR/assistée | Intégration par canal et invariants communs. |
| FR-011 cohérence concurrence | RM-007/008 | Queue Engine/PostgreSQL | Confirmation/erreur | Test charge, retry, invariant sans rang doublon. |
| FR-012 transitions | RM-015..018 | Queue Engine | Vue file et détail ticket | Tests de transition/role une fois états fixés. |
| FR-013 accès assisté | RM-019/020 | Interface coiffeur/API | Ajouter/assister | Test sans appareil client et sans rôle gérant. |
| FR-015 QR sécurisé | RM-021..024 | Serveur QR/API | Scan et erreur QR | Valide/invalide/révoqué/mauvais salon. |
| FR-017 séparation Analytics | RM-025 | Queue Engine + pipeline analytique | Dashboard | Panne Analytics n’empêche pas la file; ordre inchangé. |
| FR-018 indicateurs | RM-026/028 | Analytics Engine | Dashboard | Jeu synthétique aux formules approuvées. |
| FR-019 Android/iOS | D-019 | Application mobile / pipeline | Tous parcours mobile | Builds et tests sur appareils représentatifs. |
| FR-021 priorité exclue | RM-029/030 | Produit/API | Aucun écran prioritaire MVP | Revue backlog/API et test absence de priorisation payante. |
| NFR-004 cloisonnement | politique attendue du modèle | Auth/RLS/API | Tous espaces | Tests d’accès inter-salon par rôle. |
| NFR-006 réseau intermittent | RM-018 et exigences d’erreur | Client/API/cache | Bannière hors ligne, reprise | Test panne avant/après commit et donnée périmée. |

La colonne écran est conceptuelle tant que wireframes/prototype ne sont pas testés. La colonne test indique une méthode prévue, pas un résultat obtenu.

## 4. Références et vérifications documentaires

Les chemins Markdown cités dans l’index doivent être contrôlés à chaque mise à jour; références inter-fichiers relatives doivent rester résolubles. Diagrammes Mermaid intégrés aux documents doivent être validés par rendu avant export/présentation. Aucun contrôle automatique Markdown/Mermaid n’a été exécuté dans cette rédaction.

## 5. Audit final restant

- intégrer l’archive intégrale ou consigner son absence mise à jour;
- compléter spécifications détaillées, données/API, rôles, authentification et conservation;
- mener recherche terrain et mettre à jour hypothèses/personas;
- vérifier options fournisseurs, sécurité, coûts et obligations locales avec sources actuelles;
- produire protocole pilote, critères seuils et tests exécutés avec preuves;
- réaliser vérification liens, IDs et Mermaid, puis corriger les écarts;
- faire revue technique indépendante et faire valider explicitement les décisions ouvertes par le fondateur.

## 6. Intégration des décisions validées du 22 octobre 2026

Source SRC-008; décisions D-023..D-037. Cette mise à jour corrige l’audit initial : les questions antérieurement bloquantes ci-dessous ont maintenant une règle de cadrage. L’audit final et les vérifications techniques restent à faire.

| Décision | Règles | Exigences | Sections techniques/data | UX | Contrôle à réaliser |
|---|---|---|---|---|---|
| D-023 identité compte vérifié / salon-only | RM-031 | FR-029, FR-031, NFR-013 | Modèle identité/client, autorisation inter-salon | OTP, profil assisté | Tests isolation et portée. |
| D-024 affectation et vitesse non décisionnelle | RM-033/034 | FR-032..034 | Queue Engine, disponibilité, capacité service | Choix explicite/estimation | Tests d’égalité et d’aptitude. |
| D-025 QR navigateur salon | RM-035 | FR-035 | API QR / web | Scan sans app | Parcours web QR. |
| D-026 remplacement ticket actif | RM-036 | FR-036 | Transaction ou orchestration serveur | Écran choix garder/remplacer | Échec création préserve ancien. |
| D-027 absence manuelle après appel | RM-037 | FR-037 | Transition ticket | Action absent après appel | Tentative avant appel rejetée. |
| D-028 fermeture manuelle/expiration | RM-038..040 | FR-038..040, FR-042 | États file/ticket | Horaires informatifs, fermeture par coiffeur | Pas de fermeture horaire automatique; service en cours conservé. |
| D-029 réactivation même jour | RM-041 | FR-041..042 | Transition événement historisé | Contrôles immédiats, résultat clair | Rang d’origine et rôle/auteur. |
| D-030 changement de coiffeur | RM-042 | FR-043 | Transfert de file | Parcours pré/post appel distinct | Avant appel fin de file; après action explicite. |
| D-031 mineurs | RM-043 | FR-044 | Profil enfant lié adulte, pas compte enfant | Profil d’affichage | Revue formulaires et juridique. |
| D-032 vérification OTP | RM-032 | FR-030, FR-031 | Auth, sessions | App/QR première inscription | Vérifier service/fournisseur et session. |
| D-033 Analytics V2 | RM-044 | FR-017/018, FR-045 | Journal opérationnel V1; analytics V2 | Pas de dashboard V1 | Revue de périmètre; ordre invariant. |
| D-034 rétention/pagination | RM-045 | FR-046, NFR-014 | Tables/effacement/anonymisation | Historique sur demande paginé | Avis juridique avant essais réels/lancement. |
| D-035 notifications bornées | RM-046 | FR-047 | Adaptateur notification | Cinq types ticket seulement | Fournisseur, coût, consentement, livraison. |
| D-036 ticket gratuit client | RM-047 | FR-048 | Aucune dépendance paiement côté ticket | Aucun paiement client | Revue parcours; tarif salon séparé. |
| D-037 réseau/serveur autoritaire | RM-048 | FR-049/050, NFR-006/015 | API, cache en lecture, état server | Bandeau de fraîcheur et erreur explicite | Pas d’écriture offline; sync de lecture. |

### Contradictions résolues dans cette mise à jour

- Analytique V1 remplacée par événements opérationnels seulement; dashboards/formules et Analytics Engine en V2.
- Fermeture automatique à l’heure configurée remplacée par horaires informatifs et fermeture manuelle indépendante.
- Écriture hors ligne remplacée par lecture périmée et mutation interdite jusqu’à confirmation serveur.
- Identité globale universelle remplacée par compte/numéro vérifié inter-salon et profil assisté salon-only.
- Timer d’absence remplacé par marquage manuel après appel.
- Réactivation/change de coiffeur non spécifiés remplacés par décisions explicites, conditions temporelles et rang.
- Tickets historiques/statuts sans durée remplacés par accès client 30 jours et opérationnel salon 90 jours, sous validation juridique.
- Hypothèse de facturation client écartée pour V1 : ticket gratuit; tarif salon ouvert.

Les tests inscrits dans la matrice sont à exécuter ultérieurement. Aucun test utilisateur, test logiciel, avis juridique ou validation de fournisseur n’est prétendu réalisé.
