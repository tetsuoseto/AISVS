# 9 Segurança Da Orquestração Autônoma & Ação De Agente

## Objetivo de Controle

Garanta que sistemas de IA autônomos ou multiagentes possam executar apenas ações que sejam explicitamente pretendidas, autenticadas, auditáveis e dentro de limites de custo e risco definidos. Isso protege contra ameaças como Comprometimento de Sistemas Autônomos, Uso Indevido de Ferramentas, Detecção de Loop de Agentes, Sequestro de Comunicações, Falsificação de Identidade, Manipulação de Enxames e Manipulação de Intenções.

---

## 9.1 Planejamento de Tarefas do Agente e Orçamentos de Recursão

Limite planos recursivos e imponha pontos de verificação humanos para ações privilegiadas.

|   #   | Descrição                                                                                                                                                                                          | Nível | Papel |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.1.1 | Verifique se a profundidade máxima de recursão, a largura, o tempo de relógio, os tokens e o custo monetário por execução de cada agente estão configurados centralmente e sob controle de versão. |   1   |  D/V  |
| 9.1.2 | Verifique se ações privilegiadas ou irreversíveis (por exemplo, commits de código, transferências financeiras) exigem aprovação humana explícita por meio de um canal auditável antes da execução. |   1   |  D/V  |
| 9.1.3 | Verifique se os monitores de recursos em tempo-real acionam a interrupção do circuit-breaker quando qualquer limiar de orçamento é excedido, interrompendo a expansão adicional de tarefas.        |   2   |   D   |
| 9.1.4 | Verifique se os eventos do disjuntor são registrados com o ID do agente, a condição de disparo e o estado do plano capturado para revisão forense.                                                 |   2   |  D/V  |
| 9.1.5 | Verifique se os testes de segurança cobrem cenários de esgotamento de orçamento e de um plano fora de controle, confirmando a parada segura sem perda de dados.                                    |   3   |   V   |
| 9.1.6 | Verifique se as políticas de orçamento são expressas como policy-as-code e aplicadas no CI/CD para impedir a deriva de configuração.                                                               |   3   |   D   |

---

## 9.2 Isolamento de Plug-ins de Ferramentas

Isolar as interações com as ferramentas para impedir o acesso não autorizado ao sistema ou a execução de código.

|   #   | Descrição                                                                                                                                                                                      | Nível | Papel |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.2.1 | Verifique que cada ferramenta/plugin execute dentro de um sandbox de nível OS, contêiner ou WASM, com políticas de privilégios mínimos para o sistema de arquivos, rede e chamadas de sistema. |   1   |  D/V  |
| 9.2.2 | Verifique se as cotas de recursos do sandbox (CPU, memória, disco, tráfego de saída de rede) e os timeouts de execução são aplicados e registrados.                                            |   1   |  D/V  |
| 9.2.3 | Verifique se os binários da ferramenta ou descritores são assinados digitalmente; as assinaturas são validadas antes de serem carregadas.                                                      |   2   |  D/V  |
| 9.2.4 | Verifique se a telemetria do sandbox é enviada para um SIEM; anomalias (por exemplo, tentativas de conexões de saída) acionam alertas.                                                         |   2   |   V   |
| 9.2.5 | Verifique se plugins de alto risco passam por revisão de segurança e testes de penetração antes da implantação em produção.                                                                    |   3   |   V   |
| 9.2.6 | Verifique se as tentativas de evasão do sandbox são bloqueadas automaticamente e o plugin em questão é colocado em quarentena até a conclusão da investigação.                                 |   3   |  D/V  |

---

## 9.3 Laço Autônomo e Limite de Custo

Detectar e interromper a recursão descontrolada entre agentes e explosões de custo.

|   #   | Descrição                                                                                                                                                    | Nível | Papel |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 9.3.1 | Verifique se as chamadas entre agentes incluem um limite de saltos ou TTL que é decrementado e aplicado pelo tempo de execução.                              |   1   |  D/V  |
| 9.3.2 | Verifique se os agentes mantêm um ID único de grafo de invocação para detectar autoinvocação ou padrões cíclicos.                                            |   2   |   D   |
| 9.3.3 | Verifique se os contadores acumulados de unidades de computação e de gasto são rastreados por cadeia de solicitações; ultrapassar o limite encerra a cadeia. |   2   |  D/V  |
| 9.3.4 | Verifique se a análise formal ou a verificação de modelo demonstra a ausência de recursão ilimitada nos protocolos de agentes.                               |   3   |   V   |
| 9.3.5 | Verifique se os eventos de loop-abort geram alertas e alimentam métricas de melhoria contínua.                                                               |   3   |   D   |

---

## 9.4 Proteção contra uso indevido em nível de protocolo

Canais de comunicação seguros entre agentes e sistemas externos para evitar o sequestro de sessão ou a manipulação.

