# Segurança de Infraestrutura, Configuração & Implantação C4

## Objetivo de Controle

A infraestrutura de IA deve ser reforçada contra escalonamento de privilégios, adulteração da cadeia de suprimentos e movimento lateral através de configuração segura, isolamento em tempo de execução, pipelines de implantação confiáveis e monitoramento abrangente. Apenas componentes e configurações de infraestrutura autorizados e validados alcançam a produção por meio de processos controlados que mantêm a segurança, integridade e auditoria.

Objetivo central de segurança: Apenas componentes de infraestrutura assinados criptograficamente, escaneados em busca de vulnerabilidades, chegam à produção através de pipelines de validação automatizados que aplicam políticas de segurança e mantêm registros de auditoria imutáveis.

---

## C4.1 Isolamento do Ambiente de Execução

Prevenir escapes de contêineres e escalonamento de privilégios por meio de primitives de isolamento de nível de kernel e controles de acesso obrigatórios.

|   #   | Descrição                                                                                                                                                                                                                                                    | Nível | Papel |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 4.1.1 | Verifique se todos os containers de IA deixam de fora TODAS as capacidades do Linux, exceto CAP_SETUID, CAP_SETGID e capacidades explicitamente necessárias documentadas nas linhas de base de segurança.                                                    |   1   |  D/V  |
| 4.1.2 | Verifique se os perfis seccomp bloqueiam todas as syscalls, exceto aquelas nas listas de permissão pré-aprovadas, com violações que terminam o container e geram alertas de segurança.                                                                       |   1   |  D/V  |
| 4.1.3 | Verifique se as cargas de trabalho de IA são executadas com sistemas de arquivos raiz somente-leitura, tmpfs para dados temporários e volumes nomeados para dados persistentes, sem a aplicação de opções de montagem noexec.                                |   2   |  D/V  |
| 4.1.4 | Verifique se a monitoração em tempo de execução baseada em eBPF (Falco, Tetragon ou equivalente) detecta tentativas de escalonamento de privilégios e mata automaticamente os processos ofensores dentro dos requisitos de tempo de resposta organizacional. |   2   |  D/V  |
| 4.1.5 | Verifique se cargas de trabalho de AI de alto risco são executadas em ambientes isolados de hardware (Intel TXT, AMD SVM ou nós dedicados bare-metal) com verificação de atestação.                                                                          |   3   |  D/V  |

---

## C4.2 Pipelines Seguros de Construção e Implantação

Garanta a integridade criptográfica e a segurança da cadeia de suprimentos por meio de builds reproduzíveis e artefatos assinados.

|   #   | Descrição                                                                                                                                                                                                      | Nível | Papel |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.2.1 | Verifique se a infraestrutura-como-código é analisada com ferramentas (tfsec, Checkov ou Terrascan) em cada commit, bloqueando merges com descobertas de gravidade CRITICAL ou HIGH.                           |   1   |  D/V  |
| 4.2.2 | Verifique se as compilações de contêineres são reproduzíveis com hashes SHA256 idênticos em todas as compilações e gere atestados de proveniência do nível 3 do SLSA assinados com Sigstore.                   |   1   |  D/V  |
| 4.2.3 | Verifique se as imagens de container incorporam CycloneDX ou SPDX SBOMs e são assinadas com Cosign antes do push para o repositório, rejeitando imagens não assinadas na implantação.                          |   2   |  D/V  |
| 4.2.4 | Verifique se os pipelines de CI/CD utilizam tokens OIDC do HashiCorp Vault, AWS IAM Roles ou Azure Managed Identity com tempos de validade que não excedam os limites da política de segurança organizacional. |   2   |  D/V  |
| 4.2.5 | Verifique se as assinaturas Cosign e a proveniência SLSA são validadas durante o processo de implantação antes da execução do container e se erros de verificação fazem com que a implantação falhe.           |   2   |  D/V  |
| 4.2.6 | Verifique se os ambientes de build operam em contêineres efêmeros ou VMs sem armazenamento persistente e isolamento de rede de VPCs de produção.                                                               |   2   |  D/V  |

---

## C4.3 Segurança de Rede & Controle de Acesso

Implemente uma rede de confiança zero com políticas de negação padrão e comunicações criptografadas.

