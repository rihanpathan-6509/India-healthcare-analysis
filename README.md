# India Healthcare Analysis

Research and data analysis across 3 critical healthcare problem statements in India.
Built as a mentorship project under Yogeshwar Radhakrishna (Clinical Engineer, NHS UK).

---

## Problem Statements

| # | Problem | Core Finding |
|---|---|---|
| 1 | Shortage of Doctors in Rural India | 31,550 specialist posts unfilled; Jharkhand has 0.78 doctors per lakh rural population |
| 2 | Undiagnosed Diabetes in India | 38.6 million diabetics don't know they have it; waist circumference is the strongest predictor (OR 47.45) |
| 3 | Delayed TB Detection in India | Median delay of 87 days from symptom to treatment; 228,000 cases undetected in 2023 |

---

## Approach

### Problem 1 — Rural Healthcare Infrastructure

- RHS / Health Dynamics of India data: 2005 to 2023 (7 years)
- Specialist vacancy analysis by type: surgeon, gynaecologist, physician, paediatrician
- Correlation between rural population % and doctor density
- Vulnerability index built across 28 states

### Problem 2 — Undiagnosed Diabetes

- NFHS-5 (2019-21): high blood sugar, BMI, waist breakdown by state, gender, urban/rural
- ICMR-INDIAB Phase I and IDF Atlas 2025: national burden and clinical estimates
- IDRS (Indian Diabetes Risk Score) structure and validation documented
- Post-COVID data limitation clearly noted (NFHS-6 expected 2026-27)

### Problem 3 — TB Detection Delay

- India TB Report 2024: national trends 2015-2023
- Detection delay breakdown by age, gender, rural/urban, literacy
- Correlation analysis: NAAT coverage vs detection rate (R² = 0.38); HCW density vs detection rate (R² = 0.47)
- COVID impact on notifications (38% crash in 2020, recovery by 2023)

---

## Key Numbers

| Metric | Value |
|---|---|
| Unfilled specialist posts (CHCs, 2023) | 31,550 |
| States in critical doctor shortage zone | 15 of 28 |
| Worst state — doctors per lakh rural pop | Jharkhand: 0.78 |
| Total diabetics in India (IDF 2025) | 89.8 million |
| Undiagnosed diabetics | 38.6 million (43%) |
| Waist circumference — diabetes Odds Ratio | 47.45 |
| Median TB detection delay (national) | 87 days |
| Rural vs urban delay gap | 97 days vs 66 days (+31 days) |
| Undetected TB cases (2023) | 228,000 |
| TB detection rate (2023) | ~92% (up from 53% in 2015) |
| COVID impact on TB notifications (2020) | −38% in one year |
| NAAT coverage vs detection rate (R²) | 0.38 |
| HCW density vs detection rate (R²) | 0.47 |

---

## Solutions

9 product solutions across all 3 problem statements — each with implementation detail, tech stack, advantages, drawbacks, and competitor analysis.

| ID | Solution | Tools |
|---|---|---|
| R1 | PHC Status App | WhatsApp API, Python, FastAPI, PostgreSQL |
| R2 | Specialist Shortage Intelligence Dashboard | Python, React, D3.js, GeoJSON |
| R3 | Offline-First Rural Health SDK | PouchDB, CouchDB, PWA, Exotel |
| D1 | IDRS WhatsApp Screener | Twilio, Python, Redis, FastAPI |
| D2 | Diabetes Risk Intelligence Dashboard | Python, Pandas, React, Mapbox |
| D3 | Post-Screening Behavior Coaching | WhatsApp API, Celery, Python |
| T1 | AI Chest X-Ray TB Screening | PyTorch, ONNX, ResNet-50, TBX11K dataset |
| T2 | TB High-Risk Area Predictor | XGBoost, Python, Nikshay data, FastAPI |
| T3 | Missed-Call TB Symptom Screener | Exotel IVR, Python, Twilio |

Full detail in `reports/solutions_report.docx`

---

## Project Structure

```
india-healthcare-analysis/
│
├── rural_healthcare                                        # Problem Statement 1
│   ├── datasets
│   │   ├── Official_Reports-Data/                          # Source PDFs
│   │   │   ├── RHS 2018-19.pdf
│   │   │   ├── RHS 2019-20.pdf
│   │   │   ├── RHS 2020-21.pdf
│   │   │   └── RHS 2021-22.pdf
│   │   ├── rhs_2005.xlsx                                   # Baseline RHS data
│   │   ├── rhs_2019.xlsx
│   │   ├── rhs_2020.xlsx
│   │   ├── rhs_2020_vacancies_shortfalls.xlsx
│   │   ├── RHS_2020_21_and_2021_22.xlsx                    # Combined 2020-21 & 2021-22 data
│   │   ├── RHS_Healthcare_Infrastructure_2021_23.xlsx       # Extended 2021–2023 data
│   │   ├── rhs_population_density.xlsx
│   │   └── rhs_villages_districs_area.xlsx
│   ├── rural_healthcare_analysis.ipynb                     # Main analysis notebook
│   ├── rural_healthcare_report.docx                        # Full report
│   └── specialist_vacancy_analysis.ipynb                   # Specialist type breakdown
│
├── undiagnosed_diabetes                                    # Problem Statement 2
│   ├── dataset
│   │   ├── Official_Reports-Data/                          # Source PDFs
│   │   │   ├── IDF_Diabetes_Atlas_11th_Edition_20...pdf
│   │   │   ├── INDIAB.pdf
│   │   │   ├── NFHS5.pdf
│   │   │   └── PuneIDRS.pdf
│   │   ├── IDF_Diabetes_Atlas_2025.xlsx                    # IDF Atlas 2025 national estimates
│   │   ├── INDIAB.xlsx                                     # ICMR-INDIAB extracted dataset
│   │   ├── NFHS5.xlsx                                      # NFHS-5 extracted dataset
│   │   └── PuneIDRS.xlsx                                   # Pune IDRS extracted dataset
│   ├── undiagnosed_diabetes_india.ipynb                    # Main analysis notebook
│   └── undiagnosed_diabetes_report.docx                    # Full report
│
├── tb_detection_delay                                      # Problem Statement 3
│   ├── dataset
│   │   ├── Official_Reports-Data/                          # Source PDFs
│   │   │   └── TB-Report_for-Web_08_10-2024-1.pdf          # India TB Report 2024 (source)
│   │   ├── India_TB_Report_2024_DataBook.xlsx              # Structured TB databook
│   │   └── TB_India_Detection_Delay_Analysis.xlsx          # Structured TB dataset
│   ├── TB_India_Detection_Delay_Analysis.ipynb             # Main analysis notebook
│   └── TB_detection_report.docx                            # Full report
│
├── reports                                                 # All reports in one place
│   ├── NFHS_IDRS_Supplementary_Note.docx                   # NFHS data + IDRS structure
│   ├── rural_healthcare_report.docx
│   ├── solutions_report.docx                               # All 9 product solutions
│   ├── TB_detection_report.docx
│   └── undiagnosed_diabetes_report.docx
│
├── .gitignore
├── requirements.txt
└── README.md
```

