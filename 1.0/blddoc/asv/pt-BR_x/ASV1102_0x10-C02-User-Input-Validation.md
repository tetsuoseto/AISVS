# Validação de Entrada do Usuário C2

## Objetivo de Controle

Validação robusta da entrada do usuário é uma defesa de primeira linha contra alguns dos ataques mais destrutivos a sistemas de IA. Ataques de injeção de prompt podem sobrescrever instruções do sistema, vazar dados sensíveis ou direcionar o modelo para comportamentos não permitidos. A menos que filtros dedicados e hierarquias de instruções estejam em uso, pesquisas mostram que "jailbreaks" de múltiplas etapas que exploram janelas de contexto muito longas serão eficazes. Além disso, ataques de perturbação adversarial sutil — como trocas de homoglyphs ou leetspeak — podem alterar silenciosamente as decisões de um modelo.

---

## C2.1 Defesa contra Injeção de Prompt

Injeção de prompt é um dos principais riscos para sistemas de IA. As defesas contra essa tática empregam uma combinação de filtros de padrões estáticos, classificadores dinâmicos e aplicação de hierarquia de instruções.

|   #   | Descrição                                                                                                                                                                                                                                        | Nível | Papel |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 2.1.1 | Verifique se as entradas do usuário são filtradas em uma biblioteca continuamente atualizada de padrões conhecidos de injeção de prompt (palavras-chave de jailbreak, "ignore previous", cadeias de role-play, ataques indiretos de HTML/URL).   |   1   |  D/V  |
| 2.1.2 | Verifique se o sistema aplica uma hierarquia de instruções na qual mensagens do sistema ou do desenvolvedor prevalecem sobre as instruções do usuário, mesmo após a expansão da janela de contexto.                                              |   1   |  D/V  |
| 2.1.3 | Verifique se os testes de avaliação adversarial (por exemplo, prompts "many-shot" da Red Team) são executados antes de cada lançamento de modelo ou modelo de prompt, com limites de taxa de sucesso e bloqueadores automáticos para regressões. |   2   |  D/V  |
| 2.1.4 | Verifique se os prompts originados de conteúdo de terceiros (páginas da web, PDFs, e-mails) são sanitizados em um contexto de análise isolado antes de serem concatenados ao prompt principal.                                                   |   2   |   D   |
| 2.1.5 | Verifique se todas as atualizações das regras de filtro de prompts, versões do modelo de classificador e alterações na lista de bloqueio estão sob controle de versão e podem ser auditadas.                                                     |   3   |  D/V  |

---

## C2.2 Resistência a Exemplos Adversariais

Modelos de Processamento de Linguagem Natural (PLN) ainda são vulneráveis a perturbações sutis em nível de caractere ou palavra que os humanos frequentemente não percebem, mas que os modelos tendem a classificar incorretamente.

|   #   | Descrição                                                                                                                                                                                                                  | Nível | Papel |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 2.2.1 | Verifique se as etapas básicas de normalização de entrada (Unicode NFC, mapeamento de homoglifos, remoção de espaços em branco) são executadas antes da tokenização.                                                       |   1   |   D   |
| 2.2.2 | Verifique se a detecção de anomalias estatísticas sinaliza entradas com distância de edição incomumente alta em relação às normas do idioma, tokens repetidos em excesso ou distâncias de incorporação anormais.           |   2   |  D/V  |
| 2.2.3 | Verifique se o pipeline de inferência suporta variantes de modelo reforçadas por treinamento adversarial opcional ou camadas de defesa (por exemplo, randomização, destilação defensiva) para pontos finais de alto risco. |   2   |   D   |
| 2.2.4 | Verifique se entradas adversariais suspeitas estão em quarentena, registradas com cargas completas (após a redação de PII).                                                                                                |   2   |   V   |
| 2.2.5 | Verifique se as métricas de robustez (taxa de sucesso de suítes de ataques conhecidos) são monitoradas ao longo do tempo e se regressões acionam um bloqueador de liberação.                                               |   3   |  D/V  |

---

## C2.3 Validação de Esquema, Tipo e Comprimento

Ataques de IA apresentando entradas malformadas ou oversized podem causar erros de análise, vazamentos de prompts entre campos e exaustão de recursos. A aplicação rigorosa de esquema também é um requisito prévio ao realizar chamadas determinísticas de ferramentas.

