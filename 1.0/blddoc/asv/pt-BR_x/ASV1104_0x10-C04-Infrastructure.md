# C4 Segurança de Infraestrutura, Configuração e Implantação

## Objetivo de Controle

A infraestrutura de IA deve ser endurecida contra elevação de privilégios, adulteração da cadeia de suprimentos e movimento lateral por meio de configuração segura, isolamento em tempo de execução, pipelines de implantação confiáveis e monitoramento abrangente. Apenas componentes de infraestrutura autorizados e configurações validadas chegam à produção por meio de processos controlados que mantêm a segurança, integridade e auditabilidade.

Objetivo de Segurança Central: Somente componentes de infraestrutura assinados criptograficamente e escaneados em busca de vulnerabilidades chegam à produção por meio de pipelines de validação automatizados que impõem políticas de segurança e mantêm trilhas de auditoria imutáveis.

---

## C4.1 Isolamento do Ambiente de Tempo de Execução

Prevenir fugas de contêineres e elevação de privilégios por meio de primitivas de isolamento em nível de kernel e controles de acesso obrigatórios.

|   #   | Descrição                                                                                                                                                                                                                                                     | Nível | Papel |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.1.1 | Verifique se todos os contêineres de IA descartam ALL as capacidades do Linux, exceto CAP_SETUID, CAP_SETGID e as capacidades explicitamente exigidas documentadas nas bases de segurança.                                                                    |   1   |  D/V  |
| 4.1.2 | Verifique se os perfis seccomp bloqueiam todas as chamadas de sistema, exceto aquelas em listas de permissões pré-aprovadas, com violações encerrando o contêiner e gerando alertas de segurança.                                                             |   1   |  D/V  |
| 4.1.3 | Verifique se as cargas de trabalho de IA são executadas com sistemas de arquivos raiz somente leitura, tmpfs para dados temporários e volumes nomeados para dados persistentes, com as opções de montagem noexec impostas.                                    |   2   |  D/V  |
| 4.1.4 | Verifique se o monitoramento em tempo de execução baseado em eBPF (Falco, Tetragon ou equivalente) detecta tentativas de elevação de privilégios e encerra automaticamente os processos infratores dentro dos requisitos de tempo de resposta da organização. |   2   |  D/V  |
| 4.1.5 | Verifique se as cargas de trabalho de IA de alto risco são executadas em ambientes isolados por hardware (Intel TXT, AMD SVM ou nós bare-metal dedicados) com verificação de atestação.                                                                       |   3   |  D/V  |

---

## C4.2 Pipelines Seguros de Build e Implantação

Garanta a integridade criptográfica e a segurança da cadeia de suprimentos por meio de compilações reprodutíveis e artefatos assinados.

|   #   | Descrição                                                                                                                                                                                                                    | Nível | Papel |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.2.1 | Verifique se a infraestrutura como código é analisada com as ferramentas (tfsec, Checkov ou Terrascan) em cada commit, bloqueando fusões com achados de severidade CRÍTICO ou ALTO.                                          |   1   |  D/V  |
| 4.2.2 | Verifique se as construções de contêineres são reprodutíveis com hashes SHA256 idênticos entre as construções e gere atestados de proveniência do Nível 3 SLSA assinados com Sigstore.                                       |   1   |  D/V  |
| 4.2.3 | Verifique se as imagens de contêiner incluem SBOMs CycloneDX ou SPDX e são assinadas com Cosign antes do envio para o registro, com imagens não assinadas rejeitadas na implantação.                                         |   2   |  D/V  |
| 4.2.4 | Verifique se os pipelines de CI/CD utilizam tokens OIDC do HashiCorp Vault, Funções IAM da AWS ou Identidade Gerenciada do Azure, com tempos de validade que não excedam os limites da política de segurança organizacional. |   2   |  D/V  |
| 4.2.5 | Verifique se as assinaturas do Cosign e a proveniência SLSA são validadas durante o processo de implantação, antes da execução do contêiner, e se os erros de verificação provocam a falha da implantação.                   |   2   |  D/V  |
| 4.2.6 | Verifique se os ambientes de build rodam em contêineres efêmeros ou VMs sem armazenamento persistente e com isolamento de rede em relação às VPCs de produção.                                                               |   2   |  D/V  |

