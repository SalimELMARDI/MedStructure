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

### D. Système d'Information (`:Donnees`)

* **Dossier Médical :** Agrégateur d'informations du patient.
* **Acte Médical :** Action réalisée (chirurgie, analyse, consultation).
* **Diagnostic :** Conclusion médicale (pathologie).

---

## 4. Relations Sémantiques (Propriétés)

Le tableau ci-dessous détaille les interactions définies comme *Object Properties* dans l'ontologie.

| Concept Source (Domain) | Relation (Verbe) | Concept Cible (Range) | Description |
| --- | --- | --- | --- |
| **Médecin** | `diagnostique_et_traite` | **Patient** | Relation de soin principale. |
| **Infirmier** | `soigne_et_surveille` | **Patient** | Soins infirmiers quotidiens. |
| **Aide-Soignant** | `assiste_hygiene` | **Patient** | Assistance de vie. |
| **Tech. Labo** | `realise` | **Acte Médical** | Exécution d'examens techniques. |
| **Médecin** | `prescrit` | **Acte Médical** | Ordre de réalisation d'un soin. |
| **Acte Médical** | `concerne` | **Patient** | Lien entre l'acte et le bénéficiaire. |
| **Acte Médical** | `necessite` | **Équipement Médical** |Matériel requis pour l'acte.. |
| **Médecin** | `pose` | **Diagnostic** | Identification de la pathologie. |
| **Diagnostic** | `est_enregistre_dans` | **Dossier Médical** | Traçabilité de la pathologie. |
| **Patient** | `possede` | **Dossier Médical** | Propriété du dossier. |
| **Patient** | `est_admis_dans` | **Service** | Rattachement administratif. |
| **Patient** | `occupe` | **Chambre** | Localisation physique. |
| **Chambre** | `est_situe_dans` | **Service** | Hiérarchie spatiale. |
| **Chambre** | `est_equipe_de` | **Équipement Médical** | Équipements disponibles dans la chambre. |
| **Service Technique** | `maintient` | **Hôpital** | Gestion globale du bâtiment. |
