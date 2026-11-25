# Spec du moteur — Règles du Giretra

> Version : **v0.1 (brouillon)** · Source : [synthèse giretra.com](source/giretra-regles-synthese.md)
> Les règles marquées ⚠️ dépendent d'une [question ouverte](open-questions.md).

## Conventions

- **Places** (sens horaire) : `Sud → Ouest → Nord → Est → Sud…`
- **Équipes** : `NS` (Nord + Sud) et `EO` (Est + Ouest). Les coéquipiers sont face à face.
- **« À gauche de X »** = le joueur suivant X dans le sens horaire.
- **Enseignes** : `♣ Trèfle`, `♦ Carreau`, `♥ Cœur`, `♠ Pique`.
- **Rangs** : `A, R, D, V, 10, 9, 8, 7`.
- **Points de carte** : points comptés dans les plis pendant une donne.
- **Points de partie** : points ajoutés au score de la partie à la fin d'une donne.

---

## 1. Matériel et joueurs — `R-SETUP`

| ID | Règle |
|---|---|
| R-SETUP-01 | La partie se joue à 4 joueurs, en 2 équipes de 2 (NS contre EO). |
| R-SETUP-02 | Le jeu comporte 32 cartes : 4 enseignes × 8 rangs, chaque carte est unique. |
| R-SETUP-03 | Le jeu tourne dans le sens horaire (distribution, enchères, jeu des plis). |

## 2. Paquet, coupe et distribution — `R-DEAL`

| ID | Règle |
|---|---|
| R-DEAL-01 | **On ne mélange jamais** pendant une partie. L'ordre du paquet est conservé d'une donne à l'autre. ⚠️ Q-01 (comment on ramasse les cartes) · Q-02 (paquet de départ) |
| R-DEAL-02 | Avant chaque donne, le joueur **à gauche du donneur** coupe. |
| R-DEAL-03 | La coupe laisse **au moins 6 cartes** de chaque côté : le paquet du haut fait de 6 à 26 cartes. |
| R-DEAL-04 | Après la coupe, la moitié du bas passe dessus. |
| R-DEAL-05 | Première distribution : en partant du joueur à gauche du donneur, en sens horaire, **3 cartes** à chacun, puis **2 cartes** à chacun. Chaque joueur a 5 cartes. |
| R-DEAL-06 | Après la négociation, **3 cartes de plus** à chacun, dans le même ordre. Chaque joueur a 8 cartes. ⚠️ Q-03 |
| R-DEAL-07 | Les cartes sont distribuées depuis le dessus du paquet. |
| R-DEAL-08 | Le donneur change à chaque donne : le nouveau donneur est à gauche de l'ancien. ⚠️ Q-04 (premier donneur) |

**EX-DEAL-01** — *Étant donné* un paquet ordonné `c1…c32` (c1 au-dessus) et le donneur Est,
*quand* Sud coupe 10 cartes, *alors* le paquet devient `c11…c32, c1…c10`.

**EX-DEAL-02** — *Étant donné* le paquet `p1…p32` après la coupe et le donneur Est,
*quand* on fait la première distribution, *alors* Sud reçoit `p1-p3, p13-p14`,
Ouest `p4-p6, p15-p16`, Nord `p7-p9, p17-p18` et Est `p10-p12, p19-p20`.
*Après la négociation*, Sud reçoit `p21-p23`, Ouest `p24-p26`, Nord `p27-p29` et Est `p30-p32`.

**EX-DEAL-03** — Une coupe de 5 cartes ou de 27 cartes est **refusée**.

## 3. Modes de jeu — `R-MODE`

| ID | Règle |
|---|---|
| R-MODE-01 | Il y a 6 modes : `Trèfle`, `Carreau`, `Cœur`, `Pique` (les modes **Couleur**), `Sans Atout` et `Tout Atout`. |
| R-MODE-02 | Hiérarchie, du plus bas au plus haut : **Trèfle < Carreau < Cœur < Pique < Sans Atout < Tout Atout**. |
| R-MODE-03 | En mode Couleur, une seule enseigne est atout. En Sans Atout, aucune. En Tout Atout, toutes. |

## 4. Ordre et valeur des cartes — `R-CARD`

