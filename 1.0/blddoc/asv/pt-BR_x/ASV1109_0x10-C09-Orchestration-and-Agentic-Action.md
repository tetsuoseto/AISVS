# 9 Segurança de Orquestração Autônoma e Ação Agente

## Objetivo de Controle

Assegure-se de que sistemas de IA autônomos ou multi-agente possam executar apenas ações explicitamente desejadas, autenticadas, auditáveis e dentro de limites de custo e risco definidos. Isso protege contra ameaças como Comprometimento de Sistemas Autônomos, Uso Indevido de Ferramentas, Detecção de Loop de Agente, Sequestro de Comunicação, Falsificação de Identidade, Manipulação de Enxame e Manipulação de Intenção.

---

## 9.1 Planejamento de Tarefas do Agente e Orçamentos de Recursão

Restringir planos recursivos e forçar pontos de verificação humanos para ações privilegiadas.

|   #   | Descrição                                                                                                                                                                                             | Nível | Papel |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.1.1 | Verifique se a profundidade máxima de recursão, largura, tempo wall-clock, tokens e custo monetário por execução do agente estão configurados de forma centralizada e sob controle de versão.         |   1   |  D/V  |
| 9.1.2 | Verifique se ações privilegiadas ou irreversíveis (por exemplo, commits de código, transferências financeiras) requerem aprovação explícita humana através de um canal auditorável antes da execução. |   1   |  D/V  |
| 9.1.3 | Verifique se os monitores de recursos em tempo real acionam a interrupção do circuito-breaker quando qualquer limite de orçamento é excedido, interrompendo a expansão adicional da tarefa.           |   2   |   D   |
| 9.1.4 | Verifique se os eventos do disjuntor estão registrados com ID do agente, condição de acionamento e estado do plano capturado para revisão forense.                                                    |   2   |  D/V  |
| 9.1.5 | Verifique se os testes de segurança cobrem os cenários de esgotamento de orçamento e plano de fuga, confirmando a parada segura sem perda de dados.                                                   |   3   |   V   |
| 9.1.6 | Verifique se as políticas orçamentárias estão expressas como política-como-código e aplicadas em CI/CD para bloquear a deriva de configuração.                                                        |   3   |   D   |

---

## 9.2 sandboxing de plugins de ferramentas

Isole as interações das ferramentas para impedir acesso não autorizado ao sistema ou execução de código.

|   #   | Descrição                                                                                                                                                                                          | Nível | Papel |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.2.1 | Verifique se cada ferramenta/plugin é executada dentro de uma sandbox de nível OS, container ou WASM, com políticas de privilégios mínimos para o sistema de arquivos, rede e chamadas do sistema. |   1   |  D/V  |
| 9.2.2 | Verifique se as quotas de recursos do sandbox (CPU, memória, disco, saída de rede) e os tempos limite de execução estão sendo aplicados e registrados.                                             |   1   |  D/V  |
| 9.2.3 | Verifique se os binários ou descritores da ferramenta estão assinados digitalmente; as assinaturas são validadas antes do carregamento.                                                            |   2   |  D/V  |
| 9.2.4 | Verifique se os fluxos de telemetria do sandbox são enviados para um SIEM; anomalias (por exemplo, tentativas de conexões de saída) geram alertas.                                                 |   2   |   V   |
| 9.2.5 | Verifique se plugins de alto risco passam por revisão de segurança e testes de penetração antes da implantação em produção.                                                                        |   3   |   V   |
| 9.2.6 | Verifique se as tentativas de escape do sandbox são automaticamente bloqueadas e o plugin suspeito é colocado em quarentena aguardando investigação.                                               |   3   |  D/V  |

---

## 9.3 Laço Autônomo e Limitação de Custo

Detectar e interromper a recursão descontrolada de agentes para agentes e explosões de custo.

