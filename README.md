# ☁️ Guia Fundamental Salesforce: Preparação para Especialista

## 🎯 Contexto e Objetivos
O assunto de interesse escolhido para este caderno temático é a **Administração e Arquitetura do Salesforce**, com foco em preparar profissionais para entrevistas de nível especialista. O objetivo principal deste material é transcender o conhecimento operacional de clique (o "como apertar botões") e aprofundar no entendimento estratégico da plataforma (o "porquê" das coisas). Este estudo consolida conceitos avançados que vão desde o modelo de camadas de segurança até integrações complexas, modelagem de dados e governança de *deployments*.

## 📚 Curadoria de Fontes
As fontes utilizadas para compor este caderno foram extraídas das transcrições da série de aulas abertas "Administrador Salesforce: saindo do Zero ao Fundamental", disponibilizadas no canal do YouTube "DVLPRBR" [1-12]. 
* Foram utilizados os episódios 02 ao 13, que cobrem desde segurança, modelagem, automações e relatórios até ferramentas modernas como Agentforce e DevOps Center.

## 🧠 Engenharia de Prompts e "Cicatrizes" (Troubleshooting)

**Objetivo da Interação:** Extrair um resumo focado em entrevistas para nível de especialista, exigindo maturidade técnica em vez de guias de configuração passo a passo.

*   **Prompt Principal Testado:** *"Gostaria que você se comporta-se como um professor de selesforce com diversas certificações e me explica-se resumidamente dos este conteúdo de maneira que eu me prepare para entrevista para vaga de especialistas."*
*   **Resultados e Dificuldades ("Cicatrizes"):** A principal dificuldade na elaboração de prompts sobre Salesforce é que a IA tende a responder com instruções de navegação (ex: "Vá em Setup > Users"). Para contornar isso, o prompt definiu a persona ("professor certificado") e o objetivo final ("entrevista técnica"). 
*   **Raciocínio por trás do Resultado:** Ao ajustar o prompt para esse foco estratégico, a IA organizou a resposta em **pilares arquiteturais**, que representam os temas mais cobrados em avaliações de senioridade. 

---

## 📖 Miniguia de Estudo (Entrega Final)

### 1. Resumos Estruturados do Assunto (Pilares do Especialista)

*   **Segurança e Visibilidade (Modelo de Camadas):** A segurança age como o acesso a um prédio corporativo [13]. O *Nível da Organização* controla horários e IPs [14]. O *Nível do Objeto (OLS)* define permissões de leitura, criação e edição (CRUD) [15]. O *Nível do Registro (RLS)* controla quais registros específicos o usuário pode ver através do OWD, *Role Hierarchy* e Regras de Compartilhamento [16-18]. O *Nível do Campo (FLS)* restringe acesso a campos específicos (ex: score de crédito) mesmo se o usuário acessar o registro [19, 20]. Recomenda-se dar o acesso base mínimo no Perfil e expandi-lo através de *Permission Sets* [21, 22].
*   **Modelagem de Dados:** O relacionamento *Lookup* é flexível e independente; se o registro pai for excluído, o filho permanece [23]. O *Master-Detail* impõe forte dependência: o registro filho herda a visibilidade do pai, sofre exclusão em cascata e permite agregações através de campos *Roll-up Summary* [24-26].
*   **Gestão de Dados:** O *Data Import Wizard* é guiado e recomendado para até 50.000 registros [27]. O *Data Loader* é para grandes volumes (até 150 milhões de registros) e permite exportações, *Hard Deletes* e operações de *Upsert* [28-30]. IDs externos (*External IDs*) são chaves cruciais para atualizações e integrações, evitando dependência exclusiva do ID do Salesforce [31, 32].
*   **Automação e Validação:** O *Flow Builder* é o centro de automação declarativa recomendado (substituindo o antigo *Process Builder*) [33]. *Record-Triggered Flows* podem rodar *Before Save* (para atualizar o próprio registro com rapidez) ou *After Save* (para trabalhar com registros relacionados) [34, 35]. Já as *Validation Rules* não fazem automações, mas bloqueiam o salvamento e garantem a integridade dos dados se a fórmula retornar como "Verdadeiro" [36-38].
*   **Integração:** Integrações leves, mobile e web costumam usar a *REST API* trafegando JSON/XML [39]. Integrações legadas ou *Server-to-Server* frequentemente exigem o contrato formal WSDL via *SOAP API* [40, 41]. Padrões assíncronos incluem o *Platform Events* (evento de negócio definido pelo usuário) e o *Change Data Capture (CDC)* (evento disparado pela mera modificação do registro) [42-44].
*   **Deployments e Governança:** O *Change Set* é nativo, porém não rastreia versões ou históricos avançados e falha a transação inteira se houver erro parcial [45-47]. O moderno *DevOps Center* implementa o conceito de CI/CD para o *low code*, com *branches*, repositório conectado (Git) e rastreabilidade robusta [48-50].
*   **Agentforce e Inteligência Artificial:** O papel do administrador passa a ser governar a IA, definindo os tópicos, ações e instruções (Guardrails) do agente [51-53]. A precisão do Agente é baseada no *Grounding* (ancorar as respostas em dados confiáveis da empresa, como políticas e histórico), sempre mediado pelo *Einstein Trust Layer* para proteção de informações sensíveis [54-56].

### 2. Glossário de Conceitos

*   **OWD (Organization-Wide Default):** Define o nível de acesso base a registros quando o usuário não é o dono [18, 57].
*   **Permission Sets / Groups:** Blocos modulares que servem para conceder permissões e acessos adicionais sem a necessidade de criar múltiplos perfis idênticos [22, 58, 59].
*   **External ID:** Identificador que faz o vínculo (ponte) entre os registros no Salesforce e a numeração do sistema legado durante o Upsert [31, 32].
*   **Roll-up Summary:** Campo exclusivo de relacionamentos Master-Detail que realiza somas, contagens ou retorna o maior/menor valor dos registros filhos no pai [25, 26, 60].
*   **Grounding (Agentforce):** Técnica que disponibiliza a base de dados corporativos e arquivos de conhecimento corretos para que o Agente responda sem alucinar [54, 55, 61].

### 3. Prompts Reutilizáveis para Revisão (Testes de Entrevista)

Copie os prompts abaixo na sua IA de estudo para realizar revisões espaçadas ou simulações antes da entrevista:

1.  *"Estou revisando o modelo de segurança do Salesforce. Crie um cenário prático complexo envolvendo OWD, Role Hierarchy, Sharing Rules e Field-Level Security, e depois me pergunte como eu resolveria um problema de visibilidade de dados nesse cenário."*
2.  *"Explique a diferença técnica entre um Before Save Flow e um After Save Flow. Forneça 2 exemplos práticos de processos de negócios onde seria obrigatório usar After Save ao invés de Before Save."*
3.  *"Atue como um recrutador de DevOps no ecossistema Salesforce. Faça-me 3 perguntas difíceis sobre as limitações dos Change Sets e por que migrar para o DevOps Center."*
4.  *"Quero entender como o administrador cria parâmetros no Agentforce. Descreva 
