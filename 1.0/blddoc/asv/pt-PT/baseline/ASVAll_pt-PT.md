## Frontispício

### Sobre o Padrão

O Padrão de Verificação de Segurança em Inteligência Artificial (AISVS) é um catálogo orientado pela comunidade de requisitos de segurança que cientistas de dados, engenheiros de MLOps, arquitetos de software, desenvolvedores, testadores, profissionais de segurança, fornecedores de ferramentas, reguladores e consumidores podem usar para projetar, construir, testar e verificar sistemas e aplicações confiáveis habilitados por IA. Ele fornece uma linguagem comum para especificar controles de segurança ao longo do ciclo de vida da IA — desde a coleta de dados e desenvolvimento de modelos até a implantação e monitoramento contínuo — para que as organizações possam medir e melhorar a resiliência, privacidade e segurança de suas soluções de IA.

### Copyright e Licença

Versão 0.1 (Primeiro Rascunho Público - Trabalho em Andamento), 2025  

![license](images/license.png)
Direitos autorais © 2025 O Projeto AISVS.  

Lançado sob aCreative Commons Attribution‑ShareAlike 4.0 International License.
Para qualquer reutilização ou distribuição, você deve comunicar claramente os termos da licença desta obra para os outros.

### Líderes de Projeto

Jim Manico
Aras “Russ” Memisyazici

### Contribuidores e Revisores

https://github.com/ottosulin
https://github.com/mbhatt1
https://github.com/vineethsai
https://github.com/cciprofm
https://github.com/deepakrpandey12


---

AISVS é um padrão completamente novo criado especificamente para abordar os desafios únicos de segurança dos sistemas de inteligência artificial. Embora se baseie em melhores práticas de segurança mais amplas, cada requisito do AISVS foi desenvolvido do zero para refletir o cenário de ameaças da IA e ajudar as organizações a construir soluções de IA mais seguras e resilientes.

## Prefácio

Bem-vindo ao Padrão de Verificação de Segurança em Inteligência Artificial (AISVS) versão 1.0!

### Introdução

Estabelecido em 2025 por meio de um esforço colaborativo da comunidade, o AISVS define os requisitos de segurança a serem considerados ao projetar, desenvolver, implantar e operar modelos de IA modernos, pipelines e serviços habilitados por IA.

AISVS v1.0 representa o trabalho conjunto dos seus líderes de projeto, grupo de trabalho e colaboradores da comunidade mais ampla para produzir uma linha de base pragmática e testável para a segurança de sistemas de IA.

Nosso objetivo com este lançamento é tornar o AISVS fácil de adotar, mantendo o foco preciso em seu escopo definido e abordando o cenário de riscos em rápida evolução, exclusivo da IA.

### Objetivos Principais para a Versão 1.0 do AISVS

A versão 1.0 será criada com vários princípios orientadores.

#### Escopo Bem Definido

Cada requisito deve estar alinhado com o nome e a missão da AISVS:

Inteligência Artificial – Os controles operam na camada de IA/ML (dados, modelo, pipeline ou inferência) e são de responsabilidade dos profissionais de IA.
Segurança – Os requisitos mitigam diretamente os riscos identificados de segurança, privacidade ou segurança.
Verificação – A linguagem é escrita para que a conformidade possa ser validada objetivamente.
Padrão – As seções seguem uma estrutura e terminologia consistentes para formar uma referência coerente.
​
---

Seguindo o AISVS, as organizações podem avaliar sistematicamente e fortalecer a postura de segurança de suas soluções de IA, promovendo uma cultura de engenharia de IA segura.

## Usando o AISVS

A Norma de Verificação de Segurança para Inteligência Artificial (AISVS) define requisitos de segurança para aplicações e serviços de IA modernos, focando em aspectos sob o controle dos desenvolvedores de aplicações.

O AISVS destina-se a qualquer pessoa que desenvolva ou avalie a segurança de aplicações de IA, incluindo desenvolvedores, arquitetos, engenheiros de segurança e auditores. Este capítulo apresenta a estrutura e o uso do AISVS, incluindo seus níveis de verificação e casos de uso previstos.

### Níveis de Verificação de Segurança em Inteligência Artificial

O AISVS define três níveis crescentes de verificação de segurança. Cada nível adiciona profundidade e complexidade, permitindo que as organizações adaptem sua postura de segurança ao nível de risco de seus sistemas de IA.

As organizações podem começar no Nível 1 e progredivamente adotar níveis mais altos à medida que a maturidade em segurança e a exposição a ameaças aumentam.

#### Definição dos Níveis

Cada requisito na AISVS v1.0 é atribuído a um dos seguintes níveis:

 Requisitos do nível 1

O Nível 1 inclui os requisitos de segurança mais críticos e fundamentais. Estes se concentram em prevenir ataques comuns que não dependem de outras pré-condições ou vulnerabilidades. A maioria dos controles do Nível 1 são ou simples de implementar ou essenciais o suficiente para justificar o esforço.

 Requisitos do nível 2

O Nível 2 aborda ataques mais avançados ou menos comuns, bem como defesas em camadas contra ameaças generalizadas. Esses requisitos podem envolver lógica mais complexa ou visar pré-requisitos específicos de ataque.

 Requisitos de Nível 3

O Nível 3 inclui controles que normalmente são mais difíceis de implementar ou têm aplicabilidade situacional. Estes frequentemente representam mecanismos de defesa em profundidade ou mitigações contra ataques específicos, direcionados ou de alta complexidade.

#### Função (D/V)

Cada requisito do AISVS é marcado de acordo com o público-alvo principal:

D – Requisitos focados no desenvolvedor
V – Requisitos focados no verificador/auditor
D/V – Relevante tanto para desenvolvedores quanto para verificadores

## Governança de Dados de Treinamento C1 e Gestão de Viés

### Objetivo de Controle

Os dados de treinamento devem ser obtidos, manejados e mantidos de maneira que preservem a proveniência, segurança, qualidade e justiça. Fazer isso cumpre deveres legais e reduz riscos de viés, envenenamento ou violações de privacidade que possam surgir durante o treinamento e afetar todo o ciclo de vida da IA.

---

### C1.1 Procedência dos Dados de Treinamento

Mantenha um inventário verificável de todos os conjuntos de dados, aceite apenas fontes confiáveis e registre todas as alterações para garantir auditabilidade.

 #1.1.1    Nível: 1    Função: D/V
 Verifique se um inventário atualizado de cada fonte de dados de treinamento (origem, responsável/dono, licença, método de coleta, restrições de uso pretendido e histórico de processamento) está mantido.
 #1.1.2    Nível: 1    Função: D/V
 Verifique se os processos de dados de treinamento excluem recursos, atributos ou campos desnecessários (por exemplo, metadados não utilizados, PII sensível, dados de teste vazados).
 #1.1.3    Nível: 2    Função: D/V
 Verifique se todas as alterações no conjunto de dados estão sujeitas a um fluxo de trabalho de aprovação registrado.
 #1.1.4    Nível: 3    Função: D/V
 Verifique se os conjuntos de dados ou subconjuntos estão marcados com marca d'água ou possuem impressão digital onde for viável.

---

### C1.2 Segurança e Integridade dos Dados de Treinamento

Restrinja o acesso aos dados de treinamento, criptografe-os em repouso e em trânsito, e valide sua integridade para evitar adulterações, roubo ou envenenamento de dados.

 #1.2.1    Nível: 1    Função: D/V
 Verifique se os controles de acesso protegem o armazenamento de dados de treinamento e os pipelines.
 #1.2.2    Nível: 2    Função: D/V
 Verifique se todo o acesso aos dados de treinamento é registrado, incluindo usuário, horário e ação.
 #1.2.3    Nível: 2    Função: D/V
 Verifique se os conjuntos de dados de treinamento estão criptografados em trânsito e em repouso, utilizando algoritmos criptográficos padrão da indústria e práticas de gerenciamento de chaves.
 #1.2.4    Nível: 2    Função: D/V
 Verifique se hashes criptográficos ou assinaturas digitais são usados para garantir a integridade dos dados durante o armazenamento e a transferência dos dados de treinamento.
 #1.2.5    Nível: 2    Função: D/V
 Verifique se as técnicas automatizadas de detecção são aplicadas para proteger contra modificações não autorizadas ou corrupção dos dados de treinamento.
 #1.2.6    Nível: 2    Função: D/V
 Verifique se os dados de treinamento obsoletos são eliminados de forma segura ou anonimizados.
 #1.2.7    Nível: 3    Função: D/V
 Verifique se todas as versões do conjunto de dados de treinamento são identificadas de forma única, armazenadas de maneira imutável e auditáveis para suportar reversão e análise forense.

---

### C1.3 Qualidade, Integridade e Segurança da Rotulagem dos Dados de Treinamento

Proteger rótulos e exigir revisão técnica para dados críticos.

 #1.3.1    Nível: 2    Função: D/V
 Verifique se hashes criptográficos ou assinaturas digitais são aplicados aos artefatos de rótulo para garantir sua integridade e autenticidade.
 #1.3.2    Nível: 2    Função: D/V
 Verifique se as interfaces e plataformas de rotulagem aplicam controles de acesso rigorosos, mantêm registros de auditoria à prova de adulteração de todas as atividades de rotulagem e protegem contra modificações não autorizadas.
 #1.3.3    Nível: 3    Função: D/V
 Verifique se as informações sensíveis nos rótulos são redigidas, anonimizadas ou criptografadas ao nível do campo de dados, tanto em repouso quanto em trânsito.

---

### C1.4 Qualidade dos Dados de Treinamento e Garantia de Segurança

Combine validação automatizada, verificações manuais pontuais e remediação registrada para garantir a confiabilidade do conjunto de dados.

 #1.4.1    Nível: 1    Função: D
 Verifique se os testes automatizados detectam erros de formato e valores nulos em cada ingestão ou transformação significativa de dados.
 #1.4.2    Nível: 2    Função: D/V
 Verifique se os pipelines de treinamento e ajuste fino de LLM implementam a detecção de envenenamento e a validação da integridade dos dados (por exemplo, métodos estatísticos, detecção de outliers, análise de embeddings) para identificar potenciais ataques de envenenamento (por exemplo, inversão de rótulos, inserção de gatilhos de backdoor, comandos de troca de função, ataques por instâncias influentes) ou corrupção involuntária dos dados de treinamento.
 #1.4.3    Nível: 3    Função: D/V
 Verifique se defesas apropriadas, como treinamento adversarial (usando exemplos adversariais gerados), aumento de dados com entradas perturbadas ou técnicas de otimização robusta, estão implementadas e ajustadas para os modelos relevantes com base na avaliação de risco.
 #1.4.4    Nível: 2    Função: D/V
 Verifique se os rótulos gerados automaticamente (por exemplo, via LLMs ou supervisão fraca) estão sujeitos a limiares de confiança e verificações de consistência para detectar rótulos alucinatórios, enganosos ou de baixa confiança.
 #1.4.5    Nível: 3    Função: D
 Verifique se os testes automatizados detectam deslocamentos de rótulos em cada ingestão ou transformação significativa de dados.

---

### C1.5 Linhagem e Rastreabilidade de Dados

Rastreie toda a jornada de cada ponto de dado desde a fonte até a entrada do modelo para auditabilidade e resposta a incidentes.

 #1.5.1    Nível: 2    Função: D/V
 Verifique se a linhagem de cada ponto de dados, incluindo todas as transformações, ampliações e mesclagens, está registrada e pode ser reconstruída.
 #1.5.2    Nível: 2    Função: D/V
 Verifique se os registros de linhagem são imutáveis, armazenados de forma segura e acessíveis para auditorias.
 #1.5.3    Nível: 2    Função: D/V
 Verifique se o rastreamento de linhagem cobre dados sintéticos gerados por meio de técnicas de preservação de privacidade ou generativas e se todos os dados sintéticos estão claramente rotulados e distinguíveis dos dados reais em todo o pipeline.

---

### Referências

NIST AI Risk Management Framework
EU AI Act – Article 10: Data & Data Governance
MITRE ATLAS: Adversary Tactics for AI
Survey of ML Bias Mitigation Techniques – MDPI
Data Provenance & Lineage Best Practices – Nightfall AI
Data Labeling Quality Standards – LabelYourData
Training Data Poisoning Guide – Lakera.ai
CISA Advisory: Securing Data for AI Systems
ISO/IEC 23053: AI Management Systems Framework
IBM: What is AI Governance?
Google AI Principles
GDPR & AI Training Data – DataProtectionReport
Supply-Chain Security for AI Data – AppSOC
OpenAI Privacy Center – Data Deletion Controls
Adversarial ML Dataset – Kaggle

## Validação de Entrada do Usuário C2

### Objetivo de Controle

A validação robusta da entrada do usuário é uma defesa de primeira linha contra alguns dos ataques mais prejudiciais aos sistemas de IA. Ataques de injeção de prompt podem substituir instruções do sistema, vazar dados sensíveis ou direcionar o modelo para comportamentos não permitidos. A menos que filtros dedicados e hierarquias de instruções estejam em vigor, pesquisas indicam que jailbreaks "multi-shot" que exploram janelas de contexto muito longas serão eficazes. Além disso, ataques sutis de perturbação adversária — como trocas de homoglifos ou leetspeak — podem mudar silenciosamente as decisões de um modelo.

---

### C2.1 Defesa contra Injeção de Prompt

A injeção de prompt é um dos principais riscos para os sistemas de IA. As defesas contra essa tática empregam uma combinação de filtros de padrões estáticos, classificadores dinâmicos e aplicação da hierarquia das instruções.

 #2.1.1    Nível: 1    Função: D/V
 Verifique se as entradas do usuário são filtradas contra uma biblioteca continuamente atualizada de padrões conhecidos de injeção de prompt (palavras-chave de jailbreak, "ignorar anterior", cadeias de interpretação de papéis, ataques indiretos em HTML/URL).
 #2.1.2    Nível: 1    Função: D/V
 Verifique se o sistema aplica uma hierarquia de instruções na qual as mensagens do sistema ou do desenvolvedor substituem as instruções do usuário, mesmo após a expansão da janela de contexto.
 #2.1.3    Nível: 2    Função: D/V
 Verifique se os testes de avaliação adversarial (por exemplo, prompts "many-shot" de Red Team) são realizados antes de cada lançamento de modelo ou template de prompt, com limites mínimos de taxa de sucesso e bloqueadores automatizados para regressões.
 #2.1.4    Nível: 2    Função: D
 Verifique se os prompts originados de conteúdo de terceiros (páginas da web, PDFs, e-mails) são higienizados em um contexto de análise isolado antes de serem concatenados ao prompt principal.
 #2.1.5    Nível: 3    Função: D/V
 Verifique se todas as atualizações da regra de filtro de prompts, versões do modelo classificador e alterações na lista de bloqueio estão sob controle de versão e são auditáveis.

---

### C2.2 Resistência a Exemplos Adversariais

Modelos de Processamento de Linguagem Natural (PLN) ainda são vulneráveis a perturbações sutis em nível de caractere ou palavra que os humanos frequentemente não percebem, mas que os modelos tendem a classificar incorretamente.

 #2.2.1    Nível: 1    Função: D
 Verifique se as etapas básicas de normalização de entrada (Unicode NFC, mapeamento de homoglifos, remoção de espaços em branco) são executadas antes da tokenização.
 #2.2.2    Nível: 2    Função: D/V
 Verifique se a detecção estatística de anomalias sinaliza entradas com distância de edição incomumente alta em relação às normas linguísticas, tokens repetidos em excesso ou distâncias anormais de embedding.
 #2.2.3    Nível: 2    Função: D
 Verifique se o pipeline de inferência suporta variantes opcionais de modelos reforçados por treinamento adversarial ou camadas de defesa (por exemplo, randomização, destilação defensiva) para pontos finais de alto risco.
 #2.2.4    Nível: 2    Função: V
 Verifique se as entradas adversariais suspeitas estão isoladas, registradas com cargas completas (após a remoção de informações pessoais identificáveis).
 #2.2.5    Nível: 3    Função: D/V
 Verifique se as métricas de robustez (taxa de sucesso dos conjuntos de ataques conhecidos) são monitoradas ao longo do tempo e se as regressões acionam um bloqueio de lançamento.

---

### C2.3 Validação de Esquema, Tipo e Tamanho

Ataques de IA que envolvem entradas malformadas ou de tamanho excessivo podem causar erros de análise, vazamento de comandos entre campos e exaustão de recursos. A aplicação rigorosa do esquema também é um pré-requisito ao realizar chamadas de ferramentas determinísticas.

 #2.3.1    Nível: 1    Função: D
 Verifique se cada endpoint de chamada de API ou função define um esquema de entrada explícito (JSON Schema, Protobuf ou equivalente multimodal) e se as entradas são validadas antes da montagem do prompt.
 #2.3.2    Nível: 1    Função: D/V
 Verifique se as entradas que excedem o limite máximo de tokens ou bytes são rejeitadas com um erro seguro e nunca truncadas silenciosamente.
 #2.3.3    Nível: 2    Função: D/V
 Verifique se as verificações de tipo (por exemplo, intervalos numéricos, valores de enumeração, tipos MIME para imagens/áudio) são aplicadas no lado do servidor, e não apenas no código do cliente.
 #2.3.4    Nível: 2    Função: D
 Verifique se os validadores semânticos (por exemplo, JSON Schema) operam em tempo constante para evitar DoS algorítmico.
 #2.3.5    Nível: 3    Função: V
 Verifique se as falhas de validação são registradas com trechos de carga útil redigidos e códigos de erro inequívocos para auxiliar no processo de triagem de segurança.

---

### C2.4 Triagem de Conteúdo e Política

Os desenvolvedores devem ser capazes de detectar comandos sintaticamente válidos que solicitam conteúdo proibido (como instruções ilícitas, discurso de ódio e texto protegido por direitos autorais) e impedir que eles se propaguem.

 #2.4.1    Nível: 1    Função: D
 Verifique se um classificador de conteúdo (zero shot ou ajustado) avalia cada entrada quanto a violência, automutilação, ódio, conteúdo sexual e solicitações ilegais, com limiares configuráveis.
 #2.4.2    Nível: 1    Função: D/V
 Verifique se as entradas que violam as políticas receberão recusas padronizadas ou conclusões seguras para que não se propaguem para chamadas LLM subsequentes.
 #2.4.3    Nível: 2    Função: D
 Verifique se o modelo de triagem ou o conjunto de regras é re-treinado/atualizado pelo menos trimestralmente, incorporando novos padrões de jailbreak ou bypass de políticas observados.
 #2.4.4    Nível: 2    Função: D
 Verifique se a triagem respeita as políticas específicas do usuário (idade, restrições legais regionais) por meio de regras baseadas em atributos resolvidas no momento da solicitação.
 #2.4.5    Nível: 3    Função: V
 Verifique se os registros de triagem incluem pontuações de confiança do classificador e etiquetas de categoria de política para correlação SOC e reprodução futura de red team.

---

### C2.5 Limitação de Taxa de Entrada e Prevenção de Abuso

Os desenvolvedores devem prevenir abusos, exaustão de recursos e ataques automatizados contra sistemas de IA, limitando as taxas de entrada e detectando padrões anômalos de uso.

 #2.5.1    Nível: 1    Função: D/V
 Verifique se os limites de taxa por usuário, por IP e por chave de API são aplicados para todos os endpoints de entrada.
 #2.5.2    Nível: 2    Função: D/V
 Verifique se os limites de taxa de estouro e sustentada estão ajustados para prevenir ataques DoS e de força bruta.
 #2.5.3    Nível: 2    Função: D/V
 Verifique se padrões de uso anômalos (por exemplo, requisições em rápida sucessão, inundação de entradas) acionam bloqueios automáticos ou escalonamentos.
 #2.5.4    Nível: 3    Função: V
 Verifique se os registros de prevenção de abusos são mantidos e revisados para identificar padrões emergentes de ataque.

---

### C2.6 Validação de Entrada Multimodal

Os sistemas de IA devem incluir validação robusta para entradas não textuais (imagens, áudio, arquivos) para prevenir injeção, evasão ou abuso de recursos.

 #2.6.1    Nível: 1    Função: D
 Verifique se todas as entradas não textuais (imagens, áudio, arquivos) são validadas quanto ao tipo, tamanho e formato antes do processamento.
 #2.6.2    Nível: 2    Função: D/V
 Verifique se os arquivos são escaneados em busca de malware e cargas úteis esteganográficas antes da ingestão.
 #2.6.3    Nível: 2    Função: D/V
 Verifique se as entradas de imagem/áudio são examinadas quanto a perturbações adversariais ou padrões de ataque conhecidos.
 #2.6.4    Nível: 3    Função: V
 Verifique se as falhas na validação de entrada multimodal são registradas e acionam alertas para investigação.

---

### C2.7 Procedência e Atribuição de Entrada

Os sistemas de IA devem suportar auditoria, rastreamento de abuso e conformidade monitorando e etiquetando as origens de todas as entradas dos usuários.

 #2.7.1    Nível: 1    Função: D/V
 Verifique se todas as entradas do usuário estão marcadas com metadados (ID do usuário, sessão, origem, carimbo de data/hora, endereço IP) no momento da ingestão.
 #2.7.2    Nível: 2    Função: D/V
 Verifique se os metadados de proveniência são retidos e auditáveis para todas as entradas processadas.
 #2.7.3    Nível: 2    Função: D/V
 Verifique se as fontes de entrada anômalas ou não confiáveis são sinalizadas e sujeitas a uma análise aprimorada ou bloqueio.

---

### C2.8 Detecção Adaptativa de Ameaças em Tempo Real

