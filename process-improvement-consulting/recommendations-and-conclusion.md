# Recommendations & Conclusion

## Separate fast-track and slow-track patients

Separate slow-track and fast-track patients should be separated into two different "lines" or patient pathways, so that patients who only require a single consultation are not slowed down by those who require a full laboratory/ radiology workup.\


54% of all patients follow the slow-track—rounded up to 60% hereon. Of them, about 75% undergo Lab tests, 40% undergo a USG scan, and 25% undergo an X-Ray. This is illustrated in Annexure 1.

## Optimize physician load

One patient consultation is completed in 246 seconds, or 2.5 minutes, based on the average of 58 observations on December 3.

Thus, it takes 2.5 minutes of a doctor’s time to serve a fast-track patient, and 5 minutes to serve a slow-track patient—assuming that the first consultation and subsequent diagnosis & prescription take an equal amount of time.



On a peak day with 400 OPD patients, “physician time” required is:\


60% slow-track x 400 patients x 5 minutes + 40% fast-track x 400 patients x 2.5 minutes\
\= 1200 minutes + 400 minutes = 1600 minutes\


{% code overflow="wrap" %}
```
60% slow-track x 400 pts x 5 min + 40% fast-track x 400 pts x 2.5 min
= 1200 minutes + 400 minutes 
= 1600 minutes
```
{% endcode %}

OPD hours are from 9 am to 4 pm: 7 hours, or 420 minutes. Thus, 1600/ 420 ≈ 4 doctors are required to serve all patients.

The cycle time, or rate of operation of all other workstations, have to be set based on Physician capacity. The fast-track should be capable of serving 24 patients an hour, or one patient in 150s - the target cycle time. The slow-track should be capable of serving 36 patients an hour, or one patient in 100s.

Common workstations the precede the physician workstation—registration and vitals—should be able to serve 24 + 36 = 60 patients per hour, or one patient every 60s.

Both registration and vitals operate at lower cycle time - each registration counter is able to process a patient every 120 seconds (hence three operate @ 40s per patient) and the single counter that where vitals are measured operates at 58s per patient.

Physician Flow Balancing\
We recommend that fast-track patients be assigned a separate line – to speed them through the process. The following pattern of assignment is recommended so that flow is balanced across all physicians:

8\
AM\
9\
AM\
10 AM\
11 AM\
12 AM\
Lunch\
2\
PM\
3\
PM\
4\
PM

Day's Total\
Physician 1\
24\
24\
24\
24\
24

24\
24

168\
Physician 2\
24\
12\
12\
12\
12

12\
12

96\
Physician 3

24\
12\
12\
12

12\
12\
12

96\
Physician 4

24\
12\
12\
12

12\
12\
12

96

Legend:\
Both

Fast

Slow

Figure 5: Physician allocation 3:1 between slow-track and fast-track\
The cells indicate the number of patients seen by the end of each hour. For Physicians 2-4, the first hour's output is 24 patients since they see both fast and slow track patients at that time. By the second hour, sufficient patients have their lab tests with them to return for the second consultation (diagnosis/ prescription), at an average throughput of 12 patients/ hour. The hour-long lunch break may be halved for the physicians to step out for in pairs.\
With this configuration, the total OPD capacity is 456 patients/ day - 25% higher than the current maximum of 400 patients/ day.

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

Such a workflow requires IT support. A single screen that enables the OPD coordinators to perform these tasks is shown in Annexure 2.

Reorganize Pharmacy Operations to Support 2 Tracks


Pharmacy operations is currently split across 2 workstations, in 3 steps. A patient has to queue up thrice to get a single prescription fulfilled.

Figure 6: OPD Layout, with Pharmacy Operations highlighted\


Current Workflow\
The steps are:\
Data entry of medicines - transcription of the physician's prescription - 1 of 4 counter.\
Payment - 1 of 4 counters of the registration desk, the only location where cash is collected. This counter is shared between all OPD service billing - Pharmacy, Radiology and Laboratory.\
Dispensing of medicines - at the remaining 3 counters at the Pharmacy.\
In order to streamline Pharmacy operations, date entry, billing, and dispensing should be organized as a single set of counters. This will provide the added benefit of increasing checks on billing within the process - between pharmacy and registration staff - and will improve ensure compliance with financial guidelines.\
The 3 steps of Pharmacy operations serve patients at varying rates:\
Data entry: 60s per patient per counter\
Billing: 90s per patient per counter\
Dispensing: 224s per patient per counter\
Proposed Design\
The target time for the fast track is 150 s per patient, and that for the slow track is 100 s per patient. To meet these target cycle times, the following design is proposed for Pharmacy operations:

Figure 7: Pharmacy Operations - Fast-track in Blue, Slow-track in Red\
Since the fast-track counter has 20% more capacity than required, it can also serve IPD patients.



## Streamline Laboratory Operations

75% of all slow-track patients avail of laboratory services, which are composed of 6 types, as shown below. The table also has data about preparation time, testing time and total time (in seconds). When total time is multiplied by load (% of slow-track patients by test type), the results is the cycle time for each test type - the value in the last column. All values are in seconds unless otherwise specified.

Lab Test Type\
Prep\
Test\
Total\
Load\
Cycle Time\
Biochemistry\
60\
150\
210\
53%\
110\
Serology\
0\
30\
30\
51%\
15\
Hematology\
60\
180\
240\
30%\
73\
Clinical Path\
60\
120\
180\
30%\
53\
Urinalysis\
0\
150\
210\
27%\
41\
Virology\
0\
30\
30\
32%\
10

Figure 8: Lab operations load and cycle time\


The precursor to sample prep and test is blood sample collection, required for all test types except Urinalysis. This takes 120s per patient. Two counters operate in tandem, hence cycle time is 60s.\
Once test results are available, the last step is data entry (reports). This takes 45s per patient.\


### Current Bottleneck - Biochemistry

Slow-track target cycle time is 100s. Biochemistry does not meet this target. Also, since 3/4th of all Biochemistry tests are performed in tandem with one or more other test types, Lab technicians have to wait for Biochemistry reports to complete before they can hand out results.

Solution - Centrifuges

\
In order to reduce cycle time for Biochemistry in a cost-effective manner, preparation time should be addressed. The only preparation required for blood-based tests is centrifuging. Lab-grade centrifuges are currently priced within Rs. 20,000 each.\
The lab has 2 centrifuges - one with a capacity of 8 samples and a set time of 5 minutes, and the other with a capacity of 16 samples and a set time of 10 minutes. The duration of centrifuging varies based on the number of test types a single sample of blood has to be split into - 5 minutes for single test-type, and 10 minutes for two or more test-types.\
In order to simplify and standardize the centrifuging process, we recommend that 2 additional centrifuges, of capacity 16 samples with 10 minute set time, be procured. Each centrifuge should be run every 4 minutes - without waiting for a full batch of 16 samples. Even when run with 8 samples, this will reduce preparation time to 30 seconds, which in turn will reduce cycle time to 95s.\
This process change will also eliminate the need to split samples based on the number of test types - reducing error and consequent re-work.



Streamline X-Ray Operations


Since 25% of all slow-track patients avail of X-Ray facilities, the cycle time required at this workstation is 100s/ 25% = 400s. Currently, the X-Ray workstation serves one patient every 519s.\
However, this observation was taken on a day with two X-Ray technicians, instead of three. If the third technician assists patients in changing their attire, then the time taken per patient can be reduced to imaging time - which ranged from 180s to 300s - well within the target cycle time.

\


