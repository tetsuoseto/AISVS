# Infraestrutura C4, Configuração e Segurança de Implantação

## Objetivo de Controle

A infraestrutura de IA deve ser reforçada contra escalonamento de privilégios, adulteração da cadeia de suprimentos e movimentação lateral por meio de configuração segura, isolamento em tempo de execução, pipelines de implantação confiáveis e monitoramento abrangente. Apenas componentes e configurações da infraestrutura autorizados e validados chegam à produção por meio de processos controlados que mantêm a segurança, integridade e auditabilidade.

Objetivo Principal de Segurança: Apenas componentes de infraestrutura assinados criptograficamente e verificados quanto a vulnerabilidades chegam à produção por meio de pipelines de validação automatizados que aplicam políticas de segurança e mantêm trilhas de auditoria imutáveis.

---

## C4.1 Isolamento do Ambiente de Execução

Evite fugas de contêiner e escalonamento de privilégios por meio de primitivas de isolamento em nível de kernel e controles de acesso obrigatórios.

|   #   | Descrição                                                                                                                                                                                                                                                   | Nível | Função |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :----: |
| 4.1.1 | Verifique se todos os contêineres de IA removem TODAS as capacidades do Linux, exceto CAP_SETUID, CAP_SETGID e as capacidades explicitamente requeridas documentadas nas linhas de base de segurança.                                                       |   1   |  D/V   |
| 4.1.2 | Verifique se os perfis seccomp bloqueiam todas as syscalls, exceto aquelas nas listas de permissões pré-aprovadas, com violações terminando o contêiner e gerando alertas de segurança.                                                                     |   1   |  D/V   |
| 4.1.3 | Verifique se as cargas de trabalho de IA são executadas com sistemas de arquivos raiz somente leitura, tmpfs para dados temporários e volumes nomeados para dados persistentes com opções de montagem noexec aplicadas.                                     |   2   |  D/V   |
| 4.1.4 | Verifique se o monitoramento em tempo real baseado em eBPF (Falco, Tetragon ou equivalente) detecta tentativas de escalonamento de privilégios e encerra automaticamente os processos infratores dentro dos requisitos de tempo de resposta organizacional. |   2   |  D/V   |
| 4.1.5 | Verifique se as cargas de trabalho de IA de alto risco são executadas em ambientes isolados por hardware (Intel TXT, AMD SVM ou nós bare-metal dedicados) com verificação de atestado.                                                                      |   3   |  D/V   |

---

## C4.2 Pipelines Seguros de Build e Deployment

Garanta a integridade criptográfica e a segurança da cadeia de suprimentos por meio de builds reproduzíveis e artefatos assinados.

|   #   | Descrição                                                                                                                                                                                                           | Nível | Função |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :----: |
| 4.2.1 | Verifique se a infraestrutura como código é analisada com ferramentas (tfsec, Checkov ou Terrascan) a cada commit, bloqueando merges que contenham achados de severidade CRÍTICA ou ALTA.                           |   1   |  D/V   |
| 4.2.2 | Verifique se as construções de contêiner são reproduzíveis com hashes SHA256 idênticos entre as construções e gere atestações de proveniência no Nível 3 SLSA assinadas com Sigstore.                               |   1   |  D/V   |
| 4.2.3 | Verifique se as imagens de contêiner incorporam SBOMs CycloneDX ou SPDX e são assinadas com Cosign antes do push para o registro, rejeitando imagens não assinadas na implantação.                                  |   2   |  D/V   |
| 4.2.4 | Verifique se os pipelines de CI/CD usam tokens OIDC do HashiCorp Vault, funções IAM da AWS ou Identidade Gerenciada do Azure com tempos de vida que não excedam os limites da política de segurança organizacional. |   2   |  D/V   |
| 4.2.5 | Verifique se as assinaturas Cosign e a proveniência SLSA são validadas durante o processo de implantação antes da execução do contêiner e se erros de verificação fazem a implantação falhar.                       |   2   |  D/V   |
| 4.2.6 | Verifique se os ambientes de build são executados em contêineres efêmeros ou VMs sem armazenamento persistente e com isolamento de rede em relação às VPCs de produção.                                             |   2   |  D/V   |

