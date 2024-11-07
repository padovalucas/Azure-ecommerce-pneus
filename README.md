## E-commerce de Pneus - Arquitetura de Infraestrutura Azure
Este repositório contém a documentação da arquitetura de infraestrutura para um e-commerce de pneus, um sistema crítico responsável por mais de 80% do lucro da empresa. A arquitetura foi projetada para alta disponibilidade, segurança robusta, observabilidade abrangente e gestão eficiente de custos.

## Visão Geral
A aplicação é construída com uma arquitetura moderna em nuvem, utilizando um banco de dados PaaS MySQL, um appservice com backend em .NET 8 e outro appservice com frontend em Node.js, hospedados no Azure. O acesso à aplicação é feito via web, com autenticação via SSO. O backoffice é acessível apenas por IPs internos da empresa. Além disso, a empresa possui um ambiente local com Active Directory (AD) sincronizado com a Azure, contendo servidores de FileServer e PrintServer.

## Componentes Principais
* Azure Front Door: Entrega eficiente de conteúdo estático, com menor latência, alta escalabilidade e garantindo a segurança.
* Frontend (Node.js): Responsável pela interface do usuário e interação com o backend.
* Backend (.NET 8): Lógica de negócio e acesso ao banco de dados.
* MySQL (Clusterizado): Armazenamento de dados com alta disponibilidade e replicação.
* Load Balancers: Distribuição de carga entre as instâncias do backend.
* Firewall (WAF): Proteção contra ataques web.
* Azure AD (SSO): Autenticação única e segura.
* AD Local (Sincronizado com Azure AD): Integração com o ambiente local.

## Resiliência
* MySQL Clusterizado: Replica os dados e permite failover automático para outra região em caso de falha.
* Backend em múltiplas instâncias com Load Balancer: Garante disponibilidade mesmo com a queda de uma instância.
* Backup: Replicação dos dados em multi-zonas ou regiões

## Segurança
* Firewall (WAF): Protege contra ameaças comuns da web.
* SSO (Azure AD): Centraliza a autenticação e reforça a segurança.
* Acesso condicional: Limita o acesso ao backoffice aos IPs autorizados.
* MFA: Complementa a segurança do acesso ao backoffice garantindo que a autenticação é de um usuário legítimo.

## Observabilidade
* Azure Monitor: Acompanha o desempenho dos componentes-chave.
* Log analytics: Armazena logs para análise e troubleshooting.
* Alertas Automatizados: Notifica a equipe sobre eventos críticos.
* Azure Managed Grafana: Visualização gráfica de telemetria com alta disponibilidade e controle de segurança do Azure.

## Gestão de Custos
* CDN: Reduz a carga nos servidores e otimiza a entrega de conteúdo estático.
* Escalonamento Automático: Ajusta os recursos de acordo com a demanda.
* Instâncias Reservadas: Permite obter descontos de até 70% na nuvem.

## Pontos de melhoria
* Implementar monitoramento detalhado de cada componente.
* Configurar alertas específicos para diferentes cenários.
* Automatizar o processo teste de integridade de backup.
* Automatizar ações de resposta com base em evento.
* Aprimoramento da política de acesso condicional com análise de compliance do dispositivo.
* Data encryption at rest: Criptografa as databases, backups e logs durante o repouso.
* Microsoft Entra authentication only: Desabilita os usuários locais do banco e permie o acesso somente com a conta do Entra.
* Microsoft Defender for cloud: Detecta atividades anômalas indicando tentativas de acesso suspeita ou ataque.
