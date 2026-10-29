# FILA — Rapport de mise à jour documentaire

Date : 22 octobre 2026  
Source décisionnelle : SRC-008, décisions validées transmises par le fondateur.  
Statut : première intégration, documents **RÉDIGÉS — À VÉRIFIER**; rien n’est réputé validé par un audit technique ou juridique.

## Modifications réalisées

- `DECISIONS.md` : ajout D-023 à D-037 avec provenance, portée, liens touchés; état des questions Q-001..Q-012; nouvelles Q-013..Q-016.
- `REGLES_METIER.md` : ajout RM-031..RM-048, remplacement explicite des règles ouvertes/contradictoires sur identité, affectation, fermeture, absence, analytics et offline.
- `SRS_FILA.md` : mise à jour FR-017/018 pour Analytics V2; FR-025 et NFR-006 corrigées; ajout FR-029..050 et NFR-013..015.
- `PRODUCT_BIBLE.md` : périmètre V1 actualisé; analytics, identité, affectation, QR, ticket inter-salon, fermeture/réactivation, mineurs, notifications, gratuité client, connexion et historique précisés.
- `MODELE_DONNEES.md` : portée identité compte/salon-only, ticket enfant affichage adulte, file manuelle, statuts candidats, événements V1, historique et remplacement inter-salon détaillés; aucun DDL appliqué.
- `ARCHITECTURE_TECHNIQUE.md` : architecture V1 en ligne autoritaire; QR navigateur, OTP, événements opérationnels seulement, Analytics V2, notifications et fermeture manuelle.
- `QUEUE_ENGINE_ANALYTICS_ENGINE.md` : transitions et affectation complétées; les anciens indicateurs/événements analytiques sont désormais V2 uniquement.
- `SPECIFICATIONS_UX_UI.md` et `UX_RESEARCH.md` : nouveaux parcours OTP/QR, profil assisté/enfant, conflit ticket, fermé, réactivation, hors ligne, historique et limites d’analytics.
- `ROADMAP_BACKLOG_TESTS.md` : analytics minimum retiré du MVP et déplacé en V2; réseau, fermeture et exigences rétention actualisés.
- `DOSSIER_INVESTISSEURS.md`, `CONTENU_POWERPOINT.md`, `BUSINESS_MODEL.md` : pas de dashboard ou revenu analytics V1; ticket client gratuit, tarif salon ouvert; contenu du deck aligné.
- `PROMPTS_AGENTS.md` : garde-fous V1 ajoutés.
- `AUDIT_TRACEABILITE_INITIAL.md` : matrice D-023..037 vers règles, exigences, architecture/données, UX et vérification.
- `INDEX_DOCUMENTAIRE.md`, ce rapport, `HISTORIQUE_A_RECONSTITUER.md` et `PROJECT_STATUS.md` : source SRC-008 et état de reprise.

## Contradictions résolues

1. Analytique V1 remplacée par événements opérationnels minimaux V1; Analytics Engine, statistiques et dashboards passent en V2.
2. Fermeture automatique à l’horaire prévu remplacée par horaires informatifs et fermeture manuelle, indépendante par coiffeur.
3. Écriture hors ligne écartée en V1 : Internet et confirmation serveur requis; seule la lecture peut être périmée.
4. Identité universelle précisée : compte numéro vérifié reconnu entre salons; fiche assistée salon-only.
5. Absence par temporisation remplacée par action manuelle du coiffeur après appel.
6. Réactivation et changement de coiffeur formalisés avec conditions de date/fermeture/rang et absence de transfert silencieux.
7. Historique sans durée précisé à 30 jours client et 90 jours salon, sous réserve de validation juridique.
8. Paiement client du ticket écarté en V1; tarification salon non définie.

## Questions encore ouvertes

- Q-013 : validation juridique des règles mineurs et conservation avant essais réels et lancement.
- Q-014 : fournisseur, coût, délivrabilité OTP/notifications et consentement.
- Q-015 : réouverture d’une file après fermeture effective et sort des tickets déjà expirés.
- Q-016 : catalogue de prestations et signal de capacité d’un coiffeur.
- Détails techniques : transaction sûre de remplacement inter-salon, durée de session, sécurité/révocation QR et disponibilité du serveur.

## Vérifications ultérieures

L’archive intégrale demeure absente; SRC-008 ne la remplace pas. Aucun essai terrain, test utilisateur, test logiciel, avis juridique, validation fournisseur, migration, rendu Mermaid ou prototype Figma n’a été réalisé. Les critères de test dans les documents sont prévus, pas exécutés. Les choix techniques restent à éprouver avant implémentation.