---

## C4.3 Segurança de Rede e Controle de Acesso

Implemente redes de confiança zero com políticas de negação padrão e comunicações criptografadas.

|   #   | Descrição                                                                                                                                                                                                                               | Nível | Função |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :----: |
| 4.3.1 | Verifique se as NetworkPolicies do Kubernetes ou qualquer equivalente implementam a política padrão de negar (default-deny) o tráfego de entrada/saída com regras de permissão explícitas para as portas necessárias (443, 8080, etc.). |   1   |  D/V   |
| 4.3.2 | Verifique se SSH (porta 22), RDP (porta 3389) e os endpoints de metadados da nuvem (169.254.169.254) estão bloqueados ou exigem autenticação baseada em certificado.                                                                    |   1   |  D/V   |
| 4.3.3 | Verifique se o tráfego de saída é filtrado através de proxies HTTP/HTTPS (Squid, Istio ou gateways NAT em nuvem) com listas de permissão de domínios e se as solicitações bloqueadas são registradas.                                   |   2   |  D/V   |
| 4.3.4 | Verifique se a comunicação entre serviços utiliza TLS mútuo com certificados rotacionados de acordo com a política organizacional e validação de certificados aplicada (sem uso de flags de ignorar-verificação).                       |   2   |  D/V   |
| 4.3.5 | Verifique se a infraestrutura de IA opera em VPCs/VNets dedicadas sem acesso direto à internet e se comunica apenas por meio de gateways NAT ou hosts bastião.                                                                          |   2   |  D/V   |

---

## C4.4 Gestão de Segredos e Chaves Criptográficas

Proteja as credenciais por meio de armazenamento suportado por hardware e rotação automatizada com acesso de confiança zero.

|   #   | Descrição                                                                                                                                                                                               | Nível | Função |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :----: |
| 4.4.1 | Verifique se os segredos estão armazenados no HashiCorp Vault, AWS Secrets Manager, Azure Key Vault ou Google Secret Manager com criptografia em repouso usando AES-256.                                |   1   |  D/V   |
| 4.4.2 | Verifique se as chaves criptográficas são geradas em HSMs de Nível 2 FIPS 140-2 (AWS CloudHSM, Azure Dedicated HSM) com rotação de chaves de acordo com a política criptográfica organizacional.        |   1   |  D/V   |
| 4.4.3 | Verifique se a rotação de segredos é automatizada com implantação sem tempo de inatividade e rotação imediata acionada por mudanças de pessoal ou incidentes de segurança.                              |   2   |  D/V   |
| 4.4.4 | Verifique se as imagens de contêiner são verificadas com ferramentas (GitLeaks, TruffleHog ou detect-secrets), bloqueando builds que contenham chaves de API, senhas ou certificados.                   |   2   |  D/V   |
| 4.4.5 | Verifique se o acesso ao segredo de produção requer MFA com tokens de hardware (YubiKey, FIDO2) e é registrado por logs de auditoria imutáveis com identidades de usuários e carimbos de data/hora.     |   2   |  D/V   |
| 4.4.6 | Verifique se os segredos são injetados por meio de segredos do Kubernetes, volumes montados ou containers init e assegure que os segredos nunca sejam incorporados em variáveis de ambiente ou imagens. |   2   |  D/V   |

---

## C4.5 Sandboxing e Validação de Carga de Trabalho de IA

Isole modelos de IA não confiáveis em ambientes seguros com análise comportamental abrangente.

