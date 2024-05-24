**Health New Zealand | Te Whatu Ora Cryptography Standard - _Draft_**

**Document Information**

| **Title** | Cryptography Standard |
| --- | --- |
| **Version** | 0.94e |
| **Effective Date** | TBD |
| **Author** | Abdul Haq Mohammed |
| **Approval Authority** | Jurie Du Preez |
| **Review Cycle** | Annually |

| **Version** | **Date** | **Author(s)** | **Changes Made** |
| --- | --- | --- | --- |
| 0.1 | Dec 22, 2023 | Abdul | Initial draft of Cryptography Standard template. |
| 0.2 | Jan 6, 2024 | Abdul | Reviewed and altered clarified sections. |
| 0.3 | Jan 11, 2024 | Abdul | Added references to NIST, HISO/HISF, NZISM 3.6. |
| 0.4 | Jan 17, 2024 | Abdul | Updated encryption options. |
| 0.5 | Jan 21, 2024 | Abdul | Encryption best practices. |
| 0.6 | Jan 26, 2024 | Abdul | Reviewed and revised entire document for clarity. |
| 0.7 | Jan 29, 2024 | Abdul | Major update: restructured, added version control. |
| 0.8 | Feb 14, 2024 | Abdul | Updated references, reviewed encryption details. |
| 0.9 | Feb 17, 2024 | Abdul | Added section on KMS. |
| 0.91 | Feb 23, 2024 | Abdul | Review the standard for additional content on Cloud/HA services |
| 0.92 | Feb 28, 2024 | Abdul | Rewritten based on changes in new release - NZISM 3.7 |
| 0.93 | Feb 28, 2024 | Abdul | Review & minor modification like adding references to NZISM 3.7 |
| 0.94 | Mar 06, 2024 | Abdul | Content updated |
| 0.94a | Mar 07, 2024 | Abdul Haq | Comments added after consulting Jurie |
| 0.94b | Mar 08, 2024 | Abdul Haq | Comments addressed |
| 0.94c | Mar 11, 2024 | Abdul Haq | Updated with Tables and cheat codes |
| 0.94d | Mar 21, 2024 | Abdul Haq | Alignment as per Liz template e.g., API standard |
| 0.94e | Apr 11, 2024 | Abdul Haq | Content updates on Key management – need to update parameters in the next update |

**Health New Zealand | Te Whatu Ora Cryptography Standard - _Draft_**

**Table of Contents**

1. **Introduction**

1.1 Objective

1.2 Target Audience

1.3 Reference Sources

1.4 Compliance Language

1.5 Acceptance of Risk

1. **Cryptography Standard - Purpose & Scope**

2.1 Cryptographic Standard Requirements

1. **Encryption Methods - Rationale & Controls**

3.1 On-Premises Encryption

3.1.1 Key Size Considerations

3.1.2 Categorisation of Cryptographic Algorithms (for On-Premises Encryption)

3.1.3 Evolution of Cryptographic Standards

3.1.4 Legacy Algorithms

3.1.5 Endorsed Asymmetric/Public Key Algorithms

3.1.6 Endorsed Hashing Algorithms

3.1.7 Endorsed Symmetric Encryption Algorithms

3.1.8 Prohibited Algorithms

3.1.9 Cryptographic Function Standards and Minimum Requirements

3.1.10 Salting

**3.2 Cloud Services Encryption**

3.2.1 Secure Communication Essentials: Cryptographic Protocols

1. **Using Cryptographic Algorithms - Rationale & Controls**

4.1 Asymmetric/Public Key Algorithms

4.2 Public Key Infrastructure using RSA

4.3 Hashing Algorithms

4.4 Salts

4.5 Symmetric Encryption Algorithms

1. **Cryptographic Protocols**

5.1 Transport Layer Security (TLS)

5.2 Secure Shell (SSH)

5.3 Internet Protocol Security (IPSec)

1. **Digital Signatures**
2. **Key Management**

7.1 Key Management Life Cycle

7.2 Hybrid Solution for Key Management System (KMS)

7.3 High Assurance Cryptographic Equipment (HACE)

7.4 Hardware Security Modules (HSM)

1. **Audit and Compliance**
2. **Appendices**
3. **References & Bibliography**

10.1 Related Documents

10.2 Acronyms

10.3 Definitions

10.4 Document Management

10.4.1 Distribution

10.4.2 Document Version

10.4.3 Template Version

**1\. Introduction**

**1.1 Objective**

**Health NZ Cryptographic Standards**

**Compliance with GCSB Regulations**: Health NZ - Te Whatu Ora strictly adheres to cryptographic products, algorithms, and protocols sanctioned by the GCSB, ensuring regulatory compliance.

**Adherence to Guidelines**: Implementation aligns with the meticulous protocols delineated within this document, maintaining professional standards.

This Cryptography Standard sets a baseline for safeguarding all information and systems classified up to and including **IN CONFIDENCE** within Health NZ - Te Whatu Ora’s network infrastructure. The standard is universally applicable across On-premises, Cloud, and Hybrid environments, encompassing systems provided by external agencies or suppliers.

**1.2 Scope**

This section encompasses fundamental cryptography information, including encryption methods for safeguarding healthcare data at rest and in transit. Detailed information on endorsed cryptographic algorithms and protocols can be found in NZISM 3.7, Sections 3.1.5, 3.1.6, 3.1.7, 4.1 - Endorsed Cryptographic Algorithms and Section 5 - Endorsed Cryptographic Protocols.

**1.3 Target Audience**

This document is indispensable for the following roles within the organization:

- Steering Groups
- Managers
- Architects
- System Administrators
- Network Administrators
- Network Operators
- Database Administrators
- System Operators
- Third Parties or Suppliers offering IT products or services to Te Whatu Ora.

**1.4 Reference Sources**

This standard is based on the following industry standards, taking precedence over Te Whatu Ora’s interpretations where differences arise:

- Health Information Security Framework (HISF)
- New Zealand Information Security Manual (NZISM)
- Protective Security Requirements (PSR)
- Other relevant industry standards (NIST)

\*Regular reviews ensure alignment with evolving standards and technologies.

**1.5 Compliance Language**

- **MUST** and **MUST NOT**: Represent absolute requirements.
- **SHOULD** and **SHOULD NOT**: Indicate flexible adherence based on security risk assessment.

**1.6 Acceptance of Risk**

- Exemptions from **MUST** and **MUST NOT** controls require clear rationale and review by the CISO.
- Non-compliance with **SHOULD** and **SHOULD NOT** controls must be documented and reviewed by the Senior Security Specialist, with the CISO acting as arbitrator if needed.

**2\. Cryptography Standard - Purpose and Scope**

Cryptography serves as a critical control for data protection, ensuring confidentiality, integrity, and authenticity.

**Cryptography serves the following purposes:**

- **Encryption**: Protects data confidentiality by converting plaintext into ciphertext.
- **Digital Signatures**: Verify data authenticity and integrity.
- **Hashing**: Generates fixed-size hash values for data integrity checks.
- **Key Management**: Ensures secure key handling.

**Purpose:** This document outlines the Cryptographic standards tailored for Health New Zealand, aiming to safeguard data both during transmission and storage.

**Scope:** This standard pertains to all information systems managed or hosted by Health New Zealand or its agencies. Compliance with this standard is mandatory for all new systems where Cryptographic solution (Viz. encryption) is deemed necessary. Existing systems are encouraged to align with this standard promptly. As older cryptographic algorithms become more susceptible to vulnerabilities due to advancements in computing power and speed, adherence to the recommendations and controls outlined in this standard is crucial. In cases where compliance with this standard poses challenges, exemptions can be sought from the Cybersecurity Assurance department.

**2.1 Cryptographic Standard Requirements:**

**Assurance Levels**

Common Criteria, Protection Profiles, and Endorsed Evaluations: The level of assurance in encryption is often defined through internationally recognised standards such as **Common Criteria** (CC) and **Protection Profiles** (PP). These evaluations assess cryptographic protocols and algorithms, ensuring their reliability and effectiveness.

**Note:** Evaluations of cryptographic protocols and algorithms are not universally conducted during security product evaluations. Instead, reliance is placed on previously Endorsed evaluations.

