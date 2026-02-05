```mermaid
graph TD

    %% Estilos
    classDef wan fill:#e1f5fe,stroke:#01579b,stroke-width:2px;
    classDef router fill:#fff3e0,stroke:#e65100,stroke-width:2px;
    classDef switch fill:#e8eaf6,stroke:#1a237e,stroke-width:2px;
    classDef bridge fill:#eceff1,stroke:#455a64,stroke-dasharray: 5 5;

    %% Nodos principales
    WAN[WAN / Internet]:::wan

    PVE[Proxmox Host]:::switch
    PF[pfSense VM]:::router
    SW[Huawei S2720]:::switch

    %% Backbone
    WAN --> PVE
    PVE --> PF
    PF --> SW

    %% VLAN 210
    subgraph V210 [VLAN 210 - Administracion]
        UB[Ubuntu Admin]
    end
    SW --> V210

    %% VLAN 220
    subgraph V220 [VLAN 220 - Servidores]
        VM1[VM01]
        VM2[VM02]
    end
    SW --> V220

    %% VLAN 230
    subgraph V230 [VLAN 230 - DMZ]
        TD[Tcpdump]
        WS[Wireshark]
        OV[OpenVAS]
    end
    SW --> V230

