# Usando o AISVS

O Padrão de Verificação de Segurança da Inteligência Artificial (AISVS) define os requisitos de segurança para aplicações e serviços de IA modernos, concentrando-se em aspectos sob o controle dos desenvolvedores de aplicações.

O AISVS destina-se a qualquer pessoa que desenvolva ou avalie a segurança de aplicações de IA, incluindo desenvolvedores, arquitetos, engenheiros de segurança e auditores. Este capítulo apresenta a estrutura e o uso do AISVS, incluindo seus níveis de verificação e casos de uso pretendidos.

## Níveis de Verificação de Segurança da Inteligência Artificial

O AISVS define três níveis crescentes de verificação de segurança. Cada nível adiciona profundidade e complexidade, permitindo que as organizações ajustem sua postura de segurança ao nível de risco de seus sistemas de IA.

Organizações podem começar no Nível 1 e adotar progressivamente níveis mais altos à medida que a maturidade de segurança e a exposição a ameaças aumentam.

### Definição dos Níveis

Cada requisito no AISVS v1.0 é atribuído a um dos seguintes níveis:

#### Requisitos do Nível 1

O Nível 1 inclui os requisitos de segurança mais críticos e fundamentais. Eles se concentram em prevenir ataques comuns que não dependem de outras pré-condições ou vulnerabilidades. A maioria dos controles do Nível 1 é fácil de implementar ou suficientemente essencial para justificar o esforço.

#### Requisitos do Nível 2

O Nível 2 aborda ataques mais avançados ou menos comuns, bem como defesas em camadas contra ameaças generalizadas. Esses requisitos podem envolver lógica mais complexa ou ter como alvo pré-requisitos de ataque específicos.

#### Requisitos do Nível 3

O Nível 3 inclui controles que normalmente são mais difíceis de implementar ou cuja aplicabilidade é situacional. Estes costumam representar mecanismos de defesa em profundidade ou mitigação contra ataques de nicho, direcionados ou de alta complexidade.

### Função (D/V)

Cada requisito AISVS é marcado de acordo com o público-alvo principal:

* D – Requisitos voltados para desenvolvedores
* V – Requisitos voltados para verificador/auditor
* D/V – Relevante para desenvolvedores e verificadores

