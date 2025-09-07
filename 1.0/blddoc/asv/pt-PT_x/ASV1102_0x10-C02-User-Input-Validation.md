# Validação de Entrada do Usuário C2

## Objetivo de Controle

A validação robusta da entrada do usuário é uma defesa de primeira linha contra alguns dos ataques mais prejudiciais aos sistemas de IA. Ataques de injeção de prompt podem substituir instruções do sistema, vazar dados sensíveis ou direcionar o modelo para comportamentos não permitidos. A menos que filtros dedicados e hierarquias de instruções estejam em vigor, pesquisas indicam que jailbreaks "multi-shot" que exploram janelas de contexto muito longas serão eficazes. Além disso, ataques sutis de perturbação adversária — como trocas de homoglifos ou leetspeak — podem mudar silenciosamente as decisões de um modelo.

---

## C2.1 Defesa contra Injeção de Prompt

A injeção de prompt é um dos principais riscos para os sistemas de IA. As defesas contra essa tática empregam uma combinação de filtros de padrões estáticos, classificadores dinâmicos e aplicação da hierarquia das instruções.

|   #   | Descrição                                                                                                                                                                                                                                                         | Nível | Função |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :----: |
| 2.1.1 | Verifique se as entradas do usuário são filtradas contra uma biblioteca continuamente atualizada de padrões conhecidos de injeção de prompt (palavras-chave de jailbreak, "ignorar anterior", cadeias de interpretação de papéis, ataques indiretos em HTML/URL). |   1   |  D/V   |
| 2.1.2 | Verifique se o sistema aplica uma hierarquia de instruções na qual as mensagens do sistema ou do desenvolvedor substituem as instruções do usuário, mesmo após a expansão da janela de contexto.                                                                  |   1   |  D/V   |
| 2.1.3 | Verifique se os testes de avaliação adversarial (por exemplo, prompts "many-shot" de Red Team) são realizados antes de cada lançamento de modelo ou template de prompt, com limites mínimos de taxa de sucesso e bloqueadores automatizados para regressões.      |   2   |  D/V   |
| 2.1.4 | Verifique se os prompts originados de conteúdo de terceiros (páginas da web, PDFs, e-mails) são higienizados em um contexto de análise isolado antes de serem concatenados ao prompt principal.                                                                   |   2   |   D    |
| 2.1.5 | Verifique se todas as atualizações da regra de filtro de prompts, versões do modelo classificador e alterações na lista de bloqueio estão sob controle de versão e são auditáveis.                                                                                |   3   |  D/V   |

---

## C2.2 Resistência a Exemplos Adversariais

Modelos de Processamento de Linguagem Natural (PLN) ainda são vulneráveis a perturbações sutis em nível de caractere ou palavra que os humanos frequentemente não percebem, mas que os modelos tendem a classificar incorretamente.

|   #   | Descrição                                                                                                                                                                                                                    | Nível | Função |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :----: |
| 2.2.1 | Verifique se as etapas básicas de normalização de entrada (Unicode NFC, mapeamento de homoglifos, remoção de espaços em branco) são executadas antes da tokenização.                                                         |   1   |   D    |
| 2.2.2 | Verifique se a detecção estatística de anomalias sinaliza entradas com distância de edição incomumente alta em relação às normas linguísticas, tokens repetidos em excesso ou distâncias anormais de embedding.              |   2   |  D/V   |
| 2.2.3 | Verifique se o pipeline de inferência suporta variantes opcionais de modelos reforçados por treinamento adversarial ou camadas de defesa (por exemplo, randomização, destilação defensiva) para pontos finais de alto risco. |   2   |   D    |
| 2.2.4 | Verifique se as entradas adversariais suspeitas estão isoladas, registradas com cargas completas (após a remoção de informações pessoais identificáveis).                                                                    |   2   |   V    |
| 2.2.5 | Verifique se as métricas de robustez (taxa de sucesso dos conjuntos de ataques conhecidos) são monitoradas ao longo do tempo e se as regressões acionam um bloqueio de lançamento.                                           |   3   |  D/V   |

