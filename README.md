# Design e Arquitetura de Software II 2025/2

[AWS Canvas](#)

## Aula 30/07
## AWS

A AWS surgiu por volta dos anos 2000, quando a Amazon, então uma loja de livros online, enfrentava dificuldades para lidar com a crescente demanda por seus serviços. Em apenas seis anos, a empresa percebeu que precisava desenvolver sua própria infraestrutura tecnológica para suportar esse crescimento. Foi nesse contexto que surgiu a ideia de transformar essa infraestrutura em um serviço comercializável.

O pensamento de Jeff Bezos foi simples e estratégico:  
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

### Reliability Pillar
- Confiabilidade garante que o sistema continue funcionando mesmo diante de falhas.
- Alta disponibilidade
- Recuperação automática
- Uso de Auto Scaling e Multi-AZ
- Backups e replicação
- Ex: Se um servidor cair, outro assume usando uma cópia sincronizada.
  
### Recover Quickly
- Capacidade de restaurar o sistema rapidamente após falhas. Isso exige planejamento de recuperação, testes frequentes e monitoramento contínuo.
- 
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