---

## C4.3 Segurança de Rede e Controle de Acesso

Implemente redes de zero-trust com políticas de negação por padrão e comunicações criptografadas.

|   #   | Descrição                                                                                                                                                                                              | Nível | Papel |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 4.3.1 | Verifique se as Políticas de Rede do Kubernetes ou qualquer equivalente implementam negação por padrão de entrada/saída, com regras explícitas de permissão para as portas exigidas (443, 8080, etc.). |   1   |  D/V  |
| 4.3.2 | Verifique se o SSH (porta 22), o RDP (porta 3389) e os endpoints de metadados na nuvem (169.254.169.254) estão bloqueados ou exigem autenticação baseada em certificado.                               |   1   |  D/V  |
| 4.3.3 | Verifique se o tráfego de saída é filtrado por meio de proxies HTTP/HTTPS (Squid, Istio ou gateways NAT na nuvem), com listas de domínios permitidos e com o registro das solicitações bloqueadas.     |   2   |  D/V  |
| 4.3.4 | Verifique se a comunicação entre serviços usa TLS mútuo com certificados rotacionados de acordo com a política organizacional e validação de certificados obrigatória (sem flags skip-verify).         |   2   |  D/V  |
| 4.3.5 | Verifique se a infraestrutura de IA opera em VPCs/VNets dedicadas sem acesso direto à Internet e se comunica apenas por meio de gateways NAT ou hosts bastiões.                                        |   2   |  D/V  |

---

## C4.4 Segredos e Gerenciamento de Chaves Criptográficas

Proteja credenciais por meio de armazenamento com suporte de hardware e rotação automatizada com acesso zero-trust.

|   #   | Descrição                                                                                                                                                                                                                       | Nível | Papel |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.4.1 | Verifique se os segredos estão armazenados no HashiCorp Vault, AWS Secrets Manager, Azure Key Vault ou Google Secret Manager, com criptografia em repouso usando AES-256.                                                       |   1   |  D/V  |
| 4.4.2 | Verifique se as chaves criptográficas são geradas em HSMs de Nível 2 FIPS 140-2 (AWS CloudHSM, Azure Dedicated HSM) com rotação de chaves de acordo com a política criptográfica da organização.                                |   1   |  D/V  |
| 4.4.3 | Verifique se o rotacionamento de segredos está automatizado com implantação sem tempo de inatividade e rotacionamento imediato acionado por mudanças de pessoal ou incidentes de segurança.                                     |   2   |  D/V  |
| 4.4.4 | Verifique se as imagens de contêiner são escaneadas com ferramentas (GitLeaks, TruffleHog ou detect-secrets), bloqueando builds que contenham chaves de API, senhas ou certificados.                                            |   2   |  D/V  |
| 4.4.5 | Verifique se o acesso a segredos de produção requer autenticação multifator (MFA) com tokens de hardware (YubiKey, FIDO2) e se é registrado por logs de auditoria imutáveis com identidades de usuário e carimbos de data/hora. |   2   |  D/V  |
| 4.4.6 | Verifique se os segredos são injetados por meio de segredos do Kubernetes, volumes montados ou contêineres de inicialização e garanta que os segredos nunca estejam incorporados em variáveis de ambiente ou em imagens.        |   2   |  D/V  |

---

## C4.5 Isolamento de Cargas de Trabalho de IA e Validação

Isole modelos de IA não confiáveis em sandboxes seguros com análise comportamental abrangente.