**Specific Requirements for Encryption**

**Information or Systems Classified RESTRICTED or SENSITIVE**

- **Requirement:** When transmitting information or when systems communicate over insecure or unprotected networks (such as the Internet, public infrastructure, or non-agency-controlled networks), data classified as **RESTRICTED** or **SENSITIVE** **MUST** be encrypted.
- Endorsed **Encryption:** Use an Endorsed encryption algorithm and protocol to safeguard the confidentiality of this information (NZISM CID: 2090).

**Data Transmission Between Data Centers**

- **Requirement:** When data is transmitted between data centers over insecure or unprotected networks (such as the Internet, public infrastructure, or non-agency-controlled networks), it **MUST** be encrypted.
- **Endorsed** **Algorithm and Protocol:** Data **MUST** be encrypted using an Endorsed encryption algorithm and protocol to ensure data integrity during transmission (NZISM CID: 2091).

**3\. Encryption Methods** **\- Rationale & Controls**

**3.1 On-Premises Encryption**

Prior to implementing encryption strategies for on-premises systems, it is crucial to outline key approaches for securing data at rest and in transit. These strategies should encompass encryption techniques applied at various levels to ensure comprehensive protection of sensitive information.

<table><tbody><tr><th><p><strong>Strategy</strong></p></th><th><p><strong>Description</strong></p></th></tr><tr><td rowspan="4"><p><strong>Data Encryption at Rest</strong></p></td><td rowspan="4"><ol><li>Encrypt sensitive data stored within databases, file systems, and backups to maintain confidentiality.</li><li>Employ robust encryption algorithms, such as AES-256, to ensure strong protection.</li><li>Securely manage encryption keys using Hardware Security Modules (HSMs) or dedicated key management services to prevent unauthorized access.</li></ol></td></tr><tr><td></td></tr><tr><td></td></tr><tr><td></td></tr><tr><td rowspan="4"><p><strong>Data Encryption in Transit</strong></p></td><td rowspan="4"><ol><li>Utilise secure communication protocols like TLS/SSL for transmitting data securely over networks.</li><li>Encrypt data during its transmission across networks to safeguard against interception and unauthorized access.</li><li>Ensure regular updates of cryptographic libraries to mitigate vulnerabilities and enhance security.</li></ol></td><td></td></tr><tr><td></td></tr><tr><td></td></tr><tr><td></td></tr><tr><td rowspan="3"><p><strong>Application-Level Encryption</strong></p></td><td rowspan="3"><ol><li>Implement encryption mechanisms within applications, such as field-level encryption, to safeguard sensitive data at a granular level.</li><li><br>Apply encryption measures to protect sensitive data before storage, ensuring its confidentiality and integrity are maintained.</li></ol></td><td></td></tr><tr><td></td></tr><tr><td></td></tr></tbody></table>

**3.1.1 Key Size Considerations**

It is crucial to factor in sufficient safety margins when determining key sizes, particularly in light of potential future advancements in attack methodologies. For example, smaller RSA moduli could become vulnerable to attacks arising from developments in number factorization techniques down the line.

**3.1.2 Categorisation of Cryptographic Algorithms (_for On-Premises Encryption_):**

The cryptographic algorithms listed in this standard have undergone rigorous evaluation by government, industry, and academic communities, both in practical applications and theoretical analyses. While no algorithm can guarantee absolute security against unknown attacks, the algorithms detailed herein have not shown susceptibility to feasible attacks based on current technologies and capabilities. Here is a breakdown of Endorsed cryptographic algorithms, classified into three groups:

- - Asymmetric/public key algorithms
    - Hashing algorithms
    - Symmetric encryption algorithms Collectively known as SUITE B and initially introduced in 2006.

**3.1.3 Evolution of Cryptographic Standards:**

**SUITE B** was succeeded by the Commercial National Security Algorithm Suite in August 2015 and later augmented by the Commercial Solutions for Classified (CSFC) Programme.

**3.1.4 Legacy Algorithms:**

Some algorithms previously endorsed in earlier versions of the NZISM are now deprecated. While still permissible for decrypting or verifying previously encrypted or signed files, these algorithms are labelled as "for legacy use only" in the NZISM.

**3.1.5 Endorsed Asymmetric/Public Key Algorithms**

Endorsed asymmetric/public key algorithms include:

| **ECDH** | For encryption session key agreement. |
| --- | --- |
| **ECDSA** | For digital signatures. |
| **DH** | For encryption session key agreement (to be used only for interoperability with third parties lacking ECDH support). |
| **RSA** | For digital signatures and exchanging encryption session keys. |
| **DSA** | For digital signatures (for legacy purposes). |

**3.1.6 Endorsed Hashing Algorithms**

| **Secure Hashing Algorithm 2 (SHA-2)** |
| --- |
| **Secure Hashing Algorithm 1 (SHA-1)** (for legacy applications) |

**3.1.7 Endorsed Symmetric Encryption Algorithms**

| **Advanced Encryption Standard (AES)** |
| --- |
| **Triple Data Encryption Standard (3DES)** (for legacy purposes) |

**3.1.8 Prohibited Algorithms**

The following algorithms **MUST NOT** be used for new implementations and are exclusively Endorsed for processing previously protected information, designated for legacy use only:

| **Algorithm** | **Rationale for Prohibition** |
| --- | --- |
| **SHA-1** | **SHA-1** is deprecated due to its vulnerability to collision attacks, making it unsuitable for ensuring data integrity and security in modern cryptographic implementations. |
| **3DES** | Triple **DES (3DES)** is considered weak against brute-force attacks compared to modern encryption standards like AES. It poses a higher risk of exploitation, compromising data confidentiality and integrity. |
| **DSA** | The **Digital Signature Algorithm (DSA)** is susceptible to various attacks, including key recovery and collision attacks. Its usage is discouraged in favour of more secure alternatives like RSA or ECC. |

**3.1.9 Cryptographic Function Standards and Minimum Requirements:**

The below table outlines the recommended cryptographic algorithms and protocols along with their applicable standards and minimum security specifications:

| **Function** | **Cryptographic algorithm or protocol** | **Applicable standards** | **Minimum** |
| --- | --- | --- | --- |
| Encryption | Advanced Encryption Standard (AES) | FIPS 197 | 256-bit key |
| Hashing | Secure Hash Algorithm (SHA) | FIPS 180-4 | SHA-384<br><br>(SHA-256 IN CONFIDENCE & BELOW only) |
| Digital signature<br><br>&nbsp; | Elliptic Curve Digital Signature Algorithm (ECDSA) | FIPS 186-3 | NIST P-384 |
| Rivest-Shamir-Adleman (RSA) | NIST SP 800-56B Rev. 2 | 3072-bit key<br><br>(2048-bit key in PKI) |
| Key exchange<br><br>&nbsp;<br><br>&nbsp; | Elliptic Curve Diffie-Hellman (ECDH) | SP 800-56A  <br>ANSI X9.63 | NIST P-384 |
| Rivest-Shamir-Adleman | &nbsp; | 3072-bit key |
| Diffie-Helman (DH) | IETF RFC 3526 (Reference m) | 3072-bit key |

**3.1.10 Salting for enhanced Security:**

Salting is a crucial technique in enhancing the security of hashed passwords. Below are the guidelines and Principles for Effective Salting

| **Guidelines for Effective Salting** | **Principles for Implementing Salts for Specific Credentials** |
| --- | --- | --- |
| **Utilize Cryptographically Strong Salts**  <br>Salts should be generated using cryptographically strong algorithms to maximize their effectiveness in enhancing hash resistance. | **Generate Unique Salts**  <br>Generate a new salt every time a credential is created and stored to ensure uniqueness and enhance security. |
|     |
| **Generate Random Salts**  <br>Salts should be randomly generated to prevent predictability and improve security against various attack vectors. | **Use Cryptographically Strong Random Data**  <br>Employ robust random data sources for generating Salts to bolster security against attacks. |     |
|     |
| **Ensure Salt Uniqueness**  <br>Each password should be paired with a unique salt to prevent attackers from leveraging common salts across multiple passwords. | **Select Appropriate Salt Length**  <br>Choose a salt length of at least 32 or 64 bits based on storage and system constraints, balancing security with practicality. |     |
|     |
| **Avoid Common Implementation Errors**  <br>Steer clear of pitfalls such as using salts that are too short or reusing salts across multiple passwords, which can weaken security. | **Implement Transparent Security Schemas**  <br>Develop security schemas that do not rely on obscuring or concealing the salt, ensuring transparency and effectiveness. |     |
|     |
| **System-Wide Salt Application**  <br>Apply salts on a per-user or per-credential basis rather than system-wide to maintain granularity and mitigate security risks. | Avoid System-Wide Salt Application |     |

