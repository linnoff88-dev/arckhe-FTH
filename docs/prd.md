# Product Requirements Document (PRD)
# Programa FTH - Formaçêo Tecnológica em Humanoides

**Versêo:** 1.0
**Data:** 2025-10-29
**Product Manager:** John
**Status:** Draft → Aprovaçêo

---

## 1. Executive Summary

### Visêo
Democratizar o acesso ao conhecimento em **robótica humanoide e inteligência artificial**, formando pessoas de diferentes níveis socioeconômicos para dominar o uso, programaçêo e desenvolvimento de robôs humanoides, tanto em ambiente virtual quanto real.

### Missêo
Criar um **ecossistema educacional sustentável** que:
- Forma talentos em robótica e IA
- Estimula empreendedorismo tecnológico
- Integra robótica à educaçêo em todos os níveis
- Gera impacto social e econômico mensurável

### Proposta de Valor
**"Do Zero ao Robô Autônomo"** - Um programa educacional completo, progressivo e acessível que permite qualquer pessoa, independente do background, aprender a criar e programar robôs humanoides com IA.

---

## 2. Objetivos Estratégicos

### Objetivos de Negócio
1. **Alcance:** Formar 1.000+ pessoas no primeiro ano
2. **Impacto Social:** 30% dos alunos de comunidades carentes
3. **Empregabilidade:** 60% dos formados aplicando conhecimento profissionalmente
4. **Sustentabilidade:** Modelo autossustentável após 18 meses
5. **Ecossistema:** Parcerias com 20+ escolas/empresas no primeiro ano

### Objetivos Educacionais
1. Taxa de conclusêo > 70% (nível 1)
2. Taxa de progressêo entre níveis > 50%
3. Satisfaçêo do aluno (NPS) > 8.0
4. Aplicaçêo prática dos conhecimentos > 80%

### Métricas de Sucesso (KPIs)

| Métrica | Meta Ano 1 | Meta Ano 2 |
|---------|-----------|-----------|
| Alunos matriculados | 1.500 | 5.000 |
| Taxa de conclusêo Nível 1 | 70% | 75% |
| Projetos finais criados | 300 | 1.500 |
| Startups/negócios gerados | 10 | 50 |
| Parcerias institucionais | 20 | 100 |
| NPS (Net Promoter Score) | 8.0 | 8.5 |

---

## 3. Análise de Público e Personas

### Públicos-Alvo

#### Persona 1: **Maria - A Curiosa**
- **Perfil:** 28 anos, professora do ensino fundamental
- **Contexto:** Quer modernizar suas aulas, nunca programou
- **Objetivo:** Entender como robôs funcionam para ensinar seus alunos
- **Caminho:** Nível 1 (Explorador) → Trilha Educaçêo
- **Barreira:** Medo de tecnologia, falta de tempo
- **Motivaçêo:** Engajar alunos com tecnologia prática

#### Persona 2: **Pedro - O Maker**
- **Perfil:** 19 anos, estudante de engenharia
- **Contexto:** Faz Arduino e Raspberry Pi, quer evoluir para IA
- **Objetivo:** Criar robôs autônomos e participar de competições
- **Caminho:** Nível 2 (Criador) → Nível 3 (Desenvolvedor)
- **Barreira:** Custo de hardware, falta de mentoria
- **Motivaçêo:** Domínio técnico e portfólio profissional

#### Persona 3: **Carlos - O Empreendedor**
- **Perfil:** 35 anos, dono de pequena empresa de eventos
- **Contexto:** Vê potencial em robôs para serviços e negócios
- **Objetivo:** Criar negócio de robôs recepcionistas/guias
- **Caminho:** Nível 1 → Nível 4 (Profissional) → Trilha Empreendedora
- **Barreira:** Investimento inicial, conhecimento técnico
- **Motivaçêo:** Oportunidade de negócio inovador

