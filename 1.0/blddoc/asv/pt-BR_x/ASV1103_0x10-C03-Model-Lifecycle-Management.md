# Gestão do Ciclo de Vida do Modelo C3 & Controle de Mudanças

## Objetivo de Controle

Os sistemas de IA devem implementar processos de controle de alterações que impeçam modificações não autorizadas ou inseguras do modelo de alcançar a produção. Esse controle garante a integridade do modelo durante todo o ciclo de vida—desde o desenvolvimento até a implantação e desativação—o que possibilita uma resposta rápida a incidentes e mantém a responsabilidade por todas as mudanças.

Meta de Segurança Central: Apenas modelos autorizados e validados chegam à produção, empregando processos controlados que garantam integridade, rastreabilidade e recuperabilidade.

---

## C3.1 Autorização e Integridade do Modelo

Apenas modelos autorizados com integridade verificada chegam aos ambientes de produção.

|   #   | Descrição                                                                                                                                                                                                                                                      | Nível | Papel |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 3.1.1 | Verifique se todos os artefatos do modelo ( pesos, configurações, tokenizadores) estão assinados criptograficamente por entidades autorizadas antes da implantação.                                                                                            |   1   |  D/V  |
| 3.1.2 | Verifique se a integridade do modelo é validada no momento da implantação e se as falhas na verificação da assinatura impedem o carregamento do modelo.                                                                                                        |   1   |  D/V  |
| 3.1.3 | Verifique se os registros de proveniência do modelo incluem a identidade de uma entidade autorizadora, verificações de checksum dos dados de treinamento, resultados dos testes de validação com status de sucesso/falha e um carimbo de data/hora de criação. |   2   |  D/V  |
| 3.1.4 | Verifique se todos os artefatos do modelo usam versionamento semântico (MAJOR.MINOR.PATCH) com critérios documentados que especificam quando cada componente da versão deve ser incrementado.                                                                  |   2   |  D/V  |
| 3.1.5 | Verifique se o rastreamento de dependências mantém um inventário em tempo real que possibilita a identificação rápida de todos os sistemas consumidores.                                                                                                       |   2   |   V   |

---

## C3.2 Validação e Teste de Modelo

Os modelos devem passar por validações de segurança e segurança definidas antes da implantação.

|   #   | Descrição                                                                                                                                                                                                                                     | Nível | Papel |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 3.2.1 | Verifique se os modelos passam por testes automatizados de segurança que incluem validação de entrada, sanitização de saída e avaliações de segurança, com limites predefinidos de aprovação/reprovação organizacionais antes da implantação. |   1   |  D/V  |
| 3.2.2 | Verifique se as falhas de validação bloqueiam automaticamente a implantação do modelo após aprovação explícita de substituição por pessoal autorizado pré-designado com justificativas comerciais documentadas.                               |   1   |  D/V  |
| 3.2.3 | Verifique se os resultados do teste estão assinados criptograficamente e ligados de forma imutável ao hash da versão específica do modelo que está sendo validado.                                                                            |   2   |   V   |
| 3.2.4 | Verifique se as implantações de emergência exigem avaliação de risco de segurança documentada e aprovação de uma autoridade de segurança previamente designada dentro de prazos acordados.                                                    |   2   |  D/V  |

---

## C3.3 Implantação Controlada e Reversão

Implantações de modelos devem ser controladas, monitoradas e reversíveis.

|   #   | Descrição                                                                                                                                                                                                                                                                      | Nível | Papel |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 3.3.1 | Verifique se as implantações em produção implementam mecanismos de implantação gradual (implantação canário, implantação azul-verde) com gatilhos de rollback automatizados com base em taxas de erro pré-acordadas, limites de latência ou critérios de alertas de segurança. |   1   |   D   |
| 3.3.2 | Verifique se as funcionalidades de rollback restauram o estado completo do modelo ( pesos, configurações, dependências) de forma atômica dentro dos períodos organizacionais predefinidos.                                                                                     |   1   |  D/V  |
| 3.3.3 | Verifique se os processos de implantação validam assinaturas criptográficas e calculam verificações de integridade antes da ativação do modelo, falhando na implantação em qualquer incompatibilidade.                                                                         |   2   |  D/V  |
| 3.3.4 | Verifique se as capacidades de desligamento de emergência do modelo podem desabilitar endpoints do modelo dentro de tempos de resposta predefinidos por meio de disjuntores automáticos ou interruptores manuais.                                                              |   2   |  D/V  |
| 3.3.5 | Verifique se os artefatos de rollback (versões anteriores do modelo, configurações, dependências) estão retidos de acordo com as políticas organizacionais, utilizando armazenamento imutável para resposta a incidentes.                                                      |   2   |   V   |

