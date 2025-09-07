# Usando o AISVS

A Norma de Verificação de Segurança para Inteligência Artificial (AISVS) define requisitos de segurança para aplicações e serviços de IA modernos, focando em aspectos sob o controle dos desenvolvedores de aplicações.

O AISVS destina-se a qualquer pessoa que desenvolva ou avalie a segurança de aplicações de IA, incluindo desenvolvedores, arquitetos, engenheiros de segurança e auditores. Este capítulo apresenta a estrutura e o uso do AISVS, incluindo seus níveis de verificação e casos de uso previstos.

## Níveis de Verificação de Segurança em Inteligência Artificial

O AISVS define três níveis crescentes de verificação de segurança. Cada nível adiciona profundidade e complexidade, permitindo que as organizações adaptem sua postura de segurança ao nível de risco de seus sistemas de IA.

As organizações podem começar no Nível 1 e progredivamente adotar níveis mais altos à medida que a maturidade em segurança e a exposição a ameaças aumentam.

### Definição dos Níveis

Cada requisito na AISVS v1.0 é atribuído a um dos seguintes níveis:

#### Requisitos do nível 1

O Nível 1 inclui os requisitos de segurança mais críticos e fundamentais. Estes se concentram em prevenir ataques comuns que não dependem de outras pré-condições ou vulnerabilidades. A maioria dos controles do Nível 1 são ou simples de implementar ou essenciais o suficiente para justificar o esforço.

#### Requisitos do nível 2

O Nível 2 aborda ataques mais avançados ou menos comuns, bem como defesas em camadas contra ameaças generalizadas. Esses requisitos podem envolver lógica mais complexa ou visar pré-requisitos específicos de ataque.

#### Requisitos de Nível 3

O Nível 3 inclui controles que normalmente são mais difíceis de implementar ou têm aplicabilidade situacional. Estes frequentemente representam mecanismos de defesa em profundidade ou mitigações contra ataques específicos, direcionados ou de alta complexidade.

### Função (D/V)

Cada requisito do AISVS é marcado de acordo com o público-alvo principal:

* D – Requisitos focados no desenvolvedor
* V – Requisitos focados no verificador/auditor
* D/V – Relevante tanto para desenvolvedores quanto para verificadores

