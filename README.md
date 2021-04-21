# MeterData2Topics
Convert power meter time series datasets to NLP document sentences to an LDA vector space

Automation is gathering granular 2-second multiple time-series datasets from a residential electrical power meter, with the objective of identifying what appliances (*) are in use at any given time. An electrical power expert might be able to look at the time series metered usage data and infer what electrical devices are turned on. As more appliances are in use, it becomes difficult for a human to discern accurately, which appliances are consuming electrical power.

On the preprocessing pass, a signal processing application creates timestamped event "documents" for every transition in the time series. The sentence is made up of descriptive pseudo words summarizing what is taking place during changes in electrical power usage. Transforming the time series events to descriptive document sentences is effectively compression, it allows one to read a timeline of document sentence events, and map each document sentence to a vector space via  Latent Dirichlet Allocation (LDA).

![eyedro application view]
(https://github.com/jearlcalkins/MeterData2Topics/blob/main/i_didt_pf.png)
![eyedro application view]
(https://github.com/jearlcalkins/MeterData2Topics/blob/main/Screenshot%202021-04-20%2009.48.25.png)

* washer, dryer, dishwasher, furnace, toaster oven, instant pot, etc