|   #   | Descrição                                                                                                                                                                                                   | Nível | Papel |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 2.3.1 | Verifique se cada endpoint de API ou chamada de função define um esquema de entrada explícito (JSON Schema, Protobuf ou equivalente multimodal) e se as entradas são validadas antes da montagem do prompt. |   1   |   D   |
| 2.3.2 | Verifique se entradas que ultrapassam os limites máximos de tokens ou bytes são rejeitadas com uma mensagem de erro segura e nunca truncadas silenciosamente.                                               |   1   |  D/V  |
| 2.3.3 | Verifique se as verificações de tipo (por exemplo, intervalos numéricos, valores de enumeração, tipos MIME para imagens/áudio) são aplicadas no lado do servidor, e não apenas no código cliente.           |   2   |  D/V  |
| 2.3.4 | Verifique se os validadores semânticos (por exemplo, JSON Schema) são executados em tempo constante para evitar DoS algorítmico.                                                                            |   2   |   D   |
| 2.3.5 | Verifique se as falhas de validação são registradas com trechos de carga útil redigidos e códigos de erro unívocos para facilitar a triagem de segurança.                                                   |   3   |   V   |

---

## C2.4 Triagem de Conteúdo & Políticas

Os desenvolvedores devem ser capazes de detectar prompts sintaticamente válidos que solicitam conteúdo proibido (como instruções ilícitas, discurso de ódio e texto protegido por direitos autorais) e impedir que eles se propaguem.

|   #   | Descrição                                                                                                                                                                                                       | Nível | Papel |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 2.4.1 | Verifique se um classificador de conteúdo (zero shot ou ajustado) avalia todas as entradas para violência, automutilação, ódio, conteúdo sexual e pedidos ilegais, com limites configuráveis.                   |   1   |   D   |
| 2.4.2 | Verifique se as entradas que violam as políticas irão receber recusas padronizadas ou respostas seguras para que não sejam propagadas para chamadas subsequentes de modelos de linguagem de grande porte (LLM). |   1   |  D/V  |
| 2.4.3 | Verifique se o modelo de triagem ou conjunto de regras está sendo reestilizado/atualizado pelo menos a cada trimestre, incorporando novos padrões observados de jailbreak ou bypass de políticas.               |   2   |   D   |
| 2.4.4 | Verifique se a triagem respeita as políticas específicas do usuário (idade, restrições legais regionais) por meio de regras baseadas em atributos resolvidas no momento da solicitação.                         |   2   |   D   |
| 2.4.5 | Verifique se os registros de triagem incluem pontuações de confiança do classificador e tags de categorias de política para correlação SOC e futura reprodução da equipe de ataque.                             |   3   |   V   |

---

## C2.5 Limitação de Taxa de Entrada & Prevenção de Abuso

Os desenvolvedores devem prevenir abuso, exaustão de recursos e ataques automatizados contra sistemas de IA, limitando as taxas de entrada e detectando padrões de uso anômalos.

|   #   | Descrição                                                                                                                                       | Nível | Papel |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 2.5.1 | Verifique se os limites de taxa por usuário, por IP e por chave de API são aplicados a todos os endpoints de entrada.                           |   1   |  D/V  |
| 2.5.2 | Verifique se os limites de taxa de pico e sustentada estão ajustados para prevenir ataques DoS e de força bruta.                                |   2   |  D/V  |
| 2.5.3 | Verifique se padrões de uso anômalos (por exemplo, solicitações rápidas, inundação de entrada) acionam bloqueios automáticos ou escalonamentos. |   2   |  D/V  |
| 2.5.4 | Verifique se os registros de prevenção de abuso são retidos e revisados para padrões emergentes de ataque.                                      |   3   |   V   |

---

## C2.6 Validação de Entrada Multi-Modal

Sistemas de IA devem incluir validação robusta para entradas não textuais (imagens, áudio, arquivos) para prevenir injeção, evasão ou abuso de recursos.

|   #   | Descrição                                                                                                                                      | Nível | Papel |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 2.6.1 | Verifique se todas as entradas não-textuais (imagens, áudio, arquivos) são validadas quanto ao tipo, tamanho e formato antes do processamento. |   1   |   D   |
| 2.6.2 | Verifique se os arquivos são escaneados em busca de malware e payloads steganográficos antes da ingestão.                                      |   2   |  D/V  |
| 2.6.3 | Verifique se as entradas de imagem/árvore de áudio foram verificadas quanto a perturbações adversariais ou padrões de ataque conhecidos.       |   2   |  D/V  |
| 2.6.4 | Verifique se as falhas de validação de entrada multimodal são registradas e acionam alertas para investigação.                                 |   3   |   V   |

---

## C2.7 Proveniência da Entrada & Atribuição

