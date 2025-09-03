# C3 Gerenciamento do Ciclo de Vida do Modelo e Controle de Mudanças

## Objetivo de Controle

Os sistemas de IA devem implementar processos de controle de alterações que impeçam modificações do modelo não autorizadas ou inseguras de chegarem à produção. Esse controle garante a integridade do modelo ao longo de todo o ciclo de vida--desde o desenvolvimento até a implantação até o descomissionamento--o que permite uma resposta rápida a incidentes e mantém a responsabilidade por todas as mudanças.

Objetivo de Segurança Central: Apenas modelos autorizados e validados chegam à produção, empregando processos controlados que mantenham integridade, rastreabilidade e recuperabilidade.

---

## C3.1 Autorização e Integridade do Modelo

Apenas modelos autorizados com integridade verificada chegam aos ambientes de produção.

|   #   | Descrição                                                                                                                                                                                                                                             | Nível | Papel |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 3.1.1 | Verifique se todos os artefatos do modelo (pesos, configurações, tokenizadores) são assinados criptograficamente por entidades autorizadas antes da implantação.                                                                                      |   1   |  D/V  |
| 3.1.2 | Verifique que a integridade do modelo seja validada no momento da implantação e que as falhas na verificação da assinatura impeçam o carregamento do modelo.                                                                                          |   1   |  D/V  |
| 3.1.3 | Verifique se os registros de proveniência do modelo incluem a identidade da entidade autorizadora, os checksums dos dados de treinamento, os resultados dos testes de validação com o status aprovado/reprovado e um carimbo de data/hora de criação. |   2   |  D/V  |
| 3.1.4 | Verifique se todos os artefatos do modelo utilizam versionamento semântico (MAJOR.MINOR.PATCH) com critérios documentados que especificam quando cada componente da versão é incrementado.                                                            |   2   |  D/V  |
| 3.1.5 | Verifique se o rastreamento de dependências mantém um inventário em tempo real que permita a identificação rápida de todos os sistemas que consomem.                                                                                                  |   2   |   V   |

---

## C3.2 Validação e Testes de Modelo

Os modelos devem passar pelas validações de segurança e conformidade definidas antes da implantação.

|   #   | Descrição                                                                                                                                                                                                                                                | Nível | Papel |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 3.2.1 | Verifique se os modelos passam por testes de segurança automatizados que incluem validação de entrada, sanitização de saída e avaliações de segurança, com limiares de aprovação/reprovação previamente acordados pela organização antes da implantação. |   1   |  D/V  |
| 3.2.2 | Verifique que as falhas de validação bloqueiem automaticamente a implantação do modelo após aprovação explícita de substituição por parte de pessoal autorizado pré-designado, com justificativas comerciais documentadas.                               |   1   |  D/V  |
| 3.2.3 | Verifique se os resultados dos testes são assinados criptograficamente e vinculados de forma imutável ao hash da versão específica do modelo que está sendo validada.                                                                                    |   2   |   V   |
| 3.2.4 | Verifique se as implantações emergenciais exigem avaliação de risco de segurança documentada e aprovação de uma autoridade de segurança previamente designada dentro de prazos previamente acordados.                                                    |   2   |  D/V  |

---

## C3.3 Implantação Controlada e Reversão

As implantações de modelos devem ser controladas, monitoradas e reversíveis.

|   #   | Descrição                                                                                                                                                                                                                                                                          | Nível | Papel |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 3.3.1 | Verifique se as implantações em produção implementam mecanismos de lançamento gradual (canary deployments, blue-green deployments) com gatilhos automáticos de reversão baseados em taxas de erro acordadas previamente, limites de latência ou critérios de alertas de segurança. |   1   |   D   |
| 3.3.2 | Verifique se as capacidades de reversão restauram o estado completo do modelo (pesos, configurações, dependências) de forma atômica dentro de janelas de tempo organizacionais pré-definidas.                                                                                      |   1   |  D/V  |
| 3.3.3 | Verifique se os processos de implantação validam assinaturas criptográficas e calculam somas de verificação de integridade antes da ativação do modelo, falhando a implantação em caso de qualquer discrepância.                                                                   |   2   |  D/V  |
| 3.3.4 | Verifique se as capacidades de desligamento de emergência do modelo podem desativar os endpoints do modelo dentro de tempos de resposta predefinidos, por meio de disjuntores automáticos ou interruptores manuais de desligamento.                                                |   2   |  D/V  |
| 3.3.5 | Verifique se os artefatos de rollback (versões anteriores do modelo, configurações, dependências) são retidos de acordo com as políticas organizacionais, com armazenamento imutável para resposta a incidentes.                                                                   |   2   |   V   |

