# Jumeau numérique de la ligne ALIX

## Contexte
Projet Bureau d'Étude (PRBE 2026) réalisé à l'ISAE-SUPMECA en partenariat avec Dassault Systèmes, en binôme, dans la continuité des travaux de groupes précédents sur la plateforme ALIX (ligne de production automatisée dédiée à l'assemblage et au conditionnement de barquettes).

## Objectif
Établir une chaîne de communication fiable et temps réel entre l'automate physique de la ligne ALIX (Siemens S7-1200) et son jumeau numérique sur 3DEXPERIENCE, afin que les signaux des capteurs réels pilotent effectivement le comportement cinématique du modèle virtuel.

## Ce que j'ai fait
- **Architecture de communication temps réel** : Automate S7-1200 → Node-RED → OPC UA (serveur Prosys) → 3DEXPERIENCE, avec acquisition de 8 variables de capteurs à 1 Hz
- **Restructuration du modèle 3D** dans l'atelier Robot Virtual Commissioning (RVC) : conversion de l'assemblage en cellule de fabrication pour permettre la création de tâches robot, correction des défauts hérités des groupes précédents
- **Mise en place du mapping de signaux** RVC (contrôleurs logiques pour capteurs de présence et de position)
- **Exploration de 3 pistes de pilotage cinématique** du modèle virtuel à partir des signaux réels :
  1. Communication RVC ↔ Model Behavior (Dymola) — bloquée par une incompatibilité architecturale entre Mechanical Systems Design et RVC
  2. Centralisation complète dans RVC — nécessite une reconstruction du modèle, non finalisée dans le temps imparti
  3. Connexion Node-RED → Dymola via fichier de consigne CSV — validée avec succès sur un cas isolé (moteur du tapis convoyeur), avec relecture d'un cycle enregistré (CombiTimeTable)
- **Export CSV** de l'historique des acquisitions pour exploitation hors ligne

## Résultat
Chaîne d'acquisition automate → 3DEXPERIENCE validée de bout en bout et réutilisable. Le pilotage cinématique temps réel complet reste un verrou identifié et documenté (limites architecturales précises par piste), posant une base claire pour les travaux futurs.

## Outils
3DEXPERIENCE (DELMIA — Robot Virtual Commissioning, Equipment Design, Plant Layout Design, Behaviour Modeling), Node-RED, OPC UA (Prosys), Dymola/Modelica, automate Siemens S7-1200


