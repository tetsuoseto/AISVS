## Frontispício

### Sobre o Padrão

O Padrão de Verificação de Segurança da Inteligência Artificial (AISVS) é um catálogo impulsionado pela comunidade de requisitos de segurança que cientistas de dados, engenheiros de MLOps, arquitetos de software, desenvolvedores, testadores, profissionais de segurança, fornecedores de ferramentas, reguladores e consumidores podem usar para projetar, construir, testar e verificar sistemas e aplicações confiáveis habilitados por IA. Ele fornece uma linguagem comum para especificar controles de segurança ao longo do ciclo de vida da IA — desde a coleta de dados e o desenvolvimento de modelos até a implantação e o monitoramento contínuo — para que as organizações possam medir e melhorar a resiliência, a privacidade e a segurança de suas soluções de IA.

### Direitos Autorais e Licença

Versão 0.1 (Primeiro rascunho público - Em andamento), 2025  

![license](images/license.png)
Direitos autorais © 2025 The AISVS Project.  

Lançado sob o Creative Commons Attribution‑ShareAlike 4.0 International License.
Para qualquer reutilização ou distribuição, você deve comunicar claramente os termos de licença desta obra a terceiros.

### Líderes de projeto

Jim Manico
Aras “Russ” Memisyazici

### Contribuidores e Revisores

https://github.com/ottosulin
https://github.com/mbhatt1
https://github.com/vineethsai
https://github.com/cciprofm
https://github.com/deepakrpandey12


---

AISVS é um padrão brand‑new criado especificamente para enfrentar os desafios de segurança únicos de sistemas de inteligência artificial. Embora se inspire nas melhores práticas de segurança mais amplas, cada requisito do AISVS foi desenvolvido do zero para refletir o cenário de ameaças da IA e ajudar as organizações a construir soluções de IA mais seguras e resilientes.

## Prefácio

Bem-vindo ao Padrão de Verificação de Segurança da Inteligência Artificial (AISVS) versão 1.0!

### Introdução

Estabelecido em 2025 por meio de um esforço comunitário colaborativo, AISVS define os requisitos de segurança a considerar ao projetar, desenvolver, implantar e operar modelos modernos de IA, pipelines de IA e serviços habilitados por IA.

AISVS v1.0 representa o trabalho conjunto de seus líderes de projeto, do grupo de trabalho e dos contribuidores da comunidade mais ampla, para produzir uma linha de base pragmática e testável para a segurança de sistemas de IA.

Nosso objetivo com este lançamento é tornar o AISVS fácil de adotar, mantendo o foco‑laser em seu escopo definido e enfrentando o panorama de riscos em rápida evolução, exclusivo para IA.

### Objetivos-chave para AISVS Versão 1.0

A versão 1.0 será criada com vários princípios orientadores.

#### Escopo bem-definido

Cada requisito deve estar alinhado com o nome e a missão do AISVS:

Inteligência Artificial – Os controles operam no nível de IA/ML (dados, modelo, pipeline ou inferência) e são de responsabilidade dos profissionais de IA.
Segurança – Requisitos mitigam diretamente os riscos identificados de segurança, privacidade ou proteção.
Verificação – A linguagem é escrita para que a conformidade possa ser validada de forma objetiva.
Padrão – Seções seguem uma estrutura e terminologia consistentes para formar uma referência coerente.
​
---

Ao seguir o AISVS, as organizações podem avaliar sistematicamente e fortalecer a postura de segurança de suas soluções de IA, promovendo uma cultura de engenharia de IA segura.

## Usando o AISVS

O Padrão de Verificação de Segurança da Inteligência Artificial (AISVS) define os requisitos de segurança para aplicações e serviços de IA modernos, concentrando-se em aspectos sob o controle dos desenvolvedores de aplicações.

O AISVS destina-se a qualquer pessoa que desenvolva ou avalie a segurança de aplicações de IA, incluindo desenvolvedores, arquitetos, engenheiros de segurança e auditores. Este capítulo apresenta a estrutura e o uso do AISVS, incluindo seus níveis de verificação e casos de uso pretendidos.

### Níveis de Verificação de Segurança da Inteligência Artificial

O AISVS define três níveis crescentes de verificação de segurança. Cada nível adiciona profundidade e complexidade, permitindo que as organizações ajustem sua postura de segurança ao nível de risco de seus sistemas de IA.

Organizações podem começar no Nível 1 e adotar progressivamente níveis mais altos à medida que a maturidade de segurança e a exposição a ameaças aumentam.

#### Definição dos Níveis

Cada requisito no AISVS v1.0 é atribuído a um dos seguintes níveis:

 Requisitos do Nível 1

O Nível 1 inclui os requisitos de segurança mais críticos e fundamentais. Eles se concentram em prevenir ataques comuns que não dependem de outras pré-condições ou vulnerabilidades. A maioria dos controles do Nível 1 é fácil de implementar ou suficientemente essencial para justificar o esforço.

 Requisitos do Nível 2

O Nível 2 aborda ataques mais avançados ou menos comuns, bem como defesas em camadas contra ameaças generalizadas. Esses requisitos podem envolver lógica mais complexa ou ter como alvo pré-requisitos de ataque específicos.

 Requisitos do Nível 3

O Nível 3 inclui controles que normalmente são mais difíceis de implementar ou cuja aplicabilidade é situacional. Estes costumam representar mecanismos de defesa em profundidade ou mitigação contra ataques de nicho, direcionados ou de alta complexidade.

#### Função (D/V)

Cada requisito AISVS é marcado de acordo com o público-alvo principal:

D – Requisitos voltados para desenvolvedores
V – Requisitos voltados para verificador/auditor
D/V – Relevante para desenvolvedores e verificadores

## C1 Governança de Dados de Treinamento e Gestão de Viés

### Objetivo de Controle

Os dados de treinamento devem ser obtidos, manuseados e mantidos de forma a preservar a proveniência, a segurança, a qualidade e a imparcialidade. Isso cumpre obrigações legais e reduz os riscos de viés, envenenamento ou violação de privacidade que surgem durante o treinamento e que poderiam afetar todo o ciclo de vida da IA.

---

### C1.1 Proveniência dos Dados de Treinamento

Manter um inventário verificável de todos os conjuntos de dados, aceitar apenas fontes confiáveis e registrar cada alteração para fins de auditabilidade.

 #1.1.1    Nível: 1    Papel: D/V
 Verifique se um inventário atualizado de cada fonte de dados de treinamento (origem, responsável/proprietário, licença, método de coleta, restrições de uso previstas e histórico de processamento) é mantido.
 #1.1.2    Nível: 1    Papel: D/V
 Verifique se os processos de dados de treinamento excluem características, atributos ou campos desnecessários (por exemplo, metadados não utilizados, PII sensível, dados de teste vazados).
 #1.1.3    Nível: 2    Papel: D/V
 Verifique se todas as alterações no conjunto de dados estão sujeitas a um fluxo de aprovação registrado.
 #1.1.4    Nível: 3    Papel: D/V
 Verifique se os conjuntos de dados ou subconjuntos possuem marca d'água ou impressão digital, quando possível.

---

### C1.2 Segurança e Integridade dos Dados de Treinamento

Restringir o acesso aos dados de treinamento, criptografá-los em repouso e em trânsito, e validar sua integridade para evitar adulteração, roubo ou envenenamento de dados.

 #1.2.1    Nível: 1    Papel: D/V
 Verifique se os controles de acesso protegem o armazenamento de dados de treinamento e os pipelines.
 #1.2.2    Nível: 2    Papel: D/V
 Verifique se todo o acesso aos dados de treinamento é registrado, incluindo usuário, horário e ação.
 #1.2.3    Nível: 2    Papel: D/V
 Verifique se os conjuntos de dados de treinamento estão criptografados em trânsito e em repouso, usando algoritmos criptográficos padrão da indústria e práticas de gerenciamento de chaves.
 #1.2.4    Nível: 2    Papel: D/V
 Verifique se hashes criptográficos ou assinaturas digitais são usados para garantir a integridade dos dados durante o armazenamento e a transferência dos dados de treinamento.
 #1.2.5    Nível: 2    Papel: D/V
 Verifique se as técnicas de detecção automatizadas são aplicadas para impedir modificações não autorizadas ou corrupção dos dados de treinamento.
 #1.2.6    Nível: 2    Papel: D/V
 Verifique se os dados de treinamento obsoletos são apagados de forma segura ou anonimizados.
 #1.2.7    Nível: 3    Papel: D/V
 Verifique se todas as versões do conjunto de dados de treinamento são identificadas de forma única, armazenadas de forma imutável e passíveis de auditoria para apoiar a reversão e a análise forense.

---

### C1.3 Qualidade, Integridade e Segurança da Rotulagem de Dados de Treinamento

Proteja os rótulos e exija revisão técnica para dados críticos.

 #1.3.1    Nível: 2    Papel: D/V
 Verifique se funções de hash criptográficas ou assinaturas digitais são aplicadas aos artefatos de rótulo para garantir a integridade e a autenticidade deles.
 #1.3.2    Nível: 2    Papel: D/V
 Verifique se as interfaces de rotulagem e as plataformas de rotulagem implementam controles de acesso robustos, mantêm registros de auditoria à prova de adulteração de todas as atividades de rotulagem e protegem contra modificações não autorizadas.
 #1.3.3    Nível: 3    Papel: D/V
 Verifique se as informações sensíveis nos rótulos estão ocultas, anonimizadas ou criptografadas no nível do campo de dados em repouso e em trânsito.

---

### C1.4 Qualidade dos Dados de Treinamento e Garantia de Segurança

Combine validação automática, verificações manuais pontuais e remediação registrada para garantir a confiabilidade do conjunto de dados.

 #1.4.1    Nível: 1    Papel: D
 Verifique se os testes automatizados capturam erros de formato e valores nulos em cada ingestão de dados ou em transformações de dados significativas.
 #1.4.2    Nível: 2    Papel: D/V
 Verifique se os pipelines de treinamento e ajuste fino de LLM implementam detecção de envenenamento e validação da integridade dos dados (por exemplo, métodos estatísticos, detecção de outliers, análise de embeddings) para identificar ataques de envenenamento potenciais (por exemplo, troca de rótulos, inserção de gatilho de porta dos fundos, comandos de troca de papéis, ataques de instâncias influentes) ou corrupção acidental dos dados de treinamento.
 #1.4.3    Nível: 3    Papel: D/V
 Verifique se defesas apropriadas, como treinamento adversarial (usando exemplos adversariais gerados), aumento de dados com entradas perturbadas ou técnicas de otimização robusta, estão implementadas e ajustadas para os modelos relevantes com base na avaliação de risco.
 #1.4.4    Nível: 2    Papel: D/V
 Verifique se rótulos gerados automaticamente (por exemplo, via Modelos de Linguagem de Grande Porte (LLMs) ou supervisão fraca) estão sujeitos a limiares de confiança e verificações de consistência para detectar alucinações, rótulos enganosos ou de baixa confiança.
 #1.4.5    Nível: 3    Papel: D
 Verifique se os testes automatizados detectam o viés de rótulos em cada ingestão de dados ou em qualquer transformação de dados significativa.

---

### C1.5 Linhagem de Dados e Rastreabilidade

Rastrear a jornada completa de cada ponto de dados, desde a origem até a entrada no modelo, para auditabilidade e resposta a incidentes.

 #1.5.1    Nível: 2    Papel: D/V
 Verifique se a linhagem de cada ponto de dados, incluindo todas as transformações, aumentos de dados e fusões, está registrada e pode ser reconstruída.
 #1.5.2    Nível: 2    Papel: D/V
 Verifique se os registros de linhagem são imutáveis, armazenados com segurança e acessíveis para auditorias.
 #1.5.3    Nível: 2    Papel: D/V
 Verifique se o rastreamento de linhagem inclui dados sintéticos gerados por meio de técnicas de preservação de privacidade ou técnicas gerativas e se todos os dados sintéticos estão claramente rotulados e distinguíveis dos dados reais ao longo de todo o pipeline.

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

## C2 Validação de Entrada do Usuário

### Objetivo de Controle

A validação robusta da entrada do usuário é uma defesa de primeira linha contra alguns dos ataques mais prejudiciais aos sistemas de IA. Ataques de injeção de prompts podem substituir as instruções do sistema, vazar dados sensíveis ou conduzir o modelo a comportamentos que não são permitidos. A menos que filtros dedicados e hierarquias de instrução estejam em vigor, pesquisas mostram que jailbreaks "multi-shot" que exploram janelas de contexto muito longas serão eficazes. Além disso, ataques sutis de perturbação adversarial--tais como trocas de homógrafos ou leetspeak—-podem silenciosamente alterar as decisões de um modelo.

---

### C2.1 Defesa contra Injeção de Prompt

Injeção de prompt é um dos principais riscos para os sistemas de IA. As defesas contra essa tática empregam uma combinação de filtros de padrões estáticos, classificadores dinâmicos e a imposição da hierarquia de instruções.

 #2.1.1    Nível: 1    Papel: D/V
 Verifique se as entradas do usuário são filtradas contra uma biblioteca continuamente atualizada de padrões conhecidos de injeção de prompt (palavras-chave de jailbreak, "ignore previous", cadeias de role-play, ataques HTML/URL indiretos).
 #2.1.2    Nível: 1    Papel: D/V
 Verifique se o sistema impõe uma hierarquia de instruções na qual mensagens do sistema ou do desenvolvedor têm precedência sobre as instruções do usuário, mesmo após a expansão da janela de contexto.
 #2.1.3    Nível: 2    Papel: D/V
 Verifique se os testes de avaliação adversariais (por exemplo, prompts da Equipe Vermelha com muitos exemplos) são executados antes de cada lançamento de modelo ou template de prompt, com limiares de taxa de sucesso e bloqueadores automáticos para regressões.
 #2.1.4    Nível: 2    Papel: D
 Verifique se prompts provenientes de conteúdo de terceiros (páginas da web, PDFs, e-mails) são sanitizados em um contexto de análise isolado antes de serem concatenados ao prompt principal.
 #2.1.5    Nível: 3    Papel: D/V
 Verifique se todas as atualizações das regras de filtro de prompt, as versões dos modelos de classificador e as alterações na lista de bloqueio estão sob controle de versão e auditáveis.

---

### C2.2 Resistência a Exemplos Adversariais

Modelos de Processamento de Linguagem Natural (PLN) ainda são vulneráveis a perturbações sutis em nível de caractere ou de palavra, que os humanos costumam deixar passar, mas os modelos tendem a classificá-las de forma incorreta.

 #2.2.1    Nível: 1    Papel: D
 Verifique se as etapas básicas de normalização de entrada (Unicode NFC, mapeamento de homógrafos, remoção de espaços em branco) são executadas antes da tokenização.
 #2.2.2    Nível: 2    Papel: D/V
 Verifique se a detecção de anomalias estatísticas sinaliza entradas com distância de edição excepcionalmente alta em relação às normas da linguagem, com tokens repetidos em excesso ou distâncias de embedding anormais.
 #2.2.3    Nível: 2    Papel: D
 Verifique se o pipeline de inferência suporta variantes de modelo endurecidas por treinamento adversarial opcionais ou camadas de defesa (por exemplo, randomização, distilação defensiva) para pontos finais de alto risco.
 #2.2.4    Nível: 2    Papel: V
 Verifique se as entradas adversárias suspeitas são colocadas em quarentena, registradas com cargas úteis completas (após a anonimização de PII).
 #2.2.5    Nível: 3    Papel: D/V
 Verifique se as métricas de robustez (taxa de sucesso de conjuntos de ataques conhecidos) são monitoradas ao longo do tempo e se as regressões acionam um bloqueio de liberação.

---

### C2.3 Validação de Esquema, Tipo e Comprimento

Ataques de IA com entradas malformadas ou excessivamente grandes podem causar erros de análise, propagação de prompts entre campos e esgotamento de recursos. A imposição estrita de um esquema também é pré-requisito ao realizar chamadas determinísticas a ferramentas.

 #2.3.1    Nível: 1    Papel: D
 Verifique se cada endpoint de API ou chamada de função define um esquema de entrada explícito (JSON Schema, Protobuf ou equivalente multimodal) e se as entradas são validadas antes da montagem do prompt.
 #2.3.2    Nível: 1    Papel: D/V
 Verifique que as entradas que excedem os limites máximos de tokens ou bytes sejam rejeitadas com um erro seguro e nunca truncadas silenciosamente.
 #2.3.3    Nível: 2    Papel: D/V
 Verifique se as validações de tipo (por exemplo, intervalos numéricos, valores de enum, tipos MIME para imagens/áudio) são aplicadas no lado do servidor, e não apenas no código do cliente.
 #2.3.4    Nível: 2    Papel: D
 Verifique se os validadores semânticos (por exemplo, Esquema JSON) operam em tempo constante para evitar DoS algorítmico.
 #2.3.5    Nível: 3    Papel: V
 Verifique se as falhas de validação são registradas com trechos da carga útil redigidos e códigos de erro inequívocos para auxiliar a triagem de segurança.

---

### C2.4 Triagem de Conteúdo e Políticas

Desenvolvedores devem ser capazes de detectar prompts sintaticamente válidos que solicitam conteúdo proibido (como instruções ilícitas, discurso de ódio e texto protegido por direitos autorais) e, em seguida, impedir que esses prompts se propaguem.

 #2.4.1    Nível: 1    Papel: D
 Verifique se um classificador de conteúdo (zero-shot ou ajustado finamente) atribui pontuações a cada entrada para violência, autolesão, ódio, conteúdo sexual e solicitações ilegais, com limiares configuráveis.
 #2.4.2    Nível: 1    Papel: D/V
 Verifique se as entradas que violem políticas recebem recusas padronizadas ou respostas seguras, para que não se propaguem para chamadas subsequentes de LLM.
 #2.4.3    Nível: 2    Papel: D
 Verifique se o modelo de filtragem ou o conjunto de regras é re-treinado ou atualizado pelo menos a cada trimestre, incorporando padrões recé m-observados de jailbreak ou de contorno de políticas.
 #2.4.4    Nível: 2    Papel: D
 Verifique se a triagem respeita as políticas específicas do usuário (idade, restrições legais regionais) por meio de regras baseadas em atributos resolvidas no momento da solicitação.
 #2.4.5    Nível: 3    Papel: V
 Verifique se os registros de triagem incluem pontuações de confiança do classificador e etiquetas de categorias de políticas de segurança para a correlação com o SOC e o replay futuro da equipe vermelha.

---

### C2.5 Limitação de Taxa de Entrada e Prevenção de Abusos

Os desenvolvedores devem prevenir abusos, esgotamento de recursos e ataques automatizados contra sistemas de IA, limitando as taxas de entrada e detectando padrões de uso anômalos.

 #2.5.1    Nível: 1    Papel: D/V
 Verifique se os limites de taxa por usuário, por IP e por chave de API são aplicados em todos os endpoints de entrada.
 #2.5.2    Nível: 2    Papel: D/V
 Verifique se os limites de taxa de pico e de taxa sustentada estão ajustados para prevenir DoS e ataques de força bruta.
 #2.5.3    Nível: 2    Papel: D/V
 Verifique se padrões de uso anômalos (por exemplo, solicitações em rápida sucessão, inundação de entradas) disparam bloqueios automáticos ou escalonamentos.
 #2.5.4    Nível: 3    Papel: V
 Verifique se os registros de prevenção de abuso são retidos e revisados para padrões de ataque emergentes.

---

### C2.6 Validação de Entrada Multimodal

Sistemas de IA devem incluir validação robusta para entradas não textuais (imagens, áudio, arquivos) para evitar injeção, evasão ou abuso de recursos.

 #2.6.1    Nível: 1    Papel: D
 Verifique se todas as entradas não textuais (imagens, áudio, arquivos) são validadas quanto ao tipo, tamanho e formato antes do processamento.
 #2.6.2    Nível: 2    Papel: D/V
 Verifique se os arquivos são escaneados em busca de malware e de cargas úteis esteganográficas antes da ingestão.
 #2.6.3    Nível: 2    Papel: D/V
 Verifique se as entradas de imagem/áudio são verificadas quanto a perturbações adversariais ou padrões de ataque conhecidos.
 #2.6.4    Nível: 3    Papel: V
 Verifique se as falhas de validação de entrada multimodal são registradas e acionam alertas para investigação.

---

### C2.7 Proveniência de Entrada e Atribuição

Os sistemas de IA devem apoiar auditoria, rastreamento de abusos e conformidade, monitorando e marcando as origens de todas as entradas dos usuários.

 #2.7.1    Nível: 1    Papel: D/V
 Verifique se todas as entradas do usuário são marcadas com metadados (ID do usuário, sessão, origem, carimbo de data/hora, endereço IP) na ingestão.
 #2.7.2    Nível: 2    Papel: D/V
 Verifique se os metadados de proveniência são mantidos e auditáveis para todas as entradas processadas.
 #2.7.3    Nível: 2    Papel: D/V
 Verifique que fontes de entrada anômalas ou não confiáveis sejam sinalizadas e estejam sujeitas a escrutínio aprimorado ou bloqueio.

---

### C2.8 Detecção de Ameaças Adaptativas em Tempo-Real

