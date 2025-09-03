# C1 Governança de Dados de Treinamento e Gestão de Viés

## Objetivo de Controle

Os dados de treinamento devem ser obtidos, tratados e mantidos de modo a preservar a proveniência, a segurança, a qualidade e a equidade. Ao fazê-lo, cumpre obrigações legais e reduz os riscos de viés, envenenamento ou violações de privacidade que possam surgir durante o treinamento e afetar todo o ciclo de vida da IA.

---

## C1.1 Traçabilidade dos Dados de Treinamento

Manter um inventário verificável de todos os conjuntos de dados, aceitar apenas fontes confiáveis e registrar cada alteração para auditoria.

|   #   | Descrição                                                                                                                                                                                                               | Nível | Papel |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 1.1.1 | Verifique se um inventário atualizado de cada fonte de dados de treinamento (origem, responsável/proprietário, licença, método de coleta, restrições de uso pretendidas e histórico de processamento) é mantido.        |   1   |  D/V  |
| 1.1.2 | Verifique se os processos de dados de treinamento excluem recursos, atributos ou campos desnecessários (por exemplo, metadados não utilizados, informações de identificação pessoal sensíveis, dados de teste vazados). |   1   |  D/V  |
| 1.1.3 | Verifique se todas as alterações no conjunto de dados estão sujeitas a um fluxo de aprovação registrado.                                                                                                                |   2   |  D/V  |
| 1.1.4 | Verifique se conjuntos de dados ou subconjuntos estão marcados com marca d'água ou com impressão digital, quando for viável.                                                                                            |   3   |  D/V  |

---

## C1.2 Segurança e Integridade dos Dados de Treinamento

Restringir o acesso aos dados de treinamento, criptografá-los em repouso e em trânsito, e validar sua integridade para evitar adulteração, roubo ou envenenamento de dados.

|   #   | Descrição                                                                                                                                                                                                  | Nível | Papel |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 1.2.1 | Verifique se os controles de acesso protegem o armazenamento de dados de treinamento e os pipelines.                                                                                                       |   1   |  D/V  |
| 1.2.2 | Verifique se todo o acesso aos dados de treinamento é registrado, incluindo usuário, horário e ação.                                                                                                       |   2   |  D/V  |
| 1.2.3 | Verifique se os conjuntos de dados de treinamento estão criptografados em trânsito e em repouso, usando algoritmos criptográficos padrão da indústria e práticas de gerenciamento de chaves.               |   2   |  D/V  |
| 1.2.4 | Verifique se hashes criptográficos ou assinaturas digitais são usados para garantir a integridade dos dados durante o armazenamento e a transferência de dados de treinamento.                             |   2   |  D/V  |
| 1.2.5 | Verifique se as técnicas de detecção automatizadas são aplicadas para evitar modificações não autorizadas ou corrupção dos dados de treinamento.                                                           |   2   |  D/V  |
| 1.2.6 | Verifique se os dados de treinamento obsoletos são apagados com segurança ou anonimizados.                                                                                                                 |   2   |  D/V  |
| 1.2.7 | Verifique se todas as versões do conjunto de dados de treinamento estão identificadas de forma única, armazenadas de maneira imutável e passíveis de auditoria para apoiar a reversão e a análise forense. |   3   |  D/V  |

---

## C1.3 Rotulagem de Dados de Treinamento: Qualidade, Integridade e Segurança

Proteja rótulos e exija revisão técnica para dados críticos.

|   #   | Descrição                                                                                                                                                                                                                     | Nível | Papel |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 1.3.1 | Verifique se hashes criptográficos ou assinaturas digitais são aplicados aos artefatos de rotulagem para garantir a integridade e a autenticidade.                                                                            |   2   |  D/V  |
| 1.3.2 | Verifique se as interfaces e plataformas de rotulagem aplicam controles de acesso fortes, mantêm logs de auditoria à prova de adulteração de todas as atividades de rotulagem e protegem contra modificações não autorizadas. |   2   |  D/V  |
| 1.3.3 | Verifique se as informações sensíveis nos rótulos são redigidas, anonimizadas ou criptografadas no nível do campo de dados em repouso e em trânsito.                                                                          |   3   |  D/V  |

---

## C1.4 Qualidade dos Dados de Treinamento e Garantia de Segurança

Combine validação automatizada, checagens manuais pontuais e remediação registrada para garantir a confiabilidade do conjunto de dados.

|   #   | Descrição                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          | Nível | Papel |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 1.4.1 | Verifique se os testes automatizados detectam erros de formato e valores nulos em cada ingestão de dados ou transformação de dados significativa.                                                                                                                                                                                                                                                                                                                                                  |   1   |   D   |
| 1.4.2 | Verifique se os fluxos de treinamento e ajuste fino de modelos de linguagem de grande escala (LLM) implementam detecção de envenenamento e validação da integridade dos dados (por exemplo, métodos estatísticos, detecção de outliers, análise de embeddings) para identificar ataques de envenenamento potenciais (por exemplo, troca de rótulos, inserção de gatilho de backdoor, comandos de troca de papéis, ataques de instância influente) ou corrupção acidental dos dados de treinamento. |   2   |  D/V  |
| 1.4.3 | Verifique se defesas apropriadas, como treinamento adversarial (usando exemplos adversariais gerados), aumento de dados com entradas perturbadas ou técnicas de otimização robusta, são implementadas e ajustadas para os modelos relevantes com base na avaliação de risco.                                                                                                                                                                                                                       |   3   |  D/V  |
| 1.4.4 | Verifique se rótulos gerados automaticamente (por exemplo, por meio de modelos de linguagem de grande escala (LLMs) ou supervisão fraca) estão sujeitos a limiares de confiança e verificações de consistência para detectar rótulos alucinados, enganosos ou de baixa confiança.                                                                                                                                                                                                                  |   2   |  D/V  |
| 1.4.5 | Verifique se os testes automatizados capturam o desbalanceamento de rótulos em cada ingestão ou transformação de dados significativa.                                                                                                                                                                                                                                                                                                                                                              |   3   |   D   |

---

## C1.5 Linhagem de Dados e Rastreabilidade

Rastreie a trajetória completa de cada ponto de dados desde a origem até a entrada do modelo para auditabilidade e resposta a incidentes.

|   #   | Descrição                                                                                                                                                                                                                                                         | Nível | Papel |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 1.5.1 | Verifique se a linhagem de cada ponto de dados, incluindo todas as transformações, aumentos de dados e fusões, está registrada e pode ser reconstruída.                                                                                                           |   2   |  D/V  |
| 1.5.2 | Verifique se os registros de linhagem de dados são imutáveis, armazenados com segurança e acessíveis para auditorias.                                                                                                                                             |   2   |  D/V  |
| 1.5.3 | Verifique se o rastreamento da linhagem cobre dados sintéticos gerados por meio de técnicas de preservação de privacidade ou técnicas generativas e se todos os dados sintéticos estão claramente rotulados e distinguíveis dos dados reais ao longo do pipeline. |   2   |  D/V  |

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

