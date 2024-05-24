
# Analysis of Shipment Delivery and Prediction of Delay

Road haulage is essential for the people and businesses of the UK. Approximately 90% of all goods transported by land in Great Britain are moved directly by road. DigiHaul is a digital transport business, specialising in managing, consolidating and integrating data from both Carriers and Shippers to deliver seamless end-to-end logistics service.

Shippers book shipments on the DigiHaul platform, detailing the scheduled collection and delivery time windows / locations and required vehicle types for carriers to consider. Once a carrier accepts a job and collection is scheduled, DigiHaul’s driver app facilitates real-time tracking of shipments through GPS signals, subject to carriers granting permissions for location logging.

This project aims to consolidate and integrate data from both Carriers and Shippers to deliver seamless end-to-end logistics service.

Using data-driven approach, this presentation aims to accommodate important KPIs and prediction of likeliness of on-time delivery detection using real-time GPS data from carriers.

## Requirements
pandas==1.4.4  
numpy==1.24.1  
matplotlib==3.3.4  
seaborn==0.12.2  
sklearn==1.3.2  
python==3.8.3

### Data Sources:
GPS Data: real-time carrier location

Shipment Bookings: details about each shipment accepted by a carrier

New Bookings: details about future shipments, same as shipment bookings but different time intervals

## Explanatory Data Analysis
Checking data types of all sources. Converting datetime columns to an appropriate dtype taking into account of BST.

Making sure each data is ready to analyse, no null values and duplicates.

## 1. Analysis of Late Deliveries
Operational teams rely heavily on KPIs like on-time collection and on-time delivery to gauge carrier performance. What percentage of shipments met the on-time delivery threshold (arriving no later than 30 minutes past the scheduled delivery window) between October 1st and December 31st, 2023? 

- Percentage of on-time shipment deliveries is found as 62.62%.
- Analysis was held using data between dates  October 1st and December 31st, 2023.
- Latest update on GPS locations were taken into account, as that indicates the latest update from the carrier.
- The distance between the carrier and the latest delivery location is calculated. Carriers within 50 meters of their last delivery point are considered to have arrived.

## 2. Analysis of Potential Late Deliveries 
Timely communication of potential delays is crucial for shippers. During the 3-month period from 1st Oct to 31st Dec 2023, which shipper(s) should be notified automatically regarding potential late delivery of which shipments, and at what times?

- Assuming the drivers’ speed are 30 mile/h on average:
- Detected if the carrier can deliver the parcel on time using the distance of their location to delivery point.
- If the last time of scheduled delivery time period is further than the current time added by the expected time carrier will drive, then the shipment will be delivered on time.
- Several potential deliveries were identified.
- It is advised to send a notification of expected late delivery to the carrier during their earliest delivery schedule.
- Doing this, the carrier is notified beforehand and have time to arrange their schedule to meet the delivery on-time.

## 3. Predict Future Delays
Predict the likelihood of delay for the list of shipments in “New_bookings.csv” dataset. 
- Shipment Bookings data is used as a training dataset, and New Bookings is used as test dataset to build a predictive model.
- A predictive model is build to understand the percentage of expected delays on the future bookings using historic data.
- The model predicted that the percentage of on-time deliveries is 67.4%.

