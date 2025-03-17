# Recommendations

## Separate fast-track and slow-track patients

Separate slow-track and fast-track patients should be separated into two different "lines" or patient pathways, so that patients who only require a single consultation are not slowed down by those who require a full laboratory/ radiology workup.

54% of all patients follow the slow-track—rounded up to 60% hereon.&#x20;

Of them, about 75% undergo Lab tests, 40% undergo a USG scan, and 25% undergo an X-Ray. This is illustrated in Annexure 1.

## Optimize physician load

A single patient consultation is completed in 246 seconds, or 2.5 minutes, based on the average of 58 observations on December 3.

Thus, it takes 2.5 minutes of a doctor’s time to serve a fast-track patient, and 5 minutes to serve a slow-track patient—assuming that the first consultation and subsequent diagnosis & prescription take an equal amount of time.

On a peak day with 400 OPD patients, “physician time” required is:

{% code overflow="wrap" %}
```
60% slow-track x 400 pts x 5 min + 40% fast-track x 400 pts x 2.5 min
= 1200 minutes + 400 minutes 
= 1600 minutes
```
{% endcode %}

OPD hours are from 9 am to 4 pm: 7 hours, or 420 minutes. Thus, 1600/ 420 ≈ 4 doctors are required to serve all patients.

The cycle time, or rate of operation of all other workstations, have to be set based on Physician capacity. The target cycle times are:

* The fast-track should be capable of serving 24 patients an hour, or one patient in 150s.&#x20;
* The slow-track should be capable of serving 36 patients an hour, or one patient in 100s.
* Common workstations the precede the physician workstation—registration and vitals—should be able to serve 24 + 36 = 60 patients per hour, or one patient every 60s.

Both registration and vitals workstations operate faster than the target cycle time of 60 seconds. Each registration counter is able to process a patient every 120 seconds, and with three registration counters operating in tandem, the cycle time is 40 seconds. The single workstation where vitals are measured operates at 58s per patient.

Physician load leveling


Fast-track patients should be assigned to a separate line, to speed them through the process. The following pattern of assignment is recommended so that load—in terms of time—is leveled across all physicians:

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption><p>Figure 5: Physician allocation 3:1 between slow-track and fast-track</p></figcaption></figure>

The cells indicate the number of patients seen by the end of each hour. For Physicians 2, 3 and 4, the first hour's output is 24 patients since they see both fast and slow track patients at that time.&#x20;

By the second hour, sufficient patients have their lab tests with them to return for the second consultation (diagnosis/ prescription), at an average throughput of 12 patients/ hour. The hour-long lunch break may be halved for the physicians to step out for in pairs.

With this configuration, the total OPD capacity is 456 patients/ day—25% higher than the current maximum of 400 patients/ day, and more t.

Modify the OPD coordinator's role


In the system described above, the OPD coordinator's role has to change. Currently, three OPD coordinators perform the following tasks:

1. Check which physician's queue is empty,
2. Announce a patient's name on the PA - based on OPD visit cards available with them,
3. Direct patients to physician, and
4. Keep the queue of patients away from the doctor's desk.

To implement the flow-balancing for physicians, their role will have to change to that a "flow controller". This will require them to perform the following tasks:

1. Use registration data to call patients as per their order of arrival
2. Anticipate which patients are in the fast track, and which are in the slow track.
3. Assign fast-track patients to a single doctor, the balance equally across the rest of the doctors.
4. Receive patient investigation reports from Lab/ X-Ray - so that patients do not have to wait outside the Lab/ X-Ray room
5. Assign slow-track patients to doctors for their second consultation (diagnosis/ prescription) once their investigation results are available

