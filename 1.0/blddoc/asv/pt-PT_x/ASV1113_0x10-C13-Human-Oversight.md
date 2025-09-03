# C13 Supervisão Humana, Prestação de Contas e Governança

## Objetivo de Controle

Este capítulo fornece requisitos para manter supervisão humana e cadeias de responsabilização claras em sistemas de IA, assegurando explicabilidade, transparência e governança ética ao longo do ciclo de vida da IA.

---

## C13.1 Kill-Switch & Mecanismos de Anulação

Forneça caminhos de desligamento ou de reversão quando for observado um comportamento inseguro do sistema de IA.

|   #    | Descrição                                                                                                                                       | Nível | Papel |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 13.1.1 | Verifique se existe um mecanismo de interruptor de desligamento manual para interromper imediatamente a inferência do modelo de IA e as saídas. |   1   |  D/V  |
| 13.1.2 | Verifique se os controles de substituição são acessíveis apenas ao pessoal autorizado.                                                          |   1   |   D   |
| 13.1.3 | Verifique se os procedimentos de reversão podem reverter para versões anteriores do modelo ou operações safe-mode.                              |   3   |  D/V  |
| 13.1.4 | Verifique se os mecanismos de sobrescrita são testados regularmente.                                                                            |   3   |   V   |

---

## C13.2 Pontos de Verificação de Decisão com Intervenção Humana

Exigir aprovações humanas quando os montantes em jogo excederem os limites de risco predefinidos.

|   #    | Descrição                                                                                                                                                  | Nível | Papel |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 13.2.1 | Verifique se as decisões de IA de alto risco exigem aprovação humana explícita antes da execução.                                                          |   1   |  D/V  |
| 13.2.2 | Verifique se os limiares de risco estão claramente definidos e acionam automaticamente fluxos de trabalho de revisão humana.                               |   1   |   D   |
| 13.2.3 | Verifique se as decisões sensíveis ao tempo têm procedimentos de contingência quando não for possível obter a aprovação humana dentro dos prazos exigidos. |   2   |   D   |
| 13.2.4 | Verifique se os procedimentos de escalonamento definem níveis de autoridade claros para diferentes tipos de decisão ou categorias de risco, se aplicável.  |   3   |  D/V  |

---

## C13.3 Cadeia de Responsabilidade e Auditabilidade

Registre as ações do operador e as decisões do modelo.

|   #    | Descrição                                                                                                                                                                     | Nível | Papel |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 13.3.1 | Verifique se todas as decisões do sistema de IA e as intervenções humanas são registradas com carimbos de data e hora, identidades dos usuários e a justificativa da decisão. |   1   |  D/V  |
| 13.3.2 | Verifique se os logs de auditoria não podem ser adulterados e inclua mecanismos de verificação de integridade.                                                                |   2   |   D   |

---

## C13.4 Explainable-AI Técnicas

Importância de características superficiais, contra-factuais e explicações locais.

|   #    | Descrição                                                                                                                                                             | Nível | Papel |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 13.4.1 | Verifique se os sistemas de IA fornecem explicações básicas para suas decisões em formato legível por humanos.                                                        |   1   |  D/V  |
| 13.4.2 | Verifique se a qualidade da explicação é validada por meio de estudos de avaliação humana e de métricas.                                                              |   2   |   V   |
| 13.4.3 | Verifique se as pontuações de importância de características ou métodos de atribuição (SHAP, LIME, etc.) estão disponíveis para decisões críticas.                    |   3   |  D/V  |
| 13.4.4 | Verifique se as explicações contrafactuais mostram como as entradas poderiam ser modificadas para alterar os desfechos, se for aplicável ao caso de uso e ao domínio. |   3   |   V   |

---

## C13.5 Cartões de Modelo e Divulgações de Uso

Manter fichas de modelo para uso pretendido, métricas de desempenho e considerações éticas.