Os desenvolvedores devem empregar sistemas avançados de detecção de ameaças para IA que se adaptam a novos padrões de ataque e fornecem proteção em tempo real com correspondência de padrões compilados.

 #2.8.1    Nível: 1    Função: D/V
 Verifique se os padrões de detecção de ameaças são compilados em mecanismos regex otimizados para filtragem em tempo real de alto desempenho com impacto mínimo na latência.
 #2.8.2    Nível: 1    Função: D/V
 Verifique se os sistemas de detecção de ameaças mantêm bibliotecas de padrões separadas para diferentes categorias de ameaças (injeção de prompt, conteúdo prejudicial, dados sensíveis, comandos do sistema).
 #2.8.3    Nível: 2    Função: D/V
 Verifique se a detecção adaptativa de ameaças incorpora modelos de aprendizagem de máquina que atualizam a sensibilidade da ameaça com base na frequência e nas taxas de sucesso dos ataques.
 #2.8.4    Nível: 2    Função: D/V
 Verifique se os feeds de inteligência de ameaças em tempo real atualizam automaticamente as bibliotecas de padrões com novas assinaturas de ataque e IOCs (Indicadores de Comprometimento).
 #2.8.5    Nível: 3    Função: D/V
 Verifique se as taxas de falso positivo na detecção de ameaças são monitoradas continuamente e se a especificidade dos padrões é ajustada automaticamente para minimizar a interferência em casos de uso legítimos.
 #2.8.6    Nível: 3    Função: D/V
 Verifique se a análise contextual de ameaças considera a fonte de entrada, os padrões de comportamento do usuário e o histórico da sessão para melhorar a precisão da detecção.
 #2.8.7    Nível: 3    Função: D/V
 Verifique se as métricas de desempenho da detecção de ameaças (taxa de detecção, latência de processamento, utilização de recursos) estão sendo monitoradas e otimizadas em tempo real.

---

### C2.9 Pipeline de Validação de Segurança Multi-Modal

Os desenvolvedores devem fornecer validação de segurança para texto, imagem, áudio e outras modalidades de entrada de IA com tipos específicos de detecção de ameaças e isolamento de recursos.

 #2.9.1    Nível: 1    Função: D/V
 Verifique se cada modalidade de entrada possui validadores de segurança dedicados com padrões de ameaça documentados (texto: injeção de prompt, imagens: esteganografia, áudio: ataques de espectrograma) e limites de detecção.
 #2.9.2    Nível: 2    Função: D/V
 Verifique se as entradas multimodais são processadas em sandboxes isoladas com limites de recursos definidos (memória, CPU, tempo de processamento) específicos para cada tipo de modalidade e documentados nas políticas de segurança.
 #2.9.3    Nível: 2    Função: D/V
 Verifique se a detecção de ataques cruzados identifica ataques coordenados que abrangem múltiplos tipos de entrada (por exemplo, cargas ocultas esteganográficas em imagens combinadas com injeção de comandos em texto) por meio de regras de correlação e geração de alertas.
 #2.9.4    Nível: 3    Função: D/V
 Verifique se as falhas de validação multimodal disparam logs detalhados, incluindo todas as modalidades de entrada, resultados da validação, pontuações de ameaça e análise de correlação com formatos de log estruturados para integração SIEM.
 #2.9.5    Nível: 3    Função: D/V
 Verifique se os classificadores de conteúdo específicos por modalidade são atualizados de acordo com os cronogramas documentados (mínimo trimestralmente) com novos padrões de ameaça, exemplos adversariais e benchmarks de desempenho mantidos acima dos limiares base.

---

### Referências

LLM01:2025 Prompt Injection – OWASP Top 10 for LLM & Generative AI Security
Generative AI's Biggest Security Flaw Is Not Easy to Fix
Many-shot jailbreaking \ Anthropic
$PDF$ OpenAI GPT-4.5 System Card
Notebook for the CheckThat Lab at CLEF 2024
Mitigate jailbreaks and prompt injections – Anthropic
Chapter 3 MITRE ATT\&CK – Adversarial Model Analysis
OWASP Top 10 for LLM Applications 2025 – WorldTech IT
OWASP Machine Learning Security Top Ten
Few words about AI Security – Jussi Metso
How To Ensure LLM Output Adheres to a JSON Schema | Modelmetry
Easily enforcing valid JSON schema following – API
AI Safety + Cybersecurity R\&D Tracker – Fairly AI
Anthropic makes 'jailbreak' advance to stop AI models producing harmful results
Pattern matching filter rules - IBM
Real-time Threat Detection

## Gerenciamento do Ciclo de Vida do Modelo C3 e Controle de Mudanças

### Objetivo de Controle

Os sistemas de IA devem implementar processos de controle de mudanças que impeçam modificações não autorizadas ou inseguras do modelo de chegar à produção. Esse controle garante a integridade do modelo durante todo o ciclo de vida—desde o desenvolvimento, passando pela implantação, até o descomissionamento—o que possibilita uma resposta rápida a incidentes e mantém a responsabilidade por todas as alterações.

Objetivo Principal de Segurança: Somente modelos autorizados e validados chegam à produção por meio da aplicação de processos controlados que mantêm integridade, rastreabilidade e recuperabilidade.

---

### C3.1 Autorização e Integridade do Modelo

Apenas modelos autorizados com integridade verificada chegam aos ambientes de produção.

 #3.1.1    Nível: 1    Função: D/V
 Verifique se todos os artefatos do modelo (pesos, configurações, tokenizadores) estão assinados criptograficamente por entidades autorizadas antes da implantação.
 #3.1.2    Nível: 1    Função: D/V
 Verifique se a integridade do modelo é validada no momento da implantação e se falhas na verificação de assinatura impedem o carregamento do modelo.
 #3.1.3    Nível: 2    Função: D/V
 Verifique se os registros de proveniência do modelo incluem a identidade da entidade autorizadora, somas de verificação dos dados de treinamento, resultados dos testes de validação com status de aprovação/reprovação e um carimbo de data/hora de criação.
 #3.1.4    Nível: 2    Função: D/V
 Verifique se todos os artefatos do modelo usam versionamento semântico (MAJOR.MINOR.PATCH) com critérios documentados especificando quando cada componente da versão deve ser incrementado.
 #3.1.5    Nível: 2    Função: V
 Verifique se o rastreamento de dependências mantém um inventário em tempo real que possibilite a identificação rápida de todos os sistemas consumidores.

---

### C3.2 Validação e Teste de Modelos

Os modelos devem passar pelas validações definidas de segurança e proteção antes da implantação.

 #3.2.1    Nível: 1    Função: D/V
 Verifique se os modelos passam por testes automatizados de segurança que incluem validação de entrada, sanitização de saída e avaliações de segurança com limites de aprovação/reprovação organizacionais pré-acordados antes da implantação.
 #3.2.2    Nível: 1    Função: D/V
 Verifique se as falhas de validação bloqueiam automaticamente a implantação do modelo após aprovação explícita de substituição por parte de pessoal autorizado pré-designado, com justificativas comerciais documentadas.
 #3.2.3    Nível: 2    Função: V
 Verifique se os resultados do teste estão assinados criptograficamente e vinculados de forma imutável ao hash da versão específica do modelo que está sendo validada.
 #3.2.4    Nível: 2    Função: D/V
 Verifique se as implantações de emergência exigem avaliação de risco de segurança documentada e aprovação de uma autoridade de segurança pré-designada dentro dos prazos previamente acordados.

---

### C3.3 Implantação Controlada e Reversão

As implantações de modelos devem ser controladas, monitoradas e reversíveis.

 #3.3.1    Nível: 1    Função: D
 Verifique se as implantações em produção implementam mecanismos de lançamento gradual (implantações canário, implantações blue-green) com acionadores automáticos de rollback baseados em taxas de erro pré-acordadas, limites de latência ou critérios de alerta de segurança.
 #3.3.2    Nível: 1    Função: D/V
 Verifique se as capacidades de rollback restauram o estado completo do modelo (pesos, configurações, dependências) de forma atômica dentro de janelas de tempo organizacionais predefinidas.
 #3.3.3    Nível: 2    Função: D/V
 Verifique se os processos de implantação validam assinaturas criptográficas e calculam checksums de integridade antes da ativação do modelo, falhando a implantação em qualquer incompatibilidade.
 #3.3.4    Nível: 2    Função: D/V
 Verifique se as capacidades de desligamento de emergência do modelo podem desativar os endpoints do modelo dentro dos tempos de resposta pré-definidos por meio de disjuntores automáticos ou interruptores manuais de desligamento.
 #3.3.5    Nível: 2    Função: V
 Verifique se os artefatos de reversão (versões anteriores do modelo, configurações, dependências) são mantidos conforme as políticas organizacionais, utilizando armazenamento imutável para resposta a incidentes.

---

### C3.4 Responsabilidade por Alterações e Auditoria

Todas as alterações no ciclo de vida do modelo devem ser rastreáveis e auditáveis.

 #3.4.1    Nível: 1    Função: V
 Verifique se todas as alterações no modelo (implantação, configuração, desativação) geram registros de auditoria imutáveis, incluindo um carimbo de data/hora, a identidade autenticada do ator, um tipo de alteração e os estados anterior/depois.
 #3.4.2    Nível: 2    Função: D/V
 Verifique se o acesso ao log de auditoria requer autorização apropriada e se todas as tentativas de acesso são registradas com a identidade do usuário e um carimbo de data/hora.
 #3.4.3    Nível: 2    Função: D/V
 Verifique se os templates de prompt e as mensagens do sistema estão versionados em repositórios git com revisão de código obrigatória e aprovação de revisores designados antes da implantação.
 #3.4.4    Nível: 2    Função: V
 Verifique se os registros de auditoria incluem detalhes suficientes (hashes do modelo, instantâneos de configuração, versões de dependências) para permitir a reconstrução completa do estado do modelo para qualquer timestamp dentro do período de retenção.

---

### C3.5 Práticas de Desenvolvimento Seguro

Os processos de desenvolvimento e treinamento do modelo devem seguir práticas seguras para evitar comprometimentos.

 #3.5.1    Nível: 1    Função: D
 Verifique se os ambientes de desenvolvimento, teste e produção do modelo estão separados fisicamente ou logicamente. Eles não devem compartilhar infraestrutura, devem ter controles de acesso distintos e armazenamentos de dados isolados.
 #3.5.2    Nível: 1    Função: D
 Verifique se o treinamento e o ajuste fino do modelo ocorrem em ambientes isolados com acesso de rede controlado.
 #3.5.3    Nível: 1    Função: D/V
 Verifique se as fontes de dados de treinamento são validadas por meio de verificações de integridade e autenticadas por fontes confiáveis com cadeia de custódia documentada antes do uso no desenvolvimento do modelo.
 #3.5.4    Nível: 2    Função: D
 Verifique se os artefatos de desenvolvimento do modelo (hiperparâmetros, scripts de treinamento, arquivos de configuração) estão armazenados no controle de versão e exigem aprovação por revisão de pares antes de serem usados no treinamento.

---

### C3.6 Aposentadoria e Descomissionamento do Modelo

Os modelos devem ser desativados com segurança quando não forem mais necessários ou quando forem identificados problemas de segurança.

 #3.6.1    Nível: 1    Função: D
 Verifique se os processos de aposentadoria de modelos escaneiam automaticamente os gráficos de dependência, identificam todos os sistemas consumidores e fornecem períodos de aviso prévio previamente acordados antes da desativação.
 #3.6.2    Nível: 1    Função: D/V
 Verifique se os artefatos do modelo aposentado são apagados de forma segura usando apagamento criptográfico ou sobregravação múltipla conforme as políticas documentadas de retenção de dados, com certificados de destruição verificados.
 #3.6.3    Nível: 2    Função: V
 Verifique se os eventos de aposentadoria do modelo são registrados com carimbo de data e hora e identidade do ator, e se as assinaturas do modelo são revogadas para evitar reutilização.
 #3.6.4    Nível: 2    Função: D/V
 Verifique se a aposentadoria emergencial do modelo pode desabilitar o acesso ao modelo dentro dos prazos pré-estabelecidos de resposta a emergências por meio de desligamentos automáticos caso vulnerabilidades críticas de segurança sejam descobertas.

---

### Referências

MLOps Principles
Securing AI/ML Ops – Cisco.com
Audit logs security: cryptographically signed tamper-proof logs
Machine Learning Model Versioning: Top Tools & Best Practices
AI Hygiene Starts with Models and Data Loaders – SEI Blog
How to handle versioning and rollback of a deployed ML model?
Reinforcement fine-tuning – OpenAI API
Auditing Machine Learning models: Governance, Data Security and …
Adversarial Training to Improve Model Robustness
What is AI adversarial robustness? – IBM Research
Exploring Data Provenance: Ensuring Data Integrity and Authenticity
MITRE ATLAS
AWS Prescriptive Guidance – Best practices for retiring applications …

## Infraestrutura C4, Configuração e Segurança de Implantação

### Objetivo de Controle

A infraestrutura de IA deve ser reforçada contra escalonamento de privilégios, adulteração da cadeia de suprimentos e movimentação lateral por meio de configuração segura, isolamento em tempo de execução, pipelines de implantação confiáveis e monitoramento abrangente. Apenas componentes e configurações da infraestrutura autorizados e validados chegam à produção por meio de processos controlados que mantêm a segurança, integridade e auditabilidade.

Objetivo Principal de Segurança: Apenas componentes de infraestrutura assinados criptograficamente e verificados quanto a vulnerabilidades chegam à produção por meio de pipelines de validação automatizados que aplicam políticas de segurança e mantêm trilhas de auditoria imutáveis.

---

### C4.1 Isolamento do Ambiente de Execução

Evite fugas de contêiner e escalonamento de privilégios por meio de primitivas de isolamento em nível de kernel e controles de acesso obrigatórios.

 #4.1.1    Nível: 1    Função: D/V
 Verifique se todos os contêineres de IA removem TODAS as capacidades do Linux, exceto CAP_SETUID, CAP_SETGID e as capacidades explicitamente requeridas documentadas nas linhas de base de segurança.
 #4.1.2    Nível: 1    Função: D/V
 Verifique se os perfis seccomp bloqueiam todas as syscalls, exceto aquelas nas listas de permissões pré-aprovadas, com violações terminando o contêiner e gerando alertas de segurança.
 #4.1.3    Nível: 2    Função: D/V
 Verifique se as cargas de trabalho de IA são executadas com sistemas de arquivos raiz somente leitura, tmpfs para dados temporários e volumes nomeados para dados persistentes com opções de montagem noexec aplicadas.
 #4.1.4    Nível: 2    Função: D/V
 Verifique se o monitoramento em tempo real baseado em eBPF (Falco, Tetragon ou equivalente) detecta tentativas de escalonamento de privilégios e encerra automaticamente os processos infratores dentro dos requisitos de tempo de resposta organizacional.
 #4.1.5    Nível: 3    Função: D/V
 Verifique se as cargas de trabalho de IA de alto risco são executadas em ambientes isolados por hardware (Intel TXT, AMD SVM ou nós bare-metal dedicados) com verificação de atestado.

---

### C4.2 Pipelines Seguros de Build e Deployment

Garanta a integridade criptográfica e a segurança da cadeia de suprimentos por meio de builds reproduzíveis e artefatos assinados.

 #4.2.1    Nível: 1    Função: D/V
 Verifique se a infraestrutura como código é analisada com ferramentas (tfsec, Checkov ou Terrascan) a cada commit, bloqueando merges que contenham achados de severidade CRÍTICA ou ALTA.
 #4.2.2    Nível: 1    Função: D/V
 Verifique se as construções de contêiner são reproduzíveis com hashes SHA256 idênticos entre as construções e gere atestações de proveniência no Nível 3 SLSA assinadas com Sigstore.
 #4.2.3    Nível: 2    Função: D/V
 Verifique se as imagens de contêiner incorporam SBOMs CycloneDX ou SPDX e são assinadas com Cosign antes do push para o registro, rejeitando imagens não assinadas na implantação.
 #4.2.4    Nível: 2    Função: D/V
 Verifique se os pipelines de CI/CD usam tokens OIDC do HashiCorp Vault, funções IAM da AWS ou Identidade Gerenciada do Azure com tempos de vida que não excedam os limites da política de segurança organizacional.
 #4.2.5    Nível: 2    Função: D/V
 Verifique se as assinaturas Cosign e a proveniência SLSA são validadas durante o processo de implantação antes da execução do contêiner e se erros de verificação fazem a implantação falhar.
 #4.2.6    Nível: 2    Função: D/V
 Verifique se os ambientes de build são executados em contêineres efêmeros ou VMs sem armazenamento persistente e com isolamento de rede em relação às VPCs de produção.

---

### C4.3 Segurança de Rede e Controle de Acesso

Implemente redes de confiança zero com políticas de negação padrão e comunicações criptografadas.

 #4.3.1    Nível: 1    Função: D/V
 Verifique se as NetworkPolicies do Kubernetes ou qualquer equivalente implementam a política padrão de negar (default-deny) o tráfego de entrada/saída com regras de permissão explícitas para as portas necessárias (443, 8080, etc.).
 #4.3.2    Nível: 1    Função: D/V
 Verifique se SSH (porta 22), RDP (porta 3389) e os endpoints de metadados da nuvem (169.254.169.254) estão bloqueados ou exigem autenticação baseada em certificado.
 #4.3.3    Nível: 2    Função: D/V
 Verifique se o tráfego de saída é filtrado através de proxies HTTP/HTTPS (Squid, Istio ou gateways NAT em nuvem) com listas de permissão de domínios e se as solicitações bloqueadas são registradas.
 #4.3.4    Nível: 2    Função: D/V
 Verifique se a comunicação entre serviços utiliza TLS mútuo com certificados rotacionados de acordo com a política organizacional e validação de certificados aplicada (sem uso de flags de ignorar-verificação).
 #4.3.5    Nível: 2    Função: D/V
 Verifique se a infraestrutura de IA opera em VPCs/VNets dedicadas sem acesso direto à internet e se comunica apenas por meio de gateways NAT ou hosts bastião.

---

### C4.4 Gestão de Segredos e Chaves Criptográficas

Proteja as credenciais por meio de armazenamento suportado por hardware e rotação automatizada com acesso de confiança zero.

 #4.4.1    Nível: 1    Função: D/V
 Verifique se os segredos estão armazenados no HashiCorp Vault, AWS Secrets Manager, Azure Key Vault ou Google Secret Manager com criptografia em repouso usando AES-256.
 #4.4.2    Nível: 1    Função: D/V
 Verifique se as chaves criptográficas são geradas em HSMs de Nível 2 FIPS 140-2 (AWS CloudHSM, Azure Dedicated HSM) com rotação de chaves de acordo com a política criptográfica organizacional.
 #4.4.3    Nível: 2    Função: D/V
 Verifique se a rotação de segredos é automatizada com implantação sem tempo de inatividade e rotação imediata acionada por mudanças de pessoal ou incidentes de segurança.
 #4.4.4    Nível: 2    Função: D/V
 Verifique se as imagens de contêiner são verificadas com ferramentas (GitLeaks, TruffleHog ou detect-secrets), bloqueando builds que contenham chaves de API, senhas ou certificados.
 #4.4.5    Nível: 2    Função: D/V
 Verifique se o acesso ao segredo de produção requer MFA com tokens de hardware (YubiKey, FIDO2) e é registrado por logs de auditoria imutáveis com identidades de usuários e carimbos de data/hora.
 #4.4.6    Nível: 2    Função: D/V
 Verifique se os segredos são injetados por meio de segredos do Kubernetes, volumes montados ou containers init e assegure que os segredos nunca sejam incorporados em variáveis de ambiente ou imagens.

---

### C4.5 Sandboxing e Validação de Carga de Trabalho de IA

Isole modelos de IA não confiáveis em ambientes seguros com análise comportamental abrangente.

 #4.5.1    Nível: 1    Função: D/V
 Verifique se os modelos de IA externos são executados em gVisor, microVMs (como Firecracker, CrossVM) ou contêineres Docker com as opções --security-opt=no-new-privileges e --read-only.
 #4.5.2    Nível: 1    Função: D/V
 Verifique se os ambientes sandbox não possuem conectividade de rede (--network=none) ou possuem apenas acesso ao localhost, com todas as solicitações externas bloqueadas pelas regras do iptables.
 #4.5.3    Nível: 2    Função: D/V
 Verifique se a validação do modelo de IA inclui testes automatizados de red team com cobertura de teste definida pela organização e análise comportamental para detecção de backdoors.
 #4.5.4    Nível: 2    Função: D/V
 Verifique se, antes de um modelo de IA ser promovido para produção, seus resultados na sandbox são assinados criptograficamente por pessoal de segurança autorizado e armazenados em logs de auditoria imutáveis.
 #4.5.5    Nível: 2    Função: D/V
 Verifique se os ambientes sandbox são destruídos e recriados a partir de imagens base entre as avaliações, com limpeza completa do sistema de arquivos e da memória.

---

### C4.6 Monitoramento de Segurança da Infraestrutura

Realize a varredura e monitoramento contínuos da infraestrutura com remediação automatizada e alertas em tempo real.

 #4.6.1    Nível: 1    Função: D/V
 Verifique se as imagens de contêiner são analisadas de acordo com os cronogramas organizacionais, com vulnerabilidades CRÍTICAS bloqueando a implantação com base nos limites de risco organizacionais.
 #4.6.2    Nível: 1    Função: D/V
 Verifique se a infraestrutura atende aos CIS Benchmarks ou controles NIST 800-53 com limites de conformidade definidos pela organização e remediação automatizada para verificações que falharem.
 #4.6.3    Nível: 2    Função: D/V
 Verifique se as vulnerabilidades de gravidade ALTA estão corrigidas conforme os prazos de gerenciamento de risco organizacional, com procedimentos de emergência para CVEs ativamente explorados.
 #4.6.4    Nível: 2    Função: V
 Verifique se os alertas de segurança se integram com plataformas SIEM (Splunk, Elastic ou Sentinel) usando os formatos CEF ou STIX/TAXII com enriquecimento automatizado.
 #4.6.5    Nível: 3    Função: V
 Verifique se as métricas da infraestrutura são exportadas para sistemas de monitoramento (Prometheus, DataDog) com painéis SLA e relatórios executivos.
 #4.6.6    Nível: 2    Função: D/V
 Verifique se o desvio de configuração é detectado usando ferramentas (Chef InSpec, AWS Config) de acordo com os requisitos de monitoramento da organização, com rollback automático para alterações não autorizadas.

---

### C4.7 Gerenciamento de Recursos da Infraestrutura de IA

