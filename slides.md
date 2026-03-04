---
colorSchema: dark
transition: fade-out
mdc: true
layout: center
glowSeed: 4
timer: countdown
duration: 30min
hideInToc: true
title: Osmose - Acculturation Data
---

![](/Logo_Osmose_Horizontal_VF.png){.w-30.mt--10.mb-5}

---
layout: intro
class: pl-25
glowSeed: 14
---

<div text-5xl font-jp>Guillaume Gandon</div>

<div class="[&>*]:important-leading-10 opacity-80 mt5">
Lead Data Engineer<br>
</div>

<img src="/public/photo_profil_osmose.jpg" rounded-full absolute top-38 right-15 w-40 />

---
layout: center
glow: top
class: text-center
hideInToc: true
---

# Acculturation Data

<div abs-bl m8 flex="~ col gap-2 items-end" text-left op75>
  <img src="/Logo_Osmose_Horizontal_VF.png" h-10 alt="Vue Fes Japan">
</div>

<div abs-br m8 flex="~ col gap-2 items-end" text-left op75>
  <div text-sm opacity-75>3 mars 2026</div>
</div>

---
transition: fade-out
hideInToc: true
---

# Sommaire

<Toc text-sm minDepth="1" maxDepth="2" />

---
transition: slide-up
---

# 🎯 Objectifs de la présentation

**Pourquoi cette présentation ?**

* Démystifier la Data (ce n’est pas “juste des dashboards” ni “de la magie IA”)
* Donner un **langage commun** entre tech & commerce
* Aider les commerciaux à :

  * qualifier un besoin client
  * identifier **le bon pilier**
  * placer **le bon profil**

👉 Message clé :

> *La Data est une chaîne de valeur, pas un outil isolé.*

---
transition: slide-up
---

# 🧠 Vue d’ensemble : le parcours de la donnée

<div class="flowchart">
  <div v-click="1" class="node">Sources</div>
  <div v-click="2" class="arrow"></div>
  <div v-click="2" class="node">Ingestion</div>
  <div v-click="3" class="arrow"></div>
  <div v-click="3" class="node">Stockage</div>
  <div v-click="4" class="arrow"></div>
  <div v-click="4" class="node">Transformation / Qualité</div>
  <div v-click="5" class="arrow"></div>
  <div v-click="5" class="node">Analyse / ML</div>
  <div v-click="6" class="arrow"></div>
  <div v-click="6" class="node">Restitution / Exposition</div>
</div>

<style>
  body {
    font-family: Arial, sans-serif;
    background: #f5f7fa;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
  }

  .flowchart {
    display: flex;
    align-items: center;
    gap: 10px;
  }

  .node {
    background: rgba(16,86,102);
    padding: 20px 0px;
    border-radius: 12px;
    box-shadow: 0 4px 12px rgba(0,0,0,0.08);
    border: 2px solid #4a90e2;
    font-weight: 600;
    color: rgba(255,255,164);
    text-align: center;
    min-width: 120px;
  }

  .arrow {
    width: 0px;
    height: 2px;
    background: repeating-linear-gradient(
      to right,
      #4a90e2 0,
      #4a90e2 0px,
      transparent 0px,
      transparent 8px
    );
    position: relative;
    animation: dash 25s linear infinite;
  }

  .arrow::after {
    content: "";
    position: absolute;
    right: -6px;
    top: -5px;
    border-top: 6px solid transparent;
    border-bottom: 6px solid transparent;
    border-left: 8px solid #4a90e2;
  }

  @keyframes dash {
    from {
      background-position: 0 0;
    }
    to {
      background-position: 200px 0;
    }
  }
</style>

💡 Important :
> <span v-mark="{ at: 7, color: 'orange', type: 'underline' }">*Si une étape est mal faite, tout ce qui suit est impacté.*</span>

---
hide: true
---

# 🧠 Vue d’ensemble : le parcours de la donnée

```mermaid {scale: 0.8}
flowchart LR
    id1("Sources")
    id2("Ingestion")
    id3("Stockage")
    id4("Transformation  / Qualité")
    id5("Analyse / ML")
    id6("Restitution / Exposition")
    id1 e1@--> id2
    id2 e2@--> id3
    id3 e3@--> id4
    id4 e4@--> id5
    id5 e5@--> id6
    classDef animate stroke-dasharray: 9,5,stroke-dashoffset: 900,animation: dash 25s linear infinite;
    class e1 animate
    class e2 animate
    class e3 animate
    class e4 animate
    class e5 animate
```

💡 Important :
> <span v-mark.underline.orange>*Si une étape est mal faite, tout ce qui suit est impacté.*</span>

---
transition: slide-up
layout: two-cols-header
level: 2
---

# Étape 1 – Ingestion des données

::left::

🗂️ **Sources possibles**

* ERP (SAP, Sage…)
* CRM (Salesforce, HubSpot)
* APIs
* Fichiers (CSV, Excel, Json, XML)
* IoT / logs

🔑 **Mots-clés**

* Batch vs Temps réel
* ETL / ELT
* Connecteurs

::right::

🛠 **Outils**

* Airflow • Talend • Kafka • APIs REST

💼 **Cas concret**

> *Ingestion quotidienne des transactions pour détecter les fraudes et avoir une vue client 360°.*

<!--
Message commercial : “Un client qui a beaucoup d’Excel = opportunité.”
-->

