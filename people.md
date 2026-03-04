---
layout: single
title: "People"
permalink: /people/
---

<style>
.people-grid{
  display:flex;
  flex-wrap:wrap;
  gap:24px;
}

.people-card{
  width:200px;
  text-align:center;
  text-decoration:none;
  color:inherit;
}

.people-card img{
  width:200px;
  height:240px;
  object-fit:cover;
  border-radius:12px;
}

.people-name{
  margin-top:8px;
  font-weight:600;
}

.people-title{
  font-size:0.9em;
  opacity:0.7;
}
</style>

{% assign groups = "PI,PhD,Master,Undergraduate,RA,Alumni" | split: "," %}

{% for g in groups %}
## {{ g }}

<div class="people-grid">

{% assign members = site.people | where: "group", g %}

{% for p in members %}
<a class="people-card" href="{{ p.url | relative_url }}">
  <img src="{{ p.image }}" alt="{{ p.name }}">
  <div class="people-name">{{ p.name }}</div>
  <div class="people-title">{{ p.title }}</div>
</a>
{% endfor %}

</div>

{% endfor %}




<!--
---
layout: single
title: "People"
permalink: /people/
---
## Principal Investigator

<div style="display:flex; gap:24px; align-items:flex-start; flex-wrap:wrap;">
  <div style="flex:0 0 220px;">
    <img 
      src="https://raw.githubusercontent.com/tmucrelab/CRELab-website/master/assets/assets/images/Lee_ChengFan.jpg"
      alt="Dr. Cheng-Fan Lee"
      style="width:220px; border-radius:12px; object-fit:cover;" >
  </div>
</div>

  <div style="flex:1; min-width:260px;">
    <strong>Dr. Cheng-Fan “Bryan” Lee (李丞釩)</strong><br>
    Assistant Professor<br>
    Department of Biochemistry and Molecular Biology<br>
    Taipei Medical University<br><br>

    Dr. Lee’s research focuses on <strong>cancer resistance evolution</strong>, investigating how cancers adapt to therapeutic pressure through transcriptional and metabolic remodeling, with an emphasis on prostate cancer, organoid models, and lipid metabolism.
  </div>
</div>

## 🎓 Education
- **Ph.D.**, Graduate Institute of Biochemistry and Molecular Biology  
  College of Medicine, National Taiwan University, Taiwan  
  *(2012 – 2019)*

- **M.S.**, Department of Medical Laboratory Science and Biotechnology  
  Taipei Medical University, Taiwan  
  *(2008 – 2011)*

---

## 🧪 Professional Experience
- **Assistant Professor**,  
  Department of Biochemistry and Molecular Biology,  
  Taipei Medical University, Taiwan *(2024 – Present)*

- **Postdoctoral Fellow**,  
  Johns Hopkins University School of Medicine, USA *(2022 – 2024)*

- **Postdoctoral Researcher**,  
  National Taiwan University, Taiwan *(2019 – 2021)*

- **Visiting Scholar**,  
  Department of Urology, UT Southwestern Medical Center, USA *(2016 – 2018)*

- **Visiting Scholar**,  
  Department of Radiation Oncology, UT Southwestern Medical Center, USA *(2015 – 2016)*

---

## 🏆 Honors & Awards
- **National Innovation Award (Taiwan)**

- Poster Presentation, *Polyploidy Across the Tree of Life* *(2023)*  
- Poster Presentation, *American Association for Cancer Research (AACR)* *(2017, 2023)*  
- New Partnership Program for the Connection to Top Laboratories in the World *(2015–2018, 2021–2023)*  
- Postgraduate Outstanding Academic Research Award, National Taiwan University *(2020)*  
- Excellent Oral Presentation Award, Jun-Yaw Lin Science and Education Foundation *(2019)*  
- Higher Education Sprout Project *(2019–2021)*  
- LungYen Foundation Scholarship *(2013, 2014)*  
- Taiwan Rotary Academic Scholarship *(2015)*  

---

## 🔬 Research Interests
- Urological cancers  
- Cancer metabolism and lipid metabolism  
- Transcriptional and metabolic remodeling  
- Mechanisms of cancer therapy resistance  
- Predictive models for therapeutic targets
**Contact**  
Email: bryancflee@tmu.edu.tw
-->