Os desenvolvedores devem empregar sistemas avançados de detecção de ameaças para IA que se adaptem a novos padrões de ataque e forneçam proteção em tempo-real com correspondência de padrões compilados.

 #2.8.1    Nível: 1    Papel: D/V
 Verifique se os padrões de detecção de ameaças são compilados em motores de regex otimizados para filtragem em tempo real de alto desempenho, com impacto de latência mínimo.
 #2.8.2    Nível: 1    Papel: D/V
 Verifique se os sistemas de detecção de ameaças mantêm bibliotecas de padrões separadas para diferentes categorias de ameaça (injeção de prompt, conteúdo nocivo, dados sensíveis, comandos do sistema).
 #2.8.3    Nível: 2    Papel: D/V
 Verifique se a detecção adaptativa de ameaças incorpora modelos de aprendizado de máquina que atualizam a sensibilidade às ameaças com base na frequência de ataques e nas taxas de sucesso.
 #2.8.4    Nível: 2    Papel: D/V
 Verifique se feeds de inteligência de ameaças em tempo real atualizam automaticamente as bibliotecas de padrões com novas assinaturas de ataque e IOCs (Indicadores de Comprometimento).
 #2.8.5    Nível: 3    Papel: D/V
 Verifique se as taxas de falsos positivos na detecção de ameaças são monitoradas continuamente e se a especificidade dos padrões é ajustada automaticamente para minimizar a interferência em casos de uso legítimos.
 #2.8.6    Nível: 3    Papel: D/V
 Verifique se a análise contextual de ameaças considera a fonte de entrada, padrões de comportamento do usuário e o histórico da sessão para melhorar a precisão da detecção.
 #2.8.7    Nível: 3    Papel: D/V
 Verifique se as métricas de desempenho da detecção de ameaças (taxa de detecção, latência de processamento, utilização de recursos) são monitoradas e otimizadas em tempo real.

---

### C2.9 Pipeline de Validação de Segurança Multimodal

Os desenvolvedores devem fornecer validação de segurança para entradas de texto, imagem, áudio e outras modalidades de IA, com tipos específicos de detecção de ameaças e isolamento de recursos.

 #2.9.1    Nível: 1    Papel: D/V
 Verifique se cada modalidade de entrada possui validadores de segurança dedicados com padrões de ameaça documentados (texto: injeção de prompt, imagens: esteganografia, áudio: ataques por espectrograma) e limiares de detecção.
 #2.9.2    Nível: 2    Papel: D/V
 Verifique se as entradas multimodais são processadas em caixas de areia isoladas com limites de recursos definidos (memória, CPU, tempo de processamento) específicos para cada tipo de modalidade e documentadas nas políticas de segurança.
 #2.9.3    Nível: 2    Papel: D/V
 Verifique que a detecção de ataques multimodais identifique ataques coordenados que abrangem múltiplos tipos de entrada (por exemplo, payloads esteganográficos em imagens, combinados com injecção de prompt em texto) com regras de correlação e geração de alertas.
 #2.9.4    Nível: 3    Papel: D/V
 Verifique se as falhas de validação multimodais geram registros detalhados, incluindo todas as modalidades de entrada, resultados da validação, pontuações de ameaça e análise de correlação, com formatos de log estruturados para integração com SIEM.
 #2.9.5    Nível: 3    Papel: D/V
 Verifique se os classificadores de conteúdo específicos por modalidade são atualizados de acordo com cronogramas documentados (no mínimo trimestralmente), com novos padrões de ameaça, exemplos adversariais e benchmarks de desempenho mantidos acima dos limiares de referência.

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

## C3 Gerenciamento do Ciclo de Vida do Modelo e Controle de Mudanças

### Objetivo de Controle

Os sistemas de IA devem implementar processos de controle de alterações que impeçam modificações do modelo não autorizadas ou inseguras de chegarem à produção. Esse controle garante a integridade do modelo ao longo de todo o ciclo de vida--desde o desenvolvimento até a implantação até o descomissionamento--o que permite uma resposta rápida a incidentes e mantém a responsabilidade por todas as mudanças.

Objetivo de Segurança Central: Apenas modelos autorizados e validados chegam à produção, empregando processos controlados que mantenham integridade, rastreabilidade e recuperabilidade.

---

### C3.1 Autorização e Integridade do Modelo

Apenas modelos autorizados com integridade verificada chegam aos ambientes de produção.

 #3.1.1    Nível: 1    Papel: D/V
 Verifique se todos os artefatos do modelo (pesos, configurações, tokenizadores) são assinados criptograficamente por entidades autorizadas antes da implantação.
 #3.1.2    Nível: 1    Papel: D/V
 Verifique que a integridade do modelo seja validada no momento da implantação e que as falhas na verificação da assinatura impeçam o carregamento do modelo.
 #3.1.3    Nível: 2    Papel: D/V
 Verifique se os registros de proveniência do modelo incluem a identidade da entidade autorizadora, os checksums dos dados de treinamento, os resultados dos testes de validação com o status aprovado/reprovado e um carimbo de data/hora de criação.
 #3.1.4    Nível: 2    Papel: D/V
 Verifique se todos os artefatos do modelo utilizam versionamento semântico (MAJOR.MINOR.PATCH) com critérios documentados que especificam quando cada componente da versão é incrementado.
 #3.1.5    Nível: 2    Papel: V
 Verifique se o rastreamento de dependências mantém um inventário em tempo real que permita a identificação rápida de todos os sistemas que consomem.

---

### C3.2 Validação e Testes de Modelo

Os modelos devem passar pelas validações de segurança e conformidade definidas antes da implantação.

 #3.2.1    Nível: 1    Papel: D/V
 Verifique se os modelos passam por testes de segurança automatizados que incluem validação de entrada, sanitização de saída e avaliações de segurança, com limiares de aprovação/reprovação previamente acordados pela organização antes da implantação.
 #3.2.2    Nível: 1    Papel: D/V
 Verifique que as falhas de validação bloqueiem automaticamente a implantação do modelo após aprovação explícita de substituição por parte de pessoal autorizado pré-designado, com justificativas comerciais documentadas.
 #3.2.3    Nível: 2    Papel: V
 Verifique se os resultados dos testes são assinados criptograficamente e vinculados de forma imutável ao hash da versão específica do modelo que está sendo validada.
 #3.2.4    Nível: 2    Papel: D/V
 Verifique se as implantações emergenciais exigem avaliação de risco de segurança documentada e aprovação de uma autoridade de segurança previamente designada dentro de prazos previamente acordados.

---

### C3.3 Implantação Controlada e Reversão

As implantações de modelos devem ser controladas, monitoradas e reversíveis.

 #3.3.1    Nível: 1    Papel: D
 Verifique se as implantações em produção implementam mecanismos de lançamento gradual (canary deployments, blue-green deployments) com gatilhos automáticos de reversão baseados em taxas de erro acordadas previamente, limites de latência ou critérios de alertas de segurança.
 #3.3.2    Nível: 1    Papel: D/V
 Verifique se as capacidades de reversão restauram o estado completo do modelo (pesos, configurações, dependências) de forma atômica dentro de janelas de tempo organizacionais pré-definidas.
 #3.3.3    Nível: 2    Papel: D/V
 Verifique se os processos de implantação validam assinaturas criptográficas e calculam somas de verificação de integridade antes da ativação do modelo, falhando a implantação em caso de qualquer discrepância.
 #3.3.4    Nível: 2    Papel: D/V
 Verifique se as capacidades de desligamento de emergência do modelo podem desativar os endpoints do modelo dentro de tempos de resposta predefinidos, por meio de disjuntores automáticos ou interruptores manuais de desligamento.
 #3.3.5    Nível: 2    Papel: V
 Verifique se os artefatos de rollback (versões anteriores do modelo, configurações, dependências) são retidos de acordo com as políticas organizacionais, com armazenamento imutável para resposta a incidentes.

---

### C3.4 Responsabilização de Mudanças e Auditoria

Todas as alterações no ciclo de vida do modelo devem ser rastreáveis e auditáveis.

 #3.4.1    Nível: 1    Papel: V
 Verifique se todas as alterações de modelo (implantação, configuração, desativação) geram registros de auditoria imutáveis, incluindo um carimbo de data/hora, uma identidade de ator autenticado, um tipo de alteração e estados anterior e posterior.
 #3.4.2    Nível: 2    Papel: D/V
 Verifique se o acesso ao registro de auditoria requer autorização apropriada e se todas as tentativas de acesso são registradas com a identidade do usuário e um carimbo de data/hora.
 #3.4.3    Nível: 2    Papel: D/V
 Verifique que os modelos de prompt e as mensagens do sistema estejam sob controle de versão em repositórios Git, com revisão de código obrigatória e aprovação dos revisores designados antes da implantação.
 #3.4.4    Nível: 2    Papel: V
 Verifique se os registros de auditoria contêm detalhes suficientes (hashes do modelo, instantâneos de configuração, versões de dependências) para permitir a reconstrução completa do estado do modelo para qualquer carimbo de data/hora dentro do período de retenção.

---

### C3.5 Práticas de Desenvolvimento Seguro

Os processos de desenvolvimento e treinamento de modelos devem seguir práticas seguras para evitar comprometimento.

 #3.5.1    Nível: 1    Papel: D
 Verifique se os ambientes de desenvolvimento, teste e produção do modelo estão fisicamente ou logicamente separados. Eles não compartilham infraestrutura, possuem controles de acesso distintos e bancos de dados isolados.
 #3.5.2    Nível: 1    Papel: D
 Verifique se o treinamento do modelo e o ajuste fino ocorrem em ambientes isolados com acesso à rede controlado.
 #3.5.3    Nível: 1    Papel: D/V
 Verifique se as fontes de dados de treinamento são validadas por meio de verificações de integridade e autenticadas por fontes confiáveis com cadeia de custódia documentada antes de serem utilizadas no desenvolvimento do modelo.
 #3.5.4    Nível: 2    Papel: D
 Verifique se os artefatos de desenvolvimento de modelos (hiperparâmetros, scripts de treinamento, arquivos de configuração) estão armazenados no controle de versão e exigem aprovação por revisão por pares antes de serem usados no treinamento.

---

### C3.6 Aposentadoria de Modelos e Descomissionamento

Os modelos devem ser descomissionados com segurança quando não forem mais necessários ou quando questões de segurança forem identificadas.

 #3.6.1    Nível: 1    Papel: D
 Verifique se os processos de desativação de modelos escaneiam automaticamente grafos de dependência, identificam todos os sistemas que consomem o modelo e fornecem períodos de aviso prévio acordados antes do descomissionamento.
 #3.6.2    Nível: 1    Papel: D/V
 Verifique se artefatos de modelos aposentados são apagados com segurança usando apagamento criptográfico ou sobrescrita em várias passadas, de acordo com as políticas documentadas de retenção de dados, com certificados de destruição verificados.
 #3.6.3    Nível: 2    Papel: V
 Verifique se os eventos de retirada de modelos são registrados com carimbo de data/hora e com a identidade do ator, e se as assinaturas do modelo são revogadas para impedir a reutilização.
 #3.6.4    Nível: 2    Papel: D/V
 Verifique se a retirada de emergência do modelo pode desativar o acesso ao modelo dentro dos prazos de resposta a emergências pré-estabelecidos, por meio de interruptores automáticos de desligamento, caso vulnerabilidades críticas de segurança sejam descobertas.

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

## C4 Infraestrutura, Configuração & Segurança de Implantação

### Objetivo de Controle

Infraestrutura de IA deve ser endurecida contra elevação de privilégios, adulteração da cadeia de suprimentos e movimentação lateral por meio de configuração segura, isolamento em tempo de execução, pipelines de implantação confiáveis e monitoramento abrangente. Somente componentes de infraestrutura autorizados e validados, bem como configurações, chegam à produção por meio de processos controlados que mantêm a segurança, a integridade e a auditabilidade.

Objetivo de Segurança Central: Somente componentes de infraestrutura assinados criptograficamente e escaneados em busca de vulnerabilidades chegam ao ambiente de produção por meio de pipelines de validação automatizados, que impõem políticas de segurança e mantêm registros de auditoria imutáveis.

---

### C4.1 Isolamento do Ambiente de Execução

Prevenir fugas de contêineres e escalonamento de privilégios por meio de primitivas de isolamento em nível de kernel e controles de acesso obrigatórios.

 #4.1.1    Nível: 1    Papel: D/V
 Verifique se todos os contêineres de IA descartam todas as capacidades do Linux, exceto CAP_SETUID, CAP_SETGID e as capacidades exigidas explicitamente documentadas nos referenciais de segurança.
 #4.1.2    Nível: 1    Papel: D/V
 Verifique se os perfis seccomp bloqueiam todas as chamadas de sistema, exceto aquelas em listas de permissões pré-aprovadas, com violações encerrando o contêiner e gerando alertas de segurança.
 #4.1.3    Nível: 2    Papel: D/V
 Verifique se as cargas de trabalho de IA são executadas com sistemas de arquivos raiz somente leitura, tmpfs para dados temporários e volumes nomeados para dados persistentes, com opções de montagem noexec aplicadas.
 #4.1.4    Nível: 2    Papel: D/V
 Verifique se o monitoramento em tempo de execução baseado em eBPF (Falco, Tetragon ou equivalente) detecta tentativas de elevação de privilégios e encerra automaticamente os processos que violam as políticas de segurança dentro dos requisitos de tempo de resposta da organização.
 #4.1.5    Nível: 3    Papel: D/V
 Verifique se as cargas de trabalho de IA de alto risco são executadas em ambientes isolados por hardware (Intel TXT, AMD SVM ou nós bare-metal dedicados) com verificação de atestação.

---

### C4.2 Pipelines de Build e Implantação Seguros

Garanta a integridade criptográfica e a segurança da cadeia de suprimentos por meio de builds reprodutíveis e artefatos assinados.

 #4.2.1    Nível: 1    Papel: D/V
 Verifique se a infraestrutura como código é verificada com as ferramentas (tfsec, Checkov ou Terrascan) em cada commit, bloqueando merges com descobertas de severidade CRITICAL ou HIGH.
 #4.2.2    Nível: 1    Papel: D/V
 Verificar que as construções de contêiner são reproduzíveis com hashes SHA256 idênticos entre as construções e gerar atestações de proveniência SLSA Nível 3 assinadas com Sigstore.
 #4.2.3    Nível: 2    Papel: D/V
 Verifique se as imagens de contêiner incorporam SBOMs CycloneDX ou SPDX e são assinadas com Cosign antes do push para o registro, com imagens não assinadas rejeitadas na implantação.
 #4.2.4    Nível: 2    Papel: D/V
 Verifique se as pipelines de CI/CD utilizam tokens OIDC do HashiCorp Vault, papéis IAM da AWS ou Identidade Gerenciada do Azure, com durações que não excedam os limites da política de segurança da organização.
 #4.2.5    Nível: 2    Papel: D/V
 Verifique se as assinaturas Cosign e a proveniência SLSA são validadas durante o processo de implantação antes da execução do contêiner e se os erros de verificação causam a falha da implantação.
 #4.2.6    Nível: 2    Papel: D/V
 Verifique se os ambientes de build são executados em containers efêmeros ou VMs sem armazenamento persistente e com isolamento de rede em relação às VPCs de produção.

---

### C4.3 Segurança de Rede e Controle de Acesso

Implemente a rede zero-trust com políticas de negação padrão e comunicações criptografadas.

 #4.3.1    Nível: 1    Papel: D/V
 Verifique se as Políticas de Rede do Kubernetes, ou qualquer equivalente, implementam a negação padrão de tráfego de entrada/saída com regras explícitas de permissão para as portas necessárias (443, 8080, etc.).
 #4.3.2    Nível: 1    Papel: D/V
 Verifique se o SSH (porta 22), RDP (porta 3389) e os endpoints de metadados da nuvem (169.254.169.254) estão bloqueados ou exigem autenticação baseada em certificado.
 #4.3.3    Nível: 2    Papel: D/V
 Verifique se o tráfego de saída é filtrado por proxies HTTP/HTTPS (Squid, Istio ou gateways NAT na nuvem) com listas de domínios permitidos e requisições bloqueadas registradas.
 #4.3.4    Nível: 2    Papel: D/V
 Verifique se a comunicação entre serviços utiliza TLS com autenticação mútua, com certificados rotacionados de acordo com a política organizacional e validação de certificados aplicada (sem flags de skip-verify).
 #4.3.5    Nível: 2    Papel: D/V
 Verifique se a infraestrutura de IA opera em VPCs/VNets dedicadas, sem acesso direto à Internet, e se comunica apenas por meio de gateways NAT ou hosts Bastion.

---

### C4.4 Segredos e Gerenciamento de Chaves Criptográficas

Proteja credenciais por meio de armazenamento protegido por hardware e rotação automatizada de credenciais com acesso zero-trust.

 #4.4.1    Nível: 1    Papel: D/V
 Verifique se os segredos estão armazenados no HashiCorp Vault, AWS Secrets Manager, Azure Key Vault ou Google Secret Manager, com criptografia em repouso usando AES-256.
 #4.4.2    Nível: 1    Papel: D/V
 Verifique se as chaves criptográficas são geradas em HSMs FIPS 140-2 Nível 2 (AWS CloudHSM, Azure Dedicated HSM) com rotação de chaves de acordo com a política criptográfica organizacional.
 #4.4.3    Nível: 2    Papel: D/V
 Verifique se a rotação de segredos é automatizada com implantação sem tempo de inatividade e rotação imediata acionada por mudanças de pessoal ou incidentes de segurança.
 #4.4.4    Nível: 2    Papel: D/V
 Verifique se as imagens de contêiner são escaneadas com ferramentas (GitLeaks, TruffleHog ou detect-secrets) bloqueando builds que contenham chaves de API, senhas ou certificados.
 #4.4.5    Nível: 2    Papel: D/V
 Verifique se o acesso a segredos de produção exige autenticação multifator (MFA) com tokens de hardware (YubiKey, FIDO2) e é registrado por logs de auditoria imutáveis com identidades de usuário e carimbos de tempo.
 #4.4.6    Nível: 2    Papel: D/V
 Verifique se os segredos são injetados por meio de segredos do Kubernetes, volumes montados ou contêineres de inicialização e assegure-se de que os segredos nunca fiquem embutidos em variáveis de ambiente ou em imagens.

---

### C4.5 Isolamento de Cargas de Trabalho de IA e Validação

Isole modelos de IA não confiáveis em caixas de areia seguras com análise comportamental abrangente.

 #4.5.1    Nível: 1    Papel: D/V
 Verifique se modelos de IA externos são executados em gVisor, microVMs (como Firecracker, CrossVM) ou contêineres Docker com as opções --security-opt=no-new-privileges e --read-only.
 #4.5.2    Nível: 1    Papel: D/V
 Verifique se os ambientes sandbox não possuem conectividade de rede (--network=none) ou apenas acesso ao localhost, com todas as requisições externas bloqueadas por regras do iptables.
 #4.5.3    Nível: 2    Papel: D/V
 Verifique se a validação do modelo de IA inclui testes automatizados de equipe vermelha com cobertura de testes definida pela organização e análise comportamental para detecção de backdoors.
 #4.5.4    Nível: 2    Papel: D/V
 Verifique que, antes que um modelo de IA seja promovido à produção, seus resultados do ambiente sandbox sejam assinados criptograficamente por pessoal de segurança autorizado e armazenados em logs de auditoria imutáveis.
 #4.5.5    Nível: 2    Papel: D/V
 Verifique se os ambientes sandbox são destruídos e recriados a partir de imagens douradas entre as avaliações, com limpeza completa do sistema de arquivos e da memória.

---

### C4.6 Monitoramento da Segurança da Infraestrutura

Varrer e monitorar continuamente a infraestrutura com remediação automatizada e alertas em tempo real.

 #4.6.1    Nível: 1    Papel: D/V
 Verifique se as imagens de contêiner são escaneadas de acordo com os cronogramas da organização, com vulnerabilidades CRÍTICAS bloqueando a implantação com base nos limiares de risco da organização.
 #4.6.2    Nível: 1    Papel: D/V
 Verifique se a infraestrutura atende aos CIS Benchmarks ou aos controles NIST 800-53, com limites de conformidade definidos pela organização e remediação automatizada para verificações com falha.
 #4.6.3    Nível: 2    Papel: D/V
 Verifique se as vulnerabilidades de gravidade ALTA são corrigidas de acordo com os prazos de gestão de riscos organizacionais, com procedimentos de emergência para CVEs explorados ativamente.
 #4.6.4    Nível: 2    Papel: V
 Verifique se os alertas de segurança se integram com as plataformas SIEM (Splunk, Elastic ou Sentinel) usando os formatos CEF ou STIX/TAXII com enriquecimento automatizado.
 #4.6.5    Nível: 3    Papel: V
 Verifique se as métricas de infraestrutura são exportadas para sistemas de monitoramento (Prometheus, DataDog) com painéis de SLA e relatórios executivos.
 #4.6.6    Nível: 2    Papel: D/V
 Verifique se a deriva de configuração é detectada usando ferramentas (Chef InSpec, AWS Config) de acordo com os requisitos de monitoramento da organização, com rollback automático para alterações não autorizadas.

---

