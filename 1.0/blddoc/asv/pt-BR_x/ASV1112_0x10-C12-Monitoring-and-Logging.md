# C12 Monitoramento, Registro e Detecção de Anomalias

## Objetivo de Controle

Esta seção fornece requisitos para oferecer visibilidade em tempo real e forense sobre o que o modelo e outros componentes de IA veem, fazem e retornam, para que as ameaças possam ser detectadas, triadas e aprendidas a partir disso.

## C12.1 Registro de Solicitação e Resposta

|   #    | Descrição                                                                                                                                                                                                                                                              | Nível | Papel |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.1.1 | Verifique se todas as solicitações do usuário e as respostas do modelo são registradas com metadados adequados (por exemplo, carimbo de data/hora, ID do usuário, ID da sessão, versão do modelo).                                                                     |   1   |  D/V  |
| 12.1.2 | Verifique se os logs são armazenados em repositórios seguros com controle de acesso, políticas de retenção apropriadas e procedimentos de backup.                                                                                                                      |   1   |  D/V  |
| 12.1.3 | Verifique se os sistemas de armazenamento de logs implementam criptografia em repouso e em trânsito para proteger informações sensíveis contidas nos logs.                                                                                                             |   1   |  D/V  |
| 12.1.4 | Verifique se dados sensíveis em prompts e saídas são automaticamente anonimizados ou mascarados antes de serem registrados nos logs, com regras de anonimização configuráveis para PII (informação de identificação pessoal), credenciais e informações proprietárias. |   1   |  D/V  |
| 12.1.5 | Verifique se as decisões de políticas e as ações de filtragem de segurança são registradas com detalhes suficientes para permitir auditoria e depuração dos sistemas de moderação de conteúdo.                                                                         |   2   |  D/V  |
| 12.1.6 | Verifique se a integridade do log está protegida, por exemplo, por assinaturas criptográficas ou armazenamento apenas de escrita.                                                                                                                                      |   2   |  D/V  |

---

## C12.2 Detecção de Abuso e Alerta

|   #    | Descrição                                                                                                                                                                                                             | Nível | Papel |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.2.1 | Verifique se o sistema detecta e gera alertas sobre padrões conhecidos de jailbreak, tentativas de injeção de prompt e entradas adversárias, usando detecção baseada em assinaturas.                                  |   1   |  D/V  |
| 12.2.2 | Verifique se o sistema se integra com plataformas de Security Information and Event Management (SIEM) existentes, usando formatos de log padrão e protocolos padrão.                                                  |   1   |  D/V  |
| 12.2.3 | Verifique se os eventos de segurança enriquecidos contêm contexto específico de IA, como identificadores de modelo, pontuações de confiança e decisões do filtro de segurança.                                        |   2   |  D/V  |
| 12.2.4 | Verifique se a detecção de anomalias comportamentais identifica padrões de conversação incomuns, tentativas repetidas excessivas ou comportamentos de sondagem sistemáticos.                                          |   2   |  D/V  |
| 12.2.5 | Verifique se os mecanismos de alerta em tempo real notificam as equipes de segurança quando são detectadas violações potenciais de políticas ou tentativas de ataque.                                                 |   2   |  D/V  |
| 12.2.6 | Verifique se regras personalizadas estão incluídas para detectar padrões de ameaça específicos de IA, incluindo tentativas coordenadas de jailbreak, campanhas de injeção de prompt e ataques de extração de modelos. |   2   |  D/V  |
| 12.2.7 | Verifique se os fluxos de resposta a incidentes automatizados podem isolar modelos comprometidos, bloquear usuários mal-intencionados e escalar eventos de segurança críticos.                                        |   3   |  D/V  |

---

## C12.3 Detecção de Deriva do Modelo

|   #    | Descrição                                                                                                                                                                                     | Nível | Papel |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.3.1 | Verifique se o sistema acompanha métricas básicas de desempenho, como acurácia, pontuações de confiança, latência e taxas de erro ao longo de versões do modelo e períodos de tempo.          |   1   |  D/V  |
| 12.3.2 | Verifique se o acionamento de alertas automatizados ocorre quando as métricas de desempenho excedem limiares de degradação predefinidos ou se desviam significativamente das linhas de base.  |   2   |  D/V  |
| 12.3.3 | Verifique se os monitores de detecção de alucinações identificam e sinalizam ocorrências em que as saídas do modelo contêm informações factualmente incorretas, inconsistentes ou fabricadas. |   2   |  D/V  |

---

## C12.4 Telemetria de Desempenho e Comportamento

|   #    | Descrição                                                                                                                                                                              | Nível | Papel |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.4.1 | Verifique se as métricas operacionais, incluindo a latência de requisição, o consumo de tokens, o uso de memória e a taxa de transferência, são coletadas e monitoradas continuamente. |   1   |  D/V  |
| 12.4.2 | Verifique se as taxas de sucesso e de falha são monitoradas com a categorização dos tipos de erro e de suas causas raízes.                                                             |   1   |  D/V  |
| 12.4.3 | Verifique se o monitoramento da utilização de recursos inclui o uso de GPU/CPU, o consumo de memória e os requisitos de armazenamento, com alertas em caso de violação dos limites.    |   2   |  D/V  |

