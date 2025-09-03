## Capa

### Sobre o Padrão

O Padrão de Verificação de Segurança de Inteligência Artificial (AISVS) é um catálogo baseado na comunidade de requisitos de segurança que cientistas de dados, engenheiros de MLOps, arquitetos de software, desenvolvedores, testadores, profissionais de segurança, fornecedores de ferramentas, reguladores e consumidores podem usar para projetar, construir, testar e verificar sistemas e aplicações confiáveis habilitados por IA. Ele fornece uma linguagem comum para especificar controles de segurança ao longo do ciclo de vida da IA — desde a coleta de dados e desenvolvimento de modelos até implantação e monitoramento contínuo — para que as organizações possam medir e melhorar a resiliência, privacidade e segurança de suas soluções de IA.

### Direitos Autorais e Licença

Versão 0.1 (Primeiro Rascunho Público - Em Andamento), 2025  

![license](images/license.png)
Copyright © 2025 O Projeto AISVS.  

Liberado sob aCreative Commons Attribution‑ShareAlike 4.0 International License.
Para qualquer reutilização ou distribuição, você deve comunicar claramente os termos de licença deste trabalho aos outros.

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

AISVS é um padrão totalmente novo criado especificamente para enfrentar os desafios de segurança únicos dos sistemas de inteligência artificial. Embora se inspire em melhores práticas gerais de segurança, cada requisito do AISVS foi desenvolvido do zero para refletir o cenário de ameaças da IA e ajudar as organizações a construir soluções de IA mais seguras e resilientes.

## Prefácio

Bem-vindo ao Padrão de Verificação de Segurança em Inteligência Artificial (AISVS) versão 1.0!

### Introdução

Estabelecida em 2025 através de um esforço colaborativo da comunidade, a AISVS define os requisitos de segurança a serem considerados ao projetar, desenvolver, implantar e operar modelos de IA modernos, pipelines e serviços habilitados para IA.

AISVS v1.0 representa o trabalho conjunto de seus líderes de projeto, grupo de trabalho e contribuidores da comunidade mais ampla para fornecer uma linha de base pragmática e verificável para garantir a segurança de sistemas de IA.

Nosso objetivo com este lançamento é tornar o AISVS de fácil adoção, mantendo o foco absoluto no escopo definido e abordando o cenário de riscos em rápida evolução, exclusivo da IA.

### Objetivos principais para a versão 1.0 do AISVS

A Versão 1.0 será criada com vários princípios orientadores.

#### Escopo Bem‑Definido

Cada requisito deve estar alinhado com o nome e a missão da AISVS:

Inteligência Artificial – Os controles operam na camada de IA/ML (dados, modelo, pipeline ou inferência) e são de responsabilidade dos profissionais de IA.
Segurança – Requisitos que mitigam diretamente riscos de segurança, privacidade ou segurança identificados.
Verificação – A linguagem é escrita de modo que a conformidade possa ser validada de forma objetiva.
Padrão – Seções seguem uma estrutura e terminologia consistentes para formar uma referência coerente.
​
---

Seguindo o AISVS, as organizações podem avaliar e fortalecer de forma sistemática a postura de segurança de suas soluções de IA, promovendo uma cultura de engenharia de IA segura.

## Usando o AISVS

A Padrão de Verificação de Segurança de Inteligência Artificial (AISVS) define os requisitos de segurança para aplicações e serviços de IA modernos, com foco nos aspectos sob o controle dos desenvolvedores de aplicativos.

O AISVS destina-se a qualquer pessoa que desenvolva ou avalie a segurança de aplicações de IA, incluindo desenvolvedores, arquitetos, engenheiros de segurança e auditores. Este capítulo apresenta a estrutura e o uso do AISVS, incluindo seus níveis de verificação e casos de uso pretendidos.

### Níveis de Verificação de Segurança de Inteligência Artificial

A AISVS define três níveis ascendentes de verificação de segurança. Cada nível acrescenta profundidade e complexidade, permitindo que as organizações ajustem sua postura de segurança ao nível de risco de seus sistemas de IA.

As organizações podem começar no Nível 1 e adotar progressivamente níveis superiores à medida que a maturidade em segurança e a exposição a ameaças aumentam.

#### Definição dos Níveis

Cada requisito no AISVS v1.0 é atribuído a um dos seguintes níveis:

 Requisitos do Nível 1

O Nível 1 inclui os requisitos de segurança mais críticos e fundamentais. Estes se concentram em prevenir ataques comuns que não dependem de outras pré-condições ou vulnerabilidades. A maioria dos controles de Nível 1 é relativamente fácil de implementar ou suficientemente essenciais para justificar o esforço.

 Requisitos do Nível 2

Nível 2 aborda ataques mais avançados ou menos comuns, bem como defesas em camadas contra ameaças generalizadas. Esses requisitos podem envolver lógica mais complexa ou atingir pré-requisitos específicos de ataque.

 Requisitos do Nível 3

O Nível 3 inclui controles que geralmente são mais difíceis de implementar ou situacionalmente aplicáveis. Esses frequentemente representam mecanismos de defesa em profundidade ou mitigação contra ataques específicos, direcionados ou de alta complexidade.

#### Papel (D/V)

Cada requisito do AISVS está marcado de acordo com o público-alvo principal:

D – Requisitos focados no desenvolvedor
V – Requisitos focados em verificador/auditor
D/V – Relevante tanto para desenvolvedores quanto para verificadores

## Governança de Dados de Treinamento C1 & Gestão de Viés

### Objetivo de Controle

Os dados de treinamento devem ser obtidos, tratados e mantidos de maneira a preservar a proveniência, segurança, qualidade e equidade. Isso atende às obrigações legais e reduz os riscos de viés, envenenamento ou violações de privacidade que podem ocorrer durante o treinamento e afetar todo o ciclo de vida da IA.

---

### C1.1 Proveniência dos Dados de Treinamento

Mantenha um inventário verificável de todos os conjuntos de dados, aceite apenas fontes confiáveis e registre todas as mudanças para fins de auditoria.

 #1.1.1    Nível: 1    Papel: D/V
 Verifique se uma inventário atualizado de todas as fontes de dados de treinamento (origem, zelador/proprietário, licença, método de coleta, restrições de uso pretendido e histórico de processamento) é mantido.
 #1.1.2    Nível: 1    Papel: D/V
 Verifique se os processos de dados de treinamento excluem recursos, atributos ou campos desnecessários (por exemplo, metadados não utilizados, informações pessoais sensíveis, dados de teste vazados).
 #1.1.3    Nível: 2    Papel: D/V
 Verifique se todas as alterações no conjunto de dados estão sujeitas a um fluxo de aprovação registrado.
 #1.1.4    Nível: 3    Papel: D/V
 Verifique se os conjuntos de dados ou subconjuntos estão marcados com marca d'água ou impressos digitalmente, sempre que possível.

---

### C1.2 Segurança e Integridade dos Dados de Treinamento

Restringir o acesso aos dados de treinamento, criptografá-los em repouso e em trânsito, e validar sua integridade para prevenir adulteração, roubo ou envenenamento de dados.

 #1.2.1    Nível: 1    Papel: D/V
 Verifique se os controles de acesso protegem o armazenamento de dados de treinamento e os pipelines.
 #1.2.2    Nível: 2    Papel: D/V
 Verifique se todo acesso aos dados de treinamento está registrado, incluindo usuário, horário e ação.
 #1.2.3    Nível: 2    Papel: D/V
 Verifique se os conjuntos de dados de treinamento estão criptografados em trânsito e em repouso, usando algoritmos criptográficos padrão da indústria e práticas de gerenciamento de chaves.
 #1.2.4    Nível: 2    Papel: D/V
 Verifique se hashes criptográficos ou assinaturas digitais são usadas para garantir a integridade dos dados durante o armazenamento e transferência de dados de treinamento.
 #1.2.5    Nível: 2    Papel: D/V
 Verifique se técnicas de detecção automatizadas são aplicadas para proteger contra modificações ou corrupção não autorizada dos dados de treinamento.
 #1.2.6    Nível: 2    Papel: D/V
 Verifique se os dados de treinamento obsoletos foram apagados com segurança ou anonimizados.
 #1.2.7    Nível: 3    Papel: D/V
 Verifique se todas as versões do conjunto de dados de treinamento estão identificadas de forma exclusiva, armazenadas de maneira imutável e auditável para apoiar rollback e análise forense.

---

### C1.3 Qualidade, Integridade e Segurança da Etiquetação dos Dados de Treinamento

Proteja os rótulos e exija revisão técnica para dados críticos.

 #1.3.1    Nível: 2    Papel: D/V
 Verifique se hashes criptográficos ou assinaturas digitais são aplicados aos artefatos de rotulagem para garantir sua integridade e autenticidade.
 #1.3.2    Nível: 2    Papel: D/V
 Verifique se as interfaces e plataformas de rotulagem aplicam controles de acesso fortes, mantêm registros de auditoria à prova de adulteração de todas as atividades de rotulagem e protegem contra modificações não autorizadas.
 #1.3.3    Nível: 3    Papel: D/V
 Verifique se as informações sensíveis em rótulos estão sendo redigidas, anonimizadas ou criptografadas nos níveis dos campos de dados em repouso e em trânsito.

---

### C1.4 Qualidade dos Dados de Treinamento e Garantia de Segurança

Combine validação automatizada, verificações manuais pontuais e remediação registrada para garantir a confiabilidade do conjunto de dados.

 #1.4.1    Nível: 1    Papel: D
 Verifique se os testes automatizados detectam erros de formato e valores nulos em cada ingestão ou transformação de dados significativa.
 #1.4.2    Nível: 2    Papel: D/V
 Verifique se os pipelines de treinamento e ajuste fino de LLM implementam detecção de envenenamento e validação da integridade dos dados (por exemplo, métodos estatísticos, detecção de outliers, análise de embeddings) para identificar possíveis ataques de envenenamento (por exemplo, troca de rótulos, inserção de gatilhos backdoor, comandos de alteração de papéis, ataques de instâncias influentes) ou corrupção não intencional dos dados de treinamento.
 #1.4.3    Nível: 3    Papel: D/V
 Verifique se defesas apropriadas, como treinamento adversarial (usando exemplos adversariais gerados), aumento de dados com entradas perturbadas ou técnicas de otimização robusta, estão implementadas e ajustadas para os modelos relevantes com base na avaliação de risco.
 #1.4.4    Nível: 2    Papel: D/V
 Verifique se os rótulos gerados automaticamente (por exemplo, via LLMs ou supervisão fraca) estão sujeitos a limites de confiança e verificações de consistência para detectar rótulos inventados, enganosos ou de baixa confiança.
 #1.4.5    Nível: 3    Papel: D
 Verifique se os testes automatizados detectam desvios de rótulo em cada ingestão ou transformação significativa de dados.

---

### C1.5 Linhagem e Rastreabilidade de Dados

Acompanhe toda a trajetória de cada ponto de dado desde a fonte até a entrada do modelo para auditoria e resposta a incidentes.

 #1.5.1    Nível: 2    Papel: D/V
 Verifique se a linhagem de cada ponto de dado, incluindo todas as transformações, aumentos e mesclagens, está registrada e pode ser reconstruída.
 #1.5.2    Nível: 2    Papel: D/V
 Verifique se os registros de linhagem são imutáveis, armazenados de forma segura e acessíveis para auditorias.
 #1.5.3    Nível: 2    Papel: D/V
 Verifique se o rastreamento de linhagem cobre dados sintéticos gerados por técnicas de preservação de privacidade ou técnicas generativas e que todos os dados sintéticos são claramente rotulados e distinguíveis dos dados reais ao longo de todo o pipeline.

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

Validação robusta da entrada do usuário é uma defesa de primeira linha contra alguns dos ataques mais destrutivos a sistemas de IA. Ataques de injeção de prompt podem sobrescrever instruções do sistema, vazar dados sensíveis ou direcionar o modelo para comportamentos não permitidos. A menos que filtros dedicados e hierarquias de instruções estejam em uso, pesquisas mostram que "jailbreaks" de múltiplas etapas que exploram janelas de contexto muito longas serão eficazes. Além disso, ataques de perturbação adversarial sutil — como trocas de homoglyphs ou leetspeak — podem alterar silenciosamente as decisões de um modelo.

---

### C2.1 Defesa contra Injeção de Prompt

Injeção de prompt é um dos principais riscos para sistemas de IA. As defesas contra essa tática empregam uma combinação de filtros de padrões estáticos, classificadores dinâmicos e aplicação de hierarquia de instruções.

 #2.1.1    Nível: 1    Papel: D/V
 Verifique se as entradas do usuário são filtradas em uma biblioteca continuamente atualizada de padrões conhecidos de injeção de prompt (palavras-chave de jailbreak, "ignore previous", cadeias de role-play, ataques indiretos de HTML/URL).
 #2.1.2    Nível: 1    Papel: D/V
 Verifique se o sistema aplica uma hierarquia de instruções na qual mensagens do sistema ou do desenvolvedor prevalecem sobre as instruções do usuário, mesmo após a expansão da janela de contexto.
 #2.1.3    Nível: 2    Papel: D/V
 Verifique se os testes de avaliação adversarial (por exemplo, prompts "many-shot" da Red Team) são executados antes de cada lançamento de modelo ou modelo de prompt, com limites de taxa de sucesso e bloqueadores automáticos para regressões.
 #2.1.4    Nível: 2    Papel: D
 Verifique se os prompts originados de conteúdo de terceiros (páginas da web, PDFs, e-mails) são sanitizados em um contexto de análise isolado antes de serem concatenados ao prompt principal.
 #2.1.5    Nível: 3    Papel: D/V
 Verifique se todas as atualizações das regras de filtro de prompts, versões do modelo de classificador e alterações na lista de bloqueio estão sob controle de versão e podem ser auditadas.

---

### C2.2 Resistência a Exemplos Adversariais

Modelos de Processamento de Linguagem Natural (PLN) ainda são vulneráveis a perturbações sutis em nível de caractere ou palavra que os humanos frequentemente não percebem, mas que os modelos tendem a classificar incorretamente.

 #2.2.1    Nível: 1    Papel: D
 Verifique se as etapas básicas de normalização de entrada (Unicode NFC, mapeamento de homoglifos, remoção de espaços em branco) são executadas antes da tokenização.
 #2.2.2    Nível: 2    Papel: D/V
 Verifique se a detecção de anomalias estatísticas sinaliza entradas com distância de edição incomumente alta em relação às normas do idioma, tokens repetidos em excesso ou distâncias de incorporação anormais.
 #2.2.3    Nível: 2    Papel: D
 Verifique se o pipeline de inferência suporta variantes de modelo reforçadas por treinamento adversarial opcional ou camadas de defesa (por exemplo, randomização, destilação defensiva) para pontos finais de alto risco.
 #2.2.4    Nível: 2    Papel: V
 Verifique se entradas adversariais suspeitas estão em quarentena, registradas com cargas completas (após a redação de PII).
 #2.2.5    Nível: 3    Papel: D/V
 Verifique se as métricas de robustez (taxa de sucesso de suítes de ataques conhecidos) são monitoradas ao longo do tempo e se regressões acionam um bloqueador de liberação.

---

### C2.3 Validação de Esquema, Tipo e Comprimento

Ataques de IA apresentando entradas malformadas ou oversized podem causar erros de análise, vazamentos de prompts entre campos e exaustão de recursos. A aplicação rigorosa de esquema também é um requisito prévio ao realizar chamadas determinísticas de ferramentas.

 #2.3.1    Nível: 1    Papel: D
 Verifique se cada endpoint de API ou chamada de função define um esquema de entrada explícito (JSON Schema, Protobuf ou equivalente multimodal) e se as entradas são validadas antes da montagem do prompt.
 #2.3.2    Nível: 1    Papel: D/V
 Verifique se entradas que ultrapassam os limites máximos de tokens ou bytes são rejeitadas com uma mensagem de erro segura e nunca truncadas silenciosamente.
 #2.3.3    Nível: 2    Papel: D/V
 Verifique se as verificações de tipo (por exemplo, intervalos numéricos, valores de enumeração, tipos MIME para imagens/áudio) são aplicadas no lado do servidor, e não apenas no código cliente.
 #2.3.4    Nível: 2    Papel: D
 Verifique se os validadores semânticos (por exemplo, JSON Schema) são executados em tempo constante para evitar DoS algorítmico.
 #2.3.5    Nível: 3    Papel: V
 Verifique se as falhas de validação são registradas com trechos de carga útil redigidos e códigos de erro unívocos para facilitar a triagem de segurança.

---

### C2.4 Triagem de Conteúdo & Políticas

Os desenvolvedores devem ser capazes de detectar prompts sintaticamente válidos que solicitam conteúdo proibido (como instruções ilícitas, discurso de ódio e texto protegido por direitos autorais) e impedir que eles se propaguem.

 #2.4.1    Nível: 1    Papel: D
 Verifique se um classificador de conteúdo (zero shot ou ajustado) avalia todas as entradas para violência, automutilação, ódio, conteúdo sexual e pedidos ilegais, com limites configuráveis.
 #2.4.2    Nível: 1    Papel: D/V
 Verifique se as entradas que violam as políticas irão receber recusas padronizadas ou respostas seguras para que não sejam propagadas para chamadas subsequentes de modelos de linguagem de grande porte (LLM).
 #2.4.3    Nível: 2    Papel: D
 Verifique se o modelo de triagem ou conjunto de regras está sendo reestilizado/atualizado pelo menos a cada trimestre, incorporando novos padrões observados de jailbreak ou bypass de políticas.
 #2.4.4    Nível: 2    Papel: D
 Verifique se a triagem respeita as políticas específicas do usuário (idade, restrições legais regionais) por meio de regras baseadas em atributos resolvidas no momento da solicitação.
 #2.4.5    Nível: 3    Papel: V
 Verifique se os registros de triagem incluem pontuações de confiança do classificador e tags de categorias de política para correlação SOC e futura reprodução da equipe de ataque.

---

### C2.5 Limitação de Taxa de Entrada & Prevenção de Abuso

Os desenvolvedores devem prevenir abuso, exaustão de recursos e ataques automatizados contra sistemas de IA, limitando as taxas de entrada e detectando padrões de uso anômalos.

 #2.5.1    Nível: 1    Papel: D/V
 Verifique se os limites de taxa por usuário, por IP e por chave de API são aplicados a todos os endpoints de entrada.
 #2.5.2    Nível: 2    Papel: D/V
 Verifique se os limites de taxa de pico e sustentada estão ajustados para prevenir ataques DoS e de força bruta.
 #2.5.3    Nível: 2    Papel: D/V
 Verifique se padrões de uso anômalos (por exemplo, solicitações rápidas, inundação de entrada) acionam bloqueios automáticos ou escalonamentos.
 #2.5.4    Nível: 3    Papel: V
 Verifique se os registros de prevenção de abuso são retidos e revisados para padrões emergentes de ataque.

---

### C2.6 Validação de Entrada Multi-Modal

Sistemas de IA devem incluir validação robusta para entradas não textuais (imagens, áudio, arquivos) para prevenir injeção, evasão ou abuso de recursos.

 #2.6.1    Nível: 1    Papel: D
 Verifique se todas as entradas não-textuais (imagens, áudio, arquivos) são validadas quanto ao tipo, tamanho e formato antes do processamento.
 #2.6.2    Nível: 2    Papel: D/V
 Verifique se os arquivos são escaneados em busca de malware e payloads steganográficos antes da ingestão.
 #2.6.3    Nível: 2    Papel: D/V
 Verifique se as entradas de imagem/árvore de áudio foram verificadas quanto a perturbações adversariais ou padrões de ataque conhecidos.
 #2.6.4    Nível: 3    Papel: V
 Verifique se as falhas de validação de entrada multimodal são registradas e acionam alertas para investigação.

---

### C2.7 Proveniência da Entrada & Atribuição

Os sistemas de IA devem suportar auditoria, rastreamento de abuso e conformidade, monitorando e marcando as origens de todas as entradas de usuário.

 #2.7.1    Nível: 1    Papel: D/V
 Verifique se todas as entradas de usuário estão marcadas com metadados (ID do usuário, sessão, origem, carimbo de data/hora, endereço IP) na ingestão.
 #2.7.2    Nível: 2    Papel: D/V
 Verifique se os metadados de proveniência são mantidos e auditáveis para todas as entradas processadas.
 #2.7.3    Nível: 2    Papel: D/V
 Verifique se fontes de entrada anômalas ou não confiáveis são sinalizadas e sujeitas a uma fiscalização aprimorada ou bloqueio.

---

### C2.8 Detecção de Ameaças Adaptativa em Tempo Real

