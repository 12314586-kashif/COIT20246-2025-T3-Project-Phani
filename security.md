# Security

[Risk Assesment](#risk-assessment) | [Security Controls](#security-controls) | [Plan](./plan.md) | [Network Design](./network.md) | [Cloud Services](./cloud.md) | [Ethics](./ethics.md) | [Reflection](./reflection.md) | [Return to index](./README.md)

Security

## Risk Assessment
The spreadsheet for risk assessment can be accessed below.  
[View risk assessment spreadsheet](./risk-assessment.xlsx)

Along with spread sheet, the TVA matrix is also created which can be checked below.  

![TVA Matrix](./tva-1.png)  
![TVA Matrix](./tva-2.png)  
![TVA Matrix](./tva-3.png)

## Security Controls
The asset with highest risk is ‘Client Project Data’ which is identified as Asset Number 1. This is because the client data from all the sites is stored and it is a primary target for the attackers to extort it and use it for illegal purposes. This can be managed by employing robust security controls focussing on the NIST SP 800-53 framework.

### Control: Data Backup (CP-9)
- **Implementation:** Implementation for the same can be carried out with 3-2-1 backup strategy for internal servers that hosts the client data. The automated system can be used for creating copies of the data, one will be stored on local NAS and second one will be stored on the dedicated backup server.
- **How it reduces risk:** When the backup copies are created, it addresses the risk of insufficient backup frequency and if any extortion attack is faced, the Truelec is able to restore the data back from its backup copies without losing it.
- **Network Integration:** The backup server can be configured in the separate management VLAN across the HQ, and the firewall can be configured for allowing one-way traffic to the backup server.
- **Disadvantage:** A slight impact on the network latency due to high-volume data backup.

### Control: Access Enforcement (CP-3)
- **Implementation:** For enforcing the access control, the role-based access control (RBAC) is recommended for CRM and internal file servers. It comes with centralized directory service to restrict the access to the Client Project data and ensure only authorized ones are accessing it.
- **How it reduces risk:** The risk of IP compromise and espionage will be reduced with RBAC technique as if credentials are stolen, then also the sensitive industrial data cannot be accessed.
- **Network Integration:** The implementation for the same can be done on the Core switch and at the server level. For the network, the NAC can also be enabled for only permit authorized devices to enter the network.
- **Disadvantage:** Administrative friction can be created with this control.

### Control: Boundary Protection (CP-7)
- **Implementation:** The implementation of the next-generation firewall (NGFW) will be done on the HQ and the branch WAN edges with Data Loss Prevention (DLP) to protect the Truelec’s network.
- **How it reduces risk:** With the use of the DLP, it will scan the inbound and outbound traffic for suspicious patterns and avoids any ex-filtration to external areas. Following this, the IP compromises risk can be avoided and one can remain up to date.
- **Network Integration:** The implementation of this control will be done on the network edge (WAN router and firewall) with deep packet inspection to keep boundaries safeguarded.
- **Disadvantage:** The use of the SSL will be done which could be resource intensive, exhausting many resources.