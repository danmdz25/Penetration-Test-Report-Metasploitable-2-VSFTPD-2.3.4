#  Penetration Test Report - Metasploitable 2 Lab

##  Sumário Executivo

Este relatório técnico detalha o teste de penetração conduzido na máquina virtual `Metasploitable 2`, que serve como um ambiente de laboratório para testes de segurança. O objetivo principal da avaliação foi obter acesso ao sistema com os maiores privilégios.

Durante a avaliação, foi identificada e explorada uma vulnerabilidade crítica, que permitiu o acesso não autorizado ao sistema alvo como o usuário `root`.

## 🎯 Escopo da Avaliação

O escopo desta avaliação de segurança estava limitado à máquina virtual `Metasploitable 2`, com o endereço IP `192.168.56.103`, em um ambiente de rede de laboratório isolado.

## 🔬 Metodologia de Avaliação

A avaliação seguiu uma metodologia padrão de teste de penetração, que inclui as seguintes fases:

* **Reconhecimento**: Mapeamento da infraestrutura do alvo para descobrir serviços, portas abertas e versões de software.
* **Análise de Vulnerabilidade**: Identificação de falhas de segurança conhecidas no software e configuração do alvo.
* **Exploração**: Uso de uma vulnerabilidade para obter acesso não autorizado ao sistema.
* **Pós-Exploração**: Verificação do nível de acesso e exploração do sistema para obter informações adicionais.

## 🔍 Descoberta Detalhada

**Vulnerabilidade:** Execução de Comando de Backdoor no `vsftpd 2.3.4`

* **Descrição:** Durante a fase de reconhecimento, o serviço de FTP `vsftpd 2.3.4` foi identificado na porta `21`. Foi descoberto que esta versão do software contém uma vulnerabilidade de backdoor que permite a execução de comandos arbitrários no servidor.
* **Severidade:** **Crítica**. Esta falha pode ser explorada por um atacante remoto para obter controle total do sistema.
* **Passos da Exploração:**
    1.  O `Nmap` foi utilizado para escanear a máquina e identificar o serviço `vsftpd 2.3.4` na porta `21`.
   ---
    <img width="912" height="310" alt="image" src="https://github.com/user-attachments/assets/f839f043-10a6-4607-81e8-703205d8e3e0" />

    2.  O `Searchsploit` foi usado para pesquisar por exploits públicos para a versão `vsftpd 2.3.4`.
    ---
    <img width="903" height="139" alt="image" src="https://github.com/user-attachments/assets/572686a7-44fb-44dd-9572-c7aa1c020b3e" />

    3.  O `Metasploit Framework` foi empregado para executar o exploit correspondente à falha.
    ---
     <img width="892" height="584" alt="image" src="https://github.com/user-attachments/assets/d93da5c7-4a6b-4017-9798-af5dfe46bf98" />

    4.  Após a execução bem-sucedida, uma sessão de shell foi obtida com privilégios de `root`.
    ---
    <img width="894" height="357" alt="image" src="https://github.com/user-attachments/assets/a77c92c1-7320-4a8e-bb37-264b2a6209eb" />



## 🛡️ Recomendações de Mitigação

Para mitigar a vulnerabilidade encontrada e fortalecer a segurança do sistema, recomenda-se:

* **Atualização de Software**: Atualizar o serviço `vsftpd` para a versão mais recente e segura.
* **Remoção de Serviços Desnecessários**: Desativar serviços que não são necessários na máquina, como o serviço de FTP, para reduzir a superfície de ataque.
* **Configuração Segura**: Garantir que o acesso de login anônimo não esteja habilitado para serviços como o FTP.

---
---

# Technical Report - Template (English Version)

## Executive Summary

This technical report details the penetration test conducted on the `Metasploitable 2` virtual machine, which serves as a security testing lab environment. The primary objective of the assessment was to gain access to the system with the highest privileges.

During the assessment, a critical vulnerability was identified and exploited, which led to unauthorized access to the target system as the `root` user.

## 🎯 Assessment Scope

The scope of this security assessment was limited to the `Metasploitable 2` virtual machine, with the IP address `192.168.56.103`, in an isolated lab network environment.

## 🔬 Assessment Methodology

The assessment followed a standard penetration testing methodology, which includes the following phases:

* **Reconnaissance**: Mapping the target's infrastructure to discover services, open ports, and software versions.
* **Vulnerability Analysis**: Identifying known security flaws in the target's software and configuration.
* **Exploitation**: Using a vulnerability to gain unauthorized access to the system.
* **Post-Exploitation**: Verifying the level of access and exploring the system for additional information.

## 🔍 Detailed Findings

**Vulnerability:** `vsftpd 2.3.4` - Backdoor Command Execution

* **Description:** During the reconnaissance phase, the `vsftpd 2.3.4` FTP service was identified on port `21`. It was discovered that this software version contains a backdoor vulnerability that allows for arbitrary command execution on the server.
* **Severity:** **Critical**. This flaw can be exploited by a remote attacker to gain full control of the system.
* **Steps to Exploit:**
    1.  `Nmap` was used to scan the machine and identify the `vsftpd 2.3.4` service on port `21`.
   ---
    <img width="912" height="310" alt="image" src="https://github.com/user-attachments/assets/f839f043-10a6-4607-81e8-703205d8e3e0" />
    2.  `Searchsploit` was used to search for public exploits for the `vsftpd 2.3.4` version.

    ---
    <img width="903" height="139" alt="image" src="https://github.com/user-attachments/assets/572686a7-44fb-44dd-9572-c7aa1c020b3e" />
    
    3.  The `Metasploit Framework` was employed to execute the corresponding exploit for the flaw.
    ---
     <img width="892" height="584" alt="image" src="https://github.com/user-attachments/assets/d93da5c7-4a6b-4017-9798-af5dfe46bf98" />
     
    4.  Upon successful execution, a command shell session was obtained with `root` privileges.
    ---
    <img width="894" height="357" alt="image" src="https://github.com/user-attachments/assets/a77c92c1-7320-4a8e-bb37-264b2a6209eb" />



## 🛡️ Mitigation Recommendations

To mitigate the identified vulnerability and strengthen the system's security, it is recommended to:

* **Update Software**: Upgrade the `vsftpd` service to the latest, secure version.
* **Remove Unnecessary Services**: Deactivate services that are not required on the machine, such as the FTP service, to reduce the attack surface.
* **Secure Configuration**: Ensure that anonymous login access is not enabled for services like FTP.