|   #   | Descrição                                                                                                                                                                                       | Nível | Papel |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.3.1 | Verifique se as Kubernetes NetworkPolicies ou qualquer equivalente implementam um deny padrão de entrada/saída com regras de permissão explícitas para as portas necessárias (443, 8080, etc.). |   1   |  D/V  |
| 4.3.2 | Verifique se SSH (porta 22), RDP (porta 3389) e endpoints de metadados em nuvem (169.254.169.254) estão bloqueados ou requerem autenticação baseada em certificado.                             |   1   |  D/V  |
| 4.3.3 | Verifique se o tráfego de saída é filtrado através de proxies HTTP/HTTPS (Squid, Istio ou gateways NAT na nuvem) com listas de domínios permitidos e solicitações bloqueadas registradas.       |   2   |  D/V  |
| 4.3.4 | Verifique se a comunicação entre serviços usa TLS mútuo com certificados rotacionados de acordo com a política organizacional e validação de certificados aplicada (sem flags de skip-verify).  |   2   |  D/V  |
| 4.3.5 | Verifique se a infraestrutura de IA funciona em VPCs/VNets dedicados, sem acesso direto à internet, e se comunica apenas por meio de gateways NAT ou hosts bastião.                             |   2   |  D/V  |

---

## C4.4 Segredos & Gerenciamento de Chaves Criptográficas

Proteja credenciais por meio de armazenamento com suporte de hardware e rotação automatizada com acesso de confiança zero.

|   #   | Descrição                                                                                                                                                                                                          | Nível | Papel |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 4.4.1 | Verifique se os segredos estão armazenados no HashiCorp Vault, AWS Secrets Manager, Azure Key Vault ou Google Secret Manager com criptografia em repouso usando AES-256.                                           |   1   |  D/V  |
| 4.4.2 | Verifique se as chaves criptográficas são geradas em HSMs de Nível 2 do FIPS 140-2 (AWS CloudHSM, Azure Dedicated HSM) com rotação de chaves de acordo com a política criptográfica organizacional.                |   1   |  D/V  |
| 4.4.3 | Verifique se a rotação de segredos é automatizada com implantação de tempo de inatividade zero e rotação imediata ativada por mudanças na equipe ou incidentes de segurança.                                       |   2   |  D/V  |
| 4.4.4 | Verifique se as imagens de container são escaneadas com ferramentas (GitLeaks, TruffleHog ou detect-secrets) impedindo builds que contenham chaves de API, senhas ou certificados.                                 |   2   |  D/V  |
| 4.4.5 | Verifique se o acesso secreto de produção requer MFA com tokens de hardware (YubiKey, FIDO2) e se é registrado por logs de auditoria imutáveis com identidades de usuários e carimbos de data/hora.                |   2   |  D/V  |
| 4.4.6 | Verifique se os segredos são injetados via segredos do Kubernetes, volumes montados ou containers de inicialização e certifique-se de que os segredos nunca estejam embutidos em variáveis de ambiente ou imagens. |   2   |  D/V  |

---

## C4.5 Isolamento de Carga de Trabalho de IA e Validação

Isolar modelos de IA não confiáveis em sandboxes seguros com análise comportamental abrangente.

|   #   | Descrição                                                                                                                                                                                                                       | Nível | Papel |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.5.1 | Verifique se modelos de IA externos são executados em gVisor, microVMs (como Firecracker, CrossVM) ou contêineres Docker com as flags --security-opt=no-new-privileges e --read-only.                                           |   1   |  D/V  |
| 4.5.2 | Verifique se os ambientes sandbox não possuem conectividade de rede (--network=none) ou se têm apenas acesso ao localhost, com todas as solicitações externas bloqueadas por regras do iptables.                                |   1   |  D/V  |
| 4.5.3 | Verifique se a validação do modelo de IA inclui testes automatizados de red-team com cobertura de teste definida pela organização e análise comportamental para detecção de backdoor.                                           |   2   |  D/V  |
| 4.5.4 | Verifique se, antes de um modelo de IA ser promovido para produção, seus resultados no ambiente sandbox são assinados criptograficamente por pessoal de segurança autorizado e armazenados em registros de auditoria imutáveis. |   2   |  D/V  |
| 4.5.5 | Verifique se os ambientes sandbox são destruídos e recriados a partir de imagens de referência entre avaliações, com limpeza completa do sistema de arquivos e da memória.                                                      |   2   |  D/V  |