| ID | Règle |
|---|---|
| R-CARD-01 | Ordre **atout**, du plus fort au plus faible : **V > 9 > A > 10 > R > D > 8 > 7**. |
| R-CARD-02 | Ordre **non-atout**, du plus fort au plus faible : **A > 10 > R > D > V > 9 > 8 > 7**. |
| R-CARD-03 | Valeur **atout** : V=20, 9=14, A=11, 10=10, R=4, D=3, 8=0, 7=0 (62 par enseigne). |
| R-CARD-04 | Valeur **non-atout** : A=11, 10=10, R=4, D=3, V=2, 9=0, 8=0, 7=0 (30 par enseigne). |
| R-CARD-05 | **Dernier pli** : +10 points de carte pour l'équipe qui le remporte. |
| R-CARD-06 | Total des points de carte d'une donne : Couleur **162**, Sans Atout **130**, Tout Atout **258**. |

**EX-CARD-01** — En Tout Atout, toutes les cartes de la donne valent `4 × 62 + 10 = 258`.
**EX-CARD-02** — En Cœur, `62 + 3 × 30 + 10 = 162`.
**EX-CARD-03** — En Sans Atout, `4 × 30 + 10 = 130`.

## 5. Négociation (enchères) — `R-BID`

Les actions possibles sont : **Annoncer** un mode, **Accepter**, **Contrer** et **Surcontrer**.
On ne peut jamais passer.

| ID | Règle |
|---|---|
| R-BID-01 | La négociation a lieu après la première distribution (5 cartes en main). |
| R-BID-02 | Le joueur à gauche du donneur parle en premier et **doit annoncer** un mode (il ne peut pas accepter). |
| R-BID-03 | Ensuite, on parle à tour de rôle en sens horaire. |
| R-BID-04 | On ne peut annoncer qu'un mode **strictement supérieur** à l'enchère en cours (R-MODE-02). |
| R-BID-05 | Chaque équipe ne peut faire **qu'une seule annonce Couleur** par donne. Elle peut ensuite annoncer Sans Atout ou Tout Atout. |
| R-BID-06 | Un joueur qui a **accepté** ne peut plus **annoncer** pendant la donne. ⚠️ Q-05 (peut-il encore contrer ?) |
| R-BID-07 | **Contrer** : seule l'équipe adverse de l'équipe qui a fait l'enchère en cours peut contrer. Multiplicateur ×2. |
| R-BID-08 | **Surcontrer** : seule l'équipe dont l'enchère est contrée peut surcontrer. Multiplicateur ×4. C'est possible uniquement en **Tout Atout, Carreau, Cœur et Pique**. |
| R-BID-09 | En **Sans Atout** et en **Trèfle**, quand un adversaire **accepte** l'enchère, cela compte automatiquement comme un **Contré**. On ne peut donc pas surcontrer ces modes. ⚠️ Q-06 |
| R-BID-10 | La négociation se termine après **3 Acceptations consécutives** qui suivent une enchère ou un Contré. ⚠️ Q-07 (après un Surcontré) |
| R-BID-11 | Si plusieurs enchères ont été contrées, on joue **la première enchère contrée**. ⚠️ Q-08 |
| R-BID-12 | Le mode joué et l'**équipe annonceur** sont ceux de l'enchère retenue. |

**EX-BID-01** (source) — Donneur Est. Sud « Cœur », Ouest, Nord et Est acceptent.
→ **Cœur**, annonceur **NS**, ×1.

**EX-BID-02** (source) — Donneur Est. Sud « Trèfle », Ouest « Pique », Nord, Est et Sud acceptent.
→ **Pique**, annonceur **EO**, ×1.

**EX-BID-03** — Donneur Est. Sud « Carreau », puis Nord veut annoncer « Pique ».
→ **Refusé** (R-BID-05) : NS a déjà fait son annonce Couleur.

**EX-BID-04** — Donneur Est. Sud « Cœur », Ouest veut annoncer « Carreau ».
→ **Refusé** (R-BID-04).

**EX-BID-05** — Donneur Est. Sud veut accepter.
→ **Refusé** (R-BID-02).

**EX-BID-06** — Donneur Est. Sud « Pique », Ouest contre, Nord, Est et Sud acceptent.
→ **Pique contré**, annonceur **NS**, ×2.

**EX-BID-07** — Donneur Est. Sud « Pique », Ouest contre, Nord surcontre, Est, Sud et Ouest acceptent.
→ **Pique surcontré**, annonceur **NS**, ×4. ⚠️ Q-07

**EX-BID-08** — Donneur Est. Sud « Sans Atout », Ouest contre, Nord veut surcontrer.
→ **Refusé** (R-BID-08).

## 6. Jeu des plis — `R-PLAY`

