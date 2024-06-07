# Surgical Department Database Application

## Overview

This database application is designed to manage the records and operations of a surgical department. It offers functionality to add and delete patients, surgeons, appointments, and operations, ensuring data integrity and consistency across the system. The application also handles key error cases to maintain the integrity of the database.

## Features

### Patient Management
- **Add Patient**
  - Attributes: `patient_id`, `first_name`, `last_name`, `birth_date`, `gender`, `address`, `phone`
- **Delete Patient**
  - Allows deletion of patient records based on `patient_id`.

### Surgeon Management
- **Add Surgeon**
  - Attributes: `surgeon_id`, `first_name`, `last_name`, `birth_date`, `gender`, `address`, `phone`, `email`
- **Delete Surgeon**
  - Allows deletion of surgeon records based on `surgeon_id`.

### Appointment Management
- **Add Appointment**
  - Attributes: `appointment_id`, `patient_id`, `surgeon_id`, `operation_id`, `appointments_date`, `operationroom_id`
- **Delete Appointment**
  - Allows deletion of appointment records based on `appointment_id`.

### Operation Management
- **Add Operation**
  - Attributes: `operation_id`, `operation`, `description`, `cost`

## Error Handling

1. **Unique IDs**
   - Error message raised if two patients, surgeons, or operations with the same ID are entered to ensure each ID is unique.
   
2. **Appointment Conflicts**
   - Error message raised if attempting to enter two appointments at the same time for the same surgeon, patient, or operation room to avoid scheduling conflicts.
   
3. **Foreign Key Integrity**
   - Error message raised if attempting to enter an appointment with a non-existent `surgeon_id`, `patient_id`, `operation_id`, or `operationroom_id` to ensure all referenced entities exist.
   
4. **Cascade Deletion of Appointments**
   - Deleting an appointment for a surgeon will also update the database to delete the corresponding appointment for the patient and vice versa, ensuring the integrity of the appointment records.

## Usage

### Adding a Patient
To add a new patient:
```
INSERT INTO patients (patient_id, first_name, last_name, birth_date, gender, address, phone)
VALUES (...);
```

### Deleting a Patient
To delete a patient:
```
DELETE FROM patients WHERE patient_id = ...;
```

### Adding a Surgeon
To add a new surgeon:
```
INSERT INTO surgeons (surgeon_id, first_name, last_name, birth_date, gender, address, phone, email)
VALUES (...);
```

### Deleting a Surgeon
To delete a surgeon:
```
DELETE FROM surgeons WHERE surgeon_id = ...;
```

### Adding an Appointment
To add a new appointment:
```
INSERT INTO appointments (appointment_id, patient_id, surgeon_id, operation_id, appointments_date, operationroom_id)
VALUES (...);
```

### Deleting an Appointment
To delete an appointment:
```
DELETE FROM appointments WHERE appointment_id = ...;
```

### Adding an Operation
To add a new operation:
```
INSERT INTO operations (operation_id, operation, description, cost)
VALUES (...);
```

## Error Cases
- **Duplicate IDs**: Ensure unique IDs for patients, surgeons, and operations.
- **Scheduling Conflicts**: Avoid overlapping appointments for patients, surgeons, and operation rooms.
- **Foreign Key Validation**: Validate existence of referenced `surgeon_id`, `patient_id`, `operation_id`, and `operationroom_id` before adding an appointment.
- **Cascade Deletion**: Deleting an appointment for a surgeon or patient will also delete the corresponding records to maintain database consistency.

## Conclusion
This application provides a robust solution for managing the records and operations of a surgical department, ensuring data integrity and handling critical error cases effectively.
