
## **Business Case: Orquestração de Processos Stateful**


## **1\. Resumo Executivo**

Este documento avalia alternativas de ferramentas para orquestração de processos _stateful_ de forma eficiente, escalável e confiável.

Atualmente, a organização utiliza o **Camunda 7 Community Edition**, que, embora tenha atendido às necessidades iniciais, enfrenta limitações técnicas e estratégicas para suportar o crescimento e modernização. Entre as opções consideradas estão: **Camunda 8**, **Bamoe**, e **Step Functions (AWS)**.

A análise considera critérios como custo de licença, custo de infraestrutura, esforço para construção da arquitetura de referência, escalabilidade, facilidade de uso, suporte e integração com os sistemas existentes. A recomendação final será baseada na capacidade de cada solução em atender a esse volume operacional e às metas estratégicas da organização.

---

## **2\. Objetivo do Negócio**

Selecionar e implementar uma solução para orquestração de processos _stateful_ que:

*   Substitua o **Camunda 7 Community Edition** por uma solução mais robusta e moderna.
Atenda ao volume estimado de **10.000 operações mensais** de maneira estável e eficiente. Esse volume foi definido com base no processo **XXX de XXXX (XXX)**, utilizado como referência na elaboração deste estudo de viabilidade, daqui em diante chamado de Processo Piloto.
*   Ofereça escalabilidade para demandas futuras.
*   Simplifique a integração entre sistemas internos e externos.
*   Alinhe-se à estratégia organizacional de modernização tecnológica e otimização de processos.

---

## **3\. Definição do Problema**

Atualmente, a companhia utiliza o **Camunda 7 Community Edition** como solução principal para orquestração de processos _stateful_. Embora esta solução tenha atendido às necessidades iniciais da organização, desafios importantes têm surgido com o crescimento das demandas operacionais e estratégicas:

1.  **Custo da Licença da Versão Enterprise**:
    *   A ausência de funcionalidades avançadas presentes na versão Enterprise do Camunda 7 limita a eficiência e a produtividade operacional. No entanto, o alto custo da licença para migração à versão Enterprise gera a oportunidade de analisar alternativas.
2.  **Necessidade de Modernização Tecnológica**:
    *   O Camunda 7 possui uma arquitetura tradicional que depende de um modelo on-premises ou de infraestrutura pesada em nuvem, dificultando a escalabilidade horizontal. A companhia busca soluções mais _cloud-native_, capazes de integrar-se de forma nativa com serviços de Kubernetes e infraestrutura moderna em nuvem, como AWS e Azure.
3.  **Manutenção e Integração**:
    *   A manutenção do Camunda 7 Community Edition exige um esforço significativo por parte da equipe técnica para gerenciar atualizações, monitorar a infraestrutura e integrar o motor de orquestração com sistemas externos. Essas atividades aumentam os custos operacionais e reduzem a eficiência da equipe de TI.

Esses problemas levam a atrasos em processos críticos, custos operacionais elevados e uma incapacidade de acompanhar a modernização tecnológica necessária para sustentar o crescimento da organização. Como resposta, a empresa está analisando alternativas que ofereçam um modelo mais sustentável, escalável e econômico, alinhado às suas metas estratégicas.

---

## **4\. Solução Proposta**

Implementação de uma solução moderna para substituir o **Camunda 7 Community Edition**, com as seguintes premissas:

*   Suporte a **10 mil operações mensais**, com possibilidade de expansão.
*   Robustez, escalabilidade e confiabilidade garantidas.
*   Simplicidade na modelagem e monitoramento de processos complexos.
*   Suporte técnico confiável e documentação abrangente.
*   Integração com logs de monitoramento para acompanhamento de desempenho e métricas operacionais.

A ferramenta selecionada deve oferecer as seguintes **funcionalidades de orquestração de workflows** _**stateful**_, compatíveis com padrões como BPMN (_Business Process Model and Notation_). **Caso a ferramenta não possua esse suporte nativo, será necessário construir funcionalidades adicionais para atendê-las**:

1.  **Eventos de Início e Fim**
    *   _Start Event_ e _End Event_: Definição clara dos pontos de entrada e saída dos processos.
2.  **Tarefas**
    *   _Send Task_ e _Receive Task_: Comunicação síncrona ou assíncrona entre sistemas.
    *   _Service Task_: Execução de serviços automatizados.
    *   _Human Task_: Interações manuais no fluxo do processo.
    *   _External Task_: Suporte a tarefas gerenciadas por trabalhadores externos ou microservices independentes.
3.  **Gateways**
    *   _Exclusive Gateway_: Decisões exclusivas para direcionar o fluxo de acordo com condições específicas.
