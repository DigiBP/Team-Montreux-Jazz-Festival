# Team-Montreux-Jazz-Festival
# DigiBP_ClinicalPathway

Telemedicine pathway

Introduction 

Nowadays, a continuous increase in healthcare burden across several countries is being seen which might present a serious difficulty towards the sustained provision and enhancement of patients health. By these means, the first major load comes when someone wants to confirm an appointment with their doctor, and continuos waiting times and delays are also observed, which might end up causing patient disconfort (the payers). Several times the presenciality in the clinical consult room is not required which might indicate the help that telemedicine technologies could serve to the general public. Telemedicine is the practice of medicine using technology to deliver care at a distance using telecommunications infrastructure between a patient at one side and a physician or other licensed practioner at other site. However, making the doctor to decide which consults to take presently and which remotely might be time-consuming and subject to inter-phisician  differneces. 

Project goal 

To design a fully-automated workflow where the patient fills a survey and the presence/remote decision is made and the present/digital room are reserved and sent via mail to the patient which then has the capability to choose the available consult day and hour. Moreover, the appointment is saved in doctor's and patient's agenda. 
 
Tools:

For process automation download camunda BPMN/DMN modeler  
https://camunda.com/download/modeler/
To build, create and automate workflows download
https://www.make.com/en
 Google Spreadsheet
 Google Forms
 Calendly

 Camunda process description 
 
 ![Alt text](/BPMN.bmp)
 
 Make Process
 
  ![Alt text](/Make.bmp)
  
 Form Webpage 
 
  ![Alt text](/Webpage.bmp)
  
  Decision table:
  
  ![Alt text](/DMN.bmp)

 Workflow explanation
 
 1. The user submits his/her data on the form
 2. The patient data is saved in a Google Spreadsheet
 3. The make process takes the data from the last row of the Google spreadsheet
 4. An HTTP POST request start the business process and gives as input variable the data from the spreadsheet.
 5. A decision table is used to choose which type of consult (or even emergency) might be best suited for that concrete user. In the table the result is a number which represent to each category (3 - Remote, 2- Present, 1- Emergency). THe HIT policy is set at Collect (MIN) so that if two or more rows are fulfilled only the more little number is chosen (As lower the number, greater clinical gravity).  
 6. The next task (Service Task) fetch and locks the Make process through another HTTP request which sends the output of the deccision table to the Make process.
 7. The Make process chooses the route depending of the output of the decision table.
 8. If the consult is remote or present a Calendly module is instantaniated and redirect the user to calendly webpage where he/she can choose the day and hour of the appointment that are currently available in the doctor's agenda. 
 9. After choosing the suited hour and day of the consult the patient receives an email with the present room (present) or a google meet session invitation (remote). Moreover, the consult is saved in both patient's and doctor's Google calendar. 
 Emergency. If the output is an emergency an email is claiming the urgent of the signs the user is presenting and that he/she might call 112.
  
 
 
 Authors and acknowledgement
 
1. Marc Molina Van den Bosch 
2. Caterina Montalbano
3. Dibya kumari
4. Marco de Luca 

Responsibilities

 1. Marc Molina Van den Bosch(Modelling, Integration)
 2. Marco the Luca (Modelling and Presentation)
 3. Caterina Montalbano(Modelling and Integration)
 4. Dibya Kumari

Bibliography

[1] https://www.thedaviscommunity.org/2020/12/15/what-is-telehealth-and-when-should-i-use-it/#:~:text=So%2C%20telehealth%20services%20may%20be,Arthritis
 
