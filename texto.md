## **Business Case: Orquestração de Processos Stateful**

---

## **1\. Resumo Executivo**

Este documento avalia alternativas de ferramentas para orquestração de processos _stateful_ de forma eficiente, escalável e confiável.

Atualmente, a organização utiliza o **Camunda 7 Community Edition**, que, embora tenha atendido às necessidades iniciais, enfrenta limitações técnicas e estratégicas para suportar o crescimento e modernização. Entre as opções consideradas estão: **Camunda 8**, **Bamoe**, e **Step Functions (AWS)**.

A análise considera critérios como custo de licença, custo de infraestrutura, esforço para construção da arquitetura de referência, escalabilidade, facilidade de uso, suporte e integração com os sistemas existentes. A recomendação final será baseada na capacidade de cada solução em atender a esse volume operacional e às metas estratégicas da organização.

---

## **2\. Objetivo do Negócio**

Selecionar e implementar uma solução para orquestração de processos _stateful_ que:

*   Substitua o **Camunda 7 Community Edition** por uma solução mais robusta e moderna.
*   Atenda ao volume estimado de **10 mil operações mensais** de forma estável e eficiente, com base no processo **XXX de XXXX (XXX)**.
*   Ofereça escalabilidade para demandas futuras.
*   Simplifique a integração entre sistemas internos e externos.
*   Alinhe-se à estratégia organizacional de modernização tecnológica e otimização de processos.

---

## **3\. Definição do Problema**

Atualmente, a companhia utiliza o **Camunda 7 Community Edition** como solução principal para orquestração de processos _stateful_. Embora esta solução tenha atendido às necessidades iniciais da organização, desafios importantes têm surgido com o crescimento das demandas operacionais e estratégicas:

1.  **Custo da Licença da Versão Enterprise**:
    *   A ausência de funcionalidades avançadas presentes na versão Enterprise do Camunda 7 limita a eficiência e a produtividade operacional. No entanto, o alto custo da licença para migração à versão Enterprise gera a oportunidade de analisar alternativas.
2.  **Necessidade de Modernização Tecnológica**:
    *   O Camunda 7 possui uma arquitetura tradicional que depende de um modelo on-premises ou de infraestrutura pesada em nuvem, dificultando a escalabilidade horizontal. A companhia busca soluções mais _cloud-native_, capazes de integrar-se de forma nativa com serviços de Kubernetes e infraestrutura moderna em nuvem, como AWS e Azure.
3.  **Manutenção e Integração**:
    *   A manutenção do Camunda 7 Community Edition exige um esforço significativo por parte da equipe técnica para gerenciar atualizações, monitorar a infraestrutura e integrar o motor de orquestração com sistemas externos. Essas atividades aumentam os custos operacionais e reduzem a eficiência da equipe de TI.

Esses problemas levam a atrasos em processos críticos, custos operacionais elevados e uma incapacidade de acompanhar a modernização tecnológica necessária para sustentar o crescimento da organização. Como resposta, a empresa está analisando alternativas que ofereçam um modelo mais sustentável, escalável e econômico, alinhado às suas metas estratégicas.

---

## **4\. Solução Proposta**

Implementação de uma solução moderna para substituir o **Camunda 7 Community Edition**, com as seguintes premissas:

*   Suporte a **10 mil operações mensais**, com possibilidade de expansão.
*   Robustez, escalabilidade e confiabilidade garantidas.
*   Simplicidade na modelagem e monitoramento de processos complexos.
*   Suporte técnico confiável e documentação abrangente.
*   Integração com logs de monitoramento para acompanhamento de desempenho e métricas operacionais.

A ferramenta selecionada deve oferecer as seguintes **funcionalidades de orquestração de workflows** _**stateful**_, compatíveis com padrões como BPMN (_Business Process Model and Notation_). **Caso a ferramenta não possua esse suporte nativo, será necessário construir funcionalidades adicionais para atendê-las**:

1.  **Eventos de Início e Fim**
    *   _Start Event_ e _End Event_: Definição clara dos pontos de entrada e saída dos processos.
