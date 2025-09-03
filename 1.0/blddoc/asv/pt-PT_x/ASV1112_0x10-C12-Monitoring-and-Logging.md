# C12 Monitoramento, Registro de Logs e Detecção de Anomalias

## Objetivo de Controle

Esta seção fornece os requisitos para oferecer visibilidade em tempo real e forense sobre o que o modelo e outros componentes de IA veem, fazem e retornam, para que as ameaças possam ser detectadas, triadas e utilizadas para aprendizado.

## C12.1 Registro de Requisição e Resposta

|   #    | Descrição                                                                                                                                                                                                                                                 | Nível | Papel |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.1.1 | Verifique se todas as entradas do usuário e as respostas do modelo são registradas com metadados apropriados (por exemplo, carimbo de data/hora, ID do usuário, ID de sessão, versão do modelo).                                                          |   1   |  D/V  |
| 12.1.2 | Verifique se os logs estão armazenados em repositórios seguros, com controle de acesso, políticas de retenção adequadas e procedimentos de backup.                                                                                                        |   1   |  D/V  |
| 12.1.3 | Verifique se os sistemas de armazenamento de logs implementam criptografia em repouso e em trânsito para proteger informações sensíveis contidas nos logs.                                                                                                |   1   |  D/V  |
| 12.1.4 | Verifique se dados sensíveis em prompts e saídas são automaticamente anonimizados ou mascarados antes de registrar nos logs, com regras de anonimização configuráveis para PII (dados de identificação pessoal), credenciais e informações proprietárias. |   1   |  D/V  |
| 12.1.5 | Verifique se as decisões de políticas e as ações de filtragem de segurança estão registradas com detalhes suficientes para permitir auditoria e depuração dos sistemas de moderação de conteúdo.                                                          |   2   |  D/V  |
| 12.1.6 | Verifique se a integridade do log está protegida por meio de, por exemplo, assinaturas criptográficas ou armazenamento de apenas gravação.                                                                                                                |   2   |  D/V  |

---

## C12.2 Detecção e Alerta de Abuso

|   #    | Descrição                                                                                                                                                                                                                 | Nível | Papel |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.2.1 | Verifique se o sistema detecta e emite alertas sobre padrões de jailbreak conhecidos, tentativas de injeção de prompt e entradas adversárias usando detecção baseada em assinaturas.                                      |   1   |  D/V  |
| 12.2.2 | Verifique se o sistema se integra às plataformas SIEM existentes usando formatos de log padrão e protocolos.                                                                                                              |   1   |  D/V  |
| 12.2.3 | Verifique se eventos de segurança enriquecidos incluem contexto específico de IA, como identificadores de modelo, pontuações de confiança e decisões do filtro de segurança.                                              |   2   |  D/V  |
| 12.2.4 | Verifique se a detecção de anomalias comportamentais identifica padrões de conversa incomuns, tentativas excessivas de reenvio ou comportamentos de sondagem sistemáticos.                                                |   2   |  D/V  |
| 12.2.5 | Verifique se os mecanismos de alerta em tempo real notificam as equipes de segurança quando são detectadas violações potenciais de políticas ou tentativas de ataque.                                                     |   2   |  D/V  |
| 12.2.6 | Verifique se as regras personalizadas estão incluídas para detectar padrões de ameaça específicos de IA, incluindo tentativas coordenadas de jailbreak, campanhas de injeção de prompts e ataques de extração de modelos. |   2   |  D/V  |
| 12.2.7 | Verifique se os fluxos de resposta a incidentes automatizados podem isolar modelos comprometidos, bloquear usuários mal-intencionados e escalar eventos de segurança críticos.                                            |   3   |  D/V  |

---

## C12.3 Detecção de deriva do modelo

|   #    | Descrição                                                                                                                                                                                   | Nível | Papel |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.3.1 | Verifique se o sistema rastreia métricas básicas de desempenho, como precisão, pontuações de confiança, latência e taxas de erro, ao longo de versões do modelo e de períodos de tempo.     |   1   |  D/V  |
| 12.3.2 | Verifique se os alertas automáticos são acionados quando as métricas de desempenho excedem limiares de degradação predefinidos ou se desviam significativamente das linhas de base.         |   2   |  D/V  |
| 12.3.3 | Verifique se os monitores de detecção de alucinações identificam e sinalizam situações em que as saídas do modelo contêm informações factualmente incorretas, inconsistentes ou fabricadas. |   2   |  D/V  |

---

## C12.4 Telemetria de Desempenho e Comportamento

|   #    | Descrição                                                                                                                                                                               | Nível | Papel |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.4.1 | Verifique se as métricas operacionais, incluindo a latência de requisições, o consumo de tokens, o uso de memória e a taxa de transferência, são coletadas e monitoradas continuamente. |   1   |  D/V  |
| 12.4.2 | Verifique se as taxas de sucesso e de falha são acompanhadas pela categorização dos tipos de erro e de suas causas raízes.                                                              |   1   |  D/V  |
| 12.4.3 | Verifique se o monitoramento de utilização de recursos inclui o uso de GPU/CPU, consumo de memória e requisitos de armazenamento, com alertas para violações de limites.                |   2   |  D/V  |

