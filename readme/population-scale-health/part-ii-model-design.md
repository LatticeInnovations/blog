# Part II: Model design

## From snapshots to temporal data <a href="#id-2998" id="id-2998"></a>

Conventional risk assessment models assess risk at a particular point in time. This is based on the paradigm that past data is inaccessible — a paradigm that is ripe for inversion.

For instance, the [INTERHEART](https://www.thelancet.com/journals/lancet/article/PIIS0140-6736\(04\)17018-9/fulltext) 10-year-risk score for acute myocardial infarction emphasizes smoking history & status. However, this information is sought at one specific point in time — a snapshot. If smoking status were available across time, we would be able to compute a more graded risk score — with higher confidence.

## Risk assessment: choosing what to ask <a href="#b47d" id="b47d"></a>

Risk assessment design starts by deconstructing risk factors by disease. Then, based on how much each factor contributes to population-scale health, they have to be reintegrated. For instance, the utility of measuring oxygen saturation has significantly increased since 2020 — low SpO2 is a risk factor for both COVID-19 and chronic respiratory illnesses.

This cycle of deconstruction and reintegration has to be performed each time a new disease is added to the scope of population health. The choice of which diseases to address is a function of their incidence, prevalence, morbidity and mortality. The desired result — clinically useful estimates of risk for the majority of diseases affecting the population. One limitation of clinical utility is — many prominent risk models originate in western countries, and do not translate well to most of Asia and Africa. Primary research is required to correct this imbalance.

## Enabling configurable algorithms <a href="#id-167f" id="id-167f"></a>

Risk is population-specific, hence algorithms need to be configurable. However, the master set of factors that drives risk assessment is relatively constant. It needs to be updated only when a new predictor of risk is identified. In this manner, we can determine a master set of factors, and use subsets to assess risk of individual diseases in specific populations.

Consider cardiovascular disease, where large bodies of evidence have been used to create several risk models — such as FRS, PROCAM, SCORE, INTERHEART and WHO-CVD-PEN protocols. These models vary in the weights they assign to a risk factor, and their applicability varies across populations. However, they use a common set of parameters — Age, Gender, Family history, Smoking status & history, Systolic and diastolic blood pressure, Total & HDL cholesterol, and Diabetes status.

Though configurable, the system should provide pre-set algorithms — to introduce a deliberate bias towards scientific rigor and evidence-based medicine. Health systems may override these presets if they have more robust, context-specific evidence.

## Integrating self-reported data <a href="#id-369c" id="id-369c"></a>

Data acquired directly from individuals provides early signals that can trigger interventions well ahead of traditional, facility-centric health information systems. Self-reported health status is the foundation on which community- and facility-based care can be delivered.

## Expanding data sources <a href="#id-08a0" id="id-08a0"></a>

Public health extends beyond health — it involves the environment, socioeconomics, education, nutrition, and more. Thus, data sources must extend to non-healthcare information systems, such as employment & income data housed in labor departments, or sanitation data from public works departments. These data sets need not be precisely mapped to individuals. They should be mappable to population groups, so that _a priori_ risk can be estimated more accurately. Such estimates help direct community-based screening programs for maximum impact. For instance, data about sanitation conditions aids screening efforts for dengue, chikungunya and malaria.