2.  **Tarefas**
    *   _Send Task_ e _Receive Task_: Comunicação síncrona ou assíncrona entre sistemas.
    *   _Service Task_: Execução de serviços automatizados.
    *   _Human Task_: Interações manuais no fluxo do processo.
    *   _External Task_: Suporte a tarefas gerenciadas por trabalhadores externos ou microservices independentes.
3.  **Gateways**
    *   _Exclusive Gateway_: Decisões exclusivas para direcionar o fluxo de acordo com condições específicas.
4.  **Eventos Intermediários**
    *   _Link Intermediate Throw Event_ e _Link Intermediate Catch Event_: Conexões entre diferentes partes do fluxo de trabalho para maior flexibilidade e modularidade.
5.  **Eventos de Mensagem**
    *   _Message Events_: Para envio e recebimento de mensagens entre processos ou sistemas externos, promovendo comunicação entre diferentes serviços.
6.  **Subprocessos**
    *   _Subprocess Invocation_: Capacidade de reutilizar subprocessos dentro do fluxo principal, promovendo modularidade e reuso.
7.  **Eventos de Tempo**
    *   _Timer Boundary Event (Non-Interrupting)_: Temporizadores associados a tarefas ou subprocessos, permitindo atrasos ou prazos sem interromper o processo principal.
8.  **Compensação**
    *   _Compensation Events_: Permitem reverter etapas ou transações em caso de falhas, garantindo consistência nos processos e maior controle sobre erros.

---

## **5\. Alternativas Consideradas**

### **Opção 1: Camunda 8 (AWS)**

#### **a. Benefícios e Valor**

*   **Modernização:** Arquitetura _cloud-native_, construída para funcionar de forma nativa em ambientes Kubernetes, com suporte robusto para escalabilidade horizontal.
*   **Eficiência Operacional:** Ferramentas avançadas para modelagem e monitoramento de processos, permitindo maior visibilidade e controle.
*   **Flexibilidade:** Compatibilidade total com BPMN 2.0, o que facilita a transição do Camunda 7 para o Camunda 8.
*   **Escalabilidade:** Suporte robusto para processos de alto volume, com capacidade de expansão horizontal e integração simplificada com ambientes _cloud-native_.

---

#### **b. Análise de Gap com o Camunda 7**

##### **1\. Gaps de Funcionalidade**

| **Funcionalidade** | **Camunda 7** | **Camunda 8** | **Gap** |
| --- | --- | --- | --- |
| Arquitetura _Cloud-native_ | Não | Sim | Modernização significativa |
| Suporte a Kubernetes | Limitado | Nativo | Integração aprimorada |
| Visualização de Processos | Básico | Avançado | Melhoria significativa |
| Escalabilidade Horizontal | Limitada | Alta | Robustez na escala |
| Gerenciamento de Usuários | Básico (versão CE) | Avançado | Controle aprimorado |

##### **2\. Gaps de Features do Workflow**

| **Item de Workflow** | **Camunda 7** | **Camunda 8** | **Gap** |
| --- | --- | --- | --- |
| **Eventos de Início e Fim** | Suporte total | Suporte total | Sem diferença |
| **Send Task e Receive Task** | Suporte total | Suporte total | Sem diferença |
| **Service Task** | Suporte total | Suporte total | Sem diferença |
| **Human Task** | Suporte total | Suporte total | Sem diferença |
| **External Task** | Suporte total | Suporte total | Sem diferença |
| **Exclusive Gateway** | Suporte total | Suporte total | Sem diferença |
| **Link Intermediate Events** | Suporte parcial | Suporte total | Melhoria no suporte a _Throw_ e _Catch_ para modularidade. |
| **Message Events** | Suporte parcial | Suporte total | Melhoria significativa na comunicação com sistemas externos. |
| **Subprocess Invocation** | Suporte total | Suporte total | Sem diferença |
| **Timer Boundary Event** | Suporte total | Suporte total | Sem diferença |
| **Compensation Events** | Suporte parcial | Suporte total | Melhoria na gestão de falhas e compensações. |

---

#### **c. Prós e Contras**

