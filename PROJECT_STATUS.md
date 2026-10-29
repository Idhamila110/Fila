# FILA — État opérationnel du projet

Dernière mise à jour : 23 octobre 2026  
Source de décisions la plus récente : SRC-008, message de décisions validées transmis par le fondateur.

## 1. État général

- **Phase actuelle :** cadrage documentaire, reprise des décisions validées et revue fondatrice des livrables.
- **Objectif :** présenter des documents cohérents et substantiels pour que le fondateur puisse les vérifier avant mise au propre; ne pas commencer le développement sur des points non tranchés.
- **État général :** corpus de 14 familles documentaires sous `docs/`, index, registre des décisions et présent rapport. Les versions sont des brouillons à vérifier; aucune n’est validée par le fondateur.
- **Blocages :** aucun blocage documentaire empêchant de commencer la conception de l’application sur la base des décisions actuelles. L’archive intégrale `FILA_CHAT_ARCHIVE.md` n’est pas disponible et pourra être intégrée plus tard si nécessaire pour vérifier la provenance historique. Les preuves terrain, la revue juridique et les validations techniques restent à faire avant les étapes qui en dépendent. Pas de code FILA dans le dossier de livrables.
- **Références de reprise :** `docs/00-index-et-etat-du-projet/INDEX_DOCUMENTAIRE.md`, `DECISIONS.md`, `RAPPORT_MISE_A_JOUR_2026-10-22.md`.

## 2. Livrables et progression

