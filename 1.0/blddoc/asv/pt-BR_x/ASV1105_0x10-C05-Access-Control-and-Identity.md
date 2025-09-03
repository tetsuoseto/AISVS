# C5 Controle de Acesso e Identidade para Componentes e Usuários de IA

## Objetivo de Controle

O controle de acesso efetivo para sistemas de IA exige gestão de identidade robusta, autorização consciente do contexto e aplicação em tempo de execução, seguindo princípios de zero-trust. Esses controles garantem que humanos, serviços e agentes autônomos interajam apenas com modelos, dados e recursos computacionais dentro de escopos explicitamente concedidos, com verificação contínua e capacidades de auditoria.

---

## C5.1 Gerenciamento de Identidade e Autenticação

Estabeleça identidades respaldadas criptograficamente para todas as entidades com autenticação multifator para operações privilegiadas.

|   #   | Descrição                                                                                                                                                                                                                                                                     | Nível | Papel |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 5.1.1 | Verifique se todos os usuários humanos e principais de serviço autenticam-se por meio de um provedor de identidade corporativo centralizado (IdP) usando os protocolos OIDC/SAML, com mapeamentos únicos de identidade para token (sem contas ou credenciais compartilhadas). |   1   |  D/V  |
| 5.1.2 | Verifique se operações de alto risco (implantação de modelo, exportação de peso, acesso a dados de treinamento, alterações na configuração de produção) exigem autenticação multifator ou autenticação em etapas com revalidação de sessão.                                   |   1   |  D/V  |
| 5.1.3 | Verifique se os novos principais passam por comprovação de identidade que esteja alinhada com o NIST 800-63-3 IAL-2 ou padrões equivalentes antes de receber acesso ao sistema de produção.                                                                                   |   2   |   D   |
| 5.1.4 | Verifique se as revisões de acesso são realizadas trimestralmente com detecção automatizada de contas inativas, aplicação de rotação de credenciais e fluxos de trabalho de desativação.                                                                                      |   2   |   V   |
| 5.1.5 | Verifique se os agentes de IA federados autenticam-se por meio de afirmações JWT assinadas que têm um tempo de validade máximo de 24 horas e incluem prova criptográfica de origem.                                                                                           |   3   |  D/V  |

---

## C5.2 Autorização de Recursos e Privilégio Mínimo

Implemente controles de acesso de granulação fina para todos os recursos de IA com modelos de permissão explícitos e trilhas de auditoria.

|   #   | Descrição                                                                                                                                                                                                                                                               | Nível | Papel |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 5.2.1 | Verifique se todos os recursos de IA (conjuntos de dados, modelos, endpoints, coleções de vetores, índices de incorporação, instâncias de computação) aplicam controles de acesso baseados em funções com listas de permissão explícitas e políticas padrão de negação. |   1   |  D/V  |
| 5.2.2 | Verifique se os princípios de mínimo privilégio são aplicados por padrão com contas de serviço começando com permissões de leitura e uma justificativa comercial documentada requerida para acesso de escrita.                                                          |   1   |  D/V  |
| 5.2.3 | Verifique se todas as modificações de controle de acesso estão vinculadas a solicitações de alteração aprovadas e registradas de forma imutável com carimbos de data/hora, identidades do ator, identificadores de recursos e diferenças de permissões.                 |   1   |   V   |
| 5.2.4 | Verifique se os rótulos de classificação de dados (PII, PHI, controlado por exportação, proprietário) propagam-se automaticamente para recursos derivados (embeddings, caches de prompts, saídas do modelo) com aplicação consistente da política.                      |   2   |   D   |
| 5.2.5 | Verifique se as tentativas de acesso não autorizado e eventos de escalonamento de privilégios acionam alertas em tempo real com metadata contextual para sistemas SIEM dentro de 5 minutos.                                                                             |   2   |  D/V  |

---

## C5.3 Avaliação Dinâmica de Políticas

Implante mecanismos de controle de acesso baseado em atributos (ABAC) para decisões de autorização sensíveis ao contexto, com capacidades de auditoria.