**3.2 Cloud Services Encryption**

In cloud computing environments, encryption plays a vital role in safeguarding data confidentiality and integrity, especially in platforms like AWS and Azure.

**To effectively secure data in such environments, consider the following encryption strategies:**

| **Strategy** | **Description** | **Acceptable Practices** |
| --- | --- | --- | --- |
| Cloud Provider KMS | Utilise the Key Management Services (KMS) offered by the cloud provider.  <br>Employ managed keys provided by the cloud provider for encryption purposes. | Regularly rotate encryption keys to minimize exposure.  <br>Implement strict access controls for key management. |
|     |
| Client-Side Encryption | Encrypt data locally before transmitting it to the cloud service.  <br>Retain control over encryption keys to ensure data confidentiality. | Use strong encryption algorithms (e.g., AES-256).  <br>Safeguard client-side keys—store them securely. |     |
|     |
| Database Encryption | Enable encryption for cloud-hosted databases such as Amazon RDS or Azure SQL Database.  <br>Implement TDE or column-level encryption for sensitive data protection. | Regularly audit and monitor key usage.  <br>Rotate database encryption keys periodically. |     |
|     |
|     |

**3.3 Securing VPN Connections**

Government agencies utilizing cryptographic functionality within a product to safeguard information confidentiality, authentication, non-repudiation, or integrity must ensure that the product undergoes a cryptographic evaluation recognized by the GCSB.

**Control System Classifications(s):** All Classifications; Compliance: **Mandatory** \[**CID:2070**\]

Agencies are required to prioritize the security of VPN connections by adhering to the following key aspects:

1. **Encryption Algorithms**: Evaluate the encryption algorithms employed in VPNs to ensure they meet security standards and provide adequate protection against unauthorized access.
2. **Cryptographic Key Lengths**: Ensure that cryptographic keys used in VPN connections are of appropriate lengths to resist cryptographic attacks and maintain data confidentiality.
3. **Authentication and Key Exchange Protocols**: Select robust authentication methods and key exchange protocols to verify the identity of VPN users and establish secure communication channels.
4. **VPN Protocol Selection**: Choose VPN protocols that align with security requirements and provide the necessary features for secure data transmission over public networks.
5. **Cryptographic Key Management**: Implement effective key management practices to securely generate, distribute, and revoke cryptographic keys used in VPN connections, minimizing the risk of key compromise.

**Agencies should assess VPN services for the following criteria:**

- **Hash Authentication**: Verify the use of secure hash algorithms for authentication to prevent unauthorised access to VPN connections.
- **Perfect Forward Secrecy**: Ensure that VPN implementations support perfect forward secrecy to protect past sessions against future cryptographic attacks.
- **Encryption Settings on Data and Control Channels**: Confirm that encryption settings are properly configured for both data and control channels to maintain the confidentiality and integrity of VPN traffic.
- **Adherence to NZISM-** **Endorsed** **Cryptographic Protocols and Algorithms**: Ensure that VPN services comply with the cryptographic protocols and algorithms endorsed by NZISM to meet government security standards.

_For detailed guidance on securing VPN connections, refer to NZISM 3.7, Sections 3.1.5, 3.1.6, 3.1.7, 4.1, and 5 in the endorsed cryptographic guidelines._

**4\. Secure Communication Protocol Guidelines**

- **Endorsed** **Protocols:** Use GCSB- Endorsed cryptographic protocols.
- **Evaluation:** Ensure protocols undergo GCSB-recognized evaluations.
- **Compliance:** Adhere to regulatory standards.
- **Monitoring:** Continuously assess and monitor protocols.

**4.1 Secure Configuration of Cryptographic Algorithms**

Proper configuration of product security settings is paramount to mitigate potential vulnerabilities and security risks. Careful attention must be paid to avoid unintentionally selecting weaker security options, which could have detrimental consequences. When configuring products with specific security measures, it is imperative to deactivate any options that do not adhere to Endorsed standards. Verification of correct security settings is an integral part of the system certification process.

| **Control System Classifications(s)** | **All Classifications** |
| --- | --- |
| **Compliance** | **Must** \[NZISM CID:2128\] |
| **Requirement** | Agencies must ensure the exclusive use of endorsed Cryptographic Algorithms in unevaluated products that implement a combination of Endorsed and non-endorsed Cryptographic Algorithms. |

**4.1.1 Asymmetric/Public Key Algorithms**

As cryptographic standards continually evolve and security threats advance, it is imperative for organizations to adopt and adhere to best practices to safeguard sensitive information. From legacy systems utilizing DH and DSA to prioritizing ECDH and ECDSA for new implementations, each algorithm is accompanied by specific key length recommendations and control system classifications. Adherence to these guidelines is paramount to maintaining robust cryptographic security across all classifications of systems as outlined in our Standards document. This table presents essential recommendations and compliance requirements for asymmetric/public key algorithms within cryptographic systems.

| **Cryptographic Method** | **Rationale** | **Control System Classifications** | **Compliance** |
| --- | --- | --- | --- |
| **ECDH and ECDSA** | In recent years, DSA and DH cryptosystems have faced increasing sub-exponential factorization and index-calculus-based attacks. As more secure alternatives, ECDH and ECDSA offer enhanced security per bit increase in key size compared to DH or DSA. | All Classifications | Should \[NZISM CID:2131\] |
| **Using DH** | Although ECDH is preferred over DH, there are scenarios where DH is still in use. For such cases, a modulus of at least 3072 bits for DH is now considered best practice by the cryptographic community. | All Classifications | Must \[NZISM CID:2134\] |
| **Equipment Using DH** | In scenarios where a network device lacks support for the required cryptographic protocol, algorithm, and key length, the system faces vulnerability to cryptographic compromise. To mitigate this risk, it’s imperative to implement the longest feasible key length and promptly schedule the replacement of such devices. | All Classifications | Must \[NZISM CID:2137\] |
| **Using DSA (for legacy use only)** | For DSA usage, a modulus of at least 1024 bits is recommended by the cryptographic community. | All Classifications | Must \[NZISM CID:7189\] |
| **Using ECDH** | The cryptographic community now considers a field/key size of at least 384 bits for ECDH to be good practice. | All Classifications | NZISM CID:2144: Agencies employing ECDH for agreeing on encryption session keys MUST implement the curve P-384 (prime moduli).<br><br>NZISM CID:2145: All VPNs using an ECDH key length less than 384 MUST replace all Pre-Shared Keys with keys of at least 384 bits as soon as possible. |
| **Using ECDSA** | The cryptographic community recommends achieving an equivalent symmetric key security strength of at least 160 bits for ECDSA. However, not all legacy systems support a modulus of this length, thereby exposing significant risks. | All Classifications | NZISM CID:2148: Agencies utilizing ECDSA for digital signatures MUST implement the curve P-384 (prime moduli) to ensure compliance. |
| **Using RSA** | Maintaining a modulus of at least 3072 bits for RSA aligns with the best practices endorsed by the cryptographic community. | All Classifications | NZISM CID:2151: Agencies leveraging RSA for digital signatures and passing encryption session keys or similar keys MUST adhere to a modulus of at least 3072 bits.<br><br>NZISM CID:2152: To ensure security, agencies utilizing RSA for digital signatures and passing encryption session keys or similar keys MUST ensure that the public keys used for passing encrypted session keys differ from those used for digital signatures.<br><br>NZISM CID:7181: Agencies leveraging RSA for digital signatures and passing encryption session keys or similar keys SHOULD use a modulus of at least 4096 bits for enhanced security. |

**4.1.2 Public Key Infrastructure - Using RSA**