---

## C4.6 Segurança de Infraestrutura e Monitoramento

Escaneie e monitore continuamente a infraestrutura com remediação automatizada e alertas em tempo real.

|   #   | Descrição                                                                                                                                                                                                            | Nível | Papel |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.6.1 | Verifique se as imagens de container são escaneadas de acordo com os cronogramas organizacionais, com vulnerabilidades CRÍTICAS bloqueando a implantação com base nos limites de risco organizacionais.              |   1   |  D/V  |
| 4.6.2 | Verifique se a infraestrutura atende aos CIS Benchmarks ou aos controles NIST 800-53, com limites de conformidade definidos pela organização e remediação automatizada para verificações que falharem.               |   1   |  D/V  |
| 4.6.3 | Verifique se as vulnerabilidades de severidade ALTA foram corrigidas de acordo com os prazos de gerenciamento de risco organizacional, com procedimentos de emergência para CVEs ativamente explorados.              |   2   |  D/V  |
| 4.6.4 | Verifique se os alertas de segurança integram-se com plataformas SIEM (Splunk, Elastic ou Sentinel) usando os formatos CEF ou STIX/TAXII com enriquecimento automatizado.                                            |   2   |   V   |
| 4.6.5 | Verifique se as métricas de infraestrutura são exportadas para os sistemas de monitoramento (Prometheus, DataDog) com painéis SLA e relatórios executivos.                                                           |   3   |   V   |
| 4.6.6 | Verifique se a deriva de configuração é detectada usando ferramentas (Chef InSpec, AWS Config) de acordo com os requisitos de monitoramento organizacional, com rollback automático para alterações não autorizadas. |   2   |  D/V  |

---

## C4.7 Gerenciamento de Recursos de Infraestrutura de IA

Prevenir ataques de exaustão de recursos e garantir alocação justa de recursos por meio de cotas e monitoramento.

|   #   | Descrição                                                                                                                                                                                                                                            | Nível | Papel |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.7.1 | Verifique se a utilização de GPU/TPU está sendo monitorada com alertas acionados em limiares definidos pela organização e se o dimensionamento automático ou balanceamento de carga é ativado com base nas políticas de gerenciamento de capacidade. |   1   |  D/V  |
| 4.7.2 | Verifique se as métricas de carga de trabalho de IA (latência de inferência, throughput, taxas de erro) estão sendo coletadas de acordo com os requisitos de monitoramento organizacional e correlacionadas com a utilização da infraestrutura.      |   1   |  D/V  |
| 4.7.3 | Verifique se o ResourceQuotas do Kubernetes ou o limite equivalente limita cargas de trabalho individuais de acordo com as políticas de alocação de recursos organizacionais, com limites rígidos aplicados.                                         |   2   |  D/V  |
| 4.7.4 | Verifique se o monitoramento de custos acompanha os gastos por carga de trabalho/inquilino com alertas com base nos limites orçamentários organizacionais e controles automatizados para excessos de orçamento.                                      |   2   |   V   |
| 4.7.5 | Verifique se o planejamento de capacidade usa dados históricos com períodos de previsão definidos pela organização e provisionamento automatizado de recursos com base em padrões de demanda.                                                        |   3   |   V   |
| 4.7.6 | Verifique se o esgotamento de recursos aciona os circuit breakers de acordo com os requisitos de resposta organizacional, incluindo limitação de taxa com base nas políticas de capacidade e isolamento de carga de trabalho.                        |   2   |  D/V  |

---

## C4.8 Separação de Ambiente & Controles de Promoção

Implemente limites rigorosos de ambiente com portas de promoção automatizadas e validação de segurança.

