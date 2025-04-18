```mermaid
erDiagram

    USERS {
        int user_id PK
        string first_name
        string last_name
        string email
        string password_hash
        string phone
        string role_id
        datetime created_at
        datetime updated_at
    }

    ROLES {
        int role_id PK
        string name
        string description
        datetime created_at
    }


    USER_ACCOUNTS {
        int user_account_id PK
        int user_id FK
        float balance
        string wallet_address
        float daily_limit
        float monthly_limit
        string status
        datetime created_at
        datetime updated_at
    }

    ACCOUNT_TRANSACTIONS {
        int account_transaction_id PK
        int user_account_id FK
        string type
        float amount
        float balance
        string description
        datetime created_at
    }

    PROJECTS {
        int project_id PK
        string name
        string description
        date start_date
        date end_date
        string status_id
        date investment_deadline
        int total_budget
        string type
        datetime created_at
        datetime updated_at
    }

    PROJECT_DETAILS {
        int project_detail_id PK
        int project_id FK
        json technical_specs
        float capacity
        float efficiency
        float construction_time
        float maintenance_cost
        datetime created_at
        datetime updated_at
    }

    PROJECT_STATUSES {
        int project_status_id PK
        string name
        string description
        datetime created_at
    }

    PROJECT_PROGRESS {
        int project_progress_id PK
        int project_id FK
        string type
        string content
        string description
        datetime created_at
        datetime updated_at
    }

    PROJECT_MILESTONES {
        int project_milestone_id PK
        int project_id FK
        string title
        string description
        date due_date
        string status
        date completed_at
        datetime created_at
        datetime updated_at
    }

    LOCATIONS {
        int location_id PK
        int project_id FK
        string name
        string city
        string country
        string coordinates
        datetime created_at
        datetime updated_at
    }

    INVESTMENTS {
        int id PK
        int user_id FK
        int project_id FK
        float amount
        datetime investment_date
        float expected_return
        int transaction_id
        datetime created_at
        datetime updated_at
    }

    REPORTS {
        int report_id PK
        string type
    }

    USERS ||--|| ROLES : "has"
    USERS ||--|| USER_ACCOUNTS : "has"
    USER_ACCOUNTS ||--o{ ACCOUNT_TRANSACTIONS : "has"
    USERS ||--o{ INVESTMENTS : "makes, has"

    PROJECTS ||--o{ INVESTMENTS : "has"
    PROJECTS ||--|| PROJECT_DETAILS : "has"
    PROJECTS }|--o{ REPORTS : "has"
    PROJECTS ||--|| PROJECT_STATUSES : "has"
    PROJECTS ||--|{ PROJECT_MILESTONES : "has"
    PROJECTS ||--o{ PROJECT_PROGRESS : "has"
    PROJECTS ||--|| LOCATIONS : "has"
```