### C4.7 Gerenciamento de Recursos de Infraestrutura de IA

Prevenir ataques de esgotamento de recursos e garantir uma alocação justa de recursos por meio de cotas e monitoramento.

 #4.7.1    Nível: 1    Papel: D/V
 Verifique se a utilização de GPU/TPU é monitorada com alertas disparados em limiares definidos pela organização e se o dimensionamento automático ou o balanceamento de carga é ativado com base em políticas de gerenciamento de capacidade.
 #4.7.2    Nível: 1    Papel: D/V
 Verifique se as métricas de carga de trabalho de IA (latência de inferência, taxa de processamento, taxas de erro) são coletadas de acordo com os requisitos de monitoramento da organização e correlacionadas com a utilização da infraestrutura.
 #4.7.3    Nível: 2    Papel: D/V
 Verifique se as quotas de recursos do Kubernetes, ou equivalente, limitam cargas de trabalho individuais de acordo com as políticas organizacionais de alocação de recursos, com limites rígidos aplicados.
 #4.7.4    Nível: 2    Papel: V
 Verifique se o monitoramento de custos rastreia os gastos por carga de trabalho/locatário, com alertas baseados em limites orçamentários organizacionais e controles automatizados para estouros de orçamento.
 #4.7.5    Nível: 3    Papel: V
 Verifique se o planejamento de capacidade utiliza dados históricos com períodos de previsão definidos pela organização e provisionamento automático de recursos com base em padrões de demanda.
 #4.7.6    Nível: 2    Papel: D/V
 Verifique se a exaustão de recursos aciona circuit breakers de acordo com os requisitos de resposta da organização, incluindo limitação de taxa com base em políticas de capacidade e isolamento de cargas de trabalho.

---

### C4.8 Separação de Ambientes e Controles de Promoção

Impor limites estritos entre ambientes com portões de promoção automatizados e validação de segurança.

 #4.8.1    Nível: 1    Papel: D/V
 Verifique se os ambientes de dev/test/prod operam em VPCs/VNets separadas, sem funções IAM compartilhadas, grupos de segurança ou conectividade de rede.
 #4.8.2    Nível: 1    Papel: D/V
 Verifique se a promoção do ambiente requer aprovação do pessoal autorizado definido pela organização, com assinaturas criptográficas e registros de auditoria imutáveis.
 #4.8.3    Nível: 2    Papel: D/V
 Verifique se os ambientes de produção bloqueiam o acesso SSH, desative endpoints de depuração e exija solicitações de mudança com requisitos de aviso prévio organizacionais, exceto em emergências.
 #4.8.4    Nível: 2    Papel: D/V
 Verifique se as alterações de infraestrutura como código exigem revisão por pares com testes automatizados e varredura de segurança antes de mesclar para a ramificação principal.
 #4.8.5    Nível: 2    Papel: D/V
 Verifique se os dados de não produção estão anonimizados de acordo com os requisitos de privacidade da organização, geração de dados sintéticos ou mascaramento completo de dados com remoção de PII verificada.
 #4.8.6    Nível: 2    Papel: D/V
 Verifique se os gates de promoção incluem testes de segurança automatizados (SAST, DAST, varredura de contêineres) com zero achados CRÍTICOS exigidos para aprovação.

---

### C4.9 Backup e Recuperação de Infraestrutura

Garantir a resiliência da infraestrutura por meio de backups automatizados, procedimentos de recuperação testados e capacidades de recuperação de desastres.

 #4.9.1    Nível: 1    Papel: D/V
 Verifique se as configurações de infraestrutura são copiadas de acordo com os cronogramas organizacionais de backup para regiões geograficamente separadas, com a implementação da estratégia de backup 3-2-1.
 #4.9.2    Nível: 2    Papel: D/V
 Verifique se os sistemas de backup operam em redes isoladas, com credenciais separadas e armazenamento isolado da rede para proteção contra ransomware.
 #4.9.3    Nível: 2    Papel: V
 Verifique se os procedimentos de recuperação são testados e validados por meio de testes automatizados, de acordo com os cronogramas organizacionais, com metas de RTO e RPO que atendem aos requisitos organizacionais.
 #4.9.4    Nível: 3    Papel: V
 Verifique se a recuperação de desastres inclui runbooks específicos de IA com restauração dos pesos do modelo, reconstrução do cluster de GPU e mapeamento de dependências de serviços.

---

### C4.10 Conformidade e Governança de Infraestrutura

Manter a conformidade regulatória por meio de avaliação contínua, documentação e controles automatizados.

 #4.10.1    Nível: 2    Papel: D/V
 Verifique se a conformidade da infraestrutura está sendo avaliada de acordo com os cronogramas organizacionais em relação aos controles SOC 2, ISO 27001 ou FedRAMP, com coleta automatizada de evidências.
 #4.10.2    Nível: 2    Papel: V
 Verifique se a documentação de infraestrutura inclui diagramas de rede, mapas de fluxo de dados e modelos de ameaças atualizados de acordo com os requisitos de gestão de mudanças organizacionais.
 #4.10.3    Nível: 3    Papel: D/V
 Verifique se as alterações de infraestrutura passam por uma avaliação automatizada de impacto de conformidade com fluxos de aprovação regulatória para modificações de alto risco.

---

### C4.11 Segurança de Hardware de IA

Garanta componentes de hardware específicos para IA, incluindo GPUs, TPUs e aceleradores de IA especializados.

 #4.11.1    Nível: 2    Papel: D/V
 Verifique se o firmware do acelerador de IA (BIOS da GPU, firmware do TPU) é verificado com assinaturas criptográficas e atualizado de acordo com os cronogramas de gerenciamento de patches da organização.
 #4.11.2    Nível: 2    Papel: D/V
 Certifique-se de que, antes da execução da carga de trabalho, a integridade do acelerador de IA seja validada por atestação de hardware usando TPM 2.0, Intel TXT ou AMD SVM.
 #4.11.3    Nível: 2    Papel: D/V
 Verifique se a memória da GPU está isolada entre cargas de trabalho usando SR-IOV, MIG (GPU de instâncias múltiplas) ou particionamento de hardware equivalente com sanitização de memória entre trabalhos.
 #4.11.4    Nível: 3    Papel: V
 Verifique se a cadeia de suprimentos de hardware de IA inclui verificação de proveniência com certificados do fabricante e validação de embalagem à prova de violação.
 #4.11.5    Nível: 3    Papel: D/V
 Verifique se os Módulos de Segurança de Hardware (HSMs) protegem os pesos do modelo de IA e as chaves criptográficas com certificação FIPS 140-2 Nível 3 ou Common Criteria EAL4+.

---

### C4.12 Infraestrutura de IA na borda e distribuída

Implantações seguras de IA distribuída, incluindo computação de borda, aprendizado federado e arquiteturas de múltiplos sites.

 #4.12.1    Nível: 2    Papel: D/V
 Verifique se os dispositivos de IA de borda se autenticam na infraestrutura central usando TLS mútuo, com certificados de dispositivo rotacionados de acordo com a política de gerenciamento de certificados da organização.
 #4.12.2    Nível: 2    Papel: D/V
 Verifique se os dispositivos de borda implementam inicialização segura com assinaturas verificadas e proteção contra rollback que impeça ataques de downgrade de firmware.
 #4.12.3    Nível: 3    Papel: D/V
 Verifique se a coordenação de IA distribuída utiliza algoritmos de consenso tolerantes a falhas bizantinas, com validação de participantes e detecção de nós maliciosos.
 #4.12.4    Nível: 3    Papel: D/V
 Verifique se a comunicação de borda para a nuvem inclui limitação de largura de banda, compressão de dados e capacidades de operação offline com armazenamento local seguro.

---

### C4.13 Segurança de Infraestrutura Multi-Cloud e Híbrida

Proteja as cargas de trabalho de IA em vários provedores de nuvem e em implantações híbridas de nuvem e instalações locais.

 #4.13.1    Nível: 2    Papel: D/V
 Verifique se as implantações de IA em várias nuvens utilizam uma federação de identidade independente da nuvem (OIDC, SAML) com gerenciamento centralizado de políticas entre provedores.
 #4.13.2    Nível: 2    Papel: D/V
 Verifique se a transferência de dados entre nuvens utiliza criptografia de ponta a ponta com chaves gerenciadas pelo cliente e controles de residência de dados aplicados por jurisdição.
 #4.13.3    Nível: 2    Papel: D/V
 Verifique se as cargas de trabalho de IA em nuvem híbrida implementam políticas de segurança consistentes entre ambientes locais e na nuvem, com monitoramento e alertas unificados.
 #4.13.4    Nível: 3    Papel: V
 Verifique se a prevenção do lock-in de provedores de nuvem inclui infraestrutura como código portátil, APIs padronizadas e capacidades de exportação de dados com ferramentas de conversão de formatos.
 #4.13.5    Nível: 3    Papel: V
 Verifique se a otimização de custos multi-nuvem inclui controles de segurança que previnam a proliferação de recursos, bem como encargos de transferência de dados entre nuvens não autorizados.

---

### C4.14 Automação de Infraestrutura e Segurança do GitOps

Pipelines de automação de infraestrutura seguros e fluxos de trabalho GitOps para a gestão de infraestrutura de IA.

 #4.14.1    Nível: 2    Papel: D/V
 Verifique se os repositórios GitOps exigem commits assinados com chaves GPG e regras de proteção de ramificações que impeçam envios diretos para as ramificações principais.
 #4.14.2    Nível: 2    Papel: D/V
 Verifique se a automação de infraestrutura inclui detecção de drift com remediação automática e capacidades de rollback acionadas de acordo com os requisitos de resposta organizacionais para alterações não autorizadas.
 #4.14.3    Nível: 2    Papel: D/V
 Verifique se o provisionamento automatizado de infraestrutura inclui validação de políticas de segurança com bloqueio de implantação para configurações que não estejam em conformidade.
 #4.14.4    Nível: 2    Papel: D/V
 Verifique se os segredos de automação de infraestrutura são gerenciados por meio de operadores externos de segredos (External Secrets Operator, Bank-Vaults) com rotação automática.
 #4.14.5    Nível: 3    Papel: V
 Verifique se a infraestrutura autorreparável inclui a correlação de eventos de segurança com resposta automatizada a incidentes e fluxos de trabalho de notificação às partes interessadas.

---

### Segurança de Infraestrutura Resistente à Computação Quântica

Prepare a infraestrutura de IA para ameaças da computação quântica por meio de criptografia pós-quântica e protocolos à prova de ataques quânticos.

 #4.15.1    Nível: 3    Papel: D/V
 Verifique se a infraestrutura de IA implementa algoritmos criptográficos pós-quânticos aprovados pela NIST (CRYSTALS-Kyber, CRYSTALS-Dilithium, SPHINCS+) para troca de chaves e assinaturas digitais.
 #4.15.2    Nível: 3    Papel: D/V
 Verifique se os sistemas de distribuição de chaves quânticas (QKD) estão implementados para comunicações de IA de alta segurança, com protocolos de gerenciamento de chaves à prova de quântica.
 #4.15.3    Nível: 3    Papel: D/V
 Verifique se os frameworks de agilidade criptográfica permitem migração rápida para novos algoritmos pós-quânticos, com rotação automática de certificados e chaves.
 #4.15.4    Nível: 3    Papel: V
 Verifique se a modelagem de ameaças quânticas avalia a vulnerabilidade da infraestrutura de IA a ataques quânticos, com cronogramas de migração documentados e avaliações de risco.
 #4.15.5    Nível: 3    Papel: D/V
 Verifique se os sistemas criptográficos híbridos clássicos-quânticos fornecem defesa em profundidade durante o período de transição quântica, com monitoramento de desempenho.

---

### C4.16 Computação Confidencial e Enclaves Seguros

Proteja cargas de trabalho de IA e pesos do modelo usando ambientes de execução confiáveis baseados em hardware e tecnologias de computação confidencial.

 #4.16.1    Nível: 3    Papel: D/V
 Verifique se modelos de IA sensíveis são executados dentro de enclaves Intel SGX, AMD SEV-SNP ou ARM TrustZone com memória criptografada e verificação de atestação.
 #4.16.2    Nível: 3    Papel: D/V
 Verifique se contêineres confidenciais (Kata Containers, gVisor com computação confidencial) isolam cargas de trabalho de IA com criptografia de memória protegida por hardware.
 #4.16.3    Nível: 3    Papel: D/V
 Verifique se a atestação remota valida a integridade do enclave antes de carregar modelos de IA com prova criptográfica da autenticidade de um ambiente de execução.
 #4.16.4    Nível: 3    Papel: D/V
 Verifique se os serviços de inferência de IA confidenciais impedem a extração do modelo por meio de computação criptografada com pesos do modelo selados e execução protegida.
 #4.16.5    Nível: 3    Papel: D/V
 Verifique se a orquestração do ambiente de execução confiável gerencia o ciclo de vida do enclave seguro com atestação remota e canais de comunicação criptografados.
 #4.16.6    Nível: 3    Papel: D/V
 Verifique se a computação multipartidária segura (SMPC) permite o treinamento colaborativo de IA sem expor conjuntos de dados individuais ou parâmetros do modelo.

---

### C4.17 Zero-Knowledge Infraestrutura

Implemente sistemas de prova de conhecimento zero para verificação e autenticação de IA com preservação da privacidade, sem revelar informações sensíveis.

 #4.17.1    Nível: 3    Papel: D/V
 Verifique se as provas de conhecimento zero (ZK-SNARKs, ZK-STARKs) verificam a integridade do modelo de IA e a proveniência do treinamento sem expor os pesos do modelo ou os dados de treinamento.
 #4.17.2    Nível: 3    Papel: D/V
 Certifique-se de que os sistemas de autenticação baseados em ZK (provas de conhecimento zero) permitem a verificação de usuários com preservação da privacidade para serviços de IA sem revelar informações relacionadas à identidade.
 #4.17.3    Nível: 3    Papel: D/V
 Verifique se os protocolos de interseção de conjuntos privados (PSI) permitem a correspondência segura de dados para IA federada, sem expor conjuntos de dados individuais.
 #4.17.4    Nível: 3    Papel: D/V
 Verifique se os sistemas de aprendizado de máquina com conhecimento zero (ZKML) permitem inferências de IA verificáveis com prova criptográfica de execução correta.
 #4.17.5    Nível: 3    Papel: D/V
 Verifique se os ZK-rollups fornecem processamento de transações de IA escalável e com preservação de privacidade, com verificação em lote e redução da sobrecarga computacional.

---

### C4.18 Prevenção de ataques de canal-lateral

Proteja a infraestrutura de IA contra ataques de canal lateral baseados em temporização, consumo de energia, eletromagnéticos e cache que possam vazar informações sensíveis.

 #4.18.1    Nível: 3    Papel: D/V
 Verifique se o tempo de inferência de IA é normalizado usando algoritmos de tempo constante e preenchimento para prevenir ataques de extração de modelo baseados em tempo.
 #4.18.2    Nível: 3    Papel: D/V
 Verifique se a proteção contra análise de potência inclui injeção de ruído, filtragem da linha de alimentação e padrões de execução aleatorizados para hardware de IA.
 #4.18.3    Nível: 3    Papel: D/V
 Verifique se a mitigação de canais laterais baseada em cache utiliza particionamento de cache, randomização e instruções de flush para evitar vazamento de informações.
 #4.18.4    Nível: 3    Papel: D/V
 Verifique se a proteção contra emanções eletromagnéticas inclui blindagem, filtragem de sinais e processamento aleatorizado para prevenir ataques no estilo TEMPEST.
 #4.18.5    Nível: 3    Papel: D/V
 Verifique se as defesas contra canais laterais microarquiteturais incluem controles de execução especulativa e ofuscação de padrões de acesso à memória.

---

### C4.19 Segurança de hardware neuromórfico e IA especializada

Garanta a segurança das arquiteturas de hardware de IA emergentes, incluindo chips neuromórficos, FPGAs, ASICs personalizados e sistemas de computação óptica.

 #4.19.1    Nível: 3    Papel: D/V
 Verifique se a segurança do chip neuromórfico inclui criptografia de padrões de disparo, proteção de pesos sinápticos e validação de regras de aprendizado baseada em hardware.
 #4.19.2    Nível: 3    Papel: D/V
 Verifique se os aceleradores de IA baseados em FPGA implementam criptografia de bitstream, mecanismos anti-manipulação e carregamento seguro de configuração com atualizações autenticadas.
 #4.19.3    Nível: 3    Papel: D/V
 Verifique se a segurança de ASICs personalizados inclui processadores de segurança integrados, raiz de confiança de hardware e armazenamento seguro de chaves com detecção de adulteração.
 #4.19.4    Nível: 3    Papel: D/V
 Verifique se os sistemas de computação óptica implementam criptografia óptica resistente à computação quântica, comutação fotônica segura e processamento de sinais ópticos protegido.
 #4.19.5    Nível: 3    Papel: D/V
 Verifique se chips de IA híbridos analógico-digitais incluem computação analógica segura, armazenamento protegido de pesos e conversão analógico-digital autenticada.

---

### C4.20 Infraestrutura de Computação com Privacidade

Implemente controles de infraestrutura para computação que preserva a privacidade, a fim de proteger dados sensíveis durante o processamento e a análise por IA.

 #4.20.1    Nível: 3    Papel: D/V
 Verifique se a infraestrutura de criptografia homomórfica permite computação criptografada em cargas de trabalho sensíveis de IA, com verificação de integridade criptográfica e monitoramento de desempenho.
 #4.20.2    Nível: 3    Papel: D/V
 Verifique se os sistemas de recuperação de informações privadas permitem consultas a bancos de dados sem revelar padrões de consulta, com proteção criptográfica dos padrões de acesso.
 #4.20.3    Nível: 3    Papel: D/V
 Verifique se os protocolos de computação multipartidária segura permitem inferência de IA com preservação da privacidade, sem expor entradas individuais ou computações intermediárias.
 #4.20.4    Nível: 3    Papel: D/V
 Verifique se a gestão de chaves com preservação da privacidade inclui geração de chaves distribuída, criptografia de limiar e rotação segura de chaves com proteção baseada em hardware.
 #4.20.5    Nível: 3    Papel: D/V
 Verifique se o desempenho da computação com preservação de privacidade está otimizado por meio de processamento em lotes, armazenamento em cache e aceleração de hardware, mantendo as garantias de segurança criptográfica.

---

### C4.15 Framework de Agente: Integração em Nuvem, Segurança e Implantação Híbrida

Controles de segurança para frameworks de agentes integrados à nuvem com arquiteturas híbridas on-premises e nuvem.

 #4.15.1    Nível: 1    Papel: D/V
 Verifique se a integração de armazenamento em nuvem usa criptografia de ponta a ponta com gerenciamento de chaves controlado pelo agente.
 #4.15.2    Nível: 2    Papel: D/V
 Verifique se os limites de segurança da implantação híbrida estão claramente definidos com canais de comunicação criptografados.
 #4.15.3    Nível: 2    Papel: D/V
 Verifique se o acesso a recursos em nuvem inclui verificação de zero-trust com autenticação contínua.
 #4.15.4    Nível: 3    Papel: D/V
 Verifique se os requisitos de residência de dados são aplicados por meio de atestação criptográfica dos locais de armazenamento.
 #4.15.5    Nível: 3    Papel: D/V
 Verifique se as avaliações de segurança do provedor de nuvem incluem modelagem de ameaças específica do agente e avaliação de risco.

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

## C5 Controle de Acesso e Identidade para Componentes de IA e Usuários

### Objetivo de Controle

O controle de acesso eficaz para sistemas de IA requer gestão robusta de identidade, autorização contextual e aplicação em tempo de execução, seguindo os princípios de zero-trust. Esses controles garantem que humanos, serviços e agentes autônomos interajam apenas com modelos, dados e recursos computacionais dentro de escopos explicitamente concedidos, com verificação contínua e capacidade de auditoria.

---

### C5.1 Gestão de Identidade e Autenticação

Estabelecer identidades respaldadas criptograficamente para todas as entidades, com autenticação multifator para operações privilegiadas.

 #5.1.1    Nível: 1    Papel: D/V
 Verifique se todos os usuários humanos e identidades de serviço se autenticam por meio de um provedor de identidade empresarial centralizado (IdP), usando os protocolos OIDC/SAML, com mapeamentos únicos de identidade para token (sem contas ou credenciais compartilhadas).
 #5.1.2    Nível: 1    Papel: D/V
 Verifique se operações de alto-risco (implantação de modelos, exportação de pesos, acesso a dados de treinamento, alterações de configuração de produção) exigem autenticação multifator ou autenticação de reforço com revalidação da sessão.
 #5.1.3    Nível: 2    Papel: D
 Verifique se novas identidades passam pela verificação de identidade alinhada com o NIST 800-63-3 IAL-2 ou padrões equivalentes antes de receberem acesso ao sistema de produção.
 #5.1.4    Nível: 2    Papel: V
 Verifique se as revisões de acesso são realizadas trimestralmente, com detecção automatizada de contas inativas, exigência de rotação de credenciais e fluxos de desprovisionamento.
 #5.1.5    Nível: 3    Papel: D/V
 Verifique se os agentes federados de IA se autenticam por meio de afirmações JWT assinadas com vida útil máxima de 24 horas e incluem prova criptográfica de origem.

