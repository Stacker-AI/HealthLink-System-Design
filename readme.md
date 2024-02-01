# System Design (FYP)

# 
## What is HealthLink?
A platform facilitating communication between doctors and patients, wherein their interactions are transcribed and processed by an advanced Language Model (LLM). The generated results are then provided to both the doctor and the patient, enhancing the quality of their question-and-answer sessions, enabling more thorough analysis, and aiding in the retention of pertinent medical history. This innovative solution aims to streamline healthcare communication, fostering improved understanding and collaboration between healthcare professionals and their patients.

# Requirements
Our system should meet the following requirements:

### Enhanced Functional Requirements

**Patient:**
   - Patients should easily locate and connect with suitable doctors based on specialization, location, and availability.
   - Seamless payment integration to facilitate secure and convenient transactions for medical services.
   - Patients should have the capability to schedule, reschedule, or cancel appointments with their chosen healthcare provider.
   - Enable patients to engage in comprehensive consultations through video, audio, and chat functionalities.
   - Empower patients to efficiently manage their health information by adding, updating, or deleting clinical records.
   - Allow patients to book necessary laboratory tests and receive timely results through the platform.
   - Provide a platform for patients to conveniently purchase prescribed medicines with integrated delivery options.

**Doctor:**
   - Doctors should have a comprehensive view of past and upcoming patient appointments, enabling effective time management.
   - Facilitate the withdrawal of earnings securely and efficiently for healthcare services provided.
   - Grant doctors the authority to accept or reject appointment requests based on their availability.
   - Empower doctors to prescribe lab tests and medications, tracking patient adherence and progress.
   - Provide doctors with instant access to patients' historical clinical records for informed decision-making.

### Non-Functional Requirements
   - Ensure the system's dependability and consistency to foster trust among users.
   - Guarantee the system's continuous accessibility, minimizing delays to provide real-time interactions.
   - Design the system to scale effortlessly, accommodating a growing user base while maintaining optimal performance.

### Extended Requirements
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




# API Design

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
- Endpoint: `/api/search/doctors/`  
- Through this API, patients will be able to search a doctor.
  
**Parameters**
- city: Delhi
- q: Dentist
- page: 2
  
**Returns**

```json
{
    "doctors": [
        {
            "id": 7347,
            "profile_photo_url": "https://images1-fabric.practo.com/",
            "doctor_name": "Dr. Janak Raj Sabharwal",
            "specialization": "Dentist",
            "experience_years": 43,
            "city": "Vikas Puri",
            "available_days": ["MONDAY", "TUESDAY"],
            "consultation_fees": 1000,
            "wait_time": 15,
            "reviews_count": 86
        }
    ]
}
```

---

### View Doctor
- Endpoint: `/api/view/doctor/`  
- Through this API, patients will be able to view detailed information about a specific doctor.
  
**Parameters**
- id: 7347
  
**Returns**

```json
{
    "doctor": {
        "id": 7347,
        "profile_photo_url": "https://images1-fabric.practo.com/",
        "doctor_name": "Dr. Janak Raj Sabharwal",
        "specialization": "Dentist",
        "qualifications": "MBBS",
        "experience_years": 43,
        "city": "Vikas Puri",
        "available_timings": "20:00",
        "available_days": ["MONDAY", "TUESDAY"],
        "consultation_fees": 1000,
        "summary": "He completed BDS Degree in 1981",
        "wait_time": 15,
        "recommendation_percent": 96,
        "patients_count": 390,
        "reviews_count": 86
    }
}
```

---

### Book Appointment
- Endpoint: `/api/book/appointment/`  
- Through this API, patients can book an appointment with a specific doctor.
  
**Parameters**
- doctor_id: 7347
- appointment_date: "2024-02-15"
- appointment_time: "10:30 AM"
- patient_name: "John Doe"
- patient_email: "john.doe@example.com"
  
**Returns**

```json
{
    "appointment": {
        "id": 12345,
        "doctor_id": 7347,
        "patient_name": "John Doe",
        "appointment_date": "2024-02-15",
        "appointment_time": "10:30 AM",
        "status": "confirmed"
    }
}
```

---

### Cancel Appointment
- Endpoint: `/api/cancel/appointment/`  
- Through this API, patients can cancel a previously booked appointment.
  
**Parameters**
- appointment_id: 12345
  
**Returns**

```json
{
    "status": "cancelled",
    "message": "Appointment successfully cancelled."
}
```

---

### Patient Records
- Endpoint: `/api/patient/records/`  
- Through this API, patients can retrieve and manage their clinical records.
  
**Parameters**
- patient_id: 9876
  
**Returns**

```json
{
    "records": [
        {
            "record_id": 1,
            "date": "2024-01-15",
            "description": "Routine Checkup",
            "prescription": "Paracetamol 500mg, Rest"
        },
        {
            "record_id": 2,
            "date": "2024-02-01",
            "description": "Follow-up",
            "prescription": "Antibiotics, Painkillers"
        }
    ]
}
```

---

### Lab Test Booking
- Endpoint: `/api/book/labtest/`  
- Through this API, patients can book laboratory tests.
  
**Parameters**
- patient_id: 9876
- test_name: "Blood Test"
- appointment_date: "2024-02-10"
  
**Returns**

```json
{
    "lab_test_booking": {
        "booking_id": 54321,
        "patient_id": 9876,
        "test_name": "Blood Test",
        "appointment_date": "2024-02-10",
        "status": "scheduled"
    }
}
```

---

### Medicine Purchase
- Endpoint: `/api/purchase/medicine/`  
- Through this API, patients can purchase prescribed medicines.
  
**Parameters**
- patient_id: 9876
- medicine_name: "Paracetamol"
- quantity: 2
  
**Returns**

```json
{
    "medicine_purchase": {
        "purchase_id": 987654,
        "patient_id": 9876,
        "medicine_name": "Paracetamol",
        "quantity": 2,
        "total_cost": 10.00,
        "delivery_status": "pending"
    }
}
```

---

### Doctor Earnings
- Endpoint: `/api/doctor/earnings/`  
- Through this API, doctors can view their earnings.
  
**Parameters**
- doctor_id: 7347
  
**Returns**

```json
{
    "earnings": {
        "doctor_id": 7347,
        "total_earnings": 5000.00,
        "withdrawable_amount": 4500.00
    }
}
```

---

### Withdraw Earnings
- Endpoint: `/api/withdraw/earnings/`  
- Through this API, doctors can withdraw their earnings.
  
**Parameters**
- doctor_id: 7347
- amount: 2000.00
  
**Returns**

```json
{
    "status": "success",
    "message": "Earnings withdrawal successful. Amount: 2000.00"
}
```
