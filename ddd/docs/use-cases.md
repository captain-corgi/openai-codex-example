# Core Use Cases

This section summarizes key user journeys in the system. Each flow is implemented within the appropriate bounded context and can involve multiple aggregates.

## 1. Customer Onboarding and eKYC

```mermaid
sequenceDiagram
    participant User
    participant UI as Frontend
    participant CM as Customer Management
    participant KY as eKYC Service

    User->>UI: Provide personal details
    UI->>CM: Submit registration
    CM->>KY: Verify identity
    KY-->>CM: Verification result
    CM-->>UI: Account created or rejection
```

## 2. Wallet Top-Up from Bank Account

```mermaid
sequenceDiagram
    participant User
    participant UI
    participant WL as Wallet
    participant CB as Core Banking
    participant TX as Transaction Ledger

    User->>UI: Request top-up
    UI->>WL: Create top-up
    WL->>CB: Initiate transfer from bank
    CB-->>WL: Transfer confirmation
    WL->>TX: Record transaction
    WL-->>UI: Updated balance
```

## 3. Bill Payment Using Wallet

```mermaid
sequenceDiagram
    participant User
    participant UI
    participant BL as Billing
    participant WL as Wallet
    participant TX as Transaction Ledger

    User->>UI: Pay bill
    UI->>BL: Request payment
    BL->>WL: Deduct funds
    WL->>TX: Record payment transaction
    BL-->>UI: Payment receipt
```

These use cases demonstrate how bounded contexts collaborate through services and events. Additional flows (such as recurring payments, notifications, or reporting) can be designed similarly.

