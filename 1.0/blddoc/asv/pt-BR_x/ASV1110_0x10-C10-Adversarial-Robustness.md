# 10 Robustez Adversarial & Defesa da Privacidade

## Objetivo de Controle

Garanta que modelos de IA permaneçam confiáveis, com preservação da privacidade e resistentes a abusos ao enfrentarem ataques de evasão, inferência, extração ou envenenamento.

---

## 10.1 Alinhamento do Modelo e Segurança

Previna saídas prejudiciais ou saídas que violem políticas.

|   #    | Descrição                                                                                                                                                                       | Nível | Papel |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 10.1.1 | Verifique se um conjunto de testes de alinhamento (prompts da equipe vermelha, sondas de jailbreak, conteúdo proibido) é versionado e é executado em cada lançamento de modelo. |   1   |  D/V  |
| 10.1.2 | Verifique se as barreiras de recusa e de conclusão segura estão em vigor.                                                                                                       |   1   |   D   |
| 10.1.3 | Verifique se um avaliador automatizado mede a taxa de conteúdo nocivo e sinaliza regressões além de um limiar definido.                                                         |   2   |  D/V  |
| 10.1.4 | Verifique se o treinamento de contra-jailbreak está documentado e é reproduzível.                                                                                               |   2   |   D   |
| 10.1.5 | Verifique se as provas formais de conformidade com políticas ou o monitoramento certificado abrangem domínios críticos.                                                         |   3   |   V   |

---

## 10.2 Endurecimento de Exemplos Adversariais

Aumente a resiliência a entradas manipuladas. O treinamento adversarial robusto e a pontuação de benchmark são as melhores práticas atuais.

|   #    | Descrição                                                                                                                                | Nível | Papel |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 10.2.1 | Verifique se os repositórios do projeto incluem configurações de treinamento adversarial com sementes reprodutíveis.                     |   1   |   D   |
| 10.2.2 | Verifique se a detecção de exemplos adversários gera alertas bloqueantes em pipelines de produção.                                       |   2   |  D/V  |
| 10.2.4 | Verifique se as provas de certified‐robustness ou certificados de limites intervalares cobrem pelo menos as classes críticas principais. |   3   |   V   |
| 10.2.5 | Verifique se os testes de regressão utilizam ataques adaptativos para confirmar que não há perda mensurável de robustez.                 |   3   |   V   |

---

## 10.3 Mitigação da Inferência de Pertencimento

Limite a capacidade de determinar se um registro estava nos dados de treinamento. A privacidade diferencial e o mascaramento da pontuação de confiança continuam sendo as defesas mais eficazes conhecidas.

|   #    | Descrição                                                                                                                   | Nível | Papel |
| :----: | --------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 10.3.1 | Verifique se a regularização da entropia por consulta ou o ajuste de temperatura reduz previsões excessivamente confiantes. |   1   |   D   |
| 10.3.2 | Verifique se o treinamento utiliza ε-bounded differential-private optimization para conjuntos de dados sensíveis.           |   2   |   D   |
| 10.3.3 | Verifique se as simulações de ataque (modelo-sombra ou caixa-preta) mostram AUC de ataque ≤ 0.60 em dados hold-out.         |   2   |   V   |

---

## 10.4 Resistência à Inversão de Modelo

Impedir a reconstrução de atributos privados. Pesquisas recentes destacam o truncamento da saída e garantias de DP como defesas práticas.

|   #    | Descrição                                                                                                                            | Nível | Papel |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 10.4.1 | Verifique se atributos sensíveis nunca são exibidos diretamente; quando necessário, utilize faixas ou transformações unidirecionais. |   1   |   D   |
| 10.4.2 | Verifique se os limites de taxa de consultas limitam consultas adaptativas repetidas do mesmo principal.                             |   1   |  D/V  |
| 10.4.3 | Verifique se o modelo foi treinado com ruído que preserva a privacidade.                                                             |   2   |   D   |

---

## 10.5 Defesa contra a extração de modelos

Detectar e dissuadir clonagem não autorizada. Recomenda-se a marca d'água e a análise de padrões de consulta.

|   #    | Descrição                                                                                                                                                      | Nível | Papel |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 10.5.1 | Verifique se os gateways de inferência aplicam limites de taxa globais e por chave de API, ajustados ao limiar de memorização do modelo.                       |   1   |   D   |
| 10.5.2 | Verifique se a entropia de consulta e a pluralidade de entradas alimentam um detector de extração automatizado.                                                |   2   |  D/V  |
| 10.5.3 | Verifique que marcas d'água frágeis ou probabilísticas podem ser comprovadas com p < 0.01 em ≤ 1 000 consultas contra um clone suspeito.                       |   2   |   V   |
| 10.5.4 | Verifique se as chaves de marca d'água e os conjuntos de gatilhos estão armazenados em um Módulo de Segurança de Hardware (HSM) e são rotacionados anualmente. |   3   |   D   |
| 10.5.5 | Verifique se os eventos de alerta de extração incluem consultas ofensivas e estão integrados com playbooks de resposta a incidentes.                           |   3   |   V   |

