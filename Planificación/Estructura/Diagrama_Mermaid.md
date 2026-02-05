
# Topologia de red 

```mermaid
graph TD
    %% graph TD
    %% Definición de Nodos de Red
    WAN((WAN / INTERNET))
    
    R1[Cisco 887M<br/>L3 Gateway - RoaS]
    S1[Huawei S2720<br/>L2 Core Switch]
    
    %% VLANs como subgrafos para orden visual
    subgraph VLAN_210 [VLAN 210: Administración]
        direction TB
        V210_GW[GW: 10.200.210.1]
        Ubuntu[Ubuntu Desktop<br/>Port: Access]
    end

    subgraph VLAN_220 [VLAN 220: Servicios/DMZ]
        direction TB
        V220_GW[GW: 10.200.220.1]
        Proxmox[Proxmox Host<br/>Linux Bridges]
        vmbr220((vmbr220))
        VM01[VM 01]
        VM02[VM 02]
    end

    subgraph VLAN_230 [VLAN 230: Escaneo/SecOps]
        direction TB
        V230_GW[GW: 10.200.230.1]
        Tcpdump[Tcpdump]
        Wireshark[Wireshark]
        OpenVAS[OpenVAS]
    end

    %% Conexiones principales
    WAN --- R1
    R1 -- "Trunk Link (802.1Q)<br/>Sub-interfaces .210, .220, .230" --- S1

    %% Distribución de VLANs
    S1 --- V210_GW
    S1 --- V220_GW
    S1 --- V230_GW

    %% Conexiones internas
    V210_GW --- Ubuntu
    
    V220_GW --- Proxmox
    Proxmox --- vmbr220
    vmbr220 --- VM01
    vmbr220 --- VM02

    V230_GW --- Tcpdump
    V230_GW --- Wireshark
    V230_GW --- OpenVAS

    %% Estilos
    classDef router fill:#f96,stroke:#333,stroke-width:2px;
    classDef switch fill:#69f,stroke:#333,stroke-width:2px;
    classDef server fill:#dfd,stroke:#333,stroke-width:1px;
    
    class R1 router;
    class S1 switch;
    class Proxmox,Ubuntu,VM01,VM02 server;