|   #   | Descrição                                                                                                                                                                                                       | Nível | Papel |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.5.1 | Verifique se os modelos de IA externos são executados em gVisor, microVMs (como Firecracker, CrossVM) ou contêineres Docker com as opções --security-opt=no-new-privileges e --read-only.                       |   1   |  D/V  |
| 4.5.2 | Verifique se os ambientes sandbox não possuem conectividade de rede (--network=none) ou apenas acesso ao localhost, com todas as requisições externas bloqueadas por regras do iptables.                        |   1   |  D/V  |
| 4.5.3 | Verifique se a validação do modelo de IA inclui testes automatizados de red team com cobertura de testes definida pela organização e análise comportamental para detecção de portas dos fundos.                 |   2   |  D/V  |
| 4.5.4 | Verifique que, antes de promover um modelo de IA para produção, seus resultados do sandbox sejam assinados criptograficamente por pessoal de segurança autorizado e armazenados em logs de auditoria imutáveis. |   2   |  D/V  |
| 4.5.5 | Verifique se os ambientes sandbox são destruídos e recriados a partir de imagens douradas entre avaliações, com limpeza completa do sistema de arquivos e da memória.                                           |   2   |  D/V  |

---

## C4.6 Monitoramento de Segurança da Infraestrutura

Varredura e monitoramento contínuos da infraestrutura com remediação automatizada e alertas em tempo real.

|   #   | Descrição                                                                                                                                                                                                             | Nível | Papel |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.6.1 | Verifique se as imagens de contêiner são escaneadas de acordo com os cronogramas organizacionais, com vulnerabilidades CRÍTICAS bloqueando a implantação com base nos limiares de risco da organização.               |   1   |  D/V  |
| 4.6.2 | Verifique se a infraestrutura atende aos CIS Benchmarks ou aos controles NIST 800-53, com limiares de conformidade definidos pela organização e remediação automatizada para verificações que falharam.               |   1   |  D/V  |
| 4.6.3 | Verifique se as vulnerabilidades de severidade ALTA são corrigidas de acordo com os cronogramas de gerenciamento de risco da organização, com procedimentos de emergência para CVEs exploradas ativamente.            |   2   |  D/V  |
| 4.6.4 | Verifique se os alertas de segurança se integram às plataformas SIEM (Splunk, Elastic ou Sentinel) usando os formatos CEF ou STIX/TAXII com enriquecimento automatizado.                                              |   2   |   V   |
| 4.6.5 | Verifique se as métricas de infraestrutura são exportadas para os sistemas de monitoramento (Prometheus, DataDog) com painéis de SLA e relatórios executivos.                                                         |   3   |   V   |
| 4.6.6 | Verifique se a deriva de configuração é detectada usando ferramentas (Chef InSpec, AWS Config) de acordo com os requisitos de monitoramento organizacionais, com rollback automático para alterações não autorizadas. |   2   |  D/V  |

---

## C4.7 Gestão de Recursos de Infraestrutura de IA

Prevenir ataques de exaustão de recursos e assegurar uma alocação justa de recursos por meio de cotas e monitoramento.

|   #   | Descrição                                                                                                                                                                                                                                                  | Nível | Papel |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.7.1 | Verifique se a utilização de GPU/TPU está sendo monitorada com alertas acionados em limiares definidos pela organização e se o dimensionamento automático ou o balanceamento de carga estão ativados com base em políticas de gerenciamento de capacidade. |   1   |  D/V  |
| 4.7.2 | Verifique se as métricas de carga de trabalho de IA (latência de inferência, taxa de transferência, taxas de erro) são coletadas de acordo com os requisitos de monitoramento organizacionais e correlacionadas com a utilização da infraestrutura.        |   1   |  D/V  |
| 4.7.3 | Verifique se o Kubernetes ResourceQuotas ou equivalente limitam cargas de trabalho individuais de acordo com as políticas organizacionais de alocação de recursos, com limites rígidos aplicados.                                                          |   2   |  D/V  |
| 4.7.4 | Verifique se o monitoramento de custos acompanha os gastos por carga de trabalho/tenante, com alertas baseados em limites orçamentários organizacionais e controles automatizados para ultrapassagens orçamentárias.                                       |   2   |   V   |
| 4.7.5 | Verifique se o planejamento de capacidade utiliza dados históricos com períodos de previsão definidos pela organização e provisionamento automático de recursos com base em padrões de demanda.                                                            |   3   |   V   |
| 4.7.6 | Verifique se a exaustão de recursos aciona disjuntores de circuito de acordo com os requisitos de resposta organizacionais, incluindo limitação de taxa com base em políticas de capacidade e isolamento de carga de trabalho.                             |   2   |  D/V  |