|   #   | Descrição                                                                                                                                                                                                                   | Nível | Papel |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.8.1 | Verifique se os ambientes dev/test/prod estão em VPCs/VNets separados, sem roles IAM compartilhadas, grupos de segurança ou conectividade de rede.                                                                          |   1   |  D/V  |
| 4.8.2 | Verifique se a promoção do ambiente exige aprovação de pessoal autorizado definido pela organização com assinaturas criptográficas e trilhas de auditoria imutáveis.                                                        |   1   |  D/V  |
| 4.8.3 | Verifique se os ambientes de produção bloqueiam o acesso SSH, desativem endpoints de debug e exijam solicitações de mudança com aviso prévio organizacional, exceto em casos de emergência.                                 |   2   |  D/V  |
| 4.8.4 | Verifique se as mudanças na infraestrutura-como-código exigem revisão por pares com testes automatizados e varredura de segurança antes do merge para a branch principal.                                                   |   2   |  D/V  |
| 4.8.5 | Verifique se os dados não utilizados na produção estão anonimizados de acordo com os requisitos de privacidade da organização, geração de dados sintéticos ou mascaramento completo de dados com remoção de PII verificada. |   2   |  D/V  |
| 4.8.6 | Verifique se os portões de promoção incluem testes de segurança automatizados (SAST, DAST, varredura de containers) com zero resultados CRÍTICOS necessários para aprovação.                                                |   2   |  D/V  |

---

## C4.9 Backup e Recuperação de Infraestrutura

Garanta a resiliência da infraestrutura por meio de backups automatizados, procedimentos de recuperação testados e capacidades de recuperação de desastres.

|   #   | Descrição                                                                                                                                                                                                              | Nível | Papel |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.9.1 | Verifique se as configurações de infraestrutura estão sendo respaldadas de acordo com as programações de backup organizacionais em regiões separadas geograficamente, com implementação da estratégia de backup 3-2-1. |   1   |  D/V  |
| 4.9.2 | Verifique se os sistemas de backup funcionam em redes isoladas com credenciais separadas e armazenamento air-gapped para proteção contra ransomware.                                                                   |   2   |  D/V  |
| 4.9.3 | Verifique se os procedimentos de recuperação são testados e validados por meio de testes automatizados de acordo com as escalas organizacionais, com metas de RTO e RPO atendendo aos requisitos organizacionais.      |   2   |   V   |
| 4.9.4 | Verifique se a recuperação de desastres inclui runbooks específicos de IA com restauração de pesos de modelo, reconstrução de cluster GPU e mapeamento de dependência de serviços.                                     |   3   |   V   |

---

## C4.10 Conformidade e Governança de Infraestrutura

Manter a conformidade regulatória por meio de avaliação contínua, documentação e controles automatizados.

|   #    | Descrição                                                                                                                                                                                          | Nível | Papel |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.10.1 | Verifique se a conformidade da infraestrutura é avaliada de acordo com os cronogramas organizacionais contra controles SOC 2, ISO 27001 ou FedRAMP, com coleta automatizada de evidências.         |   2   |  D/V  |
| 4.10.2 | Verifique se a documentação de infraestrutura inclui diagramas de rede, mapas de fluxo de dados e modelos de ameaça atualizados de acordo com os requisitos de gestão de mudanças organizacionais. |   2   |   V   |
| 4.10.3 | Verifique se as mudanças na infraestrutura passam por avaliação automatizada de impacto de conformidade com fluxos de trabalho de aprovação regulatória para modificações de alto risco.           |   3   |  D/V  |

---

## C4.11 Segurança de Hardware de IA

Componentes de hardware específicos de IA seguros, incluindo GPUs, TPUs e aceleradores de IA especializados.

|   #    | Descrição                                                                                                                                                                                                  | Nível | Papel |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.11.1 | Verifique se o firmware do acelerador de IA (GPU BIOS, firmware TPU) é verificado com assinaturas criptográficas e atualizado de acordo com os cronogramas de gerenciamento de patches da organização.     |   2   |  D/V  |
| 4.11.2 | Verifique se, antes da execução da carga de trabalho, a integridade do acelerador de IA é validada por atestação de hardware usando TPM 2.0, Intel TXT ou AMD SVM.                                         |   2   |  D/V  |
| 4.11.3 | Verifique se a memória da GPU está isolada entre cargas de trabalho usando SR-IOV, MIG (GPU de múltiplas instâncias) ou particionamento de hardware equivalente, com sanitização de memória entre tarefas. |   2   |  D/V  |
| 4.11.4 | Verifique se a cadeia de suprimentos de hardware de IA inclui verificação de proveniência com certificados do fabricante e validação de embalagem à prova de violação.                                     |   3   |   V   |
| 4.11.5 | Verifique se os módulos de segurança de hardware (HSMs) protegem os pesos do modelo de IA e as chaves criptográficas com certificação FIPS 140-2 Nível 3 ou Common Criteria EAL4+.                         |   3   |  D/V  |