---

## C2.3 Validação de Esquema, Tipo e Tamanho

Ataques de IA que envolvem entradas malformadas ou de tamanho excessivo podem causar erros de análise, vazamento de comandos entre campos e exaustão de recursos. A aplicação rigorosa do esquema também é um pré-requisito ao realizar chamadas de ferramentas determinísticas.

|   #   | Descrição                                                                                                                                                                                                   | Nível | Função |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :----: |
| 2.3.1 | Verifique se cada endpoint de chamada de API ou função define um esquema de entrada explícito (JSON Schema, Protobuf ou equivalente multimodal) e se as entradas são validadas antes da montagem do prompt. |   1   |   D    |
| 2.3.2 | Verifique se as entradas que excedem o limite máximo de tokens ou bytes são rejeitadas com um erro seguro e nunca truncadas silenciosamente.                                                                |   1   |  D/V   |
| 2.3.3 | Verifique se as verificações de tipo (por exemplo, intervalos numéricos, valores de enumeração, tipos MIME para imagens/áudio) são aplicadas no lado do servidor, e não apenas no código do cliente.        |   2   |  D/V   |
| 2.3.4 | Verifique se os validadores semânticos (por exemplo, JSON Schema) operam em tempo constante para evitar DoS algorítmico.                                                                                    |   2   |   D    |
| 2.3.5 | Verifique se as falhas de validação são registradas com trechos de carga útil redigidos e códigos de erro inequívocos para auxiliar no processo de triagem de segurança.                                    |   3   |   V    |

---

## C2.4 Triagem de Conteúdo e Política

Os desenvolvedores devem ser capazes de detectar comandos sintaticamente válidos que solicitam conteúdo proibido (como instruções ilícitas, discurso de ódio e texto protegido por direitos autorais) e impedir que eles se propaguem.

|   #   | Descrição                                                                                                                                                                                          | Nível | Função |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :----: |
| 2.4.1 | Verifique se um classificador de conteúdo (zero shot ou ajustado) avalia cada entrada quanto a violência, automutilação, ódio, conteúdo sexual e solicitações ilegais, com limiares configuráveis. |   1   |   D    |
| 2.4.2 | Verifique se as entradas que violam as políticas receberão recusas padronizadas ou conclusões seguras para que não se propaguem para chamadas LLM subsequentes.                                    |   1   |  D/V   |
| 2.4.3 | Verifique se o modelo de triagem ou o conjunto de regras é re-treinado/atualizado pelo menos trimestralmente, incorporando novos padrões de jailbreak ou bypass de políticas observados.           |   2   |   D    |
| 2.4.4 | Verifique se a triagem respeita as políticas específicas do usuário (idade, restrições legais regionais) por meio de regras baseadas em atributos resolvidas no momento da solicitação.            |   2   |   D    |
| 2.4.5 | Verifique se os registros de triagem incluem pontuações de confiança do classificador e etiquetas de categoria de política para correlação SOC e reprodução futura de red team.                    |   3   |   V    |

---

## C2.5 Limitação de Taxa de Entrada e Prevenção de Abuso

Os desenvolvedores devem prevenir abusos, exaustão de recursos e ataques automatizados contra sistemas de IA, limitando as taxas de entrada e detectando padrões anômalos de uso.

|   #   | Descrição                                                                                                                                                  | Nível | Função |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :----: |
| 2.5.1 | Verifique se os limites de taxa por usuário, por IP e por chave de API são aplicados para todos os endpoints de entrada.                                   |   1   |  D/V   |
| 2.5.2 | Verifique se os limites de taxa de estouro e sustentada estão ajustados para prevenir ataques DoS e de força bruta.                                        |   2   |  D/V   |
| 2.5.3 | Verifique se padrões de uso anômalos (por exemplo, requisições em rápida sucessão, inundação de entradas) acionam bloqueios automáticos ou escalonamentos. |   2   |  D/V   |
| 2.5.4 | Verifique se os registros de prevenção de abusos são mantidos e revisados para identificar padrões emergentes de ataque.                                   |   3   |   V    |

---