---

## C4.8 Separação de Ambientes e Controles de Promoção

Impor limites rígidos entre ambientes com portões de promoção automatizados e validação de segurança.

|   #   | Descrição                                                                                                                                                                                                        | Nível | Papel |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.8.1 | Verifique se os ambientes de desenvolvimento, teste e produção rodam em VPCs/VNets separadas, sem funções IAM compartilhadas, grupos de segurança ou conectividade de rede.                                      |   1   |  D/V  |
| 4.8.2 | Verifique se a promoção do ambiente requer aprovação de pessoal autorizado definido pela organização, com assinaturas criptográficas e trilhas de auditoria imutáveis.                                           |   1   |  D/V  |
| 4.8.3 | Verifique se os ambientes de produção bloqueiam o acesso SSH, desativam endpoints de depuração e exigem solicitações de mudança com requisitos de pré-aviso organizacional, exceto em emergências.               |   2   |  D/V  |
| 4.8.4 | Verifique se as mudanças de infraestrutura como código exigem revisão por pares com testes automatizados e varredura de segurança antes de serem mescladas à ramificação principal.                              |   2   |  D/V  |
| 4.8.5 | Verifique se os dados não produtivos estão anonimizados de acordo com os requisitos de privacidade organizacionais, geração de dados sintéticos ou mascaramento completo de dados com remoção de PII verificada. |   2   |  D/V  |
| 4.8.6 | Verifique se os portões de promoção incluem testes de segurança automatizados (SAST, DAST, varredura de contêineres) com zero achados críticos necessários para aprovação.                                       |   2   |  D/V  |

---

## C4.9 Infraestrutura de Backup e Recuperação

Garantir a resiliência da infraestrutura por meio de backups automatizados, procedimentos de recuperação testados e capacidades de recuperação de desastres.

|   #   | Descrição                                                                                                                                                                                                                | Nível | Papel |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 4.9.1 | Verifique se as configurações de infraestrutura são incluídas em backups de acordo com os cronogramas de backup da organização, em regiões geograficamente separadas, com a implementação da estratégia de backup 3-2-1. |   1   |  D/V  |
| 4.9.2 | Verifique se os sistemas de backup operam em redes isoladas com credenciais separadas e armazenamento isolado (air-gapped) para proteção contra ransomware.                                                              |   2   |  D/V  |
| 4.9.3 | Verifique se os procedimentos de recuperação são testados e validados por meio de testes automatizados de acordo com os cronogramas organizacionais, com metas de RTO e RPO que atendam aos requisitos organizacionais.  |   2   |   V   |
| 4.9.4 | Verifique se a recuperação de desastres inclui runbooks específicos de IA com restauração dos pesos do modelo, reconstrução do cluster de GPU e mapeamento de dependências de serviços.                                  |   3   |   V   |

---

## C4.10 Conformidade e Governança da Infraestrutura

Manter a conformidade regulatória por meio de avaliação contínua, documentação e controles automatizados.