---

## C3.4 Responsabilização de Mudanças e Auditoria

Todas as alterações no ciclo de vida do modelo devem ser rastreáveis e auditáveis.

|   #   | Descrição                                                                                                                                                                                                                                                                | Nível | Papel |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 3.4.1 | Verifique se todas as alterações de modelo (implantação, configuração, desativação) geram registros de auditoria imutáveis, incluindo um carimbo de data/hora, uma identidade de ator autenticado, um tipo de alteração e estados anterior e posterior.                  |   1   |   V   |
| 3.4.2 | Verifique se o acesso ao registro de auditoria requer autorização apropriada e se todas as tentativas de acesso são registradas com a identidade do usuário e um carimbo de data/hora.                                                                                   |   2   |  D/V  |
| 3.4.3 | Verifique que os modelos de prompt e as mensagens do sistema estejam sob controle de versão em repositórios Git, com revisão de código obrigatória e aprovação dos revisores designados antes da implantação.                                                            |   2   |  D/V  |
| 3.4.4 | Verifique se os registros de auditoria contêm detalhes suficientes (hashes do modelo, instantâneos de configuração, versões de dependências) para permitir a reconstrução completa do estado do modelo para qualquer carimbo de data/hora dentro do período de retenção. |   2   |   V   |

---

## C3.5 Práticas de Desenvolvimento Seguro

Os processos de desenvolvimento e treinamento de modelos devem seguir práticas seguras para evitar comprometimento.

|   #   | Descrição                                                                                                                                                                                                                                          | Nível | Papel |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 3.5.1 | Verifique se os ambientes de desenvolvimento, teste e produção do modelo estão fisicamente ou logicamente separados. Eles não compartilham infraestrutura, possuem controles de acesso distintos e bancos de dados isolados.                       |   1   |   D   |
| 3.5.2 | Verifique se o treinamento do modelo e o ajuste fino ocorrem em ambientes isolados com acesso à rede controlado.                                                                                                                                   |   1   |   D   |
| 3.5.3 | Verifique se as fontes de dados de treinamento são validadas por meio de verificações de integridade e autenticadas por fontes confiáveis com cadeia de custódia documentada antes de serem utilizadas no desenvolvimento do modelo.               |   1   |  D/V  |
| 3.5.4 | Verifique se os artefatos de desenvolvimento de modelos (hiperparâmetros, scripts de treinamento, arquivos de configuração) estão armazenados no controle de versão e exigem aprovação por revisão por pares antes de serem usados no treinamento. |   2   |   D   |

---

## C3.6 Aposentadoria de Modelos e Descomissionamento

Os modelos devem ser descomissionados com segurança quando não forem mais necessários ou quando questões de segurança forem identificadas.

|   #   | Descrição                                                                                                                                                                                                                                                              | Nível | Papel |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 3.6.1 | Verifique se os processos de desativação de modelos escaneiam automaticamente grafos de dependência, identificam todos os sistemas que consomem o modelo e fornecem períodos de aviso prévio acordados antes do descomissionamento.                                    |   1   |   D   |
| 3.6.2 | Verifique se artefatos de modelos aposentados são apagados com segurança usando apagamento criptográfico ou sobrescrita em várias passadas, de acordo com as políticas documentadas de retenção de dados, com certificados de destruição verificados.                  |   1   |  D/V  |
| 3.6.3 | Verifique se os eventos de retirada de modelos são registrados com carimbo de data/hora e com a identidade do ator, e se as assinaturas do modelo são revogadas para impedir a reutilização.                                                                           |   2   |   V   |
| 3.6.4 | Verifique se a retirada de emergência do modelo pode desativar o acesso ao modelo dentro dos prazos de resposta a emergências pré-estabelecidos, por meio de interruptores automáticos de desligamento, caso vulnerabilidades críticas de segurança sejam descobertas. |   2   |  D/V  |

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