|   #   | Descrição                                                                                                                                                       | Nível | Papel |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.4.1 | Verifique se todas as mensagens entre agente e ferramenta e entre agentes estão autenticadas (por exemplo, TLS mútuo ou JWT) e criptografadas de ponta a ponta. |   1   |  D/V  |
| 9.4.2 | Verifique se os esquemas são validados estritamente; campos desconhecidos ou mensagens malformadas são rejeitadas.                                              |   1   |   D   |
| 9.4.3 | Verifique se as verificações de integridade (MACs ou assinaturas digitais) cobrem toda a carga útil da mensagem, incluindo os parâmetros da ferramenta.         |   2   |  D/V  |
| 9.4.4 | Verifique se a proteção contra replay (nonces ou janelas de carimbo de tempo) é aplicada na camada de protocolo.                                                |   2   |   D   |
| 9.4.5 | Verifique se as implementações de protocolo passam por fuzzing e análise estática para detectar falhas de injeção ou desserialização.                           |   3   |   V   |

---

## 9.5 Identidade do Agente e Evidência de Adulteração

Garanta que as ações sejam atribuíveis e que as modificações sejam detectáveis.

|   #   | Descrição                                                                                                                                              | Nível | Papel |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 9.5.1 | Verifique se cada instância de agente possui uma identidade criptográfica única (par de chaves ou credencial enraizada em hardware).                   |   1   |  D/V  |
| 9.5.2 | Verifique se todas as ações do agente estão assinadas e com carimbo de data/hora; os logs incluem a assinatura para não-repúdio.                       |   2   |  D/V  |
| 9.5.3 | Verifique se os logs à prova de adulteração são armazenados em um meio apenas de acréscimo (append-only) ou em um meio de gravação única (write-once). |   2   |   V   |
| 9.5.4 | Verifique se as chaves de identidade são rotacionadas de acordo com uma programação definida e com base em indicadores de comprometimento.             |   3   |   D   |
| 9.5.5 | Verifique se tentativas de spoofing ou de key-conflict acionam a quarentena imediata do agente afetado.                                                |   3   |  D/V  |

---

## 9.6 Redução de Risco do Enxame de Múltiplos Agentes

Mitigar riscos de comportamento coletivo por meio do isolamento e da modelagem formal de segurança.

|   #   | Descrição                                                                                                                                                  | Nível | Papel |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.6.1 | Verifique se os agentes que operam em diferentes domínios de segurança são executados em sandboxes de tempo de execução isolados ou em segmentos de rede.  |   1   |  D/V  |
| 9.6.2 | Verifique se os comportamentos de enxame são modelados e verificados formalmente quanto à vivacidade e à segurança antes da implantação.                   |   3   |   V   |
| 9.6.3 | Verifique se os monitores em tempo de execução detectam padrões inseguros emergentes (por exemplo, oscilações, interbloqueios) e iniciam ações corretivas. |   3   |   D   |

---

## 9.7 Autenticação / Autorização do Usuário e da Ferramenta

Implemente controles de acesso robustos para cada ação acionada por um agente.

|   #   | Descrição                                                                                                                                                | Nível | Papel |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.7.1 | Verifique se os agentes se autenticam como entidades de primeira classe em sistemas a jusante, nunca reutilizando credenciais do usuário final.          |   1   |  D/V  |
| 9.7.2 | Verifique se as políticas de autorização de granularidade fina restringem quais ferramentas um agente pode invocar e quais parâmetros ele pode fornecer. |   2   |   D   |
| 9.7.3 | Verifique se as verificações de privilégios são reavaliadas a cada chamada (autorização contínua), não apenas no início da sessão.                       |   2   |   V   |
| 9.7.4 | Verifique se as permissões delegadas expiram automaticamente e exigem novo consentimento após o tempo limite ou mudança de escopo.                       |   3   |   D   |

---

## 9.8 Segurança da Comunicação entre Agentes

Criptografe e proteja a integridade de todas as mensagens entre agentes para impedir a interceptação e a adulteração.

|   #   | Descrição                                                                                                                                           | Nível | Papel |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.8.1 | Verifique se a autenticação mútua e a criptografia com Perfect Forward Secrecy (PFS), como TLS 1.3, são obrigatórias para os canais de agentes.     |   1   |  D/V  |
| 9.8.2 | Verifique se a integridade da mensagem e a origem são validadas antes do processamento; as falhas geram alertas e a mensagem é descartada.          |   1   |   D   |
| 9.8.3 | Verifique se os metadados de comunicação (carimbos de tempo, números de sequência) são registrados para apoiar a reconstrução forense.              |   2   |  D/V  |
| 9.8.4 | Verifique se a verificação formal ou a verificação de modelo confirma que as máquinas de estados do protocolo não podem chegar a estados inseguros. |   3   |   V   |