---

## C3.4 Responsabilidade pela Alteração e Auditoria

Todas as mudanças no ciclo de vida do modelo devem ser rastreáveis e auditáveis.

|   #   | Descrição                                                                                                                                                                                                                                                                | Nível | Papel |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 3.4.1 | Verifique se todas as alterações no modelo (implantação, configuração, aposentadoria) geram registros de auditoria imutáveis, incluindo um carimbo de data/hora, uma identidade de ator autenticada, um tipo de alteração e os estados antes/depois.                     |   1   |   V   |
| 3.4.2 | Verifique se o acesso ao registro de auditoria exige autorização adequada e se todas as tentativas de acesso são registradas com identidade do usuário e um carimbo de data/hora.                                                                                        |   2   |  D/V  |
| 3.4.3 | Verifique se os modelos de prompt e as mensagens do sistema estão sob controle de versão em repositórios git, com revisão de código obrigatória e aprovação de revisores designados antes do implantação.                                                                |   2   |  D/V  |
| 3.4.4 | Verifique se os registros de auditoria incluem detalhes suficientes ( hashes de modelos, snapshots de configuração, versões de dependências) para permitir a reconstrução completa do estado do modelo para qualquer carimbo de data/hora dentro do período de retenção. |   2   |   V   |

---

## C3.5 Práticas Seguras de Desenvolvimento

Os processos de desenvolvimento e treinamento de modelos devem seguir práticas seguras para evitar comprometimento.

|   #   | Descrição                                                                                                                                                                                                                               | Nível | Papel |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 3.5.1 | Verifique se os ambientes de desenvolvimento, teste e produção do modelo estão fisicamente ou logicamente separados. Eles não compartilham infraestrutura, possuem controles de acesso distintos e armazenamentos de dados isolados.    |   1   |   D   |
| 3.5.2 | Verifique se o treinamento do modelo e o ajuste fino ocorrem em ambientes isolados com acesso controlado à rede.                                                                                                                        |   1   |   D   |
| 3.5.3 | Verifique se as fontes de dados de treinamento são validadas por meio de verificações de integridade e autenticadas por fontes confiáveis com cadeia de custódia documentada antes de serem usadas no desenvolvimento do modelo.        |   1   |  D/V  |
| 3.5.4 | Verifique se os artefatos de desenvolvimento do modelo (hiperparâmetros, scripts de treinamento, arquivos de configuração) estão armazenados no controle de versão e exigem aprovação de revisão por pares antes do uso no treinamento. |   2   |   D   |

---

## C3.6 Aposentadoria e Desativação de Modelos

Os modelos devem ser desativados de forma segura quando não forem mais necessários ou quando forem identificados problemas de segurança.

|   #   | Descrição                                                                                                                                                                                                                                                  | Nível | Papel |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 3.6.1 | Verifique se os processos de aposentadoria do modelo escaneiam automaticamente os gráficos de dependência, identificam todos os sistemas consumidores e oferecem períodos de aviso prévio acordados previamente antes do desligamento.                     |   1   |   D   |
| 3.6.2 | Verifique se os artefatos de modelos aposentados foram apagados de forma segura usando apagamento criptográfico ou sobrescrição múltipla, de acordo com as políticas de retenção de dados documentadas, com certificados de destruição verificados.        |   1   |  D/V  |
| 3.6.3 | Verifique se os eventos de desativação do modelo estão registrados com timestamp e identidade do ator, e se as assinaturas do modelo são revogadas para prevenir reutilização.                                                                             |   2   |   V   |
| 3.6.4 | Verifique se a aposentadoria do modelo de emergência pode desabilitar o acesso ao modelo dentro dos prazos preestabelecidos de resposta de emergência por meio de interrupções automáticas, caso vulnerabilidades críticas de segurança sejam descobertas. |   2   |  D/V  |

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