The below table highlights the necessity of employing a minimum 2048-bit RSA modulus in X.509 Public Key Infrastructure (PKI) systems. Compliance with this standard, mandated for all system classifications, ensures robust security as per \[NZISM CID:7186\].

| **Cryptographic Method** | **Rationale** | **Control System Classifications** | **Compliance** |
| --- | --- | --- | --- |
| X.509-based Public Key Infrastructure (PKI) systems | For X.509-based PKI systems, a modulus of at least 2048 bits for RSA is standard practice. | All Classifications | **Must** \[NZISM CID:7186\]  <br>Agencies **MUST** ensure RSA keys within  <br>internet X.509 PKI certificates are  <br>at least 2048 bits for compliance. |
|     |
|     |
|     |

**4.1.3 Hashing Algorithms**

The below table outlines the recommended cryptographic methods and their corresponding compliance requirements for ensuring data integrity within different system classifications. It emphasizes the necessity of transitioning from SHA-1 to more secure options like SHA-2 for new systems, while also specifying the use of SHA-384 for protecting sensitive information.

| **Cryptographic Method** | **Rationale** | **Control System Classifications** | **Compliance** |
| --- | --- | --- | --- | --- |
| Secure Hash Algorithm 1 (SHA-1) | While no practical collision attacks have been published, SHA-1 is susceptible to future attacks.  <br>SHA-1 has been deprecated due to its vulnerability to collision attacks, limited to legacy systems validation. | All Classifications | **Must** \[NZISM CID:2155\]  <br>Use SHA-2 for new systems, SHA-1 only  <br>for established legacy systems. |
|     |
|     |
|     |
| SHA-384 | For information classified as RESTRICTED/SENSITIVE, SHA-384 is mandated for hashing to ensure integrity. | All Classifications | **Must** \[NZISM CID:5905\] |     |
| SHA-256 | For integrity protection in other cases, SHA-256 is required to meet compliance standards. | All Classifications | **Must** \[NZISM CID:7187\] |     |

**4.1.4 Salts**

The below table outlines guidelines for the use of salts in cryptographic processes. Salts play a crucial role in strengthening hash values against various cyberattacks. The guidelines emphasize the importance of employing key derivation functions, using unique salts, and ensuring sufficient length to mitigate security risks effectively. Compliance with these guidelines is **MUST** for bolstering the security posture of cryptographic systems across all classifications.

| **Cryptographic Method** | **Rationale** | **Control System Classifications** | **Compliance** |
| --- | --- | --- | --- |
| Salts | Salts are crucial for bolstering hash values against various attacks such as brute-force and rainbow table attacks. | All Classifications | **Must** \[NZISM CID:6560\] |
| Key derivation functions, incorporating passwords and salts, significantly increase the difficulty and cost of guessing passwords from hash files, thus enhancing security. | All Classifications | **Should** \[NZISM CID:6561\] |
| To prevent collisions and ensure uniqueness, salts should be at least 32 bits in length and selected randomly for each instance. | All Classifications | **Should** \[NZISM CID:6562\] |

**4.1.5 Symmetric Encryption Algorithms**

The table provides guidelines for the use of Electronic Code Book (ECB) mode in symmetric encryption algorithms. It advises against the use of ECB mode due to vulnerabilities associated with repeated patterns in plaintext.

| **Cryptographic Method** | **Guidelines** | **Control System Classifications** | **Compliance** |
| --- | --- | --- | --- |
| ECB Mode | Should Not | All Classifications | \[NZISM CID:2158\]  <br>Agencies using endorsed algorithms like AES should avoid Electronic Code Book (ECB) mode to prevent vulnerabilities linked to repeated patterns in plaintext. |
|     |

**5\. Cryptographic Protocols:**

The below table presents guidelines for cryptographic protocols TLS, SSH, S/MIME, OpenPGP Message Format, and IPSec. It emphasizes the importance of using endorsed cryptographic protocols to mitigate security risks. Compliance with these guidelines’ is **SHOULD** for all classifications according to \[NZISM CID:2520\].

| **Protocol** | **Compliance** |
| --- | --- |
| TLS | Should |
| Secure Shell (SSH) | Should |
| S/MIME | Should |
| OpenPGP Message Format | Should |
| IPSec | Should |

_Compliance with these measures is essential for ensuring secure communication practices across all system classifications._

**5.1 Transport Layer Security (TLS)**

The below table outlines guidelines and compliance standards for implementing Transport Layer Security (TLS) as an Endorsed cryptographic protocol. It provides a comprehensive overview of TLS usage conditions, product usage requirements, and background information on SSL/TLS protocols. Additionally, it highlights the rationale behind TLS adoption and discontinuation of SSL, along with control system classifications and compliance directives for agencies.

| **Cryptographic Method** | **Guidelines** | **Control System Classifications** | **Compliance** |
| --- | --- | --- | --- |
| Transport Layer Security (TLS) | TLS implemented correctly as Endorsed protocol.  <br>**Scope (NZISM 3.7 17.4.2):** Covers TLS usage conditions; FTP over SSL/TLS within scope.  <br>\- **Product Usage:** TLS product usage requires reference to NZISM 3.7, Section 17.3 on endorsed Cryptographic Protocols.  <br>**Gateway Handling:** Guidance on TLS traffic handling in NZISM 3.7, Section 14.3 - Web Applications.  <br>**<br>Background Protocol Overview:  <br>SSL and TLS provide internet communication security.  <br>**\- Use certificates and asymmetric cryptography.  <br>\- Encryption ensures data confidentiality and integrity.  <br>\- Various versions widely used in web browsing, email, etc.  <br>\- TLS evolved from SSL; TLS 1.3 latest version. Protocol **Distinction:** TLS and SSL are distinct protocols.  <br><br/>**Protocol Development:  <br>TLS development history and versions. SSL Discontinuation:**  <br>\- SSL 3.0 vulnerability (POODLE attack) led to SSL discontinuation.  <br>\- SSL superseded by TLS, specifically TLS 1.3.  <br>\- SSL no longer Endorsed cryptographic protocol;  <br>**TLS recommended. Rationale:  <br>**\- SSL version 1.0 was never released; version 2.0 had significant security flaws, leading to SSL 3.0.  <br>\- SSL superseded by TLS, with TLS 1.3 being the latest version (August 2018).  <br>\- SSL no longer Endorsed cryptographic protocol. | All Classifications | **Should** \[NZISM CID:2598\]  <br>Agencies advised to use TLS current version (1.3).  <br><br/>**Should Not** \[NZISM CID:2600\]  <br>Agencies advised against using any version of SSL. |

**5.2 Secure Shell (SSH)**

The below table provides guidelines and compliance directives for **Secure Shell (SSH)** implementation as an endorsed cryptographic protocol. It outlines recommended settings to ensure secure usage of SSH in compliance with NZISM standards, aiming to mitigate vulnerabilities and unauthorised access risks.

<table><tbody><tr><th><p><strong>Cryptographic Method</strong></p></th><th><p><strong>Guidelines</strong></p></th><th><p><strong>Control System Classifications</strong></p></th><th><p><strong>Compliance</strong></p></th></tr><tr><td><p>SSH</p></td><td><ul><li>SSH software enables secure connections to remote systems.</li><li>Applicable for both commercial and open-source implementations.</li><li>Includes Secure Copy (SCP) and Secure File Transfer Protocol (SFTP).</li><li>Compliance requirements detailed in NZISM 3.7, Section 17.3.</li></ul></td><td><p>All Classifications</p></td><td><p><strong>Agencies should implement the following settings for SSH usage:</strong><br></p><ul><li>Utilise SSH version 2 to mitigate vulnerabilities to middle attacks.<br></li><li>Carefully control SSH forwarding capabilities to prevent unauthorised access to sensitive data.<br></li><li>Avoid host-based authentication to mitigate the risk of IP spoofing.<br></li><li>Refrain from using administrator login or privilege escalation to prevent severe consequences. [NZISM CID:2647]</li></ul></td></tr></tbody></table>

**Below table provides Secure SSH Configuration Directives:**