---

## C12.5 IA Planejamento e Execução de Resposta a Incidentes

|   #    | Descrição                                                                                                                                                                                                | Nível | Papel |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.5.1 | Verifique se os planos de resposta a incidentes abordam especificamente eventos de segurança relacionados à IA, incluindo comprometimento do modelo, envenenamento de dados e ataques adversariais.      |   1   |  D/V  |
| 12.5.2 | Verifique se as equipes de resposta a incidentes têm acesso a ferramentas forenses específicas de IA e perícia especializada em IA para investigar o comportamento do modelo e os vetores de ataque.     |   2   |  D/V  |
| 12.5.3 | Certifique-se de que a análise pós-incidente inclua considerações sobre o re-treinamento do modelo, atualizações dos filtros de segurança e integração das lições aprendidas aos controles de segurança. |   3   |  D/V  |

---

## C12.5 Detecção de Degradação de Desempenho de IA

Monitorar e detectar a degradação do desempenho e da qualidade do modelo de IA ao longo do tempo.

|   #    | Descrição                                                                                                                                                       | Nível | Papel |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.5.1 | Verifique se as métricas de acurácia do modelo, precisão, revocação e pontuações F1 são monitoradas continuamente e comparadas com limiares de referência.      |   1   |  D/V  |
| 12.5.2 | Verifique se a detecção de deriva de dados monitora alterações na distribuição de entrada que possam impactar o desempenho do modelo.                           |   1   |  D/V  |
| 12.5.3 | Verifique se a detecção de drift de conceito identifica mudanças na relação entre as entradas e as saídas esperadas.                                            |   2   |  D/V  |
| 12.5.4 | Verifique se a degradação de desempenho aciona alertas automatizados e inicia fluxos de re-treinamento ou substituição do modelo.                               |   2   |  D/V  |
| 12.5.5 | Verifique se a análise da causa raiz da degradação correlaciona quedas de desempenho com alterações nos dados, problemas de infraestrutura ou fatores externos. |   3   |   V   |

---

## C12.6 Visualização de Grafos Dirigidos Acíclicos (DAG) e Segurança de Fluxos de Trabalho

Proteger os sistemas de visualização de fluxos de trabalho contra vazamento de informações e ataques de manipulação.

|   #    | Descrição                                                                                                                                                                                      | Nível | Papel |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.6.1 | Verifique se os dados de visualização do DAG (grafo acíclico dirigido) foram sanitizados para remover informações sensíveis antes do armazenamento ou da transmissão.                          |   1   |  D/V  |
| 12.6.2 | Verifique se os controles de acesso à visualização do fluxo de trabalho garantem que apenas usuários autorizados possam visualizar os caminhos de decisão do agente e os traços de raciocínio. |   1   |  D/V  |
| 12.6.3 | Verifique se a integridade dos dados do DAG está protegida por assinaturas criptográficas e por mecanismos de armazenamento à prova de adulteração.                                            |   2   |  D/V  |
| 12.6.4 | Verifique se os sistemas de visualização de fluxos de trabalho implementam validação de entrada para prevenir ataques de injeção por meio de dados de nó ou de aresta criados.                 |   2   |  D/V  |
| 12.6.5 | Verifique se as atualizações em tempo real de DAGs são limitadas em taxa e validadas para evitar ataques de negação de serviço em sistemas de visualização.                                    |   3   |  D/V  |

---

## C12.7 Monitoramento Proativo do Comportamento de Segurança

Detecção e prevenção de ameaças à segurança por meio da análise proativa do comportamento de agentes.

|   #    | Descrição                                                                                                                                                     | Nível | Papel |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.7.1 | Verifique se os comportamentos proativos dos agentes são validados quanto à segurança antes da execução, com integração de avaliação de risco.                |   1   |  D/V  |
| 12.7.2 | Verifique se os gatilhos de iniciativas autônomas incluem avaliação do contexto de segurança e avaliação do panorama de ameaças.                              |   2   |  D/V  |
| 12.7.3 | Verifique se os padrões de comportamento proativo são analisados para potenciais implicações de segurança e consequências não intencionais.                   |   2   |  D/V  |
| 12.7.4 | Verifique se as ações proativas críticas de segurança exigem cadeias de aprovação explícitas com trilhas de auditoria.                                        |   3   |  D/V  |
| 12.7.5 | Verifique se a detecção de anomalias comportamentais identifica desvios nos padrões de comportamento de agentes proativos que possam indicar comprometimento. |   3   |  D/V  |

---

## Referências

* [NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6](https://www.iso.org/standard/81230.html)
* [EU AI Act — Article 12, 13, 16 and 19 on Logging and Record-keeping](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A32024R1689)