|   #   | Descrição                                                                                                                                                                                                         | Nível | Função |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :----: |
| 4.5.1 | Verifique se os modelos de IA externos são executados em gVisor, microVMs (como Firecracker, CrossVM) ou contêineres Docker com as opções --security-opt=no-new-privileges e --read-only.                         |   1   |  D/V   |
| 4.5.2 | Verifique se os ambientes sandbox não possuem conectividade de rede (--network=none) ou possuem apenas acesso ao localhost, com todas as solicitações externas bloqueadas pelas regras do iptables.               |   1   |  D/V   |
| 4.5.3 | Verifique se a validação do modelo de IA inclui testes automatizados de red team com cobertura de teste definida pela organização e análise comportamental para detecção de backdoors.                            |   2   |  D/V   |
| 4.5.4 | Verifique se, antes de um modelo de IA ser promovido para produção, seus resultados na sandbox são assinados criptograficamente por pessoal de segurança autorizado e armazenados em logs de auditoria imutáveis. |   2   |  D/V   |
| 4.5.5 | Verifique se os ambientes sandbox são destruídos e recriados a partir de imagens base entre as avaliações, com limpeza completa do sistema de arquivos e da memória.                                              |   2   |  D/V   |

---

## C4.6 Monitoramento de Segurança da Infraestrutura

Realize a varredura e monitoramento contínuos da infraestrutura com remediação automatizada e alertas em tempo real.

|   #   | Descrição                                                                                                                                                                                                            | Nível | Função |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :----: |
| 4.6.1 | Verifique se as imagens de contêiner são analisadas de acordo com os cronogramas organizacionais, com vulnerabilidades CRÍTICAS bloqueando a implantação com base nos limites de risco organizacionais.              |   1   |  D/V   |
| 4.6.2 | Verifique se a infraestrutura atende aos CIS Benchmarks ou controles NIST 800-53 com limites de conformidade definidos pela organização e remediação automatizada para verificações que falharem.                    |   1   |  D/V   |
| 4.6.3 | Verifique se as vulnerabilidades de gravidade ALTA estão corrigidas conforme os prazos de gerenciamento de risco organizacional, com procedimentos de emergência para CVEs ativamente explorados.                    |   2   |  D/V   |
| 4.6.4 | Verifique se os alertas de segurança se integram com plataformas SIEM (Splunk, Elastic ou Sentinel) usando os formatos CEF ou STIX/TAXII com enriquecimento automatizado.                                            |   2   |   V    |
| 4.6.5 | Verifique se as métricas da infraestrutura são exportadas para sistemas de monitoramento (Prometheus, DataDog) com painéis SLA e relatórios executivos.                                                              |   3   |   V    |
| 4.6.6 | Verifique se o desvio de configuração é detectado usando ferramentas (Chef InSpec, AWS Config) de acordo com os requisitos de monitoramento da organização, com rollback automático para alterações não autorizadas. |   2   |  D/V   |

---

## C4.7 Gerenciamento de Recursos da Infraestrutura de IA

Prevenir ataques de exaustão de recursos e garantir a alocação justa de recursos por meio de cotas e monitoramento.

|   #   | Descrição                                                                                                                                                                                                                                          | Nível | Função |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :----: |
| 4.7.1 | Verifique se a utilização de GPU/TPU é monitorada com alertas acionados em limiares definidos pela organização e se o escalonamento automático ou balanceamento de carga é ativado com base nas políticas de gerenciamento de capacidade.          |   1   |  D/V   |
| 4.7.2 | Verifique se as métricas de carga de trabalho de IA (latência de inferência, taxa de transferência, taxas de erro) são coletadas de acordo com os requisitos de monitoramento organizacional e correlacionadas com a utilização da infraestrutura. |   1   |  D/V   |
| 4.7.3 | Verifique se os ResourceQuotas do Kubernetes ou equivalente limitam cargas de trabalho individuais de acordo com as políticas organizacionais de alocação de recursos, com limites rígidos aplicados.                                              |   2   |  D/V   |
| 4.7.4 | Verifique se o monitoramento de custos acompanha os gastos por carga de trabalho/locatário com alertas baseados em limites orçamentários organizacionais e controles automáticos para excedentes de orçamento.                                     |   2   |   V    |
| 4.7.5 | Verifique se o planejamento de capacidade utiliza dados históricos com períodos de previsão definidos pela organização e provisionamento automático de recursos com base nos padrões de demanda.                                                   |   3   |   V    |
| 4.7.6 | Verifique se o esgotamento de recursos aciona os disjuntores de acordo com os requisitos de resposta organizacional, incluindo limitação de taxa baseada em políticas de capacidade e isolamento de carga de trabalho.                             |   2   |  D/V   |