| **Configuration description** | **Configuration directive** |
| --- | --- |
| Disallow the use of SSH version 1 | Protocol 2 |
| On machines with multiple interfaces, configure the SSH daemon to listen only on the required interfaces | ListenAddress  <br>xxx.xxx.xxx.xxx |
| Disable connection forwarding | AllowTCPForwarding no |
| Disable gateway ports | Gatewayports no |
| Disable the ability to login directly as root | PermitRootLogin no |
| Disable host-based authentication | HostbasedAuthentication no |
| Disable rhosts-based authentication | RhostsAuthentication no  <br>IgnoreRhosts yes |
| Do not allow empty passwords | PermitEmptyPasswords no |
| Configure a suitable login banner | Banner/directory/filename |
| Configure a login authentication timeout of no more than 60 seconds | LoginGraceTime xx |
| Disable X forwarding | X11Forwarding no |

**Secure SSH Authentication and Access Controls:**

The below table outlines secure authentication mechanisms and access controls for SSH (Secure Shell) protocols, ensuring robust security practices within systems:

| **Authentication Mechanisms** | **Guidelines** | **Control** |
| --- | --- | --- |
| Public Key Authentication | Provides stronger authentication compared to password-based schemes. | Public key-based authentication should precede password-based authentication. \[NZISM CID:2672\]  <br><br/>Techniques to block brute force attacks against passwords should be employed. \[NZISM CID:2673\] |
| Password Vulnerability | Susceptible to guessing attacks; countermeasures needed to mitigate brute force attacks. |
| Automated Remote Access | Password-less Authentication (Rationale) | Parameter checking recommended for 'forced command' option. \[NZISM CID:2725\] |
| Access from unknown IP addresses allows untrusted parties automatic authentication.  <br><br/>Improperly configured port forwarding could facilitate unauthorised access.  <br><br/>Enabled forwarding could compromise authentication credentials.  <br><br/>Provides unrestricted access to restricted functions. | Automated login without passwords should disable unnecessary access and forwarding options. \[NZISM CID:2726\] |
|     |
|     |
|     |

**Endorsed SSH Security Best Practices and Controls:**

The below table provides an overview of recommended practices and controls related to SSH (Secure Shell) agent and SSH versions as outlined in the New Zealand Information Security Manual (NZISM 3.7) Control Identification (CID) framework.

| **Feature** | **Description** |
| --- | --- |
| **SSH-agent Key Caching (Rationale)** | \- SSH-agent securely manages private keys, reducing exposure risks. &lt;br&gt; - Agent credential forwarding is necessary for multiple SSH connections. |
| **Controls** | \- Use SSH-agent only on secured workstations with screen locks. &lt;br&gt; - Set key cache expiration within four hours of inactivity. &lt;br&gt; - Enable agent credential forwarding for secure traversal. \[NZISM CID:2737\] |
| **SSH Versions (Rationale)** | \- Older versions of SSH may contain known vulnerabilities; upgrading to the latest versions is recommended. |
| **Control** | \- Ensure that the latest SSH software implementation is used to mitigate known vulnerabilities. \[NZISM CID:2740\] |

**5.3 Internet Protocol Security (IPSec)**

**Ensure proper implementation of Internet Protocol Security (IPSec).**

This section outlines the conditions for utilising IPSec as an endorsed Cryptographic Protocol. Requirements for IPSec implementations are outlined in Section NZISM 3.7, 17.3 Approved Cryptographic Protocols.

**IPSec Modes of Operation:**

- IPSec can operate in two modes: transport mode or tunnel mode.

**Cryptographic Algorithms:**

- IPSec implementations support various cryptographic algorithms for data encryption when using the Encapsulating Security Payload (ESP) protocol. These may include 3DES and AES.

**Key Exchange:**

- IPSec implementations offer several methods for sharing keying material used in hashing and encryption processes. Common methods include manual keying and Internet Key Exchange (IKE) using the ISAKMP protocol. Both methods are deemed suitable for use.

**ISAKMP Authentication:**

- IPSec implementations provide options for authentication within ISAKMP, including digital certificates, encrypted nonces, or pre-shared keys. All these methods are considered appropriate for use.

**ISAKMP Modes:**

The below table outlines recommended practices and controls for configuring IPSec connections, focusing on aspects like mode of operation, cryptographic protocols, security association lifetimes, HMAC algorithms, DH groups, perfect forward secrecy, and IKE extended authentication. Rationales provide insights into the security considerations behind each recommendation, while controls specify the actions agencies should take to ensure secure IPSec implementations.

| **ISAKMP Modes** | **Rationale & Controls** |
| --- | --- | --- |
| Mode of Operation | **Rationale:** The tunnel mode provides full encapsulation of IP packets. |
| **Rationale:** The transport mode encapsulates only the payload of the IP packet. |
| **Control:** Agencies **SHOULD** use tunnel mode for IPSec connections. |
| **Control:** Agencies using transport mode **SHOULD** use an IP tunnel for IPSec. \[NZISM CID:2842 (Control), 2843 (Control)\] |
| Protocol | **Rationale:** ESP is generally preferred for authentication. |
| **Rationale:** AH and ESP can provide authentication for the IP packet and payload. |
| **Control:** Agencies **SHOULD** use the ESP protocol for IPSec connections. \[NZISM CID:2847 (Control)\] |
|     |
| ISAKMP Modes | **Rationale:** Main mode provides greater security since all exchanges are protected. |     |
| **Control:** Agencies **SHOULD** disable aggressive mode for IKE. \[NZISM CID:2850 (Control)\] |     |
|     |
| Security Association | **Rationale:** A secure association lifetime of four hours provides a balance between security and usability. |     |
| Lifetimes | **Control:** Agencies **SHOULD** use a security association lifetime of four hours or less. \[NZISM CID:2853 (Control)\] |     |
|     |
| HMAC Algorithms | **Rationale:** MD5 and SHA-1 are no longer Endorsed. |     |
| **Control:** Agencies **SHOULD** use HMAC-SHA256, HMAC-SHA384, or HMAC-SHA512. \[NZISM CID:2856 (Control)\] |     |
|     |
| DH Groups | **Rationale:** Larger DH groups provide more entropy for key exchange. |     |
| **Control:** Agencies **SHOULD** use the largest modulus size available for DH. \[NZISM CID:2859 (Control)\] |     |
|     |
| Perfect Forward Secrecy | **Rationale:** Reduces the impact of a compromise. |     |
| **Control:** Agencies **SHOULD** use Perfect Forward Secrecy for IPSec. |     |
|     |
| IKE Extended Authentication | **Rationale:** XAUTH using IKEv1 has documented vulnerabilities. |     |
| **Control:** Agencies **SHOULD** disable XAUTH for IPSec connections using IKEv1. \[NZISM CID:2865 (Control)\] |     |
|     |

**6\. Digital Signatures**

Digital signatures play a critical role in verifying the authenticity and integrity of data.

**_Strategies:_**

1. **Public Key Infrastructure (PKI):**
    - Deploy a robust **Public Key Infrastructure (PKI)** for managing digital certificates and signatures.
    - Utilize **X.509** **certificates** as the standard for creating and verifying digital signatures.
2. **Hash-Based Signatures:**
    - Generate hash values of the data to be signed using cryptographic hash functions.
    - Sign the hash values using private keys to create digital signatures.
    - Verify the authenticity and integrity of signatures by using the corresponding public keys for signature verification.

**7\. Key Management**

Cryptographic keying material **MUST** be protected by key management procedures, ensuring the security of sensitive cryptographic assets. The following points outline the key aspects covered in this section:

**Cryptographic key protection:**

- - Cryptographic keying material **MUST** be safeguarded through robust key management procedures to prevent unauthorised access or compromise.

**Scope:**

- - This section provides guidance on the establishment and implementation of key management procedures to protect cryptographic keying material.
    - Key management procedures are essential for all cryptographic systems, ensuring the confidentiality, integrity, and availability of cryptographic keys.
    - Compliance with established key management standards and practices is MUST for all agencies handling cryptographic keying material.
    - The scope includes recommendations for the secure generation, storage, distribution, use, and disposal of cryptographic keys to mitigate security risks effectively.

**Key management lifecycle:**

- - Key management procedures cover the entire lifecycle of cryptographic keys, from their creation and distribution to their eventual retirement or destruction.
    - Effective key management practices ensure the ongoing security and reliability of cryptographic systems, protecting against unauthorized access or misuse of cryptographic keying material.

