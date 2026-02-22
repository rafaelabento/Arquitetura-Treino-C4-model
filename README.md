```mermaid
flowchart TB

%% ===== PERSON =====
Client["<<Person>>
Cliente"]

%% ===== SYSTEM BOUNDARY =====
subgraph SystemBoundary["<<Software System>>
Plataforma de Onboarding Digital"]

direction TB

MobileApp["<<Container>>
Aplicação Mobile
Mobile Application"]

OnboardingService["<<Container>>
Onboarding Service
Backend Service"]

MessageBroker["<<Container>>
Message Broker
Message Broker"]

IntegrationLayer["<<Container>>
Integration Layer
Integration Service"]

Database["<<Container>>
Database
Relational Database"]

end

%% ===== EXTERNAL SYSTEMS =====
Auth["<<Software System>>
Autenticação e Autorização"]

Biometric["<<Software System>>
Validação Biométrica"]

Fraud["<<Software System>>
Sistema Anti-Fraude"]

Core["<<Software System>>
Core Bancário"]

Signature["<<Software System>>
Assinatura Digital"]

%% ===== RELATIONSHIPS =====
Client -->|Uses| MobileApp

MobileApp -->|HTTPS / REST (sync)| OnboardingService

OnboardingService -->|Reads/Writes| Database

OnboardingService -->|Publishes OnboardingRequested| MessageBroker
MessageBroker -->|Delivers Event| OnboardingService

OnboardingService -->|Invokes (sync)| IntegrationLayer

IntegrationLayer -->|REST| Auth
IntegrationLayer -->|REST| Biometric
IntegrationLayer -->|REST| Fraud
IntegrationLayer -->|REST| Core
IntegrationLayer -->|REST| Signature
```
