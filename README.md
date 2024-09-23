# pshenmic-dev-dfo

The homepage of the pshenmic.dev DFO source files.

## Data Contract Structure

This project includes three key documents in the data contract schema: **Project**, **Tasks**, and **Claim**. Below is a detailed description of each.

### Project Document

The `Project` document defines the structure for storing project information.

- **name** (string, required):  
  - Position: 0  
  - Description: The name of the project.  
  - Maximum Length: 63 characters.
  
- **description** (string, required):  
  - Position: 1  
  - Description: A detailed description of the project.  
  - Maximum Length: 1000 characters.
  
- **url** (string, required):  
  - Position: 2  
  - Description: The URL associated with the project.  
  - Maximum Length: 255 characters.

#### Required Fields
- `name`
- `description`
- `url`
- `$createdAt`
- `$updatedAt`

Additional properties are not allowed.

---

### Tasks Document

The `Tasks` document is used to define individual tasks within a project.

- **title** (string, required):  
  - Position: 0  
  - Description: The title of the task.  
  - Maximum Length: 63 characters.
  
- **description** (string, optional):  
  - Position: 1  
  - Description: A detailed description of the task.  
  - Maximum Length: 1000 characters.
  
- **url** (string, optional):  
  - Position: 2  
  - Description: A URL with further details about the task.  
  - Maximum Length: 255 characters.
  
- **assignee** (array, optional):  
  - Position: 3  
  - Description: The identity of the assignee who will execute the task.  
  - Byte Array: true  
  - Length: 32 bytes.
  
- **projectId** (array, required):  
  - Position: 4  
  - Description: The ID of the project to which this task belongs.  
  - Byte Array: true  
  - Length: 32 bytes.
  
- **status** (string, required):  
  - Position: 5  
  - Description: The status of the task.  
  - Enum: `pending`, `in_progress`, `completed`, `will_not_implement`, `paid`.

- **comment** (string, optional):  
  - Position: 6  
  - Description: A comment on the status change of the task.  
  - Maximum Length: 1000 characters.

#### Required Fields
- `title`
- `projectId`
- `status`
- `$createdAt`
- `$updatedAt`

Additional properties are not allowed.

---

### Claim Document

The `Claim` document records claims for work done on tasks.

- **taskId** (array, required):  
  - Position: 0  
  - Description: The ID of the task for which the claim is being made.  
  - Byte Array: true  
  - Length: 32 bytes.
  
- **amountCredits** (number, required):  
  - Position: 1  
  - Description: The amount of credits being claimed.
  
- **amountUSD** (number, required):  
  - Position: 2  
  - Description: The equivalent amount in USD being claimed.
  
- **deliverable** (string, required):  
  - Position: 3  
  - Description: Link to the deliverable for the claim.  
  - Maximum Length: 255 characters.

#### Required Fields
- `taskId`
- `amountCredits`
- `amountUSD`
- `deliverable`
- `$createdAt`
- `$updatedAt`

Additional properties are not allowed.

---

### Common Fields

In all documents, the following fields are automatically managed:

- **$createdAt**: Timestamp of when the document was created.
- **$updatedAt**: Timestamp of the last update to the document.

These fields ensure proper tracking of document lifecycle events.

---

This schema ensures that all data related to projects, tasks, and claims is properly structured and validated before being stored on the Dash Platform.