Such a workflow requires IT support. A single screen that enables the OPD coordinators to perform these tasks is shown in [Annexure 2](annexures.md#annexure-2-opd-coordinator-screen).

Reorganize Pharmacy Operations to Support 2 Tracks


Pharmacy operations is currently split across 2 workstations, in 3 steps. A patient has to queue up thrice to get a single prescription fulfilled.

<figure><img src="../.gitbook/assets/image (6).png" alt=""><figcaption><p>Figure 6: OPD Layout, with pharmacy operations highlighted</p></figcaption></figure>

### Current Workflow&#xD;

The steps are:

1. Data entry of medicines - transcription of the physician's prescription - 1 of 4 counter.
2. Payment - 1 of 4 counters of the registration desk, the only location where cash is collected. This counter is shared between all OPD service billing - Pharmacy, Radiology and Laboratory.
3. Dispensing of medicines - at the remaining 3 counters at the Pharmacy.

In order to streamline Pharmacy operations, date entry, billing, and dispensing should be organized as a single set of counters. This will provide the added benefit of increasing checks on billing within the process - between pharmacy and registration staff - and will improve ensure compliance with financial guidelines.

The 3 steps of Pharmacy operations serve patients at varying rates:

1. Data entry: 60s per patient per counter
2. Billing: 90s per patient per counter
3. Dispensing: 224s per patient per counter

### Proposed Design&#xD;

The target time for the fast track is 150s per patient, and that for the slow track is 100s per patient. To meet these target cycle times, the following design is proposed for Pharmacy operations:

<figure><img src="../.gitbook/assets/image (7).png" alt=""><figcaption><p>Figure 7: Pharmacy Operations - Fast-track in Blue, Slow-track in Red</p></figcaption></figure>

Since the fast-track counter has 20% more capacity than required, it can also serve IPD patients.

## Streamline Laboratory Operations

75% of all slow-track patients avail of laboratory services, which are composed of 6 types, as shown below. The table also has data about preparation time, testing time and total time. When total time is multiplied by load—the percentage of slow-track patients by test type—we arrive at the cycle time for each test type. This is stated in the last column.&#x20;

All values are in seconds.

<figure><img src="../.gitbook/assets/image (8).png" alt=""><figcaption><p>Figure 8: Lab operations load and cycle time</p></figcaption></figure>

The precursor to sample prep and test is blood sample collection, required for all test types except Urinalysis. This takes 120s per patient. Two counters operate in tandem, hence cycle time is 60s.\
Once test results are available, the last step is data entry (reports). This takes 45s per patient.

### Current Bottleneck - Biochemistry

Slow-track target cycle time is 100s. Biochemistry does not meet this target. Also, since 75% of all Biochemistry tests are performed in tandem with one or more other test types, lab technicians have to wait for biochemistry reports before they can hand out results.

### Solution - Centrifuges

In order to reduce cycle time for Biochemistry in a cost-effective manner, preparation time should be addressed. The only preparation required for blood-based tests is centrifuging. Lab-grade centrifuges are currently priced within Rs. 20,000 each.

The lab has two centrifuges, one with a capacity of 8 samples and a set time of five minutes, and the other with a capacity of 16 samples and a set time of ten minutes. The duration of centrifuging varies based on the number of test types a single sample of blood has to be split into—five minutes for single test-type, and ten minutes for two or more test-types.

In order to simplify and standardize centrifuging , we recommend that 2 additional centrifuges, of capacity 16 samples with 10 minute set time, be procured. Each centrifuge should be run every 4 minutes—without waiting for a full batch of 16 samples. Local efficiency is not the goal; global efficiency is.

Running four partially-loaded centrifuges will reduce preparation cycle time to 30 seconds, which in turn will reduce biochemistry cycle time to 95s.

This process change will also eliminate the need to split samples based on the number of test types, reducing error and re-work.

Streamline X-Ray Operations


Since 25% of all slow-track patients avail of X-Ray facilities, the cycle time required at this workstation is 100s/ 25% = 400s. Currently, the X-Ray workstation serves one patient every 519s.

However, this observation was made on a day with two X-Ray technicians; three technicians are allocated to this workstation.&#x20;

If the third person assists patients in changing their attire, then cycle time can be reduced to only imaging time—which ranged from 180s to 300s. This is well within the target of 400s.

Assisting patients to change their attire is not a technical task. Thus, with three x-ray technicians, it is possible to give off-cover, attend to some IPD requirements, and still perform within the target cycle time.