|   #    | Descrição                                                                                                                                                                                          | Nível | Papel |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.10.1 | Verifique se a conformidade da infraestrutura é avaliada de acordo com os cronogramas organizacionais em relação aos controles SOC 2, ISO 27001 ou FedRAMP com coleta automatizada de evidências.  |   2   |  D/V  |
| 4.10.2 | Verifique se a documentação de infraestrutura inclui diagramas de rede, mapas de fluxo de dados e modelos de ameaça atualizados de acordo com os requisitos de gestão de mudanças organizacionais. |   2   |   V   |
| 4.10.3 | Verifique se as mudanças de infraestrutura passam por avaliação automatizada de impacto de conformidade com fluxos de aprovação regulatória para modificações de alto risco.                       |   3   |  D/V  |

---

## C4.11 Segurança de hardware de IA

Proteja componentes de hardware específicos para IA, incluindo GPUs, TPUs e aceleradores de IA especializados.

|   #    | Descrição                                                                                                                                                                                               | Nível | Papel |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.11.1 | Verifique se o firmware do acelerador de IA (BIOS de GPU, firmware de TPU) é verificado com assinaturas criptográficas e atualizado de acordo com os prazos de gerenciamento de patches da organização. |   2   |  D/V  |
| 4.11.2 | Verifique se, antes da execução da carga de trabalho, a integridade do acelerador de IA é validada por atestado de hardware usando TPM 2.0, Intel TXT ou AMD SVM.                                       |   2   |  D/V  |
| 4.11.3 | Verifique se a memória da GPU está isolada entre cargas de trabalho usando SR-IOV, MIG (Multi-Instance GPU) ou particionamento de hardware equivalente com sanitização de memória entre trabalhos.      |   2   |  D/V  |
| 4.11.4 | Verifique se a cadeia de suprimentos de hardware de IA inclui verificação de proveniência com certificados do fabricante e validação de embalagem à prova de violação.                                  |   3   |   V   |
| 4.11.5 | Verifique se os módulos de segurança de hardware (HSMs) protegem os pesos do modelo de IA e as chaves criptográficas com certificação FIPS 140-2 Nível 3 ou Common Criteria EAL4+.                      |   3   |  D/V  |

---

## C4.12 Infraestrutura de IA de borda e distribuída

Implantações seguras de IA distribuída, incluindo computação de borda, aprendizado federado e arquiteturas multi-site.

|   #    | Descrição                                                                                                                                                                                                                     | Nível | Papel |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.12.1 | Verifique que os dispositivos de IA de borda se autenticam na infraestrutura central usando TLS mútuo, com certificados de dispositivo rotacionados de acordo com a política de gerenciamento de certificados da organização. |   2   |  D/V  |
| 4.12.2 | Verifique se os dispositivos de borda implementam inicialização segura com assinaturas verificadas e proteção contra rollback que previne ataques de downgrade de firmware.                                                   |   2   |  D/V  |
| 4.12.3 | Verifique se a coordenação distribuída de IA utiliza algoritmos de consenso tolerantes a falhas bizantinas com validação de participantes e detecção de nós maliciosos.                                                       |   3   |  D/V  |
| 4.12.4 | Verifique se a comunicação edge-to-cloud inclui limitação de largura de banda, compressão de dados e capacidades de operação offline com armazenamento local seguro.                                                          |   3   |  D/V  |

---

## C4.13 Segurança de Infraestrutura Multi-Cloud e Híbrida

Proteja cargas de trabalho de IA em múltiplos provedores de nuvem e em implantações híbridas de nuvem e no local.

|   #    | Descrição                                                                                                                                                                                                    | Nível | Papel |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 4.13.1 | Verifique se as implantações de IA em multi-cloud utilizam federação de identidade independente de nuvem (OIDC, SAML) com gerenciamento centralizado de políticas entre provedores.                          |   2   |  D/V  |
| 4.13.2 | Verifique se a transferência de dados entre nuvens utiliza criptografia de ponta a ponta com chaves gerenciadas pelo cliente e controles de residência de dados aplicados conforme a jurisdição.             |   2   |  D/V  |
| 4.13.3 | Verifique se as cargas de trabalho de IA em nuvem híbrida implementam políticas de segurança consistentes entre ambientes no local e em nuvem, com monitoramento e alertas unificados.                       |   2   |  D/V  |
| 4.13.4 | Verifique se a prevenção do bloqueio do fornecedor de nuvem inclui infraestrutura como código portátil, APIs padronizadas e capacidades de exportação de dados com ferramentas de conversão de formatos.     |   3   |   V   |
| 4.13.5 | Verifique se a otimização de custos em ambientes multicloud inclui controles de segurança que impeçam o espalhamento de recursos, bem como cobranças de transferência de dados entre nuvens não autorizadas. |   3   |   V   |

