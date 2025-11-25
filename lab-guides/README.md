This is for preparing the VM lab environment.

| VM                      | CPU      | RAM      | Disk      |
| ----------------------- | -------- | -------- | --------- |
| Keycloak                | 2        | 4GB      | 40GB      |
| FreeIPA (optional)      | 2        | 4GB      | 40GB      |
| Wazuh                   | 4        | 8GB      | 80GB      |
| OpenVAS                 | 2        | 4GB      | 40GB      |
| Elastic Stack           | 4        | 8GB      | 100GB     |
| OPNsense                | 2        | 4GB      | 40GB      |
| K3s Cluster (1–3 nodes) | 2–4 each | 4GB each | 40GB each |
| Vault                   | 2        | 4GB      | 40GB      |
| Shuffle SOAR            | 2        | 4GB      | 40GB      |

| Tool            | OS Required            | Why                    |
| --------------- | ---------------------- | ---------------------- |
| Keycloak        | RHEL                   | Perfectly supported    |
| Wazuh           | RHEL                   | RPM packages available |
| Elastic Stack   | RHEL                   | Supported with yum     |
| Hashicorp Vault | RHEL                   | Official repo          |
| K3s + Istio     | RHEL                   | Works perfectly        |
| Kong Gateway    | RHEL                   | Native support         |
| Shuffle SOAR    | RHEL (Docker)          | Fully supported        |
| OpenZiti        | RHEL                   | Go binary supported    |
| OpenVAS         | **Ubuntu recommended** | RHEL support is poor   |
| OPNsense        | **FreeBSD**            | Mandatory              |
| Windows Client  | **Windows 10/11**      | For Sysmon + sensors   |


| Network Name      | Purpose                         |
| ----------------- | ------------------------------- |
| **ZT-Management** | All admin interfaces            |
| **ZT-Servers**    | Keycloak, Wazuh, Elastic, Vault |
| **ZT-Apps**       | K3s cluster                     |
| **ZT-Client**     | Windows workstation             |
| **WAN**           | NAT to internet                 |


| VM Name            | Pillar         | Network              | OS            |
| ------------------ | -------------- | -------------------- | ------------- |
| OPNsense           | Network        | WAN + MGMT + SERVERS | FreeBSD       |
| Keycloak-01        | Identity       | ZT-SERVERS           | RHEL          |
| FreeIPA (optional) | Identity       | ZT-SERVERS           | RHEL          |
| Wazuh-01           | Device         | ZT-SERVERS           | RHEL          |
| OpenVAS-01         | Device         | ZT-SERVERS           | Ubuntu        |
| Ziti-Controller    | Network/ZTNA   | ZT-SERVERS           | RHEL          |
| K3s-01             | Application    | ZT-APPS              | RHEL          |
| K3s-02             | Application    | ZT-APPS              | RHEL          |
| Kong Gateway       | Application    | ZT-APPS              | RHEL          |
| Vault-01           | Data           | ZT-SERVERS           | RHEL          |
| Elastic-01         | Visibility     | ZT-SERVERS           | RHEL          |
| Shuffle-01         | Automation     | ZT-SERVERS           | RHEL          |
| Windows-Client     | Device/Testing | ZT-CLIENTS           | Windows 10/11 |