Os desenvolvedores devem empregar sistemas avançados de detecção de ameaças para IA que se adaptem a novos padrões de ataque e ofereçam proteção em tempo real com correspondência de padrões compilados.

 #2.8.1    Nível: 1    Papel: D/V
 Verifique se os padrões de detecção de ameaças estão compilados em mecanismos de regex otimizados para filtragem em tempo real de alto desempenho, com impacto mínimo na latência.
 #2.8.2    Nível: 1    Papel: D/V
 Verifique se os sistemas de detecção de ameaças mantêm bibliotecas de padrões separadas para diferentes categorias de ameaças (injeção de prompt, conteúdo prejudicial, dados sensíveis, comandos do sistema).
 #2.8.3    Nível: 2    Papel: D/V
 Verifique se a detecção adaptativa de ameaças incorpora modelos de aprendizado de máquina que atualizam a sensibilidade às ameaças com base na frequência de ataques e nas taxas de sucesso.
 #2.8.4    Nível: 2    Papel: D/V
 Verifique se os feeds de inteligência de ameaças em tempo real atualizam automaticamente as bibliotecas de padrões com novas assinaturas de ataque e IOCs (Indicadores de Comprometimento).
 #2.8.5    Nível: 3    Papel: D/V
 Verifique se as taxas de falsos positivos na detecção de ameaças são monitoradas continuamente e se a especificidade do padrão é ajustada automaticamente para minimizar interferências em casos de uso legítimos.
 #2.8.6    Nível: 3    Papel: D/V
 Verifique se a análise de ameaça contextual considera a fonte de entrada, os padrões de comportamento do usuário e o histórico da sessão para melhorar a precisão da detecção.
 #2.8.7    Nível: 3    Papel: D/V
 Verifique se as métricas de desempenho na detecção de ameaças (taxa de detecção, latência de processamento, utilização de recursos) estão sendo monitoradas e otimizadas em tempo real.

---

### C2.9 Pipeline de Validação de Segurança Multi-Modal

Os desenvolvedores devem fornecer validação de segurança para modalidades de entrada de IA, como texto, imagem, áudio e outras, com tipos específicos de detecção de ameaças e isolamento de recursos.

 #2.9.1    Nível: 1    Papel: D/V
 Verifique se cada modalidade de entrada possui validadores de segurança dedicados com padrões de ameaça documentados (texto: injeção de comandos, imagens: esteganografia, áudio: ataques por espectrograma) e limites de detecção.
 #2.9.2    Nível: 2    Papel: D/V
 Verifique se as entradas multimodais são processadas em sandboxes isolados com limites de recursos definidos ( memória, CPU, tempo de processamento) específicos para cada tipo de modalidade e documentados nas políticas de segurança.
 #2.9.3    Nível: 2    Papel: D/V
 Verifique se a detecção de ataques cruzados de modalidades identifica ataques coordenados que abrangem múltiplos tipos de entrada (por exemplo, cargas útil esteganográficas em imagens combinadas com injeção de prompt em texto) com regras de correlação e geração de alertas.
 #2.9.4    Nível: 3    Papel: D/V
 Verifique se as falhas de validação multimodal acionam registros detalhados, incluindo todas as modalidades de entrada, resultados da validação, pontuações de ameaça e análise de correlação com formatos de registro estruturados para integração com SIEM.
 #2.9.5    Nível: 3    Papel: D/V
 Verifique se os classificadores de conteúdo específicos de modalidade estão atualizados de acordo com os cronogramas documentados (mínimo trimestralmente) com novos padrões de ameaças, exemplos adversariais e benchmarks de desempenho mantidos acima dos limites de referência.

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

## Gestão do Ciclo de Vida do Modelo C3 & Controle de Mudanças

### Objetivo de Controle

Os sistemas de IA devem implementar processos de controle de alterações que impeçam modificações não autorizadas ou inseguras do modelo de alcançar a produção. Esse controle garante a integridade do modelo durante todo o ciclo de vida—desde o desenvolvimento até a implantação e desativação—o que possibilita uma resposta rápida a incidentes e mantém a responsabilidade por todas as mudanças.

Meta de Segurança Central: Apenas modelos autorizados e validados chegam à produção, empregando processos controlados que garantam integridade, rastreabilidade e recuperabilidade.

---

### C3.1 Autorização e Integridade do Modelo

Apenas modelos autorizados com integridade verificada chegam aos ambientes de produção.

 #3.1.1    Nível: 1    Papel: D/V
 Verifique se todos os artefatos do modelo ( pesos, configurações, tokenizadores) estão assinados criptograficamente por entidades autorizadas antes da implantação.
 #3.1.2    Nível: 1    Papel: D/V
 Verifique se a integridade do modelo é validada no momento da implantação e se as falhas na verificação da assinatura impedem o carregamento do modelo.
 #3.1.3    Nível: 2    Papel: D/V
 Verifique se os registros de proveniência do modelo incluem a identidade de uma entidade autorizadora, verificações de checksum dos dados de treinamento, resultados dos testes de validação com status de sucesso/falha e um carimbo de data/hora de criação.
 #3.1.4    Nível: 2    Papel: D/V
 Verifique se todos os artefatos do modelo usam versionamento semântico (MAJOR.MINOR.PATCH) com critérios documentados que especificam quando cada componente da versão deve ser incrementado.
 #3.1.5    Nível: 2    Papel: V
 Verifique se o rastreamento de dependências mantém um inventário em tempo real que possibilita a identificação rápida de todos os sistemas consumidores.

---

### C3.2 Validação e Teste de Modelo

Os modelos devem passar por validações de segurança e segurança definidas antes da implantação.

 #3.2.1    Nível: 1    Papel: D/V
 Verifique se os modelos passam por testes automatizados de segurança que incluem validação de entrada, sanitização de saída e avaliações de segurança, com limites predefinidos de aprovação/reprovação organizacionais antes da implantação.
 #3.2.2    Nível: 1    Papel: D/V
 Verifique se as falhas de validação bloqueiam automaticamente a implantação do modelo após aprovação explícita de substituição por pessoal autorizado pré-designado com justificativas comerciais documentadas.
 #3.2.3    Nível: 2    Papel: V
 Verifique se os resultados do teste estão assinados criptograficamente e ligados de forma imutável ao hash da versão específica do modelo que está sendo validado.
 #3.2.4    Nível: 2    Papel: D/V
 Verifique se as implantações de emergência exigem avaliação de risco de segurança documentada e aprovação de uma autoridade de segurança previamente designada dentro de prazos acordados.

---

### C3.3 Implantação Controlada e Reversão

Implantações de modelos devem ser controladas, monitoradas e reversíveis.

 #3.3.1    Nível: 1    Papel: D
 Verifique se as implantações em produção implementam mecanismos de implantação gradual (implantação canário, implantação azul-verde) com gatilhos de rollback automatizados com base em taxas de erro pré-acordadas, limites de latência ou critérios de alertas de segurança.
 #3.3.2    Nível: 1    Papel: D/V
 Verifique se as funcionalidades de rollback restauram o estado completo do modelo ( pesos, configurações, dependências) de forma atômica dentro dos períodos organizacionais predefinidos.
 #3.3.3    Nível: 2    Papel: D/V
 Verifique se os processos de implantação validam assinaturas criptográficas e calculam verificações de integridade antes da ativação do modelo, falhando na implantação em qualquer incompatibilidade.
 #3.3.4    Nível: 2    Papel: D/V
 Verifique se as capacidades de desligamento de emergência do modelo podem desabilitar endpoints do modelo dentro de tempos de resposta predefinidos por meio de disjuntores automáticos ou interruptores manuais.
 #3.3.5    Nível: 2    Papel: V
 Verifique se os artefatos de rollback (versões anteriores do modelo, configurações, dependências) estão retidos de acordo com as políticas organizacionais, utilizando armazenamento imutável para resposta a incidentes.

---

### C3.4 Responsabilidade pela Alteração e Auditoria

Todas as mudanças no ciclo de vida do modelo devem ser rastreáveis e auditáveis.

 #3.4.1    Nível: 1    Papel: V
 Verifique se todas as alterações no modelo (implantação, configuração, aposentadoria) geram registros de auditoria imutáveis, incluindo um carimbo de data/hora, uma identidade de ator autenticada, um tipo de alteração e os estados antes/depois.
 #3.4.2    Nível: 2    Papel: D/V
 Verifique se o acesso ao registro de auditoria exige autorização adequada e se todas as tentativas de acesso são registradas com identidade do usuário e um carimbo de data/hora.
 #3.4.3    Nível: 2    Papel: D/V
 Verifique se os modelos de prompt e as mensagens do sistema estão sob controle de versão em repositórios git, com revisão de código obrigatória e aprovação de revisores designados antes do implantação.
 #3.4.4    Nível: 2    Papel: V
 Verifique se os registros de auditoria incluem detalhes suficientes ( hashes de modelos, snapshots de configuração, versões de dependências) para permitir a reconstrução completa do estado do modelo para qualquer carimbo de data/hora dentro do período de retenção.

---

### C3.5 Práticas Seguras de Desenvolvimento

Os processos de desenvolvimento e treinamento de modelos devem seguir práticas seguras para evitar comprometimento.

 #3.5.1    Nível: 1    Papel: D
 Verifique se os ambientes de desenvolvimento, teste e produção do modelo estão fisicamente ou logicamente separados. Eles não compartilham infraestrutura, possuem controles de acesso distintos e armazenamentos de dados isolados.
 #3.5.2    Nível: 1    Papel: D
 Verifique se o treinamento do modelo e o ajuste fino ocorrem em ambientes isolados com acesso controlado à rede.
 #3.5.3    Nível: 1    Papel: D/V
 Verifique se as fontes de dados de treinamento são validadas por meio de verificações de integridade e autenticadas por fontes confiáveis com cadeia de custódia documentada antes de serem usadas no desenvolvimento do modelo.
 #3.5.4    Nível: 2    Papel: D
 Verifique se os artefatos de desenvolvimento do modelo (hiperparâmetros, scripts de treinamento, arquivos de configuração) estão armazenados no controle de versão e exigem aprovação de revisão por pares antes do uso no treinamento.

---

### C3.6 Aposentadoria e Desativação de Modelos

Os modelos devem ser desativados de forma segura quando não forem mais necessários ou quando forem identificados problemas de segurança.

 #3.6.1    Nível: 1    Papel: D
 Verifique se os processos de aposentadoria do modelo escaneiam automaticamente os gráficos de dependência, identificam todos os sistemas consumidores e oferecem períodos de aviso prévio acordados previamente antes do desligamento.
 #3.6.2    Nível: 1    Papel: D/V
 Verifique se os artefatos de modelos aposentados foram apagados de forma segura usando apagamento criptográfico ou sobrescrição múltipla, de acordo com as políticas de retenção de dados documentadas, com certificados de destruição verificados.
 #3.6.3    Nível: 2    Papel: V
 Verifique se os eventos de desativação do modelo estão registrados com timestamp e identidade do ator, e se as assinaturas do modelo são revogadas para prevenir reutilização.
 #3.6.4    Nível: 2    Papel: D/V
 Verifique se a aposentadoria do modelo de emergência pode desabilitar o acesso ao modelo dentro dos prazos preestabelecidos de resposta de emergência por meio de interrupções automáticas, caso vulnerabilidades críticas de segurança sejam descobertas.

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

## Segurança de Infraestrutura, Configuração & Implantação C4

### Objetivo de Controle

A infraestrutura de IA deve ser reforçada contra escalonamento de privilégios, adulteração da cadeia de suprimentos e movimento lateral através de configuração segura, isolamento em tempo de execução, pipelines de implantação confiáveis e monitoramento abrangente. Apenas componentes e configurações de infraestrutura autorizados e validados alcançam a produção por meio de processos controlados que mantêm a segurança, integridade e auditoria.

Objetivo central de segurança: Apenas componentes de infraestrutura assinados criptograficamente, escaneados em busca de vulnerabilidades, chegam à produção através de pipelines de validação automatizados que aplicam políticas de segurança e mantêm registros de auditoria imutáveis.

---

### C4.1 Isolamento do Ambiente de Execução

Prevenir escapes de contêineres e escalonamento de privilégios por meio de primitives de isolamento de nível de kernel e controles de acesso obrigatórios.

 #4.1.1    Nível: 1    Papel: D/V
 Verifique se todos os containers de IA deixam de fora TODAS as capacidades do Linux, exceto CAP_SETUID, CAP_SETGID e capacidades explicitamente necessárias documentadas nas linhas de base de segurança.
 #4.1.2    Nível: 1    Papel: D/V
 Verifique se os perfis seccomp bloqueiam todas as syscalls, exceto aquelas nas listas de permissão pré-aprovadas, com violações que terminam o container e geram alertas de segurança.
 #4.1.3    Nível: 2    Papel: D/V
 Verifique se as cargas de trabalho de IA são executadas com sistemas de arquivos raiz somente-leitura, tmpfs para dados temporários e volumes nomeados para dados persistentes, sem a aplicação de opções de montagem noexec.
 #4.1.4    Nível: 2    Papel: D/V
 Verifique se a monitoração em tempo de execução baseada em eBPF (Falco, Tetragon ou equivalente) detecta tentativas de escalonamento de privilégios e mata automaticamente os processos ofensores dentro dos requisitos de tempo de resposta organizacional.
 #4.1.5    Nível: 3    Papel: D/V
 Verifique se cargas de trabalho de AI de alto risco são executadas em ambientes isolados de hardware (Intel TXT, AMD SVM ou nós dedicados bare-metal) com verificação de atestação.

---

### C4.2 Pipelines Seguros de Construção e Implantação

Garanta a integridade criptográfica e a segurança da cadeia de suprimentos por meio de builds reproduzíveis e artefatos assinados.

 #4.2.1    Nível: 1    Papel: D/V
 Verifique se a infraestrutura-como-código é analisada com ferramentas (tfsec, Checkov ou Terrascan) em cada commit, bloqueando merges com descobertas de gravidade CRITICAL ou HIGH.
 #4.2.2    Nível: 1    Papel: D/V
 Verifique se as compilações de contêineres são reproduzíveis com hashes SHA256 idênticos em todas as compilações e gere atestados de proveniência do nível 3 do SLSA assinados com Sigstore.
 #4.2.3    Nível: 2    Papel: D/V
 Verifique se as imagens de container incorporam CycloneDX ou SPDX SBOMs e são assinadas com Cosign antes do push para o repositório, rejeitando imagens não assinadas na implantação.
 #4.2.4    Nível: 2    Papel: D/V
 Verifique se os pipelines de CI/CD utilizam tokens OIDC do HashiCorp Vault, AWS IAM Roles ou Azure Managed Identity com tempos de validade que não excedam os limites da política de segurança organizacional.
 #4.2.5    Nível: 2    Papel: D/V
 Verifique se as assinaturas Cosign e a proveniência SLSA são validadas durante o processo de implantação antes da execução do container e se erros de verificação fazem com que a implantação falhe.
 #4.2.6    Nível: 2    Papel: D/V
 Verifique se os ambientes de build operam em contêineres efêmeros ou VMs sem armazenamento persistente e isolamento de rede de VPCs de produção.

---

### C4.3 Segurança de Rede & Controle de Acesso

Implemente uma rede de confiança zero com políticas de negação padrão e comunicações criptografadas.

 #4.3.1    Nível: 1    Papel: D/V
 Verifique se as Kubernetes NetworkPolicies ou qualquer equivalente implementam um deny padrão de entrada/saída com regras de permissão explícitas para as portas necessárias (443, 8080, etc.).
 #4.3.2    Nível: 1    Papel: D/V
 Verifique se SSH (porta 22), RDP (porta 3389) e endpoints de metadados em nuvem (169.254.169.254) estão bloqueados ou requerem autenticação baseada em certificado.
 #4.3.3    Nível: 2    Papel: D/V
 Verifique se o tráfego de saída é filtrado através de proxies HTTP/HTTPS (Squid, Istio ou gateways NAT na nuvem) com listas de domínios permitidos e solicitações bloqueadas registradas.
 #4.3.4    Nível: 2    Papel: D/V
 Verifique se a comunicação entre serviços usa TLS mútuo com certificados rotacionados de acordo com a política organizacional e validação de certificados aplicada (sem flags de skip-verify).
 #4.3.5    Nível: 2    Papel: D/V
 Verifique se a infraestrutura de IA funciona em VPCs/VNets dedicados, sem acesso direto à internet, e se comunica apenas por meio de gateways NAT ou hosts bastião.

---

### C4.4 Segredos & Gerenciamento de Chaves Criptográficas

Proteja credenciais por meio de armazenamento com suporte de hardware e rotação automatizada com acesso de confiança zero.

 #4.4.1    Nível: 1    Papel: D/V
 Verifique se os segredos estão armazenados no HashiCorp Vault, AWS Secrets Manager, Azure Key Vault ou Google Secret Manager com criptografia em repouso usando AES-256.
 #4.4.2    Nível: 1    Papel: D/V
 Verifique se as chaves criptográficas são geradas em HSMs de Nível 2 do FIPS 140-2 (AWS CloudHSM, Azure Dedicated HSM) com rotação de chaves de acordo com a política criptográfica organizacional.
 #4.4.3    Nível: 2    Papel: D/V
 Verifique se a rotação de segredos é automatizada com implantação de tempo de inatividade zero e rotação imediata ativada por mudanças na equipe ou incidentes de segurança.
 #4.4.4    Nível: 2    Papel: D/V
 Verifique se as imagens de container são escaneadas com ferramentas (GitLeaks, TruffleHog ou detect-secrets) impedindo builds que contenham chaves de API, senhas ou certificados.
 #4.4.5    Nível: 2    Papel: D/V
 Verifique se o acesso secreto de produção requer MFA com tokens de hardware (YubiKey, FIDO2) e se é registrado por logs de auditoria imutáveis com identidades de usuários e carimbos de data/hora.
 #4.4.6    Nível: 2    Papel: D/V
 Verifique se os segredos são injetados via segredos do Kubernetes, volumes montados ou containers de inicialização e certifique-se de que os segredos nunca estejam embutidos em variáveis de ambiente ou imagens.

---

### C4.5 Isolamento de Carga de Trabalho de IA e Validação

Isolar modelos de IA não confiáveis em sandboxes seguros com análise comportamental abrangente.

 #4.5.1    Nível: 1    Papel: D/V
 Verifique se modelos de IA externos são executados em gVisor, microVMs (como Firecracker, CrossVM) ou contêineres Docker com as flags --security-opt=no-new-privileges e --read-only.
 #4.5.2    Nível: 1    Papel: D/V
 Verifique se os ambientes sandbox não possuem conectividade de rede (--network=none) ou se têm apenas acesso ao localhost, com todas as solicitações externas bloqueadas por regras do iptables.
 #4.5.3    Nível: 2    Papel: D/V
 Verifique se a validação do modelo de IA inclui testes automatizados de red-team com cobertura de teste definida pela organização e análise comportamental para detecção de backdoor.
 #4.5.4    Nível: 2    Papel: D/V
 Verifique se, antes de um modelo de IA ser promovido para produção, seus resultados no ambiente sandbox são assinados criptograficamente por pessoal de segurança autorizado e armazenados em registros de auditoria imutáveis.
 #4.5.5    Nível: 2    Papel: D/V
 Verifique se os ambientes sandbox são destruídos e recriados a partir de imagens de referência entre avaliações, com limpeza completa do sistema de arquivos e da memória.

---

### C4.6 Segurança de Infraestrutura e Monitoramento

Escaneie e monitore continuamente a infraestrutura com remediação automatizada e alertas em tempo real.

 #4.6.1    Nível: 1    Papel: D/V
 Verifique se as imagens de container são escaneadas de acordo com os cronogramas organizacionais, com vulnerabilidades CRÍTICAS bloqueando a implantação com base nos limites de risco organizacionais.
 #4.6.2    Nível: 1    Papel: D/V
 Verifique se a infraestrutura atende aos CIS Benchmarks ou aos controles NIST 800-53, com limites de conformidade definidos pela organização e remediação automatizada para verificações que falharem.
 #4.6.3    Nível: 2    Papel: D/V
 Verifique se as vulnerabilidades de severidade ALTA foram corrigidas de acordo com os prazos de gerenciamento de risco organizacional, com procedimentos de emergência para CVEs ativamente explorados.
 #4.6.4    Nível: 2    Papel: V
 Verifique se os alertas de segurança integram-se com plataformas SIEM (Splunk, Elastic ou Sentinel) usando os formatos CEF ou STIX/TAXII com enriquecimento automatizado.
 #4.6.5    Nível: 3    Papel: V
 Verifique se as métricas de infraestrutura são exportadas para os sistemas de monitoramento (Prometheus, DataDog) com painéis SLA e relatórios executivos.
 #4.6.6    Nível: 2    Papel: D/V
 Verifique se a deriva de configuração é detectada usando ferramentas (Chef InSpec, AWS Config) de acordo com os requisitos de monitoramento organizacional, com rollback automático para alterações não autorizadas.

---

### C4.7 Gerenciamento de Recursos de Infraestrutura de IA