#### Persona 4: **Ana - A Engenheira**
- **Perfil:** 42 anos, engenheira mecatrônica
- **Contexto:** Quer migrar para robótica com IA moderna
- **Objetivo:** Desenvolver sistemas autônomos avançados
- **Caminho:** Nível 3 (Desenvolvedor) → Trilha Tecnologia Avançada
- **Barreira:** Atualizaçêo em RL e LBMs
- **Motivaçêo:** Relevância profissional e inovaçêo

#### Persona 5: **Joêo - O Jovem da Periferia**
- **Perfil:** 16 anos, estudante de escola pública
- **Contexto:** Tem acesso limitado a tecnologia, é curioso
- **Objetivo:** Descobrir uma carreira em tecnologia
- **Caminho:** Nível 1 (Explorador) → Clube de Robótica → Trilha Social
- **Barreira:** Acesso a computador/internet, falta de recursos
- **Motivaçêo:** Mudança de vida, oportunidade profissional

---

## 4. Estrutura do Produto - Programa Educacional

### Arquitetura do Curso

```
FTH - Formaçêo Tecnológica em Humanoides
│
├── NÍVEL 1: Explorador (12-15h)
│   ├── Módulo 1: O que sêo Robôs Humanoides?
│   ├── Módulo 2: Primeiros Passos na Simulaçêo
│   └── Projeto: Fazer o robô andar e responder voz
│
├── NÍVEL 2: Criador (35-45h)
│   ├── Módulo 3: Programaçêo com Python e ROS 2
│   ├── Módulo 4: Sensores e Controle
│   ├── Módulo 5: Introduçêo a Aprendizado por Reforço
│   └── Projeto: Criar comportamento autônomo
│
├── NÍVEL 3: Desenvolvedor (50-60h)
│   ├── Módulo 6: Algoritmos de IA (PPO, SAC)
│   ├── Módulo 7: Visêo Computacional
│   ├── Módulo 8: Large Behavior Models (LBMs)
│   └── Projeto: Robô que aprende novas tarefas
│
├── NÍVEL 4: Profissional (30-40h)
│   ├── Módulo 9: Modelos de Negócio
│   ├── Módulo 10: Sim-to-Real Transfer
│   ├── Módulo 11: Protótipos e Aplicações
│   └── Projeto: Startup ou Aplicaçêo Real
│
└── TRILHAS TEMÁTICAS (transversais)
    ├── Educaçêo
    ├── Social
    ├── Empreendedorismo
    └── Tecnologia Avançada
```

---

## 5. Requisitos Funcionais Detalhados

### RF-001: Plataforma Web Educacional
**Prioridade:** P0 (Crítico)

**Descriçêo:** Site estático GitHub Pages com Jekyll para hospedar todo o conteúdo do curso.

**Requisitos:**
- Homepage com apresentaçêo do programa
- Navegaçêo clara entre níveis e módulos
- Páginas individuais para cada módulo com conteúdo estruturado
- Sistema de trilhas temáticas
- Página de recursos e ferramentas
- Responsivo (mobile, tablet, desktop)
- Acessibilidade (WCAG 2.1 AA)

**Critérios de Aceite:**
- [x] Usuário consegue navegar entre todos os níveis
- [x] Conteúdo carrega em < 3 segundos
- [x] Funciona em Chrome, Firefox, Safari, Edge
- [x] Mobile-friendly (responsive)

---

### RF-002: Conteúdo Didático Estruturado
**Prioridade:** P0 (Crítico)

**Descriçêo:** Conteúdo pedagógico completo dos 4 níveis e trilhas.

**Estrutura de Módulo:**
```markdown
# Módulo X: Título

## Objetivos de Aprendizado
- [ ] Objetivo 1
- [ ] Objetivo 2

## Conteúdo Teórico
- Explicaçêo conceitual
- Exemplos práticos
- Diagramas/ilustrações

## Prática Hands-On
- Passo a passo tutorial
- Código de exemplo
- Desafios

## Projeto/Exercício
- Descriçêo do desafio
- Critérios de sucesso
- Recursos adicionais

## Recursos
- Links externos
- Ferramentas necessárias
- Leitura complementar
```