Os sistemas de IA devem suportar auditoria, rastreamento de abuso e conformidade, monitorando e marcando as origens de todas as entradas de usuário.

|   #   | Descrição                                                                                                                                              | Nível | Papel |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 2.7.1 | Verifique se todas as entradas de usuário estão marcadas com metadados (ID do usuário, sessão, origem, carimbo de data/hora, endereço IP) na ingestão. |   1   |  D/V  |
| 2.7.2 | Verifique se os metadados de proveniência são mantidos e auditáveis para todas as entradas processadas.                                                |   2   |  D/V  |
| 2.7.3 | Verifique se fontes de entrada anômalas ou não confiáveis são sinalizadas e sujeitas a uma fiscalização aprimorada ou bloqueio.                        |   2   |  D/V  |

---

## C2.8 Detecção de Ameaças Adaptativa em Tempo Real

Os desenvolvedores devem empregar sistemas avançados de detecção de ameaças para IA que se adaptem a novos padrões de ataque e ofereçam proteção em tempo real com correspondência de padrões compilados.

|   #   | Descrição                                                                                                                                                                                                          | Nível | Papel |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 2.8.1 | Verifique se os padrões de detecção de ameaças estão compilados em mecanismos de regex otimizados para filtragem em tempo real de alto desempenho, com impacto mínimo na latência.                                 |   1   |  D/V  |
| 2.8.2 | Verifique se os sistemas de detecção de ameaças mantêm bibliotecas de padrões separadas para diferentes categorias de ameaças (injeção de prompt, conteúdo prejudicial, dados sensíveis, comandos do sistema).     |   1   |  D/V  |
| 2.8.3 | Verifique se a detecção adaptativa de ameaças incorpora modelos de aprendizado de máquina que atualizam a sensibilidade às ameaças com base na frequência de ataques e nas taxas de sucesso.                       |   2   |  D/V  |
| 2.8.4 | Verifique se os feeds de inteligência de ameaças em tempo real atualizam automaticamente as bibliotecas de padrões com novas assinaturas de ataque e IOCs (Indicadores de Comprometimento).                        |   2   |  D/V  |
| 2.8.5 | Verifique se as taxas de falsos positivos na detecção de ameaças são monitoradas continuamente e se a especificidade do padrão é ajustada automaticamente para minimizar interferências em casos de uso legítimos. |   3   |  D/V  |
| 2.8.6 | Verifique se a análise de ameaça contextual considera a fonte de entrada, os padrões de comportamento do usuário e o histórico da sessão para melhorar a precisão da detecção.                                     |   3   |  D/V  |
| 2.8.7 | Verifique se as métricas de desempenho na detecção de ameaças (taxa de detecção, latência de processamento, utilização de recursos) estão sendo monitoradas e otimizadas em tempo real.                            |   3   |  D/V  |

---

## C2.9 Pipeline de Validação de Segurança Multi-Modal

Os desenvolvedores devem fornecer validação de segurança para modalidades de entrada de IA, como texto, imagem, áudio e outras, com tipos específicos de detecção de ameaças e isolamento de recursos.

|   #   | Descrição                                                                                                                                                                                                                                                                           | Nível | Papel |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 2.9.1 | Verifique se cada modalidade de entrada possui validadores de segurança dedicados com padrões de ameaça documentados (texto: injeção de comandos, imagens: esteganografia, áudio: ataques por espectrograma) e limites de detecção.                                                 |   1   |  D/V  |
| 2.9.2 | Verifique se as entradas multimodais são processadas em sandboxes isolados com limites de recursos definidos ( memória, CPU, tempo de processamento) específicos para cada tipo de modalidade e documentados nas políticas de segurança.                                            |   2   |  D/V  |
| 2.9.3 | Verifique se a detecção de ataques cruzados de modalidades identifica ataques coordenados que abrangem múltiplos tipos de entrada (por exemplo, cargas útil esteganográficas em imagens combinadas com injeção de prompt em texto) com regras de correlação e geração de alertas.   |   2   |  D/V  |
| 2.9.4 | Verifique se as falhas de validação multimodal acionam registros detalhados, incluindo todas as modalidades de entrada, resultados da validação, pontuações de ameaça e análise de correlação com formatos de registro estruturados para integração com SIEM.                       |   3   |  D/V  |
| 2.9.5 | Verifique se os classificadores de conteúdo específicos de modalidade estão atualizados de acordo com os cronogramas documentados (mínimo trimestralmente) com novos padrões de ameaças, exemplos adversariais e benchmarks de desempenho mantidos acima dos limites de referência. |   3   |  D/V  |

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

