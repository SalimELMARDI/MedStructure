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

### A. Acteurs du Système Hospitalier (:Acteur)

Ce concept regroupe l’ensemble des entités humaines impliquées dans la prise en charge du patient et le fonctionnement de l’hôpital.

* **Personnel Médical :** Médecins, chirurgiens, pharmaciens, internes.

* **Personnel Soignant (Paramédical) :** Infirmiers, aides-soignants, kinésithérapeutes, manipulateurs radio, techniciens de laboratoire.

* **Médico-Technique & Social :** Psychologues, assistants sociaux, techniciens biomédicaux.

* **Administratif & Soutien :** Cadres de santé, agents administratifs, agents de nettoyage, services techniques.

* **Patient :** Personne bénéficiant des soins et au centre du système hospitalier.

### B. Structures & Environnements (:Structure)

Ce pilier regroupe les entités physiques et organisationnelles dans lesquelles se déroulent les activités hospitalières.

* **Hôpital**

* **Service de Soins**

* **Chambre Patient**

* **Laboratoire**

* **Pharmacie**

* **Bloc Opératoire**

### C. Activités & Soins Médicaux (:ActiviteMedicale)

Ce concept couvre l’ensemble des actions cliniques, thérapeutiques et techniques réalisées dans le cadre de la prise en charge du patient.

* **Acte Médical**

* **Consultation Médicale**

* **Intervention Chirurgicale**

* **Examen Médical**

* **Rééducation Fonctionnelle**

### D. Données & Informations Médicales (:Information)

Ce pilier regroupe toutes les entités informationnelles produites, utilisées et conservées durant le parcours de soins.

* **Dossier Médical**

* **Diagnostic**

* **Résultat d’Examen**

* **Compte Rendu Médical**

* **Protocole de Soins**
 
### E. Ressources & Organisation (:Ressource)

Ce concept rassemble les moyens matériels, thérapeutiques et organisationnels nécessaires au fonctionnement hospitalier.

**Équipement Médical** 

* **Médicament**

* **Planification des Actes**

 * **Processus Administratifs (admission, transfert, sortie)**

* **Coordination des Soins**

