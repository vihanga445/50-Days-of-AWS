# Day 22: Establishing Secure SSH Bridges 🔑🏗️

## 📖 The Concept
SSH Key authentication replaces vulnerable passwords with cryptographic key pairs. This is the foundation of **Infrastructure as Code (IaC)** because it allows scripts to manage servers without human intervention.

* **Private Key (`id_rsa`):** The secret key held by the client.
* **Public Key (`id_rsa.pub`):** The lock installed on the server.
* **Authorized Keys:** A list on the server that tells Linux exactly which keys are allowed to access which user account.

---

## 🏢 Business Scenario
The **Nautilus DevOps team** is preparing for automated deployments. To enable the `aws-client` (the landing host) to push updates and manage the `nautilus-ec2` instance, a secure, passwordless connection is required. By implementing RSA key-based authentication, the team ensures that only authorized automated processes can access the root environment of the new server.

---

## 🛠️ Tasks Performed

1.  **Server Provisioning:** Launched a `t2.micro` instance named `nautilus-ec2` in the `us-east-1` region.
2.  **Cryptographic Setup:** Generated a new 2048-bit RSA key pair on the `aws-client` management host.
3.  **Key Deployment:** Distributed the public key to the `/root/.ssh/authorized_keys` file on the target instance.
4.  **Security Hardening:** Set appropriate Linux permissions (`700` and `600`) to ensure the SSH service accepts the keys.
5.  **Connectivity Test:** Verified a successful root-level login without a password prompt.


To quickly check your SSH configuration for any errors, use the "verbose" mode:

```bash
ssh -v root@<EC2_IP_ADDRESS>