---

## C12.5 Planejamento e Execução da Resposta a Incidentes de IA

|   #    | Descrição                                                                                                                                                                                                   | Nível | Papel |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.5.1 | Verifique se os planos de resposta a incidentes abordam especificamente eventos de segurança relacionados à IA, incluindo o comprometimento do modelo, o envenenamento de dados e ataques adversariais.     |   1   |  D/V  |
| 12.5.2 | Verifique se as equipes de resposta a incidentes têm acesso a ferramentas forenses específicas de IA e conhecimentos especializados em IA para investigar o comportamento do modelo e os vetores de ataque. |   2   |  D/V  |
| 12.5.3 | Verifique se a análise pós-incidente inclui considerações sobre o re-treinamento do modelo, atualizações dos filtros de segurança e a integração das lições aprendidas aos controles de segurança.          |   3   |  D/V  |

---

## C12.5 Detecção de Degradação de Desempenho da IA

Monitorar e detectar a degradação do desempenho e da qualidade do modelo de IA ao longo do tempo.

|   #    | Descrição                                                                                                                                                         | Nível | Papel |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.5.1 | Verifique se a acurácia do modelo, a precisão, a sensibilidade e as pontuações F1 são monitoradas continuamente e comparadas com os limiares de referência.       |   1   |  D/V  |
| 12.5.2 | Verifique se a detecção de deriva de dados monitora alterações na distribuição de entrada que possam afetar o desempenho do modelo.                               |   1   |  D/V  |
| 12.5.3 | Verifique se a detecção de deriva de conceito identifica mudanças na relação entre as entradas e as saídas esperadas.                                             |   2   |  D/V  |
| 12.5.4 | Verifique se a degradação de desempenho aciona alertas automatizados e inicia fluxos de re-treinamento de modelos ou fluxos de substituição de modelos.           |   2   |  D/V  |
| 12.5.5 | Verifique se a análise de causa raiz da degradação correlaciona as quedas de desempenho com alterações de dados, problemas de infraestrutura ou fatores externos. |   3   |   V   |

---

## C12.6 Visualização de DAG e Segurança do Fluxo de Trabalho

Proteja os sistemas de visualização de fluxos de trabalho contra vazamento de informações e ataques de manipulação.

|   #    | Descrição                                                                                                                                                                                       | Nível | Papel |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.6.1 | Verifique se os dados de visualização do DAG são sanitizados para remover informações sensíveis antes do armazenamento ou da transmissão.                                                       |   1   |  D/V  |
| 12.6.2 | Verifique se os controles de acesso à visualização do fluxo de trabalho garantem que apenas usuários autorizados possam visualizar os caminhos de decisão do agente e as trilhas de raciocínio. |   1   |  D/V  |
| 12.6.3 | Verifique se a integridade dos dados de DAG está protegida por assinaturas criptográficas e mecanismos de armazenamento à prova de adulteração.                                                 |   2   |  D/V  |
| 12.6.4 | Verifique se os sistemas de visualização de fluxos de trabalho implementam validação de entrada para prevenir ataques de injeção por meio de dados de nó ou de aresta manipulados.              |   2   |  D/V  |
| 12.6.5 | Verifique se as atualizações em tempo real de DAGs estão sujeitas à limitação de taxa e são validadas para evitar ataques de negação de serviço em sistemas de visualização.                    |   3   |  D/V  |

---

## C12.7 Monitoramento Proativo do Comportamento de Segurança

Detecção e prevenção de ameaças à segurança por meio da análise proativa do comportamento de agentes.

|   #    | Descrição                                                                                                                                               | Nível | Papel |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.7.1 | Verifique se os comportamentos de agentes proativos são validados em termos de segurança antes da execução com integração de avaliação de risco.        |   1   |  D/V  |
| 12.7.2 | Verifique se os gatilhos de iniciativa autônoma incluem avaliação do contexto de segurança e avaliação do panorama de ameaças.                          |   2   |  D/V  |
| 12.7.3 | Verifique se os padrões de comportamento proativo são analisados para identificar implicações de segurança potenciais e consequências não intencionais. |   2   |  D/V  |
| 12.7.4 | Verifique se ações proativas de segurança críticas exigem cadeias de aprovação explícitas com trilhas de auditoria.                                     |   3   |  D/V  |
| 12.7.5 | Verifique se a detecção de anomalias comportamentais identifica desvios nos padrões de agentes proativos que possam indicar comprometimento.            |   3   |  D/V  |

---

## Referências

* [NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6](https://www.iso.org/standard/81230.html)
* [EU AI Act — Article 12, 13, 16 and 19 on Logging and Record-keeping](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A32024R1689)

