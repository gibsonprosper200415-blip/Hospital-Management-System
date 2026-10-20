# Hospital Management System 
UML Class Diagram Assignment

HOSPITAL MANAGEMENT SYSTEM
Report 1: Project Description Report
Item	Details
Institution	Kigali Independent University (ULK)
Assignment	UML Class Diagram Modelling Assignment
Instructor	Eric Maniraguha
Project Title	Hospital Management System
Group Members	1. John Prosper Gibson - Student ID: 202520487
2. Shem Yarway Monagar - Student ID: 202412174
Submission Date	20 October 2026
1. Project Title and Business Idea
Project Title: Hospital Management System (HMS)
Business Idea: A hospital needs an information system that brings its daily activities into one organised model: registering patients, booking appointments with doctors, recording consultations and medical records, issuing prescriptions and tracking medicine stock, admitting patients to wards and beds, and billing for services. This project designs that system as a UML class diagram. Building a working application is not required.
2. Problem Statement and Purpose of the Proposed System
Problem statement. Many hospitals still rely on paper files or separate spreadsheets. This causes recurring problems:
•	Patient records are lost, duplicated or hard to find when a patient returns.
•	Appointments are double-booked, which creates long queues and wasted doctor time.
•	Prescriptions are issued without checking medicine stock or expiry dates.
•	Staff cannot see in real time which beds and wards are free.
•	Invoices are calculated by hand, leading to billing errors and delayed payments.
•	Management cannot easily see how doctors, departments and wards are being used.
Purpose. The purpose of the proposed system is to model a single, consistent structure for hospital data and operations so that a future software team can build a reliable system from it. The model aims to:
•	keep one complete record per patient, linked to appointments, medical records, admissions and invoices;
•	organise staff by department and separate clinical roles (doctors, nurses) from general staff;
•	connect consultations to prescriptions and to the medicine stock held by the pharmacy;
•	manage wards, beds and admissions so that bed availability is always known;
•	support accurate billing for each patient.
3. Project Scope
3.1 Functions covered
Module	What the system will cover
Patient management	Register patients, store demographic and contact details, update profiles, view medical history.
Staff and departments	Store staff details; specialise doctors and nurses; assign staff to departments.
Appointments	Schedule, reschedule, cancel and confirm appointments between patients and doctors.
Medical records	Record symptoms, diagnosis and treatment notes for each consultation.
Prescriptions and pharmacy	Issue prescriptions with one or more medicine items; track medicine price, stock and expiry.
Wards, beds and admissions	Manage wards and beds; admit, transfer and discharge inpatients.
Billing	Generate invoices, calculate totals, record payment status and method, produce receipts.
3.2 Functions not covered
•	Laboratory, radiology and imaging management.
•	Insurance claims processing and government reporting.
•	Payroll, staff leave and shift-roster management.
•	Ambulance and emergency dispatch.
•	Telemedicine and online video consultation.
•	Integration with hardware such as barcode scanners or biometric devices.
•	Writing or deploying a working application (this project is design only).
3.3 Users and assumptions
Users: patients, doctors, nurses and administrative staff (receptionists, pharmacists, administrators). Administrative staff use the general Staff class; only doctors and nurses are specialised because they have clinical responsibilities in the model.
Assumptions: the system serves one hospital; every staff member belongs to exactly one department; each appointment involves one patient and one doctor; a medical record is created from one appointment; a bed holds one patient at a time; every invoice is issued to one patient.
4. Main Classes and Their Responsibilities
Class	Responsibility
Patient	Stores personal and medical-contact details of a person receiving care; registers, books appointments and views medical history.
Staff	Abstract parent class holding the details common to all hospital employees (receptionists, pharmacists, administrators, doctors, nurses).
Doctor	Staff member who attends appointments, diagnoses patients, writes medical records and prescribes medicine.
Nurse	Staff member who records vital signs, assists doctors and updates bed status.
Department	Organisational unit (e.g. Paediatrics, Surgery) that employs staff and manages wards.
Appointment	A scheduled consultation between one patient and one doctor; can be scheduled, rescheduled, cancelled or confirmed.
MedicalRecord	Clinical documentation of a consultation: symptoms, diagnosis and treatment notes.
Prescription	Document issued after a consultation that groups the medicines the doctor orders.
PrescriptionItem	One medicine line inside a prescription with quantity, dosage, frequency and duration.
Medicine	Pharmacy stock item with price, quantity in stock and expiry date.
Ward	Physical hospital area (e.g. Maternity Ward) with a type and capacity that contains beds.
Bed	Individual bed in a ward; tracks availability and is assigned to admitted patients.
Admission	Inpatient stay linking a patient to a bed with admission and discharge dates.
Invoice	Bill issued to a patient with total amount, payment status and payment method.
5. System Requirements
5.1 Functional requirements
ID	The system shall…
FR-01	register a patient and keep their personal details up to date.
FR-02	store staff details, specialise them as doctors or nurses, and assign each to a department.
FR-03	allow appointments to be scheduled, rescheduled, cancelled and confirmed, and prevent a doctor from being double-booked.
FR-04	let a doctor record symptoms, diagnosis and treatment notes in a medical record linked to the appointment.
FR-05	let a doctor issue a prescription containing one or more medicine items with dosage, frequency and duration.
FR-06	maintain medicine stock levels and expiry dates, and report when stock is unavailable or expired.
FR-07	manage wards and beds and show which beds are available.
FR-08	admit a patient to a bed, transfer the patient to another bed, and record discharge.
FR-09	generate an invoice for a patient, calculate the total, record payment and produce a receipt.
FR-10	retrieve the full medical history of a patient on request.
5.2 Non-functional requirements
•	Security and privacy: role-based access; medical records visible only to authorised staff.
•	Data integrity: unique identifiers for every record and mandatory fields for key data.
•	Performance: searching for a patient or appointment should take only a few seconds.
•	Reliability: regular backups and high availability during working hours.
•	Usability: simple screens that reception, nursing and pharmacy staff can learn quickly.
•	Maintainability: modular object-oriented design so that new modules can be added later.
5.3 Technical environment
The design is technology-independent. A future implementation would need client workstations, a network and a database server, and could use any object-oriented language with a relational database.
6. Conclusion
The Hospital Management System brings patients, staff, consultations, pharmacy, wards and billing into one clear structure. The classes and relationships are shown in the UML class diagram and explained in 





