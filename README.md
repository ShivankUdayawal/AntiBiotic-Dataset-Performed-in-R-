# AntiBiotic Dataset
## Classify Suspected Infection in Patients (MedTourEasy)

## Patient may have sepsis
Sepsis is a deadly syndrome where a patient has a severe infection that causes organ failure. The sooner septic patients are treated, the more likely they are to survive, but sepsis can be challenging to recognize. It may be possible to use hospital data to develop machine learning models that could flag patients who are likely to be septic. However, before we develop predictive algorithms, we need a reliable method to determine patients who are septic. One component of sepsis is a severe infection.

In this project, we will use two weeks of hospital electronic health record (EHR) data to find out which patients had a severe infection according to four criteria. We will look into the data to see if a doctor ordered a blood test to look for bacteria (a blood culture) and gave the patient a series of intervenous antibiotics.

## Antibiotics
These data represent all drugs administered in a hospital over two weeks. Each row represents one time a patient was given an antibiotic. The variables include the patient identification number, the day the drug was administered, the name of the antibiotic, and how it was administered. For example, patient "8" received doxycycline by mouth on the first day of their stay.

We will identify patients with a serious infection using the following criteria.

Criteria for Suspected Infection*

1. The patient receives antibiotics for a sequence of four days, with gaps of one day allowed.
2. The sequence must start with a new antibiotic, defined as an antibiotic type that was not given in the previous two days.
3. The sequence must start within two days of a blood culture.
4. There must be at least one intervenous (I.V.) antibiotic within the +/-2 day window.

### blood culture data
Data are in blood_cultureDT.csv. Let's start by reading it into the workspace and having a look at a few rows.

Each row represents one blood culture and gives the patient's id and the day the blood culture test occurred. For example, patient "8" had a blood culture on the second day of their hospitalization and again on the thirteenth day. Notice that some patients from the antibiotic dataset are not in this dataset and vice versa. Some patients are in neither because they received neither antibiotics nor a blood culture.

### Check the I.V. requirement
Now let's look at the fourth item in the criteria.

Criteria for Suspected Infection*

1. The patient receives antibiotics for a sequence of four days, with gaps of one day allowed.
2. The sequence must start with a new antibiotic, defined as an antibiotic type that was not given in the previous two days.
3. The sequence must start within two days of a blood culture.
4. There must be at least one intervenous (I.V.) antibiotic within the +/-2 day window


### first day of possible sequences
We're getting close! Let's review the criteria again.

Criteria for Suspected Infection*

1. The patient receives antibiotics for a sequence of four days, with gaps of one day allowed.
2. The sequence must start with a new antibiotic, defined as an antibiotic type that was not given in the previous two days.
3. The sequence must start within two days of a blood culture.
4. There must be at least one intervenous (I.V.) antibiotic within the +/-2 day window.

### Find the prevalence of sepsis
In this project, we used two EHR datasets to flag patients who were suspected of having a serious infection. We also got a data.table workout!

So far, we've been looking at records of all antibiotics administered and blood cultures that occurred over two weeks at a particular hospital. However, not all patients who were hospitalized over this period are represented in combinedDT because not all of them took antibiotics or had blood culture tests. We have to read in and merge the rest of the patient information to see what percentage of patients at the hospital might have had a serious infection.
