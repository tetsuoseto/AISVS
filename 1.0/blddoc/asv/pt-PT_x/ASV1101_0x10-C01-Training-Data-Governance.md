# Governança de Dados de Treinamento C1 e Gestão de Viés

## Objetivo de Controle

Os dados de treinamento devem ser obtidos, manejados e mantidos de maneira que preservem a proveniência, segurança, qualidade e justiça. Fazer isso cumpre deveres legais e reduz riscos de viés, envenenamento ou violações de privacidade que possam surgir durante o treinamento e afetar todo o ciclo de vida da IA.

---

## C1.1 Procedência dos Dados de Treinamento

Mantenha um inventário verificável de todos os conjuntos de dados, aceite apenas fontes confiáveis e registre todas as alterações para garantir auditabilidade.

|   #   | Descrição                                                                                                                                                                                                  | Nível | Função |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :----: |
| 1.1.1 | Verifique se um inventário atualizado de cada fonte de dados de treinamento (origem, responsável/dono, licença, método de coleta, restrições de uso pretendido e histórico de processamento) está mantido. |   1   |  D/V   |
| 1.1.2 | Verifique se os processos de dados de treinamento excluem recursos, atributos ou campos desnecessários (por exemplo, metadados não utilizados, PII sensível, dados de teste vazados).                      |   1   |  D/V   |
| 1.1.3 | Verifique se todas as alterações no conjunto de dados estão sujeitas a um fluxo de trabalho de aprovação registrado.                                                                                       |   2   |  D/V   |
| 1.1.4 | Verifique se os conjuntos de dados ou subconjuntos estão marcados com marca d'água ou possuem impressão digital onde for viável.                                                                           |   3   |  D/V   |

---

## C1.2 Segurança e Integridade dos Dados de Treinamento

Restrinja o acesso aos dados de treinamento, criptografe-os em repouso e em trânsito, e valide sua integridade para evitar adulterações, roubo ou envenenamento de dados.

|   #   | Descrição                                                                                                                                                                                        | Nível | Função |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :----: |
| 1.2.1 | Verifique se os controles de acesso protegem o armazenamento de dados de treinamento e os pipelines.                                                                                             |   1   |  D/V   |
| 1.2.2 | Verifique se todo o acesso aos dados de treinamento é registrado, incluindo usuário, horário e ação.                                                                                             |   2   |  D/V   |
| 1.2.3 | Verifique se os conjuntos de dados de treinamento estão criptografados em trânsito e em repouso, utilizando algoritmos criptográficos padrão da indústria e práticas de gerenciamento de chaves. |   2   |  D/V   |
| 1.2.4 | Verifique se hashes criptográficos ou assinaturas digitais são usados para garantir a integridade dos dados durante o armazenamento e a transferência dos dados de treinamento.                  |   2   |  D/V   |
| 1.2.5 | Verifique se as técnicas automatizadas de detecção são aplicadas para proteger contra modificações não autorizadas ou corrupção dos dados de treinamento.                                        |   2   |  D/V   |
| 1.2.6 | Verifique se os dados de treinamento obsoletos são eliminados de forma segura ou anonimizados.                                                                                                   |   2   |  D/V   |
| 1.2.7 | Verifique se todas as versões do conjunto de dados de treinamento são identificadas de forma única, armazenadas de maneira imutável e auditáveis para suportar reversão e análise forense.       |   3   |  D/V   |

---

## C1.3 Qualidade, Integridade e Segurança da Rotulagem dos Dados de Treinamento

Proteger rótulos e exigir revisão técnica para dados críticos.

|   #   | Descrição                                                                                                                                                                                                                             | Nível | Função |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :----: |
| 1.3.1 | Verifique se hashes criptográficos ou assinaturas digitais são aplicados aos artefatos de rótulo para garantir sua integridade e autenticidade.                                                                                       |   2   |  D/V   |
| 1.3.2 | Verifique se as interfaces e plataformas de rotulagem aplicam controles de acesso rigorosos, mantêm registros de auditoria à prova de adulteração de todas as atividades de rotulagem e protegem contra modificações não autorizadas. |   2   |  D/V   |
| 1.3.3 | Verifique se as informações sensíveis nos rótulos são redigidas, anonimizadas ou criptografadas ao nível do campo de dados, tanto em repouso quanto em trânsito.                                                                      |   3   |  D/V   |

---

## C1.4 Qualidade dos Dados de Treinamento e Garantia de Segurança