---
| Concept Source (Domain) | Relation (Verbe) | Concept Cible (Range) | Description |
|------------------------|------------------|-----------------------|-------------|
| Médecin | diagnostique_et_traite | Patient | Relation de soin principale |
| Infirmier | soigne_et_surveille | Patient | Soins infirmiers quotidiens |
| Aide-Soignant | assiste_hygiene | Patient | Assistance de vie |
| Technicien de Laboratoire | realise | Acte Médical | Exécution d'examens techniques |
| Médecin | prescrit | Acte Médical | Ordre de réalisation d'un soin |
| Médecin | suit | Patient | Suivi médical du patient |
| Infirmier | assiste | Médecin | Assistance lors des actes médicaux |
| Aide-Soignant | accompagne | Patient | Accompagnement du patient au quotidien |
| Personnel Médico-Technique | utilise | Équipement Médical | Utilisation des équipements techniques |
| Personnel Médico-Technique | produit | Résultat d’Examen | Production des résultats d’examens |
| Personnel Administratif | admet | Patient | Admission administrative du patient |
| Personnel Administratif | gère | Dossier Médical | Gestion administrative du dossier |
| Personnel Administratif | planifie | Consultation Médicale | Planification des rendez-vous |
| Patient | est_pris_en_charge_par | Personnel Soignant | Prise en charge soignante |
| Acte Médical | concerne | Patient | Lien entre l'acte et le bénéficiaire |
| Acte Médical | necessite | Équipement Médical | Matériel requis pour l'acte |
| Acte Médical | est_realise_par | Personnel | Exécutant de l’acte médical |
| Acte Médical | est_enregistre_dans | Dossier Médical | Traçabilité de l’acte |
| Acte Médical | se_deroule_dans | Service | Lieu de réalisation |
| Acte Médical | produit | Résultat d'Examen | Résultat clinique généré |
| Médecin | pose | Diagnostic | Identification de la pathologie |
| Diagnostic | est_enregistre_dans | Dossier Médical | Traçabilité de la pathologie |
| Patient | possede | Dossier Médical | Propriété du dossier |
| Patient | est_admis_dans | Service | Rattachement administratif |
| Patient | occupe | Chambre | Localisation physique |
| Chambre | est_situe_dans | Service | Hiérarchie spatiale |
| Chambre | est_equipe_de | Équipement Médical | Équipements disponibles |
| Service Technique | maintient | Hôpital | Gestion globale du bâtiment |
| Infirmier | utilise | Équipement Médical | Usage direct d'un équipement |
| Technicien Biomédical | maintient | Équipement Médical | Maintenance et réparation |
| Pharmacien | delivre_medicament_a | Patient | Distribution des traitements |
| Pharmacien | valide_prescription_de | Médecin | Contrôle pharmaceutique |
| Pharmacien | stocke | Médicament | Gestion des stocks |
| Psychologue | accompagne | Patient | Soutien psychologique |
| Assistant Social | aide_administrativement | Patient | Accompagnement social |
| Cadre de Santé | supervise | Infirmier | Coordination des soins |
| Cadre de Santé | gere | Service | Responsabilité organisationnelle |
| Médecin | consulte | Dossier Médical | Accès aux antécédents |
| Infirmier | met_a_jour | Dossier Médical | Observations infirmières |
| Agent Administratif | enregistre_admission_de | Patient | Gestion des admissions |
| Manipulateur Radio | effectue_imagerie_pour | Patient | Examens radiologiques |
| Kinésithérapeute | reeduque | Patient | Rééducation fonctionnelle |
| Chirurgien | opere | Patient | Intervention chirurgicale |
| Patient | est_transfere_vers | Service | Changement de service |
| Service | collabore_avec | Service | Coordination inter-services |
| Laboratoire | transmet_resultats_a | Médecin | Communication des analyses |
| Médecin | demande_consultation_a | Médecin | Avis spécialisé |
| Interne | est_supervise_par | Médecin | Encadrement médical |
| Personnel | travaille_dans | Service | Affectation organisationnelle |
| Acte Médical | est_planifie_dans | Bloc Opératoire | Programmation |
| Agent de Nettoyage | entretient | Chambre | Hygiène et désinfection |
| Hôpital | contient | Service | Structure globale |
| Dossier Médical | contient | Résultat d'Examen | Centralisation des données |
| Médecin | redige | Compte Rendu | Documentation médicale |
| Patient | beneficie_de | Protocole de Soins | Plan thérapeutique |
| Consultation Médicale | est_un | Acte Médical | Acte clinique non invasif |
| Consultation Médicale | concerne | Patient | Patient consulté |
| Consultation Médicale | est_realisee_par | Médecin | Réalisation médicale |
| Consultation Médicale | aboutit_a | Diagnostic | Résultat clinique |
| Intervention Chirurgicale | est_un | Acte Médical | Acte invasif |
| Intervention Chirurgicale | concerne | Patient | Patient opéré |
| Intervention Chirurgicale | est_realisee_par | Chirurgien | Responsable opératoire |
| Intervention Chirurgicale | necessite | Bloc Opératoire | Lieu spécialisé |
| Intervention Chirurgicale | produit | Compte Rendu | Trace opératoire |
| Examen Médical | est_un | Acte Médical | Acte exploratoire |
| Examen Médical | est_prescrit_par | Médecin | Décision médicale |
| Examen Médical | est_realise_par | Personnel Médical | Réalisation technique |
| Examen Médical | utilise | Équipement Médical | Matériel diagnostique |
| Examen Médical | produit | Résultat d'Examen | Données cliniques |
| Examen Médical | est_archive_dans | Dossier Médical | Conservation des résultats |
| Processus Administratif | gere | Admission | Prise en charge initiale |
| Processus Administratif | gere | Transfert | Changement de service |
| Processus Administratif | gere | Sortie | Fin d’hospitalisation |
| Planification des Actes | coordonne | Acte Médical | Ordonnancement |
| Coordination des Soins | implique | Personnel Médical | Collaboration médicale |
| Coordination des Soins | implique | Personnel Soignant | Continuité des soins |
| Coordination des Soins | relie | Service | Coopération inter-services |
|Équipement Médical |	est_utilise_pour |	Acte Médical |	Support matériel des soins |
|Médicament |	est_stocke_dans	| Pharmacie | Lieu de conservation des médicaments |
|Pharmacien |	gere_stock_de	| Médicament | Gestion quantitative et qualitative |
|Technicien Biomédical |	planifie_maintenance_de	| Équipement | Médical	Maintenance préventive |