---

## 10.6 Detecção de Dados Envenenados em Tempo de Inferência

Identificar e neutralizar entradas com backdoors ou envenenadas.

|   #    | Descrição                                                                                                                                             | Nível | Papel |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 10.6.1 | Verifique se as entradas passam por um detector de anomalias (por exemplo, STRIP, pontuação de consistência) antes da inferência do modelo.           |   1   |   D   |
| 10.6.2 | Verifique se os limiares do detector estão ajustados em conjuntos de validação limpos/envenenados para alcançar menos de 5% de falsos positivos.      |   1   |   V   |
| 10.6.3 | Verifique se as entradas sinalizadas como envenenadas acionam bloqueio suave e fluxos de trabalho de revisão humana.                                  |   2   |   D   |
| 10.6.4 | Verifique se os detectores são submetidos a testes de estresse com ataques de porta dos fundos adaptativos sem gatilho.                               |   2   |   V   |
| 10.6.5 | Verifique se as métricas de eficácia da detecção são registradas e reavaliadas periodicamente com informações de inteligência de ameaças atualizadas. |   3   |   D   |

---

## 10.7 Adaptação Dinâmica da Política de Segurança

Atualizações de políticas de segurança em tempo real com base em inteligência de ameaças e na análise comportamental.

|   #    | Descrição                                                                                                                                                                        | Nível | Papel |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 10.7.1 | Verifique se as políticas de segurança podem ser atualizadas dinamicamente sem reiniciar o agente, mantendo a integridade da versão da política.                                 |   1   |  D/V  |
| 10.7.2 | Verifique se as atualizações de políticas são assinadas criptograficamente por pessoal de segurança autorizado e validadas antes de serem aplicadas.                             |   2   |  D/V  |
| 10.7.3 | Verifique se as alterações dinâmicas de políticas são registradas com trilhas de auditoria completas, incluindo justificativa, cadeias de aprovação e procedimentos de reversão. |   2   |  D/V  |
| 10.7.4 | Verifique se os mecanismos de segurança adaptativos ajustam a sensibilidade da detecção de ameaças com base no contexto de risco e nos padrões de comportamento.                 |   3   |  D/V  |
| 10.7.5 | Verifique se as decisões de adaptação de políticas são explicáveis e incluem trilhas de evidência para revisão pela equipe de segurança.                                         |   3   |  D/V  |

---

## 10.8 Análise de Segurança Baseada em Reflexão

Validação de segurança por meio da autorreflexão do agente e da análise metacognitiva.

|   #    | Descrição                                                                                                                                           | Nível | Papel |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 10.8.1 | Verifique se os mecanismos de reflexão dos agentes incluem autoavaliação com foco em segurança de decisões e ações.                                 |   1   |  D/V  |
| 10.8.2 | Verifique que as saídas de reflexão sejam validadas para evitar a manipulação dos mecanismos de autoavaliação por entradas adversárias.             |   2   |  D/V  |
| 10.8.3 | Verifique se a análise de segurança meta-cognitiva identifica viés potencial, manipulação ou comprometimento nos processos de raciocínio do agente. |   2   |  D/V  |
| 10.8.4 | Verifique se avisos de segurança baseados em reflexão disparam monitoramento aprimorado e fluxos de intervenção humana potenciais.                  |   3   |  D/V  |
| 10.8.5 | Verifique se o aprendizado contínuo a partir de feedback de segurança melhora a detecção de ameaças sem comprometer a funcionalidade legítima.      |   3   |  D/V  |

---

## 10.9 Evolução e Segurança de Autoaperfeiçoamento

Controles de segurança para sistemas de agentes capazes de auto-modificação e evolução.

|   #    | Descrição                                                                                                                                | Nível | Papel |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 10.9.1 | Verifique que as capacidades de auto-modificação estejam restritas às áreas seguras designadas, com limites de verificação formal.       |   1   |  D/V  |
| 10.9.2 | Verifique se as propostas de evolução passam por avaliação de impacto de segurança antes da implementação.                               |   2   |  D/V  |
| 10.9.3 | Verifique se os mecanismos de autoaperfeiçoamento incluem capacidades de rollback com verificação de integridade.                        |   2   |  D/V  |
| 10.9.4 | Verifique se a segurança do metaaprendizado impede a manipulação adversarial de algoritmos de melhoria.                                  |   3   |  D/V  |
| 10.9.5 | Verifique se o auto-aperfeiçoamento recursivo está limitado por restrições formais de segurança, com provas matemáticas de convergência. |   3   |  D/V  |

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