| ID | Règle |
|---|---|
| R-PLAY-01 | Une donne compte 8 plis. Chaque joueur pose une carte par pli, en sens horaire. |
| R-PLAY-02 | Le joueur **à gauche du donneur** entame le premier pli, quel que soit l'annonceur. |
| R-PLAY-03 | Le gagnant d'un pli entame le suivant. |
| R-PLAY-04 | **Fournir** : si le joueur a une carte de l'enseigne demandée, il doit en jouer une. |
| R-PLAY-05 | **Tout Atout — monter** : en fournissant, il doit battre la plus haute carte de l'enseigne déjà jouée dans le pli, s'il le peut (même si c'est la carte de son partenaire). ⚠️ Q-09 |
| R-PLAY-06 | **Couleur — couper** : s'il ne peut pas fournir et qu'il a de l'atout, il doit couper. |
| R-PLAY-07 | **Exception** à R-PLAY-06 : si son **partenaire est maître** du pli avec une carte **non-atout**, il peut défausser n'importe quelle carte. |
| R-PLAY-08 | **Couleur — surcouper** : si un atout a déjà été joué dans le pli, il doit le battre s'il le peut, **même si c'est son partenaire** qui l'a joué. ⚠️ Q-10 (s'il ne peut pas surcouper) · Q-11 (atout demandé) |
| R-PLAY-09 | **Sans Atout** : il doit seulement fournir. Sinon, il défausse n'importe quelle carte. |
| R-PLAY-10 | Si aucune obligation ne s'applique, il peut jouer n'importe quelle carte (défausse). |
| R-PLAY-11 | **Gain du pli** : s'il y a de l'atout dans le pli, le plus fort atout gagne. Sinon, la plus forte carte de l'enseigne demandée gagne. |
| R-PLAY-12 | En **Tout Atout**, la plus forte carte (ordre atout) de l'enseigne demandée gagne. Une autre enseigne ne bat jamais l'enseigne demandée. |

**EX-PLAY-01** — Cœur atout. Sud entame ♠A. Ouest n'a pas de ♠, mais a ♥7 et ♦R.
→ Ouest **doit** jouer ♥7.

**EX-PLAY-02** — Cœur atout. Sud entame ♠A, Ouest joue ♠7. Nord n'a pas de ♠, mais a ♥V et ♦7.
→ Le partenaire Sud est maître avec un non-atout : Nord **peut** jouer ♦7 (R-PLAY-07).

**EX-PLAY-03** — Cœur atout. Sud entame ♠7, Ouest coupe ♥9. Nord n'a pas de ♠, mais a ♥V et ♥8.
→ Nord **doit** jouer ♥V (surcoupe).

**EX-PLAY-04** — Cœur atout. Sud entame ♠7, Ouest joue ♠A, Nord coupe ♥10. Est n'a pas de ♠, mais a ♥9 et ♣A.
→ Est **doit** jouer ♥9 : il bat l'atout ♥10 de Nord.

**EX-PLAY-05** ⚠️ Q-10 — Cœur atout. Sud entame ♠7, Ouest coupe ♥V. Nord n'a pas de ♠, mais a ♥8 et ♦A.
→ Nord ne peut pas surcouper : **doit-il sous-couper avec ♥8, ou peut-il défausser ♦A ?**