Prevenir ataques de exaustão de recursos e garantir alocação justa de recursos por meio de cotas e monitoramento.

 #4.7.1    Nível: 1    Papel: D/V
 Verifique se a utilização de GPU/TPU está sendo monitorada com alertas acionados em limiares definidos pela organização e se o dimensionamento automático ou balanceamento de carga é ativado com base nas políticas de gerenciamento de capacidade.
 #4.7.2    Nível: 1    Papel: D/V
 Verifique se as métricas de carga de trabalho de IA (latência de inferência, throughput, taxas de erro) estão sendo coletadas de acordo com os requisitos de monitoramento organizacional e correlacionadas com a utilização da infraestrutura.
 #4.7.3    Nível: 2    Papel: D/V
 Verifique se o ResourceQuotas do Kubernetes ou o limite equivalente limita cargas de trabalho individuais de acordo com as políticas de alocação de recursos organizacionais, com limites rígidos aplicados.
 #4.7.4    Nível: 2    Papel: V
 Verifique se o monitoramento de custos acompanha os gastos por carga de trabalho/inquilino com alertas com base nos limites orçamentários organizacionais e controles automatizados para excessos de orçamento.
 #4.7.5    Nível: 3    Papel: V
 Verifique se o planejamento de capacidade usa dados históricos com períodos de previsão definidos pela organização e provisionamento automatizado de recursos com base em padrões de demanda.
 #4.7.6    Nível: 2    Papel: D/V
 Verifique se o esgotamento de recursos aciona os circuit breakers de acordo com os requisitos de resposta organizacional, incluindo limitação de taxa com base nas políticas de capacidade e isolamento de carga de trabalho.

---

### C4.8 Separação de Ambiente & Controles de Promoção

Implemente limites rigorosos de ambiente com portas de promoção automatizadas e validação de segurança.

 #4.8.1    Nível: 1    Papel: D/V
 Verifique se os ambientes dev/test/prod estão em VPCs/VNets separados, sem roles IAM compartilhadas, grupos de segurança ou conectividade de rede.
 #4.8.2    Nível: 1    Papel: D/V
 Verifique se a promoção do ambiente exige aprovação de pessoal autorizado definido pela organização com assinaturas criptográficas e trilhas de auditoria imutáveis.
 #4.8.3    Nível: 2    Papel: D/V
 Verifique se os ambientes de produção bloqueiam o acesso SSH, desativem endpoints de debug e exijam solicitações de mudança com aviso prévio organizacional, exceto em casos de emergência.
 #4.8.4    Nível: 2    Papel: D/V
 Verifique se as mudanças na infraestrutura-como-código exigem revisão por pares com testes automatizados e varredura de segurança antes do merge para a branch principal.
 #4.8.5    Nível: 2    Papel: D/V
 Verifique se os dados não utilizados na produção estão anonimizados de acordo com os requisitos de privacidade da organização, geração de dados sintéticos ou mascaramento completo de dados com remoção de PII verificada.
 #4.8.6    Nível: 2    Papel: D/V
 Verifique se os portões de promoção incluem testes de segurança automatizados (SAST, DAST, varredura de containers) com zero resultados CRÍTICOS necessários para aprovação.

---

### C4.9 Backup e Recuperação de Infraestrutura

Garanta a resiliência da infraestrutura por meio de backups automatizados, procedimentos de recuperação testados e capacidades de recuperação de desastres.

 #4.9.1    Nível: 1    Papel: D/V
 Verifique se as configurações de infraestrutura estão sendo respaldadas de acordo com as programações de backup organizacionais em regiões separadas geograficamente, com implementação da estratégia de backup 3-2-1.
 #4.9.2    Nível: 2    Papel: D/V
 Verifique se os sistemas de backup funcionam em redes isoladas com credenciais separadas e armazenamento air-gapped para proteção contra ransomware.
 #4.9.3    Nível: 2    Papel: V
 Verifique se os procedimentos de recuperação são testados e validados por meio de testes automatizados de acordo com as escalas organizacionais, com metas de RTO e RPO atendendo aos requisitos organizacionais.
 #4.9.4    Nível: 3    Papel: V
 Verifique se a recuperação de desastres inclui runbooks específicos de IA com restauração de pesos de modelo, reconstrução de cluster GPU e mapeamento de dependência de serviços.

---

### C4.10 Conformidade e Governança de Infraestrutura

Manter a conformidade regulatória por meio de avaliação contínua, documentação e controles automatizados.

 #4.10.1    Nível: 2    Papel: D/V
 Verifique se a conformidade da infraestrutura é avaliada de acordo com os cronogramas organizacionais contra controles SOC 2, ISO 27001 ou FedRAMP, com coleta automatizada de evidências.
 #4.10.2    Nível: 2    Papel: V
 Verifique se a documentação de infraestrutura inclui diagramas de rede, mapas de fluxo de dados e modelos de ameaça atualizados de acordo com os requisitos de gestão de mudanças organizacionais.
 #4.10.3    Nível: 3    Papel: D/V
 Verifique se as mudanças na infraestrutura passam por avaliação automatizada de impacto de conformidade com fluxos de trabalho de aprovação regulatória para modificações de alto risco.

---

### C4.11 Segurança de Hardware de IA

Componentes de hardware específicos de IA seguros, incluindo GPUs, TPUs e aceleradores de IA especializados.

 #4.11.1    Nível: 2    Papel: D/V
 Verifique se o firmware do acelerador de IA (GPU BIOS, firmware TPU) é verificado com assinaturas criptográficas e atualizado de acordo com os cronogramas de gerenciamento de patches da organização.
 #4.11.2    Nível: 2    Papel: D/V
 Verifique se, antes da execução da carga de trabalho, a integridade do acelerador de IA é validada por atestação de hardware usando TPM 2.0, Intel TXT ou AMD SVM.
 #4.11.3    Nível: 2    Papel: D/V
 Verifique se a memória da GPU está isolada entre cargas de trabalho usando SR-IOV, MIG (GPU de múltiplas instâncias) ou particionamento de hardware equivalente, com sanitização de memória entre tarefas.
 #4.11.4    Nível: 3    Papel: V
 Verifique se a cadeia de suprimentos de hardware de IA inclui verificação de proveniência com certificados do fabricante e validação de embalagem à prova de violação.
 #4.11.5    Nível: 3    Papel: D/V
 Verifique se os módulos de segurança de hardware (HSMs) protegem os pesos do modelo de IA e as chaves criptográficas com certificação FIPS 140-2 Nível 3 ou Common Criteria EAL4+.

---

### C4.12 Infraestrutura de IA de Borda e Distribuída

Implantações seguras de IA distribuída, incluindo computação de borda, aprendizado federado e arquiteturas multi-site.

 #4.12.1    Nível: 2    Papel: D/V
 Verifique se os dispositivos de edge AI se autenticam na infraestrutura central usando TLS mútua com certificados de dispositivos rotativos de acordo com a política de gerenciamento de certificados organizacional.
 #4.12.2    Nível: 2    Papel: D/V
 Verifique se os dispositivos de borda implementam boot seguro com assinaturas verificadas e proteção contra rollback, impedindo ataques de downgrade de firmware.
 #4.12.3    Nível: 3    Papel: D/V
 Verifique se a coordenação distribuída de IA usa algoritmos de consenso à prova de falhas bizantinas com validação de participantes e detecção de nós maliciosos.
 #4.12.4    Nível: 3    Papel: D/V
 Verifique se a comunicação de ponta a nuvem inclui limitação de largura de banda, compactação de dados e capacidades de operação offline com armazenamento local seguro.

---

### C4.13 Segurança de Infraestrutura Multi-Cloud e Híbrida

Trabalhos de AI seguros em vários provedores de nuvem e implantações híbridas de nuvem-on-premises.

 #4.13.1    Nível: 2    Papel: D/V
 Verifique se as implantações de IA multi-cloud usam federação de identidade independente de nuvem (OIDC, SAML) com gerenciamento de políticas centralizado entre provedores.
 #4.13.2    Nível: 2    Papel: D/V
 Verifique se a transferência de dados entre nuvens utiliza criptografia de ponta a ponta com chaves gerenciadas pelo cliente e controles de residência de dados aplicados por jurisdição.
 #4.13.3    Nível: 2    Papel: D/V
 Verifique se as cargas de trabalho de AI em nuvem híbrida implementam políticas de segurança consistentes em ambientes on-premise e na nuvem, com monitoramento e alerta unificados.
 #4.13.4    Nível: 3    Papel: V
 Verifique se a prevenção de lock-in com fornecedores de nuvem inclui infraestrutura como código portátil, APIs padronizadas e capacidades de exportação de dados com ferramentas de conversão de formato.
 #4.13.5    Nível: 3    Papel: V
 Verifique se a otimização de custos multi-nuvem inclui controles de segurança que impedem a propagação de recursos, bem como cobranças de transferência de dados não autorizadas entre nuvens.

---

### C4.14 Automação de Infraestrutura & Segurança GitOps

Automatize pipelines de infraestrutura segura e fluxos de trabalho GitOps para gerenciamento de infraestrutura de IA.

 #4.14.1    Nível: 2    Papel: D/V
 Verifique se os repositórios GitOps exigem commits assinados com chaves GPG e regras de proteção de branch que impedem pushes diretos para branches principais.
 #4.14.2    Nível: 2    Papel: D/V
 Verifique se a automação de infraestrutura inclui detecção de deriva com remediação automática e capacidades de reversão acionadas de acordo com os requisitos de resposta da organização para alterações não autorizadas.
 #4.14.3    Nível: 2    Papel: D/V
 Verifique se a provisão automatizada de infraestrutura inclui validação de políticas de segurança com bloqueio de implantação para configurações não conformes.
 #4.14.4    Nível: 2    Papel: D/V
 Verifique se os segredos da automação de infraestrutura são gerenciados por meio de operadores de segredos externos (External Secrets Operator, Bank-Vaults) com rotação automática.
 #4.14.5    Nível: 3    Papel: V
 Verifique se a infraestrutura auto-curativa inclui correlação de eventos de segurança com fluxos de trabalho automatizados de resposta a incidentes e notificação de partes interessadas.

---

### C4.15 Segurança de Infraestrutura Resistente a Quânticos

Prepare infraestrutura de IA para ameaças de computação quântica por meio de criptografia pós-quântica e protocolos seguros quânticos.

 #4.15.1    Nível: 3    Papel: D/V
 Verifique se a infraestrutura de IA implementa algoritmos criptográficos pós-quânticos aprovados pelo NIST (CRYSTALS-Kyber, CRYSTALS-Dilithium, SPHINCS+) para troca de chaves e assinaturas digitais.
 #4.15.2    Nível: 3    Papel: D/V
 Verifique se os sistemas de distribuição de chaves quânticas (QKD) estão implementados para comunicações de IA de alta segurança com protocolos de gerenciamento de chaves quânticas seguras.
 #4.15.3    Nível: 3    Papel: D/V
 Verifique se os frameworks de agilidade criptográfica permitem uma migração rápida para novos algoritmos pós-quânticos com rotação automatizada de certificados e chaves.
 #4.15.4    Nível: 3    Papel: V
 Verifique se a modelagem de ameaças quânticas avalia a vulnerabilidade da infraestrutura de IA a ataques quânticos com cronogramas de migração documentados e avaliações de risco.
 #4.15.5    Nível: 3    Papel: D/V
 Verifique se os sistemas criptográficos híbridos clássico-quantum proporcionam defesa em profundidade durante o período de transição quântica com monitoramento de desempenho.

---

### C4.16 Computação Confidencial & Enclaves Seguros

Proteja as cargas de trabalho de IA e pesos de modelos usando ambientes de execução confiáveis baseados em hardware e tecnologias de computação confidencial.

 #4.16.1    Nível: 3    Papel: D/V
 Verifique se os modelos de IA sensíveis são executados dentro de enclaves Intel SGX, AMD SEV-SNP ou ARM TrustZone, com memória criptografada e verificação de attestation.
 #4.16.2    Nível: 3    Papel: D/V
 Verifique se os containers confidenciais (Kata Containers, gVisor com computação confidencial) isola cargas de trabalho de IA com criptografia de memória reforçada por hardware.
 #4.16.3    Nível: 3    Papel: D/V
 Verifique se a attestation remota valida a integridade do enclave antes de carregar modelos de IA com prova criptográfica da autenticidade de um ambiente de execução.
 #4.16.4    Nível: 3    Papel: D/V
 Verifique se os serviços confidenciais de inferência de IA impedem a extração de modelo através de cálculo criptografado com pesos de modelo selados e execução protegida.
 #4.16.5    Nível: 3    Papel: D/V
 Verifique se a orquestração do ambiente de execução confiável gerencia o ciclo de vida do enclave seguro com atestação remota e canais de comunicação criptografados.
 #4.16.6    Nível: 3    Papel: D/V
 Verifique que a computação segura multi-partes (SMPC) permite o treinamento colaborativo de IA sem expor conjuntos de dados individuais ou parâmetros do modelo.

---

### C4.17 Infraestrutura de Conhecimento Zero

Implemente sistemas de prova de conhecimento zero para verificação e autenticação de IA preservando a privacidade, sem revelar informações sensíveis.

 #4.17.1    Nível: 3    Papel: D/V
 Verifique que as provas de conhecimento zero (ZK-SNARKs, ZK-STARKs) verificam a integridade do modelo de IA e a proveniência do treinamento sem expor os pesos do modelo ou os dados de treinamento.
 #4.17.2    Nível: 3    Papel: D/V
 Verifique se os sistemas de autenticação baseados em ZK permitem a verificação de usuário preservando a privacidade para serviços de IA, sem revelar informações relacionadas à identidade.
 #4.17.3    Nível: 3    Papel: D/V
 Verifique se os protocolos de interseção de conjuntos privados (PSI) permitem a correspondência segura de dados para IA federada sem divulgar conjuntos de dados individuais.
 #4.17.4    Nível: 3    Papel: D/V
 Verifique que os sistemas de aprendizado de máquina de conhecimento zero (ZKML) permitem inferências de IA verificáveis com prova criptográfica de cálculo correto.
 #4.17.5    Nível: 3    Papel: D/V
 Verifique se ZK-rollups fornecem processamento de transações de IA escalável, com preservação da privacidade, por meio de verificação em lote e redução da sobrecarga computacional.

---

### C4.18 Prevenção de Ataques de Canal Lateral

Proteja a infraestrutura de IA de ataques de canal lateral baseados em tempo, energia, eletromagnetismo e cache que podem vazar informações confidenciais.

 #4.18.1    Nível: 3    Papel: D/V
 Verifique se o tempo de inferência de IA é normalizado usando algoritmos de tempo constante e preenchimento para prevenir ataques de extração de modelo baseados em tempo.
 #4.18.2    Nível: 3    Papel: D/V
 Verifique se a proteção contra análise de energia inclui injeção de ruído, filtragem de linha de energia e padrões de execução randomizados para hardware de IA.
 #4.18.3    Nível: 3    Papel: D/V
 Verifique se a mitigação de canais side-baseados em cache usa particionamento de cache, randomização e instruções de limpeza para evitar vazamento de informações.
 #4.18.4    Nível: 3    Papel: D/V
 Verifique se a proteção contra emissão eletromagnética inclui blindagem, filtragem de sinal e processamento aleatório para prevenir ataques no estilo TEMPEST.
 #4.18.5    Nível: 3    Papel: D/V
 Verifique se as defesas de canais side microarquiteturais incluem controles de execução especulativa e ofuscação do padrão de acesso à memória.

---

### C4.19 Segurança de Hardware Neuromórfico & Especializado em IA

Garanta a segurança das arquiteturas emergentes de hardware de IA, incluindo chips neuromórficos, FPGAs, ASICs personalizados e sistemas de computação óptica.

 #4.19.1    Nível: 3    Papel: D/V
 Verifique se a segurança do chip neuromórfico inclui criptografia de padrões de picos, proteção de peso sináptico e validação de regras de aprendizado baseadas em hardware.
 #4.19.2    Nível: 3    Papel: D/V
 Verifique se aceleradores de IA baseados em FPGA implementam criptografia de bitstream, mecanismos anti-manipulação e carregamento seguro de configuração com atualizações autenticadas.
 #4.19.3    Nível: 3    Papel: D/V
 Verifique se a segurança de ASIC personalizada inclui processadores de segurança on-chip, raiz de confiança de hardware e armazenamento seguro de chaves com detecção de violação.
 #4.19.4    Nível: 3    Papel: D/V
 Verifique se os sistemas de computação óptica implementam criptografia óptica quântico-segura, comutação fotônica segura e processamento de sinais ópticos protegido.
 #4.19.5    Nível: 3    Papel: D/V
 Verifique se os chips de IA híbridos analógico-digital incluem computação analógica segura, armazenamento protegido de pesos e conversão analógica-digital autenticada.

---

### C4.20 Infraestrutura de Cálculo Preservadora de Privacidade

Implementar controles de infraestrutura para computação que preserva a privacidade e proteger dados sensíveis durante o processamento e análise de IA.

 #4.20.1    Nível: 3    Papel: D/V
 Verifique se a infraestrutura de criptografia homomórfica permite o processamento criptografado de cargas de trabalho sensíveis de IA com verificação de integridade criptográfica e monitoramento de desempenho.
 #4.20.2    Nível: 3    Papel: D/V
 Verifique se os sistemas de recuperação de informações privadas permitem consultas a banco de dados sem revelar os padrões de consulta, mediante proteção criptográfica dos padrões de acesso.
 #4.20.3    Nível: 3    Papel: D/V
 Verifique se os protocolos de computação multiparte segura permitem inferência de IA preservando a privacidade, sem expor entradas individuais ou cálculos intermediários.
 #4.20.4    Nível: 3    Papel: D/V
 Verifique se a gestão de chaves com privacidade preservada inclui geração distribuída de chaves, criptografia threshold e rotação segura de chaves com proteção suportada por hardware.
 #4.20.5    Nível: 3    Papel: D/V
 Verifique se o desempenho de computação preservadora da privacidade está otimizado por meio de agrupamento, cache e aceleração de hardware, mantendo as garantias de segurança criptográfica.

---

### C4.15 Segurança de Integração em Nuvem do Framework de Agentes e Implantação Híbrida

Controles de segurança para frameworks de agentes integrados em nuvem com arquiteturas híbridas on-premises/nuvem.

 #4.15.1    Nível: 1    Papel: D/V
 Verifique se a integração de armazenamento em nuvem utiliza criptografia de ponta a ponta com gerenciamento de chaves controlado pelo agente.
 #4.15.2    Nível: 2    Papel: D/V
 Verifique se os limites de segurança de implantação híbrida estão claramente definidos com canais de comunicação criptografados.
 #4.15.3    Nível: 2    Papel: D/V
 Verifique se o acesso aos recursos em nuvem inclui verificação de confiança zero com autenticação contínua.
 #4.15.4    Nível: 3    Papel: D/V
 Verifique se os requisitos de residência de dados são garantidos por atestação criptográfica das localidades de armazenamento.
 #4.15.5    Nível: 3    Papel: D/V
 Verifique se as avaliações de segurança do provedor de cloud incluem modelagem de ameaças específica do agente e avaliação de riscos.

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

## C5 Controle de Acesso e Identidade para Componentes e Usuários de IA

### Objetivo de Controle

O controle de acesso efetivo para sistemas de IA exige gestão de identidade robusta, autorização consciente do contexto e aplicação em tempo de execução, seguindo princípios de zero-trust. Esses controles garantem que humanos, serviços e agentes autônomos interajam apenas com modelos, dados e recursos computacionais dentro de escopos explicitamente concedidos, com verificação contínua e capacidades de auditoria.

---

### C5.1 Gerenciamento de Identidade e Autenticação

Estabeleça identidades respaldadas criptograficamente para todas as entidades com autenticação multifator para operações privilegiadas.

 #5.1.1    Nível: 1    Papel: D/V
 Verifique se todos os usuários humanos e principais de serviço autenticam-se por meio de um provedor de identidade corporativo centralizado (IdP) usando os protocolos OIDC/SAML, com mapeamentos únicos de identidade para token (sem contas ou credenciais compartilhadas).
 #5.1.2    Nível: 1    Papel: D/V
 Verifique se operações de alto risco (implantação de modelo, exportação de peso, acesso a dados de treinamento, alterações na configuração de produção) exigem autenticação multifator ou autenticação em etapas com revalidação de sessão.
 #5.1.3    Nível: 2    Papel: D
 Verifique se os novos principais passam por comprovação de identidade que esteja alinhada com o NIST 800-63-3 IAL-2 ou padrões equivalentes antes de receber acesso ao sistema de produção.
 #5.1.4    Nível: 2    Papel: V
 Verifique se as revisões de acesso são realizadas trimestralmente com detecção automatizada de contas inativas, aplicação de rotação de credenciais e fluxos de trabalho de desativação.
 #5.1.5    Nível: 3    Papel: D/V
 Verifique se os agentes de IA federados autenticam-se por meio de afirmações JWT assinadas que têm um tempo de validade máximo de 24 horas e incluem prova criptográfica de origem.

