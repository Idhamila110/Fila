# FILA — Roadmap, backlog et plan de développement

Version 0.2 — mise à jour 22 octobre 2026 — **RÉDIGÉ — À VÉRIFIER**. Phasage qualitatif; pas de dates, coûts ou engagements chiffrés validés. Priorité payante exclue du MVP.

## 1. Phases et critères de sortie (révision du 22 octobre 2026)

| Phase | Travail | Critère de sortie |
|---|---|---|
| P0 — Reconstitution | Index, décisions, archive disponible, inventaire des documents. | Sources tracées; lacunes affichées; décisions critiques contextualisées. |
| P1 — Recherche produit | Entretiens, observations, benchmark, règles de file, identité, parcours sans smartphone. | Hypothèses majeures confirmées/infirmées; arbitrages métier approuvés; personas prouvés ou conservés provisoires. |
| P2 — Prototype | Flows client/coiffeur, états, QR, erreurs, test d’usage. | Tâches prioritaires comprises; erreurs bloquantes documentées/corrigées. |
| P3 — Conception technique | Architecture, schéma, permissions, contrats, plan de reprise et sécurité. | Revue des invariants, threat model, restauration et choix fournisseurs/coûts. |
| P4 — MVP | Auth et accès retenus, Queue Engine, application Android/iOS, QR et ajout assisté, journal opérationnel des tickets uniquement; Analytics Engine/reporting V2. | Tests d’intégrité/concurrence/permissions/erreurs réussis, builds de test sur plateformes ciblées. |
| P5 — Pilote | Déploiement limité, formation/support, mesure d’usage et fiabilité. | Seuils définis avant pilote atteints ou plan correctif adopté; aucun blocage critique ouvert. |
| P6 — Lancement élargi | Publication et support, acquisition salons et suivi économique. | Capacité opérationnelle, sauvegardes, surveillance, support et modèle de revenu éprouvés. |
| P7 — V2 | Évaluer priorité payante et autres extensions. | Décision explicite et étude d’équité, acceptabilité, coût et faisabilité; hors MVP. |

## 2. Backlog initial par priorité

### P0 — Fondations
- Établir archive et registre de sources (si accessible).
- Confirmer vocabulaire, rôles, états, identité et résolution d’un ticket actif.
- Préparer protocole terrain et questionnaire.

### P1 — Parcours cœur
- Client : trouver le salon, créer profil minimal, choisir coiffeur, recevoir ticket, suivre statut.
- QR : scanner une référence valide du salon et rejoindre la même file.
- Coiffeur : consulter file, ajouter/assister personne, faire avancer ticket, gérer erreur.
- Contrôle serveur : unicité, transaction, idempotence et autorisation.

### P1 — Qualité opérationnelle
- Accès sans smartphone et téléphone partagé.
- File fermée/pausée, indisponibilité, absence, annulation et reprise.
- Analytics d’événements et indicateurs de base.
- État réseau, cache et reprise explicite.

### Hors MVP
- Voie rapide ou priorité payante.
- Modèles prédictifs d’attente non validés.
- Réservation et agenda complet si non requis par recherche.
- Expansion multi-pays et fonctionnalités non vérifiées.

## 3. User stories et critères d’acceptation initiaux

1. **Client — rejoindre une file.** En tant que client, je peux choisir un coiffeur ou demander le premier disponible. Critères : sélection enregistrée côté serveur; règles d’affectation explicables; conflit de ticket existant empêche la création d’un second.
2. **Client — profil minimum.** En tant que client, je peux poursuivre avec pseudonyme et sans type de prestation. Critères : numéro ticket attribué par FILA; aucune donnée superflue obligatoire.
3. **Client — QR.** En tant que client, je peux scanner le QR affiché par le salon et confirmer son identité avant inscription. Critères : QR invalide/révoqué rejeté; salon explicite; aucun secret privilégié dans l’URL.
4. **Coiffeur — assistance.** En tant que coiffeur, j’ajoute un client qui ne dispose pas d’un smartphone. Critères : rôle gérant non requis; champs minimaux; même vérification centrale d’unicité.
5. **Coiffeur — progression.** En tant que coiffeur, je fais avancer la file selon les transitions permises. Critères : action serveur autorisée, état confirmé et correction traçable.
6. **Salon — activité.** En tant que rôle autorisé, je consulte indicateurs de file. Critères : fenêtre/date/fuseau visibles; analytics ne change pas l’ordre.

## 4. Plan de tests à produire

- Unitaires : transitions, règles d’unicité, calculs indicateurs et validation d’entrée.
- Intégration : trois canaux vers moteur central, identité unique, transaction PostgreSQL et rollback.
- Concurrence : demandes simultanées « premier disponible », retry après réponse perdue, deux salons et deux clients concurrents.
- Sécurité : accès inter-salon, escalade de rôle, QR copié/révoqué, RLS et secrets/logs.
- Résilience : réseau interrompu avant/après commit, panne analytics, restauration, rejeu événements.
- UX : tâches client/coiffeur observées, sans aide, lenteur/perte réseau, petits écrans et accessibilité.
- Compatibilité : appareils Android/iOS représentatifs et builds de préproduction.
- Analytics : jeux de données synthétiques avec résultats attendus et cas manquants.

Seuils, appareil représentatif et outils ne sont pas définis; les établir avant implémentation/pilote. **Aucun de ces tests n’est déclaré exécuté.**

## 5. Déploiement et boutiques

Préparer environnements isolés, clés de signature, identifiants éditeur, confidentialité, captures/description, classification d’âge et procédure de support; vérifier les exigences actuelles de Google Play et App Store au moment du lancement. Construire Android et iOS, valider sur appareils réels, soumettre un pilote fermé, traiter retours puis publication progressive. Les comptes développeur, coûts, délais de revue et conformité boutique restent à confirmer.

## 6. Dépendances et risques

Règles Q-001..Q-008; choix auth et identité; QR; disponibilité/suspension; RLS; restauration; accès aux salons; capacité de support; coûts de données et notifications. Toute fonctionnalité bloquée par un choix fondateur doit rester explicitement en attente, sans implémentation supposée.


## 7. Mise à jour du périmètre après décisions du 22 octobre 2026

Source SRC-008 / D-023..D-037. La V1 comprend le QR navigateur sans installation, OTP au premier enregistrement (app ou QR), profils salon-only assistés, affectation déterministe validée, fermeture manuelle par coiffeur, absence manuelle après appel, expiration/réactivation, changement de coiffeur selon l’état du ticket, notifications ticket limitées, écritures uniquement en ligne et historiques limités/paginés. La prise et le suivi de ticket sont gratuits pour le client; prix du salon à décider.

Analytics Engine, calculs statistiques et tableaux de bord ne sont pas dans la phase MVP/P4 : ils sont déplacés en V2. En V1, seuls les événements opérationnels nécessaires à la gestion et à l’historique sont conservés; aucun test ou backlog de dashboard V1 ne doit rester.

La phrase précédente « analytics minimum » de la phase MVP est remplacée par « journal opérationnel des tickets uniquement ». Toute fermeture automatique à l’horaire configuré est supprimée; le coiffeur ferme sa file manuellement. Une fermeture n’expire pas une prestation déjà commencée. La connectivité V1 n’autorise pas les écritures hors ligne : seule la lecture potentiellement périmée est montrée et rafraîchie à la reconnexion.

Avant tout essai réel, faire vérifier juridiquement les règles de données des mineurs et la conservation client 30 jours / salon 90 jours, puis suppression/anonymisation. Cette vérification est requise avant le pilote réel et le lancement; aucun avis juridique n’a été obtenu ici.