---

## C4.8 Separação de Ambiente e Controles de Promoção

Implemente limites rigorosos no ambiente com portas de promoção automatizadas e validação de segurança.

|   #   | Descrição                                                                                                                                                                                                             | Nível | Função |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :----: |
| 4.8.1 | Verifique se os ambientes de desenvolvimento/teste/produção estão operando em VPCs/VNets separadas, sem funções IAM, grupos de segurança ou conectividade de rede compartilhados.                                     |   1   |  D/V   |
| 4.8.2 | Verifique se a promoção do ambiente requer aprovação de pessoal autorizado definido pela organização com assinaturas criptográficas e trilhas de auditoria imutáveis.                                                 |   1   |  D/V   |
| 4.8.3 | Verifique se os ambientes de produção bloqueiam o acesso SSH, desabilitam pontos de extremidade de depuração e exigem solicitações de alteração com requisitos de aviso prévio organizacional, exceto em emergências. |   2   |  D/V   |
| 4.8.4 | Verifique se as alterações de infraestrutura-como-código exigem revisão por pares com testes automatizados e varredura de segurança antes da fusão para o branch principal.                                           |   2   |  D/V   |
| 4.8.5 | Verifique se os dados não produtivos estão anonimizados de acordo com os requisitos organizacionais de privacidade, geração de dados sintéticos ou mascaramento completo de dados com remoção de PII verificada.      |   2   |  D/V   |
| 4.8.6 | Verifique se os portões de promoção incluem testes de segurança automatizados (SAST, DAST, varredura de contêiner) com zero achados CRÍTICOS exigidos para aprovação.                                                 |   2   |  D/V   |

---

## C4.9 Backup e Recuperação da Infraestrutura

Garanta a resiliência da infraestrutura por meio de backups automatizados, procedimentos de recuperação testados e capacidades de recuperação de desastres.

|   #   | Descrição                                                                                                                                                                                                            | Nível | Função |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :----: |
| 4.9.1 | Verifique se as configurações da infraestrutura são respaldadas de acordo com os cronogramas de backup da organização para regiões geograficamente separadas, com a implementação da estratégia de backup 3-2-1.     |   1   |  D/V   |
| 4.9.2 | Verifique se os sistemas de backup operam em redes isoladas com credenciais separadas e armazenamento isolado (air-gapped) para proteção contra ransomware.                                                          |   2   |  D/V   |
| 4.9.3 | Verifique se os procedimentos de recuperação são testados e validados por meio de testes automatizados de acordo com os cronogramas organizacionais, com metas de RTO e RPO atendendo aos requisitos da organização. |   2   |   V    |
| 4.9.4 | Verifique se a recuperação de desastres inclui runbooks específicos para IA com restauração de pesos do modelo, reconstrução do cluster GPU e mapeamento de dependências de serviço.                                 |   3   |   V    |

---

## C4.10 Conformidade e Governança da Infraestrutura

Mantenha a conformidade regulatória por meio de avaliação contínua, documentação e controles automatizados.

