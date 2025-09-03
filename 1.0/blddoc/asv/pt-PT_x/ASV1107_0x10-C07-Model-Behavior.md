# C7 Comportamento do Modelo, Controle de Saída e Garantia de Segurança

## Objetivo de Controle

As saídas do modelo devem ser estruturadas, confiáveis, seguras, explicáveis e continuamente monitoradas em produção. Isso reduz alucinações, vazamentos de privacidade, conteúdo nocivo e ações fora de controle, enquanto aumenta a confiança do usuário e a conformidade regulatória.

---

## C7.1 Aplicação do Formato de Saída

Esquemas estritos, decodificação com restrições e validação a jusante impedem conteúdo malformado ou malicioso antes que ele se propague.

|   #   | Descrição                                                                                                                                                                                        | Nível | Papel |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 7.1.1 | Verifique se os esquemas de resposta (por exemplo, JSON Schema) são fornecidos no prompt do sistema e se cada saída é validada automaticamente; saídas não conformes acionam reparo ou rejeição. |   1   |  D/V  |
| 7.1.2 | Verifique se a decodificação com restrições (tokens de parada, regex, max-tokens) está habilitada para evitar estouro ou canais laterais de injeção de prompt.                                   |   1   |  D/V  |
| 7.1.3 | Verifique se os componentes a jusante tratam as saídas como não confiáveis e as validam contra esquemas ou deserializadores à prova de injeção.                                                  |   2   |  D/V  |
| 7.1.4 | Verifique se os eventos de saída imprópria são registrados, limitados por taxa e disponibilizados ao monitoramento.                                                                              |   3   |   V   |

---

## C7.2 Detecção e Mitigação de Alucinações

A estimativa de incerteza e estratégias de contingência limitam respostas fabricadas.

|   #   | Descrição                                                                                                                                                                                 | Nível | Papel |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 7.2.1 | Verifique se as log-probabilidades por token, a consistência do ensemble ou detectores de alucinação ajustados atribuem uma pontuação de confiança a cada resposta.                       |   1   |  D/V  |
| 7.2.2 | Verifique se as respostas abaixo de um limiar de confiança configurável acionam fluxos de fallback (por exemplo, geração aumentada por recuperação, modelo secundário ou revisão humana). |   1   |  D/V  |
| 7.2.3 | Verifique se os incidentes de alucinação estão rotulados com metadados da causa raiz e alimentados nos pipelines de post-mortem e de ajuste fino.                                         |   2   |  D/V  |
| 7.2.4 | Verifique se os limiares e detectores são recalibrados após grandes atualizações do modelo ou da base de conhecimento.                                                                    |   3   |  D/V  |
| 7.2.5 | Verifique se as visualizações do painel monitoram as taxas de alucinação.                                                                                                                 |   3   |   V   |

---

## C7.3 Filtragem de Segurança e Privacidade de Saída

Políticas de filtragem e cobertura da equipe vermelha protegem os usuários e dados confidenciais.

|   #   | Descrição                                                                                                                                                                              | Nível | Papel |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 7.3.1 | Verifique se os classificadores pré-geração e pós-geração bloqueiam conteúdo de ódio, assédio, autolesão, extremismo e conteúdo sexualmente explícito, em conformidade com a política. |   1   |  D/V  |
| 7.3.2 | Verifique se a detecção de PII/PCI e a anonimização automática são executadas em cada resposta; violações geram um incidente de privacidade.                                           |   1   |  D/V  |
| 7.3.3 | Verifique se as etiquetas de confidencialidade se propagam entre modalidades para evitar vazamento em texto, imagens ou código.                                                        |   2   |   D   |
| 7.3.4 | Verifique se tentativas de burlar o filtro ou classificações de alto risco exigem aprovação secundária ou reautenticação do usuário.                                                   |   3   |  D/V  |
| 7.3.5 | Verifique se os limiares de filtragem refletem as jurisdições legais e o contexto de idade e função do usuário.                                                                        |   3   |  D/V  |

---

## C7.4 Limitação de Saída e Ação

Limites de taxa e portas de aprovação impedem abusos e autonomia excessiva.

