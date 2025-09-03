# Monitoramento, registro e detecção de anomalias C12

## Objetivo de Controle

Esta seção fornece requisitos para oferecer visibilidade em tempo real e forense do que o modelo e outros componentes de IA veem, fazem e retornam, para que ameaças possam ser detectadas, triadas e aprendidas.

## C12.1 Registro de Solicitações e Respostas

|   #    | Descrição                                                                                                                                                                                                                | Nível | Papel |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 12.1.1 | Verifique se todos os prompts do usuário e respostas do modelo estão sendo registrados com metadados apropriados (por exemplo, timestamp, ID do usuário, ID da sessão, versão do modelo).                                |   1   |  D/V  |
| 12.1.2 | Verifique se os logs estão armazenados em repositórios seguros, controlados por acesso, com políticas de retenção apropriadas e procedimentos de backup.                                                                 |   1   |  D/V  |
| 12.1.3 | Verifique se os sistemas de armazenamento de logs implementam criptografia em repouso e em trânsito para proteger informações confidenciais contidas nos logs.                                                           |   1   |  D/V  |
| 12.1.4 | Verifique se os dados confidenciais em prompts e saídas são automaticamente redigidos ou mascarados antes de serem registrados, com regras de redaction configuráveis para PII, credenciais e informações proprietárias. |   1   |  D/V  |
| 12.1.5 | Verifique se as decisões de política e as ações de filtragem de segurança estão registradas com detalhes suficientes para permitir auditoria e depuração dos sistemas de moderação de conteúdo.                          |   2   |  D/V  |
| 12.1.6 | Verifique se a integridade do log está protegida através de, por exemplo, assinaturas criptográficas ou armazenamento somente de escrita.                                                                                |   2   |  D/V  |

---

## C12.2 Detecção de Abuso e Alertas

|   #    | Descrição                                                                                                                                                                                                           | Nível | Papel |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.2.1 | Verifique se o sistema detecta e alerta sobre padrões de jailbreak conhecidos, tentativas de injeção de prompt e entradas adversariais usando detecção baseada em assinatura.                                       |   1   |  D/V  |
| 12.2.2 | Verifique se o sistema se integra com plataformas de Gerenciamento de Informações e Eventos de Segurança (SIEM) existentes usando formatos de log e protocolos padrão.                                              |   1   |  D/V  |
| 12.2.3 | Verifique se os eventos de segurança enriquecidos incluem contexto específico de IA, como identificadores de modelo, pontuações de confiança e decisões do filtro de segurança.                                     |   2   |  D/V  |
| 12.2.4 | Verifique se a detecção de anomalias comportamentais identifica padrões de conversa incomuns, tentativas excessivas de repetição ou comportamentos sistemáticos de sondagem.                                        |   2   |  D/V  |
| 12.2.5 | Verifique se os mecanismos de alerta em tempo real notificam as equipes de segurança quando possíveis violações de política ou tentativas de ataque são detectadas.                                                 |   2   |  D/V  |
| 12.2.6 | Verifique se regras customizadas estão incluídas para detectar padrões de ameaça específicos de IA, incluindo tentativas coordenadas de jailbreak, campanhas de injeção de prompt e ataques de extração de modelos. |   2   |  D/V  |
| 12.2.7 | Verifique se os fluxos de trabalho automatizados de resposta a incidentes podem isolar modelos comprometidos, bloquear usuários maliciosos e escalar eventos de segurança críticos.                                 |   3   |  D/V  |

---

## C12.3 Detecção de Deslocamento de Modelo

|   #    | Descrição                                                                                                                                                                              | Nível | Papel |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.3.1 | Verifique se o sistema acompanha métricas básicas de desempenho, como precisão, pontuações de confiança, latência e taxas de erro ao longo de versões do modelo e períodos de tempo.   |   1   |  D/V  |
| 12.3.2 | Verifique se os alertas automatizados são acionados quando os métricas de desempenho excedem os limites de degradação predefinidos ou divergem significativamente das linhas de base.  |   2   |  D/V  |
| 12.3.3 | Verifique se os monitores de detecção de alucinação identificam e sinalizam casos em que as saídas do modelo contêm informações factualmente incorretas, inconsistentes ou fabricadas. |   2   |  D/V  |

---

## C12.4 Telemetria de Desempenho & Comportamento

|   #    | Descrição                                                                                                                                                                      | Nível | Papel |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 12.4.1 | Verifique se as métricas operacionais, incluindo latência de requisição, consumo de tokens, uso de memória e throughput, estão sendo coletadas e monitoradas continuamente.    |   1   |  D/V  |
| 12.4.2 | Verifique se as taxas de sucesso e falha são acompanhadas com categorização dos tipos de erro e suas causas raízes.                                                            |   1   |  D/V  |
| 12.4.3 | Verifique se o monitoramento de utilização de recursos inclui o uso de GPU/CPU, consumo de memória e requisitos de armazenamento, com alertas em caso de violações de limites. |   2   |  D/V  |

