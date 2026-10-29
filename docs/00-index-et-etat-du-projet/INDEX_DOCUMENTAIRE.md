# FILA — Index documentaire et état du corpus

Mise à jour : 22 octobre 2026. Sources SRC-001..SRC-008.

## Règles de lecture et statut

- La mission principale du fondateur jointe le 17-10-2026 est la base initiale; SRC-008 du 22-10 ajoute les arbitrages D-023 à D-037. Le registre distingue les deux sources et leurs effets.
- Les décisions acceptées n’impliquent pas que les documents qui les décrivent soient validés. Documents encore à vérifier par le fondateur et/ou par contrôle technique.
- Les rapports d’audit du 15-10 sont des sources secondaires; SRC-008 est un document de décisions, non une archive intégrale. La recherche actuelle confirme l’absence de l’archive dans les fichiers examinés.
- Une recommandation ou hypothèse d’agent n’est pas une décision du fondateur.

## Sources inspectées

| ID | Source | Accès / limite |
|---|---|---|
| SRC-001 | Mission principale FILA jointe le 17 octobre | Lue intégralement; base de décisions explicites et du périmètre documentaire. |
| SRC-002 | Instruction complémentaire historique/mémoire fournie dans la conversation | Lue intégralement; méthode de continuité et contenu obligatoire du suivi. |
| SRC-003 | `C:/Users/DELL 5310/Documents/Codex/2026-10-15/fila-phase-1-audit-g-n/outputs/Audit-FILA-Phase-1.md` | Audit complet lu; état au 15 octobre et limites d’accès aux conversations. |
| SRC-004 | `C:/Users/DELL 5310/Documents/Codex/2026-10-15/fila-phase-1-audit-g-n/outputs/Registre-complementaire-FILA.md` | Registre complet lu; décisions rapportées, mais sources originales absentes. |
| SRC-005 | Inventaire récursif du dossier de travail ouvert et recherche sous `Documents/Codex` | Effectué le 17 octobre; aucun `FILA_CHAT_ARCHIVE.md`/archive correspondante trouvée. Pas de preuve d’absence dans les espaces externes. |
| SRC-006 | Recherche en ligne marché/solutions le 17 octobre | Sources INS, ARTCI, DataReportal et pages de concurrents listées dans le dossier investisseurs/UX. Chaque métrique porte date et limite d’interprétation. |
| SRC-007 | Documentation officielle technique consultée le 17 octobre | Liens Expo/Supabase inclus dans les spécifications; vérifie l’existence d’outils, pas leur adéquation/coût à FILA. |
| SRC-008 | Décisions validées transmises par le fondateur le 22 octobre | Lues intégralement; nouvelle base V1, archive de conversation non incluse. |

## Index des livrables

Statuts permis : NON COMMENCÉ; EN COURS; RÉDIGÉ — À VÉRIFIER; VÉRIFIÉ TECHNIQUEMENT; EN ATTENTE DU FONDATEUR; VALIDÉ PAR LE FONDATEUR; BLOQUÉ. Aucun document n’est annoncé comme validé par le fondateur.