---

## C4.12 Infraestrutura de IA de Borda e Distribuída

Implantações seguras de IA distribuída, incluindo computação de borda, aprendizado federado e arquiteturas multi-site.

|   #    | Descrição                                                                                                                                                                                                             | Nível | Papel |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.12.1 | Verifique se os dispositivos de edge AI se autenticam na infraestrutura central usando TLS mútua com certificados de dispositivos rotativos de acordo com a política de gerenciamento de certificados organizacional. |   2   |  D/V  |
| 4.12.2 | Verifique se os dispositivos de borda implementam boot seguro com assinaturas verificadas e proteção contra rollback, impedindo ataques de downgrade de firmware.                                                     |   2   |  D/V  |
| 4.12.3 | Verifique se a coordenação distribuída de IA usa algoritmos de consenso à prova de falhas bizantinas com validação de participantes e detecção de nós maliciosos.                                                     |   3   |  D/V  |
| 4.12.4 | Verifique se a comunicação de ponta a nuvem inclui limitação de largura de banda, compactação de dados e capacidades de operação offline com armazenamento local seguro.                                              |   3   |  D/V  |

---

## C4.13 Segurança de Infraestrutura Multi-Cloud e Híbrida

Trabalhos de AI seguros em vários provedores de nuvem e implantações híbridas de nuvem-on-premises.

|   #    | Descrição                                                                                                                                                                                                 | Nível | Papel |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.13.1 | Verifique se as implantações de IA multi-cloud usam federação de identidade independente de nuvem (OIDC, SAML) com gerenciamento de políticas centralizado entre provedores.                              |   2   |  D/V  |
| 4.13.2 | Verifique se a transferência de dados entre nuvens utiliza criptografia de ponta a ponta com chaves gerenciadas pelo cliente e controles de residência de dados aplicados por jurisdição.                 |   2   |  D/V  |
| 4.13.3 | Verifique se as cargas de trabalho de AI em nuvem híbrida implementam políticas de segurança consistentes em ambientes on-premise e na nuvem, com monitoramento e alerta unificados.                      |   2   |  D/V  |
| 4.13.4 | Verifique se a prevenção de lock-in com fornecedores de nuvem inclui infraestrutura como código portátil, APIs padronizadas e capacidades de exportação de dados com ferramentas de conversão de formato. |   3   |   V   |
| 4.13.5 | Verifique se a otimização de custos multi-nuvem inclui controles de segurança que impedem a propagação de recursos, bem como cobranças de transferência de dados não autorizadas entre nuvens.            |   3   |   V   |

---

## C4.14 Automação de Infraestrutura & Segurança GitOps

Automatize pipelines de infraestrutura segura e fluxos de trabalho GitOps para gerenciamento de infraestrutura de IA.

|   #    | Descrição                                                                                                                                                                                                                  | Nível | Papel |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.14.1 | Verifique se os repositórios GitOps exigem commits assinados com chaves GPG e regras de proteção de branch que impedem pushes diretos para branches principais.                                                            |   2   |  D/V  |
| 4.14.2 | Verifique se a automação de infraestrutura inclui detecção de deriva com remediação automática e capacidades de reversão acionadas de acordo com os requisitos de resposta da organização para alterações não autorizadas. |   2   |  D/V  |
| 4.14.3 | Verifique se a provisão automatizada de infraestrutura inclui validação de políticas de segurança com bloqueio de implantação para configurações não conformes.                                                            |   2   |  D/V  |
| 4.14.4 | Verifique se os segredos da automação de infraestrutura são gerenciados por meio de operadores de segredos externos (External Secrets Operator, Bank-Vaults) com rotação automática.                                       |   2   |  D/V  |
| 4.14.5 | Verifique se a infraestrutura auto-curativa inclui correlação de eventos de segurança com fluxos de trabalho automatizados de resposta a incidentes e notificação de partes interessadas.                                  |   3   |   V   |

---

## C4.15 Segurança de Infraestrutura Resistente a Quânticos

Prepare infraestrutura de IA para ameaças de computação quântica por meio de criptografia pós-quântica e protocolos seguros quânticos.