|   #    | Descrição                                                                                                                                                                                                                     | Nível | Papel |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 13.5.1 | Verifique se os cartões de modelo documentam os casos de uso pretendidos, limitações e modos de falha conhecidos.                                                                                                             |   1   |   D   |
| 13.5.2 | Verifique se as métricas de desempenho para diferentes casos de uso aplicáveis são divulgadas.                                                                                                                                |   1   |  D/V  |
| 13.5.3 | Verifique que as considerações éticas, avaliações de viés, avaliações de equidade, características dos dados de treinamento e limitações conhecidas dos dados de treinamento estejam documentadas e atualizadas regularmente. |   2   |   D   |
| 13.5.4 | Verifique se os cartões de modelo possuem controle de versão e são mantidos ao longo do ciclo de vida do modelo com rastreamento de alterações.                                                                               |   2   |  D/V  |

---

## C13.6 Quantificação da Incerteza

Propagar pontuações de confiança ou medidas de entropia nas respostas.

|   #    | Descrição                                                                                                              | Nível | Papel |
| :----: | ---------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 13.6.1 | Verifique se os sistemas de IA fornecem pontuações de confiança ou medidas de incerteza juntamente com as suas saídas. |   1   |   D   |
| 13.6.2 | Verifique se os limiares de incerteza acionam revisão humana adicional ou caminhos de decisão alternativos.            |   2   |  D/V  |
| 13.6.3 | Verifique se os métodos de quantificação de incerteza estão calibrados e validados com os dados de referência.         |   2   |   V   |
| 13.6.4 | Verifique se a propagação da incerteza é mantida ao longo de fluxos de trabalho de IA de várias etapas.                |   3   |  D/V  |

---

## C13.7 Relatórios de Transparência Voltados ao Usuário

Fornecer divulgações periódicas sobre incidentes, deriva de dados e uso de dados.

|   #    | Descrição                                                                                                                                            | Nível | Papel |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 13.7.1 | Verifique se as políticas de uso de dados e as práticas de gestão do consentimento do usuário são comunicadas de forma clara às partes interessadas. |   1   |  D/V  |
| 13.7.2 | Verifique se as avaliações de impacto de IA são realizadas e se os resultados estão incluídos nos relatórios.                                        |   2   |  D/V  |
| 13.7.3 | Verifique se os relatórios de transparência, publicados regularmente, divulgam incidentes de IA e métricas operacionais com detalhes razoáveis.      |   2   |  D/V  |

### Referências

* [EU Artificial Intelligence Act — Regulation (EU) 2024/1689 (Official Journal, 12 July 2024)](https://eur-lex.europa.eu/eli/reg/2024/1689/oj)
* [ISO/IEC 23894:2023 — Artificial Intelligence — Guidance on Risk Management](https://www.iso.org/standard/77304.html)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements](https://www.iso.org/standard/81230.html)
* [NIST AI Risk Management Framework 1.0](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [NIST SP 800-53 Revision 5 — Security and Privacy Controls](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-53r5.pdf)
* [A Unified Approach to Interpreting Model Predictions (SHAP, ICML 2017)](https://arxiv.org/abs/1705.07874)
* [Model Cards for Model Reporting (Mitchell et al., 2018)](https://arxiv.org/abs/1810.03993)
* [Dropout as a Bayesian Approximation: Representing Model Uncertainty in Deep Learning (Gal & Ghahramani, 2016)](https://arxiv.org/abs/1506.02142)
* [ISO/IEC 24029-2:2023 — Robustness of Neural Networks — Methodology for Formal Methods](https://www.iso.org/standard/79804.html)
* [IEEE 7001-2021 — Transparency of Autonomous Systems](https://standards.ieee.org/ieee/7001/6929/)
* [GDPR — Article 5 "Transparency Principle" (Regulation (EU) 2016/679)](https://eur-lex.europa.eu/legal-content/EN/TXT/PDF/?uri=CELEX%3A32016R0679)
* [Human Oversight under Article 14 of the EU AI Act (Fink, 2025)](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=5147196)