---

## 9.9 Verificação de Intenção e Aplicação de Restrições

Verifique se as ações do agente estão alinhadas com a intenção declarada pelo usuário e com as restrições do sistema.

|   #   | Descrição                                                                                                                                                                                              | Nível | Papel |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 9.9.1 | Verifique se os solucionadores de restrições pré-execução verificam as ações propostas em relação às regras de segurança e políticas codificadas no código.                                            |   1   |   D   |
| 9.9.2 | Verifique se as ações de alto impacto (financeiras, destrutivas, sensíveis à privacidade) exigem confirmação explícita de intenção por parte do usuário que as iniciou.                                |   2   |  D/V  |
| 9.9.3 | Verifique se as verificações de pós-condição validam que as ações concluídas atingiram os efeitos pretendidos sem efeitos colaterais; as discrepâncias acionam a reversão.                             |   2   |   V   |
| 9.9.4 | Verifique se métodos formais (por exemplo, verificação de modelos, prova de teoremas) ou testes baseados em propriedades demonstram que os planos do agente satisfazem todas as restrições declaradas. |   3   |   V   |
| 9.9.5 | Verifique se incidentes de desalinhamento de intenções ou violação de restrições alimentam ciclos de melhoria contínua e o compartilhamento de inteligência de ameaças.                                |   3   |   D   |

---

## 9.10 Agente Raciocínio Estratégia Segurança

Seleção segura e execução de diferentes estratégias de raciocínio, incluindo as abordagens ReAct, Chain-of-Thought e Tree-of-Thoughts.

|   #    | Descrição                                                                                                                                                                                                                                                        | Nível | Papel |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.10.1 | Verifique que a seleção da estratégia de raciocínio utilize critérios determinísticos (complexidade de entrada, tipo de tarefa, contexto de segurança) e que entradas idênticas produzam seleções de estratégia idênticas dentro do mesmo contexto de segurança. |   1   |  D/V  |
| 9.10.2 | Verifique se cada estratégia de raciocínio (ReAct, Chain-of-Thought, Tree-of-Thoughts) possui validação de entrada dedicada, sanitização de saída e limites de tempo de execução específicos para a sua abordagem cognitiva.                                     |   1   |  D/V  |
| 9.10.3 | Verifique se as transições da estratégia de raciocínio são registradas com contexto completo, incluindo características de entrada, valores dos critérios de seleção e metadados de execução para a reconstrução da trilha de auditoria.                         |   2   |  D/V  |
| 9.10.4 | Verifique se o raciocínio em Árvore de Pensamentos inclui mecanismos de poda de ramos que interrompem a exploração quando violações de políticas, limites de recursos ou fronteiras de segurança são detectadas.                                                 |   2   |  D/V  |
| 9.10.5 | Verifique se os ciclos ReAct (Reason-Act-Observe) incluem pontos de validação em cada fase: verificação do passo de raciocínio, autorização de ação e sanitização de observação antes de prosseguir.                                                             |   2   |  D/V  |
| 9.10.6 | Verifique se as métricas de desempenho da estratégia de raciocínio (tempo de execução, uso de recursos, qualidade da saída) são monitoradas com alertas automatizados quando as métricas se desviam além dos limiares configurados.                              |   3   |  D/V  |
| 9.10.7 | Verifique se abordagens de raciocínio híbrido que combinam várias estratégias mantêm a validação de entrada e as restrições de saída de todas as estratégias constituintes sem contornar quaisquer controles de segurança.                                       |   3   |  D/V  |
| 9.10.8 | Verifique se os testes de segurança da estratégia de raciocínio incluem fuzzing com entradas malformadas, prompts adversariais projetados para forçar a troca de estratégia e testes de condições de fronteira para cada abordagem cognitiva.                    |   3   |  D/V  |

---

## 9.11 Gerenciamento do Ciclo de Vida do Agente e Segurança

Inicialização segura do agente, transições de estado e terminação com registros de auditoria criptográficos e procedimentos de recuperação definidos.