| ID | Nom / chemin | Statut | Réalisé | Reste / dépendances | Contrôle et prochaine action |
|---|---|---|---|---|---|
| L-00 | Index, registre, rapport — `docs/00-index-et-etat-du-projet/` | RÉDIGÉ — À VÉRIFIER | Sources SRC-001..008, décisions D-001..037 et bilan SRC-008 documentés. | Reconstituer provenance si l’archive complète est fournie. | Contrôle croisé et reprise de l’archive. |
| L-00A | Historique — `docs/00-index-et-etat-du-projet/HISTORIQUE_A_RECONSTITUER.md` | EN ATTENTE DU FONDATEUR | Absence de l’archive déclarée et pièces nécessaires listées. | Fondateur fournit l’export intégral. | SRC-008 n’est pas l’archive. |
| L-00B | Décisions — `docs/00-index-et-etat-du-projet/DECISIONS.md` | RÉDIGÉ — À VÉRIFIER | D-001..037, statuts, impacts et questions Q-001..016. | Revoir chronologie avec historique complet. | Les décisions du 22-10 sont associées à SRC-008. |
| L-01 | Product Bible — `docs/01-product-bible/PRODUCT_BIBLE.md` | RÉDIGÉ — À VÉRIFIER | Vision, périmètre, parcours, analytics V2, identité et règles V1. | Revue fondatrice, questions produit et données terrain. | Schéma et texte alignés sur Analytics V2; vérifier par fondateur. |
| L-02 | Investisseurs et deck — `docs/02-investisseurs/` | RÉDIGÉ — À VÉRIFIER | Dossier et trame textuelle corrigés sur V1, gratuité client et prix salon ouvert. | Preuves terrain, marché, coûts et budget; création PPTX plus tard. | Pas de PPTX ni de traction inventée. |
| L-03 | Cahier des charges — `docs/03-srs-cahier-des-charges/SRS_FILA.md` | RÉDIGÉ — À VÉRIFIER | FR/NFR et exigences V1/V2 actualisées. | Revue et seuils mesurables. | Aucun test logiciel exécuté. |
| L-04 | Règles métier — `docs/04-regles-metier/REGLES_METIER.md` | RÉDIGÉ — À VÉRIFIER | RM-031..048 ajoutées; règles antérieures remplacées explicitement. | Revue fondatrice des cas limites. | Pas de validation juridique. |
| L-05 | UX Research — `docs/05-ux-research/UX_RESEARCH.md` | RÉDIGÉ — À VÉRIFIER | Protocole et questions actualisés. | Recherche réelle avec participants et consentement. | Aucun résultat de recherche prétendu. |
| L-06 | UX/UI — `docs/06-ux-ui/SPECIFICATIONS_UX_UI.md` | RÉDIGÉ — À VÉRIFIER | Parcours QR, identité, conflit ticket, fermeture, reprise, réseau et historique. | Revue UX, prototype et essais ultérieurs. | Aucun prototype Figma. |
| L-07 | Architecture — `docs/07-architecture-technique/ARCHITECTURE_TECHNIQUE.md` | RÉDIGÉ — À VÉRIFIER | Architecture V1 en ligne et séparation Analytics V2. | Revue technique, ADR, sécurité et coût fournisseur. | Schéma mis à jour; rien n’a été déployé. |
| L-08 | Modèle de données — `docs/08-base-de-donnees/MODELE_DONNEES.md` | RÉDIGÉ — À VÉRIFIER | Modèle logique et journal opérationnel adaptés. | Arbitrer schéma, rôles, statuts et conservation avant DDL. | Aucune migration appliquée. |
| L-09 | Queue/Analytics — `docs/09-queue-engine-analytics/QUEUE_ENGINE_ANALYTICS_ENGINE.md` | RÉDIGÉ — À VÉRIFIER | Règles de file V1, événements ticket et analytics V2. | Revue invariants, états et essais avant code. | Aucun test d’invariants exécuté. |
| L-10 | Business model — `docs/10-business-model/BUSINESS_MODEL.md` | RÉDIGÉ — À VÉRIFIER | Ticket client gratuit en V1; tarification salon non décidée. | Recherche commerciale, coûts et prix réels. | Aucun prix prétendu validé. |
| L-11 | Roadmap et tests — `docs/11-roadmap-et-tests/ROADMAP_BACKLOG_TESTS.md` | RÉDIGÉ — À VÉRIFIER | Analytics produit déplacé en V2; plan de vérification mis à jour. | Priorisation et calendrier fondateur. | Critères proposés, non exécutés. |
| L-12 | Prompts/guides — `docs/12-prompts-et-guides/PROMPTS_AGENTS.md` | RÉDIGÉ — À VÉRIFIER | Garde-fous cohérents avec SRC-008 ajoutés. | Revoir après choix de l’architecture et des outils. | Relecture documentaire uniquement. |
| L-13 | Audit/traçabilité — `docs/13-audit-final/AUDIT_TRACEABILITE_INITIAL.md` | EN COURS | Matrice de traçabilité et contradictions corrigées documentées. | Audit final après revue, tests et validation terrain/juridique. | Ce n’est pas une certification ni un audit technique exécuté. |
| L-14 | Diagrammes — `docs/diagrams/` et diagrammes intégrés | EN COURS | Diagrammes sources conservés et références mises à jour. | Contrôler rendu Mermaid visuellement; enrichir si besoin. | Aucun rendu visuel exécuté. |

## 3. Décisions

Décisions initiales D-001..D-022 et compléments D-023..D-037 figurent dans `DECISIONS.md`. Les règles les plus récentes couvrent compte/OTP et identité salon-only, choix du coiffeur, premier disponible, QR navigateur, remplacement inter-salon, absence manuelle, fermeture manuelle, réactivation, mineurs, Analytics V2, rétention 30/90 jours sous revue juridique, notifications, gratuité client et écritures en ligne confirmées par serveur. Les décisions ne valident pas automatiquement les documents qui les décrivent. Questions et provenance : Q-001..Q-016 dans le registre.

## 4. Questions ouvertes

Voir `DECISIONS.md` pour Q-001..Q-016, leur importance, options et prochaine action. Principaux points à traiter : archive conversationnelle complète; questions produit restantes; validation juridique de la conservation et des mineurs; fournisseur/coûts OTP et notifications; règles après réouverture de file; prestations/capacités; choix d’architecture et seuils NFR. Le fondateur doit également relire et corriger les brouillons.

## 5. Prochaines actions

