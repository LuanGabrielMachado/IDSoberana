# 🔐 Identidade Soberana

<div align="center">

![Build Status](https://img.shields.io/badge/version-3-blue.svg)
![Build](https://img.shields.io/badge/build-Não%20passou-red)
![Licença](https://img.shields.io/badge/licença-MIT-green)
![LGPD](https://img.shields.io/badge/LGPD-de acordo-blueviolet)  
![Proteção](https://img.shields.io/badge/Criptografia quantica-yellow) ![Proteção](https://img.shields.io/badge/Proteção de dados-pink) ![Proteção](https://img.shields.io/badge/Kotlin-purple)

# 🛰️ Identidade Soberana + Quantum  Framework
### Segurança Pós-Quântica • Criptografia HeptaKey • Identidade Descentralizada

### Identidade digital segura, offline-first e sob controle do usuário

A **Identidade Soberana** é um projeto de identidade digital focado em **segurança forte**,  
**controle granular de dados** e **funcionamento offline**, pensado desde o início para que o usuário seja o **único dono e guardião** da própria identidade.

A base atual, **Quantum Framework**, é a terceira geração do Soberana: uma reescrita estruturada, com arquitetura moderna,  
criptografia avançada e camadas preparadas para uma **arquitetura HeptaKey (7 chaves)** e recursos como **FIDO2 / WebAuthn**.

</div>

## 🎯 Objetivos do Projeto

- 🛡️ **Soberania de identidade**  
  O usuário controla o que compartilha, com quem e por quanto tempo – sempre com trilha de auditoria.

- 🔐 **Segurança desde a base**  
  Criptografia forte, biometria obrigatória em ações sensíveis, binding de dispositivo e preparado para pós-quântico.

- 📵 **Offline-first de verdade**  
  O app funciona totalmente offline: cadastro, cofre, criptografia e histórico não dependem de servidor.

- 🧾 **Compartilhamento granular e verificável**  
  Compartilhar só os campos necessários, com export em JSON assinado, para verificação de autenticidade.

- 🧩 **Arquitetura extensível**  
  Tudo foi pensado para crescer: backend, FIDO2, auditoria de rede e HeptaKey completa podem ser ativados em camadas.

---

## 🧠 Como o Soberana funciona (visão geral)

1. **Cadastro & Cofre Local**  
   - O usuário cadastra seus dados pessoais (nome, documento, endereço, etc).  
   - Esses dados são armazenados em um **banco local criptografado**, nunca em texto puro.

2. **Proteção por Biometria**  
   - Acesso ao cofre e ações sensíveis (como exportar dados) passam por **gate biométrico**.  
   - A biometria é integrada via `BiometricPrompt` com política forte (BIOMETRIC_STRONG / DEVICE_CREDENTIAL).

3. **Cofre & HeptaKey (núcleo criptográfico)**  
   - O app usa um núcleo de chaves separado por função (identidade, dados, dispositivo, etc).  
   - A base Quantum já está preparada para a arquitetura **HeptaKey** completa, mesmo que nem todas as chaves sejam usadas ainda na UI.

4. **Compartilhamento Granular**  
   - Em vez de “entregar tudo”, o usuário escolhe quais campos serão compartilhados.  
   - O app monta um **envelope protegido**: dados cifrados + metadados assinados.

5. **Export Verificável (roadmap)**  
   - Exportar um pacote JSON legível + assinatura destacada + metadados de política.  
   - Terceiros podem verificar se o pacote foi realmente emitido pelo Soberana e se não foi alterado.

6. **Integração com backend (futura)**  
   - A base já está apta a um cliente de rede (`DataRequestClient`) e interceptores HTTP de auditoria.  
   - Isso permite, no futuro, centralizar requisições e validar tudo com assinaturas e janelas de política (K5).

---

## 🧬 Segurança — o coração do Soberana

Mesmo antes de ativar todas as features avançadas, a base já é desenhada com segurança em primeiro lugar:

### 🔑 Núcleo de Chaves (HeptaKey-ready)

O projeto trabalha com o uso de **7 chaves com papéis separados**:

- **K1 – Identidade**  
  Assinatura de metadados, pedidos e exportações (base da identidade criptográfica).
- **K2 – Dados**  
  Cifra dos dados do usuário (cofre) com modos autenticados (AES-GCM).
- **K3 – Dispositivo**  
  Binding com o hardware: os dados só fazem sentido naquele aparelho.
- **K4–K7**  
  Reservadas para sessão, política, recuperação e consentimento avançado  
  (já previstas na arquitetura, prontas para serem ligadas fase a fase).

> Quantum Framework, o código já foi organizado pensando nessa hierarquia,  
> mesmo que nem todos os fluxos usem todas as chaves ainda.

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
  
### 🔐 Criptografia & Privacidade

- **Banco local cifrado** (Room + camadas de criptografia)  
- **Nada crítico em texto plano**: dados sensíveis sempre passam pelo núcleo de cifragem antes de ir para o disco.  
- Uso de AAD (Associated Authenticated Data) nas cifras em pontos estratégicos (id, device, etc).  
- Preparado para evoluir para **modos híbridos e pós-quânticos** conforme libs estáveis estiverem disponíveis.

### 👆 Biometria como gate de ações sensíveis

- Biometria integrada com reutilização controlada (janela de tempo curta para não irritar o usuário).  
- Chamada antes de ações como: abrir Meus Dados, compartilhar/exportar, responder requisições.  
- A biometria acontece **localmente**, sem depender de servidor.

### 🌐 FIDO2 / WebAuthn (camada opcional)

- Código de base para integração com `play-services-fido` já preparado.  
- Suporte a um serviço de **passkeys locais**, pronto para sincronia com backend quando ativado.  
- Mantido **desativado por padrão** na Quantum Framework, para não travar o fluxo enquanto o core é estabilizado.

---

## 🧱 Stack Tecnológica

### 📱 App Android (Quantum Framework)

- **Linguagem:** Kotlin  
- **UI:** Jetpack Compose + Material 3  
- **Arquitetura:** ViewModel + UseCases + Repositórios  
- **Persistência:** Room (com atenção a criptografia em camadas)  
- **DI / Orquestração:** Hilt ou container próprio de injeção (dependendo da fase)  
- **Conectividade:** OkHttp / Ktor client (para backend, quando ativado)  
- **Segurança:**
  - androidx.security (crypto / EncryptedFile)  
  - BiometricPrompt (BIOMETRIC_STRONG)  
  - Preparado para FIDO2 (`play-services-fido`)

### ☁️ Backend (planejado / integrável)

- **Linguagem:** Kotlin / Java  
- **Framework:** Spring Boot  
- **Banco:** PostgreSQL  
- **Responsabilidades principais:**
  - Receber envelopes de dados assinados  
  - Validar assinaturas e integridade  
  - Expor requisições de dados (requests) e auditoria

---

## 🧾 Status Atual

> **Quantum Framework** é uma base sólida para a terceira geração do Soberana:  
> a arquitetura de segurança já está desenhada e integrada,  
> o app funciona offline com foco em criptografia local e biometria,  
> e as camadas avançadas (backend, FIDO2, HeptaKey completa)  
> estão presentes no código, mas podem ser ativadas gradualmente.

---

## 🤝 Contribuição & Evolução

A evolução do Soberana segue alguns princípios:

- Segurança antes de conveniência  
- Transparência sobre o que é protegido e onde  
- Evolução incremental: primeiro o **núcleo confiável**, depois o “brilho” ao redor  
- Sempre com a meta de colocar o usuário **no controle total** da própria identidade

---

> A Identidade Soberana não é um simples app.

> É um provedor de identidade, um cofre, um manifesto
 
> É um experimento de como podemos ter de volta o controle total dos nossos dados

> Com **privacidade forte, UX simples e confiança verificável**

---

## 🧾 Licença

Desenvolvido com foco total em **segurança criptográfica pós-quântica e privacidade digital total**.

**MIT License**

Veja [LICENSE](./LICENSE) para detalhes completos.

---

<div align="center">

### 🌟 Se você acredita que privacidade é um direito, dê uma ⭐ neste projeto!

**Com 💙 para um mundo onde você controla seus dados**

[⬆ Voltar ao topo](#-identidade-soberana)

</div>

---
