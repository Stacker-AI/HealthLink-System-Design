# System Design (FYP)

# 
## What is HealthLink?
A plateform where a Doctor and Patient can communicate with each other and theri communication will be transcribed and processes by a LLM model and the result will be given back to Doctor and Patient for helping them in Question/Answer, better analysis and remebering previous history.

# Requirements
Our system should meet the following requirements:

### Functional requirements
We will design our system for two types of users: Doctor and Patient.

Patient

- Patient should be able to find the doctor
- Patient should be able to make payment.
- Patient should be able to book appointments.
- Patient should be able to make Video and Audio along with Chat option.
- Patient should be able to add/update/delete clinical records.
- Patient should be able to book lab tests.
- Patient should be able to buy medicines.
Doctor

- Doctor should be able to see past and incoming patients.
- Doctor should be able to withdraw money.
- Doctor should be able to accept/reject apointments.
- Doctor should be able to assign lab tests and medicines to patients.
- Doctor should be able to see patient's clinical records.
#### Non-Functional requirements
- High reliability.
- High availability with minimal latency.
- The system should be scalable and efficient.
#### Extended requirements
- Metrics and analytics.


# High level requirements desgn


![1.png]("/Low Level/1.png")



# Low level requirement design (Microservices)


![diagram-export-2-1-2024-5_34_51-PM.png](https://eraser.imgix.net/workspaces/bFh3OmlJ42dsrcGqhv1p/XCoQ2ksmpMfjUXTpurmNUsmSp3m2/LDdzRFAc_6jhzCZvO33j1.png?ixlib=js-3.7.0 "diagram-export-2-1-2024-5_34_51-PM.png")

![diagram-export-2-1-2024-5_35_03-PM.png](https://eraser.imgix.net/workspaces/bFh3OmlJ42dsrcGqhv1p/XCoQ2ksmpMfjUXTpurmNUsmSp3m2/iYsr7tFE3JjrlYIc3G6NU.png?ixlib=js-3.7.0 "diagram-export-2-1-2024-5_35_03-PM.png")

![diagram-export-2-1-2024-5_35_09-PM.png](https://eraser.imgix.net/workspaces/bFh3OmlJ42dsrcGqhv1p/XCoQ2ksmpMfjUXTpurmNUsmSp3m2/yzGuNEkMnGuRqfuDHNN3y.png?ixlib=js-3.7.0 "diagram-export-2-1-2024-5_35_09-PM.png")

![diagram-export-2-1-2024-5_35_16-PM.png](https://eraser.imgix.net/workspaces/bFh3OmlJ42dsrcGqhv1p/XCoQ2ksmpMfjUXTpurmNUsmSp3m2/JnBe0jRxS2uKL5nw3NqTz.png?ixlib=js-3.7.0 "diagram-export-2-1-2024-5_35_16-PM.png")

![diagram-export-2-1-2024-5_35_24-PM.png](https://eraser.imgix.net/workspaces/bFh3OmlJ42dsrcGqhv1p/XCoQ2ksmpMfjUXTpurmNUsmSp3m2/t8YRLo2igs-OuKYxGTa5S.png?ixlib=js-3.7.0 "diagram-export-2-1-2024-5_35_24-PM.png")

![diagram-export-2-1-2024-5_35_32-PM.png](https://eraser.imgix.net/workspaces/bFh3OmlJ42dsrcGqhv1p/XCoQ2ksmpMfjUXTpurmNUsmSp3m2/Qumc4h2-bMGRNO4LAGLf2.png?ixlib=js-3.7.0 "diagram-export-2-1-2024-5_35_32-PM.png")





# Data model design
ERD Models for the HealthLink.

![image.png](https://eraser.imgix.net/workspaces/bFh3OmlJ42dsrcGqhv1p/XCoQ2ksmpMfjUXTpurmNUsmSp3m2/skWd9pVw_HHHufpgK050B.png?ixlib=js-3.7.0 "image.png")



# API design
### Search Suggestions
- Endpoint: `/api/top/suggestion.json`  
- Through this API, patients will be able to search a doctor.
**Parameters**

- city: Wah
**Returns**

```json
{
    "results": {
        "matches": [
            {
                "suggestion": "Dentist",
                "original": "Dentist",
                "display_name": "SPECIALITY",
                "category": "subspeciality",
                "type": "doctor"
            }
        ]
    }
}
```
---

### Search Doctors
- Endpoint: `/api/search/doctors/ `  
- Through this API, patients will be able to search a doctor.
**Parameters**

- city: Delhi
- q: Dentist
- page: 2
**Returns**

```json
{
    "doctors": {
        "id": 7347,
        "profile_photo_url": "https://images1-fabric.practo.com/",
        "doctor_name": "Dr. Janak Raj Sabharwal",
        "specialization": "Dentist",
        "experience_years": 43,
        "city": "Vikas Puri",
        "available_days": ["MONDAY", "TUESDAY",
],
        "consultation_fees": 1000,
        "wait_time": 15,
        "reviews_count": 86
    }
}
```
### View Doctor
- Endpoint: `/api/view/doctor/ `  
- Through this API, patients will be able to search a doctor.
**Parameters**

- id: 1
**Returns**

```json
{
    "doctors": {
        "id": 7347,
        "profile_photo_url": "https://images1-fabric.practo.com/",
        "doctor_name": "Dr. Janak Raj Sabharwal",
        "specialization": "Dentist",
        "qualifications": "MBBS",
        "experience_years": 43,
        "city": "Vikas Puri",
        "available_timings": "20:00",
        "available_days": ["MONDAY", "TUESDAY",
],
        "consultation_fees": 1000,
        "summary": "He completed BDS Degree in 1981",
        "wait_time": 15,
        "recommendation_percent": 96,
        "patients_count": 390,
        "reviews_count": 86
    }
}
```