**Key Management Guidelines:**

- - Guidelines for effective key management encompass implementing strong encryption algorithms, secure key storage mechanisms, access controls, and regular key rotation.
    - Continuous monitoring and auditing of key management procedures are essential to detect and respond to any security incidents or breaches promptly.

**Compliance:**

- - Adherence to key management procedures outlined in this section is **MUST** for all agencies handling cryptographic keying material, ensuring compliance with established security standards and regulations.

**7.1 Key Management Life Cycle**

**The key management lifecycle includes:**

| **Key generation** | **Distribution** | **Installation** |
| --- | --- | --- |
| **Registration** | **Use** | **Rotation** |
| **Secure storage** | **Backup** | **Replacement** |
| **Reissue** | **Recovery** | **Revocation** |
| **Suspension** | **Retirement** | **Destruction** |

**Secure Key Exchange in Open Networks:**

**Open Networks**

- - - Protocols and trusted agents facilitate key exchange in open networks, emphasizing the use of endorsed protocols and algorithms specified in the document.

**Public Key Infrastructure (PKI)**

- - - PKI is crucial for creating, issuing, managing, and revoking digital certificates and their associated cryptographic keys, supporting various applications including encryption, digital signing, and confidentiality.

**Outsourcing Key Management**

- - - The goal of key management, whether within an organisation or in the cloud, is to enable data encryption by securely managing cryptographic keys using cryptography and secure hardware.
      - Understanding the differences between ownership, control, and possession is essential for evaluating key management solutions that meet agency requirements and these are defined as follows:

| **Ownership** | **Specifies to whom the cryptographic keys belong. This is usually the custodian. Ownership of the key applies to the owner of the encrypted data, the owner of the encryption and/or decryption process, and the owner of the key infrastructure.** |
| --- | --- |
| Control | Specifies who carries out key management lifecycle tasks, including having the option of precluding others from doing these tasks. |
| Possession | Specifies ownership of the infrastructure or location where the keys and encrypted data physically reside. |

**Risks**

**Risks associated with cryptographic key management include:**

- Exposure of keys to unauthorised persons or applications, potentially compromising the keys or the data they encrypt.
- Loss or irrecoverable loss of cryptographic keys.
- Limited protection provided by software-based key management.
- Fragmentation of key management due to changes in systems, such as alterations in the custody of hardware outside trusted environments.
- Poorly documented and understood key management processes, increasing the risk of compromise and potential compliance costs.
- Inadequate separation of duties within key ownership, control, and possession, potentially leading to unauthorized access to sensitive data.
- Lack of interoperability if an agency's key management infrastructure is incompatible with that of a cloud service provider.

To determine the most suitable key management option for security and business requirements, several factors should be assessed together, including scenario, consideration, risk, business and/or security priority, and outsourcing aspect.

| **Scenario** | **Consideration** | **Risk** | **Security and/or business priority** | **Outsource aspect** |
| --- | --- | --- | --- | --- |
| Agency generated and management of encryption keys including its storage. | Inadequate separation of duties within the ownership, control, and possession of keys, resulting in non-compatible duties being allocated to the same party, potentially resulting in unauthorised access of tenancy data. | Keys exposed to unauthorised persons or applications, potentially compromising the keys or data the encryption is protecting. | Sensitivity and value of the data. This is summarised by the classification of the data but may not always reflect the values of aggregation, cost of compliance breaches, or reputation damage from a breach. | Control |
| Agency generates the key, and it is migrated to a cloud where the provider can use the keys to perform encryption and decryption operations. | Whether the key management solution can be integrated with other data storage services. | Lack of interoperability if an agency’s key management infrastructure is not compatible with that offered by a cloud service provider. | The variety of key types, data formats, algorithms, protocols, and sources. | Possession |
| Cloud provider generates, manages, and stores keys used to encrypt and decrypt data. | Whether an externally generated key provides sufficient assurance than if the key was generated using on premises infrastructure. | Poorly documented and understood key management processes and activities increasing the possibility of compromise and potentially increasing compliance costs. | Sensitivity and value of the data. This is summarised by the classification of the data but may not always reflect the value of aggregation, cost of compliance, breaches, or reputation damage from a breach. | Ownership |

**Prioritisation**

Prioritisation is crucial for identifying and managing the requirements of cryptography and key management systems. It helps determine the scope and complexity of the key management program.

**Key considerations include:**

- Sensitivity and value of the data, often reflected in its classification, but also encompassing factors such as aggregation value, compliance breach costs, and reputational damage from breaches.
- Volume of data and keys involved.
- Diversity of key types, data formats, algorithms, protocols, and sources.
- Speed and frequency of transactions, along with requirements for data access and availability.

**Rationale & Controls Developing Key Management Plans**

Rationale Most modern cryptographic systems are designed to be highly resistant to cryptographic analysis, and it should be assumed that a determined attacker could obtain details of the cryptographic logic. Cryptographic system material is safeguarded by implementing a **Key Management Plan (KMP)** encompassing personnel, physical, and information security.

Rationale Depending on the security requirements of an agency, different key management models or combination of models may be adopted to allocate the ownership, control, and possession for keys. It should be noted that the greater the sharing model adopted the less control of keys an agency may have.

**Control System Classifications(s):** **All Classifications; Compliance: Should** \[NZISM CID:3016\] Agencies **SHOULD** assess the risks associated around key ownership, possession, and control against their own security and business requirements.

**Control System Classifications(s):** **All Classifications; Compliance: Should** \[NZISM CID:3018\] Agencies **SHOULD** develop a KMP when they have implemented a cryptographic system using commercial grade cryptographic equipment.

**Control System Classifications(s):** **All Classifications; Compliance: Must** \[NZISM CID:3017\] The level of detail included in a KMP **MUST** be consistent with the criticality and classification of the information to be protected.

**Contents of Key Management Plans**

Rationale When agencies implement the recommended contents for KMPs they will have a good starting point for the protection of cryptographic systems and their material within their agencies.

**Control System Classifications(s):** **All Classifications; Compliance: Should** \[NZISM CID:3021\]

The table below describes the minimum contents which **SHOULD** be documented in the KMP.

<table><tbody><tr><th><p><strong>Topic&nbsp;</strong></p></th><th><p><strong>&nbsp;Content</strong></p></th></tr><tr><td><p><strong>Objectives</strong></p></td><td><ul><li>Objectives of the cryptographic system and KMP, including organisational aims.</li><li>Refer to relevant NZCSIs.</li></ul></td></tr><tr><td><p><strong>System description</strong></p></td><td><ul><li>The environment.</li><li>Maximum classification of information protected.</li><li>Topology diagram(s) and description of the cryptographic system topology including data flows.</li><li>The use of keys.</li><li>Key algorithm.</li><li>Key length.</li><li>Key lifetime.</li></ul></td></tr><tr><td><p><strong>Roles and administrative responsibilities</strong></p></td><td><ul><li>Documents roles and responsibilities, including, if relevant, the COMSEC custodian, cryptographic systems administrator, record keeper, cloud service provider, and auditor.</li></ul></td></tr><tr><td><p><strong>Accounting</strong></p></td><td><ul><li>How accounting will be undertaken for the cryptographic system.</li><li>What records will be maintained.</li><li>How records will be audited.</li></ul></td></tr><tr><td><p><strong>Classification</strong></p></td><td><ul><li>Classification of the cryptographic system hardware.</li><li>Classification of cryptographic system software.</li><li>Classification of the cryptographic system documentation.</li></ul></td></tr><tr><td><p><strong>Information security incidents</strong></p></td><td><ul><li>A description of the conditions under which compromise of key material should be declared.</li><li>References to procedures to be followed when reporting and dealing with information security incidents.</li></ul></td></tr><tr><td><p><strong>Key management</strong></p></td><td><ul><li>Who generates keys?</li><li>How keys are delivered.</li><li>How keys are received.</li><li>Key distribution, including local, remote, and central.</li><li>How keys are installed.</li><li>How keys are transferred.</li><li>How keys are stored.</li><li>How keys are recovered.</li><li>How keys are revoked.</li><li>How keys are destroyed.</li><li>Each time key information or material is accessed, details are captured in logs.</li><li>Endorsed access lists to cryptographic keys.&nbsp;</li></ul></td></tr><tr><td><p><strong>Maintenance</strong></p></td><td><ul><li>Maintaining the cryptographic system software and hardware.</li><li>Destroying equipment and media.</li></ul></td></tr><tr><td><p><strong>References</strong></p></td><td><ul><li>Vendor documentation.</li><li>Related policies.</li></ul></td></tr></tbody></table>