## C2.6 Validação de Entrada Multimodal

Os sistemas de IA devem incluir validação robusta para entradas não textuais (imagens, áudio, arquivos) para prevenir injeção, evasão ou abuso de recursos.

|   #   | Descrição                                                                                                                                      | Nível | Função |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :----: |
| 2.6.1 | Verifique se todas as entradas não textuais (imagens, áudio, arquivos) são validadas quanto ao tipo, tamanho e formato antes do processamento. |   1   |   D    |
| 2.6.2 | Verifique se os arquivos são escaneados em busca de malware e cargas úteis esteganográficas antes da ingestão.                                 |   2   |  D/V   |
| 2.6.3 | Verifique se as entradas de imagem/áudio são examinadas quanto a perturbações adversariais ou padrões de ataque conhecidos.                    |   2   |  D/V   |
| 2.6.4 | Verifique se as falhas na validação de entrada multimodal são registradas e acionam alertas para investigação.                                 |   3   |   V    |

---

## C2.7 Procedência e Atribuição de Entrada

Os sistemas de IA devem suportar auditoria, rastreamento de abuso e conformidade monitorando e etiquetando as origens de todas as entradas dos usuários.

|   #   | Descrição                                                                                                                                                         | Nível | Função |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :----: |
| 2.7.1 | Verifique se todas as entradas do usuário estão marcadas com metadados (ID do usuário, sessão, origem, carimbo de data/hora, endereço IP) no momento da ingestão. |   1   |  D/V   |
| 2.7.2 | Verifique se os metadados de proveniência são retidos e auditáveis para todas as entradas processadas.                                                            |   2   |  D/V   |
| 2.7.3 | Verifique se as fontes de entrada anômalas ou não confiáveis são sinalizadas e sujeitas a uma análise aprimorada ou bloqueio.                                     |   2   |  D/V   |

---

## C2.8 Detecção Adaptativa de Ameaças em Tempo Real

Os desenvolvedores devem empregar sistemas avançados de detecção de ameaças para IA que se adaptam a novos padrões de ataque e fornecem proteção em tempo real com correspondência de padrões compilados.

|   #   | Descrição                                                                                                                                                                                                           | Nível | Função |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :----: |
| 2.8.1 | Verifique se os padrões de detecção de ameaças são compilados em mecanismos regex otimizados para filtragem em tempo real de alto desempenho com impacto mínimo na latência.                                        |   1   |  D/V   |
| 2.8.2 | Verifique se os sistemas de detecção de ameaças mantêm bibliotecas de padrões separadas para diferentes categorias de ameaças (injeção de prompt, conteúdo prejudicial, dados sensíveis, comandos do sistema).      |   1   |  D/V   |
| 2.8.3 | Verifique se a detecção adaptativa de ameaças incorpora modelos de aprendizagem de máquina que atualizam a sensibilidade da ameaça com base na frequência e nas taxas de sucesso dos ataques.                       |   2   |  D/V   |
| 2.8.4 | Verifique se os feeds de inteligência de ameaças em tempo real atualizam automaticamente as bibliotecas de padrões com novas assinaturas de ataque e IOCs (Indicadores de Comprometimento).                         |   2   |  D/V   |
| 2.8.5 | Verifique se as taxas de falso positivo na detecção de ameaças são monitoradas continuamente e se a especificidade dos padrões é ajustada automaticamente para minimizar a interferência em casos de uso legítimos. |   3   |  D/V   |
| 2.8.6 | Verifique se a análise contextual de ameaças considera a fonte de entrada, os padrões de comportamento do usuário e o histórico da sessão para melhorar a precisão da detecção.                                     |   3   |  D/V   |
| 2.8.7 | Verifique se as métricas de desempenho da detecção de ameaças (taxa de detecção, latência de processamento, utilização de recursos) estão sendo monitoradas e otimizadas em tempo real.                             |   3   |  D/V   |

---

## C2.9 Pipeline de Validação de Segurança Multi-Modal

Os desenvolvedores devem fornecer validação de segurança para texto, imagem, áudio e outras modalidades de entrada de IA com tipos específicos de detecção de ameaças e isolamento de recursos.

