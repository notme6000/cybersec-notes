# Need to Know and Least Privilege

## 1. Need to Know

- A user, system, or process is given access only to the information required to perfom its job and nothing more.

### Why Need-to-Know Exists

- Limits damage if an account is compromised
- Reduces insider threats
- Protects sensitive data
- Supports compliance and audits
    - ISO 27001
    - NIST SP 800-53
    - HIPPA

### How Need-to-Know is implemented

1. Access Control 
    - Role-Based Access Control ( RBAC )
    - Attribure-Based Access Control ( ABAC )

2. Data Classification
    - Public
    - Internal
    - Confidential
    - Restricted / Secret
3. Segmentation
    - Network Segmentation
    - Database separation
    - File system permissions

### Example ( Real-World )

- HR employee :
    - _Access_ : employee records
    - _No Access_ : financial systems, source code
- IT admin :
    - _Access_ : System configuration
    - _No Access_ : payroll data 


## 2. Leat Privilege

- 