|   #   | Descrição                                                                                                                                                                                   | Nível | Papel |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 7.4.1 | Verifique se as cotas por usuário e por chave de API limitam solicitações, tokens e custo, com back-off exponencial em erros 429.                                                           |   1   |   D   |
| 7.4.2 | Verifique se ações privilegiadas (escrita de arquivos, execução de código, chamadas de rede) exigem aprovação baseada em políticas ou intervenção humana no loop.                           |   1   |  D/V  |
| 7.4.3 | Verifique se as verificações de consistência entre modalidades garantem que imagens, código e texto gerados para a mesma solicitação não possam ser usados para ocultar conteúdo malicioso. |   2   |  D/V  |
| 7.4.4 | Verifique se a profundidade de delegação do agente, os limites de recursão e as listas de ferramentas permitidas estão configurados de forma explícita.                                     |   2   |   D   |
| 7.4.5 | Verifique se a violação de limites emite eventos de segurança estruturados para ingestão pelo SIEM.                                                                                         |   3   |   V   |

---

## C7.5 Explicabilidade da Saída

Sinais transparentes melhoram a confiança do usuário e a depuração interna.

|   #   | Descrição                                                                                                                                                | Nível | Papel |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 7.5.1 | Verifique se as pontuações de confiança apresentadas ao usuário ou breves resumos do raciocínio são expostos quando a avaliação de risco assim o exigir. |   2   |  D/V  |
| 7.5.2 | Verifique se as explicações geradas evitam revelar prompts do sistema sensíveis ou dados proprietários.                                                  |   2   |  D/V  |
| 7.5.3 | Verifique se o sistema captura probabilidades logarítmicas por token ou mapas de atenção e os armazena para inspeção autorizada.                         |   3   |   D   |
| 7.5.4 | Verifique se os artefatos de explicabilidade estão sob controle de versão juntamente com as liberações do modelo, para auditabilidade.                   |   3   |   V   |

---

## C7.6 Integração de Monitoramento

Observabilidade em tempo real fecha o ciclo entre desenvolvimento e produção.

|   #   | Descrição                                                                                                                                                               | Nível | Papel |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 7.6.1 | Verifique se as métricas (violações de esquema, taxa de alucinação, toxicidade, vazamentos de PII, latência, custo) fluem para uma plataforma central de monitoramento. |   1   |   D   |
| 7.6.2 | Verifique se os limiares de alerta estão definidos para cada métrica de segurança, com caminhos de escalonamento em plantão.                                            |   1   |   V   |
| 7.6.3 | Verifique se os painéis correlacionam anomalias de saída com o modelo/versão, flag de recurso e alterações nos dados upstream.                                          |   2   |   V   |
| 7.6.4 | Verifique se os dados de monitoramento retroalimentam o re-treinamento, o ajuste fino ou as atualizações de regras dentro de um fluxo de MLOps documentado.             |   2   |  D/V  |
| 7.6.5 | Verifique se os pipelines de monitoramento são submetidos a testes de penetração e têm controle de acesso para evitar o vazamento de logs sensíveis.                    |   3   |   V   |

---

## 7.7 Salvaguardas da Mídia Generativa

Garanta que os sistemas de IA não gerem conteúdo de mídia ilegal, prejudicial ou não autorizado, aplicando restrições de políticas, validação de saída e rastreabilidade.

|   #   | Descrição                                                                                                                                                                                                                         | Nível | Papel |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 7.7.1 | Verifique se os prompts do sistema e as instruções do usuário proíbem explicitamente a geração de mídia deepfake ilegal, nociva ou não consensual (por exemplo, imagem, vídeo, áudio).                                            |   1   |  D/V  |
| 7.7.2 | Verifique se os prompts são filtrados para evitar tentativas de gerar suplantação de identidade, deepfakes sexualmente explícitos ou conteúdo que retrate pessoas reais sem consentimento.                                        |   2   |  D/V  |
| 7.7.3 | Verifique se o sistema utiliza uma função de hash perceptual, detecção de marca d’água ou fingerprinting para impedir a reprodução não autorizada de conteúdo protegido por direitos autorais.                                    |   2   |   V   |
| 7.7.4 | Verifique se toda a mídia gerada é assinada digitalmente, marcada com marca d'água ou incorporada com metadados de proveniência à prova de adulteração para rastreabilidade a jusante.                                            |   3   |  D/V  |
| 7.7.5 | Verifique se as tentativas de contorno (por exemplo, obfuscação de prompts, gírias, formulação adversarial) são detectadas, registradas e com limitação de taxa; abusos repetidos são encaminhados aos sistemas de monitoramento. |   3   |   V   |

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

