```mermaid
---
config:
  layout: elk
---
flowchart LR
    User[User]
    DNS[DNS Server]
    
    subgraph Server
        Nginx[Nginx]
        AppServer[Application Server]
        AppFiles["Application Files / Code Base"]
        MySQL[(MySQL)]
    end
    
    User -->|Request| DNS
    DNS -->|IP Address| User
    User -->|HTTP Request| Nginx
    Nginx -->|Forward| AppServer
    AppServer -->|Reads the code| AppFiles
    AppServer -->|SQL Query| MySQL
    MySQL -->|Results| AppServer
    AppServer -->|Response| Nginx
    Nginx -->|HTTP Response| User

    classDef userNode stroke:#38bdf8,fill:#f0f9ff
    classDef dnsNode stroke:#a78bfa,fill:#f5f3ff
    classDef proxyNode stroke:#fb923c,fill:#fff7ed
    classDef appNode stroke:#4ade80,fill:#f0fdf4
    classDef dataNode stroke:#f87171,fill:#fef2f2
    classDef subgraphStyle stroke:#818cf8,fill:#eef2ff

    class User userNode
    class DNS dnsNode
    class Nginx proxyNode
    class AppServer appNode
    class AppFiles appNode
    class MySQL dataNode
    class Server subgraphStyle
```