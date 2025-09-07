# Gerenciamento do Ciclo de Vida do Modelo C3 e Controle de Mudanças

## Objetivo de Controle

Os sistemas de IA devem implementar processos de controle de mudanças que impeçam modificações não autorizadas ou inseguras do modelo de chegar à produção. Esse controle garante a integridade do modelo durante todo o ciclo de vida—desde o desenvolvimento, passando pela implantação, até o descomissionamento—o que possibilita uma resposta rápida a incidentes e mantém a responsabilidade por todas as alterações.

Objetivo Principal de Segurança: Somente modelos autorizados e validados chegam à produção por meio da aplicação de processos controlados que mantêm integridade, rastreabilidade e recuperabilidade.

---

## C3.1 Autorização e Integridade do Modelo

Apenas modelos autorizados com integridade verificada chegam aos ambientes de produção.

|   #   | Descrição                                                                                                                                                                                                                                                     | Nível | Função |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :----: |
| 3.1.1 | Verifique se todos os artefatos do modelo (pesos, configurações, tokenizadores) estão assinados criptograficamente por entidades autorizadas antes da implantação.                                                                                            |   1   |  D/V   |
| 3.1.2 | Verifique se a integridade do modelo é validada no momento da implantação e se falhas na verificação de assinatura impedem o carregamento do modelo.                                                                                                          |   1   |  D/V   |
| 3.1.3 | Verifique se os registros de proveniência do modelo incluem a identidade da entidade autorizadora, somas de verificação dos dados de treinamento, resultados dos testes de validação com status de aprovação/reprovação e um carimbo de data/hora de criação. |   2   |  D/V   |
| 3.1.4 | Verifique se todos os artefatos do modelo usam versionamento semântico (MAJOR.MINOR.PATCH) com critérios documentados especificando quando cada componente da versão deve ser incrementado.                                                                   |   2   |  D/V   |
| 3.1.5 | Verifique se o rastreamento de dependências mantém um inventário em tempo real que possibilite a identificação rápida de todos os sistemas consumidores.                                                                                                      |   2   |   V    |

---

## C3.2 Validação e Teste de Modelos

Os modelos devem passar pelas validações definidas de segurança e proteção antes da implantação.

|   #   | Descrição                                                                                                                                                                                                                                     | Nível | Função |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :----: |
| 3.2.1 | Verifique se os modelos passam por testes automatizados de segurança que incluem validação de entrada, sanitização de saída e avaliações de segurança com limites de aprovação/reprovação organizacionais pré-acordados antes da implantação. |   1   |  D/V   |
| 3.2.2 | Verifique se as falhas de validação bloqueiam automaticamente a implantação do modelo após aprovação explícita de substituição por parte de pessoal autorizado pré-designado, com justificativas comerciais documentadas.                     |   1   |  D/V   |
| 3.2.3 | Verifique se os resultados do teste estão assinados criptograficamente e vinculados de forma imutável ao hash da versão específica do modelo que está sendo validada.                                                                         |   2   |   V    |
| 3.2.4 | Verifique se as implantações de emergência exigem avaliação de risco de segurança documentada e aprovação de uma autoridade de segurança pré-designada dentro dos prazos previamente acordados.                                               |   2   |  D/V   |

---

## C3.3 Implantação Controlada e Reversão

As implantações de modelos devem ser controladas, monitoradas e reversíveis.

|   #   | Descrição                                                                                                                                                                                                                                                                       | Nível | Função |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :----: |
| 3.3.1 | Verifique se as implantações em produção implementam mecanismos de lançamento gradual (implantações canário, implantações blue-green) com acionadores automáticos de rollback baseados em taxas de erro pré-acordadas, limites de latência ou critérios de alerta de segurança. |   1   |   D    |
| 3.3.2 | Verifique se as capacidades de rollback restauram o estado completo do modelo (pesos, configurações, dependências) de forma atômica dentro de janelas de tempo organizacionais predefinidas.                                                                                    |   1   |  D/V   |
| 3.3.3 | Verifique se os processos de implantação validam assinaturas criptográficas e calculam checksums de integridade antes da ativação do modelo, falhando a implantação em qualquer incompatibilidade.                                                                              |   2   |  D/V   |
| 3.3.4 | Verifique se as capacidades de desligamento de emergência do modelo podem desativar os endpoints do modelo dentro dos tempos de resposta pré-definidos por meio de disjuntores automáticos ou interruptores manuais de desligamento.                                            |   2   |  D/V   |
| 3.3.5 | Verifique se os artefatos de reversão (versões anteriores do modelo, configurações, dependências) são mantidos conforme as políticas organizacionais, utilizando armazenamento imutável para resposta a incidentes.                                                             |   2   |   V    |

---

## C3.4 Responsabilidade por Alterações e Auditoria

Todas as alterações no ciclo de vida do modelo devem ser rastreáveis e auditáveis.