|   #    | Descrição                                                                                                                                                                                                 | Nível | Função |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :----: |
| 4.10.1 | Verifique se a conformidade da infraestrutura é avaliada de acordo com os cronogramas organizacionais em relação aos controles SOC 2, ISO 27001 ou FedRAMP, com coleta automatizada de evidências.        |   2   |  D/V   |
| 4.10.2 | Verifique se a documentação da infraestrutura inclui diagramas de rede, mapas de fluxo de dados e modelos de ameaça atualizados de acordo com os requisitos de gerenciamento de mudanças organizacionais. |   2   |   V    |
| 4.10.3 | Verifique se as mudanças na infraestrutura passam por uma avaliação automática de impacto de conformidade com fluxos de trabalho de aprovação regulatória para modificações de alto risco.                |   3   |  D/V   |

---

## C4.11 Segurança de Hardware de IA

Proteja os componentes de hardware específicos para IA, incluindo GPUs, TPUs e aceleradores especializados de IA.

|   #    | Descrição                                                                                                                                                                                                    | Nível | Função |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :----: |
| 4.11.1 | Verifique se o firmware do acelerador de IA (BIOS da GPU, firmware do TPU) é verificado com assinaturas criptográficas e atualizado de acordo com os cronogramas de gerenciamento de patches da organização. |   2   |  D/V   |
| 4.11.2 | Verifique que, antes da execução da carga de trabalho, a integridade do acelerador de IA seja validada por atestado de hardware usando TPM 2.0, Intel TXT ou AMD SVM.                                        |   2   |  D/V   |
| 4.11.3 | Verifique se a memória da GPU está isolada entre as cargas de trabalho usando SR-IOV, MIG (GPU Multi-Instância) ou particionamento de hardware equivalente com sanitização de memória entre os trabalhos.    |   2   |  D/V   |
| 4.11.4 | Verifique se a cadeia de suprimentos de hardware de IA inclui verificação de proveniência com certificados do fabricante e validação de embalagem à prova de violação.                                       |   3   |   V    |
| 4.11.5 | Verifique se os módulos de segurança de hardware (HSMs) protegem os pesos do modelo de IA e as chaves criptográficas com certificação FIPS 140-2 Nível 3 ou Common Criteria EAL4+.                           |   3   |  D/V   |

---

## C4.12 Infraestrutura de IA de Borda e Distribuída

Implantações seguras de IA distribuída incluindo computação de borda, aprendizado federado e arquiteturas multi-site.

|   #    | Descrição                                                                                                                                                                                                               | Nível | Função |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :----: |
| 4.12.1 | Verifique se os dispositivos de edge AI autenticam-se na infraestrutura central usando TLS mútuo com certificados de dispositivo rotacionados de acordo com a política organizacional de gerenciamento de certificados. |   2   |  D/V   |
| 4.12.2 | Verifique se os dispositivos de borda implementam boot seguro com assinaturas verificadas e proteção contra reversão, prevenindo ataques de downgrade de firmware.                                                      |   2   |  D/V   |
| 4.12.3 | Verifique se a coordenação de IA distribuída utiliza algoritmos de consenso tolerantes a falhas bizantinas com validação dos participantes e detecção de nós maliciosos.                                                |   3   |  D/V   |
| 4.12.4 | Verifique se a comunicação edge-to-cloud inclui limitação de largura de banda, compressão de dados e capacidades de operação offline com armazenamento local seguro.                                                    |   3   |  D/V   |

---

## C4.13 Segurança de Infraestrutura Multi-Nuvem e Híbrida

Proteja cargas de trabalho de IA em vários provedores de nuvem e implantações híbridas de nuvem no local.

|   #    | Descrição                                                                                                                                                                                                   | Nível | Função |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :----: |
| 4.13.1 | Verifique se as implantações de IA multi-nuvem utilizam federação de identidade agnóstica à nuvem (OIDC, SAML) com gerenciamento centralizado de políticas entre os provedores.                             |   2   |  D/V   |
| 4.13.2 | Verifique se a transferência de dados entre nuvens utiliza criptografia de ponta a ponta com chaves gerenciadas pelo cliente e controles de residência de dados aplicados conforme a jurisdição.            |   2   |  D/V   |
| 4.13.3 | Verifique se as cargas de trabalho de IA em nuvem híbrida implementam políticas de segurança consistentes nos ambientes locais e na nuvem, com monitoramento e alertas unificados.                          |   2   |  D/V   |
| 4.13.4 | Verifique se a prevenção de bloqueio ao fornecedor de nuvem inclui infraestrutura como código portátil, APIs padronizadas e capacidades de exportação de dados com ferramentas de conversão de formato.     |   3   |   V    |
| 4.13.5 | Verifique se a otimização de custos multi-nuvem inclui controles de segurança que previnem o aumento descontrolado de recursos, bem como cobranças não autorizadas por transferência de dados entre nuvens. |   3   |   V    |

