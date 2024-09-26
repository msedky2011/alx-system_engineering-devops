Postmortem Outage report for Vodafone Payments System

Issue Summary
Vodafone Payments System had a full outage on 12 September 2024 from 1:00 AM UTC to 1:45 AM UTC.
The outage caused a revenue delay of ~ 5,000 payment transaction with ~ 1 Mllion EGP.

Issue Timeline

1:00 AM Operation engineer noticed declining transaction count in the system monitoring tool
1:05 AM First Line support engineer checked the application logs for any errors.
1:20 First line support engineer could not find any logs.
1:25 Second line support engineer checked why logs are not written.
1:40 Database admin checked database performance and he found slowness in general.
1:43 Database admin took and an action and restarted the database.
1:45 Database return to work normally and also the application.


Root cause
Due to the high traffic of the application, the database queries clashed with each other on tables lock.
Restarting the database caused these session to reset.

Corrective and preventative measures 
* Enhancing locking to be row based instead of table based.