Prevenir ataques de exaustão de recursos e garantir a alocação justa de recursos por meio de cotas e monitoramento.

 #4.7.1    Nível: 1    Função: D/V
 Verifique se a utilização de GPU/TPU é monitorada com alertas acionados em limiares definidos pela organização e se o escalonamento automático ou balanceamento de carga é ativado com base nas políticas de gerenciamento de capacidade.
 #4.7.2    Nível: 1    Função: D/V
 Verifique se as métricas de carga de trabalho de IA (latência de inferência, taxa de transferência, taxas de erro) são coletadas de acordo com os requisitos de monitoramento organizacional e correlacionadas com a utilização da infraestrutura.
 #4.7.3    Nível: 2    Função: D/V
 Verifique se os ResourceQuotas do Kubernetes ou equivalente limitam cargas de trabalho individuais de acordo com as políticas organizacionais de alocação de recursos, com limites rígidos aplicados.
 #4.7.4    Nível: 2    Função: V
 Verifique se o monitoramento de custos acompanha os gastos por carga de trabalho/locatário com alertas baseados em limites orçamentários organizacionais e controles automáticos para excedentes de orçamento.
 #4.7.5    Nível: 3    Função: V
 Verifique se o planejamento de capacidade utiliza dados históricos com períodos de previsão definidos pela organização e provisionamento automático de recursos com base nos padrões de demanda.
 #4.7.6    Nível: 2    Função: D/V
 Verifique se o esgotamento de recursos aciona os disjuntores de acordo com os requisitos de resposta organizacional, incluindo limitação de taxa baseada em políticas de capacidade e isolamento de carga de trabalho.

---

### C4.8 Separação de Ambiente e Controles de Promoção

Implemente limites rigorosos no ambiente com portas de promoção automatizadas e validação de segurança.

 #4.8.1    Nível: 1    Função: D/V
 Verifique se os ambientes de desenvolvimento/teste/produção estão operando em VPCs/VNets separadas, sem funções IAM, grupos de segurança ou conectividade de rede compartilhados.
 #4.8.2    Nível: 1    Função: D/V
 Verifique se a promoção do ambiente requer aprovação de pessoal autorizado definido pela organização com assinaturas criptográficas e trilhas de auditoria imutáveis.
 #4.8.3    Nível: 2    Função: D/V
 Verifique se os ambientes de produção bloqueiam o acesso SSH, desabilitam pontos de extremidade de depuração e exigem solicitações de alteração com requisitos de aviso prévio organizacional, exceto em emergências.
 #4.8.4    Nível: 2    Função: D/V
 Verifique se as alterações de infraestrutura-como-código exigem revisão por pares com testes automatizados e varredura de segurança antes da fusão para o branch principal.
 #4.8.5    Nível: 2    Função: D/V
 Verifique se os dados não produtivos estão anonimizados de acordo com os requisitos organizacionais de privacidade, geração de dados sintéticos ou mascaramento completo de dados com remoção de PII verificada.
 #4.8.6    Nível: 2    Função: D/V
 Verifique se os portões de promoção incluem testes de segurança automatizados (SAST, DAST, varredura de contêiner) com zero achados CRÍTICOS exigidos para aprovação.

---

### C4.9 Backup e Recuperação da Infraestrutura

Garanta a resiliência da infraestrutura por meio de backups automatizados, procedimentos de recuperação testados e capacidades de recuperação de desastres.

 #4.9.1    Nível: 1    Função: D/V
 Verifique se as configurações da infraestrutura são respaldadas de acordo com os cronogramas de backup da organização para regiões geograficamente separadas, com a implementação da estratégia de backup 3-2-1.
 #4.9.2    Nível: 2    Função: D/V
 Verifique se os sistemas de backup operam em redes isoladas com credenciais separadas e armazenamento isolado (air-gapped) para proteção contra ransomware.
 #4.9.3    Nível: 2    Função: V
 Verifique se os procedimentos de recuperação são testados e validados por meio de testes automatizados de acordo com os cronogramas organizacionais, com metas de RTO e RPO atendendo aos requisitos da organização.
 #4.9.4    Nível: 3    Função: V
 Verifique se a recuperação de desastres inclui runbooks específicos para IA com restauração de pesos do modelo, reconstrução do cluster GPU e mapeamento de dependências de serviço.

---

### C4.10 Conformidade e Governança da Infraestrutura

Mantenha a conformidade regulatória por meio de avaliação contínua, documentação e controles automatizados.

 #4.10.1    Nível: 2    Função: D/V
 Verifique se a conformidade da infraestrutura é avaliada de acordo com os cronogramas organizacionais em relação aos controles SOC 2, ISO 27001 ou FedRAMP, com coleta automatizada de evidências.
 #4.10.2    Nível: 2    Função: V
 Verifique se a documentação da infraestrutura inclui diagramas de rede, mapas de fluxo de dados e modelos de ameaça atualizados de acordo com os requisitos de gerenciamento de mudanças organizacionais.
 #4.10.3    Nível: 3    Função: D/V
 Verifique se as mudanças na infraestrutura passam por uma avaliação automática de impacto de conformidade com fluxos de trabalho de aprovação regulatória para modificações de alto risco.

---

### C4.11 Segurança de Hardware de IA

Proteja os componentes de hardware específicos para IA, incluindo GPUs, TPUs e aceleradores especializados de IA.

 #4.11.1    Nível: 2    Função: D/V
 Verifique se o firmware do acelerador de IA (BIOS da GPU, firmware do TPU) é verificado com assinaturas criptográficas e atualizado de acordo com os cronogramas de gerenciamento de patches da organização.
 #4.11.2    Nível: 2    Função: D/V
 Verifique que, antes da execução da carga de trabalho, a integridade do acelerador de IA seja validada por atestado de hardware usando TPM 2.0, Intel TXT ou AMD SVM.
 #4.11.3    Nível: 2    Função: D/V
 Verifique se a memória da GPU está isolada entre as cargas de trabalho usando SR-IOV, MIG (GPU Multi-Instância) ou particionamento de hardware equivalente com sanitização de memória entre os trabalhos.
 #4.11.4    Nível: 3    Função: V
 Verifique se a cadeia de suprimentos de hardware de IA inclui verificação de proveniência com certificados do fabricante e validação de embalagem à prova de violação.
 #4.11.5    Nível: 3    Função: D/V
 Verifique se os módulos de segurança de hardware (HSMs) protegem os pesos do modelo de IA e as chaves criptográficas com certificação FIPS 140-2 Nível 3 ou Common Criteria EAL4+.

---

### C4.12 Infraestrutura de IA de Borda e Distribuída

Implantações seguras de IA distribuída incluindo computação de borda, aprendizado federado e arquiteturas multi-site.

 #4.12.1    Nível: 2    Função: D/V
 Verifique se os dispositivos de edge AI autenticam-se na infraestrutura central usando TLS mútuo com certificados de dispositivo rotacionados de acordo com a política organizacional de gerenciamento de certificados.
 #4.12.2    Nível: 2    Função: D/V
 Verifique se os dispositivos de borda implementam boot seguro com assinaturas verificadas e proteção contra reversão, prevenindo ataques de downgrade de firmware.
 #4.12.3    Nível: 3    Função: D/V
 Verifique se a coordenação de IA distribuída utiliza algoritmos de consenso tolerantes a falhas bizantinas com validação dos participantes e detecção de nós maliciosos.
 #4.12.4    Nível: 3    Função: D/V
 Verifique se a comunicação edge-to-cloud inclui limitação de largura de banda, compressão de dados e capacidades de operação offline com armazenamento local seguro.

---

### C4.13 Segurança de Infraestrutura Multi-Nuvem e Híbrida

Proteja cargas de trabalho de IA em vários provedores de nuvem e implantações híbridas de nuvem no local.

 #4.13.1    Nível: 2    Função: D/V
 Verifique se as implantações de IA multi-nuvem utilizam federação de identidade agnóstica à nuvem (OIDC, SAML) com gerenciamento centralizado de políticas entre os provedores.
 #4.13.2    Nível: 2    Função: D/V
 Verifique se a transferência de dados entre nuvens utiliza criptografia de ponta a ponta com chaves gerenciadas pelo cliente e controles de residência de dados aplicados conforme a jurisdição.
 #4.13.3    Nível: 2    Função: D/V
 Verifique se as cargas de trabalho de IA em nuvem híbrida implementam políticas de segurança consistentes nos ambientes locais e na nuvem, com monitoramento e alertas unificados.
 #4.13.4    Nível: 3    Função: V
 Verifique se a prevenção de bloqueio ao fornecedor de nuvem inclui infraestrutura como código portátil, APIs padronizadas e capacidades de exportação de dados com ferramentas de conversão de formato.
 #4.13.5    Nível: 3    Função: V
 Verifique se a otimização de custos multi-nuvem inclui controles de segurança que previnem o aumento descontrolado de recursos, bem como cobranças não autorizadas por transferência de dados entre nuvens.

---

### C4.14 Segurança em Automação de Infraestrutura e GitOps

Automatize pipelines de infraestrutura segura e fluxos de trabalho GitOps para gerenciamento de infraestrutura de IA.

 #4.14.1    Nível: 2    Função: D/V
 Verifique se os repositórios GitOps exigem commits assinados com chaves GPG e regras de proteção de branch que impedem pushs diretos para as branches principais.
 #4.14.2    Nível: 2    Função: D/V
 Verifique se a automação da infraestrutura inclui detecção de desvio com capacidades automáticas de remediação e reversão acionadas conforme os requisitos de resposta organizacional para mudanças não autorizadas.
 #4.14.3    Nível: 2    Função: D/V
 Verifique se o provisionamento automatizado de infraestrutura inclui a validação da política de segurança com bloqueio de implantação para configurações não conforme.
 #4.14.4    Nível: 2    Função: D/V
 Verifique se os segredos da automação de infraestrutura são gerenciados por meio de operadores externos de segredos (External Secrets Operator, Bank-Vaults) com rotação automática.
 #4.14.5    Nível: 3    Função: V
 Verifique se a infraestrutura autocurativa inclui correlação de eventos de segurança com resposta automática a incidentes e fluxos de trabalho de notificação para as partes interessadas.

---

### C4.15 Segurança de Infraestrutura Resistente a Quantum

Prepare a infraestrutura de IA para ameaças da computação quântica por meio da criptografia pós-quântica e protocolos seguros contra quânticos.

 #4.15.1    Nível: 3    Função: D/V
 Verifique se a infraestrutura de IA implementa algoritmos criptográficos pós-quânticos aprovados pelo NIST (CRYSTALS-Kyber, CRYSTALS-Dilithium, SPHINCS+) para troca de chaves e assinaturas digitais.
 #4.15.2    Nível: 3    Função: D/V
 Verifique se os sistemas de distribuição quântica de chaves (QKD) estão implementados para comunicações de IA de alta segurança com protocolos de gerenciamento de chaves quânticas seguras.
 #4.15.3    Nível: 3    Função: D/V
 Verifique se os frameworks de agilidade criptográfica permitem migração rápida para novos algoritmos pós-quânticos com rotação automatizada de certificados e chaves.
 #4.15.4    Nível: 3    Função: V
 Verifique se a modelagem de ameaça quântica avalia a vulnerabilidade da infraestrutura de IA a ataques quânticos com cronogramas de migração documentados e avaliações de risco.
 #4.15.5    Nível: 3    Função: D/V
 Verifique se os sistemas criptográficos híbridos clássicos-quânticos oferecem defesa em profundidade durante o período de transição quântica com monitoramento de desempenho.

---

### C4.16 Computação Confidencial e Enclaves Seguros

Proteja cargas de trabalho de IA e pesos de modelos usando ambientes de execução confiáveis baseados em hardware e tecnologias de computação confidencial.

 #4.16.1    Nível: 3    Função: D/V
 Verifique se os modelos de IA sensíveis são executados dentro de enclaves Intel SGX, AMD SEV-SNP ou ARM TrustZone com memória criptografada e verificação de atestação.
 #4.16.2    Nível: 3    Função: D/V
 Verifique se os contêiners confidenciais (Kata Containers, gVisor com computação confidencial) isolam cargas de trabalho de IA com criptografia de memória aplicada por hardware.
 #4.16.3    Nível: 3    Função: D/V
 Verifique se a atestação remota valida a integridade do enclave antes de carregar os modelos de IA com prova criptográfica da autenticidade do ambiente de execução.
 #4.16.4    Nível: 3    Função: D/V
 Verifique se os serviços confidenciais de inferência de IA impedem a extração do modelo por meio de computação criptografada com pesos do modelo selados e execução protegida.
 #4.16.5    Nível: 3    Função: D/V
 Verifique se a orquestração do ambiente de execução confiável gerencia o ciclo de vida do enclave seguro com atestado remoto e canais de comunicação criptografados.
 #4.16.6    Nível: 3    Função: D/V
 Verifique se a computação multipartidária segura (SMPC) permite o treinamento colaborativo de IA sem expor conjuntos de dados individuais ou parâmetros do modelo.

---

### C4.17 Infraestrutura de Conhecimento Zero

Implemente sistemas de prova de conhecimento zero para verificação e autenticação de IA que preservem a privacidade sem revelar informações sensíveis.

 #4.17.1    Nível: 3    Função: D/V
 Verifique se as provas de conhecimento zero (ZK-SNARKs, ZK-STARKs) verificam a integridade do modelo de IA e a proveniência do treinamento sem expor os pesos do modelo ou os dados de treinamento.
 #4.17.2    Nível: 3    Função: D/V
 Verifique se os sistemas de autenticação baseados em ZK permitem a verificação de usuários preservando a privacidade para serviços de IA sem revelar informações relacionadas à identidade.
 #4.17.3    Nível: 3    Função: D/V
 Verifique se os protocolos de interseção privada de conjuntos (PSI) permitem a correspondência segura de dados para IA federada sem expor conjuntos de dados individuais.
 #4.17.4    Nível: 3    Função: D/V
 Verifique se os sistemas de aprendizado de máquina com conhecimento zero (ZKML) permitem inferências de IA verificáveis com prova criptográfica de computação correta.
 #4.17.5    Nível: 3    Função: D/V
 Verifique que os ZK-rollups oferecem processamento de transações de IA escalável e que preserva a privacidade, com verificação em lote e redução da sobrecarga computacional.

---

### C4.18 Prevenção de Ataques por Canal Lateral

Proteja a infraestrutura de IA contra ataques de canal lateral baseados em tempo, energia, eletromagnéticos e cache que poderiam vazar informações sensíveis.

 #4.18.1    Nível: 3    Função: D/V
 Verifique se o tempo de inferência da IA é normalizado usando algoritmos de tempo constante e preenchimento para evitar ataques de extração de modelo baseados em tempo.
 #4.18.2    Nível: 3    Função: D/V
 Verifique se a proteção contra análise de consumo de energia inclui injeção de ruído, filtragem da linha de energia e padrões de execução randomizados para hardware de IA.
 #4.18.3    Nível: 3    Função: D/V
 Verifique se a mitigação de canal lateral baseada em cache usa particionamento de cache, randomização e instruções de flush para prevenir o vazamento de informações.
 #4.18.4    Nível: 3    Função: D/V
 Verifique se a proteção contra emanação eletromagnética inclui blindagem, filtragem de sinais e processamento randomizado para impedir ataques do tipo TEMPEST.
 #4.18.5    Nível: 3    Função: D/V
 Verifique se as defesas contra canal lateral microarquitetônico incluem controles de execução especulativa e ofuscação de padrão de acesso à memória.

---

### C4.19 Segurança de Hardware Neuromórfico e de IA Especializada

Arquiteturas de hardware emergentes de IA seguras, incluindo chips neuromórficos, FPGAs, ASICs personalizados e sistemas de computação óptica.

 #4.19.1    Nível: 3    Função: D/V
 Verifique se a segurança do chip neuromórfico inclui criptografia de padrão de disparo, proteção do peso sináptico e validação da regra de aprendizado baseada em hardware.
 #4.19.2    Nível: 3    Função: D/V
 Verifique se os aceleradores de IA baseados em FPGA implementam criptografia de bitstream, mecanismos anti-violação e carregamento seguro de configuração com atualizações autenticadas.
 #4.19.3    Nível: 3    Função: D/V
 Verifique se a segurança do ASIC personalizado inclui processadores de segurança integrados no chip, raiz de confiança de hardware e armazenamento seguro de chaves com detecção de violação.
 #4.19.4    Nível: 3    Função: D/V
 Verifique se os sistemas de computação óptica implementam criptografia óptica segura contra ataques quânticos, comutação fotônica segura e processamento protegido de sinais ópticos.
 #4.19.5    Nível: 3    Função: D/V
 Verifique se os chips híbridos analógico-digitais de IA incluem computação analógica segura, armazenamento protegido de pesos e conversão autenticada de analógico para digital.

---

### C4.20 Infraestrutura de Computação que Preserva a Privacidade

Implemente controles de infraestrutura para computação que preserva a privacidade a fim de proteger dados sensíveis durante o processamento e análise de IA.

 #4.20.1    Nível: 3    Função: D/V
 Verifique se a infraestrutura de criptografia homomórfica permite o processamento criptografado em cargas de trabalho sensíveis de IA com verificação de integridade criptográfica e monitoramento de desempenho.
 #4.20.2    Nível: 3    Função: D/V
 Verifique se os sistemas de recuperação privada de informação permitem consultas a bancos de dados sem revelar os padrões de consulta, com proteção criptográfica dos padrões de acesso.
 #4.20.3    Nível: 3    Função: D/V
 Verifique se os protocolos de computação multipartidária segura permitem inferência de IA preservando a privacidade, sem expor entradas individuais ou cálculos intermediários.
 #4.20.4    Nível: 3    Função: D/V
 Verifique se o gerenciamento de chaves com preservação da privacidade inclui geração distribuída de chaves, criptografia por limiar e rotação segura de chaves com proteção baseada em hardware.
 #4.20.5    Nível: 3    Função: D/V
 Verifique que o desempenho da computação que preserva a privacidade seja otimizado por meio de agrupamento, armazenamento em cache e aceleração de hardware, ao mesmo tempo em que mantém as garantias de segurança criptográfica.

---

### C4.15 Segurança de Integração em Nuvem do Framework de Agentes e Implantação Híbrida

Controles de segurança para frameworks de agentes integrados à nuvem com arquiteturas híbridas on-premises/nuvem.

 #4.15.1    Nível: 1    Função: D/V
 Verifique se a integração de armazenamento em nuvem utiliza criptografia de ponta a ponta com gerenciamento de chaves controlado pelo agente.
 #4.15.2    Nível: 2    Função: D/V
 Verifique se os limites de segurança do deployment híbrido estão claramente definidos com canais de comunicação criptografados.
 #4.15.3    Nível: 2    Função: D/V
 Verifique se o acesso aos recursos em nuvem inclui verificação de confiança zero com autenticação contínua.
 #4.15.4    Nível: 3    Função: D/V
 Verifique se os requisitos de residência de dados são aplicados por meio de atestação criptográfica dos locais de armazenamento.
 #4.15.5    Nível: 3    Função: D/V
 Verifique se as avaliações de segurança do provedor de nuvem incluem modelagem de ameaças específica para agentes e avaliação de riscos.

---

### Referências

NIST Cybersecurity Framework 2.0
CIS Controls v8
OWASP Container Security Verification Standard
Kubernetes Security Best Practices
SLSA Supply Chain Security Framework
NIST SP 800-190: Application Container Security Guide
Cloud Security Alliance: Cloud Controls Matrix
ENISA: Secure Infrastructure Design
NIST SP 800-53: Security Controls for Federal Information Systems
ISO 27001:2022 Information Security Management
NIST AI Risk Management Framework
CIS Kubernetes Benchmark
FIPS 140-2 Security Requirements
NIST SP 800-207: Zero Trust Architecture
IEEE 2857: Privacy Engineering for AI Systems
NIST SP 800-161: Cybersecurity Supply Chain Risk Management
NIST Post-Quantum Cryptography Standards
Intel SGX Developer Guide
AMD SEV-SNP White Paper
ARM TrustZone Technology
ZK-SNARKs: A Gentle Introduction
NIST SP 800-57: Cryptographic Key Management
Side-Channel Attack Countermeasures
Neuromorphic Computing Security Challenges
FPGA Security: Fundamentals, Evaluation, and Countermeasures
Microsoft SEAL: Homomorphic Encryption Library
HElib: Homomorphic Encryption Library
PALISADE Lattice Cryptography Library
Differential Privacy: A Survey of Results
Secure Aggregation for Federated Learning
Private Information Retrieval: Concepts and Constructions

## Controle de Acesso C5 e Identidade para Componentes e Usuários de IA

### Objetivo de Controle

O controle de acesso eficaz para sistemas de IA requer uma gestão robusta de identidade, autorização ciente do contexto e aplicação em tempo de execução seguindo os princípios de confiança zero. Esses controles garantem que humanos, serviços e agentes autônomos interajam apenas com modelos, dados e recursos computacionais dentro de escopos explicitamente concedidos, com capacidades contínuas de verificação e auditoria.

---

### C5.1 Gerenciamento de Identidade e Autenticação

Estabelecer identidades respaldadas criptograficamente para todas as entidades com autenticação multi-fator para operações privilegiadas.

 #5.1.1    Nível: 1    Função: D/V
 Verifique se todos os usuários humanos e principais de serviço autenticam-se por meio de um provedor de identidade corporativo centralizado (IdP) usando protocolos OIDC/SAML com mapeamentos únicos de identidade para token (sem contas ou credenciais compartilhadas).
 #5.1.2    Nível: 1    Função: D/V
 Verifique se operações de alto risco (implantação de modelo, exportação de pesos, acesso a dados de treinamento, alterações na configuração de produção) exigem autenticação multifator ou autenticação reforçada com revalidação da sessão.
 #5.1.3    Nível: 2    Função: D
 Verifique se os novos responsáveis passam por uma verificação de identidade alinhada com o NIST 800-63-3 IAL-2 ou padrões equivalentes antes de receberem acesso ao sistema de produção.
 #5.1.4    Nível: 2    Função: V
 Verifique se as revisões de acesso são realizadas trimestralmente com detecção automatizada de contas inativas, aplicação da rotação de credenciais e fluxos de trabalho de desprovisionamento.
 #5.1.5    Nível: 3    Função: D/V
 Verifique se os agentes de IA federados autenticam-se por meio de afirmações JWT assinadas que possuem uma vida útil máxima de 24 horas e incluem prova criptográfica de origem.