|   #   | Descrição                                                                                                                                                                                                                                                      | Nível | Função |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :----: |
| 3.4.1 | Verifique se todas as alterações no modelo (implantação, configuração, desativação) geram registros de auditoria imutáveis, incluindo um carimbo de data/hora, a identidade autenticada do ator, um tipo de alteração e os estados anterior/depois.            |   1   |   V    |
| 3.4.2 | Verifique se o acesso ao log de auditoria requer autorização apropriada e se todas as tentativas de acesso são registradas com a identidade do usuário e um carimbo de data/hora.                                                                              |   2   |  D/V   |
| 3.4.3 | Verifique se os templates de prompt e as mensagens do sistema estão versionados em repositórios git com revisão de código obrigatória e aprovação de revisores designados antes da implantação.                                                                |   2   |  D/V   |
| 3.4.4 | Verifique se os registros de auditoria incluem detalhes suficientes (hashes do modelo, instantâneos de configuração, versões de dependências) para permitir a reconstrução completa do estado do modelo para qualquer timestamp dentro do período de retenção. |   2   |   V    |

---

## C3.5 Práticas de Desenvolvimento Seguro

Os processos de desenvolvimento e treinamento do modelo devem seguir práticas seguras para evitar comprometimentos.

|   #   | Descrição                                                                                                                                                                                                                                        | Nível | Função |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :----: |
| 3.5.1 | Verifique se os ambientes de desenvolvimento, teste e produção do modelo estão separados fisicamente ou logicamente. Eles não devem compartilhar infraestrutura, devem ter controles de acesso distintos e armazenamentos de dados isolados.     |   1   |   D    |
| 3.5.2 | Verifique se o treinamento e o ajuste fino do modelo ocorrem em ambientes isolados com acesso de rede controlado.                                                                                                                                |   1   |   D    |
| 3.5.3 | Verifique se as fontes de dados de treinamento são validadas por meio de verificações de integridade e autenticadas por fontes confiáveis com cadeia de custódia documentada antes do uso no desenvolvimento do modelo.                          |   1   |  D/V   |
| 3.5.4 | Verifique se os artefatos de desenvolvimento do modelo (hiperparâmetros, scripts de treinamento, arquivos de configuração) estão armazenados no controle de versão e exigem aprovação por revisão de pares antes de serem usados no treinamento. |   2   |   D    |

---

## C3.6 Aposentadoria e Descomissionamento do Modelo

Os modelos devem ser desativados com segurança quando não forem mais necessários ou quando forem identificados problemas de segurança.

|   #   | Descrição                                                                                                                                                                                                                                                 | Nível | Função |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :----: |
| 3.6.1 | Verifique se os processos de aposentadoria de modelos escaneiam automaticamente os gráficos de dependência, identificam todos os sistemas consumidores e fornecem períodos de aviso prévio previamente acordados antes da desativação.                    |   1   |   D    |
| 3.6.2 | Verifique se os artefatos do modelo aposentado são apagados de forma segura usando apagamento criptográfico ou sobregravação múltipla conforme as políticas documentadas de retenção de dados, com certificados de destruição verificados.                |   1   |  D/V   |
| 3.6.3 | Verifique se os eventos de aposentadoria do modelo são registrados com carimbo de data e hora e identidade do ator, e se as assinaturas do modelo são revogadas para evitar reutilização.                                                                 |   2   |   V    |
| 3.6.4 | Verifique se a aposentadoria emergencial do modelo pode desabilitar o acesso ao modelo dentro dos prazos pré-estabelecidos de resposta a emergências por meio de desligamentos automáticos caso vulnerabilidades críticas de segurança sejam descobertas. |   2   |  D/V   |

---

## Referências

* [MLOps Principles](https://ml-ops.org/content/mlops-principles)
* [Securing AI/ML Ops – Cisco.com](https://sec.cloudapps.cisco.com/security/center/resources/SecuringAIMLOps)
* [Audit logs security: cryptographically signed tamper-proof logs](https://www.cossacklabs.com/blog/audit-logs-security/)
* [Machine Learning Model Versioning: Top Tools & Best Practices](https://lakefs.io/blog/model-versioning/)
* [AI Hygiene Starts with Models and Data Loaders – SEI Blog](https://insights.sei.cmu.edu/documents/6190/AI-Hygiene-Starts-with-Models-and-Data-Loaders_1G0KTRh.pdf)
* [How to handle versioning and rollback of a deployed ML model?](https://learn.microsoft.com/en-au/answers/questions/1845378/how-to-handle-versioning-and-rollback-of-a-deploye)
* [Reinforcement fine-tuning – OpenAI API](https://platform.openai.com/docs/guides/reinforcement-fine-tuning)
* [Auditing Machine Learning models: Governance, Data Security and …](https://www.linkedin.com/pulse/auditing-machine-learning-models-governance-data-security-negrete-yn81f)
* [Adversarial Training to Improve Model Robustness](https://medium.com/%40amit25173/adversarial-training-to-improve-model-robustness-5e285b516713)
* [What is AI adversarial robustness? – IBM Research](https://research.ibm.com/blog/securing-ai-workflows-with-adversarial-robustness)
* [Exploring Data Provenance: Ensuring Data Integrity and Authenticity](https://www.astera.com/type/blog/data-provenance/)
* [MITRE ATLAS](https://atlas.mitre.org/)
* [AWS Prescriptive Guidance – Best practices for retiring applications …](https://docs.aws.amazon.com/pdfs/prescriptive-guidance/latest/migration-app-retirement-best-practices/migration-app-retirement-best-practices.pdf)

