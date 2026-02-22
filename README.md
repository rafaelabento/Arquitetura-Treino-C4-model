flowchart TD
    A[Cliente]
    B[Digital Partner System]

    C[Autenticação e Autorização]
    D[Validação Biométrica]
    E[Sistema Anti-fraude]
    F[Core Bancário]
    G[Assinatura Digital]

    H[Aplicação Mobile]
    I[Onboarding Service]
    J[Integration Layer]
    K[Data Base]
    L[Message Broker]

    A --> B

    B --> C
    B --> D
    B --> F

    C --> D
    D --> E
    E --> F
    F --> G

    H --> I
    I --> J
    J --> E
    J --> F
    J --> G

    I --> L
    J --> K

    C --> H
    D --> I
    E --> J
