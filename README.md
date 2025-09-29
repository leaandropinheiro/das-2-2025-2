# Design e Arquitetura de Software II 2025/2

[AWS Canvas](#)

# Aula 30/07
### AWS

A AWS surgiu por volta dos anos 2000, quando a Amazon, então uma loja de livros online, enfrentava dificuldades para lidar com a crescente demanda por seus serviços. Em apenas seis anos, a empresa percebeu que precisava desenvolver sua própria infraestrutura tecnológica para suportar esse crescimento. Foi nesse contexto que surgiu a ideia de transformar essa infraestrutura em um serviço comercializável.

**"Se temos data centers ociosos, por que não oferecê-los como serviço para outras empresas?"**

### Role of a Cloud Architect
- O Cloud Architect é o profissional responsável por projetar e implementar soluções escaláveis, seguras, resilientes e econômicas na nuvem. Ele entende as necessidades do negócio e transforma isso em uma arquitetura técnica, utilizando os serviços certos da AWS.

### Pillars of the AWS Well-Architected Framework
- O Well-Architected Framework da AWS é baseado em seis pilares, que ajudam a construir sistemas otimizados:

### Excelência Operacional
- Segurança
- Confiabilidade
- Eficiência de Performance
- Otimização de Custos
- Sustentabilidade

### Operational Excellence Pillar
- Esse pilar foca na operação eficiente da infraestrutura, incluindo automação, monitoramento e melhoria contínua.
- Terraform:
- Ferramenta de IaC (Infrastructure as Code) que evita a criação manual de recursos. Com ela, é possível versionar a infraestrutura e aplicar mudanças com mais segurança e repetibilidade.

### Security Pillar – “Mãos de Duas Vias”
- Segurança exige cuidado tanto na AWS quanto do lado do usuário.
- De nada adianta usar uma infraestrutura segura se o básico é negligenciado:
- Uso de MFA
- Boas práticas com credenciais
- Atenção a phishing e e-mails maliciosos
- Monitoramento e controle de acesso (IAM)
- ### Autenticação e Autorização
- Autenticação: confirma a identidade do usuário.
  - Ex: login e senha (o que você sabe)
  - MFA (o que você tem)
  - Biometria(o que você é)
- Autorização: define o que o usuário pode fazer após autenticado.
  - Ex: permissões atribuidas via IAM User ou Role

### Reliability Pillar
- Confiabilidade garante que o sistema continue funcionando mesmo diante de falhas.
- Alta disponibilidade
- Recuperação automática
- Uso de Auto Scaling e Multi-AZ
- Backups e replicação
- Ex: Se um servidor cair, outro assume usando uma cópia sincronizada.
  
### Recover Quickly
- Capacidade de restaurar o sistema rapidamente após falhas. Isso exige planejamento de recuperação, testes frequentes e monitoramento contínuo.

### Dynamically Meet Compute Demand
- A infraestrutura precisa escalar de forma automática de acordo com a demanda (como em dias de pico).
Ex: Usar Auto Scaling para lidar com tráfego inesperado.

### Migrate Disruption
- Minimizar impacto ao migrar para a nuvem. Ferramentas como o AWS Migration Hub ajudam a fazer isso com menos downtime e mais controle.

### Performance Efficiency Pillar
- Esse pilar visa usar os recursos de forma eficiente e adaptável.
- Escolher o tipo certo de instância
- Manter tecnologias atualizadas
- Automatizar tarefas
Ex: Quantas máquinas seriam necessárias para suportar a venda de ingressos do Rock in Rio? O planejamento precisa prever picos extremos.

### Cost Optimization Pillar
- Foco em eficiência financeira.
- Estratégias:
- Medir uso real
- Eliminar recursos ociosos
- Usar o modelo de consumo correto (ex: Spot Instances)
- Preferir serviços gerenciados (como RDS ao invés de EC2 + banco)

### Sustainability Pillar
- Projetar sistemas com menor impacto ambiental.
- Boas práticas:
- Escolher hardware e software eficientes
- Maximizar o uso dos recursos provisionados
- Reduzir o impacto ao longo de todo o ciclo de vida do sistema

### AWS Well-Architected Tool
- Ferramenta da AWS que ajuda a avaliar a arquitetura de um sistema com base nos 6 pilares. Ela sugere melhorias, identifica riscos e promove boas práticas.

### Using AWS WA Tool
- Você pode usar a WA Tool para revisar workloads, gerar relatórios e acompanhar as melhorias ao longo do tempo, integrando o processo ao ciclo de vida da aplicação.

### Design Trade-offs
- Nem sempre é possível otimizar tudo. Às vezes é necessário escolher entre:
- Velocidade vs. Confiabilidade
- Custo vs. Performance
Exemplo: O TikTok prioriza propagação rápida de conteúdo, mesmo que isso custe mais em cache e distribuição.

### Implementing Scalability
Permitir que a aplicação escale automaticamente com base na demanda.
- Provisionamento automático
- Uso de EC2 Auto Scaling
- Elastic Load Balancing
- Containers e serverless (ECS, Lambda)

### Using EAC
- Provavelmente você quis dizer ECS (Elastic Container Service) ou EKS. Ambos permitem executar containers de forma escalável na AWS.

### Treating Resources as Disposable
- Recursos devem ser efêmeros. Ou seja, crie, destrua e substitua com facilidade.
- Isso reduz risco, facilita o deploy contínuo e previne acúmulo de configuração "manual".

### Designing Services, Not Servers
- Foque em construir serviços independentes e escaláveis (ex: Lambda, Fargate) ao invés de manter servidores fixos e longos.

### Choosing the Right Database Solution
- Escolher o banco certo para cada caso:
- Relacional: RDS (MySQL, PostgreSQL)
- Não-relacional: DynamoDB
- OLAP: Redshift
- Em memória: ElastiCache

### Optimizing for Cost
- Otimizar para custo envolve:
- Monitorar constantemente
- Reduzir subutilização
- Reservar instâncias (Reserved Instances)
- Usar instâncias Spot

### Using Caching – CloudFront
- CloudFront é a CDN da AWS. Ajuda a entregar conteúdo com baixa latência e reduzir custo, armazenando dados em cache em locais próximos ao usuário.

### Securing Your Entire Infrastructure
- Segurança de ponta a ponta:
- Criptografia de dados em trânsito e em repouso
- IAM bem configurado
- MFA em todas as contas
- Monitoramento com CloudTrail, GuardDuty, etc.
- Segurança em várias camadas (firewalls, VPC, WAF)

# Aula 06/08
### Modelo de responsabilidade compartilhada
A AWS segue o modelo de responsabilidade compartilhada, onde a segurança é dividida entre a AWS e o cliente:

- AWS: protege a infraestrutura (hardware, rede, data centers).
- Cliente: gerencia dados, permissões, aplicativos e configuração de serviços.
Isso significa que você não depende apenas da AWS; precisa também cuidar de como utiliza os recursos.

### Princípio do privilégio mínimo
Esse princípio diz que cada usuário ou serviço deve ter apenas as permissões necessárias para executar suas tarefas. Menos permissões = menos risco de falhas ou ataques.

### Autenticação e Autorização

- Autenticação: confirma quem você é (ex.: login com senha, MFA).
- Autorização: determina o que você pode fazer após ser autenticado.

### IAM User e IAM Role
- IAM User: identidade individual dentro da AWS, associada a credenciais e permissões específicas.
- IAM Role: conjunto de permissões que pode ser assumido por usuários, serviços ou recursos temporariamente. Roles são úteis para automações e aplicações que precisam acessar serviços sem usar credenciais fixas.

# Aula 13/08
### Identity Based Policies
São políticas aplicadas a usuários, grupos ou roles da AWS. Elas definem o que aquele usuário ou serviço pode ou não fazer dentro da conta. Por exemplo, um usuário de leitura pode acessar arquivos S3, mas não alterar ou deletar.

Resource Based Policies
São políticas aplicadas diretamente a recursos da AWS, como buckets do S3 ou filas do SQS. Elas definem quem (qual usuário ou serviço) tem acesso ao recurso e quais ações podem ser realizadas, independente de políticas atribuídas ao usuário.

# Aula 20/08
### Block Storage
Armazenamento em blocos divide os dados em unidades fixas chamadas “blocos”, que podem ser gerenciados individualmente. Muito usado em sistemas operacionais, bancos de dados e aplicações que precisam de desempenho e baixa latência, como volumes do EBS (Elastic Block Store).

### File Share
Armazenamento baseado em arquivos permite que múltiplos usuários acessem arquivos e pastas de forma compartilhada, similar a um servidor de arquivos local. Ex.: EFS (Elastic File System) da AWS.

### Object Store
Armazenamento baseado em objetos trata cada arquivo como um objeto independente, com metadados e um identificador único. Ideal para grandes volumes de dados não estruturados, como fotos, vídeos e backups. Ex.: Amazon S3.

### S3 – Resumo Geral
O Amazon S3 é o serviço de Object Storage mais popular da AWS. Ele oferece alta durabilidade, escalabilidade e acesso seguro a qualquer quantidade de dados, permitindo integração com outros serviços da AWS e oferecendo recursos como versionamento, replicação e controle de acesso.

# Aula 03/09
- Serviços computacionais da AWS (EC2)
  - O Amazon EC2 (Elastic Compute Cloud) é o serviço da AWS que permite criar e gerenciar máquinas virtuais na nuvem. Ele dá flexibilidade para escolher sistema operacional, CPU, memória e rede, de acordo com a necessidade da aplicação.

- Amazon Machine Images (AMI)
  - Imagens de sistemas operacionais (como Linux, Windows) ou imagens personalizadas que podem incluir softwares, bibliotecas e configurações.

- Tipos de Instâncias
  - As instâncias do EC2 são classificadas em diferentes tipos, otimizados para casos de uso específicos. General Purpose (uso geral), Compute Optimized (processamento), Memory Optimized (memória) e Storage Optimized.

- Tipos de Storage (EBS/Instance Store)
  - EBS (Elastic Block Store)
    - armazenamento persistente, ou seja, os dados continuam existindo mesmo após desligar a instância. Funciona como um HD/SSD conectado via rede.

  - Instance Store
    - armazenamento temporário direto no hardware físico. Rápido, mas os dados são perdidos ao parar ou reiniciar a instância.

- Acesso via SSH
  - O acesso a instâncias Linux na AWS é feito via SSH, que garante conexão segura através de chaves criptográficas.

# Aula 10/09
- Tipos de Storage (EBS/Instance Store)
  - EBS
    - Persistente e flexível.
  - Instance Store
    - Rápido, mas temporário.

- Elastic File System (EFS) / FSx
  - EFS (Elastic File System)
    - Sistema de arquivos escalável e gerenciado, acessível por várias instâncias EC2 ao mesmo tempo.
  - FSx
    - Serviço de file system especializado, como FSx for Windows File Server.

- EC2 Windows
  - Além de Linux, o EC2 também suporta instâncias com Windows Server.

# Aula 17/09
  - EC2:
    - User Data
      - Permite rodar scripts, instalar pacotes e configurar apps, na inicialização da instancia.

    - Instance Metadata
      - Informações internas da instância

    - Placement
      - Define onde a instância será executada fisicamente (região, zona de disponibilidade ou placement groups para baixa latência).

  - VPC
    - O que é uma VPC?
      - Uma VPC é uma rede virtual privada dentro da AWS, onde você controla endereçamento IP, sub-redes, rotas e segurança.

    - Subnets Públicas e Privadas
      - Publica
        - Acessível pela internet.
      - Privada
        - Isolada, acessada apenas internamente ou via VPN.

    - Security Group e NACL
      - Security Group
        - Firewall em nível de instância (controla portas e protocolos).
      - NACL (Network ACL)
        - Firewall em nível de subnet, com regras de entrada e saída.

    - VPN Site-to-Site
      - Conexão segura entre a rede local da empresa (on-premises) e a VPC na AWS, funcionando como se estivessem na mesma rede.

    - Peering
      - Conexão entre duas VPCs diferentes, permitindo comunicação direta entre instâncias de ambas.



