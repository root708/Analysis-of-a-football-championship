# Analysis of a Football Championship

Analyse avec **Pandas** d'un championnat de football fictif, la **Ligue Pro** (20 clubs), sur trois saisons : 2023-2024, 2024-2025 et 2025-2026.

> TP2 — Python Avancé · Licence 3 Intelligence Artificielle · ISM École d'ingénieurs

## Contenu du dépôt

```
Analysis-of-a-football-championship/
├── analysis.ipynb        # Notebook d'analyse (nettoyage, classements, rapport)
├── requirements.txt      # Dépendances Python
├── README.md
└── data/
    ├── equipes.csv       # 20 clubs (ville, stade, budget…)
    ├── matchs.csv        # Matchs : scores, tirs, possession, spectateurs
    ├── joueurs.csv       # Statistiques par joueur et par saison
    ├── buts.csv          # Chaque but : minute, buteur, passeur, type
    └── rapport_ligue.xlsx  # Rapport exporté par le notebook (3 feuilles)
```

## Données

| Fichier | Lignes (brut) | Description |
|---|---|---|
| `equipes.csv` | 20 | Identité et budget des clubs |
| `matchs.csv` | 1 145 | Matchs des 3 saisons |
| `joueurs.csv` | 1 688 | Une ligne par joueur et par saison |
| `buts.csv` | 2 660 | Un but par ligne (jeu ou penalty) |

Les données brutes contiennent volontairement des défauts (doublons, salaires en texte, postes mal écrits, valeurs manquantes), traités dans la partie 2 du notebook. Après nettoyage : **1 140 matchs, 1 680 lignes joueur-saison, 2 654 buts**.

## Plan du notebook

1. **Chargement et diagnostic** : types, valeurs manquantes, doublons, incohérences.
2. **Nettoyage** : doublons, harmonisation de `poste`, conversion des salaires, imputation (médiane par poste et saison), décomposition des minutes (`90+3`), spectateurs manquants.
3. **Classements** des trois saisons, construits à partir de la vue domicile/extérieur, avec contrôles de cohérence.
4. **Analyses** : meilleurs buteurs, avantage du terrain, affluence, répartition des buts dans le temps, penalties et passes, lien budget/résultats, carrières des joueurs, contrôles croisés.
5. **Export** vers `data/rapport_ligue.xlsx` (feuilles `Classements`, `Buteurs_2025-2026`, `Affluence_2025-2026`).
6. **Bonus** : la course au titre 2025-2026, journée par journée.

## Quelques résultats

- **Étoile du Cap-Vert** est sur le podium les trois saisons (championne en 2023-2024 avec 88 points).
- Meilleur buteur 2025-2026 : **Modou Thiam** (Niayes Académie), 19 buts.
- L'avantage du terrain recule en 2025-2026 : plus de matchs nuls (30,5 %).
- Les buts sont plus fréquents en fin de match (tranche 76-90 : 22,5 % des buts).
- Forte corrélation entre masse salariale et points en 2025-2026 (Pearson 0,82), sans qu'on puisse conclure à une causalité.
- La tête du classement 2025-2026 a changé de mains 7 fois.

## Lancer le projet

```bash
git clone https://github.com/TON-PSEUDO/Analysis-of-a-football-championship.git
cd Analysis-of-a-football-championship
pip install -r requirements.txt
jupyter notebook analysis.ipynb
```

Le notebook lit les fichiers dans `data/` : il faut l'exécuter depuis la racine du dépôt.