---

### C5.2 Autorização de Recursos e Princípio do menor privilégio

Implemente controles de acesso granulares para todos os recursos de IA, com modelos de permissão explícitos e trilhas de auditoria.

 #5.2.1    Nível: 1    Papel: D/V
 Verifique se cada recurso de IA (conjuntos de dados, modelos, endpoints, coleções de vetores, índices de embedding, instâncias de computação) aplica controles de acesso baseados em funções com listas de permissões explícitas e políticas de negação por padrão.
 #5.2.2    Nível: 1    Papel: D/V
 Verifique se os princípios do menor privilégio são aplicados por padrão, com contas de serviço que iniciam com permissões de somente leitura e que exigem justificativa de negócios documentada para acesso de escrita.
 #5.2.3    Nível: 1    Papel: V
 Verifique se todas as modificações de controle de acesso estão vinculadas a solicitações de mudança aprovadas e registradas de forma imutável com carimbos de tempo, identidades dos atores, identificadores de recursos e deltas de permissões.
 #5.2.4    Nível: 2    Papel: D
 Verifique se os rótulos de classificação de dados (PII, PHI, controle de exportação, proprietário) se propagam automaticamente para recursos derivados (vetores de embedding, caches de prompts, saídas do modelo) com aplicação consistente de políticas.
 #5.2.5    Nível: 2    Papel: D/V
 Verifique que as tentativas de acesso não autorizado e os eventos de escalonamento de privilégios acionem alertas em tempo real com metadados contextuais para sistemas SIEM dentro de 5 minutos.

---

### C5.3 Avaliação Dinâmica de Políticas

Implantar motores de controle de acesso baseado em atributos (ABAC) para decisões de autorização sensíveis ao contexto, com capacidades de auditoria.

 #5.3.1    Nível: 1    Papel: D/V
 Verifique se as decisões de autorização são externalizadas para um motor de políticas dedicado (OPA, Cedar ou equivalente) acessível via APIs autenticadas com proteção de integridade criptográfica.
 #5.3.2    Nível: 1    Papel: D/V
 Verifique se as políticas avaliam atributos dinâmicos em tempo de execução, incluindo o nível de autorização do usuário, a classificação de sensibilidade do recurso, o contexto da solicitação, o isolamento entre locatários e as restrições temporais.
 #5.3.3    Nível: 2    Papel: D
 Verifique se as definições de políticas são versionadas, revisadas por pares e validadas por meio de testes automatizados em pipelines de CI/CD antes da implantação em produção.
 #5.3.4    Nível: 2    Papel: V
 Verifique se os resultados da avaliação de políticas incluem justificativas de decisão estruturadas e são transmitidos para sistemas SIEM para análise de correlação e relatórios de conformidade.
 #5.3.5    Nível: 3    Papel: D/V
 Verifique se os valores do TTL do cache de políticas não excedem 5 minutos para recursos de alta sensibilidade e 1 hora para recursos padrão com capacidade de invalidação de cache.

---

### C5.4 Aplicação de Políticas de Segurança em Tempo de Consulta

Implemente controles de segurança na camada de banco de dados com filtragem obrigatória e políticas de segurança em nível de linha.

 #5.4.1    Nível: 1    Papel: D/V
 Verifique se todos os bancos de dados vetoriais e consultas SQL incluem filtros de segurança obrigatórios (ID do locatário, rótulos de sensibilidade, escopo do usuário) impostos no nível do motor de banco de dados, e não no código da aplicação.
 #5.4.2    Nível: 1    Papel: D/V
 Verifique se as políticas de segurança a nível de linha (RLS) e o mascaramento a nível de campo estão ativados com herança de políticas para todos os bancos de dados vetoriais, índices de busca e conjuntos de dados de treinamento.
 #5.4.3    Nível: 2    Papel: D
 Verifique se as avaliações de autorização com falha impedirão os 'ataques do ajudante confuso' ao abortar imediatamente as consultas e retornar códigos de erro de autorização explícitos, em vez de retornar conjuntos de resultados vazios.
 #5.4.4    Nível: 2    Papel: V
 Verifique se a latência da avaliação de políticas está sendo monitorada continuamente com alertas automatizados para condições de timeout que poderiam permitir o bypass de autorização.
 #5.4.5    Nível: 3    Papel: D/V
 Verifique se os mecanismos de re-tentativa de consultas reavaliam as políticas de autorização para levar em conta alterações dinâmicas de permissões durante sessões de usuário ativas.

---

### C5.5 Filtragem de Saída e Prevenção de Perda de Dados

Implantar controles de pós-processamento para impedir a exposição não autorizada de dados em conteúdo gerado por IA.

 #5.5.1    Nível: 1    Papel: D/V
 Verifique se os mecanismos de filtragem pós-inferência varrem e anonimizam PII (informação de identificação pessoal) não autorizada, informações classificadas e dados proprietários antes de entregar o conteúdo aos solicitantes.
 #5.5.2    Nível: 1    Papel: D/V
 Verifique se citações, referências e atribuições de fontes nas saídas do modelo são validadas com base nas autorizações do chamador e removidas se for detectado acesso não autorizado.
 #5.5.3    Nível: 2    Papel: D
 Verifique se as restrições de formato de saída ( PDFs sanitizados, imagens sem metadados, tipos de arquivo aprovados ) são aplicadas com base nos níveis de permissão do usuário e nas classificações de dados.
 #5.5.4    Nível: 2    Papel: V
 Verifique se os algoritmos de anonimização são determinísticos, versionados e mantêm logs de auditoria para apoiar investigações de conformidade e análises forenses.
 #5.5.5    Nível: 3    Papel: V
 Verifique se eventos de ocultação de alto risco geram logs adaptativos que incluem hashes criptográficos do conteúdo original para recuperação forense sem exposição de dados.

---

### C5.6 Isolamento entre inquilinos

Garantir isolamento criptográfico e lógico entre locatários em infraestrutura de IA compartilhada.

 #5.6.1    Nível: 1    Papel: D/V
 Verifique que os espaços de memória, os armazenamentos de embeddings, as entradas de cache e os arquivos temporários estão namespace-segregated por locatário, com purgação segura na exclusão do locatário ou no término da sessão.
 #5.6.2    Nível: 1    Papel: D/V
 Verifique se cada solicitação de API inclui um identificador de inquilino autenticado que seja validado criptograficamente em relação ao contexto de sessão e às permissões do usuário.
 #5.6.3    Nível: 2    Papel: D
 Verifique se as políticas de rede implementam regras padrão de negação para comunicação entre locatários dentro de malhas de serviço e plataformas de orquestração de contêineres.
 #5.6.4    Nível: 3    Papel: D
 Verifique se as chaves de criptografia são únicas por inquilino, com suporte a chave gerenciada pelo cliente (CMK) e isolamento criptográfico entre os bancos de dados dos inquilinos.

---

### C5.7 Autorização de Agente Autônomo

Controle as permissões para agentes de IA e sistemas autônomos por meio de tokens de capacidade com escopo e autorização contínua.

 #5.7.1    Nível: 1    Papel: D/V
 Verifique se os agentes autônomos recebem tokens de capacidade com escopo que enumeram explicitamente as ações permitidas, os recursos acessíveis, os limites de tempo e as restrições operacionais.
 #5.7.2    Nível: 1    Papel: D/V
 Verifique se as capacidades de alto risco (acesso ao sistema de arquivos, execução de código, chamadas de API externas, transações financeiras) estão desativadas por padrão e requerem autorizações explícitas para ativação com justificativas comerciais.
 #5.7.3    Nível: 2    Papel: D
 Verifique se os tokens de capacidade estão vinculados às sessões do usuário, incluem proteção de integridade criptográfica e garanta que eles não possam ser persistidos ou reutilizados em cenários offline.
 #5.7.4    Nível: 2    Papel: V
 Verifique que as ações iniciadas pelo agente passem por autorização secundária por meio do motor de políticas ABAC com avaliação completa do contexto e registro de auditoria.
 #5.7.5    Nível: 3    Papel: V
 Verifique se as condições de erro do agente e o tratamento de exceções incluem informações sobre o escopo de capacidades para apoiar a análise de incidentes e investigações forenses.

---

### Referências

#### Padrões e Frameworks

NIST SP 800-63-3: Digital Identity Guidelines
Zero Trust Architecture – NIST SP 800-207
OWASP Application Security Verification Standard (AISVS)
​
#### Guias de Implementação

Identity and Access Management in the AI Era: 2025 Guide – IDSA
Attribute-Based Access Control with OPA – Permify
How We Designed Cedar to Be Intuitive, Fast, and Safe – AWS
​
#### Segurança específica de IA

Row Level Security in Vector DBs for RAG – Bluetuple.ai
Tenant Isolation in Multi-Tenant Systems – WorkOS
Handling AI Agent Permissions – Stytch
OWASP Top 10 for Large Language Model Applications

## C6 Segurança da Cadeia de Suprimentos para Modelos, Frameworks e Dados

### Objetivo de Controle

Ataques na cadeia de suprimentos de IA exploram modelos, frameworks ou conjuntos de dados de terceiros para incorporar portas traseiras, viés ou código explorável. Esses controles fornecem proveniência fim‑a‑fim, gerenciamento de vulnerabilidades e monitoramento para proteger todo o ciclo de vida do modelo.

---

### C6.1 Verificação e Proveniência de Modelos Pré-Treinados

Avaliar e autenticar as origens de modelos de terceiros, licenças e comportamentos ocultos antes de qualquer ajuste‑fino ou implantação.

 #6.1.1    Nível: 1    Papel: D/V
 Verifique se cada artefato de modelo de terceiros inclui um registro de proveniência assinado que identifique o repositório de origem e o hash do commit.
 #6.1.2    Nível: 1    Papel: D/V
 Verifique se os modelos são varridos em busca de camadas maliciosas ou gatilhos troianos usando ferramentas automatizadas antes da importação.
 #6.1.3    Nível: 2    Papel: D
 Verifique se transfer‑learning fine‑tunes passam pela avaliação adversarial para detectar comportamentos ocultos.
 #6.1.4    Nível: 2    Papel: V
 Verifique se as licenças de modelos, as etiquetas de controle de exportação e as declarações de origem de dados estão registradas em uma entrada ML‑BOM.
 #6.1.5    Nível: 3    Papel: D/V
 Verifique se os modelos de alto‑risco (pesos carregados publicamente, criadores não verificados) permanecem em quarentena até a revisão humana e a aprovação.

---

### C6.2 Varredura de Frameworks e Bibliotecas

Varra continuamente frameworks e bibliotecas de ML em busca de CVEs e código malicioso para manter a pilha de tempo de execução segura.

 #6.2.1    Nível: 1    Papel: D/V
 Verifique se os pipelines de CI executam scanners de dependências em frameworks de IA e bibliotecas críticas.
 #6.2.2    Nível: 1    Papel: D/V
 Verifique se vulnerabilidades críticas (CVSS ≥ 7.0) bloqueiam a promoção para imagens de produção.
 #6.2.3    Nível: 2    Papel: D
 Verifique se a análise estática de código é executada em bibliotecas de ML forkadas ou vendorizadas.
 #6.2.4    Nível: 2    Papel: V
 Verifique se as propostas de atualização do framework incluem uma avaliação de impacto de segurança que faça referência a feeds públicos de CVE.
 #6.2.5    Nível: 3    Papel: V
 Verifique se os sensores em tempo de execução alertam sobre carregamentos inesperados de bibliotecas dinâmicas que se desviam do SBOM assinado.

---

### C6.3 Fixação de Dependências e Verificação

Fixe cada dependência em digests imutáveis e reproduza as compilações para garantir artefatos idênticos e livres de adulteração.

 #6.3.1    Nível: 1    Papel: D/V
 Verifique se todos os gerenciadores de pacotes garantem a fixação de versões por meio de arquivos de bloqueio.
 #6.3.2    Nível: 1    Papel: D/V
 Verifique se digests imutáveis são usados em vez de tags mutáveis em referências de contêiner.
 #6.3.3    Nível: 2    Papel: D
 Verifique se as verificações de builds reprodutíveis comparam valores de hash entre execuções de CI para garantir saídas idênticas.
 #6.3.4    Nível: 2    Papel: V
 Verifique se as atestações de compilação são armazenadas por 18 meses para rastreabilidade de auditoria.
 #6.3.5    Nível: 3    Papel: D
 Verifique se dependências expiradas acionam PRs automatizados para atualizar ou bifurcar versões fixadas.

---

### C6.4 Aplicação de Fontes Confiáveis

Permitir downloads de artefatos apenas de fontes criptograficamente verificadas e aprovadas pela organização, e bloquear tudo o mais.

 #6.4.1    Nível: 1    Papel: D/V
 Verifique se os pesos do modelo, os conjuntos de dados e os contêineres são baixados apenas de domínios aprovados ou de repositórios internos.
 #6.4.2    Nível: 1    Papel: D/V
 Verifique se as assinaturas Sigstore/Cosign validam a identidade do publicador antes que os artefatos sejam armazenados localmente em cache.
 #6.4.3    Nível: 2    Papel: D
 Verifique se os proxies de saída bloqueiam downloads de artefatos não autenticados para impor a política de fonte-confiável.
 #6.4.4    Nível: 2    Papel: V
 Verifique se as listas de permissão do repositório são revisadas trimestralmente com evidência de justificativa de negócios para cada entrada.
 #6.4.5    Nível: 3    Papel: V
 Verifique se violações de políticas acionam a quarentena de artefatos e a reversão das execuções de pipelines dependentes.

---

### C6.5 Avaliação de Risco de Conjunto de Dados de Terceiros

Avaliar conjuntos de dados externos quanto a envenenamento, viés e conformidade legal, e monitorá-los ao longo de seu ciclo de vida.

 #6.5.1    Nível: 1    Papel: D/V
 Verifique se conjuntos de dados externos passam por pontuação de risco de envenenamento (por exemplo, impressão digital de dados, detecção de valores atípicos).
 #6.5.2    Nível: 1    Papel: D
 Verifique se as métricas de viés (paridade demográfica, igualdade de oportunidades) são calculadas antes da aprovação do conjunto de dados.
 #6.5.3    Nível: 2    Papel: V
 Verifique se a proveniência e os termos de licença dos conjuntos de dados estão registrados nas entradas ML‑BOM.
 #6.5.4    Nível: 2    Papel: V
 Verifique se o monitoramento periódico detecta deriva de dados ou corrupção em conjuntos de dados hospedados.
 #6.5.5    Nível: 3    Papel: D
 Verifique se o conteúdo proibido (direitos autorais, PII) é removido por meio de uma limpeza automatizada antes do treinamento.

---

### C6.6 Monitoramento de Ataques na Cadeia de Suprimentos

Detecte ameaças na cadeia de suprimentos cedo por meio de feeds CVE, análises de logs de auditoria e simulações de red-team.

 #6.6.1    Nível: 1    Papel: V
 Verifique se os logs de auditoria de CI/CD fluem para as detecções do SIEM para pulls de pacotes anômalos ou etapas de build adulteradas.
 #6.6.2    Nível: 2    Papel: D
 Verifique se os playbooks de resposta a incidentes incluem procedimentos de rollback para modelos ou bibliotecas comprometidos.
 #6.6.3    Nível: 3    Papel: V
 Verifique se o enriquecimento de inteligência de ameaças marca indicadores ML‑específicos (por exemplo, IoCs de envenenamento de modelos) na triagem de alertas.

---

### C6.7 ML‑BOM para Artefatos do Modelo

Gere e assine SBOMs detalhadas específicas para ML (ML‑BOMs) para que os consumidores a jusante possam verificar a integridade dos componentes no momento da implantação.

 #6.7.1    Nível: 1    Papel: D/V
 Verifique se cada artefato de modelo publica um ML‑BOM que liste conjuntos de dados, pesos, hiperparâmetros e licenças.
 #6.7.2    Nível: 1    Papel: D/V
 Verifique se a geração de ML‑BOM e a assinatura Cosign são automatizadas na CI e obrigatórias para o merge.
 #6.7.3    Nível: 2    Papel: D
 Verifique se as verificações de completude do ML‑BOM fazem com que a compilação falhe caso qualquer metadado do componente (hash, licença) esteja ausente.
 #6.7.4    Nível: 2    Papel: V
 Verifique se os consumidores a jusante podem consultar ML-BOMs por meio de uma API para validar modelos importados no momento da implantação.
 #6.7.5    Nível: 3    Papel: V
 Verifique se ML‑BOMs estão sob controle de versão e são comparados para detectar modificações não autorizadas.

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

## C7 Comportamento do Modelo, Controle de Saída e Garantia de Segurança

### Objetivo de Controle

As saídas do modelo devem ser estruturadas, confiáveis, seguras, explicáveis e continuamente monitoradas em produção. Isso reduz alucinações, vazamentos de privacidade, conteúdo nocivo e ações fora de controle, enquanto aumenta a confiança do usuário e a conformidade regulatória.

---

### C7.1 Aplicação do Formato de Saída

Esquemas estritos, decodificação com restrições e validação a jusante impedem conteúdo malformado ou malicioso antes que ele se propague.

 #7.1.1    Nível: 1    Papel: D/V
 Verifique se os esquemas de resposta (por exemplo, JSON Schema) são fornecidos no prompt do sistema e se cada saída é validada automaticamente; saídas não conformes acionam reparo ou rejeição.
 #7.1.2    Nível: 1    Papel: D/V
 Verifique se a decodificação com restrições (tokens de parada, regex, max-tokens) está habilitada para evitar estouro ou canais laterais de injeção de prompt.
 #7.1.3    Nível: 2    Papel: D/V
 Verifique se os componentes a jusante tratam as saídas como não confiáveis e as validam contra esquemas ou deserializadores à prova de injeção.
 #7.1.4    Nível: 3    Papel: V
 Verifique se os eventos de saída imprópria são registrados, limitados por taxa e disponibilizados ao monitoramento.

---

### C7.2 Detecção e Mitigação de Alucinações

A estimativa de incerteza e estratégias de contingência limitam respostas fabricadas.

 #7.2.1    Nível: 1    Papel: D/V
 Verifique se as log-probabilidades por token, a consistência do ensemble ou detectores de alucinação ajustados atribuem uma pontuação de confiança a cada resposta.
 #7.2.2    Nível: 1    Papel: D/V
 Verifique se as respostas abaixo de um limiar de confiança configurável acionam fluxos de fallback (por exemplo, geração aumentada por recuperação, modelo secundário ou revisão humana).
 #7.2.3    Nível: 2    Papel: D/V
 Verifique se os incidentes de alucinação estão rotulados com metadados da causa raiz e alimentados nos pipelines de post-mortem e de ajuste fino.
 #7.2.4    Nível: 3    Papel: D/V
 Verifique se os limiares e detectores são recalibrados após grandes atualizações do modelo ou da base de conhecimento.
 #7.2.5    Nível: 3    Papel: V
 Verifique se as visualizações do painel monitoram as taxas de alucinação.

---

### C7.3 Filtragem de Segurança e Privacidade de Saída

Políticas de filtragem e cobertura da equipe vermelha protegem os usuários e dados confidenciais.

 #7.3.1    Nível: 1    Papel: D/V
 Verifique se os classificadores pré-geração e pós-geração bloqueiam conteúdo de ódio, assédio, autolesão, extremismo e conteúdo sexualmente explícito, em conformidade com a política.
 #7.3.2    Nível: 1    Papel: D/V
 Verifique se a detecção de PII/PCI e a anonimização automática são executadas em cada resposta; violações geram um incidente de privacidade.
 #7.3.3    Nível: 2    Papel: D
 Verifique se as etiquetas de confidencialidade se propagam entre modalidades para evitar vazamento em texto, imagens ou código.
 #7.3.4    Nível: 3    Papel: D/V
 Verifique se tentativas de burlar o filtro ou classificações de alto risco exigem aprovação secundária ou reautenticação do usuário.
 #7.3.5    Nível: 3    Papel: D/V
 Verifique se os limiares de filtragem refletem as jurisdições legais e o contexto de idade e função do usuário.

---

### C7.4 Limitação de Saída e Ação

Limites de taxa e portas de aprovação impedem abusos e autonomia excessiva.

 #7.4.1    Nível: 1    Papel: D
 Verifique se as cotas por usuário e por chave de API limitam solicitações, tokens e custo, com back-off exponencial em erros 429.
 #7.4.2    Nível: 1    Papel: D/V
 Verifique se ações privilegiadas (escrita de arquivos, execução de código, chamadas de rede) exigem aprovação baseada em políticas ou intervenção humana no loop.
 #7.4.3    Nível: 2    Papel: D/V
 Verifique se as verificações de consistência entre modalidades garantem que imagens, código e texto gerados para a mesma solicitação não possam ser usados para ocultar conteúdo malicioso.
 #7.4.4    Nível: 2    Papel: D
 Verifique se a profundidade de delegação do agente, os limites de recursão e as listas de ferramentas permitidas estão configurados de forma explícita.
 #7.4.5    Nível: 3    Papel: V
 Verifique se a violação de limites emite eventos de segurança estruturados para ingestão pelo SIEM.

---

