# 9 Orquestração Autônoma e Segurança de Ação Agentiva

## Objetivo de Controle

Garanta que sistemas de IA autônomos ou de múltiplos agentes possam executar apenas ações que sejam explicitamente pretendidas, autenticadas, auditáveis e dentro de limites de custo e risco definidos. Isso protege contra ameaças como Comprometimento de Sistemas Autônomos, Uso Indevido de Ferramentas, Detecção de Loop de Agentes, Interceptação de Comunicações, Suplantação de Identidade, Manipulação de Enxame e Manipulação de Intenções.

---

## 9.1 Planejamento-de-Tarefas do Agente & Orçamentos de Recursão

Limite planos recursivos e imponha pontos de verificação humanos para ações com privilégios.

|   #   | Descrição                                                                                                                                                                                          | Nível | Papel |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.1.1 | Verifique se a profundidade máxima de recursão, a largura, o tempo de parede, tokens e o custo monetário por execução de agente estão centralizados e sob controle de versão.                      |   1   |  D/V  |
| 9.1.2 | Verifique se ações privilegiadas ou irreversíveis (por exemplo, commits de código, transferências financeiras) exigem aprovação humana explícita por meio de um canal auditável antes da execução. |   1   |  D/V  |
| 9.1.3 | Verifique se os monitores de recursos em tempo real acionam a interrupção do circuit-breaker quando qualquer limite de orçamento for excedido, interrompendo a expansão adicional de tarefas.      |   2   |   D   |
| 9.1.4 | Verifique se os eventos de circuit-breaker são registrados com o ID do agente, a condição de disparo e o estado do plano capturado para revisão forense.                                           |   2   |  D/V  |
| 9.1.5 | Verifique se os testes de segurança abrangem cenários de esgotamento de orçamento e de plano fora de controle, confirmando a parada segura sem perda de dados.                                     |   3   |   V   |
| 9.1.6 | Verifique se as políticas orçamentárias são expressas como policy-as-code e são aplicadas no CI/CD para impedir a deriva de configuração.                                                          |   3   |   D   |

---

## 9.2 Isolamento de Plug-ins de Ferramentas

Isole as interações com as ferramentas para evitar acesso não autorizado ao sistema ou à execução de código.

|   #   | Descrição                                                                                                                                                                                      | Nível | Papel |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.2.1 | Verifique que cada ferramenta/plug-in opere dentro de um sandbox em nível de OS, contêiner ou WASM, com políticas de privilégio mínimo para o sistema de arquivos, rede e chamadas de sistema. |   1   |  D/V  |
| 9.2.2 | Verifique se as cotas do sandbox (CPU, memória, disco, saída de rede) e os limites de tempo de execução estão sendo aplicados e registrados.                                                   |   1   |  D/V  |
| 9.2.3 | Verifique se os binários da ferramenta ou descritores estão assinados digitalmente; as assinaturas são validadas antes do carregamento.                                                        |   2   |  D/V  |
| 9.2.4 | Verifique se a telemetria do sandbox é transmitida para um SIEM; anomalias (por exemplo, tentativas de conexões de saída) geram alertas.                                                       |   2   |   V   |
| 9.2.5 | Verifique se plugins de alto risco passam por revisão de segurança e testes de penetração antes da implantação em produção.                                                                    |   3   |   V   |
| 9.2.6 | Verifique se as tentativas de evasão do sandbox são bloqueadas automaticamente e se o plugin infrator é colocado em quarentena enquanto a investigação estiver pendente.                       |   3   |  D/V  |

---

## 9.3 Laço Autônomo & Limite de Custos

Detectar e parar a recursão agente-para-agente descontrolada e explosões de custo.

|   #   | Descrição                                                                                                                                                            | Nível | Papel |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.3.1 | Verifique se as chamadas entre agentes incluem um hop-limit ou TTL, que é decrementado e imposto pelo tempo de execução.                                             |   1   |  D/V  |
| 9.3.2 | Verifique se os agentes mantêm um identificador único do grafo de invocação para detectar auto-invocação ou padrões cíclicos.                                        |   2   |   D   |
| 9.3.3 | Verifique se os contadores cumulativos de unidades de computação e de gasto são rastreados por cadeia de solicitações; ao ultrapassar o limite, a cadeia é abortada. |   2   |  D/V  |
| 9.3.4 | Verifique se a análise formal ou a verificação de modelos demonstra a ausência de recursão ilimitada nos protocolos de agentes.                                      |   3   |   V   |
| 9.3.5 | Verifique se eventos de interrupção de loop geram alertas e alimentam métricas de melhoria-contínua.                                                                 |   3   |   D   |

