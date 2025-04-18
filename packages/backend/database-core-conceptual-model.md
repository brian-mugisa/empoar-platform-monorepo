```mermaid
erDiagram
    INVESTOR {
        string name
        string phone
        string email
        string date_registered
    }

    MANAGER {
        string name
        string phone
        string email
        string date_registered
    }

    PROJECT {
        string name
        string location
        string budget
        string investments
    }

    REPORT {
        string type
    }

    INVESTOR ||--|| PROJECT : "invests in"
    INVESTOR ||--|| REPORT : "views"
    PROJECT ||--|| REPORT : "has"
    MANAGER ||--|| PROJECT : "manages"
    MANAGER ||--|| REPORT : "builds"
``
```