### C7.5 Explicabilidade da Saída

Sinais transparentes melhoram a confiança do usuário e a depuração interna.

 #7.5.1    Nível: 2    Papel: D/V
 Verifique se as pontuações de confiança apresentadas ao usuário ou breves resumos do raciocínio são expostos quando a avaliação de risco assim o exigir.
 #7.5.2    Nível: 2    Papel: D/V
 Verifique se as explicações geradas evitam revelar prompts do sistema sensíveis ou dados proprietários.
 #7.5.3    Nível: 3    Papel: D
 Verifique se o sistema captura probabilidades logarítmicas por token ou mapas de atenção e os armazena para inspeção autorizada.
 #7.5.4    Nível: 3    Papel: V
 Verifique se os artefatos de explicabilidade estão sob controle de versão juntamente com as liberações do modelo, para auditabilidade.

---

### C7.6 Integração de Monitoramento

Observabilidade em tempo real fecha o ciclo entre desenvolvimento e produção.

 #7.6.1    Nível: 1    Papel: D
 Verifique se as métricas (violações de esquema, taxa de alucinação, toxicidade, vazamentos de PII, latência, custo) fluem para uma plataforma central de monitoramento.
 #7.6.2    Nível: 1    Papel: V
 Verifique se os limiares de alerta estão definidos para cada métrica de segurança, com caminhos de escalonamento em plantão.
 #7.6.3    Nível: 2    Papel: V
 Verifique se os painéis correlacionam anomalias de saída com o modelo/versão, flag de recurso e alterações nos dados upstream.
 #7.6.4    Nível: 2    Papel: D/V
 Verifique se os dados de monitoramento retroalimentam o re-treinamento, o ajuste fino ou as atualizações de regras dentro de um fluxo de MLOps documentado.
 #7.6.5    Nível: 3    Papel: V
 Verifique se os pipelines de monitoramento são submetidos a testes de penetração e têm controle de acesso para evitar o vazamento de logs sensíveis.

---

### 7.7 Salvaguardas da Mídia Generativa

Garanta que os sistemas de IA não gerem conteúdo de mídia ilegal, prejudicial ou não autorizado, aplicando restrições de políticas, validação de saída e rastreabilidade.

 #7.7.1    Nível: 1    Papel: D/V
 Verifique se os prompts do sistema e as instruções do usuário proíbem explicitamente a geração de mídia deepfake ilegal, nociva ou não consensual (por exemplo, imagem, vídeo, áudio).
 #7.7.2    Nível: 2    Papel: D/V
 Verifique se os prompts são filtrados para evitar tentativas de gerar suplantação de identidade, deepfakes sexualmente explícitos ou conteúdo que retrate pessoas reais sem consentimento.
 #7.7.3    Nível: 2    Papel: V
 Verifique se o sistema utiliza uma função de hash perceptual, detecção de marca d’água ou fingerprinting para impedir a reprodução não autorizada de conteúdo protegido por direitos autorais.
 #7.7.4    Nível: 3    Papel: D/V
 Verifique se toda a mídia gerada é assinada digitalmente, marcada com marca d'água ou incorporada com metadados de proveniência à prova de adulteração para rastreabilidade a jusante.
 #7.7.5    Nível: 3    Papel: V
 Verifique se as tentativas de contorno (por exemplo, obfuscação de prompts, gírias, formulação adversarial) são detectadas, registradas e com limitação de taxa; abusos repetidos são encaminhados aos sistemas de monitoramento.

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

## Memória C8, Representações Vetoriais e Segurança de Banco de Dados Vetorial

### Objetivo de Controle

Representações vetoriais e bancos de vetores atuam como a “memória ao vivo” dos sistemas de IA contemporâneos, aceitando continuamente dados fornecidos pelos usuários e retornando-os aos contextos do modelo por meio da Geração Aumentada por Recuperação (RAG). Se ficar sem governança, essa memória pode vazar PII, violar o consentimento ou ser invertida para reconstruir o texto original. O objetivo desta família de controles é fortalecer os pipelines de memória e os bancos de vetores, de modo que o acesso tenha privilégio mínimo, as representações vetoriais preservem a privacidade, os vetores armazenados expirem ou possam ser revogados sob demanda, e a memória por usuário nunca contamine as solicitações ou as saídas de outro usuário.

---

### C8.1 Controles de Acesso à Memória e aos Índices RAG

Implemente controles de acesso granulares em todas as coleções de vetores.

 #8.1.1    Nível: 1    Papel: D/V
 Verifique se as regras de controle de acesso em nível de linha ou espaço de nomes restringem as operações de inserção, exclusão e consulta por inquilino, coleção ou tag de documento.
 #8.1.2    Nível: 1    Papel: D/V
 Verifique se as chaves de API ou JWTs contêm declarações com escopo (por exemplo, identificadores de coleção, verbos de ação) e são rotacionadas pelo menos a cada trimestre.
 #8.1.3    Nível: 2    Papel: D/V
 Verifique se as tentativas de elevação de privilégios (por exemplo, consultas de similaridade entre namespaces) são detectadas e registradas em um SIEM dentro de 5 minutos.
 #8.1.4    Nível: 2    Papel: D/V
 Verifique se os logs de auditoria do banco de dados de vetores registram o identificador do sujeito, a operação, o ID/namespace do vetor, o limiar de similaridade e a contagem de resultados.
 #8.1.5    Nível: 3    Papel: V
 Verifique se as decisões de acesso são testadas quanto a falhas de bypass sempre que os motores são atualizados ou as regras de particionamento de índices mudam.

---

### C8.2 Sanitização e Validação de Embeddings

Pré-filtre o texto para PII; remova ou adote pseudonimização antes da vetorização; e, opcionalmente, pós-processe os embeddings para eliminar sinais residuais.

 #8.2.1    Nível: 1    Papel: D/V
 Verifique se PII e dados sujeitos à regulamentação são detectados por classificadores automatizados e mascarados, tokenizados ou descartados antes do pré-embedding.
 #8.2.2    Nível: 1    Papel: D
 Verifique se os pipelines de embedding rejeitam ou colocam em quarentena entradas contendo código executável ou artefatos que não estejam em UTF-8 e que possam contaminar o índice.
 #8.2.3    Nível: 2    Papel: D/V
 Verifique se a sanitização de privacidade diferencial local ou de privacidade diferencial métrica é aplicada às representações vetoriais de sentenças cuja distância até qualquer token PII conhecido fica abaixo de um limiar configurável.
 #8.2.4    Nível: 2    Papel: V
 Verifique se a eficácia da sanitização (por exemplo, recall da remoção de PII, deriva semântica) é validada pelo menos semestralmente contra corpora de referência.
 #8.2.5    Nível: 3    Papel: D/V
 Verifique se as configurações de sanitização estão sob controle de versão e se as alterações passam por revisão por pares.

---

### C8.3 Expiração da Memória, Revogação e Exclusão

GDPR "direito ao esquecimento" e leis similares exigem apagamento em tempo hábil; os bancos de vetores devem, portanto, suportar TTLs, exclusões permanentes e tomb-stoning para que vetores revogados não possam ser recuperados ou reindexados.

 #8.3.1    Nível: 1    Papel: D/V
 Verifique se cada vetor e registro de metadados carrega um TTL ou uma etiqueta de retenção explícita, que seja respeitada pelos trabalhos de limpeza automatizados.
 #8.3.2    Nível: 1    Papel: D/V
 Verifique se as solicitações de exclusão iniciadas pelo usuário purgam vetores, metadados, cópias em cache e índices derivados no prazo de 30 dias.
 #8.3.3    Nível: 2    Papel: D
 Verifique se as exclusões lógicas são seguidas pela trituração criptográfica dos blocos de armazenamento, se o hardware oferecer suporte a isso, ou pela destruição da chave no Key Vault.
 #8.3.4    Nível: 3    Papel: D/V
 Verifique se vetores expirados são excluídos dos resultados da busca de vizinhos mais próximos em menos de 500 ms após a expiração.

---

### C8.4 Prevenir a inversão de embeddings e vazamento de dados

Defesas recentes—superposição de ruído, redes de projeção, perturbação de neurônios de privacidade e criptografia da camada de aplicação—podem reduzir as taxas de inversão em nível de token para abaixo de 5%.

 #8.4.1    Nível: 1    Papel: V
 Verifique se existe um modelo de ameaça formal que abranja ataques de inversão, ataques de inferência de pertencimento e ataques de inferência de atributos, e se ele é revisado anualmente.
 #8.4.2    Nível: 2    Papel: D/V
 Verifique se a criptografia na camada de aplicação ou a criptografia pesquisável protege os vetores contra leituras diretas por administradores de infraestrutura ou pela equipe de nuvem.
 #8.4.3    Nível: 3    Papel: V
 Verifique que os parâmetros de defesa (ε para DP, ruído σ, posto de projeção k) equilibrem a privacidade ≥ 99 % com proteção de token e a utilidade ≤ 3 % com perda de precisão.
 #8.4.4    Nível: 3    Papel: D/V
 Verifique se as métricas de resiliência à inversão de modelo fazem parte dos portões de liberação para atualizações de modelo, com orçamentos de regressão definidos.

---

### C8.5 Imposição do Escopo para Memória Específica do Usuário

Vazamento entre inquilinos continua sendo um dos maiores riscos de RAG: consultas de similaridade filtradas de forma inadequada podem expor documentos privados de outro cliente.

 #8.5.1    Nível: 1    Papel: D/V
 Verifique se toda consulta de recuperação é filtrada pelo ID do inquilino/usuário antes de ser encaminhada para o prompt do LLM.
 #8.5.2    Nível: 1    Papel: D
 Verifique se os nomes de coleção ou IDs com espaço de nomes recebem um sal por usuário ou por inquilino, para que os vetores não entrem em colisão entre escopos.
 #8.5.3    Nível: 2    Papel: D/V
 Verifique que os resultados de similaridade acima do limiar de distância configurável, mas fora do escopo do chamador, sejam descartados e gerem alertas de segurança.
 #8.5.4    Nível: 2    Papel: V
 Verifique que os testes de estresse multi-tenant simulam consultas adversariais que tentam recuperar documentos fora do escopo e demonstrem zero vazamento.
 #8.5.5    Nível: 3    Papel: D/V
 Verifique se as chaves criptográficas estão segregadas por inquilino, garantindo isolamento criptográfico mesmo que o armazenamento físico seja compartilhado.

---

### C8.6 Segurança Avançada do Sistema de Memória

Controles de segurança para arquiteturas de memória sofisticadas, incluindo memória episódica, memória semântica e memória de trabalho, com requisitos específicos de isolamento e validação.

 #8.6.1    Nível: 1    Papel: D/V
 Verifique se os diferentes tipos de memória (episódica, semântica, de trabalho) possuem contextos de segurança isolados com controles de acesso baseados em papéis, chaves de criptografia separadas e padrões de acesso documentados para cada tipo de memória.
 #8.6.2    Nível: 2    Papel: D/V
 Verifique se os processos de consolidação de memória incluem validação de segurança para impedir a injeção de memórias maliciosas por meio de sanitização de conteúdo, verificação de origem e checagens de integridade antes do armazenamento.
 #8.6.3    Nível: 2    Papel: D/V
 Verifique se as consultas de recuperação de memória são validadas e sanitizadas para impedir a extração de informações não autorizadas por meio de análise de padrões de consulta, aplicação do controle de acesso e filtragem de resultados.
 #8.6.4    Nível: 3    Papel: D/V
 Verifique se os mecanismos de apagamento de memória eliminam com segurança informações sensíveis com garantias de eliminação criptográfica, usando exclusão de chaves, sobrescrita em várias passadas ou exclusão segura baseada em hardware com certificados de verificação.
 #8.6.5    Nível: 3    Papel: D/V
 Verifique se a integridade do sistema de memória é monitorada continuamente quanto a modificações não autorizadas ou corrupção, por meio de checksums, logs de auditoria e alertas automatizados quando o conteúdo da memória muda fora das operações normais.

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

## 9 Segurança Da Orquestração Autônoma & Ação De Agente

### Objetivo de Controle

Garanta que sistemas de IA autônomos ou multiagentes possam executar apenas ações que sejam explicitamente pretendidas, autenticadas, auditáveis e dentro de limites de custo e risco definidos. Isso protege contra ameaças como Comprometimento de Sistemas Autônomos, Uso Indevido de Ferramentas, Detecção de Loop de Agentes, Sequestro de Comunicações, Falsificação de Identidade, Manipulação de Enxames e Manipulação de Intenções.

---

### 9.1 Planejamento de Tarefas do Agente e Orçamentos de Recursão

Limite planos recursivos e imponha pontos de verificação humanos para ações privilegiadas.

 #9.1.1    Nível: 1    Papel: D/V
 Verifique se a profundidade máxima de recursão, a largura, o tempo de relógio, os tokens e o custo monetário por execução de cada agente estão configurados centralmente e sob controle de versão.
 #9.1.2    Nível: 1    Papel: D/V
 Verifique se ações privilegiadas ou irreversíveis (por exemplo, commits de código, transferências financeiras) exigem aprovação humana explícita por meio de um canal auditável antes da execução.
 #9.1.3    Nível: 2    Papel: D
 Verifique se os monitores de recursos em tempo-real acionam a interrupção do circuit-breaker quando qualquer limiar de orçamento é excedido, interrompendo a expansão adicional de tarefas.
 #9.1.4    Nível: 2    Papel: D/V
 Verifique se os eventos do disjuntor são registrados com o ID do agente, a condição de disparo e o estado do plano capturado para revisão forense.
 #9.1.5    Nível: 3    Papel: V
 Verifique se os testes de segurança cobrem cenários de esgotamento de orçamento e de um plano fora de controle, confirmando a parada segura sem perda de dados.
 #9.1.6    Nível: 3    Papel: D
 Verifique se as políticas de orçamento são expressas como policy-as-code e aplicadas no CI/CD para impedir a deriva de configuração.

---

### 9.2 Isolamento de Plug-ins de Ferramentas

Isolar as interações com as ferramentas para impedir o acesso não autorizado ao sistema ou a execução de código.

 #9.2.1    Nível: 1    Papel: D/V
 Verifique que cada ferramenta/plugin execute dentro de um sandbox de nível OS, contêiner ou WASM, com políticas de privilégios mínimos para o sistema de arquivos, rede e chamadas de sistema.
 #9.2.2    Nível: 1    Papel: D/V
 Verifique se as cotas de recursos do sandbox (CPU, memória, disco, tráfego de saída de rede) e os timeouts de execução são aplicados e registrados.
 #9.2.3    Nível: 2    Papel: D/V
 Verifique se os binários da ferramenta ou descritores são assinados digitalmente; as assinaturas são validadas antes de serem carregadas.
 #9.2.4    Nível: 2    Papel: V
 Verifique se a telemetria do sandbox é enviada para um SIEM; anomalias (por exemplo, tentativas de conexões de saída) acionam alertas.
 #9.2.5    Nível: 3    Papel: V
 Verifique se plugins de alto risco passam por revisão de segurança e testes de penetração antes da implantação em produção.
 #9.2.6    Nível: 3    Papel: D/V
 Verifique se as tentativas de evasão do sandbox são bloqueadas automaticamente e o plugin em questão é colocado em quarentena até a conclusão da investigação.

---

### 9.3 Laço Autônomo e Limite de Custo

Detectar e interromper a recursão descontrolada entre agentes e explosões de custo.

 #9.3.1    Nível: 1    Papel: D/V
 Verifique se as chamadas entre agentes incluem um limite de saltos ou TTL que é decrementado e aplicado pelo tempo de execução.
 #9.3.2    Nível: 2    Papel: D
 Verifique se os agentes mantêm um ID único de grafo de invocação para detectar autoinvocação ou padrões cíclicos.
 #9.3.3    Nível: 2    Papel: D/V
 Verifique se os contadores acumulados de unidades de computação e de gasto são rastreados por cadeia de solicitações; ultrapassar o limite encerra a cadeia.
 #9.3.4    Nível: 3    Papel: V
 Verifique se a análise formal ou a verificação de modelo demonstra a ausência de recursão ilimitada nos protocolos de agentes.
 #9.3.5    Nível: 3    Papel: D
 Verifique se os eventos de loop-abort geram alertas e alimentam métricas de melhoria contínua.

---

### 9.4 Proteção contra uso indevido em nível de protocolo

Canais de comunicação seguros entre agentes e sistemas externos para evitar o sequestro de sessão ou a manipulação.

 #9.4.1    Nível: 1    Papel: D/V
 Verifique se todas as mensagens entre agente e ferramenta e entre agentes estão autenticadas (por exemplo, TLS mútuo ou JWT) e criptografadas de ponta a ponta.
 #9.4.2    Nível: 1    Papel: D
 Verifique se os esquemas são validados estritamente; campos desconhecidos ou mensagens malformadas são rejeitadas.
 #9.4.3    Nível: 2    Papel: D/V
 Verifique se as verificações de integridade (MACs ou assinaturas digitais) cobrem toda a carga útil da mensagem, incluindo os parâmetros da ferramenta.
 #9.4.4    Nível: 2    Papel: D
 Verifique se a proteção contra replay (nonces ou janelas de carimbo de tempo) é aplicada na camada de protocolo.
 #9.4.5    Nível: 3    Papel: V
 Verifique se as implementações de protocolo passam por fuzzing e análise estática para detectar falhas de injeção ou desserialização.

---

### 9.5 Identidade do Agente e Evidência de Adulteração

Garanta que as ações sejam atribuíveis e que as modificações sejam detectáveis.

 #9.5.1    Nível: 1    Papel: D/V
 Verifique se cada instância de agente possui uma identidade criptográfica única (par de chaves ou credencial enraizada em hardware).
 #9.5.2    Nível: 2    Papel: D/V
 Verifique se todas as ações do agente estão assinadas e com carimbo de data/hora; os logs incluem a assinatura para não-repúdio.
 #9.5.3    Nível: 2    Papel: V
 Verifique se os logs à prova de adulteração são armazenados em um meio apenas de acréscimo (append-only) ou em um meio de gravação única (write-once).
 #9.5.4    Nível: 3    Papel: D
 Verifique se as chaves de identidade são rotacionadas de acordo com uma programação definida e com base em indicadores de comprometimento.
 #9.5.5    Nível: 3    Papel: D/V
 Verifique se tentativas de spoofing ou de key-conflict acionam a quarentena imediata do agente afetado.

---

### 9.6 Redução de Risco do Enxame de Múltiplos Agentes

Mitigar riscos de comportamento coletivo por meio do isolamento e da modelagem formal de segurança.

 #9.6.1    Nível: 1    Papel: D/V
 Verifique se os agentes que operam em diferentes domínios de segurança são executados em sandboxes de tempo de execução isolados ou em segmentos de rede.
 #9.6.2    Nível: 3    Papel: V
 Verifique se os comportamentos de enxame são modelados e verificados formalmente quanto à vivacidade e à segurança antes da implantação.
 #9.6.3    Nível: 3    Papel: D
 Verifique se os monitores em tempo de execução detectam padrões inseguros emergentes (por exemplo, oscilações, interbloqueios) e iniciam ações corretivas.

---

### 9.7 Autenticação / Autorização do Usuário e da Ferramenta

Implemente controles de acesso robustos para cada ação acionada por um agente.

 #9.7.1    Nível: 1    Papel: D/V
 Verifique se os agentes se autenticam como entidades de primeira classe em sistemas a jusante, nunca reutilizando credenciais do usuário final.
 #9.7.2    Nível: 2    Papel: D
 Verifique se as políticas de autorização de granularidade fina restringem quais ferramentas um agente pode invocar e quais parâmetros ele pode fornecer.
 #9.7.3    Nível: 2    Papel: V
 Verifique se as verificações de privilégios são reavaliadas a cada chamada (autorização contínua), não apenas no início da sessão.
 #9.7.4    Nível: 3    Papel: D
 Verifique se as permissões delegadas expiram automaticamente e exigem novo consentimento após o tempo limite ou mudança de escopo.

---

### 9.8 Segurança da Comunicação entre Agentes

Criptografe e proteja a integridade de todas as mensagens entre agentes para impedir a interceptação e a adulteração.

 #9.8.1    Nível: 1    Papel: D/V
 Verifique se a autenticação mútua e a criptografia com Perfect Forward Secrecy (PFS), como TLS 1.3, são obrigatórias para os canais de agentes.
 #9.8.2    Nível: 1    Papel: D
 Verifique se a integridade da mensagem e a origem são validadas antes do processamento; as falhas geram alertas e a mensagem é descartada.
 #9.8.3    Nível: 2    Papel: D/V
 Verifique se os metadados de comunicação (carimbos de tempo, números de sequência) são registrados para apoiar a reconstrução forense.
 #9.8.4    Nível: 3    Papel: V
 Verifique se a verificação formal ou a verificação de modelo confirma que as máquinas de estados do protocolo não podem chegar a estados inseguros.

---

### 9.9 Verificação de Intenção e Aplicação de Restrições

