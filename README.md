# DesafioDioNotebookLM

☁️ Guia Fundamental Salesforce: Preparação para Especialista
🎯 Contexto e Objetivos
O assunto de interesse escolhido para este caderno temático é a Administração e Arquitetura do Salesforce, com foco em preparar profissionais para entrevistas de nível especialista. O objetivo principal deste material é transcender o conhecimento operacional (o "como apertar botões") e aprofundar no entendimento estratégico e arquitetural da plataforma (o "porquê" das coisas). Este estudo visa consolidar conceitos que vão desde a gestão de usuários e segurança até integrações complexas, modelagem de dados e governança de deployments
.
# 📚 Curadoria de Fontes
As fontes utilizadas para compor este caderno foram extraídas da série de aulas abertas "Administrador Salesforce: saindo do Zero ao Fundamental" do canal DVLPRBR, focadas em formar administradores com visão estratégica:
Vídeo 03 - Segurança e Acesso: Focado em hierarquia, perfis, conjuntos de permissões e controle em nível de registro e campo
.
Vídeo 04 - Gestão de Dados: Cobre importação, exportação e ferramentas de migração de dados (Data Loader, Import Wizard e APIs)
.
Vídeo 05 - Modelagem de Dados: Explora os tipos de relacionamentos (Lookup, Master-Detail) e objetos externos
.
Vídeo 06 - Automação de Processos: Centralizado na evolução para o Flow Builder e os tipos de automação (Screen, Auto-launched, Record-Triggered)
.
Vídeo 10 - Deployment e Governança: Detalha as diferenças entre Change Sets e a transição moderna para o DevOps Center
.
# 🧠 Engenharia de Prompts e "Cicatrizes" (Troubleshooting)
Objetivo da Interação: Extrair um resumo focado em entrevistas para nível de especialista, exigindo maturidade técnica em vez de apenas passos de configuração básica.
Prompt Principal Testado: "Gostaria que você se comporta-se como um professor de selesforce com diversas certificações e me explica-se resumidamente dos este conteúdo de maneira que eu me prepare para entrevista para vaga de especialistas."
Resultados e Dificuldades ("Cicatrizes"): A principal dificuldade na elaboração inicial de prompts sobre Salesforce é que a IA tende a responder com guias de clique (ex: "Vá em Setup > Users"). Para contornar isso, o prompt precisou definir a persona ("professor com diversas certificações") e o objetivo final ("entrevista para vaga de especialista").
Raciocínio por trás do Resultado: Ao ajustar o prompt para esse foco estratégico, a IA organizou a resposta em pilares arquiteturais (Segurança, Modelagem, Qualidade de Dados, Automação, Integração, Analytics e Deploy), que são exatamente os temas cobrados em avaliações de senioridade no mercado.

