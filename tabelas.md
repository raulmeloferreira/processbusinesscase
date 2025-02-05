| **Categoria**                | **Camunda 7** | **Camunda 8** | **Diferença Prática (Gap)** |
|------------------------------|--------------|--------------|------------------------------|
| **Arquitetura** | Monolítica, baseada em banco de dados | Cloud-native, baseada no Zeebe (event-driven) | O Camunda 8 foi projetado para nuvem e não depende de um banco relacional para persistência. |
| **Motor de Execução** | Baseado em Threads síncronas e banco SQL | Zeebe (arquitetura distribuída e assíncrona) | O Camunda 8 pode escalar horizontalmente de forma eficiente. |
| **Persistência de Dados** | Banco relacional (PostgreSQL, MySQL, Oracle) | Event Sourcing com Zeebe (log distribuído) | No Camunda 8, os estados são armazenados em logs distribuídos, melhorando performance e escalabilidade. |
| **Orquestração** | Processos síncronos (DB-driven) | Processos assíncronos (event-driven) | O Camunda 8 pode lidar melhor com workloads variáveis e evitar gargalos de banco. |
| **Suporte a Kubernetes** | Sim, mas requer ajustes manuais | Nativo, otimizado para containers | O Camunda 8 suporta Kubernetes de forma automática, facilitando deploy e escalabilidade. |
| **Visualização de Processos** | Cockpit (logs e visão estática) | Operate (tempo real, filtros avançados) | O Camunda 8 permite monitoramento interativo e insights detalhados. |
| **Escalabilidade** | Vertical (limitada pelo banco SQL) | Horizontal (Zeebe, sem banco relacional) | O Camunda 8 pode escalar para milhões de processos sem degradação de performance. |
| **Gerenciamento de Usuários** | Simples: configuração via API ou banco de dados | Avançado: UI dedicada, SSO e permissões granulares | No Camunda 8, usuários e permissões podem ser gerenciados facilmente via interface gráfica. |
| **Autenticação** | LDAP, usuários manuais | OIDC, OAuth 2.0, Keycloak | O Camunda 8 oferece suporte nativo a autenticação moderna e SSO. |
| **Modelo de Deploy** | Aplicação standalone (Spring Boot ou JEE) | SaaS ou auto-hospedado | O Camunda 8 permite implantação flexível em nuvem. |
| **Tolerância a Falhas** | Dependente do banco de dados (stateful) | Arquitetura distribuída e resiliente | O Camunda 8 lida melhor com falhas e recuperação automática. |
| **Suporte a DMN (Decision Model and Notation)** | Sim | Sim, via Modeler | Ambos suportam DMN, mas no Camunda 8 a execução está integrada ao Zeebe. |
| **Suporte a BPMN (Business Process Model and Notation)** | Sim | Sim | Ambos seguem o padrão BPMN, mas o Camunda 8 melhora a execução escalável. |
| **Automação de Tarefas Humanas** | Tasklist básica no Cockpit | Tasklist separada e integrada | No Camunda 8, a interface de tarefas humanas foi redesenhada para maior eficiência. |
| **Integração com Microservices** | Sim, mas baseado em chamadas síncronas | Sim, arquitetura assíncrona e eventos | No Camunda 8, a comunicação assíncrona reduz dependências e melhora a escalabilidade. |
| **APIs** | REST e Java API | REST, GraphQL e gRPC | O Camunda 8 adiciona suporte moderno a GraphQL e gRPC para maior flexibilidade. |
| **Preço e Licenciamento** | Open-source (Community Edition) e Enterprise | Modelo SaaS pago, mas com versão auto-hospedada | O Camunda 8 é mais orientado a um modelo de assinatura, enquanto o Camunda 7 pode ser usado gratuitamente. |



| **Categoria** | **Camunda 7** | **AWS Step Functions** | **Diferença Prática (Gap)** |
|--------------|--------------|------------------|------------------------------|
| **Arquitetura** | Monolítica, baseada em banco de dados | Serverless, baseada em eventos (State Machine) | O Camunda 7 exige infraestrutura gerenciada, enquanto o Step Functions é gerenciado pela AWS. |
| **Motor de Execução** | Baseado em threads síncronas e banco SQL | Event-driven (serverless state machine) | O Step Functions executa fluxos de forma assíncrona e altamente distribuída. |
| **Persistência de Dados** | Banco relacional (PostgreSQL, MySQL, Oracle) | AWS DynamoDB e CloudWatch Logs | O Camunda 7 persiste estados no banco, enquanto o Step Functions usa um modelo gerenciado da AWS. |
| **Orquestração** | Processos síncronos e baseados em BPMN | Workflows assíncronos baseados em estados | O Step Functions é mais adequado para arquiteturas distribuídas e cloud-native. |
| **Escalabilidade** | Vertical (limitada pelo banco SQL) | Escalabilidade automática e infinita (AWS Lambda, ECS, etc.) | O Step Functions escala horizontalmente de forma automática sem intervenção manual. |
| **Gerenciamento de Usuários** | Simples, baseado em API ou banco de dados | Integrado ao IAM (Identity and Access Management) da AWS | O Step Functions permite controle granular via permissões do IAM. |
| **Autenticação** | LDAP, usuários manuais | IAM, Cognito, e autenticação federada | O Step Functions usa autenticação nativa da AWS para segurança e integração. |
| **Modelo de Deploy** | Aplicação standalone (Spring Boot ou JEE) | Totalmente gerenciado pela AWS | O Camunda 7 requer servidores ou containers, enquanto o Step Functions não exige infraestrutura. |
| **Tolerância a Falhas** | Depende do banco de dados | Resiliência nativa (Retry automático, Dead Letter Queues) | O Step Functions oferece recuperação automática e alta disponibilidade embutida. |
| **Suporte a BPMN** | Sim | Não | O Step Functions usa JSON para definir workflows, enquanto o Camunda 7 segue o padrão BPMN. |
| **Suporte a DMN (Decision Model and Notation)** | Sim | Não | O Camunda 7 pode executar regras de decisão DMN, enquanto o Step Functions não tem suporte nativo. |
| **Automação de Tarefas Humanas** | Tasklist básica no Cockpit | Não nativo (requer integração com serviços como SNS, SQS, Lambda) | O Camunda 7 permite tarefas humanas, enquanto no Step Functions isso precisa ser implementado separadamente. |
| **Integração com Microservices** | Sim, via REST e Java API | Sim, via AWS Lambda, API Gateway, DynamoDB, SQS, SNS, etc. | O Step Functions tem integração nativa com o ecossistema AWS. |
| **APIs** | REST e Java API | REST, SDKs AWS (Python, Node.js, Java, etc.) | O Step Functions é otimizado para serviços AWS e APIs modernas. |
| **Preço e Licenciamento** | Open-source (Community Edition) e Enterprise | Modelo pay-per-use (custo por transição) | O Camunda 7 pode ser gratuito, enquanto o Step Functions cobra por execução de estados e transições. |
