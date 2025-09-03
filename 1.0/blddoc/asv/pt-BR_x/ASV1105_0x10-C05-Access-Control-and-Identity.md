# C5 Controle de Acesso e Identidade para Componentes de IA e Usuários

## Objetivo de Controle

O controle de acesso efetivo para sistemas de IA requer gerenciamento robusto de identidade, autorização contextual e aplicação em tempo de execução, seguindo os princípios de zero-trust. Esses controles garantem que seres humanos, serviços e agentes autônomos interajam apenas com modelos, dados e recursos computacionais dentro de escopos explicitamente concedidos, com verificação contínua e capacidades de auditoria.

---

## C5.1 Gestão de Identidade e Autenticação

Estabeleça identidades respaldadas criptograficamente para todas as entidades, com autenticação multifator para operações privilegiadas.

|   #   | Descrição                                                                                                                                                                                                                                                                             | Nível | Papel |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 5.1.1 | Verifique que todos os usuários humanos e identidades de serviço se autentiquem por meio de um provedor de identidade corporativo centralizado (IdP) que utilize os protocolos OIDC/SAML, com mapeamentos de identidade-para-token únicos (sem contas ou credenciais compartilhadas). |   1   |  D/V  |
| 5.1.2 | Verifique se operações de alto risco (implantação de modelo, exportação de pesos, acesso a dados de treinamento, alterações de configuração de produção) exigem autenticação multifator ou autenticação de escalonamento com revalidação de sessão.                                   |   1   |  D/V  |
| 5.1.3 | Verifique que novas identidades passem por uma verificação de identidade alinhada com o NIST 800-63-3 IAL-2 ou padrões equivalentes antes de receber acesso ao sistema de produção.                                                                                                   |   2   |   D   |
| 5.1.4 | Verifique se as revisões de acesso são realizadas trimestralmente com detecção automática de contas inativas, aplicação da rotação de credenciais e fluxos de desprovisionamento.                                                                                                     |   2   |   V   |
| 5.1.5 | Verifique que os agentes de IA federados se autentiquem por meio de asserções JWT assinadas que tenham vida útil máxima de 24 horas e incluam prova criptográfica de origem.                                                                                                          |   3   |  D/V  |

---

## C5.2 Autorização de Recursos e Princípio do Menor Privilégio

Implemente controles de acesso granulares para todos os recursos de IA, com modelos de permissão explícitos e trilhas de auditoria.

|   #   | Descrição                                                                                                                                                                                                                                                                   | Nível | Papel |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 5.2.1 | Verifique se cada recurso de IA (conjuntos de dados, modelos, pontos de extremidade, coleções de vetores, índices de embeddings, instâncias de computação) aplica controles de acesso baseados em papéis com listas de permissões explícitas e políticas de negação padrão. |   1   |  D/V  |
| 5.2.2 | Verifique se os princípios do menor privilégio são aplicados por padrão, com contas de serviço iniciando com permissões de somente leitura e exigindo justificativa de negócios documentada para o acesso de escrita.                                                       |   1   |  D/V  |
| 5.2.3 | Verifique se todas as modificações de controle de acesso estão vinculadas a solicitações de mudança aprovadas e registradas de forma imutável com carimbos de data/hora, identidades dos agentes, identificadores de recursos e variações de permissões.                    |   1   |   V   |
| 5.2.4 | Verifique se os rótulos de classificação de dados (PII, PHI, controlados para exportação, proprietários) se propagam automaticamente para recursos derivados (embeddings, caches de prompts, saídas do modelo) com aplicação consistente de políticas.                      |   2   |   D   |
| 5.2.5 | Verifique se tentativas de acesso não autorizado e eventos de escalonamento de privilégios disparam alertas em tempo real com metadados contextuais para sistemas SIEM dentro de 5 minutos.                                                                                 |   2   |  D/V  |

---

## C5.3 Avaliação de Políticas Dinâmicas

Implantar mecanismos de controle de acesso baseado em atributos (ABAC) para decisões de autorização contextuais com capacidades de auditoria.