1. Commencer la conception de l’application à partir du cahier des charges et des décisions D-001..D-037, en conservant les questions ouvertes comme éléments à arbitrer.
2. Le fondateur signale les erreurs ou corrections à apporter aux documents; l’avis favorable exprimé le 22 octobre est consigné comme retour positif, sans convertir automatiquement chaque livrable en « VALIDÉ PAR LE FONDATEUR ».
3. Traiter Q-001..Q-016 au moment où elles affectent les écrans, les données, la sécurité ou les choix techniques; consigner chaque arbitrage.
4. Préparer la recherche terrain et la revue juridique, puis obtenir les validations techniques et fournisseurs avant les étapes qui en dépendent.
5. Intégrer l’archive conversationnelle ultérieurement si elle est fournie, pour compléter la provenance et l’historique; elle ne bloque pas la conception actuelle.

## 6. Fichiers créés ou modifiés

Le lot SRC-008 a modifié ou créé : `docs/00-index-et-etat-du-projet/INDEX_DOCUMENTAIRE.md`, `DECISIONS.md`, `HISTORIQUE_A_RECONSTITUER.md`, `RAPPORT_MISE_A_JOUR_2026-10-22.md`; `docs/01-product-bible/PRODUCT_BIBLE.md`; les deux documents de `docs/02-investisseurs/`; `docs/03-srs-cahier-des-charges/SRS_FILA.md`; `docs/04-regles-metier/REGLES_METIER.md`; `docs/05-ux-research/UX_RESEARCH.md`; `docs/06-ux-ui/SPECIFICATIONS_UX_UI.md`; `docs/07-architecture-technique/ARCHITECTURE_TECHNIQUE.md`; `docs/08-base-de-donnees/MODELE_DONNEES.md`; `docs/09-queue-engine-analytics/QUEUE_ENGINE_ANALYTICS_ENGINE.md`; `docs/10-business-model/BUSINESS_MODEL.md`; `docs/11-roadmap-et-tests/ROADMAP_BACKLOG_TESTS.md`; `docs/12-prompts-et-guides/PROMPTS_AGENTS.md`; `docs/13-audit-final/AUDIT_TRACEABILITE_INITIAL.md`; et ce fichier de statut. Le 23 octobre, le dossier complet a été déplacé dans `C:/Users/DELL 5310/Documents/Codex/vibe coding/FILA/`; l’archive ZIP est conservée dans ce dossier.

Contrôles effectués pour cette reprise : inventaire réel des livrables; lecture de l’index, du rapport et de l’ancien statut; détection et correction de formulations incohérentes dans le diagramme Product Bible, le schéma d’architecture, l’introduction du modèle de données et le visuel du deck. Pas de test logiciel, juridique, terrain, rendu Mermaid ou contrôle de liens déclaré comme fait dans ce lot.

## 7. Dernière session

- **Accompli :** décisions SRC-008 propagées aux documents; anciennes formulations visibles Analytics V1 supprimées dans les visuels repérés; index/rapport disponibles; fondateur indique que les décisions et documents lui paraissent bons et souhaite avancer sans attendre l’archive. Le projet a été rangé dans `Documents/Codex/vibe coding/FILA` avec l’archive ZIP.
- **Inachevé :** conception détaillée de l’application; contrôle exhaustif du rendu des diagrammes et cohérence fonctionnelle à mesure de la conception; terrain, droit et validation technique. L’historique intégral reste souhaitable pour la provenance, mais n’est pas une dépendance de démarrage.
- **Point exact de reprise :** commencer la conception des parcours et écrans depuis `docs/03-srs-cahier-des-charges/SRS_FILA.md`, avec `PRODUCT_BIBLE.md`, `DECISIONS.md` et `SPECIFICATIONS_UX_UI.md` comme références; garder visibles les questions non bloquantes et les signaler dès qu’un choix en dépend.
- **Fichiers prioritaires :** `DECISIONS.md`, `SRS_FILA.md`, `PRODUCT_BIBLE.md`, `REGLES_METIER.md`, `MODELE_DONNEES.md` dans `Documents/Codex/vibe coding/FILA/`.