---

## Run Locally

```bash
# 1. Clone the repo
git clone https://github.com/rihanpathan-6509/india-healthcare-analysis.git
cd india-healthcare-analysis

# 2. Install dependencies
pip install -r requirements.txt

# 3. Open any notebook
jupyter notebook rural_healthcare/rural_healthcare_analysis.ipynb
jupyter notebook undiagnosed_diabetes/undiagnosed_diabetes_india.ipynb
jupyter notebook tb_detection_delay/TB_India_Detection_Delay_Analysis.ipynb
```

---

## Dependencies

```
pandas
numpy
matplotlib
seaborn
scikit-learn
jupyter
openpyxl
adjustText
```

---

## Data Sources

### Problem Statement 1 — Rural Healthcare

| Dataset | Publisher | Year | Used For |
|---|---|---|---|
| Rural Health Statistics (RHS) 2005 | MoHFW, GoI | 2005 | Baseline doctor, specialist, and facility counts by state |
| Rural Health Statistics (RHS) 2019 | MoHFW, GoI | 2019 | Mid-period tracking of workforce and infrastructure growth |
| Rural Health Statistics (RHS) 2020 | MoHFW, GoI | 2020 | Latest Phase 1 snapshot — vacancies, shortfalls, all staff categories |
| Rural Health Statistics 2020-21 & 2021-22 | MoHFW, GoI | 2021–22 | Specialist breakdown by type — Tables 19 (Surgeons), 20 (OB&GY), 21 (Physicians), 22 (Paediatricians) |
| Health Dynamics of India 2022-23 | MoHFW, GoI | 2023 | Most recent CHC and specialist counts (PIB Press Release, Sept 2024) |
| Census of India 2011 | Registrar General of India | 2011 | Rural population %, village counts, geographic area by state |

### Problem Statement 2 — Undiagnosed Diabetes

| Dataset | Publisher | Year | Used For |
|---|---|---|---|
| NFHS-5 — Tables S2, S4, S5 | MoHFW, GoI | 2019–21 | State-level undiagnosed prevalence by gender; age, education, BMI, and healthcare access breakdown |
| ICMR-INDIAB Phase I | Indian Council of Medical Research | 2011 | Urban vs rural newly diagnosed rates; disease awareness levels |
| IDF Diabetes Atlas, 11th Edition | International Diabetes Federation | 2025 | Total diabetic population (89.8M); undiagnosed count (38.6M); 2050 projection (156.7M) |
| Patil & Gothankar 2016 | WHO Bulletin (peer-reviewed) | 2016 | Community IDRS study, Pune slum (n=383); waist circumference Odds Ratio 47.45 |
| MDRF-CURES IDRS Paper | IJEM Vol.17 Issue 1 | 2013 | IDRS tool structure, scoring, validation — sensitivity 72.5%, NPV 95.1% |

### Problem Statement 3 — TB Detection Delay

| Dataset | Publisher | Year | Used For |
|---|---|---|---|
| India TB Report 2024 | Central TB Division, MoHFW | 2023 data | National incidence, notifications (2.55M), treatment success (87%), detection rate trend 2015–2023 |
| WHO Global TB Report 2023 | World Health Organization | 2022/2023 | Country-level burden estimates; cross-validation of India incidence figures |
| NTEP / Nikshay Programme Data | National TB Elimination Programme | 2023 | State-wise case notification rates; private sector notification share |
| Patient Pathway Delay Studies | Published literature (meta-analysis) | Multiple | Median delay figures by patient group — rural vs urban, literate vs illiterate, TB type |
| NHM Human Resources Data | National Health Mission | 2023 | Healthcare worker density per 10,000 population by state |
| NFHS-5 / Census 2011 | MoHFW / Registrar General | 2021 | Rural population %, literacy rates by state for correlation analysis |

---

## Author

**Rihan Pathan**
First Year BTech, AI & ML — Walchand College of Engineering, Sangli (Batch 2025-29)
Mentored by: Yogeshwar Radhakrishna, Clinical Engineer, Bedfordshire Hospitals NHS Trust, UK