|   #   | Descrição                                                                                                                                                                                                                                | Nível | Papel |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 5.3.1 | Verifique se as decisões de autorização são externalizadas para um motor de política dedicado (OPA, Cedar ou equivalente) acessível via APIs autenticadas com proteção de integridade criptográfica.                                     |   1   |  D/V  |
| 5.3.2 | Verifique se as políticas avaliam atributos dinâmicos em tempo de execução, incluindo nível de liberação do usuário, classificação de sensibilidade do recurso, contexto da solicitação, isolamento do inquilino e restrições temporais. |   1   |  D/V  |
| 5.3.3 | Verifique se as definições de política estão sob controle de versão, passaram por revisão por pares e foram validadas por meio de testes automatizados em pipelines de CI/CD antes da implantação em produção.                           |   2   |   D   |
| 5.3.4 | Verifique se os resultados da avaliação da política incluem raciocínios de decisão estruturados e são transmitidos aos sistemas SIEM para análise de correlação e relatórios de conformidade.                                            |   2   |   V   |
| 5.3.5 | Verifique se os valores de tempo de vida (TTL) do cache de política não excedem 5 minutos para recursos de alta sensibilidade e 1 hora para recursos padrão com capacidade de invalidação de cache.                                      |   3   |  D/V  |

---

## C5.4 Aplicação de Segurança em Tempo de Consulta

Implemente controles de segurança na camada de banco de dados com filtragem obrigatória e políticas de segurança a nível de linha.

|   #   | Descrição                                                                                                                                                                                                                                            | Nível | Papel |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 5.4.1 | Verifique se todas as consultas ao banco de dados vetorial e SQL incluem filtros de segurança obrigatórios (ID do locatário, rótulos de sensibilidade, escopo do usuário) aplicados no nível do motor do banco de dados, não no código da aplicação. |   1   |  D/V  |
| 5.4.2 | Verifique se as políticas de segurança a nível de linha (RLS) e mascaramento a nível de campo estão ativadas com herança de políticas para todos os bancos de dados vetoriais, índices de pesquisa e conjuntos de dados de treinamento.              |   1   |  D/V  |
| 5.4.3 | Verifique se avaliações de autorização falhadas impedirão "ataques de deputado confuso" abortando imediatamente as consultas e retornando códigos de erro de autorização explícitos, em vez de retornar conjuntos de resultados vazios.              |   2   |   D   |
| 5.4.4 | Verifique se a latência de avaliação da política está sendo monitorada continuamente com alertas automatizados para condições de tempo limite que poderiam permitir a bypass de autorização.                                                         |   2   |   V   |
| 5.4.5 | Verifique se os mecanismos de re tentativa de consulta reavaliam as políticas de autorização para levar em conta alterações dinâmicas de permissões dentro de sessões de usuário ativas.                                                             |   3   |  D/V  |

---

## C5.5 Filtragem de Saída & Prevenção de Perda de Dados

Implemente controles de pós-processamento para evitar a exposição não autorizada de dados em conteúdo gerado por IA.

|   #   | Descrição                                                                                                                                                                                                                      | Nível | Papel |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 5.5.1 | Verifique se os mecanismos de filtragem pós-inferência escaneiam e redigem informações pessoais identificáveis não autorizadas, informações classificadas e dados proprietários antes de entregar o conteúdo aos solicitantes. |   1   |  D/V  |
| 5.5.2 | Verifique se citações, referências e atribuições de fontes nas saídas do modelo são validadas em relação às permissões do solicitante e removidas caso seja detectado acesso não autorizado.                                   |   1   |  D/V  |
| 5.5.3 | Verifique se as restrições de formato de saída (PDFs sanitizados, imagens sem metadata, tipos de arquivo aprovados) são aplicadas com base nos níveis de permissão do usuário e nas classificações de dados.                   |   2   |   D   |
| 5.5.4 | Verifique se os algoritmos de redação são determinísticos, controlados por versão e mantêm registros de auditoria para apoiar investigações de conformidade e análises forenses.                                               |   2   |   V   |
| 5.5.5 | Verifique se eventos de redação de alto risco geram registros adaptativos que incluem hashes criptográficos do conteúdo original para recuperação forense sem exposição de dados.                                              |   3   |   V   |

---

## C5.6 Isolamento Multi-Inquilino

