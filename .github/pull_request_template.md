## Description
Ticket – ['<Ticket>'](<Ticket Link>)
Documentation – ['Link'](<Documentation Link>)
<Brief Description>

### Scope
- [ ] New Workflow(s)
- [ ] New Notebook(s)
- [ ] Changes to Existing Workflow(s)
- [ ] Changes to Existing Notebook(s)
- [ ] New Catalog and Schema

---

## Evidence
Attach screenshots of successful executions.

## Validation / UAT
Evidence ensuring data accuracy and formal approval (User Acceptance Testing).

## Dependencies
* **Azure Data Factory Pipeline:** <ADF Pipeline Name, if applicable>
* **Data Factory PR:** ['<Data Factory PR Number>'](<Data Factory PR Link>)

## Production Environment (Optional)
Required actions in the Production environment to ensure the process executes correctly.

---

### Checklist
- [ ] **Coding Standards:** The workflow and its notebooks follow the project-defined standards.
- [ ] **Comments:** The code is well-commented, especially for complex logic.
- [ ] **Code Structure:** The code is organized clearly and logically, facilitating maintenance and understanding for other Data Engineers.
- [ ] **Standard Methods:** The code utilizes the standard writing methods for the data layers (e.g., `write_bronze`, `write_silver`, and `write_gold`).