| ID | Livrable / fichier | Statut | Prochaine action |
|---|---|---|---|
| L-00 | `PROJECT_STATUS.md` et dossier index | RÉDIGÉ — À VÉRIFIER | Tenir à jour chaque lot; vérifier liens et état réel. |
| L-00A | `docs/00-index-et-etat-du-projet/HISTORIQUE_A_RECONSTITUER.md` | EN ATTENTE DU FONDATEUR | Intégrer export complet et pièces jointes si accessibles. |
| L-00B | `docs/00-index-et-etat-du-projet/DECISIONS.md` | RÉDIGÉ — À VÉRIFIER | Mettre à jour à l’arrivée de l’archive et des arbitrages. |
| L-01 | `docs/01-product-bible/PRODUCT_BIBLE.md` | RÉDIGÉ — À VÉRIFIER | Revue produit; arbitrer questions critiques. |
| L-02 | `docs/02-investisseurs/DOSSIER_INVESTISSEURS.md`; `docs/02-investisseurs/CONTENU_POWERPOINT.md` | RÉDIGÉ — À VÉRIFIER | Compléter marché de salons, preuve terrain, prix et budget; produire PPTX après données. |
| L-03 | `docs/03-srs-cahier-des-charges/SRS_FILA.md` | RÉDIGÉ — À VÉRIFIER | Définir seuils NFR et compléter matrice. |
| L-04 | `docs/04-regles-metier/REGLES_METIER.md` | RÉDIGÉ — À VÉRIFIER | Revue fondatrice des règles et des cas limites. |
| L-05 | `docs/05-ux-research/UX_RESEARCH.md` | RÉDIGÉ — À VÉRIFIER | Exécuter étude réelle; compléter benchmark par test direct. |
| L-06 | `docs/06-ux-ui/SPECIFICATIONS_UX_UI.md` | RÉDIGÉ — À VÉRIFIER | Tester parcours, créer prototype Figma ultérieurement. |
| L-07 | `docs/07-architecture-technique/ARCHITECTURE_TECHNIQUE.md` | RÉDIGÉ — À VÉRIFIER | Prototype, revue, ADR et coûts fournisseurs actuels. |
| L-08 | `docs/08-base-de-donnees/MODELE_DONNEES.md` | RÉDIGÉ — À VÉRIFIER | Fixer détails de conception avant DDL et politiques RLS finales. |
| L-09 | `docs/09-queue-engine-analytics/QUEUE_ENGINE_ANALYTICS_ENGINE.md` | RÉDIGÉ — À VÉRIFIER | Revoir invariants V1; formules Analytics Engine réservées à V2. |
| L-10 | `docs/10-business-model/BUSINESS_MODEL.md` | RÉDIGÉ — À VÉRIFIER | Tester commercialement et renseigner coûts/prix réels. |
| L-11 | `docs/11-roadmap-et-tests/ROADMAP_BACKLOG_TESTS.md` | RÉDIGÉ — À VÉRIFIER | Définir seuils et calendrier après recherche/arbitrages. |
| L-12 | `docs/12-prompts-et-guides/PROMPTS_AGENTS.md` | RÉDIGÉ — À VÉRIFIER | Adapter aux décisions et outils finaux. |
| L-13 | `docs/13-audit-final/AUDIT_TRACEABILITE_INITIAL.md` | EN COURS | Faire l’audit final après contrôle technique, terrain et tests exécutés. |
| L-14 | `docs/diagrams/architecture-et-flux.md` et diagrammes intégrés | EN COURS | Vérifier le rendu Mermaid et créer les ressources utiles. |

## Arborescence documentaire

`docs/00-index-et-etat-du-projet/` à `docs/13-audit-final/`, ainsi que `docs/diagrams/` et `docs/assets/`. Les sources sont en Markdown modifiable. Les diagrammes Mermaid sont inclus dans Product Bible, UX/UI et spécification des Engines. Aucun PDF, PowerPoint ou prototype Figma n’a été généré.

## Résumé des décisions

D-001..D-022 fixent la base initiale. D-023..D-037 (SRC-008) règlent identité/OTP, affectation, QR navigateur, remplacement d’un ticket, absence/fermeture/réactivation, mineurs, Analytics V2, rétention 30/90 jours, notifications, ticket gratuit client et écritures en ligne. Voir DECISIONS.md pour décisions remplacées et Q-013..Q-016. Voir `DECISIONS.md` pour statuts, provenance, conséquences et questions Q-001..012.

## Reprise

À chaque session : lire `PROJECT_STATUS.md`, cet index et `DECISIONS.md`; vérifier les fichiers sur disque; lire ensuite le livrable concerné. Historique complet et questions majeures restent consignés séparément.

Le lot SRC-008 est décrit dans `RAPPORT_MISE_A_JOUR_2026-10-22.md`. Le statut réel et les prochaines actions détaillées sont maintenus dans `PROJECT_STATUS.md`. L’archive intégrale reste absente, mais le fondateur a indiqué que les décisions et documents actuels sont suffisants pour avancer vers la conception; son absence ne bloque donc pas cette étape.