**EX-PLAY-06** — Cœur atout. Sud entame ♠A, Ouest coupe ♥8, Nord n'a ni ♠ ni ♥ et défausse ♦7.
Est (partenaire d'Ouest) n'a pas de ♠, mais a ♥V et ♣7.
→ Est **doit** jouer ♥V : il surcoupe **son partenaire** (R-PLAY-08).

**EX-PLAY-07** — Tout Atout. Sud entame ♣A, Ouest a ♣V, ♣7 et ♦A.
→ Ouest **doit** jouer ♣V (seule carte qui monte sur ♣A).

**EX-PLAY-08** — Tout Atout. Sud entame ♣V, Ouest a ♣9 et ♣7.
→ Ouest ne peut pas monter : il **doit** fournir, ♣9 ou ♣7 au choix.

**EX-PLAY-09** — Sans Atout. Sud entame ♠10, Ouest a ♠7 et ♠A.
→ Ouest peut jouer **♠7 ou ♠A** (pas d'obligation de monter).

**EX-PLAY-10** — Pique atout. Pli : Sud ♦10, Ouest ♦A, Nord ♠7, Est ♦R.
→ **Nord** gagne (seul atout).

**EX-PLAY-11** — Sans Atout. Pli : Sud ♦9, Ouest ♠A, Nord ♦V, Est ♦7.
→ **Nord** gagne (♦V > ♦9 en non-atout ; ♠A ne compte pas).

**EX-PLAY-12** — Tout Atout. Pli : Sud ♥A, Ouest ♥9, Nord ♣V, Est ♥R.
→ **Ouest** gagne (♥9 > ♥A en ordre atout ; ♣V est une autre enseigne).

## 7. Décompte d'une donne — `R-SCORE`

| ID | Règle |
|---|---|
| R-SCORE-01 | À la fin des 8 plis, chaque équipe compte ses points de carte, y compris le dernier pli (+10). |
| R-SCORE-02 | **Couleur** : l'annonceur gagne s'il a **au moins 82** points. Le gagnant marque **16**, le perdant 0. |
| R-SCORE-03 | **Couleur — égalité 81-81** : personne ne marque. |
| R-SCORE-04 | **Sans Atout** : l'annonceur gagne s'il a plus de la moitié des points. Le gagnant marque **52**, le perdant 0. ⚠️ Q-12 (seuil 65 contre égalité 65-65) |
| R-SCORE-05 | **Sans Atout — égalité 65-65** : personne ne marque. |
| R-SCORE-06 | **Tout Atout** : si l'annonceur a **moins de 129** points, il marque 0 et les adversaires marquent **26**. |
| R-SCORE-07 | **Tout Atout — partage** : sinon, chaque équipe marque ses points de carte ÷ 10, **arrondis au supérieur**. ⚠️ Q-13 (le total ne fait pas toujours 26) |
| R-SCORE-08 | **Tout Atout — égalité** : 129-129, ou un partage arrondi à 13-13, donne 0-0. |
| R-SCORE-09 | **Multiplicateur** : les points de partie sont ×1 (normal), ×2 (contré) ou ×4 (surcontré). ⚠️ Q-14 (partage Tout Atout) |
| R-SCORE-10 | Points de partie ajoutés au score de chaque équipe. |

**EX-SCORE-01** — Cœur, annonceur NS : NS 90, EO 72 → **NS +16**, EO +0.
**EX-SCORE-02** — Cœur, annonceur NS : NS 80, EO 82 → NS +0, **EO +16**.
**EX-SCORE-03** — Cœur, annonceur NS : 81-81 → **0-0**.
**EX-SCORE-04** — Cœur contré, annonceur NS : NS 100, EO 62 → **NS +32**.
**EX-SCORE-05** — Pique surcontré, annonceur NS : NS 70, EO 92 → **EO +64**.
**EX-SCORE-06** — Sans Atout, annonceur EO : EO 80, NS 50 → **EO +52**.
**EX-SCORE-07** — Tout Atout, annonceur NS : NS 150, EO 108 → **NS +15, EO +11**.
**EX-SCORE-08** — Tout Atout, annonceur NS : NS 120, EO 138 → NS +0, **EO +26**.
**EX-SCORE-09** — Tout Atout, annonceur NS : 129-129 → **0-0**.
**EX-SCORE-10** — Tout Atout, annonceur NS : NS 130, EO 128 → arrondi 13-13 → **0-0**.

## 8. Capot — `R-CAPOT`

| ID | Règle |
|---|---|
| R-CAPOT-01 | Une équipe fait **capot** quand elle remporte les 8 plis. |
| R-CAPOT-02 | Capot en **Tout Atout** : **35** points de partie (au lieu du décompte normal). ⚠️ Q-15 (capot par la défense) |
| R-CAPOT-03 | Capot en **Sans Atout** : **90** points de partie. |
| R-CAPOT-04 | Capot en **Couleur** : **victoire immédiate de la partie**. |
| R-CAPOT-05 | Le capot est multiplié par le Contré / Surcontré (35 → 70 / 140 ; 90 → 180 / 360). Un capot Couleur reste une victoire immédiate. |

## 9. Fin de partie — `R-GAME`

| ID | Règle |
|---|---|
| R-GAME-01 | La première équipe qui atteint **150** points de partie gagne. ⚠️ Q-16 (« atteindre » ≥ 150 ou « dépasser » > 150) |
| R-GAME-02 | Si les deux équipes passent l'objectif **sur la même donne**, l'objectif monte de 100 (250, puis 350, etc.) et la partie continue. |
| R-GAME-03 | Un capot Couleur termine la partie immédiatement (R-CAPOT-04). |

**EX-GAME-01** — Score 140-100. NS marque 16 → 156-100 → **NS gagne**.
**EX-GAME-02** — Score 140-145. Tout Atout, NS +15, EO +11 → 155-156 → les deux passent 150 → **objectif 250**, la partie continue.

## 10. Hors périmètre (absent de la source)

Ces règles de la belote classique **n'existent pas** dans cette spec : belote-rebelote, annonces
(tierce, cinquante, cent, carré), « dedans » / litige mis en réserve. ⚠️ Q-17
