# MeterData2Topics (work in progress) NLP LDA results are not yet published
Convert residential electrical power meter time series datasets, to NLP "document" sentences, to an LDA vector space, to a topic 

Automation is gathering granular 2-second multiple time-series datasets from a residential electrical power meter, with the objective of identifying what appliances are in use at any given time. An electrical power expert might be able to look at the time series metered usage data and infer what electrical devices are in use. As more appliances are in use, it becomes difficult for a human to discern accurately, which appliances are consuming electrical power.

On the preprocessing pass, a signal processing application creates timestamped event "documents" for every transition in the time series. The sentence is made up of descriptive pseudo words summarizing what is taking place during changes in electrical power usage. Transforming the time series events to descriptive document sentences is effectively compression, it allows one to read a timeline of document sentence events, and map each document sentence to a vector space via  Latent Dirichlet Allocation (LDA). This is an unsupervised problem and inferring a topic requires a subject matter expert, to define a cluster of similar topics. One such subject would be "refridgerator" (the fridge is running).

#### example of residential appliances
*`refridgerator, washer, dryer, dishwasher, furnace, toaster oven, instant pot, mrcoffee, breville expresso machine, etc`*

#### Three document sentences that note, the refridgerator is running or just turned-off. The NLP topic could be called "refridgerator"
1) `2021-03-09 01:11:52-07:00 Tb0.4 Ib2 pfbDot6 OffHours`
2) `2021-03-09 01:13:28-07:00 Tb-0.4 Ib1.6 OffHours`
3) `2021-03-09 01:15:04-07:00 Tb-0.6 pfbDot-19 OffHours`

#### words from the first sentence and what that sentence means (the topic would be refridgerator, it just turned-on) 
`Tb0.4` there was a first derivate transient in current, on the 120volt B leg of the power

`Ib2` the current sensor on the B leg is using 2amps of current

`pfbDot6` the current sensor on the B leg is measuring a first derivate transient in power factor

`OffHours` the transient document sentence took place in the middle of the night

## An eyedro application view of their A & B current sensors:

The blue line is the B 120 volt leg current and it supports the refridgerator. The fridge turned-on and ran over 14 times in the day, creating periodic spikes in the current usage. The orange line is the A leg current and it supports the furnace pump, 

![eyedro application view](https://github.com/jearlcalkins/MeterData2Topics/blob/main/Screenshot%202021-04-20%2009.48.25.png)

## A python processed view of the A & B current

The A leg current is ia, the B leg current is ib, the first derivative of A current dA/dt is iaDot, dB/dt is ibDot, the A & B powerfactors are apf and bpf. Measured powerfactor provides insight into the type of load is drawing current. A PC's power supply and motors have a power factor, whereas there is no power factor when you have a resistive load like an electric stove or a Mr Coffee.

![eyedro application view](https://github.com/jearlcalkins/MeterData2Topics/blob/main/i_didt_pf.png)