---

## C4.14 Automação de Infraestrutura e Segurança do GitOps

Pipelines de automação de infraestrutura e fluxos de trabalho GitOps seguros para o gerenciamento de infraestrutura de IA.

|   #    | Descrição                                                                                                                                                                                                                  | Nível | Papel |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.14.1 | Verifique se os repositórios GitOps exigem commits assinados com chaves GPG e regras de proteção de ramificações que impeçam envios diretos para os ramos principais.                                                      |   2   |  D/V  |
| 4.14.2 | Verifique se a automação de infraestrutura inclui detecção de deriva com remediação automática e capacidades de rollback acionadas de acordo com os requisitos de resposta da organização para alterações não autorizadas. |   2   |  D/V  |
| 4.14.3 | Verifique se o provisionamento automatizado de infraestrutura inclui a validação de políticas de segurança com bloqueio de implantação para configurações não conformes.                                                   |   2   |  D/V  |
| 4.14.4 | Verifique se os segredos da automação de infraestrutura são gerenciados por meio de operadores de segredos externos (External Secrets Operator, Bank-Vaults) com rotação automática.                                       |   2   |  D/V  |
| 4.14.5 | Verifique se a infraestrutura autorreparável inclui correlação de eventos de segurança com resposta a incidentes automatizada e fluxos de notificação às partes interessadas.                                              |   3   |   V   |

---

## C4.15 Segurança de Infraestrutura Quantum-Resistant

Prepare a infraestrutura de IA para enfrentar as ameaças da computação quântica por meio de criptografia pós-quântica e de protocolos à prova de quânticos.

|   #    | Descrição                                                                                                                                                                                                | Nível | Papel |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.15.1 | Verifique se a infraestrutura de IA implementa algoritmos criptográficos pós-quânticos aprovados pelo NIST (CRYSTALS-Kyber, CRYSTALS-Dilithium, SPHINCS+) para troca de chaves e assinaturas digitais.   |   3   |  D/V  |
| 4.15.2 | Verifique se os sistemas de distribuição de chaves quânticas (QKD) estão implementados para comunicações de IA de alta segurança com protocolos de gerenciamento de chaves à prova de ataques quânticos. |   3   |  D/V  |
| 4.15.3 | Verifique se os frameworks de agilidade criptográfica permitem a migração rápida para novos algoritmos pós-quânticos com rotação automática de certificados e chaves.                                    |   3   |  D/V  |
| 4.15.4 | Verifique se a modelagem de ameaças quânticas avalia a vulnerabilidade da infraestrutura de IA a ataques quânticos, com cronogramas de migração documentados e avaliações de risco.                      |   3   |   V   |
| 4.15.5 | Verifique se os sistemas criptográficos híbridos clássico-quânticos fornecem defesa em profundidade durante o período de transição quântica com monitoramento de desempenho.                             |   3   |  D/V  |

---

## C4.16 Computação Confidencial e Enclaves Seguros

Proteja as cargas de trabalho de IA e os pesos do modelo usando ambientes de execução confiáveis baseados em hardware e tecnologias de computação confidencial.