|   #    | Descrição                                                                                                                                                                                              | Nível | Papel |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 4.15.1 | Verifique se a infraestrutura de IA implementa algoritmos criptográficos pós-quânticos aprovados pelo NIST (CRYSTALS-Kyber, CRYSTALS-Dilithium, SPHINCS+) para troca de chaves e assinaturas digitais. |   3   |  D/V  |
| 4.15.2 | Verifique se os sistemas de distribuição de chaves quânticas (QKD) estão implementados para comunicações de IA de alta segurança com protocolos de gerenciamento de chaves quânticas seguras.          |   3   |  D/V  |
| 4.15.3 | Verifique se os frameworks de agilidade criptográfica permitem uma migração rápida para novos algoritmos pós-quânticos com rotação automatizada de certificados e chaves.                              |   3   |  D/V  |
| 4.15.4 | Verifique se a modelagem de ameaças quânticas avalia a vulnerabilidade da infraestrutura de IA a ataques quânticos com cronogramas de migração documentados e avaliações de risco.                     |   3   |   V   |
| 4.15.5 | Verifique se os sistemas criptográficos híbridos clássico-quantum proporcionam defesa em profundidade durante o período de transição quântica com monitoramento de desempenho.                         |   3   |  D/V  |

---

## C4.16 Computação Confidencial & Enclaves Seguros

Proteja as cargas de trabalho de IA e pesos de modelos usando ambientes de execução confiáveis baseados em hardware e tecnologias de computação confidencial.

|   #    | Descrição                                                                                                                                                                         | Nível | Papel |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.16.1 | Verifique se os modelos de IA sensíveis são executados dentro de enclaves Intel SGX, AMD SEV-SNP ou ARM TrustZone, com memória criptografada e verificação de attestation.        |   3   |  D/V  |
| 4.16.2 | Verifique se os containers confidenciais (Kata Containers, gVisor com computação confidencial) isola cargas de trabalho de IA com criptografia de memória reforçada por hardware. |   3   |  D/V  |
| 4.16.3 | Verifique se a attestation remota valida a integridade do enclave antes de carregar modelos de IA com prova criptográfica da autenticidade de um ambiente de execução.            |   3   |  D/V  |
| 4.16.4 | Verifique se os serviços confidenciais de inferência de IA impedem a extração de modelo através de cálculo criptografado com pesos de modelo selados e execução protegida.        |   3   |  D/V  |
| 4.16.5 | Verifique se a orquestração do ambiente de execução confiável gerencia o ciclo de vida do enclave seguro com atestação remota e canais de comunicação criptografados.             |   3   |  D/V  |
| 4.16.6 | Verifique que a computação segura multi-partes (SMPC) permite o treinamento colaborativo de IA sem expor conjuntos de dados individuais ou parâmetros do modelo.                  |   3   |  D/V  |

---

## C4.17 Infraestrutura de Conhecimento Zero

Implemente sistemas de prova de conhecimento zero para verificação e autenticação de IA preservando a privacidade, sem revelar informações sensíveis.

|   #    | Descrição                                                                                                                                                                                            | Nível | Papel |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.17.1 | Verifique que as provas de conhecimento zero (ZK-SNARKs, ZK-STARKs) verificam a integridade do modelo de IA e a proveniência do treinamento sem expor os pesos do modelo ou os dados de treinamento. |   3   |  D/V  |
| 4.17.2 | Verifique se os sistemas de autenticação baseados em ZK permitem a verificação de usuário preservando a privacidade para serviços de IA, sem revelar informações relacionadas à identidade.          |   3   |  D/V  |
| 4.17.3 | Verifique se os protocolos de interseção de conjuntos privados (PSI) permitem a correspondência segura de dados para IA federada sem divulgar conjuntos de dados individuais.                        |   3   |  D/V  |
| 4.17.4 | Verifique que os sistemas de aprendizado de máquina de conhecimento zero (ZKML) permitem inferências de IA verificáveis com prova criptográfica de cálculo correto.                                  |   3   |  D/V  |
| 4.17.5 | Verifique se ZK-rollups fornecem processamento de transações de IA escalável, com preservação da privacidade, por meio de verificação em lote e redução da sobrecarga computacional.                 |   3   |  D/V  |

---

## C4.18 Prevenção de Ataques de Canal Lateral

Proteja a infraestrutura de IA de ataques de canal lateral baseados em tempo, energia, eletromagnetismo e cache que podem vazar informações confidenciais.