--------------------------------------------------------------------------------
# 📖 Miniguia de Estudo (Entrega Final)
1. Resumos Estruturados do Assunto (Os 7 Pilares do Especialista)
Pilar 1: Segurança e Visibilidade (O Modelo de Camadas): A segurança não é configurada em um único lugar, é um modelo de camadas
.
Nível da Organização: Controla horários e IPs de login
.
Nível do Objeto (OLS): Define se o usuário pode Criar, Ler, Editar ou Excluir registros do objeto (o CRUD)
. A melhor prática é dar o mínimo de acesso no Perfil e expandir com Permission Sets
.
Nível do Registro (RLS): Controla quais registros específicos o usuário visualiza (OWD, Hierarquia de Papéis e Sharing Rules)
.
Nível do Campo (FLS): Permite ocultar campos sensíveis mesmo que o usuário acesse o registro (ex: esconder CPF do time de vendas)
.
Pilar 2: Modelagem de Dados: O Salesforce utiliza objetos (tabelas) e campos (colunas)
. O especialista entende o impacto dos relacionamentos. O Lookup é flexível e o filho sobrevive se o pai for apagado
. Já o Master-Detail impõe que o filho herde a segurança do pai, possuindo exclusão em cascata e permitindo Roll-up Summary fields
. Objetos Externos exibem dados de sistemas de fora sem consumir o espaço de armazenamento (Data Storage) da organização
.
Pilar 3: Gestão de Dados: Escolher a ferramenta correta é vital. Data Import Wizard é simples, guiado e suporta até 50.000 registros
. O Data Loader é para volumes massivos (até 150 milhões), suportando Export, Upsert e Hard Delete
.
Pilar 4: Automação e Regras de Negócio: O Flow Builder é a ferramenta de automação do presente e futuro (Workflows e Process Builders são legado)
. Podem ser ativados por telas (Screen Flows), em background (Auto-launched) ou mudanças de registros (Record-Triggered)
. Regras de validação servem para qualidade de dados, bloqueando o salvamento se o critério (retornando verdadeiro) indicar uma violação da regra de negócio
.
Pilar 5: Integração (APIs e Eventos): Integrações básicas usam Web-to-Lead ou Email-to-Case
. Integrações complexas usam REST API (leve, JSON/XML para web/mobile) ou SOAP API (formal, baseada em WSDL, excelente para Server-to-Server legado)
. Eventos de plataforma (Platform Events) são mensagens de negócios customizadas em modelo Publish/Subscribe
.
Pilar 6: Relatórios e Dashboards: Servem para transformar dados em decisão
. Existem relatórios Tabulares, Resumidos e Matriz (cruzando dimensões)
. É possível usar Buckets (cestas) para agrupar dados temporariamente sem criar campos no objeto
. Dashboards Dinâmicos renderizam dados baseados no usuário logado (Running User), adaptando-se às permissões de quem visualiza
.
Pilar 7: Governança, Deploy e IA: O básico são os Change Sets, nativos, porém limitados à transações únicas sem controle de versão embutido
. O mercado atual pede DevOps Center e ferramentas como Copado, focadas em controle de versão (Git), rastreabilidade e branches
. Em IA, o Agentforce foca em dar autonomia baseada em Tópicos, Ações e Instruções (Guardrails), exigindo que o Admin configure adequadamente as permissões (Grounding) para evitar alucinações e vazamentos
.
2. Glossário de Conceitos
OWD (Organization-Wide Default): Configuração base que define o nível de acesso padrão de uma organização para os registros quando o usuário não é o proprietário
.
Permission Sets: Blocos modulares usados para estender permissões aos usuários além do seu Perfil base. Não podem ser usados para restringir acessos
.
External ID: Campo utilizado para armazenar identificadores únicos de sistemas externos, fundamental para operações de Upsert através de APIs ou Data Loader para não depender do ID padrão do Salesforce
.
Change Data Capture (CDC): Funcionalidade que notifica sistemas de forma passiva quando um registro é criado, atualizado, excluído ou recuperado, operando quase em tempo real
.
Roll-up Summary: Campo especial disponível apenas na relação Master-Detail, que permite contar, somar, ou encontrar valores máximos e mínimos nos registros filhos e exibi-los no pai
.
3. Prompts Reutilizáveis para Revisão
Copie e cole os prompts abaixo na sua IA de estudo para fazer revisões espaçadas ou aprofundar-se em temas específicos antes da entrevista:
"Estou revisando o modelo de segurança do Salesforce. Crie um cenário prático complexo envolvendo OWD, Role Hierarchy, Sharing Rules e Field-Level Security, e depois me pergunte como eu resolveria um problema de visibilidade de dados nesse cenário."
"Explique a diferença técnica e os casos de uso entre um Before Save Flow e um After Save Flow. Forneça 2 exemplos práticos de processos de negócios onde seria obrigatório usar After Save ao invés de Before Save."
"Atue como um recrutador de DevOps no ecossistema Salesforce. Faça-me 3 perguntas difíceis sobre as limitações dos Change Sets e por que uma grande corporação migraria para o DevOps Center ou Copado."
"Quero entender como evitar 'alucinações' no Agentforce. Descreva o conceito de 'Grounding' e do 'Einstein Trust Layer' e como um administrador configura limites seguros (Guardrails) para agentes baseados em IA."