4.  **Eventos Intermediários**
    *   _Link Intermediate Throw Event_ e _Link Intermediate Catch Event_: Conexões entre diferentes partes do fluxo de trabalho para maior flexibilidade e modularidade.
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

*   **Modernização:** Arquitetura _cloud-native_, construída para funcionar de forma nativa em ambientes Kubernetes, com suporte robusto para escalabilidade horizontal.
*   **Eficiência Operacional:** Ferramentas avançadas para modelagem e monitoramento de processos, permitindo maior visibilidade e controle.
*   **Flexibilidade:** Compatibilidade total com BPMN 2.0, o que facilita a transição do Camunda 7 para o Camunda 8.
*   **Escalabilidade:** Suporte robusto para processos de alto volume, com capacidade de expansão horizontal e integração simplificada com ambientes _cloud-native_.

---

#### **b. Análise de Gap com o Camunda 7**

##### **1\. Funcionalidades**

| **Funcionalidade** | **Camunda 7** | **Camunda 8** | **Gap** |
| --- | --- | --- | --- |
| Arquitetura _Cloud-native_ | Não | Sim | Modernização significativa |
| Suporte a Kubernetes | Limitado | Nativo | Integração aprimorada |
| Visualização de Processos | Básico | Avançado | Melhoria significativa |
| Escalabilidade Horizontal | Limitada | Alta | Robustez na escala |
| Gerenciamento de Usuários | Básico (versão CE) | Avançado | Controle aprimorado |

##### **2\. Itens de Workflow**

| **Item de Workflow** | **Camunda 7** | **Camunda 8** | **Gap** |
| --- | --- | --- | --- |
| **Eventos de Início e Fim** | Suporte total | Suporte total | Sem diferença |
| **Send Task e Receive Task** | Suporte total | Suporte total | Sem diferença |
| **Service Task** | Suporte total | Suporte total | Sem diferença |
| **Human Task** | Suporte total | Suporte total | Sem diferença |
| **External Task** | Suporte total | Suporte total | Sem diferença |
| **Exclusive Gateway** | Suporte total | Suporte total | Sem diferença |
| **Link Intermediate Events** | Suporte parcial | Suporte total | Melhoria no suporte a _Throw_ e _Catch_ para modularidade. |
| **Message Events** | Suporte parcial | Suporte total | Melhoria significativa na comunicação com sistemas externos. |
| **Subprocess Invocation** | Suporte total | Suporte total | Sem diferença |
| **Timer Boundary Event** | Suporte total | Suporte total | Sem diferença |
| **Compensation Events** | Suporte parcial | Suporte total | Melhoria na gestão de falhas e compensações. |

---

#### **c. Análise de Riscos**

*   **Riscos Identificados:**
    *   **Adaptação a novos componentes:** As diferenças nos itens de workflow podem gerar impacto na atualização dos workflows.
*   **Mitigação:**
    *   Planejamento detalhado para adaptação de processos existentes ao novo suporte do Camunda 8.

---

#### **d. Custo Total**

**1\. Custo de Licença:**

*   \<\< Place holder para valor da licença>>**.**

**2\. Custo de Infraestrutura:**

Serviços AWS necessários para deploy de uma solução Camunda.

