# C13 Supervisão Humana, Responsabilidade e Governança

## Objetivo de Controle

Este capítulo fornece requisitos para manter a supervisão humana e cadeias claras de responsabilidade em sistemas de IA, garantindo explicabilidade, transparência e gestão ética ao longo do ciclo de vida da IA.

---

## C13.1 Mecanismos de Interruptor de Emergência e Substituição

Forneça caminhos de desligamento ou reversão quando for observado comportamento inseguro do sistema de IA.

|   #    | Descrição                                                                                                                 | Nível | Função |
| :----: | ------------------------------------------------------------------------------------------------------------------------- | :---: | :----: |
| 13.1.1 | Verifique se existe um mecanismo manual de interrupção para parar imediatamente a inferência e as saídas do modelo de IA. |   1   |  D/V   |
| 13.1.2 | Verifique se os controles de substituição são acessíveis apenas ao pessoal autorizado.                                    |   1   |   D    |
| 13.1.3 | Verifique se os procedimentos de reversão podem reverter para versões anteriores do modelo ou operações em modo seguro.   |   3   |  D/V   |
| 13.1.4 | Verifique se os mecanismos de substituição são testados regularmente.                                                     |   3   |   V    |

---

## C13.2 Pontos de Verificação de Decisão com Intervenção Humana

Exigir aprovações humanas quando os riscos ultrapassam os limites predefinidos.

|   #    | Descrição                                                                                                                                                 | Nível | Função |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :----: |
| 13.2.1 | Verifique se decisões de IA de alto risco exigem aprovação humana explícita antes da execução.                                                            |   1   |  D/V   |
| 13.2.2 | Verifique se os limites de risco estão claramente definidos e acionam automaticamente os fluxos de trabalho de revisão humana.                            |   1   |   D    |
| 13.2.3 | Verifique se as decisões sensíveis ao tempo possuem procedimentos alternativos quando a aprovação humana não pode ser obtida dentro dos prazos exigidos.  |   2   |   D    |
| 13.2.4 | Verifique se os procedimentos de escalonamento definem níveis claros de autoridade para diferentes tipos de decisão ou categorias de risco, se aplicável. |   3   |  D/V   |

---

## C13.3 Cadeia de Responsabilidade e Auditabilidade

Registrar as ações do operador e as decisões do modelo.

|   #    | Descrição                                                                                                                                                                   | Nível | Função |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :----: |
| 13.3.1 | Verifique se todas as decisões do sistema de IA e intervenções humanas são registradas com carimbos de data e hora, identidades dos usuários e justificativas das decisões. |   1   |  D/V   |
| 13.3.2 | Verifique se os logs de auditoria não podem ser adulterados e incluem mecanismos de verificação de integridade.                                                             |   2   |   D    |

---

## C13.4 Técnicas de IA Explicável

Importância das características superficiais, contra-factuais e explicações locais.

|   #    | Descrição                                                                                                                                                     | Nível | Função |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :----: |
| 13.4.1 | Verifique se os sistemas de IA fornecem explicações básicas para suas decisões em formato compreensível para humanos.                                         |   1   |  D/V   |
| 13.4.2 | Verifique se a qualidade da explicação é validada por meio de estudos e métricas de avaliação humana.                                                         |   2   |   V    |
| 13.4.3 | Verifique se as pontuações de importância de características ou métodos de atribuição (SHAP, LIME, etc.) estão disponíveis para decisões críticas.            |   3   |  D/V   |
| 13.4.4 | Verifique se as explicações contrafactuais mostram como os inputs podem ser modificados para alterar os resultados, se aplicável ao caso de uso e ao domínio. |   3   |   V    |

---

## C13.5 Cartões de Modelo e Divulgações de Uso

Manter cartões de modelo para uso pretendido, métricas de desempenho e considerações éticas.

|   #    | Descrição                                                                                                                                                                                                                 | Nível | Função |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :----: |
| 13.5.1 | Verifique se os cartões de modelo documentam os casos de uso pretendidos, limitações e modos de falha conhecidos.                                                                                                         |   1   |   D    |
| 13.5.2 | Verifique se as métricas de desempenho em diferentes casos de uso aplicáveis estão divulgadas.                                                                                                                            |   1   |  D/V   |
| 13.5.3 | Verifique se as considerações éticas, avaliações de viés, avaliações de justiça, características dos dados de treinamento e limitações conhecidas dos dados de treinamento estão documentadas e atualizadas regularmente. |   2   |   D    |
| 13.5.4 | Verifique se os cartões do modelo estão sob controle de versão e são mantidos durante todo o ciclo de vida do modelo com rastreamento de alterações.                                                                      |   2   |  D/V   |

---

## C13.6 Quantificação da Incerteza

Propagar pontuações de confiança ou medidas de entropia nas respostas.

|   #    | Descrição                                                                                                      | Nível | Função |
| :----: | -------------------------------------------------------------------------------------------------------------- | :---: | :----: |
| 13.6.1 | Verifique se os sistemas de IA fornecem pontuações de confiança ou medidas de incerteza com seus resultados.   |   1   |   D    |
| 13.6.2 | Verifique se os limites de incerteza acionam uma revisão humana adicional ou caminhos alternativos de decisão. |   2   |  D/V   |
| 13.6.3 | Verifique se os métodos de quantificação de incerteza estão calibrados e validados com dados de referência.    |   2   |   V    |
| 13.6.4 | Verifique se a propagação da incerteza é mantida ao longo de fluxos de trabalho de IA em múltiplas etapas.     |   3   |  D/V   |

---

## C13.7 Relatórios de Transparência para o Usuário Final

Fornecer divulgações periódicas sobre incidentes, deriva e uso de dados.

|   #    | Descrição                                                                                                                                        | Nível | Função |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :----: |
| 13.7.1 | Verifique se as políticas de uso de dados e as práticas de gestão do consentimento do usuário são claramente comunicadas às partes interessadas. |   1   |  D/V   |
| 13.7.2 | Verifique se as avaliações de impacto da IA são realizadas e se os resultados estão incluídos nos relatórios.                                    |   2   |  D/V   |
| 13.7.3 | Verifique se os relatórios de transparência publicados regularmente divulgam incidentes de IA e métricas operacionais com detalhes razoáveis.    |   2   |  D/V   |

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