*   **Prós:**
    *   Arquitetura moderna e escalável.
    *   Ferramentas avançadas para monitoramento e visualização de processos.
    *   Suporte completo aos itens de workflow levantados no item 4.
    *   Transição mais simples para equipes já familiarizadas com o Camunda.
*   **Contras:**
    *   **Gap em Link Intermediate Events:** O suporte limitado no Camunda 7 pode exigir ajustes significativos em fluxos existentes.
    *   **Gap em Message Events:** Diferença significativa no suporte, com necessidade de reconfiguração para integração com sistemas externos.
    *   **Gap em Compensation Events:** A construção de compensações pode exigir esforço técnico adicional e aumento de custo.

---

#### **d. Análise de Riscos**

*   **Riscos Identificados:**
    *   **Adaptação a novos componentes:** As diferenças nos itens de workflow podem gerar atrasos e custos adicionais.
    *   **Complexidade técnica:** A construção de componentes compensatórios pode aumentar o tempo de implementação e custos gerais.
    *   **Treinamento técnico:** A curva de aprendizado para equipes que utilizam o Camunda 7 pode ser alta.
*   **Mitigação:**
    *   Planejamento detalhado para adaptação de processos existentes ao novo suporte do Camunda 8.
    *   Investimento em treinamento técnico para equipes de desenvolvimento.
    *   Construção de componentes compensatórios para gaps identificados (_Link Intermediate Events_, _Message Events_ e _Compensation Events_).

---

#### **e. Custo Total**

**1\. Custo de Licença:**

*   \<\< Place holder para valor da licença>>**.**

**2\. Custo de Infraestrutura:**

