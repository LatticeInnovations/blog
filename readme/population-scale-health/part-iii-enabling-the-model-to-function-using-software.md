# Part III: Enabling the model to function, using software

The model design presented in the prior section needs software to function. Temporal health data, risk assessment algorithms, capability maps, and group-based interventions—all of these elements require digital representation to perform to their full potential. In this concluding section, we will identify key functions that a software system should perform to enable population-scale health assessment and intervention.

We assume a **mobile-first software system**, in which beneficiaries, community health workers, and primary care staff, all use mobile apps. We assume that smartphones are commonly available among beneficiaries, but do _not_ assume that they are ubiquitous. In such a system, data is housed both on mobile devices, and in a central server.

All elements of the model map to functions, as shown in the table below.

<figure><img src="../../.gitbook/assets/image (13).png" alt=""><figcaption><p>Figure 4: Mapping model to function</p></figcaption></figure>

We conclude with a section on separating clinical aspects from procedural ones, informed by our implementation experiences.

## The right questions, at the right time <a href="#beff" id="beff"></a>

In a temporal risk profile, every interaction between a beneficiary and a care provider adds data to the beneficiary’s health record. To build such longitudinal records, the data collection instrument—such as an app used by a community health worker (CHW)—has to deliver intelligent prompts. Such prompts help collect the most valuable data first — enabling efficient service delivery. Efficiency is a key objective, because care providers have limited time.

For example, if a 60-year old male reports no current complaints, then two data points have immediate value — abdominal obesity, and resting blood pressure — to assess their risk of diabetes and cardiovascular disease. However, if the same person reports being chronically short of breath, then response to a salbutamol inhaler is a valuable next step — to assess risk of COPD versus Asthma.