---

### C5.2 Autorização de Recursos e Privilégio Mínimo

Implemente controles de acesso detalhados para todos os recursos de IA com modelos de permissão explícitos e trilhas de auditoria.

 #5.2.1    Nível: 1    Função: D/V
 Verifique se todos os recursos de IA (conjuntos de dados, modelos, endpoints, coleções vetoriais, índices de embedding, instâncias de computação) aplicam controles de acesso baseados em função com listas de permissão explícitas e políticas de negação padrão.
 #5.2.2    Nível: 1    Função: D/V
 Verifique se os princípios de menor privilégio são aplicados por padrão às contas de serviço, começando com permissões de somente leitura e exigindo justificativa comercial documentada para acesso de gravação.
 #5.2.3    Nível: 1    Função: V
 Verifique se todas as modificações no controle de acesso estão vinculadas a solicitações de alteração aprovadas e registradas de forma imutável com carimbos de data/hora, identidades dos atores, identificadores de recursos e deltas de permissão.
 #5.2.4    Nível: 2    Função: D
 Verifique se os rótulos de classificação de dados (PII, PHI, controle de exportação, proprietário) propagam automaticamente para os recursos derivados (incorporações, caches de prompt, saídas de modelo) com aplicação consistente da política.
 #5.2.5    Nível: 2    Função: D/V
 Verifique se as tentativas de acesso não autorizado e os eventos de escalonamento de privilégios acionam alertas em tempo real com metadados contextuais para os sistemas SIEM dentro de 5 minutos.

---

### C5.3 Avaliação Dinâmica de Políticas

Implemente motores de controle de acesso baseado em atributos (ABAC) para decisões de autorização com consciência de contexto e capacidades de auditoria.

 #5.3.1    Nível: 1    Função: D/V
 Verifique se as decisões de autorização são externalizadas para um mecanismo de política dedicado (OPA, Cedar ou equivalente), acessível por meio de APIs autenticadas com proteção de integridade criptográfica.
 #5.3.2    Nível: 1    Função: D/V
 Verifique se as políticas avaliam atributos dinâmicos em tempo de execução, incluindo nível de autorização do usuário, classificação de sensibilidade do recurso, contexto da solicitação, isolamento do locatário e restrições temporais.
 #5.3.3    Nível: 2    Função: D
 Verifique se as definições de políticas são controladas por versão, revisadas por pares e validadas por meio de testes automatizados em pipelines de CI/CD antes da implantação em produção.
 #5.3.4    Nível: 2    Função: V
 Verifique se os resultados da avaliação da política incluem justificativas estruturadas das decisões e são transmitidos para sistemas SIEM para análise de correlação e geração de relatórios de conformidade.
 #5.3.5    Nível: 3    Função: D/V
 Verifique se os valores de tempo de vida (TTL) do cache de política não excedem 5 minutos para recursos de alta sensibilidade e 1 hora para recursos padrão com capacidades de invalidação de cache.

---

### C5.4 Aplicação de Segurança em Tempo de Consulta

Implemente controles de segurança na camada de banco de dados com filtragem obrigatória e políticas de segurança a nível de linha.

 #5.4.1    Nível: 1    Função: D/V
 Verifique se todas as consultas de banco de dados vetorial e SQL incluem filtros de segurança obrigatórios (ID do locatário, rótulos de sensibilidade, escopo do usuário) aplicados no nível do mecanismo do banco de dados, e não no código da aplicação.
 #5.4.2    Nível: 1    Função: D/V
 Verifique se as políticas de segurança em nível de linha (RLS) e o mascaramento em nível de campo estão habilitados com herança de políticas para todos os bancos de dados vetoriais, índices de busca e conjuntos de dados de treinamento.
 #5.4.3    Nível: 2    Função: D
 Verifique se as avaliações de autorização falhadas impedirão "ataques de delegado confuso" abortando imediatamente as consultas e retornando códigos de erro de autorização explícitos em vez de retornar conjuntos de resultados vazios.
 #5.4.4    Nível: 2    Função: V
 Verifique se a latência da avaliação da política é monitorada continuamente com alertas automatizados para condições de tempo limite que possam permitir a violação de autorização.
 #5.4.5    Nível: 3    Função: D/V
 Verifique se os mecanismos de repetição de consulta reavaliam as políticas de autorização para levar em conta mudanças dinâmicas de permissões dentro de sessões de usuário ativas.

---

### Filtragem de Saída C5.5 e Prevenção de Perda de Dados

Implemente controles de pós-processamento para evitar a exposição não autorizada de dados em conteúdo gerado por IA.

 #5.5.1    Nível: 1    Função: D/V
 Verifique se os mecanismos de filtragem pós-inferência analisam e redigem informações pessoais identificáveis (PII) não autorizadas, informações classificadas e dados proprietários antes de entregar o conteúdo aos solicitantes.
 #5.5.2    Nível: 1    Função: D/V
 Verifique se as citações, referências e atribuições de fonte nos resultados do modelo são validadas de acordo com os direitos do solicitante e removidas caso seja detectado acesso não autorizado.
 #5.5.3    Nível: 2    Função: D
 Verifique se as restrições de formato de saída (PDFs sanitizados, imagens sem metadados, tipos de arquivos aprovados) são aplicadas com base nos níveis de permissão do usuário e nas classificações dos dados.
 #5.5.4    Nível: 2    Função: V
 Verifique se os algoritmos de redação são determinísticos, controlados por versão e mantêm registros de auditoria para apoiar investigações de conformidade e análise forense.
 #5.5.5    Nível: 3    Função: V
 Verifique se eventos de redação de alto risco geram logs adaptativos que incluem hashes criptográficos do conteúdo original para recuperação forense sem exposição de dados.

---

### C5.6 Isolamento Multi-Inquilino

Assegurar isolamento criptográfico e lógico entre os locatários na infraestrutura de IA compartilhada.

 #5.6.1    Nível: 1    Função: D/V
 Verifique se os espaços de memória, armazenamentos de embeddings, entradas de cache e arquivos temporários estão segregados por namespace para cada locatário, com purga segura na exclusão do locatário ou término da sessão.
 #5.6.2    Nível: 1    Função: D/V
 Verifique se cada solicitação de API inclui um identificador de locatário autenticado que é validado criptograficamente em relação ao contexto da sessão e às autorizações do usuário.
 #5.6.3    Nível: 2    Função: D
 Verifique se as políticas de rede implementam regras de negação padrão para comunicação entre locatários em malhas de serviço e plataformas de orquestração de contêineres.
 #5.6.4    Nível: 3    Função: D
 Verifique se as chaves de criptografia são exclusivas por inquilino com suporte a chave gerenciada pelo cliente (CMK) e isolamento criptográfico entre os armazenamentos de dados dos inquilinos.

---

### C5.7 Autorização de Agente Autônomo

Controle as permissões para agentes de IA e sistemas autônomos por meio de tokens de capacidade com escopo e autorização contínua.

 #5.7.1    Nível: 1    Função: D/V
 Verifique se os agentes autônomos recebem tokens de capacidade delimitada que enumeram explicitamente as ações permitidas, os recursos acessíveis, os limites de tempo e as restrições operacionais.
 #5.7.2    Nível: 1    Função: D/V
 Verifique se as capacidades de alto risco (acesso ao sistema de arquivos, execução de código, chamadas a APIs externas, transações financeiras) estão desativadas por padrão e exigem autorizações explícitas para ativação, com justificativas de negócios.
 #5.7.3    Nível: 2    Função: D
 Verifique se os tokens de capacidade estão vinculados às sessões do usuário, incluem proteção criptográfica de integridade e garantem que não possam ser persistidos ou reutilizados em cenários offline.
 #5.7.4    Nível: 2    Função: V
 Verifique se as ações iniciadas pelo agente passam por autorização secundária por meio do mecanismo de política ABAC com avaliação de contexto completo e registro de auditoria.
 #5.7.5    Nível: 3    Função: V
 Verifique se as condições de erro do agente e o tratamento de exceções incluem informações sobre o escopo de capacidade para apoiar a análise de incidentes e a investigação forense.

---

### Referências

#### Normas e Estruturas

NIST SP 800-63-3: Digital Identity Guidelines
Zero Trust Architecture – NIST SP 800-207
OWASP Application Security Verification Standard (AISVS)
​
#### Guias de Implementação

Identity and Access Management in the AI Era: 2025 Guide – IDSA
Attribute-Based Access Control with OPA – Permify
How We Designed Cedar to Be Intuitive, Fast, and Safe – AWS
​
#### Segurança Específica para IA

Row Level Security in Vector DBs for RAG – Bluetuple.ai
Tenant Isolation in Multi-Tenant Systems – WorkOS
Handling AI Agent Permissions – Stytch
OWASP Top 10 for Large Language Model Applications

## Segurança da Cadeia de Suprimentos C6 para Modelos, Frameworks e Dados

### Objetivo de Controle

Os ataques à cadeia de suprimentos de IA exploram modelos, frameworks ou conjuntos de dados de terceiros para incorporar backdoors, viés ou códigos exploráveis. Esses controles fornecem proveniência de ponta a ponta, gerenciamento de vulnerabilidades e monitoramento para proteger todo o ciclo de vida do modelo.

---

### C6.1 Verificação e Procedência do Modelo Pré-treinado

Avalie e autentique as origens, licenças e comportamentos ocultos de modelos de terceiros antes de qualquer ajuste fino ou implantação.

 #6.1.1    Nível: 1    Função: D/V
 Verifique se todo artefato de modelo de terceiros inclui um registro de proveniência assinado que identifica o repositório de origem e o hash do commit.
 #6.1.2    Nível: 1    Função: D/V
 Verifique se os modelos são analisados em busca de camadas maliciosas ou gatilhos de Trojan usando ferramentas automatizadas antes da importação.
 #6.1.3    Nível: 2    Função: D
 Verifique se o fine-tuning de transfer learning passa na avaliação adversarial para detectar comportamentos ocultos.
 #6.1.4    Nível: 2    Função: V
 Verifique se as licenças do modelo, as tags de controle de exportação e as declarações de origem dos dados estão registradas em uma entrada de ML‑BOM.
 #6.1.5    Nível: 3    Função: D/V
 Verifique se os modelos de alto risco (pesos carregados publicamente, criadores não verificados) permanecem em quarentena até a revisão e aprovação humana.

---

### C6.2 Varredura de Frameworks e Bibliotecas

Escanear continuamente frameworks e bibliotecas de ML em busca de CVEs e código malicioso para manter a pilha de execução segura.

 #6.2.1    Nível: 1    Função: D/V
 Verifique se os pipelines de CI executam scanners de dependências em frameworks de IA e bibliotecas críticas.
 #6.2.2    Nível: 1    Função: D/V
 Verifique se as vulnerabilidades críticas (CVSS ≥ 7.0) bloqueiam a promoção para imagens de produção.
 #6.2.3    Nível: 2    Função: D
 Verifique se a análise estática de código é executada em bibliotecas de ML bifurcadas ou incorporadas.
 #6.2.4    Nível: 2    Função: V
 Verifique se as propostas de atualização do framework incluem uma avaliação de impacto de segurança referenciando fontes públicas de CVE.
 #6.2.5    Nível: 3    Função: V
 Verifique se os sensores em tempo de execução alertam sobre carregamentos inesperados de bibliotecas dinâmicas que desviam do SBOM assinado.

---

### C6.3 Fixação e Verificação de Dependências

Fixe todas as dependências em digests imutáveis e reproduza as compilações para garantir artefatos idênticos e livres de adulterações.

 #6.3.1    Nível: 1    Função: D/V
 Verifique se todos os gerenciadores de pacotes aplicam o bloqueio de versão por meio de arquivos de bloqueio.
 #6.3.2    Nível: 1    Função: D/V
 Verifique se são usados resumos imutáveis em vez de tags mutáveis nas referências de contêiner.
 #6.3.3    Nível: 2    Função: D
 Verifique se as verificações de build reprodutível comparam hashes entre execuções de CI para garantir saídas idênticas.
 #6.3.4    Nível: 2    Função: V
 Verifique se as atestações de compilação são armazenadas por 18 meses para rastreabilidade de auditoria.
 #6.3.5    Nível: 3    Função: D
 Verifique se dependências expiradas acionam PRs automáticos para atualizar ou bifurcar versões fixadas.

---

### C6.4 Aplicação de Fonte Confiável

Permita downloads de artefatos apenas de fontes aprovadas pela organização e verificadas criptograficamente, e bloqueie todo o resto.

 #6.4.1    Nível: 1    Função: D/V
 Verifique se os pesos do modelo, os conjuntos de dados e os contêineres são baixados somente de domínios aprovados ou registradores internos.
 #6.4.2    Nível: 1    Função: D/V
 Verifique se as assinaturas Sigstore/Cosign validam a identidade do publicador antes que os artefatos sejam armazenados em cache localmente.
 #6.4.3    Nível: 2    Função: D
 Verifique se os proxies de saída bloqueiam downloads de artefatos não autenticados para aplicar a política de fonte confiável.
 #6.4.4    Nível: 2    Função: V
 Verifique se as listas de permissões do repositório são revisadas trimestralmente com evidência de justificativa comercial para cada entrada.
 #6.4.5    Nível: 3    Função: V
 Verifique se as violações de política acionam o isolamento dos artefatos e o rollback das execuções das pipelines dependentes.

---

### C6.5 Avaliação de Risco de Conjunto de Dados de Terceiros

Avalie conjuntos de dados externos quanto a envenenamento, viés e conformidade legal, e monitore-os ao longo de todo o seu ciclo de vida.

 #6.5.1    Nível: 1    Função: D/V
 Verificar se os conjuntos de dados externos passam por uma avaliação de risco de envenenamento (por exemplo, impressão digital dos dados, detecção de outliers).
 #6.5.2    Nível: 1    Função: D
 Verifique se as métricas de viés (paridade demográfica, igualdade de oportunidade) são calculadas antes da aprovação do conjunto de dados.
 #6.5.3    Nível: 2    Função: V
 Verifique se a proveniência e os termos de licença dos conjuntos de dados estão capturados nas entradas do ML‑BOM.
 #6.5.4    Nível: 2    Função: V
 Verifique se o monitoramento periódico detecta deriva ou corrupção nos conjuntos de dados hospedados.
 #6.5.5    Nível: 3    Função: D
 Verifique se o conteúdo não permitido (direitos autorais, informações pessoais identificáveis) é removido por meio de limpeza automatizada antes do treinamento.

---

### C6.6 Monitoramento de Ataque na Cadeia de Suprimentos

Detecte ameaças à cadeia de suprimentos cedo por meio de feeds CVE, análises de logs de auditoria e simulações de equipe vermelha.

 #6.6.1    Nível: 1    Função: V
 Verifique se os logs de auditoria do CI/CD são transmitidos para as detecções do SIEM para identificar puxadas de pacotes anômalas ou etapas de construção adulteradas.
 #6.6.2    Nível: 2    Função: D
 Verifique se os playbooks de resposta a incidentes incluem procedimentos de reversão para modelos ou bibliotecas comprometidos.
 #6.6.3    Nível: 3    Função: V
 Verifique se as tags de enriquecimento de inteligência de ameaças identificam indicadores específicos de ML (por exemplo, IoCs de envenenamento de modelo) na triagem de alertas.

---

### C6.7 ML‑BOM para Artefatos de Modelo

Gere e assine SBOMs específicas para ML detalhadas (ML-BOMs) para que os consumidores finais possam verificar a integridade dos componentes no momento da implantação.

 #6.7.1    Nível: 1    Função: D/V
 Verifique se todo artefato do modelo publica um ML-BOM que lista conjuntos de dados, pesos, hiperparâmetros e licenças.
 #6.7.2    Nível: 1    Função: D/V
 Verifique se a geração do ML‑BOM e a assinatura Cosign estão automatizadas na CI e são obrigatórias para o merge.
 #6.7.3    Nível: 2    Função: D
 Verifique se as verificações de completude do ML-BOM falham na compilação se algum metadado do componente (hash, licença) estiver ausente.
 #6.7.4    Nível: 2    Função: V
 Verifique se os consumidores a jusante podem consultar ML-BOMs via API para validar modelos importados no momento da implantação.
 #6.7.5    Nível: 3    Função: V
 Verifique se os ML‑BOMs são controlados por versão e comparados para detectar modificações não autorizadas.

---

### Referências

ML Supply Chain Compromise – MITRE ATLAS
Supply‑chain Levels for Software Artifacts (SLSA)
CycloneDX – Machine Learning Bill of Materials
What is Data Poisoning? – SentinelOne
Transfer Learning Attack – OWASP ML Security Top 10
AI Data Security Best Practices – CISA
Secure CI/CD Supply Chain – Sumo Logic
AI & Transparency: Protect ML Models – ReversingLabs
SBOM Overview – CISA
Training Data Poisoning Guide – Lakera.ai
Dependency Pinning for Reproducible Python – Medium

## Comportamento do Modelo C7, Controle de Saída e Garantia de Segurança

### Objetivo de Controle

As saídas do modelo devem ser estruturadas, confiáveis, seguras, explicáveis e continuamente monitoradas em produção. Fazer isso reduz alucinações, vazamentos de privacidade, conteúdo prejudicial e ações descontroladas, ao mesmo tempo que aumenta a confiança do usuário e a conformidade regulatória.

---

### C7.1 Aplicação do Formato de Saída

Esquemas rígidos, decodificação restrita e validação posterior impedem que conteúdo malformado ou malicioso se propague.

 #7.1.1    Nível: 1    Função: D/V
 Verifique se os esquemas de resposta (por exemplo, JSON Schema) são fornecidos no prompt do sistema e se toda saída é automaticamente validada; saídas que não estejam em conformidade acionam reparo ou rejeição.
 #7.1.2    Nível: 1    Função: D/V
 Verifique se a decodificação restrita (tokens de parada, regex, max-tokens) está ativada para evitar estouro ou canais laterais de injeção de prompt.
 #7.1.3    Nível: 2    Função: D/V
 Verifique se os componentes downstream tratam as saídas como não confiáveis e as validam contra esquemas ou desserializadores seguros contra injeção.
 #7.1.4    Nível: 3    Função: V
 Verifique se eventos de saída inadequada são registrados, limitados em taxa e exibidos no monitoramento.

---

### C7.2 Detecção e Mitigação de Alucinações

A estimativa de incerteza e as estratégias de contingência limitam respostas fabricadas.

 #7.2.1    Nível: 1    Função: D/V
 Verifique se as log-probabilidades ao nível do token, a auto-consistência do conjunto (ensemble), ou os detectores de alucinação ajustados atribuem uma pontuação de confiança a cada resposta.
 #7.2.2    Nível: 1    Função: D/V
 Verifique se as respostas abaixo de um limiar configurável de confiança acionam fluxos de trabalho de contingência (por exemplo, geração aumentada por recuperação, modelo secundário ou revisão humana).
 #7.2.3    Nível: 2    Função: D/V
 Verifique se os incidentes de alucinação estão marcados com metadados de causa raiz e enviados para os pipelines de análise post-mortem e ajuste fino.
 #7.2.4    Nível: 3    Função: D/V
 Verifique se os limiares e detectores são recalibrados após atualizações importantes do modelo ou da base de conhecimento.
 #7.2.5    Nível: 3    Função: V
 Verifique se as visualizações do dashboard acompanham as taxas de alucinação.

---

### C7.3 Filtragem de Segurança e Privacidade de Saída

Filtros de política e cobertura de red-team protegem os usuários e dados confidenciais.

 #7.3.1    Nível: 1    Função: D/V
 Verifique se os classificadores pré e pós-geração bloqueiam conteúdo de ódio, assédio, automutilação, extremismo e conteúdo sexualmente explícito alinhado à política.
 #7.3.2    Nível: 1    Função: D/V
 Verifique se a detecção de PII/PCI e a redação automática são executadas em todas as respostas; violações geram um incidente de privacidade.
 #7.3.3    Nível: 2    Função: D
 Verifique se as etiquetas de confidencialidade (por exemplo, segredos comerciais) se propagam através das modalidades para prevenir vazamentos em texto, imagens ou código.
 #7.3.4    Nível: 3    Função: D/V
 Verifique se as tentativas de contornar filtros ou classificações de alto risco exigem aprovação secundária ou reauntenticação do usuário.
 #7.3.5    Nível: 3    Função: D/V
 Verifique se os limites de filtragem refletem as jurisdições legais e o contexto de idade/papel do usuário.

---

### C7.4 Limitação de Saída e Ação

Limites de taxa e portões de aprovação evitam abusos e autonomia excessiva.

 #7.4.1    Nível: 1    Função: D
 Verifique se as cotas por usuário e por chave de API limitam solicitações, tokens e custos com retrocesso exponencial em erros 429.
 #7.4.2    Nível: 1    Função: D/V
 Verifique se ações privilegiadas (gravações em arquivos, execução de código, chamadas de rede) requerem aprovação baseada em políticas ou intervenção humana.
 #7.4.3    Nível: 2    Função: D/V
 Verifique se as verificações de consistência cruzada entre modalidades garantem que imagens, código e texto gerados para a mesma solicitação não possam ser usados para contrabandear conteúdo malicioso.
 #7.4.4    Nível: 2    Função: D
 Verifique se a profundidade de delegação do agente, os limites de recursão e as listas de ferramentas permitidas estão configurados explicitamente.
 #7.4.5    Nível: 3    Função: V
 Verifique se a violação de limites gera eventos de segurança estruturados para ingestão pelo SIEM.

---

### C7.5 Explicabilidade da Saída

