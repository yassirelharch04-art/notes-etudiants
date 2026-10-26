# Exigences de sécurité de l'application des notes

| # | Exigence : « Le système doit… » | Vérification | Étape du SDLC | Test |
|---|---|---|---|---|
| 1 | empêcher les injections SQL lors de la recherche d'un étudiant. | Vérifier que la recherche utilise des requêtes SQL paramétrées. | Développement et test | S1 |
| 2 | refuser la modification d'une note si l'utilisateur n'est pas identifié. | Envoyer une demande sans jeton et vérifier la réponse HTTP 401. | Test | S2 |
| 3 | interdire aux étudiants de modifier les notes. | Envoyer une demande avec un jeton étudiant et vérifier la réponse HTTP 403. | Test | S3 |
| 4 | empêcher un enseignant de modifier les notes d'un autre module. | Utiliser le jeton d'un enseignant d'un autre module et vérifier la réponse HTTP 403. | Test | S4 |
| 5 | accepter uniquement une note numérique comprise entre 0 et 20. | Envoyer une note invalide et vérifier la réponse HTTP 400. | Test | S5 |
| 6 | autoriser l'enseignant du module à modifier la note de son étudiant. | Modifier une note avec le bon jeton et vérifier la réponse HTTP 200 et la nouvelle valeur. | Test | S6 |
| 7 | ne pas exposer les détails techniques internes dans les messages d'erreur. | Simuler une erreur de base de données et vérifier que la réponse ne révèle pas de détails techniques. | Test | S7 |