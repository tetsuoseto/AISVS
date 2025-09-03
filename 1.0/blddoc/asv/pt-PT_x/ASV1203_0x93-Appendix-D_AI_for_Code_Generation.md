# Apêndice D: Governança e Verificação de Codificação Segura Assistida por IA

## Objetivo

Este capítulo define controles organizacionais básicos para o uso seguro e eficaz de ferramentas de codificação assistidas por IA durante o desenvolvimento de software, assegurando segurança e rastreabilidade ao longo do Ciclo de Vida de Desenvolvimento de Software (CVDS).

---

## AD.1 Fluxo de Trabalho de Codificação Segura Assistido por IA

Integrar ferramentas de IA ao ciclo de vida de desenvolvimento de software seguro (SSDLC) da organização, sem enfraquecer as barreiras de segurança existentes.

|   #    | Descrição                                                                                                                                                                         | Nível | Papel |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AD.1.1 | Verifique se um fluxo de trabalho documentado descreve quando e como as ferramentas de IA podem gerar, refatorar ou revisar código.                                               |   1   |  D/V  |
| AD.1.2 | Verifique se o fluxo de trabalho mapeia para cada fase do SSDLC (design, implementação, revisão de código, testes, implantação).                                                  |   2   |   D   |
| AD.1.3 | Verifique se métricas (por exemplo, densidade de vulnerabilidades, tempo médio de detecção) são coletadas em código gerado por IA e comparadas com linhas de base apenas humanas. |   3   |  D/V  |

---

## AD.2 Qualificação de Ferramentas de IA e Modelagem de Ameaças

Certifique-se de avaliar ferramentas de codificação de IA quanto às capacidades de segurança, risco e impacto na cadeia de suprimentos antes da adoção.

|   #    | Descrição                                                                                                                                                                                | Nível | Papel |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AD.2.1 | Verifique se um modelo de ameaça para cada ferramenta de IA identifica uso indevido, inversão de modelo, vazamento de dados e riscos de cadeia de dependências.                          |   1   |  D/V  |
| AD.2.2 | Verifique se as avaliações de ferramentas incluem análise estática/dinâmica de quaisquer componentes locais e avaliação de pontos finais SaaS (TLS, autenticação/autorização, registro). |   2   |   D   |
| AD.2.3 | Verifique se as avaliações seguem um framework reconhecido e são reexecutadas após alterações de versão maiores.                                                                         |   3   |  D/V  |

---

## AD.3 Gerenciamento Seguro de Prompt e Contexto

Prevenir o vazamento de segredos, código proprietário e dados pessoais ao criar prompts ou contextos para modelos de IA.

|   #    | Descrição                                                                                                                                                                         | Nível | Papel |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AD.3.1 | Verifique se as diretrizes escritas proíbem enviar segredos, credenciais ou dados confidenciais em prompts.                                                                       |   1   |  D/V  |
| AD.3.2 | Verifique se os controles técnicos (redação do lado do cliente, filtros de contexto aprovados) removem automaticamente artefatos sensíveis.                                       |   2   |   D   |
| AD.3.3 | Verifique se prompts e respostas são tokenizados, criptografados em trânsito e em repouso, e os períodos de retenção estão em conformidade com a política de data‑classification. |   3   |  D/V  |

---

## AD.4 Validação de Código IA‑Gerado

Detectar e corrigir vulnerabilidades introduzidas pela saída da IA antes que o código seja mesclado ou implantado.

|   #    | Descrição                                                                                                                                                                                    | Nível | Papel |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AD.4.1 | Verifique se o código IA-gerado está sempre sujeito à revisão de código por humanos.                                                                                                         |   1   |  D/V  |
| AD.4.2 | Verifique se os scanners automatizados (SAST/IAST/DAST) são executados em cada pull request que contenha código AI-gerado e bloqueiam merges com base em descobertas críticas.               |   2   |   D   |
| AD.4.3 | Verifique se os testes de fuzzing diferencial ou testes baseados em propriedades comprovam comportamentos críticos de segurança (por exemplo, validação de entradas, lógica de autorização). |   3   |  D/V  |

---

## AD.5 Explicabilidade e Traçabilidade de Sugestões de Código

Forneça aos auditores e desenvolvedores insights sobre o motivo pelo qual uma sugestão foi feita e como ela evoluiu.

|   #    | Descrição                                                                                                                                                                                                     | Nível | Papel |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AD.5.1 | Verifique se pares de prompt/resposta são registrados com IDs de commit.                                                                                                                                      |   1   |  D/V  |
| AD.5.2 | Verifique se os desenvolvedores podem exibir citações do modelo (trechos de treinamento, documentação) que apoiam uma sugestão.                                                                               |   2   |   D   |
| AD.5.3 | Verifique se os relatórios de explicabilidade são armazenados junto aos artefatos de design e referenciados nas revisões de segurança, em conformidade com os princípios de rastreabilidade da ISO/IEC 42001. |   3   |  D/V  |

---

## AD.6 Feedback Contínuo e Ajuste Fino do Modelo

Melhorar o desempenho de segurança do modelo ao longo do tempo, evitando deriva negativa.

|   #    | Descrição                                                                                                                                                                                                     | Nível | Papel |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AD.6.1 | Verifique se os desenvolvedores podem sinalizar sugestões inseguras ou não-conformes, e que as sinalizações sejam rastreadas.                                                                                 |   1   |  D/V  |
| AD.6.2 | Verifique se o feedback agregado informa ajuste fino‑periódico ou geração‑aumentada por recuperação com corpora de codificação segura verificados (por exemplo, OWASP Cheat Sheets).                          |   2   |   D   |
| AD.6.3 | Verifique que um harness de avaliação em loop‑fechado execute testes de regressão após cada ajuste fino; as métricas de segurança devem atender ou superar as linhas de base anteriores antes da implantação. |   3   |  D/V  |

---

### Referências

* [NIST AI Risk Management Framework 1.0](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements](https://www.iso.org/standard/81230.html)
* [OWASP Secure Coding Practices — Quick Reference Guide](https://owasp.org/www-project-secure-coding-practices-quick-reference-guide/)