**Accounting**

As cryptographic equipment, and the keys they store, provide a significant security function for systems it is important that agencies are able to account for all cryptographic equipment.

**Control System Classifications(s): Secret, Confidential, Top Secret; Compliance: Must \[NZISM CID:3024\]**

Agencies **MUST** be able to readily account for all transactions relating to cryptographic system material including identifying hardware and all software versions issued with the equipment and materials, including date and place of issue.

**Control System Classifications(s): All Classifications; Compliance: Should \[NZISM CID:3025\]**

Agencies **SHOULD** be able to readily account for all transactions relating to cryptographic system material including identifying hardware and all software versions issued with the equipment and materials, including date and place of issue.

**  
7.2 Hybrid Solution for Key Management System (KMS)**

**Benefits:**

1. **Flexibility:** A hybrid KMS offers the flexibility to combine on-premises and cloud-based key management, catering to diverse organizational needs.
2. **Scalability:** It provides scalability by leveraging cloud resources for dynamic cryptographic demands while retaining critical functions on-premises.
3. **Enhanced Security:** Hybrid KMS enhances security through a layered approach, combining on-premises controls with advanced cloud security measures.
4. **Cost Efficiency:** Organizations can optimize costs by utilizing cloud services for non-sensitive workloads, reducing upfront infrastructure investment.

**Considerations:**

1. **Interoperability:** Ensure seamless integration between on-premises and cloud components for effective key exchange and management.
2. **Compliance:** Address data residency requirements and regulatory compliance in hybrid environments.
3. **Key Lifecycle Management:** Implement consistent policies for key generation, distribution, rotation, and disposal across hybrid infrastructure.
4. **Monitoring and Auditing:** Deploy robust monitoring and auditing mechanisms to detect security incidents and ensure accountability.

**Inclusion in Standards:**

Cryptographic standards **SHOULD** incorporate guidelines for hybrid KMS integration, emphasizing interoperability, security, and compliance. This ensures standardized approaches to key management and encryption, enhancing overall cybersecurity posture.

**7.3 High Assurance Cryptographic Equipment**

These are the specialized cryptographic systems designed for critical applications where confidentiality, integrity, and availability are of utmost importance. Agencies use HACE to protect sensitive information and ensure secure communication.

**Following table presents the compliant best practices when utilising HACE:**

| **Topic** | **Description** | **Compliance** |
| --- | --- | --- |
| **High Assurance Cryptographic Equipment** | The NZCSI documents provide specific policies tailored to High Assurance Cryptographic Equipment (HACE). | **Must** <br><br>(NZISM CID:3043) Agencies **MUST** adhere to NZCSI standards when utilizing HACE. |
| **Transporting Commercial Grade Equipment** | Transporting commercial grade cryptographic equipment while in a keyed state poses risks of interception and compromise of the stored key. Such transportation should align with the requirements corresponding to the classification of the key within the equipment. | **Must** <br><br>(NZISM CID:3048) Unkeyed commercial grade cryptographic equipment **MUST** be distributed and managed using endorsed methods for handling government property.<br><br>(NZISM CID:3050) Keyed commercial grade cryptographic equipment **MUST** be distributed, managed, and stored using endorsed methods for handling government property, with procedures aligned with the classification of the key within the equipment.<br><br>(NZISM CID:3053) Agencies **SHOULD NOT** transport commercial grade cryptographic equipment or products while in a keyed state. |

**7.4 Hardware Security Modules (HSM)**

This section provides information on **Hardware Security Modules (HSMs)**, with detailed key management guidance available in **Section 17.9 – Key Management - NZISM**.

**Hardware Security Module**

- **Definition**: Hardware Security Modules (HSMs) are specialized hardware devices designed to offer cryptographic functions.
- **Forms**: HSMs can be integrated into a design, installed in a host, or connected externally. **They are available in various forms, including:**
  - Discrete appliances
  - PCI cards
  - USB devices
  - Smartcards

**Functions**

**HSMs perform the following essential cryptographic functions:**

- **Encryption and Decryption**: Securely handle encryption and decryption operations.
- **Key Generation**: Generate cryptographic keys.
- **Signing**: Create digital signatures.
- **Hashing**: Perform hash functions.
- **Cryptographic Acceleration**: Enhance cryptographic performance.
- **Physical Tamper-Resistance**: HSMs typically provide some level of physical tamper-resistance.
- **User and Programmable Interfaces**: HSMs offer interfaces for key management, configuration, and firmware or software updates.

**Usage**

**HSMs find application in the following scenarios:**

- **High Assurance Security Solutions**: Employed in security-critical environments adhering to established cryptographic system standards.
- **Traditional Applications**:
  - Automatic teller machines (ATMs)
  - Electronic fund transfer systems
  - Point-of-sale networks
- **PKI Deployments**: Secure Certificate Authority (CA) keys.
- **SSL Acceleration**: Enhance SSL/TLS performance.
- **DNSSEC Implementations**: Play a role in securing DNS infrastructure.

**Physical Security**

- HSMs are encapsulated multi-chip modules, devices, cards, or appliances.
- Robust physical security measures include:
  - **Tamper Resistance**: Encasing boards and components in a resin that destroys encapsulated components upon tampering.
  - **Tamper Evidence**: Utilizing seals and labels that break or reveal a message upon tampering. Regular inspection or audit mechanisms may be necessary.
  - **Tamper Detection**: Features detecting and reporting tampering attempts (e.g., conductive mesh within the package).
  - **Tamper Response**: HSMs can activate defensive measures upon detecting tampering, but this trade-off affects availability.

**Rationale & Controls - Hardware Security Modules**

**Rationale**

- When **high assurance** or **high security** is required, especially when dealing with **high volumes of encrypted or decrypted data**, the use of an **HSM** should be considered during the design of network and security architectures.

**Controls**

1. **Agencies MUST consider the use of HSMs**:
    - During **security risk assessments**.
    - When **designing network and security architectures**.
    - Especially for agencies operating within **Top Secret**, **Confidential**, or **Secret** classifications (NZISM CID: 3103).
2. **Agencies within Confidential, Secret, and Top Secret classifications MUST adhere to the following**:
    - **Product selection guidance** provided in **NZISM 3.7 manual** (NZISM CID: 3105).
3. **Regardless of classification**, all agencies are advised to:
    - Deliberate on the **potential incorporation of HSMs** during security risk assessments or when designing network and security architectures (NZISM CID: 3108).
    - **Follow the product selection guidance** outlined in **NZISM 3.7 manual** (NZISM CID: 3110). Refer to **Chapter 12 – Product Security** for detailed information.

**8\. Audit and Compliance**

Given the critical security role played by cryptographic equipment and the keys they hold, it is essential for agencies to maintain a comprehensive account of all cryptographic equipment.

**Control Requirements**

**1\. Compliance for All Classifications (Must) \[NZISM CID: 3024\]**

Agencies **MUST** have the capability to readily document all transactions related to cryptographic system materials, including:

- Identifying hardware and software versions issued.
- Recording dates and places of issue.

**2\. Compliance for All Classifications (Should) \[NZISM CID: 3025\]**

Agencies **SHOULD** have the capability to easily document all transactions associated with cryptographic system materials, including:

- Identifying hardware and software versions issued.
- Recording dates and places of issue.

**Audits, Compliance, and Inventory Checks**

**Reasoning**

Cryptographic system audits are crucial for ensuring accountability and security.

**3\. Compliance for All Classifications (Must) \[NZISM CID: 3028\]**

Agencies **MUST** conduct audits using two personnel with cryptographic system administrator access.

**4\. Compliance for All Classifications (Should) \[NZISM CID: 3029\]**

Agencies **SHOULD** conduct audits of cryptographic system materials:

1. During handover or takeover of administrative responsibility for the cryptographic system.
2. Upon change of personnel with access to the cryptographic system.
3. At least annually.