---

### C5.2 Autorização de Recursos e Privilégio Mínimo

Implemente controles de acesso de granulação fina para todos os recursos de IA com modelos de permissão explícitos e trilhas de auditoria.

 #5.2.1    Nível: 1    Papel: D/V
 Verifique se todos os recursos de IA (conjuntos de dados, modelos, endpoints, coleções de vetores, índices de incorporação, instâncias de computação) aplicam controles de acesso baseados em funções com listas de permissão explícitas e políticas padrão de negação.
 #5.2.2    Nível: 1    Papel: D/V
 Verifique se os princípios de mínimo privilégio são aplicados por padrão com contas de serviço começando com permissões de leitura e uma justificativa comercial documentada requerida para acesso de escrita.
 #5.2.3    Nível: 1    Papel: V
 Verifique se todas as modificações de controle de acesso estão vinculadas a solicitações de alteração aprovadas e registradas de forma imutável com carimbos de data/hora, identidades do ator, identificadores de recursos e diferenças de permissões.
 #5.2.4    Nível: 2    Papel: D
 Verifique se os rótulos de classificação de dados (PII, PHI, controlado por exportação, proprietário) propagam-se automaticamente para recursos derivados (embeddings, caches de prompts, saídas do modelo) com aplicação consistente da política.
 #5.2.5    Nível: 2    Papel: D/V
 Verifique se as tentativas de acesso não autorizado e eventos de escalonamento de privilégios acionam alertas em tempo real com metadata contextual para sistemas SIEM dentro de 5 minutos.

---

### C5.3 Avaliação Dinâmica de Políticas

Implante mecanismos de controle de acesso baseado em atributos (ABAC) para decisões de autorização sensíveis ao contexto, com capacidades de auditoria.

 #5.3.1    Nível: 1    Papel: D/V
 Verifique se as decisões de autorização são externalizadas para um motor de política dedicado (OPA, Cedar ou equivalente) acessível via APIs autenticadas com proteção de integridade criptográfica.
 #5.3.2    Nível: 1    Papel: D/V
 Verifique se as políticas avaliam atributos dinâmicos em tempo de execução, incluindo nível de liberação do usuário, classificação de sensibilidade do recurso, contexto da solicitação, isolamento do inquilino e restrições temporais.
 #5.3.3    Nível: 2    Papel: D
 Verifique se as definições de política estão sob controle de versão, passaram por revisão por pares e foram validadas por meio de testes automatizados em pipelines de CI/CD antes da implantação em produção.
 #5.3.4    Nível: 2    Papel: V
 Verifique se os resultados da avaliação da política incluem raciocínios de decisão estruturados e são transmitidos aos sistemas SIEM para análise de correlação e relatórios de conformidade.
 #5.3.5    Nível: 3    Papel: D/V
 Verifique se os valores de tempo de vida (TTL) do cache de política não excedem 5 minutos para recursos de alta sensibilidade e 1 hora para recursos padrão com capacidade de invalidação de cache.

---

### C5.4 Aplicação de Segurança em Tempo de Consulta

Implemente controles de segurança na camada de banco de dados com filtragem obrigatória e políticas de segurança a nível de linha.

 #5.4.1    Nível: 1    Papel: D/V
 Verifique se todas as consultas ao banco de dados vetorial e SQL incluem filtros de segurança obrigatórios (ID do locatário, rótulos de sensibilidade, escopo do usuário) aplicados no nível do motor do banco de dados, não no código da aplicação.
 #5.4.2    Nível: 1    Papel: D/V
 Verifique se as políticas de segurança a nível de linha (RLS) e mascaramento a nível de campo estão ativadas com herança de políticas para todos os bancos de dados vetoriais, índices de pesquisa e conjuntos de dados de treinamento.
 #5.4.3    Nível: 2    Papel: D
 Verifique se avaliações de autorização falhadas impedirão "ataques de deputado confuso" abortando imediatamente as consultas e retornando códigos de erro de autorização explícitos, em vez de retornar conjuntos de resultados vazios.
 #5.4.4    Nível: 2    Papel: V
 Verifique se a latência de avaliação da política está sendo monitorada continuamente com alertas automatizados para condições de tempo limite que poderiam permitir a bypass de autorização.
 #5.4.5    Nível: 3    Papel: D/V
 Verifique se os mecanismos de re tentativa de consulta reavaliam as políticas de autorização para levar em conta alterações dinâmicas de permissões dentro de sessões de usuário ativas.

---

### C5.5 Filtragem de Saída & Prevenção de Perda de Dados

Implemente controles de pós-processamento para evitar a exposição não autorizada de dados em conteúdo gerado por IA.

 #5.5.1    Nível: 1    Papel: D/V
 Verifique se os mecanismos de filtragem pós-inferência escaneiam e redigem informações pessoais identificáveis não autorizadas, informações classificadas e dados proprietários antes de entregar o conteúdo aos solicitantes.
 #5.5.2    Nível: 1    Papel: D/V
 Verifique se citações, referências e atribuições de fontes nas saídas do modelo são validadas em relação às permissões do solicitante e removidas caso seja detectado acesso não autorizado.
 #5.5.3    Nível: 2    Papel: D
 Verifique se as restrições de formato de saída (PDFs sanitizados, imagens sem metadata, tipos de arquivo aprovados) são aplicadas com base nos níveis de permissão do usuário e nas classificações de dados.
 #5.5.4    Nível: 2    Papel: V
 Verifique se os algoritmos de redação são determinísticos, controlados por versão e mantêm registros de auditoria para apoiar investigações de conformidade e análises forenses.
 #5.5.5    Nível: 3    Papel: V
 Verifique se eventos de redação de alto risco geram registros adaptativos que incluem hashes criptográficos do conteúdo original para recuperação forense sem exposição de dados.

---

### C5.6 Isolamento Multi-Inquilino

Garantir isolamento criptográfico e lógico entre locatários em infraestrutura de IA compartilhada.

 #5.6.1    Nível: 1    Papel: D/V
 Verifique se os espaços de memória, armazenamentos de embeds, entradas de cache e arquivos temporários estão segregados por namespace por locatário, com exclusão segura na exclusão do locatário ou término da sessão.
 #5.6.2    Nível: 1    Papel: D/V
 Verifique se cada solicitação de API inclui um identificador de inquilino autenticado que seja validado criptograficamente em relação ao contexto da sessão e às permissões do usuário.
 #5.6.3    Nível: 2    Papel: D
 Verifique se as políticas de rede implementam regras de negação padrão para comunicação entre inquilinos dentro de malhas de serviço e plataformas de orquestração de containers.
 #5.6.4    Nível: 3    Papel: D
 Verifique se as chaves de criptografia são exclusivas por locatário com suporte a chaves gerenciadas pelo cliente (CMK) e isolamento criptográfico entre os repositórios de dados dos locatários.

---

### C5.7 Autorização de Agente Autônomo

Controle de permissões para agentes de IA e sistemas autônomos por meio de tokens de capacidade com escopo e autorização contínua.

 #5.7.1    Nível: 1    Papel: D/V
 Verifique se agentes autônomos recebem tokens de capacidade com escopo que enumeram explicitamente ações permitidas, recursos acessíveis, limites de tempo e restrições operacionais.
 #5.7.2    Nível: 1    Papel: D/V
 Verifique se as capacidades de alto risco (acesso ao sistema de arquivos, execução de código, chamadas de API externas, transações financeiras) estão desativadas por padrão e exigem autorizações explícitas para ativação com justificativas comerciais.
 #5.7.3    Nível: 2    Papel: D
 Verifique se os tokens de capacidade estão vinculados às sessões de usuário, incluem proteção de integridade criptográfica e garantem que não possam ser persistidos ou reutilizados em cenários offline.
 #5.7.4    Nível: 2    Papel: V
 Verifique se as ações iniciadas pelo agente passam por autorização secundária através do mecanismo de política ABAC com avaliação de contexto completa e registro de auditoria.
 #5.7.5    Nível: 3    Papel: V
 Verifique se as condições de erro do agente e o tratamento de exceções incluem informações sobre o escopo da capacidade para apoiar a análise de incidentes e investigações forenses.

---

### Referências

#### Padrões & Estruturas

NIST SP 800-63-3: Digital Identity Guidelines
Zero Trust Architecture – NIST SP 800-207
OWASP Application Security Verification Standard (AISVS)
​
#### Guias de Implementação

Identity and Access Management in the AI Era: 2025 Guide – IDSA
Attribute-Based Access Control with OPA – Permify
How We Designed Cedar to Be Intuitive, Fast, and Safe – AWS
​
#### Segurança Específica de AI

Row Level Security in Vector DBs for RAG – Bluetuple.ai
Tenant Isolation in Multi-Tenant Systems – WorkOS
Handling AI Agent Permissions – Stytch
OWASP Top 10 for Large Language Model Applications

## C6 Segurança da Cadeia de Suprimentos para Modelos, Estruturas e Dados

### Objetivo de Controle

Ataques na cadeia de suprimentos de IA exploram modelos, frameworks ou conjuntos de dados de terceiros para inserir backdoors, viés ou códigos exploráveis. Esses controles fornecem proveniência de ponta a ponta, gerenciamento de vulnerabilidades e monitoramento para proteger todo o ciclo de vida do modelo.

---

### C6.1 Avaliação de Modelo Pré-treinado & Proveniência

Avalie e autentique as origens, licenças e comportamentos ocultos de modelos de terceiros antes de qualquer ajuste fino ou implantação.

 #6.1.1    Nível: 1    Papel: D/V
 Verifique se todo artefato de modelo de terceiros inclui um registro de proveniência assinado que identifique o repositório de origem e o hash do commit.
 #6.1.2    Nível: 1    Papel: D/V
 Verifique se os modelos foram analisados quanto à presença de camadas maliciosas ou gatilhos Trojan usando ferramentas automatizadas antes da importação.
 #6.1.3    Nível: 2    Papel: D
 Verifique se o ajuste fino de transfer‑learning passa na avaliação adversarial para detectar comportamentos ocultos.
 #6.1.4    Nível: 2    Papel: V
 Verifique se as licenças do modelo, tags de controle de exportação e declarações de origem dos dados estão registradas em uma entrada do ML‑BOM.
 #6.1.5    Nível: 3    Papel: D/V
 Verifique se os modelos de alto risco ( pesos carregados publicamente, criadores não verificados) permanecem em quarentena até revisão e aprovação humana.

---

### C6.2 Varredura de Frameworks & Bibliotecas

Escaneie continuamente frameworks e bibliotecas de ML em busca de CVEs e código malicioso para manter a pilha de tempo de execução segura.

 #6.2.1    Nível: 1    Papel: D/V
 Verifique se os pipelines de CI executam varredores de dependências em frameworks de IA e bibliotecas críticas.
 #6.2.2    Nível: 1    Papel: D/V
 Verifique se vulnerabilidades críticas (CVSS ≥ 7.0) bloqueiam a promoção para imagens de produção.
 #6.2.3    Nível: 2    Papel: D
 Verifique se a análise de código estático é executada em bibliotecas de ML bifurcadas ou vendidas.
 #6.2.4    Nível: 2    Papel: V
 Verifique se as propostas de atualização do framework incluem uma avaliação de impacto de segurança referenciando feeds públicos de CVE.
 #6.2.5    Nível: 3    Papel: V
 Verifique se os sensores em tempo de execução alertam sobre carregamentos inesperados de bibliotecas dinâmicas que divergem do SBOM assinado.

---

### C6.3 Fixação e Verificação de Dependências

Fixe cada dependência em dígitos imutáveis e reproduza builds para garantir artefatos idênticos e livres de adulteração.

 #6.3.1    Nível: 1    Papel: D/V
 Verifique se todos os gerenciadores de pacotes aplicam o pinning de versões por meio de arquivos de bloqueio.
 #6.3.2    Nível: 1    Papel: D/V
 Verifique se os resumos imutáveis são usados em vez de tags mutáveis nas referências de container.
 #6.3.3    Nível: 2    Papel: D
 Verifique se as verificações de build reproduzível comparam hashes entre execuções de CI para garantir saídas idênticas.
 #6.3.4    Nível: 2    Papel: V
 Verifique se as attestations de build são armazenadas por 18 meses para rastreabilidade de auditoria.
 #6.3.5    Nível: 3    Papel: D
 Verifique se dependências expiradas acionam PRs automáticos para atualização ou bifurcação de versões fixadas.

---

### C6.4 Aplicação de Fonte Confiável

Permitir downloads de artefatos apenas de fontes verificadas criptograficamente e aprovada pela organização, bloqueando tudo o mais.

 #6.4.1    Nível: 1    Papel: D/V
 Verifique se os pesos do modelo, conjuntos de dados e containers são baixados apenas de domínios aprovados ou registros internos.
 #6.4.2    Nível: 1    Papel: D/V
 Verifique se as assinaturas do Sigstore/Cosign validam a identidade do publicador antes que os artefatos sejam armazenados em cache localmente.
 #6.4.3    Nível: 2    Papel: D
 Verifique se proxies de saída bloqueiam downloads de artefatos não autenticados para garantir a política de fonte confiável.
 #6.4.4    Nível: 2    Papel: V
 Verifique se as listas de permissão do repositório são revisadas trimestralmente com evidências de justificativa de negócios para cada entrada.
 #6.4.5    Nível: 3    Papel: V
 Verifique se violações de política acionam o quarentena de artefatos e rollback de execuções de pipeline dependentes.

---

### C6.5 Avaliação de Risco de Conjuntos de Dados de Terceiros

Avalie conjuntos de dados externos quanto a envenenamento, viés e conformidade legal, e monitore-os ao longo de seu ciclo de vida.

 #6.5.1    Nível: 1    Papel: D/V
 Verifique se os conjuntos de dados externos passam por uma avaliação de risco de envenenamento (por exemplo, impressão digital de dados, detecção de outliers).
 #6.5.2    Nível: 1    Papel: D
 Verifique se as métricas de viés (paridade demográfica, oportunidade igual) são calculadas antes da aprovação do conjunto de dados.
 #6.5.3    Nível: 2    Papel: V
 Verifique se a proveniência e os termos de licença para conjuntos de dados estão registrados nas entradas do ML‑BOM.
 #6.5.4    Nível: 2    Papel: V
 Verifique se a monitorização periódica detecta deriva ou corrupção nos conjuntos de dados hospedados.
 #6.5.5    Nível: 3    Papel: D
 Verifique se o conteúdo não permitido (direitos autorais, PII) foi removido por meio de limpeza automatizada antes do treinamento.

---

### C6.6 Monitoramento de Ataques na Cadeia de Fornecimento

Detecte ameaças na cadeia de suprimentos cedo através de feeds CVE, análise de logs de auditoria e simulações de equipe vermelha.

 #6.6.1    Nível: 1    Papel: V
 Verifique se os registros de auditoria CI/CD são transmitidos para as detecções SIEM por pulls de pacote anômalicos ou etapas de build adulteradas.
 #6.6.2    Nível: 2    Papel: D
 Verifique se os playbooks de resposta a incidentes incluem procedimentos de rollback para modelos ou bibliotecas comprometidos.
 #6.6.3    Nível: 3    Papel: V
 Verifique se as tags de enriquecimento de inteligência de ameaça indicam indicadores específicos de ML (por exemplo, IoCs de envenenamento de modelo) na triagem de alertas.

---

### C6.7 ML‑BOM para Artefatos de Modelo

Gerar e assinar SBOMs específicos de ML‑ (ML‑BOMs) detalhados para que os consumidores downstream possam verificar a integridade dos componentes no momento do deploy.

 #6.7.1    Nível: 1    Papel: D/V
 Verifique se cada artefato de modelo publica uma ML‑BOM que liste conjuntos de dados, pesos, hiperparâmetros e licenças.
 #6.7.2    Nível: 1    Papel: D/V
 Verifique se a geração de ML‑BOM e a assinatura do Cosign estão automatizadas no CI e são necessárias para a mesclagem.
 #6.7.3    Nível: 2    Papel: D
 Verifique se as verificações de completude do ML‑BOM falham na construção se algum metadado do componente (hash, licença) estiver ausente.
 #6.7.4    Nível: 2    Papel: V
 Verifique se os consumidores downstream podem consultar os ML-BOMs via API para validar os modelos importados durante o tempo de implantação.
 #6.7.5    Nível: 3    Papel: V
 Verifique se os ML‑BOMs estão sob controle de versão e com diferenças monitoradas para detectar modificações não autorizadas.

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

As saídas do modelo devem ser estruturadas, confiáveis, seguras, explicáveis e continuamente monitoradas em produção. Isso reduz alucinações, vazamentos de privacidade, conteúdo prejudicial e ações descontroladas, aumentando ao mesmo tempo a confiança do usuário e a conformidade regulatória.

---

### C7.1 Aplicação da Forma de Saída

Esquemas rigorosos, decodificação com restrições e validação subsequente impedem que conteúdo malformado ou malicioso se propague.

 #7.1.1    Nível: 1    Papel: D/V
 Verifique se os esquemas de resposta (por exemplo, JSON Schema) estão fornecidos no prompt do sistema e se toda saída é validada automaticamente; saídas não conformes acionam reparo ou rejeição.
 #7.1.2    Nível: 1    Papel: D/V
 Verifique se a decodificação restrita ( tokens de parada, regex, máximo de tokens) está habilitada para evitar estouro ou canais laterais de injeção de prompts.
 #7.1.3    Nível: 2    Papel: D/V
 Verifique se os componentes downstream tratam as saídas como não confiáveis e as validam contra esquemas ou desserializadores seguros contra injeções.
 #7.1.4    Nível: 3    Papel: V
 Verifique se eventos de saída incorreta são registrados, limitados em taxa e exibidos na monitoração.

---

### C7.2 Detecção e Mitigação de Alucinações

A estimação de incerteza e estratégias de fallback reduzem respostas fabricadas.

 #7.2.1    Nível: 1    Papel: D/V
 Verifique se as log-probabilidades a nível de token, a autossessão de ensemble ou os detectores de alucinação ajustados atribuem uma pontuação de confiança a cada resposta.
 #7.2.2    Nível: 1    Papel: D/V
 Verifique se as respostas abaixo de um limiar de confiança configurável acionam fluxos de fallback (por exemplo, geração aumentada por recuperação, modelo secundário ou revisão humana).
 #7.2.3    Nível: 2    Papel: D/V
 Verifique se os incidentes de alucinação estão marcados com metadados de causa raiz e alimentados nos pipelines de análise pós-mortem e de ajuste fino.
 #7.2.4    Nível: 3    Papel: D/V
 Verifique se os limiares e detectores foram recalibrados após atualizações principais do modelo ou da base de conhecimento.
 #7.2.5    Nível: 3    Papel: V
 Verifique se as visualizações do painel monitoram as taxas de alucinação.

---

### C7.3 Filtragem de Segurança e Privacidade de Saída

Filtros de política e cobertura de red-team protegem usuários e dados confidenciais.

 #7.3.1    Nível: 1    Papel: D/V
 Verifique se os classificadores pré e pós-geração bloqueiam conteúdo de ódio, assédio, autoagressão, extremismo e conteúdo sexual explicitamente alinhado à política.
 #7.3.2    Nível: 1    Papel: D/V
 Verifique se a detecção de PII/PCI e a redação automática estão sendo executadas em todas as respostas; violações devem gerar uma ocorrência de privacidade.
 #7.3.3    Nível: 2    Papel: D
 Verifique se as tags de confidencialidade (por exemplo, segredos comerciais) se propagam entre modalidades para impedir vazamentos em texto, imagens ou código.
 #7.3.4    Nível: 3    Papel: D/V
 Verifique se tentativas de contornar filtros ou classificações de alto risco exigem aprovação secundária ou reautenticação do usuário.
 #7.3.5    Nível: 3    Papel: D/V
 Verifique se os limites de filtragem refletem as jurisdições legais e o contexto de idade/função do usuário.

---

### C7.4 Limitação de Saída & Ação

Limites de taxa e gates de aprovação impedem abuso e autonomia excessiva.

 #7.4.1    Nível: 1    Papel: D
 Verifique se as quotas por usuário e por chave de API limitam solicitações, tokens e custos com retrocesso exponencial em erros 429.
 #7.4.2    Nível: 1    Papel: D/V
 Verifique se ações privilegiadas (gravações de arquivos, execução de código, chamadas de rede) exigem aprovação baseada em políticas ou intervenção humana.
 #7.4.3    Nível: 2    Papel: D/V
 Verifique se os testes de consistência cross-modal garantem que imagens, códigos e textos gerados para a mesma solicitação não possam ser usados para mascarar conteúdo malicioso.
 #7.4.4    Nível: 2    Papel: D
 Verifique se a profundidade de delegação de agente, os limites de recursão e as listas de ferramentas permitidas estão configurados explicitamente.
 #7.4.5    Nível: 3    Papel: V
 Verifique se a violação de limites emite eventos de segurança estruturados para ingestão em SIEM.