---

## C4.14 Segurança em Automação de Infraestrutura e GitOps

Automatize pipelines de infraestrutura segura e fluxos de trabalho GitOps para gerenciamento de infraestrutura de IA.

|   #    | Descrição                                                                                                                                                                                                            | Nível | Função |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :----: |
| 4.14.1 | Verifique se os repositórios GitOps exigem commits assinados com chaves GPG e regras de proteção de branch que impedem pushs diretos para as branches principais.                                                    |   2   |  D/V   |
| 4.14.2 | Verifique se a automação da infraestrutura inclui detecção de desvio com capacidades automáticas de remediação e reversão acionadas conforme os requisitos de resposta organizacional para mudanças não autorizadas. |   2   |  D/V   |
| 4.14.3 | Verifique se o provisionamento automatizado de infraestrutura inclui a validação da política de segurança com bloqueio de implantação para configurações não conforme.                                               |   2   |  D/V   |
| 4.14.4 | Verifique se os segredos da automação de infraestrutura são gerenciados por meio de operadores externos de segredos (External Secrets Operator, Bank-Vaults) com rotação automática.                                 |   2   |  D/V   |
| 4.14.5 | Verifique se a infraestrutura autocurativa inclui correlação de eventos de segurança com resposta automática a incidentes e fluxos de trabalho de notificação para as partes interessadas.                           |   3   |   V    |

---

## C4.15 Segurança de Infraestrutura Resistente a Quantum

Prepare a infraestrutura de IA para ameaças da computação quântica por meio da criptografia pós-quântica e protocolos seguros contra quânticos.

|   #    | Descrição                                                                                                                                                                                              | Nível | Função |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :----: |
| 4.15.1 | Verifique se a infraestrutura de IA implementa algoritmos criptográficos pós-quânticos aprovados pelo NIST (CRYSTALS-Kyber, CRYSTALS-Dilithium, SPHINCS+) para troca de chaves e assinaturas digitais. |   3   |  D/V   |
| 4.15.2 | Verifique se os sistemas de distribuição quântica de chaves (QKD) estão implementados para comunicações de IA de alta segurança com protocolos de gerenciamento de chaves quânticas seguras.           |   3   |  D/V   |
| 4.15.3 | Verifique se os frameworks de agilidade criptográfica permitem migração rápida para novos algoritmos pós-quânticos com rotação automatizada de certificados e chaves.                                  |   3   |  D/V   |
| 4.15.4 | Verifique se a modelagem de ameaça quântica avalia a vulnerabilidade da infraestrutura de IA a ataques quânticos com cronogramas de migração documentados e avaliações de risco.                       |   3   |   V    |
| 4.15.5 | Verifique se os sistemas criptográficos híbridos clássicos-quânticos oferecem defesa em profundidade durante o período de transição quântica com monitoramento de desempenho.                          |   3   |  D/V   |

---

## C4.16 Computação Confidencial e Enclaves Seguros

Proteja cargas de trabalho de IA e pesos de modelos usando ambientes de execução confiáveis baseados em hardware e tecnologias de computação confidencial.

