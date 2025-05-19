# Experiment 1: Entity-Relationship (ER) Diagram

## 🎯 Objective:
To understand and apply the concepts of ER modeling by creating an ER diagram for a real-world application.

## 📚 Purpose:
The purpose of this workshop is to gain hands-on experience in designing ER diagrams that visually represent the structure of a database including entities, relationships, attributes, and constraints.

---

## 🧪 Choose One Scenario:

### 🔹 Scenario 1: University Database
Design a database to manage students, instructors, programs, courses, and student enrollments. Include prerequisites for courses.

**User Requirements:**
- Academic programs grouped under departments.
- Students have admission number, name, DOB, contact info.
- Instructors with staff number, contact info, etc.
- Courses have number, name, credits.
- Track course enrollments by students and enrollment date.
- Add support for prerequisites (some courses require others).

---

### 🔹 Scenario 2: Hospital Database
Design a database for patient management, appointments, medical records, and billing.

**User Requirements:**
- Patient details including contact and insurance.
- Doctors and their departments, contact info, specialization.
- Appointments with reason, time, patient-doctor link.
- Medical records with treatments, diagnosis, test results.
- Billing and payment details for each appointment.

---

## 📝 Tasks:
1. Identify entities, relationships, and attributes.
2. Draw the ER diagram using any tool (draw.io, dbdiagram.io, hand-drawn and scanned).
3. Include:
   - Cardinality & participation constraints
   - Prerequisites for University OR Billing for Hospital
4. Explain:
   - Why you chose the entities and relationships.
   - How you modeled prerequisites or billing.

# ER Diagram Submission - MANOJ M

## Scenario Chosen:
University / Hospital (choose one)

## ER Diagram:
![image](https://github.com/user-attachments/assets/d11813bc-51e0-4fae-a94f-ed54533279ea)


## Entities and Attributes:

Patient:

• Stores essential patient details such as ID, Name, Gender, Phone Number, and Address.

• Assumed that Age can be derived from Date of Birth, making it an optional attribute.

Doctor:

• Identified by a unique Doctor_ID.

• Includes Name, Specialization, Experience, and Contact Details.

• Assumed that each doctor belongs to one department.

Department:

• Departments like Cardiology, Pediatrics, and Oncology are included.

• Each doctor belongs to one department, but a department can have multiple doctors.

Appointment:

• Links a Patient and a Doctor.

• Contains Appointment_ID, Date & Time, and Appointment Number.

• Assumption: A patient can have multiple appointments with different or the same doctor.

Record:

• Stores patient medical records such as Treatment, Description, and Record_ID.

• Each record is linked to a specific patient and doctor.

Admission:

• Captures hospital admission details, including Date & Time.

• Links to a specific Patient_ID.

Bill:

• Stores billing details such as Bill_ID, Payment Status, Date, and Amount.

• Assumption: Each patient has multiple bills, tied to hospital services or treatments.



## Relationships and Constraints:

Patient - Appointment (1:M):

• A patient can have multiple appointments but each appointment is linked to only one patient.

Doctor - Appointment (1:M):

• A doctor can attend multiple appointments, but each appointment is with one doctor.

Patient - Record (1:M):

• A patient can have multiple medical records, but each record is linked to only one patient.

Doctor - Record (1:M):

• A doctor can handle multiple records, but each record is associated with only one doctor.

Doctor - Department (M:1):

• A doctor belongs to one department, while a department can have many doctors.

Patient - Admission (1:M):

• A patient can be admitted multiple times but each admission is for one patient.

Patient - Bill (1:M):

• A patient can have multiple bills related to different treatments or stays.

Billing & Payment Concept:

• The Bill entity tracks financial transactions.

• Each bill has a Payment Status (Paid, Pending, or Unpaid).

• Billing is linked to a Patient, assuming that treatments and services will be reflected in their records.

## Extension (Prerequisite / Billing):

## Prerequisite:

In the hospital database diagram, prerequisites are handled implicitly through relationship constraints. For example, a patient must first be admitted before any record is created, which is enforced through the one-to-one ("Has") relationship between Patient and Record. Similarly, a doctor must belong to at least one department, indicated by the many-to-one ("Can Have") relationship between Doctor and Departments. Instead of explicitly modeling prerequisites, the design uses cardinality and relationship rules to ensure logical data flow and integrity.
## Billing

Billing is modeled explicitly through a dedicated Bill entity. This entity includes attributes like Bill_ID, Payment Status, Amount, and Date. A Patient can have multiple Bills, represented through a many-to-one (M:1) relationship between Patient and Bill. This setup allows the system to track all billing transactions associated with each patient, supporting detailed financial records and multiple payments over time.
## Design Choices:

The entities, relationships, and assumptions were selected to accurately represent the operations of a hospital management system. Entities like Patient, Doctor, Department, Appointment, Record, Admission, and Bill were chosen to cover patient care, doctor management, and financial processes. Relationships were carefully designed to reflect real-world interactions, such as a patient attending multiple appointments or a doctor belonging to a department. Assumptions, such as deriving Age from Date of Birth and allowing multiple bills per patient, were made to streamline the model while maintaining flexibility and completeness.

## RESULT
Thus the concepts of ER modeling by creating an ER diagram for a Hospital Management is successfully created.
