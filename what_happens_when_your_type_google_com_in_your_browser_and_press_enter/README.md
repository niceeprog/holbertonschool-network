```mermaid
flowchart TD
    %% Nodes
    User(["👤 User / Browser"])
    DNS["🌐 DNS Server"]
    FW["🛡️ Firewall (Port 443)"]
    LB["⚖️ Load Balancer"]
    WS["🖥️ Web Server"]
    AS["⚙️ Application Server"]
    DB[("(🗄️ Database)")]

    %% DNS Flow
    User -->|"1. Request IP for [www.google.com](https://www.google.com)"| DNS
    DNS -->|"2. Return IP Address"| User

    %% Network & Security Flow
    User -->|"3. HTTPS Request (TLS/SSL Encrypted, Port 443)"| FW
    FW -->|"4. Inspect & Pass Traffic"| LB
    LB -->|"5. Distribute Request"| WS

    %% Backend Processing
    WS -->|"6. Route Dynamic Request"| AS
    AS -->|"7. Query Data"| DB
    DB -->|"8. Return Data"| AS

    %% Response Flow
    AS -->|"9. Generate HTML Page"| WS
    WS -->|"10. Serve Web Page"| LB
    LB -->|"11. Forward Encrypted Response"| FW
    FW -->|"12. Deliver Page"| User

    %% Styling
    style User fill:#e1f5fe,stroke:#0288d1,stroke-width:2px
    style DNS fill:#fff3e0,stroke:#f57c00,stroke-width:2px
    style FW fill:#ffebee,stroke:#d32f2f,stroke-width:2px
    style LB fill:#f3e5f5,stroke:#7b1fa2,stroke-width:2px
    style WS fill:#e8f5e9,stroke:#388e3c,stroke-width:2px
    style AS fill:#e8f5e9,stroke:#388e3c,stroke-width:2px
    style DB fill:#eceff1,stroke:#455a64,stroke-width:2px