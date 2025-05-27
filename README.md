# Window-Server-Active-Directory
# Instalação e Configuração do Active Directory - Windows Server 2008

Este repositório contém um guia passo a passo para instalar e configurar o Active Directory Domain Services (AD DS) no Windows Server 2008. Ideal para ambientes que precisam de autenticação centralizada, políticas de grupo e gerenciamento de usuários e dispositivos em rede.

---

## Requisitos

- Windows Server 2008 instalado e configurado.
- Nome de host configurado corretamente.
- Endereço IP fixo atribuído ao servidor.
- Permissões administrativas locais.

---

## Etapas de Instalação do Active Directory

### 1. Preparar o Ambiente

1. Defina um **nome de computador estável**:
   - Exemplo: `srv-ad01`
   - Evite renomear após a instalação do AD.

2. Configure um **endereço IP fixo**:
   - Acesse: Painel de Controle > Central de Rede > Alterar configurações do adaptador.
   - Clique com o botão direito no adaptador > Propriedades > Protocolo TCP/IP v4.
   - Configure IP, Máscara, Gateway e DNS (o próprio IP do servidor como DNS primário).

---

### 2. Instalar a Função Active Directory Domain Services (AD DS)

1. Acesse: Iniciar > Ferramentas Administrativas > Gerenciador do Servidor.
2. Clique em **Funções** no painel esquerdo.
3. No painel direito, clique em **Adicionar Funções**.
4. No assistente, marque a função **Serviços de Domínio Active Directory**.
5. Clique em **Avançar** até a tela de confirmação, e depois em **Instalar**.
6. Aguarde a instalação e clique em **Fechar** ao final.

---

### 3. Promover o Servidor a Controlador de Domínio (DCPROMO)

1. No menu Iniciar, clique em **Executar**, digite `dcpromo` e pressione Enter.

#### Etapas do Assistente:

**a. Introdução ao Assistente**
- Clique em **Avançar**.

**b. Compatibilidade**
- Leia e clique em **Avançar**.

**c. Tipo de Domínio**
- Selecione **Criar um novo domínio em uma nova floresta**.
- Clique em **Avançar**.

**d. Nome do Domínio**
- Digite o nome completo do domínio (FQDN):
  - Exemplo: `empresa.local`
- Clique em **Avançar**.

**e. Nível Funcional da Floresta e Domínio**
- Selecione o nível funcional desejado (ex: Windows Server 2008).
- Clique em **Avançar**.

**f. Funções adicionais do controlador**
- Mantenha marcada a opção para instalar o **Servidor DNS**.
- Clique em **Avançar**.

**g. Aviso de Delegação de DNS**
- Pode aparecer um alerta, apenas confirme clicando em **Sim** ou **Avançar**.

**h. Caminhos do banco de dados e logs**
- Use os padrões recomendados (normalmente `C:\Windows\NTDS`).
- Clique em **Avançar**.

**i. Senha do Modo de Restauração (DSRM)**
- Defina uma senha forte e anote em local seguro.
- Clique em **Avançar**.

**j. Resumo e Instalação**
- Revise as configurações.
- Clique em **Avançar** e aguarde o processo.
- Após a instalação, reinicie o servidor quando solicitado.

---

## Pós-instalação: Verificações Básicas

### Validar o Domínio

1. Após o reboot, faça login com a conta `DOMÍNIO\Administrador`.
2. Verifique o nome do domínio em:
   - Painel de Controle > Sistema
3. Acesse:
   - Iniciar > Ferramentas Administrativas > Usuários e Computadores do Active Directory
   - Verifique se o domínio está visível e funcional.

---

## Gerenciamento do AD

- **Usuários e Computadores do AD**: Gerencia contas, grupos e OUs.
- **Domínios e Relações de Confiança**: Gerencia domínios filhos e relações entre florestas.
- **Sites e Serviços do AD**: Gerencia controladores de domínio por localidade física.
- **GPMC (Política de Grupo)**: Gerencia GPOs aplicadas a usuários e computadores.

---