|   #    | Descrição                                                                                                                                                                                                                                                                                                             | Nível | Papel |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.11.1 | Verifique se a inicialização do agente inclui o estabelecimento de identidade criptográfica com credenciais protegidas por hardware e logs de auditoria de inicialização imutáveis contendo o ID do agente, carimbo de data e hora, hash da configuração e parâmetros de inicialização.                               |   1   |  D/V  |
| 9.11.2 | Verifique se as transições de estado do agente estão assinadas digitalmente, com carimbo de tempo e registradas com contexto completo, incluindo os eventos desencadeadores, o hash do estado anterior, o hash do estado atual e as validações de segurança realizadas.                                               |   2   |  D/V  |
| 9.11.3 | Verifique se os procedimentos de desligamento do agente incluem o apagamento seguro da memória usando eliminação criptográfica ou sobregravação em várias passadas, revogação de credenciais com notificação à autoridade certificadora e geração de certificados de encerramento à prova de adulteração.             |   2   |  D/V  |
| 9.11.4 | Verifique que os mecanismos de recuperação de agentes validam a integridade do estado usando somas de verificação criptográficas (SHA-256 no mínimo) e executam rollback para estados previamente verificados como íntegros quando é detectada corrupção, com alertas automatizados e requisitos de aprovação manual. |   3   |  D/V  |
| 9.11.5 | Verifique se os mecanismos de persistência de agentes criptografam dados de estado sensíveis com chaves AES-256 por agente e implementam rotação de chaves segura em cronogramas configuráveis (máximo de 90 dias) com implantação sem tempo de inatividade.                                                          |   3   |  D/V  |

---

## 9.12 Estrutura de Segurança para Integração de Ferramentas

Controles de segurança para carregamento dinâmico de ferramentas, execução e validação de resultados com avaliação de risco definida e processos de aprovação.

|   #    | Descrição                                                                                                                                                                                                                                                                                    | Nível | Papel |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.12.1 | Verifique se os descritores de ferramenta incluem metadados de segurança que especificam privilégios exigidos (leitura/gravação/execução), níveis de risco (baixo/médio/alto), limites de recursos (CPU, memória, rede) e requisitos de validação documentados nos manifestos da ferramenta. |   1   |  D/V  |
| 9.12.2 | Verifique se os resultados da execução da ferramenta são validados em relação aos esquemas esperados (JSON Schema, XML Schema) e às políticas de segurança (sanitização de saída, classificação de dados) antes da integração com limites de tempo e procedimentos de tratamento de erros.   |   1   |  D/V  |
| 9.12.3 | Verifique se os registros de interação de ferramentas incluem contexto de segurança detalhado, incluindo uso de privilégios, padrões de acesso a dados, tempo de execução, consumo de recursos e códigos de retorno, com registro estruturado para integração com SIEM.                      |   2   |  D/V  |
| 9.12.4 | Verifique se os mecanismos dinâmicos de carregamento de ferramentas validam assinaturas digitais usando a infraestrutura PKI e implemente protocolos de carregamento seguro com isolamento em sandbox e verificação de permissões antes da execução.                                         |   2   |  D/V  |
| 9.12.5 | Verifique que as avaliações de segurança de ferramentas são acionadas automaticamente para novas versões com portas de aprovação obrigatórias, incluindo análise estática, teste dinâmico e revisão pela equipe de segurança, com critérios de aprovação documentados e requisitos de SLA.   |   3   |  D/V  |

---

### Referências

* [MITRE ATLAS tactics ML09](https://atlas.mitre.org/)
* [Circuit-breaker research for AI agents — Zou et al., 2024](https://arxiv.org/abs/2406.04313)
* [Trend Micro analysis of sandbox escapes in AI agents — Park, 2025](https://www.trendmicro.com/vinfo/us/security/news/cybercrime-and-digital-threats/unveiling-ai-agent-vulnerabilities-code-execution)
* [Auth0 guidance on human-in-the-loop authorization for agents — Martinez, 2025](https://auth0.com/blog/secure-human-in-the-loop-interactions-for-ai-agents/)
* [Medium deep-dive on MCP & A2A protocol hijacking — ForAISec, 2025](https://medium.com/%40foraisec/security-analysis-potential-ai-agent-hijacking-via-mcp-and-a2a-protocol-insights-cd1ec5e6045f)
* [Rapid7 fundamentals on spoofing attack prevention — 2024](https://www.rapid7.com/fundamentals/spoofing-attacks/)
* [Imperial College verification of swarm systems — Lomuscio et al.](https://sail.doc.ic.ac.uk/projects/swarms/)
* [NIST AI Risk Management Framework 1.0, 2023](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [WIRED security briefing on encryption best practices, 2024](https://www.wired.com/story/encryption-apps-chinese-telecom-hacking-hydra-russia-exxon)
* [OWASP Top 10 for LLM Applications, 2025](https://owasp.org/www-project-top-10-for-large-language-model-applications/)
* [Comprehensive Vulnerability Analysis is Necessary for Trustworthy LLM-MAS](https://arxiv.org/html/2506.01245v1)
* [How Is LLM Reasoning Distracted by Irrelevant Context?
  An Analysis Using a Controlled Benchmark](https://www.arxiv.org/pdf/2505.18761)
* [Large Language Model Sentinel: LLM Agent for Adversarial Purification](https://arxiv.org/pdf/2405.20770)
* [Securing Agentic AI: A Comprehensive Threat Model and Mitigation Framework for Generative AI Agents](https://arxiv.org/html/2504.19956v2)