Sinais transparentes melhoram a confiança do usuário e a depuração interna.

 #7.5.1    Nível: 2    Função: D/V
 Verifique se as pontuações de confiança voltadas para o usuário ou os resumos breves de raciocínio são exibidos quando a avaliação de risco considerar apropriado.
 #7.5.2    Nível: 2    Função: D/V
 Verifique se as explicações geradas evitam revelar prompts sensíveis do sistema ou dados proprietários.
 #7.5.3    Nível: 3    Função: D
 Verifique se o sistema captura log-probabilidades em nível de token ou mapas de atenção e os armazena para inspeção autorizada.
 #7.5.4    Nível: 3    Função: V
 Verifique se os artefatos de explicabilidade são controlados por versão juntamente com as versões do modelo para auditabilidade.

---

### C7.6 Integração de Monitoramento

A observabilidade em tempo real fecha o ciclo entre desenvolvimento e produção.

 #7.6.1    Nível: 1    Função: D
 Verifique se as métricas (violação de esquema, taxa de alucinação, toxicidade, vazamentos de PII, latência, custo) são transmitidas para uma plataforma central de monitoramento.
 #7.6.2    Nível: 1    Função: V
 Verifique se os limites de alerta estão definidos para cada métrica de segurança, com caminhos de escalonamento para plantão.
 #7.6.3    Nível: 2    Função: V
 Verifique se os painéis correlacionam anomalias de saída com modelo/versão, sinalizador de recurso e alterações nos dados upstream.
 #7.6.4    Nível: 2    Função: D/V
 Verifique se os dados de monitoramento retornam para o re-treinamento, ajuste fino ou atualizações de regras dentro de um fluxo de trabalho MLOps documentado.
 #7.6.5    Nível: 3    Função: V
 Verifique se os pipelines de monitoramento são testados quanto à penetração e possuem controle de acesso para evitar o vazamento de logs sensíveis.

---

### 7.7 Salvaguardas para Mídia Generativa

Garantir que os sistemas de IA não gerem conteúdo de mídia ilegal, prejudicial ou não autorizado, aplicando restrições de política, validação de resultados e rastreabilidade.

 #7.7.1    Nível: 1    Função: D/V
 Verifique se os prompts do sistema e as instruções do usuário proíbem explicitamente a geração de mídia deepfake ilegal, prejudicial ou não consensual (por exemplo, imagem, vídeo, áudio).
 #7.7.2    Nível: 2    Função: D/V
 Verifique se os prompts são filtrados para tentativas de gerar personificações, deepfakes sexualmente explícitos ou mídia que retrate indivíduos reais sem consentimento.
 #7.7.3    Nível: 2    Função: V
 Verifique se o sistema utiliza hashing perceptual, detecção de marca d'água ou fingerprinting para evitar a reprodução não autorizada de mídia protegida por direitos autorais.
 #7.7.4    Nível: 3    Função: D/V
 Verifique se toda a mídia gerada é assinada criptograficamente, marcada com marca d'água ou incorporada com metadados de proveniência resistentes a adulterações para rastreabilidade posterior.
 #7.7.5    Nível: 3    Função: V
 Verifique se as tentativas de bypass (por exemplo, obfuscação de prompt, gírias, formulações adversariais) são detectadas, registradas e limitadas por taxa; abusos repetidos são reportados aos sistemas de monitoramento.

### Referências

NIST AI Risk Management Framework
ISO/IEC 42001:2023 – AI Management System
OWASP Top-10 for Large Language Model Applications (2025)
Improper Output Handling – OWASP LLM05:2025
Practical Techniques to Constrain LLM Output
Dataiku – Structured Text Generation Guide
VL-Uncertainty: Detecting Hallucinations
HaDeMiF: Hallucination Detection & Mitigation
Building Confidence in LLM Outputs
Explainable AI & LLMs
LLM Red-Teaming Guide
Sensitive Information Disclosure in LLMs
LangChain – Chat Model Rate Limiting
OpenAI Rate-Limit & Exponential Back-off
Arize AI – LLM Observability Platform

## Segurança de Memória C8, Embeddings e Banco de Dados Vetoriais

### Objetivo de Controle

Incorporação e armazenamentos vetoriais atuam como a "memória viva" dos sistemas de IA contemporâneos, aceitando continuamente dados fornecidos pelo usuário e os trazendo de volta para os contextos do modelo por meio da Geração Aumentada por Recuperação (RAG). Se deixada sem governança, essa memória pode vazar informações pessoalmente identificáveis (PII), violar consentimentos ou ser invertida para reconstruir o texto original. O objetivo desta família de controles é fortalecer os pipelines de memória e os bancos de dados vetoriais para que o acesso seja de privilégio mínimo, as incorporações preservem a privacidade, os vetores armazenados expirem ou possam ser revogados sob demanda, e a memória por usuário nunca contamine as solicitações ou respostas de outro usuário.

---

### C8.1 Controles de Acesso na Memória e Índices RAG

Implemente controles de acesso granulares em cada coleção de vetores.

 #8.1.1    Nível: 1    Função: D/V
 Verifique se as regras de controle de acesso em nível de linha/espaço de nomes restringem as operações de inserção, exclusão e consulta por locatário, coleção ou etiqueta de documento.
 #8.1.2    Nível: 1    Função: D/V
 Verifique se as chaves de API ou os JWTs possuem claims com escopo definido (por exemplo, IDs de coleção, verbos de ação) e são rotacionados pelo menos trimestralmente.
 #8.1.3    Nível: 2    Função: D/V
 Verifique se as tentativas de escalonamento de privilégios (por exemplo, consultas de similaridade entre namespaces) são detectadas e registradas em um SIEM em até 5 minutos.
 #8.1.4    Nível: 2    Função: D/V
 Verifique se o banco de dados vetorial registra no log o identificador do sujeito, a operação, o ID/namespace do vetor, o limite de similaridade e a contagem de resultados.
 #8.1.5    Nível: 3    Função: V
 Verifique se as decisões de acesso são testadas para falhas de bypass sempre que os motores são atualizados ou as regras de segmentação de índices são alteradas.

---

### C8.2 Sanitização e Validação de Embeddings

Pré-filtre o texto para informações pessoalmente identificáveis (PII), faça a redação ou pseudonimização antes da vetorização e, opcionalmente, pós-processe as embeddings para remover sinais residuais.

 #8.2.1    Nível: 1    Função: D/V
 Verifique se os dados PII e regulados são detectados por classificadores automatizados e mascarados, tokenizados ou descartados antes da incorporação.
 #8.2.2    Nível: 1    Função: D
 Verifique se os pipelines de incorporação rejeitam ou colocam em quarentena entradas que contenham código executável ou artefatos não UTF-8 que possam contaminar o índice.
 #8.2.3    Nível: 2    Função: D/V
 Verifique se a sanitização de privacidade diferencial local ou métrica é aplicada aos embeddings de sentenças cuja distância para qualquer token PII conhecido cai abaixo de um limite configurável.
 #8.2.4    Nível: 2    Função: V
 Verifique se a eficácia da sanitização (por exemplo, recall da redação de PII, deriva semântica) é validada pelo menos semestralmente contra corpora de referência.
 #8.2.5    Nível: 3    Função: D/V
 Verifique se as configurações de sanitização estão controladas por versão e se as alterações passam por revisão por pares.

---

### C8.3 Expiração, Revogação e Exclusão de Memória

A "direito ao esquecimento" do GDPR e leis semelhantes exigem a exclusão em tempo hábil; portanto, os armazenamentos vetoriais devem suportar TTLs, exclusões definitivas e tomb-stoning para que vetores revogados não possam ser recuperados ou reindexados.

 #8.3.1    Nível: 1    Função: D/V
 Verifique se cada vetor e registro de metadados possui um TTL ou um rótulo de retenção explícito respeitado por trabalhos automatizados de limpeza.
 #8.3.2    Nível: 1    Função: D/V
 Verifique se as solicitações de exclusão iniciadas pelo usuário eliminam vetores, metadados, cópias em cache e índices derivados dentro de 30 dias.
 #8.3.3    Nível: 2    Função: D
 Verifique se as exclusões lógicas são seguidas pela destruição criptográfica dos blocos de armazenamento, caso o hardware o suporte, ou pela destruição da chave do cofre de chaves.
 #8.3.4    Nível: 3    Função: D/V
 Verifique se os vetores expirados são excluídos dos resultados da busca por vizinhos mais próximos em menos de 500 ms após a expiração.

---

### C8.4 Prevenir Inversão e Vazamento de Embeddings

Defesas recentes—sobreposição de ruído, redes de projeção, perturbação de neurônios de privacidade e criptografia na camada de aplicação—podem reduzir as taxas de inversão ao nível do token para menos de 5%.

 #8.4.1    Nível: 1    Função: V
 Verificar se existe um modelo formal de ameaça que cubra ataques de inversão, de associação e de inferência de atributos, e se ele é revisado anualmente.
 #8.4.2    Nível: 2    Função: D/V
 Verifique se a criptografia na camada de aplicação ou a criptografia pesquisável protegem os vetores contra leituras diretas por administradores de infraestrutura ou funcionários da nuvem.
 #8.4.3    Nível: 3    Função: V
 Verifique se os parâmetros de defesa (ε para DP, ruído σ, posto de projeção k) equilibram a privacidade ≥ 99% de proteção de tokens e utilidade ≤ 3% de perda de precisão.
 #8.4.4    Nível: 3    Função: D/V
 Verifique se as métricas de resistência à inversão fazem parte dos critérios de liberação para atualizações do modelo, com orçamentos de regressão definidos.

---

### C8.5 Aplicação de Escopo para Memória Específica do Usuário

O vazamento entre inquilinos continua sendo um dos principais riscos do RAG: consultas de similaridade filtradas incorretamente podem expor documentos privados de outro cliente.

 #8.5.1    Nível: 1    Função: D/V
 Verifique se cada consulta de recuperação é pós-filtrada pelo ID de locatário/usuário antes de ser passada para o prompt do LLM.
 #8.5.2    Nível: 1    Função: D
 Verifique se os nomes de coleções ou IDs com namespaces são salinizados por usuário ou inquilino para que os vetores não possam colidir entre diferentes escopos.
 #8.5.3    Nível: 2    Função: D/V
 Verifique se os resultados de similaridade acima de um limite de distância configurável, mas fora do escopo do chamador, são descartados e acionam alertas de segurança.
 #8.5.4    Nível: 2    Função: V
 Verifique se os testes de estresse multi-inquilino simulam consultas adversariais que tentam recuperar documentos fora do escopo e demonstrem ausência total de vazamento.
 #8.5.5    Nível: 3    Função: D/V
 Verifique se as chaves de criptografia são segregadas por locatário, garantindo isolamento criptográfico mesmo que o armazenamento físico seja compartilhado.

---

### C8.6 Segurança Avançada do Sistema de Memória

Controles de segurança para arquiteturas de memória sofisticadas, incluindo memória episódica, semântica e de trabalho, com requisitos específicos de isolamento e validação.

 #8.6.1    Nível: 1    Função: D/V
 Verifique se os diferentes tipos de memória (episódica, semântica, de trabalho) possuem contextos de segurança isolados com controles de acesso baseados em função, chaves de criptografia separadas e padrões de acesso documentados para cada tipo de memória.
 #8.6.2    Nível: 2    Função: D/V
 Verifique se os processos de consolidação de memória incluem validação de segurança para prevenir a injeção de memórias maliciosas por meio de sanitização de conteúdo, verificação de fonte e checagens de integridade antes do armazenamento.
 #8.6.3    Nível: 2    Função: D/V
 Verifique se as consultas de recuperação de memória são validadas e higienizadas para evitar a extração de informações não autorizadas por meio da análise de padrões de consulta, aplicação de controle de acesso e filtragem de resultados.
 #8.6.4    Nível: 3    Função: D/V
 Verifique se os mecanismos de esquecimento de memória excluem informações sensíveis de forma segura com garantias de apagamento criptográfico utilizando exclusão de chave, sobregravação múltipla ou exclusão segura baseada em hardware com certificados de verificação.
 #8.6.5    Nível: 3    Função: D/V
 Verifique se a integridade do sistema de memória é continuamente monitorada para modificações ou corrupções não autorizadas por meio de somas de verificação, registros de auditoria e alertas automatizados quando o conteúdo da memória mudar fora das operações normais.

---

### Referências

Vector database security: Pinecone – IronCore Labs
Securing the Backbone of AI: Safeguarding Vector Databases and Embeddings – Privacera
Enhancing Data Security with RBAC of Qdrant Vector Database – AI Advances
Mitigating Privacy Risks in LLM Embeddings from Embedding Inversion – arXiv
DPPN: Detecting and Perturbing Privacy-Sensitive Neurons – OpenReview
Art. 17 GDPR – Right to Erasure
Sensitive Data in Text Embeddings Is Recoverable – Tonic.ai
PII Identification and Removal – NVIDIA NeMo Docs
De-identifying Sensitive Data – Google Cloud DLP
Remove PII from Conversations Using Sensitive Information Filters – AWS Bedrock Guardrails
Think Your RAG Is Secure? Think Again – Medium
Design a Secure Multitenant RAG Inferencing Solution – Microsoft Learn
Best Practices for Multi-Tenancy RAG with Milvus – Milvus Blog

## 9 Orquestração Autônoma e Segurança de Ação Agente

### Objetivo de Controle

Garantir que sistemas autônomos ou de múltiplos agentes de IA possam executar apenas ações que sejam explicitamente intencionadas, autenticadas, auditáveis e dentro de limites definidos de custo e risco. Isso protege contra ameaças como Comprometimento de Sistema Autônomo, Uso Indevido de Ferramentas, Detecção de Loop de Agente, Sequestro de Comunicação, Falsificação de Identidade, Manipulação de Enxame e Manipulação de Intenção.

---

### 9.1 Planejamento de Tarefas do Agente e Orçamentos de Recursão

Limite planos recursivos e imponha pontos de verificação humanos para ações privilegiadas.

 #9.1.1    Nível: 1    Função: D/V
 Verifique se a profundidade máxima de recursão, amplitude, tempo de relógio de parede, tokens e custo monetário por execução do agente estão configurados centralmente e controlados por versão.
 #9.1.2    Nível: 1    Função: D/V
 Verifique se ações privilegiadas ou irreversíveis (por exemplo, commits de código, transferências financeiras) exigem aprovação humana explícita por meio de um canal auditável antes da execução.
 #9.1.3    Nível: 2    Função: D
 Verifique se os monitores de recursos em tempo real acionam a interrupção do disjuntor quando qualquer limite orçamentário é excedido, interrompendo a expansão adicional da tarefa.
 #9.1.4    Nível: 2    Função: D/V
 Verifique se os eventos do disjuntor estão registrados com o ID do agente, condição de disparo e estado do plano capturado para revisão forense.
 #9.1.5    Nível: 3    Função: V
 Verifique se os testes de segurança abrangem cenários de esgotamento de orçamento e planos descontrolados, confirmando a parada segura sem perda de dados.
 #9.1.6    Nível: 3    Função: D
 Verifique se as políticas orçamentárias estão expressas como policy-as-code e aplicadas no CI/CD para impedir o desvio de configuração.

---

### 9.2 Sandboxing de Plugin de Ferramenta

Isole as interações da ferramenta para evitar acesso não autorizado ao sistema ou execução de código.

 #9.2.1    Nível: 1    Função: D/V
 Verifique se todas as ferramentas/plugins são executados dentro de um sandbox de nível OS, container ou WASM com políticas de mínimo privilégio para sistema de arquivos, rede e chamadas de sistema.
 #9.2.2    Nível: 1    Função: D/V
 Verifique se as cotas de recursos do sandbox (CPU, memória, disco, saída de rede) e os tempos limite de execução são aplicados e registrados.
 #9.2.3    Nível: 2    Função: D/V
 Verifique se os binários ou descritores das ferramentas estão assinados digitalmente; as assinaturas devem ser validadas antes do carregamento.
 #9.2.4    Nível: 2    Função: V
 Verifique se a telemetria da sandbox é transmitida para um SIEM; anomalias (por exemplo, tentativas de conexões de saída) geram alertas.
 #9.2.5    Nível: 3    Função: V
 Verifique se os plugins de alto risco passam por revisão de segurança e testes de penetração antes da implantação em produção.
 #9.2.6    Nível: 3    Função: D/V
 Verifique se as tentativas de escape do sandbox são automaticamente bloqueadas e se o plugin infrator é colocado em quarentena enquanto aguarda investigação.

---

### 9.3 Loop Autônomo e Limitação de Custos

Detectar e impedir a recursão descontrolada entre agentes e explosões de custos.

 #9.3.1    Nível: 1    Função: D/V
 Verifique se as chamadas entre agentes incluem um limite de saltos ou TTL que o runtime decrementa e impõe.
 #9.3.2    Nível: 2    Função: D
 Verifique se os agentes mantêm um ID exclusivo de gráfico de invocação para detectar auto-invocação ou padrões cíclicos.
 #9.3.3    Nível: 2    Função: D/V
 Verifique se os contadores cumulativos de unidades de computação e gastos são monitorados por cadeia de solicitação; ultrapassar o limite aborta a cadeia.
 #9.3.4    Nível: 3    Função: V
 Verifique se a análise formal ou a verificação de modelos demonstra a ausência de recursão ilimitada nos protocolos do agente.
 #9.3.5    Nível: 3    Função: D
 Verifique se os eventos de aborto de loop geram alertas e alimentam métricas de melhoria contínua.

---

### 9.4 Proteção contra Uso Indevido em Nível de Protocolo

Canais de comunicação seguros entre agentes e sistemas externos para prevenir sequestro ou manipulação.

 #9.4.1    Nível: 1    Função: D/V
 Verifique se todas as mensagens de agente para ferramenta e de agente para agente são autenticadas (por exemplo, TLS mútuo ou JWT) e criptografadas de ponta a ponta.
 #9.4.2    Nível: 1    Função: D
 Verifique se os esquemas são estritamente validados; campos desconhecidos ou mensagens malformadas são rejeitados.
 #9.4.3    Nível: 2    Função: D/V
 Verifique se as verificações de integridade (MACs ou assinaturas digitais) abrangem toda a carga útil da mensagem, incluindo os parâmetros da ferramenta.
 #9.4.4    Nível: 2    Função: D
 Verifique se a proteção contra repetição (nonces ou janelas de timestamp) é aplicada na camada do protocolo.
 #9.4.5    Nível: 3    Função: V
 Verifique se as implementações do protocolo passam por fuzzing e análise estática para detectar falhas de injeção ou desserialização.

---

### 9.5 Identidade do Agente e Evidência de Violação

Garantir que as ações sejam atribuíveis e as modificações detectáveis.

 #9.5.1    Nível: 1    Função: D/V
 Verifique se cada instância de agente possui uma identidade criptográfica única (par de chaves ou credencial baseada em hardware).
 #9.5.2    Nível: 2    Função: D/V
 Verifique se todas as ações dos agentes estão assinadas e com carimbo de data/hora; os registros incluem a assinatura para não repúdio.
 #9.5.3    Nível: 2    Função: V
 Verifique se os logs com evidência de violação são armazenados em um meio somente para acréscimos ou gravação única.
 #9.5.4    Nível: 3    Função: D
 Verifique se as chaves de identidade são rotacionadas em uma programação definida e em caso de indicadores de comprometimento.
 #9.5.5    Nível: 3    Função: D/V
 Verifique se tentativas de falsificação ou conflito de chave acionam quarentena imediata do agente afetado.

---

### 9.6 Redução de Riscos com Enxames Multiagentes

Mitigue riscos de comportamento coletivo por meio de isolamento e modelagem formal de segurança.

 #9.6.1    Nível: 1    Função: D/V
 Verifique se os agentes que operam em diferentes domínios de segurança executam em sandboxes de tempo de execução isolados ou em segmentos de rede.
 #9.6.2    Nível: 3    Função: V
 Verifique se os comportamentos do enxame são modelados e formalmente verificados quanto à vivacidade e segurança antes da implantação.
 #9.6.3    Nível: 3    Função: D
 Verifique se os monitores de tempo de execução detectam padrões emergentes inseguros (por exemplo, oscilações, deadlocks) e iniciam a ação corretiva.

---

### 9.7 Autenticação / Autorização de Usuário e Ferramentas

Implemente controles de acesso robustos para toda ação desencadeada por agentes.

 #9.7.1    Nível: 1    Função: D/V
 Verifique se os agentes se autenticam como principais de primeira classe para sistemas downstream, nunca reutilizando as credenciais do usuário final.
 #9.7.2    Nível: 2    Função: D
 Verifique se as políticas de autorização detalhadas restringem quais ferramentas um agente pode invocar e quais parâmetros ele pode fornecer.
 #9.7.3    Nível: 2    Função: V
 Verifique se as verificações de privilégios são reavaliadas a cada chamada (autorização contínua), e não apenas no início da sessão.
 #9.7.4    Nível: 3    Função: D
 Verifique se os privilégios delegados expiram automaticamente e exigem novo consentimento após o tempo limite ou alteração do escopo.

---

### 9.8 Segurança na Comunicação entre Agentes

Criptografe e proteja a integridade de todas as mensagens entre agentes para impedir escutas e adulterações.

 #9.8.1    Nível: 1    Função: D/V
 Verifique se a autenticação mútua e a criptografia com segredo perfeito à frente (por exemplo, TLS 1.3) são obrigatórias para os canais dos agentes.
 #9.8.2    Nível: 1    Função: D
 Verifique se a integridade e a origem da mensagem são validadas antes do processamento; falhas geram alertas e descartam a mensagem.
 #9.8.3    Nível: 2    Função: D/V
 Verifique se os metadados de comunicação (carimbos de data/hora, números de sequência) são registrados para suportar a reconstrução forense.
 #9.8.4    Nível: 3    Função: V
 Verifique se a verificação formal ou a model checking confirma que as máquinas de estado do protocolo não podem ser conduzidas a estados inseguros.

---

### 9.9 Verificação de Intenção e Aplicação de Restrições

