graph TB
    subgraph "Client Layer"
        A1["🖥️ Guest Web App<br/>(Next.js)"]
        A2["🔧 Admin Dashboard<br/>(Next.js)"]
        A3["📱 Mobile App<br/>(React Native)"]
    end

    subgraph "API & Gateway Layer"
        B1["🌐 API Gateway<br/>(Load Balancer)"]
        B2["🔐 Auth Service<br/>(JWT + OAuth)"]
    end

    subgraph "Backend Services"
        C1["👤 User Service"]
        C2["🏠 Property Service"]
        C3["📅 Booking Service"]
        C4["📆 Calendar Service"]
        C5["💳 Payment Service"]
        C6["📧 Notification Service"]
        C7["🔍 Search Service"]
    end

    subgraph "Data Layer"
        D1["🗄️ PostgreSQL<br/>(Primary DB)"]
        D2["⚡ Redis<br/>(Cache & Sessions)"]
        D3["🔎 Elasticsearch<br/>(Search Index)"]
    end

    subgraph "External Services & Storage"
        E1["💰 Stripe<br/>(Payments)"]
        E2["🗂️ AWS S3<br/>(Images & Files)"]
        E3["📬 SendGrid<br/>(Email)"]
        E4["🗺️ Mapbox<br/>(Geolocation)"]
        E5["📞 Twilio<br/>(SMS)"]
    end

    subgraph "DevOps & Monitoring"
        F1["🐳 Docker<br/>(Containerization)"]
        F2["📊 Sentry<br/>(Error Tracking)"]
        F3["📈 DataDog<br/>(Monitoring)"]
        F4["🚀 GitHub Actions<br/>(CI/CD)"]
    end

    A1 --> B1
    A2 --> B1
    A3 --> B1
    B1 --> B2
    B1 --> C1 & C2 & C3 & C4 & C5 & C6 & C7
    
    C1 --> D1 & D2
    C2 --> D1 & D2
    C3 --> D1 & D2
    C4 --> D1 & D2
    C5 --> E1 & D2
    C6 --> E3 & E5
    C7 --> D3
    
    C2 --> E2
    C2 --> E4
    
    F1 -.-> C1 & C2 & C3 & C4 & C5
    F2 -.-> B1
    F3 -.-> C1 & C2 & C3
    F4 -.-> F1