Garantir isolamento criptográfico e lógico entre locatários em infraestrutura de IA compartilhada.

|   #   | Descrição                                                                                                                                                                                                               | Nível | Papel |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 5.6.1 | Verifique se os espaços de memória, armazenamentos de embeds, entradas de cache e arquivos temporários estão segregados por namespace por locatário, com exclusão segura na exclusão do locatário ou término da sessão. |   1   |  D/V  |
| 5.6.2 | Verifique se cada solicitação de API inclui um identificador de inquilino autenticado que seja validado criptograficamente em relação ao contexto da sessão e às permissões do usuário.                                 |   1   |  D/V  |
| 5.6.3 | Verifique se as políticas de rede implementam regras de negação padrão para comunicação entre inquilinos dentro de malhas de serviço e plataformas de orquestração de containers.                                       |   2   |   D   |
| 5.6.4 | Verifique se as chaves de criptografia são exclusivas por locatário com suporte a chaves gerenciadas pelo cliente (CMK) e isolamento criptográfico entre os repositórios de dados dos locatários.                       |   3   |   D   |

---

## C5.7 Autorização de Agente Autônomo

Controle de permissões para agentes de IA e sistemas autônomos por meio de tokens de capacidade com escopo e autorização contínua.

|   #   | Descrição                                                                                                                                                                                                                                                  | Nível | Papel |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 5.7.1 | Verifique se agentes autônomos recebem tokens de capacidade com escopo que enumeram explicitamente ações permitidas, recursos acessíveis, limites de tempo e restrições operacionais.                                                                      |   1   |  D/V  |
| 5.7.2 | Verifique se as capacidades de alto risco (acesso ao sistema de arquivos, execução de código, chamadas de API externas, transações financeiras) estão desativadas por padrão e exigem autorizações explícitas para ativação com justificativas comerciais. |   1   |  D/V  |
| 5.7.3 | Verifique se os tokens de capacidade estão vinculados às sessões de usuário, incluem proteção de integridade criptográfica e garantem que não possam ser persistidos ou reutilizados em cenários offline.                                                  |   2   |   D   |
| 5.7.4 | Verifique se as ações iniciadas pelo agente passam por autorização secundária através do mecanismo de política ABAC com avaliação de contexto completa e registro de auditoria.                                                                            |   2   |   V   |
| 5.7.5 | Verifique se as condições de erro do agente e o tratamento de exceções incluem informações sobre o escopo da capacidade para apoiar a análise de incidentes e investigações forenses.                                                                      |   3   |   V   |

---

## Referências

### Padrões & Estruturas

* [NIST SP 800-63-3: Digital Identity Guidelines](https://pages.nist.gov/800-63-3/)
* [Zero Trust Architecture – NIST SP 800-207](https://nvlpubs.nist.gov/nistpubs/specialpublications/NIST.SP.800-207.pdf)
* [OWASP Application Security Verification Standard (AISVS)](https://owasp.org/www-project-application-security-verification-standard/)
  ​
### Guias de Implementação

* [Identity and Access Management in the AI Era: 2025 Guide – IDSA](https://www.idsalliance.org/blog/identity-and-access-management-in-the-ai-era-2025-guide/)
* [Attribute-Based Access Control with OPA – Permify](https://medium.com/permify-tech-blog/attribute-based-access-control-abac-implementation-with-open-policy-agent-opa-b47052248f29)
* [How We Designed Cedar to Be Intuitive, Fast, and Safe – AWS](https://aws.amazon.com/blogs/security/how-we-designed-cedar-to-be-intuitive-to-use-fast-and-safe/)
  ​
### Segurança Específica de AI

* [Row Level Security in Vector DBs for RAG – Bluetuple.ai](https://medium.com/bluetuple-ai/implementing-row-level-security-in-vector-dbs-for-rag-applications-fdbccb63d464)
* [Tenant Isolation in Multi-Tenant Systems – WorkOS](https://workos.com/blog/tenant-isolation-in-multi-tenant-systems)
* [Handling AI Agent Permissions – Stytch](https://stytch.com/blog/handling-ai-agent-permissions/)
* [OWASP Top 10 for Large Language Model Applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/)