|   #   | Descrição                                                                                                                                                        | Nível | Papel |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.3.1 | Verifique se as chamadas entre agentes incluem um limite de saltos ou TTL que o tempo de execução decrementa e aplica.                                           |   1   |  D/V  |
| 9.3.2 | Verifique se os agentes mantêm um ID de gráfico de invocação exclusivo para identificar auto-invocações ou padrões cíclicos.                                     |   2   |   D   |
| 9.3.3 | Verifique se os contadores de unidades de computação acumuladas e gastos estão sendo monitorados por cadeia de requisição; ultrapassar o limite aborta a cadeia. |   2   |  D/V  |
| 9.3.4 | Verifique se a análise formal ou a verificação de modelos demonstra a ausência de recursão não limitada em protocolos de agentes.                                |   3   |   V   |
| 9.3.5 | Verifique se eventos de aborto de loop geram alertas e alimentam métricas de melhoria contínua.                                                                  |   3   |   D   |

---

## 9.4 Proteção contra Uso Indevido a Nível de Protocolo

Canais de comunicação seguros entre agentes e sistemas externos para evitar sequestro ou manipulação.

|   #   | Descrição                                                                                                                                                               | Nível | Papel |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.4.1 | Verifique se todas as mensagens de agente para ferramenta e de agente para agente estão autenticadas (por exemplo, TLS mútuo ou JWT) e criptografadas de ponta a ponta. |   1   |  D/V  |
| 9.4.2 | Verifique se os esquemas são estritamente validados; campos desconhecidos ou mensagens malformadas são rejeitados.                                                      |   1   |   D   |
| 9.4.3 | Verifique se as verificações de integridade (MACs ou assinaturas digitais) cobrem toda a carga da mensagem, incluindo os parâmetros da ferramenta.                      |   2   |  D/V  |
| 9.4.4 | Verifique se a proteção contra replay (nonces ou janelas de timestamps) é aplicada na camada de protocolo.                                                              |   2   |   D   |
| 9.4.5 | Verifique se as implementações de protocolo passam por fuzzing e análise estática para detectar falhas de injeção ou desserialização.                                   |   3   |   V   |

---

## 9.5 Identidade do Agente e Evidência de Manipulação

Garanta que as ações sejam atribuíveis e as modificações detectáveis.

|   #   | Descrição                                                                                                                           | Nível | Papel |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.5.1 | Verifique se cada instância de agente possui uma identidade criptográfica única (par de chaves ou credencial baseada em hardware).  |   1   |  D/V  |
| 9.5.2 | Verifique se todas as ações do agente estão assinadas e marcadas com data/hora; os registros incluem a assinatura para não repúdio. |   2   |  D/V  |
| 9.5.3 | Verifique se os registros à prova de adulteração estão armazenados em um meio de gravação somente adição ou de gravação única.      |   2   |   V   |
| 9.5.4 | Verifique se as chaves de identidade são rotacionadas em uma programação definida e com indicadores de comprometimento.             |   3   |   D   |
| 9.5.5 | Verifique se tentativas de spoofing ou conflito de chaves acionam a quarentena imediata do agente afetado.                          |   3   |  D/V  |

---

## 9.6 Redução de Risco por Enxame Multi-Agente

Mitigue os riscos de comportamento coletivo por meio de isolamento e modelagem formal de segurança.

|   #   | Descrição                                                                                                                                              | Nível | Papel |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 9.6.1 | Verifique se os agentes que operam em diferentes domínios de segurança são executados em sandboxes de tempo de execução isolados ou segmentos de rede. |   1   |  D/V  |
| 9.6.2 | Verifique se os comportamentos de enxame são modelados e verificados formalmente quanto à vivacidade e segurança antes da implantação.                 |   3   |   V   |
| 9.6.3 | Verifique se os monitores de tempo de execução detectam padrões inseguro emergentes (por exemplo, oscilações, impasses) e iniciam ações corretivas.    |   3   |   D   |

---

## 9.7 Autenticação / Autorização de Usuário & Ferramenta

Implemente controles de acesso robustos para cada ação acionada pelo agente.

|   #   | Descrição                                                                                                                                                | Nível | Papel |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.7.1 | Verifique se os agentes se autenticam como principais de primeira classe em sistemas downstream, nunca reutilizando credenciais de usuários finais.      |   1   |  D/V  |
| 9.7.2 | Verifique se as políticas de autorização de granularidade fina restringem quais ferramentas um agente pode invocar e quais parâmetros ele pode fornecer. |   2   |   D   |
| 9.7.3 | Verifique se as verificações de privilégio são reavaliadas a cada chamada (autorização contínua), não apenas no início da sessão.                        |   2   |   V   |
| 9.7.4 | Verifique se os privilégios delegados expiram automaticamente e requerem nova consentimento após o tempo limite ou alteração do escopo.                  |   3   |   D   |

