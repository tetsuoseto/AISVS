# 10 Robustez Adversarial & Defesa de Privacidade

## Objetivo de Controle

Garantir que os modelos de IA permaneçam confiáveis, preservem a privacidade e resistam a abusos ao enfrentar ataques de evasão, inferência, extração ou envenenamento.

---

## 10.1 Alinhamento de Modelo & Segurança

Proteger contra saídas prejudiciais ou que violem políticas.

|   #    | Descrição                                                                                                                                                                                      | Nível | Papel |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 10.1.1 | Verifique se um conjunto de testes de alinhamento (prompts de equipe vermelha, sondas de jailbreak, conteúdo proibido) está sob controle de versão e é executado em cada lançamento de modelo. |   1   |  D/V  |
| 10.1.2 | Verifique se as barreiras de recusa e de conclusão segura estão sendo aplicadas.                                                                                                               |   1   |   D   |
| 10.1.3 | Verifique se um avaliador automatizado mede a taxa de conteúdo prejudicial e sinaliza regressões além de um limite definido.                                                                   |   2   |  D/V  |
| 10.1.4 | Verifique se o treinamento de counter-jailbreak está documentado e reproduzível.                                                                                                               |   2   |   D   |
| 10.1.5 | Verifique se as provas de conformidade formal de políticas ou monitoramento certificado cobrem domínios críticos.                                                                              |   3   |   V   |

---

## 10.2 Fortalecimento de Exemplos Adversariais

Aumentar a resistência a entradas manipuladas. O treinamento adversarial robusto e a pontuação de referência são as melhores práticas atuais.

|   #    | Descrição                                                                                                                               | Nível | Papel |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 10.2.1 | Verifique se os repositórios do projeto incluem configurações de treinamento adversarial com sementes reproduzíveis.                    |   1   |   D   |
| 10.2.2 | Verifique se a detecção de exemplos adversários gera alertas de bloqueio nos pipelines de produção.                                     |   2   |  D/V  |
| 10.2.4 | Verifique se as provas de robustez certificada ou certificados de limite de intervalo cobrem pelo menos as classes críticas principais. |   3   |   V   |
| 10.2.5 | Verifique se os testes de regressão usam ataques adaptativos para confirmar que não há perda mensurável de robustez.                    |   3   |   V   |

---

## 10.3 Mitigação de Inferência de Membro

Limitar a capacidade de decidir se um registro estava nos dados de treinamento. Privacidade diferencial e mascaramento de pontuação de confiança continuam sendo as defesas mais eficazes conhecidas.

|   #    | Descrição                                                                                                                          | Nível | Papel |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 10.3.1 | Verifique se a regularização de entropia por consulta ou o escalonamento de temperatura reduz predições excessivamente confiantes. |   1   |   D   |
| 10.3.2 | Verifique se o treinamento emprega otimização diferencialmente privativa com limite ε para conjuntos de dados sensíveis.           |   2   |   D   |
| 10.3.3 | Verifique se as simulações de ataque (modelo sombra ou caixa preta) mostram uma AUC de ataque ≤ 0,60 nos dados reservados.         |   2   |   V   |

---

## 10.4 Resistência à Inversão de Modelo

Prevenir a reconstrução de atributos privados. Pesquisas recentes destacam o truncamento de saída e garantias de DP como defesas práticas.

|   #    | Descrição                                                                                                                         | Nível | Papel |
| :----: | --------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 10.4.1 | Verifique se atributos sensíveis nunca são exibidos diretamente; quando necessário, use buckets ou transformações unidirecionais. |   1   |   D   |
| 10.4.2 | Verifique se os limites de taxa de consulta restringem consultas adaptativas repetidas do mesmo princípio.                        |   1   |  D/V  |
| 10.4.3 | Verifique se o modelo foi treinado com ruído de preservação de privacidade.                                                       |   2   |   D   |

---

## 10.5 Defesa contra Extração de Modelo

Detectar e impedir a clonagem não autorizada. É recomendado o uso de marca d'água e análise de padrão de consulta.

|   #    | Descrição                                                                                                                                           | Nível | Papel |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 10.5.1 | Verifique se os gateways de inferência aplicam limites de taxa globais e por-chave de API ajustados ao limite de memorização do modelo.             |   1   |   D   |
| 10.5.2 | Verifique se as estatísticas de query-entropy e input-plurality alimentam um detector de extração automatizada.                                     |   2   |  D/V  |
| 10.5.3 | Verifique se marcas d'água frágeis ou probabilísticas podem ser comprovadas com p < 0,01 em até 1 000 consultas contra uma clonagem suspeita.       |   2   |   V   |
| 10.5.4 | Verifique se as chaves de marca d'água e os conjuntos de gatilho estão armazenados em um módulo de segurança de hardware e rotacionados anualmente. |   3   |   D   |
| 10.5.5 | Verifique se os eventos de alerta de extração incluem consultas ofensivas e estão integrados aos playbooks de resposta a incidentes.                |   3   |   V   |

---

## 10.6 Detecção de Dados Envenenados em Tempo de Inferência

Identifique e neutralize entradas com backdoors ou envenenadas.

