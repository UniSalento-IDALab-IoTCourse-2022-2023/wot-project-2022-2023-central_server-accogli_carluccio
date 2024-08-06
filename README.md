# GROUND WORKERS LOCATION AND IDENTIFICATION SYSTEM

This project aims to develop a Proximity Warning System (PWS) using Bluetooth Low energy (BLE) technology in work contexts where mobile machinery and workers on the ground are present.\
\
The system can detect proximity situations between these subjects in real-time, notifying those concerned in case of danger. Additionally, it supports other types of alarms, including general communications and signaling when drivers are away from machinery.\
\
Furthermore, the system offers functionalities for the management of site resources, allows the definition of a daily configuration of active machines with their authorised drivers, and guarantees secure access to the proximity notifications. Thanks to the software and hardware solutions adopted, it is easily extendable and adaptable to specific needs. 
## Architecture
The system architecture is outlined below:

![alt text](images/image.png)

The developed components are:
* 🟡(this repo) <b>the central server </b> 
* the machinery controller board\
https://github.com/UniSalento-IDALab-IoTCourse-2022-2023/wot-project-2022-2023-controller_board-accogli_carluccio.git
* android application\
https://github.com/UniSalento-IDALab-IoTCourse-2022-2023/wot-project-2022-2023-app_android-accogli_carluccio.git
* frontend application\
https://github.com/UniSalento-IDALab-IoTCourse-2022-2023/wot-project-2022-2023-app_angular-accogli_carluccio.git

## THIS REPO: Central server
This component is the core of the architecture. It is a local server which contains a backend organised in microservices with independent MongoDB databases (<b>port 27017</b>) and a message broker to manage MQTT communications between the system components.\
The backend part consists of 3 microservices implementing the main functionalities:
- <b>AuthenticationMS on port 8080</b>, which handles authentication of actors and management of secure access to the machineries via BLE MAC Addresses;
- <b>SiteManagementMS on port 8081</b>, which manages site resources and the daily configuration of active machineries with their authorised operators;
- <b>AlarmsMS on port 8082</b>, which listens for MQTT alarms sent to machineries and allows their storage and subsequent processing of statistics.


## Usage
1. Clone the repository with:
```
git clone --recursive <URL_thisRepo>
```
2. Start the server:
```
docker-compose up
```