|   #    | Descrição                                                                                                                                                                  | Nível | Papel |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.18.1 | Verifique se o tempo de inferência de IA é normalizado usando algoritmos de tempo constante e preenchimento para prevenir ataques de extração de modelo baseados em tempo. |   3   |  D/V  |
| 4.18.2 | Verifique se a proteção contra análise de energia inclui injeção de ruído, filtragem de linha de energia e padrões de execução randomizados para hardware de IA.           |   3   |  D/V  |
| 4.18.3 | Verifique se a mitigação de canais side-baseados em cache usa particionamento de cache, randomização e instruções de limpeza para evitar vazamento de informações.         |   3   |  D/V  |
| 4.18.4 | Verifique se a proteção contra emissão eletromagnética inclui blindagem, filtragem de sinal e processamento aleatório para prevenir ataques no estilo TEMPEST.             |   3   |  D/V  |
| 4.18.5 | Verifique se as defesas de canais side microarquiteturais incluem controles de execução especulativa e ofuscação do padrão de acesso à memória.                            |   3   |  D/V  |

---

## C4.19 Segurança de Hardware Neuromórfico & Especializado em IA

Garanta a segurança das arquiteturas emergentes de hardware de IA, incluindo chips neuromórficos, FPGAs, ASICs personalizados e sistemas de computação óptica.

|   #    | Descrição                                                                                                                                                                                | Nível | Papel |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.19.1 | Verifique se a segurança do chip neuromórfico inclui criptografia de padrões de picos, proteção de peso sináptico e validação de regras de aprendizado baseadas em hardware.             |   3   |  D/V  |
| 4.19.2 | Verifique se aceleradores de IA baseados em FPGA implementam criptografia de bitstream, mecanismos anti-manipulação e carregamento seguro de configuração com atualizações autenticadas. |   3   |  D/V  |
| 4.19.3 | Verifique se a segurança de ASIC personalizada inclui processadores de segurança on-chip, raiz de confiança de hardware e armazenamento seguro de chaves com detecção de violação.       |   3   |  D/V  |
| 4.19.4 | Verifique se os sistemas de computação óptica implementam criptografia óptica quântico-segura, comutação fotônica segura e processamento de sinais ópticos protegido.                    |   3   |  D/V  |
| 4.19.5 | Verifique se os chips de IA híbridos analógico-digital incluem computação analógica segura, armazenamento protegido de pesos e conversão analógica-digital autenticada.                  |   3   |  D/V  |

---

## C4.20 Infraestrutura de Cálculo Preservadora de Privacidade

Implementar controles de infraestrutura para computação que preserva a privacidade e proteger dados sensíveis durante o processamento e análise de IA.

|   #    | Descrição                                                                                                                                                                                                         | Nível | Papel |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.20.1 | Verifique se a infraestrutura de criptografia homomórfica permite o processamento criptografado de cargas de trabalho sensíveis de IA com verificação de integridade criptográfica e monitoramento de desempenho. |   3   |  D/V  |
| 4.20.2 | Verifique se os sistemas de recuperação de informações privadas permitem consultas a banco de dados sem revelar os padrões de consulta, mediante proteção criptográfica dos padrões de acesso.                    |   3   |  D/V  |
| 4.20.3 | Verifique se os protocolos de computação multiparte segura permitem inferência de IA preservando a privacidade, sem expor entradas individuais ou cálculos intermediários.                                        |   3   |  D/V  |
| 4.20.4 | Verifique se a gestão de chaves com privacidade preservada inclui geração distribuída de chaves, criptografia threshold e rotação segura de chaves com proteção suportada por hardware.                           |   3   |  D/V  |
| 4.20.5 | Verifique se o desempenho de computação preservadora da privacidade está otimizado por meio de agrupamento, cache e aceleração de hardware, mantendo as garantias de segurança criptográfica.                     |   3   |  D/V  |

---

## C4.15 Segurança de Integração em Nuvem do Framework de Agentes e Implantação Híbrida

Controles de segurança para frameworks de agentes integrados em nuvem com arquiteturas híbridas on-premises/nuvem.

