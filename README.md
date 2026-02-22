flowchart TD

    %% Top row
    A[Cliente]
    B[Digital Partner System]

    %% Middle row (purple)
    C[Autenticação e Autorização]
    D[Validação Biométrica]
    E[Sistema Anti-fraude]
    F[Core Bancário]
    G[Assinatura Digital]

    %% Bottom row (blue)
    H[Aplicação Mobile]
    I[Onboarding Service]
    J[Integration Layer]
    K[Data Base]
    L[Message Broker]

    %% Connections (following original visual flow)
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
    J --> F
    J --> G
    J --> E

    I --> L
    J --> K

    %% Vertical/return links seen in diagram
    C --> H
    D --> I
    E --> J
