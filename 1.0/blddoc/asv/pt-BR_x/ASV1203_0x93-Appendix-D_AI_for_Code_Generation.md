# Apêndice D: Governança e Verificação da Codificação Segura Assistida por IA

## Objetivo

Este capítulo define controles organizacionais básicos para o uso seguro e eficaz de ferramentas de codificação assistidas por IA durante o desenvolvimento de software, assegurando segurança e rastreabilidade ao longo do SDLC.

---

## AD.1 Fluxo de Trabalho de Codificação Segura Assistido por IA

Integrar ferramentas de IA no ciclo de vida do desenvolvimento de software seguro (SSDLC) da organização, sem enfraquecer os portões de segurança existentes.

|   #    | Descrição                                                                                                                                                                         | Nível | Papel |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AD.1.1 | Verifique se um fluxo de trabalho documentado descreve quando e como as ferramentas de IA podem gerar, refatorar ou revisar código.                                               |   1   |  D/V  |
| AD.1.2 | Verifique se o fluxo de trabalho corresponde a cada fase do SSDLC (design, implementação, revisão de código, testes, implantação).                                                |   2   |   D   |
| AD.1.3 | Verifique se as métricas (por exemplo, densidade de vulnerabilidades, tempo médio de detecção) são coletadas em código gerado por IA e comparadas com referências apenas humanas. |   3   |  D/V  |

---

## AD.2 Qualificação de Ferramentas de IA e Modelagem de Ameaças

Certifique-se de que as ferramentas de codificação de IA sejam avaliadas quanto às capacidades de segurança, aos riscos e ao impacto na cadeia de suprimentos antes da adoção.

|   #    | Descrição                                                                                                                                                                             | Nível | Papel |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AD.2.1 | Verifique se o modelo de ameaça para cada ferramenta de IA identifica uso indevido, inversão de modelo, vazamento de dados e riscos da cadeia de dependências.                        |   1   |  D/V  |
| AD.2.2 | Verifique se as avaliações das ferramentas incluem análise estática/dinâmica de quaisquer componentes locais e avaliação de endpoints SaaS (TLS, autenticação/autorização, registro). |   2   |   D   |
| AD.2.3 | Verifique se as avaliações seguem um framework reconhecido e são re-executadas após mudanças de versão maiores.                                                                       |   3   |  D/V  |

---

## AD.3 Gerenciamento Seguro de Prompt e Contexto

Prevenir o vazamento de segredos, código proprietário e dados pessoais ao criar prompts ou contextos para modelos de IA.

|   #    | Descrição                                                                                                                                                                                            | Nível | Papel |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AD.3.1 | Verifique se as diretrizes escritas proíbem o envio de segredos, credenciais ou dados classificados em prompts.                                                                                      |   1   |  D/V  |
| AD.3.2 | Verifique se os controles técnicos (anonimização no lado do client‑side, filtros de contexto aprovados) removem automaticamente artefatos sensíveis.                                                 |   2   |   D   |
| AD.3.3 | Verifique se as solicitações e as respostas estão tokenizadas, criptografadas em trânsito e em repouso, e se os períodos de retenção estão em conformidade com a política de classificação de dados. |   3   |  D/V  |

---

## AD.4 Validação de Código Gerado por IA

Detectar e corrigir vulnerabilidades introduzidas pela saída de IA antes que o código seja mesclado ou implantado.

|   #    | Descrição                                                                                                                                                                         | Nível | Papel |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AD.4.1 | Verifique que o código gerado por IA esteja sempre sujeito à revisão de código por humanos.                                                                                       |   1   |  D/V  |
| AD.4.2 | Verifique se scanners automatizados (SAST/IAST/DAST) são executados em cada pull request que contenha código gerado por IA e bloqueiam fusões com base em achados críticos.       |   2   |   D   |
| AD.4.3 | Verifique se o fuzzing diferencial ou testes baseados em propriedades comprovam comportamentos críticos de segurança (por exemplo, validação de entrada e lógica de autorização). |   3   |  D/V  |

---

## AD.5 Explicabilidade e Rastreabilidade de Sugestões de Código

Fornecer aos auditores e aos desenvolvedores uma visão de por que uma sugestão foi feita e como ela evoluiu.

|   #    | Descrição                                                                                                                                                                                    | Nível | Papel |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AD.5.1 | Verifique se os pares de prompt e resposta são registrados com identificadores de commit.                                                                                                    |   1   |  D/V  |
| AD.5.2 | Verifique se os desenvolvedores podem tornar visíveis as citações do modelo (trechos de treinamento, documentação) que apoiam uma sugestão.                                                  |   2   |   D   |
| AD.5.3 | Verifique se os relatórios de explicabilidade estão armazenados com artefatos de design e referenciados em revisões de segurança, atendendo aos princípios de rastreabilidade ISO/IEC 42001. |   3   |  D/V  |

---

## AD.6 Feedback Contínuo & Ajuste Fino do Modelo

Melhorar o desempenho de segurança do modelo ao longo do tempo, evitando deriva negativa.

|   #    | Descrição                                                                                                                                                                                                        | Nível | Papel |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| AD.6.1 | Verifique se os desenvolvedores podem sinalizar sugestões inseguras ou não‑conformes, e se as sinalizações são rastreadas.                                                                                       |   1   |  D/V  |
| AD.6.2 | Verifique se o feedback agregado informa o ajuste-fino periódico ou a geração com recuperação aumentada usando conjuntos de corpora de codificação segura verificados (por exemplo, OWASP Cheat Sheets).         |   2   |   D   |
| AD.6.3 | Verifique que um mecanismo de avaliação em loop‑fechado executa testes de regressão após cada ajuste‑fino; métricas de segurança devem atender ou exceder padrões de referência anteriores antes da implantação. |   3   |  D/V  |

---

### Referências

* [NIST AI Risk Management Framework 1.0](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements](https://www.iso.org/standard/81230.html)
* [OWASP Secure Coding Practices — Quick Reference Guide](https://owasp.org/www-project-secure-coding-practices-quick-reference-guide/)

