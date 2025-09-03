# Comportamento do Modelo C7, Controle de Saída e Garantia de Segurança

## Objetivo de Controle

As saídas do modelo devem ser estruturadas, confiáveis, seguras, explicáveis e continuamente monitoradas em produção. Isso reduz alucinações, vazamentos de privacidade, conteúdo prejudicial e ações descontroladas, aumentando ao mesmo tempo a confiança do usuário e a conformidade regulatória.

---

## C7.1 Aplicação da Forma de Saída

Esquemas rigorosos, decodificação com restrições e validação subsequente impedem que conteúdo malformado ou malicioso se propague.

|   #   | Descrição                                                                                                                                                                                          | Nível | Papel |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 7.1.1 | Verifique se os esquemas de resposta (por exemplo, JSON Schema) estão fornecidos no prompt do sistema e se toda saída é validada automaticamente; saídas não conformes acionam reparo ou rejeição. |   1   |  D/V  |
| 7.1.2 | Verifique se a decodificação restrita ( tokens de parada, regex, máximo de tokens) está habilitada para evitar estouro ou canais laterais de injeção de prompts.                                   |   1   |  D/V  |
| 7.1.3 | Verifique se os componentes downstream tratam as saídas como não confiáveis e as validam contra esquemas ou desserializadores seguros contra injeções.                                             |   2   |  D/V  |
| 7.1.4 | Verifique se eventos de saída incorreta são registrados, limitados em taxa e exibidos na monitoração.                                                                                              |   3   |   V   |

---

## C7.2 Detecção e Mitigação de Alucinações

A estimação de incerteza e estratégias de fallback reduzem respostas fabricadas.

|   #   | Descrição                                                                                                                                                                                 | Nível | Papel |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 7.2.1 | Verifique se as log-probabilidades a nível de token, a autossessão de ensemble ou os detectores de alucinação ajustados atribuem uma pontuação de confiança a cada resposta.              |   1   |  D/V  |
| 7.2.2 | Verifique se as respostas abaixo de um limiar de confiança configurável acionam fluxos de fallback (por exemplo, geração aumentada por recuperação, modelo secundário ou revisão humana). |   1   |  D/V  |
| 7.2.3 | Verifique se os incidentes de alucinação estão marcados com metadados de causa raiz e alimentados nos pipelines de análise pós-mortem e de ajuste fino.                                   |   2   |  D/V  |
| 7.2.4 | Verifique se os limiares e detectores foram recalibrados após atualizações principais do modelo ou da base de conhecimento.                                                               |   3   |  D/V  |
| 7.2.5 | Verifique se as visualizações do painel monitoram as taxas de alucinação.                                                                                                                 |   3   |   V   |

---

## C7.3 Filtragem de Segurança e Privacidade de Saída

Filtros de política e cobertura de red-team protegem usuários e dados confidenciais.

|   #   | Descrição                                                                                                                                                             | Nível | Papel |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 7.3.1 | Verifique se os classificadores pré e pós-geração bloqueiam conteúdo de ódio, assédio, autoagressão, extremismo e conteúdo sexual explicitamente alinhado à política. |   1   |  D/V  |
| 7.3.2 | Verifique se a detecção de PII/PCI e a redação automática estão sendo executadas em todas as respostas; violações devem gerar uma ocorrência de privacidade.          |   1   |  D/V  |
| 7.3.3 | Verifique se as tags de confidencialidade (por exemplo, segredos comerciais) se propagam entre modalidades para impedir vazamentos em texto, imagens ou código.       |   2   |   D   |
| 7.3.4 | Verifique se tentativas de contornar filtros ou classificações de alto risco exigem aprovação secundária ou reautenticação do usuário.                                |   3   |  D/V  |
| 7.3.5 | Verifique se os limites de filtragem refletem as jurisdições legais e o contexto de idade/função do usuário.                                                          |   3   |  D/V  |

---

## C7.4 Limitação de Saída & Ação

Limites de taxa e gates de aprovação impedem abuso e autonomia excessiva.

|   #   | Descrição                                                                                                                                                                          | Nível | Papel |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 7.4.1 | Verifique se as quotas por usuário e por chave de API limitam solicitações, tokens e custos com retrocesso exponencial em erros 429.                                               |   1   |   D   |
| 7.4.2 | Verifique se ações privilegiadas (gravações de arquivos, execução de código, chamadas de rede) exigem aprovação baseada em políticas ou intervenção humana.                        |   1   |  D/V  |
| 7.4.3 | Verifique se os testes de consistência cross-modal garantem que imagens, códigos e textos gerados para a mesma solicitação não possam ser usados para mascarar conteúdo malicioso. |   2   |  D/V  |
| 7.4.4 | Verifique se a profundidade de delegação de agente, os limites de recursão e as listas de ferramentas permitidas estão configurados explicitamente.                                |   2   |   D   |
| 7.4.5 | Verifique se a violação de limites emite eventos de segurança estruturados para ingestão em SIEM.                                                                                  |   3   |   V   |

---

## C7.5 Explicabilidade do Resultado

Sinais transparentes aumentam a confiança do usuário e a depuração interna.