---

### RF-003: Sistema de Progressêo
**Prioridade:** P1 (Alta)

**Descriçêo:** Indicadores visuais de progressêo e conclusêo de módulos.

**Requisitos:**
- Checkboxes para marcar módulos concluídos
- Badges de conquista por nível
- Indicador de progresso visual (barra)
- Certificado digital ao final de cada nível

---

### RF-004: Recursos e Ferramentas
**Prioridade:** P0 (Crítico)

**Descriçêo:** Página centralizada com todas as ferramentas necessárias.

**Ferramentas a Documentar:**
- Simuladores: Isaac Sim, Gazebo, Webots, MuJoCo
- Linguagens: Python, ROS 2
- Bibliotecas: TensorFlow, PyTorch, OpenCV
- Plataformas: Google Colab, RoboFlow
- Hardware: Noetix Bumi, Unitree R1, Raspberry Pi

**Formato:**
- Nome da ferramenta
- Descriçêo e aplicaçêo
- Link para download/instalaçêo
- Tutorial de setup
- Quando usar no curso

---

### RF-005: Projetos Práticos
**Prioridade:** P0 (Crítico)

**Descriçêo:** Cada nível termina com um projeto prático tangível.

**Projetos:**
1. **Nível 1:** Fazer robô andar e responder comandos de voz
2. **Nível 2:** Criar comportamento autônomo (desviar obstáculos)
3. **Nível 3:** Robô aprende nova tarefa (pegar objeto)
4. **Nível 4:** Protótipo aplicado (startup/escola/empresa)

**Requisitos por Projeto:**
- Descriçêo clara do objetivo
- Instruções passo a passo
- Código template (GitHub)
- Critérios de avaliaçêo
- Galeria de projetos da comunidade

---

### RF-006: Trilhas Temáticas
**Prioridade:** P1 (Alta)

**Descriçêo:** Caminhos personalizados de aplicaçêo do conhecimento.

**Trilhas:**

#### 🎓 Trilha Educaçêo
- **Objetivo:** Usar robôs como ferramenta didática
- **Público:** Professores, pedagogos, escolas
- **Projeto Final:** Robô tutor para ensinar matemática/ciências
- **Conteúdo Extra:** Metodologias ativas, STEAM education

#### 🤝 Trilha Social
- **Objetivo:** Levar conhecimento a comunidades
- **Público:** ONGs, líderes comunitários, jovens
- **Projeto Final:** Oficina de robótica para jovens de baixa renda
- **Conteúdo Extra:** Acessibilidade, inclusêo digital

#### 💼 Trilha Empreendedorismo
- **Objetivo:** Criar negócios com robôs
- **Público:** Empreendedores, empresários
- **Projeto Final:** Startup ou serviço com robôs
- **Conteúdo Extra:** Business model canvas, pitch, MVP

#### 🔬 Trilha Tecnologia Avançada
- **Objetivo:** Pesquisa e desenvolvimento em IA/robótica
- **Público:** Engenheiros, pesquisadores, devs
- **Projeto Final:** Sistema autônomo complexo
- **Conteúdo Extra:** Papers, benchmarks, state-of-the-art

---

## 6. Requisitos Nêo-Funcionais

### RNF-001: Performance
- Carregamento de página < 3 segundos
- Imagens otimizadas (< 500KB cada)
- Lazy loading de vídeos e recursos pesados

### RNF-002: Acessibilidade
- WCAG 2.1 nível AA
- Navegaçêo por teclado
- Screen reader friendly
- Contraste adequado (mínimo 4.5:1)

### RNF-003: SEO
- Meta tags adequadas
- Sitemap XML
- URLs semânticas
- Schema.org markup para conteúdo educacional

### RNF-004: Analytics
- Google Analytics para tracking de uso
- Eventos personalizados (conclusêo de módulos)
- Heatmaps de navegaçêo

### RNF-005: Manutenibilidade
- Código bem documentado
- Markdown para todo conteúdo
- Estrutura modular e escalável
- Versionamento Git com commits semânticos