Report 2: UML Class Diagram Report

HOSPITAL MANAGEMENT SYSTEM

1. Introduction
This report presents the UML class diagram of the Hospital Management System. It lists the 14 classes with their attributes and methods, the 16 relationships between them with multiplicities, and a short explanation of each relationship type. The project scope and requirements are in Report 1.
2. The UML Class Diagram
The complete diagram is shown on the next page. It is also available as uml_class_diagram.png (full resolution) and as the editable uml_class_diagram.drawio file.
 

 
3. Classes, Attributes and Methods
Visibility: + public, - private. Attributes are private; methods are public.
Class	Attributes	Methods
Patient	- patientId: String
- fullName: String
- dateOfBirth: Date
- gender: String
- phone: String
- address: String
- bloodGroup: String	+ register(): void
+ updateProfile(): void
+ bookAppointment(): void
+ viewMedicalHistory(): List
Staff (abstract)	- staffId: String
- fullName: String
- gender: String
- phone: String
- email: String
- hireDate: Date	+ getDetails(): String
+ updateContact(): void
Doctor	- specialization: String
- licenseNumber: String
- consultationFee: double	+ viewSchedule(): List
+ diagnosePatient(): void
+ prescribeMedicine(): void
+ updateMedicalRecord(): void
Nurse	- shift: String
- qualification: String	+ recordVitalSigns(): void
+ assistDoctor(): void
+ updateBedStatus(): void
Department	- departmentId: String
- departmentName: String
- location: String
- phone: String	+ addStaff(): void
+ removeStaff(): void
+ getStaffList(): List
Appointment	- appointmentId: String
- appointmentDate: Date
- appointmentTime: Time
- reason: String
- status: String	+ schedule(): void
+ reschedule(): void
+ cancel(): void
+ confirm(): void
MedicalRecord	- recordId: String
- recordDate: Date
- symptoms: String
- diagnosis: String
- treatmentNotes: String	+ addRecord(): void
+ updateRecord(): void
+ viewRecord(): String
Prescription	- prescriptionId: String
- issueDate: Date
- instructions: String	+ generate(): void
+ viewPrescription(): String
+ printPrescription(): void
PrescriptionItem	- itemId: String
- quantity: int
- dosage: String
- frequency: String
- durationDays: int	+ calculateCost(): double
Medicine	- medicineId: String
- medicineName: String
- category: String
- unitPrice: double
- stockQuantity: int
- expiryDate: Date	+ updateStock(): void
+ checkAvailability(): boolean
+ isExpired(): boolean
Ward	- wardId: String
- wardName: String
- wardType: String
- capacity: int	+ checkAvailability(): boolean
+ addBed(): void
+ getOccupancy(): int
Bed	- bedId: String
- bedNumber: String
- status: String	+ assignBed(): void
+ releaseBed(): void
+ isAvailable(): boolean
Admission	- admissionId: String
- admissionDate: Date
- dischargeDate: Date
- reason: String
- status: String	+ admitPatient(): void
+ transferBed(): void
+ dischargePatient(): void
Invoice	- invoiceId: String
- issueDate: Date
- totalAmount: double
- paymentStatus: String
- paymentMethod: String	+ generateInvoice(): void
+ calculateTotal(): double
+ recordPayment(): void
+ generateReceipt(): String
4. Relationships and Multiplicities
#	Class A	Type	Class B	Mult. at A	Mult. at B	Meaning
1	Ward	Aggregation	Department	0..*	1	A department manages zero or more wards; each ward belongs to exactly one department.
2	Staff	Aggregation	Department	1..*	1	A department employs one or more staff members; each staff member works in exactly one department.
3	Nurse	Generalization	Staff	-	-	A Nurse is a kind of Staff and inherits all Staff attributes and methods.
4	Doctor	Generalization	Staff	-	-	A Doctor is a kind of Staff and inherits all Staff attributes and methods.
5	Bed	Composition	Ward	1..*	1	A ward contains one or more beds; a bed cannot exist without its ward.
6	Bed	Association	Admission	1	0..*	A bed can be used in many admissions over time; each admission uses exactly one bed.
7	Patient	Association	Admission	1	0..*	A patient may undergo zero or more admissions; each admission is for exactly one patient.
8	Patient	Association	Appointment	1	0..*	A patient may book zero or more appointments; each appointment is for exactly one patient.
9	Doctor	Association	Appointment	1	0..*	A doctor may attend zero or more appointments; each appointment is with exactly one doctor.
10	Appointment	Association	MedicalRecord	1	0..1	An appointment results in zero or one medical record (none if the patient does not attend); each record comes from exactly one appointment.
11	Doctor	Association	MedicalRecord	1	0..*	A doctor may write zero or more medical records; each record is written by exactly one doctor.
12	Patient	Association	MedicalRecord	1	0..*	A patient has zero or more medical records; each record belongs to exactly one patient.
13	MedicalRecord	Association	Prescription	1	0..*	A medical record may lead to zero or more prescriptions; each prescription is based on exactly one record.
14	PrescriptionItem	Composition	Prescription	1..*	1	A prescription contains one or more items; an item cannot exist without its prescription.
15	PrescriptionItem	Association	Medicine	0..*	1	An item refers to exactly one medicine; a medicine may appear in zero or more prescription items.
16	Patient	Association	Invoice	1	0..*	A patient may be billed through zero or more invoices; each invoice is issued to exactly one patient.
For aggregation and composition, Class B is the whole (the diamond is drawn next to it). For generalization, Class B is the parent class (the triangle points to it). Multiplicity at A is the number of A objects linked to one B object, and vice versa.
5. Explanation of the Relationships
Generalization (Doctor, Nurse to Staff). Doctors and nurses share the same personal and employment details, so those are stored once in the abstract class Staff. Doctor and Nurse add only what is special to them, such as specialization and shift. Receptionists, pharmacists and administrators use Staff directly.
Composition (Ward-Bed, Prescription-PrescriptionItem). These are strong whole-part relationships: a bed has no meaning without its ward, and a prescription item has no meaning without its prescription. If the whole is deleted, its parts are deleted too.
Aggregation (Department-Ward, Department-Staff). A department groups wards and staff, but they can exist on their own: a staff member can be moved to another department and a ward can be reassigned. The parts therefore survive if the whole changes.
Associations. The remaining relationships connect independent objects. The care pathway runs Patient, Appointment, MedicalRecord, Prescription, PrescriptionItem, Medicine. A Doctor takes part in appointments and writes records. Admissions link a Patient to a Bed, and Invoices link billing to the Patient.
Multiplicity choices. “1” is used where an object cannot exist without its partner (an appointment always has one patient and one doctor). “0..” is used where the link is optional and unlimited (a new patient has no appointments yet). ”1..” is used where at least one is required (a prescription needs at least one item; a department needs at least one staff member). “0..1” is used for the record of an appointment, because a missed appointment produces no record.
Why Prescription and PrescriptionItem are separate. A prescription can contain several medicines, and a medicine appears in many prescriptions. This many-to-many relationship is resolved by PrescriptionItem, which also stores the quantity, dosage, frequency and duration for each medicine.
6. Conclusion
The model has 14 classes and 16 relationships. It covers patients, staff, appointments, medical records, prescriptions, pharmacy stock, wards, beds, admissions and billing, and is ready to be turned into a database design or application.

