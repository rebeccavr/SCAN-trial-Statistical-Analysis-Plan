# SCAN-trial-Statistical-Analysis-Plan
The purpose of this script is to address survey data from the SCAN trial, specifically regarding the primary outcome and secondary outcome psychometrics.

### **SCAN TRIAL STATISTICAL ANALYSIS PLAN**

Authors: D.M. and R.V.R.
Date: 02/05/2025
Trial Registration: ACTRN12622000634774

The purpose of this script is to address survey data from the SCAN trial, specifically regarding the primary outcome and secondary outcome psychometrics. 

We will release at first all steps required for the primary outcome statistical analysis with detail regarding the secondary outcome calculations which will be added in more detail as we finalise the secondary outcome analysis. 

All steps for the primary outcome are finalised and will allow for the study unblinding. 

_STATISTICAL ANALYSES_

**Primary Outcome (Pain)**

In the primary outcome analysis we will be looking into overall pain (i.e. all pain ratings over the trial period) as well as maximum pain (i.e. the maximum pain of each day).
The aim of including both is to understand whether more specific natures to the pain are modified during the treatment period.

The primary outcome is composed of an 11-point scale ascending from 0 to 10. This data is ordinal but close to continuous. 
As such we will firstly check the data using models more appropriate to ordinal data. If an ordinal approach is not appropriate we will move on to a continuous with minimal modifications to the data
(i.e. avoiding any manipulation due to the fact that the data contains 0s)

A few key variables will be analysed to account for key effects: 

(1) We have the following factors:
 Treatment (treatment) = 2-Level (WS) Categorical: CBD, Placebo
 Phase (phase) = 2-Level (WS) Categorical: Inactive (Week 1), Active (Weeks 2-6)
 *Day (day_tx) = Continuous
 Time of Day (time) = 3-Level (WS) Categorical: T1, T2, T3
Note: Treatment Order (order) (2-Level (BS) Categorical: CBD First, Placebo First) and Treatment Period (arm) (2-Level (WS) Categorical: Period 1, Period 2) may also be relevant.
*We will be mindful that Phase and Day will be fully collinear because they correspond to non-overlapping ranges.

(2) We are primarily looking for one of the following effects:
 A significant Treatment by Phase interaction (i.e., lower Pain on CBD than Placebo during the Active Phase)
 A significant Treatment by Day interaction (i.e., a greater reduction in Pain over time on CBD than Placebo)
 A significant Treatment by Phase by Day interaction (i.e., a greater reduction in Pain over time on CBD than Placebo during the Active Phase)

As such, we need to run the following analyses (and select the model with the lowest AIC):
 a) Treatment * Phase
 b) Treatment * Day
 *c) Treatment * Phase * Day
 *the 'next best' model will be used if any of the fixed effects in this one have VIFs >10.

Once we have identified the 'best' models (i.e., one each for overall and maximum pain), we will test whether any of the following improve their fit (i.e., reduce the AIC further):
 d) [a, b or c] + Time of Day
 e) [a, b or c] + Treatment Order
 f) [a, b or c] + Treatment Period
 g) [a, b or c] * Time of Day
 h) [a, b or c] * Treatment Order
 Note 1: If the 'preferred' model contains a four-way interaction (e.g., Treatment * Phase * Day * Time of Day), we may opt for the 'next best' alternative.
 Note 2: we will not use d or g in our analysis of maximum pain (as Time of Day is no longer a factor).

**Secondary Outcomes (Stress, Anxiety, Depression, Neuropathic Pain, Pain Catastrophisation, Sleep)**

In our secondary outcome analysis we will be looking at individual surveys regarding a range of characteristics.
The aim is to observe whether the surveys are impacted by the treatment phase (i.e. active or inactive) and type of treatment (i.e. CBD or placebo).

(1) We have the following factors:
 Treatment = 2-Level (WS) Categorical: CBD, Placebo - ip_sec
 Time = 2-Level (WS) Categorical: Pre-Treatment, Post-Treatment - preorpost
 Treatment Order = 2-Level (BS) Categorical: CBD First, Placebo First - order_sec
 Treatment Period = 2-Level (WS) Categorical: Period 1, Period 2 - arm_sec

(2) We are primarily looking for one of the following effects (and we will select the model with the lowest AIC):
 a) Treatment * Time
 b) Treatment * Time + Treatment Order - This will identify and control for systematic differences between the CBD-PLA and PLA-CBD groups (e.g., if randomisation is not 100% effective)
 c) Treatment * Time + Treatment Period - This will identify and control for systematic differences between the first and second treatment period
 d) Treatment * Time * Treatment Order - This will identify and control for carryover effects (i.e., time- and/or treatment-dependent differences between the CBD-PLA and PLA-CBD groups)

Data will be treated as categorical based on survey classifications. If categorical models fail we will then treat data as continuous.
Once you have identified the model with the lowest AIC, we will need to check any issues with the models (i.e. collinearity and normality (Shapiro-Wilk test, p>0.05) and homoscedasticity (Levene test, p>0.05) in the case of continuous models)
If the continuous model violates assumptions or normality or homoscedasticity, we will need to SQRT transform the data and re-analyse it. This will happen again but with a LOG transform if the model continuous to fail testing.
We will not modify the data structure of the data if they contain 0s. Therefore in these cases we will not SQRT or LOG transform it (i.e. avoiding any manipulation due to the fact that the data contains 0s).

Though the above we have the capacity to identify situations where participants who receive CBD First differ from those who receive Placebo First (particularly at the Pre-Treatment time point) during Treatment Period 2.