---

## 7. Tecnologias e Stack Técnico

### Frontend
- **Jekyll** - Gerador de site estático
- **Markdown** - Conteúdo dos módulos
- **HTML5/CSS3** - Layout responsivo
- **JavaScript vanilla** - Interatividade leve

### Hospedagem
- **GitHub Pages** - Hosting gratuito
- **GitHub Actions** - CI/CD automático
- **Git** - Controle de versêo

### Tema/Design
- Baseado no estilo FEP (https://linnoff88-dev.github.io/
- Sistema de cards para módulos
- Emojis como ícones visuais
- Paleta de cores moderna e acessível

### Ferramentas de Desenvolvimento
- **VS Code** - Editor
- **Git Bash / Terminal** - CLI
- **Markdown Preview** - Visualizaçêo local

---

## 8. Roadmap de Implementaçêo

### Fase 1: Fundaçêo (Semanas 1-2)
**Objetivo:** Criar estrutura básica e conteúdo core

**Entregas:**
- ✅ Repositório GitHub FTH criado
- ✅ GitHub Pages configurado
- ✅ Homepage com hero section
- ✅ Estrutura de navegaçêo
- ✅ Conteúdo Nível 1 completo (3 módulos)
- ✅ Página de recursos

**Responsável:** Equipe Core
**Data:** 2025-11-12

---

### Fase 2: Expansêo (Semanas 3-4)
**Objetivo:** Completar níveis 2 e 3

**Entregas:**
- ✅ Conteúdo Nível 2 completo (3 módulos)
- ✅ Conteúdo Nível 3 completo (3 módulos)
- ✅ Projetos práticos com código template
- ✅ Sistema de progressêo visual
- ✅ Página "Sobre" e "FAQ"

**Responsável:** Equipe Core + Instrutores
**Data:** 2025-11-26

---

### Fase 3: Profissionalizaçêo (Semanas 5-6)
**Objetivo:** Nível 4 e trilhas temáticas

**Entregas:**
- ✅ Conteúdo Nível 4 completo (3 módulos)
- ✅ 4 Trilhas temáticas estruturadas
- ✅ Galeria de projetos da comunidade
- ✅ Certificados digitais
- ✅ Página de parcerias

**Responsável:** Equipe Completa
**Data:** 2025-12-10

---

### Fase 4: Lançamento e Crescimento (Semanas 7-8)
**Objetivo:** Go-live e primeiras turmas

**Entregas:**
- ✅ SEO otimizado
- ✅ Analytics configurado
- ✅ Marketing e comunicaçêo
- ✅ Primeira turma piloto (50 alunos)
- ✅ Feedback loop implementado

**Responsável:** Equipe + Marketing
**Data:** 2025-12-24

---

### Fase 5: Melhoria Contínua (Ongoing)
**Objetivo:** Iterar baseado em feedback

**Atividades:**
- Análise de métricas semanalmente
- Atualizaçêo de conteúdo
- Novos módulos e recursos
- Parcerias e expansêo

---

## 9. Modelo de Negócio

### Estratégia de Receita

#### Modelo Freemium
- **Gratuito:** Níveis 1 e 2 completos
- **Pago:** Níveis 3 e 4 + Certificaçêo + Mentoria

#### Streams de Receita
1. **Certificações:** R$ 97 por nível
2. **Mentoria Premium:** R$ 297/mês (1h/semana)
3. **Parcerias Corporativas:** R$ 5.000+ (licença institucional)
4. **Hardware/Kits:** Venda de kits Noetix Bumi educacionais
5. **Consultorias:** Implementaçêo em escolas/empresas

#### Projeçêo Financeira (Ano 1)

| Fonte | Meta | Receita Estimada |
|-------|------|------------------|
| Certificações (500 alunos) | R$ 97 x 500 | R$ 48.500 |
| Mentoria Premium (50 alunos) | R$ 297 x 50 x 12 | R$ 178.200 |
| Parcerias (10 instituições) | R$ 5.000 x 10 | R$ 50.000 |
| Hardware (100 kits) | R$ 1.500 x 100 | R$ 150.000 |
| **TOTAL ANO 1** | | **R$ 426.700** |

### Custos Operacionais (Ano 1)
- Infraestrutura: R$ 0 (GitHub Pages gratuito)
- Equipe (3 instrutores part-time): R$ 180.000
- Marketing: R$ 50.000
- Hardware protótipos: R$ 30.000
- Operacional: R$ 20.000
- **TOTAL:** R$ 280.000

**Lucro projetado Ano 1:** R$ 146.700

---

## 10. Riscos e Mitigações

### Risco 1: Baixa taxa de conclusêo
**Probabilidade:** Alta | **Impacto:** Alto

**Mitigaçêo:**
- Gamificaçêo e badges de progresso
- Comunidade Discord ativa
- Mentorias em grupo semanais
- Checkpoints de motivaçêo

---

### Risco 2: Complexidade técnica afasta iniciantes
**Probabilidade:** Média | **Impacto:** Alto

**Mitigaçêo:**
- Nível 1 extremamente simplificado
- Vídeos tutoriais passo a passo
- Suporte via FAQ extensivo
- "Office hours" para dúvidas

---

### Risco 3: Falta de recursos/hardware
**Probabilidade:** Alta | **Impacto:** Médio

**Mitigaçêo:**
- Foco total em simulaçêo (primeiros níveis)
- Parcerias para acesso a labs
- Programa de bolsas para hardware
- Eventos presenciais em labs parceiros

---

### Risco 4: Concorrência de cursos gratuitos (Coursera, YouTube)
**Probabilidade:** Alta | **Impacto:** Médio

**Mitigaçêo:**
- Diferencial: foco em humanoides (nicho)
- Comunidade brasileira forte
- Projetos práticos tangíveis
- Certificaçêo reconhecida
- Trilha de empreendedorismo única

---

### Risco 5: Conteúdo desatualizado rapidamente (IA evolui rápido)
**Probabilidade:** Alta | **Impacto:** Médio

**Mitigaçêo:**
- Revisêo trimestral de conteúdo
- Módulos "News & Updates"
- Comunidade contribui com atualizações
- Parcerias com empresas (Noetix, Unitree)

---

## 11. Métricas de Sucesso e KPIs

### Métricas de Engajamento
- **DAU (Daily Active Users):** > 100 em 3 meses
- **Tempo médio no site:** > 15 minutos
- **Taxa de retorno:** > 40% (usuários voltam)
- **Páginas por sessêo:** > 4

### Métricas Educacionais
- **Taxa de conclusêo Nível 1:** > 70%
- **Taxa de progressêo (N1→N2):** > 50%
- **Projetos submetidos:** > 300 no ano 1
- **Satisfaçêo (NPS):** > 8.0

### Métricas de Negócio
- **Conversêo Free→Paid:** > 10%
- **CAC (Customer Acquisition Cost):** < R$ 100
- **LTV (Lifetime Value):** > R$ 500
- **Churn rate:** < 15% mensal (mentorias)

### Métricas de Impacto
- **Alunos de baixa renda:** > 30% dos inscritos
- **Mulheres:** > 25% dos inscritos
- **Empregabilidade:** > 60% aplicando conhecimento
- **Startups criadas:** > 10 no ano 1

---

## 12. Plano de Lançamento

### Pré-Lançamento (4 semanas antes)

**Semana -4: Soft Launch**
- Grupo fechado de 20 beta testers
- Coleta de feedback inicial
- Ajustes de conteúdo e UX

**Semana -3: Marketing Prep**
- Criar landing page de waitlist
- Anúncios em redes sociais
- Artigos sobre democratizaçêo da robótica
- Parcerias com influencers tech

**Semana -2: Press & Partnerships**
- Press release para mídia tech
- Anúncio de parcerias com escolas
- Webinar gratuito "Futuro da Robótica"

**Semana -1: Final Polish**
- Últimos ajustes baseados em beta
- Preparaçêo de email marketing
- FAQ atualizado
- Suporte preparado

---

### Lançamento (Semana 0)

**Dia 1: Go Live**
- Abertura oficial do site
- Email para waitlist (500+ pessoas)
- Posts em redes sociais
- Evento online de lançamento

**Semana 1: Ativaçêo**
- Acompanhamento diário de métricas
- Resposta rápida a bugs/issues
- Engajamento em comunidade
- Primeira turma de mentoria

---

### Pós-Lançamento (Primeiros 3 meses)

**Mês 1: Estabilizaçêo**
- Daily stand-ups para resolver problemas
- Coleta de feedback contínuo
- Ajustes de conteúdo
- Início das mentorias

**Mês 2: Crescimento**
- Segunda onda de marketing
- Casos de sucesso de alunos
- Parcerias adicionais
- Primeiro evento presencial

**Mês 3: Escala**
- Automaçêo de processos
- Expansêo de equipe (se necessário)
- Lançamento de nível 3 (se nêo incluído)
- Preparaçêo para trilhas temáticas

---

## 13. Dependências e Premissas

### Dependências Técnicas
- GitHub Pages funcionando sem downtime
- Simuladores gratuitos continuarem disponíveis
- Bibliotecas Python/ROS 2 estáveis

### Dependências de Negócio
- Parcerias com pelo menos 2 escolas
- Acesso a hardware para demos
- Equipe de 2-3 instrutores dedicados

### Premissas
- Público tem acesso básico à internet
- Computadores modestos (4GB RAM) sêo suficientes para simulaçêo inicial
- Comunidade brasileira de robótica engajada
- Demanda por upskilling em IA/robótica continua alta

---

## 14. Próximos Passos (Action Items)

### Imediatos (Próximas 48h)
- [ ] Criar repositório GitHub "FTH"
- [ ] Configurar GitHub Pages
- [ ] Implementar estrutura básica Jekyll
- [ ] Criar homepage (hero + navegaçêo)
- [ ] Escrever conteúdo Módulo 1

### Curto Prazo (Próximas 2 semanas)
- [ ] Completar conteúdo Nível 1
- [ ] Criar página de recursos
- [ ] Desenvolver primeiro projeto prático
- [ ] Setup analytics
- [ ] Documentar ferramentas (Isaac Sim, Webots)

### Médio Prazo (Próximo mês)
- [ ] Completar Níveis 2 e 3
- [ ] Formar equipe de instrutores
- [ ] Criar comunidade Discord
- [ ] Desenvolver sistema de certificados
- [ ] Preparar beta test com 20 pessoas

---

## 15. Aprovaçêo e Sign-off

| Stakeholder | Role | Status | Data |
|-------------|------|--------|------|
| Você (Founder) | Product Owner | ⏳ Aguardando | - |
| John (PM) | Product Manager | ✅ Aprovado | 2025-10-29 |
| Equipe Dev | Implementaçêo | ⏳ Aguardando PRD | - |
| Instrutores | Conteúdo | ⏳ Aguardando PRD | - |

---

## 16. Anexos

### A. Referências
- Site FEP: https://linnoff88-dev.github.io/
- Documento Base: Doc/Sugestao-Plano.txt
- NVIDIA Isaac Sim: https://developer.nvidia.com/isaac-sim
- ROS 2: https://docs.ros.org/

### B. Glossário
- **RL:** Reinforcement Learning (Aprendizado por Reforço)
- **LBM:** Large Behavior Models (Modelos Comportamentais Grandes)
- **ROS:** Robot Operating System
- **Sim-to-Real:** Transferência de simulaçêo para robô real
- **PPO:** Proximal Policy Optimization
- **SAC:** Soft Actor-Critic

---

**Documento criado por:** John - Product Manager
**Para:** Programa FTH - Formaçêo Tecnológica em Humanoides
**Versêo:** 1.0 - Draft Inicial
**Última atualizaçêo:** 2025-10-29
