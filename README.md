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
  
- **description** (string):  
  - Position: 1  
  - Description: A detailed description of the project.  
  - Maximum Length: 1000 characters.
  
- **url** (string):  
  - Position: 2  
  - Description: The URL associated with the project.  
  - Maximum Length: 255 characters.

#### Required Fields
- `name`
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
  
- **description** (string):  
  - Position: 1  
  - Description: A detailed description of the task.  
  - Maximum Length: 1000 characters.
  
- **url** (string):  
  - Position: 2  
  - Description: A URL with further details about the task.  
  - Maximum Length: 255 characters.
  
- **assignee** (array):  
  - Position: 3  
  - Description: The identity of the assignee who will execute the task.  
  - Byte Array: true  
  - Length: 32 bytes.
  
- **projectId** (string, required):  
  - Position: 4  
  - Description: The ID of the project to which this task belongs.  
  - Minimum Length: 43 characters.  
  - Maximum Length: 44 characters.

#### Required Fields
- `title`
- `projectId`
- `$createdAt`
- `$updatedAt`

Additional properties are not allowed.

---

### Claim Document

The `Claim` document records claims for work done on tasks.

- **taskId** (string, required):  
  - Position: 0  
  - Description: The ID of the task for which the claim is being made.  
  - Minimum Length: 43 characters.  
  - Maximum Length: 44 characters.
  
- **claimerIdentity** (array):  
  - Position: 1  
  - Description: The identity of the claimer.  
  - Byte Array: true  
  - Length: 32 bytes.
  
- **amountCoins** (number):  
  - Position: 2  
  - Description: The amount of coins being claimed.
  
- **amountUSD** (number):  
  - Position: 3  
  - Description: The amount of USD being claimed.

#### Required Fields
- `taskId`
- `$createdAt`
- `$updatedAt`

Additional properties are not allowed.

---

This schema ensures that all data related to projects, tasks, and claims is properly structured and validated before being stored on the Dash Platform.