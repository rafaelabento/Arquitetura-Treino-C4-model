flowchart TB

%% Person
Client["Cliente
Person"]

%% System Boundary
subgraph OnboardingPlatform["Plataforma de Onboarding Digital"]

    MobileApp["Aplicação Mobile
    Container: Mobile Application
    Permite cadastro e submissão de dados"]

    OnboardingService["Onboarding Service
    Container: Backend Service
    Orquestra cadastro, validações e inicia processamento"]

    MessageBroker["Message Broker
    Container: Message Broker
    Comunicação assíncrona entre containers"]

    IntegrationLayer["Integration Layer
    Container: Integration Service
    Adapta chamadas para sistemas externos"]

    Database["Database
    Container: Relational Database
    Armazena dados e status do onboarding"]

end

%% External Systems
Auth["Autenticação e Autorização
Software System"]

Biometric["Validação Biométrica
Software System"]

Fraud["Sistema Anti-Fraude
Software System"]

Core["Core Bancário
Software System"]

Signature["Assinatura Digital
Software System"]

%% Relationships
Client -->|Uses| MobileApp

MobileApp -->|HTTPS/REST (synchronous)| OnboardingService

OnboardingService -->|Reads/Writes| Database

OnboardingService -->|Publishes OnboardingRequested event| MessageBroker
MessageBroker -->|Delivers OnboardingRequested event| OnboardingService

OnboardingService -->|Invokes (synchronous)| IntegrationLayer

IntegrationLayer -->|REST| Auth
IntegrationLayer -->|REST| Biometric
IntegrationLayer -->|REST| Fraud
IntegrationLayer -->|REST| Core
IntegrationLayer -->|REST| Signature
