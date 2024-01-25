# CVE-2023-22527: Atlassian Confluence Vulnerability

## Introduction

The CVE-2023-22527 vulnerability is a critical security flaw in Atlassian Confluence, a widely used collaboration and documentation platform. This vulnerability exists in both Confluence Data Center and Confluence Server, which are versions of the platform designed for organizational use on self-hosted servers or cloud infrastructure.

### Vulnerability Details

- **Vulnerability Type**: OGNL (Object-Graph Navigation Language) Injection
- **CVSS Score**: 10.0 (Critical)
- **Affected Versions**:
  - Confluence Data Center and Server: 8.0.x, 8.1.x, 8.2.x, 8.3.x, 8.4.x, 8.5.0-8.5.3

This vulnerability allows for unauthenticated remote code execution, making it possible for adversaries to exploit vulnerable Confluence instances. It's crucial for organizations to patch their systems as soon as possible, considering the high risk and the active exploitation attempts in the wild.

## Docker Setup for Testing

To facilitate testing and understanding of this vulnerability, a Docker setup is provided. The Docker configuration includes an instance of Atlassian Confluence Server `8.5.3`, which is vulnerable to CVE-2023-22527.


### Running the Docker Setup

1. Save the above configuration in a file named `docker-compose.yml`.
2. Run the Docker setup:
   ```bash
   docker-compose up
   ```
3. The Confluence instance will be accessible at `http://localhost:8090`.

## Exploit Script Usage

The exploit script is designed to test the CVE-2023-22527 vulnerability in Confluence instances.

### Running the Script

- **Single URL Mode**:
  ```bash
  python3 exploit.py -u http://<target-ip>:8090 -c "whoami"
  ```
- **File Mode** (for multiple IPs):
  ```bash
  python3 exploit.py -f ips.txt -c "whoami"
  ```
- **Interactive Shell Mode**:
  ```bash
  python3 exploit.py -u http://<target-ip>:8090 --shell
  ```

Type `exit` to leave the interactive shell.


## Disclaimer 🚨

This information is provided strictly for educational and research purposes only 📚. Testing the script should only be conducted on systems where explicit permission has been granted ✅. Unauthorized use of this script and information is illegal 🚫 and unethical 😠.

---

References:
1. [Atlassian Security Advisory](https://confluence.atlassian.com/security/)
2. [ShadowServer Report](https://www.shadowserver.org/)
3. [Tenable blog](https://www.tenable.com/blog/cve-2023-22527-atlassian-confluence-data-center-and-server-template-injection-exploited-in-the)
