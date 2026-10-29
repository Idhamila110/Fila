# FILA — Business model et monétisation

Version 0.2 — mise à jour 22 octobre 2026 — **RÉDIGÉ — À VÉRIFIER**. Aucun tarif, coût, revenu, marge ou volonté de payer n’est connu. Il s’agit d’un cadre d’expérimentation, pas d’une décision du fondateur.

## 1. Valeur économique à vérifier

FILA peut créer de la valeur pour le salon si le système réduit les erreurs de passage, le temps consacré à répondre aux questions d’attente, les pertes liées à la désorganisation ou apporte une clientèle/récurrence. Chacune de ces valeurs doit être quantifiée. Le produit ne doit pas supposer que l’attente ou l’absence représentent aujourd’hui une perte monétaire attribuable à FILA.

## 2. Clients payeurs possibles

- Salon indépendant qui veut organiser plusieurs coiffeurs.
- Coiffeur exploitant son propre espace sans responsable séparé.
- Réseau ou franchise, si cette catégorie est validée par les premiers entretiens.
- Partenaire de paiement/télécom/commerce finançant une expérimentation, sans le présumer.

Le client final est bénéficiaire, mais il n’est pas retenu comme payeur dans le MVP à ce stade.

## 3. Options commerciales comparées

| Option | Avantages possibles | Risques / coûts | Test terrain |
|---|---|---|---|
| Abonnement mensuel par salon | Revenus récurrents, simple à expliquer. | Paiement régulier peut être difficile; valeur doit être visible. | Proposer plusieurs niveaux de prix au salon après usage pilote; demander engagement réel. |
| Prix par coiffeur actif | Suit la taille de la file et le nombre d’utilisateurs opérationnels. | Un salon peut éviter d’ajouter ses autres coiffeurs ou partager des accès. | Tester compréhension et seuil de tolérance avec salon multi-coiffeurs. |
| Gratuit de base + options métier | Réduit barrière d’essai; peut monétiser analytics/support avancés. | Complexité produit, confusion sur limites, coût gratuit. | Vérifier les options qui déclenchent un paiement réel. |
| Frais d’installation/formation | Couvre onboarding et matériel QR; paiement lié à un service concret. | Frein initial et coût d’intervention locale. | Mesurer temps réel de mise en route et volonté de payer pour assistance. |
| Commission transactionnelle | Aligne revenu sur usage si paiements/réservations sont dans le flux. | Complexité et frais de paiement; peut ne pas correspondre au modèle de file. | Ne pas intégrer sans besoin confirmé; tester séparément. |
| Sponsoring/partenariat | Peut financer un pilote ou accès à certains groupes. | Dépendance et objectifs parfois incompatibles. | Valider partenaire et indépendance opérationnelle. |

La priorité payante est explicitement reportée à V2; aucune option ne doit faire payer les clients pour passer avant dans le MVP.

## 4. Coûts à mesurer

- Hébergement, base de données, fonctions serveur et stockage.
- Authentification, SMS/OTP, notifications push et livraison de messages.
- Développement, appareils de test, publication, maintenance et incidents.
- Onboarding, déplacement, impression/renouvellement QR, formation et support.
- Acquisition salon, démonstrations, contenus, partenariats et service client.
- Frais de paiement, conformité, comptabilité, fiscalité et protection des données.

Aucun coût ou tarif de fournisseur n’est inclus avant comparaison actuelle et pilote. Les coûts de SMS doivent être modélisés par scénario et rester hors du chemin critique de la file.

## 5. Scénarios de sensibilité (formules, pas prévisions)

Pour chaque période mensuelle :

- Revenu récurrent brut = salons payants actifs × prix moyen mensuel réellement payé.
- Marge de contribution salon = revenu moyen par salon − coût variable d’hébergement, notification, transaction et support attribuable.
- Coût d’acquisition salon = dépenses de vente/marketing attribuables ÷ nouveaux salons payants acquis.
- Récupération du coût d’acquisition = coût d’acquisition ÷ marge de contribution mensuelle (si marge positive et rétention observée).
- Seuil de salons payants = coûts fixes mensuels ÷ marge de contribution par salon (si marge positive).

Construire les scénarios bas/médian/haut uniquement en renseignant hypothèses explicites et sources; présenter sensibilité au taux de rétention, temps de support, taux conversion et coûts de notification.

## 6. Validation de la disposition à payer

1. Comprendre comment le salon mesure aujourd’hui coût et bénéfice d’une file mieux organisée.
2. Faire tester le produit avant de demander un prix hypothétique.
3. Comparer des propositions commerciales comprises, pas seulement une question « paieriez-vous? ».
4. Tester un engagement concret (pilote payant, dépôt remboursable ou accord de prix) sans pression ni tromperie.
5. Documenter nombre de participants, segment, dates, présentation, objections et conversion.
6. Comparer prix accepté à coûts réels et charge de support.
7. Réviser le modèle avant d’affirmer revenus ou viabilité.

## 7. Décisions en attente

Payeur exact, tarif, fréquence, inclusions gratuites/payantes, traitement des salons ayant peu de coiffeurs, matériel QR, politique de période d’essai, notification incluse ou refacturée, facturation et moyens de paiement. La recommandation provisoire est de commencer par tester un abonnement salon facile à comprendre et un onboarding assisté mesuré, tout en gardant une option de base pour diminuer le frein; ce n’est pas une décision du fondateur.

## 8. Indicateurs économiques

Suivre coût mensuel par salon actif, support/installation par salon, conversion démo→pilote→payant, rétention, revenu réellement encaissé, taux d’échec de paiement, coût SMS par ticket et marge de contribution. Associer chaque chiffre à une période et une source. Tant que ces données n’existent pas, la viabilité demeure inconnue.

## 9. Règles commerciales V1 ajoutées le 22 octobre 2026

Le client ne paie pas pour prendre ou suivre un ticket V1. Aucun paiement client ne peut modifier l’accès, la position ou l’état d’un ticket. La priorité payante reste exclue en V1 et reportée à V2. Une tarification des salons peut être étudiée séparément; elle reste non définie et ne doit pas bloquer la conception ou les règles de file.

Le coût et le prix de l’OTP ainsi que des notifications ticket font partie des coûts à mesurer, mais ne justifient aucune facturation au client. Les notifications V1 sont limitées aux événements de création confirmée, approche du tour, appel, annulation et expiration. Les promotions et statistiques sont V2. L’Analytics Engine et ses dashboards n’apportent aucun revenu V1 puisqu’ils ne font pas partie du périmètre.

Le modèle reste une hypothèse à tester auprès des salons; aucun tarif, engagement, disposition à payer ou revenu n’a été établi.
