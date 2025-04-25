# Arquitetura Simples no Azure

## Descrição

Este repositório contém a construção de uma **arquitetura básica no Microsoft Azure**, focada em uma rede privada (VNet) e uma máquina virtual (VM). O objetivo é proporcionar um ponto de partida para quem está começando a aprender sobre computação em nuvem, com uma infraestrutura simples mas funcional.

O projeto demonstra como criar e configurar os recursos essenciais no Azure, com ênfase em segurança e acessibilidade, usando boas práticas como o **Azure Bastion** para acesso remoto sem expor diretamente as portas de acesso à internet.

### Componentes Principais:

1. **Virtual Network (VNet)**: 
   - A **VNet** é uma rede isolada dentro do Azure que conecta diferentes recursos na nuvem. Ela garante que a comunicação entre os recursos seja feita de maneira segura e controlada. 
   - No projeto, a VNet foi criada com uma **sub-rede** para organizar melhor os recursos e garantir que a máquina virtual (VM) esteja isolada em uma rede privada.

2. **Máquina Virtual (VM)**:
   - A **VM** é configurada dentro da VNet, atuando como um servidor na nuvem que pode rodar sistemas operacionais e aplicativos.
   - A VM foi provisionada com **acesso remoto** via **RDP (Remote Desktop Protocol)**, permitindo que a máquina seja acessada a partir de um computador local usando o IP público.

3. **IP Público e RDP**:
   - Para garantir o acesso remoto à VM, foi configurado um **IP público**. Esse IP permite que a VM seja acessada pela internet, utilizando o protocolo **RDP** (porta 3389), uma solução comum para acessar máquinas virtuais baseadas em **Windows**.
   - Este acesso é realizado após a configuração do **NSG (Network Security Group)**, que define as regras de firewall para garantir a segurança da comunicação.

4. **Azure Bastion**:
   - O **Azure Bastion** foi configurado para fornecer uma forma de acessar a VM sem a necessidade de abrir portas diretamente na internet. Bastion cria uma conexão segura entre a máquina local e a VM, proporcionando uma camada extra de segurança.

### Estrutura do Projeto

A arquitetura foi montada de forma simples, composta pelos seguintes elementos:

- **Virtual Network (VNet)**: Rede privada onde os recursos são alocados.
  - **Sub-rede**: Para organizar os recursos de forma hierárquica e controlada.
  
- **Máquina Virtual (VM)**: Provisão de uma máquina para execução de serviços ou aplicativos.
  
- **IP Público**: Endereço atribuído à VM para permitir o acesso remoto a partir da internet.
  
- **Azure Bastion**: Acesso seguro à VM, sem a necessidade de abrir portas de RDP diretamente.

- **Network Security Group (NSG)**: Regras de segurança configuradas para controlar o tráfego de rede da VM e da VNet.

## Objetivo

O objetivo deste projeto é fornecer uma base simples para aprender como trabalhar com os serviços essenciais do **Microsoft Azure**, especificamente:

- Criação e configuração de redes privadas (VNet).
- Provisionamento de máquinas virtuais (VMs).
- Uso de IPs públicos para acesso remoto.
- Implementação do **Azure Bastion** para aumentar a segurança no acesso às máquinas virtuais.

## Passos para Implementação

Para construir esta arquitetura no Azure, siga os seguintes passos:

1. **Criar a Virtual Network (VNet)**:
   - No portal do Azure, crie uma **Virtual Network** (VNet). Durante a criação, defina o **endereço de IP** da VNet, o **espécie de rede** e a **sub-rede**.

2. **Criar a Máquina Virtual (VM)**:
   - Após a criação da VNet, crie uma **máquina virtual**. Escolha o **sistema operacional** (Windows ou Linux) e aloque a VM dentro da VNet criada.

3. **Configurar o Acesso Público (IP público)**:
   - Durante a criação da VM, atribua um **IP público** à máquina para possibilitar o acesso remoto via RDP. Esse IP será usado para se conectar à VM externamente.

4. **Habilitar o Azure Bastion**:
   - Para melhorar a segurança, configure o **Azure Bastion**. Isso permitirá que você acesse a VM de maneira segura, sem expor as portas RDP diretamente à internet.

5. **Configurar o NSG (Network Security Group)**:
   - Após configurar a VM, crie um **NSG** e defina regras de tráfego para garantir que apenas conexões seguras e autorizadas possam acessar a VM. Normalmente, você vai abrir a porta 3389 para RDP ou a porta 22 para SSH, dependendo do tipo de VM e sistema operacional.

6. **Testar o Acesso à VM**:
   - Após configurar os recursos, teste o acesso à VM. Você pode fazer isso usando o **Azure Bastion** ou conectando-se diretamente via **RDP** usando o IP público da máquina.

## Conclusão

Com a criação dessa arquitetura simples no **Microsoft Azure**, foi possível configurar os principais componentes necessários para uma infraestrutura segura e funcional. A partir da configuração da **Virtual Network (VNet)** e da **Máquina Virtual (VM)**, junto com o uso do **Azure Bastion** para acesso remoto seguro e o **NSG** para controle de tráfego, a estrutura básica foi estabelecida.

Esses blocos fundamentais criam uma base sólida, permitindo que novos recursos sejam adicionados e a infraestrutura seja expandida conforme necessário. A partir daqui, é possível explorar outras funcionalidades do **Azure**, como **armazenamento**, **bancos de dados** e **serviços de rede adicionais**, para integrar e evoluir a arquitetura conforme os requisitos do projeto crescem.

Com esse projeto, é possível obter uma compreensão básica dos principais recursos do Azure e como eles se conectam para criar uma infraestrutura segura e escalável. À medida que a experiência aumenta, é possível adicionar complexidade, incluindo o uso de **Redes Virtuais adicionais**, **Gateways VPN**, ou até mesmo **Azure Kubernetes Service (AKS)**, para soluções mais avançadas de escalabilidade e orquestração.
