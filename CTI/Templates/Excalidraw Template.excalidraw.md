---
type: excalidraw
tags: [excalidraw, template, attack-chain]
---

# {{title}} - Attack Chain Diagram

## MITRE ATT&CK Attack Chain Template

```mermaid
graph TD
    subgraph "Initial Access"
        IA1[T1566.001<br/>Spearphishing Attachment]
        IA2[T1190<br/>Exploit Public-Facing App]
        IA3[T1195<br/>Supply Chain Compromise]
    end
    
    subgraph "Execution"
        EX1[T1059.001<br/>PowerShell]
        EX2[T1059.003<br/>Windows Command Shell]
        EX3[T1204.002<br/>User Execution]
    end
    
    subgraph "Persistence"
        PR1[T1547.001<br/>Registry Run Keys]
        PR2[T1505.003<br/>Web Shell]
        PR3[T1543.003<br/>Windows Service]
    end
    
    subgraph "Privilege Escalation"
        PE1[T1068<br/>Exploitation for Priv Esc]
        PE2[T1548.002<br/>Bypass UAC]
        PE3[T1556.002<br/>Password Filter]
    end
    
    subgraph "Defense Evasion"
        DE1[T1574.002<br/>DLL Side-Loading]
        DE2[T1070.004<br/>File Deletion]
        DE3[T1562.001<br/>Disable Security Tools]
    end
    
    subgraph "Credential Access"
        CA1[T1003.001<br/>LSASS Memory]
        CA2[T1558.003<br/>Kerberoasting]
        CA3[T1003.006<br/>DCSync]
    end
    
    subgraph "Discovery"
        DI1[T1082<br/>System Info Discovery]
        DI2[T1018<br/>Remote System Discovery]
        DI3[T1069.002<br/>Permission Groups]
    end
    
    subgraph "Lateral Movement"
        LM1[T1021.004<br/>Pass the Hash]
        LM2[T1550.003<br/>Pass the Ticket]
        LM3[T1021.002<br/>SMB/Windows Admin Shares]
    end
    
    subgraph "Collection"
        CO1[T1005<br/>Data from Local System]
        CO2[T1530<br/>Data from Cloud Storage]
        CO3[T1113<br/>Screen Capture]
    end
    
    subgraph "Command & Control"
        CC1[T1573.001<br/>Encrypted Channel]
        CC2[T1090.003<br/>Multi-hop Proxy]
        CC3[T1071.001<br/>Web Protocols]
    end
    
    subgraph "Exfiltration"
        EXF1[T1041<br/>Exfil Over C2]
        EXF2[T1048<br/>Exfil Over Alt Protocol]
        EXF3[T1567.002<br/>Exfil to Cloud]
    end
    
    IA1 --> EX1
    IA1 --> EX2
    IA2 --> EX1
    EX1 --> PR1
    EX1 --> PR2
    PR1 --> PE1
    PR2 --> PE1
    PE1 --> DE1
    DE1 --> CA1
    CA1 --> DI1
    DI1 --> LM1
    LM1 --> CO1
    CO1 --> CC1
    CC1 --> EXF1
```

## Instructions
1. **Duplicate** this template for each campaign analysis
2. **Color-code** nodes:
   - 🔴 Red = Observed in campaign
   - 🟡 Yellow = Suspected/Probable
   - 🟢 Green = Not observed
   - ⚪ Gray = Not applicable
3. **Link** to relevant notes:
   - Click node → Add link to [[CTI/TTPs/TXXXX]] 
   - Link malware/tools: [[CTI/Malware/...]]
   - Link threat actors: [[CTI/Threat Actors/...]]
4. **Add evidence** in node comments (timestamps, IOCs, log sources)

## Example Usage
- [[CTI/Excalidraw/SolarWinds Attack Chain.excalidraw]]
- [[CTI/Excalidraw/APT28 Election Interference.excalidraw]]
- [[CTI/Excalidraw/Lazarus Crypto Heist.excalidraw]]

## Styling Tips
- Use **Frames** to group by tactic
- Use **Arrows** with labels for flow
- Use **Sticky Notes** for evidence/IOCs
- Embed **Images** (screenshots, PCAPs, logs)
- Add **Timestamps** on arrows for timeline