---

### C7.5 Explicabilidade do Resultado

Sinais transparentes aumentam a confiança do usuário e a depuração interna.

 #7.5.1    Nível: 2    Papel: D/V
 Verifique se as pontuações de confiança ou resumos de raciocínio breves voltados ao usuário são expostos quando a avaliação de risco considerar apropriado.
 #7.5.2    Nível: 2    Papel: D/V
 Verifique se as explicações geradas evitam revelar prompts de sistema confidenciais ou dados proprietários.
 #7.5.3    Nível: 3    Papel: D
 Verifique se o sistema captura log-probabilidades ao nível de token ou mapas de atenção e os armazena para inspeção autorizada.
 #7.5.4    Nível: 3    Papel: V
 Verifique se os artefatos de explicabilidade estão sob controle de versão junto com as versões do modelo para auditoria.

---

### C7.6 Integração de Monitoramento

A observabilidade em tempo real fecha o ciclo entre desenvolvimento e produção.

 #7.6.1    Nível: 1    Papel: D
 Verifique se as métricas ( violações de esquema, taxa de alucinação, toxicidade, vazamentos de PII, latência, custo) estão sendo transmitidas para uma plataforma de monitoramento centralizada.
 #7.6.2    Nível: 1    Papel: V
 Verifique se os limites de alerta estão definidos para cada métrica de segurança, com rotas de escalonamento de plantão.
 #7.6.3    Nível: 2    Papel: V
 Verifique se os painéis correlacionam anomalias de saída com modelo/versão, flag de recurso e mudanças nos dados upstream.
 #7.6.4    Nível: 2    Papel: D/V
 Verifique se os dados de monitoramento retornam para requalificação, ajuste fino ou atualizações de regras dentro de um fluxo de trabalho documentado de MLOps.
 #7.6.5    Nível: 3    Papel: V
 Verifique se os pipelines de monitoramento são testados quanto à penetração e controlados por acesso para evitar vazamento de logs sensíveis.

---

### 7.7 Salvaguardas de Mídia Generativa

Garanta que os sistemas de IA não gerem conteúdo de mídia ilegal, prejudicial ou não autorizado, aplicando restrições de políticas, validação de saída e rastreabilidade.

 #7.7.1    Nível: 1    Papel: D/V
 Verifique se os prompts do sistema e as instruções do usuário proíbem explicitamente a geração de mídia deepfake ilegal, prejudicial ou não consensual (por exemplo, imagem, vídeo, áudio).
 #7.7.2    Nível: 2    Papel: D/V
 Verifique se os prompts estão filtrados para evitar tentativas de gerar impersonificações, deepfakes sexualmente explícitos ou mídia que retrate pessoas reais sem consentimento.
 #7.7.3    Nível: 2    Papel: V
 Verifique se o sistema usa hashing perceptual, detecção de marca d'água ou fingerprinting para evitar a reprodução não autorizada de mídia protegida por direitos autorais.
 #7.7.4    Nível: 3    Papel: D/V
 Verifique se todos os meios de comunicação gerados estão criptograficamente assinados, com marca d'água ou incorporados com metadados de proveniência à prova de adulteração para rastreabilidade futura.
 #7.7.5    Nível: 3    Papel: V
 Verifique se as tentativas de contornar as restrições (por exemplo, obfuscação de prompts, gírias, frases adversariais) são detectadas, registradas em log e limitadas em taxa; abusos recorrentes são destacados para os sistemas de monitoramento.

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

## Segurança de Memória C8, Embeddings e Banco de Dados de Vetores

### Objetivo de Controle

Embeddings e bancos de vetores atuam como a "memória ao vivo" dos sistemas de IA contemporâneos, aceitando continuamente dados fornecidos pelo usuário e trazendo-os de volta aos contextos do modelo por meio da Geração Aumentada por Recuperação (RAG). Se não forem governados, essa memória pode vazar PII, violar consentimento ou ser invertida para reconstruir o texto original. O objetivo desta família de controles é fortalecer pipelines de memória e bancos de vetores para que o acesso seja de privilégio mínimo, embeddings sejam privacidade-resguardados, vetores armazenados expirem ou possam ser revogados sob demanda, e a memória por usuário nunca contamine os prompts ou conclusões de outro usuário.

---

### C8.1 Controles de Acesso à Memória & Índices RAG

Impor stricter controles de acesso detalhados em cada coleção de vetores.

 #8.1.1    Nível: 1    Papel: D/V
 Verifique se as regras de controle de acesso a nível de linha/namespace restringem as operações de inserir, excluir e consultar por locatário, coleção ou etiqueta de documento.
 #8.1.2    Nível: 1    Papel: D/V
 Verifique se as chaves de API ou JWTs carregam declarações de escopo (por exemplo, IDs de coleção, verbos de ação) e são rotacionados pelo menos a cada trimestre.
 #8.1.3    Nível: 2    Papel: D/V
 Verifique se as tentativas de escalonamento de privilégios (por exemplo, consultas de similaridade entre namespaces) são detectadas e registradas em um SIEM dentro de 5 minutos.
 #8.1.4    Nível: 2    Papel: D/V
 Verifique se o log de auditoria do banco de dados vetorial registra o identificador do sujeito, operação, ID/namespace do vetor, limiar de similaridade e contagem de resultados.
 #8.1.5    Nível: 3    Papel: V
 Verifique se as decisões de acesso são testadas quanto a falhas de bypass sempre que os mecanismos são atualizados ou as regras de sharding de índice são alteradas.

---

### C8.2 Sanitização e Validação de Embeddings

Pré-selecionar o texto para PII, redigir ou pseudonimizar antes da vetorização, e opcionalmente pós-processar as embeddings para remover sinais residuais.

 #8.2.1    Nível: 1    Papel: D/V
 Verifique se PII e dados regulamentados são detectados por meio de classificadores automatizados e mascarados, tokenizados ou descartados antes de serem incorporados.
 #8.2.2    Nível: 1    Papel: D
 Verifique se os pipelines de embedamento rejeitam ou colocam em quarentena entradas que contenham código executável ou artefatos não-UTF-8 que possam contaminar o índice.
 #8.2.3    Nível: 2    Papel: D/V
 Verifique se a sanitização local ou métrica de privacidade diferencial foi aplicada às embedagens de sentença cujas distâncias para qualquer token de PII conhecido caem abaixo de um limiar configurável.
 #8.2.4    Nível: 2    Papel: V
 Verifique se a eficácia da sanitização (por exemplo, recall da redação de PII, drift semântico) é validada pelo menos semestralmente usando corpora de referência.
 #8.2.5    Nível: 3    Papel: D/V
 Verifique se as configurações de sanitização estão sob controle de versão e se as alterações passam por revisão por pares.

---

### C8.3 Expiração, Revogação e Exclusão de Memória

O GDPR "direito ao esquecimento" e leis similares exigem exclusão oportuna; portanto, os armazenamentos vetoriais devem suportar TTLs, exclusões permanentes e tombstoning para que vetores revogados não possam ser recuperados ou reindexados.

 #8.3.1    Nível: 1    Papel: D/V
 Verifique se cada vetor e registro de metadados possui um TTL ou rótulo de retenção explícito, respeitado pelos trabalhos de limpeza automatizados.
 #8.3.2    Nível: 1    Papel: D/V
 Verifique se as solicitações de exclusão iniciadas pelo usuário eliminam vetores, metadados, cópias em cache e índices derivados dentro de 30 dias.
 #8.3.3    Nível: 2    Papel: D
 Verifique se as exclusões lógicas são seguidas pela destruição criptográfica dos blocos de armazenamento, se o hardware suportar, ou pela destruição da chave no coffers de chaves.
 #8.3.4    Nível: 3    Papel: D/V
 Verifique se vetores expirados são excluídos dos resultados da busca pelos vizinhos mais próximos em menos de 500 ms após a expiração.

---

### C8.4 Prevenir Inversão de Embedding & Vazamento

Defesas recentes—superposição de ruído, redes de projeção, perturbação de neurônios de privacidade e criptografia na camada de aplicação—podem reduzir as taxas de inversão ao nível de token abaixo de 5%.

 #8.4.1    Nível: 1    Papel: V
 Verifique se existe um modelo formal de ameaça que cobre ataques de inversão, de pertencimento e de inferência de atributos e se ele é revisado anualmente.
 #8.4.2    Nível: 2    Papel: D/V
 Verifique se a criptografia de camada de aplicação ou criptografia pesquisável protegem os vetores de leitura direta por administradores de infraestrutura ou equipe de nuvem.
 #8.4.3    Nível: 3    Papel: V
 Verifique se os parâmetros de defesa (ε para DP, ruído σ, rank de projeção k) equilibram privacidade ≥ 99 % proteção do token e utilidade ≤ 3 % perda de precisão.
 #8.4.4    Nível: 3    Papel: D/V
 Verifique se as métricas de resiliência à inversão fazem parte das portas de liberação para atualizações de modelos, com orçamentos de regressão definidos.

---

### C8.5 Aplicação de Escopo para Memória Específica do Usuário

Vazamentos entre locatários continuam sendo um risco principal de RAG: consultas de similaridade filtradas de forma inadequada podem revelar documentos privados de outro cliente.

 #8.5.1    Nível: 1    Papel: D/V
 Verifique se cada consulta de recuperação é filtrada posteriormente pelo ID do inquilino/usuário antes de ser encaminhada ao prompt do LLM.
 #8.5.2    Nível: 1    Papel: D
 Verifique se os nomes de coleções ou IDs de namespace são salteados por usuário ou locatário, para que os vetores não possam colidir entre escopos.
 #8.5.3    Nível: 2    Papel: D/V
 Verifique se os resultados de similaridade acima de um limiar de distância configurável, mas fora do escopo do chamador, são descartados e acionam alertas de segurança.
 #8.5.4    Nível: 2    Papel: V
 Verifique se os testes de estresse multi-inquilino simulam consultas adversariais tentando recuperar documentos fora do escopo e demonstre ausência de vazamento.
 #8.5.5    Nível: 3    Papel: D/V
 Verifique se as chaves de criptografia estão segregadas por locatário, garantindo isolamento criptográfico mesmo que o armazenamento físico seja compartilhado.

---

### C8.6 Segurança Avançada de Sistemas de Memória

Controles de segurança para arquiteturas de memória sofisticadas, incluindo memória episódica, semântica e de trabalho, com requisitos específicos de isolamento e validação.

 #8.6.1    Nível: 1    Papel: D/V
 Verifique se os diferentes tipos de memória (episódica, semântica, de trabalho) possuem contextos de segurança isolados com controles de acesso baseados em papéis, chaves de criptografia separadas e padrões de acesso documentados para cada tipo de memória.
 #8.6.2    Nível: 2    Papel: D/V
 Verifique se os processos de consolidação da memória incluem validação de segurança para evitar a injeção de memórias maliciosas por meio de sanitização de conteúdo, verificação da fonte e verificações de integridade antes do armazenamento.
 #8.6.3    Nível: 2    Papel: D/V
 Verifique se as consultas de recuperação de memória são validadas e sanitizadas para prevenir a extração de informações não autorizadas por meio de análise de padrão de consulta, aplicação de controle de acesso e filtragem de resultados.
 #8.6.4    Nível: 3    Papel: D/V
 Verifique se os mecanismos de esquecimento de memória excluem de forma segura informações confidenciais, garantindo eliminação criptográfica usando apagamento de chave, sobrescrita múltipla ou exclusão segura baseada em hardware com certificados de verificação.
 #8.6.5    Nível: 3    Papel: D/V
 Verifique se a integridade do sistema de memória está sendo monitorada continuamente para detectar modificações ou corrupção não autorizadas através de somas de verificação, registros de auditoria e alertas automatizados quando o conteúdo da memória muda fora das operações normais.

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

## 9 Segurança de Orquestração Autônoma e Ação Agente

### Objetivo de Controle

Assegure-se de que sistemas de IA autônomos ou multi-agente possam executar apenas ações explicitamente desejadas, autenticadas, auditáveis e dentro de limites de custo e risco definidos. Isso protege contra ameaças como Comprometimento de Sistemas Autônomos, Uso Indevido de Ferramentas, Detecção de Loop de Agente, Sequestro de Comunicação, Falsificação de Identidade, Manipulação de Enxame e Manipulação de Intenção.

---

### 9.1 Planejamento de Tarefas do Agente e Orçamentos de Recursão

Restringir planos recursivos e forçar pontos de verificação humanos para ações privilegiadas.

 #9.1.1    Nível: 1    Papel: D/V
 Verifique se a profundidade máxima de recursão, largura, tempo wall-clock, tokens e custo monetário por execução do agente estão configurados de forma centralizada e sob controle de versão.
 #9.1.2    Nível: 1    Papel: D/V
 Verifique se ações privilegiadas ou irreversíveis (por exemplo, commits de código, transferências financeiras) requerem aprovação explícita humana através de um canal auditorável antes da execução.
 #9.1.3    Nível: 2    Papel: D
 Verifique se os monitores de recursos em tempo real acionam a interrupção do circuito-breaker quando qualquer limite de orçamento é excedido, interrompendo a expansão adicional da tarefa.
 #9.1.4    Nível: 2    Papel: D/V
 Verifique se os eventos do disjuntor estão registrados com ID do agente, condição de acionamento e estado do plano capturado para revisão forense.
 #9.1.5    Nível: 3    Papel: V
 Verifique se os testes de segurança cobrem os cenários de esgotamento de orçamento e plano de fuga, confirmando a parada segura sem perda de dados.
 #9.1.6    Nível: 3    Papel: D
 Verifique se as políticas orçamentárias estão expressas como política-como-código e aplicadas em CI/CD para bloquear a deriva de configuração.

---

### 9.2 sandboxing de plugins de ferramentas

Isole as interações das ferramentas para impedir acesso não autorizado ao sistema ou execução de código.

 #9.2.1    Nível: 1    Papel: D/V
 Verifique se cada ferramenta/plugin é executada dentro de uma sandbox de nível OS, container ou WASM, com políticas de privilégios mínimos para o sistema de arquivos, rede e chamadas do sistema.
 #9.2.2    Nível: 1    Papel: D/V
 Verifique se as quotas de recursos do sandbox (CPU, memória, disco, saída de rede) e os tempos limite de execução estão sendo aplicados e registrados.
 #9.2.3    Nível: 2    Papel: D/V
 Verifique se os binários ou descritores da ferramenta estão assinados digitalmente; as assinaturas são validadas antes do carregamento.
 #9.2.4    Nível: 2    Papel: V
 Verifique se os fluxos de telemetria do sandbox são enviados para um SIEM; anomalias (por exemplo, tentativas de conexões de saída) geram alertas.
 #9.2.5    Nível: 3    Papel: V
 Verifique se plugins de alto risco passam por revisão de segurança e testes de penetração antes da implantação em produção.
 #9.2.6    Nível: 3    Papel: D/V
 Verifique se as tentativas de escape do sandbox são automaticamente bloqueadas e o plugin suspeito é colocado em quarentena aguardando investigação.

---

### 9.3 Laço Autônomo e Limitação de Custo

Detectar e interromper a recursão descontrolada de agentes para agentes e explosões de custo.

 #9.3.1    Nível: 1    Papel: D/V
 Verifique se as chamadas entre agentes incluem um limite de saltos ou TTL que o tempo de execução decrementa e aplica.
 #9.3.2    Nível: 2    Papel: D
 Verifique se os agentes mantêm um ID de gráfico de invocação exclusivo para identificar auto-invocações ou padrões cíclicos.
 #9.3.3    Nível: 2    Papel: D/V
 Verifique se os contadores de unidades de computação acumuladas e gastos estão sendo monitorados por cadeia de requisição; ultrapassar o limite aborta a cadeia.
 #9.3.4    Nível: 3    Papel: V
 Verifique se a análise formal ou a verificação de modelos demonstra a ausência de recursão não limitada em protocolos de agentes.
 #9.3.5    Nível: 3    Papel: D
 Verifique se eventos de aborto de loop geram alertas e alimentam métricas de melhoria contínua.

---

### 9.4 Proteção contra Uso Indevido a Nível de Protocolo

Canais de comunicação seguros entre agentes e sistemas externos para evitar sequestro ou manipulação.

 #9.4.1    Nível: 1    Papel: D/V
 Verifique se todas as mensagens de agente para ferramenta e de agente para agente estão autenticadas (por exemplo, TLS mútuo ou JWT) e criptografadas de ponta a ponta.
 #9.4.2    Nível: 1    Papel: D
 Verifique se os esquemas são estritamente validados; campos desconhecidos ou mensagens malformadas são rejeitados.
 #9.4.3    Nível: 2    Papel: D/V
 Verifique se as verificações de integridade (MACs ou assinaturas digitais) cobrem toda a carga da mensagem, incluindo os parâmetros da ferramenta.
 #9.4.4    Nível: 2    Papel: D
 Verifique se a proteção contra replay (nonces ou janelas de timestamps) é aplicada na camada de protocolo.
 #9.4.5    Nível: 3    Papel: V
 Verifique se as implementações de protocolo passam por fuzzing e análise estática para detectar falhas de injeção ou desserialização.

---

### 9.5 Identidade do Agente e Evidência de Manipulação

Garanta que as ações sejam atribuíveis e as modificações detectáveis.

 #9.5.1    Nível: 1    Papel: D/V
 Verifique se cada instância de agente possui uma identidade criptográfica única (par de chaves ou credencial baseada em hardware).
 #9.5.2    Nível: 2    Papel: D/V
 Verifique se todas as ações do agente estão assinadas e marcadas com data/hora; os registros incluem a assinatura para não repúdio.
 #9.5.3    Nível: 2    Papel: V
 Verifique se os registros à prova de adulteração estão armazenados em um meio de gravação somente adição ou de gravação única.
 #9.5.4    Nível: 3    Papel: D
 Verifique se as chaves de identidade são rotacionadas em uma programação definida e com indicadores de comprometimento.
 #9.5.5    Nível: 3    Papel: D/V
 Verifique se tentativas de spoofing ou conflito de chaves acionam a quarentena imediata do agente afetado.

---

### 9.6 Redução de Risco por Enxame Multi-Agente

Mitigue os riscos de comportamento coletivo por meio de isolamento e modelagem formal de segurança.

 #9.6.1    Nível: 1    Papel: D/V
 Verifique se os agentes que operam em diferentes domínios de segurança são executados em sandboxes de tempo de execução isolados ou segmentos de rede.
 #9.6.2    Nível: 3    Papel: V
 Verifique se os comportamentos de enxame são modelados e verificados formalmente quanto à vivacidade e segurança antes da implantação.
 #9.6.3    Nível: 3    Papel: D
 Verifique se os monitores de tempo de execução detectam padrões inseguro emergentes (por exemplo, oscilações, impasses) e iniciam ações corretivas.

---

### 9.7 Autenticação / Autorização de Usuário & Ferramenta

Implemente controles de acesso robustos para cada ação acionada pelo agente.

 #9.7.1    Nível: 1    Papel: D/V
 Verifique se os agentes se autenticam como principais de primeira classe em sistemas downstream, nunca reutilizando credenciais de usuários finais.
 #9.7.2    Nível: 2    Papel: D
 Verifique se as políticas de autorização de granularidade fina restringem quais ferramentas um agente pode invocar e quais parâmetros ele pode fornecer.
 #9.7.3    Nível: 2    Papel: V
 Verifique se as verificações de privilégio são reavaliadas a cada chamada (autorização contínua), não apenas no início da sessão.
 #9.7.4    Nível: 3    Papel: D
 Verifique se os privilégios delegados expiram automaticamente e requerem nova consentimento após o tempo limite ou alteração do escopo.

---

### 9.8 Segurança na Comunicação entre Agentes

Criptografe e proteja a integridade de todas as mensagens entre agentes para impedir espionagem e adulteração.

 #9.8.1    Nível: 1    Papel: D/V
 Verifique se a autenticação mútua e a criptografia com segredo perfeito-avançado (por exemplo, TLS 1.3) são obrigatórias para canais de agente.
 #9.8.2    Nível: 1    Papel: D
 Verifique se a integridade e a origem da mensagem são validadas antes do processamento; falhas geram alertas e descartam a mensagem.
 #9.8.3    Nível: 2    Papel: D/V
 Verifique se os metadados de comunicação (carimbos de data/hora, números de sequência) estão registrados para apoiar a reconstrução forense.
 #9.8.4    Nível: 3    Papel: V
 Verifique se a verificação formal ou a verificação de modelos confirma que máquinas de estado do protocolo não podem ser acionadas para estados inseguros.

---

### 9.9 Verificação de Intenção e Aplicação de Restrições