|   #    | Descrição                                                                                                                                     | Nível | Papel |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.15.1 | Verifique se a integração de armazenamento em nuvem utiliza criptografia de ponta a ponta com gerenciamento de chaves controlado pelo agente. |   1   |  D/V  |
| 4.15.2 | Verifique se os limites de segurança de implantação híbrida estão claramente definidos com canais de comunicação criptografados.              |   2   |  D/V  |
| 4.15.3 | Verifique se o acesso aos recursos em nuvem inclui verificação de confiança zero com autenticação contínua.                                   |   2   |  D/V  |
| 4.15.4 | Verifique se os requisitos de residência de dados são garantidos por atestação criptográfica das localidades de armazenamento.                |   3   |  D/V  |
| 4.15.5 | Verifique se as avaliações de segurança do provedor de cloud incluem modelagem de ameaças específica do agente e avaliação de riscos.         |   3   |  D/V  |

---

## Referências

* [NIST Cybersecurity Framework 2.0](https://www.nist.gov/cyberframework)
* [CIS Controls v8](https://www.cisecurity.org/controls/v8)
* [OWASP Container Security Verification Standard](https://github.com/OWASP/Container-Security-Verification-Standard)
* [Kubernetes Security Best Practices](https://kubernetes.io/docs/concepts/security/)
* [SLSA Supply Chain Security Framework](https://slsa.dev/)
* [NIST SP 800-190: Application Container Security Guide](https://csrc.nist.gov/publications/detail/sp/800-190/final)
* [Cloud Security Alliance: Cloud Controls Matrix](https://cloudsecurityalliance.org/research/cloud-controls-matrix/)
* [ENISA: Secure Infrastructure Design](https://www.enisa.europa.eu/topics/critical-information-infrastructures-and-services)
* [NIST SP 800-53: Security Controls for Federal Information Systems](https://csrc.nist.gov/publications/detail/sp/800-53/rev-5/final)
* [ISO 27001:2022 Information Security Management](https://www.iso.org/standard/27001)
* [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)
* [CIS Kubernetes Benchmark](https://www.cisecurity.org/benchmark/kubernetes)
* [FIPS 140-2 Security Requirements](https://csrc.nist.gov/publications/detail/fips/140/2/final)
* [NIST SP 800-207: Zero Trust Architecture](https://csrc.nist.gov/publications/detail/sp/800-207/final)
* [IEEE 2857: Privacy Engineering for AI Systems](https://standards.ieee.org/ieee/2857/7273/)
* [NIST SP 800-161: Cybersecurity Supply Chain Risk Management](https://csrc.nist.gov/publications/detail/sp/800-161/rev-1/final)
* [NIST Post-Quantum Cryptography Standards](https://csrc.nist.gov/Projects/post-quantum-cryptography)
* [Intel SGX Developer Guide](https://www.intel.com/content/www/us/en/developer/tools/software-guard-extensions/overview.html)
* [AMD SEV-SNP White Paper](https://www.amd.com/system/files/TechDocs/SEV-SNP-strengthening-vm-isolation-with-integrity-protection-and-more.pdf)
* [ARM TrustZone Technology](https://developer.arm.com/ip-products/security-ip/trustzone)
* [ZK-SNARKs: A Gentle Introduction](https://blog.ethereum.org/2016/12/05/zksnarks-in-a-nutshell/)
* [NIST SP 800-57: Cryptographic Key Management](https://csrc.nist.gov/publications/detail/sp/800-57-part-1/rev-5/final)
* [Side-Channel Attack Countermeasures](https://link.springer.com/book/10.1007/978-3-319-75268-6)
* [Neuromorphic Computing Security Challenges](https://ieeexplore.ieee.org/document/9458103)
* [FPGA Security: Fundamentals, Evaluation, and Countermeasures](https://link.springer.com/book/10.1007/978-3-319-90385-9)
* [Microsoft SEAL: Homomorphic Encryption Library](https://github.com/Microsoft/SEAL)
* [HElib: Homomorphic Encryption Library](https://github.com/homenc/HElib)
* [PALISADE Lattice Cryptography Library](https://palisade-crypto.org/)
* [Differential Privacy: A Survey of Results](https://link.springer.com/chapter/10.1007/978-3-540-79228-4_1)
* [Secure Aggregation for Federated Learning](https://eprint.iacr.org/2017/281.pdf)
* [Private Information Retrieval: Concepts and Constructions](https://link.springer.com/book/10.1007/978-3-030-16234-8)