| **Componente** | **Configuração** | **Custo Unitário (USD/hora)** | **Horas/Mês** | **Custo Mensal (USD)** | **Link de Referência** |
| --- | --- | --- | --- | --- | --- |
| **Amazon EKS Cluster** | 1 cluster | $0,10 | 730 | $73,00 | [AWS EKS Pricing](https://aws.amazon.com/eks/pricing/) |
| **Amazon RDS** | db.t3.medium, 5 GB armazenamento | $0,0416 | 730 | $30,37 | [AWS RDS Pricing](https://aws.amazon.com/rds/pricing/) |
| **Amazon EC2** | 3 instâncias t3.medium | $0,0416 | 730 | $91,10 | [AWS EC2 Pricing](https://aws.amazon.com/ec2/pricing/on-demand/) |
| **Armazenamento EBS** | 20 GB por nó (3 nós) | $0,10 por GB/mês | N/A | $6,00 | [AWS EBS Pricing](https://aws.amazon.com/ebs/pricing/) |
| **Transferência de Dados** | 100 GB/mês | $0,09 por GB | N/A | $9,00 | [AWS DataTransfer Pricing](https://aws.amazon.com/blogs/containers/understanding-data-transfer-costs-for-aws-container-services/) |
| **CloudWatch Logs e Métricas** | Logs e monitoramento básico | ~$0,50/GB de logs | N/A | $10,00 | [AWS CloudWatchPricing](https://aws.amazon.com/cloudwatch/pricing/) |
| **Application Load Balancer** | Balanceador para tráfego | ~$0,025 | 730 | $18,25 | [AWS ALBPricing](https://aws.amazon.com/elasticloadbalancing/pricing/) |
| **ElastiCache (opcional)** | Redis ou Memcached (pequeno) | ~$0,020 | 730 | $15,00 | [AWS ElastiCachePricing](https://aws.amazon.com/elasticache/pricing/) |
| **Certificados SSL (ACM)** | HTTPS/TLS para comunicação segura | Gratuito | N/A | $0,00 | [AWS ACMPricing](https://aws.amazon.com/certificate-manager/pricing/) |

**Custo Mensal Estimado de Infraestrutura:** **$253,22.**

**3\. Custo de Componentes Compensatórios:**

| **Componente** | **Descrição** | **Custo Estimado (USD)** |
| --- | --- | --- |
| **Link Intermediate Events** | Ajustes em fluxos para melhorar modularidade. | $3.000,00 |
| **Message Events** | Implementação adicional para comunicação externa. | $5.000,00 |
| **Compensation Events** | Construção de componentes para gestão avançada de compensações. | $7.000,00 |

**Total dos Componentes Compensatórios:** $15.000,00 (custo único).

**Custo Total Estimado (Mensal + Único):**

*   Mensal: **$253,22.**
*   Único: **$15.000,00.**

---

#### **f. Esforço de Construção da Arquitetura de Referência**

*   Investimento inicial em treinamento técnico: **$5.000,00.**

---

### **Opção 2: Bamoe (Business Automation Manager Open Edition)**

#### **a. Benefícios e Valor**

*   **Flexibilidade:** Integração nativa com OpenShift e suporte a regras de negócios (Drools).
*   **Custo Acessível:** Solução open-source sem licenciamento direto.
*   **Compatibilidade:** Suporte a BPMN 2.0, permitindo modelagem estruturada de processos.

---

#### **b. Análise de Gap com o Camunda 7**

##### **1\. Gaps de Funcionalidade**

| **Funcionalidade** | **Camunda 7** | **Bamoe** | **Gap** |
| --- | --- | --- | --- |
| Suporte a BPMN | Sim | Sim | Similar |
| Suporte a Regras (Drools) | Não | Sim | Adição importante |
| Escalabilidade Horizontal | Limitada | Limitada | Sem ganho significativo |
| Comunidade e Suporte | Ampla | Menor | Desvantagem |

##### **2\. Gaps de Features do Workflow**

| **Item de Workflow** | **Camunda 7** | **Bamoe** | **Gap** |
| --- | --- | --- | --- |
| **Eventos de Início e Fim** | Suporte total | Suporte total | Sem diferença |
| **Send Task e Receive Task** | Suporte total | Suporte parcial | Configuração manual mais trabalhosa. |
| **Service Task** | Suporte total | Suporte total | Sem diferença |
| **Human Task** | Suporte total | Suporte total | Sem diferença |
| **External Task** | Suporte parcial | Suporte parcial | Funcionalidade básica, menos flexível que o Camunda 8. |
| **Exclusive Gateway** | Suporte total | Suporte total | Sem diferença |
| **Link Intermediate Events** | Suporte parcial | Suporte parcial | Sem melhorias significativas. |
| **Message Events** | Suporte total | Suporte total | Sem diferença |
| **Subprocess Invocation** | Suporte total | Suporte total | Sem diferença |
| **Timer Boundary Event** | Suporte total | Suporte total | Sem diferença |
| **Compensation Events** | Suporte parcial | Suporte parcial | Configuração mais trabalhosa comparada ao Camunda 8. |

---

#### **c. Prós e Contras**

*   **Prós:**
    *   Sem custo de licenciamento.
    *   Suporte a BPMN e regras de negócios (Drools).
*   **Contras:**
    *   **Gap em Send Task e Receive Task**: Configuração mais complexa.
    *   **Gap em External Task**: Suporte básico com menor flexibilidade.
    *   **Gap em Compensation Events**: Exige esforço adicional para compensações.

---

#### **d. Análise de Riscos**

*   **Riscos Identificados:**
    *   **Complexidade na implementação de workflows:** Diferenças nos itens de workflow podem gerar atrasos.
    *   **Documentação limitada:** Pode dificultar o suporte técnico e a adoção.
*   **Mitigação:**
    *   Construir componentes compensatórios para os gaps identificados (_Send Task_, _External Task_ e _Compensation Events_).
    *   Investir em suporte técnico especializado.

---

#### **e. Custo Total**

**1\. Custo de Licença:** Gratuito.

**2\. Custo de Infraestrutura:**

_(Estimativa baseada em uma configuração similar ao Camunda 8, totalizando $253,22/mês.)_

| **Componente** | **Configuração** | **Custo Unitário (USD/hora)** | **Horas/Mês** | **Custo Mensal (USD)** | **Link de Referência** |
| --- | --- | --- | --- | --- | --- |
| **Amazon EKS Cluster** | 1 cluster | $0,10 | 730 | $73,00 | [AWS EKS Pricing](https://aws.amazon.com/eks/pricing/) |
| **Amazon RDS** | db.t3.medium, 5 GB armazenamento | $0,0416 | 730 | $30,37 | [AWS RDS Pricing](https://aws.amazon.com/rds/pricing/) |
| **Amazon EC2** | 3 instâncias t3.medium | $0,0416 | 730 | $91,10 | [AWS EC2 Pricing](https://aws.amazon.com/ec2/pricing/on-demand/) |
| **Armazenamento EBS** | 20 GB por nó (3 nós) | $0,10 por GB/mês | N/A | $6,00 | [AWS EBS Pricing](https://aws.amazon.com/ebs/pricing/) |
| **Transferência de Dados** | 100 GB/mês | $0,09 por GB | N/A | $9,00 | [AWS DataTransfer Pricing](https://aws.amazon.com/blogs/containers/understanding-data-transfer-costs-for-aws-container-services/) |
| **CloudWatch Logs e Métricas** | Logs e monitoramento básico | ~$0,50/GB de logs | N/A | $10,00 | [AWS CloudWatchPricing](https://aws.amazon.com/cloudwatch/pricing/) |
| **Application Load Balancer** | Balanceador para tráfego | ~$0,025 | 730 | $18,25 | [AWS ALBPricing](https://aws.amazon.com/elasticloadbalancing/pricing/) |
| **ElastiCache (opcional)** | Redis ou Memcached (pequeno) | ~$0,020 | 730 | $15,00 | [AWS ElastiCachePricing](https://aws.amazon.com/elasticache/pricing/) |
| **Certificados SSL (ACM)** | HTTPS/TLS para comunicação segura | Gratuito | N/A | $0,00 | [AWS ACMPricing](https://aws.amazon.com/certificate-manager/pricing/) |

**3\. Custo de Componentes Compensatórios:**

| **Componente** | **Descrição** | **Custo Estimado (USD)** |
| --- | --- | --- |
| **Send Task e Receive Task** | Ajustes para comunicação mais eficiente. | $4.000,00 |
| **External Task** | Implementação de flexibilidade adicional. | $6.000,00 |
| **Compensation Events** | Construção de componentes para gestão avançada de compensações. | $8.000,00 |

**Total dos Componentes Compensatórios:** $18.000,00 (custo único).

**Custo Total Estimado (Mensal + Único):**

*   Mensal: **$253,22.**
*   Único: **$18.000,00.**

---

#### **f. Esforço de Construção da Arquitetura de Referência**

*   Investimento inicial em treinamento técnico: **$8.000,00.**

### **Opção 3: Step Functions (AWS)**

#### **a. Benefícios e Valor**

*   **Escalabilidade:** Alta capacidade para volumes superiores a **10 mil operações mensais**, ideal para demandas crescentes.
*   **Modelo Gerenciado:** A infraestrutura gerenciada pela AWS elimina a necessidade de manutenção detalhada.
*   **Integração com o Ecossistema AWS:** Comunicação direta e nativa com serviços como Lambda, DynamoDB, S3 e SNS.
*   **Custo Baseado no Uso:** Modelo _pay-as-you-go_, reduzindo despesas fixas e otimizando custos para cenários variáveis.

---

#### **b. Análise de Gap com o Camunda 7**

##### **1\. Gaps de Funcionalidade**

| **Funcionalidade** | **Camunda 7** | **Step Functions** | **Gap** |
| --- | --- | --- | --- |
| Suporte a BPMN | Sim | Não | Perda de padronização |
| Escalabilidade Horizontal | Limitada | Alta | Vantagem significativa |
| Integração com Serviços Externos | Limitada | Avançada | Comunicação aprimorada |
| Modelo Gerenciado | Não | Sim | Redução de esforço técnico |

##### **2\. Gaps de Features do Workflow**

| **Item de Workflow** | **Camunda 7** | **Step Functions** | **Gap** |
| --- | --- | --- | --- |
| **Eventos de Início e Fim** | Suporte total | Suporte parcial | Necessidade de adaptação. |
| **Send Task e Receive Task** | Suporte total | Não disponível | Construção necessária para comunicação síncrona. |
| **Service Task** | Suporte total | Suporte total | Sem diferença. |
| **Human Task** | Suporte total | Não disponível | Requer implementação externa. |
| **External Task** | Suporte total | Não disponível | Construção necessária. |
| **Exclusive Gateway** | Suporte total | Parcial | Adaptação para suportar decisão baseada em lógica complexa. |
| **Link Intermediate Events** | Suporte parcial | Não disponível | Necessidade de adaptação. |
| **Message Events** | Suporte parcial | Não disponível | Construção necessária. |
| **Subprocess Invocation** | Suporte total | Não disponível | Requer implementação adicional. |
| **Timer Boundary Event** | Suporte total | Suporte parcial | Necessidade de adaptação para temporizadores não-interruptivos. |
| **Compensation Events** | Suporte parcial | Não disponível | Construção de compensações necessária. |

---

#### **c. Prós e Contras**

*   **Prós:**
    *   Alta escalabilidade e desempenho.
    *   Infraestrutura gerenciada reduz esforço técnico.
    *   Integração nativa com o ecossistema AWS.
*   **Contras:**
    *   Ausência de suporte nativo ao BPMN.
    *   Diferenças significativas nos itens de workflow requerem adaptações.
    *   Dependência de serviços AWS (vendor lock-in).

---

#### **d. Análise de Riscos**

*   **Riscos Identificados:**
    *   **Perda de padronização:** Ausência de suporte ao BPMN pode dificultar a adoção para equipes acostumadas ao modelo.
    *   **Dependência da AWS:** Forte _vendor lock-in_ pode limitar opções futuras de migração.
    *   **Gaps em Workflows:** Diferenças funcionais podem levar a atrasos na implementação.
*   **Mitigação:**
    *   Construir componentes compensatórios para os gaps identificados (_Send Task_, _Message Events_, _Compensation Events_, entre outros).
    *   Treinamento técnico intensivo para equipes de desenvolvimento.
    *   Planejamento detalhado para adaptação de processos existentes.

---

#### **e. Custo Total**

**1\. Custo de Licença:**

*   Modelo _pay-as-you-go_: **$0,025 por mil execuções**.

**2\. Custo de Infraestrutura:**

*   Gerenciado diretamente pela AWS; custos de execução baseados no volume de operações.

| **Componente** | **Configuração** | **Custo Unitário (USD)** | **Volume Estimado** | **Custo Mensal (USD)** |
| --- | --- | --- | --- | --- |
| **Execuções de Fluxo** | $0,025 por mil execuções | $0,025 | 10.000 operações | $0,25 |

**3\. Custo de Componentes Compensatórios:**

| **Componente** | **Descrição** | **Custo Estimado (USD)** |
| --- | --- | --- |
| **Send Task e Receive Task** | Construção de comunicação síncrona. | $4.000,00 |
| **Message Events** | Implementação para comunicação externa. | $5.000,00 |
| **Human Task** | Adaptação para gerenciar tarefas humanas. | $8.000,00 |
| **Compensation Events** | Construção de componentes para gestão avançada de compensações. | $7.000,00 |
| **Subprocess Invocation** | Implementação de subprocessos reutilizáveis. | $6.000,00 |

**Total dos Componentes Compensatórios:** **$30.000,00 (custo único).**

**Custo Total Estimado (Mensal + Único):**

*   Mensal: **$0,25 + custos variáveis baseados em volume.**
*   Único: **$30.000,00.**

---

#### **f. Esforço de Construção da Arquitetura de Referência**

*   Investimento inicial em treinamento técnico: **$3.000,00.**

---

## **7\. Recomendação**

Após análise detalhada, recomenda-se a migração para o **Camunda 8**, devido à sua arquitetura _cloud-native_, escalabilidade robusta e suporte completo ao BPMN. Embora o custo inicial de tempo e infraestrutura seja maior em comparação a outras opções, a solução atende melhor aos objetivos estratégicos da organização.

---

## **8\. Conclusão**

O Camunda 8 é a melhor alternativa para substituir o Camunda 7 Community Edition, proporcionando escalabilidade, modernização tecnológica e alinhamento com as metas organizacionais de expansão e eficiência operacional.
