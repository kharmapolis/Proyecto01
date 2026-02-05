graph TD
    %% Definición de Estilos (Colores más claros y profesionales)
    classDef wan fill:#e1f5fe,stroke:#01579b,stroke-width:2px,color:#01579b;
    classDef router fill:#fff3e0,stroke:#e65100,stroke-width:2px,color:#e65100,font-weight:bold;
    classDef switch fill:#e8eaf6,stroke:#1a237e,stroke-width:2px,color:#1a237e,font-weight:bold;
    classDef vlan210 fill:#f1f8e9,stroke:#33691e,stroke-width:1px;
    classDef vlan220 fill:#fffde7,stroke:#f57f17,stroke-width:1px;
    classDef vlan230 fill:#fce4ec,stroke:#880e4f,stroke-width:1px;
    classDef bridge fill:#eceff1,stroke:#455a64,stroke-dasharray: 5 5;

    %% Nodos Principales
    WAN((🌐 WAN / INTERNET)):::wan
    
    PVE[Proxmox Host]:::switch
    R1[pfSense VM<br/>Firewall / L3 Gateway]:::router
    S1[Huawei S2720<br/>L2 Core Switch]:::switch
    
    %% Conexiones de Backbone
    WAN --- PVE
    PVE --- R1
    R1 -- "Trunk Link (802.1Q)<br/>Tagged: 210, 220, 230" --- S1

    %% VLAN 210 - Administración
    subgraph V210 [VLAN 210: Administración]
        direction TB
        V210_GW[GW: 10.200.210.1]
        Ubuntu[Ubuntu Desktop<br/>Port: Access]
    end
    S1 === V210:::vlan210

    %% VLAN 220 - Servicios
    subgraph V220 [VLAN 220: Servicios]
        direction TB
        V220_GW[GW: 10.200.220.1]
        vmbr220((vmbr220 Bridge)):::bridge
        VM01[VM 01]
        VM02[VM 02]
        
        vmbr220 --- VM01
        vmbr220 --- VM02
    end
    S1 === V220:::vlan220

    %% VLAN 230 - Escaneo/SecOps
    subgraph V230 [VLAN 230: Escaneo/SecOps]
        direction TB
        V230_GW[GW: 10.200.230.1]
        Tcpdump[Tcpdump]
        Wireshark[Wireshark]
        OpenVAS[OpenVAS]
    end
    S1 === V230:::vlan230

    %% Vinculación de Gateways
    V210_GW --- Ubuntu
    V230_GW --- Tcpdump
    V230_GW --- Wireshark
    V230_GW --- OpenVAS