|   #   | Descrição                                                                                                                                                                                                                                                | Nível | Papel |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 5.3.1 | Verifique se as decisões de autorização estão externalizadas para um motor de políticas dedicado (OPA, Cedar ou equivalente) acessível via APIs autenticadas com proteção de integridade criptográfica.                                                  |   1   |  D/V  |
| 5.3.2 | Verifique se as políticas avaliam atributos dinâmicos em tempo de execução, incluindo o nível de autorização do usuário, a classificação de sensibilidade do recurso, o contexto da requisição, o isolamento entre locatários e as restrições temporais. |   1   |  D/V  |
| 5.3.3 | Verifique se as definições de políticas estão sob controle de versão, são revisadas por pares e são validadas por meio de testes automatizados em pipelines CI/CD antes da implantação em produção.                                                      |   2   |   D   |
| 5.3.4 | Verifique se os resultados da avaliação de políticas incluem justificativas de decisão estruturadas e se são transmitidos aos sistemas SIEM para análise de correlação e relatórios de conformidade.                                                     |   2   |   V   |
| 5.3.5 | Verifique se os valores de TTL (tempo de vida útil) do cache de políticas não excedem 5 minutos para recursos de alta sensibilidade e 1 hora para recursos padrão com capacidades de invalidação de cache.                                               |   3   |  D/V  |

---

## C5.4 Aplicação de Segurança em Tempo de Consulta

Implemente controles de segurança na camada de banco de dados com filtragem obrigatória e políticas de segurança em nível de linha.

|   #   | Descrição                                                                                                                                                                                                                                                | Nível | Papel |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 5.4.1 | Verifique se todas as consultas de bancos de dados vetoriais e SQL incluem filtros de segurança obrigatórios (ID do inquilino, rótulos de sensibilidade, escopo do usuário) aplicados no nível do motor de banco de dados, e não no código da aplicação. |   1   |  D/V  |
| 5.4.2 | Verifique se as políticas de segurança a nível de linha (RLS) e o mascaramento a nível de campo estão habilitados com herança de políticas para todos os bancos de dados vetoriais, índices de busca e conjuntos de dados de treinamento.                |   1   |  D/V  |
| 5.4.3 | Verifique se avaliações de autorização com falha irão impedir "confused deputy attacks" ao abortar imediatamente consultas e retornar códigos de erro de autorização explícitos, em vez de retornar conjuntos de resultados vazios.                      |   2   |   D   |
| 5.4.4 | Verifique se a latência da avaliação de políticas está monitorada continuamente com alertas automatizados para condições de tempo limite que possam permitir o bypass de autorização.                                                                    |   2   |   V   |
| 5.4.5 | Verifique se os mecanismos de reexecução de consultas reavaliam as políticas de autorização para considerar alterações dinâmicas de permissões dentro de sessões de usuário ativas.                                                                      |   3   |  D/V  |

---

## C5.5 Filtragem de Saída e Prevenção de Perda de Dados

Implantar controles de pós-processamento para evitar a exposição não autorizada de dados em conteúdo gerado por IA.

|   #   | Descrição                                                                                                                                                                                                               | Nível | Papel |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 5.5.1 | Verifique se os mecanismos de filtragem pós-inferência realizam varredura e ocultação de PII não autorizada, informações classificadas e dados proprietários antes de entregar o conteúdo aos solicitantes.             |   1   |  D/V  |
| 5.5.2 | Verifique se citações, referências e atribuições de fonte nas saídas do modelo são validadas com base nas permissões do solicitante e removidas se for detectado acesso não autorizado.                                 |   1   |  D/V  |
| 5.5.3 | Verifique se as restrições de formato de saída (PDFs sanitizados, imagens com metadados removidos, tipos de arquivo aprovados) são aplicadas com base nos níveis de permissão do usuário e nas classificações de dados. |   2   |   D   |
| 5.5.4 | Verifique se os algoritmos de anonimização são determinísticos, versionados e mantêm registros de auditoria para apoiar investigações de conformidade e análises forenses.                                              |   2   |   V   |
| 5.5.5 | Verifique se eventos de redação de alto risco geram registros adaptativos que incluem hashes criptográficos do conteúdo original para recuperação forense sem exposição de dados.                                       |   3   |   V   |

---

## C5.6 Isolamento entre inquilinos