---

## C12.5 Planejamento e Execução de Resposta a Incidentes de IA

|   #    | Descrição                                                                                                                                                                                           | Nível | Papel |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.5.1 | Verifique se os planos de resposta a incidentes abordam especificamente eventos de segurança relacionados à IA, incluindo comprometimento de modelo, envenenamento de dados e ataques adversariais. |   1   |  D/V  |
| 12.5.2 | Verifique se as equipes de resposta a incidentes têm acesso a ferramentas forenses específicas de IA e expertise para investigar o comportamento do modelo e vetores de ataque.                     |   2   |  D/V  |
| 12.5.3 | Verifique se a análise pós-incidente inclui considerações para retreinamento do modelo, atualizações de filtros de segurança e integração de lições aprendidas nos controles de segurança.          |   3   |  D/V  |

---

## C12.5 Detecção de Degradação de Desempenho de IA

Monitorar e detectar degradação no desempenho e na qualidade do modelo de IA ao longo do tempo.

|   #    | Descrição                                                                                                                                                        | Nível | Papel |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.5.1 | Verifique se a precisão do modelo, precisão, recall e pontuações F1 estão continuamente monitoradas e comparadas com os limites de referência.                   |   1   |  D/V  |
| 12.5.2 | Verifique se a detecção de deriva de dados monitora mudanças na distribuição de entrada que podem impactar o desempenho do modelo.                               |   1   |  D/V  |
| 12.5.3 | Verifique se a detecção de desvio de conceito identifica mudanças na relação entre as entradas e as saídas esperadas.                                            |   2   |  D/V  |
| 12.5.4 | Verifique se a degradação de desempenho dispara alertas automatizados e inicia fluxos de trabalho de retreinamento ou substituição de modelos.                   |   2   |  D/V  |
| 12.5.5 | Verifique se a análise da causa raiz da degradação correlaciona as quedas de desempenho com mudanças nos dados, problemas de infraestrutura ou fatores externos. |   3   |   V   |

---

## C12.6 Visualização de DAG e Segurança do Fluxo de Trabalho

Proteja os sistemas de visualização de fluxo de trabalho contra vazamento de informações e ataques de manipulação.

|   #    | Descrição                                                                                                                                                                                       | Nível | Papel |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.6.1 | Verifique se os dados de visualização DAG são sanitizados para remover informações confidenciais antes do armazenamento ou transmissão.                                                         |   1   |  D/V  |
| 12.6.2 | Verifique se os controles de acesso à visualização do fluxo de trabalho garantem que apenas usuários autorizados possam visualizar os caminhos de decisão do agente e os rastros de raciocínio. |   1   |  D/V  |
| 12.6.3 | Verifique se a integridade dos dados DAG está protegida por assinaturas criptográficas e mecanismos de armazenamento à prova de adulteração.                                                    |   2   |  D/V  |
| 12.6.4 | Verifique se os sistemas de visualização de fluxo de trabalho implementam validação de entrada para evitar ataques de injeção através de dados manipulados de nó ou aresta.                     |   2   |  D/V  |
| 12.6.5 | Verifique se as atualizações em tempo real do DAG estão limitadas em taxa e validadas para impedir ataques de negação de serviço em sistemas de visualização.                                   |   3   |  D/V  |

---

## C12.7 Monitoramento Proativo de Comportamento de Segurança

Detecção e prevenção de ameaças de segurança por meio da análise proativa do comportamento do agente.

|   #    | Descrição                                                                                                                                       | Nível | Papel |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.7.1 | Verifique se os comportamentos proativos de agentes são validados pela segurança antes da execução, com integração à avaliação de riscos.       |   1   |  D/V  |
| 12.7.2 | Verifique se os gatilhos de iniciativa autônoma incluem avaliação do contexto de segurança e análise do panorama de ameaças.                    |   2   |  D/V  |
| 12.7.3 | Verifique se os padrões de comportamento proativo são analisados quanto às possíveis implicações de segurança e consequências não intencionais. |   2   |  D/V  |
| 12.7.4 | Verifique se as ações proativas críticas à segurança exigem cadeias de aprovação explícitas com trilhas de auditoria.                           |   3   |  D/V  |
| 12.7.5 | Verifique se a detecção de anomalias comportamentais identifica desvios nos padrões de agentes proativos que possam indicar comprometimento.    |   3   |  D/V  |

---

## Referências

* [NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6](https://www.iso.org/standard/81230.html)
* [EU AI Act — Article 12, 13, 16 and 19 on Logging and Record-keeping](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A32024R1689)

