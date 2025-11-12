# 🔐 Identidade Soberana

<div align="center">

![Build Status](https://img.shields.io/badge/version-3-blue.svg)
![Build](https://img.shields.io/badge/build-Não%20passou-red)
![Licença](https://img.shields.io/badge/licença-MIT-green)
![LGPD](https://img.shields.io/badge/LGPD-de acordo-blueviolet)  
![Proteção](https://img.shields.io/badge/Criptografia quantica-yellow) ![Proteção](https://img.shields.io/badge/Proteção de dados-pink) ![Proteção](https://img.shields.io/badge/Kotlin-purple)

# 🛰️ Identidade Soberana + Quantum  Framework
### Segurança Pós-Quântica • Criptografia HeptaKey • Identidade Descentralizada

A **Identidade Soberana Quantum** redefine o conceito de privacidade digital e autenticação segura.  
Construída do zero com uma arquitetura pós-quântica, o sistema combina **criptografia multi-camada**, **biometria obrigatória** e **controle granular de dados**,  
tudo dentro de um ecossistema **offline-first**, auditável e imune a interferências externas.

---

## ⚙️ Tecnologia e Arquitetura

### 🧠 Núcleo HeptaKey (K1 → K7)
O sistema opera sobre uma **hierarquia de sete chaves criptográficas** independentes e interligadas, cada uma com propósito próprio:

| Chave | Propósito | Modo | Observação |
|:------|:-----------|:-----|:------------|
| **K1 – Identidade** | Assina requisições e metadados | Ed25519 | Base da identidade e assinatura de integridade |
| **K2 – Dados** | Cifra payloads com AAD (id/device) | AES-GCM 256 | Selagem de informações sensíveis |
| **K3 – Dispositivo** | Binding físico com hardware seguro | Keystore / StrongBox | Garante integridade local |
| **K4 – Sessão** | Cifra efêmera (Perfect Forward Secrecy) | X25519 | Destruída após uso |
| **K5 – Política** | Define janelas de validade e escopo | AES-CTR + Meta | Controla expiração e revogação |
| **K6 – Recuperação** | Shamir T-de-N (Split Key) | Offline | Recuperação sem backend |
| **K7 – Consentimento** | Assina base legal e finalidade de uso | Ed25519 | Transparência e auditoria legal |

---

## 🔐 Segurança de Próxima Geração

- **Criptografia pós-quântica híbrida** (AES-GCM + X25519 + Ed25519 → PQC-ready)  
- **HeptaKey Hierarchy** — múltiplas camadas independentes de proteção  
- **AAD dinâmico (Associated Auth Data)** — cada cifra vinculada ao ID e dispositivo  
- **Biometria obrigatória** — validação física antes de qualquer ação sensível  
- **Selagem total de disco** — nenhum dado em texto claro (EncryptedFile AES256-GCM)  
- **Assinaturas digitais K1/K7** — autenticação e verificação de consentimento  
- **Root & Tamper Protection** — bloqueio automático sob violação de integridade  

---

## 💾 Operação Offline-First

O app foi projetado para funcionar **completamente offline**:

- **Outbox Inteligente** — filas criptografadas com sincronização segura quando há rede  
- **Recovery Local (K6)** — restauração independente, sem servidor  
- **Export Verificável** — JSON legível + `.sig` + `meta.json` (K5/K7)  
- **Sincronização Assinada** — quando conectado, valida via K1 antes de transmitir  

---

## 🎯 Funcionalidades Principais

### 🔒 Segurança & Privacidade
- Biometria e assinatura digital em todas as ações sensíveis  
- Compartilhamento **campo a campo** com aprovação explícita  
- **Histórico auditável** — mostra empresa, motivo e campos solicitados  
- **Revogação instantânea** de chaves e acessos  
- **Verificação de autenticidade** via export assinável (K1 + cadeia K5/K7)

### 🧬 Estrutura Técnica
- **Android:** Kotlin • Jetpack Compose • Hilt • Room • Coroutines  
- **Cripto:** AES-GCM • X25519 • Ed25519 • EncryptedFile • Keystore  
- **UI:** Material Design 3 • Tema dinâmico • Animações suaves • Edge-to-edge  
- **Backend Quantum v19:** Spring Boot • PostgreSQL • verificação K1/K5  

---

## 🧩 Arquitetura de Camadas


- **Presentation:** UI Compose + navegação animada (AnimatedNavHost)  
- **Domain:** Fluxos de autenticação, criptografia e política de consentimento  
- **Data:** Repositórios selados, persistência segura e Outbox  

---

## 🧠 Filosofia Quantum

> “A privacidade é um direito.  
> A autenticação deve ser invisível, mas inquebrável.”

A Identidade Soberana Quantum é mais que um aplicativo — é um **framework de soberania digital**.  
Cada decisão técnica é voltada para **autonomia**, **verificabilidade** e **segurança local total**,  
permitindo que o usuário seja o **único detentor e validador da sua identidade**.

---

## 🚀 Status Atual

| Módulo | Estado | Observação |
|:--------|:--------|:------------|
| Criptografia HeptaKey | ✅ Concluído | K1–K7 integrados e testados |
| Biometria | ✅ Obrigatória | Gate em todas as ações sensíveis |
| Outbox / Offline | ✅ | 100% funcional |
| Export Verificável | ✅ | Meta + assinatura K1/K7 |
| UI / UX | ✅ | Compose M3 + tema dinâmico |
| Backend Quantum v19 | ⚙️ | Validação de integridade e assinatura K1 |

---

## 🧾 Licença

Desenvolvido no contexto do **Identidade Soberana**,  
com foco em **segurança criptográfica pós-quântica e privacidade digital total**.

**MIT License**

Veja [LICENSE](./LICENSE) para detalhes completos.

---

<div align="center">

### 🌟 Se você acredita que privacidade é um direito, dê uma ⭐ neste projeto!

**Com 💙 para um mundo onde você controla seus dados**

[⬆ Voltar ao topo](#-identidade-soberana)

</div>

---