Verifique se as ações do agente estão alinhadas com a intenção declarada do usuário e as restrições do sistema.

 #9.9.1    Nível: 1    Papel: D
 Verifique se os solucionadores de restrições de pré-execução verificam as ações propostas contra regras de segurança e políticas codificadas.
 #9.9.2    Nível: 2    Papel: D/V
 Verifique se ações de alto impacto (financeiras, destrutivas, sensíveis à privacidade) requerem confirmação explícita de intenção do usuário que as iniciou.
 #9.9.3    Nível: 2    Papel: V
 Verifique se as verificações de condição pós-condição validam que as ações concluídas alcançaram os efeitos desejados sem efeitos colaterais; discrepâncias acionam rollback.
 #9.9.4    Nível: 3    Papel: V
 Verifique se métodos formais (por exemplo, verificação de modelos, prova de teoremas) ou testes baseados em propriedades demonstram que os planos do agente atendem a todas as restrições declaradas.
 #9.9.5    Nível: 3    Papel: D
 Verifique se incidentes de incompatibilidade de intenção ou violação de restrições alimentam ciclos de melhoria contínua e compartilhamento de inteligência de ameaças.

---

### 9.10 Estratégia de Raciocínio do Agente Segurança

Seleção segura e execução de diferentes estratégias de raciocínio, incluindo abordagens ReAct, Chain-of-Thought e Tree-of-Thoughts.

 #9.10.1    Nível: 1    Papel: D/V
 Verifique se a seleção da estratégia de raciocínio usa critérios determinísticos (complexidade da entrada, tipo de tarefa, contexto de segurança) e se entradas idênticas produzem seleções de estratégia idênticas dentro do mesmo contexto de segurança.
 #9.10.2    Nível: 1    Papel: D/V
 Verifique se cada estratégia de raciocínio (ReAct, Chain-of-Thought, Tree-of-Thoughts) possui validação de entrada dedicada, sanitização de saída e limites de tempo de execução específicos para sua abordagem cognitiva.
 #9.10.3    Nível: 2    Papel: D/V
 Verifique se as transições de estratégia de raciocínio estão registradas com contexto completo, incluindo características de entrada, valores dos critérios de seleção e metadados de execução para reconstrução do rastro de auditoria.
 #9.10.4    Nível: 2    Papel: D/V
 Verifique se o raciocínio Tree-of-Thoughts inclui mecanismos de poda de ramos que encerram a exploração quando violações de política, limites de recursos ou fronteiras de segurança são detectados.
 #9.10.5    Nível: 2    Papel: D/V
 Verifique se os ciclos ReAct (Razão-Ação-Observação) incluem pontos de verificação de validação em cada fase: verificação do passo de raciocínio, autorização da ação e sanitização da observação antes de prosseguir.
 #9.10.6    Nível: 3    Papel: D/V
 Verifique se as métricas de desempenho da estratégia de raciocínio (tempo de execução, uso de recursos, qualidade da saída) estão sendo monitoradas com alertas automáticos quando as métricas desviam-se além dos limites configurados.
 #9.10.7    Nível: 3    Papel: D/V
 Verifique se as abordagens de raciocínio híbrido que combinam múltiplas estratégias mantêm a validação de entrada e as restrições de saída de todas as estratégias constituintes, sem contornar nenhum controle de segurança.
 #9.10.8    Nível: 3    Papel: D/V
 Verifique se os testes de segurança da estratégia de raciocínio incluem fuzzing com entradas malformadas, prompts adversariais projetados para forçar a troca de estratégia e testes de condições de limite para cada abordagem cognitiva.

---

### 9.11 Gestão do Estado do Ciclo de Vida do Agente e Segurança

Inicialização do agente seguro, transições de estado e terminação com trilhas de auditoria criptográficas e procedimentos de recuperação definidos.

 #9.11.1    Nível: 1    Papel: D/V
 Verifique se a inicialização do agente inclui o estabelecimento de identidade criptográfica com credenciais apoiadas por hardware e registros de auditoria de inicialização imutáveis contendo ID do agente, carimbo de data/hora, hash de configuração e parâmetros de inicialização.
 #9.11.2    Nível: 2    Papel: D/V
 Verifique se as transições de estado do agente são assinadas criptograficamente, timestamped e registradas com o contexto completo, incluindo eventos desencadeadores, hash do estado anterior, hash do novo estado e validações de segurança realizadas.
 #9.11.3    Nível: 2    Papel: D/V
 Verifique se os procedimentos de desligamento do agente incluem a limpeza segura de memória usando eliminação criptográfica ou sobrescrição múltipla, revogação de credenciais com notificação da autoridade certificadora e geração de certificados de encerramento à prova de adulteração.
 #9.11.4    Nível: 3    Papel: D/V
 Verifique se os mecanismos de recuperação de agentes validam a integridade do estado usando somas de verificação criptográficas (SHA-256 no mínimo) e retornam a estados conhecidos como bons quando a corrupção é detectada, com alertas automáticos e requisitos de aprovação manual.
 #9.11.5    Nível: 3    Papel: D/V
 Verifique se os mecanismos de persistência do agente criptografam dados sensíveis de estado com chaves AES-256 por agente e implementam rotação segura de chaves em cronogramas configuráveis (máximo de 90 dias) com implantação sem tempo de inatividade.

---

### 9.12 Estrutura de Segurança na Integração de Ferramentas

Controles de segurança para carregamento dinâmico de ferramentas, execução e validação de resultados com processos definidos de avaliação de risco e aprovação.

 #9.12.1    Nível: 1    Papel: D/V
 Verifique se os descritores de ferramenta incluem metadados de segurança especificando privilégios necessários (leitura/gravação/executar), níveis de risco (baixo/médio/alto), limites de recursos (CPU, memória, rede) e requisitos de validação documentados nos manifestos da ferramenta.
 #9.12.2    Nível: 1    Papel: D/V
 Verifique se os resultados da execução da ferramenta são validados em relação aos esquemas esperados (JSON Schema, XML Schema) e às políticas de segurança (sanitização de saída, classificação de dados) antes da integração, com limites de tempo de execução e procedimentos de tratamento de erros.
 #9.12.3    Nível: 2    Papel: D/V
 Verifique se os registros de interação da ferramenta incluem um contexto de segurança detalhado, incluindo uso de privilégios, padrões de acesso a dados, tempo de execução, consumo de recursos e códigos de retorno, com registros estruturados para integração com SIEM.
 #9.12.4    Nível: 2    Papel: D/V
 Verifique se os mecanismos de carregamento dinâmico de ferramentas validam assinaturas digitais usando infraestrutura PKI e implemente protocolos de carregamento seguros com isolamento sandbox e verificação de permissões antes da execução.
 #9.12.5    Nível: 3    Papel: D/V
 Verifique se as avaliações de segurança das ferramentas são acionadas automaticamente para novas versões, incluindo portas de aprovação obrigatórias, análise estática, testes dinâmicos e revisão da equipe de segurança, com critérios de aprovação documentados e requisitos de SLA.

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

## 10 Robustez Adversarial & Defesa de Privacidade

### Objetivo de Controle

Garantir que os modelos de IA permaneçam confiáveis, preservem a privacidade e resistam a abusos ao enfrentar ataques de evasão, inferência, extração ou envenenamento.

---

### 10.1 Alinhamento de Modelo & Segurança

Proteger contra saídas prejudiciais ou que violem políticas.

 #10.1.1    Nível: 1    Papel: D/V
 Verifique se um conjunto de testes de alinhamento (prompts de equipe vermelha, sondas de jailbreak, conteúdo proibido) está sob controle de versão e é executado em cada lançamento de modelo.
 #10.1.2    Nível: 1    Papel: D
 Verifique se as barreiras de recusa e de conclusão segura estão sendo aplicadas.
 #10.1.3    Nível: 2    Papel: D/V
 Verifique se um avaliador automatizado mede a taxa de conteúdo prejudicial e sinaliza regressões além de um limite definido.
 #10.1.4    Nível: 2    Papel: D
 Verifique se o treinamento de counter-jailbreak está documentado e reproduzível.
 #10.1.5    Nível: 3    Papel: V
 Verifique se as provas de conformidade formal de políticas ou monitoramento certificado cobrem domínios críticos.

---

### 10.2 Fortalecimento de Exemplos Adversariais

Aumentar a resistência a entradas manipuladas. O treinamento adversarial robusto e a pontuação de referência são as melhores práticas atuais.

 #10.2.1    Nível: 1    Papel: D
 Verifique se os repositórios do projeto incluem configurações de treinamento adversarial com sementes reproduzíveis.
 #10.2.2    Nível: 2    Papel: D/V
 Verifique se a detecção de exemplos adversários gera alertas de bloqueio nos pipelines de produção.
 #10.2.4    Nível: 3    Papel: V
 Verifique se as provas de robustez certificada ou certificados de limite de intervalo cobrem pelo menos as classes críticas principais.
 #10.2.5    Nível: 3    Papel: V
 Verifique se os testes de regressão usam ataques adaptativos para confirmar que não há perda mensurável de robustez.

---

### 10.3 Mitigação de Inferência de Membro

Limitar a capacidade de decidir se um registro estava nos dados de treinamento. Privacidade diferencial e mascaramento de pontuação de confiança continuam sendo as defesas mais eficazes conhecidas.

 #10.3.1    Nível: 1    Papel: D
 Verifique se a regularização de entropia por consulta ou o escalonamento de temperatura reduz predições excessivamente confiantes.
 #10.3.2    Nível: 2    Papel: D
 Verifique se o treinamento emprega otimização diferencialmente privativa com limite ε para conjuntos de dados sensíveis.
 #10.3.3    Nível: 2    Papel: V
 Verifique se as simulações de ataque (modelo sombra ou caixa preta) mostram uma AUC de ataque ≤ 0,60 nos dados reservados.

---

### 10.4 Resistência à Inversão de Modelo

Prevenir a reconstrução de atributos privados. Pesquisas recentes destacam o truncamento de saída e garantias de DP como defesas práticas.

 #10.4.1    Nível: 1    Papel: D
 Verifique se atributos sensíveis nunca são exibidos diretamente; quando necessário, use buckets ou transformações unidirecionais.
 #10.4.2    Nível: 1    Papel: D/V
 Verifique se os limites de taxa de consulta restringem consultas adaptativas repetidas do mesmo princípio.
 #10.4.3    Nível: 2    Papel: D
 Verifique se o modelo foi treinado com ruído de preservação de privacidade.

---

### 10.5 Defesa contra Extração de Modelo

Detectar e impedir a clonagem não autorizada. É recomendado o uso de marca d'água e análise de padrão de consulta.

 #10.5.1    Nível: 1    Papel: D
 Verifique se os gateways de inferência aplicam limites de taxa globais e por-chave de API ajustados ao limite de memorização do modelo.
 #10.5.2    Nível: 2    Papel: D/V
 Verifique se as estatísticas de query-entropy e input-plurality alimentam um detector de extração automatizada.
 #10.5.3    Nível: 2    Papel: V
 Verifique se marcas d'água frágeis ou probabilísticas podem ser comprovadas com p < 0,01 em até 1 000 consultas contra uma clonagem suspeita.
 #10.5.4    Nível: 3    Papel: D
 Verifique se as chaves de marca d'água e os conjuntos de gatilho estão armazenados em um módulo de segurança de hardware e rotacionados anualmente.
 #10.5.5    Nível: 3    Papel: V
 Verifique se os eventos de alerta de extração incluem consultas ofensivas e estão integrados aos playbooks de resposta a incidentes.

---

### 10.6 Detecção de Dados Envenenados em Tempo de Inferência

Identifique e neutralize entradas com backdoors ou envenenadas.

 #10.6.1    Nível: 1    Papel: D
 Verifique se as entradas passam por um detector de anomalias (por exemplo, STRIP, pontuação de consistência) antes da inferência do modelo.
 #10.6.2    Nível: 1    Papel: V
 Verifique se os limites do detector estão ajustados em conjuntos de validação limpos/contaminados para atingir menos de 5% de falsos positivos.
 #10.6.3    Nível: 2    Papel: D
 Verifique se entradas sinalizadas como envenenadas acionam fluxos de bloqueio suave e revisão humana.
 #10.6.4    Nível: 2    Papel: V
 Verifique se os detectores são submetidos a testes de resistência com ataques de porta traseira adaptativos e sem gatilho.
 #10.6.5    Nível: 3    Papel: D
 Verifique se as métricas de eficácia de detecção são registradas e reavaliadas periodicamente com informações atualizadas sobre ameaças.

---

### 10.7 Adaptação Dinâmica da Política de Segurança

Atualizações de política de segurança em tempo real com base em inteligência de ameaças e análise comportamental.

 #10.7.1    Nível: 1    Papel: D/V
 Verifique se as políticas de segurança podem ser atualizadas dinamicamente sem reiniciar o agente, mantendo a integridade da versão da política.
 #10.7.2    Nível: 2    Papel: D/V
 Verifique se as atualizações da política estão assinadas criptograficamente por pessoal de segurança autorizado e validadas antes da aplicação.
 #10.7.3    Nível: 2    Papel: D/V
 Verifique se as alterações dinâmicas na política são registradas com trilhas de auditoria completas, incluindo justificativa, cadeias de aprovação e procedimentos de reversão.
 #10.7.4    Nível: 3    Papel: D/V
 Verifique se os mecanismos de segurança adaptativa ajustam a sensibilidade da detecção de ameaças com base no contexto de risco e nos padrões comportamentais.
 #10.7.5    Nível: 3    Papel: D/V
 Verifique se as decisões de adaptação de política são explicáveis e incluem trilhas de evidências para revisão da equipe de segurança.

---

### 10.8 Análise de Segurança Baseada em Reflexão

Validação de segurança por meio de autorreflexão do agente e análise metacognitiva.

 #10.8.1    Nível: 1    Papel: D/V
 Verifique se os mecanismos de reflexão do agente incluem autoavaliação voltada à segurança de decisões e ações.
 #10.8.2    Nível: 2    Papel: D/V
 Verifique se as saídas de reflexão são validadas para impedir a manipulação dos mecanismos de autoavaliação por entradas adversárias.
 #10.8.3    Nível: 2    Papel: D/V
 Verifique se a análise de segurança metacognitiva identifica possíveis viés, manipulação ou comprometimento nos processos de raciocínio do agente.
 #10.8.4    Nível: 3    Papel: D/V
 Verifique se os avisos de segurança baseados em reflexão acionam fluxos de trabalho de monitoramento aprimorado e intervenção humana potencial.
 #10.8.5    Nível: 3    Papel: D/V
 Verifique se o aprendizado contínuo a partir de reflexões de segurança melhora a detecção de ameaças sem degradar a funcionalidade legítima.

---

### 10.9 Evolução & Segurança de Autoaperfeiçoamento

Controles de segurança para sistemas de agentes capazes de automodificação e evolução.

 #10.9.1    Nível: 1    Papel: D/V
 Verifique se as capacidades de auto-modificação estão restritas às áreas seguras designadas com limites de verificação formal.
 #10.9.2    Nível: 2    Papel: D/V
 Verifique se as propostas de evolução passam por avaliação de impacto de segurança antes da implementação.
 #10.9.3    Nível: 2    Papel: D/V
 Verifique se os mecanismos de autoaperfeiçoamento incluem capacidades de rollback com verificação de integridade.
 #10.9.4    Nível: 3    Papel: D/V
 Verifique se a segurança de meta-aprendizagem impede a manipulação adversarial dos algoritmos de melhoria.
 #10.9.5    Nível: 3    Papel: D/V
 Verifique se a auto-melhora recursiva está limitada por restrições formais de segurança com provas matemáticas de convergência.

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

## 11 Proteção da Privacidade & Gestão de Dados Pessoais

### Objetivo de Controle

Mantenha garantias rigorosas de privacidade em todo o ciclo de vida da IA—coleta, treinamento, inferência e resposta a incidentes—de modo que os dados pessoais sejam processados apenas com consentimento claro, escopo mínimo necessário, exclusão comprovável e garantias formais de privacidade.

---

### 11.1 Anonimização e Minimização de Dados

 #11.1.1    Nível: 1    Papel: D/V
 Verifique se identificadores diretos e quase-identificadores foram removidos, hashed.
 #11.1.2    Nível: 2    Papel: D/V
 Verifique se as auditorias automatizadas medem k-anonimato/l-diversidade e alertam quando os limites caem abaixo da política.
 #11.1.3    Nível: 2    Papel: V
 Verifique se os relatórios de importância de recursos do modelo demonstram que não há vazamento de identificadores além de ε = 0,01 de informação mútua.
 #11.1.4    Nível: 3    Papel: V
 Verifique se provas formais ou certificação de dados sintéticos mostram risco de re-identificação ≤ 0,05 mesmo sob ataques de ligação.

---

### 11.2 Direito ao Esquecimento e Execução da Exclusão

 #11.2.1    Nível: 1    Papel: D/V
 Verifique se as solicitações de exclusão de sujeitos de dados se propagam para conjuntos de dados brutos, checkpoints, embeddings, logs e backups dentro de acordos de nível de serviço de menos de 30 dias.
 #11.2.2    Nível: 2    Papel: D
 Verifique se as rotinas de "machine-unlearning" treinam fisicamente novamente ou aproximam-se da remoção usando algoritmos de unlearning certificados.
 #11.2.3    Nível: 2    Papel: V
 Verifique se a avaliação do modelo sombra prova que registros esquecidos influenciam menos de 1% das saídas após o desaprendizado.
 #11.2.4    Nível: 3    Papel: V
 Verifique se os eventos de exclusão são registrados de forma imutável e auditável para os reguladores.

---

### 11.3 Medidas de Proteção de Privacidade Diferencial

 #11.3.1    Nível: 2    Papel: D/V
 Verifique se os painéis de monitoramento de rastreamento de perda de privacidade alertam quando o ε acumulado excede os limites da política.
 #11.3.2    Nível: 2    Papel: V
 Verifique se as auditorias de privacidade de caixa-preta estimam ε̂ dentro de 10% do valor declarado.
 #11.3.3    Nível: 3    Papel: V
 Verifique se as provas formais abrangem todas as ajustamentos finos após o treinamento e embeddings.

---

### 11.4 Proteção contra Limitações de Propósito e Desvio de Escopo

 #11.4.1    Nível: 1    Papel: D
 Verifique se todos os conjuntos de dados e pontos de verificação do modelo possuem uma tag de propósito legível por máquina alinhada ao consentimento original.
 #11.4.2    Nível: 1    Papel: D/V
 Verifique se os monitores em tempo de execução detectam consultas incompatíveis com o propósito declarado e acionam a recusa suave.
 #11.4.3    Nível: 3    Papel: D
 Verifique se os gates de policy-as-code impedem a redistribuição de modelos para novos domínios sem revisão DPIA.
 #11.4.4    Nível: 3    Papel: V
 Verifique se as provas formais de rastreabilidade mostram que todo o ciclo de vida dos dados pessoais permanece dentro do escopo consentido.

---

### 11.5 Gestão de Consentimento & Rastreamento de Base Legal

 #11.5.1    Nível: 1    Papel: D/V
 Verifique se uma Plataforma de Gerenciamento de Consentimento (CMP) registra o status de opt-in, finalidade e período de retenção por sujeito de dado.
 #11.5.2    Nível: 2    Papel: D
 Verifique se as APIs expõem tokens de consentimento; os modelos devem validar o escopo do token antes da inferência.
 #11.5.3    Nível: 2    Papel: D/V
 Verifique se o consentimento negado ou retirado interrompe os pipelines de processamento dentro de 24 horas.

---

### 11.6 Aprendizado Federado com Controles de Privacidade

 #11.6.1    Nível: 1    Papel: D
 Verifique se as atualizações do cliente utilizam adição de ruído de privacidade diferencial local antes da agregação.
 #11.6.2    Nível: 2    Papel: D/V
 Verifique se as métricas de treinamento são diferencialmente privativas e nunca revelam a perda de um único cliente.
 #11.6.3    Nível: 2    Papel: V
 Verifique se a agregação resistente a envenenamento (por exemplo, Krum/Média Cortada) está ativada.
 #11.6.4    Nível: 3    Papel: V
 Verifique se as provas formais demonstram o orçamento total de ε com uma perda de utilidade inferior a 5.

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

## Monitoramento, registro e detecção de anomalias C12

### Objetivo de Controle

Esta seção fornece requisitos para oferecer visibilidade em tempo real e forense do que o modelo e outros componentes de IA veem, fazem e retornam, para que ameaças possam ser detectadas, triadas e aprendidas.

### C12.1 Registro de Solicitações e Respostas

 #12.1.1    Nível: 1    Papel: D/V
 Verifique se todos os prompts do usuário e respostas do modelo estão sendo registrados com metadados apropriados (por exemplo, timestamp, ID do usuário, ID da sessão, versão do modelo).
 #12.1.2    Nível: 1    Papel: D/V
 Verifique se os logs estão armazenados em repositórios seguros, controlados por acesso, com políticas de retenção apropriadas e procedimentos de backup.
 #12.1.3    Nível: 1    Papel: D/V
 Verifique se os sistemas de armazenamento de logs implementam criptografia em repouso e em trânsito para proteger informações confidenciais contidas nos logs.
 #12.1.4    Nível: 1    Papel: D/V
 Verifique se os dados confidenciais em prompts e saídas são automaticamente redigidos ou mascarados antes de serem registrados, com regras de redaction configuráveis para PII, credenciais e informações proprietárias.
 #12.1.5    Nível: 2    Papel: D/V
 Verifique se as decisões de política e as ações de filtragem de segurança estão registradas com detalhes suficientes para permitir auditoria e depuração dos sistemas de moderação de conteúdo.
 #12.1.6    Nível: 2    Papel: D/V
 Verifique se a integridade do log está protegida através de, por exemplo, assinaturas criptográficas ou armazenamento somente de escrita.