|   #    | Descrição                                                                                                                                                                         | Nível | Papel |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.16.1 | Verifique se modelos sensíveis de IA são executados dentro de enclaves Intel SGX, AMD SEV-SNP ou ARM TrustZone, com memória criptografada e verificação de atestação.             |   3   |  D/V  |
| 4.16.2 | Verifique se contêineres confidenciais (Kata Containers, gVisor com computação confidencial) isolam cargas de trabalho de IA com criptografia de memória fornecida pelo hardware. |   3   |  D/V  |
| 4.16.3 | Verifique se a atestação remota valida a integridade do enclave antes de carregar modelos de IA com uma prova criptográfica da autenticidade de um ambiente de execução.          |   3   |  D/V  |
| 4.16.4 | Verifique se os serviços de inferência de IA confidenciais impedem a extração de modelos por meio de computação criptografada com pesos do modelo selados e execução protegida.   |   3   |  D/V  |
| 4.16.5 | Verifique se a orquestração do ambiente de execução confiável gerencia o ciclo de vida do enclave seguro com atestado remoto e canais de comunicação criptografados.              |   3   |  D/V  |
| 4.16.6 | Verifique se a computação multipartidária segura (SMPC) permite treinamento colaborativo de IA sem expor conjuntos de dados individuais ou parâmetros do modelo.                  |   3   |  D/V  |

---

## C4.17 Infraestrutura de Zero-Knowledge

Implemente sistemas de provas de conhecimento zero para a verificação e autenticação da IA, preservando a privacidade, sem revelar informações sensíveis.

|   #    | Descrição                                                                                                                                                                                                                  | Nível | Papel |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.17.1 | Verifique se as provas de conhecimento zero (ZK-SNARKs, ZK-STARKs) verificam a integridade do modelo de IA e a proveniência do treinamento sem expor os pesos do modelo ou os dados de treinamento.                        |   3   |  D/V  |
| 4.17.2 | Verifique se os sistemas de autenticação baseados em provas de conhecimento zero permitem a verificação de usuários com preservação da privacidade para serviços de IA, sem revelar informações relacionadas à identidade. |   3   |  D/V  |
| 4.17.3 | Verifique se os protocolos de interseção de conjuntos privados (PSI) permitem a correspondência segura de dados para IA federada, sem expor conjuntos de dados individuais.                                                |   3   |  D/V  |
| 4.17.4 | Verifique que os sistemas de aprendizado de máquina com conhecimento zero (ZKML) permitem inferências de IA verificáveis com prova criptográfica da execução correta.                                                      |   3   |  D/V  |
| 4.17.5 | Verifique se os ZK-rollups fornecem processamento de transações de IA escalável, com preservação da privacidade, verificação em lote e menor sobrecarga computacional.                                                     |   3   |  D/V  |

---

## C4.18 Prevenção de Ataques de Canal Lateral

Proteja a infraestrutura de IA contra ataques de canal lateral baseados em temporização, consumo de energia, eletromagnetismo e cache que poderiam vazar informações sensíveis.

|   #    | Descrição                                                                                                                                                                 | Nível | Papel |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.18.1 | Verifique se o tempo de inferência de IA é normalizado usando algoritmos de tempo constante e preenchimento para evitar ataques de extração de modelo baseados no tempo.  |   3   |  D/V  |
| 4.18.2 | Verifique se a proteção contra análise de potência inclui injeção de ruído, filtragem da linha de alimentação e padrões de execução aleatórios para hardware de IA.       |   3   |  D/V  |
| 4.18.3 | Verifique se a mitigação baseada em cache de canais laterais utiliza particionamento de cache, randomização e instruções de flush para evitar o vazamento de informações. |   3   |  D/V  |
| 4.18.4 | Verifique se a proteção contra emanações eletromagnéticas inclui blindagem, filtragem de sinais e processamento randômico para impedir ataques TEMPEST-style.            |   3   |  D/V  |
| 4.18.5 | Verifique se as defesas contra canais laterais microarquiteturais incluem controles de execução especulativa e ofuscação dos padrões de acesso à memória.                 |   3   |  D/V  |

---

## C4.19 Segurança de Hardware de IA Neuromórfica e Especializada

