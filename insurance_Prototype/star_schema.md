```mermaid
erDiagram
    FACT_INSURANCE {
        int insurance_id PK
        string insurance_number
        int client_id FK
        int employee_id FK
        int insuranceType_id FK
        int branch_id FK
        int payment_id FK
        date begin_date
        date expiration_date
        int price
    }

    FACT_CLAIM {
        int claim_id PK
        int insurance_id FK
        int cs_id FK
        string claim_name
        int claim_amount
    }

    FACT_PAYMENT {
        int payment_id PK
        string payment_type
        int payment_amount
        date payment_date
    }

    DIM_CLIENT {
        int client_id PK
        string first_name
        string last_name
        date date_of_birth
        int clientType_id FK
        int location_id FK
        int discount
    }

    DIM_EMPLOYEE {
        int employee_id PK
        string first_name
        string last_name
        date date_of_birth
        date date_of_employment
        int salary
        int location_id FK
    }

    DIM_BRANCH {
        int branch_id PK
        string branch_name
        int location_id FK
    }

    DIM_LOCATION {
        int location_id PK
        string region_name
        string city_name
        string street_name
        string house_number
    }

    DIM_INSURANCE_TYPE {
        int insuranceType_id PK
        string insurance_type
    }

    DIM_CLAIM_STATUS {
        int cs_id PK
        string cs_status
    }

    DIM_CLIENT_TYPE {
        int clientType_id PK
        string clientType_name
    }

    FACT_INSURANCE }o--|| DIM_CLIENT : "client_id"
    FACT_INSURANCE }o--|| DIM_EMPLOYEE : "employee_id"
    FACT_INSURANCE }o--|| DIM_BRANCH : "branch_id"
    FACT_INSURANCE }o--|| DIM_INSURANCE_TYPE : "insuranceType_id"
    FACT_INSURANCE }o--|| FACT_PAYMENT : "payment_id"
    FACT_CLAIM }o--|| FACT_INSURANCE : "insurance_id"
    FACT_CLAIM }o--|| DIM_CLAIM_STATUS : "cs_id"
    DIM_CLIENT }o--|| DIM_CLIENT_TYPE : "clientType_id"
    DIM_CLIENT }o--|| DIM_LOCATION : "location_id"
    DIM_EMPLOYEE }o--|| DIM_LOCATION : "location_id"
    DIM_BRANCH }o--|| DIM_LOCATION : "location_id"


    ```