---

## 9.4 Proteção contra uso indevido em nível de protocolo

Canais de comunicação seguros entre agentes e sistemas externos para evitar o sequestro ou a manipulação.

|   #   | Descrição                                                                                                                                                       | Nível | Papel |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.4.1 | Verifique se todas as mensagens agente-para-ferramenta e agente-para-agente são autenticadas (por exemplo, TLS mútuo ou JWT) e criptografadas de ponta a ponta. |   1   |  D/V  |
| 9.4.2 | Verifique se os esquemas são validados estritamente; campos desconhecidos ou mensagens malformadas são rejeitados.                                              |   1   |   D   |
| 9.4.3 | Verifique se as verificações de integridade (MACs ou assinaturas digitais) cobrem a carga útil inteira da mensagem, incluindo os parâmetros da ferramenta.      |   2   |  D/V  |
| 9.4.4 | Verifique se a proteção contra replay (nonces ou janelas de carimbo de tempo) é implementada na camada de protocolo.                                            |   2   |   D   |
| 9.4.5 | Verifique se as implementações de protocolo passam por fuzzing e análise estática para falhas de injeção ou deserialização.                                     |   3   |   V   |

---

## 9.5 Identidade do Agente e Prova de Adulteração

Certifique-se de que as ações sejam atribuíveis e que as modificações sejam detectáveis.

|   #   | Descrição                                                                                                                                   | Nível | Papel |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.5.1 | Verifique se cada instância de agente possui uma identidade criptográfica única (par de chaves ou credencial enraizada no hardware).        |   1   |  D/V  |
| 9.5.2 | Verifique se todas as ações dos agentes estão assinadas e com carimbo de data/hora; os registros incluem a assinatura para não repúdio.     |   2   |  D/V  |
| 9.5.3 | Verifique se os logs à prova de adulteração são armazenados em um meio de apenas acréscimo (append-only) ou de gravação única (write-once). |   2   |   V   |
| 9.5.4 | Verifique se as chaves de identidade são rotacionadas de acordo com um cronograma definido e com base em indicadores de comprometimento.    |   3   |   D   |
| 9.5.5 | Verifique se tentativas de spoofing ou de conflito de chaves acionam a quarentena imediata do agente afetado.                               |   3   |  D/V  |

---

## 9.6 Redução de Risco de Enxame de Múltiplos Agentes

Mitigar os riscos de comportamento coletivo por meio do isolamento e da modelagem formal de segurança.

|   #   | Descrição                                                                                                                                                          | Nível | Papel |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 9.6.1 | Verifique se os agentes que operam em diferentes domínios de segurança são executados em sandboxes de tempo de execução isolados ou em segmentos de rede isolados. |   1   |  D/V  |
| 9.6.2 | Verifique se os comportamentos de enxames são modelados e verificados formalmente quanto à vivacidade e à segurança antes da implantação.                          |   3   |   V   |
| 9.6.3 | Verifique se os monitores em tempo de execução detectam padrões inseguros emergentes (por exemplo, oscilações, interbloqueios) e iniciam ações corretivas.         |   3   |   D   |

---

## 9.7 Autenticação de Usuário e Ferramenta / Autorização

Implemente controles de acesso robustos para cada ação disparada por um agente.

|   #   | Descrição                                                                                                                                                | Nível | Papel |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.7.1 | Verifique se os agentes se autenticam como entidades de primeira classe em sistemas a jusante, nunca reutilizando credenciais de usuário final.          |   1   |  D/V  |
| 9.7.2 | Verifique se as políticas de autorização de granularidade fina restringem quais ferramentas um agente pode invocar e quais parâmetros ele pode fornecer. |   2   |   D   |
| 9.7.3 | Verifique se as verificações de privilégios são reavaliadas a cada chamada (autorização contínua), e não apenas no início da sessão.                     |   2   |   V   |
| 9.7.4 | Verifique se os privilégios delegados expiram automaticamente e exigem novo consentimento após o tempo limite ou alteração do escopo.                    |   3   |   D   |