|   #   | Descrição                                                                                                                                                   | Nível | Papel |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 7.5.1 | Verifique se as pontuações de confiança ou resumos de raciocínio breves voltados ao usuário são expostos quando a avaliação de risco considerar apropriado. |   2   |  D/V  |
| 7.5.2 | Verifique se as explicações geradas evitam revelar prompts de sistema confidenciais ou dados proprietários.                                                 |   2   |  D/V  |
| 7.5.3 | Verifique se o sistema captura log-probabilidades ao nível de token ou mapas de atenção e os armazena para inspeção autorizada.                             |   3   |   D   |
| 7.5.4 | Verifique se os artefatos de explicabilidade estão sob controle de versão junto com as versões do modelo para auditoria.                                    |   3   |   V   |

---

## C7.6 Integração de Monitoramento

A observabilidade em tempo real fecha o ciclo entre desenvolvimento e produção.

|   #   | Descrição                                                                                                                                                                                        | Nível | Papel |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 7.6.1 | Verifique se as métricas ( violações de esquema, taxa de alucinação, toxicidade, vazamentos de PII, latência, custo) estão sendo transmitidas para uma plataforma de monitoramento centralizada. |   1   |   D   |
| 7.6.2 | Verifique se os limites de alerta estão definidos para cada métrica de segurança, com rotas de escalonamento de plantão.                                                                         |   1   |   V   |
| 7.6.3 | Verifique se os painéis correlacionam anomalias de saída com modelo/versão, flag de recurso e mudanças nos dados upstream.                                                                       |   2   |   V   |
| 7.6.4 | Verifique se os dados de monitoramento retornam para requalificação, ajuste fino ou atualizações de regras dentro de um fluxo de trabalho documentado de MLOps.                                  |   2   |  D/V  |
| 7.6.5 | Verifique se os pipelines de monitoramento são testados quanto à penetração e controlados por acesso para evitar vazamento de logs sensíveis.                                                    |   3   |   V   |

---

## 7.7 Salvaguardas de Mídia Generativa

Garanta que os sistemas de IA não gerem conteúdo de mídia ilegal, prejudicial ou não autorizado, aplicando restrições de políticas, validação de saída e rastreabilidade.

|   #   | Descrição                                                                                                                                                                                                                                            | Nível | Papel |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 7.7.1 | Verifique se os prompts do sistema e as instruções do usuário proíbem explicitamente a geração de mídia deepfake ilegal, prejudicial ou não consensual (por exemplo, imagem, vídeo, áudio).                                                          |   1   |  D/V  |
| 7.7.2 | Verifique se os prompts estão filtrados para evitar tentativas de gerar impersonificações, deepfakes sexualmente explícitos ou mídia que retrate pessoas reais sem consentimento.                                                                    |   2   |  D/V  |
| 7.7.3 | Verifique se o sistema usa hashing perceptual, detecção de marca d'água ou fingerprinting para evitar a reprodução não autorizada de mídia protegida por direitos autorais.                                                                          |   2   |   V   |
| 7.7.4 | Verifique se todos os meios de comunicação gerados estão criptograficamente assinados, com marca d'água ou incorporados com metadados de proveniência à prova de adulteração para rastreabilidade futura.                                            |   3   |  D/V  |
| 7.7.5 | Verifique se as tentativas de contornar as restrições (por exemplo, obfuscação de prompts, gírias, frases adversariais) são detectadas, registradas em log e limitadas em taxa; abusos recorrentes são destacados para os sistemas de monitoramento. |   3   |   V   |

## Referências

* [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)
* [ISO/IEC 42001:2023 – AI Management System](https://www.iso.org/obp/ui/en/)
* [OWASP Top-10 for Large Language Model Applications (2025)](https://owasp.org/www-project-top-10-for-large-language-model-applications/)
* [Improper Output Handling – OWASP LLM05:2025](https://genai.owasp.org/llmrisk/llm052025-improper-output-handling/)
* [Practical Techniques to Constrain LLM Output](https://mychen76.medium.com/practical-techniques-to-constraint-llm-output-in-json-format-e3e72396c670)
* [Dataiku – Structured Text Generation Guide](https://blog.dataiku.com/your-guide-to-structured-text-generation)
* [VL-Uncertainty: Detecting Hallucinations](https://arxiv.org/abs/2411.11919)
* [HaDeMiF: Hallucination Detection & Mitigation](https://openreview.net/forum?id=VwOYxPScxB)
* [Building Confidence in LLM Outputs](https://www.alkymi.io/data-science-room/building-confidence-in-llm-outputs)
* [Explainable AI & LLMs](https://duncsand.medium.com/explainable-ai-140912d31b3b)
* [LLM Red-Teaming Guide](https://www.confident-ai.com/blog/red-teaming-llms-a-step-by-step-guide)
* [Sensitive Information Disclosure in LLMs](https://virtualcyberlabs.com/llm-sensitive-information-disclosure/)
* [LangChain – Chat Model Rate Limiting](https://python.langchain.com/docs/how_to/chat_model_rate_limiting/)
* [OpenAI Rate-Limit & Exponential Back-off](https://hackernoon.com/openais-rate-limit-a-guide-to-exponential-backoff-for-llm-evaluation)
* [Arize AI – LLM Observability Platform](https://arize.com/)