---

## 9.8 Segurança na Comunicação entre Agentes

Criptografe e proteja a integridade de todas as mensagens entre agentes para impedir espionagem e adulteração.

|   #   | Descrição                                                                                                                                                  | Nível | Papel |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.8.1 | Verifique se a autenticação mútua e a criptografia com segredo perfeito-avançado (por exemplo, TLS 1.3) são obrigatórias para canais de agente.            |   1   |  D/V  |
| 9.8.2 | Verifique se a integridade e a origem da mensagem são validadas antes do processamento; falhas geram alertas e descartam a mensagem.                       |   1   |   D   |
| 9.8.3 | Verifique se os metadados de comunicação (carimbos de data/hora, números de sequência) estão registrados para apoiar a reconstrução forense.               |   2   |  D/V  |
| 9.8.4 | Verifique se a verificação formal ou a verificação de modelos confirma que máquinas de estado do protocolo não podem ser acionadas para estados inseguros. |   3   |   V   |

---

## 9.9 Verificação de Intenção e Aplicação de Restrições

Verifique se as ações do agente estão alinhadas com a intenção declarada do usuário e as restrições do sistema.

|   #   | Descrição                                                                                                                                                                                             | Nível | Papel |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.9.1 | Verifique se os solucionadores de restrições de pré-execução verificam as ações propostas contra regras de segurança e políticas codificadas.                                                         |   1   |   D   |
| 9.9.2 | Verifique se ações de alto impacto (financeiras, destrutivas, sensíveis à privacidade) requerem confirmação explícita de intenção do usuário que as iniciou.                                          |   2   |  D/V  |
| 9.9.3 | Verifique se as verificações de condição pós-condição validam que as ações concluídas alcançaram os efeitos desejados sem efeitos colaterais; discrepâncias acionam rollback.                         |   2   |   V   |
| 9.9.4 | Verifique se métodos formais (por exemplo, verificação de modelos, prova de teoremas) ou testes baseados em propriedades demonstram que os planos do agente atendem a todas as restrições declaradas. |   3   |   V   |
| 9.9.5 | Verifique se incidentes de incompatibilidade de intenção ou violação de restrições alimentam ciclos de melhoria contínua e compartilhamento de inteligência de ameaças.                               |   3   |   D   |

---

## 9.10 Estratégia de Raciocínio do Agente Segurança

Seleção segura e execução de diferentes estratégias de raciocínio, incluindo abordagens ReAct, Chain-of-Thought e Tree-of-Thoughts.

|   #    | Descrição                                                                                                                                                                                                                                                  | Nível | Papel |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.10.1 | Verifique se a seleção da estratégia de raciocínio usa critérios determinísticos (complexidade da entrada, tipo de tarefa, contexto de segurança) e se entradas idênticas produzem seleções de estratégia idênticas dentro do mesmo contexto de segurança. |   1   |  D/V  |
| 9.10.2 | Verifique se cada estratégia de raciocínio (ReAct, Chain-of-Thought, Tree-of-Thoughts) possui validação de entrada dedicada, sanitização de saída e limites de tempo de execução específicos para sua abordagem cognitiva.                                 |   1   |  D/V  |
| 9.10.3 | Verifique se as transições de estratégia de raciocínio estão registradas com contexto completo, incluindo características de entrada, valores dos critérios de seleção e metadados de execução para reconstrução do rastro de auditoria.                   |   2   |  D/V  |
| 9.10.4 | Verifique se o raciocínio Tree-of-Thoughts inclui mecanismos de poda de ramos que encerram a exploração quando violações de política, limites de recursos ou fronteiras de segurança são detectados.                                                       |   2   |  D/V  |
| 9.10.5 | Verifique se os ciclos ReAct (Razão-Ação-Observação) incluem pontos de verificação de validação em cada fase: verificação do passo de raciocínio, autorização da ação e sanitização da observação antes de prosseguir.                                     |   2   |  D/V  |
| 9.10.6 | Verifique se as métricas de desempenho da estratégia de raciocínio (tempo de execução, uso de recursos, qualidade da saída) estão sendo monitoradas com alertas automáticos quando as métricas desviam-se além dos limites configurados.                   |   3   |  D/V  |
| 9.10.7 | Verifique se as abordagens de raciocínio híbrido que combinam múltiplas estratégias mantêm a validação de entrada e as restrições de saída de todas as estratégias constituintes, sem contornar nenhum controle de segurança.                              |   3   |  D/V  |
| 9.10.8 | Verifique se os testes de segurança da estratégia de raciocínio incluem fuzzing com entradas malformadas, prompts adversariais projetados para forçar a troca de estratégia e testes de condições de limite para cada abordagem cognitiva.                 |   3   |  D/V  |