|   #   | Descrição                                                                                                                                                                                                                                                                       | Nível | Função |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :----: |
| 2.9.1 | Verifique se cada modalidade de entrada possui validadores de segurança dedicados com padrões de ameaça documentados (texto: injeção de prompt, imagens: esteganografia, áudio: ataques de espectrograma) e limites de detecção.                                                |   1   |  D/V   |
| 2.9.2 | Verifique se as entradas multimodais são processadas em sandboxes isoladas com limites de recursos definidos (memória, CPU, tempo de processamento) específicos para cada tipo de modalidade e documentados nas políticas de segurança.                                         |   2   |  D/V   |
| 2.9.3 | Verifique se a detecção de ataques cruzados identifica ataques coordenados que abrangem múltiplos tipos de entrada (por exemplo, cargas ocultas esteganográficas em imagens combinadas com injeção de comandos em texto) por meio de regras de correlação e geração de alertas. |   2   |  D/V   |
| 2.9.4 | Verifique se as falhas de validação multimodal disparam logs detalhados, incluindo todas as modalidades de entrada, resultados da validação, pontuações de ameaça e análise de correlação com formatos de log estruturados para integração SIEM.                                |   3   |  D/V   |
| 2.9.5 | Verifique se os classificadores de conteúdo específicos por modalidade são atualizados de acordo com os cronogramas documentados (mínimo trimestralmente) com novos padrões de ameaça, exemplos adversariais e benchmarks de desempenho mantidos acima dos limiares base.       |   3   |  D/V   |

---

## Referências

* [LLM01:2025 Prompt Injection – OWASP Top 10 for LLM & Generative AI Security](https://genai.owasp.org/llmrisk/llm01-prompt-injection/)
* [Generative AI's Biggest Security Flaw Is Not Easy to Fix](https://www.wired.com/story/generative-ai-prompt-injection-hacking)
* [Many-shot jailbreaking \ Anthropic](https://www.anthropic.com/research/many-shot-jailbreaking)
* [$PDF$ OpenAI GPT-4.5 System Card](https://cdn.openai.com/gpt-4-5-system-card-2272025.pdf)
* [Notebook for the CheckThat Lab at CLEF 2024](https://ceur-ws.org/Vol-3740/paper-53.pdf)
* [Mitigate jailbreaks and prompt injections – Anthropic](https://docs.anthropic.com/en/docs/test-and-evaluate/strengthen-guardrails/mitigate-jailbreaks)
* [Chapter 3 MITRE ATT\&CK – Adversarial Model Analysis](https://ama.drwhy.ai/mitre-attck.html)
* [OWASP Top 10 for LLM Applications 2025 – WorldTech IT](https://wtit.com/blog/2025/04/17/owasp-top-10-for-llm-applications-2025/)
* [OWASP Machine Learning Security Top Ten](https://owasp.org/www-project-machine-learning-security-top-10/)
* [Few words about AI Security – Jussi Metso](https://www.jussimetso.com/index.php/2024/09/28/few-words-about-ai-security/)
* [How To Ensure LLM Output Adheres to a JSON Schema | Modelmetry](https://modelmetry.com/blog/how-to-ensure-llm-output-adheres-to-a-json-schema)
* [Easily enforcing valid JSON schema following – API](https://community.openai.com/t/feature-request-function-calling-easily-enforcing-valid-json-schema-following/263515?utm_source)
* [AI Safety + Cybersecurity R\&D Tracker – Fairly AI](https://www.fairly.ai/blog/ai-cybersecurity-tracker)
* [Anthropic makes 'jailbreak' advance to stop AI models producing harmful results](https://www.ft.com/content/cf11ebd8-aa0b-4ed4-945b-a5d4401d186e)
* [Pattern matching filter rules - IBM](https://www.ibm.com/docs/ssw_aix_71/security/intrusion_pattern_matching_filter_rules.html)
* [Real-time Threat Detection](https://www.darktrace.com/cyber-ai-glossary/real-time-threat-detection)