Verifique se as ações do agente estão alinhadas com a intenção declarada pelo usuário e com as restrições do sistema.

 #9.9.1    Nível: 1    Papel: D
 Verifique se os solucionadores de restrições pré-execução verificam as ações propostas em relação às regras de segurança e políticas codificadas no código.
 #9.9.2    Nível: 2    Papel: D/V
 Verifique se as ações de alto impacto (financeiras, destrutivas, sensíveis à privacidade) exigem confirmação explícita de intenção por parte do usuário que as iniciou.
 #9.9.3    Nível: 2    Papel: V
 Verifique se as verificações de pós-condição validam que as ações concluídas atingiram os efeitos pretendidos sem efeitos colaterais; as discrepâncias acionam a reversão.
 #9.9.4    Nível: 3    Papel: V
 Verifique se métodos formais (por exemplo, verificação de modelos, prova de teoremas) ou testes baseados em propriedades demonstram que os planos do agente satisfazem todas as restrições declaradas.
 #9.9.5    Nível: 3    Papel: D
 Verifique se incidentes de desalinhamento de intenções ou violação de restrições alimentam ciclos de melhoria contínua e o compartilhamento de inteligência de ameaças.

---

### 9.10 Agente Raciocínio Estratégia Segurança

Seleção segura e execução de diferentes estratégias de raciocínio, incluindo as abordagens ReAct, Chain-of-Thought e Tree-of-Thoughts.

 #9.10.1    Nível: 1    Papel: D/V
 Verifique que a seleção da estratégia de raciocínio utilize critérios determinísticos (complexidade de entrada, tipo de tarefa, contexto de segurança) e que entradas idênticas produzam seleções de estratégia idênticas dentro do mesmo contexto de segurança.
 #9.10.2    Nível: 1    Papel: D/V
 Verifique se cada estratégia de raciocínio (ReAct, Chain-of-Thought, Tree-of-Thoughts) possui validação de entrada dedicada, sanitização de saída e limites de tempo de execução específicos para a sua abordagem cognitiva.
 #9.10.3    Nível: 2    Papel: D/V
 Verifique se as transições da estratégia de raciocínio são registradas com contexto completo, incluindo características de entrada, valores dos critérios de seleção e metadados de execução para a reconstrução da trilha de auditoria.
 #9.10.4    Nível: 2    Papel: D/V
 Verifique se o raciocínio em Árvore de Pensamentos inclui mecanismos de poda de ramos que interrompem a exploração quando violações de políticas, limites de recursos ou fronteiras de segurança são detectadas.
 #9.10.5    Nível: 2    Papel: D/V
 Verifique se os ciclos ReAct (Reason-Act-Observe) incluem pontos de validação em cada fase: verificação do passo de raciocínio, autorização de ação e sanitização de observação antes de prosseguir.
 #9.10.6    Nível: 3    Papel: D/V
 Verifique se as métricas de desempenho da estratégia de raciocínio (tempo de execução, uso de recursos, qualidade da saída) são monitoradas com alertas automatizados quando as métricas se desviam além dos limiares configurados.
 #9.10.7    Nível: 3    Papel: D/V
 Verifique se abordagens de raciocínio híbrido que combinam várias estratégias mantêm a validação de entrada e as restrições de saída de todas as estratégias constituintes sem contornar quaisquer controles de segurança.
 #9.10.8    Nível: 3    Papel: D/V
 Verifique se os testes de segurança da estratégia de raciocínio incluem fuzzing com entradas malformadas, prompts adversariais projetados para forçar a troca de estratégia e testes de condições de fronteira para cada abordagem cognitiva.

---

### 9.11 Gerenciamento do Ciclo de Vida do Agente e Segurança

Inicialização segura do agente, transições de estado e terminação com registros de auditoria criptográficos e procedimentos de recuperação definidos.

 #9.11.1    Nível: 1    Papel: D/V
 Verifique se a inicialização do agente inclui o estabelecimento de identidade criptográfica com credenciais protegidas por hardware e logs de auditoria de inicialização imutáveis contendo o ID do agente, carimbo de data e hora, hash da configuração e parâmetros de inicialização.
 #9.11.2    Nível: 2    Papel: D/V
 Verifique se as transições de estado do agente estão assinadas digitalmente, com carimbo de tempo e registradas com contexto completo, incluindo os eventos desencadeadores, o hash do estado anterior, o hash do estado atual e as validações de segurança realizadas.
 #9.11.3    Nível: 2    Papel: D/V
 Verifique se os procedimentos de desligamento do agente incluem o apagamento seguro da memória usando eliminação criptográfica ou sobregravação em várias passadas, revogação de credenciais com notificação à autoridade certificadora e geração de certificados de encerramento à prova de adulteração.
 #9.11.4    Nível: 3    Papel: D/V
 Verifique que os mecanismos de recuperação de agentes validam a integridade do estado usando somas de verificação criptográficas (SHA-256 no mínimo) e executam rollback para estados previamente verificados como íntegros quando é detectada corrupção, com alertas automatizados e requisitos de aprovação manual.
 #9.11.5    Nível: 3    Papel: D/V
 Verifique se os mecanismos de persistência de agentes criptografam dados de estado sensíveis com chaves AES-256 por agente e implementam rotação de chaves segura em cronogramas configuráveis (máximo de 90 dias) com implantação sem tempo de inatividade.

---

### 9.12 Estrutura de Segurança para Integração de Ferramentas

Controles de segurança para carregamento dinâmico de ferramentas, execução e validação de resultados com avaliação de risco definida e processos de aprovação.

 #9.12.1    Nível: 1    Papel: D/V
 Verifique se os descritores de ferramenta incluem metadados de segurança que especificam privilégios exigidos (leitura/gravação/execução), níveis de risco (baixo/médio/alto), limites de recursos (CPU, memória, rede) e requisitos de validação documentados nos manifestos da ferramenta.
 #9.12.2    Nível: 1    Papel: D/V
 Verifique se os resultados da execução da ferramenta são validados em relação aos esquemas esperados (JSON Schema, XML Schema) e às políticas de segurança (sanitização de saída, classificação de dados) antes da integração com limites de tempo e procedimentos de tratamento de erros.
 #9.12.3    Nível: 2    Papel: D/V
 Verifique se os registros de interação de ferramentas incluem contexto de segurança detalhado, incluindo uso de privilégios, padrões de acesso a dados, tempo de execução, consumo de recursos e códigos de retorno, com registro estruturado para integração com SIEM.
 #9.12.4    Nível: 2    Papel: D/V
 Verifique se os mecanismos dinâmicos de carregamento de ferramentas validam assinaturas digitais usando a infraestrutura PKI e implemente protocolos de carregamento seguro com isolamento em sandbox e verificação de permissões antes da execução.
 #9.12.5    Nível: 3    Papel: D/V
 Verifique que as avaliações de segurança de ferramentas são acionadas automaticamente para novas versões com portas de aprovação obrigatórias, incluindo análise estática, teste dinâmico e revisão pela equipe de segurança, com critérios de aprovação documentados e requisitos de SLA.

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

## 10 Robustez Adversarial e Defesa da Privacidade

### Objetivo de Controle

Garanta que os modelos de IA permaneçam confiáveis, preservem a privacidade e resistam a abusos ao enfrentarem ataques de evasão, inferência, extração ou envenenamento.

---

### 10.1 Alinhamento de Modelos e Segurança

Previna saídas nocivas ou que violem políticas.

 #10.1.1    Nível: 1    Papel: D/V
 Verifique se um conjunto de testes de alinhamento (prompts de red team, sondas de jailbreak, conteúdo proibido) está sob controle de versão e é executado em cada versão do modelo.
 #10.1.2    Nível: 1    Papel: D
 Verifique se as salvaguardas de recusa e de finalização segura estão sendo aplicadas.
 #10.1.3    Nível: 2    Papel: D/V
 Verifique se um avaliador automatizado mede a taxa de conteúdo nocivo e sinaliza regressões que excedem um limiar definido.
 #10.1.4    Nível: 2    Papel: D
 Verifique se o treinamento de counter-jailbreak está documentado e é reproduzível.
 #10.1.5    Nível: 3    Papel: V
 Verifique se as provas formais de conformidade com políticas ou o monitoramento certificado cobrem domínios críticos.

---

### 10.2 Endurecimento de Exemplos Adversários

Aumentar a resiliência a entradas manipuladas. O treinamento adversarial robusto e a avaliação por benchmarks são as melhores práticas atuais.

 #10.2.1    Nível: 1    Papel: D
 Verifique se os repositórios de projetos incluem configurações de treinamento adversarial com sementes reprodutíveis.
 #10.2.2    Nível: 2    Papel: D/V
 Verifique se a detecção de exemplos adversários gera alertas bloqueantes nos pipelines de produção.
 #10.2.4    Nível: 3    Papel: V
 Verifique se as provas de robustez certificada ou certificados com limites intervalares cobrem pelo menos as classes críticas mais importantes.
 #10.2.5    Nível: 3    Papel: V
 Verifique se os testes de regressão utilizam ataques adaptativos para confirmar que não há perda mensurável de robustez.

---

### 10.3 Mitigação da Inferência de Pertencimento

Limite a capacidade de decidir se um registro estava nos dados de treinamento. A privacidade diferencial e o mascaramento da pontuação de confiança permanecem as defesas mais eficazes conhecidas.

 #10.3.1    Nível: 1    Papel: D
 Verifique se a regularização da entropia por consulta ou o escalonamento de temperatura reduzem previsões excessivamente confiantes.
 #10.3.2    Nível: 2    Papel: D
 Verifique se o treinamento utiliza otimização com privacidade diferencial limitada por ε para conjuntos de dados sensíveis.
 #10.3.3    Nível: 2    Papel: V
 Verifique se as simulações de ataque (modelo-sombra ou caixa-preta) mostram AUC de ataque ≤ 0.60 em dados hold-out.

---

### 10.4 Modelo-Inversão Resistência

Impedir a reconstrução de atributos privados. Pesquisas recentes destacam o truncamento de saída e garantias de privacidade diferencial (DP) como defesas práticas.

 #10.4.1    Nível: 1    Papel: D
 Verifique se atributos sensíveis nunca são exibidos diretamente; quando necessário, utilize bucketização ou transformações unidirecionais.
 #10.4.2    Nível: 1    Papel: D/V
 Verifique se os limites de taxa de consulta restringem consultas adaptativas repetidas do mesmo principal.
 #10.4.3    Nível: 2    Papel: D
 Verifique se o modelo é treinado com ruído que preserva a privacidade.

---

### 10.5 Defesa contra a extração de modelos

Detectar e dissuadir a clonagem não autorizada. Marca d'água e análise de padrões de consulta são recomendadas.

 #10.5.1    Nível: 1    Papel: D
 Verifique se os gateways de inferência aplicam limites de taxa globais e por chave de API, ajustados ao limiar de memorização do modelo.
 #10.5.2    Nível: 2    Papel: D/V
 Verifique se as estatísticas de entropia de consulta e de pluralidade de entrada alimentam um detector automatizado de extração.
 #10.5.3    Nível: 2    Papel: V
 Verifique se marcas d'água frágeis ou probabilísticas podem ser comprovadas com p < 0.01 em ≤ 1 000 consultas contra um clone suspeito.
 #10.5.4    Nível: 3    Papel: D
 Verifique se as chaves de marca d'água e os conjuntos de gatilhos são armazenados em um Módulo de Segurança de Hardware (HSM) e são rotacionados anualmente.
 #10.5.5    Nível: 3    Papel: V
 Verifique se os alertas de extração incluem consultas ofensivas e estão integrados aos playbooks de resposta a incidentes.

---

### 10.6 Detecção de Dados Envenenados em Tempo de Inferência

Identifique e neutralize entradas com backdoor ou envenenadas.

 #10.6.1    Nível: 1    Papel: D
 Verifique se as entradas passam por um detector de anomalias (por exemplo, STRIP, pontuação de consistência) antes da inferência do modelo.
 #10.6.2    Nível: 1    Papel: V
 Verifique se os limiares do detector estão ajustados em conjuntos de validação limpos e envenenados para obter menos de 5% de falsos positivos.
 #10.6.3    Nível: 2    Papel: D
 Verifique se as entradas sinalizadas como envenenadas acionam bloqueio suave e fluxos de revisão humana.
 #10.6.4    Nível: 2    Papel: V
 Verifique se os detectores são submetidos a testes de estresse com ataques de porta dos fundos adaptativos, sem gatilho.
 #10.6.5    Nível: 3    Papel: D
 Verifique se as métricas de eficácia da detecção são registradas e periodicamente reavaliadas com inteligência de ameaças atualizada.

---

### 10.7 Adaptação Dinâmica da Política de Segurança

Atualizações de políticas de segurança em tempo-real com base em inteligência de ameaças e análise comportamental.

 #10.7.1    Nível: 1    Papel: D/V
 Verifique se as políticas de segurança podem ser atualizadas dinamicamente sem reiniciar o agente, mantendo a integridade da versão da política.
 #10.7.2    Nível: 2    Papel: D/V
 Verifique se as atualizações de políticas são assinadas criptograficamente por funcionários de segurança autorizados e validadas antes da aplicação.
 #10.7.3    Nível: 2    Papel: D/V
 Verifique se as alterações dinâmicas de políticas são registradas com trilhas de auditoria completas, incluindo justificativa, cadeias de aprovação e procedimentos de rollback.
 #10.7.4    Nível: 3    Papel: D/V
 Verifique se os mecanismos de segurança adaptativos ajustam a sensibilidade da detecção de ameaças com base no contexto de risco e em padrões comportamentais.
 #10.7.5    Nível: 3    Papel: D/V
 Verifique se as decisões de adaptação de políticas são explicáveis e incluem trilhas de evidência para revisão pela equipe de segurança.

---

### 10.8 Análise de Segurança Baseada em Reflexão

Validação de segurança por meio da autorreflexão do agente e da análise metacognitiva.

 #10.8.1    Nível: 1    Papel: D/V
 Verifique se os mecanismos de reflexão de agentes incluem autoavaliação com foco na segurança das decisões e ações.
 #10.8.2    Nível: 2    Papel: D/V
 Verifique se as saídas de reflexão são validadas para evitar a manipulação dos mecanismos de autoavaliação por entradas adversárias.
 #10.8.3    Nível: 2    Papel: D/V
 Verifique se a análise de segurança meta-cognitiva identifica vieses potenciais, manipulação ou comprometimento nos processos de raciocínio do agente.
 #10.8.4    Nível: 3    Papel: D/V
 Verifique se os avisos de segurança baseados em reflexão desencadeiam monitoramento aprimorado e fluxos de intervenção humana potenciais.
 #10.8.5    Nível: 3    Papel: D/V
 Verifique se o aprendizado contínuo a partir de reflexões de segurança melhora a detecção de ameaças sem prejudicar a funcionalidade legítima.

---

### 10.9 Evolução & Autoaperfeiçoamento em Segurança

Controles de segurança para sistemas de agentes capazes de auto-modificação e evolução.

 #10.9.1    Nível: 1    Papel: D/V
 Verifique se as capacidades de auto-modificação estão restritas às áreas seguras designadas, com limites de verificação formal.
 #10.9.2    Nível: 2    Papel: D/V
 Verifique se as propostas de evolução passam por avaliação de impacto de segurança antes da implementação.
 #10.9.3    Nível: 2    Papel: D/V
 Verifique se os mecanismos de autoaperfeiçoamento incluem capacidades de reversão com verificação de integridade.
 #10.9.4    Nível: 3    Papel: D/V
 Verifique se a segurança da meta-aprendizagem impede a manipulação adversária de algoritmos de melhoria.
 #10.9.5    Nível: 3    Papel: D/V
 Verifique se o autoaperfeiçoamento recursivo está limitado por restrições formais de segurança, com provas matemáticas de convergência.

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

## 11 Proteção de Privacidade e Gestão de Dados Pessoais

### Objetivo de Controle

Manter garantias de privacidade rigorosas ao longo de todo o ciclo de vida da IA—coleta, treinamento, inferência e resposta a incidentes—de modo que os dados pessoais sejam processados apenas com consentimento claro, escopo mínimo necessário, eliminação comprovável e garantias formais de privacidade.

---

### 11.1 Anonimização e Minimização de Dados

 #11.1.1    Nível: 1    Papel: D/V
 Verifique se os identificadores diretos e quase-identificadores são removidos e hasheados.
 #11.1.2    Nível: 2    Papel: D/V
 Verifique se as auditorias automatizadas medem k-anonimato/l-diversidade e alertam quando os limiares caem abaixo da política.
 #11.1.3    Nível: 2    Papel: V
 Verifique se os relatórios de importância das características do modelo provam que não há vazamento de identificadores além de ε = 0.01 de informação mútua.
 #11.1.4    Nível: 3    Papel: V
 Verifique se as provas formais ou a certificação de dados sintéticos demonstram que o risco de reidentificação é ≤ 0,05 mesmo sob ataques de vinculação.

---

### 11.2 Direito ao Esquecimento e Aplicação da Exclusão de Dados

 #11.2.1    Nível: 1    Papel: D/V
 Verifique se as solicitações de exclusão de dados do titular são propagadas para conjuntos de dados brutos, checkpoints, embeddings, logs e backups dentro dos acordos de nível de serviço com prazo inferior a 30 dias.
 #11.2.2    Nível: 2    Papel: D
 Verifique se as rotinas de "machine-unlearning" re-treinam fisicamente ou aproximam a remoção usando algoritmos certificados de desaprendizado.
 #11.2.3    Nível: 2    Papel: V
 Verifique se a avaliação do modelo sombra comprova que registros esquecidos influenciam menos de 1% das saídas após o desaprendizado.
 #11.2.4    Nível: 3    Papel: V
 Verifique se os eventos de exclusão são registrados de forma imutável e auditáveis para reguladores.

---

### 11.3 Salvaguardas de Privacidade-Diferencial

 #11.3.1    Nível: 2    Papel: D/V
 Verifique se os painéis de contabilização da perda de privacidade emitem alertas quando o ε acumulado ultrapassa os limiares da política.
 #11.3.2    Nível: 2    Papel: V
 Verifique se as auditorias de privacidade de caixa-preta estimam ε̂ dentro de 10% do valor declarado.
 #11.3.3    Nível: 3    Papel: V
 Verifique se as provas formais cobrem todos os ajustes finos pós-treinamento e embeddings.

---

### 11.4 Limitação de Propósito e Proteção contra a Expansão de Escopo

 #11.4.1    Nível: 1    Papel: D
 Verifique se todos os conjuntos de dados e checkpoints do modelo carregam uma etiqueta de finalidade legível por máquina, alinhada ao consentimento original.
 #11.4.2    Nível: 1    Papel: D/V
 Verifique se os monitores em tempo de execução detectam consultas incompatíveis com o objetivo declarado e acionam a recusa suave.
 #11.4.3    Nível: 3    Papel: D
 Verifique se os portões de política como código bloqueiam a reimplantação de modelos em novos domínios sem revisão DPIA.
 #11.4.4    Nível: 3    Papel: V
 Verifique se provas formais de rastreabilidade mostram que todo o ciclo de vida dos dados pessoais permanece dentro do escopo consentido.

---

### 11.5 Gestão de Consentimento e Rastreamento com Base Legal

 #11.5.1    Nível: 1    Papel: D/V
 Verifique se uma Plataforma de Gestão de Consentimento (PGC) registra o estado de opt-in, a finalidade e o período de retenção por data-subject.
 #11.5.2    Nível: 2    Papel: D
 Verifique se as APIs expõem tokens de consentimento; os modelos devem validar o escopo do token antes da inferência.
 #11.5.3    Nível: 2    Papel: D/V
 Verifique se o consentimento negado ou retirado interrompe os pipelines de processamento dentro de 24 horas.

---

### 11.6 Aprendizado Federado com Controles de Privacidade

 #11.6.1    Nível: 1    Papel: D
 Verifique se as atualizações dos clientes empregam a adição de ruído da privacidade diferencial local antes da agregação.
 #11.6.2    Nível: 2    Papel: D/V
 Verifique se as métricas de treinamento são diferencialmente privadas e nunca revelam a perda de um único cliente.
 #11.6.3    Nível: 2    Papel: V
 Verifique se a agregação resistente a envenenamento (por exemplo, Krum/Trimmed-Mean) está ativada.
 #11.6.4    Nível: 3    Papel: V
 Verifique se as provas formais demonstram que o orçamento total de ε apresenta uma perda de utilidade inferior a 5.

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

## C12 Monitoramento, Registro de Logs e Detecção de Anomalias

### Objetivo de Controle

Esta seção fornece os requisitos para oferecer visibilidade em tempo real e forense sobre o que o modelo e outros componentes de IA veem, fazem e retornam, para que as ameaças possam ser detectadas, triadas e utilizadas para aprendizado.

