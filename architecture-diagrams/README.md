## Architecture Diagrams

Architecture diagrams are maintained in architecture-diagrams/.

architecture-diagrams/
├── high-level-architecture.png
├── Secure_Attendance_DFD.png
└── trust-boundary-diagram.png

These diagrams illustrate component interactions:

' - User → API → Business Logic → Database flow

' - Sensitive data movement

' - Authentication and authorization checkpoints

### High-Level System Architecture

![Secure Attendance System Architecture](architecture-diagrams/high-level-architecture.png)

## Data Flows

| Flow ID | Source                 | Destination            | Data                   |
| ------- | ---------------------- | ---------------------- | ---------------------- |
| DF1     | Employee               | Attendance Device      | Biometric/Card Input   |
| DF2     | Attendance Device      | Attendance API         | Attendance Record      |
| DF3     | Attendance API         | Authentication Service | User Validation        |
| DF4     | Authentication Service | Attendance Engine      | Auth Result            |
| DF5     | Attendance Engine      | SQL Database           | Attendance Transaction |
| DF6     | Attendance API         | Audit Logging          | Security Events        |
| DF7     | HR/Admin Portal        | SQL Database           | Reports & Queries      |
| DF8     | HR/Admin Users         | HR/Admin Portal        | Management Requests    |

### Recommended Controls

- Multi-Factor Authentication (MFA) for HR/Admin users

- Role-Based Access Control (RBAC)

- Parameterized SQL Queries

- TLS 1.2+ Encryption

- Password Hashing (PBKDF2/Bcrypt)

- Audit Logging and Monitoring

- Database Encryption for Sensitive Data

- Login Rate Limiting

- Security Event Alerting
## Trust-boundary
### Security Risks Identified
#### Spoofing
- Shared user credentials
- Fake attendance device requests
#### Tampering
- Modification of attendance logs
- SQL Injection attacks
#### Repudiation
- Users denying attendance changes
#### Information Disclosure
- Exposure of employee personal information
#### Denial of Service
- Large volume of attendance submissions
#### Elevation of Privilege
- Employee gaining HR/Admin permissions
### This diagram highlights:

External Network boundary
Application Network boundary
Database Network boundary
Employee, Attendance Device, HR/Admin Users
Attendance API
Authentication Service
Audit Logging Service
SQL Database
Data flows crossing trust boundaries