Combine validação automatizada, verificações manuais pontuais e remediação registrada para garantir a confiabilidade do conjunto de dados.

|   #   | Descrição                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | Nível | Função |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :----: |
| 1.4.1 | Verifique se os testes automatizados detectam erros de formato e valores nulos em cada ingestão ou transformação significativa de dados.                                                                                                                                                                                                                                                                                                                                    |   1   |   D    |
| 1.4.2 | Verifique se os pipelines de treinamento e ajuste fino de LLM implementam a detecção de envenenamento e a validação da integridade dos dados (por exemplo, métodos estatísticos, detecção de outliers, análise de embeddings) para identificar potenciais ataques de envenenamento (por exemplo, inversão de rótulos, inserção de gatilhos de backdoor, comandos de troca de função, ataques por instâncias influentes) ou corrupção involuntária dos dados de treinamento. |   2   |  D/V   |
| 1.4.3 | Verifique se defesas apropriadas, como treinamento adversarial (usando exemplos adversariais gerados), aumento de dados com entradas perturbadas ou técnicas de otimização robusta, estão implementadas e ajustadas para os modelos relevantes com base na avaliação de risco.                                                                                                                                                                                              |   3   |  D/V   |
| 1.4.4 | Verifique se os rótulos gerados automaticamente (por exemplo, via LLMs ou supervisão fraca) estão sujeitos a limiares de confiança e verificações de consistência para detectar rótulos alucinatórios, enganosos ou de baixa confiança.                                                                                                                                                                                                                                     |   2   |  D/V   |
| 1.4.5 | Verifique se os testes automatizados detectam deslocamentos de rótulos em cada ingestão ou transformação significativa de dados.                                                                                                                                                                                                                                                                                                                                            |   3   |   D    |

---

## C1.5 Linhagem e Rastreabilidade de Dados

Rastreie toda a jornada de cada ponto de dado desde a fonte até a entrada do modelo para auditabilidade e resposta a incidentes.

|   #   | Descrição                                                                                                                                                                                                                                              | Nível | Função |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :----: |
| 1.5.1 | Verifique se a linhagem de cada ponto de dados, incluindo todas as transformações, ampliações e mesclagens, está registrada e pode ser reconstruída.                                                                                                   |   2   |  D/V   |
| 1.5.2 | Verifique se os registros de linhagem são imutáveis, armazenados de forma segura e acessíveis para auditorias.                                                                                                                                         |   2   |  D/V   |
| 1.5.3 | Verifique se o rastreamento de linhagem cobre dados sintéticos gerados por meio de técnicas de preservação de privacidade ou generativas e se todos os dados sintéticos estão claramente rotulados e distinguíveis dos dados reais em todo o pipeline. |   2   |  D/V   |

---

## Referências

* [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)
* [EU AI Act – Article 10: Data & Data Governance](https://artificialintelligenceact.eu/article/10/)
* [MITRE ATLAS: Adversary Tactics for AI](https://atlas.mitre.org/)
* [Survey of ML Bias Mitigation Techniques – MDPI](https://www.mdpi.com/2673-6470/4/1/1)
* [Data Provenance & Lineage Best Practices – Nightfall AI](https://www.nightfall.ai/ai-security-101/data-provenance-and-lineage)
* [Data Labeling Quality Standards – LabelYourData](https://labelyourdata.com/articles/data-labeling-quality-and-how-to-measure-it)
* [Training Data Poisoning Guide – Lakera.ai](https://www.lakera.ai/blog/training-data-poisoning)
* [CISA Advisory: Securing Data for AI Systems](https://www.cisa.gov/news-events/cybersecurity-advisories/aa25-142a)
* [ISO/IEC 23053: AI Management Systems Framework](https://www.iso.org/sectors/it-technologies/ai)
* [IBM: What is AI Governance?](https://www.ibm.com/think/topics/ai-governance)
* [Google AI Principles](https://ai.google/principles/)
* [GDPR & AI Training Data – DataProtectionReport](https://www.dataprotectionreport.com/2024/08/recent-regulatory-developments-in-training-artificial-intelligence-ai-models-under-the-gdpr/)
* [Supply-Chain Security for AI Data – AppSOC](https://www.appsoc.com/blog/ai-is-the-new-frontier-of-supply-chain-security)
* [OpenAI Privacy Center – Data Deletion Controls](https://privacy.openai.com/policies?modal=take-control)
* [Adversarial ML Dataset – Kaggle](https://www.kaggle.com/datasets/cnrieiit/adversarial-machine-learning-dataset)