---
transition: slide-up
layout: two-cols-header
level: 2
---

# Étape 2 – Stockage & Plateforme Data

::left::

💡 **Concepts**

* Data Lake
* Data Warehouse
* Lakehouse

🛠 **Outils**

* BigQuery, Snowflake, Redshift
* Azure Data Lake, S3
* Hadoop / Cloudera
* Databricks

::right::

💼 **Cas concret**

> *Une banque centralise et sécurise ses données clients, transactions et risques pour répondre aux besoins métier et réglementaires.*

<!--
Message commercial : modernisation d’architecture.
-->

---
transition: slide-up
layout: two-cols-header
level: 2
---

# Étape 3 – Transformation & Qualité

::left::

🎯 **Objectifs**

* nettoyer
* standardiser
* historiser
* fiabiliser

🔑 **Mots-clés**

* Modélisation
* Qualité de données
* Traçabilité
* Tests

::right::

🛠 **Outils**

* dbt
* Spark

💼 **Cas concret**

> *Chiffre d’affaires différent entre Finance et Commerce → problème de règles métiers.*

<!--
Message : dette technique = besoin de structuration. Industrialisation
-->

---
transition: slide-up
layout: two-cols-header
level: 2
---

# Étape 4 – Analyse & Machine Learning

::left::

🎯 **Objectifs**

* Prédiction de pannes
* Scoring client
* Détection de fraude
* Prévision des ventes
* Recommandation produit

🔑 **Mots-clés**

* Features
* Entraînement
* Modèle
* Prédiction

::right::

🛠 **Outils**

* Python, Pandas, Scikit-learn
* TensorFlow / PyTorch
* MLflow


💼 **Cas concret**

> *Une banque prédit le risque de défaut d’un client pour sécuriser et accélérer l’octroi de crédits.*

---
layout: two-cols-header
level: 2
---

# Étape 5 - Restitution & Exposition

::left::

🎯 **Objectif**

Rendre la donnée accessible et utile aux métiers ou aux applications.

🔑 **Mots-clés**

Dashboard • Reporting • API • Export • Partage sécurisé

::right::


🛠 **Outils**

Power BI • Tableau • APIs • Cloud

💼 **Cas concret**

> *Une banque met en place un tableau de bord pour suivre les risques et fournit les données aux applications mobiles via API.*

<style>
.two-cols-header {
  column-gap: 20px; /* Adjust the gap size as needed */
}
</style>

---

# Les rôles dans l’écosystème Data

---
transition: slide-up
level: 2
---

# 🔧 Data Engineer

* Construit les pipelines
* Gère le stockage
* Travaille sur la performance

👉 Profil technique, infra, cloud.

---
transition: slide-up
level: 2
---

# 📊 Data Analyst

* Produit les dashboards
* Analyse la performance
* Travaille avec les métiers

👉 Souvent rattaché au métier.

---
transition: slide-up
level: 2
---

# 🤖 Data Scientist

* Modèles prédictifs
* Machine learning
* Cas d’usage avancés

👉 Projet à forte valeur mais dépendant de la maturité data.

---
transition: slide-up
level: 2
---

# 🏛️ Data Steward

* Garant de la qualité des données
* Définitions des KPI
* Documentation

👉 Sujet clé dans les grandes entreprises.

---
transition: slide-up
level: 2
---

# 👔 Data Owner

* Responsable métier d’un domaine de données
* Porte la vision et la valeur

👉 Souvent décisionnaire ou sponsor.

---
level: 2
---

# 🧭 Chief Data Officer

* Stratégie data globale
* Gouvernance
* Budget

---
class: text-2xl
glow: right
transition: slide-up
---

# 🧩 Les <span font-hand text-green scale-110 ml1 inline-block>4 piliers</span> Osmose

<div grid="~ cols-[max-content_min-content_auto] items-center gap-6" py1 px3>
  <div flex="~ gap-2 items-center" text-blue relative v-click>
    <div i-ph-database text-2xl ml-12/>
    <span>Data Engineering & Plateformes</span>
  </div>
  <div i-ph-arrow-right-duotone op50 v-click />
  <div v-after>Ingestion, Transformation, Stockage</div>

  <div flex="~ gap-2 items-center" text-lime relative v-click>
    <div i-ph-book-bookmark-duotone text-2xl ml-12/>
    <span>Data Analytics & Visualisation</span>
  </div>
  <div i-ph-arrow-right-duotone op50 v-click />
  <div v-after>Analyse, Dashboard</div>

  <div flex="~ gap-2 items-center" text-amber relative v-click>
    <div i-ph-currency-circle-dollar-duotone text-2xl ml-12/>
    <span>Data Science / ML / IA</span>
  </div>
  <div i-ph-arrow-right-duotone op50 v-click />
  <div v-after>Enrichissement, Prédiction</div>

  <div flex="~ gap-2 items-center" text-orange relative v-click>
    <div i-ph-plugs-duotone text-2xl ml-12 />
    <span>Accompagnement & Pilotage</span>
  </div>
  <div i-ph-arrow-right-duotone op50 v-click />
  <div v-after>Transversal, du cadrage à la prod</div>
</div>

---
preload: false
---

<ViteEco />

---
layout: intro
class: text-center pb-5
glowX: 50
glowY: 120
---

<h1 font-jp important-text-3em>Merci</h1>
