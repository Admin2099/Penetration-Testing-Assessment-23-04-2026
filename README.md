# Penetration Testing Report – IIS WebDAV Exploitation

## Overview
This project demonstrates a complete penetration testing lifecycle performed on a vulnerable target system. The assessment follows a structured approach including reconnaissance, scanning, enumeration, exploitation, and post-exploitation.

The target system is a Windows Server 2003 R2 machine running Microsoft IIS 6.0 with WebDAV enabled, which exposes it to critical vulnerabilities.

## Objectives
- Identify vulnerabilities in the target system  
- Exploit discovered weaknesses  
- Gain initial access to the system  
- Perform privilege escalation  
- Evaluate overall security posture  
- Recommend mitigation strategies  

## Tools and Technologies
- Kali Linux  
- Nmap  
- Gobuster  
- Davtest  
- Cadaver  
- Metasploit Framework  
- Netcat (nc)  
- Churrasco  

## Target Details
| Parameter     | Value                    |
|--------------|--------------------------|
| Target IP    | 10.129.3.70              |
| OS           | Windows Server 2003 R2   |
| Web Server   | Microsoft IIS 6.0        |
| Port         | 80 (HTTP)                |
| Vulnerability| CVE-2017-7269            |

## Methodology

### Reconnaissance
Network interfaces and connectivity were verified using basic commands such as `ip a` and `ping`.

### Scanning
Nmap scans revealed that only port 80 was open on the target system.

### Enumeration
- IIS 6.0 with WebDAV enabled was identified  
- Directory brute-forcing exposed sensitive endpoints  
- FrontPage Server Extensions were detected  

### Exploitation
The Metasploit module below was used:
exploit/windows/iis/iis_webdav_scstoragepathfromurl

This exploited CVE-2017-7269 and established a Meterpreter session.

### Post-Exploitation
- Uploaded payload tools such as `nc.exe` and `churrasco.exe`  
- Established reverse shell access  
- Escalated privileges from NETWORK SERVICE to SYSTEM  

## Key Findings
- Outdated and unsupported operating system  
- WebDAV enabled with insecure HTTP methods  
- Critical remote code execution vulnerability  
- Successful system compromise  
- Full administrative (SYSTEM-level) access obtained  

## Risk Summary

| Risk Level | Description |
|------------|-------------|
| Critical   | Remote code execution and privilege escalation |
| High       | Misconfigured services and exposed attack surface |
| Medium     | Directory exposure and weak configurations |

## Remediation and Defensive Measures
- Upgrade to a supported Windows Server version  
- Disable WebDAV if not required  
- Apply latest security patches  
- Restrict dangerous HTTP methods  
- Implement HTTPS  
- Configure firewall and network segmentation  
- Deploy SIEM solutions for monitoring  
- Enforce least privilege access control  
- Use IDS/IPS and endpoint protection  

## Conclusion
The penetration test demonstrated that the target system is highly vulnerable due to outdated software and insecure configurations. Attackers can easily exploit these weaknesses to gain full system access. Immediate remediation is necessary to secure the environment.

## References
- NIST National Vulnerability Database (CVE-2017-7269)  
- OWASP Top 10  
- Metasploit Documentation  

## Author
Debayan Das  
Cybersecurity Analyst  