Validar se as ações do agente estão alinhadas com a intenção declarada pelo usuário e as restrições do sistema.

 #9.9.1    Nível: 1    Função: D
 Verifique se os solucionadores de restrições pré-execução verificam as ações propostas em relação às regras rígidas de segurança e políticas codificadas.
 #9.9.2    Nível: 2    Função: D/V
 Verifique se ações de alto impacto (financeiras, destrutivas, sensíveis à privacidade) requerem confirmação explícita de intenção do usuário que as iniciou.
 #9.9.3    Nível: 2    Função: V
 Verifique se as verificações de pós-condição validam que as ações concluídas alcançaram os efeitos pretendidos sem efeitos colaterais; discrepâncias acionam o rollback.
 #9.9.4    Nível: 3    Função: V
 Verifique se métodos formais (por exemplo, verificação de modelos, prova de teoremas) ou testes baseados em propriedades demonstram que os planos do agente satisfazem todas as restrições declaradas.
 #9.9.5    Nível: 3    Função: D
 Verifique se os incidentes de incompatibilidade de intenção ou violação de restrição alimentam ciclos de melhoria contínua e compartilhamento de inteligência sobre ameaças.

---

### 9.10 Segurança da Estratégia de Raciocínio do Agente

Seleção segura e execução de diferentes estratégias de raciocínio, incluindo abordagens ReAct, Chain-of-Thought e Tree-of-Thoughts.

 #9.10.1    Nível: 1    Função: D/V
 Verifique se a seleção da estratégia de raciocínio utiliza critérios determinísticos (complexidade da entrada, tipo de tarefa, contexto de segurança) e se entradas idênticas produzem seleções de estratégia idênticas dentro do mesmo contexto de segurança.
 #9.10.2    Nível: 1    Função: D/V
 Verifique se cada estratégia de raciocínio (ReAct, Chain-of-Thought, Tree-of-Thoughts) possui validação de entrada dedicada, sanitização de saída e limites de tempo de execução específicos para sua abordagem cognitiva.
 #9.10.3    Nível: 2    Função: D/V
 Verifique se as transições da estratégia de raciocínio são registradas com contexto completo, incluindo características de entrada, valores dos critérios de seleção e metadados de execução para reconstrução da trilha de auditoria.
 #9.10.4    Nível: 2    Função: D/V
 Verifique se o raciocínio Tree-of-Thoughts inclui mecanismos de poda de ramificações que terminam a exploração quando são detectadas violações de políticas, limites de recursos ou fronteiras de segurança.
 #9.10.5    Nível: 2    Função: D/V
 Verifique se os ciclos ReAct (Raciocinar-Agir-Observar) incluem pontos de verificação de validação em cada fase: verificação do passo de raciocínio, autorização da ação e sanitização da observação antes de prosseguir.
 #9.10.6    Nível: 3    Função: D/V
 Verifique se os indicadores de desempenho da estratégia de raciocínio (tempo de execução, uso de recursos, qualidade da saída) são monitorados com alertas automáticos quando os indicadores se desviam além dos limites configurados.
 #9.10.7    Nível: 3    Função: D/V
 Verifique se as abordagens de raciocínio híbrido que combinam múltiplas estratégias mantêm a validação de entrada e as restrições de saída de todas as estratégias constituintes, sem contornar nenhum controle de segurança.
 #9.10.8    Nível: 3    Função: D/V
 Verifique se o teste de segurança da estratégia de raciocínio inclui fuzzing com entradas malformadas, prompts adversariais projetados para forçar a troca de estratégia e testes de condições de limite para cada abordagem cognitiva.

---

### 9.11 Gerenciamento do Estado do Ciclo de Vida do Agente e Segurança

Inicialização segura do agente, transições de estado e terminação com trilhas de auditoria criptográficas e procedimentos de recuperação definidos.

 #9.11.1    Nível: 1    Função: D/V
 Verifique se a inicialização do agente inclui o estabelecimento de identidade criptográfica com credenciais suportadas por hardware e logs de auditoria imutáveis de inicialização contendo ID do agente, carimbo de data/hora, hash de configuração e parâmetros de inicialização.
 #9.11.2    Nível: 2    Função: D/V
 Verifique se as transições de estado do agente são assinadas criptograficamente, carimbadas com data e hora, e registradas com contexto completo, incluindo eventos que as desencadearam, hash do estado anterior, hash do novo estado e validações de segurança realizadas.
 #9.11.3    Nível: 2    Função: D/V
 Verifique se os procedimentos de desligamento do agente incluem limpeza segura da memória usando apagamento criptográfico ou sobrescrita múltipla, revogação de credenciais com notificação à autoridade certificadora, e geração de certificados de término à prova de adulteração.
 #9.11.4    Nível: 3    Função: D/V
 Verifique se os mecanismos de recuperação do agente validam a integridade do estado usando somas de verificação criptográficas (mínimo SHA-256) e retornam a estados conhecidos e bons quando a corrupção é detectada, com alertas automatizados e requisitos de aprovação manual.
 #9.11.5    Nível: 3    Função: D/V
 Verifique se os mecanismos de persistência do agente cifram os dados de estado sensíveis com chaves AES-256 por agente e implementam a rotação segura das chaves em cronogramas configuráveis (máximo de 90 dias) com implementação sem tempo de inatividade.

---

### 9.12 Estrutura de Segurança para Integração de Ferramentas

Controles de segurança para carregamento dinâmico de ferramentas, execução e validação de resultados com processos definidos de avaliação de risco e aprovação.

 #9.12.1    Nível: 1    Função: D/V
 Verifique se os descritores da ferramenta incluem metadados de segurança especificando privilégios necessários (leitura/gravação/execução), níveis de risco (baixo/médio/alto), limites de recursos (CPU, memória, rede) e requisitos de validação documentados nos manifests da ferramenta.
 #9.12.2    Nível: 1    Função: D/V
 Verifique se os resultados da execução da ferramenta são validados em relação aos esquemas esperados (JSON Schema, XML Schema) e às políticas de segurança (sanitização de saída, classificação de dados) antes da integração, com limites de tempo e procedimentos de tratamento de erros.
 #9.12.3    Nível: 2    Função: D/V
 Verifique se os logs de interação da ferramenta incluem contexto de segurança detalhado, incluindo uso de privilégios, padrões de acesso a dados, tempo de execução, consumo de recursos e códigos de retorno, com registro estruturado para integração com SIEM.
 #9.12.4    Nível: 2    Função: D/V
 Verifique se os mecanismos de carregamento dinâmico de ferramentas validam assinaturas digitais utilizando a infraestrutura PKI e implementam protocolos de carregamento seguros com isolamento em sandbox e verificação de permissões antes da execução.
 #9.12.5    Nível: 3    Função: D/V
 Verifique se as avaliações de segurança da ferramenta são acionadas automaticamente para novas versões com etapas de aprovação obrigatórias, incluindo análise estática, testes dinâmicos e revisão pela equipe de segurança, com critérios de aprovação documentados e requisitos de SLA.

---

#### Referências