---

## 9.11 Gestão do Estado do Ciclo de Vida do Agente e Segurança

Inicialização do agente seguro, transições de estado e terminação com trilhas de auditoria criptográficas e procedimentos de recuperação definidos.

|   #    | Descrição                                                                                                                                                                                                                                                                                    | Nível | Papel |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.11.1 | Verifique se a inicialização do agente inclui o estabelecimento de identidade criptográfica com credenciais apoiadas por hardware e registros de auditoria de inicialização imutáveis contendo ID do agente, carimbo de data/hora, hash de configuração e parâmetros de inicialização.       |   1   |  D/V  |
| 9.11.2 | Verifique se as transições de estado do agente são assinadas criptograficamente, timestamped e registradas com o contexto completo, incluindo eventos desencadeadores, hash do estado anterior, hash do novo estado e validações de segurança realizadas.                                    |   2   |  D/V  |
| 9.11.3 | Verifique se os procedimentos de desligamento do agente incluem a limpeza segura de memória usando eliminação criptográfica ou sobrescrição múltipla, revogação de credenciais com notificação da autoridade certificadora e geração de certificados de encerramento à prova de adulteração. |   2   |  D/V  |
| 9.11.4 | Verifique se os mecanismos de recuperação de agentes validam a integridade do estado usando somas de verificação criptográficas (SHA-256 no mínimo) e retornam a estados conhecidos como bons quando a corrupção é detectada, com alertas automáticos e requisitos de aprovação manual.      |   3   |  D/V  |
| 9.11.5 | Verifique se os mecanismos de persistência do agente criptografam dados sensíveis de estado com chaves AES-256 por agente e implementam rotação segura de chaves em cronogramas configuráveis (máximo de 90 dias) com implantação sem tempo de inatividade.                                  |   3   |  D/V  |

---

## 9.12 Estrutura de Segurança na Integração de Ferramentas

Controles de segurança para carregamento dinâmico de ferramentas, execução e validação de resultados com processos definidos de avaliação de risco e aprovação.

|   #    | Descrição                                                                                                                                                                                                                                                                                               | Nível | Papel |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.12.1 | Verifique se os descritores de ferramenta incluem metadados de segurança especificando privilégios necessários (leitura/gravação/executar), níveis de risco (baixo/médio/alto), limites de recursos (CPU, memória, rede) e requisitos de validação documentados nos manifestos da ferramenta.           |   1   |  D/V  |
| 9.12.2 | Verifique se os resultados da execução da ferramenta são validados em relação aos esquemas esperados (JSON Schema, XML Schema) e às políticas de segurança (sanitização de saída, classificação de dados) antes da integração, com limites de tempo de execução e procedimentos de tratamento de erros. |   1   |  D/V  |
| 9.12.3 | Verifique se os registros de interação da ferramenta incluem um contexto de segurança detalhado, incluindo uso de privilégios, padrões de acesso a dados, tempo de execução, consumo de recursos e códigos de retorno, com registros estruturados para integração com SIEM.                             |   2   |  D/V  |
| 9.12.4 | Verifique se os mecanismos de carregamento dinâmico de ferramentas validam assinaturas digitais usando infraestrutura PKI e implemente protocolos de carregamento seguros com isolamento sandbox e verificação de permissões antes da execução.                                                         |   2   |  D/V  |
| 9.12.5 | Verifique se as avaliações de segurança das ferramentas são acionadas automaticamente para novas versões, incluindo portas de aprovação obrigatórias, análise estática, testes dinâmicos e revisão da equipe de segurança, com critérios de aprovação documentados e requisitos de SLA.                 |   3   |  D/V  |

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

