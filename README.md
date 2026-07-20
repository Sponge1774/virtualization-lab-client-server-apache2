# 🖥️ virtualization-lab-client-server-apache2

🌐 **Idioma / Language:** [Português](#-português) | [English](#-english)

---

## 🇧🇷 Português

Laboratório de virtualização com **Oracle VirtualBox 7.1**, simulando um ambiente cliente-servidor Linux com **Ubuntu Desktop 24.04.1 LTS** e servidor web **Apache2**, desenvolvido para a disciplina *Development Tools & Cloud Computing* — Centro Universitário UniFECAF (Análise e Desenvolvimento de Sistemas).

> 🎓 Trabalho avaliado com nota máxima (8/8) — [feedback do tutor incluído no relatório](#-avaliação).

---

### 📋 Sobre o Projeto

O desafio proposto simula uma situação real de suporte técnico: um cliente com dificuldades para implementar um WebServer Linux virtualizado. Para resolver isso, foi montado um laboratório com **duas máquinas virtuais**:

| VM | Papel | Usuário | Hostname | IP | RAM | Disco |
|---|---|---|---|---|---|---|
| `Ubuntu_Cliente` | Cliente | `eduardo-souza-mattos` | eduardo-souza-mattos-VirtualBox | `192.168.15.16` | 4 GB | 20 GB |
| `Ubuntu_Server` | WebServer | `esmattos` | esmattosserver | `192.168.15.4` | 4 GB | 40 GB |

**Máquina hospedeira:** Samsung Expert 2018 · SSD 240 GB · 12 GB RAM · Pop!_OS · VirtualBox 7.1 · rede em modo Bridge (wlp3s0).

O servidor foi configurado com **Apache2**, servindo uma página HTML de mini currículo em `/var/www/html/index.html`, acessada com sucesso pelo cliente via navegador.

---

### 🧰 Stack Utilizada

- **Hipervisor:** Oracle VirtualBox 7.1
- **Sistema Operacional (Cliente e Servidor):** Ubuntu Desktop 24.04.1 LTS
- **Servidor Web:** Apache2 (systemd/systemctl)
- **Rede:** Modo Bridge (comunicação direta cliente ↔ servidor)
- **Documentação:** Python (ReportLab + Pillow) para geração do relatório em PDF

---

### 📂 Estrutura do Repositório

```
.
├── docs/
│   └── Relatorio_Virtualizacao_Eduardo_Souza_Mattos.pdf   # Relatório completo (ABNT)
├── screenshots/                                            # Capturas de tela de cada etapa
├── html/
│   └── index.html                                          # Página do mini currículo publicada no Apache2
└── README.md
```

---

### ⚙️ Passo a Passo Resumido

1. **Instalação do Oracle VirtualBox 7.1** no host (via repositório oficial + chave GPG).
2. **Criação da VM `Ubuntu_Cliente`** — 4 GB RAM, 2 CPUs, 20 GB de disco, rede Bridge.
3. **Criação da VM `Ubuntu_Server`** — 4 GB RAM, 2 CPUs, 40 GB de disco, rede Bridge.
4. **Instalação do Ubuntu 24.04.1 LTS** em ambas as VMs (instalação bare-metal via ISO).
5. **Instalação e habilitação do Apache2** no servidor:
   ```bash
   sudo apt update && sudo apt install apache2 -y
   sudo systemctl enable apache2
   sudo systemctl start apache2
   sudo systemctl status apache2
   ```
6. **Publicação da página HTML** (mini currículo) em `/var/www/html/index.html`, substituindo a página padrão.
7. **Testes de validação:**
   - `ip addr` em ambas as VMs para confirmar endereçamento.
   - `ping 192.168.15.4` do cliente para o servidor.
   - Acesso via Firefox à página padrão e, depois, à página do currículo.

---

### ✅ Resultados dos Testes

| Teste | Resultado |
|---|---|
| IP Cliente (`ip addr`) | ✔ 192.168.15.16/24 |
| IP Servidor (`ip addr`) | ✔ 192.168.15.4/24 |
| Ping cliente → servidor | ✔ 51/51 pacotes, 0% perda, RTT médio ~1,0 ms |
| Status Apache2 (`systemctl status`) | ✔ active (running) |
| Página padrão no navegador | ✔ servida com sucesso |
| Página do mini currículo | ✔ exibida com nome, área de atuação e habilidades |

---

### 📚 Fundamentação Teórica

O laboratório é contextualizado com o modelo **IaaS (Infraestrutura como Serviço)** de cloud computing: o aluno provisiona a infraestrutura (VMs, rede, SO) e instala manualmente a camada de serviço (Apache2), refletindo o funcionamento de provedores como AWS EC2, Azure VM e GCP Compute Engine.

Principais referências:
- FELTER, W. et al. *An updated performance comparison of virtual machines and Linux containers*. IEEE ISPASS, 2015.
- SHU, R. et al. *A study of security isolation techniques*. ACM Computing Surveys, v. 49, n. 3, 2017.
- ORACLE CORPORATION. *Oracle VM VirtualBox User Manual*, v. 7.1.
- CANONICAL. *Ubuntu 24.04.1 LTS (Noble Numbat) Release Notes*.
- APACHE SOFTWARE FOUNDATION. *Apache HTTP Server Version 2.4 Documentation*.

*(Referências completas em ABNT no relatório PDF, pasta `docs/`.)*

---

### 🏆 Avaliação

> **Nota: 8/8** — *"Este é um relatório de excelente qualidade técnica e acadêmica (...) Seu relatório demonstra que você compreendeu profundamente os conceitos por trás da virtualização, indo além do que era estritamente solicitado."*
> — Tutor Vitor Vieira

---

### 👤 Autor

**Eduardo Souza Mattos**
R.A.: 35984 — Análise e Desenvolvimento de Sistemas
Centro Universitário UniFECAF — 2026

---

### 📄 Licença

Projeto acadêmico de uso educacional, desenvolvido para fins de avaliação na disciplina *Development Tools & Cloud Computing*.

<br>

[⬆ Voltar ao topo](#-virtualization-lab-client-server-apache2)

---
---

## 🇬🇧 English

Virtualization lab built with **Oracle VirtualBox 7.1**, simulating a Linux client-server environment with **Ubuntu Desktop 24.04.1 LTS** and the **Apache2** web server, developed for the *Development Tools & Cloud Computing* course — UniFECAF University Center (Systems Analysis and Development).

> 🎓 Assignment graded with the maximum score (8/8) — [instructor feedback included in the report](#-evaluation).

---

### 📋 About the Project

The proposed challenge simulates a real technical support scenario: a client struggling to implement a virtualized Linux WebServer. To solve this, a lab was set up with **two virtual machines**:

| VM | Role | User | Hostname | IP | RAM | Disk |
|---|---|---|---|---|---|---|
| `Ubuntu_Cliente` | Client | `eduardo-souza-mattos` | eduardo-souza-mattos-VirtualBox | `192.168.15.16` | 4 GB | 20 GB |
| `Ubuntu_Server` | WebServer | `esmattos` | esmattosserver | `192.168.15.4` | 4 GB | 40 GB |

**Host machine:** Samsung Expert 2018 · 240 GB SSD · 12 GB RAM · Pop!_OS · VirtualBox 7.1 · Bridge network mode (wlp3s0).

The server was configured with **Apache2**, serving an HTML mini-résumé page at `/var/www/html/index.html`, which was successfully accessed by the client via browser.

---

### 🧰 Stack Used

- **Hypervisor:** Oracle VirtualBox 7.1
- **Operating System (Client and Server):** Ubuntu Desktop 24.04.1 LTS
- **Web Server:** Apache2 (systemd/systemctl)
- **Network:** Bridge mode (direct client ↔ server communication)
- **Documentation:** Python (ReportLab + Pillow) for PDF report generation

---

### 📂 Repository Structure

```
.
├── docs/
│   └── Relatorio_Virtualizacao_Eduardo_Souza_Mattos.pdf   # Full report (ABNT format)
├── screenshots/                                            # Screenshots of each step
├── html/
│   └── index.html                                          # Mini-résumé page published on Apache2
└── README.md
```

---

### ⚙️ Step-by-Step Summary

1. **Install Oracle VirtualBox 7.1** on the host (via the official repository + GPG key).
2. **Create the `Ubuntu_Cliente` VM** — 4 GB RAM, 2 CPUs, 20 GB disk, Bridge network.
3. **Create the `Ubuntu_Server` VM** — 4 GB RAM, 2 CPUs, 40 GB disk, Bridge network.
4. **Install Ubuntu 24.04.1 LTS** on both VMs (bare-metal install via ISO).
5. **Install and enable Apache2** on the server:
   ```bash
   sudo apt update && sudo apt install apache2 -y
   sudo systemctl enable apache2
   sudo systemctl start apache2
   sudo systemctl status apache2
   ```
6. **Publish the HTML page** (mini résumé) at `/var/www/html/index.html`, replacing the default page.
7. **Validation tests:**
   - `ip addr` on both VMs to confirm addressing.
   - `ping 192.168.15.4` from the client to the server.
   - Access via Firefox to the default page, then to the résumé page.

---

### ✅ Test Results

| Test | Result |
|---|---|
| Client IP (`ip addr`) | ✔ 192.168.15.16/24 |
| Server IP (`ip addr`) | ✔ 192.168.15.4/24 |
| Ping client → server | ✔ 51/51 packets, 0% loss, average RTT ~1.0 ms |
| Apache2 status (`systemctl status`) | ✔ active (running) |
| Default page in browser | ✔ served successfully |
| Mini-résumé page | ✔ displayed with name, area of expertise, and skills |

---

### 📚 Theoretical Background

The lab is framed around the **IaaS (Infrastructure as a Service)** cloud computing model: the student provisions the infrastructure (VMs, network, OS) and manually installs the service layer (Apache2), mirroring how providers such as AWS EC2, Azure VM, and GCP Compute Engine operate.

Main references:
- FELTER, W. et al. *An updated performance comparison of virtual machines and Linux containers*. IEEE ISPASS, 2015.
- SHU, R. et al. *A study of security isolation techniques*. ACM Computing Surveys, v. 49, n. 3, 2017.
- ORACLE CORPORATION. *Oracle VM VirtualBox User Manual*, v. 7.1.
- CANONICAL. *Ubuntu 24.04.1 LTS (Noble Numbat) Release Notes*.
- APACHE SOFTWARE FOUNDATION. *Apache HTTP Server Version 2.4 Documentation*.

*(Full references in ABNT format are available in the PDF report, `docs/` folder.)*

---

### 🏆 Evaluation

> **Grade: 8/8** — *"This is an excellent report in terms of technical and academic quality (...) Your report demonstrates that you deeply understood the concepts behind virtualization, going beyond what was strictly requested."*
> — Instructor Vitor Vieira

---

### 👤 Author

**Eduardo Souza Mattos**
Student ID: 35984 — Systems Analysis and Development
UniFECAF University Center — 2026

---

### 📄 License

Academic project for educational use, developed for assessment purposes in the *Development Tools & Cloud Computing* course.

<br>

[⬆ Back to top](#-virtualization-lab-client-server-apache2)