### C12.1 Registro de Requisição e Resposta

 #12.1.1    Nível: 1    Papel: D/V
 Verifique se todas as entradas do usuário e as respostas do modelo são registradas com metadados apropriados (por exemplo, carimbo de data/hora, ID do usuário, ID de sessão, versão do modelo).
 #12.1.2    Nível: 1    Papel: D/V
 Verifique se os logs estão armazenados em repositórios seguros, com controle de acesso, políticas de retenção adequadas e procedimentos de backup.
 #12.1.3    Nível: 1    Papel: D/V
 Verifique se os sistemas de armazenamento de logs implementam criptografia em repouso e em trânsito para proteger informações sensíveis contidas nos logs.
 #12.1.4    Nível: 1    Papel: D/V
 Verifique se dados sensíveis em prompts e saídas são automaticamente anonimizados ou mascarados antes de registrar nos logs, com regras de anonimização configuráveis para PII (dados de identificação pessoal), credenciais e informações proprietárias.
 #12.1.5    Nível: 2    Papel: D/V
 Verifique se as decisões de políticas e as ações de filtragem de segurança estão registradas com detalhes suficientes para permitir auditoria e depuração dos sistemas de moderação de conteúdo.
 #12.1.6    Nível: 2    Papel: D/V
 Verifique se a integridade do log está protegida por meio de, por exemplo, assinaturas criptográficas ou armazenamento de apenas gravação.

---

### C12.2 Detecção e Alerta de Abuso

 #12.2.1    Nível: 1    Papel: D/V
 Verifique se o sistema detecta e emite alertas sobre padrões de jailbreak conhecidos, tentativas de injeção de prompt e entradas adversárias usando detecção baseada em assinaturas.
 #12.2.2    Nível: 1    Papel: D/V
 Verifique se o sistema se integra às plataformas SIEM existentes usando formatos de log padrão e protocolos.
 #12.2.3    Nível: 2    Papel: D/V
 Verifique se eventos de segurança enriquecidos incluem contexto específico de IA, como identificadores de modelo, pontuações de confiança e decisões do filtro de segurança.
 #12.2.4    Nível: 2    Papel: D/V
 Verifique se a detecção de anomalias comportamentais identifica padrões de conversa incomuns, tentativas excessivas de reenvio ou comportamentos de sondagem sistemáticos.
 #12.2.5    Nível: 2    Papel: D/V
 Verifique se os mecanismos de alerta em tempo real notificam as equipes de segurança quando são detectadas violações potenciais de políticas ou tentativas de ataque.
 #12.2.6    Nível: 2    Papel: D/V
 Verifique se as regras personalizadas estão incluídas para detectar padrões de ameaça específicos de IA, incluindo tentativas coordenadas de jailbreak, campanhas de injeção de prompts e ataques de extração de modelos.
 #12.2.7    Nível: 3    Papel: D/V
 Verifique se os fluxos de resposta a incidentes automatizados podem isolar modelos comprometidos, bloquear usuários mal-intencionados e escalar eventos de segurança críticos.

---

### C12.3 Detecção de deriva do modelo

 #12.3.1    Nível: 1    Papel: D/V
 Verifique se o sistema rastreia métricas básicas de desempenho, como precisão, pontuações de confiança, latência e taxas de erro, ao longo de versões do modelo e de períodos de tempo.
 #12.3.2    Nível: 2    Papel: D/V
 Verifique se os alertas automáticos são acionados quando as métricas de desempenho excedem limiares de degradação predefinidos ou se desviam significativamente das linhas de base.
 #12.3.3    Nível: 2    Papel: D/V
 Verifique se os monitores de detecção de alucinações identificam e sinalizam situações em que as saídas do modelo contêm informações factualmente incorretas, inconsistentes ou fabricadas.

---

### C12.4 Telemetria de Desempenho e Comportamento

 #12.4.1    Nível: 1    Papel: D/V
 Verifique se as métricas operacionais, incluindo a latência de requisições, o consumo de tokens, o uso de memória e a taxa de transferência, são coletadas e monitoradas continuamente.
 #12.4.2    Nível: 1    Papel: D/V
 Verifique se as taxas de sucesso e de falha são acompanhadas pela categorização dos tipos de erro e de suas causas raízes.
 #12.4.3    Nível: 2    Papel: D/V
 Verifique se o monitoramento de utilização de recursos inclui o uso de GPU/CPU, consumo de memória e requisitos de armazenamento, com alertas para violações de limites.

---

### C12.5 Planejamento e Execução da Resposta a Incidentes de IA

 #12.5.1    Nível: 1    Papel: D/V
 Verifique se os planos de resposta a incidentes abordam especificamente eventos de segurança relacionados à IA, incluindo o comprometimento do modelo, o envenenamento de dados e ataques adversariais.
 #12.5.2    Nível: 2    Papel: D/V
 Verifique se as equipes de resposta a incidentes têm acesso a ferramentas forenses específicas de IA e conhecimentos especializados em IA para investigar o comportamento do modelo e os vetores de ataque.
 #12.5.3    Nível: 3    Papel: D/V
 Verifique se a análise pós-incidente inclui considerações sobre o re-treinamento do modelo, atualizações dos filtros de segurança e a integração das lições aprendidas aos controles de segurança.

---

### C12.5 Detecção de Degradação de Desempenho da IA

Monitorar e detectar a degradação do desempenho e da qualidade do modelo de IA ao longo do tempo.

 #12.5.1    Nível: 1    Papel: D/V
 Verifique se a acurácia do modelo, a precisão, a sensibilidade e as pontuações F1 são monitoradas continuamente e comparadas com os limiares de referência.
 #12.5.2    Nível: 1    Papel: D/V
 Verifique se a detecção de deriva de dados monitora alterações na distribuição de entrada que possam afetar o desempenho do modelo.
 #12.5.3    Nível: 2    Papel: D/V
 Verifique se a detecção de deriva de conceito identifica mudanças na relação entre as entradas e as saídas esperadas.
 #12.5.4    Nível: 2    Papel: D/V
 Verifique se a degradação de desempenho aciona alertas automatizados e inicia fluxos de re-treinamento de modelos ou fluxos de substituição de modelos.
 #12.5.5    Nível: 3    Papel: V
 Verifique se a análise de causa raiz da degradação correlaciona as quedas de desempenho com alterações de dados, problemas de infraestrutura ou fatores externos.

---

### C12.6 Visualização de DAG e Segurança do Fluxo de Trabalho

Proteja os sistemas de visualização de fluxos de trabalho contra vazamento de informações e ataques de manipulação.

 #12.6.1    Nível: 1    Papel: D/V
 Verifique se os dados de visualização do DAG são sanitizados para remover informações sensíveis antes do armazenamento ou da transmissão.
 #12.6.2    Nível: 1    Papel: D/V
 Verifique se os controles de acesso à visualização do fluxo de trabalho garantem que apenas usuários autorizados possam visualizar os caminhos de decisão do agente e as trilhas de raciocínio.
 #12.6.3    Nível: 2    Papel: D/V
 Verifique se a integridade dos dados de DAG está protegida por assinaturas criptográficas e mecanismos de armazenamento à prova de adulteração.
 #12.6.4    Nível: 2    Papel: D/V
 Verifique se os sistemas de visualização de fluxos de trabalho implementam validação de entrada para prevenir ataques de injeção por meio de dados de nó ou de aresta manipulados.
 #12.6.5    Nível: 3    Papel: D/V
 Verifique se as atualizações em tempo real de DAGs estão sujeitas à limitação de taxa e são validadas para evitar ataques de negação de serviço em sistemas de visualização.

---

### C12.7 Monitoramento Proativo do Comportamento de Segurança

Detecção e prevenção de ameaças à segurança por meio da análise proativa do comportamento de agentes.

 #12.7.1    Nível: 1    Papel: D/V
 Verifique se os comportamentos de agentes proativos são validados em termos de segurança antes da execução com integração de avaliação de risco.
 #12.7.2    Nível: 2    Papel: D/V
 Verifique se os gatilhos de iniciativa autônoma incluem avaliação do contexto de segurança e avaliação do panorama de ameaças.
 #12.7.3    Nível: 2    Papel: D/V
 Verifique se os padrões de comportamento proativo são analisados para identificar implicações de segurança potenciais e consequências não intencionais.
 #12.7.4    Nível: 3    Papel: D/V
 Verifique se ações proativas de segurança críticas exigem cadeias de aprovação explícitas com trilhas de auditoria.
 #12.7.5    Nível: 3    Papel: D/V
 Verifique se a detecção de anomalias comportamentais identifica desvios nos padrões de agentes proativos que possam indicar comprometimento.

---

### Referências

NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3
ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6
EU AI Act — Article 12, 13, 16 and 19 on Logging and Record-keeping

## C13 Supervisão Humana, Prestação de Contas e Governança

### Objetivo de Controle

Este capítulo fornece requisitos para manter supervisão humana e cadeias de responsabilização claras em sistemas de IA, assegurando explicabilidade, transparência e governança ética ao longo do ciclo de vida da IA.

---

### C13.1 Kill-Switch & Mecanismos de Anulação

Forneça caminhos de desligamento ou de reversão quando for observado um comportamento inseguro do sistema de IA.

 #13.1.1    Nível: 1    Papel: D/V
 Verifique se existe um mecanismo de interruptor de desligamento manual para interromper imediatamente a inferência do modelo de IA e as saídas.
 #13.1.2    Nível: 1    Papel: D
 Verifique se os controles de substituição são acessíveis apenas ao pessoal autorizado.
 #13.1.3    Nível: 3    Papel: D/V
 Verifique se os procedimentos de reversão podem reverter para versões anteriores do modelo ou operações safe-mode.
 #13.1.4    Nível: 3    Papel: V
 Verifique se os mecanismos de sobrescrita são testados regularmente.

---

### C13.2 Pontos de Verificação de Decisão com Intervenção Humana

Exigir aprovações humanas quando os montantes em jogo excederem os limites de risco predefinidos.

 #13.2.1    Nível: 1    Papel: D/V
 Verifique se as decisões de IA de alto risco exigem aprovação humana explícita antes da execução.
 #13.2.2    Nível: 1    Papel: D
 Verifique se os limiares de risco estão claramente definidos e acionam automaticamente fluxos de trabalho de revisão humana.
 #13.2.3    Nível: 2    Papel: D
 Verifique se as decisões sensíveis ao tempo têm procedimentos de contingência quando não for possível obter a aprovação humana dentro dos prazos exigidos.
 #13.2.4    Nível: 3    Papel: D/V
 Verifique se os procedimentos de escalonamento definem níveis de autoridade claros para diferentes tipos de decisão ou categorias de risco, se aplicável.

---

### C13.3 Cadeia de Responsabilidade e Auditabilidade

Registre as ações do operador e as decisões do modelo.

 #13.3.1    Nível: 1    Papel: D/V
 Verifique se todas as decisões do sistema de IA e as intervenções humanas são registradas com carimbos de data e hora, identidades dos usuários e a justificativa da decisão.
 #13.3.2    Nível: 2    Papel: D
 Verifique se os logs de auditoria não podem ser adulterados e inclua mecanismos de verificação de integridade.

---

### C13.4 Explainable-AI Técnicas

Importância de características superficiais, contra-factuais e explicações locais.

 #13.4.1    Nível: 1    Papel: D/V
 Verifique se os sistemas de IA fornecem explicações básicas para suas decisões em formato legível por humanos.
 #13.4.2    Nível: 2    Papel: V
 Verifique se a qualidade da explicação é validada por meio de estudos de avaliação humana e de métricas.
 #13.4.3    Nível: 3    Papel: D/V
 Verifique se as pontuações de importância de características ou métodos de atribuição (SHAP, LIME, etc.) estão disponíveis para decisões críticas.
 #13.4.4    Nível: 3    Papel: V
 Verifique se as explicações contrafactuais mostram como as entradas poderiam ser modificadas para alterar os desfechos, se for aplicável ao caso de uso e ao domínio.

---

### C13.5 Cartões de Modelo e Divulgações de Uso

Manter fichas de modelo para uso pretendido, métricas de desempenho e considerações éticas.

 #13.5.1    Nível: 1    Papel: D
 Verifique se os cartões de modelo documentam os casos de uso pretendidos, limitações e modos de falha conhecidos.
 #13.5.2    Nível: 1    Papel: D/V
 Verifique se as métricas de desempenho para diferentes casos de uso aplicáveis são divulgadas.
 #13.5.3    Nível: 2    Papel: D
 Verifique que as considerações éticas, avaliações de viés, avaliações de equidade, características dos dados de treinamento e limitações conhecidas dos dados de treinamento estejam documentadas e atualizadas regularmente.
 #13.5.4    Nível: 2    Papel: D/V
 Verifique se os cartões de modelo possuem controle de versão e são mantidos ao longo do ciclo de vida do modelo com rastreamento de alterações.

---

### C13.6 Quantificação da Incerteza

Propagar pontuações de confiança ou medidas de entropia nas respostas.

 #13.6.1    Nível: 1    Papel: D
 Verifique se os sistemas de IA fornecem pontuações de confiança ou medidas de incerteza juntamente com as suas saídas.
 #13.6.2    Nível: 2    Papel: D/V
 Verifique se os limiares de incerteza acionam revisão humana adicional ou caminhos de decisão alternativos.
 #13.6.3    Nível: 2    Papel: V
 Verifique se os métodos de quantificação de incerteza estão calibrados e validados com os dados de referência.
 #13.6.4    Nível: 3    Papel: D/V
 Verifique se a propagação da incerteza é mantida ao longo de fluxos de trabalho de IA de várias etapas.

---

### C13.7 Relatórios de Transparência Voltados ao Usuário

Fornecer divulgações periódicas sobre incidentes, deriva de dados e uso de dados.

 #13.7.1    Nível: 1    Papel: D/V
 Verifique se as políticas de uso de dados e as práticas de gestão do consentimento do usuário são comunicadas de forma clara às partes interessadas.
 #13.7.2    Nível: 2    Papel: D/V
 Verifique se as avaliações de impacto de IA são realizadas e se os resultados estão incluídos nos relatórios.
 #13.7.3    Nível: 2    Papel: D/V
 Verifique se os relatórios de transparência, publicados regularmente, divulgam incidentes de IA e métricas operacionais com detalhes razoáveis.

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

This glossário abrangente fornece definições de termos-chave de IA, ML e segurança usados ao longo do AISVS para garantir clareza e entendimento comum.

Exemplo adversarial: Uma entrada cuidadosamente elaborada para fazer com que um modelo de IA cometa um erro, muitas vezes por meio de perturbações sutis imperceptíveis aos humanos.
​
Robustez adversarial – A robustez adversarial na IA refere-se à capacidade de um modelo de manter seu desempenho e resistir a ser enganado ou manipulado por entradas intencionalmente elaboradas e maliciosas, projetadas para causar erros.
​
Agente – Agentes de IA são sistemas de software que usam IA para perseguir objetivos e realizar tarefas em nome dos usuários. Eles demonstram raciocínio, planejamento e memória e têm um nível de autonomia para tomar decisões, aprender e adaptar-se.
​
IA agentiva: sistemas de IA que podem operar com certo grau de autonomia para alcançar objetivos, muitas vezes tomando decisões e agindo sem intervenção humana direta.
​
Controle de Acesso Baseado em Atributos (ABAC): Um paradigma de controle de acesso no qual as decisões de autorização são baseadas em atributos do usuário, do recurso, da ação e do ambiente, avaliados no momento da consulta.
​
Ataque de porta dos fundos: Um tipo de ataque de envenenamento de dados no qual o modelo é treinado para responder de uma forma específica a certos gatilhos, comportando-se de forma normal caso contrário.
​
Viés: Erros sistemáticos nas saídas de modelos de IA que podem levar a resultados injustos ou discriminatórios para certos grupos ou em contextos específicos.
​
Exploração de vieses: Uma técnica de ataque que aproveita vieses conhecidos em modelos de IA para manipular saídas ou resultados.
​
Cedar: a linguagem de políticas e o motor da Amazon para permissões granulares usadas na implementação de ABAC para sistemas de IA.
​
Cadeia de raciocínio: uma técnica para melhorar o raciocínio em modelos de linguagem, gerando etapas intermediárias de raciocínio antes de produzir uma resposta final.
​
Disjuntores: Mecanismos que interrompem automaticamente as operações do sistema de IA quando limites de risco específicos são excedidos.
​
Vazamento de Dados: Exposição não intencional de informações sensíveis por meio das saídas ou do comportamento de modelos de IA.
​
Envenenamento de dados: A corrupção deliberada de dados de treinamento para comprometer a integridade do modelo, muitas vezes para instalar portas dos fundos ou degradar o desempenho.
​
Privacidade Diferencial – A privacidade diferencial é um arcabouço matematicamente rigoroso para divulgar informações estatísticas sobre conjuntos de dados, mantendo a privacidade dos titulares de dados. Isso permite que o detentor dos dados compartilhe padrões agregados do grupo, ao mesmo tempo em que limita as informações que são divulgadas sobre indivíduos específicos.
​
Embeddings: Representações vetoriais densas de dados (texto, imagens, etc.) que capturam o significado semântico em um espaço de alta dimensão.
​
Explicabilidade – A explicabilidade na IA é a capacidade de um sistema de IA de fornecer razões compreensíveis para suas decisões e previsões, oferecendo insights sobre seu funcionamento interno.
​
IA explicável (XAI): sistemas de IA projetados para fornecer explicações compreensíveis por humanos para suas decisões e comportamentos, por meio de várias técnicas e estruturas.
​
Aprendizado Federado: uma abordagem de aprendizado de máquina na qual modelos são treinados em vários dispositivos descentralizados que possuem amostras de dados locais, sem compartilhar os dados em si.
​
Barreiras de proteção: Restrições implementadas para impedir que sistemas de IA produzam saídas prejudiciais, tendenciosas ou de outra forma indesejáveis.
​
Alucinação – Uma alucinação de IA refere-se a um fenômeno no qual um modelo de IA gera informações incorretas ou enganosas que não se baseiam em seus dados de treinamento nem na realidade dos fatos.
​
Humano-no-Loop (HITL): Sistemas projetados para exigir supervisão humana, verificação ou intervenção em pontos cruciais de decisão.
​
Infraestrutura como Código (IaC): Gerenciar e provisionar infraestrutura por meio de código, em vez de processos manuais, permitindo o escaneamento de segurança e implantações consistentes.
​
Jailbreak: Técnicas usadas para contornar as barreiras de segurança em sistemas de IA, particularmente em grandes modelos de linguagem, para produzir conteúdo proibido.
​
Princípio do menor privilégio: o princípio de segurança que consiste em conceder apenas os direitos de acesso mínimos necessários para usuários e processos.
​
LIME (Explicações Locais Interpretáveis e Independentes do Modelo): uma técnica para explicar as previsões de qualquer classificador de aprendizado de máquina, aproximando-o localmente com um modelo interpretável.
​
Ataque de inferência de pertencimento: um ataque cuja finalidade é determinar se um ponto de dados específico foi utilizado para treinar um modelo de aprendizado de máquina.
​
MITRE ATLAS: Panorama de Ameaças Adversariais para Sistemas de Inteligência Artificial; uma base de conhecimento de táticas e técnicas adversariais contra sistemas de inteligência artificial.
​
Cartão de Modelo – É um documento que fornece informações padronizadas sobre o desempenho de um modelo de IA, suas limitações, usos pretendidos e considerações éticas, para promover transparência e o desenvolvimento responsável de IA.
​
Extração de Modelo: um atacante faz consultas repetidas a um modelo-alvo para criar uma cópia funcionalmente semelhante sem autorização.
​
Inversão de Modelo: Um ataque que tenta reconstruir os dados de treinamento analisando as saídas do modelo.
​
Gestão do Ciclo de Vida de Modelos – Gestão do Ciclo de Vida de Modelos de IA é o processo de supervisionar todas as fases da existência de um modelo de IA, incluindo seu design, desenvolvimento, implantação, monitoramento, manutenção e aposentadoria eventual, para garantir que ele permaneça eficaz e alinhado com os objetivos.
​
Envenenamento de Modelo: Introduzir vulnerabilidades ou portas dos fundos diretamente em um modelo durante o processo de treinamento.
​
Roubo/Extração de Modelo: Extrair uma cópia ou aproximação de um modelo proprietário por meio de consultas repetidas.
​
Sistema multiagente: Um sistema composto por múltiplos agentes de IA que interagem entre si, cada um com capacidades e objetivos potencialmente diferentes.
​
OPA (Open Policy Agent): um motor de políticas de código aberto que permite a execução unificada de políticas em toda a pilha de tecnologia.
​
Aprendizado de Máquina com Privacidade Preservada (PPML): Técnicas e métodos para treinar e implantar modelos de Aprendizado de Máquina, protegendo a privacidade dos dados de treinamento.
​
Injeção de Prompt: Um ataque em que instruções maliciosas são inseridas nas entradas para contornar o comportamento pretendido do modelo.
​
RAG (Geração Aumentada por Recuperação): Uma técnica que aprimora modelos de linguagem de grande escala ao recuperar informações relevantes de fontes externas de conhecimento antes de gerar uma resposta.
​
Red-Teaming: a prática de testar ativamente sistemas de IA simulando ataques adversários para identificar vulnerabilidades.
​
SBOM (Lista de Materiais de Software): Um registro formal contendo os detalhes e as relações da cadeia de suprimentos de vários componentes usados na construção de software ou modelos de IA.
​
SHAP (SHapley Additive exPlanations): Uma abordagem teórica de jogos para explicar a saída de qualquer modelo de aprendizado de máquina, calculando a contribuição de cada característica para a previsão.
​
Ataque à Cadeia de Suprimentos: Comprometer um sistema ao mirar elementos menos-seguros em sua cadeia de suprimentos, como bibliotecas de terceiros, conjuntos de dados ou modelos pré-treinados.
​
Aprendizagem por Transferência: Uma técnica na qual um modelo desenvolvido para uma tarefa é reutilizado como ponto de partida para um modelo em uma segunda tarefa.
​
Banco de Dados Vetoriais: Um banco de dados especializado projetado para armazenar vetores de alta dimensão (embeddings) e realizar buscas de similaridade eficientes.
​
Escaneamento de Vulnerabilidades: ferramentas automatizadas que identificam vulnerabilidades de segurança conhecidas em componentes de software, incluindo frameworks de IA e dependências.
​
Marca d'água: Técnicas para incorporar marcadores imperceptíveis em conteúdo gerado por IA para rastrear sua origem ou detectar a geração por IA.
​
Vulnerabilidade zero-day: uma vulnerabilidade previamente desconhecida que os atacantes podem explorar antes que os desenvolvedores criem e lancem um patch.