---

## 9.8 Segurança de Comunicação entre Agentes

Criptografe e proteja a integridade de todas as mensagens entre agentes para impedir a interceptação e a adulteração.

|   #   | Descrição                                                                                                                                                 | Nível | Papel |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.8.1 | Verifique se a autenticação mútua e a criptografia com Perfect Forward Secrecy (PFS) (por exemplo TLS 1.3) são obrigatórias para canais de agentes.       |   1   |  D/V  |
| 9.8.2 | Verifique se a integridade da mensagem e a origem são validadas antes do processamento; falhas geram alertas e a mensagem é descartada.                   |   1   |   D   |
| 9.8.3 | Verifique se os metadados de comunicação (carimbos de data/hora, números de sequência) são registrados para apoiar a reconstrução forense.                |   2   |  D/V  |
| 9.8.4 | Verifique se a verificação formal ou a verificação por modelo confirma que as máquinas de estados do protocolo não podem ser levadas a estados inseguros. |   3   |   V   |

---

## 9.9 Verificação de Intenção e Aplicação de Restrições

Verifique se as ações do agente estão alinhadas com a intenção declarada pelo usuário e com as restrições do sistema.

|   #   | Descrição                                                                                                                                                                                              | Nível | Papel |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 9.9.1 | Verifique se os solucionadores de restrições de pré-execução verificam as ações propostas em relação às regras de segurança e às políticas codificadas.                                                |   1   |   D   |
| 9.9.2 | Verifique se ações de alto impacto (financeiras, destrutivas, sensíveis à privacidade) exigem confirmação explícita de intenção por parte do usuário que as iniciou.                                   |   2   |  D/V  |
| 9.9.3 | Verifique se as verificações de pós-condição validam que as ações concluídas atingiram os efeitos pretendidos sem efeitos colaterais; discrepâncias acionam rollback.                                  |   2   |   V   |
| 9.9.4 | Verifique se métodos formais (por exemplo, verificação de modelos, prova de teoremas) ou testes baseados em propriedades demonstram que os planos do agente satisfazem todas as restrições declaradas. |   3   |   V   |
| 9.9.5 | Verifique que incidentes de intent-mismatch ou constraint-violation alimentem ciclos de melhoria-contínua e compartilhamento de threat-intel.                                                          |   3   |   D   |

---

## 9.10 Segurança da Estratégia de Raciocínio do Agente

Seleção e execução seguras de diferentes estratégias de raciocínio, incluindo ReAct, Chain-of-Thought e Tree-of-Thoughts.

|   #    | Descrição                                                                                                                                                                                                                                                  | Nível | Papel |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.10.1 | Verifique se a seleção da estratégia de raciocínio usa critérios determinísticos (complexidade de entrada, tipo de tarefa, contexto de segurança) e se entradas idênticas produzem seleções de estratégia idênticas dentro do mesmo contexto de segurança. |   1   |  D/V  |
| 9.10.2 | Verifique se cada estratégia de raciocínio (ReAct, Chain-of-Thought, Tree-of-Thoughts) possui validação de entrada dedicada, sanitização de saída e limites de tempo de execução específicos para a sua abordagem cognitiva.                               |   1   |  D/V  |
| 9.10.3 | Verifique que as transições entre estratégias de raciocínio são registradas com contexto completo, incluindo características de entrada, valores dos critérios de seleção e metadados de execução para a reconstrução da trilha de auditoria.              |   2   |  D/V  |
| 9.10.4 | Verifique se o raciocínio Tree-of-Thoughts inclui mecanismos de poda de ramos que encerram a exploração quando violações de políticas, limites de recursos ou fronteiras de segurança são detectadas.                                                      |   2   |  D/V  |
| 9.10.5 | Verifique se os ciclos ReAct (Reason-Act-Observe) incluem pontos de validação em cada fase: verificação dos passos de raciocínio, autorização de ações e sanitização das observações antes de prosseguir.                                                  |   2   |  D/V  |
| 9.10.6 | Verifique se as métricas de desempenho da estratégia de raciocínio (tempo de execução, uso de recursos, qualidade da saída) são monitoradas com alertas automatizados quando as métricas ultrapassam os limites configurados.                              |   3   |  D/V  |
| 9.10.7 | Verifique se abordagens de raciocínio híbrido que combinam várias estratégias mantêm a validação de entrada e as restrições de saída de todas as estratégias constituintes, sem burlar nenhum controle de segurança.                                       |   3   |  D/V  |
| 9.10.8 | Verifique se os testes de segurança das estratégias de raciocínio incluem fuzzing com entradas malformadas, prompts adversários projetados para forçar a troca de estratégia e testes de condições de fronteira para cada abordagem cognitiva.             |   3   |  D/V  |