|   #    | Descrição                                                                                                                                       | Nível | Papel |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 10.6.1 | Verifique se as entradas passam por um detector de anomalias (por exemplo, STRIP, pontuação de consistência) antes da inferência do modelo.     |   1   |   D   |
| 10.6.2 | Verifique se os limites do detector estão ajustados em conjuntos de validação limpos/contaminados para atingir menos de 5% de falsos positivos. |   1   |   V   |
| 10.6.3 | Verifique se entradas sinalizadas como envenenadas acionam fluxos de bloqueio suave e revisão humana.                                           |   2   |   D   |
| 10.6.4 | Verifique se os detectores são submetidos a testes de resistência com ataques de porta traseira adaptativos e sem gatilho.                      |   2   |   V   |
| 10.6.5 | Verifique se as métricas de eficácia de detecção são registradas e reavaliadas periodicamente com informações atualizadas sobre ameaças.        |   3   |   D   |

---

## 10.7 Adaptação Dinâmica da Política de Segurança

Atualizações de política de segurança em tempo real com base em inteligência de ameaças e análise comportamental.

|   #    | Descrição                                                                                                                                                                       | Nível | Papel |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 10.7.1 | Verifique se as políticas de segurança podem ser atualizadas dinamicamente sem reiniciar o agente, mantendo a integridade da versão da política.                                |   1   |  D/V  |
| 10.7.2 | Verifique se as atualizações da política estão assinadas criptograficamente por pessoal de segurança autorizado e validadas antes da aplicação.                                 |   2   |  D/V  |
| 10.7.3 | Verifique se as alterações dinâmicas na política são registradas com trilhas de auditoria completas, incluindo justificativa, cadeias de aprovação e procedimentos de reversão. |   2   |  D/V  |
| 10.7.4 | Verifique se os mecanismos de segurança adaptativa ajustam a sensibilidade da detecção de ameaças com base no contexto de risco e nos padrões comportamentais.                  |   3   |  D/V  |
| 10.7.5 | Verifique se as decisões de adaptação de política são explicáveis e incluem trilhas de evidências para revisão da equipe de segurança.                                          |   3   |  D/V  |

---

## 10.8 Análise de Segurança Baseada em Reflexão

Validação de segurança por meio de autorreflexão do agente e análise metacognitiva.

|   #    | Descrição                                                                                                                                          | Nível | Papel |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 10.8.1 | Verifique se os mecanismos de reflexão do agente incluem autoavaliação voltada à segurança de decisões e ações.                                    |   1   |  D/V  |
| 10.8.2 | Verifique se as saídas de reflexão são validadas para impedir a manipulação dos mecanismos de autoavaliação por entradas adversárias.              |   2   |  D/V  |
| 10.8.3 | Verifique se a análise de segurança metacognitiva identifica possíveis viés, manipulação ou comprometimento nos processos de raciocínio do agente. |   2   |  D/V  |
| 10.8.4 | Verifique se os avisos de segurança baseados em reflexão acionam fluxos de trabalho de monitoramento aprimorado e intervenção humana potencial.    |   3   |  D/V  |
| 10.8.5 | Verifique se o aprendizado contínuo a partir de reflexões de segurança melhora a detecção de ameaças sem degradar a funcionalidade legítima.       |   3   |  D/V  |

---

## 10.9 Evolução & Segurança de Autoaperfeiçoamento

Controles de segurança para sistemas de agentes capazes de automodificação e evolução.

|   #    | Descrição                                                                                                                       | Nível | Papel |
| :----: | ------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 10.9.1 | Verifique se as capacidades de auto-modificação estão restritas às áreas seguras designadas com limites de verificação formal.  |   1   |  D/V  |
| 10.9.2 | Verifique se as propostas de evolução passam por avaliação de impacto de segurança antes da implementação.                      |   2   |  D/V  |
| 10.9.3 | Verifique se os mecanismos de autoaperfeiçoamento incluem capacidades de rollback com verificação de integridade.               |   2   |  D/V  |
| 10.9.4 | Verifique se a segurança de meta-aprendizagem impede a manipulação adversarial dos algoritmos de melhoria.                      |   3   |  D/V  |
| 10.9.5 | Verifique se a auto-melhora recursiva está limitada por restrições formais de segurança com provas matemáticas de convergência. |   3   |  D/V  |

---

### Referências

* [MITRE ATLAS adversary tactics for ML](https://atlas.mitre.org/)
* [NIST AI Risk Management Framework 1.0, 2023](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [OWASP Top 10 for LLM Applications, 2025](https://owasp.org/www-project-top-10-for-large-language-model-applications/)
* [Adversarial Training: A Survey — Zhao et al., 2024](https://arxiv.org/abs/2410.15042)
* [RobustBench adversarial-robustness benchmark](https://robustbench.github.io/)
* [Membership-Inference & Model-Inversion Risk Survey, 2025](https://www.sciencedirect.com/science/article/abs/pii/S0950705125003867)
* [PURIFIER: Confidence-Score Defense against MI Attacks — AAAI 2023](https://ojs.aaai.org/index.php/AAAI/article/view/26289)
* [Model-Inversion Attacks & Defenses Survey — AI Review, 2025](https://link.springer.com/article/10.1007/s10462-025-11248-0)
* [Comprehensive Defense Framework Against Model Extraction — IEEE TDSC 2024](https://doi.org/10.1109/TDSC.2023.3261327)
* [Fragile Model Watermarking Survey — 2025](https://www.sciencedirect.com/science/article/abs/pii/S0165168425002026)
* [Data Poisoning in Deep Learning: A Survey — Zhao et al., 2025](https://arxiv.org/abs/2503.22759)
* [BDetCLIP: Multimodal Prompting Backdoor Detection — Niu et al., 2024](https://arxiv.org/abs/2405.15269)