Garantir arquiteturas de hardware de IA emergentes, incluindo chips neuromórficos, FPGAs, ASICs personalizados e sistemas de computação óptica.

|   #    | Descrição                                                                                                                                                                                        | Nível | Papel |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 4.19.1 | Verifique se a segurança do chip neuromórfico inclui criptografia de padrões de disparo, proteção de pesos sinápticos e validação de regras de aprendizado baseadas em hardware.                 |   3   |  D/V  |
| 4.19.2 | Verifique se os aceleradores de IA baseados em FPGA implementam criptografia do bitstream, mecanismos anti-manipulação e carregamento seguro de configuração com atualizações autenticadas.      |   3   |  D/V  |
| 4.19.3 | Verifique se a segurança do ASIC personalizado inclui processadores de segurança integrados no chip, raiz de confiança de hardware e armazenamento seguro de chaves com detecção de adulteração. |   3   |  D/V  |
| 4.19.4 | Verifique se os sistemas de computação óptica implementam criptografia óptica resistente a computadores quânticos, comutação fotônica segura e processamento de sinal óptico protegido.          |   3   |  D/V  |
| 4.19.5 | Verifique se os chips híbridos analógico-digitais de IA incluem computação analógica segura, armazenamento seguro de pesos e conversão analógica-digital autenticada.                            |   3   |  D/V  |

---

## C4.20 Infraestrutura de Computação com Privacidade

Implemente controles de infraestrutura para computação com preservação de privacidade, a fim de proteger dados sensíveis durante o processamento e a análise de IA.

|   #    | Descrição                                                                                                                                                                                                     | Nível | Papel |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.20.1 | Verifique se a infraestrutura de criptografia homomórfica permite computação criptografada em cargas de trabalho sensíveis de IA, com verificação de integridade criptográfica e monitoramento de desempenho. |   3   |  D/V  |
| 4.20.2 | Verifique se os sistemas de recuperação de informações privadas (PIR) permitem consultas a bancos de dados sem revelar padrões de consulta, com proteção criptográfica dos padrões de acesso.                 |   3   |  D/V  |
| 4.20.3 | Verifique se os protocolos de computação multipartidária segura permitem inferência de IA com preservação da privacidade, sem expor entradas individuais ou cálculos intermediários.                          |   3   |  D/V  |
| 4.20.4 | Verifique se a gestão de chaves com preservação da privacidade inclui geração distribuída de chaves, criptografia de limiar e rotação segura de chaves com proteção baseada em hardware.                      |   3   |  D/V  |
| 4.20.5 | Verifique se o desempenho de computação com privacidade preservada é otimizado por meio de processamento em lote, cache e aceleração de hardware, mantendo as garantias de segurança criptográfica.           |   3   |  D/V  |

---

## C4.15 Framework de Agente Integração em Nuvem Segurança e Implantação Híbrida

Controles de segurança para frameworks de agentes integrados à nuvem com arquiteturas híbridas locais/nuvem.

|   #    | Descrição                                                                                                                                     | Nível | Papel |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.15.1 | Verifique se a integração de armazenamento em nuvem utiliza criptografia de ponta a ponta com gerenciamento de chaves controlado pelo agente. |   1   |  D/V  |
| 4.15.2 | Verifique se as fronteiras de segurança da implantação híbrida estão claramente definidas com canais de comunicação criptografados.           |   2   |  D/V  |
| 4.15.3 | Verifique se o acesso aos recursos em nuvem inclui verificação de zero-trust com autenticação contínua.                                       |   2   |  D/V  |
| 4.15.4 | Verifique se os requisitos de residência de dados são aplicados por meio de atestação criptográfica dos locais de armazenamento.              |   3   |  D/V  |
| 4.15.5 | Verifique se as avaliações de segurança do provedor de nuvem incluem modelagem de ameaças específica para o agente e avaliação de risco.      |   3   |  D/V  |

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