---

## 9.11 Gerenciamento do Estado do Ciclo de Vida do Agente e Segurança

Inicialização segura do agente, transições de estado e término com trilhas de auditoria criptográficas e procedimentos de recuperação definidos.

|   #    | Descrição                                                                                                                                                                                                                                                                                             | Nível | Papel |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.11.1 | Verifique se a inicialização do agente inclui o estabelecimento de identidade criptográfica com credenciais protegidas por hardware e logs de auditoria de inicialização imutáveis contendo o ID do agente, carimbo de data/hora, hash de configuração e parâmetros de inicialização.                 |   1   |  D/V  |
| 9.11.2 | Verifique se as transições de estado do agente são assinadas criptograficamente, com carimbo de data/hora e registradas com contexto completo, incluindo eventos acionadores, hash do estado anterior, hash do estado novo e as validações de segurança realizadas.                                   |   2   |  D/V  |
| 9.11.3 | Verifique se os procedimentos de desligamento do agente incluem limpeza segura da memória usando apagamento criptográfico ou sobrescrita em várias passagens, revogação de credenciais com notificação à autoridade de certificação e geração de certificados de encerramento à prova de adulteração. |   2   |  D/V  |
| 9.11.4 | Verifique se os mecanismos de recuperação de agentes validam a integridade do estado usando somas criptográficas (SHA-256 no mínimo) e realizam rollback para estados conhecidos como bons quando a corrupção é detectada, com alertas automatizados e requisitos de aprovação manual.                |   3   |  D/V  |
| 9.11.5 | Verifique se os mecanismos de persistência de agentes criptografam dados de estado sensíveis com chaves AES-256 por agente e implementam rotação de chaves segura em cronogramas configuráveis (máximo de 90 dias) com implantação sem tempo de inatividade.                                          |   3   |  D/V  |

---

## 9.12 Estrutura de Segurança para Integração de Ferramentas

Controles de segurança para carregamento dinâmico de ferramentas, execução e validação de resultados com processos de avaliação de risco e aprovação definidos.

|   #    | Descrição                                                                                                                                                                                                                                                                                    | Nível | Papel |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.12.1 | Verifique se os descritores de ferramentas incluem metadados de segurança que especificam privilégios exigidos (ler/gravar/executar), níveis de risco (baixo/médio/alto), limites de recursos (CPU, memória, rede) e requisitos de validação documentados em manifests de ferramentas.       |   1   |  D/V  |
| 9.12.2 | Verifique se os resultados da execução da ferramenta são validados em relação aos esquemas esperados (JSON Schema, XML Schema) e às políticas de segurança (sanitização de saída, classificação de dados) antes da integração com limites de tempo e procedimentos de tratamento de erros.   |   1   |  D/V  |
| 9.12.3 | Verifique se os registros de interação das ferramentas incluem contexto de segurança detalhado, incluindo uso de privilégios, padrões de acesso a dados, tempo de execução, consumo de recursos e códigos de retorno, com registro estruturado para integração com SIEM.                     |   2   |  D/V  |
| 9.12.4 | Verifique se os mecanismos de carregamento dinâmico de ferramentas validam assinaturas digitais usando infraestrutura PKI e implemente protocolos de carregamento seguros com isolamento em sandbox e verificação de permissões antes da execução.                                           |   2   |  D/V  |
| 9.12.5 | Verifique se as avaliações de segurança de ferramentas são acionadas automaticamente para novas versões, com portas de aprovação obrigatórias, incluindo análise estática, testes dinâmicos e revisão pela equipe de segurança, com critérios de aprovação documentados e requisitos de SLA. |   3   |  D/V  |

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