---

### C12.2 Detecção de Abuso e Alertas

 #12.2.1    Nível: 1    Papel: D/V
 Verifique se o sistema detecta e alerta sobre padrões de jailbreak conhecidos, tentativas de injeção de prompt e entradas adversariais usando detecção baseada em assinatura.
 #12.2.2    Nível: 1    Papel: D/V
 Verifique se o sistema se integra com plataformas de Gerenciamento de Informações e Eventos de Segurança (SIEM) existentes usando formatos de log e protocolos padrão.
 #12.2.3    Nível: 2    Papel: D/V
 Verifique se os eventos de segurança enriquecidos incluem contexto específico de IA, como identificadores de modelo, pontuações de confiança e decisões do filtro de segurança.
 #12.2.4    Nível: 2    Papel: D/V
 Verifique se a detecção de anomalias comportamentais identifica padrões de conversa incomuns, tentativas excessivas de repetição ou comportamentos sistemáticos de sondagem.
 #12.2.5    Nível: 2    Papel: D/V
 Verifique se os mecanismos de alerta em tempo real notificam as equipes de segurança quando possíveis violações de política ou tentativas de ataque são detectadas.
 #12.2.6    Nível: 2    Papel: D/V
 Verifique se regras customizadas estão incluídas para detectar padrões de ameaça específicos de IA, incluindo tentativas coordenadas de jailbreak, campanhas de injeção de prompt e ataques de extração de modelos.
 #12.2.7    Nível: 3    Papel: D/V
 Verifique se os fluxos de trabalho automatizados de resposta a incidentes podem isolar modelos comprometidos, bloquear usuários maliciosos e escalar eventos de segurança críticos.

---

### C12.3 Detecção de Deslocamento de Modelo

 #12.3.1    Nível: 1    Papel: D/V
 Verifique se o sistema acompanha métricas básicas de desempenho, como precisão, pontuações de confiança, latência e taxas de erro ao longo de versões do modelo e períodos de tempo.
 #12.3.2    Nível: 2    Papel: D/V
 Verifique se os alertas automatizados são acionados quando os métricas de desempenho excedem os limites de degradação predefinidos ou divergem significativamente das linhas de base.
 #12.3.3    Nível: 2    Papel: D/V
 Verifique se os monitores de detecção de alucinação identificam e sinalizam casos em que as saídas do modelo contêm informações factualmente incorretas, inconsistentes ou fabricadas.

---

### C12.4 Telemetria de Desempenho & Comportamento

 #12.4.1    Nível: 1    Papel: D/V
 Verifique se as métricas operacionais, incluindo latência de requisição, consumo de tokens, uso de memória e throughput, estão sendo coletadas e monitoradas continuamente.
 #12.4.2    Nível: 1    Papel: D/V
 Verifique se as taxas de sucesso e falha são acompanhadas com categorização dos tipos de erro e suas causas raízes.
 #12.4.3    Nível: 2    Papel: D/V
 Verifique se o monitoramento de utilização de recursos inclui o uso de GPU/CPU, consumo de memória e requisitos de armazenamento, com alertas em caso de violações de limites.

---

### C12.5 Planejamento e Execução de Resposta a Incidentes de IA

 #12.5.1    Nível: 1    Papel: D/V
 Verifique se os planos de resposta a incidentes abordam especificamente eventos de segurança relacionados à IA, incluindo comprometimento de modelo, envenenamento de dados e ataques adversariais.
 #12.5.2    Nível: 2    Papel: D/V
 Verifique se as equipes de resposta a incidentes têm acesso a ferramentas forenses específicas de IA e expertise para investigar o comportamento do modelo e vetores de ataque.
 #12.5.3    Nível: 3    Papel: D/V
 Verifique se a análise pós-incidente inclui considerações para retreinamento do modelo, atualizações de filtros de segurança e integração de lições aprendidas nos controles de segurança.

---

### C12.5 Detecção de Degradação de Desempenho de IA

Monitorar e detectar degradação no desempenho e na qualidade do modelo de IA ao longo do tempo.

 #12.5.1    Nível: 1    Papel: D/V
 Verifique se a precisão do modelo, precisão, recall e pontuações F1 estão continuamente monitoradas e comparadas com os limites de referência.
 #12.5.2    Nível: 1    Papel: D/V
 Verifique se a detecção de deriva de dados monitora mudanças na distribuição de entrada que podem impactar o desempenho do modelo.
 #12.5.3    Nível: 2    Papel: D/V
 Verifique se a detecção de desvio de conceito identifica mudanças na relação entre as entradas e as saídas esperadas.
 #12.5.4    Nível: 2    Papel: D/V
 Verifique se a degradação de desempenho dispara alertas automatizados e inicia fluxos de trabalho de retreinamento ou substituição de modelos.
 #12.5.5    Nível: 3    Papel: V
 Verifique se a análise da causa raiz da degradação correlaciona as quedas de desempenho com mudanças nos dados, problemas de infraestrutura ou fatores externos.

---

### C12.6 Visualização de DAG e Segurança do Fluxo de Trabalho

Proteja os sistemas de visualização de fluxo de trabalho contra vazamento de informações e ataques de manipulação.

 #12.6.1    Nível: 1    Papel: D/V
 Verifique se os dados de visualização DAG são sanitizados para remover informações confidenciais antes do armazenamento ou transmissão.
 #12.6.2    Nível: 1    Papel: D/V
 Verifique se os controles de acesso à visualização do fluxo de trabalho garantem que apenas usuários autorizados possam visualizar os caminhos de decisão do agente e os rastros de raciocínio.
 #12.6.3    Nível: 2    Papel: D/V
 Verifique se a integridade dos dados DAG está protegida por assinaturas criptográficas e mecanismos de armazenamento à prova de adulteração.
 #12.6.4    Nível: 2    Papel: D/V
 Verifique se os sistemas de visualização de fluxo de trabalho implementam validação de entrada para evitar ataques de injeção através de dados manipulados de nó ou aresta.
 #12.6.5    Nível: 3    Papel: D/V
 Verifique se as atualizações em tempo real do DAG estão limitadas em taxa e validadas para impedir ataques de negação de serviço em sistemas de visualização.

---

### C12.7 Monitoramento Proativo de Comportamento de Segurança

Detecção e prevenção de ameaças de segurança por meio da análise proativa do comportamento do agente.

 #12.7.1    Nível: 1    Papel: D/V
 Verifique se os comportamentos proativos de agentes são validados pela segurança antes da execução, com integração à avaliação de riscos.
 #12.7.2    Nível: 2    Papel: D/V
 Verifique se os gatilhos de iniciativa autônoma incluem avaliação do contexto de segurança e análise do panorama de ameaças.
 #12.7.3    Nível: 2    Papel: D/V
 Verifique se os padrões de comportamento proativo são analisados quanto às possíveis implicações de segurança e consequências não intencionais.
 #12.7.4    Nível: 3    Papel: D/V
 Verifique se as ações proativas críticas à segurança exigem cadeias de aprovação explícitas com trilhas de auditoria.
 #12.7.5    Nível: 3    Papel: D/V
 Verifique se a detecção de anomalias comportamentais identifica desvios nos padrões de agentes proativos que possam indicar comprometimento.

---

### Referências

NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3
ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6
EU AI Act — Article 12, 13, 16 and 19 on Logging and Record-keeping

## C13 Supervisão Humana, Responsabilidade e Governança

### Objetivo de Controle

Este capítulo fornece requisitos para a manutenção da supervisão humana e de cadeias de responsabilidade claras em sistemas de IA, garantindo explicabilidade, transparência e gestão ética ao longo de todo o ciclo de vida da IA.

---

### C13.1 Mecanismos de Cancelamento e Sobrescrição

Forneça caminhos de desligamento ou reversão quando comportamento inseguro do sistema de IA for observado.

 #13.1.1    Nível: 1    Papel: D/V
 Verifique se existe um mecanismo manual de interruptor de emergência para interromper imediatamente a inferência e as saídas do modelo de IA.
 #13.1.2    Nível: 1    Papel: D
 Verifique se os controles de substituição são acessíveis apenas a pessoal autorizado.
 #13.1.3    Nível: 3    Papel: D/V
 Verifique se os procedimentos de rollback podem reverter para versões anteriores do modelo ou operações em modo seguro.
 #13.1.4    Nível: 3    Papel: V
 Verifique se os mecanismos de substituição são testados regularmente.

---

### C13.2 Pontos de verificação de decisão com intervenção humana

Exigir aprovações humanas quando as apostas ultrapassarem os limites de risco predefinidos.

 #13.2.1    Nível: 1    Papel: D/V
 Verifique se decisões de IA de alto risco requerem aprovação humana explícita antes da execução.
 #13.2.2    Nível: 1    Papel: D
 Verifique se os limites de risco estão claramente definidos e acionam automaticamente os fluxos de trabalho de revisão humana.
 #13.2.3    Nível: 2    Papel: D
 Verifique se as decisões sensíveis ao tempo possuem procedimentos de contingência quando a aprovação humana não puder ser obtida dentro dos prazos necessários.
 #13.2.4    Nível: 3    Papel: D/V
 Verifique se os procedimentos de escalonamento definem níveis de autoridade claros para diferentes tipos de decisão ou categorias de risco, se aplicável.

---

### C13.3 Cadeia de Responsabilidade & Rastreabilidade

Registrar ações do operador e decisões do modelo.

 #13.3.1    Nível: 1    Papel: D/V
 Verifique se todas as decisões do sistema de IA e intervenções humanas estão registradas com carimbos de data/hora, identidades de usuários e justificativa da decisão.
 #13.3.2    Nível: 2    Papel: D
 Verifique se os registros de auditoria não podem ser adulterados e inclua mecanismos de verificação de integridade.

---

### C13.4 Técnicas de IA Explicável

Importância de recursos superficiais, contra-factuais e explicações locais.

 #13.4.1    Nível: 1    Papel: D/V
 Verifique se os sistemas de IA fornecem explicações básicas para suas decisões em um formato legível para humanos.
 #13.4.2    Nível: 2    Papel: V
 Verifique se a qualidade da explicação é validada por meio de estudos de avaliação humana e métricas.
 #13.4.3    Nível: 3    Papel: D/V
 Verifique se as pontuações de importância de recursos ou métodos de atribuição (SHAP, LIME, etc.) estão disponíveis para decisões críticas.
 #13.4.4    Nível: 3    Papel: V
 Verifique se as explicações contrafactuais mostram como as entradas poderiam ser modificadas para alterar os resultados, se for aplicável ao caso de uso e ao domínio.

---

### C13.5 Cartões de Modelos e Divulgações de Uso

Mantenha os cartões do modelo para uso pretendido, métricas de desempenho e considerações éticas.

 #13.5.1    Nível: 1    Papel: D
 Verifique se os cartões de modelo documentam os casos de uso pretendidos, limitações e modos de falha conhecidos.
 #13.5.2    Nível: 1    Papel: D/V
 Verifique se as métricas de desempenho em diferentes casos de uso aplicáveis foram divulgadas.
 #13.5.3    Nível: 2    Papel: D
 Verifique se as considerações éticas, avaliações de viés, avaliações de justiça, características dos dados de treinamento e limitações conhecidas dos dados de treinamento estão documentadas e atualizadas regularmente.
 #13.5.4    Nível: 2    Papel: D/V
 Verifique se os cartões do modelo estão sob controle de versão e mantidos ao longo do ciclo de vida do modelo com rastreamento de alterações.

---

### C13.6 Quantificação de Incerteza

Propague pontuações de confiança ou medidas de entropia nas respostas.

 #13.6.1    Nível: 1    Papel: D
 Verifique se os sistemas de IA fornecem pontuações de confiança ou medidas de incerteza com seus resultados.
 #13.6.2    Nível: 2    Papel: D/V
 Verifique se os limites de incerteza acionam uma revisão humana adicional ou caminhos de decisão alternativos.
 #13.6.3    Nível: 2    Papel: V
 Verifique se os métodos de quantificação de incerteza estão calibrados e validados contra dados de verdade de solo.
 #13.6.4    Nível: 3    Papel: D/V
 Verifique se a propagação de incerteza é mantida através de fluxos de trabalho de IA de várias etapas.

---

### C13.7 Relatórios de Transparência voltados para o usuário

Forneça divulgações periódicas sobre incidentes, desvio e uso de dados.

 #13.7.1    Nível: 1    Papel: D/V
 Verifique se as políticas de uso de dados e as práticas de gerenciamento de consentimento do usuário estão claramente comunicadas às partes interessadas.
 #13.7.2    Nível: 2    Papel: D/V
 Verifique se as avaliações de impacto de IA são realizadas e os resultados são incluídos nos relatórios.
 #13.7.3    Nível: 2    Papel: D/V
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

Este glossário abrangente fornece definições dos principais termos de IA, ML e segurança utilizados ao longo do AISVS para garantir clareza e compreensão comum.

Exemplo adversarial: Uma entrada deliberadamente elaborada para fazer com que um modelo de IA cometa um erro, muitas vezes adicionando perturbações sutis imperceptíveis aos humanos.
​
Robustez Adversarial – A robustez adversarial em IA refere-se à capacidade de um modelo de manter seu desempenho e resistir a ser enganado ou manipulado por entradas maliciosas intencionalmente criadas para causar erros.
​
Agente – Agentes de IA são sistemas de software que usam IA para perseguir metas e realizar tarefas em nome dos usuários. Eles demonstram raciocínio, planejamento e memória, e possuem um nível de autonomia para tomar decisões, aprender e se adaptar.
​
Inteligência Artificial Agente: sistemas de IA que podem operar com algum grau de autonomia para atingir objetivos, muitas vezes tomando decisões e realizando ações sem intervenção humana direta.
​
Controle de Acesso Baseado em Atributos (ABAC): Um paradigma de controle de acesso onde as decisões de autorização são baseadas em atributos do usuário, recurso, ação e ambiente, avaliados no momento da consulta.
​
Ataque de Porta dos Fundos: um tipo de ataque de envenenamento de dados onde o modelo é treinado para responder de uma maneira específica a determinados gatilhos, enquanto se comporta normalmente de outra forma.
​
Viés: Erros sistemáticos nos resultados do modelo de IA que podem levar a resultados injustos ou discriminatórios para certos grupos ou em contextos específicos.
​
Exploração de Viés: Uma técnica de ataque que aproveita os vieses conhecidos em modelos de IA para manipular resultados ou desfechos.
​
Cedar: linguagem de política da Amazon e mecanismo para permissões detalhadas utilizado na implementação de ABAC para sistemas de IA.
​
Cadeia de Pensamento: Uma técnica para melhorar o raciocínio em modelos de linguagem, gerando etapas intermediárias de raciocínio antes de produzir uma resposta final.
​
Disjuntores: mecanismos que interrompem automaticamente as operações do sistema de IA quando certos limites de risco são ultrapassados.
​
Vazamento de Dados: Exposição não intencional de informações confidenciais através de saídas ou comportamento de modelos de IA.
​
Envenenamento de dados: A corrupção deliberada dos dados de treinamento para comprometer a integridade do modelo, muitas vezes para instalar backdoors ou degradar o desempenho.
​
Privacidade Diferencial – Privacidade diferencial é uma estrutura matematicamente rigorosa para divulgar informações estatísticas sobre conjuntos de dados, ao mesmo tempo em que protege a privacidade dos sujeitos de dados individuais. Ela permite que um detentor de dados compartilhe padrões agregados do grupo, limitando as informações que são vazadas sobre indivíduos específicos.
​
Embeddings: Representações vetoriais densas de dados (texto, imagens, etc.) que capturam o significado semântico em um espaço de alta dimensionalidade.
​
Explicabilidade – Explicabilidade em IA é a capacidade de um sistema de IA fornecer razões compreensíveis por humanos para suas decisões e previsões, oferecendo insights sobre seu funcionamento interno.
​
Inteligência Artificial Explicável (XAI): sistemas de IA projetados para fornecer explicações compreensíveis para humanos sobre suas decisões e comportamentos através de várias técnicas e estruturas.
​
Aprendizado Federado: Uma abordagem de aprendizado de máquina na qual os modelos são treinados em vários dispositivos descentralizados que possuem amostras de dados locais, sem trocar os próprios dados.
​
Guards: Restrições implementadas para impedir que sistemas de IA produzam resultados prejudiciais, tendenciosos ou de outro modo indesejáveis.
​
Alucinação – Uma alucinação de IA refere-se a um fenômeno em que um modelo de IA gera informações incorretas ou enganosas que não têm base em seus dados de treinamento ou na realidade factual.
​
Humano-no-Controle (HITL): Sistemas projetados para exigir supervisão, verificação ou intervenção humana em pontos críticos de decisão.
​
Infraestrutura como Código (IaC): Gerenciamento e provisionamento de infraestrutura por meio de código, em vez de processos manuais, permitindo varredura de segurança e implantações consistentes.
​
Jailbreak: Técnicas usadas para contornar as barreiras de segurança em sistemas de IA, particularmente em modelos de linguagem grande, para produzir conteúdos proibidos.
​
Privilégio Mínimo: O princípio de segurança de conceder apenas os direitos de acesso essenciais mínimos para usuários e processos.
​
LIME (Explicações Locais Interpretáveis de Modelos de Máquinas): Uma técnica para explicar as previsões de qualquer classificador de aprendizado de máquina, aproximando-o localmente com um modelo interpretável.
​
Ataque de Inferência de Membro: Um ataque que visa determinar se um ponto de dado específico foi usado para treinar um modelo de aprendizado de máquina.
​
MITRE ATLAS: Paisagem de Ameaças Adversariais para Sistemas de Inteligência Artificial; uma base de conhecimento de táticas e técnicas adversariais contra sistemas de IA.
​
Model Card – Um model card é um documento que fornece informações padronizadas sobre o desempenho, limitações, usos pretendidos e considerações éticas de um modelo de IA para promover transparência e desenvolvimento responsável de IA.
​
Extração de Modelo: Um ataque onde um adversário consulta repetidamente um modelo-alvo para criar uma cópia funcionalmente similar sem autorização.
​
Inversão de Modelo: Um ataque que tenta reconstruir os dados de treinamento analisando as saídas do modelo.
​
Gerenciamento do Ciclo de Vida do Modelo – O gerenciamento do ciclo de vida de modelos de IA é o processo de supervisionar todas as etapas da existência de um modelo de IA, incluindo seu design, desenvolvimento, implantação, monitoramento, manutenção e eventual aposentadoria, para garantir que ele permaneça eficaz e alinhado com os objetivos.
​
Envenenamento de Modelo: Introdução de vulnerabilidades ou backdoors diretamente em um modelo durante o processo de treinamento.
​
Roubo de Modelo/Model Stealing: Extração de uma cópia ou aproximação de um modelo proprietário por meio de consultas repetidas.
​
Sistema multiagente: Um sistema composto por múltiplos agentes de IA interagindo, cada um com potenciais capacidades e objetivos diferentes.
​
OPA (Open Policy Agent): Um mecanismo de política de código aberto que permite a aplicação unificada de políticas em toda a pilha.
​
Aprendizado de Máquina com Privacidade Preservada (PPML): Técnicas e métodos para treinar e implantar modelos de ML enquanto protegendo a privacidade dos dados de treinamento.
​
Injeção de Prompt: Um ataque onde instruções maliciosas são embutidas nas entradas para sobrepor o comportamento pretendido de um modelo.
​
RAG (Retrieval-Augmented Generation): Uma técnica que aprimora grandes modelos de linguagem ao recuperar informações relevantes de fontes externas de conhecimento antes de gerar uma resposta.
​
Red-Teaming: A prática de testar ativamente sistemas de IA simulando ataques adversariais para identificar vulnerabilidades.
​
SBOM (Software Bill of Materials): Um registro formal que contém os detalhes e as relações da cadeia de suprimentos de vários componentes usados na construção de softwares ou modelos de IA.
​
SHAP (SHapley Additive exPlanations): Uma abordagem teórica de jogos para explicar a saída de qualquer modelo de aprendizado de máquina, calculando a contribuição de cada feature para a previsão.
​
Ataque à cadeia de suprimentos: comprometer um sistema ao direcionar elementos menos seguros na sua cadeia de suprimentos, como bibliotecas de terceiros, conjuntos de dados ou modelos pré-treinados.
​
Transfer Learning: Uma técnica em que um modelo desenvolvido para uma tarefa é reutilizado como ponto de partida para um modelo em uma segunda tarefa.
​
Banco de Dados Vetorial: Um banco de dados especializado projetado para armazenar vetores de alta dimensionalidade ( embeddings) e realizar buscas de similaridade eficientes.
​
Vulnerabilidade de Varredura: Ferramentas automatizadas que identificam vulnerabilidades de segurança conhecidas em componentes de software, incluindo frameworks de IA e dependências.
​
Marca d'água: Técnicas para incorporar marcas imperceptíveis em conteúdo gerado por IA para rastrear sua origem ou detectar geração por IA.
​
Vulnerabilidade Zero-Day: Uma vulnerabilidade anteriormente desconhecida que atacantes podem explorar antes que os desenvolvedores criem e implementem uma correção.