## Apêndice B: Referências

### TODO

## Apêndice C: Governança de Segurança da IA e Documentação

### Objetivo

Este apêndice fornece requisitos fundamentais para estabelecer estruturas organizacionais, políticas e processos para governar a segurança de IA ao longo do ciclo de vida do sistema.

---

### AC.1 Adoção do Quadro de Gestão de Riscos de IA

Fornecer um arcabouço formal para identificar, avaliar e mitigar riscos específicos de IA ao longo do ciclo de vida do sistema.

 #AC.1.1    Nível: 1    Papel: D/V
 Verifique se uma metodologia de avaliação de risco específica para IA está documentada e implementada.
 #AC.1.2    Nível: 2    Papel: D
 Verifique se as avaliações de risco são realizadas em pontos-chave ao longo do ciclo de vida da IA e antes de mudanças significativas.
 #AC.1.3    Nível: 3    Papel: D/V
 Verifique se o quadro de gestão de riscos está alinhado com padrões estabelecidos (por exemplo, NIST AI RMF).

---

### AC.2 Política de Segurança de IA e Procedimentos

Defina e imponha padrões organizacionais para o desenvolvimento seguro de IA, implantação e operação.

 #AC.2.1    Nível: 1    Papel: D/V
 Verifique se existem políticas de segurança de IA documentadas.
 #AC.2.2    Nível: 2    Papel: D
 Verifique se as políticas são revistas e atualizadas pelo menos anualmente e após mudanças significativas no panorama de ameaças.
 #AC.2.3    Nível: 3    Papel: D/V
 Verifique se as políticas abrangem todas as categorias AISVS e os requisitos regulatórios aplicáveis.

---

### AC.3 Papéis e Responsabilidades para a Segurança da IA

Estabelecer uma responsabilidade clara pela segurança de IA em toda a organização.

 #AC.3.1    Nível: 1    Papel: D/V
 Verifique se as funções e responsabilidades de segurança da IA estão documentadas.
 #AC.3.2    Nível: 2    Papel: D
 Verifique se as pessoas responsáveis possuem a devida expertise em segurança.
 #AC.3.3    Nível: 3    Papel: D/V
 Verifique se foi criado um comitê de ética em IA ou um conselho de governança para sistemas de IA de alto‑risco.

---

### AC.4 Aplicação das Diretrizes Éticas de IA

Garanta que os sistemas de IA operem de acordo com princípios éticos estabelecidos.

 #AC.4.1    Nível: 1    Papel: D/V
 Verifique se existem diretrizes éticas para o desenvolvimento e implantação de IA.
 #AC.4.2    Nível: 2    Papel: D
 Verifique se existem mecanismos para detectar e relatar violações éticas.
 #AC.4.3    Nível: 3    Papel: D/V
 Verifique se revisões éticas regulares de sistemas de IA implantados são realizadas.

---

### AC.5 Monitoramento da Conformidade Regulatória da IA

Mantenha a conscientização e a conformidade com as regulamentações de IA em constante evolução.

 #AC.5.1    Nível: 1    Papel: D/V
 Verifique se existem processos para identificar as regulamentações de IA aplicáveis.
 #AC.5.2    Nível: 2    Papel: D
 Verifique se a conformidade com todos os requisitos regulatórios está sendo avaliada.
 #AC.5.3    Nível: 3    Papel: D/V
 Verifique se as mudanças regulatórias acionam revisões e atualizações oportunas nos sistemas de IA.

### AC.6 Governança, Documentação e Processo de Dados de Treinamento

 #1.1.2    Nível: 1    Papel: D/V
 Certifique-se de que apenas conjuntos de dados avaliados quanto à qualidade, representatividade, fornecimento ético e conformidade com licenças sejam permitidos, reduzindo os riscos de envenenamento, viés embutido e violação de propriedade intelectual.
 #1.1.5    Nível: 2    Papel: D/V
 Verifique se a qualidade da rotulagem/anotação é assegurada por meio de verificações cruzadas por revisores ou por consenso.
 #1.1.6    Nível: 2    Papel: D/V
 Verifique se 'data cards' ou 'datasheets for datasets' devem ser mantidos para conjuntos de dados de treinamento significativos, detalhando características, motivações, composição, processos de coleta, pré-processamento e usos recomendados/desencorajados.
 #1.3.2    Nível: 2    Papel: D/V
 Verifique se os vieses identificados são mitigados por meio de estratégias documentadas, como reequilíbrio de dados, aumento de dados direcionado, ajustes algorítmicos (por exemplo, pré-processamento, in-processing, pós-processamento) ou reponderação, e se o impacto da mitigação na equidade e no desempenho geral do modelo é avaliado.
 #1.3.3    Nível: 2    Papel: D/V
 Verifique se as métricas de equidade pós-treinamento são avaliadas e documentadas.
 #1.3.4    Nível: 3    Papel: D/V
 Verifique se uma política de gestão do viés do ciclo de vida atribui responsáveis e cadência de revisão.
 #1.4.1    Nível: 2    Papel: D/V
 Verifique se a qualidade da rotulagem/anotação é assegurada por meio de diretrizes claras, conferências entre revisores, mecanismos de consenso (por exemplo, monitoramento do acordo entre anotadores) e processos definidos para resolver discrepâncias.
 #1.4.4    Nível: 3    Papel: D/V
 Verifique que os rótulos críticos para a segurança, a proteção ou a equidade (por exemplo, a identificação de conteúdo tóxico, achados médicos críticos) recebam revisão dupla independente obrigatória ou verificação robusta equivalente.
 #1.4.6    Nível: 2    Papel: D/V
 Verifique se os guias de rotulagem e as instruções são abrangentes, com controle de versão e revisadas por pares.
 #1.4.6    Nível: 2    Papel: D/V
 Verifique se os esquemas de dados para rótulos estão claramente definidos e versionados.
 #1.3.1    Nível: 1    Papel: D/V
 Verifique se os conjuntos de dados são analisados quanto ao desequilíbrio representacional e aos vieses potenciais em atributos protegidos por lei (por exemplo, raça, gênero, idade) e a outras características eticamente sensíveis relevantes ao domínio de aplicação do modelo (por exemplo, status socioeconômico, localização).
 #1.5.3    Nível: 2    Papel: V
 Verifique se as checagens manuais por especialistas do domínio abrangem uma amostra estatisticamente significativa (por exemplo, ≥1% ou 1.000 amostras, o que for maior, ou conforme determinado pela avaliação de risco) para identificar questões sutis de qualidade que não são detectadas pela automação.
 #1.8.4    Nível: 2    Papel: D/V
 Verifique se fluxos de rotulagem terceirizados ou realizados por crowdsourcing incluem salvaguardas técnicas/procedimentais para garantir a confidencialidade e a integridade dos dados, a qualidade dos rótulos e evitar o vazamento de dados.
 #1.5.4    Nível: 2    Papel: D/V
 Verifique se as etapas de remediação são anexadas aos registros de proveniência.
 #1.6.2    Nível: 2    Papel: D/V
 Verifique se as amostras sinalizadas acionam a revisão manual antes do treinamento.
 #1.6.3    Nível: 2    Papel: V
 Verifique se os resultados alimentam o dossiê de segurança do modelo e informam a inteligência de ameaças em andamento.
 #1.6.4    Nível: 3    Papel: D/V
 Verifique se a lógica de detecção é atualizada com novas informações de inteligência sobre ameaças.
 #1.6.5    Nível: 3    Papel: D/V
 Verifique se os pipelines de aprendizado online monitoram a deriva de distribuição.
 #1.7.1    Nível: 1    Papel: D/V
 Verifique se os fluxos de exclusão de dados de treinamento purgam dados primários e derivados e avaliam o impacto no modelo, e que o impacto nos modelos afetados seja avaliado e, se necessário, tratado (por meio de retreinamento ou recalibração).
 #1.7.2    Nível: 2    Papel: D
 Verifique se existem mecanismos para acompanhar e respeitar o escopo e o status do consentimento do usuário (e das retiradas do consentimento) para dados utilizados no treinamento, e se o consentimento é validado antes de os dados serem incorporados a novos processos de treinamento ou atualizações significativas do modelo.
 #1.7.3    Nível: 2    Papel: V
 Verifique se os fluxos de trabalho são testados anualmente e registrados.
 #1.8.1    Nível: 2    Papel: D/V
 Verifique se os fornecedores de dados de terceiros, incluindo provedores de modelos pré-treinados e conjuntos de dados externos, passam por diligência devida em segurança, privacidade, obtenção ética e qualidade dos dados antes de seus dados ou modelos serem integrados.
 #1.8.2    Nível: 1    Papel: D
 Verifique se as transferências externas utilizam TLS/autenticação e verificações de integridade.
 #1.8.3    Nível: 2    Papel: D/V
 Verifique se fontes de dados de alto risco (por exemplo, conjuntos de dados de código aberto com proveniência desconhecida, fornecedores não verificados) recebem escrutínio aprimorado, como análise em sandbox, verificações extensas de qualidade e viés, e detecção de envenenamento direcionada, antes de serem utilizadas em aplicações sensíveis.
 #1.8.4    Nível: 3    Papel: D/V
 Verifique que os modelos pré-treinados obtidos de terceiros sejam avaliados quanto a vieses embutidos, potenciais portas traseiras, integridade de sua arquitetura e a proveniência de seus dados de treinamento originais, antes do ajuste fino ou da implantação.
 #1.5.3    Nível: 2    Papel: D/V
 Verifique se, caso seja utilizado o treinamento adversarial, a geração, a gestão e o versionamento de conjuntos de dados adversariais estejam documentados e controlados.
 #1.5.3    Nível: 3    Papel: D/V
 Verifique se o impacto do treinamento de robustez adversarial no desempenho do modelo (em relação tanto a entradas limpas quanto adversárias) e nas métricas de equidade é avaliado, documentado e monitorado.
 #1.5.4    Nível: 3    Papel: D/V
 Verifique se as estratégias de treinamento adversarial e de robustez são periodicamente revistas e atualizadas para enfrentar técnicas de ataque adversariais em evolução.
 #1.4.2    Nível: 2    Papel: D/V
 Verifique se os conjuntos de dados com falha estão em quarentena com registros de auditoria.
 #1.4.3    Nível: 2    Papel: D/V
 Verifique se as portas de qualidade bloqueiam conjuntos de dados de qualidade inferior, salvo exceções aprovadas.
 #1.11.2    Nível: 2    Papel: D/V
 Verifique se o processo de geração, os parâmetros e o uso pretendido dos dados sintéticos estão documentados.
 #1.11.3    Nível: 2    Papel: D/V
 Verifique se os dados sintéticos passaram por avaliação de risco quanto a viés, vazamento de privacidade e questões de representatividade antes de serem usados no treinamento.
 #1.12.3    Nível: 2    Papel: D/V
 Verifique se os alertas são gerados para eventos de acesso suspeitos e são investigados prontamente.
 #1.13.1    Nível: 1    Papel: D/V
 Verifique se os períodos de retenção explícitos estão definidos para todos os conjuntos de dados de treinamento.
 #1.13.2    Nível: 2    Papel: D/V
 Verifique se os conjuntos de dados são expirados automaticamente, excluídos ou analisados para exclusão ao final de seu ciclo de vida.
 #1.13.3    Nível: 2    Papel: D/V
 Verifique se as ações de retenção e exclusão são registradas e auditáveis.
 #1.14.1    Nível: 2    Papel: D/V
 Verifique se os requisitos de residência de dados e de transferência transfronteiriça são identificados e aplicados para todos os conjuntos de dados.
 #1.14.2    Nível: 2    Papel: D/V
 Verifique se as regulamentações específicas do setor (por exemplo, saúde, finanças) são identificadas e abordadas no tratamento de dados.
 #1.14.3    Nível: 2    Papel: D/V
 Verifique se a conformidade com as leis de privacidade relevantes (por exemplo, GDPR, CCPA) está documentada e revisada regularmente.
 #1.16.1    Nível: 2    Papel: D/V
 Verifique se existem mecanismos para responder a solicitações do titular dos dados de acesso, retificação, restrição do tratamento ou objeção.
 #1.16.2    Nível: 2    Papel: D/V
 Verifique se as solicitações são registradas, acompanhadas e atendidas dentro dos prazos legais obrigatórios.
 #1.16.3    Nível: 2    Papel: D/V
 Verifique se os processos relacionados aos direitos do titular dos dados são testados e revisados regularmente para garantir a eficácia.
 #1.17.1    Nível: 2    Papel: D/V
 Verifique se uma análise de impacto é realizada antes de atualizar ou substituir uma versão do conjunto de dados, abrangendo o desempenho do modelo, equidade e conformidade.
 #1.17.2    Nível: 2    Papel: D/V
 Verifique se os resultados da análise de impacto estão documentados e revisados pelas partes interessadas relevantes.
 #1.17.3    Nível: 2    Papel: D/V
 Verifique se existem planos de reversão caso as novas versões introduzam riscos inaceitáveis ou regressões.
 #1.18.1    Nível: 2    Papel: D/V
 Verifique se todo o pessoal envolvido na anotação de dados passou por verificação de antecedentes e recebeu treinamento em segurança de dados e privacidade.
 #1.18.2    Nível: 2    Papel: D/V
 Verifique se todo o pessoal de anotação assina acordos de confidencialidade e de não divulgação.
 #1.18.3    Nível: 2    Papel: D/V
 Verifique se as plataformas de anotação aplicam controles de acesso e monitoram ameaças internas.

#### Referências

NIST AI Risk Management Framework 1.0
ISO/IEC 42001:2023 — AI Management Systems Requirements
ISO/IEC 23894:2023 — Artificial Intelligence — Guidance on Risk Management
EU Artificial Intelligence Act — Regulation (EU) 2024/1689
ISO/IEC 24029‑2:2023 — Robustness of Neural Networks — Methodology for Formal Methods

## Apêndice D: Governança e Verificação de Codificação Segura Assistida por IA

### Objetivo

Este capítulo define controles organizacionais básicos para o uso seguro e eficaz de ferramentas de codificação assistidas por IA durante o desenvolvimento de software, assegurando segurança e rastreabilidade ao longo do Ciclo de Vida de Desenvolvimento de Software (CVDS).

---

### AD.1 Fluxo de Trabalho de Codificação Segura Assistido por IA

Integrar ferramentas de IA ao ciclo de vida de desenvolvimento de software seguro (SSDLC) da organização, sem enfraquecer as barreiras de segurança existentes.

 #AD.1.1    Nível: 1    Papel: D/V
 Verifique se um fluxo de trabalho documentado descreve quando e como as ferramentas de IA podem gerar, refatorar ou revisar código.
 #AD.1.2    Nível: 2    Papel: D
 Verifique se o fluxo de trabalho mapeia para cada fase do SSDLC (design, implementação, revisão de código, testes, implantação).
 #AD.1.3    Nível: 3    Papel: D/V
 Verifique se métricas (por exemplo, densidade de vulnerabilidades, tempo médio de detecção) são coletadas em código gerado por IA e comparadas com linhas de base apenas humanas.

---

### AD.2 Qualificação de Ferramentas de IA e Modelagem de Ameaças

Certifique-se de avaliar ferramentas de codificação de IA quanto às capacidades de segurança, risco e impacto na cadeia de suprimentos antes da adoção.

 #AD.2.1    Nível: 1    Papel: D/V
 Verifique se um modelo de ameaça para cada ferramenta de IA identifica uso indevido, inversão de modelo, vazamento de dados e riscos de cadeia de dependências.
 #AD.2.2    Nível: 2    Papel: D
 Verifique se as avaliações de ferramentas incluem análise estática/dinâmica de quaisquer componentes locais e avaliação de pontos finais SaaS (TLS, autenticação/autorização, registro).
 #AD.2.3    Nível: 3    Papel: D/V
 Verifique se as avaliações seguem um framework reconhecido e são reexecutadas após alterações de versão maiores.

---

### AD.3 Gerenciamento Seguro de Prompt e Contexto

Prevenir o vazamento de segredos, código proprietário e dados pessoais ao criar prompts ou contextos para modelos de IA.

 #AD.3.1    Nível: 1    Papel: D/V
 Verifique se as diretrizes escritas proíbem enviar segredos, credenciais ou dados confidenciais em prompts.
 #AD.3.2    Nível: 2    Papel: D
 Verifique se os controles técnicos (redação do lado do cliente, filtros de contexto aprovados) removem automaticamente artefatos sensíveis.
 #AD.3.3    Nível: 3    Papel: D/V
 Verifique se prompts e respostas são tokenizados, criptografados em trânsito e em repouso, e os períodos de retenção estão em conformidade com a política de data‑classification.

---

### AD.4 Validação de Código IA‑Gerado

Detectar e corrigir vulnerabilidades introduzidas pela saída da IA antes que o código seja mesclado ou implantado.

 #AD.4.1    Nível: 1    Papel: D/V
 Verifique se o código IA-gerado está sempre sujeito à revisão de código por humanos.
 #AD.4.2    Nível: 2    Papel: D
 Verifique se os scanners automatizados (SAST/IAST/DAST) são executados em cada pull request que contenha código AI-gerado e bloqueiam merges com base em descobertas críticas.
 #AD.4.3    Nível: 3    Papel: D/V
 Verifique se os testes de fuzzing diferencial ou testes baseados em propriedades comprovam comportamentos críticos de segurança (por exemplo, validação de entradas, lógica de autorização).

---

### AD.5 Explicabilidade e Traçabilidade de Sugestões de Código

Forneça aos auditores e desenvolvedores insights sobre o motivo pelo qual uma sugestão foi feita e como ela evoluiu.

 #AD.5.1    Nível: 1    Papel: D/V
 Verifique se pares de prompt/resposta são registrados com IDs de commit.
 #AD.5.2    Nível: 2    Papel: D
 Verifique se os desenvolvedores podem exibir citações do modelo (trechos de treinamento, documentação) que apoiam uma sugestão.
 #AD.5.3    Nível: 3    Papel: D/V
 Verifique se os relatórios de explicabilidade são armazenados junto aos artefatos de design e referenciados nas revisões de segurança, em conformidade com os princípios de rastreabilidade da ISO/IEC 42001.

---

### AD.6 Feedback Contínuo e Ajuste Fino do Modelo

Melhorar o desempenho de segurança do modelo ao longo do tempo, evitando deriva negativa.

 #AD.6.1    Nível: 1    Papel: D/V
 Verifique se os desenvolvedores podem sinalizar sugestões inseguras ou não-conformes, e que as sinalizações sejam rastreadas.
 #AD.6.2    Nível: 2    Papel: D
 Verifique se o feedback agregado informa ajuste fino‑periódico ou geração‑aumentada por recuperação com corpora de codificação segura verificados (por exemplo, OWASP Cheat Sheets).
 #AD.6.3    Nível: 3    Papel: D/V
 Verifique que um harness de avaliação em loop‑fechado execute testes de regressão após cada ajuste fino; as métricas de segurança devem atender ou superar as linhas de base anteriores antes da implantação.

---

#### Referências

NIST AI Risk Management Framework 1.0
ISO/IEC 42001:2023 — AI Management Systems Requirements
OWASP Secure Coding Practices — Quick Reference Guide

## Apêndice E: Ferramentas e Frameworks de Exemplo

### Objetivo

Este capítulo fornece exemplos de ferramentas e frameworks que podem apoiar a implementação ou o atendimento de um requisito AISVS específico. Estes não devem ser vistos como recomendações ou endossos pela equipe AISVS ou pelo OWASP GenAI Security Project.

---

### AE.1 Governança de Dados de Treinamento e Gestão de Viés

Ferramentas usadas para análise de dados, governança e gestão de vieses.

 #AE.1.1    Seção: 1.1
 Ferramentas de Inventário de Dados: ferramentas de gerenciamento de inventário de dados como...
 #AE.1.2    Seção: 1.2
 Criptografia-Em-Trânsito Use TLS para aplicações baseadas em HTTPS-based, com ferramentas como OpenSSL e do Python`ssl` biblioteca.

---

### AE.2 Validação de Entrada do Usuário

Ferramentas para lidar com e validar as entradas do usuário.

 #AE.2.1    Seção: 2.1
 Ferramentas de defesa contra injeção de prompt: use ferramentas de guardrail, como o NeMo da NVIDIA ou o Guardrails AI.

---