**5\. Compliance for All Classifications (Should) \[NZISM CID: 3030\]**

Agencies **SHOULD** perform audits to:

1. Account for all cryptographic system materials.
2. Verify that the agreed security measures documented in the Key Management Plan (KMP/S) are being followed.

**Access Register**

- **Overview**: Access registers serve as valuable tools for documenting personnel with privileged access to cryptographic systems and tracking relevant activities.
- **Control System Classifications(s)**: All Classifications
- **Compliance**: **Must** \[NZISM CID:3033\]
- **Requirements**:
  - Agencies **MUST** maintain an **access register** recording cryptographic system information, including details of personnel with system administrator access, withdrawals of such access, system documents, accounting activities, and audit activities.

**Cryptographic System Administrator Access**

- **Role Significance**: The cryptographic system administrator role entails significant privileges, necessitating stringent security measures.
- **Control System Classifications(s)**: All Classifications
- **Compliance**: **Must** \[NZISM CID:3036\]
- **Criteria for Granting Access**:
  - Before granting cryptographic system administrator access, agencies **MUST** ensure that personnel meet specific criteria, including:
    - A demonstrated need for access.
    - Compliance with relevant policies.
    - Appropriate security clearance.
    - Protection of authentication information.
    - Agreement to responsibilities.
    - Completion of requisite training.

**Area Security and Access Control**

- **Reasoning**: Due to the sensitivity of cryptographic equipment, additional physical security measures are warranted.
- **Control System Classifications(s)**: All Classifications
- **Compliance**: **Should** \[NZISM CID:3039\]
- **Storage Requirements**:
  - Cryptographic system equipment **SHOULD** be stored in a room meeting the requirements for a server room appropriate to the classification of information processed by the cryptographic system.
- **Controlled Cryptography Areas**:
  - Areas where cryptographic system material is used **SHOULD** be separated from other areas and designated as controlled cryptography areas.

**9\. Appendices**

**Appendix A: Cryptographic Algorithms and Protocols**

1. **Endorsed Cryptographic Algorithms**:

**Asymmetric/Public Key Algorithms:**

- - ECDH (Elliptic Curve Diffie-Hellman): Used for agreeing on encryption session keys.
    - ECDSA (Elliptic Curve Digital Signature Algorithm): Employed for digital signatures.
    - DH (Diffie-Hellman): Recommended for agreeing on encryption session keys, especially for interoperability with third parties where ECDH is not supported.
    - RSA: Used for digital signatures and passing encryption session keys or similar keys.
    - DSA (Digital Signature Algorithm): Deprecated and only allowed for legacy use1.

**Hashing Algorithms:**

- - SHA-2 (Secure Hashing Algorithm 2): Specifically, SHA-384 and SHA-512 are approved for current use.
    - SHA-1 (Secure Hashing Algorithm 1): Deprecated and allowed only for legacy systems2.

**Symmetric Encryption Algorithms:**

- - AES (Advanced Encryption Standard): Recommended for data encryption using key lengths of at least 256 bits.
    - 3DES (Triple Data Encryption Standard): Deprecated and permitted only for legacy use1.

_\*Reference: NZISM Section 17.2._

1. **Endorsed Cryptographic Protocols**:

**TLS (Transport Layer Security):**

- - Used for securing data transmission over networks. It ensures confidentiality, integrity, and authentication of communication channels1.

**Secure Shell**

- - **SSH (Secure Shell):** Primarily used for secure remote access to servers and devices. It provides encrypted communication and secure authentication1.
    - **S/MIME (Secure/Multipurpose Internet Mail Extensions):** Employed for securing email communication. It ensures confidentiality, integrity, and authentication of email messages1.

**Pretty Good Privacy**

- - **OpenPGP Message Format:** Used for secure email communication, especially for digital signatures and encryption. It’s commonly associated with PGP (Pretty Good Privacy)1.

**IPsec**

- - **IPSec (Internet Protocol Security):** Provides security services for IP packets, including encryption, authentication, and integrity. It’s commonly used for VPNs (Virtual Private Networks).

_\*Reference: NZISM Section 17.3._

**Appendix B: Key Management Procedures**

1. **Key Generation and Distribution Procedures**:
    - Detailed steps for generating cryptographic keys.
    - Secure distribution to authorised users.
    - Reference: NZISM Section 17.9.8.
2. **Key Storage and Protection Procedures**:
    - Best practices for secure key storage.
    - Use of HSMs, secure containers, and access controls.
    - Reference: NZISM Section 17.9.5.
3. **Key Rotation and Retirement Procedures**:
    - Steps for regular key rotation.
    - Secure retirement and destruction of unused keys.
    - **Reference:** NZISM Section 17.9.10.

**Appendix C: Cloud Transition Plan**

1. **Assessment of Cloud Providers**:
    - Criteria for evaluating cloud providers’ key management capabilities.
    - Reference: Cloud provider documentation.
2. **Data Migration Strategies**:
    - Secure migration of existing keys to cloud KMS.
    - **Reference:** NZISM Section 17.9.8 for re-keying guidance.

**Appendix D: Key Management Best Practices**

1. **Key Generation and Distribution Best Practices**:
    - Follow the steps outlined in Section 17.9.8 of NZISM for generating strong cryptographic keys.
    - Document key metadata (purpose, expiration date, etc.).
    - Distribute keys securely to authorized users.
    - Use secure channels for key distribution.
2. **Key Storage and Protection Best Practices**:
    - Store keys securely using hardware security modules (HSMs) or secure containers.
    - Implement access controls and regular audits.
    - Follow NZISM Section 17.9.5 for secure key storage practices.
3. **Key Rotation and Retirement Best Practices**:
    - Regularly rotate keys (e.g., annually) to prevent long-term exposure.
    - Securely retire and destroy unused keys.

**10\. References & Bibliography**

- 1. **Related Documents**

**Health Information Security Framework (HISF)**:

- - **HISO 10029.1:2023, HISO 10029.4: 2023:** Health Information Security Framework Guidance for Hospitals and its service providers. This framework establishes standards and requirements for securing health information in New Zealand, ensuring confidentiality, integrity, and availability.

**New Zealand Information Security Manual (NZISM 3.7)**:

- - Section 17.2: Endorsed Cryptographic Algorithms
    - Section 17.3: Endorsed Cryptographic Protocols
    - Section 17.9.5: Key Storage and Protection
    - Section 17.9.8: Key Strength Recommendations
    - Section 17.9.10: Key Compromise Scenarios

**Protective Security Requirements (PSR)**:

- - Relevant sections related to information security and key management.

**NIST:**

- - NIST Cryptographic Standards: NIST Cryptographic Standards.
    - NZISM Key Management Guidelines: NZISM Key Management.

    1. **Acronyms**

| **NZISM** | New Zealand Information Security Manual |
| --- | --- |
| **PSR** | Protective Security Requirements |
| **HISO** | Health Information Standards Organization |
| **TLS** | Transport Layer Security |
| **SSH** | Secure Shell |
| **IPSec** | Internet Protocol Security |

- 1. **Definitions**

| **Cryptography** | The practice and study of techniques for secure communication and data protection, as per the guidelines outlined in NZISM and HISO. |
| --- | --- |
| **Encryption** | The process of converting information into code to prevent unauthorized access, aligning with PSR requirements for safeguarding government information. |
| **Hashing** | The transformation of data into a fixed-size string of characters, typically for data integrity verification, as prescribed by HISO standards. |
| **Key Management** | The process of generating, storing, and distributing cryptographic keys securely, in accordance with NZISM and PSR guidelines. |
| **Salting** | Adding random data to hashed passwords to prevent dictionary attacks, as recommended by HISO for protecting health information. |

- 1. **Document Management**

**10.4.1 Distribution**

| Date | Governance Group | Version |
| --- | --- | --- |
|     |     |     |
|     |     |     |
|     |     |     |
|     |     |     |
|     |     |     |
|     |     |     |

**10.4.2 Document Version**

**10.4.3 Template Version**

| Date | Author | Summary of Changes | Version |
| --- | --- | --- | --- |
| 22 Dec 23 | Abdul Haq Mohammed | Initial creation |     |
|     |     |     |     |
|     |     |     |     |