|   #    | Descrição                                                                                                                                                                         | Nível | Função |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :----: |
| 4.16.1 | Verifique se os modelos de IA sensíveis são executados dentro de enclaves Intel SGX, AMD SEV-SNP ou ARM TrustZone com memória criptografada e verificação de atestação.           |   3   |  D/V   |
| 4.16.2 | Verifique se os contêiners confidenciais (Kata Containers, gVisor com computação confidencial) isolam cargas de trabalho de IA com criptografia de memória aplicada por hardware. |   3   |  D/V   |
| 4.16.3 | Verifique se a atestação remota valida a integridade do enclave antes de carregar os modelos de IA com prova criptográfica da autenticidade do ambiente de execução.              |   3   |  D/V   |
| 4.16.4 | Verifique se os serviços confidenciais de inferência de IA impedem a extração do modelo por meio de computação criptografada com pesos do modelo selados e execução protegida.    |   3   |  D/V   |
| 4.16.5 | Verifique se a orquestração do ambiente de execução confiável gerencia o ciclo de vida do enclave seguro com atestado remoto e canais de comunicação criptografados.              |   3   |  D/V   |
| 4.16.6 | Verifique se a computação multipartidária segura (SMPC) permite o treinamento colaborativo de IA sem expor conjuntos de dados individuais ou parâmetros do modelo.                |   3   |  D/V   |

---

## C4.17 Infraestrutura de Conhecimento Zero

Implemente sistemas de prova de conhecimento zero para verificação e autenticação de IA que preservem a privacidade sem revelar informações sensíveis.

|   #    | Descrição                                                                                                                                                                                           | Nível | Função |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :----: |
| 4.17.1 | Verifique se as provas de conhecimento zero (ZK-SNARKs, ZK-STARKs) verificam a integridade do modelo de IA e a proveniência do treinamento sem expor os pesos do modelo ou os dados de treinamento. |   3   |  D/V   |
| 4.17.2 | Verifique se os sistemas de autenticação baseados em ZK permitem a verificação de usuários preservando a privacidade para serviços de IA sem revelar informações relacionadas à identidade.         |   3   |  D/V   |
| 4.17.3 | Verifique se os protocolos de interseção privada de conjuntos (PSI) permitem a correspondência segura de dados para IA federada sem expor conjuntos de dados individuais.                           |   3   |  D/V   |
| 4.17.4 | Verifique se os sistemas de aprendizado de máquina com conhecimento zero (ZKML) permitem inferências de IA verificáveis com prova criptográfica de computação correta.                              |   3   |  D/V   |
| 4.17.5 | Verifique que os ZK-rollups oferecem processamento de transações de IA escalável e que preserva a privacidade, com verificação em lote e redução da sobrecarga computacional.                       |   3   |  D/V   |

---

## C4.18 Prevenção de Ataques por Canal Lateral

Proteja a infraestrutura de IA contra ataques de canal lateral baseados em tempo, energia, eletromagnéticos e cache que poderiam vazar informações sensíveis.

|   #    | Descrição                                                                                                                                                                   | Nível | Função |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :----: |
| 4.18.1 | Verifique se o tempo de inferência da IA é normalizado usando algoritmos de tempo constante e preenchimento para evitar ataques de extração de modelo baseados em tempo.    |   3   |  D/V   |
| 4.18.2 | Verifique se a proteção contra análise de consumo de energia inclui injeção de ruído, filtragem da linha de energia e padrões de execução randomizados para hardware de IA. |   3   |  D/V   |
| 4.18.3 | Verifique se a mitigação de canal lateral baseada em cache usa particionamento de cache, randomização e instruções de flush para prevenir o vazamento de informações.       |   3   |  D/V   |
| 4.18.4 | Verifique se a proteção contra emanação eletromagnética inclui blindagem, filtragem de sinais e processamento randomizado para impedir ataques do tipo TEMPEST.             |   3   |  D/V   |
| 4.18.5 | Verifique se as defesas contra canal lateral microarquitetônico incluem controles de execução especulativa e ofuscação de padrão de acesso à memória.                       |   3   |  D/V   |

---

## C4.19 Segurança de Hardware Neuromórfico e de IA Especializada

