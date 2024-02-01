# System Design (FYP)

# 
## What is HealthLink?
A platform facilitating communication between doctors and patients, wherein their interactions are transcribed and processed by an advanced Language Model (LLM). The generated results are then provided to both the doctor and the patient, enhancing the quality of their question-and-answer sessions, enabling more thorough analysis, and aiding in the retention of pertinent medical history. This innovative solution aims to streamline healthcare communication, fostering improved understanding and collaboration between healthcare professionals and their patients.

# Requirements
Our system should meet the following requirements:

### Enhanced Functional Requirements

**Patient:**

1. **Doctor Discovery:**
   - Patients should easily locate and connect with suitable doctors based on specialization, location, and availability.

2. **Payment Processing:**
   - Seamless payment integration to facilitate secure and convenient transactions for medical services.

3. **Appointment Booking:**
   - Patients should have the capability to schedule, reschedule, or cancel appointments with their chosen healthcare provider.

4. **Communication Features:**
   - Enable patients to engage in comprehensive consultations through video, audio, and chat functionalities.

5. **Clinical Records Management:**
   - Empower patients to efficiently manage their health information by adding, updating, or deleting clinical records.

6. **Lab Test Booking:**
   - Allow patients to book necessary laboratory tests and receive timely results through the platform.

7. **Medicine Purchases:**
   - Provide a platform for patients to conveniently purchase prescribed medicines with integrated delivery options.

**Doctor:**

1. **Patient Management:**
   - Doctors should have a comprehensive view of past and upcoming patient appointments, enabling effective time management.

2. **Financial Transactions:**
   - Facilitate the withdrawal of earnings securely and efficiently for healthcare services provided.

3. **Appointment Control:**
   - Grant doctors the authority to accept or reject appointment requests based on their availability.

4. **Prescription Management:**
   - Empower doctors to prescribe lab tests and medications, tracking patient adherence and progress.

5. **Access to Clinical Records:**
   - Provide doctors with instant access to patients' historical clinical records for informed decision-making.

### Non-Functional Requirements

1. **High Reliability:**
   - Ensure the system's dependability and consistency to foster trust among users.

2. **High Availability with Minimal Latency:**
   - Guarantee the system's continuous accessibility, minimizing delays to provide real-time interactions.

3. **Scalability and Efficiency:**
   - Design the system to scale effortlessly, accommodating a growing user base while maintaining optimal performance.

### Extended Requirements

- **Metrics and Analytics:**
  - Implement robust tracking mechanisms and analytics tools to gather insights into system usage, user satisfaction, and overall performance. This data can be used for continuous improvement and strategic decision-making.


# High level requirements desgn


![Low Level/1.png](https://github.com/Stacker-AI/HealthLink-System-Design/blob/main/High%20Level/1.png)

# Low level requirement design (Microservices)


![Low Level/1.png](https://github.com/Stacker-AI/HealthLink-System-Design/blob/main/Low%20Level/1.png)

![Low Level/1.png](https://github.com/Stacker-AI/HealthLink-System-Design/blob/main/Low%20Level/2.png)

![Low Level/1.png](https://github.com/Stacker-AI/HealthLink-System-Design/blob/main/Low%20Level/3.png)

![Low Level/1.png](https://github.com/Stacker-AI/HealthLink-System-Design/blob/main/Low%20Level/4.png)

![Low Level/1.png](https://github.com/Stacker-AI/HealthLink-System-Design/blob/main/Low%20Level/5.png)

![Low Level/1.png](https://github.com/Stacker-AI/HealthLink-System-Design/blob/main/Low%20Level/6.png)





# Data model design
ERD Models for the HealthLink.

![Low Level/1.png](https://github.com/Stacker-AI/HealthLink-System-Design/blob/main/ERD.png)



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


