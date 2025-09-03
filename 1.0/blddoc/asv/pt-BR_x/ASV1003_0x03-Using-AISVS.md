# Usando o AISVS

A Padrão de Verificação de Segurança de Inteligência Artificial (AISVS) define os requisitos de segurança para aplicações e serviços de IA modernos, com foco nos aspectos sob o controle dos desenvolvedores de aplicativos.

O AISVS destina-se a qualquer pessoa que desenvolva ou avalie a segurança de aplicações de IA, incluindo desenvolvedores, arquitetos, engenheiros de segurança e auditores. Este capítulo apresenta a estrutura e o uso do AISVS, incluindo seus níveis de verificação e casos de uso pretendidos.

## Níveis de Verificação de Segurança de Inteligência Artificial

A AISVS define três níveis ascendentes de verificação de segurança. Cada nível acrescenta profundidade e complexidade, permitindo que as organizações ajustem sua postura de segurança ao nível de risco de seus sistemas de IA.

As organizações podem começar no Nível 1 e adotar progressivamente níveis superiores à medida que a maturidade em segurança e a exposição a ameaças aumentam.

### Definição dos Níveis

Cada requisito no AISVS v1.0 é atribuído a um dos seguintes níveis:

#### Requisitos do Nível 1

O Nível 1 inclui os requisitos de segurança mais críticos e fundamentais. Estes se concentram em prevenir ataques comuns que não dependem de outras pré-condições ou vulnerabilidades. A maioria dos controles de Nível 1 é relativamente fácil de implementar ou suficientemente essenciais para justificar o esforço.

#### Requisitos do Nível 2

Nível 2 aborda ataques mais avançados ou menos comuns, bem como defesas em camadas contra ameaças generalizadas. Esses requisitos podem envolver lógica mais complexa ou atingir pré-requisitos específicos de ataque.

#### Requisitos do Nível 3

O Nível 3 inclui controles que geralmente são mais difíceis de implementar ou situacionalmente aplicáveis. Esses frequentemente representam mecanismos de defesa em profundidade ou mitigação contra ataques específicos, direcionados ou de alta complexidade.

### Papel (D/V)

Cada requisito do AISVS está marcado de acordo com o público-alvo principal:

* D – Requisitos focados no desenvolvedor
* V – Requisitos focados em verificador/auditor
* D/V – Relevante tanto para desenvolvedores quanto para verificadores

