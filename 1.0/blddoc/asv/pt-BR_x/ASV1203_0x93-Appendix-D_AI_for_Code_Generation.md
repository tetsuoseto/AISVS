# Anexo D: Governança e Verificação de Codificação Segura Assistida por IA

## Objetivo

Este capítulo define controles organizacionais básicos para o uso seguro e eficaz de ferramentas de codificação assistidas por IA durante o desenvolvimento de software, garantindo segurança e rastreabilidade ao longo do SDLC.

---

## AD.1 Fluxo de Trabalho de Codificação Segura Assistida por IA

Integre ferramentas de IA no ciclo de desenvolvimento de software seguro (SSDLC) da organização sem enfraquecer os portões de segurança existentes.

|   #    | Descrição                                                                                                                                                                             | Nível | Papel |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AD.1.1 | Verifique se um fluxo de trabalho documentado descreve quando e como as ferramentas de IA podem gerar, refatorar ou revisar código.                                                   |   1   |  D/V  |
| AD.1.2 | Verifique se o fluxo de trabalho corresponde a cada fase do SSDLC (design, implementação, revisão de código, testes, implantação).                                                    |   2   |   D   |
| AD.1.3 | Verifique se as métricas (por exemplo, densidade de vulnerabilidades, tempo médio para detecção) são coletadas no código produzido por IA e comparadas às referências apenas humanas. |   3   |  D/V  |

---

## AD.2 Qualificação de Ferramenta de IA e Modelagem de Ameaças

Certifique-se de que as ferramentas de codificação de IA sejam avaliadas quanto às capacidades de segurança, risco e impacto na cadeia de suprimentos antes da adoção.

|   #    | Descrição                                                                                                                                                                                    | Nível | Papel |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AD.2.1 | Verifique se o modelo de ameaça para cada ferramenta de IA identifica riscos de uso indevido, inversão de modelo, vazamento de dados e cadeia de dependência.                                |   1   |  D/V  |
| AD.2.2 | Verifique se as avaliações de ferramentas incluem análise estática/dinâmica de quaisquer componentes locais e avaliação dos pontos finais do SaaS (TLS, autenticação/autorização, registro). |   2   |   D   |
| AD.2.3 | Verifique se as avaliações seguem um framework reconhecido e são refeitas após mudanças principais na versão.                                                                                |   3   |  D/V  |

---

## AD.3 Gerenciamento Seguro de Prompt & Contexto

Prevenir o vazamento de segredos, código proprietário e dados pessoais ao construir prompts ou contextos para modelos de IA.

|   #    | Descrição                                                                                                                                                                                | Nível | Papel |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AD.3.1 | Verifique se as orientações escritas proíbem o envio de segredos, credenciais ou dados classificados nos prompts.                                                                        |   1   |  D/V  |
| AD.3.2 | Verifique se os controles técnicos (redação do lado do cliente, filtros de contexto aprovados) removem automaticamente artefatos sensíveis.                                              |   2   |   D   |
| AD.3.3 | Verifique se os prompts e respostas são tokenizados, criptografados em trânsito e em repouso, e se os prazos de retenção estão em conformidade com a política de classificação de dados. |   3   |  D/V  |

---

## AD.4 Validação do Código Gerado por IA

Detecte e remedia vulnerabilidades introduzidas pela saída de IA antes que o código seja mesclado ou implantado.

|   #    | Descrição                                                                                                                                                                                | Nível | Papel |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AD.4.1 | Verifique se o código gerado por IA está sempre sujeito à revisão humana de código.                                                                                                      |   1   |  D/V  |
| AD.4.2 | Verifique se os scanners automatizados (SAST/IAST/DAST) são executados em cada pull request contendo código gerado por IA‑e bloqueie fusões em caso de descobertas críticas.             |   2   |   D   |
| AD.4.3 | Verifique se os testes de fuzzing diferencial ou testes baseados em propriedades provam comportamentos críticos de segurança (por exemplo, validação de entrada, lógica de autorização). |   3   |  D/V  |

---

## AD.5 Explicabilidade & Rastreabilidade de Sugestões de Código

Forneça aos auditores e desenvolvedores uma visão de por que uma sugestão foi feita e como ela evoluiu.

|   #    | Descrição                                                                                                                                                                                                      | Nível | Papel |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AD.5.1 | Verifique se os pares de prompt/resposta estão registrados com IDs de commit.                                                                                                                                  |   1   |  D/V  |
| AD.5.2 | Verifique se os desenvolvedores podem exibir citações de modelos (trechos de treinamento, documentação) que apoiam uma sugestão.                                                                               |   2   |   D   |
| AD.5.3 | Verifique se os relatórios de explicabilidade estão armazenados juntamente com os artefatos de design eReferenciados em avaliações de segurança, atendendo aos princípios de rastreabilidade da ISO/IEC 42001. |   3   |  D/V  |

---

## AD.6 Feedback Contínuo e Ajuste Fino do Modelo

Melhore o desempenho de segurança do modelo ao longo do tempo, ao mesmo tempo em que evita o desvio negativo.

|   #    | Descrição                                                                                                                                                                                                  | Nível | Papel |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AD.6.1 | Verifique se os desenvolvedores podem marcar sugestões inseguras ou não conformes, e se as marcações são acompanhadas.                                                                                     |   1   |  D/V  |
| AD.6.2 | Verifique se o feedback agregado informa ajustes finos periódicos ou geração aumentada por recuperação com corpora de codificação segura aprovados (por exemplo, OWASP Cheat Sheets).                      |   2   |   D   |
| AD.6.3 | Verifique se uma estrutura de avaliação de ciclo fechado executa testes de regressão após cada ajuste fino; métricas de segurança devem atender ou superar as referências anteriores antes da implantação. |   3   |  D/V  |

---

### Referências

* [NIST AI Risk Management Framework 1.0](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements](https://www.iso.org/standard/81230.html)
* [OWASP Secure Coding Practices — Quick Reference Guide](https://owasp.org/www-project-secure-coding-practices-quick-reference-guide/)