Garanta o isolamento criptográfico e lógico entre locatários em uma infraestrutura de IA compartilhada.

|   #   | Descrição                                                                                                                                                                                                                           | Nível | Papel |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 5.6.1 | Verifique se os espaços de memória, armazenamentos de embeddings, entradas de cache e arquivos temporários estão segregados por espaço de nomes por inquilino, com purga segura na exclusão do inquilino ou encerramento da sessão. |   1   |  D/V  |
| 5.6.2 | Verifique se cada solicitação de API inclui um identificador de locatário autenticado que seja validado criptograficamente em relação ao contexto da sessão e às permissões do usuário.                                             |   1   |  D/V  |
| 5.6.3 | Verifique se as políticas de rede implementam regras de negação padrão para comunicação entre inquilinos em malhas de serviço e plataformas de orquestração de contêineres.                                                         |   2   |   D   |
| 5.6.4 | Verifique se as chaves de criptografia são únicas por inquilino, com suporte a chave gerenciada pelo cliente (CMK), e isolamento criptográfico entre os armazéns de dados dos inquilinos.                                           |   3   |   D   |

---

## C5.7 Autorização de Agente Autônomo

Controlar permissões para agentes de IA e sistemas autônomos por meio de tokens de capacidade com escopo e autorização contínua.

|   #   | Descrição                                                                                                                                                                                                                                                  | Nível | Papel |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 5.7.1 | Verifique se os agentes autônomos recebem tokens de capacidade com escopo que enumeram explicitamente as ações permitidas, os recursos acessíveis, os limites temporais e as restrições operacionais.                                                      |   1   |  D/V  |
| 5.7.2 | Verifique se as capacidades de alto risco (acesso ao sistema de arquivos, execução de código, chamadas de API externas, transações financeiras) estão desativadas por padrão e exigem autorizações explícitas para ativação com justificativas comerciais. |   1   |  D/V  |
| 5.7.3 | Verifique que os tokens de capacidade estejam vinculados às sessões do usuário, incluam proteção de integridade criptográfica e garantam que não possam ser persistidos nem reutilizados em cenários offline.                                              |   2   |   D   |
| 5.7.4 | Verifique que ações iniciadas-por agente passem por autorização secundária por meio do motor de políticas ABAC com avaliação de contexto completa e registro de auditoria.                                                                                 |   2   |   V   |
| 5.7.5 | Verifique se as condições de erro do agente e o tratamento de exceções incluem informações sobre o alcance da capacidade para apoiar a análise de incidentes e a investigação forense.                                                                     |   3   |   V   |

---

## Referências

### Padrões e Frameworks

* [NIST SP 800-63-3: Digital Identity Guidelines](https://pages.nist.gov/800-63-3/)
* [Zero Trust Architecture – NIST SP 800-207](https://nvlpubs.nist.gov/nistpubs/specialpublications/NIST.SP.800-207.pdf)
* [OWASP Application Security Verification Standard (AISVS)](https://owasp.org/www-project-application-security-verification-standard/)
  ​
### Guias de Implementação

* [Identity and Access Management in the AI Era: 2025 Guide – IDSA](https://www.idsalliance.org/blog/identity-and-access-management-in-the-ai-era-2025-guide/)
* [Attribute-Based Access Control with OPA – Permify](https://medium.com/permify-tech-blog/attribute-based-access-control-abac-implementation-with-open-policy-agent-opa-b47052248f29)
* [How We Designed Cedar to Be Intuitive, Fast, and Safe – AWS](https://aws.amazon.com/blogs/security/how-we-designed-cedar-to-be-intuitive-to-use-fast-and-safe/)
  ​
### Segurança específica de IA.

* [Row Level Security in Vector DBs for RAG – Bluetuple.ai](https://medium.com/bluetuple-ai/implementing-row-level-security-in-vector-dbs-for-rag-applications-fdbccb63d464)
* [Tenant Isolation in Multi-Tenant Systems – WorkOS](https://workos.com/blog/tenant-isolation-in-multi-tenant-systems)
* [Handling AI Agent Permissions – Stytch](https://stytch.com/blog/handling-ai-agent-permissions/)
* [OWASP Top 10 for Large Language Model Applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/)

