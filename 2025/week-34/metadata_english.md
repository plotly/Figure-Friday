
**Data Dictionary**

**Incident number (Numeric):** Unique number that identifies each incident

**Incident type (List of values):** Identification of the type of incident

* T: Train
* S: Station

**Primary cause (List of values):** Primary cause determined following analysis of the incident

* Customers
* Material on wheels
* Fixed equipment
* Train operations
* Other

**Secondary cause (List of values):** Secondary cause determined following analysis of the incident

* Injured or sick person
* Intentional mischief
* Unintentional nuisance
* Customers
* MPM-10
* MR-73
* Work vehicle
* Track service
* Train service
* Station service
* TCPE service
* Fixed equipment
* Line 1,2,4,5
* Control center
* Train operations
* External causes
* Réno-Stations contracts
* Réno-System contracts
* MPM-10 contracts
* STM staff/equipment
* External staff/equipment
* Other

**Symptom (List of values):** Initial cause attributed at the time of the incident

* Customers
* Material on wheels
* Fixed equipment
* Train operations
* Fire, smoke, odor, substance, etc.

**Line (List of values):** Name of the line on which the incident occurred

* 1: Green line
* 2: Orange line
* 4: Yellow line
* 5: Blue line

**Run number (Numeric):** Run number of the train associated with the incident; “#” indicates there is no associated run

**Date of day (Alpha) (Date and/or time):** Calendar day of the incident

**Incident time (Date and/or time):**

* For train incidents: Start time of the delay (customer service) for the incident (not the start time of the incident itself)
* For station incidents: Start time of the incident

**Recovery time (Date and/or time):**

* For train incidents: End time of the delay (customer service) for the incident (not the actual end time of the incident)
* For station incidents: End time of the incident

**Day of the month (Date and/or time):** Day of the month of the incident

**Vehicle (Numeric):** Car number of the train involved in the incident, or “#” if no car is involved

**Car door (Number) (Variable text):** Number of the door(s) involved in the incident (1 to 8 and “all”), or “#” if no door is involved

**Material on wheels type (List of values: 73;10):** Type of material on wheels (MR-73 or MPM-10)

**CAT (Boolean):** Indicator of traction power cut (1: yes / 0: no)

**Material damage (Boolean):** Indicator of possible damage to the train (1: yes / 0: no)

**KFS (Boolean):** Indicator of the use of the emergency brake by customers (1: yes / 0: no)

**Door (Boolean):** Indicator of the involvement of a door in the incident (1: yes / 0: no)

**Metro emergency (Boolean):** Indicator of the involvement of the metro emergency team at the request of the control room (1: yes / 0: no)

**Location code (Variable text):** Location of the incident

**Evacuation (Variable text):** Indicator of the evacuation of a car, a train, a station, or both a station and a train; “#” indicates no evacuation for the incident

**Calendar year (Date and/or time):** Year of the incident

**Calendar year/month (Date and/or time):** Year/month of the incident

**Calendar day (Date and/or time):** Calendar day of the incident

**Day of the week (Date and/or time):** Day of the week of the incident

**Calendar month (Date and/or time):** Calendar month of the incident