MITRE ATLAS tactics ML09
Circuit-breaker research for AI agents — Zou et al., 2024
Trend Micro analysis of sandbox escapes in AI agents — Park, 2025
Auth0 guidance on human-in-the-loop authorization for agents — Martinez, 2025
Medium deep-dive on MCP & A2A protocol hijacking — ForAISec, 2025
Rapid7 fundamentals on spoofing attack prevention — 2024
Imperial College verification of swarm systems — Lomuscio et al.
NIST AI Risk Management Framework 1.0, 2023
WIRED security briefing on encryption best practices, 2024
OWASP Top 10 for LLM Applications, 2025
Comprehensive Vulnerability Analysis is Necessary for Trustworthy LLM-MAS
[How Is LLM Reasoning Distracted by Irrelevant Context?
An Analysis Using a Controlled Benchmark](https://www.arxiv.org/pdf/2505.18761)
Large Language Model Sentinel: LLM Agent for Adversarial Purification
Securing Agentic AI: A Comprehensive Threat Model and Mitigation Framework for Generative AI Agents

## 10 Robustez Adversarial e Defesa de Privacidade

### Objetivo de Controle

Garantir que os modelos de IA permaneçam confiáveis, preservem a privacidade e sejam resistentes a abusos ao enfrentar ataques de evasão, inferência, extração ou envenenamento.

---

### 10.1 Alinhamento e Segurança do Modelo

Proteja contra resultados nocivos ou que violem as políticas.

 #10.1.1    Nível: 1    Função: D/V
 Verifique se um conjunto de testes de alinhamento (prompts de red-team, sondagens de jailbreak, conteúdo não permitido) está sob controle de versão e é executado a cada versão do modelo.
 #10.1.2    Nível: 1    Função: D
 Verifique se as barreiras de recusa e conclusão segura estão sendo aplicadas.
 #10.1.3    Nível: 2    Função: D/V
 Verifique se um avaliador automatizado mede a taxa de conteúdo prejudicial e sinaliza regressões além de um limite definido.
 #10.1.4    Nível: 2    Função: D
 Verifique se o treinamento contra-jailbreak está documentado e é reproduzível.
 #10.1.5    Nível: 3    Função: V
 Verifique se as provas formais de conformidade com a política ou o monitoramento certificado abrangem domínios críticos.

---

### 10.2 Endurecimento contra Exemplos Adversariais

Aumentar a resiliência a entradas manipuladas. Treinamento adversarial robusto e avaliação em benchmarks são as melhores práticas atuais.

 #10.2.1    Nível: 1    Função: D
 Verifique se os repositórios do projeto incluem configurações de treinamento adversarial com sementes reproduzíveis.
 #10.2.2    Nível: 2    Função: D/V
 Verifique se a detecção de exemplos adversariais gera alertas de bloqueio em pipelines de produção.
 #10.2.4    Nível: 3    Função: V
 Verifique se as provas de robustez certificada ou os certificados de intervalo abrangem pelo menos as principais classes críticas.
 #10.2.5    Nível: 3    Função: V
 Verifique se os testes de regressão utilizam ataques adaptativos para confirmar que não há perda mensurável de robustez.

---

### 10.3 Mitigação de Inferência de Associação

Limitar a capacidade de decidir se um registro estava nos dados de treinamento. Privacidade diferencial e mascaramento de pontuação de confiança continuam sendo as defesas conhecidas mais eficazes.

 #10.3.1    Nível: 1    Função: D
 Verifique se a regularização de entropia por consulta ou o escalonamento de temperatura reduzem previsões excessivamente confiantes.
 #10.3.2    Nível: 2    Função: D
 Verifique se o treinamento utiliza otimização diferencialmente privada limitada por ε para conjuntos de dados sensíveis.
 #10.3.3    Nível: 2    Função: V
 Verifique se as simulações de ataque (modelo sombra ou caixa preta) apresentam AUC de ataque ≤ 0,60 em dados reservados.

---

### 10.4 Resistência à Inversão de Modelo

Prevenir a reconstrução de atributos privados. Pesquisas recentes enfatizam a truncagem de saída e garantias de DP como defesas práticas.

 #10.4.1    Nível: 1    Função: D
 Verifique se atributos sensíveis nunca são diretamente exibidos; quando necessário, use categorias ou transformações unidirecionais.
 #10.4.2    Nível: 1    Função: D/V
 Verifique se os limites de taxa de consulta restringem consultas adaptativas repetidas do mesmo principal.
 #10.4.3    Nível: 2    Função: D
 Verifique se o modelo foi treinado com ruído preservador de privacidade.

---

### 10.5 Defesa contra Extração de Modelo

Detectar e impedir clonagem não autorizada. Recomenda-se marcação digital e análise de padrões de consulta.

 #10.5.1    Nível: 1    Função: D
 Verifique se os gateways de inferência aplicam limites de taxa globais e por chave de API ajustados ao limite de memorização do modelo.
 #10.5.2    Nível: 2    Função: D/V
 Verifique se as estatísticas de entropia da consulta e pluralidade de entrada alimentam um detector de extração automatizado.
 #10.5.3    Nível: 2    Função: V
 Verifique se marcas d'água frágeis ou probabilísticas podem ser comprovadas com p < 0,01 em ≤ 1 000 consultas contra um clone suspeito.
 #10.5.4    Nível: 3    Função: D
 Verifique se as chaves de marca d'água e os conjuntos de gatilho estão armazenados em um módulo de segurança de hardware e são rotacionados anualmente.
 #10.5.5    Nível: 3    Função: V
 Verifique se os eventos de extração-alerta incluem as consultas ofensivas e estão integrados com os playbooks de resposta a incidentes.

---

### 10.6 Detecção de Dados Envenenados em Tempo de Inferência

Identificar e neutralizar entradas com backdoor ou contaminadas.

 #10.6.1    Nível: 1    Função: D
 Verifique se as entradas passam por um detector de anomalias (por exemplo, STRIP, pontuação de consistência) antes da inferência do modelo.
 #10.6.2    Nível: 1    Função: V
 Verifique se os limiares dos detectores estão ajustados em conjuntos de validação limpos/envenenados para alcançar menos de 5% de falsos positivos.
 #10.6.3    Nível: 2    Função: D
 Verifique se as entradas marcadas como envenenadas acionam o bloqueio suave e os fluxos de trabalho de revisão humana.
 #10.6.4    Nível: 2    Função: V
 Verifique se os detectores são submetidos a testes de estresse com ataques de backdoor adaptativos e sem gatilho.
 #10.6.5    Nível: 3    Função: D
 Verifique se as métricas de eficácia da detecção são registradas e reavaliadas periodicamente com informações atualizadas sobre ameaças.

---

### 10.7 Adaptação Dinâmica de Política de Segurança

Atualizações em tempo real das políticas de segurança baseadas em inteligência de ameaças e análise comportamental.

 #10.7.1    Nível: 1    Função: D/V
 Verifique se as políticas de segurança podem ser atualizadas dinamicamente sem a necessidade de reiniciar o agente, mantendo a integridade da versão da política.
 #10.7.2    Nível: 2    Função: D/V
 Verifique se as atualizações de políticas são assinadas criptograficamente por pessoal de segurança autorizado e validadas antes da aplicação.
 #10.7.3    Nível: 2    Função: D/V
 Verifique se as alterações dinâmicas de políticas são registradas com trilhas completas de auditoria, incluindo justificativa, cadeias de aprovação e procedimentos de reversão.
 #10.7.4    Nível: 3    Função: D/V
 Verifique se os mecanismos de segurança adaptativa ajustam a sensibilidade da detecção de ameaças com base no contexto de risco e nos padrões comportamentais.
 #10.7.5    Nível: 3    Função: D/V
 Verifique se as decisões de adaptação da política são explicáveis e incluem trilhas de evidência para a revisão da equipe de segurança.

---

### 10.8 Análise de Segurança Baseada em Reflexão

Validação de segurança através da autorreflexão do agente e análise metacognitiva.

 #10.8.1    Nível: 1    Função: D/V
 Verifique se os mecanismos de reflexão do agente incluem autoavaliação focada em segurança das decisões e ações.
 #10.8.2    Nível: 2    Função: D/V
 Verifique se as saídas de reflexão são validadas para evitar a manipulação de mecanismos de autoavaliação por entradas adversárias.
 #10.8.3    Nível: 2    Função: D/V
 Verifique se a análise de segurança metacognitiva identifica possíveis vieses, manipulação ou comprometimento nos processos de raciocínio do agente.
 #10.8.4    Nível: 3    Função: D/V
 Verifique se os avisos de segurança baseados em reflexão acionam o monitoramento aprimorado e potenciais fluxos de trabalho de intervenção humana.
 #10.8.5    Nível: 3    Função: D/V
 Verifique que o aprendizado contínuo a partir de reflexões de segurança melhora a detecção de ameaças sem degradar a funcionalidade legítima.

---

### 10.9 Segurança de Evolução e Autoaperfeiçoamento

Controles de segurança para sistemas agentes capazes de auto-modificação e evolução.

 #10.9.1    Nível: 1    Função: D/V
 Verifique se as capacidades de auto-modificação estão restritas a áreas designadas como seguras, com limites de verificação formal.
 #10.9.2    Nível: 2    Função: D/V
 Verifique se as propostas de evolução passam por uma avaliação de impacto de segurança antes da implementação.
 #10.9.3    Nível: 2    Função: D/V
 Verifique se os mecanismos de autoaperfeiçoamento incluem capacidades de reversão com verificação de integridade.
 #10.9.4    Nível: 3    Função: D/V
 Verifique se a segurança de meta-aprendizado evita a manipulação adversarial dos algoritmos de aprimoramento.
 #10.9.5    Nível: 3    Função: D/V
 Verifique se a autoaperfeiçoamento recursivo está limitado por restrições formais de segurança com provas matemáticas de convergência.

---

#### Referências

MITRE ATLAS adversary tactics for ML
NIST AI Risk Management Framework 1.0, 2023
OWASP Top 10 for LLM Applications, 2025
Adversarial Training: A Survey — Zhao et al., 2024
RobustBench adversarial-robustness benchmark
Membership-Inference & Model-Inversion Risk Survey, 2025
PURIFIER: Confidence-Score Defense against MI Attacks — AAAI 2023
Model-Inversion Attacks & Defenses Survey — AI Review, 2025
Comprehensive Defense Framework Against Model Extraction — IEEE TDSC 2024
Fragile Model Watermarking Survey — 2025
Data Poisoning in Deep Learning: A Survey — Zhao et al., 2025
BDetCLIP: Multimodal Prompting Backdoor Detection — Niu et al., 2024

## 11 Proteção de Privacidade & Gestão de Dados Pessoais

### Objetivo de Controle

Mantenha garantias rigorosas de privacidade em todo o ciclo de vida da IA—coleta, treinamento, inferência e resposta a incidentes—para que os dados pessoais sejam processados apenas com consentimento claro, escopo mínimo necessário, apagamento comprovável e garantias formais de privacidade.

---

### 11.1 Anonimização e Minimização de Dados

 #11.1.1    Nível: 1    Função: D/V
 Verifique se os identificadores diretos e quase identificadores foram removidos ou hashados.
 #11.1.2    Nível: 2    Função: D/V
 Verifique se auditorias automatizadas medem k-anonimato/l-diversidade e alertam quando os limites caem abaixo da política.
 #11.1.3    Nível: 2    Função: V
 Verifique se os relatórios de importância de características do modelo provam que não há vazamento de identificador além de ε = 0,01 de informação mútua.
 #11.1.4    Nível: 3    Função: V
 Verifique se provas formais ou certificação por dados sintéticos mostram que o risco de reidentificação é ≤ 0,05 mesmo sob ataques de vinculação.

---

### 11.2 Direito ao Esquecimento e Aplicação da Exclusão

 #11.2.1    Nível: 1    Função: D/V
 Verifique se as solicitações de exclusão de dados de sujeitos são propagadas para conjuntos de dados brutos, pontos de verificação, embeddings, registros e backups dentro de acordos de nível de serviço inferiores a 30 dias.
 #11.2.2    Nível: 2    Função: D
 Verifique se as rotinas de "desaprendizado de máquina" re-treinam fisicamente ou aproximam a remoção usando algoritmos certificados de desaprendizado.
 #11.2.3    Nível: 2    Função: V
 Verifique que a avaliação do modelo sombra prova que os registros esquecidos influenciam menos de 1% das saídas após o desenraizamento.
 #11.2.4    Nível: 3    Função: V
 Verifique se os eventos de exclusão são registrados de forma imutável e auditável para os reguladores.

---

### 11.3 Salvaguardas de Privacidade Diferencial

 #11.3.1    Nível: 2    Função: D/V
 Verificar se os painéis de controle de contabilização da perda de privacidade alertam quando o ε cumulativo excede os limites da política.
 #11.3.2    Nível: 2    Função: V
 Verifique se as auditorias de privacidade black-box estimam ε̂ dentro de 10% do valor declarado.
 #11.3.3    Nível: 3    Função: V
 Verifique se as provas formais abrangem todos os ajustes finos e embeddings pós-treinamento.

---

### 11.4 Limitação de propósito e proteção contra expansão de escopo

 #11.4.1    Nível: 1    Função: D
 Verifique se todo conjunto de dados e ponto de verificação do modelo possui uma etiqueta de propósito legível por máquina alinhada ao consentimento original.
 #11.4.2    Nível: 1    Função: D/V
 Verifique se os monitores de tempo de execução detectam consultas inconsistentes com o propósito declarado e acionam uma recusa suave.
 #11.4.3    Nível: 3    Função: D
 Verifique se os controles de política como código bloqueiam a reimplantação de modelos para novos domínios sem revisão de DPIA.
 #11.4.4    Nível: 3    Função: V
 Verifique se as provas formais de rastreabilidade mostram que todo o ciclo de vida dos dados pessoais permanece dentro do escopo consentido.

---

### 11.5 Gestão de Consentimento e Rastreio com Base Legal

 #11.5.1    Nível: 1    Função: D/V
 Verifique se uma Plataforma de Gestão de Consentimento (CMP) registra o status de aceitação, o propósito e o período de retenção por titular dos dados.
 #11.5.2    Nível: 2    Função: D
 Verifique se as APIs expõem tokens de consentimento; os modelos devem validar o escopo do token antes da inferência.
 #11.5.3    Nível: 2    Função: D/V
 Verifique que o consentimento negado ou retirado interrompe os pipelines de processamento dentro de 24 horas.

---

### 11.6 Aprendizado Federado com Controles de Privacidade

 #11.6.1    Nível: 1    Função: D
 Verifique se as atualizações do cliente utilizam adição de ruído de privacidade diferencial local antes da agregação.
 #11.6.2    Nível: 2    Função: D/V
 Verifique se as métricas de treinamento são diferencialmente privadas e nunca revelam a perda de um único cliente.
 #11.6.3    Nível: 2    Função: V
 Verifique se a agregação resistente a contaminação (por exemplo, Krum/Trimmed-Mean) está habilitada.
 #11.6.4    Nível: 3    Função: V
 Verifique se as provas formais demonstram um orçamento total de ε com menos de 5 de perda de utilidade.

---

#### Referências

GDPR & AI Compliance Best Practices
EU Parliament Study on GDPR & AI, 2020
ISO 31700-1:2023 — Privacy by Design for Consumer Products
NIST Privacy Framework 1.1 (2025 Draft)
Machine Unlearning: Right-to-Be-Forgotten Techniques
A Survey of Machine Unlearning, 2024
Auditing DP-SGD — ArXiv 2024
DP-SGD Explained — PyTorch Blog
Purpose-Limitation for AI — IJLIT 2025
Data-Protection Considerations for AI — URM Consulting
Top Consent-Management Platforms, 2025
Secure Aggregation in DP Federated Learning — ArXiv 2024

## C12 Monitoramento, Registro e Detecção de Anomalias

### Objetivo de Controle

Esta seção fornece requisitos para oferecer visibilidade em tempo real e forense sobre o que o modelo e outros componentes de IA veem, fazem e retornam, para que ameaças possam ser detectadas, triadas e analisadas.

### C12.1 Registro de Requisições e Respostas

 #12.1.1    Nível: 1    Função: D/V
 Verifique se todas as solicitações do usuário e as respostas do modelo estão registradas com os metadados apropriados (por exemplo, carimbo de data/hora, ID do usuário, ID da sessão, versão do modelo).
 #12.1.2    Nível: 1    Função: D/V
 Verifique se os logs são armazenados em repositórios seguros, com controle de acesso, políticas de retenção apropriadas e procedimentos de backup.
 #12.1.3    Nível: 1    Função: D/V
 Verifique se os sistemas de armazenamento de logs implementam criptografia em repouso e em trânsito para proteger as informações sensíveis contidas nos logs.
 #12.1.4    Nível: 1    Função: D/V
 Verifique se os dados sensíveis nos prompts e nas saídas são automaticamente redigidos ou mascarados antes do registro, com regras de redacção configuráveis para informações pessoais identificáveis (PII), credenciais e informações proprietárias.
 #12.1.5    Nível: 2    Função: D/V
 Verifique se as decisões de política e as ações de filtragem de segurança são registradas com detalhes suficientes para permitir auditoria e depuração dos sistemas de moderação de conteúdo.
 #12.1.6    Nível: 2    Função: D/V
 Verifique se a integridade dos logs está protegida por meio de, por exemplo, assinaturas criptográficas ou armazenamento somente para gravação.

---

### C12.2 Detecção e Alerta de Abuso

 #12.2.1    Nível: 1    Função: D/V
 Verifique se o sistema detecta e alerta sobre padrões conhecidos de jailbreak, tentativas de injeção de prompt e entradas adversariais usando detecção baseada em assinatura.
 #12.2.2    Nível: 1    Função: D/V
 Verifique se o sistema se integra com as plataformas existentes de Gerenciamento de Informações e Eventos de Segurança (SIEM) usando formatos e protocolos de log padrão.
 #12.2.3    Nível: 2    Função: D/V
 Verifique se os eventos de segurança enriquecidos incluem contexto específico de IA, como identificadores de modelos, pontuações de confiança e decisões de filtros de segurança.
 #12.2.4    Nível: 2    Função: D/V
 Verifique se a detecção de anomalias comportamentais identifica padrões incomuns de conversa, tentativas excessivas de repetição ou comportamentos sistemáticos de sondagem.
 #12.2.5    Nível: 2    Função: D/V
 Verifique se os mecanismos de alerta em tempo real notificam as equipes de segurança quando possíveis violações de políticas ou tentativas de ataque são detectadas.
 #12.2.6    Nível: 2    Função: D/V
 Verifique se as regras personalizadas estão incluídas para detectar padrões de ameaças específicas de IA, incluindo tentativas coordenadas de jailbreak, campanhas de injeção de prompt e ataques de extração de modelo.
 #12.2.7    Nível: 3    Função: D/V
 Verifique se os fluxos de trabalho automatizados de resposta a incidentes podem isolar modelos comprometidos, bloquear usuários mal-intencionados e escalar eventos críticos de segurança.

---

### C12.3 Detecção de Deriva de Modelo

 #12.3.1    Nível: 1    Função: D/V
 Verifique se o sistema acompanha métricas básicas de desempenho, como precisão, escores de confiança, latência e taxas de erro, ao longo das versões do modelo e períodos de tempo.
 #12.3.2    Nível: 2    Função: D/V
 Verifique se os alertas automáticos são acionados quando as métricas de desempenho excedem os limiares de degradação pré-definidos ou se desviam significativamente das linhas de base.
 #12.3.3    Nível: 2    Função: D/V
 Verifique se os monitores de detecção de alucinação identificam e sinalizam casos em que as saídas do modelo contêm informações factualmente incorretas, inconsistentes ou fabricadas.

---

### C12.4 Telemetria de Desempenho e Comportamento

 #12.4.1    Nível: 1    Função: D/V
 Verifique se as métricas operacionais, incluindo latência de requisição, consumo de tokens, uso de memória e taxa de transferência, estão sendo continuamente coletadas e monitoradas.
 #12.4.2    Nível: 1    Função: D/V
 Verifique se as taxas de sucesso e fracasso são monitoradas com a categorização dos tipos de erro e suas causas raiz.
 #12.4.3    Nível: 2    Função: D/V
 Verifique se o monitoramento da utilização dos recursos inclui o uso de GPU/CPU, consumo de memória e requisitos de armazenamento, com alertas em caso de violação dos limites estabelecidos.

---

### C12.5 Planejamento e Execução de Resposta a Incidentes de IA

 #12.5.1    Nível: 1    Função: D/V
 Verifique se os planos de resposta a incidentes abordam especificamente eventos de segurança relacionados à IA, incluindo comprometimento de modelos, envenenamento de dados e ataques adversariais.
 #12.5.2    Nível: 2    Função: D/V
 Verifique se as equipes de resposta a incidentes têm acesso a ferramentas forenses específicas de IA e experiência para investigar o comportamento do modelo e os vetores de ataque.
 #12.5.3    Nível: 3    Função: D/V
 Verifique se a análise pós-incidente inclui considerações sobre re-treinamento do modelo, atualizações do filtro de segurança e a integração das lições aprendidas nos controles de segurança.

---

### C12.5 Detecção de Degradação de Desempenho em IA

Monitorar e detectar a degradação no desempenho e na qualidade do modelo de IA ao longo do tempo.

 #12.5.1    Nível: 1    Função: D/V
 Verifique se a precisão, precisão, recall e as pontuações F1 do modelo são monitoradas continuamente e comparadas com os limiares de referência.
 #12.5.2    Nível: 1    Função: D/V
 Verifique se a detecção de desvio de dados monitora mudanças na distribuição de entrada que podem impactar o desempenho do modelo.
 #12.5.3    Nível: 2    Função: D/V
 Verifique se a detecção de desvio de conceito identifica mudanças na relação entre entradas e saídas esperadas.
 #12.5.4    Nível: 2    Função: D/V
 Verifique se a degradação do desempenho aciona alertas automáticos e inicia fluxos de trabalho de retreinamento ou substituição do modelo.
 #12.5.5    Nível: 3    Função: V
 Verifique se a análise da causa raiz da degradação correlaciona as quedas de desempenho com mudanças nos dados, problemas na infraestrutura ou fatores externos.

---

### C12.6 Visualização de DAG e Segurança do Fluxo de Trabalho

Proteja os sistemas de visualização de fluxos de trabalho contra vazamento de informações e ataques de manipulação.

 #12.6.1    Nível: 1    Função: D/V
 Verifique se os dados de visualização do DAG estão sanitizados para remover informações sensíveis antes do armazenamento ou transmissão.
 #12.6.2    Nível: 1    Função: D/V
 Verifique se os controles de acesso da visualização do fluxo de trabalho garantem que somente usuários autorizados possam visualizar os caminhos de decisão do agente e os rastros de raciocínio.
 #12.6.3    Nível: 2    Função: D/V
 Verifique se a integridade dos dados do DAG está protegida por meio de assinaturas criptográficas e mecanismos de armazenamento à prova de adulteração.
 #12.6.4    Nível: 2    Função: D/V
 Verifique se os sistemas de visualização de fluxo de trabalho implementam validação de entrada para prevenir ataques de injeção através de dados manipulados de nós ou arestas.
 #12.6.5    Nível: 3    Função: D/V
 Verifique se as atualizações em tempo real do DAG são limitadas em taxa e validadas para evitar ataques de negação de serviço em sistemas de visualização.

---

### C12.7 Monitoramento Proativo de Comportamento de Segurança

Detecção e prevenção de ameaças à segurança por meio da análise proativa do comportamento de agentes.

 #12.7.1    Nível: 1    Função: D/V
 Verifique se os comportamentos proativos do agente são validados quanto à segurança antes da execução, com integração de avaliação de risco.
 #12.7.2    Nível: 2    Função: D/V
 Verifique se os gatilhos da iniciativa autônoma incluem avaliação do contexto de segurança e análise do cenário de ameaças.
 #12.7.3    Nível: 2    Função: D/V
 Verifique se os padrões de comportamento proativo são analisados quanto às potenciais implicações de segurança e consequências não intencionais.
 #12.7.4    Nível: 3    Função: D/V
 Verifique se as ações proativas críticas para a segurança exigem cadeias de aprovação explícitas com trilhas de auditoria.
 #12.7.5    Nível: 3    Função: D/V
 Verifique se a detecção de anomalias comportamentais identifica desvios nos padrões do agente proativo que podem indicar comprometimento.

---

### Referências

NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3
ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6
EU AI Act — Article 12, 13, 16 and 19 on Logging and Record-keeping

## C13 Supervisão Humana, Responsabilidade e Governança

### Objetivo de Controle

Este capítulo fornece requisitos para manter a supervisão humana e cadeias claras de responsabilidade em sistemas de IA, garantindo explicabilidade, transparência e gestão ética ao longo do ciclo de vida da IA.

---

### C13.1 Mecanismos de Interruptor de Emergência e Substituição

Forneça caminhos de desligamento ou reversão quando for observado comportamento inseguro do sistema de IA.

 #13.1.1    Nível: 1    Função: D/V
 Verifique se existe um mecanismo manual de interrupção para parar imediatamente a inferência e as saídas do modelo de IA.
 #13.1.2    Nível: 1    Função: D
 Verifique se os controles de substituição são acessíveis apenas ao pessoal autorizado.
 #13.1.3    Nível: 3    Função: D/V
 Verifique se os procedimentos de reversão podem reverter para versões anteriores do modelo ou operações em modo seguro.
 #13.1.4    Nível: 3    Função: V
 Verifique se os mecanismos de substituição são testados regularmente.

---

### C13.2 Pontos de Verificação de Decisão com Intervenção Humana

Exigir aprovações humanas quando os riscos ultrapassam os limites predefinidos.

 #13.2.1    Nível: 1    Função: D/V
 Verifique se decisões de IA de alto risco exigem aprovação humana explícita antes da execução.
 #13.2.2    Nível: 1    Função: D
 Verifique se os limites de risco estão claramente definidos e acionam automaticamente os fluxos de trabalho de revisão humana.
 #13.2.3    Nível: 2    Função: D
 Verifique se as decisões sensíveis ao tempo possuem procedimentos alternativos quando a aprovação humana não pode ser obtida dentro dos prazos exigidos.
 #13.2.4    Nível: 3    Função: D/V
 Verifique se os procedimentos de escalonamento definem níveis claros de autoridade para diferentes tipos de decisão ou categorias de risco, se aplicável.

---

### C13.3 Cadeia de Responsabilidade e Auditabilidade

Registrar as ações do operador e as decisões do modelo.

 #13.3.1    Nível: 1    Função: D/V
 Verifique se todas as decisões do sistema de IA e intervenções humanas são registradas com carimbos de data e hora, identidades dos usuários e justificativas das decisões.
 #13.3.2    Nível: 2    Função: D
 Verifique se os logs de auditoria não podem ser adulterados e incluem mecanismos de verificação de integridade.

---

### C13.4 Técnicas de IA Explicável

Importância das características superficiais, contra-factuais e explicações locais.

 #13.4.1    Nível: 1    Função: D/V
 Verifique se os sistemas de IA fornecem explicações básicas para suas decisões em formato compreensível para humanos.
 #13.4.2    Nível: 2    Função: V
 Verifique se a qualidade da explicação é validada por meio de estudos e métricas de avaliação humana.
 #13.4.3    Nível: 3    Função: D/V
 Verifique se as pontuações de importância de características ou métodos de atribuição (SHAP, LIME, etc.) estão disponíveis para decisões críticas.
 #13.4.4    Nível: 3    Função: V
 Verifique se as explicações contrafactuais mostram como os inputs podem ser modificados para alterar os resultados, se aplicável ao caso de uso e ao domínio.

---

### C13.5 Cartões de Modelo e Divulgações de Uso

Manter cartões de modelo para uso pretendido, métricas de desempenho e considerações éticas.

 #13.5.1    Nível: 1    Função: D
 Verifique se os cartões de modelo documentam os casos de uso pretendidos, limitações e modos de falha conhecidos.
 #13.5.2    Nível: 1    Função: D/V
 Verifique se as métricas de desempenho em diferentes casos de uso aplicáveis estão divulgadas.
 #13.5.3    Nível: 2    Função: D
 Verifique se as considerações éticas, avaliações de viés, avaliações de justiça, características dos dados de treinamento e limitações conhecidas dos dados de treinamento estão documentadas e atualizadas regularmente.
 #13.5.4    Nível: 2    Função: D/V
 Verifique se os cartões do modelo estão sob controle de versão e são mantidos durante todo o ciclo de vida do modelo com rastreamento de alterações.

---

### C13.6 Quantificação da Incerteza

Propagar pontuações de confiança ou medidas de entropia nas respostas.

 #13.6.1    Nível: 1    Função: D
 Verifique se os sistemas de IA fornecem pontuações de confiança ou medidas de incerteza com seus resultados.
 #13.6.2    Nível: 2    Função: D/V
 Verifique se os limites de incerteza acionam uma revisão humana adicional ou caminhos alternativos de decisão.
 #13.6.3    Nível: 2    Função: V
 Verifique se os métodos de quantificação de incerteza estão calibrados e validados com dados de referência.
 #13.6.4    Nível: 3    Função: D/V
 Verifique se a propagação da incerteza é mantida ao longo de fluxos de trabalho de IA em múltiplas etapas.

---

### C13.7 Relatórios de Transparência para o Usuário Final

Fornecer divulgações periódicas sobre incidentes, deriva e uso de dados.

 #13.7.1    Nível: 1    Função: D/V
 Verifique se as políticas de uso de dados e as práticas de gestão do consentimento do usuário são claramente comunicadas às partes interessadas.
 #13.7.2    Nível: 2    Função: D/V
 Verifique se as avaliações de impacto da IA são realizadas e se os resultados estão incluídos nos relatórios.
 #13.7.3    Nível: 2    Função: D/V
 Verifique se os relatórios de transparência publicados regularmente divulgam incidentes de IA e métricas operacionais com detalhes razoáveis.

#### Referências

EU Artificial Intelligence Act — Regulation (EU) 2024/1689 (Official Journal, 12 July 2024)
ISO/IEC 23894:2023 — Artificial Intelligence — Guidance on Risk Management
ISO/IEC 42001:2023 — AI Management Systems Requirements
NIST AI Risk Management Framework 1.0
NIST SP 800-53 Revision 5 — Security and Privacy Controls
A Unified Approach to Interpreting Model Predictions (SHAP, ICML 2017)
Model Cards for Model Reporting (Mitchell et al., 2018)
Dropout as a Bayesian Approximation: Representing Model Uncertainty in Deep Learning (Gal & Ghahramani, 2016)
ISO/IEC 24029-2:2023 — Robustness of Neural Networks — Methodology for Formal Methods
IEEE 7001-2021 — Transparency of Autonomous Systems
GDPR — Article 5 "Transparency Principle" (Regulation (EU) 2016/679)
Human Oversight under Article 14 of the EU AI Act (Fink, 2025)

## Apêndice A: Glossário

Este glossário abrangente fornece definições dos principais termos de IA, ML e segurança usados ao longo do AISVS para garantir clareza e entendimento comum.

Exemplo Adversarial: Uma entrada deliberadamente criada para fazer um modelo de IA cometer um erro, frequentemente adicionando perturbações sutis imperceptíveis para os humanos.
​
Robustez Adversarial – Robustez adversarial em IA refere-se à capacidade de um modelo de manter seu desempenho e resistir a ser enganado ou manipulado por entradas maliciosas intencionalmente criadas para causar erros.
​
Agente – Agentes de IA são sistemas de software que utilizam IA para buscar objetivos e completar tarefas em nome dos usuários. Eles apresentam raciocínio, planejamento e memória, e possuem um nível de autonomia para tomar decisões, aprender e se adaptar.
​
IA Agente: sistemas de IA que podem operar com algum grau de autonomia para alcançar objetivos, muitas vezes tomando decisões e realizando ações sem intervenção humana direta.
​
Controle de Acesso Baseado em Atributos (ABAC): Um paradigma de controle de acesso onde as decisões de autorização são baseadas em atributos do usuário, recurso, ação e ambiente, avaliados no momento da consulta.
​
Ataque de Backdoor: Um tipo de ataque de envenenamento de dados onde o modelo é treinado para responder de uma maneira específica a certos gatilhos, enquanto se comporta normalmente em outras situações.
​
Viés: Erros sistemáticos nos resultados de modelos de IA que podem levar a desfechos injustos ou discriminatórios para certos grupos ou em contextos específicos.
​
Exploração de Viés: Uma técnica de ataque que aproveita os vieses conhecidos em modelos de IA para manipular resultados ou desfechos.
​
Cedar: linguagem e mecanismo de política da Amazon para permissões detalhadas usadas na implementação de ABAC para sistemas de IA.
​
Cadeia de Pensamento: Uma técnica para melhorar o raciocínio em modelos de linguagem, gerando etapas intermediárias de raciocínio antes de produzir uma resposta final.
​
Disjuntores: Mecanismos que interrompem automaticamente as operações do sistema de IA quando limites específicos de risco são excedidos.
​
Vazamento de Dados: exposição não intencional de informações sensíveis por meio de saídas ou comportamento de modelos de IA.
​
Envenenamento de Dados: A corrupção deliberada dos dados de treinamento para comprometer a integridade do modelo, frequentemente para instalar backdoors ou degradar o desempenho.
​
Privacidade Diferencial – Privacidade diferencial é uma estrutura matematicamente rigorosa para divulgar informações estatísticas sobre conjuntos de dados enquanto protege a privacidade dos indivíduos. Ela permite que um detentor de dados compartilhe padrões agregados do grupo, limitando as informações que são reveladas sobre indivíduos específicos.
​
Incorporações: Representações vetoriais densas de dados (texto, imagens, etc.) que capturam o significado semântico em um espaço de alta dimensão.
​
Explicabilidade – Explicabilidade em IA é a capacidade de um sistema de IA de fornecer razões compreensíveis para humanos sobre suas decisões e previsões, oferecendo insights sobre seu funcionamento interno.
​
IA Explicável (XAI): sistemas de IA projetados para fornecer explicações compreensíveis por humanos para suas decisões e comportamentos por meio de várias técnicas e estruturas.
​
Aprendizado Federado: Uma abordagem de aprendizado de máquina onde os modelos são treinados em múltiplos dispositivos descentralizados que possuem amostras de dados locais, sem a troca dos dados em si.
​
Guardrails: Restrições implementadas para evitar que sistemas de IA produzam resultados prejudiciais, tendenciosos ou indesejáveis.
​
Alucinação – Uma alucinação de IA refere-se a um fenômeno em que um modelo de IA gera informações incorretas ou enganosas que não são baseadas em seus dados de treinamento ou na realidade factual.
​
Humano no Loop (HITL): Sistemas projetados para exigir supervisão, verificação ou intervenção humana em pontos decisivos cruciais.
​
Infraestrutura como Código (IaC): Gerenciamento e provisionamento de infraestrutura por meio de código em vez de processos manuais, permitindo a análise de segurança e implantações consistentes.
​
Jailbreak: Técnicas usadas para contornar as barreiras de segurança em sistemas de IA, particularmente em grandes modelos de linguagem, para produzir conteúdo proibido.
​
Privilégio Mínimo: O princípio de segurança de conceder apenas os direitos de acesso mínimos necessários para usuários e processos.
​
LIME (Explicações Localmente Interpretáveis Independentes de Modelo): Uma técnica para explicar as previsões de qualquer classificador de aprendizado de máquina aproximando-o localmente com um modelo interpretável.
​
Ataque de Inferência de Associação: Um ataque que tem como objetivo determinar se um ponto de dados específico foi usado para treinar um modelo de aprendizado de máquina.
​
MITRE ATLAS: Panorama de Ameaças Adversárias para Sistemas de Inteligência Artificial; uma base de conhecimento de táticas e técnicas adversárias contra sistemas de IA.
​
Modelo de Cartão – Um modelo de cartão é um documento que fornece informações padronizadas sobre o desempenho de um modelo de IA, limitações, usos pretendidos e considerações éticas para promover a transparência e o desenvolvimento responsável de IA.
​
Extração de Modelo: Um ataque onde um adversário consulta repetidamente um modelo-alvo para criar uma cópia funcionalmente semelhante sem autorização.
​
Inversão de Modelo: Um ataque que tenta reconstruir os dados de treinamento analisando as saídas do modelo.
​
Gerenciamento do Ciclo de Vida do Modelo – O Gerenciamento do Ciclo de Vida do Modelo de IA é o processo de supervisionar todas as etapas da existência de um modelo de IA, incluindo seu design, desenvolvimento, implantação, monitoramento, manutenção e eventual aposentadoria, para garantir que ele permaneça eficaz e alinhado com os objetivos.
​
Envenenamento de Modelo: Introdução de vulnerabilidades ou portas dos fundos diretamente em um modelo durante o processo de treinamento.
​
Roubo/Extravio de Modelo: Extrair uma cópia ou aproximação de um modelo proprietário por meio de consultas repetidas.
​
Sistema Multiagente: Um sistema composto por múltiplos agentes de IA interagindo, cada um com capacidades e objetivos potencialmente diferentes.
​
OPA (Open Policy Agent): Um motor de políticas open-source que permite a aplicação unificada de políticas em toda a stack.
​
Aprendizado de Máquina que Preserva a Privacidade (PPML): Técnicas e métodos para treinar e implantar modelos de ML enquanto protegem a privacidade dos dados de treinamento.
​
Injeção de Prompt: Um ataque onde instruções maliciosas são incorporadas nas entradas para substituir o comportamento pretendido de um modelo.
​
RAG (Geração Aumentada por Recuperação): Uma técnica que aprimora grandes modelos de linguagem recuperando informações relevantes de fontes externas de conhecimento antes de gerar uma resposta.
​
Red-Teaming: A prática de testar ativamente sistemas de IA simulando ataques adversários para identificar vulnerabilidades.
​
SBOM (Lista de Materiais de Software): Um registro formal contendo os detalhes e as relações da cadeia de suprimentos de vários componentes usados na construção de software ou modelos de IA.
​
SHAP (SHapley Additive exPlanations): Uma abordagem baseada na teoria dos jogos para explicar a saída de qualquer modelo de aprendizado de máquina calculando a contribuição de cada característica para a previsão.
​
Ataque à Cadeia de Suprimentos: Comprometer um sistema ao visar elementos menos seguros em sua cadeia de suprimentos, como bibliotecas de terceiros, conjuntos de dados ou modelos pré-treinados.
​
Aprendizado por Transferência: Uma técnica onde um modelo desenvolvido para uma tarefa é reutilizado como ponto de partida para um modelo em uma segunda tarefa.
​
Banco de Dados Vetorial: Um banco de dados especializado projetado para armazenar vetores de alta dimensão (incorporações) e realizar buscas eficientes por similaridade.
​
Varredura de Vulnerabilidades: Ferramentas automatizadas que identificam vulnerabilidades de segurança conhecidas em componentes de software, incluindo frameworks de IA e dependências.
​
Marcação d'água: Técnicas para incorporar marcadores imperceptíveis em conteúdos gerados por IA para rastrear sua origem ou detectar geração por IA.
​
Vulnerabilidade Zero-Day: Uma vulnerabilidade previamente desconhecida que atacantes podem explorar antes que os desenvolvedores criem e implementem uma correção.

## Apêndice B: Referências

### TODO

## Apêndice C: Governança e Documentação de Segurança em IA

### Objetivo

Este apêndice fornece os requisitos fundamentais para estabelecer estruturas organizacionais, políticas e processos para governar a segurança de IA ao longo do ciclo de vida do sistema.

---

### AC.1 Adoção do Framework de Gestão de Riscos em IA

Fornecer uma estrutura formal para identificar, avaliar e mitigar riscos específicos de IA ao longo do ciclo de vida do sistema.

 #AC.1.1    Nível: 1    Função: D/V
 Verifique se uma metodologia de avaliação de risco específica para IA está documentada e implementada.
 #AC.1.2    Nível: 2    Função: D
 Verifique se as avaliações de risco são realizadas em pontos-chave do ciclo de vida da IA e antes de mudanças significativas.
 #AC.1.3    Nível: 3    Função: D/V
 Verifique se o framework de gerenciamento de riscos está alinhado com os padrões estabelecidos (por exemplo, NIST AI RMF).

---

### AC.2 Política e Procedimentos de Segurança de IA

Defina e aplique padrões organizacionais para o desenvolvimento, implantação e operação seguros de IA.

 #AC.2.1    Nível: 1    Função: D/V
 Verifique se existem políticas de segurança de IA documentadas.
 #AC.2.2    Nível: 2    Função: D
 Verifique se as políticas são revisadas e atualizadas pelo menos anualmente e após mudanças significativas no cenário de ameaças.
 #AC.2.3    Nível: 3    Função: D/V
 Verifique se as políticas abordam todas as categorias AISVS e os requisitos regulatórios aplicáveis.

---

### AC.3 Funções e Responsabilidades para Segurança em IA

Estabeleça uma responsabilidade clara pela segurança da IA em toda a organização.

 #AC.3.1    Nível: 1    Função: D/V
 Verifique se os papéis e responsabilidades de segurança de IA estão documentados.
 #AC.3.2    Nível: 2    Função: D
 Verifique se os indivíduos responsáveis possuem a expertise adequada em segurança.
 #AC.3.3    Nível: 3    Função: D/V
 Verifique se um comitê de ética em IA ou conselho de governança está estabelecido para sistemas de IA de alto risco.

---

### AC.4 Aplicação das Diretrizes Éticas para IA

Garantir que os sistemas de IA operem de acordo com os princípios éticos estabelecidos.

 #AC.4.1    Nível: 1    Função: D/V
 Verifique se existem diretrizes éticas para o desenvolvimento e a implantação de IA.
 #AC.4.2    Nível: 2    Função: D
 Verifique se existem mecanismos para detectar e relatar violações éticas.
 #AC.4.3    Nível: 3    Função: D/V
 Verifique se revisões éticas regulares dos sistemas de IA implantados são realizadas.

---

### AC.5 Monitoramento de Conformidade Regulamentar de IA

Mantenha a consciência e o cumprimento das regulamentações de IA em evolução.

 #AC.5.1    Nível: 1    Função: D/V
 Verifique se existem processos para identificar as regulamentações de IA aplicáveis.
 #AC.5.2    Nível: 2    Função: D
 Verifique se o cumprimento de todos os requisitos regulatórios foi avaliado.
 #AC.5.3    Nível: 3    Função: D/V
 Verifique se as mudanças regulatórias desencadeiam revisões e atualizações oportunas nos sistemas de IA.

### AC.6 Governança, Documentação e Processo de Dados de Treinamento

 #1.1.2    Nível: 1    Função: D/V
 Verifique se apenas conjuntos de dados avaliados quanto à qualidade, representatividade, origem ética e conformidade com licenças são permitidos, reduzindo os riscos de contaminação, viés incorporado e violação de propriedade intelectual.
 #1.1.5    Nível: 2    Função: D/V
 Verifique se a qualidade da rotulagem/anotação é garantida por meio de revisões cruzadas ou consenso entre os revisores.
 #1.1.6    Nível: 2    Função: D/V
 Verifique se "cartões de dados" ou "fichas técnicas para conjuntos de dados" são mantidos para conjuntos de dados de treinamento significativos, detalhando características, motivações, composição, processos de coleta, pré-processamento e usos recomendados/desencorajados.
 #1.3.2    Nível: 2    Função: D/V
 Verifique se os vieses identificados são mitigados por meio de estratégias documentadas, como reequilíbrio, aumento de dados direcionado, ajustes algorítmicos (por exemplo, técnicas de pré-processamento, processamento e pós-processamento) ou reponderação, e se o impacto da mitigação tanto na equidade quanto no desempenho geral do modelo é avaliado.
 #1.3.3    Nível: 2    Função: D/V
 Verifique se as métricas de justiça pós-treinamento são avaliadas e documentadas.
 #1.3.4    Nível: 3    Função: D/V
 Verifique se uma política de gerenciamento de viés do ciclo de vida atribui responsáveis e cadência de revisão.
 #1.4.1    Nível: 2    Função: D/V
 Verifique se a qualidade da rotulagem/anotação é garantida por meio de diretrizes claras, verificações cruzadas por revisores, mecanismos de consenso (por exemplo, monitoramento do acordo entre anotadores) e processos definidos para resolver discrepâncias.
 #1.4.4    Nível: 3    Função: D/V
 Verifique se os rótulos críticos para segurança, proteção ou equidade (por exemplo, identificação de conteúdo tóxico, descobertas médicas críticas) recebem revisão dupla independente mandatória ou verificação robusta equivalente.
 #1.4.6    Nível: 2    Função: D/V
 Verifique se os guias de rotulagem e as instruções são abrangentes, controlados por versão e revisados por pares.
 #1.4.6    Nível: 2    Função: D/V
 Verifique se os esquemas de dados para rótulos estão claramente definidos e com controle de versões.
 #1.3.1    Nível: 1    Função: D/V
 Verifique se os conjuntos de dados são perfilados quanto ao desequilíbrio representacional e potenciais vieses em atributos legalmente protegidos (por exemplo, raça, gênero, idade) e outras características eticamente sensíveis relevantes para o domínio de aplicação do modelo (por exemplo, status socioeconômico, localização).
 #1.5.3    Nível: 2    Função: V
 Verifique se as verificações manuais pontuais por especialistas da área abrangem uma amostra estatisticamente significativa (por exemplo, ≥1% ou 1.000 amostras, o que for maior, ou conforme determinado pela avaliação de risco) para identificar problemas sutis de qualidade não detectados pela automação.
 #1.8.4    Nível: 2    Função: D/V
 Verifique se os fluxos de trabalho de rotulagem terceirizados ou crowdsourced incluem salvaguardas técnicas/procedimentais para garantir a confidencialidade dos dados, integridade, qualidade dos rótulos e prevenir o vazamento de dados.
 #1.5.4    Nível: 2    Função: D/V
 Verifique se as etapas de remediação estão anexadas aos registros de proveniência.
 #1.6.2    Nível: 2    Função: D/V
 Verifique se as amostras sinalizadas acionam uma revisão manual antes do treinamento.
 #1.6.3    Nível: 2    Função: V
 Verifique se os resultados alimentam o dossiê de segurança do modelo e informam a inteligência contínua de ameaças.
 #1.6.4    Nível: 3    Função: D/V
 Verifique se a lógica de detecção foi atualizada com novas informações sobre ameaças.
 #1.6.5    Nível: 3    Função: D/V
 Verifique se os pipelines de aprendizado online monitoram a deriva de distribuição.
 #1.7.1    Nível: 1    Função: D/V
 Verifique se os fluxos de trabalho de exclusão de dados de treinamento eliminam dados primários e derivados e avalie o impacto no modelo, além de assegurar que o impacto nos modelos afetados seja avaliado e, se necessário, tratado (por exemplo, por meio de retreinamento ou recalibração).
 #1.7.2    Nível: 2    Função: D
 Verifique se existem mecanismos para rastrear e respeitar o escopo e o status do consentimento do usuário (e retiradas) para dados usados no treinamento, e se o consentimento é validado antes que os dados sejam incorporados em novos processos de treinamento ou atualizações significativas do modelo.
 #1.7.3    Nível: 2    Função: V
 Verifique se os fluxos de trabalho são testados anualmente e registrados.
 #1.8.1    Nível: 2    Função: D/V
 Verifique se os fornecedores de dados de terceiros, incluindo provedores de modelos pré-treinados e conjuntos de dados externos, passam por diligência prévia de segurança, privacidade, origem ética e qualidade dos dados antes que seus dados ou modelos sejam integrados.
 #1.8.2    Nível: 1    Função: D
 Verifique se as transferências externas utilizam TLS/autenticação e verificações de integridade.
 #1.8.3    Nível: 2    Função: D/V
 Verifique se as fontes de dados de alto risco (por exemplo, conjuntos de dados de código aberto com procedência desconhecida, fornecedores não avaliados) recebem uma análise aprimorada, como análise em ambiente isolado, verificações extensivas de qualidade/viés e detecção direcionada de contaminação, antes de serem usadas em aplicações sensíveis.
 #1.8.4    Nível: 3    Função: D/V
 Verifique se os modelos pré-treinados obtidos de terceiros são avaliados quanto a vieses incorporados, possíveis portas dos fundos, integridade de sua arquitetura e a proveniência dos dados originais de treinamento antes do ajuste fino ou da implantação.
 #1.5.3    Nível: 2    Função: D/V
 Verifique se, caso o treinamento adversarial seja utilizado, a geração, o gerenciamento e o versionamento dos conjuntos de dados adversariais estão documentados e controlados.
 #1.5.3    Nível: 3    Função: D/V
 Verifique se o impacto do treinamento de robustez adversarial no desempenho do modelo (tanto contra entradas limpas quanto adversariais) e nas métricas de justiça é avaliado, documentado e monitorado.
 #1.5.4    Nível: 3    Função: D/V
 Verifique se as estratégias para treinamento adversarial e robustez são periodicamente revisadas e atualizadas para combater técnicas de ataque adversarial em evolução.
 #1.4.2    Nível: 2    Função: D/V
 Verifique se os conjuntos de dados que falharam são isolados com trilhas de auditoria.
 #1.4.3    Nível: 2    Função: D/V
 Verifique se os portões de qualidade bloqueiam conjuntos de dados abaixo do padrão, a menos que exceções sejam aprovadas.
 #1.11.2    Nível: 2    Função: D/V
 Verifique se o processo de geração, os parâmetros e o uso pretendido dos dados sintéticos estão documentados.
 #1.11.3    Nível: 2    Função: D/V
 Verifique se os dados sintéticos são avaliados quanto a riscos de viés, vazamento de privacidade e problemas de representatividade antes de serem usados no treinamento.
 #1.12.3    Nível: 2    Função: D/V
 Verifique se os alertas são gerados para eventos de acesso suspeitos e investigados prontamente.
 #1.13.1    Nível: 1    Função: D/V
 Verifique se os períodos de retenção explícitos estão definidos para todos os conjuntos de dados de treinamento.
 #1.13.2    Nível: 2    Função: D/V
 Verifique se os conjuntos de dados são automaticamente expirados, apagados ou revisados para exclusão ao final do seu ciclo de vida.
 #1.13.3    Nível: 2    Função: D/V
 Verifique se as ações de retenção e exclusão são registradas e auditáveis.
 #1.14.1    Nível: 2    Função: D/V
 Verifique se os requisitos de residência de dados e transferência transfronteiriça são identificados e aplicados para todos os conjuntos de dados.
 #1.14.2    Nível: 2    Função: D/V
 Verifique se as regulamentações específicas do setor (por exemplo, saúde, finanças) são identificadas e abordadas no manuseio de dados.
 #1.14.3    Nível: 2    Função: D/V
 Verifique se a conformidade com as leis de privacidade relevantes (por exemplo, GDPR, CCPA) está documentada e revisada regularmente.
 #1.16.1    Nível: 2    Função: D/V
 Verifique se existem mecanismos para responder às solicitações dos titulares dos dados para acesso, retificação, restrição ou objeção.
 #1.16.2    Nível: 2    Função: D/V
 Verifique se as solicitações são registradas, acompanhadas e cumpridas dentro dos prazos legalmente estipulados.
 #1.16.3    Nível: 2    Função: D/V
 Verifique se os processos dos direitos dos titulares de dados são testados e revisados regularmente para garantir sua eficácia.
 #1.17.1    Nível: 2    Função: D/V
 Verifique se uma análise de impacto é realizada antes de atualizar ou substituir uma versão do conjunto de dados, abrangendo desempenho do modelo, equidade e conformidade.
 #1.17.2    Nível: 2    Função: D/V
 Verifique se os resultados da análise de impacto estão documentados e revisados pelos stakeholders relevantes.
 #1.17.3    Nível: 2    Função: D/V
 Verifique se existem planos de reversão caso novas versões introduzam riscos inaceitáveis ou regressões.
 #1.18.1    Nível: 2    Função: D/V
 Verifique se todo o pessoal envolvido na anotação de dados passou por verificação de antecedentes e foi treinado em segurança e privacidade de dados.
 #1.18.2    Nível: 2    Função: D/V
 Verifique se todo o pessoal de anotação assina acordos de confidencialidade e não divulgação.
 #1.18.3    Nível: 2    Função: D/V
 Verifique se as plataformas de anotação aplicam controles de acesso e monitoram ameaças internas.

#### Referências

NIST AI Risk Management Framework 1.0
ISO/IEC 42001:2023 — AI Management Systems Requirements
ISO/IEC 23894:2023 — Artificial Intelligence — Guidance on Risk Management
EU Artificial Intelligence Act — Regulation (EU) 2024/1689
ISO/IEC 24029‑2:2023 — Robustness of Neural Networks — Methodology for Formal Methods

## Apêndice D: Governança e Verificação de Codificação Segura Assistida por IA

### Objetivo

Este capítulo define controles organizacionais básicos para o uso seguro e eficaz de ferramentas de codificação assistidas por IA durante o desenvolvimento de software, garantindo segurança e rastreabilidade ao longo do SDLC.

---

### AD.1 Fluxo de Trabalho de Codificação Segura Assistida por IA

Integrar ferramentas de IA no ciclo de vida de desenvolvimento de software seguro (SSDLC) da organização sem enfraquecer as barreiras de segurança existentes.

 #AD.1.1    Nível: 1    Função: D/V
 Verifique se um fluxo de trabalho documentado descreve quando e como as ferramentas de IA podem gerar, refatorar ou revisar código.
 #AD.1.2    Nível: 2    Função: D
 Verifique se o fluxo de trabalho corresponde a cada fase do SSDLC (design, implementação, revisão de código, testes, implantação).
 #AD.1.3    Nível: 3    Função: D/V
 Verifique se as métricas (por exemplo, densidade de vulnerabilidades, tempo médio para detectar) são coletadas no código produzido por IA e comparadas com os parâmetros de referência exclusivamente humanos.

---

### AD.2 Qualificação de Ferramentas de IA e Modelagem de Ameaças

Garanta que as ferramentas de codificação de IA sejam avaliadas quanto a capacidades de segurança, risco e impacto na cadeia de suprimentos antes da adoção.

 #AD.2.1    Nível: 1    Função: D/V
 Verifique se um modelo de ameaça para cada ferramenta de IA identifica riscos de uso indevido, inversão de modelo, vazamento de dados e cadeia de dependência.
 #AD.2.2    Nível: 2    Função: D
 Verifique se as avaliações da ferramenta incluem análise estática/dinâmica de quaisquer componentes locais e avaliação dos pontos de extremidade SaaS (TLS, autenticação/autorização, registro de logs).
 #AD.2.3    Nível: 3    Função: D/V
 Verifique se as avaliações seguem uma estrutura reconhecida e são refeitas após alterações significativas de versão.

---

### AD.3 Gerenciamento Seguro de Prompt e Contexto

Prevenir o vazamento de segredos, código proprietário e dados pessoais ao construir prompts ou contextos para modelos de IA.

 #AD.3.1    Nível: 1    Função: D/V
 Verifique se as orientações escritas proíbem o envio de segredos, credenciais ou dados classificados em prompts.
 #AD.3.2    Nível: 2    Função: D
 Verifique se os controles técnicos (redação no lado do cliente, filtros de contexto aprovados) removem automaticamente artefatos sensíveis.
 #AD.3.3    Nível: 3    Função: D/V
 Verifique se os prompts e respostas são tokenizados, criptografados durante a transmissão e em repouso, e se os períodos de retenção estão em conformidade com a política de classificação de dados.

---

### AD.4 Validação de Código Gerado por IA

Detectar e remediar vulnerabilidades introduzidas pela saída de IA antes que o código seja mesclado ou implantado.

 #AD.4.1    Nível: 1    Função: D/V
 Verifique se o código gerado por IA está sempre sujeito a revisão humana.
 #AD.4.2    Nível: 2    Função: D
 Verifique se os scanners automatizados (SAST/IAST/DAST) são executados em cada pull request contendo código gerado por IA e bloqueie as mesclagens em caso de descobertas críticas.
 #AD.4.3    Nível: 3    Função: D/V
 Verifique se o teste fuzz diferencial ou os testes baseados em propriedades comprovam os comportamentos críticos para a segurança (por exemplo, validação de entrada, lógica de autorização).

---

### AD.5 Explicabilidade e Rastreabilidade das Sugestões de Código

Fornecer aos auditores e desenvolvedores uma visão sobre o motivo pelo qual uma sugestão foi feita e como ela evoluiu.

 #AD.5.1    Nível: 1    Função: D/V
 Verifique se os pares de prompt/resposta estão registrados com IDs de commit.
 #AD.5.2    Nível: 2    Função: D
 Verifique se os desenvolvedores podem exibir citações do modelo (trechos de treinamento, documentação) que sustentem uma sugestão.
 #AD.5.3    Nível: 3    Função: D/V
 Verifique se os relatórios de explicabilidade são armazenados com os artefatos de design e referenciados nas revisões de segurança, satisfazendo os princípios de rastreabilidade da ISO/IEC 42001.

---

### AD.6 Feedback Contínuo e Ajuste Fino do Modelo

Melhorar o desempenho de segurança do modelo ao longo do tempo, evitando deriva negativa.

 #AD.6.1    Nível: 1    Função: D/V
 Verifique se os desenvolvedores podem sinalizar sugestões inseguras ou não conformes, e se as sinalizações são rastreadas.
 #AD.6.2    Nível: 2    Função: D
 Verifique se o feedback agregado informa o ajuste fino periódico ou a geração aumentada por recuperação com corpora de codificação segura avaliados (por exemplo, OWASP Cheat Sheets).
 #AD.6.3    Nível: 3    Função: D/V
 Verifique se um ambiente de avaliação de loop fechado executa testes de regressão após cada ajuste fino; os métricos de segurança devem atender ou exceder as linhas de base anteriores antes da implantação.

---

#### Referências

NIST AI Risk Management Framework 1.0
ISO/IEC 42001:2023 — AI Management Systems Requirements
OWASP Secure Coding Practices — Quick Reference Guide

## Apêndice E: Exemplos de Ferramentas e Frameworks

### Objetivo

Este capítulo oferece exemplos de ferramentas e frameworks que podem apoiar a implementação ou o cumprimento de um determinado requisito AISVS. Estes não devem ser vistos como recomendações ou endossos pela equipe AISVS ou pelo Projeto de Segurança GenAI da OWASP.

---

### AE.1 Governança de Dados de Treinamento e Gestão de Viés

Ferramentas utilizadas para análise de dados, governança e gerenciamento de viés.

 #AE.1.1    Seção: 1.1
 Ferramentas de Inventário de Dados: Ferramentas de gerenciamento de inventário de dados como...
 #AE.1.2    Seção: 1.2
 Criptografia em Trânsito Use TLS para aplicações baseadas em HTTPS, com ferramentas como openSSL e python's`ssl` biblioteca.

---

### AE.2 Validação da Entrada do Usuário

Ferramentas para manipular e validar entradas de usuários.

 #AE.2.1    Seção: 2.1
 Ferramentas de Defesa contra Injeção de Prompt: Use ferramentas de guardrail como o NeMo da NVIDIA ou o Guardrails AI.

---

