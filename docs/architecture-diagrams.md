# 🧭 IT Security Architecture Diagram (Mermaid)

Below is a basic security architecture using a **Mermaid diagram**, rendered automatically in MkDocs Material.

```mermaid
graph TD
    User[User Device]
    Auth[Authentication Provider]
    FW[Firewall]
    Proxy[Secure Proxy]
    App[Internal Application]
    DB[Database]

    User -->|Login| Auth
    Auth -->|Token| FW
    FW --> Proxy
    Proxy --> App
    App --> DB
```

---

## 🔄 Data Flow Diagram (Zero Trust)

```mermaid
sequenceDiagram
    participant User
    participant IdP
    participant Gateway
    participant App

    User->>IdP: Authenticate
    IdP-->>User: Access Token
    User->>Gateway: Request with Token
    Gateway->>App: Forward if token valid
    App-->>Gateway: Response
    Gateway-->>User: Return data
```

---

## 📌 Notes

!!! tip
    Diagrams are **just Markdown** — no external tooling required. You can document and visualize directly in your docs.
