# Projet MedStructure : Ontologie Sémantique pour l'Interopérabilité Hospitalière

## 1. Présentation du Projet

### 1.1. Définition
**MedStructure** est un projet d'ingénierie des connaissances visant à construire une ontologie formelle pour le domaine hospitalier. Il modélise les interactions complexes entre les patients, une hiérarchie détaillée du personnel médical, les infrastructures physiques et les actes de soins.

### 1.2. Objectifs
* **Interopérabilité :** Unifier le vocabulaire entre les différents services (ex: Labo, Pharmacie, Administration).
* **Traçabilité :** Lier sémantiquement un patient à son parcours de soin complet.
* **Structuration :** Organiser les données pour faciliter l'aide à la décision.

---

## 2. Architecture Sémantique (Diagramme)

Ce diagramme illustre la structure globale de l'ontologie, mettant en évidence la hiérarchie du personnel et les flux de données.

![Diagramme de l'ontologie MedStructure](<Untitled diagram-2025-12-25-144446.svg>)

---

## 3. Définition des Concepts (Classes)

L'ontologie est structurée autour de quatre piliers principaux :

### A. Hiérarchie du Personnel (`:Personnel`)

Modélisation des acteurs hospitaliers selon leurs rôles fonctionnels :

* **Personnel Médical :** Médecins, chirurgiens, pharmaciens et internes responsables du diagnostic et de la prescription.
* **Personnel Soignant (Paramédical) :** Infirmiers (IDE), aides-soignants, ainsi que les auxiliaires médicaux (kinésithérapeutes, techniciens de laboratoire, manipulateurs radio).
* **Médico-Technique & Social :** Psychologues et assistants sociaux pour l'accompagnement global.
* **Administratif & Soutien :** Cadres de santé, agents administratifs, services techniques et agents de nettoyage.

### B. Le Patient (`:Patient`)

* Entité centrale du système, bénéficiaire des soins et propriétaire des données médicales.

### C. Infrastructure & Lieux (`:Infrastructure`)

* **Hôpital :** Entité racine.
* **Service de Soins :** Unité fonctionnelle (ex: Cardiologie).
* **Chambre Patient :** Lieu d'hébergement.
* **Laboratoire / Pharmacie :** Lieux techniques.
* 

### D. Système d'Information (`:Donnees`)

* **Dossier Médical :** Agrégateur d'informations du patient.
* **Acte Médical :** Action réalisée (chirurgie, analyse, consultation).
* **Diagnostic :** Conclusion médicale (pathologie).
### E. Ressources Médicales (:Ressources)

Ce concept regroupe les éléments matériels et thérapeutiques nécessaires à la réalisation des soins et actes médicaux.

* **Équipement Médical :** Dispositifs et matériels utilisés pour les soins et examens.

* **Médicament :** Substance thérapeutique utilisée dans le traitement ou la prévention des pathologies.

### F. Processus Administratifs & Parcours Patient (:Processus)

Ce pilier couvre les événements organisationnels et administratifs structurant le parcours du patient au sein de l’établissement.

 * **Admission Hospitalière**

* **Transfert de Service**

* **Sortie Hospitalière**

* **Rendez-vous Médical**

### G. Coordination & Organisation des Soins (:Organisation)

Ce concept regroupe les éléments liés à la planification, à la coordination interprofessionnelle et à la continuité des soins.

* **Collaboration Inter-Services**

* **Supervision Médicale**

* **Planification des Actes Médicaux** 

---
| Concept Source(Domain) | Relation (Verbe) | Concept Cible (Range) | Description |
|------------------------|------------------|-----------------------|-------------|
| Médecin    | **diagnostique_et_traite** | Patient | Relation de soin principale |
| Infirmier | **soigne_et_surveille** | Patient | Soins infirmiers quotidiens |
| Aide-Soignant | **assiste_hygiene** | Patient | Assistance de vie |
| Technicien de Laboratoire | **realise** | Acte Médical | Exécution d'examens techniques |
| Médecin | **prescrit** | Acte Médical | Ordre de réalisation d'un soin |
| Acte Médical | **concerne** | Patient | Lien entre l'acte et le bénéficiaire |
| Acte Médical | **necessite** | Équipement Médical | Matériel requis pour l'acte |
| Médecin | pose | **Diagnostic** | Identification de la pathologie |
| Diagnostic | est_enregistre_dans | Dossier Médical | Traçabilité de la pathologie |
| Patient | possede | Dossier Médical | Propriété du dossier |
| Patient | est_admis_dans | Service | Rattachement administratif |
| Patient | occupe | Chambre | Localisation physique |
| Chambre | est_situe_dans | Service | Hiérarchie spatiale |
| Chambre | est_equipe_de | Équipement Médical | Équipements disponibles dans la chambre |
| Service Technique | maintient | Hôpital | Gestion globale du bâtiment |
| Infirmier | utilise | Équipement Médical | Usage direct d'un équipement |
| Technicien Biomédical | maintient | Équipement Médical | Maintenance et réparation |
| Pharmacien | delivre_medicament_a | Patient | Distribution des traitements prescrits |
| Pharmacien | valide_prescription_de | Médecin | Contrôle pharmaceutique |
| Pharmacien | stocke | Médicament | Gestion des stocks médicamenteux |
| Psychologue | accompagne | Patient | Soutien psychologique |
| Assistant Social | aide_administrativement | Patient | Accompagnement social et démarches |
| Cadre de Santé | supervise | Infirmier | Hiérarchie et coordination des soins |
| Cadre de Santé | gere | Service | Responsabilité organisationnelle |
| Médecin | consulte | Dossier Médical | Accès aux antécédents du patient |
| Infirmier | met_a_jour | Dossier Médical | Saisie des observations infirmières |
| Agent Administratif | enregistre_admission_de | Patient | Gestion des entrées hospitalières |
| Manipulateur Radio | effectue_imagerie_pour | Patient | Réalisation d'examens radiologiques |
| Kinésithérapeute | reeduque | Patient | Rééducation fonctionnelle |
| Chirurgien | opere | Patient | Intervention chirurgicale |
| Patient | est_transfere_vers | Service | Changement de service médical |
| Service | collabore_avec | Service | Coordination inter-services |
| Laboratoire | transmet_resultats_a | Médecin | Communication des analyses |
| Médecin | demande_consultation_a | Médecin | Avis spécialisé inter-médecins |
| Interne | est_supervise_par | Médecin | Formation et encadrement médical |
| Personnel | travaille_dans | Service | Affectation organisationnelle |
| Acte Médical | est_planifie_dans | Bloc Opératoire | Programmation des interventions |
| Agent de Nettoyage | entretient | Chambre | Hygiène et désinfection |
| Hôpital | contient | Service | Structure organisationnelle globale |
| Dossier Médical | contient | Résultat d'Examen | Centralisation des données cliniques |
| Médecin | redige | Compte Rendu | Documentation médicale |
| Patient | beneficie_de | Protocole de Soins | Plan thérapeutique personnalisé |