## Apêndice B: Referências

### TODO

## Apêndice C: Governança de Segurança de IA e Documentação

### Objetivo

Este apêndice fornece requisitos fundamentais para estabelecer estruturas organizacionais, políticas e processos para governar a segurança de IA ao longo do ciclo de vida do sistema.

---

### AC.1 Adoção da Estrutura de Gerenciamento de Riscos de IA

Forneça uma estrutura formal para identificar, avaliar e mitigar riscos específicos de IA ao longo do ciclo de vida do sistema.

 #AC.1.1    Nível: 1    Papel: D/V
 Verifique se uma metodologia de avaliação de risco específica para IA está documentada e implementada.
 #AC.1.2    Nível: 2    Papel: D
 Verifique se as avaliações de risco são realizadas em pontos-chave do ciclo de vida da IA e antes de alterações significativas.
 #AC.1.3    Nível: 3    Papel: D/V
 Verifique se a estrutura de gestão de riscos está alinhada com padrões estabelecidos (por exemplo, NIST AI RMF).

---

### AC.2 Política e Procedimentos de Segurança de IA

Defina e aplique padrões organizacionais para o desenvolvimento, implantação e operação segura de IA.

 #AC.2.1    Nível: 1    Papel: D/V
 Verifique se as políticas de segurança de IA documentadas existem.
 #AC.2.2    Nível: 2    Papel: D
 Verifique se as políticas são revisadas e atualizadas pelo menos uma vez por ano e após mudanças significativas no cenário de ameaças.
 #AC.2.3    Nível: 3    Papel: D/V
 Verifique se as políticas abordam todas as categorias AISVS e os requisitos regulatórios aplicáveis.

---

### AC.3 Papéis e Responsabilidades para Segurança de IA

Estabeleça responsabilidade clara pela segurança de IA em toda a organização.

 #AC.3.1    Nível: 1    Papel: D/V
 Verifique se os papéis e responsabilidades de segurança de IA estão documentados.
 #AC.3.2    Nível: 2    Papel: D
 Verifique se os indivíduos responsáveis possuem a expertise adequada em segurança.
 #AC.3.3    Nível: 3    Papel: D/V
 Verifique se um comitê de ética de IA ou conselho de governança foi estabelecido para sistemas de IA de alto risco.

---

### AC.4 Aplicação das Diretrizes de IA Ética

Garantir que os sistemas de IA operem de acordo com os princípios éticos estabelecidos.

 #AC.4.1    Nível: 1    Papel: D/V
 Verifique se diretrizes éticas para o desenvolvimento e a implantação de IA existem.
 #AC.4.2    Nível: 2    Papel: D
 Verifique se existem mecanismos para detectar e relatar violações éticas.
 #AC.4.3    Nível: 3    Papel: D/V
 Verifique se revisões éticas regulares de sistemas de IA implementados são realizadas.

---

### AC.5 Monitoramento de Conformidade Regulamentar de IA

Manter a conscientização e conformidade com a evolução das regulamentações de IA.

 #AC.5.1    Nível: 1    Papel: D/V
 Verifique se existem processos para identificar regulamentações de IA aplicáveis.
 #AC.5.2    Nível: 2    Papel: D
 Verifique se a conformidade com todos os requisitos regulamentares foi avaliada.
 #AC.5.3    Nível: 3    Papel: D/V
 Verifique se as mudanças regulatórias acionam revisões e atualizações oportunas aos sistemas de IA.

### AC.6 Governança, Documentação e Processo de Dados de Treinamento

 #1.1.2    Nível: 1    Papel: D/V
 Verifique se apenas conjuntos de dados avaliados quanto à qualidade, representatividade, origem ética e conformidade com licenças são permitidos, reduzindo os riscos de envenenamento, viés embutido e infração de propriedade intelectual.
 #1.1.5    Nível: 2    Papel: D/V
 Verifique se a qualidade da rotulagem/anotação é garantida por meio de revisões cruzadas de revisores ou consenso.
 #1.1.6    Nível: 2    Papel: D/V
 Verifique se "cartões de dados" ou "folhas de dados para conjuntos de dados" estão mantidos para conjuntos de dados de treinamento significativos, detalhando características, motivações, composição, processos de coleta, pré-processamento e usos recomendados/desaconselhados.
 #1.3.2    Nível: 2    Papel: D/V
 Verifique se os vieses identificados são mitigados por meio de estratégias documentadas, como reequilíbrio, aumento de dados direcionado, ajustes algorítmicos (por exemplo, técnicas de pré-processamento, processamento durante o processamento e pós-processamento) ou reponderação, e se o impacto da mitigação na justiça e no desempenho geral do modelo é avaliado.
 #1.3.3    Nível: 2    Papel: D/V
 Verifique se as métricas de equidade pós-treinamento foram avaliadas e documentadas.
 #1.3.4    Nível: 3    Papel: D/V
 Verifique se uma política de gerenciamento de viés de ciclo de vida atribui proprietários e frequência de revisão.
 #1.4.1    Nível: 2    Papel: D/V
 Verifique se a qualidade da rotulagem/anotação é assegurada por diretrizes claras, verificações cruzadas pelos revisores, mecanismos de consenso (por exemplo, monitoramento do acordo entre anotadores) e processos definidos para resolver discrepâncias.
 #1.4.4    Nível: 3    Papel: D/V
 Verifique se rótulos críticos para segurança, proteção ou justiça (por exemplo, identificação de conteúdo tóxico, descobertas médicas críticas) recebem revisão independente dupla obrigatória ou verificação robusta equivalente.
 #1.4.6    Nível: 2    Papel: D/V
 Verifique se os guias de rotulagem e instruções são abrangentes,controlados por versão e revisados por pares.
 #1.4.6    Nível: 2    Papel: D/V
 Verifique se os esquemas de dados para rótulos estão claramente definidos e sob controle de versão.
 #1.3.1    Nível: 1    Papel: D/V
 Verifique se os conjuntos de dados estão sendo avaliados quanto a desequilíbrios representacionais e possíveis vieses em atributos protegidos legalmente (por exemplo, raça, gênero, idade) e outras características eticamente sensíveis relevantes para o domínio de aplicação do modelo (por exemplo, status socioeconômico, localização).
 #1.5.3    Nível: 2    Papel: V
 Verifique se as verificações manuais aleatórias por especialistas no domínio abrangem uma amostra estatisticamente significativa (por exemplo, ≥1% ou 1.000 amostras, o que for maior, ou conforme determinado pela avaliação de risco) para identificar questões sutis de qualidade não detectadas pela automação.
 #1.8.4    Nível: 2    Papel: D/V
 Verifique se os fluxos de trabalho de rotulagem terceirizados ou crowdsourcing incluem salvaguardas técnicas/procedurais para garantir confidencialidade, integridade dos dados, qualidade das etiquetas e impedir vazamento de dados.
 #1.5.4    Nível: 2    Papel: D/V
 Verifique se as etapas de remediação estão anexadas aos registros de provenance.
 #1.6.2    Nível: 2    Papel: D/V
 Verifique se as amostras marcadas acionam a revisão manual antes do treinamento.
 #1.6.3    Nível: 2    Papel: V
 Verifique se os resultados alimentam o dossiê de segurança do modelo e informam a inteligência de ameaças em andamento.
 #1.6.4    Nível: 3    Papel: D/V
 Verifique se a lógica de detecção foi atualizada com novas informações de ameaças.
 #1.6.5    Nível: 3    Papel: D/V
 Verifique se os pipelines de aprendizado online monitoram o desvio de distribuição.
 #1.7.1    Nível: 1    Papel: D/V
 Verifique se os fluxos de trabalho de exclusão de dados de treinamento eliminam dados primários e derivados e avaliem o impacto no modelo, e se o impacto nos modelos afetados é avaliado e, se necessário, resolvido (por exemplo, por meio de re-treinamento ou recalibração).
 #1.7.2    Nível: 2    Papel: D
 Verifique se mecanismos estão implementados para monitorar e respeitar o escopo e o status do consentimento dos usuários (e retiradas) para os dados utilizados no treinamento, e se o consentimento é validado antes de os dados serem incorporados a novos processos de treinamento ou atualizações significativas do modelo.
 #1.7.3    Nível: 2    Papel: V
 Verifique se os fluxos de trabalho são testados anualmente e registrados.
 #1.8.1    Nível: 2    Papel: D/V
 Verifique se fornecedores de dados de terceiros, incluindo provedores de modelos pré-treinados e conjuntos de dados externos, passam por diligências de segurança, privacidade, sourcedação ética e qualidade de dados antes que seus dados ou modelos sejam integrados.
 #1.8.2    Nível: 1    Papel: D
 Verifique se as transferências externas usam TLS/autenticação e verificações de integridade.
 #1.8.3    Nível: 2    Papel: D/V
 Verifique se fontes de dados de alto risco (por exemplo, conjuntos de dados de código aberto com procedência desconhecida, fornecedores não verificados) recebem uma análise reforçada, como análise em sandbox, verificações extensas de qualidade/bias e detecção direcionada de envenenamento, antes de serem usadas em aplicações sensíveis.
 #1.8.4    Nível: 3    Papel: D/V
 Verifique se os modelos pré-treinados obtidos de terceiros são avaliados quanto a vieses embutidos, possíveis backdoors, integridade de sua arquitetura e a proveniência de seus dados de treinamento originais antes de ajuste fino ou implantação.
 #1.5.3    Nível: 2    Papel: D/V
 Verifique se, caso o treinamento adversarial seja utilizado, a geração, gestão e versionamento dos conjuntos de dados adversariais estão documentados e controlados.
 #1.5.3    Nível: 3    Papel: D/V
 Verifique se o impacto do treinamento de robustez adversarial no desempenho do modelo (contra entradas limpas e adversariais) e nas métricas de equidade foi avaliado, documentado e monitorado.
 #1.5.4    Nível: 3    Papel: D/V
 Verifique se as estratégias de treinamento adversarial e robustez são periodicamente revisadas e atualizadas para combater técnicas evolutivas de ataque adversarial.
 #1.4.2    Nível: 2    Papel: D/V
 Verifique se conjuntos de dados com falha estão em quarentena com registros de auditoria.
 #1.4.3    Nível: 2    Papel: D/V
 Verifique se os portões de qualidade bloqueiam conjuntos de dados abaixo do padrão, a menos que as exceções sejam aprovadas.
 #1.11.2    Nível: 2    Papel: D/V
 Verifique se o processo de geração, os parâmetros e o uso pretendido dos dados sintéticos estão documentados.
 #1.11.3    Nível: 2    Papel: D/V
 Verifique se os dados sintéticos foram avaliados quanto a risco de viés, vazamento de privacidade e questões de representatividade antes do uso no treinamento.
 #1.12.3    Nível: 2    Papel: D/V
 Verifique se os alertas são gerados para eventos de acesso suspeitos e investigados prontamente.
 #1.13.1    Nível: 1    Papel: D/V
 Verifique se períodos de retenção explícitos estão definidos para todos os conjuntos de dados de treinamento.
 #1.13.2    Nível: 2    Papel: D/V
 Verifique se os conjuntos de dados são automaticamente expirados, excluídos ou revisados para exclusão ao final de seu ciclo de vida.
 #1.13.3    Nível: 2    Papel: D/V
 Verifique se as ações de retenção e exclusão são registradas e podem ser auditadas.
 #1.14.1    Nível: 2    Papel: D/V
 Verifique se os requisitos de residência de dados e transferência transfronteiriça estão identificados e aplicados para todos os conjuntos de dados.
 #1.14.2    Nível: 2    Papel: D/V
 Verifique se as regulações específicas do setor (por exemplo, saúde, finanças) são identificadas e abordadas no tratamento dos dados.
 #1.14.3    Nível: 2    Papel: D/V
 Verifique se a conformidade com as leis de privacidade relevantes (por exemplo, GDPR, CCPA) está documentada e revisada regularmente.
 #1.16.1    Nível: 2    Papel: D/V
 Verifique se existem mecanismos para responder às solicitações do titular dos dados de acesso, retificação, restrição ou objeção.
 #1.16.2    Nível: 2    Papel: D/V
 Verifique se as solicitações são registradas, acompanhadas e atendidas dentro dos prazos legalmente exigidos.
 #1.16.3    Nível: 2    Papel: D/V
 Verifique se os processos de direitos do titular dos dados são testados e revisados regularmente para garantir sua eficácia.
 #1.17.1    Nível: 2    Papel: D/V
 Verifique se uma análise de impacto é realizada antes de atualizar ou substituir uma versão do conjunto de dados, abrangendo desempenho do modelo, equidade e conformidade.
 #1.17.2    Nível: 2    Papel: D/V
 Verifique se os resultados da análise de impacto estão documentados e revisados pelos stakeholders relevantes.
 #1.17.3    Nível: 2    Papel: D/V
 Verifique se planos de rollback existem caso novas versões introduzam riscos inaceitáveis ou regressões.
 #1.18.1    Nível: 2    Papel: D/V
 Verifique se todos os funcionários envolvidos na anotação de dados passaram por verificação de antecedentes e receberam treinamento em segurança de dados e privacidade.
 #1.18.2    Nível: 2    Papel: D/V
 Verifique se todos os funcionários de anotação assinaram acordos de confidencialidade e não divulgação.
 #1.18.3    Nível: 2    Papel: D/V
 Verifique se as plataformas de anotação aplicam controles de acesso e monitoram ameaças internas.

#### Referências

NIST AI Risk Management Framework 1.0
ISO/IEC 42001:2023 — AI Management Systems Requirements
ISO/IEC 23894:2023 — Artificial Intelligence — Guidance on Risk Management
EU Artificial Intelligence Act — Regulation (EU) 2024/1689
ISO/IEC 24029‑2:2023 — Robustness of Neural Networks — Methodology for Formal Methods

## Anexo D: Governança e Verificação de Codificação Segura Assistida por IA

### Objetivo

Este capítulo define controles organizacionais básicos para o uso seguro e eficaz de ferramentas de codificação assistidas por IA durante o desenvolvimento de software, garantindo segurança e rastreabilidade ao longo do SDLC.

---

### AD.1 Fluxo de Trabalho de Codificação Segura Assistida por IA

Integre ferramentas de IA no ciclo de desenvolvimento de software seguro (SSDLC) da organização sem enfraquecer os portões de segurança existentes.

 #AD.1.1    Nível: 1    Papel: D/V
 Verifique se um fluxo de trabalho documentado descreve quando e como as ferramentas de IA podem gerar, refatorar ou revisar código.
 #AD.1.2    Nível: 2    Papel: D
 Verifique se o fluxo de trabalho corresponde a cada fase do SSDLC (design, implementação, revisão de código, testes, implantação).
 #AD.1.3    Nível: 3    Papel: D/V
 Verifique se as métricas (por exemplo, densidade de vulnerabilidades, tempo médio para detecção) são coletadas no código produzido por IA e comparadas às referências apenas humanas.

---

### AD.2 Qualificação de Ferramenta de IA e Modelagem de Ameaças

Certifique-se de que as ferramentas de codificação de IA sejam avaliadas quanto às capacidades de segurança, risco e impacto na cadeia de suprimentos antes da adoção.

 #AD.2.1    Nível: 1    Papel: D/V
 Verifique se o modelo de ameaça para cada ferramenta de IA identifica riscos de uso indevido, inversão de modelo, vazamento de dados e cadeia de dependência.
 #AD.2.2    Nível: 2    Papel: D
 Verifique se as avaliações de ferramentas incluem análise estática/dinâmica de quaisquer componentes locais e avaliação dos pontos finais do SaaS (TLS, autenticação/autorização, registro).
 #AD.2.3    Nível: 3    Papel: D/V
 Verifique se as avaliações seguem um framework reconhecido e são refeitas após mudanças principais na versão.

---

### AD.3 Gerenciamento Seguro de Prompt & Contexto

Prevenir o vazamento de segredos, código proprietário e dados pessoais ao construir prompts ou contextos para modelos de IA.

 #AD.3.1    Nível: 1    Papel: D/V
 Verifique se as orientações escritas proíbem o envio de segredos, credenciais ou dados classificados nos prompts.
 #AD.3.2    Nível: 2    Papel: D
 Verifique se os controles técnicos (redação do lado do cliente, filtros de contexto aprovados) removem automaticamente artefatos sensíveis.
 #AD.3.3    Nível: 3    Papel: D/V
 Verifique se os prompts e respostas são tokenizados, criptografados em trânsito e em repouso, e se os prazos de retenção estão em conformidade com a política de classificação de dados.

---

### AD.4 Validação do Código Gerado por IA

Detecte e remedia vulnerabilidades introduzidas pela saída de IA antes que o código seja mesclado ou implantado.

 #AD.4.1    Nível: 1    Papel: D/V
 Verifique se o código gerado por IA está sempre sujeito à revisão humana de código.
 #AD.4.2    Nível: 2    Papel: D
 Verifique se os scanners automatizados (SAST/IAST/DAST) são executados em cada pull request contendo código gerado por IA‑e bloqueie fusões em caso de descobertas críticas.
 #AD.4.3    Nível: 3    Papel: D/V
 Verifique se os testes de fuzzing diferencial ou testes baseados em propriedades provam comportamentos críticos de segurança (por exemplo, validação de entrada, lógica de autorização).

---

### AD.5 Explicabilidade & Rastreabilidade de Sugestões de Código

Forneça aos auditores e desenvolvedores uma visão de por que uma sugestão foi feita e como ela evoluiu.

 #AD.5.1    Nível: 1    Papel: D/V
 Verifique se os pares de prompt/resposta estão registrados com IDs de commit.
 #AD.5.2    Nível: 2    Papel: D
 Verifique se os desenvolvedores podem exibir citações de modelos (trechos de treinamento, documentação) que apoiam uma sugestão.
 #AD.5.3    Nível: 3    Papel: D/V
 Verifique se os relatórios de explicabilidade estão armazenados juntamente com os artefatos de design eReferenciados em avaliações de segurança, atendendo aos princípios de rastreabilidade da ISO/IEC 42001.

---

### AD.6 Feedback Contínuo e Ajuste Fino do Modelo

Melhore o desempenho de segurança do modelo ao longo do tempo, ao mesmo tempo em que evita o desvio negativo.

 #AD.6.1    Nível: 1    Papel: D/V
 Verifique se os desenvolvedores podem marcar sugestões inseguras ou não conformes, e se as marcações são acompanhadas.
 #AD.6.2    Nível: 2    Papel: D
 Verifique se o feedback agregado informa ajustes finos periódicos ou geração aumentada por recuperação com corpora de codificação segura aprovados (por exemplo, OWASP Cheat Sheets).
 #AD.6.3    Nível: 3    Papel: D/V
 Verifique se uma estrutura de avaliação de ciclo fechado executa testes de regressão após cada ajuste fino; métricas de segurança devem atender ou superar as referências anteriores antes da implantação.

---

#### Referências

NIST AI Risk Management Framework 1.0
ISO/IEC 42001:2023 — AI Management Systems Requirements
OWASP Secure Coding Practices — Quick Reference Guide

## Apêndice E: Exemplos de Ferramentas e Estruturas

### Objetivo

Este capítulo fornece exemplos de ferramentas e frameworks que podem apoiar a implementação ou atendimento de um requisito AISVS específico. Estes não devem ser considerados como recomendações ou endossos pela equipe AISVS ou pelo Projeto de Segurança GenAI da OWASP.

---

### AE.1 Governança de Dados de Treinamento & Gestão de Viés

Ferramentas usadas para análise de dados, governança e gerenciamento de viés.

 #AE.1.1    Seção: 1.1
 Ferramenta de Inventário de Dados: Ferramentas de gerenciamento de inventário de dados como...
 #AE.1.2    Seção: 1.2
 Criptografia em Trânsito Use TLS para aplicações baseadas em HTTPS, com ferramentas como openSSL e Python's`ssl`biblioteca.

---

### AE.2 Validação de Entrada do Usuário

Ferramentas para lidar e validar entradas de usuários.

 #AE.2.1    Seção: 2.1
 Ferramentas de Defesa contra Injeção de Prompt: Use ferramentas de proteção como NeMo da NVIDIA ou Guardrails AI.

---