| **Serviço** | **Configuração** | **Custo Unitário (USD/hora)** | **Horas/Mês** | **Custo Mensal (USD)** | **Link de Referência** |
| --- | --- | --- | --- | --- | --- |
| **Amazon EKS Cluster** | 1 cluster | $0,10 | 730 | $73,00 | [AWS EKS Pricing](https://aws.amazon.com/eks/pricing/) |
| **Amazon RDS** | db.t3.medium, 5 GB armazenamento | $0,0416 | 730 | $30,37 | [AWS RDS Pricing](https://aws.amazon.com/rds/pricing/) |
| **Amazon EC2** | 3 instâncias t3.medium | $0,0416 | 730 | $91,10 | [AWS EC2 Pricing](https://aws.amazon.com/ec2/pricing/on-demand/) |
| **Armazenamento EBS** | 20 GB por nó (3 nós) | $0,10 por GB/mês | N/A | $6,00 | [AWS EBS Pricing](https://aws.amazon.com/ebs/pricing/) |
| **Transferência de Dados** | 100 GB/mês | $0,09 por GB | N/A | $9,00 | [AWS DataTransfer Pricing](https://aws.amazon.com/blogs/containers/understanding-data-transfer-costs-for-aws-container-services/) |
| **CloudWatch Logs e Métricas** | Logs e monitoramento básico | ~$0,50/GB de logs | N/A | $10,00 | [AWS CloudWatchPricing](https://aws.amazon.com/cloudwatch/pricing/) |
| **Application Load Balancer** | Balanceador para tráfego | ~$0,025 | 730 | $18,25 | [AWS ALBPricing](https://aws.amazon.com/elasticloadbalancing/pricing/) |
| **ElastiCache (opcional)** | Redis ou Memcached (pequeno) | ~$0,020 | 730 | $15,00 | [AWS ElastiCachePricing](https://aws.amazon.com/elasticache/pricing/) |
| **Certificados SSL (ACM)** | HTTPS/TLS para comunicação segura | Gratuito | N/A | $0,00 | [AWS ACMPricing](https://aws.amazon.com/certificate-manager/pricing/) |

**Custo Mensal Estimado de Infraestrutura:** **$253,22.**

**3\. Custo de Construção de Arquitetura de Referência**

| **Nível do Profissional** | **Esforço em Horas** | **Custo Estimado (Reais)** |
| --- | --- | --- |
| **N11** | 200  | << place holder>> |
| **N10** | 200  | << place holder>> |
| **N9** | 200 | << place holder>> |

**Custo total de Construção da Arquitetura de Referência:** << place holder >> (custo único).

**4\. Custo de Migração do Processo Piloto**

| **Nível do Profissional** | **Esforço em Horas** | **Custo Estimado (Reais)** |
| --- | --- | --- |
| **N11** | 200  | << place holder>> |
| **N10** | 200  | << place holder>> |
| **N9** | 200 | << place holder>> |

**Custo total de Migração do do Processo Piloto :** << place holder >> (custo único).

---

#### **e. Prós e Contras**

*   **Prós:**
    *   Arquitetura moderna e escalável.
    *   Ferramentas avançadas para monitoramento e visualização de processos.
    *   Suporte completo aos itens de workflow levantados no item 4.
    *   Transição mais simples para equipes já familiarizadas com o Camunda.
*   **Contras:**
    *   Alto custo de licença para a versão Enterprise, o que pode impactar o orçamento inicial.


---

### **Opção 2: Bamoe (Business Automation Manager Open Edition)**

<< TO -DO >>

---

### **Opção 3: AWS Step Functions**

---

#### **a. Benefícios e Valor**

- **Modernização:** Arquitetura gerenciada e _cloud-native_, eliminando a necessidade de manutenção de infraestrutura local. Ideal para cenários serverless.
- **Eficiência Operacional:** Modelo _pay-as-you-go_ reduz custos fixos, enquanto o monitoramento por CloudWatch oferece visibilidade sobre os workflows.
- **Flexibilidade:** Permite criar workflows personalizados em JSON, com integração nativa a serviços AWS e suporte para APIs externas.
- **Escalabilidade:** Suporte robusto para volumes elevados de operações, com execução distribuída e resiliência.

---

#### **b. Análise de Gap com o Camunda 7**

##### **1. Funcionalidades**

| **Funcionalidade**        | **Camunda 7** | **Step Functions** | **Gap**                                       |
|---------------------------|---------------|--------------------|-----------------------------------------------|
| BPMN                      | Suporte total | Não suportado      | Perda de padronização visual e modelagem BPMN.|
| Human Task                | Suporte total | Não disponível     | Requer integração com sistemas externos.      |
| Compensation Events       | Suporte parcial| Não disponível     | Construção manual necessária.                |
| Timer Boundary Event      | Suporte total | Suporte parcial    | Simulação limitada com maior complexidade.    |

##### **2. Itens de Workflow**

| **Item de Workflow**        | **Camunda 7** | **Step Functions** | **Gap**                                     | **Solução no Step Functions**                  |
|-----------------------------|---------------|--------------------|---------------------------------------------|-----------------------------------------------|
| Eventos de Início e Fim     | Suporte total | Suporte parcial    | Adaptações para correspondência.           | Usar Task States com lógica inicial e final.  |
| Send Task                   | Suporte total | Não disponível     | Envio de mensagens precisa ser implementado.| Usar Lambda Functions, SQS ou EventBridge.    |
| Receive Task                | Suporte total | Não disponível     | Espera de mensagens externas ausente.      | Callback Pattern com TaskToken ou Wait State. |
| Human Task                  | Suporte total | Não disponível     | Sem suporte nativo para tarefas humanas.   | Notificações via SNS ou interface customizada no S3. |
| Service Task                | Suporte total | Suporte total      | Sem diferença.                             | Utilizar Service Integrations ou Lambda.      |
| Exclusive Gateway           | Suporte total | Parcial            | Adaptação para lógica complexa.            | Choice State com JSONPath Expressions.        |
| Subprocess Invocation       | Suporte total | Não disponível     | Reutilização de subprocessos ausente.      | Invocar workflows aninhados com StartExecution API. |
| Timer Boundary Event        | Suporte total | Suporte parcial    | Timers não-interruptivos precisam de ajuste.| Wait State e EventBridge para eventos assíncronos.  |
| Compensation Events         | Suporte parcial| Não disponível     | Compensação precisa ser implementada.      | Criar lógica manual usando estados paralelos e tokens. |

---

#### **c. Análise de Riscos**

- **Riscos Identificados:**
  - **Perda de padronização:** A ausência de suporte ao BPMN pode dificultar a adaptação para equipes que dependem do modelo.
  - **Complexidade adicional:** Adaptações para workflows podem gerar atrasos e aumentar custos.
  - **Dependência da AWS:** _Vendor lock-in_ pode limitar opções futuras de provedores.
  - **Ineficiência em Human Tasks:** O gerenciamento manual pode impactar a produtividade.
  - **Falta de suporte a Send/Receive Task:** Necessidade de integrações customizadas para comunicação síncrona.

- **Mitigação:**
  - Construir soluções compensatórias para gaps funcionais como Human Tasks e Compensation Events.
  - Capacitação técnica para adaptação ao Step Functions.
  - Planejamento detalhado para migração e integração de sistemas existentes.
  - Uso de Lambda e SQS/EventBridge para emular tarefas síncronas e temporizadores.
  - Interfaces customizadas via S3 para compensar a ausência de tarefas manuais nativas.

---

#### **d. Custo Total**

**1. Custo de Licença:**

- Modelo _pay-as-you-go_ com $0,025 por 1.000 execuções.
- Execuções estimadas: 50.000 operações/mês → $1,25/mês.

**2. Custo de Infraestrutura:**

Serviços AWS necessários para executar o Processo  Piloto no Step Functions. **Como o Step Functions não realiza _compute_ como o Camunda, serviços adicionais da AWS devem ser utilizados para implementar os componentes compensatórios.**

| **Serviço**                  | **Configuração**                     | **Custo Mensal (USD)** | **Descrição**                                                                 |
|------------------------------|-------------------------------------|------------------------|-------------------------------------------------------------------------------|
| **Execuções de Workflow**    | $0,025/1.000 execuções (50k/mês)    | $1,25                 | Custos para orquestração via Step Functions.                                 |
| **AWS Lambda**               | 23 invocações por execução, 10s     | $48,15                | Funções serverless para executar lógica de negócio.                          |
| **HTTP Calls**               | 14 chamadas HTTP por execução       | $17,50                | Chamadas para integração com serviços externos.                              |
| **SQS**                      | 3 filas, 50.000 mensagens por fila  | $0,06                 | Troca de mensagens entre serviços via filas SQS (Standard Queue).            |


**3\. Custo de Construção de Arquitetura de Referência**

| **Nível do Profissional** | **Esforço em Horas** | **Custo Estimado (Reais)** |
| --- | --- | --- |
| **N11** | 400  | << place holder>> |
| **N10** | 400  | << place holder>> |
| **N9** | 800 | << place holder>> |

**Custo total de Construção da Arquitetura de Referência:** << place holder >> (custo único).

**4\. Custo de Migração do Processo Piloto**

| **Nível do Profissional** | **Esforço em Horas** | **Custo Estimado (Reais)** |
| --- | --- | --- |
| **N11** | 400  | << place holder>> |
| **N10** | 400  | << place holder>> |
| **N9** | 600 | << place holder>> |

**Custo total de Migração do do Processo Piloto :** << place holder >> (custo único).

---

#### **e. Prós e Contras**

- **Prós:**
  - Escalabilidade robusta para grandes volumes de operações.
  - Integração nativa com o ecossistema AWS.
  - Infraestrutura totalmente gerenciada, reduzindo a complexidade técnica.
  - Custos ajustados ao uso com o modelo _pay-as-you-go_.

- **Contras:**
  - Perda de padronização devido à ausência de suporte ao BPMN.
  - Gaps em workflows como Human Tasks e Compensation Events, que exigem soluções customizadas.
  - Dependência significativa da AWS, resultando em vendor lock-in.
  - Aumento de custos devido à necessidade de serviços adicionais para implementar gaps funcionais.


---

## **6\. Recomendação**

Após análise detalhada, recomenda-se a migração para o **Camunda 8**, devido à sua arquitetura _cloud-native_, escalabilidade robusta e suporte completo ao BPMN. Embora o custo inicial de tempo e infraestrutura seja maior em comparação a outras opções, a solução atende melhor aos objetivos estratégicos da organização.

---

## **7\. Conclusão**

O Camunda 8 é a melhor alternativa para substituir o Camunda 7 Community Edition, proporcionando escalabilidade, modernização tecnológica e alinhamento com as metas organizacionais de expansão e eficiência operacional.