Question selection is as critical as question sequencing. For instance, a 2017 Peruvian study \[[4](https://www.thelancet.com/journals/laninf/article/PIIS1473-3099\(17\)30447-4/fulltext)] demonstrated that exposure to indoor smoke was a more important contributor to TB risk than self-reported cough frequency; the latter had no meaningful impact. Thus, to estimate TB risk, it would be of far greater value to ask how a household cooks, rather than how much it coughs. Yet cough is a common question in TB screening forms, and indoor smoke data is rarely captured.&#x20;

Question selection also should take into account the shelf-life of data. Education and employment data has a relatively long shelf-life, whereas parameters like blood glucose are most valuable when “fresh”, and need to be checked often.

## Dimensions of configurability <a href="#id-0967" id="id-0967"></a>

### Adapting to varying capabilities <a href="#id-0967" id="id-0967"></a>

Assessments and intervention capability maps determine who acquires what information, at which tier of care. Hence, a CHW’s scope of work is the sum total of all the assessments and interventions mapped to the “Community” tier of the system.

In a generalizable software system, capability mapping has to be configurable — to provide a mutable structure within which care pathways operate.

Even so, the system needs to be loosely coupled; it cannot be strictly sequential. A hypertensive patient may be directly diagnosed at a tertiary care center, because they chose not to participate in community screening efforts. The system must accommodate such scenarios.

### Offline-capable

A software system that spans homes, communities and facilities has to be offline-capable. In most low-resource settings, internet access is erratic, and bandwidth is often limited.

Thus, the mobile app has to be able to perform all critical functions when offline. Consequently, it must store relevant data locally on the device, and exchange it with the server as and when the internet is available. During such sync operations, the app should limit both the bandwidth used, and the total payload.

Also, any logical updates, such as new risk algorithms, have to be packetized and then delivered to the app. Such packets should enable the app to reconfigure itself. Thus, the app has to be configurable, and cannot depend wholly on static code.

Finally, offline-capable designs need to incorporate added layers of data protection, because records are now available locally on phones.

## Beneficiaries as actors <a href="#id-2354" id="id-2354"></a>

Healthcare professionals in the public sector are often overloaded. This is particularly true of CHWs, who spend a large portion of their time moving door-to-door. The underlying assumption is that CHWs have to seek out beneficiaries in-person in order to effectively deliver services. While this is true for many aspects of care delivery, it can be supplemented by the actions of beneficiaries. Beneficiaries should be given the agency to act in concert with their CHW.

The commonest way in which health systems give greater agency and access to patients is by offering them telemedicine. However, this is a resource-intensive starting point, requiring good internet connectivity, new service delivery processes, and well-equipped smartphones. Also, it risks disintermediating the CHW, because access to telemedicine encourages patients to directly seek out doctors.

Instead, we recommend a system that strengthens the CHW-beneficiary link. Given this paradigm, the beneficiary app should enable two types of tasks:

1. **Load-leveling tasks**: Tasks that reduce data entry burden on CHWs — such as adding addresses and family member details of a beneficiary.
2. **Early-detection/ disease surveillance tasks**: Tasks that provide basic measures of a beneficiary’s wellness, without the need for any measurement tools — such as a smartphone-based vision test.

These two types of tasks are complementary — they free up the CHW’s time, and enable the CHW to utilize this time to contribute more meaningfully to community health.

## Patients’ ownership of data <a href="#id-7b3f" id="id-7b3f"></a>

Health records, and more generally, protected health information (PHI), is highly sensitive. Be it online or offline, it needs strong controls.

## Patient are data owners

PHI belongs to the patient. Often, patients assign these rights implicitly during the treatment process — this is implied consent. For example, when I interact with a CHW for a hypertension checkup, I grant them access to my vitals signs data. This consent is not expressly granted; rather, it is implicit based on my actions and the circumstances.

The software system must support rules that distinguish between implicit and explicit consent, and the latter should be supported digitally.

### Public health systems as data fiduciaries

A fiduciary is a person who holds a legal or ethical relationship of trust with a beneficiary, particularly when the fiduciary is more informed or skilled than the beneficiary. Medicine and law are everyday examples; we depend on our doctor or lawyer to use their specialized skills for our benefit.

In the context of PHI, public health systems act as data fiduciaries. Health systems maintain records of consent granted by patients, and control access to PHI based on the requestor’s identity. This is particularly critical when entities of varying affiliations contribute to, and access, a single individual’s PHI. An example — a private care provider accesses a patient’s blood pressure and body weight history collected by a CHW, arrives at a diagnosis, and provides a prescription. The software that governs such a system has to authenticate users, apply consent policies, and log the exchange of data — in a transparent, rigorous manner.

### Data storage principles

Once data is captured, its storage must be governed by three fundamental principles of purpose, duration, and proportionality. Data should be stored for a clearly defined purpose, for a fixed period of time, and in quantities or proportions that match the purpose. The principles have to be converted to policies, and policies have to be enabled by the software system.

## Interfacing with external systems <a href="#c481" id="c481"></a>

A wide variety of health indicators and operating processes has led to the creation of many customized software systems. Customization makes interfacing & interoperability challenging. A simple example is a patient’s name. Some software systems store it as a single string, whereas others store it in parts: given name, middle name, and family name. This difference in data models makes the two systems incompatible.

The increasing adoption of Fast Healthcare Interoperability Resources (FHIR®) has brought standardization to both data models, and mechanisms of exchange. FHIR is a core part of HL7 standards. It adds value in the following ways:

1. It defines the minimum structure that common data objects must adhere to.
2. It encourages the use of contemporary software interfaces for data exchange.
3. It provides easy integration of standardized clinical nomenclature systems, such as ICD-10, SNOMED-CT, and LOINC. The first two focus on conditions, diseases and symptoms. LOINC focuses on physiological parameters & lab tests.
4. It leaves room for healthcare systems to add their own customization, without disturbing the core data model, using a feature called Profiling.

Today, any software system developed for a large health system must be FHIR compliant by design. Interfaces with external, non-health systems can and will lie outside FHIR — and require judicious customization. Some design considerations for external interfaces are:

1. External systems may require batch processing — in such a case, APIs (application programming interfaces) should be able to handle batch data.
2. Data should be exchanged only via APIs. Direct data insertion must be avoided.
3. External systems that contribute to health data may, someday, ask for their data to be discarded. This must be considered while designing partitions between internal and external data sets.

## Separating the clinical from the procedural <a href="#id-97ac" id="id-97ac"></a>

Procedural aspects emerge from administrative policies used to govern a health system, but are unrelated to clinical knowhow. For instance, medicine dispensing at home may require approvals from administrative officers, and periodic inventory verification. Procedural elements must be kept separate from clinical elements, so they they can be independently configured.