Arquiteturas de hardware emergentes de IA seguras, incluindo chips neuromórficos, FPGAs, ASICs personalizados e sistemas de computação óptica.

|   #    | Descrição                                                                                                                                                                                     | Nível | Função |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :----: |
| 4.19.1 | Verifique se a segurança do chip neuromórfico inclui criptografia de padrão de disparo, proteção do peso sináptico e validação da regra de aprendizado baseada em hardware.                   |   3   |  D/V   |
| 4.19.2 | Verifique se os aceleradores de IA baseados em FPGA implementam criptografia de bitstream, mecanismos anti-violação e carregamento seguro de configuração com atualizações autenticadas.      |   3   |  D/V   |
| 4.19.3 | Verifique se a segurança do ASIC personalizado inclui processadores de segurança integrados no chip, raiz de confiança de hardware e armazenamento seguro de chaves com detecção de violação. |   3   |  D/V   |
| 4.19.4 | Verifique se os sistemas de computação óptica implementam criptografia óptica segura contra ataques quânticos, comutação fotônica segura e processamento protegido de sinais ópticos.         |   3   |  D/V   |
| 4.19.5 | Verifique se os chips híbridos analógico-digitais de IA incluem computação analógica segura, armazenamento protegido de pesos e conversão autenticada de analógico para digital.              |   3   |  D/V   |

---

## C4.20 Infraestrutura de Computação que Preserva a Privacidade

Implemente controles de infraestrutura para computação que preserva a privacidade a fim de proteger dados sensíveis durante o processamento e análise de IA.

|   #    | Descrição                                                                                                                                                                                                                          | Nível | Função |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :----: |
| 4.20.1 | Verifique se a infraestrutura de criptografia homomórfica permite o processamento criptografado em cargas de trabalho sensíveis de IA com verificação de integridade criptográfica e monitoramento de desempenho.                  |   3   |  D/V   |
| 4.20.2 | Verifique se os sistemas de recuperação privada de informação permitem consultas a bancos de dados sem revelar os padrões de consulta, com proteção criptográfica dos padrões de acesso.                                           |   3   |  D/V   |
| 4.20.3 | Verifique se os protocolos de computação multipartidária segura permitem inferência de IA preservando a privacidade, sem expor entradas individuais ou cálculos intermediários.                                                    |   3   |  D/V   |
| 4.20.4 | Verifique se o gerenciamento de chaves com preservação da privacidade inclui geração distribuída de chaves, criptografia por limiar e rotação segura de chaves com proteção baseada em hardware.                                   |   3   |  D/V   |
| 4.20.5 | Verifique que o desempenho da computação que preserva a privacidade seja otimizado por meio de agrupamento, armazenamento em cache e aceleração de hardware, ao mesmo tempo em que mantém as garantias de segurança criptográfica. |   3   |  D/V   |

---

## C4.15 Segurança de Integração em Nuvem do Framework de Agentes e Implantação Híbrida

Controles de segurança para frameworks de agentes integrados à nuvem com arquiteturas híbridas on-premises/nuvem.

|   #    | Descrição                                                                                                                                     | Nível | Função |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :----: |
| 4.15.1 | Verifique se a integração de armazenamento em nuvem utiliza criptografia de ponta a ponta com gerenciamento de chaves controlado pelo agente. |   1   |  D/V   |
| 4.15.2 | Verifique se os limites de segurança do deployment híbrido estão claramente definidos com canais de comunicação criptografados.               |   2   |  D/V   |
| 4.15.3 | Verifique se o acesso aos recursos em nuvem inclui verificação de confiança zero com autenticação contínua.                                   |   2   |  D/V   |
| 4.15.4 | Verifique se os requisitos de residência de dados são aplicados por meio de atestação criptográfica dos locais de armazenamento.              |   3   |  D/V   |
| 4.15.5 | Verifique se as avaliações de segurança do provedor de nuvem incluem modelagem de ameaças específica para agentes e avaliação de riscos.      |   3   |  D/V   |

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

